---
title: Activation ou désactivation des modules
description: Pour gérer les modules Adobe Commerce ou Magento Open Source, procédez comme suit.
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '551'
ht-degree: 0%

---


# Activation ou désactivation des modules

Cette commande ne comporte aucune condition préalable.

## État du module

Utilisez la commande suivante pour répertorier les modules activés et désactivés :

```bash
bin/magento module:status [--enabled] [--disabled] <module-list>
```

Où

* `--enabled` répertorie tous les modules activés.
* `--disabled` répertorie tous les modules désactivés.
* `<module-list>` est une liste de modules délimités par des espaces pour vérifier l’état. Si un nom de module contient des caractères spéciaux, placez le nom entre guillemets simples ou doubles.

## Activation et désactivation des modules

Pour activer ou désactiver les modules disponibles, utilisez la commande suivante :

```bash
bin/magento module:enable [-c|--clear-static-content] [-f|--force] [--all] <module-list>
```

```bash
bin/magento module:disable [-c|--clear-static-content] [-f|--force] [--all] <module-list>
```

Où

* `<module-list>` est une liste de modules délimitée par des espaces à activer ou désactiver. Si un nom de module contient des caractères spéciaux, placez le nom entre guillemets simples ou doubles.
* `--all` pour activer ou désactiver tous les modules en même temps.
* `-f` ou `--force` pour forcer l’activation ou la désactivation d’un module malgré les dépendances. Avant d’utiliser cette option, voir [A propos de l&#39;activation et de la désactivation des modules](#about-enabling-and-disabling-modules).
* `-c` ou `--clear-static-content` cleans [fichiers d’affichage statique générés](../../configuration/cli/static-view-file-deployment.md).

   Si vous n’effacez pas les fichiers d’affichage statique, des problèmes peuvent se produire s’il existe plusieurs fichiers portant le même nom et que vous ne les effacez pas tous.

   En d’autres termes, à cause de la variable [secours de fichier statique](../../configuration/cli/static-view-file-deployment.md) règles, si vous n’effacez pas les fichiers statiques et qu’il existe plusieurs fichiers nommés `logo.svg` qui sont différents, la solution de secours peut entraîner l’affichage d’un fichier incorrect.

Par exemple, pour désactiver la variable `Magento_Weee` module, saisissez :

```bash
bin/magento module:disable Magento_Weee
```

Pour obtenir des informations importantes sur l’activation et la désactivation des modules, voir [A propos de l&#39;activation et de la désactivation des modules](#about-enabling-and-disabling-modules).

## Mise à jour de la base de données

Si vous avez activé un ou plusieurs modules, exécutez la commande suivante pour mettre à jour la base de données :

```bash
bin/magento setup:upgrade
```

Nettoyez ensuite le cache :

```bash
bin/magento cache:clean
```

## A propos de l&#39;activation et de la désactivation des modules

Adobe Commerce et Magento Open Source vous permettent d’activer ou de désactiver les modules actuellement disponibles. en d’autres termes, tout module fourni par l’Adobe ou tout module tiers actuellement disponible.

Certains modules ont des dépendances sur d’autres modules, auquel cas vous ne pourrez pas activer ou désactiver un module car il a des dépendances sur d’autres modules.

En outre, il peut y avoir *conflit* modules qui ne peuvent pas être activés simultanément.

Exemples :

* Le module A dépend du module B. Vous ne pouvez pas désactiver le module B, sauf si vous avez d’abord désactivé le module A.

* Le module A dépend du module B, qui sont tous deux désactivés. Vous devez activer le module B avant de pouvoir activer le module A.

* Le module A est en conflit avec le module B. Vous pouvez désactiver le module A et le module B ou l’un ou l’autre de ces modules, mais vous pouvez *cannot* Activez simultanément les modules A et B.

* Les dépendances sont déclarées dans la variable `require` dans Adobe Commerce et Magento Open Source `composer.json` pour chaque module. Les conflits sont déclarés dans le `conflict` champ dans les modules&#39; `composer.json` fichiers . Nous utilisons ces informations pour créer un graphique de dépendances : `A->B` signifie que le module A dépend du module B.

* A *chaîne de dépendance* est le chemin d’accès d’un module à un autre. Par exemple, si le module A dépend du module B et que le module B dépend du module C, la chaîne de dépendance est `A->B->C`.

Si vous tentez d’activer ou de désactiver un module qui dépend d’autres modules, le graphique de dépendance s’affiche dans le message d’erreur.

>[!NOTE]
>
>Il est possible que le module A soit `composer.json` déclare un conflit avec le module B, mais pas à l’inverse.

*Ligne de commande uniquement :* Pour forcer l’activation ou la désactivation d’un module, quelles que soient ses dépendances, utilisez l’option `--force` argument .

>[!NOTE]
>
>Utilisation `--force` peut désactiver votre boutique et entraîner des problèmes d’accès à l’administrateur.
