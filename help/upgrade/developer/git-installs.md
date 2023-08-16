---
title: Mise à niveau d’une installation basée sur Git
description: Mettez à niveau une installation Adobe Commerce ou Magento Open Source que vous avez clonée à partir d’un référentiel git.
exl-id: a8c42857-7221-4b21-8377-4bfb6308c418
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '122'
ht-degree: 0%

---

# Mettre à niveau une installation basée sur Git

Cette rubrique explique comment un développeur contributeur peut mettre à jour Adobe Commerce ou Magento Open Source sans le réinstaller. Si vous n’êtes pas un développeur contributeur, reportez-vous à la section [Effectuer une mise à niveau](../implementation/perform-upgrade.md).

Pour effectuer une mise à niveau si vous êtes un développeur contributeur :

{{$include /help/_includes/server-login.md}}

1. Enregistrez les modifications apportées au `composer.json` car les étapes suivantes l’écrasent.

1. Créez une sauvegarde de votre `composer.json` fichier .

   ```bash
   cp composer.json composer.json.old
   ```

1. Mettez à jour votre référentiel local pour obtenir le code le plus récent :

   ```bash
   git pull origin develop
   ```

   >[!NOTE]
   >
   >If `git pull origin develop` échec, voir [dépannage](https://support.magento.com/hc/en-us/articles/360034229872).

1. Divisez et fusionnez votre `composer.json.old` avec le fichier `composer.json` fichier .

1. Résolvez les dépendances et écrivez des versions exactes dans la variable `composer.lock` fichier .

   ```bash
   composer update
   ```

1. Mettre à jour la base de données :

   ```bash
   bin/magento setup:upgrade
   ```

1. Nettoyez le cache :

   ```bash
   bin/magento cache:clean
   ```
