---
title: Phase de maintenance de la mise en oeuvre
description: Découvrez les bonnes pratiques de mise en oeuvre pour la phase de maintenance des projets Adobe Commerce.
exl-id: bd052412-a41c-4dbd-9aba-ba2fcac31f2d
feature: Best Practices
source-git-commit: fb449f0ee7d503d0c7ba60bf6bfbe3f528060606
workflow-type: tm+mt
source-wordcount: '371'
ht-degree: 2%

---

# Phase de maintenance

La phase de maintenance comprend les activités suivantes :

- Correction de bogues
- Gestion des catalogues
- Configuration
- Améliorations des fonctionnalités
- Indexation
- Managed Services
- Surveillance du site
- Mises à niveau

Les sections suivantes contiennent des informations sur les bonnes pratiques relatives à la phase de maintenance.

## Correctifs

| Bonne pratique | Description |
|-----------------------------------------------------------------------------------|-------------------------------------------------------------------------------|
| [[!DNL Quality Patches Tool] usage](../../../tools/quality-patches-tool/usage.md) | Appliquez, annulez et affichez des informations générales sur tous les correctifs Adobe Commerce. |

## Gestion des catalogues

| Bonne pratique | Description |
|------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------|
| [Gestion de catalogue de produits](https://www.gotostage.com/channel/fca90f7960be436f9b849215d9e06026/recording/2eea2782fc874047a020391000519f8b/watch?source=CHANNEL) | Enregistrement Commerce et café qui décrit les stratégies de gestion des catalogues de produits. |

## Configuration

| Bonne pratique | Description |
|-------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------|
| [Planification des mises à jour de l’administrateur sur les sites de production](scheduling-admin-updates-in-production.md) | Gérez les mises à jour critiques d’Adobe Commerce afin d’éviter des performances et des pannes lentes. |

## Gestion des bases de données

| Bonne pratique | Description |
|--------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------|
| [ Résolution des problèmes de performances de la base de données &#x200B;](resolve-database-performance-issues.md) | Correction de problèmes de base de données qui ralentissent les performances des sites Adobe Commerce déployés sur l’infrastructure cloud. |
| [Conditions préalables à la mise à niveau d’Adobe Commerce pour MariaDB &#x200B;](mariadb-upgrade.md) | Préparez votre base de données MariaDB pour une mise à niveau. |

## Améliorations des fonctionnalités

| Bonne pratique | Description |
|---------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------|
| [Personalization](https://www.gotostage.com/channel/fca90f7960be436f9b849215d9e06026/recording/e218545a77de490fb5102eca07d0580a/watch?source=CHANNEL) | Enregistrement Commerce et café qui décrit les stratégies de personnalisation. |
| [Tendances E-Commerce](https://www.gotostage.com/channel/fca90f7960be436f9b849215d9e06026/recording/9a772468d7b64409a3d5dff4d67e656d/watch?source=CHANNEL) | Enregistrement Commerce et café qui décrit les tendances du commerce électronique. |
| [Automatisation de l’IA](https://www.gotostage.com/channel/fca90f7960be436f9b849215d9e06026/recording/27ae23699c2847be981a23ca098e548f/watch?source=CHANNEL) | Enregistrement Commerce et café qui décrit les possibilités de personnalisation avec intelligence artificielle et automatisation. |

## Indexation

| Bonne pratique | Description |
|------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------|
| [Comment réindexer](https://developer.adobe.com/commerce/php/development/components/indexing/#how-to-reindex) | Utilisez les tâches cron ou l’outil d’interface de ligne de commande pour exécuter la réindexation. |
| [Configuration des indexeurs &#x200B;](indexer-configuration.md) | Optimisez les performances du site en suivant les bonnes pratiques de configuration de l’indexeur. |
| [Traitement de la commande](order-processing-configuration.md) | Améliorez les performances de traitement du passage en caisse et des commandes. |

## Surveillance et sécurité du site

| Bonne pratique | Description |
|-------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------|
| [ Performances du serveur frontal d&#39;audit](frontend-performance.md) | Identifiez et résolvez les problèmes qui ont un impact négatif sur les performances du site à l’aide des outils de performances web. |
| [Prêt, Défini, Conserver](https://business.adobe.com/blog/basics/ready-set-maintain) | Conseils pour la maintenance de vos sites Adobe Commerce afin de maximiser la valeur ajoutée et le temps de disponibilité de l’entreprise. |
| [Utilisez le  [!DNL Site-Wide Analysis Tool]](../../../tools/site-wide-analysis-tool/intro.md#integrations-with-other-adobe-commerce-support-tools) | Affichez les informations importantes sur votre site Adobe Commerce à un seul endroit. |
| [Surveillance des performances, de l’espace disque et des journaux](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/monitor/performance.html?lang=fr) | Utilisez New Relic pour surveiller les informations de performances clés relatives à votre Adobe Commerce sur le site d’infrastructure cloud. |
| [Répondre aux incidents de sécurité](respond-to-security-incident.md) | Utilisez New Relic pour surveiller les informations de performances clés relatives à votre Adobe Commerce sur le site d’infrastructure cloud. |

### Mises à niveau

| Bonne pratique | Description |
|-----------------------------------------------------------------------|--------------------------------------------------------------------------------------------|
| [Application de correctifs à l’échelle](patching-at-scale.md) | Découvrez comment l’application de correctifs centralisés pour Adobe Commerce peut vous aider à gérer les projets d’entreprise. |
| [ Mettre à jour les services et les composants vers la dernière version &#x200B;](update-services.md) | maintenez votre Adobe Commerce à jour sur la pile de technologie de l’infrastructure cloud. |
| [Liste de contrôle de mise à niveau pour Adobe Commerce &#x200B;](upgrade-checklist.md) | Créez et utilisez une liste de contrôle de mise à niveau pour planifier votre stratégie de mise à niveau d’Adobe Commerce. |
