---
title: Bonnes pratiques relatives à la configuration des services Valkey et Redis
description: Découvrez comment configurer la mise en cache Redis et Valkey pour Adobe Commerce on Cloud, y compris les connexions de réplication, le cache L2, le cache obsolète et le stockage de session.
solution: Commerce
role: Developer, Admin
level: Intermediate
feature: Best Practices, Cache
feature-set: Commerce
topic: Performance
exl-id: 8b3c9167-d2fa-4894-af45-6924eb983487
badgePaas: label="Commerce sur le cloud" type="Informative" url="https://experienceleague.adobe.com/fr/docs/commerce/user-guides/product-solutions" tooltip="S’applique uniquement à Adobe Commerce sur les projets cloud."
nudge: true
autotag-review: '2026-08-18T23:34:12.845Z'
TQID: 'https://experienceleague.adobe.com/kYuQylZb2r7ElWP1oRJbyIt9jsZMhoO9yFpBMDlf1tw'
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
  - id: cdf0c6dd-1717-4e20-9530-a24eee57088b
feature_v2:
  - id: b5f00040-57a0-4a6d-a39e-383b1936c2c9
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
  - id: e8818fe6-9c8b-4bc0-9ef8-377a10b7bc75
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
source-git-commit: 55f36b56b5d719ace064eccf42675cd8f9b7683b
workflow-type: tm+mt
source-wordcount: 3304
ht-degree: 0%

---


# Bonnes pratiques pour la configuration des services Valkey et Redis

Utilisez ces recommandations lors de la configuration de Redis ou Valkey pour le cache d’application Adobe Commerce, le stockage de session et le cache L2 pour Adobe Commerce sur les déploiements cloud.

Pour la configuration du cache local d’Adobe Commerce, voir Configuration du cache L2 [&#x200B; pour l’optimisation des performances](/help/configuration/cache/level-two-cache.md).

>[!NOTE]
>
>Cette rubrique couvre le cache de l’application Commerce et les serveurs principaux de session. La mise en cache HTTP de toutes les pages, telle que Fastly ou Varnish, est une couche de mise en cache distincte, configurée indépendamment. Les modifications apportées au serveur principal du cache d’applications ne remplacent pas ou ne configurent pas le cache HTTP de pages complètes.

Ces recommandations portent sur les points suivants :

- Sélectionner un service de cache pris en charge
- Activer la connexion de réplica
- Instances de cache et de session distinctes
- Configuration de la compression du cache
- Activer la libération asynchrone
- Activer les E/S multithreads
- Augmentation des délais d’expiration et des reprises du client
- Configurez le cache L2, y compris les clés de préchargement, le cache obsolète et le cache L2 [!DNL Symfony]
- Consulter les exemples de configuration

## Sélectionner un service de cache pris en charge

| Version d’Adobe Commerce | Service de cache recommandé | Implémentation du cache L2 |
| ---------------------- | -------------------------- | ------------------------ |
| 2.4.8 et versions antérieures, lorsqu’elles sont prises en charge par la version exacte | Redis ou Valkey | RemoteSynchronizedCache |
| 2.4.9 et versions ultérieures | Valkey | symfony_l2 |

Redis n’est pas pris en charge pour la configuration du cache dans Adobe Commerce 2.4.9 et dans les versions de correctif où la configuration système spécifie Valkey à la place. Vérifiez toujours la version exacte de Commerce, le niveau de correctif et la version de service dans les [Options du serveur principal du cache et référence de stockage](/help/configuration/cache/cache-options.md) et [Configuration requise](/help/installation/system-requirements.md).

>[!NOTE]
>
>Vérifiez que vous utilisez la dernière version du package `ece-tools`. Sinon, [effectuez une mise à niveau vers la dernière version](https://experienceleague.adobe.com/fr/docs/commerce-on-cloud/user-guide/dev-tools/ece-tools/update-package). Vous pouvez vérifier la version installée dans votre environnement local à l’aide de la commande de l’interface de ligne de commande `composer show magento/ece-tools`.

## Activer la connexion de réplica

Activez la connexion de réplica dans le fichier `.magento.env.yaml`. Cette modification permet à Adobe Commerce d’utiliser une connexion de cache supplémentaire pour les lectures tout en continuant à utiliser le point d’entrée principal pour les écritures. Cette configuration peut réduire la charge de lecture sur le service de cache principal et distribuer le trafic de lecture plus efficacement.

>[!NOTE]
>
>La disponibilité d’une connexion de réplication dépend de la topologie de votre projet (par exemple, une architecture à un seul nœud ou fractionnée ou haute disponibilité) et de la version `ece-tools`. Avant de vous fier à ce paramètre, vérifiez qu’il existe une relation de réplication pour votre service en exécutant `echo $MAGENTO_CLOUD_RELATIONSHIPS | base64 -d | json_pp` et en vérifiant une entrée `USE_SLAVE_CONNECTION`. Pour vérifier si votre topologie fournit un point d’entrée de réplica, mettez à niveau `ece-tools` et redéployez ou contactez l’assistance Adobe Commerce si aucune entrée de `USE_SLAVE_CONNECTION` n’est présente.
>
>Par `symfony_l2`, la prise en charge des connexions de réplica est assurée par le biais d’une mise à jour des correctifs `ece-tools` et Cloud. Aucune configuration de cache supplémentaire n’est requise au-delà de la modification de `VALKEY_USE_SLAVE_CONNECTION: true`. Effectuez une mise à jour vers la dernière version de `ece-tools` pour recevoir le correctif.

>[!BEGINTABS]

>[!TAB Configuration Valkey]

Pour Valkey, utilisez :

```yaml
stage:
  deploy:
    VALKEY_USE_SLAVE_CONNECTION: true
```

Pour plus d’informations sur la configuration des variables d’environnement, consultez [VALKEY _USE_ SLAVE_CONNECTION](https://experienceleague.adobe.com/fr/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy#valkey_use_slave_connection) dans le guide _Commerce sur les infrastructures cloud_.

>[!TAB Configuration Redis]

Pour Redis, utilisez :

```yaml
stage:
  deploy:
    REDIS_USE_SLAVE_CONNECTION: true
```

Pour plus d’informations sur la configuration des variables d’environnement, consultez [REDIS _USE_ SLAVE_CONNECTION](https://experienceleague.adobe.com/fr/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy#redis_use_slave_connection) dans le guide _Commerce sur les infrastructures cloud_.

>[!ENDTABS]

## Instances de cache et de session distinctes

Le cache et la configuration de session sont indépendants. `SESSION_CONFIGURATION` n’affecte pas le comportement du cache, quelle que soit l’implémentation du cache principal ou L2 que vous utilisez. La séparation du cache et des sessions permet de les gérer indépendamment. Il réduit les conflits entre le cache et le trafic de session, empêche la pression liée au cache d’affecter les sessions et permet à chaque instance Redis ou Valkey d’être dimensionnée et ajustée pour sa propre charge de travail.

>[!IMPORTANT]
>
>L’approvisionnement d’une instance de session dédiée sur Production et Évaluation n’est pas en libre-service. Vous devez envoyer un [ticket d’assistance &#x200B;](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#submit-ticket) avec vos fichiers `.magento/services.yaml` et `.magento.app.yaml` mis à jour, comme décrit à l’étape 3 ci-dessous.

Pour configurer une instance dédiée pour les sessions , procédez comme suit :

>[!BEGINTABS]

>[!TAB  Valkey ]

1. Mettez à jour le fichier de configuration `.magento/services.yaml`, en remplaçant `<version>` par les versions de service que vous utilisez. Consultez [Configuration requise](/help/installation/system-requirements.md) pour connaître les versions de service prises en charge par version.

   ```yaml
   mysql:
     type: mysql:<version>
     disk: 35000
   
   valkey:
     type: valkey:<version>
   
   valkey-session: # This is for the new Valkey instance
     type: valkey:<version>
   
   search:
     type: elasticsearch:<version>
     disk: 5000
   
   rabbitmq:
     type: rabbitmq:<version>
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

   Envoyez un [ticket d’assistance &#x200B;](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#submit-ticket). Incluez les fichiers de configuration `.magento/services.yaml` et `.magento.app.yaml` mis à jour.

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

1. Supprimez les sessions de la [base de données par défaut](/help/configuration/cache/redis-pg-cache.md) (`db 0`) sur l’instance de cache Valkey.

   ```terminal
   valkey-cli -h 127.0.0.1 -p 6370 -n 0 FLUSHDB
   ```

>[!TAB Redis ]

1. Mettez à jour le fichier de configuration `.magento/services.yaml`, en remplaçant `<version>` par les versions de service que vous utilisez.

   ```yaml
   mysql:
     type: mysql:<version>
     disk: 35000
   
   redis:
     type: redis:<version>
   
   redis-session: # This is for the new Redis instance
     type: redis:<version>
   
   search:
     type: elasticsearch:<version>
     disk: 5000
   
   rabbitmq:
     type: rabbitmq:<version>
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

   Envoyez un [ticket d’assistance &#x200B;](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#submit-ticket). Incluez les fichiers de configuration `.magento/services.yaml` et `.magento.app.yaml` mis à jour.

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

1. Supprimez les sessions de la [base de données par défaut](/help/configuration/cache/redis-pg-cache.md) (`db 0`) sur l’instance de cache Redis.

   ```terminal
   redis-cli -h 127.0.0.1 -p 6370 -n 0 FLUSHDB
   ```

>[!ENDTABS]

## Compression du cache

Si vous utilisez plus de 6 Go de `maxmemory` Redis ou Valkey, vous pouvez activer la compression du cache pour réduire l’espace consommé par les clés. Notez que ce paramètre remplace les performances côté client par des économies de mémoire. Si vous disposez d’une capacité CPU disponible, envisagez de l’activer. Voir [Utilisation de Redis pour le stockage de session](/help/configuration/cache/redis-session.md) ou [Utilisation de Valkey pour le stockage de session](/help/configuration/cache/valkey-session.md) dans le _Guide de configuration_.

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

Pour activer le `lazyfree` sur l’infrastructure cloud d’Adobe Commerce, envoyez un [ticket d’assistance Adobe Commerce](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#submit-ticket) en demandant que la configuration Redis ou Valkey suivante soit appliquée à vos environnements :

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

Pour activer le threading d’E/S Redis sur l’infrastructure cloud d’Adobe Commerce, envoyez un [ticket d’assistance Adobe Commerce](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#submit-ticket) en demandant la configuration de threading d’E/S ci-dessous. Cette configuration peut améliorer le débit en déchargeant les lectures, écritures et analyses de commande de socket du thread principal, au détriment d’une utilisation plus élevée de CPU. Validez sous charge et surveillez vos hôtes.

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

## Configurer le cache L2

Configurez le cache L2 en définissant la variable de déploiement `VALKEY_BACKEND` ou `REDIS_BACKEND` dans le fichier de configuration `.magento.env.yaml`.

Il existe deux implémentations du cache L2 disponibles pour Adobe Commerce sur les infrastructures cloud.

- L’implémentation héritée utilise `RemoteSynchronizedCache` avec `Cm_Cache_Backend_File` pour le stockage local
- L’implémentation moderne utilise la norme `symfony_l2` avec la conformité PSR-6 et des performances améliorées. L’implémentation moderne ne prend en charge que Valkey.

| Version de Commerce | RemoteSynchronizedCache avec Valkey | Configuration recommandée |
| -------------- | ----------------------------------- | ------------------------- |
| 2.4.8 et versions antérieures <br>(si Valkey est pris en charge) | Chemin L2 hérité pris en charge | `VALKEY_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'` |
| 2.4.9 et versions ultérieures | Non pris en charge | `VALKEY_BACKEND: 'symfony_l2'` |

>[!IMPORTANT]
>
>Le cache Redis n’est pas pris en charge pour Adobe Commerce 2.4.9 ou pour les versions de correctif ultérieures à 2.4.5-p16, 2.4.6-p14, 2.4.7-p9 et 2.4.8-p4. Utilisez Valkey pour la configuration du cache lorsque Redis n’est pas pris en charge. Consultez [Configuration requise](/help/installation/system-requirements.md) pour connaître les services de cache pris en charge par version.

>[!BEGINTABS]

>[!TAB Configuration Valkey]

Sur Commerce 2.4.8 et les versions antérieures qui prennent en charge Valkey, utilisez la configuration suivante :

```yaml
stage:
  deploy:
    VALKEY_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
```

Sur Commerce 2.4.9 et les versions ultérieures, utilisez la configuration suivante avec l’implémentation L2 [!DNL Symfony] :

```yaml
stage:
  deploy:
    VALKEY_BACKEND: 'symfony_l2'
```

>[!TAB Configuration Redis]

Sur la version 2.4.8 et les versions antérieures de Commerce qui prennent en charge Redis, utilisez :

```yaml
stage:
  deploy:
    REDIS_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
```

Pour plus d’informations sur la configuration de l’environnement, consultez la [`REDIS_BACKEND`](https://experienceleague.adobe.com/fr/docs/commerce-on-cloud/user-guide/configure/env/stage/variables-deploy#redis_backend) dans le guide _Commerce sur les infrastructures cloud_.

>[!ENDTABS]

### Migration vers Valkey avec [!DNL Symfony] cache L2

Si vous migrez un projet Adobe Commerce on Cloud existant de `RemoteSynchronizedCache` (Redis ou Valkey) vers `symfony_l2`, consultez les informations suivantes avant de mettre à jour `.magento.env.yaml`.

- **La modification de la variable de déploiement suffit pour activer `symfony_l2`.** La définition de `VALKEY_BACKEND: symfony_l2` seule crée automatiquement la configuration complète du cache L2. Vous n’avez pas besoin de recréer manuellement la structure de `backend_options` utilisée dans votre configuration de `RemoteSynchronizedCache` précédente. Voir [Configurer [!DNL Symfony] cache L2](#configure-symfony-l2-cache).

- **Supprimez le `preload_keys` de votre configuration existante.** Si votre configuration de `RemoteSynchronizedCache` comprend des `preload_keys` sous `CACHE_CONFIGURATION`, supprimez-les dans le cadre de la migration. Voir [Précharger les clés](#preload-keys) pour plus d’informations.

- **Le comportement du cache obsolète change automatiquement.** Sous `symfony_l2`, `ece-tools` active automatiquement le cache obsolète pour les types de cache courants (tels que `layout`, `block_html`, `full_page` et `translate`) sans nécessiter la configuration manuelle frontale qui `RemoteSynchronizedCache` nécessaire. Si vous avez précédemment configuré manuellement le cache obsolète et souhaitez conserver votre comportement précédent exact, consultez la section [Activer le cache obsolète](#enable-stale-cache) avant de migrer.

- **La compression nécessite un indicateur explicite.** Si vous personnalisez `symfony_l2` compression par `CACHE_CONFIGURATION`, la définition de `compression_lib` seule n’active pas la compression ; `compress_data` doit également être définie. Voir [&#x200B; Compression du cache &#x200B;](#cache-compression).

- **Redis n’est pas un serveur principal distant pris en charge pour `symfony_l2`.** Migrer vers Valkey dans le cadre de cette modification. Voir [&#x200B; Configuration du service Valkey &#x200B;](https://experienceleague.adobe.com/fr/docs/commerce-on-cloud/user-guide/configure/service/valkey).

- **La configuration de session n’est pas affectée par cette migration.** `SESSION_CONFIGURATION` est indépendant du serveur principal du cache et n’a pas besoin d’être modifié lors du déplacement vers `symfony_l2`. Voir [Séparer les instances de cache et de session](#separate-cache-and-session-instances).

>[!IMPORTANT]
>
>Ne configurez pas `symfony_l2` manuellement dans `app/etc/env.php`. Configurez-le via `.magento.env.yaml` afin `ece-tools` applique et conserve le paramètre pendant le déploiement. Voir [Configurer [!DNL Symfony] cache L2](#configure-symfony-l2-cache).

### Précharger les clés

Les clés de préchargement peuvent être appliquées à une configuration `symfony_l2` si vous utilisez l’emplacement correct (sous `backend_options` ou `remote_backend_options`). Cependant, Adobe déconseille d&#39;utiliser les clés de préchargement avec `symfony_l2`. L’implémentation de préchargement `symfony_l2` récupère les clés une par une, de sorte qu’elle ne réduit pas les allers-retours comme elle le fait pour les `RemoteSynchronizedCache` et qu’elle peut augmenter la charge sur Valkey sans bénéfice de performances.

La fonction de préchargement vous permet de fournir une liste des clés fréquemment utilisées que Magento récupère dans un seul pipeline lors du premier accès lors d’une requête. Magento conserve ensuite les valeurs récupérées dans la mémoire PHP pour le reste de cette requête, ce qui réduit les allers-retours répétés vers Redis ou Valkey et peut améliorer les performances d&#39;amorçage de requête pour ces clés.

Vous pouvez identifier les clés fréquemment utilisées en surveillant les commandes actives sur Redis ou Valkey :

Les clés de préchargement sont configurées dans le fichier de configuration `.magento.env.yaml`. Cet exemple illustre la configuration d’Adobe Commerce 2.4.8 et des versions antérieures qui prennent en charge `RemoteSynchronizedCache`.

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

Au bout de 10 secondes, appuyez sur **Ctrl+C**. Exécutez ensuite la commande suivante :

```terminal
cat /tmp/list.keys | grep "HGET" | awk '{print $5}' | sort | uniq -c | sort -nr | head -n 50
```

Ce journal répertorie les clés que vous pouvez précharger. Pour afficher le contenu d’une clé, exécutez la commande suivante :

```terminal
redis-cli -p 6370 -n 1 hgetall "<key_name>"
```

### Activer le cache obsolète

Le cache obsolète est une fonctionnalité de cache L2 qui permet à Adobe Commerce de servir une valeur de cache local existante à partir de `/dev/shm` pendant qu’une autre requête régénère déjà la même entrée. Cela empêche les requêtes simultanées d’attendre. Cela réduit les bousculades du cache et les conflits de verrouillage lors de la régénération des entrées de cache coûteuses.

Pour Adobe Commerce version 2.4.9 et ultérieure, définissez `VALKEY_BACKEND: symfony_l2` dans le fichier `.magento.env.yaml` :

```yaml
stage:
  deploy:
    VALKEY_BACKEND: symfony_l2
```

`ece-tools` génère automatiquement un front-end `default` et un front-end `stale_cache_enabled`, et mappe les types de cache suivants au front-end obsolète : `layout`, `block_html`, `reflection`, `config_integration`, `config_integration_api`, `full_page` et `translate`. Aucune configuration manuelle `use_stale_cache` ou frontale n’est requise pour ces types. Ce mappage automatique est lui-même un exemple d’activation sélective du cache obsolète. Seuls des types de cache spécifiques utilisent le serveur frontal obsolète, mais pas tous. Pour personnaliser les types à `stale_cache_enabled` ou ajouter des types en plus des valeurs par défaut, consultez [Personnaliser la configuration du cache L [!DNL Symfony] 2](#customize-the-symfony-l2-cache-configuration).

>[!NOTE]
>
>Le type de cache `full_page` n’est pas pertinent pour les projets d’infrastructure cloud d’Adobe Commerce, car ils utilisent Fastly pour la mise en cache de toutes les pages. Les exemples de configuration manuelle dans cette section ne `full_page` pas pour cette raison, même si `ece-tools` l’inclut dans le mappage de `symfony_l2` par défaut.

La configuration héritée suivante s’applique à Adobe Commerce 2.4.8 et versions antérieures, qui utilisent `RemoteSynchronizedCache` et nécessitent un cache obsolète manuel et une configuration frontale. La même recommandation sélective à l’échelle mondiale s’applique ici.

#### Fonctionnement de l’ancien serveur principal RemoteSynchronizedCache

Avec `RemoteSynchronizedCache`, Magento conserve deux copies de chaque entrée du cache : une copie locale dans `/dev/shm` et une copie distante dans Redis ou Valkey. Lorsque la copie distante n’est pas disponible et qu’un verrou de régénération existe déjà pour cette clé, les requêtes simultanées peuvent recevoir la valeur locale précédente au lieu d’attendre que la nouvelle valeur soit écrite.

Pour activer le cache obsolète pour la version 2.4.8 et les versions antérieures, configurez-le dans le fichier `.magento.env.yaml`.

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

>[!WARNING]
>
>La configuration ci-dessus active le cache obsolète sur le front-end du cache `default`, ce qui applique le comportement du cache obsolète à toutes les entrées du cache qui utilisent ce front-end. Les types de cache principaux de Magento fonctionnent comme prévu avec ce paramètre. Cependant, si votre projet inclut du code personnalisé ou des extensions qui écrivent dans le cache via l’API `\Magento\Framework\App\Cache` générique (par exemple `$this->cache->save()`) sans interface utilisateur frontale de cache dédiée, ces entrées peuvent également servir des valeurs obsolètes pendant la régénération.
>
>
>Si cela entraîne un comportement inattendu dans vos personnalisations, laissez le cache obsolète désactivé sur le front-end `default` et activez-le uniquement pour les types de cache sélectionnés, comme illustré ci-dessous.

#### Activer le cache obsolète par type de cache individuellement (hérité)

Vous pouvez activer le cache obsolète uniquement pour les types de cache sélectionnés en définissant une interface de cache dédiée dans `.magento.env.yaml` et en y mappant les types de cache sélectionnés. Cette approche manuelle s’applique au serveur principal de l’`RemoteSynchronizedCache` hérité ; `symfony_l2` effectue automatiquement ce mappage, comme décrit ci-dessus.

Pour fonctionner correctement, le front-end personnalisé doit être défini comme un front-end complet sous `CACHE_CONFIGURATION.frontend`. La définition de `use_stale_cache: true` uniquement pour un nouveau nom front-end ne suffit pas.

**Exemples de configurations**

Pour Redis version 2.4.8 ou antérieure, la configuration suivante active le cache périmé pour les types de cache `layout`, `reflection`, `config_integration`, `config_integration_api` et `translate`, tout en laissant les autres utilisateurs utilisant le front-end par défaut avec le cache périmé désactivé :

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

>[!NOTE]
>
>Si le serveur frontal source est configuré avec des options principales supplémentaires, copiez ces options dans `stale_cache_enabled` afin que le nouveau serveur frontal conserve le même comportement.

### Configurer [!DNL Symfony] cache L2

Adobe Commerce 2.4.9 et versions ultérieures prennent en charge le serveur principal de cache `symfony_l2`. Le serveur principal `symfony_l2` est l’implémentation du cache qu’Adobe Commerce utilise pour gérer le comportement du cache L1 et L2. **Il ne remplace pas Redis ou Valkey en tant que service de cache distant.**

>[!IMPORTANT]
>
>Configurez `symfony_l2` via la variable de déploiement `.magento.env.yaml` afin `ece-tools` applique et conserve le paramètre pendant le déploiement. Ne configurez pas les `symfony_l2` manuellement dans `app/etc/env.php`, car le déploiement peut remplacer les modifications de `env.php` manuelles. Si la `ece-tools` ne s’applique pas `symfony_l2`, Commerce peut revenir au cache basé sur les fichiers, ce qui peut augmenter les E/S de disque, ajouter une surcharge de réplication du système de fichiers sur les environnements à plusieurs nœuds et dégrader les performances.

Pour utiliser `symfony_l2` cache pour Adobe Commerce 2.4.9, procédez comme suit :

- Assurez-vous que le projet cloud utilise [`ece-tools` package v2002.2.12](https://experienceleague.adobe.com/fr/docs/commerce-on-cloud/user-guide/dev-tools/ece-tools/update-package) ou une version ultérieure.

- Définissez la variable de déploiement dans le fichier `.magento.env.yaml` : `VALKEY_BACKEND`=`symfony_l2`.

  ```yaml
  stage:
    deploy:
      VALKEY_BACKEND: symfony_l2
  ```

La définition de la variable de déploiement `VALKEY_BACKEND` sur `symfony_l2` crée automatiquement la configuration de cache L2 complète à partir des détails de connexion au service Valkey, y compris les fronts `default` et `stale_cache_enabled`, avec les types de cache communs déjà mappés. La définition de `CACHE_CONFIGURATION` est facultative et nécessaire uniquement si vous souhaitez personnaliser des options d’arrière-plan spécifiques.

>[!NOTE]
>
>Le correctif ACP2E-5132 pour Adobe Commerce 2.4.9 améliore [!DNL Symfony] performances et la fiabilité du cache L2 en optimisant le stockage des balises, en ajoutant un verrou de régénération du cache obsolète et en corrigeant les problèmes liés aux appartenances aux balises obsolètes, aux écritures distantes redondantes et à l’éviction L1 basée sur la taille (`cleanup_percentage`). Cela réduit les E/S de disque et la charge du serveur principal tout en améliorant la cohérence du cache. Voir [Performances et fiabilité améliorées du cache Symfony L2](/help/configuration/cache/level-two-cache.md#enhanced-symfony-l2-cache-performance-and-reliability) dans le _Guide de configuration d’Adobe Commerce_.
>
>Le correctif est inclus dans le package [Correctifs cloud pour Commerce](https://experienceleague.adobe.com/fr/docs/commerce-on-cloud/user-guide/release-notes/cloud-patches) (une dépendance de `ece-tools`) et est appliqué automatiquement lors du déploiement lorsque vous effectuez une mise à jour vers la dernière version de `ece-tools`. Effectuez une mise à jour vers la dernière version de `ece-tools` pour recevoir le correctif.

#### Personnalisation de la configuration du cache L2 [!DNL Symfony]

`ece-tools` dérive automatiquement les détails de connexion Valkey (`server`, `port`, `database`, `serializer`, `compression_lib`, `persistent_id`) pour les fronts `default` et `stale_cache_enabled`. Pour personnaliser d’autres options du serveur principal, telles que le répertoire de cache local, définissez `CACHE_CONFIGURATION` avec `_merge: true` et `VALKEY_BACKEND: symfony_l2`. Les valeurs que vous définissez ici remplacent les valeurs par défaut générées automatiquement correspondantes ; toutes les options que vous omettez continuent à utiliser les valeurs que `ece-tools` dérive automatiquement.

```yaml
stage:
  deploy:
    VALKEY_BACKEND: symfony_l2
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default:
          backend_options:
            remote_backend: valkey
            local_backend: file
            local_backend_options:
              cache_dir: /dev/shm/magento_l1
        stale_cache_enabled:
          backend: symfony_l2
          backend_options:
            remote_backend: valkey
            local_backend: file
            local_backend_options:
              cache_dir: /dev/shm/magento_l1_stale
            use_stale_cache: true
```

>[!CAUTION]
>
>Lors de la définition de `CACHE_CONFIGURATION` pour `symfony_l2`, remplacez uniquement `server` ou `port` si vous pointez intentionnellement vers un point d’entrée du cache autre que le service Valkey de votre projet. Le package `ece-tools` dérive automatiquement ces valeurs de votre relation de service Valkey.
>
>Si vous remplacez `server`, sa valeur doit être `localhost` lors de la connexion au service Valkey du projet. Si la valeur `server` ou `port` est incorrecte, le déploiement échoue avec une erreur de connexion au cache.

### Dimensionnement de la mémoire cache L2 pour Adobe Commerce Cloud

Le cache L2 utilise un [&#x200B; système de fichiers temporaire &#x200B;](https://en.wikipedia.org/wiki/Tmpfs) (`/dev/shm`) comme mécanisme de stockage. Contrairement aux magasins de valeur-clé spécialisés, tmpfs n’a pas de politique d’éviction des clés, de sorte que l’utilisation de la mémoire peut augmenter sans limite. Pour éviter l’épuisement, Adobe Commerce efface automatiquement le stockage L2 lorsque l’utilisation atteint un seuil configurable (95 % par défaut). Vous pouvez contrôler la consommation de mémoire en demandant un montage `/dev/shm` plus important ou en abaissant le seuil de nettoyage.

Ajustez l’utilisation maximale de la mémoire cache L2 en fonction des besoins de votre projet. Utilisez l’une des méthodes suivantes :

- Pour ajuster la taille du montage `/dev/shm`, créez un ticket de support. Pour ce scénario, Adobe recommande de définir la taille de montage `/dev/shm` sur 15 Go.
- Ajustez la propriété `cleanup_percentage` au niveau de l’application pour limiter l’utilisation du stockage et la mémoire disponible pour d’autres services.
Vous pouvez ajuster la configuration dans la configuration de déploiement sous le groupe de configuration du cache `cache/frontend/default/backend_options/cleanup_percentage`.

>[!NOTE]
>
>L’option configurable `cleanup_percentage` a été introduite dans Adobe Commerce 2.4.4.

Les exemples suivants montrent le code de configuration dans le fichier `.magento.env.yaml` :

>[!BEGINTABS]

>[!TAB Configuration Valkey]

Pour Commerce version 2.4.9 et ultérieure, utilisez la configuration suivante pour définir le seuil de nettoyage à 90 % :

```yaml
stage:
  deploy:
    VALKEY_BACKEND: symfony_l2
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default:
          backend_options:
            cleanup_percentage: 90
```

>[!TAB Configuration Redis]

Pour Commerce 2.4.8 et les versions antérieures, utilisez la configuration suivante pour définir le seuil de nettoyage à 90 % :

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

L’utilisation varie d’un nœud à l’autre, mais converge vers une valeur similaire.

## Exemples de configurations

Utilisez les exemples suivants comme point de départ pour vos configurations de service Redis ou Valkey.


### Appliquer toutes les recommandations de bonnes pratiques

>[!BEGINTABS]

>[!TAB Exemple de configuration Valkey]

Par `VALKEY_BACKEND: symfony_l2`, `ece-tools` générer les fronts `default` et `stale_cache_enabled` et leurs mappages de type cache. Ne définissez pas de `use_stale_cache` sur le front-end large `default`. Le bloc de `CACHE_CONFIGURATION` ci-dessous contient uniquement des remplacements d’options principales explicites.

```yaml
stage:
  deploy:
    MYSQL_USE_SLAVE_CONNECTION: true
    VALKEY_USE_SLAVE_CONNECTION: true # Enables read-only replica connection logic in Magento. It also works in a split architecture.
    VALKEY_BACKEND: symfony_l2 # Use symfony_l2 for Adobe Commerce 2.4.9 and later
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default:
          id_prefix: '001_' # any prefix is fine, but keep it consistent.
          backend_options:
            connect_retries: 3                # Number of connection retries
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

>[!TAB  Exemple de configuration Redis ]

Utilisez la configuration suivante pour Redis sur Adobe Commerce 2.4.8 et les versions antérieures :

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

### Séparer le cache obsolète par type de cache

>[!BEGINTABS]

>[!TAB  Valkey ]

```yaml
stage:
  deploy:
    MYSQL_USE_SLAVE_CONNECTION: true
    VALKEY_USE_SLAVE_CONNECTION: true # Enables read-only replica connection logic in Magento. It also works in a split architecture
    VALKEY_BACKEND: symfony_l2 # Use symfony_l2 for Adobe Commerce 2.4.9 and later
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default: # Keep stale cache disabled on the broad default frontend.
          id_prefix: '001_' # Keep this prefix consistent with the frontend configuration generated in env.php
          backend_options:
            connect_retries: 3
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
          backend: symfony_l2
          backend_options:
            remote_backend: valkey
            remote_backend_options:
              server: localhost
              port: 6370   # Use the same port used by the source frontend in env.php
              database: 1
              load_from_slave:
                server: localhost
                port: 26370 # Use the same read-only replica connection/read port used by the source frontend in env.php
              retry_reads_on_master: 1
              read_timeout: 10
            local_backend: file
            local_backend_options:
              cache_dir: /dev/shm/
            use_stale_cache: true
            connect_retries: 3
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
    REDIS_USE_SLAVE_CONNECTION: true # Enables read-only replica connection logic in Magento. It also works in a split architecture
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

>[!MORELIKETHIS]
>
>- [Configurer le service Valkey](https://experienceleague.adobe.com/fr/docs/commerce-on-cloud/user-guide/configure/service/valkey)
>- [Configurer le service Redis](https://experienceleague.adobe.com/fr/docs/commerce-on-cloud/user-guide/configure/service/redis)
>- [Déployer les variables](https://experienceleague.adobe.com/fr/docs/commerce-on-cloud/user-guide/configure/env/stage/variables-deploy)
