---
title: Configuration des consommateurs de messages
description: Pour configurer le comportement des consommateurs de files d’attente de messages d’Adobe Commerce, procédez comme suit.
exl-id: df292301-f4bd-49df-a241-7467c35bf1d8
last-update: 2026-04-28T00:00:00Z
source-git-commit: 1166b8fbfeef21a51ad6e4e695aed2b25006230e
workflow-type: tm+mt
source-wordcount: '65'
ht-degree: 0%

---

# Configuration des consommateurs de messages

Avant d’exécuter cette commande, vous devez effectuer les opérations suivantes *ou* vous devez [installer l’application](../advanced.md) :

* [Créer ou mettre à jour la configuration de déploiement](deployment.md)
* [Création du schéma de base de données](database.md)

## Configuration du comportement des consommateurs

La configuration du comportement des consommateurs s’effectue en envoyant des paires clé/valeur dans la fonction de configuration :

```shell
bin/magento setup:config:set [--<parameter_name>=<value>, ...]
```

### Descriptions des paramètres

{{$include /help/_includes/cli-consumers.md}}

<!-- Last updated from includes: 2022-09-12 09:38:25 -->
