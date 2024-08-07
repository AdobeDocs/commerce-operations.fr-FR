---
user-guide-title: Manuel d’implémentation
user-guide-description: Découvrez les stratégies de planification et d’implémentation d’un site Adobe Commerce performant.
mini-toc-levels: 3
source-git-commit: 36a2a86cbafab1e4913573b1c8431524ba43dc6a
workflow-type: tm+mt
source-wordcount: '257'
ht-degree: 12%

---


# Manuel d’implémentation {#implementation-playbook}

- [Vue d’ensemble](overview.md)
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
   - [Référence d’entreprise](architecture/enterprise-blueprint.md)
   - Architecture de référence globale {#global-reference-architecture}
      - [Vue d’ensemble](architecture/global-reference/overview.md)
      - [Exemples](architecture/global-reference/examples.md)
      - Développement du compositeur {#composer}
         - [Vue d’ensemble](architecture/global-reference/composer/overview.md)
         - [Structure du projet](architecture/global-reference/composer/project-structure.md)
         - [Conseils et astuces](architecture/global-reference/composer/tips-and-tricks.md)
- Infrastructure et déploiement {#infrastructure}
   - [Vue d’ensemble](infrastructure/overview.md)
   - Hébergement automatique {#self-hosting}
      - [Vue d’ensemble](infrastructure/self-hosting/overview.md)
      - [Infrastructure sur site](infrastructure/self-hosting/on-premises.md)
      - [Concepts de sécurité](infrastructure/self-hosting/security-concepts.md)
      - [Surveillance de la télémétrie et des outils](infrastructure/self-hosting/monitoring-tools.md)
      - [Idées de reprise sur sinistre](infrastructure/self-hosting/disaster-recovery-ideas.md)
      - [Conseils sur les performances](infrastructure/self-hosting/performance-tips.md)
   - infrastructure cloud {#cloud}
      - [Vue d’ensemble](infrastructure/cloud/overview.md)
      - [Régions](infrastructure/cloud/regions.md)
      - [Technologies](infrastructure/cloud/technology.md)
      - [Sécurité et conformité](infrastructure/cloud/security.md)
   - Optimisation des performances {#performance}
      - [Problèmes standard](infrastructure/performance/optimization.md)
      - [Benchmarks](infrastructure/performance/benchmarks.md)
      - [Recommendations](infrastructure/performance/recommendations.md)
- Préparation au lancement {#launch}
   - [Vue d’ensemble](launch/overview.md)
   - [Étapes de prélancement](launch/pre-launch-steps.md)
   - [Étapes de lancement](launch/launch-steps.md)
   - [Étapes de lancement de Post](launch/post-launch-steps.md)
- Maintenance et support {#maintenance}
   - [Vue d’ensemble](maintenance/overview.md)
   - [Adobe Managed Services](maintenance/adobe-managed-services.md)
- Bonnes pratiques {#best-practices}
   - [Vue d’ensemble](best-practices/phases.md)
   - Planification {#planning}
      - [Vue d’ensemble](best-practices/planning/overview.md)
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
      - [Vue d’ensemble](best-practices/development/overview.md)
      - [Bonnes pratiques générales](best-practices/development/general.md)
      - [Gestion du code](best-practices/development/code-management.md)
      - [Révision du code](best-practices/development/code-review.md)
      - [Débogage](best-practices/development/debugging.md)
      - [Gestion des exceptions](best-practices/development/exception-handling.md)
      - [Embranchement Git](best-practices/development/git-branching.md)
      - [Redimensionnement des images du catalogue](best-practices/development/catalog-image-resizing.md)
      - [Optimisation des images](best-practices/development/image-optimization.md)
      - [Dépannage](best-practices/development/troubleshooting.md)
      - [Optimisation des fichiers CSS et JS](best-practices/development/optimize-css-js-files.md)
      - [Blocs de contenu privé](best-practices/development/private-content-block-configuration.md)
      - [Déploiement de contenu statique](best-practices/development/static-content-deployment.md)
      - [Modification des tables de base de données](best-practices/development/modifying-core-and-third-party-tables.md)
      - [Modification du code principal et du code tiers](best-practices/development/modifying-core-and-third-party-code.md)
   - Lancement {#launch}
      - [Vue d’ensemble](best-practices/launch/overview.md)
      - [Configuration des moteurs de recherche web](best-practices/launch/robots-txt.md)
      - [Sécurisez votre site et votre infrastructure](best-practices/launch/security-best-practices.md)
   - Maintenance {#maintenance}
      - [Vue d’ensemble](best-practices/maintenance/overview.md)
      - [Performances du serveur frontal d’audit](best-practices/maintenance/frontend-performance.md)
      - [Optimisation des performances du serveur principal](best-practices/maintenance/backend-performance.md)
      - [Configuration de l’indexeur](best-practices/maintenance/indexer-configuration.md)
      - [Application de correctifs à l’échelle](best-practices/maintenance/patching-at-scale.md)
      - [Traitement des commandes](best-practices/maintenance/order-processing-configuration.md)
      - [Résolution des problèmes de performances de la base de données](best-practices/maintenance/resolve-database-performance-issues.md)
      - [Réaction aux incidents de sécurité](best-practices/maintenance/respond-to-security-incident.md)
      - [Planification des mises à jour de l’administrateur sur les sites de production](best-practices/maintenance/scheduling-admin-updates-in-production.md)
      - [Mise à jour des services](best-practices/maintenance/update-services.md)
      - [Liste de contrôle de mise à niveau](best-practices/maintenance/upgrade-checklist.md)
      - [Conditions préalables à la mise à niveau pour MariaDB](best-practices/maintenance/mariadb-upgrade.md)
- [Retour aux guides opérationnels](https://experienceleague.adobe.com/docs/commerce-operations/operational-guides/home.html)
