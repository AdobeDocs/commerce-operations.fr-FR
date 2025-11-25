---
title: Bonnes pratiques de dépannage
description: Découvrez comment résoudre les problèmes d’implémentation d’Adobe Commerce.
role: Developer
feature: Best Practices
exl-id: 6690eccf-d58d-4cbd-b278-90d020ee7c63
source-git-commit: 84a20012a81278cc95587ec14281b05330261687
workflow-type: tm+mt
source-wordcount: '458'
ht-degree: 0%

---

# Bonnes pratiques de dépannage

Suivez ces bonnes pratiques pour résoudre efficacement les problèmes d’infrastructure cloud d’Adobe Commerce.

## Produits et versions concernés

Adobe Commerce sur les infrastructures cloud

## Bonnes pratiques

| Type d&#39;événement | Bonnes pratiques | Ressource |
|----------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Problèmes de déploiement | **Suivez les bonnes pratiques de déploiement.** 13 % des tickets d’assistance concernent des problèmes de déploiement. Les bonnes pratiques ont été mises à jour afin d’inclure des moyens de prévenir nombre de ces causes. | [Bonnes pratiques relatives aux builds et au déploiement](https://experienceleague.adobe.com/fr/docs/commerce-cloud-service/user-guide/develop/deploy/best-practices#best-practices) dans notre documentation destinée aux développeurs. |
| Problèmes liés à l’arrêt du site | **Utilisation de l’utilitaire de résolution des problèmes de panne du site.** Crons peut être long et peut se déborder les uns les autres. Ils sont à l’origine de nombreuses pannes et de problèmes de performances. | [Résolution des problèmes d’arrêt du site](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/site-down-or-unresponsive/magento-site-down-troubleshooter.html?lang=fr) et [Comment réinitialiser les tâches cron](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-job-is-stuck-in-running-status.html?lang=fr) dans notre base de connaissances du support. |
| Problèmes de performances | **Si vous n’utilisez pas la bannière Adobe Commerce, désactivez-la.** Lorsque la bannière est activée mais n’est pas utilisée, les ressources sont utilisées pour effectuer des recherches dans la base de données alors qu’elles ne sont pas nécessaires, ce qui entraîne des problèmes de performances. | [Désactivez la sortie Adobe Commerce Banner pour améliorer les performances](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/disable-magento-banner-output-to-improve-site-performance.html?lang=fr) dans notre base de connaissances d’assistance. |
| Rechercher événements | **Le moteur de recherche catalogue MySQL a été supprimé dans Adobe Commerce 2.4.0.** Vous devez disposer de la configuration de l’hôte Elasticsearch et l’avoir configurée avant d’installer la version 2.4.0. Voir Installation et configuration d’Elasticsearch dans la documentation destinée aux développeurs. | [Configurez le service Elasticsearch](https://experienceleague.adobe.com/fr/docs/commerce-cloud-service/user-guide/configure/service/elasticsearch) dans notre documentation destinée aux développeurs. |
| Erreurs personnalisées | **Ne déployez pas pendant les heures de pointe.** L’ajout et la suppression d’utilisateurs déclencheront un déploiement. | [Déploiement sans interruption](https://experienceleague.adobe.com/fr/docs/commerce-cloud-service/user-guide/develop/deploy/reduce-downtime) dans notre documentation destinée aux développeurs. |
| Erreurs et problèmes de base de données | **Les problèmes de base de données entraînent des problèmes de déploiement (post-hook), de performances et d’arrêt du site.** Beaucoup impliquent des erreurs ou une allocation d’espace de base de données insuffisante. | [Codes d’erreur MariaDB](https://mariadb.com/docs/server/reference/error-codes/mariadb-error-code-reference) ; [Gérer l’espace de stockage](https://experienceleague.adobe.com/fr/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space) (y compris la base de données) dans notre documentation destinée aux développeurs. |
| Problèmes de configuration | **Index par planification au lieu de Index lors de l’enregistrement.** Il s’agit de la configuration d’indexation la plus efficace. L’indexation lors de l’enregistrement provoquera une réindexation complète. | [Configurez les indexeurs](../../../configuration/cli/manage-indexers.md#configure-indexers) dans notre documentation destinée aux développeurs. |
| Problèmes de code personnalisé | **Recherchez dans vos journaux de requêtes lentes des opportunités d’identifier et éventuellement d’interrompre les processus qui prennent trop de temps.** Les requêtes lentes peuvent entraîner des interblocages de base de données, ce qui entraîne des arrêts de site et des problèmes de performances. | [Vérification des requêtes lentes et des processus prenant trop de temps dans MySQL](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/database/checking-slow-queries-and-processes-mysql.html?lang=fr) |
| Problèmes d’extension | **N’utiliser que les extensions vérifiées actuellement présentes sur le Commerce Marketplace.** | [&#x200B; Extensions pour Adobe Commerce &#x200B;](https://marketplace.magento.com/extensions.html) |
| Problèmes de ressources | **Surveillez la mémoire et l&#39;espace disponibles et optimisez le stockage.** Vous disposez peut-être d’espace disponible avant une action qui consomme des ressources importantes (déploiement, par exemple). Une mauvaise optimisation du stockage des fichiers (trop d’images volumineuses et riches, par exemple) peut également contribuer à un espace insuffisant. La faiblesse des ressources entraîne des problèmes de performances, une panne du site, des déploiements bloqués et des échecs de déploiement. | [Gérer l’espace disque](https://experienceleague.adobe.com/fr/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space) dans notre documentation destinée aux développeurs ; [Le stockage des fichiers est faible/épuisé, le chargement de pages spécifiques est lent](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/file-storage-low-specific-page-loads-are-slow.html?lang=fr) dans notre base de connaissances du support. |
