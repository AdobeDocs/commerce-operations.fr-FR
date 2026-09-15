---
title: Configuration du cache L2 pour l’optimisation des performances
description: Découvrez comment configurer le cache L2 dans Adobe Commerce On-Premise pour réduire le trafic réseau et améliorer les performances. Comparez l’ancienne implémentation de RemoteSynchronizedCache à l’implémentation moderne de Symfony L2.
feature: Configuration, Cache
exl-id: 0504c6fd-188e-46eb-be8e-968238571f4e
badgePaas: label="Sur Site" type="Informative" url="https://experienceleague.adobe.com/fr/docs/commerce/user-guides/product-solutions" tooltip="S’applique uniquement aux projets Adobe Commerce on-Premise."
TQID: 'https://experienceleague.adobe.com/7vswBqyn9UZLmaeirgPRZ4xEQH5F66XUEtY5hPkz9NY'
product_v2:
  - id: b974b164-8a4e-43b8-a9e2-8e67ec131677
    internal-label: Commerce on Prem
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: b5f00040-57a0-4a6d-a39e-383b1936c2c9
    internal-label: Compliance
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
  - id: e8818fe6-9c8b-4bc0-9ef8-377a10b7bc75
    internal-label: Architecture
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
    internal-label: Intermediate
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
    internal-label: Implementation
  - id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1
    internal-label: Optimization
source-git-commit: ea07c4a7e42988b2ede3511273261fa7d560b652
workflow-type: tm+mt
source-wordcount: '1686'
ht-degree: 0%
---
# Configuration du cache L2 pour l’optimisation des performances

La mise en cache L2 (à deux niveaux) réduit le trafic réseau entre le service de cache distant et l’application Commerce en ajoutant une couche de cache locale sur chaque nœud web. Une instance Commerce standard peut transférer environ 300 Ko par requête. Lorsque le volume de requêtes est élevé, le trafic réseau qui en résulte peut être important.

Avec la mise en cache L2, chaque nœud web stocke localement les données fréquemment consultées et utilise le cache distant à deux fins :

- Vérification de la version des données du cache pour s’assurer que le dernier cache est stocké localement
- Transfert des données de cache mises à jour du service de cache distant vers l&#39;ordinateur local

Commerce stocke la version des données hachées dans le cache distant, avec le suffixe `:hash` ajouté à la clé normale. Lorsque le cache local est obsolète, les données sont récupérées à partir du service de cache distant via un adaptateur de cache.

L’implémentation du cache L2 disponible dépend de la version de Commerce et du niveau de correctif :

| Mise en œuvre | Version de Commerce | Service de cache à distance | Description |
| -------------- | ---------------- | -------------------- | ----------- |
| [`RemoteSynchronizedCache`](#remotesynchronizedcache-l2-cache-configuration) | Antérieur à la version 2.4.9, si pris en charge | Redis ou Valkey, selon la version et le niveau de correctif | Cache à deux niveaux basé sur Zend avec `Cm_Cache_Backend_File` pour le stockage local |
| [Symfony L2 (`symfony_l2`)](#symfony-l2-cache-implementation) | 2.4.9 et versions ultérieures | Valkey | Mise en œuvre moderne de Symfony Cache L2 conforme au PSR-6 |

## Configuration du cache L2 du cache RemoteSynchronizedCache


>[!NOTE]
>
>Cette section couvre la configuration L2 `RemoteSynchronizedCache` pour les versions sur site d’Adobe Commerce antérieures à la version 2.4.9, où elle est prise en charge par la version exacte de Commerce et la matrice de prise en charge au niveau du correctif.
>
>Pour Adobe Commerce 2.4.9 et versions ultérieures, utilisez Valkey avec le [cache Symfony L2](#symfony-l2-cache-implementation).
>
>Pour Adobe Commerce sur les infrastructures cloud, configurez le cache L2 via les variables de déploiement dans `.magento.env.yaml`. Ne modifiez pas `app/etc/env.php` directement. Voir [Configuration du cache L2](../../implementation-playbook/best-practices/planning/redis-valkey-service-configuration.md#configure-l2-cache).

Les instructions de configuration du cache dépendent de votre version de Commerce :

Pour les versions sur site d’Adobe Commerce qui prennent en charge Redis, utilisez l’exemple suivant pour modifier ou remplacer la section de cache existante dans le fichier `app/etc/env.php`.

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
  - `remote_backend` est l’implémentation du cache à distance : Redis ou Valkey, selon la version de Commerce et la prise en charge au niveau du correctif.
  - `remote_backend_options` est la configuration du cache distant.
  - `local_backend` mise en œuvre du cache local : `Cm_Cache_Backend_File`.
  - `local_backend_options` est la configuration du cache local.
  - `cache_dir` est une option spécifique au cache de fichiers qui définit le répertoire dans lequel le cache local est stocké.

Pour les versions d’Adobe Commerce antérieures à la version 2.4.9 qui prennent en charge Redis ou Valkey, Adobe recommande d’utiliser Redis ou Valkey pour la mise en cache à distance, comme pris en charge par la version exacte, et `Cm_Cache_Backend_File` pour la mise en cache locale. Le cache local est généralement stocké sur un système de fichiers temporaire, tel que `/dev/shm/` :

```php
'local_backend_options' => [
    'cache_dir' => '/dev/shm/'
]
```

Adobe recommande d’utiliser la fonction `[cache preload](redis-pg-cache.md#redis-preload-feature)`, car elle réduit la charge sur Redis. Veillez à ajouter le suffixe `:hash` pour les clés de préchargement.

## Options de cache obsolètes

À partir de Commerce 2.4, l’option `use_stale_cache` peut améliorer les performances dans des cas spécifiques en diffusant des données précédemment mises en cache pendant que de nouvelles données de mise en cache sont générées dans un processus parallèle. Les types de cache recommandés et les arbitrages décrits dans cette section s’appliquent à la fois aux implémentations `RemoteSynchronizedCache` et `symfony_l2`. Pour obtenir un exemple de configuration `symfony_l2`, consultez la section [Cache Symfony L2 avec cache périmé](#symfony-l2-cache-with-stale-cache).

En règle générale, le compromis avec l’attente du verrou est acceptable du point de vue du rendement. Cependant, à mesure que le nombre de blocs ou d’entrées de cache augmente, les attentes de verrouillage prennent plus de temps. Dans certains scénarios, l’attente peut atteindre **le nombre de clés** x **délai de recherche** pour le processus. Dans de rares cas, un utilisateur peut avoir des centaines de clés dans le cache `Block/Config`, de sorte que même un petit délai de recherche pour un verrou peut coûter des secondes.

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

Le code suivant illustre un exemple de configuration pour le serveur principal `RemoteSynchronizedCache`. Pour obtenir un exemple `symfony_l2`, consultez la section [Cache Symfony L2 avec cache périmé](#symfony-l2-cache-with-stale-cache).

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

## Implémentation du cache Symfony L2

Dans les versions 2.4.9 et ultérieures de Commerce, utilisez l’implémentation du cache Symfony L2 (serveur principal `symfony_l2`) au lieu de `RemoteSynchronizedCache`. Le cache Symfony L2 fournit une mise en cache compatible avec PSR-6 à l’aide de Valkey.

>[!IMPORTANT]
>
>Redis n’est pas pris en charge pour la configuration du cache dans les versions d’Adobe Commerce suivantes :
>
>- Adobe Commerce 2.4.9 et versions ultérieures
>- Correctifs Adobe Commerce 2.4.8-p4 et versions ultérieures
>- Correctifs Adobe Commerce 2.4.7-p9 et versions ultérieures
>- Correctifs Adobe Commerce 2.4.6-p14 et versions ultérieures
>- Correctifs Adobe Commerce 2.4.5-p16 et versions ultérieures
>
>Pour ces versions, configurez Valkey.
>
>Si vous configurez `symfony_l2` pour la mise en cache L2 sur Adobe Commerce version 2.4.9 ou ultérieure, vous devez utiliser Valkey pour le service de cache à distance. Voir [configurer Valkey](config-valkey.md).

### Migration de RemoteSynchronizedCache vers Symfony L2

Si vous effectuez une mise à niveau d’une installation sur site du serveur principal `RemoteSynchronizedCache` vers `symfony_l2`, consultez les informations suivantes avant de mettre à jour `app/etc/env.php`. La modification de la seule valeur `backend` n’est pas suffisante. La structure de configuration, les noms de clés et certains comportements par défaut diffèrent.

- **La structure de configuration change.** `remote_backend`, `remote_backend_options` et `local_backend` utilisent des valeurs différentes sous `symfony_l2`. Par exemple, `remote_backend` devient `'valkey'` au lieu d’un nom de classe entièrement qualifié. Utilisez l’[exemple de configuration](#configuration-example-with-symfony-l2-cache) ci-dessous comme point de départ plutôt que de modifier votre configuration `RemoteSynchronizedCache` existante.

- **`preload_keys`n’est pas recommandé avec `symfony_l2`.** Si votre configuration de `RemoteSynchronizedCache` comprend des `preload_keys`, supprimez-les dans le cadre de la migration. Le préchargement des clés n’améliore pas les performances sous `symfony_l2` et peut augmenter la charge sur Valkey en déclenchant des recherches de clés supplémentaires et inutiles.

- **La compression nécessite un indicateur explicite.** La configuration de `compression_lib` seule n’active pas la compression sous `symfony_l2`. Voir [Options du serveur principal pour le cache Symfony L2](#backend-options-for-symfony-l2-cache) pour connaître le paramètre de `compress_data` requis.

- **Les déploiements sur site configurés manuellement n’activent pas le cache obsolète par défaut.** `use_stale_cache` valeur par défaut est `false` sous `symfony_l2` (voir le tableau [options du serveur principal](#backend-options-for-symfony-l2-cache)). Si votre configuration `RemoteSynchronizedCache` a utilisé le front-end `stale_cache_enabled`, vous devez le recréer explicitement à l’aide du modèle dans le cache [Symfony L2 avec un cache obsolète](#symfony-l2-cache-with-stale-cache).

>[!NOTE]
>
>La configuration L2 complète des environnements Adobe Commerce sur Cloud qui définissent la variable de déploiement `VALKEY_BACKEND: symfony_l2`, y compris le serveur frontal `stale_cache_enabled`, est générée automatiquement par `ece-tools`. Voir [Configuration du cache L2 de Symfony](../../implementation-playbook/best-practices/planning/redis-valkey-service-configuration.md#configure-symfony-l2-cache) pour connaître le comportement spécifique au cloud.

- **Redis n’est pas un serveur principal distant pris en charge pour `symfony_l2`.** Migrer vers Valkey dans le cadre de cette modification. Voir [configurer Valkey](config-valkey.md).

### Exemple de configuration avec le cache Symfony L2

>[!IMPORTANT]
>
>Cet exemple de `app/etc/env.php` s’applique uniquement aux installations sur site. Pour Adobe Commerce sur les infrastructures cloud, ne modifiez pas directement les `app/etc/env.php`. `VALKEY_BACKEND: symfony_l2` en `.magento.env.yaml`. `ece-tools` génère et conserve la configuration du cache L2 pendant le déploiement. Voir [Configuration du cache L2 de Symfony](../../implementation-playbook/best-practices/planning/redis-valkey-service-configuration.md#configure-symfony-l2-cache).

Dans le fichier `app/etc/env.php`, utilisez le type de serveur principal `symfony_l2` simplifié pour le cache L2. Cet exemple n’inclut pas la configuration `preload_keys`, qui n’est pas recommandée avec `symfony_l2`. Pour plus d&#39;informations, consultez [Migration de RemoteSynchronizedCache vers Symfony L2](#migrating-from-remotesynchronizedcache-to-symfony-l2).

L’exemple définit `cleanup_percentage` sur `90`. La valeur par défaut est `95`. Ajustez cette valeur en fonction de l’espace de stockage du cache local disponible et des exigences de votre déploiement Commerce.

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
                    'compress_data' => '1',
                    'persistent_id' => 'magento_l2_default',
                    'timeout' => '2.5',
                    'read_timeout' => '2.0',
                    'use_lua' => '1',
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

Consultez la section [Options de cache obsolètes](#stale-cache-options) pour savoir quels types de cache bénéficient du cache obsolète et pourquoi.

Utilisez l’exemple suivant pour configurer des fronts distincts pour `symfony_l2` prise en charge du cache obsolète :

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
                    'compress_data' => '1',
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
                    'compress_data' => '1',
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
| -------- | ------ | --------- | ----------- |
| `remote_backend` | chaîne | `'valkey'` | Serveur principal du cache distant. Utilisez `valkey` avec Symfony L2. Redis n’est pas officiellement pris en charge. |
| `remote_backend_options` | tableau | `[]` | Configuration du serveur principal de la clé distante |
| `local_backend` | chaîne | `'file'` | Type de serveur principal local : `file` ou `apcu` |
| `local_backend_options` | tableau | `[]` | Configuration du serveur principal local |
| `cleanup_percentage` | nombre entier | `95` | Seuil de nettoyage du cache L1, exprimé en pourcentage de 1 à 100 |
| `use_stale_cache` | booléen | `false` | Active le cache obsolète pour le serveur frontal |
| `compress_data` | booléen | `false` | Active la compression lorsqu&#39;elle est combinée avec `compression_lib`. Définissez cette option dans les options distantes du serveur principal Valkey. |
| `persistent` | booléen | `true` | Contrôle les connexions persistantes au serveur principal distant. Définissez sur `false` (`'0'`) pour correspondre au comportement du cache Zend, qui correspond par défaut aux connexions non persistantes. |

>[!NOTE]
>
>L’option `frontend_options.write_control` s’applique à la configuration `RemoteSynchronizedCache` et ne s’applique pas aux `symfony_l2`.

### Amélioration des performances et de la fiabilité du cache Symfony L2

>[!NOTE]
>
>Ces améliorations s’appliquent aux déploiements d’Adobe Commerce 2.4.9 à l’aide de `symfony_l2` et sont disponibles dans le correctif ACP2E-5132.
>
>Pour Adobe Commerce On-Premise, appliquez ce correctif à l’aide de l’outil de correctifs de la qualité (QPT). Pour Adobe Commerce sur les infrastructures cloud, le correctif est inclus dans le package Correctifs cloud pour Commerce , qui est une dépendance de `ece-tools`. Effectuez la mise à jour vers la dernière version de `ece-tools` pour recevoir les derniers correctifs cloud lors du déploiement.

Les mises à jour les plus récentes améliorent l’évolutivité du cache Symfony L2, réduisent les E/S inutiles du système de fichiers et améliorent la cohérence et la fiabilité du cache.

#### Stockage optimisé des balises de cache L2 Symfony

Pour les déploiements de cache Symfony L2 soutenus par Valkey, les balises de cache sont stockées exclusivement dans Valkey. Cela élimine les écritures redondantes de l’index de balises du système de fichiers, réduit les E/S du disque et empêche toute croissance inutile du répertoire `var/cache/symfony/tags/`.

#### Amélioration du comportement du cache basé sur les fichiers

Pour les déploiements utilisant le cache basé sur les fichiers (sans Valkey), l’index de balise local continue d’être conservé pour prendre en charge l’invalidation du cache. L’index de balise est désormais écrit dans le `cache_dir` configuré au lieu de l’emplacement de `var/cache` précédemment codé en dur, ce qui garantit une utilisation cohérente du répertoire de cache et une meilleure prise en charge des configurations de cache personnalisées.

#### Correctif d’appartenance à une balise obsolète après le balisage

Le rebalisage d’une entrée du cache peut la laisser associée à des balises auxquelles elle n’appartient plus. Les appartenances aux balises obsolètes sont désormais effacées lors du retag, de sorte que les entrées du cache ne sont invalidées que par les balises qui leur sont actuellement affectées.

#### Correctif d’écriture à distance redondant pour les enregistrements inchangés

L’enregistrement d’une entrée de cache avec du contenu inchangé a tout de même déclenché une écriture sur le serveur principal distant (Valkey). Les enregistrements sont désormais ignorés lorsque le contenu est inchangé, ce qui réduit les écritures distantes inutiles.

#### Correctif d’expulsion L1 basé sur la taille (cleanup_percentage)

Le seuil de `cleanup_percentage` utilisé pour l’expulsion L1 basée sur la taille n’a pas déclenché de manière cohérente le nettoyage. L’éviction du cache L1 respecte désormais correctement le `cleanup_percentage` configuré.

#### Verrouillage de la régénération du cache périmé

Lorsque `use_stale_cache` est activé et que la copie distante d’une entrée est temporairement indisponible, un seul processus acquiert désormais un verrou de courte durée pour générer à nouveau cette entrée. D’autres requêtes simultanées pour la même entrée continuent à servir la valeur locale existante au lieu de la régénérer elles-mêmes, ce qui réduit les bousculades de régénération et la charge redondante du serveur principal.

#### Impact

- Élimine les écritures redondantes d’index de balises de système de fichiers pour les déploiements de cache Symfony L2 soutenus par Valkey, ce qui réduit les E/S de disque et empêche toute croissance inutile du répertoire `var/cache/symfony/tags/`.
- Garantit que les déploiements de cache basé sur des fichiers utilisent de manière cohérente le `cache_dir` configuré pour l’index de balise local tout en préservant le comportement d’invalidation du cache.
- Empêche l’invalidation incorrecte du cache causée par les appartenances obsolètes aux balises laissées derrière après le rebalisage.
- Réduit les écritures distantes inutiles pour des enregistrements de cache inchangés, ce qui réduit la charge du réseau et du serveur principal.
- Garantit que l’éviction du cache L1 se déclenche de manière fiable au seuil de `cleanup_percentage` configuré.
- Réduit les bousculades de régénération pour les entrées `use_stale_cache` en sélectionnant un seul régénérateur par clé au lieu de faire en sorte que chaque requête simultanée reconstruise l&#39;entrée.

Pour obtenir des options de configuration détaillées, voir :

- [Configuration du cache Valkey avec le cache Symfony](valkey-pg-cache.md)
