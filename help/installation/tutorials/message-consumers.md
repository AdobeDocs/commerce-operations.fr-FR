---
title: Configuration des consommateurs de messages
description: Suivez ces étapes pour configurer le comportement des clients de la file d’attente des messages d’Adobe Commerce ou de Magento Open Source.
source-git-commit: 8f05fb6fc212c2b3fda80457bbf27ecf16fb1194
workflow-type: tm+mt
source-wordcount: '69'
ht-degree: 0%

---


# Configuration des consommateurs de messages

Avant d’exécuter cette commande, vous devez effectuer les opérations suivantes : *ou* vous devez [installation de l’application](../advanced.md):

* [Création ou mise à jour de la configuration du déploiement](deployment.md)
* [Création du schéma de la base de données](database.md)

## Configuration du comportement des consommateurs

La configuration du comportement des consommateurs s’effectue en envoyant des paires clé/valeur dans la fonction de configuration :

```bash
bin/magento setup:config:set [--<parameter_name>=<value>, ...]
```

### Descriptions des paramètres

{{$include /help/_includes/cli-consumers.md}}
