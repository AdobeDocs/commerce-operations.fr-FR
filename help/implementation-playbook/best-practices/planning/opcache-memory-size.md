---
title: Bonne pratique pour la taille de mémoire OPcache
description: Décrit comment éviter une dégradation des performances par des paramètres spécifiques de la consommation de mémoire OPcache sur les projets Adobe Commerce.
role: Developer
feature: Best Practices
exl-id: d1e10068-e4e8-4e75-9f30-f3a89a08d791
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '138'
ht-degree: 1%

---

# Bonne pratique pour la taille de mémoire OPcache dans Adobe Commerce

Pour Adobe Commerce sur l’infrastructure cloud Pro, planifiez l’architecture 2.3.x, il est recommandé de définir `opcache.memory_consumption` sur 2 Go au moins, afin d’éviter une dégradation des performances.

## Produits et versions concernés

* Adobe Commerce sur l’infrastructure cloud Architecture de plan Pro 2.3.x
* PHP 7.0 et versions ultérieures

## Configurer la mémoire

Allouez au moins **2 Go** de mémoire pour le [module PHP OPcache](https://www.php.net/manual/en/book.opcache.php). Le module OPcache est configuré dans le fichier `php.ini` . Pour allouer 2 048 Mo de mémoire, définissez `opcache.memory_consumption = 2048`.

## Informations supplémentaires

* [ Bonnes pratiques de performances - Paramètres PHP](../../../performance/software.md#php-settings)
* [Configurer les options PHP](https://devdocs.magento.com/cloud/project/project-conf-files_magento-app.html#customize-phpini-settings)
* [Bonnes pratiques relatives aux bases de données pour Adobe Commerce sur l’infrastructure cloud](database-on-cloud.md)
* [Problèmes de base de données les plus courants dans Adobe Commerce sur l’infrastructure cloud](../maintenance/resolve-database-performance-issues.md)
* [Les indexeurs &quot;Mise à jour selon le calendrier&quot; optimisent les performances d’Adobe Commerce](../maintenance/indexer-configuration.md)
