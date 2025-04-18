---
title: Serveur d’applications GraphQL
description: Suivez ces instructions pour activer le serveur d’applications GraphQL dans votre déploiement Adobe Commerce.
exl-id: 9b223d92-0040-4196-893b-2cf52245ec33
source-git-commit: c5446f0273705b158297c0a253054742ec95b44e
workflow-type: tm+mt
source-wordcount: '2082'
ht-degree: 0%

---


# Serveur d’applications GraphQL

Le serveur d’applications GraphQL Commerce permet à Adobe Commerce de conserver l’état parmi les demandes d’API Commerce GraphQL. GraphQL Application Server, qui est basé sur l’extension Swoole, fonctionne comme un processus avec des threads de traitement qui gèrent le traitement des requêtes. En préservant un état d’application amorcé entre les demandes d’API GraphQL, GraphQL Application Server améliore la gestion des demandes et les performances globales du produit. Les demandes d’API deviennent beaucoup plus efficaces.

GraphQL Application Server est disponible uniquement pour Adobe Commerce. Il n’est pas disponible pour le Magento Open Source. Pour les projets Cloud Pro, vous devez [ envoyer un ticket de support Adobe Commerce](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide) pour activer le serveur d’applications GraphQL.

>[!NOTE]
>
>Le serveur d’applications GraphQL n’est actuellement pas compatible avec [[!DNL Amazon Simple Storage Service (AWS S3)]](https://aws.amazon.com/s3/). Les clients d’Adobe Commerce sur l’infrastructure cloud qui utilisent actuellement [!DNL AWS S3] pour [l’espace de stockage distant](../configuration/remote-storage/cloud-support.md) ne peuvent pas utiliser GraphQL Application Server tant qu’Adobe n’a pas publié un correctif plus tard en 2024.

## Architecture

GraphQL Application Server conserve l’état entre les demandes d’API Commerce GraphQL et élimine la nécessité d’amorcer. En partageant l’état de l’application entre les processus, les requêtes GraphQL deviennent beaucoup plus efficaces, réduisant les temps de réponse jusqu’à 30 %.

Le modèle d’exécution PHP de partage-rien pose un problème du point de vue de la latence, car chaque requête nécessite l’amorçage de la structure. Ce processus d’amorçage comprend des tâches fastidieuses telles que la lecture de la configuration, la configuration du processus d’amorçage et la création d’objets de classe de service.

La transition de la logique de gestion des requêtes à une boucle d’événements au niveau de l’application semble relever le défi de la rationalisation du traitement des requêtes au niveau de l’entreprise. Cette approche élimine la nécessité d’amorcer pendant le cycle de vie de l’exécution des requêtes.

## Avantages

GraphQL Application Server permet à Adobe Commerce de conserver l’état entre les demandes d’API GraphQL Commerce consécutives. Le partage de l’état de l’application entre les demandes améliore l’efficacité des demandes de l’API en réduisant les frais de traitement et en optimisant la gestion des demandes. Par conséquent, le temps de réponse des demandes GraphQL peut être réduit de 30 % au maximum.

## Configuration requise

L’exécution de GraphQL Application Server requiert les éléments suivants :

* Commerce version 2.4.7+
* PHP 8.2 ou version ultérieure
* Installation de l’extension PHP v5+
* RAM et processeur adéquats en fonction de la charge attendue

## Activation et déploiement sur l’infrastructure cloud

Le module `ApplicationServer` (`Magento/ApplicationServer/`) active le serveur d’applications GraphQL.

### Activation des projets Pro

>[!NOTE]
>
>Le serveur d’applications est une fonctionnalité d’opt-in sur les instances Cloud Pro. Pour l’activer, soumettez une demande d’assistance.

Une fois que la fonction Serveur d’applications est activée sur votre projet Pro, procédez comme suit avant de déployer le serveur d’applications GraphQL :

1. Déployez Adobe Commerce sur l’infrastructure cloud à l’aide du modèle cloud de la [branche de serveur d’applications 2.4.7](https://github.com/magento/magento-cloud/tree/2.4.7-appserver).
1. Assurez-vous que toutes vos personnalisations et extensions Commerce sont [compatibles](https://developer.adobe.com/commerce/php/development/components/app-server/) avec le serveur d’applications GraphQL.
1. Cloner votre projet de Commerce Cloud.
1. Ajustez les paramètres du fichier &quot;application-server/nginx.conf.sample&quot; si nécessaire.
1. Mettre en commentaire la section &#39;web&#39; active dans le fichier `project_root/.magento.app.yaml` entièrement.
1. Supprimez la mise en commentaire de la configuration de section &#39;web&#39; suivante dans le fichier `project_root/.magento.app.yaml` contenant la commande GraphQL Application Server `start` .

   ```yaml
   web:
       upstream:
           socket_family: tcp
           protocol: http
       commands:
           start: ./application-server/start.sh > var/log/application-server-status.log 2>&1
   ```

1. Vérifiez que `/application-server/start.sh` est exécutable en exécutant la commande suivante :

   ```bash
   chmod +x application-server/start.sh
   ```

1. Ajoutez les fichiers mis à jour à l’index git avec la commande suivante :

   ```bash
   git add -f .magento.app.yaml application-server/*
   ```

1. Validez vos modifications à l’aide de cette commande :

   ```bash
   git commit -m "AppServer Enabled"
   ```

### Déploiement de projets Pro

Une fois les étapes d’activation terminées, envoyez les modifications à votre référentiel Git pour déployer GraphQL Application Server :

```bash
git push
```

### Activation des projets de démarrage

Effectuez les étapes suivantes avant de déployer GraphQL Application Server sur les projets de démarrage :

1. Déployez Adobe Commerce sur l’infrastructure cloud à l’aide du modèle cloud de la [branche de serveur d’applications 2.4.7](https://github.com/magento/magento-cloud/tree/2.4.7-appserver).
1. Assurez-vous que toutes vos personnalisations et extensions Commerce sont compatibles avec GraphQL Application Server.
1. Vérifiez que la variable d&#39;environnement `CRYPT_KEY` est définie pour votre instance. Vous pouvez vérifier l’état de cette variable dans la console cloud.
1. Cloner votre projet de Commerce Cloud.
1. Renommez `application-server/.magento/.magento.app.yaml.sample` en `application-server/.magento/.magento.app.yaml` et ajustez les paramètres dans .magento.app.yaml si nécessaire.
1. Supprimez la mise en commentaire de la configuration de l’itinéraire suivant dans le fichier `project_root/.magento/routes.yaml` pour rediriger le trafic `/graphql` vers le serveur d’applications GraphQL.

   ```yaml
   "http://{all}/graphql":
       type: upstream
       upstream: "application-server:http"
   ```

1. Ajoutez les fichiers mis à jour à l’index git :

   ```bash
   git add -f .magento/routes.yaml application-server/.magento/*
   ```

1. Validez vos modifications :

   ```bash
   git commit -m "AppServer Enabled"
   ```

>[!NOTE]
>
>Assurez-vous que tous les paramètres personnalisés de votre fichier racine `.magento.app.yaml` sont correctement migrés vers le fichier `application-server/.magento/.magento.app.yaml`. Une fois le fichier `application-server/.magento/.magento.app.yaml` ajouté à votre projet, vous devez le conserver en plus du fichier racine `.magento.app.yaml`. Par exemple, si vous devez [configurer le service RabbitMQ](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/service/rabbitmq) ou [gérer les propriétés web](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/app/properties/web-property), vous devez également ajouter la même configuration à `application-server/.magento/.magento.app.yaml`.

### Déploiement de projets de démarrage

Une fois les [étapes](#before-you-begin-a-cloud-starter-deployment) d’activation terminées, placez les modifications dans votre référentiel Git pour déployer GraphQL Application Server :

```bash
git push
```

### Vérification de l’activation des projets cloud

1. Exécutez une requête ou une mutation GraphQL par rapport à votre instance pour confirmer que le point d’entrée `graphql` est accessible. Par exemple :

   ```
   mutation {  
    createEmptyCart
   }
   ```

   La réponse attendue doit ressembler à l’exemple suivant :

   ```json
   {    
    "data": {        
        "createEmptyCart": "HLATPzcLw5ylDf76IC92nxdO2hXSXOrv"    
        }
    }
   ```

1. Utilisez SSH pour accéder à votre instance Cloud. `project_root/var/log/application-server.log` doit contenir un nouvel enregistrement de journal pour chaque requête GraphQL.

1. Vous pouvez également vérifier si GraphQL Application Server est en cours d’exécution en exécutant la commande suivante :

   ```bash
   ps aux|grep php
   ```

   Vous devriez voir un processus `bin/magento server:run` avec plusieurs threads.

Si ces étapes de vérification sont réussies, le serveur d’applications GraphQL s’exécute et traite des demandes `/graphql`.

## Activation des projets sur site

Le module `ApplicationServer` (`Magento/ApplicationServer/`) active GraphQL Application Server pour les API GraphQL.

L’exécution locale de GraphQL Application Server nécessite l’installation de l’extension Swoole et une modification mineure du fichier de configuration Nginx de votre déploiement.

### Conditions préalables

Effectuez les étapes suivantes avant d’activer le module `ApplicationServer` :

* Configuration de Nginx
* Installation et configuration de l’extension Swoole v5+

#### Configuration de Nginx

Votre déploiement Commerce spécifique détermine comment configurer Nginx. En règle générale, le fichier de configuration Nginx est nommé par défaut `nginx.conf` et est placé dans l’un de ces répertoires : `/usr/local/nginx/conf`, `/etc/nginx` ou `/usr/local/etc/nginx`. Pour plus d’informations sur la configuration de Nginx, consultez le _[Guide du débutant](https://nginx.org/en/docs/beginners_guide.html)_ .

Exemple de configuration Nginx :

```conf
location /graphql {
    proxy_set_header Host $http_host;
    proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;

    proxy_pass http://127.0.0.1:9501/graphql;
}
```

#### Installation et configuration de Swoole

Pour exécuter le serveur d’applications GraphQL en local, installez l’extension Swoole (version 5.0 ou ultérieure). Il existe plusieurs façons d’installer cette extension.

La procédure suivante décrit l’installation de l’extension Swoole pour PHP 8.2 sur des systèmes OSX. Il s’agit de l’une des différentes manières d’installer l’extension Swoole.

```bash
pecl install swoole
```

Pendant l’installation, Adobe Commerce affiche des invites pour activer la prise en charge de `openssl`, `mysqlnd`, `sockets`, `http2` et `postgres`. Saisissez `yes` pour toutes les options à l’exception de `postgres`.

### Vérification de l’installation de Swoole

Vérifiez que l’extension a bien été activée :

```bash
php -m | grep swoole
```

### Erreurs courantes lors de l’installation de Swoole

Les erreurs qui se produisent pendant l’installation de Swoole surviennent généralement pendant la phase d’installation de `pecl`. Les erreurs types incluent les fichiers `openssl.h` et `pcre2.h` manquants. Pour résoudre ces erreurs, vérifiez que ces deux packages sont installés sur votre système local.

* Vérifiez l’emplacement de `openssl` en exécutant :

```bash
openssl version -d
```

Cette commande affiche le chemin d’accès où `openssl` est installé.

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

Confirmez que vous utilisez le chemin d’accès à partir de votre environnement `dev` local.

#### Confirmer la résolution des problèmes liés aux openssl

Vous pouvez exécuter à nouveau la commande suivante pour vérifier si les problèmes liés à openssl ont été résolus :

```bash
pecl install swoole
```

#### Résolution de problèmes liés à pcre2.h

Pour résoudre les problèmes liés à `pcre2.h`, liez le chemin `pcre2.h` à votre répertoire d’extension PHP installé. Votre version spécifique de PHP et `pcr2.h` détermine la version particulière de la commande que vous devez utiliser.

### Exécution du serveur d’applications GraphQL

Démarrez le serveur d’applications GraphQL :

```bash
bin/magento server:run
```

Cette commande démarre un port HTTP sur 9501. Une fois le serveur d’applications GraphQL lancé, le port 9501 devient un serveur proxy HTTP pour toutes les requêtes GraphQL.

Pour confirmer que le serveur d’applications GraphQL est en cours d’exécution dans votre déploiement :

```bash
ps aux | grep php
```

Voici d’autres moyens de confirmer que le serveur d’applications GraphQL est en cours d’exécution :

* Recherchez dans le fichier `/var/log/application-server.log` les entrées liées aux requêtes GraphQL traitées.
* Essayez de vous connecter au port HTTP sur lequel s’exécute GraphQL Application Server. Par exemple : `curl -g 'http://localhost:9501/graph`.

### Confirmer le traitement des requêtes GraphQL

GraphQL Application Server ajoute l’en-tête de réponse `X-Backend` avec la valeur `graphql_server` à chaque requête qu’il traite. Pour vérifier si un serveur d’applications GraphQL a géré une requête, recherchez cet en-tête de réponse.

### Confirmation de la compatibilité de l’extension et de la personnalisation

Les développeurs d’extensions et les marchands doivent d’abord vérifier que leur code d’extension et de personnalisation est conforme aux directives décrites dans la section _[Directives techniques](https://developer.adobe.com/commerce/php/coding-standards/technical-guidelines/)_.

Tenez compte de ces instructions lors de l’évaluation du code :

* Les classes de service (c’est-à-dire les classes qui fournissent un comportement mais pas des données, telles que `EventManager`) ne doivent pas avoir un état modifiable.
* Évitez le couplage temporel.

## Désactivation du serveur d’applications GraphQL

Les procédures de désactivation du serveur d’applications GraphQL varient selon que le serveur s’exécute dans un déploiement local ou cloud.

### Désactivation du serveur d’applications GraphQL (cloud)

1. Supprimez tous les nouveaux fichiers et toute autre modification de code qui ont été inclus dans la validation `AppServer Enabled` lors des préparatifs du déploiement.

1. Validez vos modifications à l’aide de cette commande :

   ```bash
   git commit -m "AppServer Disabled"
   ```

1. Déployez ces modifications à l’aide de cette commande :

   ```bash
   git push
   ```

### Désactivation du serveur d’applications GraphQL (sur site)

1. Mettez en commentaire la section `/graphql` du fichier `nginx.conf` que vous avez ajouté lors de l’activation du serveur d’applications GraphQL.
1. Redémarrez nginx.

Cette méthode de désactivation du serveur d’applications GraphQL peut s’avérer utile pour tester ou comparer rapidement les performances.

### Confirmation que le serveur d’applications GraphQL est désactivé

Pour confirmer que `php-fpm` traite des demandes GraphQL au lieu du serveur d’applications GraphQL, saisissez la commande suivante : `ps aux | grep php`.

Une fois que le serveur d’applications GraphQL a été désactivé :

* `bin/magento server:run` est inactif.
* `var/log/application-server.log` ne contient aucune entrée après les requêtes GraphQL.

## Tests d’intégration et de fonctionnement pour GraphQL Application Server

Les développeurs d’extensions peuvent exécuter deux tests d’intégration pour vérifier la compatibilité des extensions avec le serveur d’applications GraphQL : `GraphQlStateTest` et `ResetAfterRequestTest`.

### GraphQlStateTest

`GraphQlStateTest` détecte l’état dans les objets partagés qui ne doivent pas être réutilisés pour plusieurs requêtes.

Ce test est conçu pour détecter les changements d’état dans les objets de service générés par `ObjectManager`. Le test exécute deux fois des requêtes GraphQL identiques et compare l’état de l’objet de service avant et après la seconde requête.

#### Échec de GraphQlStateTest et correction potentielle

* **Impossible d&#39;ajouter, d&#39;ignorer ou de filtrer une liste**. Si une erreur s’affiche au sujet de l’ajout, du saut ou du filtrage d’une liste, vous pouvez refactoriser la classe d’une manière rétrocompatible pour utiliser les usines des classes de service ayant un état modifiable.

* **La classe présente un état modifiable**. Si la classe elle-même présente un état modifiable, essayez de réécrire votre code pour contourner cet état. Si l’état modifiable est requis pour des raisons de performances, implémentez `ResetAfterRequestInterface` et utilisez `_resetState()` pour réinitialiser l’état de construction initial de l’objet.

* **La propriété tapée $x ne doit pas être accessible avant le message d&#39;initialisation**. Les échecs avec ce type de message suggèrent que la propriété spécifiée n’a pas été initialisée par le constructeur. Il s’agit d’une forme de couplage temporel qui se produit, car l’objet ne peut pas être utilisé après sa construction initiale. Ce couplage se produit même si la propriété est privée car le collecteur qui récupère les données des propriétés utilise la fonction de réflexion PHP. Dans ce cas, essayez de refactoriser la classe afin d’éviter le couplage temporel et d’éviter un état modifiable. Si cette refactorisation ne résout pas l’échec, vous pouvez remplacer le type de propriété par un type null afin qu’il puisse être initialisé sur null.  Si la propriété est un tableau, essayez d’initialiser la propriété en tant que tableau vide.

Exécutez `GraphQlStateTest` en exécutant `vendor/bin/phpunit -c $(pwd)/dev/tests/integration/phpunit.xml dev/tests/integration/testsuite/Magento/GraphQl/App/GraphQlStateTest.php`.

### ResetAfterRequestTest

`ResetAfterRequestTest` recherche toutes les classes qui implémentent `ResetAfterRequestInterface` et vérifie que la méthode `_resetState()` renvoie l’état d’un objet à l’état qu’il a conservé après avoir été construit par `ObjectManager`.  Ce test crée un objet de service avec `ObjectManager`, puis clone cet objet, appelle `_resetState()`, puis compare les deux objets. Le test n’appelle aucune méthode entre l’instanciation d’objet et `_resetState()`, il ne confirme donc pas la réinitialisation d’un état modifiable. Il détecte des problèmes où un bogue ou une faute de frappe dans `_resetState()` peut définir l’état sur quelque chose de différent de ce qu’il était à l’origine.

#### Échec de ResetAfterRequestTest et correction potentielle

* **La classe contient des valeurs de propriété incohérentes**. Si ce test échoue, vérifiez si une classe a été modifiée avec le résultat que l’objet après la construction a des valeurs de propriété différentes de celles obtenues après l’appel de la méthode `_resetState()`. Si la classe sur laquelle vous travaillez ne contient pas la méthode `_resetState()` elle-même, vérifiez la hiérarchie de classe pour une superclasse qui la met en oeuvre.

* **La propriété tapée $x ne doit pas être accessible avant le message d&#39;initialisation**. Ce problème se produit également avec `GraphQlStateTest`.

  Exécutez `ResetAfterRequestTest` en exécutant : `vendor/bin/phpunit -c $(pwd)/dev/tests/integration/phpunit.xml dev/tests/integration/testsuite/Magento/Framework/ObjectManager/ResetAfterRequestTest.php`.

### Tests fonctionnels

lors du déploiement du serveur d’applications GraphQL, les développeurs d’extensions doivent exécuter des tests fonctionnels WebAPI et tout test fonctionnel automatisé ou manuel personnalisé pour GraphQL. Ces tests fonctionnels aident les développeurs à identifier les erreurs potentielles ou les problèmes de compatibilité.

#### Mode d’affichage de l’état

Lors de l’exécution de tests fonctionnels (ou de tests manuels), le serveur d’applications GraphQL peut s’exécuter avec la fonction `--state-monitor mode` activée pour aider à trouver les classes où l’état est réutilisé involontairement. Démarrez normalement le serveur d’applications, sauf ajoutez le paramètre `--state-monitor` .

```
bin/magento server:run --state-monitor
```

Une fois chaque requête traitée, un nouveau fichier est ajouté au répertoire `tmp`, par exemple : `var/tmp/StateMonitor-thread-output-50-6nmxiK`. Une fois les tests terminés, ces fichiers peuvent être fusionnés avec la commande `bin/magento server:state-monitor:aggregate-output`, qui crée deux fichiers fusionnés, un dans `XML` et un dans `JSON`.

Exemples :

```
/var/workspace/var/tmp/StateMonitor-json-2024-04-10T18:50:39Z-hW0ucN.json
/var/workspace/var/tmp/StateMonitor-junit-2024-04-10T18:50:39Z-oreUco.xml
```

Ces fichiers peuvent être inspectés avec n’importe quel outil utilisé pour afficher du code XML ou JSON qui affiche les propriétés modifiées des objets de service tels que `GraphQlStateTest`. Le mode `--state-monitor` utilise la même liste d’exclusion et de filtrage que GraphQlStateTest.

>[!NOTE]
>
>N’utilisez pas le mode `--state-monitor` en production. Il est uniquement conçu pour le développement et les tests. Il crée de nombreux fichiers de sortie et s’exécute plus lentement que normalement.

>[!NOTE]
>
>`--state-monitor` n’est pas compatible avec les versions PHP `8.3.0` - `8.3.4` en raison d’un bogue du nettoyeur de mémoire PHP. Si vous utilisez PHP 8.3, vous devez effectuer une mise à niveau vers `8.3.5` ou une version ultérieure pour utiliser cette fonctionnalité.
