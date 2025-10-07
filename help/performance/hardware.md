---
title: Recommandations matérielles
description: Découvrez les recommandations matérielles pour des performances optimales d’Adobe Commerce. Découvrez les exigences en matière de CPU, de mémoire et de stockage pour les déploiements en production.
feature: Best Practices, Install
exl-id: ab548c4b-6f56-4409-a4ed-5c959939e04b
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '470'
ht-degree: 0%

---

# Recommandations matérielles

## UC

[!DNL Commerce] nœuds web diffusent toutes les requêtes qui ne sont pas mises en cache ou qui ne peuvent pas l’être via l’application. Un cœur de CPU peut répondre efficacement à environ deux requêtes [!DNL Commerce] (parfois jusqu’à quatre). Utilisez l’équation suivante pour déterminer le nombre de nœuds/cœurs web dont vous avez besoin pour traiter toutes les requêtes entrantes sans les mettre en file d’attente :

```
N[Cores] = (N[Expected Requests] / 2) + N [Expected Cron Processes]
```

Si vous prévoyez une modification de la charge d’un magasin, vous pouvez augmenter manuellement le nombre de nœuds/cœurs web pour une période de vente active. Vous pouvez également utiliser un modèle de mise à l’échelle automatique pour étendre automatiquement les niveaux web.

## Mémoire

### PHP

Magento a différentes exigences en matière de mémoire PHP, selon la manière dont votre système est déployé.  En général, si vous configurez un seul magasin de serveur, nous vous recommandons de configurer la mémoire PHP pour la 2G.  Si vous configurez un site à l’aide du déploiement de pipeline, nous vous recommandons de disposer de 2 Go sur votre serveur de build et de 1 Go sur vos nœuds web.

Scénarios et besoins attendus en mémoire PHP :

* Webnode desservant uniquement les pages de storefront : 256 Mo
* Webnode desservant les pages d’administration avec un catalogue volumineux : 1 Go
* [!DNL Commerce] l’indexation cron d’un site avec un catalogue volumineux : > 256 Mo (voir [configuration-avancée](../performance/advanced-setup.md) pour optimiser les performances).
* [!DNL Commerce] la compilation et le déploiement des ressources statiques : 756 Mo
* Génération de profil [!DNL Commerce] performance toolkit : >1 Go de RAM PHP, >16 Mo [!DNL MySQL] paramètres TMP_TABLE_SIZE et MAX_HEAP_TABLE_SIZE

### [!DNL MySQL]

La base de données [!DNL Commerce] (ainsi que toute autre base de données) est sensible à la quantité de mémoire disponible pour stocker des données et des index. Pour tirer pleinement parti de [!DNL MySQL]&#39;indexation des données, la quantité de mémoire disponible doit être au minimum égale à près de la moitié de la taille des données stockées dans la base de données.

### Caches

Si vous déployez plusieurs [!DNL Commerce] et utilisez Redis ou [!DNL Varnish] pour vos caches, tenez compte des principes suivants :

* [!DNL Varnish] l’invalidation de la mémoire cache de toutes les pages est efficace, nous vous recommandons d’allouer suffisamment de mémoire à [!DNL Varnish] pour stocker vos pages les plus populaires en mémoire
* Le cache de session est un bon candidat à configurer pour une instance distincte de Redis.  La configuration de la mémoire pour ce type de cache doit tenir compte de la stratégie d’abandon de panier du site et de la durée probable de conservation d’une session dans le cache
* La mémoire allouée à Redis doit être suffisante pour contenir tous les autres caches en mémoire pour des performances optimales.  Le cache de bloc sera le facteur clé dans la détermination de la quantité de mémoire à configurer.  Le cache de blocs augmente par rapport au nombre de pages sur un site (nombre de sku x nombre de vues de magasin)

## Bande passante réseau

Une bande passante réseau suffisante est l’une des principales exigences pour l’échange de données entre les nœuds web, les bases de données, la mise en cache/les serveurs de session et d’autres services. Parce que [!DNL Commerce] utilise efficacement la mise en cache pour des performances élevées, votre système peut échanger activement des données avec des serveurs de mise en cache tels que Redis. Si Redis se trouve sur un serveur distant, vous devez fournir un canal réseau suffisant entre les nœuds web et le serveur de mise en cache pour éviter les goulets d’étranglement lors des opérations de lecture/écriture.
