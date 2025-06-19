---
title: 'ACSD-58325 : bouton [!UICONTROL Import] disponible même après une erreur de validation'
description: Appliquez le correctif ACSD-58325 pour résoudre le problème d’Adobe Commerce où le bouton [!UICONTROL Import] est disponible même après une erreur de validation.
feature: Data Import/Export
role: Admin, Developer
exl-id: 551a9ac7-9b7f-49b5-9255-2014c330fb07
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '287'
ht-degree: 0%

---

# ACSD-58325 : bouton [!UICONTROL Import] disponible même après une erreur de validation

Le correctif ACSD-58325 corrige le problème en raison duquel le bouton **[!UICONTROL Import]** est disponible même après une erreur de validation. Ce correctif est disponible lorsque la version 1.1.57 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-58325. Notez que le problème a été résolu dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**
* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6-p3

**Compatible avec les versions d’Adobe Commerce :**
* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6 - 2.4.6-p8

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le bouton [!UICONTROL Import] est disponible même après une erreur de validation.

<u>Procédure à suivre </u> :

1. Créez le fichier CSV pour l’importation du produit avec un nom d’image incorrect dans le fichier .
1. Créez une importation de produit planifiée à l’aide du fichier CSV créé.
1. Patientez jusqu’à ce que l’importation planifiée soit effectuée.
1. Vérifiez [!UICONTROL Last outcome] dans **[!UICONTROL Scheduled Imports/Exports]** grille.

<u>Résultats attendus</u> :

[!UICONTROL Last outcome] devrait être [!UICONTROL Failed].

<u>Résultats réels</u> :

[!UICONTROL Last outcome] est [!UICONTROL Successful].

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .


## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
