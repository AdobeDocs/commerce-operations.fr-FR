---
title: 'ACSD-63090 : la suppression d’un produit d’Admin vide le panier'
description: Appliquez le correctif ACSD-63090 pour résoudre le problème d’Adobe Commerce où les articles du panier d’un client ont disparu suite à la suppression d’un produit après son ajout au panier.
feature: Shopping Cart, Quotes
role: Admin, Developer
exl-id: c07778cb-390f-4202-9539-7bb159e4b714
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 0%

---

# ACSD-63090 : la suppression d’un produit d’Admin vide le panier

Le correctif ACSD-63090 résout le problème où les articles du panier d’un client ont disparu suite à la suppression d’un produit par l’administrateur, après son ajout au panier. Ce correctif est disponible lorsque la version 1.1.58 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-63090. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p8

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les articles du panier disparaissent lorsqu’un produit est supprimé après avoir été ajouté au panier.

<u>Procédure à suivre </u> :

1. Créez un produit configurable avec deux produits enfants.
1. Connectez-vous en tant que client enregistré.
1. Ajoutez les deux produits enfants au panier.
1. Déconnectez-vous du compte .
1. Supprimez l’un des produits enfants du catalogue.
1. Mettez à jour le prix de l’autre produit enfant en utilisant l’API .

<u>Résultats attendus</u> :

Le produit restant est affiché dans le panier et le devis existant est mis à jour dans le tableau de la base de données `quote`.

<u>Résultats réels</u> :

* Le mini panier est vide.
* Un nouvel enregistrement de devis est généré dans la table de base de données `quote`.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
