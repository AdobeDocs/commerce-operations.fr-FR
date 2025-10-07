---
title: Configurer memcached sur Ubuntu
description: Découvrez comment installer et configurer memcached sur Ubuntu pour la mise en cache Adobe Commerce. Découvrez les instructions de configuration et des conseils d’optimisation.
feature: Configuration, Cache, Storage
exl-id: 831193d2-3e81-472c-9b87-78a8d52959b4
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '453'
ht-degree: 0%

---

# Configurer memcached sur Ubuntu

Cette section fournit des instructions pour installer memcached sur Ubuntu.

>[!INFO]
>
>Adobe recommande d’utiliser la version 3.0.5 ou ultérieure de memcached.

PHP n&#39;ayant pas de support natif pour memcache, vous devez installer une extension pour que PHP puisse l&#39;utiliser. Il y a deux extensions PHP disponibles et il est important de décoder laquelle utiliser :

- `memcache` (_pas d_), une extension plus ancienne mais populaire qui n’est pas entretenue régulièrement.
L&#39;extension `memcache` actuellement _ne fonctionne pas_ avec PHP 7. Voir [Documentation PHP pour memcache](https://www.php.net/manual/en/book.memcache.php).

  Le nom exact est `php5-memcache` pour Ubuntu.

- `memcached` (_avec un`d`_) - une extension plus récente et maintenue compatible avec PHP 7. Voir [Documentation PHP pour memcached](https://www.php.net/manual/en/book.memcached.php).

  Le nom exact est `php5-memcached` pour Ubuntu.

## Installer et configurer memcached sur Ubuntu

**Pour installer et configurer memcached sur Ubuntu** :

1. En tant qu’utilisateur disposant de droits d’`root`, saisissez la commande suivante :

   ```bash
   apt-get -y update
   ```

   ```bash
   apt-get -y install php5-memcached memcached
   ```

1. Modifiez le paramètre de configuration memcached pour `CACHESIZE` et `-l` :

   1. Ouvrez `/etc/memcached.conf` dans un éditeur de texte.
   1. Recherchez le paramètre `-m` .
   1. Remplacez sa valeur par au moins `1GB`
   1. Recherchez le paramètre `-l` .
   1. Remplacez sa valeur par `127.0.0.1` ou `localhost`
   1. Enregistrez vos modifications dans `memcached.conf` et quittez l’éditeur de texte.
   1. Redémarrez memcached.

      ```bash
      service memcached restart
      ```

1. Redémarrez votre serveur web.

   Pour Apache, `service apache2 restart`

1. Passez à la section suivante.

## Vérification du fonctionnement de la mémoire cache avant l’installation de Magento

Adobe recommande de tester memcached pour s’assurer qu’il fonctionne avant d’installer Commerce. Cela ne prend que quelques minutes et peut simplifier le dépannage ultérieurement.

### Vérifiez que la mise en cache est reconnue par le serveur web

Pour vérifier que memcached est reconnu par le serveur web :

1. Créez un fichier `phpinfo.php` dans le fichier docroot du serveur web :

   ```php
   <?php
   // Show all information, defaults to INFO_ALL
   phpinfo();
   ```

1. Accédez à cette page dans votre navigateur web. Par exemple :

   ```http
   http://192.0.2.1/phpinfo.php
   ```

1. Assurez-vous que memcached affiche les informations suivantes :

   ![Confirmer que le cache est reconnu par le serveur web](../../assets/configuration/memcache.png)

   Vérifiez que vous utilisez memcached version 3.0.5 ou ultérieure.

   Si memcached ne s’affiche pas, redémarrez le serveur web et actualisez la page du navigateur. S’il ne s’affiche toujours pas, vérifiez que vous avez installé l’extension `php-pecl-memcached`.

### Vérifier que les données mises en cache peuvent être mises en cache

Ce test utilise un script PHP pour vérifier que memcached peut stocker et récupérer les données du cache.

Pour plus d&#39;informations sur ce test, voir [Tutoriel Installation et utilisation de Memcache sur Ubuntu](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-memcache-on-ubuntu-14-04).

Créez des `cache-test.php` dans la racine docroot du serveur web avec les contenus suivants :

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

Où `<memcached hostname or ip>` est `localhost`, `127.0.0.1` ou le nom d’hôte ou l’adresse IP memcache. Le `<memcached port>` est le port d’écoute ; par défaut, `11211`.

Accédez à cette page dans un navigateur web. Par exemple :

```http
http://192.0.2.1/cache-test.php
```

La première fois que vous accédez à la page , les éléments suivants s’affichent : `No matching key found. Refresh the browser to add it!`

Actualisez le navigateur. Le message devient `Successfully retrieved the data!`

Enfin, vous pouvez afficher les clés memcache à l&#39;aide de Telnet :

```bash
telnet localhost <memcache port>
```

À l’invite, saisissez .

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
