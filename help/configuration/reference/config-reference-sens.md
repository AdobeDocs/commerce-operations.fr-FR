---
title: Chemins sensibles et spécifiques au système
description: Consultez la liste des valeurs de configuration sensibles et spécifiques au système.
feature: Configuration, System
exl-id: 127880ab-7507-4e53-8b51-dfa6557d0b18
source-git-commit: e5a1c5634124831c8d5a95df6818ec30c372e8dd
workflow-type: tm+mt
source-wordcount: '3676'
ht-degree: 0%

---

# Paramètres sensibles et spécifiques au système

Cette rubrique répertorie les chemins de configuration pour les paramètres spécifiques au système et sensibles :

- La commande [`magento app:config:dump`](../cli/export-configuration.md) écrit des paramètres spécifiques au système dans le fichier de configuration spécifique au système, `app/etc/env.php`, qui doit _ne pas_ être dans le contrôle source. Il écrit également la configuration partagée de toutes les instances Commerce sur `app/etc/config.php`, ce fichier _devrait_ être dans le contrôle source.
- La commande [`magento config:sensitive:set` ](../cli/set-configuration-values.md) écrit des paramètres sensibles sur `app/etc/env.php`.

  Vous pouvez également définir des valeurs sensibles à l’aide de variables de configuration, comme décrit dans la section [Utiliser des variables d’environnement pour remplacer les paramètres de configuration](../reference/override-config-settings.md#environment-variables).

Pour obtenir la liste des autres chemins de configuration, voir :

- [Tous les chemins de configuration sauf les paiements](../reference/config-reference-general.md)
- [Chemins de configuration des paiements](../reference/config-reference-payment.md).

>[!INFO]
>
>Tous les chemins de configuration répertoriés dans cette rubrique sont sensibles. La colonne `System-specific?` indique les valeurs qui sont également spécifiques au système.

## Chemins généraux sensibles aux catégories et spécifiques au système

Cette section répertorie les noms de variable et les chemins de configuration disponibles pour les options dans l’administrateur sous **Magasins** > Paramètres > **Configuration** > **Général**.

### Chemins Web sensibles et chemins spécifiques au système

Ces valeurs de configuration sont disponibles dans l’Admin de **Magasins** > Paramètres > **Configuration** > **Général** > **Web**.

| Nom | Chemin de configuration | Commerce uniquement ? | Chiffré ? | Spécifique au système ? | Sensibles ? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| URL de base | `web/unsecure/base_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Spécifique au système](/help/assets/configuration/cloud-env.png) |
| URL du lien de base | `web/unsecure/base_link_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Spécifique au système](/help/assets/configuration/cloud-env.png) |
| URL de base des fichiers d’affichage statique | `web/unsecure/base_static_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Spécifique au système](/help/assets/configuration/cloud-env.png) |
| URL de base des fichiers multimédias utilisateur | `web/unsecure/base_media_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Spécifique au système](/help/assets/configuration/cloud-env.png) |
| URL de base sécurisée | `web/secure/base_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Spécifique au système](/help/assets/configuration/cloud-env.png) |
| URL du lien de base sécurisé | `web/secure/base_link_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Spécifique au système](/help/assets/configuration/cloud-env.png) |
| URL de base sécurisée pour les fichiers d’affichage statique | `web/secure/base_static_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Spécifique au système](/help/assets/configuration/cloud-env.png) |
| URL de base sécurisée des fichiers multimédias utilisateur | `web/secure/base_media_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Spécifique au système](/help/assets/configuration/cloud-env.png) |
| URL web par défaut | `web/default/front` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Spécifique au système](/help/assets/configuration/cloud-env.png) |
| URL sans itinéraire par défaut | `web/default/no_route` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Spécifique au système](/help/assets/configuration/cloud-env.png) |
| Chemin du cookie | `web/cookie/cookie_path` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Spécifique au système](/help/assets/configuration/cloud-env.png) |
| Domaine du cookie | `web/cookie/cookie_domain` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Spécifique au système](/help/assets/configuration/cloud-env.png) |
| Durée de vie du cookie | `web/cookie/cookie_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Spécifique au système](/help/assets/configuration/cloud-env.png) |
| Utiliser HTTP uniquement | `web/cookie/cookie_httponly` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Spécifique au système](/help/assets/configuration/cloud-env.png) |
| Mode de restriction des cookies | `web/cookie/cookie_restriction` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Spécifique au système](/help/assets/configuration/cloud-env.png) |

{style="table-layout:auto"}

### Chemins sensibles à la configuration des devises et spécifiques au système

Ces valeurs de configuration sont disponibles dans l’Admin de **Magasins** > Paramètres > **Configuration** > **Général** > **Configuration de devise**.

| Nom | Chemin de configuration | Commerce uniquement ? | Chiffré ? | Spécifique au système ? | Sensibles ? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Error Email Recipient | `currency/import/error_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### Stocker les chemins sensibles aux adresses électroniques et spécifiques au système

Ces valeurs de configuration sont disponibles dans l’Admin de **Magasins** > Paramètres > **Configuration d’email** > **Général** > **Stocker les adresses électroniques**.

| Nom | Chemin de configuration | Commerce uniquement ? | Chiffré ? | Spécifique au système ? | Sensibles ? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Nom de l’expéditeur | `trans_email/ident_general/name` | | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Email expéditeur | `trans_email/ident_general/email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Nom de l’expéditeur | `trans_email/ident_sales/name` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Email expéditeur | `trans_email/ident_sales/email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Nom de l’expéditeur | `trans_email/ident_support/name` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Email expéditeur | `trans_email/ident_support/email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Nom de l’expéditeur | `trans_email/ident_custom1/name` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Email expéditeur | `trans_email/ident_custom1/email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Nom de l’expéditeur | `trans_email/ident_custom2/name` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Email expéditeur | `trans_email/ident_custom2/email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### Contacts chemins sensibles et spécifiques au système

Ces valeurs de configuration sont disponibles dans l’Admin de **Magasins** > Paramètres > **Configuration** > **Général** > **Contacts**.

| Nom | Chemin de configuration | Commerce uniquement ? | Chiffré ? | Spécifique au système ? | Sensibles ? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Envoyer des emails à | `contact/email/recipient_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Expéditeur des emails | `contact/email/sender_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Modèle de courrier électronique | `contact/email/email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### New Relic : création de rapports sur les chemins sensibles et spécifiques au système

Ces valeurs de configuration sont disponibles dans l’Admin de **Magasins** > Paramètres > **Configuration** > **Général** > **Rapports New Relic**.

| Nom | Chemin de configuration | Commerce uniquement ? | Chiffré ? | Spécifique au système ? | Sensibles ? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Identifiant de compte New Relic | `newrelicreporting/general/account_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| New Relic Application ID | `newrelicreporting/general/app_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Clé API New Relic | `newrelicreporting/general/api` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Encrypted](/help/assets/configuration/cloud-enc.png) | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Clé API Insights | `newrelicreporting/general/insights_insert_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Encrypted](/help/assets/configuration/cloud-enc.png) | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| URL de l’API New Relic | `newrelicreporting/general/api_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| URL de l’API Insights | `newrelicreporting/general/insights_api_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

## Chemins sensibles à la catégorie et spécifiques au système des clients

Cette section répertorie les noms de variable et les chemins de configuration disponibles pour les options dans l’administrateur sous **Magasins** > Paramètres > **Configuration** > **Clients**.

### Chemins sensibles à la configuration client et spécifiques au système

Ces valeurs de configuration sont disponibles dans l’Admin de **Magasins** > Paramètres > **Configuration** > **Clients** > **Configuration client**.

| Nom | Chemin de configuration | Commerce uniquement ? | Chiffré ? | Spécifique au système ? | Sensibles ? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Domaine de messagerie par défaut | `customer/create_account/email_domain` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Spécifique au système](/help/assets/configuration/cloud-env.png) |

{style="table-layout:auto"}

## Catégorie de catalogue

Cette section répertorie les noms de variable et les chemins de configuration disponibles pour les options de l’administrateur sous **Magasins** > Paramètres > **Configuration** > **Catalogue**.

### Chemins sensibles au catalogue et spécifiques au système

Ces valeurs de configuration sont disponibles dans l’Admin de **Magasins** > Paramètres > **Configuration** > **Catalogue** > **Catalogue**.

| Nom | Chemin de configuration | Commerce uniquement ? | Chiffré ? | Spécifique au système ? | Sensibles ? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Error Email Recipient | `catalog/productalert_cron/error_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Clé API YouTube | `catalog/product_video/youtube_api_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Nom d’hôte du serveur Solr | `catalog/search/solr_server_hostname` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Port du serveur Solr | `catalog/search/solr_server_port` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Nom d’utilisateur du serveur Solr | `catalog/search/solr_server_username` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Mot de passe du serveur Solr | `catalog/search/solr_server_password` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Chemin du serveur Solr | `catalog/search/solr_server_path` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Nom d’hôte du serveur Elasticsearch | `catalog/search/elasticsearch_server_hostname` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Port du serveur Elasticsearch | `catalog/search/elasticsearch_server_port` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Préfixe d’index Elasticsearch | `catalog/search/elasticsearch_index_prefix` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Activation de l’authentification HTTP Elasticsearch | `catalog/search/elasticsearch_enable_auth` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Spécifique au système](/help/assets/configuration/cloud-env.png) |
| Nom d’utilisateur HTTP Elasticsearch | `catalog/search/elasticsearch_username` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Spécifique au système](/help/assets/configuration/cloud-env.png) |
| Mot de passe HTTP Elasticsearch | `catalog/search/elasticsearch_password` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Spécifique au système](/help/assets/configuration/cloud-env.png) |
| Délai d’expiration du serveur Elasticsearch | `catalog/search/elasticsearch_server_timeout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Spécifique au système](/help/assets/configuration/cloud-env.png) |
| Nom d’utilisateur HTTP Elasticsearch | `catalog/search/elasticsearch_username` | <!-- ![Not EE-only](/help/assets/configuration/red-x.png) --> | | ![Spécifique au système](/help/assets/configuration/cloud-env.png) |
| Mot de passe HTTP Elasticsearch | `catalog/search/elasticsearch_password` | <!-- ![Not EE-only](/help/assets/configuration/red-x.png) --> | | ![Spécifique au système](/help/assets/configuration/cloud-env.png) |
| Délai d’expiration du serveur Elasticsearch | `catalog/search/elasticsearch_server_timeout` | <!-- ![Not EE-only](/help/assets/configuration/red-x.png) --> | | ![Spécifique au système](/help/assets/configuration/cloud-env.png) |
| Nom d’hôte du serveur OpenSearch | `catalog/search/opensearch_server_hostname` | <!-- ![Not EE-only](/help/assets/configuration/red-x.png) --> | | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Port du serveur OpenSearch | `catalog/search/opensearch_server_port` | <!-- ![Not EE-only](/help/assets/configuration/red-x.png) --> | | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Préfixe d’index OpenSearch | `catalog/search/opensearch_index_prefix` | <!-- ![Not EE-only](/help/assets/configuration/red-x.png) --> | | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Activation de l’authentification HTTP OpenSearch | `catalog/search/opensearch_enable_auth` | <!-- ![Not EE-only](/help/assets/configuration/red-x.png) --> | | ![Spécifique au système](/help/assets/configuration/cloud-env.png) |
| Nom d’utilisateur HTTP OpenSearch | `catalog/search/opensearch_username` | <!-- ![Not EE-only](/help/assets/configuration/red-x.png) --> | | ![Spécifique au système](/help/assets/configuration/cloud-env.png) |
| Mot de passe HTTP OpenSearch | `catalog/search/opensearch_password` | <!-- ![Not EE-only](/help/assets/configuration/red-x.png) --> | | ![Spécifique au système](/help/assets/configuration/cloud-env.png) |
| Délai d’expiration du serveur OpenSearch | `catalog/search/opensearch_server_timeout` | <!-- ![Not EE-only](/help/assets/configuration/red-x.png) --> | | ![Spécifique au système](/help/assets/configuration/cloud-env.png) |

{style="table-layout:auto"}

>[!NOTE]
>
>Les paramètres OpenSearch ont été introduits dans Adobe Commerce 2.4.6.

### Chemins sensibles au stock et spécifiques au système

Ces valeurs de configuration sont disponibles dans l’administrateur de **Magasins** > Paramètres > **Configuration** > **Catalogue** > **Inventaire**.

| Nom | Chemin de configuration | Commerce uniquement ? | Chiffré ? | Spécifique au système ? | Sensibles ? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Clé API Google | `cataloginventory/source_selection_distance_based_google/api_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Encrypted](/help/assets/configuration/cloud-enc.png) | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### Chemins sensibles au plan de site XML et spécifiques au système

Ces valeurs de configuration sont disponibles dans l’Admin de **Magasins** > Paramètres > **Configuration** > **Catalogue** > **plan de site XML**.

| Nom | Chemin de configuration | Commerce uniquement ? | Chiffré ? | Spécifique au système ? | Sensibles ? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Error Email Recipient | `sitemap/generate/error_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

## Catégorie de ventes

Cette section répertorie les noms de variable et les chemins de configuration disponibles pour les options dans l’administrateur sous **Magasins** > Paramètres > **Configuration** > **Ventes**.

### Chemins d’accès sensibles et spécifiques au système des paramètres d’expédition

Ces valeurs de configuration sont disponibles dans l’administrateur de **Magasins** > Paramètres > **Configuration** > **Ventes** > **Paramètres d’expédition**.

| Nom | Chemin de configuration | Commerce uniquement ? | Chiffré ? | Spécifique au système ? | Sensibles ? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Pays | `shipping/origin/country_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Région/état | `shipping/origin/region_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Code postal | `shipping/origin/postcode` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Ville | `shipping/origin/city` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Adresse postale | `shipping/origin/street_line1` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Ligne d’adresse 2 de la rue | `shipping/origin/street_line2` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Compte en direct | `carriers/ups/is_account_live` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Spécifique au système](/help/assets/configuration/cloud-env.png) |

{style="table-layout:auto"}

### Chemins sensibles et spécifiques au système des emails de vente

Ces valeurs de configuration sont disponibles dans l’Admin de **Magasins** > Paramètres > **Configuration** > **Ventes** > **Courriers électroniques de vente**.

| Nom | Chemin de configuration | Commerce uniquement ? | Chiffré ? | Spécifique au système ? | Sensibles ? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Envoyer la copie de courrier électronique de commande à | `sales_email/order/copy_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Envoyer la copie de courrier électronique du commentaire de commande à | `sales_email/order_comment/copy_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Envoyer la copie du courrier électronique de facturation à | `sales_email/invoice/copy_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Envoyer la copie du message de commentaire de facture à | `sales_email/invoice_comment/copy_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Envoyer la copie du courrier électronique d’envoi à | `sales_email/shipment/copy_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Envoyer une copie du message de commentaire d’envoi à | `sales_email/shipment_comment/copy_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Envoyer la copie de l’e-mail de la note de crédit à | `sales_email/creditmemo/copy_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Envoyer une copie par courrier électronique de commentaire de crédit à | `sales_email/creditmemo_comment/copy_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Envoyer une copie de l’email prêt à recevoir à | `sales_email/temando_pickup/copy_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### Extraction de chemins sensibles et spécifiques au système

Ces valeurs de configuration sont disponibles dans l’Admin de **Magasins** > Paramètres > **Configuration** > **Ventes** > **Passage en caisse**.

| Nom | Chemin de configuration | Commerce uniquement ? | Chiffré ? | Spécifique au système ? | Sensibles ? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Envoyer la copie de l’email en échec du paiement à | `checkout/payment_failed/copy_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### Chemins sensibles à l’API Google et spécifiques au système

Ces valeurs de configuration sont disponibles dans l’Admin de **Magasins** > Paramètres > **Configuration** > **Ventes** > **API Google**.

| Nom | Chemin de configuration | Commerce uniquement ? | Chiffré ? | Spécifique au système ? | Sensibles ? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| ID de conteneur | `google/analytics/container_id` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### Chemins sensibles aux méthodes de diffusion et spécifiques au système

Ces valeurs de configuration sont disponibles dans l’Admin de **Magasins** > Paramètres > **Configuration** > **Ventes** > **Méthodes de diffusion**.

| Nom | Chemin de configuration | Commerce uniquement ? | Chiffré ? | Spécifique au système ? | Sensibles ? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| URL de passerelle | `carriers/usps/gateway_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| URL de passerelle sécurisée | `carriers/usps/gateway_secure_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Titre | `carriers/usps/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Identifiant utilisateur | `carriers/usps/userid` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Encrypted](/help/assets/configuration/cloud-enc.png) | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Mot de passe | `carriers/usps/password` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Encrypted](/help/assets/configuration/cloud-enc.png) | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Identifiant utilisateur | `carriers/ups/username` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Encrypted](/help/assets/configuration/cloud-enc.png) | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Mot de passe | `carriers/ups/password` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Encrypted](/help/assets/configuration/cloud-enc.png) | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Numéro de licence d’accès | `carriers/ups/access_license_number` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Encrypted](/help/assets/configuration/cloud-enc.png) | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Tracking de l’URL XML | `carriers/ups/tracking_xml_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| URL XML de passerelle | `carriers/ups/gateway_xml_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Numéro d’expéditeur | `carriers/ups/shipper_number` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Déboguer | `carriers/ups/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Identifiant de compte | `carriers/fedex/account` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Encrypted](/help/assets/configuration/cloud-enc.png) | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Clé | `carriers/fedex/key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Encrypted](/help/assets/configuration/cloud-enc.png) | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Nombre de mètres | `carriers/fedex/meter_number` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Encrypted](/help/assets/configuration/cloud-enc.png) | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Mot de passe | `carriers/fedex/password` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Encrypted](/help/assets/configuration/cloud-enc.png) | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Identifiant d’accès | `carriers/dhl/id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Encrypted](/help/assets/configuration/cloud-enc.png) | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Mot de passe | `carriers/dhl/password` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Encrypted](/help/assets/configuration/cloud-enc.png) | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Déboguer | `carriers/dhl/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | |
| Numéro de compte | `carriers/dhl/account` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| URL de passerelle | `carriers/dhl/gateway_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Mode sandbox | `carriers/fedex/sandbox_mode` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### Chemins sensibles aux ventes et spécifiques au système

Ces valeurs de configuration sont disponibles dans l’Admin de **Magasins** > Paramètres > **Configuration** > **Ventes** > **Ventes**.

| Nom | Chemin de configuration | Commerce uniquement ? | Chiffré ? | Spécifique au système ? | Sensibles ? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Nom du contact | `sales/magento_rma/store_name` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Adresse postale | `sales/magento_rma/address` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Adresse postale | `sales/magento_rma/address1` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Ville | `sales/magento_rma/city` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Etat/Province | `sales/magento_rma/region_id` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Code postal | `sales/magento_rma/zip` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Pays | `sales/magento_rma/country_id` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Envoyer une copie de courrier électronique RMA à | `sales_email/magento_rma/copy_to` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Envoyer la copie d’e-mail d’autorisation RMA à | `sales_email/magento_rma_auth/copy_to` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Envoyer une copie par e-mail de commentaire RMA à | `sales_email/magento_rma_comment/copy_to` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Envoyer une copie par e-mail de commentaire RMA à | `sales_email/magento_rma_customer_comment/copy_to` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### Chemins de l’API Google

Ces valeurs de configuration sont disponibles dans l’Admin de **Magasins** > Paramètres > **Configuration** > **Ventes** > **API Google**.

| Nom | Chemin de configuration | Commerce uniquement ? | Chiffré ? | Spécifique au système ? | Sensibles ? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Numéro de compte | `google/analytics/account` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

## Catégorie avancée

Cette section répertorie les noms de variable et les chemins de configuration disponibles pour les options dans l’administrateur sous **Magasins** > Paramètres > **Configuration** > **Avancé**.

### Chemins sensibles à l’administration et spécifiques au système

Ces valeurs de configuration sont disponibles dans l’Admin de **Magasins** > Paramètres > **Configuration** > **Avancé** > **Admin**.

| Nom | Chemin de configuration | Commerce uniquement ? | Chiffré ? | Spécifique au système ? | Sensibles ? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| URL d’administration personnalisée | `admin/url/custom` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Chemin d’accès d’administration personnalisé | `admin/url/custom_path` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### Chemins sensibles au système et spécifiques au système

Ces valeurs de configuration sont disponibles dans l’Admin de **Magasins** > Paramètres > **Configuration** > **Avancé** > **Système**.

| Nom | Chemin de configuration | Commerce uniquement ? | Chiffré ? | Spécifique au système ? | Sensibles ? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Error Email Recipient | `system/magento_scheduled_import_export_log/error_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Liste d’accès | `system/full_page_cache/varnish/access_list` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Error Email Sender | `system/magento_scheduled_import_export_log/error_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### Chemins sensibles pour les développeurs et spécifiques au système

Ces valeurs de configuration sont disponibles dans l’Admin de **Magasins** > Paramètres > **Configuration** > **Avancé** > **Développeur**.

| Nom | Chemin de configuration | Commerce uniquement ? | Chiffré ? | Spécifique au système ? | Sensibles ? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| IP autorisées (séparées par des virgules) | `dev/restrict/allow_ips` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

## Catégorie avancée

Cette section répertorie les noms de variable et les chemins de configuration disponibles pour les options dans l’administrateur sous **Magasins** > Paramètres > **Configuration** > **Avancé**.

### Chemins système

Ces valeurs de configuration sont disponibles dans l’Admin de **Magasins** > Paramètres > **Configuration** > **Avancé** > **Système**.

| Nom | Chemin de configuration | Commerce uniquement ? | Chiffré ? | Spécifique au système ? | Sensibles ? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Hôte | `system/smtp/host` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Port (25) | `system/smtp/port` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Hôte principal | `system/full_page_cache/varnish/backend_host` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Port principal | `system/full_page_cache/varnish/backend_port` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### Chemins de développement

Ces valeurs de configuration sont disponibles dans l’Admin de **Magasins** > Paramètres > **Configuration** > **Avancé** > **Développeur**.

| Nom | Chemin de configuration | Commerce uniquement ? | Chiffré ? | Spécifique au système ? | Sensibles ? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Enregistrer les erreurs JS dans la clé de stockage de session | `dev/js/session_storage_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Spécifique au système](/help/assets/configuration/cloud-env.png) |

{style="table-layout:auto"}

## Chemins sensibles au paiement et spécifiques au système

Cette section répertorie les noms de variable et les chemins de configuration disponibles pour les options de l’administrateur sous **Magasins** > Paramètres > **Configuration** > **Ventes** > **Paiement**.

### Variable générale

| Nom | Chemin de configuration | Commerce uniquement ? | Chiffré ? |
|--------------|--------------|--------------|--------------|
| Pays du commerce | `paypal/general/merchant_country` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

>[!INFO]
>
>Votre choix pour cette variable détermine les [chemins internationaux](#international-paths) que vous pouvez utiliser.

### Chemins sensibles et spécifiques au système PayPal

| Nom | Chemin de configuration | Commerce uniquement ? | Chiffré ? | Spécifique au système ? | Sensibles ? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Courrier électronique associé à un compte marchand PayPal (facultatif) | `paypal/general/business_account` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Identifiant de compte marchand | `payment/paypal_express/merchant_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Publisher ID | `payment/paypal_express_bml/publisher_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Mot de passe | `paypal/fetch_reports/ftp_password` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Encrypted](/help/assets/configuration/cloud-enc.png) | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Connexion | `paypal/fetch_reports/ftp_login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Encrypted](/help/assets/configuration/cloud-enc.png) | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Nom d’hôte ou adresse IP du point de terminaison personnalisé | `paypal/fetch_reports/ftp_ip` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Mode sandbox | `paypal/fetch_reports/ftp_sandbox` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Spécifique au système](/help/assets/configuration/cloud-env.png) |
| Mode de débogage | `payment/paypal_express/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Spécifique au système](/help/assets/configuration/cloud-env.png) |
| Mode de débogage | `payment/paypal_billing_agreement/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Spécifique au système](/help/assets/configuration/cloud-env.png) |
| Informations d’identification SFTP | `payment_all_paypal/express_checkout/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### Chemins sensibles et spécifiques au système PayPal Payflow Pro

| Nom | Chemin de configuration | Commerce uniquement ? | Chiffré ? | Spécifique au système ? | Sensibles ? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Utilisateur | `payment/payflow_advanced/user` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Encrypted](/help/assets/configuration/cloud-enc.png) | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Mot de passe | `payment/payflow_advanced/pwd` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Encrypted](/help/assets/configuration/cloud-enc.png) | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Chemin d’accès personnalisé | `paypal/fetch_reports/ftp_path` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Utilisateur | `payment/payflowpro/user` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Encrypted](/help/assets/configuration/cloud-enc.png) | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Mot de passe | `payment/payflowpro/pwd` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Encrypted](/help/assets/configuration/cloud-enc.png) | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Mode test | `payment/payflowpro/sandbox_flag` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Spécifique au système](/help/assets/configuration/cloud-env.png) |
| Partenaire | `payment/payflowpro/partner` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Hôte du proxy | `payment/payflowpro/proxy_host` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Port du proxy | `payment/payflowpro/proxy_port` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Mode de débogage | `payment/payflowpro/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Spécifique au système](/help/assets/configuration/cloud-env.png) |
| Informations d’identification SFTP | `payment_all_paypal/paypal_payflowpro/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Spécifique au système](/help/assets/configuration/cloud-env.png) |
| Paramètres de carte de crédit | `payment_all_paypal/paypal_payflowpro/settings_paypal_payflow/heading_cc` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### Chemins sensibles et spécifiques au système des liens de flux de production PayPal

| Nom | Chemin de configuration | Commerce uniquement ? | Chiffré ? | Spécifique au système ? | Sensibles ? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Utilisateur | `payment/payflow_link/user` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Encrypted](/help/assets/configuration/cloud-enc.png) | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Mot de passe | `payment/payflow_link/pwd` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Encrypted](/help/assets/configuration/cloud-enc.png) | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Mode test | `payment/payflow_link/sandbox_flag` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Spécifique au système](/help/assets/configuration/cloud-env.png) |
| Utiliser le proxy | `payment/payflow_link/use_proxy` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Spécifique au système](/help/assets/configuration/cloud-env.png) |
| Hôte du proxy | `payment/payflow_link/proxy_host` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Spécifique au système](/help/assets/configuration/cloud-env.png) |
| Port du proxy | `payment/payflow_link/proxy_port` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Spécifique au système](/help/assets/configuration/cloud-env.png) |
| Mode de débogage | `payment/payflow_link/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Spécifique au système](/help/assets/configuration/cloud-env.png) |
| Méthode d’URL pour annuler l’URL et renvoyer l’URL | `payment/payflow_link/url_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Spécifique au système](/help/assets/configuration/cloud-env.png) |
| Mode de débogage | `payment/payflow_express/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Spécifique au système](/help/assets/configuration/cloud-env.png) |
| Informations d’identification SFTP | `payment_all_paypal/payflow_link/settings_payflow_link/settings_payflow_link_advanced/payflow_link_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### Chemins sensibles et spécifiques au système de paiement PayPal Pro

| Nom | Chemin de configuration | Commerce uniquement ? | Chiffré ? | Spécifique au système ? | Sensibles ? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Nom d’utilisateur API | `paypal/wpp/api_username` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Encrypted](/help/assets/configuration/cloud-enc.png) | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Mot de passe de l’API | `paypal/wpp/api_password` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Encrypted](/help/assets/configuration/cloud-enc.png) | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Signature API | `paypal/wpp/api_signature` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Encrypted](/help/assets/configuration/cloud-enc.png) | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Certificat d’API | `paypal/wpp/api_cert` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Hôte du proxy | `paypal/wpp/proxy_host` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Port du proxy | `paypal/wpp/proxy_port` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Mode sandbox | `paypal/wpp/sandbox_flag` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Spécifique au système](/help/assets/configuration/cloud-env.png) |
| Informations d’identification SFTP | `payment_all_paypal/payments_pro_hosted_solution_without_bml/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### PayPal payment Pro Chemins sensibles et spécifiques au système hébergés

| Nom | Chemin de configuration | Commerce uniquement ? | Chiffré ? | Spécifique au système ? | Sensibles ? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Mode de débogage | `payment/hosted_pro/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Spécifique au système](/help/assets/configuration/cloud-env.png) |
| Informations d’identification SFTP | `payment_all_paypal/payments_pro_hosted_solution/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Informations d’identification SFTP | `payment_au/paypal_group_all_in_one/payments_pro_hosted_solution_au/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### Chemins sensibles au Braintree et spécifiques au système

| Nom | Chemin de configuration | Commerce uniquement ? | Chiffré ? | Spécifique au système ? | Sensibles ? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Identifiant du marchand | `payment/braintree/merchant_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Clé publique | `payment/braintree/public_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Encrypted](/help/assets/configuration/cloud-enc.png) | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Clé privée | `payment/braintree/private_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Encrypted](/help/assets/configuration/cloud-enc.png) | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Identifiant de compte marchand | `payment/braintree/merchant_account_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Kount Merchant ID | `payment/braintree/kount_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Remplacer le nom du marchand | `payment/braintree_paypal/merchant_name_override` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Téléphone | `payment/braintree/descriptor_phone` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| URL | `payment/braintree/descriptor_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Spécifique au système](/help/assets/configuration/cloud-env.png) |

{style="table-layout:auto"}

### Vérifier / Paires des commandes monétaires

| Nom | Chemin de configuration | Commerce uniquement ? | Chiffré ? | Spécifique au système ? | Sensibles ? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Envoyer la vérification à | `payment/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Envoyer la vérification à | `payment_us/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### Chemins internationaux

| Nom | Chemin de configuration | Commerce uniquement ? | Chiffré ? | Spécifique au système ? | Sensibles ? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Clé de transaction | `payment_au/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Encrypted](/help/assets/configuration/cloud-enc.png) | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Mode test | `payment_au/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Spécifique au système](/help/assets/configuration/cloud-env.png) |
| URL de passerelle | `payment_au/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| URL des détails de transaction | `payment_au/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Clé de transaction | `payment_au/cybersource/transaction_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![Encrypted](/help/assets/configuration/cloud-enc.png) | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Clé d’accès | `payment_au/cybersource/access_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![Encrypted](/help/assets/configuration/cloud-enc.png) | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Clé secrète | `payment_au/cybersource/secret_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![Encrypted](/help/assets/configuration/cloud-enc.png) | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Mode test | `payment_au/cybersource/sandbox_flag` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | | ![Spécifique au système](/help/assets/configuration/cloud-env.png) |
| Mot de passe de réponse de paiement | `payment_au/worldpay/response_password` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Mot de passe d’autorisation d’administrateur distant | `payment_au/worldpay/auth_password` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Mode sandbox | `payment_au/eway/sandbox_flag` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | | ![Spécifique au système](/help/assets/configuration/cloud-env.png) |
| Clé d’API Live | `payment_au/eway/live_api_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![Encrypted](/help/assets/configuration/cloud-enc.png) | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Mot de passe de l’API Live | `payment_au/eway/live_api_password` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![Encrypted](/help/assets/configuration/cloud-enc.png) | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Clé de chiffrement côté client active | `payment_au/eway/live_encryption_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![Encrypted](/help/assets/configuration/cloud-enc.png) | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Clé API Sandbox | `payment_au/eway/sandbox_api_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![Encrypted](/help/assets/configuration/cloud-enc.png) | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Mot de passe de l’API Sandbox | `payment_au/eway/sandbox_api_password` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![Encrypted](/help/assets/configuration/cloud-enc.png) | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Clé de chiffrement côté client Sandbox | `payment_au/eway/sandbox_encryption_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![Encrypted](/help/assets/configuration/cloud-enc.png) | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Clé de transaction | `payment_es/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Encrypted](/help/assets/configuration/cloud-enc.png) | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Mode test | `payment_es/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Spécifique au système](/help/assets/configuration/cloud-env.png) |
| URL de passerelle | `payment_es/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| URL des détails de transaction | `payment_es/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Clé de transaction | `payment_es/cybersource/transaction_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![Encrypted](/help/assets/configuration/cloud-enc.png) | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Clé d’accès | `payment_es/cybersource/access_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![Encrypted](/help/assets/configuration/cloud-enc.png) | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Clé secrète | `payment_es/cybersource/secret_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![Encrypted](/help/assets/configuration/cloud-enc.png) | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Mode test | `payment_es/cybersource/sandbox_flag` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | | ![Spécifique au système](/help/assets/configuration/cloud-env.png) |
| Mot de passe de réponse de paiement | `payment_es/worldpay/response_password` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Mot de passe d’autorisation d’administrateur distant | `payment_es/worldpay/auth_password` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Secret MD5 pour les transactions | `payment_es/worldpay/md5_secret` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Déboguer | `payment_es/worldpay/debug` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | | ![Spécifique au système](/help/assets/configuration/cloud-env.png) |
| Mode sandbox | `payment_es/eway/sandbox_flag` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | | ![Spécifique au système](/help/assets/configuration/cloud-env.png) |
| Clé d’API Live | `payment_es/eway/live_api_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![Encrypted](/help/assets/configuration/cloud-enc.png) | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Mot de passe de l’API Live | `payment_es/eway/live_api_password` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![Encrypted](/help/assets/configuration/cloud-enc.png) | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Clé de chiffrement côté client active | `payment_es/eway/live_encryption_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![Encrypted](/help/assets/configuration/cloud-enc.png) | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Clé API Sandbox | `payment_es/eway/sandbox_api_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![Encrypted](/help/assets/configuration/cloud-enc.png) | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Mot de passe de l’API Sandbox | `payment_es/eway/sandbox_api_password` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![Encrypted](/help/assets/configuration/cloud-enc.png) | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Clé de chiffrement côté client Sandbox | `payment_es/eway/sandbox_encryption_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![Encrypted](/help/assets/configuration/cloud-enc.png) | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Clé de transaction | `payment_nz/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Encrypted](/help/assets/configuration/cloud-enc.png) | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Mode test | `payment_nz/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Spécifique au système](/help/assets/configuration/cloud-env.png) |
| URL de passerelle | `payment_nz/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| URL des détails de transaction | `payment_nz/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Mode test | `payment_nz/cybersource/sandbox_flag` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | | ![Spécifique au système](/help/assets/configuration/cloud-env.png) |
| Mode test | `payment_nz/worldpay/sandbox_flag` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | | ![Spécifique au système](/help/assets/configuration/cloud-env.png) |
| Mode sandbox | `payment_nz/eway/sandbox_flag` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | | ![Spécifique au système](/help/assets/configuration/cloud-env.png) |
| Clé d’API Live | `payment_nz/eway/live_api_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![Encrypted](/help/assets/configuration/cloud-enc.png) | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Mot de passe de l’API Live | `payment_nz/eway/live_api_password` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![Encrypted](/help/assets/configuration/cloud-enc.png) | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Clé de chiffrement côté client active | `payment_nz/eway/live_encryption_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![Encrypted](/help/assets/configuration/cloud-enc.png) | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Clé API Sandbox | `payment_nz/eway/sandbox_api_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![Encrypted](/help/assets/configuration/cloud-enc.png) | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Mot de passe de l’API Sandbox | `payment_nz/eway/sandbox_api_password` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![Encrypted](/help/assets/configuration/cloud-enc.png) | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Clé de chiffrement côté client Sandbox | `payment_nz/eway/sandbox_encryption_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![Encrypted](/help/assets/configuration/cloud-enc.png) | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Mode test | `payment/payflow_advanced/sandbox_flag` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Spécifique au système](/help/assets/configuration/cloud-env.png) |
| Hôte du proxy | `payment/payflow_advanced/proxy_host` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Port du proxy | `payment/payflow_advanced/proxy_port` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Spécifique au système](/help/assets/configuration/cloud-env.png) |
| Mode de débogage | `payment/payflow_advanced/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Spécifique au système](/help/assets/configuration/cloud-env.png) |
| Méthode d’URL pour annuler l’URL et renvoyer l’URL | `payment/payflow_advanced/url_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Spécifique au système](/help/assets/configuration/cloud-env.png) |
| Mode test | `payment_us/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Spécifique au système](/help/assets/configuration/cloud-env.png) |
| URL de passerelle | `payment_us/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| URL des détails de transaction | `payment_us/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Clé d’accès | `payment_us/cybersource/access_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![Encrypted](/help/assets/configuration/cloud-enc.png) | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Clé secrète | `payment_us/cybersource/secret_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![Encrypted](/help/assets/configuration/cloud-enc.png) | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Mode test | `payment_us/cybersource/sandbox_flag` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | | ![Spécifique au système](/help/assets/configuration/cloud-env.png) |
| Mode test | `payment_us/worldpay/sandbox_flag` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | | ![Spécifique au système](/help/assets/configuration/cloud-env.png) |
| Mode sandbox | `payment_us/eway/sandbox_flag` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | | ![Spécifique au système](/help/assets/configuration/cloud-env.png) |
| Clé d’API Live | `payment_us/eway/live_api_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![Encrypted](/help/assets/configuration/cloud-enc.png) | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Mot de passe de l’API Live | `payment_us/eway/live_api_password` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![Encrypted](/help/assets/configuration/cloud-enc.png) | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Clé de chiffrement côté client active | `payment_us/eway/live_encryption_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![Encrypted](/help/assets/configuration/cloud-enc.png) | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Clé API Sandbox | `payment_us/eway/sandbox_api_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![Encrypted](/help/assets/configuration/cloud-enc.png) | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Mot de passe de l’API Sandbox | `payment_us/eway/sandbox_api_password` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![Encrypted](/help/assets/configuration/cloud-enc.png) | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Clé de chiffrement côté client Sandbox | `payment_us/eway/sandbox_encryption_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![Encrypted](/help/assets/configuration/cloud-enc.png) | ![Spécifique au système](/help/assets/configuration/cloud-env.png) |
| Mode test | `payment_gb/cybersource/sandbox_flag` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | | ![Spécifique au système](/help/assets/configuration/cloud-env.png) |
| Mode test | `payment_gb/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Spécifique au système](/help/assets/configuration/cloud-env.png) |
| URL de passerelle | `payment_gb/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| URL des détails de transaction | `payment_gb/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Mode test | `payment_gb/worldpay/sandbox_flag` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | | ![Spécifique au système](/help/assets/configuration/cloud-env.png) |
| Mode sandbox | `payment_gb/eway/sandbox_flag` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | | ![Spécifique au système](/help/assets/configuration/cloud-env.png) |
| Clé d’API Live | `payment_gb/eway/live_api_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![Encrypted](/help/assets/configuration/cloud-enc.png) | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Mot de passe de l’API Live | `payment_gb/eway/live_api_password` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![Encrypted](/help/assets/configuration/cloud-enc.png) | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Clé de chiffrement côté client active | `payment_gb/eway/live_encryption_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![Encrypted](/help/assets/configuration/cloud-enc.png) | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Clé API Sandbox | `payment_gb/eway/sandbox_api_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![Encrypted](/help/assets/configuration/cloud-enc.png) | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Mot de passe de l’API Sandbox | `payment_gb/eway/sandbox_api_password` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![Encrypted](/help/assets/configuration/cloud-enc.png) | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Clé de chiffrement côté client Sandbox | `payment_gb/eway/sandbox_encryption_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![Encrypted](/help/assets/configuration/cloud-enc.png) | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Clé de transaction | `payment_de/cybersource/transaction_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![Encrypted](/help/assets/configuration/cloud-enc.png) | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Clé d’accès | `payment_de/cybersource/access_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![Encrypted](/help/assets/configuration/cloud-enc.png) | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Clé secrète | `payment_de/cybersource/secret_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![Encrypted](/help/assets/configuration/cloud-enc.png) | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Mode test | `payment_de/cybersource/sandbox_flag` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | | ![Spécifique au système](/help/assets/configuration/cloud-env.png) |
| Clé de transaction | `payment_de/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Encrypted](/help/assets/configuration/cloud-enc.png) | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Mode test | `payment_de/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Spécifique au système](/help/assets/configuration/cloud-env.png) |
| URL de passerelle | `payment_de/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| URL des détails de transaction | `payment_de/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Mot de passe de réponse de paiement | `payment_de/worldpay/response_password` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Mot de passe d’autorisation d’administrateur distant | `payment_de/worldpay/auth_password` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Déboguer | `payment_de/worldpay/debug` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | | ![Spécifique au système](/help/assets/configuration/cloud-env.png) |
| Mode sandbox | `payment_de/eway/sandbox_flag` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | | ![Spécifique au système](/help/assets/configuration/cloud-env.png) |
| Clé d’API Live | `payment_de/eway/live_api_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![Encrypted](/help/assets/configuration/cloud-enc.png) | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Mot de passe de l’API Live | `payment_de/eway/live_api_password` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![Encrypted](/help/assets/configuration/cloud-enc.png) | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Clé de chiffrement côté client active | `payment_de/eway/live_encryption_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![Encrypted](/help/assets/configuration/cloud-enc.png) | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Clé API Sandbox | `payment_de/eway/sandbox_api_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![Encrypted](/help/assets/configuration/cloud-enc.png) | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Mot de passe de l’API Sandbox | `payment_de/eway/sandbox_api_password` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![Encrypted](/help/assets/configuration/cloud-enc.png) | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Clé de chiffrement côté client Sandbox | `payment_de/eway/sandbox_encryption_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![Encrypted](/help/assets/configuration/cloud-enc.png) | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Clé de transaction | `payment_other/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Encrypted](/help/assets/configuration/cloud-enc.png) | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Mode test | `payment_other/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| URL de passerelle | `payment_other/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| URL des détails de transaction | `payment_other/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Spécifique au système](/help/assets/configuration/cloud-env.png) |
| Clé de transaction | `payment_other/cybersource/transaction_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![Encrypted](/help/assets/configuration/cloud-enc.png) | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Clé d’accès | `payment_other/cybersource/access_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![Encrypted](/help/assets/configuration/cloud-enc.png) | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Clé secrète | `payment_other/cybersource/secret_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![Encrypted](/help/assets/configuration/cloud-enc.png) | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| New Order Status | `payment_other/cybersource/order_status` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | | ![Spécifique au système](/help/assets/configuration/cloud-env.png) |
| Mode test | `payment_other/cybersource/sandbox_flag` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | | ![Spécifique au système](/help/assets/configuration/cloud-env.png) |
| Mot de passe de réponse de paiement | `payment_other/worldpay/response_password` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Mot de passe d’autorisation d’administrateur distant | `payment_other/worldpay/auth_password` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Mode test | `payment_other/worldpay/sandbox_flag` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | | ![Spécifique au système](/help/assets/configuration/cloud-env.png) |
| Mode sandbox | `payment_other/eway/sandbox_flag` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | | ![Spécifique au système](/help/assets/configuration/cloud-env.png) |
| Clé d’API Live | `payment_other/eway/live_api_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![Encrypted](/help/assets/configuration/cloud-enc.png) | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Mot de passe de l’API Live | `payment_other/eway/live_api_password` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![Encrypted](/help/assets/configuration/cloud-enc.png) | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Clé de chiffrement côté client active | `payment_other/eway/live_encryption_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![Encrypted](/help/assets/configuration/cloud-enc.png) | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Clé API Sandbox | `payment_other/eway/sandbox_api_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![Encrypted](/help/assets/configuration/cloud-enc.png) | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Mot de passe de l’API Sandbox | `payment_other/eway/sandbox_api_password` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![Encrypted](/help/assets/configuration/cloud-enc.png) | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Clé de chiffrement côté client Sandbox | `payment_other/eway/sandbox_encryption_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![Encrypted](/help/assets/configuration/cloud-enc.png) | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Clé de transaction | `payment_ca/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Encrypted](/help/assets/configuration/cloud-enc.png) | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Mode test | `payment_ca/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Spécifique au système](/help/assets/configuration/cloud-env.png) |
| URL de passerelle | `payment_ca/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| URL des détails de transaction | `payment_ca/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Clé de transaction | `payment_ca/cybersource/transaction_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![Encrypted](/help/assets/configuration/cloud-enc.png) | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Clé d’accès | `payment_ca/cybersource/access_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![Encrypted](/help/assets/configuration/cloud-enc.png) | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Clé secrète | `payment_ca/cybersource/secret_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![Encrypted](/help/assets/configuration/cloud-enc.png) | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| New Order Status | `payment_ca/cybersource/order_status` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Mode test | `payment_ca/cybersource/sandbox_flag` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | | ![Spécifique au système](/help/assets/configuration/cloud-env.png) |
| Mot de passe de réponse de paiement | `payment_ca/worldpay/response_password` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | | ![Spécifique au système](/help/assets/configuration/cloud-env.png) |
| Mot de passe d’autorisation d’administrateur distant | `payment_ca/worldpay/auth_password` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Mode test | `payment_ca/worldpay/sandbox_flag` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | | ![Spécifique au système](/help/assets/configuration/cloud-env.png) |
| Mode sandbox | `payment_ca/eway/sandbox_flag` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | | ![Spécifique au système](/help/assets/configuration/cloud-env.png) |
| Clé d’API Live | `payment_ca/eway/live_api_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![Encrypted](/help/assets/configuration/cloud-enc.png) | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Mot de passe de l’API Live | `payment_ca/eway/live_api_password` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![Encrypted](/help/assets/configuration/cloud-enc.png) | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Clé de chiffrement côté client active | `payment_ca/eway/live_encryption_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![Encrypted](/help/assets/configuration/cloud-enc.png) | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Clé API Sandbox | `payment_ca/eway/sandbox_api_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![Encrypted](/help/assets/configuration/cloud-enc.png) | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Mot de passe de l’API Sandbox | `payment_ca/eway/sandbox_api_password` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![Encrypted](/help/assets/configuration/cloud-enc.png) | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Clé de chiffrement côté client Sandbox | `payment_ca/eway/sandbox_encryption_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![Encrypted](/help/assets/configuration/cloud-enc.png) | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Clé de transaction | `payment_hk/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Encrypted](/help/assets/configuration/cloud-enc.png) | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Mode test | `payment_hk/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Spécifique au système](/help/assets/configuration/cloud-env.png) |
| URL de passerelle | `payment_hk/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| URL des détails de transaction | `payment_hk/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Clé de transaction | `payment_hk/cybersource/transaction_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![Encrypted](/help/assets/configuration/cloud-enc.png) | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Clé d’accès | `payment_hk/cybersource/access_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![Encrypted](/help/assets/configuration/cloud-enc.png) | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Clé secrète | `payment_hk/cybersource/secret_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![Encrypted](/help/assets/configuration/cloud-enc.png) | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Mode test | `payment_hk/cybersource/sandbox_flag` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Mot de passe de réponse de paiement | `payment_hk/worldpay/response_password` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Mot de passe d’autorisation d’administrateur distant | `payment_hk/worldpay/auth_password` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Mode test | `payment_hk/worldpay/sandbox_flag` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Clé d’API Live | `payment_hk/eway/live_api_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![Encrypted](/help/assets/configuration/cloud-enc.png) | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Mot de passe de l’API Live | `payment_hk/eway/live_api_password` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![Encrypted](/help/assets/configuration/cloud-enc.png) | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Clé de chiffrement côté client active | `payment_hk/eway/live_encryption_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![Encrypted](/help/assets/configuration/cloud-enc.png) | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Clé API Sandbox | `payment_hk/eway/sandbox_api_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![Encrypted](/help/assets/configuration/cloud-enc.png) | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Mot de passe de l’API Sandbox | `payment_hk/eway/sandbox_api_password` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![Encrypted](/help/assets/configuration/cloud-enc.png) | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Clé de chiffrement côté client Sandbox | `payment_hk/eway/sandbox_encryption_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![Encrypted](/help/assets/configuration/cloud-enc.png) | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Clé de transaction | `payment_jp/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Encrypted](/help/assets/configuration/cloud-enc.png) | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Mode test | `payment_jp/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Spécifique au système](/help/assets/configuration/cloud-env.png) |
| URL de passerelle | `payment_jp/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| URL des détails de transaction | `payment_jp/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Clé de transaction | `payment_jp/cybersource/transaction_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![Encrypted](/help/assets/configuration/cloud-enc.png) | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Clé d’accès | `payment_jp/cybersource/access_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![Encrypted](/help/assets/configuration/cloud-enc.png) | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Clé secrète | `payment_jp/cybersource/secret_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![Encrypted](/help/assets/configuration/cloud-enc.png) | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| New Order Status | `payment_jp/cybersource/order_status` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | | ![Spécifique au système](/help/assets/configuration/cloud-env.png) |
| Mode test | `payment_jp/cybersource/sandbox_flag` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | | ![Spécifique au système](/help/assets/configuration/cloud-env.png) |
| Mot de passe de réponse de paiement | `payment_jp/worldpay/response_password` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Mot de passe d’autorisation d’administrateur distant | `payment_jp/worldpay/auth_password` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Mode test | `payment_jp/worldpay/sandbox_flag` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | | ![Spécifique au système](/help/assets/configuration/cloud-env.png) |
| Mode sandbox | `payment_jp/eway/sandbox_flag` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | | ![Spécifique au système](/help/assets/configuration/cloud-env.png) |
| Clé d’API Live | `payment_jp/eway/live_api_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![Encrypted](/help/assets/configuration/cloud-enc.png) | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Mot de passe de l’API Live | `payment_jp/eway/live_api_password` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![Encrypted](/help/assets/configuration/cloud-enc.png) | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Clé de chiffrement côté client active | `payment_jp/eway/live_encryption_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![Encrypted](/help/assets/configuration/cloud-enc.png) | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Clé API Sandbox | `payment_jp/eway/sandbox_api_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![Encrypted](/help/assets/configuration/cloud-enc.png) | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Mot de passe de l’API Sandbox | `payment_jp/eway/sandbox_api_password` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![Encrypted](/help/assets/configuration/cloud-enc.png) | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Clé de chiffrement côté client Sandbox | `payment_jp/eway/sandbox_encryption_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![Encrypted](/help/assets/configuration/cloud-enc.png) | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Clé de transaction | `payment_fr/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Encrypted](/help/assets/configuration/cloud-enc.png) | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Mode test | `payment_fr/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Spécifique au système](/help/assets/configuration/cloud-env.png) |
| URL de passerelle | `payment_fr/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| URL des détails de transaction | `payment_fr/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Clé de transaction | `payment_fr/cybersource/transaction_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![Encrypted](/help/assets/configuration/cloud-enc.png) | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Clé d’accès | `payment_fr/cybersource/access_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![Encrypted](/help/assets/configuration/cloud-enc.png) | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Clé secrète | `payment_fr/cybersource/secret_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![Encrypted](/help/assets/configuration/cloud-enc.png) | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Mode test | `payment_fr/cybersource/sandbox_flag` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | | ![Spécifique au système](/help/assets/configuration/cloud-env.png) |
| Mot de passe de réponse de paiement | `payment_fr/worldpay/response_password` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Mot de passe d’autorisation d’administrateur distant | `payment_fr/worldpay/auth_password` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Mode test | `payment_fr/worldpay/sandbox_flag` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |  | ![Spécifique au système](/help/assets/configuration/cloud-env.png) |
| Mode sandbox | `payment_fr/eway/sandbox_flag` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | | ![Spécifique au système](/help/assets/configuration/cloud-env.png) |
| Clé d’API Live | `payment_fr/eway/live_api_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![Encrypted](/help/assets/configuration/cloud-enc.png) | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Mot de passe de l’API Live | `payment_fr/eway/live_api_password` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![Encrypted](/help/assets/configuration/cloud-enc.png) | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Clé de chiffrement côté client active | `payment_fr/eway/live_encryption_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![Encrypted](/help/assets/configuration/cloud-enc.png) | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Clé API Sandbox | `payment_fr/eway/sandbox_api_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![Encrypted](/help/assets/configuration/cloud-enc.png) | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Mot de passe de l’API Sandbox | `payment_fr/eway/sandbox_api_password` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![Encrypted](/help/assets/configuration/cloud-enc.png) | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Clé de chiffrement côté client Sandbox | `payment_fr/eway/sandbox_encryption_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![Encrypted](/help/assets/configuration/cloud-enc.png) | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Clé de transaction | `payment_it/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Encrypted](/help/assets/configuration/cloud-enc.png) | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Mode test | `payment_it/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Spécifique au système](/help/assets/configuration/cloud-env.png) |
| URL de passerelle | `payment_it/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| URL des détails de transaction | `payment_it/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Clé de transaction | `payment_it/cybersource/transaction_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![Encrypted](/help/assets/configuration/cloud-enc.png) | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Clé d’accès | `payment_it/cybersource/access_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![Encrypted](/help/assets/configuration/cloud-enc.png) | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Clé secrète | `payment_it/cybersource/secret_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![Encrypted](/help/assets/configuration/cloud-enc.png) | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Mode test | `payment_it/cybersource/sandbox_flag` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | | ![Spécifique au système](/help/assets/configuration/cloud-env.png) |
| Mot de passe de réponse de paiement | `payment_it/worldpay/response_password` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Mot de passe d’autorisation d’administrateur distant | `payment_it/worldpay/auth_password` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Mode test | `payment_it/worldpay/sandbox_flag` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | | ![Spécifique au système](/help/assets/configuration/cloud-env.png) |
| Mode sandbox | `payment_it/eway/sandbox_flag` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | | ![Spécifique au système](/help/assets/configuration/cloud-env.png) |
| Clé d’API Live | `payment_it/eway/live_api_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![Encrypted](/help/assets/configuration/cloud-enc.png) | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Mot de passe de l’API Live | `payment_it/eway/live_api_password` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![Encrypted](/help/assets/configuration/cloud-enc.png) | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Clé de chiffrement côté client active | `payment_it/eway/live_encryption_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![Encrypted](/help/assets/configuration/cloud-enc.png) | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Clé API Sandbox | `payment_it/eway/sandbox_api_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![Encrypted](/help/assets/configuration/cloud-enc.png) | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Mot de passe de l’API Sandbox | `payment_it/eway/sandbox_api_password` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![Encrypted](/help/assets/configuration/cloud-enc.png) | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Clé de chiffrement côté client Sandbox | `payment_it/eway/sandbox_encryption_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![Encrypted](/help/assets/configuration/cloud-enc.png) | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Clé API | `fraud_protection/signifyd/api_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![Encrypted](/help/assets/configuration/cloud-enc.png) | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| URL de l’API | `fraud_protection/signifyd/api_url` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |  | ![Spécifique au système](/help/assets/configuration/cloud-env.png) | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Informations d’identification SFTP | `payment_au/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Informations d’identification SFTP | `payment_au/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Informations d’identification SFTP | `payment_au/paypal_payment_gateways/paypal_payflowpro_au/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| ID de connexion API | `payment_au/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Encrypted](/help/assets/configuration/cloud-enc.png) | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Merchant MD5 | `payment_au/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Encrypted](/help/assets/configuration/cloud-enc.png) | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Client de messagerie | `payment_au/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| L&#39;email du marchand | `payment_au/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| ID d’installation d’administrateur distant | `payment_au/worldpay/admin_installation_id` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Secret MD5 pour les transactions | `payment_au/worldpay/md5_secret` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Informations d’identification SFTP | `payment_es/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Informations d’identification SFTP | `payment_es/paypal_group_all_in_one/payments_pro_hosted_solution_es/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Informations d’identification SFTP | `payment_es/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Envoyer la vérification à | `payment_es/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| ID de connexion API | `payment_es/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Encrypted](/help/assets/configuration/cloud-enc.png) | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Merchant MD5 | `payment_es/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Encrypted](/help/assets/configuration/cloud-enc.png) | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Client de messagerie | `payment_es/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| L&#39;email du marchand | `payment_es/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Identifiant du marchand | `payment_es/cybersource/merchant_id` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![Encrypted](/help/assets/configuration/cloud-enc.png) | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Identifiant de profil | `payment_es/cybersource/profile_id` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![Encrypted](/help/assets/configuration/cloud-enc.png) | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| ID d’installation d’administrateur distant | `payment_es/worldpay/admin_installation_id` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Informations d’identification SFTP | `payment_nz/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Informations d’identification SFTP |
| Informations d’identification SFTP | `payment_nz/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Informations d’identification SFTP | `payment_nz/paypal_payment_gateways/paypal_payflowpro_nz/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| ID de connexion API | `payment_nz/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Encrypted](/help/assets/configuration/cloud-enc.png) | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Merchant MD5 | `payment_nz/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Encrypted](/help/assets/configuration/cloud-enc.png) | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Client de messagerie | `payment_nz/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| L&#39;email du marchand | `payment_nz/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Identifiant du marchand | `payment_nz/cybersource/merchant_id` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![Encrypted](/help/assets/configuration/cloud-enc.png) | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Clé de transaction | `payment_nz/cybersource/transaction_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![Encrypted](/help/assets/configuration/cloud-enc.png) | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Identifiant de profil | `payment_nz/cybersource/profile_id` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![Encrypted](/help/assets/configuration/cloud-enc.png) | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Clé d’accès | `payment_nz/cybersource/access_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![Encrypted](/help/assets/configuration/cloud-enc.png) | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Clé secrète | `payment_nz/cybersource/secret_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![Encrypted](/help/assets/configuration/cloud-enc.png) | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| ID d’installation | `payment_nz/worldpay/installation_id` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Mot de passe de réponse de paiement | `payment_nz/worldpay/response_password` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| ID d’installation d’administrateur distant | `payment_nz/worldpay/admin_installation_id` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Mot de passe d’autorisation d’administrateur distant | `payment_nz/worldpay/auth_password` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Secret MD5 pour les transactions | `payment_nz/worldpay/md5_secret` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Informations d’identification SFTP | `payment_us/paypal_alternative_payment_methods/express_checkout_us/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Informations d’identification SFTP | `payment_us/paypal_group_all_in_one/payflow_advanced/settings_payments_advanced/settings_payments_advanced_advanced/settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Informations d’identification SFTP | `payment_us/paypal_group_all_in_one/wpp_usuk/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Informations d’identification SFTP | `payment_us/paypal_group_all_in_one/wps_express/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Informations d’identification SFTP | `payment_us/paypal_payment_gateways/paypal_payflowpro_with_express_checkout/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Informations d’identification SFTP | `payment_us/paypal_payment_gateways/payflow_link_us/settings_payflow_link/settings_payflow_link_advanced/payflow_link_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| ID de connexion API | `payment_us/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Encrypted](/help/assets/configuration/cloud-enc.png) | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Clé de transaction | `payment_us/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Encrypted](/help/assets/configuration/cloud-enc.png) | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Merchant MD5 | `payment_us/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Encrypted](/help/assets/configuration/cloud-enc.png) | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Client de messagerie | `payment_us/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| L&#39;email du marchand | `payment_us/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Identifiant du marchand | `payment_us/cybersource/merchant_id` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![Encrypted](/help/assets/configuration/cloud-enc.png) | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Clé de transaction | `payment_us/cybersource/transaction_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![Encrypted](/help/assets/configuration/cloud-enc.png) | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Identifiant de profil | `payment_us/cybersource/profile_id` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![Encrypted](/help/assets/configuration/cloud-enc.png) | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| ID d’installation | `payment_us/worldpay/installation_id` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Mot de passe de réponse de paiement | `payment_us/worldpay/response_password` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| ID d’installation d’administrateur distant | `payment_us/worldpay/admin_installation_id` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Mot de passe d’autorisation d’administrateur distant | `payment_us/worldpay/auth_password` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Secret MD5 pour les transactions | `payment_us/worldpay/md5_secret` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Informations d’identification SFTP | `payment_gb/paypal_alternative_payment_methods/express_checkout_gb/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Informations d’identification SFTP | `payment_gb/paypal_group_all_in_one/payments_pro_hosted_solution_with_express_checkout/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Informations d’identification SFTP | `payment_gb/paypal_group_all_in_one/wps_express/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Envoyer la vérification à | `payment_gb/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Identifiant du marchand | `payment_gb/cybersource/merchant_id` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![Encrypted](/help/assets/configuration/cloud-enc.png) | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Clé de transaction | `payment_gb/cybersource/transaction_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![Encrypted](/help/assets/configuration/cloud-enc.png) | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Identifiant de profil | `payment_gb/cybersource/profile_id` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![Encrypted](/help/assets/configuration/cloud-enc.png) | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Clé d’accès | `payment_gb/cybersource/access_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![Encrypted](/help/assets/configuration/cloud-enc.png) | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Clé secrète | `payment_gb/cybersource/secret_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![Encrypted](/help/assets/configuration/cloud-enc.png) | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| ID de connexion API | `payment_gb/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Encrypted](/help/assets/configuration/cloud-enc.png) | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Clé de transaction | `payment_gb/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Encrypted](/help/assets/configuration/cloud-enc.png) | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Merchant MD5 | `payment_gb/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Encrypted](/help/assets/configuration/cloud-enc.png) | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Client de messagerie | `payment_gb/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| L&#39;email du marchand | `payment_gb/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| ID d’installation | `payment_gb/worldpay/installation_id` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Mot de passe de réponse de paiement | `payment_gb/worldpay/response_password` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| ID d’installation d’administrateur distant | `payment_gb/worldpay/admin_installation_id` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Mot de passe d’autorisation d’administrateur distant | `payment_gb/worldpay/auth_password` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Informations d’identification SFTP | `payment_de/paypal_payment_solutions/express_checkout_de/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Rendre le paiement | `payment_de/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Envoyer la vérification à | `payment_de/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Identifiant du marchand | `payment_de/cybersource/merchant_id` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![Encrypted](/help/assets/configuration/cloud-enc.png) | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Identifiant de profil | `payment_de/cybersource/profile_id` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![Encrypted](/help/assets/configuration/cloud-enc.png) | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| ID de connexion API | `payment_de/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Encrypted](/help/assets/configuration/cloud-enc.png) | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Merchant MD5 | `payment_de/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Encrypted](/help/assets/configuration/cloud-enc.png) | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Client de messagerie | `payment_de/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| L&#39;email du marchand | `payment_de/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| ID d’installation | `payment_de/worldpay/installation_id` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| ID d’installation d’administrateur distant | `payment_de/worldpay/admin_installation_id` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Secret MD5 pour les transactions | `payment_de/worldpay/md5_secret` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Informations d’identification SFTP | `payment_other/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Informations d’identification SFTP | `payment_other/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Rendre le paiement | `payment_other/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Envoyer la vérification à | `payment_other/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| ID de connexion API | `payment_other/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Encrypted](/help/assets/configuration/cloud-enc.png) | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Merchant MD5 | `payment_other/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Encrypted](/help/assets/configuration/cloud-enc.png) | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| New Order Status | `payment_other/authorizenet_directpost/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| L&#39;email du marchand | `payment_other/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Identifiant du marchand | `payment_other/cybersource/merchant_id` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![Encrypted](/help/assets/configuration/cloud-enc.png) | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Identifiant de profil | `payment_other/cybersource/profile_id` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![Encrypted](/help/assets/configuration/cloud-enc.png) | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| ID d’installation | `payment_other/worldpay/installation_id` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| ID d’installation d’administrateur distant | `payment_other/worldpay/admin_installation_id` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Secret MD5 pour les transactions | `payment_other/worldpay/md5_secret` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Informations d’identification SFTP | `payment_ca/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Informations d’identification SFTP | `payment_ca/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Informations d’identification SFTP | `payment_ca/paypal_payment_gateways/wpp_ca/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Informations d’identification SFTP | `payment_ca/paypal_payment_gateways/paypal_payflowpro_ca/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Informations d’identification SFTP | `payment_ca/paypal_payment_gateways/payflow_link_ca/settings_payflow_link/settings_payflow_link_advanced/payflow_link_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Rendre le paiement | `payment_ca/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Envoyer la vérification à | `payment_ca/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| ID de connexion API | `payment_ca/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Encrypted](/help/assets/configuration/cloud-enc.png) | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Merchant MD5 | `payment_ca/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Encrypted](/help/assets/configuration/cloud-enc.png) | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| New Order Status | `payment_ca/authorizenet_directpost/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Client de messagerie | `payment_ca/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| L&#39;email du marchand | `payment_ca/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Identifiant du marchand | `payment_ca/cybersource/merchant_id` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![Encrypted](/help/assets/configuration/cloud-enc.png) | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Identifiant de profil | `payment_ca/cybersource/profile_id` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![Encrypted](/help/assets/configuration/cloud-enc.png) | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| ID d’installation | `payment_ca/worldpay/installation_id` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| ID d’installation d’administrateur distant | `payment_ca/worldpay/admin_installation_id` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Secret MD5 pour les transactions | `payment_ca/worldpay/md5_secret` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Informations d’identification SFTP | `payment_hk/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Informations d’identification SFTP | `payment_hk/paypal_group_all_in_one/payments_pro_hosted_solution_hk/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Informations d’identification SFTP | `payment_hk/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Rendre le paiement | `payment_hk/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Envoyer la vérification à | `payment_hk/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| ID de connexion API | `payment_hk/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Encrypted](/help/assets/configuration/cloud-enc.png) | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Merchant MD5 | `payment_hk/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Encrypted](/help/assets/configuration/cloud-enc.png) | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Client de messagerie | `payment_hk/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| L&#39;email du marchand | `payment_hk/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Identifiant du marchand | `payment_hk/cybersource/merchant_id` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![Encrypted](/help/assets/configuration/cloud-enc.png) | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Identifiant de profil | `payment_hk/cybersource/profile_id` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![Encrypted](/help/assets/configuration/cloud-enc.png) | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| ID d’installation | `payment_hk/worldpay/installation_id` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| ID d’installation d’administrateur distant | `payment_hk/worldpay/admin_installation_id` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Secret MD5 pour les transactions | `payment_hk/worldpay/md5_secret` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Champs de signature | `payment_hk/worldpay/signature_fields` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Informations d’identification SFTP | `payment_jp/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Informations d’identification SFTP | `payment_jp/paypal_group_all_in_one/payments_pro_hosted_solution_jp/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Informations d’identification SFTP | `payment_jp/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Rendre le paiement | `payment_jp/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Envoyer la vérification à | `payment_jp/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| ID de connexion API | `payment_jp/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Encrypted](/help/assets/configuration/cloud-enc.png) | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Merchant MD5 | `payment_jp/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Encrypted](/help/assets/configuration/cloud-enc.png) | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Client de messagerie | `payment_jp/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| L&#39;email du marchand | `payment_jp/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Identifiant du marchand | `payment_jp/cybersource/merchant_id` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![Encrypted](/help/assets/configuration/cloud-enc.png) | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Identifiant de profil | `payment_jp/cybersource/profile_id` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![Encrypted](/help/assets/configuration/cloud-enc.png) | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| ID d’installation | `payment_jp/worldpay/installation_id` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| ID d’installation d’administrateur distant | `payment_jp/worldpay/admin_installation_id` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Secret MD5 pour les transactions | `payment_jp/worldpay/md5_secret` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Champs de signature | `payment_jp/worldpay/signature_fields` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Informations d’identification SFTP | `payment_fr/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Informations d’identification SFTP | `payment_fr/paypal_group_all_in_one/payments_pro_hosted_solution_fr/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Informations d’identification SFTP | `payment_fr/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Rendre le paiement | `payment_fr/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Envoyer la vérification à | `payment_fr/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| ID de connexion API | `payment_fr/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Encrypted](/help/assets/configuration/cloud-enc.png) | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Merchant MD5 | `payment_fr/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Encrypted](/help/assets/configuration/cloud-enc.png) | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Client de messagerie | `payment_fr/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| L&#39;email du marchand | `payment_fr/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Identifiant du marchand | `payment_fr/cybersource/merchant_id` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![Encrypted](/help/assets/configuration/cloud-enc.png) | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Identifiant de profil | `payment_fr/cybersource/profile_id` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![Encrypted](/help/assets/configuration/cloud-enc.png) | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| ID d’installation | `payment_fr/worldpay/installation_id` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| ID d’installation d’administrateur distant | `payment_fr/worldpay/admin_installation_id` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Secret MD5 pour les transactions | `payment_fr/worldpay/md5_secret` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Champs de signature | `payment_fr/worldpay/signature_fields` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Informations d’identification SFTP | `payment_it/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Informations d’identification SFTP | `payment_it/paypal_group_all_in_one/payments_pro_hosted_solution_it/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Informations d’identification SFTP | `payment_it/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Rendre le paiement | `payment_it/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Envoyer la vérification à | `payment_it/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| ID de connexion API | `payment_it/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Encrypted](/help/assets/configuration/cloud-enc.png) | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Merchant MD5 | `payment_it/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Encrypted](/help/assets/configuration/cloud-enc.png) | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Client de messagerie | `payment_it/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| L&#39;email du marchand | `payment_it/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Identifiant du marchand | `payment_it/cybersource/merchant_id` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![Encrypted](/help/assets/configuration/cloud-enc.png) | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Identifiant de profil | `payment_it/cybersource/profile_id` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![Encrypted](/help/assets/configuration/cloud-enc.png) | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| ID d’installation | `payment_it/worldpay/installation_id` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| ID d’installation d’administrateur distant | `payment_it/worldpay/admin_installation_id` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |
| Secret MD5 pour les transactions | `payment_it/worldpay/md5_secret` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | | | ![Sensitive](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}
