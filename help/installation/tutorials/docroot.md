---
title: Modification de docroot pour améliorer la sécurité
description: Empêchez les navigateurs non autorisés d’accéder à Adobe Commerce ou au système de fichiers Magento Open Source sur site.
feature: Install, Security
exl-id: aabe148d-00c8-4011-a629-aa5abfa6c682
source-git-commit: 32dd5005422b98923ce1bdf6c3fb3f55c2ec15bd
workflow-type: tm+mt
source-wordcount: '586'
ht-degree: 0%

---

# Modification de docroot pour améliorer la sécurité

Dans une installation standard avec un serveur web Apache, Adobe Commerce et Magento Open Source sont installés à la racine web par défaut : `/var/www/html/magento2`.

La variable `magento2/` contient les éléments suivants :

- `pub/`
- `setup/`
- `var/`

L’application est diffusée à partir de `/var/www/html/magento2/pub`. Le reste du système de fichiers est vulnérable, car il est accessible à partir d’un navigateur.
Définir la zone de webroot sur la valeur `pub/` empêche les visiteurs du site d’accéder à des zones sensibles du système de fichiers à partir d’un navigateur.

Cette rubrique décrit comment modifier le docroot Apache sur une instance existante pour diffuser des fichiers à partir de la fonction `pub/` , qui est plus sécurisé.

## Remarque concernant nginx

Si vous utilisez [nginx](../prerequisites/web-server/nginx.md) et la variable [`nginx.conf.sample`](https://github.com/magento/magento2/blob/2.4/nginx.conf.sample) fichier inclus dans le répertoire d’installation, vous diffusez probablement déjà des fichiers du répertoire `pub/` répertoire .

Lorsqu’elle est utilisée dans le bloc de votre serveur qui définit votre site, la variable `nginx.conf.sample` la configuration remplace les paramètres docroot de votre serveur pour diffuser des fichiers à partir de la fonction `pub/` répertoire . Voir par exemple la dernière ligne dans la configuration suivante :

```conf
# /etc/nginx/sites-available/magento

upstream fastcgi_backend {
   server  unix:/run/php/php7.4-fpm.sock;
}

server {

         listen 80;
         server_name 192.168.33.10;
         set $MAGE_ROOT /var/www/html/magento2ce;
         include /var/www/html/magento2ce/nginx.conf.sample;
}
```

## Avant de commencer

Pour terminer ce tutoriel, vous devez accéder à une installation opérationnelle s’exécutant sur une pile LAMP :

- Linux
- Apache (2.4+)
- MySQL (5.7+)
- PHP (7.4)
- Elasticsearch (7.x) ou OpenSearch (1.2)
- Adobe Commerce ou Magento Open Source (2.4+)

>[!NOTE]
>
>Voir [Conditions préalables](../prerequisites/overview.md) et la variable [Guide d’installation](../overview.md) pour plus d’informations.

## 1. Modifiez la configuration de votre serveur

Le nom et l’emplacement de votre fichier d’hôte virtuel dépendent de la version d’Apache que vous exécutez. Cet exemple illustre le nom et l’emplacement du fichier d’hôte virtuel sur Apache v2.4.

1. Connectez-vous à votre serveur d’applications.
1. Modifiez votre fichier d’hôte virtuel :

   ```bash
   vim /etc/apache2/sites-available/000-default.conf
   ```

1. Ajoutez le chemin d’accès à votre `pub/` vers le répertoire `DocumentRoot` directive :

   ```conf
   <VirtualHost *:80>
   
            ServerAdmin webmaster@localhost
            DocumentRoot /var/www/html/magento2ce/pub
   
            ErrorLog ${APACHE_LOG_DIR}/error.log
            CustomLog ${APACHE_LOG_DIR}/access.log combined
   
            <Directory "/var/www/html">
                        AllowOverride all
            </Directory>
    </VirtualHost>
   ```

1. Redémarrez Apache :

   ```bash
   systemctl restart apache2
   ```

## 2. Mettre à jour l’URL de base

Si vous avez ajouté un nom de répertoire au nom d’hôte ou à l’adresse IP de votre serveur pour créer l’URL de base lors de l’installation de l’application (par exemple : `http://192.168.33.10/magento2`), vous devez le supprimer.

>[!NOTE]
>
>Remplacer `192.168.33.10` avec le nom d’hôte de votre serveur.

1. Connectez-vous à la base de données :

   ```bash
   mysql -u <user> -p
   ```

1. Indiquez la base de données que vous avez créée lors de l&#39;installation de l&#39;application :

   ```shell
   use <database-name>
   ```

1. Mettez à jour l’URL de base :

   ```shell
   UPDATE core_config_data SET value='http://192.168.33.10' WHERE path='web/unsecure/base_url';
   ```

## 3. Mettre à jour le fichier env.php

Ajoutez le noeud suivant au noeud `env.php` fichier .

```conf
'directories' => [
    'document_root_is_pub' => true
]
```

Voir [référence env.php](../../configuration/reference/config-reference-envphp.md) pour plus d’informations.

## 4. Changement de mode

[Modes d’application](../../configuration/bootstrap/application-modes.md), qui inclut `production` et `developer`, sont conçus pour améliorer la sécurité et faciliter le développement. Comme les noms le suggèrent, vous devez passer à `developer` lors de l’extension ou de la personnalisation de l’application et passez à `production` lors de l’exécution dans un environnement en ligne.

Le basculement entre les modes est une étape importante pour vérifier que la configuration de votre serveur fonctionne correctement. Vous pouvez basculer entre les modes à l’aide de l’outil d’interface en ligne de commande :

1. Accédez au répertoire d’installation.
1. Basculer vers `production` mode .

   ```bash
   bin/magento deploy:mode:set production
   ```

   ```bash
   bin/magento cache:flush
   ```

1. Actualisez votre navigateur et vérifiez que le storefront s’affiche correctement.
1. Basculer vers `developer` mode .

   ```bash
   bin/magento deploy:mode:set developer
   ```

   ```bash
   bin/magento cache:flush
   ```

1. Actualisez votre navigateur et vérifiez que le storefront s’affiche correctement.

## 5. Vérification du storefront

Accédez au storefront dans un navigateur web pour vérifier que tout fonctionne.

1. Ouvrez un navigateur web et saisissez le nom d’hôte ou l’adresse IP de votre serveur dans la barre d’adresse. Par exemple, `http://192.168.33.10`.

   La figure suivante présente un exemple de page de storefront. S’il s’affiche comme suit, votre installation a réussi !

   ![Storefront qui vérifie une installation réussie](../../assets/installation/install-success_store.png)

   Voir [section de dépannage](https://support.magento.com/hc/en-us/articles/360032994352) si la page affiche une valeur 404 (Introuvable) ou si elle ne parvient pas à charger d’autres ressources telles que des images, des fichiers CSS et des fichiers JS.

1. Essayez d’accéder à un répertoire d’application à partir d’un navigateur. Ajoutez le nom du répertoire au nom d’hôte ou à l’adresse IP de votre serveur dans la barre d’adresse :

   Si vous voyez un message 404 ou &quot;Accès refusé&quot;, vous avez réussi à restreindre l’accès au système de fichiers.

   ![Accès refusé](../../assets/installation/access-denied.png)
