---
title: Sauvegarde et restauration du système de fichiers, du support et de la base de données
description: Pour sauvegarder et restaurer votre application Adobe Commerce, procédez comme suit.
exl-id: b9925198-37b4-4456-aa82-7c55d060c9eb
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '506'
ht-degree: 0%

---

# Sauvegarde et restauration du système de fichiers, du support et de la base de données

Cette commande permet de sauvegarder :

* Le système de fichiers (à l’exclusion des répertoires `var` et `pub/static`)
* Le répertoire `pub/media`
* La base de données

Les sauvegardes sont stockées dans le répertoire `var/backups` et peuvent être restaurées à tout moment à l’aide de la commande [`magento setup:rollback`](uninstall-modules.md#roll-back-the-file-system-database-or-media-files).

Après la sauvegarde, vous pouvez [restaurer](#rollback) plus tard.

>[!TIP]
>
>Pour les projets d’infrastructure cloud d’Adobe Commerce, voir [Snapshots et gestion des sauvegardes](https://experienceleague.adobe.com/fr/docs/commerce-cloud-service/user-guide/develop/storage/snapshots) dans le guide _Cloud_.

## Activer les sauvegardes

La fonctionnalité de sauvegarde est désactivée par défaut. Pour l’activer, saisissez la commande d’interface de ligne de commande suivante :

```bash
bin/magento config:set system/backup/functionality_enabled 1
```

>[!WARNING]
>
>**Avis d’obsolescence :**
>&#x200B;>La fonctionnalité de sauvegarde est obsolète à partir des versions 2.1.16, 2.2.7 et 2.3.0. Nous vous recommandons d’étudier d’autres technologies de sauvegarde et outils de sauvegarde binaire (tels que Percona XtraBackup).

## Définir la limite des fichiers ouverts

La restauration d’une sauvegarde précédente peut échouer en silence, ce qui entraîne l’écriture de données incomplètes dans le système de fichiers ou la base de données à l’aide de la commande [`magento setup:rollback`](uninstall-modules.md#roll-back-the-file-system-database-or-media-files).

Parfois, une longue chaîne de requête entraîne une saturation de la mémoire allouée à l’utilisateur en raison d’un trop grand nombre d’appels récursifs.

## Comment définir des fichiers ouverts `ulimit`

Nous vous recommandons de définir la [`ulimit`](https://ss64.com/bash/ulimit.html) des fichiers ouverts pour l’utilisateur du système de fichiers sur une valeur de `65536` ou plus.

Vous pouvez effectuer cette opération sur la ligne de commande ou en faire un paramètre permanent pour l’utilisateur en modifiant son script shell.

Avant de poursuivre, si vous ne l’avez pas déjà fait, passez au [propriétaire du système de fichiers](../prerequisites/file-system/overview.md).

Commande :

```bash
ulimit -s 65536
```

Si nécessaire, vous pouvez augmenter cette valeur.

>[!NOTE]
>
>La syntaxe des `ulimit` de fichiers ouverts dépend du shell UNIX utilisé. Le paramètre précédent doit fonctionner avec CentOS et Ubuntu avec le shell Bash. Toutefois, pour macOS, le paramètre correct est `ulimit -S 65532`. Consultez une page de manuel ou une référence de système d’exploitation pour plus d’informations.

Pour définir éventuellement la valeur dans le shell Bash de l’utilisateur :

1. Si vous ne l’avez pas déjà fait, basculez vers le [propriétaire du système de fichiers](../prerequisites/file-system/overview.md).
1. Ouvrez `/home/<username>/.bashrc` dans un éditeur de texte.
1. Ajoutez la ligne suivante :

   ```bash
   ulimit -s 65536
   ```

1. Enregistrez vos modifications dans `.bashrc` et quittez l’éditeur de texte.

>[!WARNING]
>
>Nous vous recommandons d’éviter de définir une valeur pour [`pcre.recursion_limit`](https://www.php.net/manual/en/pcre.configuration.php) dans le fichier `php.ini`, car cela peut entraîner des restaurations incomplètes sans avertissement d’échec.

## Sauvegarde

Utilisation des commandes :

```bash
bin/magento setup:backup [--code] [--media] [--db]
```

La commande effectue les tâches suivantes :

1. Met le magasin en mode de maintenance.
1. Exécute l&#39;une des options de commande suivantes.

   | Option | Signification | Nom et emplacement du fichier de sauvegarde |
   |--- |--- |--- |
   | `--code` | Sauvegarde le système de fichiers (à l’exclusion des répertoires var et pub/static). | `var/backups/<timestamp>/_filesystem.tgz` |
   | `--media` | Sauvegardez le répertoire pub/media. | `var/backups/<timestamp>/_filesystem_media.tgz` |
   | `--db` | Sauvegardez la base de données. | `var/backups/<timestamp>/_db.sql` |

1. Permet de sortir le magasin du mode de maintenance.

Par exemple, pour sauvegarder le système de fichiers et la base de données :

```bash
bin/magento setup:backup --code --db
```

Des messages similaires à ce qui suit s’affichent :

```
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

## Restaurer

Cette section explique comment restaurer une sauvegarde que vous avez effectuée précédemment. Vous devez connaître le nom du fichier de sauvegarde à restaurer.

Pour trouver le nom de vos sauvegardes, saisissez :

```bash
bin/magento info:backups:list
```

La première chaîne du nom du fichier de sauvegarde est la date et l’heure.

Pour restaurer une sauvegarde précédente, saisissez :

```bash
bin/magento setup:rollback [-c|--code-file="<name>"] [-m|--media-file="<name>"] [-d|--db-file="<name>"]
```

Par exemple, pour restaurer une sauvegarde de média nommée `1440611839_filesystem_media.tgz`, saisissez

```bash
bin/magento setup:rollback -m 1440611839_filesystem_media.tgz
```

Des messages similaires à ce qui suit s’affichent :

```
[SUCCESS]: Media rollback completed successfully.
Please set file permission of bin/magento to executable
Disabling maintenance mode
```
