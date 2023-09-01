---
title: Présentation de l’infrastructure cloud
description: Découvrez Adobe Commerce sur l’infrastructure cloud.
exl-id: 94cf1505-0853-4e01-ba55-befc1117fbdb
feature: Cloud
source-git-commit: c737a8e902c960c933e54e2521107475bb1e5a22
workflow-type: tm+mt
source-wordcount: '557'
ht-degree: 0%

---


# Présentation

L’une des options d’hébergement géré les plus populaires pour Adobe Commerce sur AWS est proposée par Adobe Commerce. Adobe Commerce sur l’infrastructure cloud est une plateforme d’hébergement automatisée entièrement gérée pour le logiciel Adobe Commerce.

Adobe Commerce sur l’infrastructure cloud est une plateforme en tant que service (PaaS) qui permet le déploiement rapide de storefronts web entièrement personnalisables, sécurisés et évolutifs, associée à une infrastructure d’hébergement et de Managed Services de pointe. Il propose deux plans avec des infrastructures différentes. Adobe Commerce [Starter](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/cloud-architecture.html#starter-projects) Les plans sont mieux adaptés aux petits magasins moins complexes et aux catalogues plus petits. Adobe Commerce [Pro](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/cloud-architecture.html#pro-projects) Les plans sont conçus pour les grands magasins plus complexes, les catalogues de produits plus volumineux ou le trafic qui atteint des sommets. Adobe détermine l’architecture appropriée avec l’entrée des partenaires.

Adobe Commerce est prêt pour le cloud avec une infrastructure d’hébergement multi-cloud entièrement redondante qui offre des performances optimisées, une résilience et une évolutivité élastique. Vous pouvez exécuter efficacement votre plateforme commerciale sur le réseau de diffusion de contenu (CDN) de Fastly. Avec New Relic pour la surveillance et la gestion, vous pouvez préserver le bon fonctionnement de votre environnement de magasin.

Adobe Commerce offre tous les avantages de l’informatique cloud moderne les plus couramment associés aux solutions SaaS tout en conservant une certaine flexibilité en matière de personnalisation logicielle :

- Évolutivité élastique
- Haute résilience et disponibilité
- Conformité PCI
- Disponibilité globale et correction automatisée

![Diagramme présentant les éléments architecturaux d’Adobe Commerce sur l’infrastructure cloud](../../../assets/playbooks/adobe-commerce-cloud-infrastructure.svg)

## Avantages

Les autres avantages d’Adobe Commerce sont les suivants :

- **Optimisé pour Adobe Commerce**. Les scripts de génération et la configuration de service développés par Adobe Commerce garantissent que chaque instance est correctement affinée et configurée pour des performances commerciales optimales.

- **Versions homogènes et sécurisées**. Tous les déploiements de code sont basés sur Git pour assurer la cohérence et la répétabilité, avec des environnements de production en lecture seule pour une sécurité renforcée.

- **Flexibilité pour les partenaires**. Une API REST complète et une interface de ligne de commande scriptable facilitent l’intégration aux systèmes externes et la compatibilité avec les workflows de gestion de code existants.

- **Ensemble d’outils de déploiement flexible**. Effectuez rapidement une rotation, une fusion, un clonage et décompressez un nombre illimité d’environnements à volonté pour les tâches de développement, les tests d’assurance qualité ou le diagnostic des problèmes de production.

- **Diffusion cloud continue**. Passez en toute confiance du développement à l’UAT en passant par la production, de manière continue dans les branches de code et les équipes de développement.

## Services tiers

Cette section résume les services et outils tiers clés d’Adobe Commerce sur les projets d’infrastructure cloud. Voir [Pile de technologie](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/tech-stack.html) dans le _Guide de Cloud_ pour plus d’informations.

- **Réseau de diffusion de contenu Fastly**: à mesure que les clients accèdent à votre site et stockent, les demandes atteignent Fastly afin de charger plus rapidement les pages mises en cache. Fastly WAF fournit également un service de protection DDoS.

- **New Relic**: fournit une vue complète de vos applications et de votre environnement d’exploitation. New Relic vous permet de combiner les mesures clés des applications mobiles et de navigateur avec les services, les entrepôts de données et les hôtes de prise en charge afin d’optimiser les performances de manière holistique et d’assurer le succès de chaque initiative.

- **Compositeur**: gère les dépendances et les mises à niveau dans Adobe Commerce et fournit un contexte sur les modules inclus, sur leur fonctionnement et sur la manière dont ils s’assemblent.

- **Git**: permet de gérer le code source. Git permet l’embranchement local, des zones d’évaluation pratiques et plusieurs workflows avec création et déploiement automatiques pour un développement rapide et un déploiement continu efficaces.

- **Plateforme en tant que service (PaaS)**: fournit une infrastructure préconfigurée qui inclut PHP, MySQL, Redis, [!DNL RabbitMQ]et les technologies OpenSearch ou Elasticsearch.

- **Hébergement cloud d’AWS ou Azure**: optimise l’infrastructure en tant que service (IaaS) sous-jacente, qui offre un environnement évolutif et sécurisé pour les ventes en ligne et la vente au détail.
