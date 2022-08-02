---
title: Référence sur les chemins de configuration des ventes
description: Consultez la liste des valeurs de configuration des ventes.
source-git-commit: bd1bf6edd131ec93902246e95ce857b509f2a619
workflow-type: tm+mt
source-wordcount: '1500'
ht-degree: 0%

---


# Référence sur les chemins de configuration des ventes

Cette section répertorie les noms de variable et les chemins de configuration disponibles pour les options dans l’Admin sous **Magasins** > Paramètres > **Configuration** > **Ventes**.

Le [`magento app:config:dump` command](../cli/export-configuration.md) écrit ces valeurs dans le fichier de configuration partagé, `app/etc/config.php`, qui doit être dans le contrôle de code source. Pour éventuellement remplacer des paramètres de configuration ou définir des paramètres sensibles, voir [Utilisation des variables d’environnement pour remplacer les paramètres de configuration](override-config-settings.md#environment-variables). Cette rubrique fonctionne _not_ list [valeurs sensibles et spécifiques au système](config-reference-sens.md).

## Chemins de vente

Ces valeurs de configuration sont disponibles dans l’ Admin de **Magasins** > Paramètres > **Configuration** > **Ventes** > **Ventes**.

| Nom | Chemin de configuration | Commerce uniquement ? |
|--------------|--------------|--------------|
| Masquer l’adresse IP du client | `sales/general/hide_customer_ip` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sous-total | `sales/totals_sort/subtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Remise | `sales/totals_sort/discount` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Expédition | `sales/totals_sort/shipping` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Taxe | `sales/totals_sort/tax` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Taxe sur les produits fixe | `sales/totals_sort/weee` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total général | `sales/totals_sort/grand_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Fiches d’assistance | `sales/totals_sort/giftcardaccount` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Crédit de la boutique | `sales/totals_sort/customerbalance` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Autoriser la réorganisation | `sales/reorder/allow` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Logo pour les impressions de PDF (200x50) | `sales/identity/logo` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Logo pour l’affichage d’impression par HTML | `sales/identity/logo_html` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Adresse | `sales/identity/address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activer | `sales/minimum_order/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Quantité minimale | `sales/minimum_order/amount` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Inclure la taxe au montant | `sales/minimum_order/tax_including` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Description Message | `sales/minimum_order/description` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Erreur à afficher dans le panier | `sales/minimum_order/error_message` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Validation séparée de chaque adresse dans le passage en caisse multi-adresses | `sales/minimum_order/multi_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Message de description à plusieurs adresses | `sales/minimum_order/multi_address_description` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Erreur à plusieurs adresses à afficher dans le panier | `sales/minimum_order/multi_address_error_message` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Utiliser des données agrégées | `sales/dashboard/use_aggregated_data` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Durée de vie de la commande en attente (minutes) | `sales/orders/delete_pending_after` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Autoriser les messages cadeau au niveau de la commande | `sales/gift_options/allow_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Autorisation des messages de cadeau pour les articles de commande | `sales/gift_options/allow_items` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Autoriser l’encapsulage des cadeaux au niveau de la commande | `sales/gift_options/wrapping_allow_order` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Autoriser le encapsulage des cadeaux pour les éléments de commande | `sales/gift_options/wrapping_allow_items` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Autoriser la réception de cadeau | `sales/gift_options/allow_gift_receipt` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Autoriser la carte imprimée | `sales/gift_options/allow_printed_card` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Prix par défaut pour la carte imprimée | `sales/gift_options/printed_card_price` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Activer MAP | `sales/msrp/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Afficher le prix réel | `sales/msrp/display_price_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Message de texte contextuel par défaut | `sales/msrp/explanation_message` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Message texte par défaut &quot;What&#39;s This&quot; | `sales/msrp/explanation_message_whats_this` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activation de la commande par SKU sur mon compte dans Storefront | `sales/product_sku/my_account_enable` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Activé | `sales/instant_purchase/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Texte de bouton | `sales/instant_purchase/button_text` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Groupes de clients | `sales/product_sku/allowed_groups` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Activer l’archivage | `sales/magento_salesarchive/active` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Archiver les commandes achetées | `sales/magento_salesarchive/age` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| États de commande à archiver | `sales/magento_salesarchive/order_statuses` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Activation de RMA sur Storefront | `sales/magento_rma/enabled` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Activation de la RAM au niveau du produit | `sales/magento_rma/enabled_on_product` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Utiliser l’adresse du magasin | `sales/magento_rma/use_store_address` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |

{style=&quot;table-layout:auto&quot;}

## Chemins des emails de vente

Ces valeurs de configuration sont disponibles dans l’ Admin de **Magasins** > Paramètres > **Configuration** > **Ventes** > **Courriers électroniques de vente**.

| Nom | Chemin de configuration | Commerce uniquement ? |
|--------------|--------------|--------------|
| Envoi asynchrone | `sales_email/general/async_sending` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activé | `sales_email/order/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nouvel expéditeur d’email de confirmation de commande | `sales_email/order/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nouveau modèle de confirmation de commande | `sales_email/order/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nouveau modèle de confirmation de commande pour l’invité | `sales_email/order/guest_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Méthode Envoyer la copie de courrier électronique de commande | `sales_email/order/copy_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activé | `sales_email/order_comment/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Envoyer un courrier électronique aux commentaires de commande | `sales_email/order_comment/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modèle de courrier électronique de commentaire de commande | `sales_email/order_comment/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modèle d’e-mail de commentaire de commande pour l’invité | `sales_email/order_comment/guest_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Méthode Envoyer la copie de courrier électronique des commentaires de commande | `sales_email/order_comment/copy_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activé | `sales_email/invoice/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Expéditeur des courriers électroniques de facturation | `sales_email/invoice/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modèle de courrier électronique de facturation | `sales_email/invoice/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modèle de courrier électronique de facturation pour l’invité | `sales_email/invoice/guest_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Méthode d’envoi d’une copie de courrier électronique de facturation | `sales_email/invoice/copy_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activé | `sales_email/invoice_comment/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Expéditeur du message de commentaire de facture | `sales_email/invoice_comment/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modèle d’e-mail de commentaire de facture | `sales_email/invoice_comment/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modèle d’e-mail de commentaire de facture pour l’invité | `sales_email/invoice_comment/guest_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Méthode Envoyer les commentaires de facture par courrier électronique | `sales_email/invoice_comment/copy_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activé | `sales_email/shipment/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Expéditeur des emails | `sales_email/shipment/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modèle de courrier électronique d’envoi | `sales_email/shipment/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modèle de courrier électronique d’envoi pour l’invité | `sales_email/shipment/guest_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Méthode Envoyer la copie d’email d’envoi | `sales_email/shipment/copy_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activé | `sales_email/shipment_comment/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Expéditeur d’e-mails de commentaire d’envoi | `sales_email/shipment_comment/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modèle d’e-mail de commentaire d’envoi | `sales_email/shipment_comment/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modèle d’e-mail de commentaire d’envoi pour l’invité | `sales_email/shipment_comment/guest_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Envoyer des commentaires Envoyer une copie d’email | `sales_email/shipment_comment/copy_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activé | `sales_email/creditmemo/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Expéditeur d’e-mails de notes de crédit | `sales_email/creditmemo/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modèle d’e-mail de note de crédit | `sales_email/creditmemo/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modèle d’e-mail de note de crédit pour l’invité | `sales_email/creditmemo/guest_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Méthode d’envoi d’une copie de courrier électronique de note de crédit | `sales_email/creditmemo/copy_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activé | `sales_email/creditmemo_comment/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Commentaire de la note de crédit Expéditeur du courrier électronique | `sales_email/creditmemo_comment/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modèle d’e-mail de commentaire de note de crédit | `sales_email/creditmemo_comment/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modèle d’e-mail de commentaire de note de crédit pour l’invité | `sales_email/creditmemo_comment/guest_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Envoyer des commentaires de note de crédit Méthode de copie de courrier électronique | `sales_email/creditmemo_comment/copy_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activé | `sales_email/magento_rma/enabled` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| RMA Email Sender | `sales_email/magento_rma/identity` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Modèle de courrier électronique RMA | `sales_email/magento_rma/template` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Modèle de courrier électronique RMA pour l’invité | `sales_email/magento_rma/guest_template` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Méthode d’envoi d’une copie de courrier électronique RMA | `sales_email/magento_rma/copy_method` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Activé | `sales_email/magento_rma_auth/enabled` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Expéditeur d’email d’autorisation RMA | `sales_email/magento_rma_auth/identity` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Modèle de courrier électronique d’autorisation RMA | `sales_email/magento_rma_auth/template` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Modèle de courrier électronique d’autorisation RMA pour l’invité | `sales_email/magento_rma_auth/guest_template` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Envoyer la méthode de copie d’email d’autorisation RMA | `sales_email/magento_rma_auth/copy_method` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Activé | `sales_email/magento_rma_comment/enabled` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| RMA Comment Email Sender | `sales_email/magento_rma_comment/identity` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Modèle d’e-mail de commentaire RMA | `sales_email/magento_rma_comment/template` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Modèle d’e-mail de commentaire RMA pour l’invité | `sales_email/magento_rma_comment/guest_template` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Méthode d’envoi d’une copie de courrier électronique RMA | `sales_email/magento_rma_comment/copy_method` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Activé | `sales_email/magento_rma_customer_comment/enabled` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| RMA Comment Email Sender | `sales_email/magento_rma_customer_comment/identity` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Destinataire de l’e-mail de commentaire RMA | `sales_email/magento_rma_customer_comment/recipient` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Modèle d’e-mail de commentaire RMA | `sales_email/magento_rma_customer_comment/template` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Méthode d’envoi d’une copie de courrier électronique RMA | `sales_email/magento_rma_customer_comment/copy_method` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Afficher l’identifiant de l’ordre dans l’en-tête | `sales_pdf/invoice/put_order_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Afficher l’identifiant de l’ordre dans l’en-tête | `sales_pdf/shipment/put_order_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Afficher l’identifiant de l’ordre dans l’en-tête | `sales_pdf/creditmemo/put_order_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style=&quot;table-layout:auto&quot;}

## Chemins des taxes

Ces valeurs de configuration sont disponibles dans l’ Admin de **Magasins** > Paramètres > **Configuration** > **Ventes** > **Taxe**.

| Nom | Chemin de configuration | Commerce uniquement ? |
|--------------|--------------|--------------|
| Classe fiscale d’expédition | `tax/classes/shipping_tax_class` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Classe fiscale des options de cadeau | `tax/classes/wrapping_tax_class` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Classe de taxe par défaut pour le produit | `tax/classes/default_product_tax_class` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Classe de taxe par défaut pour le client | `tax/classes/default_customer_tax_class` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Méthode de calcul de la taxe basée sur | `tax/calculation/algorithm` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Calcul de la taxe basé sur | `tax/calculation/based_on` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Prix du catalogue | `tax/calculation/price_includes_tax` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Prix de livraison | `tax/calculation/shipping_includes_tax` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Appliquer la taxe client | `tax/calculation/apply_after_discount` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Appliquer Une Remise Sur Les Prix | `tax/calculation/discount_tax` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Appliquer la taxe sur | `tax/calculation/apply_tax_on` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activer le commerce transfrontalier | `tax/calculation/cross_border_trade_enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pays par défaut | `tax/defaults/country` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| État par défaut | `tax/defaults/region` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Code de publication par défaut | `tax/defaults/postcode` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Afficher les prix des produits dans le catalogue | `tax/display/type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Afficher les prix de livraison | `tax/display/shipping` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Prix d&#39;affichage | `tax/cart_display/price` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sous-total d’affichage | `tax/cart_display/subtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Afficher le montant de livraison | `tax/cart_display/shipping` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Afficher les prix de l’emballage cadeau | `tax/cart_display/gift_wrapping` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Afficher les prix des cartes imprimées | `tax/cart_display/printed_card` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Inclure la taxe dans le total de la commande | `tax/cart_display/grandtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Afficher le résumé complet des taxes | `tax/cart_display/full_summary` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Afficher le sous-total de taxe nulle | `tax/cart_display/zero_tax` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Prix d&#39;affichage | `tax/sales_display/price` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sous-total d’affichage | `tax/sales_display/subtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Afficher le montant de livraison | `tax/sales_display/shipping` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Afficher les prix de l’emballage cadeau | `tax/sales_display/gift_wrapping` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Afficher les prix des cartes imprimées | `tax/sales_display/printed_card` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Inclure la taxe dans le total de la commande | `tax/sales_display/grandtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Afficher le résumé complet des taxes | `tax/sales_display/full_summary` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Afficher le sous-total de taxe nulle | `tax/sales_display/zero_tax` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activer FPT | `tax/weee/enable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Afficher les prix dans les listes de produits | `tax/weee/display_list` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Afficher les prix sur la page Affichage du produit | `tax/weee/display` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Prix d’affichage dans les modules de vente | `tax/weee/display_sales` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Prix D&#39;Affichage Des Emails | `tax/weee/display_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Appliquer la taxe à FPT | `tax/weee/apply_vat` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Inclure le FPT dans le sous-total | `tax/weee/include_in_subtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style=&quot;table-layout:auto&quot;}

## Chemins de passage en caisse

Ces valeurs de configuration sont disponibles dans l’ Admin de **Magasins** > Paramètres > **Configuration** > **Ventes** > **Passage en caisse**.

| Nom | Chemin de configuration | Commerce uniquement ? |
|--------------|--------------|--------------|
| Activation du passage en caisse d’une page | `checkout/options/onepage_checkout_enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Autoriser le passage en caisse des invités | `checkout/options/guest_checkout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Afficher l’adresse de facturation sur | `checkout/options/display_billing_address_on` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activation des termes et conditions | `checkout/options/enable_agreements` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Durée de vie des citations (jours) | `checkout/cart/delete_quote_after` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Après avoir ajouté une redirection de produit au panier | `checkout/cart/redirect_to_cart` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Image de produit groupé | `checkout/cart/grouped_product_image` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Image de produit configurable | `checkout/cart/configurable_product_image` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aperçu de la durée de vie des citations (minutes) | `checkout/cart/preview_quota_lifetime` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Afficher le résumé du panier | `checkout/cart_link/use_qty` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Afficher la barre latérale du panier | `checkout/sidebar/display` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nombre maximal d’éléments récemment ajoutés | `checkout/sidebar/count` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Échec du paiement de l’expéditeur du courrier électronique | `checkout/payment_failed/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Récepteur de courrier électronique en échec de paiement | `checkout/payment_failed/receiver` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modèle de paiement en échec | `checkout/payment_failed/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Envoyer le mode de copie de courrier électronique en échec du paiement | `checkout/payment_failed/copy_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style=&quot;table-layout:auto&quot;}

## Chemins d’accès des paramètres d’expédition

Ces valeurs de configuration sont disponibles dans l’ Admin de **Magasins** > Paramètres > **Configuration** > **Ventes** > **Paramètres d’expédition**.

| Nom | Chemin de configuration | Commerce uniquement ? |
|--------------|--------------|--------------|
| Appliquer une politique d’expédition personnalisée | `shipping/shipping_policy/enable_shipping_policy` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Politique d&#39;expédition | `shipping/shipping_policy/shipping_policy_content` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style=&quot;table-layout:auto&quot;}

## Chemins des paramètres de multidiffusion

Ces valeurs de configuration sont disponibles dans l’ Admin de **Magasins** > Paramètres > **Configuration** > **Ventes** > **Paramètres de multidiffusion**.

| Nom | Chemin de configuration | Commerce uniquement ? |
|--------------|--------------|--------------|
| Autorisation de l’expédition vers plusieurs adresses | `multishipping/options/checkout_multiple` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Limite maximale autorisée pour l’expédition vers plusieurs adresses | `multishipping/options/checkout_multiple_maximum_qty` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style=&quot;table-layout:auto&quot;}

## Chemins des méthodes de diffusion

Ces valeurs de configuration sont disponibles dans l’ Admin de **Magasins** > Paramètres > **Configuration** > **Ventes** > **Méthodes de diffusion**.

| Nom | Chemin de configuration | Commerce uniquement ? |
|--------------|--------------|--------------|
| Activé | `carriers/flatrate/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titre | `carriers/flatrate/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nom de méthode | `carriers/flatrate/name` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Type | `carriers/flatrate/type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Prix | `carriers/flatrate/price` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Frais de gestion des calculs | `carriers/flatrate/handling_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Gestion des frais | `carriers/flatrate/handling_fee` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Message d’erreur affiché | `carriers/flatrate/specificerrmsg` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Expédier aux pays applicables | `carriers/flatrate/sallowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ship to Specific Countries | `carriers/flatrate/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Afficher la méthode si cela n’est pas applicable | `carriers/flatrate/showmethod` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordre de tri | `carriers/flatrate/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activé | `carriers/freeshipping/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titre | `carriers/freeshipping/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nom de méthode | `carriers/freeshipping/name` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Montant minimal de la commande | `carriers/freeshipping/free_shipping_subtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Message d’erreur affiché | `carriers/freeshipping/specificerrmsg` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Expédier aux pays applicables | `carriers/freeshipping/sallowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ship to Specific Countries | `carriers/freeshipping/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Afficher la méthode si cela n’est pas applicable | `carriers/freeshipping/showmethod` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordre de tri | `carriers/freeshipping/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activé | `carriers/tablerate/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titre | `carriers/tablerate/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nom de méthode | `carriers/tablerate/name` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Condition | `carriers/tablerate/condition_name` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Inclure les produits virtuels dans le calcul des prix | `carriers/tablerate/include_virtual_price` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Exporter | `carriers/tablerate/export` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Importer | `carriers/tablerate/import` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Frais de gestion des calculs | `carriers/tablerate/handling_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Gestion des frais | `carriers/tablerate/handling_fee` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Message d’erreur affiché | `carriers/tablerate/specificerrmsg` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Expédier aux pays applicables | `carriers/tablerate/sallowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ship to Specific Countries | `carriers/tablerate/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Afficher la méthode si cela n’est pas applicable | `carriers/tablerate/showmethod` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordre de tri | `carriers/tablerate/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activé pour le passage en caisse | `carriers/ups/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activé pour la RAM | `carriers/ups/active_rma` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Type UPS | `carriers/ups/type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mode | `carriers/ups/mode_xml` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Origine de l&#39;envoi | `carriers/ups/origin_shipment` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| URL de passerelle | `carriers/ups/gateway_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titre | `carriers/ups/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activer les taux négociés | `carriers/ups/negotiated_active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Type de requête de package | `carriers/ups/shipment_requesttype` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Conteneur | `carriers/ups/container` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Unité de poids | `carriers/ups/unit_of_measure` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Type de destination | `carriers/ups/dest_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Poids maximal du package (veuillez consulter votre opérateur de transport pour connaître le poids maximal de livraison pris en charge) | `carriers/ups/max_package_weight` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Méthode de ramassage | `carriers/ups/pickup` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Poids minimum du package (veuillez consulter votre opérateur de livraison pour obtenir un poids minimum de livraison pris en charge) | `carriers/ups/min_package_weight` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Frais de gestion des calculs | `carriers/ups/handling_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Gestion appliquée | `carriers/ups/handling_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Gestion des frais | `carriers/ups/handling_fee` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Méthodes autorisées | `carriers/ups/allowed_methods` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Méthode libre | `carriers/ups/free_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activer le seuil de livraison gratuit | `carriers/ups/free_shipping_enable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Seuil du montant de la livraison gratuite | `carriers/ups/free_shipping_subtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Message d’erreur affiché | `carriers/ups/specificerrmsg` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Expédier aux pays applicables | `carriers/ups/sallowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ship to Specific Countries | `carriers/ups/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Afficher la méthode si cela n’est pas applicable | `carriers/ups/showmethod` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordre de tri | `carriers/ups/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activé pour le passage en caisse | `carriers/usps/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activé pour la RAM | `carriers/usps/active_rma` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Mode | `carriers/usps/mode` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Type de requête de package | `carriers/usps/shipment_requesttype` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Conteneur | `carriers/usps/container` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Taille | `carriers/usps/size` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Longueur | `carriers/usps/length` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Largeur | `carriers/usps/width` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Hauteur | `carriers/usps/height` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Fille | `carriers/usps/girth` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Machinable | `carriers/usps/machinable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Poids maximal du package (veuillez consulter votre opérateur de transport pour connaître le poids maximal de livraison pris en charge) | `carriers/usps/max_package_weight` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Frais de gestion des calculs | `carriers/usps/handling_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Gestion appliquée | `carriers/usps/handling_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Gestion des frais | `carriers/usps/handling_fee` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Méthodes autorisées | `carriers/usps/allowed_methods` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Méthode libre | `carriers/usps/free_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activer le seuil de livraison gratuit | `carriers/usps/free_shipping_enable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Seuil du montant de la livraison gratuite | `carriers/usps/free_shipping_subtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Message d’erreur affiché | `carriers/usps/specificerrmsg` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Expédier aux pays applicables | `carriers/usps/sallowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ship to Specific Countries | `carriers/usps/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Déboguer | `carriers/usps/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Afficher la méthode si cela n’est pas applicable | `carriers/usps/showmethod` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordre de tri | `carriers/usps/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activé pour le passage en caisse | `carriers/fedex/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activé pour la RAM | `carriers/fedex/active_rma` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Titre | `carriers/fedex/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| URL des services web (production) | `carriers/fedex/production_webservices_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| URL des services web (sandbox) | `carriers/fedex/sandbox_webservices_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Type de requête de package | `carriers/fedex/shipment_requesttype` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modules | `carriers/fedex/packaging` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Déposer | `carriers/fedex/dropoff` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Unité de poids | `carriers/fedex/unit_of_measure` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Poids maximal du package (veuillez consulter votre opérateur de transport pour connaître le poids maximal de livraison pris en charge) | `carriers/fedex/max_package_weight` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Frais de gestion des calculs | `carriers/fedex/handling_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Gestion appliquée | `carriers/fedex/handling_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Gestion des frais | `carriers/fedex/handling_fee` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Diffusion résidentielle | `carriers/fedex/residence_delivery` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Méthodes autorisées | `carriers/fedex/allowed_methods` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ID de Hub | `carriers/fedex/smartpost_hubid` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Méthode libre | `carriers/fedex/free_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activer le seuil de livraison gratuit | `carriers/fedex/free_shipping_enable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Seuil du montant de la livraison gratuite | `carriers/fedex/free_shipping_subtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Message d’erreur affiché | `carriers/fedex/specificerrmsg` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Expédier aux pays applicables | `carriers/fedex/sallowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ship to Specific Countries | `carriers/fedex/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Déboguer | `carriers/fedex/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Afficher la méthode si cela n’est pas applicable | `carriers/fedex/showmethod` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordre de tri | `carriers/fedex/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activé pour le passage en caisse | `carriers/dhl/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activé pour la RAM | `carriers/dhl/active_rma` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Titre | `carriers/dhl/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Type de contenu | `carriers/dhl/content_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Frais de gestion des calculs | `carriers/dhl/handling_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Gestion appliquée | `carriers/dhl/handling_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Gestion des frais | `carriers/dhl/handling_fee` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Diviser le poids de la commande | `carriers/dhl/divide_order_weight` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Unité de poids | `carriers/dhl/unit_of_measure` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Taille | `carriers/dhl/size` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Hauteur | `carriers/dhl/height` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Profondeur | `carriers/dhl/depth` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Largeur | `carriers/dhl/width` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Méthodes autorisées | `carriers/dhl/doc_methods` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Méthodes autorisées | `carriers/dhl/nondoc_methods` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Temps prêt | `carriers/dhl/ready_time` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Message d’erreur affiché | `carriers/dhl/specificerrmsg` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Méthode libre | `carriers/dhl/free_method_doc` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Méthode libre | `carriers/dhl/free_method_nondoc` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activer le seuil de livraison gratuit | `carriers/dhl/free_shipping_enable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Seuil du montant de la livraison gratuite | `carriers/dhl/free_shipping_subtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Expédier aux pays applicables | `carriers/dhl/sallowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ship to Specific Countries | `carriers/dhl/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Afficher la méthode si cela n’est pas applicable | `carriers/dhl/showmethod` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordre de tri | `carriers/dhl/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style=&quot;table-layout:auto&quot;}

## Chemins de l’API Google

Ces valeurs de configuration sont disponibles dans l’ Admin de **Magasins** > Paramètres > **Configuration** > **Ventes** > **API Google**.

| Nom | Chemin de configuration | Commerce uniquement ? |
|--------------|--------------|--------------|
| Activer | `google/analytics/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Type de compte | `google/analytics/type` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Activation des expériences de contenu | `google/analytics/experiments` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Propriété de liste de la page de catalogue | `google/analytics/catalog_page_list_value` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Propriété de liste du bloc de vente croisée | `google/analytics/crosssell_block_list_value` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Propriété de liste du bloc de mise à niveau | `google/analytics/upsell_block_list_value` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Propriété de liste du bloc de produits associé | `google/analytics/related_block_list_value` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Propriété de liste de la page des résultats de recherche | `google/analytics/search_page_list_value` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| &quot;Promotions internes&quot; pour le champ &quot;Libellé&quot; des promotions. | `google/analytics/promotions_list_value` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Activer | `google/adwords/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ID de conversion | `google/adwords/conversion_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Langue de conversion | `google/adwords/conversion_language` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Format de conversion | `google/adwords/conversion_format` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Couleur de conversion | `google/adwords/conversion_color` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Étiquette de conversion | `google/adwords/conversion_label` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Type de valeur de conversion | `google/adwords/conversion_value_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Valeur de conversion | `google/adwords/conversion_value` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style=&quot;table-layout:auto&quot;}

## Chemins des cartes cadeau

Ces valeurs de configuration sont disponibles dans l’ Admin de **Magasins** > Paramètres > **Configuration** > **Ventes** > **Fiches d’assistance**.

| Nom | Chemin de configuration | Commerce uniquement ? |
|--------------|--------------|--------------|
| Expéditeur d’e-mail de notification de carte cadeau | `giftcard/email/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modèle de courrier électronique de notification de carte cadeau | `giftcard/email/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Remboursable | `giftcard/general/is_redeemable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Durée de vie (jours) | `giftcard/general/lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Autoriser un message cadeau | `giftcard/general/allow_message` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Longueur maximale du message du cadeau | `giftcard/general/message_max_length` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Générer un compte de carte cadeau lorsque l’article de commande est | `giftcard/general/order_item_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Expéditeur d’e-mail de carte-cadeau | `giftcard/giftcardaccount_email/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modèle de carte cadeau | `giftcard/giftcardaccount_email/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Longueur du code | `giftcard/giftcardaccount_general/code_length` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Format de code | `giftcard/giftcardaccount_general/code_format` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Préfixe de code | `giftcard/giftcardaccount_general/code_prefix` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Suffixe de code | `giftcard/giftcardaccount_general/code_suffix` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tiret Toutes Les X Caractères | `giftcard/giftcardaccount_general/code_split` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nouvelle taille du pool | `giftcard/giftcardaccount_general/pool_size` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Seuil du pool de code faible | `giftcard/giftcardaccount_general/pool_threshold` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style=&quot;table-layout:auto&quot;}
