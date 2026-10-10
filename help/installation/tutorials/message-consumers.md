---
title: Configuration des consommateurs de messages
description: Pour configurer le comportement des consommateurs de files d’attente de messages d’Adobe Commerce, procédez comme suit.
exl-id: df292301-f4bd-49df-a241-7467c35bf1d8
last-update: 2026-04-28
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: a3c0eba7bdcd8017e88bdb4df1f45d77fe4bb351
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
