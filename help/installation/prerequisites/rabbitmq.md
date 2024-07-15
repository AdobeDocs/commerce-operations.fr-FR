---
title: courtier de messages
description: Suivez ces étapes pour installer et configurer le logiciel de courtier de messages requis (tel que [!DNL RabbitMQ]) pour les installations sur site d’Adobe Commerce.
exl-id: ae6200d6-540f-46b3-92ba-7df7f6bb6fae
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '544'
ht-degree: 0%

---

# courtier de messages

Adobe Commerce utilise le courtier de messages Open Source [!DNL RabbitMQ]. Il offre un système de messagerie fiable, hautement disponible, évolutif et portable.

Les files d’attente de messages fournissent un mécanisme de communication asynchrone dans lequel l’expéditeur et le destinataire d’un message ne se contactent pas. Ils n’ont pas non plus besoin de communiquer simultanément avec la file d’attente des messages. Lorsqu&#39;un expéditeur place un message dans une file d&#39;attente, il est stocké jusqu&#39;à ce que le destinataire les reçoive.

Le système de file d’attente des messages doit être établi avant l’installation d’Adobe Commerce. La séquence de base est la suivante :

1. Installez [!DNL RabbitMQ] et toutes les conditions préalables.
1. Connectez [!DNL RabbitMQ] à Adobe Commerce.

>[!NOTE]
>
>Vous pouvez utiliser MySQL ou [!DNL RabbitMQ] pour le traitement de la file d’attente des messages. Pour plus d’informations sur la configuration du système de file de messages, voir [Présentation des files d’attente de messages](https://developer.adobe.com/commerce/php/development/components/message-queues/). Si vous utilisez l’API en bloc avec Adobe Commerce, la configuration du système de file d’attente des messages utilise par défaut [!DNL RabbitMQ] comme courtier de messages. Pour plus d’informations, voir [Démarrage des consommateurs de la file d’attente de messages](../../configuration/cli/start-message-queues.md) .

## Installer [!DNL RabbitMQ] sur Ubuntu

Pour installer [!DNL RabbitMQ] sur Ubuntu 16, saisissez la commande suivante :

```bash
sudo apt install -y rabbitmq-server
```

Cette commande installe également les packages d’erreur requis.

Si vous disposez d&#39;une ancienne version d&#39;Ubuntu, [!DNL RabbitMQ] recommande d&#39;installer le package sur son site web.

1. Téléchargez le package .deb depuis [rabbitmq-server](https://www.rabbitmq.com/download.html).
1. Installez le package avec `dpkg`.

Pour plus d’informations, voir [Installation sur Debian/Ubuntu](https://www.rabbitmq.com/install-debian.html) .

## Installer [!DNL RabbitMQ] sur CentOS

### Installation de l’erreur

[!DNL RabbitMQ] a été écrit en utilisant le langage de programmation Erlang, qui doit être installé sur le même système que [!DNL RabbitMQ].

Voir [Installation manuelle](https://www.erlang-solutions.com/downloads/) pour plus d’informations.

Pour installer la version correcte, reportez-vous à la matrice de version [[!DNL RabbitMQ]/Erlang](https://www.rabbitmq.com/which-erlang.html).

### Installer [!DNL RabbitMQ]

Le serveur [!DNL RabbitMQ] est inclus sur CentOS, mais la version est souvent ancienne. [!DNL RabbitMQ] recommande d’installer le package sur son site web.

Consultez la page d’installation de [!DNL RabbitMQ] pour obtenir la dernière version prise en charge. Adobe Commerce 2.3 et 2.4 prennent en charge [!DNL RabbitMQ] 3.8.x.

Pour plus d’informations, voir [Installation sous Linux RPM](https://www.rabbitmq.com/install-rpm.html) .

## Configurer [!DNL RabbitMQ]

Consultez la documentation officielle [!DNL RabbitMQ] pour configurer et gérer [!DNL RabbitMQ]. Prêtez attention aux éléments suivants :

* Variables d’environnement
* Accès au port
* Comptes utilisateur par défaut
* Démarrage et arrêt du courtier
* Limites du système

## Installation avec [!DNL RabbitMQ] et connexion

Si vous installez Adobe Commerce _après_ avoir installé [!DNL RabbitMQ], ajoutez les paramètres de ligne de commande suivants lors de l’installation :

```bash
--amqp-host="<hostname>" --amqp-port="5672" --amqp-user="<user_name>" --amqp-password="<password>" --amqp-virtualhost="/"
```

Où :

| Paramètre | Description |
|--- |--- |
| `--amqp-host` | Nom d’hôte sur lequel [!DNL RabbitMQ] est installé. |
| `--amqp-port` | Port à utiliser pour la connexion à [!DNL RabbitMQ]. La valeur par défaut est `5672`. |
| `--amqp-user` | Nom d’utilisateur pour la connexion à [!DNL RabbitMQ]. N’utilisez pas l’utilisateur par défaut `guest`. |
| `--amqp-password` | Mot de passe de la connexion à [!DNL RabbitMQ]. N’utilisez pas le mot de passe par défaut `guest`. |
| `--amqp-virtualhost` | L’hôte virtuel pour la connexion à [!DNL RabbitMQ]. La valeur par défaut est `/`. |
| `--amqp-ssl` | Indique s’il faut se connecter à [!DNL RabbitMQ]. La valeur par défaut est `false`. Si vous définissez la valeur sur true, voir Configuration de SSL pour plus d’informations. |

## Connexion [!DNL RabbitMQ]

Si vous avez déjà installé Adobe Commerce et que vous souhaitez le connecter à [!DNL RabbitMQ], ajoutez une section `queue` dans le fichier `<install_directory>/app/etc/env.php` afin qu’elle soit similaire à ce qui suit :

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

Vous pouvez également définir des valeurs de configuration [!DNL RabbitMQ] à l’aide de la commande `bin/magento setup:config:set` :

```bash
bin/magento setup:config:set --amqp-host="rabbitmq.example.com" --amqp-port="11213" --amqp-user="magento" --amqp-password="magento" --amqp-virtualhost="/"
```

Après avoir exécuté la commande ou mis à jour le fichier `<install_directory>/app/etc/env.php` avec des valeurs de configuration AMQP, exécutez `bin/magento setup:upgrade` pour appliquer les modifications et créer les files d’attente et les exchanges requis dans [!DNL RabbitMQ].

## Configurer SSL

Pour configurer la prise en charge du protocole SSL, modifiez les paramètres `ssl` et `ssl_options` du fichier `<install_directory>/app/etc/env.php` afin qu’ils ressemblent à ce qui suit :

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

## Démarrez les consommateurs de la file d’attente de messages.

Après avoir connecté Adobe Commerce et [!DNL RabbitMQ], vous devez démarrer les consommateurs de la file d’attente des messages. Pour plus d’informations, voir [Configuration des files d’attente de messages](../../configuration/cli/start-message-queues.md) .
