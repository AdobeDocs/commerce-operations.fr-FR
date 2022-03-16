---
title: Architecture de storefront combinée
description: Découvrez ce que signifie un storefront couplé dans le contexte des architectures Adobe Commerce sans interface.
exl-id: 978e6853-4fbe-45b8-8e46-f491c6724fc6
source-git-commit: e76f101df47116f7b246f21f0fe0fa72769d2776
workflow-type: tm+mt
source-wordcount: '315'
ht-degree: 0%

---

# Architecture du storefront Adobe Commerce couplée (héritée)

L’option de déploiement par défaut actuelle pour la plupart des clients commerciaux comprend :

- Prise en charge de 100 % des fonctionnalités sur B2B et B2C
- Thème de référence de la fonctionnalité (Luma) qui peut être rapidement déployé/personnalisé
- Expertise en mise en oeuvre des partenaires MSI
- Totalement compatible avec les fonctionnalités commerciales telles que le créateur de pages ou l’évaluation et l’aperçu
- Compatibilité large avec les extensions dans Adobe Commerce Marketplace

![Diagramme présentant une architecture de storefront Adobe Commerce couplée](../../../assets/playbooks/coupled-storefront-architecture.svg)

## Inconvénients de la vitrine héritée

- **Pas de tête**: toute partie de l’application Adobe Commerce monolithique. Aucune séparation de la logique commerciale et des processus entre le serveur frontal et le serveur principal.

- **Non PWA**— Bien que le thème soit réactif, les performances du site sont loin derrière les meilleurs PWA de la classe.

- **Architecture front-end (composants de l’interface utilisateur d’Adobe Commerce)**: spécialistes d’Adobe Commerce/PHP pour construire à partir de storefront hérité.

Avant de passer aux options sans interface, commençons par l’architecture plus familière du storefront. Si l’absence de tête est découplée, il s’agit de l’architecture couplée du storefront, la plus souvent vue avec nos démonstrations Luma.

C’est là que les fonctionnalités de storefront sont étroitement intégrées aux services commerciaux principaux, et non séparées par cette couche d’API GraphQL. Il y a donc beaucoup de logique commerciale associée à ce thème. Cette approche n&#39;est pas sans tête, et elle n&#39;est pas PWA.

Il s’agit actuellement de l’option la plus courante utilisée par les commerçants, car elle prend entièrement en charge les fonctionnalités avec les fonctionnalités de commerce B2B et B2C. La communauté y est familière, il existe un écosystème d’expertise mature et il est largement compatible avec les extensions Adobe Commerce Marketplace.

Cependant, il n&#39;a pas les avantages dont nous avons parlé plus tôt. Sans séparation des couches, il existe de nombreuses dépendances et de nombreux points d’échec potentiels lorsque des modifications sont effectuées. Il n’est pas aussi performant qu’un PWA bien mis en oeuvre et si un commerçant n’a pas d’expertise dans le développement Adobe Commerce ou PHP, il devra trouver ces ressources.
