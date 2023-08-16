---
title: Secure cron PHP
description: Restreindre qui peut exécuter le fichier cron.php dans un navigateur.
feature: Configuration, Security
exl-id: c81fcab2-1ee3-4ec7-a300-0a416db98614
source-git-commit: 56a2461edea2799a9d569bd486f995b0fe5b5947
workflow-type: tm+mt
source-wordcount: '938'
ht-degree: 1%

---

# Secure cron PHP

Cette rubrique aborde la sécurisation `pub/cron.php` pour empêcher son utilisation dans un exploitation malveillante. Si vous ne sécurisez pas cron, un utilisateur peut exécuter cron pour attaquer votre application Commerce.

La tâche cron exécute plusieurs tâches planifiées et constitue une partie essentielle de votre configuration Commerce. Les tâches planifiées comprennent, entre autres :

- Réindexation
- Générer des emails
- Génération de newsletters
- Génération de plans de site

>[!INFO]
>
>Voir [Configuration et exécution de cron](../cli/configure-cron-jobs.md#run-cron-from-the-command-line) pour plus d’informations sur les groupes cron.

Vous pouvez exécuter une tâche cron comme suit :

- En utilisant la variable [`magento cron:run`](../cli/configure-cron-jobs.md#run-cron-from-the-command-line) à partir de la ligne de commande ou dans un crontab ;
- Accès `pub/cron.php?[group=<name>]` dans un navigateur web

>[!INFO]
>
>Vous n’avez rien à faire si vous utilisez la variable [`magento cron:run`](../cli/configure-cron-jobs.md#run-cron-from-the-command-line) pour exécuter cron, car il utilise un autre processus déjà sécurisé.

## Sécuriser cron avec Apache

Cette section explique comment sécuriser cron à l’aide de l’authentification HTTP de base avec Apache. Ces instructions sont basées sur Apache 2.2 avec CentOS 6. Pour plus d&#39;informations, consultez l&#39;une des ressources suivantes :

- [Tutoriel sur l’authentification et l’autorisation Apache 2.2](https://httpd.apache.org/docs/2.2/howto/auth.html)
- [Tutoriel sur l’authentification et l’autorisation Apache 2.4](https://httpd.apache.org/docs/2.4/howto/auth.html)

### Créer un fichier de mot de passe

Pour des raisons de sécurité, vous pouvez localiser le fichier de mot de passe n’importe où, à l’exception de la docroot de votre serveur web. Dans cet exemple, nous stockons le fichier de mot de passe dans un nouveau répertoire.

Saisissez les commandes suivantes en tant qu’utilisateur avec `root` privilèges :

```bash
mkdir -p /usr/local/apache/password
```

```bash
htpasswd -c /usr/local/apache/password/passwords <username>
```

Où `<username>` peut être un utilisateur du serveur web ou un autre utilisateur. Dans cet exemple, nous utilisons l’utilisateur du serveur web, mais c’est à vous de choisir l’utilisateur.

Suivez les invites de votre écran pour créer un mot de passe pour l’utilisateur.

Pour ajouter un autre utilisateur à votre fichier de mot de passe, saisissez la commande suivante en tant qu’utilisateur avec `root` privilèges :

```bash
htpasswd /usr/local/apache/password/passwords <username>
```

### Ajouter des utilisateurs pour créer un groupe cron autorisé (facultatif)

Vous pouvez permettre à plusieurs utilisateurs d’exécuter cron en ajoutant ces utilisateurs à votre fichier de mot de passe, y compris un fichier de groupe.

Pour ajouter un autre utilisateur à votre fichier de mot de passe :

```bash
htpasswd /usr/local/apache/password/passwords <username>
```

Pour créer un groupe autorisé, créez un fichier de groupe n’importe où en dehors de la docroot du serveur web. Le fichier group spécifie le nom du groupe et les utilisateurs du groupe. Dans cet exemple, le nom du groupe est `MagentoCronGroup`.

```bash
vim /usr/local/apache/password/group
```

Contenu du fichier :

```text
MagentoCronGroup: <username1> ... <usernameN>
```

### Sécuriser cron dans `.htaccess`

Pour sécuriser cron dans `.htaccess` fichier :

1. Connectez-vous à votre serveur Commerce en tant que propriétaire du système de fichiers ou passez à .
1. Ouvrir `<magento_root>/pub/.htaccess` dans un éditeur de texte.

   (Parce que `cron.php` se trouve dans la variable `pub` répertoire, modifiez-le `.htaccess` uniquement.)

1. _L’accès Cron pour un ou plusieurs utilisateurs._ Remplacer le `<Files cron.php>` avec les instructions suivantes :

   ```conf
   <Files cron.php>
      AuthType Basic
      AuthName "Cron Authentication"
      AuthUserFile /usr/local/apache/password/passwords
      Require valid-user
   </Files>
   ```

1. _Accès Cron pour un groupe._ Remplacer le `<Files cron.php>` avec les instructions suivantes :

   ```conf
   <Files cron.php>
      AuthType Basic
      AuthName "Cron Authentication"
      AuthUserFile /usr/local/apache/password/passwords
      AuthGroupFile <path to optional group file>
      Require group <name>
   </Files>
   ```

1. Enregistrez vos modifications dans `.htaccess` et quittez l’éditeur de texte.
1. Passez à la [Vérifier que cron est sécurisé](#verify-cron-is-secure).

## Secure cron avec Nginx

Cette section explique comment sécuriser cron à l’aide du serveur web Nginx. Vous devez effectuer les tâches suivantes :

1. Configuration d’un fichier de mot de passe chiffré pour Nginx
1. Modifiez la configuration nginx pour référencer le fichier de mot de passe lors de l’accès à `pub/cron.php`

### Créer un fichier de mot de passe

Consultez l’une des ressources suivantes pour créer un fichier de mot de passe avant de poursuivre :

- [Comment configurer l’authentification par mot de passe avec Nginx sur Ubuntu 14.04 (DigitalOcean)](https://www.digitalocean.com/community/tutorials/how-to-set-up-password-authentication-with-nginx-on-ubuntu-14-04)
- [Authentification HTTP de base avec Nginx (howtoforge)](https://www.howtoforge.com/basic-http-authentication-with-nginx)

### Sécuriser cron dans `nginx.conf.sample`

Commerce fournit un exemple optimisé de fichier de configuration nginx prêt à l’emploi. Nous vous recommandons de le modifier pour sécuriser cron.

1. Ajoutez ce qui suit à votre [`nginx.conf.sample`](https://github.com/magento/magento2/blob/2.4/nginx.conf.sample) fichier :

   ```conf
   #Securing cron
   location ~ cron\.php$ {
      auth_basic "Cron Authentication";
      auth_basic_user_file /etc/nginx/.htpasswd;
   
      try_files $uri =404;
      fastcgi_pass   fastcgi_backend;
      fastcgi_buffers 1024 4k;
   
      fastcgi_read_timeout 600s;
      fastcgi_connect_timeout 600s;
   
      fastcgi_index  index.php;
      fastcgi_param  SCRIPT_FILENAME  $document_root$fastcgi_script_name;
      include        fastcgi_params;
   }
   ```

1.Redémarrez le signal :

```bash
systemctl restart nginx
```

1. Passez à la [Vérifier que cron est sécurisé](#verify-cron-is-secure).

## Vérifier que cron est sécurisé

La méthode la plus simple pour vérifier que `pub/cron.php` est sécurisé afin de vérifier qu’il crée des lignes dans la variable `cron_schedule` table de base de données après avoir configuré l’authentification par mot de passe. Cet exemple utilise des commandes SQL pour vérifier la base de données, mais vous pouvez utiliser n&#39;importe quel outil de votre choix.

>[!INFO]
>
>La variable `default` cron que vous exécutez dans cet exemple s’exécute selon le planning défini dans `crontab.xml`. Une tâche cron ne s’exécute qu’une seule fois par jour. La première fois que vous exécutez cron à partir du navigateur, l’événement `cron_schedule` Le tableau est mis à jour, mais sa mise à jour suit `pub/cron.php` les requêtes s’exécutent selon le planning configuré.

**Pour vérifier que cron est sécurisé**:

1. Connectez-vous à la base de données en tant qu’utilisateur de base de données Commerce ou en tant que `root`.

   Par exemple,

   ```bash
   mysql -u magento -p
   ```

1. Utilisez la base de données Commerce :

   ```shell
   use <database-name>;
   ```

   Par exemple,

   ```shell
   use magento;
   ```

1. Supprimez toutes les lignes de la `cron_schedule` table de base de données :

   ```shell
   TRUNCATE TABLE cron_schedule;
   ```

1. Exécutez cron à partir d’un navigateur :

   ```shell
   http[s]://<Commerce hostname or ip>/cron.php?group=default
   ```

   Par exemple :

   ```shell
   http://magento.example.com/cron.php?group=default
   ```

1. Lorsque vous y êtes invité, saisissez le nom et le mot de passe d’un utilisateur autorisé. La figure suivante illustre un exemple.

   ![Autorisation de cron à l’aide de HTTP Basic](../../assets/configuration/cron-auth.png)

1. Vérifiez que des lignes ont été ajoutées au tableau :

   ```shell
   SELECT * from cron_schedule;
   
   mysql> SELECT * from cron_schedule;
   +-------------+-----------------------------------------------+---------+----------+---------------------+---------------------+-------------+-------------+
   | schedule_id | job_code                             | status  | messages | created_at        | scheduled_at      | executed_at | finished_at |
   +-------------+-----------------------------------------------+---------+----------+---------------------+---------------------+-------------+-------------+
   |         1 | catalog_product_outdated_price_values_cleanup | pending | NULL    | 2017-09-27 14:24:17 | 2017-09-27 14:24:00 | NULL      | NULL      |
   |         2 | sales_grid_order_async_insert             | pending | NULL    | 2017-09-27 14:24:17 | 2017-09-27 14:24:00 | NULL      | NULL      |
   |         3 | sales_grid_order_invoice_async_insert       | pending | NULL    | 2017-09-27 14:24:17 | 2017-09-27 14:24:00 | NULL      | NULL      |
   |         4 | sales_grid_order_shipment_async_insert      | pending | NULL    | 2017-09-27 14:24:17 | 2017-09-27 14:24:00 | NULL      | NULL      |
   |         5 | sales_grid_order_creditmemo_async_insert     | pending | NULL    | 2017-09-27 14:24:17 | 2017-09-27 14:24:00 | NULL      | NULL      |
   |         6 | sales_send_order_emails                  | pending | NULL    | 2017-09-27 14:24:17 | 2017-09-27 14:24:00 | NULL      | NULL      |
   |         7 | sales_send_order_invoice_emails            | pending | NULL    | 2017-09-27 14:24:17 | 2017-09-27 14:24:00 | NULL      | NULL      |
   |         8 | sales_send_order_shipment_emails           | pending | NULL    | 2017-09-27 14:24:17 | 2017-09-27 14:24:00 | NULL      | NULL      |
   |         9 | sales_send_order_creditmemo_emails         | pending | NULL    | 2017-09-27 14:24:17 | 2017-09-27 14:24:00 | NULL      | NULL      |
   |        10 | newsletter_send_all                     | pending | NULL    | 2017-09-27 14:24:17 | 2017-09-27 14:25:00 | NULL      | NULL      |
   |        11 | captcha_delete_old_attempts               | pending | NULL    | 2017-09-27 14:24:17 | 2017-09-27 14:30:00 | NULL      | NULL      |
   |        12 | captcha_delete_expired_images             | pending | NULL    | 2017-09-27 14:24:17 | 2017-09-27 14:30:00 | NULL      | NULL      |
   |        13 | outdated_authentication_failures_cleanup     | pending | NULL    | 2017-09-27 14:24:17 | 2017-09-27 14:24:00 | NULL      | NULL      |
   |        14 | magento_newrelicreporting_cron            | pending | NULL    | 2017-09-27 14:24:17 | 2017-09-27 14:24:00 | NULL      | NULL      |
   +-------------+-----------------------------------------------+---------+----------+---------------------+---------------------+-------------+-------------+
   14 rows in set (0.00 sec)
   ```

## Exécution de cron à partir d’un navigateur web

Vous pouvez exécuter cron à tout moment, par exemple pendant le développement, à l’aide d’un navigateur web.

>[!WARNING]
>
>Do _not_ exécutez cron dans un navigateur sans le sécuriser au préalable.

Si vous utilisez un serveur web Apache, vous devez supprimer la restriction de la variable `.htaccess` avant d’exécuter cron dans un navigateur :

1. Connectez-vous à votre serveur Commerce en tant qu’utilisateur disposant des autorisations nécessaires pour écrire dans le système de fichiers Commerce.
1. Ouvrez l’un des éléments suivants dans un éditeur de texte (selon votre point d’entrée vers Magento) :

   ```text
   <magento_root>/pub/.htaccess
   <magento_root>/.htaccess
   ```

1. Supprimez ou mettez en commentaire les éléments suivants :

   ```conf
   ## Deny access to cron.php
     <Files cron.php>
        order allow,deny
        deny from all
     </Files>
   ```

   Par exemple,

   ```conf
   ## Deny access to cron.php
      #<Files cron.php>
         # order allow,deny
         # deny from all
      #</Files>
   ```

1. Enregistrez vos modifications et quittez l’éditeur de texte.

   Vous pouvez ensuite exécuter cron dans un navigateur web comme suit :

   ```text
   <your hostname or IP>/<Commerce root>/pub/cron.php[?group=<group name>]
   ```

Où :

- `<your hostname or IP>` est le nom d’hôte ou l’adresse IP de votre installation Commerce ;
- `<Commerce root>` est le répertoire relatif à la docroot du serveur web sur lequel vous avez installé le logiciel Commerce ;

  L’URL exacte que vous utilisez pour exécuter l’application Commerce dépend de la manière dont vous avez configuré votre serveur web et votre hôte virtuel.

- `<group name>` est un nom de groupe cron valide (facultatif).

Par exemple,

```http
https://magento.example.com/magento2/pub/cron.php?group=index
```

>[!INFO]
>
>Vous devez exécuter cron deux fois : d’abord pour découvrir des tâches à exécuter, puis à nouveau pour exécuter les tâches elles-mêmes. Voir [Configuration et exécution de cron](../cli/configure-cron-jobs.md) pour plus d’informations sur les groupes cron.
