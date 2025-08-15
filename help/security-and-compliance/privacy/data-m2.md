---
title: Référence des informations personnelles du client (version 2.x)
description: Découvrez les diagrammes de flux de données et les mappages d’entités de base de données pour les informations personnelles des clients dans Adobe Commerce 2.x.
exl-id: f08f4f93-a7b6-4c43-bc07-f159822dc528
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '837'
ht-degree: 1%

---

# Référence des informations personnelles du client (version 2.x)

>[!NOTE]
>
>Cette rubrique fait partie d’une série de rubriques destinées à aider les commerçants et les développeurs Adobe Commerce à se préparer à la conformité aux réglementations de confidentialité. Consultez votre conseiller juridique pour déterminer si et comment votre entreprise devrait se conformer à des obligations légales.

Utilisez les diagrammes de flux de données et les mappages d’entités de base de données suivants à titre de référence lors du développement de programmes de conformité pour les réglementations de confidentialité telles que :

- [RGPD](gdpr.md)
- [CCPA](ccpa.md)

## Diagrammes de flux de données

Les diagrammes de flux de données montrent les types de données que les clients et les administrateurs peuvent saisir et récupérer dans le storefront et l’administrateur.

### Points d’entrée des données front-end

Un utilisateur peut saisir des informations sur le client, l’adresse et le paiement lors de l’inscription à un compte, du passage en caisse et d’événements similaires.

![Points d’entrée de données front-end](../../assets/security-compliance/frontend-data-entry-points.svg)

### Points d’accès aux données front-end

Adobe Commerce charge les informations du client lorsque ce dernier se connecte et consulte plusieurs pages différentes ou les extrait.

![Points d’accès aux données front-end](../../assets/security-compliance/frontend-data-access-points.svg)

### Points d’entrée des données du serveur principal

Un commerçant peut saisir des informations sur le client, des données d’adresse et des données de paiement lors de la création d’un client ou d’une commande auprès de l’administrateur.

![Points d’entrée des données du serveur principal](../../assets/security-compliance/backend-data-entry-points.svg)

### Points d’accès aux données du serveur principal

Adobe Commerce charge les informations client lorsqu’un commerçant consulte plusieurs types de grilles, clique sur une grille pour afficher des informations détaillées et effectue diverses autres tâches.

![Points d’accès aux données du serveur principal](../../assets/security-compliance/backend-data-access-points.svg)

## Entités de base de données

Adobe Commerce stocke principalement les informations spécifiques au client dans les tables de client, d’adresse, de commande, de devis et de paiement. D’autres tableaux contiennent des références à l’ID client.

### Données clients

Adobe Commerce peut être configuré pour stocker les attributs du client suivants :

- Date de naissance
- E-mail
- Prénom
- Sexe
- Nom
- Deuxième prénom/initial
- Préfixe de nom
- Suffixe du nom

>[!NOTE]
>
>Conformément aux bonnes pratiques actuelles en matière de sécurité et de confidentialité, assurez-vous d’être conscient de tous les risques juridiques et de sécurité potentiels associés au stockage de la date de naissance complète du client (mois, jour, année) ainsi que d’autres identifiants personnels, tels que le nom complet, avant de collecter ou de traiter ces données.

#### Références `customer_entity` et « customer_entity »

Les colonnes suivantes du tableau `customer_entity` contiennent des informations sur les clients :

| Colonne | Type de données |
| ------------ | ------------ |
| `email` | varchar(255) |
| `prefix` | varchar(40) |
| `firstname` | varchar(255) |
| `middlename` | varchar(255) |
| `lastname` | varchar(255) |
| `suffix` | varchar(40) |
| `dob` | date |
| `gender` | smallint(5) |

Ces tableaux font référence à `customer_entity` et peuvent contenir des attributs client personnalisés :

| Tableau | Colonne | Type de données |
| -------------------------- | ------- | ------------- |
| `customer_entity_datetime` | `value` | datetime |
| `customer_entity_decimal` | `value` | decimal(12,4) |
| `customer_entity_int` | `value` | int(11) |
| `customer_entity_text` | `value` | texte |
| `customer_entity_varchar` | `value` | varchar(255) |

#### `customer_grid_flat` table

Les colonnes suivantes du tableau `customer_grid_flat` contiennent des informations sur les clients :

| Colonne | Type de données |
| -------------------- | ------------ |
| `name` | texte |
| `email` | varchar(255) |
| `dob` | date |
| `gender` | int(11) |
| `shipping_full` | texte |
| `billing_full` | texte |
| `billing_firstname` | varchar(255) |
| `billing_lastname` | varchar(255) |
| `billing_telephone` | varchar(255) |
| `billing_postcode` | varchar(255) |
| `billing_country_id` | varchar(255) |
| `billing_region` | varchar(255) |
| `billing_city` | varchar(255) |
| `billing_fax` | varchar(255) |
| `billing_vat_id` | varchar(255) |
| `billing_company` | varchar(255) |

### Données d’adresse

Adobe Commerce stocke les attributs du client suivants :

- Ville
- Société
- Pays
- Télécopie
- Prénom
- Nom
- Deuxième prénom/initial
- Préfixe de nom
- Suffixe du nom
- Numéro de téléphone
- État/Province
- Identifiant de l’état/province
- Adresse Postale
- Numéro de TVA
- Code Postal

#### `customer_address_entity` et références `customer_address_entity`

Les colonnes suivantes du tableau `customer_address_entity` contiennent des informations sur les clients :

| Colonne | Type de données |
| ------------ | ------------ |
| `city` | varchar(255) |
| `company` | varchar(255) |
| `country_id` | varchar(255) |
| `fax` | varchar(255) |
| `firstname` | varchar(255) |
| `lastname` | varchar(255) |
| `middlename` | varchar(255) |
| `postcode` | varchar(255) |
| `region` | varchar(255) |
| `region_id` | int(10) |
| `street` | texte |
| `suffix` | varchar(40) |
| `telephone` | varchar(255) |
| `vat_id` | varchar(255) |

Ces tableaux font référence à `customer_address_entity` et peuvent contenir des attributs client personnalisés :

| Tableau | Colonne | Type de données |
| ---------------------------------- | ------- | ------------- |
| `customer_address_entity_datetime` | `value` | datetime |
| `customer_address_entity_decimal` | `value` | decimal(12,4) |
| `customer_address_entity_int` | `value` | int(11) |
| `customer_address_entity_text` | `value` | texte |
| `customer_address_entity_varchar` | `value` | varchar(255) |

### Données de commande

Le `sales_order` et les tables associées contiennent le nom du client, les adresses de facturation et d’expédition, ainsi que les données associées.

#### `sales_order` table

Les colonnes suivantes du tableau `sales_order` contiennent des informations sur les clients :

| Colonne | Type de données |
| --------------------- | ------------ |
| `customer_dob` | datetime |
| `customer_email` | varchar(128) |
| `customer_firstname` | varchar(128) |
| `customer_gender` | int(11) |
| `customer_group_id` | int(11) |
| `customer_id` | int(10) |
| `customer_lastname` | varchar(128) |
| `customer_middlename` | varchar(128) |
| `customer_prefix` | varchar(32) |
| `customer_suffix` | varchar(32) |
| `customer_taxvat` | varchar(32) |
| `quote_address_id` | int(11) |
| `remote_ip` | varchar(32) |
| `x_forwarded_for` | varchar(32) |

#### `sales_order_address` table

La table `sales_order_address` contient l&#39;adresse du client.

| Colonne | Type de données |
| --------------------- | ------------ |
| `customer_address_id` | int(11) |
| `quote_address_id` | int(11) |
| `region_id` | int(11) |
| `customer_id` | int(11) |
| `fax` | varchar(255) |
| `region` | varchar(255) |
| `postcode` | varchar(255) |
| `lastname` | varchar(255) |
| `street` | varchar(255) |
| `city` | varchar(255) |
| `email` | varchar(255) |
| `telephone` | varchar(255) |
| `country_id` | varchar(2) |
| `firstname` | varchar(255) |
| `suffix` | varchar(255) |
| `company` | varchar(255) |

#### `sales_order_grid` table

Les colonnes suivantes du tableau `sales_order_grid` contiennent des informations sur les clients :

| Colonne | Type de données |
| ---------------------- | ------------ |
| `customer_id` | int(10) |
| `shipping_name` | varchar(255) |
| `billing_name` | varchar(255) |
| `billing_address` | varchar(255) |
| `shipping_address` | varchar(255) |
| `shipping_information` | varchar(255) |
| `customer_email` | varchar(255) |
| `customer_name` | varchar(255) |

### Données de devis

Les devis contiennent le nom, l’adresse e-mail, l’adresse et les informations associées d’un client.

#### `quote` table

Les colonnes suivantes du tableau `quote` contiennent des informations sur les clients :

| Colonne | Type de données |
| --------------------- | ------------ |
| `customer_id` | int(10) |
| `customer_email` | varchar(255) |
| `customer_prefix` | varchar(40) |
| `customer_firstname` | varchar(255) |
| `customer_middlename` | varchar(40) |
| `customer_lastname` | varchar(255) |
| `customer_dob` | datetime |
| `remote_ip` | varchar(32) |
| `customer_taxvat` | varchar(255) |
| `customer_gender` | varchar(255) |

#### `quote_address` table

Les colonnes suivantes du tableau `quote_address` contiennent des informations sur les clients :

| Colonne | Type de données |
| ------------- | ------------ |
| `customer_id` | int(10) |
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
| `region_id` | int(10) |
| `postcode` | varchar(20) |
| `country_id` | varchar(30) |
| `telephone` | varchar(255) |
| `fax` | varchar(255) |

### Données de paiement

Le tableau `sales_order_payment` comprend les informations de carte de crédit et d’autres informations transactionnelles.

| Colonne | Type de données |
| ------------------------ | ------------ |
| `cc_exp_month` | varchar(12) |
| `echeck_bank_name` | varchar(128) |
| `cc_last_4` | varchar(100) |
| `cc_owner` | varchar(128) |
| `po_number` | varchar(32) |
| `cc_exp_year` | varchar(4) |
| `echeck_routing_number` | varchar(32) |
| `cc_debug_response_body` | varchar(32) |
| `echeck_account_name` | varchar(32) |
| `cc_number_enc` | varchar(128) |
| `additional_information` | texte |

### Données d’invitation

Adobe Commerce peut être configuré de sorte que les clients puissent envoyer des invitations à des ventes privées et à des événements.

#### `magento_invitation` table

La table `magento_invitation` contient l’ID client, l’adresse e-mail et l’ID de référence.

| Colonne | Type de données |
| ------------- | ------------ |
| `customer_id` | int(10) |
| `email` | varchar(255) |
| `referral_id` | int(10) |

#### `magento_invitation_track` table

Le tableau `magento_invitation_track` contient également des informations sur les clients.

| Colonne | Type de données |
| ------------- | --------- |
| `inviter_id` | int(10) |
| `referral_id` | int(10) |

### Tables diverses qui font référence au client

Les tableaux suivants contiennent une colonne `customer_id` :

- `catalog_compare_item`
- `catalog_product_frontend_action`
- `downloadable_link_purchased`
- `magento_customerbalance`
- `magento_customersegment_customer`
- `magento_reward`
- `magento_rma`
- `oauth_token`
- `paypal_billing_agreement`
- `persistent_session`
- `product_alert_price`
- `product_stock_alert`
- `report_compared_product_index`
- `report_viewed_product_index`
- `review_detail`
- `salesrule_coupon_usage`
- `salesrule_customer`
- `wishlist`
