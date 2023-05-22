---
title: Configuration du système de création
description: Découvrez comment déployer Commerce dans un système de génération.
feature: Configuration, Build, Deploy
exl-id: f6daf5c6-6d12-46b0-b775-76791bacea53
source-git-commit: dcc283b901917e3681863370516771763ae87462
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---

# Configuration du système de création

Vous pouvez disposer d’un système de génération qui répond aux exigences suivantes :

- L’ensemble du code Commerce est contrôlé par la source dans le même référentiel que les systèmes de développement et de production.
- Assurez-vous que tous les éléments suivants sont : _included_ dans le contrôle de code source :

   - `app/etc/config.php`
   - `generated` répertoire (et sous-répertoires)
   - `pub/media` directory
   - `pub/media/wysiwyg` répertoire (et sous-répertoires)
   - `pub/static` répertoire (et sous-répertoires)

- Doit avoir une version PHP compatible installée
- Composer doit être installé
- Il dispose de la propriété du système de fichiers et d’autorisations définies comme décrit dans [Conditions préalables pour vos systèmes de développement, de génération et de production](../deployment/technical-details.md).
- Le système de génération n’a pas besoin que Commerce soit installé, mais le code doit être disponible.

>[!WARNING]
>
>La connexion à la base de données n’est pas requise si elle est déjà contenue dans `config.php`; see [Exporter la configuration](../cli/export-configuration.md). Sinon, la connexion à la base de données est requise.

>[!INFO]
>
>L’ordinateur de génération peut se trouver sur son propre hôte ou sur le même hôte qu’un système Commerce installé.

## Configuration de l’ordinateur de génération

Les sections suivantes expliquent comment configurer l’appareil de génération.

### Installation du compositeur

Tout d’abord, vérifiez si le compositeur est déjà installé :

Dans une invite de commande, saisissez l’une des commandes suivantes :

- `composer --help`
- `composer list --help`

Si l’aide de la commande s’affiche, le compositeur est déjà installé.

Si une erreur s’affiche, procédez comme suit pour installer le compositeur.

Pour installer le compositeur :

1. Accédez à ou créez un répertoire vide sur votre serveur Commerce.

1. Saisissez les commandes suivantes :

   ```bash
   curl -sS https://getcomposer.org/installer | php
   ```

   ```bash
   mv composer.phar /usr/local/bin/composer
   ```

Pour connaître les autres options d’installation, voir [Documentation d’installation du compositeur][composer].

### Installer PHP

Installer PHP [CentOS] ou [Ubuntu].

### Configuration du système de génération

Pour configurer le système de génération :

1. Connectez-vous au système de génération en tant que propriétaire du système de fichiers ou passez à .
1. Récupérez le code Commerce du contrôle source.

   Si vous utilisez Git, utilisez la commande suivante :

   ```bash
   git clone [-b <branch name>] <repository URL>
   ```

1. Modifiez le répertoire racine de Commerce et saisissez :

   ```bash
   composer install
   ```

1. Attendez la mise à jour des dépendances.
1. Définir la propriété :

   ```bash
   chown -R <Commerce file system owner name>:<web server username> .
   ```

   Par exemple :

   ```bash
   chown -R commerce-username:apache .
   ```

1. Si vous utilisez Git, ouvrez `.gitignore` dans un éditeur de texte.
1. Commencez chacune des lignes suivantes par une `#` pour les commenter :

   ```conf
   # app/etc/config.php
   # pub/media/*
   # generated/*
   # pub/media/*.*
   # pub/media/wysiwyg/*
   # pub/static/*
   ```

1. Enregistrez vos modifications dans `.gitignore` et quittez l’éditeur de texte.
1. Si vous utilisez Git, utilisez les commandes suivantes pour valider la modification :

   ```bash
   git add .gitignore && git commit -m "Modify .gitignore for build and production"
   ```

   Voir [`.gitignore` reference](../reference/config-reference-gitignore.md) pour plus d’informations.

1. Le système de génération doit utiliser [mode par défaut](../bootstrap/application-modes.md#default-mode) ou [mode développeur](../bootstrap/application-modes.md#developer-mode):

   ```bash
   bin/magento deploy:mode:set <mode>
   ```

   `<mode>` est obligatoire. Cela peut être soit `default` ou `developer`.

<!-- Link Definitions -->

[CentOS]: https://wiki.centos.org/HowTos/php7
[composer]: https://getcomposer.org/download/
[Ubuntu]: https://help.ubuntu.com/lts/serverguide/php.html
