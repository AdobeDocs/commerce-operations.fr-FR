---
title: 'ACSD-47079 : statut du stock de produits composites non mis à jour lorsque le statut du stock de sous-produits change'
description: Appliquez le correctif ACSD-47079 pour résoudre le problème d’Adobe Commerce où l’état du stock des produits composites (groupés, groupés et configurables) n’est pas mis à jour lorsque l’état du stock des sous-produits change via l’API REST POST /rest/V1/inventory/source-items.
feature: Orders, Products
role: Admin
exl-id: f035f530-fae5-4b61-8af9-044f6ec02284
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '410'
ht-degree: 0%
---
# ACSD-47079 : statut du stock de produits composites non mis à jour lorsque le statut du stock de sous-produits change

Le correctif ACSD-47079 corrige le problème en raison duquel l’état de stock des produits composites (groupés, configurables et groupés) n’est pas mis à jour lorsque l’état de stock des sous-produits est modifié via l’API REST POST `/rest/V1/inventory/source-items`. Ce correctif est disponible lorsque la version 1.1.24 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-47079. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.6.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.4-p2

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

L’état du stock de produits composites (groupés, configurables et groupés) n’est pas mis à jour lorsque l’état du stock de sous-produits est modifié via l’API REST POST `/rest/V1/inventory/source-items`.

<u>Procédure à suivre </u> :

1. Créez un produit configurable, groupé et regroupé avec un produit enfant simple pour chacun.
1. Définissez chaque statut de produit enfant simple sur **[!UICONTROL Out of Stock]** à l’aide de l’appel API `source-items`.
1. Vérifiez maintenant l’état des stocks du produit parent.

<u>Résultats attendus</u> :

Le statut du produit parent est [!UICONTROL Out of Stock].

<u>Résultats réels</u> :

Le statut du produit parent est [!UICONTROL In Stock].

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
