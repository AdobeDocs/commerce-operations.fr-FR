---
title: Bonnes pratiques de configuration pour le traitement des commandes
description: Découvrez les bonnes pratiques de configuration pour améliorer les performances de passage en caisse et de traitement des commandes.
role: Admin, User
feature: Best Practices
exl-id: d15fe845-670f-4f7e-9645-7e111e6e809f
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '236'
ht-degree: 0%

---

# Bonnes pratiques de configuration pour le traitement des commandes

À mesure que le volume des commandes augmente sur vos sites Commerce, vous pouvez optimiser les performances de passage en caisse et le traitement des commandes en activant les options de configuration de magasin suivantes :

- **[!UICONTROL Asynchronous indexing]** : activez cette option pour éviter les verrous de base de données et le ralentissement du traitement qui peuvent survenir lorsqu&#39;un grand nombre de commandes sont passées simultanément.
- **[!UICONTROL Asynchronous email notifications]** : activez cette option pour accélérer les performances de passage en caisse en envoyant des notifications par e-mail de passage en caisse et de traitement de commande à des intervalles spécifiés au lieu de les envoyer immédiatement.
- **[!UICONTROL Enable Archiving]** : activez cette option pour améliorer les performances des commandes, des factures, des livraisons et des avoirs et préserver votre espace de travail des informations inutiles, afin que vous puissiez vous concentrer sur l&#39;activité actuelle. Voir [ Activer l’archivage ](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/order-management/orders/order-archive).

## Produits et versions concernés

[Toutes les versions prises en charge](../../../release/versions.md) de :

- Adobe Commerce sur les infrastructures cloud
- Adobe Commerce On-Premise

## Activer le traitement asynchrone des commandes

Les étapes permettant d&#39;activer le traitement asynchrone des commandes dépendent du mode de déploiement :

- Pour Adobe Commerce sur les infrastructures cloud et les sites locaux en mode de production, utilisez la commande d’interface de ligne de commande Magento suivante pour activer l’indexation asynchrone :

  ```php
  php bin/magento config:set dev/grid/async_indexing 1
  ```

- Pour les sites locaux Adobe Commerce en mode par défaut ou de production, activez l’indexation asynchrone en mettant à jour la configuration des paramètres de grille dans l’Administration.

  Voir [Activer les mises à jour de grille planifiées et la réindexation](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/order-management/orders/order-scheduled-operations.html#enable-scheduled-grid-updates-and-reindexing)

  >[!WARNING]
  >
  >Testez toujours les modifications de configuration dans l’environnement d’évaluation avant de mettre à jour l’environnement de production.

## Informations supplémentaires

- [Bonnes pratiques de configuration](../../../performance/configuration.md)
- [Référence des chemins de configuration généraux et avancés](../../../configuration/reference/config-reference-general.md)
- [Traitement des commandes à haut débit](../../../performance/high-throughput-order-processing.md)
