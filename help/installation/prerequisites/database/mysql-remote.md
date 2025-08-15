---
title: Configurer une connexion distante à la base de données MySQL
description: Pour configurer une connexion à la base de données distante pour les installations sur site d’Adobe Commerce, procédez comme suit.
exl-id: 5fe304bd-ff38-4066-a1fd-8937575e4de4
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '700'
ht-degree: 0%

---

# Configurer une connexion distante à la base de données MySQL

Parfois, vous pouvez héberger la base de données sur un serveur distinct au lieu d’exécuter le serveur de base de données et le serveur web sur le même ordinateur.

Adobe permet d’établir une connexion à un serveur MySQL sur un autre ordinateur. Depuis Adobe Commerce 2.4.3, vous pouvez également configurer l’application pour utiliser une base de données Aurora Amazon Web Services (AWS) sans modification de code.

Aurora est un serveur MySQL haute performance et entièrement conforme hébergé sur AWS.

## Connexion à une base de données AWS Aurora

L’utilisation d’Aurora comme base de données est aussi facile que la spécification de la base de données dans la configuration de configuration standard d’Adobe Commerce, à l’aide du connecteur de base de données par défaut.

Lors de l&#39;exécution de `bin/magento setup:install`, utilisez les informations Aurora dans les champs `db-` :

```bash
bin/magento setup:install ... --db-host='database-aurora.us-east-1.rds.amazonaws.com' --db-name='magento2' --db-user='username' --db-password='password' ...
```

La valeur `db-host` est l’URL Aurora avec le `https://` et le dernier `:portnumber` supprimés.

## Configurer une connexion à la base de données distante

>[!NOTE]
>
>Il s’agit d’une rubrique avancée qui ne doit être utilisée que par un administrateur réseau ou un administrateur de base de données expérimenté. Vous devez avoir un accès `root` au système de fichiers et être en mesure de vous connecter à MySQL en tant que `root`.

### Conditions préalables

Avant de commencer, vous devez :

* [Installez MySQL Server](mysql.md) sur le serveur de base de données.
* [Créez une instance de base de données](mysql.md#configuring-the-database-instance) sur le serveur de base de données.
* Installez le client MySQL sur votre nœud web Adobe Commerce. Consultez la documentation MySQL pour plus de détails.

### Haute disponibilité

Suivez les instructions suivantes pour configurer les connexions à la base de données distante si votre serveur Web ou votre serveur de base de données est en cluster :

* Vous devez configurer une connexion pour chaque nœud de serveur web.
* En règle générale, vous configurez une connexion de base de données à l’équilibreur de charge de base de données. Toutefois, la mise en grappe de bases de données peut être complexe et c’est à vous de la configurer. Adobe ne formule aucune recommandation spécifique pour la mise en cluster de bases de données.

  Pour plus d’informations, voir [Documentation MySQL](https://dev.mysql.com/doc/refman/5.6/en/mysql-cluster.html).

### Résolution des problèmes de connexion

Si vous rencontrez des problèmes lors de la connexion à l’un des hôtes, commencez par envoyer un ping à l’autre hôte pour vous assurer qu’il est accessible. Vous devrez peut-être autoriser les connexions d&#39;un hôte à un autre en modifiant les règles de pare-feu et SELinux (si vous utilisez SELinux).

## Créer la connexion distante

Pour créer une connexion distante :

1. Sur votre serveur de base de données, ouvrez votre fichier de configuration MySQL en tant qu’utilisateur disposant de privilèges `root`.

   Pour le localiser, saisissez la commande suivante :

   ```bash
   mysql --help
   ```

   L’emplacement ressemble à ce qui suit :

   ```
   Default options are read from the following files in the given order:
   /etc/my.cnf /etc/mysql/my.cnf /usr/etc/my.cnf ~/.my.cnf
   ```

   >[!NOTE]
   >
   >Sur Ubuntu 16, le chemin est généralement `/etc/mysql/mysql.conf.d/mysqld.cnf`.

1. Recherchez des `bind-address` dans le fichier de configuration.

   S’il existe, modifiez la valeur comme suit.

   S’il n’existe pas, ajoutez-le à la section `[mysqld]`.

   ```conf
   bind-address = <ip address of your web node>
   ```

   Voir [Documentation MySQL](https://dev.mysql.com/doc/refman/5.6/en/server-options.html), en particulier si vous disposez d’un serveur web en cluster.

1. Enregistrez vos modifications dans le fichier de configuration et quittez l’éditeur de texte.
1. Redémarrez le service MySQL :

   * CentOS : `service mysqld restart`

   * Ubuntu : `service mysql restart`

   >[!NOTE]
   >
   >Si MySQL ne démarre pas, recherchez la source du problème dans le journal système. Résolvez le problème en utilisant la [documentation MySQL](https://dev.mysql.com/doc/refman/5.6/en/server-options.html#option_mysqld_bind-address) ou une autre source faisant autorité.

## Octroi de l&#39;accès à un utilisateur de base de données

Pour permettre à votre nœud web de se connecter au serveur de base de données, vous devez accorder à un utilisateur de la base de données de nœud web l’accès à la base de données sur le serveur distant.

Cet exemple accorde à l&#39;utilisateur de la base de données `root` un accès complet à la base de données sur l&#39;hôte distant.

Accorder l&#39;accès à un utilisateur de base de données :

1. Connectez-vous au serveur de base de données.
1. Connectez-vous à la base de données MySQL en tant qu’utilisateur `root`.
1. Saisissez la commande suivante :

   ```shell
   GRANT ALL ON <local database name>.* TO <remote web node username>@<remote web node server ip address> IDENTIFIED BY '<database user password>';
   ```

   Par exemple,

   ```shell
   GRANT ALL ON magento_remote.* TO dbuser@192.0.2.50 IDENTIFIED BY 'dbuserpassword';
   ```

   >[!NOTE]
   >
   >Si votre serveur web est en cluster, saisissez la même commande sur chaque serveur web. Vous devez utiliser le même nom d&#39;utilisateur pour chaque serveur Web.

## Vérifier l&#39;accès à la base de données

Sur votre hôte de nœud web, saisissez la commande suivante pour vérifier que la connexion fonctionne :

```bash
mysql -u <local database username> -h <database server ip address> -p
```

Si le moniteur MySQL s’affiche comme suit, la base de données est prête pour Adobe Commerce :

```
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 213 Server version: 5.6.26 MySQL Community Server (GPL)

Copyright (c) 2000, 2015, Oracle and/or its affiliates. All rights reserved.

Oracle is a registered trademark of Oracle Corporation and/or its affiliates. Other names may be trademarks of their respective owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.
```

Si votre serveur web est en cluster, saisissez la commande sur chaque hôte de serveur web.

## Installation d’Adobe Commerce

Lors de l’installation d’Adobe Commerce, vous devez indiquer les informations suivantes :

* L’URL de base (également appelée *adresse du magasin*) spécifie le nom d’hôte ou l’adresse IP du *nœud web*
* L’hôte de base de données est l’adresse IP *serveur de base de données distant* (ou la répartition de charge si le serveur de base de données est en cluster)
* Le nom d&#39;utilisateur de base de données est l&#39;utilisateur de base de données *nœud web local* auquel vous avez donné accès
* Le mot de passe de la base de données est celui de l’utilisateur du nœud web local
* Database name est le nom de la base de données sur le serveur distant
