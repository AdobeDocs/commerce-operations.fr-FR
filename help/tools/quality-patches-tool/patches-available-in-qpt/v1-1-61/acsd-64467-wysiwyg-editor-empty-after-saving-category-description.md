---
title: 'ACSD-64467 : éditeur WYSIWYG vide après l’enregistrement de la description de la catégorie au niveau de l’affichage du magasin'
description: Appliquez le correctif ACSD-64467 pour résoudre le problème d’Adobe Commerce en raison duquel l’éditeur WYSIWYG apparaît vide après l’enregistrement d’une description de catégorie au niveau de l’affichage du magasin.
feature: Page Content
role: Admin, Developer
source-git-commit: 4e883b3ec9b790f52dd56206539475e72bdf361d
workflow-type: tm+mt
source-wordcount: '320'
ht-degree: 0%

---

# ACSD-64467 : éditeur WYSIWYG vide après l’enregistrement de la description de la catégorie au niveau de l’affichage du magasin

Le correctif ACSD-64467 corrige le problème en raison duquel l’éditeur WYSIWYG apparaît vide après l’enregistrement d’une description de catégorie au niveau de l’affichage du magasin. Ce correctif est disponible lorsque la version 1.1.61 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-64467. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.7-p3

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.7 - 2.4.7-p4

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

L’éditeur WYSIWYG apparaît vide après l’enregistrement d’une description de catégorie au niveau de l’affichage du magasin.

<u>Procédure à suivre </u> :

1. Modifiez une catégorie dans l’Administration Commerce au niveau de la vue de magasin.
1. Décochez la case *[!UICONTROL Use default value]* en regard de la description de la catégorie.
1. Saisissez une description dans l’éditeur WYSIWYG.
1. Cliquez sur **[!UICONTROL Save]**.

<u>Résultats attendus</u> :

La description est enregistrée et correctement affichée.

<u>Résultats réels</u> :

La description est vide après le rechargement de la page.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
