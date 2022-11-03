---
title: Bonnes pratiques de configuration des attributs de produit
description: Découvrez comment optimiser les performances d’Adobe Commerce en limitant le nombre d’attributs de produit, d’options d’attribut et de jeux d’attributs.
role: User, Admin
feature: Best Practices
feature-set: Commerce
source-git-commit: e156fcafc5792036b37d9b199b870f1888c3f1ff
workflow-type: tm+mt
source-wordcount: '564'
ht-degree: 0%

---


# Bonnes pratiques relatives à la configuration des attributs de produit

- Pour de meilleures performances, ne configurez pas plus que le nombre maximal recommandé d’attributs de produit ou d’options d’attributs de produit.

- **Attributs de produit**—
   - Pour Adobe Commerce versions 2.3.x et 2.4.0 à 2.4.1-p1, ne configurez pas plus de 500 attributs.
   - Pour Adobe Commerce version 2.4.2 et ultérieure, configurez jusqu’à 1 500 attributs de produit.
- **Options d’attribut de produit**-Configurer jusqu’à 100 options d’attribut pour chaque attribut
- **Jeux d’attributs de produit**-Configurer un maximum de 1 000 ensembles d’attributs _

>[!NOTE]
>
>Les attributs de produit spécifient les fonctionnalités qui s’appliquent globalement à tous les produits. Les options d’attribut de produit sont des personnalisations pour spécifier les fonctionnalités qui s’appliquent à des produits spécifiques.

## Produits et versions concernés

[Toutes les versions prises en charge](../../../release/versions.md) de :

- Adobe Commerce sur l’infrastructure cloud
- Adobe Commerce sur site

## Réduction du nombre d’attributs de produit

Pour de meilleures performances lors de la gestion des produits à partir de l’administrateur et de la récupération des données de produit dans le storefront :

- Utilisez différents modèles de produit (ensembles d’attributs) pour différents produits.
- Utilisation d’options personnalisées et de produits complexes pour la gestion des variations
- Réduisez le nombre d’attributs pouvant faire l’objet d’une recherche.
- Supprimez les propriétés de produit qui ne sont pas utilisées.
- Stocker et gérer les attributs non liés au commerce dans les systèmes de gestion de produits externes (SPM).

## Réduction du nombre d’options d’attribut de produit

Pour de meilleures performances lors de la gestion des produits à partir de l’administrateur et de la récupération des données de produit dans le storefront :

- Utilisez différents mécanismes de variation pour créer des produits : produits complexes, options personnalisées comme source de variations de produits.
- Créez des modèles de produit spécifiques avec des attributs et des options de ciblage afin d’éviter des modèles de produit et des conteneurs d’options généralisés.
- Conserver une liste des options d’attribut réelles.
- Gérez les informations sur les produits par le biais d’un système de gestion des produits (PMS) externe.

## Réduction du nombre de jeux d’attributs de produit

Supprimez les ensembles d’attributs de produit inutilisés à l’aide de MySQL.

### Vérification de la configuration des jeux d’attributs

1. [Connexion à la base de données du site](https://devdocs.magento.com/cloud/project/services-mysql.html#connect-to-the-database).

1. Recherche du nombre de jeux d’attributs à l’aide de MySQL

   ```sql
   SELECT COUNT(*) AS 'attribute_set' FROM *${TABLE_PREFIX}*eav_attribute_set;
   ```

1. Supprimez tous les jeux d’attributs inutilisés.

## Incidences sur les performances potentielles

Configuration de plusieurs **attributs de produit** augmente la taille du modèle de produit pour chaque produit (structure de test de performance) et la quantité de données à récupérer. Cette augmentation affecte les opérations de la manière suivante :

- Augmentation du trafic de requêtes SQL lié à la récupération des données par les VEC et de la quantité de données traitées, ce qui entraîne une diminution du débit de base de données
- Augmentation significative de la taille des index Adobe Commerce et de l’index de recherche de texte intégral
- Atteindre les limites strictes de MySQL lors de la création d’un index FLAT pour les modèles de produits surdimensionnés et l’impossibilité de l’utiliser

L’augmentation des données de produit et des tailles d’index peut affecter les performances du site de la manière suivante :

- Amélioration du temps de réponse pour la plupart des scénarios de storefront liés à la navigation dans les catalogues, à la recherche (rapide et avancée) et à la navigation par couches.
- Les opérations de gestion des produits dans l’administrateur ralentissent considérablement, ce qui peut entraîner des délais d’expiration.
- La fonctionnalité des actions en masse de produit peut être bloquée.
- Le temps de reconstruction des index pour les catalogues de taille moyenne et grande ne peut pas être réalisé quotidiennement en raison de longues heures d’exécution.

Configuration de plusieurs **options d’attribut** peut affecter les performances du site de la manière suivante :

- Longs délais de demande et de rendu sur les pages de détails du produit (PDP) et des catégories contenant des produits complexes.
- Le temps de réponse des opérations d’enregistrement des produits d’administration augmente au-dessus des cibles de performances optimales.
- Augmentation du temps de rendu du formulaire de modification du produit.
- Passage en caisse lent.

## Informations supplémentaires

- [Présentation des attributs de produit](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/product-attributes.html)
- [Jeux d’attributs](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/create/attribute-sets.html)
- [Création d’un produit](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/product-create.html)
- [Tutoriels de personnalisation > Personnaliser le formulaire de création de produits](https://developer.adobe.com/commerce/php/tutorials/admin/custom-product-creation-form/)

