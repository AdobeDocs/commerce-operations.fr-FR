---
title: Courtier en messages (Artéfacts ActiveMQ)
description: Pour installer et configurer le courtier de messages Apache ActiveMQ Artemis pour les installations sur site d’Adobe Commerce, procédez comme suit.
source-git-commit: aee02c258acaeb7a248e10b867017ef8f72b544d
workflow-type: tm+mt
source-wordcount: '902'
ht-degree: 0%

---

# Courtier en messages (Artéfacts ActiveMQ)

Adobe Commerce prend également en charge le courtier de messages open source ActiveMQ Artemis via le protocole STOMP (Simple Text Oriented Messaging Protocol). Il fournit un système de messagerie fiable et évolutif, offrant une flexibilité pour les intégrations STOMP.


>[!NOTE]
>
>ActiveMQ Artemis a été introduit dans Adobe Commerce 2.4.6 et les versions ultérieures. Pour plus d’informations sur l’installation d’ActiveMQ Artemis dans Adobe Commerce sur des projets d’infrastructure cloud, voir [Configuration du service ActiveMQ](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/service/activemq) dans le *Guide de Commerce sur le cloud*.

Les files d&#39;attente de messages fournissent un mécanisme de communication asynchrone dans lequel l&#39;expéditeur et le destinataire d&#39;un message ne se contactent pas. Ils n’ont pas non plus besoin de communiquer avec la file d’attente de messages en même temps. Lorsqu&#39;un expéditeur place un message dans une file d&#39;attente, il est stocké jusqu&#39;à ce que le destinataire le reçoive.

Le système de file d’attente des messages doit être établi avant d’installer Adobe Commerce. La séquence de base est la suivante :

1. Installez Apache ActiveMQ Artemis et toutes les conditions préalables.
1. Connectez ActiveMQ à Adobe Commerce.

>[!NOTE]
>
>Vous pouvez utiliser MySQL, ActiveMQ ou [!DNL RabbitMQ] pour le traitement des files d’attente de messages. Pour plus d’informations sur la configuration du système de files d’attente de messages, voir [Présentation des files d’attente de messages](https://developer.adobe.com/commerce/php/development/components/message-queues/). Si vous utilisez l’API Bulk avec Adobe Commerce, la configuration du système de file d’attente des messages utilise par défaut [!DNL RabbitMQ] comme courtier de messages. Voir [Démarrer les consommateurs de file d’attente de messages](../../configuration/cli/start-message-queues.md) pour plus d’informations.

>[!TIP]
>
>[&#x200B; Consultez toujours la page de téléchargement d’Apache ActiveMQ Artemis &#x200B;](https://activemq.apache.org/components/artemis/download/) la dernière version stable avant l’installation. Les exemples de ce document utilisent la version 2.42.0, qui est la dernière version stable en date de septembre 2025.


## Installation des artéfacts Apache ActiveMQ

Vous pouvez installer ActiveMQ Artemis à l’aide de Docker (recommandé pour le développement) ou d’une installation manuelle (recommandée pour la production).

### Option 1 : installation de Docker (recommandée pour le développement)

#### Conditions préalables

Vérifiez que Docker est installé et en cours d’exécution sur votre système.

>[!TIP]
>
>Pour plus d’informations sur l’image officielle d’ActiveMQ Artemis Docker, consultez la page [Apache ActiveMQ Artemis Docker Hub](https://hub.docker.com/r/apache/activemq-artemis).

#### Etapes d&#39;installation

1. Exécutez ActiveMQ Artemis à l’aide de l’image Docker officielle :

   ```bash
   # Run with default configuration
   docker run --detach \
     --name artemis \
     --publish 8161:8161 \
     --publish 61613:61613 \
     --publish 5672:5672 \
     apache/activemq-artemis:2.42.0
   ```

1. Exécuter avec des informations d’identification personnalisées :

   ```bash
   # Run with custom username/password
   docker run --detach \
     --name artemis \
     --publish 8161:8161 \
     --publish 61613:61613 \
     --publish 5672:5672 \
     --env ARTEMIS_USER=magento \
     --env ARTEMIS_PASSWORD=magento \
     apache/activemq-artemis:2.42.0
   ```

#### Commandes de gestion Docker

```bash
# Check container status
docker ps | grep artemis

# View logs
docker logs artemis

# Stop the container
docker stop artemis

# Start the container
docker start artemis

# Remove the container
docker rm artemis
```

#### Accès aux services

Une fois le conteneur Docker en cours d’exécution, vous pouvez accéder aux éléments suivants :

- **Console web** : http://localhost:8161/console (informations d’identification par défaut : artemis/artemis)
- **Port STOMP** : localhost:61613 (pour la connexion Adobe Commerce)

>[!NOTE]
>
>L’installation de Docker est recommandée pour le développement et les tests. Pour la production, envisagez d’utiliser une installation manuelle avec des configurations de sécurité appropriées.

### Option 2 : installation manuelle sur Ubuntu/CentOS

#### Conditions préalables

Assurez-vous que Java 17 ou version ultérieure est installé (requis pour ActiveMQ Artemis 2.42.0+).

### Etapes d&#39;installation

1. Téléchargez et installez la dernière version à partir du site web [Apache ActiveMQ Artemis](https://activemq.apache.org/components/artemis/download/). Depuis septembre 2025, la dernière version stable est la version 2.42.0 :

   ```bash
   sudo mkdir -p /opt/artemis
   cd /opt/artemis
   sudo curl -O https://downloads.apache.org/activemq/activemq-artemis/2.42.0/apache-artemis-2.42.0-bin.tar.gz
   sudo tar -xzf apache-artemis-2.42.0-bin.tar.gz --strip-components=1
   sudo rm apache-artemis-2.42.0-bin.tar.gz
   ```

1. Créez l’utilisateur `artemis` et définissez la propriété :

   ```bash
   # Create artemis user and set ownership
   sudo useradd -r -s /bin/false artemis 2>/dev/null || true
   sudo chown -R artemis:artemis /opt/artemis
   ```

1. Créez une instance de broker :

   ```bash
   sudo /opt/artemis/bin/artemis create /var/lib/artemis-instance --user artemis --password artemis --allow-anonymous
   sudo chown -R artemis:artemis /var/lib/artemis-instance
   ```

1. Démarrez le courtier :

   ```bash
   # Start in foreground (for testing)
   sudo /var/lib/artemis-instance/bin/artemis run
   
   # Start as background service
   sudo /var/lib/artemis-instance/bin/artemis-service start
   
   # Stop the broker
   sudo /var/lib/artemis-instance/bin/artemis-service stop
   
   # Restart the broker
   sudo /var/lib/artemis-instance/bin/artemis-service restart
   
   # Force stop the broker
   sudo /var/lib/artemis-instance/bin/artemis-service force-stop
   
   # Check broker status
   sudo /var/lib/artemis-instance/bin/artemis-service status
   ```

## Configuration des artéfacts ActiveMQ

Consultez la documentation officielle d’ActiveMQ Artemis pour configurer et gérer le courtier. Faites attention aux éléments suivants :

- Variables d’environnement
- Accès au port (protocole STOMP)
- Comptes utilisateur et informations d’identification par défaut
- Démarrer et arrêter le courtier
- Limites du système et réglage des ressources

### Fichiers de configuration de clé

- `/var/lib/artemis-instance/etc/broker.xml` - Configuration du courtier principal
- `/var/lib/artemis-instance/etc/artemis-users.properties` - Authentification de l’utilisateur
- `/var/lib/artemis-instance/etc/artemis-roles.properties` - Rôles utilisateur
- `/var/lib/artemis-instance/etc/bootstrap.xml` - Configuration de Bootstrap

### Activer le protocole STOMP

Vérifiez `/var/lib/artemis-instance/etc/broker.xml` l&#39;accepteur STOMP est configuré :

```xml
<acceptors>
   <acceptor name="artemis">tcp://0.0.0.0:61616?tcpSendBufferSize=1048576;tcpReceiveBufferSize=1048576;amqpMinLargeMessageSize=102400;protocols=CORE,AMQP,STOMP,HORNETQ,MQTT,OPENWIRE;useEpoll=true;amqpCredits=1000;amqpLowCredits=300;amqpDuplicateDetection=true</acceptor>
   <acceptor name="stomp">tcp://0.0.0.0:61613?protocols=STOMP</acceptor>
   <acceptor name="stomp-ssl">tcp://0.0.0.0:61617?protocols=STOMP;sslEnabled=true;keyStorePath=/path/to/keystore.jks;keyStorePassword=password</acceptor>
</acceptors>
```

Pour activer SSL sur STOMP, vous devez ajouter explicitement l&#39;accepteur de `stomp-ssl`.

## Installation avec les artéfacts ActiveMQ et connexion

Si vous installez Adobe Commerce _après_ vous installez ActiveMQ Artemis, ajoutez les paramètres de ligne de commande suivants lors de l’installation :

```bash
--stomp-host="<hostname>" --stomp-port="61613" --stomp-user="<user_name>" --stomp-password="<password>"
```

Où :

| Paramètre | Description |
|--- |--- |
| `--stomp-host` | Nom d’hôte sur lequel ActiveMQ est installé. |
| `--stomp-port` | Port à utiliser pour la connexion à ActiveMQ. La valeur par défaut est `61613`. |
| `--stomp-user` | Nom d’utilisateur pour la connexion à ActiveMQ. N’utilisez pas l’`artemis` utilisateur par défaut. |
| `--stomp-password` | Mot de passe de connexion à ActiveMQ. N’utilisez pas le mot de passe par défaut `artemis`. |
| `--stomp-ssl` | Indique s’il faut se connecter à ActiveMQ. La valeur par défaut est `false`. Si vous définissez la valeur sur true, consultez Configurer SSL pour plus d’informations. |

## Connecter les artéfacts ActiveMQ

Si vous disposez déjà d’une instance Adobe Commerce avec la configuration RabbitMQ (AMQP) dans le fichier `<install_directory>/app/etc/env.php` et que vous souhaitez la connecter à ActiveMQ, remplacez la section `queue` par le STOMP afin qu’elle soit similaire à ce qui suit :

```php
'queue' =>
  array (
    'stomp' =>
    array (
      'host' => 'activemq.example.com',
      'port' => '61613',  // SSL STOMP port (default 61617, non-SSL is 61613)
      'user' => 'magento',
      'password' => 'magento',
      // Performance tuning options
      'heartbeat_send' => 10000,     // 10 seconds // Optional
      'heartbeat_receive' => 10000,  // 10 seconds // Optional
      'read_timeout' => 250000       // 250ms // Optional
     ),
  ),
```

Vous pouvez également définir des valeurs de configuration ActiveMQ à l’aide de la commande `bin/magento setup:config:set` (supprimez la configuration AMQP si elle existe dans le fichier `app/etc/env.php`) :

```bash
bin/magento setup:config:set --stomp-host="activemq.example.com" --stomp-port="61613" --stomp-user="magento" --stomp-password="magento"
```

Après avoir exécuté la commande ou mis à jour le fichier `<install_directory>/app/etc/env.php` avec les valeurs de configuration STOMP, exécutez `bin/magento setup:upgrade` pour appliquer les modifications et créer les files d’attente requises dans ActiveMQ.

## Configurer SSL

Pour configurer la prise en charge de SSL, modifiez les paramètres `ssl` et `ssl_options` dans le fichier `<install_directory>/app/etc/env.php` afin qu’ils soient similaires aux paramètres suivants :

```php
'queue' =>
  array (
    'stomp' =>
    array (
      'host' => 'activemq.example.com',
      'port' => '61617',  // SSL STOMP port (default 61617, non-SSL is 61613)
      'user' => 'magento',
      'password' => 'magento',
      'ssl' => 'true',
      'ssl_options' => [
            'cafile' => '/etc/pki/tls/certs/DigiCertCA.crt',
            'local_cert' => '/path/to/magento/app/etc/ssl/test-activemq.crt', // Optional: Client certificate for mutual SSL
            'local_pk' => '/path/to/magento/app/etc/ssl/test-activemq.key', // Optional: Client private key for mutual SSL
            'passphrase' => 'client_key_password', // Optional: Passphrase for client private key
            'verify_peer' => true,
            'verify_peer_name' => true,
            'allow_self_signed' => false
       ],
      // Performance tuning options
      'heartbeat_send' => 10000,     // 10 seconds // Optional
      'heartbeat_receive' => 10000,  // 10 seconds // Optional
      'read_timeout' => 250000       // 250ms // Optional
     ),
  ),
```

### Options de configuration SSL

| Option | Description | Par défaut |
|--- |--- |--- |
| `verify_peer` | Vérifier le certificat SSL du courtier | `true` |
| `verify_peer_name` | Vérifiez que le nom d&#39;hôte du courtier correspond au certificat | `true` |
| `allow_self_signed` | Autoriser les certificats auto-signés | `false` |
| `cafile` | Chemin d&#39;accès au fichier de certificat CA pour la vérification du courtier | Requis pour SSL |
| `certfile` | Chemin d&#39;accès au fichier de certificat client (pour SSL mutuel) | Facultatif |
| `keyfile` | Chemin d&#39;accès au fichier de clé privée du client (pour SSL mutuel) | Facultatif |
| `passphrase` | Phrase secrète pour la clé privée du client | Facultatif |

### Configuration SSL de développement

Pour les environnements de développement, vous pouvez utiliser des paramètres SSL assouplis :

```php
'ssl_options' => [
    'verify_peer' => false,
    'verify_peer_name' => false,
    'allow_self_signed' => true
]
```

## Réglage des performances

ActiveMQ Artemis offre plusieurs options de réglage des performances :

```php
'queue' =>
  array (
    'stomp' =>
    array (
      'host' => 'activemq.example.com',
      'port' => '61613',
      'user' => 'artemis',
      'password' => 'artemis',
      // Performance options
      'heartbeat_send' => 10000,      // Send heartbeat every 10 seconds
      'heartbeat_receive' => 10000,   // Expect heartbeat every 10 seconds
      'read_timeout' => 250000,       // 250ms read timeout
     ),
  ),
```

## Surveillance et gestion

### Console web

ActiveMQ Artemis fournit une console de gestion web accessible à l’adresse suivante :
- URL : `http://localhost:8161/console`
- Informations d’identification par défaut : `artemis/artemis`

## Dépannage

### Problèmes courants

1. **Connexion refusée** : assurez-vous qu’ActiveMQ Artemis est en cours d’exécution et que l’accepteur STOMP est configuré.
1. **Échec de l’authentification** : vérifiez le nom d’utilisateur/mot de passe dans la configuration du courtier et dans le fichier `env.php`.
1. **Échec de l’établissement de la liaison SSL** : vérifiez les certificats SSL et la configuration.




### Vérifier la connexion STOMP

Testez la connexion STOMP à l&#39;aide de telnet :

```bash
telnet localhost 61613
```

Une connexion devrait être établie. Pour effectuer un test avec une commande STOMP :

```bash
# Test basic STOMP connection
echo -e "CONNECT\nhost:localhost\n\n\x00" | telnet localhost 61613
```

La sortie attendue doit afficher la connexion établie et la réponse du protocole STOMP.

## Démarrer les consommateurs et consommatrices de file d’attente de messages

Après avoir connecté Adobe Commerce et ActiveMQ Artemis, vous devez démarrer les consommateurs de file d’attente de messages. Voir [Configurer les files d’attente de messages](../../configuration/cli/start-message-queues.md) pour plus d’informations.

