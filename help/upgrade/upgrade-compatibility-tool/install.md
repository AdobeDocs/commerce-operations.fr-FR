---
title: Installez le [!DNL Upgrade Compatibility Tool]
description: Procédez comme suit pour installer le [!DNL Upgrade Compatibility Tool] pour votre projet Adobe Commerce.
source-git-commit: 3d9a721e33621b78f03f16b932a1ba2904ae4010
workflow-type: tm+mt
source-wordcount: '739'
ht-degree: 0%

---


# Installez le [!DNL Upgrade Compatibility Tool]

Le [!DNL Upgrade Compatibility Tool] est un outil de ligne de commande qui vérifie une instance personnalisée d’Adobe Commerce par rapport à une version spécifique en analysant tous les modules qui y sont installés. Elle renvoie une liste des erreurs et des avertissements à corriger avant la mise à niveau vers la dernière version d’Adobe Commerce.

## Workflow

Le diagramme suivant montre le workflow attendu lors de l’exécution de la variable [!DNL Upgrade Compatibility Tool]:

![[!DNL Upgrade Compatibility Tool] Diagramme](../../assets/upgrade-guide/mvp-diagram-v3.png)

## Qui est le [!DNL Upgrade Compatibility Tool] pour ?

Le cas d’utilisation suivant décrit le processus type de mise à niveau de l’instance d’un client par un partenaire Adobe Commerce :

1. L’ingénieur logiciel d’un partenaire télécharge la variable [!DNL Upgrade Compatibility Tool] du module [Référentiel Adobe Commerce](https://repo.magento.com/) et l’exécute pendant la phase bêta de la dernière version d’Adobe Commerce. Voir [Téléchargez la [!DNL Upgrade Compatibility Tool]](../upgrade-compatibility-tool/install.md#download-the-upgrade-compatibility-tool) pour plus d’informations.
1. L’ingénieur logiciel génère une instance Vanilla pour la version spécifique d’Adobe Commerce actuellement installée. Voir [Guide du contributeur](https://devdocs.magento.com/contributor-guide/contributing.html#vanilla-pr) pour plus d’informations sur l’utilisation de la variable `instance` pour générer une installation Vanilla.
1. L’ingénieur logiciel voit qu’il existe plusieurs zones personnalisées rompues dans l’inventaire et les modules de catalogue et qu’elles obtiennent également un score de complexité de X. Voir la section [Développeur](../upgrade-compatibility-tool/developer.md) pour plus d’informations sur le score de complexité.
1. Grâce à ces informations, l’ingénieur logiciel peut comprendre la complexité de la mise à niveau et transmettre ces informations au gestionnaire de compte du partenaire.
1. Le gestionnaire de compte crée un calendrier et un coût pour la mise à niveau d’Adobe Commerce, ce qui leur permet d’obtenir l’approbation de leur responsable.
1. Avec l’approbation de leur responsable, l’ingénieur logiciel travaille sur les modifications de code requises pour corriger les modules endommagés.
1. L’ingénieur logiciel exécute le [!DNL Upgrade Compatibility Tool] une fois de plus avec une version préliminaire d’Adobe Commerce pour s’assurer qu’il n’y a pas de nouveaux problèmes et que leurs modifications de code corrigent les problèmes détectés lors de la phase bêta.
1. Tout extrait et l’ingénieur logiciel envoie le code vers un environnement d’évaluation où les tests de régression confirment que tous les tests sont en vert, ce qui leur permet de publier la dernière version d’Adobe Commerce en production le jour même où la version préliminaire d’Adobe Commerce est publiée.

   ![[!DNL Upgrade Compatibility Tool] audience](../../assets/upgrade-guide/audience-uct-v3.png)

>[!NOTE]
>
>Une instance Vanilla est une installation propre d’une balise ou d’une branche de version spécifiée pour une version spécifique.

## Conditions préalables

Voir [conditions préalables](../upgrade-compatibility-tool/prerequisites.md) pour plus d’informations.

>[!NOTE]
>
>Vous pouvez exécuter la variable [!DNL Upgrade Compatibility Tool] dans n’importe quel système d’exploitation. Il n’est pas nécessaire d’exécuter la variable [!DNL Upgrade Compatibility Tool] où se trouve votre instance Adobe Commerce. Il est nécessaire que la fonction [!DNL Upgrade Compatibility Tool] pour accéder au code source de l’instance Adobe Commerce. Par exemple, vous pouvez installer l’outil sur un serveur et le pointer vers votre installation Adobe Commerce sur un autre serveur.

Si vous exécutez le [!DNL Upgrade Compatibility Tool] pour une instance Adobe Commerce avec des modules et des fichiers volumineux, l’outil peut nécessiter une grande quantité de RAM, au moins 2 Go de mémoire vive.

### Actions recommandées

Les bonnes pratiques d’Adobe Commerce recommandent d’éviter que deux modules portent le même nom. Si cela se produit, la variable [!DNL Upgrade Compatibility Tool] affiche une erreur de segmentation.

Pour éviter cette erreur, il est recommandé d’exécuter la variable `bin` avec l’option ajoutée `-m`:

```bash
bin/uct upgrade:check /<dir>/<instance-name> --coming-version=2.4.1 -m /vendor/<vendor-name>/<module-name>
```

>[!NOTE]
>
>Le `<dir>` est le répertoire dans lequel se trouve votre instance Adobe Commerce.

Le `-m` permet à la fonction [!DNL Upgrade Compatibility Tool] pour analyser chaque module spécifique indépendamment afin d’éviter de rencontrer deux modules portant le même nom dans votre instance Adobe Commerce.

Cette option de commande permet également d’activer la fonction [!DNL Upgrade Compatibility Tool] pour analyser un dossier contenant plusieurs modules :

```bash
bin/uct upgrade:check /<dir>/<instance-name> --coming-version=2.4.1 -m /vendor/<vendor-name>/
```

Cette recommandation permet également de résoudre les problèmes de mémoire qui peuvent se produire lors de l’exécution de la variable [!DNL Upgrade Compatibility Tool].

## Téléchargez la [!DNL Upgrade Compatibility Tool]

Pour télécharger le [!DNL Upgrade Compatibility Tool], exécutez la commande suivante :

```bash
composer create-project magento/upgrade-compatibility-tool uct --repository https://repo.magento.com
```

## Installer

Pour installer le [!DNL Upgrade Compatibility Tool], vous devez installer les prérequis nécessaires :

* Clés d’accès Adobe Commerce
* Compositeur
* Node.js

### Clés d’accès Adobe Commerce

Vous devez avoir [Clés d’accès Adobe Commerce](https://devdocs.magento.com/marketplace/sellers/profile-information.html#access-keys) pour télécharger et utiliser le [!DNL Upgrade Compatibility Tool]. Ajoutez vos clés d’accès Adobe Commerce à votre `auth.json` qui se trouve à l’emplacement suivant : `~/.composer` par défaut.

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

Cloner le [!DNL Upgrade Compatibility Tool] référentiel et exécution `composer install` dans votre terminal pour installer les dépendances.

>[!WARNING]
>
>Si la variable **Clés d’accès Adobe Commerce** ne sont pas correctement configurés, la variable [!DNL Upgrade Compatibility Tool] ne s’installe pas et vous obtiendrez des erreurs lors de l’exécution de la variable `composer install` .

### Node.js

Pour installer Node.js, voir Node.js [documentation](https://nodejs.dev/learn/how-to-install-nodejs).

## Extensions tierces

Adobe vous recommande de contacter votre fournisseur d’extension pour déterminer si votre extension est entièrement compatible avec Adobe Commerce 2.4.x.

Voir [Exécution de l’outil](../upgrade-compatibility-tool/run.md) pour plus d’informations sur l’exécution de la variable [!DNL Upgrade Compatibility Tool].
