---
title: Suppression ou mise à jour d’exemples de modules de données
description: Suivez ces étapes pour gérer les exemples de modules de données Adobe Commerce.
exl-id: d23f999f-18bf-449b-be23-bdf392dda539
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '107'
ht-degree: 0%

---

# Suppression ou mise à jour d’exemples de modules de données

Cette rubrique explique comment :

* [Suppression des exemples de modules de données](#remove-sample-data-modules) depuis une installation Adobe Commerce `composer.json`. Cette option permet de *not* supprimer des exemples de données de la base de données.

* [Préparation à la mise à jour des exemples de données](#prepare-to-update-sample-data) (par exemple, avant de mettre à jour l’application de Magento).

## Suppression des exemples de modules de données

Saisissez la commande suivante :

```bash
bin/magento sampledata:remove
```

La liste complète des exemples de modules de données est la suivante :

* `magento/module-bundle-sample-data`
* `magento/module-catalog-rule-sample-data`
* `magento/module-catalog-sample-data`
* `magento/module-cms-sample-data`
* `magento/module-configurable-sample-data`
* `magento/module-customer-sample-data`
* `magento/module-downloadable-sample-data`
* `magento/module-grouped-product-sample-data`
* `magento/module-msrp-sample-data`
* `magento/module-offline-shipping-sample-data`
* `magento/module-product-links-sample-data`
* `magento/module-review-sample-data`
* `magento/module-sales-rule-sample-data`
* `magento/module-sales-sample-data`
* `magento/module-sample-data`
* `magento/module-swatches-sample-data`
* `magento/module-tax-sample-data`
* `magento/module-theme-sample-data`
* `magento/module-widget-sample-data`
* `magento/module-wishlist-sample-data`
* `magento/sample-data-media`

## Préparation à la mise à jour des exemples de données

Cette commande permet de mettre à jour des données d’exemple avant de mettre à jour Adobe Commerce.

Pour préparer les exemples de données à mettre à jour, saisissez la commande suivante :

```bash
bin/magento sampledata:reset
```

Après cela, [mettre à jour l’application](../tutorials/uninstall.md#update-the-application).
