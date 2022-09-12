---
title: Configuration de Nginx pour votre moteur de recherche
description: Pour configurer un moteur de recherche avec le serveur web Nginx pour les installations sur site d’Adobe Commerce et de Magento Open Source, procédez comme suit.
source-git-commit: a0f2c6480edcda5540ca83835580d18f401de72f
workflow-type: tm+mt
source-wordcount: '652'
ht-degree: 0%

---


# Configuration de Nginx pour votre moteur de recherche

{{$include /help/_includes/web-server-communication.md}}

## Configuration d’un proxy

>[!NOTE]
>
>La prise en charge d’OpenSearch a été ajoutée dans la version 2.4.4. OpenSearch est un double compatible avec les Elasticsearch. Toutes les instructions pour configurer Elasticsearch 7 s’appliquent à OpenSearch. Voir [Migration de l’Elasticsearch vers OpenSearch](../../../upgrade/prepare/opensearch-migration.md) pour plus d’informations.

Cette section explique comment configurer nginx en tant que *unsecure* pour qu’Adobe Commerce ou Magento Open Source puisse utiliser un moteur de recherche s’exécutant sur ce serveur. Cette section ne traite pas de la configuration de l’authentification HTTP de base ; qui sont abordés dans [Communication sécurisée avec nginx](#secure-communication-with-nginx).

>[!NOTE]
>
>La raison pour laquelle le proxy n’est pas sécurisé dans cet exemple est qu’il est plus facile de configurer et de vérifier. Vous pouvez utiliser TLS avec ce proxy si vous le souhaitez ; pour ce faire, veillez à ajouter les informations proxy à votre configuration de bloc de serveur sécurisée.

### Spécifier des fichiers de configuration supplémentaires dans votre configuration globale

Assurez-vous que la variable `/etc/nginx/nginx.conf` contient la ligne suivante afin de charger les autres fichiers de configuration décrits dans les sections suivantes :

```conf
include /etc/nginx/conf.d/*.conf;
```

### Configuration de nginx en tant que proxy

Cette section explique comment spécifier qui peut accéder au [nginx](https://glossary.magento.com/nginx) serveur.

1. Utilisation d’un éditeur de texte pour créer un fichier `/etc/nginx/conf.d/magento_es_auth.conf` avec les contenus suivants :

   ```conf
   server {
      listen 8080;
      location /_cluster/health {
         proxy_pass http://localhost:9200/_cluster/health;
      }
   }
   ```

1. Redémarrez le nginx :

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

   Messages similaires à l’affichage suivant pour indiquer la réussite :

   ```terminal
   HTTP/1.1 200 OK
   Date: Tue, 23 Feb 2019 20:38:03 GMT
   Content-Type: application/json; charset=UTF-8
   Content-Length: 389
   Connection: keep-alive
   
   {"cluster_name":"elasticsearch","status":"yellow","timed_out":false,"number_of_nodes":1,"number_of_data_nodes":1,"active_primary_shards":5,"active_shards":5,"relocating_shards":0,"initializing_shards":0,"unassigned_shards":5,"delayed_unassigned_shards":0,"number_of_pending_tasks":0,"number_of_in_flight_fetch":0,"task_max_waiting_in_queue_millis":0,"active_shards_percent_as_number":50.0}
   ```

## Communication sécurisée avec nginx

Cette section explique comment configurer [Authentification HTTP de base](https://nginx.org/en/docs/http/ngx_http_auth_basic_module.html) avec votre proxy sécurisé. L’utilisation conjointe de l’authentification TLS et HTTP Basic empêche quiconque d’intercepter une communication avec un Elasticsearch ou avec votre serveur Adobe Commerce ou Magento Open Source.

Étant donné que nginx prend en charge l’authentification HTTP de base, nous vous recommandons de la passer à , par exemple : [Authentification Digest](https://www.nginx.com/resources/wiki/modules/auth_digest/), qui n’est pas recommandé en production.

Ressources supplémentaires :

* [Comment configurer l’authentification par mot de passe avec Nginx sur Ubuntu 14.04 (Digital Ocean)](https://www.digitalocean.com/community/tutorials/how-to-set-up-password-authentication-with-nginx-on-ubuntu-14-04)
* [Authentification HTTP De Base Avec Nginx (HowtoForge)](https://www.howtoforge.com/basic-http-authentication-with-nginx)
* [Exemple de configurations Nginx pour Elasticsearch](https://gist.github.com/karmi/b0a9b4c111ed3023a52d)

Pour plus d’informations, reportez-vous aux sections suivantes :

* [Créer des mots de passe](#create-a-password)
* [Configurer l’accès à nginx](#set-up-access-to-nginx)
* [Configuration d’un contexte restreint pour le moteur de recherche](#set-up-a-restricted-context-for-the-search-engine)
* [Vérifier que la communication est sécurisée](#secure-communication-with-nginx)

### Création d’un mot de passe

Nous vous recommandons d’utiliser Apache `htpasswd` pour coder les mots de passe d’un utilisateur ayant accès à Elasticsearch ou OpenSearch (nommé `magento_elasticsearch` dans cet exemple).

Pour créer un mot de passe :

1. Saisissez la commande suivante pour déterminer si `htpasswd` est déjà installé :

   ```bash
   which htpasswd
   ```

   Si un chemin s’affiche, il est installé ; si la commande ne renvoie aucune sortie, `htpasswd` n’est pas installé.

1. Si nécessaire, installez . `htpasswd`:

   * Ubuntu : `apt-get -y install apache2-utils`
   * CentOS : `yum -y install httpd-tools`

1. Créez un `/etc/nginx/passwd` répertoire de stockage des mots de passe :

   ```bash
   mkdir -p /etc/nginx/passwd
   ```

   ```bash
   htpasswd -c /etc/nginx/passwd/.<filename> <username>
   ```

   >[!WARNING]
   >
   >Pour des raisons de sécurité, `<filename>` doit être masqué ; c&#39;est-à-dire qu&#39;il doit commencer par un point.

1. *(Facultatif).* Pour ajouter un autre utilisateur à votre fichier de mot de passe, saisissez la même commande sans le champ `-c` Option (créer) :

   ```bash
   htpasswd /etc/nginx/passwd/.<filename> <username>
   ```

1. Vérifiez que le contenu de `/etc/nginx/passwd` est correcte.

### Configurer l’accès à nginx

Cette section explique comment spécifier qui peut accéder au serveur nginx.

>[!WARNING]
>
>L’exemple illustré est destiné à un *unsecure* proxy. Pour utiliser un proxy sécurisé, ajoutez les contenus suivants (à l&#39;exception du port d&#39;écoute) à votre bloc de serveur sécurisé.

Utilisez l’éditeur de texte pour modifier : `/etc/nginx/conf.d/magento_es_auth.conf` (non sécurisé) ou votre bloc de serveur sécurisé avec les contenus suivants :

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
>Le port d’écoute du moteur de recherche illustré dans l’exemple précédent n’est que des exemples. Pour des raisons de sécurité, nous vous recommandons d’utiliser un port d’écoute autre que celui par défaut.

### Configuration d’un contexte restreint pour le moteur de recherche

Cette section explique comment spécifier qui peut accéder au serveur du moteur de recherche.

1. Saisissez la commande suivante pour créer un répertoire dans lequel stocker la configuration de l&#39;authentification :

   ```bash
   mkdir /etc/nginx/auth/
   ```

1. Utilisation d’un éditeur de texte pour créer un fichier `/etc/nginx/auth/magento_elasticsearch.conf` avec les contenus suivants :

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
1. Redémarrez nginx et passez à la section suivante :

   ```bash
   service nginx restart
   ```

#### Vérifier

{{$include /help/_includes/verify-secure-communication.md}}
