---
title: 'ACSD-62689 : impossible d’ajouter des catégories dans les [!UICONTROL Related Product Rules] et les widgets après la profondeur 4'
description: Appliquez le correctif ACSD-62689 pour résoudre le problème d’Adobe Commerce en raison duquel un client ne peut pas ajouter de catégories dans les [!UICONTROL Related Product Rules] et les widgets après l’imbrication de profondeur 4.
feature: Categories
role: Admin, Developer
exl-id: 2506744a-01c8-462b-9a27-cd0bdb5664f9
source-git-commit: e18a41c5abb1cc8b407ff6c188acdeed0e8a7659
workflow-type: tm+mt
source-wordcount: '373'
ht-degree: 0%

---

# ACSD-62689 : impossible d’ajouter des catégories dans les *[!UICONTROL Related Product Rules]* et les widgets après la profondeur 4

Le correctif ACSD-62689 corrige le problème en raison duquel un client ne peut pas ajouter de catégories dans les *[!UICONTROL Related Product Rules]* et les widgets après l’imbrication de profondeur 4. Ce correctif est disponible lorsque la version 1.1.57 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-62689. Notez que ce problème doit être résolu dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.7-p3

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Un client ne peut pas ajouter de catégories dans les *[!UICONTROL Related Product Rules]* et les widgets après l’imbrication de profondeur 4.

<u>Procédure à suivre </u> :

1. Créez deux catégories appelées *[!UICONTROL Anchor]* et *[!UICONTROL Non-Anchor]* sous la catégorie racine par défaut.
   * Assurez-vous que l’indicateur *[!UICONTROL Is Anchor]* est désactivé pour la catégorie *[!UICONTROL Non-Anchor]*.
1. Accédez à **[!UICONTROL Content]** > **[!UICONTROL Widgets]** et créez un widget.
1. Sous *[!UICONTROL Layout Updates]*, sélectionnez **[!UICONTROL Non-Anchor Categories]** dans le champ *[!UICONTROL Display on]* .
1. Cliquez sur **[!UICONTROL Specific Categories]**.
1. Cliquez sur l’icône de sélection de catégorie.
1. Développez la catégorie racine .
1. Vérifiez les catégories. Les deux doivent être désactivés et non sélectionnables.
1. Sous *[!UICONTROL Layout Updates]*, sélectionnez **[!UICONTROL Anchor Categories]** dans le champ *[!UICONTROL Display on]* . Suivez ensuite les étapes 5 et 6.
1. Vérifiez les catégories. Les deux doivent être activés et sélectionnables.

<u>Résultats attendus</u> :

À l’étape 7, seule la catégorie *[!UICONTROL Non-Anchor]* doit pouvoir être sélectionnée. À l’étape 9, la catégorie *[!UICONTROL Anchor]* doit pouvoir être sélectionnée.

<u>Résultats réels</u> :

À l’étape 7, les deux catégories ne sont pas sélectionnables. À l’étape 9, les deux catégories peuvent être sélectionnées.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-Premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .


## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .

