---
title: Création du schéma de la base de données
description: Pour créer une base de données pour Adobe Commerce ou Magento Open Source, procédez comme suit.
source-git-commit: f6f438b17478505536351fa20a051d355f5b157a
workflow-type: tm+mt
source-wordcount: '52'
ht-degree: 0%

---


# Création du schéma de la base de données

Avant d’exécuter cette commande, vous devez [Création ou mise à jour de la configuration du déploiement](deployment.md).

## Configurer la base de données et ajouter des données

Utilisation des commandes :

```bash
bin/magento setup:db-schema:upgrade
```

Pour connaître le statut de la base de données, saisissez

```bash
bin/magento setup:db:status
```
