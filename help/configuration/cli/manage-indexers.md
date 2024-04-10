---
title: Gestion des indexeurs
description: Consultez des exemples d’affichage et de gestion des indexeurs de Commerce.
exl-id: d2cd1399-231e-4c42-aa0c-c2ed5d7557a0
source-git-commit: 602a1ef82fcb8d30ff027db0fe0aacb981c7e08e
workflow-type: tm+mt
source-wordcount: '943'
ht-degree: 0%

---

# Gestion des indexeurs

{{file-system-owner}}

Pour afficher la liste de tous les indexeurs :

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
> Les commerçants Adobe Commerce qui utilisent Live Search, Catalog Service ou Product Recommendations ont la possibilité d’utiliser [Indexation des prix basée sur SaaS](https://experienceleague.adobe.com/docs/commerce-merchant-services/price-indexer/index.html).

## Afficher le statut de l’indexeur

Utilisez cette commande pour afficher le statut de tous les indexeurs ou d’indexeurs spécifiques. Par exemple, déterminez si un indexeur doit être réindexé.

Options de commande :

```bash
bin/magento indexer:status [indexer]
```

Où `[indexer]` est une liste d’indexeurs séparés par des espaces. Omettre `[indexer]` pour afficher le statut de tous les indexeurs.

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

## Réindexer

Utilisez cette commande pour réindexer tous les indexeurs ou les indexeurs sélectionnés une seule fois.

>[!INFO]
>
>Cette commande ne réindexe qu’une seule fois. Pour maintenir les indexeurs à jour, vous devez configurer une [tâche cron](../cli/configure-cron-jobs.md).

Options de commande :

```bash
bin/magento indexer:reindex [indexer]
```

Où `[indexer]` est une liste d’indexeurs séparés par des espaces. Omettre `[indexer]` pour réindexer tous les indexeurs.

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
>La réindexation de tous les indexeurs peut prendre beaucoup de temps pour les magasins qui proposent un grand nombre de produits, de clients, de catégories et de règles promotionnelles.

### Réindexation en mode parallèle

{{php-process-control}}

Les indexeurs sont étendus et multithread pour prendre en charge la réindexation en mode parallèle. Il est parallélisé par la dimension de l’indexeur et s’exécute sur plusieurs threads, ce qui réduit le temps de traitement.

Dans ce contexte, `dimension` correspond à la portée de la réindexation ; par exemple, une `website` ou juste un `customer_group`.

La parallélisation d’index affecte uniquement les indexeurs étendus, ce qui signifie que Commerce divise les données en plusieurs tables en utilisant l’indexeur comme étendue au lieu de conserver toutes les données dans une seule table.

Vous pouvez exécuter les index suivants en mode parallèle :

- `Catalog Search Fulltext` peut être mis en parallèle par les vues de magasin.
- `Category Product` peut être mis en parallèle par les vues de magasin.
- `Catalog Price` peut être mis en parallèle par site web et groupes de clients.
- `Catalog Permissions` peut être mis en parallèle par des groupes de clients.

>[!INFO]
>
>La mise en parallèle du texte intégral de recherche catalogue et du produit de catégorie est activée par défaut.

Pour utiliser la parallélisation, définissez l’un des modes de dimensions disponibles pour l’indexeur de prix de produit :

- `none` (par défaut)
- `website`
- `customer_group`
- `website_and_customer_group`

Par exemple, pour définir le mode par site web :

```bash
bin/magento indexer:set-dimensions-mode catalog_product_price website
```

Pour utiliser la parallélisation pour les autorisations du catalogue, définissez l’un des modes de dimensions disponibles pour l’indexeur des autorisations du catalogue :

- `none` (par défaut)
- `customer_group`

Ou pour vérifier le mode actuel :

```bash
bin/magento indexer:show-dimensions-mode
```

Pour réindexer en mode parallèle, exécutez la commande reindex à l’aide de la variable d’environnement . `MAGE_INDEXER_THREADS_COUNT`ou ajoutez une variable d’environnement au `env.php` fichier . Cette variable définit le nombre de threads pour le traitement de la réindexation.

Par exemple, la commande suivante exécute le `Catalog Search Fulltext` indexeur sur trois threads :

```bash
MAGE_INDEXER_THREADS_COUNT=3 php -f bin/magento indexer:reindex catalogsearch_fulltext
```

## Réinitialiser l’indexeur

Utilisez cette commande pour invalider le statut de tous les indexeurs ou d’indexeurs spécifiques.

Options de commande :

```bash
bin/magento indexer:reset [indexer]
```

Où ```[indexer]``` est une liste d’indexeurs séparés par des espaces. Omettre `[indexer]` pour invalider tous les indexeurs.

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

- **Mise à jour lors de l’enregistrement (`realtime`)**: les données indexées sont mises à jour lorsqu’une modification est apportée à l’administration. (Par exemple, l’index des produits de catégorie est réindexé une fois que les produits ont été ajoutés à une catégorie dans l’Administration.) Il s’agit de la valeur par défaut.
- **Mise à jour par planning (`schedule`)**: les données sont indexées selon le planning défini par votre tâche cron.

[En savoir plus sur l’indexation](https://developer.adobe.com/commerce/php/development/components/indexing/).

### Afficher la configuration actuelle

Pour afficher la configuration actuelle de l’indexeur :

```bash
bin/magento indexer:show-mode [indexer]
```

Où `[indexer]` est une liste d’indexeurs séparés par des espaces. Omettre `[indexer]` pour afficher les modes de tous les indexeurs. Par exemple, pour afficher le mode de tous les indexeurs :

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

### Définir le mode de l’indexeur

>[!IMPORTANT]
>
>Veillez à définir la variable [!DNL Customer Grid] par `realtime` au lieu de `schedule`. Le [!DNL Customer Grid] ne peut être réindexé qu’à l’aide de [!UICONTROL Update on Save] option. Cet index ne prend pas en charge le `Update by Schedule` option. Utilisez la ligne de commande suivante pour définir cet indexeur afin de le mettre à jour lors de l’enregistrement : `php bin/magento indexer:set-mode realtime customer_grid`
>
>Voir [Bonnes pratiques relatives à la configuration de l’indexeur](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/maintenance/indexer-configuration.html) dans le _Manuel de mise en œuvre_.

>[!INFO]
>
>Avant de changer de mode d’indexeur, définissez votre site web sur . [maintenance](../../installation/tutorials/maintenance-mode.md) mode et [désactiver les traitements cron](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/app/properties/crons-property.html#disable-cron-jobs). Vous éviterez ainsi les verrous de base de données.

Pour spécifier la configuration de l’indexeur :

```bash
bin/magento indexer:set-mode {realtime|schedule} [indexer]
```

Où :

- `realtime`: définit les indexeurs sélectionnés à mettre à jour lors de l&#39;enregistrement.
- `schedule`: définit les indexeurs spécifiés à enregistrer selon le planning cron.
- `indexer`: est une liste d&#39;indexeurs séparés par des espaces. Omettre `indexer` pour configurer tous les indexeurs de la même manière.

Par exemple, pour modifier uniquement les indexeurs de catégories de produits et de catégories de produits afin de les mettre à jour selon le calendrier, saisissez :

```bash
bin/magento indexer:set-mode schedule catalog_category_product catalog_product_category
```

Exemple de résultat :

```terminal
Index mode for Indexer Category Products was changed from 'Update on Save' to 'Update by Schedule'
Index mode for Indexer Product Categories was changed from 'Update on Save' to 'Update by Schedule'
```

Les déclencheurs de base de données liés aux indexeurs sont ajoutés lorsque le mode d’indexeur est défini sur `schedule` et supprimés lorsque le mode indexeur est défini sur `realtime`. Si les déclencheurs sont absents de votre base de données alors que les indexeurs sont définis sur `schedule`, modifiez les indexeurs en `realtime` puis les redéfinir sur `schedule`. Cette opération réinitialise les déclencheurs.

### Définir le statut de l’indexeur

Cette commande permet aux administrateurs de modifier le statut opérationnel d’un ou de plusieurs indexeurs, optimisant ainsi les performances du système lors d’opérations étendues telles que l’importation de données, la mise à jour ou la maintenance.

Syntaxe de la commande :

```bash
bin/magento indexer:set-status {invalid|suspended|valid} [indexer]
```

Où :

- `invalid`: marque les indexeurs comme étant obsolètes, ce qui invite à les réindexer lors de la prochaine exécution cron, sauf s&#39;ils sont suspendus.
- `suspended`: arrête temporairement les mises à jour automatiques déclenchées par cron pour les indexeurs. Ce statut s’applique aux modes temps réel et planification , ce qui garantit que les mises à jour automatiques sont suspendues pendant les opérations intensives.
- `valid`: indique que les données de l&#39;indexeur sont à jour et n&#39;ont pas besoin d&#39;être réindexées.
- `indexer`: est une liste d&#39;indexeurs séparés par des espaces. Omettre `indexer` pour configurer tous les indexeurs de la même manière.

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

Lorsqu’un indexeur est défini sur une valeur `suspended` affecte principalement la réindexation automatique et les mises à jour des vues matérialisées. Voici un bref aperçu :

**Réindexation ignorée**: la réindexation automatique est ignorée pour . `suspended` les indexeurs et les indexeurs qui les partagent `shared_index`. Cela permet de s’assurer que les ressources système sont conservées en ne réindexant pas les données liées aux processus suspendus.

**Mises À Jour Des Vues Matérialisées Ignorées**: tout comme pour la réindexation, les mises à jour des vues matérialisées liées à `suspended` les indexeurs ou leurs index partagés sont également suspendus. Cette action réduit davantage la charge du système pendant les périodes de suspension.

>[!INFO]
>
>Le `indexer:reindex` commande réindexe tous les indexeurs, y compris ceux marqués comme `suspended`, ce qui rend utile les mises à jour manuelles lorsque les mises à jour automatiques sont suspendues.

>[!IMPORTANT]
>
>Modification du statut d’un indexeur en `valid` de `suspended` ou `invalid` requiert une attention particulière. Cette action peut entraîner une dégradation des performances en cas d’accumulation de données non indexées.
>
>Il est essentiel de s’assurer que toutes les données sont correctement indexées avant de mettre à jour manuellement le statut sur . `valid` pour maintenir les performances du système et l’intégrité des données.
