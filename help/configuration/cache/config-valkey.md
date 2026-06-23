---
title: Installation et configuration de Valkey
description: Découvrez comment installer et configurer Valkey pour la mise en cache et le stockage de session avec Adobe Commerce. Découvrez les options d’optimisation et d’optimisation des performances.
feature: Configuration, Cache
exl-id: 12dbc171-3df6-4413-869b-a3450b5647b4
badgePaas: label="Sur Site" type="Informative" url="https://experienceleague.adobe.com/fr/docs/commerce/user-guides/product-solutions" tooltip="S’applique uniquement aux projets sur site Adobe Commerce."
TQID: 'https://experienceleague.adobe.com/Ef4WREy0eq0ChsrI5-0FtrjMZWNjwr7l71Pm-RHD1GI'
product_v2:
  - id: b974b164-8a4e-43b8-a9e2-8e67ec131677
  - id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
source-git-commit: ab2a9ef6d4c3ed692f4a6a66323ab5e3d5c6673a
workflow-type: tm+mt
source-wordcount: 414
ht-degree: 0%

---

# Installation et configuration de Valkey

Valkey est un magasin de données en mémoire open source compatible avec Redis qui peut être utilisé comme serveur principal de cache et pour le stockage de session. Les principales fonctionnalités sont les suivantes :

- Stockage de session PHP
- Nettoyage du cache basé sur les balises sans boucles `foreach`
- Enregistrements sur le disque et réplication maître/esclave

{{cloud-cache-config}}

## Installer Valkey

Pour installer et configurer le logiciel Valkey, consultez les ressources suivantes :

- [Page Télécharger la clé](https://valkey.io/download/){target="_blank"}
- [Démarrage rapide de Valkey](https://valkey.io/topics/quickstart/){target="_blank"}
- [Page de documentation Valkey](https://valkey.io/docs){target="_blank"}

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
