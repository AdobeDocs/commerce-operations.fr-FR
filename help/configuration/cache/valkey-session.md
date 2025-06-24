---
title: Utiliser Valkey pour le stockage de session
description: Découvrez comment configurer Valkey pour le stockage de session.
feature: Configuration, Cache
source-git-commit: 1850301e0b7f1abbc54613209940dd63d16ef145
workflow-type: tm+mt
source-wordcount: '664'
ht-degree: 1%

---

# Utiliser Valkey pour le stockage de session

>[!IMPORTANT]
>
>Vous devez [installer Valkey](config-valkey.md#install-valkey) avant de continuer.

Adobe Commerce fournit des options de ligne de commande pour configurer le stockage de session Valkey.

Exécutez la commande `setup:config:set` et spécifiez des paramètres spécifiques à Valkey.

```bash
bin/magento setup:config:set --session-save=valkey --session-save-valkey-<parameter_name>=<parameter_value>...
```

- `--session-save=valkey` active le stockage de session Valkey. Si cette fonctionnalité est déjà activée, omettez ce paramètre.

- `--session-save-valkey-<parameter_name>=<parameter_value>` une liste de paires paramètre/valeur qui configurent le stockage de session :

| Paramètre de ligne de commande | Nom du paramètre | Signification | Valeur par défaut |
|----------------------------------------------|--- |---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--- |
| session-save-valkey-host | hôte | Nom d’hôte complet, adresse IP ou chemin absolu si vous utilisez des sockets UNIX. | localhost |
| session-save-valkey-port | port | Port d&#39;écoute du serveur Valkey. | 6379 |
| session-save-valkey-password | mot de passe | Indique un mot de passe si votre serveur Valkey requiert une authentification. | vide |
| session-save-valkey-timeout | timeout | Timeout de connexion, en secondes. | 2,5 |
| session-save-valkey-persistent-id | persistent_identifier | Chaîne unique pour activer les connexions persistantes (par exemple, sess-db0).<br>[Problèmes connus liés à phpredis et php-fpm](https://github.com/phpredis/phpredis/issues/70). |
| session-save-value-db | de données | Numéro de base de données Valkey unique, recommandé pour se protéger contre la perte de données.<br><br>**Important** : si vous utilisez Valkey pour plusieurs types de mise en cache, les numéros de base de données doivent être différents. Il est recommandé d’attribuer le numéro de base de données de mise en cache par défaut à `0`, le numéro de base de données de mise en cache de page à `1` et le numéro de base de données de stockage de session à `2`. | 0 |
| session-save-valkey-compression-threshold | compression_seuil | Définissez cette valeur sur `0` pour désactiver la compression (recommandé lorsque `suhosin.session.encrypt = On`). | 2048 |
| session-save-valkey-compression-lib | compression_library | Options : gzip, lzf, lz4 ou snappy. | gzip |
| session-save-valkey-log-level | log_level | Définissez sur l’une des options suivantes, répertoriées dans l’ordre du moins détaillé au plus détaillé :<ul><li>0 (urgence : seulement les erreurs les plus graves)<li>1 (alerte : action immédiate requise)<li>2 (critique : composant d’application non disponible)<li>3 (erreur : erreurs d’exécution, non critiques, mais doivent être surveillées)<li>4 (avertissement : informations supplémentaires, recommandé)<li>5 (avis : état normal mais significatif)<li>6 (info : messages informatifs)<li>7 (débogage : le plus d’informations pour le développement ou le test uniquement)</ul> | 1 |
| session-save-valkey-max-concurrency | max_concurrency | Nombre maximum de processus pouvant attendre un verrouillage sur une session. Pour les clusters de production volumineux, définissez cette valeur sur au moins 10 % du nombre de processus PHP. | 6 |
| session-save-value-break-after-frontend | break_after_frontend | Nombre de secondes à attendre avant d’essayer d’interrompre le verrouillage d’une session frontale (c’est-à-dire storefront). | 5 |
| session-save-value-break-after-adminhtml | break_after_adminhtml | Nombre de secondes à attendre avant d’essayer d’interrompre le verrouillage d’une session adminhtml (c’est-à-dire Admin). | 30 |
| session-save-value-first-life | first_life | Durée de vie, en secondes, de la session pour les non-robots lors de la première écriture ou utilisez `0` pour la désactiver. | 600 |
| session-save-value-bot-first-life | bot_first_life | Durée de vie, en secondes, de la session des robots lors de la première écriture ou utilisez `0` pour la désactiver. | 60 |
| session-save-valkey-bot-life | bot_life | Durée de vie, en secondes, de la session des robots lors des écritures suivantes, ou utilisez `0` pour la désactiver. | 7200 |
| session-save-valkey-disable-lock | disable_lock | Désactivez entièrement le verrouillage de session. | 0 (faux) |
| session-save-value-min-life | min_life | Durée de vie minimale d’une session, en secondes. | 60 |
| session-save-valkey-max-life | max_life | Durée de vie maximale de la session, en secondes. | 2592000 (720 heures) |
| session-save-valkey-sentinel-master | sentinelle_master | Nom de maître Valkey Sentinel. | vide |
| session-save-valkey-sentinel-servers | sentinel_servers | Liste des serveurs Sentinel Valkey, séparés par des virgules. | vide |
| session-save-valkey-sentinel-verify-master | sentinelle_verify_master | Vérifiez l&#39;indicateur de statut principal Valkey Sentinel. | 0 (faux) |
| session-save-valkey-sentinel-connect-retries | sentinel_connect_retries | Reprises de connexion pour les sentinelles. | 5 |

## Exemple

L’exemple suivant définit Valkey comme magasin de données de session, définit l’hôte sur `127.0.0.1`, définit le niveau de journal sur `4` et définit le numéro de base de données sur `2`. Tous les autres paramètres sont définis sur la valeur par défaut.

```bash
bin/magento setup:config:set --session-save=valkey --session-save-valkey-host=127.0.0.1 --session-save-valkey-log-level=4 --session-save-valkey-db=2
```

### Résultat

Commerce ajoute des lignes similaires à ce qui suit à `<magento_root>app/etc/env.php` :

```php
'session' => [
    'save' => 'valkey',
    'redis' => [
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
        'max_lifetime' => '2592000',
    ],
],
```

>[!INFO]
>
>La durée de vie des enregistrements de session utilise la valeur de la durée de vie du cookie , qui est configurée dans l’administration. Si Cookie Lifetime est défini sur `0` (la valeur par défaut est `3600`), les sessions Valkey expirent dans le nombre de secondes spécifié dans min_life (la valeur par défaut est `60`). Cette incohérence est due à des différences dans la façon dont les cookies Valkey et de session interprètent une valeur de durée de vie de `0`. Si ce comportement n&#39;est pas souhaité, augmentez la valeur de min_life.

## Vérifier la connexion Valkey

Pour vérifier que Valkey et Commerce fonctionnent correctement ensemble, connectez-vous au serveur sur lequel Valkey est exécuté, ouvrez un terminal et utilisez la commande `valkey-cli monitor` ou la commande `redis-cli ping`.

### Commande de moniteur Valkey

```bash
valkey-cli monitor
```

Exemple de sortie de stockage de session :

```
1476824834.187250 [0 127.0.0.1:52353] "select" "0"
1476824834.187587 [0 127.0.0.1:52353] "hmget" "sess_sgmeh2k3t7obl2tsot3h2ss0p1" "data" "writes"
1476824834.187939 [0 127.0.0.1:52353] "expire" "sess_sgmeh2k3t7obl2tsot3h2ss0p1" "1200"
1476824834.257226 [0 127.0.0.1:52353] "select" "0"
1476824834.257239 [0 127.0.0.1:52353] "hmset" "sess_sgmeh2k3t7obl2tsot3h2ss0p1" "data" "_session_validator_data|a:4:{s:11:\"remote_addr\";s:12:\"10.235.34.14\";s:8:\"http_via\";s:0:\"\";s:20:\"http_x_forwarded_for\";s:0:\"\";s:15:\"http_user_agent\";s:115:\"Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/53.0.2785.143 Safari/537.36\";}_session_hosts|a:1:{s:12:\"10.235.32.10\";b:1;}admin|a:0:{}default|a:2:{s:9:\"_form_key\";s:16:\"e331ugBN7vRjGMgk\";s:12:\"visitor_data\";a:3:{s:13:\"last_visit_at\";s:19:\"2016-10-18 21:06:37\";s:10:\"session_id\";s:26:\"sgmeh2k3t7obl2tsot3h2ss0p1\";s:10:\"visitor_id\";s:1:\"9\";}}adminhtml|a:0:{}customer_base|a:1:{s:20:\"customer_segment_ids\";a:1:{i:1;a:0:{}}}checkout|a:0:{}" "lock" "0"
... more ...
```

### Commande ping Valkey

```bash
valkey-cli ping
```

La réponse attendue est : `PONG`.

Si les deux commandes ont réussi, Valkey est correctement configuré.

### Inspection des données compressées

Pour inspecter les données de session compressées et le cache de page, le [RESP.app](https://flathub.org/apps/app.resp.RESP) prend en charge la décompression automatique de la session Commerce 2 et du cache de page et affiche les données de session PHP dans un format lisible par l&#39;utilisateur.
