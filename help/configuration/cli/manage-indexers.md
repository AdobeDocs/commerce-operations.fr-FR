---
title: Gestion des indexeurs
description: Consultez des exemples d’affichage et de gestion des indexeurs de commerce.
source-git-commit: 8102c083bb0216bbdcad2882f39f7711b9cee52b
workflow-type: tm+mt
source-wordcount: '626'
ht-degree: 0%

---


# Gestion des indexeurs

{{file-system-owner}}

Pour afficher une liste de tous les indexeurs :

```bash
bin/magento indexer:info
```

La liste se présente comme suit :

```terminal
design_config_grid                       Design Config Grid
customer_grid                            Customer Grid
catalog_category_product                 Category Products
catalog_product_category                 Product Categories
catalogrule_rule                         Catalog Rule Product
catalog_product_attribute                Product EAV
inventory                                Inventory
catalogrule_product                      Catalog Product Rule
cataloginventory_stock                   Stock
targetrule_product_rule                  Product/Target Rule
targetrule_rule_product                  Target Rule/Product
catalog_product_price                    Product Price
catalogsearch_fulltext                   Catalog Search
salesrule_rule                           Sales Rule
```

## Affichage de l’état de l’indexeur

Utilisez cette commande pour afficher l’état de tous les indexeurs ou des indexeurs spécifiques. Par exemple, découvrez si un indexeur doit être réindexé.

Options de commande :

```bash
bin/magento indexer:status [indexer]
```

Où `[indexer]` est une liste d’indexeurs séparés par des espaces. Omit `[indexer]` pour afficher l’état de tous les indexeurs.

Exemple de résultat :

```terminal
+----------------------+------------------+-----------+---------------------+---------------------+
| Title                | Status           | Update On | Schedule Status     | Schedule Updated    |
+----------------------+------------------+-----------+---------------------+---------------------+
| Catalog Product Rule | Reindex required | Save      |                     |                     |
| Catalog Rule Product | Reindex required | Save      |                     |                     |
| Catalog Search       | Ready            | Save      |                     |                     |
| Category Products    | Reindex required | Schedule  | idle (0 in backlog) | 2021-06-28 09:45:53 |
| Customer Grid        | Ready            | Schedule  | idle (0 in backlog) | 2021-06-28 09:45:52 |
| Design Config Grid   | Ready            | Schedule  | idle (0 in backlog) | 2018-06-28 09:45:52 |
| Inventory            | Ready            | Save      |                     |                     |
| Product Categories   | Reindex required | Schedule  | idle (0 in backlog) | 2021-06-28 09:45:53 |
| Product EAV          | Reindex required | Save      |                     |                     |
| Product Price        | Reindex required | Save      |                     |                     |
| Stock                | Reindex required | Save      |                     |                     |
+----------------------+------------------+-----------+---------------------+---------------------+
```

## Reindex

Utilisez cette commande pour réindexer tous les indexeurs ou certains indexeurs une seule fois.

>[!INFO]
>
>Cette commande effectue de nouveaux index une seule fois. Pour que les indexeurs soient à jour, vous devez configurer une [tâche cron](../cli/configure-cron-jobs.md).

Options de commande :

```bash
bin/magento indexer:reindex [indexer]
```

Où `[indexer]` est une liste d’indexeurs séparés par des espaces. Omit `[indexer]` pour réindexer tous les indexeurs.

Exemple de résultat :

```terminal
Design Config Grid index has been rebuilt successfully in <time>
Customer Grid index has been rebuilt successfully in <time>
Category Products index has been rebuilt successfully in <time>
Product Categories index has been rebuilt successfully in <time>
Catalog Rule Product index has been rebuilt successfully in <time>
Product EAV index has been rebuilt successfully in <time>
Inventory index has been rebuilt successfully in <time>
Catalog Product Rule index has been rebuilt successfully in <time>
Stock index has been rebuilt successfully in <time>
Product Price index has been rebuilt successfully in <time>
Catalog Search index has been rebuilt successfully in <time>
```

>[!INFO]
>
>La réindexation de tous les indexeurs peut prendre un certain temps pour les magasins comportant un grand nombre de produits, de clients, de catégories et de règles promotionnelles.

### Réindexation en mode parallèle

Les indexeurs sont définis et multithreads pour prendre en charge la réindexation en mode parallèle. Il se met en parallèle par la dimension de l’indexeur et s’exécute sur plusieurs threads, ce qui réduit le temps de traitement.

Dans ce contexte, `dimension` est la portée de la réindexation, par exemple une `website` ou uniquement une `customer_group`.

La parallélisation des index affecte uniquement les indexeurs ciblés, ce qui signifie que Commerce divise les données en plusieurs tables à l’aide de l’indexeur comme portée au lieu de conserver toutes les données dans une seule table.

Vous pouvez exécuter les index suivants en mode parallèle :

- `Catalog Search Fulltext` peut être mis en parallèle par les vues des magasins.
- `Category Product` peut être mis en parallèle par les vues des magasins.
- `Catalog Price` peut être mis en parallèle par le site web et les groupes de clients.
- `Catalog Permissions` peut être mis en parallèle par des groupes de clients.

Pour utiliser la mise en parallèle, définissez l’un des modes de dimensions disponibles pour l’indexeur de prix de produit :

- `none` (par défaut)
- `website`
- `customer_group`
- `website_and_customer_group`

Par exemple, pour définir le mode par site web :

```bash
bin/magento indexer:set-dimensions-mode catalog_product_price website
```

Pour utiliser la mise en parallèle pour les autorisations de catalogue, définissez l’un des modes de dimensions disponibles pour l’indexeur d’autorisations de catalogue :

- `none` (par défaut)
- `customer_group`

Ou pour vérifier le mode actuel :

```bash
bin/magento indexer:show-dimensions-mode
```

Pour réindexer en mode parallèle, exécutez la commande reindex à l’aide de la variable d’environnement. `MAGE_INDEXER_THREADS_COUNT`ou ajoutez une variable d’environnement à la variable `env.php` fichier . Cette variable définit le nombre de threads pour le traitement de réindexation.

Par exemple, la commande suivante exécute la fonction `Catalog Search Fulltext` indexeur sur trois threads :

```bash
MAGE_INDEXER_THREADS_COUNT=3 php -f bin/magento indexer:reindex catalogsearch_fulltext
```

## Réinitialiser l’indexeur

Utilisez cette commande pour invalider l’état de tous les indexeurs ou de certains indexeurs.

Options de commande :

```bash
bin/magento indexer:reset [indexer]
```

Où ```[indexer]``` est une liste d’indexeurs séparés par des espaces. Omit `[indexer]` pour invalider tous les indexeurs.

Exemple de résultat :

```terminal
Design Config Grid indexer has been invalidated.
Customer Grid indexer has been invalidated.
Category Products indexer has been invalidated.
Product Categories indexer has been invalidated.
Catalog Rule Product indexer has been invalidated.
Product EAV indexer has been invalidated.
Inventory indexer has been invalidated.
Catalog Product Rule indexer has been invalidated.
Stock indexer has been invalidated.
Product Price indexer has been invalidated.
Catalog Search indexer has been invalidated.
```

## Configuration des indexeurs

Utilisez cette commande pour définir les options d’indexeur suivantes :

- **Mise à jour lors de l’enregistrement (`realtime`)**: Les données indexées sont mises à jour lorsqu’une modification est apportée à l’administrateur. (Par exemple, l’index des produits de catégorie est réindexé une fois les produits ajoutés à une catégorie dans l’administrateur.) Il s’agit de la valeur par défaut.
- **Mise à jour par planification (`schedule`)**: Les données sont indexées selon le planning défini par votre tâche cron.

[En savoir plus sur l’indexation](https://developer.adobe.com/commerce/php/development/components/indexing/).

### Afficher la configuration actuelle

Pour afficher la configuration actuelle de l’indexeur :

```bash
bin/magento indexer:show-mode [indexer]
```

Où `[indexer]` est une liste d’indexeurs séparés par des espaces. Omit `[indexer]` pour afficher tous les modes des indexeurs. Par exemple, pour afficher le mode de tous les indexeurs :

Exemple de résultat :

```terminal
Design Config Grid:                                Update on Save
Customer Grid:                                     Update on Save
Category Products:                                 Update on Save
Product Categories:                                Update on Save
Catalog Rule Product:                              Update on Save
Product EAV:                                       Update on Save
Inventory:                                         Update on Save
Catalog Product Rule:                              Update on Save
Stock:                                             Update on Save
Product Price:                                     Update on Save
Catalog Search:                                    Update on Save
```

### Configuration des indexeurs

>[!INFO]
>
>Avant de basculer entre les modes indexeur, il est conseillé de placer votre site web sur [maintenance](../../installation/tutorials/maintenance-mode.md) mode et [Désactivation des tâches cron](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/app/properties/crons-property.html#disable-cron-jobs). Cela vous évite de subir les verrous de base de données.

Pour spécifier la configuration de l’indexeur :

```bash
bin/magento indexer:set-mode {realtime|schedule} [indexer]
```

Où :

- `realtime`: définit les indexeurs sélectionnés à mettre à jour lors de l’enregistrement.
- `schedule`: définit les indexeurs spécifiés à enregistrer selon le planning cron.
- `indexer`: il s’agit d’une liste d’indexeurs séparés par des espaces. Omit `indexer` pour configurer tous les indexeurs de la même manière.

Par exemple, pour modifier uniquement les indexeurs de catégories de produits et de catégories de produits à mettre à jour selon le calendrier, saisissez :

```bash
bin/magento indexer:set-mode schedule catalog_category_product catalog_product_category
```

Exemple de résultat :

```terminal
Index mode for Indexer Category Products was changed from 'Update on Save' to 'Update by Schedule'
Index mode for Indexer Product Categories was changed from 'Update on Save' to 'Update by Schedule'
```

Les déclencheurs de base de données liés aux indexeurs sont ajoutés lorsque le mode indexeur est défini sur `schedule` et supprimé lorsque le mode indexeur est défini sur `realtime`. Si les déclencheurs sont manquants dans votre base de données alors que les indexeurs sont définis sur `schedule`, remplacez les indexeurs par `realtime` puis les redéfinissez sur `schedule`. Cela réinitialise les déclencheurs.
