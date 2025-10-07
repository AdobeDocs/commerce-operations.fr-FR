---
title: env.php référence
description: Découvrez les valeurs et les sections de configuration du fichier env.php dans Adobe Commerce. Découvrez les paramètres d’environnement et les options de configuration.
exl-id: cf02da8f-e0de-4f0e-bab6-67ae02e9166f
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '1016'
ht-degree: 0%

---

# env.php référence

Le fichier `env.php` contient les sections suivantes :

| Nom | Description |
|-------------------------------|-----------------------------------------------------------------|
| `backend` | Paramètres de la zone Admin |
| `cache` | Configuration de la page de redis et du cache par défaut |
| `cache_types` | Paramètres de stockage dans le cache |
| `consumers_wait_for_messages` | Configurer la manière dont les consommateurs et consommatrices traitent les messages de la file d’attente des messages |
| `cron` | Activation ou désactivation des tâches cron |
| `crypt` | La clé de chiffrement pour les fonctions cryptographiques |
| `db` | Paramètres de connexion à la base de données |
| `default_connection` | Connexion par défaut des files d&#39;attente des messages |
| `directories` | Paramètres de mappage des répertoires Commerce |
| `downloadable_domains` | Liste des domaines téléchargeables |
| `install` | La date d&#39;installation |
| `lock` | Verrouiller les paramètres du fournisseur |
| `MAGE_MODE` | Le [&#x200B; mode d’application &#x200B;](../bootstrap/application-modes.md) |
| `queue` | [Files d’attente des messages](../queues/manage-message-queues.md) paramètres |
| `resource` | Mappage du nom d’une ressource sur une connexion |
| `session` | Données de stockage de la session |
| `system` | Désactive le champ à modifier dans l’administrateur |
| `x-frame-options` | Définition de [x-frame-options][x-frame-options] |

## serveur principal

Configurez le **frontName** pour l’URL d’administration Commerce à l’aide du nœud `backend` dans env.php.

```conf
'backend' => [
  'frontName' => 'admin'
]
```

## cache

Configurez la page redis et la mise en cache par défaut en utilisant `cache` nœud dans le fichier `env.php`.

```conf
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
]
```

En savoir plus dans [Configuration Redis](../cache/redis-pg-cache.md).

## cache_types

Toutes les configurations de types de cache sont disponibles à partir de ce nœud.

```conf
'cache_types' => [
  'config' => 1,
  'layout' => 1,
  'block_html' => 1,
  'collections' => 1,
  'reflection' => 1,
  'db_ddl' => 1,
  'compiled_config' => 1,
  'eav' => 1,
  'customer_notification' => 1,
  'config_integration' => 1,
  'config_integration_api' => 1,
  'full_page' => 1,
  'config_webservice' => 1,
  'translate' => 1,
  'vertex' => 1
]
```

En savoir plus sur les différents [&#x200B; types de cache &#x200B;](../cli/manage-cache.md).

## consumer_wait_for_messages

Indiquez si les consommateurs doivent continuer à interroger les messages si le nombre de messages traités est inférieur à la valeur `max_messages`. La valeur par défaut est `1`.

```conf
'queue' => [
    'consumers_wait_for_messages' => 1
]
```

Les options suivantes sont disponibles :

- `1` : les clients continuent à traiter les messages de la file d&#39;attente des messages jusqu&#39;à ce qu&#39;ils atteignent la valeur `max_messages` spécifiée dans le fichier `env.php` avant de fermer la connexion TCP et d&#39;arrêter le traitement des clients. Si la file d’attente se vide avant d’atteindre la valeur `max_messages`, le client attend l’arrivée d’autres messages.

  Nous recommandons ce paramètre pour les grands commerçants, car un flux de messages constant est attendu et les retards de traitement ne sont pas souhaitables.

- `0` : les consommateurs et consommatrices traitent les messages disponibles dans la file d&#39;attente, ferment la connexion TCP et s&#39;arrêtent. Les consommateurs et consommatrices n’attendent pas que des messages supplémentaires entrent dans la file d’attente, même si le nombre de messages traités est inférieur à la valeur `max_messages` spécifiée dans le fichier `env.php`. Cela peut permettre d’éviter les problèmes liés aux tâches cron en raison des longs délais de traitement des files d’attente des messages.

  Nous recommandons ce paramètre pour les petits commerçants qui ne s&#39;attendent pas à un flux de messages constant et qui préfèrent conserver les ressources informatiques en échange de retards de traitement mineurs alors qu&#39;il pourrait n&#39;y avoir aucun message pendant des jours.

## cron

Activez ou désactivez les tâches cron pour l’application Commerce. Par défaut, les tâches cron sont activées. Pour les désactiver, ajoutez la configuration `cron` au fichier `env.php` et définissez la valeur sur `0`.

```conf
'cron' => [
  'enabled' => 0
]
```

>[!WARNING]
>
>Soyez prudent lorsque vous désactivez les tâches cron. Lorsqu’ils sont désactivés, les processus essentiels requis par l’application Commerce ne s’exécutent pas.

En savoir plus sur [Crons](../cli/configure-cron-jobs.md).

## chiffrer

Commerce utilise une clé de chiffrement pour protéger les mots de passe et d’autres données sensibles. Cette clé est générée lors du processus d&#39;installation.

```conf
'crypt' => [
  'key' => '63d409380ccb1182bfb27c231b732f05'
]
```

Apprenez-en davantage sur la [clé de chiffrement](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/encryption-key) dans le guide d’utilisation de _Commerce_.

## db

Toutes les configurations de base de données sont disponibles dans ce nœud.

```conf
'db' => [
  'table_prefix' => '',
  'connection' => [
    'default' => [
      'host' => 'localhost',
      'dbname' => 'magento_db',
      'username' => 'root',
      'password' => 'admin123',
      'model' => 'mysql4',
      'engine' => 'innodb',
      'initStatements' => 'SET NAMES utf8;',
      'active' => '1'
    ]
  ]
]
```

## default_connection

Définit la connexion par défaut pour les files d’attente de messages. La valeur peut être `db`, `amqp` ou un système de file d’attente personnalisé comme `redismq`. Si vous spécifiez une valeur autre que `db`, le logiciel de file d’attente de messages doit d’abord être installé et configuré. Sinon, les messages ne seront pas traités correctement.

```conf
'queue' => [
    'default_connection' => 'amqp'
]
```

Si `queue/default_connection` est spécifié dans le fichier de `env.php` système, cette connexion est utilisée pour toutes les files d&#39;attente de messages du système, sauf si une connexion spécifique est définie dans un fichier `queue_topology.xml`, `queue_publisher.xml` ou `queue_consumer.xml`.
Par exemple, si `queue/default_connection` est `amqp` dans `env.php` mais qu’une connexion `db` est spécifiée dans les fichiers XML de configuration de file d’attente d’un module, le module utilisera MySQL comme courtier de messages.

## répertoires

Options de mappage de répertoire facultatives devant être définies lorsque le serveur web est configuré pour servir l’application Commerce à partir du répertoire `/pub` pour une [sécurité renforcée](../../installation/tutorials/docroot.md).

```conf
'directories' => [
    'document_root_is_pub' => true
]
```

## downloadable_domains

Liste des domaines téléchargeables disponibles dans ce nœud. D’autres domaines peuvent être ajoutés, supprimés ou répertoriés à l’aide des commandes de l’interface de ligne de commande.

```conf
'downloadable_domains' => [
    'local.vanilla.com'
]
```

En savoir plus sur les [domaines téléchargeables](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/cli-reference/commerce-on-premises#downloadabledomainsadd).

## installer

Date d’installation de l’application Commerce.

```conf
'install' => [
  'date' => 'Tue, 23 Apr 2019 09:31:07 +0000'
]
```

## serrure

Les paramètres du fournisseur de verrous sont configurés à l’aide du nœud `lock` .

En savoir plus sur la [configuration du fournisseur de verrouillage](../../installation/tutorials/lock-provider.md).

## MODE_IMAGE

Le mode de déploiement peut être configuré dans ce nœud.

```conf
'MAGE_MODE' => 'developer'
```

En savoir plus sur les [modes d’application](../cli/set-mode.md).

## file d&#39;attente

Les configurations de file d’attente de messages sont disponibles dans ce nœud.

```conf
'queue' => [
  'topics' => [
    'customer.created' => [publisher="default-rabitmq"],
    'order.created' => [publisher="default-rabitmq"],
  ]
]
```

En savoir plus sur [File d’attente des messages][message-queue].

## ressource

Les paramètres de configuration des ressources sont disponibles dans ce nœud.

```conf
'resource' => [
  'default_setup' => [
    'connection' => 'default'
  ]
]
```

## séance

Les configurations de session sont stockées dans le nœud `session`.

```conf
'session' => [
  'save' => 'files'
],
```

En savoir plus sur [Session](../storage/sessions.md).

## x-frame-options

L’en-tête x-frame-options peut être configuré à l’aide de ce nœud.

```conf
'x-frame-options' => 'SAMEORIGIN'
```

En savoir plus sur [x-frame-options](../security/xframe-options.md).

## système

En utilisant ce nœud, Commerce verrouille les valeurs de configuration dans le fichier `env.php`, puis désactive le champ dans l’administration.

```conf
'system' => [
  'default' => [
    'web' => [
      'secure' => [
          'base_url' => 'https://magento.test/'
      ]
    ]
  ]
```

En savoir plus dans [env-php-config-set](../cli/set-configuration-values.md).

<!-- Link definitions -->

[message-queue]: https://developer.adobe.com/commerce/php/development/components/message-queues/


## Ajouter des variables à la configuration du fichier

Vous pouvez définir ou remplacer chaque option de configuration (variable avec valeur) par des variables d’environnement au niveau du système d’exploitation (SE).

La configuration `env.php` est stockée dans un tableau avec des niveaux imbriqués. Pour convertir un chemin de tableau imbriqué en chaîne pour les variables d’environnement du système d’exploitation, concaténez chaque clé du chemin avec deux caractères de soulignement `__`, mis en majuscules et précédés du préfixe `MAGENTO_DC_`.

Par exemple, convertissons le gestionnaire d’enregistrement de session de `env.php` configuration en une variable d’environnement de système d’exploitation.

```conf
'session' => [
  'save' => 'files'
],
```

Concaténées avec des clés `__` et mises en majuscules deviendront `SESSION__SAVE`.

Ensuite, nous lui ajoutons le préfixe `MAGENTO_DC_` pour obtenir le `MAGENTO_DC_SESSION__SAVE` de nom de la variable d’environnement du système d’exploitation obtenu.

```shell
export MAGENTO_DC_SESSION__SAVE=files
```

Autre exemple : convertissons un chemin d’accès d’option de configuration de `env.php` scalaire.

```conf
'x-frame-options' => 'SAMEORIGIN'
```

>[!INFO]
>
>Bien que le nom de la variable doive être mis en majuscule, la valeur respecte la casse et doit être conservée tel que documenté.

Nous le mettons simplement en majuscules et le précédons de `MAGENTO_DC_` pour recevoir le `MAGENTO_DC_X-FRAME-OPTIONS` final du nom de variable d&#39;environnement du système d&#39;exploitation.

```shell
export MAGENTO_DC_X-FRAME-OPTIONS=SAMEORIGIN
```

>[!INFO]
>
>Notez que le contenu `env.php` aura la priorité sur les variables d’environnement du système d’exploitation.

## Remplacer la configuration du fichier par des variables

Pour remplacer les options de configuration de `env.php` existantes par une variable d’environnement de système d’exploitation, l’élément de tableau de la configuration doit être codé JSON et défini comme une valeur de la variable de système d’exploitation `MAGENTO_DC__OVERRIDE`.

Lorsque `MAGENTO_DC__OVERRIDE` est défini, le framework Commerce contourne les valeurs correspondantes dans le fichier `env.php` et lit la configuration directement à partir de la variable d’environnement. Les valeurs du fichier `env.php` restent inchangées, mais sont ignorées pour les sections de configuration remplacées.

>[!IMPORTANT]
>
>La variable `MAGENTO_DC__OVERRIDE` contourne complètement les sections de configuration spécifiées dans le fichier `env.php`. Ce comportement est différent de celui des variables de `MAGENTO_DC_` individuelles, qui ont une priorité inférieure aux valeurs du fichier `env.php`.

Si vous devez remplacer plusieurs options de configuration, assemblez-les toutes dans un seul tableau avant l’encodage JSON.

Par exemple, remplaçons les configurations `env.php` suivantes :

```conf
'session' => [
  'save' => 'files'
],
'x-frame-options' => 'SAMEORIGIN'
```

Le texte codé JSON du tableau ci-dessus serait .
`{"session":{"save":"files"},"x-frame-options":"SAMEORIGIN"}`.

Définissez-la désormais comme valeur de la variable du système d’exploitation `MAGENTO_DC__OVERRIDE`.

```shell
export MAGENTO_DC__OVERRIDE='{"session":{"save":"files"},"x-frame-options":"SAMEORIGIN"}'
```

>[!INFO]
>
>Assurez-vous que le tableau codé JSON est correctement cité et/ou placé dans une séquence d’échappement si nécessaire, pour empêcher le système d’exploitation de corrompre la chaîne codée.