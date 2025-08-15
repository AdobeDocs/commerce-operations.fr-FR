---
title: Conditions préalables à la mise à niveau d’Adobe Commerce pour MariaDB
description: Découvrez comment préparer votre base de données Adobe Commerce pour mettre à niveau MariaDB à partir d’une version précédente.
role: Developer
feature: Best Practices
exl-id: b86e471f-e81f-416b-a321-7aa1ac73d27c
source-git-commit: fb449f0ee7d503d0c7ba60bf6bfbe3f528060606
workflow-type: tm+mt
source-wordcount: '865'
ht-degree: 0%

---


# Conditions préalables à la mise à niveau pour MariaDB

Avant de mettre à niveau Adobe Commerce sur une infrastructure cloud, vous devrez peut-être également mettre à niveau votre logiciel de base de données si vous utilisez MariaDB. Par exemple :

- Adobe Commerce 2.4.6 avec MariaDB version 10.5.1 ou ultérieure
- Adobe Commerce 2.3.5 avec MariaDB version 10.3 ou antérieure

## Adobe Commerce 2.4.6

À partir de MariaDB 10.5.1, les colonnes avec d’anciens formats temporels sont marquées d’un commentaire `/* mariadb-5.3 */` dans la sortie des instructions `SHOW CREATE TABLE`, `SHOW COLUMNS` et `DESCRIBE`, ainsi que dans la colonne `COLUMN_TYPE` du tableau `INFORMATION_SCHEMA.COLUMNS`. [Voir la documentation MariaDB](https://mariadb.com/kb/en/datetime/#internal-format).

Adobe Commerce ne peut pas mapper les colonnes de date à un type de données approprié en raison du commentaire MariaDB, ce qui peut provoquer un comportement inattendu dans le code personnalisé.

Pour éviter tout comportement inattendu lors de la mise à niveau de MariaDB depuis les anciennes versions vers la version 10.6, Adobe recommande de migrer les colonnes vers le nouveau format interne.

### Configuration par défaut

Dans MariaDB 10.1.2, un nouveau format temporel a été introduit depuis MySQL 5.6. La variable système `mysql56_temporal_format` permet à la base de données de convertir automatiquement l&#39;ancien format de date en nouveau lorsqu&#39;une table de modification est exécutée ou qu&#39;une base de données est importée. La configuration par défaut de `mysql56_temporal_format` est toujours activée sur Adobe Commerce sur les infrastructures cloud.

### Migrer les colonnes de date

La requête suivante affiche la table et les colonnes concernées qui doivent être migrées après la mise à niveau de MariaDB vers la version 10.5.1 ou ultérieure :

```mysql
SELECT * FROM INFORMATION_SCHEMA.`COLUMNS` WHERE TABLE_SCHEMA = DATABASE() AND COLUMN_TYPE LIKE '%mariadb%';
```

Pour migrer les colonnes vers le nouveau format de date interne, il faut réimporter la base de données ou exécuter alter sur la colonne identifiée avec la même définition de colonne. La requête suivante génère les requêtes de modification nécessaires :

```mysql
SELECT CONCAT( 'ALTER TABLE `', COALESCE(TABLE_NAME), '`', ' MODIFY ', '`', COALESCE(COLUMN_NAME), '`', ' ', COALESCE(DATA_TYPE), ' ', IF(COALESCE(IS_NULLABLE)='YES','NULL', 'NOT NULL'), IF(COLUMN_DEFAULT IS NOT NULL,CONCAT(' DEFAULT ',COLUMN_DEFAULT),' '), ' ', COALESCE(EXTRA), ' COMMENT \'', COALESCE(COLUMN_COMMENT), '\';' ) as sql_query FROM INFORMATION_SCHEMA.`COLUMNS` WHERE TABLE_SCHEMA = DATABASE() AND COLUMN_TYPE LIKE '%mariadb%';
```

>[!NOTE]
>
>Il est important de migrer les colonnes vers le nouveau format de date interne _avant_ de déployer le nouveau code pour éviter tout comportement inattendu.

## Adobe Commerce 2.3.5

La mise à niveau du service MariaDB sur l’infrastructure cloud de la version 10.0 ou 10.2 vers la version 10.3, 10.4 ou 10.5. MariaDB version 10.3 et ultérieure nécessite que la base de données utilise le format de ligne de tableau dynamique et Adobe Commerce nécessite l’utilisation du moteur de stockage InnoDB pour les tableaux. Cet article explique comment mettre à jour votre base de données pour qu’elle soit conforme à ces exigences MariaDB.

Après avoir préparé la base de données, envoyez un ticket d’assistance Adobe Commerce pour mettre à jour la version du service MariaDB sur votre infrastructure cloud avant de poursuivre le processus de mise à niveau d’Adobe Commerce.

### Préparation de la base de données pour la mise à niveau

Avant que l’équipe d’assistance Adobe Commerce ne commence le processus de mise à niveau, préparez votre base de données en convertissant vos tables de base de données :

- Convertir le format de ligne de `COMPACT` en `DYNAMIC`
- Remplacez le moteur de stockage `MyISAM` par `InnoDB`

Gardez à l’esprit les points suivants lorsque vous planifiez la conversion :

- La conversion de `COMPACT` en tables `DYNAMIC` peut prendre plusieurs heures avec une base de données volumineuse.

- Pour éviter la corruption des données, ne terminez pas le travail de conversion sur un site actif.

- Effectuez le travail de conversion pendant une période de faible trafic sur votre site.

- Basculez votre site en [mode de maintenance](../../../installation/tutorials/maintenance-mode.md) avant d&#39;exécuter les commandes de conversion des tables de la base de données.

#### Convertir le format des lignes de la table de base de données

Vous pouvez convertir des tableaux sur un nœud de votre cluster. Les modifications sont répliquées automatiquement sur les autres nœuds de service.

1. Depuis votre environnement Adobe Commerce sur l’infrastructure cloud, utilisez SSH pour vous connecter au nœud 1.

1. Connectez-vous à MariaDB.

1. Identifier les tableaux à convertir du format compact au format dynamique.

   ```mysql
   SELECT table_name, row_format FROM information_schema.tables WHERE table_schema=DATABASE() and row_format = 'Compact';
   ```

1. Déterminez les tailles des tables afin de planifier le travail de conversion.

   ```mysql
   SELECT table_schema as 'Database', table_name AS 'Table', round(((data_length + index_length) / 1024 / 1024), 2) 'Size in MB' FROM information_schema.TABLES ORDER BY (data_length + index_length) DESC;
   ```

   La conversion des tableaux plus volumineux prend plus de temps. Passez en revue les tables et effectuez le travail de conversion par priorité et par taille de table pour planifier les fenêtres de maintenance requises.

1. Convertissez tous les tableaux au format dynamique un par un.

   ```mysql
   ALTER TABLE [ table name here ] ROW_FORMAT=DYNAMIC;
   ```

#### Convertir le format de stockage d&#39;une table de base de données

Vous pouvez convertir des tableaux sur un nœud de votre cluster. Les modifications sont répliquées automatiquement sur les autres nœuds de service.

Le processus de conversion du format de stockage est différent pour les projets Adobe Commerce Starter et Adobe Commerce Pro.

- Pour l’architecture Starter, utilisez la commande MySQL `ALTER` pour convertir le format .
- Sur l&#39;architecture Pro, utilisez les commandes MySQL `CREATE` et `SELECT` pour créer une table de base de données avec stockage `InnoDB` et copiez les données de la table existante dans la nouvelle table. Cette méthode garantit que les modifications sont répliquées sur tous les nœuds de votre cluster.

**Convertir le format de stockage de tableau pour les projets Adobe Commerce Pro**

1. Identifier les tables qui utilisent le stockage `MyISAM`.

   ```mysql
   SELECT table_name FROM INFORMATION_SCHEMA.TABLES WHERE engine = 'MyISAM';
   ```

1. Convertissez tous les tableaux `InnoDB` format de stockage un par un.

   - Renommez la table existante pour éviter les conflits de noms.

     ```mysql
     RENAME TABLE <existing_table> <table_old>;
     ```

   - Créez une table qui utilise le stockage `InnoDB` à l&#39;aide des données de la table existante.

     ```mysql
     CREATE TABLE <existing_table> ENGINE=InnoDB SELECT * from <table_old>;
     ```

   - Vérifiez que la nouvelle table contient toutes les données requises.

   - Supprimez le tableau d’origine que vous avez renommé.


**Convertir le format de stockage de tableau pour les projets Adobe Commerce Starter**

1. Identifier les tables qui utilisent le stockage `MyISAM`.

   ```mysql
   SELECT table_name FROM INFORMATION_SCHEMA.TABLES WHERE engine = 'MyISAM';
   ```

1. Convertissez les tableaux qui utilisent le stockage `MyISAM` en stockage `InnoDB`.

   ```mysql
   ALTER TABLE [ table name here ] ENGINE=InnoDB;
   ```

#### Vérifier la conversion de la base de données

La veille de la mise à niveau prévue vers MariaDB version 10.3, 10.4 ou 10.6, vérifiez que toutes les tables ont le bon format de ligne et le bon moteur de stockage. La vérification est requise, car les déploiements de code effectués après la conversion peuvent entraîner le rétablissement de la configuration d’origine de certaines tables.

1. Connectez-vous à votre base de données.

1. Recherchez les tableaux qui ont toujours le format de ligne `COMPACT`.

   ```mysql
   SELECT table_name, row_format FROM information_schema.tables WHERE table_schema=DATABASE() and row_format = 'Compact';
   ```

1. Recherchez les tables qui utilisent toujours le format de stockage `MyISAM`

   ```mysql
   SELECT table_name FROM INFORMATION_SCHEMA.TABLES WHERE engine = 'MyISAM';
   ```

1. Si des tableaux ont été rétablis, répétez les étapes pour modifier le format des lignes du tableau et le moteur de stockage.

### Modification du moteur de stockage

Voir [ Convertir des tables MyISAM en InnoDB](../planning/database-on-cloud.md).
