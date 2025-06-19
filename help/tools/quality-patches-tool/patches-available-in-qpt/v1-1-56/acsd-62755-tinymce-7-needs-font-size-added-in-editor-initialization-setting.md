---
title: 'ACSD-62755: [!DNL TinyMCE] 7 nécessite l’ajout de la taille et de la police aux paramètres d’initialisation de l’éditeur'
description: Appliquez le correctif ACSD-62755 pour résoudre le problème d’Adobe Commerce où  [!DNL TinyMCE] 7 nécessite que *la taille de police* et *la famille de polices* soient spécifiquement ajoutées dans les paramètres d’initialisation de l’éditeur.
feature: Page Content, Page Builder, Admin Workspace
role: Admin, Developer
exl-id: f61dc7b6-ac6b-45eb-a0a2-f3f0bff4422b
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '305'
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
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
