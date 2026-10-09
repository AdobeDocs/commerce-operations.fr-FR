---
title: Désinstallation des packages de langue
description: Pour désinstaller un package de langue Adobe Commerce, procédez comme suit.
exl-id: 9901aa0b-af1a-4ae9-968f-ac8421060f57
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '209'
ht-degree: 0%
---
# Désinstallation des packages de langue

Cette section explique comment désinstaller un ou plusieurs packages de langue, en incluant éventuellement le code des packages de langue du système de fichiers. Vous pouvez d’abord créer des sauvegardes afin de pouvoir restaurer les données ultérieurement.

Cette commande désinstalle *uniquement* les packages de langue spécifiés dans `composer.json` ; en d’autres termes, les packages de langue fournis sous la forme de packages du compositeur. Si votre package de langue n’est pas un package de compositeur, vous devez le désinstaller manuellement en supprimant le code du package de langue du système de fichiers.

Vous pouvez restaurer des sauvegardes à tout moment à l’aide de la commande [`magento setup:rollback`](uninstall-modules.md#roll-back-the-file-system-database-or-media-files).

Utilisation des commandes :

```shell
bin/magento i18n:uninstall [-b|--backup-code] {language package name} ... {language package name}
```

La commande de désinstallation du package de langue effectue les tâches suivantes :

1. Recherche les dépendances ; si c’est le cas, la commande s’arrête.

   Pour contourner ce problème, vous pouvez soit désinstaller tous les packages de langue dépendants en même temps, soit désinstaller les packages de langue dépendants en premier.

1. Si `--backup code` est spécifié, sauvegardez le système de fichiers (à l’exclusion des répertoires `var` et `pub/static`) dans `var/backups/<timestamp>_filesystem.tgz`
1. Supprime les fichiers de package de langue de la base de code à l’aide de `composer remove`.
1. Nettoie le cache.

Par exemple, si vous tentez de désinstaller un package de langue dont dépend un autre package de langue, le message suivant s’affiche :

```text
Cannot uninstall vendorname/language-en_us because the following package(s) depend on it:
      vendorname/language-en_gb
```

Une alternative consiste à désinstaller les deux packages de langue après avoir sauvegardé la base de code :

```shell
bin/magento i18n:uninstall vendorname/language-en_us vendorname/language-en_gb --backup-code
```

Des messages similaires à ce qui suit s’affichent :

```text
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
