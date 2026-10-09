---
title: 'ACSD-62708 : la taille de police de l’éditeur [!DNL TinyMCE] 7 dans le panneau d’administration affiche PT'
description: Appliquez le correctif ACSD-62708 pour résoudre le problème d’Adobe Commerce où [!DNL TinyMCE] taille de police de l’éditeur 7 dans l’administration affiche PT et non PX. Désormais, vous pouvez également définir la taille de police en PX au lieu de PT.
feature: Admin Workspace
role: Admin, Developer
exl-id: 037a5831-dbc7-4834-ab8e-9b1f765b92b2
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
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
source-wordcount: '349'
ht-degree: 0%
---
# ACSD-62708 : la taille de police de l’éditeur [!DNL TinyMCE] 7 dans le panneau d’administration affiche PT

Le correctif ACSD-62708 résout le problème d’affichage de la taille de police de l’éditeur [!DNL TinyMCE] 7 dans le panneau d’administration en PT au lieu de PX. Ce correctif vous permet de définir la taille de police en PX. Ce correctif est disponible lorsque la version 1.1.57 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-62708. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.7-p3

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4-p11, 2.4.5-p10, 2.4.6-p8

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

L’éditeur [!DNL TinyMCE] 7 du panneau d’administration affiche la taille de police en PT au lieu de PX.

<u>Procédure à suivre </u> :

1. Ouvrez la page de modification du produit dans le panneau d’administration.
1. Développez la section [!UICONTROL Content] .
1. Vérifiez les commandes de police dans l’éditeur de [!DNL TinyMCE].

<u>Résultats attendus</u> :

La taille de la police doit être en PX.

<u>Résultats réels</u> :

La taille de la police est en PT.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
