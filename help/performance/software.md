---
title: Recommandations logicielles
description: Consultez la liste des logiciels recommandés pour optimiser les performances des déploiements d’Adobe Commerce.
feature: Best Practices, Install
exl-id: b091a733-7655-4e91-a988-93271872c5d5
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '1392'
ht-degree: 0%

---

# Recommandations logicielles

Nous avons besoin des logiciels suivants pour les instances de production de [!DNL Commerce] :

* [PHP](../installation/system-requirements.md)
* Nginx et [PHP-FPM](https://php-fpm.org/)
* [[!DNL MySQL]](../installation/prerequisites/database/mysql.md)
* [[!DNL Elasticsearch] ou OpenSearch](../installation/prerequisites/search-engine/overview.md)

Pour les déploiements sur plusieurs serveurs ou pour les commerçants qui prévoient de développer leur activité, nous recommandons ce qui suit :

* [[!DNL Varnish] cache](../configuration/cache/config-varnish.md)
* [Redis](../configuration/cache/redis-session.md) pour les sessions (à partir de la version 2.0.6+)
* Une instance Redis distincte comme [cache par défaut](../configuration/cache/redis-pg-cache.md) (n’utilisez pas cette instance pour le cache de page)

Pour plus d’informations sur les versions prises en charge de chaque type de logiciel, consultez la section [Configuration requise](../installation/system-requirements.md).

## Système d’exploitation

Les configurations et optimisations du système d’exploitation sont similaires pour [!DNL Commerce] par rapport à d’autres applications web à charge élevée. À mesure que le nombre de connexions simultanées gérées par le serveur augmente, le nombre de sockets disponibles peut être entièrement alloué. Le noyau Linux prend en charge un mécanisme de « réutilisation » des connexions TCP. Pour activer ce mécanisme, définissez la valeur suivante dans `/etc/sysctl.conf` :

>[!INFO]
>
>L’activation de net.ipv4.tcp_tw_reuse n’a aucun effet sur les connexions entrantes.

```text
net.ipv4.tcp_tw_reuse = 1
```

Le paramètre de noyau `net.core.somaxconn` contrôle le nombre maximal de sockets ouverts en attente de connexions. Cette valeur peut être augmentée en toute sécurité à 1 024, mais elle doit être corrélée à la capacité du serveur à gérer cette quantité. Pour activer ce paramètre de noyau, définissez la valeur suivante dans `/etc/sysctl.conf` :

```text
net.core.somaxconn = 1024
```

## PHP

Magento prend entièrement en charge PHP 7.3 et 7.4. Il y a plusieurs facteurs à prendre en compte lors de la configuration de PHP pour obtenir une vitesse et une efficacité maximales sur le traitement des requêtes.

### Extensions PHP

Nous vous recommandons de limiter la liste des extensions PHP actives à celles qui sont requises pour la fonctionnalité [!DNL Commerce].

Magento Open Source et Adobe Commerce :

* ext-bcmath
* ext-ctype
* ext-curl
* ext-dom
* ext-fileinfo
* ext-gd
* ext-hash
* ext-iconv
* ext-intl
* ext-json
* ext-libxml
* ext-mbstring
* ext-openssl
* ext-pcre
* ext-pdo_mysql
* ext-simplexml
* ext-soap
* sockets texte
* ext-sodium
* jeton ext
* ext-xmlwriter
* ext-xsl
* ext-zip
* lib-libxml
* lib-openssl

En outre, Adobe Commerce requiert les éléments suivants :

* ext-bcmath
* ext-ctype
* ext-curl
* ext-dom
* ext-fileinfo
* ext-gd
* ext-hash
* ext-iconv
* ext-intl
* ext-json
* ext-libxml
* ext-mbstring
* ext-openssl
* ext-pcre
* ext-pdo_mysql
* ext-simplexml
* ext-soap
* sockets texte
* ext-sodium
* ext-spl
* jeton ext
* ext-xmlwriter
* ext-xsl
* ext-zip
* lib-libxml
* lib-openssl

L’ajout d’extensions supplémentaires augmente les temps de chargement de la bibliothèque.

>[!INFO]
>
>`php-mcrypt` a été supprimé de PHP 7.2 et remplacé par la bibliothèque [`sodium`](https://www.php.net/manual/en/book.sodium.php). Assurez-vous que [sodium](https://www.php.net/manual/en/sodium.installation.php) est correctement activé lors de la mise à niveau de PHP.

>[!INFO]
>
>La présence de toute extension de profilage et de débogage peut avoir un impact négatif sur le temps de réponse de vos pages. Par exemple, un module xDebug actif sans session de débogage peut augmenter le temps de réponse de la page de jusqu’à 30 %.

### Paramètres PHP

Pour garantir la réussite de l’exécution de toutes les instances [!DNL Commerce] sans vider les données ou le code sur le disque, définissez la limite de mémoire comme suit :

```text
memory_limit=1G
```

Pour le débogage, augmentez cette valeur sur 2G.

#### Configuration de Realpath_cache

Pour améliorer [!DNL Commerce] performances, ajoutez ou mettez à jour les paramètres de `realpath_cache` recommandés suivants dans le fichier `php.ini`. Cette configuration permet aux processus PHP de mettre en cache les chemins vers les fichiers au lieu de les rechercher chaque fois qu&#39;une page se charge. Voir [Réglage des performances](https://www.php.net/manual/en/ini.core.php) dans la documentation PHP.

```text
realpath_cache_size=10M
realpath_cache_ttl=7200
```

#### ByteCode

Pour obtenir une vitesse maximale hors [!DNL Commerce] sur PHP 7, vous devez activer le module OpCache et le configurer correctement. Ces paramètres sont recommandés pour le module :

```text
opcache.memory_consumption=512
opcache.max_accelerated_files=60000
opcache.consistency_checks=0
opcache.validate_timestamps=0
opcache.enable_cli=1
```

Lorsque vous ajustez l’allocation de mémoire pour opcache, tenez compte de la taille de la base de code Magento et de toutes vos extensions. L’équipe de performances de Magento utilise les valeurs de l’exemple précédent pour les tests, car elle fournit suffisamment d’espace dans opcache pour le nombre moyen d’extensions installées.

Si vous disposez d’une machine à faible mémoire et que peu d’extensions ou de personnalisations sont installées, utilisez les paramètres suivants pour obtenir un résultat similaire :

```text
opcache.memory_consumption=64
opcache.max_accelerated_files=60000
```

#### APCU

Nous vous recommandons d’activer l’extension [PHP APCu](https://getcomposer.org/doc/articles/autoloader-optimization.md#optimization-level-2-b-apcu-cache) et de [configurer `composer` pour la prendre en charge](../performance/deployment-flow.md#preprocess-dependency-injection-instructions) afin d’optimiser les performances. Cette extension met en cache les emplacements de fichiers pour les fichiers ouverts, ce qui améliore les performances des appels au serveur [!DNL Commerce], y compris les pages, les appels Ajax et les points d’entrée.

Modifiez votre fichier `apcu.ini` pour inclure les éléments suivants :

```text
extension=apcu.so
[apcu]
apc.enabled = 1
```

## Serveur Web

Magento prend entièrement en charge les serveurs web Nginx et Apache. [!DNL Commerce] fournit des exemples de fichiers de configuration recommandés dans les fichiers `<magento_home>/nginx.conf.sample` (Nginx) et `<magento_home>.htaccess.sample` (Apache).  L’exemple Nginx contient des paramètres pour de meilleures performances et est conçu de sorte qu’une petite reconfiguration soit nécessaire. Voici quelques-unes des bonnes pratiques de configuration principales définies dans l’exemple de fichier :

* Paramètres de mise en cache du contenu statique dans un navigateur
* Paramètres de mémoire et de temps d&#39;exécution pour PHP
* Paramètres de compression du contenu

Vous devez également configurer le nombre de threads pour le traitement des demandes d’entrée, comme indiqué ci-dessous :

| Serveur Web | Nom de l’attribut | Lieu | Informations connexes |
|--- | --- | --- | ---|
| Nginx | `worker_connections` | `/etc/nginx/nginx.conf` (Debian) | [Réglage de NGINX pour des performances optimales](https://www.nginx.com/blog/tuning-nginx/) |
| Apache 2.2 | `MaxClients` | `/etc/httpd/conf/httpd.conf` (CentOS) | [Réglage des performances Apache](https://httpd.apache.org/docs/2.2/misc/perf-tuning.html) |
| Apache 2.4 | `MaxRequestWorkers` | `/etc/httpd/conf/httpd.conf` (CentOS) | [Directives courantes Apache MPM](https://httpd.apache.org/docs/2.4/mod/mpm_common.html#maxrequestworkers) |

## [!DNL MySQL]

Ce document ne fournit pas d’instructions de réglage [!DNL MySQL] détaillées, car chaque magasin et chaque environnement sont différents. Nous pouvons toutefois formuler quelques recommandations générales.

De nombreuses améliorations ont été apportées à [!DNL MySQL] 5.7.9. Nous sommes convaincus que [!DNL MySQL] est distribué avec de bons paramètres par défaut. Les paramètres les plus critiques sont les suivants :

| Paramètre | Par défaut | Description |
|--- | --- | ---|
| `innodb_buffer_pool_instances` | 8 | La valeur par défaut est définie sur 8 afin d’éviter les problèmes liés à plusieurs threads tentant d’accéder à la même instance. |
| `innodb_buffer_pool_size` | 128MB | Associé aux multiples instances de pool décrites ci-dessus, cela signifie une allocation de mémoire par défaut de 1024MB. La taille totale est répartie entre tous les pools de mémoire tampon. Pour une efficacité optimale, spécifiez une combinaison de `innodb_buffer_pool_instances` et `innodb_buffer_pool_size` afin que chaque instance du pool de mémoire tampon soit d&#39;au moins 1 Go. |
| `max_connections` | 150 | La valeur du paramètre `max_connections` doit être corrélée au nombre total de threads PHP configurés dans le serveur d&#39;applications. Une recommandation générale serait de 300 pour un environnement petit et de 1 000 pour un environnement moyen. |
| `innodb_thread_concurrency` | 0 | La meilleure valeur pour cette configuration doit être calculée par la formule suivante : `innodb_thread_concurrency = 2 * (NumCPUs + NumDisks)` |

## [!DNL Varnish]

Magento recommande vivement d’utiliser [!DNL Varnish] comme serveur de cache de pages complètes pour votre boutique. Le module PageCache est toujours présent dans la base de code, mais il ne doit être utilisé qu’à des fins de développement. Il ne doit pas être utilisé avec, ou à la place de, [!DNL Varnish].

Installez [!DNL Varnish] sur un serveur distinct en amont du niveau web. Il doit accepter toutes les requêtes entrantes et fournir des copies de page mises en cache. Pour permettre aux [!DNL Varnish] de travailler efficacement avec des pages sécurisées, un proxy de terminaison SSL peut être placé devant [!DNL Varnish]. Nginx peut être utilisé à cet effet.

[!DNL Commerce] distribue un exemple de fichier de configuration pour [!DNL Varnish] (versions 4 et 5) qui contient tous les paramètres recommandés pour les performances. Parmi celles-ci, les plus critiques en termes de performances sont les suivantes :

* Le **contrôle d’intégrité du serveur principal** interroge le serveur [!DNL Commerce] pour déterminer s’il répond dans les délais impartis.
* Le **mode de grâce** vous permet de demander au [!DNL Varnish] de conserver un objet en cache au-delà de sa période de durée de vie (TTL) et de diffuser ce contenu obsolète si [!DNL Commerce] n’est pas intègre ou si du contenu récent n’a pas encore été récupéré.
* **Mode Saint** place les serveurs [!DNL Commerce] défectueux sur une liste bloquée pendant une durée configurable. Par conséquent, les serveurs principaux malsains ne peuvent pas servir le trafic lors de l’utilisation de [!DNL Varnish] comme répartition de charge.

Voir [Configuration [!DNL Varnish] avancée](../configuration/cache/config-varnish-advanced.md) pour plus d’informations sur l’implémentation de ces fonctionnalités.

### Optimisation des performances des ressources

En règle générale, nous vous recommandons de stocker vos ressources (images, JS, CSS, etc.) sur un réseau CDN pour des performances optimales.

Si votre site ne nécessite pas le déploiement d’un grand nombre de paramètres régionaux et que vos serveurs se trouvent dans la même région que la majorité de vos clients, vous pouvez réaliser des gains de performances significatifs à moindre coût en stockant vos ressources dans [!DNL Varnish] au lieu d’utiliser un réseau CDN.

Pour stocker vos ressources dans [!DNL Varnish], ajoutez les entrées VCL suivantes dans votre fichier `default.vcl` généré par [!DNL Commerce] pour [!DNL Varnish] 5.

À la fin de l’instruction `if` pour les requêtes PURGE dans la sous-routine `vcl_recv`, ajoutez :

```javascript
# static files are cacheable. remove SSL flag and cookie

if (req.url ~ "^/(pub/)?(media|static)/.*\.(ico|html|css|js|jpg|jpeg|png|gif|tiff|bmp|mp3|ogg|svg|swf|woff|woff2|eot|ttf|otf)$") {
  unset req.http.Https;
  unset req.http./* {{ ssl_offloaded_header }} */;
  unset req.http.Cookie;
}
```

Dans la sous-routine `vcl_backend_response`, recherchez l’instruction `if` qui annule le cookie des requêtes `GET` ou `HEAD`.
Le bloc de `if` mis à jour doit se présenter comme suit :

```javascript
# validate if we need to cache it and prevent from setting cookie
# images, css and js are cacheable by default so we have to remove cookie also

if (beresp.ttl > 0s && (bereq.method == "GET" || bereq.method == "HEAD")) {
  unset beresp.http.set-cookie;
if (bereq.url !~ "\.(ico|css|js|jpg|jpeg|png|gif|tiff|bmp|gz|tgz|bz2|tbz|mp3|ogg|svg|swf|woff|woff2|eot|ttf|otf)(\?|$)") {
  set beresp.http.Pragma = "no-cache";
  set beresp.http.Expires = "-1";
  set beresp.http.Cache-Control = "no-store, no-cache, must-revalidate, max-age=0";
  }
}
```

Redémarrez le serveur [!DNL Varnish] pour vider les ressources mises en cache chaque fois que vous mettez à niveau votre site ou déployez/mettez à jour des ressources.

## Mise en cache et serveurs de session

Magento propose un certain nombre d’options pour stocker vos données de cache et de session, notamment Redis, Memcache, système de fichiers et base de données. Certaines de ces options sont examinées ci-dessous.

### Configuration de nœud web unique

Si vous prévoyez de diffuser tout votre trafic avec un seul nœud web, il n’est pas logique de placer votre cache sur un serveur Redis distant. Utilisez plutôt le système de fichiers ou un serveur Redis local. Si vous souhaitez utiliser le système de fichiers, placez les dossiers de cache sur un volume monté sur un système de fichiers RAM. Si vous souhaitez utiliser un serveur Redis local, nous vous recommandons vivement de configurer Redis afin qu’il utilise des sockets pour les connexions directes, plutôt que d’échanger des données via HTTP.

### Configuration de plusieurs nœuds web

Pour une configuration de plusieurs nœuds web, Redis est la meilleure option. Comme [!DNL Commerce] met activement en cache de nombreuses données pour de meilleures performances, prêtez attention à votre canal réseau entre les nœuds web et le serveur Redis. Vous ne souhaitez pas que le canal devienne un goulot d’étranglement pour le traitement des demandes.

>[!INFO]
>
>Si vous devez traiter des centaines et des milliers de requêtes simultanées, vous aurez peut-être besoin d’un canal jusqu’à 1 Gbit (voire plus) vers votre serveur Redis.
