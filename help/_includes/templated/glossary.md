---
source-git-commit: 0d5eeb691281d7c62aa64a9d8cd042f18504a67f
workflow-type: tm+mt
source-wordcount: '6370'
ht-degree: 0%

---
# Adobe Commerce-ordlista

## A

### ovanför vikningen

_adjektiv_

I ett webbläsarfönster är det innehåll som är omedelbart synligt efter att en webbsida har lästs in och innan en användare rullade nedåt på sidan.
När du utformar din layout kan du använda flexibla format för att bäst visa de produkter, funktioner, försäljning, meddelanden, alternativ och så vidare som har högst prioritet i det här området.

När det gäller mobiler och surfplattor skiljer sig området över det förändrade avsevärt, särskilt skärmstorleken och skärmens storlek och orientering vid visning (stående eller liggande).
Genom att använda responsiva teman och tester kan du hitta rätt blandning av innehåll och layout.

_Termattribut:_

* _Fält: design_

### aktiv gren

_substantiv_

En aktiv gren eller miljö är en gren som är ansluten till en distribuerad eller körs instans med tillgång till tjänster.
När du inaktiverar tas anslutningen till tjänsterna och till den instans som körs bort, men koden bevaras.
Det blir en vanlig Git-gren.

_Termattribut:_

* _Fält: cloud_

### adapter

_substantiv_

En klass som gör att två annars inkompatibla system kan fungera tillsammans utan att ändra systemets källkod.
Exempel är databasadaptrar, cacheadaptrar, filsystemadaptrar, kort för efterprocessorbibliotek och andra typer av datoradaptrar.

_Termattribut:_

* _Fält: programmering_

### admin

_substantiv_

I programvara är det en användarroll med fullständig administratörsbehörighet som hanterar alla funktioner.
I Adobe Commerce har administratörsanvändare fullständig behörighet och tillgång till alla funktioner, alternativ och funktioner i Admin.
De kan också skapa användare och roller.

Läs mer: [Lägga till användare](https://experienceleague.adobe.com/docs/commerce-admin/systems/user-accounts/permissions-users-all.html?lang=sv-SE)

_Termattribut:_

* _Fält: e-handelsprogramvara_
* _Synonymer: administratör, superanvändare_
* _Relaterade termer: e-handelsadministratör_

### Administratörsområde

_substantiv_

Det lösenordsskyddade back office i din butik där beställningar, kataloger, innehåll och konfigurationer hanteras.
Användare har tillgång till administrationsområdet för att hantera butiken, inklusive produkter, order, leveranser, CMS-innehåll, design av butiken, kundinformation osv.
Administratörsanvändare har en associerad roll med behörigheter som styr åtkomst till funktioner, alternativ och funktioner.

Läs mer: [Adobe Commerce användarhandbok](https://experienceleague.adobe.com/docs/commerce-admin/user-guides/home.html?lang=sv-SE)

_Termattribut:_

* _Fält: e-handelsprogramvara_
* _Synonymer: Admin, Admin Panel, backend, Administration Interface, Admin UI_
* _Relaterade termer: admin_

### ADMIN-variabler

_substantiv_

ADMIN-variabler är projektmiljövariabler som åsidosätter konfigurationsinställningarna för administratörskontot för åtkomst till administratörsgränssnittet.

Läs mer: [ADMIN-variabler](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-admin.html?lang=sv-SE)

_Termattribut:_

* _Fält: admin, moln_

### adminhtml

_substantiv_

Det interna områdesnamn som tilldelats administratören.

Läs mer: [Adobe Commerce användarhandbok](https://experienceleague.adobe.com/docs/commerce-admin/user-guides/home.html?lang=sv-SE)

_Termattribut:_

* _Fält: e-handelsprogramvara_
* _Relaterade termer: område, e-handelsadministratör_

### area

_substantiv_

Område är en abstrakt term för ett Magento-programomfång.
Områden är logiska komponenter som organiserar kod för optimerad bearbetning av begäranden.
Områden minskar minneskraven för konfigurationsobjekt som används från butiken och effektiviserar webbtjänstanrop genom att bara läsa in den nödvändiga beroende koden.
Varje område kan innehålla helt olika kod för att bearbeta URL:er och förfrågningar.

Adobe Commerce omfattar följande:

* Admin (adminhtml)
* Storefront
* Webb-API REST (webapi_rest)

_Termattribut:_

* _Fält: e-handelsprogramvara_
* _Relaterade termer: handelskomponent, storefront_

### attribute

_substantiv_

En egenskap eller egenskap hos en produkt som beskriver någon aspekt av produkten.
Adobe Commerce-användare kan skapa anpassade attribut som läggs till i standardattributuppsättningen eller en anpassad attributuppsättning.
Skapa dessa attribut med Admin eller via programmering.
Exempel: färg, storlek, vikt, pris, ålder, kön och så vidare.

Anpassade attribut är en typ av Entity-Attribute-Value-attribut (EAV).

För integreringar som Google Shopping ads Channel och Amazon Sales Channel kan du mappa Commerce-attribut till attribut i tredjepartsleverantörer för att visa och sälja produkter, displayannonser.

Läs mer: [EAV och extension_attributes](https://developer.adobe.com/commerce/php/development/components/attributes/)

_Termattribut:_

* _Fält: e-handelsprogram, produkt_
* _Synonymer: produktattribut, anpassat attribut_
* _Relaterade termer: tilläggsattribut_

### attributgrupp

_substantiv_

En logisk gruppering av attribut i en attributuppsättning.

_Termattribut:_

* _Fält: e-handelsprogramvara_
* _Relaterade termer: attribut_

### attributuppsättning

_substantiv_

En samling attributgrupper, anpassade för en viss produkt.
Exempel: En T-shirts-attributuppsättning kan innehålla färg, storlek, kön och märke.

_Termattribut:_

* _Fält: e-handelsprogram, produkt_
* _Relaterade termer: attribut_

### genomsnittlig lagerkostnad

_substantiv_

Produktpris, minus kuponger eller rabatter, plus frakt och moms.
Det genomsnittliga värdet bestäms genom att den ingående kostnaden för lagret läggs till varje månad, plus den slutliga kostnaden för lagret för periodens sista månad.

_Termattribut:_

* _Fält: produkt, pris, lager_

## B

### basvaluta

_substantiv_

Den primära valutan som används per butiksvy för alla onlinebetalningar.
Butiker kan ta emot valutor från över 200 länder runt om i världen.
Affärsfronten innehåller en valutaväljare för flera godkända valutor för ett visst land eller språkområde.
Valutasymboler visas i produktpriser och försäljningsdokument som order och fakturor.
Du kan anpassa valutasymbolerna efter behov och ange hur priset ska visas separat för varje butik eller vy.

Läs mer: [Valuta](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/site-store/currency/currency.html?lang=sv-SE)

_Termattribut:_

* _Fält: pricing_

### gruppbearbetning

_substantiv_

Om du vill utföra en uppgift eller ändra flera objekt samtidigt, utan manuell upprepning.

_Termattribut:_

* _Fält: programmering_
* _Synonymer: gruppåtgärder_

### block

_substantiv_

En enhet för sidutdata som återger visst distinkt innehåll - information, användargränssnittselement - allt som är visuellt påtagligt för slutanvändaren.
[Block](https://experienceleague.adobe.com/docs/commerce-admin/content-design/elements/blocks/blocks.html?lang=sv-SE) implementeras och tillhandahålls av moduler.
Blocken använder mallar för att generera HTML.
Exempel på block är en kategorilista, en minikundvagn, produkttaggar och produktlista.

[Dynamiska block](https://experienceleague.adobe.com/docs/commerce-admin/content-design/elements/dynamic-blocks/dynamic-blocks.html?lang=sv-SE) tillhandahåller innehåll baserat på logik, till exempel prisregler.

Page Builder utökas när [block](https://experienceleague.adobe.com/docs/commerce-admin/page-builder/add-content/block.html?lang=sv-SE) och [dynamiska block](https://experienceleague.adobe.com/docs/commerce-admin/page-builder/add-content/dynamic-block.html?lang=sv-SE) skapas.

_Termattribut:_

* _Fält: e-handelsprogramvara_
* _Synonymer: Dynamiska block_
* _Relaterade termer: cms-block, statiskt block, behållare, layout_

### varumärke

_substantiv, verb_

En unik identitet som definierar en viss produkt eller produktgrupp av tillverkaren eller Designer.
Bland dessa märks namnmärkena för kläder, apparater, lyxartiklar och så vidare.
Företaget kan också vara varumärket, sälja produkter under flera varumärken baserat på affärsenhet, målgrupp osv.

Använd anpassade attribut för att spara varumärkesinformation för produkterna.

Vissa tillägg och integreringar kan använda eller kräva ett varumärke för dina produkter, till exempel Google Shopping Channel och Amazon Sales Channel.

_Termattribut:_

* _Fält: business_

### tegelsten och murbruk

_adjektiv_

Ett detaljhandelsföretag med en permanent fysisk plats, till skillnad från företag som fungerar praktiskt taget eller enbart via internet.

För [Inventory management](https://experienceleague.adobe.com/docs/commerce-admin/inventory/sources/sources-manage.html?lang=sv-SE) och [Order Management](#oms) är den här butiken en källa för att spåra produktkvantiteter, leveransorder och stöd för upphämtning i butik.

_Termattribut:_

* _Fält: företag, lager_

### gruppåtgärder

_substantiv_

Gruppåtgärder är åtgärder som utförs i stor skala.
Exempel på gruppåtgärder är att importera eller exportera artiklar, ändra priser i en massskala och tilldela produkter till ett lager.

Läs mer: [DevDocs-gruppåtgärder](https://developer.adobe.com/commerce/php/development/components/message-queues/bulk-operations/)

_Termattribut:_

* _Fält: programmering_

### paketprodukt

_substantiv_

Gör att kunderna kan sätta ihop en egen, anpassningsbar produkt av olika alternativ och konfigurationer.
Varje objekt i paketet är antingen en separat enkel eller virtuell produkt.

Läs mer: [Konfigurerbara produkter](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/types/product-create-configurable.html?lang=sv-SE)

_Termattribut:_

* _Fält: e-handelsprogram, produkt_
* _Relaterade termer: enkel produkt, virtuell produkt, produkttyper_

### paketerat tillägg

_substantiv_

Koden som utökar eller anpassar Adobe Commerce-beteendet betraktas som ett paketerat tillägg.
Den kan innehålla moduler, teman och språkpaket.

_Termattribut:_

* _Fält: bundlat tillägg, tillägg_
* _Synonymer: tillägg_
* _Relaterade villkor: tillägg, leverantörbundet tillägg_

## C

### cachelagra serverdel

_substantiv_

Lagrar cacheposter i ett serverdelssystem på två nivåer i Zends standardramverk.
En cache på första nivån är snabb - till exempel en APC eller en cache-lagrad serverdel - men den är begränsad och stöder inte taggning och gruppering av cacheposter.
En cache på andra nivån - till exempel ett filsystem eller en Redis-serverdel - är långsammare men stöder taggning och gruppering.

_Termattribut:_

* _Fält: programmering_
* _Relaterade termer: backend_

### cachefrontend

_substantiv_

Anger vilken typ av data som lagras i cachens serverdel.

_Termattribut:_

* _Fält: programmering_
* _Relaterade termer: front_

### cachetyp

_substantiv_

I ett cacheminne lagras data så att framtida anrop av dessa data kan läsas in snabbare.

Adobe Commerce innehåller följande typer:
* Konfiguration
* Layouter
* Blockera utdata för HTML
* Samlingsdata
* Reflektionsdata
* Databas-DDL-åtgärder
* Kompilerad konfiguration
* EAV-typer och -attribut
* Kundmeddelande
* Integrationskonfiguration
* API-konfiguration för integrering
* Sidcache (den mest välkända)
* Konfiguration av webbtjänster
* Översättningar
* Målregel
* Google produktcache
* Hörn

Andra typer kan skapas och definieras.

_Termattribut:_

* _Fält: programmering_

### hämtning

_verb_

Processen att konvertera ett auktoriserat orderbelopp till en fakturerbar transaktion.
Transaktioner kan inte registreras förrän de har godkänts och tillstånd kan inte inhämtas förrän varorna eller tjänsterna har levererats.

_Termattribut:_

* _Fält: business_
* _Relaterade villkor: auktorisering, orderstatus_

### kortinnehavare

_substantiv_

En person som auktoriserats av ett finansinstitut att göra inköp på ett kreditkortskonto.

_Termattribut:_

* _Fält: företag, beställning_

### kundvagnsregler

_substantiv_

Prisregler som tillämpas på kundvagnen och utlöser en åtgärd som svar på en uppsättning villkor.
Används för att skapa kampanjer.

_Termattribut:_

* _Fält: e-handelsprogramvara, priser, produkt_
* _Relaterade termer: katalogregler, kundvagn_

### katalog

_substantiv_

För handlare representerar katalogen deras produktlager.
I Adobe Commerce-arkitekturen består katalogen av kategorier, produkter och produktattribut.

Varje Commerce-butik har bara en produktkatalog, som delas av alla butiksvyer.
I en installation i flera butiker kan varje butik ha en separat katalog eller dela katalogen.
Den aktuella lagringskatalogen bestäms av standardrotkategorin, som är synlig för användaren i den översta navigeringen (huvudmenyn) i butiken.
(Termen &quot;rotkategori&quot; kan vara förvirrande eftersom &quot;rotkategorin&quot; egentligen inte är en kategori alls, utan en behållare för menyn, som består av kategorier och underkategorier.)

Du kan skapa så många rotkategorier du vill, men bara en (standardvärdet) kan användas åt gången.

_Termattribut:_

* _Fält: e-handelsprogramvara, priser, produkt_
* _Relaterade termer: delad katalog, katalogregel_

### katalogregler

_substantiv_

Prisregler som tillämpas på specifika produkter och som utlöser en åtgärd som svar på en uppsättning villkor.
Används för att skapa kampanjer.

_Termattribut:_

* _Fält: e-handelsprogramvara, priser, produkt_
* _Relaterade termer: kundvagnsregler, katalog_

### kategori

_substantiv_

En grupp produkter som har något gemensamt.
Butikens huvudmeny är ordnad i kategorier och underkategorier.

_Termattribut:_

* _Fält: e-handelsprogram, produkt_

### utcheckning

_substantiv_

Processen för att samla in den betalnings- och leveransinformation som krävs för att slutföra köpet av artiklar i kundvagnen.
När kunden har granskat informationen och skickat in beställningen skickas en bekräftelse via e-post till kunden.

Utcheckningen har många alternativ och konfigurationer som är färdiga att användas och som har utökats.

Mer information: [Självstudiekurs om utcheckning](https://developer.adobe.com/commerce/php/tutorials/frontend/custom-checkout/)

_Termattribut:_

* _Fält: företag, design, order, produkt, programmering_

### molnvariabler

_substantiv_

Molnvariabler är miljövariabler som är specifika för Adobe Commerce i molninfrastrukturen och använder prefixet **`MAGENTO_CLOUD`**.

Läs mer: [Cloud-variabler](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-cloud.html?lang=sv-SE)

_Termattribut:_

* _Fält: cloud_

### CMS block

_substantiv_

En särskild variant av [block](https://experienceleague.adobe.com/docs/commerce-admin/content-design/elements/blocks/blocks.html?lang=sv-SE) som bara kan skapas i Admin och som inte kan refereras via layoutfiler.

_Termattribut:_

* _Fält: e-handelsprogramvara_
* _Relaterade termer: block, statiskt block_

### komplexa data

_substantiv_

Data som är kopplade till flera produktalternativ.

_Termattribut:_

* _Fält: programmering_

### komponent

_substantiv_

Används för att referera till en modul, ett tema eller ett språkpaket i Adobe Commerce.

_Termattribut:_

* _Fält: e-handelsprogramvara_
* _Synonymer: komponent_
* _Relaterade termer: ui-komponent_

### konfigurerbar produkt

_substantiv_

En konfigurerbar produkt ser ut som en enskild produkt med listrutor med alternativ för varje ändring.
Varje alternativ är i själva verket en separat enkel produkt med en unik SKU, som gör det möjligt att spåra lager för varje produktvariation.
För att uppnå en liknande effekt kan en enkel produkt användas med anpassade alternativ, men utan möjlighet att spåra lager för varje variation.
Produkter med flera alternativ kallas ibland sammansatta produkter.

Även om en konfigurerbar produkt använder fler SKU:er, och till att börja med tar lite längre tid att konfigurera, kan det spara tid i slutänden.
Om du planerar att utöka din verksamhet kan den konfigurerbara produkttypen vara ett bättre val för en produkt med flera alternativ.

Exempel: T-shirts som finns i två färger och tre storlekar.
Sex varianter måste skapas som enskilda produkter (var och en med sin egen SKU).
Därefter läggs alla varianter till i en konfigurerbar produkt där kunderna kan välja storlek och färg och sedan lägga dem i kundvagnen.

_Termattribut:_

* _Fält: e-handelsprogram, produkt_
* _Relaterade termer: produkttyper_

### konverteringsgrad

_substantiv_

Andelen besökare som konverteras till köpare.

_Termattribut:_

* _Fält: företag, beställning_

### skalning på kärnnivå

_substantiv_

Skalning på kärnnivå består av tre servicenoder för datalagring, cache och tjänster, som OpenSearch, Elasticsearch, MariaDB och Redis.

_Termattribut:_

* _Fält: cloud_

### kreditnota

_substantiv_

Ett dokument som handlaren utfärdat till en kund för att skriva av ett utestående saldo på grund av överkostnad, rabatt eller retur av varor.
PM:et återställer medel till kundens konto.

_Termattribut:_

* _Fält: företag, beställning_

### kreditnota-kommentar

_substantiv_

Information om varför ett kreditnotsbelopp krediterades kunden.

_Termattribut:_

* _Fält: företag, beställning_

### kreditnotanbjekt

_substantiv_

En fakturerad artikel som en handlare skapar en kreditnota för.

_Termattribut:_

* _Fält: företag, beställning_

### korsförsäljning

_substantiv, adjektiv, verb_

En produkt som visas bredvid kundvagnen.
När en kund navigerar till kundvagnssidan visas dessa produkter som korsförsäljning till de artiklar som redan finns i kundvagnen.
De liknar impulsköp, som tidskrifter och godis i kassaregister.

_Termattribut:_

* _Fält: företag, produkt_
* _Relaterade villkor: merförsäljning_

### CVM

_substantiv_

En förkortning av &quot;Cardholder Verification Method&quot;.
Ett sätt att verifiera kundens identitet genom att bekräfta en 3- eller 4-siffrig kreditkortssäkerhetskod med betalningsprocessorn.

_Termattribut:_

* _Fält: företag, beställning_
* _Synonymer: Verifieringsmetod för kortinnehavare_
* _Relaterade villkor: säkerhetskod_

## D

### databasschema

_substantiv_

Datastrukturen i en databas.
Definierar hur data ordnas och hur datarelationer styrs, inklusive alla begränsningar som tillämpas på data.
En modul kan innehålla fragment av databasschemat om modulen har data som måste lagras i databasen.

_Termattribut:_

* _Fält: programmering_
* _Synonymer: schema_

### beroendeinjektion

_substantiv_

Ett designmönster för programvara som gör att en klass kan ange sina beroenden utan att behöva konstruera dem.
Den här klassen delegerar ansvaret för att mata in beroendet till den anropande klassen.
Används för att göra testningen enklare.
Om du vill definiera beroenden för klasser redigerar du konfigurationsfilen di.xml.

_Termattribut:_

* _Fält: programmering_

### distributionsnyckel

_substantiv_

En distributionsnyckel är den offentliga nyckeln för ditt projekt SSH och ger skrivskyddad eller skrivskyddad (om den är aktiverad) åtkomst till en Git-databas.

Läs mer: [Säkra anslutningar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html?lang=sv-SE)

_Termattribut:_

* _Fält: cloud_

### dubbel anmälan

_substantiv, verb_

En e-postverifieringsprocess som kräver att potentiella prenumeranter slutför ett andra steg som bekräftar att de har för avsikt att prenumerera.

_Termattribut:_

* _Fält: business_

### nedladdningsbar produkt

_substantiv_

En digitalt nedladdningsbar produkt som består av en eller flera filer som har laddats ned, till exempel en e-bok, musik, video, programvara eller en uppdatering.
Du kan erbjuda ett album att sälja och sälja varje låt separat.
En nedladdningsbar produkt kan leverera en elektronisk version av produktkatalogen.

Hämtningsbara filer kan finnas på servern eller tillhandahållas som URL:er till andra server- eller innehållsleveransnätverk.

_Termattribut:_

* _Fält: e-handelsprogram, produkt_
* _Relaterade termer: produkttyper_

### dynamiskt innehåll

_substantiv_

Innehåll som genereras av kod i stället för att läsas från en statisk mall.
När dynamiskt innehåll först återges när en användare besöker en sida kan innehållet ibland cachas och återanvändas utan att ett nytt dynamiskt anrop krävs.

_Termattribut:_

* _Fält: design_
* _Relaterade termer: php_

### URL för dynamiska media

_substantiv_

En URL-adress som genereras dynamiskt av systemet för att referera till en bild eller andra medier.
Adressen länkar direkt till resurser som lagras på en server eller ett leveransnätverk.
Om du vill använda en statisk URL ändrar du konfigurationsinställningen.
Om dynamiska medie-URL:er inkluderas i katalogen när du inaktiverar inställningen, blir varje referens i katalogen en bruten länk.
Länkarna kan återställas genom att aktivera dynamiska medie-URL:er igen.
Användning av dynamiska medie-URL:er kan påverka katalogsökningsprestanda.

Kodformat: media url=&quot;path/to/image.jpg&quot;

_Termattribut:_

* _Fält: programmering_
* _Relaterade villkor: leveransnätverk, url_

## E

### hjälpmedelspaket

_substantiv_

En uppsättning skript och verktyg som är utformade för att hantera och driftsätta Commerce-programmet. Det här paketet förenklar många Adobe Commerce-processer för molninfrastruktur, bland annat distribution till en Docker-miljö, hantering av kroner, verifiering av projektkonfiguration och användning av Adobe-korrigeringsfiler.

Läs mer: [ece-tools-paket](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/package-overview.html?lang=sv-SE)

_Termattribut:_

* _Fält: cli, cloud, deploy_

### enhet

_substantiv_

En unik enhet eller ett unikt objekt i programmeringen.
Innehåller attribut eller parametrar som kan ändras.
Exempel är mellanlagring - där en uppdatering kan ändra enheter som prisregler, produkter eller kategorier - och databasposter - där serviceavtal innehåller datastrukturer som skickas och tas emot.

_Termattribut:_

* _Fält: e-handelsprogramvara_
* _Relaterade termer: attribut, kundvagnsregler, katalogregler_

### entitetsattributvärde

_substantiv_

För databasentiteter, en datamodell som effektivt kodar entiteter.
Lagrar enhets-ID, attributnamn och värde som en trippel, vilket gör att nya entitetsattributnamn kan skapas när som helst.
Vid kodning kan antalet attribut som kan användas för att beskriva enheter skalas mycket, men antalet som gäller för en viss enhet minimeras.
Den här datamodellen är flexibel, men kan vara långsam.

Läs mer: [EAV och extension_attributes](https://developer.adobe.com/commerce/php/development/components/attributes/)

_Termattribut:_

* _Fält: programmering_
* _Synonymer: eav_

### vintergrönt

_substantiv_

Innehåll som har lång hållbarhet eller innehåll som kan återanvändas.

_Termattribut:_

* _Fält: business_

### extension

_substantiv_

Kod som utökar eller anpassar Adobe Commerce beteende.
Du kan även paketera och distribuera ett tillägg på Commerce Marketplace eller ett annat tilläggsdistributionssystem.
Ett Commerce-tillägg kan innehålla moduler, teman och språkpaket.

_Termattribut:_

* _Fält: e-handelsprogramvara_
* _Relaterade termer: komponent, modul, paket_

### extension-attribut

_substantiv_

Utöka funktionaliteten och använd ofta mer komplexa datatyper än anpassade attribut. Attributen visas inte i det grafiska användargränssnittet.

Läs mer: [Lägger till tilläggsattribut till entiteten](https://developer.adobe.com/commerce/php/development/components/add-attributes/)

_Termattribut:_

* _Fält: e-handelsprogramvara_
* _Relaterade termer: attribut, entitetsattributvärde_

## F

### frakt ombord

_substantiv_

I internationell sjöfart innebär denna term att den mottagande parten ansvarar för fraktkostnaderna.
FOB kan baseras på ursprungs- eller destinationsplatsen och anges som antingen fraktsamling eller förbetald frakt.

_Termattribut:_

* _Fält: företag, order, priser_
* _Synonymer: fob_

### frontend

_adjektiv_

I ett klient-server-program finns serverdelen och klientdelen.
klientkomponenten är ett gränssnitt som gör att användare kan ändra eller interagera med den underliggande backend-koden.
Serverdelskoden körs på en server.
En användare kan inte komma åt backend-kod direkt.
Användaren interagerar med butiken, som i sin tur använder kod som körs på Commerce-servern.

Obs! Tidigare har storefront kallats &quot;front-tend&quot; och Admin har kallats &quot;back end&quot;. Den här användningen stöds inte längre.

_Termattribut:_

* _Fält: design, programmering_
* _Synonymer: klientsida_
* _Relaterade termer: backend, storefront, cache front_

### egenskaper för framtend

_substantiv_

Egenskaper som bestämmer hur ett attribut visas och fungerar utifrån kundens situation i din butik.

_Termattribut:_

* _Fält: design, programmering_

### uppfyllelse

_substantiv_

Processen för att hantera kundleveranser.

_Termattribut:_

* _Fält: business_

## G

### presentkort

_substantiv_

Ett förbetalt kort eller presentkort som kan användas för inköp i butiken.
Varje presentkort tilldelas en unik kod som anges i kassan.
Presentkortets värde framgår av presentkortskontots saldo.
Det finns tre typer av presentkort:

* &quot;Fysiska&quot; presentkort kan tillverkas av plast eller kort som levereras till kunden.
* &quot;Virtuella&quot; presentkort skickas via e-post.
* &quot;Kombinerade&quot; presentkort är en kombination av de två som skickas till mottagaren som ett fysiskt kort och som också levereras via e-post.
Presentkort kan konfigureras, inklusive alternativ för produktberättigande och val av öppna eller fasta belopp.

Butiksadministratören kan även lösa in ett presentkort om kunden begär det när ordern skapas i serverdelen.

Presentkort kan också hjälpa till med kampanjer, eftersom butiksadministratörer kan skapa presentkortskonton manuellt i bakänden och skicka presentkortskoderna till det specifika kundsegmentet.
Presentkort kan fungera som ett lojalitetsprogram som riktar sig till de mest aktiva kunderna som gör många köp från webbutiken eller en viss kampanjkampanj under helger.

_Termattribut:_

* _Fält: e-handelsprogramvara_
* _Relaterade termer: produkttyper_

### bruttomarginal

_substantiv_

Skillnaden mellan kostnaden och priset för en produkt.

_Termattribut:_

* _Fält: business_

### grupperad produkt

_substantiv_

En produkttyp med flera liknande fristående produkter grupperade på en enda sida.
Kan erbjudas med variationer av en enskild produkt eller genom att gruppera dem efter årstid eller tema för att skapa en koordinerad uppsättning.
Varje produkt kan köpas separat eller som en del av gruppen.

För en kniv som är tillgänglig i fyra storlekar kan till exempel alla fyra knivar visas på en grupperad produktsida.
Kunderna kan välja vilka storlekar de vill ha och lägga till dem i kundvagnen från den här sidan.

_Termattribut:_

* _Fält: e-handelsprogram, produkt_
* _Relaterade termer: enkel produkt, produkttyper_

## H

### handtag

_substantiv_

I allmänhet är ett handtag ett sätt att referera till ett objekt.
I Adobe Commerce används handtag på många ställen, vanligtvis för att identifiera en sida.
För sidhandtag hämtas handtagets namn från URL:en och används sedan för att hitta och läsa in layoutfilerna för den refererade sidan.
I modulen Kund finns till exempel en layoutfil med namnet&quot;view/frontend/layout/checkout_cart_index.xml&quot;.
Här är &quot;front&quot; områdesnamnet och &quot;checkout_cart_index&quot; är handtagets namn, som båda härleds från URL:en.

_Termattribut:_

* _Fält: programmering_
* _Synonymer: sidreferens_

### vågrät skalförändring

_substantiv_

Vågrät skalförändring (även kallat utskalning) är processen att lägga till ytterligare noder eller datorer i infrastrukturen för att möta den växande efterfrågan.

_Termattribut:_

* _Fält: cloud_

## I

### avlyssning

_substantiv_

Processen att injicera ny kod före, efter eller runt en befintlig offentlig funktion i en PHP-klass.

För att avbryta en funktion implementerar ett plugin-program den extra kod som ska anropas.
Plugin-program är associerade med spärrpunkter av konfigurationsfilen för beroendeinjektion (di.xml).
Om flera plugin-program är definierade för samma funktion definierar beroendeinjektionskonfigurationen i vilken ordning plugin-programmen anropas, vilket gör att flera plugin-program kan användas utan konflikter.

_Termattribut:_

* _Fält: programmering_
* _Relaterade termer: plugin_

## L

### layout

_substantiv_

När du skapar en Commerce-sida är en layout en serie block som är sammansatta i en hierarki och som representerar sidans struktur.

Sidlayoutfiler fokuserar på den högsta nivån i sidstrukturen (sidhuvud, sidfot, huvudinnehållsområde, vänster sidospalt osv.).
Layoutfiler sätter sedan ihop innehåll (block) till olika områden på sidan.

_Termattribut:_

* _Fält: design, e-handelsprogram_
* _Relaterade termer: layoutinstruktioner, block_

### layoutinstruktioner

_substantiv_

Markering i en layoutfil som beskriver ändringar som ska tillämpas på ett strukturerat elementträd med block, behållare och UI-komponenter.
En enda layoutfil kan innehålla flera layoutinstruktioner.
Layoutinstruktionerna kodas i XML i layoutfiler.

_Termattribut:_

* _Fält: design, programmering_
* _Relaterade termer: layout, block, container, ui-komponent_

### layoutuppdatering

_substantiv_

Används för kodfragment som läggs till för att ändra XML-layouten eller för att importera layoutinstruktioner från en annan fil.

_Termattribut:_

* _Fält: design, e-handelsprogram_

### Licensägare

_substantiv_

Licensägaren (även kallad Kontoägare) är den person i en affärsorganisation som hanterar betalningar och andra affärsrelaterade problem för Adobe Commerce på molninfrastrukturskontot.
Den här personen fungerar som kontaktpunkt för Adobe.
När ett företag har köpt en Adobe Commerce-prenumeration på en molninfrastruktur är den initiala projekt- och kodåtkomsten endast tillgänglig för den person som har angetts som licensägare.

_Termattribut:_

* _Fält: business_

## M

### MAGEID

_substantiv_

MAGEID är vanligtvis faktureringskontakten på Adobe Commerce-kontot (och är kanske inte projektägare till Adobe Commerce i molninfrastrukturprojekt).
För åtkomstbehörighet till Adobe Commerce och Adobe Commerce för molninfrastrukturpaket måste du använda åtkomstnycklar som är kopplade till ett MAGEID som har beviljats åtkomst till dessa paket.

Läs mer: [Hämta dina autentiseringsnycklar](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/prerequisites/authentication-keys.html?lang=sv-SE)

_Termattribut:_

* _Fält: e-handelsprogramvara_

### markering

_substantiv_

I marknadsförings- och detaljhandelsledet läggs en procentandel till kostnaden för en artikel för att fastställa detaljhandelspriset.
[Konfigurera markering](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/settings/settings-advanced-custom-options.html?lang=sv-SE), eller markering, för en produkt med anpassningsbara alternativ.

Under utvecklingen är det ett datorspråk som styr bearbetning, presentation och formatering av text.
Taggar för kod är kodfragment som lägger till funktioner eller innehåll på en CMS-sida eller ett-block.

_Termattribut:_

* _Fält: företag, programmering_
* _Synonymer: Markering_

### huvudmiljö

_substantiv_

På Adobe Commerce i molninfrastruktur använder Pro-projekt en aktiv Platform som en tjänst-miljö (PaaS) som kallas master och innehåller en kopia av din produktionsmiljödatabas och webbserver.

_Termattribut:_

* _Fält: cloud_

### handlarkonto

_substantiv_

Ett konto hos en bank eller ett finansinstitut som gör det möjligt att acceptera kreditkortstransaktioner.

_Termattribut:_

* _Fält: business_

### MFTF

_substantiv_

MFTF är ett [Funktionellt testramverk](https://developer.adobe.com/commerce/testing/functional-testing-framework/).
Det utgör ett testramverk för Commerce-utvecklare och programvaruingenjörer, som QA-specialister, PHP-utvecklare och systemintegratörer.
Utvecklare och QA kan skriva tester för att testa användarinteraktioner med webbprogram, verifiera funktioner och automatisera regressionstestning.

_Termattribut:_

* _Fält: e-handelsprogram, programmering_
* _Relaterade termer: cms-block, statiskt block, behållare, layout_

### modul

_substantiv_

Kod som ändrar eller utökar funktioner som tillhandahålls av programmet Magento.
En modul finns i en katalogstruktur som innehåller PHP- och XML-filer (konfiguration, block, styrenheter, hjälpredor, modeller och så vidare) som rör en viss funktion för att leverera en tydlig samling av produktfunktioner.
Syftet med varje modul är att tillhandahålla specifika produktfunktioner genom att implementera nya funktioner eller utöka funktionaliteten för andra moduler.
Varje modul är utformad för att fungera oberoende av varandra, så om en viss modul tas med eller utesluts påverkas inte funktionen i andra moduler.

En modul kan också implementera widgetar, som är sidelement som kan anpassas av företagsanvändare i Admin.

Moduler kan inaktiveras eller tas bort utan att konsistensen i programmet Magento bryts.
Ett undantag: När modulen är beroende av andra moduler, vilket kräver att de beroende modulerna inaktiveras eller tas bort.

_Termattribut:_

* _Fält: e-handelsprogramvara_
* _Relaterade termer: php, xml, block_

## O

### OMS

_substantiv_

OMS är Adobe Order Management System.

>[!IMPORTANT]
>
>Adobe Commerce Order Management (OMS) har nått slutet av livscykeln och stöds inte längre.

OMS är en flexibel och prisvärd lösning för att hantera, sälja och uppfylla lager från valfri försäljningskanal.
OMS ger en smidig kundupplevelse, som ökar försäljningen samtidigt som kostnaderna minskar och kortar time-to-market.

OMS-funktioner:

* Global synlighet och hantering av allt lager
* Möjlighet att leverera till och från var som helst
* Enklare och mer lättillgänglig kundtjänst
* Bättre kundupplevelser och lojalitet

Mer information: [Arkiverad OMS Docs-webbplats](https://commerce-docs.github.io/oms-documentation-archive/)

_Termattribut:_

* _Fält: funktion, e-handelsprogram, orderhantering_
* _Synonymer: orderhantering, MOM, orderhanteringssystem, Magento Order Management_
* _Relaterade termer: orderhantering_

### ursprungsinsvepning

_substantiv_

Insvepning är en säkerhetsfunktion som gör det möjligt för Adobe Commerce på molninfrastrukturen att blockera all trafik som inte är snabb för att förhindra DDoS-attacker genom att gå till molninfrastrukturen (ursprung).

Läs mer: [Insvepning med snabbt ursprung](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/faq/fastly-origin-cloaking-enablement-faq.html?lang=sv-SE)

_Termattribut:_

* _Fält: säkerhet_
* _Relaterade termer: webbprogrammets brandvägg_

## P

### Page Builder

_substantiv_

Page Builder är ett Commerce-tillägg för att skapa innehållsrika sidor genom att dra och släppa färdiga kontroller för att definiera anpassade layouter.
Dessa kontroller kallas även&quot;innehållstyper&quot;.
Merchants kan designa layouter och sidor utan kodningsupplevelse.
Utvecklare kan utöka Page Builder med stöd för tillägg.

Läs mer: [Användarhandbok för Page Builder](https://experienceleague.adobe.com/docs/commerce-admin/page-builder/introduction.html?lang=sv-SE), [DevDocs för Page Builder](https://developer.adobe.com/commerce/frontend-core/page-builder/)

_Termattribut:_

* _Fält: e-handelsprogram, design_
* _Synonymer: Admin, Admin Panel, backend, Administration Interface, Admin UI_
* _Relaterade termer: admin_

### betalningsgateway

_substantiv_

En betalningstjänst är en tredjepartstjänst som smidigt behandlar kreditkortstransaktioner utan att kunden behöver lämna handlarens webbplats.

_Termattribut:_

* _Fält: företag, order, programmering_

## R

### relaterad produkt

_substantiv_

Ett urval produkter som presenteras som ett incitament att köpa ytterligare artiklar.
Om kunden till exempel visar produktsidan för en kamera, kan de relaterade produkterna innehålla andra jämförbara kameror, ett kamerafält och ett stativ.

_Termattribut:_

* _Fält: e-handelsprogram, produkt_

## S

### försäljningsregler

_substantiv_

Inkluderar korgs- och katalogregler, som används för att prissätta en produkt för kampanjer.

_Termattribut:_

* _Fält: e-handelsprogram, produkt_
* _Relaterade termer: kundvagnsregler, katalogregler_

### omfång

_substantiv_

I Adobe Commerce beskriver omfattningen av din butikshierarki som en inställning kan påverka.
Omfattningen kan gälla följande:

* Global - alla webbplatser, butiker och butiker
* Webbplats - den valda webbplatsen och alla butiker och butiksvyer som den innehåller
* Store - den valda butiken och alla butiksvyer under den
* Butiksvy - den valda butiksvyn.

I hierarkin kan inställningar som används på en lägre nivå åsidosätta vissa inställningar på en högre nivå.

_Termattribut:_

* _Fält: e-handelsprogramvara_

### tjänstekontrakt

_substantiv_

En uppsättning PHP-gränssnitt som är definierade för en modul.
Ett serviceavtal innehåller datagränssnitt som bevarar dataintegriteten och servicegränssnitt, som döljer affärslogikdetaljer för tjänstbegärare som t.ex. kontrollanter, webbtjänster och andra moduler.
Webb-API:er kan bindas till serviceavtal via konfigurationsfiler.

_Termattribut:_

* _Fält: programmering_
* _Relaterade termer: php, web api_

### inlösen

_substantiv_

Kvittning sker när den förvärvande banken och emittentens valutareserver och intäkterna är insatta i handelskontot.

_Termattribut:_

* _Fält: business_

### Delad katalog

_substantiv_

En funktion som gör att handlare kan skapa en katalog som kan fungera som hela eller en delmängd av den och sedan tilldela anpassade priser för en eller flera produkter.
Handlare kan sedan tilldela katalogen till ett eller flera företag.

En B2B-handlare har till exempel tre kunder som förhandlat fram specifika priser för butiken för elektronisk distribution.
Med hjälp av funktionen för delad katalog har handlaren

* En huvudkatalog
* En kund-1-katalog (kanske bara tre SKU:er med stora rabatter från huvudkatalogen)
* Kund 2-katalog (kan vara hela katalogen med 10 % rabatt)
* Kund 3-katalog (ett par dussin produkter med rabatter från huvudkatalogen på mellan 5 % och 60 %).

_Termattribut:_

* _Fält: e-handelsprogram, produkt_
* _Relaterade termer: katalog, b2b_

### försändelse

_substantiv_

En försändelse innehåller produkter som ska levereras och genererar ett register över produkterna i en beställning som har skickats.
Mer än en leverans kan kopplas till en enda order.

_Termattribut:_

* _Fält: företag, beställning_

### leveransdokument

_substantiv_

Ett dokument som medföljer en leverans. I dokumentet visas produkterna och deras kvantiteter i leveranspaketet.

_Termattribut:_

* _Fält: företag, beställning_

### fraktfirma

_substantiv_

Ett företag som transporterar paket. Vanliga bärare är UPS, FedEx, DHL och USPS.

_Termattribut:_

* _Fält: företag, beställning_

### kundvagn

_substantiv_

Den uppsättning produkter som en kund har valt att köpa men ännu inte köpt.
Avser också ett område på en e-handelsplats där dessa produkter kan beställas för granskning och utcheckning.

_Termattribut:_

* _Fält: företag, design, produkt, programmering_
* _Synonymer: kundvagn, korg_
* _Relaterade termer: kundvagnsregler_

### enkel produkt

_substantiv_

Den mest grundläggande produkttypen, en fysisk artikel med en enda SKU.
Enkla produkter har olika prissättnings- och indatakontroller som gör det möjligt att sälja varianter av produkten.
Enkla produkter kan användas tillsammans med grupperade, paketerade och konfigurerbara produkter.
En enkel produkt med anpassade alternativ kallas ibland för en sammansatt produkt.

_Termattribut:_

* _Fält: e-handelsprogram, produkt_
* _Relaterade termer: produkttyper_

### SKU

_substantiv_

Förkortning för lagerhållningsenhet.
Ett nummer eller en kod som tilldelats en produkt för att identifiera produkten, alternativen, priset och tillverkaren.

_Termattribut:_

* _Fält: företag, priser, produkt, programmering_
* _Relaterade termer: delad katalog_

### välkomstsida

_substantiv_

En kampanjsida med en produkt eller en annons, som vanligtvis visas före startsidan.

_Termattribut:_

* _Fält: design_

### statiskt block

_substantiv_

En modulär innehållsenhet som en användare i CMS kan montera på en sida för att visa text och bilder eller köra kodfragment.
Statiska block innehåller redigerbart innehåll och kan fungera som landningssidor för produktkategorier.
Du kan lägga till widgetar i statiska block för att få ytterligare funktioner.

_Termattribut:_

* _Fält: e-handelsprogramvara_
* _Relaterade termer: cms-block, block_

### statiskt innehåll

_substantiv_

Användargenererat innehåll (som inte genereras av kod) som inte ändras så ofta.

_Termattribut:_

* _Fält: design_
* _Relaterade termer: dynamiskt innehåll_

### statiska filer

_substantiv_

Samlingen av resurser, t.ex. CSS, teckensnitt, bilder och JavaScript som används av ett tema.

_Termattribut:_

* _Fält: e-handelsprogramvara_

### store

_substantiv_

Commerce omfångsnivå för&quot;store&quot; är den andra nivån i webbplatshierarkin, som ser ut så här: webbplats > butik > butiksvy.
Du kan ordna arkiv i ett eller flera lager. Varje butik har en egen rotkategori och delar alla kataloger och kunddata.

Varje butik kan ha flera butiksvyer, som vanligtvis används för att visa butiken på olika språk och språk.

_Termattribut:_

* _Fält: e-handelsprogram, produkt_
* _Relaterade termer: butiksvy, webbplats_

### butiksvy

_substantiv_

Commerce omfångsnivå i&quot;butiksvy&quot; avser den tredje nivån i hierarkin med webbplatser, butiker och butiksvyer.
I butiksvyer visas butiken vanligtvis på ett annat språk och språk.
Om du vill ändra butiksvyer använder du butiksväljaren i sidhuvudet.

_Termattribut:_

* _Fält: e-handelsprogram, produkt_
* _Relaterade termer: butik, webbplats_

### storefront

_substantiv_

Den webbutik kunderna upplever när de besöker er Commerce webbplats.

_Termattribut:_

* _Fält: e-handelsprogram, produkt_

## T

### momsregel

_substantiv_

En kombination av en produktskatteklass, kundskatteklass och momssats. Den här regeln definierar vilken momsberäkning som används.

_Termattribut:_

* _Fält: business_

### mall

_substantiv_

Kort för HTML-mall eller PHTML-mall.
En PHTML-fil innehåller en blandning av HTML-kod och PHP-kod för att mata in dynamiskt innehåll i HTML.
De flesta block har minst en PHTML-fil (mall) som innehåller det statiska HTML som genereras av blocket.
I mallarna Admin kombinerar e-post och nyhetsbrev text, bilder och variabler med HTML markup för att producera personaliserat innehåll som skickas av systemet.

_Termattribut:_

* _Fält: e-handelsprogramvara_
* _Relaterade termer: block_

### tema

_substantiv_

Innehåller grafik- och utseendeinformation.
Anpassar butikens utseende och känsla.
Adobe Commerce kan skicka teman i (Composer)-paket.
Men du kan placera teman under app/design, som inte levereras i ett paket.
Paket är den enhet som används för att ladda ned Composer, och - via Commerce Marketplace - Commerce-användare kan ladda ned CE eller EE som en serie paket, där paket innehåller moduler, teman eller språkpaket.

_Termattribut:_

* _Fält: e-handelsprogramvara_

## U

### UI-komponent

_substantiv_

En tagg som är utformad för Adobe Commerce för enklare och flexiblare återgivning av användargränssnitt.
Målen för UI-komponentsystemet är följande:

* Förenkla XML-filer för layouthantering
* Flytta element i användargränssnittet för administratörer från HTML+JavaScript till ett anpassat JavaScript-widgetsystem
* Skapa mer komplexa gränssnittskomponenter av mindre komponenter
* Förrenderingsdata för UI-komponenter som JSON, som är nära knutna till backend-dataobjekt
* Uppdatera komponentdata med AJAX
* Vi presenterar en ny DSL för att skapa ovanstående objekt

Läs mer: [Guiden för gränssnittskomponenter](https://developer.adobe.com/commerce/frontend-core/ui-components/), [Page Builder](https://experienceleague.adobe.com/docs/commerce-admin/page-builder/introduction.html?lang=sv-SE)

_Termattribut:_

* _Fält: programmering_
* _Relaterade termer: JavaScript, layout, komponent, sidbyggare_

### UPPGRADERING

_substantiv_

[PWA Studio](https://github.com/magento/pwa-studio) använder [UPWARD](https://developer.adobe.com/commerce/pwa-studio/guides/packages/upward/) under utvecklingen.
UPWARD är en akronym för svarsdefinitionen i Unified Progressive Web App.
En UPWARD-definitionsfil beskriver hur en webbserver levererar och stöder Progressive Web Application.

UPWARD-definitionsfiler innehåller information om serverfunktioner med plattformsoberoende, deklarativt språk.
Detta gör att Progressive Web Application kan köras ovanpå en UPWARD-kompatibel server på vilket språk som helst i en teknikerstack, eftersom programmet bara bryr sig om HTTP-slutpunktsbeteendet från UPWARD-servern.

En UPWARD-server använder en definitionsfil för att fastställa lämplig process eller tjänst för en begäran från ett programskal.
Det beskriver hur servern ska hantera en begäran och bygga svaret på den.

Ett PWA-projekt kan innehålla en UPWARD-definitionsfil för att ange tjänstberoenden.

_Termattribut:_

* _Fält: design, e-handelsprogram, programmering_
* _Synonymer: PWA Studio, svarsdefinition för Unified Progressive Web App_
* _Relaterade termer: pwa_

## V

### Leverantörspaketerat tillägg

_substantiv_

Leverantörstillverkad kod som utökar eller anpassar Commerce beteende och fungerar som ett tillägg från tredje part betraktas som ett VBE (Leverantör Bundled Extension).
VBE-programmen testas grundligt och ingår i alla versioner av Adobe Commerce som stöds.
Ett VBE kan innehålla moduler, teman och språkpaket.

Mer information finns i avsnittet [Leverantörspaket ](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/modules/upgrade.html?lang=sv-SE).

_Termattribut:_

* _Fält: e-handelstillägg, leverantörspaket, tillägg, VBE_
* _Synonymer: tillägg, VBE_
* _Relaterade villkor: tillägg, paketerat tillägg_

### lodrät skalförändring

_substantiv_

Vertikal skalning (uppskalning) avser att öka processorkraften för en enskild server eller kluster genom att lägga till disk- eller nätverks-I/O, processorer eller RAM.

_Termattribut:_

* _Fält: miljö_

### virtuell produkt

_substantiv_

Representerar en icke-fysisk produkt som kan säljas, till exempel ett medlemskap, en tjänst, en garanti eller en prenumeration.
Virtuella produkter kan säljas individuellt eller inkluderas som en del av följande produkttyper: grupperad produkt och paketprodukt.
Kräver inte frakt eller lager.

Processen att skapa en virtuell produkt och en enkel produkt är nästan densamma.
Men eftersom en virtuell produkt inte levereras finns det inget viktfält eller alternativ att inkludera ett presentkort.

_Termattribut:_

* _Fält: e-handelsprogram, produkt_
* _Relaterade termer: produkttyper_

### virtuell typ

_substantiv_

Virtuella typer är ett sätt att infoga olika beroenden i befintliga PHP-klasser utan att påverka andra klasser och utan att behöva skapa en klassfil.
Virtuella typer kan bara refereras av argumentåsidosättningar i ett `<type>`-element i di.xml-filer, aldrig i källkoden.
De kan inte utökas och kan inte vara referenser som beroenden i en klasskonstruktor.

_Termattribut:_

* _Fält: programmering_
* _Relaterade termer: php_

## B

### webbplats

_substantiv_

I Adobe Commerce är det den högsta nivån i webbplatshierarkin, ovanför butiken och butiksvyn.
Du kan ha flera webbplatser, och varje webbplats kan ha olika domännamn.
Webbplatser kan konfigureras för att dela kunddata eller för att inte dela data.

_Termattribut:_

* _Fält: e-handelsprogramvara, design, produkt_
* _Relaterade termer: butik, butiksvy_

### widget

_substantiv_

En [widget](https://experienceleague.adobe.com/docs/commerce-admin/content-design/elements/widgets/widgets.html?lang=sv-SE) är ett förberett kodfragment som kan användas för att placera block, länkar och dynamiskt innehåll på specifika platser på butikssidor.
Ni kan använda widgetar för att skapa landningssidor för marknadsföringskampanjer, visa kampanjinnehåll på specifika platser i hela butiken.
Du kan också använda widgetar för att lägga till interaktiva element och åtgärdsblock för externa granskningssystem, videochatt, röstformulär och prenumerationsformulär, eller för att tillhandahålla navigeringselement för taggmoln och bildreglage.

_Termattribut:_

* _Fält: företag, e-handelsprogram, design_
* _Relaterade termer: block_
