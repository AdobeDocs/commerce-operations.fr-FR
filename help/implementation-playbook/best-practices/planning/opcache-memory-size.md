---
title: Bonne pratique pour la taille de mémoire OPcache
description: Décrit comment éviter une dégradation des performances par des paramètres spécifiques de la consommation de mémoire OPcache sur les projets Adobe Commerce.
role: Developer
feature: Best Practices
feature-set: Commerce
source-git-commit: 85f9355d0e8c704be3760334b07414d3e15b3b97
workflow-type: tm+mt
source-wordcount: '147'
ht-degree: 0%

---


# Bonne pratique pour la taille de mémoire OPcache dans Adobe Commerce

Pour Adobe Commerce sur l’infrastructure cloud Pro, il est recommandé de définir la variable `opcache.memory_consumption` à au moins 2 Go pour éviter une dégradation des performances.

## Produits et versions concernés

* Adobe Commerce sur l’infrastructure cloud Architecture de plan Pro 2.3.x
* PHP 7.0 et versions ultérieures

## Configurer la mémoire

Allouer au moins **2 Go** de la mémoire pour le [Module PHP OPcache](https://www.php.net/manual/en/book.opcache.php). Le module OPcache est configuré dans la variable `php.ini` fichier . Pour allouer 2 048 Mo de mémoire, définissez `opcache.memory_consumption = 2048`.

## Informations supplémentaires

* [Bonnes pratiques de performances - Paramètres PHP](../../../performance/software.md#php-settings)
* [Configuration des options PHP](https://devdocs.magento.com/cloud/project/project-conf-files_magento-app.html#customize-phpini-settings)
* [Bonnes pratiques relatives aux bases de données pour Adobe Commerce sur l’infrastructure cloud](database-on-cloud.md)
* [Problèmes de base de données les plus courants dans Adobe Commerce sur l’infrastructure cloud](../maintenance/resolve-database-performance-issues.md)
* [Les indexeurs &quot;Mettre à jour selon le calendrier&quot; optimisent les performances d’Adobe Commerce](../maintenance/indexer-configuration.md)
