---
title: La variable [!UICONTROL [!DNL RabbitMQ]Onglet ]
description: En savoir plus sur les [!UICONTROL [!DNL RabbitMQ]] onglet de [!DNL Observation for Adobe Commerce].
exl-id: c5370c30-fed8-4f45-89c3-ef0d6ad41a89
feature: Configuration, Observability
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '225'
ht-degree: 0%

---

# La variable [!UICONTROL [!DNL RabbitMQ]] tab

La variable **[!UICONTROL [!DNL RabbitMQ]]** contient des informations ciblées sur [!DNL RabbitMQ] les signaux.

## [!UICONTROL [!DNL RabbitMQ] Infrastructure events]

![[!DNL RabbitMQ] Événements d’infrastructure](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-1.jpeg)

La variable **[!UICONTROL [!DNL RabbitMQ] Infrastructure events]** Le cadre affiche les événements d’infrastructure qui impliquent [!DNL RabbitMQ] qui s’est produit pendant la période sélectionnée :

* `%Response [error] for node [rabbit@host1]: unexpected http response from%`) as `unexpected_resp_node1`
* `%Response [error] for node [rabbit@host2]: unexpected http response from%`) as `unexpected_resp_node2`
* `%Response [error] for node [rabbit@host3]: unexpected http response from%`) as `unexpected_resp_node3`
* `%Response [error] for node [rabbit@host3]: Get "http://localhost:15672/api/healthchecks/node/rabbit@host3": context deadline exceeded%`) as `node3_timeout_exceeded`
* `%Response [error] for node [rabbit@host1]: Get "http://localhost:15672/api/healthchecks/node/rabbit@host1": context deadline exceeded%`) as `node1_timeout_exceeded`
* `%Response [error] for node [rabbit@host2]: Get "http://localhost:15672/api/healthchecks/node/rabbit@host2": context deadline exceeded%`) as `node2_timeout_exceeded`
* `%401 Unauthorized%`) as `401_unauth`
* `%401 Unauthorized%`) as `401_unauth`
* `%Service restarted: rabbitmq-server%`) as `rmq_service_restart`
* `%Response [failed] for node [rabbit@host1]: nodedown%`) as `rmq_node1_down`
* `%Response [failed] for node [rabbit@host2]: nodedown%`) as `rmq_node2_down`
* `%Response [failed] for node [rabbit@host2]: nodedown%`) as `rmq_node2_down`
* `%Entity modified: exchange/bindings.destination%`) as `rmq_entity_modified`
* `%Entity modified: exchange/bindings.destination%`) as `rmq_entity_modified`
* `%Entity modified: queue/exclusive%`) as `rmq_entity_created_q_exclusive` `%Entity modified: queue/auto_delete%`) as `rmq_entity_q_delete`
* `%Entity modified: queue/durable%`) as `rmq_entity_modified_q_durable`
* `%Entity modified: version/management%`) as `rmq_entity_modified_ver_mgt`
* `%Entity modified: version/management%`) as `rmq_entity_modified_ver_mgt`

## [!UICONTROL [!DNL RabbitMQ] service start/stop signals]

![[!DNL RabbitMQ] signaux de démarrage et d’arrêt du service](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-2.jpeg)

Ce cadre affiche : [!DNL RabbitMQ] signaux de démarrage/arrêt du service qui se sont produits pendant la période sélectionnée :

* `%RabbitMQ is asked to stop...%`) as `rabbitmq_stop`
* `%Starting RabbitMQ%`) as `rabbitmq_start`

## [!UICONTROL [!DNL RabbitMQ] errors]

![[!DNL RabbitMQ] errors](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-3.jpeg)

Ce cadre affiche : [!DNL RabbitMQ] erreurs qui se sont produites au cours de la période sélectionnée :

* `%exit with reason {case_clause,timeout} and stacktrace {rabbit_mgmt_wm_healthchecks%}` as `exit_timeout`
* `%client unexpectedly closed TCP connection%`) as `client_closed_tcp_conn`
* `%at undefined exit with reason shutdown in context shutdown_error%`) as `undef_exit`
* `%Connection attempt from disallowed node%`) as `disallowed_node`
* `%closing AMQP connection%`) as `rmq_err_amqp_conn`

## [!UICONTROL [!DNL RabbitMQ] node status]

![[!DNL RabbitMQ] état du noeud](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-4.jpeg)

* `%rabbit on node rabbit@host1 down%`) as `rmq_node1_down`
* `%rabbit on node rabbit@host2 down%`) as `rmq_node2_down`
* `%rabbit on node rabbit@host3 down%`) as `rmq_node3_down`
* `%rabbit on node rabbit@host1 up%`) as `rmq_node1_up`
* `%rabbit on node rabbit@host2 up%`) as `rmq_node2_up`
* `%rabbit on node rabbit@host3 up%`) as `rmq_node3_up`

## [!UICONTROL [!DNL RabbitMQ] Message High-Level Summary status by Queue]

![[!DNL RabbitMQ] État du résumé de haut niveau du message par file d’attente](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-5.jpeg)

La variable **[!UICONTROL [!DNL RabbitMQ] Message High-Level Summary status by Queue]** Le graphique affiche le nombre de messages publiés par la variable [!DNL RabbitMQ] file d’attente pour la période sélectionnée.

## [!UICONTROL [!DNL RabbitMQ] Message Detail Summary]

![[!DNL RabbitMQ] Résumé des détails du message](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-6.jpeg)

* `%report.ERROR: Cron Job consumers_runner has an error: NOT_FOUND - no queue%`) as `queue_err`
* `%report.ERROR: Cron Job consumers_runner has an error: NOT_FOUND - no queue%`) as `queue_err`
* `%authenticated and granted access to vhost%`) as `auth`
* `%closing AMQP connection%`) as `close_conn`

## [!UICONTROL [!DNL RabbitMQ] Queue Consumption MB]

![[!DNL RabbitMQ] Mo de consommation de la file d’attente](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-7.jpeg)

La variable **[!UICONTROL [!DNL RabbitMQ] Queue Consumption MB]** Le graphique indique le nombre d’octets consommés par chaque [!DNL RabbitMQ] placer la file d’attente sur la période sélectionnée.

## [!UICONTROL [!DNL RabbitMQ] Published Messages by Queue]

![[!DNL RabbitMQ] Messages publiés par file d’attente](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-8.jpeg)

La variable **[!UICONTROL [!DNL RabbitMQ] Published Messages by Queue]** Le graphique indique le nombre d’octets consommés par chaque [!DNL RabbitMQ] placer la file d’attente sur la période sélectionnée.

## [!UICONTROL [!DNL RabbitMQ] Published Message Throughput by Queue]

![[!DNL RabbitMQ] Débit des messages publiés par file d’attente](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-9.jpeg)

La variable **[!UICONTROL [!DNL RabbitMQ] Published Message Throughput by Queue]** Le graphique indique le nombre moyen de messages publiés par seconde pour chaque [!DNL RabbitMQ] placer la file d’attente sur la période sélectionnée.

## [!UICONTROL [!DNL RabbitMQ] Total Message Throughput by Queue]

![[!DNL RabbitMQ] Débit total des messages par file d’attente](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-10.jpeg)

La variable **[!UICONTROL [!DNL RabbitMQ] Total Message Throughput by Queue]** Le graphique indique le nombre total moyen de messages par seconde pour chaque [!DNL RabbitMQ] placer la file d’attente sur la période sélectionnée.

## [!UICONTROL [!DNL RabbitMQ] Consumers by Queue]

![[!DNL RabbitMQ] Consommateurs par file d’attente](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-11.jpeg)

La variable **[!UICONTROL [!DNL RabbitMQ] Consumers by Queue]** Le graphique montre le nombre total moyen de consommateurs par chaque [!DNL RabbitMQ] placer la file d’attente sur la période sélectionnée.
