---
title: Installez le [!DNL Data Migration Tool]
description: Découvrez comment installer le [!DNL Data Migration Tool] pour transférer des données entre le Magento 1 et le Magento 2.
source-git-commit: d609c497fdf00c5e5f975a5679b1d072cec4f8a2
workflow-type: tm+mt
source-wordcount: '403'
ht-degree: 0%

---


# Installez le [!DNL Data Migration Tool]

>[!INFO]
>
>Versions du Magento et [!DNL Data Migration Tool] doit correspondre.


Assurez-vous que vous utilisez *la même version publiée ;* du Magento 2 et de la variable [!DNL Data Migration Tool]. Par exemple, pour la version 2.2.0 de Magento, vous devez également utiliser la variable [!DNL Data Migration Tool] version 2.2.0.

## Vérifier votre version

Nous utilisons l’une des méthodes suivantes pour vérifier votre version de Magento :

- [Compositeur](#composer-metapackage)
- [Référentiel GitHub](#github-repository)

### Métaphorage du compositeur

Si vous avez téléchargé le logiciel de Magento à l’aide d’une [Compositeur](https://glossary.magento.com/composer) metapackage, saisissez la commande suivante :

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

Si vous êtes actuellement dans la variable `develop` vous devez passer à une <a href="https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/dev_downgrade.html">branche publiée</a> avant de continuer.

Si vous n’avez pas encore installé le logiciel de Magento, [l’installer maintenant](https://devdocs.magento.com/guides/v2.4/install-gde/bk-install-guide.html).
Si vous clonez le référentiel GitHub, veillez à extraire une balise de version comme décrit dans [(Contributeur) Cloner le référentiel du Magento](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/dev_install.html).

## Recherche des versions publiées de [!DNL Data Migration Tool]

Accédez au [Versions](https://github.com/magento/data-migration-tool/releases) de la [!DNL Data Migration Tool] Référentiel GitHub pour rechercher les versions publiées disponibles.

## Installez le [!DNL Data Migration Tool]

Vous pouvez installer le [!DNL Data Migration Tool] de :

- [`repo.magento.com`](#install-from-repomagentocom)
- [GitHub](#install-from-github)

Avant de procéder à l’installation, vérifiez que vous disposez des éléments suivants :

- Toutes les tâches mentionnées dans la variable [Conditions préalables](prerequisites.md) section
- [Vérification de la version](install.md#check-your-version) du logiciel Magento 2

### Installer à partir de `repo.magento.com`

Pour installer le [!DNL Data Migration Tool], vous devez mettre à jour `composer.json` dans le répertoire d’installation racine du Magento pour indiquer l’emplacement de la variable [!DNL Data Migration Tool] module.

1. Connectez-vous à votre serveur de Magento en tant que [propriétaire du système de fichiers](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-sys-perms-over.html).
1. Accédez au répertoire racine du Magento 2.
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

1. Lorsque vous y êtes invité, saisissez le [clés d’authentification](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html). Votre clé publique est votre nom d’utilisateur ; votre clé privée est votre mot de passe.

### Installation à partir de GitHub

Si vous avez cloné Magento 2 à partir du référentiel GitHub, procédez comme suit pour installer le [!DNL Data Migration Tool].

1. Connectez-vous à votre serveur de Magento en tant que [propriétaire du système de fichiers](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-sys-perms-over.html).
1. Accédez au répertoire racine du Magento 2.
1. Saisissez les commandes suivantes :

   ```bash
   composer config repositories.data-migration-tool git https://github.com/magento/data-migration-tool
   ```

   ```bash
   composer require magento/data-migration-tool:<version>
   ```

   where `<version>` doit correspondre à la version du code base de Magento 2.

   Par exemple, pour la version 2.2.0, saisissez :

   ```bash
   composer config repositories.data-migration-tool git https://github.com/magento/data-migration-tool
   ```

   ```bash
   composer require magento/data-migration-tool:2.2.0
   ```

### Vérifier la version de installé [!DNL Data Migration Tool]

1. Modifiez votre [!DNL Data Migration Tool] directory: `<vendor>/magento/data-migration-tool`.

1. Ouvrir [`composer.json`](https://github.com/magento/data-migration-tool/blob/2.4/composer.json) dans un éditeur de texte.

1. Le `version` l’entrée dans ce fichier est la version de la variable [!DNL Data Migration Tool].
