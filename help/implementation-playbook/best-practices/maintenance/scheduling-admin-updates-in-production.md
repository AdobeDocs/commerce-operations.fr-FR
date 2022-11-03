---
title: Planification des mises à jour de l’administrateur sur les sites de production
description: Découvrez les bonnes pratiques pour planifier des mises à jour critiques d’Adobe Commerce afin d’éviter des performances et des pannes lentes.
role: Admin, User
feature: Best Practices
feature-set: Commerce
source-git-commit: 510f2d4cdaec1034cb04a01fab0948c4261c6d10
workflow-type: tm+mt
source-wordcount: '148'
ht-degree: 0%

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

- [Bonnes pratiques relatives à la mise en cache](https://docs.magento.com/user-guide/system/cache-management.html#best-practices-for-caching)
- [Contenu privé : Invalider le contenu privé](https://developer.adobe.com/commerce/php/development/cache/page/private-content/#invalidate-private-content)
- [Recommandations matérielles : Caches](../../../performance/hardware.md#caches)
- [Configuration avancée : Configuration de Redis](../../../performance/advanced-setup.md#set-up-redis)

