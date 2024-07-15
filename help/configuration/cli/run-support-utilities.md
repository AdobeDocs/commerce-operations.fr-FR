---
title: Exécution des utilitaires de support
description: Résolution des problèmes liés à votre projet Commerce à l’aide de l’utilitaire de prise en charge intégré.
exl-id: 021b795f-e00d-43b5-9cbb-5b57a4795be7
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '461'
ht-degree: 0%

---

# Exécution des utilitaires de support

{{ee-only}}

{{file-system-owner}}

Les utilitaires de support Adobe Commerce, également appelés [Collecteur de données](https://docs.magento.com/user-guide/system/support-data-collector.html), permettent aux utilisateurs de collecter des informations de dépannage sur votre système qui peuvent être utilisées par notre équipe de support.

Adobe Commerce utilise ces sauvegardes, également appelées _dumps_, pour analyser les problèmes qui nécessitent l’accès à votre code. Voici un scénario type :

1. Vous rencontrez un problème avec votre boutique Commerce et vous contactez l’assistance Adobe Commerce.
1. L’assistance détermine qu’ils doivent voir votre code ou votre base de données pour reproduire le problème.
1. Vous sauvegardez le code dans un fichier `.tar.gz`.

   Cette sauvegarde _exclut vos fichiers multimédias afin d’accélérer le processus et d’obtenir un fichier beaucoup plus petit.

1. Vous sauvegardez la base de données dans un fichier `.tar.gz`.

   Par défaut, les données sensibles sont hachées lors de la sauvegarde.

1. Vous transférez vos sauvegardes vers un service de partage de fichiers.
1. L’assistance analyse vos problèmes sans affecter votre environnement de développement ou de production.

L’exécution des utilitaires peut prendre plusieurs minutes.

## Création d’une sauvegarde de code

Cette commande sauvegarde le code et le compresse au format `tar.gz`.

{{tip-backup-command}}

Options de commande :

```bash
bin/magento support:backup:code [--name=<file name>] [-o|--output=<path>] [-l|--logs]
```

Où :

- **`--name`** spécifie le nom de fichier de vidage (facultatif). Si vous omettez ce paramètre, le fichier de vidage est horodaté et horodaté.
- **`-o|--output=<path>`** est le chemin d’accès absolu au système de fichiers pour stocker la sauvegarde (obligatoire).
- **`-l|--logs`** comprend des fichiers journaux (facultatif).

Par exemple, pour créer une sauvegarde de code nommée `/var/www/html/magento2/var/log/mycodebackup.tar.gz` :

```bash
bin/magento support:backup:code --name mycodebackup -o /var/www/html/magento2/var/log
```

Une fois la commande terminée, effectuez la sauvegarde du code auprès de l’assistance Adobe Commerce.

## Création d’une sauvegarde de base de données

Cette commande sauvegarde la base de données Commerce et la compresse au format `tar.gz`.

{{tip-backup-command}}

Options de commande :

```bash
bin/magento support:backup:db [--name=<name>] [-o|--output=<path>] [-l|--logs] [-i|--ignore-sanitize]
```

Où :

- **`--name`** spécifie le nom de fichier de vidage (facultatif). Si vous omettez ce paramètre, le fichier de vidage est horodaté et horodaté.
- **`-o|--output=<path>` est le chemin d’accès absolu au système de fichiers pour stocker la sauvegarde (obligatoire).
- **`-l|--logs`** comprend des fichiers journaux (facultatif).
- **`-i|--ignore-sanitize`** signifie que les données sont conservées ; omettez l’indicateur pour hacher les données sensibles stockées dans la base de données lors de la création de la sauvegarde (facultatif).

Les données sensibles incluent des informations sur les clients provenant des tables de base de données suivantes :

```terminal
'customer_entity',
'customer_entity_varchar',
'customer_address_entity',
'customer_address_entity_varchar',
'customer_grid_flat',
'quote',
'quote_address',
'sales_order',
'sales_order_address',
'sales_order_grid'
```

Une fois la commande terminée, effectuez la sauvegarde de la base de données auprès du support Adobe Commerce.

## Dépannage : utilitaires d’affichage et chemins d’accès

Nous fournissons des commandes qui affichent les chemins d’accès aux utilitaires requis par le collecteur de données et la ligne de commande. Vous pouvez utiliser ces commandes, par exemple, si des erreurs comme celle-ci s’affichent dans l’Admin ou sur la ligne de commande :

```terminal
Utility lsof not found
```

Exécutez les commandes suivantes dans l’ordre indiqué pour afficher les chemins d’accès aux applications utilisées par les utilitaires de support et le collecteur de données :

1. Accédez au répertoire d’installation de Commerce.

   Par exemple, `cd /var/www/magento2`

   >[!INFO]
   >
   >Les commandes s’exécutent correctement _uniquement_ à partir du répertoire d’installation.

1. `bin/magento support:utility:paths` crée `<magento_root>/var/support/Paths.php`, qui répertorie les chemins d’accès à toutes les applications utilisées par l’utilitaire.
1. `bin/magento support:utility:check` affiche les chemins d’accès au système de fichiers.

Voici un exemple :

```terminal
   gzip => /bin/gzip
   lsof => /usr/sbin/lsof
   mysqldump => /usr/bin/mysqldump
   nice => /bin/nice
   php => /usr/bin/php
   tar => /bin/tar
   sed => /bin/sed
   bash => /bin/bash
   mysql => /usr/bin/mysql
```

Pour résoudre les problèmes liés à l’exécution des outils, assurez-vous que ces applications sont installées et se trouvent dans la variable d’environnement `$PATH` de l’utilisateur du serveur web.
