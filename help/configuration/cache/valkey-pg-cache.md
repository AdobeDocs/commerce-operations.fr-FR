---
title: Configurer la clé de valeur pour le cache de page et par défaut
description: Découvrez comment configurer Valkey comme serveur principal par défaut et du cache de page pour Adobe Commerce. Découvrez les commandes de l’interface de ligne de commande, les paramètres env.php et la vérification de la connexion.
feature: Configuration, Cache
exl-id: d0baa2a6-8aa8-4f3f-9edf-102d621430e0
badgePaas: label="Sur Site" type="Informative" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="S’applique uniquement aux projets sur site Adobe Commerce."
autotag-review: '2026-06-22T22:00:55.389Z'
TQID: 'https://experienceleague.adobe.com/AjJ86dYGRVFuY1T73ct1Gpcf6iDbb4ewP8OiGX8otQs'
product_v2: id: b974b164-8a4e-43b8-a9e2-8e67ec131677id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2: id: ba9e5be9-7de1-4f71-a5d2-baead0e425eeid: dac87252-6066-4d6e-a9d2-f6d84c323de7
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2: id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2: id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87cid: cdd65e7e-8839-44a2-bc21-0e03623b5dd1id: d095671a-1355-40aa-8b5f-06c33c68080b
source-git-commit: ab2a9ef6d4c3ed692f4a6a66323ab5e3d5c6673a
workflow-type: tm+mt
source-wordcount: 1281
ht-degree: 0%

---


# Configuration de Valkey pour le cache de page et par défaut

Commerce fournit des options de ligne de commande pour configurer la valeur par défaut de Valkey et la mise en cache des pages. Bien que vous puissiez configurer la mise en cache en modifiant le fichier `<Commerce-install-dir>app/etc/env.php`, il est recommandé d’utiliser la ligne de commande, en particulier pour les configurations initiales. La ligne de commande permet de valider en s’assurant que la configuration est correcte sur le plan syntaxique.

{{cloud-cache-config}}

**Prérequis :**

[Installez Valkey](config-valkey.md#install-valkey) avant de continuer.

## Structures prises en charge

>[!BEGINTABS]

>[!TAB Zend Cache (2.4.8 et versions antérieures)]

- **Zend Cache (2.4.8 et versions antérieures)** — Serveur principal Valkey hérité pour Commerce 2.4.8 et versions antérieures :
   - **Serveur principal Valkey hérité** — Utilise le chemin de classe complet (`Magento\Framework\Cache\Backend\Valkey`)
   - **Précharger les clés** — Prend en charge le préchargement des clés de cache fréquemment utilisées
   - **Scripts Lua** — Lua pour la récupération de l&#39;espace mémoire
   - **Compression** — Prend en charge la compression des données

>[!TAB Cache Symfony (2.4.9+)]

- **Symfony Cache (2.4.9+)** — À partir de Commerce 2.4.9, Symfony Cache fournit une mise en cache moderne, conforme à la norme PSR-6, pour Valkey, avec des améliorations de performances significatives :
   - **Pipeline Valkey automatique** — Regroupe plusieurs opérations en une seule demande, ce qui réduit la latence
   - **PSR-6 TagAwareAdapter** — Invalidation efficace du cache basé sur les balises avec des opérations atomiques
   - **Sérialisation igbinary** — La sérialisation binaire réduit la taille de l&#39;entrée du cache de 45 % et améliore la vitesse de 5 à 10 %
   - **Connexions persistantes améliorées** — Pool de connexions plus stable avec une meilleure gestion des processus dupliqués
   - **Scripts Lua optimisés** : exécution côté serveur combinée à la création de pipelines pour une efficacité maximale

>[!ENDTABS]

## Configurer la mise en cache par défaut de Valkey

Exécutez la commande `setup:config:set` et spécifiez les paramètres de mise en cache par défaut de Valkey.

```shell
bin/magento setup:config:set --cache-backend=valkey --cache-backend-valkey-<parameter>=<value>...
```

- `--cache-backend=valkey` active la mise en cache par défaut de Valkey. Si cette fonctionnalité a déjà été activée, omettez ce paramètre.

- `--cache-backend-valkey-<parameter>=<value>` une liste de paires clé-valeur qui configurent la mise en cache par défaut :

{{valkey-redis-cli-note}}

| Paramètre de ligne de commande | Valeur | Signification | Valeur par défaut |
|---------------------------------| --------- |--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------| ------------- |
| `cache-backend-valkey-server` | serveur | Nom d’hôte complet, adresse IP ou chemin d’accès absolu à un socket UNIX. La valeur par défaut `127.0.0.1` indique que Valkey est installé sur le serveur Commerce. | `127.0.0.1` |
| `cache-backend-valkey-port` | port | Port d’écoute du serveur Valkey | `6379` |
| `cache-backend-valkey-db` | de données | Obligatoire si vous utilisez Valkey pour le cache par défaut et le cache de page complète. Spécifiez le numéro de base de données de l’un des caches ; l’autre cache utilise `0` par défaut.<br><br>**Important** : si vous utilisez Valkey pour plusieurs types de mise en cache, les numéros de base de données doivent être différents. Adobe recommande d’attribuer le numéro de base de données de mise en cache par défaut à `0`, le numéro de base de données de mise en cache de page à `1` et le numéro de base de données de stockage de session à `2`. | `0` |
| `cache-backend-valkey-password` | mot de passe | La configuration d’un mot de passe Valkey active l’une de ses fonctionnalités de sécurité intégrées : la commande `auth`, qui nécessite que les clients s’authentifient pour accéder à la base de données. Le mot de passe est configuré directement dans le fichier de configuration de Valkey : `/etc/valkey/valkey.conf` | |
| `cache-backend-valkey-use-lua` | use_lua | Activez ou désactivez LUA. <br><br>**LUA** : Lua nous permet d’exécuter une partie de la logique d’application dans Valkey, ce qui améliore les performances et garantit la cohérence des données grâce à son exécution atomique. | `0` |
| `cache-backend-valkey-use-lua-on-gc` | use_lua_on_gc | Activez ou désactivez LUA pour le nettoyage. <br><br>**LUA** : Lua nous permet d’exécuter une partie de la logique d’application dans Valkey, ce qui améliore les performances et garantit la cohérence des données grâce à son exécution atomique. | `1` |

## Exemple de commande (cache par défaut)

L&#39;exemple suivant active la mise en cache par défaut de Valkey, définit l&#39;hôte sur `127.0.0.1` et affecte le numéro de base de données à `0`. Valkey utilise les valeurs par défaut pour tous les autres paramètres.

```shell
bin/magento setup:config:set --cache-backend=valkey --cache-backend-valkey-server=127.0.0.1 --cache-backend-valkey-db=0
```

{{valkey-redis-cli-note}}

## Configuration de la mise en cache des pages Clé

Pour configurer la mise en cache des pages Valkey sur Commerce, exécutez la commande `setup:config:set` avec des paramètres supplémentaires.

```shell
bin/magento setup:config:set --page-cache=valkey --page-cache-valkey-<parameter>=<value>...
```

Avec les paramètres suivants :

- `--page-cache=valkey` active la mise en cache de page Valkey. Si cette fonctionnalité a déjà été activée, omettez ce paramètre.

- `--page-cache-valkey-<parameter>=<value>` une liste de paires clé-valeur qui configurent la mise en cache de page :

| Paramètre de ligne de commande | Valeur | Signification | Valeur par défaut |
|----------------------------------------| --------- |---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------| ------------- |
| `page-cache-valkey-server` | serveur | Nom d’hôte complet, adresse IP ou chemin d’accès absolu à un socket UNIX. La valeur par défaut `127.0.0.1` indique que Valkey est installé sur le serveur Commerce. | `127.0.0.1` |
| `page-cache-valkey-port` | port | Port d&#39;écoute du serveur Valkey. | `6379` |
| `page-cache-valkey-db` | de données | Obligatoire si vous utilisez Valkey pour le cache par défaut et le cache de page entière. Spécifiez le numéro de base de données de l’un des caches ; l’autre cache utilise `0` par défaut.<br/>**Important** : si vous utilisez Valkey pour plusieurs types de mise en cache, les numéros de base de données doivent être différents. Il est recommandé d’attribuer le numéro de base de données de mise en cache par défaut à `0`, le numéro de base de données de mise en cache de page à `1` et le numéro de base de données de stockage de session à `2`. | `0` |
| `page-cache-valkey-password` | mot de passe | La configuration d’un mot de passe Valkey active l’une de ses fonctionnalités de sécurité intégrées : la commande `auth`, qui nécessite que les clients s’authentifient pour accéder à la base de données. Configurez le mot de passe dans le fichier de configuration Valkey : `/etc/valkey/valkey.conf` | |

### Exemple de commande (cache de page)

L&#39;exemple suivant active la mise en cache de page Valkey, définit l&#39;hôte sur `127.0.0.1` et affecte le numéro de base de données à `1`. Tous les autres paramètres sont définis sur la valeur par défaut.

```shell
bin/magento setup:config:set --page-cache=valkey --page-cache-valkey-server=127.0.0.1 --page-cache-valkey-db=1
```

{{valkey-redis-cli-note}}

### Vérification de la configuration de l’environnement Commerce

L’exécution des commandes pour configurer la mise en cache de Valkey met à jour la configuration de l’environnement Commerce (`<Commerce-install-dir>app/etc/env.php`) :

>[!BEGINTABS]

>[!TAB Zend Cache (2.4.8 et versions antérieures)]

```php
'cache' => [
    'frontend' => [
        'default' => [
            'backend' => 'Magento\\Framework\\Cache\\Backend\\Valkey',
            'backend_options' => [
                'server' => '127.0.0.1',
                'database' => '0',
                'port' => '6379'
            ],
        ],
        'page_cache' => [
            'backend' => 'Magento\\Framework\\Cache\\Backend\\Valkey',
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
            'backend' => 'valkey',
            'backend_options' => [
                'server' => '127.0.0.1',
                'database' => '0',
                'port' => '6379'
            ],
        ],
        'page_cache' => [
            'backend' => 'valkey',
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
>À partir de la version 2.4.9 de Commerce, utilisez le type de serveur principal simplifié `'backend' => 'valkey'` au lieu du chemin d’accès de classe complet. Symfony Cache est automatiquement utilisé lorsque le nom simplifié est spécifié.

>[!ENDTABS]

## Configurer des options de mise en cache supplémentaires

### Fonction de préchargement Valkey

Comme Commerce stocke les données de configuration dans le cache Valkey, vous pouvez précharger les données réutilisées entre les pages. Pour rechercher les clés qui doivent être préchargées, analysez les données transférées de Valkey vers Commerce. Adobe suggère de précharger les données chargées sur chaque page, telles que `SYSTEM_DEFAULT`, `EAV_ENTITY_TYPES` et `DB_IS_UP_TO_DATE`.

Valkey utilise le `pipeline` pour les requêtes de chargement composites. Les clés doivent inclure le préfixe de la base de données. Par exemple, si le préfixe de la base de données est `061_`, la clé de préchargement ressemble à ceci : `061_SYSTEM_DEFAULT`

>[!BEGINTABS]

>[!TAB Envoyer le cache]

```php
'cache' => [
    'frontend' => [
        'default' => [
            'id_prefix' => '061_',
            'backend' => 'Magento\\Framework\\Cache\\Backend\\Valkey',
            'backend_options' => [
                'server' => 'valkey',
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
            'backend' => 'valkey',
            'backend_options' => [
                'server' => 'valkey',
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
                'backend' => 'Magento\\Framework\\Cache\\Backend\\Valkey',
                'backend_options' => [
                    'server' => 'valkey',
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
                'backend' => 'valkey',
                'backend_options' => [
                    'server' => 'valkey',
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
                'server' => 'valkey',
                'database' => '0',
                'port' => '6379',
                'serializer' => 'igbinary',  // Enable Igbinary serialization
            ]
        ],
        'page_cache' => [
            'backend_options' => [
                'server' => 'valkey',
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
| Cache GET | 1-5ms | 0,5 à 2 ms | 2 à 3 fois plus rapide |
| Cache SET | 2-6 ms | 0,8 à 2,5 ms | 2 à 3 fois plus rapide |
| Opérations de balisage | 10-30ms | 3 à 10 ms | 3 à 4 fois plus rapide |

### Connexions persistantes

Les connexions persistantes réutilisent les connexions Valkey existantes entre les requêtes, ce qui accélère les opérations de mise en cache de 5 à 15 %. Configurez dans `app/etc/env.php` :

```php
'cache' => [
    'frontend' => [
        'default' => [
            'backend_options' => [
                'server' => 'valkey',
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
                'server' => 'valkey',
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

Voici une configuration prête pour la production combinant toutes les optimisations de performances :

```php
'cache' => [
    'frontend' => [
        'default' => [
            'id_prefix' => 'b0b_',
            'backend' => 'valkey',
            'backend_options' => [
                'server' => 'valkey',
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
            'backend' => 'valkey',
            'backend_options' => [
                'server' => 'valkey',
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

## Vérifier la connexion Valkey

Pour vérifier que Valkey et Commerce fonctionnent correctement ensemble :

1. Connectez-vous au serveur qui exécute Valkey et Commerce.
1. Ouvrez un terminal.
1. Vérifiez la connexion à l’aide de la commande `valkey-cli monitor` ou de la commande `valkey-cli ping`.

Si les commandes réussissent, alors Valkey est en cours d’exécution et peut communiquer avec l’application Commerce. En cas d’échec, il existe un problème de connexion entre Valkey et Commerce que vous devez résoudre.

### Commande de moniteur Valkey

```shell
valkey-cli monitor
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
1476826133.883312 [0 127.0.0.1:52369] "hget" "zc:k:ea6_GLOBAL__EVENT_CONFIG_CACHE" "d"
1476826133.898431 [0 127.0.0.1:52369] "hget" "zc:k:ea6_DB_PDO_MYSQL_DDL_STAGING_UPDATE_1" "d"
1476826133.898794 [0 127.0.0.1:52369] "hget" "zc:k:ea6_RESOLVED_STORES_D1BEFA03C79CA0B84ECC488DEA96BC68" "d"
1476826133.905738 [0 127.0.0.1:52369] "hget" "zc:k:ea6_DEFAULT_CONFIG_CACHE_STORE_DEFAULT_10__235__32__1080MAGENTO2" "d"

... more ...

1476826210.634998 [0 127.0.0.1:52439] "hmset" "zc:k:ea6_MVIEW_CONFIG" "d" "a:18:{s:19:\"design_config_dummy\";a:4:{s:7:\"view_id\";s:19:\"design_config_dummy\";s:12:\"action_class\";s:39:\"Magento\\Theme\\Model\\Indexer\\Mview\\Dummy\";s:5:\"group\";s:7:\"indexer\";s:13:\"subscriptions\";a:0:{}}s:14:\"customer_dummy\";a:4:{s:7:\"view_id\";s:14:\"customer_dummy\";s:12:\"action_class\";s:42:\"Magento\\Customer\\Model\\Indexer\\Mview\\Dummy\";s:5:\"group\";s:7:\"indexer\";s:13:\"subscriptions\";a:0:{}}s:13:\"cms_page_grid\";a:4:{s:7:\"view_id\";s:13:\"cms_page_grid\";s:12:\"action_class\";s:43:\"Magento\\Catalog\\Model\\Indexer\\Category\\Flat\";s:5:\"group\";s:7:\"indexer\";s:13:\"subscriptions\";a:1:{s:8:\"cms_page\";a:3:{s:4:\"name\";s:8:\"cms_page\";s:6:\"column\";s:7:\"page_id\";s:18:\"subscription_model\";N;}}}s:21:\"catalog_category_flat\";a:4:{s:7:\"view_id\";s:21:\"catalog_category_flat\";s:12:\"action_class\";s:43:\"Magento\\Catalog\\Model\\Indexer\\Category\\Flat\";s:5:\"group\";s:7:\"indexer\";s:13:\"subscriptions\";a:6:{s:23:\"catalog_category_entity\";a:3:{s:4:\"name\";s:23:\"catalog_category_entity\";s:6:\"column\";s:9:\"entity_id\";s:18:\"subscription_model\";N;}s:31:\"catalog_category_entity_decimal\";a:3:{s:4:\"name\";s:31:\"catalog_category_entity_decimal\";s:6:\"column\";s:9:\"entity_id\";s:18:\"subscription_model\";s:71:\"Magento\\CatalogStaging\\Model\\Mview\\View\\Category\\Attribute\\Subscription\";}s:27:\"catalog_category_entity_int\";a:3:{s:4:\"name\";s:27:\"catalog_category_entity_int\";s:6:\"column\";s:9:\"entity_id\";s:18:\"subscription_model\";s:71:\"Magento\\CatalogStaging\\Model\\Mview\\View\\Category\\Attribute\\Subscription\";}s:28:\"catalog_category_entity_text\";a:3:{s:4:\"name\";s:28:\"catalog_category_entity_text\";s:6:\"column\";s:9:\"entity_id\";s:18:\"subscription_model\";s:71:\"Magento\\CatalogStaging\\Model\\Mview\\View\\Category\\Attribute\\Subscription\";}s:31:\"catalog_category_entity_varchar\";a:3:{s:4:\"name\";s:31:\"catalog_category_entity_varchar\";s:6:\"column\";s:9:\"entity_id\";s:18:\"subscription_model\";s:71:\"Magento\\CatalogStaging\\Model\\Mview\\View\\Category\\Attribute\\Subscription\";}s:32:\"catalog_category_entity_datetime\";a:3:{s:4:\"name\";s:32:\"catalog_category_entity_datetime\";s:6:\"column\";s:9:\"entity_id\";s:18:\"subscription_model\";s:71:\"Magento\\CatalogStaging\\Model\\Mview\\View\\Category\\Attribute\\Subscription\";}}}s:24:\"catalog_category_product\";a:4:{s:7:\"view_id\";s:24:\"catalog_category_product\";s:12:\"action_class\";s:46:\"Magento\\Catalog\\Model\\Indexer\\Category\\Product\";s:5:\"group\";s:7:\"indexer\";s:13:\"subscriptions\";a:2:{s:23:\"catalog_category_entity\";a:3:{s:4:\"name\";s:23:\"catalog_category_entity\";s:6:\"column\"

... more ...
```

### Commande ping Valkey

```shell
valkey-cli ping
```

La réponse attendue est : `PONG`

Si les deux commandes ont réussi, Valkey est correctement configuré.

### Inspecter des données compressées

Pour examiner les données de session compressées et le cache de page, utilisez l’outil [RESP.app](https://flathub.org/apps/app.resp.RESP). Il prend en charge la décompression automatique des données de session Commerce 2 et du cache de page et affiche les données de session PHP dans un format lisible par l&#39;utilisateur.

