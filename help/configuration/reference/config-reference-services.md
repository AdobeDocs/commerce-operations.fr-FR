---
title: Référence sur les chemins de configuration des services
description: Consultez la liste des valeurs de configuration des services.
feature: Configuration, Services
exl-id: 77818c54-21ae-4a66-81bf-468bd7d09cda
source-git-commit: 16e9396f19693436dfc7bdac78d84624a78f0c21
workflow-type: tm+mt
source-wordcount: '156'
ht-degree: 0%

---

# Référence sur les chemins de configuration des services

Cette section répertorie les noms de variable et les chemins de configuration disponibles pour les options dans l’administrateur sous **Magasins** > Paramètres > **Configuration** > **Services**.

La commande [`magento app:config:dump`](../cli/export-configuration.md) écrit ces valeurs dans le fichier de configuration partagé, `app/etc/config.php`, qui doit être dans le contrôle source. Pour éventuellement remplacer des paramètres de configuration ou définir des paramètres sensibles, reportez-vous à la section [Utilisation de variables d’environnement pour remplacer les paramètres de configuration](override-config-settings.md#environment-variables). Cette rubrique ne _répertorie pas_ les [ valeurs sensibles et spécifiques au système ](config-reference-sens.md).

## Chemins d’accès aux API Web Commerce

Ces valeurs de configuration sont disponibles dans l’Admin de **Magasins** > Paramètres > **Configuration** > **Services** > **API web**.

| Nom | Chemin de configuration | Commerce uniquement ? |
|--------------|--------------|--------------|
| Charset de réponse par défaut | `webapi/soap/charset` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Autoriser l’accès des invités anonymes | `webapi/webapisecurity/allow_insecure` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Chemins OAuth

Ces valeurs de configuration sont disponibles dans l’Admin de **Magasins** > Paramètres > **Configuration** > **Services** > **OAuth**.

| Nom | Chemin de configuration | Commerce uniquement ? |
|--------------|--------------|--------------|
| Durée de vie du jeton client (heures) | `oauth/access_token_lifetime/customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Durée de vie du jeton d’administration (heures) | `oauth/access_token_lifetime/admin` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Probabilité de nettoyage | `oauth/cleanup/cleanup_probability` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Période d’expiration | `oauth/cleanup/expiration_period` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Période d’expiration | `oauth/consumer/expiration_period` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modules de redirection HTTP Post des informations d’identification du client OAuth | `oauth/consumer/post_maxredirects` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Délai d’expiration HTTP Post des informations d’identification du client OAuth | `oauth/consumer/post_timeout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}
