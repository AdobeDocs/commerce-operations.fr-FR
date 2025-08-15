---
title: Effacement du cache avec plusieurs instances Varnish
description: Découvrez comment l’effacement du cache fonctionne avec plusieurs instances de vernis.
feature: Configuration, Cache
exl-id: 289a4e54-9e73-454c-bfb9-e78e405af56c
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '176'
ht-degree: 1%

---

# Effacement du cache de plusieurs instances Varnish

Adobe Commerce prend en charge plusieurs instances de vernis prêtes à l’emploi.

Cette rubrique présente les principes de base de la configuration de plusieurs instances Varnish avec Commerce.

## Configuration pour purger plusieurs instances Varnish

Commerce purge les hôtes Varnish après avoir configuré les hôtes Varnish à l’aide de la commande [`magento setup:config:set`](../../installation/tutorials/deployment.md).

Vous devez utiliser le paramètre `--http-cache-hosts` pour spécifier une liste séparée par des virgules d&#39;hôtes Varnish et de ports d&#39;écoute. (Ne séparez pas les hôtes avec un espace.)

Le format du paramètre doit être `<hostname or ip>:<listen port>`, où vous pouvez omettre `<listen port>` s’il s’agit du port 80.

Par exemple,

```bash
bin/magento setup:config:set --http-cache-hosts=192.0.2.100,192.0.2.155:8080
```

Vous pouvez ensuite purger tous les hôtes Varnish lorsque vous actualisez le cache de Commerce (également appelé _nettoyage_ du cache) dans Admin ou à l’aide de la ligne de commande.

Pour actualiser le cache à l’aide de l’Administration, cliquez sur **SYSTEM** > Outils > **Gestion du cache**, puis cliquez sur **Vider le cache Magento** en haut de la page. (Vous pouvez également actualiser des types de cache individuels.)

Pour actualiser le cache de plusieurs instances Varnish à partir de l’interface en ligne de commande, utilisez la commande [`magento cache:clean <type>`](../cli/manage-cache.md#clean-and-flush-cache-types) comme [propriétaire du système de fichiers](../../installation/prerequisites/file-system/overview.md).
