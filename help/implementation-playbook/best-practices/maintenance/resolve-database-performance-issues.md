---
title: Bonnes pratiques pour résoudre les problèmes de performances des bases de données
description: Découvrez comment résoudre les problèmes de base de données qui ralentissent les performances sur les sites Adobe Commerce déployés sur l’infrastructure cloud.
role: Developer, Admin
feature: Best Practices
exl-id: e40e0564-a4eb-43a8-89dd-9f6c5cedb4a7
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '541'
ht-degree: 0%

---

<!--Consider moving this topic to the Maintenance section-->

# Bonnes pratiques pour résoudre les problèmes de performances des bases de données

Cet article explique comment résoudre les problèmes de base de données qui ont un impact négatif sur les performances de la base de données sur Adobe Commerce sur les sites d’infrastructure cloud.

## Versions affectées

Adobe Commerce sur les infrastructures cloud

## Identifier et résoudre les requêtes à exécution longue

Déterminez si des requêtes MySQL s’exécutent lentement. En fonction de votre plan d’infrastructure cloud Adobe Commerce et donc de la disponibilité des outils, vous pouvez effectuer les opérations suivantes.

### Analyse des requêtes de base de données avec MySQL

Vous pouvez utiliser MySQL pour identifier et résoudre les requêtes à long terme sur n’importe quel projet d’infrastructure cloud d’Adobe Commerce.

1. Exécutez l’instruction [`SHOW \[FULL\] PROCESSLIST`](https://dev.mysql.com/doc/refman/8.0/en/show-processlist.html).
1. Si vous voyez des requêtes à long terme, exécutez [MySQL `EXPLAIN` et `EXPLAIN ANALYZE`](https://mysqlserverteam.com/mysql-explain-analyze/) pour chacune d’elles, afin de déterminer ce qui fait que la requête s’exécute pendant longtemps.
1. En fonction des problèmes détectés, prenez les mesures nécessaires pour corriger la requête afin qu’elle s’exécute plus rapidement.

### Analysez les requêtes à l&#39;aide de Percona Toolkit (pour l&#39;architecture Pro uniquement)

Si votre projet Adobe Commerce est déployé sur une architecture Pro, vous pouvez utiliser la boîte à outils Percona pour analyser les requêtes.

1. Exécutez la commande `pt-query-digest --type=slowlog` sur les journaux de requêtes lentes MySQL.
   * Pour trouver l’emplacement des journaux de requêtes lentes, voir **[!UICONTROL Log locations > Service Logs]**(https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/test/log-locations#service-logs) dans notre documentation destinée aux développeurs.
   * Consultez la documentation [Percona Toolkit > pt-query-digest](https://www.percona.com/doc/percona-toolkit/LATEST/pt-query-digest.html#pt-query-digest) .
1. En fonction des problèmes détectés, prenez les mesures nécessaires pour corriger la requête afin qu’elle s’exécute plus rapidement.

## Vérifier que toutes les tables possèdent une clé primaire

La définition de clés primaires est nécessaire pour une bonne conception de la base de données et des tables. Les clés de Principal permettent d’identifier de manière unique une seule ligne dans n’importe quel tableau.

Si vous disposez de tables sans clé primaire, le moteur de base de données par défaut d&#39;Adobe Commerce (InnoDB) utilise la première clé non nulle comme clé primaire. Si aucune clé unique n’est disponible, InnoDB crée une clé primaire masquée (6 octets). Le problème avec une clé primaire définie implicitement est que vous n’avez aucun contrôle sur celle-ci. En outre, la valeur implicite est affectée globalement à toutes les tables sans clés primaires. Cette configuration peut entraîner des problèmes de contention si vous effectuez des écritures simultanées sur ces tables. Cela peut entraîner des problèmes de performances, car les tables partagent également l’incrément d’index de clé primaire masqué global.

Pour éviter ces problèmes, définissez une clé primaire pour toutes les tables qui n&#39;en ont pas.

### Identification et mise à jour des tables sans clé primaire

1. Identifier les tables sans clé primaire à l&#39;aide de la requête SQL suivante :

   ```sql
   SELECT table_catalog, table_schema, table_name, engine FROM information_schema.tables        WHERE (table_catalog, table_schema, table_name) NOT IN (SELECT table_catalog, table_schema, table_name FROM information_schema.table_constraints  WHERE constraint_type = 'PRIMARY KEY') AND table_schema NOT IN ('information_schema', 'pg_catalog');    
   ```

1. Pour toute table dépourvue de clé primaire, ajoutez une clé primaire en mettant à jour le `db_schema.xml` (le schéma déclaratif) avec un nœud similaire au suivant :

   ```html
   <constraint xsi:type="primary" referenceId="PRIMARY">         <column name="id_column"/>     </constraint>    
   ```

   Lorsque vous ajoutez le nœud , remplacez les variables `referenceID` et `column name` par vos valeurs personnalisées.

Pour plus d’informations, consultez [Configuration du schéma déclaratif](https://developer.adobe.com/commerce/php/development/components/declarative-schema/configuration/) dans notre documentation destinée aux développeurs.

## Identification et suppression des index en double

Identifiez les index en double dans votre base de données et supprimez-les.

### Rechercher les index en double

Pour rechercher des index en double sur l’architecture cloud Pro ou Starter, exécutez la requête SQL suivante.

```sql
SELECT s.INDEXED_COL,GROUP_CONCAT(INDEX_NAME) FROM (SELECT INDEX_NAME,GROUP_CONCAT(CONCAT(TABLE_NAME,'.',COLUMN_NAME) ORDER BY CONCAT(SEQ_IN_INDEX,COLUMN_NAME)) 'INDEXED_COL' FROM INFORMATION_SCHEMA.STATISTICS WHERE TABLE_SCHEMA = 'db?' GROUP BY INDEX_NAME)as s GROUP BY INDEXED_COL HAVING COUNT(1)>1
```

La requête renvoie les noms des colonnes et les noms des index en double.

Les marchands d&#39;architecture Pro peuvent également exécuter la vérification à l&#39;aide de la commande Percona Toolkit `[pt-duplicate-key checker](https://www.percona.com/doc/percona-toolkit/LATEST/pt-duplicate-key-checker.html%C2%A0)`.

### Supprimer les index en double

Utilisez l&#39;instruction SQL [DROP INDEX](https://dev.mysql.com/doc/refman/8.0/en/drop-index.html) pour supprimer les index en double.

```SQL
DROP INDEX
```

## Informations supplémentaires

[Bonnes pratiques de configuration de la base de données pour les déploiements dans le cloud](../planning/database-on-cloud.md)
