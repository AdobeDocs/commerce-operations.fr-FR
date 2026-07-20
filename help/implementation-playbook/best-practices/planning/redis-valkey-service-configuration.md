---
title: Bonnes pratiques relatives à la configuration des services Valkey et Redis
description: Découvrez comment configurer les services Valkey et Redis pour Adobe Commerce. Améliorez les performances du cache avec le cache L2, les connexions de réplication, le cache obsolète et les sessions.
solution: Commerce
role: Developer, Admin
level: Intermediate
feature: Best Practices, Cache
feature-set: Commerce
topic: Performance
exl-id: 8b3c9167-d2fa-4894-af45-6924eb983487
badgePaas: label="Commerce sur le cloud" type="Informative" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="S’applique uniquement à Adobe Commerce sur les projets cloud."
source-git-commit: f4209adaa964ed1f530c90cc21dfd97ca299416b
workflow-type: tm+mt
source-wordcount: '2347'
ht-degree: 0%

---


# Bonnes pratiques pour la configuration des services Valkey et Redis

Utilisez ces recommandations pour configurer la mise en cache et les sessions Valkey ou Redis pour Adobe Commerce sur l’infrastructure cloud. Pour la configuration du cache sur site, voir [Options de cache et référence de stockage](../../../configuration/cache/cache-options.md).

- Configuration du cache L2, y compris [!DNL Symfony] cache L2
- Activer la connexion de réplication en lecture seule
- Précharger les clés
- Activer le cache obsolète
- Séparer le cache et la session
- Compresser le cache
- Consulter les exemples de configuration

>[!NOTE]
>
>Vérifiez que vous utilisez la dernière version du package `ece-tools`. Sinon, [effectuez une mise à niveau vers la dernière version](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/dev-tools/ece-tools/update-package). Vous pouvez vérifier la version installée dans votre environnement local à l’aide de la commande de l’interface de ligne de commande `composer show magento/ece-tools`.

## Configurer le cache L2

Configurez le cache L2 en définissant la variable de déploiement `VALKEY_BACKEND` ou `REDIS_BACKEND` dans le fichier de configuration `.magento.env.yaml`.

Pour Adobe Commerce 2.4.9 et les versions ultérieures aux versions 2.4.8-p4, 2.4.7-p9, 2.4.6-p14 et 2.4.5-p16, configurez le cache L2 avec Valkey. Les exemples de configuration Redis de cette page s’appliquent uniquement aux versions d’Adobe Commerce prises en charge qui utilisent Redis. Consultez [Configuration requise](../../../installation/system-requirements.md) pour connaître les services de cache pris en charge par version.

Pour obtenir des détails d’implémentation, des exemples de configuration et des conseils spécifiques au déploiement, consultez [Configuration du cache L2 pour l’optimisation des performances](../../../configuration/cache/level-two-cache.md).

>[!IMPORTANT]
>
>Le cache Redis n’est pas pris en charge pour Adobe Commerce 2.4.9 ou pour les versions de correctif ultérieures à 2.4.5-p16, 2.4.6-p14, 2.4.7-p9 et 2.4.8-p4. Utilisez Valkey pour la configuration du cache lorsque Redis n’est pas pris en charge. Consultez [Configuration requise](../../../installation/system-requirements.md) pour connaître les services de cache pris en charge par version.

>[!BEGINTABS]

>[!TAB Configuration Valkey]

Pour Valkey, utilisez :

```yaml
stage:
  deploy:
    VALKEY_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
```

Pour plus d’informations sur la configuration de l’environnement, consultez [`VALKEY_BACKEND`](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/env/stage/variables-deploy#valkey_backend) variables de configuration dans le guide _Commerce sur les infrastructures cloud_.

>[!TAB Configuration Redis]

Pour Redis, utilisez :

```yaml
stage:
  deploy:
    REDIS_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
```

Pour plus d’informations sur la configuration de l’environnement, consultez la [`REDIS_BACKEND`](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/env/stage/variables-deploy#redis_backend) dans le guide _Commerce sur les infrastructures cloud_.

>[!ENDTABS]

### Configurer [!DNL Symfony] cache L2

Adobe Commerce 2.4.9 et versions ultérieures prennent en charge le serveur principal de cache `symfony_l2`. Le serveur principal `symfony_l2` est l’implémentation du cache qu’Adobe Commerce utilise pour gérer le comportement du cache L1 et L2. Il ne remplace pas Redis ou Valkey comme service de cache à distance.

>[!IMPORTANT]
>
>Ne configurez pas `symfony_l2` manuellement dans `app/etc/env.php` en tant que configuration persistante pour Adobe Commerce sur l’infrastructure cloud. Le déploiement peut remplacer les modifications de `env.php` manuelles. Si `ece-tools` ne s’applique pas `symfony_l2`, Commerce peut revenir au cache basé sur les fichiers. Cette solution de secours peut augmenter les E/S de disque, augmenter la surcharge de réplication du système de fichiers sur les environnements à plusieurs nœuds et dégrader les performances.

Pour utiliser `symfony_l2` cache pour Adobe Commerce 2.4.9, procédez comme suit :

- Assurez-vous que le projet cloud utilise le package [ECE Tools v2002.1.12](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/dev-tools/ece-tools/update-package) ou une version ultérieure.

- Définissez la variable de déploiement dans le fichier `.magento.env.yaml` : `VALKEY_BACKEND`=`symfony_l2`.

  ```yaml
  stage:
    deploy:
      VALKEY_BACKEND: symfony_l2
  ```

>[!CAUTION]
>
>Lors de la mise à jour de la configuration `.magento.env.yaml`, ne remplacez pas `server` ou `port`, sauf si vous pointez intentionnellement vers un point d’entrée du cache autre que le service Valkey de votre projet. Le package d&#39;outils ECE déduit automatiquement ces valeurs de votre relation de service Valkey. Leur remplacement par une valeur incorrecte entraîne l’échec du déploiement avec une erreur de connexion au cache.

La définition de la variable de déploiement `VALKEY_BACKEND` sur `symfony_l2` crée automatiquement la configuration de cache L2 complète à partir des détails de connexion au service Valkey, y compris un front-end `default` et un front-end `stale_cache_enabled`, avec des types pouvant être mis en cache tels que `layout`, `block_html`, `full_page` et `translate` déjà mappés au front-end obsolète. Vous n’avez pas besoin de définir `CACHE_CONFIGURATION` pour utiliser `symfony_l2`.

### Dimensionnement de la mémoire cache L2 pour Adobe Commerce Cloud

Le cache L2 utilise un [ système de fichiers temporaire ](https://en.wikipedia.org/wiki/Tmpfs) (`/dev/shm`) comme mécanisme de stockage. Contrairement aux magasins de valeur-clé spécialisés, tmpfs n’a pas de politique d’éviction des clés, de sorte que l’utilisation de la mémoire peut augmenter sans limite. Pour éviter l’épuisement, Adobe Commerce efface automatiquement le stockage L2 lorsque l’utilisation atteint un seuil configurable (95 % par défaut). Vous pouvez contrôler la consommation de mémoire en demandant un montage `/dev/shm` plus important ou en abaissant le seuil de nettoyage.

Ajustez l’utilisation maximale de la mémoire cache L2 en fonction des besoins de votre projet. Utilisez l’une des méthodes suivantes :

- Créez un ticket d’assistance pour ajuster la taille du montage `/dev/shm`. Pour ce scénario, Adobe recommande de définir la taille de montage `/dev/shm` sur 15 Go.
- Ajustez la propriété `cleanup_percentage` au niveau de l’application pour limiter l’utilisation du stockage et la mémoire disponible pour d’autres services.
Vous pouvez ajuster la configuration dans la configuration de déploiement sous le groupe de configuration du cache `cache/frontend/default/backend_options/cleanup_percentage`.

>[!NOTE]
>
>L’option configurable `cleanup_percentage` a été introduite dans Adobe Commerce 2.4.4.

Les exemples suivants montrent le code de configuration dans le fichier `.magento.env.yaml` :

>[!BEGINTABS]

>[!TAB Configuration Valkey]

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

>[!TAB Configuration Redis]

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

>[!ENDTABS]

Les exigences de cache varient en fonction de la configuration de votre projet et du code tiers personnalisé. Taille de la mémoire cache L2 afin que le cache puisse fonctionner sans accès fréquents au seuil.

Idéalement, l’utilisation de la mémoire cache L2 se stabilise en dessous du seuil afin d’éviter des effacements de stockage fréquents.

Vous pouvez vérifier l’utilisation de la mémoire cache L2 sur chaque nœud du cluster en exécutant la commande de ligne de commande suivante et en examinant la ligne de `/dev/shm`.

```shell
df -h /dev/shm
```

L’utilisation peut varier d’un nœud à l’autre, mais elle doit converger vers une valeur similaire.

## Activer la connexion esclave

Activez la connexion de réplica en lecture seule dans le fichier `.magento.env.yaml` pour permettre à Adobe Commerce d’utiliser une connexion de cache supplémentaire pour les lectures tout en continuant à utiliser le point d’entrée principal pour les écritures. Cette configuration peut réduire la charge de lecture sur le service de cache principal et distribuer le trafic de lecture plus efficacement.

>[!BEGINTABS]

>[!TAB Configuration Valkey]

Pour Valkey, utilisez :

```yaml
stage:
  deploy:
    VALKEY_USE_SLAVE_CONNECTION: true
```

Pour plus d’informations sur la configuration des variables d’environnement, consultez [VALKEY _USE_ SLAVE_CONNECTION](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#valkey_use_slave_connection) dans le guide _Commerce sur les infrastructures cloud_.

>[!TAB Configuration Redis]

Pour Redis, utilisez :

```yaml
stage:
  deploy:
    REDIS_USE_SLAVE_CONNECTION: true
```

Pour plus d’informations sur la configuration des variables d’environnement, consultez [REDIS _USE_ SLAVE_CONNECTION](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#redis_use_slave_connection) dans le guide _Commerce sur les infrastructures cloud_.

>[!ENDTABS]

## Précharger les clés

Magento charge généralement les entrées de cache de Redis ou de Valkey une clé à la fois. La fonction de préchargement vous permet de fournir une liste des clés fréquemment utilisées que Magento récupère dans un seul pipeline lors du premier accès lors d’une requête. Magento conserve ensuite les valeurs récupérées dans la mémoire PHP pour le reste de cette requête, ce qui réduit les allers-retours répétés vers Redis ou Valkey et peut améliorer les performances d&#39;amorçage de requête pour ces clés.

Vous pouvez identifier les clés fréquemment utilisées en surveillant les commandes actives sur Redis ou Valkey :

>[!BEGINTABS]

>[!TAB Configuration de la clé de préchargement Valkey]

Les clés de préchargement sont configurées dans le fichier de configuration `.magento.env.yaml`.

```yaml
stage:
  deploy:
    VALKEY_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default:
          id_prefix: '061_' # Prefix for keys to be preloaded, it can be any random string
          backend_options:
            preload_keys: # List the keys to be preloaded
              - '061_EAV_ENTITY_TYPES:hash' # The key name must start with the id_prefix set above
              - '061_GLOBAL_PLUGIN_LIST:hash'
              - '061_DB_IS_UP_TO_DATE:hash'
              - '061_SYSTEM_DEFAULT:hash'
```

Pour répertorier les clés, exécutez la commande suivante :

```terminal
valkey-cli -p 6370 -n 1 MONITOR > /tmp/list.keys
```

Au bout de 10 secondes, appuyez sur **[!UICONTROL Ctrl+C]**. Exécutez ensuite la commande suivante :

```terminal
cat /tmp/list.keys | grep "HGET" | awk '{print $5}' | sort | uniq -c | sort -nr | head -n 50
```

Ce journal répertorie les clés que vous pouvez précharger. Pour afficher le contenu d’une clé, exécutez la commande suivante :

```terminal
valkey-cli -p 6370 -n 1 hgetall "<key_name>"
```

>[!TAB Configuration de la clé de préchargement Redis]

Les clés de préchargement sont configurées dans le fichier de configuration `.magento.env.yaml`.

```yaml
stage:
  deploy:
    REDIS_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default:
          id_prefix: '061_' # Prefix for keys to be preloaded, it can be any random string
          backend_options:
            preload_keys: # List the keys to be preloaded
              - '061_EAV_ENTITY_TYPES:hash' # The key name must start with the id_prefix set above
              - '061_GLOBAL_PLUGIN_LIST:hash'
              - '061_DB_IS_UP_TO_DATE:hash'
              - '061_SYSTEM_DEFAULT:hash'
```

Pour répertorier les clés, exécutez la commande suivante :

```terminal
redis-cli -p 6370 -n 1 MONITOR > /tmp/list.keys
```

Au bout de 10 secondes, appuyez sur **[!UICONTROL Ctrl+C]**. Exécutez ensuite la commande suivante :

```terminal
cat /tmp/list.keys | grep "HGET" | awk '{print $5}' | sort | uniq -c | sort -nr | head -n 50
```

Ce journal répertorie les clés que vous pouvez précharger. Pour afficher le contenu d’une clé, exécutez la commande suivante :

```terminal
redis-cli -p 6370 -n 1 hgetall "<key_name>"
```

>[!ENDTABS]

## Activer le cache obsolète

Le cache obsolète est une fonctionnalité de cache L2 de `RemoteSynchronizedCache`. Lorsqu’il est activé, Adobe Commerce peut servir une valeur de cache local existante à partir de `/dev/shm` alors qu’une autre requête régénère déjà la même entrée, au lieu de faire attendre chaque requête simultanée. Cela réduit les bousculades du cache et les conflits de verrouillage lors de la régénération des entrées de cache coûteuses.

### Fonctionnement

Avec `RemoteSynchronizedCache`, Magento conserve deux copies de chaque entrée du cache : une copie locale dans `/dev/shm` et une copie distante dans Redis ou Valkey. Lorsque la copie distante n’est pas disponible et qu’un verrou de régénération existe déjà pour cette clé, les requêtes simultanées peuvent recevoir la valeur locale précédente au lieu d’attendre que la nouvelle valeur soit écrite.

Pour activer le cache obsolète, configurez-le dans le fichier `.magento.env.yaml`.

>[!BEGINTABS]


>[!TAB Configurer le cache obsolète pour Valkey]

Pour Valkey :

```yaml
stage:
  deploy:
    VALKEY_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default:
          backend_options:
            use_stale_cache: true
```

>[!TAB Configurer le cache obsolète pour Redis]

Pour Redis :

```yaml
stage:
  deploy:
    REDIS_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default:
          backend_options:
            use_stale_cache: true
```

>[!ENDTABS]

>[!NOTE]
>
>Le type de cache `full_page` n’est pas pertinent pour Adobe Commerce dans les projets d’infrastructure cloud, car ils utilisent [Fastly](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/fastly).

>[!WARNING]
>
>La configuration ci-dessus active le cache obsolète sur le front-end du cache `default`, ce qui applique le comportement du cache obsolète à toutes les entrées du cache qui utilisent ce front-end. Les types de cache principaux de Magento fonctionnent généralement comme prévu avec ce paramètre. Cependant, si votre projet inclut du code personnalisé ou des extensions qui écrivent dans le cache via l’API `\Magento\Framework\App\Cache` générique (par exemple `$this->cache->save()`) sans interface utilisateur frontale de cache dédiée, ces entrées peuvent également servir des valeurs obsolètes pendant la régénération.
>
>
>Si cela entraîne un comportement inattendu dans vos personnalisations, laissez le cache obsolète désactivé sur le front-end `default` et activez-le uniquement pour les types de cache sélectionnés, comme cela est généralement [fait sur site](../../../configuration/cache/level-two-cache.md#stale-cache-options).

### Activation du cache obsolète par type de cache individuellement

Vous pouvez activer le cache obsolète uniquement pour les types de cache sélectionnés en définissant une interface de cache dédiée dans `.magento.env.yaml` et en y mappant les types de cache sélectionnés.

Pour fonctionner correctement, le front-end personnalisé doit être défini comme un front-end complet sous `CACHE_CONFIGURATION.frontend`. La définition de `use_stale_cache: true` uniquement pour un nouveau nom front-end ne suffit pas.

**Exemples de configurations**

>[!BEGINTABS]

>[!TAB Configurer le cache obsolète pour Valkey]

Pour Valkey :

```yaml
stage:
  deploy:
    VALKEY_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default: # In this frontend, we keep stale cache set to false.
          id_prefix: '001_'
          backend_options:
            use_stale_cache: false

        # Now, create a new frontend called 'stale_cache_enabled'.
        # It must contain the same backend connection settings as the frontend 'default':
 
        stale_cache_enabled:
          id_prefix: '001_'
          backend: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
          backend_options:
            remote_backend: '\Magento\Framework\Cache\Backend\Valkey'
            remote_backend_options:
              server: localhost
              port: 6370 # Use the same port used by the frontend 'default' in env.php
              database: 1
              load_from_slave:
                server: localhost
                port: 26370 # Use the same port used by the frontend 'default' in env.php
              retry_reads_on_master: 1
              read_timeout: 10
            local_backend: 'Cm_Cache_Backend_File'
            local_backend_options:
              cache_dir: /dev/shm/
            use_stale_cache: true # stale cache here is enabled

      # Now select which cache types you want to enable (stale_cache_enabled), or disable (default)

      type:
        default:
          frontend: default
        layout:
          frontend: stale_cache_enabled
        reflection:
          frontend: stale_cache_enabled
        config_integration:
          frontend: stale_cache_enabled
        config_integration_api:
          frontend: stale_cache_enabled
        translate:
          frontend: stale_cache_enabled
        # add other cache types as needed...
```

>[!TAB Configurer le cache obsolète pour Redis]

Pour Redis :

```yaml
stage:
  deploy:
    REDIS_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default: # In this frontend, we keep stale cache set to false.
          id_prefix: '001_'
          backend_options:
            use_stale_cache: false

        # Now, create a new frontend called 'stale_cache_enabled'.
        # It must contain the same backend connection settings as the frontend 'default':

        stale_cache_enabled:
          id_prefix: '001_'
          backend: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
          backend_options:
            remote_backend: '\Magento\Framework\Cache\Backend\Redis'
            remote_backend_options:
              server: localhost
              port: 6370 # Use the same port used by the frontend 'default' in env.php
              database: 1
              load_from_slave:
                server: localhost
                port: 26370 # Use the same port used by the frontend 'default' in env.php
              retry_reads_on_master: 1
              read_timeout: 10
            local_backend: 'Cm_Cache_Backend_File'
            local_backend_options:
              cache_dir: /dev/shm/
            use_stale_cache: true # stale cache here is enabled

      # Now select which cache types you want to enable (stale_cache_enabled), or disable (default)

      type:
        default:
          frontend: default
        layout:
          frontend: stale_cache_enabled
        reflection:
          frontend: stale_cache_enabled
        config_integration:
          frontend: stale_cache_enabled
        config_integration_api:
          frontend: stale_cache_enabled
        translate:
          frontend: stale_cache_enabled
        # add other cache types as needed...
```

>[!ENDTABS]

>[!NOTE]
>
>Si le front-end source est configuré avec des options principales supplémentaires telles que la compression, les reprises, les clés de préchargement ou d’autres valeurs de réglage, copiez ces options dans `stale_cache_enabled` afin que le nouveau front-end conserve le même comportement.


## Instances de cache et de session distinctes

La séparation du cache et des sessions permet de les gérer indépendamment. Il réduit les conflits entre le cache et le trafic de session, empêche la pression liée au cache d’affecter les sessions et permet à chaque instance Redis ou Valkey d’être dimensionnée et ajustée pour sa propre charge de travail.

Suivez les étapes ci-dessous pour configurer une instance dédiée pour les sessions :

>[!BEGINTABS]


>[!TAB  Valkey ]

1. Mettez à jour le fichier de configuration `.magento/services.yaml`.

   ```yaml
   mysql:
     type: mysql:10.4
     disk: 35000
   
   valkey:
     type: valkey:8.0
   
   valkey-session: # This is for the new Valkey instance
     type: valkey:8.0
   
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
     valkey: "valkey:valkey"
     valkey-session: "valkey-session:valkey"   # Relationship of the new Valkey instance
     search: "search:elasticsearch"
     rabbitmq: "rabbitmq:rabbitmq"
   ```

1. Demandez une nouvelle instance Valkey dédiée aux sessions sur les environnements de production et d’évaluation.

   Envoyez un [ticket d’assistance ](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket). Incluez les fichiers de configuration `.magento/services.yaml` et `.magento.app.yaml` mis à jour.

   Cette mise à jour n’entraîne pas d’interruption, mais un déploiement est nécessaire pour activer le nouveau service.

1. Vérifiez que la nouvelle instance est en cours d’exécution et notez le numéro de port.

   ```shell
   echo $MAGENTO_CLOUD_RELATIONSHIPS | base64 -d | json_pp
   ```

1. Ajoutez le numéro de port au fichier de configuration `.magento.env.yaml`.

   >[!IMPORTANT]
   >
   >Configurez le port de session Valkey uniquement si `ece-tools` ne parvient pas à le détecter automatiquement à partir de la définition de service de session `MAGENTO_CLOUD_RELATIONSHIPS` Valkey.

   >[!NOTE]
   >
   >Définissez `disable_locking` sur `1` pour de meilleures performances. Dans de rares cas où des conditions de concurrence se produisent en raison d’une activité de session simultanée élevée, définissez-la sur `0` pour activer le verrouillage.

   ```yaml
   SESSION_CONFIGURATION:
     _merge: true
     redis: # keep 'redis' even if you are using Valkey.
       timeout: 5
       disable_locking: 1
       bot_first_lifetime: 60
       bot_lifetime: 7200
       max_lifetime: 2592000
       min_lifetime: 60
   ```

1. Supprimez les sessions de la [base de données par défaut](../../../configuration/cache/redis-pg-cache.md) (`db 0`) sur l’instance de cache Valkey.

   ```terminal
   valkey-cli -h 127.0.0.1 -p 6370 -n 0 FLUSHDB
   ```

>[!TAB Redis ]

1. Mettez à jour le fichier de configuration `.magento/services.yaml`.

   ```yaml
   mysql:
     type: mysql:10.4
     disk: 35000
   
   redis:
     type: redis:6.0
   
   redis-session: # This is for the new Redis instance
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

1. Demandez une nouvelle instance Redis dédiée aux sessions sur les environnements de production et d’évaluation.

   Envoyez un [ticket d’assistance ](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket). Incluez les fichiers de configuration `.magento/services.yaml` et `.magento.app.yaml` mis à jour.

   Cette mise à jour n’entraîne pas d’interruption, mais un déploiement est nécessaire pour activer le nouveau service.

1. Vérifiez que la nouvelle instance est en cours d’exécution et notez le numéro de port.

   ```shell
   echo $MAGENTO_CLOUD_RELATIONSHIPS | base64 -d | json_pp
   ```

1. Ajoutez le numéro de port au fichier de configuration `.magento.env.yaml`.

   >[!IMPORTANT]
   >
   >Configurez le port de session Redis uniquement si `ece-tools` ne parvient pas à le détecter automatiquement à partir de la définition du service de session Redis `MAGENTO_CLOUD_RELATIONSHIPS`.

   >[!NOTE]
   >
   >Définissez `disable_locking` sur `1` pour de meilleures performances. Dans de rares cas où des conditions de concurrence se produisent en raison d’une activité de session simultanée élevée, définissez-la sur `0` pour activer le verrouillage.

   ```yaml
   SESSION_CONFIGURATION:
     _merge: true
     redis:
       timeout: 5
       disable_locking: 1
       bot_first_lifetime: 60
       bot_lifetime: 7200
       max_lifetime: 2592000
       min_lifetime: 60
   ```

1. Supprimez les sessions de la [base de données par défaut](../../../configuration/cache/redis-pg-cache.md) (`db 0`) sur l’instance de cache Redis.

   ```terminal
   redis-cli -h 127.0.0.1 -p 6370 -n 0 FLUSHDB
   ```

>[!ENDTABS]

## Compression du cache

Si vous utilisez plus de 6 Go de `maxmemory` Redis ou Valkey, vous pouvez activer la compression du cache pour réduire l’espace consommé par les clés. Gardez à l’esprit que ce paramètre échange les performances côté client contre des économies de mémoire. Si vous disposez d’une capacité CPU disponible, envisagez de l’activer. Voir [Utilisation de Redis pour le stockage de session](../../../configuration/cache/redis-session.md) ou [Utilisation de Valkey pour le stockage de session](../../../configuration/cache/valkey-session.md) dans le _Guide de configuration_.

```yaml
stage:
  deploy:
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default:
          backend_options:
            compress_data: 4              # 0-9
            compress_tags: 4              # 0-9
            compress_threshold: 20480     # don't compress files smaller than this value
            compression_lib: 'gzip'       # snappy and lzf for performance, gzip for high compression (~69%)
```

## Activer la libération asynchrone

Pour activer le `lazyfree` sur Adobe Commerce sur les infrastructures cloud, envoyez un [ticket d’assistance Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket) en demandant que la configuration Redis ou Valkey suivante soit appliquée à vos environnements :

```text
lazyfree-lazy-eviction yes
lazyfree-lazy-expire yes
lazyfree-lazy-server-del yes
replica-lazy-flush yes
lazyfree-lazy-user-del yes
```

Lorsque `lazyfree` est activé, Redis ou Valkey décharge la récupération de la mémoire sur les threads d’arrière-plan pour les évictions, les expirations, les suppressions initiées par le serveur, les suppressions d’utilisateurs et les vidages de jeux de données de réplication. Cela réduit le blocage du thread principal et peut réduire la latence des requêtes.

>[!NOTE]
>
>L’option `lazyfree-lazy-user-del yes` fait en sorte que la commande `DEL` se comporte comme `UNLINK`, ce qui annule immédiatement le lien entre les clés et libère leur mémoire de manière asynchrone.

>[!WARNING]
>
>Comme la libération se produit en arrière-plan, la mémoire utilisée par les clés supprimées, expirées ou évincées reste allouée jusqu’à ce que les threads d’arrière-plan terminent le travail. Si votre instance Redis ou Valkey est déjà soumise à une pression de mémoire faible, testez-la avec précaution et envisagez d’abord de réduire la pression de mémoire. Par exemple, désactivez le cache de bloc pour des cas spécifiques et séparez les instances de cache et de Redis de session comme décrit ci-dessus.

## Activer les E/S multithreads

Pour activer le threading d’E/S Redis sur Adobe Commerce sur l’infrastructure cloud, envoyez un [ticket d’assistance Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket) en demandant la configuration de threading d’E/S ci-dessous. Cette configuration peut améliorer le débit en déchargeant les lectures et écritures de socket ainsi que l’analyse des commandes du thread principal, au détriment d’une utilisation plus élevée de CPU. Validez sous charge et surveillez vos hôtes.

>[!BEGINTABS]

>[!TAB Configuration des threads d’E/S pour Redis]

Pour Redis :

```text
io-threads-do-reads yes
io-threads 8 # Choose a value lower than the number of CPU cores (check with nproc), and then tune under load.
```

>[!TAB Configuration des threads d’E/S pour Valkey]

Pour Valkey :

```text
io-threads-do-reads yes
io-threads 8 # choose a value lower than the number of CPU cores (check with nproc), then tune under load
events-per-io-thread 2
```

>[!ENDTABS]


>[!NOTE]
>
>Les threads d’E/S parallélisent les E/S client et l’analyse uniquement. L’exécution de la commande Redis reste à thread unique.

>[!WARNING]
>
>L’activation des threads d’E/S peut augmenter l’utilisation de CPU et ne bénéficie pas à chaque charge de travail. Commencez par une valeur et une référence prudentes. Si la latence augmente ou que le CPU sature, réduisez le `io-threads` ou désactivez les lectures dans les threads d’E/S.


## Augmentation des délais d’expiration et des reprises du client

Augmentez la tolérance du client de cache Redis ou Valkey à de courtes périodes de saturation en ajustant les options du serveur principal dans `.magento.env.yaml`.

```yaml
stage:
  deploy:
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default:
          backend_options:
            connect_retries: 3 # Number of connection retries
            remote_backend_options:
              read_timeout: 10 # Timeout
```

Ces paramètres peuvent réduire les erreurs de connexion intermittentes et de délai d’expiration de lecture pendant les pics courts en réessayant la configuration de la connexion et en laissant plus de temps pour les réponses de Redis ou Valkey.

>[!NOTE]
>
>Ces paramètres peuvent aider à réduire la congestion pendant une courte période, mais ils ne corrigent pas la surcharge persistante.

## Exemples de configurations

Utilisez les exemples suivants comme point de départ pour vos configurations de service Redis ou Valkey.


### Appliquer toutes les recommandations de bonnes pratiques

>[!BEGINTABS]

>[!TAB Exemple de configuration Valkey]

```yaml
stage:
  deploy:
    MYSQL_USE_SLAVE_CONNECTION: true
    VALKEY_USE_SLAVE_CONNECTION: true # Enables read-only replica connection logic in Magento. It also works in a split architecture.
    VALKEY_BACKEND: \Magento\Framework\Cache\Backend\RemoteSynchronizedCache
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default:
          id_prefix: '001_' # any prefix is fine, but keep it consistent.
          backend_options:
            use_stale_cache: true             # Enables stale cache feature for all cache types
            connect_retries: 3                # Number of connection retries
            preload_keys:                     # Preload keys at backend_options level (official Adobe placement)
              - '001_EAV_ENTITY_TYPES:hash'   # Bootstrap: entity types
              - '001_GLOBAL_PLUGIN_LIST:hash' # Bootstrap: DI plugin list
              - '001_DB_IS_UP_TO_DATE:hash'   # Bootstrap: schema version
              - '001_SYSTEM_DEFAULT:hash'     # Config: system defaults
              - '001_EXTENSION_ATTRIBUTES_CONFIG:hash'
            remote_backend_options:
              read_timeout: 10
              retry_reads_on_master: 1        # Required for split architecture
            # Keep compression disabled for maximum performance. Only enable it if the cache usage is approaching the limit defined in maxmemory:
            # compress_data: 4              # 0-9
            # compress_tags: 4              # 0-9
            # compress_threshold: 20480     # don't compress files smaller than this value
            # compression_lib: 'gzip'       # snappy and lzf for performance, gzip for high compression (~69%)

    SESSION_CONFIGURATION:
      _merge: true
      redis:
        # port: 6372 # ece-tools should detect the port automatically, but if not, set here.
        timeout: 5
        disable_locking: 1 # true for max performance. If racing conditions happen when the server has an excessively high number of simultaneous session activities, set it to false.
        bot_first_lifetime: 60
        bot_lifetime: 7200
        max_lifetime: 2592000
        min_lifetime: 60
```

>[!TAB Redis ]

```yaml
stage:
  deploy:
    MYSQL_USE_SLAVE_CONNECTION: true
    REDIS_USE_SLAVE_CONNECTION: true # Enables read-only replica connection logic in Magento. It also works in a split architecture
    REDIS_BACKEND: \Magento\Framework\Cache\Backend\RemoteSynchronizedCache
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default:
          id_prefix: '001_' # Any prefix is fine, but keep it consistent.
          backend_options:
            use_stale_cache: true             # Enables stale cache feature for all cache types
            connect_retries: 3                # Number of connection retries
            preload_keys:                     # Preload keys at backend_options level (official Adobe placement)
              - '001_EAV_ENTITY_TYPES:hash'   # Bootstrap: entity types
              - '001_GLOBAL_PLUGIN_LIST:hash' # Bootstrap: DI plugin list
              - '001_DB_IS_UP_TO_DATE:hash'   # Bootstrap: schema version
              - '001_SYSTEM_DEFAULT:hash'     # Config: system defaults
              - '001_EXTENSION_ATTRIBUTES_CONFIG:hash'
            remote_backend_options:
              read_timeout: 10
              retry_reads_on_master: 1        # Required for split architecture
            # Keep compression disabled for maximum performance. Only enable it if the cache usage is approaching the limit defined in maxmemory:
            # compress_data: 4              # 0-9
            # compress_tags: 4              # 0-9
            # compress_threshold: 20480     # don't compress files smaller than this value
            # compression_lib: 'gzip'       # snappy and lzf for performance, gzip for high compression (~69%)

    SESSION_CONFIGURATION:
      _merge: true
      redis:

        # port: 6372 # ece-tools should detect the port automatically, but if not, set here.

        timeout: 5
        disable_locking: 1 # true for max performance. If racing conditions happen when the server has an excessively high number of simultaneous session activities, set it to false.
        bot_first_lifetime: 60
        bot_lifetime: 7200
        max_lifetime: 2592000
        min_lifetime: 60
```

>[!ENDTABS]

### Appliquer toutes les recommandations de bonnes pratiques et séparer le cache obsolète par type de cache

>[!BEGINTABS]

>[!TAB  Valkey ]

```yaml
stage:
  deploy:
    MYSQL_USE_SLAVE_CONNECTION: true
    VALKEY_USE_SLAVE_CONNECTION: true # Enables read-only replica connection logic in Magento. It also works in a split architecture
    VALKEY_BACKEND: \Magento\Framework\Cache\Backend\RemoteSynchronizedCache
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default: # Keep stale cache disabled on the broad default frontend.
          id_prefix: '001_' # Keep this prefix consistent with the frontend configuration generated in env.php
          backend_options:
            use_stale_cache: false # stale cache false here
            connect_retries: 3
            preload_keys:
              - '001_EAV_ENTITY_TYPES:hash'
              - '001_GLOBAL_PLUGIN_LIST:hash'
              - '001_DB_IS_UP_TO_DATE:hash'
              - '001_SYSTEM_DEFAULT:hash'
              - '001_EXTENSION_ATTRIBUTES_CONFIG:hash'
            remote_backend_options:
              read_timeout: 10
              retry_reads_on_master: 1
            # Keep compression disabled for maximum performance. Only enable it if the cache usage is approaching the limit defined in maxmemory:
            # compress_data: 4
            # compress_tags: 4
            # compress_threshold: 20480
            # compression_lib: 'gzip'

        stale_cache_enabled: # New frontend with stale cache enabled only for selected cache types.
          id_prefix: '001_' # Use the same id_prefix used by the source frontend in env.php
          backend: \Magento\Framework\Cache\Backend\RemoteSynchronizedCache
          backend_options:
            remote_backend: \Magento\Framework\Cache\Backend\Valkey
            remote_backend_options:
              server: localhost
              port: 6370   # Use the same port used by the source frontend in env.php
              database: 1
              load_from_slave:
                server: localhost
                port: 26370 # Use the same read-only replica connection/read port used by the source frontend in env.php
              retry_reads_on_master: 1
              read_timeout: 10
            local_backend: Cm_Cache_Backend_File
            local_backend_options:
              cache_dir: /dev/shm/
            use_stale_cache: true
            connect_retries: 3
            preload_keys:
              - '001_EAV_ENTITY_TYPES:hash'
              - '001_GLOBAL_PLUGIN_LIST:hash'
              - '001_DB_IS_UP_TO_DATE:hash'
              - '001_SYSTEM_DEFAULT:hash'
              - '001_EXTENSION_ATTRIBUTES_CONFIG:hash'
            # Keep compression disabled for maximum performance. Only enable it if the cache usage is approaching the limit defined in maxmemory:
            # compress_data: 4
            # compress_tags: 4
            # compress_threshold: 20480
            # compression_lib: 'gzip'

      type:
        default:
          frontend: default # Keeps stale cache disabled on the broad default frontend, including generic cache writes that use \Magento\Framework\App\Cache, such as $this->cache->save().
        block_html:
          frontend: stale_cache_enabled # This is often one of the cache types that benefits the most from stale cache, because it is heavily used and can contribute significantly to lock contention during regeneration. In most cases, it can remain enabled. Exclude it only if the project has customization-specific issues caused by stale block output.
        layout:
          frontend: stale_cache_enabled
        reflection:
          frontend: stale_cache_enabled
        config_integration:
          frontend: stale_cache_enabled
        config_integration_api:
          frontend: stale_cache_enabled
        translate:
          frontend: stale_cache_enabled
        # add other cache types as needed...

    SESSION_CONFIGURATION:
      _merge: true
      redis: # keep 'redis' even if you are using Valkey.
        # port: 6372 # ece-tools should detect the port automatically, but if not, set here.
        timeout: 5
        disable_locking: 1 # true for max performance. If racing conditions happen when the server has an excessively high number of simultaneous session activities, set it to false.
        bot_first_lifetime: 60
        bot_lifetime: 7200
        max_lifetime: 2592000
        min_lifetime: 60
```

>[!TAB Redis ]

```yaml
stage:
  deploy:
    MYSQL_USE_SLAVE_CONNECTION: true
    REDIS_USE_SLAVE_CONNECTION: true # Enables the slave connection logic in Magento. It also works in a split architecture
    REDIS_BACKEND: \Magento\Framework\Cache\Backend\RemoteSynchronizedCache
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default: # Keep stale cache disabled on the broad default frontend.
          id_prefix: '001_' # Keep this prefix consistent with the frontend configuration generated in env.php
          backend_options:
            use_stale_cache: false # stale cache false here
            connect_retries: 3
            preload_keys:
              - '001_EAV_ENTITY_TYPES:hash'
              - '001_GLOBAL_PLUGIN_LIST:hash'
              - '001_DB_IS_UP_TO_DATE:hash'
              - '001_SYSTEM_DEFAULT:hash'
              - '001_EXTENSION_ATTRIBUTES_CONFIG:hash'
            remote_backend_options:
              read_timeout: 10
              retry_reads_on_master: 1
            # Keep compression disabled for maximum performance. Only enable it if the cache usage is approaching the limit defined in maxmemory:
            # compress_data: 4
            # compress_tags: 4
            # compress_threshold: 20480
            # compression_lib: 'gzip'

        stale_cache_enabled: # New frontend with stale cache enabled only for selected cache types.
          id_prefix: '001_' # Use the same id_prefix used by the source frontend in env.php
          backend: \Magento\Framework\Cache\Backend\RemoteSynchronizedCache
          backend_options:
            remote_backend: \Magento\Framework\Cache\Backend\Redis
            remote_backend_options:
              server: localhost
              port: 6370   # Use the same port used by the source frontend in env.php
              database: 1
              load_from_slave:
                server: localhost
                port: 26370 # Use the same read-only replica connection/read port used by the source frontend in env.php
              retry_reads_on_master: 1
              read_timeout: 10
            local_backend: Cm_Cache_Backend_File
            local_backend_options:
              cache_dir: /dev/shm/
            use_stale_cache: true
            connect_retries: 3
            preload_keys:
              - '001_EAV_ENTITY_TYPES:hash'
              - '001_GLOBAL_PLUGIN_LIST:hash'
              - '001_DB_IS_UP_TO_DATE:hash'
              - '001_SYSTEM_DEFAULT:hash'
              - '001_EXTENSION_ATTRIBUTES_CONFIG:hash'
            # Keep compression disabled for maximum performance. Only enable it if the cache usage is approaching the limit defined in maxmemory:
            # compress_data: 4
            # compress_tags: 4
            # compress_threshold: 20480
            # compression_lib: 'gzip'

      type:
        default:
          frontend: default # Keeps stale cache disabled on the broad default frontend, including generic cache writes that use \Magento\Framework\App\Cache, such as $this->cache->save().
        block_html:
          frontend: stale_cache_enabled # This is often one of the cache types that benefits the most from stale cache, because it is heavily used and can contribute significantly to lock contention during regeneration. In most cases, it can remain enabled. Exclude it only if the project has customization-specific issues caused by stale block output.
        layout:
          frontend: stale_cache_enabled
        reflection:
          frontend: stale_cache_enabled
        config_integration:
          frontend: stale_cache_enabled
        config_integration_api:
          frontend: stale_cache_enabled
        translate:
          frontend: stale_cache_enabled
        # add other cache types as needed...

    SESSION_CONFIGURATION:
      _merge: true
      redis:
        # port: 6372 # ece-tools should detect the port automatically, but if not, set here.
        timeout: 5
        disable_locking: 1 # true for max performance. If racing conditions happen when the server has an excessively high number of simultaneous session activities, set it to false.
        bot_first_lifetime: 60
        bot_lifetime: 7200
        max_lifetime: 2592000
        min_lifetime: 60
```

>[!ENDTABS]

## Informations supplémentaires

Consultez les rubriques connexes suivantes :

- [Configuration du service Valkey](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/service/valkey)
- [Configuration du service Redis](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/service/redis)
- [Déployer les variables](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/env/stage/variables-deploy)

