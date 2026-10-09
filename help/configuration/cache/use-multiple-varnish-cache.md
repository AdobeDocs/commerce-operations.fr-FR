---
title: Effacement du cache avec plusieurs instances de vernis
description: Découvrez comment l’effacement du cache fonctionne avec plusieurs instances Varnish dans Adobe Commerce. Découvrez les bonnes pratiques de configuration et de gestion.
feature: Configuration, Cache
exl-id: 289a4e54-9e73-454c-bfb9-e78e405af56c
badgePaas: label="Sur Site" type="Informative" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="S’applique uniquement aux projets sur site Adobe Commerce."
autotag-review: '2026-06-22T22:16:50.500Z'
TQID: 'https://experienceleague.adobe.com/GeX8wkpM1rLLWM7jMhP2r-SJ8uV-x7fLXC8WEazZQDo'
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
subfeature_v2:
  - id: b673188e-f9fa-492a-b470-c8f949bf7827
    internal-label: Cache
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
    internal-label: Intermediate
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
    internal-label: Implementation
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '206'
ht-degree: 0%
---
# Effacement du cache avec plusieurs instances Varnish

Adobe Commerce prend en charge plusieurs instances de vernis prêtes à l’emploi.

Cette rubrique présente les principes de base de la configuration de plusieurs instances Varnish avec Commerce.

{{varnish-config-cloud}}

## Configuration pour purger plusieurs instances Varnish

Commerce purge les hôtes Varnish après avoir configuré les hôtes Varnish à l’aide de la commande [`magento setup:config:set`](../../installation/tutorials/deployment.md).

Vous devez utiliser le paramètre `--http-cache-hosts` pour spécifier une liste séparée par des virgules d&#39;hôtes Varnish et de ports d&#39;écoute. (Ne séparez pas les hôtes avec un espace.)

Le format du paramètre doit être `<hostname or ip>:<listen port>`, où vous pouvez omettre `<listen port>` s’il s’agit du port 80.

Par exemple,

```shell
bin/magento setup:config:set --http-cache-hosts=192.0.2.100,192.0.2.155:8080
```

Vous pouvez ensuite purger tous les hôtes Varnish lorsque vous actualisez le cache de Commerce (également appelé _nettoyage_ du cache) dans Admin ou à l’aide de la ligne de commande.

Pour actualiser le cache à l’aide de l’Administration, cliquez sur **SYSTEM** > Outils > **Gestion du cache**, puis cliquez sur **Vider le cache Magento** en haut de la page. (Vous pouvez également actualiser des types de cache individuels.)

Pour actualiser le cache de plusieurs instances Varnish à partir de l’interface en ligne de commande, utilisez la commande [`magento cache:clean <type>`](../cli/manage-cache.md#clean-and-flush-cache-types) comme [propriétaire du système de fichiers](../../installation/prerequisites/file-system/overview.md).
