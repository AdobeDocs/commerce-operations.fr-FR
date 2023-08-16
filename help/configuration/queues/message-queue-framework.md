---
title: Présentation des files de messages
description: Découvrez la structure de la file d’attente des messages et son fonctionnement avec l’application Adobe Commerce et Magento Open Source.
exl-id: 21e7bc3e-6265-4399-9d47-d3b9f03dfef6
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 0%

---

# Présentation des files d’attente de messages

Le Message Queue Framework (MQF) est un système qui permet à un module de publier des messages dans les files d’attente. Il définit également la variable [consommateurs](consumers.md) qui recevront les messages de manière asynchrone. Le MQF utilise [[!DNL RabbitMQ]](https://www.rabbitmq.com) en tant que courtier de messagerie, qui fournit une plateforme évolutive pour l’envoi et la réception de messages. Il comprend également un mécanisme de stockage des messages non diffusés. [!DNL RabbitMQ] est basé sur la spécification AMQP 0.9.1 du protocole Advanced Message Queuing Protocol (AMQP).

Le diagramme suivant illustre la structure de la file d’attente des messages :

![Structure de la file d’attente des messages](../../assets/configuration/mq-framework.png)

- Un éditeur est un composant qui envoie des messages à un échange. Il connaît l’échange vers lequel publier et le format des messages qu’il envoie.

- Un échange reçoit les messages des éditeurs et les envoie aux files d’attente. Bien que [!DNL RabbitMQ] prend en charge plusieurs types d’échanges, Commerce utilise uniquement les échanges de rubrique. Une rubrique comprend une clé de routage, qui contient des chaînes de texte séparées par des points. Le format du nom d’une rubrique est le suivant : `string1.string2`: par exemple, `customer.created` ou `customer.sent.email`.

  Le courtier vous permet d’utiliser des caractères génériques lors de la définition de règles pour le transfert de messages. Vous pouvez utiliser un astérisque (`*`) à remplacer. _one_ Chaîne ou signe dièse (`#`) pour remplacer 0 ou plusieurs chaînes. Par exemple : `customer.*` filtre sur `customer.create` et `customer.delete`, mais pas `customer.sent.email`. Cependant `customer.#` filtre sur `customer.create`,  `customer.delete`, et `customer.sent.email`.

- Une file d’attente est une mémoire tampon qui stocke les messages.

- Un consommateur reçoit des messages. Il sait quelle file d&#39;attente utiliser. Il peut mapper les processeurs du message à une file d’attente spécifique.

Un système de file d’attente de messages de base peut également être configuré sans utiliser [!DNL RabbitMQ]. Dans ce système, un adaptateur MySQL stocke les messages dans la base de données. Trois tables de base de données (`queue`, `queue_message`, et `queue_message_status`) gérer la charge de travail de la file d’attente des messages. Les tâches Cron permettent aux consommateurs de recevoir des messages. Cette solution n’est pas très évolutive. [!DNL RabbitMQ] doit être utilisé dans la mesure du possible.
