---
title: Activation ou désactivation de modules
description: Pour gérer les modules Adobe Commerce, procédez comme suit.
exl-id: 7155950a-a66a-4254-a71c-1a9aeab47606
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '572'
ht-degree: 0%

---

# Activation ou désactivation de modules

Cette commande n&#39;a pas de prérequis.

## Statut du module

Utilisez la commande suivante pour répertorier les modules activés et désactivés :

```bash
bin/magento module:status [--enabled] [--disabled] <module-list>
```

Où

* `--enabled` liste tous les modules activés.
* `--disabled` liste tous les modules désactivés.
* `<module-list>` une liste de modules séparés par des espaces pour vérifier le statut. Si un nom de module contient des caractères spéciaux, placez-le entre guillemets simples ou doubles.

>[!NOTE]
>
>Vous ne pouvez pas activer ni désactiver les modules directement dans les projets cloud. Vous devez exécuter ces commandes localement, puis pousser les modifications vers le fichier `app/etc/config.php` pour un environnement. Voir [Workflow de projet Pro : Workflow de déploiement](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/pro-develop-deploy-workflow.html?lang=fr#deployment-workflow).

## Activation et désactivation du module

Pour activer ou désactiver les modules disponibles, utilisez la commande suivante :

```bash
bin/magento module:enable [-c|--clear-static-content] [-f|--force] [--all] <module-list>
```

```bash
bin/magento module:disable [-c|--clear-static-content] [-f|--force] [--all] <module-list>
```

Où

* `<module-list>` est une liste délimitée par des espaces de modules à activer ou désactiver. Si un nom de module contient des caractères spéciaux, placez-le entre guillemets simples ou doubles.
* `--all` d’activer ou de désactiver tous les modules en même temps.
* `-f` ou `--force` de forcer l&#39;activation ou la désactivation d&#39;un module malgré les dépendances. Avant d’utiliser cette option, voir [&#x200B; À propos de l’activation et de la désactivation des modules &#x200B;](#about-enabling-and-disabling-modules).
* `-c` ou `--clear-static-content` nettoie [les fichiers d’affichage statiques générés](../../configuration/cli/static-view-file-deployment.md).

  Si vous ne parvenez pas à effacer les fichiers d’affichage statique, des problèmes peuvent se produire si plusieurs fichiers portent le même nom et que vous ne les effacez pas tous.

  En d’autres termes, en raison des règles [static file fallback](../../configuration/cli/static-view-file-deployment.md), si vous n’effacez pas les fichiers statiques et qu’il existe plusieurs fichiers nommés `logo.svg` différents, la fonction de secours peut entraîner l’affichage d’un fichier incorrect.

Par exemple, pour désactiver le module `Magento_Weee`, saisissez :

```bash
bin/magento module:disable Magento_Weee
```

Pour obtenir des informations importantes sur l’activation et la désactivation des modules, voir [&#x200B; À propos de l’activation et de la désactivation des modules](#about-enabling-and-disabling-modules).

## Mise à jour de la base de données

Si vous avez activé un ou plusieurs modules, exécutez la commande suivante pour mettre à jour la base de données :

```bash
bin/magento setup:upgrade
```

Nettoyez ensuite le cache :

```bash
bin/magento cache:clean
```

## À propos de l’activation et de la désactivation des modules

Adobe Commerce vous permet d’activer ou de désactiver les modules actuellement disponibles ; en d’autres termes, tout module fourni par Adobe ou tout module tiers actuellement disponible.

Certains modules ont des dépendances avec d’autres modules. Dans ce cas, vous ne pourrez peut-être pas activer ou désactiver un module en raison de ses dépendances avec d’autres modules.

En outre, des modules *en conflit* peuvent ne pas pouvoir être activés tous les deux en même temps.

Exemples :

* Le module A dépend du module B. Vous ne pouvez pas désactiver le module B à moins de désactiver le module A au préalable.

* Le module A dépend du module B, tous deux désactivés. Vous devez activer le module B avant de pouvoir activer le module A.

* Le module A est en conflit avec le module B. Vous pouvez désactiver les modules A et B, ou vous pouvez désactiver l’un ou l’autre des modules mais vous *ne pouvez pas* activer les modules A et B en même temps.

* Les dépendances sont déclarées dans le champ `require` du fichier `composer.json` d’Adobe Commerce pour chaque module. Les conflits sont déclarés dans le champ `conflict` des fichiers `composer.json` des modules. Nous utilisons ces informations pour créer un graphique de dépendance : `A->B` signifie que le module A dépend du module B.

* Une *chaîne de dépendance* est le chemin d’accès d’un module à un autre. Par example, si le module A dépend du module B et que le module B dépend du module C, alors la chaîne de dépendance est `A->B->C`.

Si vous tentez d’activer ou de désactiver un module qui dépend d’autres modules, le graphique de dépendance s’affiche dans le message d’erreur.

>[!NOTE]
>
>Il est possible que la `composer.json` du module A déclare un conflit avec le module B, mais pas l&#39;inverse.

*Ligne de commande uniquement :* pour forcer l’activation ou la désactivation d’un module, quelles que soient ses dépendances, utilisez l’argument facultatif `--force`.

>[!NOTE]
>
>L’utilisation de `--force` peut désactiver votre boutique et entraîner des problèmes d’accès à Admin.
