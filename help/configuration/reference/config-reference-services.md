---
title: Référence sur les chemins de configuration des services
description: Consultez la liste des valeurs de configuration des services.
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '162'
ht-degree: 0%

---


# Référence sur les chemins de configuration des services

Cette section répertorie les noms de variable et les chemins de configuration disponibles pour les options dans l’Admin sous **Magasins** > Paramètres > **Configuration** > **Services**.

Le [`magento app:config:dump` command](../cli/export-configuration.md) écrit ces valeurs dans le fichier de configuration partagé, `app/etc/config.php`, qui doit être dans le contrôle de code source. Pour éventuellement remplacer des paramètres de configuration ou définir des paramètres sensibles, voir [Utilisation des variables d’environnement pour remplacer les paramètres de configuration](override-config-settings.md#environment-variables). Cette rubrique fonctionne _not_ list [valeurs sensibles et spécifiques au système](config-reference-sens.md).

## Chemins des API Web Commerce

Ces valeurs de configuration sont disponibles dans l’ Admin de **Magasins** > Paramètres > **Configuration** > **Services** > **API Web**.

| Nom | Chemin de configuration | Commerce uniquement ? |
|--------------|--------------|--------------|
| Charset de réponse par défaut | `webapi/soap/charset` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Autoriser l’accès des invités anonymes | `webapi/webapisecurity/allow_insecure` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style=&quot;table-layout:auto&quot;}

## Chemins OAuth

Ces valeurs de configuration sont disponibles dans l’ Admin de **Magasins** > Paramètres > **Configuration** > **Services** > **OAuth**.

| Nom | Chemin de configuration | Commerce uniquement ? |
|--------------|--------------|--------------|
| Durée de vie du jeton client (heures) | `oauth/access_token_lifetime/customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Durée de vie du jeton d’administration (heures) | `oauth/access_token_lifetime/admin` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Probabilité de nettoyage | `oauth/cleanup/cleanup_probability` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Période d’expiration | `oauth/cleanup/expiration_period` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Période d’expiration | `oauth/consumer/expiration_period` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Informations d’identification de l’utilisateur OAuth sur les maxredirections HTTP Post | `oauth/consumer/post_maxredirects` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Délai d’expiration HTTP Post des informations d’identification du client OAuth | `oauth/consumer/post_timeout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style=&quot;table-layout:auto&quot;}
