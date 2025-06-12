---
title: 'ACSD-48404 : *[!UICONTROL Remember Category Pagination] = [!UICONTROL Yes]* entraîne une erreur lors de l’appui sur le bouton Précédent du navigateur'
description: Appliquez le correctif ACSD-48404 pour résoudre le problème d’Adobe Commerce où *[!UICONTROL Remember Category Pagination] = [!UICONTROL Yes]* provoque une erreur lors de l’appui sur le bouton Précédent du navigateur.
feature: Categories
role: Admin
exl-id: 8c08f0e2-d4f9-4ac8-b8e8-85b4a7de98fb
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '356'
ht-degree: 0%

---

# ACSD-48404 : *[!UICONTROL Remember Category Pagination]=[!UICONTROL Yes]* entraîne une erreur lorsque vous appuyez sur le bouton Précédent du navigateur

Le correctif ACSD-48404 corrige le problème où *[!UICONTROL Remember Category Pagination]=[!UICONTROL Yes]* provoque une erreur lors de l’appui sur le bouton Précédent du navigateur. Ce correctif est disponible lorsque la version 1.1.27 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est ACSD-48404. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3-p3

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.0 - 2.4.3-p3

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

*[!UICONTROL Remember Category Pagination]=[!UICONTROL Yes]* entraîne une erreur lorsque vous appuyez sur le bouton Précédent du navigateur.


<u>Procédure à suivre </u> :

1. Accédez à **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Storefront]**, puis définissez la *[!UICONTROL Remember Category Pagination]* sur *Oui*.
1. Ouvrez une catégorie sur le storefront.
1. Sélectionnez une valeur qui n’est pas la valeur par défaut dans la liste déroulante *[!UICONTROL Show Per Page]* . Après avoir sélectionné une option, la page se recharge.
1. Une fois la page rechargée, cliquez sur un produit de la page du catalogue.
1. Sur la page des détails du produit ouverte, cliquez sur le bouton **[!UICONTROL Back]** du navigateur.

<u>Résultats attendus</u> :

La page de catalogue s’ouvre à nouveau.

<u>Résultats réels</u> :

La page de catégorie renvoie une erreur.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
