---
title: Options de cache
description: Découvrez les options de cache de bas niveau et la configuration du stockage dans Adobe Commerce. Découvrez la configuration frontale, principale et de stockage pour Redis et les bases de données.
feature: Configuration, Cache
exl-id: e0330108-5c55-4a33-9f93-63fbb71af761
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '112'
ht-degree: 0%

---

# Options de cache de bas niveau

L’application Commerce utilise un cache de bas niveau frontal et principal pour permettre l’accès à l’espace de stockage du cache.

## Cache frontal de bas niveau

Commerce étend [Zend_Cache_Core](https://framework.zend.com/manual/1.12/en/zend.cache.frontends.html) en implémentant le cache frontal [Magento\Framework\Cache\Core](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Cache/Core.php).

## Cache du serveur principal de bas niveau

En règle générale, l’application Commerce fonctionne avec n’importe quel cache principal pris en charge par [Zend_Cache Backends](https://framework.zend.com/manual/1.12/en/zend.cache.backends.html). Cependant, ce guide ne couvre que les caches principaux de bas niveau suivants :

- [Redis](config-redis.md)
- [&#x200B; Base de données &#x200B;](https://developer.adobe.com/commerce/php/development/cache/partial/database-caching/)
- Système de fichiers (par défaut) : aucune configuration n’est nécessaire pour utiliser la mise en cache du système de fichiers.

[Vernis](config-varnish.md) ne nécessite pas la configuration d’un serveur principal de cache de bas niveau.
