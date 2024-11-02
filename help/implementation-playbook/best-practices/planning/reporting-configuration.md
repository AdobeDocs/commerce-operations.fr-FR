---
title: Bonne pratique pour la configuration des rapports
description: Optimisez les performances du site en supprimant le module de reporting si vous ne l’utilisez pas.
role: Admin
feature: Best Practices, Configuration
exl-id: 8c991b8a-affb-4a9e-9383-671f595ff89e
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '121'
ht-degree: 1%

---

# Bonne pratique pour la configuration des rapports

Si votre entreprise ne nécessite pas de fonctionnalités de création de rapports ou de segments de clients dynamiques, désactivez la [fonctionnalité Rapports](https://experienceleague.adobe.com/en/docs/commerce-admin/config/general/reports) pour améliorer les performances du magasin.

## Produits et versions concernés

[Toutes les versions prises en charge](../../../release/versions.md) de :

- Adobe Commerce sur l’infrastructure cloud
- Adobe Commerce sur site

## Désactivation de la création de rapports

Si vous n’utilisez pas les segments Rapports ou clients dynamiques, désactivez la fonctionnalité Rapports .

1. Depuis l’administrateur, accédez à **Magasins** > **Paramètres** > **Configuration** > **Général** > **Rapports**.
1. Sous **Options générales**, définissez **Activer les rapports** sur *Non*.
1. Videz le cache en exécutant `php bin/magento cache:flush` ou dans l’administrateur sous **System** > **Tools** > **Cache Management**.

## Informations supplémentaires

- [Générer des rapports dans Adobe Commerce](https://experienceleague.adobe.com/en/docs/commerce-admin/start/reporting/reports-menu)
- [ Segments dynamiques client ](https://experienceleague.adobe.com/en/docs/commerce-admin/customers/segments/customer-segments)
