---
title: Consommateurs de files d'attente de messages
description: Découvrez les clients de la file d’attente des messages d’Adobe Commerce et de Magento Open Source, notamment les fonctionnalités et les paramètres de configuration système qui leur sont associés.
source-git-commit: 2eecaab32b090cfd3c1a8e8832027d3531cf0edc
workflow-type: tm+mt
source-wordcount: '929'
ht-degree: 0%

---


# Consommateurs de files d&#39;attente de messages

Le tableau suivant identifie tous les consommateurs de la file d’attente de messages, décrit ce qu’ils font et identifie les paramètres de configuration du système d’administration qui leur sont associés :

| Consommateur et description | Adobe Commerce | Adobe Commerce avec B2B | Magento Open Source |
|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------|-------------------------|---------------------|
| `async.operations.all` | + | + | + |
| Crée des messages pour chaque tâche d’une [opération en bloc](https://developer.adobe.com/commerce/php/development/components/message-queues/bulk-operations/), comme l’importation ou l’exportation d’articles, la modification des prix à grande échelle et l’affectation de produits à un entrepôt. Obligatoire lorsque la variable [**[!UICONTROL Admin bulk operations]**](https://docs.magento.com/user-guide/configuration/catalog/inventory.html?#admin-bulk-operations) est définie sur **[!UICONTROL Run asynchronously]**dans les paramètres de configuration du système d’administration. |  |  |  |
| `codegeneratorProcessor` | + | + | + |
| Génère de manière asynchrone des coupons en arrière-plan. Requis pour utiliser la variable [génération de bons par lots](https://experienceleague.adobe.com/docs/commerce-admin/marketing/promotions/cart-rules/price-rules-cart-coupon.html#method-2%3A-generate-a-batch-of-coupons) fonction . |  |  |  |
| `exportProcessor` | + | + | + |
| Empêche les délais de connexion pendant la [export](https://experienceleague.adobe.com/docs/commerce-admin/systems/data-transfer/data-export.html) de jeux de données volumineux (par exemple, 200 000 produits). |  |  |  |
| `inventoryQtyCounter` | + | + |  |
| Corrige de manière asynchrone l’index de stock après le passage d’une commande ou la suppression d’un produit. Obligatoire lorsque la variable [**[!UICONTROL Use deferred stock update]**](https://docs.magento.com/user-guide/configuration/catalog/inventory.html#product-stock-options) est activée dans les paramètres de configuration de l’administrateur. Voir [Bonnes pratiques en matière de performances](https://experienceleague.adobe.com/docs/commerce-operations/performance-best-practices/configuration.html#deferred-stock-update). |  |  |  |
| `inventory.source.items.cleanup` | + | + | + |
| Supprime de manière asynchrone les éléments source par SKU du produit lorsqu’un produit est supprimé. Obligatoire lorsque la variable [**[!UICONTROL Synchronize with Catalog]**](https://docs.magento.com/user-guide/configuration/catalog/inventory.html) l’option stock est activée dans les paramètres de configuration du système d’administration. |  |  |  |
| `inventory.mass.update` | + | + | + |
| Traite de manière asynchrone les éléments de stock hérités, met à jour les éléments de stock hérités, met à jour les éléments source par défaut et réindexe l’inventaire pour des SKU de produit spécifiques. Obligatoire lorsque la variable [**[!UICONTROL Run asynchronously]**](https://docs.magento.com/user-guide/configuration/catalog/inventory.html#admin-bulk-operations) l’opération en bloc est activée dans les paramètres de configuration du système d’administration. |  |  |  |
| `inventory.reservations.cleanup` | + | + | + |
| Supprime de manière asynchrone les réservations par SKU de produit après la suppression d’un produit. Obligatoire lorsque la variable [**[!UICONTROL Synchronize with Catalog]**](https://docs.magento.com/user-guide/configuration/catalog/inventory.html) l’option stock est activée dans les paramètres de configuration du système d’administration. |  |  |  |
| `inventory.reservations.update` | + | + | + |
| Met à jour de manière asynchrone les réservations par SKU de produit après la suppression d’un produit. Obligatoire lorsque la variable [**[!UICONTROL Synchronize with Catalog]**](https://docs.magento.com/user-guide/configuration/catalog/inventory.html) l’option stock est activée dans les paramètres de configuration du système d’administration. |  |  |  |
| `inventory.reservations.updateSalabilityStatus` | + | + | + |
| Met à jour de manière asynchrone la quantité vendable de chaque produit affecté à un stock. Ce consommateur doit toujours être opérationnel si vous utilisez [!DNL Inventory Management]. |  |  |  |
| `inventory.indexer.sourceItem` | + | + | + |
| Reindexe de manière asynchrone les éléments source. Obligatoire lorsque la variable [**[!UICONTROL Stock/Source reindex strategy]**](https://docs.magento.com/user-guide/configuration/catalog/inventory.html#inventory-indexer-settings) est défini sur &quot;[!UICONTROL asynchronous]&quot; dans les paramètres de configuration du système d’administration. |  |  |  |
| `inventory.indexer.stock` | + | + | + |
| Réindexe le stock de manière asynchrone. Obligatoire lorsque la variable [**[!UICONTROL Stock/Source reindex strategy]**](https://docs.magento.com/user-guide/configuration/catalog/inventory.html#inventory-indexer-settings) est défini sur &quot;[!UICONTROL asynchronous]&quot; dans les paramètres de configuration du système d’administration. |  |  |  |
| `matchCustomerSegmentProcessor` | + | + |  |
| Crée un tableau de base de données temporaire, déplace chaque [segment client](https://docs.magento.com/user-guide/marketing/customer-segments.html) dans , supprime tous les segments qui correspondent à l’ID de segment et les copie dans les segments client à l’aide de l’ID de segment comme indicateur. Tout cela est effectué dans une transaction de sorte que si quelque chose échoue, la transaction revient à ce qu’elle était avant son exécution. Après une transaction, le consommateur abandonne la table temporaire. |  |  |  |
| `media.content.synchronization` | + | + | + |
| Vérifie que les liens vers les médias attribués pour les produits, les catégories, les blocs CMS et les pages CMS sont correctement affectés à la ressource. Supprime les anciennes ressources qui ne sont plus utilisées. |  |  |  |
| `media.gallery.renditions.update` | + | + | + |
| Génère et valide les chemins d’accès aux ressources multimédia. Le chemin d’accès absolu à une ressource est déterminé par l’emplacement où elle se trouve sur le serveur à partir du répertoire multimédia. Les images sont redimensionnées (si nécessaire) et copiées dans le répertoire multimédia à l’intérieur du chemin d’accès généré. |  |  |  |
| `media.gallery.synchronization` | + | + | + |
| Importe les fichiers image dans le `media_gallery_asset` table de base de données. |  |  |  |
| `media.storage.catalog.image.resize` | + | + | + |
| Asynchrone [redimensionne](https://developer.adobe.com/commerce/frontend-core/guide/themes/configure/#resize-catalog-images) catalogue des images. |  |  |  |
| `negotiableQuotePriceUpdate` |  | + |  |
| Met à jour les prix des devis négociables. Obligatoire lorsque la variable [**[!UICONTROL Quotes]**](https://docs.magento.com/user-guide/sales/quotes.html) est activée dans les paramètres de configuration du système d’administration. |  |  |  |
| `placeOrderProcessor` | + | + |  |
| Asynchrone [commandes de processus](https://developer.adobe.com/commerce/php/module-reference/module-async-order/), qui marque les commandes comme reçues, les place dans la file d’attente des messages et les traite en fonction du premier entré. Considérée comme une [bonne pratique](../../implementation-playbook/best-practices/maintenance/order-processing-configuration.md) pour améliorer le nombre de commandes pouvant être traitées, car les clients n’ont pas besoin d’attendre la fin des processus principaux avant d’afficher un message de succès. |  |  |  |
| `product_action_attribute.update` | + | + | + |
| Après avoir utilisé l’option Admin pour écrire de manière asynchrone les modifications apportées aux attributs de produit dans la base de données [effectuer des mises à jour](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/create/bulk-product-attribute-update.html). |  |  |  |
| `product_action_attribute.website.update` | + | + | + |
| Après avoir utilisé l’option Admin pour [effectuer des mises à jour](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/create/bulk-product-attribute-update.html). |  |  |  |
| `product_alert` | + | + | + |
| Envoie des e-mails de notification aux clients au sujet des changements de prix et d’inventaire des produits. Obligatoire lorsque la variable [**[!UICONTROL Product Alerts]**](https://experienceleague.adobe.com/docs/commerce-admin/inventory/configuration/product-alerts/alert-setup.html) est activée dans les paramètres de configuration du système d’administration. |  |  |  |
| `purchaseorder.toorder` |  | + |  |
| Convertit le bon de commande en [order](https://docs.magento.com/user-guide/stores/b2b-purchase-order-flow.html#approval-rules). Obligatoire lorsque la variable [**[!UICONTROL Purchase Order]**](https://experienceleague.adobe.com/docs/commerce-admin/b2b/purchase-orders/purchase-order-flow.html) est activée dans les paramètres de configuration du système d’administration. |  |  |  |
| `purchaseorder.transactional.email` |  | + |  |
| Envoie des courriers électroniques de bon de commande. Obligatoire lorsque la variable [**[!UICONTROL Purchase Order]**](https://experienceleague.adobe.com/docs/commerce-admin/b2b/purchase-orders/purchase-order-flow.html) est activée dans les paramètres de configuration du système d’administration. |  |  |  |
| `purchaseorder.validation` |  | + |  |
| Valide le bon de commande par rapport à ce qui est pertinent [règles de validation](https://docs.magento.com/user-guide/customers/account-dashboard-approval-rules.html). Obligatoire lorsque la variable [**[!UICONTROL Purchase Order]**](https://experienceleague.adobe.com/docs/commerce-admin/b2b/purchase-orders/purchase-order-flow.html) est activée dans les paramètres de configuration du système d’administration. |  |  |  |
| `sales.rule.update.coupon.usage` | + | + | + |
| Empêche la variable [issue](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/coupon-code-used-more-than-once-adobe-commerce.html) où des bons à usage unique peuvent être utilisés plusieurs fois. |  |  |  |
| `sharedCatalogUpdateCategoryPermissions` |  | + |  |
| Met à jour les catégories affectées à une catégorie de catalogue partagée. Obligatoire lorsque la variable [**[!UICONTROL Shared Catalogs]**](https://docs.magento.com/user-guide/catalog/catalog-shared.html) est activée dans les paramètres de configuration du système d’administration. |  |  |  |
| `sharedCatalogUpdatePrice` |  | + |  |
| Met à jour le prix de chaque produit dans un catalogue partagé. Obligatoire lorsque la variable [**[!UICONTROL Shared Catalogs]**](https://docs.magento.com/user-guide/catalog/catalog-shared.html) est activée dans les paramètres de configuration du système d’administration. |  |  |  |
| `quoteItemCleaner` | + | + |  |
| Supprime les prix invalides ou inactifs lorsqu’un produit est supprimé du catalogue ou du panier. Obligatoire lorsque la variable [**[!UICONTROL Quotes]**](https://docs.magento.com/user-guide/sales/quotes.html) est activée dans les paramètres de configuration du système d’administration. |  |  |  |

{style=&quot;table-layout:auto&quot;}
