---
title: 'ACP2E-3689 : plusieurs problèmes avec l’arborescence des catégories s’affichent à des niveaux plus profonds et reflètent les relations ancre/non-ancre'
description: Appliquez le correctif ACP2E-3689 pour résoudre le problème d’Adobe Commerce avec un affichage de l’arborescence des catégories sur plus de quatre profondeurs d’imbrication et reflétant les relations ancre/non-ancre.
feature: Categories, Page Content
role: Admin, Developer
source-git-commit: af8b7b44274b828b3f60f92fd78f9f3d3983abb8
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 0%

---


# ACP2E-3689 : plusieurs problèmes avec l’arborescence des catégories s’affichent à des niveaux plus profonds et reflètent les relations ancre/non-ancre

>[!NOTE]
>
>Ce correctif remplace le [ACSD-62689](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-57/acsd-62689-customer-add-categories-issue-related-product-rules-and-widgets.md) pour les versions 2.4.7 et ultérieures.

Le correctif ACP2E-3689 corrige plusieurs problèmes d’affichage de l’arborescence des catégories sur une imbrication de plus de profondeur quatre et reflète les relations ancre/non-ancre. Ce correctif est disponible lorsque la version 1.1.61 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACP2E-3689. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.7-p3

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.7 - 2.4.7-p4

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

L’arborescence de catégories à des niveaux plus profonds (4+) ne s’affiche pas correctement et reflète les relations ancre/non-ancre.

<u>Procédure à suivre </u> :

1. Configurez une arborescence de catégories avec des catégories imbriquées de plus de 4 niveaux.
1. Développez l’arborescence de catégories dans Admin qui s’affiche à différents emplacements :
   1. Configurez une [!UICONTROL Related Products Rule] et définissez une condition basée sur des catégories.
   1. Créez un widget et, dans [!UICONTROL Layout Updates], sélectionnez [!UICONTROL Anchor categories].

<u>Résultats attendus</u> :

Tous les niveaux de l’arborescence des catégories s’affichent correctement.

<u>Résultats réels</u> :

Seuls les premiers niveaux (&lt;4) de l&#39;arborescence des catégories sont disponibles.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
