---
title: Bonnes pratiques relatives à la configuration du service Valkey
description: Découvrez comment améliorer les performances de mise en cache à l’aide de l’implémentation de cache Valkey étendue pour Adobe Commerce.
role: Developer, Admin
feature: Best Practices, Cache
exl-id: ca1598b0-07c6-4338-aed1-f2ba05375197
source-git-commit: 75dc606da65196619028e99ec44841db3988a73e
workflow-type: tm+mt
source-wordcount: '672'
ht-degree: 0%

---

# Bonnes pratiques relatives à la configuration du service Valkey

Adobe recommande les bonnes pratiques suivantes lors de la configuration du service Valkey :

## Configuration du cache Valkey L2

Configurez le cache Valkey L2 en définissant la variable de déploiement `VALKEY_BACKEND` dans le fichier de configuration `.magento.env.yaml`.

```yaml
stage:
  deploy:
    VALKEY_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
```

Pour la configuration de l’environnement sur l’infrastructure cloud, consultez la [`VALKEY_BACKEND`](https://experienceleague.adobe.com/fr/docs/commerce-on-cloud/user-guide/configure/env/stage/variables-deploy#valkey_backend) dans le guide _Commerce sur l’infrastructure cloud_.

Pour les installations sur site, consultez [Configuration de la mise en cache de page Valkey](../../../configuration/cache/valkey-pg-cache.md#configure-page-caching) dans le _Guide de configuration_.

>[!NOTE]
>
>Vérifiez que vous utilisez la dernière version du package `ece-tools`. Sinon, [effectuez une mise à niveau vers la dernière version](https://experienceleague.adobe.com/fr/docs/commerce-on-cloud/user-guide/dev-tools/ece-tools/update-package). Vous pouvez vérifier la version installée dans votre environnement local à l’aide de la commande de l’interface de ligne de commande `composer show magento/ece-tools`.

### Dimensionnement de la mémoire cache L2 (Adobe Commerce Cloud)

Le cache L2 utilise un [&#x200B; système de fichiers temporaire &#x200B;](https://en.wikipedia.org/wiki/Tmpfs) comme mécanisme de stockage. Par rapport aux systèmes de base de données clé-valeur spécialisés, un système de fichiers temporaires ne dispose pas d’une politique d’éviction des clés pour contrôler l’utilisation de la mémoire.

L’absence de contrôle de l’utilisation de la mémoire peut entraîner une augmentation de l’utilisation de la mémoire cache L2 au fil du temps en accumulant le cache obsolète.

Pour éviter l’épuisement de la mémoire des implémentations du cache L2, Adobe Commerce efface le stockage lorsqu’un certain seuil est atteint. La valeur de seuil par défaut est de 95 %.

Il est important d’ajuster l’utilisation maximale de la mémoire cache L2 en fonction des exigences du projet pour le stockage en cache. Utilisez l’une des méthodes suivantes pour configurer le dimensionnement du cache de mémoire :

- Créez un ticket d’assistance pour demander des modifications de taille du montage `/dev/shm`.
- Ajustez la propriété `cleanup_percentage` au niveau de l’application pour limiter le pourcentage de remplissage maximal du stockage. La mémoire libre restante peut être utilisée par d’autres services.
Vous pouvez ajuster la configuration dans la configuration de déploiement sous le groupe de configuration du cache `cache/frontend/default/backend_options/cleanup_percentage`.

>[!NOTE]
>
>L’option de configuration `cleanup_percentage` a été introduite dans Adobe Commerce 2.4.4.

L’exemple suivant illustre un `CACHE_CONFIGURATION` dans le fichier `.magento.env.yaml` :

```yaml
stage:
  deploy:
    VALKEY_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default:
          backend_options:
            cleanup_percentage: 90
```

Les exigences de cache peuvent varier en fonction de la configuration du projet et du code tiers personnalisé. La portée du dimensionnement de la mémoire cache L2 permet au cache L2 de fonctionner sans accès au seuil inutiles.
Idéalement, l’utilisation de la mémoire cache L2 doit se stabiliser à un certain niveau en dessous du seuil, afin d’éviter des effacements de stockage fréquents.

Vous pouvez vérifier l’utilisation de la mémoire cache L2 sur chaque nœud du cluster à l’aide de la commande d’interface de ligne de commande suivante, puis en recherchant la ligne de `/dev/shm`.
L’utilisation peut varier d’un nœud à l’autre, mais elle doit converger vers la même valeur.

```bash
df -h
```

## Activer la connexion esclave à Valkey

Activez une connexion esclave Valkey dans le fichier de configuration `.magento.env.yaml` pour permettre à un seul nœud de gérer le trafic en lecture-écriture tandis que les autres nœuds gèrent le trafic en lecture seule.

```yaml
stage:
  deploy:
    VALKEY_USE_SLAVE_CONNECTION: true
```

Pour plus d’informations, consultez [VALKEY_USE_SLAVE_CONNECTION](https://experienceleague.adobe.com/fr/docs/commerce-on-cloud/user-guide/configure/env/stage/variables-deploy#valkey_use_slave_connection) dans le guide _Commerce sur les infrastructures cloud_.

Pour les installations sur site d’Adobe Commerce, configurez la nouvelle implémentation du cache Valkey à l’aide des commandes `bin/magento:setup`. Pour plus d’informations, consultez [Utilisation de Valkey pour le cache par défaut](../../../configuration/cache/valkey-pg-cache.md#configure-page-caching) dans le _Guide de configuration_.

>[!WARNING]
>
>Ne configurez _pas_ une connexion esclave Valkey pour les projets d’infrastructure cloud avec une [architecture mise à l’échelle/partagée](https://experienceleague.adobe.com/fr/docs/commerce-on-cloud/user-guide/architecture/scaled-architecture). Cela entraîne des erreurs de connexion Valkey. Pour plus d’informations, consultez le guide de configuration [Valkey](https://experienceleague.adobe.com/fr/docs/commerce-on-cloud/user-guide/configure/env/stage/variables-deploy#valkey_use_slave_connection) dans le guide _Commerce sur les infrastructures cloud_.

## Pré-charger les clés

Pour réutiliser les données entre les pages, répertoriez les clés à précharger dans le fichier de configuration `.magento.env.yaml`.

```yaml
stage:
  deploy:
    VALKEY_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
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

Pour les installations sur site, consultez la section [Fonctionnalité de préchargement Valkey](../../../configuration/cache/valkey-pg-cache.md#valkey-preload-feature) du _Guide de configuration_.

## Activer le cache obsolète

Réduire les temps d’attente de verrouillage et améliorer les performances, en particulier lorsque vous traitez de nombreux blocs et clés de cache, en utilisant un cache obsolète tout en générant un nouveau cache en parallèle. Activez le cache obsolète et définissez les types de cache dans le fichier de configuration `.magento.env.yaml` :

```yaml
stage:
  deploy:
    VALKEY_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
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
>Dans l’exemple précédent, le cache `full_page` n’est pas pertinent pour Adobe Commerce sur les projets d’infrastructure cloud, car ils utilisent [Fastly](https://experienceleague.adobe.com/fr/docs/commerce-on-cloud/user-guide/cdn/fastly).

Pour la configuration des installations sur site, consultez [Options de cache obsolètes](../../../configuration/cache/level-two-cache.md#stale-cache-options) dans le _Guide de configuration_.

Pendant le déploiement, les lignes suivantes doivent s’afficher dans le [journal de génération et de déploiement](https://experienceleague.adobe.com/fr/docs/commerce-on-cloud/user-guide/develop/test/log-locations#build-and-deploy-logs) :

```
W:   - Downloading colinmollenhour/credis (1.11.1)
W:   - Downloading colinmollenhour/php-redis-session-abstract (v1.4.5)
...
W:   - Installing colinmollenhour/credis (1.11.1): Extracting archive
W:   - Installing colinmollenhour/php-redis-session-abstract (v1.4.5): Extracting archive
...
[2022-08-17 01:13:40] INFO: Version of service 'valkey' is 8.0
[2022-08-17 01:13:40] INFO: Version of service 'valkey-session' is 8.0
[2022-08-17 01:13:40] INFO: valkey-session will be used for the session if it was not overridden by SESSION_CONFIGURATION.
```

## Compression du cache

Si vous utilisez plus de 6 Go de `maxmemory` Valkey, vous pouvez utiliser la compression du cache pour réduire l’espace consommé par les clés. Sachez qu&#39;il y a un compromis à faire avec le rendement côté client. Si vous disposez de processeurs supplémentaires, Adobe suggère de les activer. Voir [Utilisation de Valkey pour le stockage de session](../../../configuration/cache/valkey-session.md) dans le _Guide de configuration_.

```yaml
stage:
  deploy:
    VALKEY_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
    CACHE_CONFIGURATION:
      _merge: true;
      frontend:
        default:
          backend_options:
            compress_data: 4              # 0-9
            compress_tags: 4              # 0-9
            compress_threshold: 20480     # do not compress files smaller than this value
            compression_lib: 'gzip'       # snappy and lzf for performance, gzip for high compression (~70%)
```
