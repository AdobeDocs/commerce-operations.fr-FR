---
title: "ACSD-47803 : échantillons de produits configurables en rupture de stock affichés comme disponibles"
description: Appliquez le correctif ACSD-47803 pour résoudre le problème Adobe Commerce en raison duquel des échantillons de produits configurables en rupture de stock s’affichaient comme disponibles.
feature: Configuration, Orders, Products
role: Admin
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 0%

---

# ACSD-47803 : échantillons de produits configurables en rupture de stock affichés comme disponibles

Le correctif ACSD-47803 corrige le problème en raison duquel les échantillons de produits configurables en rupture de stock s’affichent comme disponibles. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.24 est installé. L’ID de correctif est ACSD-47803. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.6.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les échantillons de produits configurables en rupture de stock s’affichent comme disponibles.

<u>Étapes à reproduire</u> :

>[!NOTE]
>
>Les étapes ci-dessous se réfèrent à des exemples de données comme exemple.

1. Dans l’administrateur [!UICONTROL Commerce], accédez à **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Stock Options]** et définissez **[!UICONTROL Display Out of Stock Products]** sur *Oui*.
1. Encore une fois, depuis l’administrateur, accédez à **[!UICONTROL Catalog]** > **[!UICONTROL Products]** et modifiez un produit configurable dans la page de modification du produit (par exemple, le SKU &quot;WB04&quot;, si vous utilisez des données d’exemple) :
   * Pour une des variantes de configuration, définissez la quantité sur *0* (par exemple, pour &quot;WB04-M-Purple&quot;).
1. Ouvrez maintenant le produit configurable sur le storefront.
1. Sélectionnez la taille du produit pour la variante configurable avec un stock nul (c’est-à-dire &quot;M&quot;).

<u>Résultats attendus</u> :

Les options en rupture de stock sont désactivées et marquées comme [!UICONTROL Out of Stock].

<u>Résultats réels</u> :

Tous les échantillons de couleurs sont activés, même celui qui est [!UICONTROL Out of Stock].

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!UICONTROL Quality Patches Tool].


Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
