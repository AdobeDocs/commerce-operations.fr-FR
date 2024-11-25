---
title: Types de configuration
description: Créez ou étendez des types de configuration.
exl-id: 4390c310-b35a-431a-859f-3fd46d8ba6bf
source-git-commit: 4116d0983edc797ce42d24e711fb5ecdbf8fdec9
workflow-type: tm+mt
source-wordcount: '525'
ht-degree: 0%

---

# Types de configuration

## Étendre les types de configuration

Pour étendre un type de configuration existant, il vous suffit de créer un fichier de configuration dans votre module.

Par exemple, pour ajouter un observateur d’événement, vous créez `app/code/{VendorName}/{ModuleName}/etc/events.xml` et déclarez un nouvel observateur.

Comme le type de configuration d’événement existe dans Commerce, le chargeur et le schéma de validation `events.xsd` sont déjà présents et fonctionnels.

Votre nouveau `events.xml` est automatiquement collecté à partir de votre module et fusionné avec d’autres fichiers `events.xml` pour d’autres modules.

## Création de types de configuration

Pour créer un type de configuration, vous devez ajouter au minimum :

- Un chargeur
- Schéma de validation XSD
- Fichiers de configuration XML

Par exemple, pour introduire un adaptateur pour un nouveau serveur de recherche qui permet aux extensions de configurer la manière dont ses entités sont indexées sur ce serveur, créez :

- Un chargeur
- Un fichier de schéma XSD
- Un fichier de configuration correctement nommé. Par exemple, `search.xml`. Ce fichier est lu et validé par rapport à votre schéma.
- Toute autre classe requise pour votre travail.

>[!INFO]
>
>Si de nouveaux modules ont un fichier `search.xml`, ils sont fusionnés avec votre fichier lors de son chargement.

### Exemples d&#39;utilisation

Pour créer un type de configuration :

1. Créez votre fichier XSD.
1. Créez votre fichier XML.
1. Définissez votre objet de configuration dans votre `di.xml`.

   L’exemple suivant du module Magento_Sales [di.xml](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Sales/etc/di.xml) illustre à quoi un objet de configuration doit ressembler.

   ```xml
   <config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:ObjectManager/etc/config.xsd">
   
       <type name="Magento\Sales\Model\Order\Pdf\Config\Reader">
           <arguments>
               <argument name="fileName" xsi:type="string">pdf.xml</argument>
               <argument name="converter" xsi:type="object">Magento\Sales\Model\Order\Pdf\Config\Converter</argument>
               <argument name="schemaLocator" xsi:type="object">Magento\Sales\Model\Order\Pdf\Config\SchemaLocator</argument>
           </arguments>
       </type>
   
       <virtualType name="pdfConfigDataStorage" type="Magento\Framework\Config\Data">
           <arguments>
               <argument name="reader" xsi:type="object">Magento\Sales\Model\Order\Pdf\Config\Reader</argument>
               <argument name="cacheId" xsi:type="string">sales_pdf_config</argument>
           </arguments>
       </virtualType>
   
       <type name="Magento\Sales\Model\Order\Pdf\Config">
           <arguments>
               <argument name="dataStorage" xsi:type="object">pdfConfigDataStorage</argument>
           </arguments>
       </type>
   </config>
   ```

   - Le premier noeud de type définit le nom de fichier du Reader, les classes `Converter` et `SchemaLocator` associées.
   - Ensuite, le noeud de type virtuel `pdfConfigDataStorage` associe la classe Reader à une instance de [Magento\Framework\Config\Data](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/Data.php).
   - Enfin, le dernier noeud de type associe ce type virtuel de données de configuration à la classe [Magento\Sales\Model\Order\Pdf\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Sales/Model/Order/Pdf/Config.php), qui est utilisée pour lire réellement les valeurs dans à partir de ces fichiers [pdf.xml](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Sales/etc/pdf.xml).

1. Définissez un lecteur en étendant la classe [Magento\Framework\Config\Reader\Filesystem](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/Reader/Filesystem.php) et réécrivez les paramètres suivants :

   ```php
   $_idAttributes // Array of node attribute IDs.
   ```

**Exemple :**

```php
<?php
/**
 * Copyright [first year code created] Adobe
 * All Rights Reserved.
 */

namespace Vendor\ModuleName\Model\Config;

use Magento\Framework\Config\Reader\Filesystem;

class Reader extends Filesystem
{
    /**
     * List of identifier attributes for merging
     *
     * @var array
     */
    protected $_idAttributes = [
         '</path/to/node_in_your_xml_file>'        => '<identifierAttributeName>',
         '</path/to/other/node_in_your_xml_file>'  => '<identifierAttributeName>',
    ];
}
```

>[!INFO]
>
>Si vous préférez créer votre propre version du lecteur, vous pouvez le faire en implémentant `\Magento\Framework\Config\ReaderInterface`. Voir [lecteur de configuration Magento_Analytics](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Analytics/ReportXml/Config/Reader.php)

Après avoir défini votre lecteur, utilisez-le pour collecter, fusionner, valider et convertir les fichiers de configuration en une représentation de tableau interne.

## Validation d’un type de configuration

Chaque fichier de configuration est validé par rapport à un schéma spécifique à son type de configuration. Exemple : les événements, qui, dans des versions précédentes de Commerce, ont été configurés dans `config.xml`, sont désormais configurés dans `events.xml`.

Les fichiers de configuration peuvent être validés avant (facultatif) et après toute fusion de plusieurs fichiers affectant le même type de configuration. À moins que les règles de validation des fichiers individuels et fusionnés ne soient identiques, vous devez fournir deux schémas pour valider les fichiers de configuration :

- Schéma de validation d’une personne
- Schéma de validation d’un fichier fusionné

Les nouveaux fichiers de configuration doivent être accompagnés de schémas de validation XSD. Un fichier de configuration XML et son fichier de validation XSD doivent porter le même nom.

Si vous devez utiliser deux fichiers XSD pour un seul fichier XML, les noms des schémas doivent être reconnaissables et associés au fichier XML.
Si vous disposez d’un fichier `events.xml` et d’un premier fichier `events.xsd`, les fichiers XSD du fichier `events.xml` fusionné peuvent être nommés `events_merged.xsd`.
Pour garantir la validation d’un fichier XML par le fichier XSD approprié, vous devez ajouter l’URL (Uniform Resource Name) au fichier XSD dans le fichier XML. Par exemple :

```xml
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:ObjectManager:etc/config.xsd">
```

Votre IDE peut valider vos fichiers de configuration au moment de l’exécution et pendant le développement.
