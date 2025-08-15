---
title: Planification des mises à jour d’administration sur les sites de production
description: Découvrez les bonnes pratiques pour planifier des mises à jour critiques d’Adobe Commerce afin d’éviter les baisses de performance et les pannes.
role: Admin, User
feature: Best Practices
exl-id: 41c0cb87-3371-48a7-9913-264f3eea8d8d
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '135'
ht-degree: 1%

---

# Bonnes pratiques pour planifier les mises à jour d’administration sur les sites de production

Planifiez les mises à jour et opérations critiques sur vos sites Adobe Commerce pendant les heures creuses afin d’éviter la lenteur des performances et les pannes sur les sites de production.

Exemples d’actions critiques :

- Modifications de la configuration d’administration, par exemple mise à jour d’un attribut de produit ou déplacement d’une sous-catégorie de produits vers une autre catégorie
- Opérations d&#39;import ou d&#39;export de données

Les actions critiques entraînent l’invalidation du cache et les opérations de réindexation, ce qui augmente considérablement le temps de réponse et peut entraîner des pannes du site.

## Produits et versions concernés

[Toutes les versions prises en charge](../../../release/versions.md) de :

- Adobe Commerce sur les infrastructures cloud
- Adobe Commerce On-Premise

## Informations supplémentaires

- [Bonnes pratiques de mise en cache](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/cache-management#best-practices-for-caching)
- [Contenu privé : invalidation du contenu privé](https://developer.adobe.com/commerce/php/development/cache/page/private-content/#invalidate-private-content)
- [Recommandations matérielles : caches](../../../performance/hardware.md#caches)
- [Configuration avancée : configurer Redis](../../../performance/advanced-setup.md#set-up-redis)
