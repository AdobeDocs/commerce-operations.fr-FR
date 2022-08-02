---
title: Tâches Cron
description: Découvrez les groupes cron et la création d’une tâche cron personnalisée.
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '159'
ht-degree: 0%

---


# Tâches Cron

Ces rubriques expliquent comment configurer une tâche cron personnalisée et éventuellement un groupe cron personnalisé. Si votre extension Commerce requiert des tâches planifiées à exécuter périodiquement, vous pouvez utiliser ces rubriques pour configurer un cron. _job_ (la tâche planifiée) et éventuellement un cron _group_, qui exécute simultanément des tâches personnalisées.

Si vous utilisez un groupe cron fourni par Commerce, il n’est pas nécessaire de définir un groupe cron personnalisé ; toutefois, si vous souhaitez que vos tâches cron s’exécutent selon un autre planning ou que vous souhaitez qu’elles s’exécutent toutes ensemble, vous devez définir un groupe cron .

L’application Commerce fournit les groupes cron suivants :

- `default`, qui contient la plupart des tâches cron
- `index`, qui actualise [indexeurs](../cli/manage-indexers.md)
- `consumers`, qui exécute la file d’attente des messages [consommateurs](../cli/start-message-queues.md)
- Ces rubriques sont disponibles dans Adobe Commerce uniquement
   - `staging`, qui s’exécute [Intermédiaire](https://docs.magento.com/user-guide/cms/content-staging.html) tâches
   - `catalog_event`, qui exécute les tâches pour les règles de ciblage et de panier
