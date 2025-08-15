---
title: Configuration de plusieurs sites web avec Apache
description: Suivez ce tutoriel pour configurer plusieurs sites web avec Apache.
exl-id: 4c6890b3-f15a-46f2-a3e8-6f2a9b57a6ad
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '485'
ht-degree: 0%

---

# Configuration de plusieurs sites web avec Apache

Nous supposons que :

Si nécessaire, copiez le script du point d’entrée `index.php` existant pour l’affichage de votre site web ou de votre boutique et ajoutez-y les éléments suivants :

- Vous travaillez sur une machine de développement (ordinateur portable, machine virtuelle, etc.)

  Des tâches supplémentaires peuvent être nécessaires pour déployer plusieurs sites web dans un environnement hébergé. Pour plus d’informations, contactez votre fournisseur d’hébergement.

  Des tâches supplémentaires sont nécessaires pour configurer Adobe Commerce sur l’infrastructure cloud. Une fois les tâches décrites dans cette rubrique terminées, consultez [Configuration de plusieurs sites web ou magasins](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites.html?lang=fr) dans le guide _Commerce sur les infrastructures cloud_.

- Vous utilisez un hôte virtuel par site Web ; le fichier de configuration de l&#39;hôte virtuel est `/etc/httpd/httpd.conf`

  Différentes versions d’Apache sur différents systèmes d’exploitation configurent les hôtes virtuels différemment. Consultez la [documentation Apache](https://httpd.apache.org/docs/2.4/vhosts) ou contactez un administrateur réseau si vous n’êtes pas sûr de la manière de configurer un hôte virtuel.

- Le logiciel Commerce est installé dans `/var/www/html/magento2`
- Vous disposez de deux sites web autres que le site par défaut :

   - `french.mysite.mg` avec le code du site web `french` et le code d’affichage du magasin `fr`
   - `german.mysite.mg` avec le code du site web `german` et le code d’affichage du magasin `de`

## Feuille de route pour la configuration de plusieurs sites web avec Apache

La configuration de plusieurs magasins se compose des tâches suivantes :

1. [Configurez des sites web, des boutiques et des affichages de boutique](ms-admin.md) dans l’Administration.
1. Créez un [hôte virtuel Apache](#step-2-create-apache-virtual-hosts) par site web Commerce.

## Étape 1 : créer des sites web, des boutiques et des vues de boutique dans l’Administration

Voir [Configuration de plusieurs sites web, boutiques et vues de boutique dans l’Administration](ms-admin.md).

## Étape 2 : créer des hôtes virtuels Apache

Cette section explique comment définir des valeurs pour `MAGE_RUN_TYPE` et `MAGE_RUN_CODE` à l’aide de la variable de serveur Apache `SetEnvIf` dans un hôte virtuel.

Pour plus d’informations sur `SetEnvIf`, voir :

- [Apache 2.2](https://httpd.apache.org/docs/2.2/mod/mod_setenvif.html)
- [Apache 2.4](https://httpd.apache.org/docs/2.4/mod/mod_setenvif.html)

**Pour créer des hôtes virtuels Apache** :

1. En tant qu’utilisateur disposant de privilèges `root`, ouvrez le fichier de configuration de l’hôte virtuel dans un éditeur de texte.

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

## Vérification de votre site

À moins que le DNS n’ait été configuré pour les URL de vos magasins, vous devez ajouter un itinéraire statique vers l’hôte dans votre fichier `hosts` :

1. Recherchez le fichier `hosts` de votre système d’exploitation.
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
>- Des tâches supplémentaires peuvent être nécessaires pour déployer plusieurs sites web dans un environnement hébergé. Pour plus d’informations, contactez votre fournisseur d’hébergement.
>- Des tâches supplémentaires sont nécessaires pour configurer Adobe Commerce sur l’infrastructure cloud. Voir [Configuration de plusieurs sites web ou magasins cloud](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites.html?lang=fr) dans le guide _Commerce sur l’infrastructure cloud_.

### Dépannage

- Si vos sites français et allemands renvoient 404 mais que votre administrateur charge, veillez à terminer [Étape 6 : ajouter le code de magasin à l’URL de base](ms-admin.md#step-6-add-the-store-code-to-the-base-url).
- Si toutes les URL renvoient des URL 404, veillez à redémarrer votre serveur web.
- Si l’administrateur ne fonctionne pas correctement, assurez-vous de configurer correctement vos hôtes virtuels.
