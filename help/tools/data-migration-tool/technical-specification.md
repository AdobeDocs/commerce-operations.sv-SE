---
title: '[!DNL Data Migration Tool] teknisk specifikation'
description: Lär dig mer om implementeringsinformationen för  [!DNL Data Migration Tool]  och hur du utökar när du överför data mellan Magento 1 och Magento 2.
exl-id: fec3ac3a-dd67-4533-a29f-db917f54d606
topic: Commerce, Migration
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '2098'
ht-degree: 0%

---

# [!DNL Data Migration Tool] teknisk specifikation

I det här avsnittet beskrivs [!DNL Data Migration Tool]-implementeringsinformation och hur du utökar funktionaliteten.

## Databaser

Mer information om hur du kommer åt [!DNL Data Migration Tool]-källkoden finns i GitHub [databasen](https://github.com/magento/data-migration-tool).

## Systemkrav

[systemkraven](../../installation/system-requirements.md) för [!DNL Data Migration Tool] är desamma som för Magento 2.

## Intern struktur

### Katalogstruktur

Följande diagram representerar katalogstrukturen för [!DNL Data Migration Tool]:

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

## Startpunkt

Skriptet som kör migreringsprocessen finns på: `magento-root/bin/magento`.

## Konfiguration

Schemat för konfigurationsfilen `config.xsd` finns i katalogen `etc/`. Standardkonfigurationsfilen (`config.xml.dist`) skapas för varje version av Magento 1.x. Den finns i en separat katalog under `etc/` .

Standardkonfigurationsfilen kan ersättas med en anpassad fil (se [kommandosyntax](migrate-data/overview.md#command-syntax)).

Konfigurationsfilen har följande struktur:

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

* steg - beskriver alla steg som bearbetas under migreringen

* source - konfiguration för datakälla. Tillgängliga källtyper: databas

* mål - konfiguration för datamål. Tillgängliga måltyper: databas

* options - list of parameters. Innehåller både obligatoriska (map_file, settings_map_file, bulk_size) och valfria (custom_option, resource_adapter_class_name, prefix_source, prefix_dest, log_file) parametrar

Ändra prefixalternativet om Magento har installerats med prefix i databastabeller. Den kan ställas in för Magento 1- och Magento 2-databaser. Använd konfigurationsalternativen &quot;source_prefix&quot; och &quot;dest_prefix&quot; i enlighet därmed.

Konfigurationsdata är tillgängliga med klassen `\Migration\Config`.

## Åtgärder som är tillgängliga

| Dokument | Fält |
|---|---|
| `step` | Nod på andra nivån inuti noden Steps. Beskrivning av det relevanta steget måste anges i attributet `title`. |
| `integrity` | Anger den PHP-klass som ansvarar för integritetskontrollen. Jämför tabellfältets namn, typer och annan information för att verifiera kompatibiliteten mellan datastrukturen Magento 1 och 2. |
| `data` | Anger den PHP-klass som är ansvarig för datakontrollen. Överför data, tabell för tabell från Magento 1 till Magento 2. |
| `volume` | Anger den PHP-klass som ansvarar för volymkontrollen. Jämför antalet poster mellan tabeller för att verifiera att överföringen lyckades. |
| `delta` | Anger den PHP-klass som är ansvarig för deltakontrollen. Överför delta från Magento 1 till Magento 2 efter fullständig datamigrering. |

## Source databasinformationsattribut

| Dokument | Fält | Obligatoriskt? |
|---|---|---|
| `name` | Databasnamn för Magento 1-servern. | ja |
| `host` | Värdserverns IP-adress. | ja |
| `port` | Portnummer för Magento 1-servern. | no |
| `user` | Användarnamn för Magento 1-databasservern. | ja |
| `password` | Lösenord för Magento 1-databasservern. | ja |
| `ssl_ca` | Sökväg till filen för SSL-certifikatutfärdare. | no |
| `ssl_cert` | Sökväg till SSL-certifikatfil. | no |
| `ssl_key` | Sökväg till SSL-nyckelfil. | no |

## Informationsattribut för måldatabas

| Dokument | Fält | Obligatoriskt? |
|---|---|---|
| `name` | Databasnamn för Magento 2-servern. | ja |
| `host` | Värdserverns IP-adress. | ja |
| `port` | Portnummer för Magento 2-servern. | no |
| `user` | Användarnamn för Magento 2-databasservern. | ja |
| `password` | Lösenord för Magento 2-databasservern. | ja |
| `ssl_ca` | Sökväg till filen för SSL-certifikatutfärdare. | no |
| `ssl_cert` | Sökväg till SSL-certifikatfil. | no |
| `ssl_key` | Sökväg till SSL-nyckelfil. | no |

## Anslut med TLS-protokollet

Du kan också ansluta till en databas med TLS-protokollet (dvs. med offentliga/privata kryptografiska nycklar). Lägg till följande valfria attribut i elementet `database`:

* `ssl_ca`
* `ssl_cert`
* `ssl_key`

Exempel:

```xml
<source>
    <database host="localhost" name="magento1" user="root" ssl_ca="/path/to/file" ssl_cert="/path/to/file" ssl_key="/path/to/file"/>
</source>
<destination>
    <database host="localhost" name="magento2" user="root" ssl_ca="/path/to/file" ssl_cert="/path/to/file" ssl_key="/path/to/file"/>
</destination>
```

## Stega interna

Migreringsprocessen består av steg.

Steg är en enhet som tillhandahåller de funktioner som krävs för att migrera vissa separerade data. Steget kan bestå av ett eller flera steg (integritetskontroll, data, volymkontroll och delta).

Som standard finns det flera steg ([Map](#map-step), [EAV](#eav), [URL Rewrites](#url-rewrite-step) och så vidare). Du kan även lägga till egna steg.

Steg relaterade klasser finns i katalogen src/Migration/Step.

Om du vill köra en Step-klass måste klassen definieras i filen config.xml.

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

Alla scenklasser måste implementera StageInterface.

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

Om datastadien stöder återställning bör gränssnittet `RollbackInterface` implementeras.

Visualisering av det pågående steget tillhandahålls av Symfonys ProgressBar-komponent (se [Progress bar](https://symfony.com/doc/current/components/console/helpers/progressbar.html)). Kom åt den här komponenten i ett steg som LogLevelProcessor.

De viktigaste användningsmetoderna är:

```xml
$this->progress->start();
$this->progress->advance();
$this->progress->finish();
```

## Steg i steg

### Integritetskontroll

Varje steg måste kontrollera att strukturen för datakällan (Magento 1 som standard) och strukturen för datamålet (Magento 2) är kompatibla. Annars visas ett fel med enheter som inte är kompatibla. Om fälten har olika datatyper (samma fält har en decimaldatatyp i Magento 1 och ett heltal i Magento 2) visas ett varningsmeddelande (förutom när det fanns med i kartfilen).

### Dataöverföring

Om integritetskontrollen skickas körs data. Om fel uppstår går återställningen tillbaka till det tidigare läget i Magento 2. Om en stegklass implementerar gränssnittet `RollbackInterface` körs återställningsmetoden när ett fel uppstår.

### Volymkontroll

När data har migrerats kan du med volymkontrollen kontrollera att alla data har överförts korrekt.

### Delta-leverans

Delta-funktionaliteten ansvarar för att leverera resten av data som lagts till efter huvudmigreringen.

## Körningslägen

Verktyget ska köras i tre olika lägen i särskild ordning:

1. inställningar - migrering av systeminställningar
1. data - huvudmigrering av data
1. delta - migrering av resten av data som lagts till efter huvudmigreringen

Varje läge har en egen lista över steg som ska köras. Se config.xml

### Migreringsläge för inställningar

Inställningsmigreringsläget för det här verktyget används för att överföra följande enheter:

1. Webbplatser, butiker, butiksvyer.
1. Konfiguration för butik (huvudsakligen Lager->Konfiguration i M2 eller System->Konfiguration i M1)

All butikskonfiguration sparar data i tabellen core_config_data i databasen. filen settings.xml innehåller regler för den här tabellen som tillämpas under migreringsprocessen. Den här filen beskriver inställningar som ska ignoreras, namnändras eller som ska ändra deras värden. filen settings.xml har följande struktur:

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

Under noden `<key>` finns det regler som fungerar med kolumnen path i tabellen `core_config_data`. `<ignore>`-regler hindrar verktyget från att överföra vissa inställningar. Jokertecken kan användas i den här noden. Alla andra inställningar som inte finns med i noden `<ignore>` migreras. Om sökvägen till en inställning har ändrats i Magento 2 bör den läggas till i noden `//key/rename`, där den gamla sökvägen anges i noden `//key/rename/path` och den nya sökvägen anges i noden `//key/rename/to`.

Under noden `<value>` finns det regler som fungerar med kolumnen &#39;value&#39; i tabellen `core_config_data`. Dessa regler syftar till att omforma inställningsvärden av hanterare (klasser som implementerar `Migration\Handler\HandlerInterface`) och anpassa dem för Magento 2.

### Datamigreringsläge

I det här läget migreras merparten av data. Före datamigrering körs integritetskontrollens faser för varje steg. Om integritetskontrollen lyckas installerar [!DNL Data Migration Tool] deltalogtabeller (med prefix `m2_cl_*`) och motsvarande utlösare till Magento 1-databasen och kör steg för datamigrering. När migreringen är klar utan fel kontrollerar volymkontrollen datakonsekvensen. Det kan visa ett varningsmeddelande om du migrerar livebutiken. Oroa dig inte. Deltamigreringen tar hand om dessa inkrementella data. De mest värdefulla migreringsstegen är Karta, URL-omskrivning och EAV.

#### Kartsteg

Kartsteget ansvarar för att överföra merparten av data från Magento 1 till Magento 2. Det här steget läser instruktioner från filen map.xml (finns i katalogen `etc/`). Filen beskriver skillnader mellan datastrukturer för källan (Magento 1) och målet (Magento 2). Om Magento 1 innehåller tabeller eller fält som tillhör ett tillägg som inte finns i Magento 2, kan de här entiteterna placeras här för att ignorera dem i Kartsteg. Annars visas ett felmeddelande.

Kartfilen har nästa format:

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

Områden:

* *källa* - innehåller regler för källdatabasen

* *mål* - innehåller regler för måldatabasen

Alternativ:

* *ignorera* - dokument, fält eller datatyp som markerats med det här alternativet ignoreras

* *rename* - beskriver namnrelationer mellan dokument med ett annat namn. Om måldokumentnamnet inte är detsamma som källdokumentet kan du använda alternativet Byt namn för att ange ett källdokumentnamn som liknar måltabellens namn

* *move* - anger att regeln ska flytta angivet fält från källdokumentet till måldokumentet. Obs! Måldokumentets namn måste vara detsamma som källdokumentets namn. Om käll- och måldokumentnamnen är olika - du måste använda alternativet Byt namn för dokument som innehåller flyttade fält

* *transform* - är ett alternativ som gör att användaren kan migrera fält enligt det beteende som beskrivs i hanterare

* *handler* - beskriver omformningsbeteendet för fält. Om du vill anropa hanteraren måste du ange ett hanterarklassnamn i en `<handler>`-tagg. Använd taggen `<param>` med parameternamn och värdedata för att skicka den till hanteraren

**Source** tillgängliga åtgärder:

| Dokument | Fält |
|--- |--- |
| ignorera namnändring | ignorera flyttningsomformning |

**Mål** tillgängliga åtgärder:

| Dokument | Fält |
|--- |--- |
| ignorera | ignorera omformning |

#### Jokertecken

Om du vill ignorera dokument med liknande delar (`document_name_1`, `document_name_2`) kan du använda jokerteckenfunktioner. Placera `*`-symbolen i stället för den upprepade delen (`document_name_*`) så täcker den här masken alla käll- eller måldokument som uppfyller den här masken.

#### Omskrivningssteg för URL

Det här steget är komplext eftersom det finns många olika algoritmer som utvecklats i Magento 1 som inte är kompatibla med Magento 2. För olika versioner av Magento 1 kan det finnas olika algoritmer. I mappen Step/UrlRewrite finns det klasser som utvecklats för vissa versioner av Magento och Migration\Step\UrlRewrite\Version191to2000 är en av dem. Den kan överföra data från Magento 1.9.1 till Magento 2.

#### EAV-steg

I det här steget överförs alla attribut (product, customer, RMA) från Magento 1 till Magento 2. Den använder filen map-eav.xml som innehåller regler som liknar de i filen map.xml för specifika fall av databearbetning.

Några av tabellerna som bearbetas i steget:

* `eav_attribute`
* `eav_attribute_group`
* `eav_attribute_set`
* `eav_entity_attribute`
* `catalog_eav_attribute`
* `customer_eav_attribute`
* `eav_entity_type`

### Delta-migreringsläge

Efter huvudmigreringen kunde ytterligare data ha lagts till i Magento 1-databasen (t.ex. av kunder på butiken). För att spåra dessa data anger verktyget databasutlösarna för tabeller i början av migreringsprocessen. Mer information finns i [Migrera data som skapats av tillägg från tredje part](migrate-data/delta.md#migrate-data-created-by-third-party-extensions).

## Datakällor

Det finns många klasser i resursmappen för att nå datakällorna i Magento 1 och Magento 2 och arbeta med data för dem (markera, uppdatera, infoga, ta bort). Migration\ResourceModel\Source and Migration\ResourceModel\Destination är huvudklasser. Alla migreringssteg använder den för att hantera data. Dessa data finns i klasser som Migration\ResourceModel\Document, Migration\ResourceModel\Record, Migration\ResourceModel\Structure osv.

Här följer ett klassdiagram över dessa klasser:

![Datastruktur för migreringsverktyg](../../assets/data-migration/MmigrationToolDataStructure.png)

## Loggning

För att implementera utdata från migreringsprocessen och kontrollera alla möjliga nivåer används PSR-loggaren, som används i Magento. Klassen `\Migration\Logger\Logger` implementerades för att tillhandahålla loggningsfunktioner. För att använda loggningsfunktionen ska du injicera den via en konstruktorberoendeinjektion.

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

Därefter kan du använda den här klassen för att logga vissa händelser:

```php
$this->logger->info("Some information message");
$this->logger->debug("Some debug message");
$this->logger->error("Message about error operation");
$this->logger->warning("Some warning message");
```

Det finns en möjlighet att anpassa var logginformation ska skrivas. Du kan göra det genom att lägga till hanterare i loggaren med hjälp av metoden pushHandler() i loggningsfunktionen. Varje hanterare ska implementera gränssnittet `\Monolog\Handler\HandlerInterface`. För närvarande finns det två hanterare:

* ConsoleHandler: skriver meddelanden till konsolen

* FileHandler: skriver meddelanden till loggfilen som har angetts i konfigurationsalternativet &quot;log_file&quot;

Det går även att implementera ytterligare hanterare. Det finns en uppsättning hanterare i Magento Framework. Exempel på hur du lägger till hanterare i loggaren:

```php
// $this->consoleHandler is the object of Migration\Logger\ConsoleHandler class
// $this->logger is the object of Migration\Logger\Logger class
$this->logger->pushHandler($this->consoleHandler);
```

Om du vill ange ytterligare data för loggare (aktuellt läge, tabellnamn) kan du använda loggbehandlare. Det finns en befintlig processor (MessageProcessor). Den skapas för att lägga till&quot;extra&quot; data för loggningsmeddelanden och anropas varje gång loggmetoden körs. MessageProcessor har skyddad $extra var, som innehåller tomma värden för mode, stage, step och table. Extra data kan skickas till processorn som en andra parameter (context) för loggmetoden. För närvarande finns ytterligare datauppsättningar för processorn i metoden AbstractStep->runStage (skicka aktuellt läge, scen och steg till processor) och dataklasser där logger->debug-metoden (skicka migrerande tabellnamn) används. Exempel på hur du lägger till processorer i loggaren:

```php
// $this->processoris the object of Migration\Logger\messageProcessor class
// $this->logger is the object of Migration\Logger\Logger class
$this->logger->pushProcessor([$this->processor, 'setExtra']);
// As a second array value you need to pass method that should be executed when processor called
```

Det finns en möjlighet att ange nivån på den utförliga färgen. För närvarande finns det tre nivåer:

* `ERROR` (skriver endast fel i loggen)
* `INFO` (endast viktig information skrivs till loggen, standardvärde)
* `DEBUG` (allt är skrivet)

Du kan ange utförlighetsloggnivån för varje hanterare separat genom att anropa metoden `setLevel()`. Om du vill ställa in intensitetsnivån via kommandoradsparametern bör du ändra &#39;utförlig&#39;-alternativet när programmet startas.

Du kan formatera loggmeddelanden med monologgformateraren. Om du vill att formateringsfunktionen ska fungera måste du ange logghanteraren med metoden `setFormatter()`. För närvarande har vi en formateringsklass (`MessageFormatter`) som anger ett visst format (beroende på utförlighetsnivå) under meddelandehantering (via metoden `format()` som körs från hanteraren).

Hantering av loggaren (tillägg av hanterare och processorer) och bearbetning i utförligt läge utförs i metoden `process()` i klassen `Migration\Logger\Manager`. Metoden anropas när programmet startas.

## Automatiska tester

Det finns tre typer av tester i [!DNL Data Migration Tool]:

* Statisk
* Enhet
* Integrering

De finns i verktygets `tests/`-katalog, som är samma typ av test (enhetstester finns i `tests/unit`-katalogen). Om du vill starta testet bör du ha phpunit installerat. Ändra den aktuella katalogen till testkatalogen och starta phpunit. Exempel:

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
