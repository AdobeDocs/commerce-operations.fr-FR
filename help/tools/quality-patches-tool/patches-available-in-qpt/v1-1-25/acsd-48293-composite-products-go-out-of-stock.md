---
title: 'ACSD-48293 : produits composites en rupture de stock en cas de rupture de stock de produits enfants réapprovisionnés'
description: Appliquez le correctif ACSD-48293 pour résoudre le problème d'Adobe Commerce où les produits composites sont en rupture de stock lorsque les produits enfants épuisés sont retournés en stock.
feature: Admin Workspace, Orders, Products
role: Admin
exl-id: 2aa75e97-373e-4e4a-a545-69bce807ca4d
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
subfeature_v2:
  - id: bb2df8be-afdd-4818-b6b5-95ca1dd3bc3a
    internal-label: Admin workspace
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '461'
ht-degree: 0%
---
# ACSD-48293 : produits composites en rupture de stock en cas de rupture de stock de produits enfants réapprovisionnés

Le correctif ACSD-48293 corrige le problème de rupture de stock des produits composites lorsque les produits enfants épuisés sont retournés en stock. Ce correctif est disponible lorsque la version 1.1.25 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-48293. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.6.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3-p3

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3 - 2.4.4

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les produits composites sont en rupture de stock lorsque les produits enfants qui ont été vendus sont retournés en stock.

<u>Procédure à suivre </u> :

1. Créez un site web secondaire, un magasin et une vue de magasin.
1. Créez deux sources et deux stocks et affectez-les à chaque site web.
1. Activez l’option Afficher les produits en rupture de stock sous **[!UICONTROL Store]** > **[!UICONTROL Config]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Stock Options]** > **[!UICONTROL Display Out-of-Stock Products]** = *[!UICONTROL Yes]*.
1. Créez un produit configurable avec un produit associé à l&#39;aide de la source de stock du site Web principal (quantité définie = 1).
1. Commandez le produit configurable.
1. Exécutez le cron.
1. Ouvrez le produit configurable à partir du storefront et confirmez qu’il est en rupture de stock.
1. Ouvrez le produit configurable à partir du [!UICONTROL Admin] et définissez la **[!UICONTROL Manage Stock Option]** sur *[!UICONTROL No]*.
1. Exécutez le cron.
1. Expédiez la commande et ajoutez de la quantité au produit simple pour le rendre en stock.
1. Exécutez le cron.
1. Vérifiez la disponibilité du produit sur le storefront.

<u>Résultats attendus</u> :

Le produit configurable est en stock.

<u>Résultats réels</u> :

Le produit configurable est en rupture de stock.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/fr/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
