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

Les bonnes pratiques de gestion des catalogues décrites ici couvrent un large éventail de problèmes, notamment (mais sans s’y limiter) :

- Limites du panier
- Limites de catégorie
- Attributs de produit
- Pagination des listes de produits
- Options de produit
- Variations de produit
- Promotions

## Limites du panier

Pour de meilleures performances, suivez les instructions ci-après pour gérer les limites de panier pour Adobe Commerce.

### Produits et versions concernés

[Toutes les versions prises en charge](../../../release/versions.md) de :

- Adobe Commerce sur l’infrastructure cloud
- Adobe Commerce sur site

### Réduction du nombre d’articles dans le panier

Utilisez les stratégies suivantes pour gérer le nombre d’articles du panier :

- Fractionnez les commandes en plusieurs commandes plus petites avec un plus petit nombre de lignes à l’aide de la [!UICONTROL Add Item by SKU] fonctionnalité.
- Ajoutez uniquement la logique personnalisée et la personnalisation du panier requises pour charger une liste d’articles.

## Limites des catégories

La configuration d’un grand nombre de catégories peut affecter les performances.

### Produits et versions concernés

[Toutes les versions prises en charge](../../../release/versions.md) de :

- Adobe Commerce sur l’infrastructure cloud
- Adobe Commerce local

### Réduire le nombre de produits

Utilisez les stratégies suivantes pour réduire le nombre de catégories :

- Gérer les fonctionnalités uniques d’un produit à l’aide d’attributs et d’options personnalisées
- Suppression des catégories inactives
- Optimiser la profondeur de catalogue dans la navigation

## Attributs de produit

La configuration d’un trop grand nombre d’attributs de produit ou d’options d’attributs de produit peut affecter les performances.

>[!NOTE]
>
>Les attributs de produit spécifient les fonctionnalités qui s’appliquent globalement à tous les produits. Les options d’attribut de produit sont des personnalisations pour spécifier les fonctionnalités qui s’appliquent à des produits spécifiques.

### Produits et versions concernés

[Toutes les versions prises en charge](../../../release/versions.md) de :

- Adobe Commerce sur l’infrastructure cloud
- Adobe Commerce sur site

### Réduction du nombre d’attributs

Pour de meilleures performances lors de la gestion des produits à partir de l’administrateur et de la récupération des données de produit dans le storefront :

- Utilisez différents modèles de produit (ensembles d’attributs) pour différents produits.
- Utilisation d’options personnalisées et de produits complexes pour la gestion des variations
- Réduisez le nombre d’attributs pouvant faire l’objet d’une recherche.
- Supprimez les propriétés de produit qui ne sont pas utilisées.
- Stocker et gérer les attributs non liés au commerce dans les systèmes de gestion de produits externes (SPM).

### Réduction du nombre d’options d’attribut

Pour de meilleures performances lors de la gestion des produits à partir de l’administrateur et de la récupération des données de produit dans le storefront :

- Utilisez différents mécanismes de variation pour créer des produits : produits complexes, options personnalisées comme source de variations de produits.
- Créez des modèles de produit spécifiques avec des attributs et des options de ciblage afin d’éviter des modèles de produit et des conteneurs d’options généralisés.
- Conserver une liste des options d’attribut réelles.
- Gérez les informations sur les produits par le biais d’un système de gestion des produits (PMS) externe.

### Réduction du nombre de jeux d’attributs

Supprimez les ensembles d’attributs de produit inutilisés à l’aide de MySQL.

#### Vérification de la configuration des jeux d’attributs

1. [Connectez-vous à la base de données du site](https://experienceleague.adobe.com/fr/docs/commerce-cloud-service/user-guide/configure/service/mysql#connect-to-the-database).

1. Recherche du nombre de jeux d’attributs à l’aide de MySQL

   ```sql
   SELECT COUNT(*) AS 'attribute_set' FROM *${TABLE_PREFIX}*eav_attribute_set;
   ```

1. Supprimez tous les jeux d’attributs inutilisés.

### Impact potentiel sur les performances

La configuration de nombreux **attributs de produit** augmente la taille du modèle de produit pour chaque produit (structure de fichier EAV) et la quantité de données à récupérer. Cette augmentation affecte les opérations de la manière suivante :

- Augmentation du trafic de requêtes SQL lié à la récupération des données par les VEC et de la quantité de données traitées, ce qui entraîne une diminution du débit de base de données
- Augmentation significative de la taille des index Adobe Commerce et de l’index de recherche de texte intégral
- Atteindre les limites strictes de MySQL lors de la création d’un index FLAT pour les modèles de produits surdimensionnés et l’impossibilité de l’utiliser

L’augmentation des données de produit et des tailles d’index peut affecter les performances du site de la manière suivante :

- Amélioration du temps de réponse pour la plupart des scénarios de storefront liés à la navigation dans les catalogues, à la recherche (rapide et avancée) et à la navigation par couches.
- Les opérations de gestion des produits dans l’administrateur ralentissent considérablement, ce qui peut entraîner des délais d’expiration.
- La fonctionnalité des actions en masse de produit peut être bloquée.
- Le temps de reconstruction des index pour les catalogues de taille moyenne et grande ne peut pas être réalisé quotidiennement en raison de longues heures d’exécution.

La configuration de nombreuses **options d’attribut** peut affecter les performances du site de la manière suivante :

- Longs délais de demande et de rendu sur les pages de détails du produit (PDP) et des catégories contenant des produits complexes.
- Le temps de réponse des opérations d’enregistrement des produits d’administration augmente au-dessus des cibles de performances optimales.
- Augmentation du temps de rendu du formulaire de modification du produit.
- Passage en caisse lent.

## Options de produit

La configuration d’un trop grand nombre d’options de produit par produit peut affecter les performances.

### Produits et versions concernés

[Toutes les versions prises en charge](../../../release/versions.md) de :

- Adobe Commerce sur l’infrastructure cloud
- Adobe Commerce sur site

### Réduisez le nombre d’options

Utilisez les stratégies suivantes pour réduire le nombre d’options de produit par produit :

- Configurez des produits complexes et des options personnalisées en tant que source de variations de produit.
- Au lieu de créer des modèles de produits globaux et des conteneurs d’options qui s’appliquent à tous les produits, utilisez des ensembles d’attributs pour créer des modèles de produits spécifiques avec des attributs et des options ciblés.
- Gérez les informations sur les produits par le biais d’un système de gestion des produits (PMS) externe.

### Impact potentiel sur les performances

La configuration de nombreuses options de produit augmente la quantité de données récupérées pour chaque produit sur toutes les opérations de lecture et d’écriture, ce qui se traduit par :

- L’augmentation du trafic de requêtes SQL et le volume des opérations plus `JOIN` lourdes augmentent le débit de la base de données.
- Augmentation de la taille des index Commerce Adobe et de l’index de recherche de texte intégral.

Les augmentations répertoriées ci-dessus peuvent affecter les performances du site des manières suivantes :

- Temps de réponse plus long pour la plupart des scénarios de vitrine liés aux produits contenant de nombreuses options dans les attributs.
- Augmentation significative du temps nécessaire à l’exécution des opérations de gestion des produits dans l’administration, ce qui peut entraîner des dépassements de délai, en particulier pour les scénarios liés à la liste d’attributs et à la récupération d’arborescence, y compris la gestion des règles de promotion.
- Peut bloquer les actions en bloc qui terminent des opérations de masse asynchrones comme l’importation et l’exportation et affecter des prix personnalisés à plusieurs produits dans un catalogue partagé.

## Pagination des listes de produits

L’affichage d’un trop grand nombre de produits par page peut affecter les performances.

### Produits et versions concernés

[Toutes les versions prises en charge](../../../release/versions.md) de :

- Adobe Commerce sur l’infrastructure cloud
- Adobe Commerce sur site

### Mettre à jour la configuration de la liste de produits

Si vous avez trop de produits dans une catégorie, mettez à jour la configuration du catalogue storefront pour désactiver l’option **Autoriser tous les produits par page**.

Après avoir désactivé cette option, Adobe Commerce utilise les commandes de pagination storefront de la liste de produits pour gérer le nombre de produits qui s’affichent dans les composants storefront. Pour obtenir des instructions, voir [Configuration des commandes de pagination](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/navigation/navigation-product-listings.html?lang=fr#configure-the-pagination-controls).

## Limites des SKU du produit

La configuration d’un trop grand nombre de SKU de produit peut affecter les performances en ralentissant la récupération des données du produit et en augmentant le temps nécessaire pour effectuer les opérations d’administration ou les indexations.

### Produits et versions concernés

[Toutes les versions](../../../release/versions.md) prises en charge de :

- Adobe Commerce sur l’infrastructure cloud
- Adobe Commerce sur site

### Réduction du nombre de produits

Utilisez les stratégies suivantes pour réduire le nombre de produits (SKU) :

- Minimiser les multiplicateurs —
   - La consolidation des sites web réduit le multiplicateur.
   - Utilisez d’autres fonctionnalités de produit pour la tarification personnalisée afin de remplacer le catalogue partagé et les multiplicateurs de groupes de clients.
   - Les groupes de clients et le catalogue partagé fonctionnent tous deux comme des multiplicateurs pour le nombre de SKU efficaces dans un magasin.
- Restructurer le catalogue —
   - Réduire le nombre de produits affectés aux catégories.
   - Réduire le nombre de SKU en réduisant le nombre de sites web, de groupes de clients, de catalogues partagés, de produits ou d’options de produits configurables
- Fournissez d’autres variations de produit en utilisant des options personnalisées au lieu de créer des produits distincts.
- Prise en compte du fait qu’un SKU effectif peut inclure un certain nombre de permutation de prix potentielles, car les prix peuvent être spécifiés différemment selon chaque magasin ou groupe de clients.
- Désactivez ou supprimez les composants système inutilisés tels que les modules. Voir [Désinstallation des modules](../../../installation/tutorials/uninstall-modules.md).
- Gérez les produits dans un système de gestion de plateforme externe (PMS).

## Variations de produit

La configuration d’un trop grand nombre de variations par produit peut affecter les performances.

### Produits et versions concernés

[Toutes les versions prises en charge](../../../release/versions.md) de :

- Adobe Commerce sur l’infrastructure cloud
- Adobe Commerce sur site

### Réduction du nombre de variations

Pour de meilleures performances du site, utilisez les stratégies suivantes afin de réduire le nombre de variations de produits :

- Restructurez le catalogue en répartissant le nombre de variations entre différents produits.
- Supprimez les options d’attribut configurables qui ne sont pas en stock.
- Gérez les variations par le biais d’autres fonctionnalités telles que les options personnalisées, les catégories, les produits associés, regroupés et les produits de regroupement.

### Impact potentiel sur les performances

Le dépassement du nombre recommandé de variations de produit peut affecter les performances du site des manières suivantes :

- Délais de demande et de rendu longs sur les pages de détails et de catégorie d’un produit contenant des produits complexes.
- Amélioration du temps de réponse pour terminer les opérations d’enregistrement dans l’administrateur.
- Amélioration du temps d’affichage du formulaire de modification du produit.
- Passage en caisse lent.

## Promotions

Pour configurer les ventes et les promotions des articles d’un panier, suivez ces meilleures pratiques :

- **Règles de vente (règles de prix de panier)**
   - Gérez et supprimez les règles inutilisées.
   - Ajoutez des conditions de règle strictes (comme un filtre d’attribut ou de catégorie) pour une correspondance plus efficace.
- **Coupons**
   - Supprimez les bons inutilisés et expirés.
   - Générez uniquement le nombre de coupons nécessaires pour satisfaire les exigences de la campagne.

### Produits et versions concernés

[Toutes les versions prises en charge](../../../release/versions.md) de :

- Adobe Commerce sur l’infrastructure cloud
- Adobe Commerce sur site

### Impact potentiel sur les performances

Le fait d’avoir plus que le nombre maximal recommandé de règles de prix de panier ou de bons d’achat peut affecter les performances du site des manières suivantes :

- Amélioration du temps de réponse lorsque des produits sont ajoutés au panier.
- Amélioration du temps de chargement et du rendu du minicart.
- Augmentation du temps pour le rendu de la page de panier.
- Accélération accrue pour le rendu du bloc **Totaux** sur la page Passage en caisse.
