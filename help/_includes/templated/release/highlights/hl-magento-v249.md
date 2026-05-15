---
source-git-commit: 3a341190ff7ab69ad49721f78dfc90bc9ef24b20
workflow-type: tm+mt
source-wordcount: '2138'
ht-degree: 0%

---
# Points forts de Magento Open Source (v2.4.9)

## Points forts de la version v2.4.9

Les points forts suivants s’appliquent à la version 2.4.9 de Magento Open Source.

### API

#### Ajout d’une possibilité de conserver l’héritage de la galerie de produits dans l’API REST lors de la mise à jour d’un produit au niveau de l’affichage du magasin

La mise à jour d’un produit via l’API REST dans une portée de magasin n’entraîne plus l’héritage des modifications des images et vidéos de produit à partir de la portée globale si media_gallery_entries est omis dans la payload ou défini sur NULL pour empêcher toute modification de la galerie de produits dans cette portée. En outre, il est désormais possible de restaurer l’héritage de la portée pour les images et les vidéos du produit via l’API REST en définissant le champ correspondant sur NULL.

_ACP2E-4358 - [contribution du code GitHub](https://github.com/magento/magento2/commit/f7bbcb4e)_

### Braintree

#### Mise en chambre forte de Google Pay via la zone Compte

Dans Adobe Commerce 2.4.9, les clients peuvent désormais archiver leurs cartes de paiement Google via la zone de compte lorsque le coffre de paiement Google est activé dans Braintree. Les cartes voûtées apparaissent sous les modes de paiement stockés, peuvent être utilisées pour les achats futurs au moment du passage en caisse et peuvent être supprimées par le client. Cela étend la prise en charge des coffres-forts au-delà des cartes et de PayPal à Google Pay.

_LOT-3459_

#### Real-Time Account Updater (RTAU)

La fonction Real-Time Account Updater (RTAU) d’Adobe Commerce 2.4.9 pour Braintree garantit que les informations de carte Visa, Mastercard et Discover sont automatiquement mises à jour lorsque les cartes expirent ou sont remplacées. Cela réduit les paiements en échec, maintient Magento Vault à jour et ignore les types non pris en charge (prépayé, Apple Pay, Google Pay) sans erreur.

_LOT-3462_

#### Prise en charge du type de carte ELO pour les paiements par carte Braintree

Dans Adobe Commerce 2.4.9, la prise en charge du type de carte ELO a été ajoutée à Braintree Payments. Les administrateurs peuvent désormais activer l’ELO dans la configuration des cartes de crédit et les clients peuvent passer des commandes avec les cartes ELO au moment du passage en caisse, ce qui garantit des transactions transparentes via Braintree.

_LOT-3464_

#### Payer Sur Facture

Pour Adobe Commerce 2.4.9 (extension Braintree), un nouveau mode de paiement local « Payer sur facture » a été ajouté pour les acheteurs allemands. Le paiement sur facture est une option d&#39;achat immédiat, de paiement différé (BNPL) proposée par PayPal + Ratepay (« Rechnungskauf mit Ratepay ») qui permet aux clients de recevoir les marchandises en premier et de payer la facture dans les 30 jours, sans avoir besoin d&#39;un compte PayPal. Comme il ne s&#39;agit pas d&#39;un paiement instantané, la finalisation des commandes est pilotée par un webhook côté serveur de PayPal.

_LOT-3475_

#### Ajouter des offres à la feuille de paie Google Pay Express

Pour l&#39;extension Braintree dans Adobe Commerce 2.4.9, la feuille de paie Google Pay Express prend désormais en charge les codes promotion/offre. Les acheteurs peuvent appliquer, afficher et supprimer des promotions de panier Magento directement dans la feuille de paie Google, ce qui garantit que les clients effectuant un passage en caisse express reçoivent les mêmes remises et incentives que les flux de paiement standard.

_LOT-3476_

#### Ajouter des offres à la feuille de paie Apple Pay Express

Pour l&#39;extension Braintree dans Adobe Commerce 2.4.9, la feuille de paie Apple Pay Express prend désormais en charge les codes promotion/offre. Les acheteurs peuvent appliquer un coupon directement dans la feuille de paie Apple afin que les utilisateurs de passage en caisse express bénéficient des mêmes remises et campagnes que les flux de passage en caisse standard.

_LOT-3477_

#### Payer avec Apple Pay sur Chrome et Firefox

Pour l’extension Braintree dans Adobe Commerce 2.4.9, Apple Pay peut désormais être utilisé sur Chrome et Firefox, pas seulement sur Safari. Lorsque Apple Pay Express est activé, les boutons Apple Pay sont disponibles dans tous les magasins pris en charge et les clients effectuent leur paiement en scannant un code avec leur iPhone.

_LOT-3478_

#### Rappel d’expédition côté serveur

Pour l’extension Braintree dans Adobe Commerce 2.4.9, le rappel d’expédition PayPal Express a été déplacé du côté client vers le côté serveur. Cela fournit des méthodes d’expédition dynamiques, des calculs de coûts en temps réel et des détails précis au niveau du panier directement dans la fenêtre modale PayPal, améliorant la fiabilité et jetant les bases de fonctionnalités futures telles que la prise en charge du module de contact, les flux de commutation d’applications et Venmo Express.

_LOT-3479_

#### Module de contact PayPal

Pour l’extension Braintree dans Adobe Commerce 2.4.9, un nouveau module de contact PayPal est introduit pour les commerçants américains. Lorsque cette option est activée, les acheteurs qui utilisent PayPal Express peuvent afficher et mettre à jour l&#39;adresse e-mail et le numéro de téléphone partagés avec le marchand directement dans la fenêtre modale PayPal lors des flux express (PDP, mini-panier, panier, passage en caisse express). Les coordonnées sélectionnées sont alors stockées dans la commande Adobe Commerce.

_LOT-3480_

#### BLIK (mode de paiement local)

Pour l’extension Braintree dans Adobe Commerce 2.4.9, BLIK a été ajouté en tant que nouveau mode de paiement local pour les acheteurs polonais. Cela permet des paiements BLIK sécurisés, basés sur les banques, dans le flux des méthodes de paiement locales (LPM) de Braintree, améliorant ainsi la commodité de passage en caisse et la conversion pour les clients en Pologne.

_LOT-3481_

#### Politique CSP de mise à jour de l’intégration Cardinal

Pour l’extension Braintree dans Adobe Commerce 2.4.9, la politique de sécurité du contenu (CSP) a été mise à jour afin de prendre en charge les dernières exigences d’intégration de Cardinal (3-D Secure). Cela permet de s’assurer que tous les scripts, iframes et ressources associées hébergés par Cardinal utilisés pendant les flux 3-D Secure sont autorisés par le CSP du navigateur, ce qui empêche les requêtes bloquées et les expériences de défi/vérification rompues.

_LOT-3485_

### Framework

#### Mise à niveau de la bibliothèque Web-token/jwt-framework vers la dernière version majeure.

Dans le cadre du processus d&#39;examen continu de la sécurité, nous avons évalué la dernière version majeure du cadre JWT afin d&#39;assurer la compatibilité future et de maintenir des normes de sécurité solides. Les fonctionnalités existantes de cette version ne sont pas affectées.

_AC-13209 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/2bac8114) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/09b36ebb) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/33b81f28)_

#### [Partie 2] - Mettez à jour toutes les dépendances de bibliothèque js et npm avec la dernière version disponible.

la prise en charge de la version du compositeur ne dépassait que la version 2.2.x du compositeur. Désormais, la prise en charge s’étend également à la version 2.4.x.

_AC-13792 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/19844aa0)_

#### Remplacez carlos-mg89/oauth par PHP Native Functions

Remplacement de la bibliothèque tierce carlos-mg89/oauth par des fonctions PHP OAuth natives pour améliorer la sécurité, réduire les dépendances externes et améliorer la stabilité de la plateforme.

_AC-14075 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/7b8064f7)_

#### Mettez à niveau les bibliothèques jquery/uppy et uppy vers la dernière version

Mise à niveau de la bibliothèque de chargement de fichiers Uppy vers la version 4.13.4 afin d’améliorer les fonctionnalités de chargement de fichiers, l’expérience utilisateur et de corriger les vulnérabilités de sécurité dans la gestion des fichiers dans l’interface d’administration d’Adobe Commerce et les composants frontaux.

_AC-14307 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/eb491c05)_

#### Mettre à niveau la bibliothèque jquery-validate vers la dernière version

Mise à niveau de la bibliothèque jQuery Validate vers la version 1.21.0 afin d’améliorer les fonctionnalités de validation des formulaires, d’améliorer l’expérience utilisateur et d’assurer la compatibilité moderne des navigateurs dans tous les formulaires Adobe Commerce dans les interfaces d’administration et frontale.

_AC-14403 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/98b2848a)_

#### Mettre à niveau la bibliothèque jquery-ui vers la dernière version

Mise à niveau de la bibliothèque de l’interface utilisateur jQuery vers la version 1.14.1 pour améliorer les widgets de l’interface utilisateur, l’accessibilité et assurer la compatibilité moderne des navigateurs sur tous les composants d’interface d’administration et front-end d’Adobe Commerce.

_AC-14417 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/77c589a6)_

#### Mettre à niveau la bibliothèque less.js vers la dernière version

Mise à niveau du préprocesseur CSS Less.js vers la version 4.2.2 pour améliorer les performances de la compilation CSS, améliorer la prise en charge de la syntaxe et moderniser le processus de création de thème sur tous les thèmes frontaux et admin d’Adobe Commerce.

_AC-14418 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/98b2848a)_

#### Mettez à niveau la bibliothèque moment-timezone-with-data.js vers la dernière version

Mise à niveau de la bibliothèque de fuseaux horaires Moment vers la version 0.5.43 afin d’améliorer les fonctionnalités de gestion des fuseaux horaires, de mettre à jour les données de fuseaux horaires avec les dernières modifications de la base de données des fuseaux horaires IANA et d’améliorer la précision du traitement date/heure pour toutes les opérations Adobe Commerce internationales et multi-fuseaux horaires.

_AC-14419 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/98b2848a)_

#### Mise à niveau de la bibliothèque underscore.js vers la dernière version

Mise à niveau de la bibliothèque d’utilitaires Underscore.js vers la version 1.13.7 afin d’améliorer les fonctionnalités de programmation fonctionnelle de JavaScript, d’améliorer les performances de manipulation des données et d’assurer la compatibilité moderne des navigateurs sur tous les composants front-end et de l’interface d’administration d’Adobe Commerce.

_AC-14420 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/98b2848a)_

#### Mettez à jour allure-framework/allure-phpunit version 3 et supprimez la dépendance native dans 2.4.9-alpha1.

Dans Adobe Commerce 2.4.9, la dépendance allure-framework/allure-phpunit a été mise à niveau vers la version majeure 3, qui ajoute la prise en charge de PHP 8.4, PHP 8.5 et modernise notre pile de rapports de test basée sur Allure. La dépendance native précédemment requise par les anciennes versions d’Allure PHPUnit a été supprimée le cas échéant, ce qui simplifie la configuration et la maintenance.

_AC-14548 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/87b8b34e)_

#### Mettez à niveau la dépendance chart.js vers la dernière version

La dépendance chart.js est mise à niveau vers la dernière version 4.5.0.

_AC-15133 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/657f983e)_

#### Ajoutez la prise en charge officielle de Symfony 7.4 LTS et de PHP 8.5 dans Adobe Commerce 2.4.9

Dans le cadre des mises à jour de la plateforme Adobe Commerce 2.4.9, toutes les dépendances Symfony utilisées par le package magento/compositeur ont été mises à jour vers les dernières versions de Symfony LTS 7.4. Cela aligne les outils du compositeur Commerce sur la ligne Symfony LTS active et supprime les contraintes de dépendance précédentes liées aux anciennes versions de Symfony. En outre, toutes les classes personnalisées étendant les classes principales Symfony ont mis à jour les déclarations de type et les signatures de méthode conformément aux dernières exigences Symfony avant la mise à niveau vers Adobe Commerce 2.4.9. Vous éviterez ainsi les problèmes de compatibilité et garantirez une transition en douceur vers les composants de framework mis à jour.

_AC-15170 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/c127d10b)_

### GraphQL

#### Assurez-vous que la mutation clearCart GraphQL est disponible dans Open Source

Avec Adobe Commerce 2.4.9, la mutation du GraphQL clearCart est désormais disponible pour tous les utilisateurs d’Open Source. Auparavant, cette mutation n’était accessible que dans Adobe Commerce, mais elle fait désormais partie de la fonctionnalité de panier GraphQL standard pour Open Source également.
La documentation relative à la mutation a été mise à jour pour refléter sa disponibilité dans Open Source pour la version 2.4.9.
Voir la documentation [clearCart GraphQL mutation](https://developer.adobe.com/commerce/webapi/graphql/schema/cart/mutations/clear-cart/).

_AC-16683 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/4449d914)_

#### [AC-2.4.9] Fusion de la logique du panier client et invité à l’aide de la configuration d’administration

Une nouvelle option de configuration d’administration a été introduite pour contrôler la manière dont les paniers d’invités et de clients sont fusionnés lorsqu’un acheteur se connecte. Cette amélioration vous offre la possibilité de définir le comportement de fusion de panier qui correspond le mieux aux besoins de votre entreprise.

_LYNX-889_

#### [AC-2.4.9] Obtention des commandes historiques avec des produits en rupture de stock

Les commandes historiques affichent désormais les détails du produit, même si elles sont désormais en rupture de stock.

_LYNX-913_

#### [AC-2.4.9] [CE] Implémenter ReCaptcha pour les mutations GraphQL manquantes

La validation ReCaptcha est ajoutée aux mutations updateCustomer, updateCustomerV2 et contactUs.

_LYNX-941_

### Autres frais

#### Captcha / reCAPTCHA ne fonctionne pas pour l’API / GraphQL

Dans Adobe Commerce 2.4.9, lorsque le CAPTCHA (ou reCAPTCHA) est activé pour le formulaire Créer un compte , la même validation CAPTCHA est désormais appliquée pour la création de compte client via les API REST et GraphQL.

_AC-16245 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/fd7f30ee)_

#### La branche braintree doit être mise à jour avec la prise en charge de PHP 8.5

L&#39;extension de paiement Braintree a été mise à jour pour prendre en charge le dernier runtime PHP 8.5, tout en maintenant la compatibilité avec PHP 8.4.

_LOT-3493_

#### Ajouter une opération d’effacement de la liste de souhaits

Ajout d’une nouvelle mutation clearWishlist pour prendre en charge les opérations en bloc, ce qui permet de supprimer tous les éléments d’une liste de souhaits en une seule action.

_LYNX-790_

#### Présentation de la mutation exchangeExternalCustomerToken

Ajout d’une nouvelle mutation GraphQL exchangeExternalCustomerToken qui authentifie les utilisateurs via un jeton d’intégration et renvoie le jeton client et les données client associées

_LYNX-815_

#### [AC] introduisez les requêtes GraphQL qui renvoient les ID de groupe, de segment et de règle de panier appliqués

Les requêtes GraphQL exposées pour récupérer l’uid codé du groupe de clients appliqué, des segments de clients et des règles de panier.

_LYNX-867_

#### [AC-2.4.9] Introduire le champ OrderTotal.grand_total_excl_tax

Un nouveau champ, OrderTotal.grand_total_excl_tax, a été ajouté à la réponse de commande GraphQL. Ce champ fournit le total général hors taxe de la commande, ce qui facilite l’accès aux totaux hors taxe directement à partir de l’API.

Avantages :

- Récupérez facilement le total général hors taxe pour n’importe quelle commande via GraphQL.
- Simplifie l&#39;intégration avec les systèmes externes qui nécessitent des totaux hors taxes.
- Réduit la nécessité de calculs personnalisés côté client.

_LYNX-892_

### PCI, sécurité

#### Refactoriser le stockage SRI pour optimiser les performances

Le stockage de hachage SRI génère désormais des fichiers distincts par zone, thème et paramètre régional, au lieu d’un seul grand fichier sri-hashes.json. Cette modification garantit que seul le fichier de hachage approprié est chargé pour chaque page, ce qui améliore les performances et réduit l’utilisation de la mémoire sur les magasins avec plusieurs thèmes ou paramètres régionaux.

_AC-16113 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/bc83cd2c)_

### Sécurité

#### Amélioration des performances des requêtes asynchrones/en bloc

Correction de la dégradation des performances des points d’entrée web asynchrones en bloc introduite après le correctif de sécurité APSB25-08, ce qui entraînait une augmentation des temps d’exécution.

_AC-14078 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/9a7352b7)_

#### Un seul fournisseur 2FA activé doit être configuré par utilisateur

Les utilisateurs administrateurs doivent désormais configurer un seul des fournisseurs 2FA activés par le commerçant (par exemple, l’authentificateur Google ou U2F) pour accéder au panneau d’administration. D’autres fournisseurs activés peuvent être configurés ultérieurement, si nécessaire. Auparavant, lorsque plusieurs fournisseurs 2FA étaient activés (par exemple, Google Authenticator et U2F), chaque utilisateur administrateur devait configurer tous les fournisseurs activés avant de pouvoir se connecter. Cela entraînait des frictions pour les utilisateurs qui n’avaient pas accès à tous les facteurs (comme une clé matérielle pour U2F).

_AC-8253 - [Contribution du code GitHub](https://github.com/magento/security-package/commit/71e7936b)_
