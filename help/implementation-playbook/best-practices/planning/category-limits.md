---
title: Bonnes pratiques relatives à la configuration des catégories
description: Découvrez les bonnes pratiques pour optimiser les performances du site en limitant le nombre de catégories dans le catalogue.
role: Admin
feature: Best Practices
feature-set: Commerce
source-git-commit: e156fcafc5792036b37d9b199b870f1888c3f1ff
workflow-type: tm+mt
source-wordcount: '235'
ht-degree: 0%

---


# Bonnes pratiques relatives à la configuration des catégories

Pour de meilleures performances, ne configurez pas plus de catégories que le nombre maximal recommandé de catégories pour les sites Adobe Commerce.

- Pour Adobe Commerce version 2.4.2 et ultérieure, configurez un maximum de 6 000 catégories.
- Pour Adobe Commerce versions 2.3.x et 2.4.0 à 2.4.1-p1, configurez un maximum de 3 000 catégories.

## Produits et versions concernés

[Toutes les versions prises en charge](../../../release/versions.md) de :

- Adobe Commerce sur l’infrastructure cloud
- Adobe Commerce sur site

## Réduction du nombre de produits

Utilisez les stratégies suivantes pour réduire le nombre de catégories :

- Gestion des fonctionnalités de produit uniques par le biais d’attributs et d’options personnalisées
- Suppression des catégories inactives
- Optimiser la profondeur de catalogue dans la navigation

## Incidences sur les performances potentielles

Le fait d’avoir plus de catégories que le nombre maximal recommandé peut affecter les performances du site de la manière suivante :

- Augmentation tangible du temps de réponse pour les pages de catalogue non mises en cache
- Longue exécution et délais d’expiration lors de la gestion des catégories depuis l’administrateur
- Augmentation de la taille des tables de base de données correspondantes
- Les tables d’index plus volumineuses augmentent le temps nécessaire à la réalisation des opérations d’indexation pour la variable `[category/product relation index\]`
- Amélioration du temps de traitement pour terminer les opérations de création d’arborescence de catégories, de récupération de menus et de gestion des règles de catégorie

## Informations supplémentaires

- [Présentation des catégories](https://experienceleague.adobe.com/docs/commerce-admin/catalog/categories/categories.html)
- [Présentation de la navigation](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/navigation/navigation.html)
- [Affectations de produit](https://experienceleague.adobe.com/docs/commerce-admin/catalog/categories/products-in-category/categories-product-assignments.html)
- [Adobe Commerce sur l’infrastructure cloud : Bonnes pratiques pour la configuration du magasin](https://devdocs.magento.com/cloud/configure/configure-best-practices.html)
