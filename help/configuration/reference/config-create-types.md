---
title: Konfigurationstyper
description: Skapa eller utöka konfigurationstyper.
exl-id: 4390c310-b35a-431a-859f-3fd46d8ba6bf
source-git-commit: 4116d0983edc797ce42d24e711fb5ecdbf8fdec9
workflow-type: tm+mt
source-wordcount: '525'
ht-degree: 0%

---

# Konfigurationstyper

## Utöka konfigurationstyper

Om du vill utöka en befintlig konfigurationstyp behöver du bara skapa en konfigurationsfil i modulen.

Om du till exempel vill lägga till en händelseobservatör skapar du `app/code/{VendorName}/{ModuleName}/etc/events.xml` och deklarerar en ny observatör.

Eftersom händelskonfigurationstypen finns i Commerce finns redan inläsaren och det `events.xsd`-valideringsschemat och fungerar.

Din nya `events.xml` samlas automatiskt in från din modul och sammanfogas med andra `events.xml`-filer för andra moduler.

## Skapa konfigurationstyper

Om du vill skapa en konfigurationstyp måste du lägga till minst:

- En inläsare
- XSD-valideringsschema
- XML-konfigurationsfiler

Om du till exempel vill lägga till ett kort för en ny sökserver som gör att tillägg kan konfigurera hur entiteterna indexeras på den servern, skapar du:

- En inläsare
- En XSD-schemafil
- En konfigurationsfil med rätt namn. Exempel: `search.xml`. Den här filen läses och valideras mot ditt schema.
- Andra klasser som krävs för ditt arbete.

>[!INFO]
>
>Om nya moduler har en `search.xml`-fil sammanfogas de med din fil när den läses in.

### Exempel på användning

Så här skapar du en konfigurationstyp:

1. Skapa XSD-filen.
1. Skapa en XML-fil.
1. Definiera konfigurationsobjektet i `di.xml`.

   Följande exempel från Magento_Sales-modulens [di.xml](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Sales/etc/di.xml) visar hur ett konfigurationsobjekt ska se ut.

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

   - Den första typnoden anger Reader filnamn, associerade klasserna `Converter` och `SchemaLocator`.
   - Sedan kopplar den virtuella typnoden `pdfConfigDataStorage` läsarklassen till en instans av [Magento\Framework\Config\Data](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/Data.php).
   - Slutligen kopplar den sista typnoden den den virtuella typen för config data till klassen [Magento\Sales\Model\Order\Pdf\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Sales/Model/Order/Pdf/Config.php), som används för att läsa värden i dessa [pdf.xml](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Sales/etc/pdf.xml) -filer.

1. Definiera en läsare genom att utöka klassen [Magento\Framework\Config\Reader\Filesystem](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/Reader/Filesystem.php) och skriva om följande parametrar:

   ```php
   $_idAttributes // Array of node attribute IDs.
   ```

**Exempel:**

```php
<?php
/**
 * Copyright [first year code created] Adobe
 * All Rights Reserved.
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

Varje konfigurationsfil valideras mot ett schema som är specifikt för dess konfigurationstyp. Exempel: händelser som i tidigare versioner av Commerce konfigurerades i `config.xml` har nu konfigurerats i `events.xml`.

Konfigurationsfiler kan valideras både före (valfritt) och efter varje sammanfogning av flera filer som påverkar samma konfigurationstyp. Om inte verifieringsreglerna för de enskilda och sammanfogade filerna är identiska, bör du ange två scheman för validering av konfigurationsfilerna:

- Schema för att validera en enskild person
- Schema för att validera en sammanfogad fil

Nya konfigurationsfiler måste åtföljas av XSD-valideringsscheman. En XML-konfigurationsfil och dess XSD-valideringsfil måste ha samma namn.

Om du måste använda två XSD-filer för en enda XML-fil, bör schemanamnen vara identifierbara och associerade med XML-filen.
Om du har en `events.xml`-fil och en första `events.xsd`-fil kan XSD-filerna för den sammanfogade `events.xml`-filen heta `events_merged.xsd`.
För att XML-filen ska kunna valideras med en lämplig XSD-fil måste du lägga till URN (Uniform Resource Name) i XSD-filen i XML-filen. Exempel:

```xml
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:ObjectManager:etc/config.xsd">
```

IDE:n kan validera konfigurationsfilerna både under körning och utveckling.
