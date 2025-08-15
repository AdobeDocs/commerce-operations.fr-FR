---
title: Recommandations relatives à l’environnement de développement
description: Découvrez les recommandations de performances pour configurer votre environnement de développement Adobe Commerce local.
exl-id: f57396c0-86be-4933-8066-eb51c42fb9e4
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '232'
ht-degree: 0%

---

# Recommandations relatives à l’environnement de développement

Cette page fournit des recommandations pour les environnements de développement Commerce.

## Nettoyez les caches au lieu de les désactiver.

De nombreux développeurs ont tendance à désactiver tous les caches sur leurs instances de développement. Nous vous recommandons de nettoyer uniquement les caches, sans désactiver tous les caches. [!DNL Commerce] s’exécute plus efficacement lorsque vous [nettoyez les caches](../configuration/cli/manage-cache.md#clean-and-flush-cache-types) au lieu de les désactiver complètement. La plupart des types de caches sont rarement invalidés au cours du développement.

Si vous [désactivez les caches](../configuration/cli/manage-cache.md#enable-or-disable-cache-types), nous vous recommandons de ne désactiver que les caches Page et Bloc dans les instances de développement. N’oubliez pas d’activer tous les caches pendant le test.

## Commandes à éviter en mode développement

En mode de développement, n’exécutez pas de commandes pour la compilation, la génération de code et le déploiement de contenu statique. Ces commandes ont été créées pour une utilisation en mode de production uniquement.

**Ne pas exécuter** commandes d&#39;exploitation en mode développement :

* `setup:di:compile` génère des classes générées automatiquement et des caches de configuration optimisés.

  ```bash
  bin/magento setup:di:compile
  ```

  En mode de développement, Magento effectue la génération à la demande ; il n’est pas nécessaire de l’exécuter. Si vous avez modifié la signature d’une classe et que vous devez générer à nouveau sa `factories/proxies/interceptors` générée automatiquement, supprimez ces classes ou le dossier _généré_.

* `setup:static-content:deploy` déploie du contenu statique pour un magasin.

  ```bash
  bin/magento setup:static-content:deploy
  ```

  En mode de développement, Magento l’exécute à la demande ; vous n’avez pas besoin de l’exécuter.

## Temps normal de chargement des pages sur un ordinateur virtuel

Si vous développez sur une machine virtuelle et que le chargement d’une page Magento prend plus de 2 secondes, vérifiez les paramètres de votre environnement.
