---
title: Installation de l’outil de compatibilité de mise à niveau
description: Pour installer l’outil de compatibilité de mise à niveau pour votre projet Adobe Commerce, procédez comme suit.
source-git-commit: bbc412f1ceafaa557d223aabfd4b2a381d6ab04a
workflow-type: tm+mt
source-wordcount: '817'
ht-degree: 0%

---


# Installation de l’outil de compatibilité de mise à niveau

L’outil de compatibilité de mise à niveau est un outil de ligne de commande qui vérifie la personnalisation d’une instance Adobe Commerce par rapport à une version spécifique en analysant tous les modules qui y sont installés. Elle renvoie une liste des erreurs et des avertissements à corriger avant la mise à niveau vers la dernière version d’Adobe Commerce.

## Workflow

Le diagramme suivant montre le workflow attendu lors de l’exécution de l’outil de compatibilité de mise à niveau :

![Diagramme de l’outil de compatibilité de mise à niveau](../../assets/upgrade-guide/mvp-diagram-v3.png)

## Pour qui est l’outil de compatibilité de mise à niveau ?

Le cas d’utilisation suivant décrit le processus type de mise à niveau de l’instance d’un client par un partenaire Adobe Commerce :

1. L’ingénieur logiciel d’un partenaire télécharge le package de l’outil de compatibilité de mise à niveau à partir du [Référentiel Adobe Commerce](https://repo.magento.com/) et l’exécute pendant la phase bêta de la dernière version d’Adobe Commerce. Voir [Téléchargement de l’outil de compatibilité de mise à niveau](../upgrade-compatibility-tool/install.md#download-the-upgrade-compatibility-tool) pour plus d’informations.
1. L’ingénieur logiciel génère une instance Vanilla pour la version spécifique d’Adobe Commerce actuellement installée. Voir [Guide du contributeur](https://devdocs.magento.com/contributor-guide/contributing.html#vanilla-pr) pour plus d’informations sur l’utilisation de la variable `instance` pour générer une installation Vanilla.
1. L’ingénieur logiciel voit qu’il existe plusieurs zones personnalisées rompues dans l’inventaire et les modules de catalogue et qu’elles obtiennent également un score de complexité de X. Voir la section [Développeur](../upgrade-compatibility-tool/developer.md) pour plus d’informations sur le score de complexité.
1. Grâce à ces informations, l’ingénieur logiciel peut comprendre la complexité de la mise à niveau et transmettre ces informations au gestionnaire de compte du partenaire.
1. Le gestionnaire de compte crée un calendrier et un coût pour la mise à niveau d’Adobe Commerce, ce qui leur permet d’obtenir l’approbation de leur responsable.
1. Avec l’approbation de leur responsable, l’ingénieur logiciel travaille sur les modifications de code requises pour corriger les modules endommagés.
1. L’ingénieur logiciel exécute l’outil de compatibilité de mise à niveau une fois de plus avec une version préliminaire d’Adobe Commerce pour s’assurer qu’il n’y a aucun nouveau problème et que leurs modifications de code corrigent les problèmes détectés lors de la phase bêta.
1. Tout extrait et l’ingénieur logiciel envoie le code vers un environnement d’évaluation où les tests de régression confirment que tous les tests sont en vert, ce qui leur permet de publier la dernière version d’Adobe Commerce en production le jour même où la version préliminaire d’Adobe Commerce est publiée.

   ![Audience de l’outil de compatibilité de mise à niveau](../../assets/upgrade-guide/audience-uct-v3.png)

>[!NOTE]
>
>Une instance Vanilla est une installation propre d’une balise ou d’une branche de version spécifiée pour une version spécifique.

## Conditions préalables

Voir [conditions préalables](../upgrade-compatibility-tool/prerequisites.md) pour plus d’informations.

>[!NOTE]
>
>Vous pouvez exécuter l’outil de compatibilité de mise à niveau dans n’importe quel système d’exploitation. Il n’est pas nécessaire d’exécuter l’outil de compatibilité de mise à niveau où se trouve votre instance Adobe Commerce. Il est nécessaire que l’outil de compatibilité de mise à niveau ait accès au code source de l’instance Adobe Commerce. Par exemple, vous pouvez installer l’outil sur un serveur et le pointer vers votre installation Adobe Commerce sur un autre serveur.

Si vous exécutez l’outil de compatibilité de mise à niveau sur une instance Adobe Commerce avec des modules et des fichiers volumineux, l’outil peut nécessiter une quantité élevée de RAM, au moins 2 Go de mémoire vive.

### Actions recommandées

Les bonnes pratiques d’Adobe Commerce recommandent d’éviter que deux modules portent le même nom. Si cela se produit, l’outil de compatibilité de mise à niveau affiche une erreur de segmentation.

Pour éviter cette erreur, il est recommandé d’exécuter la variable `bin` avec l’option ajoutée `-m`:

```bash
bin/uct upgrade:check /<dir>/<instance-name> --coming-version=2.4.1 -m /vendor/<vendor-name>/<module-name>
```

>[!NOTE]
>
>Le `<dir>` est le répertoire dans lequel se trouve votre instance Adobe Commerce.

Le `-m` L’option permet à l’outil de compatibilité de mise à niveau d’analyser indépendamment chaque module spécifique afin d’éviter de rencontrer deux modules portant le même nom dans votre instance Adobe Commerce.

Cette option de commande permet également à l’outil de compatibilité de mise à niveau d’analyser un dossier contenant plusieurs modules :

```bash
bin/uct upgrade:check /<dir>/<instance-name> --coming-version=2.4.1 -m /vendor/<vendor-name>/
```

Cette recommandation permet également de résoudre les problèmes de mémoire qui peuvent se produire lors de l’exécution de l’outil de compatibilité de mise à niveau.

## Téléchargement de l’outil de compatibilité de mise à niveau

Pour télécharger l’outil de compatibilité de mise à niveau, exécutez la commande suivante :

```bash
composer create-project magento/upgrade-compatibility-tool uct --repository https://repo.magento.com
```

## Installer

Pour installer l’outil de compatibilité de mise à niveau, vous devez installer les prérequis nécessaires :

* Clés d’accès Adobe Commerce
* Compositeur
* Node.js

### Clés d’accès Adobe Commerce

Vous devez avoir [Clés d’accès Adobe Commerce](https://devdocs.magento.com/marketplace/sellers/profile-information.html#access-keys) pour télécharger et utiliser l’outil de compatibilité de mise à niveau. Ajoutez vos clés d’accès Adobe Commerce à votre `auth.json` qui se trouve à l’emplacement suivant : `~/.composer` par défaut.

>[!WARNING]
>
>Vérifiez vos **COMPOSER_HOME** pour voir où la variable `auth.json` se trouve.

Le **clé publique** correspond au _username_ tandis que la variable **clé privée** est la valeur _password_:

### Exemple de clés d’accès Adobe Commerce

```json
    "http-basic": {
        "repo.magento.com": {
            "username": "YOUR_MAGENTO_PUBLIC_KEY",
            "password": "YOUR_MAGENTO_PRIVATE_KEY"
        }
    },
```

### Compositeur

Cloner le référentiel de l’outil de compatibilité de mise à niveau et exécuter `composer install` dans votre terminal pour installer les dépendances.

>[!WARNING]
>
>Si la variable **Clés d’accès Adobe Commerce** ne sont pas correctement configurés, l’outil de compatibilité de mise à niveau ne s’installe pas et vous obtiendrez des erreurs lors de l’exécution de la variable `composer install` .

### Node.js

Pour installer Node.js, voir Node.js [documentation](https://nodejs.dev/learn/how-to-install-nodejs).

## Extensions tierces

Adobe vous recommande de contacter votre fournisseur d’extension pour déterminer si votre extension est entièrement compatible avec Adobe Commerce 2.4.x.

Voir [Exécution de l’outil](../upgrade-compatibility-tool/run.md) pour plus d’informations sur l’exécution de l’outil de compatibilité de mise à niveau.