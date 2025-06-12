---
title: 'MDVA-41139 : le produit configurable est en rupture de stock après l’importation du produit'
description: Le correctif MDVA-41139 corrige le problème où le produit configurable devient en rupture de stock après l’importation du produit lorsque la quantité du produit simple = 0 pour l’une de ses sources. Ce correctif est disponible lorsque l’outil [Outil de correctifs de la qualité (QPT)](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.8 est installé. L’ID du correctif est MDVA-41139. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.4.
feature: Data Import/Export, Configuration, Orders, Products
role: Admin
exl-id: 7366230c-3b7f-4211-9f0d-55a528dffdbd
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '452'
ht-degree: 0%

---

# MDVA-41139 : le produit configurable est en rupture de stock après l’importation du produit

Le correctif MDVA-41139 corrige le problème où le produit configurable devient en rupture de stock après l’importation du produit lorsque la quantité du produit simple = 0 pour l’une de ses sources. Ce correctif est disponible lors de l’installation de l’outil [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) version 1.1.8. L’ID du correctif est MDVA-41139. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.4.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3 - 2.4.3-p1

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le produit configurable devient en rupture de stock après l&#39;importation du produit lorsque la quantité du produit simple = 0 pour l&#39;une de ses sources.

<u>Conditions préalables</u> :

Les modules d’inventaire sont installés.

<u>Procédure à suivre </u> :

1. Créez une nouvelle source et un nouveau stock.
1. Créez un produit configurable avec des produits enfants affectés à la source par défaut et à la nouvelle source.
1. Définissez la valeur du stock par défaut pour chaque produit enfant = 0 et pour les autres stocks > 0.
1. Le produit configurable est en stock.
1. Exportez ce produit et importez-le à nouveau.

<u>Résultats attendus</u> :

Le produit configurable est en stock, car la quantité de la deuxième source est supérieure à 0.

<u>Résultats réels</u> :

Le produit configurable est en rupture de stock.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur l’outil de correctifs de la qualité, voir :

* Publication de l’outil [Correctifs de qualité](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) un nouvel outil permettant d’appliquer des correctifs de qualité en libre-service dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!DNL Quality Patches Tool].

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
