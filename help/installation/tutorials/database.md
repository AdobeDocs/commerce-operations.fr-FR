---
title: Création du schéma de base de données
description: Pour créer une base de données pour votre projet Adobe Commerce, procédez comme suit.
exl-id: 860c9918-44c4-4ef1-88a5-12614566307c
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '49'
ht-degree: 0%

---

# Création du schéma de base de données

Avant d’exécuter cette commande, vous devez [créer ou mettre à jour la configuration de déploiement](deployment.md).

## Configuration de la base de données et ajout de données

Utilisation des commandes :

```bash
bin/magento setup:db-schema:upgrade
```

Pour afficher l&#39;état de la base de données, saisissez

```bash
bin/magento setup:db:status
```
