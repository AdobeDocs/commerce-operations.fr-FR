---
title: Création du schéma de la base de données
description: Pour créer une base de données pour votre projet Adobe Commerce, procédez comme suit.
exl-id: 860c9918-44c4-4ef1-88a5-12614566307c
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '49'
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
