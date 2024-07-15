---
title: Configuration de la fonction [!DNL Data Migration Tool]
description: Découvrez les deux méthodes de configuration de  [!DNL Data Migration Tool] pour transférer des données entre Magento 1 et Magento 2.
exl-id: 273be997-8085-4488-a455-f6005a85b406
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '808'
ht-degree: 0%

---

# Configurez le [!DNL Data Migration Tool]

Après l’installation de [!DNL Data Migration Tool], le répertoire suivant contient les fichiers de mappage et de configuration :

* MAGENTO OPEN SOURCE :
   * `<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/opensource-to-opensource` : configuration et scripts pour la migration de Magento Open Source 1 vers Magento Open Source 2

* ADOBE COMMERCE :
   * `<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/opensource-to-commerce` : configuration et scripts pour la migration de Magento Open Source 1 vers Adobe Commerce 2
   * `<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/commerce-to-commerce` : configuration et scripts pour la migration d’Adobe Commerce 1 vers Adobe Commerce 2

Les répertoires précédents contiennent des sous-répertoires pour chaque version prise en charge.

## Configuration de la migration

Il existe deux manières de configurer le [!DNL Data Migration Tool] :

* Configurez le [!DNL Data Migration Tool] dans un module distinct (recommandé).
* Modifiez la configuration [!DNL Data Migration Tool] dans le répertoire `<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/`.

Pour utiliser le contrôle de code source afin de gérer votre configuration de migration et l’utiliser pour le déploiement, vous devez créer un module distinct.
Si vous prévoyez d’exécuter [!DNL Data Migration Tool] localement uniquement, vous pouvez modifier directement les fichiers du répertoire `<your Magento 2 install dir>/vendor/magento/data-migration-tool/`.

### Configuration de la migration dans un module distinct

Avant de migrer des données, vous devez créer un module Magento 2.

1. Créez un module Magento 2.

   * `<your Magento 2 install dir>/app/code/Vendor/Migration/composer.json`

   ```json
   {
       "name": "vendor/migration",
       "description": "Providing config for migration",
       "config": {
           "sort-packages": true
       },
       "require": {
           "magento/framework": "*",
           "magento/data-migration-tool": "*"
       },
       "type": "magento2-module",
       "autoload": {
           "files": [
               "registration.php"
           ],
           "psr-4": {
               "Vendor\\Migration\\": ""
           }
       },
       "version": "1.0.0"
   }
   ```

   * `<your Magento 2 install dir>/app/code/Vendor/Migration/registration.php`

   ```php
   <?php
   
   \Magento\Framework\Component\ComponentRegistrar::register(
       \Magento\Framework\Component\ComponentRegistrar::MODULE,
       'Vendor_Migration',
       __DIR__
   );
   ```

   * `<your Magento 2 install dir>/app/code/Vendor/Migration/etc/module.xml`

   ```xml
   <?xml version="1.0"?>
   
   <config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
           xsi:noNamespaceSchemaLocation="urn:magento:framework:Module/etc/module.xsd">
       <module name="Vendor_Migration" setup_version="1.0.0">
           <sequence>
               <module name="Magento_DataMigrationTool"/>
           </sequence>
       </module>
   </config>
   ```

1. Copiez le fichier de configuration `config.xml.dist` du répertoire approprié de [!DNL Data Migration Tool] (`<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/<migration edition>/<ce or version>`) dans le fichier `<your Magento 2 install dir>/app/code/Vendor/Migration/etc/<migration edition>/<ce or version>/config.xml`.

   Par exemple, si vous migrez `Magento 1.9.3.6 Community Edition` vers `Magento 2 Open Source` :

   ```bash
   cd <your Magento 2 install dir>
   ```

   ```bash
   cp vendor/magento/data-migration-tool/etc/opensource-to-opensource/1.9.3.6/config.xml.dist app/code/Vendor/Migration/etc/opensource-to-opensource/1.9.3.6/config.xml
   ```

1. Dans le fichier `config.xml`, vous devez définir les détails d&#39;accès aux bases de données M1 et M2 et à la clé de chiffrement.

1. Si votre boutique M1 comporte des modifications personnalisées, vous devez mapper le reste de vos fichiers de configuration à vos personnalisations de magasin Magento 1. Voir [Utilisation des fichiers de configuration et de mappage](#migration-config).

### Configuration de la migration dans le dossier `vendor`

Avant de migrer des données, vous devez créer un fichier de configuration `config.xml` à partir de l’exemple fourni.

Pour configurer le [!DNL Data Migration Tool] pour la migration :

1. Connectez-vous à votre serveur d’applications en tant que [propriétaire du système de fichiers](../../installation/prerequisites/file-system/overview.md) ou basculez-vous vers cette application.

1. Accédez au répertoire suivant :

   ```bash
   <your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/<migration edition>/<ce or version>
   ```

1. Saisissez la commande suivante pour créer un `config.xml` à partir de l’exemple fourni :

   ```bash
   cp config.xml.dist config.xml
   ```

1. Ouvrez `config.xml` dans un éditeur de texte.

1. Au minimum, le fichier config.xml doit contenir les détails d’accès aux bases de données M1 et M2 et aux clés de chiffrement.

   ```xml
   <source>
      <database host="127.0.0.1" name="magento1" user="root"/>
   </source>
   <destination>
      <database host="127.0.0.1" name="magento2" user="root"/>
   </destination>
   <options>
      <crypt_key />
   </options>
   ```

   La balise &lt;crypt_key> doit contenir une valeur. Vous pouvez le trouver dans la balise `<key>` située dans le fichier app/etc/local.xml de votre instance Magento 1.

   Paramètres facultatifs :

   * Mot de passe utilisateur de la base de données : `password=<password>`
   * Port personnalisé de la base de données : `port=<port>`
   * Préfixe de table : `<source_prefix>`, `<dest_prefix>`

   Par exemple, si le nom d’utilisateur du propriétaire de la base de données est `root` avec le mot de passe `pass` et que vous utilisez le préfixe `magento1` dans la base de données du Magento 1, utilisez ce qui suit dans `config.xml` :

   ```xml
   <source>
      <database host="127.0.0.1" name="magento1" user="root" password="pass"/>
   </source>
   <destination>
      <database host="127.0.0.1" name="magento2" user="root" password="pass"/>
   </destination>
   <options>
      <source_prefix>magento1</source_prefix>
      <crypt_key>f3e25abe619dae2387df9fs594f01985</crypt_key>
   </options>
   ```

Lorsque vous avez terminé, enregistrez vos modifications dans `config.xml` et quittez l’éditeur de texte.

### Connexion à l’aide du protocole TLS

Vous pouvez également vous connecter à une base de données à l’aide du protocole TLS (c’est-à-dire à l’aide de clés cryptographiques publiques/privées). Ajoutez les attributs facultatifs suivants à l’élément `database` :

* `ssl_ca`
* `ssl_cert`
* `ssl_key`

Par exemple :

```xml
<source>
    <database host="localhost" name="magento1" user="root" ssl_ca="/path/to/file" ssl_cert="/path/to/file" ssl_key="/path/to/file"/>
</source>
<destination>
    <database host="localhost" name="magento2" user="root" ssl_ca="/path/to/file" ssl_cert="/path/to/file" ssl_key="/path/to/file"/>
</destination>
```

## Utilisation des fichiers de configuration et de mappage

Le [!DNL Data Migration Tool] utilise des *fichiers de mappage* pour vous permettre d’effectuer un mappage personnalisé de la base de données entre vos bases de données Magento 1 et Magento 2, notamment :

* Modification des noms de table

* Modification des noms de champ

* Ignorer les tableaux ou les champs

* Adapter le transfert des données d&#39;un champ au format Magento 2

Les fichiers de mappage pour les versions de Magento prises en charge se trouvent dans les sous-répertoires de `<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc`

Pour utiliser les fichiers de mappage :

1. Copiez-les de `<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/<migration edition>/<ce or version>/` vers `<your Magento 2 install dir>/app/code/Vendor/Migration/etc/<migration edition>/<ce or version>/` et supprimez l’extension `.dist`.

1. Mettez à jour le chemin d’accès au fichier nouvellement copié dans le noeud `<options>` de `config.xml`. Le chemin d’accès mis à jour doit être l’un des suivants :

   1. Chemin d’accès absolu au fichier, par exemple `/var/www/html/app/code/Vendor/Migration/etc/opensource-to-opensource/1.9.4.1/map.xml`
   1. chemin d’accès relatif au module magento/data-migration-tool : `etc/opensource-to-opensource/1.9.4.1/map.xml`
   1. Chemin d’accès au fichier relatif à la racine du Magento : `app/code/Vendor/Migration/etc/opensource-to-opensource/1.9.4.1/map.xml`

Les répertoires `<Magento 2 dir>/vendor/magento/data-migration-tool/etc` et `<Magento 2 dir>/vendor/magento/data-migration-tool/etc/<ce version>` contiennent les fichiers de configuration suivants :

Même si vous travaillez la plupart du temps avec le fichier `map.xml.dist`, le tableau suivant traite de chaque mappage et d’autres fichiers.

| Mappage du nom de fichier | Description |
| --- | --- |
| `class-map.xml.dist` | Dictionnaire des mappages de classe entre le Magento 1 et le Magento 2 |
| `config.xml.dist` | Fichier de configuration principal qui spécifie les configurations de base de données Magento 1 et Magento 2, la configuration des étapes et les liens vers les fichiers de mappage |
| *Adobe Commerce uniquement*. `customer-attr-document-groups.xml.dist` | Liste des tables utilisées dans l’étape des attributs du client personnalisés. |
| *Adobe Commerce uniquement*. `customer-attr-map.xml.dist` | Fichier de mappage utilisé dans l’étape Attributs du client personnalisés. |
| `deltalog.xml.dist` | Contient la liste des tables requises pour la configuration des routines de base de données. |
| `eav-attribute-groups.xml.dist` | Contient la liste des attributs utilisés à chaque étape. |
| `eav-document-groups.xml.dist` | Contient la liste des tables utilisées à l’étape de l’exécution. |
| `log-document-groups.xml.dist` | Contient la liste des tables utilisées dans l’étape de journal. |
| `map-eav.xml.dist` | Fichier de carte utilisé à l’étape AEM. |
| `map-log.xml.dist` | Fichier de mappage des logs. |
| *Adobe Commerce uniquement*. `map-sales.xml.dist` | Fichier de mappage utilisé dans l’étape de commande des ventes. |
| `map.xml.dist` | Fichier de mappage requis pour l’étape de mappage. |
| `settings.xml.dist` | Définition du fichier de configuration de migration qui spécifie les règles requises pour la migration de la table `core_config_data`. |
| `customer-attribute-groups.xml.dist` | Contient la liste des attributs utilisés dans l’étape Attributs du client. |
| `customer-document-groups.xml.dist` | Contient la liste des tableaux utilisés dans l’étape Attributs du client. |
| `map-customer.xml.dist` | Fichier de mappage utilisé dans l’étape Attributs du client. |
| `order-grids-document-groups.xml.dist` | Contient la liste des tables utilisées dans l’étape OrderGrids. |
| `map-document-groups.xml.dist` | Définit les champs qui sont mis à jour lors des doublons lors de l’insertion de données. |
| `map-stores.xml.dist` | Fichier de mappage utilisé dans l’étape Magasins. |
| `map-tier-price.xml.dist` | Fichier de mappage utilisé dans l’étape de prix de niveau. |
| *Adobe Commerce uniquement*. `visual_merchandiser_map.xml.dist` | Fichier de mappage utilisé dans l’étape VisualMerchandiser. |
| *Adobe Commerce uniquement*. `visual_merchandiser_attribute_groups.xml.dist` | Contient la liste des attributs utilisés dans l’étape VisualMerchandiser. |
| *Adobe Commerce uniquement*. `visual_merchandiser_document_groups.xml.dist` | Contient la liste des tables utilisées dans l’étape VisualMerchandiser. |

Pour plus d’informations, reportez-vous à la [[!DNL Data Migration Tool] Spécification technique](technical-specification.md) .
