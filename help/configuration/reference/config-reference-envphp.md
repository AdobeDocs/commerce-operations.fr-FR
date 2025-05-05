---
title: référence env.php
description: Consultez la liste des valeurs du fichier env.php.
exl-id: cf02da8f-e0de-4f0e-bab6-67ae02e9166f
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '693'
ht-degree: 0%

---

# référence env.php

Le `env.php` fichier contient les sections suivantes :

| Nom | Description |
|-------------------------------|-----------------------------------------------------------------|
| `backend` | Paramètres de la zone Admin |
| `cache` | Configuration de la page redis et du cache par défaut |
| `cache_types` | Paramètres de stockage du cache |
| `consumers_wait_for_messages` | Configuration du traitement des messages par les consommateurs à partir de la file d’attente des messages |
| `cron` | Activation ou désactivation des tâches cron |
| `crypt` | Clé de chiffrement des fonctions cryptographiques |
| `db` | Paramètres de connexion à la base de données |
| `default_connection` | Connexion par défaut des files de messages |
| `directories` | Paramètres de mappage des répertoires Commerce |
| `downloadable_domains` | Liste des domaines téléchargeables |
| `install` | La date d&#39;installation |
| `lock` | Verrouillage des paramètres du fournisseur |
| `MAGE_MODE` | Le [mode application](../bootstrap/application-modes.md) |
| `queue` | [Paramètres des files d’attente de](../queues/manage-message-queues.md) messages |
| `resource` | Mappage du nom de la ressource à une connexion |
| `session` | Données de stockage de session |
| `system` | Désactive le champ à modifier dans l&#39;administrateur. |
| `x-frame-options` | Paramètre pour [x-frame-options][x-frame-options] |

## backend

Configurez frontName **&#x200B;**&#x200B;pour l’URL d’administration Commerce à l’aide `backend` du nœud dans env.php.

```conf
'backend' => [
  'frontName' => 'admin'
]
```

## cache

Configurez la page redis et la mise en cache par défaut à l’aide `cache` du nœud dans le `env.php` fichier.

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

En savoir plus sur la [configuration](../cache/redis-pg-cache.md) Redis.

## cache_types

Toutes les configurations de types de cache sont disponibles à partir de ce noeud.

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

En savoir plus sur les différents [types de cache](../cli/manage-cache.md).

## consumer_wait_for_messages

Indiquez si les consommateurs doivent continuer à interroger les messages si le nombre de messages traités est inférieur à la valeur `max_messages`. La valeur par défaut est `1`.

```conf
'queue' => [
    'consumers_wait_for_messages' => 1
]
```

Les options disponibles sont les suivantes :

- `1` : les consommateurs continuent à traiter les messages de la file d’attente des messages jusqu’à atteindre la valeur `max_messages` spécifiée dans le fichier `env.php` avant de fermer la connexion TCP et d’interrompre le processus client. Si la file d’attente se vide avant d’atteindre la valeur `max_messages`, le consommateur attend que d’autres messages arrivent.

  Nous vous recommandons ce paramètre pour les grands vendeurs, car un flux de messages constant est attendu et les retards de traitement ne sont pas souhaitables.

- `0` : les consommateurs traitent les messages disponibles dans la file d’attente, ferment la connexion TCP et s’arrêtent. Les consommateurs n’attendent pas que des messages supplémentaires entrent dans la file d’attente, même si le nombre de messages traités est inférieur à la valeur `max_messages` spécifiée dans le fichier `env.php`. Cela peut aider à éviter les problèmes liés aux tâches cron causés par de longs délais dans le traitement de la file d’attente des messages.

  Nous recommandons ce paramètre pour les petits commerçants qui ne s’attendent pas à un flux de messages constant et qui préfèrent conserver les ressources informatiques en exchange pour les retards de traitement mineurs lorsqu’il ne peut pas y avoir de messages pendant des jours.

## cron

Activez ou désactivez les tâches cron pour l’application Commerce. Par défaut, les tâches cron sont activées. Pour les désactiver, ajoutez la configuration `cron` au fichier `env.php` et définissez la valeur sur `0`.

```conf
'cron' => [
  'enabled' => 0
]
```

>[!WARNING]
>
>Soyez prudent lorsque vous désactivez les tâches cron. Lorsqu’elles sont désactivées, les processus essentiels requis par l’application Commerce ne s’exécuteront pas.

En savoir plus sur [Crons](../cli/configure-cron-jobs.md).

## crypte

Commerce utilise une clé de chiffrement pour protéger les mots de passe et d’autres données sensibles. Cette clé est générée pendant le processus d’installation.

```conf
'crypt' => [
  'key' => '63d409380ccb1182bfb27c231b732f05'
]
```

Pour en savoir plus sur [la clé de chiffrement](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/encryption-key), consultez le _guide de l’utilisateur de Commerce_.

## db

Toutes les configurations de base de données sont disponibles dans ce noeud.

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

Définit la connexion par défaut pour les files d’attente de messages. La valeur peut être `db`, `amqp` ou un système de file d’attente personnalisé comme `redismq`. Si vous spécifiez une valeur autre que `db`, le logiciel de la file d’attente des messages doit d’abord être installé et configuré. Sinon, les messages ne seront pas traités correctement.

```conf
'queue' => [
    'default_connection' => 'amqp'
]
```

Si `queue/default_connection` est spécifié dans le fichier `env.php` du système, cette connexion est utilisée pour toutes les files d’attente de messages à travers le système, sauf si une connexion spécifique est définie dans un fichier `queue_topology.xml`, `queue_publisher.xml` ou `queue_consumer.xml`.
Par exemple, si `queue/default_connection` est `amqp` dans `env.php` mais qu’une connexion `db` est spécifiée dans les fichiers XML de configuration de file d’attente d’un module, le module utilisera MySQL comme courtier de messages.

## répertoires

Options de mappage de répertoire facultatives qui doivent être définies lorsque le serveur Web est configuré pour servir l’application Commerce à partir du `/pub` répertoire pour [une sécurité](../../installation/tutorials/docroot.md) améliorée.

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

## install

Date d’installation de l’application Commerce.

```conf
'install' => [
  'date' => 'Tue, 23 Apr 2019 09:31:07 +0000'
]
```

## serrure

Les paramètres du fournisseur de verrouillage sont configurés à l’aide du `lock` nœud.

En savoir plus sur [la configuration du](../../installation/tutorials/lock-provider.md) fournisseur de verrouillage.

## MAGE_MODE

Le mode de déploiement peut être configuré dans ce noeud.

```conf
'MAGE_MODE' => 'developer'
```

En savoir plus sur les [modes d&#39;application](../cli/set-mode.md).

## queue

Les configurations de la file d’attente des messages sont disponibles dans ce noeud.

```conf
'queue' => [
  'topics' => [
    'customer.created' => [publisher="default-rabitmq"],
    'order.created' => [publisher="default-rabitmq"],
  ]
]
```

En savoir plus sur [Message Queue][message-queue].

## resource

Les paramètres de configuration des ressources sont disponibles dans ce noeud.

```conf
'resource' => [
  'default_setup' => [
    'connection' => 'default'
  ]
]
```

## session

Les configurations de session sont stockées dans le noeud `session` .

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

En utilisant ce noeud, Commerce verrouille les valeurs de configuration dans le fichier `env.php`, puis désactive le champ dans l’administrateur.

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
