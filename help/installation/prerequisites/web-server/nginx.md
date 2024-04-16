---
title: Nginx
description: Pour installer et configurer le serveur web Nginx pour les installations sur site d’Adobe Commerce, procédez comme suit.
exl-id: 041ddb9d-868e-4021-9388-1c9ea11bfd8f
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '1134'
ht-degree: 0%

---

# Nginx

Adobe Commerce prend en charge la version 1.x (ou la version [dernière version de mainline](https://nginx.org/en/linux_packages.html#mainline)). Vous devez également installer la dernière version de `php-fpm`.

Les instructions d’installation varient en fonction du système d’exploitation utilisé. Voir [PHP](../php-settings.md) pour plus d’informations.

## Ubuntu

La section suivante décrit comment installer Adobe Commerce 2.x sur Ubuntu à l’aide de nginx, PHP et MySQL.

### Installer nginx

```bash
sudo apt -y install nginx
```

Vous pouvez également [build nginx à partir de la source](https://www.armanism.com/blog/install-nginx-on-ubuntu)

Après avoir terminé les sections suivantes et installé l’application, nous utiliserons un exemple de fichier de configuration pour [configure nginx](#configure-nginx).

### Installation et configuration de php-fpm

Adobe Commerce nécessite plusieurs [Extensions PHP](../php-settings.md) pour fonctionner correctement. Outre ces extensions, vous devez également installer et configurer la variable `php-fpm` si vous utilisez nginx.

Installation et configuration `php-fpm`:

1. Installer `php-fpm` et `php-cli`:

   ```bash
   apt-get -y install php7.2-fpm php7.2-cli
   ```

   >[!NOTE]
   >
   >Cette commande installe la dernière version disponible de PHP 7.2.X. Voir [configuration requise](../../system-requirements.md) pour les versions PHP prises en charge.

1. Ouvrez le `php.ini` fichiers dans un éditeur :

   ```bash
   vim /etc/php/7.2/fpm/php.ini
   ```

   ```bash
   vim /etc/php/7.2/cli/php.ini
   ```

1. Editez les deux fichiers pour qu&#39;ils correspondent aux lignes suivantes :

   ```conf
   memory_limit = 2G
   max_execution_time = 1800
   zlib.output_compression = On
   ```

   >[!NOTE]
   >
   >Nous vous recommandons de définir la limite de mémoire sur 2 G lors du test d’Adobe Commerce. Voir [Paramètres PHP requis](../php-settings.md) pour plus d’informations.

1. Enregistrez l’éditeur, puis quittez-le.

1. Redémarrez le `php-fpm` service :

   ```bash
   systemctl restart php7.2-fpm
   ```

### Installation et configuration de MySQL

Voir [MySQL](../database/mysql.md) pour plus d’informations.

### Installation et configuration

Il existe plusieurs façons de télécharger Adobe Commerce, notamment :

* [Obtention du métaphorage du compositeur](../../composer.md)

* [Clonage du référentiel git](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/)

Cet exemple présente une installation basée sur le compositeur à l’aide de la ligne de commande.

1. Comme la variable [propriétaire du système de fichiers](../file-system/overview.md), connectez-vous à votre serveur d’applications.

1. Modifiez le répertoire docroot du serveur web ou un répertoire que vous avez configuré comme docroot d’hôte virtuel. Pour cet exemple, nous utilisons la valeur Ubuntu par défaut. `/var/www/html`.

   ```bash
   cd /var/www/html
   ```

1. Installez le compositeur globalement. Le compositeur est nécessaire pour mettre à jour les dépendances avant d’installer Adobe Commerce ou Magento Open Source :

   ```bash
   curl -sS https://getcomposer.org/installer | sudo php -- --install-dir=/usr/bin --filename=composer
   ```

1. Créez un projet de compositeur à l’aide du métapaquet Magento Open Source ou Adobe Commerce.

   **Magento Open Source**

   ```bash
   composer create-project --repository=https://repo.magento.com/ magento/project-community-edition <install-directory-name>
   ```

   **Adobe Commerce**

   ```bash
   composer create-project --repository=https://repo.magento.com/ magento/project-enterprise-edition <install-directory-name>
   ```

   Lorsque vous y êtes invité, saisissez le [clés d’authentification](../authentication-keys.md). Votre _clé publique_ est votre nom d’utilisateur ; votre _clé privée_ est votre mot de passe.

1. Définissez les autorisations de lecture-écriture pour le groupe de serveurs web avant d’installer l’application. Cela est nécessaire afin que la ligne de commande puisse écrire des fichiers dans le système de fichiers.

   ```bash
   cd /var/www/html/<magento install directory>
   ```

   ```bash
   find var generated vendor pub/static pub/media app/etc -type f -exec chmod g+w {} +
   ```

   ```bash
   find var generated vendor pub/static pub/media app/etc -type d -exec chmod g+ws {} +
   ```

   ```bash
   chown -R :www-data . # Ubuntu
   ```

   ```bash
   chmod u+x bin/magento
   ```

1. Installez à partir du [ligne de commande](../../advanced.md). Cet exemple suppose que le répertoire d’installation est nommé `magento2ee`, la variable `db-host` se trouve sur le même ordinateur (`localhost`), et que la variable `db-name`, `db-user`, et `db-password` sont tous `magento`:

   ```bash
   bin/magento setup:install \
   --base-url=http://localhost/magento2ee \
   --db-host=localhost \
   --db-name=magento \
   --db-user=magento \
   --db-password=magento \
   --backend-frontname=admin \
   --admin-firstname=admin \
   --admin-lastname=admin \
   --admin-email=admin@admin.com \
   --admin-user=admin \
   --admin-password=admin123 \
   --language=en_US \
   --currency=USD \
   --timezone=America/Chicago \
   --use-rewrites=1 \
   --search-engine=elasticsearch7 \
   --elasticsearch-host=es-host.example.com \
   --elasticsearch-port=9200
   ```

1. Passez en mode Développeur :

   ```bash
   cd /var/www/html/magento2/bin
   ```

   ```bash
   ./magento deploy:mode:set developer
   ```

### Configuration de nginx

Il est recommandé de configurer nginx à l’aide de la méthode `nginx.conf.sample` fichier de configuration fourni dans le répertoire d’installation et l’hôte virtuel nginx.

Ces instructions supposent que vous utilisez l’emplacement Ubuntu par défaut pour l’hôte virtuel nginx (par exemple, `/etc/nginx/sites-available`) et le docroot par défaut Ubuntu (par exemple, `/var/www/html`), toutefois, vous pouvez modifier ces emplacements en fonction de votre environnement.

1. Créez un hôte virtuel pour votre site :

   ```bash
   vim /etc/nginx/sites-available/magento
   ```

1. Ajoutez la configuration suivante :

   ```conf
   upstream fastcgi_backend {
     server  unix:/run/php/php7.2-fpm.sock;
   }
   
   server {
   
     listen 80;
     server_name www.magento-dev.com;
     set $MAGE_ROOT /var/www/html/magento2;
     include /var/www/html/magento2/nginx.conf.sample;
   }
   ```

   >[!NOTE]
   >
   >La variable `include` doit pointer vers l’exemple de fichier de configuration nginx dans votre répertoire d’installation.

1. Remplacer `www.magento-dev.com` par votre nom de domaine. Celui-ci doit correspondre à l’URL de base que vous avez spécifiée lors de l’installation d’Adobe Commerce ou de Magento Open Source.

1. Enregistrez l’éditeur, puis quittez-le.

1. Activez l’hôte virtuel que vous venez de créer en créant un lien symbolique dans le `/etc/nginx/sites-enabled` directory:

   ```bash
   ln -s /etc/nginx/sites-available/magento /etc/nginx/sites-enabled
   ```

1. Vérifiez que la syntaxe est correcte :

   ```bash
   nginx -t
   ```

1. Redémarrez le nginx :

   ```bash
   systemctl restart nginx
   ```

### Vérification de l’installation

Ouvrez un navigateur web et accédez à l’URL de base de votre site pour [vérification de l’installation](../../next-steps/verify.md).

## CentOS 7

La section suivante décrit comment installer Adobe Commerce 2.x sur CentOS 7 à l’aide de nginx, PHP et MySQL.

### Installer nginx

```bash
yum -y install epel-release
```

```bash
yum -y install nginx
```

Une fois l’installation terminée, démarrez nginx et configurez-le pour qu’il démarre au moment du démarrage :

```bash
systemctl start nginx
```

```bash
systemctl enable nginx
```

Après avoir terminé les sections suivantes et installé l’application, nous utiliserons un exemple de fichier de configuration pour configurer nginx.

### Installation et configuration de php-fpm

Adobe Commerce nécessite plusieurs [PHP](../php-settings.md) des extensions pour fonctionner correctement. Outre ces extensions, vous devez également installer et configurer la variable `php-fpm` si vous utilisez nginx.

1. Installer `php-fpm`:

   ```bash
   yum -y install php70w-fpm
   ```

1. Ouvrez le `/etc/php.ini` dans un éditeur.

1. Ne commentez pas la variable `cgi.fix_pathinfo` et modifiez la valeur en `0`.

1. Editez le fichier pour qu&#39;il corresponde aux lignes suivantes :

   ```conf
   memory_limit = 2G
   max_execution_time = 1800
   zlib.output_compression = On
   ```

   >[!NOTE]
   >
   >Nous vous recommandons de définir la limite de mémoire sur 2 G lors du test d’Adobe Commerce ou de Magento Open Source. Voir [Paramètres PHP requis](../php-settings.md) pour plus d’informations.

1. Annulez la mise en commentaire du répertoire du chemin de session et définissez le chemin d’accès :

   ```conf
   session.save_path = "/var/lib/php/session"
   ```

1. Enregistrez l’éditeur, puis quittez-le.

1. Ouvrir `/etc/php-fpm.d/www.conf` dans un éditeur.

1. Editez le fichier pour qu&#39;il corresponde aux lignes suivantes :

   ```conf
   user = nginx
   group = nginx
   listen = /run/php-fpm/php-fpm.sock
   listen.owner = nginx
   listen.group = nginx
   listen.mode = 0660
   ```

1. Ne commentez pas les lignes de l’environnement :

   ```conf
   env[HOSTNAME] = $HOSTNAME
   env[PATH] = /usr/local/bin:/usr/bin:/bin
   env[TMP] = /tmp
   env[TMPDIR] = /tmp
   env[TEMP] = /tmp
   ```

1. Enregistrez l’éditeur, puis quittez-le.

1. Créez un répertoire pour le chemin de session PHP et remplacez le propriétaire par le `apache` utilisateur et groupe :

   ```bash
   mkdir -p /var/lib/php/session/
   ```

   ```bash
   chown -R apache:apache /var/lib/php/
   ```

1. Créez un répertoire pour le chemin de session PHP et remplacez le propriétaire par le `apache` utilisateur et groupe :

   ```bash
   mkdir -p /run/php-fpm/
   ```

   ```bash
   chown -R apache:apache /run/php-fpm/
   ```

1. Démarrez le `php-fpm` et configurez-le pour qu’il démarre au moment du démarrage :

   ```bash
   systemctl start php-fpm
   ```

   ```bash
   systemctl enable php-fpm
   ```

1. Vérifiez que la variable `php-fpm` le service est en cours d’exécution :

   ```bash
   netstat -pl | grep php-fpm.sock
   ```

### Installation et configuration de MySQL

Voir [MySQL](..//database/mysql.md) pour plus d’informations.

### Installation et configuration

Il existe plusieurs façons de télécharger Adobe Commerce, notamment :

* [Obtention du métaphorage du compositeur](../../composer.md)

* [Clonage du référentiel git](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/)

Cet exemple présente une installation basée sur le compositeur à l’aide de la ligne de commande.

1. Comme la variable [propriétaire du système de fichiers](../file-system/overview.md), connectez-vous à votre serveur d’applications.

1. Modifiez le répertoire docroot du serveur web ou un répertoire que vous avez configuré comme docroot d’hôte virtuel. Pour cet exemple, nous utilisons la valeur Ubuntu par défaut. `/var/www/html`.

   ```bash
   cd /var/www/html
   ```

1. Installez le compositeur globalement. Le compositeur est nécessaire pour mettre à jour les dépendances avant d’installer Adobe Commerce ou Magento Open Source :

   ```bash
   curl -sS https://getcomposer.org/installer | sudo php -- --install-dir=/usr/bin --filename=composer
   ```

1. Créez un projet de compositeur à l’aide du métapaquet Magento Open Source ou Adobe Commerce.

   **Magento Open Source**

   ```bash
   composer create-project --repository=https://repo.magento.com/ magento/project-community-edition <install-directory-name>
   ```

   **Adobe Commerce**

   ```bash
   composer create-project --repository=https://repo.magento.com/ magento/project-enterprise-edition <install-directory-name>
   ```

   Lorsque vous y êtes invité, saisissez le [clés d’authentification](../authentication-keys.md). Votre _clé publique_ est votre nom d’utilisateur ; votre _clé privée_ est votre mot de passe.

1. Définissez les autorisations de lecture-écriture pour le groupe de serveurs web avant d’installer l’application. Cela est nécessaire afin que la ligne de commande puisse écrire des fichiers dans le système de fichiers.

   ```bash
   cd /var/www/html/<magento install directory>
   ```

   ```bash
   find var generated vendor pub/static pub/media app/etc -type f -exec chmod g+w {} +
   ```

   ```bash
   find var generated vendor pub/static pub/media app/etc -type d -exec chmod g+ws {} +
   ```

   ```bash
   chown -R :www-data . # Ubuntu
   ```

   ```bash
   chmod u+x bin/magento
   ```

1. Installez à partir du [ligne de commande](../../advanced.md). Cet exemple suppose que le répertoire d’installation est nommé `magento2ee`, la variable `db-host` se trouve sur le même ordinateur (`localhost`), et que la variable `db-name`, `db-user`, et `db-password` sont tous `magento`:

   ```bash
   bin/magento setup:install \
   --base-url=http://localhost/magento2ee \
   --db-host=localhost \
   --db-name=magento \
   --db-user=magento \
   --db-password=magento \
   --backend-frontname=admin \
   --admin-firstname=admin \
   --admin-lastname=admin \
   --admin-email=admin@admin.com \
   --admin-user=admin \
   --admin-password=admin123 \
   --language=en_US \
   --currency=USD \
   --timezone=America/Chicago \
   --use-rewrites=1
   ```

1. Passez en mode Développeur :

   ```bash
   cd /var/www/html/magento2/bin
   ```

   ```bash
   ./magento deploy:mode:set developer
   ```

### Configuration de nginx

Il est recommandé de configurer nginx à l’aide de la méthode `nginx.conf.sample` fichier de configuration fourni dans le répertoire d’installation et l’hôte virtuel nginx.

Ces instructions supposent que vous utilisez l’emplacement par défaut de CentOS pour l’hôte virtuel nginx (par exemple, `/etc/nginx/conf.d`) et docroot par défaut (par exemple, `/usr/share/nginx/html`), toutefois, vous pouvez modifier ces emplacements en fonction de votre environnement.

1. Créez un hôte virtuel pour votre site :

   ```bash
   vim /etc/nginx/conf.d/magento.conf
   ```

1. Ajoutez la configuration suivante :

   ```conf
   upstream fastcgi_backend {
     server  unix:/run/php-fpm/php-fpm.sock;
   }
   
   server {
   
     listen 80;
     server_name www.magento-dev.com;
     set $MAGE_ROOT /usr/share/nginx/html/magento2;
     include /usr/share/nginx/html/magento2/nginx.conf.sample;
   }
   ```

   >[!NOTE]
   >
   >La variable `include` doit pointer vers l’exemple de fichier de configuration nginx dans votre répertoire d’installation.

1. Remplacer `www.magento-dev.com` par votre nom de domaine.

1. Enregistrez l’éditeur, puis quittez-le.

1. Vérifiez que la syntaxe est correcte :

   ```bash
   nginx -t
   ```

1. Redémarrez le nginx :

   ```bash
   systemctl restart nginx
   ```

### Configuration de SELinux et de Firewall

SELinux est activé par défaut sur CentOS 7. Utilisez la commande suivante pour voir si elle est en cours d’exécution :

```bash
sestatus
```

Pour configurer SELinux et firewall :

1. Installez les outils de gestion SELinux :

   ```bash
   yum -y install policycoreutils-python
   ```

1. Exécutez les commandes suivantes pour modifier le contexte de sécurité du répertoire d’installation :

   ```bash
   semanage fcontext -a -t httpd_sys_rw_content_t '/usr/share/nginx/html/magento2/app/etc(/.*)?'
   ```

   ```bash
   semanage fcontext -a -t httpd_sys_rw_content_t '/usr/share/nginx/html/magento2/var(/.*)?'
   ```

   ```bash
   semanage fcontext -a -t httpd_sys_rw_content_t '/usr/share/nginx/html/magento2/pub/media(/.*)?'
   ```

   ```bash
   semanage fcontext -a -t httpd_sys_rw_content_t '/usr/share/nginx/html/magento2/pub/static(/.*)?'
   ```

   ```bash
   restorecon -Rv '/usr/share/nginx/html/magento2/'
   ```

1. Installez le package firewall :

   ```bash
   yum -y install firewalld
   ```

1. Démarrez le service de pare-feu et configurez-le pour qu’il démarre au moment du démarrage :

   ```bash
   systemctl start firewalld
   ```

   ```bash
   systemctl enable firewalld
   ```

1. Exécutez les commandes suivantes pour ouvrir les ports pour HTTP et HTTPS afin d’accéder à l’URL de base à partir d’un navigateur web :

   ```bash
   firewall-cmd --permanent --add-service=http
   ```

   ```bash
   firewall-cmd --permanent --add-service=https
   ```

   ```bash
   firewall-cmd --reload
   ```

### Vérification de l’installation

Ouvrez un navigateur web et accédez à l’URL de base de votre site pour [vérification de l’installation](../../next-steps/verify.md).
