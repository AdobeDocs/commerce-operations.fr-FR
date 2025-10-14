---
title: Configuration du système de build
description: Découvrez comment déployer Commerce dans un système de version.
feature: Configuration, Build, Deploy
exl-id: f6daf5c6-6d12-46b0-b775-76791bacea53
source-git-commit: dcc283b901917e3681863370516771763ae87462
workflow-type: tm+mt
source-wordcount: '367'
ht-degree: 0%

---

# Configuration du système de build

Vous pouvez disposer d’un système de version qui répond aux exigences suivantes :

- Tout le code Commerce est sous contrôle de code source dans le même référentiel que les systèmes de développement et de production
- Assurez-vous que tous les éléments suivants sont _inclus_ dans le contrôle de code source :

   - `app/etc/config.php`
   - Répertoire `generated` (et sous-répertoires)
   - répertoire `pub/media`
   - Répertoire `pub/media/wysiwyg` (et sous-répertoires)
   - Répertoire `pub/static` (et sous-répertoires)

- Une version PHP compatible doit être installée
- Composer doit être installé.
- La propriété et les autorisations du système de fichiers sont définies, comme indiqué dans la section [Prérequis pour les systèmes de développement, de version et de production](../deployment/technical-details.md).
- Le système de build n’a pas besoin que Commerce soit installé, mais le code doit être disponible pour lui.

>[!WARNING]
>
>La connexion à la base de données n’est pas requise si elle figure déjà dans `config.php` ; consultez la section [&#x200B; Exporter la configuration](../cli/export-configuration.md). Dans le cas contraire, la connexion à la base de données est requise.

>[!INFO]
>
>La machine de génération peut se trouver sur son propre hôte ou sur le même hôte qu’un système Commerce installé.

## Configuration de la machine de génération

Les sections suivantes expliquent comment configurer la machine de génération.

### Installer le compositeur

Tout d’abord, vérifiez si le compositeur est déjà installé :

Dans une invite de commande, saisissez l’une des commandes suivantes :

- `composer --help`
- `composer list --help`

Si l’aide de la commande s’affiche, Composer est déjà installé.

Si une erreur s’affiche, procédez comme suit pour installer le compositeur.

Pour installer le compositeur :

1. Modifiez ou créez un répertoire vide sur votre serveur Commerce.

1. Saisissez les commandes suivantes :

   ```bash
   curl -sS https://getcomposer.org/installer | php
   ```

   ```bash
   mv composer.phar /usr/local/bin/composer
   ```

Pour obtenir des options d’installation supplémentaires, consultez la [documentation d’installation du compositeur][composer].

### Installer PHP

Installez PHP sur [CentOS] ou [Ubuntu].

### Configurer le système de génération

Pour configurer le système de génération :

1. Connectez-vous au système de génération en tant que propriétaire du système de fichiers ou passez à ce système.
1. Récupérez le code Commerce du contrôle de code source.

   Si vous utilisez Git, utilisez la commande suivante :

   ```bash
   git clone [-b <branch name>] <repository URL>
   ```

1. Accédez au répertoire racine Commerce et saisissez les informations suivantes :

   ```bash
   composer install
   ```

1. Attendez que les dépendances soient mises à jour.
1. Définir la propriété :

   ```bash
   chown -R <Commerce file system owner name>:<web server username> .
   ```

   Par exemple,

   ```bash
   chown -R commerce-username:apache .
   ```

1. Si vous utilisez Git, ouvrez `.gitignore` dans un éditeur de texte.
1. Commencez chacune des lignes suivantes par un caractère `#` pour les commenter :

   ```conf
   # app/etc/config.php
   # pub/media/*
   # generated/*
   # pub/media/*.*
   # pub/media/wysiwyg/*
   # pub/static/*
   ```

1. Enregistrez vos modifications dans `.gitignore` et quittez l’éditeur de texte.
1. Si vous utilisez Git, validez la modification à l’aide des commandes suivantes :

   ```bash
   git add .gitignore && git commit -m "Modify .gitignore for build and production"
   ```

   Pour plus d’informations[`.gitignore` voir la référence &#x200B;](../reference/config-reference-gitignore.md) .

1. Le système de génération doit utiliser [mode par défaut](../bootstrap/application-modes.md#default-mode) ou [mode développeur](../bootstrap/application-modes.md#developer-mode) :

   ```bash
   bin/magento deploy:mode:set <mode>
   ```

   `<mode>` est obligatoire. Il peut être `default` ou `developer`.

<!-- Link Definitions -->

[CentOS]: https://wiki.centos.org/HowTos/php7
[composer]: https://getcomposer.org/download/
[Ubuntu]: https://help.ubuntu.com/lts/serverguide/php.html
