---
title: Compilateur de code
description: Découvrez comment exécuter le compilateur de code Adobe Commerce à partir de la ligne de commande. Découvrez les processus de compilation et les techniques d’optimisation.
exl-id: 08dbf808-ea79-4956-a0bc-f464bb80eee7
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '169'
ht-degree: 0%

---

# Compilateur de code

{{file-system-owner}}

La compilation de code comprend les éléments suivants (dans un ordre particulier) :

- Génération du code de l’application (usines, serveurs proxy)
- Agrégation des configurations de zone (configurations d&#39;injection de dépendance optimisées par zone)
- Génération d&#39;intercepteurs (génération de code optimisée d&#39;intercepteurs)
- Génération du cache d&#39;interception
- Génération du code des référentiels (code généré pour les API)
- Génération des attributs de données de service (classes d’extension générées pour les objets de données)

Vous trouverez des classes de compilation de code dans l’espace de noms [\Magento\Setup\Module\Di\App\Task\Operation][operation].

Pour exécuter le compilateur à client(e) unique :

```bash
bin/magento setup:di:compile
```

```
Generated code and dependency injection configuration successfully.
```

Pour compiler le code avant d’installer l’application Commerce :

Dans certains cas, il se peut que vous souhaitiez compiler le code avant d’installer l’application Commerce.

1. Activez les modules.

   ```bash
   bin/magento module:enable --all [-c|--clear-static-content]
   ```

   Utilisez l’option `[-c|--clear-static-content]` pour effacer le contenu statique. Cela est nécessaire si vous avez précédemment activé ou désactivé des modules et que vous devez effacer le contenu statique précédemment généré pour eux.

   Voir [Activation des modules](../../installation/tutorials/manage-modules.md).

1. Compilez le code.

   ```bash
   bin/magento setup:di:compile
   ```

   ```
   Generated code and dependency injection configuration successfully.
   ```

Pour compiler le code sans base de données, voir [Déployer des fichiers d’affichage statiques sans installer Magento](../cli/static-view-file-deployment.md).

<!-- link definitions -->

[operation]: https://github.com/magento/magento2/blob/2.4/setup/src/Magento/Setup/Module/Di/App/Task/Operation
