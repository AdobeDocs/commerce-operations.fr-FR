---
title: 'ACSD-62591 : le thème ne change pas lorsque **[!UICONTROL User Agent Rules]** est configuré'
description: Appliquez le correctif ACSD-62591 pour résoudre le problème d’Adobe Commerce en raison duquel le thème ne change pas correctement lorsque les **[!UICONTROL User Agent Rules]** sont configurés.
feature: Themes
role: Admin, Developer
source-git-commit: 319ac7ea1fb8f33f4ed7bfa440477cf6d6657cb5
workflow-type: tm+mt
source-wordcount: '308'
ht-degree: 0%

---


# ACSD-62591 : le thème ne change pas correctement lorsqu’[!UICONTROL User Agent Rules] est configuré

Le correctif ACSD-62591 corrige le problème en raison duquel le thème ne change pas correctement lorsque les **[!UICONTROL User Agent Rules]** sont configurés. Ce correctif est disponible lorsque la version 1.1.55 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-62591. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**
* Adobe Commerce (toutes les méthodes de déploiement) 2.4.7-p3

**Compatible avec les versions d’Adobe Commerce :**
* Adobe Commerce (toutes les méthodes de déploiement) 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le thème ne change pas correctement lorsque les **[!UICONTROL User Agent Rules]** sont configurés.

<u>Procédure à suivre </u> :

1. Ouvrez **[!UICONTROL Admin]** Commerce > **[!UICONTROL Content]** > **[!UICONTROL Design]** > **[!UICONTROL Configuration]**.
1. Modifiez un thème d’affichage de magasin.
1. Définissez `/iPhone|iPod|BlackBerry|Palm|Googlebot-Mobile|Mobile|mobile|mobi|Windows Mobile|Safari Mobile|Android|Opera Mini/i` dans **[!UICONTROL User Agent Rules]** et choisissez un autre thème.
1. Enregistrez les modifications et effacez les caches.
1. Ouvrez une page Storefront sur un appareil mobile.
1. Ouvrez la même page à partir d’un navigateur de bureau.

<u>Résultats attendus</u> :

Le navigateur de bureau et l’appareil mobile affichent des pages en utilisant leurs thèmes respectifs.

<u>Résultats réels</u> :

Le navigateur de bureau affiche la page mise en cache avec le thème mobile.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-Premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .


## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
