---
title: Mise à niveau d’une installation basée sur Git
description: Mettez à niveau une installation Adobe Commerce que vous avez clonée à partir d’un référentiel Git.
exl-id: a8c42857-7221-4b21-8377-4bfb6308c418
source-git-commit: 55512521254c49511100a557a4b00cf3ebee0311
workflow-type: tm+mt
source-wordcount: '110'
ht-degree: 0%

---

# Mise à niveau d’une installation basée sur Git

Cette rubrique explique comment un développeur ou une développeuse contributeur peut mettre à jour Adobe Commerce sans le réinstaller. Si vous n’êtes pas un développeur participant, consultez [Effectuer une mise à niveau](../implementation/perform-upgrade.md).

Pour effectuer la mise à niveau si vous êtes un développeur contributeur :

{{$include /help/_includes/server-login.md}}

1. Enregistrez les modifications apportées au fichier `composer.json`, car les étapes suivantes le remplacent.

1. Créez une sauvegarde de votre fichier `composer.json`.

   ```bash
   cp composer.json composer.json.old
   ```

1. Mettez à jour votre référentiel local pour obtenir le code le plus récent :

   ```bash
   git pull origin develop
   ```

   >[!NOTE]
   >
   >Si `git pull origin develop` échoue, voir [dépannage](https://support.magento.com/hc/en-us/articles/360034229872).

1. Effectuez une comparaison et fusionnez votre fichier `composer.json.old` avec le fichier `composer.json`.

1. Résolvez les dépendances et écrivez les versions exactes dans le fichier `composer.lock`.

   ```bash
   composer update
   ```

1. Mettez à jour la base de données :

   ```bash
   bin/magento setup:upgrade
   ```

1. Nettoyez le cache :

   ```bash
   bin/magento cache:clean
   ```

<!-- Last updated from includes: 2022-09-08 16:00:49 -->
