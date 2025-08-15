---
title: Bonne pratique pour la taille de la mémoire cache OP
description: Décrit comment éviter une dégradation des performances en raison de paramètres spécifiques de consommation de mémoire cache OP sur les projets Adobe Commerce.
role: Developer
feature: Best Practices
exl-id: d1e10068-e4e8-4e75-9f30-f3a89a08d791
source-git-commit: 6c0a9268cb3a3b2e76f4a389846e8407f0893b4f
workflow-type: tm+mt
source-wordcount: '138'
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
* [Configurer les options PHP](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/app/configure-app-yaml)
* [Bonnes pratiques relatives aux bases de données pour Adobe Commerce sur les infrastructures cloud](database-on-cloud.md)
* [Problèmes de base de données les plus courants dans Adobe Commerce sur les infrastructures cloud](../maintenance/resolve-database-performance-issues.md)
* [La fonction « Mettre à jour selon le calendrier » des indexeurs optimise les performances d’Adobe Commerce](../maintenance/indexer-configuration.md)
