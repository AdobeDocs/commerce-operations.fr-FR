---
title: Désinstallation des packages de langue
description: Pour désinstaller un package de langue Adobe Commerce, procédez comme suit.
exl-id: 9901aa0b-af1a-4ae9-968f-ac8421060f57
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '209'
ht-degree: 0%

---

# Désinstallation des packages de langue

Cette section explique comment désinstaller un ou plusieurs packages de langue, y compris le code des packages de langue du système de fichiers. Vous pouvez d’abord créer des sauvegardes afin de pouvoir restaurer les données ultérieurement.

Cette commande désinstalle les modules de langue *uniquement* spécifiés dans `composer.json` ; en d’autres termes, les modules de langue fournis en tant que modules du compositeur. Si votre module de langue n’est pas un module du compositeur, vous devez le désinstaller manuellement en supprimant le code du module de langue du système de fichiers.

Vous pouvez restaurer des sauvegardes à tout moment à l’aide de la commande [`magento setup:rollback`](uninstall-modules.md#roll-back-the-file-system-database-or-media-files).

Utilisation des commandes :

```bash
bin/magento i18n:uninstall [-b|--backup-code] {language package name} ... {language package name}
```

La commande de désinstallation du module de langue effectue les tâches suivantes :

1. Vérifie les dépendances ; si tel est le cas, la commande s’arrête.

   Pour contourner ce problème, vous pouvez soit désinstaller tous les modules de langue dépendants en même temps, soit désinstaller les modules de langue dépendants en premier.

1. Si `--backup code` est spécifié, sauvegardez le système de fichiers (à l’exclusion des répertoires `var` et `pub/static`) vers `var/backups/<timestamp>_filesystem.tgz`.
1. Supprime les fichiers de modules de langue du code base à l’aide de `composer remove`.
1. Nettoie le cache.

Par exemple, si vous tentez de désinstaller un module de langue dont dépend un autre module de langue, le message suivant s’affiche :

```
Cannot uninstall vendorname/language-en_us because the following package(s) depend on it:
      vendorname/language-en_gb
```

Une alternative consiste à désinstaller les deux packages de langue après la sauvegarde du code base :

```bash
bin/magento i18n:uninstall vendorname/language-en_us vendorname/language-en_gb --backup-code
```

Messages similaires à l’affichage suivant :

```
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
