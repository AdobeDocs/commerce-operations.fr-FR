---
user-guide-title: Manuel d’implémentation
user-guide-description: Découvrez les stratégies de planification et d’implémentation d’un site Adobe Commerce performant.
mini-toc-levels: 3
source-git-commit: 3e0187b7eeb6475ea9c20bc1da11c496b57853d1
workflow-type: tm+mt
source-wordcount: '254'
ht-degree: 11%

---


# Manuel d’implémentation {#implementation-playbook}

- [Présentation](overview.md)
- Commerce {#intro}
   - [À propos d’Adobe Commerce](intro/about-commerce.md)
   - [Principes de développement de plates-formes](intro/platform-development.md)
- Portée du projet {#project-scope}
   - [Le savoir est un pouvoir](project-scope/knowledge.md)
   - [Principaux intervenants](project-scope/key-stakeholders.md)
   - [Processus et chronologie](project-scope/process-timeline.md)
   - [Deliverables](project-scope/deliverables.md)
   - [Listes de contrôle des exigences](project-scope/requirement-checklists.md)
- Développement {#development}
   - [Outils Platform](development/platform-tools.md)
   - [Outils de gestion de projet](development/project-management-tools.md)
   - [Méthodologie de mise en oeuvre du projet](development/delivery.md)
   - [Contrôle qualité](development/quality-control.md)
- Planification et gouvernance {#planning}
   - [Approche de livraison et de planification](planning/delivery.md)
   - [Responsabilité et propriété](planning/ownership.md)
   - [Gouvernance des projets](planning/governance.md)
- Architecture et intégrations {#architecture}
   - [Fonctionnalités](architecture/capabilities.md)
   - [Stratégie d’intégration](architecture/integration-strategy.md)
   - [Stratégie d&#39;extensibilité](architecture/extensibility-strategy.md)
   - [Options d’intégration](architecture/integration-options.md)
   - [Architecture de référence globale](architecture/global-reference.md)
   - Commerce sans tête {#headless}
      - [Avantages](architecture/headless/benefits.md)
      - [Parcours à sans tête](architecture/headless/journey-to-headless.md)
      - [Microservices](architecture/headless/microservices.md)
      - [L&#39;évolution des sans-tête](architecture/headless/evolution.md)
      - [Architecture du storefront combinée](architecture/headless/legacy-storefront.md)
      - [Architecture sans affichage](architecture/headless/adobe-commerce.md)
- Infrastructure et déploiement {#infrastructure}
   - [Présentation](infrastructure/overview.md)
   - Auto-hébergement {#self-hosting}
      - [Présentation](infrastructure/self-hosting/overview.md)
      - [Infrastructure sur site](infrastructure/self-hosting/on-premises.md)
      - [Concepts de sécurité](infrastructure/self-hosting/security-concepts.md)
      - [Surveillance de la télémétrie et des outils](infrastructure/self-hosting/monitoring-tools.md)
      - [Idées de reprise sur sinistre](infrastructure/self-hosting/disaster-recovery-ideas.md)
      - [Conseils sur les performances](infrastructure/self-hosting/performance-tips.md)
   - infrastructure cloud {#cloud}
      - [Présentation](infrastructure/cloud/overview.md)
      - [Régions](infrastructure/cloud/regions.md)
      - [Technologies](infrastructure/cloud/technology.md)
      - [Environnements](infrastructure/cloud/environments.md)
      - [Services gérés](infrastructure/cloud/managed-services.md)
      - [Sécurité et conformité](infrastructure/cloud/security.md)
   - Optimisation des performances {#performance}
      - [Problèmes standard](infrastructure/performance/optimization.md)
      - [Benchmarks](infrastructure/performance/benchmarks.md)
      - [Recommendations](infrastructure/performance/recommendations.md)
- Préparation à Launch {#launch}
   - [Présentation](launch/overview.md)
   - [Étapes de prélancement](launch/pre-launch-steps.md)
   - [Étapes de lancement](launch/launch-steps.md)
   - [Étapes de post-lancement](launch/post-launch-steps.md)
- Maintenance et assistance {#maintenance}
   - [Présentation](maintenance/overview.md)
   - [Adobe Managed Services](maintenance/adobe-managed-services.md)
- Bonnes pratiques {#best-practices}
   - [Présentation](best-practices/phases.md)
   - Planification {#planning}
      - [Présentation](best-practices/planning/overview.md)
      - [Gestion des catalogues](best-practices/planning/catalog-management.md)
      - [Configuration de la vue Sites, magasins et magasin](best-practices/planning/sites-stores-store-views.md)
      - [Configuration des rapports](best-practices/planning/reporting-configuration.md)
      - [Configuration de la base de données pour les déploiements dans le cloud &#x200B;](best-practices/planning/database-on-cloud.md)
      - [Configuration MySQL](best-practices/planning/mysql-configuration.md)
      - [Configuration du service Redis](best-practices/planning/redis-service-configuration.md)
      - [Taille de la mémoire OPcache](best-practices/planning/opcache-memory-size.md)
      - [Taille du cache du chemin d’accès réel](best-practices/planning/realpath-cache-size.md)
      - [Extensions](best-practices/planning/extensions.md)
      - [Réaffectations de partenaire](best-practices/planning/partner-escalation.md)
      - [Traitement du stockage des paiements](best-practices/planning/payment-processing-storage.md)
   - Développement {#development}
      - [Présentation](best-practices/development/overview.md)
      - [Optimisation des images](best-practices/development/image-optimization.md)
      - [Dépannage](best-practices/development/troubleshooting.md)
      - [Optimisation des fichiers CSS et JS](best-practices/development/optimize-css-js-files.md)
      - [Blocs de contenu privé](best-practices/development/private-content-block-configuration.md)
      - [Déploiement de contenu statique](best-practices/development/static-content-deployment.md)
      - [Modification des tables de base de données](best-practices/development/modifying-core-and-third-party-tables.md)
   - Launch {#launch}
      - [Présentation](best-practices/launch/overview.md)
      - [Adobe Security Notification Service](best-practices/launch/security-notification-service.md)
      - [Configuration du fichier robots.txt](best-practices/launch/robots-txt.md)
      - [Prévention et intervention en cas d’incident de sécurité](best-practices/launch/prevent-respond-security-incident.md)
   - Maintenance {#maintenance}
      - [Présentation](best-practices/maintenance/overview.md)
      - [Performances du serveur frontal d’audit](best-practices/maintenance/frontend-performance.md)
      - [Configuration de l’indexeur](best-practices/maintenance/indexer-configuration.md)
      - [Application de correctifs à l’échelle](best-practices/maintenance/patching-at-scale.md)
      - [Traitement des commandes](best-practices/maintenance/order-processing-configuration.md)
      - [Résolution des problèmes de performances de la base de données](best-practices/maintenance/resolve-database-performance-issues.md)
      - [Planification des mises à jour de l’administrateur sur les sites de production](best-practices/maintenance/scheduling-admin-updates-in-production.md)
      - [Mise à jour des services](best-practices/maintenance/update-services.md)
      - [Liste de contrôle de mise à niveau](best-practices/maintenance/upgrade-checklist.md)
      - [Conditions préalables à la mise à niveau pour MariaDB](best-practices/maintenance/commerce-235-upgrade-prerequisites-mariadb.md)
- [Revenir aux guides opérationnels](https://experienceleague.adobe.com/docs/commerce-operations/operational-guides/home.html)
