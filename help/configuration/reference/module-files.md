---
title: Modulkonfigurationsfiler
description: Lär dig hur du anpassar en modul med hjälp av konfigurationstyper.
exl-id: 87433c28-8e3d-43d0-b77e-3ff9a680af5f
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '2024'
ht-degree: 0%

---

# Översikt över modulkonfigurationsfiler

Ansvarsområdena för `config.xml` konfigurationsfilen som används i tidigare versioner av Commerce är nu uppdelad mellan flera filer som finns i olika modulkataloger. Commerce&#39;s multiple configuration files load on demand only when a module requests a specific configuration type.

Du kan använda dessa filer - som också kallas _konfigurationstyper_- för att anpassa specifika aspekter av modulens beteende.

Flera moduler kan deklarera konfigurationsfiler som påverkar samma konfigurationstyp (till exempel händelser), och dessa flera konfigurationsfiler sammanfogas.

Här följer några vanliga termer som används i det här avsnittet:

- **Konfigurationsobjekt**- Det Commerce-bibliotek eller den klass som ansvarar för att definiera och validera konfigurationstypen. Till exempel konfigurationsobjektet för `config.xml` är [Magento\Framework\App\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/Config.php).

- **Konfigurationsfas**—Stegen definieras som _primär_, _global_ och _area_. Varje steg avgör när konfigurationstypen läses in och sammanfogas med konfigurationstyper med samma namn. Till exempel: `module.xml` filer sammanfogas med andra `module.xml` filer.

- **Konfigurationsomfattning**- Som komplement till konfigurationsfaser definierar ett omfång konfigurationsmodellen. Till exempel: `adminhtml` är ett områdesomfång som läses in med på scenen med andra moduler `adminhtml` konfigurationer. Mer information finns i [Moduler och områden](https://developer.adobe.com/commerce/php/architecture/modules/areas/).

## Inläsning och sammanfogning av konfiguration

I det här avsnittet beskrivs hur konfigurationsfiler läses in och sammanfogas.

### Hur Commerce läser in konfigurationsfiler

Konfigurationsfiler läses in i följande ordning (alla sökvägar är relativa till din Commerce-installationskatalog):

- Primär konfiguration ([app/etc/di.xml](https://github.com/magento/magento2/blob/2.4/app/etc/di.xml)). Den här filen används för att bootstrap Commerce.
- Globala konfigurationer från moduler (`<your component base dir>/<vendorname>/<component-type>-<component-name>/etc/*.xml`). Samlar in vissa konfigurationsfiler från alla moduler och sammanfogar dem.
- Områdesspecifik konfiguration från moduler (`<your component base dir>/<vendorname>/<component-type>-<component-name>/etc/<area>/*.xml`). Samlar in konfigurationsfiler från alla moduler och sammanfogar dem i den globala konfigurationen. Vissa områdesspecifika konfigurationer kan åsidosätta eller utöka den globala konfigurationen.

där

- `<your component base dir>` är baskatalogen där komponenten finns. Normala värden är `app/code` eller `vendor` i förhållande till Commerce-installationskatalogen.
- `<vendorname>` är komponentens leverantörsnamn, till exempel är Commerce-leverantörens namn `magento`.
- `<component-type>` är något av följande:

   - `module-`: Ett tillägg eller en modul.
   - `theme-`: Tema.
   - `language-`: Språkpaket.

>[!INFO]
>
>För närvarande finns teman under `<magento_root>/app/design/frontend` eller `<magento_root>/app/design/adminhtml`.

- `<component-name>`: Komponentens namn enligt definitionen i [disposition.json](https://github.com/magento/magento2/blob/2.4/composer.json).

### Sammanfogning av konfigurationsfil

Noder i konfigurationsfiler sammanfogas baserat på deras kvalificerade XPaths, som har ett särskilt attribut definierat i `$idAttributes` array som deklarerats som dess identifierare. Den här identifieraren måste vara unik för alla noder som är kapslade under samma överordnade nod.

Sammanfogningsalgoritm för Commerce-program:

- Om nodidentifierare är lika (eller om ingen identifierare har definierats) åsidosätts allt underliggande innehåll i noden (attribut, underordnade noder och skalärt innehåll).
- Om nodidentifierare inte är lika är noden en ny underordnad nod till den överordnade noden.
- Om det ursprungliga dokumentet har flera noder med samma identifierare utlöses ett fel eftersom identifierarna inte kan särskiljas.

När konfigurationsfilerna har sammanfogats innehåller det resulterande dokumentet alla noder från originalfilerna.

>[!INFO]
>
>Du kan använda [\Magento\Framework\Config\Reader\Filesystem](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/Reader/Filesystem.php) klass för felsökning och förstå logiken bakom [inläsare för konfigurationsfiler](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/Reader/Filesystem.php#L125) och [sammanfoga konfigurationer](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/Reader/Filesystem.php#L144) -processen.

## Konfigurationstyper, objekt och gränssnitt

I följande avsnitt finns information om konfigurationstyper, deras motsvarande konfigurationsobjekt och gränssnitt som du kan använda för att arbeta med objekten:

### Konfigurationstyper och objekt

I följande tabell visas varje konfigurationstyp och det Commerce-konfigurationsobjekt som den hör till.

| Konfigurationsfil | Beskrivning | Scen | Konfigurationsobjekt |
| --- | --- | --- | --- |
| `address_formats.xml` | Deklaration om adressformat | primär, global | [\Magento\Customer\Model\Address\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Customer/Model/Address/Config.php) |
| `acl.xml` | [Åtkomstkontrollista](https://developer.adobe.com/commerce/webapi/get-started/authentication/#relationship-between-aclxml-and-webapixml) | global | [\Magento\Framework\Acl\AclResource\Provider](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Acl/AclResource/Provider.php) |
| `analytics.xml` | [Avancerad rapportering](https://devdocs.magento.com/guides/v2.4/advanced-reporting/data-collection.html) | primär, global | [\Magento\Analytics\Model\Config\Reader](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Analytics/Model/Config/Reader.php) |
| `cache.xml` | Cachetypdeklaration | primär, global | [\Magento\Framework\Cache\Config\Data](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Cache/Config/Data.php) |
| `catalog_attributes.xml` | Katalogattributskonfiguration | global | [\Magento\Catalog\Model\Attribute\Config\Data](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Catalog/Model/Attribute/Config/Data.php) |
| `config.php` och `env.php` | [Distributionskonfiguration](../reference/deployment-files.md) | Dessa filer kan läsas/skrivas av den interna konfigurationsprocessorn. | Har inget objekt, kan inte anpassas |
| `config.xml` | Systemkonfiguration | primär, global | [\Magento\Framework\App\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/Config.php) |
| `communication.xml` | [Definierar aspekter av meddelandekösystemet](https://developer.adobe.com/commerce/php/development/components/message-queues/configuration/#communicationxml) | global | [\Magento\WebapiAsync\Code\Generator\Config\RemoteServiceReader\Communication](https://github.com/magento/magento2/blob/2.4/app/code/Magento/WebapiAsync/Code/Generator/Config/RemoteServiceReader/Communication.php) |
| `crontab.xml` | [Konfigurerar kundgrupper](../cron/custom-cron-reference.md#configure-cron-groups) | global | [\Magento\Cron\Model\Config\Data](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Cron/Model/Config/Data.php) |
| `cron_groups.xml` | [Anger alternativ för cron-grupp](../cron/custom-cron-reference.md) | global | [\Magento\Cron\Model\Groups\Config\Data](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Cron/Model/Groups/Config/Data.php) |
| `db_schema.xml` | [Deklarativt schema](https://developer.adobe.com/commerce/php/development/components/declarative-schema/configuration/) | global | [Magento\Framework\Setup\Declaration\Schema](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Setup/Declaration/Schema/SchemaConfig.php) |
| `di.xml` | [Beroendeinjektion](https://developer.adobe.com/commerce/php/development/components/dependency-injection/) konfiguration | primär, global, area | [\Magento\Framework\ObjectManager\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/ObjectManager/Config/Config.php) |
| `eav_attributes.xml` | Tillhandahåller konfiguration för EAV-attribut | global | [\Magento\Eav\Model\Entity\Attribute\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Eav/Model/Entity/Attribute/Config.php) |
| `email_templates.xml` | Konfiguration av e-postmallar | global | [\Magento\Email\Model\Template\Config\Data](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Email/Model/Template/Config/Data.php) |
| `esconfig.xml` | [Konfigurering av stoppord för sökmotorns språkområde](../search/search-stopwords.md#create-stopwords-for-a-new-locale) | global | [\Magento\Elasticsearch\Model\Adapter\Index\Config\EsConfig](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Elasticsearch/Model/Adapter/Index/Config/EsConfig.php) |
| `events.xml` | Konfiguration av händelse/observatör | globalt, område | [\Magento\Framework\Event](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Event.php) |
| `export.xml` | Exportera enhetskonfiguration | global | [\Magento\ImportExport\Model\Export\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/ImportExport/Model/Export/Config.php) |
| `extension_attributes.xml` | [Tillägg](https://developer.adobe.com/commerce/php/development/components/attributes/#extension-attributes) | global | [\Magento\Framework\Api\ExtensionAttribute\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Api/ExtensionAttribute/Config.php) |
| `fieldset.xml` | Definierar fältuppsättningar | global | [\Magento\Framework\DataObject\Copy\Config\Reader](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/DataObject/Copy/Config/Reader.php) |
| `indexer.xml` | [Deklarerar indexerare](https://developer.adobe.com/commerce/php/development/components/indexing/custom-indexer/) | global | [\Magento\Framework\Indexer\Config\Reader](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Indexer/Config/Reader.php) |
| `import.xml` | Deklarerar importenheter | global | [\Magento\ImportExport\Model\Import\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/ImportExport/Model/Import/Config.php) |
| `menu.xml` | Definierar menyalternativ för administratören | adminhtml | [\Magento\Backend\Model\Menu\Config\Reader](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Backend/Model/Menu/Config/Reader.php) |
| `module.xml` | Definierar modulens konfigurationsdata och mjuka beroenden | primär, global | [\Magento\Framework\Module\ModuleList\Loader](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Module/ModuleList/Loader.php) |
| `mview.xml` | [MView-konfiguration](https://developer.adobe.com/commerce/php/development/components/indexing/custom-indexer/#mview-configuration) | primär, global | [\Magento\Framework\Mview\Config\Data](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Mview/Config/Data.php) |
| `payment.xml` | Konfiguration av betalningsmodul | primär, global | [\Magento\Payment\Model\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Payment/Model/Config.php) |
| `persistent.xml` | [Magento_Beständig](https://developer.adobe.com/commerce/php/module-reference/module-persistent/) konfigurationsfil | global | [\Magento\Persistent\Helper\Data](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Persistent/Helper/Data.php) |
| `pdf.xml` | Inställningar för PDF | global | [\Magento\Sales\Model\Order\Pdf\Config\Reader](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Sales/Model/Order/Pdf/Config/Reader.php) |
| `product_options.xml` | Tillhandahåller konfiguration av produktalternativ | global | [\Magento\Catalog\Model\ProductOptions\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Catalog/Model/ProductOptions/Config.php) |
| `product_types.xml` | Definierar produkttyp | global | [\Magento\Catalog\Model\ProductTypes\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Catalog/Model/ProductTypes/Config.php) |
| `queue_consumer.xml` | [Definierar relationen mellan en befintlig kö och dess konsument](https://developer.adobe.com/commerce/php/development/components/message-queues/configuration/#queue_consumerxml) | global | [\Magento\Framework\MessageQueue\Consumer\Config\Xml\Reader](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/MessageQueue/Consumer/Config/Xml/Reader.php) |
| `queue_publisher.xml` | [Definierar det utbyte där ett ämne publiceras.](https://developer.adobe.com/commerce/php/development/components/message-queues/configuration/#queue_publisherxml) | global | [\Magento\WebapiAsync\Code\Generator\Config\RemoteServiceReader\Publisher](https://github.com/magento/magento2/blob/2.4/app/code/Magento/WebapiAsync/Code/Generator/Config/RemoteServiceReader/Publisher.php) |
| `queue_topology.xml` | [Definierar regler för meddelandedirigering, deklarerar köer och utbyten](https://developer.adobe.com/commerce/php/development/components/message-queues/configuration/#queue_topologyxml) | global | [\Magento\Framework\MessageQueue\Topology\Config\Xml\Reader](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/MessageQueue/Topology/Config/Xml/Reader.php) |
| `reports.xml` | [Avancerade rapporter](https://devdocs.magento.com/guides/v2.4/advanced-reporting/report-xml.html) | global | [\Magento\Analytics\ReportXml\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Analytics/ReportXml/Config.php) |
| `resources.xml` | Definierar modulresurs | global | [\Magento\Framework\App\ResourceConnection\Config\Reader](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/ResourceConnection/Config/Reader.php) |
| `routes.xml` | [Flöde](https://developer.adobe.com/commerce/php/development/components/routing/) konfiguration | area | [Magento\Framework\App\Route\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/Route/Config.php) |
| `sales.xml` | Definierar total konfiguration för försäljning | global | [\Magento\Sales\Model\Config\Data](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Sales/Model/Config/Data.php) |
| `search_engine.xml` | Tillhandahåller sökmotorkonfiguration | global | [Magento\Search\Model\SearchEngine\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Search/Model/SearchEngine/Config.php) |
| `search_request.xml` | Definierar katalogsökningskonfiguration | global | [\Magento\Framework\Search\Request\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Search/Request/Config.php) |
| `sections.xml` | Definierar åtgärder som utlöser cacheogiltigförklaring för privata innehållsblock | frontend | [SectionInvalidationConfigReader](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Customer/etc/di.xml#L137-L148) |
| `system.xml` | Definierar alternativ för sidan för systemkonfiguration | adminhtml | [\Magento\Framework\App\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/Config.php) |
| `validation.xml` | Konfigurationsfil för modulvalidering | global | [\Magento\Framework\Validator\Factory](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Validator/Factory.php) |
| `view.xml` | Definierar visningskonfigurationsvärden för Vendor_Module | global | [\Magento\Framework\View\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/View/Config.php) |
| `webapi.xml` | [Konfigurerar ett webb-API](https://developer.adobe.com/commerce/php/development/components/web-api/services/) | global | [\Magento\Webapi\Model\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Webapi/Model/Config.php) |
| `webapi_async.xml` | [Definierar egna REST-vägar](https://developer.adobe.com/commerce/php/development/components/web-api/custom-routes/) | global | [\Magento\WebapiAsync\Model\ServiceConfig](https://github.com/magento/magento2/blob/2.4/app/code/Magento/WebapiAsync/Model/ServiceConfig.php) |
| `widget.xml` | Definierar widgetar | global | [\Magento\Widget\Model\Config\Reader](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Widget/Model/Config/Reader.php) |
| `zip_codes.xml` | Definierar postnummerformat för varje land | global | [\Magento\Directory\Model\Country\Postcode\Config\Data](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Directory/Model/Country/Postcode/Config/Data.php) |

### Konfigurationsgränssnitt

Du kan interagera med konfigurationsfiler via gränssnitt under [Magento\Framework\Config](https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/Config).

Du kan använda dessa gränssnitt om du [skapa en konfigurationstyp](../reference/config-create-types.md#create-configuration-types).

`Magento\Framework\Config` innehåller följande gränssnitt:

- [Framework\Config\ConverterInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/ConverterInterface.php), som konverterar XML till en minnesbaserad arrayrepresentation av konfigurationerna.
- [Framework\Config\DataInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/DataInterface.php), som hämtar konfigurationsdata i ett angivet omfång.
- [Framework\Config\FileResolverInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/FileResolverInterface.php), som identifierar platsen för filer som ska läsas av [Magento\Framework\Config\ReaderInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/ReaderInterface.php).
- [Framework\Config\ReaderInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/ReaderInterface.php), som läser konfigurationsdata från lagring och väljer det lagringsutrymme som det läser från.

Det vill säga, filsystemet, databasen, annan lagring, sammanfogar konfigurationsfilerna enligt sammanfogningsreglerna och validerar konfigurationsfilerna med valideringsscheman.

- [Framework\Config\SchemaLocatorInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/SchemaLocatorInterface.php), som hittar XSD-schemat.
- [Framework\Config\ScopeListInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/ScopeListInterface.php), som returnerar en lista med omfattningar.
- [Framework\Config\ValidationStateInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/ValidationStateInterface.php), som hämtar valideringstillståndet.
