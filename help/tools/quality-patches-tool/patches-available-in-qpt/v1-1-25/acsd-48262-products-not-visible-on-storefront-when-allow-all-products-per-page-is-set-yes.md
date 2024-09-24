---
title: 'ACSD-48262 : produits non visibles sur le storefront lorsque [!UICONTROL Allow All Products Per Page] est défini [!UICONTROL Yes]'
description: Appliquez le correctif ACSD-48262 pour résoudre le problème Adobe Commerce où les produits ne sont pas visibles sur le storefront lorsque le paramètre [!UICONTROL Allow All Products Per Page] est défini sur [!UICONTROL Yes].
feature: Admin Workspace, Cache, Categories, Orders, Products, Storefront
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '364'
ht-degree: 0%

---

# ACSD-48262 : produits non visibles sur le storefront lorsque [!UICONTROL Allow All Products Per Page] est défini *[!UICONTROL Yes]*

Le correctif ACSD-48262 corrige le problème en raison duquel les produits ne sont pas visibles sur le storefront lorsque le paramètre [!UICONTROL Allow All Products Per Page] est défini sur *[!UICONTROL Yes]*. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.25 est installé. L’ID de correctif est ACSD-48262. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.6.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) >=2.4.5 &lt; 2.4.6

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le correctif ACSD-48262 corrige le problème en raison duquel les produits ne sont pas visibles sur le storefront lorsque le paramètre [!UICONTROL Allow All Products Per Page] est défini sur *[!UICONTROL Yes]*.

<u>Étapes à reproduire</u> :

1. Créez une catégorie de test.
1. Créez un produit test dans la catégorie test.
1. Parcourez la page de catégorie du produit à tester sur le storefront et assurez-vous que le produit est visible.
1. Accédez à **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** et définissez le paramètre [!UICONTROL Allow All Products Per Page] sur *[!UICONTROL Yes]*.
1. Effacez le cache.
1. Vérifiez la page de catégorie sur le storefront.

<u>Résultats attendus</u> :

Le produit est visible.

<u>Résultats réels</u> :

Le produit n’est pas visible.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.


## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!UICONTROL Quality Patches Tool].


Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].
