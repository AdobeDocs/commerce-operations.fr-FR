---
title: Gestion des indexeurs
description: Voir des exemples d’affichage et de gestion des indexeurs Commerce.
exl-id: d2cd1399-231e-4c42-aa0c-c2ed5d7557a0
source-git-commit: 5e1684d4d910f2ea52e12eeccdc291a54372f8d6
workflow-type: tm+mt
source-wordcount: '951'
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

>[!NOTE]
> Les marchands Adobe Commerce utilisant la recherche en direct, le service de catalogue ou le Recommendations de produits ont la possibilité d&#39;utiliser l&#39;[indexation de prix basée sur SaaS](https://experienceleague.adobe.com/docs/commerce-merchant-services/price-indexer/index.html).

## Afficher le statut de l’indexeur

Utilisez cette commande pour afficher l’état de tous les indexeurs ou des indexeurs spécifiques. Par exemple, découvrez si un indexeur doit être réindexé.

Options de commande :

```bash
bin/magento indexer:status [indexer]
```

Où `[indexer]` est une liste d’indexeurs séparés par des espaces. Omettez `[indexer]` pour afficher l’état de tous les indexeurs.

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
>Cette commande effectue de nouveaux index une seule fois. Pour maintenir les indexeurs à jour, vous devez configurer une [tâche cron](../cli/configure-cron-jobs.md).

Options de commande :

```bash
bin/magento indexer:reindex [indexer]
```

Où `[indexer]` est une liste d’indexeurs séparés par des espaces. Omettez `[indexer]` pour réindexer tous les indexeurs.

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

{{php-process-control}}

Les indexeurs sont définis et multithreads pour prendre en charge la réindexation en mode parallèle. Il se met en parallèle par la dimension de l’indexeur et s’exécute sur plusieurs threads, ce qui réduit le temps de traitement.

Dans ce contexte, `dimension` est la portée de la réindexation, par exemple un `website` ou un `customer_group` spécifique.

La parallélisation des index affecte uniquement les indexeurs ciblés, ce qui signifie que Commerce divise les données en plusieurs tables à l’aide de l’indexeur comme portée au lieu de conserver toutes les données dans une seule table.

Vous pouvez exécuter les index suivants en mode parallèle :

- `Catalog Search Fulltext` peut être mis en parallèle par les vues de magasin.
- `Category Product` peut être mis en parallèle par les vues de magasin.
- `Catalog Price` peut être mis en parallèle par le site web et les groupes de clients.
- `Catalog Permissions` peut être comparé par des groupes de clients.

>[!INFO]
>
>La mise en parallèle pour la recherche catalogue, le texte intégral et le produit de catégorie est activée par défaut.

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

Pour réindexer en mode parallèle, exécutez la commande reindex à l’aide de la variable d’environnement `MAGE_INDEXER_THREADS_COUNT` ou ajoutez une variable d’environnement au fichier `env.php`. Cette variable définit le nombre de threads pour le traitement de réindexation.

Par exemple, la commande suivante exécute l’indexeur `Catalog Search Fulltext` sur trois threads :

```bash
MAGE_INDEXER_THREADS_COUNT=3 php -f bin/magento indexer:reindex catalogsearch_fulltext
```

## Réinitialiser l’indexeur

Utilisez cette commande pour invalider l’état de tous les indexeurs ou de certains indexeurs.

Options de commande :

```bash
bin/magento indexer:reset [indexer]
```

Où ```[indexer]``` est une liste d’indexeurs séparés par des espaces. Omettez `[indexer]` pour invalider tous les indexeurs.

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

- **Mise à jour lors de l’enregistrement (`realtime`)** : les données indexées sont mises à jour lorsqu’une modification est apportée dans l’administrateur. (Par exemple, l’index des produits de catégorie est réindexé une fois les produits ajoutés à une catégorie dans l’administrateur.) Il s’agit du paramètre par défaut.
- **Mise à jour par planning (`schedule`)** : les données sont indexées selon le planning défini par votre tâche cron.

[En savoir plus sur l’indexation](https://developer.adobe.com/commerce/php/development/components/indexing/).

### Afficher la configuration actuelle

Pour afficher la configuration actuelle de l’indexeur :

```bash
bin/magento indexer:show-mode [indexer]
```

Où `[indexer]` est une liste d’indexeurs séparés par des espaces. Omettez `[indexer]` pour afficher tous les modes des indexeurs. Par exemple, pour afficher le mode de tous les indexeurs :

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

### Définition du mode indexeur

>[!IMPORTANT]
>
>Veillez à définir le [!DNL Customer Grid] avec `realtime` au lieu de `schedule`. [!DNL Customer Grid] ne peut être réindexé qu&#39;à l&#39;aide de l&#39;option [!UICONTROL Update on Save]. Cet index ne prend pas en charge l’option `Update by Schedule`. Utilisez la ligne de commande suivante pour définir cet indexeur à mettre à jour lors de l&#39;enregistrement : `php bin/magento indexer:set-mode realtime customer_grid`
>
>Voir [Bonnes pratiques pour la configuration de l’indexeur](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/maintenance/indexer-configuration.html) dans le _manuel d’implémentation_.

>[!INFO]
>
>Avant de passer en mode indexeur, définissez votre site web sur le mode [maintenance](../../installation/tutorials/maintenance-mode.md) et [désactiver les tâches cron](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/app/properties/crons-property.html#disable-cron-jobs). Cela vous évite de subir les verrous de base de données.

Pour spécifier la configuration de l’indexeur :

```bash
bin/magento indexer:set-mode {realtime|schedule} [indexer]
```

Où :

- `realtime` : définit les indexeurs sélectionnés à mettre à jour lors de l’enregistrement.
- `schedule` : définit les indexeurs spécifiés à enregistrer selon le planning cron.
- `indexer` : liste d’indexeurs séparés par des espaces. Omettez `indexer` pour configurer tous les indexeurs de la même manière.

Par exemple, pour modifier uniquement les indexeurs de catégories de produits et de catégories de produits à mettre à jour selon le calendrier, saisissez :

```bash
bin/magento indexer:set-mode schedule catalog_category_product catalog_product_category
```

Exemple de résultat :

```terminal
Index mode for Indexer Category Products was changed from 'Update on Save' to 'Update by Schedule'
Index mode for Indexer Product Categories was changed from 'Update on Save' to 'Update by Schedule'
```

Les déclencheurs de base de données liés aux indexeurs sont ajoutés lorsque le mode indexeur est défini sur `schedule` et supprimés lorsque le mode indexeur est défini sur `realtime`. Si les déclencheurs sont manquants dans votre base de données alors que les indexeurs sont définis sur `schedule`, remplacez les indexeurs par `realtime`, puis redéfinissez-les sur `schedule`. Cela réinitialise les déclencheurs.

### Définir l’état de l’indexeur

La commande `bin/magento indexer:set-status` a été introduite dans Adobe Commerce 2.4.7. Il permet aux administrateurs de modifier l’état opérationnel d’un ou de plusieurs indexeurs, en optimisant les performances du système lors d’opérations étendues telles que l’importation, la mise à jour ou la maintenance des données.

Syntaxe de la commande :

```bash
bin/magento indexer:set-status {invalid|suspended|valid} [indexer]
```

Où :

- `invalid` : désigne les indexeurs comme obsolètes, ce qui entraîne la réindexation lors de l’exécution suivante de cron, sauf s’ils sont suspendus.
- `suspended` : arrête temporairement les mises à jour automatiques déclenchées par cron pour les indexeurs. Ce statut s’applique aux modes temps réel et planification, ce qui garantit que les mises à jour automatiques sont suspendues pendant les opérations intensives.
- `valid` : indique que les données de l’indexeur sont à jour, sans qu’il faille procéder à une réindexation.
- `indexer` : liste d’indexeurs séparés par des espaces. Omettez `indexer` pour configurer tous les indexeurs de la même manière.

Par exemple, pour suspendre des indexeurs spécifiques, saisissez :

```bash
bin/magento indexer:set-status suspended catalog_category_product catalog_product_category
```

Exemple de résultat :

```terminal
Index status for Indexer 'Category Products' was changed from 'valid' to 'suspended'.
Index status for Indexer 'Product Categories' was changed from 'valid' to 'suspended'.
```

#### Gestion du statut de l’indexeur suspendu

Lorsqu’un indexeur est défini sur un état `suspended`, il affecte principalement la réindexation automatique et les mises à jour des vues matérialisées. Voici un bref aperçu :

**Réindexation ignorée** : la réindexation automatique est ignorée pour les indexeurs `suspended` et tous les indexeurs partageant le même `shared_index`. Cela permet de conserver les ressources système en ne réindexant pas les données liées aux processus suspendus.

**Mises à jour de vue matérialisées ignorées** : tout comme la réindexation, les mises à jour des vues matérialisées liées aux indexeurs `suspended` ou à leurs index partagés sont également suspendues. Cette action réduit davantage la charge du système pendant les périodes de suspension.

>[!INFO]
>
>La commande `indexer:reindex` réindexe tous les indexeurs, y compris ceux marqués comme `suspended`, ce qui la rend utile pour les mises à jour manuelles lorsque les mises à jour automatiques sont mises en pause.

>[!IMPORTANT]
>
>La modification de l’état d’un indexeur sur `valid` à partir de `suspended` ou `invalid` nécessite une certaine prudence. Cette action peut entraîner une dégradation des performances s’il existe des données cumulées non indexées.
>
>Il est essentiel de s’assurer que toutes les données sont correctement indexées avant de mettre manuellement à jour l’état sur `valid` afin de maintenir les performances du système et l’intégrité des données.
