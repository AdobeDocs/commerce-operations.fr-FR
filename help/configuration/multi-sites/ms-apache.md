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

Si nécessaire, copiez le script de point d’entrée `index.php` existant pour la vue de votre site web ou de votre magasin et ajoutez-y le script suivant :

- Vous travaillez sur une machine de développement (ordinateur portable, machine virtuelle, etc.)

  Des tâches supplémentaires peuvent être nécessaires pour déployer plusieurs sites web dans un environnement hébergé. Pour plus d’informations, contactez votre fournisseur d’hébergement.

  Des tâches supplémentaires sont requises pour configurer Adobe Commerce sur l’infrastructure cloud. Une fois les tâches décrites dans cette rubrique terminées, reportez-vous à la section [Configuration de plusieurs sites Web ou magasins](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites.html?lang=fr) du _guide sur l’infrastructure de Commerce on Cloud_.

- Vous utilisez un hôte virtuel par site web ; le fichier de configuration de l’hôte virtuel est `/etc/httpd/httpd.conf`

  Différentes versions d’Apache sur différents systèmes d’exploitation configurent différemment les hôtes virtuels. Consultez la [documentation Apache](https://httpd.apache.org/docs/2.4/vhosts) ou un administrateur réseau si vous ne savez pas comment configurer un hôte virtuel.

- Le logiciel Commerce est installé dans `/var/www/html/magento2`
- Vous avez deux sites web autres que le site par défaut :

   - `french.mysite.mg` avec le code de site web `french` et le code d’affichage de magasin `fr`
   - `german.mysite.mg` avec le code de site web `german` et le code d’affichage de magasin `de`

## Feuille de route pour la configuration de plusieurs sites web avec Apache

La configuration de plusieurs magasins comprend les tâches suivantes :

1. [Configurez les sites web, les magasins et les vues de magasin](ms-admin.md) dans l’administrateur.
1. Créez un [hôte virtuel Apache](#step-2-create-apache-virtual-hosts) par site web Commerce.

## Étape 1 : Création de sites web, magasins et magasins d’affichages dans l’administration

Voir [Configuration de plusieurs sites web, magasins et vues de magasin dans l’Admin](ms-admin.md).

## Étape 2 : création d’hôtes virtuels Apache

Cette section explique comment définir des valeurs pour `MAGE_RUN_TYPE` et `MAGE_RUN_CODE` à l’aide de la variable de serveur Apache `SetEnvIf` dans un hôte virtuel.

Pour plus d’informations sur `SetEnvIf`, voir :

- [Apache 2.2](https://httpd.apache.org/docs/2.2/mod/mod_setenvif.html)
- [Apache 2.4](https://httpd.apache.org/docs/2.4/mod/mod_setenvif.html)

**Pour créer des hôtes virtuels Apache** :

1. En tant qu’utilisateur disposant des privilèges `root`, ouvrez le fichier de configuration de l’hôte virtuel dans un éditeur de texte.

   Par exemple, ouvrez `/etc/httpd/conf/httpd.conf`.

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

À moins que vous n’ayez configuré DNS pour les URL de vos magasins, vous devez ajouter un itinéraire statique à l’hôte dans votre fichier `hosts` :

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
>- Des tâches supplémentaires sont requises pour configurer Adobe Commerce sur l’infrastructure cloud. Voir [ Configuration de plusieurs sites Web ou magasins cloud ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites.html?lang=fr) dans le _guide sur l’infrastructure de Commerce on Cloud_.

### Dépannage

- Si vos sites français et allemand renvoient 404 s mais que votre administrateur charge, veillez à avoir terminé [Étape 6 : ajoutez le code de magasin à l’URL de base](ms-admin.md#step-6-add-the-store-code-to-the-base-url).
- Si toutes les URL renvoient 404, veillez à redémarrer votre serveur web.
- Si l’administrateur ne fonctionne pas correctement, assurez-vous de configurer correctement vos hôtes virtuels.
