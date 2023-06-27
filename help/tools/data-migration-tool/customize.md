---
title: Personnalisez le [!DNL Data Migration Tool]
description: Découvrez comment personnaliser le [!DNL Data Migration Tool] pour transférer des données créées par des extensions entre Magento 1 et Magento 2.
exl-id: a5c1575f-9d77-416e-91fe-a82905ef2e1c
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '821'
ht-degree: 0%

---

# Configurez la variable [!DNL Data Migration Tool]

Parfois, le format et la structure des données créés par [extensions](https://marketplace.magento.com/extensions.html) ou le code personnalisé est différent entre Magento 1 et Magento 2. Utilisez les points d’extension dans la variable [!DNL Data Migration Tool] pour migrer ces données. Si le format et la structure des données sont identiques, l’outil peut migrer automatiquement les données sans intervention de l’utilisateur.

Lors de la migration, la variable [Étape de mappage](technical-specification.md#map-step) analyse et compare toutes les tables Magento 1 et Magento 2, y compris celles créées par des extensions. Si les tableaux sont identiques, l’outil migre automatiquement les données. Si les tableaux diffèrent, l’outil arrête et en informe l’utilisateur.

>[!NOTE]
>
>Lisez le [Spécifications techniques](technical-specification.md) avant d’essayer d’étendre la variable [!DNL Data Migration Tool]. En outre, passez en revue les [Guide de migration](../overview.md) pour obtenir des informations générales sur l’utilisation de l’outil de migration.


## Modifications mineures du format et de la structure des données

Dans la plupart des cas, la variable [Étape de mappage](technical-specification.md#map-step) résout suffisamment les changements mineurs du format des données et de la structure à l’aide des méthodes suivantes dans la variable `map.xml` fichier :

- Modification des noms de table ou de champ avec des règles de mappage
- Transformation des formats de données à l’aide de gestionnaires existants ou d’un gestionnaire personnalisé

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

- Ne migrez pas de données inutiles à partir du `great_blog_index` table d’index.
- La table `great_blog_publication` a été renommé en `great_blog_post` dans Magento 2, les données sont donc migrées vers le nouveau tableau.
   - Le `summary` a été renommé `title`, les données sont donc migrées vers le nouveau champ.
   - Le `priority` a été supprimé et n’existe plus dans Magento 2.
   - Les données de la variable `body` a changé de format et doit être traité par le gestionnaire personnalisé : `\Migration\Handler\GreatBlog\NewFormat`.
- Une nouvelle fonctionnalité de notation a été développée pour l&#39;extension &quot;GreatBlog&quot; en Magento 2.
   - Une nouvelle `great_blog_rating` table a été créée.
   - Une nouvelle `great_blog_post.rating` a été créé.

### Étendre le mapping dans d’autres étapes

D’autres étapes prennent en charge le mappage, telles que [Etape EAV](technical-specification.md#eav-step) et l’étape Attributs du client . Ces étapes migrent une liste prédéfinie de tables de Magento. Supposons, par exemple, que l’extension &quot;GreatBlog&quot; comporte un champ supplémentaire dans la variable `eav_attribute` et le nom a été modifié dans Magento 2. Puisque le tableau est traité par la variable [Etape EAV](technical-specification.md#eav-step), les règles de mappage doivent être écrites pour la variable `map-eav.xml` fichier . Le `map.xml` et `map-eav.xml` Les fichiers utilisent le même `map.xsd` schéma, de sorte que les règles de mappage restent identiques.

## Modifications majeures du format et de la structure des données

Outre l’étape de mappage, d’autres étapes se trouvent dans la variable `config.xml` fichier qui migre des données avec des modifications majeures de format et de structure, notamment :

- [Étape de réécriture de l’URL](technical-specification.md#url-rewrite-step)
- Étape OrderGrids
- [Etape EAV](technical-specification.md#eav-step)

Contrairement au [Étape de mappage](technical-specification.md#map-step), ces étapes analysent une liste prédéfinie de tableaux au lieu de tous les tableaux.

Pour les modifications majeures du format et de la structure des données, créez une étape personnalisée.

### Création d’une étape personnalisée

En utilisant le même exemple &quot;GreatBlog&quot;, supposons que l’extension comporte une table dans le Magento 1, mais a été repensée pour avoir deux tables dans le Magento 2.

En Magento 1, il n’y avait qu’une seule `greatblog_post` table :

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

Magento 2 `greatblog_post` le tableau se présente désormais comme suit :

```text
| Field     | Type     |
|-----------|----------|
| post_id   | INT      |
| title     | VARCHAR  |
| content   | TEXT     |
| author_id | SMALLINT |
```

Pour migrer toutes les données de l’ancienne structure de tableaux vers une nouvelle, vous pouvez créer une étape personnalisée dans le `config.xml` fichier . Par exemple :

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

L’outil exécute les étapes en fonction de leur position dans la variable `config.xml` fichier; de haut en bas. Dans notre exemple, la variable `GreatBlog Step` s’exécute en dernier.

Les étapes peuvent inclure quatre types de classes :

- Vérification de l’intégrité
- Diffusion de données
- Vérification du volume
- Diffusion Delta

>[!NOTE]
>
>Voir [Configuration](technical-specification.md#configuration), [Étape interne](technical-specification.md#step-internals), [Phases](technical-specification.md#step-stages), et [Modes d’exécution](technical-specification.md#running-modes) pour plus d’informations.


Des requêtes SQL complexes peuvent être assemblées dans ces classes pour récupérer et migrer des données. En outre, ces tableaux doivent être &quot;ignorés&quot; dans la variable [Étape de mappage](technical-specification.md#map-step) car il analyse toutes les tables existantes et tente de migrer les données, sauf si elles se trouvent dans la variable `<ignore>` de la balise `map.xml` fichier .

Pour la vérification de l’intégrité, définissez un fichier de mappage supplémentaire dans le `config.xml` pour vérifier que la structure des tables est conforme à nos attentes.

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

Fichier de carte `map-greatblog.xml`:

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

Classe de vérification de l’intégrité `Vendor\Migration\Step\GreatBlog\Integrity` étend `Migration\App\Step\AbstractIntegrity` et contient le paramètre `perform` où nous vérifions la structure du tableau :

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

Ensuite, vous devez créer une classe pour le traitement et l’enregistrement des données dans la base de données Magento 2. `Vendor\Migration\Step\GreatBlog\Data`:

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

Pour ajouter la fonctionnalité de migration delta, ajoutez un nouveau groupe au `deltalog.xml` fichier . Dans `group`, indiquez le nom des tables qui doivent être vérifiées pour les modifications :

```xml
<groups>
    ...
    <group name="delta_greatblog">
        <document key="post_id">greatblog_post</document>
    </group>
</groups>
```

Créez ensuite le `Delta` class `Vendor\Migration\Step\GreatBlog\Delta` qui étend `Migration\App\Step\AbstractDelta`:

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

Après l’implémentation de l’étape personnalisée fournie dans les exemples, le système extrait les données de la table Magento 1 unique, puis les traite à l’aide de `Vendor\Migration\Step\GreatBlog\Data` et stockez les données dans deux tables de Magento 2. Les enregistrements nouveaux et modifiés sont distribués lors de la migration delta à l’aide de la fonction `Vendor\Migration\Step\GreatBlog\Delta` classe .

## Méthodes d’extension interdites

Depuis la variable [!DNL Data Migration Tool] et le Magento 2 évoluent constamment, les étapes et les gestionnaires existants peuvent être modifiés. Il est vivement recommandé de ne pas remplacer le comportement d’étapes telles que la [Étape de mappage](technical-specification.md#map-step), [Étape de réécriture d’URL](technical-specification.md#url-rewrite-step)et les gestionnaires en étendant leurs classes.

Certaines étapes ne prennent pas en charge le mappage et ne peuvent pas être modifiées sans modifier le code. Vous pouvez soit écrire une étape supplémentaire qui modifie les données à la fin de la migration, soit créer une [Problème GitHub](https://github.com/magento/data-migration-tool/issues) et demandez un nouveau point d’extension sur l’étape existante.
