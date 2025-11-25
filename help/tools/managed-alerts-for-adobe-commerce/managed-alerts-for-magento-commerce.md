---
title: Alertes gérées pour Adobe Commerce
description: Si vous êtes un client d’Adobe Commerce sur les infrastructures cloud Pro Planifier l’architecture , vous pouvez utiliser des alertes gérées pour connaître l’intégrité de votre site. Si vous êtes un client d’Adobe Commerce sur l’architecture du plan de démarrage d’infrastructure cloud, vous ne recevrez des alertes que pour les conditions de taux d’erreur  [!DNL Apdex]  et .
feature: Observability, Support, Tools and External Services
role: Admin
exl-id: 3fc4b07f-4e27-4833-97a9-cf9741ae5648
source-git-commit: 4560e7d000ad8333c3089b8b5e8ffd25f5d31b67
workflow-type: tm+mt
source-wordcount: '542'
ht-degree: 0%

---

# Alertes gérées pour Adobe Commerce


Nous avons mis en place des tableaux de bord et des alertes clés pour vous aider à comprendre à quel moment votre site atteint des niveaux de stockage et de [!DNL Apdex] critiques (satisfaction des utilisateurs à l&#39;égard des applications et du temps de réponse des services). Cela peut vous aider à prendre des mesures avant de remarquer des temps de réponse lents ou une panne. Vous pourrez résoudre les problèmes liés aux alertes avec les articles répertoriés ci-dessous. Avant de pouvoir utiliser les alertes, commencez par configurer les canaux de notification. Reportez-vous à [[!DNL New Relic] Configuration des canaux de notification](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/monitor/new-relic/new-relic-service) dans le guide Commerce sur le cloud.

>[!NOTE]
>
>Si les alertes gérées pour la politique d’alerte d’Adobe Commerce ne sont pas disponibles, cela peut être dû au fait que ce compte a été récemment créé ou [!DNL New Relic] avoir été récemment configuré. Un processus est exécuté tous les mardis pour ajouter la politique d’alerte à ces comptes. La stratégie d’alerte doit être disponible le lendemain de l’exécution du processus suivant. Si la politique est toujours manquante, [envoyez une demande d’assistance Adobe Commerce](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#support-case) et incluez votre ID de projet.

Consultez le tableau ci-dessous pour obtenir des liens vers les articles de la base de connaissances qui fournissent des étapes de dépannage pour ces alertes :

* Alertes gérées pour Adobe Commerce : alerte d’avertissement de CPU
* Alertes gérées pour Adobe Commerce : alerte critique de CPU
* Alertes gérées pour Adobe Commerce : alerte d’avertissement de mémoire
* Alertes gérées pour Adobe Commerce : alerte critique de la mémoire
* Alertes gérées pour Adobe Commerce : alerte d’avertissement [!DNL Apdex]
* Alertes gérées pour Adobe Commerce : alerte critique [!DNL Apdex]
* Alertes gérées pour Adobe Commerce : alerte d’avertissement de disque
* Alertes gérées pour Adobe Commerce : alerte critique de disque
* Alertes gérées sur Adobe Commerce : alertes MariaDB
* Alertes gérées sur Adobe Commerce : alerte d’avertissement de mémoire [!DNL Redis]
* Alertes gérées sur Adobe Commerce : alerte critique de mémoire [!DNL Redis]

>[!NOTE]
>
>Les seuils définis pour les alertes d’avertissement et les alertes critiques sont basés sur les recherches que nous effectuons à l’aide des données de performances historiques sur l’ensemble de notre base de clients et représentent les dernières informations provenant des équipes d’assistance et d’ingénierie d’Adobe Commerce. Veuillez noter que ces seuils peuvent changer en fonction des dernières analyses en cours. Le flux d’alertes type consiste à recevoir des alertes de gravité inférieure à supérieure. Vous recevrez donc probablement une alerte Avertissement avant de recevoir une alerte Critique. Consultez les liens vers les articles pour connaître les étapes de dépannage.

| Gravité | CPU | Mémoire | Disque | [!DNL Apdex] | MariaDB | Mémoire [!DNL Redis] | Article de dépannage |
|----------|-----|--------|------|-------|---------|--------------|-------------------------|
| Attention | ✅ |        |      |       |         |              | [Alertes gérées pour Adobe Commerce : alerte d’avertissement de CPU](managed-alerts-for-magento-commerce-cpu-warning-alert.md) |
| Critique | ✅ |        |      |       |         |              | [Alertes gérées pour Adobe Commerce : alerte critique de CPU](managed-alerts-on-magento-commerce-cpu-critical-alert.md) |
| Attention |     | ✅ |      |       |         |              | [Alertes gérées pour Adobe Commerce : alerte de mémoire](managed-alerts-for-magento-commerce-memory-warning-alert.md) |
| Critique |     | ✅ |      |       |         |              | [Alertes gérées pour Adobe Commerce : alerte critique de la mémoire](managed-alerts-on-magento-commerce-memory-critical-alert.md) |
| Attention |     |        |      | ✅ |         |              | [Alertes gérées pour Adobe Commerce: [!DNL Apdex] alerte d’avertissement](managed-alerts-for-magento-commerce-apdex-warning-alert.md) |
| Critique |     |        |      | ✅ |         |              | [Alertes gérées pour Adobe Commerce: [!DNL Apdex] alerte critique](managed-alerts-for-magento-commerce-apdex-critical-alert.md) |
| Attention |     |        | ✅ |       |         |              | [Alertes gérées pour Adobe Commerce : alerte de disque](managed-alerts-for-magento-commerce-disk-warning-alert.md) |
| Critique |     |        | ✅ |       |         |              | [Alertes gérées pour Adobe Commerce : alerte critique de disque](managed-alerts-for-magento-commerce-disk-critical-alert.md) |
| Avertissement et critique |     |        |      |       | ✅ |              | [Alertes gérées sur Adobe Commerce : alertes MariaDB](managed-alerts-on-magento-commerce-mariadb-alerts.md) |
| Attention |     |        |      |       |         | ✅ | [Alertes gérées sur Adobe Commerce: [!DNL Redis] alerte d’avertissement de mémoire](managed-alerts-on-magento-commerce-redis-memory-warning-alert.md) |
| Critique |     |        |      |       |         | ✅ | [Alertes gérées sur Adobe Commerce: [!DNL Redis] alerte critique de mémoire](managed-alerts-on-magento-commerce-redis-memory-critical-alert.md) |

## Vérification des seuils d’alerte définis pour les alertes gérées

Vous pouvez consulter les seuils d’alerte configurés pour les alertes gérées à partir de votre compte New Relic. Pour obtenir des instructions, voir [Surveillance des performances avec des alertes gérées](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/monitor/new-relic/investigate/investigate-performance#monitor-performance-with-managed-alerts).
