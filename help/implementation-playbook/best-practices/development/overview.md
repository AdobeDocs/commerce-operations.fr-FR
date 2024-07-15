---
title: Phase de développement de mise en oeuvre
description: Découvrez les bonnes pratiques de mise en oeuvre pour la phase de développement des projets Adobe Commerce.
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

- Configuration de l’environnement local et d’évaluation
- Planification Sprint
- Exécution des billets
- Dépannage
- Révision, fusion et test du code
- Révision Sprint
- Validation client

>[!TIP]
>
>Pour obtenir des recommandations de haut niveau sur la gestion globale du processus de développement, voir [bonnes pratiques générales](general.md) .

Les sections suivantes contiennent des informations sur les bonnes pratiques pour la phase de développement.

## Gestion du code

| Bonne pratique | Description |
|-----------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------|
| [Examen du code](code-review.md) | Processus de validation recommandé pour s’assurer que les fonctionnalités mises en oeuvre répondent aux exigences |
| [Compositeur par rapport à Git](code-management.md) | Déterminer comment distribuer du code personnalisé en tenant compte de la gestion des versions, de la complexité du code et de la gestion des dépendances |
| [Stratégie d&#39;embranchement](git-branching.md) | Gestion du code source dans les référentiels Git |

## Plateforme et services

| Bonne pratique | Description |
|--------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------|
| [Versions et déploiement](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/deploy/best-practices.html){target="_blank"} | Décrit les bonnes pratiques pour les étapes de création et de déploiement d’Adobe Commerce sur les projets d’infrastructure cloud |
| Débogage | Débogage systématique et efficace de la structure Adobe Commerce |
| [Déploiement de contenu statique](static-content-deployment.md) | Évitez les problèmes liés au contenu statique qui n’apparaît pas sur votre storefront. |
| [Dépannage](troubleshooting.md) | Résolution des problèmes courants de mise en oeuvre d’Adobe Commerce |

## Base

| Bonne pratique | Description |
|----------------------------------------------------------------|---------------------------------------------------------------------------------|
| [Modification de table](modifying-core-and-third-party-tables.md) | Déterminer comment et à quel moment modifier des tables de base de données tierces et Adobe Commerce |

## Optimisation des fichiers

| Bonne pratique | Description |
|-----------------------------------------------------|-----------------------------------------------------------------------------------------------------------|
| [Redimensionnement d’image du catalogue](catalog-image-resizing.md) | Fournit des conseils sur le redimensionnement des images avant que le magasin ne passe en production pour garantir des performances optimales |
| [CSS et JS](optimize-css-js-files.md) | Fusion et minimisation de fichiers CSS (feuilles de style en cascade) et JavaScript (JS) depuis l’administrateur ou la ligne de commande |
| [Images](image-optimization.md) | Optimisation des images et utilisation rapide pour optimiser le temps de réponse |

## Développement des frontières

| Bonne pratique | Description |
|----------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------|
| [Développement de thème](https://developer.adobe.com/commerce/frontend-core/guide/best-practices/){target="_blank"} | Décrit les modèles de développement pour garantir la compatibilité entre votre thème, les versions futures d’Adobe Commerce et les extensions personnalisées. |

## développement PHP

| Bonne pratique | Description |
|-----------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------|
| [Gestion des exceptions](exception-handling.md) | Décrit les méthodes recommandées de journalisation des exceptions |
| [Extensions](https://developer.adobe.com/commerce/php/best-practices/){target="_blank"} | Décrit les modèles de développement pour garantir la compatibilité entre votre extension, les versions futures d’Adobe Commerce et d’autres extensions personnalisées. |
| [Blocs de contenu privé](private-content-block-configuration.md) | Configuration de blocs de contenu privés pour optimiser les performances du storefront |
| [Modifier le code PHP principal et tiers](modifying-core-and-third-party-code.md) | Modifiez la fonctionnalité, le résultat ou la saisie de tout code que vous n’avez pas créé ou dont vous n’avez pas directement le contrôle. |
