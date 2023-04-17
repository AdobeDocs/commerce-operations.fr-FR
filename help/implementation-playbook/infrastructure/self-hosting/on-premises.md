---
title: Infrastructure sur site
description: Découvrez l’infrastructure sur site d’Adobe Commerce et les services cloud tiers.
last-substantial-update: 2023-04-13T00:00:00Z
exl-id: de1467be-acec-4a0d-8229-e7e87614bc55
source-git-commit: a253da8cfe95083d1df76d3253aaa424b78a4865
workflow-type: tm+mt
source-wordcount: '631'
ht-degree: 0%

---

# infrastructure sur site d’Adobe Commerce

Les motivations pour lancer une nouvelle mise en oeuvre d’Adobe Commerce ou déplacer une mise en oeuvre d’Adobe Commerce sur site existante vers le cloud sont nombreuses, mais les facteurs stratégiques les plus courants sont la réduction des dépenses en capital, la réduction des coûts permanents, l’amélioration de l’évolutivité et de l’élasticité, l’amélioration du délai de mise sur le marché et l’amélioration de la sécurité et de la conformité.

Le diagramme suivant illustre l’architecture de référence pour le déploiement d’Adobe Commerce sur site sur l’infrastructure AWS. D’autres fournisseurs de cloud comme Azure, Google Cloud et Alibaba Cloud partagent une conception d’infrastructure similaire et des services homologues.

![Diagramme présentant l’infrastructure Adobe Commerce auto-hébergée sur des services cloud tiers](/help/assets/playbooks/on-premises-infrastructure.svg)

Examinons de plus près les rôles et les fonctions de chaque aspect de l&#39;infrastructure illustrée ci-dessus :

1. Amazon Route 53 fournit une configuration DNS.

1. AWS WAF est un pare-feu d’application web qui protège Adobe Commerce contre les attaques Web courantes.

1. Amazon CloudFront est un réseau de diffusion de contenu rapide qui accélère la distribution de contenu web statique et dynamique.

1. Le premier équilibreur de charge de l’application d’équilibrage de charge Elastic Load répartit le trafic entre les instances Varnish dans un groupe d’évolutivité automatique AWS dans plusieurs zones de disponibilité.

1. Varnish Cache est un accélérateur d’applications web qui met en cache un proxy inverse HTTP. La version d’entreprise, disponible sur AWS Marketplace, est recommandée, car elle dispose de meilleures fonctionnalités pour prendre en charge les serveurs principaux du cloud et la purge du cache sur les hôtes dynamiques.

1. Le deuxième équilibreur de charge d’application d’équilibrage de charge Elastic Load répartit le trafic à partir du cache Varnish sur le groupe d’échelle automatique AWS des instances Adobe Commerce dans plusieurs zones de disponibilité.

1. Installez la dernière version de Magento Open Source ou Adobe Commerce sur les instances Amazon EC2. L&#39;installation se compose de l&#39;application Adobe Commerce, du serveur web Nginx et de PHP. Créez l’image de la machine Amazon (AMI) pour lancer de nouvelles instances dans un groupe de mise à l’échelle automatique.

1. Amazon Elasticsearch Service est un service d’Elasticsearch géré pour la recherche catalogue Adobe Commerce.

1. Amazon ElastiCache for Redis fournit une couche de mise en cache pour la base de données.

1. Utilisez Amazon Aurora ou AmazonRDS pour simplifier l’administration des bases de données (notamment la haute disponibilité et la configuration multi-maître).

1. La cible EFSMount permet de mapper facilement le système de fichiers adaptatif Amazon (AmazonEFS) aux instances de vernis et d’Adobe Commerce.

1. Utilisez Amazon EFS pour accéder à la configuration partagée sur l’ensemble des ressources multimédias en vernis et partagées sur les instances Adobe Commerce.

## Services cloud

En plus de fournir une plateforme technologique de prise en charge pour l’activation des processus DevOps sur AWS autour de votre environnement Adobe Commerce, AWS fournit un ensemble de services qui peuvent fournir (en l’absence de) ou améliorer vos solutions SCM (Software Configuration Management, gestion de la configuration logicielle) existantes. Cela inclut AWSCodeCommit, AWSCodeBuild, AWSCodePipeline et AWSCodeDeploy, ce qui permet un contrôle de source géré, une création, une intégration/déploiement continu (CI/CD) et des services de déploiement.

## Migration vers le cloud

La proposition de valeur pour la migration d’Adobe Commerce vers AWS est encore améliorée par la disponibilité de plusieurs services offrant une vision opérationnelle et une agilité. Ce que nous voulons dire, c&#39;est un aperçu opérationnel de la plateforme non seulement d&#39;un point de vue technique (par exemple, les demandes par heure) mais aussi d&#39;un point de vue opérationnel (par exemple, les commandes par heure), particulièrement lorsque les deux ensembles de données peuvent être mariés. Cela permet d’analyser en temps quasi réel les performances de la campagne, les coûts d’exploitation de la plateforme et un nombre presque infini d’autres indicateurs.

La configuration d’Adobe Commerce vers AWS peut remplacer des dépendances d’application spécifiques par des alternatives entièrement gérées disponibles dans le cloud. Par exemple, plutôt que d’héberger directement une base de données relationnelle sur des instances EC2, la base de données de nombreuses applications peut facilement être remplacée par le service de base de données relationnelle Amazon (AmazonRDS). Cette stratégie présente l’avantage que la responsabilité de fonctionnement des composants indifférenciés peut être déchargée vers AWS sans nécessiter de modifications importantes de l’application principale.

Plusieurs options de déploiement sont disponibles pour exécuter Adobe Commerce (versions Magento Open Source et Adobe Commerce) sur AWS. Le choix le plus approprié dépend de vos besoins en termes de coût, d’échelle, de disponibilité et de flexibilité, ainsi que des compétences AWS et Adobe Commerce de votre entreprise.

{{$include /help/_includes/hosting-related-links.md}}
