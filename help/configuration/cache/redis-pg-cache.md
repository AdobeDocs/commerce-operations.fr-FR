---
title: Utiliser des redis pour le cache par défaut
description: Découvrez comment configurer Redis comme cache par défaut pour Adobe Commerce et Magento Open Source.
source-git-commit: 80abb0180fcd8ecc275428c23b68feb5883cbc28
workflow-type: tm+mt
source-wordcount: '1088'
ht-degree: 0%

---


# Utiliser des redis pour le cache par défaut

Commerce fournit des options de ligne de commande pour configurer la page Redis et la mise en cache par défaut. Bien que vous puissiez configurer la mise en cache en modifiant le `<Commerce install dir>app/etc/env.php` , il est recommandé d’utiliser la ligne de commande, en particulier pour les configurations initiales. La ligne de commande fournit la validation, en s’assurant que la configuration est syntaxiquement correcte.

Vous devez [install Redis](config-redis.md#install-redis) avant de continuer.

## Configuration de la mise en cache par défaut de Redis

Exécutez la variable `setup:config:set` et spécifiez des paramètres spécifiques à la mise en cache par défaut Redis.

```bash
bin/magento setup:config:set --cache-backend=redis --cache-backend-redis-<parameter_name>=<parameter_value>...
```

where

`--cache-backend=redis` active la mise en cache par défaut Redis. Si cette fonctionnalité a déjà été activée, omettez ce paramètre.

`--cache-backend-redis-<parameter_name>=<parameter_value>` est une liste de paires clé-valeur qui configurent la mise en cache par défaut :

| Paramètre de ligne de commande | Paramètre | Signification | Valeur par défaut |
|--- |--- |--- |--- |
| cache-backend-redis-server | server | Nom d’hôte complet, adresse IP ou chemin absolu vers un socket UNIX. La valeur par défaut 127.0.0.1 indique que Redis est installé sur le serveur Commerce. | 127.0.0.1 |
| cache-backend-redis-port | port | Port d’écoute du serveur Redis | 6379 |
| cache-backend-redis-db | base | Obligatoire si vous utilisez Redis pour le cache par défaut et de page entière. Vous devez indiquer le numéro de la base de données d’un des caches ; l’autre cache utilise 0 par défaut.<br><br>Important : Si vous utilisez Redis pour plusieurs types de mise en cache, les numéros de la base de données doivent être différents. Il est recommandé d’attribuer le numéro de base de données de mise en cache par défaut à 0, le numéro de base de données de mise en cache de page à 1 et le numéro de base de données de stockage de session à 2. | 0 |
| cache-backend-redis-password | password | La configuration d’un mot de passe Redis active l’une de ses fonctionnalités de sécurité intégrées : la valeur `auth` , ce qui nécessite que les clients s’authentifient pour accéder à la base de données. Le mot de passe est directement configuré dans le fichier de configuration de Redis, `/etc/redis/redis.conf`. |  |

### Exemple, commande

L’exemple suivant active la mise en cache par défaut de Redis, définit l’hôte sur `127.0.0.1` et attribue le numéro de la base de données à 0. Redis utilise les valeurs par défaut de tous les autres paramètres.

```bash
bin/magento setup:config:set --cache-backend=redis --cache-backend-redis-server=127.0.0.1 --cache-backend-redis-db=0
```

## Configuration de la mise en cache de la page Redis

Pour configurer la mise en cache de la page Redis dans Commerce, exécutez le `setup:config:set` avec des paramètres supplémentaires.

```bash
bin/magento setup:config:set --page-cache=redis --page-cache-redis-<parameter_name>=<parameter_value>...
```

where

`--page-cache=redis` active la mise en cache de la page Redis. Si cette fonctionnalité a déjà été activée, omettez ce paramètre.

`--page-cache-redis-<parameter_name>=<parameter_value>` est une liste de paires paramètre/valeur qui configurent la mise en cache de page :

| Paramètre de ligne de commande | Paramètre | Signification | Valeur par défaut |
|--- |--- |--- |--- |
| page-cache-redis-server | server | Nom d’hôte complet, adresse IP ou chemin absolu vers un socket UNIX. La valeur par défaut 127.0.0.1 indique que Redis est installé sur le serveur Commerce. | 127.0.0.1 |
| page-cache-redis-port | port | Port d’écoute du serveur Redis | 6379 |
| page-cache-redis-db | base | Obligatoire si vous utilisez Redis pour le cache de page par défaut et complet. Vous devez indiquer le numéro de la base de données d’un des caches ; l’autre cache utilise 0 par défaut.<br/>Important : Si vous utilisez Redis pour plusieurs types de mise en cache, les numéros de la base de données doivent être différents. Il est recommandé d’attribuer le numéro de base de données de mise en cache par défaut à 0, le numéro de base de données de mise en cache de page à 1 et le numéro de base de données de stockage de session à 2. | 0 |
| page-cache-redis-password | password | La configuration d’un mot de passe Redis active l’une de ses fonctionnalités de sécurité intégrées : la valeur `auth` , ce qui nécessite que les clients s’authentifient pour accéder à la base de données. Configurez le mot de passe dans le fichier de configuration Redis, /etc/redis/redis.conf. |  |

### Exemple, commande

L’exemple suivant active la mise en cache de la page Redis, définit l’hôte sur `127.0.0.1` et attribue le numéro de la base de données à 1. Tous les autres paramètres sont définis sur la valeur par défaut.

```bash
bin/magento setup:config:set --page-cache=redis --page-cache-redis-server=127.0.0.1 --page-cache-redis-db=1
```

## Résultats

Suite aux deux exemples de commandes, Commerce ajoute des lignes similaires à ce qui suit : `<Commerce install dir>app/etc/env.php`:

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

Depuis Commerce 2.4.3, les instances hébergées sur Amazon EC2 peuvent utiliser un ElastiCache AWS à la place d’une instance Redis locale.

>[!WARNING]
>
>Cette section ne fonctionne que pour les instances Commerce s’exécutant sur des VPC Amazon EC2. Il ne fonctionne pas pour les installations sur site.

### Configuration d’une grappe Redis

Après [configuration d’une grappe Redis sur AWS](https://aws.amazon.com/getting-started/hands-on/setting-up-a-redis-cluster-with-amazon-elasticache/), configurez l’instance EC2 pour utiliser ElastiCache.

1. [Création d’une grappe ElastiCache](https://docs.aws.amazon.com/AmazonElastiCache/latest/red-ug/set-up.html) dans la même région et le VPC de l’instance EC2.
1. Vérifiez la connexion.

   - Ouvrez une connexion SSH à votre instance EC2.
   - Sur l’instance EC2, installez le client Redis :

      ```bash
      sudo apt-get install redis
      ```

   - Ajoutez une règle entrante au groupe de sécurité EC2 : Type `- Custom TCP, port - 6379, Source - 0.0.0.0/0`
   - Ajoutez une règle entrante au groupe de sécurité Cluster ElastiCache : Type `- Custom TCP, port - 6379, Source - 0.0.0.0/0`
   - Connectez-vous à l’interface de ligne de commande Redis :

      ```bash
      redis-cli -h <ElastiCache Primary Endpoint host> -p <ElastiCache Primary Endpoint port>
      ```

### Configuration de Commerce pour l’utilisation de la grappe

Commerce prend en charge plusieurs types de configurations de mise en cache. En règle générale, les configurations de mise en cache sont fractionnées entre front-end et backend. La mise en cache frontale est classée comme &quot;par défaut&quot;, utilisée pour tout type de cache. Vous pouvez personnaliser ou diviser en caches de niveau inférieur pour obtenir de meilleures performances. Une configuration Redis courante consiste à séparer le cache par défaut et le cache de page dans leur propre base de données Redis (RDB).

Exécuter `setup` pour spécifier les points d’entrée Redis.

Configuration de Commerce pour Redis en tant que mise en cache par défaut :

```bash
bin/magento setup:config:set --cache-backend=redis --cache-backend-redis-server=<ElastiCache Primary Endpoint host> --cache-backend-redis-port=<ElastiCache Primary Endpoint port> --cache-backend-redis-db=0
```

Configurez la mise en cache de la page Commerce for Redis :

```bash
bin/magento setup:config:set --page-cache=redis --page-cache-redis-server=<ElastiCache Primary Endpoint host> --page-cache-redis-port=<ElastiCache Primary Endpoint port> --page-cache-redis-db=1
```

Configurez Commerce pour utiliser Redis pour le stockage de session :

```bash
bin/magento setup:config:set --session-save=redis --session-save-redis-host=<ElastiCache Primary Endpoint host> --session-save-redis-port=<ElastiCache Primary Endpoint port> --session-save-redis-log-level=4 --session-save-redis-db=2
```

### Vérification de la connectivité

Pour vérifier que Commerce parle à ElasiCache :

1. Ouvrez une connexion SSH à l’instance Commerce EC2.
1. Démarrez le moniteur Redis.

   ```bash
   redis-cli -h <ElastiCache Primary Endpoint host> -p <ElastiCache Primary Endpoint port> monitor
   ```

1. Ouvrez une page dans l’interface utilisateur de Commerce.
1. Vérifiez les [sortie du cache](#verify-redis-connection) dans votre terminal.

## Nouvelle implémentation du cache Redis

À compter de Commerce 2.3.5, il est recommandé d’utiliser l’implémentation étendue du cache Redis : `\Magento\Framework\Cache\Backend\Redis`.

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

Comme Commerce stocke de nombreuses données de configuration dans le cache Redis, nous pouvons précharger des données réutilisées entre les pages.
Pour trouver les clés qui doivent être préchargées, vous devez analyser les données transférées de Redis vers Commerce. Nous suggérons de précharger les données chargées sur chaque page, les exemples les plus courants sont les suivants : `SYSTEM_DEFAULT`, `EAV_ENTITY_TYPES`, `DB_IS_UP_TO_DATE`.
Redis utilise la variable `pipeline` afin de combiner des requêtes de chargement.
Veuillez noter que les clés doivent inclure le préfixe de base de données, par exemple si le préfixe de base de données est `061_`, la clé de préchargement ressemble à `061_SYSTEM_DEFAULT`.

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

Si vous utilisez la fonctionnalité de préchargement avec le cache L2, n&#39;oubliez pas d&#39;ajouter le suffixe &#39;:hash&#39; à vos clés, puisque le cache L2 ne transfère que le hachage des données, et non les données elles-mêmes :

```php
'preload_keys' => [
    '061_EAV_ENTITY_TYPES:hash',
    '061_GLOBAL_PLUGIN_LIST:hash',
    '061_DB_IS_UP_TO_DATE:hash',
    '061_SYSTEM_DEFAULT:hash',
],
```

## Génération parallèle

À compter de la version 2.4.0, nous avons introduit la variable `allow_parallel_generation` pour les utilisateurs qui souhaitent supprimer les abandons pour les verrous.
Il est désactivé par défaut et nous vous recommandons de le désactiver jusqu&#39;à ce que vous ayez un nombre excessif de configurations et/ou de blocs.

**Pour activer la génération parallèle**:

```bash
bin/magento setup:config:set --allow-parallel-generation
```

Comme il s’agit d’un indicateur, vous ne pouvez pas le désactiver à l’aide d’une commande . Vous devez définir manuellement la valeur de configuration sur `false`:

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

## Vérification de la connexion Redis

Pour vérifier que Redis et Commerce fonctionnent ensemble, connectez-vous au serveur exécutant Redis, ouvrez un terminal et utilisez la commande Redis monitor ou la commande ping .

### Redis monitor, commande

```bash
redis-cli monitor
```

Exemple de sortie de mise en cache de page :

```terminal
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

### Redis ping, commande

```bash
redis-cli ping
```

`PONG` doit être la réponse.

Si les deux commandes ont réussi, Redis est configuré correctement.

### Inspection des données compressées

Pour examiner les données de session compressées et le cache de page, la variable [RESP.app](https://flathub.org/apps/details/app.resp.RESP) prend en charge la décompression automatique du cache de session et de page Commerce 2 et affiche les données de session PHP sous une forme lisible.
