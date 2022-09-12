---
title: Autorisations d’accès aux systèmes de fichiers
description: Découvrez comment configurer le propriétaire ou les propriétaires du système de fichiers de l’application Commerce pour un système de développement et de production.
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '866'
ht-degree: 0%

---


# Autorisations d’accès aux systèmes de fichiers

Cette section explique comment configurer le propriétaire ou les propriétaires du système de fichiers Commerce pour un système de développement et de production. Avant de poursuivre, passez en revue les concepts abordés dans la section [Présentation de la propriété et des autorisations du système de fichiers](../../installation/prerequisites/file-system/overview.md).

Cette rubrique porte sur le développement commercial et les systèmes de production. Si vous installez Commerce, reportez-vous à la section [Définition de la propriété et des autorisations de pré-installation](../../installation/prerequisites/file-system/configure-permissions.md).

Les sections suivantes abordent les exigences relatives à un ou deux propriétaires de système de fichiers. Cela signifie :

- **Un utilisateur**: généralement nécessaire sur les fournisseurs d’hébergement partagés, qui vous permettent d’accéder à un seul utilisateur sur le serveur. Cet utilisateur peut se connecter, transférer des fichiers par FTP et exécuter également le serveur web.

- **Deux utilisateurs**—Nous recommandons deux utilisateurs si vous exécutez votre propre serveur Commerce : une pour transférer des fichiers et exécuter des utilitaires de ligne de commande, ainsi qu’un utilisateur distinct pour le logiciel du serveur web. Dans la mesure du possible, cette option est préférable, car elle est plus sécurisée.

   Vous avez plutôt des utilisateurs distincts :

   - Utilisateur du serveur web, qui exécute l’administrateur et le storefront.

   - A _utilisateur de ligne de commande_, qui est un compte utilisateur local que vous pouvez utiliser pour vous connecter au serveur. Cet utilisateur exécute les tâches Commerce cron et les utilitaires de ligne de commande.

## Propriété du système de fichiers de production pour l’hébergement partagé (un utilisateur)

Pour utiliser la configuration propriétaire unique, vous devez vous connecter à votre serveur Commerce en tant qu’utilisateur exécutant le serveur web. Cela est typique pour l’hébergement partagé.

Étant donné que disposer d’un propriétaire de système de fichiers est moins sécurisé, nous vous recommandons de déployer Commerce en production sur un serveur privé plutôt que sur l’hébergement partagé, si possible.

### Configuration d’un propriétaire pour le mode par défaut ou développeur

En mode développeur ou par défaut, les répertoires suivants doivent pouvoir être écrits par l’utilisateur :

- `vendor`
- `app/etc`
- `pub/static`
- `var`
- Toute autre ressource statique
- `generated/code`
- `generated/metadata`
- `var/view_preprocessed`

Vous pouvez définir ces autorisations à l’aide de la ligne de commande ou d’une application de gestionnaire de fichiers fournie par votre fournisseur d’hébergement partagé.

### Configuration d’un propriétaire pour le mode de production

Lorsque vous êtes prêt à déployer votre site en production, vous devez supprimer l’accès en écriture des fichiers dans les répertoires suivants afin d’améliorer la sécurité :

- `vendor`
- `app/code`
- `app/etc`
- `pub/static`
- Toute autre ressource statique
- `generated/code`
- `generated/metadata`
- `var/view_preprocessed`

Pour mettre à jour des composants, installer de nouveaux composants ou mettre à niveau le logiciel Commerce, tous les répertoires précédents doivent être en lecture-écriture.

#### Rendre les fichiers de code et les répertoires en lecture seule

Pour supprimer les autorisations d’écriture sur les fichiers et répertoires du groupe d’utilisateurs du serveur web :

1. Connectez-vous à votre serveur Commerce.

1. Modifiez le répertoire d’installation de Commerce.

1. Passez en mode de production.

   ```bash
   bin/magento deploy:mode:set production
   ```

1. Supprimez les autorisations d’écriture pour les répertoires suivants.

   ```bash
   find app/code var/view_preprocessed vendor pub/static app/etc generated/code generated/metadata \( -type f -or -type d \) -exec chmod u-w {} + && chmod o-rwx app/etc/env.php
   ```

1. Rendez l’outil de ligne de commande exécutable.

   ```bash
   chmod u+x bin/magento
   ```

#### Rendre les fichiers de code et les répertoires accessibles en écriture

Pour rendre les fichiers et répertoires accessibles en écriture afin de pouvoir mettre à jour les composants et mettre à niveau le logiciel Commerce :

1. Connectez-vous à votre serveur Commerce.
1. Modifiez le répertoire d’installation de Commerce.
1. Saisissez les commandes suivantes :

   ```bash
   chmod -R u+w .
   ```

### Facultatif `magento_umask`

Voir [Éventuellement, définissez un masque](../../installation/next-steps/set-umask.md) dans le _Guide d’installation_.

## Propriété du système de fichiers de production pour l’hébergement privé (deux utilisateurs)

Si vous utilisez votre propre serveur (y compris la configuration du serveur privé d’un fournisseur d’hébergement), il y a deux utilisateurs :

- Le **utilisateur du serveur web**, qui exécute l’administrateur et le storefront.

   Les systèmes Linux ne fournissent généralement pas de shell à cet utilisateur ; vous ne pouvez pas vous connecter au serveur Commerce en tant qu’utilisateur du serveur web ni le changer.

- Le **utilisateur de ligne de commande**, que vous vous connectez à votre serveur Commerce sous ou vers lequel vous basculez.

   Commerce utilise cet utilisateur pour exécuter les commandes de l’interface de ligne de commande et cron.

   >[!INFO]
   >
   >L’utilisateur de ligne de commande est également appelé _propriétaire du système de fichiers_.

Comme ces utilisateurs ont besoin d’un accès aux mêmes fichiers, nous vous recommandons de créer une [groupe partagé](../../installation/prerequisites/file-system/configure-permissions.md#about-the-shared-group) à laquelle ils appartiennent tous deux. Les procédures suivantes supposent que vous avez déjà fait cela.

Consultez l’une des sections suivantes :

- Deux propriétaires de système de fichiers en mode Développeur ou par défaut
- Deux propriétaires de système de fichiers en mode de production

### Configuration de deux propriétaires pour le mode par défaut ou développeur

Les fichiers des répertoires suivants doivent pouvoir être écrits par les utilisateurs en mode développeur et par défaut :

- `var`
- `generated`
- `pub/static`
- `pub/media`
- `app/etc`

Définissez la variable [`setgid`](https://linuxg.net/how-to-set-the-setuid-and-setgid-bit-for-files-in-linux-and-unix/) bit sur les répertoires afin que les autorisations héritent toujours du répertoire parent.

>[!INFO]
>
>`setgid` s’applique uniquement aux répertoires, _not_ aux fichiers .

En outre, les répertoires doivent pouvoir être écrits par le groupe de serveurs web. Comme le contenu peut exister dans ces répertoires, ajoutez les autorisations de manière récursive.

#### Définir les autorisations et `setgid`

Pour définir `setgid` et autorisations pour le mode développeur :

1. Connectez-vous à votre serveur Commerce en tant que propriétaire du système de fichiers ou passez à .
1. Saisissez les commandes suivantes dans l’ordre indiqué :

   ```bash
   cd <magento_root>
   ```

   ```bash
   find var generated pub/static pub/media app/etc -type f -exec chmod g+w {} +
   ```

   ```bash
   find var generated pub/static pub/media app/etc -type d -exec chmod g+ws {} +
   ```

### Deux propriétaires de système de fichiers en mode de production

Lorsque vous êtes prêt à déployer votre site en production, vous devez supprimer l’accès en écriture des fichiers dans les répertoires suivants afin d’améliorer la sécurité :

- `vendor`
- `app/code`
- `app/etc`
- `lib`
- `pub/static`
- Toute autre ressource statique
- `generated/code`
- `generated/metadata`
- `var/view_preprocessed`

#### Rendre les fichiers de code et les répertoires en lecture seule

Pour supprimer les autorisations d’écriture sur les fichiers et répertoires du groupe d’utilisateurs du serveur web :

1. Connectez-vous à votre serveur Commerce.
1. Modifiez le répertoire d’installation de Commerce.
1. En tant que propriétaire du système de fichiers, saisissez la commande suivante pour passer en mode de production :

   ```bash
   bin/magento deploy:mode:set production
   ```

1. Saisissez la commande suivante en tant qu’utilisateur avec `root` privilèges :

   ```bash
   find app/code lib pub/static app/etc generated/code generated/metadata var/view_preprocessed \( -type d -or -type f \) -exec chmod g-w {} + && chmod o-rwx app/etc/env.php
   ```

#### Rendre les fichiers de code et les répertoires accessibles en écriture

Pour rendre les fichiers et répertoires accessibles en écriture afin de pouvoir mettre à jour les composants et mettre à niveau le logiciel Commerce :

1. Connectez-vous à votre serveur Commerce.
1. Modifiez le répertoire d’installation de Commerce.
1. Saisissez la commande suivante :

   ```bash
   find app/code lib var generated vendor pub/static pub/media app/etc \( -type d -or -type f \) -exec chmod g+w {} + && chmod o+rwx app/etc/env.php
   ```
