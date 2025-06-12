---
title: 'MDVA-27239 : les produits de ventes croisées ne sont pas affichés'
description: Le correctif MDVA-27239 corrige le problème d’affichage des produits de ventes croisées. Ce correctif est disponible lorsque l’outil [Outil de correctifs de la qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.7 est installé. Notez que le problème a été résolu dans Adobe Commerce 2.3.6.
feature: Products
role: Admin
exl-id: ab8fe64d-adbe-4756-be43-1a35ba6b4123
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '402'
ht-degree: 0%

---

# MDVA-27239 : les produits de ventes croisées ne sont pas affichés

Le correctif MDVA-27239 corrige le problème d’affichage des produits de ventes croisées. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.7 est installé. Notez que le problème a été résolu dans Adobe Commerce 2.3.6.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.3.4, 2.4.0

**Compatible avec les versions d’Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.3.0 - 2.3.5-p2, 2.4.0 - 2.4.0-p1

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les produits de vente croisée ne sont pas affichés dans le bloc de vente croisée de la page du panier.

<u>Conditions préalables</u> :

1. Désactivez le module Magento_TargetRule ou supprimez du bloc de disposition Magento\TargetRule\Block\Checkout\Cart\Crosssell.
1. Créer un produit 1.
1. Créez une mise à jour de planning pour le Produit 1, de sorte que les nouveaux produits aient un row_id différent de entity_id.
1. Créez les produits 2, 3 et 4.
1. Définissez le produit 3 comme vente croisée pour le produit 4.
1. Définissez le produit 4 comme vente croisée pour le produit 2.

<u>Procédure à suivre </u> :

1. Ajoutez les produits 4 et 2 au panier.
1. Consultez la page du panier.

<u>Résultats attendus</u> :

Le produit 3 est affiché dans le bloc de ventes croisées.

<u>Résultats réels</u> :

Le bloc de ventes croisées est vide.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur l’outil de correctifs de la qualité, voir :

* Publication de l’outil [Correctifs de qualité](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) un nouvel outil permettant d’appliquer des correctifs de qualité en libre-service dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!DNL Quality Patches Tool].

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
