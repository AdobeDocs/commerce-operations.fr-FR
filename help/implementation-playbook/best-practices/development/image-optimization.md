---
title: Optimisation des images pour un site plus réactif
description: Découvrez les étapes à suivre pour optimiser les images et utilisez l’optimisation rapide des images pour optimiser le temps de réponse sur vos sites Adobe Commerce.
role: Developer, Admin
feature: Best Practices
exl-id: ada8b987-97ed-4232-9e1b-7e0a791a0807
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '197'
ht-degree: 1%

---

# Optimisation des images pour un site plus réactif

Pour Adobe Commerce sur les déploiements d’infrastructure cloud, améliorez le temps de réponse du site en optimisant les images avant de les charger. Ensuite, utilisez l’optimisation rapide des images pour accélérer la diffusion des images et simplifier la maintenance des visionneuses d’images sources.

## Produits et versions concernés

[Toutes les versions prises en charge](../../../release/versions.md) de :

Adobe Commerce sur les infrastructures cloud


## Optimisation et compression des images

Avant de charger des images sur vos sites Commerce, optimisez et compressez-les pour équilibrer les performances avec la qualité d’affichage. Cela permet d’augmenter l’espace et de réduire le temps de chargement des pages.

- Le format PNG offre des images de plus petites tailles pour les images présentant de grandes zones de couleur unie.

- Le format JPEG offre des images de plus petites tailles pour tous les autres types d’images. Utilisez la compression la plus élevée (sans dégradation notable). C&#39;est habituellement 60 à 80%.

## Activer et configurer l’optimisation d’image Fastly

Une fois que vous avez configuré le service Fastly pour votre projet Adobe Commerce Cloud, consultez [Optimisation des images Fastly](https://experienceleague.adobe.com/fr/docs/commerce-cloud-service/user-guide/cdn/fastly-image-optimization) pour obtenir des instructions sur l’activation et la configuration de l’optimisation des images.

## Informations supplémentaires

- [Configuration rapide](https://experienceleague.adobe.com/fr/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration)
- [Des images mal optimisées peuvent entraîner des problèmes de performances](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/file-storage-low-specific-page-loads-are-slow.html?lang=fr)
