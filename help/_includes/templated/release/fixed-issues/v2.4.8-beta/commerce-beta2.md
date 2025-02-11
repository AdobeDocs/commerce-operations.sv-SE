---
source-git-commit: cfaa71f84f7d27d41c9d991aceef0087ee3d8ec0
workflow-type: tm+mt
source-wordcount: '9092'
ht-degree: 0%

---
# Adobe Commerce åtgärdade problem (v2.4.8-beta2)

## Åtgärdade problem i v2.4.8-beta2

Vi har åtgärdat 206 problem i Adobe Commerce 2.4.8 Core Code. En deluppsättning av de åtgärdade problemen som ingår i den här versionen beskrivs nedan.

### API:er

* _ACP2E-3236_: Async-åtgärden misslyckas när SKU saknas i nyttolasten
   * _Korrigera anteckning_: Async- och sync-åtgärder misslyckades tidigare på grund av produktsparningsfel om sku saknas i nyttolasten. Efter korrigeringen misslyckas åtgärderna för asynkron och synkroniserad produkt för att spara rest-API med relevant undantagsmeddelande.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/66dea0de>
* _ACP2E-3376_: [CLOUD] Det går inte att uppdatera baspriserna med REST API (värdet för &#39;value_id&#39; i &#39;catalog_product_entity_decimal&#39; ökas inte korrekt.)
   * _Korrigera anteckning_: Tidigare i den här korrigeringen ökade ökningen av kostnadsöknings-ID när rest api /rest/default/V1/products/base-prices anropades felaktigt så att det fanns ett mellanrum mellan värdena. Efter korrigeringen ökas det stegvisa ID:t stegvis. Fältintervallet value_id har också ökats.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/d50f6b5d>
* _ACP2E-3486_: Standardvärden är inte inställda för datum- och tidsattribut med produkterna RestAPI
   * _Korrigera anteckning_: Standardvärden ställs nu in korrekt för datum- och datum- och tidsattribut via RestAPI
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/1984c61c>

### API:er, kundvagn och utcheckning

* _ACP2E-3343_: Kritiskt 500-fel: Magento\Framework\Webapi\Exception relaterat till Acceptera HTTP-huvud
   * _Korrigera anteckning_: Efter korrigeringen finns det inget problem med att ange rubriken&quot;Godkänn&quot;.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/1366ae5e>

### API:er, GraphQL

* _ACP2E-3348_: Det finns ingen graphQl tillgänglig för prenumeration på belöningspoänguppdateringar för kund
   * _Korrigera anteckning_: Tidigare till korrigeringen kunde kundattributet belöning_warning_notification inte uppdateras via GraphQL mutation och Rest API-anrop. Nu kan uppdateras på samma sätt som kundattributet belöning_update_notification.

### Konto

* _AC-10886_: Uppdatera administratörslösenord.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/38352>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/4bca5dfe>
* _AC-11718_: Omdirigeringsslinga när URL har versaler
   * _Korrigera anteckning_: Systemet konverterar nu automatiskt versaler i URL:er till gemener, vilket förhindrar en omdirigeringsslinga vid åtkomst till hemsidan. Tidigare skulle en omdirigeringsslinga uppstå om det fanns versaler i URL:en för den säkra basen när du försökte komma åt hemsidan.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/38538>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/pull/38539>
* _AC-13000_: Kryssrutan Logga in som kundanmälan kan inte översättas
   * _Korrigera anteckning_: Systemet tillåter nu att kryssrutorna Logga in som kundanmälan och Logga in som kund anges i Store-vyn, vilket möjliggör översättningar för olika butiksvyer. Tidigare hade dessa fält bara angetts i webbplatsomfånget, vilket förhindrar översättningar för enskilda butiksvyer.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/32329>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/pull/32359>
* _ACP2E-3329_: När du har loggat in visas inte produkter som lagts till i jämförelselistan som gästanvändare.
   * _Korrigera anteckning_: Produkter som lades till i produktjämförelselistan före inloggning som kund bevaras nu efter inloggning.
Tidigare var produkterna som lagts till i jämförelselistan som gästanvändare inte synliga efter inloggning.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/078c387e>
* _ACP2E-3433_: Konfiguration av Tillåt länder orsakar problem i kundadresskonfigurationer
   * _Korrigera anteckning_: Om du nu väljer Tillåt länder påverkas inte länder som visas utanför det angivna omfånget. Tillåt tidigare att länder konfigureras som påverkade kundadressattribut utanför angivet omfång
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/078c387e>
* _ACP2E-3445_: Delat presentregister visar händelsedatumet som en dag tidigare
   * _Korrigera anteckning_: Presentregisterdatumet visas korrekt nu i Storefront

### Konto, API:er, GraphQL

* _ACP2E-3246_: Kund-API - inloggningsfelnummer kan inte återställas till 0 efter lyckad inloggning
   * _Korrigera anteckning_: Felnumret återställs till noll i kundentitetstabellen efter att kunden har loggat in via API-slutpunkter.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/ec7e32a9>

### Konto, administratörsgränssnitt, B2B

* _ACP2E-3038_: Begränsade administratörsanvändare kan inte alltid se anpassade delade kataloger
   * _Korrigera anteckning_: Begränsade administratörsanvändare kan nu konsekvent visa och hantera kunder och alla delade kataloger som produkterna är tilldelade till, förutsatt att de har tillgång till den specifika butiken. Tidigare kunde en begränsad administratörsanvändare med åtkomst till en viss butik inte alltid se alla delade kataloger som produkterna var tilldelade eller se kunder som inte kunde spara, vilket ledde till inkonsekvenser i systemet.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/7377de59>

### Konto, kundvagn och utcheckning

* _AC-2341_: &quot;select&quot;-attributet för anpassad kundadress återges inte för ny kundadress
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/34950>

### Administratörsgränssnitt

* _AC-10705_: [Problem] Lägg till behörighetskontroll för dataknappen &quot;Läs in data igen&quot;
   * _Korrigera anteckning_: Systemet innehåller nu en behörighetskontroll för knappen &quot;Läs in data igen&quot;, som säkerställer att den bara visas och är tillgänglig för användare med rätt behörighet. Tidigare var knappen &quot;Läs in data igen&quot; synlig och klickbar för alla användare, vilket ledde till en&quot;ej tillåten&quot; sida när användaren klickade utan nödvändig behörighet.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/38283>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/pull/38279>
* _AC-13131_: [Problem] Korrigeringsvarning: Odefinierad matrisnyckel &quot;filters&quot;
   * _Korrigera anteckning_: Systemet hanterar nu scenarier där en ny användare ännu inte har interagerat med bokmärken, vilket förhindrar att en odefinierad matrisnyckelvarning (filters) loggas. Tidigare loggades den här varningen när en ny användare inte interagerat med bokmärken.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/39013>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/pull/38996>
* _AC-13529_: CSV-fil för import av produkter med specialtecken misslyckas på grund av kodändringar i filen Validate.php
   * _Korrigera anteckning_: Systemet validerar och importerar nu produktfiler som innehåller specialtecken, vilket möjliggör en lyckad dataöverföring. Tidigare uppstod ett fel när en CSV-fil med specialtecken skulle importeras.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/6cfb9b6b>
* _AC-13767_: När det maximala antalet begäranden om lösenordsåterställning är större än 0, t.ex. 3, skickas felmeddelanden om att gränsen överskrids innan gränsen nås, dvs. från andra gången
* _AC-13768_: Även om det maximala antalet begäranden om lösenordsåterställning är inställt på 0 (inaktiverat) skickas felmeddelanden om att gränsen överskrids från andra gången
* _AC-7962_: Ingen länk till leverans vid betalning i kassan i mobiltelefonvyn
   * _Korrigera anteckning_: Systemet ser nu till att utcheckningsrubrikerna/länkarna &quot;Leverans&quot; och &quot;Granska och betalningar&quot; alltid visas ovanpå sidan i mobilvyn, så att användarna enkelt kan navigera mellan stegen och göra nödvändiga korrigeringar. Tidigare var dessa titlar/länkar dolda i mobilvyn, vilket gjorde det svårt för användarna att ta reda på det aktuella steget eller gå tillbaka till tidigare steg.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/36856>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/pull/36982>
* _AC-8109_: Leveranskommentarer för kundbeställningar som skapas_at returneras i +0-tidszon som inte finns i den butikskonfigurerade tidszonen
   * _Korrigera anteckning_: Systemet visar nu korrekt fältet &#39;created_at&#39; från leveranskommentarer i kundens konfigurerade tidszon när kundorderfrågan används. Tidigare visades fältet&quot;created_at&quot; i tidszonen +0, oavsett kundens konfigurerade tidszon.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/36947>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/pull/37642>
* _ACP2E-3294_: Leveransadressläget uppdateras inte automatiskt
   * _Korrigera anteckning_: Före korrigeringen var leveransadressens region (eller region-id) inte synkroniserad med adressfaktureringsinformationen. Nu uppdateras både leveransadressens region och region-id korrekt när faktureringsadressinformationen ändras.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/581b7ef1>
* _ACP2E-3364_: Knappen Återställ fungerar inte för Admin-användare för Lägg till/redigera
   * _Korrigera anteckning_: Tidigare fungerade inte knappen Återställ på sidan Lägg till/redigera admin-användare. På panelen Admin under System -> Behörigheter -> Alla användare fungerar nu knappen Återställ korrekt på sidan Lägg till/redigera admin-användare.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/5184c067>
* _ACP2E-3392_: Bruten validering för &quot;Högsta tillåtna kvantitet i kundvagn&quot;
   * _Korrigera anteckning_: Tidigare när `Maximum Qty Allowed in Shopping Cart` skulle vara tom utlöstes inget undantag, men ett tomt värde accepteras inte här. När den här korrigeringen har tillämpats genereras undantag när en tom sträng skickas och produkten kan inte sparas.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/d50f6b5d>
* _AVS2E-3408_: [Gränssnittsproblem för förhandsgranskning i Page Builder] Knapparna i Page Builder-kolumnen är inte korrekt placerade
   * _Korrigera anteckning_: Knapparna i Page Builder-kolumnerna är nu korrekt justerade. Tidigare var de feljusterade i Page Builder-kolumnerna.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2-page-builder/commit/1a52ef4c>
* _ACP2E-3431_: Rapporten för beställda produkter exporteras inte. 404-fel i stället.
   * _Korrigera anteckning_: Rapportexporten för produkter som beställts till CSV och XML fungerar nu som förväntat
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/88660e79>
* _ACP2E-3457_: TinyMCE JS-fel i konsolen efter JS-minification aktiverat med produktionsläge
   * _Korrigera anteckning_: Tidigare visades JavaScript-fel relaterade till TinyMCE 7 i webbläsarkonsolen när JavaScript-miniatyrer aktiverades i produktionsläge på adminpanelen, vilket påverkade funktionaliteten och användarupplevelsen. Nu har problemet lösts och säkerställer att TinyMCE 7 fungerar smidigt utan att några fel genereras, även när JS-minification är aktiverat.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/56463d5e>
* _ACP2E-3459_: Begär ytterligare ändringar för att slutföra korrigeringen för AVS2E-3375 fullständigt
   * _Korrigera anteckning_: -
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/d50f6b5d>

### Administratörsgränssnitt, betalningssätt, beställning

* _AC-13520_: Transaktionsauktorisering visas inte på fliken Transaktion efter ordningen för smarta knappar i PayPal
   * _Korrigera anteckning_: Systemet visar nu transaktionsauktoriseringen korrekt på fliken Transaktion när en order har placerats med den smarta knappen PayPal. Auktoriseringstransaktionen visades inte på fliken Transaktion när du klickade på Auktorisera och ingen ny transaktion av typen Authorization skapades.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/6cfb9b6b>

### Administratörsgränssnitt, mellanlagring och förhandsvisning

* _ACP2E-3424_: [Cloud] Om du tar bort en mall med saknade bilder tas pub/media bort
   * _Korrigera anteckning_: Tidigare till den här korrigeringen togs mappen pub/media bort om namnet på förhandsvisningsbilden saknades för en sidbyggarmall. Efter korrigeringen tas bara mallen bort och förhandsvisningsbilden tas bort om den hittas.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2-page-builder/commit/0986853b>

### Analyser/rapporter

* _AC-9922_: Google Analytics CSP-fel https://region1.analytics.google.com
   * _Korrigera anteckning_: Systemet tillåter nu anslutningar till https://region1.analytics.google.com&#39; när Google Analytics är aktiverat och förhindrar CSP-fel (Content Security Policy). Tidigare skulle det resultera i fel i CSP-konsolen om Google Analytics kunde aktiveras och webbplatsen från EU på grund av en vägran att ansluta till https://region1.analytics.google.com&#39;.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/37750>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/pull/38991>
* _ACP2E-3146_: GTM-händelsen addToCart saknas i dataLayer för konfigurerbar produkt med anpassat alternativ
   * _Korrigera anteckning_: Tidigare utlöstes inte händelsen addToCart för konfigurerbara produkter. Händelsen läggs nu till korrekt i GTM-datalagrets variabel.
* _ACP2E-3183_: NewRelic-webbläsarövervakning av inlineJS-skript orsakar CSP-fel
   * _Korrigera anteckning_: Skript för övervakning av nya webbläsare har nu injicerats av programmet i stället för APM-agenten för kompatibilitet med CSP (Content Security Policy). Tidigare var de NewRelic Browser Monitoring-skript som injicerades av APM-agenten inte kompatibla med CSP och orsakade att skripten inte kördes.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/66dea0de>
* _ACP2E-3189_: INSERT-frågor i registret sales_bestsellers_aggregate_day blir långsamma i projekt med stora försäljningsordervolymer
   * _Korrigera anteckning_: Tidigare tog det lång tid att generera en rapport från de bästsäljare som aggregerade den dagliga rapporten för stora mängder placerade order. Nu genereras rapporten i tid.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/7377de59>
* _ACP2E-3276_: Orderrapporter visar fel valutasymbol
   * _Korrigeringsanteckning_: Valutasymbolen för orderbelopp i orderrapporten togs felaktigt från valuta/alternativ/bas. Det har nu korrigerats till att använda valuta/alternativ/standard för korrekt rapportering.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/fd5cf3af>
* _ACP2E-3302_: [Cloud] Felaktiga beräkningar i kuponganvändningsrapport
   * _Korrigeringsanteckning_: Försäljningssumman i kupongrapportrutnätet beräknas nu korrekt genom att både&quot;Rabattskatteutjämningsbelopp&quot; och&quot;Momskompensationsbelopp för fraktrabatt&quot; inkluderas. Tidigare saknades dessa belopp i beräkningen, vilket ledde till avvikelser mellan försäljningssumman och försäljningsorderdata.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/d75cff27>
* _ACP2E-3339_: Problem med delade &quot;&lt;project_id>/var/tmp&quot;
   * _Korrigera anteckning_: De temporära filerna för Analytics DataExport använder systemkatalogen tmp, som är mer lämplig för frekvent åtkomst och ändringar. För att undvika kollisioner om flera instanser körs på samma server uppdaterades tmp-sökvägen till att använda en instanss unika ID
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/a4cf5e62>

### Analytics/Reporting, Cloud

* _ACP2E-3187_: Mått i NR kan vara missvisande för bakgrundstransaktioner - Uppföljning av ACP2E-3067
   * _Korrigera anteckning_: För bakgrundstransaktioner (cron) används det New Relic-programnamn som definieras i konfigurationsinställningarna
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/ec7e32a9>

### B2B

* _AC-13501_: 2.4.8-beta102-paketet Enterprise Edition fungerar inte med programundantag
* _AC-13816_: Det går inte att aktivera b2b-funktionen i serverdelsadministratören för första gången
* _ACP2E-2139_: Produkter som tilldelats en delad katalog speglas inte i början när partiellt index körs
   * _Korrigera anteckning_: Produkter som har tilldelats till en delad katalog via REST API är nu omedelbart synliga i butiken när partiell indexering är klar. Tidigare var produkterna bara synliga efter en fullständig omindexering.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/7377de59>
* _ACP2E-3247_: sales_clean_quotes cron tar bort offerter från till ännu godkända inköpsorder
   * _Korrigera anteckning_: Offerter som används i inköpsorder tas nu inte bort av cron-jobbet sales_clean_quotes
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/581b7ef1>
* _ACP2E-3465_: Knappen Montera order försvinner i inköpsorderinformationen
   * _Korrigera anteckning_: Ett problem har korrigerats där knappen Montera order doldes för godkända inköpsorder när en produktvariant hade ett minsta antal på kortet angivet
* _ACP2E-3474_: [CLOUD] Ingen sådan entitet med ID = 0 med b2b-modulen
   * _Korrigera anteckning_: Den inloggade användaren kan lägga till produkten i kundvagnen när funktionen för delad katalog är aktiverad.
Tidigare tillagd produkt i kundvagn resulterade i felet &#39;ingen sådan entitet med ID = 0&#39;

### B2B, kundvagn och kassan

* _AC-13817_: Det går inte att visa produkter i kundvagnen när b2b-alla funktioner är aktiverade

### B2B, GraphQL

* _ACP2E-3391_: [Cloud] Det går inte att ange custom_attributes när ett företag skapas över grafikanropet
   * _Korrigera anteckning_: Efter korrigeringen kan du ange attributet &quot;custom_attributes&quot; för företagsadministratören när företaget skapas med hjälp av graphql-begäran.

### Paket

* _AC-10826_: Antal meddelanden om bekräftelsefel i Checkbox-kryssrutan i Store mer än 1
   * _Korrigera anteckning_: Systemet visar nu endast ett valideringsfelmeddelande när användaren klickar på knappen Lägg till i kundvagnen utan att markera några kryssrutealternativ för en paketerad produkt. Tidigare visades flera valideringsfelmeddelanden för varje omarkerad kryssruta.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/3ea26621>
* _AC-13321_: Magento Exception utlöses i vissa ordningsrelaterade testfall
   * _Korrigera anteckning_: Systemet hanterar nu steget sendGuestPaymentInformation korrekt i olika testfall, vilket förhindrar att Magento-undantag genereras. Tidigare inträffade dessa undantag på grund av en null-betalningsmetod, vilket orsakade fel i flera testfall.

### Kort och utcheckning

* _AC-11914_: [Utgåva] Beräkning av kundförsäljningsregel med fast belopp: felaktigt rabattbelopp
   * _Korrigera anteckning_: Nu beräknas rabattbeloppet korrekt för försäljningsregler med fasta kundvagnsbelopp, vilket säkerställer att korrekta rabatter tillämpas oavsett ändringar i kundvagnsartiklar. Tidigare kunde rabattbeloppet variera felaktigt när artiklar i kundvagnen ändrades, vilket ibland resulterade i betydligt större rabatter än förväntat.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/38694>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/581b7ef1>
* _AC-12479_: Kryssrutan Villkor tillåter inte HTML i butiken
   * _Korrigera anteckning_: Systemet har nu stöd för HTML-formatering i kryssrutan &quot;Villkor&quot; i butiken, vilket ger förbättrad anpassning och läsbarhet. Tidigare visades kryssrutetexten i oformaterad text, och eventuella HTML-taggar som användes ignorerades.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/6cfb9b6b>
* _AC-12541_: En kundprisregel som skapats för inloggad användare tillämpas felaktigt för användare som inte är inloggad
   * _Korrigera anteckning_: Systemet tar nu bort kundprisregeln för inloggade användare korrekt när de loggas ut automatiskt på grund av att cookie-filen har upphört att gälla, vilket säkerställer att rabatten inte tillämpas på användare som inte är inloggade. Tidigare tillämpades kundvagnsprisregeln även när användaren var utloggad, vilket resulterade i att en felaktig rabatt tillämpades på icke-inloggade användare.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/38944>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/7d5e3906>
* _AC-13302_: [Utgåva] [FUNKTION] Prestandaoptimering av stora kundvagnar genom att förhindra..
   * _Korrigera anteckning_: Systemet optimerar nu prestanda för stora kundvagnar genom att förhindra dubbla getActions-anrop, vilket ökar hastigheten och effektiviteten i kundvagnsåtgärder. Tidigare anropades funktionen getActions flera gånger för en kundvagn med flera artiklar, vilket saktade ned systemets prestanda.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/39292>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/pull/39290>
* _AC-13797_: Presentregisterlänken fungerar inte korrekt
* _ACP2E-3176_: [Cloud] snabbeställa stora mängder SKU-prestanda
   * _Korrigera anteckning_: Utcheckningsprestanda har förbättrats när attribut som används i kundprisregler inte finns för alla produkter och när funktionen för att ange lägsta annonspris är aktiverad.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/66dea0de>
* _ACP2E-3211_: Dubblerade objekt i kundvagnen
   * _Korrigera anteckning_: Systemet bearbetar nu flera parallella förfrågningar korrekt för att lägga till samma produkt i vagnen i ett enda radobjekt, vilket förhindrar att separata radartiklar för samma SKU skapas. Tidigare skulle parallella begäranden om att lägga till samma produkt i varukorgen på Storefront resultera i flera radobjekt för samma SKU.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/66dea0de>
* _ACP2E-3296_: E-postbekräftelse för utcheckningsorder skickas till e-postmeddelanden som anges i Förnamn/Efternamn
   * _Korrigera anteckning_: E-postbekräftelsen för utcheckningsordningen, som tidigare skickades när ett e-postliknande mönster angavs i fälten för för för- och efternamn, skickas inte längre.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/5184c067>
* _ACP2E-3402_: Checkout shipping address form get update with errors address
   * _Korrigera anteckning_: shippingAddressFromData sparas nu i den lokala lagringen per webbplats. Tidigare kunde en adress från fel webbplats fyllas i automatiskt i leveransadressformuläret vid utcheckning om en butikskod användes i URL:en och utcheckningen initierades från flera webbplatser under samma gästsession.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/078c387e>
* _ACP2E-3405_: [CLOUD] Utcheckningen behåller inte den valda faktureringsadressen när adresssökning är aktiverat
   * _Korrigera anteckning_: Utcheckningsbetalningssidan behåller nu den valda faktureringsadressen när adresssökning är aktiverad. Tidigare om&quot;Antal kundadresser gräns&quot; har konfigurerats till 1 och kunden har fler än en adress, kommer den valda faktureringsadressen att försvinna när sidan har lästs in igen.
* _ACP2E-3407_: Presentkortsprodukt | Koppla kort sammanfogar presentkort
   * _Korrigera anteckning_: Presentkortsprodukter har nu sammanfogats korrekt i vagnen
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/88660e79>
* _ACP2E-3488_: Befintliga offertdata uppdateras inte/visas inte, utan skapar i stället en ny offertpost när trigger_recllect = 1
   * _Korrigera anteckning_: Kundens kundvagnsartiklar försvinner inte längre om en produkt tas bort efter att den har lagts till i kundvagnen.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/1984c61c>

### Katalog

* _AC-11970_: Det går inte att ordna om konfigurerbara produkter med en kryssruta markerad som anpassat alternativ
   * _Korrigera anteckning_: Systemet bearbetar nu korrekt omsorteringen av konfigurerbara produkter med ett enda anpassat kryssrutealternativ, vilket gör att korgen kan skapas. Tidigare uppstod ett fel när sådana produkter skulle sorteras om och artiklarna kunde inte läggas till i kundvagnen.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/38736>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/1d144bce>
* _AC-13068_: Listrutealternativ saknas
   * _Korrigera anteckning_: Nu visas alla värden korrekt i listrutan när ett nytt attribut med fler än 20 värden skapas. Tidigare visades bara de första 20 värdena eller något annat av de valda sidvärdena, vilket medförde att de återstående värdena saknades.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/47b448e2>
* _AC-13296_: [Problem] Använd aktuellt lager-ID för kategorins körtidscache
   * _Korrigera anteckning_: Systemet använder nu korrekt det aktuella lagrings-ID:t för kategorikörningscache, vilket förhindrar åsidosättning av data när emulering används eller anpassad kod sparar kategorin i olika butiker. Tidigare kunde objektet som lagrats i körningsmiljön ha kommit från fel butik, vilket ledde till åsidosättande av data.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/39310>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/pull/36394>
* _AC-13324_: bin/magento sampledata:deploy —no-update genererar ett undantag
   * _Korrigera anteckning_: Systemet accepterar nu ett booleskt värde korrekt när alternativet —no-update används i kommandot sample data:deploy, vilket förhindrar fel under distributionen av exempeldata. Tidigare uppstod ett fel när det här kommandot användes eftersom ett heltalsvärde felaktigt förväntades.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/39344>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/pull/39345>
* _AC-13355_: [Problem] Korrigera användningen av EAV-cachetypen
   * _Korrigera anteckning_: Systemet använder nu EAV-cachetypen korrekt på alla relevanta platser, vilket ger en konsekvent och effektiv datacachelagring. Tidigare användes EAV-cachetypen inte konsekvent, vilket ledde till ineffektivitet och inkonsekvenser i datacachningen.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/32322>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/pull/31264>
* _AC-13596_: Katalogsökning med tomma data går till sökresultatsidan[2.4.dev-grenen]
   * _Korrigera anteckning_: Systemet behåller nu användare korrekt på sidan Avancerad sökning och visar ett felmeddelande när de försöker utföra en sökning utan att ange några data. Tidigare omdirigeras användare till sidan Avancerad sökning i katalog med ett meddelande som uppmanar dem att ändra sökningen.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/6cfb9b6b>
* _AC-13786_: Den vita kantlinjen tar inte bort efter att product_image_white_border för det anpassade temat har inaktiverats
* _ACP2E-3103_: RSS-flöde för nya produkter uppdateras inte med nya produkter på grund av cache
   * _Korrigera anteckning_: RSS-flödet för nya produkter uppdateras nu när en produkt har angetts som ny och sparad
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/d01ee51e>
* _ACP2E-3198_: [cloud] Problem med zoomning och flyttning med två fingrar på den faktiska mobila enheten
   * _Korrigera anteckning_: Systemet garanterar nu konsekvent bildzoomning på mobila enheter, vilket ger en smidig och förutsägbar användarupplevelse. Tidigare var funktionen för bildzoomning inkonsekvent och skulle plötsligt zoomas ut efter en viss punkt när den visades på en mobil enhet.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/1366ae5e>
* _ACP2E-3282_: När vi frigör produkter från den delade katalogen rensas inte önskelisteprodukterna
   * _Korrigera anteckning_: Nu visas inga objekt i önskelistan om en produkt inte är tillgänglig i den delade katalogen. Tidigare visade önskelistsidan felaktigt antalet &quot;1 objekt&quot; även när det inte fanns några objekt i önskelistan.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/5184c067>
* _ACP2E-3286_: Samhörande produkter Markera alla/Avmarkera alla problem
   * _Korrigera anteckning_: Tidigare fungerade inte knapparna Markera alla/Avmarkera alla för relaterade produkter korrekt om en produkt valdes manuellt. Efter korrigeringen fungerar knapparna nu konsekvent, även efter det manuella valet, så att alla produkter markeras eller avmarkeras korrekt.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/fd5cf3af>
* _ACP2E-3336_: [Cloud] Stock-aviseringsöversättning till fel språk
   * _Korrigera anteckning_: När du skickar butiks-/prisaviseringar för en webbplats med flera butiksvyer på olika språk används språket för butiksvyn där aviseringen skapades i e-postmeddelandet.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/a4cf5e62>, <https://github.com/magento/inventory/commit/9f3e63d1>
* _ACP2E-3350_: Namnet på de inaktiverade kategorierna är inte längre nedtonat i kategoriträdet
   * _Korrigera anteckning_: Tidigare var inaktiverade kategorier inte nedtonade i kategoriträdet. Nu visas de med en gråskaleeffekt.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/d75cff27>
* _ACP2E-3410_: Inläsning av konfigurerbara redigeringsformulär orsakar timeout och minnesöverbelastning
   * _Korrigera anteckning_: Före korrigeringen konstruerades konfigurerbara produktvariationer baserat på alla möjliga kombinationer av attributalternativ. I de fall där attributen hade många alternativ resulterade detta i en långsam och resurskrävande åtgärd. Nu kan du konstruera produktvariationer utifrån befintliga underordnade produktattribut. Detta resulterar i betydligt färre beräkningar, vilket innebär en förbättrad resursanvändning.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/078c387e>
* _ACP2E-3454_: Fotorama läser inte in video korrekt när färgrutor används och alternativet är förvalt via URL
   * _Korrigera anteckning_: Produktvideor återges nu korrekt på sidan med konfigureringsbar produktinformation, om URL:en innehåller valda alternativ.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/078c387e>
* _ACP2E-3461_: PageBuilder Carousel-widgeten visar produkter som inte matchar villkoren
   * _Korrigera anteckning_: Produktlistan som används i widgetar uppfyller nu kategorivillkoret
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/078c387e>
* _ACP2E-3469_: Verifieringsfel utlöstes för alla produkter i gruppen när en har en ogiltig kvantitet
   * _Korrigera anteckning_: Nu utlöses valideringsfelet korrekt för alla produkter i gruppen när en produkt har en ogiltig kvantitet, vilket inte hände tidigare.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/56463d5e>
* _ACP2E-3516_: Tillfälliga register rensas inte om processen avslutas
   * _Korrigera anteckning_: Temporära tabeller för indexeraren för CatalogRule rensas nu om indexeringsprocessen avslutas
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/1984c61c>
* _ACP2E-3520_: [QUANS] Kärnenhetstestfel i 2.4.7-p3
   * _Korrigera anteckning_: Versionsinformation för det här testet behövs inte eftersom det är en förbättring av enhetstestet.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/1984c61c>

### Katalog, innehåll

* _ACP2E-3063_: [Cloud]-cachen ogiltigförklaras inte.
   * _Korrigera anteckning_: När en CMS-sida med en uppdaterad designlayout sparades reflekterades den inte korrekt på framsidan. När den här korrigeringen har tillämpats visas rätt designlayout längst fram när vi ändrar designlayouten och sparar CMS-sidan.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/66dea0de>
* _ACP2E-3131_: [Cloud] ankarkategorier/icke-ankarkategorier inverterade i innehållswidgeten
   * _Korrigera anteckning_: När vi tidigare valde Visa på -> ankarkategorier visades alla kategorier som inte reflekterade relationen mellan överordnad och underordnad mellan ankarpunkten och icke-ankarpunkten. När den här korrigeringen har tillämpats visar Visa på -> ankarkategorier bara ankarkategorier (valbara), och Visa på -> icke-ankarkategorier visar icke-ankarkategorier (valbara)
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/7377de59>
* _ACP2E-3152_: Kategorier som inte fungerar med widgetar
   * _Korrigera anteckning_: Tidigare fungerade inte CMS-blocket för olika ankarkategorier/icke-ankarkategorier för de underordnade kategorierna när det visades på framsidan. När den här korrigeringen har tillämpats visas blocket längst fram för olika kategorier.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/d01ee51e>

### Katalog, GraphQL

* _ACP2E-3312_: Tier Prices returnerar fel värde i GraphQL-produkter (jämfört med Storefront)
   * _Korrigera anteckning_: Efter korrigeringen har produktskiktspriserna som returnerats för grafikförfrågningar priset per ett objekt.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/1366ae5e>
* _ACP2E-3385_: [CLOUD] B2B: kategoriproblem via GraphQL
   * _Korrigera anteckning_: Efter korrigeringen returnerar kategorifrågan kategorier med tillåten behörighet, även om rotkategorin inte tillåter behörighet.

### Katalog, söka

* _ACP2E-3345_: Typfel uppstod när objektet skapades: Magento\CatalogSearch\Model\Indexer\Fulltext\Interceptor Exception
   * _Korrigera anteckning_: Efter korrigeringen kan en instans av klassen Magento\CatalogSearch\Model\Indexer\Fulltext skapas utan att $data anges.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/1366ae5e>
* _ACP2E-3521_: [CLOUD] Problem med produkter visas inte i Edge efter att de sparats i Magento Admin
   * _Korrigera anteckning_: Efter korrigeringen går det inte att missa konfigurerbara produkter med underordnade produkter med långa namn i butiken.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/1984c61c>

### Katalog, leverans

* _ACP2E-3195_: Leveransadressen är tom när en order för ett presentregisterobjekt läggs
   * _Korrigera anteckning_: Tidigare genererade en tom adress för presentregisterobjekt för gästanvändare när de returnerades från e-postfunktionen, vilket är felaktigt för att placera en order. När den här korrigeringen har tillämpats kontrollerar presentregistret inloggade användare/gästanvändare och tilldelade adresser om de finns.

### Innehåll

* _AC-12692_: Widget-kategoriträdet återges inte korrekt
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/39008>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/58e40ceb>
* _AC-13054_: Det går inte att se meddelandet &quot;Använda standardvärde&quot; när du ändrar temat på designkonfigurationssidan
   * _Korrigera anteckning_: Systemet innehåller nu en separat kolumn som visar meddelandet &quot;Använda standardvärde&quot; beroende på det valda temat på designkonfigurationssidan. Detta garanterar att standardvärdets status är tydlig och synlig. Tidigare visades inte meddelandet&quot;Använda standardvärde&quot;, vilket ledde till missförstånd om det valda temats status.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/47b448e2>
* _AC-13569_: [Problem] Återställer bakåtkompatibilitet med TinyMCE-plugin-program igen (efter det...
   * _Korrigera anteckning_: Systemet återställer nu bakåtkompatibilitet med TinyMCE-plugin-program, vilket gör att funktioner som definierats inuti plugin-programmet kan anropas när widgeten används från en annan plats. Tidigare returnerade inte plugin-programmen widgetarna som ett objekt på grund av en ändring i TinyMCE-versionen, vilket resulterade i ett fel när vissa funktioner anropades i widgetinstansen.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/39262>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/pull/39258>
* _ACP2E-3122_: [CLOUD] Knappen Överför bild fungerar inte
   * _Korrigera anteckning_: Före knappen Överför bild för Banner och Slider från PageBuilder fungerade inte som förväntat, och när du trycker på knappen öppnas den lokala filhanteraren för att välja den bild som ska överföras.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2-page-builder/commit/476ef8ea>
* _ACP2E-3275_: [Cloud] - CMS Slider återspeglar inte de senaste ändringarna
   * _Korrigera anteckning_: Problemet har åtgärdats genom att skjutreglagelistan uppdateras medan sparhändelsen aktiveras på redigeringsbildskärmen. Tidigare utlöstes den och orsakade problemet.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2-page-builder/commit/ae2cdeb0>
* _ACP2E-3326_: Ett fel inträffar på CSM-sidan när CMS-block infogas med hjälp av Page Builder i en viss ordning
   * _Korrigera anteckning_: Tidigare i vissa versioner av PHP och OS (Linux) hade återgivningen av block som refererade till andra cms-block via PageBuilder misslyckats med &quot;Ett okänt fel uppstod. Försök igen.&quot;. Nu återges innehållet i cms-blocken korrekt i ett PageBuilder-kontrollerat innehåll.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2-page-builder/commit/ae2cdeb0>
* _ACP2E-3388_: [Dynamiska block i molnet] fungerar inte korrekt
   * _Korrigera anteckning_: Inloggade kundsegment har nu rensats efter utloggning så att gästsessionen inte kan ärva tidigare inloggade segment
* _ACP2E-3430_: De senaste säkerhetsuppdateringarna med TinyMCE 7 saknar teckensnittsstorlek
   * _Korrigera anteckning_: Väljare för teckensnittsstorlek och teckensnittsfamilj finns nu i WYSIWYG Editor. Före den här korrigeringen fanns de inte i TinyMCE 7 i redigeringsgränssnittet.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/d50f6b5d>, <https://github.com/magento/magento2-page-builder/commit/2c2f7a0e>

### Kund/Kunder

* _AC-13060_: Kundsegment > Villkor > Produkthistorik* > &quot;produkten visades&quot; fungerar inte
   * _Korrigera anteckning_: Systemet visar nu korrekt matchade registrerade kunder i villkoret&quot;Produkten visades&quot; under Kundsegment när villkoret uppfylls. Tidigare var antalet matchade registrerade kunder noll, även när villkoret var uppfyllt.
* _AC-8499_: Regiontextfältet återställs inte när listrutan för land ändras
   * _Korrigera anteckning_: Systemet återställer nu regionens textfält när landet ändras i listrutan, vilket säkerställer att tidigare värden inte kvarstår. Tidigare återställdes inte regionfältet om landet ändrades från listrutan, vilket innebar att det senast sparade värdet bevaras.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/3ea26621>
* _AC-9240_: Om du tar bort kunden rensas inte alla sessionsdata för webbläsaren på Storefront för inloggad och borttagen kund
   * _Korrigera anteckning_: Om en kund tas bort rensas alla webbläsarsessionsdata från butiken för inloggade och borttagna kunder som förväntat. Köparen kan fortsätta handla och webbläsaren behandlar sin session som en gästsession. Tidigare när kundkontot för en inloggad kund togs bort från Admin uppstod JavaScript-fel i webbläsaren.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/7d5e3906>

### Ramverk

* _AC-10738_: Varnish-konfigurationen utesluter inte alla marknadsföringsparametrar
   * _Korrigera anteckning_: Systemet exkluderar nu alla vanliga marknadsföringsparametrar korrekt i lack-konfigurationen, vilket ger korrekt spårning och analys. Tidigare har vissa marknadsföringsparametrar som gned_source, srsltid och msclodd inte uteslutits, vilket kan leda till felaktiga datainsamlingar.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/38298>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/pull/39188>
* _AC-11592_: [Utgåva] Tillåt endast giltiga inställningar under konfiguration:di:kompilering
   * _Korrigera anteckning_: Systemet genererar nu ett fel under kompileringskommandot setup:di:om en inställning skapas för en klass som inte finns eller som är exkluderad, vilket säkerställer att endast giltiga inställningar tillåts. Tidigare misslyckades dessa scenarier utan att någon information om plugin-program som är associerade med de ursprungliga klasserna återges.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/38517>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/pull/33161>
* _AC-11809_: [Problem] Skicka anpassade attribut till den aktuella länken via XML
   * _Korrigera anteckning_: Systemet tillåter nu att anpassade attribut skickas till den aktuella länken via XML, vilket säkerställer att attributen visas korrekt även när länken är den aktuella sidan. Tidigare visades inte anpassade attribut för den aktuella sidlänken eftersom metoden getAttributesHtml() inte används för den aktuella länken.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/38500>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/pull/30070>
* _AC-12127_: [Utgåva] Undvik en oändlig loop för felkonfiguration
   * _Korrigera anteckning_: Systemet undviker nu en oändlig loop genom att förhindra självrefererande mappning i virtuella typkonfigurationer. Detta garanterar att programmet inte fastnar i en oändlig slinga när ett försök görs att avreferera en självreferensnod. Tidigare, om en virtuell typkonfiguration var självrefererande, skulle det få programmet att snurra oändligt.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/38822>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/pull/38794>
* _AC-12299_: Objekthanteraren används inte för Magento\Csp\Model\Mode\Data\ModeConfigured
   * _Korrigera anteckning_: Systemet använder nu Object Manager korrekt när ModeConfiguring-objektet skapas, vilket tillåter att plugin-program används för det här objektet. Tidigare användes inte Object Manager, vilket förhindrar att plugin-program används i ModeConfiguring-objektet.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/38875>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/pull/38886>
* _AC-12540_: Felaktig dokumentblockkommentar i produktStock och prisaviseringar
   * _Korrigera anteckning_: Dokumentblockkommentaren för metoden deleteCustomer i produktStock- och prisaviseringar har korrigerats för att korrekt återspegla att metoden tar bort alla aktie- eller prisaviseringar som är kopplade till en viss kund och webbplats, inte kunden från webbplatsen. Tidigare hade kommentaren felaktigt angett att metoden var att ta bort en kund från webbplatsen.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/38939>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/pull/39001>
* _AC-12857_: PHP 8.2.15 har tagit bort FTP-tillägget
   * _Korrigera anteckning_: Systemet inkluderar nu FTP-tillägget som ett beroende i filen Composer.json, vilket säkerställer att CSV-import via FTP kan konfigureras korrekt. Tidigare uppstod ett fel vid försök att konfigurera CSV-import via FTP eftersom FTP-tillägget saknas i PHP-paketet.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/39083>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/47b448e2>
* _AC-12964_: Möjlighet att definiera område för DV:di:info CLI-kommando
   * _Korrigera anteckning_: Nu kan utvecklare definiera ett område för CLI-kommandot dev:di:info, vilket förbättrar utvecklings- och felsökningsprocessen. Tidigare kunde kommandot bara visa information för området GLOBAL.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/38758>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/pull/38759>
* _AC-13247_: konfiguration:uppgradering misslyckas med MariaDB 11.4-versionen på grund av förändringar i teckenuppsättning och sortering
* _AC-13279_: [Problem] Ta bort alla parametrar för marknadsföringsget för att minimera cachen
   * _Korrigera anteckning_: Systemet tar nu bort alla parametrar för marknadsföringsinhämtning för att optimera användningen av cache, och speglar logiken som används när lack används. Tidigare kunde de här parametrarna leda till cachebloggning och försämrade prestanda.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/39266>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/pull/39099>
* _AC-13345_: [Problem] [PHPDOC] Korrigera dåligt foto Magento\Directory\Model\AllowedCountries::getAllowedcountries()
   * _Korrigera anteckning_: PHPDoc för metoden Allowedcountries::getAllowedcountries() har korrigerats för att ge korrekt information, vilket gör dokumentationen tydligare och mer användbar. Tidigare innehöll PHPDoc för den här metoden felaktig information, vilket kan leda till förväxling eller missbruk av metoden.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/39246>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/pull/39241>
* _AC-13348_: [Utgåva] Tar bort kod för PHP-versioner som vi inte längre stöder.
   * _Korrigera anteckning_: Ta bort kod för PHP-versioner som inte längre stöds i Magento
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/39361>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/pull/39202>
* _AC-13417_: [Problem] Gör ImageMagick-adaptern kompatibel med php8 (implicit konvertering från flyttal till heltal)
   * _Korrigera anteckning_: Systemet garanterar nu kompatibilitet med PHP8 genom att hantera flyttal korrekt vid beräkning av bilddimensioner, vilket förhindrar fel som beror på implicit konvertering från flyttal till heltal. Tidigare kunde beräkningen av bildens dimensioner resultera i flyttal, som skulle orsaka ett fel om de var implicit avrundade.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/39402>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/pull/37362>
* _AC-13537_: [Problem] [PHPDOC] Korrigera felaktiga foton Magento\Framework\App\Config\ScopeConfigInterface
   * _Korrigera anteckning_: Den här uppdateringen korrigerar PHPDoc-anteckningarna i Magento\Framework\App\Config\ScopeConfigInterface så att de korrekt återspeglar typen för $scopeCode-argumentet för metoderna getValue och isSetFlag.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/39492>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/pull/39199>
* _AC-8662_: [Problem] Förbättra felloggningen
   * _Korrigera anteckning_: Systemet hämtar och loggar nu både STDERR och STDOUT för cron-processer, vilket ger värdefull diagnostikinformation i scenarier där kron-processer misslyckas. Tidigare spelades inga felmeddelanden in i cron-processer och STDERR och STDOUT för cron-grupper som körs i separata processer gick förlorade.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/37453>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/pull/32690>
* _ACP2E-3230_: Det går inte att ändra kolumnlängd via db_schema.xml när det gäller sekundärnycklar
   * _Korrigera anteckning_: Om du ändrar en kolumn med en sekundärnyckel via ett deklarativt schema uppstår inga fel med MariaDB
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/581b7ef1>
* _ACP2E-3361_: Vissa relationsposter sparas i DB när orderposten sparas
   * _Korrigera anteckning_: Innan korrigeringen av onödiga UPDATE-frågor utlöstes, vilket kan påverka prestandan negativt. Efter korrigeringen togs de onödiga UPDATE-frågorna bort.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/1366ae5e>
* _ACP2E-3375_: [CLOUD] I admin finns många javascript-fel i konsolen
   * _Korrigera anteckning_: Tidigare fanns det många javascript-fel i konsolen på administratörspanelen. Nu kommer det inte att finnas några JavaScript-fel i konsolen på administratörspanelen och alla JavaScript standardfunktioner kommer att köras utan några problem.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/d75cff27>
* _ACP2E-3387_: [Cloud] Magento: Kömeddelandet har tagits bort
   * _Korrigera anteckning_: Kömeddelanden rensas nu korrekt. Före korrigeringen kunde nya meddelanden ha tagits bort om rensningskömeddelandet kördes samtidigt eftersom SQL-kösystemet användes.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/d50f6b5d>

### Framework, UI Framework

* _ACP2E-3324_: Möjlighet att skriva över konfigurationsvärdet även om det är låst
   * _Korrigera anteckning_: Tidigare till den här korrigeringen kunde designkonfigurationen inte anges med kommandot bin/magento config:set och låsta värden kunde ändras genom att formuläret som visade dem ändrades. Efter korrigeringen av låsta värden som angetts från cli med —lock-env eller —lock-conf kan inte uppdateras längre.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/55615e61>

### GraphQL

* _ACP2E-2974_: Översättningar för kundreturattribut återspeglas inte i GraphQL API för respektive StoreView
   * _Korrigera anteckning_: Översättningar för kundreturattribut visas i GraphQL API för respektive StoreView.
Tidigare återspeglas inte kundreturattribut för respektive StoreView i GraphQL API.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/ec7e32a9>
* _ACP2E-3215_: [Cloud] Problem med användarautentisering och åtkomst med token på flera platser i konfigurationen för flera platser
   * _Korrigera anteckning_: GraphQl kundinformation och kundvagnsfrågor i installationsprogrammet för flera platser kontrollerar om kunden på en webbplats som inte är standard finns.
Tidigare arbetade frågan utan att kontrollera att kunden finns på en icke-standardwebbplats i konfigurationen av flera webbplatser.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/581b7ef1>
* _ACP2E-3255_: [GRAPHQL]-modellvärdet ska anges när customerCart hämtas
   * _Korrigera anteckning_: GraphQL kundvagnsfråga kan nu skapa en tom kundvagn även när offerten inte är tillgänglig i databasen. Tidigare misslyckades den här åtgärden på grund av landsvalideringsproblem när en tom kundvagn skapades.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/fd5cf3af>
* _AVS2E-3380_: [Önsklisteobjekt för GraphQl] visas via GraphQl men inte i butiken
   * _Korrigera anteckning_: Önskar produkter som inte visas korrekt när de begärs via GraphQL. Nu filtreras önskelisteprodukter baserat på den angivna butikskontexten.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/55615e61>
* _ACP2E-3404_: [GraphQL] Återställa inkonsekvent e-postlösenord för innehåll och ämne/länk
   * _Korrigera anteckning_: Problemet har lösts genom att simulera rätt butik där kundens konto är registrerat när begäran om lösenordsåterställning skickas, oavsett webbplatsarkivet.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/5184c067>
* _ACP2E-3419_: [Cloud] produkter GraphQL-frågan returnerar relaterade produkter som inte är tilldelade till den aktuella webbplatsen
   * _Korrigera anteckning_: Tidigare visades inte produkter som är relaterade till flera lager korrekt för produktfrågan för graphQL-frågan. När den här korrigeringen har tillämpats visas graphQL-frågor för produkter som är relaterade till flera butiker.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/078c387e>
* _ACP2E-3447_: Om du använder fel lagrings-ID i GraphQL header uppstår ett allvarligt minnesfel
   * _Korrigera anteckning_: Om du skickar fel lagringskod i en GraphQL-begäran leder detta inte längre till för stor minnesförbrukning.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/d50f6b5d>
* _ACP2E-3467_: [Cloud] 500 svar på tomt Graphql-svar på 2.4.7
   * _Korrigera anteckning_: Efter korrigeringen loggas inte ogiltiga grafikförfrågningar i filen exception.log.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/1984c61c>
* _LYNX-600_: Öka den högsta standardkomplexiteten för GraphQL-frågor till 1 000

### GraphQL, sökning

* _ACP2E-948_: Produktlista GraphQL query limited to total_count 10 000 products only
   * _Korrigera anteckning_: Efter korrigeringen är sökresultatet inte begränsat till 10000 produkter, det blir möjligt att hämta alla produkter som matchar sökvillkoren, även om antalet är mer än 10000.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/a4cf5e62>

### GraphQL, testramverket

* _ACP2E-3363_: Magento\GraphQl\App\GraphQlCustomerMutationsTest.php Integration Test failed
   * _Korrigera anteckning_: -
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/a4cf5e62>

### Importera/exportera

* _ACP2E-3172_: Knappen Importera saknas
   * _Korrigera anteckning_: Åtgärda problemet med att knappen Importera saknas efter datakontroller med korrekta och felaktiga poster i CSV-filen. Tidigare visades inte importknappen efter datakontroller med korrekta och felaktiga poster i CSV-filen.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/1819fe73>
* _ACP2E-3382_: Det går inte att importera den exporterade kundadressen
   * _Korrigera anteckning_: Importen av kundadressen fortsätter som förväntat. Tidigare godkändes inte valideringen av en kundadressimportfil om Dela kundkonton = Global, och det finns två webbplatser där standardwebbplatsen har en lista med begränsade länder och adressen som importeras är till en annan webbplats där tillåtna länder är olika
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/ec7e32a9>
* _ACP2E-3448_: [Cloud] Fel antal i CSV-fil gav inget fel
   * _Korrigera anteckning_: Nu genereras valideringsfel för icke-numeriska värden i kvantitetskolumnen vid import av Stock-källor. Om du importerar Stock-källor med ett icke-numeriskt värde i kvantitetskolumnen hade kvantiteten angetts till 0.
   * _GitHub-kodbidrag_: <https://github.com/magento/inventory/commit/5b21b7af>
* _ACP2E-3475_: Produktexport orsakar OOM även med minnesgräns på 4G
   * _Korrigera anteckning_: Före den här korrigeringen misslyckades produktexporten om produktattributen hade tusentals alternativvärden även med 4G tillgängligt minne. Efter den här korrigeringen bör produktexporten avsluta exporten av csv-filen.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/1984c61c>

### Import/export, prestanda

* _ACP2E-3476_: [Cloud] Produktimporttiden har ökat avsevärt
   * _Korrigera anteckning_: Före korrigeringen hade katalogimporten med över 10 000 poster försämrats avsevärt. Efter korrigeringen körs importen av katalogprodukten i rätt tid.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/87d012e5>

### Installera och administrera

* _AC-13242_: Magento-uppgraderingen misslyckas på MariaDB 11.4 + 2.4.8-beta1
   * _Korrigera anteckning_: Uppgraderingen bör utföras utan fel.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/7b336d0a>

### Lager/MSI

* _ACP2E-3335_: Det går inte att skicka beställningen när MSI-upphämtningsarkivet är aktiverat
   * _Korrigera anteckning_: Förbättrade lagerprestanda för att skapa leverans i händelse av många källor med hämtning i butik
   * _GitHub-kodbidrag_: <https://github.com/magento/inventory/commit/9f3e63d1>
* _ACP2E-3355_: Cron reindex misslyckas med att uppdatera produkttillgänglighet på klientsidan
   * _Korrigera anteckning_: Tidigare fanns produkterna inte i lager på klientsidan efter att bakgrundsorderstatusen uppdaterats via REST API. Efter att ha uppdaterat restorderstatusen via REST API visas nu produkterna som i lager.
   * _GitHub-kodbidrag_: <https://github.com/magento/inventory/commit/e6fe0aa7>
* _ACP2E-3357_: Det går inte att lägga till bilder i konfigurerbara när MSI är aktiverat.
   * _Korrigera anteckning_: Bildöverföring för konfigurerbar produkt kommer nu att fungera som förväntat när lagermodulen används. Tidigare fungerade inte bildöverföringen
   * _GitHub-kodbidrag_: <https://github.com/magento/inventory/commit/fdf409aa>

### Lager/MSI, Sök

* _ACP2E-3413_: Alla produkter indexeras med [ is_out_of_stock] = 1 när SKU inte är inställt som ett sökbart attribut
   * _Korrigera anteckning_: Efter korrigeringen är &quot;is_out_of_stock&quot; i katalogsökindexet korrekt, även om sku inte är sökbart.
   * _GitHub-kodbidrag_: <https://github.com/magento/inventory/commit/5b21b7af>

### Beställning

* _ACP2E-3311_: [Cloud] Det går inte att skapa order i en administratör på en butik om endast standardfaktureringsadressen inte har konfigurerats
   * _Korrigera anteckning_: Nu finns ett relevant felmeddelande,&quot;En kund med samma e-postadress finns redan på en associerad webbplats.&quot; visas om en kund inte har en standardfaktureringsadress och försöker skapa en order i en annan butik.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/d75cff27>
* _ACP2E-3416_: Administratörsförfrågningar om dubblettorder har skickats
   * _Korrigera anteckning_: Tidigare kunde användaren klicka på knappen &quot;Skicka beställning&quot; på administratörspanelen flera gånger eller aktivera den genom att trycka på Retur upprepade gånger, vilket orsakade fel vid dubbletter eller orderöverföringar. Nu kan du förhindra ytterligare åtgärder tills ordern har bearbetats fullständigt, så att bara en order skickas.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/5184c067>
* _ACP2E-3425_: Administratören kan fortfarande göra beställningar även utan betalningsmetod
   * _Korrigera anteckning_: Den betalningsmetod som valts tidigare behålls nu när betalningsmetoden visas igen i listan över tillgängliga betalningar.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/d50f6b5d>

### Order, betalningar

* _ACP2E-3233_: Administratören kan fortfarande göra beställningar även utan betalningsmetod
   * _Korrigera anteckning_: Tidigare kunde handlaren göra beställningar från adminpanelen utan att välja någon betalningsmetod. Nu måste handlaren ha en betalningsmetod för att kunna göra en beställning.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/fd5cf3af>

### Övriga

* _LYNX-426_: Rabatt_percentage beräknas inte för paketprodukter med dynamiskt pris
* _LYNX-485_: Paketprodukter visar fortfarande&quot;IN_STOCK&quot; när en av de paketerade produkterna inte finns i lager
* _LYNX-486_: not_available_message och only_x_left_in_stock visar inte samma tillgängliga lager
* _LYNX-488_: fältet original_row_total returnerar fel värde
* _LYNX-503_: Miniatyrbilder av grupperade produkter ska visas enligt konfigurationen     .
* _LYNX-510_: Fel vid fråga av selected_options i OrderAddress
* _LYNX-512_: original_item_price inkluderar inte rabatter
* _LYNX-530_: Meddelandet Inte tillgängligt visar inte tillgänglig lagerkvantitet
* _LYNX-532_: Statusen &quot;OUT_OF_STOCK&quot; returneras för Simple med anpassade alternativprodukter med flera alternativ
* _LYNX-533_: Fel (GQL): cart.itemsV2.items.product.custom_attributesV2 returnerar ett serverfel
* _LYNX-536_: order/date_of_first_order returnerar alltid null
* _LYNX-544_: Kunden får inte kunna annullera en delvis levererad order
* _LYNX-548_: Felkoder för orderannullering baserat på felmeddelandet
* _LYNX-581_: Flytta tillbaka cookie-relaterade egenskaper från privat till skyddad

### Andra utvecklingsverktyg

* _AC-12731_: CSP-problem i kombination med dev/css/use_css_critical_path
   * _Korrigera anteckning_: Nu läses CSS-filer in asynkront på utcheckningssidor, även när inställningen &#39;dev/css/use_css_critical_path&#39; är aktiverad, vilket säkerställer att sidorna återges med rätt CSS-format. Tidigare förhindrade en begränsad CSP (Content Security Policy) infogad JavaScript från att köras, vilket medförde att CSS-filer inte lästes in som förväntat.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/39020>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/pull/39040>
* _AC-13398_: Det går inte att generera gränssnittsmetoden korrekt med den virtuella typen för att konfigurera plugin-programmet i kommandot :di:kompilera
   * _Korrigera anteckning_: Systemet genererar nu korrekt spärrmetoder när en virtuell typ används för att konfigurera ett plugin-program, vilket ger konsekventa resultat oavsett om det är förkompilerat eller körtidskompilerat. Tidigare genererade systemet felaktiga resultat vid förkompilering jämfört med körtidskompilering.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/33980>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/pull/38141>
* _ACP2E-3441_: Det går inte att hämta filer från datainsamlaren
   * _Korrigera anteckning_: När du hämtar säkerhetskopian visas inte längre en tom sida i stället för att filen hämtas.

### Betalningar

* _ACP2E-3143_: PayPal-orderåterbetalning resulterar i dubblettkreditnota
   * _Korrigeringsanteckning_: Korrigerat problem med samtidig användning av IPN-skapade kreditnotor för PayPal-betalningstjänsten.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/d01ee51e>
* _ACP2E-3163_: Kundprisregeln fungerar inte för PayPal
   * _Korrigera anteckning_: Korrekt belopp visas på PayPal-sidan när rabatt tillämpas med betalningsmetod
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/7377de59>
* _ACP2E-3208_: [Cloud] Användare med en specifik roll kan inte logga in
   * _Korrigera anteckning_: Administratörsanvändare med roll som endast innehåller PayPal-avsnittsåtkomst kan nu logga in utan fel
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/66dea0de>

### Prestanda

* _AC-11932_: Problem med standardinställningar för produktattribut
   * _Korrigera anteckning_: Nu kan användare avmarkera ett standardalternativ för ett produktattribut, vilket säkerställer att attributet inte alltid har en standarduppsättning. Tidigare fanns det inget sätt att avmarkera ett produktattribut när ett standardvärde angavs, vilket innebar att attributet alltid hade en standarduppsättning.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/38703>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/7d5e3906>
* _AC-13471_: Stöd för Symfonys CommandLoaderInterface i Magento CLI
   * _Korrigera anteckning_: Den här ändringen minskar initieringstiden för Magento CLI-appen genom att tillåta fördröjd initiering av kommandon tills de behövs.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/29266>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/pull/29355>

### Produkt

* _AC-13173_: [Problem] Korrigeringstyp i PHPDoc-block
   * _Korrigera anteckning_: Systemet tar nu bort en okänd refererad variabel i PHPDoc korrekt för $helper-variabeldeklarationen, vilket gör koden tydligare och exaktare. Tidigare orsakade den här okända refererade variabeln i PHPDoc förvirring och potentiella fel i koden.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/38961>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/pull/38940>
* _AC-13423_: [Problem] Åtgärdat brutet paket och hämtningsbar layout för produktsidor i Magento >= 2.4.7
   * _Korrigera anteckning_: Layouten för programpaket och hämtningsbara produktsidor har korrigerats, vilket ger en konsekvent och korrekt visning på alla enheter. Tidigare hade dessa sidor layoutproblem på grund av en omorganisering av produktinformationsmediablocket.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/39403>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/6cfb9b6b>
* _ACP2E-3471_: [Cloud] Produkter i kategori - Lägg till produkter - Tilldela - Markera alla
   * _Korrigera anteckning_: Användare kan nu markera eller avmarkera produkter med hjälp av växlingsknappen.

### Kampanj

* _ACP2E-3139_: Förs.regel med rabattkvantitetssteg (Buy X)-attribut leder till att andra regler inte tillämpas
   * _Korrigera anteckning_: I kundvagnsprisregeln avbryts inte tidigare tillämpade regler om kvantiteten av produkten i vagnen inte räcker för att regeln ska tillämpas.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/d01ee51e>
* _ACP2E-3331_: Prestandaproblem på kundprisregel - modulen Förhandsförsäljningsregel
   * _Korrigeringsanteckning_: Saknade DB-index för AdvancedSalesRule-filter har lagts till
* _ACP2E-3332_: Utfärda försäljningsregler med fast beloppsrabatt och &quot;maximal mängdrabatt används för&quot;
   * _Korrigera anteckning_: Ett problem med rabatt på kundvagnsregler har korrigerats när rabatt på fast belopp har konfigurerats för en begränsad produktkvantitet är vagnen. Tidigare användes värdet för maximal mängdrabatt till för att beräkna den aktuella artikelns pris i kundvagnen, inte bara för att beräkna regelns rabatt.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/581b7ef1>
* _ACP2E-3342_: [CLOUD] Magento-uppgradering orsakade att kuponger blev skiftlägeskänsliga
   * _Korrigera anteckning_: Före korrigeringen var du tvungen att skriva in kupongkoden exakt som den var konfigurerad med hänsyn tagen till versaler eller gemener. Kupongen valideras nu i serverdelen oberoende av koden i versaler eller gemener.
* _ACP2E-3349_: kundvagnsreglerna &quot;Fast beloppsrabatt för hela kundvagnen&quot;  Åtgärden tillämpar rabatter felaktigt
   * _Korrigera anteckning_: Kupongkoder valideras korrekt oavsett versaler och gemener när de används för att skapa i administrationsområdet. Före validerades inte kupongkoden om den inte matchade det exakta bokstavsfallet för den konfigurerade kundvagnsregelkoden.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/581b7ef1>
* _ACP2E-3374_: I Backend lagras standardvärden för produktattribut (i stället för förväntade administratörsvärden)
   * _Korrigera anteckning_: I backend används nu administratörsvärden i stället för standardbutiksvärden för produktattribut.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/5184c067>
* _ACP2E-3377_: Cart-reglerna &quot;Fast beloppsrabatt för hela kundvagnen&quot; tillämpar rabatter felaktigt när paketprodukter läggs till
   * _Korrigeringsanteckning_: Kundvagnsregler med fast belopp tillämpades inte korrekt för paketprodukter. När man beräknar det totala rabattbeloppet beaktas även underordnade paketprodukter, vilket ger en korrekt rabattberäkning.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/1366ae5e>
* _ACP2E-3403_: Rabatt beräknas inte enligt kundprisreglerna
   * _Korrigera anteckning_: Rabatter med fast belopp beräknas nu korrekt. Före korrigeringen hade rabatterna inte summerats korrekt för paketprodukterna.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/0b488dd1>
* _ACP2E-3406_: Kapslade kategorier i regelvillkor visas inte
   * _Korrigera anteckning_: Ett problem har korrigerats när kapslade kategorier under kategori 3 inte visas i marknadsföringsregler för kategorivillkor
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/88660e79>
* _ACP2E-3432_: usage_limit och uses_per_customer uppdaterar inte i salesrule_coupon-tabellen
   * _Korrigera anteckning_: Om du uppdaterar användningen per kupong och användningen per kund i kundvagnsprisregeln kommer det nu att påverka befintliga automatiskt genererade kuponger. Tidigare påverkades endast nya kuponger
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/88660e79>
* _ACP2E-3456_: Kundprisregeln tar inte hänsyn till överordnad kategori när den använder villkoret &quot;lika med eller större än&quot;.
   * _Korrigera anteckning_: Kundprisregler hanterar nu den överordnade kategorin korrekt när den används i avancerade villkor
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/93359343>
* _ACP2E-3463_: Ogiltig rabattberäkning med prioritet
   * _Korrigeringsanteckning_: I fallet med ett fast belopp som tillämpas för hela kassarabattypen beräknades inte beloppet korrekt för kundvagnsartiklar som redan rabatterats av en tidigare kampanj. Rabatterna summeras.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/078c387e>
* _ACP2E-3498_: Felaktigt rabattvärde när flera kundprisregler tillämpas samtidigt med rabatterade/specialprissatta produkter
   * _Korrigeringsanteckning_: Före korrigeringen tillämpades inte fasta belopp för hela kundvagnsregler korrekt om fler än en tillämpades. Nu används rabattreglerna för fast belopp korrekt.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/1984c61c>

### Returnerar

* _ACP2E-3330_: [CLOUD] Administratörsanvändare med begränsad behörighet kan se returmenyn och knapparna
   * _Korrigera anteckning_: Användare med begränsad administratör har nu inte åtkomst till RMA-relaterade kontroller (menyer och knappar).
Administratörsanvändare som tidigare var begränsade kunde se returmenyn och knapparna.
* _ACP2E-3443_: Returskärmen är felaktig när skärmen uppdateras
   * _Korrigera anteckning_: Användaren kan uppdatera sidan utan att uppleva skärmförvrängning.

### Försäljning

* _AC-13750_: Summan av totalsummor och bassummor matchar inte med testresultatsteg
* _AC-13751_: Andra kundvagnsprisregeln används inte om Första kundvagnsregeln redan används

### Sök

* _AC-13053_: Hämtar &quot;Ange ett sökord och försök igen.&quot; fel på avancerad söksida i storefront i 2.4.8 beta1
   * _Korrigera anteckning_: Systemet visar nu sökresultaten korrekt på sidan Avancerad sökning när ett produktattribut är inställt på Nej. Om du tidigare angav ett produktattribut som &quot;Nej&quot; och gjorde en sökning, skulle ett felmeddelande visas: &quot;Ange ett sökord och försök igen&quot;.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/3ea26621>
* _AC-13721_: magento/module-open-search är beroende av en grenen open search-php som inte finns
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/05dc0bbf>
* _ACP2E-3362_: tabellen search_query har stor betydelse för inläsningstidens förskjutning när den är mycket stor
   * _Korrigera anteckning_: Inläsningstiden för söklistsidor har förbättrats. Före korrigeringen försenades söklistsidan på grund av en ooptimerad fråga.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/55615e61>

### Säkerhet

* _ACP2E-3273_: ReCaptcha V2 visas felaktigt vid utcheckning för tyska språk
   * _Korrigera anteckning_: Tidigare visades reaptcha från undere-postadressen i utcheckningen som oformaterad för språk med långa ord, som german. Därefter ser reaptcha ut på samma sätt som alla recaptcha-element från resten av områdena.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/7377de59>
* _ACP2E-3300_: Captcha vid administratörsinloggning kräver inte interaktion för vissa användare
   * _Korrigera anteckning_: ReCaptcha för administratörsinloggning verifieras som förväntat

### Leverans

* _AC-12938_: UPS REST &quot;sandbox&quot; och &quot;prod&quot; installationsuppdateringar i devdoc
* _ACP2E-3340_: FedEx Track API fungerar inte med REST-autentiseringsuppgifter
   * _Korrigera anteckning_: Tidigare FedEx-integrering krävde inte ytterligare API-nycklar för spårnings-API. Nu har en ny konfiguration lagts till som stöd för API-nycklar för spårning.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/ec7e32a9>
* _ACP2E-3354_: [Cloud] Förhandlingsfrekvenser för FedEx returneras inte för REST
   * _Korrigera anteckning_: Före korrigeringen har FedEx-kontospecifika frekvenser där de inte skickats på svaret, även via FedEx-dokumentation som de borde ha skickats. Efter korrigeringen skickas de kontospecifika priserna på svaret genom att begäran ändras från vår sida.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/55615e61>

### Mellanlagring och förhandsvisning

* _ACP2E-3453_: Det går inte att uppdatera schemalagd uppdatering när unikt kategoriattribut används
   * _Korrigera anteckning_: Ett problem har korrigerats där en schemalagd uppdatering för en kategori inte var möjlig om kategorin hade ett unikt attribut
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/078c387e>

### Moms

* _ACP2E-3193_: FPT (Fixed Product Tax) fungerar inte med konfigurerbara produkter
   * _Korrigera anteckning_: FPT för konfigurerbara produktvariationer fungerar korrekt.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/ec7e32a9>

### Testramverk

* _AC-13362_: [Problem ] PHPDoc-korrigeringsstavning
   * _Korrigera anteckning_: Systemet identifierar nu korrekt inaktuella metoder i IDE:er på grund av en stavningskorrigering i PHPDoc. Tidigare orsakade ett stavfel i PHPDoc att vissa metoder inte kändes igen som inaktuella.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/31399>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/pull/31398>
* _AC-13478_: MAGETWO-95118: Kontrollera beteendet med den beständiga kundvagnen när sessionen har upphört
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/7d5e3906>
* _AC-13716_: Integrationstester misslyckades Magento\NegotiableQuote\Controller\Quote\DownloadTest::testCompanyManagerDownloadWithNQSubPermission
* _ACP2E-3458_: [MFTF] StorefrontCheckoutProcessForQuoteWithoutNegotiatedPricesTest
   * _Korrigera anteckning_: Korrigerade MFTF-filer
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/078c387e>

### UI Framework

* _AC-12432_: Fält för UI-komponentfil
   * _Korrigera anteckning_: Systemet validerar nu filfältet korrekt i ett UI-komponentformulär, så att formuläret kan skickas utan fel när en fil väljs. Tidigare misslyckades valideringen även om en fil valdes, vilket förhindrar att formuläret skickas.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/38908>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/pull/39004>
* _AC-12645_: [Problem] Förbättrat datumformat i js-konsolen: växla från 12 till 24 timmar...
   * _Korrigera anteckning_: Förbättrat datumformat i js-konsolen: växla från 12 till 24 timmar
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/38983>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/pull/38972>
* _AC-12650_: [Problem] att lägga till sourceMap-generering för färre filer i utvecklarläge
   * _Korrigera anteckning_: Systemet genererar nu källkartor för mindre filer i utvecklarläge, vilket gör det enklare att identifiera källan till ett format. Tidigare var det en utmaning att identifiera källan till en stil när systemet kördes i utvecklarläge med mindre kompilering på serversidan.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/38982>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/pull/38977>
* _AC-13459_: Inkonsekvent beteende vid sortering utanför lagret med minimalt lagertröskelvärde
   * _Korrigera anteckning_: Systemet sorterar nu produkter i katalogen korrekt baserat på lagernivåer, enligt det angivna minimikravet för Stock och flyttar objekt utanför lagret till listans nedre del på ett konsekvent sätt. Tidigare var sorteringsfunktionen inkonsekvent, med objekt som inte alltid visas i rätt ordning baserat på deras lagernivåer, och ändringar i sorteringen kan inträffa oförutsägbart efter att kategorihierarkin har sparats, uppdaterats eller ändrats.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/47b448e2>
* _AC-13472_: Förslag till förbättrad felrapportering för problem med inläsning av require.js
   * _Korrigera anteckning_: Den här PR-funktionen förbättrar felmeddelandet när en komponent inte kan läsas in med nödvändiga inställningar.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/36761>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/pull/38971>
* _AC-9168_: [Utgåva] Ta bort översiktssammanfattning för onödiga skript
   * _Korrigera anteckning_: Systemet optimerar nu sidinläsningstiden genom att ta bort onödiga JavaScript-skript från klassificeringsavsnittet, i stället för att använda infogade CSS-format för en mer effektiv och läsbar kod. Tidigare kunde användningen av JavaScript-skript för klassificeringsavsnittet göra sidinläsningen långsammare.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/37776>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/pull/34643>
* _ACP2E-3367_: Platshuvud | Specialtecken som bryter kundens välkomstavsnitt
   * _Korrigera anteckning_: Efter korrigeringen visas specialtecken korrekt i välkomstavsnittet för kunder.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/1366ae5e>
