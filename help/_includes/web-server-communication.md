---
source-git-commit: 475dbc056ac3e6a00c8f794259bb0fbf04143687
workflow-type: tm+mt
source-wordcount: '345'
ht-degree: 0%

---
# Communication avec le serveur web sécurisé

Cette rubrique présente un exemple de sécurisation des communications entre votre serveur web et votre moteur de recherche (Elasticsearch ou OpenSearch) à l’aide d’une combinaison de chiffrement TLS (Transport Layer Security) et de [Authentification de base HTTP](https://datatracker.ietf.org/doc/html/rfc2617). Vous pouvez également configurer d’autres types d’authentification. Nous fournissons des références pour ces informations.

(Un terme plus ancien, SSL (Secure Sockets Layer), est fréquemment utilisé de manière interchangeable avec TLS. Dans cette rubrique, nous nous réfélicitions *TLS*.)

>[!WARNING]
>
>Sauf indication contraire, toutes les commandes de cette rubrique doivent être saisies en tant qu’utilisateur avec `root` des privilèges.

## Recommendations

Nous vous recommandons ce qui suit :

* Votre serveur web utilise TLS.

  TLS dépasse le cadre de cette rubrique ; toutefois, nous vous recommandons vivement d’utiliser un certificat réel en production et non un certificat auto-signé.

* Votre moteur de recherche s’exécute sur le même hôte qu’un serveur web. L’exécution du moteur de recherche et du serveur web sur différents hôtes dépasse le cadre de cette rubrique.

  L’avantage de placer le moteur de recherche et le serveur web sur le même hôte est qu’il rend impossible l’interception de communications cryptées. Il n’est pas nécessaire que le serveur web du moteur de recherche soit le même que le serveur web Adobe Commerce ou le serveur Magento Open Source ; par exemple, Adobe Commerce peut exécuter Apache et Elasticsearch/OpenSearch peut exécuter nginx.

  Si le moteur de recherche est exposé au Web public, vous devez configurer l’authentification. Si votre instance de moteur de recherche est protégée sur votre réseau, cela peut ne pas être nécessaire. Collaborez avec votre fournisseur d’hébergement pour déterminer les mesures de sécurité à implémenter pour protéger votre instance.

## Plus d’informations sur TLS

Consultez l’une des ressources suivantes :

* Apache

   * [Méthode de chiffrement fort Apache 2.4](https://httpd.apache.org/docs/2.4/ssl/ssl_howto.html)
   * [Comment créer un certificat SSL sur Apache pour Ubuntu 14.04 (tutoriel Digitalsea)](https://www.digitalocean.com/community/tutorials/how-to-create-a-ssl-certificate-on-apache-for-ubuntu-14-04)
   * [Configuration d’un serveur Web sécurisé SSL avec CentOS (wiki CentOS)](https://wiki.centos.org/HowTos/Https)

* Nginx

   * [Terminaison SSL de Nginx](https://www.nginx.com/resources/admin-guide/nginx-ssl-termination/)
   * [Comment créer un certificat SSL sur Nginx pour Ubuntu 14.04 (tutoriel Digitalsea)](https://www.digitalocean.com/community/tutorials/how-to-create-an-ssl-certificate-on-nginx-for-ubuntu-14-04)
   * [Installation du certificat SSL de Nginx (digicert)](https://www.digicert.com/ssl-certificate-installation-nginx.htm)
