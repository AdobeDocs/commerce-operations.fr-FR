---
title: Référence des chemins de configuration du catalogue
description: Découvrez les chemins et les valeurs de configuration du catalogue dans les paramètres d’administration d’Adobe Commerce. Découvrez les options de configuration de la gestion des produits, des catégories et des catalogues.
feature: Configuration, Catalog Management
exl-id: 19451443-228e-437d-a3eb-7dc968b9fb0d
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '845'
ht-degree: 0%

---

# Référence des chemins de configuration du catalogue

Cette section répertorie les noms de variables et les chemins de configuration disponibles pour les options dans Admin sous **Magasins** > Paramètres > **Configuration** > **Catalogue**.

La commande [`magento app:config:dump` écrit &#x200B;](../cli/export-configuration.md) ces valeurs dans le fichier de configuration partagé, `app/etc/config.php`, qui doit se trouver dans le contrôle de code source. Pour remplacer éventuellement des paramètres de configuration ou définir des paramètres sensibles, voir [Utiliser des variables d’environnement pour remplacer des paramètres de configuration](override-config-settings.md#environment-variables). Cette rubrique ne répertorie _pas_ les [valeurs sensibles et spécifiques au système](config-reference-sens.md).

## Chemins d’accès au catalogue

Ces valeurs de configuration sont disponibles dans Admin dans **Magasins** > Paramètres > **Configuration** > **Catalogue** > **Catalogue**.

| Nom | Chemin de configuration | Commerce uniquement ? |
|--------------|--------------|--------------|
| Masque pour le SKU | `catalog/fields_masks/sku` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Masque pour le titre du Meta | `catalog/fields_masks/meta_title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Masque des mots-clés Meta | `catalog/fields_masks/meta_keyword` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Masque de description du Meta | `catalog/fields_masks/meta_description` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mode Liste | `catalog/frontend/list_mode` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Produits par page sur les valeurs autorisées de la grille | `catalog/frontend/grid_per_page_values` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Produits par page sur la valeur par défaut de la grille | `catalog/frontend/grid_per_page` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Produits par page sur la liste des valeurs autorisées | `catalog/frontend/list_per_page_values` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Produits par page sur la liste Valeur par défaut | `catalog/frontend/list_per_page` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Liste des produits Trier par | `catalog/frontend/default_sort_by` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Autoriser tous les produits par page | `catalog/frontend/list_allow_all` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Utiliser une catégorie de catalogue plat | `catalog/frontend/flat_catalog_category` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Utiliser un produit de catalogue plat | `catalog/frontend/flat_catalog_product` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nuanciers par produit | `catalog/frontend/swatches_per_product` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Permettre aux invités de donner leur avis | `catalog/review/allow_guest` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Autoriser l’alerte en cas de modification du prix du produit | `catalog/productalert/allow_price` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modèle d’e-mail d’alerte de prix | `catalog/productalert/email_price_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Autoriser l’alerte lorsque le produit est de nouveau en stock | `catalog/productalert/allow_stock` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modèle d’e-mail d’alerte de stock | `catalog/productalert/email_stock_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Alerter l’expéditeur de l’e-mail | `catalog/productalert/email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Fréquence | `catalog/productalert_cron/frequency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Heure de début | `catalog/productalert_cron/time` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Erreur de l’expéditeur de l’e-mail | `catalog/productalert_cron/error_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modèle d’e-mail d’erreur | `catalog/productalert_cron/error_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Afficher pour la version actuelle | `catalog/recently_products/scope` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nombre de produits récemment consultés par défaut | `catalog/recently_products/viewed_count` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nombre de produits récemment comparés par défaut | `catalog/recently_products/compared_count` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Vidéo de base du démarrage automatique | `catalog/product_video/play_if_base` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Afficher la vidéo associée | `catalog/product_video/show_related` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Redémarrage automatique de la vidéo | `catalog/product_video/video_auto_restart` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Périmètre du prix du catalogue | `catalog/price/scope` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Prix par défaut du produit | `catalog/price/default_product_price` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Afficher le nombre de produits | `catalog/layered_navigation/display_product_count` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Calcul de l&#39;étape de navigation des prix | `catalog/layered_navigation/price_range_calculation` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Étape de navigation de prix par défaut | `catalog/layered_navigation/price_range_step` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Afficher l’intervalle de prix en tant que prix unique | `catalog/layered_navigation/one_price_interval` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nombre maximum d&#39;intervalles de prix | `catalog/layered_navigation/price_range_max_intervals` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Limite de division d&#39;intervalle | `catalog/layered_navigation/interval_division_limit` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Profondeur Maximale | `catalog/navigation/max_depth` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Longueur de requête minimale | `catalog/search/min_query_length` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Longueur de requête maximale | `catalog/search/max_query_length` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Moteur de recherche | `catalog/search/engine` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Délai d’expiration du serveur Solr | `catalog/search/solr_server_timeout` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Mode d’indexation | `catalog/search/engine_commit_mode` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activer les suggestions de recherche | `catalog/search/search_suggestion_enabled` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Nombre de suggestions de recherche | `catalog/search/search_suggestion_count` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Afficher le nombre de résultats pour chaque suggestion | `catalog/search/search_suggestion_count_results_enabled` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Activer les recommandations de recherche | `catalog/search/search_recommendations_enabled` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Nombre de recommandations de recherche | `catalog/search/search_recommendations_count` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Afficher le nombre de résultats pour chaque recommandation | `catalog/search/search_recommendations_count_results_enabled` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Conditions minimales à faire correspondre | `catalog/search/minimum_should_match` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Générer des réécritures d’URL « catégorie/produit » | `catalog/seo/generate_category_product_rewrites` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Termes de recherche populaires | `catalog/seo/search_terms` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Suffixe de l’URL du produit | `catalog/seo/product_url_suffix` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Suffixe d’URL de catégorie | `catalog/seo/category_url_suffix` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Utiliser le chemin d’accès aux catégories pour les URL de produit | `catalog/seo/product_use_categories` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Créer une redirection permanente pour les URL si la clé d’URL a changé | `catalog/seo/save_rewrites_history` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Séparateur de titre de page | `catalog/seo/title_separator` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Utiliser La Balise Meta De Lien Canonique Pour Les Catégories | `catalog/seo/category_canonical_tag` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Utiliser La Balise Meta De Lien Canonique Pour Les Produits | `catalog/seo/product_canonical_tag` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activer | `catalog/magento_catalogpermissions/enabled` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Autoriser la catégorie de navigation | `catalog/magento_catalogpermissions/grant_catalog_category_view` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Groupes de clients | `catalog/magento_catalogpermissions/grant_catalog_category_view_groups` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Page de destination | `catalog/magento_catalogpermissions/restricted_landing_page` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Afficher les prix des produits | `catalog/magento_catalogpermissions/grant_catalog_product_price` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Groupes de clients | `catalog/magento_catalogpermissions/grant_catalog_product_price_groups` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Autoriser l’ajout au panier | `catalog/magento_catalogpermissions/grant_checkout_items` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Groupes de clients | `catalog/magento_catalogpermissions/grant_checkout_items_groups` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Interdire la recherche catalogue par | `catalog/magento_catalogpermissions/deny_catalog_search` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Statut de l’élément de commande pour activer les téléchargements | `catalog/downloadable/order_item_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nombre maximal de téléchargements par défaut | `catalog/downloadable/downloads_number` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Partageable | `catalog/downloadable/shareable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titre d’exemple par défaut | `catalog/downloadable/samples_title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titre du lien par défaut | `catalog/downloadable/links_title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ouvrir les liens dans une nouvelle fenêtre | `catalog/downloadable/links_target_new_window` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Utiliser la disposition du contenu | `catalog/downloadable/content_disposition` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Désactiver le passage en caisse des invités si le panier contient des éléments téléchargeables | `catalog/downloadable/disable_guest_checkout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Utiliser le calendrier JavaScript | `catalog/custom_options/use_calendar` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordre des champs de date | `catalog/custom_options/date_fields_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Format de l’heure | `catalog/custom_options/time_format` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Plage d&#39;années | `catalog/custom_options/year_range` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activer la fonctionnalité d’événements de catalogue | `catalog/magento_catalogevent/enabled` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Activer le widget Événement de catalogue sur Storefront | `catalog/magento_catalogevent/lister_output` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Nombre d’événements à afficher dans le widget de curseur d’événement | `catalog/magento_catalogevent/lister_widget_limit` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Événements à faire défiler par clic dans le widget de curseur d’événement | `catalog/magento_catalogevent/lister_widget_scroll` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Nombre maximal de produits dans la liste des produits associés | `catalog/magento_targetrule/related_position_limit` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Afficher les produits associés | `catalog/magento_targetrule/related_position_behavior` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Mode Rotation des produits dans la liste des produits associés | `catalog/magento_targetrule/related_rotation_mode` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Nombre maximal de produits dans la liste de produits de ventes croisées | `catalog/magento_targetrule/crosssell_position_limit` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Afficher les produits de ventes croisées | `catalog/magento_targetrule/crosssell_position_behavior` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Mode de rotation pour les produits de la liste de produits de ventes croisées | `catalog/magento_targetrule/crosssell_rotation_mode` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Nombre maximal de produits dans la liste de produits de montée en gamme | `catalog/magento_targetrule/upsell_position_limit` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Afficher les produits de montée en gamme | `catalog/magento_targetrule/upsell_position_behavior` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Mode de rotation des produits dans la liste de produits de montée en gamme | `catalog/magento_targetrule/upsell_rotation_mode` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |

{style="table-layout:auto"}

## Chemins d’accès d’inventaire

Ces valeurs de configuration sont disponibles dans Admin dans **Magasins** > Paramètres > **Configuration** > **Catalogue** > **Inventaire**.

| Nom | Chemin de configuration | Commerce uniquement ? |
|--------------|--------------|--------------|
| Diminuer le stock lorsque la commande est passée | `cataloginventory/options/can_subtract` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Définir le statut des articles sur En stock lorsque la commande est annulée | `cataloginventory/options/can_back_in_stock` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Afficher les produits en rupture de stock | `cataloginventory/options/show_out_of_stock` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Seuil de gauche X | `cataloginventory/options/stock_threshold_qty` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Afficher la disponibilité des produits en stock sur Storefront | `cataloginventory/options/display_product_stock_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Synchronisation avec le catalogue | `cataloginventory/options/synchronize_with_catalog` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Gérer les stocks | `cataloginventory/item_options/manage_stock` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Commandes en souffrance | `cataloginventory/item_options/backorders` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Utiliser la mise à jour de Stock différée | `cataloginventory/item_options/use_deferred_stock_update` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Quantité maximale autorisée dans le panier | `cataloginventory/item_options/max_sale_qty` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Seuil de rupture de stock | `cataloginventory/item_options/min_qty` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Qté minimale autorisée dans le panier | `cataloginventory/item_options/min_sale_qty` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Notifier pour la quantité ci-dessous | `cataloginventory/item_options/notify_stock_qty` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activer les incréments de quantité | `cataloginventory/item_options/enable_qty_increments` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Incréments de quantité | `cataloginventory/item_options/qty_increments` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Retourner automatiquement l&#39;avoir en stock | `cataloginventory/item_options/auto_return` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Exécuter de manière asynchrone | `cataloginventory/bulk_operations/async` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Taille de lot asynchrone | `cataloginventory/bulk_operations/batch_size` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Fournisseur | `cataloginventory/source_selection_distance_based/provider` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mode de calcul | `cataloginventory/source_selection_distance_based_google/mode` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Valeur | `cataloginventory/source_selection_distance_based_google/value` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Chemins d’accès visuels du marchandiseur

[!BADGE PaaS uniquement]{type=Informative url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="S’applique uniquement aux projets Adobe Commerce on Cloud (infrastructure PaaS gérée par Adobe) et aux projets On-premise."}

Ces valeurs de configuration sont disponibles dans Admin dans **Magasins** > Paramètres > **Configuration** > **Catalogue** > **Marchandiseur visuel**.

| Nom | Chemin de configuration | Commerce uniquement ? |
|--------------|--------------|--------------|
| Attributs visibles pour les règles de catégorie | `visualmerchandiser/options/smart_attributes` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Seuil Minimal De Stock | `visualmerchandiser/options/minimum_stock_threshold` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Code d’attribut de couleur | `visualmerchandiser/options/color_attribute_code` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |
| Ordre des couleurs | `visualmerchandiser/options/color_order` | ![Commerce uniquement](/help/assets/configuration/cloud-ee.png) |

{style="table-layout:auto"}

## Chemins d’accès au plan de site XML

Ces valeurs de configuration sont disponibles dans Admin dans **Magasins** > Paramètres > **Configuration** > **Catalogue** > **Plan de site XML**.

| Nom | Chemin de configuration | Commerce uniquement ? |
|--------------|--------------|--------------|
| Fréquence | `sitemap/category/changefreq` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Priorité | `sitemap/category/priority` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Fréquence | `sitemap/product/changefreq` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Priorité | `sitemap/product/priority` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ajout d’images au plan de site | `sitemap/product/image_include` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Fréquence | `sitemap/page/changefreq` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Priorité | `sitemap/page/priority` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activé | `sitemap/generate/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Heure de début | `sitemap/generate/time` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Fréquence | `sitemap/generate/frequency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Erreur de l’expéditeur de l’e-mail | `sitemap/generate/error_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modèle d’e-mail d’erreur | `sitemap/generate/error_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nombre maximal d’URL par fichier | `sitemap/limit/max_lines` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Taille de fichier maximale | `sitemap/limit/max_file_size` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activer l’envoi au fichier Robots.txt | `sitemap/search_engines/submission_robots` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Chemins des flux RSS

Ces valeurs de configuration sont disponibles dans Admin dans **Magasins** > Paramètres > **Configuration** > **Catalogue** > **Flux RSS**.

| Nom | Chemin de configuration | Commerce uniquement ? |
|--------------|--------------|--------------|
| Activer RSS | `rss/config/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activer RSS | `rss/wishlist/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nouveaux produits | `rss/catalog/new` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Produits spéciaux | `rss/catalog/special` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Coupons/Remises | `rss/catalog/discounts` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Catégorie de niveau supérieur | `rss/catalog/category` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Notification de statut de la commande client | `rss/order/status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Chemins d’accès vers un e-mail à un ami

Ces valeurs de configuration sont disponibles dans Admin dans **Magasins** > Paramètres > **Configuration** > **Catalogue** > **Envoyer un courrier électronique à un ami**.

| Nom | Chemin de configuration | Commerce uniquement ? |
|--------------|--------------|--------------|
| Activé | `sendfriend/email/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sélectionner le modèle d’e-mail | `sendfriend/email/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Autoriser pour les invités | `sendfriend/email/allow_guest` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Destinataires max. | `sendfriend/email/max_recipients` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nombre maximal de produits envoyés en 1 heure | `sendfriend/email/max_per_hour` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Limiter l’envoi par | `sendfriend/email/check_by` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}
