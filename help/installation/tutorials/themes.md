---
title: Désinstaller les thèmes
description: Pour désinstaller un thème Adobe Commerce, procédez comme suit.
feature: Install, Themes
exl-id: 73150e8c-2d83-4479-b96b-75f41fd9c842
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '449'
ht-degree: 0%

---

# Désinstaller les thèmes

Avant d’utiliser cette commande, vous devez connaître le chemin d’accès relatif à votre thème. Les thèmes se trouvent dans un sous-répertoire de `<magento_root>/app/design/<area name>`. Vous devez spécifier le chemin d’accès au thème commençant par la zone, qui est : `frontend` (pour les thèmes de vitrine) ou `adminhtml` (pour les thèmes d’administration).

Par exemple, le chemin d’accès au thème Luma fourni avec Adobe Commerce est `frontend/Magento/luma`.

Pour plus d’informations sur les thèmes, voir [structure du thème](https://developer.adobe.com/commerce/frontend-core/guide/themes/structure/).

## Présentation des thèmes de désinstallation

Cette section explique comment désinstaller un ou plusieurs thèmes, incluant éventuellement le code des thèmes du système de fichiers. Vous pouvez d’abord créer des sauvegardes afin de pouvoir restaurer les données ultérieurement.

Cette commande désinstalle *only* les thèmes spécifiés dans `composer.json`; en d’autres termes, les thèmes fournis en tant que modules du compositeur. Si votre thème n’est pas un module de compositeur, vous devez le désinstaller manuellement en :

* Mise à jour de la `parent` informations sur les noeuds dans `theme.xml` pour supprimer les références au thème.
* Suppression du code de thème du système de fichiers.

  [Plus d’informations sur l’héritage du thème](https://developer.adobe.com/commerce/frontend-core/guide/themes/inheritance/).

## Désinstaller les thèmes

Utilisation des commandes :

```bash
bin/magento theme:uninstall [--backup-code] [-c|--clear-static-content] {theme path} ... {theme path}
```

Où

* `{theme path}` est le chemin d’accès relatif au thème, en commençant par le nom de la zone. Par exemple, le chemin vers le thème vierge fourni avec Adobe Commerce est `frontend/Magento/blank`.
* `--backup-code` sauvegarde le code base comme décrit dans les paragraphes qui suivent.
* `--clear-static-content` cleans générés [fichiers d’affichage statique](../../configuration/cli/static-view-file-deployment.md), ce qui est nécessaire pour que les fichiers d’affichage statiques s’affichent correctement.

La commande effectue les tâches suivantes :

1. Vérifie que les chemins de thème spécifiés existent ; dans le cas contraire, la commande s’arrête.
1. Vérifie que le thème est un module de compositeur ; dans le cas contraire, la commande s’arrête.
1. Vérifie les dépendances et termine la commande s’il existe des dépendances non satisfaites.

   Pour contourner ce problème, vous pouvez soit désinstaller tous les thèmes en même temps, soit désinstaller le en fonction du thème en premier.

1. Vérifie que le thème n’est pas utilisé ; si il est utilisé, la commande s’arrête.
1. Vérifie que le thème n’est pas la base du thème virtuel ; si c’est la base d’un thème virtuel, la commande s’arrête.
1. Met le magasin en mode de maintenance.
1. If `--backup-code` est spécifié, sauvegardez le code base, à l’exception de la variable `pub/static`, `pub/media`, et `var` répertoires.

   Le nom du fichier de sauvegarde est `var/backups/<timestamp>_filesystem.tgz`

   Vous pouvez restaurer des sauvegardes à tout moment à l’aide de la variable [`magento setup:rollback`](uninstall-modules.md#roll-back-the-file-system-database-or-media-files) .

1. Supprime les thèmes de la `theme` table de base de données.
1. Supprimez les thèmes de la base de code à l’aide de `composer remove`.
1. Nettoie le cache.
1. Nettoie les classes générées
1. If `--clear-static-content` est spécifié, cleans [fichiers d’affichage statique générés](../../configuration/cli/static-view-file-deployment.md).

Par exemple, si vous tentez de désinstaller un thème dont dépend un autre thème, le message suivant s’affiche :

```terminal
Cannot uninstall frontend/ExampleCorp/SampleModuleTheme because the following package(s) depend on it:
        ExampleCorp/sample-module-theme-depend
```

Une alternative consiste à désinstaller les deux thèmes en même temps, comme suit la sauvegarde du code base :

```bash
bin/magento theme:uninstall frontend/ExampleCorp/SampleModuleTheme frontend/ExampleCorp/SampleModuleThemeDepend --backup-code
```

Messages similaires à l’affichage suivant :

```terminal
Code backup is starting...
Code backup filename: 1435261098_filesystem_code.tgz (The archive can be uncompressed with 7-Zip on Windows systems)
Code backup path: /var/www/html/magento2/var/backups/1435261098_filesystem_code.tgz
[SUCCESS]: Code backup completed successfully.Removing frontend/ExampleCorp/SampleModuleTheme, frontend/ExampleCorp/SampleModuleThemeDepend from database
Loading composer repositories with package information
Updating dependencies (including require-dev)
Removing frontend/ExampleCorp/SampleModuleTheme, frontend/ExampleCorp/SampleModuleThemeDepend from Magento codebase
  - Removing ExampleCorp/sample-module-theme-depend (dev-master)
Removing ExampleCorp/SampleThemeDepend
  - Removing ExampleCorp/sample-module-theme (dev-master)
Removing ExampleCorp/SampleTheme
Writing lock file
Generating autoload files
Cache cleared successfully.
Alert: Generated static view files were not cleared. You can clear them using the --clear-static-content option.
Failure to clear static view files might cause display issues in the Admin and storefront.
Disabling maintenance mode
```

>[!NOTE]
>
>Pour désinstaller un thème d’administration, vous devez également le supprimer de la configuration d’injection de dépendance de votre composant, `<component root directory>/etc/di.xml`.
