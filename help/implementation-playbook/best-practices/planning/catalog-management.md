---
title: Bonnes pratiques de gestion des catalogues
description: Découvrez les recommandations relatives à la configuration des limites de panier et des attributs de produit, à la pagination des listes, aux options, aux promotions et aux variations.
role: Developer
feature: Best Practices, Catalog Management
exl-id: 9a672017-9122-4841-a67b-a183224b67dc
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '1403'
ht-degree: 0%

---

# Bonnes pratiques de gestion des catalogues

Les bonnes pratiques de gestion de catalogue décrites ici couvrent un large éventail de problèmes, notamment (mais sans s’y limiter) :

- Limites du panier
- Limites de catégorie
- Attributs de produit
- Pagination de la liste de produits
- Options du produit
- Variantes du produit
- Promotions

## Limites du panier

Pour de meilleures performances, suivez les instructions ci-après afin de gérer les limites du panier pour Adobe Commerce.

### Produits et versions concernés

[Toutes les versions prises en charge](../../../release/versions.md) de :

- Adobe Commerce sur les infrastructures cloud
- Adobe Commerce On-Premise

### Réduire le nombre d’articles du panier

Utilisez les stratégies suivantes pour gérer le nombre d’articles du panier

- Divisez les commandes en plusieurs commandes plus petites avec un plus petit nombre de lignes à l&#39;aide de la fonction [!UICONTROL Add Item by SKU].
- Ajoutez uniquement la logique personnalisée et la personnalisation du panier requises pour charger une liste d’éléments.

## Limites de catégorie

La configuration d’un grand nombre de catégories peut affecter les performances.

### Produits et versions concernés

[Toutes les versions prises en charge](../../../release/versions.md) de :

- Adobe Commerce sur les infrastructures cloud
- Adobe Commerce On-Premise

### Réduire le nombre de produits

Utilisez les stratégies suivantes pour réduire le nombre de catégories :

- Gestion des fonctionnalités de produit uniques par le biais d’attributs et d’options personnalisées
- Supprimer les catégories inactives
- Optimiser la profondeur du catalogue dans la navigation

## Attributs de produit

La configuration d’un trop grand nombre d’attributs de produit ou d’options d’attribut de produit peut affecter les performances.

>[!NOTE]
>
>Les attributs de produit spécifient les fonctionnalités qui s’appliquent globalement à tous les produits. Les options d’attribut de produit sont des personnalisations permettant de spécifier les fonctionnalités qui s’appliquent à des produits spécifiques.

### Produits et versions concernés

[Toutes les versions prises en charge](../../../release/versions.md) de :

- Adobe Commerce sur les infrastructures cloud
- Adobe Commerce On-Premise

### Réduire le nombre d’attributs

Pour des performances optimales lors de la gestion des produits à partir de l’administration et de la récupération des données de produit dans le storefront :

- Utilisez différents modèles de produit (jeux d’attributs) pour différents produits.
- Utilisation d’options personnalisées et de produits complexes pour la gestion des variations
- Réduisez le nombre d’attributs pouvant faire l’objet d’une recherche.
- Supprimez les propriétés de produit qui ne sont pas utilisées.
- Stockez et gérez les attributs non liés au commerce dans des systèmes de gestion de produits externes (PMS).

### Réduire le nombre d’options d’attribut

Pour des performances optimales lors de la gestion des produits à partir de l’administration et de la récupération des données de produit dans le storefront :

- Utilisez différents mécanismes de variation pour créer des produits : des produits complexes et des options personnalisées comme source de variations de produit.
- Créez des modèles de produit spécifiques avec des attributs et des options de ciblage pour éviter les modèles de produit et les conteneurs d’options généralisés.
- Tenez à jour une liste des options d’attribut réelles.
- Gérer les informations sur les produits via un système de gestion des produits (PMS) externe.

### Réduire le nombre de jeux d’attributs

Supprimer les jeux d’attributs de produit inutilisés à l’aide de MySQL.

#### Vérifier la configuration du jeu d’attributs

1. [Connexion à la base de données du site](https://experienceleague.adobe.com/fr/docs/commerce-cloud-service/user-guide/configure/service/mysql#connect-to-the-database).

1. Rechercher le nombre de jeux d’attributs à l’aide de MySQL

   ```sql
   SELECT COUNT(*) AS 'attribute_set' FROM *${TABLE_PREFIX}*eav_attribute_set;
   ```

1. Supprimez tous les jeux d’attributs inutilisés.

### Impact potentiel sur les performances

La configuration de nombreux **attributs de produit** augmente la taille du modèle de produit pour chaque produit (structure EAV) et la quantité de données à récupérer. Cette augmentation affecte les opérations des manières suivantes :

- Augmentation du trafic des requêtes SQL lié à la récupération des données EAV et de la quantité de données traitées, ce qui entraîne une diminution du débit de la base de données
- Augmentation significative de la taille des index Adobe Commerce et de l’index de recherche en texte intégral
- Atteindre les limites strictes de MySQL lors de la création d’un index FLAT pour les modèles de produit surdimensionnés et incapacité à l’utiliser

L’augmentation des données de produit et de la taille des index peut affecter les performances du site des manières suivantes :

- Temps de réponse accru pour la plupart des scénarios de storefront liés à la navigation dans les catalogues, à la recherche (rapide et avancée) et à la navigation par couches.
- Les opérations de gestion des produits dans l’administration ralentissent considérablement, ce qui peut entraîner des délais d’expiration.
- La fonctionnalité des actions en masse de produit peut être bloquée.
- Le temps de reconstruction de l’index pour les catalogues de moyenne et grande taille ne peut pas être effectué quotidiennement en raison des longs délais d’exécution.

La configuration de nombreuses **options d’attribut** peut affecter les performances du site des manières suivantes :

- Temps de requête et de rendu longs sur les pages de détails de produits (PDP) et de catégories contenant des produits complexes.
- Le temps de réponse des opérations d’enregistrement de produit de l’administrateur augmente au-dessus des cibles de performances optimales.
- Augmentation du temps de rendu du formulaire de modification de produit.
- Extraction lente.

## Options du produit

La configuration d’un trop grand nombre d’options de produit par produit peut affecter les performances.

### Produits et versions concernés

[Toutes les versions prises en charge](../../../release/versions.md) de :

- Adobe Commerce sur les infrastructures cloud
- Adobe Commerce On-Premise

### Réduire le nombre d’options

Utilisez les stratégies suivantes pour réduire le nombre d’options de produit par produit :

- Configurez des produits complexes et des options personnalisées comme source de variations de produit.
- Au lieu de créer des modèles de produit globaux et des conteneurs d’options qui s’appliquent à tous les produits, utilisez des jeux d’attributs pour créer des modèles de produit spécifiques avec des attributs et des options ciblés.
- Gérer les informations sur les produits via un système de gestion des produits (PMS) externe.

### Impact potentiel sur les performances

La configuration de nombreuses options de produit augmente la quantité de données récupérées pour chaque produit lors de toutes les opérations de lecture et d’écriture, ce qui entraîne :

- L&#39;augmentation du trafic de requêtes SQL et des opérations `JOIN` plus lourdes augmentent le débit de la base de données.
- Augmentation de la taille des index Adobe Commerce et de l’index de recherche en texte intégral.

Les augmentations répertoriées ci-dessus peuvent affecter les performances du site des manières suivantes :

- Temps de réponse plus long pour la plupart des scénarios de storefront liés aux produits contenant de nombreuses options dans les attributs.
- Augmentation significative du temps nécessaire à l’exécution des opérations de gestion des produits dans Admin, ce qui peut entraîner des délais d’expiration, en particulier pour les scénarios liés à la liste d’attributs et à la récupération d’arborescence, y compris la gestion des règles de promotion.
- Peuvent bloquer les actions en bloc qui effectuent des opérations en masse asynchrones telles que l’importation et l’exportation, et attribuer des prix personnalisés à plusieurs produits dans un catalogue partagé.

## Pagination de la liste de produits

L’affichage d’un trop grand nombre de produits par page peut affecter les performances.

### Produits et versions concernés

[Toutes les versions prises en charge](../../../release/versions.md) de :

- Adobe Commerce sur les infrastructures cloud
- Adobe Commerce On-Premise

### Mettre à jour la configuration de la liste de produits

Si une catégorie contient trop de produits, mettez à jour la configuration du catalogue storefront pour désactiver l’option **Autoriser tous les produits par page**.

Après avoir désactivé cette option, Adobe Commerce utilise les contrôles de pagination du storefront de la liste de produits pour gérer le nombre de produits qui s’affichent dans les composants du storefront. Pour obtenir des instructions, voir [Configurer les contrôles de pagination](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/navigation/navigation-product-listings.html?lang=fr#configure-the-pagination-controls).

## Limites SKU du produit

La configuration d’un trop grand nombre de SKU de produit peut affecter les performances en ralentissant la récupération des données de produit et en augmentant le temps nécessaire aux opérations ou aux indexations d’administration.

### Produits et versions concernés

[Toutes les versions prises en charge](../../../release/versions.md) de :

- Adobe Commerce sur les infrastructures cloud
- Adobe Commerce On-Premise

### Réduire le nombre de produits

Utilisez les stratégies suivantes pour réduire le nombre de produits (SKU) :

- Minimiser les multiplicateurs -
   - La consolidation des sites web réduit le multiplicateur.
   - Utilisez d’autres fonctionnalités de produit pour la tarification personnalisée afin de remplacer les multiplicateurs de catalogue partagé et de groupes de clients.
   - Les groupes de clients et les catalogues partagés servent de multiplicateurs pour le nombre de SKU en vigueur dans un magasin.
- Restructurez le catalogue...
   - Réduisez le nombre de produits affectés aux catégories.
   - Réduisez le nombre de SKU en diminuant le nombre de sites web, de groupes de clients, de catalogues partagés, de produits ou d’options de produit configurables
- Fournissez d’autres variations de produit en utilisant des options personnalisées au lieu de créer des produits distincts.
- En tenant compte du fait qu’un SKU effectif pourrait inclure un certain nombre de permutations potentielles des prix, car les prix peuvent être spécifiés différemment par chaque magasin ou groupe de clients.
- Désactivez ou supprimez les composants système inutilisés, tels que les modules. Voir [Désinstaller les modules](../../../installation/tutorials/uninstall-modules.md).
- Gérer les produits dans un système de gestion de plateforme (PMS) externe.

## Variantes du produit

La configuration d’un trop grand nombre de variations par produit peut affecter les performances.

### Produits et versions concernés

[Toutes les versions prises en charge](../../../release/versions.md) de :

- Adobe Commerce sur les infrastructures cloud
- Adobe Commerce On-Premise

### Réduction du nombre de variations

Pour optimiser les performances du site, utilisez les stratégies suivantes afin de réduire le nombre de variations de produit :

- Restructurez le catalogue en répartissant le nombre de variations entre différents produits.
- Supprimez les options d’attribut configurables qui ne sont pas en stock.
- Gérez les variations par le biais de fonctionnalités alternatives telles que les options personnalisées, les catégories, les produits associés, groupés et groupés.

### Impact potentiel sur les performances

Le dépassement du nombre recommandé de variations de produit peut affecter les performances du site des manières suivantes :

- Temps de requête et de rendu longs sur les détails de produits et les pages de catégories contenant des produits complexes.
- Temps de réponse accru pour terminer les opérations d’enregistrement dans l’administrateur.
- Temps accru pour générer le formulaire de modification de produit.
- Extraction lente.

## Promotions

Suivez ces bonnes pratiques pour configurer les ventes et les promotions pour les articles d’un panier :

- **Règles de vente (règles de prix de panier)**
   - Gérez et supprimez les règles inutilisées.
   - Ajoutez des conditions de règle strictes (comme un filtre d’attribut ou de catégorie) pour une correspondance plus efficace.
- **Coupons**
   - Supprimez les coupons inutilisés et expirés.
   - Générer uniquement le nombre de coupons nécessaires pour répondre aux besoins de la campagne.

### Produits et versions concernés

[Toutes les versions prises en charge](../../../release/versions.md) de :

- Adobe Commerce sur les infrastructures cloud
- Adobe Commerce On-Premise

### Impact potentiel sur les performances

Le fait de disposer d’un nombre de règles de prix de panier ou de coupons supérieur au nombre maximal recommandé peut affecter les performances du site des manières suivantes :

- Temps de réponse accru lorsque des produits sont ajoutés au panier.
- Temps de chargement et de rendu du mini-art augmenté.
- Temps accru pour effectuer le rendu de la page du panier.
- Temps accru pour effectuer le rendu du bloc **Totaux** sur la page Passage en caisse.
