---
source-git-commit: 78a34dc069a30b72a1e0baff36085a2458a05983
workflow-type: tm+mt
source-wordcount: '691'
ht-degree: 0%
---
# Points forts de Magento Open Source (v2.4.10)

## Caractéristiques de la version v2.4.10-alpha1

Les points forts suivants s’appliquent à la version Magento Open Source 2.4.10-alpha1.

### Braintree

#### Voie Rapide

Ajout de la prise en charge de Fastlane par PayPal pour un passage en caisse plus rapide et plus sécurisé pour les invités.
Les clients peuvent choisir d’enregistrer leurs informations de paiement et d’expédition pour leurs futurs achats plus rapides.
Les clients Fastlane récurrents peuvent s’authentifier à l’aide d’un code unique et récupérer leurs informations enregistrées.
Les clients peuvent également ajouter ou modifier leurs cartes et adresses d’expédition enregistrées lors du passage en caisse.
Les options de style et de configuration de voie rapide sont également prises en charge.

_LOT-3521_

#### Braintree Insights

Ajout de Braintree Insights pour fournir aux commerçants des rapports centralisés sur les performances des paiements dans Magento Admin.
Fournit une visibilité sur les données de transaction, de règlement, de refus, de rejet de passerelle et de mode de paiement.
Prend en charge le filtrage par site web, période et intervalles quotidiens, hebdomadaires ou mensuels.
Permet aux commerçants d&#39;importer jusqu&#39;à 13 mois de données de transaction historiques pour la création de rapports.
Inclut la conservation des données et le nettoyage automatisé pour conserver jusqu’à 3 ans de données de transaction.

_LOT-3522_

#### Swish - Mode de paiement local

Présentation de Swish comme nouveau mode de paiement local suédois dans l&#39;extension Braintree Magento.
Swish est disponible lorsque les configurations de commerçant, de pays, de devise et de paiement suédoises requises sont respectées.
Les clients ayant une adresse de livraison ou de facturation suédoise peuvent effectuer leurs paiements en utilisant Swish lors du passage en caisse.
Ajout de la prise en charge des flux de paiement Swish réussis, annulés et en échec avec des réponses de passage en caisse appropriées.
Swish ne s’affiche que lorsque toutes les conditions de configuration requises sont remplies.

_LOT-3523_

#### Mise à niveau vers la version 4.9.0

Mise à niveau du module Braintree de la version 4.8.0 vers la version 4.9.0.
La mise à niveau comprend les dernières modifications et améliorations du module Braintree.
Vérification que le passage en caisse et le traitement des paiements Braintree continuent de fonctionner comme prévu après la mise à niveau.
Les flux existants de passage en caisse et de création de commande du client restent fonctionnels avec le module mis à niveau.
Des tests de régression de base ont été effectués pour s’assurer qu’aucun problème n’avait été introduit par la mise à niveau

_LOT-3530_

### Framework

#### Mise à niveau de la dépendance NPM : underscore.js (1.13.7 → 1.13.8)

Mise à jour de underscore.js de la version 1.13.7 vers la version 1.13.8 afin d’inclure les derniers correctifs en amont et les améliorations de stabilité.

_AC-17486 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/c69ec9c5)_

#### Mise à niveau de la dépendance NPM : imagemin-svgo (9.0.0 → 12.0.0)

Mise à jour d’imagemin-svgo de la version 9.0.0 à la version 12.0.0 afin d’inclure les derniers correctifs en amont, les mises à jour de sécurité et les améliorations de l’optimisation de SVG.

_AC-17657 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/c69ec9c5)_

#### Mise à niveau de la dépendance NPM : eslint-formatter-junit (8.40.0 → 9.0.1)

Mise à jour d’eslint-formatter-junit de la version 8.40.0 à la version 9.0.1 afin d’inclure les derniers correctifs en amont et des améliorations de compatibilité pour les rapports ESLint.

_AC-17659 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/c69ec9c5)_

#### Mise à niveau de la dépendance NPM : glob (11.0.0 → 13.0.0)

Mise à jour de la version globale de 11.0.0 à 13.0.0 afin d’inclure les derniers correctifs en amont, des améliorations des performances et des améliorations de compatibilité.

_AC-17660 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/c69ec9c5)_

#### Mise à niveau de la dépendance NPM : grunt-eslint (25.0.0 → 26.0.0)

Mise à jour de grunt-eslint de la version 25.0.0 à la version 26.0.0 afin d’inclure les derniers correctifs en amont et les améliorations de compatibilité.

_AC-17661 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/c69ec9c5)_

#### Mise à niveau de la dépendance NPM : serve-static (1.16.2 → 2.2.1)

Mise à jour de serve-static de 1.16.2 à 2.2.1 afin d’inclure les derniers correctifs en amont, les mises à jour de sécurité et les améliorations de compatibilité.

_AC-17662 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/c69ec9c5)_

#### Mettre à niveau les dernières dépendances NPM pour Grunt et Less

Mise à jour de Grunt et Less vers les dernières versions prises en charge, améliorant la stabilité et la compatibilité des builds frontaux.

_AC-17663 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/c69ec9c5)_

#### Mettez à niveau les dépendances de remplacement NPM vers les dernières versions prises en charge

Mise à jour de plusieurs dépendances de remplacement de NPM vers les dernières versions prises en charge, ce qui améliore la sécurité, la stabilité de build et la compatibilité.

_AC-17664 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/c69ec9c5)_

### Autres frais

#### Mise à niveau de predis/predis de 2.x vers 3.x

La bibliothèque cliente Redis predis/predis a été mise à niveau de la version 2.x vers la version 3.x. Cette mise à niveau de version majeure s’aligne sur les dernières normes de dépendance, améliore la compatibilité et garantit la maintenabilité à long terme.

_AC-17101 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/de7188da)_

#### Mettez à niveau knockout.js de la version 3.5.1 vers la version 3.5.3.

Mise à niveau de la bibliothèque knockout.js de la version 3.5.1 vers la version 3.5.3. Cette mise à jour apporte des correctifs de bugs en amont et des améliorations de stabilité pour tous les composants de l’interface utilisateur en utilisant des liaisons Knockout dans storefront et admin.

_AC-17366 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/de7188da)_
