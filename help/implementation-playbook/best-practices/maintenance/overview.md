---
title: Phase de maintenance de l’implémentation
description: Découvrez les bonnes pratiques d’implémentation pour la phase de maintenance des projets Adobe Commerce.
exl-id: bd052412-a41c-4dbd-9aba-ba2fcac31f2d
feature: Best Practices
source-git-commit: fb449f0ee7d503d0c7ba60bf6bfbe3f528060606
workflow-type: tm+mt
source-wordcount: '371'
ht-degree: 2%

---

# Phase de maintenance

La phase de maintenance comprend les activités suivantes :

- Correction de bugs
- Gestion des catalogues
- Configuration
- Améliorations des fonctionnalités
- Indexation
- Managed Services
- Surveillance de site
- Mises à niveau

Les sections suivantes contiennent des informations relatives aux bonnes pratiques pour la phase de maintenance.

## Correctifs de bugs

| Bonne pratique | Description |
|-----------------------------------------------------------------------------------|-------------------------------------------------------------------------------|
| [[!DNL Quality Patches Tool] utilisation](../../../tools/quality-patches-tool/usage.md) | Appliquez, revenez en arrière et affichez des informations générales sur tous les correctifs Adobe Commerce. |

## Gestion des catalogues

| Bonne pratique | Description |
|------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------|
| [Gestion de catalogue de produits](https://www.gotostage.com/channel/fca90f7960be436f9b849215d9e06026/recording/2eea2782fc874047a020391000519f8b/watch?source=CHANNEL) | Enregistrement Commerce &amp; Coffee qui décrit les stratégies de gestion des catalogues de produits. |

## Configuration

| Bonne pratique | Description |
|-------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------|
| [Planification des mises à jour d’administration sur les sites de production](scheduling-admin-updates-in-production.md) | Gérez les mises à jour Adobe Commerce critiques pour éviter les baisses de performances et les pannes. |

## Gestion de base de données

| Bonne pratique | Description |
|--------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------|
| [Résoudre les problèmes de performances des bases de données&#x200B;](resolve-database-performance-issues.md) | Correction des problèmes de base de données qui ralentissent les performances sur les sites Adobe Commerce déployés sur l’infrastructure cloud. |
| [Conditions préalables à la mise à niveau d’Adobe Commerce pour MariaDB&#x200B;](mariadb-upgrade.md) | Préparez votre base de données MariaDB pour une mise à niveau. |

## Améliorations des fonctionnalités

| Bonne pratique | Description |
|---------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------|
| [Personalization](https://www.gotostage.com/channel/fca90f7960be436f9b849215d9e06026/recording/e218545a77de490fb5102eca07d0580a/watch?source=CHANNEL) | Enregistrement Commerce &amp; Coffee qui décrit les stratégies de personnalisation. |
| [Tendances E-Commerce](https://www.gotostage.com/channel/fca90f7960be436f9b849215d9e06026/recording/9a772468d7b64409a3d5dff4d67e656d/watch?source=CHANNEL) | Enregistrement Commerce &amp; Coffee qui décrit les tendances du commerce électronique. |
| [Automatisation de l’IA](https://www.gotostage.com/channel/fca90f7960be436f9b849215d9e06026/recording/27ae23699c2847be981a23ca098e548f/watch?source=CHANNEL) | Enregistrement Commerce &amp; Coffee qui décrit les possibilités de personnalisation avec l’intelligence artificielle et l’automatisation. |

## Indexation

| Bonne pratique | Description |
|------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------|
| [Comment réindexer ](https://developer.adobe.com/commerce/php/development/components/indexing/#how-to-reindex) | Utilisez les tâches cron ou l’outil d’interface de ligne de commande pour exécuter la réindexation. |
| [Configuration des indexeurs&#x200B;](indexer-configuration.md) | Optimisez les performances du site en suivant les bonnes pratiques pour la configuration de l’indexeur. |
| [Traitement des commandes](order-processing-configuration.md) | Améliorez les performances de passage en caisse et de traitement des commandes. |

## Surveillance et sécurité du site

| Bonne pratique | Description |
|-------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------|
| [Audit des performances frontales](frontend-performance.md) | Identifiez et résolvez les problèmes qui affectent négativement les performances du site à l’aide d’outils de performances web. |
| [Prêt, prêt, maintenance](https://business.adobe.com/blog/basics/ready-set-maintain) | Conseils pour maintenir vos sites Adobe Commerce afin d’optimiser la valeur commerciale et la disponibilité. |
| [Utiliser  [!DNL Site-Wide Analysis Tool]](../../../tools/site-wide-analysis-tool/intro.md#integrations-with-other-adobe-commerce-support-tools) | Affichez des informations importantes sur votre site Adobe Commerce au même endroit. |
| [Surveillance des performances, de l’espace disque et des journaux](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/monitor/performance.html?lang=fr) | Utilisez New Relic pour surveiller les informations clés de performances de votre site d’infrastructure cloud Adobe Commerce. |
| [Réagir aux incidents de sécurité](respond-to-security-incident.md) | Utilisez New Relic pour surveiller les informations clés de performances de votre site d’infrastructure cloud Adobe Commerce. |

### Mises à niveau

| Bonne pratique | Description |
|-----------------------------------------------------------------------|--------------------------------------------------------------------------------------------|
| [Correctif à grande échelle](patching-at-scale.md) | Découvrez comment les correctifs centralisés pour Adobe Commerce peuvent vous aider à gérer les projets d’entreprise. |
| [Mettre à jour les services et composants vers la dernière version&#x200B;](update-services.md) | mettez à jour votre pile technologique Adobe Commerce on cloud infrastructure. |
| [ Liste de contrôle de mise à niveau pour Adobe Commerce &#x200B;](upgrade-checklist.md) | Créez et utilisez une liste de contrôle de mise à niveau pour planifier votre stratégie de mise à niveau Adobe Commerce. |
