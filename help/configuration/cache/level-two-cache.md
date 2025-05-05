---
title: Configuration du cache L2
description: Découvrez comment configurer le cache L2.
feature: Configuration, Cache
exl-id: 0504c6fd-188e-46eb-be8e-968238571f4e
source-git-commit: ba3c656566af47f16f58f476d7bc9f4781bb0234
workflow-type: tm+mt
source-wordcount: '423'
ht-degree: 0%

---

# Configuration du cache L2

La mise en cache permet de réduire le trafic réseau entre l’enregistrement du cache distant et l’application Commerce. Une instance Commerce standard transfère environ 300 Ko par requête et le trafic peut rapidement dépasser ~1 000 requêtes dans certaines situations.

Pour réduire la bande passante du réseau à Redis, stockez les données du cache localement sur chaque noeud web et utilisez le cache distant à deux fins :

- Vérifiez la version des données du cache et assurez-vous que le dernier cache est stocké localement.
- Transfert du dernier cache de l’ordinateur distant vers l’ordinateur local

Commerce stocke la version des données hachées dans Redis, en ajoutant le suffixe &quot;:hash&quot; à la clé normale. S’il existe un cache local obsolète, les données sont transférées à l’ordinateur local avec un adaptateur de cache.

>[!INFO]
>
>Pour Adobe Commerce sur l’infrastructure cloud, vous pouvez utiliser [déployer des variables](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html?lang=fr#redis_backend) pour la configuration du cache L2.

## Exemple de configuration

Utilisez l’exemple suivant pour modifier ou remplacer la section de cache existante dans le fichier `app/etc/env.php`.

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
],
```

Où :

- `backend` est l’implémentation du cache L2.
- `backend_options` est la configuration du cache L2.
   - `remote_backend` est l’implémentation du cache distant : Redis ou MySQL.
   - `remote_backend_options` est la configuration du cache distant.
   - `local_backend` est la mise en oeuvre du cache local : `Cm_Cache_Backend_File`
   - `local_backend_options` est la configuration de cache locale.
   - `cache_dir` est une option spécifique au cache de fichier pour le répertoire dans lequel le cache local est stocké.

Adobe recommande d’utiliser Redis pour la mise en cache à distance (`\Magento\Framework\Cache\Backend\Redis`) et `Cm_Cache_Backend_File` pour la mise en cache locale des données dans la mémoire partagée, en utilisant : `'local_backend_options' => ['cache_dir' => '/dev/shm/']`

Adobe recommande l’utilisation de la fonction [`cache preload`](redis-pg-cache.md#redis-preload-feature), car elle réduit considérablement la pression sur Redis. N’oubliez pas d’ajouter le suffixe &#39;:hash&#39; pour les clés de préchargement.

## Options de cache obsolètes

À partir de [!DNL Commerce] 2.4, l’option `use_stale_cache` peut améliorer les performances dans certains cas spécifiques.

En règle générale, le compromis avec l’attente de verrouillage est acceptable du côté des performances, mais plus le nombre de blocs ou de mises en cache est élevé, plus le marchand passe de temps à attendre les verrous. Dans certains scénarios, vous pouvez attendre un délai **nombre de clés** \* **délai de recherche** pour le processus. Dans de rares cas, le marchand peut avoir des centaines de clés dans le cache `Block/Config`, de sorte que même un petit délai de recherche pour le verrouillage peut coûter des secondes.

Le cache obsolète fonctionne uniquement avec un cache L2. Avec un cache obsolète, vous pouvez envoyer un cache obsolète, alors qu’un nouveau cache est généré dans un processus parallèle. Pour activer le cache obsolète, ajoutez `'use_stale_cache' => true` à la configuration supérieure du cache L2.

Adobe recommande d’activer l’option `use_stale_cache` uniquement pour les types de cache qui en bénéficient le plus, notamment :

- `block_html`
- `config_integration_api`
- `config_integration`
- `full_page`
- `layout`
- `reflection`
- `translate`

Adobe ne recommande pas d’activer l’option `use_stale_cache` pour le type de cache `default`.

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
