---
title: Déploiement mono-machine
description: Découvrez comment déployer des mises à jour sur Commerce sur un serveur de production à l’aide de la ligne de commande.
feature: Configuration, Deploy
exl-id: ca73309c-7584-4506-99de-dd933651eeb6
source-git-commit: dcc283b901917e3681863370516771763ae87462
workflow-type: tm+mt
source-wordcount: '186'
ht-degree: 0%

---

# Déploiement mono-machine

Cette rubrique fournit des instructions pour le déploiement de mises à jour de Commerce sur un serveur de production à l’aide de la ligne de commande. Ce processus s’applique aux utilisateurs techniques responsables des magasins s’exécutant sur une seule machine avec certains thèmes et paramètres régionaux installés.

## Hypothèses

- Vous avez installé Commerce à l’aide de [Compositeur](../../installation/composer.md).
- Vous appliquez directement des mises à jour au serveur.

>[!WARNING]
>
>Ce guide ne s’applique pas si vous avez utilisé `git clone` pour installer Commerce.
>Les développeurs qui contribuent doivent utiliser [ce guide][install] pour mettre à jour leur installation Commerce.

## Etapes de déploiement

1. Connectez-vous à votre serveur de production en tant que [propriétaire du système de fichiers](../../installation/prerequisites/file-system/overview.md).

1. Remplacez le répertoire par le répertoire de base de Commerce :

   ```bash
   cd <Commerce base directory>
   ```

1. Activez le mode de maintenance à l&#39;aide de la commande :

   ```bash
   bin/magento maintenance:enable
   ```

1. Appliquez des mises à jour à Commerce ou ses composants à l’aide du modèle de commande suivant :

   ```bash
   composer require-commerce <package> <version> --no-update
   ```

   **package**: Le nom du package que vous souhaitez mettre à jour.

   Par exemple :

   - `magento/product-community-edition`
   - `magento/product-enterprise-edition`

   **version**: La version cible du module que vous souhaitez mettre à jour.

1. Mise à jour des composants avec le compositeur :

   ```bash
   composer update
   ```

1. Mise à jour du schéma et des données de la base de données :

   ```bash
   bin/magento setup:upgrade
   ```

1. Compilez le code :

   ```bash
   bin/magento setup:di:compile
   ```

1. Déployer du contenu statique :

   ```bash
   bin/magento setup:static-content:deploy
   ```

1. Nettoyez le cache :

   ```bash
   bin/magento cache:clean
   ```

1. Quitter le mode de maintenance :

   ```bash
   bin/magento maintenance:disable
   ```

<!-- link definitions -->

[install]: https://developer.adobe.com/commerce/contributor/guides/install/update-dependencies/
