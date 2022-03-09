---
title: Installez le [!DNL Upgrade Compatibility Tool]
description: Procédez comme suit pour installer le [!DNL Upgrade Compatibility Tool] pour votre projet Adobe Commerce.
source-git-commit: 218b099caa883f66ddda48407fb789e51fedc203
workflow-type: tm+mt
source-wordcount: '241'
ht-degree: 0%

---


# Installez le [!DNL Upgrade Compatibility Tool]

{{commerce-only}}

Le [!DNL Upgrade Compatibility Tool] est un outil de ligne de commande qui vérifie une instance personnalisée d’Adobe Commerce par rapport à une version spécifique en analysant tous les modules qui y sont installés. Elle renvoie une liste des erreurs et des avertissements à corriger avant la mise à niveau vers la dernière version d’Adobe Commerce.

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

## Conditions préalables

Voir [conditions préalables](../upgrade-compatibility-tool/prerequisites.md) pour plus d’informations.

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

Adobe vous recommande de contacter votre fournisseur d’extension pour déterminer si votre extension est entièrement compatible avec la dernière version d’Adobe Commerce publiée.

Voir [Exécution de l’outil](../upgrade-compatibility-tool/run.md) pour plus d’informations sur l’exécution de la variable [!DNL Upgrade Compatibility Tool].
