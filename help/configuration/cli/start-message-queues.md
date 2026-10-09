---
title: Démarrer les consommateurs des files d’attente de messages
description: Découvrez comment démarrer les consommateurs de files d’attente de messages pour les opérations asynchrones Adobe Commerce. Découvrez la configuration des fonctionnalités de gestion des consommateurs et B2B.
exl-id: fd6edb24-8ebe-4b67-8a03-6cc759b60fa8
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '191'
ht-degree: 0%
---
# Démarrer les consommateurs des files d’attente de messages

{{file-system-owner}}

Vous devez démarrer un [client de file d’attente de messages](../queues/consumers.md) pour activer les opérations asynchrones telles que les actions en masse d’Inventory management et les points d’entrée REST en bloc et asynchrones. Pour activer la fonctionnalité B2B, vous devez démarrer plusieurs consommateurs. Des modules tiers peuvent également nécessiter le démarrage d’un client personnalisé.

Pour afficher la liste de tous les consommateurs :

```shell
bin/magento queue:consumers:list
```

Pour démarrer les consommateurs de files d’attente de messages :

```shell
bin/magento queue:consumers:start [--max-messages=<value>] [--batch-size=<value>] [--single-thread] [--area-code=<value>] [--multi-process=<value>] <consumer_name>
```

Après avoir consommé tous les messages disponibles, la commande s’arrête. Vous pouvez réexécuter la commande manuellement ou avec une tâche cron. Vous pouvez également exécuter plusieurs instances de la commande `magento queue:consumers:start` pour traiter les files d’attente de messages volumineuses. Par exemple, vous pouvez ajouter `&` à la commande pour l’exécuter en arrière-plan, revenir à une invite et continuer à exécuter les commandes :

```shell
bin/magento queue:consumers:start <consumer_name> &
```

Voir [`queue:consumers:start`](../../tools/reference/commerce-on-premises.md#queueconsumersstart) dans la section Commerce du guide de référence des _outils de ligne de commande_ pour plus d’informations sur les options de commande, les paramètres et les valeurs.

>[!INFO]
>
>L’option `--multi-process` est présente dans la commande `queue:consumers:start`, mais pour exécuter des consommateurs avec des processus parallèles, configurez l’option [`multiple_processes`](../queues/manage-message-queues.md#configuration) dans `/app/etc/env.php`. Sinon, si `queue:consumers:start` est appelé avec l’option `--multi-process` , il ne fonctionne que sur un seul thread.
