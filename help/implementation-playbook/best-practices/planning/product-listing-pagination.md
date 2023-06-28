---
title: Bonnes pratiques relatives à la pagination pour les listes de produits
description: Découvrez comment optimiser les performances d’Adobe Commerce en gérant le nombre de produits qui s’affichent sur chaque page du catalogue storefront.
role: User, Admin
feature: Best Practices, Catalogs
exl-id: 473f23a9-53fb-41a6-9b3a-af7bd1208be0
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '176'
ht-degree: 0%

---

# Bonnes pratiques relatives à la pagination pour les listes de produits

Pour de meilleures performances, affichez un maximum de 48 produits par page.

Vous pouvez configurer Adobe Commerce pour permettre aux acheteurs d’afficher tous les produits de catégorie sur une seule page. Si le nombre de produits de catégorie dépasse de manière significative 48 produits, mettez à jour la configuration du catalogue pour les contrôles de pagination du storefront.

## Produits et versions concernés

[Toutes les versions prises en charge](../../../release/versions.md) de :

- Adobe Commerce sur l’infrastructure cloud
- Adobe Commerce sur site

## Mettre à jour la configuration de la liste de produits

Si vous avez plus de 48 produits dans une catégorie, mettez à jour la configuration du catalogue storefront pour désactiver l’option sur **Autoriser tous les produits par page**.

Après avoir désactivé cette option, Adobe Commerce utilise les commandes de pagination storefront de la liste de produits pour gérer le nombre de produits qui s’affichent dans les composants storefront. Pour obtenir des instructions, voir [Configuration des contrôles de pagination](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/navigation/navigation-product-listings.html#configure-the-pagination-controls).

## Informations supplémentaires

- [Configuration des listes de produits](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/navigation/navigation-product-listings.html)
