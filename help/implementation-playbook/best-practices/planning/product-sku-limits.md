---
title: Bonnes pratiques relatives aux limites de produit
description: Découvrez les bonnes pratiques de configuration des unités de gestion des stocks de produits (SKU) afin d’optimiser les performances du site.
role: Admin
feature: Best Practices
feature-set: Commerce
source-git-commit: 510f2d4cdaec1034cb04a01fab0948c4261c6d10
workflow-type: tm+mt
source-wordcount: '267'
ht-degree: 0%

---


# Bonnes pratiques relatives à la configuration du SKU du produit

Pour optimiser les performances, la valeur maximale recommandée pour les unités de gestion du stockage des produits (SKU) efficaces est de 10 millions. Ce produit maximum effectif est calculé comme suit :

`Effective SKU = N\[SKUs\] * Stores/Websites * Customer Groups`

Le fait d’avoir plus que le nombre maximal de SKU efficaces ralentit la récupération des données de produit et augmente le délai d’exécution des opérations d’administration.

## Produits et versions concernés

[Toutes les versions prises en charge](../../../release/versions.md) de :

- Adobe Commerce sur l’infrastructure cloud
- Adobe Commerce sur site

## Réduction du nombre de produits

Utilisez les stratégies suivantes pour réduire le nombre de produits (SKU) :

- Minimiser les multiplicateurs —
   - Déplacer des magasins ou des sites web réduit le multiplicateur. Si vous disposez de 50 000 SKU, de dix sites web et de dix groupes de clients, le nombre effectif de SKU est de 5 millions. La suppression de cinq groupes clients réduit les SKU en vigueur à 2,5 millions.
   - Utilisez d’autres fonctionnalités de produit pour la tarification personnalisée afin de remplacer le catalogue partagé et les multiplicateurs de groupes de clients.
- Restructurer le catalogue —
   - Réduire le nombre de produits affectés aux catégories.
   - Réduire le nombre de SKU en réduisant le nombre de magasins, de sites web, de groupes de clients ou le nombre de produits.
- Fournissez d’autres variations de produit en utilisant des options personnalisées au lieu de créer des produits distincts.
- Désactivez ou supprimez les composants système inutilisés tels que les modules. (Voir  [Désinstallation des modules](../../../installation/tutorials/uninstall-modules.md).)
- Gérez les produits dans un système de gestion de plateforme externe (PMS).

## Informations supplémentaires

- [Création d’un produit](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/product-create.html)
- [Affectations de produit](https://experienceleague.adobe.com/docs/commerce-admin/catalog/categories/products-in-category/categories-product-assignments.html)
- infrastructure cloud : [Configuration de plusieurs sites web et magasins](https://devdocs.magento.com/cloud/project/project-multi-sites.html)
- Sur site : [Plusieurs sites web ou magasins](../../../configuration/multi-sites/ms-overview.md)
- [Adobe Commerce sur l’infrastructure cloud : Bonnes pratiques pour la configuration du magasin](https://devdocs.magento.com/cloud/configure/configure-best-practices.html)
