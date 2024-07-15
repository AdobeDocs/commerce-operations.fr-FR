---
title: Instructions MySQL
description: Suivez ces étapes pour installer et configurer MySQL et MariaDB pour les installations sur site d’Adobe Commerce.
exl-id: dc5771a8-4066-445c-b1cd-9d5f449ec9e9
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '1037'
ht-degree: 0%

---

# Directives générales pour MySQL

Voir [Configuration requise](../../system-requirements.md) pour connaître les versions prises en charge de MySQL.

Adobe _strong_ vous recommande de respecter la norme suivante lors de la configuration de votre base de données :

* Adobe Commerce utilise les [déclencheurs de base de données MySQL](https://dev.mysql.com/doc/refman/8.0/en/triggers.html) pour améliorer l’accès à la base de données lors de la réindexation. Ils sont créés lorsque le mode indexeur est défini sur [schedule](../../../configuration/cli/manage-indexers.md#configure-indexers). L’application ne prend en charge aucun déclencheur personnalisé dans la base de données, car les déclencheurs personnalisés peuvent introduire des incompatibilités avec les versions futures d’Adobe Commerce.
* Familiarisez-vous avec les [limites potentielles des déclencheurs MySQL](https://dev.mysql.com/doc/mysql-reslimits-excerpt/8.0/en/stored-program-restrictions.html) avant de continuer.
* Pour améliorer la sécurité de votre base de données, activez le mode SQL [`STRICT_ALL_TABLES`](https://dev.mysql.com/doc/refman/5.7/en/sql-mode.html#sqlmode_strict_all_tables) afin d&#39;empêcher le stockage de valeurs de données non valides, ce qui peut entraîner des interactions de base de données indésirables.
* Adobe Commerce ne prend _pas_ en charge la réplication basée sur des instructions MySQL. Assurez-vous d’utiliser _uniquement_ [la réplication basée sur les lignes](https://dev.mysql.com/doc/refman/8.0/en/replication-formats.html).

>[!WARNING]
>
>Adobe Commerce utilise actuellement des instructions `CREATE TEMPORARY TABLE` dans les transactions, qui sont [incompatibles](https://dev.mysql.com/doc/refman/5.7/en/replication-gtids-restrictions.html) avec les mises en oeuvre de base de données utilisent la réplication basée sur GTID, telle que [instances de deuxième génération Google Cloud SQL](https://cloud.google.com/sql/docs/features#differences). Considérez MySQL pour Cloud SQL 8.0 comme une alternative.

>[!NOTE]
>
>Si votre serveur web et votre serveur de base de données se trouvent sur des hôtes différents, effectuez les tâches décrites dans cette rubrique sur l’hôte du serveur de base de données, puis reportez-vous à la section [Configuration d’une connexion à base de données MySQL distante](mysql-remote.md).

## Installation de MySQL sur Ubuntu

Adobe Commerce 2.4 nécessite une installation propre de MySQL 8.0. Suivez les liens ci-dessous pour obtenir des instructions sur l’installation de MySQL sur votre machine.

* [Ubuntu](https://ubuntu.com/server/docs/databases-mysql)
* [CentOS](https://dev.mysql.com/doc/refman/8.0/en/linux-installation-yum-repo.html)

Si vous prévoyez d’importer un grand nombre de produits, vous pouvez augmenter la valeur de [`max_allowed_packet`](https://dev.mysql.com/doc/refman/5.6/en/program-variables.html) supérieure à la valeur par défaut, 16 Mo.

>[!NOTE]
>
>La valeur par défaut s’applique à Adobe Commerce sur les projets d’infrastructure cloud _et_ sur site. Les clients Adobe Commerce sur l’infrastructure cloud Pro doivent ouvrir un ticket d’assistance pour augmenter la valeur `max_allowed_packet`. Les clients Adobe Commerce sur Cloud Infrastructure Starter peuvent augmenter la valeur en mettant à jour la configuration dans le fichier `/etc/mysql/mysql.cnf`.

Pour augmenter la valeur, ouvrez le fichier `/etc/mysql/mysql.cnf` dans un éditeur de texte et recherchez la valeur de `max_allowed_packet`. Enregistrez vos modifications dans le fichier `mysql.cnf`, fermez l’éditeur de texte et redémarrez MySQL (`service mysql restart`).

Pour vérifier éventuellement la valeur que vous définissez, saisissez la commande suivante à une invite `mysql>` :

```sql
SHOW VARIABLES LIKE 'max_allowed_packet';
```

Ensuite, [Configurez l’instance de base de données](#configuring-the-database-instance).

## Modifications de MySQL 8

Pour Adobe Commerce 2.4, nous avons ajouté la prise en charge de MySQL 8.
Cette section décrit les modifications majeures de MySQL 8 que les développeurs doivent connaître.

### Largeur supprimée pour les types entiers (remplissage)

La spécification de largeur d’affichage pour les types de données entiers (TINYINT, SMALLINT, MEDIUMINT, INT, BIGINT) a été abandonnée dans MySQL 8.0.17. Les instructions qui incluent des définitions de type de données dans leur sortie n’affichent plus la largeur d’affichage des types entiers, à l’exception de TINYINT(1). Les connecteurs MySQL supposent que les colonnes TINYINT(1) sont issues de colonnes BOOLÉENNES. Cette exception leur permet de continuer à faire cette hypothèse.

#### Exemple

Description de admin_user sur mysql 8.19

| Champ | Type | Null | Clé | Par défaut | Plus |
| :--- | :--- | :--- | :--- | :--- | :--- |
| user\_id | `int unsigned` | NON | PRI | `NULL` | `auto_increment` |
| `firstname` | `varchar(32)` | OUI | | `NULL` | |
| `lastname` | `varchar(32`) | OUI | | `NULL` | |
| `email` | `varchar(128)` | OUI | | `NULL` | |
| `username` | `varchar(40)` | OUI | UNI | `NULL` | |
| `password` | `varchar(255)` | NON | | `NULL` | |
| `created` | `timestamp` | NON | | `CURRENT_TIMESTAMP` | `DEFAULT_GENERATED` |
| `modified` | `timestamp` | NON | | `CURRENT_TIMESTAMP` | `DEFAULT_GENERATED` lors de la mise à jour `CURRENT_TIMESTAMP` |
| `logdate` | `timestamp` | OUI | | `NULL` | |
| `lognum` | `smallint unsigned` | NON | | `0` | |

A l&#39;exception de _TINYINT(1)_, tous les entiers de remplissage (TINYINT > 1, SMALLINT, MEDIUMINT, INT, BIGINT) doivent être supprimés du fichier `db_schema.xml`.

Pour plus d’informations, voir [https://dev.mysql.com/doc/relnotes/mysql/8.0/en/news-8-0-19.html#mysqld-8-0-19-feature](https://dev.mysql.com/doc/relnotes/mysql/8.0/en/news-8-0-19.html#mysqld-8-0-19-feature).

### Comportement PAR COMMANDE PAR défaut

Avant la version 8.0, les entrées étaient triées par clé étrangère. L’ordre de tri par défaut dépend du moteur utilisé.
Spécifiez toujours un ordre de tri si votre code dépend d’un tri spécifique.

### Qualificateurs ASC et DESC obsolètes pour GROUP BY

À compter de MySQL 8.0.13, les qualificateurs obsolètes `ASC` ou `DESC` pour les clauses `GROUP BY` ont été supprimés. Les requêtes qui utilisaient auparavant le tri `GROUP BY` peuvent produire des résultats différents des versions précédentes de MySQL. Pour produire un ordre de tri donné, fournissez une clause `ORDER BY`.

## Commerce et MySQL 8

Certaines modifications ont été apportées à Adobe Commerce pour prendre correctement en charge MySQL 8.

### Comportement de requête et d’insertion

Adobe Commerce a désactivé le comportement de validation normal en définissant SET SQL_MODE=&#39;&#39; dans `/lib/internal/Magento/Framework/DB/Adapter/Pdo/Mysql.php:424.`. Lorsque la validation est désactivée, il est possible que MySQL tronque les données. Dans MySQL, le comportement de la requête a changé : `Select * on my_table where IP='127.0.0.1'` ne renvoie plus de résultats, car l’adresse IP est désormais correctement considérée comme une chaîne, plutôt que comme un entier.

## Mise à niveau de MySQL 5.7 vers MySQL 8

Pour mettre correctement à jour MySQL de la version 5.7 à la version 8, procédez comme suit dans l’ordre :

1. Mettez à niveau Adobe Commerce vers la version 2.4.0.
Testez tout et assurez-vous que votre système fonctionne comme prévu.
1. Activer le mode de maintenance :

   ```bash
   bin/magento maintenance:enable
   ```

1. Sauvegarder une base de données :

   ```bash
   bin/magento setup:backup --db
   ```

1. Mettez à jour MySQL vers la version 8.
1. Importez les données sauvegardées dans MySQL.
1. Nettoyez le cache :

   ```bash
   bin/magento cache:clean
   ```

1. Désactiver le mode de maintenance :

   ```bash
   bin/magento maintenance:disable
   ```

## Configuration de l&#39;instance de base de données

Cette section explique comment créer une instance de base de données pour Adobe Commerce. Bien qu’une nouvelle instance de base de données soit recommandée, vous pouvez éventuellement installer Adobe Commerce avec une instance de base de données existante.

Pour configurer une instance de base de données MySQL :

1. Connectez-vous à votre serveur de base de données comme n’importe quel utilisateur.
1. Accédez à une invite de commande MySQL :

   ```bash
   mysql -u root -p
   ```

1. Saisissez le mot de passe de l’utilisateur MySQL `root` lorsque vous y êtes invité.
1. Saisissez les commandes suivantes dans l’ordre indiqué pour créer une instance de base de données nommée `magento` avec le nom d’utilisateur `magento` :

   ```sql
   create database magento;
   ```

   ```sql
   create user 'magento'@'localhost' IDENTIFIED BY 'magento';
   ```

   ```sql
   GRANT ALL ON magento.* TO 'magento'@'localhost';
   ```

   ```sql
   flush privileges;
   ```

1. Saisissez `exit` pour quitter l’invite de commande.

1. Vérification de la base de données :

   ```bash
   mysql -u magento -p
   ```

   Si le moniteur MySQL s’affiche, vous avez correctement créé la base de données. Si une erreur s’affiche, répétez les commandes précédentes.

1. Si votre serveur web et votre serveur de base de données se trouvent sur des hôtes différents, effectuez les tâches décrites dans cette rubrique sur l’hôte du serveur de base de données, puis reportez-vous à la section [Configuration d’une connexion à base de données MySQL distante](mysql-remote.md).

   Nous vous recommandons de configurer votre instance de base de données en fonction de vos besoins. Lors de la configuration de votre base de données, veuillez tenir compte des points suivants :

   * Les indexeurs requièrent des valeurs `tmp_table_size` et `max_heap_table_size` plus élevées (par exemple, 64 M). Si vous configurez le paramètre `batch_size`, vous pouvez ajuster cette valeur avec les paramètres de taille de tableau pour améliorer les performances de l’indexeur. Pour plus d’informations, consultez le [Guide d’optimisation](../../../performance/configuration.md) .

   * Pour des performances optimales, assurez-vous que toutes les tables d&#39;index MySQL et Adobe Commerce peuvent être conservées en mémoire (par exemple, configurez `innodb_buffer_pool_size`).

   * La réindexation sur MariaDB 10.4 prend plus de temps que les autres versions de MariaDB ou de MySQL. Voir [Bonnes pratiques de configuration](../../../performance/configuration.md#indexers).

1. Pour que les champs MySQL `TIMESTAMP` suivent les préférences et la composition attendues par l’architecture de schéma déclaratif de l’application, la variable système `explicit_defaults_for_timestamp` doit être définie sur `on`.

   Références :

   * [MySQL 5.7](https://dev.mysql.com/doc/refman/5.7/en/server-system-variables.html#sysvar_explicit_defaults_for_timestamp)
   * [MariaDB](https://mariadb.com/kb/en/server-system-variables/#explicit_defaults_for_timestamp)

   Si ce paramètre n’est pas activé, `bin/magento setup:db:status` signale toujours que le `Declarative Schema is not up to date`.

>[!NOTE]
>
>Le paramètre `explicit_defaults_for_timestamp` est obsolète. Ce paramètre contrôle les comportements TIMESTAMP obsolètes qui seront supprimés dans une prochaine version de MySQL. Lorsque ces comportements sont supprimés, le paramètre `explicit_defaults_for_timestamp` est également supprimé.

>[!WARNING]
>
>Pour Adobe Commerce sur les projets d’infrastructure cloud, le paramètre `explicit_defaults_for_timestamp` pour MySQL (MariaDB) est défini par défaut sur _OFF_.

{{$include /help/_includes/maria-db-config.md}}
