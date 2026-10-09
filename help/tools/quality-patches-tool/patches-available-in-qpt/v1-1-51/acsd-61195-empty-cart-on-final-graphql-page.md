---
title: 'ACSD-61195 : la requête GraphQL du panier ne parvient pas à renvoyer les éléments sur la page finale'
description: Appliquez le correctif ACSD-61195 pour résoudre le problème d’Adobe Commerce en raison duquel aucun article de panier n’est renvoyé sur la dernière page pour la requête de GraphQL de panier.
feature: GraphQL
role: Admin, Developer
exl-id: 15f0f29c-8517-4f1e-9370-772572e75c9a
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: c32adafa-ed01-4b31-997e-2413013911b0
    internal-label: Integrations
subfeature_v2:
  - id: e396cff5-f586-484c-89f0-7f1da3308f92
    internal-label: GraphQL
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 0%
---
# ACSD-61195 : la requête GraphQL du panier ne parvient pas à renvoyer les éléments sur la page finale

Le correctif ACSD-61195 corrige le problème en raison duquel aucun article de panier n’est renvoyé sur la dernière page pour la requête de GraphQL de panier. Ce correctif est disponible lorsque la version 1.1.51 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=fr) est installée. L’ID du correctif est ACSD-61195. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.7-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.7-p1 - 2.4.7-p2

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La requête GraphQL du panier ne parvient pas à renvoyer des éléments sur la page finale.

<u>Procédure à suivre </u> :

1. Créez un panier :

   ```graphql
   mutation createEmptyCart($input: createEmptyCartInput) {
       createEmptyCart(input: $input)
   } 
   ```

1. Ajoutez plus de cinq produits au panier :

   ```text
   addProductsToCart(
       cartId: "{{cartId}}"
       cartItems: [
         {
           quantity: 1
           sku: "test"
         }
       ]
     ) {
       cart {
          itemsV2 {
          items {
           product {
            name
            sku
           }
           quantity
       }
       total_count
       page_info {
         page_size
         current_page
         total_pages
       }
     }
   }
   user_errors {
     code
     message
   }
   }
   }
   ```

1. Exécutez la requête suivante :

   ```text
   cart(cart_id: $cartId) {
   email
   itemsV2(pageSize: 2, currentPage: 3) {
       total_count
       page_info {
          page_size
          current_page
          total_pages
       }
     items {
       id
       product {
         name
         sku
       }
       quantity
       }
   }
   }  
   ```

<u>Résultats attendus</u> :

La requête renvoie les éléments de la dernière page.

<u>Résultats réels</u> :

```json
  {
    "data": {
        "cart": {
            "email": "roni_cost@example.com",
            "itemsV2": {
                "total_count": 5,
                "page_info": {
                    "page_size": 2,
                    "current_page": 3,
                    "total_pages": 3
                },
                "items": []
            }
        }
    } 
    }  
```

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/fr/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
