---
title: Consommateurs de file d’attente de messages
description: Découvrez les consommateurs et consommatrices de files d’attente de messages d’Adobe Commerce, y compris les fonctionnalités et les paramètres de configuration système qui leur sont associés.
exl-id: 7fd7ab3f-581f-493c-956c-731f111d1b14
source-git-commit: 95ea96a566b0579a22b2ba738bd4a4bceef8cd9c
workflow-type: tm+mt
source-wordcount: '824'
ht-degree: 0%

---

# Consommateurs de file d’attente de messages

Le tableau suivant identifie tous les clients de file d&#39;attente de messages, décrit leur fonctionnement et identifie les paramètres de configuration du système d&#39;administration qui leur sont associés :

| Consommateur et description | Adobe Commerce | Adobe Commerce avec B2B | Magento Open Source |
|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------|-------------------------|---------------------|
| `async.operations.all` | + | + | + |
| Crée des messages pour chaque tâche individuelle d&#39;une [opération en masse](https://developer.adobe.com/commerce/php/development/components/message-queues/bulk-operations/), comme l&#39;importation ou l&#39;exportation d&#39;articles, la modification des prix à grande échelle et l&#39;affectation de produits à un entrepôt. Obligatoire lorsque l’option [**[!UICONTROL Admin bulk operations]**](https://experienceleague.adobe.com/en/docs/commerce-admin/config/catalog/inventory#admin-bulk-operations) est définie sur **[!UICONTROL Run asynchronously]**&#x200B;dans les paramètres de configuration du système d’administration. |                |                         |                     |
| `codegeneratorProcessor` | + | + | + |
| Génère des coupons de manière asynchrone en arrière-plan. Obligatoire pour utiliser la fonctionnalité [génération de coupons par lots](https://experienceleague.adobe.com/docs/commerce-admin/marketing/promotions/cart-rules/price-rules-cart-coupon.html#method-2%3A-generate-a-batch-of-coupons). |                |                         |                     |
| `commerce.eventing.event.publish` | + | + |                     |
| Recherche les événements enregistrés en priorité dans [Adobe I/O Events pour Adobe Commerce](https://developer.adobe.com/commerce/events/get-started/). |
| `exportProcessor` | + | + | + |
| Empêche les temporisations de connexion lors de l’[exportation](https://experienceleague.adobe.com/docs/commerce-admin/systems/data-transfer/data-export.html) de jeux de données volumineux (par exemple, 200 000 produits). |                |                         |                     |
| `inventoryQtyCounter` | + | + |                     |
| Corrige l’index de stock de manière asynchrone après la passation d’une commande ou la suppression d’un produit. Obligatoire lorsque l’option [**[!UICONTROL Use deferred stock update]**](https://experienceleague.adobe.com/en/docs/commerce-admin/config/catalog/inventory#product-stock-options) est activée dans les paramètres de configuration d’administration. Voir [ Bonnes pratiques en matière de performances ](https://experienceleague.adobe.com/docs/commerce-operations/performance-best-practices/configuration.html#deferred-stock-update). |                |                         |                     |
| `inventory.source.items.cleanup` | + | + | + |
| Supprime de manière asynchrone les éléments sources par SKU de produit lorsqu’un produit est supprimé. Obligatoire lorsque l’option de stock [**[!UICONTROL Synchronize with Catalog]**](https://experienceleague.adobe.com/en/docs/commerce-admin/config/catalog/inventory) est activée dans les paramètres de configuration du système d’administration. |                |                         |                     |
| `inventory.mass.update` | + | + | + |
| Traite de manière asynchrone les éléments de stock hérités, met à jour les éléments de stock hérités, met à jour les éléments source par défaut et réindexe l’inventaire pour des SKU de produit spécifiques. Obligatoire lorsque l’opération [**[!UICONTROL Run asynchronously]**](https://experienceleague.adobe.com/en/docs/commerce-admin/config/catalog/inventory#admin-bulk-operations) en bloc est activée dans les paramètres de configuration du système d’administration. |                |                         |                     |
| `inventory.reservations.cleanup` | + | + | + |
| Supprime les réservations de manière asynchrone par SKU de produit après la suppression d’un produit. Obligatoire lorsque l’option de stock [**[!UICONTROL Synchronize with Catalog]**](https://experienceleague.adobe.com/en/docs/commerce-admin/config/catalog/inventory) est activée dans les paramètres de configuration du système d’administration. |                |                         |                     |
| `inventory.reservations.update` | + | + | + |
| Met à jour les réservations de manière asynchrone par SKU de produit après la suppression d’un produit. Obligatoire lorsque l’option de stock [**[!UICONTROL Synchronize with Catalog]**](https://experienceleague.adobe.com/en/docs/commerce-admin/config/catalog/inventory) est activée dans les paramètres de configuration du système d’administration. |                |                         |                     |
| `inventory.reservations.updateSalabilityStatus` | + | + | + |
| Met à jour de manière asynchrone la quantité vendable de chaque produit affecté à un stock. Ce client doit toujours être opérationnel si vous utilisez [!DNL Inventory Management]. |                |                         |                     |
| `inventory.indexer.sourceItem` | + | + | + |
| Réindexe les éléments sources de manière asynchrone. Obligatoire lorsque la [**[!UICONTROL Stock/Source reindex strategy]**](https://experienceleague.adobe.com/en/docs/commerce-admin/config/catalog/inventory#inventory-indexer-settings) est définie sur « [!UICONTROL asynchronous] » dans les paramètres de configuration du système d’administration. |                |                         |                     |
| `inventory.indexer.stock` | + | + | + |
| Réindexe le stock de manière asynchrone. Obligatoire lorsque la [**[!UICONTROL Stock/Source reindex strategy]**](https://experienceleague.adobe.com/en/docs/commerce-admin/config/catalog/inventory#inventory-indexer-settings) est définie sur « [!UICONTROL asynchronous] » dans les paramètres de configuration du système d’administration. |                |                         |                     |
| `matchCustomerSegmentProcessor` | + | + |                     |
| Crée une table de base de données temporaire, y déplace chaque [segment client](https://experienceleague.adobe.com/en/docs/commerce-admin/customers/segments/customer-segments), supprime tous les segments correspondant à l’identifiant du segment et les copie dans les segments clients en utilisant l’identifiant du segment comme indicateur. Tout cela est réalisé dans une transaction, de sorte que si quelque chose échoue, la transaction revient à ce qu’elle était avant son exécution. Après une transaction, le client supprime la table temporaire. |                |                         |                     |
| `media.content.synchronization` | + | + | + |
| Garantit que les liens vers les médias attribués aux produits, catégories, blocs CMS et pages CMS sont correctement attribués à la ressource. Supprime les anciennes ressources qui ne sont plus utilisées. |                |                         |                     |
| `media.gallery.renditions.update` | + | + | + |
| Génère et valide des chemins d’accès aux ressources multimédias. Le chemin d’accès absolu à une ressource est déterminé par son emplacement sur le serveur à partir du répertoire des médias. Les images sont redimensionnées (si nécessaire) et copiées dans le répertoire des médias, à l’intérieur du chemin d’accès généré. |                |                         |                     |
| `media.gallery.synchronization` | + | + | + |
| Importe les fichiers image dans la table de base de données `media_gallery_asset`. |                |                         |                     |
| `media.storage.catalog.image.resize` | + | + | + |
| [redimensionne](https://developer.adobe.com/commerce/frontend-core/guide/themes/configure/#resize-catalog-images) images de catalogue de manière asynchrone. |                |                         |                     |
| `negotiableQuotePriceUpdate` |                | + |                     |
| Met à jour les prix des devis négociables. Obligatoire lorsque l’option [**[!UICONTROL Quotes]**](https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/quotes/quotes) est activée dans les paramètres de configuration du système d’administration. |                |                         |                     |
| `placeOrderProcessor` | + | + |                     |
| Asynchrone [traite les commandes](https://developer.adobe.com/commerce/php/module-reference/module-async-order/), qui marquent les commandes comme reçues, les place dans la file d’attente des messages et les traite selon le principe du premier entré, premier sorti. Considérée comme une [bonne pratique](../../implementation-playbook/best-practices/maintenance/order-processing-configuration.md) pour améliorer le nombre de commandes qui peuvent être traitées, car les clients n’ont pas besoin d’attendre que les processus principaux soient terminés avant de voir un message de succès. |                |                         |                     |
| `product_action_attribute.update` | + | + | + |
| Écrit des modifications de manière asynchrone sur les attributs de produit dans la base de données après avoir utilisé l’Administration pour [effectuer des mises à jour](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/create/bulk-product-attribute-update.html). |                |                         |                     |
| `product_action_attribute.website.update` | + | + | + |
| Écrit de manière asynchrone les modifications apportées aux attributs de produit pour une vue de magasin spécifique dans la base de données après avoir utilisé l’Administration pour [effectuer des mises à jour](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/create/bulk-product-attribute-update.html). |                |                         |                     |
| `product_alert` | + | + | + |
| Envoie des e-mails de notification aux clients sur le prix des produits et les modifications de stock. Obligatoire lorsque l’option Obligatoire lorsque l’option [**[!UICONTROL Product Alerts]**](https://experienceleague.adobe.com/docs/commerce-admin/inventory/configuration/product-alerts/alert-setup.html) est activée dans les paramètres de configuration du système d’administration. |                |                         |                     |
| `purchaseorder.toorder` |                | + |                     |
| Convertit une commande fournisseur en [commande](https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/purchase-orders/purchase-order-flow#approval-rules). Obligatoire lorsque l’option [**[!UICONTROL Purchase Order]**](https://experienceleague.adobe.com/docs/commerce-admin/b2b/purchase-orders/purchase-order-flow.html) est activée dans les paramètres de configuration du système d’administration. |                |                         |                     |
| `purchaseorder.transactional.email` |                | + |                     |
| Envoie les e-mails de bon de commande. Obligatoire lorsque l’option [**[!UICONTROL Purchase Order]**](https://experienceleague.adobe.com/docs/commerce-admin/b2b/purchase-orders/purchase-order-flow.html) est activée dans les paramètres de configuration du système d’administration. |                |                         |                     |
| `purchaseorder.validation` |                | + |                     |
| Valide la commande fournisseur par rapport aux [règles d&#39;approbation](https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/purchase-orders/account-dashboard-approval-rules) pertinentes. Obligatoire lorsque l’option [**[!UICONTROL Purchase Order]**](https://experienceleague.adobe.com/docs/commerce-admin/b2b/purchase-orders/purchase-order-flow.html) est activée dans les paramètres de configuration du système d’administration. |                |                         |                     |
| `saveConfigProcessor` | + |                         | + |
| Enregistre les modifications apportées à la configuration du magasin de manière asynchrone en plaçant les tâches d’enregistrement dans une file d’attente de messages, ce qui peut améliorer les performances sur les déploiements contenant un grand nombre de configurations au niveau du magasin. Obligatoire pour utiliser le module [`AsyncConfig`](../../performance/configuration.md#asynchronous-configuration-save). |                |                         |                     |
| `sales.rule.update.coupon.usage` | + | + | + |
| Évite les problèmes en raison desquels les coupons à usage unique peuvent être utilisés plusieurs fois. |                |                         |                     |
| `sharedCatalogUpdateCategoryPermissions` |                | + |                     |
| Met à jour les catégories affectées à une catégorie de catalogue partagé. Obligatoire lorsque l’option [**[!UICONTROL Shared Catalogs]**](https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/shared-catalogs/catalog-shared) est activée dans les paramètres de configuration du système d’administration. |                |                         |                     |
| `sharedCatalogUpdatePrice` |                | + |                     |
| Met à jour le prix de chaque produit dans un catalogue partagé. Obligatoire lorsque l’option [**[!UICONTROL Shared Catalogs]**](https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/shared-catalogs/catalog-shared) est activée dans les paramètres de configuration du système d’administration. |                |                         |                     |
| `quoteItemCleaner` | + | + |                     |
| Supprime les devis non valides ou inactifs lorsqu&#39;un produit est supprimé du catalogue ou du panier. Obligatoire lorsque l’option [**[!UICONTROL Quotes]**](https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/quotes/quotes) est activée dans les paramètres de configuration du système d’administration. |                |                         |                     |
| `sales.rule.quote.trigger.recollect` | + | + | + |
| Met à jour les paniers actifs pour prendre en compte les modifications apportées à la règle de prix de panier. Requis lors de la mise à jour des [**[!UICONTROL Catalog price rules]**](https://experienceleague.adobe.com/docs/commerce-admin/marketing/promotions/catalog-rules/price-rules-catalog.html). |                |                         |                     |

{style="table-layout:auto"}
