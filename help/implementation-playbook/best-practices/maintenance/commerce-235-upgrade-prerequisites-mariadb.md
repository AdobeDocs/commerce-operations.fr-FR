---
title: Conditions préalables à la mise à niveau d’Adobe Commerce 2.3.5 pour MariaDB
description: Découvrez comment préparer la mise à niveau de votre base de données Adobe Commerce à partir d’Adobe Commerce 2.3.5.
role: Developer
feature-set: Commerce
feature: Best Practices
source-git-commit: 1abe86197de68336e10c50cab7ad38eebb098aeb
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 0%

---


# Conditions préalables à la mise à niveau vers Adobe Commerce 2.3.5

Cet article explique comment préparer votre base de données lors de la mise à niveau vers Adobe Commerce 2.3.5 à partir de la version 2.3.4 ou antérieure.

Cette mise à niveau nécessite que l’équipe de support mette à niveau MariaDB sur l’infrastructure cloud de MariaDB 10.0 vers 10.2 pour répondre aux exigences d’ Adobe Commerce . Adobe Commerce version 2.3.5 et ultérieure.

## Produit et versions concernés

Adobe Commerce sur l’infrastructure cloud avec Adobe Commerce version 2.3.4 ou antérieure et MariaDB version 10.0 ou antérieure.

## Préparation de la base de données pour la mise à niveau

Avant que l’équipe d’assistance d’Adobe Commerce ne commence le processus de mise à niveau, vous devez préparer votre base de données en convertissant le format de tous les tableaux de `COMPACT` to `DYNAMIC`. Vous devez également convertir le type de moteur de stockage à partir de `MyISAM` to `InnoDB`.

Gardez les instructions suivantes à l’esprit lorsque vous créez le plan et le planning de conversion de la base de données.

- Conversion à partir de `COMPACT` to `DYNAMIC` Les tables peuvent prendre plusieurs heures avec une base de données volumineuse.

- Pour éviter toute corruption des données, n’effectuez pas la conversion lorsque votre site est actif.

- Terminez le travail de conversion pendant une période de faible trafic sur votre site.

- Basculez votre site vers [mode de maintenance](../../../installation/tutorials/maintenance-mode.md) avant d’exécuter la fonction `ALTER` des commandes.

### Conversion de tables de base de données

Vous pouvez convertir des tableaux sur un noeud de la grappe. Les modifications seront répliquées sur les autres noeuds principaux de la grappe.

1. Dans votre environnement d’infrastructure cloud Adobe Commerce, utilisez SSH pour vous connecter au noeud 1.

1. Connectez-vous à MariaDB.

1. Convertir le format du tableau.

   - Identifiez les tableaux à convertir au format compact ou dynamique.

      ```mysql
      SELECT table_name, row_format FROM information_schema.tables WHERE table_schema=DATABASE() and row_format 'Compact';
      ```

   - Déterminez les tailles de tableau afin de planifier le travail de conversion.

      ```mysql
      SELECT table_schema as 'Database', table_name AS 'Table', round(((data_length + index_length) / 1024 / 1024), 2) 'Size in MB' FROM information_schema.TABLES ORDER BY (data_length + index_length) DESC;
      ```

      La conversion de tableaux plus volumineux prend plus de temps. Planifiez en conséquence, lorsque vous amenez votre site en mode de maintenance ou en dehors de celui-ci, les lots de tables à convertir dans quel ordre, afin de planifier les délais des fenêtres de maintenance nécessaires.

   - Convertissez tous les tableaux au format dynamique un par un.

      ```mysql
      ALTER TABLE [ table name here ] ROW_FORMAT=DYNAMIC;
      ```

1. Mettez à jour le moteur de stockage de table.

   - Identifier les tableaux qui utilisent `MyISAM` stockage.

      ```mysql
      SELECT table_name FROM INFORMATION_SCHEMA.TABLES WHERE engine = 'MyISAM';
      ```

   - Conversion de tableaux utilisant `MyISAM` stockage vers `InnoDB` stockage.

      ```mysql
      ALTER TABLE [ table name here ] ENGINE=InnoDB;
      ```

1. Vérifiez la conversion.

   Cette étape est nécessaire, car les déploiements de code effectués après la conversion peuvent entraîner le rétablissement de la configuration d’origine de certains tableaux.

   - La veille de la mise à niveau prévue vers MariaDB version 10.2, connectez-vous à votre base de données et exécutez les requêtes pour vérifier le format et le moteur de stockage.

      ```mysql
      SELECT table_name, row_format FROM information_schema.tables WHERE table_schema=DATABASE() and row_format = 'Compact';
      ```

      ```mysql
      SELECT table_name FROM INFORMATION_SCHEMA.TABLES WHERE engine = 'MyISAM';
      ```

   - Si des tables ont été restaurées, répétez les étapes pour modifier le format de la table et le moteur de stockage.

## Informations supplémentaires

[Bonnes pratiques relatives aux bases de données pour Adobe Commerce sur l’infrastructure cloud](../planning/database-on-cloud.md)
