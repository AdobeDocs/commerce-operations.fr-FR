---
title: "ACSD-60684: [!DNL GraphQL] le tri des produits par plusieurs champs ne fonctionne pas comme prévu"
description: Appliquez le correctif ACSD-60684 pour résoudre le problème Adobe Commerce en raison duquel le tri des produits par plusieurs champs  [!DNL GraphQL] ne fonctionne pas lorsque le tri est transmis dans les variables.
feature: GraphQL, Products, Search
role: Admin, Developer
source-git-commit: 279036e9e7247ce915820a4b00173644ee7252b1
workflow-type: tm+mt
source-wordcount: '303'
ht-degree: 0%

---

# ACSD-60684 : le tri des produits [!DNL GraphQL] par plusieurs champs ne fonctionne pas comme prévu

Le correctif ACSD-60684 corrige le problème en raison duquel le tri des produits [!DNL GraphQL] par plusieurs champs ne fonctionne pas lorsque le tri est transmis dans les variables. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.52 est installé. L’ID de correctif est ACSD-60684. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6-p6

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6 - 2.4.6-p8

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le tri des produits [!DNL GraphQL] par plusieurs champs ne fonctionne pas comme prévu.

<u>Étapes à reproduire</u> :

1. Créez trois produits portant les noms A, B et C.
1. Récupérez les produits à l’aide des [!DNL GraphQL] suivants :

   ```
   query FindProducts($search: String, $filter:ProductAttributeFilterInput!, $pageSize: Int!, $currentPage: Int!, $sort: ProductAttributeSortInput!){
       products(search: $search, filter: $filter, pageSize: $pageSize, currentPage: $currentPage, sort: $sort){
           total_count
           page_info{total_pages}
           items{
               __typename
               url_key
               sku
               name
               stock_status
               price_range{
                   minimum_price{
                       final_price{
                           value
                           currency
                       }
                   }
               }
           }
       }
   } 
   ```

   Variables :

   ```
   {
       "search": null,
       "filter": {
   
       },
       "pageSize": 24,
       "currentPage": 1,
       "sort": {
           "name": "ASC"
       }
   }  
   ```

1. Répétez la requête avec `sort` : `DESC`

<u>Résultats attendus</u> :

Les résultats sont triés correctement.

<u>Résultats réels</u> :

Le tri sélectionné n&#39;a pas été appliqué.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] : outil en libre-service pour les correctifs de qualité ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils.
