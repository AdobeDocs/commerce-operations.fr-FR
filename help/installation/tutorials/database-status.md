---
title: Vérification du statut de la base de données
description: Pour vérifier l’état de votre base de données Adobe Commerce ou Magento Open Source, procédez comme suit.
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '108'
ht-degree: 2%

---


# Vérification du statut de la base de données

Avant d’exécuter cette commande, vous devez [Création ou mise à jour de la configuration du déploiement](deployment.md).

## Utilisation des commandes

Pour vérifier le statut de la base de données.

```bash
bin/magento setup:db:status
```

Cette commande ne comporte aucun argument ou option.

Voici un exemple de résultat :

```terminal
All modules are up to date.
```

La commande renvoie l’un des codes de sortie suivants :

| Code de sortie | Description | Action suggérée |
|--------------|--------------|---------------|
| 0 | Normal | Aucun |
| 1 | Certains modules utilisent des versions de code plus récentes ou plus anciennes que la base de données. | Exécuter [`magento setup:upgrade`](database-upgrade.md) pour mettre à jour le schéma de la base de données et exécuter `composer update` à partir du répertoire racine de l’application pour mettre à jour les dépendances des composants. |
| 2 | `magento setup:upgrade` est requis | [`magento setup:upgrade`](database-upgrade.md) mise à jour du schéma de base de données |
