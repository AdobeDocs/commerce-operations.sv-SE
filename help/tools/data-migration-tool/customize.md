---
title: Anpassa  [!DNL Data Migration Tool]
description: Lär dig hur du anpassar  [!DNL Data Migration Tool]  för att överföra data som har skapats med tillägg mellan Magento 1 och Magento 2.
exl-id: a5c1575f-9d77-416e-91fe-a82905ef2e1c
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '836'
ht-degree: 0%

---

# Konfigurera [!DNL Data Migration Tool]

Ibland skiljer sig dataformatet och strukturen som skapas av [extensions](https://marketplace.magento.com/extensions.html) eller anpassad kod mellan Magento 1 och Magento 2. Använd tilläggspunkter i [!DNL Data Migration Tool] för att migrera dessa data. Om dataformatet och strukturen är desamma kan verktyget automatiskt migrera data utan att användaren behöver göra något.

Under migreringen skannar och jämför [Kartsteget](technical-specification.md#map-step) alla Magento 1- och Magento 2-tabeller, inklusive de som skapats med tillägg. Om tabellerna är desamma migreras data automatiskt. Om tabellerna skiljer sig åt avslutas verktyget och användaren meddelas om detta.

>[!NOTE]
>
>Läs den [tekniska specifikationen](technical-specification.md) innan du försöker utöka [!DNL Data Migration Tool]. Granska även [migreringshandboken](../overview.md) för allmän information om hur du använder migreringsverktyget.


## Mindre förändringar i dataformat och struktur

I de flesta fall löser [Mappningssteget](technical-specification.md#map-step) mindre dataformat och strukturändringar tillräckligt med hjälp av följande metoder i filen `map.xml`:

- Ändra tabell- eller fältnamn med mappningsregler
- Omforma dataformat med befintliga hanterare eller en anpassad hanterare

I följande exempel visas ett exempel på hur du använder både mappningsregler och en hanterare. I det här exemplet används ett hypotetiskt Magento 1-tillägg som kallas &quot;GreatBlog&quot; som har förbättrats för Magento 2.

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

- Migrera inte onödiga data från indextabellen `great_blog_index`.
- Tabellen `great_blog_publication` har bytt namn till `great_blog_post` i Magento 2, så data migreras till den nya tabellen.
   - Fältet `summary` har bytt namn till `title`, så data migreras till det nya fältet.
   - Fältet `priority` togs bort och finns inte längre i Magento 2.
   - Data i fältet `body` har ändrat format och bör bearbetas av den anpassade hanteraren: `\Migration\Handler\GreatBlog\NewFormat`.
- En ny klassificeringsfunktion har utvecklats för tillägget&quot;GreatBlog&quot; i Magento 2.
   - En ny `great_blog_rating`-tabell skapades.
   - Ett nytt `great_blog_post.rating`-fält skapades.

### Utöka mappningen i andra steg

Andra steg har stöd för mappning, som [EAV Step](technical-specification.md#eav-step) och Customer Attributes Step. Med de här stegen migreras en fördefinierad lista med Magento-tabeller. Anta till exempel att tillägget GreatBlog har ett extra fält i tabellen `eav_attribute` och att namnet har ändrats i Magento 2. Eftersom tabellen bearbetas av [EAV-steget](technical-specification.md#eav-step) bör mappningsregler skrivas för filen `map-eav.xml`. Filerna `map.xml` och `map-eav.xml` använder samma `map.xsd`-schema, så mappningsreglerna är desamma.

## Större förändringar i dataformat och struktur

Förutom schemasteget finns det andra steg i filen `config.xml` som migrerar data med viktiga format- och strukturändringar, bland annat:

- [Omskrivningssteg för URL](technical-specification.md#url-rewrite-step)
- OrderGrid-steg
- [EAV-steg](technical-specification.md#eav-step)

Till skillnad från [kartsteget](technical-specification.md#map-step) skannar de här stegen en fördefinierad lista med tabeller i stället för alla tabeller.

Skapa ett anpassat steg för större ändringar av dataformat och struktur.

### Skapa ett eget steg

Anta att tillägget har en tabell i Magento 1, men att det har fått två tabeller i Magento 2, med samma&quot;GreatBlog&quot;-exempel.

I Magento 1 fanns en enda `greatblog_post`-tabell:

```text
| Field     | Type     |
|-----------|----------|
| post_id   | INT      |
| title     | VARCHAR  |
| content   | TEXT     |
| author_id | SMALLINT |
| tags      | TEXT     |
```

I Magento 2 introducerades en ny tabell för taggarna `greatblog_post_tags`:

```text
| Field      | Type     |
|------------|----------|
| post_id    | INT      |
| tag        | VARCHAR  |
| sort_order | SMALLINT |
```

Tabellen Magento 2 `greatblog_post` ser nu ut så här:

```text
| Field     | Type     |
|-----------|----------|
| post_id   | INT      |
| title     | VARCHAR  |
| content   | TEXT     |
| author_id | SMALLINT |
```

Om du vill migrera alla data från den gamla tabellstrukturen till en ny kan du skapa ett anpassat steg i filen `config.xml`. Exempel:

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

Verktyget kör steg utifrån deras position i filen `config.xml`, uppifrån och ned. I vårt exempel körs `GreatBlog Step` sist.

Stegen kan innehålla fyra typer av klasser:

- Integritetskontroll
- Dataleverans
- Volymkontroll
- Delta levererar

>[!NOTE]
>
>Mer information finns i [Konfiguration](technical-specification.md#configuration), [Steginterna](technical-specification.md#step-internals), [Steg](technical-specification.md#step-stages) och [Körningslägen](technical-specification.md#running-modes).


Komplexa SQL-frågor kan sammanställas inuti dessa klasser för att hämta och migrera data. Dessutom ska dessa tabeller&quot;ignoreras&quot; i [mappningssteget](technical-specification.md#map-step) eftersom den söker igenom alla befintliga tabeller och försöker migrera data om de inte finns i `<ignore>` -taggen i `map.xml`-filen.

För integritetskontroll kan du definiera ytterligare en mappningsfil i filen `config.xml` för att verifiera att tabellstrukturen är som förväntat.

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

Mappningsfil `map-greatblog.xml`:

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

Integritetskontrollklassen `Vendor\Migration\Step\GreatBlog\Integrity` utökar `Migration\App\Step\AbstractIntegrity` och innehåller metoden `perform` där tabellstrukturen verifieras:

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

Därefter måste du skapa en klass för att bearbeta och spara data i Magento 2-databasen `Vendor\Migration\Step\GreatBlog\Data`:

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

I en volymklass `Vendor\Migration\Step\GreatBlog\Volume` kontrollerar vi om data har migrerats fullständigt:

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

Om du vill lägga till deltamigreringsfunktioner lägger du till en ny grupp i filen `deltalog.xml`. I `group` anger du namnet på de tabeller som måste kontrolleras för ändringar:

```xml
<groups>
    ...
    <group name="delta_greatblog">
        <document key="post_id">greatblog_post</document>
    </group>
</groups>
```

Skapa sedan `Delta`-klassen `Vendor\Migration\Step\GreatBlog\Delta` som utökar `Migration\App\Step\AbstractDelta`:

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

Efter den anpassade stegimplementeringen som anges i exemplen hämtar systemet data från den enda Magento 1-tabellen,
bearbeta den med klassen `Vendor\Migration\Step\GreatBlog\Data` och lagra data i två Magento 2-tabeller. Nya och ändrade poster levereras vid deltamigrering med klassen `Vendor\Migration\Step\GreatBlog\Delta`.

## Otillåtna tilläggsmetoder

Eftersom [!DNL Data Migration Tool] och Magento 2 utvecklas hela tiden kan befintliga steg och hanterare ändras. Vi rekommenderar att du inte åsidosätter beteendet för steg som [Mappningssteg](technical-specification.md#map-step), [URL-omskrivningssteg](technical-specification.md#url-rewrite-step) och hanterare genom att utöka deras klasser.

Vissa steg stöder inte mappning och kan inte ändras utan att koden ändras. Du kan antingen skriva ett extra steg som ändrar data i slutet av migreringen eller skapa ett [GitHub-problem](https://github.com/magento/data-migration-tool/issues) och be om en ny tilläggspunkt i det befintliga steget.
