---
title: Présentation des files de messages
description: Découvrez la structure de la file d’attente des messages et son fonctionnement avec l’application Adobe Commerce.
exl-id: 21e7bc3e-6265-4399-9d47-d3b9f03dfef6
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 0%

---

# Présentation des files d’attente de messages

Le Message Queue Framework (MQF) est un système qui permet à un module de publier des messages dans les files d’attente. Il définit également les [consommateurs](consumers.md) qui recevront les messages de manière asynchrone. Le MQF utilise [[!DNL RabbitMQ]](https://www.rabbitmq.com) comme courtier de messagerie, qui fournit une plateforme évolutive pour l’envoi et la réception de messages. Il comprend également un mécanisme de stockage des messages non diffusés. [!DNL RabbitMQ] est basé sur la spécification AMQP (Advanced Message Queuing Protocol) 0.9.1.

Le diagramme suivant illustre la structure de la file d’attente des messages :

![Message Queue Framework](../../assets/configuration/mq-framework.png)

- Un éditeur est un composant qui envoie des messages à un exchange. Il connaît l’exchange vers lequel publier et le format des messages qu’il envoie.

- Un exchange reçoit les messages des éditeurs et les envoie aux files d’attente. Bien que [!DNL RabbitMQ] prenne en charge plusieurs types d’exchanges, Commerce utilise uniquement les exchanges de rubrique. Une rubrique comprend une clé de routage, qui contient des chaînes de texte séparées par des points. Le format d’un nom de rubrique est `string1.string2` : par exemple, `customer.created` ou `customer.sent.email`.

  Le courtier vous permet d’utiliser des caractères génériques lors de la définition de règles pour le transfert de messages. Vous pouvez utiliser un astérisque (`*`) pour remplacer une chaîne _one_ ou un signe dièse (`#`) pour remplacer 0 ou plusieurs chaînes. Par exemple, `customer.*` filtre sur `customer.create` et `customer.delete`, mais pas `customer.sent.email`. Cependant, `customer.#` filtrerait sur `customer.create`, `customer.delete` et `customer.sent.email`.

- Une file d’attente est une mémoire tampon qui stocke les messages.

- Un consommateur reçoit des messages. Il sait quelle file d&#39;attente utiliser. Il peut mapper les processeurs du message à une file d’attente spécifique.

Un système de file d’attente de messages de base peut également être configuré sans utiliser [!DNL RabbitMQ]. Dans ce système, un adaptateur MySQL stocke les messages dans la base de données. Trois tables de base de données (`queue`, `queue_message` et `queue_message_status`) gèrent la charge de travail de la file d’attente des messages. Les tâches Cron permettent aux consommateurs de recevoir des messages. Cette solution n’est pas très évolutive. [!DNL RabbitMQ] doit être utilisé dans la mesure du possible.
