---
title: Désinstallation des packages de langue
description: Pour désinstaller un package de langue Adobe Commerce ou Magento Open Source, procédez comme suit.
source-git-commit: f6f438b17478505536351fa20a051d355f5b157a
workflow-type: tm+mt
source-wordcount: '222'
ht-degree: 0%

---


# Désinstallation des packages de langue

Cette section explique comment désinstaller un ou plusieurs packages de langue, y compris le code des packages de langue du système de fichiers. Vous pouvez d’abord créer des sauvegardes afin de pouvoir restaurer les données ultérieurement.

Cette commande désinstalle *only* modules de langue spécifiés dans `composer.json`; en d’autres termes, les modules de langue fournis comme [Compositeur](https://glossary.magento.com/composer) modules. Si votre [package de langue](https://glossary.magento.com/language-package) n’est pas un module de compositeur, vous devez le désinstaller manuellement en supprimant le code de module de langue du système de fichiers.

Vous pouvez restaurer des sauvegardes à tout moment à l’aide de la variable [`magento setup:rollback`](uninstall-modules.md#roll-back-the-file-system-database-or-media-files) .

Utilisation des commandes :

```bash
bin/magento i18n:uninstall [-b|--backup-code] {language package name} ... {language package name}
```

La commande de désinstallation du module de langue effectue les tâches suivantes :

1. Vérifications des dépendances ; si tel est le cas, la commande s’arrête.

   Pour contourner ce problème, vous pouvez soit désinstaller tous les modules de langue dépendants en même temps, soit désinstaller les modules de langue dépendants en premier.

1. If `--backup code` est spécifié, sauvegardez le système de fichiers (à l’exception de `var` et `pub/static` répertoires) vers `var/backups/<timestamp>_filesystem.tgz`
1. Supprime les fichiers de modules de langue du code base à l’aide de `composer remove`.
1. Nettoie la variable [cache](https://glossary.magento.com/cache).

Par exemple, si vous tentez de désinstaller un module de langue dont dépend un autre module de langue, le message suivant s’affiche :

```terminal
Cannot uninstall vendorname/language-en_us because the following package(s) depend on it:
      vendorname/language-en_gb
```

Une alternative consiste à désinstaller les deux packages de langue après la sauvegarde du code base :

```bash
bin/magento i18n:uninstall vendorname/language-en_us vendorname/language-en_gb --backup-code
```

Messages similaires à l’affichage suivant :

```terminal
Code backup is starting...
Code backup filename: 1435261098_filesystem_code.tgz (The archive can be uncompressed with 7-Zip on Windows systems)
Code backup path: /var/www/html/magento2/var/backups/1435261098_filesystem_code.tgz
[SUCCESS]: Code backup completed successfully.
Loading composer repositories with package information
Updating dependencies (including require-dev)
  - Removing vendorname/language-en_us (dev-master)
Removing Magento/LanguageEn_us
  - Removing vendorname/language-en_br (dev-master)
  - Removing vendorname/language-en_br (dev-master)
Writing lock file
Generating autoload files
```
