---
title: 'ACSD-54342 : message d’erreur lors de l’importation d’un fichier CSV sans données valides'
description: Appliquez le correctif ACSD-54342 pour résoudre le problème d’Adobe Commerce où un message d’erreur incorrect se produit lors de l’importation d’un fichier CSV sans données valides.
feature: Roles/Permissions
role: Admin, Developer
exl-id: 34324a18-45af-462b-a6e6-6b6a02d4d331
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 0%

---

# ACSD-54342 : message d’erreur lors de l’importation d’un fichier CSV sans données valides

Le correctif ACSD-54342 corrige le problème où un message d’erreur incorrect se produit lors de l’importation d’un fichier CSV sans données valides. Ce correctif est disponible lorsque la version 1.1.39 de [!DNL Quality Patches Tool (QPT)] est installée. L’ID du correctif est ACSD-54342. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6-p2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.0 - 2.4.6-p3

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Un message d’erreur incorrect apparaît lors de l’importation d’un fichier CSV sans données valides.

<u>Procédure à suivre </u> :

1. Créez un fichier d’importation contenant uniquement des données non valides (exemples : [!DNL SKUs] qui n’existent pas, champs d’adresse client non valides ou adresses e-mail client incorrectes).
1. Importez le fichier, en choisissant d’ignorer les erreurs de validation.

<u>Résultats attendus</u> :

La validation échoue avec le message `There are no valid rows to import`.

<u>Résultats réels</u> :

La validation réussit, mais l’importation échoue avec `Error in data structure: values are mixed` message.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
