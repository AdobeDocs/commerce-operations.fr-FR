---
title: Gestion des modules et des extensions (développeur)
description: Gérez les modules et les extensions Adobe Commerce à l’aide de l’interface de ligne de commande et du gestionnaire de modules du compositeur.
feature: Upgrade, Extensions
exl-id: 447eb317-83e1-4900-83a5-9ac1a008e752
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '135'
ht-degree: 2%

---

# Gestion des modules et des extensions

Contribution des développeurs à la mise à niveau des modules et extensions en spécifiant leurs versions dans Adobe Commerce ou Magento Open Source `composer.json` fichier . Si vous n’êtes pas un développeur contributeur, reportez-vous à la section [Effectuer une mise à niveau](../implementation/perform-upgrade.md).

Vous pouvez ajouter une `require` à la section `composer.json` ou vous pouvez utiliser la variable `composer require` de la façon suivante :

{{$include /help/_includes/server-login.md}}

Vous disposez des options suivantes :

## Obtenir les versions de module disponibles

Utilisation des commandes :

```bash
composer show --all <vendor>/<name>
```

Par exemple :

```bash
composer show --all example/module
```

## Utilisez la variable `composer require` command

Utilisation des commandes :

```bash
composer require <vendor>/<name>:<version>
```

Par exemple :

```bash
composer require example/module:1.0.0
```

Patientez pendant que le compositeur met à jour les dépendances et installe le module.

## Ajouter un `require` au fichier compositeur.json

1. Ouvrez le `composer.json` dans un éditeur de texte.

1. Ajouter un `require` .

   ```json
   "require": {
     "<vendor>/<name>": "<version>",
     "<vendor>/<name>": "<version>"
   }
   ```

1. Enregistrez vos modifications dans le `composer.json` et quittez l’éditeur de texte.

1. Résolvez les dépendances et écrivez des versions exactes dans la variable `composer.lock` fichier .

   ```bash
   composer update
   ```
