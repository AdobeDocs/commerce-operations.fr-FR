---
title: 'ACSD-62629 : la liste de produits dans les widgets affiche des catégories incorrectes'
description: Appliquez le correctif ACSD-62629 pour résoudre le problème d’Adobe Commerce en raison duquel une liste de produits utilisée dans des widgets ne respecte pas la condition de catégorie.
feature: Page Content
role: Admin, Developer
exl-id: a7d6bd43-4b8b-48c4-ae9a-4093ac3a4110
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 0%

---

# ACSD-62629 : la liste de produits dans les widgets affiche des catégories incorrectes

Le correctif ACSD-62629 corrige le problème en raison duquel la liste de produits utilisée dans les widgets ne respecte pas la condition de catégorie. Ce correctif est disponible lorsque la version 1.1.57 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-62629. Notez que ce problème doit être résolu dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.7-p2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La liste de produits utilisée dans les widgets ne respecte pas la condition de catégorie.

<u>Procédure à suivre </u> :

1. Créez un [!UICONTROL simple product] nommé TEST et ajoutez-le à la catégorie 1.
1. Créez une mise à jour d’évaluation sans date de fin pour le produit TEST. Patientez jusqu’à ce que la mise à jour soit active.
1. Créez un [!UICONTROL configurable product] nommé TEST 2 avec deux produits enfants et ajoutez-le à la catégorie 2.
1. Créez un autre [!UICONTROL simple product] nommé TEST 5 et ajoutez-le à la catégorie 1.
1. Exécutez une réindexation complète.
1. Accédez à **[!UICONTROL Content]** > **[!UICONTROL Elements]** > **[!UICONTROL Pages]** et modifiez la page d’accueil.
1. Ajoutez un widget [!UICONTROL Products] avec *[!UICONTROL Appearance]* défini sur *[!UICONTROL Product Carousel]* et *[!UICONTROL Category]* défini sur Catégorie 2. Enregistrez la page.
1. Accédez au serveur frontal et ouvrez la page d’accueil.

<u>Résultats attendus</u> :

Seul le produit TEST 2 (configurable) doit être présent sur la page.

<u>Résultats réels</u> :

Les produits TEST 5 (simple) et TEST 2 (configurable) sont tous deux présents sur la page.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .


## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
