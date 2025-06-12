---
title: 'ACSD-54319 : le prix du produit affiche zéro dans le rapport *[!UICONTROL Products in Carts]*'
description: Appliquez le correctif ACSD-54319 pour résoudre le problème Adobe Commerce où le prix du produit affiche zéro dans le rapport *[!UICONTROL Products in Carts]*
feature: Reporting, Products
role: Admin, Developer
exl-id: 10052d32-99f8-4b45-9fe9-a4c45bcaaa44
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 0%

---

# ACSD-54319 : le prix du produit affiche zéro dans *[!UICONTROL Products in Carts]* rapport

Le correctif ACSD-54319 corrige le problème en raison duquel le prix du produit affiche zéro dans *[!UICONTROL Products in Carts]* rapport. Ce correctif est disponible lorsque la version 1.1.40 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est ACSD-54319. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p3

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2 - 2.4.5-p5

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le prix du produit affiche zéro dans *[!UICONTROL Products in Carts]* rapport.

<u>Procédure à suivre </u> :

1. Définissez **[!UICONTROL Catalog Price Scope]** sur **[!UICONTROL Website]** depuis **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog]** > **[!UICONTROL Price]** > **[!UICONTROL Catalog Price Scope]**.
1. Créez un second site web à partir de **[!UICONTROL Stores]** > **[!UICONTROL All Stores]**.
1. Créez un produit à partir de **[!UICONTROL Catalog]** > **[!UICONTROL Products]**.
1. Affectez ce produit au deuxième site web uniquement.
1. Ajoutez un produit au panier à partir du deuxième site web.
1. Accédez à **[!UICONTROL Admin]** > **[!UICONTROL Reports]** > **[!UICONTROL Marketing]** > grille **[!UICONTROL Products In Carts]**.
1. Vérifiez la colonne *[!UICONTROL Price]* dans *[!UICONTROL Products In Carts]* grille.

<u>Résultats attendus</u> :

Le prix du produit n&#39;est pas nul dans *[!UICONTROL Products in Carts]* grille de rapports.

<u>Résultats réels</u> :

Le prix du produit est nul dans *[!UICONTROL Products in Carts]* grille de rapports.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
