---
title: 'ACSD-61199 : l’onglet [!UICONTROL Hierarchy] de page CMS n’affiche pas la structure d’arborescence appropriée'
description: Appliquez le correctif ACSD-61199 pour résoudre le problème d’Adobe Commerce où l’onglet *[!UICONTROL Hierarchy]* de la page CMS n’affiche pas une arborescence appropriée lors de la modification d’une page CMS avec un *[!UICONTROL Hierarchy]* existant.
feature: Page Content
role: Admin, Developer
exl-id: f541d001-9680-431a-9a62-816c2d10b6d5
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 17d326fa-534a-55a5-b46f-8ae1de1e2f75
    internal-label: Page Content
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
source-wordcount: '348'
ht-degree: 0%
---
# ACSD-61199 : l’onglet [!UICONTROL Hierarchy] de la page CMS n’affiche pas la structure d’arborescence appropriée

Le correctif ACSD-61199 corrige le problème en raison duquel l’onglet *[!UICONTROL Hierarchy]* de la page CMS n’affiche pas une arborescence appropriée lors de la modification d’une page CMS avec un *[!UICONTROL Hierarchy]* existant. Ce correctif est disponible lorsque la version 1.1.54 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-61199. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.7

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

L’onglet *[!UICONTROL Hierarchy]* de la page CMS n’affiche pas une arborescence appropriée lors de la modification d’une page CMS avec un *[!UICONTROL Hierarchy]* existant.

<u>Procédure à suivre </u> :

1. Accédez à **[!UICONTROL Admin]** > **[!UICONTROL Content]** > **[!UICONTROL Pages]**.
1. Créez un nouveau **[!UICONTROL CMS page]**. Il est ajouté à la racine du site web au niveau du *[!UICONTROL Hierarchy]*.
1. Enregistrez la page.
1. Accédez à **[!UICONTROL Admin]** > **[!UICONTROL Content]** > **[!UICONTROL Hierarchy]**.
1. Ajoutez d’autres pages existantes à la *[!UICONTROL Hierarchy]*.
1. Enregistrez le *[!UICONTROL Hierarchy]*.
1. Accédez à **[!UICONTROL Admin]** > **[!UICONTROL Content]** > **[!UICONTROL Pages]**.
1. Modifiez l’une des pages existantes et ouvrez la *[!UICONTROL Hierarchy]*.

<u>Résultats attendus</u> :

Le *[!UICONTROL Hierarchy]* se charge comme prévu.

<u>Résultats réels</u> :

Le *[!UICONTROL Hierarchy]* n’est pas chargé dans l’onglet .

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

[[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
