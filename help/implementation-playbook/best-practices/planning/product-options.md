---
title: Bonnes pratiques de configuration des options de produit
description: Optimisez les performances d’Adobe Commerce en limitant le nombre d’options de produit.
role: Admin
feature: Best Practices, Catalog Management
exl-id: 7571a163-798a-40be-b26f-4a184bceb809
source-git-commit: df8878a3fea19b8f1780b5037273e18b5a3f1373
workflow-type: tm+mt
source-wordcount: '294'
ht-degree: 0%

---

# Bonnes pratiques relatives aux options de produit

Pour de meilleures performances, configurez un maximum de 100 options de produit par produit.

## Produits et versions concernés

[Toutes les versions prises en charge](../../../release/versions.md) de :

- Adobe Commerce sur l’infrastructure cloud
- Adobe Commerce sur site

## Réduction des options de produit

Pour de meilleures performances du site, utilisez les stratégies suivantes afin de réduire le nombre d’options de produit :

- Configurez des produits complexes et des options personnalisées en tant que source de variations de produit.
- Au lieu de créer des modèles de produits globaux et des conteneurs d’options qui s’appliquent à tous les produits, utilisez des ensembles d’attributs pour créer des modèles de produits spécifiques avec des attributs et des options ciblés.
- Gérez les informations sur les produits par le biais d’un système de gestion des produits (PMS) externe.

## Impact potentiel sur les performances

La configuration de nombreuses options de produit augmente la quantité de données récupérées pour chaque produit pour toutes les opérations de lecture et d’écriture, ce qui entraîne :

- Augmentation du trafic de requêtes SQL et augmentation du trafic `JOIN` augmente le débit de la base de données.
- Taille accrue des index Adobe Commerce et de l’index de recherche en texte intégral.

Les augmentations répertoriées ci-dessus peuvent affecter les performances du site de la manière suivante :

- Délai de réponse plus long pour la plupart des scénarios de storefront relatifs aux produits contenant de nombreuses options dans les attributs.
- Augmentation significative du temps nécessaire à l’exécution des opérations de gestion des produits dans l’administration, ce qui peut entraîner des dépassements de délai, en particulier pour les scénarios liés à la liste d’attributs et à la récupération d’arborescence, y compris la gestion des règles de promotion.
- Peut bloquer les actions en bloc qui terminent des opérations de masse asynchrones comme l’importation et l’exportation et affecter des prix personnalisés à plusieurs produits dans un catalogue partagé.

## Informations supplémentaires

- [Création d’un produit](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/product-create.html)
- [Bonnes pratiques relatives à la configuration des attributs de produit](product-attributes-and-options.md)
- [Journal des actions en bloc](https://docs.magento.com/user-guide/system/action-log-bulk-actions.html)
- [API d’actions en masse d’inventaire](https://developer.adobe.com/commerce/webapi/rest/inventory/bulk-inventory/)
- [Formation : Gestion des catalogues et des produits à l’aide d’Adobe Commerce](https://learning.adobe.com/catalog/adobe_commerce/cours000000000098643.html)
