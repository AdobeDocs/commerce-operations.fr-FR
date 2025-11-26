---
title: Instructions MySQL
description: Pour installer et configurer MySQL et MariaDB pour les installations sur site d’Adobe Commerce, procédez comme suit.
exl-id: dc5771a8-4066-445c-b1cd-9d5f449ec9e9
source-git-commit: 2d17da1f8cbda1462839ad2fa3ea569833443827
workflow-type: tm+mt
source-wordcount: '1037'
ht-degree: 0%

---

# Directives générales concernant MySQL

Voir [Configuration requise](../../system-requirements.md) pour connaître les versions prises en charge de MySQL.

Adobe _fortement_ vous recommande de respecter la norme suivante lors de la configuration de votre base de données :

* Adobe Commerce utilise [déclencheurs de base de données MySQL](https://dev.mysql.com/doc/refman/8.0/en/triggers.html) pour améliorer l’accès à la base de données lors de la réindexation. Ils sont créés lorsque le mode d’indexeur est défini sur [schedule](../../../configuration/cli/manage-indexers.md#configure-indexers). L’application ne prend en charge aucun déclencheur personnalisé dans la base de données, car les déclencheurs personnalisés peuvent introduire des incompatibilités avec les futures versions d’Adobe Commerce.
* Familiarisez-vous avec [ces limites potentielles de déclencheur MySQL](https://dev.mysql.com/doc/mysql-reslimits-excerpt/8.0/en/stored-program-restrictions.html) avant de continuer.
* Pour améliorer la posture de sécurité de votre base de données, activez le mode SQL [`STRICT_ALL_TABLES`](https://dev.mysql.com/doc/refman/5.7/en/sql-mode.html#sqlmode_strict_all_tables) pour empêcher le stockage de valeurs de données non valides, ce qui peut entraîner des interactions de base de données indésirables.
* Adobe Commerce ne prend _pas_ en charge la réplication basée sur les instructions MySQL. Veillez à utiliser _uniquement_ [réplication basée sur les lignes](https://dev.mysql.com/doc/refman/8.0/en/replication-formats.html).

>[!WARNING]
>
>Adobe Commerce utilise actuellement des instructions `CREATE TEMPORARY TABLE` dans les transactions, qui sont [incompatibles](https://dev.mysql.com/doc/refman/5.7/en/replication-gtids-restrictions.html) avec les implémentations de base de données qui utilisent la réplication basée sur GTID, telles que les [instances de deuxième génération Google Cloud SQL](https://cloud.google.com/sql/docs/features#differences). Considérez MySQL pour Cloud SQL 8.0 comme une alternative.

>[!NOTE]
>
>Si votre serveur web et votre serveur de base de données se trouvent sur des hôtes différents, effectuez les tâches décrites dans cette rubrique sur l’hôte du serveur de base de données, puis consultez [Configurer une connexion à la base de données MySQL distante](mysql-remote.md).

## Installation de MySQL sur Ubuntu

Adobe Commerce 2.4 nécessite une installation correcte de MySQL 8.0. Suivez les liens ci-dessous pour obtenir des instructions sur l’installation de MySQL sur votre ordinateur.

* [&#x200B; Ubuntu &#x200B;](https://ubuntu.com/server/docs/databases-mysql)
* [CentOS](https://dev.mysql.com/doc/refman/8.0/en/linux-installation-yum-repo.html)

Si vous prévoyez d’importer un grand nombre de produits, vous pouvez augmenter la valeur de [`max_allowed_packet`](https://dev.mysql.com/doc/refman/5.6/en/program-variables.html) de 16 Mo par défaut, soit une valeur supérieure à la valeur par défaut.

>[!NOTE]
>
>La valeur par défaut s’applique aux projets d’infrastructure cloud _et_ sur site d’Adobe Commerce. Les clients Adobe Commerce sur les infrastructures cloud Pro doivent ouvrir un ticket d’assistance pour augmenter la valeur du `max_allowed_packet`. Les clients Adobe Commerce sur les infrastructures cloud de Starter peuvent augmenter la valeur de en mettant à jour la configuration dans le fichier `/etc/mysql/mysql.cnf`.

Pour augmenter la valeur, ouvrez le fichier `/etc/mysql/mysql.cnf` dans un éditeur de texte et recherchez la valeur de `max_allowed_packet`. Enregistrez vos modifications dans le fichier `mysql.cnf`, fermez l’éditeur de texte et redémarrez MySQL (`service mysql restart`).

Pour vérifier éventuellement la valeur que vous définissez, saisissez la commande suivante à l’invite de `mysql>` :

```sql
SHOW VARIABLES LIKE 'max_allowed_packet';
```

Ensuite, [&#x200B; Configurer l’instance de base de données &#x200B;](#configuring-the-database-instance).

## Modifications de MySQL 8

Pour Adobe Commerce 2.4, nous avons ajouté la prise en charge de MySQL 8.
Cette section décrit les modifications majeures apportées à MySQL 8 que les développeurs doivent connaître.

### Suppression de la largeur pour les types entiers (remplissage)

La spécification de largeur d’affichage pour les types de données entiers (TINYINT, SMALLINT, MEDIUMINT, INT, BIGINT) a été abandonnée dans MySQL 8.0.17. Les instructions qui incluent des définitions de type de données dans leur sortie n&#39;affichent plus la largeur d&#39;affichage pour les types entiers, à l&#39;exception de TINYINT(1). Les connecteurs MySQL supposent que les colonnes TINYINT(1) proviennent de colonnes BOOLÉENNES. Cette exception leur permet de continuer à faire cette supposition.

#### Exemple

Décrire admin_user dans mysql 8.19

| Champ | Type | Null | Clé | Par défaut | Supplémentaire |
| :--- | :--- | :--- | :--- | :--- | :--- |
| user\_id | `int unsigned` | NON | PRI | `NULL` | `auto_increment` |
| `firstname` | `varchar(32)` | OUI | | `NULL` | |
| `lastname` | `varchar(32`) | OUI | | `NULL` | |
| `email` | `varchar(128)` | OUI | | `NULL` | |
| `username` | `varchar(40)` | OUI | UNI | `NULL` | |
| `password` | `varchar(255)` | NON | | `NULL` | |
| `created` | `timestamp` | NON | | `CURRENT_TIMESTAMP` | `DEFAULT_GENERATED` |
| `modified` | `timestamp` | NON | | `CURRENT_TIMESTAMP` | `DEFAULT_GENERATED` lors de la mise à jour des `CURRENT_TIMESTAMP` |
| `logdate` | `timestamp` | OUI | | `NULL` | |
| `lognum` | `smallint unsigned` | NON | | `0` | |

À l&#39;exception de _TINYINT(1)_, toute marge intérieure entière (TINYINT > 1, SMALLINT, MEDIUMINT, INT, BIGINT) doit être supprimée du fichier `db_schema.xml`.

Pour plus d’informations, voir [https://dev.mysql.com/doc/relnotes/mysql/8.0/en/news-8-0-19.html#mysqld-8-0-19-feature](https://dev.mysql.com/doc/relnotes/mysql/8.0/en/news-8-0-19.html#mysqld-8-0-19-feature).

### Comportement par défaut d’ORDER BY

Avant la version 8.0, les entrées étaient triées en fonction de la clé étrangère. L’ordre de tri par défaut dépend du moteur utilisé.
Indiquez toujours un ordre de tri si votre code dépend d’un tri spécifique.

### Qualificateurs ASC et DESC obsolètes pour GROUP BY

Depuis MySQL 8.0.13, les qualificateurs `ASC` ou `DESC` obsolètes pour les clauses `GROUP BY` ont été supprimés. Les requêtes qui dépendaient auparavant du tri `GROUP BY` peuvent produire des résultats différents des versions précédentes de MySQL. Pour générer un ordre de tri donné, fournissez une clause `ORDER BY`.

## Commerce et MySQL 8

Adobe Commerce a subi quelques modifications afin de prendre correctement en charge MySQL 8.

### Comportement de requête et d’insertion

Adobe Commerce a désactivé le comportement de validation standard en définissant SET SQL_MODE=&#39;&#39; dans `/lib/internal/Magento/Framework/DB/Adapter/Pdo/Mysql.php:424.`. Lorsque la validation est désactivée, il est possible que MySQL tronque les données. Dans MySQL, le comportement de la requête a changé : `Select * on my_table where IP='127.0.0.1'` ne renvoie plus de résultats, car l’adresse IP est désormais correctement vue comme une chaîne, plutôt que comme un entier.

## Mise à niveau de MySQL 5.7 vers MySQL 8

Pour mettre correctement à jour MySQL de la version 5.7 à la version 8, vous devez suivre les étapes suivantes dans l’ordre :

1. Mettez à niveau Adobe Commerce vers la version 2.4.0.
Testez tout et assurez-vous que votre système fonctionne comme prévu.
1. Activez le mode de maintenance :

   ```bash
   bin/magento maintenance:enable
   ```

1. Effectuez une sauvegarde de la base de données :

   ```bash
   bin/magento setup:backup --db
   ```

1. Mettez à jour MySQL vers la version 8.
1. Importez les données sauvegardées dans MySQL.
1. Nettoyez le cache :

   ```bash
   bin/magento cache:clean
   ```

1. Désactivez le mode de maintenance :

   ```bash
   bin/magento maintenance:disable
   ```

## Paramétrer l&#39;instance de base de données

Cette section explique comment créer une instance de base de données pour Adobe Commerce. Bien qu’une nouvelle instance de base de données soit recommandée, vous pouvez éventuellement installer Adobe Commerce avec une instance de base de données existante.

Pour configurer une instance de base de données MySQL, procédez comme suit :

1. Connectez-vous à votre serveur de base de données en tant qu&#39;utilisateur.
1. Accédez à une invite de commande MySQL :

   ```bash
   mysql -u root -p
   ```

1. Entrez le mot de passe de l&#39;utilisateur MySQL `root` lorsque vous y êtes invité.
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

1. Vérifiez la base de données :

   ```bash
   mysql -u magento -p
   ```

   Si le moniteur MySQL s’affiche, vous avez créé la base de données correctement. Si une erreur s’affiche, répétez les commandes précédentes.

1. Si votre serveur web et votre serveur de base de données se trouvent sur des hôtes différents, effectuez les tâches décrites dans cette rubrique sur l’hôte du serveur de base de données, puis consultez [Configurer une connexion à la base de données MySQL distante](mysql-remote.md).

   Nous vous recommandons de configurer votre instance de base de données en fonction de votre activité. Lors de la configuration de votre base de données, tenez compte des points suivants :

   * Les indexeurs nécessitent des valeurs de `tmp_table_size` et de `max_heap_table_size` plus élevées (par exemple, 64 millions). Si vous configurez le paramètre `batch_size`, vous pouvez ajuster cette valeur ainsi que les paramètres de taille de la table pour améliorer les performances de l’indexeur. Pour plus d’informations[&#x200B; consultez le &#x200B;](../../../performance/configuration.md) Guide d’optimisation .

   * Pour des performances optimales, assurez-vous que toutes les tables d’index MySQL et Adobe Commerce peuvent être conservées en mémoire (par exemple, configurez `innodb_buffer_pool_size`).

   * La réindexation sur MariaDB 10.4 prend plus de temps que les autres versions de MariaDB ou MySQL. Voir [&#x200B; Bonnes pratiques de configuration &#x200B;](../../../performance/configuration.md#indexers).

1. Pour que les champs de `TIMESTAMP` MySQL suivent les préférences et la composition attendues par l’architecture de schéma déclaratif de l’application, la variable système `explicit_defaults_for_timestamp` doit être définie sur `on`.

   Références :

   * [MySQL 5.7](https://dev.mysql.com/doc/refman/5.7/en/server-system-variables.html#sysvar_explicit_defaults_for_timestamp)
   * [&#x200B; MariaDB &#x200B;](https://mariadb.com/kb/en/server-system-variables/#explicit_defaults_for_timestamp)

   Si ce paramètre n’est pas activé, `bin/magento setup:db:status` signale toujours que le `Declarative Schema is not up to date`.

>[!NOTE]
>
>Le paramètre `explicit_defaults_for_timestamp` est obsolète. Ce paramètre contrôle les comportements TIMESTAMP obsolètes qui seront supprimés dans une prochaine version de MySQL. Lorsque ces comportements sont supprimés, le paramètre `explicit_defaults_for_timestamp` est également supprimé.

>[!WARNING]
>
>Pour Adobe Commerce sur les projets d’infrastructure cloud, le paramètre `explicit_defaults_for_timestamp` de MySQL (MariaDB) est défini par défaut sur _OFF_.

{{$include /help/_includes/maria-db-config.md}}

<!-- Last updated from includes: 2025-11-25 11:39:51 -->
