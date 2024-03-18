---
title: Serveur d’applications pour les API GraphQL
description: Suivez ces instructions pour activer le serveur d’applications pour les API GraphQL dans votre déploiement Adobe Commerce.
badgeCoreBeta: label="2.4.7-beta" type="informative"
exl-id: 9b223d92-0040-4196-893b-2cf52245ec33
source-git-commit: 9d5795400880a65947b1b90c8806b9dcb14aba23
workflow-type: tm+mt
source-wordcount: '1897'
ht-degree: 0%

---

# Serveur d’applications pour les API GraphQL

Les API Commerce Application Server for GraphQL permettent à Adobe Commerce de conserver l’état parmi les demandes d’API Commerce GraphQL. Le serveur d’applications, qui repose sur l’extension Swoole, fonctionne comme un processus avec des threads de traitement qui gèrent le traitement des requêtes. En préservant un état d’application amorcé entre les demandes d’API GraphQL, le serveur d’applications améliore la gestion des demandes et les performances globales du produit. Les demandes d’API deviennent beaucoup plus efficaces.

Le serveur d’applications est pris en charge uniquement sur le projet Adobe Commerce sur l’infrastructure cloud Starter et Pro. Elle n’est pas disponible pour les projets de Magento Open Source. Adobe ne prend pas en charge les déploiements sur site du serveur d’applications.

## Présentation de l’architecture du serveur d’applications

Le serveur d’applications conserve l’état entre les demandes d’API de Commerce GraphQL et élimine la nécessité d’amorcer. En partageant l’état de l’application entre les processus, les requêtes GraphQL deviennent beaucoup plus efficaces, réduisant les temps de réponse jusqu’à 30 %.

Le modèle d’exécution PHP de partage-rien pose un problème du point de vue de la latence, car chaque requête nécessite l’amorçage de la structure. Ce processus d’amorçage comprend des tâches fastidieuses telles que la lecture de la configuration, la configuration du processus d’amorçage et la création d’objets de classe de service.

La transition de la logique de gestion des requêtes à une boucle d’événements au niveau de l’application semble relever le défi de la rationalisation du traitement des requêtes au niveau de l’entreprise. Cette approche élimine la nécessité d’amorcer pendant le cycle de vie de l’exécution des requêtes.

## Avantages de l’utilisation du serveur d’applications

Le serveur d’applications permet à Adobe Commerce de conserver l’état entre les demandes d’API Commerce GraphQL consécutives. Le partage de l’état de l’application entre les demandes améliore l’efficacité des demandes de l’API en réduisant les frais de traitement et en optimisant la gestion des demandes. Par conséquent, le temps de réponse des demandes GraphQL peut être réduit à 30 %.

## Configuration requise

L’exécution du serveur d’applications requiert les éléments suivants :

* PHP 8.2 ou version ultérieure
* Installation de l’extension PHP v5+
* RAM et processeur adéquats en fonction de la charge attendue

## Activation du serveur d’applications

La variable `ApplicationServer` module (`Magento/ApplicationServer/`) active Application Server pour les API GraphQL. Le serveur d’applications est pris en charge sur les déploiements sur site et dans le cloud.

## Activation d’Application Server sur Cloud Pro

Effectuez les tâches suivantes avant de déployer Application Server sur Cloud Pro :

1. Vérifiez qu’Adobe Commerce est installé sur Commerce Cloud à l’aide de Cloud Template version 2.4.7 ou ultérieure.
1. Assurez-vous que toutes vos personnalisations et extensions Commerce sont [compatible](https://developer.adobe.com/commerce/php/development/components/app-server/) avec le serveur d’applications.
1. Cloner votre projet de Commerce Cloud.
1. Ajustez les paramètres du fichier &quot;application-server/nginx.conf.sample&quot; si nécessaire.
1. Mettre en commentaire la section &quot;web&quot; active dans `project_root/.magento.app.yaml` entièrement.
1. Supprimez la mise en commentaire de la configuration de section &quot;web&quot; suivante dans la `project_root/.magento.app.yaml` contenant la commande de démarrage du serveur d’applications.

   ```yaml
   web:
       upstream:
           socket_family: tcp
           protocol: http
       commands:
           start: ./application-server/start.sh > var/log/application-server-status.log 2>&1
   ```

1. Ajoutez les fichiers mis à jour à l’index git avec la commande suivante :

   ```bash
   git add -f .magento/routes.yaml application-server/.magento/*
   ```

1. Validez vos modifications à l’aide de cette commande :

   ```bash
   git commit -m "AppServer Enabled"
   ```

### Déploiement du serveur d’applications sur Cloud Pro

Après avoir effectué les tâches préalables requises, déployez Application Server à l’aide de la commande suivante :

```bash
git push
```

### Avant de commencer un déploiement Cloud Starter

Effectuez les tâches suivantes avant de déployer Application Server sur Cloud Starter :

1. Vérifiez qu’Adobe Commerce est installé sur Commerce Cloud à l’aide de Cloud Template version 2.4.7 ou ultérieure.
1. Assurez-vous que toutes vos personnalisations et extensions Commerce sont compatibles avec le serveur d’applications.
1. Confirmez que la variable `CRYPT_KEY` est définie pour votre instance. Vous pouvez vérifier l’état de cette variable sur le portail de projets cloud (interface utilisateur d’intégration).
1. Cloner votre projet de Commerce Cloud.
1. Renommer `application-server/.magento/.magento.app.yaml.sample` to `application-server/.magento/.magento.app.yaml` et ajustez les paramètres dans .magento.app.yaml si nécessaire.
1. Ne commentez pas la configuration de l’itinéraire suivant dans la `project_root/.magento/routes.yaml` fichier à rediriger `/graphql` trafic vers le serveur d’applications.

   ```yaml
   "http://{all}/graphql":
       type: upstream
       upstream: "application-server:http"
   ```

1. Ajoutez les fichiers mis à jour à l’index git avec la commande suivante :

   ```bash
   git add -f .magento/routes.yaml application-server/.magento/*
   ```

1. Validez vos modifications à l’aide de cette commande :

   ```bash
   git commit -m "AppServer Enabled"
   ```

>[!NOTE]
>
> Assurez-vous que tous les paramètres personnalisés que vous avez dans la racine `.magento.app.yaml` sont migrés de manière appropriée vers le `application-server/.magento/.magento.app.yaml` fichier . Une fois que la variable `application-server/.magento/.magento.app.yaml` est ajouté à votre projet, vous devez le conserver en plus de la racine `.magento.app.yaml` fichier .
> Par exemple, si vous devez [configurer rabbitmq](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/service/rabbitmq) ou [gestion des propriétés web](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/app/properties/web-property) vous devez ajouter la même configuration à `application-server/.magento/.magento.app.yaml` ainsi que .

### Déploiement du serveur d’applications sur Cloud Starter

Après avoir terminé la [conditions préalables](#before-you-begin-a-cloud-starter-deployment), déployez Application Server à l’aide de la commande suivante :

```bash
git push
```

### Vérification de l’activation du serveur d’applications sur Cloud Starter

1. Exécutez une requête ou une mutation GraphQL par rapport à votre instance pour confirmer que la variable `graphql` endpoint est accessible. Par exemple :

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

1. Utilisez SSH pour accéder à votre instance Cloud. La variable `project_root/var/log/application-server.log` doit contenir un nouvel enregistrement de journal pour chaque requête GraphQL.

1. Vous pouvez également vérifier si Application Server est en cours d’exécution en exécutant la commande suivante :

   ```bash
   ps aux|grep php
   ```

   Vous devriez voir une `bin/magento server:run` traiter avec plusieurs threads.

Si ces étapes de vérification sont réussies, le serveur d’applications est en cours d’exécution et de traitement. `/graphql` requêtes.


## Activation du serveur d’applications sur site

La variable `ApplicationServer` module (`Magento/ApplicationServer/`) active Application Server pour les API GraphQL.

L’exécution locale d’Application Server nécessite l’installation de l’extension Swoole et une modification mineure du fichier de configuration NGINX de votre déploiement.

### Avant de commencer un déploiement sur site

Effectuez ces deux tâches avant d’activer la fonction `ApplicationServer` module :

* Configuration de Nginx

* Installation et configuration de l’extension Swoole v5+

### Configuration de Nginx

Votre déploiement Commerce spécifique détermine comment configurer Nginx. En règle générale, le fichier de configuration Nginx est nommé par défaut `nginx.conf` et est placé dans l’un de ces répertoires : `/usr/local/nginx/conf`, `/etc/nginx`, ou `/usr/local/etc/nginx`. Voir [Guide du débutant](https://nginx.org/en/docs/beginners_guide.html) pour plus d’informations sur la configuration de Nginx.

Exemple de configuration Nginx :

```conf
location /graphql {
    proxy_set_header Host $http_host;
    proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;

    proxy_pass http://127.0.0.1:9501/graphql;
}
```

### Installation et configuration de Swoole

Pour exécuter le serveur d’applications en local, installez l’extension Swoole (version 5.0 ou ultérieure). Il existe plusieurs façons d’installer cette extension.

## Exécution du serveur d’applications

Démarrez le serveur d’applications :

```bash
bin/magento server:run
```

Cette commande démarre un port HTTP sur 9501. Une fois le serveur d’applications lancé, le port 9501 devient un serveur proxy HTTP pour toutes les requêtes GraphQL.

## Exemple : installation de Swoole (OSX)

Cette procédure illustre comment installer l’extension Swoole sur PHP 8.2 pour les systèmes OSX. Il s’agit de l’une des différentes manières d’installer l’extension Swoole.

### Installer Swoole

Entrée :

```bash
pecl install swoole
```

Pendant l’installation, Adobe Commerce affiche des invites pour activer la prise en charge de `openssl`, `mysqlnd`, `sockets`, `http2`, et `postgres`. Entrée `yes` pour toutes les options, sauf `postgres`.

### Confirmation de l’installation de Swoole

Exécuter `php -m | grep swoole` pour confirmer que l’extension a bien été activée.

### Erreurs courantes lors de l’installation de Swoole

Les erreurs qui se produisent lors de l’installation de Swoole surviennent généralement lors de la `pecl` phase d’installation. Erreurs types : absentes `openssl.h` et `pcre2.h` fichiers . Pour résoudre ces erreurs, vérifiez que ces deux packages sont installés sur votre système local.

* Vérifiez l’emplacement de `openssl` en exécutant :

```bash
openssl version -d
```

Cette commande affiche le chemin où `openssl` est installé.

* Vérifiez l’emplacement de `pcre2` en exécutant :

```bash
pcre2-config --prefix 
```

Utilisez Homebrew pour installer les packages manquants si la sortie de commande indique que les fichiers sont manquants :

```bash
brew install openssl
```

```bash
brew install pcre2
```

#### Résolution de problèmes liés à openssl

Pour résoudre les problèmes liés à `openssl`, exécutez :

```bash
export LDFLAGS="-L/opt/homebrew/etc/openssl@3/lib" export CPPFLAGS="-I/opt/homebrew/etc/openssl@3/include"
```

Confirmez que vous utilisez le chemin d’accès à partir de votre `dev` environnement.

#### Confirmer la résolution des problèmes liés aux openssl

Vous pouvez exécuter à nouveau la commande suivante pour vérifier si les problèmes liés à openssl ont été résolus :

```bash
pecl install swoole
```

#### Résolution de problèmes liés à pcre2.h

Pour résoudre les problèmes liés à `pcre2.h`, symlink le `pcre2.h` chemin d’accès au répertoire d’extension PHP installé. Votre version spécifique installée de PHP et `pcr2.h` détermine la version particulière de la commande que vous devez utiliser.

### Vérifiez que le serveur d’applications est en cours d’exécution.

Pour vérifier que le serveur d’applications s’exécute dans votre déploiement, exécutez la commande suivante :

```bash
ps aux | grep php
```

Voici d’autres moyens de confirmer l’exécution du serveur d’applications :

* Vérifiez les `/var/log/application-server.log` pour les entrées liées aux requêtes GraphQL traitées.
* Essayez de vous connecter au port HTTP sur lequel s’exécute le serveur d’applications. Par exemple : `curl -g 'http://localhost:9501/graph`.

### Confirmation que les requêtes GraphQL sont en cours de traitement par le serveur d’applications

Le serveur d’applications ajoute le `X-Backend` en-tête de réponse avec la valeur `graphql_server` à chaque requête qu’il traite. Pour vérifier si une requête a été traitée par le serveur d’applications, recherchez cet en-tête de réponse.

### Confirmation de la compatibilité de l’extension et de la personnalisation avec le serveur d’applications

Les développeurs d’extensions et les marchands doivent d’abord vérifier que leur code d’extension et de personnalisation est conforme aux directives techniques décrites dans la section [Directives techniques](https://developer.adobe.com/commerce/php/coding-standards/technical-guidelines/).

Tenez compte de ces instructions lors de l’évaluation du code :

* Classes de service (c’est-à-dire classes qui fournissent un comportement, mais pas des données, telles que `EventManager`) ne doit pas avoir d’état modifiable.
* Évitez le couplage temporel.

## Désactivation du serveur d’applications

Les procédures de désactivation du serveur d’applications varient selon que le serveur s’exécute dans un déploiement local ou cloud.

### Désactivation du serveur d’applications sur Cloud Starter

1. Supprimez tous les nouveaux fichiers et toute autre modification de code inclus dans la variable `AppServer Enabled` commit pendant les préparatifs du déploiement.

1. Validez vos modifications à l’aide de cette commande :

   ```bash
   git commit -m "AppServer Disabled"
   ```

1. Déployez ces modifications à l’aide de cette commande :

   ```bash
   git push
   ```

### Désactivation du serveur d’applications

1. Commenter `/graphql` section de `nginx.conf` fichier que vous avez ajouté lors de l’activation du serveur d’applications.
1. Redémarrez nginx.

Cette méthode de désactivation du serveur d’applications peut s’avérer utile pour tester ou comparer rapidement les performances.

### Confirmation que le serveur d’applications est désactivé

Pour confirmer le traitement des requêtes GraphQL par `php-fpm` au lieu du serveur d’applications, saisissez la commande suivante : `ps aux | grep php`.

Une fois que le serveur d’applications a été désactivé :

* `bin/magento server:run` est inactif.
* `var/log/application-server.log` ne contient aucune entrée après les requêtes GraphQL.

## Tests d’intégration et de fonctionnement pour le serveur d’applications PHP

Les développeurs d’extensions peuvent exécuter deux tests d’intégration pour vérifier la compatibilité de l’extension avec le serveur d’applications : `GraphQlStateTest` et `ResetAfterRequestTest`.

### GraphQlStateTest

`GraphQlStateTest` détecte l’état dans les objets partagés qui ne doit pas être réutilisé pour plusieurs requêtes.

Ce test est conçu pour détecter les changements d’état dans les objets de service générés par la variable `ObjectManager`. Le test exécute deux fois des requêtes GraphQL identiques et compare l’état de l’objet de service avant et après la seconde requête.

#### Échec de GraphQlStateTest et correction potentielle

* **Impossible d’ajouter, ignorer ou filtrer une liste**. Si vous rencontrez un échec qui suggère qu’il n’est pas sûr d’ajouter, d’ignorer ou de filtrer une liste, vérifiez si la classe peut être restructurée de manière rétrocompatible pour utiliser les usines des classes de service qui ont un état modifiable.

* **Classe présentant un état modifiable**. Si la classe elle-même présente un état modifiable, essayez de réécrire votre code pour contourner cet état. Si l’état modifiable est requis pour des raisons de performances, implémentez `ResetAfterRequestInterface` et utilisez `_resetState()` pour rétablir l’état de construction initial de l’objet.

* **La propriété saisie $x ne doit pas être accessible avant le message d’initialisation**. Les échecs avec ce type de message suggèrent que la propriété spécifiée n’a pas été initialisée par le constructeur. Il s’agit d’une forme de couplage temporel qui se produit, car l’objet ne peut pas être utilisé après sa construction initiale. Ce couplage se produit même si la propriété est privée car le collecteur qui récupère les données des propriétés utilise la fonction de réflexion PHP. Dans ce cas, essayez de refactoriser la classe afin d’éviter le couplage temporel et d’éviter un état modifiable. Si cette refactorisation ne résout pas l’échec, vous pouvez remplacer le type de propriété par un type null afin qu’il puisse être initialisé sur null.  Si la propriété est un tableau, essayez d’initialiser la propriété en tant que tableau vide.

Exécuter `GraphQlStateTest` en exécutant `vendor/bin/phpunit -c $(pwd)/dev/tests/integration/phpunit.xml dev/tests/integration/testsuite/Magento/GraphQl/App/GraphQlStateTest.php`.

### ResetAfterRequestTest

`ResetAfterRequestTest` recherche toutes les classes qui implémentent `ResetAfterRequestInterface` et vérifie que la variable `_resetState()` renvoie l’état d’un objet à l’état qu’il conservait après sa construction par `ObjectManager`.  Ce test crée un objet de service avec `ObjectManager`, puis clique cet objet, appelle `_resetState()`, puis compare les deux objets. Le test n’appelle aucune méthode entre l’instanciation d’objet et `_resetState()`, cela ne confirme donc pas la réinitialisation d’un état modifiable. Il ne trouve pas de problèmes où un bogue ou une faute de frappe dans `_resetState()` peut définir l’état sur quelque chose de différent de ce qu’il était initialement.

#### Échec de ResetAfterRequestTest et correction potentielle

* **La classe contient des valeurs de propriété incohérentes**. Si ce test échoue, vérifiez si une classe a été modifiée, avec pour résultat que l’objet après la construction a des valeurs de propriété différentes de celles obtenues après l’événement `_resetState()` est appelée. Si la classe sur laquelle vous travaillez ne contient pas la propriété `_resetState()` , puis vérifiez la hiérarchie de classe pour une superclasse qui l’implémente.

* **La propriété saisie $x ne doit pas être accessible avant le message d’initialisation**. Ce problème se produit également avec `GraphQlStateTest`.

  Exécuter `ResetAfterRequestTest` en exécutant : `vendor/bin/phpunit -c $(pwd)/dev/tests/integration/phpunit.xml dev/tests/integration/testsuite/Magento/Framework/ObjectManager/ResetAfterRequestTest.php`.

### Tests fonctionnels

Les développeurs d’extensions doivent exécuter des tests fonctionnels WebAPI pour GraphQL, ainsi que tout test fonctionnel automatisé ou manuel personnalisé pour GraphQL, lors du déploiement du serveur d’applications. Ces tests fonctionnels aident les développeurs à identifier les erreurs potentielles ou les problèmes de compatibilité.
