---
title: Architecture Adobe Commerce sans tête
description: Découvrez ce qui rend l’approche d’architecture sans interface d’Adobe Commerce unique.
exl-id: eac9d5b1-4917-4d2a-a8af-7f85c825fa0d
feature: Integration
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '762'
ht-degree: 0%

---

# Architecture Adobe Commerce sans tête

L&#39;avantage de l&#39;architecture d&#39;Adobe Commerce est qu&#39;elle n&#39;est pas une proposition de tout ou rien et qu&#39;un marchand peut trouver le bon mélange de solutions pour son activité. Ils peuvent créer un PWA optimisé par les PWA Studio pour leur Principale expérience sur site ou utiliser Adobe Experience Manager comme calque dans les parcours clients complexes, tout en créant un front de face personnalisé pour tester de nouveaux points de contact. Aucune autre plateforme ne peut égaler le temps nécessaire aux avantages du marché et la flexibilité qu’offre Adobe Commerce avec son architecture sans interface.

![Diagramme présentant une architecture sans interface Adobe Commerce storefront](../../../assets/playbooks/headless-storefront-architecture.svg)

Chaque approche n&#39;est pas mutuellement exclusive. Les clients peuvent créer leur propre front-end (head), utiliser PWA Studio pour les expériences web/mobiles et/ou utiliser Adobe Experience Manager pour la vitrine (dans un déploiement complet ou hybride).

Adobe Commerce a toujours autorisé les déploiements sans interface avec les API REST. Bien que REST soit puissant, en particulier pour le traitement en masse, lorsqu’il s’agit d’un traitement headless, les API GraphQL permettent un développement plus rapide grâce à une expérience de développement intuitive, une plus grande flexibilité en autorisant des modifications qui n’ont pas d’impact sur les API existantes et de meilleures performances en réduisant la quantité de données récupérées uniquement à ce qui est exactement nécessaire.

GraphQL est une norme du secteur pour les API performantes, qui est utilisée par de nombreuses plateformes de commerce électronique principales. C&#39;est une bonne chose car cela signifie que c&#39;est une solution éprouvée et que l&#39;expertise existe sur le marché.

Bien qu’Adobe Commerce dispose d’une vitrine couplée comme option, il n’est absolument pas nécessaire qu’un commerçant utilise cette interface héritée d’Adobe Commerce. Un commerçant peut tirer parti d’Adobe Commerce pour  des services commerciaux de qualité pour gérer les processus d’entreprise principaux et, en utilisant nos API storefront, intégrer son propre storefront découplé pour diriger l’expérience front-end.

Maintenant, regardons les différentes options sans tête.

## PWA Studio

Le premier est une application web progressive créée avec PWA Studio. Une partie de cela est rendue possible par le fait qu’un PWA est une vitrine sans interface découplée du serveur principal du commerce. Grâce à PWA Studio, les marchands peuvent créer des PWA hautement performants, fiables et économiques en plus d’Adobe Commerce pour offrir des expériences web haut de gamme, à la fois sur mobile et sur ordinateur de bureau. Au fil du temps, cette option remplacera le storefront couplé comme option par défaut.

La plupart des commerçants comprennent la direction que prend l&#39;industrie en ce qui concerne les PWA et de nombreux bloqueurs potentiels sont rapidement éliminés.

D’une semaine à l’autre, le nombre de partenaires développant l’expertise en PWA Studio augmente et le nombre de lancements client s’accélère. La mise à jour la plus récente de PWA Studio inclut une extensibilité qui permettra d’accomplir des progrès significatifs en matière de compatibilité avec les extensions Adobe Commerce Marketplace.

De nombreux commerçants peuvent penser qu&#39;ils ne sont pas prêts pour les PWA et les sans-tête parce qu&#39;ils nécessitent une forte dépendance envers les développeurs. L’un des énormes avantages du développement de l’application commerciale et de la tête par Adobe Commerce est qu’elle permet d’assurer la compatibilité entre les fonctionnalités commerciales.

Afin de rendre les PWA plus accessibles et plus faciles à gérer pour nos commerçants, nous permettons aux utilisateurs professionnels de gérer les modifications de contenu quotidiennes, de créer de nouvelles pages d’entrée, et plus encore d’utiliser le générateur de pages. Ces deux puissantes fonctionnalités permettent de commercialiser rapidement tous les appareils et expériences.

## Adobe Experience Manager

Combinaison puissante pour vos besoins en matière de contenu et de gestion des ressources numériques, Adobe Experience Manager permet aux vendeurs d’obtenir plus rapidement sur le marché des expériences personnalisées basées sur le contenu, en combinant la gestion des ressources numériques à la puissance de l’apprentissage automatique, du contenu optimisé par Adobe Sensei et de la gestion des parcours client.

Adobe Commerce plus Adobe Experience Manager est une puissante histoire dans la mesure où le moteur de commerce permet aux entreprises d’activer le commerce par le biais d’interfaces clients optimisées par Adobe Experience Manager.

## Têtes personnalisées

La dernière option à discuter ici est l&#39;option de construire une façade personnalisée. Cette option est destinée aux entreprises qui disposent d’une expertise existante et aux développeurs internes qualifiés dans une pile frontale particulière, comme React. S&#39;ils n&#39;ont pas de compétences dans Adobe Commerce pour  le développement front-end traditionnel, ils peuvent décider qu&#39;il est plus rentable de construire leur propre front-end React personnalisé.

Naturellement, ce modèle nécessite des compétences et des ressources de développement front-end d’intégration des clients ou des systèmes solides, et vous ne bénéficiez pas de la compatibilité native avec des éléments comme le Créateur de pages que vous obtenez avec PWA Studio. Chaque fois qu&#39;un commerçant construit quelque chose de complètement personnalisé, il peut perdre des avantages de temps à la mise sur le marché.

Les interfaces personnalisées permettent également d’innover et d’expérimenter. Il y a beaucoup de discussions à propos de l&#39;AR/VR ou du commerce vocal, et une architecture comme Adobe Commerce permet aux marchands d&#39;explorer ces options sans affecter leurs webstores existants.
