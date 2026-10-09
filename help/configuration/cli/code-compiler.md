---
title: Compilateur de code
description: Découvrez comment exécuter le compilateur de code Adobe Commerce à partir de la ligne de commande. Découvrez les processus de compilation et les techniques d’optimisation.
exl-id: 08dbf808-ea79-4956-a0bc-f464bb80eee7
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '184'
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

Vous trouverez des classes de compilation de code dans l’espace de noms [](https://github.com/magento/magento2/blob/2.4.8/setup/src/Magento/Setup/Module/Di/App/Task/Operation).

Pour exécuter le compilateur à client(e) unique :

```shell
bin/magento setup:di:compile
```

```text
Generated code and dependency injection configuration successfully.
```

Pour compiler le code avant d’installer l’application Commerce :

Dans certains cas, il se peut que vous souhaitiez compiler le code avant d’installer l’application Commerce.

1. Activez les modules.

   ```shell
   bin/magento module:enable --all [-c|--clear-static-content]
   ```

   Utilisez l’option `[-c|--clear-static-content]` pour effacer le contenu statique. Cela est nécessaire si vous avez précédemment activé ou désactivé des modules et que vous devez effacer le contenu statique précédemment généré pour eux.

   Voir [Activation des modules](../../installation/tutorials/manage-modules.md).

1. Compilez le code.

   ```shell
   bin/magento setup:di:compile
   ```

   ```text
   Generated code and dependency injection configuration successfully.
   ```

Pour compiler le code sans base de données, voir [Déployer des fichiers de vue statiques sans installer Magento](../cli/static-view-file-deployment.md).

