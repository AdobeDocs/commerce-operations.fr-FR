---
title: Architecture de storefront combinée
description: Découvrez ce que signifie un storefront couplé dans le contexte des architectures commerciales sans Adobe.
source-git-commit: 748c302527617c6a9bf7d6e666c6b3acff89e021
workflow-type: tm+mt
source-wordcount: '315'
ht-degree: 0%

---


# Architecture du storefront Adobe (héritée) couplée

L’option de déploiement par défaut actuelle pour la plupart des clients commerciaux comprend :

- Prise en charge de 100 % des fonctionnalités sur B2B et B2C
- Thème de référence de la fonctionnalité (Luma) qui peut être rapidement déployé/personnalisé
- Expertise en mise en oeuvre des partenaires MSI
- Totalement compatible avec les fonctionnalités commerciales telles que le créateur de pages ou l’évaluation et l’aperçu
- Compatibilité large avec les extensions dans le Commerce Marketplace Adobe

![Diagramme montrant une architecture de storefront Adobe associée](../../../assets/playbooks/coupled-storefront-architecture.svg)

## Inconvénients de la vitrine héritée

- **Non headless** : Toutes les parties de l’application Adobe Commerce monolithique. Aucune séparation de la logique commerciale et des processus entre le serveur frontal et le serveur principal.

- **Non PWA** : bien que le thème soit réactif, les performances du site sont loin derrière celles des PWA les plus performants.

- **Architecture front-end (composants de l’interface utilisateur d’Adobe Commerce)** : les spécialistes de Commerce/PHP d’Adobe doivent s’appuyer sur le storefront hérité.

Avant de passer aux options sans interface, commençons par l’architecture plus familière du storefront. Si l’absence de tête est découplée, il s’agit de l’architecture couplée du storefront, la plus souvent vue avec nos démonstrations Luma.

C’est là que les fonctionnalités de storefront sont étroitement intégrées aux services commerciaux principaux, et non séparées par cette couche d’API GraphQL. Il y a donc beaucoup de logique commerciale associée à ce thème. Cette approche n&#39;est pas sans tête, et elle n&#39;est pas PWA.

Il s’agit actuellement de l’option la plus courante utilisée par les commerçants, car elle prend entièrement en charge les fonctionnalités avec les fonctionnalités de commerce B2B et B2C. La communauté est familière, il y a un écosystème mature d&#39;expertise autour de lui, et il est largement compatible avec les extensions de Commerce Marketplace des Adobes.

Cependant, il n&#39;a pas les avantages dont nous avons parlé plus tôt. Sans séparation des couches, il existe de nombreuses dépendances et de nombreux points d’échec potentiels lorsque des modifications sont effectuées. Ce n’est pas aussi performant qu’un PWA bien mis en oeuvre et si un commerçant n’a pas d’expertise en commerce d’Adobe ou en développement PHP, il devra trouver ces ressources.
