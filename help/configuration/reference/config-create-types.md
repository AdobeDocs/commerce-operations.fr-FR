---
title: Types de configuration
description: Créez ou étendez des types de configuration.
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '591'
ht-degree: 0%

---


# Types de configuration

## Étendre les types de configuration

Pour étendre un type de configuration existant, il vous suffit de créer un fichier de configuration dans votre module.

Par exemple, pour ajouter un observateur d’événement, vous créez `app/code/{VendorName}/{ModuleName}/etc/events.xml` et déclarer un nouvel observateur.

Comme le type de configuration d’événement existe dans Commerce, le chargeur et la variable `events.xsd` la validation des schémas est déjà présente et fonctionnelle.

Votre nouveau `events.xml` est automatiquement collecté à partir de votre module et fusionné avec d’autres `events.xml` pour d’autres modules.

## Création de types de configuration

Pour créer un type de configuration, vous devez ajouter au minimum :

- Un chargeur
- Schéma de validation XSD
- Fichiers de configuration XML

Par exemple, pour introduire un adaptateur pour un nouveau serveur de recherche qui permet aux extensions de configurer la manière dont ses entités sont indexées sur ce serveur, créez :

- Un chargeur
- Un fichier de schéma XSD
- Un fichier de configuration correctement nommé. Par exemple : `search.xml`. Ce fichier est lu et validé par rapport à votre schéma.
- Toute autre classe requise pour votre travail.

>[!INFO]
>
>Si de nouveaux modules ont une `search.xml` , ils sont fusionnés avec votre fichier lors de son chargement.

### Exemples d&#39;utilisation

Pour créer un type de configuration :

1. Créez votre fichier XSD.
1. Créez votre fichier XML.
1. Définissez l’objet de configuration dans votre `di.xml`.

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

   - Le noeud de premier type définit le nom de fichier du Reader, associé. `Converter` et `SchemaLocator` classes.
   - Ensuite, la variable `pdfConfigDataStorage` noeud de type virtuel associe la classe Reader à une instance de [Magento\Framework\Config\Data](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/Data.php).
   - Enfin, le noeud de dernier type associe ce type virtuel de données de configuration à la propriété [Magento\Sales\Model\Order\Pdf\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Sales/Model/Order/Pdf/Config.php) , qui est utilisée pour lire réellement des valeurs à partir de ces [pdf.xml](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Sales/etc/pdf.xml) fichiers .

1. Définir un lecteur en étendant [Magento\Framework\Config\Reader\Filesystem](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/Reader/Filesystem.php) et réécrivez les paramètres suivants :

   ```php
   $_idAttributes // Array of node attribute IDs.
   ```

**Exemple :**

```php
<?php
/**
 * Copyright © Magento, Inc. All rights reserved.
 * See COPYING.txt for license details.
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
>Si vous préférez créer votre propre version du lecteur, vous pouvez le faire en implémentant `\Magento\Framework\Config\ReaderInterface`. Voir [Lecteur de configuration Magento_Analytics](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Analytics/ReportXml/Config/Reader.php)

Après avoir défini votre lecteur, utilisez-le pour collecter, fusionner, valider et convertir les fichiers de configuration en une représentation de tableau interne.

## Validation d’un type de configuration

Chaque fichier de configuration est validé par rapport à un schéma spécifique à son type de configuration. Exemple : qui, dans des versions antérieures de Commerce, étaient configurées dans `config.xml`, sont maintenant configurés dans `events.xml`.

Les fichiers de configuration peuvent être validés avant (facultatif) et après toute fusion de plusieurs fichiers affectant le même type de configuration. À moins que les règles de validation des fichiers individuels et fusionnés ne soient identiques, vous devez fournir deux schémas pour valider les fichiers de configuration :

- Schéma de validation d’une personne
- Schéma de validation d’un fichier fusionné

Les nouveaux fichiers de configuration doivent être accompagnés de schémas de validation XSD. Un fichier de configuration XML et son fichier de validation XSD doivent porter le même nom.

Si vous devez utiliser deux fichiers XSD pour un seul fichier XML, les noms des schémas doivent être reconnaissables et associés au fichier XML.
Si vous avez une `events.xml` et un premier fichier `events.xsd` fichier, les fichiers XSD pour la fusion `events.xml` peut être nommé `events_merged.xsd`.
Pour garantir la validation d’un fichier XML par le fichier XSD approprié, vous devez ajouter l’URL (Uniform Resource Name) au fichier XSD dans le fichier XML. Par exemple :

```xml
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:ObjectManager:etc/config.xsd">
```

Votre IDE peut valider vos fichiers de configuration au moment de l’exécution et pendant le développement.
