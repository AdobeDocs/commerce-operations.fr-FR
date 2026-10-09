---
title: Planification des mises à jour d’administration sur les sites de production
description: Découvrez les bonnes pratiques pour planifier des mises à jour critiques d’Adobe Commerce afin d’éviter les baisses de performance et les pannes.
role: Admin, User
feature: Best Practices
exl-id: 41c0cb87-3371-48a7-9913-264f3eea8d8d
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: cdfd3bc1-dc23-5cf0-b965-d3c0c55cde67
    internal-label: Best Practices
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '161'
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
- [Contenu privé : invalidation du contenu privé](https://developer.adobe.com/commerce/php/development/cache/page/private-content#invalidate-private-content)
- [Recommandations matérielles : caches](../../../performance/hardware.md#caches)
- [Configuration avancée : configurer Redis](../../../performance/advanced-setup.md#set-up-redis)
