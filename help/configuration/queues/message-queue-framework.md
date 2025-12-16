---
title: Présentation des files d’attente de messages
description: Découvrez le framework de file d’attente des messages et son fonctionnement avec l’application Adobe Commerce.
exl-id: 21e7bc3e-6265-4399-9d47-d3b9f03dfef6
source-git-commit: 7610a5843b526a765dd35188722b7be8e6051049
workflow-type: tm+mt
source-wordcount: '587'
ht-degree: 0%

---

# Présentation des files d’attente de messages

Le framework Message Queue (MQF) est un système qui permet à un module de publier des messages dans des files d’attente. Elle définit également les [consommateurs](consumers.md) qui recevront les messages de manière asynchrone. Le MQF prend en charge plusieurs courtiers de messagerie :

- **[[!DNL RabbitMQ]](https://www.rabbitmq.com)** - Courtier de messagerie principal, qui fournit une plateforme évolutive pour l&#39;envoi et la réception de messages. Il comprend un mécanisme de stockage des messages non diffusés et est basé sur la spécification AMQP (Advanced Message Queuing Protocol) 0.9.1 .
- **[Apache ActiveMQ Artemis](https://activemq.apache.org/components/artemis/)** - Un courtier de messagerie alternatif qui utilise le protocole STOMP (Simple Text Oriented Messaging Protocol) pour une messagerie fiable et évolutive. Introduit dans Adobe Commerce 2.4.5 et versions ultérieures.

## RabbitMQ (AMQP)

Le diagramme suivant illustre la structure de Message Queue :

![Structure de la file d’attente des messages](../../assets/configuration/mq-framework.png)

- Un éditeur est un composant qui envoie des messages à un échange. Il sait vers quel échange publier et le format des messages qu&#39;il envoie.

- Un central reçoit les messages des éditeurs et les envoie vers les files d&#39;attente. Bien que [!DNL RabbitMQ] prenne en charge plusieurs types d’échanges, Commerce utilise uniquement les échanges de sujets. Une rubrique comprend une clé de routage, qui contient des chaînes de texte séparées par des points. Le format d’un nom de rubrique est `string1.string2` : par exemple, `customer.created` ou `customer.sent.email`.

  Le courtier vous permet d’utiliser des caractères génériques lors de la définition de règles pour le transfert de messages. Vous pouvez utiliser un astérisque (`*`) pour remplacer _une_ chaîne ou un signe dièse (`#`) pour remplacer 0 ou plusieurs chaînes. Par exemple, `customer.*` filtrez sur `customer.create` et `customer.delete`, mais pas sur `customer.sent.email`. Toutefois, `customer.#` filtrez sur `customer.create`, `customer.delete` et `customer.sent.email`.

- Une file d&#39;attente est une mémoire tampon qui stocke les messages.

- Un client reçoit des messages. Il sait quelle file d’attente utiliser. Il peut mapper les processeurs du message à une file d’attente spécifique.

## Apache ActiveMQ Artemis (STOMP)

Au lieu de RabbitMQ, Adobe Commerce prend également en charge [Apache ActiveMQ Artemis](https://activemq.apache.org/components/artemis/) en tant que courtier de messagerie utilisant le protocole STOMP (Simple Text Oriented Messaging Protocol).

>[!NOTE]
>
>ActiveMQ Artemis a été introduit dans Adobe Commerce 2.4.5 et les versions ultérieures.

Le diagramme suivant illustre le framework STOMP avec les artéfacts ActiveMQ :

![Structure STOMP](../../assets/configuration/stomp-framework.png)

### Composants du framework STOMP

- Un **éditeur** est un composant qui envoie des messages vers une destination (file d’attente ou rubrique). Il sait vers quelle destination publier et le format des messages qu’il envoie.

- Une **destination** dans STOMP joue un rôle similaire aux échanges dans AMQP, en recevant les messages des éditeurs et en les acheminant. STOMP utilise l’adressage de destination direct avec un modèle de dénomination hiérarchique utilisant des points : par exemple, `customer.created` ou `inventory.updated`.

  Adobe Commerce utilise le mode d’adressage **ANYCAST** pour les destinations STOMP, qui permet la diffusion de messages point à point. En mode ANYCAST, les messages sont diffusés à un seul client à partir d’un pool de clients disponibles, ce qui permet l’équilibrage de charge et la distribution du travail sur plusieurs instances de clients.

- Une **file d’attente** est une mémoire tampon qui stocke les messages. Avec l’adressage ANYCAST, la file d’attente s’assure que les messages ne sont envoyés qu’à un seul client, même si plusieurs clients sont connectés à la même destination.

- Un **consommateur** reçoit des messages des destinations. Il sait à quelle destination s’abonner et peut traiter les messages avec différents modes d’accusé de réception (automatique, client ou client-individu).

## Adaptateur MySQL (secours)

Un système de file d&#39;attente de messages de base peut également être configuré sans utiliser de courtiers de messages externes. Dans ce système, un adaptateur MySQL stocke les messages dans la base de données. Trois tables de base de données (`queue`, `queue_message` et `queue_message_status`) gèrent la charge de travail de la file d&#39;attente des messages. Les tâches cron permettent aux consommateurs de recevoir des messages. Cette solution n&#39;est pas très évolutive. Les courtiers de messages externes tels que [!DNL RabbitMQ] ou Apache ActiveMQ Artemis doivent être utilisés chaque fois que cela est possible pour les environnements de production.

## Informations connexes

Pour les instructions d’installation et de configuration :

- [Installation et configuration de RabbitMQ](../../installation/prerequisites/rabbitmq.md)
- [Installation et configuration d’ActiveMQ Artemis](../../installation/prerequisites/activemq.md)
- [Gérer les files d&#39;attente de messages](manage-message-queues.md)
- [Consommateurs de file d’attente de messages](consumers.md)
