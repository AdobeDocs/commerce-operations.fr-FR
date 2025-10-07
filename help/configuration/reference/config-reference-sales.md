---
title: Référence des chemins de configuration des ventes
description: Découvrez les chemins de configuration des ventes et les noms des variables dans Adobe Commerce. Découvrez les paramètres d’administration pour le passage en caisse, l’expédition et les taxes.
feature: Configuration, Checkout, Gift, Shipping/Delivery, Taxes
exl-id: 7981f78a-5e5f-422c-9bff-54022e1fb9f3
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '1485'
ht-degree: 0%

---

# Référence des chemins de configuration des ventes

Cette section répertorie les noms de variables et les chemins de configuration disponibles pour les options dans Admin sous **Magasins** > Paramètres > **Configuration** > **Ventes**.

La commande [`magento app:config:dump` écrit ](../cli/export-configuration.md) ces valeurs dans le fichier de configuration partagé, `app/etc/config.php`, qui doit se trouver dans le contrôle de code source. Pour remplacer éventuellement des paramètres de configuration ou définir des paramètres sensibles, voir [Utiliser des variables d’environnement pour remplacer des paramètres de configuration](override-config-settings.md#environment-variables). Cette rubrique ne répertorie _pas_ les [valeurs sensibles et spécifiques au système](config-reference-sens.md).

## Chemins de vente

Ces valeurs de configuration sont disponibles dans Admin dans **Magasins** > Paramètres > **Configuration** > **Ventes** > **Ventes**.

| Nom | Chemin de configuration | Commerce uniquement ? |
|--------------|--------------|--------------|
| Masquer l’adresse IP du client | `sales/general/hide_customer_ip` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sous-total | `sales/totals_sort/subtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Remise | `sales/totals_sort/discount` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Expédition | `sales/totals_sort/shipping` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Taxe | `sales/totals_sort/tax` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Taxe fixe sur les produits | `sales/totals_sort/weee` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total général | `sales/totals_sort/grand_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Cartes cadeaux | `sales/totals_sort/giftcardaccount` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Crédit de la boutique | `sales/totals_sort/customerbalance` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Autoriser la réorganisation | `sales/reorder/allow` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Logo pour PDF Print-outs (200x50) | `sales/identity/logo` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Logo de la vue d’impression HTML | `sales/identity/logo_html` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Adresse | `sales/identity/address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activer | `sales/minimum_order/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Montant minimal | `sales/minimum_order/amount` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Inclure la taxe au montant | `sales/minimum_order/tax_including` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Message de description | `sales/minimum_order/description` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Erreur à afficher dans le panier | `sales/minimum_order/error_message` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Valider chaque adresse séparément dans le passage en caisse à plusieurs adresses | `sales/minimum_order/multi_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Message de description à plusieurs adresses | `sales/minimum_order/multi_address_description` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Erreur multi-adresses à afficher dans le panier | `sales/minimum_order/multi_address_error_message` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Utiliser Des Données Agrégées | `sales/dashboard/use_aggregated_data` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Durée de vie de l&#39;ordre de paiement en attente (minutes) | `sales/orders/delete_pending_after` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Autoriser les messages cadeau au niveau de la commande | `sales/gift_options/allow_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Autoriser les messages-cadeaux pour les articles de commande | `sales/gift_options/allow_items` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Autoriser l&#39;emballage-cadeau au niveau de la commande | `sales/gift_options/wrapping_allow_order` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Autoriser l&#39;emballage-cadeau pour les articles de commande | `sales/gift_options/wrapping_allow_items` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Autoriser l&#39;accusé de réception | `sales/gift_options/allow_gift_receipt` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Autoriser l&#39;impression de la carte | `sales/gift_options/allow_printed_card` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Prix par défaut pour la carte imprimée | `sales/gift_options/printed_card_price` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Activer MAP | `sales/msrp/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Afficher le prix réel | `sales/msrp/display_price_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Message texte contextuel par défaut | `sales/msrp/explanation_message` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Message texte « Qu’est-ce que c’est ? » par défaut | `sales/msrp/explanation_message_whats_this` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activer la commande par SKU sur Mon compte dans Storefront | `sales/product_sku/my_account_enable` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Activé | `sales/instant_purchase/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Texte du bouton | `sales/instant_purchase/button_text` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Groupes de clients | `sales/product_sku/allowed_groups` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Activer l’archivage | `sales/magento_salesarchive/active` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Archiver les commandes achetées | `sales/magento_salesarchive/age` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Statuts des commandes à archiver | `sales/magento_salesarchive/order_statuses` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Activer RMA sur Storefront | `sales/magento_rma/enabled` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Activer RMA au niveau du produit | `sales/magento_rma/enabled_on_product` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Utiliser l’adresse du magasin | `sales/magento_rma/use_store_address` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |

{style="table-layout:auto"}

## Chemins d’accès aux e-mails de vente

Ces valeurs de configuration sont disponibles dans Admin dans **Magasins** > Paramètres > **Configuration** > **Ventes** > **Emails commerciaux**.

| Nom | Chemin de configuration | Commerce uniquement ? |
|--------------|--------------|--------------|
| Envoi asynchrone | `sales_email/general/async_sending` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activé | `sales_email/order/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Expéditeur de l&#39;e-mail de confirmation de nouvelle commande | `sales_email/order/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nouveau modèle de confirmation de commande | `sales_email/order/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nouveau modèle de confirmation de commande pour les invités | `sales_email/order/guest_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Méthode De Copie Des E-Mails De Commande D&#39;Envoi | `sales_email/order/copy_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activé | `sales_email/order_comment/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Envoyer un commentaire de commande par e-mail | `sales_email/order_comment/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modèle d’e-mail de commentaire de commande | `sales_email/order_comment/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modèle d’e-mail de commentaire de commande pour les invités | `sales_email/order_comment/guest_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Méthode de copie par e-mail des commentaires de commande d&#39;envoi | `sales_email/order_comment/copy_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activé | `sales_email/invoice/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Expéditeur de l&#39;e-mail de la facture | `sales_email/invoice/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modèle d&#39;e-mail de facture | `sales_email/invoice/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modèle d’e-mail de facture pour l’invité | `sales_email/invoice/guest_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Méthode envoi de la copie de l&#39;e-mail de la facture | `sales_email/invoice/copy_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activé | `sales_email/invoice_comment/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Expéditeur d&#39;e-mail de commentaire de facture | `sales_email/invoice_comment/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modèle d&#39;e-mail de commentaire de facture | `sales_email/invoice_comment/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modèle d’e-mail de commentaire de facture pour l’invité | `sales_email/invoice_comment/guest_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Méthode de copie d&#39;e-mail Envoyer des commentaires de facture | `sales_email/invoice_comment/copy_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activé | `sales_email/shipment/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Expéditeur de l&#39;e-mail d&#39;expédition | `sales_email/shipment/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modèle d&#39;e-mail d&#39;expédition | `sales_email/shipment/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modèle d’e-mail d’expédition pour les invités | `sales_email/shipment/guest_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Méthode de copie de l&#39;e-mail d&#39;envoi | `sales_email/shipment/copy_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activé | `sales_email/shipment_comment/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Expéditeur d&#39;e-mail de commentaire d&#39;expédition | `sales_email/shipment_comment/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modèle d&#39;e-mail de commentaire d&#39;expédition | `sales_email/shipment_comment/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modèle d’e-mail de commentaire d’expédition pour les invités | `sales_email/shipment_comment/guest_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Méthode de copie d&#39;e-mail Envoyer des commentaires d&#39;expédition | `sales_email/shipment_comment/copy_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activé | `sales_email/creditmemo/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Expéditeur de l&#39;e-mail de l&#39;avoir | `sales_email/creditmemo/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modèle d&#39;e-mail avoir | `sales_email/creditmemo/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modèle d&#39;e-mail d&#39;avoir pour l&#39;invité | `sales_email/creditmemo/guest_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Envoyer un avoir - Méthode de copie d&#39;e-mail | `sales_email/creditmemo/copy_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activé | `sales_email/creditmemo_comment/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Commentaire d&#39;avoir - Expéditeur de l&#39;e-mail | `sales_email/creditmemo_comment/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modèle d&#39;e-mail de commentaire d&#39;avoir | `sales_email/creditmemo_comment/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modèle d&#39;e-mail de commentaire d&#39;avoir pour l&#39;invité | `sales_email/creditmemo_comment/guest_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Envoyer des commentaires d&#39;avoir Méthode de copie d&#39;e-mail | `sales_email/creditmemo_comment/copy_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activé | `sales_email/magento_rma/enabled` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Expéditeur d&#39;e-mail RMA | `sales_email/magento_rma/identity` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Modèle d&#39;e-mail RMA | `sales_email/magento_rma/template` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Modèle d’e-mail RMA pour l’invité | `sales_email/magento_rma/guest_template` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Envoyer RMA : méthode de copie d&#39;e-mail | `sales_email/magento_rma/copy_method` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Activé | `sales_email/magento_rma_auth/enabled` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Expéditeur d&#39;e-mail d&#39;autorisation RMA | `sales_email/magento_rma_auth/identity` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Modèle d&#39;e-mail d&#39;autorisation RMA | `sales_email/magento_rma_auth/template` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Modèle d’e-mail d’autorisation RMA pour les invités | `sales_email/magento_rma_auth/guest_template` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Envoyer la méthode de copie d&#39;e-mail d&#39;autorisation RMA | `sales_email/magento_rma_auth/copy_method` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Activé | `sales_email/magento_rma_comment/enabled` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Expéditeur d&#39;e-mail de commentaire RMA | `sales_email/magento_rma_comment/identity` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Modèle d&#39;e-mail de commentaire RMA | `sales_email/magento_rma_comment/template` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Modèle d&#39;e-mail de commentaire RMA pour l&#39;invité | `sales_email/magento_rma_comment/guest_template` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Envoyer RMA : méthode de copie d&#39;e-mail | `sales_email/magento_rma_comment/copy_method` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Activé | `sales_email/magento_rma_customer_comment/enabled` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Expéditeur d&#39;e-mail de commentaire RMA | `sales_email/magento_rma_customer_comment/identity` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Destinataire d&#39;e-mail de commentaire RMA | `sales_email/magento_rma_customer_comment/recipient` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Modèle d&#39;e-mail de commentaire RMA | `sales_email/magento_rma_customer_comment/template` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Envoyer RMA : méthode de copie d&#39;e-mail | `sales_email/magento_rma_customer_comment/copy_method` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Afficher l’ID de commande dans l’en-tête | `sales_pdf/invoice/put_order_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Afficher l’ID de commande dans l’en-tête | `sales_pdf/shipment/put_order_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Afficher l’ID de commande dans l’en-tête | `sales_pdf/creditmemo/put_order_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Chemins d’accès aux taxes

Ces valeurs de configuration sont disponibles dans Admin dans **Magasins** > Paramètres > **Configuration** > **Ventes** > **Taxe**.

| Nom | Chemin de configuration | Commerce uniquement ? |
|--------------|--------------|--------------|
| Classe de taxe pour l&#39;expédition | `tax/classes/shipping_tax_class` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Classe d’impôt pour les options de cadeau | `tax/classes/wrapping_tax_class` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Classe de taxe par défaut pour le produit | `tax/classes/default_product_tax_class` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Classe de taxe par défaut pour le client | `tax/classes/default_customer_tax_class` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Méthode De Calcul De La Taxe Basée Sur | `tax/calculation/algorithm` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Calcul De La Taxe Basé Sur | `tax/calculation/based_on` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Prix catalogue | `tax/calculation/price_includes_tax` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Prix d’expédition | `tax/calculation/shipping_includes_tax` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Appliquer la taxe client | `tax/calculation/apply_after_discount` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Appliquer Une Remise Sur Les Prix | `tax/calculation/discount_tax` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Appliquer la taxe sur | `tax/calculation/apply_tax_on` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Permettre le commerce transfrontalier | `tax/calculation/cross_border_trade_enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pays par défaut | `tax/defaults/country` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| État par défaut | `tax/defaults/region` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Code postal par défaut | `tax/defaults/postcode` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Afficher Les Prix Des Produits Dans Le Catalogue | `tax/display/type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Afficher les prix d&#39;expédition | `tax/display/shipping` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Afficher les prix | `tax/cart_display/price` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Afficher Le Sous-Total | `tax/cart_display/subtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Afficher le montant d&#39;expédition | `tax/cart_display/shipping` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Afficher les prix de l&#39;emballage-cadeau | `tax/cart_display/gift_wrapping` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Afficher les prix des cartes imprimées | `tax/cart_display/printed_card` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Inclure La Taxe Dans Le Total De La Commande | `tax/cart_display/grandtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Afficher la synthèse complète des taxes | `tax/cart_display/full_summary` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Afficher le sous-total de taxe nulle | `tax/cart_display/zero_tax` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Afficher les prix | `tax/sales_display/price` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Afficher Le Sous-Total | `tax/sales_display/subtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Afficher le montant d&#39;expédition | `tax/sales_display/shipping` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Afficher les prix de l&#39;emballage-cadeau | `tax/sales_display/gift_wrapping` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Afficher les prix des cartes imprimées | `tax/sales_display/printed_card` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Inclure La Taxe Dans Le Total De La Commande | `tax/sales_display/grandtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Afficher la synthèse complète des taxes | `tax/sales_display/full_summary` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Afficher le sous-total de taxe nulle | `tax/sales_display/zero_tax` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activer FPT | `tax/weee/enable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Afficher Les Prix Dans Les Listes De Produits | `tax/weee/display_list` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Afficher Les Prix Sur La Page D’Affichage Du Produit | `tax/weee/display` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Afficher Les Prix Dans Les Modules De Vente | `tax/weee/display_sales` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Afficher Les Prix Dans Les Emails | `tax/weee/display_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Appliquer la taxe à FPT | `tax/weee/apply_vat` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Inclure FPT Dans Le Sous-Total | `tax/weee/include_in_subtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Chemins de passage en caisse

Ces valeurs de configuration sont disponibles dans Admin dans **Magasins** > Paramètres > **Configuration** > **Ventes** > **Passage en caisse**.

| Nom | Chemin de configuration | Commerce uniquement ? |
|--------------|--------------|--------------|
| Activer le passage en caisse sur une page | `checkout/options/onepage_checkout_enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Autoriser le passage en caisse des invités | `checkout/options/guest_checkout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Afficher L’Adresse De Facturation Sur | `checkout/options/display_billing_address_on` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activer les conditions générales | `checkout/options/enable_agreements` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Durée de vie du devis (jours) | `checkout/cart/delete_quote_after` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Après l’ajout d’une redirection de produit au panier | `checkout/cart/redirect_to_cart` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Image de produit groupée | `checkout/cart/grouped_product_image` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Image du produit configurable | `checkout/cart/configurable_product_image` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Durée de vie du devis d&#39;aperçu (minutes) | `checkout/cart/preview_quota_lifetime` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Afficher le résumé du panier | `checkout/cart_link/use_qty` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Afficher la barre latérale du panier | `checkout/sidebar/display` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nombre maximum d&#39;éléments récemment ajoutés | `checkout/sidebar/count` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Expéditeur d&#39;e-mail d&#39;échec de paiement | `checkout/payment_failed/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Récepteur d&#39;e-mails ayant échoué au paiement | `checkout/payment_failed/receiver` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modèle d&#39;échec de paiement | `checkout/payment_failed/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Méthode de copie d’e-mail en cas d’échec de l’envoi du paiement | `checkout/payment_failed/copy_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Chemins d’accès aux paramètres d’expédition

Ces valeurs de configuration sont disponibles dans Admin dans **Magasins** > Paramètres > **Configuration** > **Ventes** > **Paramètres d’expédition**.

| Nom | Chemin de configuration | Commerce uniquement ? |
|--------------|--------------|--------------|
| Appliquer une stratégie d&#39;expédition personnalisée | `shipping/shipping_policy/enable_shipping_policy` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Politique De Transport Maritime | `shipping/shipping_policy/shipping_policy_content` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Chemins d’accès aux paramètres d’expédition multiple

Ces valeurs de configuration sont disponibles dans Admin dans **Magasins** > Paramètres > **Configuration** > **Ventes** > **Paramètres d’expédition multiple**.

| Nom | Chemin de configuration | Commerce uniquement ? |
|--------------|--------------|--------------|
| Autoriser l&#39;expédition vers plusieurs adresses | `multishipping/options/checkout_multiple` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Qté maximale autorisée pour l&#39;expédition vers plusieurs adresses | `multishipping/options/checkout_multiple_maximum_qty` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Chemins des méthodes de diffusion

Ces valeurs de configuration sont disponibles dans Admin dans **Magasins** > Paramètres > **Configuration** > **Ventes** > **Méthodes de diffusion**.

| Nom | Chemin de configuration | Commerce uniquement ? |
|--------------|--------------|--------------|
| Activé | `carriers/flatrate/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titre | `carriers/flatrate/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nom de la méthode | `carriers/flatrate/name` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Type | `carriers/flatrate/type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Prix | `carriers/flatrate/price` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Calculer les frais de gestion | `carriers/flatrate/handling_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Frais de gestion | `carriers/flatrate/handling_fee` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Message d’erreur affiché | `carriers/flatrate/specificerrmsg` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Expédier vers les pays applicables | `carriers/flatrate/sallowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Expédier vers des pays spécifiques | `carriers/flatrate/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Afficher la méthode si non applicable | `carriers/flatrate/showmethod` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordre de tri | `carriers/flatrate/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activé | `carriers/freeshipping/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titre | `carriers/freeshipping/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nom de la méthode | `carriers/freeshipping/name` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Montant minimal de la commande | `carriers/freeshipping/free_shipping_subtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Message d’erreur affiché | `carriers/freeshipping/specificerrmsg` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Expédier vers les pays applicables | `carriers/freeshipping/sallowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Expédier vers des pays spécifiques | `carriers/freeshipping/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Afficher la méthode si non applicable | `carriers/freeshipping/showmethod` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordre de tri | `carriers/freeshipping/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activé | `carriers/tablerate/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titre | `carriers/tablerate/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nom de la méthode | `carriers/tablerate/name` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Condition | `carriers/tablerate/condition_name` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Inclure les produits virtuels dans le calcul des prix | `carriers/tablerate/include_virtual_price` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Exporter | `carriers/tablerate/export` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Importer | `carriers/tablerate/import` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Calculer les frais de gestion | `carriers/tablerate/handling_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Frais de gestion | `carriers/tablerate/handling_fee` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Message d’erreur affiché | `carriers/tablerate/specificerrmsg` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Expédier vers les pays applicables | `carriers/tablerate/sallowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Expédier vers des pays spécifiques | `carriers/tablerate/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Afficher la méthode si non applicable | `carriers/tablerate/showmethod` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordre de tri | `carriers/tablerate/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activé pour le passage en caisse | `carriers/ups/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activé pour RMA | `carriers/ups/active_rma` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Type d&#39;onduleur | `carriers/ups/type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mode | `carriers/ups/mode_xml` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Origine de l&#39;expédition | `carriers/ups/origin_shipment` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| URL de passerelle | `carriers/ups/gateway_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titre | `carriers/ups/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activer les taux négociés | `carriers/ups/negotiated_active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Type de demande de packages | `carriers/ups/shipment_requesttype` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Conteneur | `carriers/ups/container` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Unité De Poids | `carriers/ups/unit_of_measure` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Type de destination | `carriers/ups/dest_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Poids maximum du colis (veuillez consulter votre transporteur pour connaître le poids maximum pris en charge) | `carriers/ups/max_package_weight` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Méthode de prélèvement | `carriers/ups/pickup` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Poids minimum du colis (veuillez consulter votre transporteur pour connaître le poids minimum pris en charge) | `carriers/ups/min_package_weight` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Calculer les frais de gestion | `carriers/ups/handling_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Gestion appliquée | `carriers/ups/handling_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Frais de gestion | `carriers/ups/handling_fee` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Méthodes autorisées | `carriers/ups/allowed_methods` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Méthode libre | `carriers/ups/free_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activer le seuil d&#39;expédition gratuite | `carriers/ups/free_shipping_enable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Seuil de montant d&#39;expédition gratuite | `carriers/ups/free_shipping_subtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Message d’erreur affiché | `carriers/ups/specificerrmsg` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Expédier vers les pays applicables | `carriers/ups/sallowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Expédier vers des pays spécifiques | `carriers/ups/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Afficher la méthode si non applicable | `carriers/ups/showmethod` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordre de tri | `carriers/ups/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activé pour le passage en caisse | `carriers/usps/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activé pour RMA | `carriers/usps/active_rma` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Mode | `carriers/usps/mode` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Type de demande de packages | `carriers/usps/shipment_requesttype` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Conteneur | `carriers/usps/container` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Taille | `carriers/usps/size` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Longueur | `carriers/usps/length` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Largeur | `carriers/usps/width` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Hauteur | `carriers/usps/height` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Naissance | `carriers/usps/girth` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Usinable | `carriers/usps/machinable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Poids maximum du colis (veuillez consulter votre transporteur pour connaître le poids maximum pris en charge) | `carriers/usps/max_package_weight` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Calculer les frais de gestion | `carriers/usps/handling_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Gestion appliquée | `carriers/usps/handling_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Frais de gestion | `carriers/usps/handling_fee` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Méthodes autorisées | `carriers/usps/allowed_methods` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Méthode libre | `carriers/usps/free_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activer le seuil d&#39;expédition gratuite | `carriers/usps/free_shipping_enable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Seuil de montant d&#39;expédition gratuite | `carriers/usps/free_shipping_subtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Message d’erreur affiché | `carriers/usps/specificerrmsg` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Expédier vers les pays applicables | `carriers/usps/sallowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Expédier vers des pays spécifiques | `carriers/usps/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Déboguer | `carriers/usps/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Afficher la méthode si non applicable | `carriers/usps/showmethod` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordre de tri | `carriers/usps/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activé pour le passage en caisse | `carriers/fedex/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activé pour RMA | `carriers/fedex/active_rma` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Titre | `carriers/fedex/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| URL des services web (production) | `carriers/fedex/production_webservices_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| URL des services web (sandbox) | `carriers/fedex/sandbox_webservices_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Type de demande de packages | `carriers/fedex/shipment_requesttype` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Emballage | `carriers/fedex/packaging` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abandon | `carriers/fedex/dropoff` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Unité De Poids | `carriers/fedex/unit_of_measure` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Poids maximum du colis (veuillez consulter votre transporteur pour connaître le poids maximum pris en charge) | `carriers/fedex/max_package_weight` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Calculer les frais de gestion | `carriers/fedex/handling_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Gestion appliquée | `carriers/fedex/handling_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Frais de gestion | `carriers/fedex/handling_fee` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Livraison en résidence | `carriers/fedex/residence_delivery` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Méthodes autorisées | `carriers/fedex/allowed_methods` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Identifiant du hub | `carriers/fedex/smartpost_hubid` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Méthode libre | `carriers/fedex/free_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activer le seuil d&#39;expédition gratuite | `carriers/fedex/free_shipping_enable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Seuil de montant d&#39;expédition gratuite | `carriers/fedex/free_shipping_subtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Message d’erreur affiché | `carriers/fedex/specificerrmsg` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Expédier vers les pays applicables | `carriers/fedex/sallowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Expédier vers des pays spécifiques | `carriers/fedex/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Déboguer | `carriers/fedex/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Afficher la méthode si non applicable | `carriers/fedex/showmethod` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordre de tri | `carriers/fedex/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activé pour le passage en caisse | `carriers/dhl/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activé pour RMA | `carriers/dhl/active_rma` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Titre | `carriers/dhl/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Type de contenu | `carriers/dhl/content_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Calculer les frais de gestion | `carriers/dhl/handling_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Gestion appliquée | `carriers/dhl/handling_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Frais de gestion | `carriers/dhl/handling_fee` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Diviser le poids de la commande | `carriers/dhl/divide_order_weight` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Unité De Poids | `carriers/dhl/unit_of_measure` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Taille | `carriers/dhl/size` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Hauteur | `carriers/dhl/height` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Profondeur | `carriers/dhl/depth` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Largeur | `carriers/dhl/width` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Méthodes autorisées | `carriers/dhl/doc_methods` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Méthodes autorisées | `carriers/dhl/nondoc_methods` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Heure de préparation | `carriers/dhl/ready_time` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Message d’erreur affiché | `carriers/dhl/specificerrmsg` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Méthode libre | `carriers/dhl/free_method_doc` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Méthode libre | `carriers/dhl/free_method_nondoc` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activer le seuil d&#39;expédition gratuite | `carriers/dhl/free_shipping_enable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Seuil de montant d&#39;expédition gratuite | `carriers/dhl/free_shipping_subtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Expédier vers les pays applicables | `carriers/dhl/sallowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Expédier vers des pays spécifiques | `carriers/dhl/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Afficher la méthode si non applicable | `carriers/dhl/showmethod` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordre de tri | `carriers/dhl/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Chemins d’accès aux API Google

Ces valeurs de configuration sont disponibles dans Admin dans l’API **Magasins** > Paramètres > **Configuration** > **Ventes** > **Google**.

| Nom | Chemin de configuration | Commerce uniquement ? |
|--------------|--------------|--------------|
| Activer | `google/analytics/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Type de compte | `google/analytics/type` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Activer les expériences de contenu | `google/analytics/experiments` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Propriété de liste de la page de catalogue | `google/analytics/catalog_page_list_value` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Propriété de liste du bloc de ventes croisées | `google/analytics/crosssell_block_list_value` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Propriété de liste pour le bloc de vente incitative | `google/analytics/upsell_block_list_value` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Propriété de liste du bloc de produits associé | `google/analytics/related_block_list_value` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Propriété de liste de la page des résultats de recherche | `google/analytics/search_page_list_value` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| &#39;Promotions internes&#39; pour le champ de promotions « Libellé ». | `google/analytics/promotions_list_value` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Activer | `google/adwords/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ID de conversion | `google/adwords/conversion_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Langue de conversion | `google/adwords/conversion_language` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Format de conversion | `google/adwords/conversion_format` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Couleur de conversion | `google/adwords/conversion_color` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Libellé de conversion | `google/adwords/conversion_label` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Type de valeur de conversion | `google/adwords/conversion_value_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Valeur de conversion | `google/adwords/conversion_value` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Chemins des cartes-cadeaux

Ces valeurs de configuration sont disponibles dans Admin dans **Magasins** > Paramètres > **Configuration** > **Ventes** > **Cartes-cadeaux**.

| Nom | Chemin de configuration | Commerce uniquement ? |
|--------------|--------------|--------------|
| Expéditeur de l’e-mail de notification de carte cadeau | `giftcard/email/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modèle d’e-mail de notification de carte cadeau | `giftcard/email/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Remboursable | `giftcard/general/is_redeemable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Durée de vie (jours) | `giftcard/general/lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Autoriser le message cadeau | `giftcard/general/allow_message` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Longueur maximale du message cadeau | `giftcard/general/message_max_length` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Générer un compte de carte cadeau lorsque l&#39;article de commande est | `giftcard/general/order_item_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Expéditeur de l’e-mail de la carte cadeau | `giftcard/giftcardaccount_email/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modèle de carte cadeau | `giftcard/giftcardaccount_email/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Longueur du code | `giftcard/giftcardaccount_general/code_length` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Format du code | `giftcard/giftcardaccount_general/code_format` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Préfixe de code | `giftcard/giftcardaccount_general/code_prefix` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Suffixe de code | `giftcard/giftcardaccount_general/code_suffix` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tiret Tous Les X Caractères | `giftcard/giftcardaccount_general/code_split` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nouvelle taille de pool | `giftcard/giftcardaccount_general/pool_size` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Seuil du pool de code faible | `giftcard/giftcardaccount_general/pool_threshold` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}
