---
title: Bästa praxis för kataloghantering
description: Läs mer om rekommendationer för hur du konfigurerar kundvagnsgränser och produktattribut, listar sidnumrering, alternativ, kampanjer och varianter.
role: Developer
feature: Best Practices, Catalog Management
source-git-commit: 3e0187b7eeb6475ea9c20bc1da11c496b57853d1
workflow-type: tm+mt
source-wordcount: '1876'
ht-degree: 0%

---


# Bästa praxis för kataloghantering

De bästa metoderna för kataloghantering som beskrivs här omfattar en rad olika frågor, bland annat (men inte begränsat till):

- Biljettbegränsningar
- Kategoribegränsningar
- Produktattribut
- Sidnumrering av produktlista
- Produktalternativ
- Produktvariationer
- Erbjudanden

## Biljettbegränsningar

Använd följande riktlinjer för att hantera kundvagnsbegränsningar för Adobe Commerce och Magento Open Source för bästa prestanda:

- I version 2.3.x - 2.4.2 tillåts maximalt 100 produkter i en kundvagn.
- I version 2.4.3 och senare ökade kundvagnens maximala storlek till 750.

För version 2.3.x - 2.4.2 är förväntad prestanda baserad på artikelgränsen för kundvagn:

- Upp till **100** produkter i en kundvagn - produkten fungerar och uppfyller prestationsmålen för svarstid.
- Upp till **300** produkter i varukorgen - produkten fungerar, men svarstiden ökar mer än målen.
- Över **500** produkter i en kundvagn - korgen och kassaflödena fungerar inte

### Berörda produkter och versioner

[Alla versioner som stöds](../../../release/versions.md) av:

- Adobe Commerce i molninfrastruktur
- Adobe Commerce lokalt

### Minska antalet varukorgsartiklar

Använd följande strategier för att hantera antalet kundvagnsartiklar

- Dela upp order i flera mindre order med ett mindre antal rader genom att använda [!UICONTROL Add Item by SKU] -funktion.
- Lägg bara till den anpassade logik och kundvagnsanpassning som krävs för att läsa in en lista med objekt.

### Potentiell inverkan på prestanda

Om du har fler än det rekommenderade maximala antalet produkter i vagnen kan det påverka webbplatsens prestanda på följande sätt:

- Ökad svarstid för datahämtningsåtgärder, validering av varukorgsartiklar, kontroll av prisregler samt moms- och totalberäkningar.
- Ökad svarstid för minicart-rendering, inklusive rendering av kundvagnen, kassaflöde och exekvering.
- Ökad inläsningstid för alla webbplatssidor där miniatyrbilden finns.

## Kategoribegränsningar

För bästa prestanda bör du inte konfigurera fler än det högsta rekommenderade antalet kategorier för Adobe Commerce-webbplatser.

- Konfigurera högst 6 000 kategorier för Adobe Commerce version 2.4.2 och senare
- För Adobe Commerce version 2.3.x och 2.4.0 till 2.4.1-p1, konfigurera maximalt 3 000 kategorier

### Berörda produkter och versioner

[Alla versioner som stöds](../../../release/versions.md) av:

- Adobe Commerce i molninfrastruktur
- Adobe Commerce lokalt

### Minska antalet produkter

Använd följande strategier för att minska antalet kategorier:

- Hantera unika produktfunktioner med attribut och anpassade alternativ
- Ta bort inaktiva kategorier
- Optimera katalogdjup i navigeringen

### Potentiell inverkan på prestanda

Om du har fler än det rekommenderade maximala antalet kategorier kan det påverka webbplatsens prestanda på följande sätt:

- En påtaglig ökning av svarstiden för icke-cachelagrade katalogsidor
- Lång körning och tidsgränser vid hantering av kategorier från administratören
- Ökad storlek på motsvarande databastabeller
- Större indextabeller ökar den tid som krävs för att slutföra indexeringen för `[category/product relation index\]`
- Ökad bearbetningstid för att slutföra åtgärder för att bygga kategorier, hämta menyer och hantera kategoriregler

## Produktattribut

- För bästa prestanda bör du inte konfigurera fler än det högsta rekommenderade antalet produktattribut eller produktattributsalternativ.

- **Produktattribut**—
   - För Adobe Commerce version 2.3.x och 2.4.0 till 2.4.1-p1 får du inte konfigurera fler än 500 attribut
   - Konfigurera upp till 1 500 produktattribut för Adobe Commerce version 2.4.2 och senare
- **Produktattributsalternativ**-Konfigurera upp till 100 attributalternativ för varje attribut
- **Produktattributuppsättningar**-Konfigurera högst 1 000 attributuppsättningar

>[!NOTE]
>
>Produktattributen anger funktioner som gäller globalt för alla produkter. Produktattributsalternativen är anpassningar för att specificera funktioner som gäller för specifika produkter.

### Berörda produkter och versioner

[Alla versioner som stöds](../../../release/versions.md) av:

- Adobe Commerce i molninfrastruktur
- Adobe Commerce lokalt

### Minska antalet attribut

För bästa prestanda när du hanterar produkter från Admin och hämtar produktdata i butiken:

- Använd olika produktmallar (attributuppsättningar) för olika produkter.
- Utnyttja anpassade alternativ och komplexa produkter för hantering av variationer
- Minimera antalet sökbara attribut.
- Ta bort produktegenskaper som inte används.
- Lagra och hantera icke-handelsrelaterade attribut i externa produkthanteringssystem (PMS).

### Minska antalet attributalternativ

För bästa prestanda när du hanterar produkter från Admin och hämtar produktdata i butiken:

- Använd olika variationsmekanismer för att skapa produkter: komplexa produkter, anpassade alternativ som en källa till produktvariationer.
- Skapa specifika produktmallar med riktade attribut och alternativ för att undvika generaliserade produktmallar och alternativbehållare.
- Underhåll en lista över faktiska attributalternativ.
- Hantera produktinformation via ett externt produkthanteringssystem (PMS).

### Minska antalet attributuppsättningar

Ta bort oanvända produktattributuppsättningar med MySQL.

#### Granska konfigurationen av attributuppsättning

1. [Anslut till platsdatabasen](https://devdocs.magento.com/cloud/project/services-mysql.html#connect-to-the-database).

1. Hitta antalet attributuppsättningar med MySQL

   ```sql
   SELECT COUNT(*) AS 'attribute_set' FROM *${TABLE_PREFIX}*eav_attribute_set;
   ```

1. Ta bort alla oanvända attributuppsättningar.

### Potentiell inverkan på prestanda

Konfigurera många **produktattribut** ökar mallstorleken för varje produkt (EAV-struktur) och mängden data som måste hämtas. Ökningen påverkar åtgärder på följande sätt:

- Ökning i SQL-frågor, trafik som är relaterad till EAV-datahämtning och mängden data som bearbetas, vilket ger minskat databasflöde
- Betydande ökning av storleken på Adobe Commerce-index och fulltextsökningsindex
- Hårda MySQL-gränser när ett FLAT-index skapas för stora produktmallar och det inte går att använda det

Ökning av produktdata och indexstorlekar kan påverka webbplatsens prestanda på följande sätt:

- Ökad svarstid för de flesta butiksscenarier som rör katalogbläddring, sökning (snabb och avancerad) och lagerstyrd navigering.
- Produkthanteringsåtgärder i Admin tar lång tid, vilket kan leda till timeout.
- Funktionen för produktmassåtgärder kan blockeras.
- Indexåterskapningstiden för medelstora och stora kataloger kan inte utföras dagligen på grund av långa körningstider.

Konfigurera många **attributalternativ** kan påverka webbplatsens prestanda på följande sätt:

- Långa efterfrågnings- och renderingstider för produktinformation (PDP) och kategorisidor som innehåller komplexa produkter.
- Admin - produkt sparar Åtgärdens svarstid ökar över optimala prestandamål.
- Öka tiden för formuläråtergivning i produktredigering.
- Långsam utcheckning.

## Produktalternativ

För bästa prestanda bör du konfigurera maximalt 100 produktalternativ per produkt.

### Berörda produkter och versioner

[Alla versioner som stöds](../../../release/versions.md) av:

- Adobe Commerce i molninfrastruktur
- Adobe Commerce lokalt

### Minska antalet alternativ

Använd följande strategier för att minska antalet produktalternativ för att få bästa prestanda för webbplatsen:

- Konfigurera komplexa produkter och anpassade alternativ som en källa till produktvariationer.
- I stället för att skapa globala produktmallar och alternativbehållare som gäller för alla produkter kan du använda attributuppsättningar för att skapa specifika produktmallar med riktade attribut och alternativ.
- Hantera produktinformation via ett externt produkthanteringssystem (PMS).

### Potentiell inverkan på prestanda

När du konfigurerar många produktalternativ ökar mängden data som hämtas för varje produkt vid alla läs- och skrivåtgärder, vilket resulterar i:

- Ökad SQL-frågetrafik och högre `JOIN` åtgärder ökar databasens genomströmning.
- Ökad storlek för Adobe Commerce-index och fulltextsökningsindex.

Ökningarna ovan kan påverka webbplatsens prestanda på följande sätt:

- Längre svarstid för de flesta butiksscenarier som är relaterade till produkter som innehåller många alternativ i attribut.
- Betydande ökning av den tid som krävs för att slutföra Product Management-åtgärder i Admin som kan leda till timeout, särskilt för scenarier som rör attributlista och hämtning av träd, inklusive hantering av kampanjregler.
- Kan blockera gruppåtgärder som slutför asynkrona massåtgärder som import och export och tilldela anpassade priser till flera produkter i en delad katalog.

## Sidnumrering av produktlista

Bästa prestanda får du om du visar högst 48 produkter per sida.

Du kan konfigurera Adobe Commerce så att kunderna kan se alla kategoriprodukter på en enda sida. Om antalet kategoriprodukter överstiger 48 produkter uppdaterar du katalogkonfigurationen för storefront-sidnumreringskontroller.

### Berörda produkter och versioner

[Alla versioner som stöds](../../../release/versions.md) av:

- Adobe Commerce i molninfrastruktur
- Adobe Commerce lokalt

### Uppdatera produktlistekonfigurationen

Om du har fler än 48 produkter i en kategori kan du uppdatera katalogkonfigurationen för storefront för att inaktivera alternativet att **Tillåt alla produkter per sida**.

När du har inaktiverat det här alternativet använder Adobe Commerce sidnumreringskontrollerna för att hantera antalet produkter som visas i butikskomponenter. Instruktioner finns i [Konfigurera sidnumreringskontroller](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/navigation/navigation-product-listings.html#configure-the-pagination-controls).

## Produkt-SKU-gränser

För att maximera prestandan rekommenderas ett maximum för effektiv produktlagringsenhet (SKU) på 242 miljoner. Denna gällande produkt-SKU-maxgräns beräknas som:

```text
Effective SKU = N[SKUs] x N[Stores] x N[Customer groups]
```

Var:

- N står som antalet objekt i den kategorin
- Kundgrupper inkluderar delade kataloger eftersom de skapar ytterligare en kundgrupp.

Om du har fler än det maximala antalet aktiva SKU:er tar det längre tid att hämta produktdata och slutföra åtgärder eller indexeringar på administratörspanelen.

### Berörda produkter och versioner

[Alla versioner som stöds](../../../release/versions.md) av:

- Adobe Commerce i molninfrastruktur
- Adobe Commerce lokalt

### Minska antalet produkter

Använd följande strategier för att minska antalet produkter (SKU):

- Minimera multiplikatorer—
   - Konsolidering av webbplatser minskar multiplikatorn. Om ni har 50 000 SKU:er, tio webbplatser och tio kundgrupper är antalet SKU:er 5 miljoner. Genom att ta bort fem kundgrupper minskas antalet effektiva SKU:er till 2,5 miljoner.
   - Använd alternativa produktfunktioner för anpassade priser för att ersätta delade kataloger och kundgruppmultiplikatorer.
   - Både kundgrupper och delade kataloger fungerar som multiplikatorer för antalet aktiva SKU:er i en butik.
- Strukturera om katalogen—
   - Minska antalet produkter som tilldelas kategorier.
   - Minska antalet SKU:er genom att minska antalet webbplatser, kundgrupper, delade kataloger, antalet produkter eller antalet konfigurerbara produktalternativ
- Skapa fler produktvarianter genom att använda anpassade alternativ istället för att skapa separata produkter.
- Med tanke på att en effektiv SKU kan innehålla ett antal möjliga permutationer av priserna, eftersom priserna kan anges olika för varje butik eller kundgrupp.
- Inaktivera eller ta bort oanvända systemkomponenter som moduler. Se  [Avinstallera moduler](../../../installation/tutorials/uninstall-modules.md).
- Hantera produkter i ett externt plattformshanteringssystem.

## Produktvariationer

För bästa prestanda bör du konfigurera maximalt 50 varianter per produkt.

### Berörda produkter och versioner

[Alla versioner som stöds](../../../release/versions.md) av:

- Adobe Commerce i molninfrastruktur
- Adobe Commerce lokalt

### Minska antalet variationer

Använd följande strategier för att minska antalet produktvariationer för bästa webbplatsprestanda:

- Strukturera om katalogen genom att distribuera antalet variationer mellan olika produkter.
- Ta bort konfigurerbara attributalternativ som inte finns i lager.
- Hantera variationer med alternativa funktioner som anpassade alternativ, kategorier, relaterade produkter, grupperade produkter och paketprodukter.

### Potentiell inverkan på prestanda

Om du överskrider det rekommenderade antalet produktvariationer kan det påverka webbplatsens prestanda på följande sätt:

- Långa efterfrågnings- och renderingstider för produktinformation och kategorisidor som innehåller komplexa produkter.
- Ökad svarstid för att slutföra Spara-åtgärder i administratören.
- Längre tid för att återge redigeringsformuläret.
- Långsam utcheckning.

## Erbjudanden

För bästa prestanda bör du följa de här bästa metoderna för att konfigurera försäljning och kampanjer för artiklar i en kundvagn:

- **Försäljningsregler (kundprisregler)**-Konfigurera inte fler än 1000 kundvagnsregler för alla webbplatser
   - Hantera och ta bort oanvända regler.
   - Lägg till strikta regelvillkor (som attribut- eller kategorifilter) för den mest effektiva matchningen.
- **Kuponger**—
   - Kontrollera att det totala antalet kuponger i databasen är mindre än 250 000.
   - Ta bort oanvända och utgångna kuponger.
   - Generera endast det antal kuponger som behövs för att uppfylla kampanjkraven.

### Berörda produkter och versioner

[Alla versioner som stöds](../../../release/versions.md) av:

- Adobe Commerce i molninfrastruktur
- Adobe Commerce lokalt

### Potentiell inverkan på prestanda

Om du har fler än det rekommenderade maximala antalet kundvagnsregler eller kuponger kan det påverka webbplatsens prestanda på följande sätt:

- Ökad svarstid när produkter läggs till i kundvagnen.
- Ökad tid för inläsning och rendering av minikortet.
- Den tid det tog att återge kundvagnssidan ökade.
- Ökad tid för att återge **Summor** -block på utcheckningssidan.
- Att tillämpa kuponger kan ta mer än 2 sekunder.