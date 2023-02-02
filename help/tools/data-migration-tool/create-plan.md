---
title: Création d’un plan de migration des données
description: Suivez ces étapes pour créer un plan de migration de données afin de garantir la réussite de la mise à niveau de Magento 1 vers Magento 2.
source-git-commit: 2e1a06b59fda7db4a9b32d000e1b2a3ca88926d3
workflow-type: tm+mt
source-wordcount: '900'
ht-degree: 0%

---


# Création d’un plan de migration des données

Pour migrer avec succès et éviter des problèmes, vous devez soigneusement planifier et tester votre migration.

## Avant de commencer : Envisager une mise à niveau

La migration est un moment idéal pour apporter des changements sérieux et préparer votre site au prochain niveau de croissance. Déterminez si votre nouveau site doit être conçu avec plus de matériel ou avec une topologie plus avancée avec de meilleurs niveaux de mise en cache.

## Étape 1 : Vérifier les extensions sur votre site actuel

* Quelles extensions avez-vous installées ?

* Avez-vous identifié si vous avez besoin de toutes ces extensions sur votre nouveau site ? Il peut y en avoir de vieilles que vous pouvez supprimer en toute sécurité.

* Avez-vous déterminé si Magento 2 versions de vos extensions existent ? Visite [Commerce Marketplace] pour connaître les dernières versions ou contacter votre fournisseur d’extension.

* Quels ressources de base de données de vos extensions souhaitez-vous migrer ?

## Étape 2 : Créer et préparer votre magasin pour la migration

* Configuration d’un système matériel Magento 2 à l’aide d’une topologie et d’une conception correspondant au moins à votre système Magento 1 existant

* Installez Magento 2.x (avec tous les modules de cette version) et le [!DNL Data Migration Tool] sur un système qui répond à la [configuration requise](../../installation/system-requirements.md)

* Effectuez vos ajustements personnalisés dans la variable [!DNL Data Migration Tool] du code au cas où vous n’auriez pas besoin de migrer certaines données (comme les pages CMS, les règles de vente) ou de convertir la personnalisation de votre Magento lors de la migration. Lisez le [!DNL Data Migration Tool]&#39;s [Spécifications techniques](technical-specification.md) pour mieux comprendre le fonctionnement de la migration depuis l’intérieur

## Étape 3 : Exécution d’essai

Avant de commencer la migration sur l’environnement de production, il est préférable de passer par toutes les étapes de migration sur votre environnement de test.

Dans ces tests de migration, procédez comme suit :

* Copie de la boutique Magento 1 sur un serveur d’évaluation

* Migration complète de la boutique du Magento répliqué 1 vers le Magento 2

* Testez minutieusement votre nouvelle boutique.

## Étape 4 : Commencer votre migration

1. Assurez-vous que la variable [!DNL Data Migration Tool] dispose d’un accès réseau pour se connecter aux bases de données Magento 1 et Magento 2. Ouvrez les ports correspondants dans votre pare-feu.

1. Arrêtez toutes les activités du panneau d’administration de Magento 1.x (à l’exception de la gestion des commandes), telles que l’expédition, la création de factures et de notes de crédit. La liste des activités autorisées peut être étendue en ajustant les paramètres du mode Delta dans la variable [!DNL Data Migration Tool].

   >[!NOTE]
   >
   >Vous ne devez pas reprendre ces activités tant que votre boutique Magento 2 n’est pas activée.

1. Nous vous recommandons d’arrêter toutes les tâches Magento 1.x cron.

   Néanmoins, si certaines tâches doivent être exécutées lors de la migration, veillez à ne pas créer de nouvelles entités de base de données ou à ne pas modifier les entités existantes de la manière dont elles ne peuvent pas être traitées par le mode Delta.

   Par exemple, la variable `enterprise_salesarchive_archive_orders` la tâche cron déplace les anciens ordres vers l’archive. L’exécution de cette tâche lors de la migration est sécurisée, car le mode Delta reconnaît cette tâche et traite correctement les commandes archivées.

1. Utilisez la variable [!DNL Data Migration Tool] pour migrer des paramètres et des sites web.

1. Copiez les fichiers multimédias Magento 1.x dans Magento 2.x.

   Vous devez copier ces fichiers manuellement à partir de la fonction `magento1-root/media` à `magento2-root/pub/media`.

1. Utilisez la variable [!DNL Data Migration Tool] pour copier en masse vos données de la base de données Magento 1 vers la base de données Magento 2.

   Si certaines de vos extensions contiennent des données que vous souhaitez migrer, vous devrez peut-être installer ces extensions adaptées à Magento 2. Si les extensions ont une structure différente dans la base de données Magento 2, utilisez les fichiers de mappage fournis avec la variable [!DNL Data Migration Tool].

1. Réindexez tous les indexeurs Magento 2.x. Pour plus d’informations, voir [Gestion des indexeurs](../../configuration/cli/manage-indexers.md) dans le _Guide de configuration_.

## Étape 5 : Apporter des modifications aux données migrées (si nécessaire)

Il peut arriver que vous souhaitiez disposer de votre magasin Magento 2 avec une structure de catalogue, des règles de vente et des pages CMS différentes après la migration.

Il est important de faire attention lorsque vous effectuez des modifications manuelles de données. Les erreurs créent des erreurs dans l’étape de migration incrémentielle des données qui suit.

Par exemple, un produit supprimé du Magento 2 : celle qui a été achetée dans votre magasin Magento 1 et qui n’est plus disponible dans votre magasin Magento 2. Le transfert des données relatives à cet achat peut entraîner une erreur lors de l’exécution de la variable [!DNL Data Migration Tool] en mode Delta.

## Étape 6 : Mise à jour des données incrémentielles

Après la migration des données, vous devez capturer par incréments les mises à jour de données qui ont été ajoutées dans le magasin Magento 1 (telles que les nouvelles commandes, les révisions et les modifications apportées aux profils client) et transférer ces mises à jour dans le magasin Magento 2 à l’aide du mode Delta.

* Démarrer la migration incrémentielle ; les mises à jour s’exécutent en permanence. Vous pouvez arrêter de transférer des mises à jour à tout moment en appuyant sur `Ctrl+C`.

* Testez votre site Magento 2 pendant cette période afin de détecter les problèmes le plus rapidement possible. Si vous rencontrez des problèmes, appuyez sur `Ctrl+C` pour arrêter la migration incrémentielle et la redémarrer après avoir résolu les problèmes.

>[!NOTE]
>
>Des avertissements relatifs à la vérification du volume peuvent s’afficher si vous testez votre site Magento 2 et exécutez le processus de migration en même temps. Cela se produit car dans Magento 2, vous créez des entités qui n’existent pas dans l’instance Magento 1.

## Étape 7 : Go live

Maintenant que votre site Magento 2 est à jour avec Magento 1 et fonctionne normalement, procédez comme suit pour le transférer vers le nouveau site :

1. Placez votre système Magento 1 en mode de maintenance (DÉMARRAGE DU TEMPS DE DOUTE).

1. Appuyez sur Ctrl+C dans la fenêtre de commande de l’outil de migration pour arrêter les mises à jour incrémentielles.

1. Démarrez vos tâches Magento 2 cron.

1. Dans votre système Magento 2, réindexez l’indexeur de stock. Pour plus d’informations, voir [Guide de configuration].

1. À l’aide d’un outil de votre choix, accédez aux pages de votre système Magento 2 pour mettre en cache les pages avant les clients qui utilisent votre storefront.

1. Effectuez toute vérification finale de votre site Magento 2.

1. Modifiez le DNS, les équilibreurs de charge, etc. afin qu’ils pointent vers le nouveau matériel de production (FIN DU TEMPS).

1. Le magasin Magento 2 est maintenant prêt à l’emploi. Vous et vos clients pouvez reprendre toutes les activités.

<!-- LINK ADDRESSES -->

[Commerce Marketplace]: https://marketplace.magento.com
