---
source-git-commit: d0304f4060080f70c079fb571210cd015407f1cf
workflow-type: tm+mt
source-wordcount: '1996'
ht-degree: 0%

---
# Adobe Commerce avec packages B2B

<!-- The 'packages' variable contains the 'packages' node of the '_data/codebase/b2b/composer_lock.json' file
 -->

<!-- The 'packages-dev' variable contains the 'packages-dev' node of the '_data/codebase/b2b/composer_lock.json' file
 -->

<!-- The 'product' variable contains data of the 'magento/product-enterprise-edition' package
 -->

<!-- The edition variable contains `commerce-b2b` value from the _data/names.yml file
 -->

B2B pour Adobe Commerce utilise le compositeur pour gérer les packages PHP.

Le `composer.json` le fichier déclare la liste des packages, alors que le `composer.lock` Le fichier stocke une liste complète des packages (une version complète de chaque package et de ses dépendances) utilisés pour créer une installation d’Adobe Commerce ou de Magento Open Source.

La documentation de référence suivante est générée à partir du `composer.lock` et couvre les packages requis inclus dans B2B pour Adobe Commerce 1.4.2.

## Dépendances

`magento/extension-b2b 1.4.2` a les dépendances suivantes :

```config
magento/framework: >=103.0.6 <=103.0.7
magento/magento2-b2b-base: 1.4.2
magento/module-b2b: 100.4.1
magento/module-bundle-negotiable-quote: 100.4.0
magento/module-bundle-requisition-list: 100.4.0
magento/module-bundle-requisition-list-graph-ql: 1.4.0
magento/module-bundle-shared-catalog: 100.4.0
magento/module-checkout-address-search-negotiable-quote: 100.4.1
magento/module-checkout-agreements-negotiable-quote: 100.4.0
magento/module-checkout-agreements-purchase-order: 1.4.0
magento/module-company: 101.2.1
magento/module-company-credit: 100.4.0
magento/module-company-credit-graph-ql: 1.4.0
magento/module-company-graph-ql: 1.4.0
magento/module-company-payment: 100.4.0
magento/module-company-shipping: 1.4.0
magento/module-configurable-negotiable-quote: 100.4.0
magento/module-configurable-requisition-list: 100.4.1
magento/module-configurable-requisition-list-graph-ql: 1.4.0
magento/module-configurable-shared-catalog: 100.4.0
magento/module-downloadable-requisition-list-graph-ql: 1.4.0
magento/module-gift-card-negotiable-quote: 100.4.0
magento/module-gift-card-requisition-list: 100.4.0
magento/module-gift-card-requisition-list-graph-ql: 1.4.0
magento/module-gift-card-shared-catalog: 100.4.0
magento/module-grouped-requisition-list: 100.4.0
magento/module-grouped-shared-catalog: 100.4.0
magento/module-negotiable-quote: 100.4.2
magento/module-negotiable-quote-async-order: 1.4.1
magento/module-negotiable-quote-graph-ql: 1.4.0
magento/module-negotiable-quote-shared-catalog: 100.4.1
magento/module-negotiable-quote-weee: 100.4.1
magento/module-order-history-search: 100.4.2
magento/module-paypal-negotiable-quote: 1.4.1
magento/module-paypal-purchase-order: 1.4.0
magento/module-purchase-order: 100.4.1
magento/module-purchase-order-graph-ql: 1.4.0
magento/module-purchase-order-rule: 100.4.0
magento/module-purchase-order-rule-graph-ql: 1.4.0
magento/module-quick-order: 100.4.0
magento/module-quick-order-graph-ql: 1.4.0
magento/module-requisition-list: 100.4.1
magento/module-requisition-list-graph-ql: 1.4.0
magento/module-shared-catalog: 100.4.1
magento/module-shared-catalog-graph-ql: 1.4.0
magento/security-package-b2b: 1.0.4
```

## Licences tierces

### Apache-2.0, LGPL-2.1-uniquement

<table>
  <thead>
    <tr>
      <th>Nom</th>
      <th>Type</th>
      <th>Description</th>
    </tr>
  </thead>
  <tbody>
  <tr>
    <td>
      <a href="https://github.com/elastic/elasticsearch-php.git">elasticsearch/elasticsearch</a>
    </td>
    <td>bibliothèque</td>
    <td>Client PHP pour Elasticsearch</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/opensearch-project/opensearch-php.git">opensearch-project/opensearch-php</a>
    </td>
    <td>bibliothèque</td>
    <td>Client PHP pour OpenSearch</td>
  </tr>
  </tbody>
</table>

### Apache-2.0

<table>
  <thead>
    <tr>
      <th>Nom</th>
      <th>Type</th>
      <th>Description</th>
    </tr>
  </thead>
  <tbody>
  <tr>
    <td>
      <a href="https://github.com/adobe/stock-api-libphp.git">astock/stock-api-libphp</a>
    </td>
    <td>bibliothèque</td>
    <td>Bibliothèque d’API Adobe Stock</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/awslabs/aws-crt-php.git">aws/aws-crt-php</a>
    </td>
    <td>bibliothèque</td>
    <td>AWS Common Runtime pour PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/aws/aws-sdk-php.git">aws/aws-sdk-php</a>
    </td>
    <td>bibliothèque</td>
    <td>SDK AWS pour PHP - Utilisez Amazon Web Services dans votre projet PHP</td>
  </tr>
  <tr>
    <td>
      paypal/module-braintree
    </td>
    <td>métapaquet</td>
    <td>Magento Braintree</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/wikimedia/less.php.git">wikimedia/less.php</a>
    </td>
    <td>bibliothèque</td>
    <td>Port PHP du processeur LESS</td>
  </tr>
  </tbody>
</table>

### BSD-2-Clause

<table>
  <thead>
    <tr>
      <th>Nom</th>
      <th>Type</th>
      <th>Description</th>
    </tr>
  </thead>
  <tbody>
  <tr>
    <td>
      <a href="https://github.com/Bacon/BaconQrCode.git">bacon/bacon-qr-code</a>
    </td>
    <td>bibliothèque</td>
    <td>BaconQrCode est un générateur de code QR pour PHP.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/DASPRiD/Enum.git">dasprid/enum</a>
    </td>
    <td>bibliothèque</td>
    <td>Implémentation de l’énumération PHP 7.1</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/webimpress/safe-writer.git">webimpress/safe-writer</a>
    </td>
    <td>bibliothèque</td>
    <td>Outil pour écrire des fichiers en toute sécurité, pour éviter les conditions de concurrence</td>
  </tr>
  </tbody>
</table>

### BSD-3-Clause

<table>
  <thead>
    <tr>
      <th>Nom</th>
      <th>Type</th>
      <th>Description</th>
    </tr>
  </thead>
  <tbody>
  <tr>
    <td>
      <a href="https://github.com/colinmollenhour/Cm_Cache_Backend_File.git">colinmollenhour/cache-backend-file</a>
    </td>
    <td>magento-module</td>
    <td>Le serveur principal Zend_Cache_Backend_File du stock présente des performances extrêmement faibles pour le nettoyage par balises, ce qui le rend inutilisable à mesure que le nombre d’éléments mis en cache augmente. Ce serveur principal effectue de nombreuses modifications, ce qui se traduit par un gain de performances considérable, en particulier pour le nettoyage des balises.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/colinmollenhour/php-redis-session-abstract.git">colinmollenhour/php-redis-session-abstract</a>
    </td>
    <td>bibliothèque</td>
    <td>Gestionnaire de sessions Redis avec verrouillage optimiste</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/firebase/php-jwt.git">firebase/php-jwt</a>
    </td>
    <td>bibliothèque</td>
    <td>Une simple bibliothèque pour coder et décoder les jetons web JSON (JWT) en PHP. Doit être conforme à la spécification actuelle.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/google/recaptcha.git">google/recaptcha</a>
    </td>
    <td>bibliothèque</td>
    <td>Bibliothèque cliente pour reCAPTCHA, un service gratuit qui protège les sites web contre le spam et les abus.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-captcha.git">laminas/laminas-captcha</a>
    </td>
    <td>bibliothèque</td>
    <td>Générer et valider des CAPTCHA à l’aide de puces, d’images, de ReCaptcha, etc</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-code.git">laminas/laminas-code</a>
    </td>
    <td>bibliothèque</td>
    <td>Extensions de l'API PHP Reflection, analyse de code statique et génération de code</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-config.git">laminas/laminas-config</a>
    </td>
    <td>bibliothèque</td>
    <td>fournit une interface utilisateur basée sur une propriété d’objet imbriqué pour accéder à ces données de configuration dans le code de l’application</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-crypt.git">laminas/laminas-crypt</a>
    </td>
    <td>bibliothèque</td>
    <td>Outils de chiffrement puissants et hachage de mot de passe</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-db.git">laminas/laminas-db</a>
    </td>
    <td>bibliothèque</td>
    <td>Couche d'abstraction de base de données, abstraction SQL, abstraction de jeu de résultats et implémentations RowDataGateway et TableDataGateway</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-di.git">laminas/laminas-di</a>
    </td>
    <td>bibliothèque</td>
    <td>Injection de dépendance automatisée pour conteneurs PSR-11</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-escaper.git">laminas/échappeur de laminas</a>
    </td>
    <td>bibliothèque</td>
    <td>Échappement sécurisé du HTML, des attributs de HTML, de JavaScript, CSS et des URL</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-eventmanager.git">laminas/laminas-eventmanager</a>
    </td>
    <td>bibliothèque</td>
    <td>Déclencher et écouter des événements dans une application PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-feed.git">laminas/laminas-feed</a>
    </td>
    <td>bibliothèque</td>
    <td>fournit des fonctionnalités pour créer et utiliser des flux RSS et Atom</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-file.git">laminas/laminas-file</a>
    </td>
    <td>bibliothèque</td>
    <td>Localisation des fichiers de classe PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-filter.git">laminas/laminas-filter</a>
    </td>
    <td>bibliothèque</td>
    <td>Filtrer et normaliser les données et les fichiers par programmation</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-http.git">laminas/laminas-http</a>
    </td>
    <td>bibliothèque</td>
    <td>Fournit une interface facile pour exécuter des requêtes HTTP (Hyper-Text Transfer Protocol)</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-i18n.git">laminas/laminas-i18n</a>
    </td>
    <td>bibliothèque</td>
    <td>Fournissez des traductions pour votre application, et filtrez et validez les valeurs internationalisées</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-json.git">laminas/laminas-json</a>
    </td>
    <td>bibliothèque</td>
    <td>fournit des méthodes pratiques pour sérialiser PHP natif en JSON et décoder JSON en PHP natif</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-loader.git">laminas/laminas-loader</a>
    </td>
    <td>bibliothèque</td>
    <td>Stratégies de chargement automatique et de chargement du plug-in</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-mail.git">laminas-mail</a>
    </td>
    <td>bibliothèque</td>
    <td>Fournit une fonctionnalité généralisée pour composer et envoyer du texte et des messages électroniques multipartie compatibles MIME</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-math.git">laminas/laminas-math</a>
    </td>
    <td>bibliothèque</td>
    <td>Créer des nombres pseudo-aléatoires cryptographiquement sécurisés et gérer les grands entiers</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-mime.git">laminas-mime</a>
    </td>
    <td>bibliothèque</td>
    <td>Création et analyse de parties et de messages MIME</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-modulemanager.git">laminas/laminas-modulemanager</a>
    </td>
    <td>bibliothèque</td>
    <td>Système d'application modulaire pour applications laminas-mvc</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-mvc.git">laminas/laminas-mvc</a>
    </td>
    <td>bibliothèque</td>
    <td>Couche MVC pilotée par les événements de Laminas, y compris les applications, contrôleurs et modules externes MVC</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-oauth.git">laminas/laminas-oauth</a>
    </td>
    <td>bibliothèque</td>
    <td></td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-permissions-acl.git">laminas/laminas-permissions-acl</a>
    </td>
    <td>bibliothèque</td>
    <td>Fournit une mise en œuvre légère et flexible de la liste de contrôle d’accès (ACL) pour la gestion des privilèges</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-recaptcha.git">laminas/laminas-recaptcha</a>
    </td>
    <td>bibliothèque</td>
    <td>wrapper OOP pour le service web ReCaptcha</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-router.git">laminas/laminas-router</a>
    </td>
    <td>bibliothèque</td>
    <td>Système de routage flexible pour applications HTTP et console</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-server.git">laminas/laminas-server</a>
    </td>
    <td>bibliothèque</td>
    <td>Créer des serveurs RPC basés sur la réflexion</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-servicemanager.git">laminas/laminas-servicemanager</a>
    </td>
    <td>bibliothèque</td>
    <td>Récipient D'Injection De Dépendance Commandé En Usine</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-session.git">laminas/laminas-session</a>
    </td>
    <td>bibliothèque</td>
    <td>Interface orientée objet pour les sessions PHP et le stockage</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-soap.git">laminas/laminas-savon</a>
    </td>
    <td>bibliothèque</td>
    <td></td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-stdlib.git">laminas/laminas-stdlib</a>
    </td>
    <td>bibliothèque</td>
    <td>Extensions SPL, utilitaires de tableau, gestionnaires d’erreur, etc</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-text.git">laminas/laminas-text</a>
    </td>
    <td>bibliothèque</td>
    <td>Création de figlets et de tableaux textuels</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-uri.git">laminas/laminas-uri</a>
    </td>
    <td>bibliothèque</td>
    <td>Un composant qui aide à la manipulation et à la validation des URI (Uniform Resource Identifiers)</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-validator.git">laminas/laminas-validator</a>
    </td>
    <td>bibliothèque</td>
    <td>Classes de validation pour un large éventail de domaines et possibilité d’enchaîner des validateurs pour créer des critères de validation complexes</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-view.git">laminas/laminas-view</a>
    </td>
    <td>bibliothèque</td>
    <td>Calque de vue flexible prenant en charge et fournissant plusieurs calques de vue, assistants, etc</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/nikic/PHP-Parser.git">nikic/php-parser</a>
    </td>
    <td>bibliothèque</td>
    <td>Un analyseur PHP écrit en PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/tedious/JShrink.git">tedivm/jshrink</a>
    </td>
    <td>bibliothèque</td>
    <td>Javascript Minifier intégré en PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/tubalmartin/YUI-CSS-compressor-PHP-port.git">tubalmartin/cssmin</a>
    </td>
    <td>bibliothèque</td>
    <td>Un port PHP du compresseur CSS YUI</td>
  </tr>
  </tbody>
</table>

### BSD-3-Clause-Modification

<table>
  <thead>
    <tr>
      <th>Nom</th>
      <th>Type</th>
      <th>Description</th>
    </tr>
  </thead>
  <tbody>
  <tr>
    <td>
      <a href="https://github.com/colinmollenhour/Cm_Cache_Backend_Redis.git">colinmollenhour/cache-backend-redis</a>
    </td>
    <td>magento-module</td>
    <td>Serveur principal Zend_Cache utilisant Redis avec prise en charge complète des balises.</td>
  </tr>
  </tbody>
</table>

### ISC

<table>
  <thead>
    <tr>
      <th>Nom</th>
      <th>Type</th>
      <th>Description</th>
    </tr>
  </thead>
  <tbody>
  <tr>
    <td>
      <a href="https://github.com/paragonie/sodium_compat.git">paragonie/sodium_compat</a>
    </td>
    <td>bibliothèque</td>
    <td>Implémentation pure PHP de libsodium ; utilise l'extension PHP si elle existe</td>
  </tr>
  </tbody>
</table>

### LGPL-2.1-ou-ultérieur

<table>
  <thead>
    <tr>
      <th>Nom</th>
      <th>Type</th>
      <th>Description</th>
    </tr>
  </thead>
  <tbody>
  <tr>
    <td>
      <a href="https://github.com/ezyang/htmlpurifier.git">ezyang/htmlpurifier</a>
    </td>
    <td>bibliothèque</td>
    <td>Filtre de HTML conforme aux normes écrit en PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-amqplib/php-amqplib.git">php-amqplib/php-amqplib</a>
    </td>
    <td>bibliothèque</td>
    <td>Anciennement videlalvaro/php-amalplib.  Cette bibliothèque est une implémentation pure de PHP du protocole AMQP. Il a été testé par rapport à RabbitMQ.</td>
  </tr>
  </tbody>
</table>

### MIT

<table>
  <thead>
    <tr>
      <th>Nom</th>
      <th>Type</th>
      <th>Description</th>
    </tr>
  </thead>
  <tbody>
  <tr>
    <td>
      <a href="https://github.com/braintree/braintree_php.git">braintree/braintree_php</a>
    </td>
    <td>bibliothèque</td>
    <td>Bibliothèque cliente PHP Braintree</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/brick/math.git">brique/mathématiques</a>
    </td>
    <td>bibliothèque</td>
    <td>Bibliothèque arithmétique de précision arbitraire</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/brick/varexporter.git">brick/varexporter</a>
    </td>
    <td>bibliothèque</td>
    <td>Une alternative puissante à var_export(), qui peut exporter des fermetures et des objets sans __set_state()</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/ChristianRiesen/base32.git">christian-riesen/base32</a>
    </td>
    <td>bibliothèque</td>
    <td>Codeur/décodeur Base32 selon RFC 4648</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/colinmollenhour/credis.git">colinmollenhour/credis</a>
    </td>
    <td>bibliothèque</td>
    <td>Credis est une interface légère vers le magasin clé-valeur Redis qui enveloppe la bibliothèque phpredis lorsqu’elle est disponible pour de meilleures performances.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/ca-bundle.git">compositeur/ca-bundle</a>
    </td>
    <td>bibliothèque</td>
    <td>Vous permet de trouver un chemin d’accès au lot d’autorité de certification système et inclut un secours au lot d’autorité de certification Mozilla.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/class-map-generator.git">compositeur/class-map-generator</a>
    </td>
    <td>bibliothèque</td>
    <td>Utilitaires pour analyser le code PHP et générer des cartes de classes.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/composer.git">compositeur</a>
    </td>
    <td>bibliothèque</td>
    <td>Le compositeur vous aide à déclarer, gérer et installer des dépendances de projets PHP. Cela garantit que vous disposez de la pile appropriée partout.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/metadata-minifier.git">compositeur/minificateur de métadonnées</a>
    </td>
    <td>bibliothèque</td>
    <td>Petite bibliothèque utilitaire qui gère la minimisation et l’extension des métadonnées.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/pcre.git">compositeur/pcre</a>
    </td>
    <td>bibliothèque</td>
    <td>Bibliothèque d’encapsulation PCRE qui propose des remplacements preg_* sécurisés par le type.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/semver.git">compositeur/serveur</a>
    </td>
    <td>bibliothèque</td>
    <td>Bibliothèque de serveurs qui offre des utilitaires, une analyse de contrainte de version et une validation.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/spdx-licenses.git">composer/spdx-licences</a>
    </td>
    <td>bibliothèque</td>
    <td>Liste des licences SPDX et bibliothèque de validation.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/xdebug-handler.git">compositeur/xdebug-handler</a>
    </td>
    <td>bibliothèque</td>
    <td>Redémarre un processus sans Xdebug.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/endroid/qr-code.git">endroid/qr-code</a>
    </td>
    <td>bibliothèque</td>
    <td>Code QR Android</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/ezimuel/guzzlestreams.git">ézimuel/guzzlestreams</a>
    </td>
    <td>bibliothèque</td>
    <td>Branchement de guzzle/ruisseaux (abandonné) à utiliser avec elasticsearch-php</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/ezimuel/ringphp.git">ezimuel/ringphp</a>
    </td>
    <td>bibliothèque</td>
    <td>Branchement de guzzle/RingPHP (abandonné) à utiliser avec elasticsearch-php</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/guzzle/guzzle.git">guzzlehttp/guzzle</a>
    </td>
    <td>bibliothèque</td>
    <td>Guzzle est une bibliothèque cliente HTTP PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/guzzle/promises.git">guzzlehttp/promesses</a>
    </td>
    <td>bibliothèque</td>
    <td>Guzzle promet une bibliothèque</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/guzzle/psr7.git">guzzlehttp/psr7</a>
    </td>
    <td>bibliothèque</td>
    <td>Implémentation du message PSR-7 qui fournit également des méthodes d’utilitaire courantes</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/justinrainbow/json-schema.git">justinrainbow/json-schema</a>
    </td>
    <td>bibliothèque</td>
    <td>Bibliothèque permettant de valider un schéma json.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/thephpleague/flysystem.git">league/flysystem</a>
    </td>
    <td>bibliothèque</td>
    <td>Abstraction de stockage de fichier pour PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/thephpleague/flysystem-aws-s3-v3.git">league/flysystem-aws-s3-v3</a>
    </td>
    <td>bibliothèque</td>
    <td>Adaptateur de système de fichiers AWS S3 pour Flysystem.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/thephpleague/mime-type-detection.git">league/mime-type-detection</a>
    </td>
    <td>bibliothèque</td>
    <td>Détection de type MIME pour Flysystem</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Seldaek/monolog.git">monologue/monologue</a>
    </td>
    <td>bibliothèque</td>
    <td>Envoie vos journaux aux fichiers, sockets, boîtes de réception, bases de données et divers services web</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/jmespath/jmespath.php.git">mtdowling/jmespath.php</a>
    </td>
    <td>bibliothèque</td>
    <td>Spécifier de manière déclarative comment extraire des éléments d’un document JSON</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/paragonie/constant_time_encoding.git">paragonie/constant_time_encoding</a>
    </td>
    <td>bibliothèque</td>
    <td>Implémentations à temps constant du codage RFC 4648 (Base-64, Base-32, Base-16)</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/paragonie/random_compat.git">paragonie/random_compat</a>
    </td>
    <td>bibliothèque</td>
    <td>PHP 5.x polyfill pour random_bytes() et random_int() de PHP 7</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/MyIntervals/emogrifier.git">pelago/emogrifier</a>
    </td>
    <td>bibliothèque</td>
    <td>Convertit les styles CSS en attributs de style intégrés dans votre code de HTML</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/PhpGt/CssXPath.git">phpgt/cssxpath</a>
    </td>
    <td>bibliothèque</td>
    <td>Convertissez les sélecteurs CSS en requêtes XPath.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/PhpGt/Dom.git">phpgt/dom</a>
    </td>
    <td>bibliothèque</td>
    <td>API DOM moderne.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/PhpGt/PropFunc.git">phpgt/propfunc</a>
    </td>
    <td>bibliothèque</td>
    <td>Fonctions d’accesseur et de mutateur de propriété.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/phpseclib/mcrypt_compat.git">phpseclib/mcrypt_compat</a>
    </td>
    <td>bibliothèque</td>
    <td>Extension PHP 5.x-8.x polyfill pour mcrypt</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/phpseclib/phpseclib.git">phpseclib/phpseclib</a>
    </td>
    <td>bibliothèque</td>
    <td>Bibliothèque de communications sécurisé PHP - Implémentations Pure-PHP de RSA, AES, SSH2, SFTP, X.509, etc.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/clock.git">psr/horloge</a>
    </td>
    <td>bibliothèque</td>
    <td>Interface commune pour la lecture de l'horloge.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/container.git">psr/container</a>
    </td>
    <td>bibliothèque</td>
    <td>Interface de conteneur commun (PHP FIG PSR-11)</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/event-dispatcher.git">psr/event-dispatcher</a>
    </td>
    <td>bibliothèque</td>
    <td>Interfaces standard pour la gestion des événements.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/http-client.git">psr/http-client</a>
    </td>
    <td>bibliothèque</td>
    <td>Interface commune pour les clients HTTP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/http-factory.git">psr/http-factory</a>
    </td>
    <td>bibliothèque</td>
    <td>Interfaces communes pour les usines de messages HTTP PSR-7</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/http-message.git">psr/http-message</a>
    </td>
    <td>bibliothèque</td>
    <td>Interface commune pour les messages HTTP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/log.git">psr/log</a>
    </td>
    <td>bibliothèque</td>
    <td>Interface commune pour les bibliothèques de journalisation</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/ralouphie/getallheaders.git">ralouphie/getallheaders</a>
    </td>
    <td>bibliothèque</td>
    <td>Un polyfill pour les en-têtes getall.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/ramsey/collection.git">ramsey/collection</a>
    </td>
    <td>bibliothèque</td>
    <td>Une bibliothèque PHP pour représenter et manipuler les collections.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/ramsey/uuid.git">ramsey/uuid</a>
    </td>
    <td>bibliothèque</td>
    <td>Une bibliothèque PHP pour générer et travailler avec des identifiants universels uniques (UUID).</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/reactphp/promise.git">react/promise</a>
    </td>
    <td>bibliothèque</td>
    <td>Une implémentation légère de CommonJS Promises/A pour PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/MyIntervals/PHP-CSS-Parser.git">sabberworm/php-css-parser</a>
    </td>
    <td>bibliothèque</td>
    <td>Analyseur pour les fichiers CSS écrits en PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Seldaek/jsonlint.git">seld/jsonlint</a>
    </td>
    <td>bibliothèque</td>
    <td>JSON Linter</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Seldaek/phar-utils.git">seld/phar-utils</a>
    </td>
    <td>bibliothèque</td>
    <td>Utilitaires de format de fichier PHAR, pour le moment où PHP vous phare</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Seldaek/signal-handler.git">seld/signal-handler</a>
    </td>
    <td>bibliothèque</td>
    <td>Gestionnaire de signaux Unix simple qui échoue silencieusement lorsque les signaux ne sont pas pris en charge pour un développement simple sur plusieurs plateformes</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Spomky-Labs/aes-key-wrap.git">spomky-labs/aes-key-wrap</a>
    </td>
    <td>bibliothèque</td>
    <td>AES Key Wrap pour PHP.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Spomky-Labs/otphp.git">spomky-labs/otphp</a>
    </td>
    <td>bibliothèque</td>
    <td>Une bibliothèque PHP pour générer des mots de passe à usage unique selon RFC 4226 (algorithme HOTP) et RFC 6238 (algorithme TOTP) et compatible avec Google Authenticator</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Spomky-Labs/pki-framework.git">spomky-labs/pki-framework</a>
    </td>
    <td>bibliothèque</td>
    <td>Un framework PHP pour la gestion des infrastructures à clé publique. Il comprend des certificats de clé publique X.509, des certificats d’attribut, des demandes de certification et la validation du chemin de certification.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/config.git">symfony/config</a>
    </td>
    <td>bibliothèque</td>
    <td>Permet de rechercher, charger, combiner, remplir automatiquement et valider des valeurs de configuration de tout type</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/console.git">symfony/console</a>
    </td>
    <td>bibliothèque</td>
    <td>Facilite la création d’interfaces de ligne de commande belles et testables</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/css-selector.git">symfony/css-selector</a>
    </td>
    <td>bibliothèque</td>
    <td>Convertit les sélecteurs CSS en expressions XPath</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/dependency-injection.git">symfony/dependency-injection</a>
    </td>
    <td>bibliothèque</td>
    <td>Permet de normaliser et de centraliser la façon dont les objets sont construits dans votre application</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/deprecation-contracts.git">symphony/deprecation-constraints</a>
    </td>
    <td>bibliothèque</td>
    <td>Fonction générique et convention pour déclencher des avis d’obsolescence</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/error-handler.git">symfony/error-handler</a>
    </td>
    <td>bibliothèque</td>
    <td>Fournit des outils pour gérer les erreurs et faciliter le débogage du code PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/event-dispatcher.git">symphony/event-dispatcher</a>
    </td>
    <td>bibliothèque</td>
    <td>Fournit des outils qui permettent aux composants de votre application de communiquer entre eux en distribuant des événements et en les écoutant</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/event-dispatcher-contracts.git">symphony/event-dispatcher-constraints</a>
    </td>
    <td>bibliothèque</td>
    <td>Abstractions génériques liées à l’événement de répartition</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/filesystem.git">symphony/filesystem</a>
    </td>
    <td>bibliothèque</td>
    <td>Fournit des utilitaires de base pour le système de fichiers</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/finder.git">symfony/finder</a>
    </td>
    <td>bibliothèque</td>
    <td>Recherche des fichiers et répertoires via une interface fluide intuitive</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/http-client.git">symfony/http-client</a>
    </td>
    <td>bibliothèque</td>
    <td>Fournit des méthodes puissantes pour récupérer des ressources HTTP de manière synchrone ou asynchrone</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/http-client-contracts.git">symfony/http-client-contrats</a>
    </td>
    <td>bibliothèque</td>
    <td>Abstractions génériques liées aux clients HTTP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/http-foundation.git">symfony/http-foundation</a>
    </td>
    <td>bibliothèque</td>
    <td>Définit un calque orienté objet pour la spécification HTTP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/http-kernel.git">symfony/http-kernel</a>
    </td>
    <td>bibliothèque</td>
    <td>Fournit un processus structuré pour convertir une requête en réponse</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/intl.git">symfony/intl</a>
    </td>
    <td>bibliothèque</td>
    <td>Donne accès aux données de localisation de la bibliothèque ICU</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-ctype.git">symfony/polyfill-type</a>
    </td>
    <td>bibliothèque</td>
    <td>Polyfill symfony pour les fonctions ctype</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-intl-grapheme.git">symfony/polyfill-intl-grapheme</a>
    </td>
    <td>bibliothèque</td>
    <td>Symfony polyfill pour les fonctions grapheme_* d'intl</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-intl-idn.git">symfony/polyfill-intl-idn</a>
    </td>
    <td>bibliothèque</td>
    <td>Symfony polyfill pour les fonctions idn_to_ascii et idn_to_utf8 d’intl</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-intl-normalizer.git">symfony/polyfill-intl-normalizer</a>
    </td>
    <td>bibliothèque</td>
    <td>Symfony polyfill pour la classe Normalizer d’intl et fonctions associées</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-mbstring.git">symfony/polyfill-mbstring</a>
    </td>
    <td>bibliothèque</td>
    <td>Polyfill Symfony pour l’extension Mbstring</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-php72.git">symfony/polyfill-php72</a>
    </td>
    <td>bibliothèque</td>
    <td>Symfony polyfill backporting certaines fonctionnalités de PHP 7.2+ pour abaisser les versions de PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-php73.git">symfony/polyfill-php73</a>
    </td>
    <td>bibliothèque</td>
    <td>Symfony polyfill backporting certaines fonctionnalités de PHP 7.3+ pour abaisser les versions de PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-php80.git">symfony/polyfill-php80</a>
    </td>
    <td>bibliothèque</td>
    <td>Symfony polyfill backporting certaines fonctionnalités de PHP 8.0+ pour abaisser les versions de PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-php81.git">symfony/polyfill-php81</a>
    </td>
    <td>bibliothèque</td>
    <td>Symfony polyfill backporting certaines fonctionnalités de PHP 8.1+ pour abaisser les versions de PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-php83.git">symfony/polyfill-php83</a>
    </td>
    <td>bibliothèque</td>
    <td>Symfony polyfill backporting certaines fonctionnalités de PHP 8.3+ pour abaisser les versions de PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/process.git">symfony/process</a>
    </td>
    <td>bibliothèque</td>
    <td>Exécute les commandes dans les sous-processus</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/service-contracts.git">symfony/service-constraints</a>
    </td>
    <td>bibliothèque</td>
    <td>Abstractions génériques liées aux services d’écriture</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/string.git">symfony/string</a>
    </td>
    <td>bibliothèque</td>
    <td>Fournit une API orientée objet aux chaînes et traite de manière unifiée les octets, les points de code UTF-8 et les clusters grapheme</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/var-dumper.git">symfony/var-dumper</a>
    </td>
    <td>bibliothèque</td>
    <td>Fournit des mécanismes pour parcourir toute variable PHP arbitraire</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/var-exporter.git">symfony/var-exporter</a>
    </td>
    <td>bibliothèque</td>
    <td>Permet d'exporter n'importe quelle structure de données PHP sérialisable en code PHP brut</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/web-token/jwt-framework.git">web-token/jwt-framework</a>
    </td>
    <td>symfony-bundle</td>
    <td>Bibliothèque de signature et de chiffrement d’objet JSON pour le bundle PHP et Symfony.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/webmozarts/assert.git">webmozart/assert</a>
    </td>
    <td>bibliothèque</td>
    <td>Assertions pour valider l'entrée/la sortie de la méthode avec de jolis messages d'erreur.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/webonyx/graphql-php.git">webonyx/graphql-php</a>
    </td>
    <td>bibliothèque</td>
    <td>Port PHP de l’implémentation de référence de GraphQL</td>
  </tr>
  </tbody>
</table>

### OSL-3.0, AFL-3.0

<table>
  <thead>
    <tr>
      <th>Nom</th>
      <th>Type</th>
      <th>Description</th>
    </tr>
  </thead>
  <tbody>
  <tr>
    <td>
      paypal/module-braintree-customer-balance
    </td>
    <td>magento2-module</td>
    <td>S.O.</td>
  </tr>
  <tr>
    <td>
      paypal/module-braintree-chèque-cadeau-compte
    </td>
    <td>magento2-module</td>
    <td>S.O.</td>
  </tr>
  <tr>
    <td>
      paypal/module-braintree-coffret-cadeau
    </td>
    <td>magento2-module</td>
    <td>S.O.</td>
  </tr>
  <tr>
    <td>
      paypal/module-braintree-graph-ql
    </td>
    <td>magento2-module</td>
    <td>S.O.</td>
  </tr>
  </tbody>
</table>

### OSL-3.0

<table>
  <thead>
    <tr>
      <th>Nom</th>
      <th>Type</th>
      <th>Description</th>
    </tr>
  </thead>
  <tbody>
  </tbody>
</table>

### PHP

<table>
  <thead>
    <tr>
      <th>Nom</th>
      <th>Type</th>
      <th>Description</th>
    </tr>
  </thead>
  <tbody>
  <tr>
    <td>
      <a href="https://github.com/2tvenom/CBOREncode.git">2tvenom/cborencode</a>
    </td>
    <td>bibliothèque</td>
    <td>Encodeur CBOR pour PHP</td>
  </tr>
  </tbody>
</table>

### Propriétaire

<table>
  <thead>
    <tr>
      <th>Nom</th>
      <th>Type</th>
      <th>Description</th>
    </tr>
  </thead>
  <tbody>
  </tbody>
</table>

### propriétaire

<table>
  <thead>
    <tr>
      <th>Nom</th>
      <th>Type</th>
      <th>Description</th>
    </tr>
  </thead>
  <tbody>
  <tr>
    <td>
      paypal/module-braintree-core
    </td>
    <td>magento2-module</td>
    <td>Branchement du module Braintree de Magento 2.2.0 de Gene Commerce pour PayPal.</td>
  </tr>
  </tbody>
</table>
