---
title: Architecture de référence d’Enterprise
description: Découvrez comment mettre en oeuvre Adobe Commerce à l’aide de la dernière technologie de commerce composable d’Adobe.
feature: App Builder, Cloud, GraphQL, Integration, Paas, Saas
exl-id: d066ab43-20e2-4e0b-8348-0c52d6a7ac8a
source-git-commit: 8eab688ed98eb1b9fcf4fc25f90fe2bbf99c02d6
workflow-type: tm+mt
source-wordcount: '799'
ht-degree: 0%

---

# Architecture de référence d’entreprise d’Adobe Commerce

Adobe Commerce est une plateforme basée sur l’expérience qui associe de manière unique la flexibilité technique avec une facilité d’utilisation, le tout afin de créer des expériences exceptionnelles qui génèrent des résultats commerciaux.

Le commerce a évolué pour répondre aux besoins de l’entreprise en termes de performances, d’échelle et de sécurité. L’adoption d’une approche moderne de mise en oeuvre qui utilise les dernières solutions commerciales composables d’Adobe est essentielle au succès des entreprises. Cette page décrit l’approche moderne de mise en oeuvre de Commerce en détail technique.

Le diagramme d’architecture suivant illustre le flux de données entre Adobe Commerce et toutes les solutions Adobe Experience Cloud.

![Schéma architectural montrant comment Adobe Commerce se connecte aux solutions Experience Cloud](../../assets/playbooks/commerce-architecture-v2.svg){zoomable=&quot;yes&quot;}

>[!NOTE]
>
>Les flux de données de haut niveau présentés dans le diagramme sont cohérents dans la plupart des mises en oeuvre d’entreprise. Le composant clé qui peut rendre les implémentations uniques est la manière dont vous créez votre catalogue (en particulier pour B2B). Vous devez soigneusement mapper l’architecture de votre catalogue à la variable [API web de commerce](https://developer.adobe.com/commerce/webapi/get-started/).

## Cloud Foundation

[Adobe Commerce sur l’infrastructure cloud](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/overview) est la base de votre implémentation de Commerce. Il fournit une [secure](../../security-and-compliance/shared-responsibility.md) plateforme d’hébergement automatisée avec une approche en libre-service pour créer, déployer, surveiller et gérer votre application Commerce dans un environnement natif au cloud.

Consultez les détails techniques suivants sur la base cloud :

- [**Architecture mise à l’échelle**](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/architecture/scaled-architecture)—Capacité ajustée automatiquement pour maintenir des performances stables et prévisibles
- [**Environnements multiples**](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/architecture/pro-architecture): préconfiguré avec PHP, MySQL (MariaDB), Redis, RabbitMQ et les technologies de moteur de recherche prises en charge pour développer, tester et déployer votre site.
- [**Gestion des configurations**](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/overview)—Fichiers de configuration d’environnement personnalisables et interface de ligne de commande pour gérer les paramètres d’application, les itinéraires, la création et le déploiement d’actions et de notifications.
- [**Workflow basé sur Git**](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/architecture/pro-develop-deploy-workflow): création et déploiement automatiques après publication des modifications de code pour un développement rapide et un déploiement continu.
- [**Observabilité intégrée**](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/monitor/performance): outils qui combinent les données de journal provenant de plusieurs sources pour vous aider à gérer les performances de votre site et à diagnostiquer les problèmes
- [**Couverture complète des API**](https://developer.adobe.com/commerce/webapi/get-started/)—[GraphQL](https://developer.adobe.com/commerce/webapi/graphql/) et [REST](https://developer.adobe.com/commerce/webapi/rest) API pour intégrer l’application Commerce principale à des systèmes tiers et étendre les fonctionnalités de Commerce

## Intégration à Experience Cloud

Adobe Commerce s’intègre à toutes les solutions Experience Cloud pour diffuser des [expériences commerciales personnalisées à grande échelle](https://experienceleague.adobe.com/en/docs/commerce-admin/customers/customers-menu/personalize-scale#customers-menu).

[Connexion aux données](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/data-connection/overview) permet d’obtenir des informations sur le comportement d’achat de vos acheteurs, de sorte que vous puissiez créer des expériences d’achat personnalisées sur tous les canaux avec d’autres produits Adobe Digital Experience.

>[!NOTE]
>
>Voir [Plans directeurs d’expérience numérique](https://experienceleague.adobe.com/en/docs/blueprints-learn/architecture/overview) pour plus de détails techniques.


## Intégration à des systèmes tiers

Adobe fournit aux développeurs des points d’extension et des outils complets pour créer des applications qui étendent les principales fonctionnalités de commerce et qui intègrent Commerce à des systèmes tiers (tels que les CRM, ERPS et PIMS). Ces outils réduisent le coût total de possession de la plate-forme comme suit :

- **Évolutivité**: les applications peuvent être mises à l’échelle séparément des logiciels principaux, ce qui permet une plus grande efficacité et une mise à niveau simplifiée.
- **Isolation**-Un environnement isolé signifie que les développeurs peuvent mettre à niveau ou modifier leurs extensions à leur discrétion sans avoir recours à une version principale.
- **L&#39;indépendance technologique**- Les développeurs peuvent choisir les piles de technologies et les langages de codage qui correspondent à leurs besoins.

Adobe fournit les outils de développement suivants pour créer des intégrations et des personnalisations :

- [**Maillage d’API pour Adobe Developer App Builder**](https://developer.adobe.com/graphql-mesh-gateway/): coordonnez et combinez plusieurs API, GraphQL, REST et autres sources dans un seul point de terminaison GraphQL interrogeable.
- [**App Builder**](https://developer.adobe.com/app-builder/docs/overview/): créez et déployez des applications web sécurisées et évolutives qui étendent les fonctionnalités de Commerce et s’intègrent à des solutions tierces.
- [**Événements**](https://developer.adobe.com/commerce/extensibility/events/): utilisez des déclencheurs d’événement personnalisés pour interagir avec d’autres outils de développement extensibles.
- [**Webhooks**](https://developer.adobe.com/commerce/extensibility/webhooks/): utilisez des webhooks pour déclencher automatiquement des interactions entre Commerce et des systèmes tiers.
- [**SDK de l’interface utilisateur d’administration**](https://developer.adobe.com/commerce/extensibility/admin-ui-sdk/): personnalisez et améliorez l’administrateur Commerce avec de nouvelles pages et fonctionnalités pour vos commerçants.

## Services Storefront

Adobe propose un large éventail de services de marchandisage composables et intelligents pour vous aider à réaliser vos objectifs commerciaux clés. Ces services fournissent également des API essentielles à l’optimisation des performances à grande échelle.

- [Recherche en direct](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/live-search/overview): proposez des résultats plus intelligents, plus rapides et pertinents aux acheteurs grâce à cet outil de recherche optimisé par l’IA.
- [Recommendations de produit](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/product-recommendations/overview): ajoutez des recommandations alimentées par l’IA basées sur le comportement des acheteurs, les tendances populaires, la similarité de produits, etc.
- [Service de catalogue](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/catalog-service/guide-overview): offrez à vos clients une expérience produit optimisée tout en améliorant les performances, l’évolutivité et les conversions.
- [Services de paiement](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/payment-services/guide-overview): attisez la satisfaction des clients en proposant divers modes de paiement, notamment des versements sans intérêts, et une vue unique du traitement des paiements, des commandes et des factures.

## storefront sans tête

Le commerce sans affichage est un commerce avec API-first. Adobe Commerce est entièrement sans interface avec une architecture découplée qui fournit tous les services et données de commerce par le biais d’une couche API GraphQL. Cette architecture permet aux équipes de développer leurs interfaces indépendamment de l’application principale, ce qui offre la possibilité de créer et de tester rapidement de nouveaux points de contact avec les technologies émergentes.

Adobe fournit une technologie moderne sans interface de storefront qui inclut les mêmes avantages et capacités que ceux apportés par [Edge Delivery Services](https://www.aem.live/home) avec la création basée sur des documents, une architecture axée sur les performances et des expérimentations natives prêtes à l’emploi. Elle tire parti de l’échelle et des performances d’Adobe Commerce [services storefront](#storefront-services) et la souplesse et la commodité de [composants de menu déroulant](https://experienceleague.adobe.com/developer/commerce/storefront/) pour offrir des fonctionnalités commerciales.

