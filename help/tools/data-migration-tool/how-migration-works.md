---
title: Fonctionnement de la migration des données
description: Découvrez le processus de migration des données entre Magento 1 et Magento 2, notamment la terminologie, les diagrammes de workflow et les étapes.
exl-id: 821492dc-ee5b-4c4a-9479-680ee8c5756d
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '782'
ht-degree: 0%

---

# Fonctionnement de la migration des données

Cette rubrique présente un aperçu général de la migration des données de Magento 1 vers Magento 2 à l’aide de la variable [!DNL Data Migration Tool].

Le [!DNL Data Migration Tool] est un outil d’interface de ligne de commande utilisé pour transférer des données du Magento 1 vers le Magento 2. L’outil vérifie la cohérence entre les structures de base de données du Magento 1 et 2 (tables et champs), suit la progression du transfert des données, crée des logs et exécute des tests de vérification des données.

## Terminologie

* **Modes** - un ensemble ordonné d’opérations pour la migration des données de Magento 1.x vers Magento 2.x.
* **Étapes** - les tâches dans un mode qui définissent les types de données à migrer.
* **Phases** : tâches de l’étape qui valident, transfèrent et vérifient les données.
* **Fichiers de mappage** - fichiers XML qui définissent les règles et les connexions entre les structures de données Magento 1.x et Magento 2.x pour terminer les étapes.

## Modes

Le [!DNL Data Migration Tool] divise le processus de migration en trois phases ou *modes* afin de transférer et d’adapter les données de Magento 1.x vers Magento 2.x. Les trois modes sont répertoriés ici et doivent être exécutés dans l’ordre suivant :

1. **Mode Paramètres**: migre la configuration système et les paramètres liés au site web.
1. **Mode des données**: migre les ressources de base de données en masse.
1. **Mode Delta**: migre les modifications incrémentielles (modifications depuis la dernière exécution), telles que les nouveaux clients et les nouvelles commandes.

![Modes de migration](../../assets/data-migration/MigrationModes2.png)

## Étapes

Le [!DNL Data Migration Tool] utilise une liste de *étapes* dans chaque mode pour migrer un type particulier de données. Par exemple, en mode Paramètres , deux étapes sont utilisées pour migrer toutes les données de paramètres : les étapes Magasins et Paramètres . Vous trouverez des détails sur les données spécifiques migrées au cours de chacune de ces étapes (et pour les étapes dans les autres modes) dans la section [[!DNL Data Migration Tool] Spécifications techniques](technical-specification.md).

![Présentation de la migration](../../assets/data-migration/MigrationOverview2.png)

## Phases

Chaque étape comporte trois *phases* qui sont toujours exécutées dans cet ordre pour s’assurer que les données sont correctement migrées :

1. **Contrôle d’intégrité**: Compare les noms, types et autres informations des champs de tableau afin de vérifier la compatibilité entre les structures de données Magento 1 et 2.
1. **Transfert de données**: Transfère le tableau de données par tableau à partir des Magento 1 et 2.
1. **Vérification du volume**: Compare le nombre d’enregistrements entre les tables pour vérifier que le transfert a réussi.

![Etapes de migration](../../assets/data-migration/MigrationSteps2.png)

## Fichiers de mappage

Au niveau le plus bas des processus de migration sont les processus XML *fichiers de mappage*. Le [!DNL Data Migration Tool] utilise des fichiers map dans les étapes d’une étape pour transformer différentes structures de données entre les tables Magento 1.x et 2.x.

Par exemple, lorsque vous transformez les données d’une base de données Magento Open Source 1.8.0.0 en Magento Open Source 2.x.x, le fichier map tient compte du fait qu’une table a été renommée et le renomme en conséquence dans la base de données de destination. S’il n’existe aucune différence au niveau de la structure ou du format des données, la variable [!DNL Data Migration Tool] le transfère en l’état, y compris les données des tables créées par des extensions, vers la base de données Magento 2.

Lorsque les différences ne sont pas déclarées dans les fichiers de mappage, la variable [!DNL Data Migration Tool] affiche une erreur et ne démarre pas.

Les fichiers de mappage sont présentés plus en détail dans la section [[!DNL Data Migration Tool] Spécifications techniques].

## Diagramme de flux de migration

![Flux de migration](../../assets/data-migration/migration_flow.png)

[[!DNL Data Migration Tool] Spécifications techniques](technical-specification.md)

Nous sommes heureux que vous envisagiez de passer de la plateforme mondiale de commerce #1 — Magento 1.x — à la plateforme du futur, Magento 2. Nous sommes ravis de partager les détails de ce processus, que nous appelons migration.

## Composants de migration

La migration du Magento 2 comprend quatre composants : données, extensions et code personnalisé, thèmes et personnalisations.

### Données

Nous avons développé la variable **Magento 2[!DNL Data Migration Tool]** pour vous aider à déplacer efficacement tous vos produits, clients et données de commande, configurations de magasin, promotions, etc. vers Magento 2. Ce guide fournit des informations sur l’outil et les bonnes pratiques pour l’utiliser pour migrer vos données.

### Extensions et code personnalisé

Nous travaillons dur avec la communauté de développement pour vous aider à utiliser vos extensions Magento 1 dans Magento 2. Maintenant, nous sommes fiers de présenter le [Commerce Marketplace](https://marketplace.magento.com/), où vous pouvez télécharger ou acheter les dernières versions de vos extensions préférées.

Pour plus d’informations sur le développement d’extensions pour Magento 2, reportez-vous à la section [Guide du développeur PHP](https://developer.adobe.com/commerce/php/development/).

### Thèmes et personnalisations

Magento 2 utilise de nouvelles approches et technologies qui donnent aux commerçants une capacité inégalée de créer des expériences commerciales innovantes et de les adapter à de nouveaux niveaux. Pour tirer parti de ces avancées, les développeurs doivent apporter des modifications à leurs thèmes et personnalisations. La documentation est disponible en ligne pour la création de Magento 2 [thèmes](https://developer.adobe.com/commerce/frontend-core/guide/themes/), [dispositions](https://developer.adobe.com/commerce/frontend-core/guide/layouts/), et [personnalisations](https://developer.adobe.com/commerce/frontend-core/guide/layouts/xml-manage/).

## Efforts de migration

Tout comme une mise à niveau entre les versions 1.x (par exemple, de la version 1.12 à la version 1.14), le niveau d’effort pour migrer de Magento 1 à Magento 2 dépend de la manière dont vous avez créé votre site et de son niveau de personnalisation.
Cependant, nous améliorons constamment le [!DNL Data Migration Tool] (voir [Changelog](https://github.com/magento/data-migration-tool/blob/2.3/CHANGELOG.md) pour plus de détails); ainsi, les efforts de migration diminuent continuellement.
