---
title: 'ACSD-47444 : _[!UICONTROL Trying to access array offset on value of type bool]_ erreur lors de l’accès à certains chemins de catégorie non existants pour des produits connus sur PHP 7.4'
description: Appliquez le correctif ACSD-47444 pour résoudre le problème Adobe Commerce en raison duquel une erreur _[!UICONTROL Trying to access array offset on value of type bool]_ s’est produite lors de l’accès à certains chemins de catégorie non existants pour des produits connus, sous PHP 7.4.
feature: Categories, Products
role: Admin
exl-id: 9f04ee28-d22c-4fdf-9228-e436abe973e8
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '334'
ht-degree: 0%

---

# ACSD-47444 : _[!UICONTROL Trying to access array offset on value of type bool]_erreur lors de l&#39;accès à certains chemins de catégorie non existants pour les produits connus sous PHP 7.4

Le correctif ACSD-4744 résout le problème d’erreur _[!UICONTROL Trying to access array offset on value of type bool]_lors de l’accès à certains chemins de catégorie non existants pour les produits connus sur PHP 7.4. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.22 est installé.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**
* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2-p1

**Compatible avec les versions d’Adobe Commerce :**
* Adobe Commerce (toutes les méthodes de déploiement) 2.4.0 - 2.4.2-p2

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

L’erreur suivante se produit : _[!UICONTROL Trying to access array offset on value of type bool]_lors de l’accès à certains chemins de catégorie non existants pour des produits connus, sous PHP 7.4.

<u>Conditions préalables</u> :

PHP 7.4.

<u>Étapes à reproduire</u> :

1. Créez un produit, nommé &quot;test&quot;.
1. Accédez à **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL CATALOG]** > **[!UICONTROL Catalog]** > **[!UICONTROL Search Engine Optimization]** > set **[!UICONTROL Generate "category/product" URL Rewrites]** = _No_.
1. Accédez au storefront et à l’URL comme ../abc/test.html (&quot;abc&quot; - ne doit pas exister).

<u>Résultats attendus</u> :

404 page.

<u>Résultats réels</u> :

Erreur 500 :

_[!UICONTROL Notice: Trying to access array offset on value of type bool in /app/code/Magento/CatalogUrlRewrite/Model/Storage/DynamicStorage.php on line 182]_

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!UICONTROL Quality Patches Tool].


Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].
