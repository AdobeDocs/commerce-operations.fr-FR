---
title: Désinstallation des modules
description: Pour désinstaller un module Adobe Commerce, procédez comme suit.
exl-id: 66879ef5-47c7-4b61-8c7e-78b60441980a
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '727'
ht-degree: 0%

---

# Désinstallation des modules

Cette section explique comment désinstaller un ou plusieurs modules. Lors de la désinstallation, vous pouvez éventuellement supprimer le code des modules, le schéma de base de données et les données de base de données. Vous pouvez d’abord créer des sauvegardes afin de récupérer les données ultérieurement.

Vous ne devez désinstaller un module que si vous êtes certain de ne pas l’utiliser. Au lieu de désinstaller un module, vous pouvez le désactiver comme décrit dans la section [Activation ou désactivation des modules](manage-modules.md).

>[!NOTE]
>
>Cette commande vérifie que seules les dépendances déclarées dans la variable `composer.json` fichier . Si vous désinstallez un module qui est _not_ défini dans la variable `composer.json` , cette commande désinstalle le module sans vérifier les dépendances. Cette commande effectue les opérations suivantes : _not_, toutefois, supprimez le code du module du système de fichiers. Vous devez utiliser les outils du système de fichiers pour supprimer le code du module (par exemple, `rm -rf <path to module>`). En tant qu’alternative, vous pouvez [disable](manage-modules.md) modules autres que le compositeur.

Utilisation des commandes :

```bash
bin/magento module:uninstall [--backup-code] [--backup-media] [--backup-db] [-r|--remove-data] [-c|--clear-static-content] \
  {ModuleName} ... {ModuleName}
```

Où `{ModuleName}` spécifie le nom du module dans `<VendorName>_<ModuleName>` format. Par exemple, le nom du module client est `Magento_Customer`. Pour obtenir une liste des noms de module, saisissez `magento module:status`

La commande de désinstallation du module effectue les tâches suivantes :

1. Vérifie que les modules spécifiés existent dans la base de code et sont des modules installés par le compositeur.

   Cette commande fonctionne _only_ avec des modules définis comme des modules du compositeur.

1. Vérifie les dépendances avec d’autres modules et termine la commande s’il existe des dépendances non satisfaites.

   Pour contourner ce problème, vous pouvez soit désinstaller tous les modules en même temps, soit désinstaller les modules dépendants en premier.

1. Demande une confirmation.
1. Met le magasin en mode de maintenance.
1. Traite les options de commande suivantes.

   | Option | Signification | Nom et emplacement du fichier de sauvegarde |
   | ---------------- | -------------------------------------------------------------------------------- | -------------------------------------------- |
   | `--backup-code` | Sauvegarde le système de fichiers (à l’exception de `var` et `pub/static` répertoires). | `var/backups/<timestamp>_filesystem.tgz` |
   | `--backup-media` | Sauvegarde le répertoire pub/media. | `var/backups/<timestamp>_filesystem_media.tgz` |
   | `--backup-db` | Sauvegarde la base de données. | `var/backups/<timestamp>_db.gz` |

1. If `--remove-data` est spécifié, supprimez le schéma de base de données et les données définis dans le `Uninstall` classes.

   Pour chaque module spécifié à désinstaller, appelle la fonction `uninstall` dans sa méthode `Uninstall` classe . Cette classe doit hériter de [Magento\Framework\Setup\UninstallInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Setup/UninstallInterface.php).

1. Supprime les modules spécifiés de la fonction `setup_module` table de base de données.
1. Supprime les modules spécifiés de la liste des modules dans la variable [configuration du déploiement](../../configuration/reference/deployment-files.md).
1. Supprime le code de la base de code à l’aide de `composer remove`.

   >[!NOTE]
   >
   >Désinstallation d’un module _always_ exécutions `composer remove`. La variable `--remove-data` supprime les données de la base et le schéma définis par le module `Uninstall` classe .

1. Nettoie le cache.
1. Met à jour les classes générées.
1. If `--clear-static-content` est spécifié, cleans [fichiers d’affichage statique générés](../../configuration/cli/static-view-file-deployment.md).
1. Supprime le magasin hors mode de maintenance.

Par exemple, si vous tentez de désinstaller un module dont dépend un autre module, le message suivant s’affiche :

```terminal
magento module:uninstall Magento_SampleMinimal
    Cannot uninstall module 'Magento_SampleMinimal' because the following module(s) depend on it:
        Magento_SampleModifyContent
```

Une alternative consiste à désinstaller les deux modules après la sauvegarde du système de fichiers du module, `pub/media` fichiers et tables de base de données, mais _not_ suppression du schéma ou des données de base du module :

```bash
bin/magento module:uninstall Magento_SampleMinimal Magento_SampleModifyContent --backup-code --backup-media --backup-db
```

Messages similaires à l’affichage suivant :

```terminal
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
>Des erreurs s’affichent si vous tentez de désinstaller un module avec une dépendance sur un autre module. Dans ce cas, vous ne pouvez pas désinstaller un module ; vous devez désinstaller les deux.

## Restauration des fichiers système de fichiers, base de données ou média

Pour restaurer le code base à l’état dans lequel vous l’avez sauvegardé, utilisez la commande suivante :

```bash
bin/magento setup:rollback [-c|--code-file="<filename>"] [-m|--media-file="<filename>"] [-d|--db-file="<filename>"]
```

Où `<filename>` est le nom du fichier de sauvegarde dans la variable `<app_root>/var/backups` répertoire . Pour afficher la liste des fichiers de sauvegarde, saisissez `magento info:backups:list`

>[!WARNING]
>
>Cette commande supprime les fichiers spécifiés ou la base de données avant de les restaurer. Par exemple, la variable `--media-file` supprime les ressources multimédia sous `pub/media` avant de restaurer à partir du fichier de restauration spécifié. Assurez-vous que vous n’avez pas modifié le système de fichiers ou la base de données que vous souhaitez conserver avant d’utiliser cette commande.

>[!NOTE]
>
>Pour afficher la liste des fichiers de sauvegarde disponibles, saisissez `magento info:backups:list`

Cette commande effectue les tâches suivantes :

1. Met le magasin en mode de maintenance.
1. Vérifie le nom du fichier de sauvegarde.
1. Si vous spécifiez un fichier de restauration de code :

   a. Vérifie que les emplacements de destination de restauration sont modifiables (notez que la variable `pub/static` et `var` Les dossiers sont ignorés).

   b. Supprime tous les fichiers et répertoires sous le répertoire d’installation de votre application.

   c. Extrait le fichier d’archive vers les emplacements de destination.

1. Si vous spécifiez un fichier de restauration de base de données :

   a. Permet de déposer l&#39;intégralité de la base de données.

   b. Restaure la base de données à l’aide de la sauvegarde de la base de données.

1. Si vous spécifiez un fichier de restauration multimédia :

   a. Vérifie que les emplacements de destination de restauration sont modifiables.

   b. Supprime tous les fichiers et répertoires sous `pub/media`

   c. Extrait le fichier d’archive vers les emplacements de destination.

1. Supprime le magasin hors mode de maintenance.

Par exemple, pour restaurer une sauvegarde de code (système de fichiers), saisissez les commandes suivantes dans l’ordre indiqué :

* Afficher une liste de sauvegardes :

  ```bash
  magento info:backups:list
  ```

* Restaurer une sauvegarde de fichier nommée `1433876616_filesystem.tgz`:

  ```bash
  magento setup:rollback --code-file="1433876616_filesystem.tgz"
  ```

  Messages similaires à l’affichage suivant :

  ```terminal
  Enabling maintenance mode
  Code rollback is starting ...
  Code rollback filename: 1433876616_filesystem.tgz
  Code rollback file path: /var/www/html/magento2/var/backups/1433876616_filesystem.tgz
  [SUCCESS]: Code rollback has completed successfully.
  Disabling maintenance mode
  ```

>[!NOTE]
>
>Pour exécuter la variable `magento` sans modifier les répertoires, vous devrez peut-être saisir `cd pwd`.
