---
title: Configuration des consommateurs de messages
description: Suivez ces étapes pour configurer le comportement des clients de la file d’attente des messages d’Adobe Commerce ou de Magento Open Source.
exl-id: df292301-f4bd-49df-a241-7467c35bf1d8
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '69'
ht-degree: 0%

---

# Configuration des consommateurs de messages

Avant d’exécuter cette commande, procédez comme suit : *ou* vous devez [installation de l’application](../advanced.md):

* [Création ou mise à jour de la configuration du déploiement](deployment.md)
* [Création du schéma de la base de données](database.md)

## Configuration du comportement des consommateurs

La configuration du comportement des consommateurs s’effectue en envoyant des paires clé/valeur dans la fonction de configuration :

```bash
bin/magento setup:config:set [--<parameter_name>=<value>, ...]
```

### Descriptions des paramètres

{{$include /help/_includes/cli-consumers.md}}
