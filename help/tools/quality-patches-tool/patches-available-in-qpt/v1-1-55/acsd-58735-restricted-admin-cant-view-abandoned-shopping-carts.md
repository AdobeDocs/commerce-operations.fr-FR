---
title: 'ACSD-58735 : l’administrateur restreint ne peut pas afficher les paniers abandonnés sur le compte client pour le site web associé'
description: Appliquez le correctif ACSD-58735 pour résoudre le problème d’Adobe Commerce en raison duquel un administrateur restreint ne peut pas afficher les paniers abandonnés sur la page du compte client dans l’Administration Commerce pour un site web associé.
feature: Shopping Cart, Admin Workspace, Customers
role: Admin, Developer
exl-id: b5dcc12f-325d-4de5-bae5-ff938ec77b13
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: df8eaa0e-dd74-553a-8ad5-28129f8e8d3d
    internal-label: Shopping Cart
  - id: 22bad240-8308-569b-a9d5-578f1ff890ca
    internal-label: Customers
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
subfeature_v2:
  - id: bb2df8be-afdd-4818-b6b5-95ca1dd3bc3a
    internal-label: Admin workspace
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '408'
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
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
