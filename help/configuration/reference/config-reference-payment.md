---
title: Référence des chemins de configuration des paiements
description: Découvrez les chemins de configuration des paiements et les valeurs des méthodes dans Adobe Commerce Admin. Découvrez les options de configuration de PayPal, de carte de crédit et de passerelle de paiement.
feature: Configuration, Payments
exl-id: f3e356aa-7262-4d99-9ed4-d77cbd93708c
source-git-commit: 7054a5286f01e26e324401f4d8505e4e0faed93e
workflow-type: tm+mt
source-wordcount: '5833'
ht-degree: 0%

---

# Référence des chemins de configuration des paiements

Ces valeurs de configuration sont disponibles dans Admin dans **Magasins** > Paramètres > **Configuration** > **Ventes** > **Modes de paiement**.

La commande [`magento app:config:dump` écrit ](../cli/export-configuration.md) ces valeurs dans le fichier de configuration partagé, `app/etc/config.php`, qui doit se trouver dans le contrôle de code source. Pour remplacer éventuellement des paramètres de configuration ou définir des paramètres sensibles, voir [Utiliser des variables d’environnement pour remplacer des paramètres de configuration](override-config-settings.md#environment-variables). Cette rubrique ne répertorie _Allt_ les [valeurs sensibles et spécifiques au système](config-reference-sens.md).

Les paramètres sont ensuite organisés par mode de paiement.

## Chemins PayPal

| Nom | Chemin de configuration | Prise en charge des versions de Commerce ? |
|--------------|--------------|--------------|
| Activer cette solution | `payment/payflowpro/active` | Tous |
| Activer l’expérience de passage en caisse contextuelle | `payment/paypal_express/in_context` | Tous |
| Activer le crédit PayPal | `payment/payflow_express_bml/active` | Tous |
| Activer le crédit PayPal | `payment/paypal_express_bml/active` | Tous |
| Affichage | `payment/paypal_express_bml/homepage_display` | Tous |
| Position | `payment/paypal_express_bml/homepage_position` | Tous |
| Taille | `payment/paypal_express_bml/homepage_size` | Tous |
| Affichage | `payment/paypal_express_bml/categorypage_display` | Tous |
| Position | `payment/paypal_express_bml/categorypage_position` | Tous |
| Taille | `payment/paypal_express_bml/categorypage_size` | Tous |
| Affichage | `payment/paypal_express_bml/productpage_display` | Tous |
| Position | `payment/paypal_express_bml/productpage_position` | Tous |
| Taille | `payment/paypal_express_bml/productpage_size` | Tous |
| Affichage | `payment/paypal_express_bml/checkout_display` | Tous |
| Position | `payment/paypal_express_bml/checkout_position` | Tous |
| Taille | `payment/paypal_express_bml/checkout_size` | Tous |
| Afficher sur la page Détails du produit | `payment/payflow_express/visible_on_product` | Tous |
| Afficher sur le panier | `payment/payflow_express/visible_on_cart` | Tous |
| Paiement Applicable À Partir De | `payment/payflow_express/allowspecific` | Tous |
| Pays Paiement Applicable De | `payment/payflow_express/specificcountry` | Tous |
| Activer la vérification SSL | `payment/payflow_express/verify_peer` | Tous |
| Transférer éléments de ligne de panier | `payment/payflow_express/line_items_enabled` | Tous |
| Ignorer l’étape de révision de la commande | `payment/paypal_express/skip_order_review_step` | Tous |
| Transférer éléments de ligne de panier | `payment/paypal_express/line_items_enabled` | Tous |
| Options d&#39;expédition de transfert | `payment/paypal_express/transfer_shipping_options` | Tous |
| Saveur des boutons de raccourci | `paypal/wpp/button_flavor` | Tous |
| Activer le passage en caisse des invités PayPal | `payment/paypal_express/solution_type` | Tous |
| Demander l&#39;adresse de facturation du client | `payment/paypal_express/require_billing_address` | Tous |
| Inscription au contrat de facturation | `payment/paypal_express/allow_ba_signup` | Tous |
| Activé | `payment/paypal_billing_agreement/active` | Tous |
| Titre | `payment/paypal_billing_agreement/title` | Tous |
| Ordre de tri | `payment/paypal_billing_agreement/sort_order` | Tous |
| Action de paiement | `payment/paypal_billing_agreement/payment_action` | Tous |
| Paiement Applicable À Partir De | `payment/paypal_billing_agreement/allowspecific` | Tous |
| Pays Paiement Applicable De | `payment/paypal_billing_agreement/specificcountry` | Tous |
| Activer la vérification SSL | `payment/paypal_billing_agreement/verify_peer` | Tous |
| Transférer éléments de ligne de panier | `payment/paypal_billing_agreement/line_items_enabled` | Tous |
| Assistant Autoriser dans le contrat de facturation | `payment/paypal_billing_agreement/allow_billing_agreement_wizard` | Tous |
| Activer la récupération automatique | `paypal/fetch_reports/active` | Tous |
| Planning | `paypal/fetch_reports/schedule` | Tous |
| Heure du jour | `paypal/fetch_reports/time` | Tous |
| Logo du produit PayPal | `paypal/style/logo` | Tous |
| Style de page | `paypal/style/page_style` | Tous |
| URL de l’image d’en-tête | `paypal/style/paypal_hdrimg` | Tous |
| Couleur d’arrière-plan de l’en-tête | `paypal/style/paypal_hdrbackcolor` | Tous |
| Couleur de la bordure de l’en-tête | `paypal/style/paypal_hdrbordercolor` | Tous |
| Couleur d’arrière-plan de la page | `paypal/style/paypal_payflowcolor` | Tous |
| Activer cette solution | `payment/paypal_express/active` | Tous |
| Ordre de tri Crédit PayPal | `payment/paypal_express_bml/sort_order` | Tous |
| Titre | `payment/paypal_express/title` | Tous |
| Ordre de tri | `payment/paypal_express/sort_order` | Tous |
| Action de paiement | `payment/paypal_express/payment_action` | Tous |
| Afficher sur la page Détails du produit | `payment/paypal_express/visible_on_product` | Tous |
| Période de l’intervalle d’autorisation (jours) | `payment/paypal_express/authorization_hoAllr_period` | Tous |
| Période de validité de la commande (jours) | `payment/paypal_express/order_valid_period` | Tous |
| Nombre d’autorisations enfants | `payment/paypal_express/child_authorization_number` | Tous |
| Afficher sur le panier | `payment/paypal_express/visible_on_cart` | Tous |
| Nombre d’autorisations enfants | `payment/paypal_express/child_authorization_number` | Tous |
| Paiement Applicable À Partir De | `payment/paypal_express/allowspecific` | Tous |
| Nombre d’autorisations enfants | `payment/paypal_express/child_authorization_number` | Tous |
| Pays Paiement Applicable De | `payment/paypal_express/specificcountry` | Tous |
| Nombre d’autorisations enfants | `payment/paypal_express/child_authorization_number` | Tous |
| Activer la vérification SSL | `payment/paypal_express/verify_peer` | Tous |
| Nombre d’autorisations enfants | `payment/paypal_express/child_authorization_number` | Tous |
| Récupération planifiée | `payment_all_paypal/express_checkout/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | Tous |
| Style des pages marchandes PayPal | `payment_all_paypal/express_checkout/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | Tous |

{style="table-layout:auto"}

## PayPal Payments Pro

| Nom | Chemin de configuration | Prise en charge des versions de Commerce ? |
|--------------|--------------|--------------|
| Méthodes d’authentification d’API | `paypal/wpp/api_authentication` | Tous |
| L’API utilise un proxy | `paypal/wpp/use_proxy` | Tous |
| Récupération planifiée | `payment_all_paypal/payments_pro_hosted_solution/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_schedule` | Tous |
| Récupération planifiée | `payment_all_paypal/payments_pro_hosted_solution_without_bml/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_schedule` | Tous |

{style="table-layout:auto"}

## Payments Pro Hosted Solution (Royaume-Uni)

Ces options ne sont disponibles que si vous avez choisi le Royaume-Uni comme [pays commerçant](../reference/config-reference-sens.md#payment-sensitive-and-system-specific-paths).

| Nom | Chemin de configuration | Prise en charge des versions de Commerce ? |
|--------------|--------------|--------------|
| Activer cette solution | `payment/hosted_pro/active` | Tous |
| Titre | `payment/hosted_pro/title` | Tous |
| Ordre de tri | `payment/hosted_pro/sort_order` | Tous |
| Action de paiement | `payment/hosted_pro/payment_action` | Tous |
| Afficher le passage en caisse express à l’étape Informations de paiement | `payment/hosted_pro/display_ec` | Tous |
| Paiement Applicable À Partir De | `payment/hosted_pro/allowspecific` | Tous |
| Pays Paiement Applicable De | `payment/hosted_pro/specificcountry` | Tous |
| Activer la vérification SSL | `payment/hosted_pro/verify_peer` | Tous |

{style="table-layout:auto"}

## PayPal Payflow Pro

| Nom | Chemin de configuration | Prise en charge des versions de Commerce ? |
|--------------|--------------|--------------|
| Vault activé | `payment/payflowpro_cc_vault/active` | Tous |
| Titre | `payment/payflowpro/title` | Tous |
| Titre du coffre | `payment/payflowpro_cc_vault/title` | Tous |
| Ordre de tri | `payment/payflowpro/sort_order` | Tous |
| Action de paiement | `payment/payflowpro/payment_action` | Tous |
| Types de cartes de crédit autorisés | `payment/payflowpro/cctypes` | Tous |
| Paiement Applicable À Partir De | `payment/payflowpro/allowspecific` | Tous |
| Pays Paiement Applicable De | `payment/payflowpro/specificcountry` | Tous |
| Activer la vérification SSL | `payment/payflowpro/verify_peer` | Tous |
| Exiger une entrée CVV | `payment/payflowpro/useccv` | Tous |
| Rejeter la transaction si : | `payment_all_paypal/paypal_payflowpro/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_avs_check/heading_avs_settings` | Tous |
| AVS Street ne correspond pas | `payment/payflowpro/avs_street` | Tous |
| Le code postal AVS ne correspond absolument pas | `payment/payflowpro/avs_zip` | Tous |
| L’indicateur AVS international ne correspond absolument pas | `payment/payflowpro/avs_international` | Tous |
| Le Code De Sécurité De La Carte Ne Correspond Pas | `payment/payflowpro/avs_security_code` | Tous |
| Fournisseur | `payment/payflowpro/vendor` | Tous |
| Utiliser le proxy | `payment/payflowpro/use_proxy` | Tous |
| Titre | `payment/payflow_express/title` | Tous |
| Ordre de tri | `payment/payflow_express/sort_order` | Tous |
| Action de paiement | `payment/payflow_express/payment_action` | Tous |
| Récupération planifiée | `payment_all_paypal/paypal_payflowpro/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_schedule` | Tous |
| Style des pages marchandes PayPal | `payment_all_paypal/payflow_link/settings_payflow_link/settings_payflow_link_advanced/payflow_link_frontend/paypal_pages` | Tous |
| Partenaire | `payment/payflow_advanced/partner` | Tous |
| Fournisseur | `payment/payflow_advanced/vendor` | Tous |
| Utiliser le proxy | `payment/payflow_advanced/use_proxy` | Tous |
| Activer cette solution | `payment/payflow_advanced/active` | Tous |
| Titre | `payment/payflow_advanced/title` | Tous |
| Ordre de tri | `payment/payflow_advanced/sort_order` | Tous |
| Action de paiement | `payment/payflow_advanced/payment_action` | Tous |
| Paiement Applicable À Partir De | `payment/payflow_advanced/allowspecific` | Tous |
| Pays Paiement Applicable De | `payment/payflow_advanced/specificcountry` | Tous |
| Activer la vérification SSL | `payment/payflow_advanced/verify_peer` | Tous |
| L’entrée CVV est modifiable. | `payment/payflow_advanced/csc_editable` | Tous |
| Exiger une entrée CVV | `payment/payflow_advanced/csc_required` | Tous |
| Envoyer un e-mail de confirmation | `payment/payflow_advanced/email_confirmation` | Tous |

{style="table-layout:auto"}

## Lien de flux de paiement PayPal

| Nom | Chemin de configuration | Prise en charge des versions de Commerce ? |
|--------------|--------------|--------------|
| Partenaire | `payment/payflow_link/partner` | Tous |
| Fournisseur | `payment/payflow_link/vendor` | Tous |
| Activer le lien de flux de production | `payment/payflow_link/active` | Tous |
| Activer le passage en caisse express | `payment/payflow_express/active` | Tous |
| Ordre de tri Crédit PayPal | `payment/payflow_express_bml/sort_order` | Tous |
| Paiement Applicable À Partir De | `payment/payflow_link/allowspecific` | Tous |
| Pays Paiement Applicable De | `payment/payflow_link/specificcountry` | Tous |
| Activer la vérification SSL | `payment/payflow_link/verify_peer` | Tous |
| L’entrée CVV est modifiable. | `payment/payflow_link/csc_editable` | Tous |
| Exiger une entrée CVV | `payment/payflow_link/csc_required` | Tous |
| Envoyer un e-mail de confirmation | `payment/payflow_link/email_confirmation` | Tous |
| Récupération planifiée | `payment_all_paypal/payflow_link/settings_payflow_link/settings_payflow_link_advanced/payflow_link_settlement_report/heading_schedule` | Tous |
| Titre | `payment/payflow_link/title` | Tous |
| Ordre de tri | `payment/payflow_link/sort_order` | Tous |
| Action de paiement | `payment/payflow_link/payment_action` | Tous |

{style="table-layout:auto"}

## Aucun chemin d’extraction de sous-total

| Nom | Chemin de configuration | Prise en charge des versions de Commerce ? |
|--------------|--------------|--------------|
| Activé | `payment/free/active` | Tous |
| Titre | `payment/free/title` | Tous |
| Statut de la nouvelle commande | `payment/free/order_status` | Tous |
| Facturer Automatiquement Tous Les Articles | `payment/free/payment_action` | Tous |
| Paiement des pays applicables | `payment/free/allowspecific` | Tous |
| Paiement de pays spécifiques | `payment/free/specificcountry` | Tous |
| Ordre de tri | `payment/free/sort_order` | Tous |

{style="table-layout:auto"}

## Chemins de paiement contre remboursement

| Nom | Chemin de configuration | Prise en charge des versions de Commerce ? |
|--------------|--------------|--------------|
| Activé | `payment/cashondelivery/active` | Tous |
| Titre | `payment/cashondelivery/title` | Tous |
| Statut de la nouvelle commande | `payment/cashondelivery/order_status` | Tous |
| Paiement des pays applicables | `payment/cashondelivery/allowspecific` | Tous |
| Paiement de pays spécifiques | `payment/cashondelivery/specificcountry` | Tous |
| Instructions | `payment/cashondelivery/instructions` | Tous |
| Nombre total minimum de commandes | `payment/cashondelivery/min_order_total` | Tous |
| Nombre total maximal de commandes | `payment/cashondelivery/max_order_total` | Tous |
| Ordre de tri | `payment/cashondelivery/sort_order` | Tous |

{style="table-layout:auto"}

## Chemins de paiement du virement bancaire

| Nom | Chemin de configuration | Prise en charge des versions de Commerce ? |
|--------------|--------------|--------------|
| Activé | `payment/banktransfer/active` | Tous |
| Titre | `payment/banktransfer/title` | Tous |
| Statut de la nouvelle commande | `payment/banktransfer/order_status` | Tous |
| Paiement des pays applicables | `payment/banktransfer/allowspecific` | Tous |
| Paiement de pays spécifiques | `payment/banktransfer/specificcountry` | Tous |
| Instructions | `payment/banktransfer/instructions` | Tous |
| Nombre total minimum de commandes | `payment/banktransfer/min_order_total` | Tous |
| Nombre total maximal de commandes | `payment/banktransfer/max_order_total` | Tous |
| Ordre de tri | `payment/banktransfer/sort_order` | Tous |

{style="table-layout:auto"}

## Chemins de chèques ou de mandats

| Nom | Chemin de configuration | Prise en charge des versions de Commerce ? |
|--------------|--------------|--------------|
| Activé | `payment/checkmo/active` | Tous |
| Titre | `payment/checkmo/title` | Tous |
| Statut de la nouvelle commande | `payment/checkmo/order_status` | Tous |
| Paiement des pays applicables | `payment/checkmo/allowspecific` | Tous |
| Paiement de pays spécifiques | `payment/checkmo/specificcountry` | Tous |
| Rendre un chèque payable à | `payment/checkmo/payable_to` | Tous |
| Nombre total minimum de commandes | `payment/checkmo/min_order_total` | Tous |
| Nombre total maximal de commandes | `payment/checkmo/max_order_total` | Tous |
| Ordre de tri | `payment/checkmo/sort_order` | Tous |

{style="table-layout:auto"}

## Chemins de commande fournisseur

| Nom | Chemin de configuration | Prise en charge des versions de Commerce ? |
|--------------|--------------|--------------|
| Activé | `payment/purchaseorder/active` | Tous |
| Titre | `payment/purchaseorder/title` | Tous |
| Statut de la nouvelle commande | `payment/purchaseorder/order_status` | Tous |
| Paiement des pays applicables | `payment/purchaseorder/allowspecific` | Tous |
| Paiement de pays spécifiques | `payment/purchaseorder/specificcountry` | Tous |
| Nombre total minimum de commandes | `payment/purchaseorder/min_order_total` | Tous |
| Nombre total maximal de commandes | `payment/purchaseorder/max_order_total` | Tous |
| Ordre de tri | `payment/purchaseorder/sort_order` | Tous |

{style="table-layout:auto"}

## Chemins internationaux

>[!INFO]
>
>Les chemins disponibles sont déterminés par votre choix de [Pays commerçant](../reference/config-reference-sens.md#payment-sensitive-and-system-specific-paths).

| Nom | Chemin de configuration | Prise en charge des versions de Commerce ? |
|--------------|--------------|--------------|
| Informations d’identification SFTP | `payment_nz/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | Tous |
| Récupération planifiée | `payment_nz/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | Tous |
| Style des pages marchandes PayPal | `payment_nz/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | Tous |
| Activer cette solution | `payment/wps_express/active` | Tous |
| Récupération planifiée | `payment_nz/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | Tous |
| Style des pages marchandes PayPal | `payment_nz/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | Tous |
| Paramètres de carte de crédit | `payment_nz/paypal_payment_gateways/paypal_payflowpro_nz/settings_paypal_payflow/heading_cc` | Tous |
| Rejeter la transaction si : | `payment_nz/paypal_payment_gateways/paypal_payflowpro_nz/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_avs_check/heading_avs_settings` | Tous |
| Récupération planifiée | `payment_nz/paypal_payment_gateways/paypal_payflowpro_nz/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_schedule` | Tous |
| Activé | `payment_nz/free/active` | Tous |
| Titre | `payment_nz/free/title` | Tous |
| Statut de la nouvelle commande | `payment_nz/free/order_status` | Tous |
| Facturer Automatiquement Tous Les Articles | `payment_nz/free/payment_action` | Tous |
| Paiement des pays applicables | `payment_nz/free/allowspecific` | Tous |
| Paiement de pays spécifiques | `payment_nz/free/specificcountry` | Tous |
| Ordre de tri | `payment_nz/free/sort_order` | Tous |
| Activé | `payment_nz/cashondelivery/active` | Tous |
| Titre | `payment_nz/cashondelivery/title` | Tous |
| Statut de la nouvelle commande | `payment_nz/cashondelivery/order_status` | Tous |
| Paiement des pays applicables | `payment_nz/cashondelivery/allowspecific` | Tous |
| Paiement de pays spécifiques | `payment_nz/cashondelivery/specificcountry` | Tous |
| Instructions | `payment_nz/cashondelivery/instructions` | Tous |
| Nombre total minimum de commandes | `payment_nz/cashondelivery/min_order_total` | Tous |
| Nombre total maximal de commandes | `payment_nz/cashondelivery/max_order_total` | Tous |
| Ordre de tri | `payment_nz/cashondelivery/sort_order` | Tous |
| Activé | `payment_nz/banktransfer/active` | Tous |
| Titre | `payment_nz/banktransfer/title` | Tous |
| Statut de la nouvelle commande | `payment_nz/banktransfer/order_status` | Tous |
| Paiement des pays applicables | `payment_nz/banktransfer/allowspecific` | Tous |
| Paiement de pays spécifiques | `payment_nz/banktransfer/specificcountry` | Tous |
| Instructions | `payment_nz/banktransfer/instructions` | Tous |
| Nombre total minimum de commandes | `payment_nz/banktransfer/min_order_total` | Tous |
| Nombre total maximal de commandes | `payment_nz/banktransfer/max_order_total` | Tous |
| Ordre de tri | `payment_nz/banktransfer/sort_order` | Tous |
| Activé | `payment_nz/checkmo/active` | Tous |
| Titre | `payment_nz/checkmo/title` | Tous |
| Statut de la nouvelle commande | `payment_nz/checkmo/order_status` | Tous |
| Paiement des pays applicables | `payment_nz/checkmo/allowspecific` | Tous |
| Paiement de pays spécifiques | `payment_nz/checkmo/specificcountry` | Tous |
| Rendre un chèque payable à | `payment_nz/checkmo/payable_to` | Tous |
| Envoyer la vérification à | `payment_nz/checkmo/mailing_address` | Tous |
| Nombre total minimum de commandes | `payment_nz/checkmo/min_order_total` | Tous |
| Nombre total maximal de commandes | `payment_nz/checkmo/max_order_total` | Tous |
| Ordre de tri | `payment_nz/checkmo/sort_order` | Tous |
| Activé | `payment_nz/purchaseorder/active` | Tous |
| Titre | `payment_nz/purchaseorder/title` | Tous |
| Statut de la nouvelle commande | `payment_nz/purchaseorder/order_status` | Tous |
| Paiement des pays applicables | `payment_nz/purchaseorder/allowspecific` | Tous |
| Paiement de pays spécifiques | `payment_nz/purchaseorder/specificcountry` | Tous |
| Nombre total minimum de commandes | `payment_nz/purchaseorder/min_order_total` | Tous |
| Nombre total maximal de commandes | `payment_nz/purchaseorder/max_order_total` | Tous |
| Ordre de tri | `payment_nz/purchaseorder/sort_order` | Tous |
| Activé | `payment_nz/authorizenet_directpost/active` | Tous |
| Action de paiement | `payment_nz/authorizenet_directpost/payment_action` | Tous |
| Titre | `payment_nz/authorizenet_directpost/title` | Tous |
| Statut de la nouvelle commande | `payment_nz/authorizenet_directpost/order_status` | Tous |
| Devise acceptée | `payment_nz/authorizenet_directpost/currency` | Tous |
| Déboguer | `payment_nz/authorizenet_directpost/debug` | Tous |
| Types de carte de crédit | `payment_nz/authorizenet_directpost/cctypes` | Tous |
| Vérification de carte de crédit | `payment_nz/authorizenet_directpost/useccv` | Tous |
| Paiement des pays applicables | `payment_nz/authorizenet_directpost/allowspecific` | Tous |
| Paiement de pays spécifiques | `payment_nz/authorizenet_directpost/specificcountry` | Tous |
| Nombre total minimum de commandes | `payment_nz/authorizenet_directpost/min_order_total` | Tous |
| Nombre total maximal de commandes | `payment_nz/authorizenet_directpost/max_order_total` | Tous |
| Ordre de tri | `payment_nz/authorizenet_directpost/sort_order` | Tous |
| Activé | `payment_nz/cybersource/active` | Commerce Enterprise uniquement |
| Action de paiement | `payment_nz/cybersource/payment_action` | Commerce Enterprise uniquement |
| Titre | `payment_nz/cybersource/title` | Commerce Enterprise uniquement |
| Statut de la nouvelle commande | `payment_nz/cybersource/order_status` | Commerce Enterprise uniquement |
| Déboguer | `payment_nz/cybersource/debug` | Commerce Enterprise uniquement |
| Types de carte de crédit | `payment_nz/cybersource/cctypes` | Commerce Enterprise uniquement |
| Paiement des pays applicables | `payment_nz/cybersource/allowspecific` | Commerce Enterprise uniquement |
| Paiement de pays spécifiques | `payment_nz/cybersource/specificcountry` | Commerce Enterprise uniquement |
| Nombre total minimum de commandes | `payment_nz/cybersource/min_order_total` | Commerce Enterprise uniquement |
| Nombre total maximal de commandes | `payment_nz/cybersource/max_order_total` | Commerce Enterprise uniquement |
| Ordre de tri | `payment_nz/cybersource/sort_order` | Commerce Enterprise uniquement |
| Activé | `payment_nz/worldpay/active` | Commerce Enterprise uniquement |
| Titre | `payment_nz/worldpay/title` | Commerce Enterprise uniquement |
| Autoriser À Modifier Les Coordonnées | `payment_nz/worldpay/fix_contact` | Commerce Enterprise uniquement |
| Masquer les coordonnées | `payment_nz/worldpay/hide_contact` | Commerce Enterprise uniquement |
| Champs de signature | `payment_nz/worldpay/signature_fields` | Commerce Enterprise uniquement |
| Déboguer | `payment_nz/worldpay/debug` | Commerce Enterprise uniquement |
| Action de paiement pour le test | `payment_nz/worldpay/test_action` | Commerce Enterprise uniquement |
| Action de paiement | `payment_nz/worldpay/payment_action` | Commerce Enterprise uniquement |
| Paiement Des Pays Applicables | `payment_nz/worldpay/allowspecific` | Commerce Enterprise uniquement |
| Paiement De Pays Spécifiques | `payment_nz/worldpay/specificcountry` | Commerce Enterprise uniquement |
| Définir le statut de la commande sur Fraude suspectée pour CVV | `payment_nz/worldpay/cvv_fraud_case` | Commerce Enterprise uniquement |
| Définir le statut de la commande sur Fraude suspectée pour le code postal AVS | `payment_nz/worldpay/avs_fraud_case` | Commerce Enterprise uniquement |
| Ordre de tri | `payment_nz/worldpay/sort_order` | Commerce Enterprise uniquement |
| Activé | `payment_nz/eway/active` | Commerce Enterprise uniquement |
| Type de connexion | `payment_nz/eway/connection_type` | Commerce Enterprise uniquement |
| Titre | `payment_nz/eway/title` | Commerce Enterprise uniquement |
| Action de paiement | `payment_nz/eway/payment_action` | Commerce Enterprise uniquement |
| Déboguer | `payment_nz/eway/debug` | Commerce Enterprise uniquement |
| Types de carte de crédit | `payment_nz/eway/cctypes` | Commerce Enterprise uniquement |
| Paiement des pays applicables | `payment_nz/eway/allowspecific` | Commerce Enterprise uniquement |
| Paiement de pays spécifiques | `payment_nz/eway/specificcountry` | Commerce Enterprise uniquement |
| Ordre de tri | `payment_nz/eway/sort_order` | Commerce Enterprise uniquement |
| Récupération planifiée | `payment_hk/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | Tous |
| Style des pages marchandes PayPal | `payment_hk/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | Tous |
| Récupération planifiée | `payment_hk/paypal_group_all_in_one/payments_pro_hosted_solution_hk/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_schedule` | Tous |
| Récupération planifiée | `payment_hk/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | Tous |
| Style des pages marchandes PayPal | `payment_hk/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | Tous |
| Activé | `payment_hk/free/active` | Tous |
| Titre | `payment_hk/free/title` | Tous |
| Statut de la nouvelle commande | `payment_hk/free/order_status` | Tous |
| Facturer Automatiquement Tous Les Articles | `payment_hk/free/payment_action` | Tous |
| Paiement des pays applicables | `payment_hk/free/allowspecific` | Tous |
| Paiement de pays spécifiques | `payment_hk/free/specificcountry` | Tous |
| Ordre de tri | `payment_hk/free/sort_order` | Tous |
| Activé | `payment_hk/cashondelivery/active` | Tous |
| Titre | `payment_hk/cashondelivery/title` | Tous |
| Statut de la nouvelle commande | `payment_hk/cashondelivery/order_status` | Tous |
| Paiement des pays applicables | `payment_hk/cashondelivery/allowspecific` | Tous |
| Paiement de pays spécifiques | `payment_hk/cashondelivery/specificcountry` | Tous |
| Instructions | `payment_hk/cashondelivery/instructions` | Tous |
| Nombre total minimum de commandes | `payment_hk/cashondelivery/min_order_total` | Tous |
| Nombre total maximal de commandes | `payment_hk/cashondelivery/max_order_total` | Tous |
| Ordre de tri | `payment_hk/cashondelivery/sort_order` | Tous |
| Activé | `payment_hk/banktransfer/active` | Tous |
| Titre | `payment_hk/banktransfer/title` | Tous |
| Statut de la nouvelle commande | `payment_hk/banktransfer/order_status` | Tous |
| Paiement des pays applicables | `payment_hk/banktransfer/allowspecific` | Tous |
| Paiement de pays spécifiques | `payment_hk/banktransfer/specificcountry` | Tous |
| Instructions | `payment_hk/banktransfer/instructions` | Tous |
| Nombre total minimum de commandes | `payment_hk/banktransfer/min_order_total` | Tous |
| Nombre total maximal de commandes | `payment_hk/banktransfer/max_order_total` | Tous |
| Ordre de tri | `payment_hk/banktransfer/sort_order` | Tous |
| Activé | `payment_hk/checkmo/active` | Tous |
| Titre | `payment_hk/checkmo/title` | Tous |
| Statut de la nouvelle commande | `payment_hk/checkmo/order_status` | Tous |
| Paiement des pays applicables | `payment_hk/checkmo/allowspecific` | Tous |
| Paiement de pays spécifiques | `payment_hk/checkmo/specificcountry` | Tous |
| Nombre total minimum de commandes | `payment_hk/checkmo/min_order_total` | Tous |
| Nombre total maximal de commandes | `payment_hk/checkmo/max_order_total` | Tous |
| Ordre de tri | `payment_hk/checkmo/sort_order` | Tous |
| Activé | `payment_hk/purchaseorder/active` | Tous |
| Titre | `payment_hk/purchaseorder/title` | Tous |
| Statut de la nouvelle commande | `payment_hk/purchaseorder/order_status` | Tous |
| Paiement des pays applicables | `payment_hk/purchaseorder/allowspecific` | Tous |
| Paiement de pays spécifiques | `payment_hk/purchaseorder/specificcountry` | Tous |
| Nombre total minimum de commandes | `payment_hk/purchaseorder/min_order_total` | Tous |
| Nombre total maximal de commandes | `payment_hk/purchaseorder/max_order_total` | Tous |
| Ordre de tri | `payment_hk/purchaseorder/sort_order` | Tous |
| Activé | `payment_hk/authorizenet_directpost/active` | Tous |
| Action de paiement | `payment_hk/authorizenet_directpost/payment_action` | Tous |
| Titre | `payment_hk/authorizenet_directpost/title` | Tous |
| Statut de la nouvelle commande | `payment_hk/authorizenet_directpost/order_status` | Tous |
| Devise acceptée | `payment_hk/authorizenet_directpost/currency` | Tous |
| Déboguer | `payment_hk/authorizenet_directpost/debug` | Tous |
| Types de carte de crédit | `payment_hk/authorizenet_directpost/cctypes` | Tous |
| Vérification de carte de crédit | `payment_hk/authorizenet_directpost/useccv` | Tous |
| Paiement des pays applicables | `payment_hk/authorizenet_directpost/allowspecific` | Tous |
| Paiement de pays spécifiques | `payment_hk/authorizenet_directpost/specificcountry` | Tous |
| Nombre total minimum de commandes | `payment_hk/authorizenet_directpost/min_order_total` | Tous |
| Nombre total maximal de commandes | `payment_hk/authorizenet_directpost/max_order_total` | Tous |
| Ordre de tri | `payment_hk/authorizenet_directpost/sort_order` | Tous |
| Activé | `payment_hk/cybersource/active` | Commerce Enterprise uniquement |
| Action de paiement | `payment_hk/cybersource/payment_action` | Commerce Enterprise uniquement |
| Titre | `payment_hk/cybersource/title` | Commerce Enterprise uniquement |
| Statut de la nouvelle commande | `payment_hk/cybersource/order_status` | Commerce Enterprise uniquement |
| Déboguer | `payment_hk/cybersource/debug` | Commerce Enterprise uniquement |
| Types de carte de crédit | `payment_hk/cybersource/cctypes` | Commerce Enterprise uniquement |
| Paiement des pays applicables | `payment_hk/cybersource/allowspecific` | Commerce Enterprise uniquement |
| Paiement de pays spécifiques | `payment_hk/cybersource/specificcountry` | Commerce Enterprise uniquement |
| Nombre total minimum de commandes | `payment_hk/cybersource/min_order_total` | Commerce Enterprise uniquement |
| Nombre total maximal de commandes | `payment_hk/cybersource/max_order_total` | Commerce Enterprise uniquement |
| Ordre de tri | `payment_hk/cybersource/sort_order` | Commerce Enterprise uniquement |
| Activé | `payment_hk/worldpay/active` | Commerce Enterprise uniquement |
| Titre | `payment_hk/worldpay/title` | Commerce Enterprise uniquement |
| Autoriser À Modifier Les Coordonnées | `payment_hk/worldpay/fix_contact` | Commerce Enterprise uniquement |
| Masquer les coordonnées | `payment_hk/worldpay/hide_contact` | Commerce Enterprise uniquement |
| Déboguer | `payment_hk/worldpay/debug` | Commerce Enterprise uniquement |
| Action de paiement pour le test | `payment_hk/worldpay/test_action` | Commerce Enterprise uniquement |
| Action de paiement | `payment_hk/worldpay/payment_action` | Commerce Enterprise uniquement |
| Paiement Des Pays Applicables | `payment_hk/worldpay/allowspecific` | Commerce Enterprise uniquement |
| Paiement De Pays Spécifiques | `payment_hk/worldpay/specificcountry` | Commerce Enterprise uniquement |
| Définir le statut de la commande sur Fraude suspectée pour CVV | `payment_hk/worldpay/cvv_fraud_case` | Commerce Enterprise uniquement |
| Définir le statut de la commande sur Fraude suspectée pour le code postal AVS | `payment_hk/worldpay/avs_fraud_case` | Commerce Enterprise uniquement |
| Ordre de tri | `payment_hk/worldpay/sort_order` | Commerce Enterprise uniquement |
| Activé | `payment_hk/eway/active` | Commerce Enterprise uniquement |
| Type de connexion | `payment_hk/eway/connection_type` | Commerce Enterprise uniquement |
| Titre | `payment_hk/eway/title` | Commerce Enterprise uniquement |
| Mode Sandbox | `payment_hk/eway/sandbox_flag` | Commerce Enterprise uniquement |
| Action de paiement | `payment_hk/eway/payment_action` | Commerce Enterprise uniquement |
| Déboguer | `payment_hk/eway/debug` | Commerce Enterprise uniquement |
| Types de carte de crédit | `payment_hk/eway/cctypes` | Commerce Enterprise uniquement |
| Paiement des pays applicables | `payment_hk/eway/allowspecific` | Commerce Enterprise uniquement |
| Paiement de pays spécifiques | `payment_hk/eway/specificcountry` | Commerce Enterprise uniquement |
| Ordre de tri | `payment_hk/eway/sort_order` | Commerce Enterprise uniquement |
| Récupération planifiée | `payment_es/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | Tous |
| Style des pages marchandes PayPal | `payment_es/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | Tous |
| Récupération planifiée | `payment_es/paypal_group_all_in_one/payments_pro_hosted_solution_es/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_schedule` | Tous |
| Récupération planifiée | `payment_es/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | Tous |
| Style des pages marchandes PayPal | `payment_es/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | Tous |
| Activé | `payment_es/free/active` | Tous |
| Titre | `payment_es/free/title` | Tous |
| Statut de la nouvelle commande | `payment_es/free/order_status` | Tous |
| Facturer Automatiquement Tous Les Articles | `payment_es/free/payment_action` | Tous |
| Paiement des pays applicables | `payment_es/free/allowspecific` | Tous |
| Paiement de pays spécifiques | `payment_es/free/specificcountry` | Tous |
| Ordre de tri | `payment_es/free/sort_order` | Tous |
| Activé | `payment_es/cashondelivery/active` | Tous |
| Titre | `payment_es/cashondelivery/title` | Tous |
| Statut de la nouvelle commande | `payment_es/cashondelivery/order_status` | Tous |
| Paiement des pays applicables | `payment_es/cashondelivery/allowspecific` | Tous |
| Paiement de pays spécifiques | `payment_es/cashondelivery/specificcountry` | Tous |
| Instructions | `payment_es/cashondelivery/instructions` | Tous |
| Nombre total minimum de commandes | `payment_es/cashondelivery/min_order_total` | Tous |
| Nombre total maximal de commandes | `payment_es/cashondelivery/max_order_total` | Tous |
| Ordre de tri | `payment_es/cashondelivery/sort_order` | Tous |
| Activé | `payment_es/banktransfer/active` | Tous |
| Titre | `payment_es/banktransfer/title` | Tous |
| Statut de la nouvelle commande | `payment_es/banktransfer/order_status` | Tous |
| Paiement des pays applicables | `payment_es/banktransfer/allowspecific` | Tous |
| Paiement de pays spécifiques | `payment_es/banktransfer/specificcountry` | Tous |
| Instructions | `payment_es/banktransfer/instructions` | Tous |
| Nombre total minimum de commandes | `payment_es/banktransfer/min_order_total` | Tous |
| Nombre total maximal de commandes | `payment_es/banktransfer/max_order_total` | Tous |
| Ordre de tri | `payment_es/banktransfer/sort_order` | Tous |
| Activé | `payment_es/checkmo/active` | Tous |
| Titre | `payment_es/checkmo/title` | Tous |
| Statut de la nouvelle commande | `payment_es/checkmo/order_status` | Tous |
| Paiement des pays applicables | `payment_es/checkmo/allowspecific` | Tous |
| Paiement de pays spécifiques | `payment_es/checkmo/specificcountry` | Tous |
| Rendre un chèque payable à | `payment_es/checkmo/payable_to` | Tous |
| Nombre total minimum de commandes | `payment_es/checkmo/min_order_total` | Tous |
| Nombre total maximal de commandes | `payment_es/checkmo/max_order_total` | Tous |
| Ordre de tri | `payment_es/checkmo/sort_order` | Tous |
| Activé | `payment_es/purchaseorder/active` | Tous |
| Titre | `payment_es/purchaseorder/title` | Tous |
| Statut de la nouvelle commande | `payment_es/purchaseorder/order_status` | Tous |
| Paiement des pays applicables | `payment_es/purchaseorder/allowspecific` | Tous |
| Paiement de pays spécifiques | `payment_es/purchaseorder/specificcountry` | Tous |
| Nombre total minimum de commandes | `payment_es/purchaseorder/min_order_total` | Tous |
| Nombre total maximal de commandes | `payment_es/purchaseorder/max_order_total` | Tous |
| Ordre de tri | `payment_es/purchaseorder/sort_order` | Tous |
| Activé | `payment_es/authorizenet_directpost/active` | Tous |
| Action de paiement | `payment_es/authorizenet_directpost/payment_action` | Tous |
| Titre | `payment_es/authorizenet_directpost/title` | Tous |
| Statut de la nouvelle commande | `payment_es/authorizenet_directpost/order_status` | Tous |
| Devise acceptée | `payment_es/authorizenet_directpost/currency` | Tous |
| Déboguer | `payment_es/authorizenet_directpost/debug` | Tous |
| Types de carte de crédit | `payment_es/authorizenet_directpost/cctypes` | Tous |
| Vérification de carte de crédit | `payment_es/authorizenet_directpost/useccv` | Tous |
| Paiement des pays applicables | `payment_es/authorizenet_directpost/allowspecific` | Tous |
| Paiement de pays spécifiques | `payment_es/authorizenet_directpost/specificcountry` | Tous |
| Nombre total minimum de commandes | `payment_es/authorizenet_directpost/min_order_total` | Tous |
| Nombre total maximal de commandes | `payment_es/authorizenet_directpost/max_order_total` | Tous |
| Ordre de tri | `payment_es/authorizenet_directpost/sort_order` | Tous |
| Activé | `payment_es/cybersource/active` | Commerce Enterprise uniquement |
| Action de paiement | `payment_es/cybersource/payment_action` | Commerce Enterprise uniquement |
| Titre | `payment_es/cybersource/title` | Commerce Enterprise uniquement |
| Identifiant du profil | `payment_es/cybersource/profile_id` | Commerce Enterprise uniquement\| ![Chiffré](/help/assets/configuration/cloud-enc.png) |
| Statut de la nouvelle commande | `payment_es/cybersource/order_status` | Commerce Enterprise uniquement |
| Déboguer | `payment_es/cybersource/debug` | Commerce Enterprise uniquement |
| Types de carte de crédit | `payment_es/cybersource/cctypes` | Commerce Enterprise uniquement |
| Paiement des pays applicables | `payment_es/cybersource/allowspecific` | Commerce Enterprise uniquement |
| Paiement de pays spécifiques | `payment_es/cybersource/specificcountry` | Commerce Enterprise uniquement |
| Nombre total minimum de commandes | `payment_es/cybersource/min_order_total` | Commerce Enterprise uniquement |
| Nombre total maximal de commandes | `payment_es/cybersource/max_order_total` | Commerce Enterprise uniquement |
| Ordre de tri | `payment_es/cybersource/sort_order` | Commerce Enterprise uniquement |
| Activé | `payment_es/worldpay/active` | Commerce Enterprise uniquement |
| Titre | `payment_es/worldpay/title` | Commerce Enterprise uniquement |
| ID d’installation | `payment_es/worldpay/installation_id` | Commerce Enterprise uniquement |
| ID d’installation de l’administrateur distant | `payment_es/worldpay/admin_installation_id` | Commerce Enterprise uniquement |
| Autoriser À Modifier Les Coordonnées | `payment_es/worldpay/fix_contact` | Commerce Enterprise uniquement |
| Masquer les coordonnées | `payment_es/worldpay/hide_contact` | Commerce Enterprise uniquement |
| Champs de signature | `payment_es/worldpay/signature_fields` | Commerce Enterprise uniquement |
| Mode Test | `payment_es/worldpay/sandbox_flag` | Commerce Enterprise uniquement |
| Action de paiement pour le test | `payment_es/worldpay/test_action` | Commerce Enterprise uniquement |
| Action de paiement | `payment_es/worldpay/payment_action` | Commerce Enterprise uniquement |
| Paiement Des Pays Applicables | `payment_es/worldpay/allowspecific` | Commerce Enterprise uniquement |
| Paiement De Pays Spécifiques | `payment_es/worldpay/specificcountry` | Commerce Enterprise uniquement |
| Définir le statut de la commande sur Fraude suspectée pour CVV | `payment_es/worldpay/cvv_fraud_case` | Commerce Enterprise uniquement |
| Définir le statut de la commande sur Fraude suspectée pour le code postal AVS | `payment_es/worldpay/avs_fraud_case` | Commerce Enterprise uniquement |
| Ordre de tri | `payment_es/worldpay/sort_order` | Commerce Enterprise uniquement |
| Activé | `payment_es/eway/active` | Commerce Enterprise uniquement |
| Type de connexion | `payment_es/eway/connection_type` | Commerce Enterprise uniquement |
| Titre | `payment_es/eway/title` | Commerce Enterprise uniquement |
| Action de paiement | `payment_es/eway/payment_action` | Commerce Enterprise uniquement |
| Déboguer | `payment_es/eway/debug` | Commerce Enterprise uniquement |
| Types de carte de crédit | `payment_es/eway/cctypes` | Commerce Enterprise uniquement |
| Paiement des pays applicables | `payment_es/eway/allowspecific` | Commerce Enterprise uniquement |
| Paiement de pays spécifiques | `payment_es/eway/specificcountry` | Commerce Enterprise uniquement |
| Ordre de tri | `payment_es/eway/sort_order` | Commerce Enterprise uniquement |
| Récupération planifiée | `payment_it/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | Tous |
| Style des pages marchandes PayPal | `payment_it/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | Tous |
| Récupération planifiée | `payment_it/paypal_group_all_in_one/payments_pro_hosted_solution_it/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_schedule` | Tous |
| Récupération planifiée | `payment_it/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | Tous |
| Style des pages marchandes PayPal | `payment_it/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | Tous |
| Activé | `payment_it/free/active` | Tous |
| Titre | `payment_it/free/title` | Tous |
| Statut de la nouvelle commande | `payment_it/free/order_status` | Tous |
| Facturer Automatiquement Tous Les Articles | `payment_it/free/payment_action` | Tous |
| Paiement des pays applicables | `payment_it/free/allowspecific` | Tous |
| Paiement de pays spécifiques | `payment_it/free/specificcountry` | Tous |
| Ordre de tri | `payment_it/free/sort_order` | Tous |
| Activé | `payment_it/cashondelivery/active` | Tous |
| Titre | `payment_it/cashondelivery/title` | Tous |
| Statut de la nouvelle commande | `payment_it/cashondelivery/order_status` | Tous |
| Paiement des pays applicables | `payment_it/cashondelivery/allowspecific` | Tous |
| Paiement de pays spécifiques | `payment_it/cashondelivery/specificcountry` | Tous |
| Instructions | `payment_it/cashondelivery/instructions` | Tous |
| Nombre total minimum de commandes | `payment_it/cashondelivery/min_order_total` | Tous |
| Nombre total maximal de commandes | `payment_it/cashondelivery/max_order_total` | Tous |
| Ordre de tri | `payment_it/cashondelivery/sort_order` | Tous |
| Activé | `payment_it/banktransfer/active` | Tous |
| Titre | `payment_it/banktransfer/title` | Tous |
| Statut de la nouvelle commande | `payment_it/banktransfer/order_status` | Tous |
| Paiement des pays applicables | `payment_it/banktransfer/allowspecific` | Tous |
| Paiement de pays spécifiques | `payment_it/banktransfer/specificcountry` | Tous |
| Instructions | `payment_it/banktransfer/instructions` | Tous |
| Nombre total minimum de commandes | `payment_it/banktransfer/min_order_total` | Tous |
| Nombre total maximal de commandes | `payment_it/banktransfer/max_order_total` | Tous |
| Ordre de tri | `payment_it/banktransfer/sort_order` | Tous |
| Activé | `payment_it/checkmo/active` | Tous |
| Titre | `payment_it/checkmo/title` | Tous |
| Statut de la nouvelle commande | `payment_it/checkmo/order_status` | Tous |
| Paiement des pays applicables | `payment_it/checkmo/allowspecific` | Tous |
| Paiement de pays spécifiques | `payment_it/checkmo/specificcountry` | Tous |
| Nombre total minimum de commandes | `payment_it/checkmo/min_order_total` | Tous |
| Nombre total maximal de commandes | `payment_it/checkmo/max_order_total` | Tous |
| Ordre de tri | `payment_it/checkmo/sort_order` | Tous |
| Activé | `payment_it/purchaseorder/active` | Tous |
| Titre | `payment_it/purchaseorder/title` | Tous |
| Statut de la nouvelle commande | `payment_it/purchaseorder/order_status` | Tous |
| Paiement des pays applicables | `payment_it/purchaseorder/allowspecific` | Tous |
| Paiement de pays spécifiques | `payment_it/purchaseorder/specificcountry` | Tous |
| Nombre total minimum de commandes | `payment_it/purchaseorder/min_order_total` | Tous |
| Nombre total maximal de commandes | `payment_it/purchaseorder/max_order_total` | Tous |
| Ordre de tri | `payment_it/purchaseorder/sort_order` | Tous |
| Activé | `payment_it/authorizenet_directpost/active` | Tous |
| Action de paiement | `payment_it/authorizenet_directpost/payment_action` | Tous |
| Titre | `payment_it/authorizenet_directpost/title` | Tous |
| Statut de la nouvelle commande | `payment_it/authorizenet_directpost/order_status` | Tous |
| Devise acceptée | `payment_it/authorizenet_directpost/currency` | Tous |
| Déboguer | `payment_it/authorizenet_directpost/debug` | Tous |
| Types de carte de crédit | `payment_it/authorizenet_directpost/cctypes` | Tous |
| Vérification de carte de crédit | `payment_it/authorizenet_directpost/useccv` | Tous |
| Paiement des pays applicables | `payment_it/authorizenet_directpost/allowspecific` | Tous |
| Paiement de pays spécifiques | `payment_it/authorizenet_directpost/specificcountry` | Tous |
| Nombre total minimum de commandes | `payment_it/authorizenet_directpost/min_order_total` | Tous |
| Nombre total maximal de commandes | `payment_it/authorizenet_directpost/max_order_total` | Tous |
| Ordre de tri | `payment_it/authorizenet_directpost/sort_order` | Tous |
| Activé | `payment_it/cybersource/active` | Commerce Enterprise uniquement |
| Action de paiement | `payment_it/cybersource/payment_action` | Commerce Enterprise uniquement |
| Titre | `payment_it/cybersource/title` | Commerce Enterprise uniquement |
| Statut de la nouvelle commande | `payment_it/cybersource/order_status` | Commerce Enterprise uniquement |
| Déboguer | `payment_it/cybersource/debug` | Commerce Enterprise uniquement |
| Types de carte de crédit | `payment_it/cybersource/cctypes` | Commerce Enterprise uniquement |
| Paiement des pays applicables | `payment_it/cybersource/allowspecific` | Commerce Enterprise uniquement |
| Paiement de pays spécifiques | `payment_it/cybersource/specificcountry` | Commerce Enterprise uniquement |
| Nombre total minimum de commandes | `payment_it/cybersource/min_order_total` | Commerce Enterprise uniquement |
| Nombre total maximal de commandes | `payment_it/cybersource/max_order_total` | Commerce Enterprise uniquement |
| Ordre de tri | `payment_it/cybersource/sort_order` | Commerce Enterprise uniquement |
| Activé | `payment_it/worldpay/active` | Commerce Enterprise uniquement |
| Titre | `payment_it/worldpay/title` | Commerce Enterprise uniquement |
| Autoriser À Modifier Les Coordonnées | `payment_it/worldpay/fix_contact` | Commerce Enterprise uniquement |
| Masquer les coordonnées | `payment_it/worldpay/hide_contact` | Commerce Enterprise uniquement |
| Champs de signature | `payment_it/worldpay/signature_fields` | Commerce Enterprise uniquement |
| Déboguer | `payment_it/worldpay/debug` | Commerce Enterprise uniquement |
| Action de paiement pour le test | `payment_it/worldpay/test_action` | Commerce Enterprise uniquement |
| Action de paiement | `payment_it/worldpay/payment_action` | Commerce Enterprise uniquement |
| Paiement Des Pays Applicables | `payment_it/worldpay/allowspecific` | Commerce Enterprise uniquement |
| Paiement De Pays Spécifiques | `payment_it/worldpay/specificcountry` | Commerce Enterprise uniquement |
| Définir le statut de la commande sur Fraude suspectée pour CVV | `payment_it/worldpay/cvv_fraud_case` | Commerce Enterprise uniquement |
| Définir le statut de la commande sur Fraude suspectée pour le code postal AVS | `payment_it/worldpay/avs_fraud_case` | Commerce Enterprise uniquement |
| Ordre de tri | `payment_it/worldpay/sort_order` | Commerce Enterprise uniquement |
| Activé | `payment_it/eway/active` | Commerce Enterprise uniquement |
| Type de connexion | `payment_it/eway/connection_type` | Commerce Enterprise uniquement |
| Titre | `payment_it/eway/title` | Commerce Enterprise uniquement |
| Action de paiement | `payment_it/eway/payment_action` | Commerce Enterprise uniquement |
| Déboguer | `payment_it/eway/debug` | Commerce Enterprise uniquement |
| Types de carte de crédit | `payment_it/eway/cctypes` | Commerce Enterprise uniquement |
| Paiement des pays applicables | `payment_it/eway/allowspecific` | Commerce Enterprise uniquement |
| Paiement de pays spécifiques | `payment_it/eway/specificcountry` | Commerce Enterprise uniquement |
| Ordre de tri | `payment_it/eway/sort_order` | Commerce Enterprise uniquement |
| Récupération planifiée | `payment_fr/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | Tous |
| Style des pages marchandes PayPal | `payment_fr/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | Tous |
| Récupération planifiée | `payment_fr/paypal_group_all_in_one/payments_pro_hosted_solution_fr/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_schedule` | Tous |
| Récupération planifiée | `payment_fr/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | Tous |
| Style des pages marchandes PayPal | `payment_fr/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | Tous |
| Activé | `payment_fr/free/active` | Tous |
| Titre | `payment_fr/free/title` | Tous |
| Statut de la nouvelle commande | `payment_fr/free/order_status` | Tous |
| Facturer Automatiquement Tous Les Articles | `payment_fr/free/payment_action` | Tous |
| Paiement des pays applicables | `payment_fr/free/allowspecific` | Tous |
| Paiement de pays spécifiques | `payment_fr/free/specificcountry` | Tous |
| Ordre de tri | `payment_fr/free/sort_order` | Tous |
| Activé | `payment_fr/cashondelivery/active` | Tous |
| Titre | `payment_fr/cashondelivery/title` | Tous |
| Statut de la nouvelle commande | `payment_fr/cashondelivery/order_status` | Tous |
| Paiement des pays applicables | `payment_fr/cashondelivery/allowspecific` | Tous |
| Paiement de pays spécifiques | `payment_fr/cashondelivery/specificcountry` | Tous |
| Instructions | `payment_fr/cashondelivery/instructions` | Tous |
| Nombre total minimum de commandes | `payment_fr/cashondelivery/min_order_total` | Tous |
| Nombre total maximal de commandes | `payment_fr/cashondelivery/max_order_total` | Tous |
| Ordre de tri | `payment_fr/cashondelivery/sort_order` | Tous |
| Activé | `payment_fr/banktransfer/active` | Tous |
| Titre | `payment_fr/banktransfer/title` | Tous |
| Statut de la nouvelle commande | `payment_fr/banktransfer/order_status` | Tous |
| Paiement des pays applicables | `payment_fr/banktransfer/allowspecific` | Tous |
| Paiement de pays spécifiques | `payment_fr/banktransfer/specificcountry` | Tous |
| Instructions | `payment_fr/banktransfer/instructions` | Tous |
| Nombre total minimum de commandes | `payment_fr/banktransfer/min_order_total` | Tous |
| Nombre total maximal de commandes | `payment_fr/banktransfer/max_order_total` | Tous |
| Ordre de tri | `payment_fr/banktransfer/sort_order` | Tous |
| Activé | `payment_fr/checkmo/active` | Tous |
| Titre | `payment_fr/checkmo/title` | Tous |
| Statut de la nouvelle commande | `payment_fr/checkmo/order_status` | Tous |
| Paiement des pays applicables | `payment_fr/checkmo/allowspecific` | Tous |
| Paiement de pays spécifiques | `payment_fr/checkmo/specificcountry` | Tous |
| Nombre total minimum de commandes | `payment_fr/checkmo/min_order_total` | Tous |
| Nombre total maximal de commandes | `payment_fr/checkmo/max_order_total` | Tous |
| Ordre de tri | `payment_fr/checkmo/sort_order` | Tous |
| Activé | `payment_fr/purchaseorder/active` | Tous |
| Titre | `payment_fr/purchaseorder/title` | Tous |
| Statut de la nouvelle commande | `payment_fr/purchaseorder/order_status` | Tous |
| Paiement des pays applicables | `payment_fr/purchaseorder/allowspecific` | Tous |
| Paiement de pays spécifiques | `payment_fr/purchaseorder/specificcountry` | Tous |
| Nombre total minimum de commandes | `payment_fr/purchaseorder/min_order_total` | Tous |
| Nombre total maximal de commandes | `payment_fr/purchaseorder/max_order_total` | Tous |
| Ordre de tri | `payment_fr/purchaseorder/sort_order` | Tous |
| Activé | `payment_fr/authorizenet_directpost/active` | Tous |
| Action de paiement | `payment_fr/authorizenet_directpost/payment_action` | Tous |
| Titre | `payment_fr/authorizenet_directpost/title` | Tous |
| Statut de la nouvelle commande | `payment_fr/authorizenet_directpost/order_status` | Tous |
| Devise acceptée | `payment_fr/authorizenet_directpost/currency` | Tous |
| Déboguer | `payment_fr/authorizenet_directpost/debug` | Tous |
| Types de carte de crédit | `payment_fr/authorizenet_directpost/cctypes` | Tous |
| Vérification de carte de crédit | `payment_fr/authorizenet_directpost/useccv` | Tous |
| Paiement des pays applicables | `payment_fr/authorizenet_directpost/allowspecific` | Tous |
| Paiement de pays spécifiques | `payment_fr/authorizenet_directpost/specificcountry` | Tous |
| Nombre total minimum de commandes | `payment_fr/authorizenet_directpost/min_order_total` | Tous |
| Nombre total maximal de commandes | `payment_fr/authorizenet_directpost/max_order_total` | Tous |
| Ordre de tri | `payment_fr/authorizenet_directpost/sort_order` | Tous |
| Activé | `payment_fr/cybersource/active` | Commerce Enterprise uniquement |
| Action de paiement | `payment_fr/cybersource/payment_action` | Commerce Enterprise uniquement |
| Titre | `payment_fr/cybersource/title` | Commerce Enterprise uniquement |
| Statut de la nouvelle commande | `payment_fr/cybersource/order_status` | Commerce Enterprise uniquement |
| Déboguer | `payment_fr/cybersource/debug` | Commerce Enterprise uniquement |
| Types de carte de crédit | `payment_fr/cybersource/cctypes` | Commerce Enterprise uniquement |
| Paiement des pays applicables | `payment_fr/cybersource/allowspecific` | Commerce Enterprise uniquement |
| Paiement de pays spécifiques | `payment_fr/cybersource/specificcountry` | Commerce Enterprise uniquement |
| Nombre total minimum de commandes | `payment_fr/cybersource/min_order_total` | Commerce Enterprise uniquement |
| Nombre total maximal de commandes | `payment_fr/cybersource/max_order_total` | Commerce Enterprise uniquement |
| Ordre de tri | `payment_fr/cybersource/sort_order` | Commerce Enterprise uniquement |
| Activé | `payment_fr/worldpay/active` | Commerce Enterprise uniquement |
| Titre | `payment_fr/worldpay/title` | Commerce Enterprise uniquement |
| Autoriser À Modifier Les Coordonnées | `payment_fr/worldpay/fix_contact` | Commerce Enterprise uniquement |
| Masquer les coordonnées | `payment_fr/worldpay/hide_contact` | Commerce Enterprise uniquement |
| Déboguer | `payment_fr/worldpay/debug` | Commerce Enterprise uniquement |
| Action de paiement pour le test | `payment_fr/worldpay/test_action` | Commerce Enterprise uniquement |
| Action de paiement | `payment_fr/worldpay/payment_action` | Commerce Enterprise uniquement |
| Paiement Des Pays Applicables | `payment_fr/worldpay/allowspecific` | Commerce Enterprise uniquement |
| Paiement De Pays Spécifiques | `payment_fr/worldpay/specificcountry` | Commerce Enterprise uniquement |
| Définir le statut de la commande sur Fraude suspectée pour CVV | `payment_fr/worldpay/cvv_fraud_case` | Commerce Enterprise uniquement |
| Définir le statut de la commande sur Fraude suspectée pour le code postal AVS | `payment_fr/worldpay/avs_fraud_case` | Commerce Enterprise uniquement |
| Ordre de tri | `payment_fr/worldpay/sort_order` | Commerce Enterprise uniquement |
| Activé | `payment_fr/eway/active` | Commerce Enterprise uniquement |
| Type de connexion | `payment_fr/eway/connection_type` | Commerce Enterprise uniquement |
| Titre | `payment_fr/eway/title` | Commerce Enterprise uniquement |
| Action de paiement | `payment_fr/eway/payment_action` | Commerce Enterprise uniquement |
| Déboguer | `payment_fr/eway/debug` | Commerce Enterprise uniquement |
| Types de carte de crédit | `payment_fr/eway/cctypes` | Commerce Enterprise uniquement |
| Paiement des pays applicables | `payment_fr/eway/allowspecific` | Commerce Enterprise uniquement |
| Paiement de pays spécifiques | `payment_fr/eway/specificcountry` | Commerce Enterprise uniquement |
| Ordre de tri | `payment_fr/eway/sort_order` | Commerce Enterprise uniquement |
| Récupération planifiée | `payment_jp/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | Tous |
| Style des pages marchandes PayPal | `payment_jp/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | Tous |
| Récupération planifiée | `payment_jp/paypal_group_all_in_one/payments_pro_hosted_solution_jp/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_schedule` | Tous |
| Récupération planifiée | `payment_jp/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | Tous |
| Style des pages marchandes PayPal | `payment_jp/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | Tous |
| Activé | `payment_jp/free/active` | Tous |
| Titre | `payment_jp/free/title` | Tous |
| Statut de la nouvelle commande | `payment_jp/free/order_status` | Tous |
| Facturer Automatiquement Tous Les Articles | `payment_jp/free/payment_action` | Tous |
| Paiement des pays applicables | `payment_jp/free/allowspecific` | Tous |
| Paiement de pays spécifiques | `payment_jp/free/specificcountry` | Tous |
| Ordre de tri | `payment_jp/free/sort_order` | Tous |
| Activé | `payment_jp/cashondelivery/active` | Tous |
| Titre | `payment_jp/cashondelivery/title` | Tous |
| Statut de la nouvelle commande | `payment_jp/cashondelivery/order_status` | Tous |
| Paiement des pays applicables | `payment_jp/cashondelivery/allowspecific` | Tous |
| Paiement de pays spécifiques | `payment_jp/cashondelivery/specificcountry` | Tous |
| Instructions | `payment_jp/cashondelivery/instructions` | Tous |
| Nombre total minimum de commandes | `payment_jp/cashondelivery/min_order_total` | Tous |
| Nombre total maximal de commandes | `payment_jp/cashondelivery/max_order_total` | Tous |
| Ordre de tri | `payment_jp/cashondelivery/sort_order` | Tous |
| Activé | `payment_jp/banktransfer/active` | Tous |
| Titre | `payment_jp/banktransfer/title` | Tous |
| Statut de la nouvelle commande | `payment_jp/banktransfer/order_status` | Tous |
| Paiement des pays applicables | `payment_jp/banktransfer/allowspecific` | Tous |
| Paiement de pays spécifiques | `payment_jp/banktransfer/specificcountry` | Tous |
| Instructions | `payment_jp/banktransfer/instructions` | Tous |
| Nombre total minimum de commandes | `payment_jp/banktransfer/min_order_total` | Tous |
| Nombre total maximal de commandes | `payment_jp/banktransfer/max_order_total` | Tous |
| Ordre de tri | `payment_jp/banktransfer/sort_order` | Tous |
| Activé | `payment_jp/checkmo/active` | Tous |
| Titre | `payment_jp/checkmo/title` | Tous |
| Statut de la nouvelle commande | `payment_jp/checkmo/order_status` | Tous |
| Paiement des pays applicables | `payment_jp/checkmo/allowspecific` | Tous |
| Paiement de pays spécifiques | `payment_jp/checkmo/specificcountry` | Tous |
| Nombre total minimum de commandes | `payment_jp/checkmo/min_order_total` | Tous |
| Nombre total maximal de commandes | `payment_jp/checkmo/max_order_total` | Tous |
| Ordre de tri | `payment_jp/checkmo/sort_order` | Tous |
| Activé | `payment_jp/purchaseorder/active` | Tous |
| Titre | `payment_jp/purchaseorder/title` | Tous |
| Statut de la nouvelle commande | `payment_jp/purchaseorder/order_status` | Tous |
| Paiement des pays applicables | `payment_jp/purchaseorder/allowspecific` | Tous |
| Paiement de pays spécifiques | `payment_jp/purchaseorder/specificcountry` | Tous |
| Nombre total minimum de commandes | `payment_jp/purchaseorder/min_order_total` | Tous |
| Nombre total maximal de commandes | `payment_jp/purchaseorder/max_order_total` | Tous |
| Ordre de tri | `payment_jp/purchaseorder/sort_order` | Tous |
| Activé | `payment_jp/authorizenet_directpost/active` | Tous |
| Action de paiement | `payment_jp/authorizenet_directpost/payment_action` | Tous |
| Titre | `payment_jp/authorizenet_directpost/title` | Tous |
| Statut de la nouvelle commande | `payment_jp/authorizenet_directpost/order_status` | Tous |
| Devise acceptée | `payment_jp/authorizenet_directpost/currency` | Tous |
| Déboguer | `payment_jp/authorizenet_directpost/debug` | Tous |
| Types de carte de crédit | `payment_jp/authorizenet_directpost/cctypes` | Tous |
| Vérification de carte de crédit | `payment_jp/authorizenet_directpost/useccv` | Tous |
| Paiement des pays applicables | `payment_jp/authorizenet_directpost/allowspecific` | Tous |
| Paiement de pays spécifiques | `payment_jp/authorizenet_directpost/specificcountry` | Tous |
| Nombre total minimum de commandes | `payment_jp/authorizenet_directpost/min_order_total` | Tous |
| Nombre total maximal de commandes | `payment_jp/authorizenet_directpost/max_order_total` | Tous |
| Ordre de tri | `payment_jp/authorizenet_directpost/sort_order` | Tous |
| Activé | `payment_jp/cybersource/active` | Commerce Enterprise uniquement |
| Action de paiement | `payment_jp/cybersource/payment_action` | Commerce Enterprise uniquement |
| Titre | `payment_jp/cybersource/title` | Commerce Enterprise uniquement |
| Déboguer | `payment_jp/cybersource/debug` | Commerce Enterprise uniquement |
| Types de carte de crédit | `payment_jp/cybersource/cctypes` | Commerce Enterprise uniquement |
| Paiement des pays applicables | `payment_jp/cybersource/allowspecific` | Commerce Enterprise uniquement |
| Paiement de pays spécifiques | `payment_jp/cybersource/specificcountry` | Commerce Enterprise uniquement |
| Nombre total minimum de commandes | `payment_jp/cybersource/min_order_total` | Commerce Enterprise uniquement |
| Nombre total maximal de commandes | `payment_jp/cybersource/max_order_total` | Commerce Enterprise uniquement |
| Ordre de tri | `payment_jp/cybersource/sort_order` | Commerce Enterprise uniquement |
| Activé | `payment_jp/worldpay/active` | Commerce Enterprise uniquement |
| Titre | `payment_jp/worldpay/title` | Commerce Enterprise uniquement |
| Autoriser À Modifier Les Coordonnées | `payment_jp/worldpay/fix_contact` | Commerce Enterprise uniquement |
| Masquer les coordonnées | `payment_jp/worldpay/hide_contact` | Commerce Enterprise uniquement |
| Déboguer | `payment_jp/worldpay/debug` | Commerce Enterprise uniquement |
| Action de paiement pour le test | `payment_jp/worldpay/test_action` | Commerce Enterprise uniquement |
| Action de paiement | `payment_jp/worldpay/payment_action` | Commerce Enterprise uniquement |
| Paiement Des Pays Applicables | `payment_jp/worldpay/allowspecific` | Commerce Enterprise uniquement |
| Paiement De Pays Spécifiques | `payment_jp/worldpay/specificcountry` | Commerce Enterprise uniquement |
| Définir le statut de la commande sur Fraude suspectée pour CVV | `payment_jp/worldpay/cvv_fraud_case` | Commerce Enterprise uniquement |
| Définir le statut de la commande sur Fraude suspectée pour le code postal AVS | `payment_jp/worldpay/avs_fraud_case` | Commerce Enterprise uniquement |
| Ordre de tri | `payment_jp/worldpay/sort_order` | Commerce Enterprise uniquement |
| Activé | `payment_jp/eway/active` | Commerce Enterprise uniquement |
| Type de connexion | `payment_jp/eway/connection_type` | Commerce Enterprise uniquement |
| Titre | `payment_jp/eway/title` | Commerce Enterprise uniquement |
| Action de paiement | `payment_jp/eway/payment_action` | Commerce Enterprise uniquement |
| Déboguer | `payment_jp/eway/debug` | Commerce Enterprise uniquement |
| Types de carte de crédit | `payment_jp/eway/cctypes` | Commerce Enterprise uniquement |
| Paiement des pays applicables | `payment_jp/eway/allowspecific` | Commerce Enterprise uniquement |
| Paiement de pays spécifiques | `payment_jp/eway/specificcountry` | Commerce Enterprise uniquement |
| Ordre de tri | `payment_jp/eway/sort_order` | Commerce Enterprise uniquement |
| Récupération planifiée | `payment_au/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | Tous |
| Style des pages marchandes PayPal | `payment_au/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | Tous |
| Récupération planifiée | `payment_au/paypal_group_all_in_one/payments_pro_hosted_solution_au/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_schedule` | Tous |
| Récupération planifiée | `payment_au/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | Tous |
| Style des pages marchandes PayPal | `payment_au/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | Tous |
| Paramètres de carte de crédit | `payment_au/paypal_payment_gateways/paypal_payflowpro_au/settings_paypal_payflow/heading_cc` | Tous |
| Rejeter la transaction si : | `payment_au/paypal_payment_gateways/paypal_payflowpro_au/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_avs_check/heading_avs_settings` | Tous |
| Récupération planifiée | `payment_au/paypal_payment_gateways/paypal_payflowpro_au/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_schedule` | Tous |
| Activé | `payment_au/free/active` | Tous |
| Titre | `payment_au/free/title` | Tous |
| Statut de la nouvelle commande | `payment_au/free/order_status` | Tous |
| Facturer Automatiquement Tous Les Articles | `payment_au/free/payment_action` | Tous |
| Paiement des pays applicables | `payment_au/free/allowspecific` | Tous |
| Paiement de pays spécifiques | `payment_au/free/specificcountry` | Tous |
| Ordre de tri | `payment_au/free/sort_order` | Tous |
| Activé | `payment_au/cashondelivery/active` | Tous |
| Titre | `payment_au/cashondelivery/title` | Tous |
| Statut de la nouvelle commande | `payment_au/cashondelivery/order_status` | Tous |
| Paiement des pays applicables | `payment_au/cashondelivery/allowspecific` | Tous |
| Paiement de pays spécifiques | `payment_au/cashondelivery/specificcountry` | Tous |
| Instructions | `payment_au/cashondelivery/instructions` | Tous |
| Nombre total minimum de commandes | `payment_au/cashondelivery/min_order_total` | Tous |
| Nombre total maximal de commandes | `payment_au/cashondelivery/max_order_total` | Tous |
| Ordre de tri | `payment_au/cashondelivery/sort_order` | Tous |
| Activé | `payment_au/banktransfer/active` | Tous |
| Titre | `payment_au/banktransfer/title` | Tous |
| Statut de la nouvelle commande | `payment_au/banktransfer/order_status` | Tous |
| Paiement des pays applicables | `payment_au/banktransfer/allowspecific` | Tous |
| Paiement de pays spécifiques | `payment_au/banktransfer/specificcountry` | Tous |
| Instructions | `payment_au/banktransfer/instructions` | Tous |
| Nombre total minimum de commandes | `payment_au/banktransfer/min_order_total` | Tous |
| Nombre total maximal de commandes | `payment_au/banktransfer/max_order_total` | Tous |
| Ordre de tri | `payment_au/banktransfer/sort_order` | Tous |
| Activé | `payment_au/checkmo/active` | Tous |
| Titre | `payment_au/checkmo/title` | Tous |
| Statut de la nouvelle commande | `payment_au/checkmo/order_status` | Tous |
| Paiement des pays applicables | `payment_au/checkmo/allowspecific` | Tous |
| Paiement de pays spécifiques | `payment_au/checkmo/specificcountry` | Tous |
| Rendre un chèque payable à | `payment_au/checkmo/payable_to` | Tous |
| Envoyer la vérification à | `payment_au/checkmo/mailing_address` | Tous |
| Nombre total minimum de commandes | `payment_au/checkmo/min_order_total` | Tous |
| Nombre total maximal de commandes | `payment_au/checkmo/max_order_total` | Tous |
| Ordre de tri | `payment_au/checkmo/sort_order` | Tous |
| Activé | `payment_au/purchaseorder/active` | Tous |
| Titre | `payment_au/purchaseorder/title` | Tous |
| Statut de la nouvelle commande | `payment_au/purchaseorder/order_status` | Tous |
| Paiement des pays applicables | `payment_au/purchaseorder/allowspecific` | Tous |
| Paiement de pays spécifiques | `payment_au/purchaseorder/specificcountry` | Tous |
| Nombre total minimum de commandes | `payment_au/purchaseorder/min_order_total` | Tous |
| Nombre total maximal de commandes | `payment_au/purchaseorder/max_order_total` | Tous |
| Ordre de tri | `payment_au/purchaseorder/sort_order` | Tous |
| Activé | `payment_au/authorizenet_directpost/active` | Tous |
| Action de paiement | `payment_au/authorizenet_directpost/payment_action` | Tous |
| Titre | `payment_au/authorizenet_directpost/title` | Tous |
| Statut de la nouvelle commande | `payment_au/authorizenet_directpost/order_status` | Tous |
| Devise acceptée | `payment_au/authorizenet_directpost/currency` | Tous |
| Déboguer | `payment_au/authorizenet_directpost/debug` | Tous |
| Types de carte de crédit | `payment_au/authorizenet_directpost/cctypes` | Tous |
| Vérification de carte de crédit | `payment_au/authorizenet_directpost/useccv` | Tous |
| Paiement des pays applicables | `payment_au/authorizenet_directpost/allowspecific` | Tous |
| Paiement de pays spécifiques | `payment_au/authorizenet_directpost/specificcountry` | Tous |
| Nombre total minimum de commandes | `payment_au/authorizenet_directpost/min_order_total` | Tous |
| Nombre total maximal de commandes | `payment_au/authorizenet_directpost/max_order_total` | Tous |
| Ordre de tri | `payment_au/authorizenet_directpost/sort_order` | Tous |
| Activé | `payment_au/cybersource/active` | Commerce Enterprise uniquement |
| Action de paiement | `payment_au/cybersource/payment_action` | Commerce Enterprise uniquement |
| Titre | `payment_au/cybersource/title` | Commerce Enterprise uniquement |
| Identifiant du commerçant | `payment_au/cybersource/merchant_id` | Commerce Enterprise uniquement \| ![chiffré](/help/assets/configuration/cloud-enc.png) |
| Identifiant du profil | `payment_au/cybersource/profile_id` | Commerce Enterprise uniquement \| ![chiffré](/help/assets/configuration/cloud-enc.png) |
| Statut de la nouvelle commande | `payment_au/cybersource/order_status` | Commerce Enterprise uniquement |
| Déboguer | `payment_au/cybersource/debug` | Commerce Enterprise uniquement |
| Types de carte de crédit | `payment_au/cybersource/cctypes` | Commerce Enterprise uniquement |
| Paiement des pays applicables | `payment_au/cybersource/allowspecific` | Commerce Enterprise uniquement |
| Paiement de pays spécifiques | `payment_au/cybersource/specificcountry` | Commerce Enterprise uniquement |
| Nombre total minimum de commandes | `payment_au/cybersource/min_order_total` | Commerce Enterprise uniquement |
| Nombre total maximal de commandes | `payment_au/cybersource/max_order_total` | Commerce Enterprise uniquement |
| Ordre de tri | `payment_au/cybersource/sort_order` | Commerce Enterprise uniquement |
| Activé | `payment_au/worldpay/active` | Commerce Enterprise uniquement |
| Titre | `payment_au/worldpay/title` | Commerce Enterprise uniquement |
| ID d’installation | `payment_au/worldpay/installation_id` | Commerce Enterprise uniquement |
| Autoriser À Modifier Les Coordonnées | `payment_au/worldpay/fix_contact` | Commerce Enterprise uniquement |
| Masquer les coordonnées | `payment_au/worldpay/hide_contact` | Commerce Enterprise uniquement |
| Champs de signature | `payment_au/worldpay/signature_fields` | Commerce Enterprise uniquement |
| Déboguer | `payment_au/worldpay/debug` | Commerce Enterprise uniquement |
| Mode Test | `payment_au/worldpay/sandbox_flag` | Commerce Enterprise uniquement |
| Action de paiement pour le test | `payment_au/worldpay/test_action` | Commerce Enterprise uniquement |
| Action de paiement | `payment_au/worldpay/payment_action` | Commerce Enterprise uniquement |
| Paiement Des Pays Applicables | `payment_au/worldpay/allowspecific` | Commerce Enterprise uniquement |
| Paiement De Pays Spécifiques | `payment_au/worldpay/specificcountry` | Commerce Enterprise uniquement |
| Définir le statut de la commande sur Fraude suspectée pour CVV | `payment_au/worldpay/cvv_fraud_case` | Commerce Enterprise uniquement |
| Définir le statut de la commande sur Fraude suspectée pour le code postal AVS | `payment_au/worldpay/avs_fraud_case` | Commerce Enterprise uniquement |
| Ordre de tri | `payment_au/worldpay/sort_order` | Commerce Enterprise uniquement |
| Activé | `payment_au/eway/active` | Commerce Enterprise uniquement |
| Type de connexion | `payment_au/eway/connection_type` | Commerce Enterprise uniquement |
| Titre | `payment_au/eway/title` | Commerce Enterprise uniquement |
| Action de paiement | `payment_au/eway/payment_action` | Commerce Enterprise uniquement |
| Déboguer | `payment_au/eway/debug` | Commerce Enterprise uniquement |
| Types de carte de crédit | `payment_au/eway/cctypes` | Commerce Enterprise uniquement |
| Paiement des pays applicables | `payment_au/eway/allowspecific` | Commerce Enterprise uniquement |
| Paiement de pays spécifiques | `payment_au/eway/specificcountry` | Commerce Enterprise uniquement |
| Ordre de tri | `payment_au/eway/sort_order` | Commerce Enterprise uniquement |
| Récupération planifiée | `payment_ca/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | Tous |
| Style des pages marchandes PayPal | `payment_ca/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | Tous |
| Récupération planifiée | `payment_ca/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | Tous |
| Style des pages marchandes PayPal | `payment_ca/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | Tous |
| Activer cette solution | `payment/paypal_payment_pro/active` | Tous |
| Paramètres de carte de crédit | `payment_ca/paypal_payment_gateways/wpp_ca/settings_paypal_payflow/heading_cc` | Tous |
| Rejeter la transaction si : | `payment_ca/paypal_payment_gateways/wpp_ca/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_avs_check/heading_avs_settings` | Tous |
| Récupération planifiée | `payment_ca/paypal_payment_gateways/wpp_ca/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_schedule` | Tous |
| Paramètres de carte de crédit | `payment_ca/paypal_payment_gateways/paypal_payflowpro_ca/settings_paypal_payflow/heading_cc` | Tous |
| Rejeter la transaction si : | `payment_ca/paypal_payment_gateways/paypal_payflowpro_ca/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_avs_check/heading_avs_settings` | Tous |
| Récupération planifiée | `payment_ca/paypal_payment_gateways/paypal_payflowpro_ca/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_schedule` | Tous |
| Récupération planifiée | `payment_ca/paypal_payment_gateways/payflow_link_ca/settings_payflow_link/settings_payflow_link_advanced/payflow_link_settlement_report/heading_schedule` | Tous |
| Style des pages marchandes PayPal | `payment_ca/paypal_payment_gateways/payflow_link_ca/settings_payflow_link/settings_payflow_link_advanced/payflow_link_frontend/paypal_pages` | Tous |
| Activé | `payment_ca/free/active` | Tous |
| Titre | `payment_ca/free/title` | Tous |
| Statut de la nouvelle commande | `payment_ca/free/order_status` | Tous |
| Facturer Automatiquement Tous Les Articles | `payment_ca/free/payment_action` | Tous |
| Paiement des pays applicables | `payment_ca/free/allowspecific` | Tous |
| Paiement de pays spécifiques | `payment_ca/free/specificcountry` | Tous |
| Ordre de tri | `payment_ca/free/sort_order` | Tous |
| Activé | `payment_ca/cashondelivery/active` | Tous |
| Titre | `payment_ca/cashondelivery/title` | Tous |
| Statut de la nouvelle commande | `payment_ca/cashondelivery/order_status` | Tous |
| Paiement des pays applicables | `payment_ca/cashondelivery/allowspecific` | Tous |
| Paiement de pays spécifiques | `payment_ca/cashondelivery/specificcountry` | Tous |
| Instructions | `payment_ca/cashondelivery/instructions` | Tous |
| Nombre total minimum de commandes | `payment_ca/cashondelivery/min_order_total` | Tous |
| Nombre total maximal de commandes | `payment_ca/cashondelivery/max_order_total` | Tous |
| Ordre de tri | `payment_ca/cashondelivery/sort_order` | Tous |
| Activé | `payment_ca/banktransfer/active` | Tous |
| Titre | `payment_ca/banktransfer/title` | Tous |
| Statut de la nouvelle commande | `payment_ca/banktransfer/order_status` | Tous |
| Paiement des pays applicables | `payment_ca/banktransfer/allowspecific` | Tous |
| Paiement de pays spécifiques | `payment_ca/banktransfer/specificcountry` | Tous |
| Instructions | `payment_ca/banktransfer/instructions` | Tous |
| Nombre total minimum de commandes | `payment_ca/banktransfer/min_order_total` | Tous |
| Nombre total maximal de commandes | `payment_ca/banktransfer/max_order_total` | Tous |
| Ordre de tri | `payment_ca/banktransfer/sort_order` | Tous |
| Activé | `payment_ca/checkmo/active` | Tous |
| Titre | `payment_ca/checkmo/title` | Tous |
| Statut de la nouvelle commande | `payment_ca/checkmo/order_status` | Tous |
| Paiement des pays applicables | `payment_ca/checkmo/allowspecific` | Tous |
| Paiement de pays spécifiques | `payment_ca/checkmo/specificcountry` | Tous |
| Nombre total minimum de commandes | `payment_ca/checkmo/min_order_total` | Tous |
| Nombre total maximal de commandes | `payment_ca/checkmo/max_order_total` | Tous |
| Ordre de tri | `payment_ca/checkmo/sort_order` | Tous |
| Activé | `payment_ca/purchaseorder/active` | Tous |
| Titre | `payment_ca/purchaseorder/title` | Tous |
| Statut de la nouvelle commande | `payment_ca/purchaseorder/order_status` | Tous |
| Paiement des pays applicables | `payment_ca/purchaseorder/allowspecific` | Tous |
| Paiement de pays spécifiques | `payment_ca/purchaseorder/specificcountry` | Tous |
| Nombre total minimum de commandes | `payment_ca/purchaseorder/min_order_total` | Tous |
| Nombre total maximal de commandes | `payment_ca/purchaseorder/max_order_total` | Tous |
| Ordre de tri | `payment_ca/purchaseorder/sort_order` | Tous |
| Activé | `payment_ca/authorizenet_directpost/active` | Tous |
| Action de paiement | `payment_ca/authorizenet_directpost/payment_action` | Tous |
| Titre | `payment_ca/authorizenet_directpost/title` | Tous |
| Devise acceptée | `payment_ca/authorizenet_directpost/currency` | Tous |
| Déboguer | `payment_ca/authorizenet_directpost/debug` | Tous |
| Types de carte de crédit | `payment_ca/authorizenet_directpost/cctypes` | Tous |
| Vérification de carte de crédit | `payment_ca/authorizenet_directpost/useccv` | Tous |
| Paiement des pays applicables | `payment_ca/authorizenet_directpost/allowspecific` | Tous |
| Paiement de pays spécifiques | `payment_ca/authorizenet_directpost/specificcountry` | Tous |
| Nombre total minimum de commandes | `payment_ca/authorizenet_directpost/min_order_total` | Tous |
| Nombre total maximal de commandes | `payment_ca/authorizenet_directpost/max_order_total` | Tous |
| Ordre de tri | `payment_ca/authorizenet_directpost/sort_order` | Tous |
| Activé | `payment_ca/cybersource/active` | Commerce Enterprise uniquement |
| Action de paiement | `payment_ca/cybersource/payment_action` | Commerce Enterprise uniquement |
| Titre | `payment_ca/cybersource/title` | Commerce Enterprise uniquement |
| Déboguer | `payment_ca/cybersource/debug` | Commerce Enterprise uniquement |
| Types de carte de crédit | `payment_ca/cybersource/cctypes` | Commerce Enterprise uniquement |
| Paiement des pays applicables | `payment_ca/cybersource/allowspecific` | Commerce Enterprise uniquement |
| Paiement de pays spécifiques | `payment_ca/cybersource/specificcountry` | Commerce Enterprise uniquement |
| Nombre total minimum de commandes | `payment_ca/cybersource/min_order_total` | Commerce Enterprise uniquement |
| Nombre total maximal de commandes | `payment_ca/cybersource/max_order_total` | Commerce Enterprise uniquement |
| Ordre de tri | `payment_ca/cybersource/sort_order` | Commerce Enterprise uniquement |
| Activé | `payment_ca/worldpay/active` | Commerce Enterprise uniquement |
| Titre | `payment_ca/worldpay/title` | Commerce Enterprise uniquement |
| Autoriser À Modifier Les Coordonnées | `payment_ca/worldpay/fix_contact` | Commerce Enterprise uniquement |
| Masquer les coordonnées | `payment_ca/worldpay/hide_contact` | Commerce Enterprise uniquement |
| Champs de signature | `payment_ca/worldpay/signature_fields` | Commerce Enterprise uniquement |
| Déboguer | `payment_ca/worldpay/debug` | Commerce Enterprise uniquement |
| Action de paiement pour le test | `payment_ca/worldpay/test_action` | Commerce Enterprise uniquement |
| Action de paiement | `payment_ca/worldpay/payment_action` | Commerce Enterprise uniquement |
| Paiement Des Pays Applicables | `payment_ca/worldpay/allowspecific` | Commerce Enterprise uniquement |
| Paiement De Pays Spécifiques | `payment_ca/worldpay/specificcountry` | Commerce Enterprise uniquement |
| Définir le statut de la commande sur Fraude suspectée pour CVV | `payment_ca/worldpay/cvv_fraud_case` | Commerce Enterprise uniquement |
| Définir le statut de la commande sur Fraude suspectée pour le code postal AVS | `payment_ca/worldpay/avs_fraud_case` | Commerce Enterprise uniquement |
| Ordre de tri | `payment_ca/worldpay/sort_order` | Commerce Enterprise uniquement |
| Activé | `payment_ca/eway/active` | Commerce Enterprise uniquement |
| Type de connexion | `payment_ca/eway/connection_type` | Commerce Enterprise uniquement |
| Titre | `payment_ca/eway/title` | Commerce Enterprise uniquement |
| Action de paiement | `payment_ca/eway/payment_action` | Commerce Enterprise uniquement |
| Déboguer | `payment_ca/eway/debug` | Commerce Enterprise uniquement |
| Types de carte de crédit | `payment_ca/eway/cctypes` | Commerce Enterprise uniquement |
| Paiement des pays applicables | `payment_ca/eway/allowspecific` | Commerce Enterprise uniquement |
| Paiement de pays spécifiques | `payment_ca/eway/specificcountry` | Commerce Enterprise uniquement |
| Ordre de tri | `payment_ca/eway/sort_order` | Commerce Enterprise uniquement |
| Récupération planifiée | `payment_other/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | Tous |
| Style des pages marchandes PayPal | `payment_other/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | Tous |
| Récupération planifiée | `payment_other/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | Tous |
| Style des pages marchandes PayPal | `payment_other/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | Tous |
| Activé | `payment_other/free/active` | Tous |
| Titre | `payment_other/free/title` | Tous |
| Statut de la nouvelle commande | `payment_other/free/order_status` | Tous |
| Facturer Automatiquement Tous Les Articles | `payment_other/free/payment_action` | Tous |
| Paiement des pays applicables | `payment_other/free/allowspecific` | Tous |
| Paiement de pays spécifiques | `payment_other/free/specificcountry` | Tous |
| Ordre de tri | `payment_other/free/sort_order` | Tous |
| Activé | `payment_other/cashondelivery/active` | Tous |
| Titre | `payment_other/cashondelivery/title` | Tous |
| Statut de la nouvelle commande | `payment_other/cashondelivery/order_status` | Tous |
| Paiement des pays applicables | `payment_other/cashondelivery/allowspecific` | Tous |
| Paiement de pays spécifiques | `payment_other/cashondelivery/specificcountry` | Tous |
| Instructions | `payment_other/cashondelivery/instructions` | Tous |
| Nombre total minimum de commandes | `payment_other/cashondelivery/min_order_total` | Tous |
| Nombre total maximal de commandes | `payment_other/cashondelivery/max_order_total` | Tous |
| Ordre de tri | `payment_other/cashondelivery/sort_order` | Tous |
| Activé | `payment_other/banktransfer/active` | Tous |
| Titre | `payment_other/banktransfer/title` | Tous |
| Statut de la nouvelle commande | `payment_other/banktransfer/order_status` | Tous |
| Paiement des pays applicables | `payment_other/banktransfer/allowspecific` | Tous |
| Paiement de pays spécifiques | `payment_other/banktransfer/specificcountry` | Tous |
| Instructions | `payment_other/banktransfer/instructions` | Tous |
| Nombre total minimum de commandes | `payment_other/banktransfer/min_order_total` | Tous |
| Nombre total maximal de commandes | `payment_other/banktransfer/max_order_total` | Tous |
| Ordre de tri | `payment_other/banktransfer/sort_order` | Tous |
| Activé | `payment_other/checkmo/active` | Tous |
| Titre | `payment_other/checkmo/title` | Tous |
| Statut de la nouvelle commande | `payment_other/checkmo/order_status` | Tous |
| Paiement des pays applicables | `payment_other/checkmo/allowspecific` | Tous |
| Paiement de pays spécifiques | `payment_other/checkmo/specificcountry` | Tous |
| Nombre total minimum de commandes | `payment_other/checkmo/min_order_total` | Tous |
| Nombre total maximal de commandes | `payment_other/checkmo/max_order_total` | Tous |
| Ordre de tri | `payment_other/checkmo/sort_order` | Tous |
| Activé | `payment_other/purchaseorder/active` | Tous |
| Titre | `payment_other/purchaseorder/title` | Tous |
| Statut de la nouvelle commande | `payment_other/purchaseorder/order_status` | Tous |
| Paiement des pays applicables | `payment_other/purchaseorder/allowspecific` | Tous |
| Paiement de pays spécifiques | `payment_other/purchaseorder/specificcountry` | Tous |
| Nombre total minimum de commandes | `payment_other/purchaseorder/min_order_total` | Tous |
| Nombre total maximal de commandes | `payment_other/purchaseorder/max_order_total` | Tous |
| Ordre de tri | `payment_other/purchaseorder/sort_order` | Tous |
| Activé | `payment_other/authorizenet_directpost/active` | Tous |
| Action de paiement | `payment_other/authorizenet_directpost/payment_action` | Tous |
| Titre | `payment_other/authorizenet_directpost/title` | Tous |
| Devise acceptée | `payment_other/authorizenet_directpost/currency` | Tous |
| Déboguer | `payment_other/authorizenet_directpost/debug` | Tous |
| Envoyer un e-mail au client | `payment_other/authorizenet_directpost/email_customer` | Tous |
| Types de carte de crédit | `payment_other/authorizenet_directpost/cctypes` | Tous |
| Vérification de carte de crédit | `payment_other/authorizenet_directpost/useccv` | Tous |
| Paiement des pays applicables | `payment_other/authorizenet_directpost/allowspecific` | Tous |
| Paiement de pays spécifiques | `payment_other/authorizenet_directpost/specificcountry` | Tous |
| Nombre total minimum de commandes | `payment_other/authorizenet_directpost/min_order_total` | Tous |
| Nombre total maximal de commandes | `payment_other/authorizenet_directpost/max_order_total` | Tous |
| Ordre de tri | `payment_other/authorizenet_directpost/sort_order` | Tous |
| Activé | `payment_other/cybersource/active` | Commerce Enterprise uniquement |
| Action de paiement | `payment_other/cybersource/payment_action` | Commerce Enterprise uniquement |
| Titre | `payment_other/cybersource/title` | Commerce Enterprise uniquement |
| Déboguer | `payment_other/cybersource/debug` | Commerce Enterprise uniquement |
| Types de carte de crédit | `payment_other/cybersource/cctypes` | Commerce Enterprise uniquement |
| Paiement des pays applicables | `payment_other/cybersource/allowspecific` | Commerce Enterprise uniquement |
| Paiement de pays spécifiques | `payment_other/cybersource/specificcountry` | Commerce Enterprise uniquement |
| Nombre total minimum de commandes | `payment_other/cybersource/min_order_total` | Commerce Enterprise uniquement |
| Nombre total maximal de commandes | `payment_other/cybersource/max_order_total` | Commerce Enterprise uniquement |
| Ordre de tri | `payment_other/cybersource/sort_order` | Commerce Enterprise uniquement |
| Activé | `payment_other/worldpay/active` | Commerce Enterprise uniquement |
| Titre | `payment_other/worldpay/title` | Commerce Enterprise uniquement |
| Autoriser À Modifier Les Coordonnées | `payment_other/worldpay/fix_contact` | Commerce Enterprise uniquement |
| Masquer les coordonnées | `payment_other/worldpay/hide_contact` | Commerce Enterprise uniquement |
| Champs de signature | `payment_other/worldpay/signature_fields` | Commerce Enterprise uniquement |
| Déboguer | `payment_other/worldpay/debug` | Commerce Enterprise uniquement |
| Action de paiement pour le test | `payment_other/worldpay/test_action` | Commerce Enterprise uniquement |
| Action de paiement | `payment_other/worldpay/payment_action` | Commerce Enterprise uniquement |
| Paiement Des Pays Applicables | `payment_other/worldpay/allowspecific` | Commerce Enterprise uniquement |
| Paiement De Pays Spécifiques | `payment_other/worldpay/specificcountry` | Commerce Enterprise uniquement |
| Définir le statut de la commande sur Fraude suspectée pour CVV | `payment_other/worldpay/cvv_fraud_case` | Commerce Enterprise uniquement |
| Définir le statut de la commande sur Fraude suspectée pour le code postal AVS | `payment_other/worldpay/avs_fraud_case` | Commerce Enterprise uniquement |
| Ordre de tri | `payment_other/worldpay/sort_order` | Commerce Enterprise uniquement |
| Activé | `payment_other/eway/active` | Commerce Enterprise uniquement |
| Type de connexion | `payment_other/eway/connection_type` | Commerce Enterprise uniquement |
| Titre | `payment_other/eway/title` | Commerce Enterprise uniquement |
| Action de paiement | `payment_other/eway/payment_action` | Commerce Enterprise uniquement |
| Déboguer | `payment_other/eway/debug` | Commerce Enterprise uniquement |
| Types de carte de crédit | `payment_other/eway/cctypes` | Commerce Enterprise uniquement |
| Paiement des pays applicables | `payment_other/eway/allowspecific` | Commerce Enterprise uniquement |
| Paiement de pays spécifiques | `payment_other/eway/specificcountry` | Commerce Enterprise uniquement |
| Ordre de tri | `payment_other/eway/sort_order` | Commerce Enterprise uniquement |
| Récupération planifiée | `payment_de/paypal_payment_solutions/express_checkout_de/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | Tous |
| Style des pages marchandes PayPal | `payment_de/paypal_payment_solutions/express_checkout_de/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | Tous |
| Activé | `payment_de/checkmo/active` | Tous |
| Titre | `payment_de/checkmo/title` | Tous |
| Statut de la nouvelle commande | `payment_de/checkmo/order_status` | Tous |
| Paiement des pays applicables | `payment_de/checkmo/allowspecific` | Tous |
| Paiement de pays spécifiques | `payment_de/checkmo/specificcountry` | Tous |
| Nombre total minimum de commandes | `payment_de/checkmo/min_order_total` | Tous |
| Nombre total maximal de commandes | `payment_de/checkmo/max_order_total` | Tous |
| Ordre de tri | `payment_de/checkmo/sort_order` | Tous |
| Activé | `payment_de/banktransfer/active` | Tous |
| Titre | `payment_de/banktransfer/title` | Tous |
| Statut de la nouvelle commande | `payment_de/banktransfer/order_status` | Tous |
| Paiement des pays applicables | `payment_de/banktransfer/allowspecific` | Tous |
| Paiement de pays spécifiques | `payment_de/banktransfer/specificcountry` | Tous |
| Instructions | `payment_de/banktransfer/instructions` | Tous |
| Nombre total minimum de commandes | `payment_de/banktransfer/min_order_total` | Tous |
| Nombre total maximal de commandes | `payment_de/banktransfer/max_order_total` | Tous |
| Ordre de tri | `payment_de/banktransfer/sort_order` | Tous |
| Activé | `payment_de/cashondelivery/active` | Tous |
| Titre | `payment_de/cashondelivery/title` | Tous |
| Statut de la nouvelle commande | `payment_de/cashondelivery/order_status` | Tous |
| Paiement des pays applicables | `payment_de/cashondelivery/allowspecific` | Tous |
| Paiement de pays spécifiques | `payment_de/cashondelivery/specificcountry` | Tous |
| Instructions | `payment_de/cashondelivery/instructions` | Tous |
| Nombre total minimum de commandes | `payment_de/cashondelivery/min_order_total` | Tous |
| Nombre total maximal de commandes | `payment_de/cashondelivery/max_order_total` | Tous |
| Ordre de tri | `payment_de/cashondelivery/sort_order` | Tous |
| Activé | `payment_de/free/active` | Tous |
| Titre | `payment_de/free/title` | Tous |
| Statut de la nouvelle commande | `payment_de/free/order_status` | Tous |
| Facturer Automatiquement Tous Les Articles | `payment_de/free/payment_action` | Tous |
| Paiement des pays applicables | `payment_de/free/allowspecific` | Tous |
| Paiement de pays spécifiques | `payment_de/free/specificcountry` | Tous |
| Ordre de tri | `payment_de/free/sort_order` | Tous |
| Activé | `payment_de/purchaseorder/active` | Tous |
| Titre | `payment_de/purchaseorder/title` | Tous |
| Statut de la nouvelle commande | `payment_de/purchaseorder/order_status` | Tous |
| Paiement des pays applicables | `payment_de/purchaseorder/allowspecific` | Tous |
| Paiement de pays spécifiques | `payment_de/purchaseorder/specificcountry` | Tous |
| Nombre total minimum de commandes | `payment_de/purchaseorder/min_order_total` | Tous |
| Nombre total maximal de commandes | `payment_de/purchaseorder/max_order_total` | Tous |
| Ordre de tri | `payment_de/purchaseorder/sort_order` | Tous |
| Activé | `payment_de/cybersource/active` | Commerce Enterprise uniquement |
| Action de paiement | `payment_de/cybersource/payment_action` | Commerce Enterprise uniquement |
| Titre | `payment_de/cybersource/title` | Commerce Enterprise uniquement |
| Statut de la nouvelle commande | `payment_de/cybersource/order_status` | Commerce Enterprise uniquement |
| Déboguer | `payment_de/cybersource/debug` | Commerce Enterprise uniquement |
| Types de carte de crédit | `payment_de/cybersource/cctypes` | Commerce Enterprise uniquement |
| Paiement des pays applicables | `payment_de/cybersource/allowspecific` | Commerce Enterprise uniquement |
| Paiement de pays spécifiques | `payment_de/cybersource/specificcountry` | Commerce Enterprise uniquement |
| Nombre total minimum de commandes | `payment_de/cybersource/min_order_total` | Commerce Enterprise uniquement |
| Nombre total maximal de commandes | `payment_de/cybersource/max_order_total` | Commerce Enterprise uniquement |
| Ordre de tri | `payment_de/cybersource/sort_order` | Commerce Enterprise uniquement |
| Activé | `payment_de/authorizenet_directpost/active` | Tous |
| Action de paiement | `payment_de/authorizenet_directpost/payment_action` | Tous |
| Titre | `payment_de/authorizenet_directpost/title` | Tous |
| Statut de la nouvelle commande | `payment_de/authorizenet_directpost/order_status` | Tous |
| Devise acceptée | `payment_de/authorizenet_directpost/currency` | Tous |
| Déboguer | `payment_de/authorizenet_directpost/debug` | Tous |
| Types de carte de crédit | `payment_de/authorizenet_directpost/cctypes` | Tous |
| Vérification de carte de crédit | `payment_de/authorizenet_directpost/useccv` | Tous |
| Paiement des pays applicables | `payment_de/authorizenet_directpost/allowspecific` | Tous |
| Paiement de pays spécifiques | `payment_de/authorizenet_directpost/specificcountry` | Tous |
| Nombre total minimum de commandes | `payment_de/authorizenet_directpost/min_order_total` | Tous |
| Nombre total maximal de commandes | `payment_de/authorizenet_directpost/max_order_total` | Tous |
| Ordre de tri | `payment_de/authorizenet_directpost/sort_order` | Tous |
| Activé | `payment_de/worldpay/active` | Commerce Enterprise uniquement |
| Titre | `payment_de/worldpay/title` | Commerce Enterprise uniquement |
| Autoriser À Modifier Les Coordonnées | `payment_de/worldpay/fix_contact` | Commerce Enterprise uniquement |
| Masquer les coordonnées | `payment_de/worldpay/hide_contact` | Commerce Enterprise uniquement |
| Champs de signature | `payment_de/worldpay/signature_fields` | Commerce Enterprise uniquement |
| Mode Test | `payment_de/worldpay/sandbox_flag` | Commerce Enterprise uniquement |
| Action de paiement pour le test | `payment_de/worldpay/test_action` | Commerce Enterprise uniquement |
| Action de paiement | `payment_de/worldpay/payment_action` | Commerce Enterprise uniquement |
| Paiement Des Pays Applicables | `payment_de/worldpay/allowspecific` | Commerce Enterprise uniquement |
| Paiement De Pays Spécifiques | `payment_de/worldpay/specificcountry` | Commerce Enterprise uniquement |
| Définir le statut de la commande sur Fraude suspectée pour CVV | `payment_de/worldpay/cvv_fraud_case` | Commerce Enterprise uniquement |
| Définir le statut de la commande sur Fraude suspectée pour le code postal AVS | `payment_de/worldpay/avs_fraud_case` | Commerce Enterprise uniquement |
| Ordre de tri | `payment_de/worldpay/sort_order` | Commerce Enterprise uniquement |
| Activé | `payment_de/eway/active` | Commerce Enterprise uniquement |
| Type de connexion | `payment_de/eway/connection_type` | Commerce Enterprise uniquement |
| Titre | `payment_de/eway/title` | Commerce Enterprise uniquement |
| Action de paiement | `payment_de/eway/payment_action` | Commerce Enterprise uniquement |
| Déboguer | `payment_de/eway/debug` | Commerce Enterprise uniquement |
| Types de carte de crédit | `payment_de/eway/cctypes` | Commerce Enterprise uniquement |
| Paiement des pays applicables | `payment_de/eway/allowspecific` | Commerce Enterprise uniquement |
| Paiement de pays spécifiques | `payment_de/eway/specificcountry` | Commerce Enterprise uniquement |
| Ordre de tri | `payment_de/eway/sort_order` | Commerce Enterprise uniquement |
| Récupération planifiée | `payment_gb/paypal_alternative_payment_methods/express_checkout_gb/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | Tous |
| Style des pages marchandes PayPal | `payment_gb/paypal_alternative_payment_methods/express_checkout_gb/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | Tous |
| Récupération planifiée | `payment_gb/paypal_group_all_in_one/payments_pro_hosted_solution_with_express_checkout/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_schedule` | Tous |
| Style des pages marchandes PayPal | `payment_gb/paypal_group_all_in_one/payments_pro_hosted_solution_with_express_checkout/pphs_settings/pphs_settings_advanced/pphs_frontend/paypal_pages` | Tous |
| Récupération planifiée | `payment_gb/paypal_group_all_in_one/wps_express/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | Tous |
| Style des pages marchandes PayPal | `payment_gb/paypal_group_all_in_one/wps_express/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | Tous |
| Activé | `payment_gb/checkmo/active` | Tous |
| Titre | `payment_gb/checkmo/title` | Tous |
| Statut de la nouvelle commande | `payment_gb/checkmo/order_status` | Tous |
| Paiement des pays applicables | `payment_gb/checkmo/allowspecific` | Tous |
| Paiement de pays spécifiques | `payment_gb/checkmo/specificcountry` | Tous |
| Rendre un chèque payable à | `payment_gb/checkmo/payable_to` | Tous |
| Nombre total minimum de commandes | `payment_gb/checkmo/min_order_total` | Tous |
| Nombre total maximal de commandes | `payment_gb/checkmo/max_order_total` | Tous |
| Ordre de tri | `payment_gb/checkmo/sort_order` | Tous |
| Activé | `payment_gb/banktransfer/active` | Tous |
| Titre | `payment_gb/banktransfer/title` | Tous |
| Statut de la nouvelle commande | `payment_gb/banktransfer/order_status` | Tous |
| Paiement des pays applicables | `payment_gb/banktransfer/allowspecific` | Tous |
| Paiement de pays spécifiques | `payment_gb/banktransfer/specificcountry` | Tous |
| Instructions | `payment_gb/banktransfer/instructions` | Tous |
| Nombre total minimum de commandes | `payment_gb/banktransfer/min_order_total` | Tous |
| Nombre total maximal de commandes | `payment_gb/banktransfer/max_order_total` | Tous |
| Ordre de tri | `payment_gb/banktransfer/sort_order` | Tous |
| Activé | `payment_gb/cashondelivery/active` | Tous |
| Titre | `payment_gb/cashondelivery/title` | Tous |
| Statut de la nouvelle commande | `payment_gb/cashondelivery/order_status` | Tous |
| Paiement des pays applicables | `payment_gb/cashondelivery/allowspecific` | Tous |
| Paiement de pays spécifiques | `payment_gb/cashondelivery/specificcountry` | Tous |
| Instructions | `payment_gb/cashondelivery/instructions` | Tous |
| Nombre total minimum de commandes | `payment_gb/cashondelivery/min_order_total` | Tous |
| Nombre total maximal de commandes | `payment_gb/cashondelivery/max_order_total` | Tous |
| Ordre de tri | `payment_gb/cashondelivery/sort_order` | Tous |
| Activé | `payment_gb/free/active` | Tous |
| Titre | `payment_gb/free/title` | Tous |
| Statut de la nouvelle commande | `payment_gb/free/order_status` | Tous |
| Facturer Automatiquement Tous Les Articles | `payment_gb/free/payment_action` | Tous |
| Paiement des pays applicables | `payment_gb/free/allowspecific` | Tous |
| Paiement de pays spécifiques | `payment_gb/free/specificcountry` | Tous |
| Ordre de tri | `payment_gb/free/sort_order` | Tous |
| Activé | `payment_gb/purchaseorder/active` | Tous |
| Titre | `payment_gb/purchaseorder/title` | Tous |
| Statut de la nouvelle commande | `payment_gb/purchaseorder/order_status` | Tous |
| Paiement des pays applicables | `payment_gb/purchaseorder/allowspecific` | Tous |
| Paiement de pays spécifiques | `payment_gb/purchaseorder/specificcountry` | Tous |
| Nombre total minimum de commandes | `payment_gb/purchaseorder/min_order_total` | Tous |
| Nombre total maximal de commandes | `payment_gb/purchaseorder/max_order_total` | Tous |
| Ordre de tri | `payment_gb/purchaseorder/sort_order` | Tous |
| Activé | `payment_gb/cybersource/active` | Commerce Enterprise uniquement |
| Action de paiement | `payment_gb/cybersource/payment_action` | Commerce Enterprise uniquement |
| Titre | `payment_gb/cybersource/title` | Commerce Enterprise uniquement |
| Statut de la nouvelle commande | `payment_gb/cybersource/order_status` | Commerce Enterprise uniquement |
| Déboguer | `payment_gb/cybersource/debug` | Commerce Enterprise uniquement |
| Types de carte de crédit | `payment_gb/cybersource/cctypes` | Commerce Enterprise uniquement |
| Paiement des pays applicables | `payment_gb/cybersource/allowspecific` | Commerce Enterprise uniquement |
| Paiement de pays spécifiques | `payment_gb/cybersource/specificcountry` | Commerce Enterprise uniquement |
| Nombre total minimum de commandes | `payment_gb/cybersource/min_order_total` | Commerce Enterprise uniquement |
| Nombre total maximal de commandes | `payment_gb/cybersource/max_order_total` | Commerce Enterprise uniquement |
| Ordre de tri | `payment_gb/cybersource/sort_order` | Commerce Enterprise uniquement |
| Activé | `payment_gb/authorizenet_directpost/active` | Tous |
| Action de paiement | `payment_gb/authorizenet_directpost/payment_action` | Tous |
| Titre | `payment_gb/authorizenet_directpost/title` | Tous |
| Statut de la nouvelle commande | `payment_gb/authorizenet_directpost/order_status` | Tous |
| Devise acceptée | `payment_gb/authorizenet_directpost/currency` | Tous |
| Déboguer | `payment_gb/authorizenet_directpost/debug` | Tous |
| Types de carte de crédit | `payment_gb/authorizenet_directpost/cctypes` | Tous |
| Vérification de carte de crédit | `payment_gb/authorizenet_directpost/useccv` | Tous |
| Paiement des pays applicables | `payment_gb/authorizenet_directpost/allowspecific` | Tous |
| Paiement de pays spécifiques | `payment_gb/authorizenet_directpost/specificcountry` | Tous |
| Nombre total minimum de commandes | `payment_gb/authorizenet_directpost/min_order_total` | Tous |
| Nombre total maximal de commandes | `payment_gb/authorizenet_directpost/max_order_total` | Tous |
| Ordre de tri | `payment_gb/authorizenet_directpost/sort_order` | Tous |
| Activé | `payment_gb/worldpay/active` | Commerce Enterprise uniquement |
| Titre | `payment_gb/worldpay/title` | Commerce Enterprise uniquement |
| Secret MD5 pour les transactions | `payment_gb/worldpay/md5_secret` | Commerce Enterprise uniquement |
| Autoriser À Modifier Les Coordonnées | `payment_gb/worldpay/fix_contact` | Commerce Enterprise uniquement |
| Masquer les coordonnées | `payment_gb/worldpay/hide_contact` | Commerce Enterprise uniquement |
| Champs de signature | `payment_gb/worldpay/signature_fields` | Commerce Enterprise uniquement |
| Déboguer | `payment_gb/worldpay/debug` | Commerce Enterprise uniquement |
| Action de paiement pour le test | `payment_gb/worldpay/test_action` | Commerce Enterprise uniquement |
| Action de paiement | `payment_gb/worldpay/payment_action` | Commerce Enterprise uniquement |
| Paiement Des Pays Applicables | `payment_gb/worldpay/allowspecific` | Commerce Enterprise uniquement |
| Paiement De Pays Spécifiques | `payment_gb/worldpay/specificcountry` | Commerce Enterprise uniquement |
| Définir le statut de la commande sur Fraude suspectée pour CVV | `payment_gb/worldpay/cvv_fraud_case` | Commerce Enterprise uniquement |
| Définir le statut de la commande sur Fraude suspectée pour le code postal AVS | `payment_gb/worldpay/avs_fraud_case` | Commerce Enterprise uniquement |
| Ordre de tri | `payment_gb/worldpay/sort_order` | Commerce Enterprise uniquement |
| Activé | `payment_gb/eway/active` | Commerce Enterprise uniquement |
| Type de connexion | `payment_gb/eway/connection_type` | Commerce Enterprise uniquement |
| Titre | `payment_gb/eway/title` | Commerce Enterprise uniquement |
| Action de paiement | `payment_gb/eway/payment_action` | Commerce Enterprise uniquement |
| Déboguer | `payment_gb/eway/debug` | Commerce Enterprise uniquement |
| Types de carte de crédit | `payment_gb/eway/cctypes` | Commerce Enterprise uniquement |
| Paiement des pays applicables | `payment_gb/eway/allowspecific` | Commerce Enterprise uniquement |
| Paiement de pays spécifiques | `payment_gb/eway/specificcountry` | Commerce Enterprise uniquement |
| Ordre de tri | `payment_gb/eway/sort_order` | Commerce Enterprise uniquement |
| Récupération planifiée | `payment_us/paypal_alternative_payment_methods/express_checkout_us/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | Tous |
| Style des pages marchandes PayPal | `payment_us/paypal_alternative_payment_methods/express_checkout_us/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | Tous |
| Récupération planifiée | `payment_us/paypal_group_all_in_one/payflow_advanced/settings_payments_advanced/settings_payments_advanced_advanced/settlement_report/heading_schedule` | Tous |
| Style des pages marchandes PayPal | `payment_us/paypal_group_all_in_one/payflow_advanced/settings_payments_advanced/settings_payments_advanced_advanced/frontend/paypal_pages` | Tous |
| Paramètres de carte de crédit | `payment_us/paypal_group_all_in_one/wpp_usuk/settings_paypal_payflow/heading_cc` | Tous |
| Rejeter la transaction si : | `payment_us/paypal_group_all_in_one/wpp_usuk/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_avs_check/heading_avs_settings` | Tous |
| Récupération planifiée | `payment_us/paypal_group_all_in_one/wpp_usuk/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_schedule` | Tous |
| Style des pages marchandes PayPal | `payment_us/paypal_group_all_in_one/wpp_usuk/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_frontend/paypal_pages` | Tous |
| Activer le crédit PayPal | `payment/wps_express_bml/active` | Tous |
| Récupération planifiée | `payment_us/paypal_group_all_in_one/wps_express/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | Tous |
| Style des pages marchandes PayPal | `payment_us/paypal_group_all_in_one/wps_express/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | Tous |
| Paramètres de carte de crédit | `payment_us/paypal_payment_gateways/paypal_payflowpro_with_express_checkout/settings_paypal_payflow/heading_cc` | Tous |
| Rejeter la transaction si : | `payment_us/paypal_payment_gateways/paypal_payflowpro_with_express_checkout/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_avs_check/heading_avs_settings` | Tous |
| Récupération planifiée | `payment_us/paypal_payment_gateways/paypal_payflowpro_with_express_checkout/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_schedule` | Tous |
| Style des pages marchandes PayPal | `payment_us/paypal_payment_gateways/paypal_payflowpro_with_express_checkout/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_frontend/paypal_pages` | Tous |
| Récupération planifiée | `payment_us/paypal_payment_gateways/payflow_link_us/settings_payflow_link/settings_payflow_link_advanced/payflow_link_settlement_report/heading_schedule` | Tous |
| Style des pages marchandes PayPal | `payment_us/paypal_payment_gateways/payflow_link_us/settings_payflow_link/settings_payflow_link_advanced/payflow_link_frontend/paypal_pages` | Tous |
| Activé | `payment_us/free/active` | Tous |
| Titre | `payment_us/free/title` | Tous |
| Statut de la nouvelle commande | `payment_us/free/order_status` | Tous |
| Facturer Automatiquement Tous Les Articles | `payment_us/free/payment_action` | Tous |
| Paiement des pays applicables | `payment_us/free/allowspecific` | Tous |
| Paiement de pays spécifiques | `payment_us/free/specificcountry` | Tous |
| Ordre de tri | `payment_us/free/sort_order` | Tous |
| Activé | `payment_us/cashondelivery/active` | Tous |
| Titre | `payment_us/cashondelivery/title` | Tous |
| Statut de la nouvelle commande | `payment_us/cashondelivery/order_status` | Tous |
| Paiement des pays applicables | `payment_us/cashondelivery/allowspecific` | Tous |
| Paiement de pays spécifiques | `payment_us/cashondelivery/specificcountry` | Tous |
| Instructions | `payment_us/cashondelivery/instructions` | Tous |
| Nombre total minimum de commandes | `payment_us/cashondelivery/min_order_total` | Tous |
| Nombre total maximal de commandes | `payment_us/cashondelivery/max_order_total` | Tous |
| Ordre de tri | `payment_us/cashondelivery/sort_order` | Tous |
| Activé | `payment_us/banktransfer/active` | Tous |
| Titre | `payment_us/banktransfer/title` | Tous |
| Statut de la nouvelle commande | `payment_us/banktransfer/order_status` | Tous |
| Paiement des pays applicables | `payment_us/banktransfer/allowspecific` | Tous |
| Paiement de pays spécifiques | `payment_us/banktransfer/specificcountry` | Tous |
| Instructions | `payment_us/banktransfer/instructions` | Tous |
| Nombre total minimum de commandes | `payment_us/banktransfer/min_order_total` | Tous |
| Nombre total maximal de commandes | `payment_us/banktransfer/max_order_total` | Tous |
| Ordre de tri | `payment_us/banktransfer/sort_order` | Tous |
| Activé | `payment_us/checkmo/active` | Tous |
| Titre | `payment_us/checkmo/title` | Tous |
| Statut de la nouvelle commande | `payment_us/checkmo/order_status` | Tous |
| Paiement des pays applicables | `payment_us/checkmo/allowspecific` | Tous |
| Paiement de pays spécifiques | `payment_us/checkmo/specificcountry` | Tous |
| Rendre un chèque payable à | `payment_us/checkmo/payable_to` | Tous |
| Nombre total minimum de commandes | `payment_us/checkmo/min_order_total` | Tous |
| Nombre total maximal de commandes | `payment_us/checkmo/max_order_total` | Tous |
| Ordre de tri | `payment_us/checkmo/sort_order` | Tous |
| Activé | `payment_us/purchaseorder/active` | Tous |
| Titre | `payment_us/purchaseorder/title` | Tous |
| Statut de la nouvelle commande | `payment_us/purchaseorder/order_status` | Tous |
| Paiement des pays applicables | `payment_us/purchaseorder/allowspecific` | Tous |
| Paiement de pays spécifiques | `payment_us/purchaseorder/specificcountry` | Tous |
| Nombre total minimum de commandes | `payment_us/purchaseorder/min_order_total` | Tous |
| Nombre total maximal de commandes | `payment_us/purchaseorder/max_order_total` | Tous |
| Ordre de tri | `payment_us/purchaseorder/sort_order` | Tous |
| Activé | `payment_us/authorizenet_directpost/active` | Tous |
| Action de paiement | `payment_us/authorizenet_directpost/payment_action` | Tous |
| Titre | `payment_us/authorizenet_directpost/title` | Tous |
| Statut de la nouvelle commande | `payment_us/authorizenet_directpost/order_status` | Tous |
| Devise acceptée | `payment_us/authorizenet_directpost/currency` | Tous |
| Déboguer | `payment_us/authorizenet_directpost/debug` | Tous |
| Types de carte de crédit | `payment_us/authorizenet_directpost/cctypes` | Tous |
| Vérification de carte de crédit | `payment_us/authorizenet_directpost/useccv` | Tous |
| Paiement des pays applicables | `payment_us/authorizenet_directpost/allowspecific` | Tous |
| Paiement de pays spécifiques | `payment_us/authorizenet_directpost/specificcountry` | Tous |
| Nombre total minimum de commandes | `payment_us/authorizenet_directpost/min_order_total` | Tous |
| Nombre total maximal de commandes | `payment_us/authorizenet_directpost/max_order_total` | Tous |
| Ordre de tri | `payment_us/authorizenet_directpost/sort_order` | Tous |
| Activé | `payment_us/cybersource/active` | Commerce Enterprise uniquement |
| Action de paiement | `payment_us/cybersource/payment_action` | Commerce Enterprise uniquement |
| Titre | `payment_us/cybersource/title` | Commerce Enterprise uniquement |
| Statut de la nouvelle commande | `payment_us/cybersource/order_status` | Commerce Enterprise uniquement |
| Déboguer | `payment_us/cybersource/debug` | Commerce Enterprise uniquement |
| Types de carte de crédit | `payment_us/cybersource/cctypes` | Commerce Enterprise uniquement |
| Paiement des pays applicables | `payment_us/cybersource/allowspecific` | Commerce Enterprise uniquement |
| Paiement de pays spécifiques | `payment_us/cybersource/specificcountry` | Commerce Enterprise uniquement |
| Nombre total minimum de commandes | `payment_us/cybersource/min_order_total` | Commerce Enterprise uniquement |
| Nombre total maximal de commandes | `payment_us/cybersource/max_order_total` | Commerce Enterprise uniquement |
| Ordre de tri | `payment_us/cybersource/sort_order` | Commerce Enterprise uniquement |
| Activé | `payment_us/worldpay/active` | Commerce Enterprise uniquement |
| Titre | `payment_us/worldpay/title` | Commerce Enterprise uniquement |
| Autoriser À Modifier Les Coordonnées | `payment_us/worldpay/fix_contact` | Commerce Enterprise uniquement |
| Masquer les coordonnées | `payment_us/worldpay/hide_contact` | Commerce Enterprise uniquement |
| Champs de signature | `payment_us/worldpay/signature_fields` | Commerce Enterprise uniquement |
| Déboguer | `payment_us/worldpay/debug` | Commerce Enterprise uniquement |
| Action de paiement pour le test | `payment_us/worldpay/test_action` | Commerce Enterprise uniquement |
| Action de paiement | `payment_us/worldpay/payment_action` | Commerce Enterprise uniquement |
| Paiement Des Pays Applicables | `payment_us/worldpay/allowspecific` | Commerce Enterprise uniquement |
| Paiement De Pays Spécifiques | `payment_us/worldpay/specificcountry` | Commerce Enterprise uniquement |
| Définir le statut de la commande sur Fraude suspectée pour CVV | `payment_us/worldpay/cvv_fraud_case` | Commerce Enterprise uniquement |
| Définir le statut de la commande sur Fraude suspectée pour le code postal AVS | `payment_us/worldpay/avs_fraud_case` | Commerce Enterprise uniquement |
| Ordre de tri | `payment_us/worldpay/sort_order` | Commerce Enterprise uniquement |
| Activé | `payment_us/eway/active` | Commerce Enterprise uniquement |
| Type de connexion | `payment_us/eway/connection_type` | Commerce Enterprise uniquement |
| Titre | `payment_us/eway/title` | Commerce Enterprise uniquement |
| Action de paiement | `payment_us/eway/payment_action` | Commerce Enterprise uniquement |
| Déboguer | `payment_us/eway/debug` | Commerce Enterprise uniquement |
| Types de carte de crédit | `payment_us/eway/cctypes` | Commerce Enterprise uniquement |
| Paiement des pays applicables | `payment_us/eway/allowspecific` | Commerce Enterprise uniquement |
| Paiement de pays spécifiques | `payment_us/eway/specificcountry` | Commerce Enterprise uniquement |
| Ordre de tri | `payment_us/eway/sort_order` | |

{style="table-layout:auto"}
