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

Avant de mettre à niveau Adobe Commerce sur l’infrastructure cloud, vous devrez peut-être également mettre à niveau votre logiciel de base de données si vous utilisez MariaDB. Par exemple :

- Adobe Commerce 2.4.6 avec MariaDB version 10.5.1 ou ultérieure
- Adobe Commerce 2.3.5 avec MariaDB version 10.3 ou antérieure

## Adobe Commerce 2.4.6

À partir de MariaDB 10.5.1, les colonnes avec d’anciens formats temporels sont marquées avec un commentaire `/* mariadb-5.3 */` dans la sortie des instructions `SHOW CREATE TABLE`, `SHOW COLUMNS`, `DESCRIBE`, ainsi que dans la colonne `COLUMN_TYPE` de la table `INFORMATION_SCHEMA.COLUMNS`. [Voir la documentation MariaDB](https://mariadb.com/kb/en/datetime/#internal-format).

Adobe Commerce n’est pas en mesure de mapper les colonnes de dates à un type de données approprié en raison du commentaire MariaDB, ce qui peut entraîner un comportement inattendu dans le code personnalisé.

Pour éviter tout comportement inattendu lors de la mise à niveau de MariaDB d’anciennes versions vers la version 10.6, Adobe recommande de migrer les colonnes vers le nouveau format interne.

### Configuration par défaut

Dans MariaDB 10.1.2, un nouveau format temporel a été introduit à partir de MySQL 5.6. La variable système `mysql56_temporal_format` permet à la base de données de convertir automatiquement l’ancien format de date en nouveau lors de l’exécution d’une autre table ou de l’import d’une base de données. La configuration par défaut de `mysql56_temporal_format` est toujours activée sur Adobe Commerce sur l’infrastructure cloud.

### Migrer les colonnes de dates

La requête suivante affiche la table et les colonnes concernées qui doivent être migrées après la mise à niveau de MariaDB vers la version 10.5.1 ou ultérieure :

```mysql
SELECT * FROM INFORMATION_SCHEMA.`COLUMNS` WHERE TABLE_SCHEMA = DATABASE() AND COLUMN_TYPE LIKE '%mariadb%';
```

La migration des colonnes vers le nouveau format de date interne nécessite un réimport de la base de données ou l&#39;exécution de l&#39;autre sur la colonne identifiée avec la même définition de colonne. La requête suivante génère les requêtes alter nécessaires :

```mysql
SELECT CONCAT( 'ALTER TABLE `', COALESCE(TABLE_NAME), '`', ' MODIFY ', '`', COALESCE(COLUMN_NAME), '`', ' ', COALESCE(DATA_TYPE), ' ', IF(COALESCE(IS_NULLABLE)='YES','NULL', 'NOT NULL'), IF(COLUMN_DEFAULT IS NOT NULL,CONCAT(' DEFAULT ',COLUMN_DEFAULT),' '), ' ', COALESCE(EXTRA), ' COMMENT \'', COALESCE(COLUMN_COMMENT), '\';' ) as sql_query FROM INFORMATION_SCHEMA.`COLUMNS` WHERE TABLE_SCHEMA = DATABASE() AND COLUMN_TYPE LIKE '%mariadb%';
```

>[!NOTE]
>
>Il est important de migrer les colonnes vers le nouveau format de date interne _avant_ le déploiement du nouveau code afin d’éviter tout comportement inattendu.

## Adobe Commerce 2.3.5

La mise à niveau du service MariaDB sur l’infrastructure cloud de la version 10.0 ou 10.2 vers la version 10.3, 10.4 ou 10.5. MariaDB version 10.3 et ultérieure nécessite que la base de données utilise le format de ligne de tableau dynamique et Adobe Commerce requiert l’utilisation du moteur de stockage InnoDB pour les tables. Cet article explique comment mettre à jour votre base de données pour se conformer à ces exigences MariaDB.

Après avoir préparé la base de données, soumettez un ticket de support Adobe Commerce pour mettre à jour la version du service MariaDB sur votre infrastructure cloud avant de poursuivre le processus de mise à niveau d’Adobe Commerce.

### Préparation de la base de données pour la mise à niveau

Avant que l’équipe d’assistance Adobe Commerce ne commence le processus de mise à niveau, préparez votre base de données en convertissant vos tables de base de données :

- Convertir le format des lignes de `COMPACT` à `DYNAMIC`
- Remplacez le moteur de stockage `MyISAM` par `InnoDB`

Tenez compte des points suivants lorsque vous planifiez et planifiez la conversion :

- La conversion de `COMPACT` en `DYNAMIC` tables peut prendre plusieurs heures avec une base de données volumineuse.

- Pour éviter la corruption des données, ne terminez pas le travail de conversion sur un site actif.

- Terminez le travail de conversion pendant une période de faible trafic sur votre site.

- Passez votre site en [mode de maintenance](../../../installation/tutorials/maintenance-mode.md) avant d’exécuter les commandes pour convertir les tables de base de données.

#### Conversion du format des lignes du tableau de la base de données

Vous pouvez convertir des tableaux sur un noeud de la grappe. Les modifications se répliquent automatiquement sur les autres noeuds de service.

1. Dans votre environnement d’infrastructure cloud Adobe Commerce, utilisez SSH pour vous connecter au noeud 1.

1. Connectez-vous à MariaDB.

1. Identifiez les tableaux à convertir au format compact ou dynamique.

   ```mysql
   SELECT table_name, row_format FROM information_schema.tables WHERE table_schema=DATABASE() and row_format = 'Compact';
   ```

1. Déterminez les tailles de tableau afin de planifier le travail de conversion.

   ```mysql
   SELECT table_schema as 'Database', table_name AS 'Table', round(((data_length + index_length) / 1024 / 1024), 2) 'Size in MB' FROM information_schema.TABLES ORDER BY (data_length + index_length) DESC;
   ```

   La conversion de tableaux plus volumineux prend plus de temps. Passez en revue les tableaux et effectuez par lots le travail de conversion par priorité et par taille de tableau pour planifier les fenêtres de maintenance requises.

1. Convertissez tous les tableaux au format dynamique un par un.

   ```mysql
   ALTER TABLE [ table name here ] ROW_FORMAT=DYNAMIC;
   ```

#### Conversion du format de stockage des tables de la base de données

Vous pouvez convertir des tableaux sur un noeud de la grappe. Les modifications se répliquent automatiquement sur les autres noeuds de service.

Le processus de conversion du format de stockage est différent pour les projets Adobe Commerce Starter et Adobe Commerce Pro.

- Pour l’architecture de démarrage, utilisez la commande MySQL `ALTER` pour convertir le format.
- Sur l’architecture Pro, utilisez les commandes MySQL `CREATE` et `SELECT` pour créer une table de base de données avec le stockage `InnoDB` et copier les données de la table existante dans la nouvelle table. Cette méthode garantit que les modifications sont répliquées sur tous les noeuds de la grappe.

**Convert table storage format for Adobe Commerce Pro projects**

1. Identifiez les tables qui utilisent le stockage `MyISAM`.

   ```mysql
   SELECT table_name FROM INFORMATION_SCHEMA.TABLES WHERE engine = 'MyISAM';
   ```

1. Convertissez toutes les tables au format de stockage `InnoDB` une par une.

   - Renommez la table existante pour éviter tout conflit de nom.

     ```mysql
     RENAME TABLE <existing_table> <table_old>;
     ```

   - Créez une table qui utilise le stockage `InnoDB` à l&#39;aide des données de la table existante.

     ```mysql
     CREATE TABLE <existing_table> ENGINE=InnoDB SELECT * from <table_old>;
     ```

   - Vérifiez que le nouveau tableau contient toutes les données requises.

   - Supprimez la table d’origine que vous avez renommée.


**Convert table storage format for Adobe Commerce Starter projects**

1. Identifiez les tables qui utilisent le stockage `MyISAM`.

   ```mysql
   SELECT table_name FROM INFORMATION_SCHEMA.TABLES WHERE engine = 'MyISAM';
   ```

1. Convertissez les tables qui utilisent le stockage `MyISAM` en stockage `InnoDB`.

   ```mysql
   ALTER TABLE [ table name here ] ENGINE=InnoDB;
   ```

#### Vérifier la conversion de la base de données

La veille de la mise à niveau programmée vers la version 10.3, 10.4 ou 10.6 de MariaDB, vérifiez que tous les tableaux ont le format de ligne et le moteur de stockage appropriés. La vérification est requise, car les déploiements de code effectués après la conversion peuvent entraîner le rétablissement de la configuration d’origine de certains tableaux.

1. Connectez-vous à votre base de données.

1. Recherchez les tableaux qui ont toujours le format de ligne `COMPACT`.

   ```mysql
   SELECT table_name, row_format FROM information_schema.tables WHERE table_schema=DATABASE() and row_format = 'Compact';
   ```

1. Recherchez les tables qui utilisent toujours le format de stockage `MyISAM`.

   ```mysql
   SELECT table_name FROM INFORMATION_SCHEMA.TABLES WHERE engine = 'MyISAM';
   ```

1. Si des tableaux ont été restaurés, répétez les étapes pour modifier le format des rangées de tableau et le moteur de stockage.

### Modification du moteur de stockage

Voir [ Conversion des tables MyISAM en InnoDB](../planning/database-on-cloud.md).
