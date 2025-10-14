---
title: Serveur d’applications GraphQL
description: Découvrez le serveur d’applications GraphQL dans Adobe Commerce. Découvrez les conseils d’implémentation et les stratégies d’optimisation.
exl-id: 9b223d92-0040-4196-893b-2cf52245ec33
source-git-commit: cb89f0c0a576cf6cd8b53a4ade12c21106e2cdf3
workflow-type: tm+mt
source-wordcount: '2360'
ht-degree: 0%

---


# Serveur d’applications GraphQL

Le serveur d’applications Commerce GraphQL permet à Adobe Commerce de conserver l’état des requêtes d’API Commerce GraphQL. GraphQL Application Server, qui repose sur l’extension Swoole, fonctionne comme un processus avec des threads de traitement qui gèrent le traitement des requêtes. En préservant un état d’application amorcé parmi les requêtes d’API GraphQL, le serveur d’applications GraphQL améliore la gestion des requêtes et les performances globales du produit. Les requêtes d’API deviennent beaucoup plus efficaces.

GraphQL Application Server est disponible uniquement pour Adobe Commerce. Il n’est pas disponible pour Magento Open Source. Pour les projets Cloud Pro, vous devez [envoyer un ticket d’assistance Adobe Commerce](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide) pour activer le serveur d’applications GraphQL.

>[!NOTE]
>
>Le serveur d’applications GraphQL n’est actuellement pas compatible avec [[!DNL Amazon Simple Storage Service (AWS S3)]](https://aws.amazon.com/s3/). Les clients Adobe Commerce sur les infrastructures cloud qui utilisent actuellement [!DNL AWS S3] pour le [stockage à distance](../configuration/remote-storage/cloud-support.md) ne peuvent pas utiliser GraphQL Application Server.

## Architecture

Le serveur d’applications GraphQL conserve l’état entre les requêtes d’API Commerce GraphQL et élimine le besoin de démarrage. En partageant l’état de l’application entre les processus, les requêtes GraphQL deviennent beaucoup plus efficaces, ce qui réduit les temps de réponse de jusqu’à 30 %.

Le modèle d’exécution PHP sans partage représente un défi du point de vue de la latence, car chaque requête nécessite le bootstrapping du framework. Ce processus d’amorçage comprend des tâches longues, telles que la lecture de la configuration, la configuration du processus d’amorçage et la création d’objets de classe de service.

La transition de la logique de gestion des demandes vers une boucle d’événements au niveau de l’application semble relever le défi de rationaliser le traitement des demandes au niveau de l’entreprise. Cette approche élimine la nécessité de procéder à un amorçage pendant le cycle de vie de l’exécution des requêtes.

## Avantages

Le serveur d’applications GraphQL permet à Adobe Commerce de conserver l’état entre les requêtes consécutives de l’API Commerce GraphQL. Le partage de l’état de l’application entre les requêtes améliore l’efficacité des requêtes API en réduisant la surcharge de traitement et en optimisant la gestion des requêtes. Par conséquent, vous pouvez réduire le temps de réponse des requêtes GraphQL de jusqu’à 30 %.

## Configuration requise

L’exécution du serveur d’applications GraphQL requiert les éléments suivants :

* Commerce version 2.4.7+
* PHP 8.2 ou version ultérieure
* RAM et CPU adéquates en fonction de la charge prévue
* Extension Swoole PHP v5+ (voir les exigences spécifiques au projet ci-dessous)

### Projets cloud

Adobe Commerce sur les projets d’infrastructure cloud inclut l’extension Swoole par défaut. Vous pouvez l’[activer](https://experienceleague.adobe.com/fr/docs/commerce-on-cloud/user-guide/configure/app/php-settings#enable-extensions) dans la propriété `runtime` du fichier `.magento.app.yaml`. Par exemple :

```yaml
runtime:
    extensions:
        - swoole
```

### Projets sur site

Vous devez manuellement [installer et configurer](#install-and-configure-swoole) l’extension Swoole PHP pour les projets sur site.

## Activation et déploiement sur une infrastructure cloud

Le module `ApplicationServer` (`Magento/ApplicationServer/`) active GraphQL Application Server.

### Activer les projets professionnels

>[!NOTE]
>
>Le serveur d’applications est une fonctionnalité de souscription sur les instances de Cloud Pro. Pour l’activer, envoyez une demande d’assistance.

Une fois que la fonction Serveur d’applications est activée sur votre projet Pro, effectuez les étapes suivantes avant de déployer GraphQL Application Server :

1. Déployez Adobe Commerce sur l’infrastructure cloud à l’aide du modèle cloud de la branche [2.4.7-appserver](https://github.com/magento/magento-cloud/tree/2.4.7-appserver).
1. Assurez-vous que toutes les personnalisations et extensions de Commerce sont [compatibles](https://developer.adobe.com/commerce/php/development/components/app-server/) avec GraphQL Application Server.
1. Clonez votre projet Commerce Cloud.
1. Ajustez les paramètres du fichier « application-server/nginx.conf.sample » si nécessaire.
1. Commentez entièrement la section « web » active dans `project_root/.magento.app.yaml` fichier .
1. Supprimez les commentaires de la configuration de section « web » suivante dans le fichier `project_root/.magento.app.yaml` qui inclut la commande `start` du serveur d’applications GraphQL.

   ```yaml
   web:
       upstream:
           socket_family: tcp
           protocol: http
       commands:
           start: ./application-server/start.sh > var/log/application-server-status.log 2>&1
   ```

1. Assurez-vous que `/application-server/start.sh` est exécutable en exécutant la commande suivante :

   ```bash
   chmod +x application-server/start.sh
   ```

1. Ajoutez les fichiers mis à jour à l’index Git avec la commande suivante :

   ```bash
   git add -f .magento.app.yaml application-server/*
   ```

1. Validez vos modifications avec cette commande :

   ```bash
   git commit -m "AppServer Enabled"
   ```

### Déployer des projets professionnels

Une fois les étapes d’activation terminées, envoyez les modifications à votre référentiel Git pour déployer le serveur d’applications GraphQL :

```bash
git push
```

### Activer les projets de démarrage

Procédez comme suit avant de déployer GraphQL Application Server sur des projets de démarrage :

1. Déployez Adobe Commerce sur l’infrastructure cloud à l’aide du modèle cloud de la branche [2.4.7-appserver](https://github.com/magento/magento-cloud/tree/2.4.7-appserver).
1. Assurez-vous que toutes les personnalisations et extensions de Commerce sont compatibles avec le serveur d’applications GraphQL.
1. Vérifiez que la variable d’environnement `CRYPT_KEY` est définie pour votre instance. Vous pouvez vérifier le statut de cette variable sur la console Cloud.
1. Clonez votre projet Commerce Cloud.
1. Renommez `application-server/.magento/.magento.app.yaml.sample` en `application-server/.magento/.magento.app.yaml` et ajustez les paramètres dans .magento.app.yaml si nécessaire.
1. Supprimez les commentaires de la configuration de l’itinéraire suivant dans le fichier `project_root/.magento/routes.yaml` pour rediriger le trafic `/graphql` vers GraphQL Application Server.

   ```yaml
   "http://{all}/graphql":
       type: upstream
       upstream: "application-server:http"
   ```

1. Supprimez les commentaires de la section `files` dans le fichier `.magento/services.yaml`.

   ```yaml
   files:
       type: network-storage:2.0
       disk: 5120
   ```

1. Supprimez les commentaires de la partie `TEMPORARY SHARED MOUNTS` de la configuration de montage dans le fichier `.magento.app.yaml`.

   ```yaml
   "var_shared":
       source: "service"
       service: "files"
       source_path: "var"
   "app/etc_shared":
       source: "service"
       service: "files"
       source_path: "etc"
   "pub/media_shared":
       source: "service"
       service: "files"
       source_path: "media"
   "pub/static_shared":
       source: "service"
       service: "files"
       source_path: "static"
   ```

1. Ajoutez les fichiers mis à jour à l’index Git :

   ```bash
   git add -f .magento.app.yaml .magento/routes.yaml .magento/services.yaml application-server/.magento/*
   ```

1. Validez vos modifications et envoyez-les pour déclencher un déploiement :

   ```bash
   git commit -m "Enabling AppServer: initial changes"
   git push
   ```

1. Utilisez SSH pour vous connecter à l’environnement cloud distant (_et non_ à l’application `application-server`) :

   ```bash
   magento-cloud ssh -p <project-ID> -e <environment-ID>
   ```

1. Synchronisez les données des montages locaux aux montages partagés :

   ```bash
   rsync -avz var/* var_shared/
   rsync -avz app/etc/* app/etc_shared/
   rsync -avz pub/media/* pub/media_shared/
   rsync -avz pub/static/* pub/static_shared/
   ```

1. Mettez en commentaire les parties `DEFAULT MOUNTS` et `TEMPORARY SHARED MOUNTS` de la configuration des montages dans le fichier `.magento.app.yaml`.

   ```yaml
   #"var": "shared:files/var"
   #"app/etc": "shared:files/etc"
   #"pub/media": "shared:files/media"
   #"pub/static": "shared:files/static"
   
   #"var_shared":
   #    source: "service"
   #    service: "files"
   #    source_path: "var"
   #"app/etc_shared":
   #    source: "service"
   #    service: "files"
   #    source_path: "etc"
   #"pub/media_shared":
   #    source: "service"
   #    service: "files"
   #    source_path: "media"
   #"pub/static_shared":
   #    source: "service"
   #    service: "files"
   #    source_path: "static"
   ```

1. Supprimez les commentaires des parties `OLD LOCAL MOUNTS` et `SHARED MOUNTS` de la configuration des montages dans le fichier `.magento.app.yaml`.

   ```yaml
   "var_old": "shared:files/var"
   "app/etc_old": "shared:files/etc"
   "pub/media_old": "shared:files/media"
   "pub/static_old": "shared:files/static"
   
   "var":
       source: "service"
       service: "files"
       source_path: "var"
   "app/etc":
       source: "service"
       service: "files"
       source_path: "etc"
   "pub/media":
       source: "service"
       service: "files"
       source_path: "media"
   "pub/static":
       source: "service"
       service: "files"
       source_path: "static"
   ```

1. Ajoutez le fichier mis à jour à l’index Git, validez les modifications et effectuez une notification push pour déclencher un déploiement :

   ```bash
   git add -f .magento.app.yaml
   git commit -m "Enabling AppServer: switch mounts"
   git push
   ```

1. Assurez-vous que les fichiers des répertoires `*_old` sont présents dans les répertoires réels.

1. Nettoyage des anciens montages locaux :

   ```bash
   rm -rf var_old/*
   rm -rf app/etc_old/*
   rm -rf pub/media_old/*
   rm -rf pub/static_old/*
   ```

1. Mettez en commentaire la partie `OLD LOCAL MOUNTS` de la configuration des montages dans le fichier `.magento.app.yaml`.

   ```yaml
   #"var_old": "shared:files/var"
   #"app/etc_old": "shared:files/etc"
   #"pub/media_old": "shared:files/media"
   #"pub/static_old": "shared:files/static"
   ```

1. Ajoutez le fichier mis à jour à l’index Git, validez les modifications et effectuez une notification push pour déclencher un déploiement :

   ```bash
   git add -f .magento.app.yaml
   git commit -m "Enabling AppServer: finish"
   git push
   ```

>[!NOTE]
>
>Assurez-vous que tous les paramètres personnalisés de votre fichier de `.magento.app.yaml` racine sont migrés de manière appropriée vers le fichier `application-server/.magento/.magento.app.yaml`. Une fois le fichier `application-server/.magento/.magento.app.yaml` ajouté à votre projet, vous devez le gérer en plus du fichier racine `.magento.app.yaml`. Par exemple, si vous devez [configurer le service RabbitMQ](https://experienceleague.adobe.com/fr/docs/commerce-on-cloud/user-guide/configure/service/rabbitmq) ou [gérer les propriétés web](https://experienceleague.adobe.com/fr/docs/commerce-on-cloud/user-guide/configure/app/properties/web-property) vous devez également ajouter la même configuration à `application-server/.magento/.magento.app.yaml`.

### Vérifier l’activation sur les projets cloud

1. Exécutez une requête GraphQL ou une mutation sur votre instance pour confirmer que le point d’entrée `graphql` est accessible. Par exemple :

   ```
   mutation {  
    createEmptyCart
   }
   ```

   La réponse attendue doit ressembler à cet exemple :

   ```json
   {    
    "data": {        
        "createEmptyCart": "HLATPzcLw5ylDf76IC92nxdO2hXSXOrv"    
        }
    }
   ```

1. Utilisez SSH pour accéder à votre instance cloud. Le `project_root/var/log/application-server.log` doit contenir un nouvel enregistrement de journal pour chaque requête GraphQL.

1. Vous pouvez également vérifier si GraphQL Application Server est en cours d’exécution en exécutant la commande suivante :

   ```bash
   ps aux|grep php
   ```

   Un processus `bin/magento server:run` avec plusieurs threads doit s’afficher.

Si ces étapes de vérification réussissent, le serveur d’applications GraphQL exécute et diffuse les requêtes `/graphql`.

## Activer les projets sur site

Le module `ApplicationServer` (`Magento/ApplicationServer/`) active les API GraphQL Application Server for GraphQL.

L’exécution locale du serveur d’applications GraphQL nécessite l’installation de l’extension Swoole et une modification mineure du fichier de configuration Nginx de votre déploiement.

### Conditions préalables

Procédez comme suit avant d’activer le module `ApplicationServer` :

* Configurer Nginx
* Installation et configuration de l’extension Swoole v5+

#### Configurer Nginx

Votre déploiement Commerce spécifique détermine comment configurer Nginx. En général, le fichier de configuration Nginx est nommé par défaut `nginx.conf` et placé dans l&#39;un de ces répertoires : `/usr/local/nginx/conf`, `/etc/nginx` ou `/usr/local/etc/nginx`. Voir le _[Guide du débutant](https://nginx.org/en/docs/beginners_guide.html)_ pour plus d&#39;informations sur la configuration de Nginx.

Exemple de configuration Nginx :

```conf
location /graphql {
    proxy_set_header Host $http_host;
    proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;

    proxy_pass http://127.0.0.1:9501/graphql;
}
```

#### Installation et configuration de Swoole

Pour exécuter le serveur d’applications GraphQL localement, installez l’extension Swoole (v5.0 ou version ultérieure). Il existe plusieurs façons d’installer cette extension.

La procédure suivante décrit comment installer l&#39;extension Swoole pour PHP 8.2 sur les systèmes OSX. Il s’agit de l’une des nombreuses façons d’installer l’extension Swoole.

```bash
pecl install swoole
```

Lors de l’installation, Adobe Commerce affiche des invites pour activer la prise en charge de `openssl`, `mysqlnd`, `sockets`, `http2` et `postgres`. Saisissez `yes` pour toutes les options, à l’exception de `postgres`.

### Vérifier l’installation de Swoole

Vérifiez que l’extension a bien été activée :

```bash
php -m | grep swoole
```

### Erreurs courantes lors de l’installation de Swoole

Les erreurs qui se produisent lors de l’installation de Swoole se produisent généralement pendant la phase d’installation de `pecl`. Les erreurs standard incluent les fichiers `openssl.h` et `pcre2.h` manquants. Pour résoudre ces erreurs, assurez-vous que ces deux packages sont installés dans votre système local.

* Vérifiez l’emplacement des `openssl` en exécutant :

```bash
openssl version -d
```

Cette commande affiche le chemin d’accès où `openssl` est installé.

* Vérifiez l’emplacement des `pcre2` en exécutant :

```bash
pcre2-config --prefix 
```

Utilisez Homebrew pour installer les packages manquants si la sortie de commande indique que des fichiers sont manquants :

```bash
brew install openssl
```

```bash
brew install pcre2
```

#### Résoudre les problèmes liés à openssl

Pour résoudre les problèmes liés à `openssl`, exécutez :

```bash
export LDFLAGS="-L/opt/homebrew/etc/openssl@3/lib" export CPPFLAGS="-I/opt/homebrew/etc/openssl@3/include"
```

Vérifiez que vous utilisez le chemin d’accès à partir de votre environnement de `dev` local.

#### Confirmer la résolution des problèmes en cours

Vous pouvez exécuter à nouveau la commande suivante pour vérifier si les problèmes liés à openssl ont été résolus :

```bash
pecl install swoole
```

#### Résolution des problèmes avec pcre2.h

Pour résoudre les problèmes liés à `pcre2.h`, liez symboliquement le chemin `pcre2.h` à votre répertoire d&#39;extension PHP installé. Votre version installée spécifique de PHP et `pcr2.h` détermine la version particulière de la commande que vous devez utiliser.

### Exécution du serveur d’applications GraphQL

Démarrez le serveur d’applications GraphQL :

```bash
bin/magento server:run
```

Cette commande démarre un port HTTP sur 9501. Une fois GraphQL Application Server lancé, le port 9501 devient un serveur proxy HTTP pour toutes les requêtes GraphQL.

Pour confirmer que GraphQL Application Server est en cours d’exécution dans votre déploiement :

```bash
ps aux | grep php
```

Voici d’autres moyens de vérifier que GraphQL Application Server est en cours d’exécution :

* Recherchez dans le fichier `/var/log/application-server.log` les entrées liées aux demandes GraphQL traitées.
* Essayez de vous connecter au port HTTP sur lequel GraphQL Application Server s’exécute. Par exemple : `curl -g 'http://localhost:9501/graph`.

### Confirmer que les demandes GraphQL sont en cours de traitement

GraphQL Application Server ajoute l’en-tête de réponse `X-Backend` avec la valeur `graphql_server` à chaque requête qu’il traite. Pour vérifier si le serveur d’applications GraphQL a géré une requête, recherchez cet en-tête de réponse.

### Confirmation de la compatibilité des extensions et des personnalisations

Les développeurs d’extensions et les commerçants doivent d’abord vérifier que leur code d’extension et de personnalisation respecte les directives décrites dans la section _[Directives techniques](https://developer.adobe.com/commerce/php/coding-standards/technical-guidelines/)_.

Tenez compte des recommandations suivantes lors de l’évaluation du code :

* Les classes de service (c’est-à-dire les classes qui fournissent un comportement, mais pas de données, telles que `EventManager`) ne doivent pas avoir le statut modifiable.
* Éviter le couplage temporel.

## Désactivation du serveur d’applications GraphQL

Les procédures de désactivation de GraphQL Application Server varient selon que le serveur s’exécute sur site ou dans un déploiement cloud.

### Désactiver GraphQL Application Server (cloud)

1. Supprimez tous les nouveaux fichiers et toutes les autres modifications de code inclus dans la validation `AppServer Enabled` lors de vos préparations pour le déploiement.

1. Validez vos modifications à l’aide de la commande suivante :

   ```bash
   git commit -m "AppServer Disabled"
   ```

1. Déployez ces modifications à l’aide de la commande suivante :

   ```bash
   git push
   ```

### Désactivation du serveur d’applications GraphQL (sur site)

1. Mettez en commentaire la section `/graphql` `nginx.conf` fichier que vous avez ajoutée lors de l’activation de GraphQL Application Server.
1. Redémarrez Nginx.

Cette méthode de désactivation du serveur d’applications GraphQL peut s’avérer utile pour tester ou comparer rapidement les performances.

### Vérifiez que GraphQL Application Server est désactivé.

Pour confirmer que `php-fpm` traite les requêtes GraphQL au lieu du serveur d’applications GraphQL, saisissez la commande suivante : `ps aux | grep php`.

Après la désactivation du serveur d’applications GraphQL :

* `bin/magento server:run` est inactif.
* `var/log/application-server.log` ne contient aucune entrée après des requêtes GraphQL.

## Tests d’intégration et tests fonctionnels pour GraphQL Application Server

Les développeurs d’extensions peuvent exécuter deux tests d’intégration pour vérifier la compatibilité des extensions avec GraphQL Application Server : `GraphQlStateTest` et `ResetAfterRequestTest`.

### GraphQlStateTest

Le `GraphQlStateTest` détecte l’état dans les objets partagés qui ne doivent pas être réutilisés pour plusieurs requêtes.

Ce test est conçu pour détecter les changements d’état dans les objets de service générés par le `ObjectManager`. Le test exécute deux fois des requêtes GraphQL identiques et compare l’état de l’objet de service avant et après la seconde requête.

#### Échecs de GraphQlStateTest et mesures correctives potentielles

* **Impossible d’ajouter, d’ignorer ou de filtrer une liste**. Si vous obtenez cette erreur, essayez de refactoriser votre classe pour utiliser des usines pour les classes de service avec un état mutable.

* **La classe présente un état mutable**. Si la classe elle-même présente un état mutable, essayez de réécrire votre code pour contourner cet état. Si l’état mutable est requis pour des raisons de performances, implémentez `ResetAfterRequestInterface` et utilisez `_resetState()` pour réinitialiser l’objet à son état construit initial.

* **La propriété de type $x ne doit pas être accessible avant le message d’initialisation**. Les échecs avec ce type de message suggèrent que la propriété spécifiée n’a pas été initialisée par le constructeur. Il s&#39;agit d&#39;une forme de couplage temporel qui se produit parce que l&#39;objet ne peut pas être utilisé après sa construction initiale. Ce couplage se produit même si la propriété est privée, car le collecteur qui récupère les données des propriétés utilise la fonction de réflexion PHP. Dans ce cas, essayez de refactoriser la classe pour éviter le couplage temporel et éviter un état mutable. Si cette refactorisation ne résout pas l’échec, vous pouvez changer le type de propriété en un type nullable afin qu’il puisse être initialisé en null.  Si la propriété est un tableau, essayez d’initialiser la propriété en tant que tableau vide.

Exécutez `GraphQlStateTest` en exécutant `vendor/bin/phpunit -c $(pwd)/dev/tests/integration/phpunit.xml dev/tests/integration/testsuite/Magento/GraphQl/App/GraphQlStateTest.php`.

### ResetAfterRequestTest

Le `ResetAfterRequestTest` recherche toutes les classes qui implémentent `ResetAfterRequestInterface` et vérifie que la méthode `_resetState()` renvoie l’état d’un objet au même état qu’il avait après avoir été construite par `ObjectManager`.  Ce test crée un objet de service avec `ObjectManager`, puis clone cet objet, appelle `_resetState()`, puis compare les deux objets. Le test n’appelle aucune méthode entre l’instanciation de l’objet et `_resetState()`, il ne confirme donc pas la réinitialisation d’un état mutable. Il détecte des problèmes lorsqu’un bug ou une faute de frappe dans `_resetState()` peut définir l’état sur quelque chose de différent de ce qu’il était à l’origine.

#### Échecs de ResetAfterRequestTest et mesures correctives potentielles

* **La classe possède des valeurs de propriété incohérentes**. Si ce test échoue, vérifiez si une classe a été modifiée avec pour résultat que l&#39;objet après construction a des valeurs de propriété différentes de celles qu&#39;il a après l&#39;appel de la méthode `_resetState()`. Si la classe sur laquelle vous travaillez ne contient pas la méthode `_resetState()` elle-même, vérifiez la hiérarchie de classe pour une superclasse qui l’implémente.

* **La propriété de type $x ne doit pas être accessible avant le message d’initialisation**. Ce problème se produit également avec `GraphQlStateTest`.

  Exécutez `ResetAfterRequestTest` en exécutant : `vendor/bin/phpunit -c $(pwd)/dev/tests/integration/phpunit.xml dev/tests/integration/testsuite/Magento/Framework/ObjectManager/ResetAfterRequestTest.php`.

### Tests fonctionnels

Lors du déploiement de GraphQL Application Server, les développeurs d’extensions doivent exécuter des tests fonctionnels WebAPI et tout test fonctionnel automatisé ou manuel personnalisé pour GraphQL. Ces tests fonctionnels aident les développeurs et développeuses à identifier les erreurs potentielles ou les problèmes de compatibilité.

#### Mode Moniteur d&#39;état

Lors de l’exécution de tests fonctionnels (ou de tests manuels), le serveur d’applications GraphQL peut s’exécuter avec `--state-monitor mode` activé pour aider à trouver les classes où l’état est réutilisé involontairement. Démarrez le serveur d’applications normalement, mais ajoutez le paramètre `--state-monitor` .

```
bin/magento server:run --state-monitor
```

Une fois chaque demande traitée, un nouveau fichier est ajouté dans le répertoire `tmp`, par exemple : `var/tmp/StateMonitor-thread-output-50-6nmxiK`. Une fois les tests terminés, ces fichiers peuvent être fusionnés avec la commande `bin/magento server:state-monitor:aggregate-output`, ce qui crée deux fichiers fusionnés, l’un dans `XML` et l’autre dans `JSON`.

Exemples :

```
/var/workspace/var/tmp/StateMonitor-json-2024-04-10T18:50:39Z-hW0ucN.json
/var/workspace/var/tmp/StateMonitor-junit-2024-04-10T18:50:39Z-oreUco.xml
```

Ces fichiers peuvent être inspectés à l’aide de n’importe quel outil que vous utilisez pour afficher des fichiers XML ou JSON qui affichent les propriétés modifiées des objets de service comme le fait `GraphQlStateTest`. Le mode `--state-monitor` utilise la même liste d’omission et la même liste de filtres que GraphQlStateTest.

>[!NOTE]
>
>N’utilisez pas le mode `--state-monitor` en production. Il est uniquement conçu pour le développement et les tests. Il crée de nombreux fichiers de sortie et s’exécute plus lentement que d’habitude.

>[!NOTE]
>
>`--state-monitor` n&#39;est pas compatible avec les versions PHP `8.3.0` - `8.3.4` en raison d&#39;un bug dans le nettoyeur de mémoire PHP. Si vous utilisez PHP 8.3, vous devez effectuer une mise à niveau vers la version `8.3.5` ou plus récente pour utiliser cette fonctionnalité.

## Configuration d’en-têtes alternatifs pour la détection des adresses IP client

Par défaut, GraphQL Application Server prend en charge une configuration standard pour l’en-tête `x-forwarded-for` défini dans le fichier `app/etc/di.xml`, ce qui permet de récupérer avec précision l’adresse IP du client dans des environnements proxy et CDN standard.

Si vous devez prendre en charge des en-têtes supplémentaires ou personnalisés (tels que `x-client-ip`, `fastly-client-ip` ou `x-real-ip`), vous pouvez étendre ou remplacer l’argument `alternativeHeaders` dans votre fichier `app/etc/di.xml`. Cela n’est nécessaire que si votre environnement utilise des en-têtes autres que `x-forwarded-for` pour transmettre l’adresse IP du client.

Par exemple, pour ajouter la prise en charge d’autres en-têtes, mettez à jour votre `app/etc/di.xml` comme suit :

```xml
<type name="Magento\Framework\HTTP\PhpEnvironment\RemoteAddress">
    <arguments>
        <argument name="alternativeHeaders" xsi:type="array">
            <item name="x-client-ip" xsi:type="string">HTTP_X_CLIENT_IP</item>
            <item name="fastly-client-ip" xsi:type="string">HTTP_FASTLY_CLIENT_IP</item>
            <item name="x-real-ip" xsi:type="string">HTTP_X_REAL_IP</item>
            <item name="x-forwarded-for" xsi:type="string">HTTP_X_FORWARDED_FOR</item>
        </argument>
    </arguments>
</type>
```

Vous pouvez ajouter, supprimer ou réorganiser les en-têtes selon les besoins pour vous assurer que l’adresse IP du client est récupérée à partir de la source appropriée pour votre configuration.

>[!NOTE]
>
>Si vous utilisez Adobe Commerce Cloud avec le module Fast CDN, cette configuration est gérée automatiquement et aucune modification manuelle n’est nécessaire. Une configuration manuelle n’est nécessaire que pour les configurations de réseau CDN, de proxy ou d’en-tête non standard.
