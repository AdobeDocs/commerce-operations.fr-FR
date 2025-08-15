---
title: Bonne pratique pour la configuration des rapports
description: Optimisez les performances du site en supprimant le module de création de rapports si vous ne l’utilisez pas.
role: Admin
feature: Best Practices, Configuration
exl-id: 8c991b8a-affb-4a9e-9383-671f595ff89e
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '121'
ht-degree: 1%

---

# Bonne pratique pour la configuration des rapports

Si votre entreprise n’a pas besoin de la fonctionnalité de création de rapports ou de segments dynamiques de clients, désactivez la fonctionnalité [Rapports](https://experienceleague.adobe.com/en/docs/commerce-admin/config/general/reports) pour améliorer les performances de la boutique.

## Produits et versions concernés

[Toutes les versions prises en charge](../../../release/versions.md) de :

- Adobe Commerce sur les infrastructures cloud
- Adobe Commerce On-Premise

## Désactiver les rapports

Si vous n’utilisez pas les rapports ou les segments clients dynamiques, désactivez la fonctionnalité Rapports.

1. À partir de l’interface d’administration, accédez à **Magasins** > **Paramètres** > **Configuration** > **Général** > **Rapports**.
1. Sous **Options générales**, définissez **Activer les rapports** sur *Non*.
1. Videz le cache en exécutant `php bin/magento cache:flush` ou dans Admin sous **Système** > **Outils** > **Gestion du cache**.

## Informations supplémentaires

- [Générer des rapports dans Adobe Commerce](https://experienceleague.adobe.com/en/docs/commerce-admin/start/reporting/reports-menu)
- [Segments dynamiques client](https://experienceleague.adobe.com/en/docs/commerce-admin/customers/segments/customer-segments)
