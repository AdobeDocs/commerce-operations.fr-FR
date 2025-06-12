---
title: 'ACSD-45817 : la mutation des produits GraphQL donne toutes les variantes configurables'
description: Le correctif ACSD-45817 corrige le problème où une mutation GraphQL « products » pour un magasin spécifique renvoie toutes les variantes configurables, y compris celles qui ne sont pas affectées au magasin demandé. Ce correctif est disponible lorsque l’outil [Outil de correctifs de la qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.18 est installé. L’ID du correctif est ACSD-45817. Notez que le problème a été résolu dans Adobe Commerce 2.4.4.
feature: GraphQL, Configuration, Products
role: Admin
exl-id: f00e9a8e-c18b-4fa8-b7c6-c228b6a22a2c
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '454'
ht-degree: 0%

---

# ACSD-45817 : la mutation des produits GraphQL donne toutes les variantes configurables

Le correctif ACSD-45817 corrige le problème où une mutation de `products` GraphQL pour un magasin spécifique renvoie toutes les variantes configurables, y compris celles qui ne sont pas affectées au magasin demandé. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) version 1.1.18 est installé. L’ID du correctif est ACSD-45817. Notez que le problème a été résolu dans Adobe Commerce 2.4.4.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2 - 2.4.3-p3

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Une mutation de `products` GraphQL pour un magasin spécifique renvoie toutes les variantes configurables, y compris celles qui ne sont pas affectées au magasin demandé.

<u>Conditions préalables</u> :

Créez un deuxième site web, un deuxième magasin et une deuxième vue de magasin.

<u>Procédure à suivre </u> :

1. Créez un produit configurable avec deux sous-produits : « configurable-a » et « configurable-b ».
1. Attribuez le produit configurable aux deux sites web.
1. Attribuez une seule variation « configurable-a » au deuxième site web.
1. Accédez au **Storefront**, passez au 2e site web et ouvrez le produit configurable.
1. Assurez-vous de ne voir qu’une seule option enfant : « configurable-a ».
1. Exécutez une requête GraphQL à l’aide `POST: /graphql` point d’entrée et `Headers: "store" = "new"`

   ```GraphQL
   {
     products(filter: { sku: { eq: "configurable" } }) {
       items {
         id
         attribute_set_id
         name
         sku
         __typename
         price_range{
           minimum_price{
             regular_price{
               value
               currency
             }
           }
         }
         categories {
           id
         }
         ... on ConfigurableProduct {
           configurable_options {
             id
             attribute_id_v2
             label
             position
             use_default
             attribute_code
             values {
               value_index
               label
             }
             product_id
           }
           variants {
             product {
               id
               name
               sku
               attribute_set_id
               ... on PhysicalProductInterface {
                 weight
               }
               price_range{
                 minimum_price{
                   regular_price{
                     value
                     currency
                   }
                 }
               }
             }
             attributes {
               uid
               label
               code
               value_index
             }
           }
         }
       }
     }
   }
   ```

<u>Résultats attendus</u> :

La variation « configurable-b » n’est pas affectée au deuxième site web et ne doit pas être affichée dans la réponse.

<u>Résultats réels</u> :

La variation « configurable-b » s’affiche dans la réponse.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur l’outil de correctifs de la qualité, voir :

* Publication de l’outil [Correctifs de qualité](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) un nouvel outil permettant d’appliquer des correctifs de qualité en libre-service dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!DNL Quality Patches Tool].

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
