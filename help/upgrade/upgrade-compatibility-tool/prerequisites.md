---
title: '[!DNL Upgrade Compatibility Tool] requirements'
description: Vérifiez que votre système répond aux exigences nécessaires pour exécuter le  [!DNL Upgrade Compatibility Tool]  dans une interface de ligne de commande pour votre projet Adobe Commerce.
exl-id: b8af2e07-3d28-4937-bb88-b0a1c88a2938
source-git-commit: 40d850add2ef8c51e9192758135768306b163780
workflow-type: tm+mt
source-wordcount: '273'
ht-degree: 0%

---

# Clés d’accès Adobe Commerce

{{commerce-only}}

Vous devez disposer de [clés d’accès Adobe Commerce](https://developer.adobe.com/commerce/marketplace/guides/sellers/profile-information/#access-keys) pour télécharger et utiliser [!DNL Upgrade Compatibility Tool]. Ajoutez vos clés d’accès Adobe Commerce à votre fichier `auth.json`, situé par défaut à l’emplacement `~/.composer`.

>[!NOTE]
>
>Vérifiez la variable d&#39;environnement **COMPOSER_HOME** pour voir où se trouve le fichier `auth.json`.

La **clé publique** correspond au _nom d’utilisateur_ tandis que la **clé privée** correspond au _mot de passe_ :

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
> Si vous ne configurez pas correctement vos **clés d&#39;accès Adobe Commerce**, vous ne pouvez pas télécharger [!DNL Upgrade Compatibility Tool] et la commande `composer create-project` échouera.

Exécutez `composer install` dans votre terminal pour installer les dépendances.

## Configuration requise

La configuration minimale requise pour utiliser le [!DNL Upgrade Compatibility Tool] dans une interface de ligne de commande est la suivante :

| **Exigences** | **Contraintes** |
|----------------|-----------------|
| version PHP | >= 7.3 |
| Compositeur | aucune exigence connue. |
| Node.js | Node.js versions `^12.22.0`, `^14.17.0` ou `>=16.0.0` (voir [ Installation de Node.js](https://nodejs.org/en/learn/getting-started/how-to-install-nodejs)) |
| Limites de mémoire | Au moins 2 Go de mémoire vive. |

[!DNL Upgrade Compatibility Tool] nécessite [PCNTL](https://www.php.net/manual/en/book.pcntl.php) et d’autres extensions PHP pour l’exécution. Vérifiez les extensions PHP requises à l’aide de la commande `composer check-platform-reqs` :

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

Adobe Commerce est uniquement pris en charge sur les systèmes d’exploitation Linux. Vous pouvez exécuter le [!DNL Upgrade Compatibility Tool] dans un système d’exploitation Linux. Il n’est pas nécessaire d’exécuter l’ [!DNL Upgrade Compatibility Tool] où se trouve votre instance Adobe Commerce.

Il est nécessaire que le [!DNL Upgrade Compatibility Tool] ait accès au code source de l&#39;instance Adobe Commerce. Par exemple, vous pouvez l’installer sur un serveur et le pointer vers votre installation Adobe Commerce sur un autre serveur.

Si vous exécutez le [!DNL Upgrade Compatibility Tool] sur une instance Adobe Commerce avec des modules et des fichiers volumineux, l’outil peut nécessiter une quantité élevée de RAM (au moins 2 Go).

Exécutez le [!DNL Upgrade Compatibility Tool] à partir des projets [[!DNL Site-Wide Analysis Tool]](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/upgrade-compatibility-tool/use-upgrade-compatibility-tool/integrate-analysis-tool.html?lang=fr) pour [Adobe Commerce sur l’infrastructure cloud](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html?lang=fr){target=_blank}.
