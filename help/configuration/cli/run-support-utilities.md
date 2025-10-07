---
title: Exécution des utilitaires d’assistance
description: Découvrez comment exécuter des utilitaires d’assistance pour résoudre les problèmes liés à votre projet Adobe Commerce. Découvrez les outils de diagnostic et de support intégrés.
exl-id: 021b795f-e00d-43b5-9cbb-5b57a4795be7
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '470'
ht-degree: 0%

---

# Exécution des utilitaires d’assistance

{{ee-only}}

{{file-system-owner}}

Les utilitaires d’assistance Adobe Commerce (également appelés collecteurs de données[&#x200B; &#x200B;](https://experienceleague.adobe.com/fr/docs/commerce-admin/systems/tools/support#data-collector) permettent aux utilisateurs de collecter des informations de dépannage sur votre système, que notre équipe d’assistance peut utiliser.

Adobe Commerce utilise ces sauvegardes, également appelées _vidages_, pour analyser les problèmes qui nécessitent l’accès à votre code. Voici un scénario type :

1. Vous rencontrez un problème avec votre boutique Commerce et vous contactez l’assistance Adobe Commerce.
1. L’assistance détermine qu’ils ont besoin de voir votre code ou votre base de données pour reproduire le problème.
1. Vous sauvegardez le code dans un fichier `.tar.gz`.

   Cette sauvegarde _exclut vos fichiers multimédias afin d’accélérer le processus et d’obtenir un fichier beaucoup plus petit.

1. Vous sauvegardez la base de données dans un fichier `.tar.gz`.

   Par défaut, les données sensibles sont hachées lors de la sauvegarde.

1. Vous chargez vos sauvegardes vers un service de partage de fichiers.
1. L’assistance analyse vos problèmes sans affecter votre environnement de développement ou de production.

Les utilitaires peuvent prendre plusieurs minutes.

## Création d’une sauvegarde du code

Cette commande sauvegarde le code et le compresse au format `tar.gz`.

{{tip-backup-command}}

Options de commande :

```bash
bin/magento support:backup:code [--name=<file name>] [-o|--output=<path>] [-l|--logs]
```

Où :

- **`--name`** indique le nom du fichier de vidage (facultatif). Si vous omettez ce paramètre, le fichier de vidage est horodaté.
- **`-o|--output=<path>`** est le chemin d’accès absolu au système de fichiers pour stocker la sauvegarde (obligatoire).
- **`-l|--logs`** inclut les fichiers journaux (facultatif).

Par exemple, pour créer une sauvegarde de code nommée `/var/www/html/magento2/var/log/mycodebackup.tar.gz` :

```bash
bin/magento support:backup:code --name mycodebackup -o /var/www/html/magento2/var/log
```

Une fois la commande terminée, fournissez la sauvegarde du code au support Adobe Commerce.

## Création d’une sauvegarde de base de données

Cette commande sauvegarde la base de données Commerce et la compresse au format `tar.gz`.

{{tip-backup-command}}

Options de commande :

```bash
bin/magento support:backup:db [--name=<name>] [-o|--output=<path>] [-l|--logs] [-i|--ignore-sanitize]
```

Où :

- **`--name`** indique le nom du fichier de vidage (facultatif). Si vous omettez ce paramètre, le fichier de vidage est horodaté.
- **`-o|--output=<path>` est le chemin d’accès absolu au système de fichiers pour stocker la sauvegarde (obligatoire).
- **`-l|--logs`** inclut les fichiers journaux (facultatif).
- **`-i|--ignore-sanitize`** signifie que les données sont conservées ; omettez l’indicateur pour hacher les données sensibles stockées dans la base de données lors de la création de la sauvegarde (facultatif).

Les données sensibles incluent des informations client provenant des tables de base de données suivantes :

```
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

Une fois la commande terminée, fournissez la sauvegarde de la base de données au support Adobe Commerce.

## Dépannage : utilitaires d’affichage et chemins d’accès

Nous fournissons des commandes qui affichent les chemins d’accès aux utilitaires requis par le collecteur de données et la ligne de commande. Vous pouvez utiliser ces commandes, par exemple, si des erreurs telles que celles-ci s’affichent dans l’interface d’administration ou sur la ligne de commande :

```
Utility lsof not found
```

Exécutez les commandes suivantes dans l’ordre indiqué pour afficher les chemins d’accès aux applications utilisées par les utilitaires de prise en charge et le collecteur de données :

1. Modifiez votre répertoire d’installation Commerce.

   Par exemple, `cd /var/www/magento2`

   >[!INFO]
   >
   >Les commandes s’exécutent correctement _uniquement_ à partir de votre répertoire d’installation.

1. `bin/magento support:utility:paths` crée des `<magento_root>/var/support/Paths.php` qui répertorient les chemins d’accès à toutes les applications utilisées par l’utilitaire.
1. `bin/magento support:utility:check` affiche les chemins d’accès au système de fichiers.

Voici un exemple :

```
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

Pour résoudre les problèmes d’exécution des outils, assurez-vous que ces applications sont installées et se trouvent dans la variable d’environnement `$PATH` de l’utilisateur ou de l’utilisatrice du serveur web.
