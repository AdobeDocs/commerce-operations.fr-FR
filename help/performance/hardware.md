---
title: Recommendations matériel
description: Consultez la liste du matériel recommandé pour optimiser les performances des déploiements Adobe Commerce.
feature: Best Practices, Install
exl-id: ab548c4b-6f56-4409-a4ed-5c959939e04b
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '466'
ht-degree: 0%

---

# Recommandations matérielles

## CPU

[!DNL Commerce] les noeuds web diffusent toutes les requêtes qui ne sont pas mises en cache ou qui ne peuvent pas l’être par le biais de l’application. Un noyau de processeur peut servir autour de deux (parfois jusqu’à quatre) [!DNL Commerce] demande de manière efficace. Utilisez l’équation suivante pour déterminer le nombre de noeuds/coeurs web dont vous avez besoin pour traiter toutes les requêtes entrantes sans les mettre en file d’attente :

```
N[Cores] = (N[Expected Requests] / 2) + N [Expected Cron Processes]
```

Si vous prévoyez une modification de la charge d’un magasin, vous pouvez augmenter manuellement le nombre de noeuds/coeurs web pour une période de vente active. Vous pouvez également utiliser un modèle de mise à l’échelle automatique pour étendre automatiquement les niveaux web.

## Mémoire

### PHP

Magento a des exigences de mémoire PHP différentes, en fonction de la manière dont votre système est déployé.  En règle générale, si vous configurez un seul magasin de serveurs, nous vous recommandons de configurer la mémoire PHP pour 2G.  Si vous configurez un site à l’aide du déploiement du pipeline, il est recommandé d’utiliser 2 Go sur votre serveur de génération et 1 Go sur vos noeuds web.

Scénarios et exigences de mémoire PHP attendues :

* Noeud web ne diffusant que les pages de storefront : 256 Mo
* Noeud web servant les pages d’administration avec un catalogue volumineux : 1 Go
* [!DNL Commerce] indexation cron d’un site avec un catalogue volumineux : >256 Mo (voir [advanced-setup](../performance/advanced-setup.md) pour optimiser les performances.)
* [!DNL Commerce] compilation et déploiement de ressources statiques : 756 Mo
* [!DNL Commerce] génération de profils de boîte à outils de performance : >1 Go de RAM PHP, >16 Mo [!DNL MySQL] Paramètres TMP_TABLE_SIZE et MAX_HEAP_TABLE_SIZE

### [!DNL MySQL]

La variable [!DNL Commerce] La base de données (ainsi que toute autre base de données) est sensible à la quantité de mémoire disponible pour le stockage des données et des index. Pour tirer pleinement parti des [!DNL MySQL] indexation des données, la quantité de mémoire disponible doit être, au minimum, proche de la moitié de la taille des données stockées dans la base de données.

### Caches

Si vous déployez plusieurs [!DNL Commerce] et en utilisant Redis ou [!DNL Varnish] pour vos caches, veuillez tenir compte des principes suivants :

* [!DNL Varnish] l’invalidation de la mémoire cache de la page entière est effective, il est recommandé d’allouer suffisamment de mémoire [!DNL Varnish] pour conserver vos pages les plus populaires en mémoire
* Le cache de session est un bon candidat à configurer pour une instance distincte de Redis.  La configuration de la mémoire pour ce type de cache doit tenir compte de la stratégie d’abandon de panier du site et de la durée pendant laquelle une session doit rester dans le cache.
* La mémoire des redis doit être suffisante pour contenir tous les autres caches en mémoire pour des performances optimales.  Le cache des blocs sera le facteur clé pour déterminer la quantité de mémoire à configurer.  Le cache des blocs augmente par rapport au nombre de pages sur un site (nombre de SKU x nombre de vues de magasin).

## Bande passante réseau

Une bande passante réseau suffisante est l’une des principales exigences pour l’exchange des données entre les noeuds web, les bases de données, les serveurs de mise en cache/session et d’autres services. Parce que [!DNL Commerce] exploite efficacement la mise en cache pour des performances élevées, votre système peut exchange activement des données avec des serveurs de mise en cache tels que Redis. Si Redis se trouve sur un serveur distant, vous devez fournir un canal réseau suffisant entre les noeuds web et le serveur de mise en cache pour éviter les goulets d’étranglement lors des opérations de lecture/écriture.
