---
title: Configuration de la propriété et des autorisations de fichier
description: Pour configurer les autorisations du système de fichiers pour les installations sur site d’Adobe Commerce, procédez comme suit.
exl-id: 2410ee4f-978c-4b71-b3f6-0c042f9f4dc4
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '981'
ht-degree: 0%

---

# Configuration de la propriété et des autorisations de fichier

Cette rubrique explique comment définir des autorisations de lecture-écriture pour le groupe de serveurs web avant d’installer Adobe Commerce. Cela est nécessaire afin que la ligne de commande puisse écrire des fichiers dans le système de fichiers.

La procédure que vous utilisez est différente, selon que vous utilisez l&#39;[hébergement partagé](#set-permissions-for-one-user-on-shared-hosting) et que vous utilisez un utilisateur ou un [serveur privé](#set-ownership-and-permissions-for-two-users) et que vous avez deux utilisateurs.

## Définition des autorisations pour un utilisateur sur l’hébergement partagé

Cette section explique comment définir les autorisations de pré-installation si vous vous connectez au serveur d’applications en tant qu’utilisateur exécutant également le serveur web. Ce type de configuration est courant dans les environnements d’hébergement partagés.

Pour définir les autorisations avant d’installer l’application :

1. Connectez-vous à votre serveur d’applications.
1. Utilisez une application de gestionnaire de fichiers fournie par votre fournisseur d’hébergement partagé pour vérifier que les autorisations d’écriture sont définies sur les répertoires suivants :

   * `vendor` (installation du compositeur ou de l’archive compressée)
   * `app/etc`
   * `pub/static`
   * `var`
   * `generated`
   * Toute autre ressource statique

1. Si vous disposez d’un accès en ligne de commande, saisissez les commandes suivantes dans l’ordre indiqué :

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

   Si vous le souhaitez, saisissez toutes les commandes sur une seule ligne, en supposant que l’application soit installée dans `/var/www/html/magento2` :

   ```bash
   cd /var/www/html/magento2 && find var generated vendor pub/static pub/media app/etc -type f -exec chmod u+w {} + && find var generated vendor pub/static pub/media app/etc -type d -exec chmod u+w {} + && chmod u+x bin/magento
   ```

1. Si vous ne l’avez pas déjà fait, récupérez l’application de l’une des manières suivantes :

   * [Métaphorage du compositeur](../../composer.md)
   * [Cloner le référentiel (développeurs contributeurs uniquement)](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/)

1. Après avoir défini la propriété et les autorisations du système de fichiers, [installez l’application](../../advanced.md)

>[!NOTE]
>
>Pour restreindre davantage les autorisations après l&#39;installation de l&#39;application, vous pouvez [configurer un umask](../../next-steps/set-umask.md).

## Définir la propriété et les autorisations pour deux utilisateurs

Cette section explique comment définir la propriété et les autorisations pour votre propre serveur ou une configuration d’hébergement privé. Dans ce type de configuration, vous *ne pouvez pas* vous connecter en tant qu’utilisateur du serveur web ou passer à . En règle générale, vous vous connectez en tant qu’utilisateur unique et exécutez le serveur web en tant qu’utilisateur différent.

Pour définir la propriété et les autorisations d’un système à deux utilisateurs :

Effectuez les tâches suivantes dans l’ordre indiqué :

* [À propos du groupe partagé](#about-the-shared-group)
* [Créez le propriétaire du système de fichiers et attribuez à l’utilisateur un mot de passe sécurisé.](#create-the-file-system-owner-and-give-the-user-a-strong-password)
* [Recherche du groupe d’utilisateurs du serveur web](#find-the-web-server-user-group)
* [Placez le propriétaire du système de fichiers dans le groupe de serveurs web](#put-the-file-system-owner-in-the-web-server-group)
* [Obtention du logiciel](#get-the-software)
* [Définir la propriété et les autorisations pour le groupe partagé](#set-ownership-and-permissions-for-the-shared-group)

### À propos du groupe partagé

Pour permettre au serveur web d’écrire des fichiers et des répertoires dans le système de fichiers, mais aussi de gérer la *propriété* par le propriétaire du système de fichiers, les deux utilisateurs doivent appartenir au même groupe. Cela est nécessaire afin que les deux utilisateurs puissent partager l’accès aux fichiers (y compris les fichiers créés à l’aide de l’administrateur ou d’autres utilitaires web).

Cette section explique comment créer un propriétaire de système de fichiers et placer cet utilisateur dans le groupe du serveur web. Si vous le souhaitez, vous pouvez utiliser un compte utilisateur existant ; nous vous recommandons de disposer d’un mot de passe sécurisé.

>[!NOTE]
>
>Passez à [Trouvez le groupe d’utilisateurs du serveur web](#find-the-web-server-user-group) si vous envisagez d’utiliser un compte d’utilisateur existant.

### Créez le propriétaire du système de fichiers et attribuez à l’utilisateur un mot de passe sécurisé.

Cette section explique comment créer le propriétaire du système de fichiers. (Le propriétaire du système de fichiers est un autre terme pour l’ *utilisateur de ligne de commande*.)

Pour créer un utilisateur sous CentOS ou Ubuntu, saisissez la commande suivante en tant qu’utilisateur disposant des privilèges `root` :

```bash
adduser <username>
```

Pour attribuer un mot de passe à l’utilisateur, saisissez la commande suivante en tant qu’utilisateur disposant des privilèges `root` :

```bash
passwd <username>
```

Suivez les invites de votre écran pour créer un mot de passe pour l’utilisateur.

>[!WARNING]
>
>Si vous ne disposez pas des privilèges `root` sur votre serveur d’applications, vous pouvez utiliser un autre compte d’utilisateur local. Assurez-vous que l&#39;utilisateur dispose d&#39;un mot de passe fort et continuez avec [Placez le propriétaire du système de fichiers dans le groupe de serveurs web](#step-3-put-the-file-system-owner-in-the-web-servers-group).

Par exemple, pour créer un utilisateur nommé `magento_user` et donner un mot de passe à l’utilisateur, saisissez :

```bash
sudo adduser magento_user
```

```bash
sudo passwd magento_user
```

>[!WARNING]
>
>Comme la création de cet utilisateur a pour but de fournir une sécurité supplémentaire, veillez à créer un [mot de passe fort](https://en.wikipedia.org/wiki/Password_strength).

### Recherche du groupe d’utilisateurs du serveur web

Pour trouver le groupe d’utilisateurs du serveur web :

* CentOS :

  ```bash
  grep -E -i '^user|^group' /etc/httpd/conf/httpd.conf
  ```

  ou

  ```bash
  grep -Ei '^user|^group' /etc/httpd/conf/httpd.conf
  ```

En règle générale, le nom de l’utilisateur et le nom du groupe sont `apache`.

* Ubuntu : `ps aux | grep apache` pour trouver l’utilisateur Apache, puis `groups <apache user>` pour trouver le groupe.

En règle générale, le nom d’utilisateur et le nom du groupe sont `www-data`.

### Placez le propriétaire du système de fichiers dans le groupe de serveurs web

Pour placer le propriétaire du système de fichiers dans le groupe principal du serveur web (en supposant que le nom type du groupe Apache soit CentOS et Ubuntu), saisissez la commande suivante en tant qu’utilisateur disposant des privilèges `root` :

* CentOS : `usermod -a -G apache <username>`
* Ubuntu : `usermod -a -G www-data <username>`

>[!NOTE]
>
>Les options `-a -G` sont importantes car elles ajoutent `apache` ou `www-data` en tant que groupe *secondaire* au compte utilisateur, ce qui conserve le groupe *principal* de l’utilisateur. L&#39;ajout d&#39;un groupe secondaire à un compte utilisateur permet de [restreindre la propriété et les autorisations des fichiers](#set-ownership-and-permissions-for-two-users) pour s&#39;assurer que les membres d&#39;un groupe partagé n&#39;ont accès qu&#39;à certains fichiers.

Par exemple, pour ajouter l&#39;utilisateur `magento_user` au groupe principal `apache` sur CentOS :

```bash
sudo usermod -a -G apache magento_user
```

Pour confirmer que votre utilisateur fait partie du groupe de serveurs web, saisissez la commande suivante :

```bash
groups magento_user
```

L’exemple de résultat suivant montre les groupes primaire (`magento`) et secondaire (`apache`) de l’utilisateur.

```bash
magento_user : magento_user apache
```

>[!NOTE]
>
>En règle générale, le nom d’utilisateur et le nom du groupe principal sont identiques.

Pour terminer la tâche, redémarrez le serveur web :

* Ubuntu : `service apache2 restart`
* CentOS : `service httpd restart`

### Obtention du logiciel

Si vous ne l’avez pas déjà fait, récupérez le logiciel de l’une des manières suivantes :

* [Métaphorage du compositeur](../../composer.md)
* [Cloner le référentiel (développeurs contributeurs uniquement)](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/)

### Définir la propriété et les autorisations pour le groupe partagé

Pour définir la propriété et les autorisations avant d’installer l’application :

1. Connectez-vous à votre serveur d’applications en tant que propriétaire du système de fichiers ou basculez vers .
1. Saisissez les commandes suivantes dans l’ordre indiqué :

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

Si vous le souhaitez, saisissez toutes les commandes sur une seule ligne, en supposant que l’application soit installée dans `/var/www/html/magento2` et que le nom du groupe de serveurs web soit `apache` :

```bash
cd /var/www/html/magento2 && find var generated vendor pub/static pub/media app/etc -type f -exec chmod g+w {} + && find var generated vendor pub/static pub/media app/etc -type d -exec chmod g+ws {} + && chown -R :apache . && chmod u+x bin/magento
```

Dans le système de fichiers d’événements, les autorisations sont définies de manière incorrecte et ne peuvent pas être modifiées par le propriétaire du système de fichiers. Vous pouvez saisir la commande en tant qu’utilisateur disposant des privilèges `root` :

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
