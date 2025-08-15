---
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '318'
ht-degree: 0%

---
# Communication sécurisée avec le serveur web

Cette rubrique présente un exemple de sécurisation de la communication entre votre serveur web et votre moteur de recherche (Elasticsearch ou OpenSearch) à l’aide d’une combinaison du chiffrement TLS (Transport Layer Security) et de l’[authentification de base HTTP](https://datatracker.ietf.org/doc/html/rfc2617). Vous pouvez également configurer d’autres types d’authentification ; nous fournissons des références pour ces informations.

(Un terme plus ancien, Secure Sockets Layer (SSL), est souvent utilisé de manière interchangeable avec TLS. Dans cette rubrique, nous nous référons à *TLS*.)

>[!WARNING]
>
>Sauf indication contraire, toutes les commandes de cette rubrique doivent être saisies en tant qu’utilisateur disposant de droits d’`root`.

## Recommendations

Nous recommandons ce qui suit :

* Votre serveur web utilise TLS.

  TLS dépasse le cadre de cette rubrique. Cependant, nous vous recommandons vivement d’utiliser un certificat réel en production et non un certificat auto-signé.

* Votre moteur de recherche s’exécute sur le même hôte qu’un serveur web. L’exécution du moteur de recherche et du serveur web sur différents hôtes dépasse le cadre de cette rubrique.

  L’avantage de placer le moteur de recherche et le serveur web sur le même hôte est qu’il rend impossible l’interception de la communication chiffrée. Le serveur web du moteur de recherche ne doit pas nécessairement être identique au serveur web d’Adobe Commerce. Par exemple, Adobe Commerce peut exécuter Apache et Elasticsearch/OpenSearch peut exécuter nginx.

  Si le moteur de recherche est exposé au Web public, vous devez configurer l’authentification. Si votre instance de moteur de recherche est protégée au sein de votre réseau, cela peut ne pas être nécessaire. Contactez votre fournisseur d’hébergement pour déterminer les mesures de sécurité à mettre en œuvre pour protéger votre instance.

## Plus d’informations sur TLS

Consultez l’une des ressources suivantes :

* Apache

   * [Tutoriel sur le chiffrement fort Apache 2.4](https://httpd.apache.org/docs/2.4/ssl/ssl_howto.html)
   * [Comment créer un certificat SSL sur Apache pour Ubuntu 14.04 (tutoriel Digitalocean)](https://www.digitalocean.com/community/tutorials/how-to-create-a-ssl-certificate-on-apache-for-ubuntu-14-04)
   * [Configuration d’un serveur web sécurisé SSL avec CentOS (wiki CentOS)](https://wiki.centos.org/HowTos/Https)

* Nginx

   * [Terminaison SSL Nginx](https://www.nginx.com/resources/admin-guide/nginx-ssl-termination/)
   * [Comment créer un certificat SSL sur Nginx pour Ubuntu 14.04 (tutoriel Digitalocean)](https://www.digitalocean.com/community/tutorials/how-to-create-an-ssl-certificate-on-nginx-for-ubuntu-14-04)
   * [Installation du certificat SSL Nginx (digicert)](https://www.digicert.com/ssl-certificate-installation-nginx.htm)
