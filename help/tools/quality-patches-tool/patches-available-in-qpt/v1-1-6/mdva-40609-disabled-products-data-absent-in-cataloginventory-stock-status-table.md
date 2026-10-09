---
title: 'MDVA-40609 : données de produits désactivés absentes de la table cataloginventory_stock_status'
description: Le correctif MDVA-40609 résout le problème où les données des produits désactivés ne sont pas affichées dans la table d’index « cataloginventory_stock_status », ce qui entraîne l’affichage de quantités de produits incorrectes. Ce correctif est disponible lorsque l’outil [Outil de correctifs de la qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.6 est installé. L’ID du correctif est MDVA-40609. Notez que le problème a été résolu dans Adobe Commerce 2.4.3.
feature: Catalog Management, Inventory, Orders, Products
role: Admin
exl-id: e207ee55-b6ce-4065-bae1-2be89dcf5092
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: c18ed297-2187-4aec-affb-9d9654eca6fc
    internal-label: Catalog management
  - id: 8dc0e58b-adf0-51bb-8db5-bb36e3e656fb
    internal-label: Inventory
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '452'
ht-degree: 0%
---
# MDVA-40609 : données de produits désactivés absentes de la table cataloginventory_stock_status

Le correctif MDVA-40609 résout le problème où les données des produits désactivés ne s’affichent pas dans la table d’index `cataloginventory_stock_status`, ce qui entraîne l’affichage de quantités de produits incorrectes. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.6 est installé. L’ID du correctif est MDVA-40609. Notez que le problème a été résolu dans Adobe Commerce 2.4.3.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2 - 2.4.2-p2

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les données des produits désactivés ne s’affichent pas dans le tableau d’index `cataloginventory_stock_status`, ce qui entraîne l’affichage de quantités de produits incorrectes.

<u>Conditions préalables</u> :

Le module Inventaire est installé.

<u>Procédure à suivre </u> :

1. Configurez deux sites web avec des magasins et des vues de magasin.
1. Créez une source et un stock supplémentaires.
1. Ajoutez un produit simple :
   * Définissez Activer le produit sur *Non*.
   * Affectez deux origines avec Statut article Source = En stock et Qté supérieure à zéro.
1. Enregistrez le produit.
1. Vérifiez l&#39;onglet **Quantité de produit commercialisable**.

<u>Résultats attendus</u> :

Les deux stocks ont des valeurs saisies supérieures à zéro.

<u>Résultats réels</u> :

Un stock a une valeur nulle.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur l’outil de correctifs de la qualité, voir :

* Publication de l’outil [Correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) un nouvel outil permettant d’appliquer des correctifs de qualité en libre-service dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!DNL Quality Patches Tool].

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-).
