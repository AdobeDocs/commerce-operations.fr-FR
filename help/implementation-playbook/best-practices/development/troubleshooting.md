---
title: Bonnes pratiques de dépannage
description: Découvrez comment résoudre les problèmes de mise en oeuvre d’Adobe Commerce.
role: Developer
feature: Best Practices
exl-id: 6690eccf-d58d-4cbd-b278-90d020ee7c63
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '458'
ht-degree: 0%

---

# Bonnes pratiques de dépannage

Suivez ces meilleures pratiques pour un dépannage efficace de Adobe Commerce sur les problèmes d’infrastructure cloud.

## Produits et versions concernés

Adobe Commerce sur l’infrastructure cloud

## Bonnes pratiques

| Type de problème | Bonnes pratiques | Ressource |
|----------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Problèmes de déploiement | **Suivez les bonnes pratiques de déploiement.** 13 % des tickets d’assistance impliquent des problèmes de déploiement. Les bonnes pratiques ont été mises à jour afin d’inclure des moyens d’éviter nombre de ces causes. | [Bonnes pratiques pour les versions et le déploiement](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/deploy/best-practices#best-practices) dans notre documentation destinée aux développeurs. |
| Problèmes liés au site | **Utilisez l’outil de dépannage Site Down .** Les escadrons peuvent être longs et peuvent se chevaucher. Elles sont la source de nombreuses pannes et de nombreux problèmes de performance. | [Résolution des problèmes de Site Down](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/site-down-or-unresponsive/magento-site-down-troubleshooter.html?lang=en) et [Comment réinitialiser les tâches cron](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-job-is-stuck-in-running-status.html?lang=en) dans notre base de connaissances de support. |
| Problèmes de performances | **Si vous n’utilisez pas la bannière Adobe Commerce, désactivez-la.** Lorsque la bannière est activée mais pas utilisée, les ressources sont utilisées pour effectuer des recherches dans la base de données lorsqu’elles ne sont pas requises, ce qui entraîne des problèmes de performances. | [Désactivez la sortie de la bannière Adobe Commerce pour améliorer les performances](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/disable-magento-banner-output-to-improve-site-performance.html) dans notre base de connaissances de support. |
| Problèmes de recherche | **Le moteur de recherche de catalogue MySQL a été supprimé dans Adobe Commerce 2.4.0.** Vous devez avoir configuré l’hôte Elasticsearch et configuré avant d’installer la version 2.4.0. Reportez-vous à la section Installation et configuration de l’Elasticsearch dans notre documentation destinée aux développeurs. | [Configurez Elasticsearch service](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/service/elasticsearch) dans notre documentation destinée aux développeurs. |
| Erreurs personnalisées | **Ne déployez pas en période de pointe.** L’ajout et la suppression d’utilisateurs déclencheront un déploiement. | [Déploiement sans interruption](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/deploy/reduce-downtime) dans notre documentation destinée aux développeurs. |
| Erreurs et problèmes de base de données | **Les problèmes de base de données entraînent des situations de déploiement (problèmes de post hook), de performance et de mise en service du site.** La plupart comportent des erreurs ou une allocation insuffisante de l’espace de base de données. | [Codes d’erreur MariaDB](https://mariadb.com/kb/en/library/mariadb-error-codes/#mariadb-specific-error-codes) ; [Gérer l’espace de stockage](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space) (y compris la base de données) dans la documentation destinée aux développeurs. |
| Problèmes de configuration | **Index par planification au lieu de Index sur Enregistrer.** Il s’agit de la configuration d’indexation la plus efficace. L’index sur Enregistrer provoque une réindexation complète. | [Configurez les indexeurs](../../../configuration/cli/manage-indexers.md#configure-indexers) dans notre documentation destinée aux développeurs. |
| Problèmes liés au code personnalisé | **Vérifiez vos logs de requête lents pour connaître les opportunités d’identification et éventuellement de suppression des processus qui prennent trop de temps à se terminer.** La lenteur des requêtes peut entraîner des blocages de base de données, ce qui entraîne des problèmes de performances et de perte de site. | [Vérification des requêtes et processus lents trop longs dans MySQL](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/database/checking-slow-queries-and-processes-mysql.html) |
| Problèmes d’extension | **Utilisez uniquement des extensions vérifiées actuellement sur le Commerce Marketplace.** | [Extensions pour Adobe Commerce](https://marketplace.magento.com/extensions.html) |
| Problèmes de ressource | **Surveillez la mémoire et l’espace disponibles et optimisez le stockage.** Il se peut que vous disposiez d’un espace avant une action qui consomme des ressources importantes (déploiement, par exemple). Une mauvaise optimisation du stockage des fichiers (trop d’images riches volumineuses, par exemple) peut également contribuer à un espace insuffisant. Les ressources faibles provoquent des problèmes de performances, des sites en panne, des déploiements bloqués et des échecs de déploiement. | [Gérez l’espace disque](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space) dans notre documentation destinée aux développeurs ; [Le stockage de fichiers est faible/épuisé, les chargements de pages spécifiques sont lents](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/file-storage-low-specific-page-loads-are-slow.html?lang=en) dans notre base de connaissances de support. |
