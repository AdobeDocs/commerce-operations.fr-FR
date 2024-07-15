---
title: Personnaliser le [!DNL Data Migration Tool]
description: Découvrez comment personnaliser  [!DNL Data Migration Tool]  pour transférer des données créées par des extensions entre Magento 1 et Magento 2.
exl-id: a5c1575f-9d77-416e-91fe-a82905ef2e1c
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '836'
ht-degree: 0%

---

# Configurez le [!DNL Data Migration Tool]

Parfois, le format et la structure des données créés par [extensions](https://marketplace.magento.com/extensions.html) ou le code personnalisé sont différents entre Magento 1 et Magento 2. Utilisez des points d’extension dans le [!DNL Data Migration Tool] pour migrer ces données. Si le format et la structure des données sont identiques, l’outil peut migrer automatiquement les données sans intervention de l’utilisateur.

Pendant la migration, l’ [étape de mappage](technical-specification.md#map-step) analyse et compare toutes les tables Magento 1 et Magento 2, y compris celles créées par des extensions. Si les tableaux sont identiques, l’outil migre automatiquement les données. Si les tableaux diffèrent, l’outil arrête et en informe l’utilisateur.

>[!NOTE]
>
>Lisez la [spécification technique](technical-specification.md) avant de tenter d’étendre le [!DNL Data Migration Tool]. Consultez également le [Guide de migration](../overview.md) pour obtenir des informations générales sur l’utilisation de l’outil de migration.


## Modifications mineures du format et de la structure des données

Dans la plupart des cas, l’ [étape de mappage](technical-specification.md#map-step) résout suffisamment les changements mineurs de format de données et de structure à l’aide des méthodes suivantes dans le fichier `map.xml` :

- Modification des noms de table ou de champ avec des règles de mappage
- Transformer les formats de données avec des gestionnaires existants ou un gestionnaire personnalisé

Vous trouverez ci-dessous un exemple d’utilisation des règles de mappage et d’un gestionnaire. Cet exemple utilise une extension de Magento 1 hypothétique appelée &quot;GreatBlog&quot; qui a été améliorée pour Magento 2.

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

- Ne migrez pas de données inutiles à partir de la table d&#39;index `great_blog_index`.
- La table `great_blog_publication` a été renommée `great_blog_post` dans le Magento 2. Les données sont donc migrées vers la nouvelle table.
   - Le champ `summary` a été renommé `title`. Par conséquent, les données sont migrées vers le nouveau champ.
   - Le champ `priority` a été supprimé et n’existe plus dans Magento 2.
   - Les données du champ `body` ont changé de format et doivent être traitées par le gestionnaire personnalisé : `\Migration\Handler\GreatBlog\NewFormat`.
- Une nouvelle fonctionnalité de notation a été développée pour l&#39;extension &quot;GreatBlog&quot; en Magento 2.
   - Une nouvelle table `great_blog_rating` a été créée.
   - Un nouveau champ `great_blog_post.rating` a été créé.

### Étendre le mapping dans d’autres étapes

D’autres étapes prennent en charge le mappage, telles que l’[Étape AVC](technical-specification.md#eav-step) et l’étape Attributs du client. Ces étapes migrent une liste prédéfinie de tables de Magento. Supposons, par exemple, que l’extension &quot;GreatBlog&quot; ait un champ supplémentaire dans la table `eav_attribute` et que le nom ait été modifié dans Magento 2. Puisque la table est traitée par l’[Etape EV](technical-specification.md#eav-step), les règles de mappage doivent être écrites pour le fichier `map-eav.xml`. Les fichiers `map.xml` et `map-eav.xml` utilisent le même schéma `map.xsd`, de sorte que les règles de mappage restent identiques.

## Modifications majeures du format et de la structure des données

Outre l’étape de mappage, d’autres étapes se trouvent dans le fichier `config.xml` pour migrer les données avec des modifications majeures de format et de structure, notamment :

- [Étape de réécriture de l’URL](technical-specification.md#url-rewrite-step)
- Étape OrderGrids
- [Etape EAV](technical-specification.md#eav-step)

Contrairement à l’[étape de mappage](technical-specification.md#map-step), ces étapes analysent une liste prédéfinie de tables au lieu de toutes les tables.

Pour les modifications majeures du format et de la structure des données, créez une étape personnalisée.

### Création d’une étape personnalisée

En utilisant le même exemple &quot;GreatBlog&quot;, supposons que l’extension comporte une table dans le Magento 1, mais a été repensée pour avoir deux tables dans le Magento 2.

Dans Magento 1, il y avait une seule table `greatblog_post` :

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

La table Magento 2 `greatblog_post` se présente désormais comme suit :

```text
| Field     | Type     |
|-----------|----------|
| post_id   | INT      |
| title     | VARCHAR  |
| content   | TEXT     |
| author_id | SMALLINT |
```

Pour migrer toutes les données de l’ancienne structure de tables vers une nouvelle, vous pouvez créer une étape personnalisée dans le fichier `config.xml`. Par exemple :

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

L’outil exécute les étapes en fonction de leur position dans le fichier `config.xml`, de haut en bas. Dans notre exemple, `GreatBlog Step` s’exécute en dernier.

Les étapes peuvent inclure quatre types de classes :

- Vérification de l’intégrité
- Diffusion de données
- Vérification du volume
- Diffusion Delta

>[!NOTE]
>
>Pour plus d’informations, reportez-vous aux sections [Configuration](technical-specification.md#configuration), [Step internals](technical-specification.md#step-internals), [Stages](technical-specification.md#step-stages) et [Modes d’exécution](technical-specification.md#running-modes).


Des requêtes SQL complexes peuvent être assemblées dans ces classes pour récupérer et migrer des données. En outre, ces tables doivent être &quot;ignorées&quot; dans l’ [Étape de mappage](technical-specification.md#map-step) car elle analyse toutes les tables existantes et tente de migrer les données, sauf si elles se trouvent dans la balise `<ignore>` du fichier `map.xml`.

Pour la vérification de l’intégrité, définissez un fichier map supplémentaire dans le fichier `config.xml` afin de vérifier que la structure des tables est conforme à nos attentes.

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

Fichier map `map-greatblog.xml` :

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

La classe de vérification de l’intégrité `Vendor\Migration\Step\GreatBlog\Integrity` étend `Migration\App\Step\AbstractIntegrity` et contient la méthode `perform` dans laquelle nous vérifions la structure du tableau :

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

Ensuite, vous devez créer une classe pour le traitement et l’enregistrement des données dans la base de données Magento 2 `Vendor\Migration\Step\GreatBlog\Data` :

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

Dans une classe Volume `Vendor\Migration\Step\GreatBlog\Volume`, nous vérifions si les données ont été entièrement migrées :

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

Pour ajouter la fonctionnalité de migration delta, ajoutez un nouveau groupe au fichier `deltalog.xml`. Dans `group`, spécifiez le nom des tables devant faire l&#39;objet de modifications :

```xml
<groups>
    ...
    <group name="delta_greatblog">
        <document key="post_id">greatblog_post</document>
    </group>
</groups>
```

Créez ensuite la classe `Delta` `Vendor\Migration\Step\GreatBlog\Delta` qui étend `Migration\App\Step\AbstractDelta` :

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

Après l’implémentation de l’étape personnalisée fournie dans les exemples, le système extrait les données du tableau Magento 1 unique,
traitez-le à l’aide de la classe `Vendor\Migration\Step\GreatBlog\Data` et stockez les données dans deux tables de Magento 2. Les enregistrements nouveaux et modifiés sont distribués lors de la migration delta à l’aide de la classe `Vendor\Migration\Step\GreatBlog\Delta`.

## Méthodes d’extension interdites

Puisque [!DNL Data Migration Tool] et le Magento 2 évoluent constamment, les étapes et les gestionnaires existants peuvent être modifiés. Nous vous recommandons vivement de ne pas remplacer le comportement des étapes telles que l’[étape de mappage](technical-specification.md#map-step), l’[étape de réécriture d’URL](technical-specification.md#url-rewrite-step) et les gestionnaires en étendant leurs classes.

Certaines étapes ne prennent pas en charge le mappage et ne peuvent pas être modifiées sans modifier le code. Vous pouvez soit écrire une étape supplémentaire qui modifie les données à la fin de la migration, soit créer un [problème GitHub](https://github.com/magento/data-migration-tool/issues) et demander un nouveau point d’extension sur l’étape existante.
