---
title: Options de cache
description: Configurez l’accès au stockage du cache de bas niveau.
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '125'
ht-degree: 0%

---

# Options de cache de bas niveau

L’application Commerce utilise un serveur frontal et un serveur principal de cache de bas niveau pour fournir l’accès au stockage du cache.

## Cache frontal de bas niveau

Le commerce étend [Zend_Cache_Core](https://framework.zend.com/manual/1.12/en/zend.cache.frontends.html) en implémentant [Magento\Framework\Cache\Core](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Cache/Core.php) cache frontal.

## Cache principal de bas niveau

En règle générale, l’application Commerce fonctionne avec tout cache principal qui [Zend_Cache Backends](https://framework.zend.com/manual/1.12/en/zend.cache.backends.html) prend en charge . Toutefois, ce guide couvre uniquement les caches d’arrière-plan de bas niveau suivants :

- [Redis](config-redis.md)
- [Base](https://developer.adobe.com/commerce/php/development/cache/partial/database-caching/)
- Système de fichiers (par défaut) : Aucune configuration n’est nécessaire pour utiliser la mise en cache du système de fichiers.

[Varnish](config-varnish.md) ne nécessite pas de configuration d’un serveur principal de cache de bas niveau.
