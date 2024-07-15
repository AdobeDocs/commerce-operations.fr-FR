---
title: Démarrage des consommateurs de la file de messages
description: Découvrez comment démarrer un consommateur de file d’attente de messages.
exl-id: fd6edb24-8ebe-4b67-8a03-6cc759b60fa8
source-git-commit: cdd752532d17e1168e0aa7d354ec283089d98be3
workflow-type: tm+mt
source-wordcount: '178'
ht-degree: 0%

---

# Démarrage des consommateurs de la file de messages

{{file-system-owner}}

Vous devez démarrer un [consommateur de file de messages](../queues/consumers.md) pour activer les opérations asynchrones telles que les actions de masse Inventory management et les points de terminaison REST en masse et asynchrones. Pour activer la fonctionnalité B2B, vous devez démarrer plusieurs consommateurs. Les modules tiers peuvent également nécessiter le démarrage d’un consommateur personnalisé.

Pour afficher la liste de tous les consommateurs :

```bash
bin/magento queue:consumers:list
```

Pour démarrer les consommateurs de la file d’attente des messages :

```bash
bin/magento queue:consumers:start [--max-messages=<value>] [--batch-size=<value>] [--single-thread] [--area-code=<value>] [--multi-process=<value>] <consumer_name>
```

Après avoir consommé tous les messages disponibles, la commande s’arrête. Vous pouvez exécuter à nouveau la commande manuellement ou avec une tâche cron. Vous pouvez également exécuter plusieurs instances de la commande `magento queue:consumers:start` pour traiter les files d’attente de messages volumineuses. Par exemple, vous pouvez ajouter `&` à la commande pour l’exécuter en arrière-plan, revenir à une invite et continuer à exécuter les commandes :

```bash
bin/magento queue:consumers:start <consumer_name> &
```

Pour plus d’informations sur les options de commande, les paramètres et les valeurs, voir [`queue:consumers:start`](../../tools/reference/commerce-on-premises.md#queueconsumersstart) dans la section Commerce de la _référence des outils de ligne de commande_.

>[!INFO]
>
>L’option `--multi-process` est présente dans la commande `queue:consumers:start`, mais pour exécuter les consommateurs avec des processus parallèles, configurez l’option [`multiple_processes`](../queues/manage-message-queues.md#configuration) dans `/app/etc/env.php`. Sinon, si `queue:consumers:start` est appelé avec l’option `--multi-process`, il ne fonctionne que sur un seul thread.
