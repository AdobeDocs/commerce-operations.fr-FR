---
title: '"Le [!UICONTROL RabbitMQ] tab"'
description: En savoir plus sur les [!UICONTROL RabbitMQ] de [!DNL Observation for Adobe Commerce].
source-git-commit: 3f2a401bb916fc04405f21ba2acfc42f7defdccb
workflow-type: tm+mt
source-wordcount: '570'
ht-degree: 0%

---

# Le [!UICONTROL RabbitMQ] tab

Le **[!UICONTROL RabbitMQ]** contient des informations ciblées sur [!DNL RabbitMQ] signaux.

## [!UICONTROL RabbitMQ Infrastructure events]

![Événements d’infrastructure RabbitMQ](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-1.jpeg)

Le **[!UICONTROL RabbitMQ Infrastructure events]** Le cadre affiche les événements d’infrastructure qui impliquent [!DNL RabbitMQ] qui s’est produit au cours de la période sélectionnée :

* %Response [error] pour le noeud [rabbit@host1]: réponse http inattendue de %) comme &quot;inattendu_resp_node1&quot;
* &#39;%Response [error] pour le noeud [rabbit@host2]: réponse http inattendue de%) en tant que &quot;inattendu_resp_node2&quot;
* &#39;%Response [error] pour le noeud [rabbit@host3]: réponse http inattendue de %) en tant que &quot;inattendu_resp_node3&quot;
* &#39;%Response [error] pour le noeud [rabbit@host3]: Obtenir &quot;http://localhost:15672/api/healthchecks/node/rabbit@host3&quot; : contexte d’échéance dépassée%) en tant que &quot;node3_timeout_exceeded&quot;
* &#39;%Response [error] pour le noeud [rabbit@host1]: Obtenir &quot;http://localhost:15672/api/healthchecks/node/rabbit@host1&quot; : date limite du contexte dépassée %) en tant que &quot;node1_timeout_exceeded&quot;
* &#39;%Response [error] pour le noeud [rabbit@host2]: Obtenir &quot;http://localhost:15672/api/healthchecks/node/rabbit@host2&quot; : contexte d’échéance dépassée%) en tant que &quot;node2_timeout_exceeded&quot;
* &quot;%401 Unauthorized%&quot;) comme &quot;401_unauth&quot;
* &quot;%401 Unauthorized%&quot;) comme &quot;401_unauth&quot;
* %Service redémarré : rabbmq-server%) en tant que &quot;rmq_service_restart&quot;
* &#39;%Response [failed] pour le noeud [rabbit@host1]: nodedown%) comme &quot;rmq_node1_down&quot;
* &#39;%Response [failed] pour le noeud [rabbit@host2]: nodedown%) comme &quot;rmq_node2_down&quot;
* &#39;%Response [failed] pour le noeud [rabbit@host2]: nodedown%) comme &quot;rmq_node2_down&quot;
* &#39;%Entity modifié : exchange/bindings.destination%) comme &quot;rmq_entity_modified&quot;
* &#39;%Entity modifié : exchange/bindings.destination%) comme &quot;rmq_entity_modified&quot;
* &#39;%Entity modifié : queue/exclusive%) comme &quot;rmq_entity_created_q_exclusive&quot;%Entité modifiée : queue/auto_delete%) comme &quot;rmq_entity_q_delete&quot;
* &#39;%Entity modifié : queue/durable%) comme &quot;rmq_entity_modified_q_durable&quot;
* &#39;%Entity modifié : version/management%) en tant que &quot;rmq_entity_modified_ver_mgt&quot;
* &#39;%Entity modifié : version/management%) en tant que &quot;rmq_entity_modified_ver_mgt&quot;

## [!UICONTROL RabbitMQ service start/stop signals]

![Signaux de démarrage/arrêt du service RabbitMQ](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-2.jpeg)

Ce cadre affiche : [!DNL RabbitMQ] signaux de démarrage/arrêt du service qui se sont produits pendant la période sélectionnée :

* &quot;%RabbitMQ doit s’arrêter...%&#39;) comme &quot;rabbitmq_stop&quot;
* &quot;%Start RabbitMQ%&quot;) en tant que &quot;rabbitmq_start&quot;

## [!UICONTROL RabbitMQ errors]

![Erreurs RabbitMQ](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-3.jpeg)

Ce cadre affiche : [!DNL RabbitMQ] erreurs qui se sont produites au cours de la période sélectionnée :

* &#39;%exit avec la raison {case_clause,timeout} et stacktrace {rabbit_mgmt_wm_healthchecks%&#39;} comme &#39;exit_timeout&#39;
* &quot;%client a fermé la connexion TCP de manière inattendue&quot;) en tant que &quot;client_closed_tcp_conn&quot;
* &#39;%à la sortie non définie avec la raison arrêtée dans le contexte shutdown_error%&#39;) comme &#39;undef_exit&#39;
* &quot;%Tentative de connexion à partir du noeud interdit%&quot;) comme &quot;disallowed_node&quot;
* &quot;%fermeture de la connexion AMQP%&quot;) en tant que &quot;rmq_err_amqp_conn&quot;

## [!UICONTROL RabbitMQ node status]

![État du noeud RabbitMQ](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-4.jpeg)

* &quot;%rabbit sur le noeud rabbit@host1 down%&quot;) comme &quot;rmq_node1_down&quot;
* ’%rabbit sur le noeud rabbit@host2 down%’) en tant que ’rmq_node2_down’
* ’%rabbit sur le noeud rabbit@host3 down%’) en tant que ’rmq_node3_down’
* &quot;%rabbit sur le noeud rabbit@host1 up%&quot;) en tant que &quot;rmq_node1_up&quot;
* &quot;%rabbit sur le noeud rabbit@host2 up%&quot;) en tant que &quot;rmq_node2_up&quot;
* &quot;%rabbit sur le noeud rabbit@host3 up%&quot;) en tant que &quot;rmq_node3_up&quot;

## [!UICONTROL RabbitMQ Message High-Level Summary status by Queue]

![État du résumé de haut niveau du message RabbitMQ par file d’attente](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-5.jpeg)

Le **[!UICONTROL RabbitMQ Message High-Level Summary status by Queue]** Le graphique affiche le nombre de messages publiés par la variable [!DNL RabbitMQ] file d’attente pour la période sélectionnée.

## [!UICONTROL RabbitMQ Message Detail Summary]

![Résumé des détails du message RabbitMQ](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-6.jpeg)

* ’%report.ERROR: Cron Job consumer_runner a une erreur : NOT_FOUND - no queue%) as &#39;queue_err&#39;
* ’%report.ERROR: Cron Job consumer_runner a une erreur : NOT_FOUND - no queue%) as &#39;queue_err&#39;
* ’%authentifié et accordé l’accès à vhost%’) en tant que &#39;auth&#39;
* &#39;%fermeture de la connexion AMQP%&#39;) comme &#39;close_conn&#39;

## [!UICONTROL RabbitMQ Queue Consumption MB]

![MQ Consommation de la file d’attente RabbitMQ (Mo)](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-7.jpeg)

Le **[!UICONTROL RabbitMQ Queue Consumption MB]** Le graphique indique le nombre d’octets consommés par chaque [!DNL RabbitMQ] placer la file d’attente sur la période sélectionnée.

## [!UICONTROL RabbitMQ Published Messages by Queue]

![Messages publiés par RabbitMQ par file d’attente](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-8.jpeg)

Le **[!UICONTROL RabbitMQ Published Messages by Queue]** Le graphique indique le nombre d’octets consommés par chaque [!DNL RabbitMQ] placer la file d’attente sur la période sélectionnée.

## [!UICONTROL RabbitMQ Published Message Throughput by Queue]

![Débit des messages publiés sur RabbitMQ par file d’attente](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-9.jpeg)

Le **[!UICONTROL RabbitMQ Published Message Throughput by Queue]** Le graphique indique le nombre moyen de messages publiés par seconde pour chaque [!DNL RabbitMQ] placer la file d’attente sur la période sélectionnée.

## [!UICONTROL RabbitMQ Total Message Throughput by Queue]

![Débit total des messages RabbitMQ par file d’attente](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-10.jpeg)

Le **[!UICONTROL RabbitMQ Total Message Throughput by Queue]** Le graphique indique le nombre total moyen de messages par seconde pour chaque [!DNL RabbitMQ] placer la file d’attente sur la période sélectionnée.

## [!UICONTROL RabbitMQ Consumers by Queue]

![Consommateurs RabbitMQ par file d’attente](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-11.jpeg)

Le **[!UICONTROL RabbitMQ Consumers by Queue]** Le graphique montre le nombre total moyen de consommateurs par chaque [!DNL RabbitMQ] placer la file d’attente sur la période sélectionnée.
