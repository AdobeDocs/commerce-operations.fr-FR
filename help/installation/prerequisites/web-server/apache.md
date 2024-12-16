---
title: Apache
description: Pour installer et configurer le serveur web Apache pour les installations sur site d’Adobe Commerce, procédez comme suit.
exl-id: a9a394c9-389f-42ef-9029-dd22c979cfb8
source-git-commit: f8c5d714a4e96d0508f745d1b7617696c8cc94a7
workflow-type: tm+mt
source-wordcount: '759'
ht-degree: 0%

---

# Apache

Adobe Commerce prend en charge Apache 2.4.x.

## Directives requises Apache

1. Définissez `AllowEncodedSlashes` dans la configuration du serveur (globalement) ou dans les configurations de l’hôte virtuel pour éviter de décoder les barres obliques codées qui peuvent entraîner des problèmes pour les URL. Par exemple, lors de la récupération de produits avec une barre oblique dans le SKU via l’API, vous ne souhaitez pas que cela soit converti. L’exemple de bloc n’est pas complet et d’autres directives sont requises.

   ```conf
   <VirtualHost *:443>
     # Allow encoded slashes
     AllowEncodedSlashes NoDecode
   </VirtualHost>
   ```

## Apache réécrit et htaccess

Cette rubrique explique comment activer les réécritures Apache 2.4 et spécifier un paramètre pour le `.htaccess`](https://github.com/magento/magento2/blob/2.4-develop/.htaccess.sample) [fichier de configuration distribué).

Adobe Commerce utilise des réécritures et des `.htaccess` de serveur pour fournir des instructions au niveau du répertoire pour Apache. Les instructions suivantes sont également incluses dans toutes les autres sections de cette rubrique.

Utilisez cette section pour activer les réécritures Apache 2.4 et spécifier un paramètre pour le [fichier de configuration distribué, `.htaccess`](https://httpd.apache.org/docs/current/howto/htaccess.html)

Adobe Commerce utilise des réécritures et des `.htaccess` de serveur pour fournir des instructions au niveau du répertoire pour Apache.

>[!NOTE]
>
>Si ces paramètres ne sont pas activés, aucun style ne s’affiche généralement sur votre storefront ou votre administrateur.

1. Activez le module de réécriture Apache :

   ```bash
   a2enmod rewrite
   ```

1. Pour permettre à l’application d’utiliser le fichier de configuration de `.htaccess` distribué, consultez les instructions de la documentation d’[Apache 2.4](https://httpd.apache.org/docs/current/mod/mod_rewrite.html).

   >[!TIP]
   >
   >Dans Apache 2.4, le fichier de configuration de site par défaut du serveur est `/etc/apache2/sites-available/000-default.conf`.

   Par exemple, vous pouvez ajouter ce qui suit à la fin de `000-default.conf` :

   ```
   <Directory "/var/www/html">
       AllowOverride All
   </Directory>
   ```

   >[!NOTE]
   >
   >Parfois, des paramètres supplémentaires peuvent être nécessaires. Pour plus d’informations, consultez la [documentation d’Apache 2.4](https://httpd.apache.org/docs/2.4/mod/mod_access_compat.html#order).

1. Si vous avez modifié les paramètres Apache, redémarrez Apache :

   ```bash
   service apache2 restart
   ```

   >[!NOTE]
   >
   >- Si vous avez effectué une mise à niveau à partir d’une version précédente d’Apache, recherchez d’abord `<Directory "/var/www/html">` ou `<Directory "/var/www">` dans `000-default.conf`.
   >- Vous devez modifier la valeur de `AllowOverride` dans la directive du répertoire dans lequel vous comptez installer le logiciel Adobe Commerce. Par exemple, pour effectuer une installation dans le serveur web docroot, modifiez la directive dans `<Directory /var/www>`.

>[!NOTE]
>
>Si ces paramètres ne sont pas activés, les styles ne s’affichent généralement pas sur le storefront ou l’administrateur.

## Modules Apache requis

Adobe Commerce nécessite l’installation des modules Apache suivants :

- [mod_deflate.c](https://httpd.apache.org/docs/2.4/mod/mod_deflate.html)
- [mod_expires.c](https://httpd.apache.org/docs/2.4/mod/mod_expires.html)
- [mod_headers.c](https://httpd.apache.org/docs/2.4/mod/mod_headers.html)
- [mod_rewrite.c](https://httpd.apache.org/docs/2.4/mod/mod_rewrite.html)
- [mod_security.c](https://modsecurity.org)
- [mod_ssl.c](https://httpd.apache.org/docs/2.4/mod/mod_ssl.html)

## Vérification de la version Apache

Pour vérifier la version d’Apache en cours d’exécution, saisissez :

```bash
apache2 -v
```

Le résultat s’affiche comme suit :

```
Server version: Apache/2.4.04 (Ubuntu)
Server built: Jul 22 2020 14:35:32
```

- Si Apache n’est *pas* installé, voir :
   - [Installation ou mise à niveau d’Apache sur Ubuntu](#installing-apache-on-ubuntu)
   - [Installation d’Apache sous CentOS](#installing-apache-on-centos)

## Installation ou mise à niveau d’Apache sur Ubuntu

Les sections suivantes expliquent comment installer ou mettre à niveau Apache :

- Installation d’Apache
- Effectuez la mise à niveau vers Apache 2.4 sur Ubuntu pour utiliser PHP 7.4.

### Installation d’Apache sur Ubuntu

Pour installer la version par défaut d’Apache :

1. Installation d’Apache

   ```bash
   apt-get -y install apache2
   ```

1. Vérifiez l’installation.

   ```bash
   apache2 -v
   ```

   Le résultat s’affiche comme suit :

   ```
   Server version: Apache/2.4.18 (Ubuntu)
   Server built: 2020-04-15T18:00:57
   ```

1. Activez les [réécritures et `.htaccess`](#apache-rewrites-and-htaccess)).

### Mise à niveau d’Apache sur Ubuntu

Pour effectuer la mise à niveau vers Apache 2.4 :

1. Ajoutez le référentiel `ppa:ondrej`, qui contient Apache 2.4 :

   ```bash
   apt-get -y update
   ```

   ```bash
   apt-add-repository ppa:ondrej/apache2
   ```

   ```bash
   apt-get -y update
   ```

1. Installez Apache 2.4 :

   ```bash
   apt-get install -y apache2
   ```

   >[!NOTE]
   >
   >Si la commande « apt-get install » échoue en raison de dépendances non satisfaites, consultez une ressource telle que [https://askubuntu.com/](https://askubuntu.com/questions/140246/how-do-i-resolve-unmet-dependencies-after-adding-a-ppa).

1. Vérifiez l’installation.

   ```bash
   apache2 -v
   ```

   Des messages similaires à ceux-ci doivent s’afficher :

   ```
   Server version: Apache/2.4.10 (Ubuntu)
   Server built: Jul 22 2020 22:46:25
   ```

1. Activez les [réécritures et `.htaccess`](#apache-rewrites-and-htaccess)).

## Installation d’Apache sous CentOS

Adobe Commerce nécessite des réécritures du serveur Apache. Vous devez également spécifier le type de directives pouvant être utilisées dans `.htaccess`, que l’application utilise pour spécifier des règles de réécriture.

L’installation et la configuration d’Apache sont essentiellement un processus en trois étapes : installation du logiciel, activation des réécritures et spécification des directives `.htaccess`.

### Installation d’Apache

1. Installez Apache 2.4 si ce n’est pas déjà fait.

   ```bash
   yum -y install httpd
   ```

1. Vérifiez l’installation :

   ```bash
   httpd -v
   ```

   Des messages similaires au suivant s’affichent pour confirmer que l’installation a réussi :

   ```
   Server version: Apache/2.4.40 (Unix)
   Server built: Oct 16 2020 14:48:21
   ```

1. Passez à la section suivante.

   >[!NOTE]
   >
   >Même si Apache 2.4 est fourni par défaut avec CentOS, consultez la section suivante pour le configurer.

### Activer les réécritures et l’accès .html pour CentOS

1. Ouvrez `/etc/httpd/conf/httpd.conf` fichier pour le modifier :

   ```bash
   vim /etc/httpd/conf/httpd.conf`
   ```

1. Localisez le bloc commençant par :

   ```conf
   <Directory "/var/www/html">
   ```

1. Remplacez la valeur de `AllowOverride` par `All`.

   Par exemple,

   ```conf
   <Directory "/var/www/">
     Options Indexes FollowSymLinks MultiViews
     AllowOverride All
     Order allow,deny
     Allow from all
   </Directory>
   ```

   >[!NOTE]
   >
   >Les valeurs précédentes pour `Order` peuvent ne pas fonctionner dans tous les cas. Pour plus d’informations, consultez la documentation Apache ([2.4](https://httpd.apache.org/docs/2.4/mod/mod_authz_host.html#order)).

1. Enregistrez le fichier et quittez l’éditeur de texte.

1. Pour appliquer les paramètres Apache, redémarrez Apache.

   ```bash
   service apache2 restart
   ```

>[!NOTE]
>
>Si ces paramètres ne sont pas activés, aucun style ne s’affiche généralement sur votre storefront ou votre administrateur.

### Activer les réécritures et .htaccess pour Ubuntu

1. Ouvrez `/etc/apache2/sites-available/default` fichier pour le modifier :

   ```bash
   vim /etc/apache2/sites-available/default
   ```

1. Localisez le bloc commençant par :

   `<Directory "/var/www/html">`

1. Remplacez la valeur de `AllowOverride` par `All`.

   Par exemple :

   ```conf
   <Directory "/var/www/html">
     Options Indexes FollowSymLinks MultiViews
     AllowOverride All
     Order allow,deny
     Allow from all
   </Directory>
   ```

1. Enregistrez le fichier et quittez l’éditeur de texte.

1. Configurez Apache pour utiliser le module `mod_rewrite` :

   ```bash
   cd /etc/apache2/mods-enabled
   ```

   ```bash
   ln -s ../mods-available/rewrite.load
   ```

1. Redémarrez Apache pour appliquer les modifications :

   ```bash
   service apache2 restart
   ```

## Résolution des erreurs 403 (Interdit)

Si vous rencontrez des erreurs 403 Interdit lors de l’accès au site, vous pouvez mettre à jour votre configuration Apache ou votre configuration d’hôte virtuel pour permettre aux visiteurs et visiteuses d’accéder au site :

### Résolution d’erreurs 403 Interdit pour Apache 2.4

Pour permettre aux visiteurs et visiteuses du site Web d’accéder à votre site, utilisez l’une des [Directives requises](https://httpd.apache.org/docs/2.4/howto/access.html).

Par exemple :

```conf
<Directory "/var/www/">
  Options Indexes FollowSymLinks MultiViews
  AllowOverride All
  Order allow,deny
  Require all granted
</Directory>
```

>[!NOTE]
>
>Les valeurs précédentes pour `Order` peuvent ne pas fonctionner dans tous les cas. Pour plus d’informations, consultez la [documentation Apache](https://httpd.apache.org/docs/2.4/mod/mod_access_compat.html#order).
