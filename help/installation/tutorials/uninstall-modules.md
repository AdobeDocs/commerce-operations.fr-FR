---
title: Désinstallation des modules
description: Pour désinstaller un module Adobe Commerce, procédez comme suit.
exl-id: 66879ef5-47c7-4b61-8c7e-78b60441980a
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '727'
ht-degree: 0%

---

# Désinstallation des modules

Cette section explique comment désinstaller un ou plusieurs modules. Lors de la désinstallation, vous avez la possibilité de supprimer le code, le schéma de base de données et les données de la base de données des modules. Vous pouvez d’abord créer des sauvegardes afin de pouvoir récupérer les données ultérieurement.

Vous ne devez désinstaller un module que si vous êtes certain de ne pas l&#39;utiliser. Au lieu de désinstaller un module, vous pouvez le désactiver comme indiqué dans la section [&#x200B; Activer ou désactiver des modules](manage-modules.md).

>[!NOTE]
>
>Cette commande vérifie que seules les dépendances déclarées dans le fichier `composer.json`. Si vous désinstallez un module qui n’est _pas_ défini dans le fichier `composer.json`, cette commande désinstalle le module sans vérifier les dépendances. Cette commande ne supprime _pas_ le code du module du système de fichiers. Vous devez utiliser des outils de système de fichiers pour supprimer le code du module (par exemple, `rm -rf <path to module>`). Vous pouvez également [désactiver](manage-modules.md) les modules autres que le compositeur.

Utilisation des commandes :

```bash
bin/magento module:uninstall [--backup-code] [--backup-media] [--backup-db] [-r|--remove-data] [-c|--clear-static-content] \
  {ModuleName} ... {ModuleName}
```

Où `{ModuleName}` spécifie le nom du module au format `<VendorName>_<ModuleName>`. Par exemple, le nom du module Client est `Magento_Customer`. Pour obtenir une liste des noms de module, saisissez `magento module:status`

La commande de désinstallation du module effectue les tâches suivantes :

1. Vérifie que les modules spécifiés existent dans la base de code et sont des packages installés par le compositeur.

   Cette commande fonctionne _uniquement_ avec des modules définis comme des packages de compositeur.

1. Recherche les dépendances avec d’autres modules et met fin à la commande s’il existe des dépendances non satisfaites.

   Pour contourner ce problème, vous pouvez soit désinstaller tous les modules en même temps, soit désinstaller les modules dépendants en premier.

1. Demande confirmation pour continuer.
1. Met le magasin en mode de maintenance.
1. Traite les options de commande suivantes.

   | Option | Signification | Nom et emplacement du fichier de sauvegarde |
   | ---------------- | -------------------------------------------------------------------------------- | -------------------------------------------- |
   | `--backup-code` | Sauvegarde le système de fichiers (à l’exclusion des répertoires `var` et `pub/static`). | `var/backups/<timestamp>_filesystem.tgz` |
   | `--backup-media` | Sauvegarde le répertoire pub/media. | `var/backups/<timestamp>_filesystem_media.tgz` |
   | `--backup-db` | Sauvegarde la base de données. | `var/backups/<timestamp>_db.gz` |

1. Si `--remove-data` est spécifié, supprimez le schéma de base de données et les données définies dans les classes `Uninstall` du module.

   Pour chaque module spécifié à désinstaller, appelle la méthode `uninstall` dans sa classe `Uninstall`. Cette classe doit hériter de [Magento\Framework\Setup\UninstallInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Setup/UninstallInterface.php).

1. Supprime les modules spécifiés de la table de base de données `setup_module`.
1. Supprime les modules spécifiés de la liste des modules dans la [configuration de déploiement](../../configuration/reference/deployment-files.md).
1. Supprime le code de la base de code à l’aide de `composer remove`.

   >[!NOTE]
   >
   >La désinstallation d&#39;un module _toujours_ s&#39;exécute `composer remove`. L&#39;option `--remove-data` supprime les données de la base de données et le schéma défini par la classe `Uninstall` du module.

1. Nettoie le cache.
1. Met à jour les classes générées.
1. Si `--clear-static-content` est spécifié, nettoie [les fichiers d’affichage statiques générés](../../configuration/cli/static-view-file-deployment.md).
1. Permet de sortir le magasin du mode de maintenance.

Par exemple, si vous tentez de désinstaller un module dont dépend un autre module, le message suivant s’affiche :

```
magento module:uninstall Magento_SampleMinimal
    Cannot uninstall module 'Magento_SampleMinimal' because the following module(s) depend on it:
        Magento_SampleModifyContent
```

Une alternative consiste à désinstaller les deux modules après avoir sauvegardé le système de fichiers du module, les fichiers `pub/media` et les tables de la base de données, mais _pas_ en supprimant le schéma ou les données de la base de données du module :

```bash
bin/magento module:uninstall Magento_SampleMinimal Magento_SampleModifyContent --backup-code --backup-media --backup-db
```

Des messages similaires à ce qui suit s’affichent :

```
You are about to remove code and/or database tables. Are you sure?[y/N]y
Enabling maintenance mode
Code backup is starting...
Code backup filename: 1435261098_filesystem_code.tgz (The archive can be uncompressed with 7-Zip on Windows systems)
Code backup path: /var/www/html/magento2/var/backups/1435261098_filesystem_code.tgz
[SUCCESS]: Code backup completed successfully.
Media backup is starting...
Media backup filename: 1435261098_filesystem_media.tgz (The archive can be uncompressed with 7-Zip on Windows systems)
Media backup path: /var/www/html/magento2/var/backups/1435261098_filesystem_media.tgz
[SUCCESS]: Media backup completed successfully.
DB backup is starting...
DB backup filename: 1435261098_db.gz (The archive can be uncompressed with 7-Zip on Windows systems)
DB backup path: /var/www/html/magento2/var/backups/1435261098_db.gz
[SUCCESS]: DB backup completed successfully.
You are about to remove a module(s) that might have database data. Remove the database data manually after uninstalling, if desired.
Removing Magento_SampleMinimal, Magento_SampleModifyContent from module registry in database
Removing Magento_SampleMinimal, Magento_SampleModifyContent from module list in deployment configuration
Removing code from Magento codebase:
Loading composer repositories with package information
Updating dependencies (including require-dev)
  - Removing magento/sample-module-modifycontent (1.0.0)
Removing Magento/SampleModifycontent
  - Removing magento/sample-module-minimal (1.0.0)
Removing Magento/SampleMinimal
Writing lock file
Generating autoload files
Cache cleared successfully.
Generated classes cleared successfully.
Alert: Generated static view files were not cleared. You can clear them using the --clear-static-content option. Failure to clear static view files might cause display issues in the Admin and storefront.
Disabling maintenance mode
```

>[!NOTE]
>
>Des erreurs s’affichent si vous tentez de désinstaller un module ayant une dépendance sur un autre module. Dans ce cas, vous ne pouvez pas désinstaller un module ; vous devez désinstaller les deux.

## Restaurez les fichiers du système de fichiers, de la base de données ou du média

Pour restaurer la base de code à l’état où vous l’avez sauvegardée, utilisez la commande suivante :

```bash
bin/magento setup:rollback [-c|--code-file="<filename>"] [-m|--media-file="<filename>"] [-d|--db-file="<filename>"]
```

Où `<filename>` est le nom du fichier de sauvegarde dans le répertoire `<app_root>/var/backups`. Pour afficher la liste des fichiers de sauvegarde, saisissez `magento info:backups:list`

>[!WARNING]
>
>Cette commande supprime les fichiers spécifiés de la base de données avant de les restaurer. Par exemple, l’option `--media-file` supprime les ressources multimédias du répertoire `pub/media` avant de restaurer à partir du fichier de restauration spécifié. Assurez-vous de ne pas avoir modifié le système de fichiers ou la base de données que vous voulez conserver avant d&#39;utiliser cette commande.

>[!NOTE]
>
>Pour afficher la liste des fichiers de sauvegarde disponibles, saisissez `magento info:backups:list`

Cette commande effectue les tâches suivantes :

1. Met le magasin en mode de maintenance.
1. Vérifie le nom du fichier de sauvegarde.
1. Si vous spécifiez un fichier de restauration de code :

   a. Vérifie que les emplacements de destination de restauration sont accessibles en écriture (notez que les dossiers `pub/static` et `var` sont ignorés).

   b. Supprime tous les fichiers et répertoires du répertoire d’installation de votre application.

   c. Extrait le fichier d’archive vers les emplacements de destination.

1. Si vous spécifiez un fichier de restauration de base de données :

   a. Supprime l’intégralité de la base de données.

   b. Restaure la base de données à l’aide de la sauvegarde de la base de données.

1. Si vous spécifiez un fichier de restauration de média :

   a. Vérifie que les emplacements de destination de restauration sont accessibles en écriture.

   b. Supprime tous les fichiers et répertoires sous `pub/media`

   c. Extrait le fichier d’archive vers les emplacements de destination.

1. Permet de sortir le magasin du mode de maintenance.

Par exemple, pour restaurer une sauvegarde de code (c’est-à-dire de système de fichiers), saisissez les commandes suivantes dans l’ordre indiqué :

* Afficher une liste des sauvegardes :

  ```bash
  magento info:backups:list
  ```

* Restaurez une sauvegarde de fichier nommée `1433876616_filesystem.tgz` :

  ```bash
  magento setup:rollback --code-file="1433876616_filesystem.tgz"
  ```

  Des messages similaires à ce qui suit s’affichent :

  ```
  Enabling maintenance mode
  Code rollback is starting ...
  Code rollback filename: 1433876616_filesystem.tgz
  Code rollback file path: /var/www/html/magento2/var/backups/1433876616_filesystem.tgz
  [SUCCESS]: Code rollback has completed successfully.
  Disabling maintenance mode
  ```

>[!NOTE]
>
>Pour exécuter à nouveau la commande `magento` sans modifier les répertoires, vous devrez peut-être saisir `cd pwd`.
