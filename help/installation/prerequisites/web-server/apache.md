---
title: Installation d’Apache pour les déploiements On-Premise
description: Découvrez comment installer et configurer Apache pour les déploiements d’Adobe Commerce sur site. Activez les modules requis, les réécritures et les paramètres &grave;.htaccess&grave;.
feature: Install, Configuration
badgePaas: label="On-premise" type="Informative" url="https://experienceleague.adobe.com/fr/docs/commerce/user-guides/product-solutions" tooltip="S’applique uniquement aux projets sur site Adobe Commerce."
exl-id: a9a394c9-389f-42ef-9029-dd22c979cfb8
source-git-commit: 352a71cb88ff38c0920201f49f1d7b889509fd61
workflow-type: tm+mt
source-wordcount: '1015'
ht-degree: 0%

---

# Installation d’Apache pour les déploiements sur site {#apache}

Ce guide vous guide tout au long de l’installation d’Apache pour les déploiements sur site d’Adobe Commerce et de la configuration des paramètres Apache requis par Commerce. Il comprend des exigences Apache partagées et des procédures spécifiques au système d’exploitation pour Ubuntu et CentOS. Adobe recommande de suivre les instructions de configuration fournies dans ce guide afin de préserver les fonctionnalités et la sécurité de l’application Commerce.

Adobe prend en charge les versions d’Apache répertoriées dans la [configuration requise](../../system-requirements.md) pour votre version d’Adobe Commerce. Les versions prises en charge varient selon les versions. Apache nécessite également une configuration PHP prise en charge. Pour les exigences PHP associées, voir [Paramètres PHP](../php-settings.md).

Commencez par la section correspondant à votre environnement :

- Si Apache est déjà installé, commencez par [vérifier les exigences d’Apache](#review-apache-requirements).
- Si vous devez installer ou mettre à niveau Apache sur Ubuntu, accédez à [&#x200B; Installer ou mettre à niveau Apache sur Ubuntu &#x200B;](#installing-or-upgrading-apache-on-ubuntu).
- Si vous devez installer Apache sous CentOS, accédez à [Installer Apache sous CentOS](#installing-apache-on-centos).

## Vérifier les exigences d’Apache

Effectuez ces exigences sur tout serveur Apache hébergeant Adobe Commerce.

### Configurer les directives requises

Définissez `AllowEncodedSlashes` dans la configuration du serveur (globalement) ou dans les configurations de l’hôte virtuel pour éviter de décoder les barres obliques codées qui peuvent entraîner des problèmes pour les URL. Par exemple, lors de la récupération de produits avec une barre oblique dans le SKU via l’API, vous ne souhaitez pas que la barre oblique soit convertie. L’exemple de bloc suivant est incomplet et d’autres directives sont requises.

```conf
<VirtualHost *:443>
  # Allow encoded slashes
  AllowEncodedSlashes NoDecode
</VirtualHost>
```

### Configuration des réécritures et de .htaccess {#apache-rewrites-and-htaccess}

Utilisez cette section pour activer les réécritures Apache et configurer le [fichier `.htaccess` distribué](https://httpd.apache.org/docs/current/howto/htaccess.html). Adobe Commerce utilise des réécritures et des `.htaccess` de serveur pour fournir des instructions au niveau du répertoire pour Apache.

>[!IMPORTANT]
>
>Si ces paramètres ne sont pas activés, aucun style ne s’affiche généralement sur votre storefront ou votre administrateur. Cela peut également empêcher Apache d’appliquer les protections de sécurité Adobe Commerce définies dans `.htaccess`.

1. Activez le module de réécriture Apache :

   ```bash
   a2enmod rewrite
   ```

1. Autorisez l’application à utiliser le fichier de configuration de `.htaccess` distribué.

   1. Sur Ubuntu, modifiez `/etc/apache2/sites-available/000-default.conf`. Pour d’autres dispositions Apache ou si des paramètres supplémentaires sont requis, consultez la [documentation Apache](https://httpd.apache.org/docs/current/mod/mod_rewrite.html) et la [documentation sur le contrôle d’accès Apache](https://httpd.apache.org/docs/2.4/mod/mod_access_compat.html#order).

   1. Ajoutez ou mettez à jour la directive `AllowOverride` pour le répertoire dans lequel vous envisagez d’installer Adobe Commerce.

   Par exemple, si vous installez Adobe Commerce dans le `docroot` par défaut, ajoutez le bloc suivant à `000-default.conf` :

   ```conf
   <Directory "/var/www/html">
     AllowOverride All
   </Directory>
   ```

   >[!NOTE]
   >
   >Si vous avez effectué une mise à niveau à partir d’une version précédente d’Apache, recherchez d’abord un bloc `<Directory "/var/www/html">` ou `<Directory "/var/www">` existant dans `000-default.conf`. Si vous installez Adobe Commerce dans un autre `docroot`, mettez à jour le bloc de `<Directory>` correspondant à ce chemin d’accès.

1. Redémarrez Apache pour appliquer vos modifications :

   ```bash
   service apache2 restart
   ```

### Installation des modules requis

Adobe Commerce nécessite l’installation des modules Apache suivants :

- [mod_deflate.c](https://httpd.apache.org/docs/2.4/mod/mod_deflate.html)
- [mod_expires.c](https://httpd.apache.org/docs/2.4/mod/mod_expires.html)
- [mod_headers.c](https://httpd.apache.org/docs/2.4/mod/mod_headers.html)
- [mod_rewrite.c](https://httpd.apache.org/docs/2.4/mod/mod_rewrite.html)
- [mod_security.c](https://modsecurity.org)
- [mod_ssl.c](https://httpd.apache.org/docs/2.4/mod/mod_ssl.html)

## Vérifier qu’Apache est installé

Pour vérifier qu’Apache est installé et afficher la version actuelle, saisissez :

```bash
apache2 -v
```

Le résultat affiche des informations similaires à ce qui suit :

```text
Server version: Apache/<installed-version>
Server built: <build-date>
```

- Si Apache n’est *pas* installé, voir :
   - [Installer ou mettre à niveau Apache sur Ubuntu](#installing-or-upgrading-apache-on-ubuntu)
   - [Installation d’Apache sous CentOS](#installing-apache-on-centos)

## Installer ou mettre à niveau Apache sur Ubuntu {#installing-or-upgrading-apache-on-ubuntu}

L’installation et la configuration d’Apache sur Ubuntu est un processus en trois étapes :

1. Installez le logiciel.
1. Activez les réécritures.
1. Spécifiez les directives `.htaccess`.

Lorsque vous configurez les réécritures du serveur Apache, vous devez spécifier le type de directives pouvant être utilisées dans `.htaccess`, que l’application utilise pour spécifier les règles de réécriture et les protections de sécurité.

### Installer Apache sur Ubuntu

1. Installez Apache si vous ne l’avez pas déjà fait :

   ```bash
   apt-get -y install apache2
   ```

1. Vérifiez l’installation :

   ```bash
   apache2 -v
   ```

   Des messages similaires au suivant s’affichent pour confirmer que l’installation a réussi :

   ```text
   Server version: Apache/<installed-version>
   Server built: <build-date>
   ```

1. Passez à la section suivante.

   >[!NOTE]
   >
   >Même si Apache est fourni par défaut avec Ubuntu, consultez la section suivante pour le configurer.

### Mettre à niveau Apache sur Ubuntu

Si Apache est déjà installé et que vous utilisez une version antérieure à `2.4`, effectuez une mise à niveau vers Apache `2.4` ou vers la dernière version prise en charge par la version d’Adobe Commerce que vous avez déployée. Voir [&#x200B; Configuration requise &#x200B;](../../system-requirements.md).

1. Mettre à jour les informations sur le package :

   ```bash
   apt-get -y update
   ```

1. Ajoutez un référentiel qui fournit une version Apache prise en charge pour votre environnement, si nécessaire.

1. Installez ou mettez à niveau Apache :

   ```bash
   apt-get install -y apache2
   ```

   >[!NOTE]
   >
   >Si la commande `apt-get install` échoue en raison de dépendances non satisfaites, consultez la documentation du package de votre système d’exploitation ou les ressources d’assistance pour la distribution.

1. Vérifiez l’installation :

   ```bash
   apache2 -v
   ```

1. Vérifiez que la version installée correspond à la version prise en charge pour votre version d’Adobe Commerce dans [configuration requise](../../system-requirements.md).

1. Activez [réécritures et `.htaccess` pour Ubuntu](#enable-rewrites-and-htaccess-for-ubuntu).

### Activer les réécritures et .htaccess pour Ubuntu

1. Ouvrez le fichier `/etc/apache2/sites-available/000-default.conf` pour le modifier :

   ```bash
   vim /etc/apache2/sites-available/000-default.conf
   ```

1. Localisez le bloc commençant par :

   ```conf
   <Directory "/var/www/html">
   ```

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

>[!IMPORTANT]
>
>Si ces paramètres ne sont pas activés, aucun style ne s’affiche généralement sur votre storefront ou votre administrateur. Cela peut également empêcher Apache d’appliquer les protections de sécurité Adobe Commerce définies dans `.htaccess`.

## Installation d’Apache sous CentOS {#installing-apache-on-centos}

L’installation et la configuration d’Apache sur CentOS est un processus en trois étapes :

1. Installation du logiciel
2. Activer les réécritures
3. Spécifiez les directives `.htaccess`.

Lorsque vous configurez les réécritures du serveur Apache, vous devez spécifier le type de directives pouvant être utilisées dans `.htaccess`, que l’application utilise pour spécifier les règles de réécriture et les protections de sécurité.

### Installation d’Apache

1. Installez Apache si vous ne l’avez pas déjà fait.

   ```bash
   yum -y install httpd
   ```

1. Vérifiez l’installation :

   ```bash
   httpd -v
   ```

   Des messages similaires au suivant s’affichent pour confirmer que l’installation a réussi :

   ```text
   Server version: Apache/<installed-version>
   Server built: <build-date>
   ```

1. Passez à la section suivante.

   >[!NOTE]
   >
   >Même si Apache est fourni par défaut avec CentOS, consultez la section suivante pour le configurer.

### Activer les réécritures et l’accès .html pour CentOS

1. Ouvrez le fichier `/etc/httpd/conf/httpd.conf` pour le modifier :

   ```bash
   vim /etc/httpd/conf/httpd.conf
   ```

1. Localisez le bloc commençant par :

   ```conf
   <Directory "/var/www/html">
   ```

1. Remplacez la valeur de `AllowOverride` par `All`.

   Par exemple :

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
   >Les valeurs précédentes pour `Order` peuvent ne pas fonctionner dans tous les cas. Pour plus d’informations, consultez la [documentation Apache](https://httpd.apache.org/docs/2.4/mod/mod_authz_host.html#order).

1. Enregistrez le fichier et quittez l’éditeur de texte.

1. Pour appliquer les paramètres Apache, redémarrez Apache.

   ```bash
   systemctl restart httpd
   ```

>[!IMPORTANT]
>
>Si ces paramètres ne sont pas activés, aucun style ne s’affiche généralement sur votre storefront ou votre administrateur. Cela peut également empêcher Apache d’appliquer les protections de sécurité Adobe Commerce définies dans `.htaccess`.

## Résolution des erreurs 403 (Interdit)

Si vous rencontrez des erreurs 403 Interdit lors de l’accès au site, vous pouvez mettre à jour votre configuration Apache ou votre configuration d’hôte virtuel pour permettre aux visiteurs et visiteuses d’accéder au site :

### Résolution des erreurs 403 Interdit pour Apache

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
