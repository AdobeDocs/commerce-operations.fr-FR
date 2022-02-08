---
title: Architecture Adobe Commerce sans tête
description: Learn about what makes Adobe Commerce's headless architecture approach unique.
exl-id: eac9d5b1-4917-4d2a-a8af-7f85c825fa0d
source-git-commit: 6509c939c7abc5462bffbe104466b2ff9e6fadc9
workflow-type: tm+mt
source-wordcount: '762'
ht-degree: 0%

---

# Architecture Adobe Commerce sans tête

L’avantage de l’architecture d’Adobe Commerce est qu’elle n’est pas une proposition de tout ou rien et qu’un marchand peut trouver le bon mélange de solutions pour son activité. Ils peuvent créer un PWA optimisé par les PWA Studio pour leur Principale expérience sur site ou utiliser Adobe Experience Manager comme calque dans les parcours clients complexes, tout en créant un front de face personnalisé pour tester de nouveaux points de contact. Aucune autre plateforme ne peut égaler le temps nécessaire aux avantages du marché et la flexibilité qu’offre Adobe Commerce avec son architecture sans interface.

![Diagram showing a headless Adobe Commerce storefront architecture](../../../assets/playbooks/headless-storefront-architecture.svg)

Chaque approche n&#39;est pas mutuellement exclusive. Les clients peuvent créer leur propre front-end (head), utiliser PWA Studio pour les expériences web/mobiles et/ou utiliser Adobe Experience Manager pour la vitrine (dans un déploiement complet ou hybride).

Adobe Commerce a toujours autorisé les déploiements sans interface avec les API REST. Bien que REST soit puissant, en particulier pour le traitement en masse, lorsqu’il s’agit d’un traitement headless, les API GraphQL permettent un développement plus rapide grâce à une expérience de développement intuitive, une plus grande flexibilité en autorisant des modifications qui n’affectent pas les API existantes et de meilleures performances en réduisant la quantité de données récupérées à ce qui est exactement nécessaire.

GraphQL est une norme du secteur pour les API performantes, qui est utilisée par de nombreuses plateformes de commerce électronique principales. C&#39;est une bonne chose car cela signifie que c&#39;est une solution éprouvée et que l&#39;expertise existe sur le marché.

Bien qu’Adobe Commerce dispose d’une vitrine couplée comme option, il n’est absolument pas nécessaire qu’un commerçant utilise cette interface héritée d’Adobe Commerce. Un commerçant peut tirer parti des services commerciaux haut de gamme d’Adobe Commerce pour gérer les processus d’entreprise principaux et, en utilisant nos API storefront, intégrer son propre storefront découplé pour diriger l’expérience front-end.

Maintenant, regardons les différentes options sans tête.

## PWA Studio

Le premier est une application web progressive créée avec PWA Studio. Une partie de cela est rendue possible par le fait qu’un PWA est une vitrine sans interface découplée du serveur principal du commerce. Grâce à PWA Studio, les marchands peuvent créer des PWA hautement performants, fiables et économiques en plus d’Adobe Commerce pour offrir des expériences web haut de gamme, à la fois sur mobile et sur ordinateur de bureau. Au fil du temps, cette option remplacera le storefront couplé comme option par défaut.

La plupart des commerçants comprennent la direction que prend l&#39;industrie en ce qui concerne les PWA et de nombreux bloqueurs potentiels sont rapidement éliminés.

D’une semaine à l’autre, le nombre de partenaires développant l’expertise en PWA Studio augmente et le nombre de lancements client s’accélère. La mise à jour la plus récente de PWA Studio inclut une extensibilité qui permettra d’accomplir des progrès significatifs en matière de compatibilité avec les extensions Adobe Commerce Marketplace.

De nombreux commerçants peuvent penser qu&#39;ils ne sont pas prêts pour les PWA et les sans-tête parce qu&#39;ils nécessitent une forte dépendance envers les développeurs. L’un des énormes avantages du développement de l’application commerciale et de la tête par Adobe Commerce est qu’elle permet d’assurer la compatibilité entre les fonctionnalités commerciales.

Afin de rendre les PWA plus accessibles et plus faciles à gérer pour nos commerçants, nous permettons aux utilisateurs professionnels de gérer les modifications de contenu quotidiennes, de créer de nouvelles pages d’entrée, et plus encore d’utiliser le générateur de pages. Ces deux puissantes fonctionnalités permettent de commercialiser rapidement tous les appareils et expériences.

## Adobe Experience Manager

A powerhouse combination for your content and digital asset management needs, Adobe Experience Manager helps merchants get personalized, content-led experiences into market faster, combining digital asset management with the power of machine learning, Adobe Sensei-powered content, and customer journey management.

Adobe Commerce plus Adobe Experience Manager is a powerful story in that the commerce engine allows businesses to enable commerce though customer interfaces that are powered by Adobe Experience Manager.

## Têtes personnalisées

La dernière option à discuter ici est l&#39;option de construire une façade personnalisée. Cette option est destinée aux entreprises qui disposent d’une expertise existante et aux développeurs internes qualifiés dans une pile frontale particulière, comme React. If they don’t have skills in Adobe Commerce’s traditional frontend development, they can decide that it&#39;s more cost effective to build their own custom React frontend.

Naturellement, ce modèle nécessite des compétences et des ressources de développement front-end d’intégration des clients ou des systèmes solides, et vous ne bénéficiez pas de la compatibilité native avec des éléments comme le Créateur de pages que vous obtenez avec PWA Studio. Chaque fois qu&#39;un commerçant construit quelque chose de complètement personnalisé, il peut perdre des avantages de temps à la mise sur le marché.

Les interfaces personnalisées permettent également d’innover et d’expérimenter. There’s a lot of talk about AR/VR or voice commerce, and an architecture like Adobe Commerce’s allows merchants to explore these options without impacting their existing webstores.
