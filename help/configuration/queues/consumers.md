---
title: Consommateurs de files d'attente de messages
description: Découvrez les clients de la file d’attente de messages Adobe Commerce, notamment les fonctionnalités et les paramètres de configuration système qui leur sont associés.
exl-id: 7fd7ab3f-581f-493c-956c-731f111d1b14
source-git-commit: 95ea96a566b0579a22b2ba738bd4a4bceef8cd9c
workflow-type: tm+mt
source-wordcount: '824'
ht-degree: 0%

---

# Consommateurs de files d&#39;attente de messages

Le tableau suivant identifie tous les consommateurs de la file d’attente de messages, décrit ce qu’ils font et identifie les paramètres de configuration du système d’administration qui leur sont associés :

| Consommateur et description | Adobe Commerce | Adobe Commerce avec B2B | Magento Open Source |
|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------|-------------------------|---------------------|
| `async.operations.all` | + | + | + |
| Crée des messages pour chaque tâche individuelle d’une [opération en masse](https://developer.adobe.com/commerce/php/development/components/message-queues/bulk-operations/), comme importer ou exporter des articles, modifier les prix à grande échelle et affecter des produits à un entrepôt. Obligatoire lorsque l’option [**[!UICONTROL Admin bulk operations]**](https://experienceleague.adobe.com/en/docs/commerce-admin/config/catalog/inventory#admin-bulk-operations) est définie sur **[!UICONTROL Run asynchronously]**&#x200B;dans les paramètres de configuration du système d’administration. |                |                         |                     |
| `codegeneratorProcessor` | + | + | + |
| Génère de manière asynchrone des coupons en arrière-plan. Requis pour utiliser la fonction [génération de bons par lots](https://experienceleague.adobe.com/docs/commerce-admin/marketing/promotions/cart-rules/price-rules-cart-coupon.html#method-2%3A-generate-a-batch-of-coupons). |                |                         |                     |
| `commerce.eventing.event.publish` | + | + |                     |
| Vérifie les événements qui ont été enregistrés en priorité dans [Événements d’Adobe I/O pour Adobe Commerce](https://developer.adobe.com/commerce/events/get-started/). |
| `exportProcessor` | + | + | + |
| Empêche les délais de connexion pendant l’ [export](https://experienceleague.adobe.com/docs/commerce-admin/systems/data-transfer/data-export.html) des jeux de données volumineux (par exemple, 200 000 produits). |                |                         |                     |
| `inventoryQtyCounter` | + | + |                     |
| Corrige de manière asynchrone l’index de stock après le passage d’une commande ou la suppression d’un produit. Obligatoire lorsque l’option [**[!UICONTROL Use deferred stock update]**](https://experienceleague.adobe.com/en/docs/commerce-admin/config/catalog/inventory#product-stock-options) est activée dans les paramètres de configuration de l’administrateur. Voir [Bonnes pratiques de performances](https://experienceleague.adobe.com/docs/commerce-operations/performance-best-practices/configuration.html#deferred-stock-update). |                |                         |                     |
| `inventory.source.items.cleanup` | + | + | + |
| Supprime de manière asynchrone les éléments source par SKU du produit lorsqu’un produit est supprimé. Obligatoire lorsque l’option de stock [**[!UICONTROL Synchronize with Catalog]**](https://experienceleague.adobe.com/en/docs/commerce-admin/config/catalog/inventory) est activée dans les paramètres de configuration du système d’administration. |                |                         |                     |
| `inventory.mass.update` | + | + | + |
| Traite de manière asynchrone les éléments de stock hérités, met à jour les éléments de stock hérités, met à jour les éléments source par défaut et réindexe l’inventaire pour des SKU de produit spécifiques. Obligatoire lorsque l’opération en bloc [**[!UICONTROL Run asynchronously]**](https://experienceleague.adobe.com/en/docs/commerce-admin/config/catalog/inventory#admin-bulk-operations) est activée dans les paramètres de configuration du système d’administration. |                |                         |                     |
| `inventory.reservations.cleanup` | + | + | + |
| Supprime de manière asynchrone les réservations par SKU de produit après la suppression d’un produit. Obligatoire lorsque l’option de stock [**[!UICONTROL Synchronize with Catalog]**](https://experienceleague.adobe.com/en/docs/commerce-admin/config/catalog/inventory) est activée dans les paramètres de configuration du système d’administration. |                |                         |                     |
| `inventory.reservations.update` | + | + | + |
| Met à jour de manière asynchrone les réservations par SKU de produit après la suppression d’un produit. Obligatoire lorsque l’option de stock [**[!UICONTROL Synchronize with Catalog]**](https://experienceleague.adobe.com/en/docs/commerce-admin/config/catalog/inventory) est activée dans les paramètres de configuration du système d’administration. |                |                         |                     |
| `inventory.reservations.updateSalabilityStatus` | + | + | + |
| Met à jour de manière asynchrone la quantité vendable de chaque produit affecté à un stock. Ce consommateur doit toujours être opérationnel si vous utilisez [!DNL Inventory Management]. |                |                         |                     |
| `inventory.indexer.sourceItem` | + | + | + |
| Reindexe de manière asynchrone les éléments source. Obligatoire lorsque [**[!UICONTROL Stock/Source reindex strategy]**](https://experienceleague.adobe.com/en/docs/commerce-admin/config/catalog/inventory#inventory-indexer-settings) est défini sur &quot;[!UICONTROL asynchronous]&quot; dans les paramètres de configuration du système d’administration. |                |                         |                     |
| `inventory.indexer.stock` | + | + | + |
| Réindexe le stock de manière asynchrone. Obligatoire lorsque [**[!UICONTROL Stock/Source reindex strategy]**](https://experienceleague.adobe.com/en/docs/commerce-admin/config/catalog/inventory#inventory-indexer-settings) est défini sur &quot;[!UICONTROL asynchronous]&quot; dans les paramètres de configuration du système d’administration. |                |                         |                     |
| `matchCustomerSegmentProcessor` | + | + |                     |
| Crée une table de base de données temporaire, y déplace chaque [segment client](https://experienceleague.adobe.com/en/docs/commerce-admin/customers/segments/customer-segments), supprime tous les segments qui correspondent à l’ID de segment et les copie dans les segments client à l’aide de l’ID de segment comme indicateur. Tout cela est effectué dans une transaction de sorte que si quelque chose échoue, la transaction revient à ce qu’elle était avant qu’elle ne soit exécutée. Après une transaction, le consommateur abandonne la table temporaire. |                |                         |                     |
| `media.content.synchronization` | + | + | + |
| Vérifie que les liens vers les médias attribués pour les produits, les catégories, les blocs CMS et les pages CMS sont correctement affectés à la ressource. Supprime les anciennes ressources qui ne sont plus utilisées. |                |                         |                     |
| `media.gallery.renditions.update` | + | + | + |
| Génère et valide les chemins d’accès aux ressources multimédia. Le chemin d’accès absolu à une ressource est déterminé par l’emplacement où elle se trouve sur le serveur à partir du répertoire multimédia. Les images sont redimensionnées (si nécessaire) et copiées dans le répertoire multimédia à l’intérieur du chemin d’accès généré. |                |                         |                     |
| `media.gallery.synchronization` | + | + | + |
| Importe les fichiers image dans la table de base de données `media_gallery_asset`. |                |                         |                     |
| `media.storage.catalog.image.resize` | + | + | + |
| [redimensionne de manière asynchrone](https://developer.adobe.com/commerce/frontend-core/guide/themes/configure/#resize-catalog-images) les images du catalogue. |                |                         |                     |
| `negotiableQuotePriceUpdate` |                | + |                     |
| Met à jour les prix des devis négociables. Obligatoire lorsque l’option [**[!UICONTROL Quotes]**](https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/quotes/quotes) est activée dans les paramètres de configuration du système d’administration. |                |                         |                     |
| `placeOrderProcessor` | + | + |                     |
| [ traite de manière asynchrone les commandes](https://developer.adobe.com/commerce/php/module-reference/module-async-order/), qui marquent les commandes comme reçues, les place dans la file d’attente des messages et les traite de façon &quot;first-in-first-out&quot;. Considérée comme une [bonne pratique](../../implementation-playbook/best-practices/maintenance/order-processing-configuration.md) pour améliorer le nombre de commandes pouvant être traitées, car les clients n’ont pas besoin d’attendre la fin des processus du serveur principal avant d’afficher un message de succès. |                |                         |                     |
| `product_action_attribute.update` | + | + | + |
| Écrit de manière asynchrone les modifications apportées aux attributs de produit dans la base de données après avoir utilisé l’administrateur pour [effectuer des mises à jour](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/create/bulk-product-attribute-update.html). |                |                         |                     |
| `product_action_attribute.website.update` | + | + | + |
| Après avoir utilisé l’administrateur pour [effectuer des mises à jour](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/create/bulk-product-attribute-update.html), écrit de manière asynchrone les modifications apportées aux attributs de produit pour une vue de magasin spécifique dans la base de données. |                |                         |                     |
| `product_alert` | + | + | + |
| Envoie des e-mails de notification aux clients au sujet des changements de prix et d’inventaire des produits. Obligatoire lorsque l’option Obligatoire lorsque l’option [**[!UICONTROL Product Alerts]**](https://experienceleague.adobe.com/docs/commerce-admin/inventory/configuration/product-alerts/alert-setup.html) est activée dans les paramètres de configuration du système d’administration. |                |                         |                     |
| `purchaseorder.toorder` |                | + |                     |
| Convertit la commande d’achat en [order](https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/purchase-orders/purchase-order-flow#approval-rules). Obligatoire lorsque l’option [**[!UICONTROL Purchase Order]**](https://experienceleague.adobe.com/docs/commerce-admin/b2b/purchase-orders/purchase-order-flow.html) est activée dans les paramètres de configuration du système d’administration. |                |                         |                     |
| `purchaseorder.transactional.email` |                | + |                     |
| Envoie des courriers électroniques de bon de commande. Obligatoire lorsque l’option [**[!UICONTROL Purchase Order]**](https://experienceleague.adobe.com/docs/commerce-admin/b2b/purchase-orders/purchase-order-flow.html) est activée dans les paramètres de configuration du système d’administration. |                |                         |                     |
| `purchaseorder.validation` |                | + |                     |
| Valide la commande d’achat par rapport aux [règles d’approbation](https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/purchase-orders/account-dashboard-approval-rules) appropriées. Obligatoire lorsque l’option [**[!UICONTROL Purchase Order]**](https://experienceleague.adobe.com/docs/commerce-admin/b2b/purchase-orders/purchase-order-flow.html) est activée dans les paramètres de configuration du système d’administration. |                |                         |                     |
| `saveConfigProcessor` | + |                         | + |
| enregistre de manière asynchrone les modifications apportées à la configuration du magasin en plaçant les tâches d’enregistrement dans une file d’attente de messages, ce qui peut améliorer les performances sur les déploiements qui contiennent un grand nombre de configurations au niveau du magasin. Requis pour utiliser le module [`AsyncConfig`](../../performance/configuration.md#asynchronous-configuration-save). |                |                         |                     |
| `sales.rule.update.coupon.usage` | + | + | + |
| Permet d’éviter un problème en raison duquel les bons à usage unique peuvent être utilisés plusieurs fois. |                |                         |                     |
| `sharedCatalogUpdateCategoryPermissions` |                | + |                     |
| Met à jour les catégories affectées à une catégorie de catalogue partagée. Obligatoire lorsque l’option [**[!UICONTROL Shared Catalogs]**](https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/shared-catalogs/catalog-shared) est activée dans les paramètres de configuration du système d’administration. |                |                         |                     |
| `sharedCatalogUpdatePrice` |                | + |                     |
| Met à jour le prix de chaque produit dans un catalogue partagé. Obligatoire lorsque l’option [**[!UICONTROL Shared Catalogs]**](https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/shared-catalogs/catalog-shared) est activée dans les paramètres de configuration du système d’administration. |                |                         |                     |
| `quoteItemCleaner` | + | + |                     |
| Supprime les prix invalides ou inactifs lorsqu’un produit est supprimé du catalogue ou du panier. Obligatoire lorsque l’option [**[!UICONTROL Quotes]**](https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/quotes/quotes) est activée dans les paramètres de configuration du système d’administration. |                |                         |                     |
| `sales.rule.quote.trigger.recollect` | + | + | + |
| Met à jour les paniers actifs pour prendre en compte les modifications de la règle de prix du panier. Obligatoire lors de la mise à jour de [**[!UICONTROL Catalog price rules]**](https://experienceleague.adobe.com/docs/commerce-admin/marketing/promotions/catalog-rules/price-rules-catalog.html). |                |                         |                     |

{style="table-layout:auto"}
