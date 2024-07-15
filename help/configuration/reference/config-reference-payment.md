---
title: Référence des chemins de configuration des paiements
description: Consultez la liste des valeurs configurables des modes de paiement.
feature: Configuration, Payments
exl-id: f3e356aa-7262-4d99-9ed4-d77cbd93708c
source-git-commit: 16e9396f19693436dfc7bdac78d84624a78f0c21
workflow-type: tm+mt
source-wordcount: '4100'
ht-degree: 0%

---

# Référence des chemins de configuration des paiements

Ces valeurs de configuration sont disponibles dans l’Admin de **Magasins** > Paramètres > **Configuration** > **Ventes** > **Méthodes de paiement**.

La commande [`magento app:config:dump`](../cli/export-configuration.md) écrit ces valeurs dans le fichier de configuration partagé, `app/etc/config.php`, qui doit être dans le contrôle source. Pour éventuellement remplacer des paramètres de configuration ou définir des paramètres sensibles, reportez-vous à la section [Utilisation de variables d’environnement pour remplacer les paramètres de configuration](override-config-settings.md#environment-variables). Cette rubrique ne _répertorie pas_ les [ valeurs sensibles et spécifiques au système ](config-reference-sens.md).

Les paramètres sont organisés par mode de paiement.

## Chemins PayPal

| Nom | Chemin de configuration | Commerce uniquement ? | Chiffré ? |
|--------------|--------------|--------------|--------------|
| Activer cette solution | `payment/payflowpro/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activation de l’expérience de passage en caisse contextuelle | `payment/paypal_express/in_context` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activer le crédit PayPal | `payment/payflow_express_bml/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activer le crédit PayPal | `payment/paypal_express_bml/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Affichage | `payment/paypal_express_bml/homepage_display` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Position | `payment/paypal_express_bml/homepage_position` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Taille | `payment/paypal_express_bml/homepage_size` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Affichage | `payment/paypal_express_bml/categorypage_display` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Position | `payment/paypal_express_bml/categorypage_position` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Taille | `payment/paypal_express_bml/categorypage_size` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Affichage | `payment/paypal_express_bml/productpage_display` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Position | `payment/paypal_express_bml/productpage_position` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Taille | `payment/paypal_express_bml/productpage_size` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Affichage | `payment/paypal_express_bml/checkout_display` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Position | `payment/paypal_express_bml/checkout_position` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Taille | `payment/paypal_express_bml/checkout_size` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Afficher sur la page Détails du produit | `payment/payflow_express/visible_on_product` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Afficher sur le panier | `payment/payflow_express/visible_on_cart` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paiement applicable depuis | `payment/payflow_express/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pays Paiement Applicable Depuis | `payment/payflow_express/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activer la vérification SSL | `payment/payflow_express/verify_peer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Transférer les éléments du panier | `payment/payflow_express/line_items_enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ignorer l’étape de révision des commandes | `payment/paypal_express/skip_order_review_step` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Transférer les éléments du panier | `payment/paypal_express/line_items_enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Options d’expédition de transfert | `payment/paypal_express/transfer_shipping_options` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Flavor des boutons de raccourci | `paypal/wpp/button_flavor` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activer le paiement des invités PayPal | `payment/paypal_express/solution_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Exiger l’adresse de facturation du client | `payment/paypal_express/require_billing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Signature d’un contrat de facturation | `payment/paypal_express/allow_ba_signup` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activé | `payment/paypal_billing_agreement/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titre | `payment/paypal_billing_agreement/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordre de tri | `payment/paypal_billing_agreement/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Action de paiement | `payment/paypal_billing_agreement/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paiement applicable depuis | `payment/paypal_billing_agreement/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pays Paiement Applicable Depuis | `payment/paypal_billing_agreement/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activer la vérification SSL | `payment/paypal_billing_agreement/verify_peer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Transférer les éléments du panier | `payment/paypal_billing_agreement/line_items_enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Autoriser dans l’assistant de contrat de facturation | `payment/paypal_billing_agreement/allow_billing_agreement_wizard` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activation de la récupération automatique | `paypal/fetch_reports/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Planning | `paypal/fetch_reports/schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Heure de la journée | `paypal/fetch_reports/time` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Logo du produit PayPal | `paypal/style/logo` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Style de page | `paypal/style/page_style` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| URL de l’image d’en-tête | `paypal/style/paypal_hdrimg` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Couleur d’arrière-plan de l’en-tête | `paypal/style/paypal_hdrbackcolor` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Couleur de bordure de l’en-tête | `paypal/style/paypal_hdrbordercolor` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Couleur d’arrière-plan de page | `paypal/style/paypal_payflowcolor` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activer cette solution | `payment/paypal_express/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Crédit PayPal des commandes de tri | `payment/paypal_express_bml/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titre | `payment/paypal_express/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordre de tri | `payment/paypal_express/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Action de paiement | `payment/paypal_express/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Afficher sur la page Détails du produit | `payment/paypal_express/visible_on_product` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Période d’honneur de l’autorisation (jours) | `payment/paypal_express/authorization_honor_period` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Période valide de la commande (jours) | `payment/paypal_express/order_valid_period` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nombre d’autorisations pour enfants | `payment/paypal_express/child_authorization_number` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Afficher sur le panier | `payment/paypal_express/visible_on_cart` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paiement applicable depuis | `payment/paypal_express/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pays Paiement Applicable Depuis | `payment/paypal_express/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activer la vérification SSL | `payment/paypal_express/verify_peer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Récupération planifiée | `payment_all_paypal/express_checkout/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Style des pages marchandes PayPal | `payment_all_paypal/express_checkout/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## PayPal payment Pro

| Nom | Chemin de configuration | Commerce uniquement ? | Chiffré ? |
|--------------|--------------|--------------|--------------|
| Méthodes d’authentification API | `paypal/wpp/api_authentication` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| API utilise le proxy | `paypal/wpp/use_proxy` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Récupération planifiée | `payment_all_paypal/payments_pro_hosted_solution/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Récupération planifiée | `payment_all_paypal/payments_pro_hosted_solution_without_bml/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Paiements pour la solution hébergée (Royaume-Uni)

Ces options ne sont disponibles que si vous avez choisi le Royaume-Uni comme [ pays commerçant ](../reference/config-reference-sens.md#payment-sensitive-and-system-specific-paths).

| Nom | Chemin de configuration | Commerce uniquement ? | Chiffré ? |
|--------------|--------------|--------------|--------------|
| Activer cette solution | `payment/hosted_pro/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titre | `payment/hosted_pro/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordre de tri | `payment/hosted_pro/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Action de paiement | `payment/hosted_pro/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Afficher le passage en caisse express à l’étape Informations de paiement | `payment/hosted_pro/display_ec` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paiement applicable depuis | `payment/hosted_pro/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pays Paiement Applicable Depuis | `payment/hosted_pro/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activer la vérification SSL | `payment/hosted_pro/verify_peer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## PayPal Payflow Pro

| Nom | Chemin de configuration | Commerce uniquement ? | Chiffré ? |
|--------------|--------------|--------------|--------------|
| Vault activé | `payment/payflowpro_cc_vault/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titre | `payment/payflowpro/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titre du coffre | `payment/payflowpro_cc_vault/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordre de tri | `payment/payflowpro/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Action de paiement | `payment/payflowpro/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Types de carte de crédit autorisés | `payment/payflowpro/cctypes` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paiement applicable depuis | `payment/payflowpro/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pays Paiement Applicable Depuis | `payment/payflowpro/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activer la vérification SSL | `payment/payflowpro/verify_peer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Entrée CVV requise | `payment/payflowpro/useccv` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Rejeter la transaction si : | `payment_all_paypal/paypal_payflowpro/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_avs_check/heading_avs_settings` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| La rue AVS ne correspond pas | `payment/payflowpro/avs_street` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Le code postal AVS ne correspond pas | `payment/payflowpro/avs_zip` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| L’indicateur AVS international ne correspond pas | `payment/payflowpro/avs_international` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Le code de sécurité de carte ne correspond pas | `payment/payflowpro/avs_security_code` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Fournisseur | `payment/payflowpro/vendor` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Utiliser le proxy | `payment/payflowpro/use_proxy` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titre | `payment/payflow_express/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordre de tri | `payment/payflow_express/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Action de paiement | `payment/payflow_express/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Récupération planifiée | `payment_all_paypal/paypal_payflowpro/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Style des pages marchandes PayPal | `payment_all_paypal/payflow_link/settings_payflow_link/settings_payflow_link_advanced/payflow_link_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Partenaire | `payment/payflow_advanced/partner` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Fournisseur | `payment/payflow_advanced/vendor` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Utiliser le proxy | `payment/payflow_advanced/use_proxy` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activer cette solution | `payment/payflow_advanced/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titre | `payment/payflow_advanced/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordre de tri | `payment/payflow_advanced/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Action de paiement | `payment/payflow_advanced/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paiement applicable depuis | `payment/payflow_advanced/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pays Paiement Applicable Depuis | `payment/payflow_advanced/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activer la vérification SSL | `payment/payflow_advanced/verify_peer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Entrée CVV modifiable | `payment/payflow_advanced/csc_editable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Entrée CVV requise | `payment/payflow_advanced/csc_required` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Envoyer la confirmation par courrier électronique | `payment/payflow_advanced/email_confirmation` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Lien de flux de production PayPal

| Nom | Chemin de configuration | Commerce uniquement ? | Chiffré ? |
|--------------|--------------|--------------|--------------|
| Partenaire | `payment/payflow_link/partner` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Fournisseur | `payment/payflow_link/vendor` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activer le lien de flux de production | `payment/payflow_link/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activer le passage en caisse express | `payment/payflow_express/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Crédit PayPal des commandes de tri | `payment/payflow_express_bml/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paiement applicable depuis | `payment/payflow_link/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pays Paiement Applicable Depuis | `payment/payflow_link/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activer la vérification SSL | `payment/payflow_link/verify_peer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Entrée CVV modifiable | `payment/payflow_link/csc_editable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Entrée CVV requise | `payment/payflow_link/csc_required` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Envoyer la confirmation par courrier électronique | `payment/payflow_link/email_confirmation` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Récupération planifiée | `payment_all_paypal/payflow_link/settings_payflow_link/settings_payflow_link_advanced/payflow_link_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titre | `payment/payflow_link/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordre de tri | `payment/payflow_link/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Action de paiement | `payment/payflow_link/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Zéro sous-total chemins de passage en caisse

| Nom | Chemin de configuration | Commerce uniquement ? | Chiffré ? |
|--------------|--------------|--------------|--------------|
| Activé | `payment/free/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titre | `payment/free/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| New Order Status | `payment/free/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Facturer automatiquement tous les éléments | `payment/free/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paiement par les pays applicables | `payment/free/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paiement par pays spécifique | `payment/free/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordre de tri | `payment/free/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Espèces sur les chemins de paiement de diffusion

| Nom | Chemin de configuration | Commerce uniquement ? | Chiffré ? |
|--------------|--------------|--------------|--------------|
| Activé | `payment/cashondelivery/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titre | `payment/cashondelivery/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| New Order Status | `payment/cashondelivery/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paiement par les pays applicables | `payment/cashondelivery/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paiement par pays spécifique | `payment/cashondelivery/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Instructions | `payment/cashondelivery/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de la commande minimale | `payment/cashondelivery/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de la commande maximale | `payment/cashondelivery/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordre de tri | `payment/cashondelivery/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Chemins de paiement de transfert bancaire

| Nom | Chemin de configuration | Commerce uniquement ? | Chiffré ? |
|--------------|--------------|--------------|--------------|
| Activé | `payment/banktransfer/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titre | `payment/banktransfer/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| New Order Status | `payment/banktransfer/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paiement par les pays applicables | `payment/banktransfer/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paiement par pays spécifique | `payment/banktransfer/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Instructions | `payment/banktransfer/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de la commande minimale | `payment/banktransfer/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de la commande maximale | `payment/banktransfer/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordre de tri | `payment/banktransfer/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Vérifier ou passer des commandes

| Nom | Chemin de configuration | Commerce uniquement ? | Chiffré ? |
|--------------|--------------|--------------|--------------|
| Activé | `payment/checkmo/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titre | `payment/checkmo/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| New Order Status | `payment/checkmo/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paiement par les pays applicables | `payment/checkmo/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paiement par pays spécifique | `payment/checkmo/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Rendre le paiement | `payment/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de la commande minimale | `payment/checkmo/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de la commande maximale | `payment/checkmo/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordre de tri | `payment/checkmo/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Chemins des commandes d’achat

| Nom | Chemin de configuration | Commerce uniquement ? | Chiffré ? |
|--------------|--------------|--------------|--------------|
| Activé | `payment/purchaseorder/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titre | `payment/purchaseorder/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| New Order Status | `payment/purchaseorder/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paiement par les pays applicables | `payment/purchaseorder/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paiement par pays spécifique | `payment/purchaseorder/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de la commande minimale | `payment/purchaseorder/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de la commande maximale | `payment/purchaseorder/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordre de tri | `payment/purchaseorder/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Chemins internationaux

>[!INFO]
>
>Les chemins disponibles sont déterminés par votre choix de [Pays commerçant](../reference/config-reference-sens.md#payment-sensitive-and-system-specific-paths).

| Nom | Chemin de configuration | Commerce uniquement ? | Chiffré ? |
|--------------|--------------|--------------|--------------|
| Informations d’identification SFTP | `payment_nz/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Récupération planifiée | `payment_nz/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Style des pages marchandes PayPal | `payment_nz/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activer cette solution | `payment/wps_express/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Récupération planifiée | `payment_nz/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Style des pages marchandes PayPal | `payment_nz/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paramètres de carte de crédit | `payment_nz/paypal_payment_gateways/paypal_payflowpro_nz/settings_paypal_payflow/heading_cc` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Rejeter la transaction si : | `payment_nz/paypal_payment_gateways/paypal_payflowpro_nz/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_avs_check/heading_avs_settings` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Récupération planifiée | `payment_nz/paypal_payment_gateways/paypal_payflowpro_nz/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activé | `payment_nz/free/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titre | `payment_nz/free/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| New Order Status | `payment_nz/free/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Facturer automatiquement tous les éléments | `payment_nz/free/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paiement par les pays applicables | `payment_nz/free/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paiement par pays spécifique | `payment_nz/free/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordre de tri | `payment_nz/free/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activé | `payment_nz/cashondelivery/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titre | `payment_nz/cashondelivery/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| New Order Status | `payment_nz/cashondelivery/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paiement par les pays applicables | `payment_nz/cashondelivery/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paiement par pays spécifique | `payment_nz/cashondelivery/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Instructions | `payment_nz/cashondelivery/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de la commande minimale | `payment_nz/cashondelivery/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de la commande maximale | `payment_nz/cashondelivery/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordre de tri | `payment_nz/cashondelivery/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activé | `payment_nz/banktransfer/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titre | `payment_nz/banktransfer/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| New Order Status | `payment_nz/banktransfer/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paiement par les pays applicables | `payment_nz/banktransfer/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paiement par pays spécifique | `payment_nz/banktransfer/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Instructions | `payment_nz/banktransfer/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de la commande minimale | `payment_nz/banktransfer/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de la commande maximale | `payment_nz/banktransfer/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordre de tri | `payment_nz/banktransfer/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activé | `payment_nz/checkmo/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titre | `payment_nz/checkmo/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| New Order Status | `payment_nz/checkmo/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paiement par les pays applicables | `payment_nz/checkmo/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paiement par pays spécifique | `payment_nz/checkmo/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Rendre le paiement | `payment_nz/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Envoyer la vérification à | `payment_nz/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de la commande minimale | `payment_nz/checkmo/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de la commande maximale | `payment_nz/checkmo/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordre de tri | `payment_nz/checkmo/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activé | `payment_nz/purchaseorder/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titre | `payment_nz/purchaseorder/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| New Order Status | `payment_nz/purchaseorder/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paiement par les pays applicables | `payment_nz/purchaseorder/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paiement par pays spécifique | `payment_nz/purchaseorder/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de la commande minimale | `payment_nz/purchaseorder/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de la commande maximale | `payment_nz/purchaseorder/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordre de tri | `payment_nz/purchaseorder/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activé | `payment_nz/authorizenet_directpost/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Action de paiement | `payment_nz/authorizenet_directpost/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titre | `payment_nz/authorizenet_directpost/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| New Order Status | `payment_nz/authorizenet_directpost/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Devise acceptée | `payment_nz/authorizenet_directpost/currency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Déboguer | `payment_nz/authorizenet_directpost/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Types de carte de crédit | `payment_nz/authorizenet_directpost/cctypes` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Vérification de carte de crédit | `payment_nz/authorizenet_directpost/useccv` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paiement par les pays applicables | `payment_nz/authorizenet_directpost/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paiement par pays spécifique | `payment_nz/authorizenet_directpost/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de la commande minimale | `payment_nz/authorizenet_directpost/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de la commande maximale | `payment_nz/authorizenet_directpost/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordre de tri | `payment_nz/authorizenet_directpost/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activé | `payment_nz/cybersource/active` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Action de paiement | `payment_nz/cybersource/payment_action` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Titre | `payment_nz/cybersource/title` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| New Order Status | `payment_nz/cybersource/order_status` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Déboguer | `payment_nz/cybersource/debug` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Types de carte de crédit | `payment_nz/cybersource/cctypes` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Paiement par les pays applicables | `payment_nz/cybersource/allowspecific` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Paiement par pays spécifique | `payment_nz/cybersource/specificcountry` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Total de la commande minimale | `payment_nz/cybersource/min_order_total` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Total de la commande maximale | `payment_nz/cybersource/max_order_total` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Ordre de tri | `payment_nz/cybersource/sort_order` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Activé | `payment_nz/worldpay/active` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Titre | `payment_nz/worldpay/title` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Autoriser la modification des coordonnées | `payment_nz/worldpay/fix_contact` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Masquer les informations de contact | `payment_nz/worldpay/hide_contact` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Champs de signature | `payment_nz/worldpay/signature_fields` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Déboguer | `payment_nz/worldpay/debug` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Action de paiement pour le test | `payment_nz/worldpay/test_action` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Action de paiement | `payment_nz/worldpay/payment_action` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Paiement Des Pays Applicables | `payment_nz/worldpay/allowspecific` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Paiement De Pays Spécifiques | `payment_nz/worldpay/specificcountry` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Définir l’état de la commande sur Fraude suspectée pour CVV | `payment_nz/worldpay/cvv_fraud_case` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Définir l’état de la commande sur Fraude suspectée pour le code Postcode AVS | `payment_nz/worldpay/avs_fraud_case` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Ordre de tri | `payment_nz/worldpay/sort_order` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Activé | `payment_nz/eway/active` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Type de connexion | `payment_nz/eway/connection_type` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Titre | `payment_nz/eway/title` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Action de paiement | `payment_nz/eway/payment_action` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Déboguer | `payment_nz/eway/debug` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Types de carte de crédit | `payment_nz/eway/cctypes` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Paiement par les pays applicables | `payment_nz/eway/allowspecific` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Paiement par pays spécifique | `payment_nz/eway/specificcountry` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Ordre de tri | `payment_nz/eway/sort_order` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Récupération planifiée | `payment_hk/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Style des pages marchandes PayPal | `payment_hk/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Récupération planifiée | `payment_hk/paypal_group_all_in_one/payments_pro_hosted_solution_hk/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Récupération planifiée | `payment_hk/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Style des pages marchandes PayPal | `payment_hk/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activé | `payment_hk/free/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titre | `payment_hk/free/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| New Order Status | `payment_hk/free/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Facturer automatiquement tous les éléments | `payment_hk/free/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paiement par les pays applicables | `payment_hk/free/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paiement par pays spécifique | `payment_hk/free/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordre de tri | `payment_hk/free/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activé | `payment_hk/cashondelivery/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titre | `payment_hk/cashondelivery/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| New Order Status | `payment_hk/cashondelivery/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paiement par les pays applicables | `payment_hk/cashondelivery/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paiement par pays spécifique | `payment_hk/cashondelivery/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Instructions | `payment_hk/cashondelivery/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de la commande minimale | `payment_hk/cashondelivery/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de la commande maximale | `payment_hk/cashondelivery/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordre de tri | `payment_hk/cashondelivery/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activé | `payment_hk/banktransfer/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titre | `payment_hk/banktransfer/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| New Order Status | `payment_hk/banktransfer/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paiement par les pays applicables | `payment_hk/banktransfer/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paiement par pays spécifique | `payment_hk/banktransfer/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Instructions | `payment_hk/banktransfer/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de la commande minimale | `payment_hk/banktransfer/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de la commande maximale | `payment_hk/banktransfer/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordre de tri | `payment_hk/banktransfer/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activé | `payment_hk/checkmo/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titre | `payment_hk/checkmo/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| New Order Status | `payment_hk/checkmo/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paiement par les pays applicables | `payment_hk/checkmo/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paiement par pays spécifique | `payment_hk/checkmo/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de la commande minimale | `payment_hk/checkmo/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de la commande maximale | `payment_hk/checkmo/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordre de tri | `payment_hk/checkmo/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activé | `payment_hk/purchaseorder/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titre | `payment_hk/purchaseorder/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| New Order Status | `payment_hk/purchaseorder/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paiement par les pays applicables | `payment_hk/purchaseorder/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paiement par pays spécifique | `payment_hk/purchaseorder/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de la commande minimale | `payment_hk/purchaseorder/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de la commande maximale | `payment_hk/purchaseorder/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordre de tri | `payment_hk/purchaseorder/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activé | `payment_hk/authorizenet_directpost/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Action de paiement | `payment_hk/authorizenet_directpost/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titre | `payment_hk/authorizenet_directpost/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| New Order Status | `payment_hk/authorizenet_directpost/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Devise acceptée | `payment_hk/authorizenet_directpost/currency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Déboguer | `payment_hk/authorizenet_directpost/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Types de carte de crédit | `payment_hk/authorizenet_directpost/cctypes` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Vérification de carte de crédit | `payment_hk/authorizenet_directpost/useccv` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paiement par les pays applicables | `payment_hk/authorizenet_directpost/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paiement par pays spécifique | `payment_hk/authorizenet_directpost/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de la commande minimale | `payment_hk/authorizenet_directpost/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de la commande maximale | `payment_hk/authorizenet_directpost/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordre de tri | `payment_hk/authorizenet_directpost/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activé | `payment_hk/cybersource/active` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Action de paiement | `payment_hk/cybersource/payment_action` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Titre | `payment_hk/cybersource/title` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| New Order Status | `payment_hk/cybersource/order_status` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Déboguer | `payment_hk/cybersource/debug` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Types de carte de crédit | `payment_hk/cybersource/cctypes` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Paiement par les pays applicables | `payment_hk/cybersource/allowspecific` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Paiement par pays spécifique | `payment_hk/cybersource/specificcountry` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Total de la commande minimale | `payment_hk/cybersource/min_order_total` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Total de la commande maximale | `payment_hk/cybersource/max_order_total` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Ordre de tri | `payment_hk/cybersource/sort_order` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Activé | `payment_hk/worldpay/active` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Titre | `payment_hk/worldpay/title` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Autoriser la modification des coordonnées | `payment_hk/worldpay/fix_contact` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Masquer les informations de contact | `payment_hk/worldpay/hide_contact` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Déboguer | `payment_hk/worldpay/debug` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Action de paiement pour le test | `payment_hk/worldpay/test_action` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Action de paiement | `payment_hk/worldpay/payment_action` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Paiement Des Pays Applicables | `payment_hk/worldpay/allowspecific` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Paiement De Pays Spécifiques | `payment_hk/worldpay/specificcountry` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Définir l’état de la commande sur Fraude suspectée pour CVV | `payment_hk/worldpay/cvv_fraud_case` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Définir l’état de la commande sur Fraude suspectée pour le code Postcode AVS | `payment_hk/worldpay/avs_fraud_case` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Ordre de tri | `payment_hk/worldpay/sort_order` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Activé | `payment_hk/eway/active` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Type de connexion | `payment_hk/eway/connection_type` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Titre | `payment_hk/eway/title` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Mode sandbox | `payment_hk/eway/sandbox_flag` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Action de paiement | `payment_hk/eway/payment_action` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Déboguer | `payment_hk/eway/debug` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Types de carte de crédit | `payment_hk/eway/cctypes` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Paiement par les pays applicables | `payment_hk/eway/allowspecific` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Paiement par pays spécifique | `payment_hk/eway/specificcountry` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Ordre de tri | `payment_hk/eway/sort_order` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Récupération planifiée | `payment_es/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Style des pages marchandes PayPal | `payment_es/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Récupération planifiée | `payment_es/paypal_group_all_in_one/payments_pro_hosted_solution_es/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Récupération planifiée | `payment_es/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Style des pages marchandes PayPal | `payment_es/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activé | `payment_es/free/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titre | `payment_es/free/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| New Order Status | `payment_es/free/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Facturer automatiquement tous les éléments | `payment_es/free/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paiement par les pays applicables | `payment_es/free/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paiement par pays spécifique | `payment_es/free/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordre de tri | `payment_es/free/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activé | `payment_es/cashondelivery/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titre | `payment_es/cashondelivery/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| New Order Status | `payment_es/cashondelivery/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paiement par les pays applicables | `payment_es/cashondelivery/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paiement par pays spécifique | `payment_es/cashondelivery/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Instructions | `payment_es/cashondelivery/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de la commande minimale | `payment_es/cashondelivery/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de la commande maximale | `payment_es/cashondelivery/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordre de tri | `payment_es/cashondelivery/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activé | `payment_es/banktransfer/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titre | `payment_es/banktransfer/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| New Order Status | `payment_es/banktransfer/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paiement par les pays applicables | `payment_es/banktransfer/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paiement par pays spécifique | `payment_es/banktransfer/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Instructions | `payment_es/banktransfer/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de la commande minimale | `payment_es/banktransfer/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de la commande maximale | `payment_es/banktransfer/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordre de tri | `payment_es/banktransfer/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activé | `payment_es/checkmo/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titre | `payment_es/checkmo/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| New Order Status | `payment_es/checkmo/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paiement par les pays applicables | `payment_es/checkmo/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paiement par pays spécifique | `payment_es/checkmo/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Rendre le paiement | `payment_es/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de la commande minimale | `payment_es/checkmo/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de la commande maximale | `payment_es/checkmo/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordre de tri | `payment_es/checkmo/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activé | `payment_es/purchaseorder/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titre | `payment_es/purchaseorder/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| New Order Status | `payment_es/purchaseorder/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paiement par les pays applicables | `payment_es/purchaseorder/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paiement par pays spécifique | `payment_es/purchaseorder/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de la commande minimale | `payment_es/purchaseorder/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de la commande maximale | `payment_es/purchaseorder/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordre de tri | `payment_es/purchaseorder/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activé | `payment_es/authorizenet_directpost/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Action de paiement | `payment_es/authorizenet_directpost/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titre | `payment_es/authorizenet_directpost/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| New Order Status | `payment_es/authorizenet_directpost/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Devise acceptée | `payment_es/authorizenet_directpost/currency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Déboguer | `payment_es/authorizenet_directpost/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Types de carte de crédit | `payment_es/authorizenet_directpost/cctypes` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Vérification de carte de crédit | `payment_es/authorizenet_directpost/useccv` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paiement par les pays applicables | `payment_es/authorizenet_directpost/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paiement par pays spécifique | `payment_es/authorizenet_directpost/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de la commande minimale | `payment_es/authorizenet_directpost/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de la commande maximale | `payment_es/authorizenet_directpost/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordre de tri | `payment_es/authorizenet_directpost/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activé | `payment_es/cybersource/active` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Action de paiement | `payment_es/cybersource/payment_action` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Titre | `payment_es/cybersource/title` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Identifiant de profil | `payment_es/cybersource/profile_id` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![Encrypted](/help/assets/configuration/cloud-enc.png) |
| New Order Status | `payment_es/cybersource/order_status` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Déboguer | `payment_es/cybersource/debug` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Types de carte de crédit | `payment_es/cybersource/cctypes` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Paiement par les pays applicables | `payment_es/cybersource/allowspecific` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Paiement par pays spécifique | `payment_es/cybersource/specificcountry` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Total de la commande minimale | `payment_es/cybersource/min_order_total` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Total de la commande maximale | `payment_es/cybersource/max_order_total` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Ordre de tri | `payment_es/cybersource/sort_order` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Activé | `payment_es/worldpay/active` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Titre | `payment_es/worldpay/title` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| ID d’installation | `payment_es/worldpay/installation_id` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| ID d’installation d’administrateur distant | `payment_es/worldpay/admin_installation_id` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Autoriser la modification des coordonnées | `payment_es/worldpay/fix_contact` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Masquer les informations de contact | `payment_es/worldpay/hide_contact` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Champs de signature | `payment_es/worldpay/signature_fields` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Mode test | `payment_es/worldpay/sandbox_flag` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Action de paiement pour le test | `payment_es/worldpay/test_action` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Action de paiement | `payment_es/worldpay/payment_action` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Paiement Des Pays Applicables | `payment_es/worldpay/allowspecific` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Paiement De Pays Spécifiques | `payment_es/worldpay/specificcountry` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Définir l’état de la commande sur Fraude suspectée pour CVV | `payment_es/worldpay/cvv_fraud_case` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Définir l’état de la commande sur Fraude suspectée pour le code Postcode AVS | `payment_es/worldpay/avs_fraud_case` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Ordre de tri | `payment_es/worldpay/sort_order` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Activé | `payment_es/eway/active` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Type de connexion | `payment_es/eway/connection_type` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Titre | `payment_es/eway/title` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Action de paiement | `payment_es/eway/payment_action` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Déboguer | `payment_es/eway/debug` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Types de carte de crédit | `payment_es/eway/cctypes` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Paiement par les pays applicables | `payment_es/eway/allowspecific` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Paiement par pays spécifique | `payment_es/eway/specificcountry` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Ordre de tri | `payment_es/eway/sort_order` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Récupération planifiée | `payment_it/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Style des pages marchandes PayPal | `payment_it/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Récupération planifiée | `payment_it/paypal_group_all_in_one/payments_pro_hosted_solution_it/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Récupération planifiée | `payment_it/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Style des pages marchandes PayPal | `payment_it/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activé | `payment_it/free/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titre | `payment_it/free/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| New Order Status | `payment_it/free/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Facturer automatiquement tous les éléments | `payment_it/free/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paiement par les pays applicables | `payment_it/free/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paiement par pays spécifique | `payment_it/free/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordre de tri | `payment_it/free/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activé | `payment_it/cashondelivery/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titre | `payment_it/cashondelivery/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| New Order Status | `payment_it/cashondelivery/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paiement par les pays applicables | `payment_it/cashondelivery/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paiement par pays spécifique | `payment_it/cashondelivery/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Instructions | `payment_it/cashondelivery/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de la commande minimale | `payment_it/cashondelivery/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de la commande maximale | `payment_it/cashondelivery/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordre de tri | `payment_it/cashondelivery/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activé | `payment_it/banktransfer/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titre | `payment_it/banktransfer/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| New Order Status | `payment_it/banktransfer/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paiement par les pays applicables | `payment_it/banktransfer/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paiement par pays spécifique | `payment_it/banktransfer/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Instructions | `payment_it/banktransfer/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de la commande minimale | `payment_it/banktransfer/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de la commande maximale | `payment_it/banktransfer/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordre de tri | `payment_it/banktransfer/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activé | `payment_it/checkmo/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titre | `payment_it/checkmo/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| New Order Status | `payment_it/checkmo/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paiement par les pays applicables | `payment_it/checkmo/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paiement par pays spécifique | `payment_it/checkmo/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de la commande minimale | `payment_it/checkmo/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de la commande maximale | `payment_it/checkmo/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordre de tri | `payment_it/checkmo/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activé | `payment_it/purchaseorder/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titre | `payment_it/purchaseorder/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| New Order Status | `payment_it/purchaseorder/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paiement par les pays applicables | `payment_it/purchaseorder/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paiement par pays spécifique | `payment_it/purchaseorder/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de la commande minimale | `payment_it/purchaseorder/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de la commande maximale | `payment_it/purchaseorder/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordre de tri | `payment_it/purchaseorder/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activé | `payment_it/authorizenet_directpost/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Action de paiement | `payment_it/authorizenet_directpost/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titre | `payment_it/authorizenet_directpost/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| New Order Status | `payment_it/authorizenet_directpost/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Devise acceptée | `payment_it/authorizenet_directpost/currency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Déboguer | `payment_it/authorizenet_directpost/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Types de carte de crédit | `payment_it/authorizenet_directpost/cctypes` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Vérification de carte de crédit | `payment_it/authorizenet_directpost/useccv` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paiement par les pays applicables | `payment_it/authorizenet_directpost/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paiement par pays spécifique | `payment_it/authorizenet_directpost/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de la commande minimale | `payment_it/authorizenet_directpost/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de la commande maximale | `payment_it/authorizenet_directpost/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordre de tri | `payment_it/authorizenet_directpost/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activé | `payment_it/cybersource/active` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Action de paiement | `payment_it/cybersource/payment_action` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Titre | `payment_it/cybersource/title` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| New Order Status | `payment_it/cybersource/order_status` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Déboguer | `payment_it/cybersource/debug` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Types de carte de crédit | `payment_it/cybersource/cctypes` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Paiement par les pays applicables | `payment_it/cybersource/allowspecific` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Paiement par pays spécifique | `payment_it/cybersource/specificcountry` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Total de la commande minimale | `payment_it/cybersource/min_order_total` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Total de la commande maximale | `payment_it/cybersource/max_order_total` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Ordre de tri | `payment_it/cybersource/sort_order` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Activé | `payment_it/worldpay/active` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Titre | `payment_it/worldpay/title` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Autoriser la modification des coordonnées | `payment_it/worldpay/fix_contact` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Masquer les informations de contact | `payment_it/worldpay/hide_contact` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Champs de signature | `payment_it/worldpay/signature_fields` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Déboguer | `payment_it/worldpay/debug` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Action de paiement pour le test | `payment_it/worldpay/test_action` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Action de paiement | `payment_it/worldpay/payment_action` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Paiement Des Pays Applicables | `payment_it/worldpay/allowspecific` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Paiement De Pays Spécifiques | `payment_it/worldpay/specificcountry` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Définir l’état de la commande sur Fraude suspectée pour CVV | `payment_it/worldpay/cvv_fraud_case` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Définir l’état de la commande sur Fraude suspectée pour le code Postcode AVS | `payment_it/worldpay/avs_fraud_case` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Ordre de tri | `payment_it/worldpay/sort_order` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Activé | `payment_it/eway/active` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Type de connexion | `payment_it/eway/connection_type` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Titre | `payment_it/eway/title` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Action de paiement | `payment_it/eway/payment_action` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Déboguer | `payment_it/eway/debug` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Types de carte de crédit | `payment_it/eway/cctypes` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Paiement par les pays applicables | `payment_it/eway/allowspecific` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Paiement par pays spécifique | `payment_it/eway/specificcountry` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Ordre de tri | `payment_it/eway/sort_order` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Récupération planifiée | `payment_fr/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Style des pages marchandes PayPal | `payment_fr/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Récupération planifiée | `payment_fr/paypal_group_all_in_one/payments_pro_hosted_solution_fr/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Récupération planifiée | `payment_fr/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Style des pages marchandes PayPal | `payment_fr/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activé | `payment_fr/free/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titre | `payment_fr/free/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| New Order Status | `payment_fr/free/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Facturer automatiquement tous les éléments | `payment_fr/free/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paiement par les pays applicables | `payment_fr/free/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paiement par pays spécifique | `payment_fr/free/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordre de tri | `payment_fr/free/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activé | `payment_fr/cashondelivery/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titre | `payment_fr/cashondelivery/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| New Order Status | `payment_fr/cashondelivery/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paiement par les pays applicables | `payment_fr/cashondelivery/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paiement par pays spécifique | `payment_fr/cashondelivery/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Instructions | `payment_fr/cashondelivery/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de la commande minimale | `payment_fr/cashondelivery/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de la commande maximale | `payment_fr/cashondelivery/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordre de tri | `payment_fr/cashondelivery/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activé | `payment_fr/banktransfer/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titre | `payment_fr/banktransfer/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| New Order Status | `payment_fr/banktransfer/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paiement par les pays applicables | `payment_fr/banktransfer/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paiement par pays spécifique | `payment_fr/banktransfer/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Instructions | `payment_fr/banktransfer/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de la commande minimale | `payment_fr/banktransfer/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de la commande maximale | `payment_fr/banktransfer/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordre de tri | `payment_fr/banktransfer/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activé | `payment_fr/checkmo/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titre | `payment_fr/checkmo/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| New Order Status | `payment_fr/checkmo/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paiement par les pays applicables | `payment_fr/checkmo/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paiement par pays spécifique | `payment_fr/checkmo/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de la commande minimale | `payment_fr/checkmo/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de la commande maximale | `payment_fr/checkmo/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordre de tri | `payment_fr/checkmo/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activé | `payment_fr/purchaseorder/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titre | `payment_fr/purchaseorder/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| New Order Status | `payment_fr/purchaseorder/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paiement par les pays applicables | `payment_fr/purchaseorder/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paiement par pays spécifique | `payment_fr/purchaseorder/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de la commande minimale | `payment_fr/purchaseorder/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de la commande maximale | `payment_fr/purchaseorder/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordre de tri | `payment_fr/purchaseorder/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activé | `payment_fr/authorizenet_directpost/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Action de paiement | `payment_fr/authorizenet_directpost/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titre | `payment_fr/authorizenet_directpost/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| New Order Status | `payment_fr/authorizenet_directpost/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Devise acceptée | `payment_fr/authorizenet_directpost/currency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Déboguer | `payment_fr/authorizenet_directpost/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Types de carte de crédit | `payment_fr/authorizenet_directpost/cctypes` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Vérification de carte de crédit | `payment_fr/authorizenet_directpost/useccv` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paiement par les pays applicables | `payment_fr/authorizenet_directpost/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paiement par pays spécifique | `payment_fr/authorizenet_directpost/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de la commande minimale | `payment_fr/authorizenet_directpost/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de la commande maximale | `payment_fr/authorizenet_directpost/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordre de tri | `payment_fr/authorizenet_directpost/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activé | `payment_fr/cybersource/active` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Action de paiement | `payment_fr/cybersource/payment_action` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Titre | `payment_fr/cybersource/title` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| New Order Status | `payment_fr/cybersource/order_status` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Déboguer | `payment_fr/cybersource/debug` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Types de carte de crédit | `payment_fr/cybersource/cctypes` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Paiement par les pays applicables | `payment_fr/cybersource/allowspecific` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Paiement par pays spécifique | `payment_fr/cybersource/specificcountry` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Total de la commande minimale | `payment_fr/cybersource/min_order_total` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Total de la commande maximale | `payment_fr/cybersource/max_order_total` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Ordre de tri | `payment_fr/cybersource/sort_order` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Activé | `payment_fr/worldpay/active` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Titre | `payment_fr/worldpay/title` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Autoriser la modification des coordonnées | `payment_fr/worldpay/fix_contact` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Masquer les informations de contact | `payment_fr/worldpay/hide_contact` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Déboguer | `payment_fr/worldpay/debug` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Action de paiement pour le test | `payment_fr/worldpay/test_action` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Action de paiement | `payment_fr/worldpay/payment_action` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Paiement Des Pays Applicables | `payment_fr/worldpay/allowspecific` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Paiement De Pays Spécifiques | `payment_fr/worldpay/specificcountry` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Définir l’état de la commande sur Fraude suspectée pour CVV | `payment_fr/worldpay/cvv_fraud_case` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Définir l’état de la commande sur Fraude suspectée pour le code Postcode AVS | `payment_fr/worldpay/avs_fraud_case` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Ordre de tri | `payment_fr/worldpay/sort_order` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Activé | `payment_fr/eway/active` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Type de connexion | `payment_fr/eway/connection_type` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Titre | `payment_fr/eway/title` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Action de paiement | `payment_fr/eway/payment_action` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Déboguer | `payment_fr/eway/debug` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Types de carte de crédit | `payment_fr/eway/cctypes` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Paiement par les pays applicables | `payment_fr/eway/allowspecific` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Paiement par pays spécifique | `payment_fr/eway/specificcountry` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Ordre de tri | `payment_fr/eway/sort_order` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Récupération planifiée | `payment_jp/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Style des pages marchandes PayPal | `payment_jp/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Récupération planifiée | `payment_jp/paypal_group_all_in_one/payments_pro_hosted_solution_jp/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Récupération planifiée | `payment_jp/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Style des pages marchandes PayPal | `payment_jp/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activé | `payment_jp/free/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titre | `payment_jp/free/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| New Order Status | `payment_jp/free/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Facturer automatiquement tous les éléments | `payment_jp/free/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paiement par les pays applicables | `payment_jp/free/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paiement par pays spécifique | `payment_jp/free/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordre de tri | `payment_jp/free/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activé | `payment_jp/cashondelivery/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titre | `payment_jp/cashondelivery/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| New Order Status | `payment_jp/cashondelivery/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paiement par les pays applicables | `payment_jp/cashondelivery/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paiement par pays spécifique | `payment_jp/cashondelivery/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Instructions | `payment_jp/cashondelivery/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de la commande minimale | `payment_jp/cashondelivery/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de la commande maximale | `payment_jp/cashondelivery/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordre de tri | `payment_jp/cashondelivery/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activé | `payment_jp/banktransfer/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titre | `payment_jp/banktransfer/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| New Order Status | `payment_jp/banktransfer/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paiement par les pays applicables | `payment_jp/banktransfer/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paiement par pays spécifique | `payment_jp/banktransfer/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Instructions | `payment_jp/banktransfer/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de la commande minimale | `payment_jp/banktransfer/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de la commande maximale | `payment_jp/banktransfer/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordre de tri | `payment_jp/banktransfer/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activé | `payment_jp/checkmo/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titre | `payment_jp/checkmo/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| New Order Status | `payment_jp/checkmo/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paiement par les pays applicables | `payment_jp/checkmo/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paiement par pays spécifique | `payment_jp/checkmo/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de la commande minimale | `payment_jp/checkmo/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de la commande maximale | `payment_jp/checkmo/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordre de tri | `payment_jp/checkmo/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activé | `payment_jp/purchaseorder/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titre | `payment_jp/purchaseorder/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| New Order Status | `payment_jp/purchaseorder/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paiement par les pays applicables | `payment_jp/purchaseorder/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paiement par pays spécifique | `payment_jp/purchaseorder/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de la commande minimale | `payment_jp/purchaseorder/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de la commande maximale | `payment_jp/purchaseorder/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordre de tri | `payment_jp/purchaseorder/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activé | `payment_jp/authorizenet_directpost/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Action de paiement | `payment_jp/authorizenet_directpost/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titre | `payment_jp/authorizenet_directpost/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| New Order Status | `payment_jp/authorizenet_directpost/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Devise acceptée | `payment_jp/authorizenet_directpost/currency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Déboguer | `payment_jp/authorizenet_directpost/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Types de carte de crédit | `payment_jp/authorizenet_directpost/cctypes` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Vérification de carte de crédit | `payment_jp/authorizenet_directpost/useccv` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paiement par les pays applicables | `payment_jp/authorizenet_directpost/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paiement par pays spécifique | `payment_jp/authorizenet_directpost/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de la commande minimale | `payment_jp/authorizenet_directpost/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de la commande maximale | `payment_jp/authorizenet_directpost/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordre de tri | `payment_jp/authorizenet_directpost/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activé | `payment_jp/cybersource/active` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Action de paiement | `payment_jp/cybersource/payment_action` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Titre | `payment_jp/cybersource/title` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Déboguer | `payment_jp/cybersource/debug` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Types de carte de crédit | `payment_jp/cybersource/cctypes` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Paiement par les pays applicables | `payment_jp/cybersource/allowspecific` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Paiement par pays spécifique | `payment_jp/cybersource/specificcountry` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Total de la commande minimale | `payment_jp/cybersource/min_order_total` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Total de la commande maximale | `payment_jp/cybersource/max_order_total` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Ordre de tri | `payment_jp/cybersource/sort_order` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Activé | `payment_jp/worldpay/active` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Titre | `payment_jp/worldpay/title` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Autoriser la modification des coordonnées | `payment_jp/worldpay/fix_contact` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Masquer les informations de contact | `payment_jp/worldpay/hide_contact` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Déboguer | `payment_jp/worldpay/debug` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Action de paiement pour le test | `payment_jp/worldpay/test_action` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Action de paiement | `payment_jp/worldpay/payment_action` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Paiement Des Pays Applicables | `payment_jp/worldpay/allowspecific` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Paiement De Pays Spécifiques | `payment_jp/worldpay/specificcountry` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Définir l’état de la commande sur Fraude suspectée pour CVV | `payment_jp/worldpay/cvv_fraud_case` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Définir l’état de la commande sur Fraude suspectée pour le code Postcode AVS | `payment_jp/worldpay/avs_fraud_case` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Ordre de tri | `payment_jp/worldpay/sort_order` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Activé | `payment_jp/eway/active` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Type de connexion | `payment_jp/eway/connection_type` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Titre | `payment_jp/eway/title` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Action de paiement | `payment_jp/eway/payment_action` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Déboguer | `payment_jp/eway/debug` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Types de carte de crédit | `payment_jp/eway/cctypes` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Paiement par les pays applicables | `payment_jp/eway/allowspecific` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Paiement par pays spécifique | `payment_jp/eway/specificcountry` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Ordre de tri | `payment_jp/eway/sort_order` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Récupération planifiée | `payment_au/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Style des pages marchandes PayPal | `payment_au/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Récupération planifiée | `payment_au/paypal_group_all_in_one/payments_pro_hosted_solution_au/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Récupération planifiée | `payment_au/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Style des pages marchandes PayPal | `payment_au/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paramètres de carte de crédit | `payment_au/paypal_payment_gateways/paypal_payflowpro_au/settings_paypal_payflow/heading_cc` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Rejeter la transaction si : | `payment_au/paypal_payment_gateways/paypal_payflowpro_au/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_avs_check/heading_avs_settings` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Récupération planifiée | `payment_au/paypal_payment_gateways/paypal_payflowpro_au/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activé | `payment_au/free/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titre | `payment_au/free/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| New Order Status | `payment_au/free/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Facturer automatiquement tous les éléments | `payment_au/free/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paiement par les pays applicables | `payment_au/free/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paiement par pays spécifique | `payment_au/free/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordre de tri | `payment_au/free/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activé | `payment_au/cashondelivery/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titre | `payment_au/cashondelivery/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| New Order Status | `payment_au/cashondelivery/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paiement par les pays applicables | `payment_au/cashondelivery/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paiement par pays spécifique | `payment_au/cashondelivery/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Instructions | `payment_au/cashondelivery/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de la commande minimale | `payment_au/cashondelivery/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de la commande maximale | `payment_au/cashondelivery/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordre de tri | `payment_au/cashondelivery/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activé | `payment_au/banktransfer/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titre | `payment_au/banktransfer/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| New Order Status | `payment_au/banktransfer/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paiement par les pays applicables | `payment_au/banktransfer/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paiement par pays spécifique | `payment_au/banktransfer/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Instructions | `payment_au/banktransfer/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de la commande minimale | `payment_au/banktransfer/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de la commande maximale | `payment_au/banktransfer/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordre de tri | `payment_au/banktransfer/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activé | `payment_au/checkmo/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titre | `payment_au/checkmo/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| New Order Status | `payment_au/checkmo/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paiement par les pays applicables | `payment_au/checkmo/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paiement par pays spécifique | `payment_au/checkmo/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Rendre le paiement | `payment_au/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Envoyer la vérification à | `payment_au/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de la commande minimale | `payment_au/checkmo/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de la commande maximale | `payment_au/checkmo/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordre de tri | `payment_au/checkmo/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activé | `payment_au/purchaseorder/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titre | `payment_au/purchaseorder/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| New Order Status | `payment_au/purchaseorder/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paiement par les pays applicables | `payment_au/purchaseorder/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paiement par pays spécifique | `payment_au/purchaseorder/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de la commande minimale | `payment_au/purchaseorder/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de la commande maximale | `payment_au/purchaseorder/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordre de tri | `payment_au/purchaseorder/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activé | `payment_au/authorizenet_directpost/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Action de paiement | `payment_au/authorizenet_directpost/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titre | `payment_au/authorizenet_directpost/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| New Order Status | `payment_au/authorizenet_directpost/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Devise acceptée | `payment_au/authorizenet_directpost/currency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Déboguer | `payment_au/authorizenet_directpost/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Types de carte de crédit | `payment_au/authorizenet_directpost/cctypes` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Vérification de carte de crédit | `payment_au/authorizenet_directpost/useccv` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paiement par les pays applicables | `payment_au/authorizenet_directpost/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paiement par pays spécifique | `payment_au/authorizenet_directpost/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de la commande minimale | `payment_au/authorizenet_directpost/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de la commande maximale | `payment_au/authorizenet_directpost/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordre de tri | `payment_au/authorizenet_directpost/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activé | `payment_au/cybersource/active` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Action de paiement | `payment_au/cybersource/payment_action` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Titre | `payment_au/cybersource/title` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Identifiant du marchand | `payment_au/cybersource/merchant_id` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![Encrypted](/help/assets/configuration/cloud-enc.png) |
| Identifiant de profil | `payment_au/cybersource/profile_id` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![Encrypted](/help/assets/configuration/cloud-enc.png) |
| New Order Status | `payment_au/cybersource/order_status` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Déboguer | `payment_au/cybersource/debug` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Types de carte de crédit | `payment_au/cybersource/cctypes` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Paiement par les pays applicables | `payment_au/cybersource/allowspecific` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Paiement par pays spécifique | `payment_au/cybersource/specificcountry` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Total de la commande minimale | `payment_au/cybersource/min_order_total` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Total de la commande maximale | `payment_au/cybersource/max_order_total` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Ordre de tri | `payment_au/cybersource/sort_order` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Activé | `payment_au/worldpay/active` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Titre | `payment_au/worldpay/title` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| ID d’installation | `payment_au/worldpay/installation_id` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Autoriser la modification des coordonnées | `payment_au/worldpay/fix_contact` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Masquer les informations de contact | `payment_au/worldpay/hide_contact` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Champs de signature | `payment_au/worldpay/signature_fields` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Déboguer | `payment_au/worldpay/debug` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Mode test | `payment_au/worldpay/sandbox_flag` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Action de paiement pour le test | `payment_au/worldpay/test_action` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Action de paiement | `payment_au/worldpay/payment_action` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Paiement Des Pays Applicables | `payment_au/worldpay/allowspecific` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Paiement De Pays Spécifiques | `payment_au/worldpay/specificcountry` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Définir l’état de la commande sur Fraude suspectée pour CVV | `payment_au/worldpay/cvv_fraud_case` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Définir l’état de la commande sur Fraude suspectée pour le code Postcode AVS | `payment_au/worldpay/avs_fraud_case` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Ordre de tri | `payment_au/worldpay/sort_order` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Activé | `payment_au/eway/active` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Type de connexion | `payment_au/eway/connection_type` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Titre | `payment_au/eway/title` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Action de paiement | `payment_au/eway/payment_action` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Déboguer | `payment_au/eway/debug` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Types de carte de crédit | `payment_au/eway/cctypes` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Paiement par les pays applicables | `payment_au/eway/allowspecific` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Paiement par pays spécifique | `payment_au/eway/specificcountry` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Ordre de tri | `payment_au/eway/sort_order` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Récupération planifiée | `payment_ca/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Style des pages marchandes PayPal | `payment_ca/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Récupération planifiée | `payment_ca/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Style des pages marchandes PayPal | `payment_ca/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activer cette solution | `payment/paypal_payment_pro/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paramètres de carte de crédit | `payment_ca/paypal_payment_gateways/wpp_ca/settings_paypal_payflow/heading_cc` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Rejeter la transaction si : | `payment_ca/paypal_payment_gateways/wpp_ca/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_avs_check/heading_avs_settings` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Récupération planifiée | `payment_ca/paypal_payment_gateways/wpp_ca/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paramètres de carte de crédit | `payment_ca/paypal_payment_gateways/paypal_payflowpro_ca/settings_paypal_payflow/heading_cc` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Rejeter la transaction si : | `payment_ca/paypal_payment_gateways/paypal_payflowpro_ca/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_avs_check/heading_avs_settings` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Récupération planifiée | `payment_ca/paypal_payment_gateways/paypal_payflowpro_ca/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Récupération planifiée | `payment_ca/paypal_payment_gateways/payflow_link_ca/settings_payflow_link/settings_payflow_link_advanced/payflow_link_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Style des pages marchandes PayPal | `payment_ca/paypal_payment_gateways/payflow_link_ca/settings_payflow_link/settings_payflow_link_advanced/payflow_link_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activé | `payment_ca/free/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titre | `payment_ca/free/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| New Order Status | `payment_ca/free/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Facturer automatiquement tous les éléments | `payment_ca/free/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paiement par les pays applicables | `payment_ca/free/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paiement par pays spécifique | `payment_ca/free/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordre de tri | `payment_ca/free/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activé | `payment_ca/cashondelivery/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titre | `payment_ca/cashondelivery/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| New Order Status | `payment_ca/cashondelivery/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paiement par les pays applicables | `payment_ca/cashondelivery/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paiement par pays spécifique | `payment_ca/cashondelivery/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Instructions | `payment_ca/cashondelivery/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de la commande minimale | `payment_ca/cashondelivery/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de la commande maximale | `payment_ca/cashondelivery/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordre de tri | `payment_ca/cashondelivery/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activé | `payment_ca/banktransfer/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titre | `payment_ca/banktransfer/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| New Order Status | `payment_ca/banktransfer/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paiement par les pays applicables | `payment_ca/banktransfer/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paiement par pays spécifique | `payment_ca/banktransfer/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Instructions | `payment_ca/banktransfer/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de la commande minimale | `payment_ca/banktransfer/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de la commande maximale | `payment_ca/banktransfer/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordre de tri | `payment_ca/banktransfer/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activé | `payment_ca/checkmo/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titre | `payment_ca/checkmo/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| New Order Status | `payment_ca/checkmo/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paiement par les pays applicables | `payment_ca/checkmo/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paiement par pays spécifique | `payment_ca/checkmo/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de la commande minimale | `payment_ca/checkmo/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de la commande maximale | `payment_ca/checkmo/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordre de tri | `payment_ca/checkmo/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activé | `payment_ca/purchaseorder/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titre | `payment_ca/purchaseorder/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| New Order Status | `payment_ca/purchaseorder/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paiement par les pays applicables | `payment_ca/purchaseorder/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paiement par pays spécifique | `payment_ca/purchaseorder/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de la commande minimale | `payment_ca/purchaseorder/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de la commande maximale | `payment_ca/purchaseorder/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordre de tri | `payment_ca/purchaseorder/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activé | `payment_ca/authorizenet_directpost/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Action de paiement | `payment_ca/authorizenet_directpost/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titre | `payment_ca/authorizenet_directpost/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Devise acceptée | `payment_ca/authorizenet_directpost/currency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Déboguer | `payment_ca/authorizenet_directpost/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Types de carte de crédit | `payment_ca/authorizenet_directpost/cctypes` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Vérification de carte de crédit | `payment_ca/authorizenet_directpost/useccv` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paiement par les pays applicables | `payment_ca/authorizenet_directpost/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paiement par pays spécifique | `payment_ca/authorizenet_directpost/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de la commande minimale | `payment_ca/authorizenet_directpost/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de la commande maximale | `payment_ca/authorizenet_directpost/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordre de tri | `payment_ca/authorizenet_directpost/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activé | `payment_ca/cybersource/active` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Action de paiement | `payment_ca/cybersource/payment_action` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Titre | `payment_ca/cybersource/title` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Déboguer | `payment_ca/cybersource/debug` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Types de carte de crédit | `payment_ca/cybersource/cctypes` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Paiement par les pays applicables | `payment_ca/cybersource/allowspecific` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Paiement par pays spécifique | `payment_ca/cybersource/specificcountry` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Total de la commande minimale | `payment_ca/cybersource/min_order_total` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Total de la commande maximale | `payment_ca/cybersource/max_order_total` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Ordre de tri | `payment_ca/cybersource/sort_order` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Activé | `payment_ca/worldpay/active` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Titre | `payment_ca/worldpay/title` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Autoriser la modification des coordonnées | `payment_ca/worldpay/fix_contact` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Masquer les informations de contact | `payment_ca/worldpay/hide_contact` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Champs de signature | `payment_ca/worldpay/signature_fields` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Déboguer | `payment_ca/worldpay/debug` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Action de paiement pour le test | `payment_ca/worldpay/test_action` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Action de paiement | `payment_ca/worldpay/payment_action` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Paiement Des Pays Applicables | `payment_ca/worldpay/allowspecific` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Paiement De Pays Spécifiques | `payment_ca/worldpay/specificcountry` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Définir l’état de la commande sur Fraude suspectée pour CVV | `payment_ca/worldpay/cvv_fraud_case` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Définir l’état de la commande sur Fraude suspectée pour le code Postcode AVS | `payment_ca/worldpay/avs_fraud_case` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Ordre de tri | `payment_ca/worldpay/sort_order` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Activé | `payment_ca/eway/active` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Type de connexion | `payment_ca/eway/connection_type` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Titre | `payment_ca/eway/title` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Action de paiement | `payment_ca/eway/payment_action` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Déboguer | `payment_ca/eway/debug` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Types de carte de crédit | `payment_ca/eway/cctypes` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Paiement par les pays applicables | `payment_ca/eway/allowspecific` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Paiement par pays spécifique | `payment_ca/eway/specificcountry` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Ordre de tri | `payment_ca/eway/sort_order` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Récupération planifiée | `payment_other/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Style des pages marchandes PayPal | `payment_other/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Récupération planifiée | `payment_other/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Style des pages marchandes PayPal | `payment_other/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activé | `payment_other/free/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titre | `payment_other/free/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| New Order Status | `payment_other/free/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Facturer automatiquement tous les éléments | `payment_other/free/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paiement par les pays applicables | `payment_other/free/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paiement par pays spécifique | `payment_other/free/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordre de tri | `payment_other/free/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activé | `payment_other/cashondelivery/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titre | `payment_other/cashondelivery/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| New Order Status | `payment_other/cashondelivery/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paiement par les pays applicables | `payment_other/cashondelivery/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paiement par pays spécifique | `payment_other/cashondelivery/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Instructions | `payment_other/cashondelivery/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de la commande minimale | `payment_other/cashondelivery/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de la commande maximale | `payment_other/cashondelivery/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordre de tri | `payment_other/cashondelivery/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activé | `payment_other/banktransfer/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titre | `payment_other/banktransfer/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| New Order Status | `payment_other/banktransfer/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paiement par les pays applicables | `payment_other/banktransfer/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paiement par pays spécifique | `payment_other/banktransfer/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Instructions | `payment_other/banktransfer/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de la commande minimale | `payment_other/banktransfer/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de la commande maximale | `payment_other/banktransfer/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordre de tri | `payment_other/banktransfer/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activé | `payment_other/checkmo/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titre | `payment_other/checkmo/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| New Order Status | `payment_other/checkmo/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paiement par les pays applicables | `payment_other/checkmo/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paiement par pays spécifique | `payment_other/checkmo/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de la commande minimale | `payment_other/checkmo/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de la commande maximale | `payment_other/checkmo/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordre de tri | `payment_other/checkmo/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activé | `payment_other/purchaseorder/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titre | `payment_other/purchaseorder/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| New Order Status | `payment_other/purchaseorder/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paiement par les pays applicables | `payment_other/purchaseorder/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paiement par pays spécifique | `payment_other/purchaseorder/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de la commande minimale | `payment_other/purchaseorder/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de la commande maximale | `payment_other/purchaseorder/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordre de tri | `payment_other/purchaseorder/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activé | `payment_other/authorizenet_directpost/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Action de paiement | `payment_other/authorizenet_directpost/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titre | `payment_other/authorizenet_directpost/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Devise acceptée | `payment_other/authorizenet_directpost/currency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Déboguer | `payment_other/authorizenet_directpost/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Client de messagerie | `payment_other/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Types de carte de crédit | `payment_other/authorizenet_directpost/cctypes` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Vérification de carte de crédit | `payment_other/authorizenet_directpost/useccv` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paiement par les pays applicables | `payment_other/authorizenet_directpost/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paiement par pays spécifique | `payment_other/authorizenet_directpost/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de la commande minimale | `payment_other/authorizenet_directpost/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de la commande maximale | `payment_other/authorizenet_directpost/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordre de tri | `payment_other/authorizenet_directpost/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activé | `payment_other/cybersource/active` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Action de paiement | `payment_other/cybersource/payment_action` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Titre | `payment_other/cybersource/title` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Déboguer | `payment_other/cybersource/debug` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Types de carte de crédit | `payment_other/cybersource/cctypes` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Paiement par les pays applicables | `payment_other/cybersource/allowspecific` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Paiement par pays spécifique | `payment_other/cybersource/specificcountry` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Total de la commande minimale | `payment_other/cybersource/min_order_total` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Total de la commande maximale | `payment_other/cybersource/max_order_total` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Ordre de tri | `payment_other/cybersource/sort_order` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Activé | `payment_other/worldpay/active` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Titre | `payment_other/worldpay/title` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Autoriser la modification des coordonnées | `payment_other/worldpay/fix_contact` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Masquer les informations de contact | `payment_other/worldpay/hide_contact` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Champs de signature | `payment_other/worldpay/signature_fields` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Déboguer | `payment_other/worldpay/debug` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Action de paiement pour le test | `payment_other/worldpay/test_action` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Action de paiement | `payment_other/worldpay/payment_action` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Paiement Des Pays Applicables | `payment_other/worldpay/allowspecific` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Paiement De Pays Spécifiques | `payment_other/worldpay/specificcountry` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Définir l’état de la commande sur Fraude suspectée pour CVV | `payment_other/worldpay/cvv_fraud_case` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Définir l’état de la commande sur Fraude suspectée pour le code Postcode AVS | `payment_other/worldpay/avs_fraud_case` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Ordre de tri | `payment_other/worldpay/sort_order` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Activé | `payment_other/eway/active` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Type de connexion | `payment_other/eway/connection_type` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Titre | `payment_other/eway/title` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Action de paiement | `payment_other/eway/payment_action` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Déboguer | `payment_other/eway/debug` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Types de carte de crédit | `payment_other/eway/cctypes` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Paiement par les pays applicables | `payment_other/eway/allowspecific` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Paiement par pays spécifique | `payment_other/eway/specificcountry` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Ordre de tri | `payment_other/eway/sort_order` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Récupération planifiée | `payment_de/paypal_payment_solutions/express_checkout_de/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Style des pages marchandes PayPal | `payment_de/paypal_payment_solutions/express_checkout_de/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activé | `payment_de/checkmo/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titre | `payment_de/checkmo/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| New Order Status | `payment_de/checkmo/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paiement par les pays applicables | `payment_de/checkmo/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paiement par pays spécifique | `payment_de/checkmo/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de la commande minimale | `payment_de/checkmo/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de la commande maximale | `payment_de/checkmo/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordre de tri | `payment_de/checkmo/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activé | `payment_de/banktransfer/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titre | `payment_de/banktransfer/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| New Order Status | `payment_de/banktransfer/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paiement par les pays applicables | `payment_de/banktransfer/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paiement par pays spécifique | `payment_de/banktransfer/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Instructions | `payment_de/banktransfer/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de la commande minimale | `payment_de/banktransfer/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de la commande maximale | `payment_de/banktransfer/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordre de tri | `payment_de/banktransfer/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activé | `payment_de/cashondelivery/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titre | `payment_de/cashondelivery/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| New Order Status | `payment_de/cashondelivery/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paiement par les pays applicables | `payment_de/cashondelivery/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paiement par pays spécifique | `payment_de/cashondelivery/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Instructions | `payment_de/cashondelivery/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de la commande minimale | `payment_de/cashondelivery/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de la commande maximale | `payment_de/cashondelivery/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordre de tri | `payment_de/cashondelivery/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activé | `payment_de/free/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titre | `payment_de/free/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| New Order Status | `payment_de/free/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Facturer automatiquement tous les éléments | `payment_de/free/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paiement par les pays applicables | `payment_de/free/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paiement par pays spécifique | `payment_de/free/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordre de tri | `payment_de/free/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activé | `payment_de/purchaseorder/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titre | `payment_de/purchaseorder/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| New Order Status | `payment_de/purchaseorder/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paiement par les pays applicables | `payment_de/purchaseorder/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paiement par pays spécifique | `payment_de/purchaseorder/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de la commande minimale | `payment_de/purchaseorder/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de la commande maximale | `payment_de/purchaseorder/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordre de tri | `payment_de/purchaseorder/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activé | `payment_de/cybersource/active` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Action de paiement | `payment_de/cybersource/payment_action` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Titre | `payment_de/cybersource/title` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| New Order Status | `payment_de/cybersource/order_status` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Déboguer | `payment_de/cybersource/debug` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Types de carte de crédit | `payment_de/cybersource/cctypes` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Paiement par les pays applicables | `payment_de/cybersource/allowspecific` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Paiement par pays spécifique | `payment_de/cybersource/specificcountry` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Total de la commande minimale | `payment_de/cybersource/min_order_total` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Total de la commande maximale | `payment_de/cybersource/max_order_total` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Ordre de tri | `payment_de/cybersource/sort_order` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Activé | `payment_de/authorizenet_directpost/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Action de paiement | `payment_de/authorizenet_directpost/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titre | `payment_de/authorizenet_directpost/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| New Order Status | `payment_de/authorizenet_directpost/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Devise acceptée | `payment_de/authorizenet_directpost/currency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Déboguer | `payment_de/authorizenet_directpost/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Types de carte de crédit | `payment_de/authorizenet_directpost/cctypes` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Vérification de carte de crédit | `payment_de/authorizenet_directpost/useccv` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paiement par les pays applicables | `payment_de/authorizenet_directpost/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paiement par pays spécifique | `payment_de/authorizenet_directpost/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de la commande minimale | `payment_de/authorizenet_directpost/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de la commande maximale | `payment_de/authorizenet_directpost/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordre de tri | `payment_de/authorizenet_directpost/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activé | `payment_de/worldpay/active` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Titre | `payment_de/worldpay/title` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Autoriser la modification des coordonnées | `payment_de/worldpay/fix_contact` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Masquer les informations de contact | `payment_de/worldpay/hide_contact` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Champs de signature | `payment_de/worldpay/signature_fields` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Mode test | `payment_de/worldpay/sandbox_flag` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Action de paiement pour le test | `payment_de/worldpay/test_action` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Action de paiement | `payment_de/worldpay/payment_action` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Paiement Des Pays Applicables | `payment_de/worldpay/allowspecific` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Paiement De Pays Spécifiques | `payment_de/worldpay/specificcountry` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Définir l’état de la commande sur Fraude suspectée pour CVV | `payment_de/worldpay/cvv_fraud_case` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Définir l’état de la commande sur Fraude suspectée pour le code Postcode AVS | `payment_de/worldpay/avs_fraud_case` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Ordre de tri | `payment_de/worldpay/sort_order` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Activé | `payment_de/eway/active` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Type de connexion | `payment_de/eway/connection_type` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Titre | `payment_de/eway/title` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Action de paiement | `payment_de/eway/payment_action` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Déboguer | `payment_de/eway/debug` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Types de carte de crédit | `payment_de/eway/cctypes` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Paiement par les pays applicables | `payment_de/eway/allowspecific` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Paiement par pays spécifique | `payment_de/eway/specificcountry` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Ordre de tri | `payment_de/eway/sort_order` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Récupération planifiée | `payment_gb/paypal_alternative_payment_methods/express_checkout_gb/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Style des pages marchandes PayPal | `payment_gb/paypal_alternative_payment_methods/express_checkout_gb/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Récupération planifiée | `payment_gb/paypal_group_all_in_one/payments_pro_hosted_solution_with_express_checkout/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Style des pages marchandes PayPal | `payment_gb/paypal_group_all_in_one/payments_pro_hosted_solution_with_express_checkout/pphs_settings/pphs_settings_advanced/pphs_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Récupération planifiée | `payment_gb/paypal_group_all_in_one/wps_express/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Style des pages marchandes PayPal | `payment_gb/paypal_group_all_in_one/wps_express/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activé | `payment_gb/checkmo/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titre | `payment_gb/checkmo/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| New Order Status | `payment_gb/checkmo/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paiement par les pays applicables | `payment_gb/checkmo/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paiement par pays spécifique | `payment_gb/checkmo/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Rendre le paiement | `payment_gb/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de la commande minimale | `payment_gb/checkmo/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de la commande maximale | `payment_gb/checkmo/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordre de tri | `payment_gb/checkmo/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activé | `payment_gb/banktransfer/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titre | `payment_gb/banktransfer/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| New Order Status | `payment_gb/banktransfer/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paiement par les pays applicables | `payment_gb/banktransfer/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paiement par pays spécifique | `payment_gb/banktransfer/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Instructions | `payment_gb/banktransfer/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de la commande minimale | `payment_gb/banktransfer/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de la commande maximale | `payment_gb/banktransfer/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordre de tri | `payment_gb/banktransfer/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activé | `payment_gb/cashondelivery/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titre | `payment_gb/cashondelivery/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| New Order Status | `payment_gb/cashondelivery/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paiement par les pays applicables | `payment_gb/cashondelivery/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paiement par pays spécifique | `payment_gb/cashondelivery/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Instructions | `payment_gb/cashondelivery/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de la commande minimale | `payment_gb/cashondelivery/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de la commande maximale | `payment_gb/cashondelivery/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordre de tri | `payment_gb/cashondelivery/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activé | `payment_gb/free/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titre | `payment_gb/free/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| New Order Status | `payment_gb/free/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Facturer automatiquement tous les éléments | `payment_gb/free/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paiement par les pays applicables | `payment_gb/free/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paiement par pays spécifique | `payment_gb/free/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordre de tri | `payment_gb/free/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activé | `payment_gb/purchaseorder/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titre | `payment_gb/purchaseorder/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| New Order Status | `payment_gb/purchaseorder/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paiement par les pays applicables | `payment_gb/purchaseorder/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paiement par pays spécifique | `payment_gb/purchaseorder/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de la commande minimale | `payment_gb/purchaseorder/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de la commande maximale | `payment_gb/purchaseorder/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordre de tri | `payment_gb/purchaseorder/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activé | `payment_gb/cybersource/active` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Action de paiement | `payment_gb/cybersource/payment_action` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Titre | `payment_gb/cybersource/title` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| New Order Status | `payment_gb/cybersource/order_status` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Déboguer | `payment_gb/cybersource/debug` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Types de carte de crédit | `payment_gb/cybersource/cctypes` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Paiement par les pays applicables | `payment_gb/cybersource/allowspecific` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Paiement par pays spécifique | `payment_gb/cybersource/specificcountry` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Total de la commande minimale | `payment_gb/cybersource/min_order_total` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Total de la commande maximale | `payment_gb/cybersource/max_order_total` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Ordre de tri | `payment_gb/cybersource/sort_order` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Activé | `payment_gb/authorizenet_directpost/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Action de paiement | `payment_gb/authorizenet_directpost/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titre | `payment_gb/authorizenet_directpost/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| New Order Status | `payment_gb/authorizenet_directpost/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Devise acceptée | `payment_gb/authorizenet_directpost/currency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Déboguer | `payment_gb/authorizenet_directpost/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Types de carte de crédit | `payment_gb/authorizenet_directpost/cctypes` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Vérification de carte de crédit | `payment_gb/authorizenet_directpost/useccv` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paiement par les pays applicables | `payment_gb/authorizenet_directpost/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paiement par pays spécifique | `payment_gb/authorizenet_directpost/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de la commande minimale | `payment_gb/authorizenet_directpost/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de la commande maximale | `payment_gb/authorizenet_directpost/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordre de tri | `payment_gb/authorizenet_directpost/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activé | `payment_gb/worldpay/active` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Titre | `payment_gb/worldpay/title` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Secret MD5 pour les transactions | `payment_gb/worldpay/md5_secret` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Autoriser la modification des coordonnées | `payment_gb/worldpay/fix_contact` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Masquer les informations de contact | `payment_gb/worldpay/hide_contact` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Champs de signature | `payment_gb/worldpay/signature_fields` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Déboguer | `payment_gb/worldpay/debug` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Action de paiement pour le test | `payment_gb/worldpay/test_action` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Action de paiement | `payment_gb/worldpay/payment_action` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Paiement Des Pays Applicables | `payment_gb/worldpay/allowspecific` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Paiement De Pays Spécifiques | `payment_gb/worldpay/specificcountry` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Définir l’état de la commande sur Fraude suspectée pour CVV | `payment_gb/worldpay/cvv_fraud_case` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Définir l’état de la commande sur Fraude suspectée pour le code Postcode AVS | `payment_gb/worldpay/avs_fraud_case` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Ordre de tri | `payment_gb/worldpay/sort_order` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Activé | `payment_gb/eway/active` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Type de connexion | `payment_gb/eway/connection_type` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Titre | `payment_gb/eway/title` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Action de paiement | `payment_gb/eway/payment_action` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Déboguer | `payment_gb/eway/debug` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Types de carte de crédit | `payment_gb/eway/cctypes` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Paiement par les pays applicables | `payment_gb/eway/allowspecific` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Paiement par pays spécifique | `payment_gb/eway/specificcountry` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Ordre de tri | `payment_gb/eway/sort_order` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Récupération planifiée | `payment_us/paypal_alternative_payment_methods/express_checkout_us/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Style des pages marchandes PayPal | `payment_us/paypal_alternative_payment_methods/express_checkout_us/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Récupération planifiée | `payment_us/paypal_group_all_in_one/payflow_advanced/settings_payments_advanced/settings_payments_advanced_advanced/settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Style des pages marchandes PayPal | `payment_us/paypal_group_all_in_one/payflow_advanced/settings_payments_advanced/settings_payments_advanced_advanced/frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paramètres de carte de crédit | `payment_us/paypal_group_all_in_one/wpp_usuk/settings_paypal_payflow/heading_cc` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Rejeter la transaction si : | `payment_us/paypal_group_all_in_one/wpp_usuk/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_avs_check/heading_avs_settings` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Récupération planifiée | `payment_us/paypal_group_all_in_one/wpp_usuk/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Style des pages marchandes PayPal | `payment_us/paypal_group_all_in_one/wpp_usuk/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activer le crédit PayPal | `payment/wps_express_bml/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Récupération planifiée | `payment_us/paypal_group_all_in_one/wps_express/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Style des pages marchandes PayPal | `payment_us/paypal_group_all_in_one/wps_express/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paramètres de carte de crédit | `payment_us/paypal_payment_gateways/paypal_payflowpro_with_express_checkout/settings_paypal_payflow/heading_cc` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Rejeter la transaction si : | `payment_us/paypal_payment_gateways/paypal_payflowpro_with_express_checkout/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_avs_check/heading_avs_settings` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Récupération planifiée | `payment_us/paypal_payment_gateways/paypal_payflowpro_with_express_checkout/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Style des pages marchandes PayPal | `payment_us/paypal_payment_gateways/paypal_payflowpro_with_express_checkout/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Récupération planifiée | `payment_us/paypal_payment_gateways/payflow_link_us/settings_payflow_link/settings_payflow_link_advanced/payflow_link_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Style des pages marchandes PayPal | `payment_us/paypal_payment_gateways/payflow_link_us/settings_payflow_link/settings_payflow_link_advanced/payflow_link_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activé | `payment_us/free/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titre | `payment_us/free/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| New Order Status | `payment_us/free/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Facturer automatiquement tous les éléments | `payment_us/free/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paiement par les pays applicables | `payment_us/free/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paiement par pays spécifique | `payment_us/free/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordre de tri | `payment_us/free/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activé | `payment_us/cashondelivery/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titre | `payment_us/cashondelivery/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| New Order Status | `payment_us/cashondelivery/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paiement par les pays applicables | `payment_us/cashondelivery/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paiement par pays spécifique | `payment_us/cashondelivery/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Instructions | `payment_us/cashondelivery/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de la commande minimale | `payment_us/cashondelivery/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de la commande maximale | `payment_us/cashondelivery/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordre de tri | `payment_us/cashondelivery/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activé | `payment_us/banktransfer/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titre | `payment_us/banktransfer/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| New Order Status | `payment_us/banktransfer/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paiement par les pays applicables | `payment_us/banktransfer/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paiement par pays spécifique | `payment_us/banktransfer/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Instructions | `payment_us/banktransfer/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de la commande minimale | `payment_us/banktransfer/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de la commande maximale | `payment_us/banktransfer/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordre de tri | `payment_us/banktransfer/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activé | `payment_us/checkmo/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titre | `payment_us/checkmo/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| New Order Status | `payment_us/checkmo/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paiement par les pays applicables | `payment_us/checkmo/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paiement par pays spécifique | `payment_us/checkmo/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Rendre le paiement | `payment_us/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de la commande minimale | `payment_us/checkmo/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de la commande maximale | `payment_us/checkmo/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordre de tri | `payment_us/checkmo/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activé | `payment_us/purchaseorder/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titre | `payment_us/purchaseorder/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| New Order Status | `payment_us/purchaseorder/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paiement par les pays applicables | `payment_us/purchaseorder/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paiement par pays spécifique | `payment_us/purchaseorder/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de la commande minimale | `payment_us/purchaseorder/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de la commande maximale | `payment_us/purchaseorder/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordre de tri | `payment_us/purchaseorder/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activé | `payment_us/authorizenet_directpost/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Action de paiement | `payment_us/authorizenet_directpost/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titre | `payment_us/authorizenet_directpost/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| New Order Status | `payment_us/authorizenet_directpost/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Devise acceptée | `payment_us/authorizenet_directpost/currency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Déboguer | `payment_us/authorizenet_directpost/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Types de carte de crédit | `payment_us/authorizenet_directpost/cctypes` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Vérification de carte de crédit | `payment_us/authorizenet_directpost/useccv` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paiement par les pays applicables | `payment_us/authorizenet_directpost/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paiement par pays spécifique | `payment_us/authorizenet_directpost/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de la commande minimale | `payment_us/authorizenet_directpost/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de la commande maximale | `payment_us/authorizenet_directpost/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordre de tri | `payment_us/authorizenet_directpost/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activé | `payment_us/cybersource/active` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Action de paiement | `payment_us/cybersource/payment_action` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Titre | `payment_us/cybersource/title` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| New Order Status | `payment_us/cybersource/order_status` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Déboguer | `payment_us/cybersource/debug` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Types de carte de crédit | `payment_us/cybersource/cctypes` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Paiement par les pays applicables | `payment_us/cybersource/allowspecific` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Paiement par pays spécifique | `payment_us/cybersource/specificcountry` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Total de la commande minimale | `payment_us/cybersource/min_order_total` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Total de la commande maximale | `payment_us/cybersource/max_order_total` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Ordre de tri | `payment_us/cybersource/sort_order` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Activé | `payment_us/worldpay/active` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Titre | `payment_us/worldpay/title` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Autoriser la modification des coordonnées | `payment_us/worldpay/fix_contact` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Masquer les informations de contact | `payment_us/worldpay/hide_contact` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Champs de signature | `payment_us/worldpay/signature_fields` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Déboguer | `payment_us/worldpay/debug` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Action de paiement pour le test | `payment_us/worldpay/test_action` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Action de paiement | `payment_us/worldpay/payment_action` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Paiement Des Pays Applicables | `payment_us/worldpay/allowspecific` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Paiement De Pays Spécifiques | `payment_us/worldpay/specificcountry` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Définir l’état de la commande sur Fraude suspectée pour CVV | `payment_us/worldpay/cvv_fraud_case` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Définir l’état de la commande sur Fraude suspectée pour le code Postcode AVS | `payment_us/worldpay/avs_fraud_case` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Ordre de tri | `payment_us/worldpay/sort_order` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Activé | `payment_us/eway/active` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Type de connexion | `payment_us/eway/connection_type` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Titre | `payment_us/eway/title` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Action de paiement | `payment_us/eway/payment_action` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Déboguer | `payment_us/eway/debug` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Types de carte de crédit | `payment_us/eway/cctypes` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Paiement par les pays applicables | `payment_us/eway/allowspecific` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Paiement par pays spécifique | `payment_us/eway/specificcountry` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| Ordre de tri | `payment_us/eway/sort_order` | |

{style="table-layout:auto"}
