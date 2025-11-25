---
title: Configurer Redis
description: Découvrez comment configurer la mise en cache Redis pour l’optimisation des performances d’Adobe Commerce. Découvrez les fonctionnalités, les étapes de configuration et les bonnes pratiques de configuration.
feature: Configuration, Cache
exl-id: e037c382-334a-4096-a417-a25fdb61a9ce
source-git-commit: 84a20012a81278cc95587ec14281b05330261687
workflow-type: tm+mt
source-wordcount: '380'
ht-degree: 0%

---

# Configurer Redis

Les fonctionnalités Redis incluent :

- Stockage de session PHP
- Nettoyage du cache basé sur les balises sans boucles `foreach`
- Enregistrements sur le disque et réplication maître/esclave

## Installer Redis

L&#39;installation et la configuration du logiciel Redis ne font pas partie de ce guide. Consultez des ressources telles que :

- [Télécharger la page Redis](https://redis.io/download)
- [ Démarrage rapide Redis ](https://redis.io/docs/latest/)
- [DigitalOcean](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-redis)
- [page de documentation Redis](https://redis.io/docs)

## Paramétrer la configuration Redis

Selon votre installation, vous pouvez généralement trouver votre configuration Redis dans l’un des fichiers suivants : `/etc/redis/redis.conf` ou `/etc/redis/<port>.conf`

Pour optimiser l’instance Redis en fonction de vos besoins, vous obtenez de meilleurs résultats en utilisant une instance dédiée pour chaque session, le cache Commerce et FPC.

Pour les sessions, Adobe vous recommande d’activer la persistance pour copier les données Redis sur le disque à l’aide de l’une des options de persistance suivantes : instantanés Redis Database Backup (RDB) standard ou journaux de persistance Ajout de fichier uniquement (AOF).

- Les instantanés **Redis Database Backup** (RDB) stockent la base de données complète dans un fichier de vidage après un temps donné, lorsqu&#39;un nombre minimum de clés a changé depuis le dernier enregistrement. Utilisez le paramètre `save` dans le fichier `redis.conf` pour configurer ce paramètre.

- **Append Only File** (AOF) stocke chaque opération d’écriture envoyée à Redis dans un fichier journal. Redis lit ce fichier au redémarrage uniquement et l’utilise pour restaurer le jeu de données d’origine.

Vous pouvez également activer simultanément les options RDB et AOF. Pour plus d’informations, y compris les avantages et les inconvénients des options de persistance, consultez la [documentation sur la persistance Redis](https://redis.io/topics/persistence).

Pour l’instance de cache, configurez-la de sorte qu’elle soit suffisamment grande pour stocker l’intégralité de votre cache Commerce. Les exigences de taille dépendent de différents facteurs, tels que le nombre de produits et de vues de magasin. Pour commencer, vous pouvez utiliser la taille du dossier de cache sur votre système de fichiers. Par exemple, si le dossier `var/cache` de votre système de fichiers fait 5 Go, configurez votre instance Redis avec au moins 5 Go pour démarrer. La persistance n’est pas requise pour l’instance de cache, car le cache de Commerce peut être restauré. Voir [Guide du cache Redis](https://redis.io/docs/latest/develop/use/).

Pour l’optimisation des performances, vous pouvez activer les paramètres suivants pour la suppression asynchrone. Ces paramètres ne modifient pas le comportement de Redis.

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
