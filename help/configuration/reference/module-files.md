---
title: Fichiers de configuration du module
description: Découvrez comment personnaliser des modules à l’aide de types de configuration dans Adobe Commerce. Découvrez les bonnes pratiques en matière de gestion des fichiers de configuration et de personnalisation des modules.
exl-id: 87433c28-8e3d-43d0-b77e-3ff9a680af5f
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '1263'
ht-degree: 0%

---

# Présentation des fichiers de configuration du module

Les responsabilités du fichier de configuration `config.xml` utilisé dans les versions antérieures de Commerce sont désormais réparties entre plusieurs fichiers, situés dans différents répertoires de module. Commerce charge plusieurs fichiers de configuration à la demande uniquement lorsqu’un module demande un type de configuration spécifique.

Vous pouvez utiliser ces fichiers (également appelés _types de configuration_) pour personnaliser des aspects spécifiques du comportement de votre module.

Plusieurs modules peuvent déclarer des fichiers de configuration qui affectent le même type de configuration (par exemple, des événements) et ces plusieurs fichiers de configuration sont fusionnés.

Voici les termes courants utilisés dans cette rubrique :

- **Objet de configuration** : bibliothèque ou classe Commerce chargée de définir et de valider le type de configuration. Par exemple, l’objet de configuration pour `config.xml` est [Magento\Framework\App\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/Config.php).

- **Étape de configuration** : les étapes sont définies comme _principale_, _globale_ et _zone_. Chaque étape détermine à quel moment le type de configuration est chargé et fusionné avec des types de configuration portant le même nom. Par exemple, les fichiers `module.xml` sont fusionnés avec d’autres fichiers `module.xml`.

- **Portée de la configuration** : en complément des étapes de configuration, une portée définit le modèle de type de configuration. Par exemple, `adminhtml` est une étendue de zone qui est chargée avec à l’étape avec les configurations de `adminhtml` d’autres modules. Pour plus d’informations, voir [Modules et zones](https://developer.adobe.com/commerce/php/architecture/modules/areas/).

## Chargement et fusion de la configuration

Cette section explique comment les fichiers de configuration sont chargés et fusionnés.

### Chargement des fichiers de configuration par Commerce

Commerce charge les fichiers de configuration dans l’ordre suivant (tous les chemins d’accès sont relatifs à votre répertoire d’installation Commerce) :

- Configuration du Principal ([app/etc/di.xml](https://github.com/magento/magento2/blob/2.4/app/etc/di.xml)). Ce fichier est utilisé pour amorcer Commerce.
- Configurations globales des modules (`<your component base dir>/<vendorname>/<component-type>-<component-name>/etc/*.xml`). Collecte certains fichiers de configuration de tous les modules et les fusionne.
- Configuration spécifique à une zone à partir des modules (`<your component base dir>/<vendorname>/<component-type>-<component-name>/etc/<area>/*.xml`). Collecte les fichiers de configuration de tous les modules et les fusionne dans la configuration globale. Certaines configurations spécifiques à une zone peuvent remplacer ou étendre la configuration globale.

où

- `<your component base dir>` est le répertoire de base dans lequel se trouve votre composant. Les valeurs standard sont `app/code` ou `vendor` par rapport au répertoire d’installation de Commerce.
- `<vendorname>` est le nom du fournisseur du composant ; par exemple, le nom du fournisseur du Commerce est `magento`.
- `<component-type>` est l’un des éléments suivants :

   - `module-` : une extension ou un module.
   - `theme-` : thème.
   - `language-` : package de langue.

>[!INFO]
>
>Actuellement, les thèmes sont situés sous `<magento_root>/app/design/frontend` ou `<magento_root>/app/design/adminhtml`.

- `<component-name>` : nom de votre composant tel que défini dans [composer.json](https://github.com/magento/magento2/blob/2.4/composer.json).

### Fusion du fichier de configuration

Les nœuds dans les fichiers de configuration sont fusionnés en fonction de leurs XPaths complets, qui possèdent un attribut spécial défini dans `$idAttributes` tableau déclaré comme identifiant. Cet identifiant doit être unique pour tous les nœuds imbriqués sous le même nœud parent.

Algorithme de fusion des applications Commerce :

- Si les identifiants de nœud sont égaux (ou s’il n’existe aucun identifiant défini), tout le contenu sous-jacent dans le nœud (attributs, nœuds enfants et contenu scalaire) est remplacé.
- Si les identifiants de nœud ne sont pas égaux, le nœud est un nouveau enfant du nœud parent.
- Si le document d’origine comporte plusieurs nœuds avec le même identifiant, une erreur est déclenchée, car les identifiants ne peuvent pas être distingués.

Une fois les fichiers de configuration fusionnés, le document obtenu contient tous les nœuds des fichiers d’origine.

>[!INFO]
>
>Vous pouvez utiliser la classe [\Magento\Framework\Config\Reader\Filesystem](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/Reader/Filesystem.php) pour déboguer et comprendre la logique derrière le processus [chargeur de fichiers de configuration](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/Reader/Filesystem.php#L125) et [fusion de configurations](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/Reader/Filesystem.php#L144).

## Types de configuration, objets et interfaces

Les sections suivantes fournissent des informations sur les types de configuration, les objets de configuration correspondants et les interfaces que vous pouvez utiliser pour travailler avec les objets :

### Types de configuration et objets

Le tableau ci-dessous présente chaque type de configuration et l’objet de configuration Commerce auquel il se rapporte.

| Fichier de configuration | Description | Étape | Objet Configuration |
| --- | --- | --- | --- |
| `address_formats.xml` | Déclaration du format de l’adresse | principal, global | [\Magento\Customer\Model\Address\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Customer/Model/Address/Config.php) |
| `acl.xml` | [&#x200B; Liste de contrôle d’accès &#x200B;](https://developer.adobe.com/commerce/webapi/get-started/authentication/#relationship-between-aclxml-and-webapixml) | global | [\Magento\Framework\Acl\AclResource\Provider](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Acl/AclResource/Provider.php) |
| `analytics.xml` | [Rapports avancés](https://developer.adobe.com/commerce/php/development/advanced-reporting/data-collection/) | principal, global | [\Magento\Analytics\Model\Config\Reader](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Analytics/Model/Config/Reader.php) |
| `cache.xml` | Déclaration de type de cache | principal, global | [\Magento\Framework\Cache\Config\Data](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Cache/Config/Data.php) |
| `catalog_attributes.xml` | Configuration des attributs de catalogue | global | [\Magento\Catalog\Model\Attribute\Config\Data](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Catalog/Model/Attribute/Config/Data.php) |
| `config.php` et `env.php` | [Configuration du déploiement](../reference/deployment-files.md) | Ces fichiers sont lisibles/inscriptibles par le processeur de configuration interne. | N’a aucun objet, ne peut pas être personnalisé |
| `config.xml` | Configuration du système | principal, global | [\Magento\Framework\App\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/Config.php) |
| `communication.xml` | [Définit les aspects du système de file d’attente des messages](https://developer.adobe.com/commerce/php/development/components/message-queues/configuration/#communicationxml) | global | [\Magento\WebapiAsync\Code\Generator\Config\RemoteServiceReader\Communication](https://github.com/magento/magento2/blob/2.4/app/code/Magento/WebapiAsync/Code/Generator/Config/RemoteServiceReader/Communication.php) |
| `crontab.xml` | [Configure les groupes cron](../cron/custom-cron-reference.md#configure-cron-groups) | global | [\Magento\Cron\Model\Config\Data](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Cron/Model/Config/Data.php) |
| `cron_groups.xml` | [Spécifie les options du groupe cron](../cron/custom-cron-reference.md) | global | [\Magento\Cron\Model\Groups\Config\Data](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Cron/Model/Groups/Config/Data.php) |
| `db_schema.xml` | [Schéma déclaratif](https://developer.adobe.com/commerce/php/development/components/declarative-schema/configuration/) | global | [Magento\Framework\Setup\Declaration\Schema](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Setup/Declaration/Schema/SchemaConfig.php) |
| `di.xml` | [Injection de dépendance](https://developer.adobe.com/commerce/php/development/components/dependency-injection/) configuration | principal, global, area | [\Magento\Framework\ObjectManager\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/ObjectManager/Config/Config.php) |
| `eav_attributes.xml` | Fournit la configuration des attributs EAV | global | [\Magento\Eav\Model\Entity\Attribute\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Eav/Model/Entity/Attribute/Config.php) |
| `email_templates.xml` | Configuration des modèles d’e-mail | global | [\Magento\Email\Model\Template\Config\Data](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Email/Model/Template/Config/Data.php) |
| `esconfig.xml` | [Configuration des mots vides du paramètre régional du moteur de recherche](../search/search-stopwords.md#create-stopwords-for-a-new-locale) | global | [\Magento\Elasticsearch\Model\Adapter\Index\Config\EsConfig](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Elasticsearch/Model/Adapter/Index/Config/EsConfig.php) |
| `events.xml` | Configuration d’événement/observateur | global, area | [\Magento\Framework\Event](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Event.php) |
| `export.xml` | Exporter la configuration des entités | global | [\Magento\ImportExport\Model\Export\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/ImportExport/Model/Export/Config.php) |
| `extension_attributes.xml` | [&#x200B; Attributs d’extension &#x200B;](https://developer.adobe.com/commerce/php/development/components/attributes/#extension-attributes) | global | [\Magento\Framework\Api\ExtensionAttribute\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Api/ExtensionAttribute/Config.php) |
| `fieldset.xml` | Définit des jeux de champs | global | [\Magento\Framework\DataObject\Copy\Config\Reader](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/DataObject/Copy/Config/Reader.php) |
| `indexer.xml` | [déclare les indexeurs](https://developer.adobe.com/commerce/php/development/components/indexing/custom-indexer/) | global | [\Magento\Framework\Indexer\Config\Reader](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Indexer/Config/Reader.php) |
| `import.xml` | Déclare les entités d&#39;import | global | [\Magento\ImportExport\Model\Import\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/ImportExport/Model/Import/Config.php) |
| `menu.xml` | Définit les éléments de menu pour l’administrateur | adminhtml | [\Magento\Backend\Model\Menu\Config\Reader](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Backend/Model/Menu/Config/Reader.php) |
| `module.xml` | Définit les données de configuration du module et la dépendance conditionnelle | principal, global | [\Magento\Framework\Module\ModuleList\Loader](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Module/ModuleList/Loader.php) |
| `mview.xml` | [Configuration de MView](https://developer.adobe.com/commerce/php/development/components/indexing/custom-indexer/#mview-configuration) | principal, global | [\Magento\Framework\Mview\Config\Data](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Mview/Config/Data.php) |
| `payment.xml` | Configuration du module de paiement | principal, global | [\Magento\Payment\Model\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Payment/Model/Config.php) |
| `persistent.xml` | Fichier de configuration [Magento_Persistent](https://developer.adobe.com/commerce/php/module-reference/module-persistent/) | global | [\Magento\Persistent\Helper\Data](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Persistent/Helper/Data.php) |
| `pdf.xml` | Paramètres de PDF | global | [\Magento\Sales\Model\Order\Pdf\Config\Reader](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Sales/Model/Order/Pdf/Config/Reader.php) |
| `product_options.xml` | Fournit la configuration des options de produit | global | [\Magento\Catalog\Model\ProductOptions\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Catalog/Model/ProductOptions/Config.php) |
| `product_types.xml` | Définit le type de produit | global | [\Magento\Catalog\Model\ProductTypes\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Catalog/Model/ProductTypes/Config.php) |
| `queue_consumer.xml` | [&#x200B; Définit la relation entre une file d’attente existante et son client](https://developer.adobe.com/commerce/php/development/components/message-queues/configuration/#queue_consumerxml) | global | [\Magento\Framework\MessageQueue\Consumer\Config\Xml\Reader](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/MessageQueue/Consumer/Config/Xml/Reader.php) |
| `queue_publisher.xml` | [Définit l’échange où une rubrique est publiée.](https://developer.adobe.com/commerce/php/development/components/message-queues/configuration/#queue_publisherxml) | global | [\Magento\WebapiAsync\Code\Generator\Config\RemoteServiceReader\Publisher](https://github.com/magento/magento2/blob/2.4/app/code/Magento/WebapiAsync/Code/Generator/Config/RemoteServiceReader/Publisher.php) |
| `queue_topology.xml` | [&#x200B; Définit les règles de routage des messages, déclare les files d&#39;attente et les échanges](https://developer.adobe.com/commerce/php/development/components/message-queues/configuration/#queue_topologyxml) | global | [\Magento\Framework\MessageQueue\Topology\Config\Xml\Reader](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/MessageQueue/Topology/Config/Xml/Reader.php) |
| `reports.xml` | [Rapports avancés](https://developer.adobe.com/commerce/php/development/advanced-reporting/report-xml/) | global | [\Magento\Analytics\ReportXml\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Analytics/ReportXml/Config.php) |
| `resources.xml` | Définit la ressource du module | global | [\Magento\Framework\App\ResourceConnection\Config\Reader](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/ResourceConnection/Config/Reader.php) |
| `routes.xml` | Configuration [Route](https://developer.adobe.com/commerce/php/development/components/routing/) | zone | [Magento\Framework\App\Route\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/Route/Config.php) |
| `sales.xml` | Définit la configuration du total des ventes | global | [\Magento\Sales\Model\Config\Data](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Sales/Model/Config/Data.php) |
| `search_engine.xml` | Fournit la configuration du moteur de recherche | global | [Magento\Search\Model\SearchEngine\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Search/Model/SearchEngine/Config.php) |
| `search_request.xml` | Définit la configuration de la recherche catalogue | global | [\Magento\Framework\Search\Request\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Search/Request/Config.php) |
| `sections.xml` | Définit des actions qui déclenchent l’invalidation du cache pour les blocs de contenu privés | front-end | [SectionInvalidationConfigReader](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Customer/etc/di.xml#L137-L148) |
| `system.xml` | Définit les options de la page de configuration du système | adminhtml | [\Magento\Framework\App\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/Config.php) |
| `validation.xml` | Fichier de configuration de validation du module | global | [\Magento\Framework\Validator\Factory](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Validator/Factory.php) |
| `view.xml` | Définit les valeurs de configuration de la vue Vendor_Module | global | [\Magento\Framework\View\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/View/Config.php) |
| `webapi.xml` | [Configure une API web](https://developer.adobe.com/commerce/php/development/components/web-api/services/) | global | [\Magento\Webapi\Model\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Webapi/Model/Config.php) |
| `webapi_async.xml` | [Définit les itinéraires personnalisés REST](https://developer.adobe.com/commerce/php/development/components/web-api/custom-routes/) | global | [\Magento\WebapiAsync\Model\ServiceConfig](https://github.com/magento/magento2/blob/2.4/app/code/Magento/WebapiAsync/Model/ServiceConfig.php) |
| `widget.xml` | Définit des widgets | global | [\Magento\Widget\Model\Config\Reader](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Widget/Model/Config/Reader.php) |
| `zip_codes.xml` | Définit le format du code postal de chaque pays | global | [\Magento\Directory\Model\Country\Postcode\Config\Data](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Directory/Model/Country/Postcode/Config/Data.php) |

### Interfaces de configuration

Vous pouvez interagir avec les fichiers de configuration à l’aide des interfaces sous [Magento\Framework\Config](https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/Config).

Vous pouvez utiliser ces interfaces si vous [créez un type de configuration](../reference/config-create-types.md#create-configuration-types).

`Magento\Framework\Config` fournit les interfaces suivantes :

- [Framework\Config\ConverterInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/ConverterInterface.php), qui convertit le code XML en une représentation de tableau en mémoire des configurations.
- [Framework\Config\DataInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/DataInterface.php), qui récupère les données de configuration dans une portée spécifiée.
- [Framework\Config\FileResolverInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/FileResolverInterface.php), qui identifie l&#39;emplacement des fichiers à lire par [Magento\Framework\Config\ReaderInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/ReaderInterface.php).
- [Framework\Config\ReaderInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/ReaderInterface.php), qui lit les données de configuration du stockage et sélectionne le stockage à partir duquel il lit.

En d’autres termes, le système de fichiers, la base de données et d’autres solutions de stockage fusionnent les fichiers de configuration en fonction des règles de fusion et valident les fichiers de configuration avec les schémas de validation.

- [Framework\Config\SchemaLocatorInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/SchemaLocatorInterface.php), qui localise le schéma XSD.
- [Framework\Config\ScopeListInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/ScopeListInterface.php), qui renvoie une liste de portées.
- [Framework\Config\ValidationStateInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/ValidationStateInterface.php), qui récupère l’état de validation.
