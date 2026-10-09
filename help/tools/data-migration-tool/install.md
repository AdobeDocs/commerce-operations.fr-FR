---
title: Installation du [!DNL Data Migration Tool]
description: Découvrez comment installer le [!DNL Data Migration Tool] pour transférer des données entre Magento 1 et Magento 2.
exl-id: 5f57067b-3ce8-4b51-b9ae-f60ae089c4ba
topic: Commerce, Migration
feature: Configuration, Install
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
  - id: 6388cf7b-8a81-5248-a1e4-7bb57bbe250f
    internal-label: Install
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
source-wordcount: '389'
ht-degree: 0%
---
# Installation du [!DNL Data Migration Tool]

>[!INFO]
>
>Les versions de Magento et de [!DNL Data Migration Tool] doivent correspondre.


Assurez-vous d’utiliser *la même version publiée* de Magento 2 et de la [!DNL Data Migration Tool]. Par exemple, pour Magento version 2.2.0, vous devez également utiliser la version 2.2.0 de [!DNL Data Migration Tool].

## Vérifier votre version

Utilisez l’une des méthodes suivantes pour vérifier votre version de Magento :

- [Compositeur](#composer-metapackage)
- [Référentiel GitHub](#github-repository)

### Métapaquet du compositeur

Si vous avez téléchargé le logiciel Magento à l’aide d’un métapaquet Composer, saisissez la commande suivante :

```shell
php <magento_root>/bin/magento --version
```

### Référentiel GitHub

Si vous avez cloné le référentiel GitHub Magento 2, saisissez les commandes suivantes :

```shell
cd <your Magento 2 clone directory>
```

```shell
git branch
```

Si vous vous trouvez actuellement dans la branche `develop`, vous devez passer à une branche [publiée](https://developer.adobe.com/commerce/contributor/guides/install/change-version) avant de continuer.

Si vous n’avez pas encore installé le logiciel Adobe Commerce, [installez-le maintenant](../../installation/prerequisites/commerce.md).
Si vous clonez le référentiel GitHub, veillez à extraire une balise de version, comme indiqué dans la section [&#x200B; (Contributeur) Cloner le référentiel GitHub &#x200B;](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository).

## Rechercher les versions publiées de [!DNL Data Migration Tool]

Accédez à la page [Versions](https://github.com/magento/data-migration-tool/releases) du référentiel GitHub [!DNL Data Migration Tool] pour trouver les versions publiées disponibles.

## Installation du [!DNL Data Migration Tool]

Vous pouvez installer le [!DNL Data Migration Tool] à partir de :

- [`repo.magento.com`](#install-from-repomagentocom)
- [GitHub](#install-from-github)

Avant l’installation, vérifiez que vous disposez des éléments suivants :

- A terminé toutes les tâches mentionnées dans la section [Conditions préalables](prerequisites.md)
- [Vérification de la version](install.md#check-your-version) du logiciel Magento 2

### Installer à partir de `repo.magento.com`

Pour installer le [!DNL Data Migration Tool], vous devez mettre à jour `composer.json` dans le répertoire d’installation racine Magento afin de fournir l’emplacement du package [!DNL Data Migration Tool].

1. Connectez-vous au serveur d’applications en tant que [propriétaire du système de fichiers](../../installation/prerequisites/file-system/overview.md) ou passez à ce serveur.
1. Accédez au répertoire racine de l’application.
1. Saisissez les commandes suivantes :

   ```shell
   composer config repositories.magento composer https://repo.magento.com
   ```

   ```shell
   composer require magento/data-migration-tool:<version>
   ```

   Où `<version>` doit correspondre à la version de la base de code Magento 2.

   Par exemple, pour la version 2.2.0, saisissez :

   ```shell
   composer config repositories.magento composer https://repo.magento.com
   ```

   ```shell
   composer require magento/data-migration-tool:2.2.0
   ```

1. A l’invite, saisissez vos [clés d’authentification](../../installation/prerequisites/authentication-keys.md). Votre clé publique est votre nom d&#39;utilisateur ; votre clé privée est votre mot de passe.

### Installer à partir de GitHub

Si vous avez cloné le référentiel GitHub, suivez les étapes ci-dessous pour installer le [!DNL Data Migration Tool].

1. Connectez-vous au serveur d’applications en tant que [propriétaire du système de fichiers](../../installation/prerequisites/file-system/overview.md) ou passez à ce serveur.
1. Accédez au répertoire racine de l’application.
1. Saisissez les commandes suivantes :

   ```shell
   composer config repositories.data-migration-tool git https://github.com/magento/data-migration-tool
   ```

   ```shell
   composer require magento/data-migration-tool:<version>
   ```

   où `<version>` doit correspondre à la version de la base de code Magento 2.

   Par exemple, pour la version 2.2.0, saisissez :

   ```shell
   composer config repositories.data-migration-tool git https://github.com/magento/data-migration-tool
   ```

   ```shell
   composer require magento/data-migration-tool:2.2.0
   ```

### Vérification de la version des [!DNL Data Migration Tool] installés

1. Modifiez votre répertoire [!DNL Data Migration Tool] : `<vendor>/magento/data-migration-tool`.

1. Ouvrez [`composer.json`](https://github.com/magento/data-migration-tool/blob/2.4/composer.json) dans un éditeur de texte.

1. L’entrée `version` de ce fichier correspond à la version du [!DNL Data Migration Tool].
