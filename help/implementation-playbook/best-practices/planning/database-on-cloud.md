---
title: Bonnes pratiques de configuration de base de données pour les déploiements cloud
description: Découvrez comment configurer les paramètres de la base de données et de l’application afin d’améliorer les performances lors du déploiement d’Adobe Commerce sur l’infrastructure cloud.
role: Developer, Admin
feature: Best Practices
exl-id: ca377dc8-c8bd-4f77-a24b-22a298e2bba4
source-git-commit: 3e0187b7eeb6475ea9c20bc1da11c496b57853d1
workflow-type: tm+mt
source-wordcount: '680'
ht-degree: 0%

---

# Bonnes pratiques relatives à la configuration des bases de données

Découvrez les bonnes pratiques pour améliorer les performances de la base de données et travailler efficacement avec la base de données lors du déploiement d’Adobe Commerce sur l’infrastructure cloud.

## Produits concernés

Adobe Commerce sur l’infrastructure cloud

## Convertir toutes les tables MyISAM en InnoDB

Adobe recommande d&#39;utiliser le moteur de base de données InnoDB. Dans une installation Adobe Commerce par défaut, toutes les tables de la base sont stockées à l&#39;aide du moteur InnoDB. Cependant, certains modules tiers (extensions) peuvent introduire des tableaux au format MyISAM. Après avoir installé un module tiers, vérifiez la base de données pour identifier les tables dans `myisam` formater et les convertir en `innodb` format.

### Déterminer si un module comprend des tables MyISAM

Vous pouvez analyser le code de module tiers avant de l’installer afin de déterminer s’il utilise des tables MyISAM.

Si vous avez déjà installé une extension, exécutez la requête suivante pour déterminer si la base de données contient des tables MyISAM :

```sql
SELECT table_schema, CONCAT(ROUND((index_length+data_length)/1024/1024),'MB')
    AS total_size FROM information_schema. TABLES WHERE engine='myisam' AND table_schema
    NOT IN ('mysql', 'information_schema', 'performance_schema', 'sys');
```

### Remplacez le moteur de stockage par InnoDB.

Dans le `db_schema.xml` déclaration du tableau, définissez la variable `engine` valeur d’attribut pour la `table` noeud à `innodb`. À titre de référence, voir [Configuration du schéma déclaratif > noeud de tableau](https://developer.adobe.com/commerce/php/development/components/declarative-schema/configuration/) dans notre documentation destinée aux développeurs.

Le schéma de déclaration a été introduit dans Adobe Commerce sur l’infrastructure cloud version 2.3.

## Configuration du moteur de recherche recommandé pour la recherche MySQL native

Adobe recommande de toujours configurer Elasticsearch ou OpenSearch pour votre projet d’infrastructure cloud Adobe Commerce sur , même si vous envisagez de configurer un outil de recherche tiers pour votre application Adobe Commerce. Cette configuration fournit une option de secours en cas d’échec de l’outil de recherche tiers.

Le moteur de recherche que vous utilisez dépend de la version cloud d’Adobe Commerce installée :

- Pour Adobe Commerce 2.4.4 et versions ultérieures, utilisez le service OpenSearch pour la recherche MySQL native.

- Pour les versions antérieures d’Adobe Commerce, utilisez Elasticsearch.

Pour déterminer quel moteur de recherche est actuellement utilisé, exécutez la commande suivante :

```bash
./bin/magento config:show catalog/search/engine
```

Pour obtenir des instructions sur la configuration, consultez le Guide du développeur pour Adobe Commerce sur le cloud :

- [Configuration du service OpenSearch](https://devdocs.magento.com/cloud/project/services-opensearch.html)

- [Configuration du service Elasticsearch](https://devdocs.magento.com/cloud/project/services-elastic.html)

## Éviter les déclencheurs personnalisés

Si possible, évitez d’utiliser des déclencheurs personnalisés.

Les déclencheurs sont utilisés pour consigner les modifications dans les tables de contrôle. Adobe recommande de configurer l’application pour qu’elle écrive directement dans les tableaux d’audit au lieu d’utiliser la fonctionnalité de déclenchement pour les raisons suivantes :

- Les déclencheurs sont interprétés comme du code et MySQL ne les précompile pas. En se connectant à l’espace de transaction de votre requête, ils ajoutent la surcharge à un analyseur et à un interprète pour chaque requête effectuée avec la table.
- Les déclencheurs partagent le même espace de transaction que les requêtes d’origine, et tandis que ces requêtes se disputent les verrous sur la table, les déclencheurs se disputent indépendamment les verrous sur une autre table.

Pour en savoir plus sur les alternatives à l’utilisation de déclencheurs personnalisés, voir [Déclencheurs MySQL](mysql-configuration.md#triggers).

## Mettre à niveau [!DNL ECE-Tools] vers la version 2002.0.21 ou ultérieure {#ece-tools-version}

Pour éviter tout problème potentiel lié à des blocages cron, effectuez une mise à niveau de CEE-Tools vers la version 2002.0.21 ou ultérieure. Pour obtenir des instructions, voir [Mettre à jour `ece-tools` version](https://devdocs.magento.com/cloud/project/ece-tools-update.html) dans notre documentation destinée aux développeurs.

## Basculer le mode indexeur en toute sécurité

<!--This best practice might belong in the Maintenance phase. Database lock prevention might be consolidated under a single heading-->

Changement des indexeurs générés [!DNL data definition language] (DDL) pour créer des déclencheurs pouvant entraîner des verrous de base de données. Vous pouvez éviter ce problème en mettant votre site web en mode de maintenance et en désactivant les tâches cron avant de modifier la configuration.
Pour obtenir des instructions, voir [Configuration des indexeurs](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/manage-indexers.html#configure-indexers-1) dans le *Guide de configuration d’Adobe Commerce*.

## N’exécutez pas d’instructions DDL dans Production

Évitez d’exécuter des instructions DDL dans l’environnement de production pour éviter les conflits (comme les modifications et les créations de tableau). La variable `setup:upgrade` process est une exception.

Si vous devez exécuter une instruction DDL, mettez le site web en mode de maintenance et désactivez cron (voir les instructions pour changer d’index en toute sécurité dans la section précédente).

## Activer l’archivage des commandes

Activez l’archivage des commandes auprès de l’administrateur afin de réduire l’espace requis pour les tables de ventes au fur et à mesure que vos données de commande s’accroissent. L’archivage permet d’économiser de l’espace disque MySQL et d’améliorer les performances d’extraction.

Voir [Activer l’archivage](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/order-management/orders/order-archive.html) dans la documentation d’Adobe Commerce Merchant.

## Informations supplémentaires

- [Moteurs de stockage MySQL](https://dev.mysql.com/doc/refman/8.0/en/storage-engines.html)
- [Conditions préalables à la mise à niveau d’Adobe Commerce 2.3.5 pour MariaDB](../maintenance/commerce-235-upgrade-prerequisites-mariadb.md)
- [Bonnes pratiques pour résoudre les problèmes de performances de la base de données](../maintenance/resolve-database-performance-issues.md)
