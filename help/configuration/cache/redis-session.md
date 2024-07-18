---
title: Utilisation de Redis pour le stockage de session
description: Découvrez comment configurer Redis pour le stockage de session.
feature: Configuration, Cache
exl-id: f93f500d-65b0-4788-96ab-f1c3d2d40a38
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '712'
ht-degree: 1%

---

# Utilisation de Redis pour le stockage de session

>[!IMPORTANT]
>
>Vous devez [installer Redis](config-redis.md#install-redis) avant de continuer.


Commerce fournit désormais des options de ligne de commande pour configurer l’enregistrement de session Redis. Dans les versions précédentes, vous aviez modifié le fichier `<Commerce install dir>app/etc/env.php`. La ligne de commande fournit la validation et est la méthode de configuration recommandée, mais vous pouvez toujours modifier le fichier `env.php`.

Exécutez la commande `setup:config:set` et spécifiez des paramètres spécifiques à Redis.

```bash
bin/magento setup:config:set --session-save=redis --session-save-redis-<parameter_name>=<parameter_value>...
```

where

`--session-save=redis` active le stockage de session Redis. Si cette fonctionnalité a déjà été activée, omettez ce paramètre.

`--session-save-redis-<parameter_name>=<parameter_value>` est une liste de paires paramètre/valeur qui configurent le stockage de session :

| Paramètre de ligne de commande | Nom du paramètre | Signification | Valeur par défaut |
|--- |--- |--- |--- |
| session-save-redis-host | hôte | Nom d’hôte complet, adresse IP ou chemin d’accès absolu si vous utilisez des sockets UNIX. | localhost |
| session-save-redis-port | port | Port d’écoute du serveur Redis. | 6379 |
| session-save-redis-password | password | Indique un mot de passe si votre serveur Redis doit être authentifié. | empty |
| session-save-redis-timeout | timeout | Timeout de connexion, en secondes. | 2,5 |
| session-save-redis-persistent-id | persistent_identifier | Chaîne unique pour activer les connexions persistantes (par exemple, sess-db0).<br>[Problèmes connus avec phpredis et php-fpm](https://github.com/phpredis/phpredis/issues/70). |
| session-save-redis-db | base | Numéro de base de données Redis unique, recommandé pour éviter toute perte de données.<br><br>**Important** : Si vous utilisez Redis pour plusieurs types de mise en cache, les numéros de la base de données doivent être différents. Il est recommandé d’attribuer le numéro de base de données de mise en cache par défaut à 0, le numéro de base de données de mise en cache de page à 1 et le numéro de base de données de stockage de session à 2. | 0 |
| session-save-redis-compression-threshold | compression_threshold | Définissez cette variable sur 0 pour désactiver la compression (recommandé lorsque `suhosin.session.encrypt = On`).<br>[Problème connu avec des chaînes de plus de 64 Ko](https://github.com/colinmollenhour/Cm_Cache_Backend_Redis/issues/18). | 2048 |
| session-save-redis-compression-lib | compression_library | Options : gzip, lzf, lz4 ou snappy. | gzip |
| session-save-redis-log-level | log_level | Définissez sur l’un des éléments suivants, répertoriés dans l’ordre entre au moins verbose et la plupart des verbose :<ul><li>0 (urgence : seules les erreurs les plus graves)<li>1 (alerte : action immédiate requise)<li>2 (critique : composant d’application indisponible)<li>3 (erreur : erreurs d’exécution, non critiques mais devant être surveillées)<li>4 (avertissement : informations supplémentaires, recommandé)<li>5 (avis : état normal mais significatif)<li>6 (informations : messages d’information)<li>7 (débogage : informations les plus complètes à des fins de développement ou de test uniquement)</ul> | 1 |
| session-save-redis-max-concurrency | max_concurrency | Nombre maximal de processus pouvant attendre un verrouillage sur une session. Pour les grappes de production volumineuses, définissez cette valeur sur au moins 10 % du nombre de processus PHP. | 6 |
| session-save-redis-break-after-frontend | break_after_frontend | Nombre de secondes à attendre avant d’essayer de rompre le verrouillage de la session front-end (c’est-à-dire storefront). | 5 |
| session-save-redis-break-after-adminhtml | break_after_adminhtml | Nombre de secondes à attendre avant de tenter de rompre le verrouillage pour une session adminhtml (c’est-à-dire admin). | 30 |
| session-save-redis-first-lifetime | first_lifetime | Durée de vie, en secondes, de la session pour les non-robots lors de la première écriture, ou utilisez 0 pour désactiver. | 600 |
| session-save-redis-bot-first-lifetime | bot_first_lifetime | Durée de vie, en secondes, de la session pour les robots lors de la première écriture, ou utilisez 0 pour désactiver. | 60 |
| session-save-redis-bot-lifetime | bot_lifetime | Durée de vie, en secondes, de la session pour les robots lors des écritures suivantes, ou utilisez 0 pour désactiver. | 7200 |
| session-save-redis-disable-locking | disable_locking | Désactivez entièrement le verrouillage de session. | 0 (false) |
| session-save-redis-min-lifetime | min_lifetime | Durée de session minimale, en secondes. | 60 |
| session-save-redis-max-lifetime | max_lifetime | Durée maximale de la session, en secondes. | 2592000 (720 heures) |
| session-save-redis-sentinel-master | sentinel_master | Nom principal Redis Sentinel | empty |
| session-save-redis-sentinel-servers | sentinel_servers | Liste des serveurs Redis Sentinel, séparés par des virgules | empty |
| session-save-redis-sentinel-verify-master | sentinel_verify_master | Vérification de l’indicateur d’état principal Redis Sentinel | 0 (false) |
| session-save-redis-sentinel-connect-retries | sentinel_connect_retries | Reprises de connexion pour les envois | 5 |

## Exemple

L’exemple suivant définit Redis comme entrepôt de données de session, définit l’hôte sur `127.0.0.1`, définit le niveau de journal sur 4 et définit le numéro de base de données sur 2. Tous les autres paramètres sont définis sur la valeur par défaut.

```bash
bin/magento setup:config:set --session-save=redis --session-save-redis-host=127.0.0.1 --session-save-redis-log-level=4 --session-save-redis-db=2
```

### Résultat

Commerce ajoute des lignes similaires à celles-ci à `<magento_root>app/etc/env.php` :

```php
    'session' =>
    array (
      'save' => 'redis',
      'redis' =>
      array (
        'host' => '127.0.0.1',
        'port' => '6379',
        'password' => '',
        'timeout' => '2.5',
        'persistent_identifier' => '',
        'database' => '2',
        'compression_threshold' => '2048',
        'compression_library' => 'gzip',
        'log_level' => '4',
        'max_concurrency' => '6',
        'break_after_frontend' => '5',
        'break_after_adminhtml' => '30',
        'first_lifetime' => '600',
        'bot_first_lifetime' => '60',
        'bot_lifetime' => '7200',
        'disable_locking' => '0',
        'min_lifetime' => '60',
        'max_lifetime' => '2592000'
      )
    ),
```

>[!INFO]
>
>TTL pour les enregistrements de session utilise la valeur de durée de vie du cookie, qui est configurée dans l’Admin. Si la durée de vie du cookie est définie sur 0 (la valeur par défaut est 3 600), les sessions de redirection expirent en secondes spécifiées en min_lifetime (la valeur par défaut est 60). Cette incohérence est due aux différences dans la manière dont les cookies de session et de redis interprètent une valeur de durée de vie de 0. Si ce comportement n’est pas souhaité, augmentez la valeur de min_lifetime .

## Vérification de la connexion Redis

Pour vérifier que Redis et Commerce fonctionnent ensemble, connectez-vous au serveur exécutant Redis, ouvrez un terminal et utilisez la commande Redis monitor ou la commande ping.

### Redis monitor, commande

```bash
redis-cli monitor
```

Exemple de sortie session-storage :

```
1476824834.187250 [0 127.0.0.1:52353] "select" "0"
1476824834.187587 [0 127.0.0.1:52353] "hmget" "sess_sgmeh2k3t7obl2tsot3h2ss0p1" "data" "writes"
1476824834.187939 [0 127.0.0.1:52353] "expire" "sess_sgmeh2k3t7obl2tsot3h2ss0p1" "1200"
1476824834.257226 [0 127.0.0.1:52353] "select" "0"
1476824834.257239 [0 127.0.0.1:52353] "hmset" "sess_sgmeh2k3t7obl2tsot3h2ss0p1" "data" "_session_validator_data|a:4:{s:11:\"remote_addr\";s:12:\"10.235.34.14\";s:8:\"http_via\";s:0:\"\";s:20:\"http_x_forwarded_for\";s:0:\"\";s:15:\"http_user_agent\";s:115:\"Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/53.0.2785.143 Safari/537.36\";}_session_hosts|a:1:{s:12:\"10.235.32.10\";b:1;}admin|a:0:{}default|a:2:{s:9:\"_form_key\";s:16:\"e331ugBN7vRjGMgk\";s:12:\"visitor_data\";a:3:{s:13:\"last_visit_at\";s:19:\"2016-10-18 21:06:37\";s:10:\"session_id\";s:26:\"sgmeh2k3t7obl2tsot3h2ss0p1\";s:10:\"visitor_id\";s:1:\"9\";}}adminhtml|a:0:{}customer_base|a:1:{s:20:\"customer_segment_ids\";a:1:{i:1;a:0:{}}}checkout|a:0:{}" "lock" "0"
... more ...
```

### Redis ping, commande

```bash
redis-cli ping
```

`PONG` doit être la réponse.

Si les deux commandes ont réussi, Redis est configuré correctement.

### Inspection des données compressées

Pour examiner les données de session compressées et le cache de page, [RESP.app](https://flathub.org/apps/details/app.resp.RESP) prend en charge la décompression automatique du cache de page et de session Commerce 2 et affiche les données de session PHP sous une forme lisible par l’utilisateur.
