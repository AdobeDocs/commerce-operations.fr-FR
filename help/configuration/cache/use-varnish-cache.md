---
title: Nettoyage du cache avec vernis
description: Découvrez comment l’effacement de la mémoire cache fonctionne avec le vernis et comment l’utiliser comme accélérateur de mise en cache web pour l’application Adobe Commerce.
source-git-commit: c65c065c5f9ac2847caa8898535afdacf089006a
workflow-type: tm+mt
source-wordcount: '395'
ht-degree: 0%

---


# Nettoyage du cache avec vernis

Cette rubrique aborde les principes de base de l’utilisation du vernis comme accélérateur de mise en cache web pour Adobe Commerce et Magento Open Source.

## Purge de vernis

Selon [Documentation en pointillé](https://www.varnish-cache.org/docs/trunk/users-guide/purging.html), &quot;A *purge* est ce qui se passe lorsque vous sélectionnez un objet dans la variable [cache](https://glossary.magento.com/cache) et le jetez avec ses variantes.&quot; Une purge de vernis est similaire à une commande de nettoyage du cache (ou en cliquant sur **Vider le cache du Magento** dans Admin).

En fait, lorsque vous nettoyez, videz ou actualisez le cache Commerce, Varnish purge également.

Une fois que vous avez installé et configuré Varnish pour qu’il fonctionne avec Commerce, les actions suivantes peuvent entraîner une purge de vernis :

- Maintien d’un [site web](https://glossary.magento.com/website).

   Par exemple, tout ce que vous faites dans l’Admin de :

   - **MAGASINS** > **Paramètres** > **Configuration** > GÉNÉRAL > **Général**
   - **MAGASINS** > **Paramètres** > **Configuration** > GÉNÉRAL > **Configuration de devise**
   - **MAGASINS** > **Paramètres** > **Configuration** > GÉNÉRAL > **Stocker les adresses électroniques**

   Lorsque Commerce détecte une telle modification, un message s’affiche vous informant de l’actualisation du cache.

- Maintenance d’un magasin (par exemple, ajout ou modification de catégories, de prix, de produits et de règles de tarification promotionnelle).

   Le vernis est purgé automatiquement lorsque vous effectuez l’une de ces tâches.

- Maintenance du code source.

   Vous devez actualiser le cache et supprimer régulièrement tout ce qui se trouve dans la variable `generated/code` et `generated/metadata` répertoires. Pour plus d’informations sur l’actualisation du cache, voir la section suivante.

## Configuration de Commerce pour purger le vernis

Commerce purge les hôtes ternes après avoir configuré les hôtes ternes à l’aide de la fonction [`magento setup:config:set`](https://devdocs.magento.com/guides/v2.4/reference/cli/magento.html#setupconfigset) .

Vous pouvez utiliser le paramètre facultatif. `--http-cache-hosts` pour spécifier une liste séparée par des virgules d’hôtes et de ports d’écoute Varnish. Configurez tous les hôtes vernis, qu’il y en ait un ou plusieurs. (Ne séparez pas les hôtes avec un espace.)

Le format du paramètre doit être `<hostname or ip>:<listen port>`, où vous pouvez omettre `<listen port>` s’il s’agit du port 80.

Par exemple,

```bash
bin/magento setup:config:set --http-cache-hosts=192.0.2.100,192.0.2.155:6081
```

Vous pouvez ensuite purger les hôtes ternes lorsque vous actualisez le cache Commerce (également appelé *nettoyage* le cache) dans l’Admin ou à l’aide de la ligne de commande.

Pour actualiser le cache à l’aide de l’administrateur, cliquez sur **[!UICONTROL SYSTEM]** > Outils > **Gestion du cache**, puis cliquez sur **Vider le cache du Magento** en haut de la page. (Vous pouvez également actualiser des types de cache individuels.)

Pour actualiser le cache à l’aide de la ligne de commande, vous utilisez généralement la méthode [`magento cache:clean <type>`](../cli/manage-cache.md#clean-and-flush-cache-types) comme la commande [propriétaire du système de fichiers](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-sys-perms-over.html).
