---
title: Configuration des consommateurs de messages
description: Suivez ces étapes pour configurer le comportement des consommateurs de la file d’attente de messages Adobe Commerce.
exl-id: df292301-f4bd-49df-a241-7467c35bf1d8
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '65'
ht-degree: 0%

---

# Configuration des consommateurs de messages

Avant d&#39;exécuter cette commande, vous devez effectuer les *ou* suivants en [installant l&#39;application](../advanced.md) :

* [Création ou mise à jour de la configuration du déploiement](deployment.md)
* [Création du schéma de la base de données](database.md)

## Configuration du comportement des consommateurs

La configuration du comportement des consommateurs s’effectue en envoyant des paires clé/valeur dans la fonction de configuration :

```bash
bin/magento setup:config:set [--<parameter_name>=<value>, ...]
```

### Descriptions des paramètres

{{$include /help/_includes/cli-consumers.md}}
