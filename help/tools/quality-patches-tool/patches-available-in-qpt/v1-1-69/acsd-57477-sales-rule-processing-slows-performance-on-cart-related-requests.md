---
title: 'ACSD-57477 : le traitement des règles de vente ralentit les performances des requêtes liées au panier'
description: Appliquez le correctif ACSD-57477 pour résoudre le problème d’Adobe Commerce où, dans un projet avec de nombreux attributs de produit disponibles (par exemple, 1 000 attributs), lorsque l’opération AddProductsToCart GraphQL est exécutée avec des variables, Commerce tente de charger tous ces attributs de produit et entraîne des problèmes de performances lentes à partir de l’opération AddProductsToCart GraphQL.
feature: GraphQL, Shopping Cart
role: Admin, Developer
type: Troubleshooting
source-git-commit: 00fce49fbe5432a16324937e0430a08ec7c41188
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 0%

---


# ACSD-57477 : le traitement des règles de vente ralentit les performances des requêtes liées au panier

Le correctif ACSD-57477 corrige le problème en raison duquel le traitement des règles de vente ralentit les performances des requêtes liées au panier. Ce correctif est disponible lorsque la version 1.1.69 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-57477. Notez que ce problème doit être résolu dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6-p2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6 - 2.4.6-p11

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le traitement des règles de vente ralentit les performances des requêtes liées au panier si vous envoyez les paramètres sous forme de variables GraphQL.

<u>Procédure à suivre </u> :

1. Ajoutez 1 000 attributs de produit.
1. Créez un panier à l’aide de la requête GraphQL ci-dessous.

   ```
   mutation {createEmptyCart}{noformat}
   ```

1. Ajoutez un produit au panier à l’aide de la requête GraphQL ci-dessous.

   ```
   mutation AddProductsToCart($cartId: String!, $products: [CartItemInput!]!) {
       addProductsToCart(cartId: $cartId, cartItems: $products) {
         cart {
           id
           __typename
         }
         __typename
       }
     }
   ```

1. Définissez ces variables.

   ```
   {
     "cartId": "id_here",
     "products": [
       {
         "sku": "product_dynamic_1",
         "parent_sku": "product_dynamic_1",
         "quantity": 1
       }
     ]
   }
   ```

1. Ce problème se produit uniquement lorsque vous envoyez les paramètres sous forme de variables GraphQL. Si vous incluez les paramètres dans la requête GraphQL elle-même, ce problème ne se produit pas.
1. Envoyez la même requête **Ajouter au panier** après l’ajout de paramètres dans la requête GraphQL elle-même.

   ```
   mutation {
    addProductsToCart(
      cartId: "id_here"
      cartItems:  [
       {
         sku: "product_dynamic_1",
         parent_sku: "product_dynamic_1",
         quantity: 1
       }
     ]
    ) {
      cart {
           id
           __typename
         }
         __typename
    }
   }
   ```

<u>Résultats attendus</u> :

Les performances de l’opération GraphQL `AddProductsToCart` ne doivent pas être dégradées.

<u>Résultats réels</u> :

Les performances de l’opération GraphQL `AddProductsToCart` se dégradent, car elle charge tous les attributs de produit lorsque les paramètres sont envoyés en tant que variables.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool]
* Adobe Commerce sur les infrastructures cloud : [ Mises à niveau et correctifs > Appliquer des correctifs ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
