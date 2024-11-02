---
title: Consommateurs de file d’attente de messages
description: Découvrez les consommateurs de file d’attente de messages Adobe Commerce, y compris les fonctionnalités et les paramètres de configuration système qui leur sont associés.
exl-id: 7fd7ab3f-581f-493c-956c-731f111d1b14
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '825'
ht-degree: 0%

---

# Consommateurs de file d’attente de messages

Le tableau suivant identifie tous les consommateurs de file d’attente de messages, décrit ce qu’ils font et identifie les paramètres de configuration du système d’administration qui leur sont associés :

| Consommateur et description | Adobe Commerce | Adobe Commerce avec B2B | Magento Open Source |
|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------|-------------------------|---------------------|
| `async.operations.all` | + | + | + |
| Crée des messages pour chaque tâche individuelle d’une [opération](https://developer.adobe.com/commerce/php/development/components/message-queues/bulk-operations/) en bloc, telle que l’importation ou l’exportation d’articles, la modification des prix à grande échelle et l’affectation de produits à un warehouse. Obligatoire lorsque l’option [**[!UICONTROL Admin bulk operations]**](https://experienceleague.adobe.com/en/docs/commerce-admin/config/catalog/inventory#admin-bulk-operations) est définie sur **[!UICONTROL Run asynchronously]**dans les paramètres de configuration du système d’administration. |                |                         |                     |
| `codegeneratorProcessor` | + | + | + |
| Génère de manière asynchrone des coupons en arrière-plan. Requis pour utiliser la fonction [génération de bons par lots](https://experienceleague.adobe.com/docs/commerce-admin/marketing/promotions/cart-rules/price-rules-cart-coupon.html#method-2%3A-generate-a-batch-of-coupons). |                |                         |                     |
| `commerce.eventing.event.publish` | + | + |                     |
| Vérifie les événements qui ont été enregistrés comme prioritaires dans Adobe événements d’E [/S pour Adobe Commerce](https://developer.adobe.com/commerce/events/get-started/). |
| `exportProcessor` | + | + | + |
| Empêche les délais d’expiration de connexion lors de l’exportation [](https://experienceleague.adobe.com/docs/commerce-admin/systems/data-transfer/data-export.html) de jeux de données volumineux (par exemple, 200 000 produits). |                |                         |                     |
| `inventoryQtyCounter` | + | + |                     |
| Corrige de manière asynchrone l’indice boursier après qu’une commande a été passée ou qu’un produit a été retiré. Obligatoire lorsque l’option [**[!UICONTROL Use deferred stock update]**](https://experienceleague.adobe.com/en/docs/commerce-admin/config/catalog/inventory#product-stock-options) est activée dans les paramètres de configuration de l’administrateur. Voir [Bonnes pratiques](https://experienceleague.adobe.com/docs/commerce-operations/performance-best-practices/configuration.html#deferred-stock-update) en matière de performances. |                |                         |                     |
| `inventory.source.items.cleanup` | + | + | + |
| Supprime de manière asynchrone les éléments source par SKU du produit lorsqu’un produit est supprimé. Obligatoire lorsque l’option de stock [**[!UICONTROL Synchronize with Catalog]**](https://experienceleague.adobe.com/en/docs/commerce-admin/config/catalog/inventory) est activée dans les paramètres de configuration du système d’administration. |                |                         |                     |
| `inventory.mass.update` | + | + | + |
| Traite de manière asynchrone les éléments de stock hérités, met à jour les éléments de stock hérités, met à jour les éléments source par défaut et réindexe l’inventaire pour des SKU de produit spécifiques. Obligatoire lorsque l’opération en bloc [**[!UICONTROL Run asynchronously]**](https://experienceleague.adobe.com/en/docs/commerce-admin/config/catalog/inventory#admin-bulk-operations) est activée dans les paramètres de configuration du système d’administration. |                |                         |                     |
| `inventory.reservations.cleanup` | + | + | + |
| Supprime de manière asynchrone les réservations par SKU de produit après la suppression d’un produit. Obligatoire lorsque l’option de stock [**[!UICONTROL Synchronize with Catalog]**](https://experienceleague.adobe.com/en/docs/commerce-admin/config/catalog/inventory) est activée dans les paramètres de configuration du système d’administration. |                |                         |                     |
| `inventory.reservations.update` | + | + | + |
| Met à jour de façon asynchrone les réservations par SKU de produit après la suppression d’un produit. Requis lorsque l’option d’achat d’actions [**[!UICONTROL Synchronize with Catalog]**](https://experienceleague.adobe.com/en/docs/commerce-admin/config/catalog/inventory) est activée dans les paramètres de configuration du système d’administration. |                |                         |                     |
| `inventory.reservations.updateSalabilityStatus` | + | + | + |
| Met à jour de manière asynchrone la quantité vendable de chaque produit affecté à un stock. Ce consommateur doit toujours être opérationnel si vous utilisez [!DNL Inventory Management]. |                |                         |                     |
| `inventory.indexer.sourceItem` | + | + | + |
| Réindexe les éléments sources de façon asynchrone. Obligatoire lorsque la variable [**[!UICONTROL Stock/Source reindex strategy]**](https://experienceleague.adobe.com/en/docs/commerce-admin/config/catalog/inventory#inventory-indexer-settings) est définie sur « [!UICONTROL asynchronous] » dans les paramètres de configuration du système d’administration. |                |                         |                     |
| `inventory.indexer.stock` | + | + | + |
| Réindexe les actions de façon asynchrone. Obligatoire lorsque la variable [**[!UICONTROL Stock/Source reindex strategy]**](https://experienceleague.adobe.com/en/docs/commerce-admin/config/catalog/inventory#inventory-indexer-settings) est définie sur « [!UICONTROL asynchronous] » dans les paramètres de configuration du système d’administration. |                |                         |                     |
| `matchCustomerSegmentProcessor` | + | + |                     |
| Crée une table de base de données temporaire, y déplace chaque [segment](https://experienceleague.adobe.com/en/docs/commerce-admin/customers/segments/customer-segments) de clients, supprime tous les segments qui correspondent à l’ID de segment et les copie dans les segments de clientèle en utilisant l’ID de segment comme indicateur. Tout cela est effectué dans une transaction de sorte que si quelque chose échoue, il rétablit la transaction à ce qu’elle était avant son exécution. Après une transaction, le consommateur supprime la table temporaire. |                |                         |                     |
| `media.content.synchronization` | + | + | + |
| Garantit que les liens vers les médias affectés pour les produits, les catégories, les blocs CMS et les pages CMS sont correctement attribués à la ressource. Supprime les anciennes ressources qui ne sont plus utilisées. |                |                         |                     |
| `media.gallery.renditions.update` | + | + | + |
| Génère et valide les chemins d’accès aux ressources multimédias. Le chemin d’accès absolu à un actif est déterminé par l’endroit où il se trouve sur le serveur depuis le répertoire des médias. Les images sont redimensionnées (si nécessaire) et copiées dans le répertoire multimédia à l’intérieur du chemin généré. |                |                         |                     |
| `media.gallery.synchronization` | + | + | + |
| Importe les fichiers image dans la table de base de `media_gallery_asset` données. |                |                         |                     |
| `media.storage.catalog.image.resize` | + | + | + |
| Redimensionne](https://developer.adobe.com/commerce/frontend-core/guide/themes/configure/#resize-catalog-images) les images de catalogue de façon [asynchrone. |                |                         |                     |
| `negotiableQuotePriceUpdate` |                | + |                     |
| Met à jour les prix des devis négociables. Obligatoire lorsque l’option [**[!UICONTROL Quotes]**](https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/quotes/quotes) est activée dans les paramètres de configuration du système d’administration. |                |                         |                     |
| `placeOrderProcessor` | + | + |                     |
| Traite de manière asynchrone les commandes](https://developer.adobe.com/commerce/php/module-reference/module-async-order/), qui marquent [les commandes comme reçues, les place dans la file d’attente des messages et les traite selon le principe du premier entré, premier sorti. Considéré comme une [meilleure pratique](../../implementation-playbook/best-practices/maintenance/order-processing-configuration.md) pour améliorer le nombre de commandes pouvant être traitées, car les clients n’ont pas besoin d’attendre la fin des processus backend avant de voir un message de réussite. |                |                         |                     |
| `product_action_attribute.update` | + | + | + |
| Écrit de manière asynchrone les modifications apportées aux attributs de produit dans la base de données après avoir utilisé l’administrateur pour [effectuer des mises à jour](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/create/bulk-product-attribute-update.html). |                |                         |                     |
| `product_action_attribute.website.update` | + | + | + |
| Après avoir utilisé l’administrateur pour [effectuer des mises à jour](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/create/bulk-product-attribute-update.html), écrit de manière asynchrone les modifications apportées aux attributs de produit pour une vue de magasin spécifique dans la base de données. |                |                         |                     |
| `product_alert` | + | + | + |
| Envoie des e-mails de notification aux clients au sujet des changements de prix et d’inventaire des produits. Obligatoire lorsque l’option Obligatoire lorsque l’option [**[!UICONTROL Product Alerts]**](https://experienceleague.adobe.com/docs/commerce-admin/inventory/configuration/product-alerts/alert-setup.html) est activée dans les paramètres de configuration du système d’administration. |                |                         |                     |
| `purchaseorder.toorder` |                | + |                     |
| Convertit la commande d’achat en [order](https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/purchase-orders/purchase-order-flow#approval-rules). Obligatoire lorsque l’option [**[!UICONTROL Purchase Order]**](https://experienceleague.adobe.com/docs/commerce-admin/b2b/purchase-orders/purchase-order-flow.html) est activée dans les paramètres de configuration du système d’administration. |                |                         |                     |
| `purchaseorder.transactional.email` |                | + |                     |
| Envoie le courrier électronique du bon de commande. Obligatoire lorsque l’option [**[!UICONTROL Purchase Order]**](https://experienceleague.adobe.com/docs/commerce-admin/b2b/purchase-orders/purchase-order-flow.html) est activée dans les paramètres de configuration du système d’administration. |                |                         |                     |
| `purchaseorder.validation` |                | + |                     |
| Valide le bon de commande par rapport aux règles](https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/purchase-orders/account-dashboard-approval-rules) d’approbation pertinentes[. Obligatoire lorsque l’option [**[!UICONTROL Purchase Order]**](https://experienceleague.adobe.com/docs/commerce-admin/b2b/purchase-orders/purchase-order-flow.html) est activée dans les paramètres de configuration du système d’administration. |                |                         |                     |
| `saveConfigProcessor` | + |                         | + |
| enregistre de manière asynchrone les modifications apportées à la configuration du magasin en plaçant les tâches d’enregistrement dans une file d’attente de messages, ce qui peut améliorer les performances sur les déploiements qui contiennent un grand nombre de configurations au niveau du magasin. Requis pour utiliser le module [`AsyncConfig`](../../performance/configuration.md#asynchronous-configuration-save). |                |                         |                     |
| `sales.rule.update.coupon.usage` | + | + | + |
| Empêche d’éviter le [problème](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/coupon-code-used-more-than-once-adobe-commerce.html) où les coupons à usage unique peuvent être utilisés plusieurs fois. |                |                         |                     |
| `sharedCatalogUpdateCategoryPermissions` |                | + |                     |
| Met à jour les catégories affectées à une catégorie de catalogue partagé. Obligatoire lorsque l’option [**[!UICONTROL Shared Catalogs]**](https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/shared-catalogs/catalog-shared) est activée dans les paramètres de configuration du système d’administration. |                |                         |                     |
| `sharedCatalogUpdatePrice` |                | + |                     |
| Met à jour le prix de chaque produit d’un catalogue partagé. Obligatoire lorsque l’option [**[!UICONTROL Shared Catalogs]**](https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/shared-catalogs/catalog-shared) est activée dans les paramètres de configuration du système d’administration. |                |                         |                     |
| `quoteItemCleaner` | + | + |                     |
| Supprime les devis invalides ou inactifs lorsqu’un produit est supprimé du catalogue ou du panier. Obligatoire lorsque l’option [**[!UICONTROL Quotes]**](https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/quotes/quotes) est activée dans les paramètres de configuration du système d’administration. |                |                         |                     |
| `sales.rule.quote.trigger.recollect` | + | + | + |
| Met à jour les paniers actifs pour prendre en compte les modifications de la règle de prix du panier. Obligatoire lors de la mise à jour de [**[!UICONTROL Catalog price rules]**](https://experienceleague.adobe.com/docs/commerce-admin/marketing/promotions/catalog-rules/price-rules-catalog.html). |                |                         |                     |

{style="table-layout:auto"}
