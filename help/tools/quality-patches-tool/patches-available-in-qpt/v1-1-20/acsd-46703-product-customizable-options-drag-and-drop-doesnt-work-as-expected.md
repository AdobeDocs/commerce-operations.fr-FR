---
title: 'ACSD-46703 : le glisser-déposer de la personnalisation du produit ne fonctionne pas'
description: Cet article fournit une solution au problème de fonctionnement inattendu du glisser-déposer des options personnalisables du produit.
feature: Products
role: Developer
exl-id: 38b9490a-c9d4-4f8e-b90f-69bf50a6b571
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '375'
ht-degree: 0%

---

# ACSD-46703 : le glisser-déposer de la personnalisation du produit ne fonctionne pas

Le correctif ACSD-46703 corrige le problème en raison duquel les options personnalisables du produit (glisser-déposer) ne fonctionnent pas comme prévu. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) version 1.1.20 est installé. L’ID du correctif est ACSD-46703. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.6.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.5

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec les nouvelles versions de l’[outil de correctifs de qualité]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les utilisateurs ne peuvent pas faire glisser les options personnalisables d’une page à une autre.

<u>Procédure à suivre </u> :

1. Créez un produit simple.
1. Ajoutez des options personnalisables au produit simple et veillez à ajouter plus de 20 options pour obtenir une pagination.
1. Essayez de déplacer une option personnalisable (glisser-déposer) dans la même page.
1. Essayez maintenant de déplacer une option personnalisable de la page 2 vers la page 1.

<u>Résultats attendus</u> :

* Vous pouvez faire glisser les options personnalisables d’une page à une autre.
* Vous pouvez trier les valeurs à l’aide de la fonctionnalité de glisser-déposer, même pour plusieurs pages.

<u>Résultats réels</u> :

Vous ne pouvez déplacer aucune valeur vers une autre page à l’aide de la fonctionnalité de glisser-déposer.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [Outils de correctifs de qualité > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de l’outil de correctifs de qualité.
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
