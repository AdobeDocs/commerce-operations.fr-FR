---
title: Bonnes pratiques relatives aux limites de produit
description: Découvrez les bonnes pratiques de configuration des unités de gestion des stocks de produits (SKU) pour optimiser les performances du site.
role: Admin
feature: Best Practices, Catalog Management
exl-id: 37af7b92-05ac-4a4f-9009-11e8d9f95c2f
source-git-commit: df8878a3fea19b8f1780b5037273e18b5a3f1373
workflow-type: tm+mt
source-wordcount: '356'
ht-degree: 0%

---

# Bonnes pratiques relatives à la configuration du SKU du produit

Pour optimiser les performances, le maximum recommandé pour les unités de gestion du stockage des produits (SKU) efficaces est de 242 millions. Ce maximum de SKU du produit effectif est calculé comme suit :

```text
Effective SKU = N[SKUs] x N[Stores] x N[Customer groups]
```

Où :

- N représente le nombre d’éléments pour cette catégorie.
- Les groupes de clients incluent des catalogues partagés, car ils créent un groupe de clients supplémentaire.

Le fait d’avoir plus que le nombre maximal de SKU efficaces ralentit la récupération des données de produit et augmente le temps nécessaire pour terminer les opérations ou les indexations du panneau d’administration.

## Produits et versions concernés

[Toutes les versions prises en charge](../../../release/versions.md) de :

- Adobe Commerce sur l’infrastructure cloud
- Adobe Commerce sur site

## Réduction du nombre de produits

Utilisez les stratégies suivantes pour réduire le nombre de produits (SKU) :

- Minimiser les multiplicateurs —
   - La consolidation des sites web réduit le multiplicateur. Si vous disposez de 50 000 SKU, de dix sites web et de dix groupes de clients, le nombre effectif de SKU est de 5 millions. La suppression de cinq groupes clients réduit les SKU en vigueur à 2,5 millions.
   - Utilisez d’autres fonctionnalités de produit pour la tarification personnalisée afin de remplacer le catalogue partagé et les multiplicateurs de groupes de clients.
   - Les groupes de clients et le catalogue partagé fonctionnent tous deux comme des multiplicateurs pour le nombre de SKU efficaces dans un magasin.
- Restructurer le catalogue —
   - Réduire le nombre de produits affectés aux catégories.
   - Réduire le nombre de SKU en réduisant le nombre de sites web, de groupes de clients, de catalogues partagés, de produits ou d’options de produits configurables
- Fournissez d’autres variations de produit en utilisant des options personnalisées au lieu de créer des produits distincts.
- Prise en compte du fait qu’un SKU effectif peut inclure un certain nombre de permutation de prix potentielles, car les prix peuvent être spécifiés différemment selon chaque magasin ou groupe de clients.
- Désactivez ou supprimez les composants système inutilisés tels que les modules. (Voir  [Désinstallation des modules](../../../installation/tutorials/uninstall-modules.md).)
- Gérez les produits dans un système de gestion de plateforme externe (PMS).

## Informations supplémentaires

- [Création d’un produit](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/product-create.html)
- [Affectations de produit](https://experienceleague.adobe.com/docs/commerce-admin/catalog/categories/products-in-category/categories-product-assignments.html)
- [Utilisation de catalogues partagés](https://experienceleague.adobe.com/docs/commerce-admin/b2b/shared-catalogs/catalog-shared.html)
- infrastructure cloud : [Configuration de plusieurs sites web et magasins](https://devdocs.magento.com/cloud/project/project-multi-sites.html)
- Sur site : [Plusieurs sites web ou magasins](../../../configuration/multi-sites/ms-overview.md)
- [Adobe Commerce sur l’infrastructure cloud : bonnes pratiques pour la configuration du magasin](https://devdocs.magento.com/cloud/configure/configure-best-practices.html)
