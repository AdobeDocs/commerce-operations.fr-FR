---
source-git-commit: 78a34dc069a30b72a1e0baff36085a2458a05983
workflow-type: tm+mt
source-wordcount: '1349'
ht-degree: 0%
---
# Adobe Commerce (v2.4.10)

## Caractéristiques de la version v2.4.10-alpha1

Les points forts suivants s’appliquent à la version Adobe Commerce 2.4.10-alpha1.

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

#### [2.4.10-alpha1] Mise à niveau des composants Platform

Adobe Commerce version 2.4.10-alpha1 comprend un ensemble de mises à niveau des dépendances de la plateforme, des améliorations de la compatibilité, des mises à jour de la bibliothèque frontend et des correctifs de stabilité. Les modifications terminées suivantes sont incluses dans cette version :

- Predis : mise à niveau de `predis/predis` de la version 2.x vers la version 3.x, amélioration de la compatibilité avec les environnements Redis et Valkey et maintien de l’alignement du client Redis avec les dernières versions de dépendance prises en charge.
- Programme d’installation du compositeur Magento : correction d’un problème en raison duquel `magento-composer-installer` pouvait quitter silencieusement sans terminer le processus d’installation, ce qui améliorait la fiabilité des installations basées sur le compositeur.
- Knockout.js : mise à niveau de Knockout.js de la version 3.5.1 vers la version 3.5.3, avec les mises à jour de validation et de compatibilité requises.
- Chart.js : mise à niveau de Chart.js de la version 4.5.0 vers la version 4.5.1, y compris les mises à jour de validation et de compatibilité nécessaires.
- Less.js : mise à niveau de Less.js de la version 4.2.2 vers la version 4.6.4, avec les mises à jour de validation et de compatibilité associées.
- Uppy : mise à niveau de Uppy de la version 5.0.0 vers la version 5.2.0, y compris les modifications de validation et de compatibilité requises.
- Interface utilisateur de jQuery : mise à niveau de l’interface utilisateur de jQuery de la version 1.14.1 vers la version 1.14.2, avec les mises à jour de validation et de compatibilité associées.
- Compatibilité PHP 8.5 : Correction d&#39;un problème d&#39;obsolescence de PHP 8.5 lié à `chr()`, en s&#39;assurant que la fonction est fournie avec des valeurs d&#39;octets valides et en améliorant la compatibilité avec PHP 8.5.
- Recherche catalogue : correction d’un problème en raison duquel la réindexation des `catalogsearch_fulltext` pouvait s’arrêter pendant le traitement, ce qui améliorait la fiabilité de l’indexation de la recherche catalogue.
- js-cookie : mise à niveau de js-cookie de la version 3.0.5 vers la version 3.0.7 ou la version prise en charge applicable, en répondant aux exigences de dépendance et de compatibilité.

_AC-17061_

#### Assurer la compatibilité de B2B 1.5.3-p1/1.5.4-alpha1 avec 2.4.10-alpha1, 2.4.9-p1, 2.4.8-p6, 2.4.7-p11 et 2.4.6-p16

B2B 1.5.4-alpha1 est compatible avec les lignes de mise à jour Adobe Commerce suivantes : 2.4.9, 2.4.8, 2.4.7 et 2.4.6.

_AC-17100_

#### Mettre à niveau et moderniser les dépendances NPM

Mise à jour des dépendances npm suivantes vers leurs dernières versions sécurisées afin de résoudre les vulnérabilités de sécurité connues :

- trait de soulignement
- imagemin-svgo
- globuleux
- serve-static
- grognement
- moins
- uglify-js
- marqué
- clean-css
- minimiste
- trim-newlines
- terser
- css-select
- énième contrôle
- semver-regex
- http-cache-semantics
- js-yaml
- package-json

Ces mises à jour de dépendance atténuent les vulnérabilités de sécurité identifiées tout en conservant les fonctionnalités de l’application existante.

_AC-17372_

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

#### [B2B] Les commandes fournisseur ne sont pas converties automatiquement en commande client avec ActiveMQ

Correction d’un problème en raison duquel les commandes fournisseur placées via le storefront avec l’approbation automatique activée n’étaient pas automatiquement converties en commandes client lors de l’utilisation d’ActiveMQ et de l’exécution des clients via cron (bin/magento cron:run). Auparavant, les messages étaient ajoutés à la file d’attente ActiveMQ, mais n’étaient pas traités, sauf si le client était démarré manuellement via l’interface de ligne de commande. Grâce à ce correctif, le client traite désormais les messages comme prévu après l’exécution de cron, assurant ainsi une conversion de commande transparente pour les commerçants B2B à l’aide d’ActiveMQ.

_AC-17679_

#### Optimisation du cache L2 de Symfony et rétrocompatibilité du cache hérité

Adobe Commerce 2.4.10 offre désormais une prise en charge optimisée du cache Symfony L2 tout en conservant l’implémentation existante du cache basé sur Zend en tant que valeur par défaut.

Les commerçants qui souhaitent utiliser Symfony Cache doivent explicitement l’activer et mettre à jour la configuration de cache requise spécifique à l’implémentation de Symfony L1/L2. Les commerçants existants qui continuent à utiliser le cache basé sur Zend n’ont pas besoin d’apporter de modifications à la configuration.

Cette approche de double cache offre aux commerçants la possibilité d’adopter le cache Symfony en fonction de leurs besoins, tout en assurant une rétrocompatibilité avec les configurations et déploiements de cache existants.

_AC-17865_

### Autres frais

#### Gestion administrative des sous-régions des pays (Etats et Provinces)

Les commerçants peuvent désormais gérer les sous-régions des pays (telles que les États et les provinces) directement à partir de l’interface d’administration. Cette nouvelle fonctionnalité permet aux commerçants de :

- Afficher, ajouter, modifier, désactiver ou supprimer des régions pour n’importe quel pays.
- Mettez instantanément de nouvelles régions à disposition sous forme d’options de liste déroulante lors du passage en caisse, dans les formulaires d’adresse client et lors de la création de la commande d’administration. Aucun changement de code n’est nécessaire.
- Modifier les noms d&#39;affichage des régions (y compris les noms localisés) et les codes ISO.
- Désactivez les régions référencées par des commandes, des adresses ou des règles fiscales existantes (en veillant à ce que les données historiques restent exactes), tout en empêchant la suppression définitive de ces régions.
- Toutes les régions prédéfinies restent inchangées et sont désormais visibles et gérables dans la nouvelle interface.

Cette fonctionnalité est entièrement rétrocompatible et garantit que le comportement des adresses orientées client et API reste cohérent.

_AC-16192_

#### Mise à niveau de predis/predis de 2.x vers 3.x

La bibliothèque cliente Redis predis/predis a été mise à niveau de la version 2.x vers la version 3.x. Cette mise à niveau de version majeure s’aligne sur les dernières normes de dépendance, améliore la compatibilité et garantit la maintenabilité à long terme.

_AC-17101 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/de7188da)_

#### Mettez à niveau knockout.js de la version 3.5.1 vers la version 3.5.3.

Mise à niveau de la bibliothèque knockout.js de la version 3.5.1 vers la version 3.5.3. Cette mise à jour apporte des correctifs de bugs en amont et des améliorations de stabilité pour tous les composants de l’interface utilisateur en utilisant des liaisons Knockout dans storefront et admin.

_AC-17366 - [Contribution du code GitHub](https://github.com/magento/magento2/commit/de7188da)_

#### Mise à niveau du vernis vers la version 9 pour la version 2.4.10-alpha1

Adobe Commerce 2.4.10 est compatible avec Varnish version 9.0.

_AC-17972_
