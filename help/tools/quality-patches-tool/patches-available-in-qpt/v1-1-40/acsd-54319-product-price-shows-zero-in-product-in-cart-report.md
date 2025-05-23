---
title: 'ACSD-54319 : le prix du produit affiche zéro dans le rapport *[!UICONTROL Products in Carts]*'
description: Appliquez le correctif ACSD-54319 pour résoudre le problème Adobe Commerce où le prix du produit affiche zéro dans le rapport *[!UICONTROL Products in Carts]*.
feature: Reporting, Products
role: Admin, Developer
exl-id: 10052d32-99f8-4b45-9fe9-a4c45bcaaa44
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 0%

---

# ACSD-54319 : le prix du produit affiche zéro dans le rapport *[!UICONTROL Products in Carts]*

Le correctif ACSD-54319 corrige le problème où le prix du produit affiche zéro dans le rapport *[!UICONTROL Products in Carts]*. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.40 est installé. L’ID de correctif est ACSD-54319. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p3

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2 - 2.4.5-p5

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le prix du produit affiche zéro dans le rapport *[!UICONTROL Products in Carts]*.

<u>Étapes à reproduire</u> :

1. Définissez **[!UICONTROL Catalog Price Scope]** sur **[!UICONTROL Website]** à partir de **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog]** > **[!UICONTROL Price]** > **[!UICONTROL Catalog Price Scope]**.
1. Créez un second site web à partir de **[!UICONTROL Stores]** > **[!UICONTROL All Stores]**.
1. Créez un produit à partir de **[!UICONTROL Catalog]** > **[!UICONTROL Products]**.
1. Attribuez ce produit au deuxième site web uniquement.
1. Ajoutez un produit au panier à partir du deuxième site web.
1. Accédez à la grille **[!UICONTROL Admin]** > **[!UICONTROL Reports]** > **[!UICONTROL Marketing]** > **[!UICONTROL Products In Carts]**.
1. Vérifiez la colonne *[!UICONTROL Price]* dans la grille *[!UICONTROL Products In Carts]*.

<u>Résultats attendus</u> :

Le prix du produit n’est pas nul dans la grille de rapports *[!UICONTROL Products in Carts]*.

<u>Résultats réels</u> :

Le prix du produit est zéro dans la grille de rapports *[!UICONTROL Products in Carts]*.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!UICONTROL Quality Patches Tool].


Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
