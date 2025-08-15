---
title: spécification technique [!DNL Data Migration Tool]
description: Découvrez les détails d’implémentation de et comment optimiser l’extension lors  [!DNL Data Migration Tool]  transfert de données entre Magento 1 et Magento 2.
exl-id: fec3ac3a-dd67-4533-a29f-db917f54d606
topic: Commerce, Migration
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '2098'
ht-degree: 0%

---

# spécification technique [!DNL Data Migration Tool]

Cette section décrit [!DNL Data Migration Tool] détails d’implémentation et comment étendre ses fonctionnalités.

## Référentiels

Pour accéder au code source [!DNL Data Migration Tool], voir la section GitHub [référentiel](https://github.com/magento/data-migration-tool).

## Configuration requise

La [configuration requise](../../installation/system-requirements.md) pour le [!DNL Data Migration Tool] est la même que pour Magento 2.

## Structure interne

### Structure de répertoires

Le diagramme suivant représente la structure des répertoires de [!DNL Data Migration Tool] :

```
├── etc                                    --- all configuration files
│   ├── opensource-to-opensource            --- configuration files for migration from Magento Open Source 1 to Magento Open Source 2
│   │   ├── 1.9.1.1
│   │   │   ├── config.xml.dist
│   │   │   └── map.xml.dist
│   │   ├── 1.9.2.0
│   │   │   ├── config.xml.dist
│   │   │   └── map.xml.dist
│   │   ├── ........
│   │   ├── class-map.xml.dist
│   │   ├── deltalog.xml.dist
│   │   └── settings.xml.dist
│   │   ├── ........
│   ├── opensource-to-commerce              --- configuration files for migration from Magento Open Source 1 to Adobe Commerce 2
│   ├── commerce-to-commerce                --- configuration files for migration from Adobe Commerce 1 to Adobe Commerce 2
│   ├── class-map.xsd
│   ├── config.xsd
│   ├── map.xsd
│   └── settings.xsd
├── src
│   └── Migration
│       ├── App                             --- application framework
│       ├── Console
│       ├── Handler                         --- handlers are used by map files
│       │   ├── AbstractHandler.php
│       │   ├── AddPrefix.php
│       │   ├── ConvertIp.php
│       │   ├── ........
│       ├── Logger
│       ├── Reader
│       ├── Mode
│       │   ├── AbstractMode.php
│       │   ├── Data.php
│       │   ├── Delta.php
│       │   └── Settings.php
│       ├── ResourceModel                   --- contains adapter for connection to data storage and classes to work with structured data
│       │   ├── Adapter
│       │   │   └── Mysql.php
│       │   ├── AbstractCollection.php
│       │   ├── AbstractResource.php
│       │   ├── AdapterInterface.php
│       │   ├── Destination.php
│       │   ├── Document.php
│       │   ├── Record.php
│       │   ├── Source.php
│       │   └── Structure.php
│       ├── Config.php
│       ├── Exception.php
│       └── Step                            --- functionality for migrating specific data
│           ├── Eav
│           │   ├── Data.php
│           │   ├── Helper.php
│           │   ├── InitialData.php
│           │   ├── Integrity.php
│           │   └── Volume.php
│           ├── Map
│           │   ├── Data.php
│           │   ├── Delta.php
│           │   ├── Helper.php
│           │   ├── Integrity.php
│           │   └── Volume.php
│           ├── UrlRewrite
│           │   ├── Version11300to2000.php
│           │   ├── Version11410to2000.php
│           │   └── Version191to2000.php
│           ├── ..........
└── tests
    ├── integration
    ├── static
    └── unit
```

## Point D&#39;Entrée

Le script qui exécute le processus de migration se trouve à l’emplacement suivant : `magento-root/bin/magento`.

## Configuration

Le schéma du fichier de `config.xsd` de configuration se trouve dans le répertoire `etc/` . Le fichier de configuration par défaut (`config.xml.dist`) est créé pour chaque version de Magento 1.x. Il se trouve dans un répertoire distinct sous `etc/`.

Le fichier de configuration par défaut peut être remplacé par un fichier personnalisé (voir [syntaxe de commande](migrate-data/overview.md#command-syntax)).

Le fichier de configuration présente la structure suivante :

```xml
<config xmlns:xs="http://www.w3.org/2001/XMLSchema-instance" xs:noNamespaceSchemaLocation="config.xsd">
    <steps mode="settings">
        <step title="Settings step">
            <integrity>Migration\Step\Settings</integrity>
            <data>Migration\Step\Settings</data>
        </step>
    </steps>
    <steps mode="data">
        <step title="Map step">
            <integrity>Migration\Step\Map\Integrity</integrity>
            <data>Migration\Step\Map\Data</data>
            <volume>Migration\Step\Map\Volume</volume>
        </step>
        ...
    </steps>
    <steps mode="delta">
        <step title="Map step">
            <delta>Migration\Step\Map\Delta</delta>
            <volume>Migration\Step\Map\Volume</volume>
        </step>
        ...
    </steps>
    <source>
        <database host="localhost" name="magento1" user="root" password=""/>
    </source>
    <destination>
        <database host="localhost" name="magento2" user="root" password=""/>
    </destination>
    <options>
        <map_file>map-file.xml</map_file>
        <settings_map_file>settings-map-file.xml</settings_map_file>
        <bulk_size>100</bulk_size>
        <custom_option>custom_option_value</custom_option>
        <source_prefix />
        <dest_prefix />
        ...
    </options>
</config>
```

* étapes : décrit toutes les étapes traitées lors de la migration

* source : configuration de la source de données. Types de sources disponibles : base de données

* destination : configuration pour la destination des données. Types de destination disponibles : base de données

* options - liste des paramètres. Contient des paramètres obligatoires (map_file, settings_map_file, bulk_size) et facultatifs (custom_option, resource_adapter_class_name, prefix_source, prefix_dest, log_file)

Modifiez l’option de préfixe au cas où Magento aurait été installé avec le préfixe dans les tables de la base de données. Elle peut être définie pour les bases de données Magento 1 et Magento 2. Utilisez les options de configuration « source_prefix » et « dest_prefix » en conséquence.

Les données de configuration sont accessibles avec la classe `\Migration\Config`.

## Étapes des opérations disponibles

| Document | Champ |
|---|---|
| `step` | Nœud de deuxième niveau à l’intérieur du nœud Étapes. La description de l’étape concernée doit être spécifiée dans l’attribut `title`. |
| `integrity` | Spécifie la classe PHP responsable de la vérification d&#39;intégrité. Compare les noms, types et autres informations des champs de la table afin de vérifier la compatibilité entre les structures de données Magento 1 et 2. |
| `data` | Spécifie la classe PHP responsable de la vérification des données. Transfère les données, tableau par tableau, de Magento 1 vers Magento 2. |
| `volume` | Spécifie la classe PHP responsable de la vérification du volume. Compare le nombre d&#39;enregistrements entre les tables pour vérifier que le transfert a réussi. |
| `delta` | Spécifie la classe PHP responsable de la vérification delta. Transfère le delta de Magento 1 vers Magento 2 après la migration complète des données. |

## Attributs d’informations de base de données Source

| Document | Champ | Obligatoire ? |
|---|---|---|
| `name` | Nom de base de données du serveur Magento 1. | oui |
| `host` | Adresse IP de l’hôte du serveur Magento 1. | oui |
| `port` | Numéro de port du serveur Magento 1. | non |
| `user` | Nom d’utilisateur du serveur de la base de données Magento 1. | oui |
| `password` | Mot de passe du serveur de la base de données Magento 1. | oui |
| `ssl_ca` | Chemin d’accès au fichier d’autorité de certification SSL. | non |
| `ssl_cert` | Chemin d’accès au fichier de certificat SSL. | non |
| `ssl_key` | Chemin d’accès au fichier de clé SSL. | non |

## Attributs d’informations sur la base de données de destination

| Document | Champ | Obligatoire ? |
|---|---|---|
| `name` | Nom de base de données du serveur Magento 2. | oui |
| `host` | Adresse IP de l’hôte du serveur Magento 2. | oui |
| `port` | Numéro de port du serveur Magento 2. | non |
| `user` | Nom d’utilisateur du serveur de la base de données Magento 2. | oui |
| `password` | Mot de passe du serveur de la base de données Magento 2. | oui |
| `ssl_ca` | Chemin d’accès au fichier d’autorité de certification SSL. | non |
| `ssl_cert` | Chemin d’accès au fichier de certificat SSL. | non |
| `ssl_key` | Chemin d’accès au fichier de clé SSL. | non |

## Se connecter en utilisant le protocole TLS

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

## Internes des étapes

Le processus de migration se compose d’étapes.

L’étape est une unité qui fournit les fonctionnalités requises pour la migration de certaines données séparées. L’étape peut se composer d’une ou de plusieurs étapes (contrôle d’intégrité, contrôle des données, contrôle du volume et delta).

Par défaut, il existe plusieurs étapes ([Map](#map-step), [EAV](#eav), [URL Rewrites](#url-rewrite-step), etc.). Vous pouvez également ajouter vos propres étapes.

Les classes associées aux étapes se trouvent dans le répertoire src/Migration/Step.

Pour exécuter une classe d’étape, la classe doit être définie dans le fichier config.xml.

```xml
<config xmlns:xs="http://www.w3.org/2001/XMLSchema-instance" xs:noNamespaceSchemaLocation="config.xsd">
    <steps mode="mode_name">
        <step title="Step Name">
            <integrity>Migration\Step\StepName\Integrity</integrity>  <!-- integrity check stage of the step -->
            <data>Migration\Step\StepName\Data</data>
            <volume>Migration\Step\StepName\Volume</volume>
        </step>
        ...
    </steps>
    ...
</config>
```

Chaque classe d’étape doit implémenter StageInterface.

```php
class StageClass implements StageInterface
{
  /**
   * Perform the stage
   *
   * @return bool
   */
  public function perform()
  {
  }
}
```

Si l’étape de données prend en charge la restauration, elle doit implémenter l’interface `RollbackInterface`.

La visualisation de l’étape en cours d’exécution est fournie par le composant ProgressBar de Symfony (voir [Barre de progression](https://symfony.com/doc/current/components/console/helpers/progressbar.html)). Accédez à ce composant dans une étape en tant que LogLevelProcessor.

Les principales méthodes d’utilisation sont les suivantes :

```xml
$this->progress->start();
$this->progress->advance();
$this->progress->finish();
```

## Étapes

### Vérification de l&#39;intégrité

Chaque étape doit vérifier que la structure de la source de données (Magento 1 par défaut) et la structure de la destination des données (Magento 2) sont compatibles. Si ce n’est pas le cas, une erreur s’affiche avec les entités non compatibles. Si des champs ont des types de données différents (le même champ a un type de données décimal dans Magento 1 et un entier dans Magento 2), un message d’avertissement s’affiche (sauf lorsqu’il a été couvert dans le fichier de mappage).

### Transfert de données

Si la vérification d’intégrité est réussie, le transfert de données est en cours. Si des erreurs apparaissent, la restauration s’exécute pour revenir à l’état précédent de Magento 2. Si une classe d’étape implémente l’interface `RollbackInterface`, la méthode de restauration s’exécute en cas d’erreur.

### Vérification du volume

Une fois les données migrées, la Vérification du volume permet de vérifier que toutes les données ont été correctement transférées.

### Diffusion Delta

La fonctionnalité Delta assure la diffusion du reste des données ajoutées après la migration principale.

## Modes d’exécution

L’outil doit être exécuté dans trois modes différents, dans un ordre particulier :

1. paramètres - migration des paramètres système
1. données - migration principale des données
1. delta : migration du reste des données ajoutées après la migration principale.

Chaque mode possède sa propre liste d’étapes à exécuter. Voir config.xml

### Mode de migration des paramètres

Le mode de migration des paramètres de cet outil est utilisé pour transférer les entités suivantes :

1. Sites web, boutiques, affichages de boutique.
1. Configuration des magasins (principalement Magasins->Configuration dans M2 ou Système->Configuration dans M1)

Toutes les configurations de magasin conservent leurs données dans la table core_config_data de la base de données. le fichier settings.xml contient les règles de cette table qui sont appliquées pendant le processus de migration. Ce fichier décrit les paramètres qui doivent être ignorés, renommés ou dont les valeurs doivent être modifiées. Le fichier settings.xml présente la structure suivante :

```xml
<?xml version="1.0" encoding="UTF-8"?>
<settings xmlns:xs="http://www.w3.org/2001/XMLSchema-instance" xs:noNamespaceSchemaLocation="settings.xsd">
    <key>
        <ignore>
            <path>path/to/ignore*</path>
        </ignore>
        <rename>
            <path>path/to/rename</path>
            <to>new/path/renamed</to>
        </rename>
    <key>
    <value>
        <transform>
            <path>some/key/to/change</path>
            <handler class="Some\Handler\Class"/>
        </transform>
    </value>
</settings>
```

Sous le nœud `<key>` se trouvent des règles qui fonctionnent avec la colonne « path » du tableau `core_config_data`. `<ignore>` règles empêchent l’outil de transférer certains paramètres. Vous pouvez utiliser des caractères génériques dans ce nœud. Tous les autres paramètres non répertoriés dans le nœud `<ignore>` sont migrés. Si le chemin d’accès à un paramètre a été modifié dans Magento 2, il doit être ajouté `//key/rename` nœud , où l’ancien chemin d’accès indique dans `//key/rename/path` nœud et le nouveau chemin d’accès indique dans `//key/rename/to` nœud .

Sous le nœud `<value>`, des règles fonctionnent avec la colonne « value » du tableau `core_config_data`. Ces règles visent à transformer la valeur des paramètres par des gestionnaires (classes qui implémentent `Migration\Handler\HandlerInterface`) et à l’adapter à Magento 2.

### Mode de migration des données

Dans ce mode, la plupart des données sont migrées. Avant la migration des données, les étapes de vérification de l’intégrité s’exécutent pour chaque étape. Si la vérification d’intégrité réussit, le [!DNL Data Migration Tool] installe les tables du deltalog (avec le préfixe `m2_cl_*`) et les déclencheurs correspondants dans la base de données Magento 1 et exécute l’étape de migration des données des étapes. Lorsque la migration est terminée sans erreur, le contrôle du volume vérifie la cohérence des données. Un message d’avertissement peut s’afficher si vous migrez le magasin dynamique. Ne vous inquiétez pas, la migration delta prend en charge ces données incrémentielles. Les étapes de migration les plus importantes sont Map, URL Rewrite et EAV.

#### Étape de mappage

L’étape de mappage est chargée de transférer la plupart des données de Magento 1 vers Magento 2. Cette étape lit les instructions du fichier map.xml (situé dans le répertoire `etc/`). Le fichier décrit les différences entre les structures de données de la source (Magento 1) et de la destination (Magento 2). Si Magento 1 contient des tables ou des champs qui appartiennent à une extension qui n’existe pas dans Magento 2, ces entités peuvent être placées ici pour les ignorer par l’étape de mappage. Sinon, elle affiche un message d’erreur.

Le fichier de mappage présente le format suivant :

```xml
<?xml version="1.0" encoding="UTF-8"?>
<map xmlns:xs="http://www.w3.org/2001/XMLSchema-instance" xs:noNamespaceSchemaLocation="map.xsd">
    <source>
        <document_rules>
            <ignore>
                <document>some_document2</document>
            </ignore>
            <rename>
                <document>some_document</document>
                <to>some_dest_document</to>
            </rename>
            <log_changes>
                <document key="primary_key">some_dest_document</document>
            </log_changes>
        </document_rules>

        <field_rules>
            <move>
                <field>some_document1.field1</field>
                <to>some_document1.field2</to>
            </move>
            <ignore>
                <field>some_document3.field8</field>
            </ignore>
            <transform>
                <field>some_document1.field1</field>
                <handler class="\Migration\Handler\Convert">
                    <param name="map" value="[value1:value2;value3:value4;value5:value6;]" />
                </handler>
            </transform>
        </field_rules>
    </source>
    <destination>
        <document_rules>
            <ignore>
                <document>some_document8</document>
            </ignore>
        </document_rules>

        <field_rules>
            <transform>
                <field>some_document5.field3</field>
                <handler class="\Migration\Handler\SetValue">
                    <param name="value" value="10" />
                </handler>
            </transform>
        </field_rules>
    </destination>
</map>
```

Domaines :

* *source* - contient les règles de la base de données source

* *destination* - contient les règles de la base de données de destination

Options :

* *ignorer* - le document, le champ ou le type de données marqué avec cette option est ignoré

* *rename* - décrit les relations de nom entre les documents portant un nom différent. Si le nom du document de destination n’est pas le même que celui du document source, vous pouvez utiliser l’option renommer pour définir un nom de document source similaire au nom de la table de destination

* *move* - définit la règle pour déplacer le champ spécifié du document source vers le document de destination. REMARQUE : le nom du document de destination doit être identique au nom du document source. Si les noms des documents source et de destination sont différents - vous devez utiliser l&#39;option Renommer pour le document qui contient un champ déplacé

* *transform* - est une option qui permet à l’utilisateur de migrer des champs en fonction du comportement décrit dans les gestionnaires

* *handler* - Décrit le comportement de transformation des champs. Pour appeler le gestionnaire, vous devez spécifier un nom de classe de gestionnaire dans une balise `<handler>`. Utilisez la balise `<param>` avec le nom du paramètre et les données de valeur pour les transmettre au gestionnaire .

**Source** opérations disponibles :

| Document | Champ |
|--- |--- |
| ignorer le changement de nom | ignorer la transformation de déplacement |

**Destination** opérations disponibles :

| Document | Champ |
|--- |--- |
| ignorer | ignorer la transformation |

#### Caractères génériques

Pour ignorer les documents comportant des parties similaires (`document_name_1`, `document_name_2`), vous pouvez utiliser la fonctionnalité de caractères génériques. Insérez `*` symbole au lieu de répéter la partie (`document_name_*`) et ce masque couvre tous les documents source ou de destination qui répondent à ce masque.

#### Étape de réécriture d’URL

Cette étape est complexe, car de nombreux algorithmes différents développés dans Magento 1 ne sont pas compatibles avec Magento 2. Pour différentes versions de Magento 1, il peut y avoir différents algorithmes. Ainsi, sous le dossier Step/UrlRewrite , il existe des classes qui ont été développées pour certaines versions spécifiques de Magento et Migration\Step\UrlRewrite\Version191to2000 en fait partie. Il peut transférer les données de réécriture d’URL de Magento 1.9.1 vers Magento 2.

#### EAV step

Cette étape transfère tous les attributs (produit, client, RMA) de Magento 1 vers Magento 2. Il utilise le fichier map-eav.xml qui contient des règles similaires à celles du fichier map.xml pour des cas spécifiques de traitement des données.

Certaines des tables traitées à l’étape :

* `eav_attribute`
* `eav_attribute_group`
* `eav_attribute_set`
* `eav_entity_attribute`
* `catalog_eav_attribute`
* `customer_eav_attribute`
* `eav_entity_type`

### Mode de migration delta

Après la migration principale, des données supplémentaires auraient pu être ajoutées à la base de données Magento 1 (par exemple, par les clients sur storefront). Pour suivre ces données, l&#39;outil configure les déclencheurs de base de données pour les tables au début du processus de migration. Pour plus d’informations, voir [Migrer les données créées par des extensions tierces](migrate-data/delta.md#migrate-data-created-by-third-party-extensions).

## Sources de données

Pour accéder aux sources de données de Magento 1 et Magento 2 et utiliser leurs données (sélectionner, mettre à jour, insérer, supprimer), le dossier Ressource contient de nombreuses classes. Migration\ResourceModel\Source et Migration\ResourceModel\Destination sont des classes principales. Toutes les étapes de migration l’utilisent pour fonctionner avec les données. Ces données sont contenues dans des classes telles que Migration\ResourceModel\Document, Migration\ResourceModel\Record, Migration\ResourceModel\Structure, etc.

Voici un diagramme de classes de ces classes :

![Structure de données de l’outil de migration](../../assets/data-migration/MmigrationToolDataStructure.png)

## Journalisation

Afin d’implémenter la sortie du processus de migration et de contrôler tous les niveaux possibles, l’enregistreur PSR, qui est utilisé dans Magento, est appliqué. `\Migration\Logger\Logger` classe a été implémentée pour fournir une fonctionnalité de journalisation. Pour utiliser l’enregistreur, vous devez l’injecter par injection de dépendance du constructeur.

```php
class SomeClass
{
    ...
    protected $logger;

    public function __construct(\Migration\Logger\Logger $logger)
    {
        $this->logger = $logger;
    }
    ...
}
```

Ensuite, vous pouvez utiliser cette classe pour la journalisation de certains événements :

```php
$this->logger->info("Some information message");
$this->logger->debug("Some debug message");
$this->logger->error("Message about error operation");
$this->logger->warning("Some warning message");
```

Il est possible de personnaliser l’emplacement où les informations du journal doivent être écrites. Vous pouvez le faire en ajoutant un gestionnaire à l’enregistreur à l’aide de la méthode pushHandler() de l’enregistreur. Chaque gestionnaire doit implémenter `\Monolog\Handler\HandlerInterface` interface . Pour l’instant, il existe deux gestionnaires :

* ConsoleHandler : écrit des messages dans la console

* FileHandler : écrit des messages dans le fichier journal défini dans l&#39;option de configuration « log_file »

Il est également possible de mettre en œuvre n’importe quel gestionnaire supplémentaire. Il existe un ensemble de gestionnaires dans le framework Magento. Exemple d’ajout de gestionnaires à l’enregistreur :

```php
// $this->consoleHandler is the object of Migration\Logger\ConsoleHandler class
// $this->logger is the object of Migration\Logger\Logger class
$this->logger->pushHandler($this->consoleHandler);
```

Pour définir des données supplémentaires pour l’enregistreur (mode actuel, nom de la table), vous pouvez utiliser des processeurs d’enregistreur. Il existe un processeur (MessageProcessor). Il est créé pour ajouter des données « supplémentaires » pour la journalisation des messages. Il est appelé chaque fois que la méthode du journal est exécutée. MessageProcessor a protégé $extra var, qui contient des valeurs vides pour &#39;mode&#39;, &#39;stage&#39;, &#39;step&#39; et &#39;table&#39;. Des données supplémentaires peuvent être transmises au processeur en tant que deuxième paramètre (contexte) pour la méthode de log. Actuellement, des jeux de données supplémentaires au processeur dans la méthode AbstractStep->runStage (transmettre le mode actuel, l’étape et l’étape au processeur) et les classes de données où utilisé logger->debug method (transmettre le nom de la table de migration). Exemple d’ajout de processeurs à l’enregistreur :

```php
// $this->processoris the object of Migration\Logger\messageProcessor class
// $this->logger is the object of Migration\Logger\Logger class
$this->logger->pushProcessor([$this->processor, 'setExtra']);
// As a second array value you need to pass method that should be executed when processor called
```

Il est possible de définir le niveau de verbosité. Pour l&#39;instant, il y a trois niveaux :

* `ERROR` (écrit uniquement les erreurs dans le journal)
* `INFO` (seules les informations importantes sont écrites dans le journal, valeur par défaut)
* `DEBUG` (tout est écrit)

Le niveau de journalisation du niveau de détail peut être défini séparément pour chaque gestionnaire en appelant `setLevel()` méthode . Si vous souhaitez définir le niveau de détail par le biais d’un paramètre de ligne de commande, vous devez modifier l’option « verbose » au lancement de l’application.

Vous pouvez formater les messages du journal à l’aide du formateur de monologue. Pour que la fonctionnalité de formateur fonctionne, vous devez spécifier le gestionnaire de journaux à l’aide de la méthode `setFormatter()`. Actuellement, nous disposons d’une classe de formateur (`MessageFormatter`) qui définit un certain format (en fonction du niveau de verbosité) pendant la gestion des messages (via la méthode `format()` exécutée à partir du gestionnaire ).

La manipulation de l’enregistreur (ajout de gestionnaires et de processeurs) et le traitement en mode verbeux sont effectués dans la méthode `process()` de la classe `Migration\Logger\Manager`. La méthode est appelée au démarrage de l’application.

## Tests automatiques

Il existe trois types de tests dans le [!DNL Data Migration Tool] :

* Statique
* Unité
* Intégration

Ils se trouvent dans le répertoire `tests/` de l’outil, qui est identique au type de test (les tests unitaires se trouvent dans le répertoire `tests/unit`). Pour lancer le test, phpunit doit être installé. Remplacez le répertoire actuel par le répertoire test et lancez phpunit. Par exemple :

```bash
[10:32 AM]-[vagrant@debian-70rc1-x64-vbox4210]-[/var/www/magento2/vendor/magento/data-migration-tool]-[git master]
$ cd tests/unit
```

```bash
[10:33 AM]-[vagrant@debian-70rc1-x64-vbox4210]-[/var/www/magento2/vendor/magento/data-migration-tool/tests/unit]-[git master]
$ phpunit
PHPUnit 8.1.0 by Sebastian Bergmann.
....
```
