---
source-git-commit: 78a34dc069a30b72a1e0baff36085a2458a05983
workflow-type: tm+mt
source-wordcount: '10868'
ht-degree: 0%
---
# Problèmes résolus dans Adobe Commerce (v2.4.10-alpha1)

## Correction de problèmes dans v2.4.10-alpha1

Nous avons corrigé 169 problèmes dans le code principal 2.4.10-alpha1 d’Adobe Commerce. Un sous-ensemble des problèmes résolus inclus dans cette version est décrit ci-dessous.

### API

#### [Problème] TypeError dans Creditmemo\Validation\QuantityValidator causée par min() avec la quantité de chaîne

Pour stabiliser les pipelines de journalisation financière et empêcher les échecs de requête d&#39;API lors des remboursements de commande automatisés en masse, des mécanismes de sécurisation de conversion de type de données ont été ajoutés aux couches de fabrique et de validation des avoirs de vente internes.

_AC-16056 - [Problème GitHub](https://github.com/magento/magento2/issues/40302) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/40429) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/40303)_

#### La mise à jour des attributs de l’API REST échoue sans attribute_id

Correction d’un problème en raison duquel la mise à jour d’un attribut de produit existant via l’API REST échouait lorsque attribute_id n’était pas fourni. L’API identifie désormais correctement l’attribut à l’aide de la variable attribute_code de l’URL et le met à jour avec succès.

_AC-16424 - [Problème GitHub](https://github.com/magento/magento2/issues/40458) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/c10554e1)_

#### Afficher une erreur d’authentification lorsque les informations d’identification Adobe Stock ne sont pas valides

Les administrateurs voient désormais une erreur d’authentification lorsque les informations d’identification Adobe Stock ne sont pas valides.

_AC-17123_

#### L’échantillon visuel est supprimé lors de la mise à jour de l’option via l’API REST

Pour protéger l’intégrité des données du catalogue et rationaliser les intégrations automatisées, un bug a été résolu dans la couche de gestion d’échantillons EAV où les valeurs d’échantillon visuelles ou textuelles existantes étaient effacées par inadvertance lors des mises à jour des options standard.

_AC-9199 - [Problème GitHub](https://github.com/magento/magento2/issues/37794) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/40872)_

#### L’API de prix de niveau en masse échoue pour un lot entier lorsqu’un SKU est manquant

Auparavant, l’API de mise à jour des prix de niveau par lot (POST /V1/products/tier-prices) échouait sur l’ensemble de la requête lorsqu’aucun SKU n’existait dans la payload, laissant les SKU valides sans mises à jour. Désormais, les SKU valides sont traités avec succès, tandis que les SKU manquants sont signalés comme des erreurs par élément, de sorte qu’une seule entrée incorrecte n’abandonne plus l’ensemble du lot.

_ACP2E-4998 - [contribution du code GitHub](https://github.com/magento/magento2/commit/51f6d191)_

#### La mise à jour des attributs échoue avec le libellé Valeur correspondant à l’ID de valeur d’option existant

Correction du problème en raison duquel une nouvelle option d’attribut de produit de liste déroulante/sélection multiple ne pouvait pas être créée via l’API REST lorsque son libellé correspondait à l’identifiant d’une option existante. Auparavant, l’API renvoyait une erreur « existe déjà » (et pouvait renvoyer le mauvais ID d’option) même si la même option pouvait être créée avec succès via l’interface utilisateur d’administration.

_ACP2E-5107 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/4d0357d7)_

### API, import et export

#### L’API REST autorise des prix de produit négatifs alors que l’interface utilisateur d’administration les bloque

L’importation de produits via le point d’entrée de l’API REST rejette désormais les valeurs négatives pour les attributs de type prix (prix, special_price, coût et champs MSRP associés), conformément au comportement de l’importation de l’interface utilisateur d’administration. Auparavant, l’API acceptait les prix négatifs en silence et les persistait.

_ACP2E-4941 - [contribution du code GitHub](https://github.com/magento/magento2/commit/08b91f1a)_

### API, Ordre

#### Fonction de limite du taux de commande incompatible avec le serveur principal du cache Valkey

Auparavant, cette limitation de débit fixe était silencieusement contournée et chaque requête était autorisée, quelle que soit la limite configurée. Après la correction, les requêtes qui dépassent la limite configurée sont correctement rejetées avec le HTTP 429.

_ACP2E-4899 - [contribution du code GitHub](https://github.com/magento/magento2/commit/9b6a8bd9)_

### Compte

#### [Problème] correction : libellé de mot de passe incorrect pour le formulaire de connexion

Correction d’un problème en raison duquel le champ Mot de passe de la page de connexion du client avait une association de libellé incorrecte. Le libellé du mot de passe cible désormais correctement le champ Mot de passe , ce qui permet de l’identifier correctement par les outils de test automatisés.

_AC-16193 - [Problème GitHub](https://github.com/magento/magento2/issues/40353) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/64eb754d)_

#### [Problème ] valider le type d’entrée front-end pour les chargements de fichiers

Les chargements de fichiers d’adresses client valident désormais que le type d’entrée de l’attribut cible est fichier ou image avant traitement, de sorte que le texte et les autres attributs non liés aux fichiers ne peuvent pas être utilisés abusivement comme cibles de chargement. Les tentatives de chargement non valides renvoient une erreur de validation claire au lieu d’échouer de manière imprévisible ou d’accepter des types de fichiers non autorisés.

_AC-17076 - [Problème GitHub](https://github.com/magento/magento2/issues/40795) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/40583)_

#### Le jeton client généré sur le site Web A peut être utilisé sur le site Web B dans la configuration client de portée web.

Pour appliquer une isolation stricte des données client sur les instances multi-sites, un écart de sécurité a été résolu dans la couche d’authentification GraphQL où les jetons étaient incorrectement validés au-delà des frontières distinctes.

_AC-17299 - [Problème GitHub](https://github.com/magento/magento2/issues/40847) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/40858)_

#### [Problème] Correction de l&#39;obsolescence de PHP 8.5 : utilisation de null comme paramètre de clé pour array_key_exists()

Correction d’un problème sur PHP 8.5 en raison duquel la connexion du client lors du passage en caisse des invités échouait en raison d’un appel array_key_exists() obsolète avec une clé null. La connexion du client fonctionne désormais sans générer d’erreur d’obsolescence.

_AC-17395 - [Problème GitHub](https://github.com/magento/magento2/issues/40875) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/515d3dd3)_

#### [Problème ] magento/magento2 : ajoutez les traductions i18 aux mutations requestPasswordResetEmail et resetPassword GraphQL

Pour garantir une expérience de storefront entièrement localisée, des fonctionnalités d’internationalisation (i18n) ont été ajoutées aux points d’entrée de l’API de récupération du compte client

_AC-9356 - [Problème GitHub](https://github.com/magento/magento2/issues/29658) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/28950)_

### Interface utilisateur d’administration

#### Le tableau de bord doit afficher les 7 derniers jours par défaut lorsque des données agrégées sont utilisées

Correction d’un problème en raison duquel le tableau de bord affichait Aujourd’hui par défaut lorsque les données de ventes agrégées étaient activées. Le tableau de bord affiche désormais 7 derniers jours par défaut lors de l’utilisation de données agrégées.

_AC-13799 - [Problème GitHub](https://github.com/magento/magento2/issues/28152) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/29a7cdbe)_

#### Les valeurs FPT dans la page de panier et la page de produit sont différentes pour les mêmes configurations pour un produit simple

Correction d’un problème en raison duquel les valeurs de taxe sur les produits fixes (FPT) s’affichaient différemment sur les pages de produits et de panier pour la même configuration de taxe. Les valeurs FPT sont désormais affichées de manière cohérente sur les pages de produits, de catalogues, de mini-panier et de panier.

_AC-17007 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/ecbeba3a)_

#### Implémentation de configuration différée

Optimisation des performances qui améliore les performances de chargement de la configuration en résolvant de manière différée les données de configuration système étendues tout en préservant le comportement de configuration existant.

_ACP2E-4751 - [contribution du code GitHub](https://github.com/magento/magento2/commit/65f660bd)_

#### Éditeur de RTE énorme bloque les émoticônes - échec de la validation de JavaScript

Correction du problème en raison duquel HugeRTE bloquait l’enregistrement du contenu contenant des émoticônes utf8mb4 (par exemple, 🔵⚪🔴) lors de la modification dans les modèles de type contenu PageBuilder (texte, bannière, diapositive). Auparavant, la configuration de validation wysiwyg de ces formulaires modaux était résolue `allowUtf8mb4` à `false`, ce qui entraînait le rejet par l’éditeur de caractères UTF-8 de 4 octets même sur les installations où la base de données prend entièrement en charge utf8mb4.

_ACP2E-4822 - [contribution du code GitHub](https://github.com/magento/magento2-page-builder/commit/f2691e17)_

#### L’administrateur restreint ne peut pas supprimer les clients après la mise à niveau

Correction d’un problème en raison duquel l’administrateur restreint ne pouvait pas supprimer les clients après la mise à niveau, avec une bannière rouge en haut de la grille des clients indiquant : « Des autorisations supplémentaires sont nécessaires pour afficher cet élément ».

_ACP2E-4838_

#### L’administrateur est déconnecté lors de l’affichage de clients avec des carnets d’adresses volumineux dans la page d’édition client du panneau d’administration

Correction d’un problème en raison duquel l’administrateur était déconnecté lors de l’affichage de clients avec des carnets d’adresses volumineux dans la page d’édition client du panneau d’administration

_ACP2E-4875 - [contribution du code GitHub](https://github.com/magento/magento2/commit/b63925d9)_

#### Les commandes n&#39;apparaissent pas dans la grille des ventes

Correction d’un problème en raison duquel l’affichage des nouvelles commandes dans les grilles Ventes était retardé lorsque l’indexation asynchrone de la grille était activée, en raison de la réinitialisation du curseur de réconciliation une fois qu’il rattrapait l’entité la plus récente. Les nouvelles entrées apparaissent désormais dans la grille lors de la prochaine exécution de cron.

_ACP2E-4893 - [contribution du code GitHub](https://github.com/magento/magento2/commit/b63925d9)_

#### [Cloud] filtre Produits affectés manquants dans la grille de produits de catégorie lorsque Magento_VisualMerchandiser est activé

Correction du problème en raison duquel le filtre « Affecté » était absent de la grille modale Ajouter des produits Rechercher tous les produits lorsque Visual Merchandiser est activé. Auparavant, les utilisateurs administrateurs n’avaient aucun moyen de filtrer les produits en fonction de leur statut affecté/non affecté dans cette boîte de dialogue modale, ce qui rendait difficile l’identification des produits qui se trouvaient déjà dans la catégorie.

_ACP2E-4974_

#### Le journal des actions n&#39;affiche pas le numéro de retour/l&#39;ID de retour pour les actions liées au retour

Correction du problème en raison duquel le numéro de retour/l’ID de retour ne s’affichait pas dans les entrées du journal d’actions pour les actions d’administration liées au retour. Auparavant, des actions telles que l&#39;affichage ou l&#39;enregistrement d&#39;un retour client étaient enregistrées dans le journal d&#39;actions sans aucun identifiant de retour, contrairement aux actions liées aux commandes qui affichaient correctement le numéro de commande.

_ACP2E-5050_

#### « Utiliser la valeur par défaut » non coché pour la classe de prix et de taxe sur l’enregistrement de produit Admin à la portée de la vue du magasin.

Les utilisateurs administrateurs restreints peuvent désormais enregistrer des produits dans la portée d’affichage du magasin sans perdre l’état « Utiliser la valeur par défaut » pour les attributs de prix, de statut et de classe de taxe. Auparavant, l’enregistrement d’un produit en tant qu’administrateur restreint (avec la modification du prix et du statut refusée) désélectionnait silencieusement « Utiliser la valeur par défaut » pour ces champs, provoquant l’écriture de remplacements au niveau du magasin, même si aucun n’était prévu.

_ACP2E-5081_

### Interface utilisateur d’administration, commande

#### Prix incorrect affiché pour le produit groupé dans la commande de création d’administration lorsque deux produits groupés partagent le même produit simple

Correction d’un problème en raison duquel le prix d’un produit regroupé dans la commande de création d’administration était incorrectement calculé lorsque deux produits regroupés partageant le même produit simple étaient configurés sans être ajoutés au panier.

_ACP2E-4965 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/08b91f1a)_

### Interface utilisateur d’administration, structure de l’interface utilisateur

#### Magento2 redirige vers la page d’accueil au lieu d’afficher une erreur avec une déclaration de menu incorrecte

Pour optimiser le workflow de développement d’extension et garantir un chargement stable du serveur principal, un défaut de routage structurel a été résolu lorsque des déclarations non valides du menu d’administration déclenchaient des échecs de boucle de navigateur silencieux au lieu d’afficher des messages de diagnostic exploitables.

_AC-7543 - [Problème GitHub](https://github.com/magento/magento2/issues/36632) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/40881)_

### Analyses / Rapports

#### [QUANS ] peut-il être possible d’afficher l’ID d’e-mail et le nom du client dans le tableau des KPI du client sous Rapports avancés ?

Adobe Commerce inclut désormais le prénom, le deuxième prénom et le nom du client dans les données exportées vers les rapports avancés, ce qui permet au tableau des KPI du client d’afficher le nom du client. Auparavant, seul un identifiant client codé était exporté. Par conséquent, les commerçants ne pouvaient pas identifier les clients par nom dans les rapports avancés.

_ACP2E-3928 - [contribution du code GitHub](https://github.com/magento/magento2/commit/4d0357d7)_

#### INSERTION lourde sur sales_bestsellers_aggregate_monthly

Amélioration des performances de la commande cron aggregate_sales_report_bestsellers_data.

_ACP2E-4559 - [contribution du code GitHub](https://github.com/magento/magento2/commit/8d95ae6e)_

#### La payload de l’événement Ajouter au panier est au format d’e-commerce amélioré hérité d’Universal Analytics au lieu du format d’e-commerce GA4.

Avant le correctif, les événements d’e-commerce envoyés à Google Analytics 4 via Google Tag Manager utilisaient l’ancien format Universal Analytics et il leur manquait plusieurs événements de passage en caisse. Après le correctif, tous les événements d’e-commerce utilisent le format GA4 correct et le funnel d’extraction complet est suivi.

_ACP2E-5176 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/24667df1)_

### B2B

#### placeNegotiableQuoteOrderV2 renvoie total.total_shipping = null pour les commandes passées à partir d&#39;un devis négociable

Correction d&#39;un problème en raison duquel placeNegotiableQuoteOrderV2 renvoyait un total d&#39;expédition nul pour les commandes passées à partir d&#39;un devis négociable avec expédition payée. L’API renvoie désormais correctement le montant de la livraison, correspondant aux frais de livraison inclus dans le total de la commande.

_AC-18083_

#### [B2B] Prix d&#39;option de bundle manquants dans les détails du devis après la conversion du devis en commande

Correction d’un problème en raison duquel les prix des options de produit groupé manquaient sur la page des détails du devis négociable après la conversion du devis en commande.

_ACP2E-5055_

### B2B, Commande

#### Aide sur le nettoyage des tables de devis de plus de 59M (impossible d&#39;exécuter sales_clean_quotes)

Correction du problème en raison duquel la tâche cron `sales_clean_quotes` expirait sur les instances comportant des tables de guillemets volumineuses. Auparavant, la requête de nettoyage sélectionnait inutilement toutes les colonnes de la table `negotiable_quote`, ce qui entraînait l’exécution par MySQL d’un tri de fichiers complet sur des millions de lignes ; et chaque citation était supprimée individuellement via la couche de modèle PHP, ce qui augmentait le coût de la performance.

_ACP2E-4891 - [contribution du code GitHub](https://github.com/magento/magento2/commit/b63925d9)_

### Panier et passer en caisse

#### Notification Ajouter au panier pour les produits associés

Correction d’un problème en raison duquel la notification Ajouter au panier n’incluait pas le produit associé lors de l’ajout d’un produit et de son produit associé.
La notification affiche désormais les noms des deux produits ajoutés au panier.

_AC-11976 - [Problème GitHub](https://github.com/magento/magento2/issues/27164) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/515d3dd3)_

#### [Problème] Mettre à jour CartRepositoryInterface.php

Mise à jour du fichier CartRepositoryInterface.php pour déclarer les exceptions qui peuvent être levées lors de l’enregistrement d’un panier. L’interface reste ainsi cohérente avec l’implémentation de l’enregistrement du panier sous-jacente.

_AC-13323 - [Problème GitHub](https://github.com/magento/magento2/issues/39328) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/29a7cdbe)_

#### Le champ [Bogue] Société de l’adresse d’expédition est défini sur null dans la configuration multi-magasin lors de l’ajout d’une nouvelle adresse lors de l’étape d’expédition de passage en caisse

Correction d’un problème en raison duquel le champ Société n’était pas enregistré lorsque les clients ajoutaient une nouvelle adresse de livraison lors du passage en caisse dans une configuration multi-magasin. La valeur Société est désormais correctement enregistrée dans le devis, la commande passée et le carnet d’adresses du client.

_AC-13456 - [Problème GitHub](https://github.com/magento/magento2/issues/39424) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/515d3dd3)_

#### Paypal > Inadéquation des données client (préfixe, prénom, nom)

Correction d’un problème en raison duquel les détails du nom du client étaient incorrectement mappés lors du flux de passage en caisse de PayPal SEPA. Le préfixe, le prénom et le nom sont désormais correctement renseignés dans l’ordre, sans aucune incohérence.

_AC-15366 - [Problème GitHub](https://github.com/magento/magento2/issues/39061) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/ecbeba3a)_

#### Indicateur free_shipping incorrect pour les produits virtuels

Correction d’un problème en raison duquel l’indicateur free_shipping était incorrectement défini pour les produits virtuels lorsque plusieurs articles étaient ajoutés au panier. L&#39;indicateur est désormais correctement défini pour tous les articles lorsque la règle d&#39;expédition gratuite applicable est appliquée.

_AC-15648 - [Problème GitHub](https://github.com/magento/magento2/issues/40184) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/c10554e1)_

#### Ajout au panier de l’invité : la section « panier » du mini-panier/des données client indique que le panier est vide même si l’élément est correctement conservé.

Correction d’un problème en raison duquel le mini-panier invité ne reflétait pas les articles immédiatement après l’ajout d’un produit au panier. Le compteur et la liste déroulante du mini-panier sont désormais correctement mis à jour et les produits ajoutés s’affichent dans le panier comme prévu.

_AC-17973 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/2b218686)_

#### messages d’erreur intégrés d’ajout au panier AJAX perdus sémantique role=« alert »

Correction d’un problème en raison duquel les messages d’erreur de l’ajout au panier AJAX étaient visibles sur le storefront mais n’étaient pas annoncés par les lecteurs d’écran. Les erreurs de complément au panier sont désormais affichées dans une région role=« alert » accessible pour une prise en charge adéquate de l’accessibilité.

_AC-18036 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/2b218686)_

#### Ignorer les règles suivantes pour le montant de l&#39;expédition

Pour garantir une tarification promotionnelle précise et une stricte conformité aux règles de remise configurées, une erreur du calculateur de règles de prix de panier a été résolue lorsque des remises sur les expéditions de priorité inférieure ont été appliquées de manière incorrecte

_AC-9612 - [Problème GitHub](https://github.com/magento/magento2/issues/37985) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/40869)_

#### Commandes en double créées même si l&#39;erreur est déclenchée

Correction d’un problème en raison duquel les commandes pouvaient toujours être passées avec une adresse client non valide

_ACP2E-4774 - [contribution du code GitHub](https://github.com/magento/magento2/commit/8d95ae6e)_

#### Impact des performances du produit configurable sur le passage en caisse (totaux-informations, devis-modules-d’expédition)

Avant la correction, les demandes de passage en caisse telles que les totaux-informations et les méthodes-d’expédition-estimation pouvaient devenir considérablement plus lentes pour les produits configurables avec de nombreux produits enfants lorsque le premier enfant vendable apparaissait tard dans la liste des enfants. Après le correctif, cette dégradation des performances ne se produit plus et les temps de réponse restent cohérents quelle que soit la position du premier enfant vendable.

_ACP2E-4805 - [contribution du code GitHub](https://github.com/magento/inventory/commit/30fbdb0f)_

#### Totaux du panier recalculés à chaque page vue du panier

Demandes de totaux de panier optimisées sur la page de panier. Les totaux du panier ont été recalculés deux fois sur chaque page vue du panier.

_ACP2E-4817 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/b63925d9)_

#### Les règles de validation Attribut de l’adresse du client (EAV) Ville et Rue sont en conflit avec les règles de validation codées en dur.

Correction d’un problème en raison duquel le programme de validation de ville rejetait incorrectement les noms de ville valides de plus de 100 caractères (la limite de la base de données est de 255), et où les adresses postales de plus de 255 caractères pouvaient être tronquées silencieusement dans la base de données sans\
renvoie une erreur de validation. Les deux validateurs appliquent désormais des limites alignées avec la contrainte de colonne de base de données la plus étroite sur toutes les tables d’adresses.

_ACP2E-4861 - [contribution du code GitHub](https://github.com/magento/magento2/commit/b63925d9)_

#### [Storefront] Message indiquant que la quantité demandée n’est pas disponible pour l’ajout au panier, qui n’apparaît pas par intermittence sur le PDP

Correction du problème lié au message d’indisponibilité du stock (« La quantité demandée n’est pas disponible, veuillez réduire la quantité. »). par intermittence n’était pas affiché sur la page des détails du produit après une tentative d’ajout au panier ayant échoué. Auparavant, la page pouvait être actualisée en silence sans commentaires d’erreur lorsqu’un acheteur cliquait à plusieurs reprises sur Ajouter au panier pour un produit dont le stock disponible était déjà entièrement réservé dans son panier.

_ACP2E-5071 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/8d70f246)_

#### Effacement du panier persistant à l’expiration de la session naturelle lorsque Effacer la persistance lors de la déconnexion = Oui

Correction du problème en raison duquel le panier persistant était effacé après expiration de la session du navigateur. Auparavant, lorsque la fonction Effacer la persistance lors de la déconnexion était activée, une session expirée vidait le panier et supprimait le cookie persistant même si l’acheteur ne s’était pas déconnecté.

_ACP2E-5088 - [contribution du code GitHub](https://github.com/magento/magento2/commit/597c7211)_

#### Customer_email de devis invité non resynchronisé depuis l&#39;adresse de facturation après restoreQuote() lors d&#39;une nouvelle tentative de passage en caisse

Correction d’un problème en raison duquel une nouvelle tentative de passage en caisse d’un invité ayant échoué passait la commande avec l’e-mail saisi précédemment au lieu de celui mis à jour.

_ACP2E-5188 - [contribution du code GitHub](https://github.com/magento/magento2/commit/597c7211)_

### Panier et passer en caisse, GraphQL

#### L’API Quote GraphQL peut affecter des objets de devise au lieu de codes de devise ISO aux champs de devis

Mise à jour de l&#39;API Quote GraphQL pour affecter des codes de devise ISO aux champs de devise de magasin et de devis d&#39;un devis au lieu d&#39;affecter des objets de devise.

_ACP2E-5229 - [contribution du code GitHub](https://github.com/magento/magento2/commit/24667df1)_

### Catalogue

#### [Problème ] améliorations apportées au fichier module.xml pour les modules Magento_ConfigurableProductGraphQl, Magento_MsrpConfigurableProduct, Magento_NewRelicReporting et Magento_Swatches.

Optimisation de l’architecture de déclaration de module en supprimant les dépendances redondantes de Magento_Catalog de quatre sous-modules principaux. Ce nettoyage résout les doublons inutiles dans l’arborescence des dépendances, simplifie les calculs d’ordre de chargement des modules et améliore la maintenabilité du framework à long terme sans introduire de modifications importantes.

_AC-10762 - [Problème GitHub](https://github.com/magento/magento2/issues/30675) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/30638)_

#### Possible fuite de mémoire dans la fonction getUsedProducts pour les éléments configurables

Correction d’un problème en raison duquel le traitement de plusieurs produits configurables entraînait une augmentation du temps d’exécution et de l’utilisation de la mémoire au fil du temps.
Les produits configurables peuvent désormais être traités sans le ralentissement progressif et l’augmentation de la mémoire.

_AC-10942 - [Problème GitHub](https://github.com/magento/magento2/issues/37639) - [Contribution du code GitHub](https://github.com/magento/inventory/commit/8c058c2e)_

#### Filtre Shop By Category visible sur les catégories autres que les catégories d’ancrage

Correction d’un problème où le filtre Shop By Category s’affichait sur les catégories non ancrées même si le filtre de catégorie était désactivé dans Admin.
Le filtre est désormais masqué sur le storefront conformément au paramètre configuré.

_AC-10945 - [Problème GitHub](https://github.com/magento/magento2/issues/38379) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/64eb754d)_

#### Le type de données applied_rule_ids dans Quote et Quote Item est différent

Pour garantir la cohérence absolue du schéma de base de données et empêcher les incohérences de données de panier critiques sur les magasins promotionnels à volume élevé, les définitions de la colonne de données des promotions actives ont été étendues sur les structures de passage en caisse parentes.

_AC-14518 - [Problème GitHub](https://github.com/magento/magento2/issues/39838) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/40540)_

#### Impossible d’obtenir l’attribut de `decimal` de la collection de produits dont la portée est globale

Pour garantir une tarification précise du storefront et un rendu des attributs sur les configurations internationales, un bug de collecte de données principales a été résolu où les valeurs décimales spécifiques au magasin ont été remplacées par erreur par les valeurs globales par défaut.

_AC-15806 - [Problème GitHub](https://github.com/magento/magento2/issues/40218) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/40419)_

#### Gestion incorrecte des paramètres GET

Pour améliorer la stabilité de la plateforme et protéger le funnel de passage en caisse, une couche de validation d’entrée au niveau du bloc a été ajoutée pour empêcher les requêtes d’URL incorrectes de bloquer les pages de produits de storefront.

_AC-16262 - [Problème GitHub](https://github.com/magento/magento2/issues/40405) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/40433)_

#### Magento\SalesRule\Model\Plugin\QuoteConfigProductAttributes::afterGetProductAttributes déclenché sur toutes les requêtes de panier

Pour réduire les contraintes d’exécution de la base de données et éliminer les accès non optimisés à la base de données lors des passages en caisse des clients, le plug-in de configuration du produit de règle de vente a été optimisé pour exécuter de manière conditionnelle et exploiter les structures de mise en cache.

_AC-16559 - [Problème GitHub](https://github.com/magento/magento2/issues/40226) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/40251)_

#### [Problème] [PHPDOC] Correction des fonctions orderComment dans Magento\Sales\Model\Order

Afin d’éliminer les restrictions de saisie strictes, d’améliorer la précision des analyses statiques et l’expérience des développeurs sous des moteurs de liaison rigoureux tels que PHPStan (niveau 5 ou supérieur), les blocs de documentation structurelle intégrés ont été normalisés dans les sous-systèmes principaux des commandes client.

_AC-16759 - [Problème GitHub](https://github.com/magento/magento2/issues/39575) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/39572)_

#### [Problème] [Bogue] GraphQL SearchCriteriaValidator non chargé — supprimé par le remplacement du tableau di.xml module-graph-ql

Pour préserver une validation de requête robuste et appliquer les mécanismes de sécurisation de la plateforme, un défaut de configuration d’injection de dépendance (DI) a été résolu lorsque le calque SearchCriteriaValidator était désactivé par inadvertance.

_AC-16959 - [Problème GitHub](https://github.com/magento/magento2/issues/40762) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/40742)_

#### strpos() s&#39;attend à ce que le paramètre 1 soit une chaîne, tableau donné | magento/module-eav

Pour protéger la stabilité du storefront et offrir une expérience client ininterrompue, un défaut critique de correspondance de type a été résolu dans les moteurs de traitement de recherche de catalogue avancés.

_AC-1706 - [Problème GitHub](https://github.com/magento/magento2/issues/33588) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/40422)_

#### Des enregistrements de devis vides sont créés lorsque le client visite une page

Dans certains cas, la consultation de la page produit sur le storefront ne crée pas d’enregistrements de devis vides.
Auparavant, des enregistrements de devis vides étaient créés lorsque le client visitait une page produit sur le storefront

_ACP2E-4682 - [contribution du code GitHub](https://github.com/magento/magento2/commit/8d95ae6e)_

#### L’attribut « Poids » de la page de détails du produit n’affiche pas le suffixe d’unité dans la section « Informations supplémentaires »

Correction du problème en raison duquel l’attribut Poids sur la page produit de Storefront affichait uniquement une valeur numérique brute dans la section « Informations supplémentaires » ou « Informations supplémentaires » sans l’unité de mesure configurée (lb ou kg).

_ACP2E-4808 - [contribution du code GitHub](https://github.com/magento/magento2/commit/b63925d9)_

#### [Cloud] L’activation des règles de prix de catalogue ne se reflète pas dans la recherche en direct avant la prochaine resynchronisation forcée - délai de synchronisation des flux de prix

Correction d’un problème en raison duquel l’activation d’une règle de prix de catalogue ne mettait pas à jour les prix dans la recherche en direct avant une resynchronisation forcée ultérieure. L’indexeur du flux de prix pouvait s’exécuter avant la fin de l’indexeur des règles de catalogue dont il dépend, et donc les prix obsolètes exportés. Les indexeurs avec des dépendances non terminées sont désormais reportés à la prochaine exécution cron, de sorte que le flux de prix s&#39;exécute toujours par rapport aux prix à jour.

_ACP2E-5029 - [contribution du code GitHub](https://github.com/magento/magento2/commit/ec436b10)_

#### [CLOUD] problème de logique de l’opérateur OU de la règle de catégorie Adobe Commerce Cloud

L’opérateur Contains accepte désormais plusieurs valeurs séparées par des virgules, évaluées comme une correspondance OR. Une seule ligne de règle peut donc correspondre à l’un de plusieurs termes au lieu d’un seul.

_ACP2E-5061_

#### Le texte secondaire (libellé) n’est pas enregistré pour une image de produit nouvellement ajoutée

Correction d’un problème où le texte secondaire (libellé) d’une image de produit nouvellement chargée n’était pas enregistré lorsque le fichier chargé était renommé lors de l’enregistrement en raison d’une collision de nom de fichier dans la galerie de médias. Auparavant, les attributs de rôle d’image (image, small_image, thumbnail) étaient correctement stockés, mais leurs attributs *_label correspondants étaient silencieusement supprimés, laissant le texte secondaire vide sur les pages de recherche et de liste de storefront. Le gestionnaire de création de galerie résout désormais le fichier renommé sur son entrée d’image d’origine, de sorte que le libellé est conservé pour tous les rôles d’image attribués. Par conséquent, le texte secondaire saisi lors de la création du produit est enregistré et rendu de manière fiable sur le storefront.

_ACP2E-5216 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/24667df1)_

#### Erreur d’obsolescence de PHP 8.5 « null as array offset » ouvrant la page Ajouter un produit dans l’administration lorsque l’utilisateur ne dispose pas de la ressource Modifier le statut du produit

Auparavant, les utilisateurs administrateurs ne disposant pas de l’autorisation « Modifier le statut du produit » pouvaient rencontrer une erreur d’obsolescence « null en tant que décalage de tableau » lors de l’ouverture de la page Ajouter un produit. Ce problème a été corrigé afin que la page se charge correctement, quelles que soient les autorisations de statut du produit de l’utilisateur.

_ACP2E-5248 - [contribution du code GitHub](https://github.com/magento/magento2/commit/24667df1)_

### Catalogue, GraphQL

#### Problèmes de filtre de prix de requête de produits [GraphQl] avec des prix nets saisis dans adminhtml

Correction d’un problème en raison duquel la requête de produits GraphQL ne prenait pas en compte la taxe lors de l’application d’un filtre de prix.
Le filtre de prix utilise désormais le prix TTC affiché, de sorte que seuls les produits de la plage de prix spécifiée sont renvoyés.

_AC-6883 - [Problème GitHub](https://github.com/magento/magento2/issues/36337) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/8b67e8ed)_

### Catalogue, Performances

#### [CLOUD] customer_group_exclude_website ne sont pas pris en charge par le pipeline d’indexation des autorisations de catalogue

L’index des autorisations de catalogue exclut désormais le site web qui est exclu du groupe de clients.

_ACP2E-5223_

### Catalogue, SEO

#### La modification url_path de la catégorie ne se synchronise pas sur url_key pour toutes les vues de magasin.

Auparavant, la modification de la clé URL d’une catégorie dans la portée « Toutes les vues de la boutique » pouvait laisser les catégories descendantes de la boutique avec un chemin_URL obsolète ou ayant un préfixe incorrect et la modification d’une catégorie avec son propre remplacement de chemin_URL spécifique à la boutique pouvait récupérer sa clé URL de prémodification au lieu de celle que vous venez de saisir. Ce problème est désormais résolu : les modifications de clé d’URL sont correctement répercutées en cascade sur tous les descendants dont l’étendue est stockée, dans l’ordre hiérarchique approprié, avec le chemin parent correct. Le remplacement du chemin d’URL de l’étendue d’une catégorie est recalculé à l’aide de sa clé d’URL qui vient d’être modifiée. Les URL dont l’étendue est stockée restent donc exactes immédiatement après l’enregistrement.

_ACP2E-5113 - [contribution du code GitHub](https://github.com/magento/magento2/commit/597c7211)_

### Cloud, framework

#### Régression des performances et stockage en cache incorrect avec SymfonyL2 activé

Correction d’un problème en raison duquel la configuration du chemin d’accès de stockage du cache L1 en tant que chemin absolu (par exemple /dev/shm) entraînait sa redirection silencieuse vers le répertoire var/ et un problème de performances distinct où l’invalidation des balises de cache sur des catalogues volumineux pouvait entraîner des délais de réponse importants en raison d’une opération Redis de blocage.

_ACP2E-4989 - [contribution du code GitHub](https://github.com/magento/magento2/commit/51f6d191)_

### Contenu

#### Les pages CMS créées pour différents sites web affichent des pages incorrectes dans frontend

Auparavant, dans les configurations multi-sites web, la clé de cache de la page de destination de la restriction du site web n’était pas définie par site web, ce qui entraînait la diffusion d’une page CMS incorrecte sur le storefront du site web secondaire. La clé de cache dans WebsiteRestriction/Controller/Index/Stub.php inclut désormais correctement l’ID de site web actuel résolu via le gestionnaire de magasin.

_ACP2E-4593_

#### L’évaluation des segments de clients renvoie les clients du premier site web uniquement et non de tous les sites web attribués lorsque le partage global de clients est activé

Correction d’un problème en raison duquel l’évaluation des segments client renvoie les clients du premier site web uniquement et non de tous les sites web affectés lorsque le partage global de clients est activé.

_ACP2E-5079_

#### La demande d’aperçu ajax de Page Builder renvoie une erreur 500 avec le cache de traduction désactivé

L’aperçu PageBuilder s’affiche désormais correctement, que le cache de traductions soit activé ou désactivé. Auparavant, l’aperçu PageBuilder ne s’affichait pas lorsque le cache de traductions était désactivé.

_ACP2E-5118 - [Contribution du code GitHub](https://github.com/magento/magento2-page-builder/commit/606e12fd)_

#### Les chargements GIF animés sont convertis en PNG lorsque l’option Activer l’ancienne galerie de médias est activée

Correction d’un problème où les images GIF animées chargées par le biais de la galerie de médias étaient converties au format PNG lorsque la galerie de médias héritée était activée. Auparavant, lorsque l’option Activer le redimensionnement frontal était activée, les GIF animés chargés via l’ancienne galerie de médias perdaient leur animation et étaient enregistrés en tant que fichiers PNG statiques. Les GIF animés sont maintenant téléchargés et stockés dans leur format d’origine.

_ACP2E-5232 - [contribution du code GitHub](https://github.com/magento/magento2/commit/24667df1)_

### Contenu / CMS

#### [Problème ] correction de l’onglet Galerie de produits lorsqu’un libellé d’attribut d’image contient une apostrophe

Pour garantir une expérience de gestion de catalogue fiable et ininterrompue dans le panneau d’administration, un défaut de formatage de JavaScript a été résolu, ce qui a complètement rompu l’interface de l’espace de travail du produit principal

_AC-16474 - [Problème GitHub](https://github.com/magento/magento2/issues/40519) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/40870)_

#### [Problème ] améliore les performances lorsque l’URL de l’image redimensionnée est accessible mais n’existe pas encore.

Pour optimiser la réactivité de diffusion des ressources, réduire considérablement les E/S de disque serveur et empêcher les pics de processeur serveur importants, le sous-système de génération d’images de catalogue a été optimisé afin de gérer les URL de médias manquantes strictement à la demande.

_AC-16547 - [Problème GitHub](https://github.com/magento/magento2/issues/40399) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/40388)_

#### Régression : le composant URI codé non UTF-8 renvoie toujours « Impossible de sérialiser la valeur » dans CatalogWidget sur 2.4.7-p5

Pour éliminer les échecs de rendu critiques causés par un trafic web de production incorrect, le bloc de widget de catalogue a été renforcé pour gérer de manière appropriée les séquences de données non-UTF-8 dans les URL demandées.

_AC-17264 - [Problème GitHub](https://github.com/magento/magento2/issues/40824) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/40825)_

#### `Using null as an array offset is deprecated, use an empty string instead` lors de la modification de la portée de la configuration de conception globale

Correction d’un problème en raison duquel la modification de la portée globale sous Contenu > Conception > Configuration renvoyait une erreur HTTP 500 sur PHP 8.5 en raison d’un décalage de tableau nul obsolète. La configuration de conception globale s’ouvre désormais sans erreur.

_AC-17456 - [Problème GitHub](https://github.com/magento/magento2/issues/40886) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/515d3dd3)_

### Framework

#### FAITES VOTRE CHOIX parmi media_storage_file_storage lorsque le stockage de la base de données multimédia n’est pas utilisé ou désactivé

Pour réduire la surcharge des requêtes inutiles et éliminer les exceptions bruyantes de systèmes, la couche de synchronisation des fichiers multimédias a été optimisée pour contourner les contrôles de stockage de la base de données lorsque le système est explicitement configuré pour utiliser le système de fichiers local

_AC-10586 - [Problème GitHub](https://github.com/magento/magento2/issues/38116) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/40480)_

#### Erreur fatale générée sur le constructeur d’exception lorsque l’entrepôt de cookies est un tableau

Correction d’un problème en raison duquel une valeur de cookie de magasin non valide provoquait une erreur fatale PHP.
Magento renvoie désormais correctement une exception « Paramètre de magasin non valide » lorsque le cookie de magasin contient une valeur non valide.

_AC-10888 - [Problème GitHub](https://github.com/magento/magento2/issues/38365) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/7aecc9f1)_

#### [Problème] Utiliser la const statique dans Magento\Customer\Model\Address\Config

Correction d’un problème en raison duquel les classes de configuration d’adresses personnalisées devaient dupliquer getFormats() pour utiliser un chemin d’accès de modèle d’adresse personnalisée. Les configurations d’adresses personnalisées peuvent désormais définir leur propre chemin d’accès au modèle à l’aide d’une constante statique sans dupliquer la méthode.

_AC-12906 - [Problème GitHub](https://github.com/magento/magento2/issues/39135) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/29a7cdbe)_

#### Impossible d’utiliser processFilter dans la collection de produits

Correction d’un problème où l’application de plusieurs filtres à une collection de produits à l’aide de FilterProcessor provoquait une erreur PHP. Les collections de produits peuvent désormais être correctement filtrées à l’aide de plusieurs conditions de filtrage.

_AC-15018 - [Problème GitHub](https://github.com/magento/magento2/issues/40014) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/7aecc9f1)_

#### Problème potentiel de performance de l’indexeur pour les catalogues volumineux - Insertion en bloc et verrouillage de la table CL entière pour identifier la dernière version

Pour garantir les performances de la base de données sur les catalogues d’entreprise volumineux, le pipeline de l’indexeur de base de données système a été renforcé afin d’analyser les modifications de données planifiées dans des lots limités, éliminant les verrous de base de données haute pression.

_AC-16238 - [Problème GitHub](https://github.com/magento/magento2/issues/40331) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/40546)_

#### [Problème] Amélioration Des Performances

Pour éliminer l&#39;allocation inutile de mémoire et réduire la surcharge de traitement d&#39;exécution, plusieurs routines de manipulation de chaînes de base ont été refactorisées pour utiliser le comportement optimisé natif de PHP.

_AC-16565 - [Problème GitHub](https://github.com/magento/magento2/issues/40383) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/40375)_

#### [Problème] Correction de la prise en charge de GLOB_BRACE sur les systèmes Linux non-GNU

Pour garantir une capacité de déploiement transparente dans les environnements de virtualisation légers, un bug de découverte de chemin critique a été corrigé afin de restaurer complètement la prise en charge de l&#39;exécution pour les systèmes utilisant des bibliothèques non-GNU, telles que les images Alpine Linux Docker.

_AC-16568 - [Problème GitHub](https://github.com/magento/magento2/issues/40552) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/40538)_

#### Paramètres marketing réajoutés dans la requête utilisée pour la création d’identifiants FPC intégrés

Pour améliorer les taux d’accès au cache et éliminer les régressions de performances du serveur, un défaut structurel a été corrigé dans le système FPC (Full Page Cache) natif, où les paramètres de requête de marketing et de suivi ont été réintroduits accidentellement dans les signatures d’identifiant de cache.

_AC-16583 - [Problème GitHub](https://github.com/magento/magento2/issues/40350) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/40349)_

#### Ajouter la prise en charge des objets simples avec des propriétés promues dans la communication de file d&#39;attente de messages

Pour prendre en charge les pratiques de développement PHP modernes et simplifier les workflows d&#39;architecture asynchrones, le moteur de réflexion de framework a été amélioré pour traiter nativement les objets de transfert de données (DTO) en utilisant des propriétés de constructeur publiques, promues et en lecture seule.

_AC-16672 - [Problème GitHub](https://github.com/magento/magento2/issues/36660) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/40457)_

#### [Problème] Correction : l’introspection de type réel de colonne ignore les processeurs non signés/nullables et utilise les valeurs par défaut

Pour garantir un suivi précis de la configuration du système, un défaut d&#39;abstraction de base de données a été résolu lorsque les commandes de vérification de schéma déclaratif étaient signalées en permanence en attente de modifications pour les colonnes DOUBLE UNSIGNED ne possédant pas d&#39;attributs de précision ou d&#39;échelle explicites.

_AC-16758 - [Problème GitHub](https://github.com/magento/magento2/issues/40646) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/40582)_

#### [Fonctionnalité] Prise en charge de l’état « désactivé » pour les options de sélection individuelles dans la configuration de l’administrateur

Pour améliorer la flexibilité du formulaire principal et fournir aux développeurs un contrôle de mise en page granulaire, la prise en charge au niveau de la structure a été introduite pour marquer les balises d’option individuelles comme non sélectionnables dans les éléments de formulaire.

_AC-16761 - [Problème GitHub](https://github.com/magento/magento2/issues/40564) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/40565)_

#### Performances ⚡ : mémoire manquante dans StoreManager et surcharge du plug-in dans le module Store

Pour réduire considérablement la contrainte d’exécution du CPU et minimiser l’attrition inutile de la mémoire de l’application, une routine de mise en cache des valeurs de configuration critique a été mise en œuvre pour intercepter les processus de vérification de magasin redondants.

_AC-16838 - [Problème GitHub](https://github.com/magento/magento2/issues/40706) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/40732)_

#### [Problème] correction : supprimez le chemin d’accès du code openssl_free_key() mort dans JwkFactory

Pour nettoyer la dette de technologie structurelle et aligner les outils de chiffrement sur les profils d’exécution modernes, les hooks de libération de ressources hérités ont été purgés du serveur principal de l’utilitaire de clé web JSON.

_AC-16958 - [Problème GitHub](https://github.com/magento/magento2/issues/40761) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/40688)_

#### [Problème] Orthographe de correction PHPDoc

Pour maintenir des normes de qualité de code élevées et améliorer la précision des indications de code de l’environnement de développement intégré (IDE), des nettoyages structurels ont été appliqués aux couches de documentation de code intégré dans les modules de structure principaux.

_AC-16960 - [Problème GitHub](https://github.com/magento/magento2/issues/40763) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/40745)_

#### [Issue] perf(di:compile) : met en cache les instanciations ReflectionClass dans Type, Config/Reader et ClassReader

Pour accélérer considérablement les temps de compilation et maximiser le débit de déploiement d&#39;intégration continue (CI), le serveur principal du compilateur d&#39;injection de dépendance interne (`setup:di:compile`) a été optimisé pour éliminer les cycles de réflexion PHP redondants.

_AC-17077 - [Problème GitHub](https://github.com/magento/magento2/issues/40796) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/40615)_

#### [Problème] Mettez à jour Filter.php pour autoriser `{{block template="Magento_Module::path/to/template.phtml"}}` et définir \Magento\Framework\View\Element\Template comme classe par défaut

Pour simplifier la création de contenu et aligner les directives CMS sur les normes de mise en page des modèles, le système principal de traitement des balises de balisage a été amélioré afin de prendre en charge les déclarations de bloc sans définition de classe explicite.

_AC-17078 - [Problème GitHub](https://github.com/magento/magento2/issues/38477) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/38469)_

#### [Problème] perf(di:compile) : mémoriser les lectures de portée de la configuration d&#39;interception lors de la compilation

Afin d’accélérer considérablement les déploiements de site et la compilation back-end automatisée, le compilateur d’injection de dépendance (`setup:di:compile`) a été optimisé pour éliminer les opérations d’analyse XML redondantes.

_AC-17313 - [Problème GitHub](https://github.com/magento/magento2/issues/40852) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/40614)_

#### Mise à niveau de underscore.js vers la version 1.13.8 pour éviter les vulnérabilités de sécurité

La bibliothèque Underscore.js groupée (lib/web/underscore.js) a été mise à niveau de la version 1.13.7 vers la version 1.13.8. Aucune modification de configuration n’est requise.

_AC-17349 - [Problème GitHub](https://github.com/magento/magento2/issues/40857) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/12d0be1e)_

#### le programme d’installation de magento-composer ne remplit pas setup/ (et d’autres répertoires mappés) lorsqu’une destination de déploiement est un lien symbolique

Correction d’un problème en raison duquel le programme d’installation de magento-compositeur ne pouvait silencieusement pas remplir setup/ et d’autres répertoires mappés par le compositeur lorsque la destination de déploiement était configurée comme lien symbolique. Cela peut entraîner des fichiers manquants et un déploiement Commerce incomplet.

_AC-17360 - [Problème GitHub](https://github.com/magento/magento2/issues/40864)_

#### Les clés de préchargement du cache n’ont plus besoin de préfixe d’identifiant lors de l’utilisation de l’adaptateur Symfony Cache

Les clés de préchargement (preload_keys) de l&#39;adaptateur Symfony Cache peuvent maintenant être configurées sans le paramètre cache id_prefix. Auparavant, suite à la configuration documentée et à l’inclusion du préfixe sur chaque clé (par exemple, 061_SYSTEM_DEFAULT), les clés n’étaient pas préchargées. Vous pouvez maintenant spécifier les clés exactement comme l’application les demande (par exemple, SYSTEM_DEFAULT) pour qu’Adobe Commerce applique automatiquement le préfixe id_prefix.

_AC-17407 - [Problème GitHub](https://github.com/magento/magento2/issues/40877) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/3a6b9667)_

#### [Problème ] Correction de l’obsolescence de PHP 8.5 lorsque l’attribut de catégorie a « frontend_input »...

Correction d’un problème en raison duquel l’ouverture d’une catégorie dans le panneau d’administration provoquait une erreur sur PHP 8.5 lorsque l’attribut frontend_input d’une catégorie était défini sur null. Les pages de catégories s’ouvrent maintenant et peuvent être modifiées sans l’erreur d’obsolescence.

_AC-17499 - [Problème GitHub](https://github.com/magento/magento2/issues/40908) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/ecbeba3a)_

#### [Problème] Remplacer les assertions PHPUnit obsolètes et la configuration de stub de test

Mise à jour de la suite de tests de l&#39;unité centrale de Magento 2 pour les futures mises à niveau de PHPUnit en remplaçant sept utilisations obsolètes de PHPUnit. Les modifications portent sur les assertions de `isType()` et la configuration de `with*()` sur les stubs de test, des motifs qui déclenchent des avis d&#39;obsolescence dans les versions actuelles de PHPUnit et qui sont censés être supprimés dans PHPUnit 13 ou versions ultérieures.

_AC-17750 - [Problème GitHub](https://github.com/magento/magento2/issues/41040) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/41033)_

#### Les horodatages order_date et comment de GraphQL renvoient une date de calendrier incorrecte dans des paramètres régionaux non en_US (IntlDateForMATTER misparse) — Correction AC-14431 incomplète

Correction d’un problème en raison duquel les dates de commande GraphQL pouvaient afficher une date de calendrier incorrecte pour les paramètres régionaux français et allemand.
Les dates de commande et les horodatages des commentaires associés renvoient désormais la date et l’heure correctes.
Amélioration de la mise en forme des dates afin que les valeurs de date GraphQL puissent être analysées de manière fiable par les applications.
Le comportement existant des paramètres régionaux en_US reste inchangé.

_AC-18084 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/d10ab92b)_

#### [Problème] Supprimer la balise @author interdite

Afin d’assurer un alignement strict avec les directives techniques de base, un balayage de maintenance de code incrémentiel a été effectué pour nettoyer les blocs de documentation des ressources intégrées sur plusieurs modules système.

_AC-8366 - [Problème GitHub](https://github.com/magento/magento2/issues/37248) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/36993)_

#### [Problème] Supprimer la balise `@author` interdite de `Magento_Catalog` (partie 2)

Pour garantir un alignement complet avec les directives de diffusion de code unifié de Magento, une étape de nettoyage incrémentiel a été exécutée pour supprimer systématiquement les commentaires de fichier non conformes sur les modèles de ressources de storefront principaux.

_AC-8370 - [Problème GitHub](https://github.com/magento/magento2/issues/37247) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/36988)_

#### Le bogue de suppression de l&#39;interface de stockage de niveau de prix ne supprime pas tous les prix de niveau

Correction d’un problème dans TierPriceStorage en raison duquel la suppression des prix de niveau produit sur plusieurs sites web ne supprimait pas tous les prix en mettant à jour la logique de correspondance des ID de prix pour tenir compte de l’ID de site web affecté.

_AC-9738 - [Problème GitHub](https://github.com/magento/magento2/issues/37949) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/40557)_

#### [B2B] Les commandes fournisseur ne sont pas converties automatiquement en commande client avec ActiveMQ

Correction d’un problème en raison duquel les consommateurs démarrés par cron ne traitaient pas les messages lorsqu’ActiveMQ était utilisé avec le protocole STOMP. Par conséquent, les commandes fournisseur approuvées automatiquement n&#39;ont pas été converties en commandes client. Le traitement des messages pour les files d’attente STOMP est désormais plus fiable et cohérent avec les implémentations des files d’attente DB et AMAP.

_ACP2E-4349 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/08b91f1a) - [Contribution du code GitHub](https://github.com/magento/inventory/commit/239464da)_

#### Échec des exportations avec le stockage AWS S3 configuré

L’exportation de produits fonctionne désormais correctement lorsque le stockage distant AWS S3 est configuré. Auparavant, les fichiers exportés ne pouvaient pas être écrits dans S3 en raison d’une résolution de chemin non valide dans le pilote de stockage.

_ACP2E-4786 - [contribution du code GitHub](https://github.com/magento/magento2/commit/8d95ae6e)_

#### Les indexeurs sont bloqués dans une boucle de verrouillage automatique avec &#39;use_application_lock&#39; et le fournisseur &#39;file&#39;

Correction d’un problème en raison duquel les indexeurs se bloquaient indéfiniment lors de la réindexation lorsque le paramètre use_application_lock de l’indexeur était activé avec le fournisseur de verrouillage de fichier. Les opérations de réindexation se terminent désormais comme prévu.

_ACP2E-5027 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/ec436b10)_

#### Performances lentes avec les variables MAGENTO_DC définies dans l’interface utilisateur du cloud

Après la correction, la configuration de déploiement n’est pas rechargée chaque fois que la clé demandée n’est pas présente et que certaines variables d’environnement sont définies.

_ACP2E-5094 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/2b9e8316)_

#### [CLOUD] Un chemin d’URL incorrect renvoie HTTP 500 au lieu de 404 dans le routeur de réécriture d’URL

Correction du problème où une URL de storefront incorrecte renvoyait une page d’erreur HTTP 500 au lieu d’une URL 404 introuvable standard. Auparavant, certains chemins de requête incorrects provoquaient une erreur non interceptée lors de la résolution de réécriture d’URL.

_ACP2E-5154 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/4d0357d7)_

#### Compatibilité [CLOUD] PHP 8.5 — ComponentRegistrar::getPath() le décalage de tableau nul bloque setup:static-content:deploy (stratégie compacte) sur 2.4.9

Correction d&#39;un problème en raison duquel `setup:static-content:deploy` échouait sur PHP 8.5 avec une erreur « Utilisation de null comme décalage de tableau » lors de la compilation des fichiers LESS du module qui utilisent la directive //@magento_import. Le déploiement du contenu statique est maintenant terminé avec succès sur PHP 8.5.

_ACP2E-5183 - [contribution du code GitHub](https://github.com/magento/magento2/commit/597c7211)_

#### [CMS ] Faux positif « Contenu HTML non valide fourni » lors de l’enregistrement du bloc CMS avec une ancre href suivie d’un autre attribut

Le contenu CMS contenant un lien d’ancrage standard (par exemple, `&lt;a href="https://example.com/page" target="_blank" rel="noopener">`) ne déclenche plus un faux avertissement de validation « Contenu HTML non valide fourni » ou un échec d’enregistrement lorsque cms/wysiwyg/force_valid est activé.

_ACP2E-5203 - [contribution du code GitHub](https://github.com/magento/magento2/commit/24667df1)_

### Framework, GraphQL

#### l’élément du tableau di.xml est remplacé si la configuration ultérieure a utilisé une clé numérique

Pour protéger l’intégrité des données architecturales et améliorer l’extensibilité modulaire, un bug de base a été résolu dans le moteur d’analyse XML à injection de dépendance (DI) où les configurations de tableau utilisant la clé numérique « 0 » ont été silencieusement remplacées ou supprimées lors de la compilation du module.

_AC-8102 - [Problème GitHub](https://github.com/magento/magento2/issues/36861) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/40880)_

### GraphQL

#### addProductsToCart renvoie des erreurs sur custom_attributesV2 si le code d’attribut est model

Correction d’un problème en raison duquel addProductsToCart renvoyait une erreur de serveur interne lorsqu’un produit avait un attribut personnalisé avec le modèle de code. L’attribut personnalisé peut désormais être récupéré correctement via custom_attributesV2.

_AC-16987 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/809ba93c)_

#### Quantité GQL nulle lorsque stock_status est IN_STOCK

Le champ de quantité dans la requête GraphQL de produits a incorrectement renvoyé la valeur null pour les produits qui étaient en stock sur un stock MSI personnalisé. Le programme de résolution obtenait la réponse sur la valeur de configuration cataloginventory/options/not_available_message avant de récupérer la quantité réelle de stock, et la valeur XML par défaut de cette configuration (2 — « Pas assez d’articles à vendre ») provoquait le renvoi de la valeur null sur tout nouveau magasin sans remplacement explicite de l’administrateur.
Le contrôle est maintenant évalué une fois la quantité vendable résolue. Une valeur null est renvoyée uniquement lorsque le produit n’a pas de stock disponible (saleableQty &lt;= 0) et que le magasin est explicitement configuré avec « Pas assez d’articles à vendre ». Les produits en stock renvoient toujours leur quantité vendable réelle, quel que soit ce paramètre de configuration. La configuration lue est également corrigée pour utiliser la portée du magasin afin que les remplacements au niveau du magasin soient respectés.

_ACP2E-4840 - [contribution du code GitHub](https://github.com/magento/magento2/commit/b63925d9)_

#### [CLOUD] BundleProduct items.options.price ignore les prix de la portée du site web lorsque Prix du catalogue Scope = Website

Correction des prix des options de bundle de portée site web dans GraphQL : correction d’un problème en raison duquel l’interrogation d’options de produit bundle via GraphQL renvoyait des prix globaux « Toutes les vues de la boutique » au lieu de prix de portée site web lorsque la portée du prix du catalogue était définie sur Site web. Le résolveur Magento\BundleGraphQl\Model\Resolver\Links\Collection vérifie désormais correctement la portée des prix et joint les prix de sélection spécifiques au site web en fonction de la portée du magasin demandée.

_ACP2E-5057 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/597c7211)_

#### Duplication de panier actif créé pour le client en raison d’une condition de concurrence pour les requêtes GraphQL customerCart simultanées

Le système garantit désormais qu’un seul panier actif est créé par client, quelle que soit la simultanéité de la demande. Auparavant, deux requêtes GraphQL customerCart simultanées ou des requêtes REST POST /V1/carts/mine pour le même client authentifié sans panier actif pouvaient entraîner des enregistrements de panier actif en double dans la base de données.

_ACP2E-5077 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/8d70f246)_

#### [Cloud] GraphQlNoSoEntityException gérée à partir de QuoteGraphQl consignée dans exception.log, provoquant une croissance illimitée du journal

Correction d’un problème en raison duquel les erreurs GraphQlNoSoEntityException attendues, telles que celles renvoyées pour un ID de panier expiré ou non valide, étaient écrites sur var/log/exception.log. Ces erreurs gérées sont toujours renvoyées au client sous la forme de réponses d’erreur GraphQL normales, mais elles ne remplissent plus le journal des exceptions.

_ACP2E-5122 - [contribution du code GitHub](https://github.com/magento/magento2/commit/2b9e8316)_

### GraphQL, Inventaire / MSI

#### GraphQL : l’ID de magasin transmis en tant qu’ID de site web dans ProductStock::isProductAvailable cause l’erreur « site web ... not found »

Auparavant, certains storefronts pouvaient rencontrer une erreur de site Web introuvable lors de la vérification de la disponibilité du stock de produits lors de l’ajout d’articles au panier, en raison de l’ID de magasin utilisé lorsqu’un ID de site Web était requis. Ce problème a été corrigé de sorte que les contrôles de disponibilité du stock utilisent le contexte correct du site web, empêchant l’erreur.

_ACP2E-5242 - [contribution du code GitHub](https://github.com/magento/magento2/commit/597c7211)_

### GraphQL, Commande

#### [Requête de fonctionnalité] effacer les données redondantes dans les données de retrait en magasin lors du changement de transporteur

Lors du passage de la collecte en magasin à la méthode de livraison à domicile, l’emplacement de la collecte et l’adresse du magasin associé sont supprimés du panier. Une adresse de livraison valide doit être fournie avant que la commande puisse être passée.

_ACP2E-4973 - [contribution du code GitHub](https://github.com/magento/inventory/commit/57047d29)_

### GraphQL, Produit

#### Clé \« model\ » manquante dans les données de valeur de liste de souhaits

Correction d’un problème en raison duquel l’interrogation des détails de liste de souhaits via GraphQL renvoyait une erreur de serveur interne.
La requête de liste de souhaits est désormais renvoyée sans l’erreur « Modèle de clé manquant dans les données de valeur de la liste de souhaits ».

_AC-8062 - [Problème GitHub](https://github.com/magento/magento2/issues/36909) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/515d3dd3)_

### Importer et exporter

#### [Problème] Correction de la visibilité de l’iframe d’importation

Pour garantir une interface utilisateur épurée et soignée dans le panneau d’administration Magento, un défaut de disposition de modèle a été résolu : un iframe d’exécution en arrière-plan interne est devenu visible par les responsables de stockage lors des validations de données

_AC-13250 - [Problème GitHub](https://github.com/magento/magento2/issues/39267) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/39265)_

#### [Problème] correctif : algorithme de hachage xxh128 codé en dur dans l’importation du produit

Pour nettoyer les sous-systèmes internes et tirer parti des lignes de base d’optimisation des systèmes modernes, le composant d’importation de produit a été rationalisé afin d’utiliser un seul algorithme de hachage permanent.

_AC-16967 - [Problème GitHub](https://github.com/magento/magento2/issues/40770) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/40687)_

#### Le bouton Importer reste disponible après les erreurs de validation lorsque la stratégie de validation est définie sur « Arrêter en cas d’erreur »

Correction du problème en raison duquel le bouton Importer était toujours affiché dans les résultats de validation après un échec de validation des données lorsque la stratégie de validation était définie sur « Arrêter en cas d’erreur ». Auparavant, le bouton s’affichait et pouvait être activé même si tous les enregistrements n’avaient pas été validés, de sorte que la tentative d’importation a été immédiatement arrêtée.

_ACP2E-5124 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/2b9e8316)_

### Installer et administrer

#### [Cloud] Correction des codes de subdivision ISO existants obsolètes

Mise à jour des codes de région pour 13 pays afin qu’ils correspondent à la norme ISO 3166-2. Auparavant, certains codes de région ne correspondaient pas à la norme, ce qui pouvait entraîner des problèmes au niveau des intégrations tierces et de la conformité internationale. Ajout de nouvelles régions pour la Belgique, la Colombie, l’Espagne, la France, l’Italie et la Lettonie. Codes de région mis à jour pour l’Autriche, la Colombie, le Costa Rica, l’Allemagne, l’Estonie, l’Espagne, la Finlande, la France, l’Inde, l’Islande et la Lettonie.

_ACP2E-4495 - [contribution du code GitHub](https://github.com/magento/magento2/commit/9b6a8bd9)_

### Inventaire / MSI

#### [CLOUD] Carte cadeau et apparentée non vendable WF-1688

Le produit ne disparaît pas lorsque des stocks/sources autres que ceux par défaut sont utilisés et que les produits associés (liés ou de montée en gamme ou de vente croisée) sont enregistrés.

_ACP2E-4741 - [contribution du code GitHub](https://github.com/magento/inventory/commit/30fbdb0f)_

#### Incohérence du statut du stock de produits groupés

Auparavant, lorsque l’administrateur d’un magasin mettait à jour manuellement l’état du stock d’un produit groupé à partir du panneau d’administration, la modification n’était pas répercutée sur le storefront pour les magasins configurés avec plusieurs sources d’inventaire. Les clients continueraient à voir le statut de stock obsolète malgré les modifications de l’administrateur.

Ce problème a été résolu. Les modifications de statut du stock de produits groupés effectuées dans le panneau d’administration sont désormais correctement propagées à toutes les sources d’inventaire et à tous les emplacements de stock configurés, ce qui garantit que les clients voient toujours la disponibilité précise du stock sur le storefront.

_ACP2E-4866 - [Contribution du code GitHub](https://github.com/magento/inventory/commit/db712a46)_

#### NoTelEntityException « le magasin demandé est introuvable » généré par GetStockIdForCurrentWebsite.php

Correction d’un problème en raison duquel la visite d’une page de storefront avec un paramètre de requête ?store= non valide entraînait l’enregistrement d’une NoLikeEntityException au niveau CRITIQUE pour chaque requête de ce type. Auparavant, le plug-in de données de stock MSI transmettait le code de magasin brut directement à StoreManager::getStore() sans gérer le cas où le magasin n’existait pas, ce qui entraînait un encombrement des journaux d’exceptions.

_ACP2E-5003 - [contribution du code GitHub](https://github.com/magento/inventory/commit/1bf25e46)_

### Ordre

#### Annuler l’observateur de commande non exécuté lorsque la portée est frontend ou webapi_rest

Correction d’un problème en raison duquel l’annulation d’une commande à partir du storefront ou via la portée webapi_rest n’exécutait pas correctement l’observateur d’annulation. Les montants des cartes-cadeaux sont maintenant rétablis dans le crédit de la boutique du client lorsque la commande est annulée.

_AC-16353 - [Problème GitHub](https://github.com/magento/magento2/issues/40414) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/64eb754d)_

#### La règle de prix de panier avec utilisation limitée n’est pas appliquée lors de la modification d’une commande existante dans Admin (par exemple, « Utilisations par client = 1 »).

Correction d’un problème en raison duquel les remises de la règle de prix du panier avec des limites d’utilisation étaient supprimées lors de la modification d’une commande existante dans Admin. La remise d’origine est désormais conservée lorsque la commande est modifiée, même après que la limite d’utilisation a été atteinte.

_AC-16671 - [Problème GitHub](https://github.com/magento/magento2/issues/40624) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/c10554e1)_

#### Erreur de validation de quantité minimale dans le panneau d’administration pour les produits groupés

Pour améliorer l&#39;expérience de commande du serveur principal et supprimer les blocs fonctionnels lors de la génération de devis manuels, une erreur de validation a été résolue lorsque les paramètres d&#39;article enfant ont été évalués de manière incorrecte lors de la création de la commande d&#39;administration.

_AC-17193 - [Problème GitHub](https://github.com/magento/magento2/issues/40812) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/40863)_

#### Incohérence de la quantité d&#39;article enfant du produit groupé dans la vue de commande front-end

La page Détails de la commande de Storefront affiche désormais la quantité totale commandée pour chaque option de produit groupé. Auparavant, la colonne Quantité de chaque option enfant affichait la quantité commandée du lot parent au lieu de la quantité totale commandée par option.

_ACP2E-4820 - [contribution du code GitHub](https://github.com/magento/magento2/commit/b63925d9)_

#### [ASUS] OrderMutex::execute() manquant DeadlockException provoque l&#39;échec permanent de ShipOrder/InvoiceOrder-

Les opérations ShipOrder et InvoiceOrder sont maintenant résolues avec succès en cas d&#39;impasse.
Auparavant, les opérations ShipOrder et InvoiceOrder échouaient définitivement en raison d&#39;un blocage

_ACP2E-4913 - [contribution du code GitHub](https://github.com/magento/magento2/commit/51f6d191)_

#### Calcul au niveau des lignes FPT/WEEE incorrect sur les articles configurables parents pendant la génération des factures

Les totaux généraux des factures et des avoirs pour les produits configurables incluent désormais correctement le montant de taxe fixe sur les produits. Auparavant, les montants au niveau des lignes FPT n&#39;étaient pas propagés à l&#39;article de commande configurable parent, ce qui entraînait une facture et un avoir totaux inférieurs au total général de la commande par le montant FPT.

_ACP2E-4977 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/51f6d191)_

#### Quantités de produits modifiées lors de l’actualisation de la page lors de la création de la commande auprès de l’administrateur

Correction d’un problème en raison duquel l’actualisation de la page pouvait entraîner l’ajout multiple du même SKU.

_ACP2E-5046 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/ec436b10)_

#### Les programmes de travail asynchrones simultanés envoient des e-mails de confirmation de commande en double pour la même commande

Correction d’un problème en raison duquel les programmes de travail de messagerie simultanés pouvaient envoyer des e-mails de confirmation de commande en double pour la même commande.

_ACP2E-5059 - [contribution du code GitHub](https://github.com/magento/magento2/commit/8d70f246)_

#### La mémoire de la tâche cron [CLOUD] sales_clean_quotes est insuffisante

Correction du problème en raison duquel la mémoire de la tâche cron sales_clean_quotes était insuffisante lors du nettoyage d’un grand nombre de devis expirés. Auparavant, la tâche conservait chaque devis traité en mémoire et se terminait par une erreur fatale d’épuisement de la mémoire avant la suppression de tous les devis expirés.

_ACP2E-5137 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/4d0357d7)_

### Commande, Promotion

#### [Cloud] Problème lors de l’ajout de plusieurs coupons à réorganiser

Correction d’un problème en raison duquel les coupons valides n’étaient plus appliqués à une commande après l’échec d’une tentative de coupon non valide. Désormais, si un coupon non valide est saisi, tous les coupons valides précédemment appliqués resteront appliqués correctement.

_ACP2E-4810_

#### La règle de prix de panier de catégorie à montant fixe réduit les enfants de lot dynamique non correspondants lorsque la règle correspond au parent du lot

Correction d’un problème en raison duquel une règle de prix de panier à montant fixe avec une condition de catégorie appliquait incorrectement une remise à tous les enfants d’un lot à prix dynamique lorsque la règle ne correspondait qu’au parent du lot. Auparavant, les enfants de l’offre groupée qui n’appartenaient pas à la catégorie ciblée recevaient une part de la remise calculée au prorata, au lieu de zéro.

_ACP2E-5075 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/2b9e8316)_

### Paiements

#### La commande config:show ne fonctionne pas avec les chemins partiels dans les versions plus récentes

La commande `config:show` accepte désormais les chemins de configuration partiels, tels que le paiement, et affiche les valeurs de configuration sous ce chemin. Auparavant, l’exécution `php bin/magento config:show` paiement renvoyait une erreur : `The "payment" path doesn't exist. Verify and try again.` au lieu d’afficher les valeurs correctes.

_AC-13908 - [Problème GitHub](https://github.com/magento/magento2/issues/39610) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/40432)_

### Performances

#### le programme d:upgradeinstallation modifie le mode de l’indexeur pour `save` de `schedule` à le ralentir considérablement

Correction d’un problème de longue date en raison duquel l’exécution de la configuration bin/magento:upgrade modifiait par inadvertance les modes de l’indexeur de « Enregistrer dans les délais » à « Enregistrer dans les délais » et supprimait et recréait inutilement les déclencheurs de base de données, réduisant ainsi considérablement les temps d’arrêt et empêchant les goulots d’étranglement des performances lors des déploiements sur des catalogues volumineux.

_AC-2423 - [Problème GitHub](https://github.com/magento/magento2/issues/33386) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/40643)_

#### Les clés de cache Valkey LAYOUT occupent beaucoup d&#39;espace pour un catalogue de produits volumineux

Auparavant, chaque produit générait sa propre entrée de cache LAYOUT par vue de magasin, provoquant une consommation excessive de mémoire dans Redis/Valkey sur les catalogues volumineux. Désormais, les entrées du cache de mise en page sont partagées entre les produits avec le même type, le même jeu d’attributs et la même vue de magasin, ce qui limite la croissance du cache quelle que soit la taille du catalogue.

_ACP2E-4908 - [contribution du code GitHub](https://github.com/magento/magento2/commit/9b6a8bd9)_

#### Erreur de blocage sur la requête de produit

Correction d’un blocage InnoDB sur les pages avec une liste de produits CatalogWidget filtrée par catégorie, qui se produisait lorsque l’indexeur de prix en mode horaire s’exécutait simultanément.

_ACP2E-5052 - [contribution du code GitHub](https://github.com/magento/magento2/commit/ec436b10)_

#### [Quans] dégradation des performances des requêtes de résolution d’URL Adobe Commerce

Correction du problème où la requête d’itinéraire GraphQL affichait toujours le contenu complet de la page CMS, y compris l’exécution du widget Page Builder et le chargement de la collection de produits, même lorsque seules des métadonnées de routage d’URL (relative_url, redirect_code, type) étaient demandées. Auparavant, cela provoquait un rendu inutile de widget/produit et une augmentation significative des requêtes de base de données par requête pour les pages CMS contenant des widgets Page Builder.

_ACP2E-5143 - [contribution du code GitHub](https://github.com/magento/magento2/commit/597c7211)_

#### Administrateur - Client - Modifier les réservoirs de performances lorsque le Partage de compte client est défini sur Global

Correction d’un problème de performances sur la page Modifier des clients administrateurs où le temps de chargement et la taille de réponse HTTP augmentaient de manière quadratique lorsque le paramètre Partager les comptes client était défini sur Global.

_ACP2E-5164 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/24667df1)_

### Produit

#### Le bouton Ajouter au panier dans la fenêtre contextuelle « Cliquer pour le prix » ne fonctionne pas.

Correction d’un problème en raison duquel le bouton Ajouter au panier dans la fenêtre contextuelle « Cliquer pour voir le prix » de la page de liste des produits n’ajoutait pas le produit au panier.
Les produits peuvent désormais être ajoutés au panier à partir de la fenêtre contextuelle.

_AC-11896 - [Problème GitHub](https://github.com/magento/magento2/issues/30356) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/29a7cdbe)_

#### Les résolveurs GraphQL Bundle créent des instances de produit différé distinctes, ce qui annule le traitement par lots des requêtes (N+1)

Afin d’accélérer considérablement le débit de réponse de l’API et de minimiser la surcharge du serveur, la couche de résolution GraphQL a été optimisée pour appliquer un vrai traitement par lots des requêtes pour les produits groupés, éliminant les fuites de base de données N+1 qui drainent les performances.

_AC-16647 - [Problème GitHub](https://github.com/magento/magento2/issues/40595) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/40867)_

#### La validation des attributs EAV Select et Multiselect rejette incorrectement les libellés d’option avec la valeur « 0 »

Pour améliorer l’intégrité des données et éliminer les erreurs d’envoi inattendues dans les formulaires client et de catalogue, une erreur de validation a été résolue où les libellés d’option contenant la valeur de chaîne exacte « 0 » ont été rejetés par erreur par le framework principal de l’EAV

_AC-16986 - [Problème GitHub](https://github.com/magento/magento2/issues/40634) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/40827)_

#### Les libellés d’option personnalisables et les titres d’option personnalisables ne peuvent pas être enregistrés lorsque le rôle d’un utilisateur est limité à une certaine portée

Correction d’un problème en raison duquel les libellés et titres d’options personnalisables étaient rétablis lorsqu’ils étaient modifiés par un utilisateur administrateur dont l’accès était limité à une portée de magasin spécifique.
Les libellés et titres mis à jour sont désormais correctement enregistrés pour la portée sélectionnée.

_AC-2684 - [Problème GitHub](https://github.com/magento/magento2/issues/35210)_

#### Le prix de la carte cadeau ne s&#39;affiche pas correctement dans la liste de souhaits

Correction d’un problème en raison duquel le prix minimum de la carte cadeau configurée s’affichait comme 0,00 $ dans la liste de souhaits.
Le prix minimum correct de la carte cadeau est maintenant affiché sur la page Ma liste de souhaits et le widget de la barre latérale Liste de souhaits.

_AC-8037_

#### Alerte de produit Le client ignore le système défini pour le magasin/stmp/disable

Le consommateur d’alerte de produit prend désormais en compte le paramètre système / stmp / disable pour le magasin.

_ACP2E-4870 - [contribution du code GitHub](https://github.com/magento/magento2/commit/ec436b10)_

#### Page de comparaison frontale affichant des traductions incorrectes des libellés de description courte

Auparavant, sur la page Comparer des produits , des libellés d’attribut comparables tels que Description courte pouvaient afficher une traduction provenant d’une vue de magasin différente au lieu de celle du magasin actuel. Désormais, les traductions appropriées spécifiques au magasin s’affichent.

_ACP2E-4929 - [contribution du code GitHub](https://github.com/magento/magento2/commit/08b91f1a)_

#### Le carrousel de produits Page Builder ignore l’ordre de tri des positions de catégorie et affiche les produits dans l’ordre entity_id DESC à la place

Correction d’un problème en raison duquel les produits affichés dans un carrousel Page Builder défini pour un tri par position de catégorie s’affichaient dans le mauvais ordre sur le storefront. Les produits s’affichent désormais dans l’ordre configuré dans l’onglet Admin → Catalog → Categories → Products .

_ACP2E-4980 - [contribution du code GitHub](https://github.com/magento/magento2/commit/51f6d191)_

### Règles de promotion

#### Mauvais calcul de remise lorsque l&#39;une des règles de prix de panier appliquées a une valeur d&#39;étape de quantité de remise

Correction d’un problème en raison duquel la remise n’était pas calculée correctement lorsque plusieurs règles de prix de panier étaient appliquées et qu’une règle avait une valeur d’étape de quantité de remise (Acheter X).
Les remises sont désormais calculées correctement pour toutes les quantités éligibles.

_AC-12307 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/c10554e1)_

### Promotion, ciblage

#### Les produits associés sont automatiquement supprimés

Correction d’un problème en raison duquel les produits associés n’étaient pas supprimés lorsque les attributs d’un produit changeaient et qu’il cessait de correspondre à une règle Target. Auparavant, le moteur d’indexation mview ne pouvait pas supprimer les associations obsolètes entre les règles et les produits et émettait un avertissement PHP (clé de tableau non définie) lors de la réindexation.

_ACP2E-4836_

### Renvoie

#### RMA - API Ajouter des commentaires de retour - Les e-mails sont déclenchés pour l’expéditeur (représentant commercial), mais pas pour le client

Correction d’un problème en raison duquel les e-mails de commentaires sur les retours envoyés par le biais de l’API de retours étaient envoyés au commercial, mais pas au client.
Les clients reçoivent désormais une notification par e-mail lorsqu’un commentaire de retour est ajouté via l’API avec la notification du client activée.

_AC-1138 - [Problème GitHub](https://github.com/magento/magento2/issues/33985)_

### Ventes

#### `[Order][REST]` colonne sales_order_items product_options ne contient pas de données lorsque la commande est passée à partir de l’api rest V1/orders ou V1/orders/create endpoints

Correction d’un problème en raison duquel les éléments de commande créés via l’API REST n’incluaient pas de données product_options complètes. Les libellés d’option personnalisés et les détails d’option pertinents sont désormais correctement enregistrés pour les commandes créées via l’API REST.

_AC-15187 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/8b67e8ed)_

#### La grille de commande client est bloquée de manière permanente au statut périmé lorsque l&#39;indexation asynchrone de grille est activée en raison des horodatages updated_at liés

Correction d’un problème en raison duquel la grille des commandes client pouvait rester bloquée avec un statut de commande obsolète lorsque l’indexation asynchrone de la grille était activée. Le statut de la grille de commandes est désormais correctement mis à jour pour correspondre au statut actuel de la commande, y compris dans les cas où plusieurs mises à jour de commande se produisent au cours de la même seconde.

_AC-17118 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/478f8e7c)_

### Sécurité

#### [Problème ] mettez à jour le texte DOM js.phtml réinterprété comme HTML.

Pour renforcer la base de sécurité de la plateforme et minimiser le risque d’exécution d’entrée malveillante, le modèle de script intégré principal gérant les mises à jour DOM dynamiques a été restructuré afin d’éliminer les vecteurs d’injection de script entre sites (XSS).

_AC-12118 - [Problème GitHub](https://github.com/magento/magento2/issues/38821) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/38804)_

### Expédition

#### Problème avec l’API REST USPS, taux incorrects pour le poids maximal du package

Correction d’estimations d’expédition incorrectes lorsqu’une commande est divisée en plusieurs packages (par exemple, au-dessus du « Poids maximal du package »). L’opérateur demande désormais un taux pour chaque package et totalise les montants, conformément au flux des outils web hérités.

_ACP2E-4813 - [contribution du code GitHub](https://github.com/magento/magento2/commit/6c67a9b5)_

### Évaluation et prévisualisation

#### Erreurs de console en mode d’aperçu de la mise à jour du planning

Correction d’un problème en raison duquel la page d’aperçu d’une mise à jour d’évaluation ne se chargeait pas correctement avec des erreurs de console JavaScript lorsque deux mises à jour partageaient la même heure de début. Auparavant, l’URL d’aperçu signée utilisait un ID de version incrémenté qui ne correspondait pas à la date et à l’heure dérivées par le JavaScript d’aperçu, ce qui entraînait une incohérence des signatures et empêchait le chargement correct de la page en mode aperçu.

_ACP2E-4828_

#### La configuration :upgrade prend trop de temps sur le correctif de données Magento_CatalogStaging avec un grand nombre de magasins, vues et catégories.

Correction d’un problème en raison duquel le correctif de migration de données CE vers EE ne migrait pas correctement les mises à jour de conception de catégorie planifiées et les prix spéciaux des produits dans les mises à jour d’évaluation. Les catégories avec des dates de conception planifiées ont produit des mises à jour d’évaluation vides en raison d’une approche de contexte d’évaluation incorrecte. Les produits étaient silencieusement ignorés sur PHP 8.1+ lorsque les valeurs de date et d&#39;heure NULL étaient présentes lors d&#39;une migration précédente. Amélioration des performances de migration en chargeant uniquement les catégories et produits concernés au lieu d’itérer le catalogue complet.

_ACP2E-5009_

#### La grille Règles de prix du catalogue du tableau de bord d’évaluation de contenu affiche les données en double

La grille Règles de prix du catalogue affiche désormais correctement les détails uniques de chaque règle de prix du catalogue affectée à une mise à jour d&#39;évaluation. Auparavant, lorsque plusieurs règles de prix de catalogue étaient affectées à la même mise à jour d&#39;évaluation, la grille Règles de prix de catalogue sur la page de cette mise à jour dans le tableau de bord d&#39;évaluation de contenu affichait le nombre correct de lignes, mais chaque ligne affichait incorrectement les mêmes données de la (dernière) règle au lieu des détails de chaque règle.

_ACP2E-5097_

### Taxe

#### base_wee_tax_applied_amount n&#39;est pas défini pour le produit parent

la valeur base_weee_tax_applied_amount est désormais renseignée pour le produit configurable dans les tables de base de données telles que sales_order_item, sales_facture_item, sales_creditmemo_item, et pas seulement pour son enfant

_ACP2E-4922 - [contribution du code GitHub](https://github.com/magento/magento2/commit/08b91f1a)_

### Framework de test

#### [Problème] Mettre à jour GraphQL teste Client.php pour une comparaison de sous-chaînes insensible à la casse

Correction d’un problème en raison duquel les tests de l’API GraphQL ne reconnaissaient pas les en-têtes Set-Cookie lorsque l’en-tête utilisait une casse différente. Les tests gèrent désormais correctement les en-têtes Set-Cookie, set-cookie et SET-COOKIE.

_AC-15337 - [Problème GitHub](https://github.com/magento/magento2/issues/39713) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/c10554e1)_

#### Tests fonctionnels GraphQL WebAPI extrêmement lents

Pour optimiser les configurations de diffusion de build et accélérer les environnements d’intégration continue (CI), un goulot d’étranglement d’infrastructure de test a été résolu en faisant passer les comportements d’effacement du cache des appels de commande système externes à la gestion native de la mémoire en cours de processus.

_AC-15395 - [Problème GitHub](https://github.com/magento/magento2/issues/39725) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/40804)_

### Framework de l’interface utilisateur

#### Le minicart ne peut pas être utilisé deux fois sur la même page

Pour offrir aux développeurs front-end une plus grande flexibilité de mise en page, une limitation de longue date de l’interface utilisateur de base a été résolue, ce qui permet à plusieurs blocs mini-art (par exemple, un dans l’en-tête et un autre dans le pied de page) d’exister et de se mettre à jour indépendamment sur une seule mise en page.

_AC-12579 - [Problème GitHub](https://github.com/magento/magento2/issues/38958) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/40871)_

### from-github

#### [Problème] correctif (pagecache) : reconnaître PATCH comme méthode HTTP valide dans le VCL de vernis

Le VCL de vernis par défaut de Magento reconnaît désormais PATCH comme une méthode HTTP valide, de sorte que les demandes de mise à jour partielle de l’API REST (par exemple, PATCH /rest/V1/products/:sku) sont transmises au serveur principal au lieu d’être transmises. Cette option corrige les échecs d’appels PATCH ou les comportements incorrects lorsque le cache de page complet est défini sur Vernis.

_AC-16954 - [Problème GitHub](https://github.com/magento/magento2/issues/40757) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/40657)_

#### [Problème] Remplacer tous les paramètres gad_* dans VCL

Pour éliminer les régressions de performances dues aux campagnes publicitaires dynamiques, les couches de mise en cache de l’application ont été mises à jour afin d’ignorer de manière proactive toutes les chaînes de requête gad_* de Google Ads. Cela empêche les liens de campagne externes d’invalider les caches de page et de ralentir les pages cibles

_AC-16980 - [Problème GitHub](https://github.com/magento/magento2/issues/40781) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/40780)_

#### [Problème] correctif : mettez à jour la version PHP minimale pour démarrer avec la version 8.3

Pour éviter les erreurs d’exécution déroutantes et améliorer la résolution des problèmes d’installation du développeur, le programme de validation d’environnement PHP natif dans le framework de bootstrap du système a été mis en conformité avec les exigences principales réelles de l’application.

_AC-17312 - [Problème GitHub](https://github.com/magento/magento2/issues/40851) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/40686)_

#### `health_check.php` renvoie 500 lorsque `igbinary` est installé et que le cache de fichier par défaut est utilisé (vernis 503)

Correction d’un problème en raison duquel health_check.php renvoyait HTTP 500 lorsque igbinary était installé avec le serveur principal du cache de fichiers par défaut. Le contrôle de l’intégrité accepte désormais les configurations de cache valides sans clé principale explicite, ce qui empêche Varnish de marquer le serveur principal comme malsain et de renvoyer le HTTP 503.

_AC-17400 - [Problème GitHub](https://github.com/magento/magento2/issues/40876) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/8b67e8ed)_

#### [Problème] correction : mettez à jour les types gzip et supprimez la solution de contournement IE6 dans la configuration nginx

Pour améliorer la vitesse de chargement des pages et optimiser la diffusion des ressources réseau, la configuration de serveur de secours a été modernisée afin de mieux prendre en charge les composants storefront modernes et de supprimer la surcharge technologique héritée

_AC-17498 - [Problème GitHub](https://github.com/magento/magento2/issues/40774) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/40681)_

#### [Problème] Tentative de correction d&#39;un paramètre GraphQL non fiable OrderStatusChangeDateTest.

Pour améliorer la fiabilité de l’intégration continue (CI) et réduire les échecs de génération de faux positifs, une condition de concurrence a été résolue dans la suite de tests fonctionnels WebAPI. Le test de validation du statut de la commande GraphQL (OrderStatusChangeDateTest) a déjà connu des échecs intermittents dus à de subtiles disparités de minutage entre la mémoire PHP et les horodatages MySQL

_AC-17959 - [Problème GitHub](https://github.com/magento/magento2/issues/41126) - [Contribution du code GitHub](https://github.com/magento/magento2/pull/40618)_
