---
title: Configuration de plusieurs sites web avec Apache
description: Suivez ce tutoriel pour configurer plusieurs sites web avec Apache.
source-git-commit: 8102c083bb0216bbdcad2882f39f7711b9cee52b
workflow-type: tm+mt
source-wordcount: '508'
ht-degree: 0%

---


# Configuration de plusieurs sites web avec Apache

Nous supposons que :

Si nécessaire, copiez le fichier `index.php` script de point d’entrée pour votre site web ou [vue de magasin](https://glossary.magento.com/store-view) et ajoutez-y les éléments suivants :

- Vous travaillez sur une machine de développement (ordinateur portable, machine virtuelle, etc.)

   Des tâches supplémentaires peuvent être nécessaires pour déployer plusieurs sites web dans un environnement hébergé ; contactez votre fournisseur d’hébergement pour plus d’informations.

   Des tâches supplémentaires sont requises pour configurer Adobe Commerce sur l’infrastructure cloud. Une fois les tâches abordées dans cette rubrique terminées, reportez-vous à la section [Configuration de plusieurs sites web ou magasins](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites.html) dans le _Guide sur l’infrastructure de Commerce on Cloud_.

- Vous utilisez un hôte virtuel par site web ; le fichier de configuration de l’hôte virtuel est `/etc/httpd/httpd.conf`

   Différentes versions d’Apache sur différents systèmes d’exploitation configurent différemment les hôtes virtuels. Consultez la [Documentation Apache](https://httpd.apache.org/docs/2.4/vhosts) ou un administrateur réseau si vous ne savez pas comment configurer un hôte virtuel.

- Le logiciel Commerce est installé dans `/var/www/html/magento2`
- Vous avez deux sites web autres que le site par défaut :

   - `french.mysite.mg` avec code du site web `french` et stocker le code d’affichage `fr`
   - `german.mysite.mg` avec code du site web `german` et stocker le code d’affichage `de`

## Feuille de route pour la configuration de plusieurs sites web avec Apache

La configuration de plusieurs magasins comprend les tâches suivantes :

1. [Configuration des sites web, des magasins et des vues de magasin](ms-admin.md) dans Admin.
1. En créer un [Hôte virtuel Apache](#step-2-create-apache-virtual-hosts) par site web Commerce.

## Étape 1 : Créer des sites web, des magasins et des vues de magasin dans l’administrateur

Voir [Configuration de plusieurs sites web, magasins et vues de magasin dans l’administrateur](ms-admin.md).

## Étape 2 : Création d’hôtes virtuels Apache

Cette section explique comment définir des valeurs pour `MAGE_RUN_TYPE` et `MAGE_RUN_CODE` utilisation de la variable de serveur Apache `SetEnvIf` dans un hôte virtuel.

Pour plus d’informations sur `SetEnvIf`, voir :

- [Apache 2.2](https://httpd.apache.org/docs/2.2/mod/mod_setenvif.html)
- [Apache 2.4](https://httpd.apache.org/docs/2.4/mod/mod_setenvif.html)

**Pour créer des hôtes virtuels Apache**:

1. En tant qu’utilisateur avec `root` , ouvrez le fichier de configuration de l’hôte virtuel dans un éditeur de texte.

   Par exemple, ouvrez `/etc/httpd/conf/httpd.conf`

1. Recherchez la section commençant par `<VirtualHost *:80>`.
1. Créez les hôtes virtuels suivants après tout hôte virtuel existant :

   ```conf
   <VirtualHost *:80>
      ServerName          mysite.mg
      DocumentRoot        /var/www/html/magento2/pub/
   </VirtualHost>
   
   <VirtualHost *:80>
      ServerName          french.mysite.mg
      DocumentRoot        /var/www/html/magento2/pub/
      SetEnv MAGE_RUN_CODE "french"
      SetEnv MAGE_RUN_TYPE "website"
   </VirtualHost>
   
   <VirtualHost *:80>
      ServerName          german.mysite.mg
      DocumentRoot        /var/www/html/magento2/pub/
      SetEnv MAGE_RUN_CODE "german"
      SetEnv MAGE_RUN_TYPE "website"
   </VirtualHost>
   ```

1. Enregistrez vos modifications dans `httpd.conf` et quittez l’éditeur de texte.
1. Redémarrez Apache :

   - CentOS : `service httpd restart`
   - Ubuntu : `service apache2 restart`

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
