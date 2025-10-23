---
source-git-commit: 5b0229d73dc7b8ad53750102e99447bb15baa84d
workflow-type: tm+mt
source-wordcount: '647'
ht-degree: 0%

---
# Notes de mise à jour de Magento Open Source (v2.4.9-alpha2)

## Caractéristiques de la version v2.4.9-alpha2

Les points forts suivants s’appliquent à la version 2.4.9-alpha2 de Magento Open Source.

### Framework

#### Ajouter la prise en charge d’OpenSearch 3

Adobe Commerce 2.4.9 est désormais entièrement compatible avec OpenSearch 3.x. Cette mise à jour permet aux commerçants de bénéficier d’une amélioration des performances, de la sécurité et d’une prise en charge à long terme tout en conservant une rétrocompatibilité avec OpenSearch 2.x.

_AC-11846_

#### Mise à jour de la version Nginx de 1.26 à 1.28

La version de Nginx utilisée dans les environnements de développement et de test dans toutes les versions actuellement prises en charge d’Adobe Commerce est mise à jour de 1.26 à 1.28, conformément à la dernière version stable de Nginx disponible.
Les tests au niveau des relations publiques s’exécutent désormais sur Nginx 1.28, ce qui confirme la compatibilité et la prise en charge complètes de toutes les versions d’Adobe Commerce.

_AC-14104_

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

#### Migration de TinyMCE vers Hugerte.org

En raison de la fin de la prise en charge de TinyMCE 5 et 6 et des incompatibilités de licence avec TinyMCE 7, l’implémentation actuelle de l’éditeur WYSIWYG d’Adobe Commerce est migrée de TinyMCE vers l’éditeur open source HugeRTE (https://hugerte.org/).
Cette migration garantit qu’Adobe Commerce reste conforme aux licences open source, évite les vulnérabilités connues de TinyMCE 6 et offre une expérience de modification moderne et prise en charge pour les commerçants et les développeurs.

_AC-14568_

#### Ajoutez la prise en charge complète de Valkey 8.x pour la version 2.4.9-alpha2

Adobe Commerce 2.4.9 prend entièrement en charge les commandes d’interface de ligne de commande Valkey, reflétant les fonctionnalités Redis actuelles. Mise à jour de la configuration admin et cloud pour permettre une configuration transparente de Valkey.
Cette mise à jour permet à Adobe Commerce de rester à l’épreuve du temps et performant en prenant en charge Valkey 8.x, offrant ainsi aux commerçants et aux développeurs une alternative fiable à Redis à l’approche de sa fin de vie.

_AC-14604_

### Autres frais

#### Mettre à jour le service AWS Valkey 8.x pour la création et le test de CNS

Mettre à jour le service AWS Valkey 8.x pour la version CNS

_AC-14470_

#### 2.4.9-alpha2 - Août Améliorations de base de la qualité

_AC-14700_

### Sécurité

#### Améliorations de la sécurité pour la version 2.4.9-alpha2

_AC-14610_

### Expédition

#### Migration de l’intégration USPS depuis les API Web Tools obsolètes vers les nouvelles API RESTful USPS

Pour se conformer à l’annonce d’USPS de la suppression des anciennes API Web Tools d’ici le 25 janvier 2026, l’intégration d’Adobe Commerce USPS est migrée vers les nouvelles API RESTful USPS.

Améliorations clés :

* Prise en charge de la double API : les utilisateurs administrateurs peuvent désormais choisir entre l’ancienne API Web Tools et la nouvelle API RESTful USPS via les paramètres de configuration.
* Mise à niveau de l’authentification : OAuth 2.0 implémenté pour un accès sécurisé à l’API.
* Format de données amélioré : passage de XML à JSON pour une communication plus épurée et plus efficace.
* Nouveaux champs d’administration :
   * URL REST de la passerelle (en fonction du mode : En développement ou En direct)
   * ID client et secret
   * Type de compte, Numéro de compte
   * CRID, MID, code d&#39;identification de l&#39;expéditeur
   * AES/ITN pour les expéditions internationales
   * Modes d’expédition autorisés spécifiques à REST

Cette migration garantit qu’Adobe Commerce reste conforme aux normes USPS, améliore la fiabilité du système et garantit aux commerçants des intégrations d’expédition pérennes.

_AC-13257_
