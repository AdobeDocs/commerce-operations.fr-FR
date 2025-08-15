---
title: Désinstaller les thèmes
description: Pour désinstaller un thème Adobe Commerce, procédez comme suit.
feature: Install, Themes
exl-id: 73150e8c-2d83-4479-b96b-75f41fd9c842
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '449'
ht-degree: 0%

---

# Désinstaller les thèmes

Avant d’utiliser cette commande, vous devez connaître le chemin d’accès relatif à votre thème. Les thèmes se trouvent dans un sous-répertoire de `<magento_root>/app/design/<area name>`. Vous devez spécifier le chemin d’accès au thème commençant par la zone, qui est `frontend` (pour les thèmes de storefront) ou `adminhtml` (pour les thèmes d’administration).

Par exemple, le chemin d’accès au thème Luma fourni avec Adobe Commerce est `frontend/Magento/luma`.

Pour plus d’informations sur les thèmes, voir [structure des thèmes](https://developer.adobe.com/commerce/frontend-core/guide/themes/structure/).

## Présentation de la désinstallation des thèmes

Cette section explique comment désinstaller un ou plusieurs thèmes, en incluant éventuellement le code des thèmes du système de fichiers. Vous pouvez d’abord créer des sauvegardes afin de pouvoir restaurer les données ultérieurement.

Cette commande désinstalle *uniquement* les thèmes spécifiés dans `composer.json` ; en d’autres termes, les thèmes fournis sous la forme de packages du compositeur. Si votre thème n’est pas un package de compositeur, vous devez le désinstaller manuellement en :

* Mise à jour des informations du nœud `parent` dans `theme.xml` pour supprimer les références au thème.
* Suppression du code de thème du système de fichiers.

  [Plus d’informations sur l’héritage des thèmes](https://developer.adobe.com/commerce/frontend-core/guide/themes/inheritance/).

## Désinstaller les thèmes

Utilisation des commandes :

```bash
bin/magento theme:uninstall [--backup-code] [-c|--clear-static-content] {theme path} ... {theme path}
```

Où

* `{theme path}` est le chemin d’accès relatif au thème, en commençant par le nom de la zone. Par exemple, le chemin d’accès au Thème vierge fourni avec Adobe Commerce est `frontend/Magento/blank`.
* `--backup-code` sauvegarde la base de code comme décrit dans les paragraphes qui suivent.
* `--clear-static-content` nettoie les [fichiers d’affichage statiques](../../configuration/cli/static-view-file-deployment.md) générés, ce qui est nécessaire pour que les fichiers d’affichage statiques s’affichent correctement.

La commande effectue les tâches suivantes :

1. Vérifie que les chemins d’accès au thème spécifiés existent ; dans le cas contraire, la commande s’arrête.
1. Vérifie que le thème est un package du compositeur ; dans le cas contraire, la commande s’arrête.
1. Recherche les dépendances et met fin à la commande s’il existe des dépendances non satisfaites.

   Pour contourner ce problème, vous pouvez soit désinstaller tous les thèmes en même temps, soit désinstaller le en fonction du thème en premier.

1. Vérifie que le thème n’est pas utilisé ; s’il l’est, la commande s’arrête.
1. Vérifie que le thème n’est pas la base du thème virtuel ; si c’est la base d’un thème virtuel, la commande s’arrête.
1. Met le magasin en mode de maintenance.
1. Si `--backup-code` est spécifié, sauvegardez la base de code, en excluant les répertoires `pub/static`, `pub/media` et `var`.

   Le nom du fichier de sauvegarde est `var/backups/<timestamp>_filesystem.tgz`

   Vous pouvez restaurer des sauvegardes à tout moment à l’aide de la commande [`magento setup:rollback`](uninstall-modules.md#roll-back-the-file-system-database-or-media-files).

1. Supprime les thèmes de la table de base de données `theme`.
1. Supprimez des thèmes de la base de code à l’aide de `composer remove`.
1. Nettoie le cache.
1. Nettoie les classes générées
1. Si `--clear-static-content` est spécifié, nettoie [les fichiers d’affichage statiques générés](../../configuration/cli/static-view-file-deployment.md).

Par exemple, si vous tentez de désinstaller un thème dont dépend un autre thème, le message suivant s’affiche :

```
Cannot uninstall frontend/ExampleCorp/SampleModuleTheme because the following package(s) depend on it:
        ExampleCorp/sample-module-theme-depend
```

Une alternative consiste à désinstaller les deux thèmes en même temps comme suit, en sauvegardant la base de code :

```bash
bin/magento theme:uninstall frontend/ExampleCorp/SampleModuleTheme frontend/ExampleCorp/SampleModuleThemeDepend --backup-code
```

Des messages similaires à ce qui suit s’affichent :

```
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
