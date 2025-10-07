---
title: Référence des chemins de configuration des clients
description: Découvrez les chemins et les valeurs de configuration du client dans les paramètres d’administration Adobe Commerce. Découvrez les options de newsletter, de gestion de compte et de service client.
feature: Configuration, Customers
exl-id: a0571423-6fbd-4cfc-9797-a13c0c24bb53
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '896'
ht-degree: 0%

---

# Référence des chemins de configuration des clients

Cette section répertorie les noms de variables et les chemins de configuration disponibles pour les options dans Admin sous **Magasins** > Paramètres > **Configuration** > **Clients**.

La commande [`magento app:config:dump` écrit ](../cli/export-configuration.md) ces valeurs dans le fichier de configuration partagé, `app/etc/config.php`, qui doit se trouver dans le contrôle de code source. Pour remplacer éventuellement des paramètres de configuration ou définir des paramètres sensibles, voir [Utiliser des variables d’environnement pour remplacer des paramètres de configuration](override-config-settings.md#environment-variables). Cette rubrique ne répertorie _pas_ les [valeurs sensibles et spécifiques au système](config-reference-sens.md).

## Chemins d’accès à la newsletter

Ces valeurs de configuration sont disponibles dans Admin dans **Magasins** > Paramètres > **Configuration** > **Clients** > **Newsletter**.

| Nom | Chemin de configuration | Commerce uniquement ? |
|--------------|--------------|--------------|
| Autoriser l’abonnement des invités | `newsletter/subscription/allow_guest_subscribe` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Confirmation nécessaire | `newsletter/subscription/confirm` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Expéditeur d’e-mail de confirmation | `newsletter/subscription/confirm_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modèle d’e-mail de confirmation | `newsletter/subscription/confirm_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Expéditeur d’e-mail de succès | `newsletter/subscription/success_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modèle d’e-mail de succès | `newsletter/subscription/success_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Expéditeur d’e-mail de désabonnement | `newsletter/subscription/un_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modèle d’e-mail de désabonnement | `newsletter/subscription/un_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Chemins de configuration du client

Ces valeurs de configuration sont disponibles dans Admin dans **Magasins** > Paramètres > **Configuration** > **Clients** > **Configuration client**.

| Nom | Chemin de configuration | Commerce uniquement ? |
|--------------|--------------|--------------|
| Intervalle de minutes en ligne | `customer/online_customers/online_minutes_interval` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Partager les comptes client | `customer/account_share/scope` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activer l&#39;affectation automatique au groupe de clients | `customer/create_account/auto_group_assign` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Calcul De La Taxe Basé Sur | `customer/create_account/tax_calculation_address_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Groupe par défaut | `customer/create_account/default_group` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Groupe pour ID TVA valide - Domestique | `customer/create_account/viv_domestic_group` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Groupe pour ID TVA valide - intra-Union | `customer/create_account/viv_intra_union_group` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Regrouper les ID TVA non valides | `customer/create_account/viv_invalid_group` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Groupe d’erreurs de validation | `customer/create_account/viv_error_group` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Valider sur chaque transaction | `customer/create_account/viv_on_each_transaction` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Valeur par défaut pour Désactiver les modifications de groupe automatiques basées sur l&#39;ID TVA | `customer/create_account/viv_disable_auto_group_assign_default` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Afficher le numéro de TVA sur Storefront | `customer/create_account/vat_frontend_visibility` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-mail de bienvenue par défaut | `customer/create_account/email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-Mail De Bienvenue Par Défaut Sans Mot De Passe | `customer/create_account/email_no_password_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Expéditeur de l’e-mail | `customer/create_account/email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Exiger la confirmation des e-mails | `customer/create_account/confirm` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-mail du lien de confirmation | `customer/create_account/email_confirmation_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Welcome Email | `customer/create_account/email_confirmed_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Générer un ID de client convivial | `customer/create_account/generate_human_friendly_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Type de protection contre la réinitialisation du mot de passe | `customer/password/password_reset_protection_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nbre max. de demandes de réinitialisation de mot de passe | `customer/password/max_number_password_reset_requests` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Durée Minimale Entre Les Demandes De Réinitialisation De Mot De Passe | `customer/password/min_time_between_password_reset_requests` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modèle d’e-mail oublié | `customer/password/forgot_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modèle d’e-mail de rappel | `customer/password/remind_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Réinitialiser le modèle de mot de passe | `customer/password/reset_password_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Expéditeur d’e-mail du modèle de mot de passe | `customer/password/forgot_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Délai d&#39;expiration du lien de récupération (heures) | `customer/password/reset_link_expiration_period` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activer la saisie automatique sur les formulaires de mot de passe de connexion/oubli | `customer/password/autocomplete_on_storefront` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nombre de classes de caractères obligatoires | `customer/password/required_character_classes_number` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nombre maximal d’échecs de connexion au compte de verrouillage | `customer/password/lockout_failures` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Longueur minimale du mot de passe | `customer/password/minimum_password_length` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Durée du verrouillage (minutes) | `customer/password/lockout_threshold` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nombre de lignes dans une adresse postale | `customer/address/street_lines` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Afficher le préfixe | `customer/address/prefix_show` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Options de liste déroulante de préfixe | `customer/address/prefix_options` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Afficher le deuxième prénom (initial) | `customer/address/middlename_show` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Afficher le suffixe | `customer/address/suffix_show` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Options de la liste déroulante des suffixes | `customer/address/suffix_options` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Afficher la date de naissance | `customer/address/dob_show`<br>Conformément aux bonnes pratiques actuelles en matière de sécurité et de confidentialité, assurez-vous d&#39;être conscient de tous les risques juridiques et de sécurité potentiels associés au stockage de la date de naissance complète du client (mois, jour, année) ainsi que d&#39;autres identifiants personnels, tels que le nom complet, avant de collecter ou de traiter ces données. | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Afficher le numéro de taxe/TVA | `customer/address/taxvat_show` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Afficher le genre | `customer/address/gender_show` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activer la fonctionnalité de crédit de magasin | `customer/magento_customerbalance/is_enabled` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Afficher l&#39;historique de crédit de la boutique aux clients | `customer/magento_customerbalance/show_history` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Rembourser automatiquement le crédit de la boutique | `customer/magento_customerbalance/refund_automatically` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Expéditeur de l&#39;e-mail de mise à jour du crédit de la boutique | `customer/magento_customerbalance/email_identity` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Modèle d&#39;e-mail de mise à jour du crédit de la boutique | `customer/magento_customerbalance/email_template` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Rediriger le client vers le tableau de bord du compte après la connexion | `customer/startup/redirect_dashboard` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Texte | `customer/address_templates/text` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Texte Une Ligne | `customer/address_templates/oneline` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| HTML | `customer/address_templates/html` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PDF | `customer/address_templates/pdf` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activer la fonctionnalité de segment client | `customer/magento_customersegment/is_enabled` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Activer CAPTCHA sur Storefront | `customer/captcha/enable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Police | `customer/captcha/font` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Forms | `customer/captcha/forms` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mode d’affichage | `customer/captcha/mode` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nombre de tentatives de connexion ayant échoué | `customer/captcha/failed_attempts_login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Délai d’expiration de CAPTCHA (minutes) | `customer/captcha/timeout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nombre de symboles | `customer/captcha/length` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Symboles utilisés dans CAPTCHA | `customer/captcha/symbols` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Respect De La Casse | `customer/captcha/case_sensitive` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Chemins de liste de souhaits

Ces valeurs de configuration sont disponibles dans Admin dans **Magasins** > Paramètres > **Configuration** > **Clients** > **Liste de souhaits**.

| Nom | Chemin de configuration | Commerce uniquement ? |
|--------------|--------------|--------------|
| Activé | `wishlist/general/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activer plusieurs listes de souhaits | `wishlist/general/multiple_enabled` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Nombre de listes de souhaits multiples | `wishlist/general/multiple_wishlist_number` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Expéditeur de l’e-mail | `wishlist/email/email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modèle d’e-mail | `wishlist/email/email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nombre maximal d’e-mails pouvant être envoyés | `wishlist/email/number_limit` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Limite de longueur du texte d’e-mail | `wishlist/email/text_limit` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Afficher le résumé des listes de souhaits | `wishlist/wishlist_link/use_qty` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Chemins d’accès aux invitations

Ces valeurs de configuration sont disponibles dans Admin dans **Magasins** > Paramètres > **Configuration** > **Clients** > **Invitations**.

| Nom | Chemin de configuration | Commerce uniquement ? |
|--------------|--------------|--------------|
| Activer la fonctionnalité Invitations | `magento_invitation/general/enabled` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Activer les invitations sur Storefront | `magento_invitation/general/enabled_on_front` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Groupe de clients référencés | `magento_invitation/general/registration_use_inviter_group` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Enregistrement de nouveaux comptes | `magento_invitation/general/registration_required_invitation` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Autoriser les clients à ajouter un message personnalisé à l&#39;e-mail d&#39;invitation | `magento_invitation/general/allow_customer_message` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Nombre maximal d’invitations pouvant être envoyées à la fois | `magento_invitation/general/max_invitation_amount_per_send` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Invitation du client Envoyant un e-mail | `magento_invitation/email/identity` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Modèle d’e-mail d’invitation de client | `magento_invitation/email/template` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |

{style="table-layout:auto"}

## Chemins d’accès aux points de récompense

Ces valeurs de configuration sont disponibles dans Admin dans **Magasins** > Paramètres > **Configuration** > **Clients** > **Points de récompense**.

| Nom | Chemin de configuration | Commerce uniquement ? |
|--------------|--------------|--------------|
| Activer la fonctionnalité de points de récompense | `magento_reward/general/is_enabled` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Activer la fonctionnalité de points de récompense sur Storefront | `magento_reward/general/is_enabled_on_front` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Les Clients Peuvent Consulter L’Historique Des Points De Récompense | `magento_reward/general/publish_history` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Seuil de remboursement du solde des points de récompense | `magento_reward/general/min_points_balance` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Solde Des Points De Récompense Limité À | `magento_reward/general/max_points_balance` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Les points de récompense expirent dans (jours) | `magento_reward/general/expiration_days` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Calcul de l’expiration des points de récompense | `magento_reward/general/expiry_calculation` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Rembourser automatiquement les points de récompense | `magento_reward/general/refund_automatically` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Déduire automatiquement les points de récompense du montant du remboursement | `magento_reward/general/deduct_automatically` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Page de destination | `magento_reward/general/landing_page` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Achat | `magento_reward/points/order` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Inscription | `magento_reward/points/register` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Inscription à la newsletter | `magento_reward/points/newsletter` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Convertir une invitation en client | `magento_reward/points/invitation_customer` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Limite de quantité des invitations à des conversions client | `magento_reward/points/invitation_customer_limit` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Convertir une invitation en commande | `magento_reward/points/invitation_order` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Limite de quantité des invitations à commander des conversions | `magento_reward/points/invitation_order_limit` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Conversion de l&#39;invitation en récompense de commande | `magento_reward/points/invitation_order_frequency` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Consulter la soumission | `magento_reward/points/review` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Limite de quantité de soumission pour les révisions récompensées | `magento_reward/points/review_limit` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Expéditeur de l’e-mail | `magento_reward/notification/email_sender` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Abonner les clients par défaut | `magento_reward/notification/subscribe_by_default` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| E-mail de mise à jour du solde | `magento_reward/notification/balance_update_template` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| E-mail d’avertissement d’expiration des points de récompense | `magento_reward/notification/expiry_warning_template` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Avertissement d&#39;expiration avant (jours) | `magento_reward/notification/expiry_day_before` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |

{style="table-layout:auto"}

## Chemins de promotion

Ces valeurs de configuration sont disponibles dans Admin dans **Magasins** > Paramètres > **Configuration** > **Clients** > **Promotions**.

| Nom | Chemin de configuration | Commerce uniquement ? |
|--------------|--------------|--------------|
| Activer les e-mails de rappel | `promo/magento_reminder/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Fréquence | `promo/magento_reminder/frequency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Intervalle | `promo/magento_reminder/interval` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Minute de l’heure | `promo/magento_reminder/minutes` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Heure de début | `promo/magento_reminder/time` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Nombre maximal d’e-mails par exécution | `promo/magento_reminder/limit` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Seuil d’échec de l’envoi d’e-mail | `promo/magento_reminder/threshold` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Expéditeur d’e-mail de rappel | `promo/magento_reminder/identity` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Longueur du code | `promo/auto_generated_coupon_codes/length` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Format du code | `promo/auto_generated_coupon_codes/format` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Préfixe de code | `promo/auto_generated_coupon_codes/prefix` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Suffixe de code | `promo/auto_generated_coupon_codes/suffix` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tiret Tous Les X Caractères | `promo/auto_generated_coupon_codes/dash` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Chemins d&#39;accès au registre des cadeaux

Ces valeurs de configuration sont disponibles dans Admin dans **Magasins** > Paramètres > **Configuration** > **Clients** > **Registre des cadeaux**.

| Nom | Chemin de configuration | Commerce uniquement ? |
|--------------|--------------|--------------|
| Activer le registre des cadeaux | `magento_giftregistry/general/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nombre maximal d&#39;inscrits | `magento_giftregistry/general/max_registrant` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modèle d’e-mail | `magento_giftregistry/owner_email/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Expéditeur de l’e-mail | `magento_giftregistry/owner_email/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modèle d’e-mail | `magento_giftregistry/sharing_email/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Expéditeur de l’e-mail | `magento_giftregistry/sharing_email/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Seuil maximum d’e-mails envoyés | `magento_giftregistry/sharing_email/send_limit` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modèle d’e-mail | `magento_giftregistry/update_email/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Expéditeur de l’e-mail | `magento_giftregistry/update_email/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Chemins d’accès persistants au panier

Ces valeurs de configuration sont disponibles dans Admin dans **Magasins** > Paramètres > **Configuration** > **Clients** > **Panier persistant**.

| Nom | Chemin de configuration | Commerce uniquement ? |
|--------------|--------------|--------------|
| Activer la persistance | `persistent/options/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Durée de vie de la persistance (secondes) | `persistent/options/lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activer « Se souvenir de moi » | `persistent/options/remember_enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Valeur Par Défaut « Se Souvenir De Moi » | `persistent/options/remember_default` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Effacer la persistance au moment de la déconnexion | `persistent/options/logout_clear` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Conserver le panier | `persistent/options/shopping_cart` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Conserver la liste de souhaits | `persistent/options/wishlist` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Conserver les articles récemment commandés | `persistent/options/recently_ordered` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Conserver Les Produits Comparés Actuellement | `persistent/options/compare_current` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Conserver l’historique de comparaison | `persistent/options/compare_history` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Conserver les produits récemment consultés | `persistent/options/recently_viewed` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Conservation de l’appartenance à un groupe de clients et de la segmentation | `persistent/options/customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}
