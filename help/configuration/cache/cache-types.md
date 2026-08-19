---
title: Configuration des types et des fronts de cache
description: Découvrez comment définir des fronts de cache et les associer à des types de cache dans Adobe Commerce. Découvrez la syntaxe de configuration pour env.php.
feature: Configuration, Cache
exl-id: 67d4ba06-b48b-4e1a-a7a8-9830490dfe3d
product_v2:
  - id: cdf0c6dd-1717-4e20-9530-a24eee57088b
  - id: eadea719-cf89-469b-a6fd-a236a7138047
  - id: b974b164-8a4e-43b8-a9e2-8e67ec131677
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
source-git-commit: 3652976a8db3d0bb19ff9cd06adb3a7736c89539
workflow-type: tm+mt
source-wordcount: 398
ht-degree: 0%

---

# Configuration des fronts et des types du cache

Une interface de cache connecte les types de cache Commerce au stockage en cache. Vous pouvez définir plusieurs fronts et affecter des types de cache spécifiques à chaque front-end.

>[!BEGINSHADEBOX]

Utilisez la relation suivante pour déterminer où un type de cache stocke ses données :

type de cache → cache frontal → principal du cache

>[!ENDSHADEBOX]

Pour une présentation de l’architecture de mise en cache du Commerce, voir [&#x200B; Présentation de la mise en cache et options de configuration](caching-overview.md).

>[!NOTE]
>
>Pour Adobe Commerce sur les infrastructures cloud, utilisez la [configuration du déploiement cloud](https://experienceleague.adobe.com/fr/docs/commerce-on-cloud/user-guide/configure/env/configure-env-yaml) décrite dans le guide sur le cloud. Ne modifiez pas `app/etc/env.php` directement. Les outils de déploiement génèrent ce fichier et peuvent remplacer les modifications manuelles.

## Utiliser le serveur frontal par défaut

Commerce fournit un système frontal par défaut qui peut être utilisé par tous les types de cache.

Dans la plupart des cas, vous n’avez pas besoin de définir un système frontal personnalisé. Si tous les types de cache peuvent utiliser les mêmes options de serveur principal et de serveur principal, utilisez le serveur frontal par défaut et configurez son serveur principal. Consultez [Mettre en cache les options du serveur principal](cache-options.md) pour une configuration spécifique au serveur principal.

Pour les versions d’Adobe Commerce antérieures à la version 2.4.9, le serveur frontal par défaut utilise l’implémentation de cache héritée basée sur Zend. Le serveur frontal `Magento\Framework\Cache\Core` étend `Zend_Cache_Core`. Adobe Commerce 2.4.9 et versions ultérieures utilisent la mise en œuvre moderne de Symfony. Consultez [Options du serveur principal de mise en cache](cache-options.md) pour obtenir des conseils spécifiques à la version.

## Définir un serveur frontal personnalisé

Utilisez un cache frontal personnalisé lorsqu’un ou plusieurs types de cache ont besoin de paramètres de serveur principal différents de ceux du cache frontal par défaut.

Pour les déploiements sur site, définissez le serveur frontal dans `app/etc/env.php`. Attribuez-lui ensuite un ou plusieurs types de cache :

```php?start_inline=1
'cache' => [
    'frontend' => [
        '<frontend-id>' => [
            'backend' => '<backend-type>',
            'backend_options' => [
                // Backend-specific options
            ],
        ],
    ],
    'type' => [
        '<cache-type-id>' => [
            'frontend' => '<frontend-id>',
        ],
    ],
],
```

Où :

- `<frontend-id>` est l’identifiant unique du front-end, par exemple `default` ou `page_cache`.
- `<backend-type>` identifie le serveur principal utilisé par le serveur frontal. La valeur prise en charge dépend de la version d’Adobe Commerce et du serveur principal sélectionné.
- `backend_options` contient des options pour le serveur principal sélectionné.
- `<cache-type-id>` est un type de cache Commerce, tel que `config`, `layout`, `block_html` ou `full_page`.


Pour connaître les types de serveur principal, les options prises en charge et les exemples de configuration spécifiques à une version, consultez [Mettre en cache les options du serveur principal](cache-options.md).

## Affectation d’un type de cache à un serveur frontal

La configuration `type` mappe un type de cache à un front-end :

```php?start_inline=1
'type' => [
    'full_page' => [
        'frontend' => 'page_cache',
    ],
],
```

Dans cet exemple, Commerce affecte le type de cache `full_page` au serveur frontal `page_cache`. Le serveur frontal détermine la configuration du serveur principal qui stocke ce type de cache.

>[!NOTE]
>
>La clé `full_page` représente un type de cache d’application Commerce. La mise en cache HTTP de pages entières via Varnish ou Fastly est une couche de mise en cache distincte. Voir [&#x200B; Présentation de la mise en cache et options de configuration](caching-overview.md).

>[!MORELIKETHIS]
>
>- Configuration du cache L2 [&#x200B; pour l’optimisation des performances](level-two-cache.md)
>- [&#x200B; Gérer le cache &#x200B;](../cli/manage-cache.md)
