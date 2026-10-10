---
title: 'ACSD-47559 : prévisualisation du modèle d’e-mail pour l’e-mail pas entièrement visible'
description: Appliquez le correctif ACSD-47559 pour résoudre le problème d’Adobe Commerce où l’aperçu du modèle d’e-mail n’est pas entièrement visible.
feature: Communications, Marketing Tools, Personalization
role: Admin
exl-id: a0bd51e0-990b-47c9-8de0-6071b6f79e54
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: bb03f6c4-cab9-560e-9d02-5816e1808d17
    internal-label: Communications
  - id: 125c1f49-aefd-5f34-a252-288937f95f6b
    internal-label: Marketing Tools
  - id: f37757d8-3174-5335-b977-1161792f965d
    internal-label: Personalization
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '371'
ht-degree: 0%
---
# ACSD-47559 : aperçu du modèle d’e-mail pas entièrement visible

Le correctif ACSD-47559 corrige le problème en raison duquel l’aperçu du modèle d’e-mail n’est pas entièrement visible. Ce correctif est disponible lorsque la version 1.1.24 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.html?lang=fr) est installée. L’ID du correctif est ACSD-47559. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.6.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

L’aperçu du modèle d’e-mail n’est pas entièrement visible.

<u>Procédure à suivre </u> :

* Ajoutez un modèle d’e-mail ou utilisez un modèle d’e-mail existant dans Adobe Commerce Admin > **[!UICONTROL Marketing]** > **[!UICONTROL Communications]** > **[!UICONTROL Email Templates]**.

<u>Résultats attendus</u> :

La fenêtre de prévisualisation est mise à l’échelle en fonction de la taille du modèle d’e-mail.

<u>Résultats réels</u> :

Le pop-up d’aperçu s’ouvre avec des barres de défilement, ce qui est une manière peu pratique de prévisualiser un modèle d’e-mail.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/fr/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
