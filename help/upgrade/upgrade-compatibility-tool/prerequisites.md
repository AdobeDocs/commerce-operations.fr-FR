---
title: '''[!DNL Upgrade Compatibility Tool] conditions requises'
description: Vérifiez que votre système respecte la configuration requise pour exécuter la variable [!DNL Upgrade Compatibility Tool] dans une interface de ligne de commande pour votre projet Adobe Commerce.
exl-id: b8af2e07-3d28-4937-bb88-b0a1c88a2938
source-git-commit: 40d850add2ef8c51e9192758135768306b163780
workflow-type: tm+mt
source-wordcount: '303'
ht-degree: 0%

---

# Clés d’accès Adobe Commerce

{{commerce-only}}

Vous devez avoir [Clés d’accès Adobe Commerce](https://developer.adobe.com/commerce/marketplace/guides/sellers/profile-information/#access-keys) pour télécharger et utiliser le [!DNL Upgrade Compatibility Tool]. Ajoutez vos clés d’accès Adobe Commerce à votre `auth.json` qui se trouve à l’emplacement suivant : `~/.composer` par défaut.

>[!NOTE]
>
>Vérifiez vos **COMPOSER_HOME** pour voir où la variable `auth.json` se trouve.

La variable **clé publique** correspond au _username_ tandis que la variable **clé privée** est la valeur _password_:

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
> Si vous ne configurez pas correctement votre **Clés d’accès Adobe Commerce**, vous ne pouvez pas télécharger le fichier [!DNL Upgrade Compatibility Tool] et la variable `composer create-project` échoue.

Exécuter `composer install` dans votre terminal pour installer les dépendances.

## Configuration requise

Conditions minimales requises pour utiliser la variable [!DNL Upgrade Compatibility Tool] dans une interface de ligne de commande :

| **Conditions** | **Contrainte** |
|----------------|-----------------|
| version PHP | >= 7.3 |
| Compositeur | aucune exigence connue. |
| Node.js | Versions de Node.js `^12.22.0`, `^14.17.0`, ou `>=16.0.0` (voir [Installation de Node.js](https://nodejs.org/en/learn/getting-started/how-to-install-nodejs)) |
| Limites de mémoire | Au moins 2 Go de mémoire vive. |

[!DNL Upgrade Compatibility Tool] require [PCNTL](https://www.php.net/manual/en/book.pcntl.php) et d’autres extensions PHP pour l’exécution. Vérifiez les extensions PHP requises en utilisant `composer check-platform-reqs` command :

```bash
# Example output of `composer check-platform-reqs` command for UCT 2.2.6 and PHP 7.4:

$ composer check-platform-reqs
Checking platform requirements for packages in the vendor dir
ext-ctype     *         success provided by symfony/polyfill-ctype
ext-dom       20031129  success
ext-filter    7.4.30    success
ext-json      7.4.30    success
ext-libxml    7.4.30    success
ext-mbstring  *         success provided by symfony/polyfill-mbstring
ext-openssl   7.4.30    success
ext-pcntl     7.4.30    success
ext-pcre      7.4.30    success
ext-phar      7.4.30    success
ext-simplexml 7.4.30    success
ext-tokenizer 7.4.30    success
ext-xml       7.4.30    success
ext-xmlwriter 7.4.30    success
ext-zip       1.15.6    success
php           7.4.30    success
```

Adobe Commerce est uniquement pris en charge sur les systèmes d’exploitation Linux. Vous pouvez exécuter la variable [!DNL Upgrade Compatibility Tool] sous Linux OS. Vous n’avez pas à exécuter la variable [!DNL Upgrade Compatibility Tool] où se trouve votre instance Adobe Commerce.

Il est nécessaire que la fonction [!DNL Upgrade Compatibility Tool] pour accéder au code source de l’instance Adobe Commerce. Par exemple, vous pouvez l’installer sur un serveur et le pointer vers votre installation Adobe Commerce sur un autre serveur.

Si vous exécutez la variable [!DNL Upgrade Compatibility Tool] pour une instance Adobe Commerce avec des modules et des fichiers volumineux, l’outil peut nécessiter une quantité élevée de mémoire vive (au moins 2 Go).

Exécutez la variable [!DNL Upgrade Compatibility Tool] de la [[!DNL Site-Wide Analysis Tool]](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/upgrade-compatibility-tool/use-upgrade-compatibility-tool/integrate-analysis-tool.html) pour [Adobe Commerce sur l’infrastructure cloud](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html){target=_blank} projets.
