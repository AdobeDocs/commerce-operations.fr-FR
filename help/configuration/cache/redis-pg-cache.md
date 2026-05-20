---
title: Configuration de Redis pour le cache de page et par défaut
description: Découvrez comment configurer Redis en tant que serveur principal par défaut et du cache de page pour Adobe Commerce. Découvrez les commandes de l’interface de ligne de commande, les paramètres env.php et la vérification de la connexion.
feature: Configuration, Cache
exl-id: 8c097cfc-85d0-4e96-b56e-284fde40d459
source-git-commit: d82061ad2fa4676bd8fa71a9d34a954444eb0f54
workflow-type: tm+mt
source-wordcount: '1467'
ht-degree: 0%

---

# Configuration de Redis pour le cache de page et par défaut

Commerce fournit des options de ligne de commande pour configurer la page Redis et la mise en cache par défaut. Bien que vous puissiez configurer la mise en cache en modifiant le fichier `<Commerce-install-dir>app/etc/env.php`, la ligne de commande est la méthode recommandée, en particulier pour les configurations initiales. La ligne de commande fournit une validation pour s’assurer que la configuration est correcte d’un point de vue syntaxique.

**Prérequis :**

[Installez Redis](config-redis.md#install-redis) avant de continuer.

>[!NOTE]
>
>Pour les instances Commerce hébergées sur EC2, vous pouvez utiliser AWS ElastiCache au lieu d’une instance Redis locale. Voir [Configuration d’Elasticache pour les instances EC2](redis-elasticache-for-ec2.md).

## Structures prises en charge

>[!BEGINTABS]

>[!TAB Zend Cache (2.4.8 et versions antérieures)]

- **Zend Cache (2.4.8 et versions antérieures)** — Serveur principal Redis hérité pour Commerce 2.4.8 et versions antérieures :
   - **Serveur principal Redis hérité** — Utilise le chemin de classe complet (`Magento\Framework\Cache\Backend\Redis`)
   - **Précharger les clés** — Prend en charge le préchargement des clés de cache fréquemment utilisées
   - **Scripts Lua** — Lua pour la récupération de l&#39;espace mémoire
   - **Compression** — Prend en charge la compression des données

>[!TAB Cache Symfony (2.4.9+)]

- **Symfony Cache (2.4.9+)** — À partir de Commerce 2.4.9, Symfony Cache fournit une mise en cache moderne, conforme à la norme PSR-6, pour Redis, avec des améliorations significatives des performances :
   - **Pipeline Redis automatique** : regroupe plusieurs opérations en une seule demande, ce qui réduit la latence.
   - **PSR-6 TagAwareAdapter** — Invalidation efficace du cache basé sur les balises avec des opérations atomiques
   - **Sérialisation igbinary** — La sérialisation binaire réduit la taille de l&#39;entrée du cache de 45 % et améliore la vitesse de 5 à 10 %
   - **Connexions persistantes améliorées** — Pool de connexions plus stable avec une meilleure gestion des processus dupliqués
   - **Scripts Lua optimisés** : exécution côté serveur combinée à la création de pipelines pour une efficacité maximale

>[!ENDTABS]


## Configurer la mise en cache par défaut de Redis

Exécutez la commande `setup:config:set` et spécifiez les paramètres spécifiques à la mise en cache par défaut de Redis.

```shell
bin/magento setup:config:set --cache-backend=redis --cache-backend-redis-<parameter>=<value>...
```

Avec les paramètres suivants :

- `--cache-backend=redis` active la mise en cache par défaut de Redis. Si cette fonctionnalité a déjà été activée, omettez ce paramètre.

- `--cache-backend-redis-<parameter>=<value>` une liste de paires clé-valeur qui configurent la mise en cache par défaut :

| Paramètre de ligne de commande | Valeur | Signification | Valeur par défaut |
| ------------------------------ | --------- | ------- | ------------- |
| `cache-backend-redis-server` | serveur | Nom d’hôte complet, adresse IP ou chemin d’accès absolu à un socket UNIX. La valeur par défaut 127.0.0.1 indique que Redis est installé sur le serveur Commerce. | `127.0.0.1` |
| `cache-backend-redis-port` | port | Port d’écoute du serveur Redis | `6379` |
| `cache-backend-redis-db` | de données | Obligatoire si vous utilisez Redis pour le cache par défaut et le cache de page complète. Indiquez le numéro de base de données de l’un des caches ; l’autre cache utilise 0 par défaut.<br><br>**Important** : si vous utilisez Redis pour plusieurs types de mise en cache, les numéros de base de données doivent être différents. Il est recommandé d&#39;attribuer le numéro de base de données de mise en cache par défaut à 0, le numéro de base de données de mise en cache de page à 1 et le numéro de base de données de stockage de session à 2. | `0` |
| `cache-backend-redis-password` | mot de passe | La configuration d’un mot de passe Redis active l’une de ses fonctionnalités de sécurité intégrées : la commande `auth`, qui nécessite que les clients s’authentifient pour accéder à la base de données. Le mot de passe est configuré directement dans le fichier de configuration de Redis : `/etc/redis/redis.conf` | |
| `cache-backend-redis-use-lua` | use_lua | Activez ou désactivez les scripts Lua pour toutes les opérations de lecture. <br><br>**Valeur par défaut : conserver à `0`.** Le mode Lua est désactivé par défaut pour éviter les régressions de performances connues et les problèmes d’échec de cache GraphQL introduits par la bibliothèque Redis groupée (1.17.x) lorsque Lua a été activé. | `0` |
| `cache-backend-redis-use-lua-on-gc` | use_lua_on_gc | Activez ou désactivez les scripts Lua pour le nettoyage (la tâche cron `backend_clean_cache`). <br><br>**Valeur par défaut : conserver à `1`.** Activé intentionnellement pour assurer le nettoyage atomique du jeu de balises pendant le GC. Sans cela, une condition de concurrence peut se produire lorsque le cron `backend_clean_cache` s’exécute en même temps qu’une opération d’enregistrement de cache, laissant les entrées de cache sans enregistrement correspondant dans l’index de balise de cache. Cela entraîne l’échec silencieux de l’invalidation basée sur les balises ; par exemple, la mise à jour d’un prix de produit peut ne pas invalider le cache de produit, nécessitant alors un vidage complet du cache. | `1` |

### Mode Lua

Lorsqu’il est activé, le mode Lua regroupe plusieurs opérations Redis (écritures de cache, mises à jour de balises, récupération de l’espace mémoire) dans un seul script atomique exécuté côté serveur via `EVALSHA`. Cela empêche l’entrelacement des requêtes simultanées, par exemple en s’assurant qu’une entrée de cache et son appartenance à une balise sont écrites ensemble.

>[!WARNING]
>
>Ne modifiez pas les valeurs par défaut de `use_lua` et `use_lua_on_gc` sans comprendre les implications pour votre version d’Adobe Commerce :
>
>- **`use_lua`** : l’activation de cette option sur Adobe Commerce 2.4.7 ou 2.4.8 (bibliothèque `colinmollenhour/cache-backend-redis` 1.17.1) peut entraîner une corruption du cache et des problèmes d’échec du cache GraphQL.
>- **`use_lua_on_gc`** : la désactivation de cette option sur Adobe Commerce 2.4.8 supprime la protection atomique pendant la récupération de l’espace mémoire et peut entraîner l’échec silencieux de l’invalidation du cache basé sur les balises, ce qui nécessite un vidage complet du cache pour la récupération.

## Exemple de commande (cache par défaut)

L&#39;exemple suivant active la mise en cache par défaut de Redis, définit l&#39;hôte sur `127.0.0.1` et affecte le numéro de base de données à 0. Redis utilise les valeurs par défaut pour tous les autres paramètres.

```shell
bin/magento setup:config:set --cache-backend=redis --cache-backend-redis-server=127.0.0.1 --cache-backend-redis-db=0
```

## Configuration de la mise en cache des pages Redis

Pour configurer la mise en cache des pages Redis sur Commerce, exécutez la commande `setup:config:set` avec des paramètres supplémentaires.

```shell
bin/magento setup:config:set --page-cache=redis --page-cache-redis-<parameter>=<value>...
```

Avec les paramètres suivants :

- `--page-cache=redis` active la mise en cache de page Redis. Si cette fonctionnalité a déjà été activée, omettez ce paramètre.

- `--page-cache-redis-<parameter>=<value>` une liste de paires clé-valeur qui configurent la mise en cache de page :

| Paramètre de ligne de commande | Valeur | Signification | Valeur par défaut |
| ------------------------------ | --------- | ------- | ------------- |
| `page-cache-redis-server` | serveur | Nom d’hôte complet, adresse IP ou chemin d’accès absolu à un socket UNIX. La valeur par défaut 127.0.0.1 indique que Redis est installé sur le serveur Commerce. | `127.0.0.1` |
| `page-cache-redis-port` | port | Port d’écoute du serveur Redis | `6379` |
| `page-cache-redis-db` | de données | Obligatoire si vous utilisez Redis pour le cache de page par défaut et le cache de page complet. Indiquez le numéro de base de données de l’un des caches ; l’autre cache utilise 0 par défaut.<br/>**Important** : si vous utilisez Redis pour plusieurs types de mise en cache, les numéros de base de données doivent être différents. Il est recommandé d&#39;attribuer le numéro de base de données de mise en cache par défaut à 0, le numéro de base de données de mise en cache de page à 1 et le numéro de base de données de stockage de session à 2. | `0` |
| `page-cache-redis-password` | mot de passe | La configuration d’un mot de passe Redis active l’une de ses fonctionnalités de sécurité intégrées : la commande `auth`, qui nécessite que les clients s’authentifient pour accéder à la base de données. Configurez le mot de passe dans le fichier de configuration Redis : `/etc/redis/redis.conf` | |

L&#39;exemple suivant active la mise en cache de page Redis, définit l&#39;hôte sur `127.0.0.1` et affecte le numéro de base de données à `1`. Tous les autres paramètres sont définis sur la valeur par défaut.

```shell
bin/magento setup:config:set --page-cache=redis --page-cache-redis-server=127.0.0.1 --page-cache-redis-db=1
```

{{valkey-redis-cli-note}}

### Vérification de la configuration de l’environnement Commerce

L’exécution des commandes pour configurer la mise en cache Redis met à jour la configuration de l’environnement Commerce (`<Commerce-install-dir>app/etc/env.php`) :

>[!BEGINTABS]

>[!TAB Zend Cache (2.4.8 et versions antérieures)]

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

>[!TAB Cache Symfony (2.4.9+)]

```php
'cache' => [
    'frontend' => [
        'default' => [
            'backend' => 'redis',
            'backend_options' => [
                'server' => '127.0.0.1',
                'database' => '0',
                'port' => '6379'
            ],
        ],
        'page_cache' => [
            'backend' => 'redis',
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

>[!NOTE]
>
>À partir de la version 2.4.9 de Commerce, utilisez le type de serveur principal simplifié `'backend' => 'redis'` au lieu du chemin d’accès de classe complet. Symfony Cache est automatiquement utilisé lorsque le nom simplifié est spécifié.

>[!ENDTABS]

## Configurer des options de mise en cache supplémentaires

### Fonction de préchargement Redis

Comme Commerce stocke les données de configuration dans le cache Redis, vous pouvez précharger les données réutilisées entre les pages. Pour rechercher les clés qui doivent être préchargées, analysez les données transférées de Redis vers Commerce. Adobe suggère de précharger les données chargées sur chaque page, telles que `SYSTEM_DEFAULT`, `EAV_ENTITY_TYPES` et `DB_IS_UP_TO_DATE`.

Redis utilise le `pipeline` pour les requêtes de chargement composites. Les clés doivent inclure le préfixe de la base de données. Par exemple, si le préfixe de la base de données est `061_`, la clé de préchargement ressemble à ceci : `061_SYSTEM_DEFAULT`

>[!BEGINTABS]

>[!TAB Envoyer le cache]

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

>[!TAB Cache Symfony]

```php
'cache' => [
    'frontend' => [
        'default' => [
            'id_prefix' => '061_',
            'backend' => 'redis',
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

>[!ENDTABS]

Lors de l’utilisation de la fonction de préchargement avec un cache L2, vous devez ajouter le suffixe `:hash` à vos clés. Le cache L2 transfère uniquement le hachage des données, et non les données réelles.

```php
'preload_keys' => [
    '061_EAV_ENTITY_TYPES:hash',
    '061_GLOBAL_PLUGIN_LIST:hash',
    '061_DB_IS_UP_TO_DATE:hash',
    '061_SYSTEM_DEFAULT:hash',
],
```

### Génération parallèle

À partir de la version 2.4.0 de Commerce, Adobe a introduit l’option `allow_parallel_generation` pour les utilisateurs qui souhaitent éliminer l’attente de verrous. Il est désactivé par défaut et Adobe recommande de le désactiver jusqu’à ce que vous disposiez de configurations et/ou de blocs excessifs.

**Pour activer la génération parallèle** :

```shell
bin/magento setup:config:set --allow-parallel-generation
```

Comme il s’agit d’un indicateur , vous ne pouvez pas le désactiver avec une commande. Définissez manuellement la valeur de configuration sur `false` :

>[!BEGINTABS]

>[!TAB Envoyer le cache]

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

>[!TAB Cache Symfony]

```php
    'cache' => [
        'frontend' => [
            'default' => [
                'id_prefix' => 'b0b_',
                'backend' => 'redis',
                'backend_options' => [
                    'server' => 'redis',
                    'database' => '0',
                    'port' => '6379',
                    'serializer' => 'igbinary',
                    'compress_data' => '1',
                    'compression_lib' => 'gzip'
                ]
            ],
            'page_cache' => [
                'id_prefix' => 'b0b_'
            ]
        ],
        'allow_parallel_generation' => false
    ],
```

>[!ENDTABS]


## Optimisation des performances du cache de synonymes

Si vous utilisez Symfony Cache, vous pouvez optimiser davantage les performances en configurant le sérialiseur Igbinary, en installant l&#39;extension PHP igbinary et l&#39;extension phpredis, et en activant les connexions persistantes.

### Sérialiseur Igbinaire

Le sérialiseur Igbinary offre des améliorations de performances significatives par rapport à la sérialisation par défaut de PHP. Il doit être configuré manuellement dans `app/etc/env.php` :

```php
'cache' => [
    'frontend' => [
        'default' => [
            'backend_options' => [
                'server' => 'redis',
                'database' => '0',
                'port' => '6379',
                'serializer' => 'igbinary',  // Enable Igbinary serialization
            ]
        ],
        'page_cache' => [
            'backend_options' => [
                'server' => 'redis',
                'database' => '1',
                'port' => '6379',
                'serializer' => 'igbinary',  // Enable Igbinary for page cache too
            ]
        ]
    ]
]
```

### Installer l&#39;extension PHP Igbinary

Pour utiliser la sérialisation igbinary, vous devez installer l&#39;extension PHP Igbinary.

**Utilisation d’apt (recommandé pour Debian/Ubuntu)** :

```bash
sudo apt-get install php-igbinary
sudo systemctl restart php-fpm
php -m | grep igbinary
```

**Utilisation de pecl (méthode alternative)** :

```bash
sudo pecl install igbinary
echo "extension=igbinary.so" | sudo tee /etc/php/8.3/mods-available/igbinary.ini
sudo phpenmod igbinary
sudo systemctl restart php-fpm
php -m | grep igbinary
```

### Extensions PHP Redis : phpredis vs Predis

Commerce 2.4.9+ inclut une version de secours automatique entre phpredis (extension native C) et Predis (bibliothèque PHP pure). Pour des performances optimales, installez phpredis :

**Utilisation d’apt (recommandé pour Debian/Ubuntu)** :

```bash
sudo apt-get install php-redis
sudo systemctl restart php-fpm
php -m | grep redis
```

**Utilisation de pecl (méthode alternative)** :

```bash
sudo pecl install redis
echo "extension=redis.so" | sudo tee /etc/php/8.3/mods-available/redis.ini
sudo phpenmod redis
sudo systemctl restart php-fpm
php -m | grep redis
```

**Comparaison des performances** :

| Fonctionnement | Predis | phpredis | Amélioration |
|-----------|--------|----------|-------------|
| GET du cache | 1-5ms | 0,5 à 2 ms | 2 à 3 fois plus rapide |
| Cache SET | 2-6 ms | 0,8 à 2,5 ms | 2 à 3 fois plus rapide |
| Opérations de balisage | 10-30ms | 3 à 10 ms | 3 à 4 fois plus rapide |

### Connexions persistantes

Les connexions persistantes réutilisent les connexions Redis existantes entre les requêtes, ce qui accélère les opérations de mise en cache de 5 à 15 %. Configurez dans `app/etc/env.php` :

```php
'cache' => [
    'frontend' => [
        'default' => [
            'backend_options' => [
                'server' => 'redis',
                'database' => '0',
                'port' => '6379',
                'persistent' => '1',
                'persistent_id' => 'cache_default',
                'timeout' => '2.5',
                'read_timeout' => '2.0',
            ]
        ],
        'page_cache' => [
            'backend_options' => [
                'server' => 'redis',
                'database' => '1',
                'port' => '6379',
                'persistent' => '1',
                'persistent_id' => 'cache_fpc',
            ]
        ]
    ]
]
```

>[!IMPORTANT]
>
>Utilisez un `persistent_id` unique pour chaque type de cache afin d’éviter les conflits de connexion.

### Configuration optimisée complète

Voici une configuration Symfony prête pour la production combinant toutes les optimisations de performances :

```php
'cache' => [
    'frontend' => [
        'default' => [
            'id_prefix' => 'b0b_',
            'backend' => 'redis',
            'backend_options' => [
                'server' => 'redis',
                'database' => '0',
                'port' => '6379',
                'serializer' => 'igbinary',
                'compress_data' => '1',
                'compression_lib' => 'gzip',
                'persistent' => '1',
                'persistent_id' => 'cache_default',
                'timeout' => '2.5',
                'read_timeout' => '2.0',
                'use_lua' => '1',
                'use_lua_on_gc' => '1',
                'preload_keys' => [
                    'b0b_EAV_ENTITY_TYPES',
                    'b0b_GLOBAL_PLUGIN_LIST',
                    'b0b_DB_IS_UP_TO_DATE',
                    'b0b_SYSTEM_DEFAULT',
                ],
            ]
        ],
        'page_cache' => [
            'id_prefix' => 'b0b_',
            'backend' => 'redis',
            'backend_options' => [
                'server' => 'redis',
                'database' => '1',
                'port' => '6379',
                'serializer' => 'igbinary',
                'compress_data' => '0',
                'persistent' => '1',
                'persistent_id' => 'cache_fpc',
            ]
        ]
    ],
    'allow_parallel_generation' => false
]
```

## Vérifier la connexion Redis

Pour vérifier que Redis et Commerce fonctionnent correctement ensemble :

1. Connectez-vous au serveur qui exécute Redis et Commerce.
1. Ouvrez un terminal.
1. Vérifiez la connexion à l’aide de la commande `redis-cli monitor` ou de la commande `redis-cli ping`.

Si les commandes réussissent, Redis est en cours d’exécution et peut communiquer avec l’application Commerce. S’ils échouent, il existe un problème de connexion entre Redis et Commerce que vous devez résoudre.

### Commande Redis monitor

```shell
redis-cli monitor
```

Exemple de sortie de mise en cache de page :

```text
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
...
```

Si les deux commandes réussissent, Redis est correctement configuré.

### Inspecter des données compressées

Pour examiner les données de session compressées et le cache de page, utilisez l’outil [RESP.app](https://flathub.org/apps/details/app.resp.RESP). Il prend en charge la décompression automatique des données de session et de cache de page de Commerce 2 et affiche les données de session PHP sous une forme lisible par l&#39;utilisateur.
