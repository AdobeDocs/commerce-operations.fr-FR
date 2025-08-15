---
title: Configurer et utiliser le vernis
description: Découvrez comment Varnish stocke des fichiers et améliore le trafic HTTP.
feature: Configuration, Cache
exl-id: 57614878-e349-43bb-b22b-1aa321907be1
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '1049'
ht-degree: 0%

---

# Configurer le vernis

[Varnish Cache] est un accélérateur d’applications web open source (également appelé _accélérateur HTTP_ ou _proxy inverse HTTP de mise en cache_). Varnish stocke (ou met en cache) des fichiers ou des fragments de fichiers en mémoire, ce qui permet à Varnish de réduire le temps de réponse et la consommation de bande passante du réseau pour les futures demandes équivalentes. Contrairement aux serveurs web Apache et Nginx, Varnish a été conçu pour être utilisé exclusivement avec le protocole HTTP.

[Configuration requise](../../installation/system-requirements.md) répertorie les versions prises en charge de Vernis.

>[!WARNING]
>
>Nous vous _recommandons vivement_ d&#39;utiliser le vernis en production. La mise en cache de pleine page intégrée, vers le système de fichiers ou la [base de données](https://developer.adobe.com/commerce/php/development/cache/partial/database-caching/), est beaucoup plus lente que Varnish, qui est conçu pour accélérer le trafic HTTP.

Pour plus d&#39;informations sur le vernis, voir :

- [Le Grand Vernis]
- [Options de démarrage avec vernis]
- [Vernis et performances de site web]

## Diagramme de topologie de vernis

La figure suivante présente une vue de base de Varnish dans votre topologie Commerce.

![Diagramme de vernis de base](../../assets/configuration/varnish-basic.png)

Dans la figure précédente, les requêtes HTTP des utilisateurs sur Internet entraînent de nombreuses requêtes pour les CSS, HTML, JavaScript et les images (appelées collectivement _ressources_). Varnish se trouve en face du serveur web et envoie par proxy ces requêtes au serveur web.

Lorsque le serveur web renvoie des ressources, les ressources pouvant être mises en cache sont stockées en vernis. Toutes les demandes ultérieures pour ces ressources sont traitées par Varnish (en d’autres termes, les demandes n’atteignent pas le serveur web). Le vernis renvoie le contenu mis en cache extrêmement rapidement. Vous obtiendrez ainsi des temps de réponse plus rapides pour renvoyer le contenu aux utilisateurs et utilisatrices, ainsi qu’un nombre réduit de requêtes qui doivent être satisfaites par Commerce.

Les Assets mises en cache par Vernis expirent à un intervalle configurable ou sont remplacées par de nouvelles versions des mêmes ressources. Vous pouvez également vider le cache manuellement à l’aide de la commande Admin ou [`magento cache:clean`](../cli/manage-cache.md#clean-and-flush-cache-types) .

## Présentation du processus

Cette rubrique explique comment installer initialement Varnish avec un jeu minimal de paramètres et tester son fonctionnement. Ensuite, exportez une configuration de vernis à partir de l’administration Commerce et testez-la à nouveau.

Le processus peut être résumé comme suit :

1. Installez le vernis et testez-le en accédant à n’importe quelle page Commerce pour voir si vous obtenez des en-têtes de réponse HTTP indiquant que le vernis fonctionne.
1. Installez le logiciel Commerce et utilisez l&#39;Admin pour créer un fichier de configuration Varnish.
1. Remplacez votre fichier de configuration de vernis existant par celui généré par l&#39;administrateur.
1. Testez à nouveau tout.

   S&#39;il n&#39;y a rien dans votre répertoire `<magento_root>/var/page_cache`, vous avez correctement configuré Varnish avec Commerce !

>[!NOTE]
>
>- Sauf indication contraire, vous devez saisir toutes les commandes décrites dans cette rubrique en tant qu’utilisateur disposant de droits d’`root`.
>
>- Cette rubrique a été écrite pour Varnish sur CentOS et Apache 2.4. Si vous configurez le vernis dans un environnement différent, certaines commandes peuvent être différentes. Consultez la documentation de Varnish pour plus d’informations.

## Problèmes connus

Nous connaissons les problèmes suivants avec le vernis :

- [Le vernis ne prend pas en charge SSL]

  Vous pouvez également utiliser la terminaison SSL ou un proxy de terminaison SSL.

- Si vous supprimez manuellement le contenu du répertoire `<magento_root>/var/cache`, vous devez redémarrer Varnish.

- Erreur possible lors de l’installation de Commerce :

  ```
  Error 503 Service Unavailable
  Service Unavailable
  XID: 303394517
  Varnish cache server
  ```

  Si vous rencontrez cette erreur, modifiez les `default.vcl` et ajoutez un délai d’expiration à la stature `backend` comme suit :

  ```conf
  backend default {
      .host = "127.0.0.1";
      .port = "8080";
      .first_byte_timeout = 600s;
  }
  ```

## Présentation de la mise en cache du vernis

La mise en cache des vernis fonctionne avec Commerce à l’aide des éléments suivants :

- [`nginx.conf.sample`](https://github.com/magento/magento2/blob/2.4/nginx.conf.sample) du référentiel GitHub de Magento 2
- `.htaccess` fichier de configuration distribué pour Apache fourni avec Commerce
- Configuration `default.vcl` pour le vernis générée à l’aide de l’[Admin](../cache/configure-varnish-commerce.md)

>[!INFO]
>
>Cette rubrique ne couvre que les options par défaut de la liste précédente. Il existe de nombreuses autres façons de configurer la mise en cache dans des scénarios complexes (par exemple, à l’aide d’un réseau de diffusion de contenu) ; ces méthodes ne font pas partie de ce guide.

Lors de la première requête du navigateur, les ressources pouvant être mises en cache sont diffusées au navigateur client à partir de Varnish et mises en cache dans le navigateur.

En outre, Varnish utilise une balise d’entité (ETag) pour les ressources statiques. L’ETag permet de déterminer à quel moment les fichiers statiques changent sur le serveur. Par conséquent, les ressources statiques sont envoyées au client lorsqu’elles sont modifiées sur le serveur, soit lors d’une nouvelle demande d’un navigateur, soit lorsque le client actualise le cache du navigateur, généralement en appuyant sur F5 ou Contrôle+F5.

Vous trouverez plus de détails dans les sections suivantes.

## Mise en cache par requête de navigateur

Cette section utilise un inspecteur de navigateur pour afficher la manière dont les ressources sont diffusées au navigateur dans la première requête, puis chargées à partir du cache du navigateur local.

### Première requête de navigateur

`nginx.conf.sample` et `.htaccess` fournissent des options de mise en cache du client. Lorsque la première requête est effectuée à partir d’un navigateur pour un objet pouvant être mis en cache, Varnish la diffuse au client.

La figure suivante illustre un exemple d’utilisation d’un inspecteur de navigateur :

![La première fois qu’une demande est envoyée pour un objet pouvant être mis en cache, Varnish la transmet au navigateur](../../assets/configuration/varnish-apache-first-visit.png)

L’exemple précédent illustre une requête pour la page principale de storefront (`m2_ce_my`). Les ressources CSS et JavaScript sont mises en cache dans le navigateur client.

>[!NOTE]
>
>La plupart des ressources statiques comportent un code d’état HTTP 200 (OK), indiquant que la ressource a été récupérée à partir du serveur.

### Deuxième requête de navigateur

Si le même navigateur demande à nouveau la même page, ces ressources sont diffusées à partir du cache du navigateur local, comme le montre la figure suivante.

![La prochaine fois que le même objet est demandé, les ressources se chargent à partir du cache du navigateur local](../../assets/configuration/varnish-apache-second-visit.png)

Notez la différence de temps de réponse entre la première et la seconde requête. Là encore, les ressources statiques ont un code de réponse 200 (OK), car elles sont diffusées à partir du cache local pour la première fois.

## Utilisation d’Etag par Commerce

L’exemple suivant illustre les en-têtes de réponse pour une ressource statique spécifique.

![L’ETag permet de déterminer plus facilement si une ressource statique a changé ou non](../../assets/configuration/varnish-etag.png)

`calendar.css` comporte un en-tête de réponse ETag, ce qui signifie que le fichier CSS du navigateur client peut être comparé à celui du serveur.

En outre, les ressources statiques sont renvoyées avec un code d’état HTTP 304 (Non modifié), comme le montre la figure suivante.

![Le code de réponse HTTP 304 (Non modifié) indique que la ressource statique dans le cache local est la même que sur le serveur](../../assets/configuration/varnish-304.png)

Le code d’état 304 se produit, car l’utilisateur a invalidé son cache local et le contenu sur le serveur n’a pas été modifié. En raison du code d’état 304, la ressource statique _content_ n’est pas transférée ; seuls les en-têtes HTTP sont téléchargés sur le navigateur.

Si le contenu change sur le serveur, le client télécharge la ressource statique avec un code d’état HTTP 200 (OK) et un nouvel ETag.

<!-- Link Definitions -->

[Le Grand Tableau Verni]: https://www.varnish-cache.org/docs/trunk/users-guide/intro.html
[Cache de vernis]: https://varnish-cache.org
[Options de démarrage du vernis]: https://www.varnish-cache.org/docs/trunk/reference/varnishd.html#ref-varnishd-options
[Vernis et performances de site web]: https://www.varnish-cache.org/docs/trunk/users-guide/performance.html#users-performance
[Le vernis ne prend pas en charge SSL]: https://www.varnish-cache.org/docs/3.0/phk/ssl.html
