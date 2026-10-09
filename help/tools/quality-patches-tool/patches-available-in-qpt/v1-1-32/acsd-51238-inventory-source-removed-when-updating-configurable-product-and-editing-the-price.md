---
title: 'ACSD-51238 : la source de stock est supprimée lors de la mise à jour d''un produit configurable et de la modification du prix'
description: Appliquez le correctif ACSD-51238 pour résoudre le problème d’Adobe Commerce en raison duquel la source d’inventaire est supprimée lors de la mise à jour d’un produit configurable et de la modification du prix.
feature: Configuration, Inventory, Orders, Products
role: Admin
exl-id: 785f012f-e064-4ac6-b559-9e9aa42c679c
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
  - id: 8dc0e58b-adf0-51bb-8db5-bb36e3e656fb
    internal-label: Inventory
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '403'
ht-degree: 0%
---
# ACSD-51238 : la source de stock est supprimée lors de la mise à jour d&#39;un produit configurable et de la modification du prix

Le correctif ACSD-51238 corrige le problème de suppression de la source d&#39;inventaire lors de la mise à jour d&#39;un produit configurable et de la modification du prix. Ce correctif est disponible lorsque la version 1.1.32 de [!DNL Quality Patches Tool (QPT)] est installée. L’ID du correctif est ACSD-51238. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.6

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

L&#39;origine de l&#39;inventaire est supprimée lors de la mise à jour d&#39;un produit configurable et de la modification du prix.

<u>Procédure à suivre </u> :

1. Installer **[!DNL Adobe Commerce]** avec **[!DNL Inventory module]**
1. Accédez à la **[!UICONTROL Admin]** -> **[!UICONTROL Stores]** -> **[!UICONTROL Inventory]** et créez *deux sources* et *deux stocks*.
1. Créez un **[!UICONTROL configurable product]** et affectez-le à **[!UICONTROL default sources]** ou **[!UICONTROL newly created sources]**.
1. Cliquez sur le **[!UICONTROL next button]** et *enregistrez* le produit.
1. Maintenant, modifiez le même **[!UICONTROL Configurable Product]** et cliquez sur **[!UICONTROL Edit Configuration]** dans le **[!UICONTROL Configuration tab]**.
1. Dans `Step 3: Bulk Images,Price and Quantity`, modifiez la `price` et laissez `Quantity` et `Images` sur `Skip quantity at this time` et `Skip image uploading at this time`, respectivement.
1. Cliquez sur **[!UICONTROL next button]** et générez le produit.

<u>Résultats attendus</u>

La quantité par source dans le **[!UICONTROL Configuration tab]** ne doit pas être vide.

<u>Résultats réels</u>

La quantité par source à l&#39;intérieur du **[!UICONTROL Configuration tab]** est vide.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/fr/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
