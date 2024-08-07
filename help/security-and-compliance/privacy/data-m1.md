---
title: Référence des informations personnelles du client (version 1.x)
description: Découvrez les mappages des flux de données et des entités de base de données pour les informations personnelles des clients dans Magento 1.x.
exl-id: 8b01418d-8ca1-48fc-9577-a324ed3109d1
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '715'
ht-degree: 0%

---

# Référence des informations personnelles du client (version 1.x)

>[!NOTE]
>
>Il s’agit d’une rubrique parmi d’autres destinée à aider les marchands et les développeurs Adobe Commerce à se préparer à la conformité aux réglementations de confidentialité. Consultez votre service juridique pour déterminer si et comment votre entreprise doit se conformer à des obligations légales.

Utilisez les diagrammes de flux de données suivants et les mappages d’entités de base de données à titre de référence lors du développement de programmes de conformité aux réglementations de confidentialité, comme :

- [RGPD](gdpr.md)
- [CCPA](ccpa.md)

## Diagrammes de flux de données

Les diagrammes de flux de données indiquent les types de données que les clients et les administrateurs peuvent saisir et récupérer sur le storefront et l’administrateur.

### Points d’entrée des données frontaux

Un utilisateur peut saisir des informations sur son client, son adresse et son paiement lors de son enregistrement pour un compte, lors de son passage en caisse et pour d’autres événements similaires.

![ Points d’entrée de données frontend](../../assets/security-compliance/frontend-data-entry-points.svg)

### Points d’accès aux données frontaux

Commerce charge les informations sur les clients lorsque le client se connecte et consulte plusieurs pages ou extraits différents.

![ Points d’accès aux données frontend](../../assets/security-compliance/frontend-data-access-points.svg)

### Points d’entrée des données dorsales

Un commerçant peut saisir des informations sur le client, l’adresse et le paiement auprès de l’administrateur pour créer un client ou une commande.

![ Points d’entrée des données principales](../../assets/security-compliance/backend-data-entry-points.svg)

### Points d’accès aux données du serveur principal

Commerce charge les informations sur les clients lorsqu’un commerçant affiche plusieurs types de grilles, clique sur une grille pour afficher des informations détaillées et effectue diverses autres tâches.

![ Points d’accès aux données du serveur principal](../../assets/security-compliance/backend-data-access-points.svg)

## Entités de base de données

Le Magento 1 stocke les informations sur les clients dans des tables de base de données, de ventes et autres.

### Données client

Magento 1 stocke les informations sur les clients dans les tables `customer_entity` et `customer_address_entity`. Ces deux tables comportent plusieurs tables de référence qui peuvent contenir des attributs client personnalisés.

#### `customer_entity` et tables de référence

Les colonnes suivantes du `customer_entity`tableau contiennent les informations sur les clients :

| Colonne | Type de données |
| --- | --- |
| `email` | varchar(255) |

Ces tables font référence à `customer_entity` et peuvent contenir des attributs client personnalisés :

| Tableau | Colonne | Type de données |
| --- | --- | --- |
| `customer_entity_datetime` | `value` | datetime |
| `customer_entity_decimal` | `value` | decimal(12,4) |
| `customer_entity_int` | `value` | int(11) |
| `customer_entity_text` | `value` | text |
| `customer_entity_varchar` | `value` | varchar(255) |

#### `customer_address_entity` et tables de référence

Les tables suivantes font référence à `customer_address_entity` et peuvent contenir des attributs client personnalisés :

| Tableau | Colonne | Type de données |
| --- | --- | --- |
| `customer_address_entity_datetime` | `value` | datetime |
| `customer_address_entity_decimal` | `value` | decimal(12,4) |
| `customer_address_entity_int` | `value` | int(11) |
| `customer_address_entity_text` | `value` | text |
| `customer_address_entity_varchar` | `value` | varchar(255) |

### Données de commande

Les `sales_flat_order` et tables connexes contiennent le nom du client, les adresses de facturation et d’expédition, ainsi que les informations connexes.

#### `sales_flat_order` table

Les colonnes suivantes du tableau `sales_order` contiennent les informations sur les clients :

| Colonne | Type de données |
| --- | --- |
| `customer_id` | int(10) |
| `customer_email` | varchar(128) |
| `customer_firstname` | varchar(128) |
| `customer_gender` | int(11) |
| `customer_lastname` | varchar(128) |
| `customer_middlename` | varchar(128) |
| `customer_prefix` | varchar(32) |
| `customer_suffix` | varchar(32) |
| `customer_taxvat` | varchar(32) |
| `remote_ip` | varchar(32) |

#### `sales_flat_order_address` table

La table `sales_flat_order_address` contient l’adresse du client.

| Colonne | Type de données |
| --- | --- |
| `customer_id` | int(10) |
| `fax` | varchar(255) |
| `region` | varchar(255) |
| `postcode` | varchar(255) |
| `lastname` | varchar(255) |
| `street` | varchar(255) |
| `city` | varchar(255) |
| `email` | varchar(255) |
| `telephone` | varchar(255) |
| `firstname` | varchar(255) |
| `prefix` | varchar(255) |
| `suffix` | varchar(255) |
| `middlename` | varchar(255) |
| `company` | varchar(255) |
| `vat_id` | text |

#### `sales_flat_order_grid` table

Les colonnes suivantes du tableau `sales_flat_order_grid` contiennent les informations sur les clients :

| Colonne | Type de données |
| --- | --- |
| `customer_id` | int(10) |
| `shipping_name` | varchar(255) |
| `billing_name` | varchar(255) |

#### `sales_flat_order_payment` table

Les colonnes suivantes du tableau `sales_flat_order_payment` contiennent les informations sur les clients :

| Colonne | Type de données |
| --- | --- |
| `cc_exp_month` | varchar(255) |
| `cc_ss_start_year` | varchar(255) |
| `echeck_bank_name` | varchar(128) |
| `echeck_type` | varchar(255) |
| `cc_ss_start_month` | varchar(255) |
| `cc_owner` | varchar(255) |
| `cc_exp_year` | varchar(255) |
| `echeck_routing_number` | varchar(255) |
| `echeck_account_name` | varchar(255) |

### Données citées

Les citations contiennent le nom, l’adresse électronique, l’adresse électronique et les informations associées d’un client.

#### `sales_flat_quote` table

Les colonnes suivantes du tableau `sales_flat_quote` contiennent les informations sur les clients :

| Colonne | Type de données |
| --- | --- |
| `customer_id` | int(10) |
| `customer_tax_class_id` | int(10) |
| `customer_group_id` | int(10) |
| `customer_email` | varchar(255) |
| `customer_prefix` | varchar(40) |
| `customer_firstname` | varchar(255) |
| `customer_middlename` | varchar(40) |
| `customer_lastname` | varchar(255) |
| `customer_suffix` | varchar(40) |
| `customer_dob` | datetime |
| `customer_note` | varchar(255) |
| `remote_ip` | varchar(255) |
| `customer_gender` | varchar(255) |

#### `sales_flat_quote_address` table

Les colonnes suivantes du tableau `sales_flat_quote_address` contiennent les informations sur les clients :

| Colonne | Type de données |
| --- | --- |
| `email` | varchar(255) |
| `prefix` | varchar(40) |
| `firstname` | varchar(255) |
| `middlename` | varchar(40) |
| `lastname` | varchar(255) |
| `suffix` | varchar(40) |
| `company` | varchar(255) |
| `street` | varchar(255) |
| `city` | varchar(255) |
| `region` | varchar(255) |
| `postcode` | varchar(255) |
| `fax` | varchar(255) |

#### `sales_flat_quote_payment` table

La table `sales_flat_quote_payment` comprend des informations de carte de crédit et d’autres informations transactionnelles.

| Colonne | Type de données |
| --- | --- |
| `cc_last_4` | varchar(255) |
| `cc_owner` | varchar(255) |
| `cc_exp_month` | smallint(5) |
| `cc_exp_year` | smallint(5) |
| `cc_ss_owner` | varchar(255) |
| `cc_ss_start_month` | smallint(5) |
| `cc_ss_start_year` | smallint(5) |

### Archiver des données

Les tableaux et colonnes suivants contiennent les informations sur les clients :

| Tableau | Colonne | Type de données |
| --- | --- | --- |
| `enterprise_sales_creditmemo_grid_archive` | `billing_name` | varchar(255) |
| `enterprise_sales_invoice_grid_archive` | `billing_name` | varchar(255) |
| `enterprise_sales_order_grid_archive` | `billing_name` | varchar(255) |
| `enterprise_sales_order_grid_archive` | `customer_id` | int(10) |
| `enterprise_sales_order_grid_archive` | `shipping_name` | varchar(255) |
| `enterprise_sales_shipment_grid_archive` | `shipping_name` | varchar(255) |

### Données de vente

Les tableaux et colonnes suivants contiennent les informations sur les clients :

| Tableau | Colonne | Type de données |
| --- | --- | --- |
| `sales_flat_creditmemo_grid` | `billing_name` | varchar(255) |
| `sales_flat_invoice_grid` | `billing_name` | varchar(255) |

### Données RMA

Les tableaux et colonnes RMA suivants contiennent des informations sur les clients :

| Tableau | Colonne | Type de données |
| --- | --- | --- |
| `enterprise_rma` | `customer_custom_email` | varchar(255) |
| `enterprise_rma_grid` | `customer_id` | int(10) |
| `enterprise_rma_grid` | `customer_name` | varchar(255) |

### Données diverses

Les tableaux et colonnes suivants contiennent les informations sur les clients :

| Tableau | Colonne | Type de données |
| --- | --- | --- |
| `core_email_queue_recipients` | `recipient_email` | varchar(128) |
| `core_email_queue_recipients` | `recipient_name` | varchar(255) |
| `customer_flowpassword` | `email` | varchar(255) |
| `customer_flowpassword` | `ip` | varchar(50) |
| `enterprise_giftregistry_person` | `email` | varchar(150) |
| `enterprise_giftregistry_person` | `firstname` | varchar(100) |
| `enterprise_giftregistry_person` | `lastname` | varchar(100) |
| `enterprise_giftregistry_person` | `middlename` | text |
| `enterprise_invitation` | `customer_id` | int(10) |
| `enterprise_invitation` | `email` | varchar(255) |
| `enterprise_invitation` | `referral_id` | int(10) |
| `enterprise_reminder_rule_coupon` | `customer_id` | int(10) |
| `enterprise_reminder_rule_coupon` | `emails_failed` | smallint(5) |
| `enterprise_scheduled_operations` | `email_receiver` | varchar(150) |
| `enterprise_scheduled_operations` | `email_sender` | varchar(150) |
| `gift_message` | `customer_id` | int(10) |
| `gift_message` | `recipient` | varchar(255) |
| `gift_message` | `sender` | varchar(255) |
| `newsletter_subscriber` | `customer_id` | int(10) |
| `newsletter_subscriber` | `subscriber_email` | varchar(150) |
| `persistent_session` | `customer_id` | int(10) |
| `persistent_session` | `info` | text |
| `poll_vote` | `customer_id` | int(10) |
| `poll_vote` | `ip_address` | varbinary(16) |
| `rating_option_vote` | `customer_id` | int(10) |
| `rating_option_vote` | `remote_ip` | varchar(50) |
| `rating_option_vote` | `remote_ip_long` | varbinary(516) |
| `send_friend_log` | `ip` | varbinary(16) |

Autres tables faisant référence à Customer :

- `catalog_compare_item`
- `downloadable_link_purchased`
- `enterprise_customerbalance`
- `enterprise_customersegment_customer`
- `enterprise_giftregistry_entity`
- `enterprise_reminder_rule_log`
- `enterprise_reward`
- `log_customer`
- `log_visitor_online`
- `oauth_token`
- `product_alert_price`
- `product_alert_stock`
- `report_compared_product_index`
- `report_viewed_product_index`
- `review_detail`
- `sales_billing_agreement`
- `sales_flat_shipment`
- `sales_recurring_profile`
- `salesrule_coupon_usage`
- `salesrule_customer`
- `tag`
- `tag_relation`
- `wishlist`
