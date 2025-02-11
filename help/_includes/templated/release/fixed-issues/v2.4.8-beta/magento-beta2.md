---
source-git-commit: cfaa71f84f7d27d41c9d991aceef0087ee3d8ec0
workflow-type: tm+mt
source-wordcount: '8487'
ht-degree: 0%

---
# Notes de mise à jour de Magento Open Source (v2.4.8-beta2)

## Caractéristiques de la version v2.4.8-beta2

Les 30 points forts suivants s’appliquent à la version 2.4.8 de Magento Open Source.

### Braintree

* _BUNDLE-3400_ : supprimer les LPM non pris en charge
   * _Contribution du code GitHub_ : <https://github.com/magento/ext-braintree/pull/208>
* _BUNDLE-3401_ : Google Pay Mark
   * _Contribution du code GitHub_ : <https://github.com/magento/ext-braintree/pull/208>
* _BUNDLE-3402_ : Apple Pay Mark
   * _Contribution du code GitHub_ : <https://github.com/magento/ext-braintree/pull/208>
* _BUNDLE-3403_ : rappel de paiement d&#39;expédition Google
   * _Contribution du code GitHub_ : <https://github.com/magento/ext-braintree/pull/208>
* _BUNDLE-3404_ : messagerie Pay Later
   * _Contribution du code GitHub_ : <https://github.com/magento/ext-braintree/pull/208>
* _BUNDLE-3405_ : bouton JS-SDK
   * _Contribution du code GitHub_ : <https://github.com/magento/ext-braintree/pull/208>
* _BUNDLE-3406_ : optimisation du code dans l’extension Braintree
   * _Contribution du code GitHub_ : <https://github.com/magento/ext-braintree/pull/208>
* _BUNDLE-3407_ : mise à jour de Braintree PHP et JS SDK
   * _Contribution du code GitHub_ : <https://github.com/magento/ext-braintree/pull/208>
* _BUNDLE-3408_ : Lignes (GooglePay)
   * _Contribution du code GitHub_ : <https://github.com/magento/ext-braintree/pull/208>
* _BUNDLE-3409_ : Lignes de commande (Apple Pay)
   * _Contribution du code GitHub_ : <https://github.com/magento/ext-braintree/pull/208>
* _BUNDLE-3420_ : suivi de packages
   * _Contribution du code GitHub_ : <https://github.com/magento/ext-braintree/pull/208>

### Framework

* _AC-12012_ : Mise à jour de la version Nginx de 1.24 à 1.26
* _AC-12028_ : ajouter la compatibilité avec la dernière version du compositeur 2.8 pour les versions 2.4.8 et 2.4.7
* _AC-12029_ : Vérifier la compatibilité avec Varnish 7.6
* _AC-12970_ : PHPUnit 10 upgrade part 2 - Supprimer les obsolètes
   * _Remarque de correction_ : mise à jour des dépendances phpunit/phpunit composer vers une version compatible - « phpunit/phpunit »:« 10.x »
* _AC-13076_ : mettez à jour toutes les dépendances de bibliothèque js et npm avec la dernière version disponible.
   * _Remarque sur la correction_ : la prise en charge de la version du compositeur ne concernait que la version 2.2.x du compositeur. Désormais, la prise en charge s’étend également à la version 2.4.x.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/19844aa0>
* _AC-13077_ : Toutes les extensions groupées et les composants intégrés sont compatibles avec PHP 8.4
* _AC-13078_ : Tous les outils Adobe Commerce sont compatibles avec PHP 8.4
* _AC-13079_ : Tous les laminas/dépendances du projet Adobe Commerce sont compatibles avec PHP 8.4
* _AC-13256_ : rétrogradation de la dépendance TinyMCE de la version 7 à la version 6.8.5
* _AC-13276_ : les dépréciations de PHP 8.4 nécessitent des modifications avec rupture d&#39;Adobe Commerce
* _AC-8828_ : définissez le classement par défaut sur utf8mb4 pour MySQL

### Autres frais

* _AC-12133_ : le code principal Adobe Commerce 2.4.8 est compatible avec PHP 8.4
* _AC-12972_ : Améliorations de la qualité de base de la version 2.4.8-beta2
* _AC-13038_ : Supprimer PHP 8.1 de composer.json et toute prise en charge connexe
* _AC-13448_ : correctif d’amélioration des performances des opérations au niveau du prix dans 2.4.8
   * _Remarque de correctif_ : le système permet désormais des mises à jour en bloc plus efficaces des prix de niveau sans causer de problèmes de performances ou d’absence de réponse du site lors de l’utilisation du point d’entrée de l’API REST « /V1/products/tier-prices ». Auparavant, la mise à jour d’un grand nombre de prix à l’aide de ce point d’entrée pouvait entraîner des problèmes de performances et une absence de réactivité du site.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/082d981c>
* _AC-13550_ : supprimer tous les avis de copyright confidentiels Adobe des référentiels Magento Open Source
   * _Remarque sur la correction_ : toutes les notifications de copyright confidentielles Adobe ont été supprimées des référentiels open source, ce qui garantit que seule la forme réduite de copyright Adobe est utilisée. Auparavant, certains fichiers des référentiels publics contenaient des avis confidentiels de copyright Adobe, ce qui entraînait des remontées d’informations de la part de la communauté.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/39493>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/4bca5dfe>

### Sécurité

* _AC-10982_ : [2FA] Intégrez-la à Duo Web SDK pour prendre en charge Universal Prompt
   * _Corriger la note_ : à déterminer

### Framework de test

* _AC-9037_ : possibilité d’utiliser le copyright Adobe pour le code source Adobe Commerce

### Framework de l’interface utilisateur

* _AC-12944_ : supprimer TinyMCE 5 d’adobe commerce

## Correction de problèmes dans la version v2.4.8-beta2

Nous avons corrigé 159 problèmes dans le code principal de Magento Open Source 2.4.8. Un sous-ensemble des problèmes résolus inclus dans cette version est décrit ci-dessous.

### API

* _ACP2E-3236_ : l’opération asynchrone échoue lorsque le SKU est absent de la payload
   * _Remarque de correction_ : les opérations asynchrones et de synchronisation ont précédemment échoué en raison d’erreurs d’enregistrement du produit si le SKU est absent de la payload. Après le correctif, les opérations de l’api rest d’enregistrement de produit asynchrones et synchronisées échouent avec un message d’exception approprié.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/66dea0de>
* _ACP2E-3376_ : [CLOUD] impossible de mettre à jour les prix de base à l’aide de l’API REST (la valeur de « value_id » dans « catalog_product_entity_decimal » n’est pas incrémentée correctement.)
   * _Remarque sur la correction_ : auparavant, lorsque l’api rest /rest/default/V1/products/base-prices était appelée, l’ID d’incrément était augmenté par erreur, laissant un écart entre les valeurs. Après la correction, l’ID d’incrément est augmenté comme prévu, de manière incrémentielle. La plage de champs value_id a également été augmentée.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/d50f6b5d>
* _ACP2E-3486_ : les valeurs par défaut ne sont pas définies pour les attributs de date et d’heure avec les produits RestAPI
   * _Correction d’une remarque_ : les valeurs par défaut sont désormais correctement définies pour les attributs de date et de date et d’heure via RestAPI
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/1984c61c>

### API, panier et passage en caisse

* _ACP2E-3343_ : erreur critique 500 : Magento\Framework\Webapi\Exception liée à l’acceptation de l’en-tête HTTP
   * _Remarque sur la correction_ : après la correction, il n’y a plus de problème avec la spécification de l’en-tête « Accepter ».
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/1366ae5e>

### Compte

* _AC-10886_ : mise à jour du mot de passe de l’administrateur.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38352>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/4bca5dfe>
* _AC-11718_ : boucle de redirection lorsque les URL sont en majuscules
   * _Remarque à propos de la correction_ : le système convertit désormais automatiquement les caractères majuscules des URL en minuscules, ce qui empêche l’apparition d’une boucle de redirection lors de l’accès à la page d’accueil. Auparavant, la présence de caractères majuscules dans l’URL de base sécurisée entraînait une boucle de redirection continue lors de la tentative d’accès à la page d’accueil.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38538>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/38539>
* _AC-13000_ : la case à cocher Se connecter en tant que client ne peut pas être traduite
   * _Remarque à corriger_ : le système permet désormais de définir les champs « Case à cocher Se connecter en tant que client opt-in » et « Infobulle de la case à cocher Se connecter en tant que client » sur la portée « Affichage de la boutique », ce qui permet d’obtenir des traductions pour différents affichages de la boutique. Auparavant, ces champs n’étaient définis que sur la portée « Site web », ce qui empêchait les traductions pour les vues de magasin individuelles.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/32329>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/32359>
* _ACP2E-3329_ : après s’être connecté, les produits ajoutés à la liste de comparaison en tant qu’utilisateur invité ne sont pas visibles.
   * _Remarque sur la correction_ : les produits qui ont été ajoutés à la liste de comparaison des produits avant de se connecter en tant que client sont désormais conservés après la connexion.
Auparavant, après s’être connecté, les produits ajoutés à la liste de comparaison en tant qu’utilisateur invité n’étaient pas visibles.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/078c387e>
* _ACP2E-3433_ : la configuration Autoriser les pays entraîne des problèmes dans les configurations d’adresses client
   * _Remarque à propos de la correction_ : la sélection de la configuration Autoriser les pays n’influence pas les pays affichés pour en dehors de la portée donnée. Auparavant, la configuration Autoriser les pays avait influencé l’attribut d’adresse du client en dehors de la portée donnée
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/078c387e>

### Compte, API, GraphQL

* _ACP2E-3246_ : API Client - Le Nombre D’Échecs De Connexion Ne Peut Pas Être Réinitialisé À 0 Après Une Connexion Réussie
   * _Remarque de correction_ : le numéro d’échec est désormais réinitialisé sur zéro dans la table des entités client après la connexion réussie du client via les points d’entrée de l’API.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/ec7e32a9>

### Compte, interface utilisateur d’administration, B2B

* _ACP2E-3038_ : les utilisateurs administrateurs restreints ne peuvent pas toujours voir les catalogues partagés personnalisés
   * _Remarque de correction_ : les utilisateurs administrateurs restreints peuvent désormais afficher et gérer de manière cohérente les clients et tous les catalogues partagés auxquels les produits sont affectés, à condition qu’ils aient accès à la boutique spécifique. Auparavant, un utilisateur administrateur restreint ayant accès à une boutique particulière ne pouvait pas toujours voir tous les catalogues partagés auxquels les produits étaient affectés ou pouvait voir les clients qui ne pouvaient pas effectuer d’enregistrement, ce qui entraînait des incohérences dans le système.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/7377de59>

### Interface utilisateur d’administration

* _AC-10705_ : [Problème] ajoutez une vérification des autorisations pour le bouton de données « recharger les données »
   * _Remarque sur la correction_ : le système inclut désormais une vérification des autorisations pour le bouton « Recharger les données », afin de s’assurer qu’elles ne s’affichent et ne sont accessibles qu’aux utilisateurs disposant des autorisations appropriées. Auparavant, le bouton « Recharger les données » était visible et cliquable par tous les utilisateurs et utilisatrices, ce qui entraînait l’affichage d’une page « non autorisée » lorsque les utilisateurs et utilisatrices cliquaient dessus sans les autorisations nécessaires.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38283>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/38279>
* _AC-13131_ : [Problème] Avertissement de correctif : clé de tableau non définie « filtres »
   * _Remarque à propos de la correction_ : le système gère désormais les scénarios dans lesquels un nouvel utilisateur n’a pas encore interagi avec les signets, empêchant la journalisation d’un avertissement de « filtres » de clé de tableau non défini. Auparavant, cet avertissement était consigné lorsqu’un nouvel utilisateur n’avait pas interagi avec des signets.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/39013>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/38996>
* _AC-13529_ : Le fichier CSV d&#39;importation de produit avec des caractères spéciaux échoue en raison de changements de code dans le fichier Validate.php
   * _Remarque de correction_ : le système valide et importe désormais correctement les fichiers CSV de produit contenant des caractères spéciaux, ce qui permet de réussir le transfert des données. Auparavant, toute tentative d’importation d’un fichier CSV de produit avec des caractères spéciaux entraînait une erreur, empêchant le processus d’importation.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/6cfb9b6b>
* _AC-7962_ : Aucun lien vers l&#39;expédition lors des paiements en caisse en vue téléphone mobile
   * _Correction de la note_ : le système garantit désormais que les titres/liens de passage en caisse « Expédition » et « Révision et paiements » sont toujours visibles en haut de la page en mode mobile, ce qui permet aux utilisateurs de naviguer facilement entre les étapes et d’effectuer les corrections nécessaires. Auparavant, ces titres/liens étaient masqués en mode mobile, ce qui rendait difficile pour les utilisateurs de connaître l’étape en cours ou de revenir aux étapes précédentes.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/36856>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/36982>
* _AC-8109_ : les commentaires d&#39;expédition de requête de commandes client created_at sont renvoyés dans un fuseau horaire +0 qui n&#39;est pas dans le fuseau horaire configuré du magasin
   * _Correction de note_ : le système affiche désormais correctement le champ &#39;created_at&#39; à partir des commentaires d&#39;expédition dans le fuseau horaire configuré du client lors de l&#39;utilisation de la requête Commandes client. Auparavant, le champ « created_at » s’affichait dans le fuseau horaire +0, quel que soit le fuseau horaire configuré du client.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/36947>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/37642>
* _ACP2E-3294_ : l&#39;état de l&#39;adresse de livraison n&#39;est pas mis à jour automatiquement
   * _Remarque sur la correction_ : avant la correction, la région de l’adresse d’expédition (ou l’ID de région) n’était pas synchronisée avec les informations de facturation de l’adresse. Désormais, la région et l’ID de région de l’adresse de livraison sont correctement mis à jour lorsque les informations de l’adresse de facturation sont modifiées.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/581b7ef1>
* _ACP2E-3364_ : le bouton Réinitialiser ne fonctionne pas sur Ajouter/Modifier l’utilisateur administrateur
   * _Correction de la note_ : auparavant, le bouton Réinitialiser ne fonctionnait pas sur la page Ajouter/modifier un utilisateur administrateur. Désormais, dans le panneau d’administration sous Système -> Autorisations -> Tous les utilisateurs, le bouton Réinitialiser fonctionnera correctement sur la page Ajouter/modifier un utilisateur administrateur .
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/5184c067>
* _ACP2E-3392_ : validation non effectuée de la « quantité maximale autorisée dans le panier »
   * _Correction de note_ : auparavant, lorsque nous mettions `Maximum Qty Allowed in Shopping Cart` vide, aucune exception n’était générée, bien qu’une valeur vide ne soit pas acceptée ici. Une fois que ce correctif est appliqué, le fait de placer une chaîne vide génère des exceptions et ne permet pas d’enregistrer le produit.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/d50f6b5d>
* _ACP2E-3408_ : [problème d’interface utilisateur de l’aperçu de Pagebuilder] les boutons de la colonne Page Builder ne s’alignent pas correctement
   * _Correction de la note_ : les boutons des colonnes du Générateur de page sont désormais correctement alignés. Auparavant, ils n’étaient pas alignés correctement dans les colonnes du Page Builder.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2-page-builder/commit/1a52ef4c>
* _ACP2E-3431_ : le rapport Produits commandés n&#39;est pas exporté. Erreur 404 à la place.
   * _Remarque sur la correction_ : l’exportation du rapport Produits commandés au format CSV et XML fonctionne désormais comme prévu
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/88660e79>
* _ACP2E-3457_ : erreur JS TinyMCE dans la console après l’activation de la minification JS avec le mode de production
   * _Remarque de correction_ : auparavant, l’activation de la minimisation JavaScript en mode production dans le panneau d’administration entraînait l’affichage d’erreurs JavaScript liées à TinyMCE 7 dans la console du navigateur, ce qui affectait les fonctionnalités et l’expérience utilisateur. Maintenant, ce problème a été résolu, en veillant à ce que TinyMCE 7 fonctionne correctement sans générer d&#39;erreurs, même lorsque la minimisation JS est activée.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/56463d5e>
* _ACP2E-3459_ : demande de modifications supplémentaires pour terminer le correctif ACP2E-3375
   * _Corriger la note_ : &#39;-
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/d50f6b5d>

### Interface utilisateur d’administration, Modes de paiement, Commande

* _AC-13520_ : Autorisation de transaction non affichée dans l&#39;onglet Transaction après la commande du bouton intelligent PayPal
   * _Corriger la note_ : Le système affiche désormais correctement l&#39;autorisation de transaction dans l&#39;onglet Transaction après qu&#39;une commande a été passée à l&#39;aide du bouton intelligent PayPal. Auparavant, la transaction d’autorisation n’apparaissait pas dans l’onglet Transaction après avoir cliqué sur le bouton « Autoriser », et aucune nouvelle transaction de type « Autorisation » n’a été créée.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/6cfb9b6b>

### Interface utilisateur d’administration, évaluation et prévisualisation

* _ACP2E-3424_ : [Cloud] la suppression d’un modèle avec des images manquantes entraîne la suppression de médias/pubs
   * _Remarque sur la correction_ : auparavant, si le nom de l’image d’aperçu était manquant pour un modèle pagebuilder, le dossier pub/media était supprimé. Après la correction, seul le modèle est supprimé et l’image d’aperçu, si elle est trouvée.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2-page-builder/commit/0986853b>

### Analyses / Rapports

* _AC-9922_ : erreur Google Analytics CSP https://region1.analytics.google.com
   * _Remarque de correction_ : le système autorise désormais correctement les connexions à « https://region1.analytics.google.com&#39; » lorsque Google Analytics est activé, ce qui empêche les erreurs de politique de sécurité du contenu (CSP). Auparavant, l’activation de Google Analytics et l’affichage du site web depuis l’UE entraînaient des erreurs de console CSP en raison d’un refus de connexion à « https://region1.analytics.google.com&#39; ».
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/37750>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/38991>
* _ACP2E-3183_ : la surveillance du navigateur NewRelic par le script inlineJS provoque des erreurs CSP
   * _Remarque sur la correction_ : les scripts de surveillance du navigateur NewRelic sont désormais injectés par l’application au lieu de l’agent APM pour assurer la conformité avec la CSP (Content Security Policy, politique de sécurité du contenu). Auparavant, les scripts de surveillance du navigateur NewRelic injectés par l’agent APM n’étaient pas conformes à la CSP et empêchaient leur exécution.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/66dea0de>
* _ACP2E-3189_ : les requêtes INSERT à la table sales_bestsellers_aggregated_daily deviennent lentes sur les projets avec un volume de commandes client important
   * _Correction de note_ : auparavant, le rapport quotidien agrégé des meilleures ventes prenait beaucoup de temps à générer pour un grand volume de commandes passées. Le rapport est maintenant généré en temps voulu.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/7377de59>
* _ACP2E-3276_ : rapports de commande affichant le mauvais symbole de devise
   * _Corriger la note_ : Le symbole de devise pour les montants de commande dans l&#39;état des commandes a été extrait de manière incorrecte de la devise/des options/de la base. Correction de l’utilisation de la devise, des options et de la valeur par défaut pour un compte rendu des performances précis.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/fd5cf3af>
* _ACP2E-3302_ : [Cloud] calculs incorrects dans le rapport d’utilisation des coupons
   * _Corriger la note_ : Le total des ventes dans la grille d&#39;état des coupons est désormais calculé avec précision en incorporant le « Montant de la remise de taxe » et le « Montant de la remise de taxe d&#39;expédition ». Auparavant, ces montants étaient absents du calcul, ce qui entraînait des écarts entre le total des ventes et les données des commandes client.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/d75cff27>
* _ACP2E-3339_ : problèmes liés au partage de « &lt;project_id>/var/tmp »
   * _Remarque à propos de la correction_ : les fichiers temporaires Analytics DataExport utiliseront le répertoire tmp du système, qui est plus adapté aux accès fréquents et aux modifications. Pour éviter les collisions si plusieurs instances sont exécutées sur le même serveur, le chemin tmp a été mis à jour pour utiliser l’ID unique d’une instance
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/a4cf5e62>

### Analytics/Création de rapports, Cloud

* _ACP2E-3187_ : La mesure dans NR peut être trompeuse pour les transactions en arrière-plan - Suivi de ACP2E-3067
   * _Remarque de correction_ : les transactions en arrière-plan (cron) utiliseront le nom de l’application New Relic défini dans les paramètres de configuration
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/ec7e32a9>

### B2B

* _ACP2E-2139_ : les produits affectés au catalogue partagé ne sont pas reflétés sur le front-end lors de l’exécution de l’index partiel
   * _Remarque de correction_ : les produits affectés au catalogue partagé via l’API REST sont désormais immédiatement visibles sur storefront une fois l’indexation partielle terminée. Auparavant, les produits n’étaient visibles qu’après une réindexation complète.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/7377de59>
* _ACP2E-3247_ : sales_clean_quotes cron supprime les devis de vers commandes fournisseur encore approuvées
   * _Corriger la note_ : les devis utilisés dans les commandes fournisseur ne seront pas supprimés par le traitement cron sales_clean_quotes
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/581b7ef1>

### Bundle

* _AC-10826_ : le nombre de messages d&#39;erreur de validation de la case à cocher du lot Storefront est supérieur à 1
   * _Correction de la note_ : le système n’affiche désormais qu’un seul message d’erreur de validation lorsque l’utilisateur clique sur le bouton « Ajouter au panier » sans cocher d’option pour un produit groupé. Auparavant, le système affichait plusieurs messages d’erreur de validation pour chaque case à cocher désélectionnée.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/3ea26621>

### Panier et passer en caisse

* _AC-11914_ : [Problème] Règle de vente Calcul fixe panier : montant de remise incorrect
   * _Corriger la note_ : le système calcule désormais correctement le montant de la remise pour les règles de vente avec des montants fixes de panier, en veillant à ce que des remises précises soient appliquées quelles que soient les modifications apportées aux articles du panier. Auparavant, le montant de la remise pouvait varier de manière incorrecte lorsque les articles du panier étaient modifiés, ce qui entraînait parfois des remises considérablement plus importantes que prévu.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38694>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/581b7ef1>
* _AC-12479_ : la case Termes et conditions n’autorise pas HTML sur storefront
   * _Remarque à propos de la correction_ : le système prend désormais en charge le formatage d’HTML dans la case à cocher « Termes et conditions » du storefront, ce qui permet une personnalisation et une lisibilité améliorées. Auparavant, le texte de la case à cocher s’affichait au format texte brut, ignorant les balises HTML utilisées.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/6cfb9b6b>
* _AC-12541_ : la règle de prix de panier créée pour l’utilisateur connecté est incorrectement appliquée pour l’utilisateur non connecté
   * _Remarque à propos de la correction_ : le système supprime désormais correctement la règle de prix du panier pour les utilisateurs connectés lorsqu’ils sont automatiquement déconnectés en raison de l’expiration du cookie, en s’assurant que la remise n’est pas appliquée aux utilisateurs non connectés. Auparavant, la règle de prix du panier était toujours appliquée même lorsque l’utilisateur était déconnecté, ce qui entraînait l’application d’une remise incorrecte aux utilisateurs non connectés.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38944>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/7d5e3906>
* _AC-13302_ : [Problème] [FONCTIONNALITÉ] Optimisation des performances des grands paniers en empêchant...
   * _Remarque à propos de la correction_ : le système optimise désormais les performances des paniers volumineux en empêchant les appels getActions en double, ce qui améliore la vitesse et l’efficacité des opérations sur les paniers. Auparavant, pour un panier contenant plusieurs articles, la fonction getActions était appelée plusieurs fois, ce qui ralentissait les performances du système.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/39292>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/39290>
* _ACP2E-3176_ : [Cloud] commande rapide grande quantité de performances de SKU
   * _Remarque de correction_ : les performances de passage en caisse ont été améliorées lorsque les attributs utilisés dans les conditions des règles de prix de panier ne sont pas présents pour tous les produits et lorsque la fonctionnalité MAP (Prix minimum annoncé) est activée.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/66dea0de>
* _ACP2E-3211_ : objets dupliqués dans le panier
   * _Remarque de correction_ : le système traite désormais correctement plusieurs demandes parallèles pour ajouter le même produit au panier dans un seul élément de ligne, ce qui empêche la création d’éléments de ligne distincts pour le même SKU. Auparavant, la réalisation de requêtes parallèles pour ajouter le même produit au panier sur Storefront entraînait plusieurs éléments de ligne pour le même SKU.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/66dea0de>
* _ACP2E-3296_ : l’e-mail de confirmation de commande de passage en caisse est envoyé aux e-mails saisis en prénom/nom
   * _Correction de la note_ : l’e-mail de confirmation de commande de passage en caisse, précédemment envoyé lorsqu’un modèle de type e-mail était saisi dans les champs Prénom et Nom , n’est plus envoyé.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/5184c067>
* _ACP2E-3402_ : le formulaire d&#39;adresse d&#39;expédition de paiement est mis à jour avec une adresse incorrecte
   * _Remarque de correction_ : shippingAddressFromData est désormais enregistré dans le stockage local par site web. Auparavant, une adresse du mauvais site web pouvait être automatiquement renseignée dans le formulaire d’adresse d’expédition lors du passage en caisse si un code de magasin était utilisé dans l’URL et que le passage en caisse était initié à partir de plusieurs sites web au cours de la même session de personne invitée.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/078c387e>
* _ACP2E-3407_ : Produit De Carte Cadeau | Fusion de panier en cours de fusion de cartes-cadeaux
   * _Correction de la note_ : les produits de carte cadeau sont désormais correctement fusionnés dans le panier
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/88660e79>
* _ACP2E-3488_ : les données de devis existantes ne sont pas mises à jour/invisibles, mais créent un nouvel enregistrement de devis lorsque trigger_recollect = 1
   * _Remarque de correction_ : les articles du panier du client ne disparaissent plus suite à la suppression d’un produit après son ajout au panier.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/1984c61c>

### Catalogue

* _AC-11970_ : impossible de réorganiser les produits configurables avec une case à cocher sélectionnée pour l’option personnalisée
   * _Note de correction_ : le système traite désormais correctement la réorganisation des produits configurables avec une seule case à cocher sélectionnée option personnalisée, ce qui permet de créer un panier avec succès. Auparavant, toute tentative de réorganisation de ces produits entraînait une erreur et empêchait l’ajout d’articles dans le panier.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38736>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/1d144bce>
* _AC-13068_ : options de liste déroulante manquantes
   * _Remarque de correction_ : le système affiche désormais correctement toutes les valeurs dans la liste déroulante lors de la création d’un nouvel attribut avec plus de 20 valeurs. Auparavant, seules les 20 premières valeurs ou une autre valeur de page sélectionnée s’affichait, ce qui entraînait l’absence des valeurs restantes.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/47b448e2>
* _AC-13296_ : [Problème] Utilisez l’ID de magasin actuel pour le cache d’exécution de catégorie.
   * _Remarque de correction_ : le système utilise désormais correctement l’ID de magasin actuel pour le cache d’exécution de catégorie, ce qui empêche le remplacement des données lorsque l’émulation est utilisée ou que le code personnalisé enregistre la catégorie dans différents magasins. Auparavant, l’objet stocké dans l’exécution pouvait provenir d’un magasin incorrect, ce qui entraînait le remplacement des données.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/39310>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/36394>
* _AC-13324_ : bin/magento sampledata:deploy —no-update renvoie une exception
   * _Remarque de correction_ : le système accepte désormais correctement une valeur booléenne lors de l’utilisation de l’option —no-update dans la commande sampledata:deploy, ce qui empêche toute erreur lors du déploiement des données d’exemple. Auparavant, une erreur était générée lors de l’utilisation de cette commande, car le système s’attendait incorrectement à une valeur entière.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/39344>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/39345>
* _AC-13355_ : [Problème] Corrigez l’utilisation du type de cache EAV
   * _Remarque à propos de la correction_ : le système utilise désormais correctement le type de cache EAV à tous les emplacements pertinents, ce qui garantit une mise en cache des données cohérente et efficace. Auparavant, le type de cache EAV n’était pas utilisé de manière cohérente, ce qui entraînait des inefficacités et des incohérences potentielles dans la mise en cache des données.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/32322>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/31264>
* _AC-13596_ : la recherche avancée de catalogue avec des données vides accède à la page de résultats de recherche[branche 2.4.dev]
   * _Remarque de correction_ : le système conserve désormais correctement les utilisateurs sur la page Recherche avancée et affiche un message d’erreur lorsqu’ils tentent d’effectuer une recherche sans saisir de données. Auparavant, l’exécution d’une recherche vide redirigeait les utilisateurs vers la page de recherche avancée du catalogue avec un message les invitant à modifier leur recherche.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/6cfb9b6b>
* _ACP2E-3103_ : le flux RSS des nouveaux produits n&#39;est pas mis à jour avec les nouveaux produits en raison du cache
   * _Remarque de correction_ : le flux Rss pour les nouveaux produits est désormais mis à jour lorsqu’un produit est défini comme nouveau et enregistré
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/d01ee51e>
* _ACP2E-3198_ : [cloud] problème de zoom avec deux doigts et de déplacement sur l’appareil mobile réel
   * _Remarque sur les correctifs_ : le système assure désormais une fonctionnalité de zoom d’image cohérente sur les appareils mobiles, offrant ainsi une expérience utilisateur fluide et prévisible. Auparavant, la fonction de zoom sur l’image était incohérente et effectuait soudainement un zoom arrière après un certain point lorsqu’elle était affichée sur un appareil mobile.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/1366ae5e>
* _ACP2E-3282_ : lorsque nous annulons l&#39;affectation de produits du catalogue partagé, les produits de la liste de souhaits ne sont pas effacés
   * _Remarque de correction_ : désormais, aucun élément n’est visible dans la liste de souhaits si un produit n’est pas disponible dans le catalogue partagé. Auparavant, la page de liste de souhaits affichait incorrectement un nombre de « 1 élément » même si aucun élément n’était réellement disponible dans la liste de souhaits.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/5184c067>
* _ACP2E-3286_ : Produits associés Sélectionner tout/Désélectionner tout Événement
   * _Correction de la remarque_ : auparavant, les boutons « Tout sélectionner »/« Tout désélectionner » pour les produits associés ne fonctionnaient pas correctement si un produit était sélectionné manuellement. Après la correction, ces boutons fonctionnent désormais de manière cohérente, même après une sélection manuelle, garantissant que tous les produits sont correctement sélectionnés ou non sélectionnés.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/fd5cf3af>
* _ACP2E-3336_ : [Cloud] la traduction de l’e-mail d’alerte Stock est incorrecte
   * _Remarque sur la correction_ : lors de l’envoi d’alertes de stock/prix pour un site web comportant plusieurs vues de magasin utilisant différentes langues, la langue de la vue de magasin dans laquelle l’alerte a été créée est utilisée dans l’e-mail.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/a4cf5e62>, <https://github.com/magento/inventory/commit/9f3e63d1>
* _ACP2E-3350_ : les noms des catégories désactivées ne sont plus grisés dans l&#39;arborescence des catégories
   * _Remarque de correction_ : auparavant, les catégories désactivées n’étaient pas grisées dans l’arborescence des catégories. Désormais, elles s’affichent avec un effet de gris.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/d75cff27>
* _ACP2E-3410_ : le chargement configurable du formulaire de modification du produit entraîne un délai d’expiration et un épuisement de la mémoire
   * _Remarque sur la correction_ : avant la correction, les variations de produit configurables étaient créées en fonction de toutes les combinaisons d’options d’attribut possibles. Dans les cas où les attributs disposaient de nombreuses options, une opération longue et gourmande en ressources s’est produite. Désormais, les variations de produit configurables sont construites en fonction des attributs de produit enfant existants. Il en résulte beaucoup moins de calculs, ce qui améliore l’utilisation des ressources.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/078c387e>
* _ACP2E-3454_ : Fotorama ne charge pas correctement la vidéo lors de l’utilisation des nuanciers et l’option est présélectionnée via l’URL
   * _Remarque de correction_ : les vidéos de produit s’affichent désormais correctement sur la page des détails du produit configurable, si l’URL contient les options sélectionnées.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/078c387e>
* _ACP2E-3461_ : le widget de carrousel PageBuilder affiche les produits qui ne correspondent pas aux conditions
   * _Remarque sur la correction_ : la liste de produits utilisée dans les widgets respecte désormais la condition de catégorie
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/078c387e>
* _ACP2E-3469_ : une erreur de validation se déclenche pour tous les produits du groupe lorsque la quantité d&#39;un produit n&#39;est pas valide
   * _Correction de la note_ : désormais, l’erreur de validation est correctement déclenchée pour tous les produits du groupe lorsqu’un produit présente une quantité non valide, ce qui ne se produisait pas auparavant.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/56463d5e>
* _ACP2E-3516_ : les tables temporaires des indexeurs ne sont pas nettoyées si le processus est arrêté
   * _Remarque sur la correction_ : les tables temporaires de l’indexeur CatalogRule sont désormais nettoyées si le processus de l’indexeur est arrêté
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/1984c61c>
* _ACP2E-3520_ : [QUANS] échecs des tests unitaires principaux dans 2.4.7-p3
   * _Note de correction_ : les notes de mise à jour de ce test ne sont pas nécessaires, car il s’agit d’une amélioration du test unitaire.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/1984c61c>

### Catalogue, Contenu

* _ACP2E-3063_ : le cache [Cloud] n’est pas invalidé.
   * _Remarque de correction_ : auparavant, lors de l’enregistrement d’une page CMS avec une mise en page de conception mise à jour, la représentation n’était pas appropriée sur le front-end. Une fois ce correctif appliqué, la mise en page de conception appropriée est visible sur le front-end lorsque nous modifions la mise en page de conception et enregistrons la page CMS.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/66dea0de>
* _ACP2E-3131_ : [cloud] catégories ancre/non ancre inversées dans le widget de contenu
   * _Corriger la note_ : précédemment, lorsque nous avons sélectionné Afficher sur -> Catégories d&#39;ancrage, toutes les catégories qui ne reflétaient pas la relation parent-enfant entre l&#39;ancre et la non-ancre étaient affichées. Une fois ce correctif appliqué, l’option Afficher sur -> Catégories d’ancrage affiche uniquement les catégories d’ancrage (sélectionnables) et l’option Afficher sur -> Catégories non ancrées affiche les catégories non ancrées (sélectionnables)
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/7377de59>
* _ACP2E-3152_ : catégories ne fonctionnant pas avec les widgets
   * _Correction de la note_ : auparavant, si nous avions enregistré le bloc CMS pour différentes catégories d’ancrage/non-ancrage, il ne fonctionnait pas pour les catégories enfants lorsqu’il s’affichait sur le front-end. Une fois ce correctif appliqué, le bloc s’affiche en front-end pour différentes catégories.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/d01ee51e>

### Catalogue, GraphQL

* _ACP2E-3312_ : les prix de niveau renvoient une valeur incorrecte dans les produits GraphQL (par rapport à Storefront)
   * _Remarque sur la correction_ : après la correction, les prix de niveau du produit renvoyés pour les requêtes GraphQL ont un prix par article.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/1366ae5e>

### Catalogue, recherche

* _ACP2E-3345_ : erreur de type lors de la création de l&#39;objet : Magento\CatalogSearch\Model\Indexer\Fulltext\Interceptor Exception
   * _Remarque sur la correction_ : après la correction, une instance de la classe Magento\CatalogSearch\Model\Indexer\Fulltext peut être créée sans spécifier $data.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/1366ae5e>
* _ACP2E-3521_ : [CLOUD] le problème lié aux produits n’est pas visible dans le front-end après l’enregistrement dans Magento Admin
   * _Remarque sur la correction_ : après la correction, les produits configurables qui ont des produits enfants avec des noms longs ne seront pas manqués dans le storefront.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/1984c61c>

### Contenu

* _AC-12692_ : l’arborescence de catégorie du widget n’est pas rendue correctement
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/39008>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/58e40ceb>
* _AC-13054_ : impossible de voir le message « Utilisation de la valeur par défaut » lors de la modification du thème dans la page de configuration de la conception
   * _Correction de la note_ : le système inclut désormais une colonne distincte pour afficher le message « Utilisation de la valeur par défaut » en fonction du thème sélectionné dans la page de configuration de la conception. Cela garantit la clarté et la visibilité du statut de la valeur par défaut. Auparavant, le message « Utiliser la valeur par défaut » ne s’affichait pas, ce qui entraînait une confusion sur le statut du thème sélectionné.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/47b448e2>
* _AC-13569_ : [Problème] Restaure à nouveau la compatibilité descendante avec les plug-ins TinyMCE (après cela...
   * _Remarque de correction_ : le système restaure désormais la rétrocompatibilité avec les modules externes TinyMCE, ce qui permet d’appeler les fonctions définies dans le module externe lors de l’utilisation du widget à partir d’un autre emplacement. Auparavant, en raison d’une modification de la version de TinyMCE, les modules externes ne renvoyaient pas les widgets en tant qu’objet, ce qui entraînait une erreur lors de la tentative d’appel de certaines fonctions sur l’instance de widget.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/39262>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/39258>
* _ACP2E-3122_ : le bouton [CLOUD] Charger l’image ne fonctionne pas
   * _Remarque de correction_ : avant que le bouton Charger l’image pour la bannière et le curseur de PageBuilder ne fonctionne pas comme prévu, et maintenant, lorsque vous appuyez dessus, le gestionnaire de fichiers local s’ouvre pour sélectionner l’image à charger.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2-page-builder/commit/476ef8ea>
* _ACP2E-3275_: [Cloud] - Le curseur CMS ne reflète pas les dernières modifications
   * _Correction d’une remarque_ : le problème a été résolu en veillant à ce que la liste des curseurs soit actualisée tandis que l’événement d’enregistrement est déclenché sur l’écran de modification de la diapositive. Auparavant, cela se déclenchait et provoquait le problème.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2-page-builder/commit/ae2cdeb0>
* _ACP2E-3326_ : une erreur se produit dans la page CSM lorsque des blocs CMS sont insérés à l’aide du générateur de page dans un certain ordre
   * _Remarque sur la correction_ : Auparavant, sur certaines versions de PHP et OS (Linux), le rendu des blocs qui référençaient d’autres blocs cms via PageBuilder aurait échoué avec une erreur « Une erreur inconnue s’est produite. Veuillez réessayer. » Désormais, le contenu des blocs cms est correctement rendu dans un contenu contrôlé par PageBuilder.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2-page-builder/commit/ae2cdeb0>
* _ACP2E-3430_ : dernières mises à jour de sécurité avec la taille de police manquante de TinyMCE 7
   * _Correction d’une remarque_ : la taille de police et les sélecteurs de famille de polices sont désormais disponibles dans l’éditeur de WYSIWYG. Avant ce correctif, avec TinyMCE 7, ils n’étaient pas disponibles dans l’interface de l’éditeur.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/d50f6b5d>, <https://github.com/magento/magento2-page-builder/commit/2c2f7a0e>

### Client/Clients

* _AC-8499_ : le champ de texte Région n’est pas réinitialisé lorsque la liste déroulante Pays est modifiée
   * _Correction de la note_ : le système réinitialise désormais le champ de texte Région lorsque le pays est modifié dans le menu déroulant, en s’assurant que les valeurs précédentes ne persistent pas. Auparavant, la modification du pays de la liste déroulante ne réinitialisait pas le champ Région, ce qui entraînait la conservation de la dernière valeur enregistrée.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/3ea26621>
* _AC-9240_ : la suppression d’un client ne nettoie pas toutes les données de session du navigateur sur Storefront pour le client connecté et supprimé
   * _Remarque de correction_ : la suppression d’un client nettoie désormais toutes les données de session du navigateur du storefront pour les clients connectés et supprimés comme prévu. L’acheteur peut continuer à faire des achats et son navigateur traite sa session comme une session d’invité. Auparavant, lorsque le compte client d’un acheteur connecté était supprimé de l’administration, le navigateur de l’acheteur générait des erreurs JavaScript.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/7d5e3906>

### Framework

* _AC-10738_ : la configuration du vernis n’exclut pas tous les paramètres marketing
   * _Remarque de correction_ : le système exclut désormais correctement tous les paramètres marketing courants dans la configuration de Varnish, ce qui garantit un suivi et des analyses précis. Auparavant, certains paramètres marketing tels que gad_source, srsltid et msclkid n’étaient pas exclus, ce qui entraînait des inexactitudes potentielles dans la collecte des données.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38298>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/39188>
* _AC-11592_ : [Problème] Autoriser uniquement les préférences valides pendant la configuration:di:la compilation
   * _Remarque de correction_ : le système renvoie désormais une erreur lors de la commande setup:di:compile si une préférence est créée pour une classe qui n’existe pas ou qui est spécifiquement exclue, en s’assurant que seules des préférences valides sont autorisées. Auparavant, ces scénarios échouaient en silence, ce qui rendait inutiles les modules externes associés aux classes d’origine.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38517>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/33161>
* _AC-11809_ : [Problème] Transmettez les attributs personnalisés au lien actuel via XML
   * _Remarque de correction_ : le système permet désormais de transmettre des attributs personnalisés au lien actif via XML, en veillant à ce que ces attributs s’affichent correctement même lorsque le lien est la page active. Auparavant, les attributs personnalisés n’étaient pas affichés pour le lien de la page en cours, car la méthode getAttributesHtml() n’était pas utilisée pour le lien en cours.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38500>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/30070>
* _AC-12127_ : [Problème] éviter une boucle infinie de mauvaise configuration
   * _Remarque de correction_ : le système évite désormais une boucle infinie en empêchant le mappage autoréférentiel dans les configurations de type virtuel. Cela permet de s’assurer que l’application n’est pas bloquée dans une boucle sans fin lors de la tentative de déréférencement d’un nœud autoréférentiel. Auparavant, si une configuration de type virtuel était auto-référentielle, l’application tournait indéfiniment.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38822>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/38794>
* _AC-12299_ : gestionnaire d’objets non utilisé pour Magento\Csp\Model\Mode\Data\ModeConfigured
   * _Remarque de correction_ : le système utilise désormais correctement le Gestionnaire d’objets lors de la création de l’objet ModeConfigured, ce qui permet d’utiliser des modules externes sur cet objet. Auparavant, le Gestionnaire d&#39;objets n&#39;était pas utilisé, empêchant l&#39;application de modules externes à l&#39;objet ModeConfigured.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38875>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/38886>
* _AC-12540_ : commentaire de bloc de document inexact dans les alertes de stock de produits et de prix
   * _Corriger la note_ : le commentaire du bloc doc pour la méthode deleteCustomer dans les alertes de stock de produits et de prix a été corrigé afin de refléter précisément le fait que la méthode supprime du site web toutes les alertes de produit ou de prix de stock associées à un client et à un site web donnés, et non au client. Auparavant, le commentaire indiquait à tort que la méthode était destinée à supprimer un client du site web.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38939>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/39001>
* _AC-12857_ : PHP 8.2.15 a supprimé l&#39;extension FTP
   * _Remarque de correction_ : le système inclut désormais l’extension FTP en tant que dépendance dans le fichier composer.json, ce qui garantit la réussite de la configuration des importations de fichiers CSV par FTP. Auparavant, une erreur était générée lors de la tentative de configuration des imports de fichiers CSV via FTP en raison de l’absence de l’extension FTP dans le package PHP.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/39083>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/47b448e2>
* _AC-12964_ : possibilité de définir la zone pour la commande de ligne de commande dev:di:info
   * _Remarque sur la correction_ : le système permet désormais aux développeurs de définir une zone pour la commande dev:di:info CLI, ce qui améliore le processus de développement et de débogage. Auparavant, cette commande ne pouvait afficher que les informations relatives à la zone GLOBAL.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38758>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/38759>
* _AC-13279_ : [Problème] supprimez tous les paramètres marketing get pour réduire le cache
   * _Remarque à propos de la correction_ : le système supprime désormais tous les paramètres marketing get pour optimiser l’utilisation du cache, reflétant la logique utilisée lorsque le vernis est utilisé. Auparavant, ces paramètres pouvaient entraîner un gonflement du cache et une réduction des performances.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/39266>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/39099>
* _AC-13345_ : [Problème] [PHPDOC] Correction d’un phpdoc incorrect Magento\Directory\Model\AllowedCountries::getAllowedCountries()
   * _Remarque à propos de la correction_ : la PHPDoc pour la méthode AllowedCountries::getAllowedCountries() a été corrigée afin de fournir des informations précises, ce qui améliore la clarté et l’utilité de la documentation. Auparavant, la PHPDoc de cette méthode contenait des informations incorrectes, ce qui pouvait entraîner une confusion ou une mauvaise utilisation de la méthode.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/39246>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/39241>
* _AC-13348_ : [Problème] Supprime du code pour les versions PHP que nous ne prenons plus en charge.
   * _Correction de note_ : suppression du code des versions PHP qui ne sont plus prises en charge dans Magento
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/39361>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/39202>
* _AC-13417_ : [Problème] Rendre l&#39;adaptateur ImageMagick compatible avec php8 (Conversion implicite de float en int)
   * _Note de correction_ : Le système assure désormais la compatibilité avec PHP8 en gérant correctement les nombres flottants lors du calcul des dimensions de l&#39;image, évitant ainsi toute erreur due à une conversion implicite de float en int. Auparavant, le calcul des dimensions de l’image pouvait entraîner des nombres flottants qui, lorsqu’ils étaient implicitement arrondis, provoquaient une erreur.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/39402>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/37362>
* _AC-13537_ : [Problème] [PHPDOC] Corriger le mauvais phpdoc Magento\Framework\App\Config\ScopeConfigInterface
   * _Correction d’une note_ : cette mise à jour corrige les annotations PHPDoc dans le fichier Magento\Framework\App\Config\ScopeConfigInterface afin de refléter précisément le type de l’argument $scopeCode pour les méthodes getValue et isSetFlag.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/39492>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/39199>
* _AC-8662_ : [problème] améliorer la journalisation des erreurs cron
   * _Remarque de correction_ : le système capture et consigne désormais à la fois STDERR et STDOUT pour les processus cron, fournissant ainsi des informations de diagnostic précieuses dans les cas où les processus cron échouent. Auparavant, tous les messages d’erreur des processus cron n’étaient pas enregistrés et STDERR et STDOUT pour les groupes cron s’exécutant dans des processus distincts étaient perdus.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/37453>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/32690>
* _ACP2E-3230_ : la modification de la longueur des colonnes via db_schema.xml ne fonctionne pas en cas de clés étrangères
   * _Remarque de correction_ : la modification d’une colonne avec une clé étrangère via un schéma déclaratif ne génère désormais pas d’erreurs avec MariaDB
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/581b7ef1>
* _ACP2E-3361_ : certains enregistrements de relations sont enregistrés dans la base de données lorsque l&#39;enregistrement de commande est enregistré
   * _Remarque sur la correction_ : avant la correction, les requêtes UPDATE inutiles étaient déclenchées, ce qui peut avoir un impact sur les performances. Après le correctif, les requêtes UPDATE inutiles ont été éliminées.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/1366ae5e>
* _ACP2E-3375_: [CLOUD] L’administration rencontre de nombreuses erreurs JavaScript dans la console
   * _Remarque de correction_ : auparavant, dans le panneau d’administration, il y avait de nombreuses erreurs JavaScript dans la console. Désormais, dans le panneau d’administration, il n’y aura aucune erreur JavaScript dans la console et toutes les fonctions JavaScript par défaut s’exécuteront correctement sans problème.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/d75cff27>
* _ACP2E-3387_ : [Cloud] Magento : le message de file d’attente a été supprimé
   * _Remarque de correction_ : les messages de la file d’attente sont désormais correctement effacés. Avant la correction, étant donné que le système de file d’attente SQL était utilisé, les nouveaux messages pouvaient être supprimés si le message de la file d’attente de nettoyage était en cours d’exécution au même moment.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/d50f6b5d>

### Framework, framework d’interface utilisateur

* _ACP2E-3324_ : possibilité de remplacer la valeur de configuration même si elle est verrouillée
   * _Remarque sur la correction_ : auparavant, la configuration de conception ne pouvait pas être définie via la commande bin/magento config:set et les valeurs verrouillées pouvaient être modifiées en manipulant le formulaire qui les affichait. Après la correction, les valeurs verrouillées définies depuis l’interface en ligne de commande avec —lock-env ou —lock-conf ne peuvent plus être mises à jour.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/55615e61>

### GraphQL

* _ACP2E-2974_ : les traductions des attributs de retour client ne sont pas reflétées dans l’API GraphQL pour StoreView respectif
   * _Remarque de correction_ : les traductions des attributs de retour client sont reflétées dans l’API GraphQL pour l’affichage de magasin correspondant.
Auparavant, les attributs de retour client pour les StoreView respectifs n’étaient pas reflétés dans l’API GraphQL.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/ec7e32a9>
* _ACP2E-3215_ : [Cloud] problème d’authentification des utilisateurs et d’accès aux jetons intersites dans la configuration multisite
   * _Remarque à propos de la correction_ : les requêtes Informations du client et Panier GraphQl dans la configuration multisite vérifient si le client se trouve sur un site web autre que celui par défaut.
La requête précédente fonctionnait sans s’assurer que le client existe sur un site web autre que celui par défaut dans la configuration multisite.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/581b7ef1>
* _ACP2E-3255_ : la valeur du modèle [GRAPHQL] doit être spécifiée lors de l’obtention du panier client
   * _Remarque sur la correction_ : la requête « customerCart » de GraphQL peut désormais créer un panier vide même si le devis n’est pas disponible dans la base de données. Auparavant, cette opération échouait en raison de problèmes de validation du pays lors de la création du panier vide.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/fd5cf3af>
* _ACP2E-3380_ : les éléments de liste de souhaits [GraphQl] sont visibles via GraphQl, mais pas sur storefront
   * _Remarque sur la correction_ : les produits de liste de souhaits n’étaient pas correctement répertoriés lorsqu’ils étaient demandés via GraphQL. Désormais, les produits de la liste de souhaits sont filtrés en fonction du contexte de magasin fourni.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/55615e61>
* _ACP2E-3404_ : [GraphQL] Réinitialiser l&#39;incohérence de l&#39;e-mail de mot de passe entre le contenu et l&#39;objet/lien
   * _Remarque à propos de la correction_ : le problème a été résolu en simulant le magasin correct où le compte du client est enregistré lors de l’envoi de la demande de réinitialisation de mot de passe, quel que soit le magasin du site web.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/5184c067>
* _ACP2E-3419_ : la requête GraphQL de produits [Cloud] renvoie les produits associés non affectés au site web actuel
   * _Remarque sur la correction_ : auparavant, pour les requêtes GraphQL, les produits associés à plusieurs magasins ne s’affichaient pas correctement pour les requêtes de produit. Une fois ce correctif appliqué, pour les produits , graphQL interroge les produits associés à plusieurs magasins et les affiche en conséquence.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/078c387e>
* _ACP2E-3447_ : l’utilisation d’un ID de magasin incorrect dans l’en-tête GraphQL entraîne une erreur de mémoire fatale
   * _Remarque de correctif_ : l’envoi d’un code de magasin incorrect dans la requête GraphQL n’entraîne plus une consommation excessive de mémoire.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/d50f6b5d>
* _ACP2E-3467_ : réponse [Cloud] 500 à une réponse Graphql vide sur 2.4.7
   * _Remarque sur la correction_ : après la correction, les requêtes GraphQL non valides ne seront pas consignées dans le fichier exception.log.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/1984c61c>

### GraphQL, Recherche

* _ACP2E-948_ : requête GraphQL de liste de produits limitée à total_count 10 000 produits uniquement
   * _Note de correction_ : une fois la correction effectuée, le résultat de la recherche ne se limite pas à 10000 produits. Il devient alors possible d’obtenir tous les produits correspondant aux critères de recherche, même si le nombre est supérieur à 10000.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/a4cf5e62>

### GraphQL, framework de test

* _ACP2E-3363_ : échec du test de l&#39;intégration Magento\GraphQl\App\GraphQlCustomerMutationsTest.php
   * _Corriger la note_ : &#39;-
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/a4cf5e62>

### Importer/exporter

* _ACP2E-3172_ : bouton Importer manquant
   * _Correction de la remarque_ : résolvez le problème manquant du bouton Importer après la vérification des données avec des enregistrements corrects et incorrects dans le fichier CSV. Auparavant, le bouton d’importation ne s’affichait pas après la vérification des données avec des enregistrements corrects et incorrects dans le fichier CSV.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/1819fe73>
* _ACP2E-3382_ : impossible d&#39;importer l&#39;adresse du client exportée
   * _Correction de la remarque_ : l’importation de l’adresse du client se déroulera comme prévu. Auparavant, un fichier d’importation d’adresses client n’était pas validé si Partager les comptes client = Global et il existe deux sites web où le site web par défaut comporte une liste de pays restreinte et l’adresse importée correspond à un autre site web où les pays autorisés sont différents
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/ec7e32a9>
* _ACP2E-3448_ : [Cloud] Une quantité incorrecte dans le fichier CSV n&#39;a pas donné d&#39;erreur
   * _Corriger la note_ : Désormais, l&#39;importation des origines de stock générera une erreur de validation pour les valeurs non numériques dans la colonne de quantité. Auparavant, l&#39;importation d&#39;origines de stock avec une valeur non numérique dans la colonne Quantité entraînait la définition de la quantité sur 0.
   * _Contribution du code GitHub_ : <https://github.com/magento/inventory/commit/5b21b7af>
* _ACP2E-3475_ : l&#39;exportation du produit entraîne un OOM même avec une limite de mémoire 4G
   * _Remarque sur la correction_ : avant ce correctif, l’exportation du produit échouait si les attributs de produit avaient des milliers de valeurs d’option même avec la mémoire disponible 4G. Après ce correctif, l’exportation du produit doit terminer l’exportation du fichier CSV.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/1984c61c>

### Importation/exportation, Performances

* _ACP2E-3476_ : [Cloud] Le temps d’importation des produits a considérablement augmenté
   * _Remarque sur la correction_ : avant la correction, l’importation de produits de catalogue avec plus de 10 000 entrées présentait une dégradation temporelle significative. Après le correctif, l’importation des produits du catalogue s’exécute dans les délais impartis.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/87d012e5>

### Installer et administrer

* _AC-13242_ : la mise à niveau de Magento échoue sur MariaDB 11.4 + 2.4.8-beta1
   * _Remarque sur la correction_ : la mise à niveau doit s’être effectuée sans erreur.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/7b336d0a>

### Inventaire / MSI

* _ACP2E-3335_ : impossible d&#39;expédier la commande lorsque le magasin de prélèvement MSI est activé
   * _Remarque sur la correction_ : amélioration des performances d’inventaire de la création d’expédition pour de nombreuses sources avec retrait en magasin
   * _Contribution du code GitHub_ : <https://github.com/magento/inventory/commit/9f3e63d1>
* _ACP2E-3355_ : la réindexation Cron ne parvient pas à mettre à jour la disponibilité du produit sur le serveur frontal
   * _Remarque de correction_ : auparavant, les produits restaient en rupture de stock sur le serveur frontal après la mise à jour du statut de la commande en attente via l’API REST. Désormais, après la mise à jour du statut de la commande en attente via l’API REST, les produits s’affichent comme en stock.
   * _Contribution du code GitHub_ : <https://github.com/magento/inventory/commit/e6fe0aa7>
* _ACP2E-3357_ : échec de l&#39;ajout d&#39;images à configurable lorsque MSI est activé.
   * _Remarque sur la correction_ : le chargement des images pour les produits configurables fonctionne désormais comme prévu lorsque le module d’inventaire est utilisé. Auparavant, le chargement de l’image ne fonctionnait pas
   * _Contribution du code GitHub_ : <https://github.com/magento/inventory/commit/fdf409aa>

### Inventaire / MSI, Recherche

* _ACP2E-3413_ : tous les produits sont indexés avec [is_out_of_stock] = 1 lorsque le SKU n’est pas défini comme attribut consultable
   * _Remarque de correction_ : après la correction, le paramètre « is_out_of_stock » dans l’index de recherche catalogue est correct, même lorsque le SKU ne peut pas faire l’objet de recherches.
   * _Contribution du code GitHub_ : <https://github.com/magento/inventory/commit/5b21b7af>

### Ordre

* _ACP2E-3311_: [Cloud] Impossible de créer une commande dans l’administration sur un magasin si seule l’adresse de facturation par défaut n’a pas été configurée
   * _Correction de la note_ : désormais, le message d’erreur approprié « Un client ou une cliente avec la même adresse e-mail existe déjà dans un site web associé ». s’affiche si un client ne dispose pas d’une adresse de facturation par défaut et tente de créer une commande dans un autre magasin.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/d75cff27>
* _ACP2E-3416_ : l&#39;administrateur a dupliqué les demandes de commande envoyées
   * _Correction de la note_ : auparavant, il était possible de cliquer plusieurs fois sur le bouton « Envoyer la commande » du panneau d’administration ou de l’activer en appuyant de manière répétée sur la touche « Entrée », ce qui entraînait des envois en double ou des commandes avec une erreur. Vous pouvez désormais empêcher d’autres actions tant que la commande n’est pas entièrement traitée, en veillant à ce qu’une seule commande soit envoyée.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/5184c067>
* _ACP2E-3425_ : l&#39;administrateur peut toujours passer commande même sans mode de paiement
   * _Corriger note_ : Le mode de paiement précédemment sélectionné est désormais conservé lorsque le mode de paiement réapparaît dans la liste des paiements disponibles.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/d50f6b5d>

### Commande, Paiements

* _ACP2E-3233_ : l&#39;administrateur peut toujours passer commande même sans mode de paiement
   * _Corriger la note_ : Auparavant, le commerçant pouvait passer des commandes à partir du panneau d&#39;administration sans sélectionner de mode de paiement. Maintenant, le commerçant doit utiliser un mode de paiement pour passer une commande.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/fd5cf3af>

### Autres outils de développement

* _AC-12731_ : problèmes de CSP combinés avec dev/css/use_css_critical_path
   * _Remarque à propos de la correction_ : le système charge désormais correctement les fichiers CSS de manière asynchrone sur les pages de passage en caisse, même lorsque le paramètre « dev/css/use_css_critical_path » est activé, ce qui garantit que ces pages sont rendues avec les styles CSS appropriés. Auparavant, une politique de sécurité du contenu (CSP) restreinte empêchait l’exécution du JavaScript intégré, ce qui entraînait le chargement inattendu des fichiers CSS.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/39020>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/39040>
* _AC-13398_ : en utilisant le type virtuel pour configurer le plug-in, la méthode d&#39;intercepteur ne peut pas être générée correctement dans la commande setup:di:compile
   * _Remarque de correction_ : le système génère désormais correctement des méthodes d’intercepteur lors de l’utilisation d’un type virtuel pour configurer un plug-in, ce qui garantit des résultats cohérents, qu’ils soient précompilés ou compilés lors de l’exécution. Auparavant, le système générait des résultats incorrects lors de la précompilation par rapport à la compilation à l’exécution.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/33980>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/38141>

### Paiements

* _ACP2E-3143_ : le remboursement d&#39;une commande PayPal génère un avoir en double
   * _Correction de note_ : correction d&#39;un problème de simultanéité des avoirs créés par IPN pour le service de paiement PayPal.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/d01ee51e>
* _ACP2E-3163_ : la règle de prix du panier ne fonctionne pas pour Paypal
   * _Corriger la note_ : le montant correct s&#39;affiche du côté de PayPal lorsque la remise est appliquée par le mode de paiement
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/7377de59>
* _ACP2E-3208_ : [Cloud] les utilisateurs dotés d’un rôle spécifique ne peuvent pas se connecter
   * _Remarque sur la correction_ : l&#39;utilisateur administrateur dont le rôle contient uniquement un accès à la section PayPal peut désormais se connecter sans erreur
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/66dea0de>

### Performances

* _AC-11932_ : problème de paramètres d’attribut de produit par défaut
   * _Remarque sur la correction_ : le système permet désormais aux utilisateurs de désélectionner une option par défaut pour un attribut de produit, en s’assurant que l’attribut n’a pas toujours de valeur par défaut définie. Auparavant, une fois qu’une valeur par défaut était définie pour un attribut de produit, il n’était pas possible de la désélectionner, ce qui définissait toujours une valeur par défaut pour l’attribut.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38703>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/7d5e3906>
* _AC-13471_ : prise en charge de l’interface CommandLoaderInterface de Symfony dans l’interface de ligne de commande Magento
   * _Remarque de correction_ : cette modification réduit le temps d’initialisation de l’application de ligne de commande Magento en permettant l’initialisation différée des commandes jusqu’à ce qu’elles soient nécessaires.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/29266>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/29355>

### Produit

* _AC-13173_ : [Problème] Corriger la faute de frappe dans le bloc PHPDoc
   * _Remarque de correction_ : le système supprime désormais correctement une variable référencée inconnue dans PHPDoc pour la déclaration de variable $helper, ce qui améliore la clarté et la précision du code. Auparavant, cette variable référencée inconnue dans PHPDoc provoquait une confusion et des inexactitudes potentielles dans le code.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38961>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/38940>
* _AC-13423_ : [Problème] Correction d’un lot rompu et de la disposition des pages de produits téléchargeables dans Magento >= 2.4.7
   * _Remarque sur la correction_ : la mise en page du lot et des pages de produits téléchargeables a été corrigée, assurant ainsi un affichage cohérent et correct sur tous les appareils. Auparavant, ces pages rencontraient des problèmes de mise en page en raison d’une réorganisation du bloc de médias d’informations sur le produit.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/39403>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/6cfb9b6b>

### Promotion

* _ACP2E-3139_ : si la règle de vente comporte l&#39;attribut Etape de quantité de remise (Acheter X), les autres règles ne sont pas appliquées
   * _Corriger la note_ : la règle de prix du panier n’annule pas les règles précédemment appliquées si la quantité du produit dans le panier est insuffisante pour que la règle soit appliquée.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/d01ee51e>
* _ACP2E-3332_ : émettre des règles de vente avec une remise de montant fixe et une « remise de quantité maximale est appliquée à »
   * _Corriger la note_ : problème résolu avec la remise des règles du panier, lorsque la remise de montant fixe est configurée pour être appliquée à une quantité limitée de produits est le panier. Auparavant, la valeur « Remise Qté maximale appliquée à » était utilisée pour calculer le prix de l’article actuel dans le panier, et pas seulement pour calculer la remise de la règle.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/581b7ef1>
* _ACP2E-3349_ : règles de panier « Remise de montant fixe pour le panier entier »  L’action applique incorrectement les remises
   * _Correction de la note_ : les codes promotionnels seront correctement validés, indépendamment des majuscules ou des minuscules, lorsqu’ils sont utilisés lors de la création de la commande à partir de la zone d’administration. Auparavant, le code de coupon n’était pas validé s’il ne correspondait pas à la casse exacte de la lettre du code de règle de panier configuré.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/581b7ef1>
* _ACP2E-3374_ : dans le serveur principal, stockez les valeurs par défaut des attributs de produit (au lieu des valeurs d’administration attendues)
   * _Remarque à propos de la correction_ : désormais, dans le serveur principal, les valeurs d’administration sont utilisées au lieu des valeurs de magasin par défaut pour les attributs de produit.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/5184c067>
* _ACP2E-3377_ : l’action « Remise de montant fixe pour l’ensemble du panier » applique incorrectement les remises lors de l’ajout de produits groupés
   * _Remarque sur la correction_ : les règles de panier à montant fixe n’étaient pas correctement appliquées pour les produits groupés. Désormais, lors du calcul du montant de la remise totale, les produits enfants groupés sont pris en compte, ce qui permet d’obtenir un calcul de remise correct.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/1366ae5e>
* _ACP2E-3403_ : Les Règles De Prix Du Panier Calculent Mal La Remise
   * _Correction de note_ : les remises sur montant fixe sont désormais correctement calculées. Avant la correction, les remises sur montant fixe n’étaient pas correctement totalisées pour les produits groupés.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/0b488dd1>
* _ACP2E-3406_ : les catégories imbriquées dans les conditions de règle ne s’affichent pas
   * _Corriger la note_ : problème résolu lorsque les catégories imbriquées sous la catégorie de niveau 3 ne sont pas affichées dans les règles marketing pour la condition de catégorie
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/88660e79>
* _ACP2E-3432_ : usage_limit et uses_per_customer ne sont pas mis à jour dans la table salesrule_coupon.
   * _Remarque de correction_ : la mise à jour des Utilisations par coupon et des Utilisations par client dans la règle de prix du panier affecte désormais les coupons générés automatiquement existants. Auparavant, les nouvelles valeurs affectaient uniquement les nouveaux coupons
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/88660e79>
* _ACP2E-3456_ : la règle de prix du panier ne prend pas en compte la catégorie parent lorsqu’elle utilise la condition « égal à ou supérieur à ».
   * _Corriger la note_ : les règles de prix du panier considèrent désormais correctement la catégorie parent lorsqu’elle est utilisée dans des conditions avancées
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/93359343>
* _ACP2E-3463_ : calcul de remise non valide avec priorité
   * _Corriger la note_ : dans le cas d&#39;un montant fixe appliqué pour le type de remise Panier entier, le montant n&#39;était pas calculé correctement pour les articles du panier qui étaient déjà remis par une promotion précédente. Désormais, les remises sont correctement résumées.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/078c387e>
* _ACP2E-3498_ : valeur de remise incorrecte lorsque plusieurs règles de prix de panier sont appliquées simultanément à des produits à prix réduit/spéciaux
   * _Remarque sur la correction_ : avant la correction, le montant fixe pour l’ensemble des règles de panier n’était pas correctement appliqué si plusieurs règles étaient appliquées. Désormais, les règles de panier de remises à montant fixe sont correctement appliquées.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/1984c61c>

### Rechercher

* _AC-13053_ : obtention de « Saisissez un terme de recherche et réessayez ». erreur sur la page de recherche avancée dans storefront dans 2.4.8-beta1
   * _Remarque de correction_ : le système affiche désormais correctement les résultats de la recherche sur la page Recherche avancée lorsqu’un attribut de produit est défini sur « Non ». Auparavant, la définition d’un attribut de produit sur « Non » et l’exécution d’une recherche entraînait un message d’erreur « Saisissez un terme de recherche et réessayez ».
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/3ea26621>
* _AC-13721_ : magento/module-open-search dépend d&#39;une branche opensearch-php inexistante
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/05dc0bbf>
* _ACP2E-3362_ : la table search_query, lorsqu’elle est de taille importante, a un impact important sur le temps de chargement frontal
   * _Remarque sur la correction_ : amélioration du temps de chargement de la page de liste de recherche. Avant la correction, la page de liste de recherche était retardée en raison d’une requête non optimisée.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/55615e61>

### Sécurité

* _ACP2E-3273_ : ReCaptcha V2 s’affiche incorrectement lors du passage en caisse en allemand
   * _Correction de la note_ : auparavant, le recaptcha de sous l’adresse e-mail de l’extraction semblait sans style pour les langues comportant des mots longs, comme l’allemand. Ensuite, le recaptcha sera identique à tous les éléments recaptcha du reste des zones.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/7377de59>

### Expédition

* _ACP2E-3340_ : l’API de suivi FedEx ne fonctionne pas avec les informations d’identification REST
   * _Remarque sur la correction_ : auparavant, l’intégration de FedEx ne nécessitait pas de clés API supplémentaires pour l’API de suivi. Une nouvelle configuration a été ajoutée pour prendre en charge les clés d’API de suivi.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/ec7e32a9>
* _ACP2E-3354_ : [Cloud] FedEx n&#39;a pas renvoyé les taux négociés sur REST
   * _Note de correction_ : avant la correction, les taux spécifiques au compte FedEx n&#39;étaient pas envoyés sur la réponse, même si selon la documentation de FedEx, ils auraient dû être envoyés. Après la correction, les taux spécifiques au compte sont envoyés sur la réponse en modifiant la requête de notre côté.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/55615e61>

### Évaluation et prévisualisation

* _ACP2E-3453_ : impossible de mettre à jour la mise à jour planifiée lors de l&#39;utilisation d&#39;un attribut de catégorie personnalisée unique
   * _Correction d’une note_ : correction d’un problème en raison duquel la mise à jour d’une mise à jour planifiée pour une catégorie n’était pas possible si la catégorie avait un attribut unique
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/078c387e>

### Taxe

* _ACP2E-3193_ : la taxe sur les produits fixes (FPT) ne fonctionne pas avec les produits configurables
   * _Remarque sur la correction_ : FPT pour que les variations de produit configurables fonctionnent correctement.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/ec7e32a9>

### Framework de test

* _AC-13362_ : [Problème] Orthographe de correction PHPDoc
   * _Remarque sur la correction_ : le système reconnaît désormais correctement les méthodes obsolètes dans les IDE en raison d’une correction orthographique dans le PHPDoc. Auparavant, une erreur d’orthographe dans le PHPDoc empêchait les IDE de reconnaître certaines méthodes comme obsolètes.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/31399>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/31398>
* _AC-13478_ : MAGETWO-95118 : vérification du comportement avec le panier persistant après l’expiration de la session
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/7d5e3906>
* _ACP2E-3458_ : [MFTF] StorefrontCheckoutProcessForQuoteWithoutNegotiatedPriceTest
   * _Remarque sur la correction_ : Mftfs fixes
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/078c387e>

### Framework de l’interface utilisateur

* _AC-12432_ : Champ De Fichier De Composant D’Interface Utilisateur
   * _Remarque sur la correction_ : le système valide désormais correctement le champ de fichier dans un formulaire de composant de l’interface utilisateur, ce qui permet d’envoyer le formulaire sans erreur lorsqu’un fichier est sélectionné. Auparavant, la validation échouait même lorsqu’un fichier était sélectionné, ce qui empêchait l’envoi du formulaire.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38908>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/39004>
* _AC-12645_ : [Problème] Format de date amélioré dans la console js : passez de 12 heures à 24 heures pour...
   * _Remarque sur la correction_ : format de date amélioré dans la console js : passez de 12 heures à 24 heures.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38983>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/38972>
* _AC-12650_ : [Problème] ajoutez la génération sourceMap pour moins de fichiers en mode développeur
   * _Remarque de correction_ : le système génère désormais des mappages source pour moins de fichiers en mode Développeur, ce qui facilite l’identification de la source d’un style. Auparavant, l’identification de la source d’un style était difficile lors de l’exécution du système en mode développeur avec une compilation côté serveur moins .
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/38982>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/38977>
* _AC-13459_ : comportement incohérent dans le tri « en rupture de stock » avec le seuil minimum de stock
   * _Correction de la note_ : le système trie désormais correctement les produits du catalogue en fonction des niveaux de stock, en respectant le seuil minimal de stock défini et en déplaçant régulièrement les articles en rupture de stock au bas de la liste. Auparavant, le comportement du tri était incohérent, les articles n’apparaissant pas toujours dans le bon ordre en fonction de leur niveau de stock, et les modifications du tri pouvaient se produire de manière imprévisible après l’enregistrement, l’actualisation ou la modification de la hiérarchie des catégories.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/47b448e2>
* _AC-13472_ : suggestion pour améliorer les rapports d’erreur en cas de problèmes de chargement de required.js.
   * _Remarque de correction_ : cette requête de résolution améliore le message d’erreur lorsque requirejs ne parvient pas à charger un composant.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/36761>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/38971>
* _AC-9168_ : [Problème] Supprimer les scripts inutiles
   * _Remarque à propos de la correction_ : le système optimise désormais le temps de chargement des pages en supprimant les scripts JavaScript inutiles de la section d’évaluation, au lieu d’utiliser des styles CSS intégrés pour un code plus efficace et plus lisible. Auparavant, l’utilisation de scripts JavaScript pour la section d’évaluation pouvait potentiellement ralentir le temps de chargement des pages.
   * _Problème GitHub_ : <https://github.com/magento/magento2/issues/37776>
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/pull/34643>
* _ACP2E-3367_ : En-Tête Du Site | Caractères spéciaux Rompant la section Bienvenue du client
   * _Remarque sur la correction_ : une fois la correction effectuée, les caractères spéciaux s’affichent correctement dans la section d’accueil du client.
   * _Contribution du code GitHub_ : <https://github.com/magento/magento2/commit/1366ae5e>
