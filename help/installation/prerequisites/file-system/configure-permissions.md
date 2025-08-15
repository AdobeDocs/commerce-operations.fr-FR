---
title: Configuration de la propriété et des autorisations des fichiers
description: Pour configurer les autorisations de système de fichiers pour les installations sur site d’Adobe Commerce, procédez comme suit.
exl-id: 2410ee4f-978c-4b71-b3f6-0c042f9f4dc4
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '981'
ht-degree: 0%

---

# Configuration de la propriété et des autorisations des fichiers

Cette rubrique explique comment définir des autorisations de lecture/écriture pour le groupe de serveurs web avant d’installer Adobe Commerce. Cela est nécessaire pour que la ligne de commande puisse écrire des fichiers dans le système de fichiers.

La procédure à suivre est différente selon que vous utilisez [hébergement partagé](#set-permissions-for-one-user-on-shared-hosting) et que vous avez un utilisateur ou un [serveur privé](#set-ownership-and-permissions-for-two-users) et que vous avez deux utilisateurs.

## Définition des autorisations pour un utilisateur sur l’hébergement partagé

Cette section explique comment définir des autorisations de préinstallation si vous vous connectez au serveur d’applications avec le même utilisateur qui exécute également le serveur web. Ce type de configuration est courant dans les environnements d’hébergement partagés.

Pour définir des autorisations avant d’installer l’application, procédez comme suit :

1. Connectez-vous à votre serveur d’applications.
1. Utilisez une application de gestion de fichiers fournie par votre fournisseur d’hébergement partagé pour vérifier que les autorisations d’écriture sont définies sur les répertoires suivants :

   * `vendor` (installation du compositeur ou de l’archive compressée)
   * `app/etc`
   * `pub/static`
   * `var`
   * `generated`
   * Toute autre ressource statique

1. Si vous disposez d’un accès à la ligne de commande, saisissez les commandes suivantes dans l’ordre indiqué :

   ```bash
   cd <app_root>
   ```

   ```bash
   find var generated vendor pub/static pub/media app/etc -type f -exec chmod u+w {} +
   ```

   ```bash
   find var generated vendor pub/static pub/media app/etc -type d -exec chmod u+w {} +
   ```

   ```bash
   chmod u+x bin/magento
   ```

   Pour éventuellement saisir toutes les commandes sur une ligne, saisissez ce qui suit en supposant que l&#39;application soit installée dans `/var/www/html/magento2` :

   ```bash
   cd /var/www/html/magento2 && find var generated vendor pub/static pub/media app/etc -type f -exec chmod u+w {} + && find var generated vendor pub/static pub/media app/etc -type d -exec chmod u+w {} + && chmod u+x bin/magento
   ```

1. Si vous ne l&#39;avez pas déjà fait, obtenez l&#39;application de l&#39;une des façons suivantes :

   * [Métapaquet du compositeur](../../composer.md)
   * [Cloner le référentiel (développeurs et développeuses contributeurs uniquement)](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/)

1. Après avoir défini la propriété et les autorisations du système de fichiers, [installez l’application](../../advanced.md)

>[!NOTE]
>
>Pour restreindre davantage les autorisations après l’installation de l’application, vous pouvez [configurer un masque](../../next-steps/set-umask.md).

## Définir la propriété et les autorisations pour deux utilisateurs

Cette section explique comment définir la propriété et les autorisations de votre propre serveur ou d’une configuration d’hébergement privée. Dans ce type de configuration, vous ne pouvez généralement *pas* vous connecter en tant qu’utilisateur du serveur web ou passer à cet utilisateur. En règle générale, vous vous connectez en tant qu’utilisateur unique et exécutez le serveur web en tant qu’utilisateur différent.

Pour définir la propriété et les autorisations d’un système à deux utilisateurs :

Effectuez les tâches suivantes dans l’ordre indiqué :

* [À propos du groupe partagé](#about-the-shared-group)
* [Créez le propriétaire du système de fichiers et donnez à l&#39;utilisateur un mot de passe fort](#create-the-file-system-owner-and-give-the-user-a-strong-password)
* [Rechercher le groupe de l&#39;utilisateur du serveur web](#find-the-web-server-user-group)
* [Placez le propriétaire du système de fichiers dans le groupe de serveurs web](#put-the-file-system-owner-in-the-web-server-group)
* [Obtenir le logiciel](#get-the-software)
* [Définir la propriété et les autorisations pour le groupe partagé](#set-ownership-and-permissions-for-the-shared-group)

### À propos du groupe partagé

Pour permettre au serveur Web d&#39;écrire des fichiers et des répertoires dans le système de fichiers mais aussi de conserver *propriété* par le propriétaire du système de fichiers, les deux utilisateurs doivent appartenir au même groupe. Cela est nécessaire afin que les deux utilisateurs puissent partager l’accès aux fichiers (y compris les fichiers créés à l’aide d’Admin ou d’autres utilitaires web).

Cette section explique comment créer un propriétaire de système de fichiers et placer cet utilisateur dans le groupe du serveur web. Vous pouvez utiliser un compte utilisateur existant si vous le souhaitez ; nous recommandons à l’utilisateur d’avoir un mot de passe sécurisé pour des raisons de sécurité.

>[!NOTE]
>
>Passez à [Rechercher le groupe d’utilisateurs du serveur web](#find-the-web-server-user-group) si vous envisagez d’utiliser un compte utilisateur existant.

### Créez le propriétaire du système de fichiers et donnez à l&#39;utilisateur un mot de passe fort

Cette section explique comment créer le propriétaire du système de fichiers. (propriétaire du système de fichiers est un autre terme pour *utilisateur de ligne de commande*.)

Pour créer un utilisateur sous CentOS ou Ubuntu, saisissez la commande suivante en tant qu&#39;utilisateur disposant des privilèges `root` :

```bash
adduser <username>
```

Pour attribuer un mot de passe à l&#39;utilisateur, saisissez la commande suivante en tant qu&#39;utilisateur disposant des privilèges `root` :

```bash
passwd <username>
```

Suivez les invites à l&#39;écran pour créer un mot de passe pour l&#39;utilisateur.

>[!WARNING]
>
>Si vous ne disposez pas des privilèges `root` sur votre serveur d’applications, vous pouvez utiliser un autre compte utilisateur local. Assurez-vous que l’utilisateur dispose d’un mot de passe fort et continuez avec [Placez le propriétaire du système de fichiers dans le groupe de serveurs web](#step-3-put-the-file-system-owner-in-the-web-servers-group).

Par exemple, pour créer un utilisateur nommé `magento_user` et lui donner un mot de passe, saisissez :

```bash
sudo adduser magento_user
```

```bash
sudo passwd magento_user
```

>[!WARNING]
>
>Le but de la création de cet utilisateur étant de fournir une sécurité accrue, veillez à créer un [mot de passe sécurisé](https://en.wikipedia.org/wiki/Password_strength).

### Recherche du groupe d’utilisateurs du serveur web

Pour trouver le groupe de l&#39;utilisateur du serveur web :

* CentOS :

  ```bash
  grep -E -i '^user|^group' /etc/httpd/conf/httpd.conf
  ```

  ou

  ```bash
  grep -Ei '^user|^group' /etc/httpd/conf/httpd.conf
  ```

En règle générale, les noms d’utilisateur et de groupe sont tous deux `apache`.

* Ubuntu : `ps aux | grep apache` pour trouver l&#39;utilisateur Apache, puis `groups <apache user>` pour trouver le groupe.

En règle générale, le nom d’utilisateur et le nom du groupe sont tous deux `www-data`.

### Placez le propriétaire du système de fichiers dans le groupe de serveurs web

Pour placer le propriétaire du système de fichiers dans le groupe principal du serveur web (en supposant le nom de groupe Apache standard pour CentOS et Ubuntu), saisissez la commande suivante en tant qu’utilisateur avec des privilèges `root` :

* CentOS : `usermod -a -G apache <username>`
* Ubuntu : `usermod -a -G www-data <username>`

>[!NOTE]
>
>Les options de `-a -G` sont importantes, car elles ajoutent `apache` ou `www-data` en tant que groupe *secondaire* au compte d’utilisateur, ce qui préserve le groupe *principal* de l’utilisateur. L’ajout d’un groupe secondaire à un compte utilisateur permet de [restreindre la propriété et les autorisations des fichiers](#set-ownership-and-permissions-for-two-users) pour s’assurer que les membres d’un groupe partagé n’ont accès qu’à certains fichiers.

Par exemple, pour ajouter l’utilisateur `magento_user` au groupe principal `apache` sous CentOS :

```bash
sudo usermod -a -G apache magento_user
```

Pour confirmer que votre utilisateur est membre du groupe de serveurs web , saisissez la commande suivante :

```bash
groups magento_user
```

L’exemple de résultat suivant montre les groupes principal (`magento`) et secondaire (`apache`) de l’utilisateur.

```bash
magento_user : magento_user apache
```

>[!NOTE]
>
>En règle générale, le nom d’utilisateur et le nom du groupe principal sont identiques.

Pour terminer la tâche, redémarrez le serveur web :

* Ubuntu : `service apache2 restart`
* CentOS : `service httpd restart`

### Obtenir le logiciel

Si vous ne l&#39;avez pas déjà fait, procurez-vous le logiciel de l&#39;une des façons suivantes :

* [Métapaquet du compositeur](../../composer.md)
* [Cloner le référentiel (développeurs et développeuses contributeurs uniquement)](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/)

### Définir la propriété et les autorisations pour le groupe partagé

Pour définir la propriété et les autorisations avant d’installer l’application :

1. Connectez-vous au serveur d’applications en tant que propriétaire du système de fichiers ou passez à ce serveur.
1. Saisissez les commandes suivantes dans l&#39;ordre indiqué :

   ```bash
   cd <app_root>
   ```

   ```bash
   find var generated vendor pub/static pub/media app/etc -type f -exec chmod g+w {} +
   ```

   ```bash
   find var generated vendor pub/static pub/media app/etc -type d -exec chmod g+ws {} +
   ```

   ```bash
   chown -R :<web server group> .
   ```

   ```bash
   chmod u+x bin/magento
   ```

Pour éventuellement saisir toutes les commandes sur une ligne, saisissez ce qui suit en supposant que l&#39;application soit installée dans `/var/www/html/magento2` et que le nom du groupe de serveurs web soit `apache` :

```bash
cd /var/www/html/magento2 && find var generated vendor pub/static pub/media app/etc -type f -exec chmod g+w {} + && find var generated vendor pub/static pub/media app/etc -type d -exec chmod g+ws {} + && chown -R :apache . && chmod u+x bin/magento
```

Dans le cas où les autorisations du système de fichiers sont définies de manière incorrecte et ne peuvent pas être modifiées par le propriétaire du système de fichiers, vous pouvez saisir la commande en tant qu’utilisateur disposant de droits d’`root` :

```bash
cd /var/www/html/magento2 && sudo find var generated vendor pub/static pub/media app/etc -type f -exec chmod g+w {} + && sudo find var generated vendor pub/static pub/media app/etc -type d -exec chmod g+ws {} + && sudo chown -R :apache . && sudo chmod u+x bin/magento
```

## Basculer vers le propriétaire du système de fichiers

Après avoir effectué les autres tâches de cette rubrique, saisissez l’une des commandes suivantes pour passer à cet utilisateur :

* Ubuntu : `su <username>`
* CentOS : `su - <username>`

Par exemple,

```bash
su magento_user
```
