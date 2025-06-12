---
title: 'ACSD-53636 : le prix normal n''est pas affiché sur [!UICONTROL Product Listing] page'
description: Appliquez le correctif ACSD-53636 pour résoudre le problème d’Adobe Commerce où le prix normal n’est pas affiché sur les pages *[!UICONTROL Product Listing]* pour les produits configurables qui ont des produits enfants avec des prix spéciaux.
feature: Catalog Management, Products
role: Admin, Developer
exl-id: e6d66ae4-2c21-466a-b03c-a1f486e7fa29
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '441'
ht-degree: 0%

---

# ACSD-53636 : le prix normal n&#39;est pas affiché sur *[!UICONTROL Product Listing]* page

Le correctif ACSD-53636 corrige le problème où le prix normal n&#39;est pas affiché sur les pages *[!UICONTROL Product Listing]* pour les produits configurables qui ont des produits enfants avec des prix spéciaux. Ce correctif est disponible lorsque la version 1.1.43 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est ACSD-53636. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3 - 2.4.4-p6

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le prix normal ne s’affiche pas sur les pages *[!UICONTROL Product Listing]* pour les produits configurables qui ont des produits enfants avec des prix spéciaux.

<u>Procédure à suivre </u> :

1. Connectez-vous en tant qu’administrateur, accédez à **[!UICONTROL Admin]** > **[!UICONTROL Catalog]**, puis créez ou ouvrez tout produit configurable.
2. Ouvrez le produit enfant et ajoutez un prix spécial à l&#39;ensemble ou à l&#39;un des produits enfants et enregistrez le produit.
3. Accédez à l’interface utilisateur et ouvrez la page **[!UICONTROL Product Detail]** du produit configurable. Sur les échantillons du produit enfant au prix spécial, le *[!UICONTROL Regular price]* est barré (prévu).
4. Accédez au serveur frontal et ouvrez la page **[!UICONTROL Product Listing]** pour le produit configurable avec un prix spécial. Veillez à ce que les modifications de l’échantillon de produit configurable n’affichent pas le prix normal, contrairement au *[!UICONTROL Product Detail Page]* et aux autres produits simples.

<u>Résultats attendus</u> :

Sur la page *[!UICONTROL Product Listing]*, le produit configurable affiche le prix normal de son produit enfant.

<u>Résultats réels</u> :

Sur la page *[!UICONTROL Product Listing]*, le produit configurable n’affiche pas le prix normal de son produit enfant.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
