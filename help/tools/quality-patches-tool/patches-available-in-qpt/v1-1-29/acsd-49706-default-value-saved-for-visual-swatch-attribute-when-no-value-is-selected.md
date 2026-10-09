---
title: 'ACSD-49706 : valeur par défaut enregistrée pour l’attribut d’échantillon visuel lorsqu’aucune valeur n’est sélectionnée'
description: Appliquez le correctif ACSD-49706 pour résoudre le problème d’Adobe Commerce où une valeur par défaut est enregistrée pour un attribut d’échantillon visuel lorsqu’aucune valeur n’est sélectionnée.
feature: Admin Workspace, Attributes
role: Admin
exl-id: fa3cb0a1-f898-4826-aa64-efeba1af58a8
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 76cfaac4-e563-56dd-8938-708bf8b84956
    internal-label: Attributes
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
source-wordcount: '425'
ht-degree: 0%
---
# ACSD-49706 : valeur par défaut enregistrée pour l’attribut d’échantillon visuel lorsqu’aucune valeur n’est sélectionnée

Le correctif ACSD-49706 corrige le problème où une valeur par défaut est enregistrée pour un attribut d’échantillon visuel lorsqu’aucune valeur n’est sélectionnée. Ce correctif est disponible lorsque la version 1.1.29 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-49706. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.7 - 2.4.6

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Une valeur par défaut est enregistrée pour un attribut d’échantillon visuel lorsqu’aucune valeur n’est sélectionnée.

<u>Procédure à suivre </u> :

1. Accédez à **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Product]**.
1. Cliquez sur **[!UICONTROL Add New Attribute]**.
1. Renseignez les champs .

   * Par exemple, choisissez le type d’entrée *[!UICONTROL Visual Swatch]* et ajoutez plusieurs options (telles que *Rouge* *Vert*). Veillez à choisir l’une de ces options par défaut.
   * Cliquez sur **[!UICONTROL Save Attribute]**.

1. Accédez à **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Attribute Set]**.
1. Modifiez le jeu d’attributs *[!UICONTROL Default]*.
1. Déplacez le *[!UICONTROL New Attribute]* de la colonne *[!UICONTROL Unassigned Attributes]* vers le dossier *[!UICONTROL Product Details]* de la colonne centrale.

   * Cliquez sur **[!UICONTROL Save]**.

1. Créez un produit à l’aide du jeu d’attributs *[!UICONTROL Default]*.

   * Laissez le *[!UICONTROL New Attribute]* vide et enregistrez-le.

1. Une fois enregistrée, une valeur apparaît dans *[!UICONTROL New Attribute]*.

<u>Résultats attendus</u> :

Aucune valeur n’est affectée à *[!UICONTROL New Attribute]* par défaut.

<u>Résultats réels</u> :

Une valeur par défaut est appliquée à l’attribut lors de l’enregistrement d’un produit.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/fr/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
