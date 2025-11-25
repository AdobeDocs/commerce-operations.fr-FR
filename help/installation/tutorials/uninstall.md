---
title: Désinstallation ou réinstallation d’Adobe Commerce
description: Pour désinstaller et réinstaller les installations sur site d’Adobe Commerce, procédez comme suit.
exl-id: fbaeee2c-8da0-4c89-a6d1-882a65014520
source-git-commit: 84a20012a81278cc95587ec14281b05330261687
workflow-type: tm+mt
source-wordcount: '265'
ht-degree: 0%

---

# Désinstallation ou réinstallation d’Adobe Commerce

Avant d’utiliser ces commandes, vous devez [installer l’application](../tutorials/install.md).

## Mise à jour de l’application

Pour mettre à jour l’application :

* Si vous avez installé le logiciel à partir d&#39;une archive ou si vous avez utilisé &#39;composer-create-project&#39;, consultez le [&#x200B; Guide de mise à niveau](../../upgrade/overview.md).
* Si vous êtes un développeur contributeur (c’est-à-dire que vous avez utilisé `git clone`), consultez [Mise à jour de l’application](../../upgrade/developer/git-installs.md).

## Réinstaller l’application

La façon dont vous réinstallez l’application à partir de la ligne de commande dépend de votre rôle :

* Si vous avez installé le logiciel à partir d&#39;une archive ou si vous avez utilisé &#39;composer-create-project&#39;, voir [Mise à jour des dépendances d&#39;installation](https://developer.adobe.com/commerce/contributor/guides/install/update-dependencies).
* Si vous êtes un développeur contributeur (c’est-à-dire que vous avez commencé à utiliser `git clone`), reportez-vous à la section [Mise à jour des dépendances d’installation](https://developer.adobe.com/commerce/contributor/guides/install/update-dependencies).

## Désinstallation de l’application

La désinstallation de l’application interrompt et restaure la base de données, supprime la configuration de déploiement et efface les répertoires situés sous `var`.

Pour désinstaller l&#39;application, saisissez la commande suivante :

```bash
bin/magento setup:uninstall
```

Le message suivant s’affiche pour confirmer la réussite de la désinstallation :

```
[SUCCESS]: Magento uninstallation complete.
```

## Conserver éventuellement les fichiers générés

Par défaut, `bin/magento setup:upgrade` efface le code compilé et le cache. En règle générale, vous utilisez `bin/magento setup:upgrade` pour mettre à jour les composants et chaque composant peut nécessiter différentes classes compilées.

Cependant, dans certains cas (en particulier lors d’un déploiement en production), vous pouvez éviter d’effacer le code compilé, car cela peut prendre un certain temps. (Le cache est toujours effacé.) Pour mettre à jour le schéma et les données de la base de données *sans* effacer le code compilé, saisissez :

```bash
bin/magento setup:upgrade --keep-generated
```

>[!WARNING]
>
>L’option `--keep-generated` facultative ne doit être utilisée que dans certains cas par des intégrateurs système expérimentés *uniquement*. Cette option ne doit *jamais* être utilisée dans un environnement de développement. Une utilisation incorrecte de ce paramètre facultatif peut entraîner des erreurs lors de l’exécution du code.

## Installation de l’application

* [Installation à l’aide de la ligne de commande](../advanced.md)
