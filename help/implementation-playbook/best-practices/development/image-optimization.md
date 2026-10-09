---
title: Optimisation des images pour un site plus réactif
description: Découvrez les étapes à suivre pour optimiser les images et utilisez l’optimisation rapide des images pour optimiser le temps de réponse sur vos sites Adobe Commerce.
role: Developer, Admin
feature: Best Practices
exl-id: ada8b987-97ed-4232-9e1b-7e0a791a0807
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: cdfd3bc1-dc23-5cf0-b965-d3c0c55cde67
    internal-label: Best Practices
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '239'
ht-degree: 0%
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

Une fois que vous avez configuré le service Fastly pour votre projet Adobe Commerce Cloud, consultez [Optimisation des images Fastly](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/cdn/fastly-image-optimization) pour obtenir des instructions sur l’activation et la configuration de l’optimisation des images.

## Informations supplémentaires

- [Configuration rapide](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/cdn/setup-fastly/fastly-configuration)
- [Des images mal optimisées peuvent entraîner des problèmes de performances](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/file-storage-low-specific-page-loads-are-slow)
