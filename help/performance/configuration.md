---
title: Bästa praxis för konfiguration
description: Optimera svarstiden för driftsättningen av Adobe Commerce eller Magento Open Source med hjälp av dessa metodtips.
exl-id: 4cb0f5e7-49d5-4343-a8c7-b8e351170f91
source-git-commit: 1d7f5f58f8c21013c2ab0d68ab93a125ba0f3764
workflow-type: tm+mt
source-wordcount: '1448'
ht-degree: 0%

---

# Bästa praxis för konfiguration

I Commerce finns många inställningar och verktyg som du kan använda för att förbättra svarstiden på sidorna samt för att ge högre dataflöde.

## Kronjobb

Alla asynkrona åtgärder i [!DNL Commerce] utförs med Linux `cron` -kommando. Se [Konfigurera och kör cron](../configuration/cli/configure-cron-jobs.md) för att konfigurera det korrekt.

## Indexerare

En indexerare kan köras i **[!UICONTROL Update on Save]** eller **[!UICONTROL Update on Schedule]** läge. The **[!UICONTROL Update on Save]** indexeras omedelbart när katalogen eller andra data ändras. I det här läget används låg intensitet för uppdaterings- och bläddringsåtgärder i din butik. Det kan leda till betydande förseningar och otillgänglighet av data vid höga belastningar. Vi rekommenderar att du använder **Uppdatera enligt schema** i produktionen eftersom information om datauppdateringar lagras och indexeras av delar i bakgrunden via ett specifikt kroniskt jobb. Du kan ändra läge för varje [!DNL Commerce] indexeraren separat på  **[!UICONTROL System]** > [!UICONTROL Tools] > **[!UICONTROL Index Management]** konfigurationssida.

>[!TIP]
>
>Omindexering av MariaDB 10.4 och 10.6 tar längre tid jämfört med andra MariaDB eller [!DNL MySQL] versioner. Vi föreslår att du ändrar standardkonfigurationsinställningen för MariaDB, som beskrivs i [installationskrav](../installation/prerequisites/database/mysql.md).

## Cacheminnen

Aktivera alla cacheminnen från **[!UICONTROL System]** > [!UICONTROL Tools] > **[!UICONTROL Cache Management]** sida. Vi rekommenderar att du använder [!DNL Varnish], eftersom det är en effektiv cachelösning för produktionssidor.

## Asynkrona e-postmeddelanden

Om du aktiverar inställningen&quot;Asynkrona e-postmeddelanden&quot; flyttas processer som hanterar utcheckning och beställer e-postmeddelanden till bakgrunden. Om du vill aktivera den här funktionen går du till **[!UICONTROL Stores]> [!UICONTROL Settings] > [!UICONTROL Configuration] > [!UICONTROL Sales] > [!UICONTROL Sales Emails] > [!UICONTROL General Settings] >[!UICONTROL Asynchronous Sending]**. Se [Försäljningsmejl](https://docs.magento.com/user-guide/configuration/sales/sales-emails.html) i _Användarhandbok för Magento Open Source_ för mer information.

## Asynkron bearbetning av orderdata

Det kan finnas tillfällen då intensiv försäljning sker samtidigt som [!DNL Commerce] utför intensiv orderbehandling. Du kan konfigurera [!DNL Commerce] för att särskilja dessa två trafikmönster på databasnivå för att undvika konflikter mellan läs- och skrivåtgärder i motsvarande tabeller. Du kan lagra och indexera orderdata asynkront. Beställningar läggs i tillfällig lagring och flyttas gruppvis till orderhanteringsrutnätet utan några kollisioner. Du kan aktivera det här alternativet från **[!UICONTROL Stores]> [!UICONTROL Settings] > [!UICONTROL Configuration] > [!UICONTROL Advanced] > [!UICONTROL Developer] > [!UICONTROL Grid Settings] >[!UICONTROL Asynchronous indexing]**. Se [Schemalagda uppdateringar av stödraster](https://docs.magento.com/user-guide/sales/order-grid-updates-schedule.html) i _Användarhandbok för Magento Open Source_ för mer information.

>[!WARNING]
>
>The **[!UICONTROL Developer]** och alternativ är bara tillgängliga i [Utvecklarläge](../configuration/cli/set-mode.md). [Adobe Commerce i molninfrastruktur](https://devdocs.magento.com/cloud/requirements/cloud-requirements.html#cloud-req-test) stöder inte `Developer` läge.

## Spara asynkron konfiguration [!BADGE 2.4.7-beta1]{type=Informative url="/help/release/release-notes/commerce/2-4-7.md" tooltip="Finns endast i 2.4.7-beta1"}

För projekt med ett stort antal butikskonfigurationer kan det ta oordinerad tid att spara en butikskonfiguration eller resultera i en timeout. The _Async Config_ i aktiveras asynkrona konfigurationssparningar genom att ett cron-jobb körs som använder en konsument för att bearbeta sparandet i en meddelandekö. AsyncConfig är **inaktiverad** som standard.

Du kan aktivera AsyncConfig med kommandoradsgränssnittet:

```bash
bin/magento setup:config:set --config-async 1
```

The `set` skriver följande till `app/etc/env.php` fil:

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

I tider med intensiv försäljning [!DNL Commerce] kan skjuta upp lageruppdateringar relaterade till order. Detta minimerar antalet åtgärder och snabbar upp orderplaceringsprocessen. Det här alternativet är dock riskabelt och kan bara användas när restorder aktiveras i butiken, eftersom det här alternativet kan leda till negativa lagerkvantiteter. Det här alternativet kan ge avsevärda prestandaförbättringar i utcheckningsflöden för butiker som enkelt kan fylla i sitt lager på begäran. Om du vill aktivera fördröjda Stock-uppdateringar på din webbplats går du till **[!UICONTROL Stores]> [!UICONTROL Settings] > [!UICONTROL Configuration] > [!UICONTROL Catalog] > [!UICONTROL Inventory] > [!UICONTROL Product Stock Options] >[!UICONTROL Use Deferred Stock Update]**. Se [Hantera lager](https://docs.magento.com/user-guide/catalog/inventory.html) i _Adobe Commerce Användarhandbok_ för mer information.

>[!INFO]
>
>Det här alternativet är bara tillgängligt om **[!UICONTROL Backorder with any mode]** är aktiverat.

>[!INFO]
>
>Det här alternativet fungerar även med [Asynkron orderplacering](high-throughput-order-processing.md#asynchronous-order-placement) i kombination med [Inventory management](https://experienceleague.adobe.com/docs/commerce-admin/inventory/guide-overview.html).

## Optimeringsinställningar på klientsidan

För att förbättra svarstiderna på marknaden [!DNL Commerce] Gå till Admin i standardläge eller utvecklarläge och ändra följande inställningar:

**[!UICONTROL Stores]-> [!UICONTROL Configuration] -> [!UICONTROL Advanced] -> [!UICONTROL Developer]:**

| Inställningsgrupp | Inställning | Värde |
| ------------------- | -------------------------- | ------ |
| Stödrasterinställningar | Asynkron indexering | Aktivera |
| CSS-inställningar | Minimera CSS-filer | Ja |
| [!DNL JavaScript] Inställningar | Minify [!DNL JavaScript] Filer | Ja |
| [!DNL JavaScript] Inställningar | Aktivera [!DNL JavaScript] Paket | Ja |
| Mallinställningar | Minfy HTML | Ja |

>[!INFO]
>
>The **[!UICONTROL Developer]** och alternativ är bara tillgängliga i [Utvecklarläge](../configuration/cli/set-mode.md). [Adobe [!DNL Commerce] om molninfrastruktur](https://devdocs.magento.com/cloud/requirements/cloud-requirements.html#cloud-req-test) stöder inte `Developer` läge.

När du aktiverar **[!UICONTROL Enable [!DNL JavaScript] Bundling]** kan du tillåta att Commerce sammanfogar alla JS-resurser till ett eller flera paket som är inlästa på butikssidor. Paketeringen av JS resulterar i färre begäranden till servern, vilket förbättrar sidans prestanda. Det hjälper även webbläsaren att cachelagra JS-resurser vid det första anropet och återanvända dem för all vidare surfning. Det här alternativet ger även en lat utvärdering eftersom all JS läses in som text. Den initierar bara analys och utvärdering av kod efter att specifika åtgärder har utlösts på sidan. Den här inställningen rekommenderas dock inte för butiker där den första sidans laddningstid är extremt viktig eftersom allt JS-innehåll läses in vid det första anropet.

>[!INFO]
>
>Se [Optimering av CSS- och Javascript-filer på Adobe Commerce i molninfrastrukturen och Adobe Commerce](https://support.magento.com/hc/en-us/articles/360044482152) i Adobe Commerce Help Center_ om du vill ha mer information om hur du optimerar CSS och Javascript.

### Pakettips

* Vi rekommenderar att du använder verktyg från tredje part för miniatyr- och paketering (som [r.js](https://requirejs.org/)). [!DNL Commerce] Inbyggda mekanismer är inte optimala och levereras som reservalternativ.
* Att aktivera HTTP2-protokollet kan vara ett bra alternativ till att använda JS-paketering. Protokollet ger i stort sett samma fördelar.
* Vi rekommenderar inte att du använder föråldrade inställningar som att sammanfoga JS- och CSS-filer, eftersom de bara är utformade för synkront inläst JS i sidans HEAD-avsnitt. Om du använder den här tekniken kan paketeringen och requireJS-logiken fungera felaktigt.

## Validering av kundsegment

Handlare som har ett stort antal [kundsegment](https://docs.magento.com/user-guide/marketing/customer-segments.html) kan försämra prestandan avsevärt med kundens aktiviteter, som kundinloggning och tillägg av produkter i kundvagnen.

Kundåtgärder utlöser en valideringsprocess för kundsegment, vilket kan leda till sämre prestanda. Som standard validerar Adobe Commerce varje segment i realtid för att definiera vilka kundsegment som matchas och vilka som inte gör det.

För att undvika prestandaförsämringar kan du ange **[!UICONTROL Real-time Check if Customer is Matched by Segment]** systemkonfigurationsalternativ till **Nej** för att validera kundsegment med en enda kombinerad SQL-villkorsfråga.

Om du vill aktivera optimeringen går du till **[!UICONTROL Stores]> [!UICONTROL Settings] > [!UICONTROL Configuration] > [!UICONTROL Customers] > [!UICONTROL Customer Configuration] > [!UICONTROL Customer Segments] >[!UICONTROL Real-time Check if Customer is Matched by Segment]**.

Den här inställningen förbättrar prestandan vid validering av kundsegment om det finns många kundsegment i systemet. Det fungerar dock inte med [delad databas](../configuration/storage/multi-master.md) implementeringar eller när det inte finns några registrerade kunder.

## Databasunderhållsschema {#database}

Vi rekommenderar att du gör regelbundna databassäkerhetskopieringar för instanserna Staging och Production. På grund av I/O-intensiva säkerhetskopieringsåtgärder kan det uppstå långsammare säkerhetskopiering och potentiella problem. Att köra databasprocesser för flera miljöer samtidigt kan eventuellt gå långsammare på grund av att det finns invändningar mot tillgängliga resurser.

För bättre prestanda bör du schemalägga säkerhetskopieringar så att de körs i följd, en åt gången, vid låg belastning. Med den här metoden undviker du I/O-problem och förkortar tiden för slutförande, särskilt för mindre instanser, större databaser och så vidare.

Vi rekommenderar till exempel att du schemalägger en säkerhetskopia av din produktionsdatabas som följs av mellanlagringsdatabasen när dina butiker stöter på lägre besök.

## Begränsa antalet produkter i rutnätet

För att förbättra prestanda för stora kataloger rekommenderar vi att du begränsar antalet produkter i rutnätet med **[!UICONTROL Stores]> [!UICONTROL Settings] > [!UICONTROL Configuration] > [!UICONTROL Advanced] > [!UICONTROL Admin] > [!UICONTROL Admin Grids] >[!UICONTROL Limit Number of Products in Grid]** systemkonfigurationsinställning.

Den här systemkonfigurationsinställningen är inaktiverad som standard. Genom att aktivera det kan du begränsa antalet produkter i rutnätet till ett visst värde. **[!UICONTROL Records Limit]** är en anpassningsbar inställning som har standardvärdet `20000`.
När **[!UICONTROL Limit Number of Products in Grid]** inställningen är aktiverad och antalet produkter i rutnätet är större än postgränsen, så returneras den begränsade mängden poster. När gränsen nås döljs de totala antalet poster som hittats, antalet valda poster och sidnumreringselementen från rutnätets rubrik.

När det totala antalet produkter i rutnätet är begränsat påverkas inte massåtgärder i produktrutnätet. Det påverkar bara presentationsskiktet för produktrutnät. Det finns t.ex. ett begränsat antal `20000` produkter i rutnätet klickar användaren på **[!UICONTROL Select All]**, markerar **[!UICONTROL Update attributes]** massåtgärd och uppdaterar vissa attribut. Därför uppdateras alla produkter, inte den begränsade samlingen av `20000` poster.

Begränsningen för produktstödraster påverkar bara produktsamlingar som används av gränssnittskomponenter. Därför påverkas inte alla produktrutnät av den här begränsningen. Endast de som använder `Magento\Catalog\Ui\DataProvider\Product\ProductCollection`.
Du kan endast begränsa produktstödrastersamlingar på följande sidor:

* Katalogproduktrutnät
* Lägg till relaterat/merförsäljning/korsförsäljning av produkter
* Lägg till produkter i programpaketet
* Lägg till produkter i gruppprodukt
* Admin - Skapa ordersida

Om du inte vill att produktrutnätet ska begränsas bör du använda filter mer exakt så att resultatsamlingen har färre objekt än **[!UICONTROL Records Limit]**.
