---
title: Configuration de plusieurs sites web avec Nginx
description: Suivez ce tutoriel pour configurer plusieurs sites web avec Nginx.
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '959'
ht-degree: 0%

---


# Configuration de plusieurs sites web avec Nginx

Nous supposons que :

- Vous travaillez sur une machine de développement (ordinateur portable, machine virtuelle ou autre).

   Des tâches supplémentaires peuvent être nécessaires pour déployer plusieurs sites web dans un environnement hébergé ; contactez votre fournisseur d’hébergement pour plus d’informations.

   Des tâches supplémentaires sont requises pour configurer Adobe Commerce sur l’infrastructure cloud. Une fois les tâches abordées dans cette rubrique terminées, reportez-vous à la section [Configuration de plusieurs sites web ou magasins](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites.html) dans le _Guide sur l’infrastructure de Commerce on Cloud_.

- Vous acceptez plusieurs domaines dans un fichier d’hôte virtuel ou utilisez un hôte virtuel par site Web ; les fichiers de configuration de l’hôte virtuel se trouvent dans `/etc/nginx/sites-available`.
- Vous utilisez le `nginx.conf.sample` fourni par Commerce avec uniquement les modifications abordées dans ce tutoriel.
- Le logiciel Commerce est installé dans `/var/www/html/magento2`.
- Vous avez deux sites web autres que le site par défaut :

   - `french.mysite.mg` avec code du site web `french` et stocker le code d’affichage `fr`
   - `german.mysite.mg` avec code du site web `german` et stocker le code d’affichage `de`
   - `mysite.mg` est le site web par défaut et la vue de magasin par défaut.

>[!TIP]
>
>Voir [Créer des sites web](ms-admin.md#step-2-create-websites) et [Créer des vues de magasin](ms-admin.md#step-4-create-store-views) pour obtenir de l’aide sur la localisation de ces valeurs.

Voici une feuille de route pour la configuration de plusieurs sites web avec nginx :

1. [Configuration des sites web, des magasins et des vues de magasin](ms-admin.md) dans Admin.
1. Créez un [Hôte virtuel Nginx](#step-2-create-nginx-virtual-hosts)) pour mapper de nombreux sites web ou un hôte virtuel Nginx par site web Commerce (étapes détaillées ci-dessous).
1. Transmettez les valeurs de la variable [Variables MAGE](ms-overview.md) `$MAGE_RUN_TYPE` et `$MAGE_RUN_CODE` pour signer à l’aide du Magento fourni `nginx.conf.sample` (étapes détaillées ci-dessous).

   - `$MAGE_RUN_TYPE` peut être `store` ou `website`:

      - Utilisation `website` pour charger votre site web dans votre storefront.
      - Utilisation `store` pour charger n’importe quelle vue de magasin dans votre storefront.
   - `$MAGE_RUN_CODE` est le code d’affichage unique du site web ou du magasin qui correspond à `$MAGE_RUN_TYPE`.


1. Mettez à jour la configuration de l’URL de base sur l’administrateur Commerce.

## Étape 1 : Créer des sites web, des magasins et des vues de magasin dans l’administrateur

Voir [Configuration de plusieurs sites web, magasins et vues de magasin dans l’administrateur](ms-admin.md).

## Étape 2 : Création d’hôtes virtuels nginx

Cette étape explique comment charger des sites web sur le storefront. Vous pouvez utiliser des sites web ou des vues de magasin ; si vous utilisez des vues de magasin, vous devez ajuster les valeurs de paramètre en conséquence. Vous devez effectuer les tâches de cette section en tant qu’utilisateur avec `sudo` des privilèges.

En utilisant un seul [fichier d’hôte virtuel nginx](#step-2-create-nginx-virtual-hosts), vous pouvez garder simple et propre votre configuration de ingx. En utilisant plusieurs fichiers d’hôtes virtuels, vous pouvez personnaliser chaque magasin (pour utiliser un emplacement personnalisé pour `french.mysite.mg` par exemple).

**Pour créer un hôte virtuel** (simplifié) :

Cette configuration s’étend à [configuration nginx](../../installation/prerequisites/web-server/nginx.md).

1. Ouvrez un éditeur de texte et ajoutez le contenu suivant à un nouveau fichier nommé `/etc/nginx/sites-available/magento`:

   ```conf
   map $http_host $MAGE_RUN_CODE {
       default '';
       french.mysite.mg french;
       german.mysite.mg german;
   }
   
   server {
       listen 80;
       server_name mysite.mg french.mysite.mg german.mysite.mg;
       set $MAGE_ROOT /var/www/html/magento2;
       set $MAGE_MODE developer;
       set $MAGE_RUN_TYPE website; #or set $MAGE_RUN_TYPE store;
       include /var/www/html/magento2/nginx.conf;
   }
   ```

1. Enregistrez vos modifications dans les fichiers et quittez l’éditeur de texte.
1. Vérifiez la configuration du serveur :

   ```bash
   nginx -t
   ```

1. En cas de réussite, le message suivant s’affiche :

   ```terminal
   nginx: configuration file /etc/nginx/nginx.conf test is successful
   ```

   Si des erreurs s’affichent, vérifiez la syntaxe de vos fichiers de configuration d’hôte virtuel.

1. Créez un lien symbolique dans le `/etc/nginx/sites-enabled` directory:

   ```bash
   cd /etc/nginx/sites-enabled
   ```

   ```bash
   ln -s /etc/nginx/sites-available/magento magento
   ```

Pour plus d’informations sur la directive map, voir [Documentation de nginx sur la directive map](http://nginx.org/en/docs/http/ngx_http_map_module.html#map).


**Pour créer plusieurs hôtes virtuels**:

1. Ouvrez un éditeur de texte et ajoutez le contenu suivant à un nouveau fichier nommé `/etc/nginx/sites-available/french.mysite.mg`:

   ```conf
   server {
       listen 80;
       server_name french.mysite.mg;
       set $MAGE_ROOT /var/www/html/magento2;
       set $MAGE_MODE developer;
       set $MAGE_RUN_TYPE website; #or set $MAGE_RUN_TYPE store;
       set $MAGE_RUN_CODE french;
       include /var/www/html/magento2/nginx.conf;
   }
   ```

1. Créez un autre fichier nommé `german.mysite.mg` dans le même répertoire avec les contenus suivants :

   ```conf
   server {
       listen 80;
       server_name german.mysite.mg;
       set $MAGE_ROOT /var/www/html/magento2;
       set $MAGE_MODE developer;
       set $MAGE_RUN_TYPE website; #or set $MAGE_RUN_TYPE store;
       set $MAGE_RUN_CODE german;
       include /var/www/html/magento2/nginx.conf;
   }
   ```

1. Enregistrez vos modifications dans les fichiers et quittez l’éditeur de texte.
1. Vérifiez la configuration du serveur :

   ```bash
   nginx -t
   ```

1. En cas de réussite, le message suivant s’affiche :

   ```terminal
   nginx: configuration file /etc/nginx/nginx.conf test is successful
   ```

   Si des erreurs s’affichent, vérifiez la syntaxe de vos fichiers de configuration d’hôte virtuel.

1. Créez des liens symboliques dans le `/etc/nginx/sites-enabled` directory:

   ```bash
   cd /etc/nginx/sites-enabled
   ```

   ```bash
   ln -s /etc/nginx/sites-available/french.mysite.mg french.mysite.mg
   ```

   ```bash
   ln -s /etc/nginx/sites-available/german.mysite.mg german.mysite.mg
   ```

## Étape 3 : Modifier nginx.conf.sample

>[!TIP]
>
>Ne modifiez pas la variable `nginx.conf.sample` fichier; il s’agit d’un fichier Commerce de base qui peut être mis à jour avec chaque nouvelle version. Copiez plutôt la variable `nginx.conf.sample` , renommez-le, puis modifiez le fichier copié.

**Pour modifier le point d’entrée PHP de l’application principale**:

Pour modifier la variable `nginx.conf.sample` file**:

1. Ouvrez un éditeur de texte et passez en revue les `nginx.conf.sample` fichier ,`<magento2_installation_directory>/nginx.conf.sample`. Recherchez la section suivante :

   ```conf
   # PHP entry point for main application
   location ~ (index|get|static|report|404|503|health_check)\.php$ {
       try_files $uri =404;
       fastcgi_pass   fastcgi_backend;
       fastcgi_buffers 1024 4k;
   
       fastcgi_param  PHP_FLAG  "session.auto_start=off \n suhosin.session.cryptua=off";
       fastcgi_param  PHP_VALUE "memory_limit=1G \n max_execution_time=18000";
       fastcgi_read_timeout 600s;
       fastcgi_connect_timeout 600s;
   
       fastcgi_index  index.php;
       fastcgi_param  SCRIPT_FILENAME  $document_root$fastcgi_script_name;
       include        fastcgi_params;
   }
   ```

1. Mettez à jour le `nginx.conf.sample` avec les deux lignes suivantes avant l’instruction d’inclusion :

   ```conf
   fastcgi_param MAGE_RUN_TYPE $MAGE_RUN_TYPE;
   fastcgi_param MAGE_RUN_CODE $MAGE_RUN_CODE;
   ```

Voici un exemple de point d’entrée PHP mis à jour pour l’application principale :

```conf
# PHP entry point for main application

location ~ (index|get|static|report|404|503|health_check)\.php$ {
    try_files $uri =404;
    fastcgi_pass   fastcgi_backend;
    fastcgi_buffers 1024 4k;

    fastcgi_param  PHP_FLAG  "session.auto_start=off \n suhosin.session.cryptua=off";
    fastcgi_param  PHP_VALUE "memory_limit=1G \n max_execution_time=18000";
    fastcgi_read_timeout 600s;
    fastcgi_connect_timeout 600s;

    fastcgi_index  index.php;
    fastcgi_param  SCRIPT_FILENAME  $document_root$fastcgi_script_name;
    # START - Multisite customization
    fastcgi_param MAGE_RUN_TYPE $MAGE_RUN_TYPE;
    fastcgi_param MAGE_RUN_CODE $MAGE_RUN_CODE;
    # END - Multisite customization
    include        fastcgi_params;
}
```

## Étape 4 : Mise à jour de la configuration de l’URL de base

Vous devez mettre à jour l’URL de base de la variable `french` et le `german` sites web dans l’administrateur Commerce.

### Mettre à jour l’URL de base du site web français

1. Connectez-vous à l’administrateur Commerce et accédez à **Magasins** > **Paramètres** > **Configuration** > **Général** > **Web**.
1. Modifiez la variable _portée de configuration_ au `french` site web.
1. Développer **URL de base** et mettre à jour la section **URL de base** et **URL du lien de base** valeur à `http://french.magento24.com/`.
1. Développer **URL de base (sécurisées)** et mettre à jour la section **URL de base sécurisée** et **URL du lien de base sécurisé** valeur à `https://french.magento24.com/`.
1. Cliquez sur **Enregistrer la configuration** et enregistrez les modifications de configuration.

### Mettre à jour l’URL de base du site web allemand

1. Connectez-vous à l’administrateur Commerce et accédez à **Magasins** > **Paramètres** > **Configuration** > **Général** > **Web**.
1. Modifiez la variable _portée de configuration_ au `german` site web.
1. Développer **URL de base** et mettre à jour la section **URL de base** et **URL du lien de base** valeur à `http://german.magento24.com/`.
1. Développer **URL de base (sécurisées)** et mettre à jour la section **URL de base sécurisée** et **URL du lien de base sécurisé** valeur à `https://german.magento24.com/`.
1. Cliquez sur **Enregistrer la configuration** et enregistrez les modifications de configuration.

### Nettoyer le cache

Exécutez la commande suivante pour nettoyer la variable `config` et `full_page` caches.

```bash
bin/magento cache:clean config full_page
```

## Vérification du site

À moins que vous n’ayez configuré le DNS pour les URL de vos magasins, vous devez ajouter un itinéraire statique à l’hôte dans votre `hosts` fichier :

1. Localisation de votre système d’exploitation `hosts` fichier .
1. Ajoutez l’itinéraire statique au format :

   ```conf
   <ip-address> french.mysite.mg
   <ip-address> german.mysite.mg
   ```

1. Accédez à l’une des URL suivantes dans votre navigateur :

   ```http
   http://mysite.mg/admin
   http://french.mysite.mg/frenchstoreview
   http://german.mysite.mg/germanstoreview
   ```

>[!INFO]
>
>- Des tâches supplémentaires peuvent être nécessaires pour déployer plusieurs sites web dans un environnement hébergé ; contactez votre fournisseur d’hébergement pour plus d’informations.
>- Des tâches supplémentaires sont nécessaires pour configurer Adobe Commerce sur l’infrastructure cloud ; see [Configuration de plusieurs sites Web ou magasins Cloud](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites.html) dans le _Guide sur l’infrastructure de Commerce on Cloud_.


### Dépannage

- Si vos sites français et allemand renvoient 404 s mais que votre administrateur charge, assurez-vous que vous avez terminé [Étape 6 : Ajouter le code de magasin à l’URL de base](ms-admin.md#step-6-add-the-store-code-to-the-base-url).
- Si toutes les URL renvoient 404, veillez à redémarrer votre serveur web.
- Si l’administrateur ne fonctionne pas correctement, assurez-vous de configurer correctement vos hôtes virtuels.
