---
title: 'ACSD-58735 : l’administrateur restreint ne peut pas afficher les paniers abandonnés sur le compte client pour le site web associé'
description: Appliquez le correctif ACSD-58735 pour résoudre le problème d’Adobe Commerce en raison duquel un administrateur restreint ne peut pas afficher les paniers abandonnés sur la page du compte client dans l’Administration Commerce pour un site web associé.
feature: Shopping Cart, Admin Workspace, Customers
role: Admin, Developer
exl-id: b5dcc12f-325d-4de5-bae5-ff938ec77b13
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '389'
ht-degree: 0%

---

# ACSD-58735 : l’administrateur restreint ne peut pas afficher les paniers abandonnés sur le compte client pour le site web associé

Le correctif ACSD-58735 corrige le problème en raison duquel un utilisateur administrateur disposant d’un rôle restreint ne peut pas afficher les paniers des clients abandonnés à partir de l’onglet **[!UICONTROL Admin]** Commerce > **[!UICONTROL Reports]** > **[!UICONTROL Abandoned Carts]** > **[!UICONTROL Select Cart]** > **[!UICONTROL Shopping Cart]** .

Le problème se produit, car lors de l’affichage de la grille pour plusieurs sites web, si un panier abandonné est chargé par défaut dans le panneau d’administration, il n’obtient pas l’identifiant de magasin associé à afficher.

Ce correctif est disponible lorsque la version 1.1.55 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-58735. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.5.0.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6-p4

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les administrateurs restreints ne peuvent pas afficher les paniers abandonnés sur la page du compte client dans le panneau d’administration.

<u>Procédure à suivre </u> :

1. Créez un rôle d’administrateur ayant accès à un seul des sites web.
1. Créez un panier abandonné.
1. Connectez-vous en tant qu’utilisateur administrateur avec des privilèges complets. Cochez **[!UICONTROL Reports]** > **[!UICONTROL Abandoned Carts]** et vérifiez que le panier s’affiche.
1. Cochez **[!UICONTROL Reports]** > **[!UICONTROL Abandoned Carts]** en tant qu’utilisateur administrateur restreint.

<u>Résultats attendus</u> :

L’administrateur restreint peut voir les paniers abandonnés pour le site web associé.

<u>Résultats réels</u> :

L’administrateur restreint ne voit pas les paniers abandonnés pour le site web associé.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
