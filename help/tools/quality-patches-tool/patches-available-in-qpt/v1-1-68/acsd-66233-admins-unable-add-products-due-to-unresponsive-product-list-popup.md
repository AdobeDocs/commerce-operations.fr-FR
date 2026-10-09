---
title: 'ACSD-66233 : les administrateurs ne peuvent pas ajouter de produits en raison d’une fenêtre contextuelle de liste de produits qui ne répond pas'
description: Appliquez le correctif ACSD-66233 pour résoudre le problème d’Adobe Commerce en raison duquel les administrateurs et administratrices ne peuvent pas ajouter de produits aux catégories, car la fenêtre contextuelle [!UICONTROL Add Product] dans Visual Merchandiser se charge indéfiniment.
feature: Inventory, Merchandising
role: Admin, Developer
type: Troubleshooting
exl-id: 2e01e62d-b6f9-4aa5-9040-7908aa83d422
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 8dc0e58b-adf0-51bb-8db5-bb36e3e656fb
    internal-label: Inventory
  - id: 58c984c2-e237-5c50-9718-500e40d1e82c
    internal-label: Merchandising
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '377'
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
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/fr/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
