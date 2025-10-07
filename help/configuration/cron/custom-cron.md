---
title: Traitements cron
description: Découvrez les groupes cron et comment créer des tâches cron personnalisées dans Adobe Commerce. Découvrez la configuration des tâches planifiées et la configuration du groupe cron.
exl-id: a9d83af7-9979-4653-adc9-30ffeb13a5ce
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '167'
ht-degree: 0%

---

# Traitements cron

Ces rubriques expliquent comment configurer une tâche cron personnalisée et, éventuellement, un groupe cron personnalisé. Si votre extension Commerce nécessite l’exécution périodique de tâches planifiées, vous pouvez utiliser ces rubriques pour configurer un cron _job_ (la tâche planifiée) et éventuellement un cron _group_, qui exécute des tâches personnalisées en même temps.

Si vous utilisez un groupe cron fourni par Commerce, vous n’avez pas à définir de groupe cron personnalisé. Cependant, si vous souhaitez que vos tâches cron s’exécutent selon un planning différent ou qu’elles s’exécutent toutes ensemble, vous devez définir un groupe cron

L’application Commerce fournit les groupes cron suivants :

- `default`, qui contient la plupart des tâches cron
- `index`, qui actualise les [indexeurs](../cli/manage-indexers.md)
- `consumers`, qui exécute la file d’attente de messages [consommateurs](../cli/start-message-queues.md)
- Ces rubriques sont disponibles dans Adobe Commerce uniquement
   - `staging`, qui exécute [&#x200B; tâches liées à l’évaluation &#x200B;](https://experienceleague.adobe.com/fr/docs/commerce-admin/content-design/staging/content-staging)
   - `catalog_event`, qui exécute des tâches pour les règles de cible et de panier
