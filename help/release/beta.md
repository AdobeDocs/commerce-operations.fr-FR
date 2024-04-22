---
title: Versions bêta
description: Découvrez les versions bêta d’Adobe Commerce et comment y participer.
exl-id: 662cb061-995f-4e09-a2ef-9e607cc0000b
source-git-commit: 1dd4b44c6aa685795e16dccebfaf073dcc0062f2
workflow-type: tm+mt
source-wordcount: '690'
ht-degree: 0%

---

# Versions bêta d’Adobe Commerce

Les programmes bêta d’Adobe Commerce sont un moyen pour les marchands d’accéder aux fonctionnalités et au code de version préliminaire, de fournir des commentaires et de guider l’avenir d’Adobe Commerce. Il existe deux types de programmes bêta :

- Version bêta publique : un programme bêta public est disponible pour tous les clients et partenaires d’Adobe Commerce
- Beta privée : un programme bêta privé peut nécessiter une approbation basée sur des critères admissibles pour participer.

>[!IMPORTANT]
>
>Les versions bêta peuvent contenir des défauts et sont fournies &quot;EN L’ÉTAT&quot; sans aucune garantie de quelque type que ce soit. Adobe n’aura aucune obligation de gérer, corriger, mettre à jour, modifier, modifier ou d’autre manière prendre en charge (via les services d’assistance d’Adobe ou d’une autre manière) les versions bêta. Il est conseillé aux clients de faire preuve de prudence et de ne pas s’appuyer d’aucune manière sur le bon fonctionnement ou les performances des versions bêta et/ou de la documentation ou des documents associés. Les fonctionnalités et les API en version bêta peuvent être modifiées sans préavis. Par conséquent, toute utilisation des versions bêta est entièrement à la charge du client.

## Avantages de la participation

L’obtention d’un accès anticipé aux fonctionnalités qu’Adobe développe permet aux clients et aux partenaires de fournir des commentaires, de façonner le développement de produits et de se préparer à adopter de nouvelles fonctionnalités avant la disponibilité générale.

## Programmes bêta actuels

Consultez les sections suivantes pour obtenir la liste des programmes bêta actifs.

### Intégration du système de gestion des commandes client IBM (version bêta privée)

Cet accélérateur d’intégration pour IBM Sterling Order Management permet aux clients Adobe Commerce de commencer à utiliser des fonctionnalités avancées de gestion des commandes, optimisées par IBM Sterling OMS. Avec cette intégration, les marchands obtiennent :
- Visibilité en temps réel des niveaux d’inventaire et des dates de remise précises pour vos clients.
- L’approvisionnement automatisé pour les commandes basées sur des règles configurables, afin que vous puissiez optimiser votre réseau d’exécution et votre inventaire.
- Une vue universelle des commandes sur tous les canaux à partir d’un seul tableau de bord afin que vos équipes d’assistance puissent fournir un service exceptionnel et identifier et gérer rapidement les exceptions.
- Flux de gestion des retours modèle pour simplifier la gestion des retours.

Pour participer à cette version bêta, envoyez une demande par courrier électronique à [sbieber@adobe.com](mailto:sbieber@adobe.com).

### Connexion aux données et Audience Activation (version bêta publique)

Étendu du partage de données entre Adobe Commerce et Adobe Experience Platform afin de générer des expériences personnalisées plus puissantes. Cette fonctionnalité permet aux marchands de :
- Partage des profils client Commerce
- Création d’attributs personnalisés
- Obtention d’informations sur Commerce dans Real-Time CDP et Adobe Journey Optimizer
- Prise en charge de plusieurs jeux de données et flux de données

Pour participer à cette version bêta, envoyez une demande par courrier électronique à [DataConnection@adobe.com](mailto:DataConnection@adobe.com).

### Kit de démarrage d’intégration backoffice (version bêta privée)

Le back-office [kit de démarrage d’intégration](https://developer-stage.adobe.com/commerce/extensibility/app-development/starter-kit/) fournit aux développeurs un accélérateur pour créer des intégrations basées sur des événements avec des systèmes tels que les ERP, les CRM et les OMS. Avec le kit de démarrage, vous pouvez réduire les coûts de développement jusqu’à 50 %. Le kit de démarrage suit également les bonnes pratiques d’Adobe Commerce qui réduisent considérablement le coût de maintenance. Voici les points forts du kit de démarrage :
- Synchronisation des données pour les objets fréquemment utilisés tels que le produit, la commande, le client, le stock et l’expédition
- Plans directeurs architecturaux suivant les bonnes pratiques
- Intégration de scripts pour accélérer le développement

Pour participer à cette version bêta, exécutez la [formulaire d&#39;inscription](https://forms.office.com/r/YbYArqE3DT).

### Adobe Commerce Foundation (version bêta publique)

Chaque version bêta d’Adobe Commerce Foundation comprend toutes les modifications apportées au code de base d’Adobe Commerce d’ici la date de publication prévue, notamment, mais sans s’y limiter, les domaines fonctionnels suivants :

- Derniers correctifs de sécurité
- Amélioration des performances
- Améliorations apportées à GraphQL
- Correctifs de qualité générale
- Contributions de la communauté
- Modifications requises pour prendre en charge la compatibilité avec [Services Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/home.html)

#### Convention d’affectation de nom et planification

Adobe publie généralement deux fois par an des correctifs bêta.

Les modules de version bêta ont une `-betaX` suffixe. Par exemple, les packages de version bêta d’Adobe Commerce 2.4.7 utilisent la convention d’affectation des noms suivante :

- `2.4.7-beta1`
- `2.4.7-beta2`

Voir [calendrier de publication](schedule.md) pour obtenir la liste des dates de publication de la version bêta publique à venir.


#### Accès aux versions bêta

Les versions bêta d’Adobe Commerce sont distribuées de la même manière que toute autre version de correctif d’Adobe Commerce : sous la forme de métaphores du compositeur sur `https://repo.magento.com`. Le code source est disponible sur [GitHub](https://github.com/magento/magento2).

Voir [Démarrage rapide de l’installation du compositeur](../installation/composer.md) pour plus d’informations.

#### Rapports sur les problèmes

Adobe ne fournit pas le service d’assistance Adobe standard pour les versions bêta.

Pour envoyer des commentaires relatifs aux versions bêta, suivez notre [flux de création de rapports de problèmes standard](https://developer.adobe.com/commerce/contributor/guides/code-contributions/) on [GitHub](https://github.com/magento/magento2).

Nos équipes internes surveilleront tous les problèmes critiques signalés par rapport à la dernière version bêta et prioriseront leur résolution avant la date de publication de la version GA.
