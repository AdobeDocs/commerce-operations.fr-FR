---
title: 'ACSD-53309 : Demande de taxe incomplète pour les options personnalisables et le libellé de [!UICONTROL Regular Price]'
description: Appliquez le correctif ACSD-53309 pour résoudre le problème d’Adobe Commerce où la taxe n’est pas entièrement appliquée dans le libellé « [!UICONTROL Regular Price] » lorsqu’une option personnalisable est sélectionnée.
feature: Taxes, Shipping/Delivery
role: Admin, Developer
exl-id: 7f4a8923-11dd-48b2-9d97-77de5c2b24ce
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 0%

---

# ACSD-53309 : demande de taxe incomplète pour les options personnalisables et le libellé « [!UICONTROL Regular Price] »

Le correctif ACSD-53309 corrige le problème où la taxe n&#39;est pas entièrement appliquée dans le libellé « [!UICONTROL Regular Price] » lorsqu&#39;une option personnalisable est sélectionnée. Ce correctif est disponible lorsque la version 1.1.43 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est ACSD-53309. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La taxe n’est pas entièrement reflétée dans le libellé « [!UICONTROL Regular Price] » lorsqu’une option personnalisable est sélectionnée.

<u>Procédure à suivre </u> :

1. Connectez-vous au panneau d’administration.
1. Accédez à **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Tax]** pour configurer les paramètres de taxe.

   * [!UICONTROL Tax Classes] :

      * [!UICONTROL Tax Class for Shipping] = [!UICONTROL Taxable Goods]
      * [!UICONTROL Tax Class for Gift Options] = [!UICONTROL Taxable Goods]

   * [!UICONTROL Calculation Settings] :

      * [!UICONTROL Catalog Prices] = [!UICONTROL Including Tax]
      * [!UICONTROL Shipping Prices] = [!UICONTROL Including Tax]
      * [!UICONTROL Apply Discount On Prices] = [!UICONTROL Including Tax]

   * [!UICONTROL Default Tax Destination Calculation] :

      * [!UICONTROL Default Post Code] = *

   * [!UICONTROL Price Display Settings] :

      * [!UICONTROL Display Product Prices In Catalog] = [!UICONTROL Including Tax]
      * [!UICONTROL Display Shipping Prices] = [!UICONTROL Including Tax]

   * [!UICONTROL Shopping Cart Display Settings] :

      * [!UICONTROL Display Prices] = [!UICONTROL Including Tax]
      * [!UICONTROL Display Subtotal] = [!UICONTROL Including Tax]
      * [!UICONTROL Display Shipping Amount] = [!UICONTROL Including Tax]

1. Définissez **[!UICONTROL Shipping Settings]** > **[!UICONTROL Origin]** > **[!UICONTROL Country]** = *Royaume-Uni*.

1. Créez les *[!UICONTROL Tax Rate]* et *[!UICONTROL Tax Rules]* suivants :

   * [!UICONTROL Country] = États-Unis
   * [!UICONTROL Zip Code] = *
   * [!UICONTROL State] = *
   * [!UICONTROL Rate] = 20 %
1. Créez un produit simple et définissez les éléments suivants :
   * [!UICONTROL Price = 110]
   * [!UICONTROL Special Price = 100]
   * Dans la liste déroulante, définissez le type sur l’option personnalisée avec le prix défini sur 15 %
1. Accédez à la page produit pour l’article simple fabriqué sur le storefront.
1. Sélectionnez l’option personnalisée créée, *15 %*.

<u>Résultats attendus</u> :

* Une taxe de 20 % est appliquée à l’option personnalisée sélectionnée.
* &#39;[!UICONTROL Regular Price]&#39; = 151,80.

<u>Résultats réels</u> :

* La taxe de 20 % n&#39;est pas appliquée à l&#39;option personnalisée sélectionnée.
* &#39;[!UICONTROL Regular Price]&#39; = 148,50.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
