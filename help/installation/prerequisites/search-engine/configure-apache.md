---
title: Configuration d’Apache pour votre moteur de recherche
description: Pour configurer un moteur de recherche avec le serveur web Apache pour les installations sur site d’Adobe Commerce et de Magento Open Source, procédez comme suit.
source-git-commit: f6f438b17478505536351fa20a051d355f5b157a
workflow-type: tm+mt
source-wordcount: '662'
ht-degree: 0%

---


# Configuration d’Apache pour votre moteur de recherche

{{$include /help/_includes/web-server-communication.md}}

## Configuration d’un proxy

>[!NOTE]
>
>La prise en charge d’OpenSearch a été ajoutée dans la version 2.4.4. OpenSearch est un double compatible avec les Elasticsearch. Toutes les instructions pour configurer Elasticsearch 7 s’appliquent à OpenSearch. Voir [Migration de l’Elasticsearch vers OpenSearch](../../../upgrade/prepare/opensearch-migration.md) pour plus d’informations.

Cette section explique comment configurer Apache en tant que *unsecure* pour qu’Adobe Commerce ou Magento Open Source puisse utiliser un moteur de recherche s’exécutant sur ce serveur. Cette section ne traite pas de la configuration de l’authentification HTTP de base ; qui sont abordés dans [Communication sécurisée avec Apache](#secure-communication-with-apache).

>[!NOTE]
>
>La raison pour laquelle le proxy n’est pas sécurisé dans cet exemple est qu’il est plus facile de configurer et de vérifier. Vous pouvez utiliser TLS avec ce proxy. Si vous le souhaitez, veillez à ajouter les informations de proxy à votre configuration d’hôte virtuel sécurisée.

### Configuration d’un proxy pour Apache 2.4

Cette section explique comment configurer un proxy à l’aide d’un hôte virtuel.

1. Activer `mod_proxy` comme suit :

   ```bash
   a2enmod proxy_http
   ```

1. Utilisation d’un éditeur de texte pour l’ouverture `/etc/apache2/sites-available/000-default.conf`
1. Ajoutez la directive suivante en haut du fichier :

   ```conf
   Listen 8080
   ```

1. Ajoutez les éléments suivants au bas du fichier :

   ```conf
   <VirtualHost *:8080>
       ProxyPass "/" "http://localhost:9200/"
       ProxyPassReverse "/" "http://localhost:9200/"
   </VirtualHost>
   ```

1. Redémarrez Apache :

   ```bash
   service apache2 restart
   ```

1. Vérifiez que le proxy fonctionne en saisissant la commande suivante :

   ```bash
   curl -i http://localhost:<proxy port>/_cluster/health
   ```

   Par exemple, si vous utilisez Elasticsearch et que votre proxy utilise le port 8080 :

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

## Communication sécurisée avec Apache

Cette section explique comment sécuriser la communication entre Apache et le moteur de recherche à l’aide de [HTTP Basic](https://datatracker.ietf.org/doc/html/rfc2617) authentification avec Apache. Pour plus d’options, consultez l’une des ressources suivantes :

* [Tutoriel sur l’authentification et l’autorisation Apache 2.4](https://httpd.apache.org/docs/2.4/howto/auth.html)

Consultez l’une des sections suivantes :

* [Création d’un fichier de mot de passe](#create-a-password)
* [Configuration de votre hôte virtuel sécurisé](#secure-communication-with-apache)

### Création d’un mot de passe

Pour des raisons de sécurité, vous pouvez localiser le fichier de mot de passe n’importe où, à l’exception de la docroot de votre serveur web. Dans cet exemple, nous montrons comment stocker le fichier de mot de passe dans un nouveau répertoire.

#### Installez htpasswd si nécessaire

Tout d’abord, voir si vous disposez de l’Apache `htpasswd` L’utilitaire est installé comme suit :

1. Saisissez la commande suivante pour déterminer si `htpasswd` est déjà installé :

   ```bash
   which htpasswd
   ```

   Si un chemin s’affiche, il est installé ; si la commande ne renvoie aucune sortie, `htpasswd` n’est pas installé.

1. Si nécessaire, installez . `htpasswd`:

   * Ubuntu : `apt-get -y install apache2-utils`
   * CentOS : `yum -y install httpd-tools`

#### Création d’un fichier de mot de passe

Saisissez les commandes suivantes en tant qu’utilisateur avec `root` privilèges :

```bash
mkdir -p /usr/local/apache/password
```

```bash
htpasswd -c /usr/local/apache/password/.<password file name> <username>
```

Où

* `<username>` peut être :

   * Configuration de cron : l’utilisateur du serveur web ou un autre utilisateur.

   Dans cet exemple, nous utilisons l’utilisateur du serveur web, mais c’est à vous de choisir l’utilisateur.

   * Configuration de l’Elasticsearch : l’utilisateur est nommé `magento_elasticsearch` dans cet exemple


* `<password file name>` doit être un fichier masqué (commence par `.`) et doit refléter le nom de l’utilisateur. Consultez les exemples plus loin dans cette section pour plus d’informations.

Suivez les invites de votre écran pour créer un mot de passe pour l’utilisateur.

#### Exemples

**Exemple 1 : cron**
Vous ne devez configurer l’authentification que pour un seul utilisateur pour cron ; dans cet exemple, nous utilisons l’utilisateur du serveur web. Pour créer un fichier de mot de passe pour l’utilisateur du serveur web, saisissez les commandes suivantes :

```bash
mkdir -p /usr/local/apache/password
```

```bash
htpasswd -c /usr/local/apache/password/.htpasswd apache
```

**Exemple 2 : Elasticsearch**
Vous devez configurer l’authentification pour deux utilisateurs : une avec accès à nginx et une avec accès à Elasticsearch. Pour créer des fichiers de mot de passe pour ces utilisateurs, saisissez les commandes suivantes :

```bash
mkdir -p /usr/local/apache/password
```

```bash
htpasswd -c /usr/local/apache/password/.htpasswd_elasticsearch magento_elasticsearch
```

#### Ajout d’utilisateurs

Pour ajouter un autre utilisateur à votre fichier de mot de passe, saisissez la commande suivante en tant qu’utilisateur avec `root` privilèges :

```bash
htpasswd /usr/local/apache/password/.htpasswd <username>
```

### Communication sécurisée avec Apache

Cette section explique comment configurer [Authentification HTTP de base](https://httpd.apache.org/docs/2.2/howto/auth.html). L’utilisation conjointe de l’authentification TLS et HTTP Basic empêche quiconque d’intercepter une communication avec un Elasticsearch ou avec votre serveur d’applications.

Cette section explique comment spécifier qui peut accéder au serveur Apache.

1. Utilisez un éditeur de texte pour ajouter le contenu suivant à votre hôte virtuel sécurisé.

   * Apache 2.4 : Modifier `/etc/apache2/sites-available/default-ssl.conf`

   ```conf
   <Proxy *>
       Order deny,allow
       Allow from all
   
       AuthType Basic
       AuthName "Elastic Server"
       AuthBasicProvider file
       AuthUserFile /usr/local/apache/password/.htpasswd_elasticsearch
       Require valid-user
   
     # This allows OPTIONS-requests without authorization
     <LimitExcept OPTIONS>
           Require valid-user
     </LimitExcept>
   </Proxy>
   ```

1. Si vous avez ajouté le précédent à votre hôte virtuel sécurisé, supprimez `Listen 8080` et le `<VirtualHost *:8080>` directives que vous avez ajoutées précédemment à votre hôte virtuel non sécurisé.

1. Enregistrez vos modifications, quittez l’éditeur de texte, puis redémarrez Apache :

   * CentOS : `service httpd restart`
   * Ubuntu : `service apache2 restart`

#### Vérifier

{{$include /help/_includes/verify-secure-communication.md}}
