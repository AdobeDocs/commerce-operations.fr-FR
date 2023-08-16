---
title: Bonnes pratiques pour résoudre les problèmes de performances de la base de données
description: Découvrez comment résoudre les problèmes de base de données qui ralentissent les performances des sites Adobe Commerce déployés sur l’infrastructure cloud.
role: Developer, Admin
feature: Best Practices
exl-id: e40e0564-a4eb-43a8-89dd-9f6c5cedb4a7
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '570'
ht-degree: 0%

---

<!--Consider moving this topic to the Maintenance section-->

# Bonnes pratiques pour résoudre les problèmes de performances de la base de données

Cet article explique comment résoudre les problèmes de base de données qui ont un impact négatif sur les performances de la base de données sur Adobe Commerce sur les sites d’infrastructure cloud.

## Versions affectées

Adobe Commerce sur l’infrastructure cloud

## Identification et résolution de requêtes longues

Déterminez si les requêtes MySQL s’exécutent lentement. En fonction de votre plan d’infrastructure cloud Adobe Commerce et donc de la disponibilité des outils, vous pouvez effectuer les opérations suivantes.

### Analyse des requêtes de base de données avec MySQL

Vous pouvez utiliser MySQL pour identifier et résoudre des requêtes longues sur n’importe quel projet d’infrastructure cloud d’Adobe Commerce.

1. Exécutez la variable [`SHOW \[FULL\] PROCESSLIST`](https://dev.mysql.com/doc/refman/8.0/en/show-processlist.html) .
1. Si vous voyez des requêtes longues, exécutez [MySQL `EXPLAIN` et `EXPLAIN ANALYZE`](https://mysqlserverteam.com/mysql-explain-analyze/) pour chacun d’entre eux, pour savoir ce qui fait que la requête s’exécute pendant longtemps.
1. En fonction des problèmes détectés, suivez les étapes pour corriger la requête afin qu’elle s’exécute plus rapidement.

### Analyse des requêtes à l’aide de Percona Toolkit (pour l’architecture Pro uniquement)

Si votre projet Adobe Commerce est déployé sur l’architecture Pro, vous pouvez utiliser Percona Toolkit pour analyser les requêtes.

1. Exécutez la variable `pt-query-digest --type=slowlog` par rapport aux journaux de requête lents MySQL.
   * Pour connaître l’emplacement des journaux de requête lente, voir **[!UICONTROL Log locations > Service Logs]**(https://devdocs.magento.com/cloud/project/log-locations.html#service-logs) dans notre documentation destinée aux développeurs.
   * Voir [Percona Toolkit > pt-query-digest](https://www.percona.com/doc/percona-toolkit/LATEST/pt-query-digest.html#pt-query-digest) la documentation.
1. En fonction des problèmes détectés, suivez les étapes pour corriger la requête afin qu’elle s’exécute plus rapidement.

## Vérification de la présence d’une clé primaire pour toutes les tables

La définition de clés primaires est une exigence pour une bonne conception de base de données et de tableau. Les clés de Principal permettent d’identifier de manière unique une ligne d’un tableau.

Si vous disposez de tables sans clé primaire, le moteur de base de données par défaut pour Adobe Commerce (InnoDB) utilise la première clé non nulle unique comme clé primaire. Si aucune clé unique n’est disponible, InnoDB crée une clé primaire masquée (6 octets). Le problème avec une clé primaire implicitement définie est que vous n’en avez pas le contrôle. En outre, la valeur implicite est affectée globalement à toutes les tables sans clés primaires. Cette configuration peut entraîner des problèmes de conflit si vous effectuez des écritures simultanées sur ces tables. Cela peut entraîner des problèmes de performances, car les tables partagent également l’incrément d’index de clé primaire masqué global.

Empêchez ces problèmes en définissant une clé primaire pour toutes les tables qui n’en ont pas.

### Identifier et mettre à jour les tables sans clé primaire

1. Identifiez les tables sans clé primaire à l&#39;aide de la requête SQL suivante :

   ```sql
   SELECT table_catalog, table_schema, table_name, engine FROM information_schema.tables        WHERE (table_catalog, table_schema, table_name) NOT IN (SELECT table_catalog, table_schema, table_name FROM information_schema.table_constraints  WHERE constraint_type = 'PRIMARY KEY') AND table_schema NOT IN ('information_schema', 'pg_catalog');    
   ```

1. Pour toute table ne comportant pas de clé primaire, ajoutez une clé primaire en mettant à jour la variable `db_schema.xml` (le schéma déclaratif) avec un noeud similaire à ce qui suit :

   ```html
   <constraint xsi:type="primary" referenceId="PRIMARY">         <column name="id_column"/>     </constraint>    
   ```

   Lorsque vous ajoutez le noeud, remplacez le `referenceID` et `column name` avec vos valeurs personnalisées.

Pour plus d’informations, voir [Configuration du schéma déclaratif](https://developer.adobe.com/commerce/php/development/components/declarative-schema/configuration/) dans notre documentation destinée aux développeurs.

## Identification et suppression des index en double

Identifiez les index en double dans votre base de données et supprimez-les.

### Vérification des index en double

Pour rechercher des index en double sur l’architecture cloud Pro ou Starter, exécutez la requête SQL suivante.

```sql
SELECT s.INDEXED_COL,GROUP_CONCAT(INDEX_NAME) FROM (SELECT INDEX_NAME,GROUP_CONCAT(CONCAT(TABLE_NAME,'.',COLUMN_NAME) ORDER BY CONCAT(SEQ_IN_INDEX,COLUMN_NAME)) 'INDEXED_COL' FROM INFORMATION_SCHEMA.STATISTICS WHERE TABLE_SCHEMA = 'db?' GROUP BY INDEX_NAME)as s GROUP BY INDEXED_COL HAVING COUNT(1)>1
```

La requête renvoie les noms des colonnes et les noms des index en double.

Les marchands d’architecture Pro peuvent également exécuter la vérification à l’aide de Percona Toolkit  `[pt-duplicate-key checker](https://www.percona.com/doc/percona-toolkit/LATEST/pt-duplicate-key-checker.html%C2%A0)` .

### Suppression des index en double

Utilisation du langage SQL [Instruction DROP INDEX](https://dev.mysql.com/doc/refman/8.0/en/drop-index.html) pour supprimer les index en double.

```SQL
DROP INDEX
```

## Informations supplémentaires

[Bonnes pratiques de configuration de base de données pour les déploiements cloud](../planning/database-on-cloud.md)
