---
title: Phase de planification de la mise en oeuvre
description: Découvrez les bonnes pratiques de mise en oeuvre pour la phase de planification des projets Adobe Commerce.
role: Developer, Admin, User
feature: Best Practices
exl-id: 6baeac79-8dc3-45b4-bb25-8f2add8b3443
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '248'
ht-degree: 0%

---

# Phase de planification

La phase de planification comprend les activités suivantes :

- Collecte des exigences
- Design architectural
- Conception de catalogue
- Portée du projet
- Approvisionnement des comptes
- Accès utilisateur
- Achats d&#39;extensions

Les sections suivantes contiennent des informations sur les bonnes pratiques relatives à la phase de planification.

## Collecte des exigences

- **Configuration des applications**
   - [Bonnes pratiques relatives à la configuration des sites, des magasins et des vues de magasin (infrastructure cloud)](sites-stores-store-views.md)
   - [Comment prévenir et résoudre les cinq problèmes de configuration les plus courants pour les sites Adobe Commerce](https://business.adobe.com/blog/how-to/usual-suspects-five-configuration-fixes-maximize-your-peak-sales)
   - [Bonnes pratiques relatives à la mise en cache](https://docs.magento.com/user-guide/system/cache-management.html#best-practices-for-caching)
   - [Mise en cache complète des pages](https://developer.adobe.com/commerce/php/development/cache/page/public-content/)
   - [Taille de la mémoire OPcache](opcache-memory-size.md)
   - [Configuration des rapports](reporting-configuration.md)

- **Configuration de la base de données**
   - [Bonnes pratiques relatives à la configuration des bases de données pour les déploiements dans le cloud &#x200B;](database-on-cloud.md)
   - [Configuration de la connexion au Secondaire MySQL &#x200B;](configure-mysql-slave-connection-on-cloud.md)
   - [Utilisation des déclencheurs MySQL](mysql-triggers-usage.md)

- **Configuration des services**
   - [Configuration rapide](https://devdocs.magento.com/cloud/cdn/configure-fastly.html)
   - [New Relic - Configuration des canaux de notification](https://devdocs.magento.com/cloud/project/new-relic.html#configure-notification-channels)
   - [Bonnes pratiques relatives à la configuration du service Redis &#x200B;](redis-service-configuration.md)
   - [Meilleure pratique concernant la taille du cache du chemin d’accès réel](realpath-cache-size.md)

## **Design architectural**

<!--Asset not yet integrated
- [GRA Architecture examples](https://wiki.corp.adobe.com/x/kD4ykw)
-->
- [Présentation de l’architecture de référence globale](../../../implementation-playbook/architecture/global-reference.md)

## **Conception de catalogue**

Les rubriques suivantes décrivent les bonnes pratiques d’optimisation des performances pour la configuration de votre catalogue Adobe Commerce, notamment les maximums recommandés pour le nombre de catégories, les SKU efficaces sur les produits, les variations de produit, les attributs et options de produit, etc.

- [Configuration des catégories](category-limits.md)
- [&#x200B; de configuration de produit](product-sku-limits.md)
- [Configuration des variations de produit](product-variations.md)
- [Configuration des options de produit](product-options.md)
- [&#x200B; de configuration des attributs de produit](product-attributes-and-options.md)
- [Configuration de pagination pour les listes de produits](product-listing-pagination.md)

## **Ventes et marketing**

- [Bonnes pratiques relatives à la limite du panier de produits](product-cart.md)
- [Bonnes pratiques relatives à la configuration des promotions](product-cart-promotions.md)

## **Portée du projet**

- [Réaffectations de partenaire](partner-escalation.md)
- [Traitement du stockage des paiements](payment-processing-storage.md)

## **Extensions d’achat**

- [Bonnes pratiques relatives à l’utilisation d’extensions tierces dans Adobe Commerce](extensions.md)
