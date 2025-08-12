---
source-git-commit: bfad68a46b9b1a79a702f04efd39129decda1a1c
workflow-type: tm+mt
source-wordcount: '4413'
ht-degree: 0%

---
# Adobe Commerce åtgärdade problem (v2.4.9-alpha2)

## Åtgärdade problem i v2.4.9-alpha2

Vi har åtgärdat 118 problem i Adobe Commerce 2.4.9-alpha2-kärnkoden. En deluppsättning av de åtgärdade problemen som ingår i den här versionen beskrivs nedan.

### API:er

#### Specialpris till datum valideras felaktigt för applySpecialPrice

Systemet fungerar som det ska när det gäller specialpriset och produktens specialpris upphör att gälla det datum som anges av administratören eller tredjepartssystemet av REST API

_AC-13130 - [GitHub-problem](https://github.com/magento/magento2/issues/39169) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/39690)_

#### Felformaterad begärandetext eller felaktiga parametrar orsakar &quot;Internt serverfel&quot;

_AC-746 - [GitHub-problem](https://github.com/magento/magento2/issues/32784) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/f1adb44e)_

#### Ordningen &quot;base_row_total&quot; och &quot;row_total&quot; visar priset för en artikel i REST API-svar

REST api-svar för orderdetaljer innehåller nu korrekta värden för attributen &quot;base_row_total&quot; och &quot;row_total&quot; om flera objekt sorterades

_ACP2E-3874 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/4ca73607)_

### API:er, ordning

#### [CLOUD] Orderinformationsproblem med radsummeutseende för order 000075568

Korrigerar problemet där värdet row_total_incl_tax i order-API-svaret returnerades som ett nästan noll restvärde i stället för 0,00 när ett objekt helt rabatterades.

_ACP2E-3950 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/462ede94)_

### Konto

#### Problem vid uppdatering av kundens e-post på Admin Panel med ö och swiss-domän

_AC-13409 - [GitHub-problem](https://github.com/magento/magento2/issues/39394) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/d3ea191d)_

#### Växeln för prenumerationsaktiverade nyhetsbrev fungerar inte per webbplats/butik

Systemet hanterar prenumerationer med nyhetsbrev korrekt när vi har flera webbplatser/butiksgranskningar när det inaktiverats på global nivå

_AC-14283 - [GitHub-problem](https://github.com/magento/magento2/issues/39751) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/39752)_

#### Föråldrade ett kundsegmentvillkor för&quot;Produkten visades&quot;

_AC-14542_

#### [Utgåva] Borttagen e-postexponering

Systemet visar nu Visa ett felmeddelande som anger ett felaktigt e-postmeddelande om den angivna e-postadressen inte krävs för att bekräfta kontot, oavsett om kunden finns eller inte.

_AC-14561 - [GitHub-problem](https://github.com/magento/magento2/issues/39574) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/39570)_

### Administratörsgränssnitt

#### FPT-värdet i kundvagnssidan och produktsidan är olika för samma konfigurationer för enkla produkter

_AC-13066 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/8953613e)_

#### Det går inte att spara attributalternativen Multiselect/select när modulen Färgrutor är inaktiverad

_AC-13071 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/8953613e)_

#### FPT-värdet i kundvagnssidan och produktsidan är olika för samma konfigurationer för en dynamisk produkt

_AC-13075 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/8953613e)_

#### Hovringsfärgen används inte på statiska stödraster i administratören

Hovringsfärger används nu som förväntat på raderna i det statiska administratörsstödrastret.[GitHub-35358](https://github.com/magento/magento2/issues/35358)

_AC-2916 - [GitHub-problem](https://github.com/magento/magento2/issues/35358) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/35384)_

#### Begränsade administratörsanvändare kan inte massuppdatera produktstatus

Den anpassade administratören kan massuppdatera produktstatus som en egenskap på webbplatsnivå. Statusen uppdateras endast på de webbplatser som den begränsade administratören har tillgång till.

_ACP2E-3772_

#### [Mellanlagring2] Lagrade kort visas inte på administratörspanelen

Korrigerar problemet där betalningsalternativet &quot;Lagrat kort&quot; inte längre fanns i ersättningsformuläret för backend-order efter en uppgradering.

_ACP2E-3830 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/7accebfa)_

### B2B

#### Verifiering av företagsfält misslyckas för gästutcheckning

_AC-14987 - [GitHub-problem](https://github.com/magento/magento2/issues/40011) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/f1adb44e)_

### Paket

#### Uteslut JS-filer för redigering i toppklass från utdata i olika teman

_AC-15128 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/43648891) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/2bc584af)_

### Kort och utcheckning

#### Valideringar av grupperat produktantal saknas

Systemet fungerar nu som det ska och ett valideringsfel visas när vi försöker lägga till negativ kvantitet och maximal kvantitet

_AC-13524 - [GitHub-problem](https://github.com/magento/magento2/issues/39479) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/39480)_

#### Gästprefixet har inte sparats i offertadressen 2.4.8

_AC-14705 - [GitHub-problem](https://github.com/magento/magento2/issues/39915) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/f1adb44e)_

#### [Utgåva] Ange pris för offertobjekt i stället för baspris

Systemet hanterar offertobjektets pris inställt på base_price i stället för priset om du har flera valutor på en webbplats i klientdelen

_AC-9985 - [GitHub-problem](https://github.com/magento/magento2/issues/38094) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/36878)_

#### [Molnet] Senaste beställningar visas inte i den andra butiksvyn om beställningarna skapas i en butiksvy

Ett problem har korrigerats där sidan Mitt konto inte visade de senaste beställningarna från andra butiksvyer i samma Store. Logiken för orderhämtning har uppdaterats för att säkerställa att ordern visas på ett konsekvent sätt i alla butiksvyer, i enlighet med beteendet på sidan&quot;Mina beställningar&quot;.

_ACP2E-3807 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/a20a6ff2)_

#### Kvantitet som visas som  0 i kundvagnsdelen för administratör när BUNDLE-produkter läggs till  

I avsnittet Kundvagn i Kundaktiviteter visas nu rätt kvantitet. Tidigare visades kvantiteten som 0.

_ACP2E-3872 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/3ad96f6a)_

### Kort och utcheckning, GraphQL

#### Fel vid mappning av meddelande till felkod vid beställning via GraphQL

GraphQL anropar för att lägga en order på en obefintlig eller inaktiv varukorg som nu returnerar felkoderna CART_NOT_ACTIVE eller CART_NOT_FOUND korrekt i alla butiksvyer, vilket åtgärdar ett problem där översatta felmeddelanden tidigare resulterade i en UNDEFINED-kod.

_ACP2E-3942 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/7accebfa)_

### Kort och utcheckning, GraphQL, Inventory / MSI

#### is_available-attributet i CartItemInterface returnerar false även när det säljbara lagret är högt

Attributet is_available returnerar true när det säljbara lagret är högt. Tidigare returneras alltid false.

_ACP2E-3885 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/3ad96f6a)_

### Katalog

#### Scope bug in Catalog URL resource (_getCategories)

Den här PR-versionen lägger till en reserv i standardomfånget om inget värde har definierats i butiksomfånget i kategorins URL-resurs.

_AC-11011 - [GitHub-problem](https://github.com/magento/magento2/issues/38393) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/38394)_

#### [Utgåva] Kontrollera om OpenGraph kan visa pris

Systemet fungerar bra när vi använder ett plugin-program som döljer priset och med det här ändringspriset visas inte i OG-taggen.

_AC-11635 - [GitHub-problem](https://github.com/magento/magento2/issues/38512) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/38510)_

#### [Fel] REST API: Uppdatera specialpriser anger inte värden för alla butiksvyer

_AC-13671 - [GitHub-problem](https://github.com/magento/magento2/issues/39521) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/7bdafaa2)_

#### [\Magento\ConfigurableProduct\Model\Product\Type\Configurable] PHP-fel okänt

Den här PR Ändra ett loopvariabelnamn så att &quot;_cache_instance_product_ids&quot;-data på den angivna produkten läggs till korrekt för efterföljande anrop.

_AC-14159 - [GitHub-problem](https://github.com/magento/magento2/issues/39641) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/39642)_

#### [Mainline] [CLOUD] Bildstorleksändring förbrukar mer än 400 GB diskutrymme

Efter korrigeringen genererar inte kommandot `catalog:images:resize` som används med flaggan —skip_hidden_images bildcacher för webbplatser där bilder saknas.

_ACP2E-3869 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/9ad7d277)_

#### Angivet land-ID finns inte - Irland (IE)

Efter korrigeringen kan Irland-postkoder användas för att söka efter hämtningsplatser.

_ACP2E-3932 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/4ca73607) - [GitHub-kodbidrag](https://github.com/magento/inventory/commit/d2f1d6c6)_

### Katalog, prestanda

#### Kategorier i administratören läses in mycket långsamt

Kategoriinläsningsprestanda har förbättrats avsevärt. Tidigare tog det så lång tid att läsa in kategorin som orsakade ett timeout-problem.

_ACP2E-3891 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/4ca73607)_

### Katalog, pris

#### Felaktig rabatt på katalogprisregel för underordnad produkt

Korrigerar problemet där katalogprisregeln för variationen åsidosätts av den överordnade konfigurerbara produkten, om båda reglerna har samma prioritet.

_ACP2E-3693 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/a20a6ff2)_

### Katalog, söka

#### RestAPI-begäran &#39;/rest/default/V1/categories?searchCriteria%5Bpage_size%5D=1&#39; misslyckas med timeout-fel

_AC-13358 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/7bdafaa2)_

### Innehåll

#### Efter uppgradering till magento 2.4.7 kan p2 inte se nyligen överförda filer i mediegalleriet

_AC-13262 - [GitHub-problem](https://github.com/magento/magento2/issues/39275)_

#### Om du tar bort en galleribild helt och hållet från omfånget behåller rollerna/typerna angivna (bas/liten/miniatyrbild) och när du har lagt till&quot;gamla&quot; roller/typer igen visas

Systemet fungerar som förväntat i lagringsomfånget. Bilderna ärver rollerna/typerna för den nya tillagda bilden enligt standardomfånget

_AC-13556 - [GitHub-problem](https://github.com/magento/magento2/issues/39481) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/39680)_

#### [Små fel] Filter för Admin Panel `listing component` kan inte påverkas när fältvärdet innehåller `\`

Systemet fungerar bra när vi filtrerar sidrubriken med snedstreck (t.ex. Magento\Store)

_AC-13661 - [GitHub-problem](https://github.com/magento/magento2/issues/39513) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/39535)_

#### Loggflödet &quot;CMS-sidan med ID &quot;0&quot; finns inte&quot;

Systemet fungerar som väntat efter att admin-användaren har skapats och när vi skapar ett nytt sidsystem.log visas inga felmeddelanden

_AC-14254 - [GitHub-problem](https://github.com/magento/magento2/issues/39743) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/39746)_

#### Kataloglänkswidgetar använder felaktig URL

Systemet hanterar nu widgetar korrekt efter att länken för katalogprodukt och katalogkategori har lagts till och rätt URL:er i HTML-källan visas också

_AC-14437 - [GitHub-problem](https://github.com/magento/magento2/issues/39464) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/39710)_

#### Page Builders produktkomponent fungerar inte om användaren inte har Widget-behörighet

Före korrigeringen genererades ett allmänt fel på sidan när en widget utan behörigheter öppnades och en&quot;inläsande&quot; GIF visades. Efter korrigeringen visas nu ett modalt fönster med&quot;Du måste ha behörighet att visa det här innehållet&quot;. meddelande.

_ACP2E-3664 - [GitHub-kodbidrag](https://github.com/magento/magento2-page-builder/commit/bd9181b6)_

#### Page Builder Product Widget-ordningen används inte i GraphQL

Korrigerar problemet där GraphQL&quot;rutt&quot;-frågesvaret inte returnerade produkter i rätt sorteringsordning i en Page Builder-innehållstyp.

_ACP2E-3898 - [GitHub-kodbidrag](https://github.com/magento/magento2-page-builder/commit/bd9181b6)_

#### Problem med visning av priser i icke-engelska butiker på grund av ICU-biblioteksversionen

Efter korrigeringen visas produktpriset korrekt på hebreiska (Israel).

_ACP2E-3938 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/7accebfa)_

#### Uppdaterar rensad designkonfiguration för butikskod

Korrigerar problemet där uppdateringen av lagringsvyns kod rensade designkonfigurationsinställningarna på grund av att konfigurationscachen inte uppdaterades korrekt.

_ACP2E-3941 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/462ede94)_

### Ramverk

#### Fel vid körning av kommandokonfiguration :upgrade med anpassad DB-utlösare

_AC-11487 - [GitHub-problem](https://github.com/magento/magento2/issues/38481)_

#### Det går inte att utöka entitetsformuläret Website/Group/Store med formulärelement med flera värden för tilläggsattribut

Denna PR tillåter formulärelement med flera värden att skicka data till webbplatsen/gruppen/butiksformuläret.

_AC-11657 - [GitHub-problem](https://github.com/magento/magento2/issues/24070) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/24094)_

#### [Problem] Ta bort användning av scopematchare

Den här PR:en åtgärdar URL-inställningarna för administratörer globalt i stället för det aktuella arkivet

_AC-11736 - [GitHub-problem](https://github.com/magento/magento2/issues/38566) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/38554)_

#### Magento Version-exponering via Setup-väg med Nginx-standardkonfiguration

Systemet fungerar nu som förväntat och visar inte den exakta versionen av Magento som webbplatsen körs i

_AC-13205 - [GitHub-problem](https://github.com/magento/magento2/issues/39227) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/39228)_

#### [Utfärdande] av refactoringcitatadress validerar metod

Denna PR innehåller läsbarhetsförbättringar av metoden doValidate.

_AC-13214 - [GitHub-problem](https://github.com/magento/magento2/issues/38230) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/38219)_

#### Magento option —magento-init-params never used when running cli?

_AC-13231 - [GitHub-problem](https://github.com/magento/magento2/issues/39248) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/132b9e68)_

#### fel typdeklaration för getItemsByColumnValue

Systemet definierar nu indataparametern $value korrekt som en primitiv typ, inte en array, i funktionen getItemsByColumnValue, vilket säkerställer att funktionen returnerar den förväntade mängden. Tidigare, om en array med ett enda värde användes som indataparameter, skulle funktionen returnera null och IDE:er skulle markera det som ett fel.

_AC-13240 - [GitHub-problem](https://github.com/magento/magento2/issues/33070) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/33120)_

#### Cachenycklar som är associerade med FPC i Magento 2.4.7-multilagringsimplementationer

_AC-13719 - [GitHub-problem](https://github.com/magento/magento2/issues/39456) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/ae6f305b)_

#### Magento Rest API exponerar PII

_AC-13904 - [GitHub-problem](https://github.com/magento/magento2/issues/39336)_

#### Partiell indexering fungerar inte längre för kunder med enormt många uppdateringar

_AC-14424 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/7bdafaa2)_

#### Undersök om &quot;use strict&quot; inte finns i moduler

_AC-14517 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/77c589a6)_

#### Efter nedladdning av fraktsetikett kan vi se en del fraktbelopp som inte matchar frakt- och hanteringspriset.

_AC-14560_

#### MView-funktionen ignorerar fel vid utlösarkörning

_AC-14567 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/ae6f305b)_

#### [Problem] Undvik många onödiga undantag vid inläsning av XML-sammanfogning av layout

Denna PR introducerar en ny funktion (för B/C-kompilering skriver vi inte över den skyddade _loadXmlString) för att läsa in och inte generera ett undantag

_AC-14580 - [GitHub-problem](https://github.com/magento/magento2/issues/39877) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/37570)_

#### [Problem] Använd egenskapshöjning för konstruktor i moduldiagrammet Ql för vaultdiagram

Denna PR ersätter konstruktoregenskaper med egenskapshöjning i modulen VaultGraphQl

_AC-14616 - [GitHub-problem](https://github.com/magento/magento2/issues/39900) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/36996)_

#### [Problem] Kodredundans har tagits bort för modulens klientlayouter.

Den här PR-funktionen tar bort kodredundans för temalayouter för frontend-layouterna Magento_Msrp, Magento_LoginAsCustomerAssistance, Magento_Newsletter &amp; Magento_Sitemap.

_AC-14625 - [GitHub-problem](https://github.com/magento/magento2/issues/30673) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/30644)_

#### [Problem] Ta bort kod som är relaterad till Microsoft IIS

Den här PR-åtgärden rensar koden som är relaterad till Microsoft IIS enligt dokumentationen för Magento-systemkrav som anger att Microsoft Windows OS inte stöds

_AC-14702 - [GitHub-problem](https://github.com/magento/magento2/issues/39910) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/39894)_

#### Syntaxfel för Förstoringsglaset.js

Funktionen för förstoringsglaset bör fortsätta att fungera som den fungerade tidigare och förstoringsalternativ bör inte vara tillgängliga i det globala omfånget

_AC-14722 - [GitHub-problem](https://github.com/magento/magento2/issues/36200) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/39321)_

#### Bakgrundsvisningsläge i CLI-kommandot `setup:db:status`

_AC-14807 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/7bdafaa2)_

#### SMTP-e-post som skickas med tls och 2.4.8

_AC-14883 - [GitHub-problem](https://github.com/magento/magento2/issues/39947) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/3717e6cb) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/8b453942) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/d3ea191d)_

#### [Problem] Åtgärda samtidighetsproblem vid distribuering av statiskt innehåll

Denna PR åtgärdar ett fel där flera samtidiga processer snurrar upp för att hantera samma temapaket, beroende på hur teman definieras med sina överordnade.

_AC-14944 - [GitHub-problem](https://github.com/magento/magento2/issues/39990) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/39954)_

#### [Problem] Ta bort tidigare kompatibilitetskod för PHP-versioner &lt; 8.1

Den här pull-begäran tar bort kod som är avsedd att köras på PHP &lt;8.1.
Borttagen kontrollerar också om PHP_VERSION_ID-kontakt är tillgänglig eftersom den är tillgänglig i alla PHP-versioner

_AC-14971 - [GitHub-problem](https://github.com/magento/magento2/issues/39891) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/39882)_

#### FPC fungerar inte vid inloggning

_AC-14999 - [GitHub-problem](https://github.com/magento/magento2/issues/40007) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/)_

#### [Problem] förbättrar felhanteringen i SchemaBuilder

Denna PR förbättrar felmeddelandehanteringen i databasschemat. Det hjälper oss att identifiera problem utan omfattande felsökning.

_AC-15020 - [GitHub-problem](https://github.com/magento/magento2/issues/39816) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/39799)_

#### Integrationstestfel i SYNC PR för 2.4.9-alpha2-develop på grund av CliStateTest-modifiering

_AC-15136 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/2d0f8066)_

#### PHP8.1 type bugfix

De associerade produkterna initieras nu till en tom array i stället för till false när det strikta behandlingsläget inte är aktivt eller när produktinformation är tillgänglig. Denna förändring säkerställer att den efterföljande logikhanteringen av tillhörande produkter fungerar på ett konsekvent sätt, vilket förbättrar stabiliteten och förutsägbarheten i produktberedningsprocessen.

_AC-6017 - [GitHub-problem](https://github.com/magento/magento2/issues/35808) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/35842)_

#### [Problem] Ta bort ej tillåten `@author` tagg från ramverket (del 3)

Systemet följer nu kodstandarderna genom att ta bort den förbjudna taggen `@author` från vissa moduler, vilket förbättrar den övergripande kodkvaliteten. Tidigare var förekomsten av den här taggen i vissa moduler ett brott mot de fastställda kodstandarderna.

_AC-8343 - [GitHub-problem](https://github.com/magento/magento2/issues/37270) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/37020)_

#### [Utgåva] Använda egenskapshöjning för konstruktor i modulen Skicka QL-diagram för vän

Systemet utnyttjar nu befordring av konstruktoregenskaper i GraphQL-modulen&quot;skicka vän&quot;, vilket förbättrar kodläsbarheten och minskar komplexiteten. Tidigare använde modulen egenskaper som upptog flera rader, vilket gjorde koden mer komplex och mindre läsbar.

_AC-8346 - [GitHub-problem](https://github.com/magento/magento2/issues/37235) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/37197)_

#### [Problem] Ta bort ej tillåten `@author`-tagg från `Magento_Downloadable`

Systemet följer nu kodstandarderna genom att ta bort den förbjudna taggen `@author` från vissa moduler, vilket förbättrar den övergripande kodkvaliteten. Tidigare var förekomsten av den här taggen i vissa moduler ett brott mot de fastställda kodstandarderna.

_AC-8355 - [GitHub-problem](https://github.com/magento/magento2/issues/37251) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/37001)_

#### [Utgåva] Ta bort förbjuden `@author` -tagg

Systemet följer nu kodstandarderna genom att ta bort den förbjudna taggen `@author` från vissa moduler, vilket förbättrar kodkvaliteten och konsekvensen. Tidigare var förekomsten av den här taggen i vissa moduler ett brott mot de fastställda kodstandarderna.

_AC-8358 - [GitHub-problem](https://github.com/magento/magento2/issues/37264) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/37014)_

#### [Utgåva] Ta bort förbjuden `@author` -tagg

Systemet följer nu kodstandarderna genom att ta bort den förbjudna taggen `@author` från vissa moduler, vilket förbättrar den övergripande kodkvaliteten. Tidigare var förekomsten av den här taggen i vissa moduler ett brott mot de fastställda kodstandarderna.

_AC-8360 - [GitHub-problem](https://github.com/magento/magento2/issues/37261) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/37011)_

#### [Utgåva] Ta bort förbjuden `@author` -tagg

Systemet följer nu kodstandarderna genom att ta bort den förbjudna taggen `@author` från vissa moduler, vilket ger en renare och mer standardiserad kod. Tidigare var förekomsten av den här taggen i vissa moduler ett brott mot de fastställda kodstandarderna.

_AC-8361 - [GitHub-problem](https://github.com/magento/magento2/issues/37260) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/37010)_

#### [Utgåva] Ta bort förbjuden `@author` -tagg

Systemet följer nu kodstandarderna genom att ta bort den förbjudna taggen `@author` från vissa moduler, vilket förbättrar den övergripande kodkvaliteten. Tidigare var förekomsten av den här taggen i vissa moduler ett brott mot de fastställda kodstandarderna.

_AC-8363 - [GitHub-problem](https://github.com/magento/magento2/issues/37258) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/37008)_

#### [Utgåva] Ta bort förbjuden `@author` -tagg

Systemet följer nu kodstandarderna genom att ta bort den förbjudna taggen `@author` från vissa moduler, vilket förbättrar den övergripande kodkvaliteten. Tidigare var förekomsten av den här taggen i vissa moduler ett brott mot de fastställda kodstandarderna.

_AC-8375 - [GitHub-problem](https://github.com/magento/magento2/issues/37257) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/37007)_

#### [Utgåva] Ta bort förbjuden `@author` -tagg

Systemet följer nu kodstandarderna genom att ta bort den förbjudna taggen `@author` från vissa moduler, vilket förbättrar den övergripande kodkvaliteten. Tidigare var förekomsten av den här taggen i vissa moduler ett brott mot de fastställda kodstandarderna.

_AC-8376 - [GitHub-problem](https://github.com/magento/magento2/issues/37256) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/37006)_

#### [Utgåva] Ta bort förbjuden `@author` -tagg

Systemet följer nu kodstandarderna genom att ta bort den förbjudna taggen `@author` från vissa moduler, vilket förbättrar den övergripande kodkvaliteten. Tidigare var förekomsten av den här taggen i vissa moduler ett brott mot de fastställda kodstandarderna.

_AC-8400 - [GitHub-problem](https://github.com/magento/magento2/issues/37254) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/37004)_

#### [Utgåva] Ta bort förbjuden `@author` -tagg

Systemet följer nu kodstandarderna genom att ta bort den förbjudna taggen `@author` från vissa moduler, vilket förbättrar den övergripande kodkvaliteten. Tidigare var förekomsten av den här taggen i vissa moduler ett brott mot de fastställda kodstandarderna.

_AC-8401 - [GitHub-problem](https://github.com/magento/magento2/issues/37255) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/37005)_

#### [Problem] Förbättra utökningsbarheten för generering av tjänst-URL

Systemet gör det nu möjligt att anpassa funktionen för att generera tjänstens URL via plugin-program, vilket ger ett mer underhållningsbart tillvägagångssätt vid ändringar. Tidigare gjordes anpassningar av den här funktionen via inställningar som kanske inte var lika effektiva eller underhållbara.

_AC-8813 - [GitHub-problem](https://github.com/magento/magento2/issues/37404) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/37403)_

#### Problem med uppgradering 2.4.7-p5 på grund av ny validering

Korrigerade ett problem i klassen SchemaBuilder där en odefinierad matrisnyckel, kolumn, orsakade en krasch när scheman skapades eller uppdaterades. Detta inträffade när tabelldata som inte innehöll någon kolumnnyckel bearbetades.

_ACP2E-3871 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/9ad7d277)_

#### PHP8.4-undertryckningsfel: E_USER_ERROR efter uppgradering till Adobe Commerce 2.4.8

Kundorienterade scenarier påverkas inte av korrigeringen.

_ACP2E-3963 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/7accebfa)_

### Framework, Search

#### OpenSearch 2.19.1 illegal_argument_exception i kategorier med ett pris

OpenSearch genererar inte längre ett illegal_argument_exception för de kategorier som innehåller alla produkter med samma pris. Tidigare fanns det ett undantag, [from]-parametern, som inte kan vara negativ.

_ACP2E-3896 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/3ad96f6a)_

### GraphQL

#### customerOrders-graf returnerar fel när produkten togs bort

Kravet på diagram customerOrders genererar inte längre något fel även om produkten i ordern har tagits bort. Tidigare uppstod felet &quot;Internt serverfel&quot;.

_ACP2E-3936_

#### Önsklisteobjekt delas inte mellan butiksvyer på en webbplats i en GraphQL-begäran

Före korrigeringen filtrerades önskelisteobjekten efter arkiv-ID. Efter korrigeringen filtreras önskelisteobjekten efter webbplats.

_ACP2E-3987 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/2a252ae6)_

### GraphQL, produkt

#### Produktgraf saknar media_type i MediaGalleryInterface

MediaGallery GraphQL-begäran innehåller nu fältet &quot;types&quot; (Typer) för produktbildtyper. Tidigare fanns inte det här typfältet i GraphQL-begäran för MediaGallery.

_ACP2E-3880 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/3ad96f6a)_

### Lager/MSI

#### Ingen butik är tillgänglig efter omdirigering till startsidan och kassan

Tidigare valda butiker väljs nu i förväg i leveranserna&quot;Välj i butik&quot; om kunden navigerar till betalningssidan, sedan återgår till startsidan och slutligen går tillbaka till utcheckningssidan. Tidigare rensades den valda butiken i&quot;Plocka i butik&quot; efter att du upprepade gånger gått tillbaka till utcheckningssidan.

_ACP2E-3793 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/a20a6ff2) - [GitHub-kodbidrag](https://github.com/magento/inventory/commit/62c0d79b)_

### Beställning

#### AbstractAddress setData(&#39;custom_attributes&#39;, AttributeValue[]) bryter anpassade attribut

_AC-10568 - [GitHub-problem](https://github.com/magento/magento2/issues/31644)_

#### v2.4.7-p1 Magento reorder -1 ordernummer

Systemet fungerar som förväntat och efter omsortering från serverdelen blir ordernumret unikt med 8 siffror

_AC-12854 - [GitHub-problem](https://github.com/magento/magento2/issues/39089) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/39399)_

#### Förlora filöverföring för anpassade produktalternativ vid utcheckning med betalningsmetoden Adobe kreditkort

_AC-14306 - [GitHub-problem](https://github.com/magento/magento2/issues/39647)_

#### Beställningsstatus låst vid bearbetning

Före korrigeringen växlade orderstatusen inte automatiskt till&quot;fullständig&quot; efter faktura och leverans när en paketprodukt med alternativet&quot;Leverera tillsammans&quot; aktiverades. Efter korrigeringen ändras orderstatusen automatiskt till&quot;fullständig&quot; efter att ordern har fakturerats och skickats.

_ACP2E-3947 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/2a252ae6)_

#### [Cloud]Magento OOTB-kod - Problem med konfiguration av e-postmall

Före korrigeringen, när asynkron e-postutsändning användes, var e-postutskick inkonsekvent med butiksbeställningen. Efter korrigeringen levereras rätt e-postorder för leverans i butik.

_ACP2E-3998 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/462ede94)_

### Andra utvecklingsverktyg

#### [Fel typtips] för den skyddade medlemmen $_urlHelper

Systemet åtgärdar nu fel typtips med rätt typ, som också används i konstruktorn

_AC-10716 - [GitHub-problem](https://github.com/magento/magento2/issues/32503) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/32496)_

### Prestanda

#### [Utgåva] Uppdatera Store.php

Denna PR förbättrar prestanda genom att hoppa över den aktuella lagringsupplösningen.

_AC-14791 - [GitHub-problem](https://github.com/magento/magento2/issues/39949) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/38717)_

### Priser

#### Priset är alltid 0 för produktartiklar utan dynamiskt pris i order rest-API

_AC-11925 - [GitHub-problem](https://github.com/magento/magento2/issues/38687) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/7da46f52)_

### Produkt

#### Procentrabatt på skiktpris och katalogprisregel som beräknas på det ursprungliga priset utan valda alternativ.

_AC-12004 - [GitHub-problem](https://github.com/magento/magento2/issues/38750)_

#### Magento 2.4.7 minTillåten saknad produktorderkvantitet

Systemet fungerar som det ska och sidans källa visar produktens minsta kvantitet korrekt

_AC-12909 - [GitHub-problem](https://github.com/magento/magento2/issues/39142) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/39480)_

#### Magento Exception while execute Magento Payflow Pro Test

_AC-13681_

#### Problem med stödrastret för anpassningsbara alternativ på produktsidan på administratörspanelen

Systemet fungerar som väntat när vi skapar anpassningsbara alternativ med listrutan Typ

_AC-14003 - [GitHub-problem](https://github.com/magento/magento2/issues/39640) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/39694)_

#### Utskriftsalternativet Rekvisitionslistsida fungerar inte

_AC-14711_

#### Alla objekt från andra kunders jämförelselistor tilldelas kunden efter inloggning via administratören

Tidigare, när en administratör använde funktionen&quot;Logga in som kund&quot; i serverdelen, hade produkter från jämförelselistan för en tidigare inloggad kund felaktigt tilldelats den just nu personifierade kunden.  Efter korrigeringen läses jämförelselistan in korrekt för rätt inloggade kund.

_ACP2E-3818 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/462ede94)_

### SEO

#### Uppdatera product url_key via REST API genererar inte en 301 URL-omskrivning

När du uppdaterar URL-nyckeln för produkten via REST API, med inställningen&quot;Skapa permanent omdirigering för URL:er om URL-nyckeln har ändrats&quot; inställd på Ja, skapas en omdirigering från en gammal URL till en ny.

_ACP2E-3900 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/462ede94)_

### Försäljning

#### Orderstatus försvinner när du väljer ett värde i listrutan Orderläge

_AC-15010_

### Säkerhet

#### Paketerad/sammanfogad JS ingår inte i SRI-hash

Före korrigeringen av det skapade paketet eller de sammanfogade filerna lades inte till i listan över SRI-hashar. Nu läggs filerna till korrekt i SRI-hashen.

_ACP2E-3854 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/4ca73607)_

### Leverans

#### [QUANS] - Söker Magento_Fedex kärnmodul efter en giltig token innan du skickar en begäran om en ny?

Adobe Commerce gör inte längre många förfrågningar till FedEx API-tjänsten för åtkomsttoken. Tidigare gjorde Adobe Commerce alltid nya förfrågningar till FedEx API trots att åtkomsttoken fortfarande är giltig, vilket orsakade ett hastighetsbegränsande problem.

_ACP2E-3930 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/4ca73607)_

### Mellanlagring och förhandsvisning

#### Det går inte att förhandsgranska den schemalagda produktuppdateringen med kategoribehörigheter aktiverade

Före korrigeringen visades inte en framtida produkt som skulle aktiveras i förhandsgranskningsläget. Nu visas den även om den aktuella statusen är inaktiverad.

_ACP2E-3786 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/7accebfa)_

#### Olika butiksvyer visas för omfånget vid förhandsgranskning

Före korrigeringen kan en förhandsgranskning av cms-block och cms-sidinnehåll ha öppnats i en annan butik än den butik som tilldelats på cms-blocket eller cms-sidan vid åtkomst från Content Staging Dashboard. Om cms-blocket eller cms-sidan bara har ett visst arkiv tilldelat i mellanlagringsuppdateringen öppnas förhandsgranskningen från Instrumentpanelen för innehållsmellanlagring med rätt arkiv markerat.

_ACP2E-3815_

#### Validering saknas för rabattbeloppsfältet för katalogprisregel

Tidigare validerades fältet rabatt_amount i uppdateringen av mellanlagringsschemat inte korrekt med de aktuella valideringsreglerna. När du har tillämpat korrigeringen valideras dock fältet rabatt_amount korrekt.

_ACP2E-3867 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/462ede94)_

### Moms

#### Fel ordersumma, avrundningen används inte i prisberäkningen.

Systemet hanteras nu korrekt vid beräkning av pris_after_rabatt, rabatt_amount och moms.
orderns faktiska totalbelopp

_AC-11389 - [GitHub-problem](https://github.com/magento/magento2/issues/38455) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/39687)_

### Testramverk

#### [Problem] Ignorera lib/internal/Magento/Framework/App/Test/Unit/_files/app/etc/en..

Systemet ignorerar nu filen &#39;env.php&#39; som genereras när enhetstester körs, vilket säkerställer att Git-statusen förblir ren när testerna körs. Tidigare genererade enhetstester en ny fil, env.php, vilket fick Git-statusen att visa en ny fil som hittades och som fick den att se smutsig ut.

_AC-13293 - [GitHub-problem](https://github.com/magento/magento2/issues/39304) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/37631)_

#### [Problem] Åtgärda integreringstest med spärr

Systemet identifierar och hanterar nu \Magento\TestFramework\App\Config\Interceptor korrekt i integreringstestet, vilket säkerställer att testet kan komma åt nödvändiga data även när det finns ett plugin-program för klassen. Tidigare kunde systemet inte ta hänsyn till att \Magento\TestFramework\App\Config kan vara \Magento\TestFramework\App\Config\Interceptor, vilket resulterade i ett fel vid försök att komma åt egenskapen $data.

_AC-13305 - [GitHub-problem](https://github.com/magento/magento2/issues/39324) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/37187)_

#### [Utgåva] MFTF: Skickar e-post till vänformulär med aktiverad captcha

Testfallet åtgärdar funktionaliteten i formuläret&quot;E-post till vän&quot; när CAPTCHA är aktiverat, vilket säkerställer att inskickningsprocessen fungerar korrekt med både felaktiga och korrekta CAPTCHA-värden.

_AC-13492 - [GitHub-problem](https://github.com/magento/magento2/issues/39462) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/32830)_

#### [TestFramework] Användning av TestCase::getTestResultObject är ogiltig eftersom phpunit v10

_AC-13502 - [GitHub-problem](https://github.com/magento/magento2/issues/39463)_

#### Miljöspecifika enhetstestfel i AC 2.4.7-p3

Det här problemet åtgärdar enhetstestfel som inte återskapas i alla versioner och miljöer. Tidigare gick det inte att åtgärda vissa enhetstester på grund av olika biblioteksversioner eller på grund av att funktioner som lagts till i en senare version saknas.

_ACP2E-3712 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/9ad7d277)_

### Verktyg/DataMigrationTool

#### [ATLH] Allvarligt fel när det inte finns några skillnader

Allvarligt fel visas inte längre när det inte finns någon skillnad att visa

_ACP2E-3901_

### UI Framework

#### WYSIWYG är tomt i dynamiska rader

_AC-12336 - [GitHub-problem](https://github.com/magento/magento2/issues/38893) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/7bdafaa2)_

#### [Problem] Korrigera MIME-typ

Systemet hanterar och korrigerar MIME-typen och typen av gif-bild korrekt

_AC-8001 - [GitHub-problem](https://github.com/magento/magento2/issues/36899) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/36669)_

#### [Problem] Undvik direktåtkomst till granskningslistan Ajax

Systemet hanterar och förhindrar direkt åtkomst till granskningslistan Ajax

_AC-9381 - [GitHub-problem](https://github.com/magento/magento2/issues/37920) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/33876)_

### Uppgraderingar - verktyg för uppgraderingskompatibilitet

#### Föråldrad funktionalitet: Skapande av den dynamiska egenskapen Magento\Framework\Acl::$_roleRegistry

_AC-12343 - [GitHub-problem](https://github.com/magento/magento2/issues/37469)_
