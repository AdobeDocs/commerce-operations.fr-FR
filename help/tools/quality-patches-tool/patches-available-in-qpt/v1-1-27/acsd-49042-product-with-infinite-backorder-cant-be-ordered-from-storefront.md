---
title: 'ACSD-49042 : produit avec arriéré infini ne peut pas être commandé depuis le storefront'
description: Appliquez le correctif ACSD-49042 pour résoudre le problème d’Adobe Commerce en raison duquel un produit avec une commande en souffrance infinie ne peut pas être commandé depuis le storefront.
feature: Admin Workspace, Orders, Products, Storefront
role: Admin
exl-id: b94d06c0-806a-40be-bcd4-d6b8e5e474c3
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
  - id: d1e21356-0064-4f48-9089-16e3f0dbd2a6
    internal-label: Storefront
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
subfeature_v2:
  - id: bb2df8be-afdd-4818-b6b5-95ca1dd3bc3a
    internal-label: Admin workspace
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '444'
ht-degree: 0%
---
# ACSD-49042 : produit avec arriéré infini ne peut pas être commandé depuis le storefront

Le correctif ACSD-49042 corrige le problème où un produit avec une commande infinie ne peut pas être commandé depuis le storefront. Ce correctif est disponible lorsque la version 1.1.27 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-49042. Notez que le problème a été résolu dans Adobe Commerce 2.4.5.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.4-p2

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

L’erreur se produit lorsqu’un produit avec une commande en souffrance infinie ne peut pas être commandé depuis le storefront.

<u>Procédure à suivre </u> :

1. Définissez les paramètres de configuration suivants :
   * **[!UICONTROL Display Out of Stock Products]** défini sur *[!UICONTROL Yes]*.
   * **[!UICONTROL Backorders]** défini sur *[!UICONTROL Allow Qty Below 0]*.
1. Ajoutez une nouvelle **[!DNL custom stock]** et un nouveau **[!DNL custom source]**.
1. Attribuez un produit au **[!DNL custom source]** et assurez-vous qu’un numéro d’inventaire est défini pour lui (par exemple : *10*).
1. Sur la page de modification du produit, ouvrez **[!UICONTROL Advanced Inventory]**. Définissez le **[!UICONTROL minimum quantity]** dans le panier (par exemple : *160*). La quantité doit être supérieure au stock.
1. Allez à la vitrine et achetez un produit pour créer une réservation.
1. Remplacez le **[!UICONTROL product quantity]** par *0*. Le point essentiel est d’enregistrer le produit sur le **[!DNL Admin panel]** en cas de réservation.
1. Ouvrez le **[!UICONTROL product page]** sur le storefront et essayez d’ajouter le produit au panier.

<u>Résultats attendus</u> :

Il est possible d’ajouter le produit au panier, car les reliquats pour une quantité inférieure à *0* sont autorisés.

<u>Résultats réels</u> :

Le produit s’affiche comme étant en rupture de stock.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/fr/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
