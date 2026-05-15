---
source-git-commit: b829cf3685457f9f9ad3dfca2d294b6167accb82
workflow-type: tm+mt
source-wordcount: '3479'
ht-degree: 0%

---
# Points forts d’Adobe Commerce (v2.4.9)

## Points forts de la version v2.4.9

Les points forts suivants s’appliquent à la version 2.4.9 d’Adobe Commerce.

### Modifications de l’API REST

#### Contrôle de l’héritage de la galerie de produits de l’API REST au niveau de la vue magasin

La mise à jour d’un produit via l’API REST dans une portée de magasin n’entraîne plus l’héritage des modifications des images et vidéos du produit à partir de la portée globale lorsque la `media_gallery_entries` est omise de la payload ou définie sur `NULL`. Il est désormais également possible de restaurer l’héritage de la portée pour les images et vidéos de produit via l’API REST en définissant le champ correspondant sur `NULL`.

Lors de la mise à jour de produits via l’API REST au niveau de la vue du magasin :

- L’omission de `media_gallery_entries` ou sa définition sur NULL préserve désormais l’héritage de la galerie par défaut/globale.
- Pour restaurer l’héritage pour des attributs de galerie spécifiques (tels que `label`, `position`, `disabled`, `video_title`, `video_description`), définissez ces champs sur NULL dans le tableau `media_gallery_entries`.

Cette modification permet de s’assurer que les vues du magasin peuvent facilement conserver ou restaurer les valeurs par défaut de la galerie, ce qui réduit la confusion et rend la gestion de la galerie plus cohérente.

_ACP2E-4358 - [contribution du code GitHub](https://github.com/magento/magento2/commit/f7bbcb4e)_

### Modifications de l’API GraphQL

#### `clearCart` mutation GraphQL est désormais disponible dans Magento Open Source

La mutation [clearCart](https://developer.adobe.com/commerce/webapi/graphql/schema/cart/mutations/clear-cart/) GraphQL est désormais disponible pour tous les utilisateurs de Magento Open Source. Auparavant, cette mutation n’était accessible que dans Adobe Commerce.

_AC-16683 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/4449d914)_

#### Erreurs plus descriptives de la mutation `applyGiftCardToCart` GraphQL

Amélioration de la gestion des erreurs pour la mutation `applyGiftCardToCart`. La mutation renvoie désormais des messages d’erreur spécifiques pour des cas tels que les cartes-cadeaux expirées ou à solde nul, ce qui améliore l’expérience de l’acheteur. En outre, le serveur principal empêche l’application de cartes-cadeaux supplémentaires aux commandes déjà gratuites.

_LYNX-787_

#### La nouvelle mutation `clearWishlist` GraphQL supprime tous les éléments de la liste de souhaits à la fois

Ajout d’une mutation `clearWishlist` qui supprime tous les éléments d’une liste de souhaits dans un seul appel.

_LYNX-790_

#### Nouvelle mutation `exchangeExternalCustomerToken` GraphQL pour l’authentification basée sur l’intégration

Ajout d’une nouvelle mutation `exchangeExternalCustomerToken` GraphQL qui authentifie les utilisateurs via un jeton d’intégration et renvoie le jeton client et les données client associées.

_LYNX-815_


#### Les nouvelles requêtes GraphQL renvoient les ID de groupe de clients, de segments et de règles de panier appliqués

Les nouvelles requêtes GraphQL renvoient le `uid` codé du groupe de clients et clientes appliqué, des segments de clients et clientes et des règles de panier.

_LYNX-867_

#### Les options de cadeau sont effacées automatiquement lorsque le panier est vidé

Correction d’un problème en raison duquel les options de cadeau persistaient sur un panier vide après la suppression de tous les articles. Les options de cadeau sont désormais effacées automatiquement lorsque le panier est vidé, ce qui correspond au comportement existant pour les coupons.

_LYNX-786_

#### Les options de cadeau fusionnent de manière cohérente lorsque les paniers clients et invités sont combinés

Amélioration de la gestion des options de cadeau lors des fusions de panier pour garantir une expérience utilisateur plus cohérente. Les options de cadeau suivent désormais une logique de fusion hiérarchisée, ce qui empêche les remplacements inattendus lorsqu’un utilisateur invité se connecte et que son panier est fusionné avec un panier client existant.

_LYNX-788_

#### Nouveau champ de `grand_total_excl_tax` dans la réponse de `OrderTotal` GraphQL

Un nouveau champ, `OrderTotal.grand_total_excl_tax`, a été ajouté à la réponse de commande GraphQL. Ce champ fournit le total général hors taxe de la commande, ce qui facilite l’accès aux totaux hors taxe directement à partir de l’API.

Avantages :

- Récupérez facilement le total général hors taxe pour n’importe quelle commande via GraphQL.
- Simplifie l&#39;intégration avec les systèmes externes qui nécessitent des totaux hors taxes.
- Réduit la nécessité de calculs personnalisés côté client.

_LYNX-892_

#### Les commandes historiques affichent les détails des produits qui sont désormais en rupture de stock.

Les commandes historiques affichent désormais tous les détails des produits pour les lignes même après rupture de stock du produit, de sorte que les clients et les commerçants conservent un enregistrement complet de ce qui a été acheté.

_LYNX-913_

#### Validation reCAPTCHA ajoutée aux mutations `updateCustomer`, `updateCustomerV2` et `contactUs` de GraphQL

Lorsque reCAPTCHA est activé pour les formulaires de storefront correspondants, les mutations de GraphQL `updateCustomer`, `updateCustomerV2` et `contactUs` appliquent désormais la même validation, ce qui permet d’éviter les abus automatisés via l’API.

_LYNX-941_

#### Validation reCAPTCHA ajoutée à la mutation `applyCouponsToCart` GraphQL

Lorsque reCAPTCHA est activé pour le formulaire de coupon, la mutation `applyCouponsToCart` de GraphQL applique désormais la même validation, ce qui permet d’empêcher l’énumération du code de coupon via l’API.

_LYNX-942_

#### Champ `customer_id` de l’API B2B GraphQL restauré et entièrement pris en charge

Le champ `customer_id` de l’API GraphQL B2B est restauré et renvoie désormais la valeur correcte dans les requêtes et mutations de gestion de société. Auparavant, le champ était obsolète et renvoyait `null`, ce qui limitait son utilité pour les intégrations B2B.

_LYNX-955_

### Interface utilisateur d’administration

#### Menu Actions de la grille des règles de prix du catalogue

La grille **Règles de prix du catalogue** dans l’administration Commerce comprend désormais un menu **Actions** qui permet aux commerçants d’activer, de désactiver ou de supprimer plusieurs règles à la fois. La gestion des règles de prix de catalogue s’aligne ainsi sur les actions en masse existantes disponibles pour les **règles de prix de panier**, ce qui réduit considérablement le temps nécessaire à la gestion des jeux de règles volumineux.

_AC-13916_

#### Aperçu de l’affichage mobile pour l’évaluation du contenu

La fonctionnalité d’aperçu intermédiaire d’Admin effectue désormais un rendu précis des aperçus d’appareil mobile simulés par un navigateur, de sorte que les commerçants puissent voir comment une mise à jour intermédiaire apparaîtra sur un appareil mobile avant qu’elle ne soit activée.

_ACP2E-3397 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/520f9e30)_

#### La nouvelle configuration d’administration contrôle le comportement de fusion du panier client et invité lors de la connexion

Les commerçants peuvent désormais choisir la manière dont les articles du panier sont fusionnés lorsqu’un invité se connecte et dispose déjà d’un panier client :

- **Priorité des invités** — Utilisez la quantité de panier d&#39;invités.
- **Priorité client** — Utilisez la quantité du panier client.
- **Fusionner les quantités** (par défaut) : additionnez les deux quantités.

Configurez ce comportement dans **Magasins** > **Configuration** > **Ventes** > **Passage en caisse**, sous **Préférence de fusion de panier**. Le paramètre s’applique à tous les types de produits, ce qui permet aux commerçants de contrôler entièrement la manière dont les paniers d’invités et de clients sont combinés lors de la connexion.

_LYNX-889_

### Braintree

#### Passage en caisse express

- **Offres promotionnelles sur la feuille de paie Google Pay express**

  La feuille de paie Google Pay express prend désormais en charge les codes promotion et offre. Les acheteurs peuvent appliquer, afficher et supprimer des promotions de panier Commerce directement dans la feuille de paie Google, de sorte que les clients de passage en caisse express reçoivent les mêmes remises et incentives que les flux de paiement standard.

  _LOT-3476_

- **Offres promotionnelles sur la feuille de paie Apple Pay express**

  La feuille de paie Apple Pay express prend désormais en charge les codes promotion et offre. Les acheteurs peuvent appliquer un coupon directement dans la feuille de paie Apple afin que les utilisateurs de passage en caisse express bénéficient des mêmes remises et campagnes que les flux de passage en caisse standard.

  _LOT-3477_

- **Apple Pay sur Chrome et Firefox**

  Apple Pay peut désormais être utilisé sur Chrome et Firefox, pas seulement sur Safari. Lorsqu’Apple Pay Express est activé, les boutons Apple Pay sont disponibles sur les pages PDP, mini-panier, panier et passage en caisse. Les clients effectuent leur paiement en scannant un code avec leur iPhone.

  _LOT-3478_

- **Rappel d&#39;expédition côté serveur pour PayPal Express**

  Le rappel d&#39;expédition PayPal Express a été déplacé du côté client vers le côté serveur. Cela fournit des méthodes d’expédition dynamiques, des calculs de coûts en temps réel et des détails précis au niveau du panier directement dans la fenêtre modale PayPal, améliorant la fiabilité et jetant les bases de fonctionnalités futures telles que la prise en charge du module de contact, les flux de commutation d’applications et Venmo Express.

  _LOT-3479_

- **Module de contact PayPal pour paiement express des commerçants américains**

  Un nouveau module de contact PayPal est introduit pour les commerçants américains. Lorsque cette option est activée, les acheteurs qui utilisent PayPal Express peuvent afficher et mettre à jour l&#39;adresse e-mail et le numéro de téléphone partagés avec le marchand directement dans la fenêtre modale PayPal lors des flux express (PDP, mini-panier, panier, passage en caisse express). Les coordonnées sélectionnées sont alors stockées dans la commande Commerce.

  _LOT-3480_

#### Modes de paiement

- **Prise en charge du type de carte ELO pour les paiements Braintree**

  Ajout de la prise en charge du type de carte ELO dans Braintree Payments. Les administrateurs peuvent activer ELO dans la configuration de la carte de crédit et les clients peuvent payer avec des cartes ELO au moment du passage en caisse.

  _LOT-3464_

- **Méthode de paiement locale BLIK pour les acheteurs polonais**

  Ajout de BLIK comme nouveau mode de paiement local pour les acheteurs polonais. Cela permet des paiements BLIK sécurisés, basés sur les banques, dans le flux des méthodes de paiement locales (LPM) de Braintree, améliorant ainsi la commodité de passage en caisse et la conversion pour les clients en Pologne.

  _LOT-3481_

- **Paiement sur facture — nouveau mode de paiement BNPL pour l&#39;Allemagne**

  Ajout de [!DNL Pay Upon Invoice] comme nouveau mode de paiement local pour les acheteurs allemands. [!DNL Pay Upon Invoice] est une option d&#39;achat immédiat, de paiement différé (BNPL) optimisée par PayPal et Ratepay (« Rechnungskauf mit Ratepay ») qui permet aux clients de recevoir les marchandises en premier et de payer la facture dans les 30 jours sans avoir besoin d&#39;un compte PayPal. Comme il ne s&#39;agit pas d&#39;un paiement instantané, la finalisation des commandes est pilotée par un webhook côté serveur de PayPal.

  _LOT-3475_

#### Coffre de cartes

- **Vault Google Pay via la zone de compte**

  Les clients peuvent désormais archiver leurs cartes Google Pay dans la zone de compte lorsque Google Pay Vault est activé dans Braintree. Les cartes voûtées apparaissent sous les modes de paiement stockés, peuvent être utilisées pour les achats futurs au moment du passage en caisse et peuvent être supprimées par le client. Cela étend la prise en charge des coffres-forts au-delà des cartes et de PayPal à Google Pay.

  _LOT-3459_

- **Dispositif de mise à jour de compte en temps réel (RTAU) pour cartes Braintree voûtées**

  La fonction Real-Time Account Updater (RTAU) ajoutée à Braintree permet de mettre à jour automatiquement les informations des cartes Visa, Mastercard et Discover lorsque les cartes expirent ou sont remplacées. Cela réduit les paiements en échec, maintient le coffre Commerce Vault à jour et ignore les types non pris en charge (prépayé, Apple Pay, Google Pay) sans erreur.

  _LOT-3462_

#### Outils d’administration

- **Lier la commande Commerce au portail Braintree**

  Un lien Portail Braintree est maintenant ajouté aux détails de la commande dans l’Administration de Commerce. Cliquez sur le lien pour ouvrir la transaction associée sur le portail Braintree (dans un nouvel onglet), à l’aide des identifiants de commerçant et de transaction de la commande Commerce. Cela permet des références croisées directes sans se connecter séparément aux deux systèmes.

  _LOT-3461_

#### Sécurité et compatibilité

- **Mise à jour de la politique de sécurité du contenu de l’intégration Cardinal pour 3-D Secure**

  La politique de sécurité du contenu (CSP) a été mise à jour pour prendre en charge les dernières exigences d’intégration de Cardinal (3-D Secure). Cela permet de s’assurer que tous les scripts, iframes et ressources associées hébergés par Cardinal utilisés pendant les flux 3-D Secure sont autorisés par le CSP du navigateur, ce qui empêche les requêtes bloquées et les expériences de vérification ou de défi rompues.

  _LOT-3485_

- **Compatibilité de l&#39;extension de paiement Braintree PHP 8.5**

  L&#39;extension de paiement Braintree a été mise à jour pour prendre en charge le runtime PHP 8.5, tout en maintenant la compatibilité avec PHP 8.4.

  _LOT-3493_

### Plateforme et infrastructure

#### Chargement plus rapide des pages sur des magasins à thèmes multiples et à paramètres régionaux multiples après refactorisation du stockage de hachage SRI

Le stockage de hachage SRI génère désormais des fichiers distincts par zone, thème et paramètre régional, au lieu d’un seul fichier `sri-hashes.json` volumineux. Cette modification garantit que seul le fichier de hachage approprié est chargé pour chaque page, ce qui améliore les temps de chargement des pages et réduit l’utilisation de la mémoire sur les magasins avec plusieurs thèmes ou paramètres régionaux.

_AC-16113 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/bc83cd2c)_

#### Ajouter la compatibilité avec PHPUnit 12

La dépendance du compositeur Adobe Commerce est mise à niveau vers la version `phpunit/phpunit` 12.x. Tous les tests sont mis à jour pour la compatibilité, améliorant la sécurité et l&#39;alignement avec les dernières fonctionnalités PHPUnit. Cette mise à niveau permet à Adobe Commerce de rester prêt pour les prochaines versions de PHP et PHPUnit.

_AC-14808_

#### Ajouter la compatibilité avec RabbitMQ 4.2

RabbitMQ 4.2 est désormais un courtier de messages pris en charge. Cette mise à jour est un chemin de compatibilité à court terme qui permet aux commerçants qui dépendent du protocole AMQP de continuer à utiliser RabbitMQ avant la fin de la prise en charge de RabbitMQ 4.1 en février 2026, sans migration immédiate vers STOMP. Pour les déploiements à long terme, utilisez Apache ActiveMQ Artemis comme remplacement à long terme de RabbitMQ.

_AC-16117_

#### Apache ActiveMQ Artemis remplace à long terme RabbitMQ

Apache ActiveMQ Artemis est le courtier de messages à long terme recommandé pour Adobe Commerce. Il est géré par les risques de fin de prise en charge associés à RabbitMQ 4.1. ActiveMQ Artemis est entièrement pris en charge sur les lignes de version 2.4.6 à 2.4.9 de Commerce. Sur Adobe Commerce Cloud, il est fourni en tant qu’AWS ActiveMQ pour les déploiements natifs dans le cloud. Les consommateurs et les éditeurs de file d’attente peuvent être configurés pour utiliser STOMP.


Les installations existantes de RabbitMQ 4 restent compatibles pour les commerçants qui préfèrent continuer à utiliser leur service de file d&#39;attente de messages actuel à court terme — voir [Ajouter la compatibilité avec RabbitMQ 4.2](#add-compatibility-with-rabbitmq-42) ci-dessus. Planifiez une migration vers ActiveMQ Artemis pour une prise en charge à long terme.

_AC-14558_

#### Ajouter la prise en charge de Valkey 9.x

Adobe Commerce 2.4.9 étend la prise en charge de Valkey en tant que serveur principal de cache compatible Redis :

- **Valkey 9.x** — Prise en charge complète introduite dans Adobe Commerce 2.4.9, y compris la parité complète des commandes de l’interface de ligne de commande avec Redis et les options de configuration d’administration et de cloud mises à jour pour une configuration transparente. Ce travail est motivé par les changements de fin de prise en charge et de licence de Redis 7.2, offrant aux commerçants une alternative fiable et entièrement prise en charge à Redis.

_AC-14103, AC-14604, AC-16122_

#### Ajouter la prise en charge d’OpenSearch 3.x

Adobe Commerce 2.4.9 est entièrement compatible avec OpenSearch 3.x. La dernière version mineure est désormais le moteur de recherche recommandé. Les commerçants bénéficient d’une amélioration des performances, de la sécurité et d’une prise en charge à long terme, tout en conservant une rétrocompatibilité avec OpenSearch 2.x.

_AC-11846, AC-16403_

#### Ajouter la prise en charge de MariaDB 11.8 et 12.x

MariaDB 11.8 et 12.x sont désormais des versions de base de données prises en charge, ce qui permet aux commerçants d’adopter les dernières versions pour améliorer les performances SQL et la stabilité à long terme de la plateforme.

_AC-16533_

### PHP et compositeur

#### Compatibilité PHP 8.5

Adobe Commerce 2.4.9 prend désormais en charge PHP 8.5 et PHP 8.4, ce qui vous permet d’exécuter votre boutique sur les dernières versions PHP sécurisées et conformes. Toutes les fonctions principales, les extensions groupées (y compris Page Builder, B2B, Braintree, etc.) et les services SaaS Adobe sont compatibles avec PHP 8.5.

- PHP 8.5 et 8.4 sont entièrement pris en charge.
- PHP 8.3 est autorisé pour la mise à niveau uniquement (non recommandé pour la production).
- Garantit la conformité PCI et la pérennisation de votre installation Adobe Commerce.

_AC-15615_

#### Prise en charge de PHP 8.2 supprimée

Depuis Adobe Commerce 2.4.9, PHP 8.2 n&#39;est plus pris en charge. La plateforme cible désormais PHP 8.3 et versions ultérieures, avec le code de base, les dépendances et les outils mis à jour pour fonctionner de manière propre et fiable sur PHP 8.4 et 8.5.

_AC-15758_

#### Compatibilité du compositeur 2.9 vérifiée

Adobe Commerce 2.4.9 est entièrement compatible avec Composer 2.x, y compris Composer 2.9. La rétrocompatibilité avec les versions antérieures de Composer 2.x est préservée, ce qui garantit une expérience de création et de déploiement stable pour les commerçants et les développeurs qui utilisent les dernières versions de Composer.

_AC-14481_

### Framework

#### Mise à jour de sécurité et de compatibilité du framework JWT

Dans le cadre de la révision continue de la sécurité de la plateforme, la dépendance du framework JWT des jetons web a été évaluée et mise à jour vers la dernière version majeure, afin d’assurer la compatibilité future et des normes de sécurité solides pour l’authentification par jeton dans les intégrations de Commerce. Les fonctionnalités existantes sont entièrement préservées.

_AC-13209 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/2bac8114) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/09b36ebb) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/33b81f28)_

#### Mise à jour de la structure de tests fonctionnels d’Adobe Commerce vers les dépendances LTS de Symfony

Le framework de tests fonctionnels (MFTF) Adobe Commerce a été mis à jour afin d’utiliser les dernières dépendances Symfony LTS, y compris symfony/config, comme l’exige la mise à niveau du jeton web/jwt-framework. Cela résout les conflits de dépendance antérieurs et garantit une pile stable et prise en charge pour les tests fonctionnels.

_AC-13244_

#### Les fonctions natives PHP OAuth remplacent les bibliothèques tierces

La bibliothèque `carlos-mg89/oauth` tierce a été remplacée par des fonctions PHP OAuth natives, ce qui améliore la sécurité, réduit les dépendances externes et améliore la stabilité de la plateforme.

_AC-14075 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/7b8064f7)_

#### Le composant Symfony Cache remplace Zend_Cache.

À compter d’Adobe Commerce version 2.4.9, le composant obsolète Zend_Cache a été remplacé par le composant Cache Symfony. Cette mise à jour améliore les performances et la maintenabilité du cache et assure la compatibilité à long terme avec PHP 8.x et les futures mises à jour de la plateforme. Les serveurs principaux de cache existants et les commandes de gestion du cache restent entièrement pris en charge, sans modifications requises pour les intégrations actuelles.

_AC-15823_

#### Migration de l’éditeur de WYSIWYG de TinyMCE vers HugeRTE

En raison de la fin de la prise en charge de TinyMCE 5 et 6 et des incompatibilités de licence avec TinyMCE 7, l’éditeur WYSIWYG d’Adobe Commerce a été migré vers l’éditeur open source [HugeRTE](https://hugerte.org/). Cette migration garantit qu’Adobe Commerce reste conforme aux licences open source, évite les vulnérabilités connues de TinyMCE 6 et offre une expérience de modification moderne et prise en charge pour les commerçants et les développeurs.

_AC-14568_

#### L’implémentation native de MVC remplace Laminas MVC.

Adobe Commerce a introduit une implémentation native de MVC, qui remplace l’ancien MVC Laminas, afin d’assurer la compatibilité et la stabilité à long terme au-delà de PHP 8.5. Cette modification renforce les performances, réduit les dépendances externes et fournit une base plus évolutive pour Commerce.

_AC-15160_

#### Prise en charge officielle de Symfony 7.4 LTS

Dans le cadre des mises à jour de la plateforme Adobe Commerce 2.4.9, toutes les dépendances de Symfony ont été mises à jour vers les dernières versions de Symfony LTS 7.4. Toutes les classes personnalisées étendant les classes principales Symfony ont des déclarations de type et des signatures de méthode mises à jour alignées sur les dernières exigences Symfony, évitant les problèmes de compatibilité et assurant une transition en douceur vers les composants de framework mis à jour.

_AC-15170 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/c127d10b)_

#### Dépendance Allure PHPUnit mise à niveau vers la version 3

La dépendance `allure-framework/allure-phpunit` a été mise à niveau vers la version majeure 3, qui ajoute la prise en charge de PHP 8.4 et PHP 8.5 et modernise la pile de rapports de test basée sur Allure. La dépendance native précédemment requise par les anciennes versions d’Allure PHPUnit a été supprimée, ce qui simplifie l’installation et la maintenance.

_AC-14548 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/87b8b34e)_

#### Rapports New Relic mis à jour vers l’API NerdGraph

Le module de reporting New Relic a été mis à jour afin de prendre en charge l’API de suivi des modifications de New Relic NerdGraph (GraphQL) tout en préservant complètement l’intégration existante du marqueur de déploiement REST v2. Le changement offre des métadonnées de déploiement plus riches, la prise en charge des points d’entrée régionaux (États-Unis et UE) et la configurabilité via les paramètres d’administration sans interrompre les configurations existantes.

_AC-15461_

#### Mises à jour de la bibliothèque JavaScript

- **Chart.js mis à jour vers la version 4.5.0**

  Mise à niveau de la bibliothèque de graphiques JavaScript Chart.js vers la version 4.5.0 afin d’améliorer les performances de rendu des graphiques, d’améliorer les fonctionnalités visuelles et de corriger les vulnérabilités de sécurité dans le tableau de bord d’administration et les modules de création de rapports.

  _AC-14304, AC-15133 - [contribution de code GitHub](https://github.com/magento/magento2/commit/768b4442), [contribution de code GitHub](https://github.com/magento/magento2/commit/657f983e)_

- **Bibliothèque de chargement de fichier de copie mise à jour vers la version 4.13.4**

  Mise à niveau de la bibliothèque de chargement de fichiers Uppy vers la version 4.13.4 afin d’améliorer les fonctionnalités de chargement de fichiers, l’expérience utilisateur et de corriger les vulnérabilités de sécurité dans la gestion des fichiers dans l’interface d’administration d’Adobe Commerce et les composants frontaux.

  _AC-14307 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/eb491c05)_

- Bibliothèque **jQuery Validate mise à niveau vers la version 1.21.0**

  Mise à niveau de la bibliothèque jQuery Validate vers la version 1.21.0 afin d’améliorer les fonctionnalités de validation des formulaires, d’améliorer l’expérience utilisateur et d’assurer la compatibilité moderne des navigateurs dans tous les formulaires Adobe Commerce dans les interfaces d’administration et frontale.

  _AC-14403 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/98b2848a)_

- Bibliothèque de l’interface utilisateur **jQuery mise à niveau vers la version 1.14.1**

  Mise à niveau de la bibliothèque de l’interface utilisateur jQuery vers la version 1.14.1 pour améliorer les widgets de l’interface utilisateur, l’accessibilité et assurer la compatibilité moderne des navigateurs sur tous les composants d’interface d’administration et front-end d’Adobe Commerce.

  _AC-14417 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/77c589a6)_

- **Préprocesseur CSS Less.js mis à niveau vers la version 4.2.2**

  Mise à niveau du préprocesseur CSS Less.js vers la version 4.2.2 pour améliorer les performances de la compilation CSS, améliorer la prise en charge de la syntaxe et moderniser le processus de création de thème sur tous les thèmes frontaux et admin d’Adobe Commerce.

  _AC-14418 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/98b2848a)_

- **Bibliothèque de fuseau horaire Moment mise à niveau vers la version 0.5.43**

  Mise à niveau de la bibliothèque de fuseaux horaires Moment (`moment-timezone-with-data.js`) vers la version 0.5.43 afin d’améliorer les fonctionnalités de gestion des fuseaux horaires, de mettre à jour les données de fuseau horaire avec les dernières modifications de la base de données des fuseaux horaires IANA et d’améliorer la précision du traitement de la date et de l’heure pour toutes les opérations Adobe Commerce internationales et multi-fuseaux horaires.

  _AC-14419 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/98b2848a)_

- **Bibliothèque utilitaire Underscore.js mise à niveau vers la version 1.13.7**

  Mise à niveau de la bibliothèque d’utilitaires Underscore.js vers la version 1.13.7 afin d’améliorer les fonctionnalités de programmation fonctionnelle de JavaScript, d’améliorer les performances de manipulation des données et d’assurer la compatibilité moderne des navigateurs sur tous les composants front-end et de l’interface d’administration d’Adobe Commerce.

  _AC-14420 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/98b2848a)_

### Sécurité

#### Validation CAPTCHA désormais appliquée pour les API REST et GraphQL

Lorsque CAPTCHA (ou reCAPTCHA) est activé pour le formulaire Créer un compte , la même validation CAPTCHA est désormais appliquée pour la création de compte client via les API REST et GraphQL.

_AC-16245_

#### Amélioration des performances des requêtes asynchrones/en bloc

Ce correctif corrige la dégradation des performances des points d’entrée d’API web asynchrones en bloc introduits après le correctif de sécurité APSB25-08, en restaurant les délais d’exécution attendus.

_AC-14078 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/9a7352b7)_

#### Configuration simplifiée de l’authentification à deux facteurs

Les utilisateurs administrateurs doivent désormais configurer un seul des fournisseurs 2FA activés par le commerçant (par exemple, l’authentificateur Google ou U2F) pour accéder au panneau d’administration. D’autres fournisseurs activés peuvent être configurés ultérieurement, si nécessaire. Auparavant, lorsque plusieurs fournisseurs 2FA étaient activés, chaque utilisateur administrateur devait tous les configurer avant de pouvoir se connecter, ce qui entraînait des frictions pour les utilisateurs qui n’avaient pas accès à chaque fournisseur.

_AC-8253 - [Contribution du code GitHub](https://github.com/magento-commerce/security-package/commit/41e5a26bd36528cb6b1bdc27b249696a2c721779)_

### Expédition

#### Migration de l’intégration USPS vers les API RESTful USPS

Pour se conformer à la suppression annoncée par USPS des anciennes API Web Tools, Adobe Commerce a migré son intégration USPS vers les nouvelles API RESTful USPS.

Améliorations clés :

- Prise en charge de la double API : les utilisateurs administrateurs peuvent désormais choisir entre l’ancienne API Web Tools et la nouvelle API RESTful USPS via les paramètres de configuration.
- Mise à niveau de l’authentification : utilise OAuth 2.0 pour un accès sécurisé à l’API.
- Format de données amélioré : utilise JSON au lieu de XML pour une communication plus épurée et plus efficace.
- Nouveaux champs d’administration :
   - URL REST de la passerelle (en fonction du mode : En développement ou En direct)
   - ID client et secret
   - Type de compte, Numéro de compte
   - CRID, MID, code d&#39;identification de l&#39;expéditeur
   - AES/ITN pour les expéditions internationales
   - Modes d’expédition autorisés spécifiques à REST

Cette migration garantit qu’Adobe Commerce reste conforme aux normes USPS, améliore la fiabilité du système et garantit aux commerçants des intégrations d’expédition pérennes.

_AC-13257_

#### Migration de l’intégration DHL vers les API RESTful MyDHL

L&#39;intégration d&#39;expédition DHL intégrée prend désormais en charge les API RESTful MyDHL, tout en préservant la compatibilité avec l&#39;ancienne API XML DHL Express. Les commerçants peuvent choisir l’API DHL à utiliser dans l’administration, bénéficiant des fonctionnalités REST modernes sans interrompre les configurations XML existantes.

_AC-13258_
