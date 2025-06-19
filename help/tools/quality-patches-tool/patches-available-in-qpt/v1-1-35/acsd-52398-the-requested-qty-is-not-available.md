---
title: 'ACSD-52398 : quantité demandée non disponible lors de la tentative de mise à jour de la quantité de produit groupé'
description: Appliquez le correctif ACSD-52398 pour résoudre le problème d’Adobe Commerce en raison duquel la quantité demandée n’est pas disponible lors de la tentative de mise à jour de la quantité d’un produit groupé dans le panier sur le storefront.
feature: Shopping Cart, Quotes, Products
role: Admin
exl-id: 75fa5f96-22e7-40a2-8b8a-f44452e5124d
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '407'
ht-degree: 0%

---

# ACSD-52398 : quantité demandée non disponible lors de la tentative de mise à jour de la quantité de produit groupé

Le correctif ACSD-52398 corrige le problème où la quantité demandée n’est pas disponible lors de la tentative de mise à jour de la quantité d’un produit groupé dans le panier sur le storefront. Ce correctif est disponible lorsque la version 1.1.35 de [!DNL Quality Patches Tool (QPT)] est installée. L’ID du correctif est ACSD-52398. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3-p3

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.0 - 2.4.6-p1

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La quantité demandée n’est pas disponible lors de la tentative de mise à jour de la quantité d’un produit groupé dans le panier sur le storefront.

<u>Procédure à suivre </u> :

1. Créez deux produits simples avec la quantité *1* et *10*.
1. Créez un produit groupé à l’aide des produits simples.
1. Ajoutez le produit groupé au panier.
1. Modifiez le produit et essayez de mettre à jour la quantité à *3* pour l’option où les articles *10* sont disponibles.

<u>Résultats attendus</u> :

Il n’y a aucune erreur. La quantité a été mise à jour avec succès, car 10 articles ** sont en stock pour cette option.

<u>Résultats réels</u> :

L&#39;erreur suivante est générée : *La quantité demandée n&#39;est pas disponible*.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
