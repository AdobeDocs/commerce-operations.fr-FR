---
title: 'ACSD-47444 : erreur _[!UICONTROL Trying to access array offset on value of type bool]_ lors de l’accès à certains chemins de catégorie non existants pour les produits connus sur PHP 7.4'
description: Appliquez le patch ACSD-47444 pour corriger le problème d'Adobe Commerce où il y a une erreur _[!UICONTROL Trying to access array offset on value of type bool]_ lors de l'accès à certains chemins de catégories non existants pour les produits connus, sur PHP 7.4.
feature: Categories, Products
role: Admin
exl-id: 9f04ee28-d22c-4fdf-9228-e436abe973e8
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '334'
ht-degree: 0%

---

# ACSD-47444 : erreur _[!UICONTROL Trying to access array offset on value of type bool]_&#x200B;lors de l&#39;accès à certains chemins de catégorie non existants pour les produits connus sur PHP 7.4

Le patch ACSD-47444 résout le problème où vous voyez _[!UICONTROL Trying to access array offset on value of type bool]_&#x200B;erreur lors de l&#39;accès à certains chemins de catégorie non existants pour les produits connus sur PHP 7.4. Ce correctif est disponible lorsque la version 1.1.22 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**
* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2-p1

**Compatible avec les versions d’Adobe Commerce :**
* Adobe Commerce (toutes les méthodes de déploiement) 2.4.0 - 2.4.2-p2

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Vous rencontrez l&#39;erreur suivante : _[!UICONTROL Trying to access array offset on value of type bool]_&#x200B;lors de l&#39;accès à certains chemins de catégories non existants pour des produits connus, sur PHP 7.4.

<u>Conditions préalables</u> :

PHP 7.4.

<u>Procédure à suivre </u> :

1. Créez un produit nommé « test ».
1. Accédez à **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL CATALOG]** > **[!UICONTROL Catalog]** > **[!UICONTROL Search Engine Optimization]** > définir **[!UICONTROL Generate "category/product" URL Rewrites]** = _Non_.
1. Accédez au storefront et visitez l’URL telle que ../abc/test.html (« abc » - ne doit pas exister).

<u>Résultats attendus</u> :

Page 404.

<u>Résultats réels</u> :

Erreur 500 :

_[!UICONTROL Notice: Trying to access array offset on value of type bool in /app/code/Magento/CatalogUrlRewrite/Model/Storage/DynamicStorage.php on line 182]_

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans notre documentation destinée aux développeurs et développeuses.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
