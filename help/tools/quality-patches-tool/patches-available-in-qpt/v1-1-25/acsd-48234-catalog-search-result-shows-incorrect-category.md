---
title: 'ACSD-48234 : le nombre d’éléments de catégorie du résultat de la recherche catalogue est incorrect lorsqu’[!UICONTROL Display Out of Stock Products] est activé'
description: Appliquez le correctif ACSD-48234 pour résoudre le problème d’Adobe Commerce où le résultat de la recherche catalogue affiche un nombre d’éléments de catégorie incorrect lorsque l’option [!UICONTROL Display Out of Stock Products] est activée.
feature: Admin Workspace, Categories, Catalog Management, Orders, Products, Search
role: Admin
exl-id: c177f12d-2db5-48e2-8f88-ff589cea4dd4
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 0%

---

# ACSD-48234 : le résultat de la recherche catalogue affiche un nombre d’éléments de catégorie incorrect **[!UICONTROL Display Out of Stock Products]** activé

Le correctif ACSD-48234 résout le problème où le résultat de la recherche catalogue affiche un nombre d’éléments de catégorie incorrect lorsque l’option **[!UICONTROL Display Out of Stock Products]** est activée. Ce correctif est disponible lorsque la version 1.1.25 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est ACSD-48234. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.6.


## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**
* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p1

**Compatible avec les versions d’Adobe Commerce :**
* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5 - 2.4.5-p4

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le résultat de la recherche catalogue affiche un nombre d’éléments de catégorie incorrect lorsque l’option **[!UICONTROL Display Out of Stock Products]** est activée.

<u>Procédure à suivre </u> :

1. Accédez à **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Product]** et ouvrez l’attribut **[!UICONTROL color]** .
1. Ajoutez deux options, par exemple orange et vert. Enregistrez l’attribut.
1. Accédez à **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Attribute Set]** et ajoutez l’attribut **[!UICONTROL color]** au jeu d’attributs **[!UICONTROL Default]**.
1. Accédez à **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL CATALOG]** > **[!UICONTROL Inventory]** > **[!UICONTROL Stock Options]** et définissez **[!UICONTROL Display Out of Stock Products]** sur _Oui_.
1. Créez la catégorie « cat1 ».
1. Créez deux produits :
   1. Nom : prod1, Couleur : orange, Catégories : cat1.
   1. Nom : prod2, Couleur : vert, Catégories : cat1.
1. Ouvrez la catégorie cat1 sur le storefront.
1. Sélectionnez la couleur orange au niveau de la navigation superposée.

<u>Résultats attendus</u> :

Seul le produit prod1 s&#39;affiche.

<u>Résultats réels</u> :

Les produits prod1 et prod2 sont affichés.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
