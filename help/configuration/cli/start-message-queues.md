---
title: Démarrage des consommateurs de la file de messages
description: Découvrez comment démarrer un consommateur de file d’attente de messages.
exl-id: fd6edb24-8ebe-4b67-8a03-6cc759b60fa8
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '189'
ht-degree: 0%

---

# Démarrage des consommateurs de la file de messages

{{file-system-owner}}

Vous devez commencer une [client de la file d&#39;attente de messages](../queues/consumers.md) pour activer les opérations asynchrones telles que les actions de masse Inventory management et les points de terminaison REST en masse et asynchrones. Pour activer la fonctionnalité B2B, vous devez démarrer plusieurs consommateurs. Les modules tiers peuvent également nécessiter le démarrage d’un consommateur personnalisé.

Pour afficher la liste de tous les consommateurs :

```bash
bin/magento queue:consumers:list
```

Pour démarrer les consommateurs de la file d’attente des messages :

```bash
bin/magento queue:consumers:start [--max-messages=<value>] [--batch-size=<value>] [--single-thread] [--area-code=<value>] [--multi-process=<value>] <consumer_name>
```

Après avoir consommé tous les messages disponibles, la commande s’arrête. Vous pouvez exécuter à nouveau la commande manuellement ou avec une tâche cron. Vous pouvez également exécuter plusieurs instances de la variable `magento queue:consumers:start` pour traiter les files d’attente de messages volumineuses. Par exemple, vous pouvez ajouter `&` à la commande pour l’exécuter en arrière-plan, revenez à une invite et continuez à exécuter les commandes :

```bash
bin/magento queue:consumers:start <consumer_name> &
```

Voir [queue:consumers:start](https://devdocs.magento.com/guides/v2.4/reference/cli/magento-commerce.html#queueconsumersstart) dans la section Commerce du _Référence des outils de ligne de commande_ pour plus d’informations sur les options de commande, les paramètres et les valeurs.

>[!INFO]
>
>La variable `--multi-process` est présente dans la variable `queue:consumers:start` mais pour exécuter des consommateurs avec des processus parallèles, configurez la variable [`multiple_processes`](../queues/manage-message-queues.md#configuration) dans `/app/etc/env.php`. Sinon, si `queue:consumers:start` est appelé avec la fonction `--multi-process` , il ne fonctionne que sur un seul thread.
