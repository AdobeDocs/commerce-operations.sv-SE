---
title: Bästa tillvägagångssätt för att ändra databastabeller
description: Lär dig hur och när du ska ändra databastabeller från Adobe Commerce och tredje part.
role: Developer, Architect
feature: Best Practices
last-substantial-update: 2022-11-15T00:00:00Z
exl-id: 9e7adaaa-b165-4293-aa98-5dc4b8c23022
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '1438'
ht-degree: 0%

---

# Bästa tillvägagångssätt för att ändra databastabeller

I den här artikeln beskrivs de bästa sätten att ändra databastabeller som skapas av [!DNL Adobe Commerce] eller tredjepartsmoduler. Genom att förstå när och hur ni effektivt ändrar tabeller kan ni säkerställa långsiktig lönsamhet och stabilitet på er handelsplattform.

Migrerar från [!DNL Magento 1] och andra e-handelsplattformar, eller arbeta med moduler från [!DNL Adobe Commerce] Marketplace, kan kräva att extra data läggs till och sparas. Den första instansen kan vara att lägga till en kolumn i en databastabell eller att justera en befintlig kolumn. Du bör dock bara ändra en kärna [!DNL Adobe Commerce] register (eller leverantörsregister från tredje part) i begränsade situationer.

## Varför Adobe rekommenderar att man undviker ändringar

Det främsta skälet till att undvika att ändra huvudtabeller är att Adobe Commerce innehåller underliggande logik som innehåller råa SQL-frågor. Ändringar i tabellstrukturen kan orsaka oväntade biverkningar som är svåra att felsöka. Ändringen kan också påverka DDL-åtgärder (Data Definition Language) som kan ge oväntade och oförutsägbara effekter på prestandan.

Ett annat skäl till att undvika att ändra databastabellens struktur är att dina ändringar kan orsaka problem om huvudutvecklingsteamet eller tredjepartsutvecklare ändrar strukturen i sina databastabeller. Det finns till exempel några viktiga databastabeller som har en kolumn som kallas `additional_data`. Det här har alltid varit en `text` kolumntyp. Av prestandaskäl kan dock huvudteamet ändra kolumnen till `longtext`. Den här kolumntypen är ett alias för JSON. Genom att konvertera till den här kolumntypen läggs resultatvinster och sökbarhet till i den kolumnen, som inte finns som en `text` typ. Du kan läsa mer om det här avsnittet i [JSON-datatyp](https://mariadb.com/kb/en/json-data-type/){target="_blank"}.

## Ha koll på när data ska sparas eller tas bort

Adobe rekommenderar att du först avgör om du behöver spara dessa data eller inte. Om du flyttar data från ett äldre system sparar alla data som du kan ta bort både tid och arbete under migreringen. (Det finns olika sätt att arkivera data om de behöver användas senare.) För att programmet och prestandan ska bli en bra fördel kan det vara bra att bestrida en begäran om att spara extra data. Målet är att säkerställa att sparandet av data är ett krav för att uppfylla ett affärsbehov som inte kan uppfyllas på ett annat sätt.

### Äldre data

Om projektet innehåller äldre data, t.ex. gamla order eller kundposter, bör du överväga en alternativ sökmetod. Om företaget till exempel kräver åtkomst till data endast för tillfälliga referenser, bör du implementera en extern sökning av den gamla databasen som ligger utanför handelsplattformen i stället för att migrera gamla data till [!DNL Adobe Commerce].

Detta kräver att databasen migreras till en server, antingen med ett webbgränssnitt för att läsa data, eller kanske utbildning i användningen av MySQL Workbench eller liknande verktyg. Genom att dessa data utelämnas från den nya databasen går migreringen snabbare eftersom utvecklingsteamet kan fokusera på den nya webbplatsen i stället för att felsöka datamigreringsproblem.

Ett annat relaterat alternativ för att göra data externa för e-handel, men som gör det möjligt att använda dem i realtid, är att utnyttja andra verktyg, som GraphQL-nät. Det här alternativet kombinerar olika datakällor och returnerar dem som ett enda svar.

Du kan till exempel `stitch` tillsammans gamla order från en extern databas, kanske den gamla Magento 1-anläggningen som är avvecklad. Visa dem sedan som en del av kundens orderhistorik med GraphQL-nät. Dessa gamla order kan kombineras med beställningarna från din nuvarande [!DNL Adobe Commerce] miljö.

Mer information om hur du använder API-nät med GraphQL finns i [Vad är API Mesh?](https://developer.adobe.com/graphql-mesh-gateway/gateway/overview/){target="_blank"}) and [GraphQL Mesh Gateway](https://developer.adobe.com/graphql-mesh-gateway/){target="_blank"}.

## Migrera äldre data med tilläggsattribut

Om du fastställer att äldre data kräver migrering eller att nya data måste sparas i [!DNL Adobe Commerce], Adobe rekommenderar att du använder [tilläggsattribut](https://developer.adobe.com/commerce/php/development/components/add-attributes/){target="_blank"}. Att använda tilläggsattribut för att spara ytterligare data ger följande fördelar:

- Du kan styra vilka data som ska bevaras och databasstrukturen, vilket säkerställer att data sparas med rätt kolumntyp och korrekta index.
- De flesta entiteter i [!DNL Adobe Commerce] och [!DNL Magento Open Source] har stöd för användning av tilläggsattribut.
- Tilläggsattribut är en lagringsalgoritmisk mekanism som ger flexibilitet att spara data på den optimala platsen för ditt projekt.

Två exempel på lagringsplatser är databastabeller och [!DNL Redis]. Det viktigaste att tänka på när du väljer en plats är om platsen medför extra komplexitet eller påverkar prestandan.

### Överväg andra alternativ

Som utvecklare är det viktigt att alltid överväga att använda verktyg utanför [!DNL Adobe Commerce] -miljö, till exempel GraphQL mesh och Adobe App Builder. De här verktygen kan hjälpa dig att behålla åtkomsten till data men påverkar inte centrala e-handelsprogrammet eller dess underliggande databastabeller. Med den här metoden kan du visa data via ett API. Sedan lägger du till en datakälla i din App Builder-konfiguration. Med GraphQL Mesh kan du kombinera dessa datakällor och få ett enda svar som nämns i [äldre data](#legacy-data).

Mer information om GraphQL-nät finns i [GraphQL Mesh Gateway](https://developer.adobe.com/graphql-mesh-gateway/){target="_blank"}. For information about the Adobe App Builder,  see [Introducing App Builder](https://experienceleague.adobe.com/docs/adobe-developers-live-events/events/2021/oct2021/introduction-app-builder.html?lang=en){target="_blank"}.

## Ändra en bastabell eller tredjepartstabell

Om du bestämmer dig för att lagra data genom att ändra en kärna [!DNL Adobe Commerce] Använd följande riktlinjer för att minimera påverkan på stabilitet och prestanda.

- Lägg endast till nya kolumner.
- Ändra aldrig _type_ värdet för en befintlig kolumn. Ändra till exempel inte en `integer` till `varchar` för att uppfylla dina unika användningsbehov.
- Undvik att lägga till kolumner i EAV-attributtabeller. De här tabellerna är redan överbelastade med logik och ansvar.
- Innan du justerar en tabell bestämmer du dess storlek. Om du ändrar stora tabeller påverkas distributionen, vilket kan orsaka minuter eller timmars fördröjning när ändringarna tillämpas.

## Bästa tillvägagångssätt för att ändra en extern databastabell

Adobe rekommenderar att du följer de här stegen när du lägger till en kolumn i en huvuddatabastabell eller en tredjepartstabell:

1. Skapa en modul med ett namn i namnutrymmet som representerar det du uppdaterar.

   Exempel: `app/code/YourCompany/Customer`

1. Skapa lämpliga filer för att aktivera modulen (se [Skapa en modul](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/backend-development/create-module.html){target="_blank"}.

1. Skapa en fil med namnet `db_schema.xml` i `etc` och gör de ändringar som behövs.

   Generera en `db_schema_whitelist.json` -fil. Se [Deklarationsschema](https://developer.adobe.com/commerce/php/development/components/declarative-schema/configuration/){target="_blank"} för mer information.

### Potentiella effekter

Om du lägger till en kolumn i en extern databas kan det påverka ditt Adobe Commerce-projekt på följande sätt:

- Uppgraderingar kan vara mer komplicerade.
- Distributioner påverkas om tabellen som ändras är stor.
- Migreringar till en ny plattform kan vara mer komplicerade.

## Olika sätt att undvika att ändra huvudtabeller

Du kan undvika att ändra Adobe Commerce databastabeller genom att använda [tilläggsattribut](#migrate-legacy-data-with-extension-attributes). Ett annat alternativ är att använda en särskild kolumn (`additional_data`) finns i några huvudtabeller för att lagra data och spara dem i JSON-kodat format.

### Spara data i en JSON-kodad datakolumn

Vissa bastabeller har `additional_data` kolumn som innehåller JSON-kodade data. I den här kolumnen finns ett inbyggt sätt att mappa ytterligare data i ett fält. Med den här metoden undviker du att lägga till en tabell för små, enkla dataelement som lagrar information för datahämtning utan sökkrav. The `additional_data` -kolumnen är vanligtvis bara tillgänglig på objektnivå, inte för hela offerten eller ordningen.

- Fördelar med att använda `additional_data` fält

   - Inga ytterligare fält behövs, vilket gör att antalet kolumner är minimalt. Detta är användbart i försäljningsflödet, där det redan finns många tabeller. Det är bäst att inte göra denna redan komplicerade process mer komplicerad. Den här metoden uppfyller många användningsområden, men inte alla.

- Nackdelar

   - Den här metoden är idealisk endast för lagring av skrivskyddade data. Problemet inträffar eftersom koden måste avserialiseras för att kunna ändra och skapa objektet för att lägga till beroenden eller databasrelationer.

   - Det är svårt att använda databasåtgärder för att söka efter dessa fält. Det går långsamt att söka med den här metoden.

   - Särskild försiktighet måste iakttas vid lagring av data i `additional_data` för att undvika att utlösa serialisering eller icke-serialiseringsåtgärder som kan bryta koden genom att skapa ogiltig JSON eller orsaka läsfel under körning.

   - Dessa fält måste vara tydligt deklarerade i koden så att utvecklaren enkelt kan hitta dem.

   - Andra problem som kan uppstå och som kan vara mycket svåra att diagnostisera. Med vissa inbyggda PHP-funktioner om du inte använder [!DNL Adobe Commerce] wrapper-metoder som tillhandahålls av huvudprogrammet kan slutresultatet av omformade data skilja sig från det förväntade formatet. Använd alltid wrapper-funktionerna för att säkerställa att data som sparas eller hämtas är konsekventa och förutsägbara.

Här är exempel på tabeller som har kolumnen och strukturen för `additional_data` kolumn.

```mysql
MariaDB [main]> DESCRIBE quote_item additional_data;
+-----------------+------+------+-----+---------+-------+
| Field           | Type | Null | Key | Default | Extra |
+-----------------+------+------+-----+---------+-------+
| additional_data | text | YES  |     | NULL    |       |
+-----------------+------+------+-----+---------+-------+
1 row in set (0.001 sec)


MariaDB [main]> DESCRIBE sales_order_item additional_data;
+-----------------+------+------+-----+---------+-------+
| Field           | Type | Null | Key | Default | Extra |
+-----------------+------+------+-----+---------+-------+
| additional_data | text | YES  |     | NULL    |       |
+-----------------+------+------+-----+---------+-------+
1 row in set (0.001 sec)
```

I versionerna 2.4.3, 2.4.4 och 2.4.5 finns det tio tabeller som har kolumnen `additional_data`.

```mysql
MariaDB [magento]> SELECT DISTINCT TABLE_NAME FROM INFORMATION_SCHEMA.COLUMNS WHERE COLUMN_NAME IN ('additional_data') AND TABLE_SCHEMA='main';
+------------------------+
| TABLE_NAME             |
+------------------------+
| sales_shipment_item    |
| sales_creditmemo_item  |
| sales_invoice_item     |
| catalog_eav_attribute  |
| sales_order_payment    |
| quote_address_item     |
| quote_payment          |
| quote_item             |
| magento_reward_history |
| sales_order_item       |
+------------------------+
10 rows in set (0.020 sec)
```
