---
title: Architecture de référence
description: Consultez les diagrammes de l’architecture de référence recommandée pour les déploiements d’Adobe Commerce.
exl-id: 85a6d3d6-f47f-4806-97bd-fa7a73605f4c
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '414'
ht-degree: 0%

---

# Architecture de référence

Cette rubrique décrit une configuration générique recommandée pour les instances Adobe Commerce utilisant des serveurs simples hébergés physiquement dans un centre de données (non virtualisé) dans lequel les ressources ne sont pas partagées avec d’autres utilisateurs. Votre fournisseur d’hébergement, en particulier s’il est spécialisé dans l’hébergement haute performance de Commerce, peut recommander une configuration différente qui est également ou plus efficace pour vos besoins.

Pour Adobe Commerce sur les environnements d’infrastructure cloud, voir [Architecture de démarrage](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/architecture/starter-architecture).

## Diagramme d’architecture de référence [!DNL Commerce]

Le diagramme d’architecture de référence [!DNL Commerce] représente l’approche recommandée pour configurer un site [!DNL Commerce] évolutif.

La couleur de chaque élément du diagramme indique si l’élément fait partie de Magento Open Source ou d’Adobe Commerce et s’il est obligatoire.

* Les éléments orange sont requis pour Magento Open Source
* Les éléments gris sont facultatifs pour Magento Open Source
* Les éléments bleus sont facultatifs pour Adobe Commerce

![Diagramme d’architecture de référence Commerce](../assets/performance/images/ref-architecture-2.3.png)

Les sections suivantes fournissent des recommandations et des considérations pour chaque section du diagramme d’architecture de référence de Commerce.

### [!DNL Varnish]

* Un cluster [!DNL Varnish] peut être mis à l’échelle pour gérer le trafic d’un site
* Réglez la taille de l’instance en fonction du nombre de pages de cache nécessaires
* Sur un site à trafic élevé, utilisez un Principal [!DNL Varnish] pour garantir que la purge sur le cache s’effectue à une seule requête (au plus) par niveau web

### Web

* Activer l’échelle des nœuds pour le trafic et la redondance
* Un nœud est le nœud principal et exécute cron
* Vous pouvez également utiliser un nœud Administrateur et de travail dédié

### Cache

* Envisagez de mettre en œuvre une instance Redis distincte pour les sessions
* Vous pouvez avoir une instance Redis par cache
* Dimensionnez votre instance pour qu’elle contienne la plus grande taille de cache attendue

### Base de données et files d&#39;attente

* Les sites à trafic élevé peuvent ajuster les performances des bases de données avec des bases de données esclaves et des bases de données fractionnées pour les commandes et les paniers (dans Adobe Commerce).
* Envisagez d’utiliser une base de données esclave pour permettre une récupération rapide et des sauvegardes de données
* Les sites à faible trafic peuvent stocker des images dans la base de données

### Rechercher {#search-heading}

* Régler le nombre d’instances en fonction du trafic de recherche

### Stockage

* Envisagez d’utiliser GFS ou GlusterFS pour le stockage sur pub/média
* Vous pouvez également utiliser le stockage de la base de données pour les sites à faible trafic

### Architecture de référence [!DNL Varnish] recommandée

Magento prend en charge plusieurs moteurs de mise en cache de pages complètes (File, Memcache, Redis, [!DNL Varnish]) prêts à l’emploi, ainsi qu’une couverture étendue par le biais d’extensions. [!DNL Varnish] est le moteur de cache de page complète recommandé.  [!DNL Commerce] prend en charge de nombreuses configurations de [!DNL Varnish] différentes.

Pour les sites qui ne nécessitent pas de haute disponibilité, nous vous recommandons d&#39;utiliser une configuration [!DNL Varnish] simple avec terminaison SSL Nginx.

![Configuration de [!DNL Varnish] simple avec terminaison SSL](../assets/performance/images/single-varnish-with-ssl-termination.png)

Pour les sites qui nécessitent une haute disponibilité, nous vous recommandons d’utiliser une configuration [!DNL Varnish] à 2 niveaux avec une répartition de charge à terminaison SSL.

![Configuration de [!DNL Varnish] à deux niveaux haute disponibilité avec équilibreur de charge à terminaison SSL](../assets/performance/images/ha-2-tier-varnish-with-ssl-term-load-balancer.png)
