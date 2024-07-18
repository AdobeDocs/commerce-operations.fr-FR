---
title: Options du mode de maintenance pour la mise à niveau
description: Créez une page de mode de maintenance personnalisée que vos clients voient sur votre vitrine Adobe Commerce pendant l’exécution d’une mise à niveau.
exl-id: 77e6d82d-5cc6-4d14-8b5c-1d2108f27b29
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '382'
ht-degree: 0%

---

# Options du mode de maintenance pour la mise à niveau

Cette rubrique explique comment créer une page de maintenance personnalisée à afficher aux utilisateurs pendant la mise à niveau de votre application de Magento. La création d’une page personnalisée est facultative, mais recommandée, car votre site est accessible pendant une partie de la mise à niveau.

La création d’une page personnalisée vers laquelle rediriger les utilisateurs empêche tout accès au site et informe également les utilisateurs que le site est en cours de maintenance.

>[!NOTE]
>
>Vous devez effectuer les tâches de cette section en tant qu’utilisateur disposant des privilèges `root`. Les pages de maintenance personnalisées ne peuvent pas être définies en mode développeur.

## Création d’une page de maintenance personnalisée

Pour créer une page de maintenance et la rediriger vers celle-ci, vous devez d’abord créer une page de maintenance nommée :

- Apache : `<web server docroot>/maintenance.html`
- nginx : `<magento_root>/maintenance.html`

Ajoutez les contenus suivants :

```html
<!DOCTYPE html>
<html>
<head>
<title>Temporarily Offline</title>
<meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
<style>
h1
{ font-size: 50px; }

body
{ text-align:center; font: 20px Helvetica, sans-serif; color: #333; }

</style>
</head>
<body>

# Temporarily offline

<p>We're down for a short time to perform maintenance on our site to give you the best possible experience. Check back soon!</p>
</body>
</html>
```

## Page de maintenance personnalisée pour Apache

Cette section explique comment créer une page de maintenance personnalisée et comment rediriger le trafic vers cette page.

L’exemple de cette section montre comment modifier les fichiers suivants, ce qui est une façon de configurer votre page de maintenance :

- Apache 2.4 : `/etc/apache2/sites-available/000-default.conf`
- Apache 2.2 : `/etc/apache2/sites-available/default` (Ubuntu), `/etc/httpd/conf/httpd.conf` (CentOS)

Pour rediriger le trafic vers une page de maintenance personnalisée :

1. Mettez à jour votre configuration Apache pour effectuer les opérations suivantes :

   - Rediriger tout le trafic vers la page de maintenance
   - Placez sur la liste autorisée certaines adresses IP afin qu’un administrateur puisse mettre à niveau le logiciel du Magento.

   L’exemple suivant place sur la liste autorisée la version 192.0.2.110.

   Ajoutez ce qui suit à la fin de votre fichier de configuration Apache :

   ```
   RewriteEngine On
   RewriteCond %{REMOTE_ADDR} !^192\.0\.2\.110
   RewriteCond %{DOCUMENT_ROOT}/maintenance.html -f
   RewriteCond %{DOCUMENT_ROOT}/maintenance.enable -f
   RewriteCond %{SCRIPT_FILENAME} !maintenance.html
   RewriteRule ^.*$ /maintenance.html [R=503,L]
   ErrorDocument 503 /maintenance.html
   Header Set Cache-Control "max-age=0, no-store"
   ```

1. Redémarrez Apache :

   - CentOS : `service httpd restart`
   - Ubuntu : `service apache2 restart`

1. Saisissez la commande suivante :

   ```bash
   touch <web server docroot>/maintenance.enable
   ```

1. [Mettez à niveau votre système](../implementation/perform-upgrade.md).
1. Testez votre site pour vous assurer qu’il fonctionne correctement.
1. Une fois la mise à niveau terminée, supprimez `maintenance.enable`.

## Page de maintenance personnalisée de nginx

Cette section explique comment créer une page de maintenance personnalisée et comment rediriger le trafic vers cette page.

Pour rediriger le trafic vers une page de maintenance personnalisée :

1. Utilisez un éditeur de texte pour ouvrir le fichier de configuration nginx contenant votre bloc de serveur.
1. Ajoutez le code suivant au bloc de serveur (`server` s’affiche pour plus de clarté uniquement ; n’ajoutez pas de second bloc de serveur).

   Les listes autorisées suivantes  les adresses IP 192.0.2.110 et 192.0.2.115 sur un système où Magento est installé dans `/var/www/html/magento2` :

   ```conf
   server {
        listen 80;
        set $MAGE_ROOT /var/www/html/magento2;
   
        set $maintenance off;
   
        if (-f $MAGE_ROOT/maintenance.enable) {
            set $maintenance on;
        }
   
        if ($remote_addr ~ (192.0.2.110|192.0.2.115)) {
            set $maintenance off;
        }
   
        if ($maintenance = on) {
            return 503;
        }
   
        location /maintenance {
        }
   
        error_page 503 @maintenance;
   
        location @maintenance {
        root $MAGE_ROOT;
        rewrite ^(.*)$ /maintenance.html break;
    }
   
        include /var/www/html/magento2/nginx.conf;
   }
   ```

1. Saisissez la commande suivante :

   ```bash
   touch <magento_root>/maintenance.enable
   ```

1. Rechargez la configuration de nginx :

   ```bash
   service nginx reload
   ```

1. [Mettez à niveau votre système](../implementation/perform-upgrade.md).
1. Testez votre site pour vous assurer qu’il fonctionne correctement.
1. Une fois la mise à niveau terminée, supprimez ou renommez `maintenance.enable`
1. Rechargez la configuration de nginx :

   ```bash
   service nginx reload
   ```
