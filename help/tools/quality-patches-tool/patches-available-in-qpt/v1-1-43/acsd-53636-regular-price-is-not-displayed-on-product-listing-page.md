---
title: '''ACSD-53636 : Le prix normal n''est pas affiché sur la page [!UICONTROL Product Listing]'''
description: Appliquez le correctif ACSD-53636 pour résoudre le problème Adobe Commerce en raison duquel le prix normal n’est pas affiché sur les *[!UICONTROL Product Listing]* pages pour les produits configurables qui ont des produits enfants avec des prix spéciaux.
feature: Catalog Management, Products
role: Admin, Developer
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '441'
ht-degree: 0%

---

# ACSD-53636 : Le prix normal n&#39;est pas affiché sur la page *[!UICONTROL Product Listing]*

Le correctif ACSD-53636 corrige le problème en raison duquel le prix normal n’est pas affiché sur les pages *[!UICONTROL Product Listing]* pour les produits configurables ayant des produits enfants avec des prix spéciaux. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.43 est installé. L’ID de correctif est ACSD-53636. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3 - 2.4.4-p6

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le prix normal n’est pas affiché sur les pages *[!UICONTROL Product Listing]* pour les produits configurables qui ont des produits enfants avec des prix spéciaux.

<u>Étapes à reproduire</u> :

1. Connectez-vous à l’administrateur et accédez à **[!UICONTROL Admin]** > **[!UICONTROL Catalog]**, puis créez ou ouvrez un produit configurable.
2. Ouvrez le produit enfant, ajoutez un prix spécial à tous les produits enfants ou à l’un d’eux et enregistrez le produit.
3. Accédez à l’interface frontale et ouvrez la page **[!UICONTROL Product Detail]** du produit configurable ; sur les échantillons du produit enfant à prix spécial, vous verrez l’ *[!UICONTROL Regular price]* exclu (prévu).
4. Accédez à l’interface frontale et ouvrez la page **[!UICONTROL Product Listing]** pour le produit configurable à prix spécial. Notez que les modifications d’échantillon de produit configurables n’affichent pas le prix normal contrairement à *[!UICONTROL Product Detail Page]* et à d’autres produits simples.

<u>Résultats attendus</u> :

Sur la page *[!UICONTROL Product Listing]*, le produit configurable indique le prix normal de son produit enfant.

<u>Résultats réels</u> :

Sur la page *[!UICONTROL Product Listing]*, le produit configurable n’affiche pas le prix normal de son produit enfant.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!UICONTROL Quality Patches Tool].


Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].
