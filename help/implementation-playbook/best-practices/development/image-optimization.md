---
title: Optimiser les images pour un site plus réactif
description: Découvrez les étapes d’optimisation des images et d’optimisation rapide des images pour optimiser le temps de réponse sur vos sites Adobe Commerce.
role: Developer, Admin
feature: Best Practices
exl-id: ada8b987-97ed-4232-9e1b-7e0a791a0807
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '210'
ht-degree: 0%

---

# Optimiser les images pour un site plus réactif

Pour Adobe Commerce sur les déploiements d’infrastructure cloud, augmentez le temps de réponse du site en optimisant les images avant de les télécharger. Ensuite, utilisez l’optimisation d’image rapide pour accélérer la diffusion des images et simplifier la maintenance des visionneuses de sources d’images.

## Produits et versions concernés

[Toutes les versions prises en charge](../../../release/versions.md) de :

Adobe Commerce sur l’infrastructure cloud


## Optimisation et compression des images

Avant de charger des images sur vos sites Commerce, optimisez-les et compressez-les pour équilibrer les performances avec la qualité d’affichage. Cela permet d’augmenter l’espace et de réduire les temps de chargement des pages.

- Le format PNG fournit des images de plus petite taille pour les images avec de grandes zones de couleur unie.

- Le format JPEG fournit des images de plus petite taille pour tous les autres types d’images. Utilisez la compression la plus élevée (sans dégradation notable). C&#39;est en général entre 60 et 80%.

## Activation et configuration de l’optimisation d’images Fastly

Une fois que vous avez configuré le service Fastly pour votre projet Adobe Commerce Cloud, voir [Optimisation rapide des images](https://devdocs.magento.com/cloud/cdn/fastly-image-optimization.html) pour obtenir des instructions sur l’activation et la configuration de l’optimisation des images.

## Informations supplémentaires

- [Configuration rapide](https://devdocs.magento.com/cloud/cdn/configure-fastly.html)
- [Les images mal optimisées peuvent entraîner des problèmes de performances.](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/file-storage-low-specific-page-loads-are-slow.html)
