---
title: Fichiers de configuration de module
description: Découvrez comment personnaliser un module à l’aide de types de configuration.
exl-id: 87433c28-8e3d-43d0-b77e-3ff9a680af5f
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '1252'
ht-degree: 0%

---

# Présentation des fichiers de configuration de module

Les responsabilités du fichier de configuration `config.xml` utilisé dans les versions antérieures de Commerce sont désormais réparties entre plusieurs fichiers situés dans différents répertoires de module. Le Commerce plusieurs fichiers de configuration charge à la demande uniquement lorsqu’un module demande un type de configuration spécifique.

Vous pouvez utiliser ces fichiers, également appelés _types de configuration_, pour personnaliser des aspects spécifiques du comportement de votre module.

Plusieurs modules peuvent déclarer des fichiers de configuration qui affectent le même type de configuration (des événements, par exemple), et ces fichiers de configuration multiples sont fusionnés.

Vous trouverez ci-dessous les termes courants utilisés dans cette rubrique :

- **Objet de configuration** : bibliothèque ou classe Commerce chargée de définir et de valider le type de configuration. Par exemple, l’objet de configuration pour `config.xml` est [Magento\Framework\App\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/Config.php).

- **Étape de configuration** : les étapes sont définies comme _primaire_, _global_ et _area_. Chaque étape détermine le moment où le type de configuration est chargé et fusionné avec les types de configuration du même nom. Par exemple, les fichiers `module.xml` sont fusionnés avec d’autres fichiers `module.xml`.

- **Étendue de configuration** : Complémentaire aux étapes de configuration, une étendue définit le modèle de type de configuration. Par exemple, `adminhtml` est une portée de zone qui est chargée avec à l’étape avec les configurations `adminhtml` d’autres modules. Pour plus d’informations, voir [Modules et zones](https://developer.adobe.com/commerce/php/architecture/modules/areas/).

## Chargement et fusion des configurations

Cette section explique comment les fichiers de configuration sont chargés et fusionnés.

### Comment Commerce charge les fichiers de configuration

Commerce charge les fichiers de configuration dans l’ordre suivant (tous les chemins d’accès dépendent du répertoire d’installation de Commerce) :

- Configuration de Principal ([app/etc/di.xml](https://github.com/magento/magento2/blob/2.4/app/etc/di.xml)). Ce fichier est utilisé pour démarrer Commerce.
- Configurations globales des modules (`<your component base dir>/<vendorname>/<component-type>-<component-name>/etc/*.xml`). Collecte certains fichiers de configuration de tous les modules et les fusionne.
- Configuration spécifique à la zone à partir des modules (`<your component base dir>/<vendorname>/<component-type>-<component-name>/etc/<area>/*.xml`). Collecte des fichiers de configuration de tous les modules et les fusionne dans la configuration globale. Certaines configurations spécifiques à une zone peuvent remplacer ou étendre la configuration globale.

where

- `<your component base dir>` est le répertoire de base dans lequel se trouve votre composant. Les valeurs types sont `app/code` ou `vendor` par rapport au répertoire d’installation de Commerce.
- `<vendorname>` est le nom du fournisseur du composant ; par exemple, le nom du fournisseur Commerce est `magento`.
- `<component-type>` est l’un des suivants :

   - `module-` : extension ou module.
   - `theme-` : thème.
   - `language-` : package de langue.

>[!INFO]
>
>Actuellement, les thèmes se trouvent sous `<magento_root>/app/design/frontend` ou `<magento_root>/app/design/adminhtml`.

- `<component-name>` : nom de votre composant tel que défini dans [compositeur.json](https://github.com/magento/magento2/blob/2.4/composer.json).

### Fusion du fichier de configuration

Les noeuds des fichiers de configuration sont fusionnés en fonction de leurs XPath entièrement qualifiés, qui a un attribut spécial défini dans le tableau `$idAttributes` déclaré comme identifiant. Cet identifiant doit être unique pour tous les noeuds imbriqués dans le même noeud parent.

Algorithme de fusion d’applications Commerce :

- Si les identifiants de noeud sont égaux (ou si aucun identifiant n’est défini), tout le contenu sous-jacent dans le noeud (attributs, noeuds enfants et contenu scalaire) est remplacé.
- Si les identifiants de noeud ne sont pas égaux, le noeud est un nouvel enfant du noeud parent.
- Si le document d’origine comporte plusieurs noeuds portant le même identifiant, une erreur est déclenchée car les identifiants ne peuvent pas être distingués.

Une fois les fichiers de configuration fusionnés, le document obtenu contient tous les noeuds des fichiers d’origine.

>[!INFO]
>
>Vous pouvez utiliser la classe [\Magento\Framework\Config\Reader\Filesystem](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/Reader/Filesystem.php) pour déboguer et comprendre la logique derrière le processus [chargeur de fichiers de configuration](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/Reader/Filesystem.php#L125) et [configurations de fusion](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/Reader/Filesystem.php#L144).

## Types, objets et interfaces de configuration

Les sections suivantes fournissent des informations sur les types de configuration, les objets de configuration correspondants et les interfaces que vous pouvez utiliser pour travailler avec les objets :

### Types et objets de configuration

Le tableau suivant présente chaque type de configuration et l’objet de configuration Commerce auquel il se rapporte.

| Fichier de configuration | Description | Évaluation | Objet de configuration |
| --- | --- | --- | --- |
| `address_formats.xml` | Déclaration du format d’adresse | principal, global | [\Magento\Customer\Model\Address\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Customer/Model/Address/Config.php) |
| `acl.xml` | [Liste de contrôle d’accès](https://developer.adobe.com/commerce/webapi/get-started/authentication/#relationship-between-aclxml-and-webapixml) | global | [\Magento\Framework\Acl\AclResource\Provider](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Acl/AclResource/Provider.php) |
| `analytics.xml` | [Création de rapports avancés](https://devdocs.magento.com/guides/v2.4/advanced-reporting/data-collection.html) | principal, global | [\Magento\Analytics\Model\Config\Reader](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Analytics/Model/Config/Reader.php) |
| `cache.xml` | Déclaration du type de cache | principal, global | [\Magento\Framework\Cache\Config\Data](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Cache/Config/Data.php) |
| `catalog_attributes.xml` | Configuration des attributs du catalogue | global | [\Magento\Catalog\Model\Attribute\Config\Data](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Catalog/Model/Attribute/Config/Data.php) |
| `config.php` et `env.php` | [Configuration de déploiement](../reference/deployment-files.md) | Ces fichiers sont lisibles/modifiables par le processeur de configuration interne. | Sans objet, ne peut pas être personnalisé |
| `config.xml` | Configuration du système | principal, global | [\Magento\Framework\App\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/Config.php) |
| `communication.xml` | [Définit les aspects du système de file de messages](https://developer.adobe.com/commerce/php/development/components/message-queues/configuration/#communicationxml) | global | [\Magento\WebapiAsync\Code\Generator\Config\RemoteServiceReader\Communication](https://github.com/magento/magento2/blob/2.4/app/code/Magento/WebapiAsync/Code/Generator/Config/RemoteServiceReader/Communication.php) |
| `crontab.xml` | [Configure les groupes cron](../cron/custom-cron-reference.md#configure-cron-groups) | global | [\Magento\Cron\Model\Config\Data](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Cron/Model/Config/Data.php) |
| `cron_groups.xml` | [ Spécifie les options du groupe cron ](../cron/custom-cron-reference.md) | global | [\Magento\Cron\Model\Groups\Config\Data](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Cron/Model/Groups/Config/Data.php) |
| `db_schema.xml` | [Schéma déclaratif](https://developer.adobe.com/commerce/php/development/components/declarative-schema/configuration/) | global | [Magento\Framework\Setup\Declaration\Schema](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Setup/Declaration/Schema/SchemaConfig.php) |
| `di.xml` | Configuration de [injection de dépendance](https://developer.adobe.com/commerce/php/development/components/dependency-injection/) | principal, global, zone | [\Magento\Framework\ObjectManager\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/ObjectManager/Config/Config.php) |
| `eav_attributes.xml` | Fournit la configuration des attributs d’expérience visuelle | global | [\Magento\Eav\Model\Entity\Attribute\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Eav/Model/Entity/Attribute/Config.php) |
| `email_templates.xml` | Configuration des modèles d&#39;email | global | [\Magento\Email\Model\Template\Config\Data](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Email/Model/Template/Config/Data.php) |
| `esconfig.xml` | [Mot de passe du moteur de recherche avec les paramètres régionaux du moteur de recherche config](../search/search-stopwords.md#create-stopwords-for-a-new-locale) | global | [\Magento\Elasticsearch\Model\Adapter\Index\Config\EsConfig](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Elasticsearch/Model/Adapter/Index/Config/EsConfig.php) |
| `events.xml` | Configuration des événements/observateurs | global, zone | [\Magento\Framework\Event](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Event.php) |
| `export.xml` | Exporter la configuration des entités | global | [\Magento\ImportExport\Model\Export\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/ImportExport/Model/Export/Config.php) |
| `extension_attributes.xml` | [Attributs d’extension](https://developer.adobe.com/commerce/php/development/components/attributes/#extension-attributes) | global | [\Magento\Framework\Api\ExtensionAttribute\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Api/ExtensionAttribute/Config.php) |
| `fieldset.xml` | Définit les jeux de champs | global | [\Magento\Framework\DataObject\Copy\Config\Reader](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/DataObject/Copy/Config/Reader.php) |
| `indexer.xml` | [Déclarer les indexeurs](https://developer.adobe.com/commerce/php/development/components/indexing/custom-indexer/) | global | [\Magento\Framework\Indexer\Config\Reader](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Indexer/Config/Reader.php) |
| `import.xml` | Déclarer les entités d’importation | global | [\Magento\ImportExport\Model\Import\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/ImportExport/Model/Import/Config.php) |
| `menu.xml` | Définit les options de menu pour l’administrateur. | adminhtml | [\Magento\Backend\Model\Menu\Config\Reader](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Backend/Model/Menu/Config/Reader.php) |
| `module.xml` | Définit les données de configuration de module et la dépendance de type Soft. | principal, global | [\Magento\Framework\Module\ModuleList\Loader](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Module/ModuleList/Loader.php) |
| `mview.xml` | [Configuration MView](https://developer.adobe.com/commerce/php/development/components/indexing/custom-indexer/#mview-configuration) | principal, global | [\Magento\Framework\Mview\Config\Data](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Mview/Config/Data.php) |
| `payment.xml` | Configuration du module de paiement | principal, global | [\Magento\Payment\Model\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Payment/Model/Config.php) |
| `persistent.xml` | Fichier de configuration [Magento_Persistent](https://developer.adobe.com/commerce/php/module-reference/module-persistent/) | global | [\Magento\Persistent\Helper\Data](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Persistent/Helper/Data.php) |
| `pdf.xml` | Paramètres du PDF | global | [\Magento\Sales\Model\Order\Pdf\Config\Reader](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Sales/Model/Order/Pdf/Config/Reader.php) |
| `product_options.xml` | Configuration des options de produit | global | [\Magento\Catalog\Model\ProductOptions\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Catalog/Model/ProductOptions/Config.php) |
| `product_types.xml` | Définit le type de produit | global | [\Magento\Catalog\Model\ProductTypes\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Catalog/Model/ProductTypes/Config.php) |
| `queue_consumer.xml` | [Définit la relation entre une file d&#39;attente existante et son consommateur](https://developer.adobe.com/commerce/php/development/components/message-queues/configuration/#queue_consumerxml) | global | [\Magento\Framework\MessageQueue\Consumer\Config\Xml\Reader](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/MessageQueue/Consumer/Config/Xml/Reader.php) |
| `queue_publisher.xml` | [Définit l’exchange de publication d’une rubrique.](https://developer.adobe.com/commerce/php/development/components/message-queues/configuration/#queue_publisherxml) | global | [\Magento\WebapiAsync\Code\Generator\Config\RemoteServiceReader\Publisher](https://github.com/magento/magento2/blob/2.4/app/code/Magento/WebapiAsync/Code/Generator/Config/RemoteServiceReader/Publisher.php) |
| `queue_topology.xml` | [Définit les règles de routage des messages, déclare les files d’attente et les exchanges](https://developer.adobe.com/commerce/php/development/components/message-queues/configuration/#queue_topologyxml) | global | [\Magento\Framework\MessageQueue\Topology\Config\Xml\Reader](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/MessageQueue/Topology/Config/Xml/Reader.php) |
| `reports.xml` | [Rapports avancés](https://devdocs.magento.com/guides/v2.4/advanced-reporting/report-xml.html) | global | [\Magento\Analytics\ReportXml\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Analytics/ReportXml/Config.php) |
| `resources.xml` | Définit la ressource de module | global | [\Magento\Framework\App\ResourceConnection\Config\Reader](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/ResourceConnection/Config/Reader.php) |
| `routes.xml` | Configuration [Route](https://developer.adobe.com/commerce/php/development/components/routing/) | area | [Magento\Framework\App\Route\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/Route/Config.php) |
| `sales.xml` | Définit la configuration totale des ventes | global | [\Magento\Sales\Model\Config\Data](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Sales/Model/Config/Data.php) |
| `search_engine.xml` | Fournit la configuration du moteur de recherche | global | [Magento\Search\Model\SearchEngine\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Search/Model/SearchEngine/Config.php) |
| `search_request.xml` | Définit la configuration de la recherche catalogue | global | [\Magento\Framework\Search\Request\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Search/Request/Config.php) |
| `sections.xml` | Définit les actions qui déclenchent l’invalidation du cache pour les blocs de contenu privés. | frontend | [SectionInvalidationConfigReader](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Customer/etc/di.xml#L137-L148) |
| `system.xml` | Définit les options de la page de configuration du système. | adminhtml | [\Magento\Framework\App\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/Config.php) |
| `validation.xml` | Fichier de configuration de validation de module | global | [\Magento\Framework\Validator\Factory](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Validator/Factory.php) |
| `view.xml` | Définit les valeurs de configuration de la vue Vendor_Module | global | [\Magento\Framework\View\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/View/Config.php) |
| `webapi.xml` | [ Configure une API web](https://developer.adobe.com/commerce/php/development/components/web-api/services/) | global | [\Magento\Webapi\Model\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Webapi/Model/Config.php) |
| `webapi_async.xml` | [Définit les itinéraires personnalisés REST](https://developer.adobe.com/commerce/php/development/components/web-api/custom-routes/) | global | [\Magento\WebapiAsync\Model\ServiceConfig](https://github.com/magento/magento2/blob/2.4/app/code/Magento/WebapiAsync/Model/ServiceConfig.php) |
| `widget.xml` | Définit des widgets | global | [\Magento\Widget\Model\Config\Reader](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Widget/Model/Config/Reader.php) |
| `zip_codes.xml` | Définit le format du code postal de chaque pays. | global | [\Magento\Directory\Model\Country\Postcode\Config\Data](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Directory/Model/Country/Postcode/Config/Data.php) |

### Interfaces de configuration

Vous pouvez interagir avec les fichiers de configuration à l’aide d’interfaces sous [Magento\Framework\Config](https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/Config).

Vous pouvez utiliser ces interfaces si vous [créez un type de configuration](../reference/config-create-types.md#create-configuration-types).

`Magento\Framework\Config` fournit les interfaces suivantes :

- [Framework\Config\ConverterInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/ConverterInterface.php), qui convertit le fichier XML en une représentation de tableau en mémoire des configurations.
- [Framework\Config\DataInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/DataInterface.php), qui récupère les données de configuration dans une portée spécifiée.
- [Framework\Config\FileResolverInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/FileResolverInterface.php), qui identifie l&#39;emplacement des fichiers à lire par [Magento\Framework\Config\ReaderInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/ReaderInterface.php).
- [Framework\Config\ReaderInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/ReaderInterface.php), qui lit les données de configuration du stockage et sélectionne le stockage à partir duquel il lit.

En d’autres termes, le système de fichiers, la base de données et les autres espaces de stockage fusionnent les fichiers de configuration selon les règles de fusion et valident les fichiers de configuration avec les schémas de validation.

- [Framework\Config\SchemaLocatorInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/SchemaLocatorInterface.php), qui localise le schéma XSD.
- [Framework\Config\ScopeListInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/ScopeListInterface.php), qui renvoie une liste de portées.
- [Framework\Config\ValidationStateInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/ValidationStateInterface.php), qui récupère l’état de validation.
