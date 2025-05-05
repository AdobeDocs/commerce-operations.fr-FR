---
title: Activation ou désactivation des modules
description: Pour gérer les modules Adobe Commerce, procédez comme suit.
exl-id: 7155950a-a66a-4254-a71c-1a9aeab47606
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '572'
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

>[!NOTE]
>
>Vous ne pouvez pas activer ni désactiver les modules directement sur les projets cloud. Vous devez exécuter ces commandes localement, puis envoyer les modifications au fichier `app/etc/config.php` pour un environnement. Voir [Workflow de projet Pro : Workflow de déploiement](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/pro-develop-deploy-workflow.html?lang=fr#deployment-workflow).

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
* `--all` pour activer ou désactiver tous les modules simultanément.
* `-f` ou `--force` pour forcer l’activation ou la désactivation d’un module malgré les dépendances. Avant d&#39;utiliser cette option, voir [A propos de l&#39;activation et de la désactivation des modules](#about-enabling-and-disabling-modules).
* `-c` ou `--clear-static-content` nettoie [fichiers de vue statique générés](../../configuration/cli/static-view-file-deployment.md).

  Si vous n’effacez pas les fichiers d’affichage statique, des problèmes peuvent se produire s’il existe plusieurs fichiers portant le même nom et que vous ne les effacez pas tous.

  En d’autres termes, en raison des règles de [secours de fichier statique](../../configuration/cli/static-view-file-deployment.md), si vous n’effacez pas les fichiers statiques et qu’il y a plusieurs fichiers nommés `logo.svg` différents, le secours peut entraîner l’affichage d’un fichier incorrect.

Par exemple, pour désactiver le module `Magento_Weee`, saisissez :

```bash
bin/magento module:disable Magento_Weee
```

Pour obtenir des informations importantes sur l&#39;activation et la désactivation des modules, voir [À propos de l&#39;activation et de la désactivation des modules](#about-enabling-and-disabling-modules).

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

Adobe Commerce vous permet d’activer ou de désactiver les modules actuellement disponibles, c’est-à-dire tout module fourni par Adobe ou tout module tiers actuellement disponible.

Certains modules ont des dépendances sur d’autres modules, auquel cas vous ne pourrez pas activer ou désactiver un module car il a des dépendances sur d’autres modules.

En outre, il peut y avoir des modules *en conflit* qui ne peuvent pas être activés en même temps.

Exemples :

* Le module A dépend du module B. Vous ne pouvez pas désactiver le module B, sauf si vous avez d’abord désactivé le module A.

* Le module A dépend du module B, qui sont tous deux désactivés. Vous devez activer le module B avant de pouvoir activer le module A.

* Le module A est en conflit avec le module B. Vous pouvez désactiver le module A et le module B, ou l’un de ces modules, mais vous *ne pouvez pas* activer le module A et le module B en même temps.

* Les dépendances sont déclarées dans le champ `require` du fichier Adobe Commerce `composer.json` pour chaque module. Les conflits sont déclarés dans le champ `conflict` des fichiers `composer.json` des modules. Nous utilisons ces informations pour créer un graphique de dépendance : `A->B` signifie que le module A dépend du module B.

* Une *chaîne de dépendance* est le chemin d’accès d’un module à un autre. Par exemple, si le module A dépend du module B et que le module B dépend du module C, la chaîne de dépendance est `A->B->C`.

Si vous tentez d’activer ou de désactiver un module qui dépend d’autres modules, le graphique de dépendance s’affiche dans le message d’erreur.

>[!NOTE]
>
>Il est possible que le module A `composer.json` déclare un conflit avec le module B, mais pas inversement.

*Ligne de commande uniquement :* Pour forcer l’activation ou la désactivation d’un module, quelles que soient ses dépendances, utilisez l’argument facultatif `--force`.

>[!NOTE]
>
>L’utilisation de `--force` peut désactiver votre magasin et entraîner des problèmes d’accès à l’administrateur.
