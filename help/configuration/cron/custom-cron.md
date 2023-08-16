---
title: Tâches Cron
description: Découvrez les groupes cron et la création d’une tâche cron personnalisée.
exl-id: a9d83af7-9979-4653-adc9-30ffeb13a5ce
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '159'
ht-degree: 0%

---

# Tâches Cron

Ces rubriques expliquent comment configurer une tâche cron personnalisée et éventuellement un groupe cron personnalisé. Si votre extension Commerce requiert des tâches planifiées à exécuter périodiquement, vous pouvez utiliser ces rubriques pour configurer un cron. _job_ (la tâche planifiée) et éventuellement un cron _group_, qui exécute des tâches personnalisées en même temps.

Si vous utilisez un groupe cron fourni par Commerce, vous n’avez pas à définir un groupe cron personnalisé. Toutefois, si vous souhaitez que vos tâches cron s’exécutent selon un autre planning ou si vous souhaitez qu’elles s’exécutent toutes ensemble, vous devez définir un groupe cron.

L’application Commerce fournit les groupes cron suivants :

- `default`, qui contient la plupart des tâches cron
- `index`, qui actualise [indexeurs](../cli/manage-indexers.md)
- `consumers`, qui exécute la file des messages [consommateurs](../cli/start-message-queues.md)
- Ces rubriques sont disponibles dans Adobe Commerce uniquement
   - `staging`, qui exécute [Lié à l’évaluation](https://docs.magento.com/user-guide/cms/content-staging.html) tâches
   - `catalog_event`, qui exécute les tâches pour les règles de ciblage et de panier
