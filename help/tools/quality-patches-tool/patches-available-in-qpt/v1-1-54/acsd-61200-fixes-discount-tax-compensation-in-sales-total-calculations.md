---
title: "ACSD-61200 : fixe la compensation de la taxe de remise dans les calculs du total des ventes"
description: Appliquez le correctif ACSD-61200 pour résoudre le problème Adobe Commerce en raison duquel *[!UICONTROL Discount Tax Compensation Amount]* et *[!UICONTROL Shipping Discount Tax Compensation Amount]* sont absents des calculs du total des ventes, ce qui entraîne des incohérences entre les données de commande et les données de rapport de coupon.
feature: Reporting, Taxes
role: Admin, Developer
source-git-commit: 61259d8e059cd813a84907e4baef873b2cc8cad0
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 0%

---

# ACSD-61200 : fixe la compensation de la taxe de remise dans les calculs du total des ventes.

Le correctif ACSD-61200 corrige le problème en raison duquel *[!UICONTROL Discount Tax Compensation Amount]* et *[!UICONTROL Shipping Discount Tax Compensation Amount]* ne figurent pas dans les calculs *[!UICONTROL Total Amount]* et *[!UICONTROL Total Amount Actual]*, ce qui entraîne des incohérences entre les données de commande client et les données de rapport de coupon. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.54 est installé. L’ID de correctif est ACSD-61200. Veuillez noter que le problème doit être corrigé dans Adobe Commerce version 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

- Adobe Commerce (toutes les méthodes de déploiement) 2.4.6

**Compatible avec les versions d’Adobe Commerce :**

- Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Inexactitudes dans les données des rapports de commande et de coupon de vente en raison de *[!UICONTROL Discount Tax Compensation Amount]* et *[!UICONTROL Shipping Discount Tax Compensation Amount]* manquants dans les calculs du total des ventes.

<u>Étapes à reproduire</u> :

1. Créez un [!UICONTROL Tax Zone] et un [!UICONTROL Tax Rule].
1. Définissez les configurations de taxe suivantes :
   - **[!UICONTROL Tax Class for Shipping]** = [!UICONTROL Taxable Goods]
   - **[!UICONTROL Catalog Prices]** = [!UICONTROL Including Tax]
   - **[!UICONTROL Shipping Prices]** = [!UICONTROL Including Tax]
   - **[!UICONTROL Apply Discount on Prices]** = [!UICONTROL Including Tax]
   - **[!UICONTROL Display Product Prices in Catalog]** = [!UICONTROL Including Tax]
   - **[!UICONTROL Display Shipping Prices]** = [!UICONTROL Including Tax]
1. Mettez à jour les paramètres d’affichage suivants pour les commandes, les factures et les notes de crédit :
   - **[!UICONTROL Display Prices]** = [!UICONTROL Including Tax]
   - **[!UICONTROL Display Subtotal]**= [!UICONTROL Including Tax]
   - **[!UICONTROL Display Shipping Amount]** = [!UICONTROL Including Tax]
1. Créez un [!UICONTROL Cart Price Rule] avec un coupon pour une remise de 10 %.
1. Effectuez une commande à l&#39;aide du coupon et générez une facture et un envoi.
1. Accédez à **[!UICONTROL Reports]** > **[!UICONTROL Sales]** > **[!UICONTROL Coupons]** et générez un rapport.
1. Comparez les données du résumé de la commande à celles du rapport.

<u>Résultats attendus</u> :

Les calculs *[!UICONTROL Total Amount]* et *[!UICONTROL Total Amount Actual]* comprennent *[!UICONTROL Discount Tax Compensation Amount]* et *[!UICONTROL Shipping Discount Tax Compensation Amount]*, en correspondance du résumé de la commande avec les données du rapport.

<u>Résultats réels</u> :

Les données des rapports de commande commerciale et de coupon ne correspondent pas, car *[!UICONTROL Discount Tax Compensation Amount]* et *[!UICONTROL Shipping Discount Tax Compensation Amount]* ne sont pas pris en compte dans les calculs.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

- Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
- Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

[[!DNL Quality Patches Tool] release : un nouvel outil pour les correctifs de qualité en libre-service](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans le guide Outils.
