---
title: 'ACSD-66233 : les administrateurs ne peuvent pas ajouter de produits en raison d’une fenêtre contextuelle de liste de produits qui ne répond pas'
description: Appliquez le correctif ACSD-66233 pour résoudre le problème d’Adobe Commerce en raison duquel les administrateurs et administratrices ne peuvent pas ajouter de produits aux catégories, car la fenêtre contextuelle [!UICONTROL Add Product] dans Visual Merchandiser se charge indéfiniment.
feature: Inventory, Merchandising
role: Admin, Developer
type: Troubleshooting
source-git-commit: 165b62a875747a846b15f8f86b036e67704ebc8e
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 0%

---


# ACSD-66233 : les administrateurs ne peuvent pas ajouter de produits en raison d’une fenêtre contextuelle de liste de produits qui ne répond pas

Le correctif ACSD-66233 corrige un problème en raison duquel les administrateurs ne peuvent pas ajouter de produits aux catégories, car la fenêtre contextuelle [!UICONTROL Add Product] dans Visual Merchandiser se charge indéfiniment. Ce correctif est disponible lorsque la version 1.1.68 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-66233. Notez que ce problème doit être résolu dans Adobe Commerce 2.4.9.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.8

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.8 - 2.4.8-p1

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Problème au cours duquel la fenêtre contextuelle [!UICONTROL Add Product] dans Visual Merchandiser se charge indéfiniment, empêchant les administrateurs d’ajouter des produits aux catégories.

<u>Procédure à suivre </u> :

1. Installation et activation des modules d’inventaire
1. Créez un grand nombre de sources d’inventaire (par exemple, 700).
1. Créez plusieurs stocks de stock (par exemple, 12) et affectez-leur les origines de stock.
1. Créez des produits et affectez-les aux sources d&#39;inventaire.
1. Créez une catégorie.
1. Développez la section [!UICONTROL Products in Category] .
1. Cliquez sur le bouton [!UICONTROL Add Product] .
1. Observez le pop-up avec la liste des produits.

<u>Résultats attendus</u> :

La liste des produits s’affiche dans la fenêtre contextuelle dans un délai raisonnable.

<u>Résultats réels</u> :

La fenêtre contextuelle se charge indéfiniment et n’affiche pas la liste des produits.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
