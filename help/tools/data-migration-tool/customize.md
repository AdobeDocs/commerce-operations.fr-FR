---
title: Personnalisez le  [!DNL Data Migration Tool]
description: Découvrez comment personnaliser le pour transférer  [!DNL Data Migration Tool]  données créées par les extensions entre Magento 1 et Magento 2.
exl-id: a5c1575f-9d77-416e-91fe-a82905ef2e1c
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '836'
ht-degree: 0%

---

# Configuration du [!DNL Data Migration Tool]

Parfois, le format et la structure des données créés par les [extensions](https://marketplace.magento.com/extensions.html) ou le code personnalisé sont différents entre Magento 1 et Magento 2. Utilisez des points d’extension dans le [!DNL Data Migration Tool] pour migrer ces données. Si le format et la structure des données sont identiques, l’outil peut migrer automatiquement les données sans intervention de l’utilisateur.

Lors de la migration, l’étape [Mapper](technical-specification.md#map-step) analyse et compare toutes les tables Magento 1 et Magento 2, y compris celles créées par les extensions. Si les tables sont identiques, l’outil migre automatiquement les données. Si les tableaux sont différents, l’outil s’arrête et en informe l’utilisateur.

>[!NOTE]
>
>Lisez la [Spécification technique](technical-specification.md) avant de tenter d’étendre l’[!DNL Data Migration Tool]. Consultez également le [ Guide de migration ](../overview.md) pour obtenir des informations générales sur l’utilisation de l’outil de migration.


## Modifications mineures du format et de la structure des données

Dans la plupart des cas, l’étape [Mapper](technical-specification.md#map-step) résout suffisamment les modifications mineures du format et de la structure des données à l’aide des méthodes suivantes dans le fichier `map.xml` :

- Modifier les noms de table ou de champ avec des règles de mappage
- Transformer des formats de données avec des gestionnaires existants ou un gestionnaire personnalisé

Vous trouverez ci-dessous un exemple d’utilisation des règles de mappage et d’un gestionnaire . Cet exemple utilise une extension Magento 1 hypothétique appelée « GreatBlog » qui a été améliorée pour Magento 2.

```xml
<source>
    <document_rules>
        <ignore>
            <document>great_blog_index</document>
        </ignore>
        <rename>
            <document>great_blog_publication</document>
            <to>great_blog_post</to>
        </rename>
    </document_rules>
    <field_rules>
        <move>
            <field>great_blog_publication.summary</field>
            <to>great_blog_post.title</to>
        </move>
        <ignore>
            <field>great_blog_publication.priority</field>
        </ignore>
        <transform>
            <field>great_blog_publication.body</field>
            <handler class="\Migration\Handler\GreatBlog\NewFormat">
                <param name="switch" value="yes" />
            </handler>
        </transform>
    </field_rules>
</source>
<destination>
    <document_rules>
        <ignore>
            <document>great_blog_rating</document>
        </ignore>
    </document_rules>
    <field_rules>
        <ignore>
            <field>great_blog_post.rating</field>
        </ignore>
    </field_rules>
</destination>
```

- Ne migrez pas les données inutiles de la table d’index `great_blog_index`.
- La table `great_blog_publication` a été renommée en `great_blog_post` dans Magento 2, de sorte que les données sont migrées vers la nouvelle table.
   - Le champ `summary` a été renommé `title`, de sorte que les données sont migrées vers le nouveau champ.
   - Le champ `priority` a été supprimé et n’existe plus dans Magento 2.
   - Les données du champ `body` ont changé de format et doivent être traitées par le gestionnaire personnalisé : `\Migration\Handler\GreatBlog\NewFormat`.
- Une nouvelle fonction d’évaluation a été développée pour l’extension « GreatBlog » dans Magento 2.
   - Une nouvelle table `great_blog_rating` a été créée.
   - Un nouveau champ `great_blog_post.rating` a été créé.

### Étendre le mappage dans d’autres étapes

D’autres étapes prennent en charge le mappage, telles que l’étape [EAV](technical-specification.md#eav-step) et l’étape Attributs du client. Ces étapes permettent de migrer une liste prédéfinie de tables Magento. Supposons, par exemple, que l’extension « GreatBlog » comporte un champ supplémentaire dans la table `eav_attribute` et que son nom soit modifié dans Magento 2. Puisque la table est traitée par l’étape [EAV](technical-specification.md#eav-step), les règles de mappage doivent être écrites pour le fichier `map-eav.xml`. Les fichiers `map.xml` et `map-eav.xml` utilisent le même schéma de `map.xsd`. Les règles de mappage restent donc les mêmes.

## Modifications majeures du format et de la structure des données

Outre l’étape Mapper , le fichier `config.xml` contient d’autres étapes pour migrer les données avec des modifications majeures de format et de structure, notamment :

- [Étape De Réécriture D’Url](technical-specification.md#url-rewrite-step)
- Étape OrderGrids
- [EAV Step](technical-specification.md#eav-step)

Contrairement à l’étape [Mapper](technical-specification.md#map-step), ces étapes analysent une liste prédéfinie de tableaux au lieu de tous les tableaux.

Pour des modifications majeures du format et de la structure des données, créez une étape personnalisée.

### Création d’une étape personnalisée

En reprenant le même exemple « GreatBlog », supposons que l’extension ait une table dans Magento 1, mais qu’elle ait été repensée pour avoir deux tables dans Magento 2.

Dans Magento 1, il n’existait qu’une seule table `greatblog_post` :

```text
| Field     | Type     |
|-----------|----------|
| post_id   | INT      |
| title     | VARCHAR  |
| content   | TEXT     |
| author_id | SMALLINT |
| tags      | TEXT     |
```

Dans Magento 2, un nouveau tableau pour les balises `greatblog_post_tags` a été introduit :

```text
| Field      | Type     |
|------------|----------|
| post_id    | INT      |
| tag        | VARCHAR  |
| sort_order | SMALLINT |
```

Le tableau de `greatblog_post` de Magento 2 ressemble désormais à ceci :

```text
| Field     | Type     |
|-----------|----------|
| post_id   | INT      |
| title     | VARCHAR  |
| content   | TEXT     |
| author_id | SMALLINT |
```

Pour migrer toutes les données de l’ancienne structure des tables vers une nouvelle, vous pouvez créer une étape personnalisée dans le fichier `config.xml`. Par exemple :

```xml
<steps mode="data">
    ...
    <step title="GreatBlog Step">
        <integrity>Vendor\Migration\Step\GreatBlog\Integrity</integrity>
        <data>Vendor\Migration\Step\GreatBlog\Data</data>
        <volume>Vendor\Migration\Step\GreatBlog\Volume</volume>
    </step>
</steps>
<steps mode="delta">
    ...
    <step title="GreatBlog Step">
        <delta>Vendor\Migration\Step\GreatBlog\Delta</delta>
        <volume>Vendor\Migration\Step\GreatBlog\Volume</volume>
    </step>
</steps>
```

L’outil exécute les étapes en fonction de leur position dans le fichier `config.xml`, du haut vers le bas. Dans notre exemple, la `GreatBlog Step` s’exécute en dernier.

Les étapes peuvent inclure quatre types de classes :

- Vérification de l&#39;intégrité
- Diffusion de données
- Vérification du volume
- Diffusion Delta

>[!NOTE]
>
>Pour plus d’informations[ voir ](technical-specification.md#configuration)Configuration, [Internes des étapes](technical-specification.md#step-internals), [Étapes](technical-specification.md#step-stages) et [Modes d’exécution](technical-specification.md#running-modes).


Des requêtes SQL complexes peuvent être assemblées dans ces classes pour récupérer et migrer des données. En outre, ces tables doivent être « ignorées » dans l’étape [Mapper](technical-specification.md#map-step), car elle analyse toutes les tables existantes et tente de migrer les données à moins qu’elles ne se trouvent dans la balise `<ignore>` du fichier `map.xml`.

Pour la vérification d’intégrité, définissez un fichier de mappage supplémentaire dans le fichier `config.xml` pour vérifier que la structure des tableaux est conforme à nos attentes.

```xml
<config xmlns:xs="http://www.w3.org/2001/XMLSchema-instance"
        xs:noNamespaceSchemaLocation="urn:magento:module:Magento_DataMigrationTool:etc/config.xsd">
    ...
    <options>
        ...
        <greatblog_map_file>app/code/Vendor/Migration/etc/opensource-to-opensource/map-greatblog.xml</greatblog_map_file>
        ...
    </options>
</config>
```

Mapper le fichier `map-greatblog.xml` :

```xml
<map xmlns:xs="http://www.w3.org/2001/XMLSchema-instance"
     xs:noNamespaceSchemaLocation="urn:magento:module:Magento_DataMigrationTool:etc/map.xsd">
    <source>
        <field_rules>
            <ignore>
                <field>greatblog_post.tags</field>
            </ignore>
        </field_rules>
    </source>
    <destination>
        <document_rules>
            <ignore>
                <document>greatblog_post_tags</document>
            </ignore>
        </document_rules>
    </destination>
</map>
```

La classe de vérification d’intégrité `Vendor\Migration\Step\GreatBlog\Integrity` étend `Migration\App\Step\AbstractIntegrity` et contient la méthode `perform` dans laquelle nous vérifions la structure des tables :

```php
class Integrity extends \Migration\App\Step\AbstractIntegrity
{
    ...
    /**
     * Integrity constructor.
     * @param ProgressBar\LogLevelProcessor $progress
     * @param Logger $logger
     * @param Config $config
     * @param ResourceModel\Source $source
     * @param ResourceModel\Destination $destination
     * @param MapFactory $mapFactory
     * @param string $mapConfigOption
     */
    public function __construct(
        ProgressBar\LogLevelProcessor $progress,
        Logger $logger,
        Config $config,
        ResourceModel\Source $source,
        ResourceModel\Destination $destination,
        MapFactory $mapFactory,
        $mapConfigOption = 'greatblog_map_file'
    ) {
        parent::__construct($progress, $logger, $config, $source, $destination, $mapFactory, $mapConfigOption);
    }

    /**
     * @inheritDoc
     */
    public function perform()
    {
        $this->progress->start($this->getIterationsCount());
        $this->check(['greatblog_post'], MapInterface::TYPE_SOURCE);
        $this->check(['greatblog_post', 'greatblog_post_tags'], MapInterface::TYPE_DEST);
        $this->progress->finish();
        return $this->checkForErrors();
    }
    ...
}
```

Vous devez ensuite créer une classe pour le traitement et l’enregistrement des données dans la base de données Magento 2 `Vendor\Migration\Step\GreatBlog\Data` :

```php
class Data implements \Migration\App\Step\StageInterface
{
    ...
    /**
     * Data constructor.
     *
     * @param ProgressBar\LogLevelProcessor $progress
     * @param ResourceModel\Source $source
     * @param ResourceModel\Destination $destination
     * @param ResourceModel\RecordFactory $recordFactory
     * @param RecordTransformerFactory $recordTransformerFactory
     * @param MapFactory $mapFactory
     */
    public function __construct(
        ProgressBar\LogLevelProcessor $progress,
        ResourceModel\Source $source,
        ResourceModel\Destination $destination,
        ResourceModel\RecordFactory $recordFactory,
        RecordTransformerFactory $recordTransformerFactory,
        MapFactory $mapFactory
    ) {
        $this->progress = $progress;
        $this->destination = $destination;
        $this->recordFactory = $recordFactory;
        $this->source = $source;
        $this->recordTransformerFactory = $recordTransformerFactory;
        $this->map = $mapFactory->create('greatblog_map_file');
    }

    /**
     * @inheritDoc
     */
    public function perform()
    {
        $sourceDocName = 'greatblog_post';
        $sourceDocument = $this->source->getDocument($sourceDocName);
        $destinationDocName = 'greatblog_post';
        $destinationDocument = $this->destination->getDocument($destinationDocName);
        /** @var \Migration\RecordTransformer $recordTransformer */
        $recordTransformer = $this->recordTransformerFactory->create(
            [
                'sourceDocument' => $sourceDocument,
                'destDocument'   => $destinationDocument,
                'mapReader'      => $this->map
            ]
        );
        $recordTransformer->init();

        $this->progress->start($this->source->getRecordsCount($sourceDocName));
        $pageNumber = 0;
        while (!empty($items = $this->source->getRecords($sourceDocName, $pageNumber))) {
            $pageNumber++;
            $recordsToSave = $destinationDocument->getRecords();
            foreach ($items as $item) {
                $sourceRecord = $this->recordFactory->create(
                    ['document' => $sourceDocument, 'data' => $item]
                );
                $destinationRecord = $this->recordFactory->create(['document' => $destinationDocument]);
                $recordTransformer->transform($sourceRecord, $destinationRecord);
                $recordsToSave->addRecord($destinationRecord);
            }
            $this->destination->saveRecords($destinationDocName, $recordsToSave);

            $tags = $this->getTags($items);
            $this->destination->saveRecords('greatblog_post_tags', $tags);
            $this->progress->advance();
        }

        $this->progress->finish();
        return true;
    }
    ...
}
```

Dans un `Vendor\Migration\Step\GreatBlog\Volume` de classe de volume, nous vérifions si les données ont été entièrement migrées :

```php
class Volume extends \Migration\App\Step\AbstractVolume
{
    ...
    /**
     * @inheritdoc
     */
    public function perform()
    {
        $documentName = 'greatblog_post';
        $sourceCount = $this->source->getRecordsCount($documentName);
        $destinationCount = $this->destination->getRecordsCount($documentName);
        if ($sourceCount != $destinationCount) {
            $this->errors[] = sprintf(
                'Mismatch of entities in the document: %s Source: %s Destination: %s',
                $documentName,
                $sourceCount,
                $destinationCount
            );
        }

        return $this->checkForErrors(Logger::ERROR);
    }
    ...
}
```

Pour ajouter la fonctionnalité de migration delta, ajoutez un nouveau groupe au fichier `deltalog.xml`. Dans `group`, indiquez le nom des tables dont les modifications doivent être vérifiées :

```xml
<groups>
    ...
    <group name="delta_greatblog">
        <document key="post_id">greatblog_post</document>
    </group>
</groups>
```

Créez ensuite le `Delta` de classe `Vendor\Migration\Step\GreatBlog\Delta` qui étend `Migration\App\Step\AbstractDelta` :

```php
class Delta extends \Migration\App\Step\AbstractDelta
{
    /**
     * @var string
     */
    protected $mapConfigOption = 'greatblog_map_file';

    /**
     * @var string
     */
    protected $groupName = 'delta_greatblog';

    /**
     * @inheritDoc
     */
    public function perform()
    {
        $sourceDocumentName = 'greatblog_post';
        $idKeys = ['post_id'];
        $page = 0;
        while (!empty($items = $this->source->getChangedRecords($sourceDocumentName, $idKeys, $page++))) {
            $this->destination->deleteRecords(
                'greatblog_post_tags',
                $idKeys,
                $items
            );

            $tags = $this->getTags($items);
            $this->destination->saveRecords('greatblog_post_tags', $tags);
        }

        //parent class takes care of greatblog_post records automatically
        return parent::perform();
    }
}
```

Après l’implémentation de l’étape personnalisée fournie dans les exemples, le système extrait les données de la table Magento 1 unique,
traitez-le à l’aide de la classe `Vendor\Migration\Step\GreatBlog\Data` et stockez les données dans deux tableaux Magento 2. Les enregistrements nouveaux et modifiés sont diffusés lors de la migration delta à l’aide de la classe `Vendor\Migration\Step\GreatBlog\Delta`.

## Méthodes d’extension interdites

Étant donné que [!DNL Data Migration Tool] et Magento 2 évoluent constamment, les étapes et les gestionnaires existants peuvent faire l’objet de modifications. Nous vous recommandons vivement de ne pas remplacer le comportement d’étapes telles que [Étape de mappage](technical-specification.md#map-step), [Étape de réécriture d’URL](technical-specification.md#url-rewrite-step) et de gestionnaires en étendant leurs classes.

Certaines étapes ne prennent pas en charge le mappage et ne peuvent pas être modifiées sans modifier le code. Vous pouvez écrire une étape supplémentaire qui modifie les données à la fin de la migration ou créer un [problème GitHub](https://github.com/magento/data-migration-tool/issues) et demander un nouveau point d’extension sur l’étape existante.
