---
title: Commerce sans tête
description: Découvrez ce que le commerce sans interface signifie et comment Adobe Commerce prend en charge les architectures sans interface.
exl-id: acf66714-c10e-4c8b-b7ca-04cb2ca2fcf9
feature: Integration
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '303'
ht-degree: 0%

---

# Commerce sans tête

## Pourquoi ne pas avoir la tête ?

Tout d&#39;abord, le commerce d&#39;entreprise hérité est coûteux et difficile à développer en raison des silotis ; les structures héritées sont renforcées par des limitations de plates-formes ; et l&#39;innovation devient un défi.

Les clients s’attendent à ce qu’une entreprise interagisse avec eux et interagisse avec eux sur tous les canaux. Les entreprises axées sur la clientèle cherchent à créer des plateformes à l’épreuve du temps qui peuvent s’adapter aux attentes changeantes des clients.

Le commerce sans affichage est un commerce basé sur les API. Il découple la logique commerciale, ainsi que les aspects transactionnels et de données du commerce, de la présentation. Headless est une structure intégrée qui offre une flexibilité totale pour tous les canaux et points de contact, avec une couche d’expérience frontale séparée de la plateforme elle-même. Cela permet aux marques de diffuser du contenu tel que des produits, des données et des commandes sur n’importe quel point de contact, maintenant et à l’avenir, tout en étant en mesure de l’afficher comme bon leur semble.

L’architecture sans affichage est la séparation technique de l’en-tête du reste de l’application commerciale. Adobe Commerce est entièrement sans interface avec une architecture découplée qui fournit tous les services et données de commerce par le biais d’une couche API GraphQL. Cette architecture permet aux équipes front-end de développer leurs interfaces indépendamment d’Adobe Commerce, ce qui offre la possibilité de créer et de tester rapidement de nouveaux points de contact à l’aide des technologies émergentes.

Les API GraphQL d’Adobe Commerce peuvent également être étendues avec des microservices déployés sur l’exécution I/O d’Adobe. Cela offre une agilité inégalée pour intégrer, étendre et personnaliser les processus métier omnicanaux sans nécessiter de personnalisations de code au serveur principal, ce qui garantit que la plateforme principale peut être facilement mise à niveau sans impact sur les points de contact frontend. Les API GraphQL d’Adobe Commerce sont Open Source et font partie de notre programme d’ingénierie de communauté, avec des contributions et une supervision importantes de la part de notre communauté de développeurs.

![Diagramme d’architecture de commerce sans affichage](../../../assets/playbooks/headless-diagram.svg)

![Avantages du diagramme d’architecture de commerce sans interface](../../../assets/playbooks/headless-benefits.svg)
