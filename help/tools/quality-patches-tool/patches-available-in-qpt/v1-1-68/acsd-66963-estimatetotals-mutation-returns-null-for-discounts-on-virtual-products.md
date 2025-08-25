---
title: 'ACSD-66963 : la mutation « estimateTotals » renvoie la valeur null pour les remises sur les produits virtuels'
description: Appliquez le correctif ACSD-66963 pour résoudre le problème d’Adobe Commerce où « estimateTotals » renvoie *null* pour les remises lorsqu’un code de remise est appliqué à un panier avec uniquement des produits virtuels.
feature: GraphQL
role: Admin, Developer
type: Troubleshooting
source-git-commit: 0eede09026df98426cd3b6b1550be274c26d7e13
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 0%

---


# ACSD-66963 : la mutation `estimateTotals` renvoie la valeur null pour les remises sur les produits virtuels

Le correctif ACSD-66963 corrige le problème où `estimateTotals` renvoie *null* pour les remises lorsqu’un code de remise est appliqué à un panier avec uniquement des produits virtuels. Ce correctif est disponible lorsque la version 1.1.68 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-66963. Ce problème a été résolu dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.7-p4

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.7 - 2.4.7-p6

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La mutation `estimateTotals` renvoie la valeur *null* pour les remises lorsqu’un code de remise est appliqué à un panier contenant uniquement des produits virtuels.

<u>Procédure à suivre </u> :

1. Créez un panier contenant uniquement des produits virtuels.
1. Appliquer un code remise :

   ```
   mutation {
     estimateTotals(
       input: {
         cart_id: "cart_id",
         address: {
           country_code: US,
           postcode: "78732",
           region: {
             region_code: "TX"
           }
         },
         shipping_method: {
           carrier_code: "{$shipping}",
           method_code: "{$shipping}"
         }
       }
     ) {
       cart {
         prices {
           discounts {
             amount {
               value
               currency
             }
             label
             coupon {
               code
             }
             applied_to
             type
           }
         }
       }
     }
   }
   ```

<u>Résultats attendus</u> :

Les informations de remise sont incluses pour les paniers contenant uniquement des produits virtuels.

     »
    &lbrace;
    « data »: &lbrace;
    « estimateTotals »: &lbrace;
    « cart »: &lbrace;
    « prices »: &lbrace;
    « remises »: &lbrack;
    &lbrace;
    « amount »: &lbrace;
    « value »: 100.5,
    « currency »: « USD »
    &rbrace;,
    « label »: « Un second code de remise pour le test »,
    « coupon »: &lbrace;
    « code »: « z3r0c00l »
    &rbrace;,
    « applied_to »: « ITEM »,
    « type »: null
    &rbrace;
    &rbrack;
    &rbrace;
    &rbrace;,
    « extensions »: 
    &rbrace;
    «{}
     
     

<u>Résultats réels</u> :

Les informations de remise sont renvoyées comme *nulles* pour les paniers contenant uniquement des produits virtuels.

     »
    &lbrace;
    « data »: &lbrace;
    « estimateTotals »: &lbrace;
    « cart »: &lbrace;
    « prices »: &lbrace;
    « remises »: null
    &rbrace;
    &rbrace;
    &rbrace;
    &rbrace;,
    « extensions »: {}
    &rbrace;
     »
 »

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
