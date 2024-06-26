---
title: Télécharger des exemples de modules du compositeur de données
description: Suivez ces étapes pour installer des exemples de données Adobe Commerce à l’aide du gestionnaire de modules PHP du compositeur.
feature: Install, Deploy
exl-id: 735591af-a152-4476-9fa6-e31c4bab3ba8
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '286'
ht-degree: 0%

---

# Télécharger des exemples de modules du compositeur de données

Cette section explique comment installer des exemples de données si vous avez obtenu le logiciel Adobe Commerce de l’une des manières suivantes :

* Téléchargement d’une archive compressée depuis `https://magento.com/tech-resources/download`.

  Si vous avez téléchargé une archive à partir de GitHub, cette méthode ne fonctionne pas car la variable `composer.json` ne contient pas le fichier `repo.magento.com` URL.

* Utilisé `composer create-project`

Vous pouvez utiliser cette méthode pour obtenir des exemples de données pour Adobe Commerce, mais vous devez utiliser la même méthode. [clés d’authentification](../prerequisites/authentication-keys.md) que vous avez utilisé pour installer l’application.

>[!NOTE]
>
>Si vous rencontrez des erreurs, telles que `Could not find package...` ou `...no matching package found...`, assurez-vous qu’il n’y a pas de fautes de frappe dans votre commande. Si vous rencontrez toujours des erreurs, il se peut que vous n’ayez pas accès aux référentiels du compositeur approprié, en particulier si vous utilisez Adobe Commerce. Contact [Assistance Adobe Commerce](https://support.magento.com/hc/en-us) pour obtenir de l’aide.

Vous pouvez utiliser le compositeur pour installer des exemples de données avant ou après l’installation de l’application. Cependant, il peut y avoir [tâches supplémentaires](remove-or-update.md).

Si vous êtes un développeur contributeur, reportez-vous à la section [Installation par clonage des référentiels](git-repositories.md).

>[!WARNING]
>
>N’installez pas de données d’exemple si votre application est définie sur [mode de production](../../configuration/bootstrap/application-modes.md#production-mode). Basculer vers [mode développeur](../../configuration/bootstrap/application-modes.md#developer-mode) en premier. Installation des exemples de données en mode de production [échec](https://support.magento.com/hc/en-us/articles/360033824571#symptom-production-mode-trouble-samp-prod-).

Pour installer des exemples de données à l’aide de la ligne de commande, saisissez la commande suivante en tant que propriétaire du système de fichiers dans la propriété `<app_root>` directory:

```bash
bin/magento sampledata:deploy
```

>[!WARNING]
>
>Si vous installez des exemples de données _after_ lors de l&#39;installation de l&#39;application, vous devez également exécuter la commande suivante pour mettre à jour la base de données et le schéma de la `<app_root>` directory:

```bash
bin/magento setup:upgrade
```

Vous devez : [authentifier](../prerequisites/authentication-keys.md) pour terminer l’action.

## Erreur d’authentification

L’erreur d’authentification suivante peut s’afficher :

```terminal
[Composer\Downloader\TransportException]
The 'https://repo.magento.com/packages.json' URL required authentication.
You must be using the interactive console to authenticate
```

Si l’erreur s’affiche, modifiez le répertoire d’installation de votre application et exécutez `composer update`, qui vous invite à [clés d’authentification](../prerequisites/authentication-keys.md).

## Effectuez l’installation des exemples de données

{{$include /help/_includes/sample-data-complete.md}}
