---
title: 'ACSD-51149 : la [!UICONTROL ImportExport] planifiée avec le [!UICONTROL Catalog Permissions] activé invalide les indexeurs'
description: Appliquez le correctif ACSD-51149 pour résoudre le problème de performances d’Adobe Commerce où le [!UICONTROL ImportExport] planifié avec le [!UICONTROL Catalog Permissions] activé invalide les indexeurs.
feature: Cache, Data Import/Export
role: Admin
exl-id: eafc69ab-ec81-4192-85f8-a235f0a131a9
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 0%

---

# ACSD-51149 : la [!UICONTROL ImportExport] planifiée avec le [!UICONTROL Catalog Permissions] activé invalide les indexeurs

Le correctif ACSD-51149 corrige le problème où le [!UICONTROL ImportExport] planifié avec activé [!UICONTROL Catalog Permissions] invalide les indexeurs. Ce correctif est disponible lorsque la version 1.1.35 de [!DNL Quality Patches Tool (QPT)] est installée. L’ID du correctif est ACSD-51149. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.7 - 2.4.6-p1

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les [!UICONTROL ImportExport] planifiés avec le [!UICONTROL Catalog Permissions] activé invalident les indexeurs.

<u>Procédure à suivre </u> :

1. Activez *[!UICONTROL Catalog Permissions]*.
1. Définissez tous les indexeurs sur *[!UICONTROL Update by Schedule]*.
1. Créez un produit simple.
1. Exportez ce produit via **[!UICONTROL System]** > **[!UICONTROL Data Transfer]** > **[!UICONTROL Export]**.
1. Téléchargez le fichier CSV exporté et placez-le dans `<AC root folder>/var/import`.
1. Créez une importation de produit planifiée avec le fichier CSV téléchargé.
1. Exécutez la réindexation complète.
1. Vérifiez le statut des indexeurs. Tous les indexeurs doivent avoir le statut *[!UICONTROL Ready]*.
1. Exécutez l’import planifié créé à partir de la grille.
1. Vérifiez à nouveau le statut des indexeurs.

<u>Résultats attendus</u> :

Tous les indexeurs ont le statut *[!UICONTROL Ready]*.

<u>Résultats réels</u> :

Certains indexeurs ont le statut *[!UICONTROL Reindex Required]*.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
