---
title: Effacement du cache avec vernis
description: Découvrez comment l’effacement du cache fonctionne avec Varnish et comment l’utiliser comme accélérateur de mise en cache web pour l’application Adobe Commerce.
feature: Configuration, Cache
exl-id: 866da415-c428-4092-a045-c3079493cdc4
source-git-commit: 79c8a15fb9686dd26d73805e9d0fd18bb987770d
workflow-type: tm+mt
source-wordcount: '367'
ht-degree: 0%

---

# Effacement du cache avec vernis

Cette rubrique présente les principes de base de l’utilisation de Varnish comme accélérateur de mise en cache web pour Adobe Commerce.

## Purge de vernis

Selon la [documentation Varnish](https://www.varnish-cache.org/docs/trunk/users-guide/purging.html), « une *purge* est ce qui se produit lorsque vous sélectionnez un objet du cache et que vous le supprimez avec ses variantes ». Une purge de vernis est similaire à une commande de nettoyage du cache (ou à un clic sur **Vider le cache Magento** dans l’Administration).

En fait, lorsque vous nettoyez, videz ou actualisez le cache de Commerce, Varnish se purge également.

Après avoir installé et configuré le vernis pour qu’il fonctionne avec Commerce, les actions suivantes peuvent entraîner une purge du vernis :

- Maintenance d’un site web.

  Par exemple, toutes les actions effectuées dans l’Administration dans :

   - **MAGASINS** > **Paramètres** > **Configuration** > GÉNÉRAL > **Général**
   - **MAGASINS** > **Paramètres** > **Configuration** > GÉNÉRAL > **Configuration de la devise**
   - **MAGASINS** > **Paramètres** > **Configuration** > GÉNÉRAL > **Adresses e-mail du magasin**

  Lorsque Commerce détecte une telle modification, un message s’affiche pour vous informer d’actualiser le cache.

- Tenir à jour un magasin (par exemple, ajouter ou modifier des catégories, des prix, des produits et des règles de tarification promotionnelle).

  Le vernis est automatiquement purgé lorsque vous effectuez l&#39;une de ces tâches.

- Gestion du code source.

  Vous devez actualiser le cache et également supprimer périodiquement tout ce qui se trouve dans les répertoires `generated/code` et `generated/metadata`. Pour plus d’informations sur l’actualisation du cache, consultez la section suivante.

## Configuration de Commerce pour purger le vernis

Commerce purge les hôtes Varnish après avoir configuré les hôtes Varnish à l’aide de la commande [`magento setup:config:set`](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/cli-reference/commerce-on-premises#setupconfigset).

Vous pouvez utiliser le paramètre facultatif `--http-cache-hosts` pour spécifier une liste séparée par des virgules d&#39;hôtes et de ports d&#39;écoute de vernis. Configurez tous les hôtes Varnish, que vous en ayez un ou plusieurs. (Ne séparez pas les hôtes avec un espace.)

Le format du paramètre doit être `<hostname or ip>:<listen port>`, où vous pouvez omettre `<listen port>` s’il s’agit du port 80.

Par exemple,

```bash
bin/magento setup:config:set --http-cache-hosts=192.0.2.100,192.0.2.155:6081
```

Vous pouvez ensuite purger les hôtes Vernis lorsque vous actualisez le cache de Commerce (également appelé *nettoyage* du cache) dans l’Administration ou à l’aide de la ligne de commande.

Pour actualiser le cache à l’aide de l’Administration, cliquez sur **[!UICONTROL SYSTEM]** > Outils > **Gestion du cache**, puis cliquez sur **Vider le cache Magento** en haut de la page. (Vous pouvez également actualiser des types de cache individuels.)

Pour actualiser le cache à l’aide de la ligne de commande, vous utilisez généralement la commande [`magento cache:clean <type>`](../cli/manage-cache.md#clean-and-flush-cache-types) comme [propriétaire du système de fichiers](../../installation/prerequisites/file-system/overview.md).
