---
title: Optimisation des performances du serveur principal
description: Découvrez l’optimisation des performances du serveur principal des sites Adobe Commerce.
badge: label="Contribution par objet" type="Informative" url="https://objectsource.co.uk/" tooltip="objectsource"
role: Admin, User, Developer
feature: Best Practices
exl-id: 18bc97a0-3d34-4d48-a3e2-84af2da7d0d3
source-git-commit: e5df5a7242dbe8ceff548257daeb39f7c9fc5c69
workflow-type: tm+mt
source-wordcount: '1075'
ht-degree: 0%

---

# Bonnes pratiques relatives à l’optimisation des performances du serveur principal

Cette rubrique décrit les bonnes pratiques pour étudier et optimiser les performances du serveur principal des sites Adobe Commerce en se concentrant sur l’optimisation et le test des bases de données. Les développeurs peuvent utiliser ces informations pour étudier le contexte unique de chaque projet Commerce et identifier les opportunités d’optimiser la configuration du serveur principal et les opérations afin d’améliorer les performances du site.

>[!NOTE]
>
>Recommendations et les exemples s’inspirent de processus que objectsource suit dans les engagements client réels pour fournir des sites Adobe Commerce hautement performants à grande échelle.

## Produits et versions concernés

[Toutes les versions prises en charge](../../../release/versions.md) de :

- Adobe Commerce sur l’infrastructure cloud
- Adobe Commerce sur site

## Optimisation de la base de données pour de meilleures performances

L’optimisation de la base de données est un moyen sûr d’améliorer l’expérience utilisateur et d’augmenter les ventes. Lorsque vous optimisez la base de données, la colonne vertébrale d’un site de commerce, vous pouvez éviter la lenteur des performances du site web et éliminer les longs temps de chargement qui créent des frictions pour les clients.

### Test de contrainte

Les périodes de trafic élevé, telles que Black Friday, exigent que les sites de commerce gèrent des volumes de trafic massifs. Pour préparer de tels événements, les tests de stress sont essentiels pour comprendre comment un site fonctionne avec des augmentations de charge exponentielles.

GTmetrix est l’un des outils que vous pouvez utiliser pour les tests de stress. Évaluez la préparation du site pour les augmentations de charge en configurant GTmetrix pour répliquer et multiplier le comportement et les actions normaux des visiteurs. Exécutez ensuite des tests afin d’identifier et de résoudre les problèmes susceptibles d’affecter les performances et la disponibilité du site lors des principaux événements d’achat.

En savoir plus sur la préparation des projets Commerce pour les périodes à fort trafic :

- [Préparation des vacances](https://experienceleague.adobe.com/docs/events/commerce-intelligence-webinar-recordings/2021/holiday-readiness.html)
- [Analyse des achats de vacances](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/analyze/performance/holiday-season-perf.html)
- [Augmentation de la capacité](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/2021-holiday-surge-capacity-requests-for-magento-commerce-cloud.html)

### Test de chargement

Vous pouvez également utiliser GTmetrix ou un outil similaire pour charger des projets Commerce de test. Avant les tests de stress, les tests de charge sont une pratique essentielle pour les sites à trafic élevé à grande échelle. Éviter les pannes de site inattendues, les clients frustrés et les pertes financières en anticipant et en atténuant les problèmes qui affectent les performances du site en cas de charge maximale.

Utilisez GTmetrix pour simuler un trafic important et analyser les performances du site afin d’obtenir des informations claires sur la capacité du site. Cette analyse permet d’identifier et de résoudre les goulets d’étranglement et d’identifier les opportunités d’optimisation, en veillant à ce que les sites de commerce puissent fonctionner efficacement sous une charge accrue.

En savoir plus sur le test des projets Adobe Commerce :

- [Instructions de test](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/guidance.html)  (infrastructure cloud)
- [Test d’application](https://developer.adobe.com/commerce/testing/guide/)

### Identification et résolution des problèmes de performances

Résolvez les problèmes de performances en utilisant divers outils tels que New Relic et Observation pour Adobe Commerce afin de détecter les goulets d’étranglement et d’optimiser efficacement les sites Commerce. [New Relic](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/monitor/new-relic/new-relic-service.html) est inclus dans Adobe Commerce sur l’infrastructure cloud ; et [Observation pour Adobe Commerce](/help/tools/observation-for-adobe-commerce/intro.md) est inclus pour les déploiements cloud et sur site.

Utilisez ces outils pour analyser les performances du site et identifier les problèmes de performances liés à :

- Fonctionnalités gourmandes en processeur
- Configuration de la gestion du cache pour les requêtes et les opérations principales
- Appels API tiers
- Planification Cron

Vous pouvez, par exemple, examiner de plus près les transactions en vous concentrant sur les pages de détails et de catégories d’un produit. Identifiez les processus chronophages qui peuvent être optimisés pour améliorer les performances. Dans un engagement client, objectsource a remarqué un problème de performance sur une page des détails du produit et a trouvé un appel API qui prenait 3,5 % du temps de performance. Sur la base de ce résultat, ils ont examiné la hiérarchie de l’exécution du code afin d’identifier et de résoudre le problème provoquant le goulot d’étranglement.

En savoir plus sur la gestion des performances du site :

- [Suivi des performances](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/monitor/performance.html) (infrastructure cloud)
- [Examen de l’optimisation des performances](/help/implementation-playbook/infrastructure/performance/recommendations.md)
- [Bonnes pratiques de configuration](/help/performance/configuration.md)
- [Observation pour Adobe Commerce](/help/tools/observation-for-adobe-commerce/intro.md)

### Optimisation des performances de MySQL

La résolution des problèmes de performances MySQL par l’implémentation de la mise en grappe de bases de données et de l’optimisation des requêtes est une approche efficace pour améliorer les performances avant et pendant les périodes à trafic élevé comme Black Friday.

#### Implémentation du clusterisation de base de données

Les sites Web à trafic élevé sont souvent confrontés à des goulets d’étranglement au niveau de la base de données, principalement dus à la dépendance à un seul serveur MySQL. Vous pouvez remédier à ces goulets d’étranglement en mettant en oeuvre la mise en grappe de la base de données, une architecture répartie qui améliore les performances et assure une haute disponibilité.

La mise en grappe de la base de données réduit l’impact des problèmes liés à la base de données pendant les périodes de trafic élevées en permettant à plusieurs noeuds web de se connecter à plusieurs serveurs MySQL. Utilisez des outils tels que la grappe Galera pour configurer la mise en grappe de bases de données pour les sites de commerce. La grappe Galera est incluse dans [Projets Adobe Commerce déployés sur l’infrastructure cloud](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/infrastructure/cloud/technology.html).

#### Optimisation des requêtes MySQL

En règle générale, l’infrastructure de la plupart des sites Adobe Commerce se compose de plusieurs noeuds web connectés à un seul serveur MySQL.

Dans cette configuration, chaque noeud web front-end se connecte à la grappe Galera, ce qui permet de disposer de plusieurs serveurs MySQL. L’augmentation du nombre de noeuds web front-end peut améliorer les performances de l’application, mais le seul serveur MySQL reste un goulot d’étranglement.

Pour optimiser les performances du serveur MySQL et réduire les goulets d’étranglement, il est essentiel d’identifier et de réduire les requêtes inutiles. Par exemple, si vous envoyez 1 000 requêtes par seconde, mais que 200 requêtes seulement sont nécessaires, l’optimisation et la réduction du nombre de requêtes peuvent améliorer considérablement les performances.

En savoir plus sur la configuration et l’optimisation de MySQL :

- [Bonnes pratiques relatives à la configuration des bases de données](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/planning/database-on-cloud.html)
- [Réplication lente pour la réplication de la base de données Galera](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/backend-development/galera-db-slow-replication.html)
- [Directives générales pour MySQL](/help/installation/prerequisites/database/mysql.md)
- [Mise en cache des requêtes MySQL](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/backend-development/mysql-query-cache.html)

## Gérer efficacement les tâches cron : performances et timing

Les tâches Cron jouent un rôle essentiel dans les tâches en arrière-plan du site de traitement, telles que la génération de rapports et l’indexation de produits. Toutefois, l’optimisation des tâches de cron nécessite une réflexion approfondie de leur impact sur les performances globales. Les développeurs doivent évaluer la fréquence de planification et déterminer le timing optimal en fonction de besoins spécifiques.

Pour équilibrer les performances et la commodité, il est souvent conseillé de planifier des tâches cron pendant les périodes de faible trafic. Toutefois, le traitement des clients dans différents fuseaux horaires peut présenter des défis, ce qui exige une approche réfléchie pour garantir une expérience harmonieuse dans plusieurs zones géographiques.

Si vous êtes responsable de l’optimisation des performances et du minutage de cron, passez en revue la configuration cron actuelle auprès de l’administrateur Commerce et découvrez comment configurer et configurer les tâches cron pour les projets Commerce.

Vous pouvez également utiliser Observation pour Adobe Commerce pour afficher les indicateurs de performances liés au cron. Cet outil combine les données de journal provenant de plusieurs sources afin de vous aider à mieux gérer les performances du site Adobe Commerce et à diagnostiquer les problèmes.

En savoir plus sur l’implémentation d’Adobe Commerce cron :

- [Cron (tâches planifiées)](https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/cron.html) dans le _Guide de l’utilisateur de Commerce Admin Systems_
- [Configuration de l’application - propriété crons](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/app/properties/crons-property.html) (infrastructure cloud)
- [Configuration et exécution des crons](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/app/properties/crons-property.html) (sur place)
- [Observation pour Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-operations/tools/observation-for-adobe-commerce/intro.html) (Voir [!UICONTROL Cron] et [!UICONTROL MySQL] onglets.)
