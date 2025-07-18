---
title: Utiliser Redis pour le cache par défaut
description: Découvrez comment configurer Redis comme cache par défaut pour Adobe Commerce.
feature: Configuration, Cache
exl-id: 8c097cfc-85d0-4e96-b56e-284fde40d459
source-git-commit: 2c489f2655e6fb067de1730355df6cd3683ea562
workflow-type: tm+mt
source-wordcount: '1126'
ht-degree: 0%

---

# Utiliser Redis pour le cache par défaut

Commerce fournit des options de ligne de commande pour configurer la page Redis et la mise en cache par défaut. Bien que vous puissiez configurer la mise en cache en modifiant le fichier `<Commerce-install-dir>app/etc/env.php`, il est recommandé d’utiliser la ligne de commande, en particulier pour les configurations initiales. La ligne de commande permet de valider en s’assurant que la configuration est correcte sur le plan syntaxique.

Vous devez [installer Redis](config-redis.md#install-redis) avant de continuer.

## Configurer la mise en cache par défaut de Redis

Exécutez la commande `setup:config:set` et spécifiez des paramètres spécifiques à la mise en cache par défaut de Redis.

```bash
bin/magento setup:config:set --cache-backend=redis --cache-backend-redis-<parameter>=<value>...
```

Avec les paramètres suivants :

- `--cache-backend=redis` active la mise en cache par défaut de Redis. Si cette fonctionnalité a déjà été activée, omettez ce paramètre.

- `--cache-backend-redis-<parameter>=<value>` une liste de paires clé-valeur qui configurent la mise en cache par défaut :

| Paramètre de ligne de commande | Valeur | Signification | Valeur par défaut |
| ------------------------------ | --------- | ------- | ------------- |
| `cache-backend-redis-server` | serveur | Nom d’hôte complet, adresse IP ou chemin d’accès absolu à un socket UNIX. La valeur par défaut 127.0.0.1 indique que Redis est installé sur le serveur Commerce. | `127.0.0.1` |
| `cache-backend-redis-port` | port | Port d’écoute du serveur Redis | `6379` |
| `cache-backend-redis-db` | de données | Obligatoire si vous utilisez Redis pour le cache par défaut et le cache de page complète. Vous devez indiquer le numéro de base de données de l&#39;un des caches ; l&#39;autre cache utilise 0 par défaut.<br><br>**Important** : si vous utilisez Redis pour plusieurs types de mise en cache, les numéros de base de données doivent être différents. Il est recommandé d&#39;attribuer le numéro de base de données de mise en cache par défaut à 0, le numéro de base de données de mise en cache de page à 1 et le numéro de base de données de stockage de session à 2. | `0` |
| `cache-backend-redis-password` | mot de passe | La configuration d’un mot de passe Redis active l’une de ses fonctionnalités de sécurité intégrées : la commande `auth`, qui nécessite que les clients s’authentifient pour accéder à la base de données. Le mot de passe est configuré directement dans le fichier de configuration de Redis : `/etc/redis/redis.conf` | |
| `--cache-backend-redis-use-lua` | use_lua | Activez ou désactivez LUA. <br><br>**LUA** : Lua nous permet d’exécuter une partie de la logique de l’application dans Redis, ce qui améliore les performances et assure la cohérence des données grâce à son exécution atomique. | `0` |
| `--cache-backend-redis-use-lua-on-gc` | use_lua_on_gc | Activez ou désactivez LUA pour le nettoyage. <br><br>**LUA** : Lua nous permet d’exécuter une partie de la logique de l’application dans Redis, ce qui améliore les performances et assure la cohérence des données grâce à son exécution atomique. | `1` |

### Exemple de commande

L&#39;exemple suivant active la mise en cache par défaut de Redis, définit l&#39;hôte sur `127.0.0.1` et affecte le numéro de base de données à 0. Redis utilise les valeurs par défaut pour tous les autres paramètres.

```bash
bin/magento setup:config:set --cache-backend=redis --cache-backend-redis-server=127.0.0.1 --cache-backend-redis-db=0
```

## Configuration de la mise en cache des pages Redis

Pour configurer la mise en cache des pages Redis sur Commerce, exécutez la commande `setup:config:set` avec des paramètres supplémentaires.

```bash
bin/magento setup:config:set --page-cache=redis --page-cache-redis-<parameter>=<value>...
```

Avec les paramètres suivants :

- `--page-cache=redis` active la mise en cache de page Redis. Si cette fonctionnalité a déjà été activée, omettez ce paramètre.

- `--page-cache-redis-<parameter>=<value>` une liste de paires clé-valeur qui configurent la mise en cache de page :

| Paramètre de ligne de commande | Valeur | Signification | Valeur par défaut |
| ------------------------------ | --------- | ------- | ------------- |
| `page-cache-redis-server` | serveur | Nom d’hôte complet, adresse IP ou chemin d’accès absolu à un socket UNIX. La valeur par défaut 127.0.0.1 indique que Redis est installé sur le serveur Commerce. | `127.0.0.1` |
| `page-cache-redis-port` | port | Port d’écoute du serveur Redis | `6379` |
| `page-cache-redis-db` | de données | Obligatoire si vous utilisez Redis pour le cache de page par défaut et le cache de page complet. Vous devez indiquer le numéro de base de données de l&#39;un des caches ; l&#39;autre cache utilise 0 par défaut.<br/>**Important** : si vous utilisez Redis pour plusieurs types de mise en cache, les numéros de base de données doivent être différents. Il est recommandé d&#39;attribuer le numéro de base de données de mise en cache par défaut à 0, le numéro de base de données de mise en cache de page à 1 et le numéro de base de données de stockage de session à 2. | `0` |
| `page-cache-redis-password` | mot de passe | La configuration d’un mot de passe Redis active l’une de ses fonctionnalités de sécurité intégrées : la commande `auth`, qui nécessite que les clients s’authentifient pour accéder à la base de données. Configurez le mot de passe dans le fichier de configuration Redis : `/etc/redis/redis.conf` | |

### Exemple de commande

L&#39;exemple suivant active la mise en cache de page Redis, définit l&#39;hôte sur `127.0.0.1` et affecte le numéro de base de données à 1. Tous les autres paramètres sont définis sur la valeur par défaut.

```bash
bin/magento setup:config:set --page-cache=redis --page-cache-redis-server=127.0.0.1 --page-cache-redis-db=1
```

## Résultats

Suite à ces deux exemples de commandes, Commerce ajoute des lignes similaires à ce qui suit à `<Commerce-install-dir>app/etc/env.php` :

```php
'cache' => [
    'frontend' => [
        'default' => [
            'backend' => 'Magento\\Framework\\Cache\\Backend\\Redis',
            'backend_options' => [
                'server' => '127.0.0.1',
                'database' => '0',
                'port' => '6379'
            ],
        ],
        'page_cache' => [
            'backend' => 'Magento\\Framework\\Cache\\Backend\\Redis',
            'backend_options' => [
                'server' => '127.0.0.1',
                'port' => '6379',
                'database' => '1',
                'compress_data' => '0'
            ]
        ]
    ]
],
```

## Utilisation d’AWS ElastiCache avec votre instance EC2

Depuis Commerce version 2.4.3, les instances hébergées sur Amazon EC2 peuvent utiliser un ElastiCache AWS à la place d’une instance Redis locale.

>[!WARNING]
>
>Cette section fonctionne uniquement pour les instances Commerce s’exécutant sur des VPC EC2 d’Amazon. Il ne fonctionne pas pour les installations sur site.

### Configuration d’un cluster Redis

Après [configuration d’un cluster Redis sur AWS](https://aws.amazon.com/getting-started/hands-on/setting-up-a-redis-cluster-with-amazon-elasticache/), configurez l’instance EC2 pour utiliser ElastiCache.

1. [Créez un cluster ElastiCache](https://docs.aws.amazon.com/AmazonElastiCache/latest/red-ug/set-up.html) dans la même région et le même VPC de l’instance EC2.
1. Vérifiez la connexion.

   - Ouvrez une connexion SSH à votre instance EC2
   - Sur l’instance EC2, installez le client Redis :

     ```bash
     sudo apt-get install redis
     ```

   - Ajoutez une règle entrante au groupe de sécurité EC2 : Type `- Custom TCP, port - 6379, Source - 0.0.0.0/0`
   - Ajoutez une règle entrante au groupe de sécurité de cluster ElastiCache : Type `- Custom TCP, port - 6379, Source - 0.0.0.0/0`
   - Connectez-vous à l’interface de ligne de commande Redis :

     ```bash
     redis-cli -h <ElastiCache Primary Endpoint host> -p <ElastiCache Primary Endpoint port>
     ```

### Configuration de Commerce pour utiliser le cluster

Commerce prend en charge plusieurs types de configurations de mise en cache. En règle générale, les configurations de mise en cache sont réparties entre le serveur frontal et le serveur principal. La mise en cache front-end est classée comme `default`, utilisée pour tout type de cache. Vous pouvez personnaliser ou diviser les caches en caches de niveau inférieur pour obtenir de meilleures performances. Une configuration Redis courante consiste à séparer le cache par défaut et le cache de page dans leur propre base de données Redis (RDB).

Exécutez `setup` commandes pour spécifier les points d’entrée Redis.

Pour configurer Commerce pour Redis en tant que mise en cache par défaut :

```bash
bin/magento setup:config:set --cache-backend=redis --cache-backend-redis-server=<ElastiCache Primary Endpoint host> --cache-backend-redis-port=<ElastiCache Primary Endpoint port> --cache-backend-redis-db=0
```

Pour configurer Commerce pour la mise en cache de page Redis, procédez comme suit :

```bash
bin/magento setup:config:set --page-cache=redis --page-cache-redis-server=<ElastiCache Primary Endpoint host> --page-cache-redis-port=<ElastiCache Primary Endpoint port> --page-cache-redis-db=1
```

Pour configurer Commerce afin d’utiliser Redis pour le stockage de session :

```bash
bin/magento setup:config:set --session-save=redis --session-save-redis-host=<ElastiCache Primary Endpoint host> --session-save-redis-port=<ElastiCache Primary Endpoint port> --session-save-redis-log-level=4 --session-save-redis-db=2
```

### Vérifier la connectivité

**Pour vérifier que Commerce communique avec ElastiCache** :

1. Ouvrez une connexion SSH à l’instance Commerce EC2.
1. Démarrez le moniteur Redis.

   ```bash
   redis-cli -h <ElastiCache-Primary-Endpoint-host> -p <ElastiCache-Primary-Endpoint-port> monitor
   ```

1. Ouvrez une page dans l’interface utilisateur de Commerce.
1. Vérifiez la sortie [cache](#verify-redis-connection) dans votre terminal.

## Nouvelle implémentation du cache Redis

Depuis Commerce version 2.3.5, il est recommandé d’utiliser l’implémentation étendue du cache Redis : `\Magento\Framework\Cache\Backend\Redis`.

```php
'cache' => [
    'frontend' => [
        'default' => [
            'backend' => '\\Magento\\Framework\\Cache\\Backend\\Redis',
            'backend_options' => [
                'server' => '127.0.0.1',
                'database' => '0',
                'port' => '6379'
            ],
        ],
],
```

## Fonction de préchargement Redis

Comme Commerce stocke les données de configuration dans le cache Redis, nous pouvons précharger les données réutilisées entre les pages. Pour rechercher les clés qui doivent être préchargées, analysez les données transférées de Redis vers Commerce. Nous vous suggérons de précharger les données chargées sur chaque page, telles que `SYSTEM_DEFAULT`, `EAV_ENTITY_TYPES`, `DB_IS_UP_TO_DATE`.

Redis utilise le `pipeline` afin de composer les requêtes de chargement. Les clés doivent inclure le préfixe de la base de données. Par exemple, si le préfixe de la base de données est `061_`, la clé de préchargement ressemble à ce qui suit : `061_SYSTEM_DEFAULT`

```php
'cache' => [
    'frontend' => [
        'default' => [
            'id_prefix' => '061_',
            'backend' => 'Magento\\Framework\\Cache\\Backend\\Redis',
            'backend_options' => [
                'server' => 'redis',
                'database' => '0',
                'port' => '6379',
                'password' => '',
                'compress_data' => '1',
                'compression_lib' => '',
                'preload_keys' => [
                    '061_EAV_ENTITY_TYPES',
                    '061_GLOBAL_PLUGIN_LIST',
                    '061_DB_IS_UP_TO_DATE',
                    '061_SYSTEM_DEFAULT',
                ],
            ]
        ],
        'page_cache' => [
            'id_prefix' => '061_'
        ]
    ]
]
```

Si vous utilisez la fonction de préchargement avec le cache L2, n’oubliez pas d’ajouter le suffixe `:hash` à vos clés, car le cache L2 ne transfère que le hachage des données, et non les données elles-mêmes :

```php
'preload_keys' => [
    '061_EAV_ENTITY_TYPES:hash',
    '061_GLOBAL_PLUGIN_LIST:hash',
    '061_DB_IS_UP_TO_DATE:hash',
    '061_SYSTEM_DEFAULT:hash',
],
```

## Génération parallèle

À partir de la version 2.4.0, nous avons introduit l’option `allow_parallel_generation` pour les utilisateurs qui souhaitent éliminer les attentes de verrous.
Il est désactivé par défaut et nous vous recommandons de le désactiver jusqu’à ce que vous disposiez de configurations et/ou de blocs excessifs.

**Pour activer la génération parallèle** :

```bash
bin/magento setup:config:set --allow-parallel-generation
```

Comme il s’agit d’un indicateur , vous ne pouvez pas le désactiver avec une commande. Vous devez définir manuellement la valeur de configuration sur `false` :

```php
    'cache' => [
        'frontend' => [
            'default' => [
                'id_prefix' => 'b0b_',
                'backend' => 'Magento\\Framework\\Cache\\Backend\\Redis',
                'backend_options' => [
                    'server' => 'redis',
                    'database' => '0',
                    'port' => '6379',
                    'password' => '',
                    'compress_data' => '1',
                    'compression_lib' => ''
                ]
            ],
            'page_cache' => [
                'id_prefix' => 'b0b_'
            ]
        ],
        'allow_parallel_generation' => false
    ],
```

## Vérifier la connexion Redis

Pour vérifier que Redis et Commerce fonctionnent ensemble, connectez-vous au serveur exécutant Redis, ouvrez un terminal et utilisez la commande Redis monitor ou la commande ping.

### Commande Redis monitor

```bash
redis-cli monitor
```

Exemple de sortie de mise en cache de page :

```
1476826133.810090 [0 127.0.0.1:52366] "select" "1"
1476826133.816293 [0 127.0.0.1:52367] "select" "0"
1476826133.817461 [0 127.0.0.1:52367] "hget" "zc:k:ea6_GLOBAL__DICONFIG" "d"
1476826133.829666 [0 127.0.0.1:52367] "hget" "zc:k:ea6_DICONFIG049005964B465901F774DB9751971818" "d"
1476826133.837854 [0 127.0.0.1:52367] "hget" "zc:k:ea6_INTERCEPTION" "d"
1476826133.868374 [0 127.0.0.1:52368] "select" "1"
1476826133.869011 [0 127.0.0.1:52369] "select" "0"
1476826133.869601 [0 127.0.0.1:52369] "hget" "zc:k:ea6_DEFAULT_CONFIG_CACHE_DEFAULT__10__235__32__1080MAGENTO2" "d"
1476826133.872317 [0 127.0.0.1:52369] "hget" "zc:k:ea6_INITIAL_CONFIG" "d"
1476826133.879267 [0 127.0.0.1:52369] "hget" "zc:k:ea6_GLOBAL_PRIMARY_PLUGIN_LIST" "d"
1476826133.883312 [0 127.0.0.1:52369] "hget" "zc:k:ea6_GLOBAL__EVENT_CONFIG_CACHE" "d"
1476826133.898431 [0 127.0.0.1:52369] "hget" "zc:k:ea6_DB_PDO_MYSQL_DDL_STAGING_UPDATE_1" "d"
1476826133.898794 [0 127.0.0.1:52369] "hget" "zc:k:ea6_RESOLVED_STORES_D1BEFA03C79CA0B84ECC488DEA96BC68" "d"
1476826133.905738 [0 127.0.0.1:52369] "hget" "zc:k:ea6_DEFAULT_CONFIG_CACHE_STORE_DEFAULT_10__235__32__1080MAGENTO2" "d"

... more ...

1476826210.634998 [0 127.0.0.1:52439] "hmset" "zc:k:ea6_MVIEW_CONFIG" "d" "a:18:{s:19:\"design_config_dummy\";a:4:{s:7:\"view_id\";s:19:\"design_config_dummy\";s:12:\"action_class\";s:39:\"Magento\\Theme\\Model\\Indexer\\Mview\\Dummy\";s:5:\"group\";s:7:\"indexer\";s:13:\"subscriptions\";a:0:{}}s:14:\"customer_dummy\";a:4:{s:7:\"view_id\";s:14:\"customer_dummy\";s:12:\"action_class\";s:42:\"Magento\\Customer\\Model\\Indexer\\Mview\\Dummy\";s:5:\"group\";s:7:\"indexer\";s:13:\"subscriptions\";a:0:{}}s:13:\"cms_page_grid\";a:4:{s:7:\"view_id\";s:13:\"cms_page_grid\";s:12:\"action_class\";s:43:\"Magento\\Catalog\\Model\\Indexer\\Category\\Flat\";s:5:\"group\";s:7:\"indexer\";s:13:\"subscriptions\";a:1:{s:8:\"cms_page\";a:3:{s:4:\"name\";s:8:\"cms_page\";s:6:\"column\";s:7:\"page_id\";s:18:\"subscription_model\";N;}}}s:21:\"catalog_category_flat\";a:4:{s:7:\"view_id\";s:21:\"catalog_category_flat\";s:12:\"action_class\";s:43:\"Magento\\Catalog\\Model\\Indexer\\Category\\Flat\";s:5:\"group\";s:7:\"indexer\";s:13:\"subscriptions\";a:6:{s:23:\"catalog_category_entity\";a:3:{s:4:\"name\";s:23:\"catalog_category_entity\";s:6:\"column\";s:9:\"entity_id\";s:18:\"subscription_model\";N;}s:31:\"catalog_category_entity_decimal\";a:3:{s:4:\"name\";s:31:\"catalog_category_entity_decimal\";s:6:\"column\";s:9:\"entity_id\";s:18:\"subscription_model\";s:71:\"Magento\\CatalogStaging\\Model\\Mview\\View\\Category\\Attribute\\Subscription\";}s:27:\"catalog_category_entity_int\";a:3:{s:4:\"name\";s:27:\"catalog_category_entity_int\";s:6:\"column\";s:9:\"entity_id\";s:18:\"subscription_model\";s:71:\"Magento\\CatalogStaging\\Model\\Mview\\View\\Category\\Attribute\\Subscription\";}s:28:\"catalog_category_entity_text\";a:3:{s:4:\"name\";s:28:\"catalog_category_entity_text\";s:6:\"column\";s:9:\"entity_id\";s:18:\"subscription_model\";s:71:\"Magento\\CatalogStaging\\Model\\Mview\\View\\Category\\Attribute\\Subscription\";}s:31:\"catalog_category_entity_varchar\";a:3:{s:4:\"name\";s:31:\"catalog_category_entity_varchar\";s:6:\"column\";s:9:\"entity_id\";s:18:\"subscription_model\";s:71:\"Magento\\CatalogStaging\\Model\\Mview\\View\\Category\\Attribute\\Subscription\";}s:32:\"catalog_category_entity_datetime\";a:3:{s:4:\"name\";s:32:\"catalog_category_entity_datetime\";s:6:\"column\";s:9:\"entity_id\";s:18:\"subscription_model\";s:71:\"Magento\\CatalogStaging\\Model\\Mview\\View\\Category\\Attribute\\Subscription\";}}}s:24:\"catalog_category_product\";a:4:{s:7:\"view_id\";s:24:\"catalog_category_product\";s:12:\"action_class\";s:46:\"Magento\\Catalog\\Model\\Indexer\\Category\\Product\";s:5:\"group\";s:7:\"indexer\";s:13:\"subscriptions\";a:2:{s:23:\"catalog_category_entity\";a:3:{s:4:\"name\";s:23:\"catalog_category_entity\";s:6:\"column\"

... more ...
```

### Commande de redimensionnement

```bash
redis-cli ping
```

La réponse attendue est : `PONG`

Si les deux commandes ont réussi, Redis est correctement configuré.

### Inspection des données compressées

Pour inspecter les données de session compressées et le cache de page, le [RESP.app](https://flathub.org/apps/details/app.resp.RESP) prend en charge la décompression automatique du cache de session et de page de Commerce 2 et affiche les données de session PHP sous une forme lisible par l&#39;utilisateur.
