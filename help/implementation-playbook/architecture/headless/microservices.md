---
title: Microservices Adobe Commerce
description: être capable de différencier les produits et les microservices en fonction de leur pertinence avec Adobe Commerce ;
exl-id: 078e0e8e-7acc-4913-8b78-585a950f3f5e
source-git-commit: 4e8f6ce05c14195433e7c46e6090a93a76b8b5f9
workflow-type: tm+mt
source-wordcount: '294'
ht-degree: 0%

---

# Sans affichage et microservices

Il est important de ne pas confondre tête-baissée avec microservices. La plupart du temps, nous entendons des conversations sur les microservices dans la même phrase que sans tête. Ce sont des choses complètement différentes. Ils peuvent être utilisés ensemble, mais ce sont des concepts complètement différents.

Une architecture de microservices est un terme utilisé pour décrire la pratique consistant à diviser une application en un ensemble de services plus petits et à couplage faible. Les microservices permettent à des services principaux individuels d’être :

- **Isolés les uns des autres**: par exemple, le service de tarification ne dépend pas du service de catalogue.

- **Déployé à la carte**: les clients ne déploient que les parties de l’application dont ils ont besoin.

- **Échelle indépendamment**: les ressources peuvent être affectées à des services à forte demande, tels que la recherche d’inventaire.

- **Autonomie développée**: peut être développé et déployé indépendamment l’un de l’autre.

Les microservices n’ont rien à voir avec le fait de couper l’accès de la pile commerciale ou des API. Quand nous pensons à ces services commerciaux dans le code principal qui se trouvent dans le back-office d’Adobe Commerce, il s’agit d’isoler ces services les uns des autres. Ainsi, une architecture de microservices est en train de décomposer tous ces services comme les services de tarification, les services de catalogue et les services d&#39;inventaire, et de les isoler les uns des autres.

Les microservices peuvent être développés indépendamment et développés de manière autonome. Les microservices ressemblent à un processus de développement SaaS multi-locataires. De nombreux produits SaaS multi-locataires modernes sont développés selon une approche multi-services. Même les propres produits SaaS d’Adobe, tels que la gestion des commandes, le nouvel outil Recommendations basé sur l’IA et d’autres composants SaaS d’Adobe Commerce, sont développés à l’aide d’une approche de microservices. Pour être très clair, Adobe Commerce 2.4.x n’est pas une architecture de microservices, mais plutôt une architecture sans interface.
