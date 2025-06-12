---
title: 'ACSD-51899 : l’adresse d’expédition par défaut n’est pas correctement renseignée'
description: Appliquez le correctif ACSD-51899 pour résoudre le problème d’Adobe Commerce où l’adresse d’expédition par défaut est automatiquement renseignée avec une adresse incorrecte.
feature: Checkout
role: Admin
exl-id: 14e48613-6af8-476c-978d-87c27a0b0d15
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 0%

---

# ACSD-51899 : l’adresse d’expédition par défaut n’est pas correctement renseignée

Le correctif ACSD-51899 corrige le problème en raison duquel l’adresse d’expédition par défaut est automatiquement renseignée avec une adresse incorrecte. Ce correctif est disponible lorsque la version 1.1.35 de [!DNL Quality Patches Tool (QPT)] est installée. L’ID du correctif est ACSD-51899. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4-p3

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.0 - 2.4.6-p1

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

L’adresse d’expédition par défaut est automatiquement renseignée avec une adresse incorrecte

<u>Procédure à suivre </u> :

1. Activez **En magasin - Récupération** sous le mode d’expédition.
1. Créez *stock* et *source*.
1. Créez un produit et affectez-le à la source.
1. Ajouter un produit au panier.
1. Cliquez sur **Passer en caisse** dans le mini-panier.
1. Saisissez l’adresse e-mail de test et sélectionnez **Choisir en magasin**.
1. Cliquez sur le bouton **Sélectionner une boutique**, puis sélectionnez l’emplacement de la boutique à sélectionner.
1. Cliquez sur le bouton **suivant**.
1. Accédez à la **Page d’accueil** en cliquant sur le logo de la boutique.
1. Ouvrez le **Mini panier**.
1. Cliquez sur le lien hypertexte inférieur nommé **Afficher et modifier le panier**.
1. Cliquez sur **Passer en caisse**.
1. Cliquez sur le bouton d&#39;expédition de la page d&#39;expédition.

<u>Résultats attendus</u>

Le champ Adresse de livraison reste vide, à l’exception de *Pays, région et code postal*.

<u>Résultats réels</u>

L’adresse de livraison par défaut est automatiquement renseignée avec l’adresse *ramassage en magasin* après actualisation de la page.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
