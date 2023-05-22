---
title: Réplication des bases de données
description: Découvrez les avantages de la configuration de la réplication de base de données.
recommendations: noCatalog
exl-id: 0e41dca0-5a23-4d12-96fe-241c511ae366
source-git-commit: af45ac46afffeef5cd613628b2a98864fd7da69b
workflow-type: tm+mt
source-wordcount: '175'
ht-degree: 0%

---

# Réplication des bases de données

{{ee-only}}

{{deprecate-split-db}}

La configuration de la réplication de base de données offre les avantages suivants :

- Sauvegarde des données
- Active l’analyse des données sans affecter la base de données principale
- Évolutivité

Les bases de données MySQL se répliquent de manière asynchrone, ce qui signifie que les Secondaires n’ont pas besoin d’être connectés de manière permanente pour recevoir les mises à jour du maître.

## Configuration de la réplication de base de données

Ce guide ne vise pas à approfondir la question de la réplication des bases de données. Pour le configurer, vous pouvez consulter une ressource du type :

- [Documentation MySQL](https://dev.mysql.com/doc/refman/5.6/en/replication.html)
- [Comment configurer la réplication de Secondaire par Principal dans MySQL (digitalsea)](https://www.digitalocean.com/community/tutorials/how-to-set-up-replication-in-mysql)

Commerce fournit des exemples de configurations MySQL pour vos bases de données de Secondaire. Une configuration simple est fournie avec la variable `ResourceConnections` class `README.md`.

Les éléments suivants sont plus avancés et ne sont fournis que pour vos informations :

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

Pour améliorer les performances de la réplication du Secondaire maître, vous pouvez filtrer certains tableaux sur des instances de Secondaire. Nous vous recommandons de filtrer toutes les tables temporaires avec un modèle de nom. `search\_tmp\_%` qui sont utilisés pour la recherche catalogue.

Pour ce faire, ajoutez la ligne suivante à votre `my.cnf` sur vos instances de Secondaire :

```conf
replicate-wild-ignore-table=%.search\_tmp\_%
```
