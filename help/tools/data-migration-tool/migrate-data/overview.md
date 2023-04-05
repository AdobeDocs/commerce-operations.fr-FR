---
title: Présentation de la migration
description: Découvrez comment commencer la migration des données de Magento 1 vers Magento 2 avec le [!DNL Data Migration Tool].
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '303'
ht-degree: 0%

---


# Présentation de la migration

Avant de commencer la migration, arrêtez toutes les tâches Magento 1 cron.

Lors du processus de migration, suivez les règles générales suivantes pour réussir la migration :

1. **Ne pas** Apportez des modifications à l’administrateur Magento 1, à l’exception de la gestion des commandes (expédition, création de factures et d’annotations de crédit).
1. **Ne pas** modifier n’importe quel code ;
1. **Ne pas** Apportez des modifications à l’administrateur et au storefront de Magento 2.

>[!TIP]
>
>Toutes les opérations dans le storefront Magento 1 sont autorisées.

## Exécutez la variable [!DNL Data Migration Tool]

Cette section explique comment exécuter la variable [!DNL Data Migration Tool] pour migrer les paramètres, les données ou les modifications incrémentielles.

### Premières étapes

1. Connectez-vous au serveur d’applications en tant qu’utilisateur ou passez à un utilisateur autorisé à écrire sur le système de fichiers. Voir [passer au propriétaire du système de fichiers](../../../installation/prerequisites/file-system/overview.md).

   Si vous utilisez le shell bash, vous pouvez utiliser la syntaxe suivante pour basculer vers le propriétaire du système de fichiers et saisir la commande en même temps :

   ```bash
   su <file system owner> -s /bin/bash -c <command>
   ```

   Si le propriétaire du système de fichiers n’autorise pas les connexions, vous pouvez effectuer les opérations suivantes :

   ```bash
   sudo -u <file system owner>  <command>
   ```

1. Pour exécuter des commandes de Magento depuis n’importe quel répertoire, ajoutez `<magento_root>/bin` sur votre système `PATH`.

   Les shells ayant une syntaxe différente, consultez une référence comme [unix.stackexchange.com](https://unix.stackexchange.com/questions/117467/how-to-permanently-set-environmental-variables).

   Exemple de shell bash pour CentOS :

   ```bash
   export PATH=$PATH:/var/www/html/magento2/bin
   ```

   Vous pouvez éventuellement exécuter les commandes comme suit :

   - `cd <magento_root>/bin` et exécutez-les comme `./magento <command name>`
   - `<magento_root>/bin/magento <command name>`
   - `<magento_root>` est un sous-répertoire de votre serveur web docroot.

### Syntaxe de commande

Voici un exemple de commande type :

```bash
bin/magento migrate:<mode> [-r|--reset] [-a|--auto] {<path to config.xml>}
```

Où :

- `<mode>` peut être : [`settings`](settings.md), [`data`](data.md)ou [`delta`](delta.md)
- `[-r|--reset]` est un argument facultatif qui lance la migration à partir du début. Vous pouvez utiliser cet argument pour tester la migration.
- `[-a|--auto]` est un argument facultatif qui empêche l’arrêt de la migration lorsqu’elle rencontre des erreurs de vérification d’intégrité.
- `{<path to config.xml>}` est le chemin d’accès absolu au système de fichiers vers `config.xml`; cet argument est obligatoire.

>[!NOTE]
>
>Les journaux sont écrits dans la variable `<magento_root>/var/` répertoire .


## Ordre de migration

Lorsque nous avons créé la variable [!DNL Data Migration Tool], nous avons supposé la séquence de transfert de données suivante :

1. [Paramètres](settings.md)
1. [Données](data.md)
1. [Modifications](delta.md)

Nous vous recommandons vivement de migrer les données dans le même ordre.
