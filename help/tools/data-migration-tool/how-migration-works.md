---
title: Fonctionnement de la migration des données
description: Découvrez le processus de migration des données entre Magento 1 et Magento 2, notamment la terminologie, les diagrammes de workflow et les étapes.
exl-id: 821492dc-ee5b-4c4a-9479-680ee8c5756d
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '781'
ht-degree: 0%

---

# Fonctionnement de la migration des données

Cette rubrique fournit une présentation détaillée de la migration des données de Magento 1 vers Magento 2 à l’aide de l’[!DNL Data Migration Tool] .

Le [!DNL Data Migration Tool] est un outil d’interface de ligne de commande (CLI) utilisé pour transférer des données de Magento 1 vers Magento 2. L’outil vérifie la cohérence entre les structures de base de données Magento 1 et 2 (tables et champs), suit la progression du transfert de données, crée des journaux et exécute des tests de vérification des données.

## Terminologie

* **Modes** : ensemble ordonné d’opérations pour la migration des données de Magento 1.x vers Magento 2.x.
* **Étapes** : les tâches d’un mode qui définissent les types de données à migrer.
* **Étapes** - les tâches de l’étape qui valident, transfèrent et vérifient les données.
* **Fichiers de mappage** - Fichiers XML qui définissent les règles et les connexions entre les structures de données Magento 1.x et Magento 2.x pour terminer les étapes.

## Modes

Le [!DNL Data Migration Tool] divise le processus de migration en trois phases ou *modes* afin de transférer et d’adapter les données de Magento 1.x à Magento 2.x. Les trois modes sont répertoriés ici et doivent être exécutés dans cet ordre :

1. **Mode Paramètres** : migre la configuration du système et les paramètres liés au site Web.
1. **Mode données** : migre les ressources de base de données en bloc.
1. **Mode Delta** : migre les modifications incrémentielles (modifications depuis la dernière exécution), telles que les nouveaux clients et les commandes.

![Modes de migration](../../assets/data-migration/MigrationModes2.png)

## Étapes

Le [!DNL Data Migration Tool] utilise une liste d’*étapes* dans chaque mode pour migrer un type de données particulier. Par exemple, en mode Paramètres , deux étapes sont utilisées pour migrer toutes les données de paramètres : l’étape Magasins et l’étape Paramètres . Vous trouverez des informations détaillées sur les données spécifiques qui sont migrées à chacune de ces étapes (et pour les étapes dans les autres modes) dans la [[!DNL Data Migration Tool] Spécification technique](technical-specification.md).

![Présentation de la migration](../../assets/data-migration/MigrationOverview2.png)

## Étapes

Au sein de chaque étape se trouvent trois *étapes* qui sont toujours exécutées dans cet ordre pour s’assurer que les données sont correctement migrées :

1. **Vérification de l’intégrité** : compare les noms, types et autres informations des champs de la table afin de vérifier la compatibilité entre les structures de données Magento 1 et 2.
1. **Transfert de données** : transfère la table de données par table depuis Magento 1 et 2.
1. **Vérification du volume** : compare le nombre d’enregistrements entre les tables pour vérifier que le transfert a réussi.

![Étapes de migration](../../assets/data-migration/MigrationSteps2.png)

## Mapper des fichiers

Au niveau le plus bas des processus de migration se trouvent les fichiers XML *map*. Le [!DNL Data Migration Tool] utilise des fichiers de mappage dans les étapes d’une étape pour transformer différentes structures de données entre les tables Magento 1.x et 2.x.

Par exemple, lorsque vous transformez des données d’une base de données Magento Open Source 1.8.0.0 en Magento Open Source 2.x.x, le fichier map tient compte du fait qu’une table a été renommée et la renomme en conséquence dans la base de données de destination. S’il n’existe aucune différence dans la structure ou le format des données, le [!DNL Data Migration Tool] les transfère en l’état, y compris les données des tables créées par les extensions, vers la base de données Magento 2.

Lorsque les différences ne sont pas déclarées dans les fichiers de mappage, le [!DNL Data Migration Tool] affiche une erreur et ne démarre pas.

Les fichiers de mappage sont traités plus en détail dans la [Spécification technique [!DNL Data Migration Tool]].

## Diagramme de flux de migration

![Flux de migration](../../assets/data-migration/migration_flow.png)

[Spécification technique [!DNL Data Migration Tool]](technical-specification.md)

Nous sommes ravis que vous envisagiez de passer de la plateforme de commerce #1 mondiale (Magento 1.x) à la plateforme de l’avenir, Magento 2. Nous sommes ravis de vous communiquer les détails de ce processus, que nous appelons la migration.

## Composants de migration

La migration de Magento 2 implique quatre composants : les données, les extensions et le code personnalisé, les thèmes et les personnalisations.

### Données

Nous avons développé le **[!DNL Data Migration Tool]** Magento 2 pour vous aider à déplacer efficacement vers Magento 2 l’ensemble de vos données de produits, de clients et de commandes, les configurations de magasin, les promotions, etc. Ce guide fournit des informations sur l’outil et les bonnes pratiques pour l’utiliser afin de migrer vos données.

### Extensions et code personnalisé

Nous avons travaillé dur avec la communauté de développement pour vous aider à utiliser vos extensions Magento 1 dans Magento 2. Nous sommes maintenant fiers de présenter le [Commerce Marketplace](https://marketplace.magento.com/), où vous pouvez télécharger ou acheter les dernières versions de vos extensions préférées.

Vous trouverez plus d’informations sur le développement d’extensions pour Magento 2 dans le [Guide du développeur de PHP](https://developer.adobe.com/commerce/php/development/).

### Thèmes et personnalisations

Magento 2 utilise de nouvelles approches et technologies qui donnent aux commerçants une capacité inégalée à créer des expériences d’achat innovantes et à passer à de nouveaux niveaux. Pour tirer parti de ces avancées, les développeurs doivent apporter des modifications à leurs thèmes et personnalisations. La documentation relative à la création de Magento 2 [thèmes](https://developer.adobe.com/commerce/frontend-core/guide/themes/), [mises en page](https://developer.adobe.com/commerce/frontend-core/guide/layouts/) et [personnalisations](https://developer.adobe.com/commerce/frontend-core/guide/layouts/xml-manage/) est disponible en ligne.

## Efforts de migration

Tout comme une mise à niveau entre les versions 1.x (par exemple, de v1.12 à v1.14), le niveau d’effort pour migrer de Magento 1 à Magento 2 dépend de la manière dont vous avez créé votre site et de son niveau de personnalisation.
Cependant, nous améliorons constamment la [!DNL Data Migration Tool] (voir le [Journal des modifications](https://github.com/magento/data-migration-tool/blob/2.3/CHANGELOG.md) pour plus de détails) ; les efforts de migration diminuent donc continuellement.
