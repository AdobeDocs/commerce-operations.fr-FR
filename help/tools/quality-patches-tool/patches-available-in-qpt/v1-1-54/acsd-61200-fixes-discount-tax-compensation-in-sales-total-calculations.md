---
title: 'ACSD-61200 : fixe la compensation de taxe de remise dans les calculs de total des ventes'
description: Appliquez le correctif ACSD-61200 pour résoudre le problème d'Adobe Commerce où *[!UICONTROL Discount Tax Compensation Amount]* et *[!UICONTROL Shipping Discount Tax Compensation Amount]* sont absents des calculs de total des ventes, ce qui entraîne des incohérences entre les données des commandes client et les données des rapports sur les coupons.
feature: Reporting, Taxes
role: Admin, Developer
exl-id: eb908827-de29-4b2c-b094-b5db0931cd52
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 0%

---

# ACSD-61200 : fixe la compensation de taxe de remise dans les calculs de total des ventes

Le correctif ACSD-61200 corrige le problème où les *[!UICONTROL Discount Tax Compensation Amount]* et les *[!UICONTROL Shipping Discount Tax Compensation Amount]* sont absents des calculs de *[!UICONTROL Total Amount]* et de *[!UICONTROL Total Amount Actual]*, ce qui entraîne des incohérences entre les données des commandes client et les données des rapports sur les coupons. Ce correctif est disponible lorsque la version 1.1.54 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-61200. Notez que le problème est planifié pour être corrigé dans la version 2.4.8 d’Adobe Commerce.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

- Adobe Commerce (toutes les méthodes de déploiement) 2.4.6

**Compatible avec les versions d’Adobe Commerce :**

- Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Inexactitude des données de l&#39;état des commandes client et des coupons en raison de *[!UICONTROL Discount Tax Compensation Amount]* et de *[!UICONTROL Shipping Discount Tax Compensation Amount]* manquants dans les calculs du total des ventes.

<u>Procédure à suivre </u> :

1. Créez un [!UICONTROL Tax Zone] et un [!UICONTROL Tax Rule].
1. Définissez les configurations de taxe suivantes :
   - **[!UICONTROL Tax Class for Shipping]** = [!UICONTROL Taxable Goods]
   - **[!UICONTROL Catalog Prices]** = [!UICONTROL Including Tax]
   - **[!UICONTROL Shipping Prices]** = [!UICONTROL Including Tax]
   - **[!UICONTROL Apply Discount on Prices]** = [!UICONTROL Including Tax]
   - **[!UICONTROL Display Product Prices in Catalog]** = [!UICONTROL Including Tax]
   - **[!UICONTROL Display Shipping Prices]** = [!UICONTROL Including Tax]
1. Mettez à jour les paramètres d&#39;affichage suivants pour les commandes, les factures et les avoirs :
   - **[!UICONTROL Display Prices]** = [!UICONTROL Including Tax]
   - **[!UICONTROL Display Subtotal]**= [!UICONTROL Including Tax]
   - **[!UICONTROL Display Shipping Amount]** = [!UICONTROL Including Tax]
1. Créez un [!UICONTROL Cart Price Rule] avec un coupon pour une remise de 10 %.
1. Terminez une commande à l’aide du bon et générez une facture et une expédition.
1. Accédez à **[!UICONTROL Reports]** > **[!UICONTROL Sales]** > **[!UICONTROL Coupons]** et générez un rapport.
1. Comparez les données de la synthèse des commandes à celles du rapport.

<u>Résultats attendus</u> :

Les calculs de *[!UICONTROL Total Amount]* et de *[!UICONTROL Total Amount Actual]* comprennent les *[!UICONTROL Discount Tax Compensation Amount]* et les *[!UICONTROL Shipping Discount Tax Compensation Amount]*, et font correspondre la synthèse des commandes avec les données du rapport.

<u>Résultats réels</u> :

Les données de commande client et de rapport de coupon ne correspondent pas, car les *[!UICONTROL Discount Tax Compensation Amount]* et les *[!UICONTROL Shipping Discount Tax Compensation Amount]* sont absents des calculs.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

- Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
- Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

[[!DNL Quality Patches Tool] sortie : un nouvel outil permettant d’appliquer des correctifs de qualité en libre-service](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans le guide Outils .
