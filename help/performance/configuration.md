---
title: Bästa praxis för konfiguration
description: Optimera svarstiden för er Adobe Commerce-driftsättning med hjälp av dessa metodtips.
feature: Best Practices, Configuration
exl-id: 4cb0f5e7-49d5-4343-a8c7-b8e351170f91
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '1417'
ht-degree: 0%

---

# Bästa praxis för konfiguration

Commerce har många inställningar och verktyg som du kan använda för att förbättra svarstiden på sidorna och ge högre genomströmning.

## Kronjobb

Alla asynkrona åtgärder i [!DNL Commerce] utförs med Linux `cron`-kommandot. Se [Konfigurera och kör cron](../configuration/cli/configure-cron-jobs.md) för att konfigurera det korrekt.

## Indexerare

En indexerare kan köras i antingen **[!UICONTROL Update on Save]**- eller **[!UICONTROL Update on Schedule]**-läge. Läget **[!UICONTROL Update on Save]** indexeras omedelbart när katalogen eller andra data ändras. I det här läget används låg intensitet för uppdaterings- och bläddringsåtgärder i din butik. Det kan leda till betydande förseningar och otillgänglighet av data vid höga belastningar. Vi rekommenderar att du använder **Uppdatera i schemat** i prestandasyfte, eftersom det lagrar information om datauppdateringar och utför indexering av delar i bakgrunden via ett specifikt cron-jobb. Du kan ändra läget för varje [!DNL Commerce]-indexerare separat på konfigurationssidan **[!UICONTROL System]** > [!UICONTROL Tools] > **[!UICONTROL Index Management]** . Indexvärdet [!UICONTROL Customer Grid] måste alltid anges till läget **[!UICONTROL Update on Save]**.

>[!TIP]
>
>Omindexering av MariaDB 10.4 och 10.6 tar längre tid jämfört med andra MariaDB- eller [!DNL MySQL]-versioner. Vi föreslår att du ändrar standardkonfigurationsinställningen för MariaDB, som beskrivs i [installationskraven](../installation/prerequisites/database/mysql.md).

## Cacher

När du startar din butik i produktion aktiverar du alla cacheminnen från sidan **[!UICONTROL System]** > [!UICONTROL Tools] > **[!UICONTROL Cache Management]**. Vi rekommenderar att du använder [!DNL Varnish] eftersom det är en effektiv cachelösning för produktionssidor.

## Asynkrona e-postmeddelanden

Om du aktiverar inställningen&quot;Asynkrona e-postmeddelanden&quot; flyttas processer som hanterar utcheckning och beställer e-postmeddelanden till bakgrunden. Om du vill aktivera den här funktionen går du till **[!UICONTROL Stores]> [!UICONTROL Settings] > [!UICONTROL Configuration] > [!UICONTROL Sales] > [!UICONTROL Sales Emails] > [!UICONTROL General Settings] >[!UICONTROL Asynchronous Sending]**. Mer information finns i [E-postmeddelanden](https://docs.magento.com/user-guide/configuration/sales/sales-emails.html) i _användarhandboken för administratören_.

## Asynkron bearbetning av orderdata

Det kan finnas tillfällen då intensiv försäljning i en butik sker samtidigt som [!DNL Commerce] utför intensiv orderbearbetning. Du kan konfigurera [!DNL Commerce] så att dessa två trafikmönster särskiljs på databasnivå för att undvika konflikter mellan läs- och skrivåtgärder i motsvarande tabeller. Du kan lagra och indexera orderdata asynkront. Beställningar läggs i tillfällig lagring och flyttas i bulk till Order Management rutnät utan några kollisioner. Du kan aktivera det här alternativet från **[!UICONTROL Stores]> [!UICONTROL Settings] > [!UICONTROL Configuration] > [!UICONTROL Advanced] > [!UICONTROL Developer] > [!UICONTROL Grid Settings] >[!UICONTROL Asynchronous indexing]**. Mer information finns i [Schemalagda stödrasteruppdateringar](https://docs.magento.com/user-guide/sales/order-grid-updates-schedule.html) i _användarhandboken för administratören_.

>[!WARNING]
>
>Fliken **[!UICONTROL Developer]** och alternativen är bara tillgängliga i [Utvecklarläge](../configuration/cli/set-mode.md). [Adobe Commerce i molninfrastrukturen](https://devdocs.magento.com/cloud/requirements/cloud-requirements.html#cloud-req-test) stöder inte `Developer`-läge.

## Spara asynkron konfiguration

För projekt med ett stort antal butikskonfigurationer kan det ta oordinerad tid att spara en butikskonfiguration eller resultera i en timeout. Modulen _Async Config_ aktiverar asynkrona konfigurationssparningar genom att köra ett cron-jobb där en konsument bearbetar sparandet i en meddelandekö. AsyncConfig är **inaktiverad** som standard.

Du kan aktivera AsyncConfig med kommandoradsgränssnittet:

```bash
bin/magento setup:config:set --config-async 1
```

Kommandot `set` skriver följande till filen `app/etc/env.php`:

```conf
...
   'config' => [
       'async' => 1
   ]
```

Starta följande konsument för att börja bearbeta meddelandena i kön först-i-först-ut-baserat:

```bash
bin/magento queue:consumers:start saveConfigProcessor --max-messages=1
```

## Uppskjuten lageruppdatering

I tider med intensiv försäljning kan [!DNL Commerce] skjuta upp lageruppdateringar relaterade till order. Detta minimerar antalet åtgärder och snabbar upp orderplaceringsprocessen. Det här alternativet är dock riskabelt och kan bara användas när restorder aktiveras i butiken, eftersom det här alternativet kan leda till negativa lagerkvantiteter. Det här alternativet kan ge avsevärda prestandaförbättringar i utcheckningsflöden för butiker som enkelt kan fylla i sitt lager på begäran. Om du vill aktivera fördröjda Stock-uppdateringar på din webbplats går du till **[!UICONTROL Stores]> [!UICONTROL Settings] > [!UICONTROL Configuration] > [!UICONTROL Catalog] > [!UICONTROL Inventory] > [!UICONTROL Product Stock Options] >[!UICONTROL Use Deferred Stock Update]**. Mer information finns i [Hantera lager](https://docs.magento.com/user-guide/catalog/inventory.html) i _Adobe Commerce användarhandbok_.

>[!INFO]
>
>Det här alternativet är bara tillgängligt om **[!UICONTROL Backorder with any mode]** har aktiverats.

>[!INFO]
>
>Det här alternativet fungerar även med [asynkron orderplacering](high-throughput-order-processing.md#asynchronous-order-placement) i kombination med [Inventory management](https://experienceleague.adobe.com/docs/commerce-admin/inventory/guide-overview.html).

## Optimeringsinställningar på klientsidan

Om du vill förbättra butiksvarstiden för din [!DNL Commerce]-instans går du till Admin i läget Standard eller Utvecklare och ändrar följande inställningar:

**[!UICONTROL Stores]-> [!UICONTROL Configuration] -> [!UICONTROL Advanced] -> [!UICONTROL Developer]:**

| Inställningsgrupp | Inställning | Värde |
| ------------------- | -------------------------- | ------ |
| Stödrasterinställningar | Asynkron indexering | Aktivera |
| CSS-inställningar | Minimera CSS-filer | Ja |
| Inställningar för [!DNL JavaScript] | Minimera [!DNL JavaScript] filer | Ja |
| Inställningar för [!DNL JavaScript] | Aktivera [!DNL JavaScript]-paketet | Ja |
| Mallinställningar | Minfy HTML | Ja |

>[!INFO]
>
>Fliken **[!UICONTROL Developer]** och alternativen är bara tillgängliga i [Utvecklarläge](../configuration/cli/set-mode.md). [Adobe [!DNL Commerce] i molninfrastrukturen](https://devdocs.magento.com/cloud/requirements/cloud-requirements.html#cloud-req-test) stöder inte `Developer`-läge.

När du aktiverar alternativet **[!UICONTROL Enable [!DNL JavaScript] Bundling]** tillåter du att Commerce sammanfogar alla JS-resurser till ett eller flera paket som är inlästa på butikssidor. Paketeringen av JS resulterar i färre begäranden till servern, vilket förbättrar sidans prestanda. Det hjälper även webbläsaren att cachelagra JS-resurser vid det första anropet och återanvända dem för all vidare surfning. Det här alternativet ger även en lat utvärdering eftersom all JS läses in som text. Den initierar bara analys och utvärdering av kod efter att specifika åtgärder har utlösts på sidan. Den här inställningen rekommenderas dock inte för butiker där den första sidans laddningstid är extremt viktig eftersom allt JS-innehåll läses in vid det första anropet.

>[!INFO]
>
>Mer information om hur du optimerar CSS och JavaScript finns i [Optimering av CSS- och JavaScript-filer på Adobe Commerce i molninfrastrukturen och Adobe Commerce](https://support.magento.com/hc/en-us/articles/360044482152) i Adobe Commerce Help Center_.

### Pakettips

* Vi rekommenderar att du använder tredjepartsverktyg för miniatyr och paketering (som [r.js](https://requirejs.org/)). [!DNL Commerce] inbyggda mekanismer är inte optimala och levereras som reservalternativ.
* Att aktivera HTTP/2-protokollet kan vara ett bra alternativ till att använda JS-paketering. Protokollet ger många av samma fördelar. Det är aktiverat som standard i Adobe Commerce för molninfrastrukturprojekt.
* Vi rekommenderar inte att du använder föråldrade inställningar som att sammanfoga JS- och CSS-filer, eftersom de bara är utformade för synkront inläst JS i sidans HEAD-avsnitt. Om du använder den här tekniken kan paketeringen och requireJS-logiken fungera felaktigt.

## Validering av kundsegment

Handlare som har ett stort antal [kundsegment](https://docs.magento.com/user-guide/marketing/customer-segments.html) kan uppleva betydande prestandaförsämringar med kundåtgärder, till exempel kundinloggning och tillägg av produkter i kundvagnen.

Kundåtgärder utlöser en valideringsprocess för kundsegment, vilket kan leda till sämre prestanda. Som standard validerar Adobe Commerce varje segment i realtid för att definiera vilka kundsegment som matchas och vilka som inte gör det.

För att undvika prestandaförsämringar kan du ställa in systemkonfigurationsalternativet **[!UICONTROL Real-time Check if Customer is Matched by Segment]** på **Nej** för att validera kundsegment med en enda SQL-villkorsfråga.

Om du vill aktivera den här optimeringen går du till **[!UICONTROL Stores]> [!UICONTROL Settings] > [!UICONTROL Configuration] > [!UICONTROL Customers] > [!UICONTROL Customer Configuration] > [!UICONTROL Customer Segments] >[!UICONTROL Real-time Check if Customer is Matched by Segment]**.

Den här inställningen förbättrar prestandan vid validering av kundsegment om det finns många kundsegment i systemet. Det fungerar dock inte med [delade databasimplementeringar](../configuration/storage/multi-master.md) eller när det inte finns några registrerade kunder.

## Databasunderhållsschema {#database}

Vi rekommenderar att du gör regelbundna databassäkerhetskopieringar för instanserna Staging och Production. På grund av I/O-intensiva säkerhetskopieringsåtgärder kan det uppstå långsammare säkerhetskopiering och potentiella problem. Att köra databasprocesser för flera miljöer samtidigt kan eventuellt gå långsammare på grund av att det finns invändningar mot tillgängliga resurser.

För bättre prestanda bör du schemalägga säkerhetskopieringar så att de körs i följd, en åt gången, vid låg belastning. Med den här metoden undviker du I/O-problem och förkortar tiden för slutförande, särskilt för mindre instanser, större databaser och så vidare.

Vi rekommenderar till exempel att du schemalägger en säkerhetskopia av din produktionsdatabas som följs av mellanlagringsdatabasen när dina butiker stöter på lägre besök.

## Begränsa antalet produkter i rutnätet

För att förbättra prestanda för produktstödraster för stora kataloger rekommenderar vi att du begränsar antalet produkter i stödrastret med **[!UICONTROL Stores]> [!UICONTROL Settings] > [!UICONTROL Configuration] > [!UICONTROL Advanced] > [!UICONTROL Admin] > [!UICONTROL Admin Grids] >[!UICONTROL Limit Number of Products in Grid]** systemkonfigurationsinställningen.

Den här systemkonfigurationsinställningen är inaktiverad som standard. Genom att aktivera det kan du begränsa antalet produkter i rutnätet till ett visst värde. **[!UICONTROL Records Limit]** är en anpassningsbar inställning som har standardvärdet `20000`.
När inställningen **[!UICONTROL Limit Number of Products in Grid]** är aktiverad och antalet produkter i rutnätet är större än postgränsen, returneras den begränsade mängden poster. När gränsen nås döljs de totala antalet poster som hittats, antalet valda poster och sidnumreringselementen från rutnätets rubrik.

När det totala antalet produkter i rutnätet är begränsat påverkas inte massåtgärder i produktrutnätet. Det påverkar bara presentationsskiktet för produktrutnät. Det finns till exempel ett begränsat antal `20000` produkter i rutnätet, användaren klickar på **[!UICONTROL Select All]**, väljer massåtgärden **[!UICONTROL Update attributes]** och uppdaterar vissa attribut. Därför uppdateras alla produkter, inte den begränsade samlingen av `20000` poster.

Begränsningen för produktstödraster påverkar bara produktsamlingar som används av gränssnittskomponenter. Därför påverkas inte alla produktrutnät av den här begränsningen. Endast de som använder `Magento\Catalog\Ui\DataProvider\Product\ProductCollection`.
Du kan endast begränsa produktstödrastersamlingar på följande sidor:

* Katalogproduktrutnät
* Lägg till relaterat/merförsäljt/korsförsäljt produktrutnät
* Lägg till produkter i programpaketet
* Lägg till produkter i gruppprodukt
* Admin - Skapa ordersida

Om du inte vill att produktrutnätet ska begränsas bör du använda filter mer exakt så att resultatsamlingen har färre objekt än **[!UICONTROL Records Limit]**.
