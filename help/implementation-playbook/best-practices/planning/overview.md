---
title: Phase de planification de l’implémentation
description: Découvrez les bonnes pratiques d’implémentation pour la phase de planification des projets Adobe Commerce.
role: Developer, Admin, User
feature: Best Practices
exl-id: 6baeac79-8dc3-45b4-bb25-8f2add8b3443
source-git-commit: ee7551374aa6d4ad462dd64ee3d05b934b43ce45
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 1%

---

# Phase de planification

La phase de planification comprend les activités suivantes :

- Design architectural
- Conception de catalogue
- Achat d’extension
- Définition de la portée du projet
- Collecte des exigences
- Ventes et marketing

Les sections suivantes contiennent des informations relatives aux bonnes pratiques pour la phase de planification.

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
    <td colspan="2"><em>Configuration de l’application</em></td>
  </tr>
  <tr>
    <td><a href="sites-stores-store-views.md">Configuration des sites, des boutiques et des vues de boutique</a></td>
    <td>Configurez les sites, les boutiques et les vues de boutique pour optimiser les performances du site.</td>
  </tr>
  <tr>
    <td><a href="https://business.adobe.com/blog/how-to/the-usual-suspects-5-configuration-issues-to-maximize-your-peak-sales">Problèmes de configuration courants</a></td>
    <td>Corrigez et évitez les cinq problèmes de configuration les plus courants pour les sites Adobe Commerce.</td>
  </tr>
  <tr>
    <td><a href="https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/cache-management.html?lang=fr">Mise en cache</a></td>
    <td>Utilisez les outils de gestion du cache pour améliorer les performances de votre site.</td>
  </tr>
  <tr>
    <td><a href="https://developer.adobe.com/commerce/php/development/cache/page/public-content/">Mise en cache de toutes les pages</a></td>
    <td>Découvrez comment utiliser les données publiques lors de l’implémentation de la mise en cache dans votre extension Adobe Commerce.</td>
  </tr>
  <tr>
    <td><a href="opcache-memory-size.md">Taille de la mémoire cache de l'OP</a></td>
    <td>Éviter la dégradation des performances avec des paramètres spécifiques de consommation de la mémoire cache OP.</td>
  </tr>
  <tr>
    <td><a href="reporting-configuration.md">Configuration des rapports</a></td>
    <td>Optimisez les performances du site en supprimant le module de création de rapports si vous ne l’utilisez pas.</td>
  </tr>
  <tr>
    <td colspan="2"><em>Configuration de la base de données</em></td>
  </tr>
  <tr>
    <td><a href="database-on-cloud.md">Configuration de la base de données pour les déploiements cloud</a></td>
    <td>Configurez les paramètres de la base de données et de l’application pour améliorer les performances lors du déploiement d’Adobe Commerce sur des projets d’infrastructure cloud.</td>
  </tr>
  <tr>
    <td><a href="mysql-configuration.md">Configurer MySQL</a></td>
    <td>Découvrez comment les déclencheurs MySQL et les connexions esclaves affectent les performances du site et comment les utiliser efficacement.</td>
  </tr>
  <tr>
    <td colspan="2"><em>Configuration des services</em></td>
  </tr>
  <tr>
    <td><a href="https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html?lang=fr">Configuration rapide</a></td>
    <td>Configurez les services Fastly pour votre projet d’infrastructure cloud Adobe Commerce.</td>
  </tr>
  <tr>
    <td><a href="https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/monitor/new-relic.html?lang=fr">Configuration des canaux de notification pour New Relic</a></td>
    <td>Accédez à votre tableau de bord New Relic et analysez les données de votre projet d’infrastructure cloud Adobe Commerce.</td>
  </tr>
  <tr>
    <td><a href="redis-service-configuration.md">Configurer Redis</a></td>
    <td>Améliorez les performances de la mise en cache en utilisant l’implémentation du cache Redis étendue pour Adobe Commerce.</td>
  </tr>
  <tr>
    <td><a href="realpath-cache-size.md">Taille du cache du Realpath</a></td>
    <td>Optimisez les performances en mettant à jour la configuration de cache PHP « readlpath » pour utiliser les paramètres recommandés.</td>
  </tr>
</tbody>
</table>

## Conception de catalogue

| Bonne pratique | Description |
|---------------------------------------------------------------------------------------------------|---------------------------------------------------------------|
| [Configuration de la catégorie](catalog-management.md#category-limits) | Configurez des catégories de produits pour des performances optimales. |
| [Configuration du produit&#x200B;](catalog-management.md#product-sku-limits) | Configurez les SKU de produit pour des performances optimales. |
| [Configuration de variation de produit](catalog-management.md#product-variations) | Configurez les variations de produit pour des performances optimales. |
| [Configuration des options du produit](catalog-management.md#product-options) | Configurez les options du produit pour des performances optimales. |
| [Configuration des attributs de produit&#x200B;](catalog-management.md#product-attributes) | Configurez les attributs de produit pour des performances optimales. |
| [Configuration de la pagination pour les listes de produits](catalog-management.md#product-listing-pagination) | Configurez la pagination des listes de produits pour des performances optimales. |

## Extensions

| Bonne pratique | Description |
|-----------------------------------------------------------------|----------------------------------------------------------------------------------------|
| [Utilisation d’extensions tierces dans Adobe Commerce](extensions.md) | Découvrez comment éviter les problèmes de performances causés par les extensions Adobe Commerce tierces. |

## Définition de la portée du projet

| Bonne pratique | Description |
|--------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------|
| [Escalades des partenaires](partner-escalation.md) | Préparez-vous à signaler un problème de partenaire à une équipe de compte Adobe ou apprenez à éviter une signalisation. |
| [Traitement du stockage des paiements](payment-processing-storage.md) | Traitez et stockez en toute sécurité les informations de paiement. |

## Ventes et marketing

| Bonne pratique | Description |
|------------------------------------------------------------|--------------------------------------------------------------|
| [Limites du panier de produits](catalog-management.md#cart-limits) | Gérez les limites du panier pour des performances optimales. |
| [Configuration des promotions](catalog-management.md#promotions) | Configurez les ventes et les promotions pour les articles d’un panier. |
