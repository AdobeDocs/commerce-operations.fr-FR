---
title: Exemples d’architecture de référence globale
description: Consultez des exemples de gestion du code pour les projets Adobe Commerce de grande envergure.
role: Developer, Architect
level: Experienced
hide: true
hidefromtoc: true
exl-id: 2a85b9bf-e547-4a2a-9234-210865f55609
source-git-commit: 80cf4dc2b5c9dd690aee1b224fbe6c766fe8f2ab
workflow-type: tm+mt
source-wordcount: '816'
ht-degree: 0%

---

# Exemples d’architecture de référence globale

Cette rubrique décrit les méthodes courantes d’organisation d’une [architecture de référence globale (GRA)](overview.md) base de code. Bien que la variable [packages distincts](#option-1-separate-packages) est préférable, certaines situations nécessitent l’une des autres options décrites ci-dessous.

## Définitions

{{$include /help/_includes/gra-definitions.md}}

## Option 1 : packages distincts

Voir [Structure de projet du compositeur](composer/project-structure.md) bonnes pratiques pour configurer cette méthode.

![Diagramme illustrant l’option de packages distincts pour l’architecture de référence globale](../../../assets/playbooks/gra-separate-packages.png)

La méthode la plus souple pour gérer les modules du compositeur d’expérience visuelle passe par les métaphores. Les métaphores contiennent un `composer.json` uniquement, qui définit d’autres dépendances de package. Créer des métaphores à l’aide de [Packagiste privé](https://packagist.com/) référentiels.

### Projet principal `composer.json`

```json
{
    "name": "example-client/region-1",
    "description": "Example Client Region 1",
    "type": "project",
    "require": {
        "magento/product-enterprise-edition": "2.3.5",
        "example-client/meta-region-1": "~1.0"
    },
    "minimum-stability": "dev",
    "prefer-stable": true,
    "repositories": [
        {"type": "composer", "url": "https://repo.packagist.com/example-client/"},
        {"packagist.org": false}
    ]
}
```

### `example-client/meta-region-1 composer.json`

```json
{
    "name": "example-client/meta-region-1",
    "description": "Region 1 meta package",
    "type": "metapackage",
    "require": {
        "example-client/meta-gra": "~1.0",
        "example-client/theme-frontend-region1",
        "example-client/language-es-es",
        "ingenico/ogone-client"
    }
}
```

### `example-client/meta-gra composer.json`

```json
{
    "name": "example-client/meta-gra",
    "description": "GRA meta package",
    "type": "metapackage",
    "require": {
        "geoip2/geoip2": "~2.0",
        "magento-services/module-stackify-logger": "~1.1",
        "example-client/sap-connector",
        "example-client/service-chat",
        "example-client/store-locator"
    }
}
```

Chaque module, module de langue, thème et bibliothèque possède son propre référentiel Git. Chaque référentiel Git se synchronise automatiquement avec le référentiel Packagist privé et y génère un module tant qu’il y a une `composer.json` dans la racine du référentiel Git.

## Options 2 : packages en bloc

Vous trouverez ci-dessous un exemple de plusieurs modules dans un seul module de compositeur.

Un module en bloc ne peut inclure que des modules du même type. Par exemple, si vous disposez de plusieurs modules pour les modules, thèmes, modules de langue et bibliothèques Adobe Commerce, vous devez créer des modules en bloc distincts pour chaque type.

La structure de fichiers dans le répertoire du fournisseur doit ressembler à l’exemple suivant. Toutefois, vérifiez votre projet (pour savoir ce qui doit être inclus dans votre référentiel Git) :

```tree
.
└── example-client/
    └── gra/
        └── src/
            ├── SapConnector/
            │   ├── etc/
            │   └── registration.php
            ├── ServiceChat/
            │   ├── etc/
            │   └── registration.php
            ├── StoreLocator/
            │   ├── etc/
            │   └── registration.php
            └── composer.json
```

La variable `composer.json` doit ressembler à ceci :

```json
{
    "name": "example-client/gra",
    "description": "GRA Modules",
    "require": {
        "magento/magento-composer-installer": "*"
    },
    "type": "magento2-module",
    "autoload": {
        "files": [
            "src/SapConnector/registration.php",
            "src/ServiceChat/registration.php",
            "src/StoreLocator/registration.php"
        ],
        "psr-4": {
            "ExampleClient\\SapConnector\\": "src/SapConnector",
            "ExampleClient\\ServiceChat\\": "src/ServiceChat",
            "ExampleClient\\StoreLocator\\": "src/StoreLocator"
        }
    }
}
```

## Option 3 : Fractionner Git

Cette architecture utilise quatre référentiels Git pour stocker du code :

- `core`: contient l’installation principale d’Adobe Commerce. est utilisé pour mettre à niveau les versions d’Adobe Commerce.
- `GRA`: contient le code GRA. Tous les modules GRA, modules de langue, thèmes de libellé blanc et bibliothèques.
- `brand/region`: chaque marque ou région possède son propre référentiel avec uniquement du code spécifique à la marque ou à la région.
- `release`: tous les éléments ci-dessus sont fusionnés dans ce référentiel Git. Seules les validations de fusion sont autorisées ici.

![Diagramme illustrant l’option split Git pour l’architecture de référence globale](../../../assets/playbooks/gra-split-git.png)

Pour configurer cette option :

1. Créez les quatre types de référentiel dans Git. Créez le `core` et `GRA` référentiels une seule fois. En créer un `brand/region` et un `release` pour chaque marque.

   Noms de référentiel suggérés :

   - `m2-core`
   - `m2-gra`
   - `m2-region-x`/`m2-brand-x` (par exemple, `m2-emea`/`m2-adobe`)
   - `m2-release-region-x`/`m2-release-brand-x` (par exemple, `m2-release-emea`/`m2-release-adobe`)

1. Créez un `release/` et exécutez le suivant pour créer un historique Git partagé pour tous les référentiels.

   ```bash
   git init
   git remote add origin git@github.com:example-client/m2-release-brand-x.git
   git remote add core git@github.com:example-client/m2-core.git
   git remote add gra git@github.com:example-client/m2-gra.git
   git remote add region-x git@github.com:example-client/m2-region-x.git
   touch .gitkeep
   git add .gitkeep
   git commit -m 'initialize repository'
   git push -u origin master
   git push core master
   git push gra master
   git push region-x master
   ```

1. Cloner chaque référentiel, sauf `core`, dans un autre répertoire de votre ordinateur.

   ```bash
   git clone git@github.com:example-client/m2-release-brand-x.git
   git clone git@github.com:example-client/m2-region-x.git
   git clone git@github.com:example-client/m2-gra.git
   ```

1. [Installation d’Adobe Commerce avec le compositeur](../../../installation/composer.md). Supprimez le `.gitignore` , ajoutez le fichier `core` à distance, ajoutez et validez le code, puis envoyez une notification push.

   ```bash
   composer create-project --repository-url=https://repo.magento.com/ magento/project-enterprise-edition m2-core
   cd m2-core
   git init
   rm .gitignore
   git remote add origin git@github.com:example-client/m2-core.git
   git fetch
   git checkout .gitkeep
   git add --all
   git commit -m 'install Adobe Commerce'
   git push
   ```

1. Dans le `GRA` , créez les répertoires suivants :

   - `app/code/`
   - `app/design/`
   - `app/i18n/`
   - `lib/`

1. Ajoutez du code. Supprimez le `.gitignore` , ajoutez et validez le code, ajoutez la télécommande et push.

1. Dans le `brand/region` référentiel. Faites de même que dans `GRA` et gardez à l’esprit que les fichiers doivent être uniques. Vous ne pouvez pas inclure le même fichier dans ce référentiel et dans la variable `GRA` référentiel.

1. Dans le `release` , appliquez la fusion.

   ```bash
   git clone git@github.com:example-client/m2-release-brand-x.git
   cd m2-release-brand-x
   git remote add core git@github.com:example-client/m2-core.git
   git remote add gra git@github.com:example-client/m2-gra.git
   git remote add region-x git@github.com:example-client/m2-region-x.git
   git fetch --all
   git merge core/master gra/master brand-a/master
   git push
   ```

1. Supprimez le `.gitkeep` fichier .

1. Déployez la variable `release` vers les serveurs de production, de test, d’assurance qualité et de développement. Mise à niveau `core`, `GRA`, et `brand` Le code est aussi facile à exécuter les commandes suivantes :

   ```bash
   git fetch --all
   git merge core/master gra/master brand-a/master
   git push
   ```

## Option 4 : Monorepo (recommandé)

Cette stratégie reproduit fidèlement le fonctionnement du référentiel Git du Magento Open Source.

Tout le code est développé et testé dans un seul référentiel. L’automatisation distribue des modules de ce référentiel unique, qui peuvent être installés sur UAT et dans les environnements de production à l’aide du compositeur.

![Diagramme illustrant l’option monorepo pour l’architecture de référence globale](../../../assets/playbooks/gra-monorepo1.png)

L’option monorepo vous permet de travailler facilement dans un seul référentiel, tout en offrant la possibilité de composer des instances avec des packages.

Le contrôle de version et la distillation des packages s’effectuent par le biais de l’automatisation, à l’aide des actions GitHub ou des actions GitLab.

![Diagramme illustrant l’option monorepo pour l’architecture de référence globale](../../../assets/playbooks/gra-monorepo2.png)

Consultez les ressources suivantes pour plus d’informations sur cette automatisation :

- [https://github.com/symplify/monorepo-builder](https://github.com/symplify/monorepo-builder)
- [https://github.com/danharrin/monorepo-split-github-action](https://github.com/danharrin/monorepo-split-github-action)

>[!TIP]
>
>La configuration d’un monorepo est avancée, mais offre la plus grande flexibilité au moindre coût de surcharge.

## Ne pas mélanger de stratégies

Il n’est pas conseillé d’utiliser une approche combinée à l’aide du compositeur pour les modules GRA et de la variable `app/` pour les packages de marque ou de région.

Vous n&#39;obtenez pas que tout _avantages_ mais aussi tous _inconvénients_ des deux méthodes. Vous devez choisir l’un ou l’autre (Git ou Compositeur) pour un fonctionnement optimal.

## Solutions à éviter

- **Conventions de dénomination des modules pour désigner la GRA ou la marque**

  Attribuer un nom aux modules pour désigner la GRA ou la marque entraîne un manque de flexibilité. Utilisez plutôt des métaphores du compositeur pour déterminer à quel groupe appartient un module. Par exemple, pour le VF client, module `vf/meta-gra` contient des références à tous les packages GRA et peut être installé à l’aide de la variable `composer require vf/meta-gra` . Package `vf/meta-kipling` contient des références à tous les modules spécifiques Kipling et au `vf/meta-gra` module. Les modules sont nommés `vf/module-sales` et `vf/module-sap` par exemple. Cette convention d’affectation des noms vous permet de déplacer des modules entre l’état de la marque et l’état GRA, avec un faible impact.

- **Mises à niveau de base d’Adobe Commerce par instance**

  Planifiez les mises à niveau de base d’Adobe Commerce, y compris les mises à niveau de correctif, pour que les différentes marques ou régions soient exécutées de manière aussi rapprochée que possible. La prise en charge de plusieurs versions d’Adobe Commerce pour les modules partagés entraîne le vidage des modules en raison de contraintes de compatibilité et plus que le double de l’effort de maintenance. Empêchez cette augmentation des efforts en veillant à ce que toutes les instances s’exécutent sur la même version d’Adobe Commerce avant de poursuivre le développement régulier.
