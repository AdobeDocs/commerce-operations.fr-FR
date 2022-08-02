---
title: Fichiers de configuration de module
description: Découvrez comment personnaliser un module à l’aide de types de configuration.
source-git-commit: 53448b11a2d000fe8e8a7eecf2ffcef4b7e248fa
workflow-type: tm+mt
source-wordcount: '2019'
ht-degree: 0%

---


# Présentation des fichiers de configuration de module

Les responsabilités de `config.xml` Le fichier de configuration utilisé dans les versions antérieures de Commerce est désormais divisé entre plusieurs fichiers, situés dans différents répertoires de module. Les multiples fichiers de configuration de Commerce se chargent à la demande uniquement lorsqu’un module demande un type de configuration spécifique.

Vous pouvez utiliser ces fichiers, également appelés _types de configuration_: pour personnaliser des aspects spécifiques du comportement de votre module.

Plusieurs modules peuvent déclarer des fichiers de configuration qui affectent le même type de configuration (des événements, par exemple), et ces fichiers de configuration multiples sont fusionnés.

Vous trouverez ci-dessous les termes courants utilisés dans cette rubrique :

- **Objet de configuration**: bibliothèque de commerce ou classe responsable de la définition et de la validation du type de configuration. Par exemple, l’objet de configuration pour `config.xml` is [Magento\Framework\App\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/Config.php).

- **Etape de configuration**: les étapes sont définies comme _Principal_, _global_, et _area_. Chaque étape détermine le moment où le type de configuration est chargé et fusionné avec les types de configuration du même nom. Par exemple : `module.xml` Les fichiers sont fusionnés avec d’autres `module.xml` fichiers .

- **Étendue de la configuration**—Complémentaire aux étapes de configuration, un périmètre définit le modèle de type de configuration. Par exemple : `adminhtml` est une portée de zone chargée avec à l’étape avec d’autres modules `adminhtml` configurations. Pour plus d’informations, voir [Modules et zones](https://devdocs.magento.com/guides/v2.4/architecture/archi_perspectives/components/modules/mod_and_areas.html).

## Chargement et fusion des configurations

Cette section explique comment les fichiers de configuration sont chargés et fusionnés.

### Comment Commerce charge les fichiers de configuration

Commerce charge les fichiers de configuration dans l’ordre suivant (tous les chemins sont relatifs à votre répertoire d’installation Commerce) :

- Configuration Principal ([app/etc/di.xml](https://github.com/magento/magento2/blob/2.4/app/etc/di.xml)). Ce fichier est utilisé pour démarrer Commerce.
- Configurations globales à partir de modules (`<your component base dir>/<vendorname>/<component-type>-<component-name>/etc/*.xml`). Collecte certains fichiers de configuration de tous les modules et les fusionne.
- Configuration spécifique à une zone à partir des modules (`<your component base dir>/<vendorname>/<component-type>-<component-name>/etc/<area>/*.xml`). Collecte des fichiers de configuration de tous les modules et les fusionne dans la configuration globale. Certaines configurations spécifiques à une zone peuvent remplacer ou étendre la configuration globale.

where

- `<your component base dir>` est le répertoire de base dans lequel se trouve votre composant. Les valeurs standard sont les suivantes : `app/code` ou `vendor` par rapport au répertoire d’installation de Commerce.
- `<vendorname>` est le nom du fournisseur du composant ; par exemple, le nom du fournisseur de Commerce est `magento`.
- `<component-type>` est l’un des suivants :

   - `module-`: Une extension ou un module.
   - `theme-`: Thème.
   - `language-`: Package de langue.

>[!INFO]
>
>Actuellement, les thèmes se trouvent sous `<magento_root>/app/design/frontend` ou `<magento_root>/app/design/adminhtml`.

- `<component-name>`: Nom de votre composant tel que défini dans [compositeur.json](https://github.com/magento/magento2/blob/2.4/composer.json).

### Fusion du fichier de configuration

Les noeuds des fichiers de configuration sont fusionnés en fonction de leurs XPath entièrement qualifiés, qui a un attribut spécial défini dans `$idAttributes` tableau déclaré comme identifiant. Cet identifiant doit être unique pour tous les noeuds imbriqués dans le même noeud parent.

Algorithme de fusion d’applications de commerce :

- Si les identifiants de noeud sont égaux (ou si aucun identifiant n’est défini), tout le contenu sous-jacent dans le noeud (attributs, noeuds enfants et contenu scalaire) est remplacé.
- Si les identifiants de noeud ne sont pas égaux, le noeud est un nouvel enfant du noeud parent.
- Si le document d’origine comporte plusieurs noeuds portant le même identifiant, une erreur est déclenchée car les identifiants ne peuvent pas être distingués.

Une fois les fichiers de configuration fusionnés, le document obtenu contient tous les noeuds des fichiers d’origine.

>[!INFO]
>
>Vous pouvez utiliser [\Magento\Framework\Config\Reader\Filesystem](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/Reader/Filesystem.php) classe pour le débogage et la compréhension de la logique derrière [chargeur de fichiers de configuration](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/Reader/Filesystem.php#L125) et [configurations de fusion](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/Reader/Filesystem.php#L144) processus.

## Types, objets et interfaces de configuration

Les sections suivantes fournissent des informations sur les types de configuration, les objets de configuration correspondants et les interfaces que vous pouvez utiliser pour travailler avec les objets :

- [Types et objets de configuration](#config-files-classes-objects)
- [Interfaces de configuration](#config-files-classes-int)

### Types et objets de configuration

Le tableau suivant présente chaque type de configuration et l’objet de configuration Commerce auquel il se rapporte.

| Fichier de configuration | Description | Évaluation | Objet de configuration |
| --- | --- | --- | --- |
| `address_formats.xml` | Déclaration du format d’adresse | Principale, globale | [\Magento\Customer\Model\Address\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Customer/Model/Address/Config.php) |
| `acl.xml` | [Liste de contrôle d’accès](https://devdocs.magento.com/guides/v2.4/get-started/authentication/gs-authentication.html#relationship-between-aclxml-and-webapixml) | global | [\Magento\Framework\Acl\AclResource\Provider](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Acl/AclResource/Provider.php) |
| `analytics.xml` | [Rapports avancés](https://devdocs.magento.com/guides/v2.4/advanced-reporting/data-collection.html) | Principale, globale | [\Magento\Analytics\Model\Config\Reader](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Analytics/Model/Config/Reader.php) |
| `cache.xml` | Déclaration du type de cache | Principale, globale | [\Magento\Framework\Cache\Config\Data](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Cache/Config/Data.php) |
| `catalog_attributes.xml` | Configuration des attributs du catalogue | global | [\Magento\Catalog\Model\Attribute\Config\Data](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Catalog/Model/Attribute/Config/Data.php) |
| `config.php` et `env.php` | [Configuration du déploiement](../reference/deployment-files.md) | Ces fichiers sont lisibles/modifiables par le processeur de configuration interne. | Sans objet, ne peut pas être personnalisé |
| `config.xml` | Configuration du système | Principale, globale | [\Magento\Framework\App\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/Config.php) |
| `communication.xml` | [Définit les aspects du système de file d’attente des messages.](https://devdocs.magento.com/guides/v2.4/extension-dev-guide/message-queues/config-mq.html#communicationxml) | global | [\Magento\WebapiAsync\Code\Generator\Config\RemoteServiceReader\Communication](https://github.com/magento/magento2/blob/2.4/app/code/Magento/WebapiAsync/Code/Generator/Config/RemoteServiceReader/Communication.php) |
| `crontab.xml` | [Configuration des groupes cron](../cron/custom-cron-reference.md#configure-cron-groups) | global | [\Magento\Cron\Model\Config\Data](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Cron/Model/Config/Data.php) |
| `cron_groups.xml` | [Spécifie les options du groupe cron](../cron/custom-cron-reference.md) | global | [\Magento\Cron\Model\Groups\Config\Data](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Cron/Model/Groups/Config/Data.php) |
| `db_schema.xml` | [Schéma déclaratif](https://devdocs.magento.com/guides/v2.4/extension-dev-guide/declarative-schema/db-schema.html) | global | [Magento\Framework\Setup\Declaration\Schema](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Setup/Declaration/Schema/SchemaConfig.php) |
| `di.xml` | [Injection de dépendance](https://devdocs.magento.com/guides/v2.4/extension-dev-guide/depend-inj.html) configuration | Principale, globale, zone | [\Magento\Framework\ObjectManager\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/ObjectManager/Config/Config.php) |
| `eav_attributes.xml` | Fournit la configuration des attributs d’expérience visuelle | global | [\Magento\Eav\Model\Entity\Attribute\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Eav/Model/Entity/Attribute/Config.php) |
| `email_templates.xml` | Configuration des modèles d&#39;email | global | [\Magento\Email\Model\Template\Config\Data](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Email/Model/Template/Config/Data.php) |
| `esconfig.xml` | [Configuration des mots-clés du paramètre régional du moteur de recherche](../search/search-stopwords.md#create-stopwords-for-a-new-locale) | global | [\Magento\Elasticsearch\Model\Adapter\Index\Config\EsConfig](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Elasticsearch/Model/Adapter/Index/Config/EsConfig.php) |
| `events.xml` | Configuration des événements/observateurs | global, zone | [\Magento\Framework\Event](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Event.php) |
| `export.xml` | Exporter la configuration des entités | global | [\Magento\ImportExport\Model\Export\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/ImportExport/Model/Export/Config.php) |
| `extension_attributes.xml` | [Attributs d’extension](https://devdocs.magento.com/guides/v2.4/extension-dev-guide/attributes.html#extension) | global | [\Magento\Framework\Api\ExtensionAttribute\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Api/ExtensionAttribute/Config.php) |
| `fieldset.xml` | Définit les jeux de champs | global | [\Magento\Framework\DataObject\Copy\Config\Reader](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/DataObject/Copy/Config/Reader.php) |
| `indexer.xml` | [Déclarer les indexeurs](https://devdocs.magento.com/guides/v2.4/extension-dev-guide/indexing-custom.html) | global | [\Magento\Framework\Indexer\Config\Reader](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Indexer/Config/Reader.php) |
| `import.xml` | Déclarer les entités d’importation | global | [\Magento\ImportExport\Model\Import\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/ImportExport/Model/Import/Config.php) |
| `menu.xml` | Définit les options de menu pour l’administrateur. | adminhtml | [\Magento\Backend\Model\Menu\Config\Reader](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Backend/Model/Menu/Config/Reader.php) |
| `module.xml` | Définit les données de configuration de module et la dépendance de type Soft. | Principale, globale | [\Magento\Framework\Module\ModuleList\Loader](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Module/ModuleList/Loader.php) |
| `mview.xml` | [Configuration du mode MV](https://devdocs.magento.com/guides/v2.4/extension-dev-guide/indexing-custom.html#mview-configuration) | Principale, globale | [\Magento\Framework\Mview\Config\Data](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Mview/Config/Data.php) |
| `payment.xml` | Configuration du module de paiement | Principale, globale | [\Magento\Payment\Model\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Payment/Model/Config.php) |
| `persistent.xml` | [Magento_Persistent](https://devdocs.magento.com/guides/v2.4/mrg/module-persistent.html) fichier de configuration | global | [\Magento\Persistent\Helper\Data](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Persistent/Helper/Data.php) |
| `pdf.xml` | Paramètres du PDF | global | [\Magento\Sales\Model\Order\Pdf\Config\Reader](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Sales/Model/Order/Pdf/Config/Reader.php) |
| `product_options.xml` | Configuration des options de produit | global | [\Magento\Catalog\Model\ProductOptions\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Catalog/Model/ProductOptions/Config.php) |
| `product_types.xml` | Définit le type de produit | global | [\Magento\Catalog\Model\ProductTypes\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Catalog/Model/ProductTypes/Config.php) |
| `queue_consumer.xml` | [Définit la relation entre une file d’attente existante et son consommateur](https://devdocs.magento.com/guides/v2.4/extension-dev-guide/message-queues/config-mq.html#queueconsumerxml) | global | [\Magento\Framework\MessageQueue\Consumer\Config\Xml\Reader](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/MessageQueue/Consumer/Config/Xml/Reader.php) |
| `queue_publisher.xml` | [Définit l’échange dans lequel une rubrique est publiée.](https://devdocs.magento.com/guides/v2.4/extension-dev-guide/message-queues/config-mq.html#queuepublisherxml) | global | [\Magento\WebapiAsync\Code\Generator\Config\RemoteServiceReader\Publisher](https://github.com/magento/magento2/blob/2.4/app/code/Magento/WebapiAsync/Code/Generator/Config/RemoteServiceReader/Publisher.php) |
| `queue_topology.xml` | [Définit les règles de routage des messages, déclare les files d’attente et les échanges.](https://devdocs.magento.com/guides/v2.4/extension-dev-guide/message-queues/config-mq.html#queuetopologyxml) | global | [\Magento\Framework\MessageQueue\Topology\Config\Xml\Reader](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/MessageQueue/Topology/Config/Xml/Reader.php) |
| `reports.xml` | [Rapports avancés](https://devdocs.magento.com/guides/v2.4/advanced-reporting/report-xml.html) | global | [\Magento\Analytics\ReportXml\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Analytics/ReportXml/Config.php) |
| `resources.xml` | Définit la ressource de module | global | [\Magento\Framework\App\ResourceConnection\Config\Reader](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/ResourceConnection/Config/Reader.php) |
| `routes.xml` | [Route](https://devdocs.magento.com/guides/v2.4/extension-dev-guide/routing.html) configuration | area | [Magento\Framework\App\Route\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/Route/Config.php) |
| `sales.xml` | Définit la configuration totale des ventes | global | [\Magento\Sales\Model\Config\Data](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Sales/Model/Config/Data.php) |
| `search_engine.xml` | Fournit la configuration du moteur de recherche | global | [Magento\Search\Model\SearchEngine\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Search/Model/SearchEngine/Config.php) |
| `search_request.xml` | Définit la configuration de la recherche catalogue | global | [\Magento\Framework\Search\Request\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Search/Request/Config.php) |
| `sections.xml` | Définit les actions qui déclenchent l’invalidation du cache pour les blocs de contenu privés. | frontend | [SectionInvalidationConfigReader](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Customer/etc/di.xml#L137-L148) |
| `system.xml` | Définit les options de la page de configuration du système. | adminhtml | [\Magento\Framework\App\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/Config.php) |
| `validation.xml` | Fichier de configuration de validation de module | global | [\Magento\Framework\Validator\Factory](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Validator/Factory.php) |
| `view.xml` | Définit les valeurs de configuration de la vue Vendor_Module | global | [\Magento\Framework\View\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/View/Config.php) |
| `webapi.xml` | [Configuration d’une API web](https://devdocs.magento.com/guides/v2.4/extension-dev-guide/service-contracts/service-to-web-service.html) | global | [\Magento\Webapi\Model\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Webapi/Model/Config.php) |
| `webapi_async.xml` | [Définit les itinéraires personnalisés REST](https://devdocs.magento.com/guides/v2.4/extension-dev-guide/webapi/custom-routes.html) | global | [\Magento\WebapiAsync\Model\ServiceConfig](https://github.com/magento/magento2/blob/2.4/app/code/Magento/WebapiAsync/Model/ServiceConfig.php) |
| `widget.xml` | Définit des widgets | global | [\Magento\Widget\Model\Config\Reader](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Widget/Model/Config/Reader.php) |
| `zip_codes.xml` | Définit le format du code postal de chaque pays. | global | [\Magento\Directory\Model\Country\Postcode\Config\Data](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Directory/Model/Country/Postcode/Config/Data.php) |

### Interfaces de configuration

Vous pouvez interagir avec les fichiers de configuration à l’aide d’interfaces sous [Magento\Framework\Config](https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/Config).

Vous pouvez utiliser ces interfaces si vous [créer un type de configuration ;](../reference/config-create-types.md#create-configuration-types).

`Magento\Framework\Config` fournit les interfaces suivantes :

- [Framework\Config\ConverterInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/ConverterInterface.php), qui convertit le fichier XML en une représentation de tableau en mémoire des configurations.
- [Framework\Config\DataInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/DataInterface.php), qui récupère les données de configuration dans une portée spécifiée.
- [Framework\Config\FileResolverInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/FileResolverInterface.php), qui identifie l’emplacement des fichiers à lire [Magento\Framework\Config\ReaderInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/ReaderInterface.php).
- [Framework\Config\ReaderInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/ReaderInterface.php), qui lit les données de configuration du stockage et sélectionne le stockage à partir duquel il lit.

En d’autres termes, le système de fichiers, la base de données et les autres espaces de stockage fusionnent les fichiers de configuration selon les règles de fusion et valident les fichiers de configuration avec les schémas de validation.

- [Framework\Config\SchemaLocatorInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/SchemaLocatorInterface.php), qui localise le schéma XSD.
- [Framework\Config\ScopeListInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/ScopeListInterface.php), qui renvoie une liste de portées.
- [Framework\Config\ValidationStateInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/ValidationStateInterface.php), qui récupère l’état de validation.
