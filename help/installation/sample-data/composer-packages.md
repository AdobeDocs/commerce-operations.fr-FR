---
title: Télécharger des exemples de modules du compositeur de données
description: Suivez ces étapes pour installer des exemples de données Adobe Commerce à l’aide du gestionnaire de modules PHP du compositeur.
feature: Install, Deploy
exl-id: 735591af-a152-4476-9fa6-e31c4bab3ba8
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '286'
ht-degree: 0%

---

# Télécharger des exemples de modules du compositeur de données

Cette section explique comment installer des exemples de données si vous avez obtenu le logiciel Adobe Commerce de l’une des manières suivantes :

* Téléchargement d’une archive compressée depuis `https://magento.com/tech-resources/download`.

  Si vous avez téléchargé une archive à partir de GitHub, cette méthode ne fonctionne pas car le fichier `composer.json` ne contient pas l’URL `repo.magento.com`.

* Utilisé `composer create-project`

Vous pouvez utiliser cette méthode pour obtenir des exemples de données pour Adobe Commerce, mais vous devez utiliser les mêmes [clés d&#39;authentification](../prerequisites/authentication-keys.md) que celles utilisées pour installer l&#39;application.

>[!NOTE]
>
>Si vous rencontrez des erreurs, telles que `Could not find package...` ou `...no matching package found...`, assurez-vous qu’il n’y a pas de fautes de frappe dans votre commande. Si vous rencontrez toujours des erreurs, il se peut que vous n’ayez pas accès aux référentiels du compositeur approprié, en particulier si vous utilisez Adobe Commerce. Contactez le [support Adobe Commerce](https://support.magento.com/hc/en-us) pour obtenir de l’aide.

Vous pouvez utiliser le compositeur pour installer des exemples de données avant ou après l’installation de l’application. Cependant, il peut y avoir [tâches supplémentaires](remove-or-update.md).

Si vous êtes un développeur contributeur, reportez-vous à la section [Installation en clonant des référentiels](git-repositories.md).

>[!WARNING]
>
>N’installez pas de données d’exemple si votre application est définie pour le [mode de production](../../configuration/bootstrap/application-modes.md#production-mode). Passez d’abord en [mode développeur](../../configuration/bootstrap/application-modes.md#developer-mode) . L&#39;installation de données d&#39;exemple en mode de production [échoue](https://support.magento.com/hc/en-us/articles/360033824571#symptom-production-mode-trouble-samp-prod-).

Pour installer des exemples de données à l’aide de la ligne de commande, saisissez la commande suivante en tant que propriétaire du système de fichiers dans le répertoire `<app_root>` :

```bash
bin/magento sampledata:deploy
```

>[!WARNING]
>
>Si vous installez des exemples de données _après_ l&#39;installation de l&#39;application, vous devez également exécuter la commande suivante pour mettre à jour la base de données et le schéma dans le répertoire `<app_root>` :

```bash
bin/magento setup:upgrade
```

Vous devez [authentifier](../prerequisites/authentication-keys.md) pour terminer l’action.

## Erreur d’authentification

L’erreur d’authentification suivante peut s’afficher :

```
[Composer\Downloader\TransportException]
The 'https://repo.magento.com/packages.json' URL required authentication.
You must be using the interactive console to authenticate
```

Si l’erreur s’affiche, modifiez le répertoire d’installation de votre application et exécutez `composer update`, ce qui vous invite à utiliser vos [clés d’authentification](../prerequisites/authentication-keys.md).

## Effectuez l’installation des exemples de données

{{$include /help/_includes/sample-data-complete.md}}
