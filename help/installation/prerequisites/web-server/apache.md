---
title: Apache
description: Pour installer et configurer le serveur web Apache pour les installations sur site d’Adobe Commerce et de Magento Open Source, procédez comme suit.
source-git-commit: 61638d373408d9a7c3c3a935eee61927acfac7a6
workflow-type: tm+mt
source-wordcount: '844'
ht-degree: 0%

---


# Apache

Adobe Commerce prend en charge Apache 2.4.x.

## Instructions requises pour Apache

1. Définir `AllowEncodedSlashes` dans la configuration du serveur (globalement) ou dans les configurations de l’hôte virtuel afin d’éviter le décodage des barres obliques codées susceptibles de poser des problèmes pour les URL. Par exemple, lors de la récupération de produits avec une barre oblique dans le SKU via l’API, vous ne souhaitez pas qu’ils soient convertis. Le bloc d’exemple n’est pas terminé et d’autres directives sont requises.

   ```conf
   <VirtualHost *:443>
     # Allow encoded slashes
     AllowEncodedSlashes NoDecode
   </VirtualHost>
   ```

## Apache réécrit et htaccess

Cette rubrique explique comment activer les réécritures Apache 2.4 et comment spécifier un paramètre pour le [fichier de configuration distribué, `.htaccess`](https://httpd.apache.org/docs/current/howto/htaccess.html).

Réécritures du serveur d’utilisation d’Adobe Commerce et de Magento Open Source et `.htaccess` pour fournir des instructions au niveau du répertoire pour Apache. Les instructions suivantes sont également incluses dans toutes les autres sections de cette rubrique.

Utilisez cette section pour activer les réécritures Apache 2.4 et spécifiez un paramètre pour le [fichier de configuration distribué, `.htaccess`](https://httpd.apache.org/docs/current/howto/htaccess.html)

Réécritures du serveur d’utilisation d’Adobe Commerce et de Magento Open Source et `.htaccess` pour fournir des instructions au niveau du répertoire pour Apache.

>[!NOTE]
>
>Si ces paramètres ne sont pas activés, aucun style ne s’affiche sur votre storefront ou votre administrateur.

1. Activez le module de réécriture Apache :

   ```bash
   a2enmod rewrite
   ```

1. Pour permettre à l’application d’utiliser la variable distribuée `.htaccess` fichier de configuration, reportez-vous aux instructions de la section [Documentation Apache 2.4](https://httpd.apache.org/docs/current/mod/mod_rewrite.html).

   >[!TIP]
   >
   >Dans Apache 2.4, le fichier de configuration de site par défaut du serveur est `/etc/apache2/sites-available/000-default.conf`.

   Par exemple, vous pouvez ajouter les éléments suivants à la fin de la `000-default.conf`:

   ```terminal
   <Directory "/var/www/html">
       AllowOverride All
   </Directory>
   ```

   >[!NOTE]
   >
   >Il peut arriver que des paramètres supplémentaires soient nécessaires. Pour plus d’informations, voir [Documentation Apache 2.4](https://httpd.apache.org/docs/2.4/mod/mod_access_compat.html#order).

1. Si vous avez modifié les paramètres Apache, redémarrez Apache :

   ```bash
   service apache2 restart
   ```

   >[!NOTE]
   >
   >- Si vous avez effectué une mise à niveau à partir d’une version antérieure d’Apache, recherchez d’abord `<Directory "/var/www/html">` ou `<Directory "/var/www">` in `000-default.conf`.
   >- Vous devez modifier la valeur de `AllowOverride` dans la directive correspondant au répertoire dans lequel vous prévoyez d’installer le logiciel Adobe Commerce ou Magento Open Source. Par exemple, pour installer dans le répertoire docroot du serveur web, modifiez la directive dans `<Directory /var/www>`.


>[!NOTE]
>
>Si ces paramètres ne sont pas activés, les styles ne s’affichent généralement pas sur le storefront ni sur l’administrateur.

## Modules Apache requis

Adobe Commerce et Magento Open Source nécessitent que les modules Apache suivants soient installés :

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

```terminal
Server version: Apache/2.4.04 (Ubuntu)
Server built: Jul 22 2020 14:35:32
```

- Si Apache est *not* installé, voir :
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

   ```terminal
   Server version: Apache/2.4.18 (Ubuntu)
   Server built: 2020-04-15T18:00:57
   ```

1. Activer [réécrit et `.htaccess`](#apache-rewrites-and-htaccess).

### Mise à niveau d’Apache sur Ubuntu

Pour effectuer la mise à niveau vers Apache 2.4 :

1. Ajoutez la variable `ppa:ondrej` qui contient Apache 2.4 :

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

   ```terminal
   Server version: Apache/2.4.10 (Ubuntu)
   Server built: Jul 22 2020 22:46:25
   ```

1. Activer [réécrit et `.htaccess`](#apache-rewrites-and-htaccess).

## Installation d’Apache sur CentOS

Adobe Commerce et Magento Open Source nécessitent des réécritures de serveur d’utilisation Apache. Vous devez également spécifier le type de directives qui peut être utilisé dans `.htaccess`, que l’application utilise pour spécifier les règles de réécriture.

L&#39;installation et la configuration d&#39;Apache sont essentiellement un processus en trois étapes : installez le logiciel, activez les réécritures et spécifiez `.htaccess` directives.

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

   ```terminal
   Server version: Apache/2.4.40 (Unix)
   Server built: Oct 16 2020 14:48:21
   ```

1. Passez à la section suivante.

   >[!NOTE]
   >
   >Même si Apache 2.4 est fourni par défaut avec CentOS, consultez la section suivante pour le configurer.

### Activation des réécritures et des accès .html pour CentOS

1. Ouvrir `/etc/httpd/conf/httpd.conf` fichier à modifier :

   ```bash
   vim /etc/httpd/conf/httpd.conf`
   ```

1. Localisez le bloc qui commence par :

   ```conf
   <Directory "/var/www/html">
   ```

1. Modifier la valeur de `AllowOverride` to `All`.

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
   >Les valeurs précédentes pour `Order` peut ne pas fonctionner dans tous les cas. Pour plus d’informations, voir la documentation Apache ([2,4](https://httpd.apache.org/docs/2.4/mod/mod_authz_host.html#order)).

1. Enregistrez le fichier et quittez l’éditeur de texte.

1. Pour appliquer les paramètres Apache, redémarrez Apache.

   ```bash
   service apache2 restart
   ```

>[!NOTE]
>
>Si ces paramètres ne sont pas activés, aucun style ne s’affiche sur votre storefront ou votre administrateur.

### Activer les réécritures et .htaccess pour Ubuntu

1. Ouvrir `/etc/apache2/sites-available/default` fichier à modifier :

   ```bash
   vim /etc/apache2/sites-available/default
   ```

1. Localisez le bloc qui commence par :

   `<Directory "/var/www/html">`

1. Modifier la valeur de `AllowOverride` to `All`.

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

1. Configuration d’Apache pour utiliser la méthode `mod_rewrite` module :

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

Pour permettre aux visiteurs de votre site Web d’accéder à votre site, utilisez l’une des méthodes suivantes : [Directives requises](https://httpd.apache.org/docs/2.4/howto/access.html).

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
>Les valeurs précédentes pour `Order` peut ne pas fonctionner dans tous les cas. Pour plus d’informations, voir [Documentation Apache](https://httpd.apache.org/docs/2.4/mod/mod_access_compat.html#order).
