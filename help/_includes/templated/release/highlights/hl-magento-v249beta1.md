---
source-git-commit: 56974b4ada65c21ce1303e4b93bd8acb9fe41b28
workflow-type: tm+mt
source-wordcount: '991'
ht-degree: 0%

---
# Points forts de Magento Open Source (v2.4.9-beta1)

## Caractéristiques de la version v2.4.9-beta1

Les points forts suivants s’appliquent à la version Magento Open Source 2.4.9-bêta1.

### API

#### Ajout d’une possibilité de conserver l’héritage de la galerie de produits dans l’API REST lors de la mise à jour d’un produit au niveau de l’affichage du magasin

La mise à jour d’un produit via l’API REST dans une portée de magasin n’entraîne plus l’héritage des modifications des images et vidéos de produit à partir de la portée globale si media_gallery_entries est omis dans la payload ou défini sur NULL pour empêcher toute modification de la galerie de produits dans cette portée. En outre, il est désormais possible de restaurer l’héritage de la portée pour les images et les vidéos du produit via l’API REST en définissant le champ correspondant sur NULL

_ACP2E-4358 - [contribution du code GitHub](https://github.com/magento/magento2/commit/f7bbcb4e)_

### Framework

#### Recherchez la dernière version majeure de web-token/jwt-framework.

Dans le cadre du processus d&#39;examen continu de la sécurité, nous avons évalué la dernière version majeure du cadre JWT afin d&#39;assurer la compatibilité future et de maintenir des normes de sécurité solides. Les fonctionnalités existantes de cette version ne sont pas affectées.

_AC-13209 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/2bac8114) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/09b36ebb) - [Contribution du code GitHub](https://github.com/magento/magento2/commit/33b81f28)_

#### [Partie 2] - Mettez à jour toutes les dépendances de bibliothèque js et npm avec la dernière version disponible.

la prise en charge de la version du compositeur ne dépassait que la version 2.2.x du compositeur. Désormais, la prise en charge s’étend également à la version 2.4.x.

_AC-13792 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/19844aa0)_

#### Remplacez carlos-mg89/oauth par PHP Native Functions

Remplacement de la bibliothèque tierce carlos-mg89/oauth par des fonctions PHP OAuth natives pour améliorer la sécurité, réduire les dépendances externes et améliorer la stabilité de la plateforme.

_AC-14075 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/7b8064f7)_

#### Examiner la dernière version de chart.js

Mise à niveau de la bibliothèque de graphiques JavaScript Chart.js vers la dernière version 4.4.8 afin d’améliorer les performances de rendu des graphiques, d’améliorer les fonctionnalités visuelles et de corriger les vulnérabilités de sécurité dans le tableau de bord d’administration et les modules de création de rapports.

_AC-14304 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/768b4442)_

#### Rechercher la dernière version de jquery/uppy et uppy

Mise à niveau de la bibliothèque de chargement de fichiers Uppy vers la version 4.13.4 afin d’améliorer les fonctionnalités de chargement de fichiers, l’expérience utilisateur et de corriger les vulnérabilités de sécurité dans la gestion des fichiers dans l’interface d’administration d’Adobe Commerce et les composants frontaux.

_AC-14307 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/eb491c05)_

#### Examiner la dernière version de jquery-validate

Mise à niveau de la bibliothèque jQuery Validate vers la version 1.21.0 afin d’améliorer les fonctionnalités de validation des formulaires, d’améliorer l’expérience utilisateur et d’assurer la compatibilité moderne des navigateurs dans tous les formulaires Adobe Commerce dans les interfaces d’administration et frontale.

_AC-14403 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/98b2848a)_

#### Examiner la dernière version de jquery-ui

Mise à niveau de la bibliothèque de l’interface utilisateur jQuery vers la version 1.14.1 pour améliorer les widgets de l’interface utilisateur, l’accessibilité et assurer la compatibilité moderne des navigateurs sur tous les composants d’interface d’administration et front-end d’Adobe Commerce.

_AC-14417 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/77c589a6)_

#### Examiner la dernière version de less.js

Mise à niveau du préprocesseur CSS Less.js vers la version 4.2.2 pour améliorer les performances de la compilation CSS, améliorer la prise en charge de la syntaxe et moderniser le processus de création de thème sur tous les thèmes frontaux et admin d’Adobe Commerce.

_AC-14418 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/98b2848a)_

#### Recherchez la dernière version de moment-timezone-with-data.js

Mise à niveau de la bibliothèque de fuseaux horaires Moment vers la version 0.5.43 afin d’améliorer les fonctionnalités de gestion des fuseaux horaires, de mettre à jour les données de fuseaux horaires avec les dernières modifications de la base de données des fuseaux horaires IANA et d’améliorer la précision du traitement date/heure pour toutes les opérations Adobe Commerce internationales et multi-fuseaux horaires.

_AC-14419 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/98b2848a)_

#### Examiner la dernière version de underscore.js

Mise à niveau de la bibliothèque d’utilitaires Underscore.js vers la version 1.13.7 afin d’améliorer les fonctionnalités de programmation fonctionnelle de JavaScript, d’améliorer les performances de manipulation des données et d’assurer la compatibilité moderne des navigateurs sur tous les composants front-end et de l’interface d’administration d’Adobe Commerce.

_AC-14420 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/98b2848a)_

#### Mettez à jour allure-framework/allure-phpunit version 3 et supprimez la dépendance native dans 2.4.9-alpha1.

Dans Adobe Commerce 2.4.9, la dépendance allure-framework/allure-phpunit a été mise à niveau vers la version majeure 3, qui ajoute la prise en charge de PHP 8.4, PHP 8.5 et modernise notre pile de rapports de test basée sur Allure. La dépendance native précédemment requise par les anciennes versions d’Allure PHPUnit a été supprimée le cas échéant, ce qui simplifie la configuration et la maintenance.

_AC-14548 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/87b8b34e)_

#### Mettez à niveau la dépendance chart.js vers la dernière version

La dépendance chart.js est mise à niveau vers la dernière version 4.5.0

_AC-15133 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/657f983e)_

#### Ajoutez la prise en charge officielle de Symfony 7.4 LTS et de PHP 8.5 dans Adobe Commerce 2.4.9

Dans le cadre des mises à jour de la plateforme Adobe Commerce 2.4.9, toutes les dépendances Symfony utilisées par le package magento/compositeur ont été mises à jour vers les dernières versions de Symfony LTS 7.4. Cela permet d’aligner l’outil Compositeur de Commerce sur la ligne Symfony LTS actuelle et de supprimer les contraintes de dépendance précédentes liées aux anciennes versions de Symfony. En outre, toutes les classes personnalisées étendant les classes principales Symfony ont mis à jour les déclarations de type et les signatures de méthode conformément aux dernières exigences Symfony avant la mise à niveau vers Adobe Commerce 2.4.9. Vous éviterez ainsi les problèmes de compatibilité et garantirez une transition en douceur vers les composants de framework mis à jour.

_AC-15170 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/c127d10b)_

### Autres frais

#### Captcha / reCaptcha ne fonctionne pas pour l’API / GraphQl

Dans Adobe Commerce 2.4.9, lorsque le CAPTCHA (ou reCAPTCHA) est activé pour le formulaire Créer un compte , la même validation CAPTCHA est désormais appliquée pour la création de compte client via les API REST et GraphQL.

_AC-16245 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/fd7f30ee)_

### Sécurité

#### Amélioration des performances des requêtes asynchrones/en bloc

Correction de la dégradation des performances des points d’entrée web asynchrones en bloc introduite après le correctif de sécurité APSB25-08, ce qui entraînait une augmentation des temps d’exécution.

_AC-14078 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/9a7352b7)_

#### Un seul fournisseur 2FA activé doit être configuré par utilisateur

Les utilisateurs administrateurs doivent désormais configurer un seul des fournisseurs 2FA activés par le commerçant (par exemple, l’authentificateur Google ou U2F) pour accéder au panneau d’administration. D’autres fournisseurs activés peuvent être configurés ultérieurement, si nécessaire. Auparavant, lorsque plusieurs fournisseurs 2FA étaient activés (par exemple, Google Authenticator et U2F), chaque utilisateur administrateur devait configurer tous les fournisseurs activés avant de pouvoir se connecter. Cela entraînait des frictions pour les utilisateurs qui n’avaient pas accès à tous les facteurs (comme une clé matérielle pour U2F).

_AC-8253 - [Contribution du code GitHub](https://github.com/magento/security-package/commit/71e7936b)_

### Évaluation et prévisualisation

#### [Requête de fonctionnalité] Aperçu de l’évaluation du contenu dans la vue mobile

La fonctionnalité d’aperçu intermédiaire du panneau d’administration permet désormais de générer avec précision des aperçus d’appareil mobile simulés par un navigateur, ce qui permet d’avoir une représentation visuelle de la façon dont la mise à jour intermédiaire apparaîtra sur un appareil mobile.

_ACP2E-3397 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/520f9e30)_
