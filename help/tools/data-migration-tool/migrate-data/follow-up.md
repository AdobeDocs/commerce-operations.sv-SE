---
title: Uppföljning av datamigrering
description: Lär dig hur du validerar att datamigreringen mellan Magento 1 och Magento 2 lyckades och att alla funktioner fungerar som förväntat.
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '301'
ht-degree: 0%

---


# Uppföljning av datamigrering

Vissa beteenden och logik i Magento 1 har implementerats på ett annat sätt i Magento 2. The [!DNL Data Migration Tool] tar hand om det. Det finns vissa migreringsaspekter du bör känna till, och ibland måste du vidta några mindre åtgärder för att vissa funktioner ska fungera smidigt efter migreringen.

## Information

### Delad databas stöds inte

The [!DNL Data Migration Tool] stöder inte delade databaser.

### Grupppriser konverterade till nivåpriser

Alla grupppriser konverteras automatiskt till nivåpriser under migreringen.

### Ny numrering för försäljningsenheter

Referensnummer för beställningar, fakturor, leveranser, kreditnotor och RMA-migrering. Efter migreringen gäller de nya nummertilldelningsreglerna för Magento 2. Numreringen för de nya försäljningsenheterna är annorlunda.

## Steg

### Spara om kundsegment [Endast Adobe Commerce]

Efter migreringen måste kundsegment sparas om från adminpanelen för att de ska komma igång.

### Konfigurera tidszon

Verktyget migrerar inte tidszonsinställningar, så du måste konfigurera tidszonen manuellt efter migreringen vid **Lager** > **Konfiguration** > **Nationella inställningar** > **Tidszon**.

Som standard lagrar Magento tidsdata i UTC-0-zonen i databasen och visar dem enligt de aktuella tidszonsinställningarna. Om tidsdata redan har sparats i databasen i en annan zon än UTC-0, måste du konvertera den befintliga tiden till UTC-0 med [!DNL Data Migration Tool]&#39;s `\Migration\Handler\Timezone` hanterare.

I följande exempel har Magento 1 felaktigt sparat tid i UTC-7-zonen i databasen (till exempel på grund av ett felaktigt tillägg från tredje part). Följ de här stegen för att konvertera skapandetiden för kundkontot till UTC-0-zonen när du migrerar:

1. Kopiera `map-customer.xml.dist` konfigurationsfilen från lämplig katalog i [!DNL Data Migration Tool] (`<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/<migration edition>`) till `<your Magento 2 install dir>/app/code/Vendor/Migration/etc/<migration edition>/map-customer.xml` -fil.

1. Uppdatera `<customer_map_file>` nod i `config.xml` och ta bort `.dist` tillägg från `map-customer.xml.dist`

1. Lägg till följande regel i `map-customer.xml` fil:

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
