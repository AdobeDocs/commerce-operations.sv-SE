---
title: Konfigurationstyper
description: Skapa eller utöka konfigurationstyper.
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '597'
ht-degree: 0%

---


# Konfigurationstyper

## Utöka konfigurationstyper

Om du vill utöka en befintlig konfigurationstyp behöver du bara skapa en konfigurationsfil i [modul](https://glossary.magento.com/module).

Om du till exempel vill lägga till en händelseobservatör skapar du `app/code/{VendorName}/{ModuleName}/etc/events.xml` och deklarera en ny observatör.

Eftersom händelskonfigurationstypen finns i Commerce, inläsaren och `events.xsd` det finns redan ett valideringsschema som kan valideras.

Dina nya `events.xml` samlas automatiskt in från modulen och sammanfogas med andra `events.xml` filer för andra moduler.

## Skapa konfigurationstyper

Om du vill skapa en konfigurationstyp måste du lägga till minst:

- En inläsare
- XSD-valideringsschema
- XML-konfigurationsfiler

Om du till exempel vill infoga en [adapter](https://glossary.magento.com/adapter) Om du vill ha en ny sökserver som tillåter tillägg att konfigurera hur entiteterna indexeras på den servern skapar du:

- En inläsare
- En XSD-schemafil
- En konfigurationsfil med rätt namn. Exempel, `search.xml`. Den här filen läses och valideras mot ditt schema.
- Andra klasser som krävs för ditt arbete.

>[!INFO]
>
>Om nya moduler har en `search.xml` så sammanfogas de med filen när den läses in.

### Exempel på användning

Så här skapar du en konfigurationstyp:

1. Skapa XSD-filen.
1. Skapa en XML-fil.
1. Definiera konfigurationsobjektet i `di.xml`.

   Följande exempel från modulen Magento_Sales [di.xml](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Sales/etc/di.xml) visar hur ett konfigurationsobjekt ska se ut.

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

   - Den första typnoden anger Reader filnamn, associerat `Converter` och `SchemaLocator` klasser.
   - Sedan `pdfConfigDataStorage` virtuell typnod kopplar klassen reader till en instans av [Magento\Framework\Config\Data](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/Data.php).
   - Slutligen kopplar den sista typnoden den den virtuella typen för config data till [Magento\Sales\Model\Order\Pdf\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Sales/Model/Order/Pdf/Config.php) -klass, som används för att faktiskt läsa värden i [pdf.xml](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Sales/etc/pdf.xml) filer.

1. Definiera en läsare genom att utöka [Magento\Framework\Config\Reader\Filesystem](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/Reader/Filesystem.php) och skriva om följande parametrar:

   ```php
   $_idAttributes // Array of node attribute IDs.
   ```

**Exempel:**

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
>Om du föredrar att skapa en egen version av läsaren kan du göra det genom att implementera `\Magento\Framework\Config\ReaderInterface`. Se [Magento_Analytics, konfigurationsläsare](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Analytics/ReportXml/Config/Reader.php)

När du har definierat läsaren kan du använda den för att samla in, sammanfoga, validera och konvertera konfigurationsfilerna till en intern arrayrepresentation.

## Validera en konfigurationstyp

Varje konfigurationsfil valideras mot ett schema som är specifikt för dess konfigurationstyp. Exempel: händelser som i tidigare versioner av Commerce konfigurerats i `config.xml`är nu konfigurerade i `events.xml`.

Konfigurationsfiler kan valideras både före (valfritt) och efter varje sammanfogning av flera filer som påverkar samma konfigurationstyp. Om inte verifieringsreglerna för de enskilda och sammanfogade filerna är identiska, bör du ange två scheman för validering av konfigurationsfilerna:

- Schema för att validera en enskild person
- Schema för att validera en sammanfogad fil

Nya konfigurationsfiler måste åtföljas av XSD-valideringsscheman. En XML-konfigurationsfil och dess XSD-valideringsfil måste ha samma namn.

Om du måste använda två XSD-filer för en enda XML-fil, bör schemanamnen vara identifierbara och associerade med XML-filen.
Om du har en `events.xml` och en första `events.xsd` -filen, XSD-filerna för den sammanfogade filen `events.xml` filen kan ha ett namn `events_merged.xsd`.
För att XML-filen ska kunna valideras med en lämplig XSD-fil måste du lägga till URN (Uniform Resource Name) i XSD-filen i XML-filen. Exempel:

```xml
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:ObjectManager:etc/config.xsd">
```

IDE:n kan validera konfigurationsfilerna både under körning och utveckling.
