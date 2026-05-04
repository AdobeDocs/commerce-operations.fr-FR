---
title: Migrer les données
description: Découvrez comment commencer à migrer des données de Magento 1 vers Magento 2 avec l’ [!DNL Data Migration Tool].
exl-id: f4ea8f6a-21f8-4db6-b598-c5efecec254f
topic: Commerce, Migration
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '337'
ht-degree: 0%

---

# Migrer les données

Avant de commencer, effectuez les étapes de préparation suivantes :

1. Connectez-vous au serveur d’applications en tant que [propriétaire du système de fichiers](../../../installation/prerequisites/file-system/overview.md).
1. Modifiez le répertoire d’installation de l’application ou assurez-vous qu’il est ajouté à votre `PATH` système.

Voir la section [premières étapes](overview.md#first-steps) pour plus d’informations.

## Exécutez la commande de migration des données

Pour commencer à migrer les données, exécutez :

```shell
bin/magento migrate:data [-r|--reset] [-a|--auto] {<path to config.xml>}
```

Où :

* `[-a|--auto]` est un argument facultatif qui empêche l’arrêt de la migration lorsqu’elle rencontre des erreurs de contrôle d’intégrité.

* `[-r|--reset]` est un argument facultatif qui lance la migration depuis le début. Vous pouvez utiliser cet argument pour tester la migration.

* `{<path to config.xml>}` est le chemin d’accès absolu au système de fichiers à `config.xml` ; cet argument est obligatoire

Au cours de cette étape, l’[!DNL Data Migration Tool] crée des tables et des déclencheurs supplémentaires pour les tables de migration dans la base de données Magento 1. Ils sont utilisés à l’étape de migration [incrémentale/delta](delta.md). Les tables supplémentaires contiennent des informations sur les enregistrements modifiés après l’exécution de la migration finale. Les déclencheurs de base de données sont utilisés pour remplir ces tables supplémentaires. Par conséquent, si une nouvelle opération est effectuée sur la table en question (un enregistrement est ajouté/modifié/supprimé), ces déclencheurs de base de données enregistrent des informations sur cette opération dans la table supplémentaire. Lorsque nous exécutons un processus de migration delta, le [!DNL Data Migration Tool] recherche les enregistrements non traités dans ces tables et migre le contenu nécessaire vers la base de données Magento 2.

Chaque nouveau tableau contient :

* préfixe `m2_cl`
* `INSERT`, `UPDATE`, `DELETE` déclencheurs d’événement.

Par exemple, pour le `sales_flat_order` créé par le [!DNL Data Migration Tool] :

* `m2_cl_sales_flat_order` table :

  ```sql
  CREATE TABLE `m2_cl_sales_flat_order` (
    `entity_id` int(11) NOT NULL COMMENT 'Entity_id',
    `operation` text COMMENT 'Operation',
    `processed` tinyint(1) NOT NULL DEFAULT '0' COMMENT 'Processed',
    PRIMARY KEY (`entity_id`)
  ) COMMENT='m2_cl_sales_flat_order';
  ```

* Déclencheurs `trg_sales_flat_order_after_insert`, `trg_sales_flat_order_after_update` et `trg_sales_flat_order_after_delete` :

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
>La [!DNL Data Migration Tool] enregistre sa progression en cours pendant son exécution. Si des erreurs ou une intervention de l’utilisateur l’arrêtent, l’outil reprend la progression au dernier état de fonctionnement connu. Pour forcer l’[!DNL Data Migration Tool] à s’exécuter depuis le début, utilisez l’argument `--reset` . Dans ce cas, nous vous recommandons de restaurer votre image mémoire de la base de données Magento 2 pour éviter de dupliquer les données précédemment migrées.


## Erreurs de cohérence possibles

Lors de l’exécution, le [!DNL Data Migration Tool] peut signaler des incohérences entre les bases de données Magento 1 et Magento 2, et afficher des messages tels que :

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

Voir la section [&#x200B; Dépannage &#x200B;](https://support.magento.com/hc/en-us/articles/360033020451) de ce guide pour plus d’informations et de recommandations.

## Étape de migration suivante

[Migrer les modifications](delta.md)
