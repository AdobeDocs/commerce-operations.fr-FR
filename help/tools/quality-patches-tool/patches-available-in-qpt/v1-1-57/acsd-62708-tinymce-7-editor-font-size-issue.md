---
title: 'La taille de police de l’éditeur ACSD-62708: [!DNL TinyMCE] 7 dans le panneau d’administration affiche PT'
description: Appliquez le correctif ACSD-62708 pour résoudre le problème d’Adobe Commerce où la taille de police de l’éditeur  [!DNL TinyMCE] 7 dans l’administration affiche PT et non PX. Désormais, vous pouvez également définir la taille de police en PX au lieu de PT.
feature: Admin Workspace
role: Admin, Developer
source-git-commit: ecb04a058e858580dfbc7a1edcd319423be9eeaa
workflow-type: tm+mt
source-wordcount: '327'
ht-degree: 0%

---


# ACSD-62708 : la taille de police de l’éditeur [!DNL TinyMCE] 7 dans le panneau d’administration affiche PT

Le correctif ACSD-62708 résout le problème d’affichage de la taille de police de l’éditeur [!DNL TinyMCE] 7 dans le panneau d’administration en PT au lieu de PX. Ce correctif vous permet de définir la taille de police en PX. Ce correctif est disponible lorsque la version 1.1.57 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-62708. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.7-p3

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4-p11, 2.4.5-p10, 2.4.6-p8

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

L’éditeur [!DNL TinyMCE] 7 du panneau d’administration affiche la taille de police en PT au lieu de PX.

<u>Procédure à suivre </u> :

1. Ouvrez la page de modification du produit dans le panneau d’administration.
1. Développez la section [!UICONTROL Content] .
1. Vérifiez les commandes de police dans l’éditeur de [!DNL TinyMCE].

<u>Résultats attendus</u> :

La taille de la police doit être en PX.

<u>Résultats réels</u> :

La taille de la police est en PT.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-Premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
