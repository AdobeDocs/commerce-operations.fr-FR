---
title: Bonnes pratiques relatives à la configuration des sites, des magasins et des vues des magasins
description: Découvrez les bonnes pratiques de configuration des sites, des magasins et des vues de magasin afin d’optimiser les performances du site.
role: Admin
feature: Best Practices
feature-set: Commerce
source-git-commit: 510f2d4cdaec1034cb04a01fab0948c4261c6d10
workflow-type: tm+mt
source-wordcount: '280'
ht-degree: 0%

---


# Bonne pratique pour configurer les sites, les magasins et l’affichage en magasin

Pour optimiser les performances du site, configurez un maximum de 50 sites, 50 magasins et 50 vues de magasin pour Adobe Commerce sur les projets d’infrastructure cloud.

>[!NOTE]
>
>Pour Adobe Commerce sur l’infrastructure cloud, les bonnes pratiques s’appliquent spécifiquement à l’environnement de production (et éventuellement à l’environnement d’évaluation sur l’architecture Pro, soumis à des contraintes de ressources) qui aurait plus de ressources que les environnements d’intégration et de développement. Pour les environnements d’intégration (Pro et Starter) et d’évaluation (Starter), réduisez le nombre d’affichages de magasin à moins de 5 ou 10 (soumis à une révision technique).

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

- Des tables d’index plus volumineuses augmentent le temps nécessaire pour terminer les opérations d’indexation. [Indice de prix].
- La durée accrue de récupération de la configuration de l’application dégrade le temps de réponse du storefront pour les pages de catalogue non mises en cache.
- Augmentation significative du temps nécessaire à l’exécution des opérations de sauvegarde dans l’administrateur, car les données sont enregistrées séparément pour chaque site web.


## Informations supplémentaires

- [Présentation des sites web, des magasins et des vues de magasin](https://devdocs.magento.com/cloud/configure/configure-best-practices.html#sites)
- [Configuration de plusieurs sites web ou magasins](https://devdocs.magento.com/cloud/project/project-multi-sites.html)

