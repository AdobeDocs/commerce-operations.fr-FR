---
title: "ACSD-45488 : produit configurable avec plusieurs sources qui ne sont pas automatiquement retournées en stock"
description: Le correctif ACSD-45488 résout le problème en raison duquel un produit configurable avec plusieurs sources n’est pas automatiquement renvoyé en stock. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.18 est installé. L’ID de correctif est ACSD-45488. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.6.
feature: Configuration, Orders, Products, Returns
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '457'
ht-degree: 0%

---

# ACSD-45488 : le produit configurable avec plusieurs sources qui ne sont pas retournées en stock automatiquement

Le correctif ACSD-45488 résout le problème en raison duquel un produit configurable avec plusieurs sources n’est pas automatiquement renvoyé en stock. Ce correctif est disponible lorsque l’ [outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.18 est installé. L’ID de correctif est ACSD-45488. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.6.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2-p2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2 - 2.4.5

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Un produit configurable avec plusieurs sources n’est pas automatiquement renvoyé en stock.

<u>Étapes à reproduire</u> :

1. Créez une source de stock secondaire.
1. Créez un produit configurable avec deux produits virtuels associés.
1. Attribuez les produits associés à la source de stock par défaut et définissez la quantité sur une.
1. Vérifiez le `stock_status` de `cataloginventory_stock_status`.
1. Définissez les deux produits associés sur *out of stock*.
1. Vérifiez le `stock_status` de `cataloginventory_stock_status`.
1. Définissez les deux produits associés sur *en stock*.
1. Vérifiez le `stock_status` de `cataloginventory_stock_status`.

<u>Résultats attendus</u> :

L’état du stock du produit configurable est mis à jour sur *en stock* lorsque les produits associés sont définis pour être en stock.

<u>Résultats réels</u> :

L’état du stock du produit configurable n’est pas mis à jour vers *en stock* lorsque les produits associés sont définis pour être en stock.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [ L’outil de correctifs de qualité est sorti : un nouvel outil pour les correctifs de qualité en libre-service ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!DNL Quality Patches Tool].

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].
