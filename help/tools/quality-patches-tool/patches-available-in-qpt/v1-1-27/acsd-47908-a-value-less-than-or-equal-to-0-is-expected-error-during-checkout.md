---
title: 'ACSD-47908 : *Une valeur inférieure ou égale à 0 est attendue* lors de l’extraction'
description: Appliquez le correctif ACSD-47908 pour corriger l’erreur Adobe Commerce *Une valeur inférieure ou égale à 0 est attendue* lors de la sélection de la source et de la quantité à l’étape d’expédition lors du passage en caisse.
feature: Admin Workspace, Checkout, Orders
role: Admin
exl-id: f1429bd9-652d-43c0-af52-b2258e2a7643
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 8cd50456-5eb0-5364-922a-f14161feb828
    internal-label: Checkout
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
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
source-wordcount: '493'
ht-degree: 0%
---
# ACSD-47908 : *Une valeur inférieure ou égale à 0 est attendue* erreur lors de l’extraction

Le correctif ACSD-47908 corrige l’erreur *Une valeur inférieure ou égale à 0 est attendue* lors de la sélection de la source et de la quantité à l’étape d’expédition lors du passage en caisse. Ce correctif est disponible lorsque la version 1.1.27 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-47908. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4-p2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.7 - 2.4.6

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

L’erreur suivante est générée lors de la sélection de l’origine et de la quantité à l’étape d’expédition lors du passage en caisse : *Une valeur inférieure ou égale à 0 est attendue*.

<u>Conditions préalables</u> :

Installez les modules Adobe Commerce Inventory management (MSI).

<u>Procédure à suivre </u> :

1. Accédez à **[!UICONTROL Stores]** > **[!UICONTROL Inventory]** > **[!UICONTROL Sources]** et configurez plusieurs sources.
1. Accédez à **[!UICONTROL Stores]** > **[!UICONTROL Inventory]** > **[!UICONTROL Stock]** et créez un nouveau stock.
   * Affectez maintenant les sources au nouveau stock.
1. Accédez à **[!UICONTROL Catalog]** > **[!UICONTROL Products]** et modifiez au moins un produit.
   * Assurez-vous que les produits sont affectés aux nouvelles sources et spécifiez la quantité disponible.
1. Accédez à **[!UICONTROL Sales]** > **[!UICONTROL Orders]** et créez une commande.
1. Ajoutez ces produits à la commande et passez-les.
1. Cliquez sur **[!UICONTROL Ship]**.
1. Sélectionnez la source à partir de laquelle effectuer l&#39;expédition.
1. Indiquez la quantité de chaque article à expédier.
1. Rechargez la page.
1. Cliquez sur **[!UICONTROL Proceed to Shipment]**.

<u>Résultats attendus</u> :

La nouvelle page d’expédition s’ouvre sans erreur.

<u>Résultats réels</u> :

* La quantité saisie ne peut pas être validée.
* L’erreur suivante est générée : *Veuillez saisir une valeur inférieure ou égale à 0*.

  Toutefois, l’erreur est incohérente et peut ne pas toujours apparaître.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
