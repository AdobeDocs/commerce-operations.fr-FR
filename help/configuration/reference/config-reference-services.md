---
title: Référence des chemins de configuration des services
description: Découvrez les chemins et les valeurs de configuration des services dans les paramètres d’administration Adobe Commerce. Découvrez les options de configuration de l’intégration de l’API Web, d’OAuth et du service.
feature: Configuration, Services
exl-id: 77818c54-21ae-4a66-81bf-468bd7d09cda
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '170'
ht-degree: 0%

---

# Référence des chemins de configuration des services

Cette section répertorie les noms de variables et les chemins de configuration disponibles pour les options dans Admin sous **Magasins** > Paramètres > **Configuration** > **Services**.

La commande [`magento app:config:dump` écrit &#x200B;](../cli/export-configuration.md) ces valeurs dans le fichier de configuration partagé, `app/etc/config.php`, qui doit se trouver dans le contrôle de code source. Pour remplacer éventuellement des paramètres de configuration ou définir des paramètres sensibles, voir [Utiliser des variables d’environnement pour remplacer des paramètres de configuration](override-config-settings.md#environment-variables). Cette rubrique ne répertorie _pas_ les [valeurs sensibles et spécifiques au système](config-reference-sens.md).

## Chemins d’accès aux API web Commerce

Ces valeurs de configuration sont disponibles dans Admin dans **Magasins** > Paramètres > **Configuration** > **Services** > **API Web**.

| Nom | Chemin de configuration | Commerce uniquement ? |
|--------------|--------------|--------------|
| Charset de réponse par défaut | `webapi/soap/charset` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Autoriser l’accès anonyme des invités | `webapi/webapisecurity/allow_insecure` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Chemins OAuth

Ces valeurs de configuration sont disponibles dans Admin dans **Magasins** > Paramètres > **Configuration** > **Services** > **OAuth**.

| Nom | Chemin de configuration | Commerce uniquement ? |
|--------------|--------------|--------------|
| Durée de vie du jeton client (heures) | `oauth/access_token_lifetime/customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Durée de vie du jeton d’administration (heures) | `oauth/access_token_lifetime/admin` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Probabilité de nettoyage | `oauth/cleanup/cleanup_probability` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Délai d’expiration | `oauth/cleanup/expiration_period` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Délai d’expiration | `oauth/consumer/expiration_period` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Informations d’identification du client OAuth via les redirections max du post HTTP | `oauth/consumer/post_maxredirects` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Délai d’expiration du post HTTP des informations d’identification du client OAuth | `oauth/consumer/post_timeout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}
