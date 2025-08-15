---
title: Nginx
description: Pour installer et configurer le serveur web Nginx pour les installations sur site d’Adobe Commerce, procédez comme suit.
exl-id: 041ddb9d-868e-4021-9388-1c9ea11bfd8f
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '1110'
ht-degree: 0%

---

# Nginx

Adobe Commerce prend en charge nginx 1.x (ou la [dernière version mainline](https://nginx.org/en/linux_packages.html#mainline)). Vous devez également installer la dernière version de `php-fpm`.

Les instructions d’installation varient en fonction du système d’exploitation utilisé. Voir [PHP](../php-settings.md) pour plus d’informations.

## Ubuntu

La section suivante décrit comment installer Adobe Commerce 2.x sur Ubuntu à l’aide de nginx, PHP et MySQL.

### Installer Nginx

```bash
sudo apt -y install nginx
```

Vous pouvez également [créer nginx à partir de la source](https://www.armanism.com/blog/install-nginx-on-ubuntu)

Après avoir complété les sections suivantes et installé l’application, nous utiliserons un exemple de fichier de configuration pour [configurer nginx](#configure-nginx).

### Installation et configuration de php-fpm

Adobe Commerce requiert plusieurs [extensions PHP](../php-settings.md) pour fonctionner correctement. En plus de ces extensions, vous devez également installer et configurer l’extension `php-fpm` si vous utilisez nginx.

Pour installer et configurer `php-fpm` :

1. Installez `php-fpm` et `php-cli` :

   ```bash
   apt-get -y install php7.2-fpm php7.2-cli
   ```

   >[!NOTE]
   >
   >Cette commande installe la dernière version disponible de PHP 7.2.X. Voir [configuration requise](../../system-requirements.md) pour les versions PHP prises en charge.

1. Ouvrez les fichiers `php.ini` dans un éditeur :

   ```bash
   vim /etc/php/7.2/fpm/php.ini
   ```

   ```bash
   vim /etc/php/7.2/cli/php.ini
   ```

1. Modifiez les deux fichiers pour qu’ils correspondent aux lignes suivantes :

   ```conf
   memory_limit = 2G
   max_execution_time = 1800
   zlib.output_compression = On
   ```

   >[!NOTE]
   >
   >Nous vous recommandons de définir la limite de mémoire sur 2 Go lors du test d’Adobe Commerce. Pour plus d’informations, voir [Paramètres PHP requis](../php-settings.md).

1. Enregistrez et quittez l’éditeur.

1. Redémarrez le service `php-fpm` :

   ```bash
   systemctl restart php7.2-fpm
   ```

### Installation et configuration de MySQL

Voir [MySQL](../database/mysql.md) pour plus d’informations.

### Installation et configuration

Il existe plusieurs façons de télécharger Adobe Commerce, notamment :

* [Obtenir le métapaquet du compositeur](../../composer.md)

* [Clonez le référentiel Git](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/)

Cet exemple illustre une installation basée sur le compositeur à l’aide de la ligne de commande .

1. Connectez-vous à votre serveur d’applications en tant que [propriétaire du système de fichiers](../file-system/overview.md).

1. Passez au répertoire docroot du serveur web ou à un répertoire que vous avez configuré en tant qu&#39;hôte virtuel docroot. Pour cet exemple, nous utilisons le `/var/www/html` par défaut Ubuntu.

   ```bash
   cd /var/www/html
   ```

1. Installez Composer globalement. Le compositeur est nécessaire pour mettre à jour les dépendances avant d’installer Adobe Commerce :

   ```bash
   curl -sS https://getcomposer.org/installer | sudo php -- --install-dir=/usr/bin --filename=composer
   ```

1. Créez un projet Composer à l’aide du métapaquet Adobe Commerce.

   **Magento Open Source**

   ```bash
   composer create-project --repository=https://repo.magento.com/ magento/project-community-edition <install-directory-name>
   ```

   **Adobe Commerce**

   ```bash
   composer create-project --repository=https://repo.magento.com/ magento/project-enterprise-edition <install-directory-name>
   ```

   A l’invite, saisissez vos [clés d’authentification](../authentication-keys.md). Votre _clé publique_ est votre nom d’utilisateur ; votre _clé privée_ est votre mot de passe.

1. Définissez les autorisations de lecture et d’écriture pour le groupe de serveurs web avant d’installer l’application. Cela est nécessaire pour que la ligne de commande puisse écrire des fichiers dans le système de fichiers.

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

1. Installez à partir de la [ligne de commande](../../advanced.md). Cet exemple suppose que le répertoire d’installation est nommé `magento2ee`, que le `db-host` se trouve sur le même ordinateur (`localhost`) et que les `db-name`, `db-user` et `db-password` sont tous `magento` :

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

1. Basculez vers le mode Développeur :

   ```bash
   cd /var/www/html/magento2/bin
   ```

   ```bash
   ./magento deploy:mode:set developer
   ```

### Configuration de Nginx

Nous vous recommandons de configurer nginx en utilisant le fichier de configuration `nginx.conf.sample` fourni dans le répertoire d&#39;installation et l&#39;hôte virtuel nginx.

Ces instructions supposent que vous utilisez l&#39;emplacement par défaut Ubuntu pour l&#39;hôte virtuel nginx (par exemple, `/etc/nginx/sites-available`) et la racine docroot par défaut Ubuntu (par exemple, `/var/www/html`), mais vous pouvez modifier ces emplacements en fonction de votre environnement.

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
   >La directive `include` doit pointer vers l&#39;exemple de fichier de configuration nginx dans votre répertoire d&#39;installation.

1. Remplacez `www.magento-dev.com` par votre nom de domaine. Elle doit correspondre à l’URL de base que vous avez spécifiée lors de l’installation d’Adobe Commerce.

1. Enregistrez et quittez l’éditeur.

1. Activez l’hôte virtuel que vous venez de créer en y créant un lien symbolique dans le répertoire `/etc/nginx/sites-enabled` :

   ```bash
   ln -s /etc/nginx/sites-available/magento /etc/nginx/sites-enabled
   ```

1. Vérifiez que la syntaxe est correcte :

   ```bash
   nginx -t
   ```

1. Redémarrez Angles :

   ```bash
   systemctl restart nginx
   ```

### Vérification de l’installation

Ouvrez un navigateur web et accédez à l’URL de base de votre site pour [vérifier l’installation](../../next-steps/verify.md).

## CentOS 7

La section suivante décrit comment installer Adobe Commerce 2.x sur CentOS 7 à l’aide de nginx, PHP et MySQL.

### Installer Nginx

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

Après avoir complété les sections suivantes et installé l’application, nous utiliserons un exemple de fichier de configuration pour configurer nginx.

### Installation et configuration de php-fpm

Adobe Commerce requiert plusieurs extensions [PHP](../php-settings.md) pour fonctionner correctement. En plus de ces extensions, vous devez également installer et configurer l&#39;extension `php-fpm` si vous utilisez nginx.

1. Installez `php-fpm` :

   ```bash
   yum -y install php70w-fpm
   ```

1. Ouvrez le fichier `/etc/php.ini` dans un éditeur.

1. Supprimez les commentaires de la ligne de `cgi.fix_pathinfo` et définissez la valeur sur `0`.

1. Modifiez le fichier pour qu’il corresponde aux lignes suivantes :

   ```conf
   memory_limit = 2G
   max_execution_time = 1800
   zlib.output_compression = On
   ```

   >[!NOTE]
   >
   >Nous vous recommandons de définir la limite de mémoire sur 2 Go lors du test d’Adobe Commerce. Pour plus d’informations, voir [Paramètres PHP requis](../php-settings.md).

1. Supprimez les commentaires du répertoire de chemin de session et définissez le chemin d’accès :

   ```conf
   session.save_path = "/var/lib/php/session"
   ```

1. Enregistrez et quittez l’éditeur.

1. Ouvrez `/etc/php-fpm.d/www.conf` dans un éditeur.

1. Modifiez le fichier pour qu’il corresponde aux lignes suivantes :

   ```conf
   user = nginx
   group = nginx
   listen = /run/php-fpm/php-fpm.sock
   listen.owner = nginx
   listen.group = nginx
   listen.mode = 0660
   ```

1. Supprimez les commentaires des lignes d’environnement :

   ```conf
   env[HOSTNAME] = $HOSTNAME
   env[PATH] = /usr/local/bin:/usr/bin:/bin
   env[TMP] = /tmp
   env[TMPDIR] = /tmp
   env[TEMP] = /tmp
   ```

1. Enregistrez et quittez l’éditeur.

1. Créez un répertoire pour le chemin de session PHP et modifiez le propriétaire en utilisateur et groupe `apache` :

   ```bash
   mkdir -p /var/lib/php/session/
   ```

   ```bash
   chown -R apache:apache /var/lib/php/
   ```

1. Créez un répertoire pour le chemin de session PHP et modifiez le propriétaire en utilisateur et groupe `apache` :

   ```bash
   mkdir -p /run/php-fpm/
   ```

   ```bash
   chown -R apache:apache /run/php-fpm/
   ```

1. Démarrez le service `php-fpm` et configurez-le pour qu&#39;il démarre au démarrage :

   ```bash
   systemctl start php-fpm
   ```

   ```bash
   systemctl enable php-fpm
   ```

1. Vérifiez que le service `php-fpm` est en cours d’exécution :

   ```bash
   netstat -pl | grep php-fpm.sock
   ```

### Installation et configuration de MySQL

Voir [MySQL](..//database/mysql.md) pour plus d’informations.

### Installation et configuration

Il existe plusieurs façons de télécharger Adobe Commerce, notamment :

* [Obtenir le métapaquet du compositeur](../../composer.md)

* [Clonez le référentiel Git](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/)

Cet exemple illustre une installation basée sur le compositeur à l’aide de la ligne de commande .

1. Connectez-vous à votre serveur d’applications en tant que [propriétaire du système de fichiers](../file-system/overview.md).

1. Passez au répertoire docroot du serveur web ou à un répertoire que vous avez configuré en tant qu&#39;hôte virtuel docroot. Pour cet exemple, nous utilisons le `/var/www/html` par défaut Ubuntu.

   ```bash
   cd /var/www/html
   ```

1. Installez Composer globalement. Le compositeur est nécessaire pour mettre à jour les dépendances avant d’installer Adobe Commerce :

   ```bash
   curl -sS https://getcomposer.org/installer | sudo php -- --install-dir=/usr/bin --filename=composer
   ```

1. Créez un projet Composer à l’aide du métapaquet Adobe Commerce.

   **Magento Open Source**

   ```bash
   composer create-project --repository=https://repo.magento.com/ magento/project-community-edition <install-directory-name>
   ```

   **Adobe Commerce**

   ```bash
   composer create-project --repository=https://repo.magento.com/ magento/project-enterprise-edition <install-directory-name>
   ```

   A l’invite, saisissez vos [clés d’authentification](../authentication-keys.md). Votre _clé publique_ est votre nom d’utilisateur ; votre _clé privée_ est votre mot de passe.

1. Définissez les autorisations de lecture et d’écriture pour le groupe de serveurs web avant d’installer l’application. Cela est nécessaire pour que la ligne de commande puisse écrire des fichiers dans le système de fichiers.

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

1. Installez à partir de la [ligne de commande](../../advanced.md). Cet exemple suppose que le répertoire d’installation est nommé `magento2ee`, que le `db-host` se trouve sur le même ordinateur (`localhost`) et que les `db-name`, `db-user` et `db-password` sont tous `magento` :

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

1. Basculez vers le mode Développeur :

   ```bash
   cd /var/www/html/magento2/bin
   ```

   ```bash
   ./magento deploy:mode:set developer
   ```

### Configuration de Nginx

Nous vous recommandons de configurer nginx en utilisant le fichier de configuration `nginx.conf.sample` fourni dans le répertoire d&#39;installation et l&#39;hôte virtuel nginx.

Ces instructions supposent que vous utilisez l’emplacement par défaut de CentOS pour l’hôte virtuel nginx (par exemple, `/etc/nginx/conf.d`) et docroot par défaut (par exemple, `/usr/share/nginx/html`), mais vous pouvez modifier ces emplacements en fonction de votre environnement.

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
   >La directive `include` doit pointer vers l&#39;exemple de fichier de configuration nginx dans votre répertoire d&#39;installation.

1. Remplacez `www.magento-dev.com` par votre nom de domaine.

1. Enregistrez et quittez l’éditeur.

1. Vérifiez que la syntaxe est correcte :

   ```bash
   nginx -t
   ```

1. Redémarrez Angles :

   ```bash
   systemctl restart nginx
   ```

### Configuration de SELinux et de Firewall

SELinux est activé par défaut sur CentOS 7. Utilisez la commande suivante pour vérifier si elle est en cours d’exécution :

```bash
sestatus
```

Pour configurer SELinux et le pare-feu :

1. Installez les outils de gestion SELinux :

   ```bash
   yum -y install policycoreutils-python
   ```

1. Exécutez les commandes suivantes pour modifier le contexte de sécurité du répertoire d&#39;installation :

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

1. Installez le package de pare-feu :

   ```bash
   yum -y install firewalld
   ```

1. Démarrez le service de pare-feu et configurez-le pour qu&#39;il démarre au démarrage :

   ```bash
   systemctl start firewalld
   ```

   ```bash
   systemctl enable firewalld
   ```

1. Exécutez les commandes suivantes pour ouvrir les ports HTTP et HTTPS afin de pouvoir accéder à l’URL de base à partir d’un navigateur web :

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

Ouvrez un navigateur web et accédez à l’URL de base de votre site pour [vérifier l’installation](../../next-steps/verify.md).
