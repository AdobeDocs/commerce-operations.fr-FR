---
title: Phase de planification de la mise en oeuvre
description: Découvrez les bonnes pratiques de mise en oeuvre pour la phase de planification des projets Adobe Commerce.
role: Developer, Admin, User
feature: Best Practices
exl-id: 6baeac79-8dc3-45b4-bb25-8f2add8b3443
source-git-commit: 48ed42e69c5786a10de3426d581e35030412c001
workflow-type: tm+mt
source-wordcount: '458'
ht-degree: 1%

---

# Planification

La phase de planification comprend les activités suivantes :

- Design architectural
- Conception de catalogue
- Achats d&#39;extensions
- Portée du projet
- Collecte des exigences
- Ventes et marketing

Les sections suivantes contiennent des informations sur les bonnes pratiques relatives à la phase de planification.

## Collecte des exigences

<table>
<thead>
  <tr>
    <th>Bonne pratique</th>
    <th>Description</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td colspan="2"><em>Configuration des applications</em></td>
  </tr>
  <tr>
    <td><a href="sites-stores-store-views.md">Configuration des sites, des magasins et des vues de magasin</a></td>
    <td>Configurez les sites, les magasins et les vues de magasin afin d’optimiser les performances du site.</td>
  </tr>
  <tr>
    <td><a href="https://business.adobe.com/blog/how-to/usual-suspects-five-configuration-fixes-maximize-your-peak-sales">Problèmes de configuration courants</a></td>
    <td>Correction et prévention des cinq problèmes de configuration les plus courants pour les sites Adobe Commerce.</td>
  </tr>
  <tr>
    <td><a href="https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/cache-management.html">Mise en cache</a></td>
    <td>Utilisez les outils de gestion du cache pour améliorer les performances de votre site.</td>
  </tr>
  <tr>
    <td><a href="https://developer.adobe.com/commerce/php/development/cache/page/public-content/">Mise en cache pleine page</a></td>
    <td>Découvrez comment utiliser les données publiques lors de l’implémentation de la mise en cache dans votre extension Adobe Commerce ou Magento Open Source.</td>
  </tr>
  <tr>
    <td><a href="opcache-memory-size.md">Taille de la mémoire OPcache</a></td>
    <td>Évitez la dégradation des performances avec des paramètres spécifiques de la consommation de mémoire OPcache.</td>
  </tr>
  <tr>
    <td><a href="reporting-configuration.md">Configuration de la création de rapports</a></td>
    <td>Optimisez les performances du site en supprimant le module de reporting si vous ne l’utilisez pas.</td>
  </tr>
  <tr>
    <td colspan="2"><em>Configuration de la base de données</em></td>
  </tr>
  <tr>
    <td><a href="database-on-cloud.md">Configuration de la base de données pour les déploiements cloud</a></td>
    <td>Configurez les paramètres de base de données et d’application pour améliorer les performances lors du déploiement d’Adobe Commerce sur des projets d’infrastructure cloud.</td>
  </tr>
  <tr>
    <td><a href="mysql-configuration.md">Configuration de MySQL</a></td>
    <td>Découvrez comment les déclencheurs MySQL et les connexions esclaves affectent les performances du site et comment les utiliser efficacement.</td>
  </tr>
  <tr>
    <td colspan="2"><em>Configuration des services</em></td>
  </tr>
  <tr>
    <td><a href="https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html">Configuration rapide</a></td>
    <td>Configurez des services rapides pour votre projet d’infrastructure cloud Adobe Commerce.</td>
  </tr>
  <tr>
    <td><a href="https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/monitor/new-relic.html">Configuration des canaux de notification pour New Relic</a></td>
    <td>Accédez à votre tableau de bord New Relic et analysez les données de votre projet d’infrastructure cloud Adobe Commerce.</td>
  </tr>
  <tr>
    <td><a href="redis-service-configuration.md">Configuration de Redis</a></td>
    <td>Améliorez les performances de mise en cache en utilisant l’implémentation étendue du cache Redis pour Adobe Commerce.</td>
  </tr>
  <tr>
    <td><a href="realpath-cache-size.md">Taille du cache du chemin d’accès réel</a></td>
    <td>Optimisez les performances en mettant à jour la configuration du cache PHP `readlpath` pour utiliser les paramètres recommandés.</td>
  </tr>
</tbody>
</table>

## Design architectural

| Bonne pratique | Description |
|----------------------------------------------------------------------------------------|----------------------------------------------------------|
| [Architecture de référence globale (GRA)](../../architecture/global-reference/examples.md) | Découvrez les méthodes courantes d’organisation d’une base de code GRA. |

## Conception de catalogue

| Bonne pratique | Description |
|---------------------------------------------------------------------------------------------------|---------------------------------------------------------------|
| [Configuration des catégories](catalog-management.md#category-limits) | Configurez des catégories de produits pour des performances optimales. |
| [&#x200B; de configuration de produit](catalog-management.md#product-sku-limits) | Configurez des SKU de produit pour des performances optimales. |
| [Configuration des variations de produit](catalog-management.md#product-variations) | Configurez des variations de produit pour des performances optimales. |
| [Configuration des options de produit](catalog-management.md#product-options) | Configurez les options de produit pour des performances optimales. |
| [&#x200B; de configuration des attributs de produit](catalog-management.md#product-attributes) | Configurez les attributs de produit pour des performances optimales. |
| [Configuration de pagination pour les listes de produits](catalog-management.md#product-listing-pagination) | Configurez la pagination des listes de produits pour des performances optimales. |

## Extensions

| Bonne pratique | Description |
|-----------------------------------------------------------------|----------------------------------------------------------------------------------------|
| [Utilisation d’extensions tierces dans Adobe Commerce](extensions.md) | Découvrez comment éviter les problèmes de performances causés par les extensions tierces d’Adobe Commerce. |

## Portée du projet

| Bonne pratique | Description |
|--------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------|
| [Réaffectations de partenaire](partner-escalation.md) | Préparez-vous à la réaffectation d’un problème de partenaire avec une équipe de compte d’Adobe ou apprenez à éviter une réaffectation. |
| [Traitement du stockage des paiements](payment-processing-storage.md) | Traitez et stockez en toute sécurité les informations de paiement. |

## Ventes et marketing

| Bonne pratique | Description |
|------------------------------------------------------------|--------------------------------------------------------------|
| [Limites du panier de produits](catalog-management.md#cart-limits) | Gérez les limites de panier pour des performances optimales. |
| [Configuration des promotions](catalog-management.md#promotions) | Configurez les ventes et les promotions pour les articles d’un panier. |
