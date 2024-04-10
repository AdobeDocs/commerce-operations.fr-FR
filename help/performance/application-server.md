---
title: Serveur d’applications GraphQL
description: Suivez ces instructions pour activer GraphQL Application Server dans votre déploiement Adobe Commerce.
exl-id: 9b223d92-0040-4196-893b-2cf52245ec33
source-git-commit: a1e548c1b1bffd634e0d5b1df0a77ef65c5997f8
workflow-type: tm+mt
source-wordcount: '1880'
ht-degree: 0%

---


# Serveur d’applications GraphQL

Le serveur d’applications Commerce GraphQL permet à Adobe Commerce de conserver l’état des requêtes d’API Commerce GraphQL. GraphQL Application Server, qui repose sur l’extension Swoole, fonctionne comme un processus avec des threads de traitement qui gèrent le traitement des demandes. En préservant un état d’application amorcé parmi les requêtes d’API GraphQL, le serveur d’applications GraphQL améliore la gestion des requêtes et les performances globales du produit. Les requêtes d’API deviennent beaucoup plus efficaces.

GraphQL Application Server est disponible uniquement pour Adobe Commerce. Il n’est pas disponible pour le Magento Open Source. Vous devez [envoyer un support technique Adobe Commerce](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide) ticket pour activer GraphQL Application Server sur les projets Pro.

>[!NOTE]
>
>GraphQL Application Server n’est actuellement pas compatible avec [[!DNL Amazon Simple Storage Service (AWS S3)]](https://aws.amazon.com/s3/). Adobe Commerce sur les clients d’infrastructure cloud qui utilisent actuellement [!DNL AWS S3] pour [stockage à distance](../configuration/remote-storage/cloud-support.md) Impossible d’utiliser le serveur d’applications GraphQL avant la publication d’un correctif plus tard en 2024 par Adobe.

## Architecture

Le serveur d’applications GraphQL conserve l’état entre les requêtes d’API Commerce GraphQL et élimine le besoin de démarrage. En partageant l’état de l’application entre les processus, les requêtes GraphQL deviennent beaucoup plus efficaces, ce qui réduit les temps de réponse de jusqu’à 30 %.

Le modèle d’exécution PHP sans partage représente un défi du point de vue de la latence, car chaque requête nécessite le bootstrapping du framework. Ce processus d’amorçage comprend des tâches longues, telles que la lecture de la configuration, la configuration du processus d’amorçage et la création d’objets de classe de service.

La transition de la logique de gestion des demandes vers une boucle d’événements au niveau de l’application semble relever le défi de rationaliser le traitement des demandes au niveau de l’entreprise. Cette approche élimine le besoin de bootstrapping pendant le cycle de vie de l’exécution des requêtes.

## Avantages

Le serveur d’applications GraphQL permet à Adobe Commerce de conserver l’état entre les requêtes consécutives de l’API GraphQL Commerce. Le partage de l’état de l’application entre les requêtes améliore l’efficacité des requêtes API en réduisant la surcharge de traitement et en optimisant la gestion des requêtes. Par conséquent, le temps de réponse des requêtes GraphQL peut être réduit jusqu’à 30 %.

## Configuration requise

L’exécution du serveur d’applications GraphQL requiert les éléments suivants :

* PHP 8.2 ou version ultérieure
* Extension Swoole PHP v5+ installée
* RAM et processeur appropriés en fonction de la charge attendue

## Activation et déploiement sur une infrastructure cloud

Le `ApplicationServer` module (`Magento/ApplicationServer/`) active le serveur d’applications GraphQL.

### Activer les projets professionnels

Effectuez les étapes suivantes avant de déployer GraphQL Application Server sur des projets Pro :

1. Déployez Adobe Commerce sur l’infrastructure cloud à l’aide du modèle cloud d’. [2.4.7-branche appserver](https://github.com/magento/magento-cloud/tree/2.4.7-appserver).
1. Vérifiez que toutes les personnalisations et extensions de Commerce sont [compatible](https://developer.adobe.com/commerce/php/development/components/app-server/) avec le serveur d’applications GraphQL.
1. Clonez votre projet de Commerce Cloud.
1. Ajustez les paramètres du fichier « application-server/nginx.conf.sample » si nécessaire.
1. Mettre en commentaire la section « web » active dans `project_root/.magento.app.yaml` fichier entièrement.
1. Supprimez les commentaires de la configuration de section « web » suivante dans le `project_root/.magento.app.yaml` fichier contenant le serveur d’applications GraphQL `start` commande.

   ```yaml
   web:
       upstream:
           socket_family: tcp
           protocol: http
       commands:
           start: ./application-server/start.sh > var/log/application-server-status.log 2>&1
   ```

1. Ajoutez les fichiers mis à jour à l’index Git avec la commande suivante :

   ```bash
   git add -f .magento/routes.yaml application-server/.magento/*
   ```

1. Validez vos modifications avec cette commande :

   ```bash
   git commit -m "AppServer Enabled"
   ```

### Déployer des projets professionnels

Une fois les étapes d’activation terminées, envoyez les modifications à votre référentiel Git pour déployer GraphQL Application Server :

```bash
git push
```

### Activer les projets de démarrage

Effectuez les étapes suivantes avant de déployer GraphQL Application Server sur des projets de démarrage :

1. Déployez Adobe Commerce sur l’infrastructure cloud à l’aide du modèle cloud d’. [2.4.7-branche appserver](https://github.com/magento/magento-cloud/tree/2.4.7-appserver).
1. Assurez-vous que toutes les personnalisations et extensions de Commerce sont compatibles avec le serveur d’applications GraphQL.
1. Vérifiez que le `CRYPT_KEY` La variable d’environnement est définie pour votre instance. Vous pouvez vérifier le statut de cette variable sur le Portail de projets cloud (interface utilisateur d’intégration).
1. Clonez votre projet de Commerce Cloud.
1. Renommer `application-server/.magento/.magento.app.yaml.sample` vers `application-server/.magento/.magento.app.yaml` et ajustez les paramètres dans .magento.app.yaml si nécessaire.
1. Supprimez les commentaires de la configuration de l’itinéraire suivant dans le `project_root/.magento/routes.yaml` fichier à rediriger `/graphql` du trafic vers le serveur d’applications GraphQL.

   ```yaml
   "http://{all}/graphql":
       type: upstream
       upstream: "application-server:http"
   ```

1. Ajoutez les fichiers mis à jour à l’index Git :

   ```bash
   git add -f .magento/routes.yaml application-server/.magento/*
   ```

1. Validez vos modifications :

   ```bash
   git commit -m "AppServer Enabled"
   ```

>[!NOTE]
>
>Vérifiez que tous les paramètres personnalisés de votre racine `.magento.app.yaml` Les fichiers sont migrés de manière appropriée vers . `application-server/.magento/.magento.app.yaml` fichier . Après le `application-server/.magento/.magento.app.yaml` si le fichier est ajouté à votre projet, vous devez le gérer en plus du fichier racine `.magento.app.yaml` fichier . Par exemple, si vous avez besoin de [configurer rabbitmq](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/service/rabbitmq) ou [gestion des propriétés web](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/app/properties/web-property) vous devez ajouter la même configuration à `application-server/.magento/.magento.app.yaml` et aussi.

### Déploiement de projets de démarrage

Après avoir terminé l’activation [étapes](#before-you-begin-a-cloud-starter-deployment), apportez les modifications à votre référentiel Git pour déployer le serveur d’applications GraphQL :

```bash
git push
```

### Vérifier l’activation sur les projets cloud

1. Exécutez une requête GraphQL ou une mutation sur votre instance pour confirmer que le `graphql` point d’entrée accessible. Par exemple :

   ```
   mutation {  
    createEmptyCart
   }
   ```

   La réponse attendue doit ressembler à l’exemple suivant :

   ```terminal
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

   Vous devriez voir une `bin/magento server:run` processus avec plusieurs threads.

Si ces étapes de vérification réussissent, le serveur d’applications GraphQL est en cours d’exécution et sert `/graphql` demandes.

## Activer les projets sur site

Le `ApplicationServer` module (`Magento/ApplicationServer/`) active le serveur d’applications GraphQL pour les API GraphQL.

L’exécution locale du serveur d’applications GraphQL nécessite l’installation de l’extension Swoole et une modification mineure du fichier de configuration Nginx de votre déploiement.

### Conditions préalables

Procédez comme suit avant d’activer `ApplicationServer` module :

* Configurer Nginx
* Installation et configuration de l’extension Swoole v5+

#### Configurer Nginx

Votre déploiement Commerce spécifique détermine comment configurer Nginx. En général, le fichier de configuration Nginx est nommé par défaut `nginx.conf` et est placé dans l’un de ces répertoires : `/usr/local/nginx/conf`, `/etc/nginx`, ou `/usr/local/etc/nginx`. Voir [Guide du débutant](https://nginx.org/en/docs/beginners_guide.html) pour plus d’informations sur la configuration de Nginx.

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

Lors de l’installation, Adobe Commerce affiche des invites pour activer la prise en charge de `openssl`, `mysqlnd`, `sockets`, `http2`, et `postgres`. Enter `yes` pour toutes les options, sauf `postgres`.

### Vérification de l’installation de Swoole

Vérifiez que l’extension a bien été activée :

```bash
php -m | grep swoole
```

### Erreurs courantes lors de l’installation de Swoole

Toutes les erreurs qui se produisent lors de l’installation de Swoole se produisent généralement pendant le `pecl` phase d’installation. Les erreurs standard incluent les données manquantes. `openssl.h` et `pcre2.h` fichiers. Pour résoudre ces erreurs, assurez-vous que ces deux packages sont installés dans votre système local.

* Vérifier l’emplacement de `openssl` en exécutant :

```bash
openssl version -d
```

Cette commande affiche le chemin où : `openssl` est installé.

* Vérifier l’emplacement de `pcre2` en exécutant :

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

Pour résoudre des problèmes liés à `openssl`, exécutez :

```bash
export LDFLAGS="-L/opt/homebrew/etc/openssl@3/lib" export CPPFLAGS="-I/opt/homebrew/etc/openssl@3/include"
```

Confirmez que vous utilisez le chemin d’accès de votre local . `dev` environnement.

#### Confirmer la résolution des problèmes en cours

Vous pouvez exécuter à nouveau la commande suivante pour vérifier si les problèmes liés à openssl ont été résolus :

```bash
pecl install swoole
```

#### Résolution des problèmes avec pcre2.h

Pour résoudre des problèmes liés à `pcre2.h`, lien symbolique `pcre2.h` Chemin d&#39;accès au répertoire d&#39;extension PHP installé. Votre version installée spécifique de PHP et `pcr2.h` détermine la version spécifique de la commande à utiliser.

### Exécution du serveur d’applications GraphQL

Démarrez le serveur d’applications GraphQL :

```bash
bin/magento server:run
```

Cette commande démarre un port HTTP sur 9501. Une fois GraphQL Application Server lancé, le port 9501 devient un serveur proxy HTTP pour toutes les requêtes GraphQL.

Pour confirmer que le serveur d’applications GraphQL est en cours d’exécution dans votre déploiement :

```bash
ps aux | grep php
```

Voici d’autres moyens de vérifier que GraphQL Application Server est en cours d’exécution :

* Vérifier le `/var/log/application-server.log` pour les entrées liées aux demandes GraphQL traitées.
* Essayez de vous connecter au port HTTP sur lequel GraphQL Application Server s’exécute. Par exemple : `curl -g 'http://localhost:9501/graph`.

### Confirmer que les demandes GraphQL sont en cours de traitement

GraphQL Application Server ajoute le `X-Backend` en-tête de réponse avec la valeur `graphql_server` à chaque requête qu’il traite. Pour vérifier si une requête a été traitée par GraphQL Application Server, recherchez cet en-tête de réponse.

### Confirmation de la compatibilité des extensions et des personnalisations

Les développeurs d’extensions et les commerçants doivent d’abord vérifier que leur code d’extension et de personnalisation respecte les directives techniques décrites dans la section [Directives techniques](https://developer.adobe.com/commerce/php/coding-standards/technical-guidelines/).

Tenez compte des recommandations suivantes lors de l’évaluation du code :

* Classes de service (c’est-à-dire les classes qui fournissent un comportement, mais pas de données, telles que . `EventManager`) ne doit pas avoir de statut modifiable.
* Éviter le couplage temporel.

## Désactivation du serveur d’applications GraphQL

Les procédures de désactivation de GraphQL Application Server varient selon que le serveur s’exécute sur site ou dans un déploiement cloud.

### Désactiver GraphQL Application Server (cloud)

1. Supprimez tous les nouveaux fichiers et toutes les autres modifications de code inclus dans le `AppServer Enabled` valider pendant les préparatifs du déploiement.

1. Validez vos modifications à l’aide de la commande suivante :

   ```bash
   git commit -m "AppServer Disabled"
   ```

1. Déployez ces modifications à l’aide de la commande suivante :

   ```bash
   git push
   ```

### Désactivation de GraphQL Application Server (sur site)

1. Commentez le `/graphql` section de `nginx.conf` fichier ajouté lors de l’activation de GraphQL Application Server.
1. Redémarrez Ingx.

Cette méthode de désactivation de GraphQL Application Server peut s’avérer utile pour tester ou comparer rapidement les performances.

### Vérifiez que GraphQL Application Server est désactivé.

Pour confirmer que les demandes GraphQL sont en cours de traitement par `php-fpm` au lieu de GraphQL Application Server, saisissez la commande suivante : `ps aux | grep php`.

Après la désactivation du serveur d’applications GraphQL :

* `bin/magento server:run` est inactif.
* `var/log/application-server.log` ne contient aucune entrée après des requêtes GraphQL.

## Tests d’intégration et tests fonctionnels pour GraphQL Application Server

Les développeurs d’extensions peuvent exécuter deux tests d’intégration pour vérifier la compatibilité des extensions avec GraphQL Application Server : `GraphQlStateTest` et `ResetAfterRequestTest`.

### GraphQlStateTest

`GraphQlStateTest` détecte l’état dans les objets partagés qui ne doivent pas être réutilisés pour plusieurs requêtes.

Ce test est conçu pour détecter les changements d’état dans les objets de service générés par le `ObjectManager`. Le test exécute deux fois des requêtes GraphQL identiques et compare l’état de l’objet de service avant et après la seconde requête.

#### Échecs de GraphQlStateTest et mesures correctives potentielles

* **Impossible d’ajouter, d’ignorer ou de filtrer une liste**. Si vous rencontrez un échec qui suggère qu’il n’est pas sûr d’ajouter, d’ignorer ou de filtrer une liste, déterminez si la classe peut être refactorisée d’une manière rétrocompatible pour utiliser les fabriques des classes de service qui ont un état mutable.

* **La classe présente un état mutable**. Si la classe elle-même présente un état mutable, essayez de réécrire votre code pour contourner cet état. Si l’état mutable est requis pour des raisons de performances, alors implémentez . `ResetAfterRequestInterface` et utiliser `_resetState()` pour réinitialiser l’objet à son état de construction initial.

* **La propriété de type $x ne doit pas être accessible avant le message d’initialisation**. Les échecs avec ce type de message suggèrent que la propriété spécifiée n’a pas été initialisée par le constructeur. C&#39;est une forme de couplage temporel qui se produit parce que l&#39;objet ne peut pas être utilisé après sa construction initiale. Ce couplage se produit même si la propriété est privée, car le collecteur qui récupère les données des propriétés utilise la fonction de réflexion PHP. Dans ce cas, essayez de refactoriser la classe pour éviter le couplage temporel et l’état mutable. Si cette refactorisation ne résout pas l’échec, vous pouvez changer le type de propriété en un type nullable afin qu’il puisse être initialisé en null.  Si la propriété est un tableau, essayez d’initialiser la propriété en tant que tableau vide.

Exécuter `GraphQlStateTest` en exécutant `vendor/bin/phpunit -c $(pwd)/dev/tests/integration/phpunit.xml dev/tests/integration/testsuite/Magento/GraphQl/App/GraphQlStateTest.php`.

### ResetAfterRequestTest

`ResetAfterRequestTest` recherche toutes les classes qui implémentent `ResetAfterRequestInterface` et vérifie que le `_resetState()` la méthode renvoie l’état d’un objet au même état qu’il avait après avoir été construit par . `ObjectManager`.  Ce test crée un objet de service avec `ObjectManager`, puis clone cet objet, appelle `_resetState()`, puis compare les deux objets. Le test n’appelle aucune méthode entre l’instanciation de l’objet et `_resetState()`, de sorte qu’il ne confirme pas la réinitialisation d’un état mutable. Il détecte des problèmes lorsqu’un bogue ou une faute de frappe est présent `_resetState()` peut définir l’état sur quelque chose de différent de ce qu’il était à l’origine.

#### Échecs de ResetAfterRequestTest et mesures correctives potentielles

* **La classe a des valeurs de propriété incohérentes.**. Si ce test échoue, vérifiez si une classe a été modifiée, de sorte que l’objet après construction possède des valeurs de propriété différentes de celles qu’il possède après l’ `_resetState()` La méthode est appelée. Si la classe sur laquelle vous travaillez ne contient pas `_resetState()` , puis vérifiez la hiérarchie de classe pour une superclasse qui l’implémente.

* **La propriété de type $x ne doit pas être accessible avant le message d’initialisation**. Ce problème se produit également avec `GraphQlStateTest`.

  Exécuter `ResetAfterRequestTest` en exécutant : `vendor/bin/phpunit -c $(pwd)/dev/tests/integration/phpunit.xml dev/tests/integration/testsuite/Magento/Framework/ObjectManager/ResetAfterRequestTest.php`.

### Tests fonctionnels

Les développeurs d’extensions doivent exécuter des tests fonctionnels WebAPI pour GraphQL, ainsi que tout test fonctionnel automatisé ou manuel personnalisé pour GraphQL, lors du déploiement de GraphQL Application Server. Ces tests fonctionnels aident les développeurs et développeuses à identifier les erreurs potentielles ou les problèmes de compatibilité.
