---
title: Sauvegarde et restauration du système de fichiers, du média et de la base de données
description: Pour sauvegarder et restaurer votre application Adobe Commerce, procédez comme suit.
exl-id: b9925198-37b4-4456-aa82-7c55d060c9eb
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '506'
ht-degree: 0%

---

# Sauvegarde et restauration du système de fichiers, du média et de la base de données

Cette commande permet de sauvegarder :

* Le système de fichiers (à l’exclusion de `var` et `pub/static` répertoires)
* La variable `pub/media` directory
* La base

Les sauvegardes sont stockées dans la variable `var/backups` et peut être restauré à tout moment à l’aide de la variable [`magento setup:rollback`](uninstall-modules.md#roll-back-the-file-system-database-or-media-files) .

Après la sauvegarde, vous pouvez [restauration](#rollback) plus tard.

>[!TIP]
>
>Pour Adobe Commerce sur les projets d’infrastructure cloud, voir [Instantanés et gestion des sauvegardes](https://devdocs.magento.com/cloud/project/project-webint-snap.html) dans le _Guide de Cloud_.

## Activation des sauvegardes

La fonction de sauvegarde est désactivée par défaut. Pour l’activer, saisissez la commande d’interface de ligne de commande suivante :

```bash
bin/magento config:set system/backup/functionality_enabled 1
```

>[!WARNING]
>
>**Avis d’obsolescence :**
>La fonctionnalité de sauvegarde est obsolète depuis les versions 2.1.16, 2.2.7 et 2.3.0. Nous vous recommandons d’étudier des technologies de sauvegarde supplémentaires et des outils de sauvegarde binaires (tels que Percona XtraBackup).

## Définition de la limite des fichiers ouverts

La restauration d’une sauvegarde précédente peut échouer silencieusement, ce qui entraîne l’écriture de données incomplètes dans le système de fichiers ou la base de données à l’aide de la variable [`magento setup:rollback`](uninstall-modules.md#roll-back-the-file-system-database-or-media-files) .

Parfois, une longue chaîne de requête entraîne une insuffisance de mémoire de l’utilisateur en raison d’un trop grand nombre d’appels récursifs.

## Comment définir les fichiers ouverts `ulimit`

Nous vous recommandons de définir les fichiers ouverts. [`ulimit`](https://ss64.com/bash/ulimit.html) pour que l’utilisateur du système de fichiers ait la valeur `65536` ou plus.

Vous pouvez le faire sur la ligne de commande ou en faire un paramètre permanent pour l’utilisateur en modifiant son script shell.

Avant de continuer, si ce n’est pas déjà fait, passez à la [propriétaire du système de fichiers](../prerequisites/file-system/overview.md).

Commande :

```bash
ulimit -s 65536
```

Si nécessaire, vous pouvez définir cette valeur sur une valeur plus élevée.

>[!NOTE]
>
>Syntaxe des fichiers ouverts `ulimit` dépend du shell UNIX utilisé. Le paramètre précédent doit fonctionner avec CentOS et Ubuntu avec le conteneur Bash. Toutefois, pour macOS, le paramètre correct est `ulimit -S 65532`. Pour plus d’informations, consultez la page de gestion ou la référence du système d’exploitation.

Pour définir éventuellement la valeur dans le conteneur Bash de l’utilisateur :

1. Si vous ne l’avez pas déjà fait, passez à la [propriétaire du système de fichiers](../prerequisites/file-system/overview.md).
1. Ouvrir `/home/<username>/.bashrc` dans un éditeur de texte.
1. Ajoutez la ligne suivante :

   ```bash
   ulimit -s 65536
   ```

1. Enregistrez vos modifications dans `.bashrc` et quittez l’éditeur de texte.

>[!WARNING]
>
>Nous vous recommandons d’éviter de définir une valeur pour [`pcre.recursion_limit`](https://www.php.net/manual/en/pcre.configuration.php) dans le `php.ini` car cela peut entraîner des restaurations incomplètes sans préavis d’échec.

## Sauvegarde

Utilisation des commandes :

```bash
bin/magento setup:backup [--code] [--media] [--db]
```

La commande effectue les tâches suivantes :

1. Met le magasin en mode de maintenance.
1. Exécute l’une des options de commande suivantes.

   | Option | Signification | Nom et emplacement du fichier de sauvegarde |
   |--- |--- |--- |
   | `--code` | Sauvegarde le système de fichiers (à l’exception des répertoires var et pub/static). | `var/backups/<timestamp>/_filesystem.tgz` |
   | `--media` | Sauvegardez le répertoire pub/média. | `var/backups/<timestamp>/_filesystem_media.tgz` |
   | `--db` | Sauvegardez la base. | `var/backups/<timestamp>/_db.sql` |

1. Supprime le magasin hors mode de maintenance.

par exemple pour sauvegarder le système de fichiers et la base de données,

```bash
bin/magento setup:backup --code --db
```

Messages similaires à l’affichage suivant :

```terminal
Enabling maintenance mode
Code backup is starting...
Code backup filename: 1434133011_filesystem.tgz (The archive can be uncompressed with 7-Zip on Windows systems)
Code backup path: /var/www/html/magento2/var/backups/1434133011_filesystem.tgz
[SUCCESS]: Code backup completed successfully.
DB backup is starting...
DB backup filename: 1434133011_db.sql
DB backup path: /var/www/html/magento2/var/backups/1434133011_db.sql
[SUCCESS]: DB backup completed successfully.
Disabling maintenance mode
```

## Retour arrière

Cette section explique comment restaurer une sauvegarde que vous avez effectuée précédemment. Vous devez connaître le nom de fichier du fichier de sauvegarde à restaurer.

Pour connaître le nom de vos sauvegardes, saisissez :

```bash
bin/magento info:backups:list
```

La première chaîne du nom du fichier de sauvegarde est l’horodatage.

Pour restaurer une sauvegarde précédente, saisissez :

```bash
bin/magento setup:rollback [-c|--code-file="<name>"] [-m|--media-file="<name>"] [-d|--db-file="<name>"]
```

Par exemple, pour restaurer une sauvegarde multimédia nommée `1440611839_filesystem_media.tgz`, saisissez

```bash
bin/magento setup:rollback -m 1440611839_filesystem_media.tgz
```

Messages similaires à l’affichage suivant :

```terminal
[SUCCESS]: Media rollback completed successfully.
Please set file permission of bin/magento to executable
Disabling maintenance mode
```
