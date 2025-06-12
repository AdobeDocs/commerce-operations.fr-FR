---
title: 'ACSD-55004 : le programme de validation se bloque lors du chargement d’un fichier d’importation plus volumineux que la valeur'
description: Appliquez le correctif ACSD-55004 pour résoudre le problème d’Adobe Commerce où un programme de validation se bloque lors du chargement d’un fichier d’importation dont la taille est supérieure à la valeur configurée dans « php.ini ».
feature: Data Import/Export
role: Admin, Developer
exl-id: c889f645-a3ae-4330-8ca9-45f8b6616ac8
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '331'
ht-degree: 0%

---

# ACSD-55004 : le programme de validation se bloque lors du chargement d’un fichier d’importation plus volumineux que la valeur

Le correctif ACSD-55004 corrige le problème où un programme de validation se bloque lors du chargement d’un fichier d’importation plus volumineux que la valeur configurée dans `php.ini`. Ce correctif est disponible lorsque la version 1.1.40 de [!DNL Quality Patches Tool (QPT)] est installée. L’ID du correctif est ACSD-55004. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le programme de validation se bloque lors du chargement d’un fichier d’importation dont la taille est supérieure à la valeur configurée dans `php.ini`.

<u>Procédure à suivre </u> :

Essayez de charger un fichier d’importation plus volumineux que configuré dans `php.ini`.

<u>Résultats attendus</u> :

La taille du fichier est validée sans erreur.

<u>Résultats réels</u> :

Le programme de validation plante.

`var/log/exception.log` contient :

```
[2023-10-06T21:36:30.470618+00:00] report.CRITICAL: Error: Class "Zend_Validate_File_Upload" not found in ../module-import-export/Model/Source/Upload.php:81
```

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
