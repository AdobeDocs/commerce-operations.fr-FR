---
title: "[!DNL Data Migration Tool] spécification technique"
description: "En savoir plus sur les détails de mise en oeuvre de la variable [!DNL Data Migration Tool] et comment étendre lors du transfert de données entre Magento 1 et Magento 2."
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '2079'
ht-degree: 0%

---


# [!DNL Data Migration Tool] spécification technique

Cette section décrit [!DNL Data Migration Tool] détails de mise en oeuvre et extension de ses fonctionnalités.

## Référentiels

Pour accéder au [!DNL Data Migration Tool] code source, voir GitHub [référentiel](https://github.com/magento/data-migration-tool).

## Configuration requise

Le [configuration requise](../../installation/system-requirements.md) pour le [!DNL Data Migration Tool] sont identiques à pour Magento 2.

## Structure interne

### Structure du répertoire

Le diagramme suivant représente la structure de répertoires de [!DNL Data Migration Tool]:

```terminal
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

## Point d’entrée

Le script qui exécute le processus de migration se trouve à l’emplacement suivant : `magento-root/bin/magento`.

## Configuration

Le schéma de la configuration `config.xsd` se trouve dans le fichier `etc/` répertoire . Le fichier de configuration par défaut (`config.xml.dist`) est créé pour chaque version de Magento 1.x. Il se trouve dans un répertoire distinct sous `etc/`.

Le fichier de configuration par défaut peut être remplacé par un fichier personnalisé (voir [syntaxe de commande](migrate-data/overview.md#command-syntax)).

Le fichier de configuration possède la structure suivante :

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

* Steps : décrit toutes les étapes qui sont traitées lors de la migration.

* source : configuration pour la source de données. Types de source disponibles : base

* destination : configuration pour la destination des données. Types de destination disponibles : base

* options - liste des paramètres. Contient les paramètres obligatoires (map_file, settings_map_file, bulk_size) et facultatifs (option_personnalisée, resource_adapter_class_name, prefix_source, prefix_dest, log_file).

Modifier l’option de préfixe au cas où Magento aurait été installé avec le préfixe dans les tables de base de données. Il peut être défini pour les bases de données Magento 1 et Magento 2. Utilisez les options de configuration &quot;source_prefix&quot; et &quot;dest_prefix&quot; en conséquence.

Les données de configuration sont accessibles à l’aide de la variable `\Migration\Config` classe .

## Étapes disponibles

| Document | Champ |
|---|---|
| `step` | Noeud de second niveau dans le noeud Steps. La description de l’étape concernée doit être indiquée dans la variable `title` attribut. |
| `integrity` | Spécifie la classe PHP responsable de la vérification de l’intégrité. Compare les noms, types et autres informations des champs de tableau afin de vérifier la compatibilité entre les structures de données Magento 1 et 2. |
| `data` | Spécifie la classe PHP responsable de la vérification des données. Transfère les données, tableau par tableau, du Magento 1 au Magento 2. |
| `volume` | Spécifie la classe PHP responsable de la vérification du volume. Compare le nombre d’enregistrements entre les tables pour vérifier que le transfert a réussi. |
| `delta` | Spécifie la classe PHP responsable de la vérification delta. Transfère le delta du Magento 1 au Magento 2 après la migration complète des données. |

## Attributs d’informations de base de données source

| Document | Champ | Obligatoire ? |
|---|---|---|
| `name` | Nom de la base de données du serveur Magento 1. | oui |
| `host` | Adresse IP de l’hôte du serveur Magento 1. | oui |
| `port` | Numéro de port du serveur Magento 1. | non |
| `user` | Nom d’utilisateur du serveur de base de données Magento 1. | oui |
| `password` | Mot de passe du serveur de base de données Magento 1. | oui |
| `ssl_ca` | Chemin d’accès au fichier de l’autorité de certification SSL. | non |
| `ssl_cert` | Chemin d’accès au fichier de certificat SSL. | non |
| `ssl_key` | Chemin d’accès au fichier de clé SSL. | non |

## Attributs d’informations de base de données de destination

| Document | Champ | Obligatoire ? |
|---|---|---|
| `name` | Nom de la base de données du serveur Magento 2. | oui |
| `host` | Adresse IP de l’hôte du serveur Magento 2. | oui |
| `port` | Numéro de port du serveur Magento 2. | non |
| `user` | Nom d’utilisateur du serveur de base de données Magento 2. | oui |
| `password` | Mot de passe du serveur de base de données Magento 2. | oui |
| `ssl_ca` | Chemin d’accès au fichier de l’autorité de certification SSL. | non |
| `ssl_cert` | Chemin d’accès au fichier de certificat SSL. | non |
| `ssl_key` | Chemin d’accès au fichier de clé SSL. | non |

## Connexion à l’aide du protocole TLS

Vous pouvez également vous connecter à une base de données à l’aide du protocole TLS (c’est-à-dire à l’aide de clés cryptographiques publiques/privées). Ajoutez les attributs facultatifs suivants au `database` element:

* `ssl_ca`
* `ssl_cert`
* `ssl_key`

Par exemple :

```xml
<source>
    <database host="localhost" name="magento1" user="root" ssl_ca="/path/to/file" ssl_cert="/path/to/file" ssl_key="/path/to/file"/>
</source>
<destination>
    <database host="localhost" name="magento2" user="root" ssl_ca="/path/to/file" ssl_cert="/path/to/file" ssl_key="/path/to/file"/>
</destination>
```

## Étape interne

Le processus de migration se compose d’étapes.

L’étape est une unité qui fournit les fonctionnalités requises pour la migration de certaines données séparées. L’étape peut se composer d’une ou de plusieurs étapes (contrôle de l’intégrité, données, contrôle du volume et delta).

Par défaut, il existe plusieurs étapes ([Carte](#map-step), [EAV](#eav), [URL Rewrites](#url-rewrite-step), etc.). Vous pouvez également ajouter vos propres étapes.

Les classes liées aux étapes se trouvent dans le répertoire src/Migration/Step .

Pour exécuter une classe Step, la classe doit être définie dans le fichier config.xml .

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

Chaque classe d’étape doit mettre en oeuvre StageInterface.

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

Si l’étape de données prend en charge la restauration, elle doit mettre en oeuvre la variable `RollbackInterface` .

La visualisation de l’étape en cours d’exécution est fournie par le composant ProgressBar de Symfony (voir [Barre de progression](https://symfony.com/doc/current/components/console/helpers/progressbar.html)). Accédez à ce composant dans une étape en tant que LogLevelProcessor.

Les principales méthodes d’utilisation sont les suivantes :

```xml
$this->progress->start();
$this->progress->advance();
$this->progress->finish();
```

## Étapes

### Vérification de l’intégrité

Chaque étape doit vérifier que la structure de la source de données (Magento 1 par défaut) et la structure de la destination de données (Magento 2) sont compatibles. Si ce n’est pas le cas, une erreur s’affiche avec les entités non compatibles. Si les champs ont des types de données différents (le même champ a un type de données décimal dans Magento 1 et un entier dans Magento 2), un message d’avertissement s’affiche (sauf lorsqu’il a été traité dans le fichier Map).

### Transfert de données

Si l’intégrité est vérifiée, le transfert des données est en cours d’exécution. Si des erreurs s’affichent, la restauration s’exécute pour revenir à l’état précédent de Magento 2. Si une classe d’étape met en oeuvre la variable `RollbackInterface` , la méthode de restauration s’exécute en cas d’erreur.

### Vérification du volume

Une fois les données migrées, le contrôle du volume permet de vérifier que toutes les données ont été correctement transférées.

### Diffusion delta

La fonctionnalité Delta est chargée de fournir le reste des données ajoutées après la migration principale.

## Modes d’exécution

L’outil doit être exécuté selon trois modes différents, dans un ordre particulier :

1. settings - migration des paramètres système
1. data - migration principale des données
1. delta : migration du reste des données ajoutées après la migration principale

Chaque mode possède sa propre liste d’étapes à exécuter. Voir config.xml

### Mode de migration des paramètres

Le mode de migration des paramètres de cet outil est utilisé pour transférer les entités suivantes :

1. Sites web, magasins, vues de magasin.
1. Configuration de magasin (principalement Magasins->Configuration dans M2 ou Système->Configuration dans M1)

Toutes les configurations de magasin conservent ses données dans la table core_config_data de la base de données. Le fichier settings.xml contient les règles de cette table qui sont appliquées lors du processus de migration. Ce fichier décrit les paramètres qui doivent être ignorés, renommés ou qui doivent modifier leurs valeurs. Le fichier settings.xml possède la structure suivante :

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

Sous le noeud `<key>` certaines règles fonctionnent avec la colonne &quot;chemin&quot; dans la variable `core_config_data` table. `<ignore>` les règles empêchent l’outil de transférer certains paramètres. Les caractères génériques peuvent être utilisés dans ce noeud. Tous les autres paramètres ne sont pas répertoriés dans la variable `<ignore>` sont migrés. Si le chemin d’accès à un paramètre a été modifié dans Magento 2, il doit être ajouté à `//key/rename` , où l’ancien chemin d’accès indique dans `//key/rename/path` Le noeud et le nouveau chemin d’accès indiquent dans `//key/rename/to` noeud .

Sous le noeud `<value>`, certaines règles fonctionnent avec la colonne &quot;valeur&quot; dans la variable `core_config_data` table. Ces règles visent à transformer la valeur des paramètres par les gestionnaires (classes qui implémentent `Migration\Handler\HandlerInterface`) et l’adapter pour Magento 2.

### Mode de migration des données

Dans ce mode, la plupart des données sont migrées. Avant la migration des données, les étapes de vérification de l’intégrité sont exécutées pour chaque étape. Si la vérification de l’intégrité est effectuée, la variable [!DNL Data Migration Tool] installe les tables de suppression (avec préfixe) `m2_cl_*`) et les déclencheurs correspondants à la base de données Magento 1 et exécutent l’étape de migration des données des étapes. Une fois la migration terminée sans erreur, la vérification du volume vérifie la cohérence des données. Il peut afficher un message d’avertissement si vous migrez le magasin en direct. Ne vous inquiétez pas, la migration delta prend en charge ces données incrémentielles. Les étapes de migration les plus utiles sont les cartes, la réécriture d’URL et le contrôle qualité de vue.

#### Étape de mappage

L’étape de carte est chargée de transférer la plupart des données du Magento 1 vers le Magento 2. Cette étape lit les instructions à partir du fichier map.xml (situé dans `etc/` ). Le fichier décrit les différences entre les structures de données de la source (Magento 1) et de la destination (Magento 2). Si le Magento 1 contient des tables ou des champs appartenant à une extension qui n’existe pas dans le Magento 2, ces entités peuvent être placées ici pour les ignorer par l’étape de carte. Sinon, un message d’erreur s’affiche.

Le fichier de carte a le format suivant :

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

Zones :

* *source* - contient les règles de la base de données source

* *destination* - contient les règles de la base de données de destination

Options :

* *ignore* - document, champ ou type de données marqué par cette option est ignoré

* *renommer* - décrit les relations de nom entre les documents portant un nom différent. Dans un cas où le nom du document de destination n’est pas le même que pour le document source, vous pouvez utiliser l’option de changement de nom pour définir le nom du document source comme nom de la table de destination.

* *move* - définit la règle pour déplacer un champ spécifié du document source vers le document de destination. REMARQUE : le nom du document de destination doit être identique au nom du document source. Si les noms des documents source et de destination sont différents, vous devez utiliser l’option de changement de nom pour le document qui contient un champ déplacé.

* *transform* - est une option qui permet à l’utilisateur de migrer des champs en fonction du comportement décrit dans les gestionnaires.

* *gestionnaire* - décrit le comportement de transformation des champs. Pour appeler le gestionnaire, vous devez spécifier un nom de classe de gestionnaire dans une `<handler>` balise . Utilisez la variable `<param>` balise avec le nom du paramètre et les données de valeur pour les transmettre au gestionnaire.

**Source** opérations disponibles :

| Document | Champ |
|--- |--- |
| ignorer le changement | ignorer la transformation |

**Destination** opérations disponibles :

| Document | Champ |
|--- |--- |
| ignore | ignorer la transformation |

#### Caractères génériques

Pour ignorer les documents comportant des parties similaires (`document_name_1`, `document_name_2`), vous pouvez utiliser la fonctionnalité de caractères génériques. Put `*` symbole au lieu d’une partie qui se répète (`document_name_*`) et ce masque couvre tous les documents source ou destination qui correspondent à ce masque.

#### Étape de réécriture d’URL

Cette étape est complexe car de nombreux algorithmes différents développés dans Magento 1 ne sont pas compatibles avec Magento 2. Pour différentes versions de Magento 1, il peut y avoir différents algorithmes. Ainsi, sous le dossier Step/UrlRewrite, il existe des classes qui ont été développées pour certaines versions spécifiques de Magento et Migration\Step\UrlRewrite\Version191to2000 is one of them. Il peut transférer l’URL Réécrit les données de Magento 1.9.1 vers Magento 2.

#### Etape EAV

Cette étape transfère tous les attributs (produit, client, RMA) du Magento 1 au Magento 2. Il utilise le fichier map-eav.xml qui contient des règles similaires à celles du fichier map.xml pour des cas spécifiques de données de traitement.

Certaines des tables qui sont traitées à l’étape :

* `eav_attribute`
* `eav_attribute_group`
* `eav_attribute_set`
* `eav_entity_attribute`
* `catalog_eav_attribute`
* `customer_eav_attribute`
* `eav_entity_type`

### Mode de migration delta

Après la migration principale, des données supplémentaires peuvent avoir été ajoutées à la base de données Magento 1 (par exemple, par les clients sur le storefront). Pour suivre ces données, l&#39;outil configure les déclencheurs de base de données pour les tables au début du processus de migration. Pour plus d’informations, voir [Migration de données créées par des extensions tierces](migrate-data/delta.md#migrate-data-created-by-third-party-extensions).

## Sources de données

Pour accéder aux sources de données du Magento 1 et du Magento 2 et utiliser ses données (sélectionner, mettre à jour, insérer, supprimer), de nombreuses classes sont présentes dans le dossier Ressource. Migration\ResourceModel\Source et Migration\ResourceModel\Destination sont les classes principales. Toutes les étapes de migration l’utilisent pour fonctionner avec les données. Ces données sont contenues dans des classes telles que Migration\ResourceModel\Document, Migration\ResourceModel\Record, Migration\ResourceModel\Structure, etc.

Voici un diagramme de classe de ces classes :

![Structure des données de l’outil de migration](../../assets/data-migration/MmigrationToolDataStructure.png)

## Journalisation

Pour mettre en oeuvre la sortie du processus de migration et contrôler tous les niveaux possibles, le journal PSR, utilisé en Magento, est appliqué. `\Migration\Logger\Logger` a été mise en oeuvre pour fournir des fonctionnalités de journalisation. Pour utiliser l’enregistreur, vous devez l’injecter par injection de dépendance de constructeur.

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

Il est possible de personnaliser l’emplacement où les informations de journal doivent être écrites. Pour ce faire, ajoutez un gestionnaire à l’enregistreur à l’aide de la méthode pushHandler() de l’enregistreur. Chaque gestionnaire doit implémenter `\Monolog\Handler\HandlerInterface` . Pour l&#39;instant, il y a deux gestionnaires :

* ConsoleHandler : écrit les messages sur la console

* FileHandler : écrit les messages dans le fichier journal qui a été défini dans l’option de configuration &quot;log_file&quot;.

Il est également possible de mettre en oeuvre tout gestionnaire supplémentaire. Il existe un ensemble de gestionnaires dans le cadre Magento. Exemple d’ajout de gestionnaires à l’enregistreur :

```php
// $this->consoleHandler is the object of Migration\Logger\ConsoleHandler class
// $this->logger is the object of Migration\Logger\Logger class
$this->logger->pushHandler($this->consoleHandler);
```

Pour définir des données supplémentaires pour la journalisation (mode actuel, nom de table), vous pouvez utiliser des processeurs de journalisation. Il existe un processeur existant (MessageProcessor). Il est créé pour ajouter des données &quot;supplémentaires&quot; pour les messages de journalisation et est appelé chaque fois que la méthode de journal est exécutée. MessageProcessor a protégé $extra var, qui contient des valeurs vides pour &quot;mode&quot;, &quot;stage&quot;, &quot;step&quot; et &quot;table&quot;. Des données supplémentaires peuvent être transmises au processeur en tant que second paramètre (contexte) pour la méthode de journal. Actuellement, des ensembles de données supplémentaires sont affectés au processeur dans la méthode AbstractStep->runStage (transmettez le mode en cours, l’étape et l’étape au processeur) et les classes de données dans lesquelles la méthode logger->debug (transmettez le nom de la table de migration) a été utilisée. Exemple d’ajout de processeurs à l’enregistreur :

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

Le niveau de journal de la visibilité peut être défini séparément pour chaque gestionnaire en appelant `setLevel()` . Si vous souhaitez définir le niveau de détail via un paramètre de ligne de commande, vous devez modifier l’option &quot;verbose&quot; au lancement de l’application.

Vous pouvez formater les messages du journal à l’aide du formateur monolog. Pour que la fonctionnalité de formatage fonctionne, vous devez spécifier le gestionnaire de journaux à l’aide de la variable `setFormatter()` . Actuellement, nous avons une classe de formatage (`MessageFormatter`) qui définit un certain format (dépend du niveau de verbosité) lors de la gestion des messages (via `format()` à partir du gestionnaire).

La manipulation de l’enregistreur (ajout de gestionnaires et de processeurs) et le traitement en mode verbose s’effectue dans la variable `process()` de la méthode `Migration\Logger\Manager` classe . La méthode est appelée au démarrage de l’application.

## Tests automatiques

Il existe trois types de tests dans la variable [!DNL Data Migration Tool]:

* Statique
* Unité
* Intégration

Ils se trouvent dans le `tests/` , qui est identique au type de test (les tests unitaires se trouvent dans la variable `tests/unit` ). Pour lancer le test, phpunit doit être installé. Remplacez le répertoire actuel par le répertoire test et lancez phpunit. Par exemple :

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
