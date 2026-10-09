---
title: 'ACSD-62755 : la [!DNL TinyMCE] 7 nécessite l’ajout de la taille de police et de la police aux paramètres d’initialisation de l’éditeur'
description: Appliquez le correctif ACSD-62755 pour résoudre le problème d’Adobe Commerce où la [!DNL TinyMCE] 7 nécessite que *la taille de police* et *la famille de polices* soient spécifiquement ajoutées dans les paramètres d’initialisation de l’éditeur.
feature: Page Content, Page Builder, Admin Workspace
role: Admin, Developer
exl-id: f61dc7b6-ac6b-45eb-a0a2-f3f0bff4422b
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 17d326fa-534a-55a5-b46f-8ae1de1e2f75
    internal-label: Page Content
  - id: cc250cf1-34eb-4863-80d0-d170d45ea067
    internal-label: Developer tools
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
subfeature_v2:
  - id: ed510963-0b8c-4764-86f6-f3c7735bc334
    internal-label: Page Builder
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
source-wordcount: '328'
ht-degree: 0%
---
# ACSD-62755 : la [!DNL TinyMCE] 7 nécessite l’ajout de la taille de police et de la police aux paramètres d’initialisation de l’éditeur

Le correctif ACSD-62755 corrige le problème où la [!DNL TinyMCE] 7 exige que les sélecteurs *taille de police* et *famille de polices* soient spécifiquement ajoutés dans les paramètres d’initialisation de l’éditeur. Ce correctif est disponible avec la version [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.56 installée. L’ID du correctif est ACSD-62755. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p10

**Compatible avec les versions d’Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.4-p11, 2.4.5-p10, 2.4.6-p8, 2.4.7-p3

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La [!DNL TinyMCE] 7 nécessite l’ajout spécifique des sélecteurs *taille de police* et *famille de polices* dans les paramètres d’initialisation de l’éditeur.

<u>Procédure à suivre </u> :

Accédez à **[!UICONTROL Catalog]** > **[!UICONTROL Products]** > **[!UICONTROL Content]**, puis sélectionnez *[!UICONTROL Show Editor]*.

<u>Résultats attendus</u> :

Les sélecteurs *Taille de police* et *famille de polices* sont visibles dans l’éditeur de WYSIWYG.

<u>Résultats réels</u> :

Le sélecteur *Taille de police* est absent de l’éditeur WYSIWYG.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
