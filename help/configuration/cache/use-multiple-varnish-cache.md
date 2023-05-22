---
title: Nettoyage du cache avec plusieurs instances de vernis
description: Découvrez comment l’effacement du cache fonctionne avec plusieurs instances de vernis.
feature: Configuration, Cache
exl-id: 289a4e54-9e73-454c-bfb9-e78e405af56c
source-git-commit: a2bd4139aac1044e7e5ca8fcf2114b7f7e9e9b68
workflow-type: tm+mt
source-wordcount: '179'
ht-degree: 0%

---

# Nettoyage du cache de plusieurs instances Varnish

Adobe Commerce et Magento Open Source prennent en charge plusieurs instances de vernis prêtes à l’emploi.

Cette rubrique présente les principes de base de la configuration de plusieurs instances de vernis avec Commerce.

## Configuration pour purger plusieurs instances de vernis

Commerce purge les hôtes ternes après avoir configuré les hôtes ternes à l’aide de la fonction [`magento setup:config:set`](../../installation/tutorials/deployment.md) .

Vous devez utiliser la variable `--http-cache-hosts` pour spécifier une liste séparée par des virgules d’hôtes et de ports d’écoute Varnish. (Ne séparez pas les hôtes avec un espace.)

Le format du paramètre doit être `<hostname or ip>:<listen port>`, où vous pouvez omettre `<listen port>` s’il s’agit du port 80.

Par exemple :

```bash
bin/magento setup:config:set --http-cache-hosts=192.0.2.100,192.0.2.155:8080
```

Vous pouvez ensuite purger tous les hôtes de marque lors de l’actualisation du cache Commerce (également appelé _nettoyage_ le cache) dans l’Admin ou à l’aide de la ligne de commande.

Pour actualiser le cache à l’aide de l’administrateur, cliquez sur **SYSTÈME** > Outils > **Gestion du cache**, puis cliquez sur **Vider le cache du Magento** en haut de la page. (Vous pouvez également actualiser des types de cache individuels.)

Pour actualiser le cache de plusieurs instances de vernis à partir de l’interface de ligne de commande, utilisez la fonction [`magento cache:clean <type>`](../cli/manage-cache.md#clean-and-flush-cache-types) comme la commande [propriétaire du système de fichiers](../../installation/prerequisites/file-system/overview.md).
