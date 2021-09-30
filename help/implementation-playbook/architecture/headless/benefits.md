---
title: Headless Commerce
description: Découvrez ce que le commerce sans interface et comment Adobe Commerce prend en charge les architectures sans interface.
source-git-commit: 748c302527617c6a9bf7d6e666c6b3acff89e021
workflow-type: tm+mt
source-wordcount: '303'
ht-degree: 0%

---


# Commerce sans tête

## Pourquoi ne pas avoir la tête ?

Tout d&#39;abord, le commerce d&#39;entreprise hérité est coûteux et difficile à développer en raison de ses loyers ; les structures héritées sont renforcées par les limitations des plateformes ; et l&#39;innovation devient difficile.

Les clients s’attendent à ce qu’une entreprise interagisse avec eux et interagisse avec eux sur tous les canaux. Les entreprises axées sur la clientèle cherchent à créer des plateformes à l’épreuve du temps qui peuvent s’adapter aux attentes changeantes des clients.

Le commerce sans affichage est un commerce basé sur les API. Il découple la logique commerciale, ainsi que les aspects transactionnels et de données du commerce, de la présentation. Headless est une structure intégrée qui offre une flexibilité totale pour tous les canaux et points de contact, avec une couche d’expérience frontale séparée de la plateforme elle-même. Cela permet aux marques de diffuser du contenu tel que des produits, des données et des commandes sur n’importe quel point de contact, maintenant et à l’avenir, tout en étant en mesure de l’afficher comme bon leur semble.

L’architecture sans affichage est la séparation technique de l’en-tête du reste de l’application commerciale. Adobe Commerce est totalement sans interface avec une architecture découplée qui fournit tous les services et données de commerce par le biais d’une couche API GraphQL. Cette architecture permet aux équipes front-end de développer leurs interfaces indépendamment d’Adobe Commerce, ce qui offre la possibilité de créer et de tester rapidement de nouveaux points de contact avec les technologies émergentes.

Les API GraphQL d’Adobe Commerce peuvent également être étendues avec des microservices déployés sur l’exécution I/O d’Adobe. Cela offre une agilité inégalée pour intégrer, étendre et personnaliser les processus métier omnicanaux sans nécessiter de personnalisations de code au serveur principal, ce qui garantit que la plateforme principale peut être facilement mise à niveau sans impact sur les points de contact frontend. Adobe Commerce GraphQL APIs are open sourced and part of our community engineering program with significant contributions and oversight coming from our community of developers.

![Diagramme d’architecture de commerce sans affichage](../../../assets/playbooks/headless-diagram.svg)

![Avantages du diagramme d’architecture de commerce sans interface](../../../assets/playbooks/headless-benefits.svg)
