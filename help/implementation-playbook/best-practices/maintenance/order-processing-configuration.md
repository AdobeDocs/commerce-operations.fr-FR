---
title: Bonnes pratiques de configuration pour le traitement des commandes
description: Découvrez les bonnes pratiques de configuration afin d’améliorer les performances de traitement des commandes et des passages en caisse.
role: Admin, User
feature: Best Practices
exl-id: d15fe845-670f-4f7e-9645-7e111e6e809f
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '249'
ht-degree: 0%

---

# Bonnes pratiques de configuration pour le traitement des commandes

À mesure que le volume des commandes augmente sur vos sites de commerce, vous pouvez optimiser les performances de passage en caisse et le traitement des commandes en activant les options de configuration de magasin suivantes :

- **[!UICONTROL Asynchronous indexing]**: activez cette option pour empêcher les verrous de base de données et le ralentissement du traitement qui peuvent se produire lorsque de grands nombres de commandes sont placés simultanément.
- **[!UICONTROL Asynchronous email notifications]**: activez cette option pour accélérer les performances de passage en caisse en envoyant des notifications par courrier électronique de passage en caisse et de traitement des commandes à des intervalles désignés au lieu de les envoyer immédiatement.
- **[!UICONTROL Enable Archiving]**: activez cette option pour améliorer les performances des commandes, des factures, des envois et des notes de crédit, et garder votre espace de travail à l’abri des informations superflues afin que vous puissiez vous concentrer sur l’activité actuelle. Voir [Activer l’archivage](https://docs.magento.com/user-guide/sales/order-archive.html#to-enable-archiving).

## Produits et versions concernés

[Toutes les versions prises en charge](../../../release/versions.md) de :

- Adobe Commerce sur l’infrastructure cloud
- Adobe Commerce sur site

## Activation du traitement asynchrone des commandes

Les étapes pour activer le traitement asynchrone des commandes dépendent du mode de déploiement :

- Pour Adobe Commerce sur l’infrastructure cloud et les sites sur site en mode de production, utilisez la commande d’interface de ligne de commande du Magento suivante pour activer l’indexation asynchrone :

  ```php
  php bin/magento config:set dev/grid/async_indexing 1
  ```

- Pour les sites sur site Adobe Commerce en mode par défaut ou de production, activez l’indexation asynchrone en mettant à jour la configuration des paramètres de grille dans l’administrateur.

  Voir [Activation des mises à jour de grille planifiées et de la réindexation](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/order-management/orders/order-scheduled-operations.html#enable-scheduled-grid-updates-and-reindexing)

  >[!WARNING]
  >
  >Toujours tester les modifications de configuration dans l’environnement d’évaluation avant de mettre à jour l’environnement de production.

## Informations supplémentaires

- [Bonnes pratiques de configuration](../../../performance/configuration.md)
- [Référence sur les chemins de configuration généraux et avancés](../../../configuration/reference/config-reference-general.md)
- [Traitement des commandes à haut débit](../../../performance/high-throughput-order-processing.md)
