---
title: Migration des données
description: Découvrez comment commencer la migration des données du Magento 1 vers le Magento 2 avec le  [!DNL Data Migration Tool].
exl-id: f4ea8f6a-21f8-4db6-b598-c5efecec254f
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '331'
ht-degree: 0%

---

# Migration des données

Avant de commencer, procédez comme suit pour préparer :

1. Connectez-vous à votre serveur d’applications en tant que [propriétaire du système de fichiers](../../../installation/prerequisites/file-system/overview.md).
1. Modifiez le répertoire d&#39;installation de l&#39;application ou assurez-vous qu&#39;il est ajouté à votre système `PATH`.

Pour plus d’informations, voir la section [premières étapes](overview.md#first-steps) .

## Exécution de la commande de migration des données

Pour commencer la migration des données, exécutez :

```bash
bin/magento migrate:data [-r|--reset] [-a|--auto] {<path to config.xml>}
```

Où :

* `[-a|--auto]` est un argument facultatif qui empêche l’arrêt de la migration lorsqu’elle rencontre des erreurs de vérification de l’intégrité.

* `[-r|--reset]` est un argument facultatif qui lance la migration à partir du début. Vous pouvez utiliser cet argument pour tester la migration.

* `{<path to config.xml>}` est le chemin d’accès absolu au système de fichiers vers `config.xml` ; cet argument est obligatoire.

Au cours de cette étape, [!DNL Data Migration Tool] crée des tables et des déclencheurs supplémentaires pour les tables de migration dans la base de données Magento 1. Ils sont utilisés dans l’étape de migration [incrémentielle/delta](delta.md). Les tableaux supplémentaires contiennent des informations sur les enregistrements modifiés après l’exécution finale de la migration. Les déclencheurs de base de données sont utilisés pour remplir ces tables supplémentaires. Ainsi, si une nouvelle opération est effectuée sur la table particulière (un enregistrement est ajouté/modifié/supprimé), cette base de données déclenche l’enregistrement des informations sur cette opération dans la table supplémentaire. Lors de l&#39;exécution d&#39;un processus de migration delta, [!DNL Data Migration Tool] recherche dans ces tables les enregistrements non traités et migre le contenu nécessaire dans la base de données Magento 2.

Chaque nouveau tableau contient :

* `m2_cl` préfixe
* `INSERT`, `UPDATE`, `DELETE` déclencheurs d’événement.

Par exemple, pour le `sales_flat_order`, le [!DNL Data Migration Tool] crée :

* table `m2_cl_sales_flat_order` :

  ```sql
  CREATE TABLE `m2_cl_sales_flat_order` (
    `entity_id` int(11) NOT NULL COMMENT 'Entity_id',
    `operation` text COMMENT 'Operation',
    `processed` tinyint(1) NOT NULL DEFAULT '0' COMMENT 'Processed',
    PRIMARY KEY (`entity_id`)
  ) COMMENT='m2_cl_sales_flat_order';
  ```

* `trg_sales_flat_order_after_insert`, `trg_sales_flat_order_after_update`, `trg_sales_flat_order_after_delete` déclencheurs :

  ```sql
  DELIMITER ;;
  CREATE TRIGGER `trg_sales_flat_order_after_insert` AFTER INSERT ON `sales_flat_order`
    FOR EACH ROW
    BEGIN
     INSERT INTO m2_cl_sales_flat_order (`entity_id`, `operation`) VALUES (NEW.entity_id, 'INSERT')ON DUPLICATE KEY UPDATE operation = 'INSERT';
    END
  ;;
  
  DELIMITER ;;
  CREATE TRIGGER `trg_sales_flat_order_after_update` AFTER UPDATE ON `sales_flat_order`
    FOR EACH ROW
    BEGIN
     INSERT INTO m2_cl_sales_flat_order (`entity_id`, `operation`) VALUES (NEW.entity_id, 'UPDATE') ON DUPLICATE KEY UPDATE operation = 'UPDATE';
    END
  ;;
  
  DELIMITER ;;
  CREATE TRIGGER `trg_sales_flat_order_after_delete` AFTER DELETE ON `sales_flat_order`
    FOR EACH ROW
    BEGIN
     INSERT INTO m2_cl_sales_flat_order (`entity_id`, `operation`) VALUES (OLD.entity_id, 'DELETE')ON DUPLICATE KEY UPDATE operation = 'DELETE';
    END
  ;;
  ```

>[!NOTE]
>
>Le [!DNL Data Migration Tool] enregistre sa progression actuelle lors de son exécution. Si des erreurs ou une intervention de l’utilisateur l’empêchent d’exécuter, l’outil reprend la progression au dernier état correct connu. Pour forcer l’exécution de [!DNL Data Migration Tool] à partir du début, utilisez l’argument `--reset`. Dans ce cas, nous vous recommandons de restaurer le vidage de la base de données Magento 2 afin d’éviter la duplication des données migrées précédemment.


## Erreurs de cohérence possibles

Lors de l’exécution, le [!DNL Data Migration Tool] peut signaler des incohérences entre les bases de données du Magento 1 et du Magento 2 et afficher des messages du type :

* `Source documents are missing: <EXTENSION_TABLE_1>,<EXTENSION_TABLE_2>,...<EXTENSION_TABLE_N>`
* `Destination documents are missing: <EXTENSION_TABLE_1>,<EXTENSION_TABLE_2>,...<EXTENSION_TABLE_N>`
* `Source documents are not mapped: <EXTENSION_TABLE_1>,<EXTENSION_TABLE_2>,...<EXTENSION_TABLE_N>`
* `Destination documents are not mapped: <EXTENSION_TABLE_1>,<EXTENSION_TABLE_2>,...<EXTENSION_TABLE_N>`
* `Source fields are missing. Document: <EXTENSION_TABLE>. Fields: <FIELD_1>,<FIELD_2>...<FIELD_N>`
* `Destination fields are missing. Document: <EXTENSION_TABLE>. Fields: <FIELD_1>,<FIELD_2>...<FIELD_N>`
* `Source fields are not mapped. Document: <EXTENSION_TABLE>. Fields: <FIELD_1>,<FIELD_2>...<FIELD_N>`
* `Destination fields are not mapped. Document: <EXTENSION_TABLE>. Fields: <FIELD_1>,<FIELD_2>...<FIELD_N>`
* `Mismatch of data types. Source document: <EXTENSION_TABLE>. Fields: <FIELD_1>,<FIELD_2>...<FIELD_N>`
* `Mismatch of data types. Destination document: <EXTENSION_TABLE>. Fields: <FIELD_1>,<FIELD_2>...<FIELD_N>`
* `Incompatibility in data. Source document: <EXTENSION_TABLE>. Field: <FIELD>. Error: <ERROR_MESSAGE>`
* `Incompatibility in data. Destination document: <EXTENSION_TABLE>. Field: <FIELD>. Error: <ERROR_MESSAGE>`

Pour plus d’informations et de recommandations, consultez la section [Dépannage](https://support.magento.com/hc/en-us/articles/360033020451) de ce guide.

## Étape suivante de migration

[Migrer les modifications](delta.md)
