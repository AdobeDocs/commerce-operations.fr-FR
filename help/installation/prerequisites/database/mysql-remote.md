---
title: Configuration d’une connexion de base de données MySQL distante
description: Pour configurer une connexion à base de données distante pour les installations sur site d’Adobe Commerce, procédez comme suit.
exl-id: 5fe304bd-ff38-4066-a1fd-8937575e4de4
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '700'
ht-degree: 0%

---

# Configuration d’une connexion de base de données MySQL distante

Il peut arriver que vous souhaitiez héberger la base de données sur un serveur distinct au lieu d’exécuter le serveur de base de données et le serveur web sur le même ordinateur.

Adobe a fourni un moyen de se connecter à un serveur MySQL sur une autre machine. Depuis Adobe Commerce 2.4.3, vous pouvez également configurer l’application pour utiliser une base de données Amazon Web Services (AWS) Aurora sans modification de code.

Aurora est un serveur MySQL hautement performant et entièrement compatible hébergé sur AWS.

## Connexion à une base de données AWS Aurora

Utiliser Aurora comme base de données est aussi simple que de spécifier la base de données dans la configuration standard d&#39;Adobe Commerce, à l&#39;aide du connecteur de base de données par défaut.

Lors de l’exécution de `bin/magento setup:install`, utilisez les informations Aurora dans les champs `db-` :

```bash
bin/magento setup:install ... --db-host='database-aurora.us-east-1.rds.amazonaws.com' --db-name='magento2' --db-user='username' --db-password='password' ...
```

La valeur `db-host` est l’URL de l’Aurora dont `https://` et `:portnumber` de fin ont été supprimés.

## Configurer une connexion à une base de données distante

>[!NOTE]
>
>Il s’agit d’une rubrique avancée qui ne doit être utilisée que par un administrateur réseau ou un administrateur de base de données expérimenté. Vous devez disposer de `root` accès au système de fichiers et vous devez pouvoir vous connecter à MySQL en tant que `root`.

### Conditions préalables

Avant de commencer, vous devez :

* [Installez MySQL Server](mysql.md) sur le serveur de base de données.
* [Créez une instance de base de données](mysql.md#configuring-the-database-instance) sur le serveur de base de données.
* Installez le client MySQL sur votre noeud web Adobe Commerce. Pour plus d’informations, consultez la documentation MySQL .

### Haute disponibilité

Suivez les instructions suivantes pour configurer les connexions à une base de données distante si votre serveur web ou serveur de base de données est mis en grappe :

* Vous devez configurer une connexion pour chaque noeud de serveur web.
* En règle générale, vous configurez une connexion de base de données à l’équilibreur de charge de la base de données. Toutefois, la mise en grappe de la base de données peut être complexe et vous pouvez la configurer. Adobe ne fait aucune recommandation spécifique pour la mise en grappe de la base de données.

  Pour plus d’informations, voir la [documentation MySQL](https://dev.mysql.com/doc/refman/5.6/en/mysql-cluster.html).

### Résolution des problèmes de connexion

Si vous rencontrez des problèmes de connexion à l’un des hôtes, commencez par envoyer un ping à l’autre hôte pour vérifier qu’il est accessible. Vous devrez peut-être autoriser les connexions d’un hôte à un autre en modifiant les règles de pare-feu et SELinux (si vous utilisez SELinux).

## Créer la connexion distante

Pour créer une connexion distante :

1. Sur votre serveur de base de données, en tant qu’utilisateur disposant des privilèges `root`, ouvrez votre fichier de configuration MySQL.

   Pour le localiser, saisissez la commande suivante :

   ```bash
   mysql --help
   ```

   L’emplacement s’affiche comme suit :

   ```
   Default options are read from the following files in the given order:
   /etc/my.cnf /etc/mysql/my.cnf /usr/etc/my.cnf ~/.my.cnf
   ```

   >[!NOTE]
   >
   >Sur Ubuntu 16, le chemin est généralement `/etc/mysql/mysql.conf.d/mysqld.cnf`.

1. Recherchez le fichier de configuration `bind-address`.

   Si elle existe, modifiez la valeur comme suit.

   S’il n’existe pas, ajoutez-le à la section `[mysqld]`.

   ```conf
   bind-address = <ip address of your web node>
   ```

   Voir la [documentation MySQL](https://dev.mysql.com/doc/refman/5.6/en/server-options.html), en particulier si vous disposez d’un serveur web en grappe.

1. Enregistrez vos modifications dans le fichier de configuration et quittez l’éditeur de texte.
1. Redémarrez le service MySQL :

   * CentOS : `service mysqld restart`

   * Ubuntu : `service mysql restart`

   >[!NOTE]
   >
   >Si MySQL ne démarre pas, recherchez la source du problème dans syslog. Résolvez le problème à l’aide de la [documentation MySQL](https://dev.mysql.com/doc/refman/5.6/en/server-options.html#option_mysqld_bind-address) ou d’une autre source de référence.

## Accorder l’accès à un utilisateur de base de données

Pour permettre à votre noeud web de se connecter au serveur de base de données, vous devez accorder à un utilisateur de base de données de noeud web l’accès à la base de données sur le serveur distant.

Cet exemple donne à l’utilisateur de la base de données `root` un accès complet à la base de données sur l’hôte distant.

Pour accorder l’accès à un utilisateur de la base de données :

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
   >Si votre serveur web est en grappe, saisissez la même commande sur chaque serveur web. Vous devez utiliser le même nom d’utilisateur pour chaque serveur web.

## Vérification de l’accès à la base de données

Sur l’hôte de noeud web, saisissez la commande suivante pour vérifier le fonctionnement de la connexion :

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

Si votre serveur web est en grappe, saisissez la commande sur chaque hôte de serveur web.

## Installation d’Adobe Commerce

Lorsque vous installez Adobe Commerce, vous devez indiquer les informations suivantes :

* L’URL de base (également appelée *adresse de magasin*) spécifie le nom d’hôte ou l’adresse IP du *noeud web*
* L’hôte de base de données est l’adresse IP du *serveur de base de données distant* (ou équilibreur de charge si le serveur de base de données est en grappe).
* Le nom d’utilisateur de la base de données est l’utilisateur de base de données *noeud web local* auquel vous avez donné accès.
* Mot de passe de la base de données est le mot de passe de l’utilisateur du noeud web local.
* Le nom de la base de données est le nom de la base de données sur le serveur distant
