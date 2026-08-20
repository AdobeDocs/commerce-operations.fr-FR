---
title: Configuration du cache L2 pour l’optimisation des performances
description: Découvrez comment configurer le cache L2 dans Adobe Commerce pour réduire le trafic réseau et améliorer les performances. Découvrez les options d’implémentation héritées et Symfony.
feature: Configuration, Cache
exl-id: 0504c6fd-188e-46eb-be8e-968238571f4e
badgePaas: label="Sur Site" type="Informative" url="https://experienceleague.adobe.com/fr/docs/commerce/user-guides/product-solutions" tooltip="S’applique uniquement aux projets Adobe Commerce on-Premise."
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
source-git-commit: 7ebadd26eee51aa2c2f3dfe8a8a2ed3dc20657b9
workflow-type: tm+mt
source-wordcount: 1725
ht-degree: 0%

---

# Configuration du cache L2 pour l’optimisation des performances

La mise en cache L2 (à deux niveaux) réduit le trafic réseau entre le stockage de cache distant (Redis ou Valkey) et l’application Commerce en ajoutant une couche de cache locale sur chaque nœud web. Une instance Commerce standard transfère environ 300 Ko par requête et le trafic peut rapidement passer à plus de 1 000 requêtes dans certains cas.

Avec la mise en cache L2, chaque nœud web stocke localement les données fréquemment consultées et utilise le cache distant à deux fins :

- Vérification de la version des données du cache pour s’assurer que le dernier cache est stocké localement
- Transfert des données de cache mises à jour du magasin distant vers l&#39;ordinateur local

Commerce stocke la version des données hachées dans le cache distant, avec le suffixe `:hash` ajouté à la clé normale. Lorsque le cache local est obsolète, les données sont extraites de l&#39;ordinateur distant via un adaptateur de cache.

Il existe deux implémentations du cache L2 disponibles dans Adobe Commerce :

| Mise en œuvre | Version | Description |
| -------------- | ------- | ----------- |
| [Hérité (`RemoteSynchronizedCache`)](#legacy-l2-cache-configuration-remotesynchronizedcache) | &lt;2.4.9 | Cache à deux niveaux basé sur Zend avec `Cm_Cache_Backend_File` pour le stockage local |
| [Moderne (`symfony_l2`)](#modern-symfony-l2-cache-implementation) | 2.4.9+ | Symfony Cache-based L2 avec conformité PSR-6 et performances améliorées. Prend en charge Valkey. |

Le cache Symfony L2 est l’implémentation recommandée pour Adobe Commerce 2.4.9 et les versions ultérieures. Il fournit une mise en cache moderne, conforme à la norme PSR-6, avec des performances nettement supérieures à celles de la `RemoteSynchronizedCache` traditionnelle.

## Configuration de cache L2 héritée (RemoteSynchronizedCache)

Les instructions de configuration de cache L2 héritées s’appliquent aux versions plus anciennes d’Adobe Commerce. Si vous utilisez la version 2.4.9 ou une version ultérieure d’Adobe Commerce, utilisez Valkey avec l’implémentation du cache L2 de [Modern Symfony](#modern-symfony-l2-cache-implementation).

>[!NOTE]
>
>Cette page traite uniquement de la configuration locale. Pour Adobe Commerce on Cloud, voir [Configuration du cache L2](../../implementation-playbook/best-practices/planning/redis-valkey-service-configuration.md#configure-l2-cache).

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
  - `remote_backend` est l’implémentation du cache distant : Redis ou MySQL.
  - `remote_backend_options` est la configuration du cache distant.
  - `local_backend` mise en œuvre du cache local : `Cm_Cache_Backend_File`.
  - `local_backend_options` est la configuration du cache local.
  - `cache_dir` est une option spécifique au cache de fichiers pour le répertoire dans lequel le cache local est stocké.

Pour les versions d’Adobe Commerce antérieures à la version 2.4.9 qui prennent en charge Redis, Adobe recommande d’utiliser Redis pour la mise en cache à distance (`\Magento\Framework\Cache\Backend\Redis`) et `Cm_Cache_Backend_File` pour la mise en cache locale des données en mémoire partagée, en utilisant : `'local_backend_options' => ['cache_dir' => '/dev/shm/']`.

Adobe recommande l’utilisation de la fonction [`cache preload`](redis-pg-cache.md#redis-preload-feature), car elle réduit considérablement la pression sur Redis. N&#39;oubliez pas d&#39;ajouter le suffixe `:hash` pour les clés de préchargement.

## Options de cache obsolètes

À partir de Commerce 2.4, l’option `use_stale_cache` peut améliorer les performances dans des cas spécifiques en diffusant des données précédemment mises en cache pendant que de nouvelles données de mise en cache sont générées dans un processus parallèle. Les types de cache et les arbitrages recommandés décrits dans cette section s’appliquent à la fois aux implémentations `RemoteSynchronizedCache` et `symfony_l2` héritées. Pour obtenir un exemple de configuration `symfony_l2`, consultez la section [Cache Symfony L2 avec cache périmé](#symfony-l2-cache-with-stale-cache).

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

Le code suivant illustre un exemple de configuration pour l’ancien serveur principal `RemoteSynchronizedCache`. Pour obtenir un exemple `symfony_l2`, consultez la section [Cache Symfony L2 avec cache périmé](#symfony-l2-cache-with-stale-cache).

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

>[!IMPORTANT]
>
>Redis n’est pas pris en charge en tant que serveur principal de cache distant commençant par :
>
>- Adobe Commerce 2.4.9 et versions ultérieures
>- Correctifs 2.4.8-p4 et ultérieurs
>- Correctifs 2.4.7-p9 et ultérieurs
>- Correctifs 2.4.6-p14 et ultérieurs
>- Correctifs 2.4.5-p16 et versions ultérieures
>
>Si vous effectuez une mise à niveau au-delà de ces versions, configurez Valkey et mettez à jour votre configuration de cache pour utiliser `symfony_l2`. Voir [configuration de Valkey](config-valkey.md) et [Configuration requise](../../installation/system-requirements.md).

### Avantages du cache Symfony L2

- **Architecture moderne :** basée sur les composants de cache Symfony (compatible avec PSR-6)
- **Meilleures performances :** prise en charge native de la sérialisation Igbinary, de la compression gzip et des scripts Lua
- **Connexions persistantes :** réduit la surcharge de connexion de Valkey grâce au pool de connexions
- **Clés de préchargement :** prend en charge le préchargement des clés de cache pour les données critiques
- **Prise en charge du cache obsolète :** compatibilité totale avec l’option `use_stale_cache`
- **Configuration simplifiée :** des noms de type de serveur principal plus propres (`valkey`, `file`)

### Migration de RemoteSynchronizedCache vers Symfony L2

Si vous effectuez une mise à niveau d’une installation sur site à partir de l’ancien serveur principal `RemoteSynchronizedCache` vers `symfony_l2`, consultez les informations suivantes avant de mettre à jour `app/etc/env.php`. La modification de la seule valeur `backend` n’est pas suffisante. La structure de configuration, les noms de clés et certains comportements par défaut diffèrent.

- **La structure de configuration change.** `remote_backend`, `remote_backend_options` et `local_backend` utilisent des valeurs différentes sous `symfony_l2`. Par exemple, `remote_backend` devient `'valkey'` au lieu d’un nom de classe entièrement qualifié. Utilisez l’[exemple de configuration](#configuration-example-with-symfony-l2-cache) ci-dessous comme point de départ plutôt que de modifier votre configuration héritée existante.

- **`preload_keys`n’est pas recommandé avec `symfony_l2`.** Si votre configuration héritée comprend des `preload_keys`, supprimez-les dans le cadre de la migration. Le préchargement des clés n’améliore pas les performances sous `symfony_l2` et peut augmenter la charge sur Valkey en déclenchant des recherches de clés supplémentaires et inutiles.

- **La compression nécessite un indicateur explicite.** La configuration de `compression_lib` seule n’active pas la compression sous `symfony_l2`. Voir [Options du serveur principal pour le cache Symfony L2](#backend-options-for-symfony-l2-cache) pour connaître le paramètre de `compress_data` requis.

- **Le cache obsolète n’est pas activé par défaut pour les déploiements sur site configurés manuellement.** `use_stale_cache` valeur par défaut est `false` sous `symfony_l2` (voir le tableau [options du serveur principal](#backend-options-for-symfony-l2-cache)). Si votre configuration héritée utilisait le front-end `stale_cache_enabled`, vous devez le recréer explicitement à l’aide du modèle dans le cache [Symfony L2 avec un cache obsolète](#symfony-l2-cache-with-stale-cache).

>[!NOTE]
>
>La configuration L2 complète des environnements Adobe Commerce sur Cloud qui définissent la variable de déploiement `VALKEY_BACKEND: symfony_l2`, y compris le serveur frontal `stale_cache_enabled`, est générée automatiquement par `ece-tools`. Voir [Configuration du cache L2 de Symfony](../../implementation-playbook/best-practices/planning/redis-valkey-service-configuration.md#configure-symfony-l2-cache) pour connaître le comportement spécifique au cloud.

- **Redis n’est pas un serveur principal distant pris en charge pour `symfony_l2`.** Migrer vers Valkey dans le cadre de cette modification. Voir [configurer Valkey](config-valkey.md).

### Exemple de configuration avec le cache Symfony L2

>[!NOTE]
>
>Cet exemple concerne la configuration de `app/etc/env.php` sur site. Pour Adobe Commerce on Cloud, la configuration du cache est gérée automatiquement par `ece-tools`. Au lieu de modifier directement les `env.php`, consultez [Configuration du cache L2 de Symfony](../../implementation-playbook/best-practices/planning/redis-valkey-service-configuration.md#configure-symfony-l2-cache).

Dans le fichier `app/etc/env.php`, utilisez le type de serveur principal `symfony_l2` simplifié pour le cache L2. Cet exemple n’inclut pas la configuration `preload_keys`, qui n’est pas recommandée avec `symfony_l2`. Pour plus d&#39;informations, consultez [Migration de RemoteSynchronizedCache vers Symfony L2](#migrating-from-remotesynchronizedcache-to-symfony-l2).

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
| -------- | ------ | --------- | --------------------------------------------------------------------- |
| `remote_backend` | chaîne | `'valkey'` | Type de serveur principal distant : `valkey` ou `file`. Utilisez `valkey` pour le cache L2. |
| `remote_backend_options` | tableau | `[]` | Configuration du serveur principal distant (voir la documentation de Valkey) |
| `local_backend` | chaîne | `'file'` | Type de serveur principal local : `file` ou `apcu` |
| `local_backend_options` | tableau | `[]` | Configuration du serveur principal local |
| `cleanup_percentage` | nombre entier | `95` | Seuil de nettoyage du cache L1 (1-100) |
| `use_stale_cache` | booléen | `false` | Activer le cache obsolète pour une haute disponibilité |
| `compress_data` | booléen | `false` | Active la compression lorsqu&#39;elle est combinée avec `compression_lib`. La configuration de `compression_lib` seule n’active pas la compression. |
| `persistent` | booléen | `true` | Contrôle les connexions persistantes au serveur principal distant. Définissez sur `false` (`'0'`) pour correspondre au comportement du cache Zend hérité, qui correspond par défaut aux connexions non persistantes. |


>[!NOTE]
>
>- L’option `remote_backend` accepte également une valeur de `redis`, mais Redis n’est pas officiellement pris en charge (voir la remarque ci-dessus sous [Implémentation du cache L2 Modern Symfony](#modern-symfony-l2-cache-implementation)).
>
>- `frontend_options.write_control`, utilisé dans la configuration de `RemoteSynchronizedCache` héritée, ne s’applique pas aux `symfony_l2`.

### Amélioration des performances et de la fiabilité du cache Symfony L2

>[!NOTE]
>
>Ces améliorations s’appliquent aux déploiements d’Adobe Commerce 2.4.9 à l’aide de `symfony_l2` et sont disponibles dans le correctif ACP2E-5132. Pour Adobe Commerce On-Premise, appliquez ce correctif à l’aide de l’outil de correctifs de la qualité (QPT). Pour Adobe Commerce on Cloud, ce correctif est distribué automatiquement via [Correctifs cloud pour Commerce](https://experienceleague.adobe.com/fr/docs/commerce-on-cloud/user-guide/release-notes/cloud-patches#latest).

Les mises à jour les plus récentes améliorent l’évolutivité du cache Symfony L2, réduisent les E/S inutiles du système de fichiers et améliorent la cohérence et la fiabilité du cache.

#### Stockage optimisé des balises de cache L2 Symfony

Optimisation du comportement du cache Symfony L2 pour les déploiements pris en charge par Valkey en éliminant les écritures d’index de balises de système de fichiers redondantes. Les balises de cache sont désormais stockées exclusivement dans Valkey, ce qui aligne le comportement du cache Symfony L2 sur l’implémentation de cache héritée. Cela réduit les E/S de disque inutiles, améliore les performances d’écriture du cache et empêche la croissance du répertoire `var/cache/symfony/tags/`.

#### Amélioration du comportement du cache basé sur les fichiers

Pour les déploiements utilisant le cache basé sur les fichiers (sans Valkey), l’index de balise local continue d’être conservé pour prendre en charge l’invalidation du cache. L’index de balise est désormais écrit dans le `cache_dir` configuré au lieu de l’emplacement de `var/cache` précédemment codé en dur, ce qui garantit une utilisation cohérente du répertoire de cache et une meilleure prise en charge des configurations de cache personnalisées.

#### Correctif d’appartenance à une balise obsolète après le balisage

Le rebalisage d’une entrée du cache peut la laisser associée à des balises auxquelles elle n’appartenait plus. Les appartenances aux balises obsolètes sont désormais effacées lors du retag, de sorte que les entrées du cache ne sont invalidées que par les balises qui leur sont actuellement affectées.

#### Correctif d’écriture à distance redondant pour les enregistrements inchangés

L’enregistrement d’une entrée de cache avec du contenu inchangé a tout de même déclenché une écriture sur le serveur principal distant (Valkey). Les enregistrements sont désormais ignorés lorsque le contenu est inchangé, ce qui réduit les écritures distantes inutiles.

#### Correctif d’expulsion L1 basé sur la taille (cleanup_percentage)

Le seuil de `cleanup_percentage` utilisé pour l’expulsion L1 basée sur la taille n’a pas déclenché de manière cohérente le nettoyage. L’éviction du cache L1 respecte désormais correctement le `cleanup_percentage` configuré.

#### Verrouillage de la régénération du cache périmé

Lorsque `use_stale_cache` est activé et que la copie distante d’une entrée est temporairement indisponible, un seul processus acquiert désormais un verrou de courte durée pour générer à nouveau cette entrée. D’autres requêtes simultanées pour la même entrée continuent à servir la valeur locale existante au lieu de la régénérer elles-mêmes, ce qui réduit les bousculades de régénération et la charge redondante du serveur principal.

#### Impact

- Élimine les écritures d’index de balises de système de fichiers redondantes pour les déploiements de cache Symfony L2 soutenus par Valkey, ce qui réduit les E/S de disque et empêche toute croissance inutile du répertoire `var/cache/symfony/tags/`.
- Garantit que les déploiements de cache basé sur des fichiers utilisent de manière cohérente le `cache_dir` configuré pour l’index de balise local tout en préservant le comportement d’invalidation du cache.
- Empêche l’invalidation incorrecte du cache causée par les appartenances obsolètes aux balises laissées derrière après le rebalisage.
- Réduit les écritures distantes inutiles pour des enregistrements de cache inchangés, ce qui réduit la charge du réseau et du serveur principal.
- Garantit que l’éviction du cache L1 se déclenche de manière fiable au seuil de `cleanup_percentage` configuré.
- Réduit les bousculades de régénération pour les entrées `use_stale_cache` en sélectionnant un seul régénérateur par clé au lieu de chaque requête simultanée la reconstruisant.

Pour obtenir des options de configuration détaillées, voir :

- [Configuration du cache Valkey avec le cache Symfony](valkey-pg-cache.md)

>[!MORELIKETHIS]
>
>- [Présentation de la mise en cache et options de configuration](caching-overview.md)
>- [Options de cache du serveur principal et référence de stockage](cache-options.md)
>- [Configuration des fronts et des types du cache](cache-types.md)
>- [Configurer Redis pour le cache de page et par défaut](redis-pg-cache.md)
