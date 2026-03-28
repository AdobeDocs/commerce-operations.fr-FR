---
title: Chemins sensibles et spécifiques au système
description: Découvrez les chemins de configuration sensibles et spécifiques au système pour Adobe Commerce. Découvrez la configuration sécurisée et la gestion des variables d’environnement.
feature: Configuration, System
exl-id: 127880ab-7507-4e53-8b51-dfa6557d0b18
source-git-commit: 7054a5286f01e26e324401f4d8505e4e0faed93e
workflow-type: tm+mt
source-wordcount: '4206'
ht-degree: 0%

---

# Paramètres sensibles et spécifiques au système

Cette rubrique répertorie les chemins de configuration pour les paramètres spécifiques au système et sensibles :

- La commande [`magento app:config:dump` écrit &#x200B;](../cli/export-configuration.md) paramètres spécifiques au système dans le fichier de configuration spécifique au système, `app/etc/env.php`, qui ne doit _pas_ se trouver dans le contrôle de code source. Il écrit également la configuration partagée pour toutes les instances Commerce à `app/etc/config.php`. Ce fichier _doit_ se trouve dans le contrôle de code source.
- La commande [`magento config:sensitive:set` écrit &#x200B;](../cli/set-configuration-values.md) paramètres sensibles à `app/etc/env.php`.

  Vous pouvez également définir des valeurs sensibles à l’aide de variables de configuration, comme indiqué dans la section [Utiliser des variables d’environnement pour remplacer les paramètres de configuration](../reference/override-config-settings.md#environment-variables).

Pour obtenir la liste des autres chemins de configuration, voir :

- [Tous les chemins de configuration, sauf les paiements](../reference/config-reference-general.md)
- [&#x200B; Chemins de configuration des paiements &#x200B;](../reference/config-reference-payment.md).

>[!INFO]
>
>Tous les chemins de configuration répertoriés dans cette rubrique sont sensibles. La colonne `System-specific?` indique les valeurs qui sont également spécifiques au système.

## Chemins d’accès généraux spécifiques aux systèmes et sensibles aux catégories

Cette section répertorie les noms de variables et les chemins de configuration disponibles pour les options dans Admin sous **Magasins** > Paramètres > **Configuration** > **Général**.

### Chemins d’accès web sensibles et spécifiques au système

Ces valeurs de configuration sont disponibles dans Admin dans **Magasins** > Paramètres > **Configuration** > **Général** > **Web**.

| Nom | Chemin de configuration | Prise en charge des versions de Commerce | Chiffré ? | Spécifique au système ? | Sensible ? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| URL de base | `web/unsecure/base_url` |  | | Spécifique au système | |
| URL du lien de base | `web/unsecure/base_link_url` |  | | Spécifique au système | |
| URL de base des fichiers de vue statiques | `web/unsecure/base_static_url` |  | | Spécifique au système | |
| URL de base des fichiers multimédias utilisateur | `web/unsecure/base_media_url` |  | | Spécifique au système | |
| URL de base sécurisée | `web/secure/base_url` |  | | Spécifique au système | |
| URL du lien de base sécurisé | `web/secure/base_link_url` |  | | Spécifique au système | |
| URL de base sécurisée pour les fichiers de vue statiques | `web/secure/base_static_url` |  | | Spécifique au système | |
| URL de base sécurisée pour les fichiers multimédias utilisateur | `web/secure/base_media_url` |  | | Spécifique au système | |
| URL Web par défaut | `web/default/front` |  | | Spécifique au système | |
| URL sans itinéraire par défaut | `web/default/no_route` |  | | Spécifique au système | |
| Chemin du cookie | `web/cookie/cookie_path` |  | | Spécifique au système | |
| Domaine de cookie | `web/cookie/cookie_domain` |  | | Spécifique au système | |
| Durée de vie du cookie | `web/cookie/cookie_lifetime` |  | | Spécifique au système | |
| Utiliser HTTP uniquement | `web/cookie/cookie_httponly` |  | | Spécifique au système | |
| Mode de restriction des cookies | `web/cookie/cookie_restriction` |  | | Spécifique au système | |

{style="table-layout:auto"}

### Chemins d’accès sensibles à la configuration des devises et spécifiques au système

Ces valeurs de configuration sont disponibles dans Admin dans **Magasins** > Paramètres > **Configuration** > **Général** > **Configuration de la devise**.

| Nom | Chemin de configuration | Prise en charge des versions de Commerce | Chiffré ? | Spécifique au système ? | Sensible ? |
| --- | --- | --- | --- | --- | --- |
| Destinataire de l’e-mail d’erreur | `currency/import/error_email` |  | | | Sensible |

{style="table-layout:auto"}

### Stocker les chemins sensibles à l’adresse e-mail et spécifiques au système

Ces valeurs de configuration sont disponibles dans Admin dans **Magasins** > Paramètres > **Configuration des e-mails** > **Général** > **Stocker les adresses e-mail**.

| Nom | Chemin de configuration | Prise en charge des versions de Commerce | Chiffré ? | Spécifique au système ? | Sensible ? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Nom de l’expéditeur | `trans_email/ident_general/name` | | | | Sensible |
| E-mail de l’expéditeur | `trans_email/ident_general/email` |  | | | Sensible |
| Nom de l’expéditeur | `trans_email/ident_sales/name` |  | | | Sensible |
| E-mail de l’expéditeur | `trans_email/ident_sales/email` |  | | | Sensible |
| Nom de l’expéditeur | `trans_email/ident_support/name` |  | | | Sensible |
| E-mail de l’expéditeur | `trans_email/ident_support/email` |  | | | Sensible |
| Nom de l’expéditeur | `trans_email/ident_custom1/name` |  | | | Sensible |
| E-mail de l’expéditeur | `trans_email/ident_custom1/email` |  | | | Sensible |
| Nom de l’expéditeur | `trans_email/ident_custom2/name` |  | | | Sensible |
| E-mail de l’expéditeur | `trans_email/ident_custom2/email` |  | | | Sensible |

{style="table-layout:auto"}

### Chemins d’accès sensibles aux contacts et spécifiques au système

Ces valeurs de configuration sont disponibles dans Admin dans **Magasins** > Paramètres > **Configuration** > **Général** > **Contacts**.

| Nom | Chemin de configuration | Prise en charge des versions de Commerce | Chiffré ? | Spécifique au système ? | Sensible ? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Envoyer Des E-Mails À | `contact/email/recipient_email` |  | | | Sensible |
| Expéditeur de l’e-mail | `contact/email/sender_email_identity` |  | | | Sensible |
| Modèle d’e-mail | `contact/email/email_template` |  | | | Sensible |

{style="table-layout:auto"}

### Chemins d’accès sensibles aux rapports et spécifiques au système New Relic

Ces valeurs de configuration sont disponibles dans Admin dans **Magasins** > Paramètres > **Configuration** > **Général** > **Rapports New Relic**.

| Nom | Chemin de configuration | Prise en charge des versions de Commerce | Chiffré ? | Spécifique au système ? | Sensible ? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| ID de compte New Relic | `newrelicreporting/general/account_id` |  | | | Sensible |
| ID de l’application New Relic | `newrelicreporting/general/app_id` |  | | | Sensible |
| Clé API New Relic | `newrelicreporting/general/api` |  | Chiffré | | Sensible |
| Clé API Insights | `newrelicreporting/general/insights_insert_key` |  | Chiffré | | Sensible |
| URL DE L’API New Relic | `newrelicreporting/general/api_url` |  | | Spécifique au système | Sensible |
| URL de l’API Insights | `newrelicreporting/general/insights_api_url` |  | | Spécifique au système | Sensible |

{style="table-layout:auto"}

## Chemins d’accès sensibles aux catégories de clients et spécifiques au système

Cette section répertorie les noms de variables et les chemins de configuration disponibles pour les options dans Admin sous **Magasins** > Paramètres > **Configuration** > **Clients**.

### Chemins d’accès sensibles à la configuration du client et spécifiques au système

Ces valeurs de configuration sont disponibles dans Admin dans **Magasins** > Paramètres > **Configuration** > **Clients** > **Configuration client**.

| Nom | Chemin de configuration | Prise en charge des versions de Commerce | Chiffré ? | Spécifique au système ? | Sensible ? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Domaine d’e-mail par défaut | `customer/create_account/email_domain` |  | | Spécifique au système | |

{style="table-layout:auto"}

## Catégorie de catalogue

Cette section répertorie les noms de variables et les chemins de configuration disponibles pour les options dans Admin sous **Magasins** > Paramètres > **Configuration** > **Catalogue**.

### Chemins d’accès sensibles au catalogue et spécifiques au système

Ces valeurs de configuration sont disponibles dans Admin dans **Magasins** > Paramètres > **Configuration** > **Catalogue** > **Catalogue**.

| Nom | Chemin de configuration | Prise en charge des versions de Commerce | Chiffré ? | Spécifique au système ? | Sensible ? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Destinataire de l’e-mail d’erreur | `catalog/productalert_cron/error_email` |  | | | Sensible |
| Clé API YouTube | `catalog/product_video/youtube_api_key` |  | | | Sensible |
| Nom D’Hôte Du Serveur Solr | `catalog/search/solr_server_hostname` | Commerce Enterprise uniquement | | Spécifique au système | Sensible |
| Port Du Serveur Solr | `catalog/search/solr_server_port` | Commerce Enterprise uniquement | | Spécifique au système | Sensible |
| Nom d’utilisateur du serveur Solr | `catalog/search/solr_server_username` | Commerce Enterprise uniquement | | Spécifique au système | Sensible |
| Mot de passe du serveur Solr | `catalog/search/solr_server_password` | Commerce Enterprise uniquement | | Spécifique au système | Sensible |
| Chemin d’accès au serveur Solr | `catalog/search/solr_server_path` | Commerce Enterprise uniquement | | Spécifique au système | Sensible |
| Nom d’hôte du serveur Elasticsearch | `catalog/search/elasticsearch_server_hostname` |  | | Spécifique au système | Sensible |
| Port du serveur Elasticsearch | `catalog/search/elasticsearch_server_port` |  | | Spécifique au système | Sensible |
| Préfixe d’index Elasticsearch | `catalog/search/elasticsearch_index_prefix` |  | | Spécifique au système | Sensible |
| Activer l’authentification HTTP Elasticsearch | `catalog/search/elasticsearch_enable_auth` |  | | Spécifique au système | |
| Nom d’utilisateur HTTP Elasticsearch | `catalog/search/elasticsearch_username` |  | | Spécifique au système | |
| Mot de passe HTTP Elasticsearch | `catalog/search/elasticsearch_password` |  | | Spécifique au système | |
| Délai d’expiration du serveur Elasticsearch | `catalog/search/elasticsearch_server_timeout` |  | | Spécifique au système | |
| Nom d’utilisateur HTTP Elasticsearch | `catalog/search/elasticsearch_username` | | | Spécifique au système | |
| Mot de passe HTTP Elasticsearch | `catalog/search/elasticsearch_password` | | | Spécifique au système | |
| Délai d’expiration du serveur Elasticsearch | `catalog/search/elasticsearch_server_timeout` | | | Spécifique au système | |
| Nom d’hôte du serveur OpenSearch | `catalog/search/opensearch_server_hostname` | | | Spécifique au système | Sensible |
| Port du serveur OpenSearch | `catalog/search/opensearch_server_port` | | | Spécifique au système | Sensible |
| Préfixe d’index OpenSearch | `catalog/search/opensearch_index_prefix` | | | Spécifique au système | Sensible |
| Activer l’authentification HTTP OpenSearch | `catalog/search/opensearch_enable_auth` | | | Spécifique au système | |
| Nom d’utilisateur HTTP OpenSearch | `catalog/search/opensearch_username` | | | Spécifique au système | |
| Mot de passe HTTP OpenSearch | `catalog/search/opensearch_password` | | | Spécifique au système | |
| Délai d’expiration d’OpenSearch Server | `catalog/search/opensearch_server_timeout` | | | Spécifique au système | |

{style="table-layout:auto"}

>[!NOTE]
>
>Les paramètres OpenSearch ont été introduits dans Adobe Commerce 2.4.6.

### Chemins d’accès sensibles au stock et spécifiques au système

Ces valeurs de configuration sont disponibles dans Admin dans **Magasins** > Paramètres > **Configuration** > **Catalogue** > **Inventaire**.

| Nom | Chemin de configuration | Prise en charge des versions de Commerce| Chiffré ? | Spécifique au système ? | Sensible ? | |
|--------------|--------------|--------------|--------------|--------------|--------------| |
| Clé API Google | `cataloginventory/source_selection_distance_based_google/api_key` | Chiffrée | Sensible |

### Chemins d’accès sensibles au plan de site XML et spécifiques au système

Ces valeurs de configuration sont disponibles dans Admin dans **Magasins** > Paramètres > **Configuration** > **Catalogue** > **Plan de site XML**.

| Nom | Chemin de configuration | Prise en charge des versions de Commerce | Chiffré ? | Spécifique au système ? | Sensible ? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Destinataire de l’e-mail d’erreur | `sitemap/generate/error_email` |  | | | Sensible |

{style="table-layout:auto"}

## Catégorie de vente

Cette section répertorie les noms de variables et les chemins de configuration disponibles pour les options dans Admin sous **Magasins** > Paramètres > **Configuration** > **Ventes**.

### Chemins d’accès sensibles aux paramètres d’expédition et spécifiques au système

Ces valeurs de configuration sont disponibles dans Admin dans **Magasins** > Paramètres > **Configuration** > **Ventes** > **Paramètres d’expédition**.

| Nom | Chemin de configuration | Prise en charge des versions de Commerce | Chiffré ? | Spécifique au système ? | Sensible ? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Pays | `shipping/origin/country_id` |  | | | Sensible |
| Région/État | `shipping/origin/region_id` |  | | | Sensible |
| Code postal | `shipping/origin/postcode` |  | | | Sensible |
| Ville | `shipping/origin/city` |  | | | Sensible |
| Adresse Postale | `shipping/origin/street_line1` |  | | | Sensible |
| Adresse postale Ligne 2 | `shipping/origin/street_line2` |  | | | Sensible |
| Compte dynamique | `carriers/ups/is_account_live` |  | | Spécifique au système | |

{style="table-layout:auto"}

### Chemins d’accès sensibles et spécifiques au système pour les e-mails commerciaux

Ces valeurs de configuration sont disponibles dans Admin dans **Magasins** > Paramètres > **Configuration** > **Ventes** > **Emails commerciaux**.

| Nom | Chemin de configuration | Prise en charge des versions de Commerce | Chiffré ? | Spécifique au système ? | Sensible ? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Envoyer La Copie De L&#39;E-Mail De Commande À | `sales_email/order/copy_to` |  | | | Sensible |
| Envoyer La Copie E-Mail Du Commentaire De Commande À | `sales_email/order_comment/copy_to` |  | | | Sensible |
| Envoyer La Copie De L&#39;E-Mail De Facture À | `sales_email/invoice/copy_to` |  | | | Sensible |
| Envoyer La Copie D&#39;E-Mail De Commentaire De Facture À | `sales_email/invoice_comment/copy_to` |  | | | Sensible |
| Envoyer La Copie De L&#39;E-Mail D&#39;Expédition À | `sales_email/shipment/copy_to` |  | | | Sensible |
| Envoyer La Copie E-Mail Du Commentaire D&#39;Expédition À | `sales_email/shipment_comment/copy_to` |  | | | Sensible |
| Envoyer Une Copie D&#39;E-Mail D&#39;Avoir À | `sales_email/creditmemo/copy_to` |  | | | Sensible |
| Envoyer Une Copie D&#39;E-Mail De Commentaire D&#39;Avoir À | `sales_email/creditmemo_comment/copy_to` |  | | | Sensible |
| Envoyer la copie d&#39;e-mail prête pour le retrait à | `sales_email/temando_pickup/copy_to` |  | | | Sensible |

{style="table-layout:auto"}

### Chemins d’accès sensibles et spécifiques au système pour l’extraction

Ces valeurs de configuration sont disponibles dans Admin dans **Magasins** > Paramètres > **Configuration** > **Ventes** > **Passage en caisse**.

| Nom | Chemin de configuration | Prise en charge des versions de Commerce | Chiffré ? | Spécifique au système ? | Sensible ? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Envoyer La Copie D&#39;E-Mail D&#39;Échec Du Paiement À | `checkout/payment_failed/copy_to` |  | | | Sensible |

{style="table-layout:auto"}

### Chemins sensibles à l’API Google et spécifiques au système

Ces valeurs de configuration sont disponibles dans Admin dans l’API **Magasins** > Paramètres > **Configuration** > **Ventes** > **Google**.

| Nom | Chemin de configuration | Prise en charge des versions de Commerce | Chiffré ? | Spécifique au système ? | Sensible ? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Id De Conteneur | `google/analytics/container_id` | Commerce Enterprise uniquement | | | Sensible |

{style="table-layout:auto"}

### Chemins spécifiques aux systèmes et sensibles aux méthodes de diffusion

Ces valeurs de configuration sont disponibles dans Admin dans **Magasins** > Paramètres > **Configuration** > **Ventes** > **Méthodes de diffusion**.

| Nom | Chemin de configuration | Prise en charge des versions de Commerce | Chiffré ? | Spécifique au système ? | Sensible ? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| URL de passerelle | `carriers/usps/gateway_url` |  | | | Sensible |
| URL de passerelle sécurisée | `carriers/usps/gateway_secure_url` |  | | | Sensible |
| Titre | `carriers/usps/title` |  | | | |
| Identifiant utilisateur | `carriers/usps/userid` |  | Chiffré | | Sensible |
| Mot de passe | `carriers/usps/password` |  | Chiffré | | Sensible |
| Identifiant utilisateur | `carriers/ups/username` |  | Chiffré | | Sensible |
| Mot de passe | `carriers/ups/password` |  | Chiffré | | Sensible |
| Numéro de licence d&#39;accès | `carriers/ups/access_license_number` |  | Chiffré | | Sensible |
| Tracking de l&#39;URL XML | `carriers/ups/tracking_xml_url` |  | | | Sensible |
| URL XML de la passerelle | `carriers/ups/gateway_xml_url` |  | | | Sensible |
| Numéro de l&#39;expéditeur | `carriers/ups/shipper_number` |  | | | Sensible |
| Déboguer | `carriers/ups/debug` |  | | | Sensible |
| ID de compte | `carriers/fedex/account` |  | Chiffré | | Sensible |
| Clé | `carriers/fedex/key` |  | Chiffré | | Sensible |
| Numéro du compteur | `carriers/fedex/meter_number` |  | Chiffré | | Sensible |
| Mot de passe | `carriers/fedex/password` |  | Chiffré | | Sensible |
| ID d’accès | `carriers/dhl/id` |  | Chiffré | | Sensible |
| Mot de passe | `carriers/dhl/password` |  | Chiffré | | Sensible |
| Déboguer | `carriers/dhl/debug` |  | | | |
| Numéro de compte | `carriers/dhl/account` |  | | | Sensible |
| URL de passerelle | `carriers/dhl/gateway_url` |  | | | Sensible |
| Mode Sandbox | `carriers/fedex/sandbox_mode` |  | | | Sensible |

{style="table-layout:auto"}

### Chemins sensibles aux ventes et spécifiques au système

Ces valeurs de configuration sont disponibles dans Admin dans **Magasins** > Paramètres > **Configuration** > **Ventes** > **Ventes**.

| Nom | Chemin de configuration | Prise en charge des versions de Commerce | Chiffré ? | Spécifique au système ? | Sensible ? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Nom du contact | `sales/magento_rma/store_name` | Commerce Enterprise uniquement | | | Sensible |
| Adresse Postale | `sales/magento_rma/address` | Commerce Enterprise uniquement | | | Sensible |
| Adresse Postale | `sales/magento_rma/address1` |  | | | Sensible |
| Ville | `sales/magento_rma/city` | Commerce Enterprise uniquement | | | Sensible |
| État/Province | `sales/magento_rma/region_id` | Commerce Enterprise uniquement | | | Sensible |
| Code postal | `sales/magento_rma/zip` | Commerce Enterprise uniquement | | | Sensible |
| Pays | `sales/magento_rma/country_id` | Commerce Enterprise uniquement | | | Sensible |
| Envoyer la copie d&#39;e-mail RMA à | `sales_email/magento_rma/copy_to` | Commerce Enterprise uniquement | | | Sensible |
| Envoyer la copie d&#39;e-mail d&#39;autorisation RMA à | `sales_email/magento_rma_auth/copy_to` | Commerce Enterprise uniquement | | | Sensible |
| Envoyer une copie d&#39;e-mail de commentaire RMA à | `sales_email/magento_rma_comment/copy_to` | Commerce Enterprise uniquement | | | Sensible |
| Envoyer une copie d&#39;e-mail de commentaire RMA à | `sales_email/magento_rma_customer_comment/copy_to` | Commerce Enterprise uniquement | | | Sensible |

{style="table-layout:auto"}

### Chemins d’accès aux API Google

Ces valeurs de configuration sont disponibles dans Admin dans l’API **Magasins** > Paramètres > **Configuration** > **Ventes** > **Google**.

| Nom | Chemin de configuration | Prise en charge des versions de Commerce | Chiffré ? | Spécifique au système ? | Sensible ? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Numéro de compte | `google/analytics/account` |  | | | Sensible |

{style="table-layout:auto"}

## Catégorie avancée

Cette section répertorie les noms de variables et les chemins de configuration disponibles pour les options dans Admin sous **Magasins** > Paramètres > **Configuration** > **Avancé**.

### Chemins d’accès sensibles et spécifiques au système pour les administrateurs

Ces valeurs de configuration sont disponibles dans Admin dans **Magasins** > Paramètres > **Configuration** > **Avancé** > **Admin**.

| Nom | Chemin de configuration | Prise en charge des versions de Commerce | Chiffré ? | Spécifique au système ? | Sensible ? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| URL d’administration personnalisée | `admin/url/custom` |  | | | Sensible |
| Chemin d’accès d’administration personnalisé | `admin/url/custom_path` |  | | | Sensible |

{style="table-layout:auto"}

### Chemins d’accès sensibles au système et spécifiques au système

Ces valeurs de configuration sont disponibles dans Admin dans **Magasins** > Paramètres > **Configuration** > **Avancé** > **Système**.

| Nom | Chemin de configuration | Prise en charge des versions de Commerce | Chiffré ? | Spécifique au système ? | Sensible ? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Destinataire de l’e-mail d’erreur | `system/magento_scheduled_import_export_log/error_email` |  | | | Sensible |
| Accéder à la liste | `system/full_page_cache/varnish/access_list` |  |  | | Sensible |
| Erreur de l’expéditeur de l’e-mail | `system/magento_scheduled_import_export_log/error_email_identity` |  |  | | Sensible |

{style="table-layout:auto"}

### Chemins d’accès spécifiques au système et sensibles au développeur

Ces valeurs de configuration sont disponibles dans Admin dans **Magasins** > Paramètres > **Configuration** > **Avancé** > **Développeur**.

| Nom | Chemin de configuration | Prise en charge des versions de Commerce | Chiffré ? | Spécifique au système ? | Sensible ? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Adresses IP autorisées (séparées par des virgules) | `dev/restrict/allow_ips` |  | | Spécifique au système | Sensible |

{style="table-layout:auto"}

## Catégorie avancée

Cette section répertorie les noms de variables et les chemins de configuration disponibles pour les options dans Admin sous **Magasins** > Paramètres > **Configuration** > **Avancé**.

### Chemins système

Ces valeurs de configuration sont disponibles dans Admin dans **Magasins** > Paramètres > **Configuration** > **Avancé** > **Système**.

| Nom | Chemin de configuration | Prise en charge des versions de Commerce | Chiffré ? | Spécifique au système ? | Sensible ? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Etablissement d&#39;accueil | `system/smtp/host` |  | | Spécifique au système | Sensible |
| Port (25) | `system/smtp/port` |  | | Spécifique au système | Sensible |
| Hôte principal | `system/full_page_cache/varnish/backend_host` |  | | Spécifique au système | Sensible |
| Port du serveur principal | `system/full_page_cache/varnish/backend_port` |  | | Spécifique au système | Sensible |

{style="table-layout:auto"}

### Chemins du développeur

Ces valeurs de configuration sont disponibles dans Admin dans **Magasins** > Paramètres > **Configuration** > **Avancé** > **Développeur**.

| Nom | Chemin de configuration | Prise en charge des versions de Commerce | Chiffré ? | Spécifique au système ? | Sensible ? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Consigner les erreurs JS dans la clé de stockage de session | `dev/js/session_storage_key` | ![Pas en mode Commerce uniquement](/help/assets/configuration/red-x.png) | | Spécifique au système | |

{style="table-layout:auto"}

## Chemins sensibles aux paiements et spécifiques au système

Cette section répertorie les noms de variables et les chemins de configuration disponibles pour les options dans Admin sous **Magasins** > Paramètres > **Configuration** > **Ventes** > **Paiement**.

### Variable générale

| Nom | Chemin de configuration | Prise en charge des versions de Commerce | Chiffré ? |
|--------------|--------------|--------------|--------------|
| Pays commerçant | `paypal/general/merchant_country` |  | Sensible |

{style="table-layout:auto"}

>[!INFO]
>
>Votre choix pour cette variable détermine les [chemins internationaux](#international-paths) que vous pouvez utiliser.

### Chemins d&#39;accès sensibles à PayPal et spécifiques au système

| Nom | Chemin de configuration | Prise en charge des versions de Commerce | Chiffré ? | Spécifique au système ? | Sensible ? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| E-mail associé au compte marchand PayPal (facultatif) | `paypal/general/business_account` |  | | | Sensible |
| ID de compte marchand | `payment/paypal_express/merchant_id` |  | | | Sensible |
| ID de l’éditeur | `payment/paypal_express_bml/publisher_id` |  | | | Sensible |
| Mot de passe | `paypal/fetch_reports/ftp_password` |  | Chiffré | | Sensible |
| Login | `paypal/fetch_reports/ftp_login` |  | Chiffré | | Sensible |
| Nom d’hôte ou adresse IP du point d’entrée personnalisé | `paypal/fetch_reports/ftp_ip` |  | | Spécifique au système | Sensible |
| Mode Sandbox | `paypal/fetch_reports/ftp_sandbox` |  | | Spécifique au système | |
| Mode de débogage | `payment/paypal_express/debug` |  | | Spécifique au système | |
| Mode de débogage | `payment/paypal_billing_agreement/debug` |  | | Spécifique au système | |
| Informations d’identification SFTP | `payment_all_paypal/express_checkout/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | Sensible |

{style="table-layout:auto"}

### Chemins d&#39;accès sensibles et spécifiques au système PayPal Payflow Pro

| Nom | Chemin de configuration | Prise en charge des versions de Commerce | Chiffré ? | Spécifique au système ? | Sensible ? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Utilisateur | `payment/payflow_advanced/user` |  | Chiffré | | Sensible |
| Mot de passe | `payment/payflow_advanced/pwd` |  | Chiffré | | Sensible |
| Chemin personnalisé | `paypal/fetch_reports/ftp_path` |  | | Spécifique au système | Sensible |
| Utilisateur | `payment/payflowpro/user` |  | Chiffré | | Sensible |
| Mot de passe | `payment/payflowpro/pwd` |  | Chiffré | Spécifique au système | Sensible |
| Mode Test | `payment/payflowpro/sandbox_flag` |  | | Spécifique au système | |
| Partenaire | `payment/payflowpro/partner` |  | | | Sensible |
| Hôte du proxy | `payment/payflowpro/proxy_host` |  | | Spécifique au système | Sensible |
| Port du proxy | `payment/payflowpro/proxy_port` |  | | Spécifique au système | Sensible |
| Mode de débogage | `payment/payflowpro/debug` |  | | Spécifique au système | |
| Informations d’identification SFTP | `payment_all_paypal/paypal_payflowpro/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` |  | | Spécifique au système | |
| Paramètres de carte de crédit | `payment_all_paypal/paypal_payflowpro/settings_paypal_payflow/heading_cc` |  | | | Sensible |

{style="table-layout:auto"}

### Chemins d&#39;accès sensibles et spécifiques au système PayPal Payflow Link

| Nom | Chemin de configuration | Prise en charge des versions de Commerce | Chiffré ? | Spécifique au système ? | Sensible ? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Utilisateur | `payment/payflow_link/user` |  | Chiffré | | Sensible |
| Mot de passe | `payment/payflow_link/pwd` |  | Chiffré | | Sensible |
| Mode Test | `payment/payflow_link/sandbox_flag` |  | | Spécifique au système | |
| Utiliser le proxy | `payment/payflow_link/use_proxy` |  | | Spécifique au système | |
| Hôte du proxy | `payment/payflow_link/proxy_host` |  | | Spécifique au système | |
| Port du proxy | `payment/payflow_link/proxy_port` |  |  | Spécifique au système | |
| Mode de débogage | `payment/payflow_link/debug` |  | | Spécifique au système | |
| Méthode pour l’URL d’annulation et l’URL de retour | `payment/payflow_link/url_method` |  | | Spécifique au système | |
| Mode de débogage | `payment/payflow_express/debug` |  | | Spécifique au système | |
| Informations d’identification SFTP | `payment_all_paypal/payflow_link/settings_payflow_link/settings_payflow_link_advanced/payflow_link_settlement_report/heading_sftp` |  | | | Sensible |

{style="table-layout:auto"}

### PayPal Payments Pro chemins sensibles et spécifiques au système

| Nom | Chemin de configuration | Prise en charge des versions de Commerce | Chiffré ? | Spécifique au système ? | Sensible ? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Nom d’utilisateur de l’API | `paypal/wpp/api_username` |  | Chiffré | | Sensible |
| Mot de passe de l’API | `paypal/wpp/api_password` |  | Chiffré | | Sensible |
| Signature d’API | `paypal/wpp/api_signature` |  | Chiffré | | Sensible |
| Certificat d’API | `paypal/wpp/api_cert` |  | | | Sensible |
| Hôte du proxy | `paypal/wpp/proxy_host` |  | | Spécifique au système | Sensible |
| Port du proxy | `paypal/wpp/proxy_port` |  | | Spécifique au système | Sensible |
| Mode Sandbox | `paypal/wpp/sandbox_flag` |  | | Spécifique au système | |
| Informations d’identification SFTP | `payment_all_paypal/payments_pro_hosted_solution_without_bml/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` |  | | | Sensible |

{style="table-layout:auto"}

### PayPal Payments Pro Hébergé chemins sensibles et spécifiques au système

| Nom | Chemin de configuration | Prise en charge des versions de Commerce | Chiffré ? | Spécifique au système ? | Sensible ? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Mode de débogage | `payment/hosted_pro/debug` |  | | Spécifique au système | |
| Informations d’identification SFTP | `payment_all_paypal/payments_pro_hosted_solution/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` |  | | | Sensible |
| Informations d’identification SFTP | `payment_au/paypal_group_all_in_one/payments_pro_hosted_solution_au/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` |  | | | Sensible |

{style="table-layout:auto"}

### Chemins d’accès spécifiques au système et sensibles à Braintree

| Nom | Chemin de configuration | Prise en charge des versions de Commerce | Chiffré ? | Spécifique au système ? | Sensible ? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Identifiant du commerçant | `payment/braintree/merchant_id` |  | | | Sensible |
| Clé Publique | `payment/braintree/public_key` |  | Chiffré | | Sensible |
| Clé Privée | `payment/braintree/private_key` |  | Chiffré | | Sensible |
| ID de compte marchand | `payment/braintree/merchant_account_id` |  | | | Sensible |
| ID commerçant du montant | `payment/braintree/kount_id` |  | | | Sensible |
| Remplacer le nom du commerçant | `payment/braintree_paypal/merchant_name_override` |  | | | Sensible |
| Téléphone | `payment/braintree/descriptor_phone` |  | | | Sensible |
| URL | `payment/braintree/descriptor_url` |  | | Spécifique au système | |

{style="table-layout:auto"}

### Chemins de chèques / mandats

| Nom | Chemin de configuration | Prise en charge des versions de Commerce | Chiffré ? | Spécifique au système ? | Sensible ? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Envoyer la vérification à | `payment/checkmo/mailing_address` |  | | | Sensible |
| Envoyer la vérification à | `payment_us/checkmo/mailing_address` |  | | | Sensible |

{style="table-layout:auto"}

### Chemins internationaux

| Nom | Chemin de configuration | Prise en charge des versions de Commerce | Chiffré ? | Spécifique au système ? | Sensible ? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Clé de transaction | `payment_au/authorizenet_directpost/trans_key` |  | Chiffré | Spécifique au système | Sensible |
| Mode Test | `payment_au/authorizenet_directpost/test` |  | | Spécifique au système | |
| URL de passerelle | `payment_au/authorizenet_directpost/cgi_url` |  | | Spécifique au système | Sensible |
| URL des détails de transaction | `payment_au/authorizenet_directpost/cgi_url_td` |  | | Spécifique au système | Sensible |
| Clé de transaction | `payment_au/cybersource/transaction_key` | Commerce Enterprise uniquement | Chiffré | Spécifique au système | Sensible |
| Clé d’accès | `payment_au/cybersource/access_key` | Commerce Enterprise uniquement | Chiffré | Spécifique au système | Sensible |
| Clé Secrète | `payment_au/cybersource/secret_key` | Commerce Enterprise uniquement | Chiffré | Spécifique au système | Sensible |
| Mode Test | `payment_au/cybersource/sandbox_flag` | Commerce Enterprise uniquement | | Spécifique au système | |
| Mot de passe de réponse au paiement | `payment_au/worldpay/response_password` | Commerce Enterprise uniquement | | Spécifique au système | Sensible |
| Mot de passe d’autorisation de l’administrateur distant | `payment_au/worldpay/auth_password` | Commerce Enterprise uniquement | | Spécifique au système | Sensible |
| Mode Sandbox | `payment_au/eway/sandbox_flag` | Commerce Enterprise uniquement | | Spécifique au système | |
| Clé API en direct | `payment_au/eway/live_api_key` | Commerce Enterprise uniquement | Chiffré | Spécifique au système | Sensible |
| Mot de passe de l’API Live | `payment_au/eway/live_api_password` | Commerce Enterprise uniquement | Chiffré | Spécifique au système | Sensible |
| Clé de chiffrement côté client en direct | `payment_au/eway/live_encryption_key` | Commerce Enterprise uniquement | Chiffré | Spécifique au système | Sensible |
| Clé API Sandbox | `payment_au/eway/sandbox_api_key` | Commerce Enterprise uniquement | Chiffré | Spécifique au système | Sensible |
| Mot de passe de l’API Sandbox | `payment_au/eway/sandbox_api_password` | Commerce Enterprise uniquement | Chiffré | Spécifique au système | Sensible |
| Clé de chiffrement côté client du sandbox | `payment_au/eway/sandbox_encryption_key` | Commerce Enterprise uniquement | Chiffré | Spécifique au système | Sensible |
| Clé de transaction | `payment_es/authorizenet_directpost/trans_key` |  | Chiffré | Spécifique au système | Sensible |
| Mode Test | `payment_es/authorizenet_directpost/test` |  | | Spécifique au système | |
| URL de passerelle | `payment_es/authorizenet_directpost/cgi_url` |  | | Spécifique au système | Sensible |
| URL des détails de transaction | `payment_es/authorizenet_directpost/cgi_url_td` |  | | Spécifique au système | Sensible |
| Clé de transaction | `payment_es/cybersource/transaction_key` | Commerce Enterprise uniquement | Chiffré | Spécifique au système | Sensible |
| Clé d’accès | `payment_es/cybersource/access_key` | Commerce Enterprise uniquement | Chiffré | Spécifique au système | Sensible |
| Clé Secrète | `payment_es/cybersource/secret_key` | Commerce Enterprise uniquement | Chiffré | Spécifique au système | Sensible |
| Mode Test | `payment_es/cybersource/sandbox_flag` | Commerce Enterprise uniquement | | Spécifique au système | |
| Mot de passe de réponse au paiement | `payment_es/worldpay/response_password` | Commerce Enterprise uniquement | | Spécifique au système | Sensible |
| Mot de passe d’autorisation de l’administrateur distant | `payment_es/worldpay/auth_password` | Commerce Enterprise uniquement | | Spécifique au système | Sensible |
| Secret MD5 pour les transactions | `payment_es/worldpay/md5_secret` | Commerce Enterprise uniquement | | Spécifique au système | Sensible |
| Déboguer | `payment_es/worldpay/debug` | Commerce Enterprise uniquement | | Spécifique au système | |
| Mode Sandbox | `payment_es/eway/sandbox_flag` | Commerce Enterprise uniquement | | Spécifique au système | |
| Clé API en direct | `payment_es/eway/live_api_key` | Commerce Enterprise uniquement | Chiffré | Spécifique au système | Sensible |
| Mot de passe de l’API Live | `payment_es/eway/live_api_password` | Commerce Enterprise uniquement | Chiffré | Spécifique au système | Sensible |
| Clé de chiffrement côté client en direct | `payment_es/eway/live_encryption_key` | Commerce Enterprise uniquement | Chiffré | Spécifique au système | Sensible |
| Clé API Sandbox | `payment_es/eway/sandbox_api_key` | Commerce Enterprise uniquement | Chiffré | Spécifique au système | Sensible |
| Mot de passe de l’API Sandbox | `payment_es/eway/sandbox_api_password` | Commerce Enterprise uniquement | Chiffré | Spécifique au système | Sensible |
| Clé de chiffrement côté client du sandbox | `payment_es/eway/sandbox_encryption_key` | Commerce Enterprise uniquement | Chiffré | Spécifique au système | Sensible |
| Clé de transaction | `payment_nz/authorizenet_directpost/trans_key` |  | Chiffré | Spécifique au système | Sensible |
| Mode Test | `payment_nz/authorizenet_directpost/test` |  | | Spécifique au système | |
| URL de passerelle | `payment_nz/authorizenet_directpost/cgi_url` |  | | Spécifique au système | Sensible |
| URL des détails de transaction | `payment_nz/authorizenet_directpost/cgi_url_td` |  | | Spécifique au système | Sensible |
| Mode Test | `payment_nz/cybersource/sandbox_flag` | Commerce Enterprise uniquement | | Spécifique au système | |
| Mode Test | `payment_nz/worldpay/sandbox_flag` | Commerce Enterprise uniquement | | Spécifique au système | |
| Mode Sandbox | `payment_nz/eway/sandbox_flag` | Commerce Enterprise uniquement | | Spécifique au système | |
| Clé API en direct | `payment_nz/eway/live_api_key` | Commerce Enterprise uniquement | Chiffré | Spécifique au système | Sensible |
| Mot de passe de l’API Live | `payment_nz/eway/live_api_password` | Commerce Enterprise uniquement | Chiffré | Spécifique au système | Sensible |
| Clé de chiffrement côté client en direct | `payment_nz/eway/live_encryption_key` | Commerce Enterprise uniquement | Chiffré | Spécifique au système | Sensible |
| Clé API Sandbox | `payment_nz/eway/sandbox_api_key` | Commerce Enterprise uniquement | Chiffré | | Sensible |
| Mot de passe de l’API Sandbox | `payment_nz/eway/sandbox_api_password` | Commerce Enterprise uniquement | Chiffré | Spécifique au système | Sensible |
| Clé de chiffrement côté client du sandbox | `payment_nz/eway/sandbox_encryption_key` | Commerce Enterprise uniquement | Chiffré | Spécifique au système | Sensible |
| Mode Test | `payment/payflow_advanced/sandbox_flag` |  | | Spécifique au système | |
| Hôte du proxy | `payment/payflow_advanced/proxy_host` |  | | Spécifique au système | Sensible |
| Port du proxy | `payment/payflow_advanced/proxy_port` |  | | Spécifique au système | |
| Mode de débogage | `payment/payflow_advanced/debug` |  | | Spécifique au système | |
| Méthode pour l’URL d’annulation et l’URL de retour | `payment/payflow_advanced/url_method` |  | | Spécifique au système | |
| Mode Test | `payment_us/authorizenet_directpost/test` |  | | Spécifique au système | |
| URL de passerelle | `payment_us/authorizenet_directpost/cgi_url` |  | | Spécifique au système | Sensible |
| URL des détails de transaction | `payment_us/authorizenet_directpost/cgi_url_td` |  | | Spécifique au système | Sensible |
| Clé d’accès | `payment_us/cybersource/access_key` | Commerce Enterprise uniquement | Chiffré | Spécifique au système | Sensible |
| Clé Secrète | `payment_us/cybersource/secret_key` | Commerce Enterprise uniquement | Chiffré | Spécifique au système | Sensible |
| Mode Test | `payment_us/cybersource/sandbox_flag` | Commerce Enterprise uniquement | | Spécifique au système | |
| Mode Test | `payment_us/worldpay/sandbox_flag` | Commerce Enterprise uniquement | | Spécifique au système | |
| Mode Sandbox | `payment_us/eway/sandbox_flag` | Commerce Enterprise uniquement | | Spécifique au système | |
| Clé API en direct | `payment_us/eway/live_api_key` | Commerce Enterprise uniquement | Chiffré | Spécifique au système | Sensible |
| Mot de passe de l’API Live | `payment_us/eway/live_api_password` | Commerce Enterprise uniquement | Chiffré | Spécifique au système | Sensible |
| Clé de chiffrement côté client en direct | `payment_us/eway/live_encryption_key` | Commerce Enterprise uniquement | Chiffré | Spécifique au système | Sensible |
| Clé API Sandbox | `payment_us/eway/sandbox_api_key` | Commerce Enterprise uniquement | Chiffré | Spécifique au système | Sensible |
| Mot de passe de l’API Sandbox | `payment_us/eway/sandbox_api_password` | Commerce Enterprise uniquement | Chiffré | Spécifique au système | Sensible |
| Clé de chiffrement côté client du sandbox | `payment_us/eway/sandbox_encryption_key` | Commerce Enterprise uniquement | Chiffré | Spécifique au système | |
| Mode Test | `payment_gb/cybersource/sandbox_flag` | Commerce Enterprise uniquement | | Spécifique au système | |
| Mode Test | `payment_gb/authorizenet_directpost/test` |  | | Spécifique au système | |
| URL de passerelle | `payment_gb/authorizenet_directpost/cgi_url` |  | | Spécifique au système | Sensible |
| URL des détails de transaction | `payment_gb/authorizenet_directpost/cgi_url_td` |  | | Spécifique au système | Sensible |
| Mode Test | `payment_gb/worldpay/sandbox_flag` | Commerce Enterprise uniquement | | Spécifique au système | |
| Mode Sandbox | `payment_gb/eway/sandbox_flag` | Commerce Enterprise uniquement | | Spécifique au système | |
| Clé API en direct | `payment_gb/eway/live_api_key` | Commerce Enterprise uniquement | Chiffré | Spécifique au système | Sensible |
| Mot de passe de l’API Live | `payment_gb/eway/live_api_password` | Commerce Enterprise uniquement | Chiffré | Spécifique au système | Sensible |
| Clé de chiffrement côté client en direct | `payment_gb/eway/live_encryption_key` | Commerce Enterprise uniquement | Chiffré | Spécifique au système | Sensible |
| Clé API Sandbox | `payment_gb/eway/sandbox_api_key` | Commerce Enterprise uniquement | Chiffré | Spécifique au système | Sensible |
| Mot de passe de l’API Sandbox | `payment_gb/eway/sandbox_api_password` | Commerce Enterprise uniquement | Chiffré | Spécifique au système | Sensible |
| Clé de chiffrement côté client du sandbox | `payment_gb/eway/sandbox_encryption_key` | Commerce Enterprise uniquement | Chiffré | Spécifique au système | Sensible |
| Clé de transaction | `payment_de/cybersource/transaction_key` | Commerce Enterprise uniquement | Chiffré | Spécifique au système | Sensible |
| Clé d’accès | `payment_de/cybersource/access_key` | Commerce Enterprise uniquement | Chiffré | Spécifique au système | Sensible |
| Clé Secrète | `payment_de/cybersource/secret_key` | Commerce Enterprise uniquement | Chiffré | Spécifique au système | Sensible |
| Mode Test | `payment_de/cybersource/sandbox_flag` | Commerce Enterprise uniquement | | Spécifique au système | |
| Clé de transaction | `payment_de/authorizenet_directpost/trans_key` |  | Chiffré | Spécifique au système | Sensible |
| Mode Test | `payment_de/authorizenet_directpost/test` |  | | Spécifique au système | |
| URL de passerelle | `payment_de/authorizenet_directpost/cgi_url` |  | | Spécifique au système | Sensible |
| URL des détails de transaction | `payment_de/authorizenet_directpost/cgi_url_td` |  | | Spécifique au système | Sensible |
| Mot de passe de réponse au paiement | `payment_de/worldpay/response_password` | Commerce Enterprise uniquement | | Spécifique au système | Sensible |
| Mot de passe d’autorisation de l’administrateur distant | `payment_de/worldpay/auth_password` | Commerce Enterprise uniquement | | Spécifique au système | Sensible |
| Déboguer | `payment_de/worldpay/debug` | Commerce Enterprise uniquement | | Spécifique au système | |
| Mode Sandbox | `payment_de/eway/sandbox_flag` | Commerce Enterprise uniquement | | Spécifique au système | |
| Clé API en direct | `payment_de/eway/live_api_key` | Commerce Enterprise uniquement | Chiffré | Spécifique au système | Sensible |
| Mot de passe de l’API Live | `payment_de/eway/live_api_password` | Commerce Enterprise uniquement | Chiffré | Spécifique au système | Sensible |
| Clé de chiffrement côté client en direct | `payment_de/eway/live_encryption_key` | Commerce Enterprise uniquement | Chiffré | Spécifique au système | Sensible |
| Clé API Sandbox | `payment_de/eway/sandbox_api_key` | Commerce Enterprise uniquement | Chiffré | Spécifique au système | Sensible |
| Mot de passe de l’API Sandbox | `payment_de/eway/sandbox_api_password` | Commerce Enterprise uniquement | Chiffré | Spécifique au système | Sensible |
| Clé de chiffrement côté client du sandbox | `payment_de/eway/sandbox_encryption_key` | Commerce Enterprise uniquement | Chiffré | Spécifique au système | Sensible |
| Clé de transaction | `payment_other/authorizenet_directpost/trans_key` |  | Chiffré | Spécifique au système | Sensible |
| Mode Test | `payment_other/authorizenet_directpost/test` |  | | Spécifique au système | Sensible |
| URL de passerelle | `payment_other/authorizenet_directpost/cgi_url` |  | | Spécifique au système | Sensible |
| URL des détails de transaction | `payment_other/authorizenet_directpost/cgi_url_td` |  | | Spécifique au système | |
| Clé de transaction | `payment_other/cybersource/transaction_key` | Commerce Enterprise uniquement | Chiffré | Spécifique au système | Sensible |
| Clé d’accès | `payment_other/cybersource/access_key` | Commerce Enterprise uniquement | Chiffré | Spécifique au système | Sensible |
| Clé Secrète | `payment_other/cybersource/secret_key` | Commerce Enterprise uniquement | Chiffré | Spécifique au système | Sensible |
| Statut de la nouvelle commande | `payment_other/cybersource/order_status` | Commerce Enterprise uniquement | | Spécifique au système | |
| Mode Test | `payment_other/cybersource/sandbox_flag` | Commerce Enterprise uniquement | | Spécifique au système | |
| Mot de passe de réponse au paiement | `payment_other/worldpay/response_password` | Commerce Enterprise uniquement | | Spécifique au système | Sensible |
| Mot de passe d’autorisation de l’administrateur distant | `payment_other/worldpay/auth_password` | Commerce Enterprise uniquement | | Spécifique au système | Sensible |
| Mode Test | `payment_other/worldpay/sandbox_flag` | Commerce Enterprise uniquement | | Spécifique au système | |
| Mode Sandbox | `payment_other/eway/sandbox_flag` | Commerce Enterprise uniquement | | Spécifique au système | |
| Clé API en direct | `payment_other/eway/live_api_key` | Commerce Enterprise uniquement | Chiffré | Spécifique au système | Sensible |
| Mot de passe de l’API Live | `payment_other/eway/live_api_password` | Commerce Enterprise uniquement | Chiffré | Spécifique au système | Sensible |
| Clé de chiffrement côté client en direct | `payment_other/eway/live_encryption_key` | Commerce Enterprise uniquement | Chiffré | Spécifique au système | Sensible |
| Clé API Sandbox | `payment_other/eway/sandbox_api_key` | Commerce Enterprise uniquement | Chiffré | Spécifique au système | Sensible |
| Mot de passe de l’API Sandbox | `payment_other/eway/sandbox_api_password` | Commerce Enterprise uniquement | Chiffré | Spécifique au système | Sensible |
| Clé de chiffrement côté client du sandbox | `payment_other/eway/sandbox_encryption_key` | Commerce Enterprise uniquement | Chiffré | Spécifique au système | Sensible |
| Clé de transaction | `payment_ca/authorizenet_directpost/trans_key` |  | Chiffré | Spécifique au système | Sensible |
| Mode Test | `payment_ca/authorizenet_directpost/test` |  | | Spécifique au système | |
| URL de passerelle | `payment_ca/authorizenet_directpost/cgi_url` |  | | Spécifique au système | Sensible |
| URL des détails de transaction | `payment_ca/authorizenet_directpost/cgi_url_td` |  | | Spécifique au système | Sensible |
| Clé de transaction | `payment_ca/cybersource/transaction_key` | Commerce Enterprise uniquement | Chiffré | Spécifique au système | Sensible |
| Clé d’accès | `payment_ca/cybersource/access_key` | Commerce Enterprise uniquement | Chiffré | Spécifique au système | Sensible |
| Clé Secrète | `payment_ca/cybersource/secret_key` | Commerce Enterprise uniquement | Chiffré | Spécifique au système | Sensible |
| Statut de la nouvelle commande | `payment_ca/cybersource/order_status` | Commerce Enterprise uniquement | | | |
| Mode Test | `payment_ca/cybersource/sandbox_flag` | Commerce Enterprise uniquement | | Spécifique au système | |
| Mot de passe de réponse au paiement | `payment_ca/worldpay/response_password` | Commerce Enterprise uniquement | | Spécifique au système | |
| Mot de passe d’autorisation de l’administrateur distant | `payment_ca/worldpay/auth_password` | Commerce Enterprise uniquement | | Spécifique au système | Sensible |
| Mode Test | `payment_ca/worldpay/sandbox_flag` | Commerce Enterprise uniquement | | Spécifique au système | |
| Mode Sandbox | `payment_ca/eway/sandbox_flag` | Commerce Enterprise uniquement | | Spécifique au système | |
| Clé API en direct | `payment_ca/eway/live_api_key` | Commerce Enterprise uniquement | Chiffré | Spécifique au système | Sensible |
| Mot de passe de l’API Live | `payment_ca/eway/live_api_password` | Commerce Enterprise uniquement | Chiffré | Spécifique au système | Sensible |
| Clé de chiffrement côté client en direct | `payment_ca/eway/live_encryption_key` | Commerce Enterprise uniquement | Chiffré | Spécifique au système | Sensible |
| Clé API Sandbox | `payment_ca/eway/sandbox_api_key` | Commerce Enterprise uniquement | Chiffré | | Sensible |
| Mot de passe de l’API Sandbox | `payment_ca/eway/sandbox_api_password` | Commerce Enterprise uniquement | Chiffré | Spécifique au système | Sensible |
| Clé de chiffrement côté client du sandbox | `payment_ca/eway/sandbox_encryption_key` | Commerce Enterprise uniquement | Chiffré | Spécifique au système | Sensible |
| Clé de transaction | `payment_hk/authorizenet_directpost/trans_key` |  | Chiffré | Spécifique au système | Sensible |
| Mode Test | `payment_hk/authorizenet_directpost/test` |  | | Spécifique au système | |
| URL de passerelle | `payment_hk/authorizenet_directpost/cgi_url` |  | | | Sensible |
| URL des détails de transaction | `payment_hk/authorizenet_directpost/cgi_url_td` |  | | Spécifique au système | Sensible |
| Clé de transaction | `payment_hk/cybersource/transaction_key` | Commerce Enterprise uniquement | Chiffré | Spécifique au système | Sensible |
| Clé d’accès | `payment_hk/cybersource/access_key` | Commerce Enterprise uniquement | Chiffré | Spécifique au système | Sensible |
| Clé Secrète | `payment_hk/cybersource/secret_key` | Commerce Enterprise uniquement | Chiffré | Spécifique au système | Sensible |
| Mode Test | `payment_hk/cybersource/sandbox_flag` | Commerce Enterprise uniquement | | Spécifique au système | Sensible |
| Mot de passe de réponse au paiement | `payment_hk/worldpay/response_password` | Commerce Enterprise uniquement | | Spécifique au système | Sensible |
| Mot de passe d’autorisation de l’administrateur distant | `payment_hk/worldpay/auth_password` | Commerce Enterprise uniquement | | Spécifique au système | Sensible |
| Mode Test | `payment_hk/worldpay/sandbox_flag` | Commerce Enterprise uniquement | | Spécifique au système | Sensible |
| Clé API en direct | `payment_hk/eway/live_api_key` | Commerce Enterprise uniquement | Chiffré | | Sensible |
| Mot de passe de l’API Live | `payment_hk/eway/live_api_password` | Commerce Enterprise uniquement | Chiffré | Spécifique au système | Sensible |
| Clé de chiffrement côté client en direct | `payment_hk/eway/live_encryption_key` | Commerce Enterprise uniquement | Chiffré | Spécifique au système | Sensible |
| Clé API Sandbox | `payment_hk/eway/sandbox_api_key` | Commerce Enterprise uniquement | Chiffré | Spécifique au système | Sensible |
| Mot de passe de l’API Sandbox | `payment_hk/eway/sandbox_api_password` | Commerce Enterprise uniquement | Chiffré | Spécifique au système | Sensible |
| Clé de chiffrement côté client du sandbox | `payment_hk/eway/sandbox_encryption_key` | Commerce Enterprise uniquement | Chiffré | Spécifique au système | Sensible |
| Clé de transaction | `payment_jp/authorizenet_directpost/trans_key` |  | Chiffré | Spécifique au système | Sensible |
| Mode Test | `payment_jp/authorizenet_directpost/test` |  | | Spécifique au système | |
| URL de passerelle | `payment_jp/authorizenet_directpost/cgi_url` |  | | Spécifique au système | Sensible |
| URL des détails de transaction | `payment_jp/authorizenet_directpost/cgi_url_td` |  | | Spécifique au système | Sensible |
| Clé de transaction | `payment_jp/cybersource/transaction_key` | Commerce Enterprise uniquement | Chiffré | Spécifique au système | Sensible |
| Clé d’accès | `payment_jp/cybersource/access_key` | Commerce Enterprise uniquement | Chiffré | Spécifique au système | Sensible |
| Clé Secrète | `payment_jp/cybersource/secret_key` | Commerce Enterprise uniquement | Chiffré | Spécifique au système | Sensible |
| Statut de la nouvelle commande | `payment_jp/cybersource/order_status` | Commerce Enterprise uniquement | | Spécifique au système | |
| Mode Test | `payment_jp/cybersource/sandbox_flag` | Commerce Enterprise uniquement | | Spécifique au système | |
| Mot de passe de réponse au paiement | `payment_jp/worldpay/response_password` | Commerce Enterprise uniquement | | Spécifique au système | Sensible |
| Mot de passe d’autorisation de l’administrateur distant | `payment_jp/worldpay/auth_password` | Commerce Enterprise uniquement | | Spécifique au système | Sensible |
| Mode Test | `payment_jp/worldpay/sandbox_flag` | Commerce Enterprise uniquement | | Spécifique au système | |
| Mode Sandbox | `payment_jp/eway/sandbox_flag` | Commerce Enterprise uniquement | | Spécifique au système | |
| Clé API en direct | `payment_jp/eway/live_api_key` | Commerce Enterprise uniquement | Chiffré | Spécifique au système | Sensible |
| Mot de passe de l’API Live | `payment_jp/eway/live_api_password` | Commerce Enterprise uniquement | Chiffré | Spécifique au système | Sensible |
| Clé de chiffrement côté client en direct | `payment_jp/eway/live_encryption_key` | Commerce Enterprise uniquement | Chiffré | Spécifique au système | Sensible |
| Clé API Sandbox | `payment_jp/eway/sandbox_api_key` | Commerce Enterprise uniquement | Chiffré | Spécifique au système | Sensible |
| Mot de passe de l’API Sandbox | `payment_jp/eway/sandbox_api_password` | Commerce Enterprise uniquement | Chiffré | Spécifique au système | Sensible |
| Clé de chiffrement côté client du sandbox | `payment_jp/eway/sandbox_encryption_key` | Commerce Enterprise uniquement | Chiffré | Spécifique au système | Sensible |
| Clé de transaction | `payment_fr/authorizenet_directpost/trans_key` |  | Chiffré | Spécifique au système | Sensible |
| Mode Test | `payment_fr/authorizenet_directpost/test` |  | | Spécifique au système | |
| URL de passerelle | `payment_fr/authorizenet_directpost/cgi_url` |  | | Spécifique au système | Sensible |
| URL des détails de transaction | `payment_fr/authorizenet_directpost/cgi_url_td` |  | | Spécifique au système | Sensible |
| Clé de transaction | `payment_fr/cybersource/transaction_key` | Commerce Enterprise uniquement | Chiffré | Spécifique au système | Sensible |
| Clé d’accès | `payment_fr/cybersource/access_key` | Commerce Enterprise uniquement | Chiffré | Spécifique au système | Sensible |
| Clé Secrète | `payment_fr/cybersource/secret_key` | Commerce Enterprise uniquement | Chiffré | Spécifique au système | Sensible |
| Mode Test | `payment_fr/cybersource/sandbox_flag` | Commerce Enterprise uniquement | | Spécifique au système | |
| Mot de passe de réponse au paiement | `payment_fr/worldpay/response_password` | Commerce Enterprise uniquement | | Spécifique au système | Sensible |
| Mot de passe d’autorisation de l’administrateur distant | `payment_fr/worldpay/auth_password` | Commerce Enterprise uniquement | | Spécifique au système | Sensible |
| Mode Test | `payment_fr/worldpay/sandbox_flag` | Commerce Enterprise uniquement |  | Spécifique au système | |
| Mode Sandbox | `payment_fr/eway/sandbox_flag` | Commerce Enterprise uniquement | | Spécifique au système | |
| Clé API en direct | `payment_fr/eway/live_api_key` | Commerce Enterprise uniquement | Chiffré | Spécifique au système | Sensible |
| Mot de passe de l’API Live | `payment_fr/eway/live_api_password` | Commerce Enterprise uniquement | Chiffré | Spécifique au système | Sensible |
| Clé de chiffrement côté client en direct | `payment_fr/eway/live_encryption_key` | Commerce Enterprise uniquement | Chiffré | Spécifique au système | Sensible |
| Clé API Sandbox | `payment_fr/eway/sandbox_api_key` | Commerce Enterprise uniquement | Chiffré | Spécifique au système | Sensible |
| Mot de passe de l’API Sandbox | `payment_fr/eway/sandbox_api_password` | Commerce Enterprise uniquement | Chiffré | Spécifique au système | Sensible |
| Clé de chiffrement côté client du sandbox | `payment_fr/eway/sandbox_encryption_key` | Commerce Enterprise uniquement | Chiffré | Spécifique au système | Sensible |
| Clé de transaction | `payment_it/authorizenet_directpost/trans_key` |  | Chiffré | Spécifique au système | Sensible |
| Mode Test | `payment_it/authorizenet_directpost/test` |  | | Spécifique au système | |
| URL de passerelle | `payment_it/authorizenet_directpost/cgi_url` |  | | Spécifique au système | Sensible |
| URL des détails de transaction | `payment_it/authorizenet_directpost/cgi_url_td` |  | | Spécifique au système | Sensible |
| Clé de transaction | `payment_it/cybersource/transaction_key` | Commerce Enterprise uniquement | Chiffré | Spécifique au système | Sensible |
| Clé d’accès | `payment_it/cybersource/access_key` | Commerce Enterprise uniquement | Chiffré | Spécifique au système | Sensible |
| Clé Secrète | `payment_it/cybersource/secret_key` | Commerce Enterprise uniquement | Chiffré | Spécifique au système | Sensible |
| Mode Test | `payment_it/cybersource/sandbox_flag` | Commerce Enterprise uniquement | | Spécifique au système | |
| Mot de passe de réponse au paiement | `payment_it/worldpay/response_password` | Commerce Enterprise uniquement | | Spécifique au système | Sensible |
| Mot de passe d’autorisation de l’administrateur distant | `payment_it/worldpay/auth_password` | Commerce Enterprise uniquement | | Spécifique au système | Sensible |
| Mode Test | `payment_it/worldpay/sandbox_flag` | Commerce Enterprise uniquement | | Spécifique au système | |
| Mode Sandbox | `payment_it/eway/sandbox_flag` | Commerce Enterprise uniquement | | Spécifique au système | |
| Clé API en direct | `payment_it/eway/live_api_key` | Commerce Enterprise uniquement | Chiffré | Spécifique au système | Sensible |
| Mot de passe de l’API Live | `payment_it/eway/live_api_password` | Commerce Enterprise uniquement | Chiffré | Spécifique au système | Sensible |
| Clé de chiffrement côté client en direct | `payment_it/eway/live_encryption_key` | Commerce Enterprise uniquement | Chiffré | Spécifique au système | Sensible |
| Clé API Sandbox | `payment_it/eway/sandbox_api_key` | Commerce Enterprise uniquement | Chiffré | Spécifique au système | Sensible |
| Mot de passe de l’API Sandbox | `payment_it/eway/sandbox_api_password` | Commerce Enterprise uniquement | Chiffré | Spécifique au système | Sensible |
| Clé de chiffrement côté client du sandbox | `payment_it/eway/sandbox_encryption_key` | Commerce Enterprise uniquement | Chiffré | Spécifique au système | Sensible |
| Clé API | `fraud_protection/signifyd/api_key` | Commerce Enterprise uniquement | Chiffré | Spécifique au système | Sensible |
| URL DE L’API | `fraud_protection/signifyd/api_url` | Commerce Enterprise uniquement |  | Spécifique au système | Sensible |
| Informations d’identification SFTP | `payment_au/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | Sensible |
| Informations d’identification SFTP | `payment_au/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | Sensible |
| Informations d’identification SFTP | `payment_au/paypal_payment_gateways/paypal_payflowpro_au/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` |  | | | Sensible |
| ID de connexion à l’API | `payment_au/authorizenet_directpost/login` |  | Chiffré | | Sensible |
| Marchand MD5 | `payment_au/authorizenet_directpost/trans_md5` |  | Chiffré | | Sensible |
| Envoyer un e-mail au client | `payment_au/authorizenet_directpost/email_customer` |  | | | Sensible |
| Adresse électronique du commerçant | `payment_au/authorizenet_directpost/merchant_email` |  | | | Sensible |
| ID d’installation de l’administrateur distant | `payment_au/worldpay/admin_installation_id` | Commerce Enterprise uniquement | | | Sensible |
| Secret MD5 pour les transactions | `payment_au/worldpay/md5_secret` | Commerce Enterprise uniquement | | | Sensible |
| Informations d’identification SFTP | `payment_es/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | Sensible |
| Informations d’identification SFTP | `payment_es/paypal_group_all_in_one/payments_pro_hosted_solution_es/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` |  | | | Sensible |
| Informations d’identification SFTP | `payment_es/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | Sensible |
| Envoyer la vérification à | `payment_es/checkmo/mailing_address` |  | | | Sensible |
| ID de connexion à l’API | `payment_es/authorizenet_directpost/login` |  | Chiffré | | Sensible |
| Marchand MD5 | `payment_es/authorizenet_directpost/trans_md5` |  | Chiffré | | Sensible |
| Envoyer un e-mail au client | `payment_es/authorizenet_directpost/email_customer` |  | | | Sensible |
| Adresse électronique du commerçant | `payment_es/authorizenet_directpost/merchant_email` |  | | | Sensible |
| Identifiant du commerçant | `payment_es/cybersource/merchant_id` | Commerce Enterprise uniquement | Chiffré | | Sensible |
| Identifiant du profil | `payment_es/cybersource/profile_id` | Commerce Enterprise uniquement | Chiffré | | Sensible |
| ID d’installation de l’administrateur distant | `payment_es/worldpay/admin_installation_id` | Commerce Enterprise uniquement | | | Sensible |
| Informations d’identification SFTP | `payment_nz/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | Sensible |
| Informations d’identification SFTP | | | | | |
| Informations d’identification SFTP | `payment_nz/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | Sensible |
| Informations d’identification SFTP | `payment_nz/paypal_payment_gateways/paypal_payflowpro_nz/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` |  | | | Sensible |
| ID de connexion à l’API | `payment_nz/authorizenet_directpost/login` |  | Chiffré | | Sensible |
| Marchand MD5 | `payment_nz/authorizenet_directpost/trans_md5` |  | Chiffré | | Sensible |
| Envoyer un e-mail au client | `payment_nz/authorizenet_directpost/email_customer` |  | | | Sensible |
| Adresse électronique du commerçant | `payment_nz/authorizenet_directpost/merchant_email` |  | | | Sensible |
| Identifiant du commerçant | `payment_nz/cybersource/merchant_id` | Commerce Enterprise uniquement | Chiffré | | Sensible |
| Clé de transaction | `payment_nz/cybersource/transaction_key` | Commerce Enterprise uniquement | Chiffré | | Sensible |
| Identifiant du profil | `payment_nz/cybersource/profile_id` | Commerce Enterprise uniquement | Chiffré | | Sensible |
| Clé d’accès | `payment_nz/cybersource/access_key` | Commerce Enterprise uniquement | Chiffré | | Sensible |
| Clé Secrète | `payment_nz/cybersource/secret_key` | Commerce Enterprise uniquement | Chiffré | | Sensible |
| ID d’installation | `payment_nz/worldpay/installation_id` | Commerce Enterprise uniquement | | | Sensible |
| Mot de passe de réponse au paiement | `payment_nz/worldpay/response_password` | Commerce Enterprise uniquement | | | Sensible |
| ID d’installation de l’administrateur distant | `payment_nz/worldpay/admin_installation_id` | Commerce Enterprise uniquement | | | Sensible |
| Mot de passe d’autorisation de l’administrateur distant | `payment_nz/worldpay/auth_password` | Commerce Enterprise uniquement | | | Sensible |
| Secret MD5 pour les transactions | `payment_nz/worldpay/md5_secret` | Commerce Enterprise uniquement | | | Sensible |
| Informations d’identification SFTP | `payment_us/paypal_alternative_payment_methods/express_checkout_us/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | Sensible |
| Informations d’identification SFTP | `payment_us/paypal_group_all_in_one/payflow_advanced/settings_payments_advanced/settings_payments_advanced_advanced/settlement_report/heading_sftp` |  | | | Sensible |
| Informations d’identification SFTP | `payment_us/paypal_group_all_in_one/wpp_usuk/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` |  | | | Sensible |
| Informations d’identification SFTP | `payment_us/paypal_group_all_in_one/wps_express/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | Sensible |
| Informations d’identification SFTP | `payment_us/paypal_payment_gateways/paypal_payflowpro_with_express_checkout/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` |  | | | Sensible |
| Informations d’identification SFTP | `payment_us/paypal_payment_gateways/payflow_link_us/settings_payflow_link/settings_payflow_link_advanced/payflow_link_settlement_report/heading_sftp` |  | | | Sensible |
| ID de connexion à l’API | `payment_us/authorizenet_directpost/login` |  | Chiffré | | Sensible |
| Clé de transaction | `payment_us/authorizenet_directpost/trans_key` |  | Chiffré | | Sensible |
| Marchand MD5 | `payment_us/authorizenet_directpost/trans_md5` |  | Chiffré | | Sensible |
| Envoyer un e-mail au client | `payment_us/authorizenet_directpost/email_customer` |  | | | Sensible |
| Adresse électronique du commerçant | `payment_us/authorizenet_directpost/merchant_email` |  | | | Sensible |
| Identifiant du commerçant | `payment_us/cybersource/merchant_id` | Commerce Enterprise uniquement | Chiffré | | Sensible |
| Clé de transaction | `payment_us/cybersource/transaction_key` | Commerce Enterprise uniquement | Chiffré | | Sensible |
| Identifiant du profil | `payment_us/cybersource/profile_id` | Commerce Enterprise uniquement | Chiffré | | Sensible |
| ID d’installation | `payment_us/worldpay/installation_id` | Commerce Enterprise uniquement | | | Sensible |
| Mot de passe de réponse au paiement | `payment_us/worldpay/response_password` | Commerce Enterprise uniquement | | | Sensible |
| ID d’installation de l’administrateur distant | `payment_us/worldpay/admin_installation_id` | Commerce Enterprise uniquement | | | Sensible |
| Mot de passe d’autorisation de l’administrateur distant | `payment_us/worldpay/auth_password` | Commerce Enterprise uniquement | | | Sensible |
| Secret MD5 pour les transactions | `payment_us/worldpay/md5_secret` | Commerce Enterprise uniquement | | | Sensible |
| Informations d’identification SFTP | `payment_gb/paypal_alternative_payment_methods/express_checkout_gb/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  |  | | Sensible |
| Informations d’identification SFTP | `payment_gb/paypal_group_all_in_one/payments_pro_hosted_solution_with_express_checkout/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` |  | | | Sensible |
| Informations d’identification SFTP | `payment_gb/paypal_group_all_in_one/wps_express/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | Sensible |
| Envoyer la vérification à | `payment_gb/checkmo/mailing_address` |  | | | Sensible |
| Identifiant du commerçant | `payment_gb/cybersource/merchant_id` | Commerce Enterprise uniquement | Chiffré | | Sensible |
| Clé de transaction | `payment_gb/cybersource/transaction_key` | Commerce Enterprise uniquement | Chiffré | | Sensible |
| Identifiant du profil | `payment_gb/cybersource/profile_id` | Commerce Enterprise uniquement | Chiffré | | Sensible |
| Clé d’accès | `payment_gb/cybersource/access_key` | Commerce Enterprise uniquement | Chiffré | | Sensible |
| Clé Secrète | `payment_gb/cybersource/secret_key` | Commerce Enterprise uniquement | Chiffré | | Sensible |
| ID de connexion à l’API | `payment_gb/authorizenet_directpost/login` |  | Chiffré | | Sensible |
| Clé de transaction | `payment_gb/authorizenet_directpost/trans_key` |  | Chiffré | | Sensible |
| Marchand MD5 | `payment_gb/authorizenet_directpost/trans_md5` |  | Chiffré | | Sensible |
| Envoyer un e-mail au client | `payment_gb/authorizenet_directpost/email_customer` |  | | | Sensible |
| Adresse électronique du commerçant | `payment_gb/authorizenet_directpost/merchant_email` |  |  | | Sensible |
| ID d’installation | `payment_gb/worldpay/installation_id` | Commerce Enterprise uniquement | | | Sensible |
| Mot de passe de réponse au paiement | `payment_gb/worldpay/response_password` | Commerce Enterprise uniquement | | | Sensible |
| ID d’installation de l’administrateur distant | `payment_gb/worldpay/admin_installation_id` | Commerce Enterprise uniquement | | | Sensible |
| Mot de passe d’autorisation de l’administrateur distant | `payment_gb/worldpay/auth_password` | Commerce Enterprise uniquement | | | Sensible |
| Informations d’identification SFTP | `payment_de/paypal_payment_solutions/express_checkout_de/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | Sensible |
| Rendre un chèque payable à | `payment_de/checkmo/payable_to` |  | | | Sensible |
| Envoyer la vérification à | `payment_de/checkmo/mailing_address` |  | | | Sensible |
| Identifiant du commerçant | `payment_de/cybersource/merchant_id` | Commerce Enterprise uniquement | Chiffré | | Sensible |
| Identifiant du profil | `payment_de/cybersource/profile_id` | Commerce Enterprise uniquement | Chiffré | | Sensible |
| ID de connexion à l’API | `payment_de/authorizenet_directpost/login` |  | Chiffré | | Sensible |
| Marchand MD5 | `payment_de/authorizenet_directpost/trans_md5` |  | Chiffré | | Sensible |
| Envoyer un e-mail au client | `payment_de/authorizenet_directpost/email_customer` |  | | | Sensible |
| Adresse électronique du commerçant | `payment_de/authorizenet_directpost/merchant_email` |  | | | Sensible |
| ID d’installation | `payment_de/worldpay/installation_id` | Commerce Enterprise uniquement | | | |
| ID d’installation de l’administrateur distant | `payment_de/worldpay/admin_installation_id` | Commerce Enterprise uniquement | | | Sensible |
| Secret MD5 pour les transactions | `payment_de/worldpay/md5_secret` | Commerce Enterprise uniquement | | | Sensible |
| Informations d’identification SFTP | `payment_other/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  |  | | Sensible |
| Informations d’identification SFTP | `payment_other/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | Sensible |
| Rendre un chèque payable à | `payment_other/checkmo/payable_to` |  | | | Sensible |
| Envoyer la vérification à | `payment_other/checkmo/mailing_address` |  | | | Sensible |
| ID de connexion à l’API | `payment_other/authorizenet_directpost/login` |  | Chiffré | | Sensible |
| Marchand MD5 | `payment_other/authorizenet_directpost/trans_md5` |  | Chiffré | | Sensible |
| Statut de la nouvelle commande | `payment_other/authorizenet_directpost/order_status` |  | | | Sensible |
| Adresse électronique du commerçant | `payment_other/authorizenet_directpost/merchant_email` |  | | | Sensible |
| Identifiant du commerçant | `payment_other/cybersource/merchant_id` | Commerce Enterprise uniquement | Chiffré | | Sensible |
| Identifiant du profil | `payment_other/cybersource/profile_id` | Commerce Enterprise uniquement | Chiffré | | Sensible |
| ID d’installation | `payment_other/worldpay/installation_id` | Commerce Enterprise uniquement | | | Sensible |
| ID d’installation de l’administrateur distant | `payment_other/worldpay/admin_installation_id` | Commerce Enterprise uniquement | | | Sensible |
| Secret MD5 pour les transactions | `payment_other/worldpay/md5_secret` | Commerce Enterprise uniquement | | | Sensible |
| Informations d’identification SFTP | `payment_ca/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | Sensible |
| Informations d’identification SFTP | `payment_ca/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | Sensible |
| Informations d’identification SFTP | `payment_ca/paypal_payment_gateways/wpp_ca/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` |  | | | Sensible |
| Informations d’identification SFTP | `payment_ca/paypal_payment_gateways/paypal_payflowpro_ca/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` |  | | | Sensible |
| Informations d’identification SFTP | `payment_ca/paypal_payment_gateways/payflow_link_ca/settings_payflow_link/settings_payflow_link_advanced/payflow_link_settlement_report/heading_sftp` |  | | | Sensible |
| Rendre un chèque payable à | `payment_ca/checkmo/payable_to` |  | | | Sensible |
| Envoyer la vérification à | `payment_ca/checkmo/mailing_address` |  | | | Sensible |
| ID de connexion à l’API | `payment_ca/authorizenet_directpost/login` |  | Chiffré | | Sensible |
| Marchand MD5 | `payment_ca/authorizenet_directpost/trans_md5` |  | Chiffré | | Sensible |
| Statut de la nouvelle commande | `payment_ca/authorizenet_directpost/order_status` |  | | | Sensible |
| Envoyer un e-mail au client | `payment_ca/authorizenet_directpost/email_customer` |  | | | Sensible |
| Adresse électronique du commerçant | `payment_ca/authorizenet_directpost/merchant_email` |  | | | Sensible |
| Identifiant du commerçant | `payment_ca/cybersource/merchant_id` | Commerce Enterprise uniquement | Chiffré | | Sensible |
| Identifiant du profil | `payment_ca/cybersource/profile_id` | Commerce Enterprise uniquement | Chiffré | | Sensible |
| ID d’installation | `payment_ca/worldpay/installation_id` | Commerce Enterprise uniquement | | | Sensible |
| ID d’installation de l’administrateur distant | `payment_ca/worldpay/admin_installation_id` | Commerce Enterprise uniquement | | | Sensible |
| Secret MD5 pour les transactions | `payment_ca/worldpay/md5_secret` | Commerce Enterprise uniquement | | | Sensible |
| Informations d’identification SFTP | `payment_hk/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | Sensible |
| Informations d’identification SFTP | `payment_hk/paypal_group_all_in_one/payments_pro_hosted_solution_hk/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` |  |  | | Sensible |
| Informations d’identification SFTP | `payment_hk/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | Sensible |
| Rendre un chèque payable à | `payment_hk/checkmo/payable_to` |  | | | Sensible |
| Envoyer la vérification à | `payment_hk/checkmo/mailing_address` |  | | | Sensible |
| ID de connexion à l’API | `payment_hk/authorizenet_directpost/login` |  | Chiffré | | Sensible |
| Marchand MD5 | `payment_hk/authorizenet_directpost/trans_md5` |  | Chiffré | | Sensible |
| Envoyer un e-mail au client | `payment_hk/authorizenet_directpost/email_customer` |  | | | Sensible |
| Adresse électronique du commerçant | `payment_hk/authorizenet_directpost/merchant_email` |  | | | Sensible |
| Identifiant du commerçant | `payment_hk/cybersource/merchant_id` | Commerce Enterprise uniquement | Chiffré | | Sensible |
| Identifiant du profil | `payment_hk/cybersource/profile_id` | Commerce Enterprise uniquement | Chiffré | | Sensible |
| ID d’installation | `payment_hk/worldpay/installation_id` | Commerce Enterprise uniquement | | | Sensible |
| ID d’installation de l’administrateur distant | `payment_hk/worldpay/admin_installation_id` | Commerce Enterprise uniquement | | | Sensible |
| Secret MD5 pour les transactions | `payment_hk/worldpay/md5_secret` | Commerce Enterprise uniquement | | | Sensible |
| Champs de signature | `payment_hk/worldpay/signature_fields` | Commerce Enterprise uniquement | | | Sensible |
| Informations d’identification SFTP | `payment_jp/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | Sensible |
| Informations d’identification SFTP | `payment_jp/paypal_group_all_in_one/payments_pro_hosted_solution_jp/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` |  | | | Sensible |
| Informations d’identification SFTP | `payment_jp/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | Sensible |
| Rendre un chèque payable à | `payment_jp/checkmo/payable_to` |  | | | Sensible |
| Envoyer la vérification à | `payment_jp/checkmo/mailing_address` |  | | | Sensible |
| ID de connexion à l’API | `payment_jp/authorizenet_directpost/login` |  | Chiffré | | Sensible |
| Marchand MD5 | `payment_jp/authorizenet_directpost/trans_md5` |  | Chiffré | | Sensible |
| Envoyer un e-mail au client | `payment_jp/authorizenet_directpost/email_customer` |  | | | Sensible |
| Adresse électronique du commerçant | `payment_jp/authorizenet_directpost/merchant_email` |  | | | Sensible |
| Identifiant du commerçant | `payment_jp/cybersource/merchant_id` | Commerce Enterprise uniquement | Chiffré | | Sensible |
| Identifiant du profil | `payment_jp/cybersource/profile_id` | Commerce Enterprise uniquement | Chiffré | | Sensible |
| ID d’installation | `payment_jp/worldpay/installation_id` | Commerce Enterprise uniquement | | | |
| ID d’installation de l’administrateur distant | `payment_jp/worldpay/admin_installation_id` | Commerce Enterprise uniquement | | | Sensible |
| Secret MD5 pour les transactions | `payment_jp/worldpay/md5_secret` | Commerce Enterprise uniquement | | | Sensible |
| Champs de signature | `payment_jp/worldpay/signature_fields` | Commerce Enterprise uniquement | | | Sensible |
| Informations d’identification SFTP | `payment_fr/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | Sensible |
| Informations d’identification SFTP | `payment_fr/paypal_group_all_in_one/payments_pro_hosted_solution_fr/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` |  | | | Sensible |
| Informations d’identification SFTP | `payment_fr/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | Sensible |
| Rendre un chèque payable à | `payment_fr/checkmo/payable_to` |  | | | Sensible |
| Envoyer la vérification à | `payment_fr/checkmo/mailing_address` |  | | | Sensible |
| ID de connexion à l’API | `payment_fr/authorizenet_directpost/login` |  | Chiffré | | Sensible |
| Marchand MD5 | `payment_fr/authorizenet_directpost/trans_md5` |  | Chiffré | | Sensible |
| Envoyer un e-mail au client | `payment_fr/authorizenet_directpost/email_customer` |  | | | Sensible |
| Adresse électronique du commerçant | `payment_fr/authorizenet_directpost/merchant_email` |  | | | Sensible |
| Identifiant du commerçant | `payment_fr/cybersource/merchant_id` | Commerce Enterprise uniquement | Chiffré | | Sensible |
| Identifiant du profil | `payment_fr/cybersource/profile_id` | Commerce Enterprise uniquement | Chiffré | | Sensible |
| ID d’installation | `payment_fr/worldpay/installation_id` | Commerce Enterprise uniquement | | | Sensible |
| ID d’installation de l’administrateur distant | `payment_fr/worldpay/admin_installation_id` | Commerce Enterprise uniquement | | | Sensible |
| Secret MD5 pour les transactions | `payment_fr/worldpay/md5_secret` | Commerce Enterprise uniquement | | | Sensible |
| Champs de signature | `payment_fr/worldpay/signature_fields` | Commerce Enterprise uniquement | | | Sensible |
| Informations d’identification SFTP | `payment_it/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | Sensible |
| Informations d’identification SFTP | `payment_it/paypal_group_all_in_one/payments_pro_hosted_solution_it/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` |  | | | Sensible |
| Informations d’identification SFTP | `payment_it/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | Sensible |
| Rendre un chèque payable à | `payment_it/checkmo/payable_to` |  | | | Sensible |
| Envoyer la vérification à | `payment_it/checkmo/mailing_address` |  | | | Sensible |
| ID de connexion à l’API | `payment_it/authorizenet_directpost/login` |  | Chiffré | | Sensible |
| Marchand MD5 | `payment_it/authorizenet_directpost/trans_md5` |  | Chiffré | | Sensible |
| Envoyer un e-mail au client | `payment_it/authorizenet_directpost/email_customer` |  | | | Sensible |
| Adresse électronique du commerçant | `payment_it/authorizenet_directpost/merchant_email` |  | | | Sensible |
| Identifiant du commerçant | `payment_it/cybersource/merchant_id` | Commerce Enterprise uniquement | Chiffré | | Sensible |
| Identifiant du profil | `payment_it/cybersource/profile_id` | Commerce Enterprise uniquement | Chiffré | | Sensible |
| ID d’installation | `payment_it/worldpay/installation_id` | Commerce Enterprise uniquement | | | Sensible |
| ID d’installation de l’administrateur distant | `payment_it/worldpay/admin_installation_id` | Commerce Enterprise uniquement | | | Sensible |
| Secret MD5 pour les transactions | `payment_it/worldpay/md5_secret` | Commerce Enterprise uniquement | | | Sensible |

{style="table-layout:auto"}
