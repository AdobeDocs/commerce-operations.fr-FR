---
title: 'Alertes gérées sur Adobe Commerce : alerte critique de CPU'
description: Cet article décrit les étapes de dépannage à suivre lorsque vous recevez une alerte critique CPU pour Adobe Commerce dans  [!DNL New Relic]. Une action immédiate est nécessaire pour remédier au problème.
feature: Cache, Marketing Tools, Observability, Support, Tools and External Services
role: Admin
source-git-commit: b30266b8f39989103ca70fa3e57ade8cea9b0dcc
workflow-type: tm+mt
source-wordcount: '776'
ht-degree: 0%

---

# Alertes gérées sur Adobe Commerce : alerte critique de CPU

Cet article décrit les étapes de dépannage à suivre lorsque vous recevez une alerte critique CPU pour Adobe Commerce en [!DNL New Relic]. Une action immédiate est nécessaire pour remédier au problème. L’alerte se présente comme suit, selon le canal de notification d’alerte que vous avez sélectionné.

![alerte critique de disque](../../assets/managed-alerts/cpu-critical-magento-managed.png){width="500"}

## Produits et versions concernés

Architecture de plan Pro d’Adobe Commerce sur les infrastructures cloud

## Problème

Vous recevrez une alerte gérée en [!DNL New Relic] si vous vous êtes inscrit aux [alertes gérées pour Adobe Commerce](managed-alerts-for-magento-commerce.md) et qu’un ou plusieurs seuils d’alerte ont été dépassés. Ces alertes ont été développées par Adobe Commerce pour fournir aux clients un ensemble de normes à l’aide des informations provenant des services d’assistance et d’ingénierie.

<u>**Do!**</u> :

* Abandonner tout déploiement planifié jusqu’à ce que cette alerte soit effacée.
* Mettez immédiatement votre site en mode de maintenance s’il ne répond plus du tout. Pour connaître les étapes, reportez-vous à la section [Activation ou désactivation du mode de maintenance](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) dans le Guide d’installation de Commerce. Veillez à ajouter votre adresse IP à la liste des adresses IP exemptées pour vous assurer que vous pouvez toujours accéder à votre site à des fins de dépannage. Pour connaître les étapes, reportez-vous à la section [Tenir à jour la liste des adresses IP exemptées](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode#maintain-the-list-of-exempt-ip-addresses) du Guide d’installation de Commerce.

<u>**Ne fais pas ça !**</u> :

* Lancez d’autres campagnes marketing qui peuvent apporter des pages vues supplémentaires à votre site.
* Exécutez des indexeurs ou des crons supplémentaires, ce qui peut entraîner une contrainte supplémentaire sur le CPU ou le disque.
* Effectuez toutes les tâches administratives importantes (c’est-à-dire, l’administration Commerce, les importations/exportations de données).
* Videz votre cache.

Votre site peut ne plus répondre (si vous ne rencontrez pas déjà de panne de site) si vous effectuez l’une des actions « Ne pas » avant d’avoir enquêté et résolu la cause de l’alerte.

## Solution

Pour identifier et résoudre les problèmes, procédez comme suit.

>[!WARNING]
>
>Comme il s’agit d’une alerte critique, il est vivement recommandé d’effectuer l’**étape 1** avant d’essayer de résoudre le problème (étape 2 et suivantes).

Vérifiez si le ticket d’assistance Adobe Commerce existe. Pour connaître les étapes à suivre, reportez-vous à la section [Tracker vos tickets d’assistance](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#track-support-case) dans la base de connaissances de l’assistance Commerce. L’assistance peut avoir reçu une alerte de seuil [!DNL New Relic], créé un ticket et commencé à travailler sur le problème. S’il n’existe aucun ticket, créez-en un. Le ticket doit contenir les informations suivantes :

1. Motif du contact : sélectionnez **[!UICONTROL New Relic CRITICAL alert received]**.
1. Description de l’alerte.
1. [[!DNL New Relic] Lien de l’incident](https://docs.newrelic.com/docs/alerts-applied-intelligence/new-relic-alerts/alert-incidents/view-violation-event-details-incidents). Cela est inclus dans vos [alertes gérées pour Adobe Commerce](managed-alerts-for-magento-commerce.md).
1. Utilisez la page Transaction d’[[!DNL New Relic] APM](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems) pour identifier les transactions présentant des problèmes de performances :
   * Triez les transactions en fonction des scores Apdex croissants. [[!DNL Apdex]](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/apdex-measure-user-satisfaction) fait référence à la satisfaction des utilisateurs quant au temps de réponse de vos applications et services web. Un [faible [!DNL Apdex] score](managed-alerts-for-magento-commerce-apdex-warning-alert.md) peut indiquer un goulot d’étranglement (une transaction avec un temps de réponse plus élevé). En général, elle est liée à la base de données [!DNL Redis] ou PHP. Pour connaître les étapes, reportez-vous à la section New Relic [Afficher les transactions avec le niveau  [!DNL Apdex] ’insatisfaction le plus élevé](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/view-your-apdex-score#apdex-dissat).
   * Triez les transactions en fonction du débit le plus élevé, du temps de réponse moyen le plus lent, du temps le plus long et d’autres seuils. Pour connaître les étapes, reportez-vous à [!DNL New Relic] [Rechercher des problèmes de performances spécifiques](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems).
1. Si vous avez toujours du mal à identifier la source, utilisez la page Infrastructure d’[[!DNL New Relic] APM](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page) pour identifier les services qui requièrent un grand nombre de ressources. Pour connaître les étapes, reportez-vous à [!DNL New Relic] page [Hôtes de surveillance des infrastructures : Onglet Processus](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/#processes).
1. Si vous identifiez la source, insérez SSH dans l’environnement pour en savoir plus. Pour connaître les étapes, reportez-vous à la section [SSH dans votre environnement](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html) dans le guide de Commerce sur le cloud.
1. Si vous avez toujours du mal à identifier la source :
   * Consultez les tendances récentes pour identifier les problèmes liés aux récents déploiements de code ou aux modifications de configuration (par exemple, les nouveaux groupes de clients et les modifications importantes apportées au catalogue). Il est recommandé de passer en revue les sept derniers jours d’activité pour toutes les corrélations dans les déploiements ou modifications de code.
   * Recherchez et désactivez les catalogues plats. Pour connaître les étapes, reportez-vous à la section [Performances lentes, crons lents et à long terme](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/slow-performance-slow-and-long-running-crons) de la base de connaissances de support de Commerce.
   * Si vous pensez être victime d’une attaque DDoS, essayez de bloquer le trafic des robots. Pour connaître les étapes, reportez-vous à la section [Comment bloquer le trafic malveillant pour Adobe Commerce sur l’infrastructure cloud au niveau Fastly ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/how-to/block-malicious-traffic-for-magento-commerce-on-fastly-level) dans la base de connaissances du support Commerce.
1. Si le problème semble temporaire, effectuez des étapes de réduction, telles qu’une mise à niveau ou placez le site en mode de maintenance. Pour connaître les étapes, reportez-vous aux sections [Comment demander un redimensionnement temporaire](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/how-to/how-to-request-temporary-magento-upsize) dans la base de connaissances de la prise en charge de Commerce et [Activer ou désactiver le mode de maintenance](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) dans le guide d’installation de Commerce. Si la mise à niveau revient au fonctionnement normal du site, envisagez de demander une mise à niveau permanente (contactez l’équipe de votre compte Adobe) ou essayez de reproduire le problème dans votre évaluation dédiée en exécutant un test de charge et en optimisant les requêtes ou le code qui réduit la pression sur les services. Pour connaître les étapes, reportez-vous à la section [Test de charge et de contrainte](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/test/staging-and-production#load-and-stress-testing) dans le guide Commerce sur Cloud .
