---
title: 'ACSD-58008 : la modification de la date de fin en tant que *vide* entraîne la disparition de la mise à jour du planning'
description: Appliquez le correctif ACSD-58008 pour résoudre le problème d’Adobe Commerce en raison duquel la modification de la date de fin en tant que *vide* entraîne la disparition de la mise à jour du planning.
feature: Staging, Page Content
role: Admin, Developer
exl-id: 6d2279e5-6580-4325-b0a8-ed62a95da3c2
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 0%

---

# ACSD-58008 : la modification de la date de fin en tant que *vide* entraîne la disparition de la mise à jour du planning

Le correctif ACSD-58008 corrige le problème en raison duquel la modification de la date de fin en tant que *vide* entraîne la disparition de la mise à jour du planning. Ce correctif est disponible lorsque la version 1.1.48 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est ACSD-58008. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p5

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5 - 2.4.6-p4

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La modification de la date de fin en tant que *vide* entraîne la disparition de la mise à jour du planning

<u>Procédure à suivre </u> :

1. Connectez-vous en tant qu’[!UICONTROL Admin].
1. Accédez à **[!UICONTROL Content]** > **[!UICONTROL Elements]** > **[!UICONTROL Pages]** et créez une page.
1. Sélectionnez la page créée et cliquez sur **[!UICONTROL Schedule New Update]**. *(Accédez au coin supérieur droit de la page)*.
1. Créez quatre mises à jour. *(par exemple, par incrément de* 2 *minutes)*.
1. Mettez à jour la *mise à jour 2* et définissez l’heure sur une heure antérieure à la dernière *mise à jour 4*.
1. Enregistrez les mises à jour effectuées.

<u>Résultats attendus</u> :

La mise à jour du planning affiche la *mise à jour 3*.

<u>Résultats réels</u> :

La mise à jour du planning n’affiche pas la *mise à jour 3*.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
