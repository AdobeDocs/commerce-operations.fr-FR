---
title: '"Le [!UICONTROL Indexing] tab"'
description: En savoir plus sur les [!UICONTROL Indexing] de [!DNL Observation for Adobe Commerce].
source-git-commit: 1f334f329b72b715afa7f3617b1ce2fb8004f816
workflow-type: tm+mt
source-wordcount: '433'
ht-degree: 0%

---

# Le [!UICONTROL Indexing] tab

Le **[!UICONTROL Indexing]** tente d’expliquer les problèmes liés à l’indexation et d’identifier les causes potentielles.

## [!UICONTROL Core index invalidated]

![Index principal invalidé](../../assets/tools/observation-for-adobe-commerce/indexing-tab-1.jpg)

Le **[!UICONTROL Core index invalidated]** frame examine l’invalidation de l’indexation sur une période sélectionnée. Si l’indexation se produit en même temps que d’autres crons gourmands en ressources, elle place une charge importante sur les ressources du site.

* &quot;%L’indexeur de règles de produit du catalogue a été invalidé%&quot;) en tant que &quot;catalog_product_rule_idx_reset&quot;
* &quot;%L’indexeur de produit de règle de catalogue a été invalidé%&quot;) en tant que &quot;catalog_rule_product_idx_reset&quot;
* &quot;%L’indexeur de recherche de catalogue a été invalidé%&quot;) en tant que &quot;catalog_search_idx_reset&quot;
* &quot;%L’indexeur de produits de catégorie a été invalidé%&quot;) en tant que &quot;category_products_idx_reset&quot;
* &quot;%L’indexeur de grille client a été invalidé%&quot;) en tant que &quot;customer_grid_idx_reset&quot;
* &quot;%Design Config Grid indexeur a été invalidé%&quot;) en tant que &quot;design_config_grid_idx_
* &quot;%L’indexeur de catégories de produits a été invalidé%&quot;) en tant que &quot;product_categories_idx_reset&quot;
* &quot;%L’indexeur EAV du produit a été invalidé%&quot;) en tant que &quot;product_eav_idx_reset&quot;
* &quot;%L’indexeur de prix du produit a été invalidé%&quot;) en tant que &quot;product_price_idx_reset&quot;
* &quot;%Stock indexer a été invalidé%&quot;) en tant que &quot;stock_idx_reset&quot;
* &quot;%L’indexeur d’inventaire a été invalidé%&quot;) en tant que &quot;inventory_idx_reset&quot;
* &quot;%L’indexeur d’inventaire a été invalidé%&quot;) en tant que &quot;inventory_idx_reset&quot;
* &quot;%L’indexeur de règles de ventes a été invalidé%&quot;) en tant que &quot;sales_rule_idx_reset&quot;

## [!UICONTROL Core index rebuilds]

![Recréations de l’index principal](../../assets/tools/observation-for-adobe-commerce/indexing-tab-2.jpg)

Le **[!UICONTROL Core index rebuilds]** frame s’intéresse aux recompilations d’index principal au cours d’une période sélectionnée. Voici les chaînes analysées à partir des journaux pour indiquer la fin de la reconstruction de l’index.

* &quot;%L’index de règle de produit du catalogue a été reconstruit%&quot;) en tant que &quot;catalog_product_rule_idx&quot;
* &quot;%L’index de produit de la règle de catalogue a été reconstruit%&quot;) en tant que &quot;catalog_rule_product_idx&quot;
* &quot;%L’index de recherche catalogue a été reconstruit%&quot;) en tant que &quot;catalog_search_idx&quot;
* &quot;%L’index Produits de catégorie a été reconstruit avec succès%&quot;) en tant que &quot;category_products_idx&quot;
* &quot;%L’index de la grille client a été reconstruit%&quot;) en tant que &quot;customer_grid_idx&quot;
* &quot;%Design Config Grid index a été reconstruit%&quot;) en tant que &quot;design_config_grid_idx&quot;
* &quot;%L’index des catégories de produits a été reconstruit%&quot;) en tant que &quot;product_categories_idx&quot;
* &quot;%L’index EAV du produit a été reconstruit%&quot;) en tant que &quot;product_eav_idx&quot;
* &quot;%L&#39;indice des prix du produit a été reconstruit%&quot;) en tant que &quot;product_price_idx&quot;
* &quot;%Stock index has rebuild%&quot;) en tant que &quot;stock_idx&quot;
* &quot;%Index de l’inventaire reconstruit avec succès%&quot;) en tant que &quot;inventory_idx&quot;
* %L’index de règle produit/cible a été reconstruit avec succès%) en tant que &quot;prod_target_rule_idx&quot;
* &quot;%L’index de règle de vente a été reconstruit avec succès%&quot;) en &quot;sales_rule_idx&quot;


## [!UICONTROL catalogsearch index table(s)]

![table(s) d’index catalogsearch](../../assets/tools/observation-for-adobe-commerce/indexing-tab-3.jpg)

Le **[!UICONTROL catalogsearch index table(s)]** frame examine les tables d’index de recherche de catalogues sur une période sélectionnée. Cette requête examine la durée des opérations de banque de données par rapport aux tables dont le nom de la table contient &quot;%catalogsearch%&quot;.

## [!UICONTROL product index table(s)]

![table(s) d’index de produit](../../assets/tools/observation-for-adobe-commerce/indexing-tab-4.jpg)

Le **[!UICONTROL product index table(s)]** frame examine les tables d’index de produit sur une période sélectionnée. Cette requête examine la durée des opérations de banque de données par rapport aux tables dont le nom de la table contient &quot;%product%&quot;.
