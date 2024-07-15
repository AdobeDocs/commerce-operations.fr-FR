---
title: Structure de projet du compositeur
description: Découvrez comment configurer et gérer l’option des packages distincts décrite dans les exemples d’architecture de référence globale.
feature: Best Practices
role: Developer
hide: true
hidefromtoc: true
exl-id: 8757d5b8-8309-452f-bfb3-1188a816d14f
source-git-commit: 80cf4dc2b5c9dd690aee1b224fbe6c766fe8f2ab
workflow-type: tm+mt
source-wordcount: '498'
ht-degree: 0%

---

# Structure de projet du compositeur

Ce guide décrit comment configurer et gérer l’ [option de packages distincte](../examples.md#option-1-separate-packages) décrite dans les exemples d’architecture de référence globale (GRA).

## Conditions préalables

Avant de commencer, vérifiez les éléments suivants :

- Vous avez un référentiel Git.
- Vous disposez d’un référentiel de compositeur (cette rubrique met en évidence Private Packagist).
- Vous avez configuré votre référentiel Composer pour qu’il reflète les référentiels `repo.magento.com` et `packagist.org`.

## Référentiel de projet Git principal

Le référentiel de projet Git principal ne doit contenir qu’un projet Composer. Vous pouvez gérer tout le reste avec les packages du compositeur. Le projet principal ne doit jamais contenir d’autres éléments que la structure de fichiers suivante, car le compositeur installe tous les autres packages par le biais de dépendances :

```tree
./
├─ .git/
├─ .gitignore
├─ composer.json
└─ composer.lock
```

Ajoutez le contenu suivant au fichier `.gitignore` :

```tree
/*
!/composer.json
!/composer.lock
```

## Initialisation du projet principal

1. Créez un référentiel Git appelé `project-<region/country/brand>`.

1. Créez les fichiers `composer.json` et `composer.lock` :

   ```bash
   composer create-project --no-install --repository-url=https://repo.magento.com/ magento/project-enterprise-edition project-<region/country/brand>
   cd <install-directory-name>
   printf '/*\n!/composer.json\n!/composer.lock\n!/.gitignore' > .gitignore
   composer config --unset version
   composer config name '<client>/project-<region/country/brand>'
   composer config description '<client> <region/country/brand> main composer project'
   composer config repositories.private-packagist composer https://repo.packagist.com/<client>/
   composer config repositories.packagist.org false
   composer config --unset repositories.0
   composer install
   git init
   git add --all
   git commit -m 'initialize project'
   git remote add origin git@bitbucket.org:<client>/project-<region/country/brand>.git
   git push -u origin master
   ```

## Enregistrer les fichiers non-module

1. Ajoutez le fichier `app/etc/config.xml` au référentiel Git.

   Vous pouvez utiliser le module que vous allez créer pour installer d’autres fichiers de région ou de marque, tels que des fichiers texte d’authentification `.htaccess`, Google ou Bing, des exécutables ou d’autres fichiers statiques qui ne sont pas gérés par les modules Adobe Commerce.

   Utilisez des packages de type `magento2-component` pour créer un mappage de fichiers afin de copier des fichiers dans le référentiel Git principal pendant les opérations `composer install` et `composer update`.

1. Créez un référentiel Git qui suit la convention d’affectation des noms `component-environment-<region/country/brand>` :

   ```bash
   bin/magento module:enable --all
   cd ../
   mkdir component-environment-<region/country/brand>
   cd component-environment-<region/country/brand>
   composer init --no-interaction \
    --name='<client>/component-environment-<region/country/brand>' \
    --description='<client> <region/country/brand> environment files' \
    --type=magento2-component \
    --require="magento/magento-composer-installer:*"
   mkdir -p app/etc
   cp ../project-<region/country/brand>/app/etc/config.php app/etc/
   composer config -e
   ```

1. Ajoutez le fichier `app/etc/config.php` comme mappage dans l’attribut `extra.map` de votre fichier `composer.json` :

   ```json
   {
       "name": "example-client/component-environment-emea",
       "description": "Example client EMEA environment files",
       "type": "magento2-component",
       "require": {
           "magento/magento-composer-installer": "*"
       },
       "extra": {
           "map": [
               [
                   "app/etc/config.php",
                   "app/etc/config.php"
               ]
           ]
       }
   }
   ```

1. Validez votre fichier `composer.json` et validez-le dans le référentiel Git :

   ```bash
   composer validate
   git init
   git add --all
   git commit -m 'initialize component'
   git remote add origin git@bitbucket.org:<client>/component-environment-<region/country/brand>.git
   git push -u origin master
   git tag 0.1.0 -m "0.1.0"
   git push --tags
   ```

## Configuration de métaphores

1. Créez les référentiels Git suivants :

   - `meta-gra`
   - `meta-<region/country/brand>`

1. Configurez l’arborescence de dépendances suivante :

   ```tree
   client/project-<region/country/brand>
   └─ requires -> client/meta-<region/country/brand>
                  ├─ requires -> client/component-environment-<region/country/brand>
                  └─ requires -> client/meta-gra
                                 └─ requires -> magento/product-enterprise-edition
   ```

1. Créez le métappackage GRA :

   ```bash
   cd ..
   mkdir meta-gra
   cd meta-gra
   composer init --no-interaction \
    --name='<client>/meta-gra' \
    --description='<client> GRA meta package' \
    --type=metapackage \
    --require="magento/product-enterprise-edition:<exact.required.version>"
   git init
   git add --all
   git commit -m 'initialize meta package'
   git remote add origin git@bitbucket.org:<client>/meta-gra.git
   git push -u origin master
   git tag 0.1.0 -m "0.1.0"
   git push --tags
   ```

1. Créez le métappackage de marque :

   ```bash
   cd ..
   mkdir meta-<region/country/brand>
   cd meta-<region/country/brand>
   composer init --no-interaction \
    --name='<client>/meta-<region/country/brand>' \
    --description='<client> <region/country/brand> meta package' \
    --type=metapackage \
    --require="<client>/component-environment-<region/country/brand>:~0.1" \
    --require="<client>/meta-gra:~0.1"
   git init
   git add --all
   git commit -m 'initialize meta package'
   git remote add origin git@bitbucket.org:<client>/meta-<region/country/brand>.git
   git push -u origin master
   git tag 0.1.0 -m "0.1.0"
   git push --tags
   ```

1. Requiert la collection par le biais de la gestion des dépendances dans le projet principal :

   ```bash
   cd ../project-<region/country/brand>
   rm app/etc/config.php
   composer remove --no-update magento/product-enterprise-edition
   composer require --no-update "<client>/meta-<region/country/brand>:~0.1"
   composer config minimum-stability alpha
   composer config prefer-stable true
   composer update
   git add --all
   git commit -m 'set up GRA dependency tree'
   git push origin master
   git tag 0.1.0 -m "0.1.0"
   git push --tags
   ```

1. Vérifiez que le compositeur a copié le fichier `app/etc/config.php` à partir de `<client>/component-environment-<region/country/brand>`.

## Déploiement du code

Sur le serveur web, vous pouvez déployer du code à l’aide du compositeur d’expérience, mais vous ne pouvez pas mettre à jour le projet principal. Réinstallez le projet à l’aide du compositeur avec chaque nouveau déploiement, ce qui évite aux serveurs de production et de test d’avoir accès à Git.

## Ajouter d’autres instances et packages

Chaque instance (installation Adobe Commerce unique, de marque ou de région) doit avoir sa propre instance **projet principal**, un **métappackage spécifique** et un **package de composant d’environnement**. Le **métapackage GRA** doit être **partagé** sur toutes les instances.

Les modules fonctionnels (modules, thèmes, modules de langue et bibliothèques Adobe Commerce, par exemple) et les modules tiers doivent être requis par :

- **Métapackage GRA**—Pour une installation sur _toutes{3 instances_
- **métappackage spécifique à l’instance**—Pour une installation sur une seule marque ou une seule région

>[!IMPORTANT]
>
>Ne nécessite pas de packages dans le fichier `composer.json` du projet principal sur les branches `main` ou `release`.

## Préparation au développement

Pour le développement, installez les versions `develop` de tous les modules que vous conservez.

Selon votre stratégie d&#39;embranchement, vous pouvez avoir `develop`, `qa`, `uat` et `main` branches. Chaque branche existe dans le compositeur avec un préfixe `dev-`. La branche `develop` peut donc être requise par le biais du compositeur en tant que version `dev-develop`.

1. Créez `develop` branches dans tous les modules et référentiels de projet.

   ```bash
   cd ../component-environment-<region/country/brand>
   git checkout master
   git checkout -b develop
   git push -u origin develop
   
   
   cd ../meta-<region/country/brand>
   git checkout master
   git checkout -b develop
   
   git push -u origin develop
   
   
   cd ../meta-gra
   git checkout master
   git checkout -b develop
   git push -u origin develop
   
   
   cd ../project-<region/country/brand>
   git checkout master
   git checkout -b develop
   git push -u origin develop
   
   
   composer require \
   "magento-services/meta-fantasy-corp:dev-develop as 0.999" \
   "magento-services/meta-gra:dev-develop as 0.999" \
   "magento-services/component-environment-fantasy-corp:dev-develop as 0.999"
   ```

   L’étape précédente génère les lignes suivantes dans votre fichier `composer.json` :

   ```json
   "require": {
       "magento-services/component-environment-fantasy-corp": "dev-develop as 0.999",
       "magento-services/meta-fantasy-corp": "dev-develop as 0.999",
       "magento-services/meta-gra": "dev-develop as 0.999"
   },
   ```

   >[!IMPORTANT]
   >
   >**Ne fusionnez pas** ces `composer.json` modifications de fichier dans votre branche de production. Installez uniquement les versions stables des packages sur les branches `release` et `main`. Vous pouvez définir ces dépendances pour `qa` branches et d’autres branches non principales.
