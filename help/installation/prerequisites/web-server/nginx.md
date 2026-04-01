---
title: Installation de Nginx pour les déploiements On-Premise
description: Découvrez comment installer et configurer le serveur web Nginx pour les déploiements d’Adobe Commerce sur site. Configurez PHP-FPM et votre hôte virtuel.
feature: Install, Configuration
badgePaas: label="On-premise" type="Informative" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="S’applique uniquement aux projets sur site Adobe Commerce."
exl-id: 041ddb9d-868e-4021-9388-1c9ea11bfd8f
source-git-commit: 352a71cb88ff38c0920201f49f1d7b889509fd61
workflow-type: tm+mt
source-wordcount: '1430'
ht-degree: 0%

---

# Installation de Nginx pour les déploiements sur site {#nginx}

Ce guide vous guide tout au long de l’installation de Nginx pour les déploiements sur site d’Adobe Commerce et de la configuration des paramètres Nginx requis par Commerce. Il comprend des procédures spécifiques au système d&#39;exploitation pour Ubuntu et CentOS, ainsi que des conseils pour la configuration de PHP-FPM. Adobe recommande de suivre les instructions de configuration fournies dans ce guide afin de préserver les fonctionnalités et la sécurité de l’application Commerce.

Adobe prend en charge les versions de Nginx répertoriées dans la [configuration requise](../../system-requirements.md) pour votre version d’Adobe Commerce. Les versions prises en charge varient selon les versions. Nginx nécessite également une configuration PHP-FPM prise en charge. Pour les exigences PHP associées, voir [PHP](../php-settings.md).

## Installer sur Ubuntu

Utilisez cette section pour installer Adobe Commerce sur Ubuntu avec Nginx, PHP et MySQL.

### Installer Nginx

```bash
sudo apt -y install nginx
```

Vous pouvez également [créer Nginx à partir de la source](https://www.armanism.com/blog/install-nginx-on-ubuntu).

Une fois que vous avez terminé les sections suivantes et installé l’application, utilisez l’exemple de fichier de configuration pour [configurer Nginx](#configure-nginx). Cette configuration recommandée permet de préserver les fonctionnalités et la sécurité de l’application Commerce.

### Installer et configurer PHP-FPM

Adobe Commerce requiert plusieurs [extensions PHP](../php-settings.md) pour fonctionner correctement. En plus de ces extensions, vous devez également installer et configurer l’extension `php-fpm` si vous utilisez Nginx.

Pour installer et configurer `php-fpm` :

1. Installez les packages `php-fpm` et `php-cli` pour la version PHP prise en charge par votre version d’Adobe Commerce. Sur Ubuntu, les noms de package suivent généralement le modèle suivant :

   ```bash
   apt-get -y install php<php-version>-fpm php<php-version>-cli
   ```

   >[!NOTE]
   >
   >Remplacez `<php-version>` par la version PHP mineure prise en charge répertoriée dans [configuration requise](../../system-requirements.md) pour la version d’Adobe Commerce que vous installez. Utilisez la même valeur dans les chemins d’accès aux fichiers, le nom du service et le chemin d’accès au socket dans les étapes suivantes.

1. Ouvrez les fichiers `php.ini` dans un éditeur :

   ```bash
   vim /etc/php/<php-version>/fpm/php.ini
   ```

   ```bash
   vim /etc/php/<php-version>/cli/php.ini
   ```

1. Modifiez les deux fichiers pour qu’ils correspondent aux lignes suivantes :

   ```conf
   memory_limit = 2G
   max_execution_time = 1800
   zlib.output_compression = On
   ```

   >[!NOTE]
   >
   >Adobe recommande de définir la limite de mémoire sur 2 Go lors du test d’Adobe Commerce. Pour plus d’informations, voir [Paramètres PHP requis](../php-settings.md).

1. Enregistrez et quittez l’éditeur.

1. Redémarrez le service `php-fpm` :

   ```bash
   systemctl restart php<php-version>-fpm
   ```

### Installation et configuration de MySQL

Voir [MySQL](../database/mysql.md) pour plus d’informations.

### Installation d’Adobe Commerce

Vous pouvez télécharger Adobe Commerce de plusieurs façons :

* [Obtenir le métapaquet du compositeur](../../composer.md)

* [Clonez le référentiel Git](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository)

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

   **&#x200B;**

   ```bash
   composer create-project --repository=https://repo.magento.com/ magento/project-community-edition <install-directory-name>
   ```

   **&#x200B;**

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

1. Installez à partir de la [ligne de commande](../../advanced.md). Cet exemple suppose que le répertoire d’installation est nommé `magento2ee` et que l’hôte de base de données se trouve sur le même ordinateur (`localhost`) :

   ```bash
   bin/magento setup:install \
   --base-url=http://localhost/magento2ee \
   --db-host=localhost \
   --db-name=<db-name> \
   --db-user=<db-user> \
   --db-password=<db-password> \
   --backend-frontname=<backend-uri> \
   --admin-firstname=<admin-first-name> \
   --admin-lastname=<admin-last-name> \
   --admin-email=<admin-email> \
   --admin-user=<admin-user> \
   --admin-password=<admin-password> \
   --language=en_US \
   --currency=USD \
   --timezone=America/Chicago \
   --use-rewrites=1 \
   --search-engine=<search-engine-value> \
   --<search-engine-host-parameter>=search-host.example.com \
   --<search-engine-port-parameter>=9200
   ```

   >[!NOTE]
   >
   >Utilisez la valeur `--search-engine` et les options hôte/port correspondantes requises par la version d’Adobe Commerce que vous installez. Pour les versions antérieures à la version 2.4.6, utilisez `elasticsearch7` avec les options `--elasticsearch-*` pour Elasticsearch 7 ou OpenSearch. Pour les versions 2.4.6 et ultérieures, utilisez la valeur du moteur de recherche et les options de ligne de commande correspondantes prises en charge par cette version.

1. Basculez vers le mode Développeur :

   ```bash
   cd /var/www/html/magento2/bin
   ```

   ```bash
   ./magento deploy:mode:set developer
   ```

### Configurer Nginx

Adobe recommande de configurer Nginx à l&#39;aide du fichier de configuration `nginx.conf.sample` fourni dans le répertoire d&#39;installation et de la configuration de votre hôte virtuel Nginx afin de préserver les fonctionnalités et la sécurité de l&#39;application Commerce.

>[!IMPORTANT]
>
>Le fichier `nginx.conf.sample` fournit le routage d’application requis ainsi que des règles de renforcement de la sécurité. Par exemple, elle limite l’exécution des scripts nuisibles chargés sur le serveur. Si vous n’utilisez pas ce fichier ou ne modifiez pas ses règles, vous êtes responsable de l’implémentation de contrôles de sécurité équivalents dans votre configuration d’onglets personnalisés.

Ces instructions supposent que vous utilisez l&#39;emplacement par défaut Ubuntu pour l&#39;hôte virtuel Nginx, tel que `/etc/nginx/sites-available`, et le docroot par défaut Ubuntu, tel que `/var/www/html`. Vous pouvez modifier ces emplacements en fonction de votre environnement.

1. Créez un hôte virtuel pour votre site :

   ```bash
   vim /etc/nginx/sites-available/magento
   ```

1. Ajoutez la configuration suivante :

   ```conf
   upstream fastcgi_backend {
     server  unix:/run/php/php<php-version>-fpm.sock;
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

1. Redémarrez Nginx :

   ```bash
   systemctl restart nginx
   ```

### Vérification de l’installation

Pour vérifier l’installation, ouvrez un navigateur web et accédez à l’URL de base de votre site. Pour plus d’informations, voir [Vérification de l’installation](../../next-steps/verify.md).

## Installer sous CentOS 7

Utilisez cette section pour installer Adobe Commerce sur CentOS 7 avec Nginx, PHP et MySQL.

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

Une fois que vous avez terminé les sections suivantes et installé l’application, utilisez un exemple de fichier de configuration pour configurer Nginx.

### Installer et configurer PHP-FPM

Adobe Commerce requiert plusieurs extensions [PHP](../php-settings.md) pour fonctionner correctement. En plus de ces extensions, vous devez également installer et configurer l’extension `php-fpm` si vous utilisez Nginx.

1. Installez `php-fpm` :

   ```bash
   yum -y install <php-fpm-package>
   ```

1. Ouvrez le fichier `/etc/php.ini` dans un éditeur.

   >[!NOTE]
   >
   >Installez le package qui fournit les `php-fpm` pour la version PHP prise en charge par la version Adobe Commerce que vous installez. Les noms de packages varient selon le référentiel et le système d’exploitation. Voir [&#x200B; Configuration requise &#x200B;](../../system-requirements.md).

1. Supprimez les commentaires de la ligne de `cgi.fix_pathinfo` et définissez la valeur sur `0`.

1. Modifiez le fichier pour qu’il corresponde aux lignes suivantes :

   ```conf
   memory_limit = 2G
   max_execution_time = 1800
   zlib.output_compression = On
   ```

   >[!NOTE]
   >
   >Adobe recommande de définir la limite de mémoire sur 2 Go lors du test d’Adobe Commerce. Pour plus d’informations, voir [Paramètres PHP requis](../php-settings.md).

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

1. Créez un répertoire pour le chemin de session PHP et modifiez le propriétaire en utilisateur et groupe `nginx` :

   ```bash
   mkdir -p /var/lib/php/session/
   ```

   ```bash
   chown -R nginx:nginx /var/lib/php/
   ```

1. Créez un répertoire pour le socket PHP-FPM et remplacez le propriétaire par l&#39;utilisateur et le groupe `nginx` :

   ```bash
   mkdir -p /run/php-fpm/
   ```

   ```bash
   chown -R nginx:nginx /run/php-fpm/
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

Voir [MySQL](../database/mysql.md) pour plus d’informations.

### Installation d’Adobe Commerce

Vous pouvez télécharger Adobe Commerce de plusieurs façons :

* [Obtenir le métapaquet du compositeur](../../composer.md)

* [Clonez le référentiel Git](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository)

Cet exemple illustre une installation basée sur le compositeur à l’aide de la ligne de commande .

1. Connectez-vous à votre serveur d’applications en tant que [propriétaire du système de fichiers](../file-system/overview.md).

1. Passez au répertoire docroot du serveur web ou à un répertoire que vous avez configuré en tant qu&#39;hôte virtuel docroot. Pour cet exemple, utilisez la `/usr/share/nginx/html` par défaut de CentOS.

   ```bash
   cd /usr/share/nginx/html
   ```

1. Installez Composer globalement. Le compositeur est nécessaire pour mettre à jour les dépendances avant d’installer Adobe Commerce :

   ```bash
   curl -sS https://getcomposer.org/installer | sudo php -- --install-dir=/usr/bin --filename=composer
   ```

1. Créez un projet Composer à l’aide du métapaquet Adobe Commerce.

   **&#x200B;**

   ```bash
   composer create-project --repository=https://repo.magento.com/ magento/project-community-edition <install-directory-name>
   ```

   **&#x200B;**

   ```bash
   composer create-project --repository=https://repo.magento.com/ magento/project-enterprise-edition <install-directory-name>
   ```

   A l’invite, saisissez vos [clés d’authentification](../authentication-keys.md). Votre _clé publique_ est votre nom d’utilisateur ; votre _clé privée_ est votre mot de passe.

1. Définissez les autorisations de lecture et d’écriture pour le groupe de serveurs web avant d’installer l’application. Cela est nécessaire pour que la ligne de commande puisse écrire des fichiers dans le système de fichiers.

   ```bash
   cd /usr/share/nginx/html/<magento install directory>
   ```

   ```bash
   find var generated vendor pub/static pub/media app/etc -type f -exec chmod g+w {} +
   ```

   ```bash
   find var generated vendor pub/static pub/media app/etc -type d -exec chmod g+ws {} +
   ```

   ```bash
   chown -R :nginx . # CentOS
   ```

   ```bash
   chmod u+x bin/magento
   ```

1. Installez à partir de la [ligne de commande](../../advanced.md). Cet exemple suppose que le répertoire d’installation est nommé `magento2ee` et que l’hôte de base de données se trouve sur le même ordinateur (`localhost`) :

   ```bash
   bin/magento setup:install \
   --base-url=http://localhost/magento2ee \
   --db-host=localhost \
   --db-name=<db-name> \
   --db-user=<db-user> \
   --db-password=<db-password> \
   --backend-frontname=<backend-uri> \
   --admin-firstname=<admin-first-name> \
   --admin-lastname=<admin-last-name> \
   --admin-email=<admin-email> \
   --admin-user=<admin-user> \
   --admin-password=<admin-password> \
   --language=en_US \
   --currency=USD \
   --timezone=America/Chicago \
   --use-rewrites=1
   ```

1. Basculez vers le mode Développeur :

   ```bash
   cd /usr/share/nginx/html/magento2/bin
   ```

   ```bash
   ./magento deploy:mode:set developer
   ```

### Configurer Nginx

Nous vous recommandons de configurer Nginx en utilisant le fichier `nginx.conf.sample` dans le répertoire d&#39;installation et votre configuration d&#39;hôte virtuel Nginx.

>[!IMPORTANT]
>
>Le fichier `nginx.conf.sample` fournit le routage d’application requis ainsi que des règles de renforcement de la sécurité. Par exemple, elle limite l’exécution des scripts nuisibles chargés sur le serveur. Si vous n’utilisez pas ce fichier ou ne modifiez pas ses règles, vous êtes responsable de l’implémentation de contrôles de sécurité équivalents dans votre configuration d’onglets personnalisés.

Ces instructions supposent que vous utilisez l’emplacement par défaut de CentOS pour l’hôte virtuel Nginx, tel que `/etc/nginx/conf.d`, et la racine docroot par défaut, telle que `/usr/share/nginx/html`. Vous pouvez modifier ces emplacements en fonction de votre environnement.

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

1. Redémarrez Nginx :

   ```bash
   systemctl restart nginx
   ```

### Configuration de SELinux et du pare-feu

SELinux est activé par défaut sur CentOS 7. Utilisez la commande suivante pour confirmer qu’il est en cours d’exécution :

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

Pour vérifier l’installation, ouvrez un navigateur web et accédez à l’URL de base de votre site. Pour plus d’informations, voir [Vérification de l’installation](../../next-steps/verify.md).
