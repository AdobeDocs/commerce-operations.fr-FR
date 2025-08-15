---
title: Bonnes pratiques relatives à la configuration du service Redis
description: Découvrez comment améliorer les performances de la mise en cache à l’aide de l’implémentation du cache Redis étendue pour Adobe Commerce.
role: Developer, Admin
feature: Best Practices, Cache
exl-id: 8b3c9167-d2fa-4894-af45-6924eb983487
source-git-commit: bbebb414ae3b8c255e17b1f3673a6c4b7c6f23b2
workflow-type: tm+mt
source-wordcount: '840'
ht-degree: 0%

---

# Bonnes pratiques relatives à la configuration du service Redis

- Configuration du cache L2 Redis
- Activer la connexion esclave Redis
- Pré-charger les clés
- Activer le cache obsolète
- Séparer le cache Redis de la session Redis
- Compressez le cache Redis et utilisez `gzip` pour une compression plus élevée

## Configuration du cache L2 Redis

Configurez le cache Redis L2 en définissant la variable de déploiement `REDIS_BACKEND` dans le fichier de configuration `.magento.env.yaml`.

```yaml
stage:
  deploy:
    REDIS_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
```

Pour la configuration de l’environnement sur l’infrastructure cloud, consultez la [`REDIS_BACKEND`](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#redis_backend) dans le guide _Commerce sur l’infrastructure cloud_.

Pour les installations sur site, consultez [Configuration de la mise en cache de page Redis](../../../configuration/cache/redis-pg-cache.md#configure-redis-page-caching) dans le _Guide de configuration_.

>[!NOTE]
>
>Vérifiez que vous utilisez la dernière version du package `ece-tools`. Sinon, [effectuez une mise à niveau vers la dernière version](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/update-package.html). Vous pouvez vérifier la version installée dans votre environnement local à l’aide de la commande de l’interface de ligne de commande `composer show magento/ece-tools`.


### Dimensionnement de la mémoire cache L2 (Adobe Commerce Cloud)

Le cache L2 utilise un [ système de fichiers temporaire ](https://en.wikipedia.org/wiki/Tmpfs) comme mécanisme de stockage. Par rapport aux systèmes de base de données clé-valeur spécialisés, un système de fichiers temporaires ne dispose pas d’une politique d’éviction des clés pour contrôler l’utilisation de la mémoire.

L’absence de contrôle de l’utilisation de la mémoire peut entraîner une augmentation de l’utilisation de la mémoire cache L2 au fil du temps en accumulant le cache obsolète.

Pour éviter l’épuisement de la mémoire des implémentations du cache L2, Adobe Commerce efface le stockage lorsqu’un certain seuil est atteint. La valeur de seuil par défaut est de 95 %.

Il est important d’ajuster l’utilisation maximale de la mémoire cache L2 en fonction des exigences du projet pour le stockage en cache. Utilisez l’une des méthodes suivantes pour configurer le dimensionnement du cache de mémoire :

- Créez un ticket d’assistance pour demander des modifications de taille du montage `/dev/shm`.
- Ajustez la propriété `cleanup_percentage` au niveau de l’application pour limiter le pourcentage de remplissage maximal du stockage. La mémoire libre restante peut être utilisée par d’autres services.
Vous pouvez ajuster la configuration dans la configuration de déploiement sous le groupe de configuration du cache `cache/frontend/default/backend_options/cleanup_percentage`.

>[!NOTE]
>
>L’option configurable `cleanup_percentage` a été introduite dans Adobe Commerce 2.4.4.

Le code suivant illustre un exemple de configuration dans le fichier `.magento.env.yaml` :

```yaml
stage:
  deploy:
    REDIS_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default:
          backend_options:
            cleanup_percentage: 90
```

Les exigences de cache peuvent varier en fonction de la configuration du projet et du code tiers personnalisé. La portée du dimensionnement de la mémoire cache L2 permet au cache L2 de fonctionner sans trop d’accès au seuil.
Idéalement, l’utilisation de la mémoire cache L2 doit se stabiliser à un certain niveau en dessous du seuil, afin d’éviter des effacements de stockage fréquents.

Vous pouvez vérifier l’utilisation de la mémoire cache L2 sur chaque nœud du cluster à l’aide de la commande d’interface de ligne de commande suivante et en recherchant la ligne `/dev/shm`.
L’utilisation peut varier d’un nœud à l’autre, mais elle doit converger vers la même valeur.

```bash
df -h
```

## Activer la connexion esclave Redis

Activez une connexion esclave Redis dans le fichier de configuration `.magento.env.yaml` pour permettre à un seul nœud de gérer le trafic en lecture-écriture tandis que les autres nœuds gèrent le trafic en lecture seule.

```yaml
stage:
  deploy:
    REDIS_USE_SLAVE_CONNECTION: true
```

Voir [REDIS_USE_SLAVE_CONNECTION](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#redis_use_slave_connection) dans le _Guide de Commerce sur les infrastructures cloud_.

Pour les installations sur site d’Adobe Commerce, configurez la nouvelle mise en œuvre du cache Redis à l’aide des commandes `bin/magento:setup`. Voir [Utiliser Redis pour le cache par défaut](../../../configuration/cache/redis-pg-cache.md#configure-redis-page-caching) dans le _Guide de configuration_.

>[!WARNING]
>
>Ne configurez _pas_ une connexion esclave Redis pour les projets d’infrastructure cloud avec une [architecture mise à l’échelle/partagée](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/scaled-architecture.html). Cela entraîne des erreurs de connexion Redis. Voir [Guide de configuration Redis](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#redis_use_slave_connection) dans le guide _Commerce sur les infrastructures cloud_.

## Pré-charger les clés

Pour réutiliser les données entre les pages, répertoriez les clés à précharger dans le fichier de configuration `.magento.env.yaml`.

```yaml
stage:
  deploy:
    REDIS_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default:
          id_prefix: '061_'                       # Prefix for keys to be preloaded
          backend_options:
            preload_keys:                         # List the keys to be preloaded
              - '061_EAV_ENTITY_TYPES:hash'
              - '061_GLOBAL_PLUGIN_LIST:hash'
              - '061_DB_IS_UP_TO_DATE:hash'
              - '061_SYSTEM_DEFAULT:hash'
```

Pour les installations sur site, consultez la section [Fonctionnalité de préchargement Redis](../../../configuration/cache/redis-pg-cache.md#redis-preload-feature) du _Guide de configuration_.

## Activer le cache obsolète

Réduisez les temps d’attente de verrouillage et améliorez les performances, en particulier lorsque vous traitez de nombreux blocs et clés de cache, en utilisant un cache obsolète tout en générant un nouveau cache en parallèle. Activez le cache obsolète et définissez les types de cache dans le fichier de configuration `.magento.env.yaml` :

```yaml
stage:
  deploy:
    REDIS_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
    CACHE_CONFIGURATION:
      _merge: true
      default:
        backend_options:
          use_stale_cache: false
      stale_cache_enabled:
        backend_options:
          use_stale_cache: true
      type:
        default:
          frontend: "default"
        layout:
          frontend: "stale_cache_enabled"
        block_html:
          frontend: "stale_cache_enabled"
        reflection:
          frontend: "stale_cache_enabled"
        config_integration:
          frontend: "stale_cache_enabled"
        config_integration_api:
          frontend: "stale_cache_enabled"
        full_page:
          frontend: "stale_cache_enabled"
        translate:
          frontend: "stale_cache_enabled"
```

>[!NOTE]
>
>Dans l’exemple précédent, le cache `full_page` n’est pas pertinent pour Adobe Commerce sur les projets d’infrastructure cloud, car ils utilisent [Fastly](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/fastly).

Pour la configuration des installations sur site, consultez [Options de cache obsolètes](../../../configuration/cache/level-two-cache.md#stale-cache-options) dans le _Guide de configuration_.

## Séparer le cache Redis des instances de session

La séparation du cache Redis de la session Redis vous permet de gérer le cache et les sessions indépendamment. Cela empêche les problèmes de cache d’affecter les sessions, ce qui pourrait avoir un impact sur le chiffre d’affaires. Chaque instance Redis s’exécute sur son propre noyau, ce qui améliore les performances.

1. Mettez à jour le fichier de configuration `.magento/services.yaml`.

   ```yaml
   mysql:
       type: mysql:10.4
       disk: 35000
   
   redis:
      type: redis:6.0
   
   redis-session:              # This is for the new Redis instance
      type: redis:6.0
   
   search:
      type: elasticsearch:7.9
      disk: 5000
   
   rabbitmq:
      type: rabbitmq:3.8
      disk: 2048
   ```

1. Mettez à jour le fichier de configuration `.magento.app.yaml`.

   ```yaml
   relationships:
       database: "mysql:mysql"
       redis: "redis:redis"
       redis-session: "redis-session:redis"   # Relationship of the new Redis instance
       search: "search:elasticsearch"
       rabbitmq: "rabbitmq:rabbitmq"
   ```

1. Envoyez un [ticket d’assistance Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket) pour demander la mise en service d’une nouvelle instance Redis dédiée aux sessions dans les environnements de production et d’évaluation. Incluez les fichiers de configuration `.magento/services.yaml` et `.magento.app.yaml` mis à jour. Cela n’entraîne pas d’interruption, mais un déploiement est nécessaire pour activer le nouveau service.

1. Vérifiez que la nouvelle instance est en cours d’exécution et notez le numéro de port.

   ```bash
   echo $MAGENTO_CLOUD_RELATIONSHIPS | base64 -d | json_pp
   ```

1. Ajoutez le numéro de port au fichier de configuration `.magento.env.yaml`.

   >[!IMPORTANT]
   >
   >Configurez le port de session Redis uniquement si `ece-tools` ne parvient pas à le détecter automatiquement à partir de la définition du service de session `MAGENTO_CLOUD_RELATIONSHIPS` Redis.

   >[!NOTE]
   >
   >`disable_locking` doit être défini sur `1`.

   ```yaml
   SESSION_CONFIGURATION:
     _merge: true
     redis:
       port: 6374 # check the port in $MAGENTO_CLOUD_RELATIONSHIPS and put it here (by default, you can delete this line!!)
       timeout: 5
       disable_locking: 1
       bot_first_lifetime: 60
       bot_lifetime: 7200
       max_lifetime: 2592000
       min_lifetime: 60
   ```

1. Supprimez les sessions de la [base de données par défaut](../../../configuration/cache/redis-pg-cache.md) (`db 0`) sur l’instance de cache Redis.

   ```bash
   redis-cli -h 127.0.0.1 -p 6374 -n 0 FLUSHDB
   ```

Pendant le déploiement, les lignes suivantes doivent s’afficher dans le [journal de génération et de déploiement](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/log-locations.html#build-and-deploy-logs) :

```
W:   - Downloading colinmollenhour/credis (1.11.1)
W:   - Downloading colinmollenhour/php-redis-session-abstract (v1.4.5)
...
W:   - Installing colinmollenhour/credis (1.11.1): Extracting archive
W:   - Installing colinmollenhour/php-redis-session-abstract (v1.4.5): Extracting archive
...
[2022-08-17 01:13:40] INFO: Version of service 'redis' is 6.0
[2022-08-17 01:13:40] INFO: Version of service 'redis-session' is 6.0
[2022-08-17 01:13:40] INFO: redis-session will be used for session if it was not override by SESSION_CONFIGURATION
```

## Compression du cache

Si vous utilisez plus de 6 Go de Redis `maxmemory`, vous pouvez utiliser la compression du cache pour réduire l’espace consommé par les clés. Sachez qu&#39;il y a un compromis à faire avec le rendement côté client. Si vous disposez de processeurs supplémentaires, activez-les. Voir [Utilisation de Redis pour le stockage de session](../../../configuration/cache/redis-session.md) dans le _Guide de configuration_.

```yaml
stage:
  deploy:
    REDIS_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
    CACHE_CONFIGURATION:
      _merge: true;
      frontend:
        default:
          backend_options:
            compress_data: 4              # 0-9
            compress_tags: 4              # 0-9
            compress_threshold: 20480     # don't compress files smaller than this value
            compression_lib: 'gzip'       # snappy and lzf for performance, gzip for high compression (~69%)
```

## Informations supplémentaires

- [Redéfinir le cache de page](../../../configuration/cache/redis-pg-cache.md)
- [Utilisation de Redis pour le stockage de session](../../../configuration/cache/redis-session.md)
