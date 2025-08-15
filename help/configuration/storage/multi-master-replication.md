---
title: Réplication de la base de données
description: Découvrez les avantages de la configuration de la réplication de base de données.
recommendations: noCatalog
exl-id: 0e41dca0-5a23-4d12-96fe-241c511ae366
source-git-commit: af45ac46afffeef5cd613628b2a98864fd7da69b
workflow-type: tm+mt
source-wordcount: '166'
ht-degree: 0%

---

# Réplication de la base de données

{{ee-only}}

{{deprecate-split-db}}

La configuration de la réplication de base de données présente les avantages suivants :

- Sauvegarde des données
- Permet l&#39;analyse des données sans affecter la base de données principale
- Évolutivité

Les bases de données MySQL se répliquent de manière asynchrone, ce qui signifie que les esclaves n’ont pas besoin d’être connectés en permanence pour recevoir les mises à jour du maître.

## Configuration de la réplication de la base de données

Une discussion approfondie sur la réplication de base de données dépasse le cadre de ce guide. Pour le configurer, vous pouvez consulter une ressource telle que :

- [Documentation MySQL](https://dev.mysql.com/doc/refman/5.6/en/replication.html)
- [Configuration de la réplication esclave de Principal dans MySQL (digitalocean)](https://www.digitalocean.com/community/tutorials/how-to-set-up-replication-in-mysql)

Commerce fournit des exemples de configuration MySQL pour vos bases de données esclaves. Une configuration simple est fournie avec le `ResourceConnections` de classe `README.md`.

Les éléments suivants sont plus avancés et sont fournis uniquement à titre d’information :

```php
   return array (
      //...
      'db' =>
         array (
            'connection' =>
               array (
                  'indexer' =>
                     array (
                        'host' => 'default-master-host',
                        'dbname' => 'magento',
                        'username' => 'magento',
                        'password' => 'magento',
                        'active' => '1',
                        'persistent' => NULL,
                     ),
                  'default' =>
                     array (
                        'host' => 'default-master-host',
                        'dbname' => 'magento',
                        'username' => 'magento',
                        'password' => 'magento',
                        'active' => '1',
                     ),
                  'checkout' =>
                     array (
                        'host' => 'checkout-master-host',
                        'dbname' => 'checkout',
                        'username' => 'magento',
                        'password' => 'magento',
                        'model' => 'mysql4',
                        'engine' => 'innodb',
                        'initStatements' => 'SET NAMES utf8;',
                        'active' => '1',
                     ),
                  'sales' =>
                     array (
                        'host' => 'sales-master-host',
                        'dbname' => 'sales',
                        'username' => 'magento',
                        'password' => 'magento',
                        'model' => 'mysql4',
                        'engine' => 'innodb',
                        'initStatements' => 'SET NAMES utf8;',
                        'active' => '1',
                     ),
               ),
            'slave_connection' =>
               array (
                  'default' =>
                     array (
                        'host' => 'default-slave-host',
                        'dbname' => 'magento',
                        'username' => 'read_only',
                        'password' => 'password',
                        'active' => '1',
                     ),
                  'checkout' =>
                     array (
                        'host' => 'checkout-slave-host',
                        'dbname' => 'checkout',
                        'username' => 'read_only',
                        'password' => 'password',
                        'model' => 'mysql4',
                        'engine' => 'innodb',
                        'initStatements' => 'SET NAMES utf8;',
                        'active' => '1',
                     ),
                  'sales' =>
                     array (
                        'host' => 'sales-slave-host',
                        'dbname' => 'sales',
                        'username' => 'read_only',
                        'password' => 'password',
                        'model' => 'mysql4',
                        'engine' => 'innodb',
                        'initStatements' => 'SET NAMES utf8;',
                        'active' => '1',
                     ),
                  ),
               'table_prefix' => '',
   ),
   //.......
```

## Amélioration des performances

Pour améliorer les performances de la réplication maître-esclave, vous pouvez filtrer certaines tables sur les instances esclaves. Nous vous recommandons de filtrer toutes les tables temporaires avec des `search\_tmp\_%` de modèle de nom utilisées pour la recherche catalogue.

Pour ce faire, ajoutez la ligne suivante à votre fichier `my.cnf` sur vos instances esclaves :

```conf
replicate-wild-ignore-table=%.search\_tmp\_%
```
