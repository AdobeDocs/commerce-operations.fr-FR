---
title: "ACSD-61195 : la demande GraphQL de panier ne parvient pas à renvoyer les éléments sur la dernière page"
description: Appliquez le correctif ACSD-61195 pour résoudre le problème Adobe Commerce en raison duquel aucun élément de panier n’est renvoyé sur la dernière page pour la demande GraphQL de panier.
feature: GraphQL
role: Admin, Developer
source-git-commit: f6e410e0787e56717b3910b7f3938108a7af9cd8
workflow-type: tm+mt
source-wordcount: '328'
ht-degree: 0%

---

# ACSD-61195 : la demande GraphQL de panier ne parvient pas à renvoyer les éléments sur la dernière page

Le correctif ACSD-61195 corrige le problème lorsqu’aucun élément de panier n’est renvoyé sur la dernière page pour la demande GraphQL de panier. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 1.1.51 est installé. L’ID de correctif est ACSD-61195. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.7-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.7-p1 - 2.4.7-p2

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La demande GraphQL de panier ne parvient pas à renvoyer les éléments sur la dernière page.

<u>Étapes à reproduire</u> :

1. Créez un panier :

   ```
   mutation createEmptyCart($input: createEmptyCartInput) {
       createEmptyCart(input: $input)
   } 
   ```

1. Ajoutez plus de cinq produits au panier :

   ```
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

   ```
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

```
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

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!UICONTROL Quality Patches Tool].


Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].
