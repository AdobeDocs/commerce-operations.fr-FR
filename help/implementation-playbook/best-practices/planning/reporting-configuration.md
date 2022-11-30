---
title: Bonne pratique pour la configuration des rapports
description: Optimisez les performances du site en supprimant le module de reporting si vous ne l’utilisez pas.
role: Admin
feature: Best Practices
feature-set: Commerce
source-git-commit: 85f9355d0e8c704be3760334b07414d3e15b3b97
workflow-type: tm+mt
source-wordcount: '133'
ht-degree: 0%

---


# Bonne pratique pour la configuration des rapports

Si votre entreprise ne nécessite pas de fonctionnalités de création de rapports ou de segments de clients dynamiques, désactivez la variable [Fonctionnalité des rapports](https://docs.magento.com/user-guide/configuration/general/reports.html) pour améliorer les performances du magasin.

## Produits et versions concernés

[Toutes les versions prises en charge](../../../release/versions.md) de :

- Adobe Commerce sur l’infrastructure cloud
- Adobe Commerce sur site

## Désactivation des rapports

Si vous n’utilisez pas les segments Rapports ou clients dynamiques, désactivez la fonctionnalité Rapports .

1. Depuis l’administrateur, accédez à **Magasins** > **Paramètres** > **Configuration** > **Général** > **Rapports**.
1. Sous **Options générales**, définit **Activation des rapports** to *Non*.
1. Videz le cache en exécutant `php bin/magento cache:flush` ou dans l’Admin sous **Système** > **Outils** > **Gestion du cache**.

## Informations supplémentaires

- [Génération de rapports dans Adobe Commerce](https://docs.magento.com/user-guide/reports.html)
- [Segments dynamiques de client](https://docs.magento.com/user-guide/marketing/customer-segments.html)