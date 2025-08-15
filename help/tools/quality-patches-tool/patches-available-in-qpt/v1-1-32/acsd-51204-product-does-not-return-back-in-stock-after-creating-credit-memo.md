---
title: 'ACSD-51204 : le produit ne revient pas en stock après la création de l''avoir'
description: Appliquez le correctif ACSD-51204 pour résoudre le problème d'Adobe Commerce en raison duquel le produit n'est pas retourné en stock après la création de l'avoir.
feature: Orders, Products, Returns
role: Admin
exl-id: a4dba28c-c239-4812-8b3a-ce0493f9b1aa
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '400'
ht-degree: 0%

---

# ACSD-51204 : le produit ne revient pas en stock après la création de l&#39;avoir

Le correctif ACSD-51204 corrige le problème lorsque le produit ne revient pas en stock après la création de l&#39;avoir. Ce correctif est disponible lorsque la version 1.1.32 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est ACSD-51204. Notez que le problème a été résolu dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3 - 2.4.6-p1

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le produit épuisé ne revient pas en stock après la création de l&#39;avoir.

<u>Procédure à suivre </u> :

1. Installez **[!UICONTROL Adobe Commerce]** et activez le **[!UICONTROL Inventory Management Module]** avec les valeurs par défaut *source* et *stock* uniquement.
1. Ajoutez une **[!UICONTROL new product]** avec une quantité de *10*.
1. Attribuez le produit au **[!UICONTROL default stock]**.
1. Sur le Storefront, ajoutez le produit au panier et passez une commande pour une quantité totale disponible 10.
1. Dans le panneau d’administration, générez une *facture* et *expédition* pour la commande.
1. Créez un **[!UICONTROL Credit Memo]** avec la case *Retour au stock* sélectionnée pour tous les éléments.
1. Vérifiez les **[!UICONTROL Salable Quantity]** du produit dans l’administrateur.

<u>Résultats attendus</u> :

La quantité commercialisable du produit doit revenir à *10*.

<u>Résultats réels</u> :

La quantité commercialisable du produit est laissée à *0*.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>) dans le guide de [!DNL Quality Patches Tool].
