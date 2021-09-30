---
title: Adobe Commerce Microservices
description: Être capable de différencier les produits et les microservices en ce qui concerne Adobe Commerce.
source-git-commit: 748c302527617c6a9bf7d6e666c6b3acff89e021
workflow-type: tm+mt
source-wordcount: '318'
ht-degree: 0%

---


# Sans affichage et microservices

Il est important de ne pas confondre tête-baissée avec microservices. La plupart du temps, nous entendons des conversations sur les microservices dans la même phrase que sans tête. Ce sont des choses complètement différentes. Ils peuvent être utilisés ensemble, mais ce sont des concepts complètement différents.

Une architecture de microservices est un terme utilisé pour décrire la pratique consistant à diviser une application en un ensemble de services plus petits et à couplage faible. Les microservices permettent à des services principaux individuels d’être :

- **Isolé l’un de l’autre** : par exemple, le service de tarification ne dépend pas du service de catalogue.

- **Déployé à la carte** : les clients déploient uniquement les parties de l’application dont ils ont besoin.

- **Échelle indépendante** : les ressources peuvent être affectées à des services à forte demande, tels que la recherche d’inventaire.

- **Développement** autonome : peut être développé et déployé indépendamment l’un de l’autre.

Les microservices n’ont rien à voir avec le fait de couper l’accès de la pile commerciale ou des API. Quand nous pensons à ces services commerciaux dans le code principal qui sont dans le back office d’Adobe Commerce, il s’agit d’isoler ces services les uns des autres. Ainsi, une architecture de microservices est en train de décomposer tous ces services comme les services de tarification, les services de catalogue et les services d&#39;inventaire, et de les isoler les uns des autres. Cela garantit qu’il s’agit d’un panier de sorte que vous n’ayez pas besoin d’acheter et de déployer tous les produits Adobe Commerce en une seule fois.

Les microservices peuvent être développés indépendamment et développés de manière autonome. Les microservices ressemblent à un processus de développement SaaS multi-locataires. De nombreux produits SaaS multi-locataires modernes sont développés selon une approche multi-services. Même les propres produits SaaS d’Adobe, comme la gestion des commandes, le nouvel outil Recommendations basé sur l’IA et d’autres composants SaaS d’Adobe Commerce sont développés à l’aide d’une approche de microservices. Pour être très clair, Adobe Commerce 2.4.x n’est pas une architecture de microservices, mais plutôt une architecture sans interface.
