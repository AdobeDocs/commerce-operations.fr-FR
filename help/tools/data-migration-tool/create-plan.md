---
title: Création d’un plan de migration des données
description: Découvrez comment créer un plan de migration des données pour effectuer la mise à niveau de Magento 1 vers Magento 2. Planifiez et testez votre migration pour éviter les problèmes.
exl-id: a14237f3-c5fe-4f5f-86eb-ed4c39507bff
topic: Commerce, Migration
source-git-commit: 6896d31a202957d7354c3dd5eb6459eda426e8d7
workflow-type: tm+mt
source-wordcount: '889'
ht-degree: 0%

---

# Création d’un plan de migration des données

Pour migrer avec succès et éviter les problèmes, vous devez planifier minutieusement et tester votre migration.

## Avant de commencer : envisagez une mise à niveau

La migration est un bon moment pour effectuer des changements importants et préparer votre site pour le prochain niveau de croissance. Déterminez si votre nouveau site doit être conçu avec du matériel supplémentaire ou avec une topologie plus avancée avec de meilleurs niveaux de mise en cache.

## Étape 1 : vérifier les extensions sur votre site actuel

* Quelles extensions avez-vous installées ?

* Avez-vous déterminé si vous avez besoin de toutes ces extensions sur votre nouveau site ? Il peut y en avoir d’anciennes que vous pouvez supprimer en toute sécurité.

* Avez-vous déterminé si des versions Magento 2 de vos extensions existent ? Rendez-vous sur [Commerce Marketplace](https://commercemarketplace.adobe.com/) pour obtenir les dernières versions ou contactez votre fournisseur d’extensions.

* Quelles ressources de base de données de vos extensions souhaitez-vous migrer ?

## Étape 2 : créer et préparer votre boutique pour la migration

* Configurez un système matériel Magento 2 en utilisant une topologie et une conception qui correspondent au moins à votre système Magento 1 existant

* Installez Magento 2 (avec tous les modules de cette version) et le [!DNL Data Migration Tool] sur un système conforme à la [configuration requise](../../installation/system-requirements.md)

* Personnalisez le code [!DNL Data Migration Tool] pour ignorer certaines données (comme les pages CMS ou les règles de vente) ou convertir des personnalisations lors de la migration. Lisez le [!DNL Data Migration Tool]Spécifications techniques[ de la ](technical-specification.md) pour en savoir plus sur le fonctionnement de la migration

## Étape 3 : Exécution d’essai

Avant de commencer la migration dans l’environnement de production, passez en revue toutes les étapes de migration dans votre environnement de test.

Dans ces tests de migration, procédez comme suit :

* Copiez votre magasin Magento 1 sur un serveur d’évaluation

* Effectuez une migration complète du magasin Magento 1 répliqué vers Magento 2

* Testez minutieusement votre nouvelle boutique

## Étape 4 : démarrer la migration

1. Assurez-vous que le [!DNL Data Migration Tool] dispose d’un accès réseau pour se connecter aux bases de données Magento 1 et Magento 2. Ouvrez les ports correspondants dans votre pare-feu.

1. Arrêtez toutes les activités du panneau d’administration de Magento 1 (à l’exception d’Order Management), telles que l’expédition, la création de factures et d’avoirs. La liste des activités autorisées peut être étendue en ajustant les paramètres du mode Delta dans la [!DNL Data Migration Tool].

   >[!NOTE]
   >
   >Ne reprenez pas ces activités tant que votre boutique Magento 2 n’est pas activée.

1. Nous vous recommandons d’arrêter toutes les tâches cron de Magento 1.

   Si certains traitements doivent être exécutés pendant la migration, assurez-vous qu&#39;ils ne créent ou ne modifient pas les entités de base de données d&#39;une manière que le mode Delta ne peut pas traiter.

   Par exemple, la tâche cron `enterprise_salesarchive_archive_orders` déplace les anciennes commandes vers l’archive. L&#39;exécution de cette tâche pendant la migration est sécurisée, car le mode Delta reconnaît cette tâche et traite correctement les commandes archivées.

1. Utilisez l’[!DNL Data Migration Tool] pour migrer les paramètres et les sites web.

1. Copiez vos fichiers multimédias Magento 1 dans Magento 2.

   Copiez ces fichiers manuellement depuis le répertoire `magento1-root/media` vers `magento2-root/pub/media`.

1. Utilisez le [!DNL Data Migration Tool] pour copier en bloc vos données de la base de données Magento 1 vers la base de données Magento 2.

   Si certaines de vos extensions contiennent des données que vous souhaitez migrer, vous devrez peut-être installer ces extensions adaptées à Magento 2. Si les extensions ont une structure différente dans la base de données Magento 2, utilisez les fichiers de mappage fournis avec le [!DNL Data Migration Tool].

1. Réindexez tous les indexeurs Magento 2. Pour plus d’informations, consultez [Gestion des indexeurs](../../configuration/cli/manage-indexers.md) dans le _Guide de configuration_.

## Étape 5 : apporter des modifications aux données migrées (si nécessaire)

Parfois, vous pouvez avoir besoin de votre boutique Magento 2 avec une structure de catalogue, des règles de vente et des pages CMS différentes après la migration.

Il est important de faire preuve de prudence lorsque vous effectuez des modifications manuelles des données. Les erreurs créent des erreurs dans l’étape de migration incrémentielle des données qui suit.

Par exemple, un produit supprimé de Magento 2 : celui qui a été acheté sur votre boutique Magento 1 active et qui n’est plus disponible dans votre boutique Magento 2. Le transfert des données relatives à cet achat peut entraîner une erreur lors de l&#39;exécution du [!DNL Data Migration Tool] en mode Delta.

## Étape 6 : mettre à jour les données incrémentielles

Après la migration des données, utilisez le mode Delta pour capturer et transférer des mises à jour incrémentielles de Magento 1 (telles que de nouvelles commandes, révisions et modifications du profil client) vers Magento 2.

* Lancez la migration incrémentielle ; les mises à jour s’exécutent en continu. Vous pouvez arrêter de transférer des mises à jour à tout moment en appuyant sur `Ctrl+C`.

* Testez votre site Magento 2 pendant cette période pour détecter d’éventuels problèmes dès que possible. Si vous rencontrez des problèmes, appuyez sur `Ctrl+C` pour arrêter la migration incrémentielle et la redémarrer une fois les problèmes résolus.

>[!NOTE]
>
>Des avertissements de vérification de volume peuvent s’afficher si vous effectuez des tests sur votre site Magento 2 et exécutez le processus de migration en même temps. Cela se produit car dans Magento 2, vous créez des entités qui n’existent pas dans l’instance Magento 1.

## Étape 7 : activation

Une fois votre site Magento 2 entièrement migré et fonctionnant normalement, effectuez la transition :

1. Mettez votre système Magento 1 en mode de maintenance (LE TEMPS D’ARRÊT DÉMARRE).

1. Appuyez sur Ctrl+C dans la fenêtre de commande de l’outil de migration pour arrêter les mises à jour incrémentielles.

1. Démarrez vos traitements Magento 2 cron.

1. Dans votre système Magento 2, réindexez l’indexeur de stock. Pour plus d’informations, consultez [Gestion des indexeurs](../../configuration/cli/manage-indexers.md) dans le _Guide de configuration_.

1. À l’aide d’un outil de votre choix, accédez aux pages de votre système Magento 2 pour mettre en cache les pages avant les clients qui utilisent votre storefront.

1. Effectuez toute vérification finale de votre site Magento 2.

1. Modifiez le DNS, les équilibreurs de charge, etc. pour pointer vers un nouveau matériel de production (DOWNTIME ENDS).

1. Le magasin Magento 2 est maintenant prêt à l’emploi. Vous et vos clients pouvez reprendre toutes les activités.
