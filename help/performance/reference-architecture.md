---
title: Architecture de référence
description: Examinez les diagrammes de l’architecture de référence recommandée pour les déploiements Adobe Commerce.
exl-id: 85a6d3d6-f47f-4806-97bd-fa7a73605f4c
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '414'
ht-degree: 0%

---

# Architecture de référence

Cette rubrique décrit une configuration recommandée générique pour les instances Adobe Commerce utilisant des serveurs standard hébergés physiquement dans un centre de données (non virtualisés) dans lequel les ressources ne sont pas partagées avec d’autres utilisateurs. Votre fournisseur d’hébergement, en particulier s’il se spécialise dans l’hébergement haute performance de Commerce, peut recommander une configuration différente qui soit également ou plus efficace pour vos besoins.

Pour Adobe Commerce dans les environnements d’infrastructure cloud, voir [Architecture de démarrage](https://experienceleague.adobe.com/fr/docs/commerce-cloud-service/user-guide/architecture/starter-architecture).

## [!DNL Commerce] Diagramme d’architecture de référence

Le diagramme [!DNL Commerce] de l’architecture de référence représente l’approche recommandée pour configurer un site [!DNL Commerce] évolutif.

La couleur de chaque élément du diagramme indique si l’élément fait partie de Magento Open Source ou d’Adobe Commerce et s’il est obligatoire.

* Les éléments orange sont requis pour Magento Open Source
* Les éléments gris sont facultatifs pour Magento Open Source.
* Les éléments bleus sont facultatifs pour Adobe Commerce.

![ Diagramme d’architecture de référence Commerce](../assets/performance/images/ref-architecture-2.3.png)

Les sections suivantes contiennent des recommandations et des considérations pour chaque section du diagramme de l’architecture de référence de Commerce.

### [!DNL Varnish]

* Une grappe [!DNL Varnish] peut s’adapter au trafic d’un site.
* Réglez la taille de l’instance en fonction du nombre de pages du cache nécessaire.
* Sur un site à trafic élevé, utilisez un Principal [!DNL Varnish] pour vous assurer que le vidage en cache d’une requête (au plus) par niveau web.

### Web

* Activer l’échelle des noeuds pour le trafic et la redondance
* Un noeud est maître et exécute cron
* Vous pouvez également utiliser un noeud Admin et Worker dédié.

### Cache

* Envisagez de mettre en oeuvre une instance Redis distincte pour les sessions.
* Vous pouvez avoir une instance Redis par cache.
* Dimensionnez l’instance pour qu’elle contienne la plus grande taille de cache attendue.

### Base de données et files d’attente

* Les sites à trafic élevé peuvent optimiser les performances de la base de données avec des bases de données esclaves et fractionner les bases de données pour les commandes/paniers (dans Adobe Commerce).
* Envisagez d’utiliser une base de données esclave pour permettre une récupération rapide et des sauvegardes de données.
* Les sites à faible trafic peuvent stocker des images dans la base de données

### Rechercher {#search-heading}

* Réglage du nombre d’instances en fonction du trafic de recherche

### Stockage

* Envisagez d’utiliser GFS ou GlusterFS pour le stockage des pub/médias.
* Vous pouvez également utiliser le stockage DB pour les sites à faible trafic.

### Architecture de référence [!DNL Varnish] recommandée

Magento prend en charge plusieurs moteurs de mise en cache de page complète (File, Memcache, Redis, [!DNL Varnish]) prêts à l’emploi, ainsi qu’une couverture étendue par le biais d’extensions. [!DNL Varnish] est le moteur de cache de page complète recommandé.  [!DNL Commerce] prend en charge de nombreuses configurations [!DNL Varnish] différentes.

Pour les sites qui ne nécessitent pas de haute disponibilité, nous vous recommandons d’utiliser une configuration simple [!DNL Varnish] avec terminaison SSL Nginx.

![Configuration simple [!DNL Varnish] avec arrêt SSL](../assets/performance/images/single-varnish-with-ssl-termination.png)

Pour les sites qui nécessitent une haute disponibilité, nous vous recommandons d’utiliser une configuration [!DNL Varnish] à 2 niveaux avec un équilibreur de charge d’arrêt SSL.

![ Configuration à deux niveaux haute disponibilité [!DNL Varnish] avec SSL arrêtant l&#39;équilibreur de charge](../assets/performance/images/ha-2-tier-varnish-with-ssl-term-load-balancer.png)
