---
title: Présentation de l’infrastructure cloud
description: Découvrez Adobe Commerce sur l’infrastructure cloud.
source-git-commit: 748c302527617c6a9bf7d6e666c6b3acff89e021
workflow-type: tm+mt
source-wordcount: '536'
ht-degree: 0%

---


# Présentation

L’une des options d’hébergement géré les plus populaires pour Adobe Commerce sur AWS est proposée par Adobe Commerce lui-même. Adobe Commerce sur l’infrastructure cloud est une plateforme d’hébergement automatisée entièrement gérée pour le logiciel Adobe Commerce.

Adobe Commerce sur l’infrastructure cloud est une offre de plateforme en tant que service (PaaS) qui permet le déploiement rapide de storefronts web entièrement personnalisables, sécurisés et évolutifs, associée à une infrastructure d’hébergement et de services gérés de pointe. Il propose deux plans avec des infrastructures différentes. Adobe Commerce Starter est plus adapté aux petits magasins moins complexes et aux catalogues plus petits. Adobe Commerce Pro est conçu pour les grands magasins plus complexes, les catalogues de produits plus volumineux ou les pics de trafic. Adobe Commerce détermine l’architecture appropriée avec l’apport de partenaires.

Adobe Commerce est prêt pour le cloud avec une infrastructure d’hébergement multi-cloud entièrement redondante qui offre des performances optimisées, une résilience et une évolutivité élastique. Vous pouvez exécuter efficacement votre plateforme commerciale sur le réseau de diffusion de contenu (CDN) de Fastly. Grâce à la nouvelle version pour la surveillance et la gestion, vous pouvez préserver le bon fonctionnement de votre environnement de stockage.

Adobe Commerce offre tous les avantages de l’informatique cloud moderne les plus couramment associés aux solutions SaaS : évolutivité élastique, haute résilience et disponibilité, conformité PCI, disponibilité globale et correction automatisée, tout en maintenant une flexibilité en matière de personnalisation logicielle requise par nos commerçants.

![Diagramme présentant les éléments architecturaux d’Adobe Commerce sur l’infrastructure cloud](../../../assets/playbooks/adobe-commerce-cloud-infrastructure.svg)

## Avantages

Les autres avantages d’Adobe Commerce incluent :

- **Optimized for Adobe Commerce**. Adobe Commerce-developed build scripts and service configuration ensure every instance is correctly tuned and configured for optimal merchant performance.

- **Versions** cohérentes et sécurisées. Tous les déploiements de code sont basés sur Git pour assurer la cohérence et la répétabilité, avec des environnements de production en lecture seule pour une sécurité renforcée.

- **Flexibilité pour les partenaires**. Une API REST complète et une interface de ligne de commande scriptable facilitent l’intégration aux systèmes externes et la compatibilité avec les workflows de gestion de code existants.

- **Ensemble d’outils de déploiement flexible**. Effectuez rapidement une rotation, une fusion, un clonage et décompressez un nombre illimité d’environnements à volonté pour les tâches de développement, les tests d’assurance qualité ou le diagnostic des problèmes de production.

- **Diffusion cloud continue**. Passez en toute confiance du développement à l’UAT en passant par la production, de manière continue dans les branches de code et les équipes de développement.

## Services tiers

Examinons également le logiciel qui fait des avantages d’Adobe Commerce une réalité.

![Diagramme présentant Adobe Commerce sur la pile de technologie de l’infrastructure cloud](../../../assets/playbooks/cloud-tech-stack.svg)

- Réseau de diffusion de contenu Fastly : À mesure que les clients accèdent à votre site et stockent, les demandes atteignent Fastly afin de charger plus rapidement les pages mises en cache. Fastly WAF fournit également un service de protection DDoS.

- Nouvelle Relique vous donne une vue complète de vos applications et de votre environnement d’exploitation. Il vous permet de combiner les mesures clés des applications mobiles et des navigateurs avec les services de prise en charge, les entrepôts de données et les hôtes afin que vous puissiez optimiser les performances de manière holistique et assurer le succès de chaque initiative.

- Le compositeur gère les dépendances et les mises à niveau dans Adobe Commerce et fournit un contexte sur les modules inclus, sur leur fonctionnement et sur la manière dont ils s’assemblent.

- Git est votre code dans les référentiels. Il permet l’embranchement local, des zones d’évaluation pratiques et plusieurs workflows avec création et déploiement automatiques pour un développement rapide et un déploiement continu efficaces.

- Platform-as-a-Service (PaaS) fournit une infrastructure préconfigurée qui comprend des technologies PHP, MySQL, Redis, RabbitMQ et Elasticsearch.

- L’hébergement cloud d’AWS ou d’Azure alimente l’infrastructure en tant que service (IaaS) sous-jacente, qui offre un environnement évolutif et sécurisé pour les ventes en ligne et la vente au détail.
