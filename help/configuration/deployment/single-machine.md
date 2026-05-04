---
title: Déploiement sur un seul ordinateur
description: Découvrez comment déployer des mises à jour sur Commerce sur un serveur de production à l’aide de la ligne de commande.
feature: Configuration, Deploy
exl-id: ca73309c-7584-4506-99de-dd933651eeb6
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '188'
ht-degree: 1%

---

# Déploiement sur un seul ordinateur

Cette rubrique fournit des instructions pour déployer des mises à jour sur Commerce sur un serveur de production à l’aide de la ligne de commande. Ce processus s’applique aux utilisateurs et utilisatrices techniques responsables des magasins s’exécutant sur une seule machine avec certains thèmes et paramètres régionaux installés.

## Hypothèses

- Vous avez installé Commerce à l’aide du [compositeur](../../installation/composer.md).
- Vous appliquez directement des mises à jour au serveur.

>[!WARNING]
>
>Ce guide ne s’applique pas si vous avez utilisé `git clone` pour installer Commerce.
>Les développeurs contributeurs doivent utiliser [ce guide](https://developer.adobe.com/commerce/contributor/guides/install/update-dependencies) pour mettre à jour leur installation Commerce.

## Étapes de déploiement

1. Connectez-vous au serveur de production en tant que [propriétaire du système de fichiers](../../installation/prerequisites/file-system/overview.md) ou passez à ce serveur.

1. Remplacez le répertoire par le répertoire de base de Commerce :

   ```shell
   cd <Commerce base directory>
   ```

1. Activez le mode de maintenance à l&#39;aide de la commande :

   ```shell
   bin/magento maintenance:enable
   ```

1. Appliquez les mises à jour à Commerce ou à ses composants à l’aide du modèle de commande suivant :

   ```shell
   composer require-commerce <package> <version> --no-update
   ```

   **package** : nom du package que vous souhaitez mettre à jour.

   Par exemple :

   - `magento/product-community-edition`
   - `magento/product-enterprise-edition`

   **version** : version cible du package à mettre à jour.

1. Mettre à jour les composants avec le compositeur :

   ```shell
   composer update
   ```

1. Mettre à jour le schéma et les données de la base :

   ```shell
   bin/magento setup:upgrade
   ```

1. Compilez le code :

   ```shell
   bin/magento setup:di:compile
   ```

1. Déployez du contenu statique :

   ```shell
   bin/magento setup:static-content:deploy
   ```

1. Nettoyez le cache :

   ```shell
   bin/magento cache:clean
   ```

1. Quitter le mode de maintenance :

   ```shell
   bin/magento maintenance:disable
   ```

