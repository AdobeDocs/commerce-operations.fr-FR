---
title: Vérification finale
description: Vérifiez que votre configuration de vernis est correctement configurée pour fonctionner avec l’application Adobe Commerce.
feature: Configuration, Cache
exl-id: 01f28c93-75cd-4969-9142-b8dac0aa2adb
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '345'
ht-degree: 0%

---

# Vérification finale de la configuration du vernis

Maintenant que vous utilisez le `default.vcl` généré pour vous par Commerce, vous pouvez effectuer quelques vérifications finales pour vous assurer que le vernis fonctionne.

## Vérifier les en-têtes de réponse HTTP

Utilisez `curl` ou un autre utilitaire pour afficher les en-têtes de réponse HTTP lorsque vous visitez une page Commerce dans un navigateur web.

Tout d’abord, assurez-vous d’utiliser le [mode développeur](../cli/set-mode.md#change-to-developer-mode), sinon les en-têtes ne s’afficheront pas.

Par exemple,

```bash
curl -I -v --location-trusted 'http://192.0.2.55/magento2'
```

En-têtes importants :

```
X-Magento-Cache-Control: max-age=86400, public, s-maxage=86400
Age: 0
X-Magento-Cache-Debug: MISS
```

>[!INFO]
>
>Cette valeur est également acceptable : `X-Magento-Cache-Debug: HIT`.

## Vérifier les temps de chargement des pages

Si le vernis fonctionne, toute page Commerce avec des blocs pouvant être mis en cache doit se charger en moins de 150 ms. Les pages de catégorie porte d’entrée et storefront sont des exemples de ces pages.

Utilisez un inspecteur de navigateur pour mesurer les temps de chargement des pages.

Par exemple, pour utiliser l’inspecteur Chrome :

1. Accédez à n’importe quelle page Commerce pouvant être mise en cache dans Chrome.
1. Cliquez avec le bouton droit n’importe où sur la page.
1. Dans le menu pop-up, cliquez sur **[!UICONTROL Inspect Element]**
1. Dans le volet d&#39;inspection, cliquez sur l&#39;onglet **[!UICONTROL Network]**.
1. Actualisez la page.
1. Faites défiler la page jusqu’en haut du volet d’inspection pour afficher l’URL de la page que vous consultez.

   La figure suivante illustre un exemple de chargement de la page d’index `magento2`.

   ![Cliquez sur la page que vous consultez](../../assets/configuration/varnish-inspector.png)

   Le temps de chargement de la page s’affiche en regard de l’URL de la page. Dans ce cas, le temps de chargement est de 5 ms. Cela permet de confirmer que Varnish a mis la page en cache.

1. Pour afficher les en-têtes de réponse HTTP, cliquez sur l’URL de la page (dans la colonne Nom).

   Vous pouvez afficher les en-têtes HTTP qui sont traités plus en détail dans la section Vérifier les en-têtes de réponse HTTP .

## Vérification du cache du Commerce

Vérifiez que le répertoire `<magento_root>/var/page_cache` est vide :

1. Connectez-vous à votre serveur Commerce ou passez au propriétaire du système de fichiers.
1. Saisissez la commande suivante :

   ```bash
   rm -rf <magento_root>/var/page_cache/*
   ```

1. Accédez à une ou plusieurs pages Commerce pouvant être mises en cache.
1. Vérifiez le répertoire `var/page_cache/`.

   Si le répertoire est vide, félicitations ! Vous avez correctement configuré Varnish et Commerce pour qu’ils fonctionnent ensemble.

1. Si vous avez effacé le répertoire `var/page_cache/`, redémarrez Varnish.

>[!TIP]
>
>Si vous rencontrez des erreurs 503 (échec de la récupération du serveur principal), consultez [Dépannage des erreurs 503 (service indisponible)](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/troubleshooting-503-errors.html?lang=fr) dans le Centre d’aide d’_Adobe Commerce_.
