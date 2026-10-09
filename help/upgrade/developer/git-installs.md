---
title: Mise à niveau d’une installation basée sur Git
description: Mettez à niveau une installation Adobe Commerce que vous avez clonée à partir d’un référentiel Git.
exl-id: a8c42857-7221-4b21-8377-4bfb6308c418
last-update: 2026-04-28T00:00:00.000Z
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
source-wordcount: '118'
ht-degree: 0%
---
# Mise à niveau d’une installation basée sur Git

Cette rubrique explique comment un développeur ou une développeuse contributeur peut mettre à jour Adobe Commerce sans le réinstaller. Si vous n’êtes pas un développeur participant, consultez [Effectuer une mise à niveau](../implementation/perform-upgrade.md).

Pour effectuer la mise à niveau si vous êtes un développeur contributeur :

{{$include /help/_includes/server-login.md}}

1. Enregistrez les modifications apportées au fichier `composer.json`, car les étapes suivantes le remplacent.

1. Créez une sauvegarde de votre fichier `composer.json`.

   ```shell
   cp composer.json composer.json.old
   ```

1. Mettez à jour votre référentiel local pour obtenir le code le plus récent :

   ```shell
   git pull origin develop
   ```

   >[!NOTE]
   >
   >Si `git pull origin develop` échoue, voir [dépannage](https://support.magento.com/hc/en-us/articles/360034229872).

1. Effectuez une comparaison et fusionnez votre fichier `composer.json.old` avec le fichier `composer.json`.

1. Résolvez les dépendances et écrivez les versions exactes dans le fichier `composer.lock`.

   ```shell
   composer update
   ```

1. Mettez à jour la base de données :

   ```shell
   bin/magento setup:upgrade
   ```

1. Nettoyez le cache :

   ```shell
   bin/magento cache:clean
   ```

<!-- Last updated from includes: 2026-04-17 13:49:36 -->
