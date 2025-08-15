---
title: Autorisations d’accès aux systèmes de fichiers
description: Découvrez comment configurer le ou les propriétaires du système de fichiers d’application Commerce pour un système de développement et de production.
feature: Configuration, Roles/Permissions
exl-id: 95b27db9-5247-4f58-a9af-1590897d73db
source-git-commit: dcc283b901917e3681863370516771763ae87462
workflow-type: tm+mt
source-wordcount: '864'
ht-degree: 0%

---

# Autorisations d’accès aux systèmes de fichiers

Cette section explique comment configurer le ou les propriétaires du système de fichiers Commerce pour un système de développement et de production. Avant de poursuivre, passez en revue les concepts abordés dans [Présentation de la propriété et des autorisations du système de fichiers](../../installation/prerequisites/file-system/overview.md).

Cette rubrique se concentre sur le développement et les systèmes de production Commerce. Si vous installez Commerce, consultez [Définition de la propriété et des autorisations de préinstallation](../../installation/prerequisites/file-system/configure-permissions.md).

Les sections suivantes traitent des exigences applicables à un ou deux propriétaires de systèmes de fichiers. Cela signifie :

- **Un utilisateur** : généralement nécessaire sur les fournisseurs d&#39;hébergement partagés, qui vous permettent d&#39;accéder à un seul utilisateur sur le serveur. Cet utilisateur peut se connecter, transférer des fichiers via FTP et exécuter également le serveur web.

- **Deux utilisateurs**—Nous vous recommandons d&#39;utiliser deux utilisateurs si vous exécutez votre propre serveur Commerce : un pour transférer les fichiers et exécuter les utilitaires de ligne de commande, et un autre pour le logiciel du serveur Web. Dans la mesure du possible, cette option est préférable, car elle est plus sécurisée.

  Au lieu de cela, vous disposez d’utilisateurs distincts :

   - L’utilisateur du serveur web qui exécute l’administrateur et le storefront.

   - Un _utilisateur de ligne de commande_, qui est un compte utilisateur local que vous pouvez utiliser pour vous connecter au serveur. Cet utilisateur exécute les tâches cron et les utilitaires de ligne de commande de Commerce.

## Propriété du système de fichiers de production pour l’hébergement partagé (un utilisateur)

Pour utiliser la configuration propriétaire unique, vous devez vous connecter à votre serveur Commerce en tant que même utilisateur que celui qui exécute le serveur web. C’est typique pour l’hébergement partagé.

Comme le fait d’avoir un propriétaire de système de fichiers est moins sécurisé, nous vous recommandons de déployer Commerce en production sur un serveur privé plutôt que sur un hébergement partagé, si possible.

### Configurer un propriétaire pour le mode par défaut ou le mode Développeur

En mode développeur ou par défaut, les répertoires suivants doivent pouvoir être écrits par l&#39;utilisateur :

- `vendor`
- `app/etc`
- `pub/static`
- `var`
- Toute autre ressource statique
- `generated/code`
- `generated/metadata`
- `var/view_preprocessed`

Vous pouvez définir ces autorisations à l’aide de la ligne de commande ou d’une application de gestionnaire de fichiers fournie par votre fournisseur d’hébergement partagé.

### Configurer un propriétaire pour le mode de production

Lorsque vous êtes prêt à déployer votre site en production, vous devez supprimer l’accès en écriture aux fichiers des répertoires suivants pour une sécurité accrue :

- `vendor`
- `app/code`
- `app/etc`
- `pub/static`
- Toute autre ressource statique
- `generated/code`
- `generated/metadata`
- `var/view_preprocessed`

Pour mettre à jour des composants, installer de nouveaux composants ou mettre à niveau le logiciel Commerce, tous les répertoires précédents doivent être en lecture/écriture.

#### Rendre les fichiers et répertoires de code en lecture seule

Pour supprimer les autorisations d’écriture sur les fichiers et répertoires du groupe de l’utilisateur du serveur web :

1. Connectez-vous à votre serveur Commerce.

1. Modifiez votre répertoire d’installation Commerce.

1. Passez en mode de production.

   ```bash
   bin/magento deploy:mode:set production
   ```

1. Supprimez les autorisations d’écriture sur les répertoires suivants.

   ```bash
   find app/code var/view_preprocessed vendor pub/static app/etc generated/code generated/metadata \( -type f -or -type d \) -exec chmod u-w {} + && chmod o-rwx app/etc/env.php
   ```

1. Rendez l’outil de ligne de commande exécutable.

   ```bash
   chmod u+x bin/magento
   ```

#### Rendre les fichiers et répertoires de code accessibles en écriture

Pour rendre les fichiers et les répertoires accessibles en écriture afin de pouvoir mettre à jour les composants et mettre à niveau le logiciel Commerce :

1. Connectez-vous à votre serveur Commerce.
1. Modifiez votre répertoire d’installation Commerce.
1. Saisissez les commandes suivantes :

   ```bash
   chmod -R u+w .
   ```

### Définissez éventuellement `magento_umask`

Voir [Vous pouvez éventuellement définir un masque](../../installation/next-steps/set-umask.md) dans le _Guide d’installation_.

## Propriété du système de fichiers de production pour l’hébergement privé (deux utilisateurs)

Si vous utilisez votre propre serveur (y compris la configuration de serveur privé d’un fournisseur d’hébergement), il y a deux utilisateurs :

- L’**utilisateur du serveur web**, qui exécute l’administrateur et le storefront.

  Les systèmes Linux ne fournissent généralement pas de shell à cet utilisateur ; vous ne pouvez pas vous connecter au serveur Commerce en tant qu’utilisateur du serveur web ni passer à cet utilisateur.

- L’**utilisateur de ligne de commande** auquel vous vous connectez à votre serveur Commerce en tant que ou auquel vous passez.

  Commerce utilise cet utilisateur pour exécuter les commandes de l’interface de ligne de commande et cron.

  >[!INFO]
  >
  >L’utilisateur de la ligne de commande est également appelé _propriétaire du système de fichiers_.

Comme ces utilisateurs doivent avoir accès aux mêmes fichiers, nous vous recommandons de créer un [groupe partagé](../../installation/prerequisites/file-system/configure-permissions.md#about-the-shared-group) auquel ils appartiennent tous les deux. Les procédures suivantes supposent que vous l’ayez déjà fait.

Consultez l’une des sections suivantes :

- Deux propriétaires de système de fichiers en mode développeur ou par défaut
- Deux propriétaires de système de fichiers en mode production

### Configurer deux propriétaires pour le mode par défaut ou le mode développeur

Les fichiers des répertoires suivants doivent pouvoir être écrits par les utilisateurs en mode développeur et par défaut :

- `var`
- `generated`
- `pub/static`
- `pub/media`
- `app/etc`

Définissez le bit [`setgid`](https://linuxg.net/how-to-set-the-setuid-and-setgid-bit-for-files-in-linux-and-unix/) sur les répertoires afin que les autorisations héritent toujours du répertoire parent.

>[!INFO]
>
>`setgid` s’applique uniquement aux répertoires, et _pas_ aux fichiers.

En outre, les répertoires doivent pouvoir être écrits par le groupe de serveurs Web. Le contenu pouvant exister dans ces répertoires, ajoutez les autorisations de manière récursive.

#### Définition des autorisations et des `setgid`

Pour définir les `setgid` et les autorisations pour le mode Développeur :

1. Connectez-vous à votre serveur Commerce en tant que propriétaire du système de fichiers ou passez à ce dernier.
1. Saisissez les commandes suivantes dans l&#39;ordre indiqué :

   ```bash
   cd <magento_root>
   ```

   ```bash
   find var generated pub/static pub/media app/etc -type f -exec chmod g+w {} +
   ```

   ```bash
   find var generated pub/static pub/media app/etc -type d -exec chmod g+ws {} +
   ```

### Deux propriétaires de système de fichiers en mode production

Lorsque vous êtes prêt à déployer votre site en production, vous devez supprimer l’accès en écriture aux fichiers des répertoires suivants pour une sécurité accrue :

- `vendor`
- `app/code`
- `app/etc`
- `lib`
- `pub/static`
- Toute autre ressource statique
- `generated/code`
- `generated/metadata`
- `var/view_preprocessed`

#### Rendre les fichiers et répertoires de code en lecture seule

Pour supprimer les autorisations d’écriture sur les fichiers et répertoires du groupe de l’utilisateur du serveur web :

1. Connectez-vous à votre serveur Commerce.
1. Modifiez votre répertoire d’installation Commerce.
1. En tant que propriétaire du système de fichiers, saisissez la commande suivante pour passer en mode de production :

   ```bash
   bin/magento deploy:mode:set production
   ```

1. Saisissez la commande suivante en tant qu’utilisateur disposant de droits d’`root` :

   ```bash
   find app/code lib pub/static app/etc generated/code generated/metadata var/view_preprocessed \( -type d -or -type f \) -exec chmod g-w {} + && chmod o-rwx app/etc/env.php
   ```

#### Rendre les fichiers et répertoires de code accessibles en écriture

Pour rendre les fichiers et les répertoires accessibles en écriture afin de pouvoir mettre à jour les composants et mettre à niveau le logiciel Commerce :

1. Connectez-vous à votre serveur Commerce.
1. Modifiez votre répertoire d’installation Commerce.
1. Saisissez la commande suivante :

   ```bash
   find app/code lib var generated vendor pub/static pub/media app/etc \( -type d -or -type f \) -exec chmod g+w {} + && chmod o+rwx app/etc/env.php
   ```
