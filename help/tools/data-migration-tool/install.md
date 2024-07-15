---
title: Installez le  [!DNL Data Migration Tool]
description: Découvrez comment installer le  [!DNL Data Migration Tool]  pour transférer des données entre Magento 1 et Magento 2.
exl-id: 5f57067b-3ce8-4b51-b9ae-f60ae089c4ba
topic: Commerce, Migration
feature: Configuration, Install
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '365'
ht-degree: 0%

---

# Installez le [!DNL Data Migration Tool]

>[!INFO]
>
>Les versions de Magento et [!DNL Data Migration Tool] doivent correspondre.


Assurez-vous d’utiliser *la même version publiée* de Magento 2 et de [!DNL Data Migration Tool]. Par exemple, pour la version 2.2.0 du Magento, vous devez également utiliser la version 2.2.0 de [!DNL Data Migration Tool].

## Vérifier votre version

Nous utilisons l’une des méthodes suivantes pour vérifier votre version de Magento :

- [Compositeur](#composer-metapackage)
- [Référentiel GitHub](#github-repository)

### Métaphorage du compositeur

Si vous avez téléchargé le logiciel de Magento à l’aide d’un métapaquage du compositeur, saisissez la commande suivante :

```bash
php <magento_root>/bin/magento --version
```

### Référentiel GitHub

Si vous avez cloné le référentiel GitHub Magento 2, saisissez les commandes suivantes :

```bash
cd <your Magento 2 clone directory>
```

```bash
git branch
```

Si vous vous trouvez actuellement dans la branche `develop`, vous devez passer à une [branche publiée](https://developer.adobe.com/commerce/contributor/guides/install/change-version/) avant de continuer.

Si vous n&#39;avez pas encore installé le logiciel Adobe Commerce, [installez-le maintenant](../../installation/prerequisites/commerce.md).
Si vous clonez le référentiel GitHub, veillez à extraire une balise de version comme décrit dans [(Contributor) Cloner le référentiel GitHub](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/).

## Rechercher les versions publiées de [!DNL Data Migration Tool]

Accédez à la page [Versions](https://github.com/magento/data-migration-tool/releases) du référentiel GitHub [!DNL Data Migration Tool] pour trouver les versions publiées disponibles.

## Installez le [!DNL Data Migration Tool]

Vous pouvez installer le [!DNL Data Migration Tool] à partir de :

- [`repo.magento.com`](#install-from-repomagentocom)
- [GitHub](#install-from-github)

Avant de procéder à l’installation, vérifiez que vous disposez des éléments suivants :

- Réalisation de toutes les tâches mentionnées dans la section [Conditions préalables](prerequisites.md)
- [Vérification de la version](install.md#check-your-version) du logiciel Magento 2

### Installation à partir de `repo.magento.com`

Pour installer [!DNL Data Migration Tool], vous devez mettre à jour `composer.json` dans le répertoire d’installation racine du Magento afin de fournir l’emplacement du package [!DNL Data Migration Tool].

1. Connectez-vous à votre serveur d’applications en tant que [propriétaire du système de fichiers](../../installation/prerequisites/file-system/overview.md) ou basculez-vous vers cette application.
1. Modifiez le répertoire racine de l’application.
1. Saisissez les commandes suivantes :

   ```bash
   composer config repositories.magento composer https://repo.magento.com
   ```

   ```bash
   composer require magento/data-migration-tool:<version>
   ```

   Où `<version>` doit correspondre à la version du code base de Magento 2.

   Par exemple, pour la version 2.2.0, saisissez :

   ```bash
   composer config repositories.magento composer https://repo.magento.com
   ```

   ```bash
   composer require magento/data-migration-tool:2.2.0
   ```

1. Lorsque vous y êtes invité, saisissez vos [clés d&#39;authentification](../../installation/prerequisites/authentication-keys.md). Votre clé publique est votre nom d’utilisateur ; votre clé privée est votre mot de passe.

### Installation à partir de GitHub

Si vous avez cloné le référentiel GitHub, suivez les étapes ci-dessous pour installer le [!DNL Data Migration Tool].

1. Connectez-vous à votre serveur d’applications en tant que [propriétaire du système de fichiers](../../installation/prerequisites/file-system/overview.md) ou basculez-vous vers cette application.
1. Modifiez le répertoire racine de l’application.
1. Saisissez les commandes suivantes :

   ```bash
   composer config repositories.data-migration-tool git https://github.com/magento/data-migration-tool
   ```

   ```bash
   composer require magento/data-migration-tool:<version>
   ```

   où `<version>` doit correspondre à la version du code base de Magento 2.

   Par exemple, pour la version 2.2.0, saisissez :

   ```bash
   composer config repositories.data-migration-tool git https://github.com/magento/data-migration-tool
   ```

   ```bash
   composer require magento/data-migration-tool:2.2.0
   ```

### Vérifier la version de [!DNL Data Migration Tool] installé

1. Modifiez votre répertoire [!DNL Data Migration Tool] : `<vendor>/magento/data-migration-tool`.

1. Ouvrez [`composer.json`](https://github.com/magento/data-migration-tool/blob/2.4/composer.json) dans un éditeur de texte.

1. L’entrée `version` de ce fichier est la version de [!DNL Data Migration Tool].
