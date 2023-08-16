---
title: Recommendations logicielle
description: Consultez la liste des logiciels recommandés relatifs aux performances optimales des déploiements Adobe Commerce et Magento Open Source.
feature: Best Practices, Install
exl-id: b091a733-7655-4e91-a988-93271872c5d5
source-git-commit: 012cba58b336b032b1c911539008c1fb961c2e07
workflow-type: tm+mt
source-wordcount: '1415'
ht-degree: 0%

---

# Recommandations logicielles

Nous avons besoin des logiciels suivants pour les instances de production de [!DNL Commerce]:

* [PHP](../installation/system-requirements.md)
* Nginx et [PHP-FPM](https://php-fpm.org/)
* [[!DNL MySQL]](../installation/prerequisites/database/mysql.md)
* [[!DNL Elasticsearch] ou OpenSearch](../installation/prerequisites/search-engine/overview.md)

Pour les déploiements multi-serveurs, ou pour les commerçants qui prévoient de développer leur activité, nous vous recommandons ce qui suit :

* [[!DNL Varnish] cache](../configuration/cache/config-varnish.md)
* [Redis](../configuration/cache/redis-session.md) pour les sessions (à partir de la version 2.0.6+)
* Une instance Redis distincte comme [cache par défaut](../configuration/cache/redis-pg-cache.md) (n’utilisez pas cette instance pour le cache de page)

Voir [configuration requise](../installation/system-requirements.md) pour plus d’informations sur les versions prises en charge de chaque type de logiciel.

## Système d’exploitation

Les configurations et optimisations des systèmes d’exploitation sont similaires pour [!DNL Commerce] par rapport aux autres applications web à charge élevée. À mesure que le nombre de connexions simultanées gérées par le serveur augmente, le nombre de sockets disponibles peut être entièrement alloué. Le noyau Linux prend en charge un mécanisme de &quot;réutilisation&quot; des connexions TCP. Pour activer ce mécanisme, définissez la valeur suivante dans `/etc/sysctl.conf`:

>[!INFO]
>
>L’activation de net.ipv4.tcp_tw_reset n’a aucun effet sur les connexions entrantes.

```text
net.ipv4.tcp_tw_reuse = 1
```

Le paramètre du noyau `net.core.somaxconn` contrôle le nombre maximal de sockets ouverts en attente de connexions. Cette valeur peut être augmentée en toute sécurité à 1024, mais elle doit être corrélée avec la capacité du serveur à gérer cette quantité. Pour activer ce paramètre de noyau, définissez la valeur suivante dans `/etc/sysctl.conf`:

```text
net.core.somaxconn = 1024
```

## PHP

Magento prend entièrement en charge PHP 7.3 et 7.4. Plusieurs facteurs doivent être pris en compte lors de la configuration de PHP pour obtenir une vitesse et une efficacité optimales lors du traitement des requêtes.

### Extensions PHP

Nous vous recommandons de limiter la liste des extensions PHP actives à celles requises pour [!DNL Commerce] .

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
* ext-sockets
* ext-sodium
* ext-tokenizer
* ext-xmlwriter
* ext-xsl
* ext-zip
* lib-libxml
* lib-openssl

En outre, Adobe Commerce requiert :

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
* ext-sockets
* ext-sodium
* ext-spl
* ext-tokenizer
* ext-xmlwriter
* ext-xsl
* ext-zip
* lib-libxml
* lib-openssl

L’ajout d’autres extensions augmente les temps de chargement de bibliothèque.

>[!INFO]
>
>`php-mcrypt` a été supprimé de PHP 7.2 et remplacé par le [`sodium` bibliothèque](https://www.php.net/manual/en/book.sodium.php). Assurez-vous que [sodium](https://www.php.net/manual/en/sodium.installation.php) est correctement activé lors de la mise à niveau de PHP.

>[!INFO]
>
>La présence d’extensions de profilage et de débogage peut avoir une incidence négative sur le temps de réponse de vos pages. Par exemple, un module xDebug actif sans session de débogage peut augmenter le temps de réponse de la page de 30 %.

### Paramètres PHP

Pour garantir une exécution réussie de tous les [!DNL Commerce] les instances sans vider de données ou de code sur le disque, définissez la limite de mémoire comme suit :

```text
memory_limit=1G
```

Pour le débogage, augmentez cette valeur à 2G.

#### Configuration Realpath_cache

Pour améliorer [!DNL Commerce] performances, ajouter ou mettre à jour les recommandations suivantes `realpath_cache` dans le `php.ini` fichier . Cette configuration permet aux processus PHP de mettre en cache les chemins d’accès aux fichiers au lieu de les rechercher chaque fois qu’une page est chargée. Voir [Optimisation des performances](https://www.php.net/manual/en/ini.core.php) dans la documentation PHP.

```text
realpath_cache_size=10M
realpath_cache_ttl=7200
```

#### ByteCode

Pour obtenir une vitesse maximale hors de [!DNL Commerce] sous PHP 7, vous devez activer le module OpCache et le configurer correctement. Ces paramètres sont recommandés pour le module :

```text
opcache.memory_consumption=512
opcache.max_accelerated_files=60000
opcache.consistency_checks=0
opcache.validate_timestamps=0
opcache.enable_cli=1
```

Lorsque vous affinez l’allocation de mémoire pour opcache, prenez en compte la taille de la base de code du Magento et toutes vos extensions. L’équipe des performances du Magento utilise les valeurs de l’exemple précédent pour les tests, car elle fournit suffisamment d’espace dans opcache pour le nombre moyen d’extensions installées.

Si vous disposez d’une machine à faible mémoire et que vous n’avez pas installé de nombreuses extensions ou personnalisations, utilisez les paramètres suivants pour obtenir un résultat similaire :

```text
opcache.memory_consumption=64
opcache.max_accelerated_files=60000
```

#### APCU

Nous vous recommandons d’activer la variable [Extension APCu PHP](https://getcomposer.org/doc/articles/autoloader-optimization.md#optimization-level-2-b-apcu-cache) et [configuration `composer` pour la prendre en charge](../performance/deployment-flow.md#preprocess-dependency-injection-instructions) pour optimiser les performances. Cette extension met en cache les emplacements des fichiers ouverts, ce qui augmente les performances pour [!DNL Commerce] les appels au serveur, y compris les pages, les appels Ajax et les points de terminaison.

Modifiez votre `apcu.ini` afin d’inclure les éléments suivants :

```text
extension=apcu.so
[apcu]
apc.enabled = 1
```

## Serveur web

Magento prend entièrement en charge les serveurs web Nginx et Apache. [!DNL Commerce] fournit des exemples de fichiers de configuration recommandés dans la variable  `<magento_home>/nginx.conf.sample` (Nginx) et  `<magento_home>.htaccess.sample` fichiers (Apache).  L’exemple Nginx contient des paramètres pour de meilleures performances et est conçu de sorte qu’une petite reconfiguration soit requise. Voici quelques-unes des principales bonnes pratiques de configuration définies dans le fichier d’exemple :

* Paramètres de mise en cache du contenu statique dans un navigateur
* Paramètres de mémoire et d’heure d’exécution pour PHP
* Paramètres de compression du contenu

Vous devez également configurer le nombre de threads pour le traitement des requêtes d’entrée, comme indiqué ci-dessous :

| Serveur web | Nom de l’attribut | Emplacement | Informations connexes |
|--- | --- | --- | ---|
| Nginx | `worker_connections` | `/etc/nginx/nginx.conf` (Debian) | [Réglage de NGINX pour les performances](https://www.nginx.com/blog/tuning-nginx/) |
| Apache 2.2 | `MaxClients` | `/etc/httpd/conf/httpd.conf` (CentOS) | [Réglage des performances d’Apache](https://httpd.apache.org/docs/2.2/misc/perf-tuning.html) |
| Apache 2.4 | `MaxRequestWorkers` | `/etc/httpd/conf/httpd.conf` (CentOS) | [Directives communes Apache MPM](https://httpd.apache.org/docs/2.4/mod/mpm_common.html#maxrequestworkers) |

## [!DNL MySQL]

Ce document ne fournit pas de détails [!DNL MySQL] l’optimisation des instructions car chaque magasin et environnement est différent, mais nous pouvons faire des recommandations générales.

De nombreuses améliorations ont été apportées à [!DNL MySQL] 5.7.9 Nous sommes sûrs que [!DNL MySQL] est distribué avec de bons paramètres par défaut. Les paramètres les plus critiques sont les suivants :

| Paramètre | Par défaut | Description |
|--- | --- | ---|
| `innodb_buffer_pool_instances` | 8 | La valeur par défaut est définie sur 8 pour éviter les problèmes liés à plusieurs threads tentant d’accéder à la même instance. |
| `innodb_buffer_pool_size` | 128MB | Combiné avec les instances de pool décrites ci-dessus, cela signifie une allocation de mémoire par défaut de 1 024 Mo. La taille totale est divisée entre tous les pools de mémoire tampon. Pour une meilleure efficacité, indiquez une combinaison de `innodb_buffer_pool_instances` et `innodb_buffer_pool_size` de sorte que chaque instance de pool de mémoire tampon soit d’au moins 1 Go. |
| `max_connections` | 150 | La valeur de la variable `max_connections` doit correspondre au nombre total de threads PHP configurés dans le serveur d’applications. Une recommandation générale serait de 300 pour un petit et de 1 000 pour un environnement moyen. |
| `innodb_thread_concurrency` | 0 | La meilleure valeur pour ce paramétrage doit être calculée par la formule : `innodb_thread_concurrency = 2 * (NumCPUs + NumDisks)` |

## [!DNL Varnish]

Magento recommande vivement d’utiliser [!DNL Varnish] comme serveur de cache de page complet pour votre magasin. Le module PageCache est toujours présent dans le code base, mais il doit être utilisé à des fins de développement uniquement. Elle ne doit pas être utilisée avec ou au lieu de [!DNL Varnish].

Installer [!DNL Varnish] sur un serveur distinct devant le niveau web. Il doit accepter toutes les requêtes entrantes et fournir des copies de page mises en cache. Pour autoriser [!DNL Varnish] pour travailler efficacement avec des pages sécurisées, un proxy de terminaison SSL peut être placé devant [!DNL Varnish]. Nginx peut être utilisé à cet effet.

[!DNL Commerce] distribue un exemple de fichier de configuration pour [!DNL Varnish] (versions 4 et 5) qui contient tous les paramètres recommandés pour les performances. Parmi celles-ci, les plus critiques en termes de performances sont les suivantes :

* **Contrôle d’intégrité du serveur principal** interroge la variable [!DNL Commerce] afin de déterminer s’il répond en temps opportun.
* **Mode de grâce** vous permet d’indiquer à [!DNL Varnish] pour conserver un objet en cache au-delà de sa période de temps d’activation (TTL) et diffuser ce contenu obsolète si [!DNL Commerce] n’est pas sain ou si du contenu neuf n’a pas encore été récupéré.
* **Mode Saint** blacklister les listes malsaines [!DNL Commerce] pendant une durée configurable. Par conséquent, les arrière-plans malsains ne peuvent pas traiter le trafic lors de l’utilisation de [!DNL Varnish] comme équilibreur de charge.

Voir [Avancé [!DNL Varnish] configuration](../configuration/cache/config-varnish-advanced.md) pour plus d’informations sur l’implémentation de ces fonctionnalités.

### Optimisation des performances des ressources

En général, nous vous recommandons de stocker vos ressources (images, JS, CSS, etc.) sur un réseau de diffusion de contenu pour des performances optimales.

Si votre site ne nécessite pas de déploiement d’un grand nombre de paramètres régionaux et que vos serveurs se trouvent dans la même région que la majorité de vos clients, vous pouvez obtenir des gains de performances significatifs à moindre coût en stockant vos ressources dans [!DNL Varnish] au lieu d’utiliser un CDN.

Pour stocker vos ressources dans [!DNL Varnish], ajoutez les entrées VCL suivantes dans votre `default.vcl` fichier généré par [!DNL Commerce] pour [!DNL Varnish] 5.

À la fin du `if` instruction des requêtes PURGE dans la variable `vcl_recv` sous-routine, ajoutez :

```javascript
# static files are cacheable. remove SSL flag and cookie

if (req.url ~ "^/(pub/)?(media|static)/.*\.(ico|html|css|js|jpg|jpeg|png|gif|tiff|bmp|mp3|ogg|svg|swf|woff|woff2|eot|ttf|otf)$") {
  unset req.http.Https;
  unset req.http./* {{ ssl_offloaded_header }} */;
  unset req.http.Cookie;
}
```

Dans le `vcl_backend_response` sous-routine, recherchez `if` qui annule la définition du cookie pour `GET` ou `HEAD` requêtes.
La mise à jour `if` block doit ressembler à ce qui suit :

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

Redémarrez le [!DNL Varnish] pour vider les ressources mises en cache chaque fois que vous mettez à niveau votre site ou déployez/mettez à jour des ressources.

## Mise en cache et serveurs de session

Magento propose plusieurs options pour stocker vos données de cache et de session, notamment Redis, Memcache, filesystem et database. Certaines de ces options sont décrites ci-dessous.

### Configuration d’un noeud web unique

Si vous prévoyez de diffuser tout votre trafic avec un seul noeud web, il n’est pas logique de placer votre cache sur un serveur Redis distant. Utilisez plutôt le système de fichiers ou un serveur Redis local. Si vous souhaitez utiliser le système de fichiers, placez vos dossiers de cache sur un volume monté sur un système de fichiers RAM. Si vous souhaitez utiliser un serveur Redis local, nous vous recommandons vivement de configurer Redis afin qu’il utilise des sockets pour les connexions directes, plutôt que d’échanger des données via HTTP.

### Configuration de plusieurs noeuds web

Pour la configuration de plusieurs noeuds web, Redis est la meilleure option. Parce que [!DNL Commerce] met activement en cache de nombreuses données pour de meilleures performances, prêtez attention à votre canal réseau entre les noeuds web et le serveur Redis. Vous ne souhaitez pas que le canal devienne un goulot d’étranglement pour le traitement des demandes.

>[!INFO]
>
>Si vous avez besoin de traiter des centaines, des milliers de demandes simultanées, vous devrez peut-être avoir un canal allant jusqu’à 1 Gbit (ou même plus large) sur votre serveur Redis.
