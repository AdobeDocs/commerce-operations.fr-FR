---
title: 'ACSD-44851 : catégorie dont les sous-catégories ne peuvent pas s''ouvrir ni se développer'
description: Cet article fournit une solution au problème en raison duquel l’utilisateur ne peut pas ouvrir ou développer une catégorie avec des sous-catégories.
feature: Categories
role: Admin
exl-id: c1ad13d8-94e1-47cf-ad65-9bc5ce1c26ad
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 0%

---

# ACSD-44851 : catégorie dont les sous-catégories ne peuvent pas s&#39;ouvrir ni se développer

Le correctif ACSD-44851 résout le problème où l’utilisateur ne peut pas ouvrir ou développer une catégorie avec des sous-catégories. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) version 1.1.20 est installé. L’ID du correctif est ACSD-44851. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.6.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.0 - 2.4.5

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

L’utilisateur ne peut pas ouvrir ni développer une catégorie avec des sous-catégories.

<u>Procédure à suivre </u> :

1. Dans Adobe Commerce Admin, créez une arborescence de catégories avec deux catégories racines et quelques sous-catégories pour chacune d’elles.
1. Ouvrez l’émulateur ou la vue mobile ou réduisez la largeur de fenêtre jusqu’à ce que la disposition devienne mobile.
1. Ouvrez le menu principal du catalogue.
1. Essayez de développer les catégories racine.
1. Essayez d’ouvrir la catégorie.

<u>Résultats attendus</u> :

Le menu est accessible.

<u>Résultats réels</u> :

Le deuxième niveau du menu mobile ne s’ouvre pas.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [Outils de correctifs de qualité > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de l’outil de correctifs de qualité.

* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
