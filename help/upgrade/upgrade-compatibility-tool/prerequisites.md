---
title: '"[!DNL Upgrade Compatibility Tool] conditions requises"'
description: 'Vérifiez que votre système respecte la configuration requise pour exécuter la variable [!DNL Upgrade Compatibility Tool] dans une interface de ligne de commande pour votre projet Adobe Commerce. '
source-git-commit: 7ec999f9122eb0707ac6c37b7b49f9c423945318
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Clés d’accès Adobe Commerce

{{commerce-only}}

Vous devez avoir [Clés d’accès Adobe Commerce](https://devdocs.magento.com/marketplace/sellers/profile-information.html#access-keys) pour télécharger et utiliser le [!DNL Upgrade Compatibility Tool]. Ajoutez vos clés d’accès Adobe Commerce à votre `auth.json` qui se trouve à l’emplacement suivant : `~/.composer` par défaut.

>[!NOTE]
>
>Vérifiez vos **COMPOSER_HOME** pour voir où la variable `auth.json` se trouve.

Le **clé publique** correspond au _username_ tandis que la variable **clé privée** est la valeur _password_:

## Exemple de clés d’accès Adobe Commerce

```json
    "http-basic": {
        "repo.magento.com": {
            "username": "YOUR_MAGENTO_PUBLIC_KEY",
            "password": "YOUR_MAGENTO_PRIVATE_KEY"
        }
    },
```

>[!NOTE]
>
> Si vous ne configurez pas correctement votre **Clés d’accès Adobe Commerce**, vous ne pouvez pas télécharger le [!DNL Upgrade Compatibility Tool] et le `composer create-project` échoue.

Exécuter `composer install` dans votre terminal pour installer les dépendances.

## Configuration requise

Conditions minimales requises pour utiliser la variable [!DNL Upgrade Compatibility Tool] dans une interface de ligne de commande :

| **Conditions** | **Contraintes** |
|----------------|-----------------|
| version PHP | >= 7.3 |
| Compositeur | aucune exigence connue. |
| Node.js | Versions de Node.js `^12.22.0`, `^14.17.0`ou `>=16.0.0` (voir [Installation de Node.js](https://nodejs.dev/learn/how-to-install-nodejs)) |
| Limites de mémoire | Au moins 2 Go de mémoire vive. |

Adobe Commerce est uniquement pris en charge sur les systèmes d’exploitation Linux. Vous pouvez exécuter la variable [!DNL Upgrade Compatibility Tool] sous Linux OS. Vous n’avez pas à exécuter la variable [!DNL Upgrade Compatibility Tool] où se trouve votre instance Adobe Commerce.

Il est nécessaire que la fonction [!DNL Upgrade Compatibility Tool] pour accéder au code source de l’instance Adobe Commerce. Par exemple, vous pouvez l’installer sur un serveur et le pointer vers votre installation Adobe Commerce sur un autre serveur.

Si vous exécutez le [!DNL Upgrade Compatibility Tool] pour une instance Adobe Commerce avec des modules et des fichiers volumineux, l’outil peut nécessiter une quantité élevée de mémoire vive (au moins 2 Go).
