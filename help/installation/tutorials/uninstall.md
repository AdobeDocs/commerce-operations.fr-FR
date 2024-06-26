---
title: Désinstallation ou réinstallation d’Adobe Commerce
description: Pour désinstaller et réinstaller les installations sur site d’Adobe Commerce, procédez comme suit.
exl-id: fbaeee2c-8da0-4c89-a6d1-882a65014520
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '265'
ht-degree: 0%

---

# Désinstallation ou réinstallation d’Adobe Commerce

Avant d’utiliser ces commandes, vous devez : [installation de l’application](../tutorials/install.md).

## Mettre à jour l’application

Pour mettre à jour l’application :

* Si vous avez installé le logiciel à partir d’une archive ou si vous avez utilisé &quot;compositeur-create-project&quot;, reportez-vous à la section [Guide de mise à niveau](../../upgrade/overview.md).
* Si vous êtes un développeur contributeur (c’est-à-dire que vous avez utilisé `git clone`), voir [Mettre à jour l’application](../../upgrade/developer/git-installs.md).

## Réinstallation de l’application

La manière dont vous réinstallez l’application à partir de la ligne de commande dépend de votre rôle :

* Si vous avez installé le logiciel à partir d’une archive ou si vous avez utilisé &quot;compositeur-create-project&quot;, reportez-vous à la section [Mise à jour des dépendances d’installation](https://developer.adobe.com/commerce/contributor/guides/install/update-dependencies/).
* Si vous êtes un développeur contributeur (c’est-à-dire que vous avez commencé à utiliser `git clone`), voir [Mise à jour des dépendances d’installation](https://developer.adobe.com/commerce/contributor/guides/install/update-dependencies/).

## Désinstallation de l’application

La désinstallation de l’application entraîne le dépôt et la restauration de la base de données, la suppression de la configuration de déploiement et l’effacement des répertoires situés sous `var`.

Pour désinstaller l’application, saisissez la commande suivante :

```bash
bin/magento setup:uninstall
```

Le message suivant s’affiche pour confirmer la désinstallation :

```terminal
[SUCCESS]: Magento uninstallation complete.
```

## Conservation facultative des fichiers générés

Par défaut, `bin/magento setup:upgrade` efface le code compilé et le cache. En règle générale, vous utilisez `bin/magento setup:upgrade` pour mettre à jour les composants et chaque composant peut nécessiter différentes classes compilées.

Cependant, dans certains cas (en particulier lors du déploiement en production), vous souhaiterez peut-être éviter d’effacer le code compilé, car cela peut prendre du temps. (Le cache est toujours effacé.) Mise à jour du schéma et des données de la base de données *without* effacement du code compilé, saisissez :

```bash
bin/magento setup:upgrade --keep-generated
```

>[!WARNING]
>
>Le paramètre facultatif `--keep-generated` doit être utilisée dans des circonstances limitées par des intégrateurs système expérimentés. *only*. Cette option doit être *never* à utiliser dans un environnement de développement. Une utilisation incorrecte de ce paramètre facultatif peut entraîner des erreurs lors de l’exécution du code.

## Installation de l’application

* [Installation à l’aide de la ligne de commande](../advanced.md)
