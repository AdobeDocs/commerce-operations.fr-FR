---
title: Référence des chemins de configuration généraux
description: Découvrez les chemins et valeurs de configuration généraux et avancés d’Adobe Commerce. Découvrez les options de configuration du système, de la sécurité et de l’administration.
feature: Configuration, Observability, Roles/Permissions, System
exl-id: 3c557746-5182-4929-aebf-5b6fe76f0d8f
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '971'
ht-degree: 0%

---

# Référence des chemins de configuration généraux et avancés

Cette rubrique répertorie les chemins de configuration généraux et avancés ainsi que les valeurs _non_ [ sensibles et spécifiques au système](config-reference-sens.md). La commande [`magento app:config:dump` écrit ](../cli/export-configuration.md) ces valeurs dans le fichier de configuration partagé, `app/etc/config.php`, qui doit se trouver dans le contrôle de code source.

Pour remplacer éventuellement des paramètres de configuration ou définir des paramètres sensibles, voir [Utiliser des variables d’environnement pour remplacer des paramètres de configuration](override-config-settings.md#environment-variables).

## Catégorie générale

Cette section répertorie les noms de variables et les chemins de configuration disponibles pour les options dans Admin sous **Magasins** > Paramètres > **Configuration** > **Général**.

### Chemins généraux

Ces valeurs de configuration sont disponibles dans Admin dans **Magasins** > Paramètres > **Configuration** > Général > **Général**.

| Nom | Chemin de configuration | Commerce uniquement ? | Sensible ? |
|--------------|--------------|--------------|--------------|
| Pays par défaut | `general/country/default` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![ Sensible ](/help/assets/configuration/cloud-sens.png) |
| Autoriser les pays | `general/country/allow` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![ Sensible ](/help/assets/configuration/cloud-sens.png) |
| Le code postal est facultatif pour | `general/country/optional_zip_countries` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![ Sensible ](/help/assets/configuration/cloud-sens.png) |
| Pays de l&#39;Union européenne | `general/country/eu_countries` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![ Sensible ](/help/assets/configuration/cloud-sens.png) |
| Destinations principales | `general/country/destinations` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| L’état est requis pour | `general/region/state_required` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Autoriser à choisir l’état s’il est facultatif pour le pays | `general/region/display_all` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | |
| Fuseau horaire | `general/locale/timezone` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | |
| Locale | `general/locale/code` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | |
| Unité De Poids | `general/locale/weight_unit` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | |
| Premier jour de la semaine | `general/locale/firstday` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | |
| Jours de week-end | `general/locale/weekend` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | |
| Restriction d’accès | `general/restriction/is_active` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) | |
| Mode de restriction | `general/restriction/mode` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) | |
| Page de démarrage | `general/restriction/http_redirect` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) | |
| Page de destination | `general/restriction/cms_page` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) | |
| Réponse HTTP | `general/restriction/http_status` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) | |
| Nom de la boutique | `general/store_information/name` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | |
| Numéro de téléphone de la boutique | `general/store_information/phone` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | |
| Stocker les heures d&#39;ouverture | `general/store_information/hours` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | |
| Pays | `general/store_information/country_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | |
| Région/État | `general/store_information/region_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | |
| Code postal | `general/store_information/postcode` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | |
| Ville | `general/store_information/city` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | |
| Adresse Postale | `general/store_information/street_line1` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | |
| Adresse postale Ligne 2 | `general/store_information/street_line2` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | |
| Numéro de TVA | `general/store_information/merchant_vat_number` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | |
| Activer le mode de magasin unique | `general/single_store_mode/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | |

{style="table-layout:auto"}

### Chemins web

Ces valeurs de configuration sont disponibles dans Admin dans **Magasins** > Paramètres > **Configuration** > **Général** > **Web**.

| Nom | Chemin de configuration | Commerce uniquement ? |
|--------------|--------------|--------------|
| Ajout du code de magasin aux URL | `web/url/use_store` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Redirection automatique vers l’URL de base | `web/url/redirect_to_base` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Utiliser les réécritures du serveur Web | `web/seo/use_rewrites` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Utiliser des URL sécurisées sur Storefront | `web/secure/use_in_frontend` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Utiliser des URL sécurisées dans l’administration | `web/secure/use_in_adminhtml` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activer HTTP Strict Transport Security (HSTS) | `web/secure/enable_hsts` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mettre à niveau les demandes non sécurisées | `web/secure/enable_upgrade_insecure` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| En-tête du déchargeur | `web/secure/offloader_header` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Page d’accueil de CMS | `web/default/cms_home_page` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Page CMS sans itinéraire | `web/default/cms_no_route` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Page CMS sans cookies | `web/default/cms_no_cookies` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Afficher le chemin de navigation pour les pages CMS | `web/default/show_cms_breadcrumbs` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Durée de vie du cookie | `web/cookie/cookie_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Utiliser HTTP uniquement | `web/cookie/cookie_httponly` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mode de restriction des cookies | `web/cookie/cookie_restriction` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Validate REMOTE_ADDR | `web/session/use_remote_addr` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Valider HTTP_VIA | `web/session/use_http_via` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Valider HTTP_X_FORWARDED_FOR | `web/session/use_http_x_forwarded_for` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Valider HTTP_USER_AGENT | `web/session/use_http_user_agent` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Utiliser le SID sur Storefront | `web/session/use_frontend_sid` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Rediriger vers la page CMS si les cookies sont désactivés | `web/browser_capabilities/cookies` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Afficher une notification si JavaScript est désactivé | `web/browser_capabilities/javascript` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Afficher une notification si le stockage local est désactivé | `web/browser_capabilities/local_storage` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

### Chemins de configuration des devises

Ces valeurs de configuration sont disponibles dans Admin dans **Magasins** > Paramètres > **Configuration** > **Général** > **Configuration de la devise**.

| Nom | Chemin de configuration | Commerce uniquement ? |
|--------------|--------------|--------------|
| Devise de base | `currency/options/base` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Devise d’affichage par défaut | `currency/options/default` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Devises autorisées | `currency/options/allow` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Yahoo Finance Exchange | `TBD` | |
| Fixer.io | `TBD` | |
| Webservices | `TBD` | |
| Timeout de connexion en secondes | `currency/yahoofinance/timeout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Timeout de connexion en secondes | `currency/fixerio/timeout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Timeout de connexion en secondes | `currency/webservicex/timeout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activé | `currency/import/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Service | `currency/import/service` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Heure de début | `currency/import/time` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Fréquence | `currency/import/frequency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Destinataire de l’e-mail d’erreur | `currency/import/error_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Erreur de l’expéditeur de l’e-mail | `currency/import/error_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modèle d’e-mail d’erreur | `currency/import/error_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

### Chemins des contacts

Ces valeurs de configuration sont disponibles dans Admin dans **Magasins** > Paramètres > **Configuration** > **Général** > **Contacts**.

| Nom | Chemin de configuration | Commerce uniquement ? |
|--------------|--------------|--------------|
| Activer Nous Contacter | `contact/contact/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Envoyer Des E-Mails À | `contact/email/recipient_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Expéditeur de l’e-mail | `contact/email/sender_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modèle d’e-mail | `contact/email/email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

### Chemins d’accès aux rapports

Ces valeurs de configuration sont disponibles dans Admin dans **Magasins** > Paramètres > **Configuration** > **Général** > **Rapports**.

| Nom | Chemin de configuration | Commerce uniquement ? |
|--------------|--------------|--------------|
| Cumul Annuel Commence | `reports/dashboard/ytd_start` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mois en cours commence | `reports/dashboard/mtd_start` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

### Chemins de gestion de contenu

Ces valeurs de configuration sont disponibles dans Admin dans **Magasins** > Paramètres > **Configuration** > **Général** > **Gestion de contenu**.

| Nom | Chemin de configuration | Commerce uniquement ? |
|--------------|--------------|--------------|
| Activation de l’éditeur WYSIWYG | `cms/wysiwyg/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Utilisation d’URL statiques pour le contenu multimédia dans WYSIWYG for Catalog | `cms/wysiwyg/use_static_urls_in_catalog` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activer la fonctionnalité de hiérarchie | `cms/hierarchy/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activer les métadonnées de hiérarchie | `cms/hierarchy/metadata_enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mise en page par défaut du menu Hiérarchie | `cms/hierarchy/menu_layout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

### Chemins de création de rapports New Relic

Ces valeurs de configuration sont disponibles dans Admin dans **Magasins** > Paramètres > **Configuration** > **Général** > **Rapports New Relic**.

| Nom | Chemin de configuration | Commerce uniquement ? |
|--------------|--------------|--------------|
| Activer l’intégration de New Relic | `newrelicreporting/general/enable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nom de l’application New Relic | `newrelicreporting/general/app_name` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activer cron | `newrelicreporting/cron/enable_cron` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Catégorie avancée

Cette section répertorie les noms de variables et les chemins de configuration disponibles pour les options dans Admin sous **Magasins** > Paramètres > **Configuration** > **Avancé**.

### Chemins d’accès admin

Ces valeurs de configuration sont disponibles dans Admin dans **Magasins** > Paramètres > **Configuration** > **Avancé** > **Admin**.

| Nom | Chemin de configuration | Commerce uniquement ? |
|--------------|--------------|--------------|
| Modèle d’e-mail de mot de passe oublié | `admin/emails/forgot_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Expéditeur d’e-mail oublié et réinitialisé | `admin/emails/forgot_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modèle de notification de l’utilisateur | `admin/emails/user_notification_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Page de démarrage | `admin/startup/menu_item_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Utiliser une URL d’administration personnalisée | `admin/url/use_custom` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Utiliser le chemin d’accès d’administration personnalisé | `admin/url/use_custom_path` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Partage de compte d’administrateur | `admin/security/admin_account_sharing` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Type de protection contre la réinitialisation du mot de passe | `admin/security/password_reset_protection_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Délai d&#39;expiration du lien de récupération (heures) | `admin/security/password_reset_link_expiration_period` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nbre max. de demandes de réinitialisation de mot de passe | `admin/security/max_number_password_reset_requests` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Durée Minimale Entre Les Demandes De Réinitialisation De Mot De Passe | `admin/security/min_time_between_password_reset_requests` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ajout d’une clé secrète aux URL | `admin/security/use_form_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| La connexion respecte la casse. | `admin/security/use_case_sensitive_login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Durée de vie de la session d&#39;administrateur (secondes) | `admin/security/session_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nombre maximal d’échecs de connexion au compte de verrouillage | `admin/security/lockout_failures` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Durée du verrouillage (minutes) | `admin/security/lockout_threshold` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Durée de vie du mot de passe (jours) | `admin/security/password_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Changement de mot de passe | `admin/security/password_is_forced` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activer les graphiques | `admin/dashboard/enable_charts` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activer CAPTCHA dans l’administration | `admin/captcha/enable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Police | `admin/captcha/font` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Forms | `admin/captcha/forms` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mode d’affichage | `admin/captcha/mode` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nombre de tentatives de connexion ayant échoué | `admin/captcha/failed_attempts_login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Délai d’expiration de CAPTCHA (minutes) | `admin/captcha/timeout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nombre de symboles | `admin/captcha/length` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Symboles utilisés dans CAPTCHA | `admin/captcha/symbols` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Respect De La Casse | `admin/captcha/case_sensitive` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Actions activées | `admin/magento_logging/actions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

### Chemins système

Ces valeurs de configuration sont disponibles dans Admin dans **Magasins** > Paramètres > **Configuration** > **Avancé** > **Système**.

| Nom | Chemin de configuration | Commerce uniquement ? |
|--------------|--------------|--------------|
| Durée De Vie Des Messages Réussis | `system/mysqlmq/successful_messages_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Réessayer les messages en cours après | `system/mysqlmq/retry_inprogress_after` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Durée de vie des messages en échec | `system/mysqlmq/failed_messages_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Durée de vie des nouveaux messages | `system/mysqlmq/new_messages_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Générer des planifications toutes les | `system/cron/index/schedule_generate_every` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Planifier en avance pour | `system/cron/index/schedule_ahead_for` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ignoré si non exécuté dans | `system/cron/index/schedule_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nettoyage de l’historique tous les | `system/cron/index/history_cleanup_every` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Durée de vie de l’historique de succès | `system/cron/index/history_success_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Durée de vie de l’historique des échecs | `system/cron/index/history_failure_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Utiliser un processus distinct | `system/cron/index/use_separate_process` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Générer des planifications toutes les | `system/cron/default/schedule_generate_every` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Planifier en avance pour | `system/cron/default/schedule_ahead_for` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ignoré si non exécuté dans | `system/cron/default/schedule_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nettoyage de l’historique tous les | `system/cron/default/history_cleanup_every` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Durée de vie de l’historique de succès | `system/cron/default/history_success_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Durée de vie de l’historique des échecs | `system/cron/default/history_failure_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Générer des planifications toutes les | `system/cron/staging/schedule_generate_every` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Planifier en avance pour | `system/cron/staging/schedule_ahead_for` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Ignoré si non exécuté dans | `system/cron/staging/schedule_lifetime` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Nettoyage de l’historique tous les | `system/cron/staging/history_cleanup_every` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Durée de vie de l’historique de succès | `system/cron/staging/history_success_lifetime` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Durée de vie de l’historique des échecs | `system/cron/staging/history_failure_lifetime` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Utiliser un processus distinct | `system/cron/staging/use_separate_process` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Générer des planifications toutes les | `system/cron/catalog/event/schedule_generate_every` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Planifier en avance pour | `system/cron/catalog/event/schedule_ahead_for` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Ignoré si non exécuté dans | `system/cron/catalog/event/schedule_lifetime` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Nettoyage de l’historique tous les | `system/cron/catalog/event/history_cleanup_every` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Durée de vie de l’historique de succès | `system/cron/catalog/event/history_success_lifetime` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Durée de vie de l’historique des échecs | `system/cron/catalog/event/history_failure_lifetime` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Utiliser un processus distinct | `system/cron/catalog/event/use_separate_process` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Utiliser un processus distinct | `system/cron/default/use_separate_process` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Désactiver les communications par e-mail | `system/smtp/disable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Définir le chemin de retour | `system/smtp/set_return_path` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-Mail De Retour | `system/smtp/return_path_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Devises installées | `system/currency/installed` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Utiliser HTTPS pour obtenir le flux | `system/adminnotification/use_https` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Fréquence de mise à jour | `system/adminnotification/frequency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Dernière mise à jour | `system/adminnotification/last_update` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activer la sauvegarde planifiée | `system/backup/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Type de sauvegarde | `system/backup/type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Heure de début | `system/backup/time` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Fréquence | `system/backup/frequency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mode de maintenance | `system/backup/maintenance` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Durée De Vie De L&#39;Entrée Du Journal, Jours | `system/rotation/lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Fréquence D’Archivage Des Journaux | `system/rotation/frequency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Application de mise en cache | `system/full_page_cache/caching_application` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| TTL pour le contenu public | `system/full_page_cache/ttl` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Délai de grâce | `system/full_page_cache/varnish/grace_period` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Exporter la configuration | `system/full_page_cache/varnish/export_button_version4` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Jours enregistrés dans le journal | `system/bulk/lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stockage multimédia | `system/media_storage_configuration/media_storage` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sélectionner la base de données des médias | `system/media_storage_configuration/media_database` (obsolète dans Commerce 2.4.3) | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Heure de mise à jour de l’environnement | `system/media_storage_configuration/configuration_update_time` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enregistrer les fichiers, jours | `system/magento_scheduled_import_export_log/save_days` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activer le nettoyage planifié de l’historique des fichiers | `system/magento_scheduled_import_export_log/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Heure de début | `system/magento_scheduled_import_export_log/time` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Fréquence | `system/magento_scheduled_import_export_log/frequency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modèle d’e-mail d’erreur | `system/magento_scheduled_import_export_log/error_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

### Chemins du développeur

Ces valeurs de configuration sont disponibles dans Admin dans **Magasins** > Paramètres > **Configuration** > **Avancé** > **Développeur**.

| Nom | Chemin de configuration | Commerce uniquement ? |
|--------------|--------------|--------------|
| Type de workflow | `dev/front_end_development_workflow/type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Autoriser les liens symboliques | `dev/template/allow_symlink` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Minimiser Le Code Html | `dev/template/minify_html` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activer les conseils de chemin d’accès du modèle pour Storefront | `dev/debug/template_hints_storefront` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activer les conseils de chemin d’accès du modèle pour l’administrateur | `dev/debug/template_hints_admin` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ajouter des noms de bloc aux conseils | `dev/debug/template_hints_blocks` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Consigner dans un fichier | `dev/debug/debug_logging` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Consigner dans syslog | `dev/syslog/syslog_logging` |  |
| Activé pour Storefront | `dev/translate_inline/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activé pour l’administrateur | `dev/translate_inline/active_admin` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Fusion de fichiers JavaScript | `dev/js/merge_files` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activer le regroupement JavaScript | `dev/js/enable_js_bundling` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Minimisation des fichiers JavaScript | `dev/js/minify_files` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stratégie de traduction | `dev/js/translate_strategy` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Consigner les erreurs JS dans le stockage de session | `dev/js/session_storage_logging` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Fusion de fichiers CSS | `dev/css/merge_css_files` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Minimiser les fichiers CSS | `dev/css/minify_files` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Adaptateur d&#39;image | `dev/image/default_adapter` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Signer des fichiers statiques | `dev/static/sign` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Indexation asynchrone | `dev/grid/async_indexing` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mettre en cache les attributs définis par l&#39;utilisateur | `dev/caching/cache_user_defined_attributes` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}
