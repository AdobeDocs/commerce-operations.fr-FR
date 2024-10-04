---
title: "ACSD-47079 : statut des stocks de produits composites non mis à jour lorsque l’état des stocks de sous-produits change"
description: Appliquez le correctif ACSD-47079 pour résoudre le problème Adobe Commerce en raison duquel l’état du stock des produits composites (groupé, groupé et configurable) n’est pas mis à jour lorsque l’état du stock des sous-produits change via le POST API REST /rest/V1/inventory/source-items.
feature: Orders, Products
role: Admin
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '383'
ht-degree: 0%

---

# ACSD-47079 : l’état du stock des produits composites n’est pas mis à jour lorsque l’état du stock des sous-produits change

Le correctif ACSD-47079 corrige le problème en raison duquel l’état du stock des produits composites (groupé, groupé et configurable) n’est pas mis à jour lorsque l’état du stock du sous-produit est modifié via le POST API REST `/rest/V1/inventory/source-items`. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.24 est installé. L’ID de correctif est ACSD-47079. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.6.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.4-p2

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

L’état du stock des produits composites (bundle, groupé et configurable) n’est pas mis à jour lorsque l’état du stock du sous-produit est modifié via le POST API REST `/rest/V1/inventory/source-items`.

<u>Étapes à reproduire</u> :

1. Créez un produit configurable, groupé et groupé avec un seul produit enfant pour chacun d’eux.
1. Définissez l’état de chaque produit enfant simple sur **[!UICONTROL Out of Stock]** à l’aide de l’appel API `source-items`.
1. Vérifiez maintenant l’état du stock du produit parent.

<u>Résultats attendus</u> :

L’état du produit parent est [!UICONTROL Out of Stock].

<u>Résultats réels</u> :

L’état du produit parent est [!UICONTROL In Stock].

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!UICONTROL Quality Patches Tool].


Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].