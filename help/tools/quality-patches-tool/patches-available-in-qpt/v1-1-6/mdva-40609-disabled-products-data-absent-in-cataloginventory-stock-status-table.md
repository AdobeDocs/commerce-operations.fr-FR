---
title: 'MDVA-40609 : données des produits désactivées absentes de la table cataloginventory_stock_status'
description: Le correctif MDVA-40609 résout le problème en raison duquel les données des produits désactivés ne s’affichent pas dans la table d’index `cataloginventory_stock_status`, ce qui entraîne l’affichage de quantités de produits incorrectes. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.6 est installé. L’ID de correctif est MDVA-40609. Veuillez noter que le problème a été corrigé dans Adobe Commerce 2.4.3.
feature: Catalog Management, Inventory, Orders, Products
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '418'
ht-degree: 0%

---

# MDVA-40609 : Désactivation des données de produits absentes dans la table cataloginventory_stock_status

Le correctif MDVA-40609 résout le problème en raison duquel les données des produits désactivés ne s’affichent pas dans la table d’index `cataloginventory_stock_status`, ce qui entraîne l’affichage de quantités de produits incorrectes. Ce correctif est disponible lorsque l’ [outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.6 est installé. L’ID de correctif est MDVA-40609. Veuillez noter que le problème a été corrigé dans Adobe Commerce 2.4.3.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2 - 2.4.2-p2

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les données des produits désactivés ne s’affichent pas dans la table d’index `cataloginventory_stock_status`, ce qui entraîne l’affichage de quantités de produits incorrectes.

<u>Conditions préalables</u> :

Le module Inventaire est installé.

<u>Étapes à reproduire</u> :

1. Configurez deux sites web avec des magasins et des vues de magasin.
1. Créez une source et un stock supplémentaires.
1. Ajoutez un produit simple :
   * Définissez Activer le produit sur *Non*.
   * Attribuez deux sources avec l’état de l’élément Source = En stock et Qté supérieur à zéro.
1. Enregistrez le produit.
1. Vérifiez l’onglet **Quantité commercialisable de produit** .

<u>Résultats attendus</u> :

Les deux stocks ont des valeurs saisies supérieures à zéro.

<u>Résultats réels</u> :

Un stock a une valeur nulle.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [ L’outil de correctifs de qualité est sorti : un nouvel outil pour les correctifs de qualité en libre-service ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!DNL Quality Patches Tool].

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) .
