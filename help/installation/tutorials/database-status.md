---
title: Vérification du statut de la base de données
description: Pour vérifier l’état de votre base de données Adobe Commerce, procédez comme suit.
exl-id: 33d9b30a-4504-4955-b11a-0a642f23209b
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
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '104'
ht-degree: 3%
---
# Vérification du statut de la base de données

Avant d’exécuter cette commande, vous devez [créer ou mettre à jour la configuration de déploiement](deployment.md).

## Utilisation des commandes

Pour vérifier le statut de la base de données.

```shell
bin/magento setup:db:status
```

Cette commande ne comporte aucun argument ni option.

Voici un exemple de sortie :

```text
All modules are up to date.
```

La commande renvoie l’un des codes de sortie suivants :

| Code de sortie | Description | Action suggérée |
|--------------|--------------|---------------|
| 0 | Normale | Aucune |
| 1 | Certains modules utilisent des versions de code plus récentes ou plus anciennes que la base de données | Exécutez [`magento setup:upgrade`](database-upgrade.md) pour mettre à jour le schéma de base de données et exécutez `composer update` à partir du répertoire racine de l’application pour mettre à jour les dépendances des composants |
| 2 | `magento setup:upgrade` est obligatoire | [`magento setup:upgrade`](database-upgrade.md) de mise à jour du schéma de base de données |
