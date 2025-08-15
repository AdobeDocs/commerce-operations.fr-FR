---
title: Configurer la mise en cache sous CentOS
description: Installez et configurez memcached sur CentOS.
feature: Configuration, Cache, Storage
exl-id: fc4ad18b-7e99-496e-aebc-1d7640d8716c
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '550'
ht-degree: 0%

---

# Configurer la mise en cache sous CentOS

Cette section fournit des instructions pour installer memcached sur CentOS. Pour plus d’informations, consultez le [wiki mis en cache](https://github.com/memcached/old-wiki).

>[!INFO]
>
>Adobe recommande d’utiliser la dernière version stable de memcached (actuellement 3.1.3 pour memcached).

PHP n&#39;ayant pas de support natif pour memcache, vous devez installer une extension pour que PHP puisse l&#39;utiliser. Il y a deux extensions PHP disponibles et il est important de décoder laquelle utiliser :

- `memcache` (_pas d_), une extension plus ancienne mais populaire qui n’est pas entretenue régulièrement.
L&#39;extension `memcache` actuellement _ne fonctionne pas_ avec PHP 7. Voir [Documentation PHP pour memcache](https://www.php.net/manual/en/book.memcache.php).

  Le nom exact est `php-pecl-memcache` pour CentOS.

- `memcached` (_avec un`d`_) - une extension plus récente et maintenue compatible avec PHP 7. Voir [Documentation PHP pour memcached](https://www.php.net/manual/en/book.memcached.php).

  Le nom exact est `php-pecl-memcached` pour CentOS.

## Installation et configuration de memcached sur CentOS

Pour installer memcached sur CentOS, effectuez les tâches suivantes en tant qu’utilisateur avec des privilèges `root` :

1. Installez memcached et ses dépendances :

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
   >La syntaxe des commandes précédentes peut dépendre des référentiels de package que vous utilisez. Par exemple, si vous utilisez webtatic et PHP 5.6, saisissez `yum install -y php56w-pecl-memcache`. Utilisez `yum search memcache|grep php` pour trouver le nom de package approprié.


1. Modifiez le paramètre de configuration memcached pour `CACHESIZE` et `OPTIONS` :

   1. Ouvrez `/etc/sysconfig/memcached` dans un éditeur de texte.
   1. Recherchez la valeur de `CACHESIZE` et définissez-la sur au moins 1 Go. Par exemple :

      ```config
      CACHESIZE="1GB"
      ```

   1. Recherchez la valeur de `OPTIONS` et définissez-la sur `localhost` ou `127.0.0.1`

1. Enregistrez vos modifications dans `memcached` et quittez l’éditeur de texte.
1. Redémarrez memcached.

   ```bash
   service memcached restart
   ```

1. Redémarrez votre serveur web.

   Pour Apache :

   ```bash
   service httpd restart
   ```

1. Passez à la section suivante.

## Vérification du fonctionnement de la mémoire cache avant l’installation de Commerce

Adobe recommande de tester memcached pour s’assurer qu’il fonctionne avant d’installer Commerce. Cela ne prend que quelques minutes et peut simplifier le dépannage ultérieurement.

### Vérifiez que la mise en cache est reconnue par le serveur web

Pour vérifier que memcached est reconnu par le serveur web :

1. Créez un fichier `phpinfo.php` dans le fichier docroot du serveur web :

   ```php
   <?php
   // Show all information, defaults to INFO_ALL
   phpinfo();
   ```

1. Accédez à cette page dans votre navigateur web.

   Par exemple, `http://192.0.2.1/phpinfo.php`

1. Assurez-vous que le cache mémoire s’affiche comme suit :

![Confirmer que le cache mémoire est reconnu par le serveur web](../../assets/configuration/memcache.png)

Vérifiez que vous utilisez memcached version 3.0.5 ou ultérieure.

Si le cache mémoire ne s’affiche pas, redémarrez le serveur web et actualisez la page du navigateur. S’il ne s’affiche toujours pas, vérifiez que vous avez installé l’extension `php-pecl-memcache`.

### Créez un test memcache composé d&#39;une base MySQL et d&#39;un script PHP

Le test utilise une base de données, une table et des données MySQL pour vérifier que vous pouvez récupérer les données de la base de données et les stocker dans le cache mémoire. Un script PHP commence par rechercher le cache. Si le résultat n’existe pas, le script interroge la base de données. Une fois la requête remplie par la base de données d’origine, le script stocke le résultat dans memcache, à l’aide de la commande `set`.

[Plus d’informations sur ce test](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-memcache-on-ubuntu-12-04)

Créez la base de données MySQL :

```bash
mysql -u root -p
```

À l’invite de `mysql`, saisissez les commandes suivantes :

```sql
create database memcache_test;
GRANT ALL ON memcache_test.* TO memcache_test@localhost IDENTIFIED BY 'memcache_test';
use memcache_test;
create table example (id int, name varchar(30));
insert into example values (1, "new_data");
exit
```

Créez des `cache-test.php` dans la racine docroot de votre serveur web :

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

Où `<memcached hostname or ip>` est `localhost`, `127.0.0.1` ou le nom d’hôte ou l’adresse IP memcache. Le `<memcached port>` est le port d’écoute ; par défaut, `11211`.

Exécutez le script à partir de la ligne de commande.

```bash
cd <web server docroot>
```

```bash
php cache-test.php
```

Le premier résultat est `got result from mysql`. Cela signifie que la clé n’existait pas dans memcached, mais elle a été récupérée depuis MySQL.

Le deuxième résultat est `got result from memcached`, qui vérifie que la valeur est stockée correctement dans le cache mémoire.

Enfin, vous pouvez afficher les clés memcache à l&#39;aide de Telnet :

```bash
telnet localhost <memcache port>
```

À l’invite, saisissez .

```bash
stats items
```

Le résultat est similaire à ce qui suit :

```
STAT items:3:number 1
STAT items:3:age 1075
STAT items:3:evicted 0
STAT items:3:evicted_nonzero 0
STAT items:3:evicted_time 0
STAT items:3:outofmemory 0
STAT items:3:tailrepairs 0
```

Videz la mémoire cache et quittez Telnet :

```bash
flush_all
```

```bash
quit
```

[Informations supplémentaires sur le test Telnet](https://darkcoding.net/software/memcached-list-all-keys/)
