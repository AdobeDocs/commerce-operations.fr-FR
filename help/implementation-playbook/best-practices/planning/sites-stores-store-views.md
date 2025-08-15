---
title: Bonnes pratiques relatives à la configuration des sites, des boutiques et des vues de boutique
description: Découvrez les bonnes pratiques de configuration des sites, des boutiques et des affichages de boutique afin d’optimiser les performances du site.
role: Admin
feature: Best Practices
exl-id: 3ea0c6c5-15a9-4e77-b4d0-ce15721c7167
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '228'
ht-degree: 0%

---

# Bonne pratique pour la configuration des sites, des boutiques et de la vue de boutique

Pour Adobe Commerce sur les infrastructures cloud, les bonnes pratiques s’appliquent spécifiquement à l’environnement de production (et éventuellement à l’architecture Staging on Pro, soumise à des contraintes de ressources) qui disposerait de davantage de ressources que les environnements d’intégration et de développement.

## Produits et versions concernés

[Toutes les versions prises en charge](../../../release/versions.md) de :

- Adobe Commerce sur les infrastructures cloud
- Adobe Commerce On-Premise

## Stratégies d’amélioration des performances

Si votre projet nécessite de nombreux sites, magasins ou vues de magasin, vous pouvez utiliser les stratégies suivantes pour améliorer les performances :

- Restructurer le catalogue en transférant la logique aux catégories
- Séparez les tarifs des données du catalogue à l&#39;aide d&#39;un prix externe et d&#39;un système de gestion des prix (PMS).
- Utiliser un autre stockage de données noSQL comme Elasticsearch

## Impacts potentiels sur les performances

Les sites web et les magasins sont des multiplicateurs pour les données de catalogue. Par conséquent, un grand nombre de sites web et de magasins peut avoir une incidence négative sur les performances du site des manières suivantes :

- Les tables d’index plus volumineuses augmentent le temps nécessaire aux opérations d’indexation [Indice de prix].
- L’augmentation du temps de récupération de la configuration de l’application dégrade le temps de réponse du storefront pour les pages de catalogue non mises en cache.
- Augmentation significative du temps nécessaire pour terminer les opérations d’enregistrement dans l’Administration, car les données sont enregistrées séparément pour chaque site web.


## Informations supplémentaires

- [Présentation des sites web, des boutiques et des affichages de boutique](https://experienceleague.adobe.com/fr/docs/commerce-cloud-service/user-guide/configure-store/best-practices)
- [Configurer plusieurs sites web ou magasins](https://experienceleague.adobe.com/fr/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites)
