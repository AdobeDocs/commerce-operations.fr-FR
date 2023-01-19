---
title: Conditions préalables à la mise à niveau d’Adobe Commerce 2.3.5 pour MariaDB
description: Découvrez comment préparer la mise à niveau de votre base de données Adobe Commerce à partir d’Adobe Commerce 2.3.5.
role: Developer
feature-set: Commerce
feature: Best Practices
source-git-commit: 35efea20181b112e97bfae803c8d0168cfc88dfc
workflow-type: tm+mt
source-wordcount: '562'
ht-degree: 0%

---


# Conditions préalables à la mise à niveau vers Adobe Commerce 2.3.5

Cet article explique comment préparer votre base de données lors de la mise à niveau vers Adobe Commerce 2.3.5 à partir de la version 2.3.4 ou antérieure.

Cette mise à niveau nécessite que l’équipe de support mette à niveau MariaDB sur l’infrastructure cloud de MariaDB 10.0 vers 10.2 pour répondre aux exigences d’Adobe Commerce version 2.3.5 et ultérieure.

## Produit et versions concernés

Adobe Commerce sur l’infrastructure cloud avec Adobe Commerce version 2.3.4 ou antérieure et MariaDB version 10.0 ou antérieure.

## Préparation de la base de données pour la mise à niveau

Avant que l’équipe d’assistance Adobe Commerce ne commence le processus de mise à niveau, préparez votre base de données en convertissant vos tables de base de données :

- Convertir le format des lignes à partir de `COMPACT` to `DYNAMIC`
- Convertir le moteur de stockage à partir de `MyISAM` to `InnoDB`

Tenez compte des points suivants lorsque vous planifiez et planifiez la conversion :

- Conversion à partir de `COMPACT` to `DYNAMIC` Les tables peuvent prendre plusieurs heures avec une base de données volumineuse.

- Pour éviter la corruption des données, ne terminez pas le travail de conversion sur un site actif.

- Terminez le travail de conversion pendant une période de faible trafic sur votre site.

- Basculez votre site vers [mode de maintenance](../../../installation/tutorials/maintenance-mode.md) avant d’exécuter les commandes pour convertir les tables de base de données.

### Conversion du format des lignes du tableau de la base de données

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

### Conversion du format de stockage des tables de la base de données

Vous pouvez convertir des tableaux sur un noeud de la grappe. Les modifications se répliquent automatiquement sur les autres noeuds de service.

Le processus de conversion du format de stockage diffère pour les projets Adobe Commerce Starter et Adobe Commerce Pro.

- Pour l’architecture de démarrage, utilisez MySQL. `ALTER` pour convertir le format.
- Sur l’architecture Pro, utilisez MySQL. `CREATE` et `SELECT` commandes pour créer une table de base de données avec `InnoDB` stockez et copiez les données de la table existante dans la nouvelle table. Cette méthode garantit que les modifications sont répliquées sur tous les noeuds de la grappe.

**Conversion du format de stockage de tableau pour les projets Adobe Commerce Pro**

1. Identifier les tableaux qui utilisent `MyISAM` stockage.

   ```mysql
   SELECT table_name FROM INFORMATION_SCHEMA.TABLES WHERE engine = 'MyISAM';
   ```

1. Convertir tous les tableaux en `InnoDB` format de stockage un par un.

   - Renommez la table existante pour éviter tout conflit de nom.

      ```mysql
      RENAME TABLE <existing_table> <table_old>;
      ```

   - Créer un tableau qui utilise `InnoDB` stockage à partir des données de la table existante.

      ```mysql
      CREATE TABLE <existing_table> ENGINE=InnoDB SELECT * from <table_old>;
      ```

   - Vérifiez que le nouveau tableau contient toutes les données requises.

   - Supprimez la table d’origine que vous avez renommée.


**Conversion du format de stockage de tableau pour les projets Adobe Commerce Starter**

1. Identifier les tableaux qui utilisent `MyISAM` stockage.

   ```mysql
   SELECT table_name FROM INFORMATION_SCHEMA.TABLES WHERE engine = 'MyISAM';
   ```

1. Conversion de tableaux utilisant `MyISAM` stockage vers `InnoDB` stockage.

   ```mysql
   ALTER TABLE [ table name here ] ENGINE=InnoDB;
   ```

### Vérifier la conversion de la base de données

La veille de la mise à niveau prévue vers la version 10.2 de MariaDB, vérifiez que tous les tableaux ont le format de ligne et le moteur de stockage appropriés. La vérification est requise, car les déploiements de code effectués après la conversion peuvent entraîner le rétablissement de la configuration d’origine de certains tableaux.

1. Connectez-vous à votre base de données.

1. Recherchez les tables qui ont toujours le `COMPACT` format de ligne.

   ```mysql
   SELECT table_name, row_format FROM information_schema.tables WHERE table_schema=DATABASE() and row_format = 'Compact';
   ```

1. Recherchez les tables qui utilisent toujours la variable `MyISAM` format de stockage

   ```mysql
   SELECT table_name FROM INFORMATION_SCHEMA.TABLES WHERE engine = 'MyISAM';
   ```

1. Si des tableaux ont été restaurés, répétez les étapes pour modifier le format des rangées de tableau et le moteur de stockage.

## Informations supplémentaires

[Bonnes pratiques relatives aux bases de données pour Adobe Commerce sur l’infrastructure cloud](../planning/database-on-cloud.md)
