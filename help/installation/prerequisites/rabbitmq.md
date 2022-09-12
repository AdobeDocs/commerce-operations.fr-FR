---
title: courtier de messages
description: Suivez ces étapes pour installer et configurer les logiciels de courtier de messages requis (tels que RabbitMQ) pour les installations sur site d’Adobe Commerce et de Magento Open Source.
source-git-commit: 8f05fb6fc212c2b3fda80457bbf27ecf16fb1194
workflow-type: tm+mt
source-wordcount: '615'
ht-degree: 0%

---


# courtier de messages

Adobe Commerce utilise le courtier de messages open source RabbitMQ. Il offre un système de messagerie fiable, hautement disponible, évolutif et portable.

Les files d’attente de message fournissent un mécanisme de communication asynchrone dans lequel l’expéditeur et le destinataire d’un message ne se contactent pas. Ils n’ont pas non plus besoin de communiquer simultanément avec la file d’attente des messages. Lorsqu&#39;un expéditeur place un message dans une file d&#39;attente, il est stocké jusqu&#39;à ce que le destinataire les reçoive.

Le système de file d’attente des messages doit être établi avant l’installation d’Adobe Commerce ou de Magento Open Source. La séquence de base est la suivante :

1. Installez RabbitMQ et toutes les conditions préalables.
1. Connectez RabbitMQ à Adobe Commerce ou Magento Open Source.

>[!NOTE]
>
>Vous pouvez utiliser MySQL ou RabbitMQ pour le traitement de la file d’attente des messages. Pour plus d’informations sur la configuration du système de file d’attente des messages, voir [Présentation des files d’attente de messages](https://developer.adobe.com/commerce/php/development/components/message-queues/). Si vous utilisez l’API en bloc avec Adobe Commerce, la configuration du système de file d’attente des messages utilise par défaut RabbitMQ comme courtier de messages. Voir [Démarrage des consommateurs de la file de messages](../../configuration/cli/start-message-queues.md) pour plus d’informations.

## Installer RabbitMQ sur Ubuntu

Pour installer RabbitMQ sur Ubuntu 16, saisissez la commande suivante :

```bash
sudo apt install -y rabbitmq-server
```

Cette commande installe également les packages d’erreur requis.

Si vous disposez d’une ancienne version d’Ubuntu, RabbitMQ recommande d’installer le package sur son site web.

1. Téléchargez le package .deb depuis [rabbitmq-server](https://www.rabbitmq.com/download.html).
1. Installez le module avec `dpkg`.

Voir [Installation sur Debian/Ubuntu](https://www.rabbitmq.com/install-debian.html) pour plus d’informations.

## Installation de RabbitMQ sur CentOS

### Installer Erlang

RabbitMQ a été écrit à l’aide du langage de programmation Erlang, qui doit être installé sur le même système que RabbitMQ.

Voir [Installation manuelle](https://www.erlang-solutions.com/downloads/) pour plus d’informations.

Reportez-vous à la section [Matrice de version RabbitMQ/Erlang](https://www.rabbitmq.com/which-erlang.html) pour installer la version correcte.

### Installer RabbitMQ

Le serveur RabbitMQ est inclus sur CentOS, mais la version est souvent ancienne. RabbitMQ recommande d’installer le package sur son site web.

Consultez la page d’installation de RabbitMQ pour obtenir la dernière version prise en charge. Adobe Commerce et Magento Open Source 2.3 et 2.4 prennent en charge RabbitMQ 3.8.x.

Voir [Installation sous Linux basé sur RPM](https://www.rabbitmq.com/install-rpm.html) pour plus d’informations.

## Configuration de RabbitMQ

Consultez la documentation officielle de RabbitMQ pour configurer et gérer RabbitMQ. Prêtez attention aux éléments suivants :

* Variables d’environnement
* Accès au port
* Comptes utilisateur par défaut
* Démarrage et arrêt du courtier
* Limites du système

## Installation avec RabbitMQ et connexion

Si vous installez Adobe Commerce ou Magento Open Source _after_ Si vous installez RabbitMQ, ajoutez les paramètres de ligne de commande suivants lors de l’installation :

```bash
--amqp-host="<hostname>" --amqp-port="5672" --amqp-user="<user_name>" --amqp-password="<password>" --amqp-virtualhost="/"
```

Où :

| Paramètre | Description |
|--- |--- |
| `--amqp-host` | Nom d’hôte où RabbitMQ est installé. |
| `--amqp-port` | Port à utiliser pour se connecter à RabbitMQ. La valeur par défaut est `5672`. |
| `--amqp-user` | Nom d’utilisateur pour la connexion à RabbitMQ. N’utilisez pas l’utilisateur par défaut `guest`. |
| `--amqp-password` | Mot de passe de connexion à RabbitMQ. N’utilisez pas le mot de passe par défaut `guest`. |
| `--amqp-virtualhost` | L’hôte virtuel pour la connexion à RabbitMQ. La valeur par défaut est `/`. |
| `--amqp-ssl` | Indique s’il faut se connecter à RabbitMQ. La valeur par défaut est `false`. Si vous définissez la valeur sur true, voir Configuration de SSL pour plus d’informations. |

## Connexion à RabbitMQ

Si Adobe Commerce ou Magento Open Source était déjà installé et que vous souhaitez le connecter à RabbitMQ, ajoutez une `queue` dans la section `<install_directory>/app/etc/env.php` afin qu’il soit similaire à ce qui suit :

```php
'queue' =>
  array (
    'amqp' =>
    array (
      'host' => 'rabbitmq.example.com',
      'port' => '11213',
      'user' => 'magento',
      'password' => 'magento',
      'virtualhost' => '/'
     ),
  ),
```

Vous pouvez également définir les valeurs de configuration de RabbitMQ à l’aide de l’option `bin/magento setup:config:set` command :

```bash
bin/magento setup:config:set --amqp-host="rabbitmq.example.com" --amqp-port="11213" --amqp-user="magento" --amqp-password="magento" --amqp-virtualhost="/"
```

Après avoir exécuté la commande ou mis à jour la variable `<install_directory>/app/etc/env.php` fichier avec des valeurs de configuration AMQP, exécutez `bin/magento setup:upgrade` pour appliquer les modifications et créer les files d’attente et les échanges requis dans RabbitMQ.

## Configurer SSL

Pour configurer la prise en charge du protocole SSL, modifiez la variable `ssl` et `ssl_options` dans le `<install_directory>/app/etc/env.php` afin qu’ils soient similaires aux éléments suivants :

```php
'queue' =>
  array (
    'amqp' =>
    array (
      'host' => 'rabbitmq.example.com',
      'port' => '11213',
      'user' => 'magento',
      'password' => 'magento',
      'virtualhost' => '/',
      'ssl' => 'true',
      'ssl_options' => [
            'cafile' =>  '/etc/pki/tls/certs/DigiCertCA.crt',
            'certfile' => '/path/to/magento/app/etc/ssl/test-rabbit.crt',
            'keyfile' => '/path/to/magento/app/etc/ssl/test-rabbit.key'
       ],
     ),
  ),
```

## Démarrez les consommateurs de la file d’attente de messages

Après avoir connecté Adobe Commerce et RabbitMQ, vous devez démarrer les consommateurs de la file d’attente des messages. Voir [Configuration des files de messages](../../configuration/cli/start-message-queues.md) pour plus d’informations.
