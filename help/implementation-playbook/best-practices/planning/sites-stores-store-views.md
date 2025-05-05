---
title: Bonnes pratiques relatives à la configuration des sites, des magasins et des vues des magasins
description: Découvrez les bonnes pratiques de configuration des sites, des magasins et de la vue du magasin afin d’optimiser les performances du site.
role: Admin
feature: Best Practices
exl-id: 3ea0c6c5-15a9-4e77-b4d0-ce15721c7167
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '228'
ht-degree: 0%

---

# Bonne pratique pour la configuration des sites, des magasins et de l’affichage en magasin

Pour Adobe Commerce sur l’infrastructure cloud, les bonnes pratiques s’appliquent spécifiquement à l’environnement de production (et éventuellement à l’environnement d’évaluation sur l’architecture Pro, soumis à des contraintes de ressources) qui aurait plus de ressources que les environnements d’intégration et de développement.

## Produits et versions concernés

[Toutes les versions prises en charge](../../../release/versions.md) de :

- Adobe Commerce sur l’infrastructure cloud
- Adobe Commerce sur site

## Stratégies pour améliorer les performances

Si votre projet nécessite de nombreux sites, magasins ou vues de magasin, vous pouvez utiliser les stratégies suivantes pour améliorer les performances :

- Restructurer le catalogue en transférant la logique vers des catégories
- Séparez les listes de prix des données de catalogue à l’aide d’un prix externe et d’un système de gestion des prix (PMS).
- Utiliser un stockage de données non SQL alternatif comme Elasticsearch

## Incidences sur les performances potentielles

Les sites web et les magasins sont des multiplicateurs pour les données de catalogue. Par conséquent, le fait d’avoir de nombreux sites web et magasins peut avoir une incidence négative sur les performances du site des manières suivantes :

- Des tables d’index plus volumineuses augmentent le temps nécessaire pour terminer les opérations d’indexation [Index de prix].
- La durée accrue de récupération de la configuration de l’application dégrade le temps de réponse du storefront pour les pages de catalogue non mises en cache.
- Augmentation significative du temps nécessaire à l’exécution des opérations de sauvegarde dans l’administrateur, car les données sont enregistrées séparément pour chaque site web.


## Informations supplémentaires

- [Comprendre les sites web, les magasins et les vues de magasin](https://experienceleague.adobe.com/fr/docs/commerce-cloud-service/user-guide/configure-store/best-practices)
- [ Configuration de plusieurs sites Web ou magasins](https://experienceleague.adobe.com/fr/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites)
