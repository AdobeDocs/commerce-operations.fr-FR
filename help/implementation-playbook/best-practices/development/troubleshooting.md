---
title: Bonnes pratiques de dépannage
description: Découvrez comment résoudre les problèmes de mise en oeuvre d’Adobe Commerce.
role: Developer
feature: Best Practices
exl-id: 6690eccf-d58d-4cbd-b278-90d020ee7c63
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '523'
ht-degree: 0%

---

# Bonnes pratiques de dépannage

Suivez ces bonnes pratiques pour résoudre efficacement les problèmes d’infrastructure cloud liés à Adobe Commerce.

## Produits et versions concernés

Adobe Commerce sur l’infrastructure cloud

## Bonnes pratiques

| Type de problème | Bonnes pratiques | Ressource |
|----------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Problèmes de déploiement | **Suivez les bonnes pratiques de déploiement.** 13 % des tickets d’assistance impliquent des problèmes de déploiement. Les bonnes pratiques ont été mises à jour afin d’inclure des moyens d’éviter nombre de ces causes. | [Bonnes pratiques relatives aux versions et au déploiement](https://devdocs.magento.com/cloud/reference/discover-deploy.html#best-practices) dans notre documentation destinée aux développeurs. |
| Problèmes liés au site | **Utilisez l’outil de dépannage de Site Down.** Les escadrons peuvent être longs et peuvent se chevaucher. Elles sont la source de nombreuses pannes et de nombreux problèmes de performance. | [Dépannage de Site Down](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/site-down-or-unresponsive/magento-site-down-troubleshooter.html?lang=en) et [Comment réinitialiser les tâches cron](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-job-is-stuck-in-running-status.html?lang=en) dans notre base de connaissances de soutien. |
| Problèmes de performances | **Si vous n’utilisez pas la bannière Adobe Commerce, désactivez-la.** Lorsque la bannière est activée, mais pas utilisée, les ressources sont utilisées pour effectuer des recherches dans la base de données lorsqu’elles ne sont pas requises, ce qui entraîne des problèmes de performances. | [Désactiver la sortie de la bannière Adobe Commerce pour améliorer les performances](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/disable-magento-banner-output-to-improve-site-performance.html) dans notre base de connaissances de soutien. |
| Problèmes de recherche | **Le moteur de recherche catalogue MySQL a été supprimé dans Adobe Commerce 2.4.0.** Vous devez avoir configuré et configuré l’hôte Elasticsearch avant d’installer la version 2.4.0. Reportez-vous à la section Installation et configuration de l’Elasticsearch dans notre documentation destinée aux développeurs. | [Configuration du service Elasticsearch](https://devdocs.magento.com/cloud/project/services-elastic.html) dans notre documentation destinée aux développeurs. |
| Erreurs personnalisées | **Ne déployez pas en période de pointe.** L’ajout et la suppression d’utilisateurs déclenchent un déploiement. | [Déploiement sans interruption](https://devdocs.magento.com/cloud/deploy/reduce-downtime.html) dans notre documentation destinée aux développeurs. |
| Erreurs et problèmes de base de données | **Les problèmes de base de données entraînent des situations de déploiement (problèmes de crochet de publication), de performances et de mise en service du site.** La plupart impliquent des erreurs ou une allocation insuffisante de l’espace de base de données. | [Codes d’erreur MariaDB](https://mariadb.com/kb/en/library/mariadb-error-codes/#mariadb-specific-error-codes); [Gestion de l’espace de stockage](https://devdocs.magento.com/cloud/project/manage-disk-space.html) (y compris la base de données) dans la documentation destinée aux développeurs. |
| Problèmes de configuration | **Indexez par planification plutôt que par index sur Enregistrer.** Il s’agit de la configuration d’indexation la plus efficace. L’index sur Enregistrer provoque une réindexation complète. | [Configuration des indexeurs](../../../configuration/cli/manage-indexers.md#configure-indexers) dans notre documentation destinée aux développeurs. |
| Problèmes liés au code personnalisé | **Vérifiez vos journaux de requêtes lents pour connaître les opportunités d’identification et éventuellement de suppression des processus qui prennent trop de temps à se terminer.** La lenteur des requêtes peut entraîner des blocages de base de données, ce qui entraîne des problèmes de performances et de panne du site. | [Vérifier les requêtes et processus lents qui prennent trop de temps dans MySQL](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/database/checking-slow-queries-and-processes-mysql.html) |
| Problèmes d’extension | **N’utilisez que les extensions vérifiées actuellement sur le Commerce Marketplace.** | [Extensions pour Adobe Commerce](https://marketplace.magento.com/extensions.html) |
| Problèmes de ressource | **Surveillez la mémoire et l’espace disponibles et optimisez le stockage.** Vous pouvez disposer d’un espace disponible avant une action qui consomme des ressources importantes (déploiement, par exemple). Une mauvaise optimisation du stockage des fichiers (trop d’images riches volumineuses, par exemple) peut également contribuer à un espace insuffisant. Les ressources faibles provoquent des problèmes de performances, des sites en panne, des déploiements bloqués et des échecs de déploiement. | [Gestion de l’espace disque](https://devdocs.magento.com/cloud/project/manage-disk-space.html) dans notre documentation destinée aux développeurs ; [Le stockage de fichiers est faible/épuisé, le chargement de pages spécifiques est lent.](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/file-storage-low-specific-page-loads-are-slow.html?lang=en) dans notre base de connaissances de soutien. |
