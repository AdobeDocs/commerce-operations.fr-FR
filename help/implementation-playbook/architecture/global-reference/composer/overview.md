---
title: Développement de compositeur
description: Découvrez comment développer des modules de compositeur en place dans le répertoire "vendor/".
feature: Best Practices
role: Developer
source-git-commit: b4213c40fdf903fd962a15fc99b143f31aedbcde
workflow-type: tm+mt
source-wordcount: '273'
ht-degree: 0%

---


# Développement de compositeur

Cette rubrique décrit l’approche recommandée pour le développement statique des modules du compositeur (en tant que référentiels Git dans la variable `vendor/` ) et d’ajouter ces modules à votre projet Git principal.

>[!NOTE]
>
>Ces directives s’appliquent principalement aux [architecture de référence globale (GRA)](../overview.md) projets.

## Préparation d’une branche de développement

1. Créez ou extrayez la branche de développement dans votre référentiel Git principal.
1. Requiert des versions de développement pour chaque module que vous conservez.

   Dans cet exemple, chaque branche de votre référentiel Git principal représente une version de module Composer. La convention d’affectation de nom recommandée pour les versions du compositeur dans ce scénario est la suivante : `dev-` suivi du nom de la branche. Par exemple :

   - `dev-develop`
   - `dev-qa`

   ```bash
   composer require client/module-example:dev-develop
   ```

1. Si un autre module de compositeur nécessite une version spécifique d’un module (par exemple : `client/module-example 1.0.12`), installez-le avec un alias :

   ```bash
   composer require 'client/module-example:dev-develop as 1.0.12'
   ```

   Pour le `qa` branche, remplacer `dev-develop` avec `dev-qa`.

## Conversion de modules en référentiels Git

Par défaut, les modules ne contiennent pas de `.git/` répertoire . Le compositeur peut extraire des modules à partir de Git au lieu d’utiliser les modules prédéfinis du compositeur. L’avantage de cette approche est que vous pouvez facilement modifier les packages pendant le développement.

1. Supprimez le module de la fonction `vendor/` répertoire .

   ```bash
   rm -rf vendor/client/module-example
   ```

1. Réinstallez le module à l’aide du [source Git spécifiée](#prepare-a-development-branch).

   ```bash
   composer install --prefer-source
   ```

1. Vérifiez que le package du compositeur est désormais un référentiel Git :

   ```bash
   cd vendor/client/module-example
   git remote -v
   ```

1. Pour convertir par lots plusieurs modules en référentiels Git (par exemple, modules &quot;client&quot;) :

   ```bash
   rm -rf vendor/client
   composer install --prefer-source
   ```

## Démarrer le développement

1. Créez ou extrayez une branche de fonction/de travail. L’exemple suivant montre une branche portant le même nom qu’un ticket Jira.

   ```bash
   cd vendor/client/module-example
   git checkout master
   git checkout -b JIRA-1200
   ```

1. Après avoir modifié des branches dans un module, voir les modifications en vidant le cache Adobe Commerce et le contenu statique.

   ```bash
   bin/magento cache:flush
   bin/magento module:enable --all --clear-static-content
   ```

## Mettre à jour le projet principal avec votre développement

Mettez à jour votre référentiel Git principal en modifiant les `composer.lock` fichier . Si votre module est nouveau, activez-le.

```bash
# to update your packages and all dependencies of the package
composer update --with-all-dependencies client/module-example
# to update just your package
composer update client/module-example
 
bin/magento module:enable Client_ModuleExample
git add composer.lock app/etc/config.php
git commit
```
