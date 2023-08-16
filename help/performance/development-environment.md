---
title: Recommendations d’environnement de développement
description: Découvrez les recommandations de performances pour configurer votre environnement de développement Adobe Commerce ou Magento Open Source local.
exl-id: f57396c0-86be-4933-8066-eb51c42fb9e4
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '235'
ht-degree: 0%

---

# Recommandations relatives à l’environnement de développement

Cette page fournit des recommandations pour les environnements de développement Commerce.

## Nettoyer les caches au lieu de désactiver

De nombreux développeurs ont tendance à désactiver tous les caches sur leurs instances de développeur. Il est recommandé de ne nettoyer que les caches, sans désactiver tous les caches. [!DNL Commerce] s’exécute plus efficacement lorsque vous [nettoyage des caches](../configuration/cli/manage-cache.md#clean-and-flush-cache-types) au lieu de les désactiver complètement. La plupart des types de caches sont rarement invalidés lors du développement.

Si vous [Désactivation des caches](../configuration/cli/manage-cache.md#enable-or-disable-cache-types), nous vous recommandons de ne désactiver que les caches de page et de bloc dans les instances de développement. N’oubliez pas d’activer tous les caches pendant le test.

## Commandes à éviter en mode de développement

En mode de développement, n’exécutez pas de commandes pour la compilation, la génération de code et le déploiement de contenu statique. Ces commandes ont été créées pour une utilisation en mode de production uniquement.

**Ne pas exécuter** commandes de production en mode de développement :

* `setup:di:compile` génère des classes générées automatiquement et des caches de configuration optimisés.

  ```bash
  bin/magento setup:di:compile
  ```

  En mode de développement, Magento effectue la génération à la demande ; vous n’avez pas besoin de l’exécuter. Si vous avez modifié la signature d’une classe et que vous devez générer à nouveau son auto-généré `factories/proxies/interceptors`, supprimez ces classes ou la variable _généré_ dossier.

* `setup:static-content:deploy` déploie le contenu statique pour un magasin.

  ```bash
  bin/magento setup:static-content:deploy
  ```

  En mode de développement, Magento l’exécute à la demande ; vous n’avez pas besoin de l’exécuter.

## Durée normale de chargement des pages sur une machine virtuelle

Si vous développez sur une machine virtuelle et que le chargement d’une page de Magento prend plus de 2 secondes, vérifiez les paramètres de votre environnement.
