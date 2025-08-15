---
title: Optimisation des performances du serveur principal
description: Découvrez comment optimiser les performances du serveur principal des sites Adobe Commerce.
badge: label="Contribué par objectsource" type="Informative" url="https://objectsource.co.uk/" tooltip="objectsource"
role: Admin, User, Developer
feature: Best Practices
exl-id: 18bc97a0-3d34-4d48-a3e2-84af2da7d0d3
source-git-commit: d884d434e696a911de626dc76983468556cf451f
workflow-type: tm+mt
source-wordcount: '977'
ht-degree: 0%

---

# Bonnes pratiques d’optimisation des performances du serveur principal

Cette rubrique présente les bonnes pratiques pour étudier et optimiser les performances du serveur principal des sites Adobe Commerce, en mettant l’accent sur l’optimisation et les tests des bases de données. L’équipe de développement peut utiliser ces informations pour étudier le contexte unique de chaque projet Commerce et identifier les opportunités d’optimisation de la configuration et des opérations du serveur principal afin d’améliorer les performances du site.

>[!NOTE]
>
>Les recommandations et les exemples s’inspirent des processus suivis par objectsource dans le cadre d’engagements clients réels pour fournir des sites Adobe Commerce hautement performants à grande échelle.

## Produits et versions concernés

[Toutes les versions prises en charge](../../../release/versions.md) de :

- Adobe Commerce sur les infrastructures cloud
- Adobe Commerce On-Premise

## Optimisation de la base de données pour de meilleures performances

L’optimisation des bases de données est un moyen infaillible d’améliorer l’expérience utilisateur et d’augmenter les ventes. Lorsque vous optimisez la base de données, colonne dorsale d’un site Commerce, vous pouvez éviter la lenteur des performances du site web et éliminer les temps de chargement longs qui entraînent des frictions pour les clients.

### Test de résistance

Les périodes de trafic élevé, telles que le Black Friday, exigent que les sites Commerce gèrent des volumes de trafic massifs. En prévision de tels événements, les tests de résistance sont essentiels pour comprendre comment un site fonctionne sous des augmentations exponentielles de la charge.

GTmetrix est un outil que vous pouvez utiliser pour les tests de résistance. Évaluez la préparation du site aux augmentations de charge en configurant GTmetrix pour répliquer et multiplier le comportement et les actions normaux des visiteurs. Exécutez ensuite des tests pour identifier et résoudre les problèmes susceptibles d’affecter les performances et la disponibilité du site lors d’événements d’achat majeurs.

En savoir plus sur la préparation des projets Commerce pour les périodes de trafic élevé :

- [Préparation des vacances](https://experienceleague.adobe.com/docs/events/commerce-intelligence-webinar-recordings/2021/holiday-readiness.html)
- [Analyse des achats de vacances](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/analyze/performance/holiday-season-perf.html)
- [Augmentation de la capacité de pointe](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/2021-holiday-surge-capacity-requests-for-magento-commerce-cloud.html)

### Test de charge

Vous pouvez également utiliser GTmetrix ou un outil similaire pour charger des projets Commerce de test. En tant que précurseur des tests de résistance, les tests de charge sont une pratique essentielle pour les sites à grande échelle et à trafic élevé. Prévenez les pannes de site inattendues, les clients frustrés et les pertes financières en anticipant et en atténuant les problèmes qui affectent les performances du site lors des pics de charge.

Utilisez GTmetrix pour simuler un trafic important et analyser la performance du site pour obtenir des informations claires sur la capacité du site. Cette analyse permet d’identifier et de résoudre les goulets d’étranglement, ainsi que d’identifier les opportunités d’optimisation, afin que les sites Commerce puissent fonctionner efficacement sous une charge accrue.

En savoir plus sur le test de projets Adobe Commerce :

- [Conseils de test](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/guidance.html) (infrastructure cloud)
- [Test de l’application](https://developer.adobe.com/commerce/testing/guide/)

### Identifier et résoudre les problèmes de performances

Résolvez les problèmes de performances en utilisant divers outils tels que New Relic et Observation for Adobe Commerce pour détecter les goulets d’étranglement et optimiser efficacement les sites Commerce. [New Relic](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/monitor/new-relic/new-relic-service.html) est inclus avec Adobe Commerce sur l’infrastructure cloud et [Observation pour Adobe Commerce](/help/tools/observation-for-adobe-commerce/intro.md) est inclus pour les déploiements cloud et on-premise.

Utilisez ces outils pour analyser les performances du site et identifier les problèmes de performances liés aux éléments suivants :

- Fonctionnalités à forte utilisation de CPU
- Configuration de la gestion du cache pour les requêtes et les opérations principales
- Appels d’API tiers
- Planification cron

Par exemple, vous pouvez examiner de près les transactions en mettant l’accent sur les pages de détails de produits et de catégories. Identifier les processus fastidieux qui peuvent être optimisés pour améliorer les performances. Dans un engagement client, objectsource a remarqué un problème de performance sur une page de détails du produit et a trouvé un appel API qui consommait 3,5 % du temps de performance. Sur la base de ce résultat, ils ont examiné la hiérarchie d’exécution du code afin de localiser et de résoudre le problème à l’origine du goulot d’étranglement.

En savoir plus sur la gestion des performances du site :

- [Surveillance des performances](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/monitor/performance.html) (infrastructure cloud)
- [Bonnes pratiques de configuration](/help/performance/configuration.md)
- [Observation pour Adobe Commerce](/help/tools/observation-for-adobe-commerce/intro.md)

### Optimiser les performances de MySQL

Résoudre les problèmes de performances de MySQL en implémentant le clustering de bases de données et l’optimisation des requêtes est une approche efficace pour améliorer les performances avant et pendant les périodes de trafic élevé comme le Black Friday.

#### Implémentation de la mise en cluster de bases de données

Les sites web à trafic élevé sont souvent confrontés à des goulots d’étranglement au niveau de la base de données, principalement en raison de la dépendance à un seul serveur MySQL. Vous pouvez résoudre ces goulots d’étranglement en implémentant le clustering de base de données, une architecture distribuée qui améliore les performances et assure une haute disponibilité.

La mise en grappe des bases de données minimise l&#39;impact des problèmes liés aux bases de données pendant les périodes de pointe du trafic en permettant à plusieurs nœuds web de se connecter à plusieurs serveurs MySQL. Utilisez des outils tels que Galera Cluster pour configurer la mise en cluster de bases de données pour les sites Commerce. Le cluster Galera est inclus dans [les projets Adobe Commerce déployés sur l’infrastructure cloud](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/architecture/pro-architecture).

#### Optimiser les requêtes MySQL

En règle générale, l’infrastructure de la plupart des sites Adobe Commerce se compose de plusieurs nœuds web connectés à un seul serveur MySQL.

Dans cette configuration, chaque nœud web front-end se connecte au cluster Galera, ce qui permet d’avoir plusieurs serveurs MySQL. L’augmentation du nombre de nœuds web front-end peut améliorer les performances des applications, mais le seul serveur MySQL reste un goulot d’étranglement.

Pour optimiser les performances du serveur MySQL et minimiser les goulots d’étranglement, il est essentiel d’identifier et de réduire les requêtes inutiles. Par exemple, si vous envoyez 1 000 requêtes par seconde, mais que seulement 200 sont nécessaires, l’optimisation et la diminution du nombre de requêtes peuvent améliorer considérablement les performances.

En savoir plus sur la configuration et l’optimisation de MySQL :

- [Bonnes pratiques relatives à la configuration de la base de données](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/planning/database-on-cloud.html)
- [Réplication lente pour la réplication Galera DB](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/backend-development/galera-db-slow-replication.html)
- [Directives générales concernant MySQL](/help/installation/prerequisites/database/mysql.md)
- [Mise en cache des requêtes MySQL](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/backend-development/mysql-query-cache.html)

## Gérer efficacement les tâches cron : performances et timing

Les tâches cron jouent un rôle essentiel dans le traitement des tâches en arrière-plan du site, telles que la génération de rapports et l’indexation de produits. Toutefois, l’optimisation des tâches cron nécessite de soigneusement étudier leur impact sur les performances globales. L’équipe de développement doit évaluer la fréquence de planification et déterminer le timing optimal en fonction des besoins spécifiques.

En équilibrant les performances et la commodité, il est souvent conseillé de planifier des tâches cron pendant les périodes de faible trafic. Cependant, traiter avec des clients dans des fuseaux horaires différents peut présenter des défis, exigeant une approche réfléchie pour assurer une expérience harmonieuse dans plusieurs zones géographiques.

Si vous êtes en charge de l’optimisation des performances et du timing cron, consultez la configuration cron en cours dans l’Administration de Commerce et découvrez comment configurer les tâches cron pour les projets Commerce.

Vous pouvez également utiliser l’observation pour Adobe Commerce afin d’afficher les indicateurs de performances liés à cron. Cet outil associe des données de journal provenant de plusieurs sources pour vous aider à mieux gérer les performances du site Adobe Commerce et à diagnostiquer les problèmes.

En savoir plus sur l’implémentation d’Adobe Commerce cron :

- [Cron (tâches planifiées)](https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/cron.html) dans le Guide de l’utilisateur des systèmes d’administration Commerce __
- [Configuration de l’application - propriété crons](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/app/properties/crons-property.html) (infrastructure cloud)
- [Configuration et exécution de crons](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/app/properties/crons-property.html) (sur site)
- [Observation pour Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-operations/tools/observation-for-adobe-commerce/intro.html) (voir les onglets [!UICONTROL Cron] et [!UICONTROL MySQL]).
