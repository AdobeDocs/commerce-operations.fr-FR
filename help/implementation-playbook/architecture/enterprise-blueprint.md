---
title: Architecture de référence d’entreprise
description: Découvrez comment mettre en œuvre Adobe Commerce à l’aide de la dernière technologie de commerce composable d’Adobe.
feature: App Builder, Cloud, GraphQL, Integration, Paas, Saas
exl-id: d066ab43-20e2-4e0b-8348-0c52d6a7ac8a
source-git-commit: 16feb8ec7ecc88a6ef03a769d45b1a3a2fe88d97
workflow-type: tm+mt
source-wordcount: '836'
ht-degree: 0%

---

# Architecture de référence d’entreprise Adobe Commerce

Adobe Commerce est une plateforme basée sur l’expérience qui associe de manière unique la flexibilité technique à la facilité d’utilisation, le tout dans le but de créer des expériences exceptionnelles qui génèrent des résultats commerciaux.

Commerce a évolué pour répondre aux exigences des entreprises en matière de performances, d’évolutivité et de sécurité. L’adoption d’une approche de mise en œuvre moderne qui utilise les dernières solutions de commerce composables d’Adobe est essentielle au succès des entreprises. Cette page décrit en détail l’approche moderne de mise en œuvre de Commerce.

Le diagramme d’architecture suivant illustre le flux de données entre Adobe Commerce et toutes les solutions Adobe Experience Cloud.

![Diagramme architectural montrant comment Adobe Commerce se connecte aux solutions Experience Cloud](../../assets/playbooks/commerce-architecture-v3.svg){zoomable="yes"}

>[!NOTE]
>
>Les flux de données de haut niveau présentés dans le diagramme sont cohérents entre la plupart des implémentations d’entreprise. Le composant clé qui peut rendre les implémentations uniques est la manière dont vous créez votre catalogue (en particulier pour B2B). Mappez soigneusement l’architecture de votre catalogue aux [API web de Commerce](https://developer.adobe.com/commerce/webapi/get-started/).

## Cloud Foundation

[Adobe Commerce sur les infrastructures cloud](https://experienceleague.adobe.com/fr/docs/commerce-cloud-service/user-guide/overview) est la base de votre implémentation Commerce. Il fournit une plateforme d’hébergement automatisée [sécurisée](../../security-and-compliance/shared-responsibility.md) avec une approche en libre-service pour créer, déployer, surveiller et gérer votre application Commerce dans un environnement conçu pour le cloud.

Consultez les détails techniques de Cloud Foundation suivants :

- [**Architecture évolutive**](https://experienceleague.adobe.com/fr/docs/commerce-cloud-service/user-guide/architecture/scaled-architecture) : capacité ajustée automatiquement pour maintenir des performances stables et prévisibles
- [**Plusieurs environnements**](https://experienceleague.adobe.com/fr/docs/commerce-cloud-service/user-guide/architecture/pro-architecture) : préconfigurés avec PHP, MySQL (MariaDB), Redis, RabbitMQ et les technologies de moteurs de recherche prises en charge pour développer, tester et déployer votre site
- [**Gestion de la configuration**](https://experienceleague.adobe.com/fr/docs/commerce-cloud-service/user-guide/configure/overview) : fichiers de configuration d’environnement personnalisables et interface de ligne de commande (CLI) pour gérer les paramètres, les itinéraires, les actions de génération et de déploiement et les notifications de l’application.
- [**Workflow basé sur Git**](https://experienceleague.adobe.com/fr/docs/commerce-cloud-service/user-guide/architecture/pro-develop-deploy-workflow) : créez et déployez automatiquement après avoir envoyé les modifications de code pour un développement rapide et un déploiement continu
- [**Observabilité intégrée**](https://experienceleague.adobe.com/fr/docs/commerce-cloud-service/user-guide/monitor/performance) : outils qui combinent des données de journal provenant de plusieurs sources pour vous aider à gérer les performances de votre site et à diagnostiquer les problèmes
- [**Couverture d’API complète**](https://developer.adobe.com/commerce/webapi/get-started/)—[API GraphQL](https://developer.adobe.com/commerce/webapi/graphql/) et [REST](https://developer.adobe.com/commerce/webapi/rest) pour intégrer l’application Commerce principale à des systèmes tiers et étendre les fonctionnalités de Commerce

## Intégration avec Experience Cloud

Adobe Commerce s’intègre à toutes les solutions Experience Cloud pour offrir des [expériences commerciales personnalisées à grande échelle](https://experienceleague.adobe.com/fr/docs/commerce-admin/customers/customers-menu/personalize-scale#customers-menu).

[Connexion de données](https://experienceleague.adobe.com/fr/docs/commerce/data-connection/overview) débloque des informations sur le comportement d’achat de vos clients afin que vous puissiez créer des expériences d’achat personnalisées sur tous les canaux avec d’autres produits d’expérience digitale Adobe.

>[!NOTE]
>
>Consultez les ressources suivantes pour plus d’informations :
>
>- [Plans directeurs d’expérience digitale](https://experienceleague.adobe.com/fr/docs/blueprints-learn/architecture/overview) pour plus de détails techniques.
>- Voir [&#x200B; Personnaliser l’expérience client &#x200B;](https://experienceleague.adobe.com/fr/docs/events/the-skill-exchange-recordings/commerce/aug2024/personalization).


## Intégration à des systèmes tiers

Adobe fournit aux développeurs des points d’extension et des outils complets pour créer des applications qui étendent les fonctionnalités de base de Commerce et intègrent Commerce à des systèmes tiers (tels que CRM, ERPS et PIMS). Ces outils permettent de réduire le coût total de possession de la plateforme comme suit :

- **Évolutivité** : les applications peuvent être mises à l&#39;échelle séparément du logiciel principal, ce qui permet d&#39;accroître l&#39;efficacité et de simplifier les mises à niveau.
- **Isolation**-Un environnement isolé signifie que les développeurs peuvent mettre à niveau ou modifier leurs extensions à leur guise sans avoir recours à une version principale.
- **Indépendance technologique**-Les développeurs peuvent choisir la pile technologique et le langage de codage qui correspondent à leurs besoins.

Adobe fournit les outils de développement suivants pour créer des intégrations et des personnalisations :

- [**Maillage API pour Adobe Developer App Builder**](https://developer.adobe.com/graphql-mesh-gateway/) : coordonnez et combinez plusieurs API, GraphQL, REST et d’autres sources en un seul point d’entrée GraphQL interrogeable.
- [**App Builder**](https://developer.adobe.com/app-builder/docs/overview/) : créez et déployez des applications web sécurisées et évolutives qui étendent les fonctionnalités de Commerce et s’intègrent à des solutions tierces.
- [**Événements**](https://developer.adobe.com/commerce/extensibility/events/) : utilisez des déclencheurs d&#39;événement personnalisés pour interagir avec d&#39;autres outils de développement extensibles.
- [**Webhooks**](https://developer.adobe.com/commerce/extensibility/webhooks/) : utilisez les webhooks pour déclencher automatiquement les interactions entre Commerce et les systèmes tiers.
- [**Admin UI SDK**](https://developer.adobe.com/commerce/extensibility/admin-ui-sdk/) : personnalisez et améliorez l’administration Commerce avec de nouvelles pages et fonctionnalités pour vos commerçants.
- [**Kit de démarrage d’intégration**](https://developer.adobe.com/commerce/extensibility/starter-kit/) : accélérez vos intégrations back-office avec des intégrations de référence, des scripts d’intégration et une architecture normalisée.

>[!NOTE]
>
>Voir [L’approche moderne : une extensibilité efficace dans Adobe Commerce](https://experienceleague.adobe.com/fr/docs/events/the-skill-exchange-recordings/commerce/aug2024/extensibility).

## Services Storefront

Adobe fournit un ensemble riche de services de marchandisage intelligents et composables pour vous aider à atteindre vos principaux objectifs commerciaux. Ces services fournissent également des API qui sont essentielles pour optimiser les performances à grande échelle.

- [Recherche en direct](https://experienceleague.adobe.com/fr/docs/commerce/live-search/overview) : obtenez des résultats plus intelligents, plus rapides et pertinents pour les acheteurs grâce à cet outil de recherche optimisé par l’IA.
- [Recommandations de produits](https://experienceleague.adobe.com/fr/docs/commerce/product-recommendations/overview) : ajoutez des recommandations optimisées par l’IA en fonction du comportement des acheteurs, des tendances populaires, de la similarité des produits, etc.
- [Service de catalogue](https://experienceleague.adobe.com/fr/docs/commerce/catalog-service/guide-overview) : offrez à vos clients une expérience de produit optimisée tout en améliorant les performances, l’évolutivité et les conversions.
- [Services de paiement](https://experienceleague.adobe.com/fr/docs/commerce/payment-services/guide-overview)—Augmentez la satisfaction des clients en offrant diverses méthodes de paiement, y compris des acomptes provisionnels sans intérêt, et une vue unique du traitement des paiements, des commandes et des factures.

## Storefront découplé

Le commerce découplé est un commerce API-first. Adobe Commerce est entièrement découplé avec une architecture découplée qui fournit tous les services et données commerciaux via une couche d’API GraphQL. Cette architecture permet aux équipes de développer leurs interfaces indépendamment de l’application principale, ce qui leur offre l’agilité nécessaire pour créer et tester rapidement de nouveaux points de contact avec les technologies émergentes.

Adobe fournit une technologie storefront découplée moderne qui inclut les mêmes avantages et fonctionnalités que ceux fournis par [Edge Delivery Services](https://www.aem.live/home) avec la création basée sur des documents, une architecture performante et des expériences natives prêtes à l’emploi. Il tire parti de l’échelle et des performances des [services de storefront](#storefront-services) d’Adobe Commerce, ainsi que de la flexibilité et de la commodité des [composants de dépôt](https://experienceleague.adobe.com/developer/commerce/storefront/?lang=fr) pour offrir des fonctionnalités commerciales.

