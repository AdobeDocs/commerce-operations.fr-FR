---
title: Configuration de la mémoire mise en cache sur Ubuntu
description: Installez et configurez memcached sur Ubuntu.
feature: Configuration, Cache, Storage
exl-id: 831193d2-3e81-472c-9b87-78a8d52959b4
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '440'
ht-degree: 0%

---

# Configuration de la mémoire mise en cache sur Ubuntu

Cette section fournit des instructions pour installer memcached sur Ubuntu.

>[!INFO]
>
>Adobe recommande d’utiliser la version 3.0.5 ou ultérieure de memcached.

Comme PHP ne prend pas en charge le memcache, vous devez installer une extension pour que PHP l’utilise. Deux extensions PHP sont disponibles et il est important de décoder laquelle utiliser :

- `memcache` (_no d_) : extension plus ancienne mais populaire qui n’est pas gérée régulièrement.
L&#39;extension `memcache` actuellement _ne fonctionne pas_ avec PHP 7. Voir la [documentation PHP pour memcache](https://www.php.net/manual/en/book.memcache.php).

  Le nom exact est `php5-memcache` pour Ubuntu.

- `memcached` (_avec un`d`_) : extension plus récente et plus gérée compatible avec PHP 7. Voir la [documentation PHP pour memcached](https://www.php.net/manual/en/book.memcached.php).

  Le nom exact est `php5-memcached` pour Ubuntu.

## Installation et configuration de la mémoire mise en cache sur Ubuntu

**Pour installer et configurer la mémoire mise en cache sur Ubuntu** :

1. En tant qu’utilisateur disposant de droits `root`, saisissez la commande suivante :

   ```bash
   apt-get -y update
   ```

   ```bash
   apt-get -y install php5-memcached memcached
   ```

1. Modifiez le paramètre de configuration de la mémoire mise en cache pour `CACHESIZE` et `-l` :

   1. Ouvrez `/etc/memcached.conf` dans un éditeur de texte.
   1. Recherchez le paramètre `-m` .
   1. Remplacez sa valeur par au moins `1GB`
   1. Recherchez le paramètre `-l` .
   1. Remplacez sa valeur par `127.0.0.1` ou `localhost`
   1. Enregistrez vos modifications dans `memcached.conf` et quittez l’éditeur de texte.
   1. Redémarrez le memcached.

      ```bash
      service memcached restart
      ```

1. Redémarrez votre serveur web.

   Pour Apache, `service apache2 restart`

1. Passez à la section suivante.

## Vérifier le fonctionnement de la mémoire mise en cache avant l’installation du Magento

Adobe recommande de tester la mémoire mise en cache pour s’assurer qu’elle fonctionne avant d’installer Commerce. Cette opération ne prend que quelques minutes et peut simplifier ultérieurement le dépannage.

### Vérifier que la mémoire mise en cache est reconnue par le serveur web

Pour vérifier que memcached est reconnu par le serveur web :

1. Créez un fichier `phpinfo.php` dans la docroot du serveur web :

   ```php
   <?php
   // Show all information, defaults to INFO_ALL
   phpinfo();
   ```

1. Accédez à cette page dans votre navigateur web. Par exemple :

   ```http
   http://192.0.2.1/phpinfo.php
   ```

1. Assurez-vous que la mémoire mise en cache s’affiche comme suit :

   ![Confirmer que la mémoire mise en cache est reconnue par le serveur web](../../assets/configuration/memcache.png)

   Vérifiez que vous utilisez la version 3.0.5 ou ultérieure de la mémoire cache.

   Si le message mis en cache ne s’affiche pas, redémarrez le serveur web et actualisez la page du navigateur. S’il ne s’affiche toujours pas, vérifiez que vous avez installé l’extension `php-pecl-memcached`.

### Vérifier que les données mises en cache peuvent être mises en cache

Ce test utilise un script PHP pour vérifier que la mémoire mise en cache peut stocker et récupérer les données du cache.

Pour plus d’informations sur ce test, consultez le [tutoriel Installation et utilisation de Memcache sur Ubuntu](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-memcache-on-ubuntu-14-04).

Créez `cache-test.php` dans le docroot du serveur web avec les contenus suivants :

```php
$meminstance = new Memcached();

$meminstance->addServer("<memcached hostname or ip>", <memcached port>);

$result = $meminstance->get("test");

if ($result) {
    echo $result;
} else {
    echo "No matching key found. Refresh the browser to add it!";
    $meminstance->set("test", "Successfully retrieved the data!") or die("Could not save anything to memcached...");
}
```

Où `<memcached hostname or ip>` est `localhost`, `127.0.0.1` ou le nom d’hôte ou l’adresse IP du memcache. `<memcached port>` est le port d’écoute ; par défaut, `11211`.

Accédez à cette page dans un navigateur web. Par exemple

```http
http://192.0.2.1/cache-test.php
```

La première fois que vous accédez à la page, les éléments suivants s’affichent : `No matching key found. Refresh the browser to add it!`

Actualisez le navigateur. Le message passe à `Successfully retrieved the data!`.

Enfin, vous pouvez afficher les clés memcache à l’aide de Telnet :

```bash
telnet localhost <memcache port>
```

À l’invite, saisissez

```shell
stats items
```

Le résultat est similaire à ce qui suit :

```
STAT items:2:number 1
STAT items:2:age 106
STAT items:2:evicted 0
STAT items:2:evicted_nonzero 0
STAT items:2:evicted_time 0
STAT items:2:outofmemory 0
STAT items:2:tailrepairs 0
STAT items:2:reclaimed 0
STAT items:2:expired_unfetched 0
STAT items:2:evicted_unfetched 0
```

Videz le stockage en mémoire cache et quittez Telnet :

```shell
flush_all
```

```shell
quit
```

[Informations supplémentaires sur le test Telnet](https://darkcoding.net/software/memcached-list-all-keys/)
