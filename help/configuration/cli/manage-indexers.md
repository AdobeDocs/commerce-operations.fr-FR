---
title: Gestion des indexeurs
description: Découvrez comment afficher et gérer les indexeurs Adobe Commerce à l’aide d’outils de ligne de commande. Découvrez les commandes de l’indexeur, la vérification de l’état et les techniques de réindexation.
exl-id: d2cd1399-231e-4c42-aa0c-c2ed5d7557a0
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '974'
ht-degree: 0%

---

# Gestion des indexeurs

{{file-system-owner}}

Pour afficher la liste de tous les indexeurs :

```bash
bin/magento indexer:info
```

La liste se présente comme suit :

```text
cataloginventory_stock                   Stock
design_config_grid                       Design Config Grid
customer_grid                            Customer Grid
catalog_category_product                 Category Products
catalog_product_category                 Product Categories
catalogrule_rule                         Catalog Rule Product
catalog_product_attribute                Product EAV
inventory                                Inventory
catalog_product_price                    Product Price
catalogrule_product                      Catalog Product Rule
targetrule_product_rule                  Product/Target Rule
targetrule_rule_product                  Target Rule/Product
catalogsearch_fulltext                   Catalog Search
salesrule_rule                           Sales Rule
sales_order_data_exporter                Sales Order Feed
sales_order_status_data_exporter         Sales Order Statuses Feed
store_data_exporter                      Stores Feed
```

>[!NOTE]
>
> Les commerçants Adobe Commerce qui utilisent Live Search, Catalog Service ou Product Recommendations ont la possibilité d’utiliser l’indexation de prix [basée sur SaaS](https://experienceleague.adobe.com/en/docs/commerce/price-indexer/price-indexing).

## Afficher le statut de l’indexeur

Utilisez cette commande pour afficher le statut de tous les indexeurs ou d’indexeurs spécifiques. Par exemple, déterminez si un indexeur doit être réindexé.

Options de commande :

```bash
bin/magento indexer:status [indexer]
```

Où `[indexer]` est une liste d’indexeurs séparés par des espaces. Omettez `[indexer]` pour afficher le statut de tous les indexeurs.

Exemple de résultat :

```text
+----------------------------------+---------------------------+--------+-----------+---------------------+---------------------+
| ID                               | Title                     | Status | Update On | Schedule Status     | Schedule Updated    |
+----------------------------------+---------------------------+--------+-----------+---------------------+---------------------+
| catalogrule_product              | Catalog Product Rule      | Ready  | Schedule  | idle (0 in backlog) | 2025-07-11 08:00:52 |
| catalogrule_rule                 | Catalog Rule Product      | Ready  | Schedule  | idle (0 in backlog) | 2025-07-11 08:00:52 |
| catalogsearch_fulltext           | Catalog Search            | Ready  | Schedule  | idle (0 in backlog) | 2025-07-11 08:01:02 |
| catalog_category_product         | Category Products         | Ready  | Schedule  | idle (0 in backlog) | 2025-06-03 14:11:33 |
| customer_grid                    | Customer Grid             | Ready  | Schedule  | idle (0 in backlog) | 2025-06-03 14:11:31 |
| design_config_grid               | Design Config Grid        | Ready  | Schedule  | idle (0 in backlog) | 2025-06-03 14:11:31 |
| inventory                        | Inventory                 | Ready  | Schedule  | idle (0 in backlog) | 2025-06-03 14:11:36 |
| catalog_product_category         | Product Categories        | Ready  | Schedule  | idle (0 in backlog) | 2025-06-03 14:11:33 |
| catalog_product_attribute        | Product EAV               | Ready  | Schedule  | idle (0 in backlog) | 2025-06-03 14:11:36 |
| catalog_product_price            | Product Price             | Ready  | Schedule  | idle (0 in backlog) | 2025-07-11 08:00:54 |
| targetrule_product_rule          | Product/Target Rule       | Ready  | Schedule  | idle (0 in backlog) | 2025-06-03 14:11:39 |
| sales_order_data_exporter        | Sales Order Feed          | Ready  | Schedule  | idle (0 in backlog) | 2025-06-03 14:12:10 |
| sales_order_status_data_exporter | Sales Order Statuses Feed | Ready  | Schedule  | idle (0 in backlog) | 2025-06-03 14:12:10 |
| salesrule_rule                   | Sales Rule                | Ready  | Schedule  | idle (0 in backlog) | 2025-06-03 14:12:10 |
| cataloginventory_stock           | Stock                     | Ready  | Schedule  | idle (0 in backlog) | 2025-06-03 14:11:31 |
| store_data_exporter              | Stores Feed               | Ready  | Schedule  | idle (0 in backlog) | 2025-06-03 14:12:11 |
| targetrule_rule_product          | Target Rule/Product       | Ready  | Schedule  | idle (0 in backlog) | 2025-06-03 14:11:39 |
+----------------------------------+---------------------------+--------+-----------+---------------------+---------------------+
```

## Réindexer

Utilisez cette commande pour réindexer tous les indexeurs ou les indexeurs sélectionnés une seule fois.

>[!INFO]
>
>Cette commande est réindexée une seule fois. Pour maintenir les indexeurs à jour, vous devez configurer une tâche [cron](../cli/configure-cron-jobs.md).

Options de commande :

```bash
bin/magento indexer:reindex [indexer]
```

Où `[indexer]` est une liste d’indexeurs séparés par des espaces. Omettez `[indexer]` pour réindexer tous les indexeurs.

Exemple de résultat :

```text
Stock index has been rebuilt successfully in <time>
Design Config Grid index has been rebuilt successfully in <time>
Customer Grid index has been rebuilt successfully in <time>
Category Products index has been rebuilt successfully in <time>
Product Categories index has been rebuilt successfully in <time>
Catalog Rule Product index has been rebuilt successfully in <time>
Product EAV index has been rebuilt successfully in <time>
Inventory index has been rebuilt successfully in <time>
Product Price index has been rebuilt successfully in <time>
Catalog Product Rule index has been rebuilt successfully in <time>
Product/Target Rule index has been rebuilt successfully in <time>
Target Rule/Product index has been rebuilt successfully in <time>
Catalog Search index has been rebuilt successfully in <time>
Sales Rule index has been rebuilt successfully in <time>
Sales Order Feed index has been rebuilt successfully in <time>
Sales Order Statuses Feed index has been rebuilt successfully in <time>
Stores Feed index has been rebuilt successfully in <time>
```

>[!INFO]
>
>La réindexation de tous les indexeurs peut prendre beaucoup de temps pour les magasins qui contiennent un grand nombre de produits, de clients, de catégories et de règles promotionnelles.

### Réindexation en mode parallèle

{{php-process-control}}

Les indexeurs sont étendus et multithread pour prendre en charge la réindexation en mode parallèle. Il est parallélisé par la dimension de l’indexeur et s’exécute sur plusieurs threads, réduisant ainsi le temps de traitement.

Dans ce contexte, `dimension` s’agit de la portée de la réindexation, par exemple une `website` ou simplement une `customer_group` spécifique.

La parallélisation d’index affecte uniquement les indexeurs inclus dans l’étendue, ce qui signifie que Commerce divise les données en plusieurs tables en utilisant l’indexeur comme étendue au lieu de conserver toutes les données dans une seule table.

Vous pouvez exécuter les index suivants en mode parallèle :

- `Catalog Search Fulltext` vues du magasin peuvent être utilisées en parallèle.
- `Category Product` vues du magasin peuvent être utilisées en parallèle.
- `Catalog Price` peut être mis en parallèle par site web et groupes de clients.
- `Catalog Permissions` peuvent être mis en parallèle par des groupes de clients.

>[!INFO]
>
>La parallélisation pour Catalog Search Fulltext et Category Product est activée par défaut.

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

Pour réindexer en mode parallèle, exécutez la commande reindex à l’aide de la variable d’environnement `MAGE_INDEXER_THREADS_COUNT` ou ajoutez une variable d’environnement au fichier `env.php`. Cette variable définit le nombre de threads pour le traitement de la réindexation.

Par exemple, la commande suivante exécute l’indexeur `Catalog Search Fulltext` sur trois threads :

```bash
MAGE_INDEXER_THREADS_COUNT=3 php -f bin/magento indexer:reindex catalogsearch_fulltext
```

## Réinitialiser l’indexeur

Utilisez cette commande pour invalider le statut de tous les indexeurs ou d’indexeurs spécifiques.

Options de commande :

```bash
bin/magento indexer:reset [indexer]
```

Où ```[indexer]``` est une liste d’indexeurs séparés par des espaces. Omettez `[indexer]` pour invalider tous les indexeurs.

Exemple de résultat :

```text
Stock indexer has been invalidated.
Design Config Grid indexer has been invalidated.
Customer Grid indexer has been invalidated.
Category Products indexer has been invalidated.
Product Categories indexer has been invalidated.
Catalog Rule Product indexer has been invalidated.
Product EAV indexer has been invalidated.
Inventory indexer has been invalidated.
Product Price indexer has been invalidated.
Catalog Product Rule indexer has been invalidated.
Product/Target Rule indexer has been invalidated.
Target Rule/Product indexer has been invalidated.
Catalog Search indexer has been invalidated.
Sales Rule indexer has been invalidated.
Sales Order Feed indexer has been invalidated.
Sales Order Statuses Feed indexer has been invalidated.
Stores Feed indexer has been invalidated.
```

## Configuration des indexeurs

Utilisez cette commande pour définir les options d’indexeur suivantes :

- **Mise à jour lors de l’enregistrement (`realtime`)** : les données indexées sont mises à jour lorsqu’une modification est apportée dans l’administrateur. (Par exemple, l’index de catégorie de produits est réindexé une fois que les produits ont été ajoutés à une catégorie dans l’Administration.)
- **Mise à jour par planning (`schedule`)** : les données sont indexées en fonction du planning défini par votre tâche cron.

[En savoir plus sur l’indexation](https://developer.adobe.com/commerce/php/development/components/indexing/).

### Afficher la configuration actuelle

Pour afficher la configuration actuelle de l’indexeur :

```bash
bin/magento indexer:show-mode [indexer]
```

Où `[indexer]` est une liste d’indexeurs séparés par des espaces. Omettez `[indexer]` pour afficher tous les modes des indexeurs. Par exemple, pour afficher le mode de tous les indexeurs :

Exemple de résultat :

```text
Stock:                                             Update by Schedule
Design Config Grid:                                Update by Schedule
Customer Grid:                                     Update by Schedule
Category Products:                                 Update by Schedule
Product Categories:                                Update by Schedule
Catalog Rule Product:                              Update by Schedule
Product EAV:                                       Update by Schedule
Inventory:                                         Update by Schedule
Product Price:                                     Update by Schedule
Catalog Product Rule:                              Update by Schedule
Product/Target Rule:                               Update by Schedule
Target Rule/Product:                               Update by Schedule
Catalog Search:                                    Update by Schedule
Sales Rule:                                        Update by Schedule
Sales Order Feed:                                  Update by Schedule
Sales Order Statuses Feed:                         Update by Schedule
Stores Feed:                                       Update by Schedule
```

### Définir le mode de l’indexeur

>[!IMPORTANT]
>
>Le comportement de l’indexeur [!DNL Customer Grid] a changé dans la version 2.4.8 :
>
>- **Antérieur à la version 2.4.8** : l’indexeur de [!DNL Customer Grid] ne peut être réindexé qu’à l’aide de l’option [!UICONTROL Update on Save] et ne prend pas en charge l’option [!UICONTROL Update by Schedule].
>
>   Utilisez la commande suivante pour définir cet indexeur afin qu’il soit mis à jour lors de l’enregistrement :
>
>   ```bash
>   bin/magento indexer:set-mode realtime customer_grid
>   ```
>
>- **2.4.8 et versions ultérieures** : l’indexeur de [!DNL Customer Grid] prend en charge les modes [!UICONTROL Update on Save] et [!UICONTROL Update by Schedule], et la valeur par défaut est [!UICONTROL Update by Schedule].
>
>Voir [Bonnes pratiques pour la configuration de l’indexeur](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/maintenance/indexer-configuration) dans le _Guide d’implémentation_.

>[!INFO]
>
>Avant de changer de mode d’indexation, définissez votre site web sur le mode [maintenance](../../installation/tutorials/maintenance-mode.md) et [désactivez les tâches cron](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/app/properties/crons-property). Vous éviterez ainsi les verrous de base de données.

Pour spécifier la configuration de l’indexeur :

```bash
bin/magento indexer:set-mode {realtime|schedule} [indexer]
```

Où :

- `realtime` : définit les indexeurs sélectionnés à mettre à jour lors de l&#39;enregistrement.
- `schedule` : permet de définir les indexeurs spécifiés à enregistrer selon le planning cron.
- `indexer` : il s&#39;agit d&#39;une liste d&#39;indexeurs séparés par des espaces. Omettez `indexer` pour configurer tous les indexeurs de la même manière.

Par exemple, pour modifier uniquement les indexeurs de catégories de produits et de catégories de produits afin de les mettre à jour selon le calendrier, saisissez :

```bash
bin/magento indexer:set-mode schedule catalog_category_product catalog_product_category
```

Exemple de résultat :

```
Index mode for Indexer Category Products was changed from 'Update on Save' to 'Update by Schedule'
Index mode for Indexer Product Categories was changed from 'Update on Save' to 'Update by Schedule'
```

Les déclencheurs de base de données liés aux indexeurs sont ajoutés lorsque le mode d’indexeur est défini sur `schedule` et supprimés lorsque le mode d’indexeur est défini sur `realtime`. Si les déclencheurs sont absents de votre base de données alors que les indexeurs sont définis sur `schedule`, définissez-les sur `realtime` puis redéfinissez-les sur `schedule`. Cette opération réinitialise les déclencheurs.

### Définir le statut de l’indexeur

La commande `bin/magento indexer:set-status` a été introduite dans Adobe Commerce 2.4.7. Il permet aux administrateurs de modifier le statut opérationnel d’un ou de plusieurs indexeurs, optimisant ainsi les performances du système lors d’opérations étendues telles que l’importation de données, la mise à jour ou la maintenance.

Syntaxe de la commande :

```bash
bin/magento indexer:set-status {invalid|suspended|valid} [indexer]
```

Où :

- `invalid` : marque les indexeurs comme étant obsolètes, ce qui invite à les réindexer lors de la prochaine exécution cron, à moins qu&#39;ils ne soient suspendus.
- `suspended` : arrête temporairement les mises à jour automatiques déclenchées par cron pour les indexeurs. Ce statut s’applique aux modes temps réel et planification , ce qui garantit que les mises à jour automatiques sont suspendues pendant les opérations intensives.
- `valid` : indique que les données de l&#39;indexeur sont à jour, sans qu&#39;il soit nécessaire de les réindexer.
- `indexer` : il s&#39;agit d&#39;une liste d&#39;indexeurs séparés par des espaces. Omettez `indexer` pour configurer tous les indexeurs de la même manière.

Par exemple, pour suspendre des indexeurs spécifiques, saisissez :

```bash
bin/magento indexer:set-status suspended catalog_category_product catalog_product_category
```

Exemple de résultat :

```
Index status for Indexer 'Category Products' was changed from 'valid' to 'suspended'.
Index status for Indexer 'Product Categories' was changed from 'valid' to 'suspended'.
```

#### Gestion du statut de l’indexeur suspendu

Lorsqu&#39;un indexeur est défini sur un statut `suspended`, il affecte principalement la réindexation automatique et les mises à jour des vues matérialisées. Voici un bref aperçu :

**Réindexation ignorée** : le système ignore la réindexation automatique pour les indexeurs `suspended` et tous les indexeurs qui partagent le même `shared_index`. Cette approche permet de conserver les ressources du système en évitant de réindexer les données liées aux processus suspendus.

**Mises à jour de vues matérialisées ignorées** : tout comme pour la réindexation, le système suspend également les mises à jour des vues matérialisées liées aux indexeurs `suspended` ou à leurs index partagés. Cette pause réduit davantage la charge du système pendant les périodes de suspension.

>[!INFO]
>
>La commande `indexer:reindex` réindexe tous les indexeurs, y compris ceux marqués comme `suspended`, ce qui les rend utiles pour les mises à jour manuelles lorsque les indexeurs automatiques sont en pause.

>[!IMPORTANT]
>
>La modification du statut d’un indexeur en `valid` à partir de `suspended` ou `invalid` requiert des précautions. Cette action peut entraîner une dégradation des performances en cas d’accumulation de données non indexées.
>
>Il est essentiel de s’assurer que toutes les données sont indexées avec précision avant de mettre à jour manuellement l’état sur `valid` pour maintenir les performances du système et l’intégrité des données.
