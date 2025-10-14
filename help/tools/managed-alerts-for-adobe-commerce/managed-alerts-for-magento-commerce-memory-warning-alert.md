---
title: 'Alertes gérées pour Adobe Commerce : alerte d’avertissement de mémoire'
description: Cet article décrit les étapes de dépannage à suivre lorsque vous recevez une alerte de mémoire pour Adobe Commerce dans  [!DNL New Relic]. Une action immédiate est nécessaire pour remédier au problème.
feature: Cache, Marketing Tools, Observability, Support, Tools and External Services
role: Admin
exl-id: 0910a431-bf2c-469e-81e2-92c8d9be3249
source-git-commit: 18c8e466bf15957b73cd3cddda8ff078ebeb23b0
workflow-type: tm+mt
source-wordcount: '770'
ht-degree: 0%

---

# Alertes gérées pour Adobe Commerce : alerte d’avertissement de mémoire

Cet article décrit les étapes de dépannage à suivre lorsque vous recevez une alerte de mémoire pour Adobe Commerce dans [!DNL New Relic]. Une action immédiate est nécessaire pour remédier au problème. L’alerte se présente comme suit, selon le canal de notification d’alerte que vous avez sélectionné.

![avertissement de mémoire](../../assets/managed-alerts/memory-warning-magento-managed.png){width="500"}

## Produits et versions concernés

Architecture de plan Pro d’Adobe Commerce sur les infrastructures cloud

## Problème

Vous recevrez une alerte en [!DNL New Relic] si vous vous êtes inscrit aux alertes [Gérées pour Adobe Commerce](managed-alerts-for-magento-commerce.md) et qu’un ou plusieurs seuils d’alerte ont été dépassés. Ces alertes ont été développées par Adobe Commerce pour fournir aux clients un ensemble de normes à l’aide des informations provenant des services d’assistance et d’ingénierie.

<u>**Do!**</u> :

* Il est recommandé d’abandonner tout déploiement planifié jusqu’à ce que cette alerte soit effacée.
* Mettez immédiatement votre site en mode de maintenance s’il ne répond plus du tout. Pour connaître les étapes, reportez-vous à la section [Activation ou désactivation du mode de maintenance](https://experienceleague.adobe.com/fr/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) dans le Guide d’installation de Commerce. Veillez à ajouter votre adresse IP à la liste des adresses IP exemptées pour vous assurer que vous pouvez toujours accéder à votre site à des fins de dépannage. Pour connaître les étapes, reportez-vous à la section [Tenir à jour la liste des adresses IP exemptées](https://experienceleague.adobe.com/fr/docs/commerce-operations/installation-guide/tutorials/maintenance-mode#maintain-the-list-of-exempt-ip-addresses) du Guide d’installation de Commerce.

<u>**Ne fais pas ça !**</u> :

* Lancez d’autres campagnes marketing qui peuvent apporter des pages vues supplémentaires à votre site.
* Exécutez des indexeurs ou des crons supplémentaires, ce qui peut entraîner une contrainte supplémentaire sur le CPU ou le disque.
* Effectuez toute tâche administrative majeure (à savoir, l’administration, les importations/exportations de données).
* Videz votre cache.

## Solution

Pour identifier et résoudre les problèmes, procédez comme suit.

1. Utilisez la page Infrastructure d’[[!DNL New Relic] APM](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/) pour identifier les processus les plus gourmands en mémoire. Pour connaître les étapes, consultez [[!DNL New Relic] [page Hôtes de surveillance de l’infrastructure : onglet [!UICONTROL Processes]]](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/#processes). Si des services tels que [!DNL Redis] ou MySQL sont la principale source de consommation de mémoire, essayez les méthodes suivantes :

   * Vérifiez que vous utilisez la dernière version. Les versions plus récentes peuvent parfois corriger les fuites de mémoire. Si vous n’utilisez pas la dernière version, envisagez d’effectuer une mise à niveau. Pour connaître les étapes, reportez-vous à la section [Services de modification](https://experienceleague.adobe.com/fr/docs/commerce-on-cloud/user-guide/configure/service/services-yaml) dans le guide de Commerce sur le cloud.
   * Si vous ne parvenez toujours pas à identifier la source de l’augmentation de la consommation de mémoire, recherchez les problèmes de MySQL tels que les requêtes longues, les clés de Principal non définies et les index en double. Pour connaître les étapes, reportez-vous à la section [Problèmes de base de données les plus courants dans Adobe Commerce sur l’infrastructure cloud](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/maintenance/resolve-database-performance-issues.html?lang=fr) dans le guide d’implémentation de Commerce.
   * S&#39;il n&#39;y a aucun problème MySQL, vérifiez les problèmes PHP. Examinez les processus en cours d’exécution en exécutant `ps aufx` dans l’interface de ligne de commande/Terminal. Dans la sortie du terminal, vous verrez les tâches et processus cron en cours d’exécution. Vérifiez la sortie pour le temps d’exécution des processus. S’il existe un fichier cron dont la durée d’exécution est longue, il est possible qu’il soit suspendu. Pour connaître les étapes de dépannage[&#x200B; reportez-vous aux sections &#x200B;](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/slow-performance-slow-and-long-running-crons)Performances lentes, crons lents et de longue exécution et [Traitement Cron bloqué à l’état « en cours d’exécution »](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-job-is-stuck-in-running-status) de la base de connaissances du support Commerce.

1. Si vous avez toujours du mal à identifier la source du problème, utilisez la page Transaction d’[[!DNL New Relic] APM](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems) pour identifier les transactions présentant des problèmes de performances :

   * Triez les transactions en fonction des scores [!DNL Apdex]. [[!DNL Apdex]](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/apdex-measure-user-satisfaction) fait référence à la satisfaction des utilisateurs quant au temps de réponse de vos applications et services web. Un [faible [!DNL Apdex] score](managed-alerts-for-magento-commerce-apdex-warning-alert.md) peut indiquer un goulot d’étranglement (une transaction avec un temps de réponse plus élevé). Habituellement, il s&#39;agit de la base de données, [!DNL Redis] ou PHP. Pour connaître les étapes, reportez-vous à la section New Relic [Afficher les transactions avec le niveau  [!DNL Apdex] ’insatisfaction le plus élevé](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/view-your-apdex-score#apdex-dissat).
   * Triez les transactions en fonction du débit le plus élevé, du temps de réponse moyen le plus lent, du temps le plus long et d’autres seuils. Pour connaître les étapes, reportez-vous à la section [[!DNL New Relic] Rechercher des problèmes de performances spécifiques](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems). Si vous avez toujours du mal à identifier le problème, utilisez la page Infrastructure d’[[!DNL New Relic] APM](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/).

1. Si vous ne pouvez pas identifier la cause de l’augmentation de la consommation de mémoire, passez en revue les tendances récentes pour identifier les problèmes liés aux récents déploiements de code ou aux modifications de configuration (par exemple, nouveaux groupes de clients et modifications importantes du catalogue). Il est recommandé de passer en revue les sept derniers jours d’activité pour toutes les corrélations dans les déploiements ou modifications de code.

1. Si les méthodes ci-dessus ne vous aident pas à trouver la cause et/ou la solution dans un délai raisonnable, demandez un upsize ou placez le site en mode de maintenance si vous ne l&#39;avez pas déjà fait. Pour connaître les étapes, reportez-vous aux sections [Comment demander un redimensionnement temporaire](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/how-to/how-to-request-temporary-magento-upsize) dans la base de connaissances de la prise en charge de Commerce et [Activer ou désactiver le mode de maintenance](https://experienceleague.adobe.com/fr/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) dans le guide d’installation de Commerce.

1. Si la mise à niveau revient au fonctionnement normal du site, envisagez de demander une mise à niveau permanente (contactez l’équipe de votre compte Adobe) ou essayez de reproduire le problème dans votre évaluation dédiée en exécutant un test de charge et en optimisant les requêtes, ou un code qui réduit la pression sur les services. Reportez-vous à la section [Tests de charge et de contrainte](https://experienceleague.adobe.com/fr/docs/commerce-cloud-service/user-guide/develop/test/staging-and-production#load-and-stress-testing) du guide Commerce sur le cloud .
