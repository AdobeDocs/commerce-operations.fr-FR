---
title: Consommateurs de file d’attente de messages
description: Découvrez Adobe Commerce et les consommateurs et consommatrices de files d’attente de messages de Magento Open Source, y compris les fonctionnalités et les paramètres de configuration système qui leur sont associés.
exl-id: 7fd7ab3f-581f-493c-956c-731f111d1b14
source-git-commit: 602a1ef82fcb8d30ff027db0fe0aacb981c7e08e
workflow-type: tm+mt
source-wordcount: '829'
ht-degree: 0%

---

# Consommateurs de file d’attente de messages

Le tableau suivant identifie tous les consommateurs de file d&#39;attente de messages, décrit leur action et identifie les paramètres de configuration du système d&#39;administration qui leur sont associés :

| Consommateur et description | Adobe Commerce | Adobe Commerce avec B2B | Magento Open Source |
|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------|-------------------------|---------------------|
| `async.operations.all` | + | + | + |
| Crée des messages pour chaque tâche individuelle d’une tâche [opération en bloc](https://developer.adobe.com/commerce/php/development/components/message-queues/bulk-operations/), par exemple l&#39;importation ou l&#39;exportation d&#39;articles, la modification des prix à grande échelle et l&#39;affectation de produits à un entrepôt. Obligatoire lorsque le [**[!UICONTROL Admin bulk operations]**](https://docs.magento.com/user-guide/configuration/catalog/inventory.html?#admin-bulk-operations) est définie sur **[!UICONTROL Run asynchronously]**dans les paramètres de configuration du système d’administration. |                |                         |                     |
| `codegeneratorProcessor` | + | + | + |
| Génère des coupons de manière asynchrone en arrière-plan. Obligatoire pour utiliser [génération de coupons par lots](https://experienceleague.adobe.com/docs/commerce-admin/marketing/promotions/cart-rules/price-rules-cart-coupon.html#method-2%3A-generate-a-batch-of-coupons) fonctionnalité. |                |                         |                     |
| `commerce.eventing.event.publish` | + | + |                     |
| Recherche les événements qui ont été enregistrés en priorité dans [Événements d’Adobe I/O pour Adobe Commerce](https://developer.adobe.com/commerce/events/get-started/). |
| `exportProcessor` | + | + | + |
| Empêche les temporisations de connexion pendant le [exportation](https://experienceleague.adobe.com/docs/commerce-admin/systems/data-transfer/data-export.html) de jeux de données volumineux (par exemple 200 000 produits). |                |                         |                     |
| `inventoryQtyCounter` | + | + |                     |
| Corrige de manière asynchrone l’indice de stock après la passation d’une commande ou la suppression d’un produit. Obligatoire lorsque le [**[!UICONTROL Use deferred stock update]**](https://docs.magento.com/user-guide/configuration/catalog/inventory.html#product-stock-options) est activée dans les paramètres de configuration d’Administration . Voir [Bonnes pratiques en matière de performances](https://experienceleague.adobe.com/docs/commerce-operations/performance-best-practices/configuration.html#deferred-stock-update). |                |                         |                     |
| `inventory.source.items.cleanup` | + | + | + |
| Supprime de manière asynchrone les éléments sources par SKU de produit lorsqu’un produit est supprimé. Obligatoire lorsque le [**[!UICONTROL Synchronize with Catalog]**](https://docs.magento.com/user-guide/configuration/catalog/inventory.html) L’option stock est activée dans les paramètres de configuration du système d’administration. |                |                         |                     |
| `inventory.mass.update` | + | + | + |
| Traite de manière asynchrone les éléments de stock hérités, met à jour les éléments de stock hérités, met à jour les éléments source par défaut et réindexe l’inventaire pour des SKU de produit spécifiques. Obligatoire lorsque le [**[!UICONTROL Run asynchronously]**](https://docs.magento.com/user-guide/configuration/catalog/inventory.html#admin-bulk-operations) L’opération en bloc est activée dans les paramètres de configuration du système d’administration. |                |                         |                     |
| `inventory.reservations.cleanup` | + | + | + |
| Supprime de manière asynchrone les réservations par SKU de produit après la suppression d’un produit. Obligatoire lorsque le [**[!UICONTROL Synchronize with Catalog]**](https://docs.magento.com/user-guide/configuration/catalog/inventory.html) L’option stock est activée dans les paramètres de configuration du système d’administration. |                |                         |                     |
| `inventory.reservations.update` | + | + | + |
| Met à jour les réservations de manière asynchrone par SKU de produit après la suppression d’un produit. Obligatoire lorsque le [**[!UICONTROL Synchronize with Catalog]**](https://docs.magento.com/user-guide/configuration/catalog/inventory.html) L’option stock est activée dans les paramètres de configuration du système d’administration. |                |                         |                     |
| `inventory.reservations.updateSalabilityStatus` | + | + | + |
| Met à jour de manière asynchrone la quantité vendable de chaque produit affecté à un stock. Ce client doit toujours être opérationnel si vous utilisez [!DNL Inventory Management]. |                |                         |                     |
| `inventory.indexer.sourceItem` | + | + | + |
| Réindexe les éléments sources de manière asynchrone. Obligatoire lorsque le [**[!UICONTROL Stock/Source reindex strategy]**](https://docs.magento.com/user-guide/configuration/catalog/inventory.html#inventory-indexer-settings) est défini sur « »[!UICONTROL asynchronous]» dans les paramètres de configuration du système d’administration. |                |                         |                     |
| `inventory.indexer.stock` | + | + | + |
| Réindexe le stock de manière asynchrone. Obligatoire lorsque le [**[!UICONTROL Stock/Source reindex strategy]**](https://docs.magento.com/user-guide/configuration/catalog/inventory.html#inventory-indexer-settings) est défini sur « »[!UICONTROL asynchronous]» dans les paramètres de configuration du système d’administration. |                |                         |                     |
| `matchCustomerSegmentProcessor` | + | + |                     |
| Crée une table de base de données temporaire et déplace chacune d&#39;elles [segment client](https://docs.magento.com/user-guide/marketing/customer-segments.html) dans celui-ci, supprime tous les segments qui correspondent à l’identifiant du segment et les copie dans les segments clients à l’aide de l’identifiant du segment comme indicateur. Tout cela est réalisé dans une transaction, de sorte que si quelque chose échoue, la transaction revient à ce qu’elle était avant son exécution. Après une transaction, le client supprime la table temporaire. |                |                         |                     |
| `media.content.synchronization` | + | + | + |
| Garantit que les liens vers les médias attribués pour les produits, les catégories, les blocs CMS et les pages CMS sont correctement attribués à la ressource. Supprime les anciennes ressources qui ne sont plus utilisées. |                |                         |                     |
| `media.gallery.renditions.update` | + | + | + |
| Génère et valide les chemins d’accès aux ressources multimédias. Le chemin d’accès absolu à une ressource est déterminé par son emplacement sur le serveur à partir du répertoire des médias. Les images sont redimensionnées (si nécessaire) et copiées dans le répertoire des médias à l’intérieur du chemin d’accès généré. |                |                         |                     |
| `media.gallery.synchronization` | + | + | + |
| Importe les fichiers image dans le `media_gallery_asset` table de base de données. |                |                         |                     |
| `media.storage.catalog.image.resize` | + | + | + |
| Asynchrone [redimensionne](https://developer.adobe.com/commerce/frontend-core/guide/themes/configure/#resize-catalog-images) images de catalogue. |                |                         |                     |
| `negotiableQuotePriceUpdate` |                | + |                     |
| Met à jour les prix des devis négociables. Obligatoire lorsque le [**[!UICONTROL Quotes]**](https://docs.magento.com/user-guide/sales/quotes.html) est activée dans les paramètres de configuration du système d’administration. |                |                         |                     |
| `placeOrderProcessor` | + | + |                     |
| Asynchrone [traite les commandes](https://developer.adobe.com/commerce/php/module-reference/module-async-order/)qui marque les commandes comme reçues, les place dans la file d’attente des messages et les traite selon le principe du premier entré, premier sorti. Considéré comme un [bonne pratique](../../implementation-playbook/best-practices/maintenance/order-processing-configuration.md) pour améliorer le nombre de commandes pouvant être traitées, car les clients n’ont pas besoin d’attendre que les processus principaux se terminent avant de voir un message de succès. |                |                         |                     |
| `product_action_attribute.update` | + | + | + |
| Écrit des modifications de manière asynchrone sur les attributs de produit dans la base de données après avoir utilisé l’Administration pour [effectuer des mises à jour](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/create/bulk-product-attribute-update.html). |                |                         |                     |
| `product_action_attribute.website.update` | + | + | + |
| Écrit de manière asynchrone les modifications apportées aux attributs de produit pour une vue de magasin spécifique dans la base de données après avoir utilisé l’Administration pour [effectuer des mises à jour](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/create/bulk-product-attribute-update.html). |                |                         |                     |
| `product_alert` | + | + | + |
| Envoie des e-mails de notification aux clients sur le prix des produits et les modifications de stock. Obligatoire lorsque l’option Obligatoire lorsque l’option [**[!UICONTROL Product Alerts]**](https://experienceleague.adobe.com/docs/commerce-admin/inventory/configuration/product-alerts/alert-setup.html) est activée dans les paramètres de configuration du système d’administration. |                |                         |                     |
| `purchaseorder.toorder` |                | + |                     |
| Convertit une commande fournisseur en [ordre](https://docs.magento.com/user-guide/stores/b2b-purchase-order-flow.html#approval-rules). Obligatoire lorsque le [**[!UICONTROL Purchase Order]**](https://experienceleague.adobe.com/docs/commerce-admin/b2b/purchase-orders/purchase-order-flow.html) est activée dans les paramètres de configuration du système d’administration. |                |                         |                     |
| `purchaseorder.transactional.email` |                | + |                     |
| Envoie les e-mails de bon de commande. Obligatoire lorsque le [**[!UICONTROL Purchase Order]**](https://experienceleague.adobe.com/docs/commerce-admin/b2b/purchase-orders/purchase-order-flow.html) est activée dans les paramètres de configuration du système d’administration. |                |                         |                     |
| `purchaseorder.validation` |                | + |                     |
| Valide la commande fournisseur par rapport à l&#39;élément pertinent [règles d’approbation](https://docs.magento.com/user-guide/customers/account-dashboard-approval-rules.html). Obligatoire lorsque le [**[!UICONTROL Purchase Order]**](https://experienceleague.adobe.com/docs/commerce-admin/b2b/purchase-orders/purchase-order-flow.html) est activée dans les paramètres de configuration du système d’administration. |                |                         |                     |
| `saveConfigProcessor` | + |                         | + |
| Enregistre les modifications apportées à la configuration de la boutique de manière asynchrone en plaçant les tâches d’enregistrement dans une file d’attente de messages, ce qui peut améliorer les performances sur les déploiements contenant un grand nombre de configurations au niveau de la boutique. Obligatoire pour utiliser [`AsyncConfig`](../../performance/configuration.md#asynchronous-configuration-save) module. |                |                         |                     |
| `sales.rule.update.coupon.usage` | + | + | + |
| Empêche l’ [problème](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/coupon-code-used-more-than-once-adobe-commerce.html) où les coupons à usage unique peuvent être utilisés plusieurs fois. |                |                         |                     |
| `sharedCatalogUpdateCategoryPermissions` |                | + |                     |
| Met à jour les catégories affectées à une catégorie de catalogue partagé. Obligatoire lorsque le [**[!UICONTROL Shared Catalogs]**](https://docs.magento.com/user-guide/catalog/catalog-shared.html) est activée dans les paramètres de configuration du système d’administration. |                |                         |                     |
| `sharedCatalogUpdatePrice` |                | + |                     |
| Met à jour le prix de chaque produit dans un catalogue partagé. Obligatoire lorsque le [**[!UICONTROL Shared Catalogs]**](https://docs.magento.com/user-guide/catalog/catalog-shared.html) est activée dans les paramètres de configuration du système d’administration. |                |                         |                     |
| `quoteItemCleaner` | + | + |                     |
| Supprime les devis non valides ou inactifs lorsqu&#39;un produit est supprimé du catalogue ou du panier. Obligatoire lorsque le [**[!UICONTROL Quotes]**](https://docs.magento.com/user-guide/sales/quotes.html) est activée dans les paramètres de configuration du système d’administration. |                |                         |                     |
| `sales.rule.quote.trigger.recollect` | + | + | + |
| Met à jour les paniers actifs pour prendre en compte les modifications apportées à la règle de prix de panier. Obligatoire lors de la mise à jour [**[!UICONTROL Catalog price rules]**](https://experienceleague.adobe.com/docs/commerce-admin/marketing/promotions/catalog-rules/price-rules-catalog.html). |                |                         |                     |

{style="table-layout:auto"}
