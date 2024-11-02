---
title: Bästa praxis för kataloghantering
description: Läs mer om rekommendationer för hur du konfigurerar kundvagnsgränser och produktattribut, listar sidnumrering, alternativ, kampanjer och varianter.
role: Developer
feature: Best Practices, Catalog Management
exl-id: 9a672017-9122-4841-a67b-a183224b67dc
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '1403'
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

För bästa prestanda bör du använda följande riktlinjer för att hantera kundvagnsbegränsningar för Adobe Commerce.

### Berörda produkter och versioner

[Alla versioner som stöds](../../../release/versions.md) av:

- Adobe Commerce i molninfrastruktur
- Adobe Commerce lokalt

### Minska antalet varukorgsartiklar

Använd följande strategier för att hantera antalet kundvagnsartiklar

- Dela upp order i flera mindre order med ett mindre antal rader genom att använda funktionen [!UICONTROL Add Item by SKU].
- Lägg bara till den anpassade logik och kundvagnsanpassning som krävs för att läsa in en lista med objekt.

## Kategoribegränsningar

Ett stort antal kategorier kan påverka prestandan.

### Berörda produkter och versioner

[Alla versioner som stöds](../../../release/versions.md) av:

- Adobe Commerce i molninfrastruktur
- Adobe Commerce lokalt

### Minska antalet produkter

Använd följande strategier för att minska antalet kategorier:

- Hantera unika produktfunktioner med attribut och anpassade alternativ
- Ta bort inaktiva kategorier
- Optimera katalogdjup i navigeringen

## Produktattribut

Om du konfigurerar för många produktattribut eller produktattributsalternativ kan prestandan påverkas.

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

1. [Anslut till platsdatabasen](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/service/mysql#connect-to-the-database).

1. Hitta antalet attributuppsättningar med MySQL

   ```sql
   SELECT COUNT(*) AS 'attribute_set' FROM *${TABLE_PREFIX}*eav_attribute_set;
   ```

1. Ta bort alla oanvända attributuppsättningar.

### Potentiell inverkan på prestanda

Om du konfigurerar många **produktattribut** ökas produktmallens storlek för varje produkt (EAV-struktur) och mängden data som måste hämtas. Ökningen påverkar åtgärder på följande sätt:

- Ökning i SQL-frågor, trafik som är relaterad till EAV-datahämtning och mängden data som bearbetas, vilket ger minskat databasflöde
- Betydande ökning av storleken på Adobe Commerce-index och fulltextsökningsindex
- Hårda MySQL-gränser när ett FLAT-index skapas för stora produktmallar och det inte går att använda det

Ökning av produktdata och indexstorlekar kan påverka webbplatsens prestanda på följande sätt:

- Ökad svarstid för de flesta butiksscenarier som rör katalogbläddring, sökning (snabb och avancerad) och lagerstyrd navigering.
- Produkthanteringsåtgärder i Admin tar lång tid, vilket kan leda till timeout.
- Funktionen för produktmassåtgärder kan blockeras.
- Indexåterskapningstiden för medelstora och stora kataloger kan inte utföras dagligen på grund av långa körningstider.

Om du konfigurerar många **attributalternativ** kan platsens prestanda påverkas på följande sätt:

- Långa efterfrågnings- och renderingstider för produktinformation (PDP) och kategorisidor som innehåller komplexa produkter.
- Admin - produkt sparar Åtgärdens svarstid ökar över optimala prestandamål.
- Öka tiden för formuläråtergivning i produktredigering.
- Långsam utcheckning.

## Produktalternativ

Om du konfigurerar för många produktalternativ per produkt kan prestandan påverkas.

### Berörda produkter och versioner

[Alla versioner som stöds](../../../release/versions.md) av:

- Adobe Commerce i molninfrastruktur
- Adobe Commerce lokalt

### Minska antalet alternativ

Använd följande strategier för att minska antalet produktalternativ per produkt:

- Konfigurera komplexa produkter och anpassade alternativ som en källa till produktvariationer.
- I stället för att skapa globala produktmallar och alternativbehållare som gäller för alla produkter kan du använda attributuppsättningar för att skapa specifika produktmallar med riktade attribut och alternativ.
- Hantera produktinformation via ett externt produkthanteringssystem (PMS).

### Potentiell inverkan på prestanda

När du konfigurerar många produktalternativ ökar mängden data som hämtas för varje produkt vid alla läs- och skrivåtgärder, vilket resulterar i:

- Ökad SQL-frågetrafik och tyngre `JOIN`-åtgärder ökar databasens genomströmning.
- Ökad storlek för Adobe Commerce-index och fulltextsökningsindex.

Ökningarna ovan kan påverka webbplatsens prestanda på följande sätt:

- Längre svarstid för de flesta butiksscenarier som är relaterade till produkter som innehåller många alternativ i attribut.
- Betydande ökning av den tid som krävs för att slutföra Product Management-åtgärder i Admin som kan leda till timeout, särskilt för scenarier som rör attributlista och hämtning av träd, inklusive hantering av kampanjregler.
- Kan blockera gruppåtgärder som slutför asynkrona massåtgärder som import och export och tilldela anpassade priser till flera produkter i en delad katalog.

## Sidnumrering av produktlista

För många produkter per sida kan påverka prestanda.

### Berörda produkter och versioner

[Alla versioner som stöds](../../../release/versions.md) av:

- Adobe Commerce i molninfrastruktur
- Adobe Commerce lokalt

### Uppdatera produktlistekonfigurationen

Om du har för många produkter i en kategori kan du uppdatera katalogkonfigurationen för storefront så att alternativet **Tillåt alla produkter per sida** inaktiveras.

När du har inaktiverat det här alternativet använder Adobe Commerce sidnumreringskontrollerna för att hantera antalet produkter som visas i butikskomponenter. Instruktioner finns i [Konfigurera sidnumreringskontroller](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/navigation/navigation-product-listings.html#configure-the-pagination-controls).

## Produkt-SKU-gränser

Om du konfigurerar för många produkt-SKU:er kan det påverka prestanda genom att produktinhämtningen blir långsammare och tiden det tar att slutföra administratörsåtgärder eller indexeringar ökar.

### Berörda produkter och versioner

[Alla versioner som stöds](../../../release/versions.md) av:

- Adobe Commerce i molninfrastruktur
- Adobe Commerce lokalt

### Minska antalet produkter

Använd följande strategier för att minska antalet produkter (SKU):

- Minimera multiplikatorer—
   - Konsolidering av webbplatser minskar multiplikatorn.
   - Använd alternativa produktfunktioner för anpassade priser för att ersätta delade kataloger och kundgruppmultiplikatorer.
   - Både kundgrupper och delade kataloger fungerar som multiplikatorer för antalet aktiva SKU:er i en butik.
- Strukturera om katalogen—
   - Minska antalet produkter som tilldelas kategorier.
   - Minska antalet SKU:er genom att minska antalet webbplatser, kundgrupper, delade kataloger, antalet produkter eller antalet konfigurerbara produktalternativ
- Skapa fler produktvarianter genom att använda anpassade alternativ istället för att skapa separata produkter.
- Med tanke på att en effektiv SKU kan innehålla ett antal möjliga permutationer av priserna, eftersom priserna kan anges olika för varje butik eller kundgrupp.
- Inaktivera eller ta bort oanvända systemkomponenter som moduler. Se [Avinstallera moduler](../../../installation/tutorials/uninstall-modules.md).
- Hantera produkter i ett externt plattformshanteringssystem.

## Produktvariationer

Om du konfigurerar för många variationer per produkt kan prestandan påverkas.

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

Följ dessa metodtips för att konfigurera försäljning och kampanjer för artiklar i en kundvagn:

- **Försäljningsregler (kundprisregler)**
   - Hantera och ta bort oanvända regler.
   - Lägg till strikta regelvillkor (som attribut- eller kategorifilter) för den mest effektiva matchningen.
- **Kuponger**
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
- Den tid det tog att återge blocket **Totals** på utcheckningssidan har ökat.
