---
title: 'ACSD-60684 : le tri des produits [!DNL GraphQL] par plusieurs champs ne fonctionne pas comme prévu'
description: Appliquez le correctif ACSD-60684 pour résoudre le problème d’Adobe Commerce en raison duquel [!DNL GraphQL] tri du produit par plusieurs champs ne fonctionne pas lorsque le tri est transmis dans des variables.
feature: GraphQL, Products, Search
role: Admin, Developer
exl-id: 1c29299b-c85f-4166-886b-357a1486e67e
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
  - id: c32adafa-ed01-4b31-997e-2413013911b0
    internal-label: Integrations
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
subfeature_v2:
  - id: e396cff5-f586-484c-89f0-7f1da3308f92
    internal-label: GraphQL
  - id: a1d22079-48b9-5e69-9ee6-eb236068ef34
    internal-label: Search
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
source-wordcount: '322'
ht-degree: 0%
---
# ACSD-60684 : le tri des produits [!DNL GraphQL] par plusieurs champs ne fonctionne pas comme prévu

Le correctif ACSD-60684 corrige le problème en raison duquel [!DNL GraphQL] tri du produit par plusieurs champs ne fonctionne pas lorsque le tri est transmis dans des variables. Ce correctif est disponible lorsque la version 1.1.52 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-60684. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6-p6

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6 - 2.4.6-p8

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le tri des produits [!DNL GraphQL] par plusieurs champs ne fonctionne pas comme prévu.

<u>Procédure à suivre </u> :

1. Créez trois produits portant les noms A, B et C.
1. Récupérez les produits à l’aide des [!DNL GraphQL] suivantes :

   ```graphql
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

   ```json
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

Les résultats sont triés de manière appropriée.

<u>Résultats réels</u> :

Le tri sélectionné n&#39;a pas été appliqué.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/fr/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
