---
title: Gestion des indexeurs
description: Consultez des exemples d’affichage et de gestion des indexeurs Commerce.
exl-id: d2cd1399-231e-4c42-aa0c-c2ed5d7557a0
source-git-commit: 16feb8ec7ecc88a6ef03a769d45b1a3a2fe88d97
workflow-type: tm+mt
source-wordcount: '947'
ht-degree: 0%

---

# Gestion des indexeurs

{{file-system-owner}}

Pour afficher la liste de tous les indexeurs :

```bash
bin/magento indexer:info
```

La liste se présente comme suit :

```
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
> Les commerçants Adobe Commerce qui utilisent Live Search, Catalog Service ou Product Recommendations ont la possibilité d’utiliser l’indexation de prix [basée sur SaaS](https://experienceleague.adobe.com/docs/commerce/price-indexer/index.html).

## Afficher le statut de l’indexeur

Utilisez cette commande pour afficher le statut de tous les indexeurs ou d’indexeurs spécifiques. Par exemple, déterminez si un indexeur doit être réindexé.

Options de commande :

```bash
bin/magento indexer:status [indexer]
```

Où `[indexer]` est une liste d’indexeurs séparés par des espaces. Omettez `[indexer]` pour afficher le statut de tous les indexeurs.

Exemple de résultat :

```
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
>Cette commande est réindexée une seule fois. Pour maintenir les indexeurs à jour, vous devez configurer une tâche [cron](../cli/configure-cron-jobs.md).

Options de commande :

```bash
bin/magento indexer:reindex [indexer]
```

Où `[indexer]` est une liste d’indexeurs séparés par des espaces. Omettez `[indexer]` pour réindexer tous les indexeurs.

Exemple de résultat :

```
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

```
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

```
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
>Veillez à définir le [!DNL Customer Grid] avec `realtime` au lieu de `schedule`. La [!DNL Customer Grid] ne peut être réindexée qu’à l’aide de l’option [!UICONTROL Update on Save]. Cet index ne prend pas en charge l’option `Update by Schedule`. Utilisez la ligne de commande suivante pour définir cet indexeur afin qu’il soit mis à jour lors de l’enregistrement : `php bin/magento indexer:set-mode realtime customer_grid`
>
>Voir [Bonnes pratiques pour la configuration de l’indexeur](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/maintenance/indexer-configuration.html) dans le _Guide d’implémentation_.

>[!INFO]
>
>Avant de changer de mode d’indexation, définissez votre site web sur le mode [maintenance](../../installation/tutorials/maintenance-mode.md) et [désactivez les tâches cron](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/app/properties/crons-property.html#disable-cron-jobs). Vous éviterez ainsi les verrous de base de données.

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

**Réindexation ignorée** : la réindexation automatique est ignorée pour les indexeurs `suspended` et les indexeurs partageant le même `shared_index`. Cela garantit la conservation des ressources système en évitant de réindexer les données liées aux processus suspendus.

**Mises à jour de vues matérialisées ignorées** : tout comme pour la réindexation, les mises à jour des vues matérialisées liées aux indexeurs `suspended` ou à leurs index partagés sont également suspendues. Cette action réduit davantage la charge du système pendant les périodes de suspension.

>[!INFO]
>
>La commande `indexer:reindex` réindexe tous les indexeurs, y compris ceux marqués comme `suspended`, ce qui les rend utiles pour les mises à jour manuelles lorsque les indexeurs automatiques sont en pause.

>[!IMPORTANT]
>
>La modification du statut d’un indexeur en `valid` à partir de `suspended` ou `invalid` requiert des précautions. Cette action peut entraîner une dégradation des performances en cas d’accumulation de données non indexées.
>
>Il est essentiel de s’assurer que toutes les données sont indexées avec précision avant de mettre à jour manuellement l’état sur `valid` pour maintenir les performances du système et l’intégrité des données.
