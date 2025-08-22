---
title: Gestion des modules et des extensions (développeur)
description: Gérez les modules et les extensions Adobe Commerce à l’aide de l’interface de ligne de commande et du gestionnaire de packages du compositeur.
feature: Upgrade, Extensions
exl-id: 447eb317-83e1-4900-83a5-9ac1a008e752
source-git-commit: 55512521254c49511100a557a4b00cf3ebee0311
workflow-type: tm+mt
source-wordcount: '131'
ht-degree: 3%

---

# Gestion des modules et des extensions

Les développeurs qui contribuent mettent à niveau les modules et les extensions en spécifiant leurs versions dans le fichier `composer.json` d’Adobe Commerce. Si vous n’êtes pas un développeur participant, consultez [Effectuer une mise à niveau](../implementation/perform-upgrade.md).

Vous pouvez ajouter une section `require` au fichier `composer.json` ou utiliser la commande `composer require` comme suit :

{{$include /help/_includes/server-login.md}}

Les options disponibles sont les suivantes :

## Obtenir les versions de module disponibles

Utilisation des commandes :

```bash
composer show --all <vendor>/<name>
```

Par exemple :

```bash
composer show --all example/module
```

## Utiliser la commande `composer require`

Utilisation des commandes :

```bash
composer require <vendor>/<name>:<version>
```

Par exemple :

```bash
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

   ```bash
   composer update
   ```

<!-- Last updated from includes: 2022-09-08 16:00:49 -->
