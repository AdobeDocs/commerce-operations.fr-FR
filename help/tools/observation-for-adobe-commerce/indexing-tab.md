---
title: Onglet [!UICONTROL Indexing]
description: En savoir plus sur l’onglet [!UICONTROL Indexing] de  [!DNL Observation for Adobe Commerce].
exl-id: c7e123b7-2d0c-49d4-9f76-128939dc02a8
feature: Configuration, Observability
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '176'
ht-degree: 0%

---

# Onglet [!UICONTROL Indexing]

L’onglet **[!UICONTROL Indexing]** tente d’expliquer les problèmes d’indexation et d’identifier les causes potentielles.

## [!UICONTROL Core index invalidated]

![Index principal invalidé](../../assets/tools/observation-for-adobe-commerce/indexing-tab-1.jpg)

Le cadre **[!UICONTROL Core index invalidated]** examine l’invalidation de l’indexation sur une période sélectionnée. Si l’indexation s’effectue en même temps que d’autres [!DNL crons] gourmandes en ressources, cela place une charge importante sur les ressources du site.

* `%Catalog Product Rule indexer has been invalidated%`) comme `catalog_product_rule_idx_reset`
* `%Catalog Rule Product indexer has been invalidated%`) comme `catalog_rule_product_idx_reset`
* `%Catalog Search indexer has been invalidated%`) comme `catalog_search_idx_reset`
* `%Category Products indexer has been invalidated%`) comme `category_products_idx_reset`
* `%Customer Grid indexer has been invalidated%`) comme `customer_grid_idx_reset`
* `%Design Config Grid indexer has been invalidated%`) comme `design_config_grid_idx_`
* `%Product Categories indexer has been invalidated%`) comme `product_categories_idx_reset`
* `%Product EAV indexer has been invalidated%`) comme `product_eav_idx_reset`
* `%Product Price indexer has been invalidated%`) comme `product_price_idx_reset`
* `%Stock indexer has been invalidated%`) comme `stock_idx_reset`
* `%Inventory indexer has been invalidated%`) comme `inventory_idx_reset`
* `%Inventory indexer has been invalidated%`) comme `inventory_idx_reset`
* `%Sales Rule indexer has been invalidated%`) comme `sales_rule_idx_reset`

## [!UICONTROL Core index rebuilds]

![Reconstructions de l’index de base](../../assets/tools/observation-for-adobe-commerce/indexing-tab-2.jpg)

L’image **[!UICONTROL Core index rebuilds]** examine les reconstructions de l’index de base sur une période sélectionnée. Voici les chaînes qui sont analysées à partir des journaux pour indiquer l’achèvement de la reconstruction de l’index.

* `%Catalog Product Rule index has been rebuilt%`) comme `catalog_product_rule_idx`
* `%Catalog Rule Product index has been rebuilt%`) comme `catalog_rule_product_idx`
* `%Catalog Search index has been rebuilt%`) comme `catalog_search_idx`
* `%Category Products index has been rebuilt successfully%`) comme `category_products_idx`
* `%Customer Grid index has been rebuilt%`) comme `customer_grid_idx`
* `%Design Config Grid index has been rebuilt%`) comme `design_config_grid_idx`
* `%Product Categories index has been rebuilt%`) comme `product_categories_idx`
* `%Product EAV index has been rebuilt%`) comme `product_eav_idx`
* `%Product Price index has been rebuilt%`) comme `product_price_idx`
* `%Stock index has been rebuilt%`) comme `stock_idx`
* `%Inventory index has been rebuilt successfully%`) comme `inventory_idx`
* `%Product/Target Rule index has been rebuilt successfully%`) comme `prod_target_rule_idx`
* `%Sales Rule index has been rebuilt successfully%`) comme `sales_rule_idx`


## [!UICONTROL catalogsearch index table(s)]

![table(s) d&#39;index catalogsearch](../../assets/tools/observation-for-adobe-commerce/indexing-tab-3.jpg)

Le cadre de **[!UICONTROL catalogsearch index table(s)]** examine les tables d’index de recherche de catalogue sur une période sélectionnée. Cette requête examine la durée de toutes les opérations du magasin de données par rapport aux tables dont le nom contient `%catalogsearch%`.

## [!UICONTROL product index table(s)]

![table(s) d’index de produit)](../../assets/tools/observation-for-adobe-commerce/indexing-tab-4.jpg)

Le cadre de **[!UICONTROL product index table(s)]** examine les tables d’index de produit sur une période sélectionnée. Cette requête examine la durée de toutes les opérations du magasin de données par rapport aux tables dont le nom contient `%product%`.
