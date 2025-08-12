---
title: Configurer Valkey
description: Obtenez un aperçu des fonctionnalités de Valkey et commencez votre configuration de Valkey.
feature: Configuration, Cache
exl-id: 12dbc171-3df6-4413-869b-a3450b5647b4
source-git-commit: b2cf71bfda3e5db8e27eb28d764cf99216454e33
workflow-type: tm+mt
source-wordcount: '341'
ht-degree: 0%

---

# Configurer Valkey

Les fonctionnalités de Valkey incluent :

- Stockage de session PHP
- Nettoyage du cache basé sur les balises sans boucles `foreach`
- Enregistrements sur le disque et réplication maître/esclave

## Installer Valkey

Pour installer et configurer le logiciel Valkey, consultez les ressources suivantes :

- [Télécharger la page Valkey](https://valkey.io/download/)
- [Démarrage rapide de Valkey](https://valkey.io/topics/quickstart/)
- [Page de documentation Valkey](https://valkey.io/docs)

## Configuration de Valkey

Selon votre installation, vous trouverez généralement votre configuration Valkey dans le fichier `/etc/valkey/valkey.conf` ou dans le fichier `/etc/valkey/<port>.conf`.

Pour optimiser l’instance Valkey en fonction de vos besoins, vous pouvez obtenir les meilleurs résultats en utilisant une instance dédiée pour chaque session, le cache de Commerce et FPC.

Adobe recommande d’activer la persistance pour les sessions afin de copier les données Valkey sur le disque. Vous pouvez utiliser des instantanés de sauvegarde de base de données Valkey (RDB) ou des journaux de persistance Append Only File (AOF).

- Les instantanés **RDB** (Valkey Database) stockent la base de données complète dans un fichier de vidage après un temps donné, lorsqu&#39;un nombre minimum de clés a changé depuis le dernier enregistrement. Utilisez le paramètre `save` dans le fichier `valkey.conf` pour configurer ce paramètre.

- **Append Only File** (AOF) stocke chaque opération d’écriture envoyée à Valkey dans un fichier journal. Valkey lit ce fichier au redémarrage uniquement et l’utilise pour restaurer le jeu de données d’origine.

Vous pouvez également activer simultanément les options RDB et AOF. Pour plus d’informations, y compris les avantages et les inconvénients des options de persistance, consultez la [documentation sur la persistance de Valkey](https://valkey.io/topics/persistence/).

Pour l’instance de cache, configurez-la de sorte qu’elle soit suffisamment grande pour stocker l’intégralité de votre cache Commerce. Les exigences de taille dépendent de différents facteurs, tels que le nombre de produits et de vues de magasin. Pour commencer, vous pouvez utiliser la taille du dossier de cache sur votre système de fichiers. Par exemple, si le dossier `var/cache` de votre système de fichiers fait 5 Go, configurez votre instance Valkey avec au moins 5 Go pour démarrer. La persistance n’est pas requise pour l’instance de cache, car le cache de Commerce peut être restauré.

Pour l’optimisation des performances, vous pouvez activer les paramètres suivants pour la suppression asynchrone. Ces paramètres ne modifient pas le comportement de Valkey.

```ini
lazyfree-lazy-eviction yes
lazyfree-lazy-expire yes
lazyfree-lazy-server-del yes
replica-lazy-flush yes
lazyfree-lazy-user-del yes
```
