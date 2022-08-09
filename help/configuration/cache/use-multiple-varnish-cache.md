---
title: Nettoyage du cache avec plusieurs instances de vernis
description: Découvrez comment l’effacement du cache fonctionne avec plusieurs instances de vernis.
source-git-commit: 80abb0180fcd8ecc275428c23b68feb5883cbc28
workflow-type: tm+mt
source-wordcount: '194'
ht-degree: 1%

---


# Nettoyage du cache de plusieurs instances Varnish

Adobe Commerce et Magento Open Source prennent en charge plusieurs instances de vernis prêtes à l’emploi.

Cette rubrique présente les principes de base de la configuration de plusieurs instances de vernis avec Commerce.

## Configuration pour purger plusieurs instances de vernis

Commerce purge les hôtes ternes après avoir configuré les hôtes ternes à l’aide de la fonction [`magento setup:config:set`](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-deployment.html) .

Vous devez utiliser la variable `--http-cache-hosts` pour spécifier une liste séparée par des virgules d’hôtes et de ports d’écoute Varnish. (Ne séparez pas les hôtes avec un espace.)

Le format du paramètre doit être `<hostname or ip>:<listen port>`, où vous pouvez omettre `<listen port>` s’il s’agit du port 80.

Par exemple,

```bash
bin/magento setup:config:set --http-cache-hosts=192.0.2.100,192.0.2.155:8080
```

Vous pouvez ensuite purger tous les hôtes de marque lors de l’actualisation du cache Commerce (également appelé _nettoyage_ le cache) dans l’Admin ou à l’aide de la ligne de commande.

Pour actualiser le cache à l’aide de l’administrateur, cliquez sur **SYSTÈME** > Outils > **Gestion du cache**, puis cliquez sur **Vider le cache du Magento** en haut de la page. (Vous pouvez également actualiser des types de cache individuels.)

Pour actualiser le cache de plusieurs instances de vernis à partir de l’interface de ligne de commande, utilisez la fonction [`magento cache:clean <type>`](../cli/manage-cache.md#clean-and-flush-cache-types) comme la commande [propriétaire du système de fichiers](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-sys-perms-over.html).