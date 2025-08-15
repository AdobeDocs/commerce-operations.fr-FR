---
title: Télécharger des exemples de packages du compositeur de données
description: Pour installer les données d’exemple Adobe Commerce à l’aide du gestionnaire de packages Composer PHP, procédez comme suit.
feature: Install, Deploy
exl-id: 735591af-a152-4476-9fa6-e31c4bab3ba8
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '286'
ht-degree: 0%

---

# Télécharger des exemples de packages du compositeur de données

Cette section explique comment installer des données d’exemple si vous disposez du logiciel Adobe Commerce de l’une des manières suivantes :

* Téléchargement d’une archive compressée depuis `https://magento.com/tech-resources/download`.

  Si vous avez téléchargé une archive à partir de GitHub, cette méthode ne fonctionne pas, car le fichier `composer.json` ne contient pas l’URL `repo.magento.com`.

* Utilisé `composer create-project`

Vous pouvez utiliser cette méthode pour obtenir des exemples de données pour Adobe Commerce, mais vous devez utiliser les mêmes [clés d’authentification](../prerequisites/authentication-keys.md) que celles utilisées pour installer l’application.

>[!NOTE]
>
>Si vous rencontrez des erreurs, telles que `Could not find package...` ou `...no matching package found...`, assurez-vous qu’il n’y a aucune faute de frappe dans votre commande. Si vous rencontrez toujours des erreurs, vous n’avez peut-être pas accès aux référentiels de compositeur appropriés, en particulier si vous utilisez Adobe Commerce. Contactez [l’assistance Adobe Commerce](https://support.magento.com/hc/en-us) pour obtenir de l’aide.

Vous pouvez utiliser le compositeur pour installer des données d’exemple avant ou après l’installation de l’application ; cependant, il peut y avoir [tâches supplémentaires](remove-or-update.md).

Si vous êtes un développeur contributeur, reportez-vous à la section [Installation en clonant des référentiels](git-repositories.md).

>[!WARNING]
>
>N’installez pas de données d’exemple si votre application est définie pour le [mode de production](../../configuration/bootstrap/application-modes.md#production-mode). Commencez par passer en [mode Développeur](../../configuration/bootstrap/application-modes.md#developer-mode). L’installation des données d’exemple en mode production [échoue](https://support.magento.com/hc/en-us/articles/360033824571#symptom-production-mode-trouble-samp-prod-).

Pour installer des données d’exemple à l’aide de la ligne de commande, saisissez la commande suivante en tant que propriétaire du système de fichiers dans le répertoire `<app_root>` :

```bash
bin/magento sampledata:deploy
```

>[!WARNING]
>
>Si vous installez des données d’exemple _après_ avoir installé l’application, vous devez également exécuter la commande suivante pour mettre à jour la base de données et le schéma dans le répertoire `<app_root>` :

```bash
bin/magento setup:upgrade
```

Vous devez vous [authentifier](../prerequisites/authentication-keys.md) pour terminer l’action.

## Erreur d’authentification

L’erreur d’authentification suivante peut s’afficher :

```
[Composer\Downloader\TransportException]
The 'https://repo.magento.com/packages.json' URL required authentication.
You must be using the interactive console to authenticate
```

Si l’erreur s’affiche, modifiez le répertoire d’installation de votre application et exécutez `composer update`, qui vous invite à saisir vos [clés d’authentification](../prerequisites/authentication-keys.md).

## Terminer l’installation des données d’exemple

{{$include /help/_includes/sample-data-complete.md}}
