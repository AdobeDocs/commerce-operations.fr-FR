---
title: Options de cache
description: Configurez l’accès au stockage du cache de bas niveau.
feature: Configuration, Cache
exl-id: e0330108-5c55-4a33-9f93-63fbb71af761
source-git-commit: a2bd4139aac1044e7e5ca8fcf2114b7f7e9e9b68
workflow-type: tm+mt
source-wordcount: '97'
ht-degree: 0%

---

# Options de cache de bas niveau

L’application Commerce utilise un serveur frontal et un serveur principal de cache de bas niveau pour permettre l’accès au stockage du cache.

## Cache frontal de bas niveau

Commerce étend [Zend_Cache_Core](https://framework.zend.com/manual/1.12/en/zend.cache.frontends.html) en implémentant le cache frontal [Magento\Framework\Cache\Core](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Cache/Core.php).

## Cache principal de bas niveau

En règle générale, l’application Commerce fonctionne avec tout cache d’arrière-plan que [Zend_Cache Backends](https://framework.zend.com/manual/1.12/en/zend.cache.backends.html) prend en charge. Toutefois, ce guide couvre uniquement les caches d’arrière-plan de bas niveau suivants :

- [Redis](config-redis.md)
- [Base de données](https://developer.adobe.com/commerce/php/development/cache/partial/database-caching/)
- Système de fichiers (par défaut) : aucune configuration n’est nécessaire pour utiliser la mise en cache du système de fichiers.

[Varnish](config-varnish.md) ne nécessite pas de configuration d’un serveur principal de cache de bas niveau.
