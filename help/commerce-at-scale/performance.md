---
title: Optimering av AEM
description: Optimera din standardkonfiguration av Adobe Experience Manager så att den stöder hög belastning på Adobe Commerce.
exl-id: 923a709f-9048-4e67-a5b0-ece831d2eb91
source-git-commit: e76f101df47116f7b246f21f0fe0fa72769d2776
workflow-type: tm+mt
source-wordcount: '2248'
ht-degree: 0%

---

# Optimering av AEM

AEM är en omvänd proxy som hjälper till att leverera en miljö som är både snabb och dynamisk. Den fungerar som en del av en statisk HTML-server, t.ex. Apache HTTP Server, i syfte att lagra (eller &quot;cachelagra&quot;) så mycket som möjligt av webbplatsinnehållet i form av statiska resurser. Den här metoden syftar till att minimera behovet av att få tillgång till AEM sidåtergivningsfunktioner och Adobe Commerce GraphQL-tjänsten så mycket som möjligt. Resultatet av att hantera en stor del av sidorna som statiska HTML, CSS och JS ger användarna prestandafördelar och minskar behovet av infrastruktur i miljön. Alla sidor eller frågor som troligen upprepas från användare till användare ska cachelagras.

Följande avsnitt visar på en hög nivå det rekommenderade fokusområdet som ska granskas för att möjliggöra effektiv cachning av AEM i en CIF/Adobe Commerce-miljö.

## TTL-baserad cachelagring av AEM

Cachelagring av så mycket som möjligt av webbplatsen på avsändare är bästa praxis för alla AEM projekt. Om du använder tidsbaserad cacheogiltigförklaring cachelagras serversidans renderade CIF-sidor under en begränsad tidsperiod. När den angivna tiden har gått ut återskapar nästa begäran sidan från den AEM utgivaren och Adobe Commerce GraphQL och sparar den i dispatcherns cache igen tills nästa ogiltigförklaring görs.

TTL-cachningsfunktionen kan konfigureras i AEM med komponenten Dispatcher TTL i ACS-AEM Commons-paketet och med inställningen /enableTTL 1 i Dispatcher.any-konfigurationsfilen.

Om det här alternativet är aktiverat utvärderas svarshuvuden från serverdelen och om de innehåller ett max-age-värde för Cache-Control eller ett förfallodatum skapas en extra, tom fil bredvid cachefilen, med en ändringstid som är lika med förfallodatumet. När den cachelagrade filen begärs efter ändringstiden återbegärs den automatiskt från serverdelen. Detta ger en effektiv cachningsmekanism som inte kräver någon manuell åtgärd eller underhåll när produktuppdateringsfördröjningen har bekräftats och accepterats av företagsintressenter.

## Webbläsarcachelagring

TTL-metoden för avsändare ovan minskar avsevärt antalet förfrågningar och belastningen på utgivaren, men det finns vissa resurser som sannolikt inte kommer att ändras och därför kan till och med förfrågningar till avsändaren minskas genom att relevanta filer cachelagras lokalt i användarens webbläsare. Till exempel behöver webbplatsens logotyp, som visas på varje sida på webbplatsen i webbplatsmallen, inte efterfrågas varje gång till avsändaren. Detta kan i stället lagras i användarens webbläsarcache. Minskade bandbreddskrav för varje sidinläsning skulle få stor effekt på webbplatsens svarstider och sidinläsningstiderna.

Cachelagring på webbläsarnivå sker vanligtvis via &quot;Cache-Control: max-age=&quot; svarshuvud. Inställningen maxage anger för webbläsaren hur många sekunder filen ska cachelagras i innan ett försök görs att &quot;verifiera om&quot; eller begära den från platsen igen. Konceptet cacheminne max-age kallas vanligtvis &quot;Cachelagring förfaller&quot; eller TTL (&quot;TTL-tid&quot;). Leverera e-handelsupplevelser i stor skala - med Adobe Experience Manager, Commerce Integration Framework, Adobe Commerce 7

Vissa delar av en AEM/CIF/Adobe Commerce-webbplats som kan ställas in för cachelagring i klientens webbläsare är:

- Bilder (i själva AEM, t.ex. webbplatslogotyp och malldesignbilder - katalogproduktbilder anropas från Adobe Commerce via Snabbt och cachelagring av dessa bilder behandlas senare)
- HTML-filer (för sidor som ändrats sällan - villkor osv.)
- CSS-filer
- Alla JavaScript-filer för webbplatser - inklusive CIF JavaScript-filer

## Optimering av tidsgräns för statusnivåpanel för utskicksstatus

I standardkonfigurationen för dispatcher används inställningen /statfillevel &quot;0&quot; - det innebär att en enskild .stat-fil placeras i roten för htdocs-katalogen (dokumentets rotkatalog). Om en ändring görs av en sida eller fil i AEM uppdateras ändringstiden för den här enskilda lägesfilen till tidpunkten för ändringen. Om tiden är nyare än resursens ändringstid kommer dispatchern att granska alla resurser som ogiltigförklaras och alla efterföljande begäranden om en ogiltig resurs kommer att utlösa ett anrop till publiceringsinstansen. Så i stort sett, med den här inställningen blir alla aktiveringar ogiltiga i hela cachen.

För alla webbplatser, i synnerhet e-handelssajter med stor belastning, skulle detta innebära en onödig belastning på AEM-publiceringsnivån för att hela webbplatsstrukturen skulle bli ogiltig med endast en uppdatering.

I stället kan statusnivåinställningen ändras till ett högre värde, som motsvarar djupet för underkataloger i htdocs-katalogen från dokumentets rotkatalog, så att när en fil som finns på en viss nivå blir ogiltig uppdateras bara filer på den .stat-katalognivån och nedan.

Till exempel: Säg att du har en produktsidmall på:

```
content/ecommerce/us/en/products/product-page.html
```

Varje mappnivå skulle ha&quot;statusnivå&quot; - vilket visas i tabellen ovan.

| innehåll (docroot) | e-handel | oss | en | produkter | product-page.tml |
|-------------------|-----------|----|----|----------|------------------|
| 0 | 1 | 2 | 3 | 4 | - |

I det här fallet, om du har lämnat statfillevel-egenskapen inställd på standardvärdet &quot;0&quot; och product-page.html-mallen uppdateras och aktiveras så att en ogiltigförklaring aktiveras, kommer alla .stat-filer från docroot till level 4 att påverkas och filerna ogiltigförklaras, vilket ger en ytterligare begäran från AEM publiceringsinstanser för alla sidor på webbplatsen (inklusive andra webbplatser, länder och språk) från den enskilda ändringen.

Om statfillevel-egenskapen däremot är inställd på nivå 4 och en ändring görs i product-page.html - så kommer endast .stat-filen i produktkatalogen för den specifika webbplatsen/landet/språket att påverkas.

Observera att .stat-filnivån inte ska ställas in på en för hög nivå - över 20 kan ha prestandapåverkan. Om du utför en gruppfilaktivering medan du kör ett prestandatest bör du ha rätt nivå att justera din statusnivå till.

En annan inställning som optimeras när statusfilnivån konfigureras är inställningen GracePeriod. Detta anger hur många sekunder en inaktuell, automatiskt ogiltigförklarad resurs fortfarande kan betjänas från cachen efter den senaste aktiveringen. Automatiskt ogiltiga resurser ogiltigförklaras av en aktivering (när deras sökväg matchar avsnittet dispatcher/invalidate och till nivån som anges i egenskapen statfilesLevel). Om du anger inställningen för GracePeriod till 2 sekunder kan du förhindra ett scenario där flera begäranden skickas kontinuerligt till utgivaren, även medan utgivaren fortfarande håller på att skapa den nya sidan.

>[!NOTE]
>
> Mer detaljerad information om detta finns i [aem-dispatcher-experiment](https://github.com/adobe/aem-dispatcher-experiments/tree/main/experiments/gracePeriod) GitHub-databas.

## CIF - GraphQL-cachning via komponenter

Enskilda komponenter i AEM kan ställas in för cachelagring, vilket innebär att GraphQL-begäran till Adobe Commerce anropas en gång och sedan hämtas efterföljande begäranden, upp till den konfigurerade tidsgränsen, från AEM cache och skulle inte placera ytterligare inläsning på Adobe Commerce. Exempel är en webbplatsnavigering baserad på ett kategoriträd som visas på varje sida och alternativ inom en fasetterad sökfunktion - det är bara två områden där resurskrävande frågor på Adobe Commerce behöver byggas men som sannolikt inte ändras regelbundet och därför är bra att välja mellan för cachelagring. På det här sättet kommer, till exempel, även när utgivaren återskapar en PDP eller PLP, den resurskrävande GraphQL-begäran för navigeringsbygget inte att drabba Adobe Commerce och kan hämtas från GraphQL-cachen AEM CIF.

Ett exempel nedan är om navigeringskomponenten ska cachelagras eftersom samma GraphQL-fråga skickas till alla sidor på platsen. I begäran nedan cachelagras de senaste 100 posterna under 10 minuter för navigeringsstrukturen:

```
venia/components/structure/navigation:true:100:600
```

I exemplet nedan cachelagras de senaste 100 fasetterade sökalternativen på en söksida i en timme:

```
com.adobe.cq.commerce.core.search.services.SearchFilterService:true:100:3600
```

Begäran, inklusive alla anpassade http-huvuden och variabler, måste matcha exakt för att cachen ska&quot;trätas&quot; och för att förhindra att Adobe Commerce anropas igen. Det bör noteras att det inte finns något enkelt sätt att göra cachen ogiltig manuellt när den väl har angetts. Detta kan innebära att om en ny kategori läggs till i Adobe Commerce, kommer den inte att börja visas i navigeringen förrän den förfallotid som angetts i cachen ovan har gått ut och GraphQL-begäran har uppdaterats. Detsamma gäller för sökfacets. Med tanke på de prestandafördelar som cachelagringen medför är detta dock vanligtvis en godtagbar kompromiss.

Cachelagringsalternativen ovan kan ställas in med konfigurationskonsolen för AEM OSGi i GraphQL Client Configuration Factory. Varje cachekonfigurationspost kan anges med följande format:

```
• NAME:ENABLE:MAXSIZE:TIMEOUT like for example mycache:true:1000:60 where each attribute is defined as:
    › NAME (String): name of the cache
    › ENABLE (true|false): enables or disables that cache entry
    › MAXSIZE (Integer): maximum size of the cache (in number of entries)
    › TIMEOUT (Integer): timeout for each cache entry (in seconds)
```

## Hybrid-cachning - klientsidan begär GraphQL-filer på cachelagrade dispatchersidor

Det är också möjligt att använda en hybridmetod för cachelagring av sidor: en CIF-sida kan innehålla komponenter som alltid begär den senaste informationen från Adobe Commerce direkt från kundens webbläsare. Detta kan vara användbart för specifika delar av sidan i en mall som är viktiga att hålla uppdaterad med realtidsinformation: Produktpriser inom en PDP, till exempel. Om priserna ändras ofta på grund av dynamisk prismatchning kan den informationen konfigureras så att den inte cachas av dispatchern, i stället kan priserna hämtas på klientsidan i kundens webbläsare direkt från Adobe Commerce via GraphQL API:er med AEM CIF-webbkomponenter.

Detta kan konfigureras via AEM komponentinställningar - för prisinformation på produktlistsidor kan detta konfigureras i produktlistmallen, markera produktlistkomponenten på sidinställningarna och markera alternativet &quot;load prices&quot;. Samma tillvägagångssätt fungerar för lagernivåer.

Metoderna ovan bör endast användas i de fall då det krävs information i realtid som är ständigt aktuell. I exemplet ovan med prissättning kan man komma överens med affärsintressenter om att bara uppdatera priserna dagligen vid låg trafiktid och sedan utföra cachetömning. På så sätt elimineras behovet av information om realtidspriser och den efterföljande extra belastningen på Adobe Commerce när varje sida med prisinformation skapas.

## Otillgängliga GraphQL-begäranden

Specifika dynamiska datakomponenter på sidor får inte cachelagras och kräver alltid ett GraphQL-samtal till Adobe Commerce, t.ex. för kundvagnen och samtal på kassasidorna. Den här informationen är specifik för en användare och ändras ständigt på grund av kundens aktivitet på webbplatsen, t.ex. genom att produkter läggs till i kundvagnen.

GraphQL Query-resultat ska inte cachas för inloggade kunder om webbplatsens design ger olika svar beroende på användarens roll. Du kan till exempel skapa flera kundgrupper och ange olika produktpriser eller olika synlighet för produktkategorier för varje grupp. Cachelagra resultat som dessa kan få kunderna att se priserna för en annan kundgrupp eller få felaktiga kategorier att visas.

## Spårningsparametrar ignoreras i cachen AEM dispatcher

E-handelswebbplatser kan leda till trafik till deras webbplats med PPC-sökannonser eller kampanjer i sociala medier.

Användningen av dessa medier innebär att ett spårnings-ID läggs till på den utgående länken från den plattformen. Facebook kommer till exempel att lägga till ett Facebook Click ID (fbclid) i URL:en. Google Adverts kommer att lägga till ett Google Click ID (gclid), vilket gör att inkommande länkar till AEM visas som nedan:

```
https://www.adobe.com/?gclid=oirhgj34y43yowiahg9u3t
```

gclid och fbclid ändras för alla användare som klickar på annonsen, det är avsett för spårningsändamål, men med standardinställningarna ser AEM alla förfrågningar som en unik sida, vilket skulle kringgå dispatchern och generera onödig extra belastning på utgivaren och Adobe Commerce.

Vid en plötslig händelse kan detta till och med leda till att de AEM utgivarna blir överbelastade och inte svarar. När en parameter är inställd på att ignoreras för en sida cachelagras sidan första gången som sidan begärs. Efterföljande begäranden för sidan skickas till den cachelagrade sidan, oavsett värdet på parametern i begäran.

>[!NOTE]
>
>Läs mer om vikten av att ställa in `ignoreUrlParams` finns i [aem-dispatcher-experiment](https://github.com/adobe/aem-dispatcher-experiments/tree/main/experiments/ignoreUrlParams) GitHub-databas.

Den bör därför konfigureras så att den ignorerar alla parametrar som standard i ignoreUrlParams, utom när en GET-parameter används som skulle ändra sidans HTML-struktur. Ett exempel på detta är en söksida där söktermen finns i URL:en som GET-parameter. I det här fallet bör du manuellt konfigurera ignoreUrlParams så att parametrar som gclid, fbclid och andra spårningsparametrar som används i dina annonskanaler ignoreras, vilket gör att de GET-parametrar som krävs för vanliga webbplatsåtgärder inte påverkas.

## MPM-arbetare begränsar antalet utskickare

MPM-arbetarnas inställningar är en avancerad konfiguration för Apache HTTP-servern som skulle kräva grundlig testning för att optimera baserat på Dispatcher-datorns tillgängliga processor och RAM. I den här rapporten föreslår vi dock att ServerLimit och MaxRequestWorkers ska ökas till en nivå som serverns tillgängliga processor och RAM ska stödja, och sedan ökas både MinSpareThreads och MaxSpareThreads till en nivå som matchar MaxRequestWorkers.

Den här konfigurationen lämnar Apache HTTP på en inställning för fullständig beredskap, vilket är en högpresterande konfiguration för servrar med stort RAM-minne och flera processorkärnor. Den här konfigurationen ger bästa möjliga svarstider från Apache HTTP genom att behålla beständiga öppna anslutningar som är klara att betjäna förfrågningar och tar bort eventuella förseningar i att skapa nya processer som svar på plötsliga trafikökningar, som vid blixtförsäljning.
