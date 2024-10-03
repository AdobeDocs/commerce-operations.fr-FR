---
title: Versions de Beta
description: Découvrez les versions bêta d’Adobe Commerce et comment y participer.
exl-id: 662cb061-995f-4e09-a2ef-9e607cc0000b
source-git-commit: a6c0a7f8c2a2bd6156f19838e05f8046209177e4
workflow-type: tm+mt
source-wordcount: '1102'
ht-degree: 0%

---

# Versions bêta d’Adobe Commerce

Les programmes bêta d’Adobe Commerce sont un moyen pour les marchands d’accéder aux fonctionnalités et au code de version préliminaire, de fournir des commentaires et de guider l’avenir d’Adobe Commerce. Il existe deux types de programmes bêta :

- Beta publique : un programme bêta public est disponible pour tous les clients et partenaires d’Adobe Commerce
- Private Beta : un programme bêta privé peut nécessiter une approbation basée sur des critères admissibles pour participer.

>[!IMPORTANT]
>
>Les versions de Beta peuvent contenir des défauts et sont fournies &quot;EN L’ÉTAT&quot; sans aucune garantie de quelque type que ce soit. Adobe n’aura aucune obligation de gérer, corriger, mettre à jour, modifier, modifier ou d’autre manière prendre en charge (via les services d’assistance d’Adobe ou d’une autre manière) les versions bêta. Il est conseillé aux clients de faire preuve de prudence et de ne pas s’appuyer d’aucune manière sur le bon fonctionnement ou les performances des versions bêta et/ou de la documentation ou des documents associés. Les fonctionnalités et les API en version bêta peuvent être modifiées sans préavis. Par conséquent, toute utilisation des versions bêta est entièrement à la charge du client.

## Avantages de la participation

L’obtention d’un accès anticipé aux fonctionnalités qu’Adobe développe permet aux clients et aux partenaires de fournir des commentaires, de façonner le développement de produits et de se préparer à adopter de nouvelles fonctionnalités avant la disponibilité générale.

## Programmes Beta actuels

Consultez les sections suivantes pour obtenir la liste des programmes bêta actifs.

### Amélioration des fonctionnalités de recherche pour la recherche en direct (Beta public)

Cette version bêta prend en charge trois nouvelles fonctionnalités de la requête [`productSearch`](https://developer.adobe.com/commerce/services/graphql/live-search/product-search/) :

- **Recherche en couches** - Recherche dans un autre contexte de recherche - Grâce à cette fonctionnalité, vous pouvez effectuer jusqu’à deux couches de recherche pour vos requêtes de recherche. Par exemple :

   - **Recherche de calque 1** - Recherchez &quot;engine&quot; sur &quot;product_attribute_1&quot;.
   - **Recherche par couche 2** - Recherchez &quot;numéro de partie 123&quot; sur &quot;product_attribute_2&quot;. Cet exemple recherche &quot;part number 123&quot; dans les résultats pour &quot;engine&quot;.

  La recherche en couches est disponible pour l’indexation de recherche `startsWith` et l’indexation de recherche `contains` comme décrit ci-dessous :

- **startsWith search indexation** - Effectuez une recherche en utilisant l’indexation `startsWith`. Cette nouvelle fonctionnalité permet :

   - La recherche de produits pour lesquels la valeur d’attribut commence par une chaîne spécifique.
   - Configuration d’une recherche &quot;se termine par&quot; afin que les acheteurs puissent rechercher des produits pour lesquels la valeur d’attribut se termine par une chaîne spécifique. Pour activer une recherche &quot;se termine par&quot;, l’attribut de produit doit être ingéré en sens inverse et l’appel API doit également être une chaîne inversée.

- **contient l’indexation de la recherche** - Recherchez un attribut à l’aide de l’indexation contient. Cette nouvelle fonctionnalité permet :

   - Recherche d’une requête dans une chaîne plus grande. Par exemple, si un acheteur recherche le numéro de produit &quot;PE-123&quot; dans la chaîne &quot;HAPE-123&quot;.

      - Remarque : Ce type de recherche est différent de la [recherche d’expression](https://developer.adobe.com/commerce/services/graphql/live-search/product-search/#phrase) existante, qui effectue une recherche de saisie semi-automatique. Par exemple, si la valeur de votre attribut de produit est &quot;pantalon extérieur&quot;, une recherche d’expression renvoie une réponse pour &quot;pantalon d’extraction&quot;, mais ne renvoie pas de réponse pour &quot;fourmis d’extérieur&quot;. Une recherche contient, cependant, renvoie une réponse pour &quot;fourmis pauvres&quot;.

Ces nouvelles conditions améliorent le mécanisme de filtrage des requêtes de recherche pour affiner les résultats de recherche. Ces nouvelles conditions n’affectent pas la requête de recherche principale. Pour participer à la version bêta, envoyez une demande par courrier électronique à [Sandra Gonzales Mangana](mailto:sagonzal@adobe.com) ou [Alex Jose](mailto:alexj@adobe.com).

Pour installer la version bêta de Live Search, consultez le [guide de Live Search](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/live-search/install#install-the-live-search-beta).

### Intégration de Experience Manager Assets pour Commerce (Private Beta)

L’intégration de Experience Manager Assets pour Commerce permet une gestion et une diffusion efficaces d’un grand volume d’images de produits de Experience Manager Assets à Adobe Commerce avec un faible effort opérationnel ou aucun effort nécessaire.

Principales fonctionnalités :

- Intégration de l’installation et de la lecture : proposez un Adobe prêt à l’emploi, l’intégration entre Experience Manager Assets et Adobe Commerce, afin de permettre aux commerçants de se concentrer sur ce qui importe le plus, avec des coûts d’exploitation réduits et une meilleure efficacité.

- Personnalisez des images de produit à l’échelle Utilisez Experience Manager Assets afin de générer des millions de variations de produit pour des expériences Commerce personnalisées avec des outils d’édition faciles basés sur l’interface utilisateur, la création de contenu génératif à l’aide de l’Adobe Firefly et des workflows de ressources attribués pour garantir la cohérence de la marque. Une fois que vous êtes satisfait des ressources, distribuez-les facilement dans vos vitrines Commerce à l’aide de l’intégration Experience Manager Assets.

- Intégration simple : simplifiez l’intégration des commerçants grâce à un processus de synchronisation configurable qui permet une synchronisation complète entre le référentiel Experience Manager Assets et le catalogue Commerce.

- Stratégie de correspondance flexible : l’intégration comprend des algorithmes de correspondance de ressources par défaut basés sur des SKU de produit qui synchronisent les images entre AEM Assets et Commerce. Elle est extensible à l’aide d’Adobe Developer App Builder. Collaborez avec votre partenaire de solution pour créer une stratégie de mise en correspondance des ressources personnalisée en plus de l’intégration afin de prendre en compte n’importe quelle structure de référentiel de gestion des ressources.

Pour participer à la version bêta, envoyez une demande par courrier électronique à [Shaun McCran](mailto:mccran@adobe.com).

### Intégration du système IBM Sterling Order Management (Private Beta)

Cet accélérateur d’intégration pour IBM Sterling Order Management permet aux clients Adobe Commerce de commencer à utiliser des fonctionnalités avancées de gestion des commandes, optimisées par IBM Sterling OMS. Avec cette intégration, les marchands obtiennent :

- Visibilité en temps réel des niveaux d’inventaire et des dates de remise précises pour vos clients.
- L’approvisionnement automatisé pour les commandes basées sur des règles configurables, afin que vous puissiez optimiser votre réseau d’exécution et votre inventaire.
- Une vue universelle des commandes sur tous les canaux à partir d’un seul tableau de bord afin que vos équipes d’assistance puissent fournir un service exceptionnel et identifier et gérer rapidement les exceptions.
- Flux de gestion des retours modèle pour simplifier la gestion des retours.

Pour participer à cette version bêta, envoyez une demande par e-mail à [sbieber@adobe.com](mailto:sbieber@adobe.com).

### Connexion et Audience Activation des données (Beta public)

Étendu du partage de données entre Adobe Commerce et Adobe Experience Platform afin de générer des expériences personnalisées plus puissantes. Cette fonctionnalité permet aux marchands de :

- Partage des profils client Commerce
- Création d’attributs personnalisés

Pour participer à cette version bêta, envoyez une demande par e-mail à [DataConnection@adobe.com](mailto:DataConnection@adobe.com).

### Adobe Commerce Foundation (Beta public)

Chaque version bêta d’Adobe Commerce Foundation comprend toutes les modifications apportées au code de base d’Adobe Commerce d’ici la date de publication prévue, notamment, mais sans s’y limiter, les domaines fonctionnels suivants :

- Derniers correctifs de sécurité
- Amélioration des performances
- Améliorations apportées à GraphQL
- Correctifs de qualité générale
- Contributions de la communauté
- Modifications requises pour prendre en charge la compatibilité avec les [services Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/home.html)

#### Convention d’affectation de nom et planification

Adobe publie généralement deux fois par an des correctifs bêta.

Les modules de version Beta ont un suffixe `-betaX`. Par exemple, les packages de version bêta d’Adobe Commerce 2.4.7 utilisent la convention d’affectation des noms suivante :

- `2.4.7-beta1`
- `2.4.7-beta2`

Consultez le [calendrier de publication](schedule.md) pour obtenir la liste des dates de publication de la version bêta publique à venir.


#### Accès aux versions de Beta

Les versions bêta d’Adobe Commerce sont distribuées de la même manière que toute autre version de correctif d’Adobe Commerce : sous la forme de métaphores du compositeur sur `https://repo.magento.com`. Le code source est disponible sur [GitHub](https://github.com/magento/magento2).

Voir [Démarrage rapide de l’installation du compositeur](../installation/composer.md) pour plus d’informations.

#### Rapports sur les problèmes

Adobe ne fournit pas le service d’assistance Adobe standard pour les versions bêta.

Pour envoyer des commentaires relatifs aux versions bêta, suivez notre [ flux de création de rapports de problèmes standard](https://developer.adobe.com/commerce/contributor/guides/code-contributions/) sur [GitHub](https://github.com/magento/magento2).

Nos équipes internes surveilleront tous les problèmes critiques signalés par rapport à la dernière version bêta et prioriseront leur résolution avant la date de publication de la version GA.
