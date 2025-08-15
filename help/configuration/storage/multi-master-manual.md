---
title: Configuration manuelle des bases de données principales
description: Voir les conseils sur la configuration manuelle de la solution de base de données partagée.
recommendations: noCatalog
exl-id: 2c357486-4a8a-4a36-9e13-b53c83f69456
source-git-commit: af45ac46afffeef5cd613628b2a98864fd7da69b
workflow-type: tm+mt
source-wordcount: '1373'
ht-degree: 0%

---

# Configuration manuelle des bases de données principales

{{ee-only}}

{{deprecate-split-db}}

Si l’application Commerce est déjà en production ou si vous avez déjà installé du code personnalisé ou des composants, vous devrez peut-être configurer manuellement les bases de données fractionnées. Avant de poursuivre, contactez l’assistance Adobe Commerce pour voir si cela est nécessaire dans votre cas.

Le fractionnement manuel de bases de données implique :

- Créer les bases de données du système de gestion des commandes (OMS)
- Exécutez une série de scripts SQL qui :

   - Déposer les clés étrangères
   - Sauvegarder les tables de la base de données des ventes et des devis
   - Déplacer des tables de votre base de données principale vers les bases de données de ventes et de devis

>[!WARNING]
>
>Si un code personnalisé utilise des JOINTURES avec des tables dans les bases de données de ventes et de devis, vous _ne pouvez pas_ utiliser des bases de données fractionnées. En cas de doute, contactez les auteurs de code personnalisé ou d’extensions pour vous assurer que leur code n’utilise pas les jointures.

Cette rubrique utilise les conventions de dénomination suivantes :

- Le nom de la base de données principale est `magento` et ses nom d&#39;utilisateur et mot de passe sont tous deux `magento`
- Le nom de la base de données de guillemets est `magento_quote` et ses nom d&#39;utilisateur et mot de passe sont tous deux `magento_quote`

  La base de données de devis est également appelée base de données _checkout_.

- Le nom de la base de données des ventes est `magento_sales` et ses nom d&#39;utilisateur et mot de passe sont tous deux `magento_sales`

  La base de données des ventes est également appelée base de données OMS.

>[!INFO]
>
>Ce guide suppose que les trois bases de données se trouvent sur le même hôte que l’application Commerce. Cependant, le choix de l&#39;emplacement des bases de données et de leur nom dépend de vous. Nous espérons que nos exemples rendront les instructions plus faciles à suivre.

## Sauvegarde du système Commerce

Adobe vous recommande vivement de sauvegarder votre base de données et votre système de fichiers actuels afin de pouvoir les restaurer en cas de problèmes au cours du processus.

**Pour sauvegarder votre système** :

1. Connectez-vous à votre serveur Commerce en tant que [propriétaire du système de fichiers](../../installation/prerequisites/file-system/overview.md) ou passez à ce dernier.
1. Saisissez les commandes suivantes :

   ```bash
   magento setup:backup --code --media --db
   ```

1. Passez à la section suivante.

## Configurer des bases de données principales supplémentaires

Cette section explique comment créer des instances de base de données pour les tables de ventes et de devis.

**Pour créer des bases de données de devis de vente et OMS** :

1. Connectez-vous à votre serveur de base de données en tant qu&#39;utilisateur.
1. Saisissez la commande suivante pour accéder à une invite de commande MySQL :

   ```bash
   mysql -u root -p
   ```

1. Entrez le mot de passe de l&#39;utilisateur MySQL `root` lorsque vous y êtes invité.
1. Saisissez les commandes suivantes dans l’ordre indiqué pour créer des instances de base de données appelées `magento_quote` et `magento_sales` avec les mêmes noms d’utilisateur et mots de passe :

   ```shell
   create database magento_quote;
   GRANT ALL ON magento_quote.* TO magento_quote@localhost IDENTIFIED BY 'magento_quote';
   ```

   ```shell
   create database magento_sales;
   GRANT ALL ON magento_sales.* TO magento_sales@localhost IDENTIFIED BY 'magento_sales';
   ```

1. Saisissez `exit` pour quitter l’invite de commande.

1. Vérifiez les bases de données une par une :

   base de données de devis :

   ```bash
   mysql -u magento_quote -p
   ```

   ```shell
   exit
   ```

   ```bash
   mysql -u magento_quote -p
   ```

   ```bash
   mysql -u magento_sales -p
   ```

   ```shell
   exit
   ```

   Si le moniteur MySQL s’affiche, vous avez créé la base de données correctement. Si une erreur s’affiche, répétez les commandes précédentes.

1. Passez à la section suivante.

## Configuration de la base de données des ventes

Cette section explique comment créer et exécuter des scripts SQL qui modifient des tables de base de données de guillemets et sauvegardent les données de ces tables.

Les noms des tables de la base de données des ventes commencent par :

- `salesrule_`
- `sales_`
- `magento_sales_`
- La table `magento_customercustomattributes_sales_flat_order` est également affectée

>[!INFO]
>
>Cette section contient des scripts avec des noms de table de base de données spécifiques. Si vous avez effectué des personnalisations ou souhaitez afficher la liste complète des tables avant d’effectuer des actions sur celles-ci, reportez-vous à la section [Scripts de référence](#reference-scripts).

Pour plus d’informations, voir :

- [Création de scripts SQL pour la base de données des ventes](#create-sales-database-sql-scripts)
- [Sauvegarder les données de vente](#back-up-sales-data)

### Création de scripts SQL pour la base de données des ventes

Créez les scripts SQL suivants à un emplacement accessible par l’utilisateur pour lequel vous vous connectez à votre serveur Commerce. Par exemple, si vous vous connectez ou exécutez des commandes en tant que `root`, vous pouvez créer les scripts dans le répertoire `/root/sql-scripts`.

#### Supprimer les clés étrangères

Ce script supprime de la base de données sales les clés étrangères qui font référence à des tables hors ventes.

Créez le script suivant et donnez-lui un nom tel que `1_foreign-sales.sql`. Remplacez `<your main DB name>` par le nom de votre base de données.

```sql
use <your main DB name>;
ALTER TABLE salesrule_coupon_aggregated_order DROP FOREIGN KEY SALESRULE_COUPON_AGGREGATED_ORDER_STORE_ID_STORE_STORE_ID;
ALTER TABLE salesrule_coupon_aggregated DROP FOREIGN KEY SALESRULE_COUPON_AGGREGATED_STORE_ID_STORE_STORE_ID;
ALTER TABLE salesrule_coupon_aggregated_updated DROP FOREIGN KEY SALESRULE_COUPON_AGGREGATED_UPDATED_STORE_ID_STORE_STORE_ID;
ALTER TABLE salesrule_coupon_usage DROP FOREIGN KEY SALESRULE_COUPON_USAGE_CUSTOMER_ID_CUSTOMER_ENTITY_ENTITY_ID;
ALTER TABLE salesrule_customer_group DROP FOREIGN KEY SALESRULE_CSTR_GROUP_CSTR_GROUP_ID_CSTR_GROUP_CSTR_GROUP_ID;
ALTER TABLE salesrule_customer DROP FOREIGN KEY SALESRULE_CUSTOMER_CUSTOMER_ID_CUSTOMER_ENTITY_ENTITY_ID;
ALTER TABLE salesrule_label DROP FOREIGN KEY SALESRULE_LABEL_STORE_ID_STORE_STORE_ID;
ALTER TABLE salesrule_product_attribute DROP FOREIGN KEY SALESRULE_PRD_ATTR_ATTR_ID_EAV_ATTR_ATTR_ID;
ALTER TABLE salesrule_product_attribute DROP FOREIGN KEY SALESRULE_PRD_ATTR_CSTR_GROUP_ID_CSTR_GROUP_CSTR_GROUP_ID;
ALTER TABLE salesrule_product_attribute DROP FOREIGN KEY SALESRULE_PRODUCT_ATTRIBUTE_WEBSITE_ID_STORE_WEBSITE_WEBSITE_ID;
ALTER TABLE salesrule_website DROP FOREIGN KEY SALESRULE_WEBSITE_WEBSITE_ID_STORE_WEBSITE_WEBSITE_ID;
ALTER TABLE sales_bestsellers_aggregated_daily DROP FOREIGN KEY SALES_BESTSELLERS_AGGRED_DAILY_PRD_ID_CAT_PRD_ENTT_ENTT_ID;
ALTER TABLE sales_bestsellers_aggregated_monthly DROP FOREIGN KEY SALES_BESTSELLERS_AGGRED_MONTHLY_PRD_ID_CAT_PRD_ENTT_ENTT_ID;
ALTER TABLE sales_bestsellers_aggregated_yearly DROP FOREIGN KEY SALES_BESTSELLERS_AGGRED_YEARLY_PRD_ID_CAT_PRD_ENTT_ENTT_ID;
ALTER TABLE sales_bestsellers_aggregated_daily DROP FOREIGN KEY SALES_BESTSELLERS_AGGREGATED_DAILY_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_bestsellers_aggregated_monthly DROP FOREIGN KEY SALES_BESTSELLERS_AGGREGATED_MONTHLY_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_bestsellers_aggregated_yearly DROP FOREIGN KEY SALES_BESTSELLERS_AGGREGATED_YEARLY_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_creditmemo_grid DROP FOREIGN KEY SALES_CREDITMEMO_GRID_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_creditmemo DROP FOREIGN KEY SALES_CREDITMEMO_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_invoiced_aggregated_order DROP FOREIGN KEY SALES_INVOICED_AGGREGATED_ORDER_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_invoiced_aggregated DROP FOREIGN KEY SALES_INVOICED_AGGREGATED_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_invoice_grid DROP FOREIGN KEY SALES_INVOICE_GRID_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_invoice DROP FOREIGN KEY SALES_INVOICE_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_order_aggregated_created DROP FOREIGN KEY SALES_ORDER_AGGREGATED_CREATED_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_order_aggregated_updated DROP FOREIGN KEY SALES_ORDER_AGGREGATED_UPDATED_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_order DROP FOREIGN KEY SALES_ORDER_CUSTOMER_ID_CUSTOMER_ENTITY_ENTITY_ID;
ALTER TABLE sales_order_grid DROP FOREIGN KEY SALES_ORDER_GRID_CUSTOMER_ID_CUSTOMER_ENTITY_ENTITY_ID;
ALTER TABLE sales_order_grid DROP FOREIGN KEY SALES_ORDER_GRID_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_order_item DROP FOREIGN KEY SALES_ORDER_ITEM_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_order_status_label DROP FOREIGN KEY SALES_ORDER_STATUS_LABEL_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_order DROP FOREIGN KEY SALES_ORDER_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_refunded_aggregated_order DROP FOREIGN KEY SALES_REFUNDED_AGGREGATED_ORDER_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_refunded_aggregated DROP FOREIGN KEY SALES_REFUNDED_AGGREGATED_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_shipment_grid DROP FOREIGN KEY SALES_SHIPMENT_GRID_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_shipment DROP FOREIGN KEY SALES_SHIPMENT_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_shipping_aggregated_order DROP FOREIGN KEY SALES_SHIPPING_AGGREGATED_ORDER_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_shipping_aggregated DROP FOREIGN KEY SALES_SHIPPING_AGGREGATED_STORE_ID_STORE_STORE_ID;
ALTER TABLE magento_sales_creditmemo_grid_archive DROP FOREIGN KEY MAGENTO_SALES_CREDITMEMO_GRID_ARCHIVE_STORE_ID_STORE_STORE_ID;
ALTER TABLE magento_sales_invoice_grid_archive DROP FOREIGN KEY MAGENTO_SALES_INVOICE_GRID_ARCHIVE_STORE_ID_STORE_STORE_ID;
ALTER TABLE magento_sales_order_grid_archive DROP FOREIGN KEY MAGENTO_SALES_ORDER_GRID_ARCHIVE_CSTR_ID_CSTR_ENTT_ENTT_ID;
ALTER TABLE magento_sales_order_grid_archive DROP FOREIGN KEY MAGENTO_SALES_ORDER_GRID_ARCHIVE_STORE_ID_STORE_STORE_ID;
ALTER TABLE magento_sales_shipment_grid_archive DROP FOREIGN KEY MAGENTO_SALES_SHIPMENT_GRID_ARCHIVE_STORE_ID_STORE_STORE_ID;
ALTER TABLE downloadable_link_purchased_item DROP FOREIGN KEY DL_LNK_PURCHASED_ITEM_ORDER_ITEM_ID_SALES_ORDER_ITEM_ITEM_ID;
ALTER TABLE downloadable_link_purchased DROP FOREIGN KEY DOWNLOADABLE_LINK_PURCHASED_ORDER_ID_SALES_ORDER_ENTITY_ID;
ALTER TABLE paypal_billing_agreement_order DROP FOREIGN KEY PAYPAL_BILLING_AGREEMENT_ORDER_ORDER_ID_SALES_ORDER_ENTITY_ID;
```

### Configuration de la base de données des ventes

Exécutez le script précédent :

1. Connectez-vous à votre base de données MySQL en tant qu’utilisateur `root` ou administrateur :

   ```bash
   mysql -u root -p
   ```

1. À l’invite `mysql>`, exécutez le script comme suit :

   ```shell
   source <path>/<script>.sql
   ```

   Par exemple,

   ```shell
   source /root/sql-scripts/1_foreign-sales.sql
   ```

1. Après l’exécution du script, saisissez `exit`.

### Sauvegarder les données de vente

Cette section explique comment sauvegarder les tables de ventes de la base de données Commerce principale afin de les restaurer dans une base de données de ventes distincte.

Si vous êtes actuellement à l’invite de `mysql>`, saisissez `exit` pour revenir au shell de commande.

Exécutez les commandes `mysqldump` suivantes, une par une, à partir du shell de commande. Dans chaque fichier, remplacez ce qui suit :

- `<your database root username>` avec le nom de l&#39;utilisateur racine de votre base de données
- `<your database root user password>` avec le mot de passe de l’utilisateur
- `<your main Commerce DB name>` avec le nom de votre base de données Commerce
- `<path>` avec un chemin d&#39;accès en écriture au système de fichiers

#### Script 1

```bash
mysqldump -u <your database root username> -p <your main Commerce DB name> sales_bestsellers_aggregated_daily sales_bestsellers_aggregated_monthly sales_bestsellers_aggregated_yearly sales_creditmemo sales_creditmemo_comment sales_creditmemo_grid sales_creditmemo_item sales_invoice sales_invoice_comment sales_invoice_grid sales_invoice_item sales_invoiced_aggregated sales_invoiced_aggregated_order sales_order sales_order_address sales_order_aggregated_created sales_order_aggregated_updated sales_order_grid sales_order_item sales_order_payment sales_order_status sales_order_status_history sales_order_status_label sales_order_status_state sales_order_tax sales_order_tax_item sales_payment_transaction sales_refunded_aggregated sales_refunded_aggregated_order sales_sequence_meta sales_sequence_profile sales_shipment sales_shipment_comment sales_shipment_grid sales_shipment_item sales_shipment_track sales_shipping_aggregated sales_shipping_aggregated_order > /<path>/sales.sql
```

#### Script 2

```bash
mysqldump -u <your database root username> -p <your main Commerce DB name> magento_sales_creditmemo_grid_archive magento_sales_invoice_grid_archive magento_sales_order_grid_archive magento_sales_shipment_grid_archive > /<path>/salesarchive.sql
```

#### Script 3

```bash
mysqldump -u <your database root username> -p <your main Commerce DB name> magento_customercustomattributes_sales_flat_order magento_customercustomattributes_sales_flat_order_address > /<path>/customercustomattributes.sql
```

#### Script 4

```bash
mysqldump -u <your database root username> -p <your main Commerce DB name> sequence_creditmemo_0 sequence_creditmemo_1 sequence_invoice_0 sequence_invoice_1 sequence_order_0 sequence_order_1 sequence_rma_item_0 sequence_rma_item_1 sequence_shipment_0 sequence_shipment_1 > /<path>/sequence.sql
```

### Restaurer les données de vente

Ce script restaure les données de vente dans votre base de données de devis.

#### Exigence NDB

Si vous utilisez un cluster [Network Database (NDB)](https://dev.mysql.com/doc/refman/5.6/en/mysql-cluster.html) :

1. Convertissez les tableaux de InnoDb en type NDB dans les fichiers de vidage :

   ```bash
   sed -ei 's/InnoDb/NDB/' <file name>.sql
   ```

1. Supprimez les lignes comportant une clé FULLTEXT des images mémoire, car les tableaux NDB ne prennent pas en charge le texte intégral.

#### Restaurer les données

Exécutez les commandes suivantes :

```bash
mysql -u <root username> -p <your sales DB name> < /<path>/sales.sql
```

```bash
mysql -u <root username> -p <your sales DB name> < /<path>/sequence.sql
```

```bash
mysql -u <root username> -p <your sales DB name> < /<path>/salesarchive.sql
```

```bash
mysql -u <root username> -p <your sales DB name> < /<path>/customercustomattributes.sql
```

Où

- `<your sales DB name>` avec le nom de votre base de données de ventes.

  Dans cette rubrique, le nom de l&#39;exemple de base de données est `magento_sales`.

- `<root username>` avec votre nom d’utilisateur racine MySQL
- `<root user password>` avec le mot de passe de l’utilisateur
- Vérifiez l’emplacement des fichiers de sauvegarde que vous avez créés précédemment (par exemple, `/var/sales.sql`)

## Configuration de la base de données de devis

Cette section décrit les tâches requises pour supprimer des clés étrangères des tables de la base de données des ventes et déplacer des tables vers la base de données des ventes.

>[!INFO]
>
>Cette section contient des scripts avec des noms de table de base de données spécifiques. Si vous avez effectué des personnalisations ou souhaitez afficher la liste complète des tables avant d’effectuer des actions sur celles-ci, reportez-vous à la section [Scripts de référence](#reference-scripts).

Les noms des tables de la base de données entre guillemets commencent par `quote`. Les tableaux `magento_customercustomattributes_sales_flat_quote` et `magento_customercustomattributes_sales_flat_quote_address` sont également affectés

### Déposer les clés étrangères des tables de guillemets

Ce script supprime les clés étrangères qui font référence aux tables hors guillemets des tables entre guillemets. Remplacez `<your main Commerce DB name>` par le nom de votre base de données Commerce.

Créez le script suivant et donnez-lui un nom tel que `2_foreign-key-quote.sql` :

```sql
use <your main DB name>;
ALTER TABLE quote DROP FOREIGN KEY QUOTE_STORE_ID_STORE_STORE_ID;
ALTER TABLE quote_item DROP FOREIGN KEY QUOTE_ITEM_PRODUCT_ID_CATALOG_PRODUCT_ENTITY_ENTITY_ID;
ALTER TABLE quote_item DROP FOREIGN KEY QUOTE_ITEM_STORE_ID_STORE_STORE_ID;
```

Exécutez le script comme suit :

1. Connectez-vous à votre base de données MySQL en tant qu’utilisateur racine ou administrateur :

   ```bash
   mysql -u root -p
   ```

1. À l’invite `mysql >`, exécutez le script comme suit :
   `source <path>/<script>.sql`

   Par exemple,

   ```shell
   source /root/sql-scripts/2_foreign-key-quote.sql
   ```

1. Une fois le script exécuté, saisissez `exit`.

### Sauvegarder les tables de devis

Cette section explique comment sauvegarder les tables de devis de la base de données principale et les restaurer dans votre base de données de devis.

Exécutez la commande suivante à partir d’une invite de commande :

```bash
mysqldump -u <your database root username> -p <your main Commerce DB name> magento_customercustomattributes_sales_flat_quote magento_customercustomattributes_sales_flat_quote_address quote quote_address quote_address_item quote_item quote_item_option quote_payment quote_shipping_rate quote_id_mask > /<path>/quote.sql;
```

### Exigence NDB

Si vous utilisez un cluster [Network Database (NDB)](https://dev.mysql.com/doc/refman/5.6/en/mysql-cluster.html) :

1. Convertissez les tableaux de InnoDb en type NDB dans les fichiers de vidage :

   ```bash
   sed -ei 's/InnoDb/NDB/' <file name>.sql
   ```

1. Supprimez les lignes comportant une clé FULLTEXT des images mémoire, car les tableaux NDB ne prennent pas en charge le texte intégral.

### Restaurer les tables dans la base de données des guillemets

```bash
mysql -u root -p magento_quote < /<path>/quote.sql
```

## Déposer les tables de ventes et de devis de la base de données

Ce script contient les tables de ventes et de devis de la base de données Commerce. Remplacez `<your main DB name>` par le nom de votre base de données Commerce.

Créez le script suivant et donnez-lui un nom tel que `3_drop-tables.sql` :

```sql
use <your main DB name>;
SET foreign_key_checks = 0;
DROP TABLE magento_customercustomattributes_sales_flat_quote;
DROP TABLE magento_customercustomattributes_sales_flat_quote_address;
DROP TABLE quote;
DROP TABLE quote_address;
DROP TABLE quote_address_item;
DROP TABLE quote_item;
DROP TABLE quote_item_option;
DROP TABLE quote_payment;
DROP TABLE quote_shipping_rate;
DROP TABLE quote_id_mask;
DROP TABLE sales_bestsellers_aggregated_daily;
DROP TABLE sales_bestsellers_aggregated_monthly;
DROP TABLE sales_bestsellers_aggregated_yearly;
DROP TABLE sales_creditmemo;
DROP TABLE sales_creditmemo_comment;
DROP TABLE sales_creditmemo_grid;
DROP TABLE sales_creditmemo_item;
DROP TABLE sales_invoice;
DROP TABLE sales_invoice_comment;
DROP TABLE sales_invoice_grid;
DROP TABLE sales_invoice_item;
DROP TABLE sales_invoiced_aggregated;
DROP TABLE sales_invoiced_aggregated_order;
DROP TABLE sales_order;
DROP TABLE sales_order_address;
DROP TABLE sales_order_aggregated_created;
DROP TABLE sales_order_aggregated_updated;
DROP TABLE sales_order_grid;
DROP TABLE sales_order_item;
DROP TABLE sales_order_payment;
DROP TABLE sales_order_status;
DROP TABLE sales_order_status_history;
DROP TABLE sales_order_status_label;
DROP TABLE sales_order_status_state;
DROP TABLE sales_order_tax;
DROP TABLE sales_order_tax_item;
DROP TABLE sales_payment_transaction;
DROP TABLE sales_refunded_aggregated;
DROP TABLE sales_refunded_aggregated_order;
DROP TABLE sales_sequence_meta;
DROP TABLE sales_sequence_profile;
DROP TABLE sales_shipment;
DROP TABLE sales_shipment_comment;
DROP TABLE sales_shipment_grid;
DROP TABLE sales_shipment_item;
DROP TABLE sales_shipment_track;
DROP TABLE sales_shipping_aggregated;
DROP TABLE sales_shipping_aggregated_order;
DROP TABLE magento_sales_creditmemo_grid_archive;
DROP TABLE magento_sales_invoice_grid_archive;
DROP TABLE magento_sales_order_grid_archive;
DROP TABLE magento_sales_shipment_grid_archive;
DROP TABLE magento_customercustomattributes_sales_flat_order;
DROP TABLE magento_customercustomattributes_sales_flat_order_address;
DROP TABLE sequence_creditmemo_0;
DROP TABLE sequence_creditmemo_1;
DROP TABLE sequence_invoice_0;
DROP TABLE sequence_invoice_1;
DROP TABLE sequence_order_0;
DROP TABLE sequence_order_1;
DROP TABLE sequence_rma_item_0;
DROP TABLE sequence_rma_item_1;
DROP TABLE sequence_shipment_0;
DROP TABLE sequence_shipment_1;
SET foreign_key_checks = 1;
```

Exécutez le script comme suit :

1. Connectez-vous à votre base de données MySQL en tant qu’utilisateur racine ou administrateur :

   ```bash
   mysql -u root -p
   ```

1. À l’invite `mysql>`, exécutez le script comme suit :

   ```shell
   source <path>/<script>.sql
   ```

   Par exemple,

   ```shell
   source /root/sql-scripts/3_drop-tables.sql
   ```

1. Une fois le script exécuté, saisissez `exit`.

## Mise à jour de la configuration de déploiement

La dernière étape du fractionnement manuel des bases de données consiste à ajouter des informations de connexion et de ressource à la configuration de déploiement de Commerce, `env.php`.

Pour mettre à jour la configuration de déploiement :

1. Connectez-vous à votre serveur Commerce en tant que [propriétaire du système de fichiers](../../installation/prerequisites/file-system/overview.md) ou passez à ce dernier.
1. Sauvegardez la configuration de déploiement :

   ```bash
   cp <magento_root>/app/etc/env.php <magento_root>/app/etc/env.php.orig
   ```

1. Ouvrez `<magento_root>/app/etc/env.php` dans un éditeur de texte et mettez-le à jour en suivant les instructions décrites dans les sections suivantes.

### Mettre à jour les connexions à la base de données

Localisez le bloc commençant par `'default'` (sous `'connection'`) et ajoutez les sections `'checkout'` et `'sales'` . Remplacez les exemples de valeurs par les valeurs appropriées pour votre site.

```php
 'default' =>
      array (
'host' => 'localhost',
'dbname' => 'magento',
'username' => 'magento',
'password' => 'magento',
'model' => 'mysql4',
'engine' => 'innodb',
'initStatements' => 'SET NAMES utf8;',
'active' => '1',
      ),
      'checkout' =>
      array (
'host' => 'localhost',
'dbname' => 'magento_quote',
'username' => 'magento_quote',
'password' => 'magento_quote',
'model' => 'mysql4',
'engine' => 'innodb',
'initStatements' => 'SET NAMES utf8;',
'active' => '1',
      ),
      'sales' =>
      array (
'host' => 'localhost',
'dbname' => 'magento_sales',
'username' => 'magento_sales',
'password' => 'magento_sales',
'model' => 'mysql4',
'engine' => 'innodb',
'initStatements' => 'SET NAMES utf8;',
'active' => '1',
      ),
    ),
```

### Mise à jour des ressources

Localisez le bloc commençant par `'resource'` et ajoutez-y des sections `'checkout'` et `'sales'` comme suit :

```php
'resource' =>
  array (
    'default_setup' =>
    array (
      'connection' => 'default',
    ),
    'checkout' =>
    array (
      'connection' => 'checkout',
    ),
    'sales' =>
    array (
      'connection' => 'sales',
    ),
```

## Scripts de référence

Cette section fournit des scripts que vous pouvez exécuter et qui impriment une liste complète des tables concernées sans y effectuer d&#39;actions. Vous pouvez les utiliser pour voir quelles tables sont affectées avant de fractionner manuellement des bases de données, ce qui peut s&#39;avérer utile si vous utilisez des extensions qui personnalisent le schéma de base de données.

Pour utiliser ces scripts :

1. Créez un script SQL avec le contenu de chaque script dans cette section.
1. Dans chaque script, remplacez `<your main DB name>` par le nom de votre base de données Commerce.

   Dans cette rubrique, le nom de l&#39;exemple de base de données est `magento`.

1. Exécutez chaque script de l’invite de `mysql>` comme `source <script name>`
1. Examinez la sortie.
1. Copiez le résultat de chaque script dans un autre script SQL, en supprimant les caractères de barre verticale (`|`).
1. Exécutez chaque script de l’invite de `mysql>` comme `source <script name>`.

   L’exécution de ce second script exécute les actions dans votre base de données Commerce principale.

### Supprimer les clés étrangères (tables de ventes)

Ce script supprime de la base de données sales les clés étrangères qui font référence à des tables hors ventes.

```sql
select concat(
    'ALTER TABLE ',
    replace(for_name, '<your main DB name>/', ''),
    ' DROP FOREIGN KEY ',
    replace(id, '<your main DB name>/', ''),
    ';'
    )
from information_schema.INNODB_SYS_FOREIGN
where for_name like  '<your main DB name>/|sales_%' escape '|'
    and ref_name not like  '<your main DB name>/|sales_%' escape '|'
union all
select concat(
    'ALTER TABLE ',
    replace(for_name, '<your main DB name>/', ''),
    ' DROP FOREIGN KEY ',
    replace(id, '<your main DB name>/', ''),
    ';'
    )
from information_schema.INNODB_SYS_FOREIGN
where for_name like  '<your main DB name>/|magento_sales|_%' escape '|'
    and ref_name not like  '<your main DB name>/|sales|_%' escape '|'
;
```

### Supprimer les clés étrangères (guillemets)

Ce script supprime les clés étrangères qui font référence aux tables hors guillemets des tables entre guillemets.

```sql
select concat(
    'ALTER TABLE ',
    replace(for_name, '<your main DB name>/', ''),
    ' DROP FOREIGN KEY ',
    replace(id, '<your main DB name>/', ''),
    ';'
    )
from information_schema.INNODB_SYS_FOREIGN
where for_name like '<your main DB name>/%'
    and ref_name like '<your main DB name>/sales\_%'
union all
select concat(
    'ALTER TABLE ',
    replace(for_name, '<your main DB name>/', ''),
    ' DROP FOREIGN KEY ',
    replace(id, '<your main DB name>/', ''),
    ';'
    )
from information_schema.INNODB_SYS_FOREIGN
where for_name like '<your main DB name>/%'
    and ref_name like '<your main DB name>/magento_sales\_%'
union all
select concat(
    'ALTER TABLE ',
    replace(for_name, '<your main DB name>/', ''),
    ' DROP FOREIGN KEY ',
    replace(id, '<your main DB name>/', ''),
    ';'
    )
from information_schema.INNODB_SYS_FOREIGN
where for_name like '<your main DB name>/%'
    and ref_name like '<your main DB name>/magento_customercustomattributes\_%'
;
```

### Déposer les tables de ventes

Ce script supprime les tables de ventes de la base de données Commerce.

```sql
use <your main DB name>;
select ' SET foreign_key_checks = 0;' as querytext
union all
select
    concat('DROP TABLE IF EXISTS ' , table_name, ';')
from information_schema.tables
where table_schema = '<your main DB name>'
and table_name like 'sales/_%' escape '/'
union all
select
    concat('DROP TABLE IF EXISTS ' , table_name, ';')
from information_schema.tables
where table_schema = '<your main DB name>'
and table_name like 'magento_sales/_%' escape '/'
union all
select
    concat('DROP TABLE IF EXISTS ' , table_name, ';')
from information_schema.tables
where table_schema = '<your main DB name>'
and table_name like 'magento_customercustomattributes_sales_flat_order%' escape '/'
union all
select
    concat('DROP TABLE IF EXISTS ' , table_name, ';')
from information_schema.tables
where table_schema = '<your main DB name>'
and table_name like 'sequence/_%' escape '/'
union all
select 'SET foreign_key_checks = 1;';
```

### Déposer les tables de guillemets

Supprimez tous les tableaux commençant par `quote_`.
