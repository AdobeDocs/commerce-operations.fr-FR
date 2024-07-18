---
title: Apache
description: Pour installer et configurer le serveur web Apache pour les installations sur site d’Adobe Commerce, procédez comme suit.
exl-id: a9a394c9-389f-42ef-9029-dd22c979cfb8
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '759'
ht-degree: 0%

---

# Apache

Adobe Commerce prend en charge Apache 2.4.x.

## Instructions requises pour Apache

1. Définissez `AllowEncodedSlashes` dans la configuration du serveur (globalement) ou dans les configurations de l’hôte virtuel afin d’éviter le décodage des barres obliques codées susceptibles de poser des problèmes pour les URL. Par exemple, lors de la récupération de produits avec une barre oblique dans le SKU via l’API, vous ne souhaitez pas qu’ils soient convertis. Le bloc d’exemple n’est pas terminé et d’autres directives sont requises.

   ```conf
   <VirtualHost *:443>
     # Allow encoded slashes
     AllowEncodedSlashes NoDecode
   </VirtualHost>
   ```

## Apache réécrit et htaccess

Cette rubrique explique comment activer les réécritures Apache 2.4 et spécifier un paramètre pour le [fichier de configuration distribué, `.htaccess`](https://httpd.apache.org/docs/current/howto/htaccess.html).

Adobe Commerce utilise les réécritures de serveur et `.htaccess` pour fournir des instructions au niveau du répertoire pour Apache. Les instructions suivantes sont également incluses dans toutes les autres sections de cette rubrique.

Utilisez cette section pour activer les réécritures Apache 2.4 et spécifier un paramètre pour le [fichier de configuration distribué, `.htaccess`](https://httpd.apache.org/docs/current/howto/htaccess.html)

Adobe Commerce utilise les réécritures de serveur et `.htaccess` pour fournir des instructions au niveau du répertoire pour Apache.

>[!NOTE]
>
>Si ces paramètres ne sont pas activés, aucun style ne s’affiche sur votre storefront ou votre administrateur.

1. Activez le module de réécriture Apache :

   ```bash
   a2enmod rewrite
   ```

1. Pour permettre à l’application d’utiliser le fichier de configuration `.htaccess` distribué, consultez les instructions de la [documentation Apache 2.4](https://httpd.apache.org/docs/current/mod/mod_rewrite.html).

   >[!TIP]
   >
   >Dans Apache 2.4, le fichier de configuration de site par défaut du serveur est `/etc/apache2/sites-available/000-default.conf`.

   Par exemple, vous pouvez ajouter les éléments suivants à la fin de `000-default.conf` :

   ```
   <Directory "/var/www/html">
       AllowOverride All
   </Directory>
   ```

   >[!NOTE]
   >
   >Il peut arriver que des paramètres supplémentaires soient nécessaires. Pour plus d’informations, voir la [documentation Apache 2.4](https://httpd.apache.org/docs/2.4/mod/mod_access_compat.html#order).

1. Si vous avez modifié les paramètres Apache, redémarrez Apache :

   ```bash
   service apache2 restart
   ```

   >[!NOTE]
   >
   >- Si vous avez effectué une mise à niveau à partir d’une version antérieure d’Apache, recherchez d’abord `<Directory "/var/www/html">` ou `<Directory "/var/www">` dans `000-default.conf`.
   >- Vous devez modifier la valeur de `AllowOverride` dans la directive pour le répertoire dans lequel vous prévoyez d’installer le logiciel Adobe Commerce. Par exemple, pour installer dans le docroot du serveur web, modifiez la directive dans `<Directory /var/www>`.

>[!NOTE]
>
>Si ces paramètres ne sont pas activés, les styles ne s’affichent généralement pas sur le storefront ni sur l’administrateur.

## Modules Apache requis

Adobe Commerce requiert l’installation des modules Apache suivants :

- [mod_deflate.c](https://httpd.apache.org/docs/2.4/mod/mod_deflate.html)
- [mod_expires.c](https://httpd.apache.org/docs/2.4/mod/mod_expires.html)
- [mod_headers.c](https://httpd.apache.org/docs/2.4/mod/mod_headers.html)
- [mod_rewrite.c](https://httpd.apache.org/docs/2.4/mod/mod_rewrite.html)
- [mod_security.c](https://modsecurity.org)
- [mod_ssl.c](https://httpd.apache.org/docs/2.4/mod/mod_ssl.html)

## Vérification de la version d’Apache

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
   - [Installation d’Apache sur CentOS](#installing-apache-on-centos)

## Installation ou mise à niveau d’Apache sur Ubuntu

Les sections suivantes expliquent comment installer ou mettre à niveau Apache :

- Installer Apache
- Effectuez une mise à niveau vers Apache 2.4 sous Ubuntu pour utiliser PHP 7.4.

### Installation d’Apache sur Ubuntu

Pour installer la version par défaut d’Apache :

1. Installer Apache

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

1. Activez [ réécritures et `.htaccess`](#apache-rewrites-and-htaccess).

### Mise à niveau d’Apache sur Ubuntu

Pour effectuer la mise à niveau vers Apache 2.4 :

1. Ajoutez le référentiel `ppa:ondrej`, qui possède Apache 2.4 :

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
   >Si la commande &quot;apt-get install&quot; échoue en raison de dépendances non satisfaites, consultez une ressource telle que [https://askubuntu.com/](https://askubuntu.com/questions/140246/how-do-i-resolve-unmet-dependencies-after-adding-a-ppa).

1. Vérifiez l’installation.

   ```bash
   apache2 -v
   ```

   Les messages similaires aux suivants doivent s’afficher :

   ```
   Server version: Apache/2.4.10 (Ubuntu)
   Server built: Jul 22 2020 22:46:25
   ```

1. Activez [ réécritures et `.htaccess`](#apache-rewrites-and-htaccess).

## Installation d’Apache sur CentOS

Adobe Commerce nécessite des réécritures du serveur Apache. Vous devez également spécifier le type de directives qui peut être utilisé dans `.htaccess`, que l’application utilise pour spécifier les règles de réécriture.

L&#39;installation et la configuration d&#39;Apache sont essentiellement un processus en trois étapes : installation du logiciel, activation des réécritures et spécification des directives `.htaccess`.

### Installation d’Apache

1. Installez Apache 2.4 si vous ne l’avez pas déjà fait.

   ```bash
   yum -y install httpd
   ```

1. Vérifiez l’installation :

   ```bash
   httpd -v
   ```

   Messages similaires à l’affichage suivant pour confirmer la réussite de l’installation :

   ```
   Server version: Apache/2.4.40 (Unix)
   Server built: Oct 16 2020 14:48:21
   ```

1. Passez à la section suivante.

   >[!NOTE]
   >
   >Même si Apache 2.4 est fourni par défaut avec CentOS, consultez la section suivante pour le configurer.

### Activation des réécritures et des accès .html pour CentOS

1. Ouvrez le fichier `/etc/httpd/conf/httpd.conf` pour le modifier :

   ```bash
   vim /etc/httpd/conf/httpd.conf`
   ```

1. Localisez le bloc qui commence par :

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
   >Les valeurs précédentes pour `Order` peuvent ne pas fonctionner dans tous les cas. Pour plus d’informations, voir la documentation Apache ([2.4](https://httpd.apache.org/docs/2.4/mod/mod_authz_host.html#order)).

1. Enregistrez le fichier et quittez l’éditeur de texte.

1. Pour appliquer les paramètres Apache, redémarrez Apache.

   ```bash
   service apache2 restart
   ```

>[!NOTE]
>
>Si ces paramètres ne sont pas activés, aucun style ne s’affiche sur votre storefront ou votre administrateur.

### Activer les réécritures et .htaccess pour Ubuntu

1. Ouvrez le fichier `/etc/apache2/sites-available/default` pour le modifier :

   ```bash
   vim /etc/apache2/sites-available/default
   ```

1. Localisez le bloc qui commence par :

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

Si vous rencontrez des erreurs 403 interdites lors de la tentative d’accès au site, vous pouvez mettre à jour votre configuration Apache ou votre configuration d’hôte virtuel pour permettre aux visiteurs de se rendre sur le site :

### Résolution des erreurs 403 interdites pour Apache 2.4

Pour permettre aux visiteurs de votre site web d’accéder à votre site, utilisez l’une des [directives requises](https://httpd.apache.org/docs/2.4/howto/access.html).

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
>Les valeurs précédentes pour `Order` peuvent ne pas fonctionner dans tous les cas. Pour plus d’informations, voir la [documentation Apache](https://httpd.apache.org/docs/2.4/mod/mod_access_compat.html#order).
