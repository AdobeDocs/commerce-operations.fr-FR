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

Ce guide décrit comment configurer et gérer la variable [option packages séparés](../examples.md#option-1-separate-packages) décrits dans les exemples d’architecture de référence globale (GRA).

## Conditions préalables

Avant de commencer, vérifiez les éléments suivants :

- Vous avez un référentiel Git.
- Vous disposez d’un référentiel de compositeur (cette rubrique met en évidence Private Packagist).
- Vous avez configuré votre référentiel de compositeur pour qu’il reflète la variable `repo.magento.com` et `packagist.org` référentiels

## Référentiel de projet Git principal

Le référentiel de projet Git principal ne doit contenir qu’un projet Composer. Vous pouvez gérer tout le reste avec les packages du compositeur. Le projet principal ne doit jamais contenir d’autres éléments que la structure de fichiers suivante, car le compositeur installe tous les autres packages par le biais de dépendances :

```tree
./
├─ .git/
├─ .gitignore
├─ composer.json
└─ composer.lock
```

Ajoutez le contenu suivant au `.gitignore` fichier :

```tree
/*
!/composer.json
!/composer.lock
```

## Initialisation du projet principal

1. Créez un référentiel Git appelé `project-<region/country/brand>`.

1. Créer `composer.json` et `composer.lock` files :

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

1. Ajoutez la variable `app/etc/config.xml` vers le référentiel Git.

   Vous pouvez utiliser le module que vous allez créer pour installer d’autres fichiers de région ou de marque, tels que `.htaccess`, fichiers texte d’authentification Google ou Bing, exécutables ou autres fichiers statiques qui ne sont pas gérés par les modules Adobe Commerce.

   Utilisation `magento2-component` des packages de type pour créer un mappage de fichiers afin de copier des fichiers dans le référentiel Git principal pendant la `composer install` et `composer update` opérations.

1. Création d’un référentiel Git conforme à la convention d’affectation des noms `component-environment-<region/country/brand>`:

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

1. Ajoutez la variable `app/etc/config.php` comme mappage dans la variable `extra.map` de votre `composer.json` fichier :

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

1. Validez votre `composer.json` et validez-la dans le référentiel Git :

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

1. Vérifiez que le compositeur a copié le `app/etc/config.php` fichier à partir de `<client>/component-environment-<region/country/brand>`.

## Déploiement du code

Sur le serveur web, vous pouvez déployer du code à l’aide du compositeur d’expérience, mais vous ne pouvez pas mettre à jour le projet principal. Réinstallez le projet à l’aide du compositeur avec chaque nouveau déploiement, ce qui évite aux serveurs de production et de test d’avoir accès à Git.

## Ajouter d’autres instances et packages

Chaque instance (région, marque ou autre installation Adobe Commerce unique) doit avoir sa propre **projet principal** instance, **métaphorage spécifique**, et **package du composant d’environnement**. La variable **Métappackage GRA** should **shared** sur toutes les instances.

Les modules fonctionnels (modules, thèmes, modules de langue et bibliothèques Adobe Commerce, par exemple) et les modules tiers doivent être requis par :

- **Métappackage GRA**—Pour l’installation sur _all_ instances
- **métaphorage spécifique à une instance**: installation sur une seule marque ou région

>[!IMPORTANT]
>
>Ne nécessite pas de modules dans le fichier du projet principal `composer.json` sur le `main` ou `release` branches.

## Préparation au développement

Pour le développement, installez . `develop` versions de tous les modules que vous conservez.

Selon votre stratégie d’embranchement, vous pouvez avoir `develop`, `qa`, `uat`, et `main` branches. Chaque branche existe dans le compositeur avec une `dev-` préfixe. Ainsi, la variable `develop` la branche peut être requise par le biais du compositeur en tant que version `dev-develop`.

1. Créer `develop` branches dans tous les modules et référentiels de projet.

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

   L’étape précédente génère les lignes suivantes dans votre `composer.json` fichier :

   ```json
   "require": {
       "magento-services/component-environment-fantasy-corp": "dev-develop as 0.999",
       "magento-services/meta-fantasy-corp": "dev-develop as 0.999",
       "magento-services/meta-gra": "dev-develop as 0.999"
   },
   ```

   >[!IMPORTANT]
   >
   >**Ne pas fusionner** these `composer.json` modifications apportées à votre branche de production. Installer uniquement les versions stables des modules sur `release` et `main` branches. Vous pouvez définir ces dépendances pour `qa` branches et autres branches non principales.
