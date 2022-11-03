---
title: Bonnes pratiques relatives au panier de produits
description: Découvrez comment optimiser les performances d’Adobe Commerce en limitant le nombre de produits d’un panier.
role: User
feature: Best Practices
feature-set: Commerce
source-git-commit: 85f9355d0e8c704be3760334b07414d3e15b3b97
workflow-type: tm+mt
source-wordcount: '282'
ht-degree: 0%

---


# Bonnes pratiques relatives à la gestion du panier de produits

Pour de meilleures performances, suivez les instructions suivantes pour gérer les limites de panier pour Adobe Commerce et Magento Open Source :

- Pour les versions 2.3.x à 2.4.2, autorisez un maximum de 100 produits dans un panier.
- Pour les versions 2.4.3 et ultérieures, l’amélioration des fonctionnalités des règles de vente a augmenté le nombre maximum de paniers à 750.


Pour les versions 2.3.x à 2.4.2, les performances attendues basées sur les limites des articles de panier sont les suivantes :

- Jusqu’à **100** produits d’un panier : le produit fonctionne et atteint les objectifs de performances pour le temps de réponse.
- Jusqu’à **300** produits d’un panier : le produit fonctionne, mais le temps de réponse augmente au-dessus des cibles.
- Dessus **500** produits d’un panier : les flux de panier et de passage en caisse ne sont pas garantis

## Produits et versions concernés

[Toutes les versions prises en charge](../../../release/versions.md) de :

- Adobe Commerce sur l’infrastructure cloud
- Adobe Commerce sur site

## Réduction du nombre d’articles dans le panier

Utilisez les stratégies suivantes pour gérer le nombre d’articles du panier :

- Divisez les commandes en plusieurs commandes plus petites avec un plus petit nombre de lignes à l’aide de la fonction [!UICONTROL Add Item by SKU] fonction .
- Ajoutez uniquement la logique personnalisée et la personnalisation du panier nécessaires au chargement d’une liste d’éléments.

## Incidences sur les performances potentielles

Le fait d’avoir plus que le nombre maximal recommandé de produits dans le panier peut avoir une incidence sur les performances du site des manières suivantes :

- Amélioration du temps de réponse pour les opérations de récupération des données, la validation des articles de panier, les contrôles pour l’application des règles de prix et les calculs des taxes et du total.
- Amélioration du temps de réponse pour le rendu minicart, notamment le rendu des paniers, le flux de passage en caisse et l’exécution.
- Augmentation du temps de chargement pour toutes les pages du site où le minicart est présent.

## Informations supplémentaires

- [Configuration des options du produit](https://experienceleague.adobe.com/docs/commerce-admin/inventory/configuration/product-options.html)
- [Gestion d’un panier](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/point-of-purchase/assist/shopping-assisted-cart-manage.html)
