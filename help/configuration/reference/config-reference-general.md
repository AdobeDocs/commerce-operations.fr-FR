---
title: Référence générale sur les chemins de configuration
description: Consultez la liste des valeurs de configuration générales et avancées.
feature: Configuration, Observability, Roles/Permissions, System
exl-id: 3c557746-5182-4929-aebf-5b6fe76f0d8f
source-git-commit: 16e9396f19693436dfc7bdac78d84624a78f0c21
workflow-type: tm+mt
source-wordcount: '965'
ht-degree: 0%

---

# Référence sur les chemins de configuration généraux et avancés

Cette rubrique répertorie les chemins de configuration généraux et avancés et _not_ [valeurs sensibles et spécifiques au système](config-reference-sens.md). Le [`magento app:config:dump` command](../cli/export-configuration.md) écrit ces valeurs dans le fichier de configuration partagé, `app/etc/config.php`, qui doit être dans le contrôle de code source.

Pour éventuellement remplacer des paramètres de configuration ou définir des paramètres sensibles, voir [Utilisation des variables d’environnement pour remplacer les paramètres de configuration](override-config-settings.md#environment-variables).

## Catégorie générale

Cette section répertorie les noms de variable et les chemins de configuration disponibles pour les options dans l’Admin sous **Magasins** > Paramètres > **Configuration** > **Général**.

### Chemins généraux

Ces valeurs de configuration sont disponibles dans l’ Admin de **Magasins** > Paramètres > **Configuration** > Général > **Général**.

| Nom | Chemin de configuration | Commerce uniquement ? | Sensibles ? |
|--------------|--------------|--------------|--------------|
| Pays par défaut | `general/country/default` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Sensibilité](/help/assets/configuration/cloud-sens.png) |
| Autoriser les pays | `general/country/allow` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Sensibilité](/help/assets/configuration/cloud-sens.png) |
| Le code postal est facultatif pour les | `general/country/optional_zip_countries` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Sensibilité](/help/assets/configuration/cloud-sens.png) |
| Pays de l’Union européenne | `general/country/eu_countries` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Sensibilité](/help/assets/configuration/cloud-sens.png) |
| Destinations principales | `general/country/destinations` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| L’état est requis pour | `general/region/state_required` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Autoriser l’état s’il est facultatif pour le pays | `general/region/display_all` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |
| Fuseau horaire | `general/locale/timezone` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |
| Paramètres régionaux | `general/locale/code` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |
| Unité de poids | `general/locale/weight_unit` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |
| Premier jour de la semaine | `general/locale/firstday` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |
| Jours de week-end | `general/locale/weekend` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |
| Restriction d’accès | `general/restriction/is_active` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |  |
| Mode Restriction | `general/restriction/mode` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |  |
| Page de démarrage | `general/restriction/http_redirect` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |  |
| Page d’entrée | `general/restriction/cms_page` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |  |
| Réponse HTTP | `general/restriction/http_status` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |  |
| Nom de la boutique | `general/store_information/name` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |
| Numéro de téléphone du magasin | `general/store_information/phone` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |
| Heures d’ouverture du magasin | `general/store_information/hours` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |
| Pays | `general/store_information/country_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |
| Région/état | `general/store_information/region_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |
| Code postal | `general/store_information/postcode` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |
| Ville | `general/store_information/city` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |
| Adresse postale | `general/store_information/street_line1` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |
| Ligne d’adresse 2 de rue | `general/store_information/street_line2` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |
| Numéro TVA | `general/store_information/merchant_vat_number` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |
| Activation du mode Boutique unique | `general/single_store_mode/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |

{style="table-layout:auto"}

### Chemins Web

Ces valeurs de configuration sont disponibles dans l’ Admin de **Magasins** > Paramètres > **Configuration** > **Général** > **Web**.

| Nom | Chemin de configuration | Commerce uniquement ? |
|--------------|--------------|--------------|
| Ajout de code de magasin aux URL | `web/url/use_store` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Redirection automatique vers l’URL de base | `web/url/redirect_to_base` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Utiliser les réécritures de serveur web | `web/seo/use_rewrites` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Utilisation d’URL sécurisées sur Storefront | `web/secure/use_in_frontend` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Utilisation d’URL sécurisées dans l’administrateur | `web/secure/use_in_adminhtml` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activation de HTTP Strict Transport Security (HSTS) | `web/secure/enable_hsts` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mettre à niveau les requêtes non sécurisées | `web/secure/enable_upgrade_insecure` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| En-tête de déchargement | `web/secure/offloader_header` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Page d’accueil du CMS | `web/default/cms_home_page` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| CMS No Route Page | `web/default/cms_no_route` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Page Aucun cookie CMS | `web/default/cms_no_cookies` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Afficher le chemin de navigation des pages CMS | `web/default/show_cms_breadcrumbs` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Durée de vie du cookie | `web/cookie/cookie_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Utiliser HTTP uniquement | `web/cookie/cookie_httponly` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mode de restriction des cookies | `web/cookie/cookie_restriction` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Validation de REMOTE_ADDR | `web/session/use_remote_addr` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Validation de HTTP_VIA | `web/session/use_http_via` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Validation de HTTP_X_FORWARDED_FOR | `web/session/use_http_x_forwarded_for` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Validation de HTTP_USER_AGENT | `web/session/use_http_user_agent` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Utilisation du SID sur Storefront | `web/session/use_frontend_sid` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Redirection vers la page CMS si les cookies sont désactivés | `web/browser_capabilities/cookies` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Afficher l’avis si JavaScript est désactivé | `web/browser_capabilities/javascript` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Afficher l’avis si le stockage local est désactivé | `web/browser_capabilities/local_storage` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

### Chemins de configuration des devises

Ces valeurs de configuration sont disponibles dans l’ Admin de **Magasins** > Paramètres > **Configuration** > **Général** > **Configuration des devises**.

| Nom | Chemin de configuration | Commerce uniquement ? |
|--------------|--------------|--------------|
| Devise de base | `currency/options/base` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Devise d’affichage par défaut | `currency/options/default` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Devises autorisées | `currency/options/allow` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Yahoo Finance Exchange | `TBD` |  |
| Fixer.io | `TBD` |  |
| Webservicex | `TBD` |  |
| Timeout de connexion en secondes | `currency/yahoofinance/timeout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Timeout de connexion en secondes | `currency/fixerio/timeout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Timeout de connexion en secondes | `currency/webservicex/timeout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activé | `currency/import/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Service | `currency/import/service` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Heure de début | `currency/import/time` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Fréquence | `currency/import/frequency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Error Email Recipient | `currency/import/error_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Error Email Sender | `currency/import/error_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modèle de courrier électronique d’erreur | `currency/import/error_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

### Chemins des contacts

Ces valeurs de configuration sont disponibles dans l’ Admin de **Magasins** > Paramètres > **Configuration** > **Général** > **Contacts**.

| Nom | Chemin de configuration | Commerce uniquement ? |
|--------------|--------------|--------------|
| Activer les contacts | `contact/contact/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Envoyer des emails à | `contact/email/recipient_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Expéditeur des emails | `contact/email/sender_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modèle de courrier électronique | `contact/email/email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

### Chemins des rapports

Ces valeurs de configuration sont disponibles dans l’ Admin de **Magasins** > Paramètres > **Configuration** > **Général** > **Rapports**.

| Nom | Chemin de configuration | Commerce uniquement ? |
|--------------|--------------|--------------|
| Démarrages d’année à date | `reports/dashboard/ytd_start` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Démarrages du mois en cours | `reports/dashboard/mtd_start` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

### Chemins de gestion de contenu

Ces valeurs de configuration sont disponibles dans l’ Admin de **Magasins** > Paramètres > **Configuration** > **Général** > **Gestion de contenu**.

| Nom | Chemin de configuration | Commerce uniquement ? |
|--------------|--------------|--------------|
| Activation de WYSIWYG Editor | `cms/wysiwyg/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Utilisation d’URL statiques pour le contenu multimédia dans WYSIWYG pour le catalogue | `cms/wysiwyg/use_static_urls_in_catalog` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activation de la fonctionnalité de hiérarchie | `cms/hierarchy/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activation des métadonnées de hiérarchie | `cms/hierarchy/metadata_enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Disposition par défaut du menu Hiérarchie | `cms/hierarchy/menu_layout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

### Chemins de création de rapports New Relic

Ces valeurs de configuration sont disponibles dans l’ Admin de **Magasins** > Paramètres > **Configuration** > **Général** > **Rapports New Relic**.

| Nom | Chemin de configuration | Commerce uniquement ? |
|--------------|--------------|--------------|
| Activation de l’intégration New Relic | `newrelicreporting/general/enable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nom de l’application New Relic | `newrelicreporting/general/app_name` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activer Cron | `newrelicreporting/cron/enable_cron` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Catégorie avancée

Cette section répertorie les noms de variable et les chemins de configuration disponibles pour les options dans l’Admin sous **Magasins** > Paramètres > **Configuration** > **Avancé**.

### Chemins d’accès des administrateurs

Ces valeurs de configuration sont disponibles dans l’ Admin de **Magasins** > Paramètres > **Configuration** > **Avancé** > **Administration**.

| Nom | Chemin de configuration | Commerce uniquement ? |
|--------------|--------------|--------------|
| Modèle de courrier électronique avec mot de passe oublié | `admin/emails/forgot_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Expéditeur d’email oublié et réinitialisé | `admin/emails/forgot_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modèle de notification utilisateur | `admin/emails/user_notification_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Page de démarrage | `admin/startup/menu_item_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Utiliser l’URL d’administration personnalisée | `admin/url/use_custom` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Utiliser le chemin d’accès d’administrateur personnalisé | `admin/url/use_custom_path` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Partage des comptes d’administrateur | `admin/security/admin_account_sharing` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Type de protection de réinitialisation de mot de passe | `admin/security/password_reset_protection_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Période d’expiration du lien de récupération (heures) | `admin/security/password_reset_link_expiration_period` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nombre max. de demandes de réinitialisation de mot de passe | `admin/security/max_number_password_reset_requests` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Durée min. entre les demandes de réinitialisation de mot de passe | `admin/security/min_time_between_password_reset_requests` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ajout d’une clé secrète aux URL | `admin/security/use_form_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| La connexion est sensible à la casse | `admin/security/use_case_sensitive_login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Durée de vie de la session d’administration (secondes) | `admin/security/session_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nombre maximal d’échecs de connexion pour verrouiller le compte | `admin/security/lockout_failures` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Durée du verrouillage (minutes) | `admin/security/lockout_threshold` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Durée de vie du mot de passe (jours) | `admin/security/password_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modification de mot de passe | `admin/security/password_is_forced` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activation des graphiques | `admin/dashboard/enable_charts` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activation de CAPTCHA dans l’administrateur | `admin/captcha/enable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Police | `admin/captcha/font` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Forms | `admin/captcha/forms` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mode d’affichage | `admin/captcha/mode` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nombre de tentatives infructueuses de connexion | `admin/captcha/failed_attempts_login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Délai d’expiration CAPTCHA (minutes) | `admin/captcha/timeout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nombre de symboles | `admin/captcha/length` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Symboles utilisés dans CAPTCHA | `admin/captcha/symbols` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Respect de la casse | `admin/captcha/case_sensitive` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Actions activées | `admin/magento_logging/actions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

### Chemins système

Ces valeurs de configuration sont disponibles dans l’ Admin de **Magasins** > Paramètres > **Configuration** > **Avancé** > **Système**.

| Nom | Chemin de configuration | Commerce uniquement ? |
|--------------|--------------|--------------|
| Durée de vie des messages réussis | `system/mysqlmq/successful_messages_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Réessayer Les Messages En Cours Après | `system/mysqlmq/retry_inprogress_after` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Durée de vie des messages en échec | `system/mysqlmq/failed_messages_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Durée de vie des nouveaux messages | `system/mysqlmq/new_messages_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Générer des planifications toutes les | `system/cron/index/schedule_generate_every` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Prévision pour | `system/cron/index/schedule_ahead_for` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Absente si non exécutée dans | `system/cron/index/schedule_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nettoyage de l’historique tous les | `system/cron/index/history_cleanup_every` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Durée de vie de l’historique de succès | `system/cron/index/history_success_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Durée de vie de l’historique des échecs | `system/cron/index/history_failure_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Utilisation d’un processus distinct | `system/cron/index/use_separate_process` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Générer des planifications toutes les | `system/cron/default/schedule_generate_every` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Prévision pour | `system/cron/default/schedule_ahead_for` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Absente si non exécutée dans | `system/cron/default/schedule_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nettoyage de l’historique tous les | `system/cron/default/history_cleanup_every` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Durée de vie de l’historique de succès | `system/cron/default/history_success_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Durée de vie de l’historique des échecs | `system/cron/default/history_failure_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Générer des planifications toutes les | `system/cron/staging/schedule_generate_every` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Prévision pour | `system/cron/staging/schedule_ahead_for` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Absente si non exécutée dans | `system/cron/staging/schedule_lifetime` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Nettoyage de l’historique tous les | `system/cron/staging/history_cleanup_every` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Durée de vie de l’historique de succès | `system/cron/staging/history_success_lifetime` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Durée de vie de l’historique des échecs | `system/cron/staging/history_failure_lifetime` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Utilisation d’un processus distinct | `system/cron/staging/use_separate_process` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Générer des planifications toutes les | `system/cron/catalog/event/schedule_generate_every` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Prévision pour | `system/cron/catalog/event/schedule_ahead_for` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Absente si non exécutée dans | `system/cron/catalog/event/schedule_lifetime` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Nettoyage de l’historique tous les | `system/cron/catalog/event/history_cleanup_every` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Durée de vie de l’historique de succès | `system/cron/catalog/event/history_success_lifetime` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Durée de vie de l’historique des échecs | `system/cron/catalog/event/history_failure_lifetime` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Utilisation d’un processus distinct | `system/cron/catalog/event/use_separate_process` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Utilisation d’un processus distinct | `system/cron/default/use_separate_process` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Désactiver les communications par courrier électronique | `system/smtp/disable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Définir Return-Path | `system/smtp/set_return_path` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Return-Path Email | `system/smtp/return_path_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Devises installées | `system/currency/installed` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Utilisation de HTTPS pour obtenir un flux | `system/adminnotification/use_https` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Fréquence de mise à jour | `system/adminnotification/frequency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Dernière mise à jour | `system/adminnotification/last_update` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activation de la sauvegarde planifiée | `system/backup/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Type de sauvegarde | `system/backup/type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Heure de début | `system/backup/time` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Fréquence | `system/backup/frequency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mode de maintenance | `system/backup/maintenance` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Durée de vie de l’entrée de journal, jours | `system/rotation/lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Fréquence d&#39;archivage des logs | `system/rotation/frequency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mise en cache des applications | `system/full_page_cache/caching_application` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| TTL pour le contenu public | `system/full_page_cache/ttl` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Période de grâce | `system/full_page_cache/varnish/grace_period` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Configuration d’exportation | `system/full_page_cache/varnish/export_button_version4` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Jours enregistrés dans le journal | `system/bulk/lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stockage multimédia | `system/media_storage_configuration/media_storage` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sélectionner la base de données multimédia | `system/media_storage_configuration/media_database` (obsolète dans Commerce 2.4.3) | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Heure de mise à jour de l’environnement | `system/media_storage_configuration/configuration_update_time` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enregistrer les fichiers, jours | `system/magento_scheduled_import_export_log/save_days` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activer le nettoyage de l’historique des fichiers planifiés | `system/magento_scheduled_import_export_log/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Heure de début | `system/magento_scheduled_import_export_log/time` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Fréquence | `system/magento_scheduled_import_export_log/frequency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modèle de courrier électronique d’erreur | `system/magento_scheduled_import_export_log/error_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

### Chemins de développement

Ces valeurs de configuration sont disponibles dans l’ Admin de **Magasins** > Paramètres > **Configuration** > **Avancé** > **Développeur**.

| Nom | Chemin de configuration | Commerce uniquement ? |
|--------------|--------------|--------------|
| Type de workflow | `dev/front_end_development_workflow/type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Autoriser les liens | `dev/template/allow_symlink` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Minimiser Le Code Html | `dev/template/minify_html` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activation des conseils de chemin de modèle pour Storefront | `dev/debug/template_hints_storefront` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activation des conseils sur les chemins de modèle pour l’administrateur | `dev/debug/template_hints_admin` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ajout de noms de bloc à des conseils | `dev/debug/template_hints_blocks` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Log to File | `dev/debug/debug_logging` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Connexion à syslog | `dev/syslog/syslog_logging` |  |
| Activé pour Storefront | `dev/translate_inline/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activé pour l’administrateur | `dev/translate_inline/active_admin` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Fusionner les fichiers JavaScript | `dev/js/merge_files` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activation de la collecte JavaScript | `dev/js/enable_js_bundling` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Minimisation des fichiers JavaScript | `dev/js/minify_files` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stratégie de traduction | `dev/js/translate_strategy` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enregistrer les erreurs JS dans le stockage de session | `dev/js/session_storage_logging` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Fusionner les fichiers CSS | `dev/css/merge_css_files` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Minimisation des fichiers CSS | `dev/css/minify_files` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Adaptateur d’image | `dev/image/default_adapter` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Signature de fichiers statiques | `dev/static/sign` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Indexation asynchrone | `dev/grid/async_indexing` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Attributs définis par l’utilisateur du cache | `dev/caching/cache_user_defined_attributes` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}
