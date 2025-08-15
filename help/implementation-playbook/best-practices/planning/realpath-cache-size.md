---
title: Taille du cache du Realpath
description: Découvrez comment optimiser les performances d’Adobe Commerce en mettant à jour la configuration du cache de chemin de lecture PHP pour utiliser les paramètres recommandés.
role: Developer
feature: Best Practices, Cache
exl-id: 1cd48155-5d60-48b2-b07b-9b5784b81681
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '182'
ht-degree: 1%

---

# Bonnes pratiques relatives à la configuration du cache Realpath

Le cache Realpath met en cache les chemins réels des systèmes de fichiers pour les noms de fichiers référencés au lieu de les rechercher à chaque fois. Chaque fois que différentes fonctions de fichier sont effectuées ou nécessitent un fichier et utilisent un chemin relatif, PHP doit rechercher où ce fichier existe réellement.

Pour améliorer les performances de Commerce, utilisez les paramètres recommandés ci-dessous pour configurer les paramètres `realpath_cache` dans le fichier `php.ini` :

- Définissez la taille du cache sur 10 Mo (`realpath cache_size=10M`)
- Définissez la durée de vie (ttl) sur 7 200 secondes (`realpath_cache_ttl=7200`)

Pour les instructions de configuration, voir [Comment définir les options PHP](../../../installation/prerequisites/php-settings.md#how-to-set-php-options).

## Produits et versions concernés

- Adobe Commerce on-premise, toutes les versions 2.3.x et ultérieures
- Adobe Commerce sur les infrastructures cloud, toutes les versions 2.3.x et ultérieures

## Impact potentiel sur les performances

Si les valeurs de configuration du cache Realpath sont trop faibles ou trop élevées, cela ajoute une surcharge supplémentaire pendant la génération du cache, ce qui ralentit les performances.

## Informations supplémentaires

- [Sur site : paramètres PHP](../../../performance/software.md#php-settings)
- Sur les infrastructures cloud :
   - [Bonnes pratiques relatives aux bases de données](database-on-cloud.md)
   - [Problèmes de base de données les plus courants dans Magento Commerce Cloud](../maintenance/resolve-database-performance-issues.md)
- [La fonction « Mettre à jour selon le calendrier » des indexeurs optimise les performances de Magento](../maintenance/indexer-configuration.md)
