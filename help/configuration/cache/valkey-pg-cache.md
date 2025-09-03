---
title: Utiliser Valkey pour le cache par défaut
description: Découvrez comment configurer Valkey en tant que cache par défaut pour Adobe Commerce.
feature: Configuration, Cache
exl-id: d0baa2a6-8aa8-4f3f-9edf-102d621430e0
source-git-commit: dea0ad57a8c4525be9bc442708bdd2495f28d72d
workflow-type: tm+mt
source-wordcount: '1047'
ht-degree: 0%

---


# Utiliser Valkey pour le cache par défaut

Commerce fournit des options de ligne de commande pour configurer la page Valkey et la mise en cache par défaut. Bien que vous puissiez configurer la mise en cache en modifiant le fichier `<Commerce-install-dir>app/etc/env.php`, il est recommandé d’utiliser la ligne de commande, en particulier pour les configurations initiales. La ligne de commande permet de valider en s’assurant que la configuration est correcte sur le plan syntaxique.

Vous devez [installer Valkey](config-redis.md#install-redis) avant de continuer.

## Configurer la mise en cache par défaut de Valkey

Exécutez la commande `setup:config:set` et spécifiez les paramètres de mise en cache par défaut de Valkey.

```bash
bin/magento setup:config:set --cache-backend=valkey --cache-backend-valkey-<parameter>=<value>...
```

- `--cache-backend=valkey` active la mise en cache par défaut de valkey. Si cette fonctionnalité a déjà été activée, omettez ce paramètre.

- `--cache-backend-valkey-<parameter>=<value>` une liste de paires clé-valeur qui configurent la mise en cache par défaut :

>[!NOTE]
>
>À partir de **Adobe Commerce 2.4.9-alpha2**, **Valkey** a officiellement remplacé Redis dans l’outil d’interface de ligne de commande en raison de changements dans les licences. Valkey est une fourchette de Redis et conserve des fonctionnalités quasi identiques. Pour les **versions 2.4.8 et antérieures**, les commandes d’interface de ligne de commande utilisées pour configurer Valkey restent identiques à celles de Redis, assurant ainsi une rétrocompatibilité transparente et simplifiant la migration ou la prise en charge de deux environnements. L’exemple suivant illustre la commande spécifique à Valkey.

```bash
bin/magento setup:config:set --cache-backend=redis --cache-backend-valkey-<parameter>=<value>...
```

| Paramètre de ligne de commande | Valeur | Signification | Valeur par défaut |
|---------------------------------| --------- |--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------| ------------- |
| `cache-backend-valkey-server` | serveur | Nom d’hôte complet, adresse IP ou chemin d’accès absolu à un socket UNIX. La valeur par défaut `127.0.0.1` indique que Valkey est installé sur le serveur Commerce. | `127.0.0.1` |
| `cache-backend-valkey-port` | port | Port d’écoute du serveur Valkey | `6379` |
| `cache-backend-valkey-db` | de données | Obligatoire si vous utilisez Valkey pour le cache par défaut et le cache de page complète. Vous devez indiquer le numéro de base de données de l’un des caches ; l’autre cache utilise `0` par défaut.<br><br>**Important** : si vous utilisez Valkey pour plusieurs types de mise en cache, les numéros de base de données doivent être différents. Adobe recommande d’attribuer le numéro de base de données de mise en cache par défaut à `0`, le numéro de base de données de mise en cache de page à `1` et le numéro de base de données de stockage de session à `2`. | `0` |
| `cache-backend-valkey-password` | mot de passe | La configuration d’un mot de passe Valkey active l’une de ses fonctionnalités de sécurité intégrées : la commande `auth`, qui nécessite que les clients s’authentifient pour accéder à la base de données. Le mot de passe est configuré directement dans le fichier de configuration de Valkey : `/etc/valkey/valkey.conf` | |

### Exemple de commande

L&#39;exemple suivant active la mise en cache par défaut de Valkey, définit l&#39;hôte sur `127.0.0.1` et affecte le numéro de base de données à `0`. Valkey utilise les valeurs par défaut pour tous les autres paramètres.

```bash
bin/magento setup:config:set --cache-backend=valkey --cache-backend-valkey-server=127.0.0.1 --cache-backend-valkey-db=0
```

>[!NOTE]
>
>À partir de **Adobe Commerce 2.4.9-alpha2**, **Valkey** a officiellement remplacé Redis dans l’outil d’interface de ligne de commande en raison de changements dans les licences. Valkey est une fourchette de Redis et conserve des fonctionnalités quasi identiques. Pour les **versions 2.4.8 et antérieures**, les commandes d’interface de ligne de commande utilisées pour configurer Valkey restent identiques à celles de Redis, assurant ainsi une rétrocompatibilité transparente et simplifiant la migration ou la prise en charge de deux environnements. L’exemple suivant illustre la commande spécifique à Valkey.

```bash
bin/magento setup:config:set --cache-backend=redis --cache-backend-redis-server=127.0.0.1 --cache-backend-redis-db=0
```

## Configuration de la mise en cache de pages

Pour configurer la mise en cache des pages Valkey sur Commerce, exécutez la commande `setup:config:set` avec des paramètres supplémentaires.

```bash
bin/magento setup:config:set --page-cache=valkey --page-cache-valkey-<parameter>=<value>...
```

Avec les paramètres suivants :

- `--page-cache=valkey` active la mise en cache de page Valkey. Si cette fonctionnalité a déjà été activée, omettez ce paramètre.

- `--page-cache-valkey-<parameter>=<value>` une liste de paires clé-valeur qui configurent la mise en cache de page :

>[!NOTE]
>
>À partir de **Adobe Commerce 2.4.9-alpha2**, **Valkey** a officiellement remplacé Redis dans l’outil d’interface de ligne de commande en raison de changements dans les licences. Valkey est une fourchette de Redis et conserve des fonctionnalités quasi identiques. Pour les **versions 2.4.8 et antérieures**, les commandes d’interface de ligne de commande utilisées pour configurer Valkey restent identiques à celles de Redis, assurant ainsi une rétrocompatibilité transparente et simplifiant la migration ou la prise en charge de deux environnements. L’exemple suivant illustre la commande spécifique à Valkey.

```bash
bin/magento setup:config:set --page-cache=redis --page-cache-redis-<parameter>=<value>...
```

| Paramètre de ligne de commande | Valeur | Signification | Valeur par défaut |
|------------------------------| --------- |-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------| ------------- |
| `page-cache-valkey-server` | serveur | Nom d’hôte complet, adresse IP ou chemin d’accès absolu à un socket UNIX. La valeur par défaut `127.0.0.1` indique que Valkey est installé sur le serveur Commerce. | `127.0.0.1` |
| `page-cache-valkey-port` | port | Port d&#39;écoute du serveur Valkey. | `6379` |
| `page-cache-valkey-db` | de données | Obligatoire si vous utilisez Valkey pour le cache par défaut et le cache de page entière. Vous devez indiquer le numéro de base de données de l’un des caches ; l’autre cache utilise `0` par défaut.<br/>**Important** : si vous utilisez Valkey pour plusieurs types de mise en cache, les numéros de base de données doivent être différents. Il est recommandé d’attribuer le numéro de base de données de mise en cache par défaut à `0`, le numéro de base de données de mise en cache de page à `1` et le numéro de base de données de stockage de session à `2`. | `0` |
| `page-cache-valkey-password` | mot de passe | La configuration d’un mot de passe Valkey active l’une de ses fonctionnalités de sécurité intégrées : la commande `auth`, qui nécessite que les clients s’authentifient pour accéder à la base de données. Configurez le mot de passe dans le fichier de configuration Valkey : `/etc/valkey/valkey.conf` | |

### Exemple de commande

L&#39;exemple suivant active la mise en cache de page Valkey, définit l&#39;hôte sur `127.0.0.1` et affecte le numéro de base de données à `1`. Tous les autres paramètres sont définis sur la valeur par défaut.

```bash
bin/magento setup:config:set --page-cache=valkey --page-cache-valkey-server=127.0.0.1 --page-cache-valkey-db=1
```

>[!NOTE]
>
>À partir de **Adobe Commerce 2.4.9-alpha2**, **Valkey** a officiellement remplacé Redis dans l’outil d’interface de ligne de commande en raison de changements dans les licences. Valkey est une fourchette de Redis et conserve des fonctionnalités quasi identiques. Pour les **versions 2.4.8 et antérieures**, les commandes d’interface de ligne de commande utilisées pour configurer Valkey restent identiques à celles de Redis, assurant ainsi une rétrocompatibilité transparente et simplifiant la migration ou la prise en charge de deux environnements. L’exemple suivant illustre la commande spécifique à Valkey.

```bash
bin/magento setup:config:set --page-cache=redis --page-cache-redis-server=127.0.0.1 --page-cache-valkey-db=1
```

## Résultats

Suite à ces deux exemples de commandes, Commerce ajoute des lignes similaires à ce qui suit à `<Commerce-install-dir>app/etc/env.php` :

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

## Nouvelle implémentation du cache Valkey

[!BADGE 2.4.9-alpha]{type=Negative tooltip="Disponible uniquement en version 2.4.9-alpha."}

À partir d’Adobe Commerce 2.4.9, Adobe recommande d’utiliser l’implémentation du cache Valkey : `\Magento\Framework\Cache\Backend\Valkey`.

```php
'cache' => [
    'frontend' => [
        'default' => [
            'backend' => '\\Magento\\Framework\\Cache\\Backend\\Valkey',
            'backend_options' => [
                'server' => '127.0.0.1',
                'database' => '0',
                'port' => '6379'
            ],
        ],
],
```

## Fonction de préchargement Valkey

Comme Commerce stocke les données de configuration dans le cache Valkey, vous pouvez précharger les données réutilisées entre les pages. Pour rechercher les clés qui doivent être préchargées, analysez les données transférées de Valkey vers Commerce. Adobe suggère de précharger les données chargées sur chaque page, telles que `SYSTEM_DEFAULT`, `EAV_ENTITY_TYPES` et `DB_IS_UP_TO_DATE`.

Valkey utilise le `pipeline` pour les requêtes de chargement composites. Les clés doivent inclure le préfixe de la base de données. Par exemple, si le préfixe de la base de données est `061_`, la clé de préchargement ressemble à ceci : `061_SYSTEM_DEFAULT`

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

Lors de l’utilisation de la fonction de préchargement avec un cache L2, vous devez ajouter le suffixe `:hash` à vos clés. Le cache L2 transfère uniquement le hachage des données, et non les données réelles.

```php
'preload_keys' => [
    '061_EAV_ENTITY_TYPES:hash',
    '061_GLOBAL_PLUGIN_LIST:hash',
    '061_DB_IS_UP_TO_DATE:hash',
    '061_SYSTEM_DEFAULT:hash',
],
```

## Génération parallèle

À partir de la version 2.4.0 de Commerce, Adobe a introduit l’option `allow_parallel_generation` pour les utilisateurs et utilisatrices qui souhaitent éliminer les attentes de verrous.
Il est désactivé par défaut et Adobe recommande de le désactiver jusqu’à ce que vous disposiez de configurations et/ou de blocs excessifs.

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
                'backend' => 'Magento\\Framework\\Cache\\Backend\\Valkey',
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

## Vérifier la connexion Valkey

Pour vérifier que Valkey et Commerce fonctionnent correctement ensemble, connectez-vous au serveur exécutant Valkey, ouvrez un terminal et utilisez la commande `valkey-cli monitor` ou la commande `redis-cli ping`.

### Commande de moniteur Valkey

```bash
valkey-cli monitor
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

### Commande ping Valkey

```bash
redis-cli ping
```

La réponse attendue est : `PONG`

Si les deux commandes ont réussi, Valkey est correctement configuré.

### Inspection des données compressées

Pour inspecter les données de session compressées et le cache de page, le [RESP.app](https://flathub.org/apps/app.resp.RESP) prend en charge la décompression automatique de la session Commerce 2 et du cache de page et affiche les données de session PHP dans un format lisible par l&#39;utilisateur.
