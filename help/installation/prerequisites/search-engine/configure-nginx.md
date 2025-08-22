---
title: Configuration de Nginx pour votre moteur de recherche
description: Pour configurer un moteur de recherche avec le serveur web Nginx pour les installations sur site d’Adobe Commerce, procédez comme suit.
feature: Install, Search
exl-id: 8d2f8695-e30a-4acc-bba3-d122212b0a53
source-git-commit: 55512521254c49511100a557a4b00cf3ebee0311
workflow-type: tm+mt
source-wordcount: '603'
ht-degree: 0%

---

# Configuration de Nginx pour votre moteur de recherche

{{$include /help/_includes/web-server-communication.md}}

## Configuration d’un proxy

>[!NOTE]
>
>Ajout de la prise en charge d’OpenSearch dans la version 2.4.4. OpenSearch est un formulaire compatible d’Elasticsearch. Voir [Migration d’Elasticsearch vers OpenSearch](../../../upgrade/prepare/opensearch-migration.md) pour plus d’informations.

Cette section explique comment configurer nginx en tant que proxy *non sécurisé* afin qu’Adobe Commerce puisse utiliser un moteur de recherche s’exécutant sur ce serveur. Cette section ne traite pas de la configuration de l’authentification HTTP de base, qui est traitée dans la section [Communication sécurisée avec nginx](#secure-communication-with-nginx).

>[!NOTE]
>
>La raison pour laquelle le proxy n’est pas sécurisé dans cet exemple est qu’il est plus facile à configurer et à vérifier. Vous pouvez utiliser TLS avec ce proxy si vous le souhaitez ; pour ce faire, veillez à ajouter les informations de proxy à la configuration de votre bloc de serveur sécurisé.

### Spécifiez des fichiers de configuration supplémentaires dans votre configuration globale

Assurez-vous que votre `/etc/nginx/nginx.conf` globale contient la ligne suivante afin de charger les autres fichiers de configuration décrits dans les sections suivantes :

```conf
include /etc/nginx/conf.d/*.conf;
```

### Configuration de Nginx en tant que proxy

Cette section explique comment spécifier qui peut accéder au serveur Nginx.

1. Utilisez un éditeur de texte pour créer un `/etc/nginx/conf.d/magento_es_auth.conf` de fichier avec le contenu suivant :

   ```conf
   server {
      listen 8080;
      location /_cluster/health {
         proxy_pass http://localhost:9200/_cluster/health;
      }
   }
   ```

1. Redémarrez Angles :

   ```bash
   service nginx restart
   ```

1. Vérifiez que le proxy fonctionne en saisissant la commande suivante :

   ```bash
   curl -i http://localhost:<proxy port>/_cluster/health
   ```

   Par exemple, si votre proxy utilise le port 8080 :

   ```bash
   curl -i http://localhost:8080/_cluster/health
   ```

   Des messages similaires à ce qui suit s’affichent pour indiquer la réussite :

   ```
   HTTP/1.1 200 OK
   Date: Tue, 23 Feb 2019 20:38:03 GMT
   Content-Type: application/json; charset=UTF-8
   Content-Length: 389
   Connection: keep-alive
   
   {"cluster_name":"elasticsearch","status":"yellow","timed_out":false,"number_of_nodes":1,"number_of_data_nodes":1,"active_primary_shards":5,"active_shards":5,"relocating_shards":0,"initializing_shards":0,"unassigned_shards":5,"delayed_unassigned_shards":0,"number_of_pending_tasks":0,"number_of_in_flight_fetch":0,"task_max_waiting_in_queue_millis":0,"active_shards_percent_as_number":50.0}
   ```

## Communication sécurisée avec Nginx

Cette section explique comment configurer l’[authentification HTTP de base](https://nginx.org/en/docs/http/ngx_http_auth_basic_module.html) avec votre proxy sécurisé. L’utilisation conjointe de l’authentification TLS et HTTP de base empêche quiconque d’intercepter la communication avec Elasticsearch ou OpenSearch ou avec votre serveur d’applications.

Comme nginx prend en charge l’authentification HTTP de base en mode natif, nous vous recommandons de le remplacer, par exemple, par l’authentification [Digest](https://www.nginx.com/resources/wiki/modules/auth_digest/), qui n’est pas recommandée en production.

Ressources supplémentaires :

* [Comment configurer l’authentification par mot de passe avec Nginx sur Ubuntu 14.04 (Digital Ocean)](https://www.digitalocean.com/community/tutorials/how-to-set-up-password-authentication-with-nginx-on-ubuntu-14-04)
* [Authentification HTTP de base avec Nginx (HowtoForge)](https://www.howtoforge.com/basic-http-authentication-with-nginx)
* [Exemples de configurations Nginx pour Elasticsearch](https://gist.github.com/karmi/b0a9b4c111ed3023a52d)

Pour plus d’informations, consultez les sections suivantes :

* [Créer des mots de passe](#create-a-password)
* [Configurer l’accès à Nginx](#set-up-access-to-nginx)
* [Configurer un contexte restreint pour le moteur de recherche](#set-up-a-restricted-context-for-the-search-engine)
* [Vérifier que la communication est sécurisée](#secure-communication-with-nginx)

### Création d’un mot de passe

Nous vous recommandons d’utiliser la commande Apache `htpasswd` pour coder les mots de passe d’un utilisateur ayant accès à Elasticsearch ou OpenSearch (nommé `magento_elasticsearch` dans cet exemple).

Pour créer un mot de passe :

1. Saisissez la commande suivante pour déterminer si `htpasswd` est déjà installé :

   ```bash
   which htpasswd
   ```

   Si un chemin s’affiche, il est installé ; si la commande ne renvoie aucune sortie, `htpasswd` n’est pas installé.

1. Au besoin, installez `htpasswd` :

   * Ubuntu : `apt-get -y install apache2-utils`
   * CentOS : `yum -y install httpd-tools`

1. Créez un répertoire `/etc/nginx/passwd` pour stocker les mots de passe :

   ```bash
   mkdir -p /etc/nginx/passwd
   ```

   ```bash
   htpasswd -c /etc/nginx/passwd/.<filename> <username>
   ```

   >[!WARNING]
   >
   >Pour des raisons de sécurité, `<filename>` doit être masqué ; en d’autres termes, il doit commencer par un point.

1. *(facultatif).* Pour ajouter un autre utilisateur à votre fichier de mots de passe, saisissez la même commande sans l&#39;option `-c` (créer) :

   ```bash
   htpasswd /etc/nginx/passwd/.<filename> <username>
   ```

1. Vérifiez que le contenu de `/etc/nginx/passwd` est correct.

### Configurer l’accès à Nginx

Cette section explique comment spécifier qui peut accéder au serveur Nginx.

>[!WARNING]
>
>L’exemple illustré concerne un proxy *non sécurisé*. Pour utiliser un proxy sécurisé, ajoutez le contenu suivant (à l’exception du port d’écoute) à votre bloc de serveur sécurisé.

Utilisez un éditeur de texte pour modifier `/etc/nginx/conf.d/magento_es_auth.conf` (non sécurisé) ou votre bloc de serveur sécurisé avec le contenu suivant :

```conf
server {
  listen 8080;
  server_name 127.0.0.1;

  location / {
   limit_except HEAD {
      auth_basic "Restricted";
      auth_basic_user_file  /etc/nginx/passwd/.htpasswd_magento_elasticsearch;
   }
   proxy_pass http://127.0.0.1:9200;
   proxy_redirect off;
   proxy_set_header Host $host;
   proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
  }

  location /_aliases {
   auth_basic "Restricted";
   auth_basic_user_file  /etc/nginx/passwd/.htpasswd_magento_elasticsearch;
   proxy_pass http://127.0.0.1:9200;
   proxy_redirect off;
   proxy_set_header Host $host;
   proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
  }

  include /etc/nginx/auth/*.conf;
}
```

>[!NOTE]
>
>Le port d’écoute du moteur de recherche illustré dans l’exemple précédent sont uniquement des exemples. Pour des raisons de sécurité, nous vous recommandons d’utiliser un port d’écoute autre que celui par défaut.

### Configurer un contexte restreint pour le moteur de recherche

Cette section explique comment spécifier qui peut accéder au serveur du moteur de recherche.

1. Saisissez la commande suivante afin de créer un répertoire pour stocker la configuration d’authentification :

   ```bash
   mkdir /etc/nginx/auth/
   ```

1. Utilisez un éditeur de texte pour créer un `/etc/nginx/auth/magento_elasticsearch.conf` de fichier avec le contenu suivant :

   ```conf
   location /elasticsearch {
   auth_basic "Restricted - elasticsearch";
   auth_basic_user_file /etc/nginx/passwd/.htpasswd_magento_elasticsearch;
   
   proxy_pass http://127.0.0.1:9200;
   proxy_redirect off;
   proxy_set_header Host $host;
   proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
   }
   ```

1. Si vous configurez un proxy sécurisé, supprimez `/etc/nginx/conf.d/magento_es_auth.conf`.
1. Redémarrez Nginx et passez à la section suivante :

   ```bash
   service nginx restart
   ```

#### Vérifier

{{$include /help/_includes/verify-secure-communication.md}}

<!-- Last updated from includes: 2024-07-18 15:50:54 -->
