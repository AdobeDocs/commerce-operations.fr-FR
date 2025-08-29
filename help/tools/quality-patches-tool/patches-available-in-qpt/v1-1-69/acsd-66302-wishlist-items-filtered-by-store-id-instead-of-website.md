---
title: 'ACSD-66302 : éléments de liste de souhaits filtrés par ID de magasin au lieu de site web'
description: Appliquez le correctif ACSD-66302 pour résoudre le problème d’Adobe Commerce où les éléments de liste de souhaits sont filtrés par identifiant de magasin au lieu de sites web dans les demandes  [!DNL GraphQL] .
feature: GraphQL
role: Admin, Developer
type: Troubleshooting
source-git-commit: 7f9a13a9a8cc666c8aa9d964da8aaff01913d35f
workflow-type: tm+mt
source-wordcount: '378'
ht-degree: 0%

---


# ACSD-66302 : éléments de liste de souhaits filtrés par ID de magasin au lieu de site web

Le correctif ACSD-66302 corrige le problème de filtrage des éléments de liste de souhaits par ID de magasin plutôt que par site web dans les requêtes de [!DNL GraphQL]. Ce correctif est disponible lorsque la version 1.1.69 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-66302. Notez que ce problème doit être résolu dans Adobe Commerce 2.4.9.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.8

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.8 - 2.4.8-p1

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les éléments de liste de souhaits sont incorrectement filtrés par ID de boutique plutôt que par site web.

<u>Procédure à suivre </u> :

1. Créez un produit simple.
1. Créez un magasin supplémentaire.
1. Dans Admin, accédez à **[!UICONTROL Stores]** > *[!UICONTROL Settings]* > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Wish List]** > **[!UICONTROL General Options]**, puis définissez **[!UICONTROL Enable Multiple Wish Lists]** sur `Yes`.
1. Accédez à **[!UICONTROL Stores]** > *[!UICONTROL Settings]* > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL Web]** > **[!UICONTROL Url Options]**, puis définissez **[!UICONTROL Add Store Code to Urls]** sur `Yes`.
1. Créez un compte client.
1. Utilisez une requête [!DNL GraphQL] pour récupérer le jeton d’authentification du client.
1. Connectez-vous en tant que client.
1. Sélectionnez le **[!UICONTROL Default Store View]** et ajoutez le produit à la liste de souhaits.
1. Basculez la vue du magasin sur *test*.
1. Vérifiez que le produit apparaît toujours dans la liste de souhaits (comportement correct).
1. Exécutez la requête [!DNL GraphQL] suivante :

```
{
  customer {
    wishlists {
      id
      name
      items_count
      items_v2 {
        items {
          id
          product {
            uid
            name
            sku
          }
        }
      }
    }
  }
}
```

1. Exécutez la requête sur le magasin par défaut. Le produit s’affiche alors comme prévu.
1. Exécutez la même requête sur le magasin de test - le produit n’apparaît pas.

<u>Résultats attendus</u> :

Le produit doit être visible dans toutes les vues de magasin sur le même site web via des requêtes [!DNL GraphQL].

<u>Résultats réels</u> :

Le produit disparaît de la liste de souhaits lors du changement d’affichage de la boutique.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
