---
title: Déploiement sur un seul ordinateur
description: Découvrez comment déployer des mises à jour sur Commerce sur un serveur de production à l’aide de la ligne de commande.
feature: Configuration, Deploy
exl-id: ca73309c-7584-4506-99de-dd933651eeb6
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
  - id: bcd8874c-7b93-5596-bdaa-22660e84df14
    internal-label: Deploy
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
source-wordcount: '189'
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

