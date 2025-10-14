---
title: 'Alertes gérées pour Adobe Commerce : alerte critique [!DNL Apdex] '
description: Cet article décrit les étapes de dépannage à suivre lorsque vous recevez une alerte  [!DNL Apdex]  critique pour Adobe Commerce in [!DNL New Relic]. The [!DNL Apdex] score qui évalue la satisfaction des utilisateurs quant au temps de réponse des applications et services web. Une action immédiate est nécessaire pour remédier au problème.
feature: Cache, Marketing Tools, Observability, Support, Tools and External Services
role: Admin
exl-id: 00e29611-fd4b-45c8-a1e0-56fc3cbe90e0
source-git-commit: 18c8e466bf15957b73cd3cddda8ff078ebeb23b0
workflow-type: tm+mt
source-wordcount: '926'
ht-degree: 0%

---

# Alertes gérées pour Adobe Commerce : alerte critique [!DNL Apdex]

Cet article décrit les étapes de dépannage à suivre lorsque vous recevez une alerte critique [!DNL Apdex] pour Adobe Commerce dans [!DNL New Relic]. Le score [!DNL Apdex] mesure la satisfaction des utilisateurs quant au temps de réponse des applications et services web. Une action immédiate est nécessaire pour remédier au problème. L’alerte se présente comme suit, selon le canal de notification d’alerte que vous avez sélectionné.

![alerte critique apdex &#x200B;](../../assets/managed-alerts/apdex-critical-magento-managed.png){width="500"}

## Produits et versions concernés

* Architecture de plan Pro d’Adobe Commerce sur les infrastructures cloud
* Architecture du plan de démarrage d’Adobe Commerce sur les infrastructures cloud

## Problème

Vous recevrez une alerte gérée en [!DNL New Relic] si vous vous êtes inscrit aux [alertes gérées pour Adobe Commerce](managed-alerts-for-magento-commerce.md) et qu’un ou plusieurs seuils d’alerte ont été dépassés. Ces alertes ont été développées par Adobe pour fournir aux commerçants un ensemble de normes en utilisant les informations de l’assistance et de l’ingénierie.

<u> **Do!** </u>

* Abandonner tout déploiement planifié jusqu’à ce que cette alerte soit effacée.
* Mettez immédiatement votre site en mode de maintenance s’il ne répond plus du tout. Pour connaître les étapes, reportez-vous à la section [Activation ou désactivation du mode de maintenance](https://experienceleague.adobe.com/fr/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) dans le Guide d’installation de Commerce. Veillez à ajouter votre adresse IP à la liste des adresses IP exemptées pour vous assurer que vous pouvez toujours accéder à votre site à des fins de dépannage. Pour connaître les étapes, reportez-vous à la section [Tenir à jour la liste des adresses IP exemptées](https://experienceleague.adobe.com/fr/docs/commerce-operations/installation-guide/tutorials/maintenance-mode#maintain-the-list-of-exempt-ip-addresses) du Guide d’installation de Commerce.

<u>**Non !**</u>

* Lancez d’autres campagnes marketing qui peuvent apporter des pages vues supplémentaires à votre site.
* Exécutez des indexeurs ou des crons supplémentaires, ce qui peut entraîner une contrainte supplémentaire sur le CPU ou le disque.
* Effectuez toutes les tâches administratives importantes (c’est-à-dire, l’administration Commerce, les importations/exportations de données).
* Videz votre cache.

Si vous procédez comme indiqué ci-dessus lorsque vous avez reçu une alerte critique, avant d’avoir résolu la cause de l’alerte, votre site risque de ne plus répondre, si vous ne rencontrez pas déjà une panne de site.

## Solution

Pour identifier et résoudre les problèmes, procédez comme suit.

>[!WARNING]
>
>Comme il s’agit d’une alerte critique, il est vivement recommandé d’effectuer l’**étape 1** avant d’essayer de résoudre le problème (étape 2 et suivantes).

1. Vérifiez si un ticket d’assistance Adobe Commerce existe. Pour connaître les étapes à suivre, reportez-vous à la section [Tracker vos tickets d’assistance](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#track-support-case) dans la base de connaissances de l’assistance Commerce. L’assistance peut avoir reçu une alerte de seuil [!DNL New Relic], créé un ticket et commencé à travailler sur le problème. S’il n’existe aucun ticket, créez-en un. Le ticket doit contenir les informations suivantes :
   * Motif du contact : sélectionnez **[!UICONTROL New Relic CRITICAL alert received]**.
   * Description de l’alerte.
   * [[!DNL New Relic] Lien de l’incident](https://docs.newrelic.com/docs/alerts-applied-intelligence/new-relic-alerts/alert-incidents/view-violation-event-details-incidents). Cela est inclus dans vos [alertes gérées pour Adobe Commerce](managed-alerts-for-magento-commerce.md).
1. Pour identifier la source du problème, utilisez la page Transaction d’[[!DNL New Relic] APM](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems) afin d’identifier les transactions présentant des problèmes de performances :
   * Triez les transactions en fonction des scores [!DNL Apdex]. [[!DNL Apdex]](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/apdex-measure-user-satisfaction) fait référence à la satisfaction des utilisateurs quant au temps de réponse de vos applications et services web. Un score de [!DNL Apdex] faible peut indiquer un goulot d’étranglement (une transaction avec un temps de réponse plus élevé). Généralement, il s&#39;agit de la base de données, [!DNL Redis] ou PHP. Pour connaître les étapes, reportez-vous à la section [[!DNL New Relic] Afficher les transactions présentant le taux d’insatisfaction Apdex le plus élevé](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/apdex-measure-user-satisfaction/#dissatisfaction).
   * Triez les transactions en fonction du débit le plus élevé, du temps de réponse moyen le plus lent, du temps le plus long et d’autres seuils. Pour connaître les étapes, reportez-vous à la section [[!DNL New Relic] Rechercher des problèmes de performances spécifiques](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems). Si vous avez toujours du mal à identifier le problème, utilisez [[!DNL New Relic] la page Infrastructure d’APM](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/).
1. Utilisez la page Infrastructure d’[[!DNL New Relic] APM](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/) pour identifier les processus gourmands en ressources. Pour connaître les étapes, reportez-vous à la page [[!DNL New Relic] Hôtes de surveillance de l’infrastructure : [!UICONTROL Processes tab]](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/#processes).
1. Si des services tels que [!DNL Redis] ou MySQL sont la principale source de consommation de mémoire, essayez les méthodes suivantes :
   * Vérifiez que vous utilisez la dernière version. Les versions plus récentes peuvent parfois corriger les fuites de mémoire. Si vous n’utilisez pas la dernière version, envisagez d’effectuer une mise à niveau. Pour connaître les étapes, reportez-vous à la section [Services de modification](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/services-yaml.html?lang=fr) dans le guide de Commerce sur le cloud.
   * Recherchez les problèmes MySQL tels que les requêtes à exécution longue, les clés de Principal non définies et les index en double. Pour connaître les étapes, reportez-vous à la section [Problèmes de base de données les plus courants dans Adobe Commerce sur l’infrastructure cloud](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/maintenance/resolve-database-performance-issues.html?lang=fr) dans le guide d’implémentation de Commerce.
   * Recherchez les problèmes PHP. Examinez les processus en cours d’exécution en exécutant `ps aufx` dans l’interface de ligne de commande/Terminal. Dans la sortie du terminal, vous verrez les tâches et processus cron en cours d’exécution. Vérifiez la sortie pour le temps d’exécution des processus. S’il existe un fichier cron dont la durée d’exécution est longue, il est possible qu’il soit suspendu. Pour connaître les étapes de dépannage, reportez-vous aux sections [Performances lentes, crons à exécution lente et longue](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/slow-performance-slow-and-long-running-crons) et [Traitement Cron bloqué au statut « en cours d’exécution »](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-job-is-stuck-in-running-status) de la base de connaissances du support Commerce.

1. Une fois la source identifiée, SSH dans l’environnement pour en savoir plus. Pour connaître les étapes, reportez-vous à la section [SSH dans votre environnement](https://experienceleague.adobe.com/fr/docs/commerce-cloud-service/user-guide/develop/secure-connections#ssh) dans le guide de Commerce sur le cloud.
1. Si vous avez toujours du mal à identifier la source, passez en revue les tendances récentes pour identifier les problèmes liés aux récents déploiements de code ou aux modifications de configuration (par exemple, nouveaux groupes de clients et modifications importantes du catalogue). Il est recommandé de passer en revue les sept derniers jours d’activité pour toutes les corrélations dans les déploiements ou modifications de code.
1. Si vous ne parvenez pas à trouver une solution dans un délai raisonnable, demandez un upsize ou placez le site en mode de maintenance si vous ne l&#39;avez pas déjà fait. Pour connaître les étapes, reportez-vous aux sections [Comment demander un redimensionnement temporaire](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/how-to/how-to-request-temporary-magento-upsize) dans notre Base de connaissances de prise en charge de Commerce et [Activer ou désactiver le mode de maintenance](https://experienceleague.adobe.com/fr/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) dans le Guide d’installation de Commerce.
1. Si la mise à niveau revient au fonctionnement normal du site, envisagez de demander une mise à niveau permanente (contactez l’équipe de votre compte Adobe) ou essayez de reproduire le problème dans votre évaluation dédiée en exécutant un test de charge et en optimisant les requêtes, ou un code qui réduit la pression sur les services. Reportez-vous à la section [Tests de charge et de contrainte](https://experienceleague.adobe.com/fr/docs/commerce-cloud-service/user-guide/develop/test/staging-and-production#load-and-stress-testing) du guide Commerce sur le cloud .
