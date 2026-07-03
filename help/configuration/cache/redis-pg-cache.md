---
title: Configuration de Redis pour le cache de page et par défaut
description: Découvrez comment configurer Redis en tant que serveur principal par défaut et du cache de page pour Adobe Commerce. Découvrez les commandes de l’interface de ligne de commande, les paramètres env.php et la vérification de la connexion.
feature: Configuration, Cache
exl-id: 8c097cfc-85d0-4e96-b56e-284fde40d459
badgePaas: label="Sur Site" type="Informative" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="S’applique uniquement aux projets sur site Adobe Commerce."
autotag-review: '2026-06-22T21:55:53.227Z'
TQID: 'https://experienceleague.adobe.com/2KjWE19ud32PUdvJQWNWkK338ysaa5vt0mA4EyyP66I'
product_v2:
  - id: b974b164-8a4e-43b8-a9e2-8e67ec131677
  - id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2:
  - id: ba9e5be9-7de1-4f71-a5d2-baead0e425ee
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
  - id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
source-git-commit: 7171e5abfad69ad0f2d3f4c4b5eb57c13d07feb4
workflow-type: tm+mt
source-wordcount: 1261
ht-degree: 0%

---

# Configuration de Redis pour le cache de page et par défaut

{{cloud-cache-config}}

Commerce fournit des options de ligne de commande pour configurer la page Redis et la mise en cache par défaut. Bien que vous puissiez configurer la mise en cache en modifiant le fichier `<Commerce-install-dir>app/etc/env.php`, il est recommandé d’utiliser la ligne de commande, en particulier pour les configurations initiales. La ligne de commande permet de valider en s’assurant que la configuration est correcte sur le plan syntaxique.

**Prérequis :**

[Installez Redis](config-redis.md#install-redis) avant de continuer.

>[!NOTE]
>
>Pour les instances Commerce hébergées sur EC2, vous pouvez utiliser AWS ElastiCache au lieu d’une instance Redis locale. Voir [Configuration d’Elasticache pour les instances EC2](redis-elasticache-for-ec2.md).

## Reprise des implémentations du cache

Adobe Commerce a utilisé les implémentations principales de cache Redis suivantes :

- **Serveur principal Redis hérité** (`Cm_Cache_Backend_Redis`) : mise en œuvre obsolète utilisée dans les anciennes configurations Redis.
- **Serveur principal Redis** (`Magento\Framework\Cache\Backend\Redis`) : serveur principal utilisé par la configuration de ligne de commande dans cette rubrique pour le cache par défaut et de page.
- **Serveur principal du cache L2** (`Magento\Framework\Cache\Backend\RemoteSynchronizedCache`) : implémentation du cache à deux niveaux qui utilise Redis comme serveur principal distant et le stockage du cache de fichiers local pour synchroniser les données du cache entre les nœuds. Voir [Configuration du cache à deux niveaux](level-two-cache.md).

## Configurer la mise en cache par défaut de Redis

Exécutez la commande `setup:config:set` et spécifiez les paramètres spécifiques à la mise en cache par défaut de Redis.

```shell
bin/magento setup:config:set --cache-backend=redis --cache-backend-redis-<parameter>=<value>...
```

Les paramètres courants sont les suivants :

- `--cache-backend=redis` active la mise en cache par défaut de Redis. Si cette fonctionnalité a déjà été activée, omettez ce paramètre.

- `--cache-backend-redis-<parameter>=<value>` une liste de paires clé-valeur qui configurent la mise en cache par défaut :

| Paramètre de ligne de commande | Valeur | Signification | Valeur par défaut |
| --- | --- | --- | --- |
| `cache-backend-redis-server` | serveur | Nom d’hôte complet, adresse IP ou chemin d’accès absolu à un socket UNIX. La valeur par défaut 127.0.0.1 indique que Redis est installé sur le serveur Commerce. | `127.0.0.1` |
| `cache-backend-redis-port` | port | Port d’écoute du serveur Redis | `6379` |
| `cache-backend-redis-db` | de données | Obligatoire si vous utilisez Redis pour le cache par défaut et le cache de page complète. Indiquez le numéro de base de données de l’un des caches ; l’autre cache utilise 0 par défaut.<br><br>**Important** : si vous utilisez Redis pour plusieurs types de mise en cache, les numéros de base de données doivent être différents. Il est recommandé d&#39;attribuer le numéro de base de données de mise en cache par défaut à 0, le numéro de base de données de mise en cache de page à 1 et le numéro de base de données de stockage de session à 2. | `0` |
| `cache-backend-redis-password` | mot de passe | La configuration d’un mot de passe Redis active l’une de ses fonctionnalités de sécurité intégrées : la commande `auth`, qui nécessite que les clients s’authentifient pour accéder à la base de données. Le mot de passe est configuré directement dans le fichier de configuration de Redis : `/etc/redis/redis.conf` | |
| `cache-backend-redis-compress-data` | compress_data | Définissez sur `0` pour désactiver la compression. | `1` |
| `cache-backend-redis-compression-lib` | compression_lib | Bibliothèque de compression à utiliser. Les valeurs prises en charge sont `snappy`, `lzf`, `l4z`, `zstd` et `gzip`. Laisser vide pour déterminer automatiquement. | |
| `cache-backend-redis-use-lua` | use_lua | Activez ou désactivez les scripts Lua pour toutes les opérations Redis. <br><br>**Valeur par défaut : conserver à `0`.** Le mode Lua est désactivé par défaut pour éviter les régressions de performances connues et les problèmes d’échec de cache GraphQL introduits par la bibliothèque Redis groupée (1.17.x) lorsque Lua a été activé. | `0` |
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

Les paramètres courants sont les suivants :

- `--page-cache=redis` active la mise en cache de page Redis. Si cette fonctionnalité a déjà été activée, omettez ce paramètre.

- `--page-cache-redis-<parameter>=<value>` une liste de paires clé-valeur qui configurent la mise en cache de page :

| Paramètre de ligne de commande | Valeur | Signification | Valeur par défaut |
| --- | --- | --- | --- |
| `page-cache-redis-server` | serveur | Nom d’hôte complet, adresse IP ou chemin d’accès absolu à un socket UNIX. La valeur par défaut 127.0.0.1 indique que Redis est installé sur le serveur Commerce. | `127.0.0.1` |
| `page-cache-redis-port` | port | Port d’écoute du serveur Redis | `6379` |
| `page-cache-redis-db` | de données | Obligatoire si vous utilisez Redis pour le cache de page par défaut et le cache de page complet. Indiquez le numéro de base de données de l’un des caches ; l’autre cache utilise 0 par défaut.<br/>**Important** : si vous utilisez Redis pour plusieurs types de mise en cache, les numéros de base de données doivent être différents. Il est recommandé d&#39;attribuer le numéro de base de données de mise en cache par défaut à 0, le numéro de base de données de mise en cache de page à 1 et le numéro de base de données de stockage de session à 2. | `0` |
| `page-cache-redis-password` | mot de passe | La configuration d’un mot de passe Redis active l’une de ses fonctionnalités de sécurité intégrées : la commande `auth`, qui nécessite que les clients s’authentifient pour accéder à la base de données. Configurez le mot de passe dans le fichier de configuration Redis : `/etc/redis/redis.conf` | |
| `page-cache-redis-compress-data` | compress_data | Définissez cette valeur sur `1` pour compresser le cache pleine page. Utilisez `0` pour désactiver la compression. | `0` |
| `page-cache-redis-compression-lib` | compression_lib | Bibliothèque de compression à utiliser. Les valeurs prises en charge sont `snappy`, `lzf`, `l4z`, `zstd` et `gzip`. Laisser vide pour déterminer automatiquement. | |

L&#39;exemple suivant active la mise en cache de page Redis, définit l&#39;hôte sur `127.0.0.1` et affecte le numéro de base de données à `1`. Tous les autres paramètres sont définis sur la valeur par défaut.

```shell
bin/magento setup:config:set --page-cache=redis --page-cache-redis-server=127.0.0.1 --page-cache-redis-db=1
```

{{valkey-redis-cli-note}}

### Vérification de la configuration de l’environnement Commerce

L’exécution des commandes pour configurer la mise en cache Redis met à jour la configuration de l’environnement Commerce (`<Commerce-install-dir>app/etc/env.php`) :

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

## Configurer des options de mise en cache supplémentaires

### Fonction de préchargement Redis

Comme Commerce stocke les données de configuration dans le cache Redis, vous pouvez précharger les données réutilisées entre les pages. Pour rechercher les clés qui doivent être préchargées, analysez les données transférées de Redis vers Commerce. Adobe suggère de précharger les données chargées sur chaque page, telles que `SYSTEM_DEFAULT`, `EAV_ENTITY_TYPES` et `DB_IS_UP_TO_DATE`.

Redis utilise le `pipeline` pour les requêtes de chargement composites. Les clés doivent inclure le préfixe de la base de données. Par exemple, si le préfixe de la base de données est `061_`, la clé de préchargement ressemble à ceci : `061_SYSTEM_DEFAULT`

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

### Extension PHP Redis

Utilisez l&#39;extension native PHP Redis (`phpredis`) lorsque votre environnement la supporte :

#### Utilisation d’apt

Pour Debian ou Ubuntu, utilisez `apt` :

```bash
sudo apt-get install php-redis
sudo systemctl restart php-fpm
php -m | grep redis
```

#### Utiliser pecl

Vous pouvez également utiliser `pecl` :

```bash
sudo pecl install redis
echo "extension=redis.so" | sudo tee /etc/php/<version>/mods-available/redis.ini
sudo phpenmod redis
sudo systemctl restart php-fpm
php -m | grep redis
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
