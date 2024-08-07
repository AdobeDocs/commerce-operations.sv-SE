---
title: Uppföljning av datamigrering
description: Lär dig hur du validerar att datamigreringen mellan Magento 1 och Magento 2 lyckades och att alla funktioner fungerar som förväntat.
exl-id: a55f357b-6c95-49d6-b2f1-c2e403a8c85f
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '312'
ht-degree: 0%

---

# Uppföljning av datamigrering

Vissa beteenden och logik i Magento 1 har implementerats på ett annat sätt i Magento 2. [!DNL Data Migration Tool] tar hand om det. Det finns vissa migreringsaspekter du bör känna till, och ibland måste du vidta några mindre åtgärder för att vissa funktioner ska fungera smidigt efter migreringen.

## Information

### Delad databas stöds inte

[!DNL Data Migration Tool] stöder inte delade databaser.

### Grupppriser konverterade till nivåpriser

Alla grupppriser konverteras automatiskt till nivåpriser under migreringen.

### Ny numrering för försäljningsenheter

Referensnummer för beställningar, fakturor, leveranser, kreditnotor och RMA-migrering i befintligt skick. Efter migreringen gäller de nya nummertilldelningsreglerna för Magento 2. Numreringen för de nya försäljningsenheterna är annorlunda.

## Steg

### Spara endast kundsegment [Adobe Commerce]

Efter migreringen måste kundsegment sparas om från adminpanelen för att de ska komma igång.

### Konfigurera tidszon

Verktyget migrerar inte tidszonsinställningar, så du måste konfigurera tidszonen manuellt efter migreringen på **Lagrar** > **Konfiguration** > **Språkalternativ** > **Tidszon**.

Som standard lagrar Magento tidsdata i UTC-0-zonen i databasen och visar dem enligt de aktuella tidszonsinställningarna. Om tidsdata redan har sparats i databasen i en annan zon än UTC-0, måste du konvertera den befintliga tiden till UTC-0 med `\Migration\Handler\Timezone`-hanteraren för [!DNL Data Migration Tool].

I följande exempel har Magento 1 felaktigt sparat tid i UTC-7-zonen i databasen (till exempel på grund av ett felaktigt tillägg från tredje part). Följ de här stegen för att konvertera skapandetiden för kundkontot till UTC-0-zonen när du migrerar:

1. Kopiera konfigurationsfilen `map-customer.xml.dist` från lämplig katalog för [!DNL Data Migration Tool] (`<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/<migration edition>`) till filen `<your Magento 2 install dir>/app/code/Vendor/Migration/etc/<migration edition>/map-customer.xml`.

1. Uppdatera noden `<customer_map_file>` i `config.xml` och ta bort tillägget `.dist` från `map-customer.xml.dist`

1. Lägg till följande regel i filen `map-customer.xml`:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<map xmlns:xs="http://www.w3.org/2001/XMLSchema-instance" xs:noNamespaceSchemaLocation="../map.xsd">
  <!--...-->
  <destination>
      <field_rules>
          <!--...-->
          <transform>
              <field>customer_entity.created_at</field>
              <handler class="\Migration\Handler\Timezone">
                  <param name="offset" value="-7" />
              </handler>
          </transform>
      </field_rules>
  </destination>
</map>
```
