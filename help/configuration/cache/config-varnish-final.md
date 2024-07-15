---
title: Vérification finale
description: Vérifiez que la configuration de vernis est configurée correctement pour fonctionner avec l’application Adobe Commerce.
feature: Configuration, Cache
exl-id: 01f28c93-75cd-4969-9142-b8dac0aa2adb
source-git-commit: a2bd4139aac1044e7e5ca8fcf2114b7f7e9e9b68
workflow-type: tm+mt
source-wordcount: '345'
ht-degree: 0%

---

# Vérification finale de la configuration de vernis

Maintenant que vous utilisez le `default.vcl` généré pour vous par Commerce, vous pouvez effectuer certaines vérifications finales pour vous assurer que Varnish fonctionne.

## Vérification des en-têtes de réponse HTTP

Utilisez `curl` ou un autre utilitaire pour afficher les en-têtes de réponse HTTP lorsque vous visitez une page Commerce dans un navigateur web.

Tout d’abord, assurez-vous d’utiliser le [mode développeur](../cli/set-mode.md#change-to-developer-mode) ; dans le cas contraire, les en-têtes ne s’afficheront pas.

Par exemple,

```bash
curl -I -v --location-trusted 'http://192.0.2.55/magento2'
```

En-têtes importants :

```terminal
X-Magento-Cache-Control: max-age=86400, public, s-maxage=86400
Age: 0
X-Magento-Cache-Debug: MISS
```

>[!INFO]
>
>Cette valeur est également acceptable : `X-Magento-Cache-Debug: HIT`.

## Vérifier les temps de chargement des pages

Si le vernis fonctionne, toute page Commerce contenant des blocs pouvant être mis en cache doit se charger en moins de 150 ms. Les pages de catégorie de la porte d’entrée et du storefront sont des exemples de ces pages.

Utilisez un inspecteur de navigateur pour mesurer le temps de chargement des pages.

Par exemple, pour utiliser l’Inspecteur Chrome :

1. Accédez à toute page Commerce pouvant être mise en cache dans Chrome.
1. Cliquez avec le bouton droit de la souris n’importe où sur la page.
1. Dans le menu contextuel, cliquez sur **[!UICONTROL Inspect Element]**
1. Dans le volet Inspecteur, cliquez sur l’onglet **[!UICONTROL Network]** .
1. Actualisez la page.
1. Faites défiler l’écran jusqu’en haut du volet d’inspection pour voir l’URL de la page que vous affichez.

   La figure suivante illustre un exemple de chargement de la page d’index `magento2`.

   ![Cliquez sur la page que vous affichez](../../assets/configuration/varnish-inspector.png)

   Le temps de chargement de la page s’affiche en regard de l’URL de la page. Dans ce cas, le temps de chargement est de 5 ms. Cela permet de confirmer que Varnish a mis la page en cache.

1. Pour afficher les en-têtes de réponse HTTP, cliquez sur l’URL de la page (dans la colonne Nom ).

   Vous pouvez afficher les en-têtes HTTP qui sont abordés plus en détail dans la section Vérifier les en-têtes de réponse HTTP .

## Vérification du cache Commerce

Assurez-vous que le répertoire `<magento_root>/var/page_cache` est vide :

1. Connectez-vous à votre serveur Commerce ou basculez vers le propriétaire du système de fichiers.
1. Saisissez la commande suivante :

   ```bash
   rm -rf <magento_root>/var/page_cache/*
   ```

1. Accédez à une ou plusieurs pages Commerce pouvant être mises en cache.
1. Vérifiez le répertoire `var/page_cache/`.

   Si le répertoire est vide, félicitations ! Vous avez correctement configuré Varnish et Commerce pour qu’ils fonctionnent ensemble !

1. Si vous avez effacé le répertoire `var/page_cache/`, redémarrez Varnish.

>[!TIP]
>
>Si vous rencontrez des erreurs 503 (échec de la récupération du serveur principal), reportez-vous à la section [Dépannage des erreurs 503 (service indisponible)](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/troubleshooting-503-errors.html) dans le _Centre d’aide Adobe Commerce_.
