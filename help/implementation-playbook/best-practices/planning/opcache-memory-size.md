---
title: Bonne pratique pour la taille de la mémoire cache OP
description: Décrit comment éviter une dégradation des performances en raison de paramètres spécifiques de consommation de mémoire cache OP sur les projets Adobe Commerce.
role: Developer
feature: Best Practices
exl-id: d1e10068-e4e8-4e75-9f30-f3a89a08d791
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: cdfd3bc1-dc23-5cf0-b965-d3c0c55cde67
    internal-label: Best Practices
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '159'
ht-degree: 1%
---
# Bonne pratique pour la taille de la mémoire cache OP dans Adobe Commerce

Pour Adobe Commerce sur l’infrastructure cloud Pro plan architecture 2.3.x, il est recommandé de définir la `opcache.memory_consumption` sur au moins 2 Go, afin d’éviter une dégradation des performances.

## Produits et versions concernés

* Adobe Commerce sur les infrastructures cloud Pro plan architecture 2.3.x
* PHP 7.0 et versions ultérieures

## Configuration de la mémoire

Allouez au moins **2 Go** de mémoire pour le module PHP [OPcache](https://www.php.net/manual/en/book.opcache.php). Le module OPcache est configuré dans le fichier `php.ini`. Pour allouer 2 048 Mo de mémoire, définissez `opcache.memory_consumption = 2048`.

## Informations supplémentaires

* [Bonnes pratiques de performance - Paramètres PHP](../../../performance/software.md#php-settings)
* [Configuration des options PHP](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/app/configure-app-yaml)
* [Bonnes pratiques relatives aux bases de données pour Adobe Commerce sur les infrastructures cloud](database-on-cloud.md)
* [Problèmes de base de données les plus courants dans Adobe Commerce sur les infrastructures cloud](../maintenance/resolve-database-performance-issues.md)
* [La fonction « Mettre à jour selon le calendrier » des indexeurs optimise les performances d’Adobe Commerce](../maintenance/indexer-configuration.md)
