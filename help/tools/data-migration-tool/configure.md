---
title: Konfigurera  [!DNL Data Migration Tool]
description: Lär dig mer om de två metoderna för att konfigurera  [!DNL Data Migration Tool]  för överföring av data mellan Magento 1 och Magento 2.
exl-id: 273be997-8085-4488-a455-f6005a85b406
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '808'
ht-degree: 0%

---

# Konfigurera [!DNL Data Migration Tool]

När du har installerat [!DNL Data Migration Tool] innehåller följande katalog mappnings- och konfigurationsfiler:

* Magento Open Source:
   * `<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/opensource-to-opensource`: Konfiguration och skript för migrering från Magento Open Source 1 till Magento Open Source 2

* Adobe Commerce:
   * `<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/opensource-to-commerce`: Konfiguration och skript för migrering från Magento Open Source 1 till Adobe Commerce 2
   * `<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/commerce-to-commerce`: Konfiguration och skript för migrering från Adobe Commerce 1 till Adobe Commerce 2

Föregående kataloger innehåller underkataloger för varje version som stöds.

## Konfigurera migreringen

Det finns två sätt att konfigurera [!DNL Data Migration Tool]:

* Konfigurera [!DNL Data Migration Tool] i en separat modul (rekommenderas)
* Ändra [!DNL Data Migration Tool]-konfigurationen i katalogen `<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/`.

Om du vill använda källkontroll för att hantera din migreringskonfiguration och använda den för distribution måste du skapa en separat modul.
Om du bara tänker köra [!DNL Data Migration Tool] lokalt kan du redigera filer direkt i katalogen `<your Magento 2 install dir>/vendor/magento/data-migration-tool/`.

### Konfigurera migrering i en separat modul

Innan du migrerar några data måste du skapa en Magento 2-modul.

1. Skapa en Magento 2-modul.

   * `<your Magento 2 install dir>/app/code/Vendor/Migration/composer.json`

   ```json
   {
       "name": "vendor/migration",
       "description": "Providing config for migration",
       "config": {
           "sort-packages": true
       },
       "require": {
           "magento/framework": "*",
           "magento/data-migration-tool": "*"
       },
       "type": "magento2-module",
       "autoload": {
           "files": [
               "registration.php"
           ],
           "psr-4": {
               "Vendor\\Migration\\": ""
           }
       },
       "version": "1.0.0"
   }
   ```

   * `<your Magento 2 install dir>/app/code/Vendor/Migration/registration.php`

   ```php
   <?php
   
   \Magento\Framework\Component\ComponentRegistrar::register(
       \Magento\Framework\Component\ComponentRegistrar::MODULE,
       'Vendor_Migration',
       __DIR__
   );
   ```

   * `<your Magento 2 install dir>/app/code/Vendor/Migration/etc/module.xml`

   ```xml
   <?xml version="1.0"?>
   
   <config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
           xsi:noNamespaceSchemaLocation="urn:magento:framework:Module/etc/module.xsd">
       <module name="Vendor_Migration" setup_version="1.0.0">
           <sequence>
               <module name="Magento_DataMigrationTool"/>
           </sequence>
       </module>
   </config>
   ```

1. Kopiera konfigurationsfilen `config.xml.dist` från lämplig katalog för [!DNL Data Migration Tool] (`<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/<migration edition>/<ce or version>`) till filen `<your Magento 2 install dir>/app/code/Vendor/Migration/etc/<migration edition>/<ce or version>/config.xml`.

   Om du till exempel migrerar `Magento 1.9.3.6 Community Edition` till `Magento 2 Open Source`:

   ```bash
   cd <your Magento 2 install dir>
   ```

   ```bash
   cp vendor/magento/data-migration-tool/etc/opensource-to-opensource/1.9.3.6/config.xml.dist app/code/Vendor/Migration/etc/opensource-to-opensource/1.9.3.6/config.xml
   ```

1. I filen `config.xml` måste du ange åtkomstinformation till M1- och M2-databaser och krypteringsnyckel.

1. Om din M1-butik har anpassade ändringar bör du mappa resten av konfigurationsfilerna till dina anpassningar för Magento 1-butiken. Se [Arbeta med konfigurations- och mappningsfiler](#migration-config).

### Konfigurera migrering i mappen `vendor`

Innan du migrerar några data måste du skapa en `config.xml`-konfigurationsfil från det angivna exemplet.

Så här konfigurerar du [!DNL Data Migration Tool] för migrering:

1. Logga in på programservern som, eller växla till, ägare av [filsystemet](../../installation/prerequisites/file-system/overview.md).

1. Byt till följande katalog:

   ```bash
   <your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/<migration edition>/<ce or version>
   ```

1. Ange följande kommando för att skapa en `config.xml` från det angivna exemplet:

   ```bash
   cp config.xml.dist config.xml
   ```

1. Öppna `config.xml` i en textredigerare.

1. Filen config.xml måste minst innehålla åtkomstinformation till M1- och M2-databaser och krypteringsnycklar.

   ```xml
   <source>
      <database host="127.0.0.1" name="magento1" user="root"/>
   </source>
   <destination>
      <database host="127.0.0.1" name="magento2" user="root"/>
   </destination>
   <options>
      <crypt_key />
   </options>
   ```

   Taggen &lt;crypt_key> måste innehålla ett värde. Du kan hitta den inuti taggen `<key>`, som finns i app/etc/local.xml-filen på Magento 1-instansen.

   Valfria parametrar:

   * Användarlösenord för databas: `password=<password>`
   * Anpassad databasport: `port=<port>`
   * Tabellprefix: `<source_prefix>`, `<dest_prefix>`

   Om databasägarens användarnamn till exempel är `root` med lösenordet `pass` och du använder prefixet `magento1` i din Magento 1-databas använder du följande i `config.xml`:

   ```xml
   <source>
      <database host="127.0.0.1" name="magento1" user="root" password="pass"/>
   </source>
   <destination>
      <database host="127.0.0.1" name="magento2" user="root" password="pass"/>
   </destination>
   <options>
      <source_prefix>magento1</source_prefix>
      <crypt_key>f3e25abe619dae2387df9fs594f01985</crypt_key>
   </options>
   ```

När du är klar sparar du ändringarna i `config.xml` och avslutar textredigeraren.

### Anslut med TLS-protokollet

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

## Arbeta med konfigurations- och mappningsfiler

[!DNL Data Migration Tool] använder *mappningsfiler* för att du ska kunna utföra anpassad databasmappning mellan Magento 1- och Magento 2-databaser, inklusive:

* Ändra tabellnamn

* Ändra fältnamn

* Ignorerar tabeller eller fält

* Anpassa överföring av data från ett fält till Magento 2-format

Mappningsfiler för Magento-versioner som stöds finns i underkataloger till `<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc`

Så här använder du mappningsfilerna:

1. Kopiera dem från `<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/<migration edition>/<ce or version>/` till `<your Magento 2 install dir>/app/code/Vendor/Migration/etc/<migration edition>/<ce or version>/` och ta bort tillägget `.dist`.

1. Uppdatera sökvägen till den nyligen kopierade filen i noden `<options>` i `config.xml`. Den uppdaterade sökvägen ska vara någon av följande:

   1. Absolut filsökväg, t ex `/var/www/html/app/code/Vendor/Migration/etc/opensource-to-opensource/1.9.4.1/map.xml`
   1. modulen magento/data-migration-tool relativ filsökväg: `etc/opensource-to-opensource/1.9.4.1/map.xml`
   1. Magento rotberoende filsökväg: `app/code/Vendor/Migration/etc/opensource-to-opensource/1.9.4.1/map.xml`

Katalogerna `<Magento 2 dir>/vendor/magento/data-migration-tool/etc` och `<Magento 2 dir>/vendor/magento/data-migration-tool/etc/<ce version>` innehåller följande konfigurationsfiler:

Även om du arbetar med filen `map.xml.dist` för det mesta, beskrivs varje mappning och andra filer i följande tabell.

| Mappningsfilnamn | Beskrivning |
| --- | --- |
| `class-map.xml.dist` | Ordlista för klassmappningar mellan Magento 1 och Magento 2 |
| `config.xml.dist` | Huvudkonfigurationsfil som anger databaskonfigurationer för Magento 1 och Magento 2, stegkonfiguration och länkar till mappningsfiler |
| *Endast Adobe Commerce*. `customer-attr-document-groups.xml.dist` | Lista med tabeller som används i steget för anpassade kundattribut. |
| *Endast Adobe Commerce*. `customer-attr-map.xml.dist` | Mappningsfil som används i steget Anpassade kundattribut. |
| `deltalog.xml.dist` | Innehåller en lista med register som krävs för konfiguration av databasrutiner. |
| `eav-attribute-groups.xml.dist` | Innehåller en lista med attribut som används i Eav Step. |
| `eav-document-groups.xml.dist` | Innehåller en lista med tabeller som används i Eav-steg. |
| `log-document-groups.xml.dist` | Innehåller en lista med tabeller som används i loggsteget. |
| `map-eav.xml.dist` | Kartfil som används i EAV-steg. |
| `map-log.xml.dist` | Loggmappningsfil. |
| *Endast Adobe Commerce*. `map-sales.xml.dist` | Mappningsfil som används i SalesOrder Step. |
| `map.xml.dist` | Mappningsfil krävs för mappningssteget. |
| `settings.xml.dist` | Anger en migreringskonfigurationsfil som anger regler som krävs för att migrera tabellen `core_config_data`. |
| `customer-attribute-groups.xml.dist` | Innehåller en lista med attribut som används i steget Kundattribut. |
| `customer-document-groups.xml.dist` | Innehåller en lista med tabeller som används i steget Kundattribut. |
| `map-customer.xml.dist` | Mappningsfil som används i steget Kundattribut. |
| `order-grids-document-groups.xml.dist` | Innehåller en lista med tabeller som används i OrderGrid Step. |
| `map-document-groups.xml.dist` | Definierar vilka fält som ska uppdateras när dubbletter inträffar vid infogning av data |
| `map-stores.xml.dist` | Kartfil som används i butikssteg. |
| `map-tier-price.xml.dist` | Kartfil som används i steg för nivåpris. |
| *Endast Adobe Commerce*. `visual_merchandiser_map.xml.dist` | Mappningsfil som används i VisualMerchandiser Step. |
| *Endast Adobe Commerce*. `visual_merchandiser_attribute_groups.xml.dist` | Innehåller en lista med attribut som används i VisualMerchandiser Step. |
| *Endast Adobe Commerce*. `visual_merchandiser_document_groups.xml.dist` | Innehåller en lista med tabeller som används i VisualMerchandiser Step. |

Mer information finns i [[!DNL Data Migration Tool] den tekniska specifikationen](technical-specification.md).
