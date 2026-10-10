---
title: Gestion des modules et des extensions (développeur)
description: Gérez les modules et les extensions Adobe Commerce à l’aide de l’interface de ligne de commande et du gestionnaire de packages du compositeur.
feature: Upgrade, Extensions
exl-id: 447eb317-83e1-4900-83a5-9ac1a008e752
last-update: 2026-04-28
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: a8ae7a5a-6cdc-5922-bd0d-6feb44b04984
    internal-label: Upgrade
  - id: f08fa0de-a550-4acd-b570-f81cf1d03aaf
    internal-label: Commerce ecosystem
subfeature_v2:
  - id: dad884f1-e840-49a1-970e-2f965bdbc410
    internal-label: Extensions
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
source-wordcount: '132'
ht-degree: 3%
---
# Gestion des modules et des extensions

Les développeurs qui contribuent mettent à niveau les modules et les extensions en spécifiant leurs versions dans le fichier `composer.json` d’Adobe Commerce. Si vous n’êtes pas un développeur participant, consultez [Effectuer une mise à niveau](../implementation/perform-upgrade.md).

Vous pouvez ajouter une section `require` au fichier `composer.json` ou utiliser la commande `composer require` comme suit :

{{$include /help/_includes/server-login.md}}

Les options disponibles sont les suivantes :

## Obtenir les versions de module disponibles

Utilisation des commandes :

```shell
composer show --all <vendor>/<name>
```

Par exemple :

```shell
composer show --all example/module
```

## Utiliser la commande `composer require`

Utilisation des commandes :

```shell
composer require <vendor>/<name>:<version>
```

Par exemple :

```shell
composer require example/module:1.0.0
```

Patientez pendant que le compositeur met à jour les dépendances et installe le module .

## Ajoutez une section `require` au fichier composer.json

1. Ouvrez le `composer.json` dans un éditeur de texte.

1. Ajoutez une section `require` .

   ```json
   "require": {
     "<vendor>/<name>": "<version>",
     "<vendor>/<name>": "<version>"
   }
   ```

1. Enregistrez vos modifications dans le fichier `composer.json` et quittez l’éditeur de texte.

1. Résolvez les dépendances et écrivez les versions exactes dans le fichier `composer.lock`.

   ```shell
   composer update
   ```

<!-- Last updated from includes: 2026-04-17 13:49:36 -->
