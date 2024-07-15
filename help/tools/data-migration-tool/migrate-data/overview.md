---
title: Présentation de la migration
description: Découvrez comment commencer la migration des données du Magento 1 vers le Magento 2 avec le  [!DNL Data Migration Tool].
exl-id: b775ede1-9d1d-49d5-ad0f-763404b48278
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '306'
ht-degree: 0%

---

# Présentation de la migration

Avant de commencer la migration, arrêtez toutes les tâches Magento 1 cron.

Lors du processus de migration, suivez les règles générales suivantes pour réussir la migration :

1. **N’effectuez pas** de modifications dans l’administrateur Magento 1, à l’exception de la gestion des commandes (expédition, création de factures et de notes de crédit).
1. **Ne modifiez pas** le code
1. **N’effectuez pas** de modifications dans l’administrateur et le storefront de Magento 2

>[!TIP]
>
>Toutes les opérations dans le storefront Magento 1 sont autorisées.

## Exécutez le [!DNL Data Migration Tool]

Cette section explique comment exécuter le [!DNL Data Migration Tool] pour migrer les paramètres, les données ou les modifications incrémentielles.

### Premières étapes

1. Connectez-vous au serveur d’applications en tant qu’utilisateur ou passez à un utilisateur autorisé à écrire sur le système de fichiers. Voir [basculement vers le propriétaire du système de fichiers](../../../installation/prerequisites/file-system/overview.md).

   Si vous utilisez le shell bash, vous pouvez utiliser la syntaxe suivante pour basculer vers le propriétaire du système de fichiers et saisir la commande en même temps :

   ```bash
   su <file system owner> -s /bin/bash -c <command>
   ```

   Si le propriétaire du système de fichiers n’autorise pas les connexions, vous pouvez effectuer les opérations suivantes :

   ```bash
   sudo -u <file system owner>  <command>
   ```

1. Pour exécuter des commandes de Magento depuis n’importe quel répertoire, ajoutez `<magento_root>/bin` à votre système `PATH`.

   Les shells ayant une syntaxe différente, consultez une référence telle que [unix.stackexchange.com](https://unix.stackexchange.com/questions/117467/how-to-permanently-set-environmental-variables).

   Exemple de shell bash pour CentOS :

   ```bash
   export PATH=$PATH:/var/www/html/magento2/bin
   ```

   Vous pouvez éventuellement exécuter les commandes comme suit :

   - `cd <magento_root>/bin` et exécutez-les comme `./magento <command name>`
   - `<magento_root>/bin/magento <command name>`
   - `<magento_root>` est un sous-répertoire de votre serveur web docroot.

### Syntaxe de la commande

Voici un exemple de commande type :

```bash
bin/magento migrate:<mode> [-r|--reset] [-a|--auto] {<path to config.xml>}
```

Où :

- `<mode>` peut être : [`settings`](settings.md), [`data`](data.md) ou [`delta`](delta.md)
- `[-r|--reset]` est un argument facultatif qui lance la migration à partir du début. Vous pouvez utiliser cet argument pour tester la migration.
- `[-a|--auto]` est un argument facultatif qui empêche l’arrêt de la migration lorsqu’elle rencontre des erreurs de vérification de l’intégrité.
- `{<path to config.xml>}` est le chemin d’accès absolu au système de fichiers `config.xml` ; cet argument est obligatoire.

>[!NOTE]
>
>Les journaux sont écrits dans le répertoire `<magento_root>/var/`.


## Ordre de migration

Lorsque nous avons créé le [!DNL Data Migration Tool], nous avons supposé la séquence de transfert de données suivante :

1. [Paramètres](settings.md)
1. [Données](data.md)
1. [Modifications](delta.md)

Nous vous recommandons vivement de migrer les données dans le même ordre.
