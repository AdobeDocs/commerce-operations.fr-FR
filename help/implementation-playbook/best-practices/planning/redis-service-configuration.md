---
title: Bonnes pratiques relatives à la configuration du service Redis
description: Découvrez comment améliorer les performances de mise en cache à l’aide de la mise en oeuvre étendue du cache Redis pour Adobe Commerce.
role: Developer, Admin
feature: Best Practices, Cache
exl-id: 8b3c9167-d2fa-4894-af45-6924eb983487
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '439'
ht-degree: 0%

---

# Bonnes pratiques relatives à la configuration du service Redis

- Utilisez l’implémentation étendue du cache Redis, qui inclut les optimisations suivantes afin de minimiser le nombre de requêtes Redis exécutées sur chaque requête d’Adobe Commerce :
   - Diminue la taille des transferts de données réseau entre Redis et Adobe Commerce
   - Réduit la consommation des cycles du processeur en améliorant la capacité de l’adaptateur à déterminer automatiquement ce qui doit être chargé.
   - Réduit les conditions de concurrence sur les opérations d’écriture Redis
- Séparez le cache Redis de la session Redis
- Compressez le cache Redis et utilisez `gzip` pour améliorer les performances

## Mise en oeuvre étendue du cache Redis

Mettez à jour votre configuration pour utiliser l’implémentation du cache Redis étendu. `\Magento\Framework\Cache\Backend\Redis`.

### Configuration des déploiements cloud

Configurez le cache Redis amélioré en définissant la variable `REDIS_BACKEND` de déploiement dans la variable `.magento.env.yaml` fichier de configuration.

```yaml
stage:
  deploy:
    REDIS_BACKEND: '\Magento\Framework\Cache\Backend\Redis'
```

Pour plus d’informations, voir [`REDIS_BACKEND`](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#redis_backend) description de la variable dans la variable _Guide d’infrastructure de Commerce on Cloud_.

>[!NOTE]
>
> Vérifiez les `ece-tools` version installée dans votre environnement local à partir de la ligne de commande à l’aide de la fonction `composer show magento/ece-tools` . Si nécessaire, [mettre à jour vers la dernière version](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/update-package.html).

>[!WARNING]
>
>Do _not_ configurer une connexion Redis Secondaire pour les projets d’infrastructure cloud avec une [architecture mise à l’échelle](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/scaled-architecture.html). Cela entraîne des erreurs de connexion Redis. Voir [les instructions de configuration Redis ;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#redis_use_slave_connection) dans le _Commerce sur l’infrastructure cloud_ guide.

### Configuration des déploiements sur site

Pour les déploiements sur site d’Adobe Commerce, configurez la nouvelle mise en oeuvre du cache Redis à l’aide du `bin/magento:setup` des commandes. Pour obtenir des instructions, voir [Utiliser des redis pour le cache par défaut](../../../configuration/cache/redis-pg-cache.md#configure-redis-page-caching).

## Séparation des instances de cache et de session

La séparation du cache Redis de la session Redis vous permet de gérer le cache et les sessions indépendamment afin d’empêcher les problèmes de cache d’affecter les sessions.

1. Mettez à jour le `.magento/services.yaml` fichier de configuration.

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

1. Mettez à jour le `.magento.app.yaml` fichier de configuration.

   ```yaml
   relationships:
       database: "mysql:mysql"
       redis: "redis:redis"
       redis-session: "redis-session:redis"   # Relationship of the new Redis instance
       search: "search:elasticsearch"
       rabbitmq: "rabbitmq:rabbitmq"
   ```

1. Envoyer un [ticket d’assistance Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket) pour modifier la configuration du service Redis dans les environnements de production et d’évaluation Pro. Inclure la mise à jour `.magento/services.yaml` et `.magento.app.yaml` fichiers de configuration.

1. Vérifiez que la nouvelle instance est en cours d’exécution et notez le numéro de port.

   ```bash
   echo $MAGENTO_CLOUD_RELATIONSHIPS | base64 -d | json_pp
   ```

1. Ajoutez le numéro de port au `.magento.env.yaml` fichier de configuration.

   >[!NOTE]
   >`disable_locking` doit être défini sur `1`.
   >   

   ```yaml
   SESSION_CONFIGURATION:
     _merge: true
     redis:
       port: 6374       # check the port in $MAGENTO_CLOUD_RELATIONSHIPS
       timeout: 5
       disable_locking: 1
       bot_first_lifetime: 60
       bot_lifetime: 7200
       max_lifetime: 2592000
       min_lifetime: 60
   ```

1. Supprimer des sessions du [base de données par défaut](../../../configuration/cache/redis-pg-cache.md) (`db 0`) sur l’instance de cache Redis.

   ```bash
   redis-cli -h 127.0.0.1 -p 6374 -n 0 FLUSHDB
   ```

Au cours du déploiement, les lignes suivantes doivent s’afficher dans le [journal de création et de déploiement](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/log-locations.html#build-and-deploy-logs):

```terminal
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

Utilisez la compression du cache, mais sachez qu’il existe un compromis avec les performances côté client. Si vous disposez de spare CPU, activez-le. Voir [Utilisation de Redis pour le stockage de session](../../../configuration/cache/redis-session.md).

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

- [Redis Page Cache](../../../configuration/cache/redis-pg-cache.md)
- [Utilisation de Redis pour le stockage de session](../../../configuration/cache/redis-session.md)
