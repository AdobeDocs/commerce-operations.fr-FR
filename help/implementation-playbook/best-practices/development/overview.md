---
title: Phase de développement de la mise en œuvre
description: Découvrez les bonnes pratiques de mise en œuvre pour la phase de développement des projets Adobe Commerce.
exl-id: 499c16df-0e4d-4950-8169-96356bdff1a7
feature: Best Practices
role: Developer
source-git-commit: cca301a72b972d843b878fae28901a47c8fc0489
workflow-type: tm+mt
source-wordcount: '336'
ht-degree: 2%

---


# Phase de développement

La phase de développement comprend les activités suivantes :

- Configuration des environnements local et d’évaluation
- Planification du sprint
- Exécution du ticket
- Dépannage
- Révision, fusion et test du code
- Révision au sprint
- Approbation du client

>[!TIP]
>
>Voir [Bonnes pratiques générales](general.md) pour des recommandations de haut niveau sur la gestion globale du processus de développement.

Les sections suivantes contiennent des informations sur les bonnes pratiques pour la phase de développement.

## Gestion du code

| Bonne pratique | Description |
|-----------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------|
| [ Révision du code ](code-review.md) | Processus de validation recommandé pour s’assurer que la fonctionnalité implémentée répond aux exigences |
| [Compositeur et Git](code-management.md) | Déterminez comment distribuer le code personnalisé en prenant en compte la gestion des versions, la complexité du code et la gestion des dépendances |
| [Stratégie d’embranchement](git-branching.md) | Gestion du code source dans les référentiels Git |

## Plateforme et services

| Bonne pratique | Description |
|--------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------|
| [Versions et déploiement](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/deploy/best-practices.html){target="_blank"} | Décrit les bonnes pratiques pour les étapes de création et de déploiement d’Adobe Commerce sur les projets d’infrastructure cloud |
| Débogage | Déboguer systématiquement et efficacement le framework Adobe Commerce |
| [Déploiement de contenu statique](static-content-deployment.md) | Évitez les problèmes liés au contenu statique qui n’apparaît pas sur votre storefront |
| [Dépannage](troubleshooting.md) | Résolution des problèmes courants d’implémentation d’Adobe Commerce |

## Base de données

| Bonne pratique | Description |
|----------------------------------------------------------------|---------------------------------------------------------------------------------|
| [Modification du tableau](modifying-core-and-third-party-tables.md) | Déterminez comment et quand modifier Adobe Commerce et les tables de bases de données tierces. |

## Optimisation des fichiers

| Bonne pratique | Description |
|-----------------------------------------------------|-----------------------------------------------------------------------------------------------------------|
| [Redimensionnement de l’image du catalogue](catalog-image-resizing.md) | Fournit des conseils sur le redimensionnement des images avant le démarrage en production d’un magasin pour garantir des performances optimales |
| [ CSS et JS ](optimize-css-js-files.md) | Fusionner et réduire les fichiers de feuille de style en cascade (CSS) et JavaScript (JS) depuis Admin ou la ligne de commande |
| [Images](image-optimization.md) | Optimisez les images et utilisez Fastly pour optimiser le temps de réponse |

## Développement frontal

| Bonne pratique | Description |
|----------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------|
| [Développement du thème](https://developer.adobe.com/commerce/frontend-core/guide/best-practices/){target="_blank"} | Décrit les modèles de développement pour garantir la compatibilité entre votre thème, les futures versions d’Adobe Commerce et les extensions personnalisées |

## Développement PHP

| Bonne pratique | Description |
|-----------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------|
| [Gestion des exceptions](exception-handling.md) | Décrit les méthodes recommandées pour la journalisation des exceptions |
| [ Extensions ](https://developer.adobe.com/commerce/php/best-practices/){target="_blank"} | Décrit les modèles de développement pour garantir la compatibilité entre votre extension, les futures versions d’Adobe Commerce et d’autres extensions personnalisées |
| [Blocs de contenu privés](private-content-block-configuration.md) | Configurer des blocs de contenu privés pour optimiser les performances du storefront |
| [Modification du code PHP principal et tiers](modifying-core-and-third-party-code.md) | Modifier la fonctionnalité, le résultat ou l’entrée d’un code que vous n’avez pas créé ou que vous ne contrôlez pas directement |
