---
title: Configuration du cache L2 pour l’optimisation des performances
description: Découvrez comment configurer le cache L2 dans Adobe Commerce pour réduire le trafic réseau et améliorer les performances. Découvrez les options d’implémentation héritées et Symfony.
feature: Configuration, Cache
exl-id: 0504c6fd-188e-46eb-be8e-968238571f4e
badgePaas: label="Sur Site" type="Informative" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="S’applique uniquement aux projets Adobe Commerce on-Premise."
TQID: 'https://experienceleague.adobe.com/7vswBqyn9UZLmaeirgPRZ4xEQH5F66XUEtY5hPkz9NY'
product_v2:
  - id: b974b164-8a4e-43b8-a9e2-8e67ec131677
  - id: eadea719-cf89-469b-a6fd-a236a7138047
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
  - id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1
source-git-commit: a816ed6fff5e2573b93712069bc7b1524dcad403
workflow-type: tm+mt
source-wordcount: 1166
ht-degree: 0%

---

# Configuration du cache L2 pour l’optimisation des performances

La mise en cache L2 (à deux niveaux) réduit le trafic réseau entre le stockage de cache distant (Redis ou Valkey) et l’application Commerce en ajoutant une couche de cache locale sur chaque nœud web. Une instance Commerce standard transfère environ 300 Ko par requête et le trafic peut rapidement passer à plus de 1 000 requêtes dans certains cas.

Avec la mise en cache L2, chaque nœud web stocke localement les données fréquemment consultées et utilise le cache distant à deux fins :

- Vérification de la version des données du cache pour s’assurer que le dernier cache est stocké localement
- Transfert des données de cache mises à jour du magasin distant vers l&#39;ordinateur local

Commerce stocke la version des données hachées dans le cache distant, avec le suffixe `:hash` ajouté à la clé normale. Lorsque le cache local est obsolète, les données sont extraites de l&#39;ordinateur distant via un adaptateur de cache.

Deux implémentations du cache L2 sont disponibles :

| Mise en œuvre | Version | Description |
| -------------- | ------- | ----------- |
| [Hérité (`RemoteSynchronizedCache`)](#legacy-l2-cache-configuration-remotesynchronizedcache) | &lt;2.4.9 | Cache à deux niveaux basé sur Zend avec `Cm_Cache_Backend_File` pour le stockage local |
| [Moderne (`symfony_l2`)](#modern-symfony-l2-cache-implementation) | 2.4.9+ | Symfony Cache-based L2 avec conformité PSR-6 et performances améliorées. Prend uniquement en charge Valkey. |

## Configuration de cache L2 héritée (RemoteSynchronizedCache)

>[!NOTE]
>
>Les instructions de configuration de cache L2 héritées s’appliquent aux versions plus anciennes d’Adobe Commerce. Si vous utilisez la version 2.4.9 ou ultérieure d’Adobe Commerce, utilisez Valkey avec [Symfony 2 pour le cache L2](#modern-symfony-l2-cache-implementation).

Les instructions de configuration du cache dépendent de votre type de déploiement :

- **Pour Adobe Commerce on Cloud**, configurez le cache L2 en définissant la variable de déploiement [`REDIS_BACKEND`](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#redis_backend) ou [`VALKEY_BACKEND`](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/env/stage/variables-deploy#valkey_backend) dans `.magento.env.yaml`. Consultez [Configuration du cache L2](../../implementation-playbook/best-practices/planning/redis-valkey-service-configuration.md#configure-l2-cache) pour obtenir des exemples de configuration.

- **Pour les versions sur site d’Adobe Commerce qui prennent en charge Redis**, utilisez l’exemple suivant pour modifier ou remplacer la section de cache existante dans le fichier `app/etc/env.php`.

```php
'cache' => [
    'frontend' => [
        'default' => [
            'backend' => '\\Magento\\Framework\\Cache\\Backend\\RemoteSynchronizedCache',
            'backend_options' => [
                'remote_backend' => '\\Magento\\Framework\\Cache\\Backend\\Redis',
                'remote_backend_options' => [
                    'persistent' => 0,
                    'server' => 'localhost',
                    'database' => '0',
                    'port' => '6379',
                    'password' => '',
                    'compress_data' => '1',
                ],
                'local_backend' => 'Cm_Cache_Backend_File',
                'local_backend_options' => [
                    'cache_dir' => '/dev/shm/'
                ]
            ],
            'frontend_options' => [
                'write_control' => false,
            ],
        ]
    ],
    'type' => [
        'default' => ['frontend' => 'default'],
    ],
]
```

Où :

- `backend` est l’implémentation du cache L2.
- `backend_options` est la configuration du cache L2.
  - `remote_backend` est l’implémentation du cache distant : Redis ou MySQL.
  - `remote_backend_options` est la configuration du cache distant.
  - `local_backend` mise en œuvre du cache local : `Cm_Cache_Backend_File`
  - `local_backend_options` est la configuration du cache local.
  - `cache_dir` est une option spécifique au cache de fichiers pour le répertoire dans lequel le cache local est stocké.

Pour Adobe Commerce, Adobe recommande d’utiliser Redis pour la mise en cache à distance (`\Magento\Framework\Cache\Backend\Redis`) et `Cm_Cache_Backend_File` pour la mise en cache locale des données en mémoire partagée, en utilisant : `'local_backend_options' => ['cache_dir' => '/dev/shm/']`

Adobe recommande l’utilisation de la fonction [`cache preload`](redis-pg-cache.md#redis-preload-feature), car elle réduit considérablement la pression sur Redis. N&#39;oubliez pas d&#39;ajouter le suffixe &#39;:hash&#39; pour les clés de préchargement.

## Options de cache obsolètes

À partir de Commerce 2.4, l’option `use_stale_cache` peut améliorer les performances dans des cas spécifiques en diffusant des données précédemment mises en cache pendant que de nouvelles données de mise en cache sont générées dans un processus parallèle.

En règle générale, le compromis avec l’attente du verrou est acceptable du point de vue du rendement. Cependant, à mesure que le nombre de blocs ou d’entrées de cache augmente, les attentes de verrouillage prennent plus de temps. Dans certains scénarios, l’attente peut atteindre **le nombre de clés** x **délai de recherche** pour le processus. Dans de rares cas, un commerçant peut avoir des centaines de clés dans le cache `Block/Config`, de sorte que même un petit délai de recherche pour un verrou peut coûter des secondes.

>[!IMPORTANT]
>
>Le cache obsolète ne fonctionne qu’avec le cache L2. Pour l’activer, ajoutez `'use_stale_cache' => true` à la configuration de niveau supérieur du cache L2 frontal.

Adobe recommande de n’activer l’option `use_stale_cache` que pour les types de cache qui en bénéficient le plus, notamment :

- `block_html`
- `config_integration_api`
- `config_integration`
- `full_page`
- `layout`
- `reflection`
- `translate`

Adobe déconseille d&#39;activer l&#39;option `use_stale_cache` pour le type de cache `default`.

Le code suivant illustre un exemple de configuration :

```php
'cache' => [
    'frontend' => [
        'default' => [
            'backend' => '\\Magento\\Framework\\Cache\\Backend\\RemoteSynchronizedCache',
            'backend_options' => [
                'remote_backend' => '\\Magento\\Framework\\Cache\\Backend\\Redis',
                'remote_backend_options' => [
                    'persistent' => 0,
                    'server' => 'localhost',
                    'database' => '0',
                    'port' => '6379',
                    'password' => '',
                    'compress_data' => '1',
                ],
                'local_backend' => 'Cm_Cache_Backend_File',
                'local_backend_options' => [
                    'cache_dir' => '/dev/shm/'
                ]
            ],
            'frontend_options' => [
                'write_control' => false,
            ],
        ],
         'stale_cache_enabled' => [
            'backend' => '\\Magento\\Framework\\Cache\\Backend\\RemoteSynchronizedCache',
            'backend_options' => [
                'remote_backend' => '\\Magento\\Framework\\Cache\\Backend\\Redis',
                'remote_backend_options' => [
                    'persistent' => 0,
                    'server' => 'localhost',
                    'database' => '0',
                    'port' => '6379',
                    'password' => '',
                    'compress_data' => '1',
                ],
                'local_backend' => 'Cm_Cache_Backend_File',
                'local_backend_options' => [
                    'cache_dir' => '/dev/shm/'
                ],
                'use_stale_cache' => true,
            ],
            'frontend_options' => [
                'write_control' => false,
            ],
        ]
    ],
    'type' => [
        'default' => ['frontend' => 'default'],
        'layout' => ['frontend' => 'stale_cache_enabled'],
        'block_html' => ['frontend' => 'stale_cache_enabled'],
        'reflection' => ['frontend' => 'stale_cache_enabled'],
        'config_integration' => ['frontend' => 'stale_cache_enabled'],
        'config_integration_api' => ['frontend' => 'stale_cache_enabled'],
        'full_page' => ['frontend' => 'stale_cache_enabled'],
        'translate' => ['frontend' => 'stale_cache_enabled']
    ],
],
```

## Implémentation du cache moderne Symfony L2

Dans les versions 2.4.9 et ultérieures de Commerce, utilisez l’implémentation du cache L2 basée sur le cache Symfony (serveur principal `symfony_l2`) au lieu de l’ancien cache L2. Le cache Symfony L2 offre une mise en cache moderne conforme à la norme PSR-6, avec des performances nettement supérieures à celles de la `RemoteSynchronizedCache` traditionnelle.

>[!NOTE]
>
>Pour Adobe Commerce on Cloud, le package ECE Tools (`ece-tools`) gère automatiquement cette configuration. Ne modifiez pas directement les `app/etc/env.php` : le déploiement remplace les modifications manuelles. Pour la configuration du cloud, voir [Configurer le cache L2 de Symfony](../../implementation-playbook/best-practices/planning/redis-valkey-service-configuration.md#configure-symfony-l2-cache) à la place.

>[!IMPORTANT]
>
>{{redis-cache-support}}
>
>Étant donné que `symfony_l2` est disponible uniquement dans Adobe Commerce 2.4.9 et versions ultérieures, configurez-le avec Valkey comme serveur principal distant. Redis n’est pas un serveur principal distant officiellement pris en charge pour `symfony_l2`. Consultez [Configuration requise](../../installation/system-requirements.md) pour connaître les services de cache pris en charge par version.

### Avantages du cache Symfony L2

- **Architecture moderne** : repose sur les composants de cache Symfony (compatible avec PSR-6)
- **Meilleures performances** : prise en charge native de la sérialisation Igbinary, de la compression gzip et des scripts Lua
- **Connexions persistantes** : réduit la surcharge de connexion Valkey avec le pool de connexions
- **Clés de préchargement** : prend en charge le préchargement des clés de cache pour les données critiques
- **Prise en charge du cache obsolète** : compatibilité totale avec l’option `use_stale_cache`
- **Configuration simplifiée** : noms des types de serveur principal plus propres (`valkey`, `file`)

### Exemple de configuration avec le cache Symfony L2

Utilisez le type de serveur principal `symfony_l2` simplifié pour le cache L2 :

```php
'cache' => [
    'frontend' => [
        'default' => [
            'backend' => 'symfony_l2',
            'backend_options' => [
                // L2 (Remote): Valkey with Symfony Cache
                'remote_backend' => 'valkey',
                'remote_backend_options' => [
                    'server' => 'localhost',
                    'database' => '0',
                    'port' => '6379',
                    'password' => '',
                    'serializer' => 'igbinary',
                    'compression_lib' => 'gzip',
                    'persistent_id' => 'magento_l2_default',
                    'timeout' => '2.5',
                    'read_timeout' => '2.0',
                    'use_lua' => '1',
                    'preload_keys' => [
                        'prefix_EAV_ENTITY_TYPES:hash',
                        'prefix_GLOBAL_PLUGIN_LIST:hash',
                        'prefix_DB_IS_UP_TO_DATE:hash',
                        'prefix_SYSTEM_DEFAULT:hash',
                    ],
                ],
                // L1 (Local): File cache
                'local_backend' => 'file',
                'local_backend_options' => [
                    'cache_dir' => '/dev/shm/magento_l1'
                ],
                'cleanup_percentage' => 90,
            ],
        ]
    ],
    'type' => [
        'default' => ['frontend' => 'default'],
    ],
],
```

### Cache Symfony L2 avec cache périmé

Configurez des fronts distincts pour la prise en charge du cache obsolète :

```php
'cache' => [
    'frontend' => [
        // Default frontend: NO stale cache
        'default' => [
            'backend' => 'symfony_l2',
            'backend_options' => [
                'remote_backend' => 'valkey',
                'remote_backend_options' => [
                    'server' => 'localhost',
                    'database' => '0',
                    'port' => '6379',
                    'serializer' => 'igbinary',
                    'compression_lib' => 'gzip',
                    'persistent_id' => 'magento_l2_default',
                ],
                'local_backend' => 'file',
                'local_backend_options' => [
                    'cache_dir' => '/dev/shm/magento_l1'
                ],
            ],
        ],
        // Stale cache enabled frontend
        'stale_cache_enabled' => [
            'backend' => 'symfony_l2',
            'backend_options' => [
                'remote_backend' => 'valkey',
                'remote_backend_options' => [
                    'server' => 'localhost',
                    'database' => '0',
                    'port' => '6379',
                    'serializer' => 'igbinary',
                    'compression_lib' => 'gzip',
                    'persistent_id' => 'magento_l2_stale',
                ],
                'local_backend' => 'file',
                'local_backend_options' => [
                    'cache_dir' => '/dev/shm/magento_l1_stale'
                ],
                'use_stale_cache' => true,
            ],
        ]
    ],
    'type' => [
        'default' => ['frontend' => 'default'],
        'layout' => ['frontend' => 'stale_cache_enabled'],
        'block_html' => ['frontend' => 'stale_cache_enabled'],
        'reflection' => ['frontend' => 'stale_cache_enabled'],
        'config_integration' => ['frontend' => 'stale_cache_enabled'],
        'config_integration_api' => ['frontend' => 'stale_cache_enabled'],
        'full_page' => ['frontend' => 'stale_cache_enabled'],
        'translate' => ['frontend' => 'stale_cache_enabled'],
    ],
],
```

### Options principales du cache Symfony L2

| Option | Type | Par défaut | Description |
|--------|------|---------|-------------------------------------------------------------------|
| `remote_backend` | chaîne | `'valkey'` | Type de serveur principal distant : `valkey` ou `file`. Utilisez `valkey` pour le cache L2. |
| `remote_backend_options` | tableau | `[]` | Configuration du serveur principal distant (voir la documentation de Valkey) |
| `local_backend` | chaîne | `'file'` | Type de serveur principal local : `file` ou `apcu` |
| `local_backend_options` | tableau | `[]` | Configuration du serveur principal local |
| `cleanup_percentage` | nombre entier | `95` | Seuil de nettoyage du cache L1 (1-100) |
| `use_stale_cache` | booléen | `false` | Activer le cache obsolète pour une haute disponibilité |

>[!NOTE]
>
>L’option `remote_backend` accepte également une valeur de `redis`. Cependant, Redis n’est pas un service de cache officiellement pris en charge pour Adobe Commerce 2.4.9 et versions ultérieures. Adobe recommande de configurer `symfony_l2` avec `valkey` uniquement. Consultez [Configuration requise](../../installation/system-requirements.md) pour connaître les services de cache pris en charge par version.

### Amélioration des performances et de la fiabilité du cache Symfony L2

>[!NOTE]
>
>Ces améliorations s’appliquent aux déploiements d’Adobe Commerce 2.4.9 à l’aide de `symfony_l2` et sont disponibles avec le correctif ACP2E-5132. Voir [Correctifs cloud pour Commerce](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/release-notes/cloud-patches#latest) pour consulter les dernières notes de mise à jour des correctifs.

#### Stockage optimisé des balises de cache L2 Symfony

Optimisation du comportement du cache Symfony L2 pour les déploiements pris en charge par Valkey en éliminant les écritures d’index de balises de système de fichiers redondantes. Les balises de cache sont désormais stockées exclusivement dans Valkey, ce qui aligne le comportement du cache Symfony L2 sur l’implémentation de cache héritée. Cela réduit les E/S de disque inutiles, améliore les performances d’écriture du cache et empêche la croissance du répertoire `var/cache/symfony/tags/`.

#### Amélioration du comportement du cache basé sur les fichiers

Pour les déploiements utilisant le cache basé sur les fichiers (sans Valkey), l’index de balise local continue d’être conservé pour prendre en charge l’invalidation du cache. L’index de balise est désormais écrit dans le `cache_dir` configuré au lieu de l’emplacement de `var/cache` précédemment codé en dur, ce qui garantit une utilisation cohérente du répertoire de cache et une meilleure prise en charge des configurations de cache personnalisées.

#### Amélioration de l’invalidation du cache

L’invalidation du cache utilise désormais des verrous de régénération TTL avec un nettoyage de balise L1 correct, éliminant les entrées de cache obsolètes qui pouvaient auparavant persister après l’invalidation de la balise.

#### Compression activée par défaut

La compression Redis/Valkey (`compress_data`) est désormais activée par défaut pour le cache Symfony L2, ce qui réduit la consommation de mémoire et le trafic réseau et s’aligne sur le comportement par défaut de l’implémentation du cache hérité.

#### Impact

- Élimine les écritures d’index de balises de système de fichiers redondantes pour les déploiements de cache Symfony L2 avec support Valkey.
- Réduit les E/S du disque et améliore les performances d’écriture du cache.
- Empêche toute croissance inutile du répertoire `var/cache/symfony/tags/`.
- Garantit que les déploiements de cache basé sur des fichiers utilisent le `cache_dir` configuré de manière cohérente, tout en préservant le comportement d’invalidation du cache.
- Élimine les entrées de cache obsolètes par le biais de verrous de régénération basés sur TTL et d’un nettoyage de balise L1 approprié.
- Réduit la consommation de mémoire et le trafic réseau avec le `compress_data` activé par défaut.

Pour obtenir des options de configuration détaillées, voir :
- [Configuration du cache Valkey avec le cache Symfony](valkey-pg-cache.md)
