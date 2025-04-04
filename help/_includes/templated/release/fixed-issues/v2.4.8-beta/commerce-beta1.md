---
source-git-commit: b3059a262fe6144bca47fc9fb1b4d201b38af3ba
workflow-type: tm+mt
source-wordcount: '15251'
ht-degree: 0%

---
# Adobe Commerce åtgärdade problem (v2.4.8-beta1)

## Åtgärdade problem i v2.4.8-beta1

Vi har åtgärdat 308 problem i Adobe Commerce 2.4.8 Core-koden. En deluppsättning av de åtgärdade problemen som ingår i den här versionen beskrivs nedan.

### API:er

* _AC-10042_: /V1/operations REST API returnerar fel när parent_txn_id = txn_id
   * _Korrigera anteckning_: Systemet hanterar nu transaktioner för det överordnade och underordnade konceptet korrekt där det överordnade transaktions-ID:t är detsamma som transaktions-ID:t, vilket förhindrar en oändlig loop när en fråga ställs till REST API-slutpunkten för /V1/transaktioner. Tidigare skulle detta scenario resultera i ett allvarligt fel på grund av att den maximala körningstiden överskrids.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/1bafc571>
* _AC-11878_: [Graphql] Typproblem i 2.4.7
   * _Korrigera anteckning_: Systemet hanterar nu heltalsvärden korrekt i funktionen GetCustomSelectedOptionAttributes när en GraphQL-fråga körs, vilket förhindrar typrelaterade fel. Tidigare uppstod ett typfel när en GraphQL-fråga som använde GetCustomSelectedOptionAttributes med ett heltalsargument startades.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/38662>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/pull/38663>
* _ACP2E-2703_: REST API visar order från en annan webbplats. 
   * _Korrigera anteckning_: Systemet stöder nu scopeauktoriserad åtkomst för REST API-administratörstoken och Magento_Sales-slutpunkter, vilket säkerställer att REST API endast visar order som administratören har åtkomst till. Tidigare visades beställningar från alla webbplatser i REST-API:t, oavsett vilken webbplats administratörsanvändaren tilldelat.
* _ACP2E-2755_: Problem med rest api efter aktivering av 2FA Duo
   * _Korrigera anteckning_: 2FA med Duo-säkerhetsalternativ genererar nu korrekt signatur för Rest API
* _ACP2E-2927_: [REST API]: Använd standardvärdet i butiksvyn kontrolleras inte när du har lagt till konfigurationer för en konfigurerbar produkt
   * _Korrigera anteckning_: Problemet har åtgärdats genom att korrekta databasposter har angetts för de anpassningsbara alternativen för en icke-standardbutik. Kryssrutan för den anpassade butiken i avsnittet&quot;Admin > Katalog > Produktredigering > Anpassningsbara alternativ&quot; avmarkerades tidigare på grund av felaktiga databasposter, även om alternativtiteln för den anpassade butiken inte var densamma som standardbutiken.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/3056e9cb>
* _ACP2E-2969_: REST API kan inte göra förfrågningar med snedstreck (/) i SKU när Oauth1 används
   * _Korrigera anteckning_: Före korrigeringen kunde du inte göra ett lyckat API-anrop för en produkt som hade &quot;/&quot; i SKU:n. Nu kan du utfärda en lyckad API-inhämtning av produktinformation även om SKU:n innehåller ett snedstreck.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/b21e5d91>
* _ACP2E-3079_: Uppdatering av kundadress misslyckas vid uppdatering via REST API om &quot;validateDefaultAddress&quot; är aktiverat
   * _Korrigera anteckning_: API-slutpunkten fungerar nu som avsett efter att problemet med ID-nyckeln som saknas i API-nyttolasten har åtgärdats.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/9af794a4>
* _ACP2E-3091_: [Cloud] Skapar kundgruppen Duplicera webbplatsens grupppris i Tier Prices API.
   * _Korrigera anteckning_: Nu går det inte att skapa kundgruppen Duplicera webbplatsens grupppris i .
Tidigare var det möjligt att skapa kundgruppen Duplicera webbplatsens grupppris i Tier Prices API som inte klarade valideringen i Admin när produkten sparades.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/148c3ead>
* _ACP2E-3130_: Det går inte att lägga till orderkommentar med status via REST API
   * _Korrigera anteckning_: Problemet har lösts genom att ändra orderstatus om det endast är från det aktuella läget. Tidigare respekterade den inte orderstatus och förhindrade ändringar i orderstatus, även om den kom från samma läge.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/93d50f8d>

### API:er, GraphQL, skatt

* _AC-12060_: Både Luma (Rest API) och Graphql beräknar inte skatter när bara postnummer anges.
   * _Korrigera anteckning_: Systemet beräknar nu skatter korrekt när bara ett postnummer anges, vilket ger korrekta skattningar för både Luma (Rest API) och GraphQL. Tidigare beräknades endast fraktuppskattningar och skatter inkluderades inte när endast postnummer angavs.

### Konto

* _AC-10782_: Kundadressformuläret tillåter slumpmässig kod i namnfälten
   * _Korrigera anteckning_: Systemet validerar nu indata i fälten Förnamn och Efternamn i kundadressformuläret, vilket förhindrar att slumpmässig kod används. Tidigare tillät systemet att slumpmässig kod användes i dessa fält utan att något fel uppstod.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/38331>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/pull/38345>
* _AC-10990_: mitt konto lägger till en adress som kraschar när jag sparar
   * _Korrigera anteckning_: Systemet sparar nu kundadresser korrekt även när regionsfältet inte visas, vilket förhindrar en krasch under sparningsprocessen. Tidigare uppstod ett undantagsfel om du försöker lägga till eller redigera en adress utan ett fält som visas.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/38406>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/pull/38407>
* _AC-11919_: Admin: Sidåtgärdsknappar flyter åt vänster i stället för åt höger
   * _Korrigera anteckning_: Systemet justerar nu sidåtgärdsknapparna korrekt till höger om det klisterlappande huvudet på adminpanelen, vilket förbättrar det professionella utseendet och känslan. Tidigare var dessa knappar felaktigt flytande till vänster om den klibbiga rubriken.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/38701>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/44cef3a9>
* _AC-11999_: dev:di:infofel i magento 2.4.7
   * _Korrigera anteckning_: Systemet visar nu konstruktorparametrar korrekt när kommandot dev:di:info körs, vilket förhindrar att fel uppstår. Tidigare resulterade körningen av det här kommandot i ett fel på grund av ett typmatchningsfel i argumentet.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/38740>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/0c53bbf7>
* _AC-6071_: Kunden är inloggad, men 404-fel i frontend visas.
   * _Korrigera anteckning_: Butikskundens kontrollpanel läses nu in som förväntat när en kund loggar in. Tidigare kunde kunderna logga in, men den här sidan visade ett 404-fel. [GitHub-35838](https://github.com/magento/magento2/issues/35838)
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/35838>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/pull/36263>
* _ACP2E-2791_: Det går inte att spara kundattributsinformation i kundavsnittet för Admin Edit;
   * _Korrigera anteckning_: Kundens butiks-ID implementeras nu korrekt per webbplatsomfång för administratörskundens redigeringsformulär.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/488c1034>
* _ACP2E-3115_: [Cloud] Det går inte att skapa kund via API när privat försäljning är aktiverat
   * _Korrigera anteckning_: Nu kan kunden skapas av autentiserade administratörsanvändare och med autentiserad integreringstoken via REST api när webbplatsbegränsning är aktiverat.

### Administratörsgränssnitt

* _AC-11588_: Datavalideringen är klar och knappen Importera finns under Importera produkter med beteendet Ersätt
   * _Korrigera anteckning_: Systemet validerar data korrekt och döljer knappen Importera under produktimportprocessen med beteendet Ersätt, vilket förhindrar oavsiktlig ersättning av data. Tidigare validerades data felaktigt och knappen Importera visades, vilket kan leda till inkonsekventa data.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/0574ac23>
* _AC-12167_: [Fel] Magento 2.4.7 tillåter inte produktfoton med filnamnstillägg i versaler.
   * _Korrigera anteckning_: Systemet accepterar nu produktavbildningar med filtillägg i versaler, vilket ger en smidig process för att skapa produkter. Tidigare nekades bildöverföringar med filtillägg i versaler, vilket tvingade användarna att ändra filnamnstillägget till gemener.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/38831>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/c8f87c25>
* _AC-6975_: [Problem] Ange standardindexeringsläget till &quot;schedule&quot;
   * _Korrigera anteckning_: Alla nya indexerare är som standard i **[!UICONTROL Update by Schedule]**-läge.  Tidigare var standardläget **[!UICONTROL Update on Save]**. Befintliga indexerare påverkas inte. [GitHub-36419](https://github.com/magento/magento2/issues/36419)
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/36419>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/0b410856>
* _AC-7700_: [Utgåva] Ta bort indexerarändringstabeller när mview-prenumerationen avbryts
   * _Korrigera anteckning_: Systemet tar nu automatiskt bort oanvända ändringstabeller när ett index ändras från &quot;uppdatera enligt schema&quot; till &quot;uppdatera vid spara&quot;, vilket markerar indexet som ogiltigt för att säkerställa att inga poster missas. Om du tidigare växlade ett index till&quot;update on save&quot; skulle oanvända ändringsloggtabeller i systemet utelämnas och alla ändrade index markeras som&quot;valid&quot;.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/29789>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/pull/25859>
* _AC-9843_: i18n:collect-frases break the translations integrity
   * _Korrigera anteckning_: Kommandot `bin/magento i18n:collect-phrases -o` samlar nu in och lägger till nya fraser från JavaScript- och .phtml-filer korrekt, vilket säkerställer att översättningarna återspeglas korrekt i översättningsfilen. Tidigare kunde systemet inte inkludera flerradiga översättningsfraser från JavaScript-filer och fraser från .phtml-filer i översättningsfilen, vilket ledde till ofullständiga eller felaktiga översättningar.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/0c53bbf7>
* _ACP2E-2687_: Behörighetsproblem för åtkomst till dynamiskt block
   * _Korrigera anteckning_: Tidigare för begränsad administratör som lade till ett nytt dynamiskt block uppstod ett fel. Efter implementeringen av den här korrigeringsbegränsade administratören kan lägga till det dynamiska blocket och redigera blocket utan fel
* _ACP2E-2787_: Apostrofen i butiksvyns namn ersätts av &#39;
   * _Korrigera anteckning_: Stödrastrets visningsfilter visar nu apostrofer korrekt
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/38395>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/39d54c2d>
* _ACP2E-2847_: Favicon-överföringen kan inte validera ICO-filer
   * _Korrigera anteckning_: Filverifieringsfelet har uppdaterats till &quot;Filverifieringen misslyckades. Kontrollera inställningarna för bildbearbetning i Store-konfigurationen.&quot; Tidigare var det bara&quot;Filvalidering misslyckades&quot;.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/39d54c2d>
* _ACP2E-2957_: Galleriet i PageBuilder visar en gammal miniatyrbild i stället för den nyligen överförda bilden
   * _Korrigera anteckning_: Generera om förhandsvisningar av bilder för bilder som har tagits bort och överförts med samma namn via mediegalleriet i sidbyggarinnehållet.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/001e5188>, <https://github.com/magento/magento2-page-builder/commit/60140cd2>
* _ACP2E-2978_: Om du sparar produkten av en admin-användare med ett annat rollomfång skrivs befintlig relaterad produktinformation över/tas bort i produkten
   * _Korrigera anteckning_: Tidigare, före korrigeringen, återställdes de relaterade produkterna och blev tomma när den sekundära administratören klickade på knappen Spara utan att ändra i den relaterade produkten. Efter den här korrigeringen klickar den sekundära administratören på knappen Spara och produkten återställs inte och sparas utan fel.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/3056e9cb>
* _ACP2E-3033_: Det går inte att exportera fler än 200 order
   * _Korrigera anteckning_: Servergränsen för begärandorleken för tidigare skickade valda ID:n har ignorerats genom att HTTP-begäran från GET till POST ändrades för att åtgärda problemet. På grund av serverbegränsningarna för GET-begäran har ett problem påträffats.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/93d50f8d>
* _ACP2E-3037_: Utcheckningssidans valideringsmeddelande är felaktigt.
   * _Korrigera anteckning_: Om ett obligatoriskt fält lämnas tomt, till exempel &quot;adress&quot;, visas inte meddelandet vid validering på serversidan. Valideringen på klientsidan säkerställer att det obligatoriska fältfelmeddelandet visas med meddelandet&quot;This is a required field&quot;. Tidigare visades meddelandet&quot;address is required&quot; om något obligatoriskt fält lämnades tomt, förutom valideringsmeddelandet på klientsidan.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/9af794a4>
* _ACP2E-3125_: Problem med mallar för återställning av lösenord med administratörsanvändare
   * _Korrigera anteckning_: Problemet har lösts med rätt nyckel, som nu inkluderar administratörens användarnamn i e-postmallen och korrekt fyller i ämnet. Tidigare berodde problemet på en inaktuell nyckel som användes.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/93d50f8d>
* _ACP2E-3149_: Dubbla snedstreck i kundsegmentets URL
   * _Korrigera anteckning_: Dubbla snedstreck visas inte i URL:en när användaren klickar på Återställ filter i rutnätet.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/8459b17d>
* _ACP2E-3171_: COD är inte tillgängligt för tillåtna specifika länder
   * _Korrigera anteckning_: Nu kan du få kontanter vid leverans i vissa länder när det behövs och   AC-3216 fungerar som förväntat.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/6f4805f8>
* _ACP2E-3178_: Det går inte att uppdatera status för anpassad skapad order
   * _Korrigera anteckning_: &#39;
Vi kan nu uppdatera beställningsstatus som har skapats av användaren, men tidigare gick det bara att ändra status om den aktuella statusen var antingen &quot;bearbetning&quot; eller &quot;bedrägeri&quot;.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/38659>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/8459b17d>

### Administratörsgränssnitt, katalog

* _ACP2E-2708_: Det går inte att ändra befattningar för kategoriprodukterna på den tillåtna webbplatsen som en begränsad administratörsanvändare
   * _Korrigera anteckning_: Tillåt att en begränsad administratörsanvändare kan lägga till och sortera produkter i en kategori i rotkategorin som tilldelats under en begränsad webbplats.

### Administratörsgränssnitt, prestanda

* _ACP2E-3169_: Efter uppdatering till 2.4.5-p8 uppstår 500 fel när order skapas från administratör
   * _Korrigera anteckning_: Tidigare gick det inte att göra en beställning från administratören när HTML-minifiering aktiverades. Nu när HTML minification är aktiverat kan du beställa från administratören.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/b21e5d91>

### Administratörsgränssnitt, leverans

* _ACP2E-2519_: Kupongkodsantalet uppdateras inte i   Kolumnen &quot;Använd tid&quot; på fliken Hantera kupongkoder om en order har flera leveranser.
   * _Korrigera anteckning_: När en order placerades med flera leveranser uppdaterades inte kupongkodsantalet i kolumnen Används på fliken Hantera kupongkoder. Nu visas rätt antal i både &quot;Använd tid&quot; och återspeglar önskade värden vid flera leveranser.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/4745100c>

### Analyser/rapporter

* _ACP2E-2570_: Avancerad rapport fungerar inte
   * _Korrigera anteckning_: Systemet stöder nu generering av datafiler för avancerad rapportering för extra stora datauppsättningar genom att läsa in och skriva rapporter i grupper om 10 000. Tidigare kunde inte modulen för avancerad rapportering generera datafiler för extra stora datauppsättningar, vilket orsakade felen&quot;MySQL-servern har försvunnit&quot; under körningen av cron-jobbet analytics_collect_data.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/a12063bd>
* _ACP2E-3080_: Admin Ordered Products Products Report date range visibility issue.
   * _Korrigera anteckning_: Användaren kan välja valfritt datum från rapporten för beställda produkter. När en tabell har uppdaterats återställs TO-datumet när du väljer FROM-datumet.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/6f4805f8>
* _ACP2E-3096_: Felaktiga rullhuvuden som gör att newrelic:create:deploy-marker fungerar inte
   * _Korrigera anteckning_: Systemet formaterar nu krullningshuvuden korrekt, så att kommandot newrelic:create:deploy-marker kan skapa en distributionsmarkör i New Relic. Tidigare kunde felaktiga rullrubriker inte skapa en distributionsmarkör i New Relic.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/37641>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/6a185204>

### Analys/rapportering, B2B

* _ACP2E-2300_: B2B - platskartan innehåller produkter/kategorier som inte har tilldelats den delade katalogen
   * _Korrigera anteckning_: Begränsa webbplatskartgenererade kategorier och produkter till de kategorier och produkter som endast tilldelats den offentliga delade katalogen och/eller behörighetsinställningarna för katalogkategorin.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/ea79f7dd>

### Analytics/Reporting, Cloud

* _ACP2E-3067_: Magento ignorerar de flesta New Relic kredittransaktioner #34108
   * _Korrigeringsanteckning_: AC rapporterar korrekt kundjobbrelaterade transaktioner till NewRelic. Tidigare visades vissa kundjobbrelaterade transaktioner som&quot;OtherTransaction/Action/unknown&quot; i NR
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/35b1b1da>

### B2B

* _ACP2E-2873_: [Cloud] Prisvisningen i mobil- och datorversionen är inte densamma i&quot;Mina offerter&quot;
   * _Korrigeringsanteckning_: Raden Inkludera moms som inte behövs visas inte längre i Negotiable Quote när avsnittet för katalogens totala pris har utökats.
* _ACP2E-3044_: Onödiga kantlinjer i avsnittet Mina beställningar
   * _Korrigera anteckning_: Tidigare skapades en extra behållare (orderreferenser) som tillämpade ytterligare CSS-klasser, vilket orsakade att onödiga kantlinjer visades under ordernumret i avsnittet Mina beställningar, som inte visas nu.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/9af794a4>

### B2B, katalog

* _ACP2E-2860_: Produkter/kategorier som visas under omindexering vid användning av NoDDL- och kategoribehörigheter
   * _Korrigera anteckning_: Undvik att visa för butiksbegränsade kategorier och deras innehåll medan katalogbehörighetsindexering utförs.

### B2B, ramverk

* _AC-9607_: Det går inte att filtrera företagsstödrastret och sedan försöka exportera stödraster-CSV:n. Undantag genereras
   * _Korrigera anteckning_: Systemet tillåter nu lyckad CSV-export av företagsrutnätsdata på adminpanelen, även när filter som Utgående balans och Företagstyp tillämpas. Om du tidigare tillämpade vissa filter och försökte exportera stödrasterdata skulle det resultera i ett fel och ett undantag genereras.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/44cef3a9>

### Braintree

* _BUNDLE-3367_: Betala via LPM
   * _Korrigera anteckning_: Systemet återger nu LPM (Local Payment Methods) korrekt vid första inläsningen, även när en inloggad kunds frakt- och faktureringsadresser inte stämmer, vilket ger en smidig utcheckningsprocess. Tidigare var det fel på kundens leverans- och faktureringsadresser som förhindrar LPM-återgivning, vilket kan orsaka störningar vid utcheckningen.
   * _GitHub-kodbidrag_: <https://github.com/magento/ext-braintree/pull/204>
* _BUNDLE-3368_: Kan konfigureras med virtuell som underordnad produkt
   * _Korrigera anteckning_: Systemet tillåter nu expressbetalningsmetoder för konfigurerbara produkter som har en virtuell underordnad produkt, vilket ger en smidig utcheckningsprocess. Tidigare var expressbetalningsmetoder inte tillgängliga när en konfigurerbar produkt med en virtuell underordnad produkt lades till i kundvagnen.
   * _GitHub-kodbidrag_: <https://github.com/magento/ext-braintree/pull/204>
* _BUNDLE-3369_: Fel vid CVV-verifiering
   * _GitHub-kodbidrag_: <https://github.com/magento/ext-braintree/pull/204>
* _BUNDLE-3370_: Vaulting Via kontoområdet Issues 247
   * _Åtgärda anteckning_: Nu kan kunder spara ny kortinformation eller PayPal-kontoinformation på flera webbplatser utan att stöta på auktoriseringsfel. Tidigare kunde kunderna inte spara nya betalningsmetoder på olika webbplatser och fick ett felmeddelande om auktorisering.
   * _GitHub-kodbidrag_: <https://github.com/magento/ext-braintree/pull/204>
* _BUNDLE-3371_: Leverera till en adress från ett annat land
   * _Korrigera anteckning_: Systemet tillåter nu att transaktioner behandlas utan fel när de skickas till en adress från ett annat land, vilket ger en smidig utcheckningsprocess. Tidigare skulle försök att leverera till en adress från ett annat land resultera i konsolfel, trots att det inte finns några synliga fel på klientsidan.
   * _GitHub-kodbidrag_: <https://github.com/magento/ext-braintree/pull/204>
* _BUNDLE-3372_: Kreditkort - Teardown-funktion
   * _Korrigera anteckning_: Systemet hanterar nu rippningen av Braintree PayPal-komponenter korrekt när en kund går tillbaka från betalningssidan till leveranssidan, vilket förhindrar fel och säkerställer att PayPal Express-knapparna återges korrekt. Tidigare uppstod ibland ett fel när Braintree PayPal-komponenterna skulle kapas ned när du navigerade tillbaka till leveranssidan från betalningssidan.
   * _GitHub-kodbidrag_: <https://github.com/magento/ext-braintree/pull/204>
* _BUNDLE-3373_: Leveransåteranrop för PayPal Express
   * _Korrigera anteckning_: Systemet visar nu korrekt tillgängliga leveransmetoder i modala PayPal Express, så att kunderna kan välja önskad leveransmetod innan de går vidare till granskningssidan eller slutför transaktionen. Tidigare fanns det inga leveransmetoder att välja mellan i PayPal Express modal, vilket innebar att kunderna måste välja en leveransmetod på en separat granskningssida innan de kunde slutföra transaktionen.
   * _GitHub-kodbidrag_: <https://github.com/magento/ext-braintree/pull/204>

### Kort och utcheckning

* _AC-10660_: Undantag hanteras inte korrekt när en produkt läggs till i kundvagnen på produktsidan för jämförelse
   * _Korrigera anteckning_: Systemet hanterar nu undantag korrekt när en produkt läggs till i kundvagnen från jämförelseproduktsidan och ett meddelandehanterarmeddelande visas i kontrollenheten. Tidigare skulle ett undantag resultera i att en JSON-kodad sida returneras i stället för att fångas upp och hanteras korrekt.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/38200>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/pull/38257>, <https://github.com/magento/magento2/commit/0c53bbf7>
* _AC-10698_: GTag skickar inte transaktionspriser och summor.
   * _Korrigera anteckning_: Systemet skickar nu transaktionspriser och summor korrekt till Google Tag när GTag är aktiverat, vilket ger korrekt spårning av e-handelsdata. Tidigare skickades valutan felaktigt som en del av&quot;alla&quot;-beställningarna, i stället för att kopplas till den enskilda ordern.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/37348>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/pull/37504>, <https://github.com/magento/magento2/pull/37349>
* _AC-11641_: [Utgåva] [Utcheckning] Beroende direktiv uppdaterat i mallen för misslyckade betalningar via e-post
   * _Korrigera anteckning_: Systemet utelämnar nu leveransadressen och leveransmetoden korrekt från den misslyckade e-postmallen för betalningar för virtuella produkter, så att endast relevant information inkluderas i e-postmeddelandet. Tidigare innehöll den misslyckade e-postbetalningen för virtuella produkter felaktigt leveransadressen och leveransmetoden.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/32781>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/pull/32511>
* _AC-11876_: [Problem] Regressionsregression för försäljningsregler i 2.4.7
   * _Korrigera anteckning_: Systemet validerar nu försäljningsreglerna korrekt och förhindrar att en kupongkod används i en kundvagn när produktvillkoret inte matchar något produktnamn. Tidigare kunde en försäljningsregel tillämpas och en rabatt ges på fraktbeloppet även när produktvillkoret inte matchade något produktnamn.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/38671>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/0574ac23>
* _AC-11993_: [Utgåva] Inläsaren blockerar leveransmetoderna efter att postkoden har ändrats, regler för validering av fraktsatser
   * _Korrigera anteckning_: Systemet hanterar nu anpassade leveransmetoder korrekt utan valideringsregler för fraktsatser, vilket säkerställer att inläsaren inte blockerar leveransmetoderna efter att postkoden har ändrats i leveransadressen under utcheckningen. Om du ändrar postnumret i leveransadressen under utcheckningen skulle det medföra att inläsaren blockerar leveransmetoderna och inte försvinner när anpassade leveransmetoder utan regler för utcheckning av fraktsatser används.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/38742>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/1bafc571>
* _AC-12170_: Funktionen för kupongkod fungerar inte som den ska på utcheckningssidan för Magento 2.4.7
   * _Korrigera anteckning_: Systemet aktiverar nu inmatningsfältet för rabattkod/kupong på utcheckningssidan för virtuella och nedladdningsbara produkter, så att användare kan tillämpa rabattkoder som förväntat. Tidigare inaktiverades rabattkoden/kuponginmatningen och knappens titel visades som&quot;Avbryt kupong&quot;, vilket förhindrar användare att använda rabattkoder.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/38826>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/1bafc571>
* _AC-8103_: Översättningsmoms vid adressrendering
   * _Korrigera anteckning_: Systemet tillåter nu översättning av texten&quot;moms&quot;,&quot;T&quot;,&quot;F&quot; i adressrenderarna, vilket gör att användare kan översätta dessa villkor till butikens specifika språk. Tidigare var dessa villkor inte översättningsbara, vilket tvingade användarna att använda en lösning.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/36942>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/pull/36943>
* _ACP2E-2055_: Duplicera order med samma offert-ID samtidigt med få tidsskillnader
   * _Korrigera anteckning_: Problemet när Adobe Commerce-kunder påträffade dubblettorder som placerats med samma QuoteID har åtgärdats
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/f89a447e>
* _ACP2E-2470_: Beständig kundvagn rensad under kassan
   * _Korrigera anteckning_: Efter korrigeringen avslutas inte den beständiga sessionen om du väljer betalningsmetod under utcheckning när du inte är inloggad.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/a4fbf702>
* _ACP2E-2518_: Omarbetning lägger till ej tilldelad produkt i kundvagn
   * _Korrigera anteckning_: Tidigare kunde produkter i olika butiker ordnas om från den andra butiken. När korrigeringen har tillämpats på samma butik kan samma omfattningsprodukt omordnas när kundkontoresursen är aktiverad
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/f89a447e>
* _ACP2E-2620_: I admin uppdateras inte kundvagnen till vänster när du väljer artiklar och &quot;Flytta till kundvagn&quot; till höger
   * _Korrigera anteckning_: Kundvagnen till vänster uppdateras när du väljer artiklarna och Flytta till kundvagn till höger i administratörssidan. Tidigare fungerade inte den här funktionen eftersom de omformade varukorgsobjekten inte blev tomma från sessionen.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/39d54c2d>
* _AVS2E-2646_: [Förs.regel för molnet] tillämpas inte på den första ordern för flerleverans
   * _Korrigera anteckning_: Efter korrigeringen visas rabatten korrekt för varje order av samma flerleveransoffert.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/f89a447e>
* _ACP2E-2664_: [Cloud] Production Parallel-begäranden om att lägga till samma produkt i kundvagnen resulterar i två separata objekt i Cart rest API
   * _Korrigera anteckning_: Systemet bearbetar nu flera parallella förfrågningar korrekt för att lägga till samma produkt i vagnen i ett enda radobjekt, vilket förhindrar att separata radartiklar för samma SKU skapas. Tidigare skulle parallella begäranden om att lägga till samma produkt i kundvagnen via REST API resultera i flera radobjekt för samma SKU.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/f89a447e>
* _ACP2E-2676_: Problem med beställning från presentregistret Magento 2.4.4 Enterprise/Commerce
   * _Korrigera anteckning_: Problemet med att det inte gick att köpa en produkt från ett presentregister har lösts, vilket gör att det går att placera beställningar och uppdatera presentregistret korrekt. Tidigare inträffade ett fel när en beställning från ett presentregister skulle göras, vilket förhindrar att köpet slutförs.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/35432>
* _ACP2E-2704_: Det gick inte att skicka cookien. Storlek på&quot;bildmeddelanden&quot; vid försök att ändra ordning
   * _Korrigera anteckning_: Omsorteringsprocessen genererar inga egna fel nu. Den förlitar sig på varukorg som listar inbyggda artikelkontroller.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/ba25af8a>
* _ACP2E-2798_: Standardleveransadress har inte valts vid utcheckning
   * _Korrigera anteckning_: Standardleveransadress väljs nu för händelse i samband med aktiverad adresssökning.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/7e0e5582>
* _ACP2E-2897_: [CLOUD] graphql addProductsToCart api-problem med anpassat alternativ
   * _Korrigera anteckning_: GraphQL lägger korrekt till samma produkt i varukorgen med olika anpassade alternativ
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/c971859e>
* _AVS2E-2917_: [Regler för relaterade produkter i molnet] fungerar inte när butiksvyn ändras
   * _Korrigera anteckning_: Problemet har åtgärdats genom att det anpassade egenskapsvärdet har tagits emot på kundvagnssidan. Tidigare hämtades det inte korrekt när man växlade mellan butiker på kundvagnssidan.
* _ACP2E-2923_: Flera adresser har lagts till i kontot vid utcheckning som ny kund
   * _Korrigera anteckning_: Systemet sparar nu en ny kundadress endast en gång om beställningen inte kunde skapas, vilket förhindrar att flera identiska adresser skapas i händelse av orderplaceringsfel. Tidigare sparade systemet en ny adress varje gång ett orderplaceringsförsök gjordes, oavsett om ordern skapades eller inte.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/001e5188>, <https://github.com/magento/inventory/commit/2ebcef39>
* _ACP2E-3004_: Om du ändrar ordningen på kundorder via gästbeställningsformulär blir kundvagnen tom
   * _Korrigera anteckning_: Tidigare omdirigerades kunden till inloggningssidan när en ombeställning placerades via sidan Beställningar och returnering. När den här korrigeringen har tillämpats omdirigeras den registrerade kunden korrekt till sidan Visa kundvagn när en ombeställning görs. Flödet fungerar på samma sätt som gästkunder.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/6a185204>
* _ACP2E-3025_: Administratörsanvändare med begränsade rollresurser kan inte visa varukorgar
   * _Korrigera anteckning_: Tidigare kunde den begränsade administratören inte se den övergivna kundvagnen från adminpanelen för en associerad webbplats. När den här korrigeringen har tillämpats kan administratören se den övergivna kundvagnen på adminpanelen.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/d1f7dc95>

### Kort och utcheckning, utcheckning/utcheckning av en sida

* _AC-9386_: [Slumpmässigt fel] E-postfältet renderas inte eller det tar lång tid att visa det på utchecknings- eller betalningssidan
   * _Korrigera anteckning_: Commerce återger nu fältet **[!UICONTROL Email]** på utchecknings-, leverans- och betalningssidorna som förväntat. Tidigare fanns inte det här fältet eller så renderades det långsamt.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/e1babcfd>

### Kort och utcheckning, beställ

* _ACP2E-3097_: Datumväljaren för produkt med flera anpassningsbara alternativ med datumfält som inte fungerar när en beställning från en administratör placeras
   * _Korrigera anteckning_: Datumväljaren visas nu korrekt för alla datumfält när en produkt konfigureras med flera anpassningsbara datumalternativ i processen för att skapa administratörsorder. Tidigare visades datumväljaren bara för det första datumfältet, och återstående fält lämnades utan datumväljare.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/b21e5d91>

### Kundvagn och utcheckning, leverans

* _AC-12119_: Direktköp -&quot;billigaste leveransen&quot; brutet för konfigurerbara produkter
   * _Korrigera anteckning_: Funktionen Direktköp har felaktigt valt det dyrare alternativet för leverans i butik för konfigurerbara produkter i stället för den billigaste metoden med schablonbelopp. Med den här programfixen kan du säkerställa att rätt leveranssätt väljs baserat på det faktiska priset.&quot;
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/38811>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/pull/38819>, <https://github.com/magento/magento2/commit/29fe9097>

### Katalog

* _AC-10910_: Rensning av databastabellen cron_schedule rensar inte jobb som inte finns
   * _Korrigera anteckning_: Systemet rensar nu automatiskt databastabellen cron_schedule och tar bort poster för jobb som inte längre finns i systemet. Detta ger optimala prestanda genom att ett minimalt antal rader i tabellen bevaras. Tidigare rensades inte poster för jobb från inaktiva eller borttagna moduler, vilket ledde till onödig datainsamling i tabellen cron_schedule.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/38217>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/pull/38693>
* _AC-10953_: Nivåpriset tas inte bort från den konfigurerbara produkten
   * _Korrigera anmärkning_: Systemet tar nu bort ett produktskikt korrekt när det konverteras från en enkel produkt till en konfigurerbar produkt, vilket ger korrekt prisvisning i förgrunden. Tidigare togs inte nivåpriset bort för en konfigurerbar produkt när en produkt konverterades från en enkel produkt till en konfigurerbar produkt, vilket ledde till en felmatchning av det visade priset.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/38390>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/pull/38427>
* _AC-11804_: Kategoribeskrivningen WYSIWYG är tomt för icke-standardgranskning
   * _Korrigera anteckning_: Systemet sparar och visar nu kategoribeskrivningen korrekt i WYSIWYG Editor när en kategori redigeras på butiksvynivå. Tidigare visades WYSIWYG-redigeraren som tom när en kategoribeskrivning sparades på butiksvynivån.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/38622>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/pull/38623>
* _AC-12076_: [Problem] Åtgärda formuleringen för filterobjektet vid navigering i lager
   * _Korrigera anteckning_: Systemet använder nu orden&quot;objekt&quot; och&quot;objekt&quot; korrekt i det lageruppbyggda navigeringsfilterobjektet, vilket gör filterbeskrivningarna tydligare och exaktare. Tidigare användes dessa ord felaktigt, vilket kan skapa förvirring för användare som navigerar i filteralternativen.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/38789>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/pull/37852>
* _AC-12164_: Formatet Datum och tid för det anpassade alternativet fungerar inte
   * _Korrigera anteckning_: Systemet tillämpar nu korrekt det konfigurerade datumformatet på anpassade produktalternativ av typen Datum, vilket säkerställer att datumformatet visas korrekt på frontsidan. Tidigare speglade inte ändringar i datumformatskonfigurationen på frontend för anpassade produktalternativ av typen Date.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/32990>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/pull/38925>
* _AC-6738_: Unik nyckel saknas i eav_attribute_option_value-tabellen
   * _Korrigera anteckning_: Systemet innehåller nu en unik nyckel för kolumnerna &#39;option_id&#39; och &#39;store_id&#39; i tabellen &#39;eav_attribute_option_value&#39;, vilket förhindrar möjligheten att ha flera värden för samma butiksvy. Tidigare kunde felaktig kod resultera i ett alternativ med flera värden för samma butiksvy, vilket orsakade problem när du redigerade produkter eller attribut.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/24718>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/pull/28796>
* _AC-8297_: [Issue] Använd synlighetsklassen för kategoriproduktindexeraren i stället för hårdkodade värden
   * _Korrigera anteckning_: Systemet använder nu synlighetsklassen för kategoriproduktindexeraren i stället för hårdkodade värden, vilket förbättrar modulariteten. Tidigare användes hårdkodade värden i kategoriproduktindexeraren, vilket begränsade flexibiliteten och anpassningsbarheten.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/37200>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/pull/37199>
* _AC-9375_: Valutakoden ändras inte i widgeten Ny produkt
   * _Korrigera anteckning_: Systemet uppdaterar nu valutakoden korrekt i widgeten Ny produkt när valutan ändras i förgrunden, vilket ger en konsekvent valutavisning på hela webbplatsen. Tidigare påverkades inte valutakoden som visades i widgeten Ny produkt om du ändrade valutan i klientdelen.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/37898>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/pull/37899>
* _ACP2E-2224_: Normalpriset visas inte på PLP för konfigurerbar produkt
   * _Korrigera anteckning_: Normalpriset visas nu på produktlistsidor för konfigurerbara produkter som har underordnade produkter med specialpris.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/a4fbf702>
* _ACP2E-2478_: Stock-information visas inte korrekt på Visual Merchandising-rutnät
   * _Korrigera anteckning_: Stock visas nu enligt vald butik.
   * _GitHub-kodbidrag_: <https://github.com/magento/inventory/commit/bdbf97ea>
* _ACP2E-2621_: Widget-innehåll uppdateras inte på cms-sidan
   * _Korrigera anteckning_: Systemet uppdaterar nu widgetinnehållet på en CMS-sida när en produkt är inställd som ny och sparad, så att den uppdaterade produktsamlingen visas på sidan. Tidigare uppdaterades inte sidan för att visa den nya produkten på grund av de felaktiga cacheidentiteter som användes för widgeten i cachen.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/f89a447e>
* _ACP2E-2630_: Problem med att spara avancerade priser på paketprodukter
   * _Korrigera anteckning_: Prestandaförbättring för produktsparande.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/b2286ecf>
* _ACP2E-2652_: [On-Premise] Indexeringsprocessen är ineffektiv när regler för katalogpris skapas
   * _Korrigera anteckning_: Om du nu sparar katalogprisregel blir indexerare inte ogiltiga, utan indexerar bara om berörda produkter
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/f89a447e>
* _ACP2E-2679_: Uppdaterar tid för produktattribut av typen Datum och Tid via CSV-import
   * _Korrigera anteckning_: Nu datum- och tidsattribut kommer att ha en tidsdel i exporterade data. Det går också att uppdatera tiden för sådana attribut med import. Om Fältbilaga är aktiverat kommer attributvärden i kolumnen &quot;additional_attributes&quot; att omslutas av dubbla citattecken.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/38306>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/ea79f7dd>
* _ACP2E-2689_: Inget lämpligt felmeddelande när webbplats-ID är fel i begäran
   * _Korrigera anteckning_: Nu har rätt felmeddelande lagts till för att visas när webbplats-ID:t är fel i begäran. Tidigare fanns det ingen validering när webbplats-ID:t var fel i begäran.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/39d54c2d>
* _ACP2E-2785_: Produktbilden förloras efter att en befintlig schemalagd uppdatering som inte påverkar bilden har tagits bort
   * _Korrigera anteckning_: Produktbilder tas inte bort när mellanlagringsuppdateringen tas bort.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/c8931218>
* _ACP2E-2799_: [Cloud] Fel produktpris för paket när det används med nivåpriser
   * _Korrigera anteckning_: Tidigare genererades olika slutpriser för kundvagnen och produktlistningssidan/produktinformationssidan när vissa procentuella rabatter avrundade uppåt till 2 decimaler skulle beräknas. När den här korrigeringen har tillämpats är slutpriset för paketprodukten detsamma som på produktinformationssidan, produktlistningssidan och minikundvagnssidan.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/38091>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/b2286ecf>
* _ACP2E-2805_: Katalogkampanjregeln fungerar inte med attributet quantity_and_stock_status
   * _Korrigera anteckning_: Attributet quantity_and_stock_status kommer nu att beaktas av katalogerbjudanderegeln, som inte tidigare har beaktats när ny produkt genereras från adminsidan.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/35627>
   * _GitHub-kodbidrag_: <https://github.com/magento/inventory/commit/cf34971d>
* _ACP2E-2837_: Produktentitetens kolumnvärden updated_at uppdateras inte när priset uppdateras via REST API
   * _Korrigera anteckning_: Produktens kolumn för senaste uppdatering från administratören uppdateras med rätt datum samtidigt som befintliga produkter uppdateras via REST API. Tidigare uppdaterades inte kolumnen&quot;senast uppdaterad&quot; korrekt.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/39d54c2d>
* _ACP2E-2840_: Det går att ange icke-unika värden via produktimport
   * _Korrigera anteckning_: Systemet använder nu den unika värdebegränsningen för unika produktattribut vid import, vilket förhindrar dubblettvärden för det attributet. Tidigare var det möjligt att ange icke-unika värden för produktattribut som konfigurerats att ha unika värden via produktimport.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/38445>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/7e0e5582>
* _ACP2E-2843_: Produkter på klientsidan lagrar specifika data när Single-Store-läge är aktiverat
   * _Korrigera anteckning_: Tidigare migrerades inte ändringarna till webbplatsnivå när vi aktiverade läget för en enskild butik för standardbutiksvyn. När den här korrigeringen har tillämpats synkroniseras standardarkivspecifika data med data på webbplatsnivå när läget för en enskild butik aktiveras, och eventuella konflikter för produkter och kategorier kommer att lösas.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/c8931218>
* _ACP2E-2857_: Det går inte att ange &quot;Default Sort By&quot; i en kategori med det övriga API:t
   * _Korrigera anteckning_: Uppdatera korrekt default_sort_by för en kategori via REST/SOAP APi-begäran
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/57a32313>
* _ACP2E-2871_: [Cloud] Affärsmannen har problem med önskelisteantal
   * _Korrigera anteckning_: Om du lägger till en produkt i önskelistan i en butik ökar inte längre antalet önskelistor i andra butiker som är öppna i samma webbläsare. Tidigare hade antalet önskelistor ökat även i den andra butiken om båda butikerna lästs in i samma webbläsare.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/3a7c4d17>
* _ACP2E-2874_: Kategorisidan i förgrunden visar tomma platser när paketprodukten används
   * _Korrigera anteckning_: Paketprodukter som inte kan säljas i den aktuella butikskontexten indexeras inte längre.
   * _GitHub-kodbidrag_: <https://github.com/magento/inventory/commit/bc37ec76>
* _ACP2E-2888_: [CLARIFICATION] Problem i produktsekvensregister för paket
   * _Korrigera anteckning_: Posterna i produktsekvenstabellerna (sequence_product_bundle_option, sequence_product_bundle_selection) tas nu bort när paketprodukten tas bort eller Paketproduktalternativen tas bort.
Tidigare togs posterna i produktsekvenstabellerna i Bundle inte bort.
* _ACP2E-2905_: [Cloud] Utfärdande av offert i arkitektur för flera webbplatser
   * _Korrigera anteckning_: Tidigare kunde inte arkitekturen för flera webbplatser med olika valutor och kundgrupper tillämpa rabatter på butiken korrekt. När den här korrigeringen har implementerats kommer flerwebbplatsarkitekturen med olika kundgruppsprisrabatter att gälla för olika butiker.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/38506>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/a4fbf702>
* _ACP2E-2909_: dynamic-rows.js:658 Uncaught TypeError: dataRecord.slice när paketprodukter redigeras
   * _Korrigera anteckning_: Det finns inget javascript-fel i webbläsarkonsolen när du tar bort alternativ från paketprodukten.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/38505>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/93d50f8d>
* _ACP2E-2950_: [Cloud] Felaktigt produktpris i orderbekräftelsen
   * _Korrigera anteckning_: Korrekt belopp visas för paketalternativ i ordning på Storefront när en annan valuta än bas användes.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/a4fbf702>
* _ACP2E-2956_: YouTube Video Adding Bug
   * _Korrigera anteckning_: Produktbilder och videor har konfigurerats i det globala omfånget. Eftersom du inte kan ha en produktvideo i ett omfång och inte i ett annat, har Youtube API-nyckelinställningen ställts in på globalt omfång.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/a4fbf702>
* _ACP2E-2964_: [Cloud] URL-uppdatering endast för store_id=0
   * _Korrigera anteckning_: URL-sökvägen lagras nu med rätt lagrings-ID. Tidigare var lagrings-ID felaktigt, vilket resulterade i att felaktiga URL-sökvägar återstår i databasen när kategorier flyttas.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/9af794a4>
* _ACP2E-3009_: async.operations.all utfördes och ett fel skapades.
   * _Korrigera anteckning_: Felaktiga produktlänksdata i REST API-anrop orsakar inte längre allvarliga fel.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/a4fbf702>
* _ACP2E-3029_: [Cloud] Mobilproblem Det går endast att fästa vid PDP-bilden
   * _Korrigera anteckning_: Systemet har nu stöd för funktionen att nypa till zooma i bilder av produktinformationssidor i mobilvyn i Chrome, vilket förbättrar användarupplevelsen för mobila enheter. Tidigare zoomade inte dubbeltryck på bilden i mobilvyn i Chrome in på bilden som förväntat.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/148c3ead>
* _ACP2E-3058_: Etikett saknas i LayeredNavigation med alternativnamnet 0
   * _Korrigera anteckning_: Problemet har åtgärdats genom att ett tomt värdekontrollprogram ignoreras för attributvärdet 0. Tidigare ansågs den vara tom och orsakade problemet.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/3a7c4d17>
* _ACP2E-3069_: Kunderna ser priser från andra kundgrupper
   * _Korrigeringsanteckning_: Ett problem där kundgruppsrelaterad information sparades i fel segment på grund av det gamla värdet för X-Magento-Vary i begäran har åtgärdats
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/d1f7dc95>
* _ACP2E-3076_: Fel vid borttagning av paketalternativ
   * _Korrigera anteckning_: Systemet tar nu bort paketalternativen korrekt utan att utlösa ett fel eller få sidan att sluta svara. Om du tidigare försökte ta bort paketalternativen skulle det resultera i felet&quot;Sidan svarar inte&quot; och förhindra att produkten sparas.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/6a185204>
* _ACP2E-3094_: Kategoribehörigheter i webbläsaren för slut på minne
   * _Korrigera anteckning_: Gränssnittet för kategoribehörigheter har omdesignats så att det går att återge ett stort antal behörigheter med hjälp av gränssnittskomponent och sidnumrering som inte ingår i rutan. Tidigare kategoribehörigheter kan få webbläsaren att krascha med ett stort antal behörigheter som tilldelats kategorin.
* _ACP2E-3100_: [Cloud] Bildfilen finns inte i New Relic fellogg
   * _Korrigera anteckning_: Systemet synkroniserar nu anpassade platshållarbilder till lokal lagring så att de återges korrekt när du använder fjärrlagring som AWS S3. Tidigare kunde inte anpassade platshållarbilder återges när fjärrlagring användes, vilket resulterade i en trasig bildvisning och felloggar.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/d1f7dc95>
* _ACP2E-3126_: [Cloud] GQL-svaret för produktmediegalleriet är inte sorterat efter bildposition
   * _Korrigera anteckning_: Systemet sorterar nu objekt korrekt i mediegalleriet efter position i GraphQL-svaret, vilket ger rätt visningsordning. Tidigare sorterades inte objekt i mediegalleriet efter position, vilket ledde till en felaktig visningsordning.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/37671>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/b21e5d91>
* _ACP2E-3136_: [Underkategoriobjekt i molnet] visas inte i widgetredigeringen på administratörens serverdel
   * _Korrigera anteckning_: Kategoriträdet på den nya widgetsidan bör inte längre ha problem med att läsa in kategorierna Nivå 5+. Tidigare saknades vissa kategorier när trädet lästes in efter kategorierna Nivå 5.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/148c3ead>

### Katalog, Framework

* _ACP2E-2949_: [Cloud]Uppföljning: Felmatchning i datajämförelse vid kontroll av om data har ändrats
   * _Korrigera anteckning_: Tidigare anropades objektet save varje gång utan dataändringar (för numeriska datafält, till exempel int/float/double). Den utlöser flaggan _hasDataChanges till true och anropar funktionen save. Den kontrollerar inte heller de flytande talen som är inkapslade med sträng. När den här korrigeringen har tillämpats anropas funktionen spara bara om data har ändrats. Datavärdet för int/float/double check med värdet som skickas till funktionen och utför strikt typmatchning
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/c8931218>

### Katalog, GraphQL

* _ACP2E-3090_: Hantera kategorifilter i GraphQL: includeDirectChildrenOnly och category_uid
   * _Korrigera anteckning_: Endast direkt underordnade kategorier hämtas vid filtrering efter category_uid.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/93d50f8d>
* _ACP2E-3166_: [Cloud] Graphql Product sorting fungerar inte
   * _Korrigera anteckning_: Produktsortering för GraphQl efter flera fält när fälten skickas i variabler fungerar nu som förväntat.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/8459b17d>

### Katalog, priser, mellanlagring och förhandsvisning

* _ACP2E-2672_: [Cloud] API-slutpunkten för specialpris returnerar ett fel när ett stort antal produkter uppdateras samtidigt
   * _Korrigera anteckning_: Nu skapas en kampanj för varje datumintervall i stället för flera schemalagda uppdateringar för varje produkt och datumintervall. Dessutom kommer det att stödja samtidiga API-begäranden för snabbare bearbetning av ett stort antal SKU:er.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/f89a447e>

### Katalog, produkt

* _AC-7050_: Kategorivalsträdet i redigeringsprodukten är inte i samma ordning som i Catalog->Kategorier
   * _Korrigera anteckning_: Systemet visar nu kategorivalsträdet korrekt i produktredigeringsavsnittet i samma ordning som i Katalog->Kategorier, vilket gör produktadministrationen enklare i stora kataloger. Tidigare visades kategoriträdet i produktredigeringsavsnittet i den ordning som kategorin skapades, oavsett visningsordningen i Katalog->Kategorier.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/36101>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/pull/36104>

### Katalog, söka

* _ACP2E-2757_: Produkter som inte visas i kategori och sökning, men direktlänkar fungerar
   * _Korrigera anteckning_: Tidigare fungerade inte attributet Yes/No med price_* attribute_code med indexering. Efter den här korrigeringen fungerar attributet Yes/No som förväntat.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/ba25af8a>
* _ACP2E-3053_: [Cloud] Elastiskt sökfel på vissa kategorisidor
   * _Korrigera anteckning_: Tidigare, med konfigurationsbiljetten angiven, utlöstes ett undantag på gruppkategorisidan när vi sätter priset 0 för flera produkter. När den här korrigeringen har tillämpats när flera produktpriser 0 och vi läser in kategorisidan direkt genereras inga undantag och kategorisidan läses in korrekt.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/c8931218>

### Cloud

* _ACP2E-3010_: [Cloud] PHPSESSID ändrar varje POST-begäran
   * _Korrigera anteckning_: PHPSESSID återskapas inte längre på POST-begäranden i frontend för en inloggad kund om L2 Redis-cache är aktiverad och kunden har uppdaterats från backend-sidan
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/6a185204>

### Innehåll

* _AC-10539_: [Problem] med prisvisningen i widgeten Senast visade
   * _Korrigera anteckning_: Systemet visar nu priset på enkla produkter som inte finns i lager i widgeten &quot;Senast visade produkter&quot;, vilket ger en konsekvent hantering för alla widgetar och produktlistsidor. Tidigare visades inte priset på färdiga enkla produkter i widgeten &quot;Senast visade produkt&quot; på grund av ett villkor i prissättningsmallarna.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/38167>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/pull/38159>
* _AC-10596_: [Problem] Korrigera stavfel och grammatik i filen acl.xsd
   * _Korrigera anteckning_: Systemet rättar nu till ett stavfel och grammatikfel i filen acl.xsd, vilket gör dokumentationen tydligare och exaktare. Tidigare innehöll filen acl.xsd ett stavfel och en felaktig grammatik, vilket skulle kunna orsaka förvirring.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/38061>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/pull/38046>
* _AC-10845_: Banderollbilden för PageBuilder visas inte i galleriet
   * _Korrigera anteckning_: Systemet visar nu banderollbilder som överförts i nyligen skapade mappar i PageBuilder-galleriet korrekt, vilket eliminerar tidigare konsolfel. Före den här korrigeringen var banderollbilderna inte synliga i galleriet om de överfördes till en ny mapp, vilket orsakade ett konsolfel.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/c8f87c25>
* _AC-12283_: &quot;Riktnummer har inte angetts&quot; efter uppdatering till 2.4.5-p8
   * _Korrigera anteckning_: Systemet slutför nu den statiska innehållsdistributionsprocessen när Magento_CSP-modulen är aktiverad och&quot;dev/js/translate_strategy&quot; är inställd på&quot;embedded&quot;, utan att utlösa felet&quot;Area code not set&quot;. Tidigare misslyckades den statiska innehållsdistributionsprocessen under dessa förhållanden med felet&quot;Ingen riktkod har angetts&quot;.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/38845>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/pull/38922>
* _AC-9638_: [Problem med filöverföring] i WYSIWYG-redigeraren på produktsidan
   * _Korrigera anteckning_: Systemet visar nu mappträdet korrekt och tillåter bildöverföringar i WYSIWYG Editor på produktsidan, även efter att fliken Bild och video har expanderats först. När du tidigare expanderade fliken Bild och video visades inte mappträdet och ett felmeddelande visades när en bild skulle överföras i WYSIWYG Editor.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/38026>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/pull/38025>
* _ACP2E-2392_: [On-PREM] Problem med dynamiskt block
   * _Korrigera anteckning_: Wdigets renderas nu korrekt i dynamiska block.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/a12063bd>
* _ACP2E-2606_: YouTube nocookie url fungerar inte i Page Builder
   * _Korrigera anteckning_: Nu tillåter PageBuilder URL för youtube no-cookie i formulärelementinställningarna för verifieringsreglerna. Tidigare fungerar inte youtube no-cookie url i pagebuilder.
* _ACP2E-2693_: [Cloud] Sidslut läses inte in på grund av problem i nyhetsbrevmallen
   * _Korrigera anteckning_: Om du lägger till block via innehållsavsnittet på CMS-sidan leder detta inte längre till något undantag
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/ea79f7dd>
* _ACP2E-2836_: ACP2E-2836: [Cloud] Ett undersökningsundantag hittades i loggen: InvalidArgumentException: Klassen finns inte i vendor/magento/module-rule/Model/ConditionFactory.php
   * _Korrigera anteckning_: Om du tar bort ett villkor i innehållsinställningarna för PageBuilder-produkter registreras inte längre ett undantag i loggfilerna. Om du tidigare tog bort ett villkor i innehållsinställningarna för PageBuilder-produkter skulle ett kritiskt undantag registreras i loggarna, trots att inga problem uppstod i förgrunden.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2-page-builder/commit/36c0f5df>
* _ACP2E-2842_: Växlar till läget för en enskild butik - globalt innehåll visas inte längre
   * _Korrigera anteckning_: Systemet synkroniserar nu designkonfigurationer för butiksvyn med designkonfigurationer för webbplatser när du aktiverar läget för en enskild butik, vilket säkerställer att innehållsuppdateringar visas på klientsidan. Om du växlar till läget för en enskild butik tidigare skulle det förhindra att innehållsuppdateringar återspeglas i butiken.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/7e0e5582>
* _ACP2E-2903_: Page Builder ersätter bilden när du försöker lägga till länkar och andra användbarhetsfel.
   * _Korrigera anteckning_: När du klickar på en bild läses korrekta data in i bildens länkkonfigurationsdialogruta via länkar i Wysiwyg-redigeraren i textelementet i Page Builder. Nu fungerar det också bra att lägga till en länk till en bild i redigeraren. Tidigare ersattes bilden med en länk.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2-page-builder/commit/4d5db10a>
* _ACP2E-2970_: Det gamla mediegalleriet kan inte återge bilder när en bild på 0 byte placeras i katalogen
   * _Korrigera anteckning_: Systemet hanterar nu bilder på 0 byte i mediegalleriet utan att störa funktionaliteten, vilket gör att andra bilder i katalogen kan visas och markeras som förväntat. Tidigare fanns det en bild på 0 byte i mediegalleriet som hindrade alla bilder i katalogen från att visas eller markeras.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/35b1b1da>
* _ACP2E-3064_: Fel i Page Builder vid redigering av CMS Block
   * _Korrigera anteckning_: Systemet sparar nu ändringar som gjorts i administratörsområdet med Page Builder korrekt, utan att utlösa felet&quot;Page Builder återgav i 5 sekunder utan att frigöra lås&quot;. i webbläsarkonsolen. Tidigare inträffade detta fel när ändringar skulle sparas, vilket förhindrar att innehållet uppdateras.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/35b1b1da>, <https://github.com/magento/magento2-page-builder/commit/4d5db10a>
* _ACP2E-3092_: [CLOUD] Inga knappar för utcheckning eller redigering av kundvagn i kundvagnssektionen
   * _Korrigera anteckning_: Paketprodukten läggs nu till i vagnen via widgetar utan fel.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/b21e5d91>, <https://github.com/magento/magento2-page-builder/commit/4ebe3f1d>
* _ACP2E-3113_: Förhandsvisning av innehållsmellanlagring på kategorisidor visar inte produktwidgetar
   * _Korrigera anteckning_: Problemet har åtgärdats genom att produktposter för den ytterligare kategori som är länkad till CMS-blocket har registrerats korrekt i databasen. Tidigare returnerades en tom resultatuppsättning när sidan för kategoriförhandsgranskning begärdes.
* _ACP2E-3127_: imagecreatetruecolor(): Argument #2 ($height) måste vara större än 0. Det går inte att överföra en viss bild
   * _Korrigera anteckning_: Problemet med att bilder med höjden 0 överfördes via mediegalleriet löstes och resurssynkroniseringen slutfördes med synkroniseringskommandot. Tidigare gick det inte att överföra bilden via mediegalleriet och synkroniseringskommandot misslyckas också när en viss bild finns i galleriet.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/6f4805f8>
* _ACP2E-3154_: Prototype.js Array.from i konflikt med Google Maps API
   * _Korrigera anteckning_: Google Maps återges nu korrekt i PageBuilder-redigeraren. Tidigare förhindrade ett Javascript-fel Google Maps från att återges korrekt.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/148c3ead>

### Innehåll, SEO

* _ACP2E-2870_: CMS sidhierarki kan orsaka problem med URL-omskrivning
   * _Korrigera anteckning_: Tidigare, för anpassad permanent URL-omskrivning för icke-webbplatsens rotsidor, omdirigeras oändligt och sidan lästes aldrig in. När den här korrigeringen har tillämpats fungerar den anpassade URL-omskrivningen för rotsidan som inte är webbplats som förväntat och ingen omdirigeringsslinga sker.

### Innehåll, mellanlagring och förhandsvisning

* _ACP2E-2979_: Katalogprisregeln visas inte när den är inställd på att schemalägga med dynamiska block
   * _Korrigera anteckning_: Systemet visar nu korrekt dynamiskt innehåll som är associerat med schemalagda katalogprisregler på produktinformationssidan. Tidigare gick det inte att läsa in dynamiskt innehåll när katalogens prisregler var schemalagda.

### Kund/Kunder

* _AC-12162_: Front end - Det gick inte att validera födelsedatumet på sidan Kund
   * _Korrigera anteckning_: Se till att all validering fungerar efter uppgraderingsövningen.js systemberoende av den senaste delversionen
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/de4dfb8e>

### Ramverk

* _AC-10654_: V1/customers/password endpoint question/issue
   * _Korrigera anteckning_: Systemet följer nu de begränsningar som anges i det hanterings-GUI när begäranden om lösenordsändringar bearbetas via API:t, vilket förhindrar eventuellt missbruk av funktionen för lösenordsåterställning. Tidigare kunde API:t bearbeta begäranden om lösenordsändringar utanför de regler som definierats i det hanterade användargränssnittet, vilket eventuellt skulle möjliggöra en konstant ström av återställda e-postmeddelanden om giltiga e-postmeddelanden var kända.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/38238>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/0c53bbf7>
* _AC-10721_:
   * _Korrigera anteckning_: Uppgradera dispositionsberoende för linje/flygsystem och uppgradera till den senaste versionen
   * _GitHub-problem_: &lt;<https://github.com/magento/magento2/commit/91cb4d46>>
   * _GitHub-kodbidrag_: Uppgradera Composer-beroenden för 2.x-ligan/flygsystemet till senaste version 3.x
* _AC-10838_: Indexeringsprocess för katalogsökindexprocessfel
   * _Korrigera anteckning_: Systemet slutför nu kommandot för omindexering utan att stöta på några fel, oavsett vilken libxml-version som kompilerats med PHP. Tidigare resulterade omindexeringskommandot i ett fel av typen&quot;Katalogsökindexprocessfel under indexeringsprocessen&quot; när PHP kompilerades med vissa versioner av libxml.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/38254>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/pull/38553>, <https://github.com/magento/magento2/commit/0574ac23>
* _AC-10941_: Filtren created_at, status och total_total_total har lagts till i kundorderfrågan och flera filterfel har åtgärdats
   * _Korrigera anteckning_: Systemet stöder nu användningen av filtren created_at, status och total_total i kundorderfrågor och har åtgärdat ett problem där flera filter inte tillämpades korrekt. Tidigare hade systemet inte stöd för dessa filter och kunde inte tillämpa alla filter när mer än ett användes i en fråga.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/38392>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/pull/36949>
* _AC-10971_: https://github.com/magento/magento2/issues/38415
   * _Korrigera anteckning_: PHP 8.2/8.3, endast ett beroende fungerar inte med PHP-pekaren för tillfället: ligan/flygsystemet
   * _GitHub-problem_: &lt;<https://github.com/magento/magento2/commit/672a2e61>>
   * _GitHub-kodbidrag_: Systemet har nu stöd för PHP 8.2/8.3 genom att uppdatera paketet leag/flysystem till version 3.0.20, vilket säkerställer att inga PHP-lintingfel inträffar. Tidigare orsakade PHP-filer som kördes via PHP-pekaren med PHP 8.3 lintingfel i paketet för ligan/flygsystemet.
* _AC-10991_: Slumpmässigt översvämmas av frågor från relaterade block/merförsäljning/korsförsäljning och prisindexering
   * _Korrigera anteckning_: Systemet optimerar nu frågor från relaterade block, merförsäljning och korsförsäljning, vilket förbättrar prestanda och förhindrar att webbplatsen kraschar på grund av för många frågor. Tidigare kunde systemet bli överbelastat med frågor från de här blocken, vilket gjorde att det gick betydligt långsammare och kunde göra att webbplatsen inte fungerade som den skulle.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/36667>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/pull/38050>
* _AC-11388_:
   * _Korrigera anteckning_: Verifiera borttagning av mapp tar bort S3 och lokala fillagringskataloger
* _AC-11423_: Undantag: Varning! Försöker få åtkomst till matrisförskjutning i.. -> Calendar.php sedan uppgradering till ICU 74.1 (PHP Intl)
   * _Korrigera anteckning_: Commerce loggar inte längre följande undantag i exception.log när en köpare eller handlare besöker antingen butiken eller administratören: `main.CRITICAL: Exception: Warning: Trying to access array offset on value of type null in /vendor/magento/framework/View/Element/Html/Calendar.php on line 114 in /vendor/magento/framework/App/ErrorHandler.php:62`. [GitHub-38214](https://github.com/magento/magento2/issues/38214)
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/38214>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/pull/38364>
* _AC-11476_: [Problem] Åtgärda problem med kunddata när formuläret innehåller element med namnet `method`
   * _Korrigera anteckning_: Systemet identifierar nu korrekt attributet method i formuläröverföringar, även när det finns ett element med namnet method i formuläret. Detta säkerställer korrekt behandling av kunddata. Tidigare, om ett formulärelement hette &#39;method&#39;, skulle det störa identifieringen av &#39;method&#39;-attributet i formulärskickningar, vilket skulle kunna orsaka problem med kunddatahanteringen.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/38484>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/pull/38449>
* _AC-11489_: [Problem] Korrigera PHPDocs för \Magento\Framework\Data\Collection::getItemById
   * _Korrigera anteckning_: PHPDocs för metoden \Magento\Framework\Data\Collection::getItemById har uppdaterats så att null inkluderas som en möjlig returtyp, vilket åtgärdar problem med statiska analysverktyg. Tidigare specificerade metodens PHPDocs inte null som en möjlig returtyp, vilket ledde till varningar eller fel i den statiska analysen när metoden användes i villkorssatser.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/38485>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/pull/38439>
* _AC-11651_: Magento försöker ändra den skrivskyddade egenskapen i __wakeup-metoden för LoggerProxy
   * _Korrigera anteckning_: Systemet tillåter nu att tidigare skrivskyddade egenskaper ändras i LoggerProxyns __wakeup-metod, vilket ger en smidig funktion utan att användarna tvingas använda en lösning. Tidigare uppstod problem om du försökte tilldela om värdet för en skrivskyddad egenskap i LoggerProxyns __wakeup-metod.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/38526>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/c8f87c25>
* _AC-11673_:
   * _Korrigera anteckning_: Undersök de senaste versionerna av php-amqplib/php-amqplib
   * _GitHub-problem_: &lt;<https://github.com/magento/magento2/commit/de4dfb8e>>
   * _GitHub-kodbidrag_: Uppdaterat den senaste versionen av php-amqplib/php-amqplib :^3.x
* _AC-11681_: [Issue] AC-2039 AC-1667 upgrade TinyMCE references
   * _Korrigera anteckning_: Uppdaterad timer av den senaste versionen i Composer.json
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/38533>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/pull/36543>, <https://github.com/magento/magento2/commit/b34c0a75>
* _AC-11696_: ChangelogBatchWalker fungerar inte i flera trådar
   * _Korrigera anteckning_: Systemet har nu stöd för processförgreningar för MView-indexering, vilket förhindrar fel under indexeringskörning vid arbete på flera trådar. Tidigare ledde en körning av ChangelogBatchWalker på flera trådar till att tabeller som används av andra trådar togs bort, vilket orsakade ett fel under körningen av indexeraren.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/38246>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/pull/38248>
* _AC-11781_: [Problem] Byt namn på variabeln med fel namn
   * _Korrigera anteckning_: Systemet namnger nu variabeln som innehåller den summa pengar som fortfarande kan återbetalas, vilket förhindrar förvirring under felsökning. Tidigare hade variabeln felaktigt fått namnet totalRefund, vilket kunde leda till missförstånd för utvecklare.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/38609>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/pull/36205>
* _AC-11808_:
   * _Korrigera anteckning_: Aktivera och uppgradera listan över Adobe Commerce Core-beroenden
   * _GitHub-kodbidrag_: Adobe Commerce Core-beroendelista måste uppgraderas 
* _AC-11819_: Inbyggt FPC-cacheminne har brutits i 2.4.7 för vissa konfigurationer
   * _Korrigera anteckning_: Systemet cachelagrar nu sidor korrekt när parametern MAGE_RUN_CODE har angetts, vilket ger optimala prestanda. Tidigare cachelagrades inte sidor under dessa förhållanden, vilket ledde till potentiella prestandaproblem.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/38626>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/pull/38646>, <https://github.com/magento/magento2/commit/0c53bbf7>
* _AC-11829_: [Problem] Korrigera inkonsekvent hantering av undantag mellan utvecklare och produktionslägen
   * _Korrigera anteckning_: Systemet hanterar nu konsekvent undantag mellan utvecklare och produktionsläge, vilket förhindrar oväntad omdirigering till inloggningssidan när ett undantag inträffar. Tidigare kunde en inkonsekvens i undantagshanteringen leda till en omdirigering till inloggningssidan i produktionsläge i stället för att visa undantagsmeddelandet.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/38639>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/pull/37712>
* _AC-11852_: Ersätt översättning av PayPal-konto i token_list.phtml
   * _Korrigera anteckning_: Systemet etiketterar nu avsnittet för tokenanvändbara kontobetalningsmetoder som &quot;Konto&quot; i stället för &quot;PayPal-konto&quot; på sidan Lagrade betalningsmetoder, vilket gör det mer representativt för funktionen. Tidigare hette det här avsnittet särskilt&quot;PayPal Account&quot;, vilket var vilseledande när andra tokenliknande betalningsmetoder lades till.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/35622>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/pull/37959>
* _AC-11874_: Bakåtkompatibiliteten har förlorats i klassen Magento\Catalog\Model\ProductRepository
   * _Korrigera anteckning_: Klassen ProductRepository behåller nu bakåtkompatibilitet genom att återställa klassen Initialization Helper som den andra parametern, vilket säkerställer att moduler som utökas från den här klassen fungerar som förväntat. Tidigare ledde borttagningen av initieringshjälpen från konstruktorn i klassen ProductRepository till att bakåtkompatibiliteten gick förlorad, vilket tvingade användarna att använda en lösning.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/38669>
* _AC-11905_: [Problem] vid distribution av statiskt innehåll - typfel
   * _Korrigera anteckning_: Systemet hanterar nu tomma LESS-filer korrekt under distributionen av statiskt innehåll och visar felmeddelandet&quot;LESS-filen är tom&quot;. Tidigare uppstod ett felaktigt typfel när en tom LESS-fil påträffades under distributionen.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/38682>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/pull/38683>
* _AC-11911_:
   * _Korrigera anteckning_: Rensning av jQuery/fileuploader-css efter migrering till uppy-biblioteket
   * _GitHub-problem_: &lt;<https://github.com/magento/magento2/commit/7cabfb46>>
   * _GitHub-kodbidrag_: jQuery/fileUploader-biblioteket har tagits bort eftersom det har migrerats till Uppy-biblioteket
* _AC-12002_: [Problem] [Visa] Extra utrymme i länk- och skripttagg har tagits bort
   * _Korrigera anteckning_: Systemet ser nu till att det inte finns några extra blanksteg i länk- och skripttaggarna, vilket ger en renare och mer effektiv kod. Tidigare gick det att hitta dubbla mellanslag mellan attribut i link- och script-taggarna.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/32920>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/pull/32919>
* _AC-12015_:
   * _Korrigera anteckning_: ExtJs-mapprensning efter migrering till jsTree-biblioteket
   * _GitHub-problem_: &lt;<https://github.com/magento/magento2/commit/7cabfb46>>
   * _GitHub-kodbidrag_: TextJs-mappen togs bort eftersom den relaterade funktionen har migrerats till jsTree
* _AC-12022_:
   * _Korrigera anteckning_: Uppgradera systemberoende för monolog/monolog till den senaste större versionen
   * _GitHub-problem_: &lt;<https://github.com/magento/magento2/commit/edcd0dcc>>
   * _GitHub-kodbidrag_: Systemet har uppdaterats för att använda den senaste större versionen av biblioteket &quot;monolog/monolog:^3.x&quot;, vilket garanterar kompatibilitet och förbättrade prestanda. Tidigare använde systemet en föråldrad version av &quot;monolog/monolog&quot;-biblioteket som kunde ha orsakat potentiella problem och begränsningar.
* _AC-12023_:
   * _Korrigera anteckning_: Uppgradera wikimedia/less.php till den senaste större versionen
   * _GitHub-problem_: &lt;<https://github.com/magento/magento2/commit/edcd0dcc>>
   * _GitHub-kodbidrag_: Systemet har uppdaterats för att använda den senaste större versionen, 5.x, av biblioteket wikimedia/less.php, vilket garanterar kompatibilitet och aktuella funktioner. Tidigare använde systemet en inaktuell version av biblioteket som kunde ha orsakat säkerhetsproblem.
* _AC-12024_:
   * _Korrigera anteckning_: Uppgradera jQuery/validera biblioteksberoendet till den senaste delversionen
   * _GitHub-problem_: &lt;<https://github.com/magento/magento2/commit/de4dfb8e>>
   * _GitHub-kodbidrag_: Uppgradera jQuery/validera biblioteksberoende till den senaste delversionen, 1.20.0
* _AC-12025_:
   * _Korrigera anteckning_: Systemberoende för uppgradering av stund.js till den senaste mindre versionen
   * _GitHub-problem_: &lt;<https://github.com/magento/magento2/commit/de4dfb8e>>
   * _GitHub-kodbidrag_: Systemberoende för uppgradering av stund.js till den senaste mindre versionen, 2.30.1
* _AC-12267_:
   * _Korrigera anteckning_: Stöd för anslutningsförsök för Redis-sessioner och kompatibelt med colinvåra/php-redis-session-abstract v2.0.0
   * _GitHub-problem_: &lt;<https://github.com/magento/magento2/commit/672a2e61>>
   * _GitHub-kodbidrag_: Uppdaterad version av colinblöenhour/php-redis-session-abstract v2.0.0 som är kompatibel med Adobe commerce
* _AC-12268_:
   * _Korrigera anteckning_: Uppgradera dispositionsberoenden för gänge/flygsystem till den senaste versionen
   * _GitHub-kodbidrag_: Uppgradera Composer-beroenden för 2.x-ligan/flygsystemet till senaste version 3.x
* _AC-12594_: [Problem] Använd kompilerad konfiguration för genererade data i stället för allmän konfiguration
   * _Korrigera anteckning_: Systemet använder nu den kompilerade konfigurationen för genererade data i stället för den allmänna konfigurationen, vilket minskar nätverksöverföringen och belastningen på data som är beroende av en viss version av koden. Den här ändringen förhindrar åsidosättning av cache i delade instanser under behållarbyte, vilket leder till förbättrad stabilitet och minskad drifttid. Tidigare använde vissa huvudklasser en delad config-typ, vilket kan leda till att cache-lagring åsidosätts eller att programmet blir driftsavbrott på grund av skillnader i kodversioner mellan flera servrar.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/38785>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/pull/29954>
* _AC-12597_: [Problem] Ta bort referenser till filer från filer som har tagits bort i e1ccdb..
   * _Korrigera anteckning_: Systemet tar nu bort referenser till filer från tidigare borttagna filer, vilket eliminerar fel i webbläsarens konsol och systemloggfilen. Tidigare orsakade dessa referenser fel på grund av att det inte fanns några refererade filer.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/38960>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/pull/38951>
* _AC-12715_:
   * _Korrigera anteckning_: Uppdatera beroenden för laminas-dispositionsverktyget genom att uppgradera till den senaste versionen
   * _GitHub-problem_: &lt;<https://github.com/magento/magento2/commit/b34c0a75>>
   * _GitHub-kodbidrag_: Systemet har nu stöd för de senaste versionerna av beroenden för laminas Composer:
laminas/laminas-servicemanager
laminas/laminas-server
laminas/laminas-stdlib
laminas/laminas-validator
säkerställa kompatibilitet och aktuell funktionalitet. Tidigare kunde uppdatering till de senaste versionerna av dessa beroenden orsaka bakåtkompatibilitetsproblem och testfel.
* _AC-12750_:
   * _Korrigera anteckning_: Borttagningen av ExtJs loggar fel i webbläsarkonsolloggen och magentaloggen
* _AC-12778_: [Utgåva] Mindre rensning: korrigerad felaktig användning av sprintf, tar bara två platshållare här och w..
   * _Korrigera anteckning_: Systemet använder nu sprintf-funktionen korrekt med rätt antal platshållare, vilket förbättrar renheten och konsekvensen i koden. Tidigare användes sprintf-funktionen felaktigt med ett extra argument, som inte orsakade några större problem men som inte var korrekt.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/39062>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/pull/38628>
* _AC-12823_:
   * _Korrigera anteckning_: Undersök enhetstestfelet på grund av att korrigeringsfilen har ändrats i ett steg under komponentuppgraderingen
   * _GitHub-problem_: &lt;<https://github.com/magento/magento2/commit/b34c0a75>>
* _AC-12866_:
   * _Korrigera anteckning_: Ta bort borttagningar - Integrationstester för PhpUnit10
   * _GitHub-problem_: &lt;<https://github.com/magento/magento2/commit/edcd0dcc>>
   * _GitHub-kodbidrag_: Korrigera PHPUnit-borttagningar
* _AC-12868_:
   * _Korrigera anteckning_: Ta bort borttagningar - PhpUnit10 WebAPI-tester
   * _GitHub-problem_: &lt;<https://github.com/magento/magento2/commit/edcd0dcc>>
   * _GitHub-kodbidrag_: Korrigera PHPUnit-borttagningar
* _AC-12869_: [Problem] Korrigerar felaktiga klasser som refereras i Magento-moduler.
   * _Korrigera anteckning_: Systemet refererar nu klasser i moduler korrekt, vilket ger en smidigare åtgärd och förhindrar krascher på grund av klasser som inte finns. Detta inkluderar en bugfix i indexer- och Creditmemo-modulerna och implementeringen av HttpGetActionInterface i klassen PrintAction. Tidigare ledde felaktiga klassreferenser till fel och potentiella systemkrascher, och vissa funktioner, som t.ex. filnamnet för kreditnota PDF-filer och omindexering av lager, fungerade inte som förväntat.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/39126>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/pull/37784>
* _AC-12882_:
   * _Korrigera anteckning_: Undersök integreringsbygget efter komponentuppgradering
   * _GitHub-problem_: &lt;<https://github.com/magento/magento2/commit/b34c0a75>>
* _AC-6754_: typfel i en js-fil.
   * _Korrigera anteckning_: Systemet använder nu termen &quot;prenumeranter&quot; i JavaScript-filen korrekt, vilket garanterar att de relaterade funktionerna fungerar som de ska. Tidigare har ett typografiskt fel i JavaScript-filen resulterat i felaktig användning av termen &quot;subsctibers&quot;.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/36163>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/pull/36171>
* _AC-8089_:
   * _Korrigera anteckning_: Undersök dispositionsberoenden för gänget/flygsystemet som uppgraderar till den senaste versionen
* _AC-8353_: [Issue] Ta bort förbjuden `@author` tagg
   * _Korrigera anteckning_: Systemet följer nu kodningsstandarder genom att ta bort den förbjudna `@author` -taggen från vissa moduler, vilket ger en renare och mer standardiserad kod. Tidigare fanns taggen `@author` i vissa moduler, vilket stred mot de etablerade kodningsstandarderna.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/37253>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/pull/37003>
* _AC-8356_: [Problem] Ta bort ej tillåten `@author` tagg från `Magento_Customer` (del 2)
   * _Korrigera anteckning_: Systemet följer nu kodningsstandarden genom att ta bort den förbjudna `@author` -taggen från vissa moduler, vilket ger en renare och mer standardiserad kod. Tidigare fanns taggen `@author` i vissa moduler, vilket stred mot de etablerade kodningsstandarderna.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/37250>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/pull/37000>
* _AC-8659_: Utrymme i syntaxbrytningsregel för redigerarconfig för [{disposition,auth}.json]
   * _Korrigera anteckning_: Systemet tillämpar nu korrekt ett indrag med 4 blanksteg på filerna Composer och auth.json, efter en korrigering av ett syntaxfel i EditorConfig. Tidigare formaterades dessa filer felaktigt med ett indrag med två blanksteg på grund av ett blanksteg i editorconfig-syntaxen.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/37394>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/pull/37395>
* _AC-8984_: [Issue] Lägger till fler färger i utdata för vissa kommandon för att konfigurera kli
   * _Korrigera anteckning_: Systemet lägger nu till fler färger i utdata från vissa kommandon i kommandoradsgränssnittet (CLI), vilket förbättrar läsbarheten och användarupplevelsen. Tidigare var utdata från kommandona svårare att läsa på grund av bristande färgdifferentiering.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/29335>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/pull/29298>
* _AC-9630_: Uppgradering av Magento återställer general/region/state_required när ett nytt land med obligatoriskt tillstånd/region läggs till.
   * _Korrigera anteckning_: Systemet lägger nu bara till det ändrade landet i konfigurationen &quot;general/region/state_required&quot; när ett nytt land med obligatoriska lägen läggs till, vilket förhindrar eventuella avbrott i den anpassade koden som förutsätter att regionen är inaktiverad. Om du tidigare lade till ett nytt land med obligatoriska lägen återställs konfigurationen General/region/state_required till standardländer med ett obligatoriskt tillstånd, vilket kan göra att affären bryts.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/37796>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/pull/38076>
* _AC-9712_: Skillnad i mindre kompilering mellan php- och nodatumbibliotek (grunt) med komplicerade `calc`-uttryck
   * _Korrigera anteckning_: Korrigera skillnaden i mindre kompilering mellan php- och nodejs-biblioteket (grunt) efter uppdatering wikimedia/less.php:^5.x
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/37841>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/b34c0a75>
* _ACP2E-2692_: Felet &quot;Bastabellen eller vyn hittades inte&quot; inträffar när partiell indexering körs
   * _Korrigera anteckning_: Partiell omindexering fungerar nu korrekt med stor ändringslogg vid sekundär databasanslutning
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/ba25af8a>
* _ACP2E-2844_: Problem efter uppgradering av MariaDB till 10.5.1 eller senare
   * _Åtgärdade felet_ när datetime-värden i en DB skulle konverteras till 0000-00 00:00:00 efter Mysql-uppgradering
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/a12063bd>
* _ACP2E-2855_: Typmatchningsfel i datajämförelse vid kontroll av om data har ändrats
   * _Korrigera anteckning_: Tidigare anropades objektet save varje gång utan dataändringar (för numeriska datafält, till exempel int/float/double). Den utlöser flaggan _hasDataChanges till true och anropar funktionen save. När den här korrigeringen har tillämpats anropas funktionen spara bara om data har ändrats. Datavärdet för int/float/double-check med värdet som skickas till funktionen och utför strikt typmatchning.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/57a32313>
* _ACP2E-2959_: [Det går inte att använda molnimport] med katalogen var
   * _Korrigera anteckning_: Det går att importera produkten oavsett filnamn.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/3a7c4d17>
* _ACP2E-2966_: I iPad mini läses meny och header in som mobila, i stället läses de in som skrivbord.
   * _Korrigera anteckning_: Systemet hanterar nu enheter med en bredd på 768 px som stationära datorer, vilket säkerställer att meny och rubrik läses in korrekt. Tidigare behandlades enheter med bredden 768 px som mobila enheter, vilket gjorde att menyn och huvudet lästes in i en mobilvy.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/35b1b1da>, <https://github.com/magento/magento2-page-builder/commit/4d5db10a>
* _ACP2E-3046_: Det gick inte att hitta ett fel i bastabellen eller vyn när mview-objektet kördes när en DDL-åtgärd utfördes
   * _Korrigera anteckning_: Systemet hanterar nu databasuppdateringsåtgärder korrekt medan mview-uppdateringen körs i bakgrunden, vilket förhindrar förekomsten av fel i bastabellen eller vyn som inte hittades. Tidigare kunde en del databasuppdateringsåtgärder resultera i felet &quot;Bastabell eller vy hittades inte&quot; om mview-uppdateringen kördes samtidigt.

### Framework, GraphQL

* _AC-7976_: [Issue] Stöd för anpassade skalära typer för GraphQL-schema introducerades
   * _Korrigera anteckning_: Systemet har nu stöd för anpassade skalära typer för GraphQL-schema, vilket gör att utvecklare kan definiera anpassade skalära typer och implementeringar. Den här funktionen kan vara särskilt användbar för att uttrycka värden som kan behöva valideras, t.ex. HTML, e-post, URL:er, datum och mer avancerade fall som EAV-attribut. Tidigare hade systemet inte stöd för bearbetning av anpassade skalära typer i GraphQL.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/36877>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/pull/34651>, <https://github.com/magento/magento2/commit/0574ac23>

### Framework, Product

* _AC-13011_: 2.4.8-beta1 EE-rapporter genereras inte på grund av ett magento-undantag

### GraphQL

* _AC-11729_: Magento_GraphQl kör rubriker även om rubrikvärdet inte godkänns i valideringen
   * _Korrigera anteckning_: Systemet ser nu till att huvudbearbetningen bara körs en gång och bara om huvudvärdet godkänns i valideringen, förbättrar säkerheten och förhindrar potentiella sårbarheter. Tidigare utfördes rubrikbearbetning även om rubrikvärdet inte godkändes vid valideringen, vilket ledde till potentiella sårbarheter och oväntade beteenden på grund av dubbelbearbetning av rubrikvärden.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/c8f87c25>
* _AC-8951_: Alternativen för fysiskt Giftcard har inte rätt sorteringsordning
   * _Korrigera anteckning_: Systemet sorterar nu alternativen för fysiska presentkortsprodukter korrekt när de efterfrågas via GraphQL, vilket ger en konsekvent återgivning med Luma-temat. Tidigare var sorteringsordningen felaktig enligt lumatema, vilket ledde till felaktig visning och ordning av alternativ som avsändarnamn, mottagarnamn och belopp.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/1bafc571>
* _AC-9157_: [GraphQL]-matchningscachen är ogiltig när en mellanlagringsuppdatering skapas/redigeras/flyttas/tas bort
   * _Korrigera anteckning_: Systemet ser nu till att matchningscachen inte blir ogiltig när en mellanlagringsuppdatering skapas, redigeras, flyttas eller tas bort, utan endast när mellanlagringsuppdateringen tillämpas på entiteten. Tidigare ogiltigförklarades cacheminnet för lösaren i förtid, till och med innan mellanlagringsuppdateringen tillämpades, vilket ledde till onödiga cacheminnen.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/0c53bbf7>
* _ACP2E-2642_: Snabb cachelagring har inte rensats för uppdatering av innehållsmellanlagring
   * _Korrigera anteckning_: Nu är svarscachen för GraphQL med PageBuilder-innehåll ogiltig när innehållsrelaterade entiteter för PageBuilder uppdateras.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/ba25af8a>
* _ACP2E-2653_: Inaktiverar navigering i lager - tar inte bort aggregering från Graphql
   * _Korrigera anteckning_: Problemet har åtgärdats efter att kontrollen har tillämpats när en produktsökning med kategoriaggregeringar begärdes via en GraphQL-fråga när administratörskonfigurationsinställningen &quot;Katalog > Lagrad navigering > Visningskategorifilter&quot; har angetts.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/12e071c3>
* _ACP2E-2928_: GraphQL Products-anropet som innehåller prisfiltret {från:&quot;0&quot;} returnerar inget resultat
   * _Korrigera anteckning_: Tidigare sökning med grafikprocessorer med filter för nollpriser returnerade inga resultat alls på grund av ett utlöst undantag. Nu returnerar sökningen det förväntade resultatet.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/c971859e>
* _ACP2E-3128_: [Cloud] Avbrutet GraphQL-anrop för getPurchaseOrder med nodcitat
   * _Korrigera anteckning_: GraphQL-anropet för inköpsorder kan utföra uppgiften utan att några interna serverfel påträffas.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/6f4805f8>
* _ACP2E-3184_: [Konfigurerbara produkter i molnet] visas inte på produktionsplatsen om Produkten inte är aktiverad i Alla butiksvyer
   * _Korrigera anteckning_: Systemet visar nu konfigurerbara produkter på webbplatsen korrekt, även om produkten inte har aktiverats i Alla butiksvyer, men har aktiverats i specifika butiksvyområden.
Om en produkt tidigare var inaktiverad i&quot;Alla butiksvyer&quot; och endast aktiverad i specifika butiksvyområden, skulle produktattributen inte visas korrekt i GraphQL-svaret, vilket leder till att produkten inte visas korrekt.
   * _GitHub-kodbidrag_: <https://github.com/magento/inventory/commit/3f300077>
* _ACP2E-3190_: [Cloud] Produktgrafik har fel när samma enkla produkt har tilldelats flera konfigurerbara produkter
   * _Korrigera anteckning_: Tidigare, med olika konfigurerbara produkter med samma enkla produkt, returnerade grapQL ett fel. När den här korrigeringen har tillämpats returnerar grapQL resultat utan fel för olika konfigurerbara produkter med samma enkla produkt.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/148c3ead>
* _ACP2E-3253_: GraphQL cart itemsV2 pagination fungerar inte korrekt
   * _Åtgärda anteckning_: Problemet har åtgärdats genom att rätt värde för det aktuella sidargumentet har skickats i samlingsfrågan. Tidigare skickades fel värde för att ställa in den aktuella sidan, vilket orsakade problemet.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/8459b17d>

### GraphQL, Inventory / MSI

* _ACP2E-2607_: MergeCart-mutation genererar undantag när käll- och målvagnen har samma paketobjekt
   * _Korrigera anteckning_: -
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/c971859e>, <https://github.com/magento/inventory/commit/db0620da>

### GraphQL, Inventory/MSI, Performance

* _ACP2E-1716_: Platsen stängs efter uppgradering
   * _Korrigera anteckning_: Prestandan för hämtning av paketprodukter via GraphQl har förbättrats.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/ba25af8a>, <https://github.com/magento/inventory/commit/bdbf97ea>

### GraphQL, prestanda

* _AC-9569_: [GraphQL Resolver] Kundlösningsdata har inte verifierats från import
   * _Korrigera anteckning_: GraphQL kundmatchningscache ogiltigförklaras nu som förväntat när en kund redigeras eller tas bort via import. Tidigare var cachen inte ogiltig och kunddata kunde redigeras eller tas bort under importen.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/0574ac23>

### GraphQL, sökning

* _ACP2E-2809_: Det går inte att sortera GraphQL produktlista efter flera parametrar
   * _Korrigera anteckning_: Produktsortering efter flera fält i GraphQl fungerar nu enligt beskrivningen i dokumentationen
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/c971859e>

### Importera/exportera

* _AC-12172_: Problem vid produktimport när den tillhandahålls med en fil av typen anpassad options (den skapade produkten innehåller inte pris för anpassade alternativ och visar bara det första filtypstillägget som anges)
   * _Korrigera anteckning_: Systemet importerar nu produktdata korrekt med anpassade alternativ av typen &#39;file&#39;, vilket säkerställer att alla angivna filtillägg visas och att priset för det anpassade alternativet inkluderas. Tidigare visades bara det första tillägget under produktimporten om ett anpassat alternativ av typen &#39;file&#39; hade fler än ett filtillägg, och priset för det anpassade alternativet saknades.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/38805>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/pull/38926>
* _ACP2E-2710_: Felaktig körningstid för importåtgärd i rutnätet för importhistorik
   * _Korrigera anteckning_: Körningstiden för importrapporten visas korrekt oberoende av administratörens nationella inställningar.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/ea79f7dd>
* _ACP2E-2737_: Duplicera kunder som skapas med samma e-postadress med hjälp av import
   * _Korrigera anteckning_: Importerar kunden när kontodelningen är inställd på Global, importerad kund som finns i systemet uppdateras.
Tidigare importerad kund duplicerades.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/c971859e>
* _ACP2E-2902_: Lägg till/uppdatera import för produkter som duplicerar anpassningsbara alternativ
   * _Korrigera anteckning_: Problemet har åtgärdats genom att rätt butik har tilldelats produktalternativ under CSV-import av produktalternativ.
Tidigare tilldelades till administratörsarkivet i stället för deras respektive butik.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/3a7c4d17>
* _ACP2E-2990_: Kundens &quot;created_at&quot;-datum har inte konverterats för att lagra tidszonen vid export
   * _Korrigera anteckning_: Ett datumvärde för kolumnen &#39;created_at&#39; konverteras till rätt datumformat baserat på butikstidszonen i CSV-avsnittet för kundexport.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/3056e9cb>
* _ACP2E-3165_: [Cloud] Hämtar fel vid kontroll av data i importdata med CSV
   * _Korrigera anteckning_: Det finns inget fel när data kontrolleras vid CSV-import. Tidigare visades felmeddelandet:&quot;Vi kan inte hitta en kund som matchar den här e-postadressen och webbplatskoden i rad(er): 1&quot; när data kontrolleras i importavsnittet med CSV från administratören.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/8459b17d>

### Installera och administrera

* _ACP2E-2102_: Ingen VCL för export för lack 7-knapp på administratörspanelen
   * _Korrigera anteckning_: Knappen Exportera VCL för lack 7 har lagts till på panelen Admin.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/a4fbf702>

### Lager/MSI

* _AC-10750_: Lageruppdateringen av den konfigurerbara produkten misslyckas när databasen använder prefix
   * _Korrigera anteckning_: Systemet uppdaterar nu lagret för konfigurerbara produkter korrekt när prefix används i databasen, vilket förhindrar felmeddelanden och säkerställer att rätt kvantitet sparas. Tidigare uppstod ett fel när lagerkvantiteten för enkla produkter i en konfigurerbar produkt skulle sparas om databasen använde prefix.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/38045>
* _AC-11593_: Google Google API-nyckel fungerar inte när en karta med attribut läggs till
   * _Korrigera anteckning_: Systemet har nu stöd för den senaste Google Maps API-versionen, 3.56, vilket gör att användare kan lägga till ett kartinnehållsblock från PageBuilder-menyn på scenen utan att några fel påträffas. Tidigare kunde användare inte lägga till ett kartinnehållsblock på grund av kompatibilitetsproblem med Google Maps API-versionen, vilket resulterade i ett felmeddelande om att något gick fel.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/0574ac23>
* _ACP2E-1411_: [Testa] Paketprodukter med 0 lager vid lagerframsidan
   * _Korrigera anteckning_: Paketprodukten visas inte på ytterligare webbplatser som använder extra lager.
* _ACP2E-2794_: [Cloud] Kritiskt problem med produktlistor med tomma utrymmen
   * _Korrigera anteckning_: Systemet visar nu produktlistor korrekt utan tomma utrymmen när produkter anges till Out of Stock, vilket ger en konsekvent och korrekt visning av tillgängliga produkter. Om du tidigare angav en produkt som &quot;Out of Stock&quot; skulle det resultera i att ett tomt utrymme visas i produktlistan, vilket stör layouten och kan förvirra kunderna.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/ea79f7dd>, <https://github.com/magento/inventory/commit/b59e48ca>

### Beställning

* _AC-10828_: Skärm med översikt över backend-order: Kvantitet som inte är synlig på orderartikelnivå
   * _Korrigera anteckning_: Systemet visar nu antalet underordnade objekt i kolumnen quantity på översiktsskärmen för backend-order. Detta gör att användarna kan spåra status för alla objekt i en ordning på rätt sätt. Tidigare visade kolumnen för kvantitet endast antalet artiklar som beställts, fakturerats och levererats, men inte antalet beställda artiklar.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/38252>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/pull/38320>
* _AC-10994_: [Problem] Fel lagrings-ID används i orderadressrenderaren
   * _Korrigera anteckning_: Systemet använder nu korrekt det arkiv-ID som är kopplat till en order när orderadressen återges, vilket säkerställer att adresserna formateras korrekt enligt deras respektive butik-ID. Tidigare använde systemet felaktigt det aktuella butiks-ID:t, vilket kunde leda till felaktig adressformatering om flera beställningsmejl från olika butiker behövde skickas.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/38412>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/pull/37932>
* _AC-11798_: [Utleverans] Leveranspriset skiljer sig åt i utskriven PDF
   * _Korrigera anteckning_: Systemet visar nu leveranspriserna korrekt i utskrivna PDF-filer enligt momskonfigurationsinställningarna, vilket säkerställer konsekvens mellan försäljningsorderfakturavyn och den utskrivna fakturan. Tidigare undantogs moms för det fraktpris som visades i den utskrivna PDF, oavsett momskonfigurationsinställningar.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/38608>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/pull/38595>, <https://github.com/magento/magento2/commit/1bafc571>
* _ACP2E-2622_: Det går inte att spara ändringar i telefonnummer i befintlig orderinformation
   * _Åtgärda anteckning_: Nu kan användaren lägga till det internationella prefixet 00 i telefonfältet för orderadress
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/38201>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/12e071c3>
* _ACP2E-2734_: E-postmeddelanden kan inte skickas
   * _Korrigera anteckning_: Systemet innehåller nu ett konfigurationsalternativ för async_sending_try för att ange antalet försök att skicka ett e-postmeddelande innan det stoppas, vilket förbättrar hanteringen av misslyckade e-postmeddelanden när asynkron sändning är aktiverat. Tidigare, om ett e-postmeddelande inte kunde skickas, skulle systemet kontinuerligt försöka skicka om det, vilket resulterar i en oändlig loop med felmeddelanden i systemloggen.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/b2286ecf>
* _ACP2E-2756_: [Cloud] Beställningsstatus ändrad till Fullständigt när delvis återbetalning av en delvis levererad order har gjorts
   * _Korrigera anteckning_: När du utfärdar en kreditnota ändras orderstatusen inte längre till&quot;slutförd&quot; om det finns artiklar som ännu inte har skickats.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/7e0e5582>
* _ACP2E-3002_: [CLOUD] Det går inte att inaktivera Skicka e-post från Admin UI som Dev Docs visar
   * _Korrigera anteckning_: Systemet förhindrar nu att e-postmeddelanden skickas korrekt när e-postkommunikation är inaktiverad. Dessa e-postmeddelanden skickas inte längre när e-postkommunikation har återaktiverats. Tidigare skickades säljmeddelanden som initierats medan e-postkommunikation inaktiverades när e-postkommunikation återaktiverades.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/c8931218>
* _ACP2E-3045_: Beställningen har stängts utan att återbetalas helt
   * _Korrigera anteckning_: Systemet behåller nu orderstatusen korrekt som Bearbetning och fakturastatusen som Väntande när en order med en ej infångad betalning har en leverans skapad. Detta garanterar att beställningar endast markeras som&quot;Stängda&quot; efter att de har återbetalats helt. Om du tidigare skapade en leverans för en order med en väntande faktura skulle orderstatusen felaktigt ändras till Stängd.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/6a185204>

### Order, returer

* _ACP2E-2982_: Orderåterbetalning resulterar i dubblettkreditnota
   * _Korrigera anteckning_: Om återbetalningen skickas via REST API när två identiska förfrågningar utfördes samtidigt skapas inte längre dubbla kreditnotor.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/a4fbf702>

### Order, skatt

* _ACP2E-3003_: [CLOUD] Felaktig base_row_total i RESTFUL order API när gränsöverskridande transaktioner aktiveras och kupongrabatter tillämpas
   * _Korrigera anteckning_: Nu returneras korrekt base_row_total från RESTFUL-order-API när gränsöverskridande transaktioner är aktiverade och kupongrabatt tillämpas.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/9af794a4>

### Övriga

* _LYNX-339_: cookien private_content_version returnerades i GQL-frågor
* _LYNX-366_: Serverfel för e-postproppar i fysiska presentkortsfrågor
* _LYNX-380_: attributet is_available i CartItemInterface returnerar alltid false för konfigurerbara produkter
* _LYNX-382_: attributet is_available i CartItemInterface returnerar true även när det säljbara lagret är mindre än produktkvantiteten
* _LYNX-395_: attributet only_x_left_in_stock i ProductInterface är inte korrekt för konfigurerbara produkter
* _LYNX-399_: Platshållarminiatyrbilder returneras när en enkel produkt läggs till i varukorgen i en grupperad produkt
* _LYNX-400_: Kundens anpassade alternativattribut fungerar inte med heltalsvärden
* _LYNX-402_: Internt serverfel vid försök att hämta priceDetails för paketprodukter med dynamiskt pris
* _LYNX-403_: only_x_left_in_stock returnerar alltid 0 för konfigurerbara produkter
* _LYNX-405_: GraphQL-fel: Filtypen stöds inte i frågan om anpassningsbara alternativ
* _LYNX-411_: GraphQL-frågan returnerar inte korrekt beräknat normalpris för anpassningsbara produkter
* _LYNX-412_: AppliedTaxes via EstimatedTotals kvarstår med uppdaterade mutationer
* _LYNX-420_: attributet is_available i CartItemInterface returnerar true även när det säljbara lagret är mindre än produktkvantiteten
* _LYNX-421_: Det går inte att lägga till kupong i kundvagn för rabatt endast för frakt
* _LYNX-425_: Normalpris för produkt med 12 decimaler och fel värde
* _LYNX-430_: GraphQL-serverfel i varukorgen med produkt som inte ingår i paketet
* _LYNX-441_: Det går inte att skapa en adress med anpassade attribut
* _LYNX-447_: GraphQL-serverfel i kundvagn med endast_x_left_in_stock för paketerad produkt
* _LYNX-464_: GraphQL-fel vid borttagning av andra produkter med otillräckligt konfigurerbar produkt i kundvagn
* _LYNX-469_: Det går inte att lägga till produkter eftersom SKU:n i mutationen är skiftlägeskänslig
* _LYNX-526_: GraphQL. Konfigurationen respekteras inte för CANCEL-order available_actions

### Andra utvecklingsverktyg

* _AC-10658_: [Problem] Korrigera HTML-syntaxfel i visual.phtml
   * _Korrigera anteckning_: Systemet stänger nu starttaggen i filen visual.phtml korrekt, vilket garanterar korrekt HTML-syntax. Tidigare stängdes inte starttaggen korrekt, vilket orsakade ett syntaxfel i HTML.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/38247>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/pull/37457>
* _AC-11474_: [Issue] Ändrad &quot;active&quot; till &quot;enabled&quot; i kommandot bin/magento Maintenance:status
   * _Korrigera anteckning_: Systemet tillhandahåller nu mer korrekta statusmeddelanden för kommandot för underhållsläge, vilket ändrar statusen från &quot;aktiv&quot; till &quot;aktiverad&quot; och från &quot;inte aktiv&quot; till &quot;inaktiverad&quot;. Tidigare visades statusmeddelandet för kommandot för underhållsläge som &quot;active&quot; eller &quot;not active&quot;, vilket kan leda till förvirring.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/38486>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/pull/38410>
* _AC-12571_: Navigering i kategoriträdet leder till fel i Redis: &quot;Redis-sessionen överskrider samtidiga anslutningar&quot;
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/38851>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/0611e750>

### Betalningar

* _ACP2E-2841_: Betalningsflödet skapar en ny transaktion varje gång vi klickar på knappen Hämta på skärmen Visa transaktion
   * _Korrigera anteckning_: Systemet hämtar nu transaktionsinformation korrekt utan att skapa en ny betalningstransaktion varje gång knappen Hämta visas på skärmen Visa transaktion. Tidigare skapades en ny betalningstransaktion felaktigt för en beställning som redan hade betalats när du klickade på knappen Hämta.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/b2286ecf>
* _ACP2E-3028_: Senare betalningsmeddelande visas inte i PDP för kanadensiskt betalningsmottagarkonto
   * _Korrigera anteckning_: Systemet visar nu korrekt PayLater-meddelandet för kanadensiska PayPal-handelskonton på produktinformationssidan (PDP) när köparens land kan fastställas från faktureringsadressen eller leveransen för kontot. Tidigare visades inte PayLater-meddelandet på grund av en saknad parameter, vilket resulterade i ett fel i webbläsarkonsolen.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/6a185204>

### Prestanda

* _AC-12000_: [Utgåva] Kodrensning och lägg till nytt kritiskt huvudblock och flytta kritiska CSS före resurser
   * _Korrigera anteckning_: Systemet innehåller nu ett nytt kritiskt huvudblock och flyttar kritisk CSS före resurser, vilket möjliggör mer anpassning och prestandaoptimering i förgrunden. Tidigare placerades inte den kritiska CSS-koden före resurserna, vilket begränsade möjligheterna till anpassning och optimering.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/38748>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/pull/35580>
* _AC-12176_: Temakompileringen avbryts när mysql-värden innehåller portinformation
   * _Korrigera anteckning_: Systemet hanterar nu konfigurationen för MySQL-värden som innehåller portinformation, vilket säkerställer att temat kompileras. Tidigare misslyckades temakompileringen om konfigurationen MySQL-värd i databasanslutningen innehöll portinformation.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/38799>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/pull/38842>
* _ACP2E-2494_: Prestandaproblem vid inläsning av produktattribut i kundvagnsregler
   * _Korrigera anteckning_: Förbättrade frågeprestanda för försäljningsregler - från ca 150 ms till ensiffriga ms.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/ba25af8a>
* _ACP2E-2673_: Prestanda för partiell prisindexering
   * _Korrigera anteckning_: Prestandan för partiell prisindexering har förbättrats genom att några av de borttagningsfrågor som används i indexeringsprocessen har optimerats.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/ba25af8a>
* _ACP2E-2850_: Beställningen avvisas vid konfiguration av flera butiker när Async-order-bearbetning används + Villkor
   * _Korrigera anteckning_: Beställningar från icke-standardwebbplatser med aktiverade villkor bearbetas nu.
Innan de avvisades automatiskt.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/57a32313>
* _ACP2E-2910_: API-anrop för orderåterställning tar lång tid att köra
   * _Korrigera anteckning_: Systemet kör nu anropet till API:t för orderåterställning inom en rimlig tidsram, vilket förbättrar prestanda när ett stort antal order hämtas. Tidigare tog det lång tid att köra anropet till API:t för orderraster, vilket orsakade fördröjningar när ett stort antal order hämtades.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/001e5188>

### Prestanda, marknadsföring

* _ACP2E-2617_: Indexeraren för försäljningsregel slutade köras
   * _Korrigera anteckning_: Systemet slutför nu försäljningsregelindexeraren även med ett stort antal kombinerade filtergrupper, vilket säkerställer att kundvagnsregelvillkoren tillämpas som förväntat. Tidigare kunde indexeraren för försäljningsregeln inte slutföras när det fanns ett stort antal kombinerade filtergrupper, vilket ledde till ett felmeddelande och förhindrar att villkoren för kundvagnsregeln tillämpades.

### Priser

* _AC-11810_: Pris saknas för Magento2.4.6-p4 Order API Simple Item
   * _Korrigera anteckning_: Systemet visar nu priset på enkla produkter korrekt när det efterfrågas via Order API, vilket ger korrekt datarepresentation. Tidigare visades priset på enkla produkter felaktigt som noll i API-svaret.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/38603>

### Produkt

* _AC-10535_: Specialtecken i konfigurerbara associerade produktnamn konverteras till HTML-entiteter.
   * _Korrigera anteckning_: Systemet behåller nu specialtecken i namnen på associerade produkter när en konfigurerbar produkt redigeras, vilket förhindrar att de konverteras till HTML-entiteter. Tidigare konverterades specialtecken i associerade produktnamn till HTML-enheter när den konfigurerbara produkten redigerades.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/38146>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/pull/38447>
* _AC-10947_: Funktionen GetById i ProductRepository skapar inte rätt cachenyckel
   * _Korrigera anteckning_: Systemet skapar nu korrekt en cachenyckel i funktionen GetById för ProductRepository, oavsett om detta lagrings-ID skickas som en sträng eller ett heltal. Detta garanterar att produkten hämtas från minnet vid efterföljande anrop, vilket förbättrar prestandan. Tidigare skulle systemet hämta produkten från databasen varje gång funktionen anropas, även med samma parametrar, på grund av att en felaktig cachenyckel skapades.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/38384>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/pull/38433>
* _AC-11992_: [Utgåva] [MFTF] AdminClickAddOptionForBundleItemsActionGroup
   * _Korrigera anteckning_: Systemet innehåller nu AdminClickAddOptionForBundleItemsActionGroup, vilket förbättrar administratörspanelens funktioner. Den här åtgärdsgruppen var inte tillgänglig tidigare.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/30857>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/pull/30838>
* _AC-5969_: AlertProcessor - Argument #2 ($storeId) måste vara av typen int, sträng angiven
   * _Korrigera anteckning_: Systemet utlöser nu produktvarningsmeddelanden korrekt genom att se till att butiksidentifieraren har rätt datatyp. Tidigare skickades inga produktvarningsmeddelanden på grund av ett typmatchningsfel i butiksidentifieraren.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/35602>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/0574ac23>
* _ACP2E-2944_: [Cloud] funktionen addFilterToMap fungerar inte för vissa kolumner
   * _Korrigera anteckning_: Nu kan den anpassade modulen användas i orderstödrastret. Tidigare inträffade fel när en anpassad modul användes.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/3a7c4d17>

### Kampanj

* _ACP2E-2602_: Kundattributet är inte synligt när kontot skapas från inbjudan
   * _Korrigera anteckning_: Kundattribut är tillgängliga när du skapar konto från inbjudan.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/39d54c2d>
* _ACP2E-2627_: Kupongkod med en kuponggräns frisläppas inte för betalning. Orderannullering misslyckades.
   * _Korrigera anteckning_: Systemet uppdaterar nu omedelbart kuponganvändning när en order skapas eller annulleras, och lägger till regelanvändning i en kö för att förhindra potentiella lås. Detta garanterar att en kupongkod med en kuponggräns för användning per kupong frisläpps och kan återanvändas om en order annulleras på grund av en misslyckad betalning. Tidigare släppte systemet inte kupongkoden för återanvändning i sådana fall, vilket resulterade i ett felmeddelande om att kupongkoden inte var giltig.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/c971859e>
* _ACP2E-2811_: [Cloud] Omindexering av katalogregelns produktindexerare ger SQLSTATE [HY000]: Allmänt fel: 2006 MySQL-servern har försvunnit.
   * _Korrigera anteckning_: Systemet hanterar nu korrekt anpassat batchantal i di.xml för Magento\CatalogRule\Model\Indexer\IndexBuilder, vilket förhindrar SQL-fel som &quot;Allmänt fel: 2006 MySQL-servern har försvunnit&quot; under omindexeringen av katalogregelns produktindexerare på grund av felaktig batchstorlek för stora kataloger
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/b2286ecf>
* _ACP2E-2926_: [CLOUD]Kundsegmentets kundprisregel för besökare tillämpar inte rabatt på kundvagnen
   * _Korrigera anteckning_: Systemet tillämpar nu korrekt kundprisregler för besökare, även om regeln inte använder en kupong, så att rätt rabatter tillämpas på kundvagnen. Tidigare tillämpades inga rabatter på kundvagnen för besökssegment såvida inte kundprisregeln använde en kupong.
* _ACP2E-3024_: Attributet &quot;Type&quot; saknas på fliken &quot;Products to Match&quot; i relaterade produktregler
   * _Korrigera anteckning_: Attributet &quot;Typ&quot; är nu tillgängligt som ett filteralternativ på fliken &quot;Produkter att matcha&quot; i modulen &quot;Relaterade produktregler&quot;, vilket ger en mer exakt regeldefinition. Tidigare saknades det här attributet på fliken&quot;Produkter att matcha&quot;, vilket begränsar möjligheten att skapa korrekta matchningsvillkor.

### SEO

* _AC-11907_: Om du lägger till URL-omskrivningar med en accent läses den oändliga inläsningen in
   * _Korrigera anteckning_: Systemet skapar nu och hanterar URL:er som skrivs om med accenter, vilket förhindrar oändlig inläsning under sparandet. Tidigare orsakade tillägg av en URL-omskrivning med en accent ett oändligt inläsningsproblem.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/38692>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/44cef3a9>
* _ACP2E-2641_: Fel kategori-url-rewrite för flera lager för kategori på tredje nivån
   * _Korrigera anteckning_: Generera korrekt URL-omskrivning för underordnade med överordnad med anpassad URL-omfångsnyckel
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/ea79f7dd>
* _ACP2E-2770_: Dubbelbyte-tecken (specialtecken) i fältet Produktnamn blockerar skapande av produkter i serverdelen
   * _Korrigera anteckning_: En ny inställning har lagts till som gör att du kan använda transkribering på produkt-URL:en eller inte. Inställningen är tillgänglig här: Lagrar > Konfiguration > Katalog > Katalog > Sökmotoroptimering: &quot;Tillämpa transkribering för produkt-URL&quot;
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/b2286ecf>

### Säkerhet

* _AC-11762_:
   * _Korrigera anteckning_: Uppdatera 2FA OTP-fönsterfält med korrekt beskrivning och standardvärde efter BiC-ändring
   * _GitHub-kodbidrag_: Uppdaterat kommando för sättet som otp_window-perioden ska anges från och med nu bin/magento config:set twofactorauth/google/otp_window VALUE
to bin/magento config:set twofactorauth/google/leeway VALUE
* _AC-11855_: [Problem] Popup-meny för CSP-teckensnittsstöd saknas
   * _Korrigera anteckning_: Systemet tillåter nu inläsning av teckensnittet https://www.paypalobjects.com/webstatic/mktg/2014design/font/PP-Sans/PayPalSansBig-Medium.woff&#39; utan att bryta mot direktivet Content Security Policy, vilket säkerställer att popup-menyn Paylater visas korrekt. Tidigare nekades teckensnittet att läsas in på grund av en överträdelse av direktivet Content Security Policy, vilket orsakade visningsproblem med popup-menyn Paylater.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/38624>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/pull/37401>
* _AC-11937_:
   * _Korrigera anteckning_: Uppdatera 2FA OTP-fönsterfält med korrekt beskrivning och standardvärde efter BiC-ändring
   * _GitHub-kodbidrag_: Uppdaterat kommando för sättet som otp_window-perioden ska anges från och med nu bin/magento config:set twofactorauth/google/otp_window VALUE
to bin/magento config:set twofactorauth/google/leeway VALUE
* _AC-12309_:
   * _Korrigera anteckning_: Uppdatera användardokumentationen för tvåfaktorautentisering (2FA) för att ändra kommandot otp_window
   * _GitHub-kodbidrag_: Uppdatera användardokumentation för tvåfaktorautentisering (2FA) om du vill ändra kommandot för OTP_WINDOW-inställningar enligt: https://jira.corp.adobe.com/browse/AC-11762

### Leverans

* _AC-10757_: [Problem] Korrigerat stavfel i tracking.phtml - JS-funktioner med namnet &quot;currier&quot; har ändrats till &quot;operator&quot;
   * _Korrigera anteckning_: Systemet använder nu termen &quot;operator&quot; i stället för den felstavade &quot;currier&quot; i de JavaScript-hanterarfunktioner som används i orderspårningsmallen, vilket ger korrekt funktionsnamn och kodklarhet. Tidigare användes den felstavade termen&quot;currier&quot;, vilket kan leda till förvirring och inkonsekvenser i kodbasen.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/34523>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/pull/33414>
* _AC-11811_:
   * _Korrigeringsanteckning_: UPS REST &quot;En leverans kan inte ha KGS/IN eller LBS/CM eller OZS/CM som måttenhet&quot;
   * _GitHub-problem_: &lt;<https://github.com/magento/magento2/commit/9b1713d8>>
   * _GitHub-kodbidrag_: UPS-hastigheterna visas i kassan och i kundvagnen.
* _AC-11916_:
   * _Åtgärdsanteckning_: [QPT] UPS REST &quot;En leverans kan inte ha KGS/IN eller LBS/CM eller OZS/CM som måttenhet&quot;
   * _GitHub-kodbidrag_: UPS-hastigheterna visas i kassan och i kundvagnen.
* _AC-11938_: UPS REST &quot;En leverans kan inte ha KGS/IN eller LBS/CM eller OZS/CM som måttenhet&quot;
   * _Korrigera anteckning_: Se till att UPS-hastigheterna visas i kassan och kundvagnen.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/38618>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/493e01f5>
* _AC-11983_:
   * _Åtgärdsanteckning_: [QPT] UPS REST &quot;En leverans kan inte ha KGS/IN eller LBS/CM eller OZS/CM som måttenhet&quot;
   * _GitHub-kodbidrag_: UPS-hastigheterna visas i kassan och i kundvagnen.
* _AC-11984_:
   * _Åtgärdsanteckning_: [QPT] UPS REST &quot;En leverans kan inte ha KGS/IN eller LBS/CM eller OZS/CM som måttenhet&quot;
   * _GitHub-kodbidrag_: UPS-hastigheterna visas i kassan och i kundvagnen.
* _ACP2E-2738_: Spårningsfönstret visar fel förväntat leveransdatum
   * _Korrigeringsanteckning_: Visa korrekt leveransdatum för fedex-fraktfirma.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/57a32313>
* _ACP2E-2763_: Tabellhastigheter visas fortfarande även om kostnadsfri leverans används
   * _Korrigera anteckning_: Leveransmetoden för tabellhastighet visas nu även om Fri frakt blir tillgänglig efter kupongtillämpning
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/b2286ecf>
* _ACP2E-2765_: MFTF-test AdminCreatingShippingLabelTest misslyckades på grund av att autentiseringsuppgifter inte har lagts till i Jenkins-miljön
   * _Korrigera anteckning_: korrigering för mftf-test
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/ea79f7dd>

### Mellanlagring och förhandsvisning

* _ACP2E-2901_: Inställningarna för schemalagd uppdatering sparas inte om de ursprungligen lades till genom att uppdatera
   * _Korrigera anteckning_: Systemet raderar nu produktattributvärden korrekt i efterföljande schemalagda uppdateringar när sådana attribut ändras i den aktuella uppdateringen. Tidigare var det omöjligt att radera sådana attributvärden när ett produktattribut ändrades av en schemalagd uppdatering när en ny schemalagd uppdatering skapades, vilket innebar att användaren måste redigera dem igen när den skapades.
* _ACP2E-2999_: Från-datum- och till-datumregeln för kundvagn är inte synkroniserad med mellanlagringsuppdatering
   * _Korrigera anteckning_: Datum sparas enligt uppdateringar för kundprisregelsmellanlagring.
* _ACP2E-3104_: JS-fel i förhandsvisning av mellanlagring
   * _Korrigera anteckning_: Nu läses filen form-mini-stub.js in utan JS-syntaxfel i utvecklingsverktygen.
* _ACP2E-3162_: Produktens mellanlagrade innehåll för specialpris kan inte uppdateras
   * _Korrigera anteckning_: Systemet tillåter nu redigering av slutdatumet för en prisuppdateringskampanj efter att den har startats, vilket säkerställer att användarna kan göra nödvändiga justeringar i sina kampanjer. Tidigare uppstod ett fel när slutdatumet för en aktiv kampanj skulle uppdateras, vilket hindrade användarna från att göra ändringar.

### Målinriktning

* _AC-9432_: [Utgåva] Tillåt användning av CIDR-intervall i tillåtelselista för underhåll
   * _Korrigera anteckning_: Systemet stöder nu användning av CIDR-intervall i underhållsläget Tillåt IP-lista, vilket möjliggör ett intervall av IP-adresser för att kringgå underhållsläge. Tidigare tillät underhållsläget IP-listan endast tillåtna enskilda IP-adresser att kringgå underhållsläge.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/37943>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/pull/30699>

### Testramverk

* _AC-11491_:
   * _Korrigera anteckning_: [Hoppa över] Du måste ångra integreringstestet igen
   * _GitHub-problem_: &lt;<https://github.com/magento/magento2/commit/493e01f5>>
   * _GitHub-kodbidrag_: Hoppa över alla integreringstest som hoppas över i den här PR-funktionen - https://github.com/magento-commerce/magento2ce/pull/8811/
* _AC-11654_: Integrationstest misslyckades med testDbSchemaUpToDate på grund av JSON-kolumntyp
   * _Korrigera anteckning_: Systemet känner nu igen JSON-kolumntyper korrekt i databasschemat under integrationstester och förhindrar testfel på grund av en felmatchning mellan databasschemat och det deklarativa schemat. Tidigare identifierades JSON-kolumntyper felaktigt som LONGTEXT i MariaDB, vilket medförde att integreringstester misslyckades.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/ef81f5a2>

### UI Framework

* _AC-12128_: Prototype.js security vulnerability fix CVE-2020-27511
   * _Åtgärdsmeddelande_: Systemet har uppdaterats för att åtgärda säkerhetsluckan CVE-2020-27511 i Prototype.js 1.7.3, vilket förbättrar den övergripande säkerheten i systemet. Före den här uppdateringen var systemet känsligt för en denial of service-attack (Regular Expression Denial of Service) genom att ta bort skapade HTML-taggar.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/de4dfb8e>
* _AC-12189_: Grunt Less använder pub/-prefix för källmappningar
   * _Korrigera anteckning_: Systemet genererar nu färre/css-källkartor utan prefixet /pub för sökvägar när grunt används, vilket eliminerar behovet av en lösning i webbserverkonfigurationen. Tidigare krävdes en specifik konfiguration på webbservern för att /pub-prefixet i källmappssökvägar skulle fungera korrekt.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/38837>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/pull/38840>
* _AC-1306_: Statiskt innehåll distribueras för inaktiverade moduler
   * _Korrigera anteckning_: Nu utesluts CSS-relaterade till inaktiverade moduler från de slutliga CSS-utdatafilerna, vilket säkerställer att onödiga format inte läses in. Tidigare inkluderades CSS för inaktiverade moduler i de slutliga CSS-utdatafilerna, vilket ledde till inläsning av extra, onödiga format.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/24666>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/pull/32922>
* _AC-9007_: [Utgåva] Läs inte in kontext för serverdelsblock på klientdel
   * _Korrigera anteckning_: Systemet ser nu till att kontexten för backend-block inte läses in på klientservern, vilket förhindrar att onödiga backend-sessioner och eventuella sessionslås skapas. Tidigare lästes serverdelen in felaktigt på klientsidan, vilket ledde till att serverdelssessioner och eventuella sessionslås skapades.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/37617>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/pull/36368>
* _ACP2E-2529_: Undantag vid kontroll av ett presentkortssaldo när Recaptcha är aktiverat
   * _Korrigera anteckning_: Användare kan hämta presentkortssaldo i vyn och redigera kundvagnsskärmen. Tidigare visades inte dessa uppgifter när reCAPTCHA aktiverades.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2-page-builder/commit/4a2795ea>
* _ACP2E-2729_: [CLARIFICATION] Funktionsbegäran ADA-överensstämmelse
   * _Korrigera anteckning_: Systemet garanterar nu ADA-kompatibilitet genom att ta bort CSS-egenskaper som inte stöds och ersätta dem med de som stöds i filen print.css. Tidigare ledde användningen av CSS-egenskaper som inte stöds till problem med webbläsarkompatibiliteten.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/57a32313>
* _ACP2E-3061_: [Cloud] Sammanfusionsbibliotekskod i effect-drop.js i AC 2.4.4-p8
   * _Korrigera anteckning_: Systemet implementerar nu biblioteket effect-drop.js korrekt, vilket garanterar att jQuery-gränssnittseffekterna fungerar som de ska. Tidigare skrevs biblioteket effect-drop.js av misstag över med biblioteket effect-clip.js, vilket kan orsaka problem med jQuery-gränssnittseffekter.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/35b1b1da>
