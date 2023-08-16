---
title: Compilateur de code
description: Découvrez comment exécuter le compilateur de code à partir de la ligne de commande.
exl-id: 08dbf808-ea79-4956-a0bc-f464bb80eee7
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '174'
ht-degree: 0%

---

# Compilateur de code

{{file-system-owner}}

La compilation de code comprend les éléments suivants (sans ordre particulier) :

- Génération de code d’application (usines, proxies)
- Agrégation de la configuration de zone (configurations d’injection de dépendance optimisées par zone)
- Génération d’intercepteurs (génération de code optimisée d’intercepteurs)
- Génération du cache d’interception
- Génération de code de référentiels (code généré pour les API)
- Génération d’attributs de données de service (classes d’extension générées pour les objets de données)

Vous trouverez les classes de compilation de code dans la variable [\Magento\Setup\Module\Di\App\Task\Operation][operation] espace de noms.

Pour exécuter le compilateur client unique :

```bash
bin/magento setup:di:compile
```

```terminal
Generated code and dependency injection configuration successfully.
```

Pour compiler le code avant d’installer l’application Commerce :

Dans certains cas, vous souhaiterez peut-être compiler le code avant d’installer l’application Commerce.

1. Activez les modules.

   ```bash
   bin/magento module:enable --all [-c|--clear-static-content]
   ```

   Utilisez la variable `[-c|--clear-static-content]` pour effacer le contenu statique. Cela est nécessaire si vous avez précédemment activé ou désactivé les modules et que vous devez effacer le contenu statique généré précédemment pour ceux-ci.

   Voir [Activation des modules](../../installation/tutorials/manage-modules.md).

1. Compilez le code.

   ```bash
   bin/magento setup:di:compile
   ```

   ```terminal
   Generated code and dependency injection configuration successfully.
   ```

Pour compiler du code sans base de données, voir [Déployer des fichiers d’affichage statique sans installer Magento](../cli/static-view-file-deployment.md).

<!-- link definitions -->

[operation]: https://github.com/magento/magento2/blob/2.4/setup/src/Magento/Setup/Module/Di/App/Task/Operation
