---
title: Configuration des types et des fronts de cache
description: Découvrez comment définir des fronts de cache et les associer à des types de cache dans Adobe Commerce. Découvrez la syntaxe de configuration pour env.php.
feature: Configuration, Cache
exl-id: 67d4ba06-b48b-4e1a-a7a8-9830490dfe3d
product_v2:
  - id: cdf0c6dd-1717-4e20-9530-a24eee57088b
    internal-label: Commerce on Cloud
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
  - id: b974b164-8a4e-43b8-a9e2-8e67ec131677
    internal-label: Commerce on Prem
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
    internal-label: Intermediate
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
    internal-label: Implementation
source-git-commit: 23f63c896760992da9b0d30b756a37de2117f6b8
workflow-type: tm+mt
source-wordcount: '471'
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
>Pour Adobe Commerce sur les infrastructures cloud, utilisez la [configuration du déploiement cloud](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/env/configure-env-yaml) décrite dans le guide sur le cloud. Ne modifiez pas `app/etc/env.php` directement. Les outils de déploiement génèrent ce fichier et peuvent remplacer les modifications manuelles.

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

Où :

- `<frontend_type>` : type de cache front-end de bas niveau. Spécifiez un nom de classe compatible avec `Zend_Cache_Core`.
Si cet attribut est omis, [&#128279;](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Cache/Core.php) est utilisé.

- `<frontend_option>`, `<frontend_option_value>` : nom et valeur des options que le framework Commerce transmet sous forme de tableau associatif au cache front-end lors de la création.

- `<backend_type>` : type de cache du serveur principal de bas niveau. Vous pouvez spécifier les éléments suivants :
  - **Cache Symfony (2.4.9+, recommandé)** : noms simplifiés tels que `valkey` ou `file`
  - **basé sur Zend** : nom de classe complet compatible avec `Zend_Cache_Backend` qui implémente `Zend_Cache_Backend_Interface`

- `<backend_option>`, `<backend_option_value>` : le nom et la valeur des options que le framework Commerce transmet sous forme de tableau associatif au cache du serveur principal lors de la création.

>[!NOTE]
>
>Pour les formats de valeur de serveur principal, tels que les noms de classe basés sur Zend par rapport aux noms simplifiés de Symfony Cache tels que `valkey` ou `file`, consultez [Mettre en cache les options de serveur principal](cache-options.md).

>[!MORELIKETHIS]
>
>- Configuration du cache L2 [&#x200B; pour l’optimisation des performances](level-two-cache.md)
>- [&#x200B; Gérer le cache &#x200B;](../cli/manage-cache.md)
