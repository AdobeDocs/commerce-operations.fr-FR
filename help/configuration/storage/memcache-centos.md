---
title: Configuration de la mémoire mise en cache sur CentOS
description: Installez et configurez memmis en cache sur CentOS.
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '561'
ht-degree: 0%

---


# Configuration de la mémoire mise en cache sur CentOS

Cette section fournit des instructions pour l’installation de la mémoire mise en cache sur CentOS. Pour plus d’informations, consultez la [wiki mis en cache](https://github.com/memcached/old-wiki).

>[!INFO]
>
>Adobe recommande d’utiliser la dernière version stable en mémoire cache (actuellement 3.1.3 pour la mémoire mise en cache).

Comme PHP ne prend pas en charge le memcache, vous devez installer une extension pour que PHP l’utilise. Deux extensions PHP sont disponibles et il est important de décoder laquelle utiliser :

- `memcache` (_no d_) : extension plus ancienne mais populaire qui n’est pas gérée régulièrement.
Le `memcache` extension actuellement _ne fait pas_ fonctionne avec PHP 7. Voir [documentation PHP pour memcache](https://www.php.net/manual/en/book.memcache.php).

   Le nom exact est : `php-pecl-memcache` pour CentOS.

- `memcached` (_avec un`d`_) : extension plus récente et plus gérée compatible avec PHP 7. Voir [documentation PHP pour memcached](https://www.php.net/manual/en/book.memcached.php).

   Le nom exact est : `php-pecl-memcached` pour CentOS.

## Installation et configuration des mèmes mis en cache sur CentOS

Pour installer le memcached sur CentOS, effectuez les tâches suivantes en tant qu’utilisateur avec `root` privilèges :

1. Installez le memmis en cache et ses dépendances :

   ```bash
   yum -y update
   ```

   ```bash
   yum install -y libevent libevent-devel
   ```

   ```bash
   yum install -y memcached
   ```

   ```bash
   yum install -y php-pecl-memcache
   ```

   >[!INFO]
   >
   >La syntaxe des commandes précédentes peut dépendre des référentiels de package que vous utilisez. Par exemple, si vous utilisez webtatic et PHP 5.6, saisissez `yum install -y php56w-pecl-memcache`. Utilisation `yum search memcache|grep php` pour trouver le nom du module approprié.


1. Modification du paramètre de configuration de la mémoire mise en cache pour `CACHESIZE` et `OPTIONS`:

   1. Ouvrir `/etc/sysconfig/memcached` dans un éditeur de texte.
   1. Recherchez la valeur pour `CACHESIZE` et définissez-le sur au moins 1 Go. Par exemple :

      ```config
      CACHESIZE="1GB"
      ```

   1. Recherchez la valeur pour `OPTIONS` et modifiez-le en `localhost` ou `127.0.0.1`

1. Enregistrez vos modifications dans `memcached` et quittez l’éditeur de texte.
1. Redémarrez le memcached.

   ```bash
   service memcached restart
   ```

1. Redémarrez votre serveur web.

   Pour Apache :

   ```bash
   service httpd restart
   ```

1. Passez à la section suivante.

## Vérifier le fonctionnement de la mémoire mise en cache avant l’installation de Commerce

Adobe recommande de tester la mémoire mise en cache pour s’assurer qu’elle fonctionne avant l’installation de Commerce. Cette opération ne prend que quelques minutes et peut simplifier ultérieurement le dépannage.

### Vérifier que la mémoire mise en cache est reconnue par le serveur web

Pour vérifier que la mémoire mise en cache est reconnue par le serveur web :

1. Créez un `phpinfo.php` dans le docroot du serveur web :

   ```php
   <?php
   // Show all information, defaults to INFO_ALL
   phpinfo();
   ```

1. Accédez à cette page dans votre navigateur web.

   Par exemple : `http://192.0.2.1/phpinfo.php`

1. Assurez-vous que memcache s’affiche comme suit :

![Vérifiez que le cache de mémoire est reconnu par le serveur web.](../../assets/configuration/memcache.png)

Vérifiez que vous utilisez la version 3.0.5 ou ultérieure de la mémoire cache.

Si memcache ne s’affiche pas, redémarrez le serveur web et actualisez la page du navigateur. S’il ne s’affiche toujours pas, vérifiez que vous avez installé le `php-pecl-memcache` extension .

### Créez un test memcache constitué d’une base de données MySQL et d’un script PHP.

Le test utilise une base de données, un tableau et des données MySQL pour vérifier que vous pouvez récupérer les données de la base de données et les stocker dans le cache mémoire. Un script PHP recherche d’abord le cache. Si le résultat n’existe pas, le script interroge la base de données. Une fois la requête remplie par la base de données d’origine, le script stocke le résultat dans memcache, à l’aide de la fonction `set` .

[Plus d’informations sur ce test](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-memcache-on-ubuntu-12-04)

Créez la base de données MySQL :

```bash
mysql -u root -p
```

Dans le `mysql` saisissez les commandes suivantes :

```sql
create database memcache_test;
GRANT ALL ON memcache_test.* TO memcache_test@localhost IDENTIFIED BY 'memcache_test';
use memcache_test;
create table example (id int, name varchar(30));
insert into example values (1, "new_data");
exit
```

Créer `cache-test.php` dans le docroot de votre serveur web :

```php
$meminstance = new Memcached();

$meminstance->addServer('<memcached hostname or ip>', <memcached port>);

$query = "select id from example where name = 'new_data'";
$querykey = "KEY" . md5($query);

$result = $meminstance->get($querykey);

if (!$result) {
   try {
        $dbh = new PDO('mysql:host=localhost;dbname=memcache_test','memcache_test','memcache_test');
        $dbh->setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION);
        $result = $dbh->query("select id from example where name = 'new_data'")->fetch();
        $meminstance->set($querykey, $result, 0, 600);
        print "got result from mysql\n";
        return 0;
    } catch (PDOException $e) {
        die($e->getMessage());
    }
}
print "got result from memcached\n";
return 0;
```

Où `<memcached hostname or ip>` est `localhost`, `127.0.0.1`ou le nom d’hôte ou l’adresse IP du memcache. Le `<memcached port>` est le port d’écoute ; par défaut, `11211`.

Exécutez le script à partir de la ligne de commande.

```bash
cd <web server docroot>
```

```bash
php cache-test.php
```

Le premier résultat est `got result from mysql`. Cela signifie que la clé n’existait pas dans la mémoire mise en cache, mais qu’elle a été récupérée à partir de MySQL.

Le deuxième résultat est le suivant : `got result from memcached`, qui vérifie que la valeur est stockée correctement dans la mémoire mise en cache.

Enfin, vous pouvez afficher les clés memcache à l’aide de Telnet :

```bash
telnet localhost <memcache port>
```

À l’invite, saisissez

```bash
stats items
```

Le résultat est similaire à ce qui suit :

```terminal
STAT items:3:number 1
STAT items:3:age 1075
STAT items:3:evicted 0
STAT items:3:evicted_nonzero 0
STAT items:3:evicted_time 0
STAT items:3:outofmemory 0
STAT items:3:tailrepairs 0
```

Videz le stockage de memcache et quittez Telnet :

```bash
flush_all
```

```bash
quit
```

[Informations supplémentaires sur le test Telnet](https://darkcoding.net/software/memcached-list-all-keys/)
