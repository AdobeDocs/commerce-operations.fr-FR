---
title: 'ACSD-45488 : produit configurable avec plusieurs sources non retourné automatiquement en stock'
description: Le correctif ACSD-45488 résout le problème où un produit configurable avec plusieurs sources n'est pas automatiquement retourné en stock. Ce correctif est disponible lorsque l’outil [Outil de correctifs de la qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.18 est installé. L’ID du correctif est ACSD-45488. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.6.
feature: Configuration, Orders, Products, Returns
role: Admin
exl-id: 53f34e8e-00bd-4386-bebf-b15882e36da1
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '457'
ht-degree: 0%

---

# ACSD-45488 : produit configurable avec plusieurs sources non retourné automatiquement en stock

Le correctif ACSD-45488 résout le problème où un produit configurable avec plusieurs sources n&#39;est pas automatiquement retourné en stock. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) version 1.1.18 est installé. L’ID du correctif est ACSD-45488. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.6.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2-p2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2 - 2.4.5

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Un produit configurable avec plusieurs sources n’est pas automatiquement renvoyé en stock.

<u>Procédure à suivre </u> :

1. Créez une source de stock secondaire.
1. Créez un produit configurable avec deux produits virtuels associés.
1. Affectez les produits associés à l&#39;origine de stock par défaut et définissez la quantité sur un.
1. Vérifiez le `stock_status` à partir de `cataloginventory_stock_status`.
1. Paramétrez les deux produits associés *en rupture de stock*.
1. Vérifiez le `stock_status` à partir de `cataloginventory_stock_status`.
1. Définissez les deux produits associés pour qu’ils soient *en stock*.
1. Vérifiez le `stock_status` à partir de `cataloginventory_stock_status`.

<u>Résultats attendus</u> :

Le statut de stock du produit configurable est mis à jour à *en stock* lorsque les produits associés sont définis pour être en stock.

<u>Résultats réels</u> :

L&#39;état de stock du produit configurable n&#39;est pas mis à jour à *en stock* lorsque les produits associés sont définis comme étant en stock.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur l’outil de correctifs de la qualité, voir :

* Publication de l’outil [Correctifs de qualité](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) un nouvel outil permettant d’appliquer des correctifs de qualité en libre-service dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!DNL Quality Patches Tool].

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
