---
title: Serveur d’applications pour les API GraphQL
description: Suivez ces instructions pour activer le serveur d’applications pour les API GraphQL dans votre déploiement Adobe Commerce.
badgeCoreBeta: label="2.4.7-beta1" type="informative"
exl-id: 346cc722-131e-4ed0-bc8c-23c3a1e58258
source-git-commit: f085c0a77fe59ff3b2d76abbd6965b6bc8ee69db
workflow-type: tm+mt
source-wordcount: '533'
ht-degree: 0%

---

# Serveur d’applications pour les API GraphQL

Les API Commerce Application Server for GraphQL permettent à Adobe Commerce de conserver l’état entre les demandes de l’API Commerce GraphQL et réduisent le délai d’amorçage de chaque demande. En partageant l’état de l’application entre les processus, les demandes d’API deviennent beaucoup plus efficaces.

Cette version bêta du serveur d’applications est disponible pour les déploiements sur site exécutant PHP 8.1 ou 8.2 uniquement. Il ne prend pas en charge les déploiements basés sur le cloud. Il ne prend pas encore en charge la fonctionnalité de GraphQL B2B. Les requêtes GraphQL peuvent ne pas fonctionner comme prévu dans les déploiements sur site lorsque cette version du serveur d’applications PHP est configurée.

## Qui peut utiliser le serveur d’applications ?

Application Server est disponible uniquement pour les déploiements Commerce sur site.

## Activation du serveur d’applications pour les API GraphQL

La variable `ApplicationServer` module (`Magento/ApplicationServer/`) active Application Server pour les API GraphQL.

L’exécution d’Application Server nécessite l’installation de l’extension Open Swoole et une modification mineure du fichier de configuration Nginx de votre déploiement pour exécuter ce serveur d’applications localement.

### Avant de commencer

Effectuez ces deux tâches avant d’activer la fonction `ApplicationServer` module :

* Configuration de Nginx

* Installation et configuration de l’extension Open Swoole v22

### Configuration de Nginx

Votre déploiement Commerce spécifique détermine comment configurer Nginx. En règle générale, le fichier de configuration Nginx est nommé par défaut `nginx.conf` et est placé dans l’un de ces répertoires : `/usr/local/nginx/conf`, `/etc/nginx`, ou `/usr/local/etc/nginx`. Voir [Guide du débutant](http://nginx.org/en/docs/beginners_guide.html) pour plus d’informations sur la configuration de Nginx.

Exemple de configuration Nginx :

```conf
location /graphql {
    proxy_set_header Host $http_host;
    proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;

    proxy_pass http://127.0.0.1:9501/graphql;
}
```

### Installation et configuration d’Open Swoole

Pour exécuter le serveur d’applications en local, installez l’extension Open Swoole v22. Il existe plusieurs façons d’installer cette extension.

## Exécution du serveur d’applications

Démarrez le serveur d’applications :

```bash
bin/magento server:run
```

Cette commande démarre un port HTTP sur 9501. Une fois le serveur d’applications lancé, le port 9501 devient un serveur proxy HTTP pour toutes les requêtes GraphQL.

## Exemple : installation d’Open Swoole (OSX)

Cette procédure illustre comment installer l’extension Open Swoole sur PHP 8.2 pour les systèmes OSX. Il s’agit de l’une des différentes manières d’installer l’extension Open Swoole.

Vous pouvez installer l’extension Open Swoole pour PHP (v22) et les packages Composer requis par cette extension avec une seule commande.

### Installer Open Swoole

Entrée :

```bash
pecl install openswoole-22.0.0 | composer require openswoole/core:22.1.1
```

Pendant l’installation, Adobe Commerce affiche des invites pour activer la prise en charge de `openssl`, `mysqlnd`, `sockets`, `http2`, et `postgres`. Entrée `yes` pour toutes les options, sauf `postgres`.

### Confirmation de l’installation d’Open Swoole

Exécuter `php -m | grep openswoole` pour confirmer que l’extension a bien été activée.

### Erreurs courantes lors de l’installation Open Swoole

Toutes les erreurs qui se produisent lors de l’installation Open Swoole surviennent généralement lors de la `pecl` phase d’installation. Erreurs types : absentes `openssl.h` et `pcre2.h` fichiers . Pour résoudre ces erreurs, vérifiez que ces deux packages sont installés sur votre système local.

* Vérifier l’emplacement de `openssl` en exécutant :

```bash
openssl version -d
```

Cette commande affiche le chemin où `openssl` est installé.

* Vérifier l’emplacement de `pcre2` en exécutant :

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
pecl install openswoole-22.0.0
```

#### Résolution de problèmes liés à pcre2.h

Pour résoudre les problèmes liés à `pcre2.h`, symlink le `pcre2.h` chemin d’accès au répertoire d’extension PHP installé. Votre version spécifique installée de PHP et `pcr2.h` détermine la version particulière de la commande que vous devez utiliser.
