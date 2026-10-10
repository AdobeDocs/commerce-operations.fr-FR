---
title: 'ACSD-46581 : l’estimation du total des taxes n’est pas mise à jour après la sélection d’un pays dans le panier'
description: Appliquez le correctif ACSD-46581 pour résoudre le problème d’Adobe Commerce où le taux de taxe n’est pas mis à jour après avoir changé de pays dans le panier.
feature: Orders, Shopping Cart
role: Admin
exl-id: 45800055-8556-4f87-8938-c6be5d82938d
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: df8eaa0e-dd74-553a-8ad5-28129f8e8d3d
    internal-label: Shopping Cart
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '477'
ht-degree: 0%
---
# ACSD-46581 : l’estimation du total des taxes n’est pas mise à jour après la sélection d’un pays dans le panier

Ce correctif ACSD-46581 résout le problème où le taux de taxe n’est pas mis à jour après avoir changé de pays dans le panier. Elle n’est mise à jour qu’après avoir sélectionné le mode d’expédition. Ce correctif est disponible lorsque la version 1.1.21 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-46581. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.6.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**
* Adobe Commerce (toutes les méthodes de déploiement) 2.4.1-p1

**Compatible avec les versions d’Adobe Commerce :**
* Adobe Commerce (toutes les méthodes de déploiement) 2.4.0 - 2.4.5

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le taux de taxe n’est pas mis à jour après avoir changé de pays dans le panier.

<u>Procédure à suivre </u> :

1. Dans Adobe Commerce Admin, accédez à **[!UICONTROL Stores]** > **[!UICONTROL Tax Zone and Rates]**.
1. Créez un nouveau taux d’imposition pour **[!UICONTROL Country]** = _États-Unis_, **[!UICONTROL State]** = _*_, **[!UICONTROL Rate]** = _8,25_.
1. Créez un nouveau taux d’imposition pour **[!UICONTROL Country]** = _Inde_, **[!UICONTROL State]** = _*_, **[!UICONTROL Rate]** = _10_.
1. Créez une règle fiscale avec les deux taux d&#39;imposition pour les États-Unis et l&#39;Inde.
1. Accédez à **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Shipping Methods]** et activez plusieurs modes d’expédition (_Tarif forfaitaire_ et _Livraison gratuite_ par exemple).
1. Créez un produit simple avec la classe de taxe **[!UICONTROL Taxable Goods]**.
1. Ajoutez le produit au panier en face du magasin.
1. Ouvrez le panier et vérifiez le montant de la taxe.
1. Les paramètres de taxe par défaut pour les États-Unis sont appliqués et la taxe est calculée sur la base d&#39;un taux de 8,25 %.
1. Transférer le pays en Inde.

<u>Résultats attendus</u> :

Le montant de la taxe est passé à 10% lors du changement de pays en Inde.

<u>Résultats réels</u> :

Le montant de la taxe reste le même dans la section totale du panier.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/fr/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
