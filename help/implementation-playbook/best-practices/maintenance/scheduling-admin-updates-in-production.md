---
title: Planification des mises à jour de l’administrateur sur les sites de production
description: Découvrez les bonnes pratiques pour planifier des mises à jour critiques d’Adobe Commerce afin d’éviter des performances et des pannes lentes.
role: Admin, User
feature: Best Practices
exl-id: 41c0cb87-3371-48a7-9913-264f3eea8d8d
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '135'
ht-degree: 1%

---

# Bonnes pratiques pour la planification des mises à jour de l’administrateur sur les sites de production

Planifiez les mises à jour et les opérations critiques sur vos sites Adobe Commerce aux heures creuses afin d’éviter des performances ralenties et des pannes sur les sites de production.

Exemples d’actions critiques :

- Modifications de la configuration de l’administrateur, par exemple la mise à jour d’un attribut de produit ou le déplacement d’une sous-catégorie de produit vers une autre catégorie
- Opérations d’import ou d’export de données

Les actions critiques entraînent l’invalidation du cache et la réindexation, ce qui augmente considérablement le temps de réponse et peut entraîner des pannes de site.

## Produits et versions concernés

[Toutes les versions prises en charge](../../../release/versions.md) de :

- Adobe Commerce sur l’infrastructure cloud
- Adobe Commerce sur site

## Informations supplémentaires

- [Bonnes pratiques pour la mise en cache](https://experienceleague.adobe.com/fr/docs/commerce-admin/systems/tools/cache-management#best-practices-for-caching)
- [Contenu privé : invalider le contenu privé](https://developer.adobe.com/commerce/php/development/cache/page/private-content/#invalidate-private-content)
- [Recommandations matérielles : mises en cache](../../../performance/hardware.md#caches)
- [Configuration avancée : configuration de Redis](../../../performance/advanced-setup.md#set-up-redis)
