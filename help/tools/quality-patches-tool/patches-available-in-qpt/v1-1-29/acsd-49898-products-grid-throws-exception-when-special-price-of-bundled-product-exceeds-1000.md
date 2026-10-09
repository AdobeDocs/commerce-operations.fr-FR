---
title: 'ACSD-49898 : la grille de produits renvoie une exception'
description: Appliquez le correctif ACSD-49898 pour résoudre le problème d’Adobe Commerce lorsque la grille de produits renvoie une exception lorsqu’un produit groupé a un prix spécial qui dépasse 1 000.
feature: Admin Workspace, Orders, Products
role: Admin
exl-id: adc8f12e-73e4-4ed5-8081-a9907ec13342
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
subfeature_v2:
  - id: bb2df8be-afdd-4818-b6b5-95ca1dd3bc3a
    internal-label: Admin workspace
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '407'
ht-degree: 0%
---
# ACSD-49898 : la grille de produits renvoie une exception

Le correctif ACSD-49898 corrige le problème où la grille de produits lance une exception lorsqu’un produit groupé a un prix spécial qui dépasse 1 000. Ce correctif est disponible lorsque la version 1.1.29 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-49898. Notez que le problème a été résolu dans Adobe Commerce 2.4.6.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.5-p2

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La grille de produits renvoie une exception lorsqu’un produit groupé a un prix spécial qui dépasse 1 000. Le problème concerne l’utilisation de virgules au lieu de points pour les nombres décimaux dans certains paramètres régionaux.

<u>Procédure à suivre </u> :

1. Créez un produit groupé.
1. Définissez le prix spécial sur 9999 ; enregistrez et fermez.
1. Accédez à **[!UICONTROL Catalog]** > **[!UICONTROL Products]**

>[!NOTE]
>
>Recherchez le SKU de produit groupé s’il n’est pas visible.

<u>Résultats attendus</u> :

* L’utilisateur peut filtrer/voir le produit groupé avec le prix spécial.
* Le prix spécial s’affiche sous la forme d’un pourcentage pour les produits groupés et d’un prix pour les autres types de produits.

<u>Résultats réels</u> :

L’erreur suivante est générée : *valeur non numérique rencontrée*.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
