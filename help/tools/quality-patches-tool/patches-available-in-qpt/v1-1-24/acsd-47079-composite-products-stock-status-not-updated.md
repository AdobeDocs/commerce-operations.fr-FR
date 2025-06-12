---
title: 'ACSD-47079 : statut du stock de produits composites non mis à jour lorsque le statut du stock de sous-produits change'
description: Appliquez le correctif ACSD-47079 pour résoudre le problème d’Adobe Commerce où l’état du stock des produits composites (groupés, groupés et configurables) n’est pas mis à jour lorsque l’état du stock des sous-produits change via l’API REST POST /rest/V1/inventory/source-items.
feature: Orders, Products
role: Admin
exl-id: f035f530-fae5-4b61-8af9-044f6ec02284
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '383'
ht-degree: 0%

---

# ACSD-47079 : statut du stock de produits composites non mis à jour lorsque le statut du stock de sous-produits change

Le correctif ACSD-47079 corrige le problème en raison duquel l’état de stock des produits composites (groupés, configurables et groupés) n’est pas mis à jour lorsque l’état de stock des sous-produits est modifié via l’API REST POST `/rest/V1/inventory/source-items`. Ce correctif est disponible lorsque la version 1.1.24 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est ACSD-47079. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.6.

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
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
