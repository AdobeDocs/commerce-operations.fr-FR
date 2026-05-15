---
title: Options du serveur principal de mise en cache et référence de stockage
description: Découvrez les options du serveur principal de cache dans Adobe Commerce, notamment le système de fichiers, Redis, Valkey et le stockage dans la base de données. Découvrez les approches héritées et modernes.
feature: Configuration, Cache
exl-id: e0330108-5c55-4a33-9f93-63fbb71af761
source-git-commit: 9cd0f2a84772e2d68fd15a00651216abfa9ec91c
workflow-type: tm+mt
source-wordcount: '300'
ht-degree: 0%

---

# Mettre en cache les options principales et la référence de stockage

L’application Commerce utilise un cache de bas niveau frontal et principal pour permettre l’accès au stockage du cache. Commerce prend en charge plusieurs stratégies et back-ends de mise en cache, chacun adapté à différents cas d’utilisation. Cette page décrit les serveurs principaux disponibles et leurs différences.

>[!NOTE]
>
>Pour plus d’informations sur la configuration du cache frontal, voir [Configuration des fronts de cache](cache-types.md).

## Options de cache du serveur principal

Le tableau suivant résume les caches principaux disponibles :

| Serveur principal | Description | Guide de configuration |
| ------- | ----------- | ------------------- |
| Système de fichiers | Valeur par défaut. Stocke les données de cache dans des fichiers sous `var/cache/`. Aucune configuration requise. | S.O. |
| [Redis &#x200B;](config-redis.md) | Magasin de données en mémoire pour une mise en cache hautes performances. | [Utiliser Redis pour le cache par défaut](redis-pg-cache.md) |
| [&#x200B; Valkey &#x200B;](config-valkey.md) | Alternative open source compatible avec Redis. | [Utiliser Valkey pour le cache par défaut](valkey-pg-cache.md) |
| [&#x200B; Base de données &#x200B;](https://developer.adobe.com/commerce/php/development/cache/partial/database-caching/) | Mise en cache de base de données. | [Création de moteurs de cache personnalisés](https://developer.adobe.com/commerce/php/development/cache/partial/database-caching/){target="_blank"} (documentation Adobe destinée aux développeurs) |

>[!NOTE]
>
>[Vernis](config-varnish.md) gère la mise en cache de pleine page au niveau HTTP et n’utilise pas le serveur principal du cache de bas niveau.

## Approches de mise en œuvre

Commerce prend en charge deux approches d’implémentation principales. L’approche que vous choisissez dépend de votre version de Commerce :

>[!BEGINTABS]

>[!TAB Ancien cache basé sur Zend (2.4.8 et versions antérieures)]

Utilise des noms de classe complets pour la configuration du serveur principal :

| Serveur principal | Nom de la classe |
| ------- | ---------- |
| Redis | `Magento\Framework\Cache\Backend\Redis` |
| Valkey | `Magento\Framework\Cache\Backend\Valkey` |

Ils sont compatibles avec l’interface `Zend_Cache_Backend`.

**Exemple de configuration :**

```php?start_inline=1
'backend' => 'Magento\\Framework\\Cache\\Backend\\Redis',
'backend_options' => [
    'server' => '127.0.0.1',
    'database' => '0',
    'port' => '6379',
],
```

>[!TAB Cache Symfony moderne (2.4.9 et versions ultérieures, recommandé)]

>[!TIP]
>
>L’implémentation moderne de Symfony Cache offre de meilleures performances grâce à la conformité PSR-6, la sérialisation Igbinary, la compression gzip, les scripts Lua et les connexions persistantes.

Utilise des noms de type back-end simplifiés :

| Serveur principal | Saisir le nom |
| ------- | --------- |
| Redis | `redis` |
| Valkey | `valkey` |
| Système de fichiers | `file` |

**Exemple de configuration :**

```php?start_inline=1
'backend' => 'redis',
'backend_options' => [
    'server' => '127.0.0.1',
    'database' => '0',
    'port' => '6379',
    'serializer' => 'igbinary',
    'compression_lib' => 'gzip',
],
```

>[!ENDTABS]

Pour obtenir des options de configuration complètes, voir :

- [Utiliser Redis pour le cache par défaut](redis-pg-cache.md)
- [Utiliser Valkey pour le cache par défaut](valkey-pg-cache.md)
- [Configuration du cache L2](level-two-cache.md)

Consultez la [Documentation Laminas](https://docs.laminas.dev/) pour connaître les options héritées basées sur Zend.
