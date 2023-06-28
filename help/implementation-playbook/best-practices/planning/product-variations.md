---
title: Bonnes pratiques de configuration des variations de produit
description: Découvrez comment optimiser les performances d’Adobe Commerce en limitant le nombre de variations de produit configurées.
role: Admin
feature: Best Practices, Catalogs
exl-id: a19dd8b4-23b8-498f-be51-a0adfcd12a11
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '198'
ht-degree: 0%

---

# Bonnes pratiques relatives à la configuration des variations de produit

Pour de meilleures performances, configurez un maximum de 50 variations par produit.

## Produits et versions concernés

[Toutes les versions prises en charge](../../../release/versions.md) de :

- Adobe Commerce sur l’infrastructure cloud
- Adobe Commerce sur site

## Réduction du nombre de variations de produits

Pour de meilleures performances du site, utilisez les stratégies suivantes afin de réduire le nombre de variations de produits :

- Restructurez le catalogue en répartissant le nombre de variations entre différents produits.
- Supprimez les options d’attribut configurables qui ne sont pas en stock.
- Gérez les variations par le biais d’autres fonctionnalités telles que les options personnalisées, les catégories, les produits associés, regroupés et les produits de regroupement.

## Impact potentiel sur les performances

Le dépassement du nombre recommandé de variations de produit peut affecter les performances du site des manières suivantes :

- Délais de demande et de rendu longs sur les pages de détails et de catégorie d’un produit contenant des produits complexes.
- Amélioration du temps de réponse pour terminer les opérations d’enregistrement dans l’administrateur.
- Amélioration du temps d’affichage du formulaire de modification du produit.
- Passage en caisse lent.

## Informations supplémentaires

- [Créer des produits configurables](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/types/product-create-configurable.html)
- [Création d’un produit](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/product-create.html)

- Formation—[Gestion des catalogues et des produits à l’aide d’Adobe Commerce](https://learning.adobe.com/catalog/adobe_commerce/cours000000000098643.html)
