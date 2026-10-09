---
title: Présentation de la migration
description: Découvrez comment commencer à migrer des données de Magento 1 vers Magento 2 avec le [!DNL Data Migration Tool].
exl-id: b775ede1-9d1d-49d5-ad0f-763404b48278
topic: Commerce, Migration
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
source-wordcount: '315'
ht-degree: 0%
---
# Présentation de la migration

Avant de commencer la migration, arrêtez toutes les tâches cron de Magento 1.

Pendant le processus de migration, suivez les règles générales suivantes pour réussir la migration :

1. **N’apportez pas** modifications à l’administrateur Magento 1, à l’exception de la gestion des commandes (expédition, création de factures et d’avoirs).
1. **Ne modifiez** code
1. **N’apportez pas** modifications à l’administration et au storefront Magento 2.

>[!TIP]
>
>Toutes les opérations dans le storefront Magento 1 sont autorisées.

## Exécuter le [!DNL Data Migration Tool]

Cette section explique comment exécuter le [!DNL Data Migration Tool] pour migrer les paramètres, les données ou les modifications incrémentielles.

### Premières étapes

1. Connectez-vous au serveur d’applications en tant qu’utilisateur ou en tant qu’utilisateur disposant des autorisations d’écriture sur le système de fichiers. Voir [passer au propriétaire du système de fichiers](../../../installation/prerequisites/file-system/overview.md).

   Si vous utilisez le shell bash, vous pouvez utiliser la syntaxe suivante pour passer au propriétaire du système de fichiers et saisir simultanément la commande :

   ```shell
   su <file system owner> -s /bin/bash -c <command>
   ```

   Si le propriétaire du système de fichiers n’autorise pas les connexions, vous pouvez effectuer les opérations suivantes :

   ```shell
   sudo -u <file system owner>  <command>
   ```

1. Pour exécuter des commandes Magento à partir de n’importe quel répertoire, ajoutez des `<magento_root>/bin` à votre `PATH` système.

   Étant donné que les shell ont une syntaxe différente, consultez une référence telle que [unix.stackexchange.com](https://unix.stackexchange.com/questions/117467/how-to-permanently-set-environmental-variables).

   Exemple de shell Bash pour CentOS :

   ```shell
   export PATH=$PATH:/var/www/html/magento2/bin
   ```

   Vous pouvez éventuellement exécuter les commandes des manières suivantes :

   - `cd <magento_root>/bin` et exécutez-les en tant que `./magento <command name>`
   - `<magento_root>/bin/magento <command name>`
   - `<magento_root>` est un sous-répertoire de la racine docroot de votre serveur web.

### Syntaxe des commandes

Voici un exemple de commande type :

```shell
bin/magento migrate:<mode> [-r|--reset] [-a|--auto] {<path to config.xml>}
```

Où :

- `<mode>` peut être : [`settings`](settings.md), [`data`](data.md) ou [`delta`](delta.md)
- `[-r|--reset]` est un argument facultatif qui lance la migration depuis le début. Vous pouvez utiliser cet argument pour tester la migration.
- `[-a|--auto]` est un argument facultatif qui empêche l’arrêt de la migration lorsqu’elle rencontre des erreurs de contrôle d’intégrité.
- `{<path to config.xml>}` est le chemin d’accès absolu au système de fichiers à `config.xml` ; cet argument est obligatoire.

>[!NOTE]
>
>Les journaux sont écrits dans le répertoire `<magento_root>/var/`.


## Ordre de migration

Lors de la création du [!DNL Data Migration Tool], nous avons supposé que la séquence de transfert de données suivante était active :

1. [Paramètres](settings.md)
1. [Données](data.md)
1. [Modifications](delta.md)

Nous vous recommandons vivement de migrer les données dans le même ordre.
