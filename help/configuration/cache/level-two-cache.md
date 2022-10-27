---
title: Configuration du cache L2
description: Découvrez comment configurer le cache L2.
source-git-commit: 2ef8b48fab84221c8e6423f41126bbee37706809
workflow-type: tm+mt
source-wordcount: '427'
ht-degree: 0%

---

# Configuration du cache L2

La mise en cache permet de réduire le trafic réseau entre le stockage du cache distant et l’application Commerce. Une instance Commerce standard transfère environ 300 Ko par requête et le trafic peut rapidement dépasser ~1 000 requêtes dans certaines situations.

Pour réduire la bande passante du réseau à Redis, stockez les données du cache localement sur chaque noeud web et utilisez le cache distant à deux fins :

- Vérifiez la version des données du cache et assurez-vous que le dernier cache est stocké localement.
- Transfert du dernier cache de l’ordinateur distant vers l’ordinateur local

Commerce stocke la version des données hachées dans Redis, avec le suffixe &quot;:hash&quot; ajouté à la clé normale. S’il existe un cache local obsolète, les données sont transférées à l’ordinateur local avec un adaptateur de cache.

>[!INFO]
>
>Pour Adobe Commerce sur l’infrastructure cloud, vous pouvez utiliser [variables de déploiement](https://devdocs.magento.com/cloud/env/variables-deploy.html#redis_backend) pour la configuration du cache L2.

## Exemple de configuration

Utilisez l’exemple suivant pour modifier ou remplacer la section de cache existante dans la variable `app/etc/env.php` fichier .

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
                ],
                'use_stale_cache' => false,
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
   - `local_backend` est l’implémentation du cache local : `Cm_Cache_Backend_File`
   - `local_backend_options` est la configuration du cache local.
      - `cache_dir` est une option spécifique au cache de fichier pour le répertoire dans lequel le cache local est stocké.
   - `use_stale_cache` est un indicateur qui active ou désactive l’utilisation du cache obsolète.

Adobe recommande l’utilisation de Redis pour la mise en cache à distance (`\Magento\Framework\Cache\Backend\Redis`) et `Cm_Cache_Backend_File` pour la mise en cache locale des données en mémoire partagée, en utilisant : `'local_backend_options' => ['cache_dir' => '/dev/shm/']`

Adobe recommande l’utilisation de la variable [`cache preload`](redis-pg-cache.md#redis-preload-feature) , car elle réduit considérablement la pression sur Redis. N’oubliez pas d’ajouter le suffixe &#39;:hash&#39; pour les clés de préchargement.

## Options de cache obsolètes

Prise en main de [!DNL Commerce] 2.4, la variable `use_stale_cache` peut améliorer les performances dans certains cas spécifiques.

En règle générale, le compromis avec l’attente de verrouillage est acceptable du côté des performances, mais plus le nombre de blocs ou de mises en cache est élevé, plus le marchand passe de temps à attendre les verrous. Dans certains scénarios, vous pouvez attendre une **nombre de clés** \* **délai de recherche** durée du processus. Dans de rares cas, le marchand peut avoir des centaines de clés dans le `Block/Config` cache, de sorte que même un petit délai de recherche pour le verrouillage peut coûter des secondes.

Le cache obsolète fonctionne uniquement avec un cache L2. Avec un cache obsolète, vous pouvez envoyer un cache obsolète, alors qu’un nouveau cache est généré dans un processus parallèle. Pour activer le cache obsolète, ajoutez `'use_stale_cache' => true` à la configuration supérieure du cache L2.

Adobe recommande d’activer la fonction `use_stale_cache` uniquement pour les types de cache qui en bénéficient le plus, notamment :

- `block_html`
- `config_integration_api`
- `config_integration`
- `full_page`
- `layout`
- `reflection`
- `translate`

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
                ],
                'use_stale_cache' => false,
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
