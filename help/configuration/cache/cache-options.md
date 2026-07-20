---
title: Options du serveur principal de mise en cache et référence de stockage
description: Découvrez les options du serveur principal de cache dans Adobe Commerce, notamment le système de fichiers, Redis, Valkey et le stockage dans la base de données. Découvrez les approches héritées et modernes.
feature: Configuration, Cache
exl-id: e0330108-5c55-4a33-9f93-63fbb71af761
badgePaas: label="Sur Site" type="Informative" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="S’applique uniquement aux projets sur site Adobe Commerce."
autotag-review: '2026-06-22T18:37:32.504Z'
TQID: 'https://experienceleague.adobe.com/m7eUBNrt8UF43iJq9Tpl0Y1WcmR-dlt7Z4PoHvXVNnA'
product_v2: id: b974b164-8a4e-43b8-a9e2-8e67ec131677id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2: id: dac87252-6066-4d6e-a9d2-f6d84c323de7
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2: id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2: id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
source-git-commit: a7e44e5b4ddeda89b9fee08aa29b1a31f521e90a
workflow-type: tm+mt
source-wordcount: 362
ht-degree: 0%

---

# Mettre en cache les options principales et la référence de stockage

{{cloud-cache-config}}

L’application Commerce utilise un cache de bas niveau frontal et principal pour permettre l’accès au stockage du cache. Commerce prend en charge plusieurs stratégies et back-ends de mise en cache, chacun adapté à différents cas d’utilisation. Cette page décrit les serveurs principaux disponibles et leurs différences.

>[!NOTE]
>
>[Vernis](config-varnish.md) gère la mise en cache de pleine page au niveau HTTP et n’utilise pas le serveur principal du cache de bas niveau.

## Options de cache du serveur principal

Le tableau suivant résume les caches principaux disponibles :

| Serveur principal | Description | Guide de configuration |
| ------- | ----------- | ------------------- |
| Système de fichiers | Valeur par défaut. Stocke les données de cache dans des fichiers sous `var/cache/`. Aucune configuration requise. | S.O. |
| [Redis ](config-redis.md) | Magasin de données en mémoire pour une mise en cache hautes performances. | [Utiliser Redis pour le cache par défaut](redis-pg-cache.md)<br>**Remarque : le cache Redis n’est pas pris en charge pour Adobe Commerce 2.4.9 ou les versions de correctif ultérieures à 2.4.5-p16, 2.4.6-p14, 2.4.7-p9 et 2.4.8-p5. Utilisez Valkey pour la configuration du cache lorsque Redis n’est pas pris en charge. Consultez [Configuration requise](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/system-requirements) pour connaître les services de cache pris en charge par version. |
| [ Valkey ](config-valkey.md) | Alternative open source compatible avec Redis. | [Utiliser Valkey pour le cache par défaut](valkey-pg-cache.md) |
| [ Base de données ](https://developer.adobe.com/commerce/php/development/cache/partial/database-caching/) | Mise en cache de base de données. | [Création de moteurs de cache personnalisés](https://developer.adobe.com/commerce/php/development/cache/partial/database-caching/){target="_blank"} (documentation Adobe destinée aux développeurs) |

{{redis-cache-support}}

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
