---
title: Bonnes pratiques relatives à la configuration des promotions
description: Découvrez les bonnes pratiques relatives à la configuration des règles de vente et des codes de bon afin d’optimiser les performances de la boutique de commerce.
role: User
feature: Best Practices, Price Rules, Shopping Cart
exl-id: 6e177836-b8da-4e55-842c-e12ff54ffaf5
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '252'
ht-degree: 0%

---

# Bonnes pratiques relatives à la configuration des promotions

Pour de meilleures performances, suivez les bonnes pratiques suivantes pour configurer les ventes et les promotions pour les articles d’un panier :

- **Règles de vente (règles de prix du panier)**- Ne configurer pas plus de 1 000 règles de prix de panier pour tous les sites web
   - Gérez et supprimez les règles inutilisées.
   - Ajoutez des conditions de règle strictes (comme un filtre d’attribut ou de catégorie) pour une correspondance plus efficace.
- **Coupons**—
   - Vérifiez que le nombre total de coupons dans la base de données est inférieur à 250 000.
   - Supprimez les bons inutilisés et expirés.
   - Générez uniquement le nombre de coupons nécessaires pour répondre aux besoins de l&#39;opération.

## Produits et versions concernés

[Toutes les versions prises en charge](../../../release/versions.md) de :

- Adobe Commerce sur l’infrastructure cloud
- Adobe Commerce sur site

## Incidences sur les performances potentielles

Le fait d’avoir plus que le nombre maximal recommandé de règles de prix de panier ou de bons d’achat peut affecter les performances du site des manières suivantes :

- Amélioration du temps de réponse lorsque des produits sont ajoutés au panier.
- Amélioration du temps de chargement et du rendu du minicart.
- Augmentation du temps pour le rendu de la page de panier.
- Augmentation du temps pour le rendu de la variable **Totaux** sur la page Passage en caisse .
- La demande de coupons peut prendre plus de 2 secondes.

## Informations supplémentaires

- [Présentation des campagnes et promotions marketing](https://devdocs.magento.com/cloud/configure/configure-best-practices.html#campaigns)
- [Règles de prix du panier](https://experienceleague.adobe.com/docs/commerce-admin/marketing/promotions/cart-rules/price-rules-cart.html)
- [Tutoriel : Créer une règle de prix de panier](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/marketing/cart-price-rules.html)
- [Codes coupon](https://experienceleague.adobe.com/docs/commerce-admin/marketing/promotions/cart-rules/price-rules-cart-coupon.html)
- [Adobe Commerce sur l’infrastructure cloud : Bonnes pratiques pour la configuration du magasin](https://devdocs.magento.com/cloud/configure/configure-best-practices.html)
