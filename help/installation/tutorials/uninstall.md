---
title: Désinstallation ou réinstallation d’Adobe Commerce
description: Pour désinstaller et réinstaller les installations sur site d’Adobe Commerce, procédez comme suit.
exl-id: fbaeee2c-8da0-4c89-a6d1-882a65014520
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '265'
ht-degree: 0%

---

# Désinstallation ou réinstallation d’Adobe Commerce

Avant d&#39;utiliser ces commandes, vous devez [installer l&#39;application](../tutorials/install.md).

## Mettre à jour l’application

Pour mettre à jour l’application :

* Si vous avez installé le logiciel à partir d’une archive ou si vous avez utilisé &#39;compositeur-create-project&#39;, consultez le [Guide de mise à niveau](../../upgrade/overview.md).
* Si vous êtes un développeur contributeur (c&#39;est-à-dire que vous avez utilisé `git clone`), voir [Mise à jour de l&#39;application](../../upgrade/developer/git-installs.md).

## Réinstallation de l’application

La manière dont vous réinstallez l’application à partir de la ligne de commande dépend de votre rôle :

* Si vous avez installé le logiciel à partir d’une archive ou si vous avez utilisé &#39;compositeur-create-project&#39;, reportez-vous à la section [Mise à jour des dépendances d’installation](https://developer.adobe.com/commerce/contributor/guides/install/update-dependencies/).
* Si vous êtes un développeur contributeur (c&#39;est-à-dire que vous avez commencé à utiliser `git clone`), consultez la section [Mise à jour des dépendances d&#39;installation](https://developer.adobe.com/commerce/contributor/guides/install/update-dependencies/).

## Désinstallation de l’application

La désinstallation de l’application annule et restaure la base de données, supprime la configuration de déploiement et efface les répertoires sous `var`.

Pour désinstaller l’application, saisissez la commande suivante :

```bash
bin/magento setup:uninstall
```

Le message suivant s’affiche pour confirmer la désinstallation :

```
[SUCCESS]: Magento uninstallation complete.
```

## Conservation facultative des fichiers générés

Par défaut, `bin/magento setup:upgrade` efface le code compilé et le cache. En règle générale, vous utilisez `bin/magento setup:upgrade` pour mettre à jour les composants et chaque composant peut nécessiter différentes classes compilées.

Cependant, dans certains cas (en particulier lors du déploiement en production), vous souhaiterez peut-être éviter d’effacer le code compilé, car cela peut prendre du temps. (Le cache est toujours effacé.) Pour mettre à jour le schéma de base de données et les données *sans* effacer le code compilé, saisissez :

```bash
bin/magento setup:upgrade --keep-generated
```

>[!WARNING]
>
>L’option facultative `--keep-generated` doit être utilisée dans des circonstances limitées par des intégrateurs système expérimentés *uniquement*. Cette option doit *ne jamais* être utilisée dans un environnement de développement. Une utilisation incorrecte de ce paramètre facultatif peut entraîner des erreurs lors de l’exécution du code.

## Installation de l’application

* [Installation à l’aide de la ligne de commande](../advanced.md)
