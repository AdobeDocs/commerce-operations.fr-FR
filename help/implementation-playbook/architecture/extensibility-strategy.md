---
title: Stratégie d’extensibilité Adobe Commerce
description: Découvrez comment le modèle d’extensibilité d’Adobe Commerce vous permet de personnaliser votre mise en oeuvre.
exl-id: fac4630d-8a41-40dc-899a-01eabceaa61e
feature: Extensibility
source-git-commit: 4873a51fbf67d305fdd1898f3740c73ac5ccbad8
workflow-type: tm+mt
source-wordcount: '339'
ht-degree: 0%

---

# Stratégie d&#39;extensibilité

La plate-forme d’extensibilité d’Adobe Commerce permet aux marques de personnaliser efficacement les processus, d’intégrer les systèmes et de déployer de nouvelles fonctionnalités tout en maintenant la mise à niveau.

## Présentation des stratégies d’extension Commerce

L’extension des fonctionnalités de la plateforme Commerce comprend les approches de haut niveau suivantes :

* Extension des fonctionnalités natives de la plateforme Commerce. Par exemple, les marchands peuvent installer des applications Marketplace (souvent créées par des tiers) qui étendent et affinent les fonctionnalités natives de la plateforme, par exemple une extension qui peut valider les adresses de livraison lors du passage en caisse et faciliter une intégration rapide avec les API des adresses de l’opérateur UPS.

* Intégration d’applications/d’extensions tierces à la plateforme Commerce. Les développeurs peuvent utiliser les API REST et GraphQL existantes et complètes de Commerce pour intégrer directement Commerce à des solutions tierces.

Cependant, l’architecture de la plateforme détermine les meilleures stratégies d’extension d’une plateforme. Commerce fournit une couverture d’API REST et GQL riche pour un déploiement sans interface. La base de code Commerce de base continue d’évoluer vers une architecture plus modulaire et une couche d’intégration unique, qui fournit de nouveaux outils de personnalisation améliorés :

* [App Builder pour Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/adobe-developer-app-builder/introduction-to-app-builder.html) est un cadre de développement et un ensemble d’outils qui repose sur l’infrastructure d’Adobe. Les développeurs peuvent l’utiliser pour créer des extensions Commerce qui vont de la personnalisation de l’expérience utilisateur/du storefront à des extensions de middleware et de logique commerciale.

* [Maillage d’API pour Adobe Developer App Builder](https://developer.adobe.com/graphql-mesh-gateway/) permet aux développeurs de combiner plusieurs sources de données en un seul point d’entrée API. Cela prend en charge l’orchestration des API, ou l’intégration, d’API privées et tierces, ainsi que d’autres interfaces logicielles avec les API Adobe Commerce et d’autres produits Adobe à l’aide d’Adobe I/O.

* [Événements d’Adobe I/O pour Adobe Commerce](https://developer.adobe.com/commerce/events/get-started/) rend les données transactionnelles disponibles pour les applications qui sont développées avec App Builder et des hooks web tiers, ce qui permet la création d’applications pilotées par un événement.

Ces outils permettent d’accéder à la console Adobe Developer et aux outils de développement d’Adobe pour créer des API et intégrer des modules externes et des intégrations personnalisés.

Le diagramme suivant met en évidence les principaux composants de la stratégie d’extensibilité de Commerce.

![Diagramme de stratégie d’extensibilité d’Adobe Commerce](../../assets/playbooks/extensibility-strategy-overview.png)
