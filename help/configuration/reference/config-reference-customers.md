---
title: Référence sur les chemins de configuration des clients
description: Afficher la liste des valeurs de configuration des clients.
feature: Configuration, Customers
exl-id: a0571423-6fbd-4cfc-9797-a13c0c24bb53
source-git-commit: 16e9396f19693436dfc7bdac78d84624a78f0c21
workflow-type: tm+mt
source-wordcount: '883'
ht-degree: 0%

---

# Référence sur les chemins de configuration des clients

Cette section répertorie les noms de variable et les chemins de configuration disponibles pour les options dans l’Admin sous **Magasins** > Paramètres > **Configuration** > **Clients**.

La variable [`magento app:config:dump` command](../cli/export-configuration.md) écrit ces valeurs dans le fichier de configuration partagé, `app/etc/config.php`, qui doit être dans le contrôle source. Pour éventuellement remplacer des paramètres de configuration ou définir des paramètres sensibles, voir [Utilisation des variables d’environnement pour remplacer les paramètres de configuration](override-config-settings.md#environment-variables). Cette rubrique fonctionne _not_ list [valeurs sensibles et spécifiques au système](config-reference-sens.md).

## Chemins de newsletter

Ces valeurs de configuration sont disponibles dans l’ Admin de la section **Magasins** > Paramètres > **Configuration** > **Clients** > **Newsletter**.

| Nom | Chemin de configuration | Commerce uniquement ? |
|--------------|--------------|--------------|
| Autoriser l’abonnement des invités | `newsletter/subscription/allow_guest_subscribe` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Besoin de confirmer | `newsletter/subscription/confirm` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Expéditeur d’email de confirmation | `newsletter/subscription/confirm_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modèle de courrier électronique de confirmation | `newsletter/subscription/confirm_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Success Email Sender | `newsletter/subscription/success_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modèle de courrier électronique de succès | `newsletter/subscription/success_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Désabonnement de l’expéditeur d’emails | `newsletter/subscription/un_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modèle de courrier électronique de désabonnement | `newsletter/subscription/un_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Chemins de configuration des clients

Ces valeurs de configuration sont disponibles dans l’ Admin de la section **Magasins** > Paramètres > **Configuration** > **Clients** > **Configuration client**.

| Nom | Chemin de configuration | Commerce uniquement ? |
|--------------|--------------|--------------|
| Intervalle des minutes en ligne | `customer/online_customers/online_minutes_interval` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Partage de comptes clients | `customer/account_share/scope` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activation de l’affectation automatique au groupe client | `customer/create_account/auto_group_assign` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Calcul de la taxe basé sur | `customer/create_account/tax_calculation_address_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Groupe par défaut | `customer/create_account/default_group` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Groupe pour un identifiant de TVA valide - indigène | `customer/create_account/viv_domestic_group` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Groupe pour un identifiant de TVA valide - Union intercommunautaire | `customer/create_account/viv_intra_union_group` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Groupe pour un ID de TVA non valide | `customer/create_account/viv_invalid_group` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Groupe d’erreurs de validation | `customer/create_account/viv_error_group` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Validation sur chaque transaction | `customer/create_account/viv_on_each_transaction` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Valeur par défaut pour désactiver les modifications automatiques de groupe en fonction de l’ID de TVA | `customer/create_account/viv_disable_auto_group_assign_default` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Afficher le numéro de TVA sur Storefront | `customer/create_account/vat_frontend_visibility` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-mail de bienvenue par défaut | `customer/create_account/email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Courriel de bienvenue par défaut sans mot de passe | `customer/create_account/email_no_password_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Expéditeur des emails | `customer/create_account/email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Confirmation de l’exigence des emails | `customer/create_account/confirm` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Adresse électronique du lien de confirmation | `customer/create_account/email_confirmation_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Courriel de bienvenue | `customer/create_account/email_confirmed_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Générer un ID de client compatible avec les humains | `customer/create_account/generate_human_friendly_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Type de protection de réinitialisation de mot de passe | `customer/password/password_reset_protection_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nombre max. de demandes de réinitialisation de mot de passe | `customer/password/max_number_password_reset_requests` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Durée min. entre les demandes de réinitialisation de mot de passe | `customer/password/min_time_between_password_reset_requests` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modèle de courrier électronique oublié | `customer/password/forgot_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Remplacer le modèle de courrier électronique | `customer/password/remind_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Réinitialiser le modèle de mot de passe | `customer/password/reset_password_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modèle de mot de passe Email Sender | `customer/password/forgot_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Période d’expiration du lien de récupération (heures) | `customer/password/reset_link_expiration_period` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activer la saisie automatique dans les formulaires de connexion/mot de passe oublié | `customer/password/autocomplete_on_storefront` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nombre de classes de caractères obligatoires | `customer/password/required_character_classes_number` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Échecs de connexion max. pour verrouiller le compte | `customer/password/lockout_failures` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Longueur minimale du mot de passe | `customer/password/minimum_password_length` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Durée du verrouillage (minutes) | `customer/password/lockout_threshold` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nombre de lignes d’une adresse de rue | `customer/address/street_lines` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Afficher le préfixe | `customer/address/prefix_show` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Options de liste déroulante des préfixes | `customer/address/prefix_options` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Show Middle Name (initial) | `customer/address/middlename_show` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Afficher le suffixe | `customer/address/suffix_show` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Options du menu déroulant des suffixes | `customer/address/suffix_options` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Afficher la date de naissance | `customer/address/dob_show`<br>Conformément aux bonnes pratiques actuelles en matière de sécurité et de confidentialité, veillez à être conscient des risques potentiels liés à la sécurité et à la légalité liés au stockage de la date de naissance complète des clients (mois, jour, année), ainsi que d’autres identifiants personnels, tels que le nom complet, avant de collecter ou de traiter ces données. | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Afficher le numéro Taxe/TVA | `customer/address/taxvat_show` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Afficher le genre | `customer/address/gender_show` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activation de la fonctionnalité de crédit de magasin | `customer/magento_customerbalance/is_enabled` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Afficher l’historique du crédit de magasin aux clients | `customer/magento_customerbalance/show_history` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Rembourser automatiquement le crédit de la boutique | `customer/magento_customerbalance/refund_automatically` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Store Credit Update Email Sender | `customer/magento_customerbalance/email_identity` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Modèle de courrier électronique de mise à jour de crédit de magasin | `customer/magento_customerbalance/email_template` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Redirection du client vers le tableau de bord de compte après connexion | `customer/startup/redirect_dashboard` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Texte | `customer/address_templates/text` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Texte une ligne | `customer/address_templates/oneline` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| HTML | `customer/address_templates/html` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PDF | `customer/address_templates/pdf` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activation de la fonctionnalité de segment client | `customer/magento_customersegment/is_enabled` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Activation de CAPTCHA sur Storefront | `customer/captcha/enable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Police | `customer/captcha/font` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Forms | `customer/captcha/forms` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mode d’affichage | `customer/captcha/mode` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nombre de tentatives infructueuses de connexion | `customer/captcha/failed_attempts_login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Délai d’expiration CAPTCHA (minutes) | `customer/captcha/timeout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nombre de symboles | `customer/captcha/length` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Symboles utilisés dans CAPTCHA | `customer/captcha/symbols` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Respect de la casse | `customer/captcha/case_sensitive` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Chemins des listes de souhaits

Ces valeurs de configuration sont disponibles dans l’ Admin de la section **Magasins** > Paramètres > **Configuration** > **Clients** > **Liste de souhaits**.

| Nom | Chemin de configuration | Commerce uniquement ? |
|--------------|--------------|--------------|
| Activé | `wishlist/general/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activer plusieurs listes de souhaits | `wishlist/general/multiple_enabled` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Nombre de listes de souhaits multiples | `wishlist/general/multiple_wishlist_number` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Expéditeur des emails | `wishlist/email/email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modèle de courrier électronique | `wishlist/email/email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nombre maximal de courriers électroniques autorisés à être envoyés | `wishlist/email/number_limit` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Limite de longueur du texte d’un email | `wishlist/email/text_limit` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Afficher le résumé des listes de souhaits | `wishlist/wishlist_link/use_qty` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Chemins d’accès des invitations

Ces valeurs de configuration sont disponibles dans l’ Admin de la section **Magasins** > Paramètres > **Configuration** > **Clients** > **Invitations**.

| Nom | Chemin de configuration | Commerce uniquement ? |
|--------------|--------------|--------------|
| Activation de la fonctionnalité d’invitation | `magento_invitation/general/enabled` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Activation des invitations sur Storefront | `magento_invitation/general/enabled_on_front` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Groupe de clients référents | `magento_invitation/general/registration_use_inviter_group` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Nouvelle inscription aux comptes | `magento_invitation/general/registration_required_invitation` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Autoriser les clients à ajouter un message personnalisé à un message d’invitation | `magento_invitation/general/allow_customer_message` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Nombre max. d’invitations autorisées à être envoyées simultanément | `magento_invitation/general/max_invitation_amount_per_send` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Expéditeur du courrier électronique d’invitation du client | `magento_invitation/email/identity` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Modèle de courrier électronique d’invitation du client | `magento_invitation/email/template` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |

{style="table-layout:auto"}

## Chemins de récompense

Ces valeurs de configuration sont disponibles dans l’ Admin de la section **Magasins** > Paramètres > **Configuration** > **Clients** > **Points de récompense**.

| Nom | Chemin de configuration | Commerce uniquement ? |
|--------------|--------------|--------------|
| Activation de la fonctionnalité de points de récompense | `magento_reward/general/is_enabled` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Activation de la fonctionnalité Reward Points sur Storefront | `magento_reward/general/is_enabled_on_front` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Les Clients Peuvent Voir L’Historique Des Points De Remise | `magento_reward/general/publish_history` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Seuil de rétribution du solde des points de récompense | `magento_reward/general/min_points_balance` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Solde des points de récompense max. à | `magento_reward/general/max_points_balance` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Points de récompense Expiration en (jours) | `magento_reward/general/expiration_days` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Calcul de l’expiration des points de récompense | `magento_reward/general/expiry_calculation` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Rembourser automatiquement les points de récompense | `magento_reward/general/refund_automatically` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Déduire automatiquement les points de récompense du montant remboursé | `magento_reward/general/deduct_automatically` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Page d’entrée | `magento_reward/general/landing_page` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Achat | `magento_reward/points/order` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Enregistrement | `magento_reward/points/register` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Inscription à la newsletter | `magento_reward/points/newsletter` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Conversion d’une invitation en client | `magento_reward/points/invitation_customer` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Limite de quantité d’invitation à des conversions client | `magento_reward/points/invitation_customer_limit` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Conversion d’une invitation en commande | `magento_reward/points/invitation_order` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Limite de quantité d’invitation à commander des conversions | `magento_reward/points/invitation_order_limit` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Conversion d’invitation en récompense de commande | `magento_reward/points/invitation_order_frequency` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Vérifier l’envoi | `magento_reward/points/review` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Limite de la quantité d’envoi des révisions récompensées | `magento_reward/points/review_limit` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Expéditeur des emails | `magento_reward/notification/email_sender` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Abonnement des clients par défaut | `magento_reward/notification/subscribe_by_default` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Email de mise à jour de solde | `magento_reward/notification/balance_update_template` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Email d’avertissement d’expiration des points de récompense | `magento_reward/notification/expiry_warning_template` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Avertissement d’expiration avant (jours) | `magento_reward/notification/expiry_day_before` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |

{style="table-layout:auto"}

## Chemins de promotion

Ces valeurs de configuration sont disponibles dans l’ Admin de la section **Magasins** > Paramètres > **Configuration** > **Clients** > **Promotions**.

| Nom | Chemin de configuration | Commerce uniquement ? |
|--------------|--------------|--------------|
| Activer les e-mails de rappel | `promo/magento_reminder/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Fréquence | `promo/magento_reminder/frequency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Intervalle | `promo/magento_reminder/interval` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Minute de l&#39;heure | `promo/magento_reminder/minutes` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Heure de début | `promo/magento_reminder/time` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Nombre maximal de courriers électroniques par exécution | `promo/magento_reminder/limit` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Seuil d’échec d’envoi d’email | `promo/magento_reminder/threshold` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Rappel de l’expéditeur de l’email | `promo/magento_reminder/identity` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Longueur du code | `promo/auto_generated_coupon_codes/length` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Format de code | `promo/auto_generated_coupon_codes/format` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Préfixe de code | `promo/auto_generated_coupon_codes/prefix` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Suffixe de code | `promo/auto_generated_coupon_codes/suffix` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tiret Toutes Les X Caractères | `promo/auto_generated_coupon_codes/dash` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Chemins du registre des cadeaux

Ces valeurs de configuration sont disponibles dans l’ Admin de la section **Magasins** > Paramètres > **Configuration** > **Clients** > **Registre des cadeaux**.

| Nom | Chemin de configuration | Commerce uniquement ? |
|--------------|--------------|--------------|
| Activation du registre des cadeaux | `magento_giftregistry/general/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nombre maximum d&#39;inscrits | `magento_giftregistry/general/max_registrant` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modèle de courrier électronique | `magento_giftregistry/owner_email/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Expéditeur des emails | `magento_giftregistry/owner_email/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modèle de courrier électronique | `magento_giftregistry/sharing_email/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Expéditeur des emails | `magento_giftregistry/sharing_email/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Seuil maximal d’emails envoyés | `magento_giftregistry/sharing_email/send_limit` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modèle de courrier électronique | `magento_giftregistry/update_email/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Expéditeur des emails | `magento_giftregistry/update_email/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Chemins du panier persistants

Ces valeurs de configuration sont disponibles dans l’ Admin de la section **Magasins** > Paramètres > **Configuration** > **Clients** > **Panier persistant**.

| Nom | Chemin de configuration | Commerce uniquement ? |
|--------------|--------------|--------------|
| Activer la persistance | `persistent/options/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Durée de vie de la persistance (secondes) | `persistent/options/lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activez &quot;Mémoriser moi&quot;. | `persistent/options/remember_enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Valeur par défaut &quot;Mémoriser&quot; | `persistent/options/remember_default` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Effacer la persistance lors de la déconnexion | `persistent/options/logout_clear` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Persister le panier | `persistent/options/shopping_cart` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Liste des souhaits persistants | `persistent/options/wishlist` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Persister Les Éléments Récemment Commandés | `persistent/options/recently_ordered` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Persister Les Produits Comparés Actuellement | `persistent/options/compare_current` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Persistance de l’historique de comparaison | `persistent/options/compare_history` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Persister Les Produits Récemment Consultés | `persistent/options/recently_viewed` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Persistance de l’appartenance et de la segmentation du groupe client | `persistent/options/customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}
