---
title: Configuration de Redis
description: Obtenez un aperçu des fonctionnalités Redis et démarrez votre configuration Redis.
feature: Configuration, Cache
exl-id: e037c382-334a-4096-a417-a25fdb61a9ce
source-git-commit: 95ea96a566b0579a22b2ba738bd4a4bceef8cd9c
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 0%

---

# Configuration de Redis

Redis features :

- Stockage des sessions PHP
- Nettoyage du cache basé sur les balises sans boucles `foreach`
- Enregistrement sur disque et réplication maître/esclave

## Installer Redis

L’installation et la configuration du logiciel Redis ne font pas partie de ce guide. Consultez des ressources telles que :

- [Télécharger la page Redis](https://redis.io/download)
- [Démarrage rapide de Redis](https://redis.io/docs/getting-started/)
- [DigitalOcean](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-redis)
- [Redis documentation page](https://redis.io/docs)

## Configuration de Redis

Selon votre installation, vous pouvez généralement trouver votre configuration Redis dans l’un des fichiers suivants : `/etc/redis/redis.conf` ou `/etc/redis/<port>.conf`

Pour optimiser l’instance Redis en fonction de vos besoins, vous obtenez de meilleurs résultats en utilisant une instance dédiée pour chaque session, cache Commerce et FPC.

Pour les sessions, Adobe vous recommande d’activer la persistance pour copier les données Redis sur le disque à l’aide de l’une des options de persistance suivantes : instantanés RDB (Redis Database Backup) standard ou journaux de persistance AOF (Append Only File).

- Les instantanés **Redis Database Backup** (RDB) stockent la base de données complète dans un fichier de sauvegarde après une période donnée, lorsqu’un nombre minimum de clés a changé depuis le dernier enregistrement. Utilisez le paramètre `save` du fichier `redis.conf` pour configurer ce paramètre.

- **Ajouter uniquement le fichier** (AOF) stocke chaque opération d’écriture envoyée à Redis dans un fichier journal. Redis lit ce fichier au redémarrage uniquement et l’utilise pour restaurer le jeu de données d’origine.

Vous pouvez également activer simultanément les options RDB et AOF. Pour plus d’informations, notamment sur les avantages et les inconvénients des options de persistance, consultez la [documentation sur la persistance des segments](https://redis.io/topics/persistence).

Pour l’instance de cache, configurez l’instance de sorte qu’elle soit suffisamment grande pour stocker l’intégralité du cache Commerce. Les exigences de taille dépendent de différents facteurs tels que le nombre de produits et de consultations en magasin. Pour commencer, vous pouvez utiliser la taille du dossier de cache sur votre système de fichiers. Par exemple, si le dossier `var/cache` de votre système de fichiers est de 5 Go, configurez votre instance Redis avec au moins 5 Go pour démarrer. La persistance n’est pas requise pour l’instance de cache, car le cache de Commerce peut être restauré. Voir le [guide de mise en cache des révisions](https://redis.io/docs/latest/develop/use/).

Pour optimiser les performances, vous pouvez activer les paramètres suivants pour la suppression asynchrone. Ces paramètres ne modifient pas le comportement de Redis.

```ini
lazyfree-lazy-eviction yes
lazyfree-lazy-expire yes
lazyfree-lazy-server-del yes
replica-lazy-flush yes
```

Sur Redis 6.x et versions ultérieures, vous pouvez également ajouter la valeur suivante :

```ini
lazyfree-lazy-user-del yes
```
