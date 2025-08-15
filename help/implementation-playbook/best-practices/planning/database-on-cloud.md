---
title: Bonnes pratiques de configuration de la base de données pour les déploiements dans le cloud
description: Découvrez comment configurer les paramètres de la base de données et de l’application pour améliorer les performances lors du déploiement d’Adobe Commerce sur une infrastructure cloud.
role: Developer, Admin
feature: Best Practices
exl-id: ca377dc8-c8bd-4f77-a24b-22a298e2bba4
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '651'
ht-degree: 0%

---

# Bonnes pratiques relatives à la configuration de la base de données

Découvrez les bonnes pratiques pour améliorer les performances de la base de données et utiliser efficacement cette dernière lors du déploiement d’Adobe Commerce sur une infrastructure cloud.

## Produits concernés

Adobe Commerce sur les infrastructures cloud

## Convertir toutes les tables MyISAM en InnoDB

Adobe recommande d’utiliser le moteur de base de données InnoDB. Dans une installation Adobe Commerce par défaut, toutes les tables de la base de données sont stockées à l’aide du moteur InnoDB. Cependant, certains modules tiers (extensions) peuvent introduire des tableaux au format MyISAM. Après avoir installé un module tiers, vérifiez la base de données pour identifier les tables au format `myisam` et les convertir au format `innodb`.

### Déterminer si un module comprend des tables MyISAM

Vous pouvez analyser le code du module tiers avant de l’installer afin de déterminer s’il utilise des tables MyISAM.

Si vous avez déjà installé une extension, exécutez la requête suivante pour déterminer si la base de données contient des tables MyISAM :

```sql
SELECT table_schema, CONCAT(ROUND((index_length+data_length)/1024/1024),'MB')
    AS total_size FROM information_schema. TABLES WHERE engine='myisam' AND table_schema
    NOT IN ('mysql', 'information_schema', 'performance_schema', 'sys');
```

### Remplacer le moteur de stockage par InnoDB

Dans le fichier `db_schema.xml` qui déclare la table, définissez la valeur de l’attribut `engine` pour le nœud `table` correspondant sur `innodb`. Pour référence, consultez [Configuration du schéma déclaratif > nœud de tableau](https://developer.adobe.com/commerce/php/development/components/declarative-schema/configuration/) dans notre documentation destinée aux développeurs.

Le schéma déclaratif a été introduit dans Adobe Commerce sur l’infrastructure cloud version 2.3.

## Configuration du moteur de recherche recommandé pour la recherche MySQL native

Adobe vous recommande de toujours configurer Elasticsearch ou OpenSearch pour votre projet d’infrastructure cloud Adobe Commerce, même si vous envisagez de configurer un outil de recherche tiers pour votre application Adobe Commerce. Cette configuration fournit une option de secours en cas d’échec de l’outil de recherche tiers.

Le moteur de recherche que vous utilisez dépend de la version d’Adobe Commerce sur le cloud installée :

- Pour Adobe Commerce 2.4.4 et versions ultérieures, utilisez le service OpenSearch pour une recherche MySQL native.

- Pour les versions antérieures d’Adobe Commerce, utilisez Elasticsearch.

Pour déterminer le moteur de recherche actuellement utilisé, exécutez la commande suivante :

```bash
./bin/magento config:show catalog/search/engine
```

Pour obtenir des instructions de configuration, consultez le Guide du développeur pour Adobe Commerce sur le cloud :

- [Configurer le service OpenSearch](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/service/opensearch)

- [Configurer le service Elasticsearch](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/service/elasticsearch)

## Éviter les déclencheurs personnalisés

Dans la mesure du possible, évitez d’utiliser des déclencheurs personnalisés.

Des déclencheurs sont utilisés pour consigner les modifications dans les tables d&#39;audit. Adobe recommande de configurer l’application pour qu’elle écrive directement dans les tables d’audit au lieu d’utiliser la fonctionnalité de déclenchement, et ce pour les raisons suivantes :

- Les Triggers sont interprétés comme du code et MySQL ne les précompile pas. En se connectant à l’espace de transaction de votre requête, ils ajoutent la surcharge à un analyseur et à un interpréteur pour chaque requête effectuée avec la table.
- Les déclencheurs partagent le même espace de transaction que les requêtes d&#39;origine et, tandis que ces requêtes sont en concurrence pour les verrous sur la table, les déclencheurs sont en concurrence indépendante pour les verrous sur une autre table.

Pour en savoir plus sur les alternatives à l’utilisation de déclencheurs personnalisés, voir [Déclencheurs MySQL](mysql-configuration.md#triggers).

## Mettre à niveau [!DNL ECE-Tools] vers la version 2002.0.21 ou ultérieure {#ece-tools-version}

Pour éviter des problèmes potentiels avec les blocages cron, mettez à niveau ECE-Tools vers la version 2002.0.21 ou supérieure. Pour obtenir des instructions, consultez [Mise à jour de `ece-tools` version](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/update-package) dans notre documentation destinée aux développeurs.

## Basculer en mode indexeur en toute sécurité

<!--This best practice might belong in the Maintenance phase. Database lock prevention might be consolidated under a single heading-->

Le changement d’indexeur génère des instructions [!DNL data definition language] (DDL) pour créer des déclencheurs susceptibles de provoquer des verrous de base de données. Vous pouvez éviter ce problème en mettant votre site web en mode de maintenance et en désactivant les tâches cron avant de modifier la configuration.
Pour obtenir des instructions, consultez [Configuration des indexeurs](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/manage-indexers.html#configure-indexers-1) dans le *Guide de configuration d’Adobe Commerce*.

## N’exécutez pas les instructions DDL dans Production

Évitez d’exécuter des instructions DDL dans l’environnement de production pour éviter les conflits (comme les modifications et les créations de tables). Le processus `setup:upgrade` est une exception.

Si vous devez exécuter une instruction DDL, placez le site web en mode de maintenance et désactivez cron (voir les instructions pour changer d’index en toute sécurité dans la section précédente).

## Activer l’archivage des commandes

Activez l’archivage des commandes auprès de l’administrateur afin de réduire l’espace requis pour les tables de ventes à mesure que les données de commande augmentent. L’archivage permet de gagner de l’espace disque MySQL et d’améliorer les performances de passage en caisse.

Voir [Activer l’archivage](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/order-management/orders/order-archive.html) dans la documentation pour les commerçants Adobe Commerce.

## Informations supplémentaires

- [Moteurs de stockage MySQL](https://dev.mysql.com/doc/refman/8.0/en/storage-engines.html)
- [Conditions préalables à la mise à niveau d’Adobe Commerce 2.3.5 pour MariaDB](../maintenance/mariadb-upgrade.md)
- [Bonnes pratiques pour résoudre les problèmes de performances des bases de données](../maintenance/resolve-database-performance-issues.md)
