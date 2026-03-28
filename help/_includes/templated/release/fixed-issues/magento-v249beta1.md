---
source-git-commit: 7054a5286f01e26e324401f4d8505e4e0faed93e
workflow-type: tm+mt
source-wordcount: '24355'
ht-degree: 0%

---
# Magento Open Source åtgärdade problem (v2.4.9-beta1)

## Åtgärdade problem i v2.4.9-beta1

Vi har åtgärdat 501 problem i Magento Open Source 2.4.9-beta1-kärnkoden. En deluppsättning av de åtgärdade problemen som ingår i den här versionen beskrivs nedan.

### API:er

#### Specialpris till datum valideras felaktigt för applySpecialPrice

Systemet fungerar som det ska när det gäller specialpriset och produktens specialpris upphör att gälla det datum som anges av administratören eller tredjepartssystemet av REST API

_AC-13130 - [GitHub-problem](https://github.com/magento/magento2/issues/39169) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/39690)_

#### [WebAPI] - bekräftelse av e-post från kund via WebAPI-paradox

Ett problem har korrigerats där kunder inte kunde aktivera sina konton via WebAPI på grund av en auktoriseringsparadox som kräver en token före bekräftelse. Uppdateringen gör det möjligt för obekräftade kunder att aktivera sina konton genom API:t, vilket ger ett konsekvent och funktionellt bekräftelseflöde.

_AC-13281 - [GitHub-problem](https://github.com/magento/magento2/issues/39255) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/c95ed7d7)_

#### Faktureringsadressfel saknas i Admin Dashboard när en order skapas via REST API med endast betalningsinformation

Ett problem där beställningar kunde skapas via API utan faktureringsadress har korrigerats, vilket medförde att kontrollpanelen kraschade.
Nu är beställningar utan faktureringsadress begränsade och skapas inte längre.

_AC-14049 - [GitHub-problem](https://github.com/magento/magento2/issues/39651) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/36d4d6fb)_

#### Product Add to Cart issue in Rest API

Ett problem har korrigerats där produkter som inte har tilldelats till en viss webbplats fortfarande kunde läggas till i kundvagnen och köpas.
Nu visas ett felmeddelande:&quot;Produkten som du försöker lägga till är inte tillgänglig.&quot;

_AC-15054 - [GitHub-problem](https://github.com/magento/magento2/issues/40029) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/f5cc09fc)_

#### Etiketten för attributalternativ skrivs över vid uppdatering av butiksetiketter

Ett problem har korrigerats där en uppdatering av ett flervalsproduktattribut via REST API skulle skriva över alla store_labels och ta bort befintliga butiksspecifika etiketter.
När du uppdaterar standardetiketten för butiksvyn sammanfogar nu Magento de angivna etiketterna med befintliga i stället för att skriva över dem helt.
Detta garanterar att butiksspecifika etiketter för andra butiksvyer förblir intakta efter uppdateringar.

_AC-15208 - [GitHub-problem](https://github.com/magento/magento2/issues/40093) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/36d4d6fb)_

#### [Utgåva]: Det finns redan ett svar på det klarlagda attributalternativet

Systemet ersatte nu den besvärliga frasen&quot;Hämta nytt filnamn om det redan finns&quot; med en tydligare och grammatiskt korrekt version:&quot;Hämta ett nytt filnamn om det redan finns ett&quot;. Detta förbättrar läsbarheten och användarförståelsen.
Samma för attributalternativets svar.

_AC-15473 - [GitHub-problem](https://github.com/magento/magento2/issues/39943) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/39941)_

#### Internt serverfel i /V1/products/special-price API Endpoint

Ett problem har korrigerats där felaktigt formaterade begäranden till /V1/products/special-price och relaterade API:er för prissättning returnerade ett internt 500-serverfel på grund av ett TypeError-fel som är null.
API:erna validerar indata korrekt och returnerar 400-fel för ogiltiga nyttolaster, vilket förbättrar felhanteringen och API-tillförlitligheten.

_AC-6419 - [GitHub-problem](https://github.com/magento/magento2/issues/35934) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/a7ef6300)_

#### Internt serverfel i API-slutpunkten `/V1/order/{orderId}/ship`

Systemet åtgärdar nu det interna serverfelet i API-slutpunkten `/V1/order/{orderId}/ship` och returnerar ett 400-fel eftersom begäran har fel format.

_AC-6420 - [GitHub-problem](https://github.com/magento/magento2/issues/35931) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/38282)_

#### Internt serverfel i /V1/creditmemo API Endpoint

Ett problem har korrigerats där felaktigt utformade begäranden till API:t /V1/creditmemo returnerade ett internt 500-serverfel.
API:t validerar nu begäran korrekt och returnerar 400-fel för ogiltiga nyttolaster, vilket förbättrar felhanteringen och stabiliteten.

_AC-6422 - [GitHub-problem](https://github.com/magento/magento2/issues/35924) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/a7ef6300)_

#### Återstående API och Magento backend använder olika valideringsmetoder för attribute_code när nya attribut skapas

Inkonsekvensen har korrigerats där Magento Admin tillåter versaler i attribute_code, men REST API avvisade dem när produktattribut skapades.
Nu följer både Admin och REST API samma validering, vilket gör att du kan skapa attribut med versaler.

_AC-6660 - [GitHub-problem](https://github.com/magento/magento2/issues/33138) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/8670a2b4)_

#### Olika validering mellan skapande av attribut och uppdatering via REST API

Ett problem har korrigerats där inkonsekvent validering vid skapande av attribut via REST API resulterade i att en felaktig backend_type tilldelades.
Nu ställer systemet in rätt backend-typ när den är giltig, genererar ett undantag för ogiltiga värden eller återgår korrekt om den inte anges, vilket säkerställer ett konsekvent attributbeteende.

_AC-6885 - [GitHub-problem](https://github.com/magento/magento2/issues/36327) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/64823f95)_

#### Felformaterad begärandetext eller felaktiga parametrar orsakar &quot;Internt serverfel&quot;

Felformaterade begärandeinstanser eller parametrar returnerar nu ett tydligt 400-svar för Ogiltig begäran.
Tidigare resulterade sändning av felformaterade begärandetexter eller parametrar till olika REST API-slutpunkter (som /V1/carts/search, /V1/orders, /V1/products, etc.) i ett allmänt &quot;Internt serverfel&quot; (500), vilket gjorde det svårt att diagnostisera indataproblem.
Nu returnerar Adobe Commerce svaret&quot;400 Bad Request&quot;, vilket ger tydligare feedback när begäranden är ogiltiga.

_AC-746 - [GitHub-problem](https://github.com/magento/magento2/issues/32784) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/f1adb44e)_

#### `/orders`(eller `/orders/:id`) slutpunkt saknar fälten &quot;state&quot; och &quot;status&quot;

Ett problem har korrigerats där API-svaren `/orders` och `/orders/{id}` utelämnade tillstånds- och statusfälten när databasvärdena var null.
Nu returneras båda fälten konsekvent i svaret, vilket säkerställer överensstämmelse med API-dokumentationen och förbättrar datatillförlitligheten.

_AC-9244 - [GitHub-problem](https://github.com/magento/magento2/issues/37807) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/01cee3c3)_

#### Async Bulk Operation är fortfarande i öppet läge för async.magento.configur.product.api.optiondatabase.interface.save.post

Massor-API-slutpunkter genererar nu ett fel om begärandetexten inte är en matris, vilket kräver att bulkartikelnycklar är siffror i följd från 0. Tidigare uppdaterades inte bulkartikelstatus på grund av den godtyckliga artikelnyckeln som skickades i bulkbegäran.

_ACP2E-3544 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/9608ca21)_

#### [REST-fel för API:t ] för värdet is_subscribed som inte beaktas från det aktuella arkivet med searchCriteria

API REST-kundfrågan hämtar rätt &quot;is_subscribed&quot;-värde från rätt butik med hjälp av searchCriteria
Tidigare beaktades inte arkivet vid hämtning av värdet is_subscribed i API:ts REST-kundfråga.

_ACP2E-3621 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/9608ca21)_

#### async.operations.all kan skapa flera poster för 1 SKU

Samtidiga begäranden om att spara och uppdatera samma produkt har nu serialiserats för att förhindra konkurrensförhållanden som kan leda till inkonsekventa data eller dubblerade produkter

_ACP2E-3744 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/520f9e30)_

#### Ordningen &quot;base_row_total&quot; och &quot;row_total&quot; visar priset för en artikel i REST API-svar

REST api-svar för orderdetaljer innehåller nu korrekta värden för attributen &quot;base_row_total&quot; och &quot;row_total&quot; om flera objekt sorterades

_ACP2E-3874 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/4ca73607)_

#### REST API-slutpunkt export-stock-salable-quet returnerar felaktigt antal poster total_count

Ett problem med sidnumrering i API:t för lagerexportlagersaldo där total_count felaktigt begränsades till sidstorleken har åtgärdats. Tidigare, när du använde slutpunkten /rest/all/V1/layer/export-stock-salable-qty/website/base med sidnumreringsparametrar som page_size=5, skulle fältet total_count i svaret returnera 5 i stället för det faktiska antalet produkter som matchar sökvillkoren. Efter den här korrigeringen återspeglar fältet total_count nu korrekt det totala antalet produkter som är tillgängliga oavsett page_size-parametern, vilket säkerställer ett konsekvent sidnumreringsbeteende för alla Magento REST API-slutpunkter.

_ACP2E-4086 - [GitHub-kodbidrag](https://github.com/magento/inventory/commit/5632fb5e)_

#### Valideringsproblem med anpassade alternativ-ID:n i REST API:er för kundvagnsobjekt.

REST API:er V1/gästcarts/&lt;cartId>/items/ and V1/carts/mine/items/ validerar nu &quot;product_options.extension_attributes.custom_options.*.option_id&quot; för att säkerställa att den refererar till ett giltigt option_id för artikelvagnsartikeln SKU. Tidigare bearbetades och sparades den här parametern i databasen utan validering.

_ACP2E-4138 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/a1c57b2e)_

#### När produkten hämtas från varukorgen och butikshuvudet ändras inte

GraphQL customerCart-frågan returnerar nu produktattributvärden enligt butikens rubrikvärde. Tidigare återspeglade inte ändringen av butikshuvudet när en produkt hämtades från kundvagnen via GraphQL det uppdaterade språket, vilket resulterade i inkonsekvent lokalisering.

_ACP2E-4227 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/6e134409)_

#### REST API /media endpoint failed for Gift Card products - returns &quot;The product cannot be saved&quot;

Före korrigeringen fick du skapa presentkortsprodukter som inte innehöll något belopp i det globala omfånget. Med korrigeringen har en validering lagts till som söker efter belopp i globalt omfång.

_ACP2E-4395 - [GitHub-problem](https://mcstaging.panini.it/shp_ita_it/)_

### API:er, kundvagn och utcheckning

#### Verifiering på serversidan för leveransinformation fungerar inte med REST API

Korrigerade ett fel i REST API där verifieringen av leveransadressinformation inte följde den attributkonfiguration som definierats i Admin-serverdelen. Valideringen följer nu de konfigurerade inställningarna korrekt.

_ACP2E-4156 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/45cbf9b6)_

### API:er, katalog

#### Ta bort standardslutpunkt för prisnivå för webbplatser/butiker

Om du tidigare tog bort standardbaswebbplatsen och använde den sekundära webbplatsen som standardwebbplats uppstod ett fel när priset för den sekundära webbplatsen skulle uppdateras. När du har tillämpat den här korrigeringen kan skiktpriset uppdateras även om baswebbplatsen tas bort eller inaktiveras.

_ACP2E-4334 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/0a3b7032)_

### API:er, Framework

#### RedisRequestLogger\RedisClient (hastighetsbegränsare) undantag på programservern

Efter korrigeringen kan funktionen för hastighetsbegränsning användas tillsammans med GraphQL Application Server om PHP-tillägget är installerat.

_ACP2E-4237 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/e885088b)_

### API:er, importera/exportera

#### Async Fvoice Refund API skapar offlineåterbetalningar i stället för onlineåterbetalningar

Åtgärdade asynkrona återbetalningsåtgärder där återbetalningsbegäranden med parametern `is_online` inte bearbetades korrekt.

_ACP2E-4394 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/61c96348)_

### API:er, ordning

#### [CLOUD] Orderinformationsproblem med radsummeutseende för order 000075568

Korrigerar problemet där värdet row_total_incl_tax i order-API-svaret returnerades som ett nästan noll restvärde i stället för 0,00 när ett objekt helt rabatterades.

_ACP2E-3950 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/462ede94)_

### Konto

#### [Problem] Åtgärda skrivfel i mallalternativen för katalogwidget

Systemet korrigerar nu skrivfel i mallalternativen för katalogwidget.

_AC-11576 - [GitHub-problem](https://github.com/magento/magento2/issues/38185) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/38178)_

#### [Problem] Onödigt avstånd i backend-stödrastret har tagits bort

Systemet tar nu bort onödiga avstånd i backend-stödrastret när det finns markerade objekt

_AC-11579 - [GitHub-problem](https://github.com/magento/magento2/issues/38502) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/32622)_

#### Den sparade kundgruppskoden matchar inte indata när flerbytetecken används

Korrigerade ett problem där kundgruppskoder som använder multibytetecken trunkerades och inte matchade det angivna värdet. Uppdateringen säkerställer att alla indata sparas korrekt, vilket ger möjlighet att skapa kundgrupper med multibytenamn korrekt.

_AC-13335 - [GitHub-problem](https://github.com/magento/magento2/issues/39342) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/a06a4a57)_

#### Problem vid uppdatering av kundens e-post på Admin Panel med ö och swiss-domän

På Admin Panel kan man nu skicka e-postmeddelanden med specialtecken och .swiss-domäner.
Tidigare gick det inte att uppdatera ett e-postmeddelande till en adress som max@möstermann.swiss, eftersom det uppstod fel om ogiltiga värdnamn och TLD.
AC-13409

_AC-13409 - [GitHub-problem](https://github.com/magento/magento2/issues/39394) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/d3ea191d)_

#### Växeln för prenumerationsaktiverade nyhetsbrev fungerar inte per webbplats/butik

Systemet hanterar prenumerationer med nyhetsbrev korrekt när vi har flera webbplatser/butiksgranskningar när det inaktiverats på global nivå

_AC-14283 - [GitHub-problem](https://github.com/magento/magento2/issues/39751) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/39752)_

#### [Utgåva] Borttagen e-postexponering

Systemet visar nu Visa ett felmeddelande som anger ett felaktigt e-postmeddelande om den angivna e-postadressen inte krävs för att bekräfta kontot, oavsett om kunden finns eller inte.

_AC-14561 - [GitHub-problem](https://github.com/magento/magento2/issues/39574) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/39570)_

#### Det går inte att rensa kommentar för önskelisteobjekt via `updateProductsInWishlist` GraphQL-mutation

Ett problem där önskelistekommentarer inte uppdaterades via GraphQL-mutationer har korrigerats.
Nu uppdateras kommentarerna korrekt och återspeglas både i API-svaret och i butiken.

_AC-14682 - [GitHub-problem](https://github.com/magento/magento2/issues/39911) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/36d4d6fb)_

#### Produkten borttagen på mobilen visas fortfarande i avsnittet Mini Compare på webben tills den loggas in igen

Systemet tar nu bort produkten omedelbart från alla jämförelsevyer på både mobilen och webben, inklusive avsnittet för minijämförelse.

_AC-14703 - [GitHub-problem](https://github.com/magento/magento2/issues/39905) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/40023)_

#### Visa prefix-/suffixinställning som ignoreras om den är inställd på Nej

Ett problem har korrigerats där kundnamnsprefixet/suffixet fortfarande visades i order även när det är inaktiverat i konfigurationen.
Prefix-/suffixvärden tas bort från ordningsinformation baserat på konfigurationsinställningen.

_AC-15074 - [GitHub-problem](https://github.com/magento/magento2/issues/40036) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/a3b1abc2)_

#### Kundkontoregister i Stock: e-postadressformat konverteras med ett annat domänformat

Felet åtgärdade ett problem där kundmeddelanden med specialtecken i domänen (t.ex. tec55241@adòbe.com) konverterades automatiskt till punycode-format (tec55241@xn—adbe-mqa.com).
I Magento 2.4.9-alpha3 säkerställer korrigeringen att dessa e-post-ID:n förblir oförändrade och giltiga och förhindrar leveransfel.

_AC-15177 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/68a45d0a)_

#### Valideringsmeddelanden saknas (bildfel) i registreringsformuläret

Ett problem har korrigerats där obligatoriska fält på sidan där kundkontot skapades inte visade några valideringsmeddelanden när de lämnades tomma.
Nu visas korrekta felmeddelanden för alla tomma eller felaktiga fält.

_AC-15185 - [GitHub-problem](https://github.com/magento/magento2/issues/40076) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/36d4d6fb)_

#### Modal titel för annullering av order saknar översättning

Systemet åtgärdar nu en saknad översättning i orderns spärrningsmodal på lagerframsidan. När en kund klickar på knappen Avbryt på sidan Mitt konto > Mina beställningar visas en modal fråga om en annulleringsorsak. Den modala titeln var dock tidigare hårdkodad och inte översättningsbar. Den här ändringen garanterar att den modala titeln använder en korrekt översättningsmetod.

_AC-15260 - [GitHub-problem](https://github.com/magento/magento2/issues/40098) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/40100)_

#### Problem efter inloggning i magento 2.4.8-p1

Korrigerat problem i Magento 2.4.8-p1 där länken Skapa ett konto fortfarande var synlig på startsidan efter inloggningen.
Länken döljs nu korrekt efter inloggning, vilket överensstämmer med andra sidor.

_AC-15292 - [GitHub-problem](https://github.com/magento/magento2/issues/40120)_

#### [Problem] Ange isSecureArea innan kund tas bort

Systemet fungerar nu som det ska och denna PR-uppsättning är SecureArea för borttagningsprocessen och kunden kan registrera sig igen.

_AC-15723 - [GitHub-problem](https://github.com/magento/magento2/issues/40211) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/38462)_

#### [Borttagningsåtgärden i molnet] tillåts inte för aktuellt områdesfel när kundkonton skapas

När korrigeringen har sparats returnerar en kund med en ogiltig adress ett meddelande som beskriver orsaken till invaliditeten i stället för irrelevant&quot;Delete-åtgärden är förbjuden för aktuellt område&quot;.

_ACP2E-3791 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/6ea61121)_

#### [B2B] Webapi-begäranden blir en oändlig slinga för inloggade kunder när eav-cachen är inaktiverad

Efter korrigeringen kommer inaktivering av eav-cachen inte att leda till en oändlig slinga under vissa REST-begäranden.

_ACP2E-4191 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/45cbf9b6)_

#### Fel vid inläsning av vissa nationella inställningar

Ett problem har korrigerats där det inte gick att skapa ett kundkonto när det arabiska språket användes och attributet Födelsedatum var inställt på att visas i butiken. Kontot kan nu skapas i den här konfigurationen.

_ACP2E-4311 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/2687b487)_

#### Felaktigt datum vid uppdatering av kontoinformation

Kunder kan nu uppdatera sitt konto korrekt när de använder den arabiska språkversionen. Tidigare gjordes ett försök att spara kontoinformationen. Födelsedatumet misslyckades på grund av ett ogiltigt datumfel.

_ACP2E-4344 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/31258bf6)_

### Konto, administratörsgränssnitt

#### [Cloud] Ingen sådan entitet med cartId

Ett problem har korrigerats där inloggning som kund med två företagsadministratörskonton i samma session orsakade felet&quot;Ingen sådan entitet med cartId&quot;.

_ACP2E-4137 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/e885088b)_

#### Kunden skapar felmeddelanden i formulär inte översätts

Ett problem har korrigerats där felmeddelanden från kundvalideringen inte översattes och formaterades korrekt mellan olika gränssnitt. Valideringsfel visar nu korrekt översatta meddelanden i alla delar av programmet: storefront, adminhtml, rest api och graphql.

_ACP2E-4354 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/31258bf6)_

### Administratörsgränssnitt

#### Kategoriproduktrutnät > Status- och synlighetskolumner är tomma vid sortering efter namn

Korrigerade ett problem där status- och synlighetskolumnerna verkade tomma i rutnätet för kategoriprodukter vid sortering efter produktnamn.
I rutnätet visas nu alla kolumndata korrekt efter sorteringen, vilket ger korrekt produktinformation på adminpanelen.

_AC-10659 - [GitHub-problem](https://github.com/magento/magento2/issues/38233) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/3cf1a106)_

#### E-postmallens butiksväxlare

Ett problem har korrigerats där butiksväljaren i förhandsvisningen av e-postmallen för nyhetsbrev inte öppnades när användaren klickade på på grund av en inaktuell jQuery-kod. Uppdateringen av load-händelsen återställde korrekta funktioner, vilket ger användarna tillgång till butiksväxlaren som förväntat.

_AC-12334 - [GitHub-problem](https://github.com/magento/magento2/issues/38892) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/8670a2b4)_

#### FPT-värdet i kundvagnssidan och produktsidan är olika för samma konfigurationer för enkla produkter

FPT-värdena är nu desamma för kundvagn och produktsidor för enkla produkter.
Tidigare kunde värden för fast produktskatt (FPT) variera i decimaler mellan kundvagnen och produktsidorna, även när samma konfigurationer tillämpades.
AC-13066

_AC-13066 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/8953613e)_

#### Det går inte att spara attributalternativen Multiselect/select när modulen Färgrutor är inaktiverad

Det går nu att spara attributalternativen för multimarkering/markering när modulen Färgrutor är inaktiverad.
Tidigare orsakade inaktivering av modulen Färgrutor undantag när nya attributalternativ för multiselect/select skapades.
AC-13071

_AC-13071 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/8953613e)_

#### FPT-värdet i kundvagnssidan och produktsidan är olika för samma konfigurationer för en dynamisk produkt

FPT-värdena är nu konsekventa mellan kundvagn- och produktsidor för dynamiska produkter.
Tidigare kunde FPT-värdena (Fixed Product Tax) vara olika i decimaler mellan kundvagnen och produktsidorna för samma konfigurationer.
AC-13075

_AC-13075 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/8953613e)_

#### Datumformatet har inte respekterats i Date ui-komponenten

Ett problem där användargränssnittskomponenten för datum ignorerade det konfigurerade formatet och visade felaktiga värden har åtgärdats. Korrigeringen ser till att datumfältet nu uppfyller det angivna formatet (t.ex. Y-m-d) för både visning och inmatning.

_AC-13174 - [GitHub-problem](https://github.com/magento/magento2/issues/39218) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/913bf1a6)_

#### Det finns inget alternativ för att ta bort källor

Ett borttagningsalternativ för lagerkällor har lagts till i administratörsgränssnittet, vilket gör att administratörer kan ta bort extra källor i stället för att bara aktivera eller inaktivera dem. Den här förbättringen förbättrar lagerhanteringen genom att ge bättre kontroll över oanvända källor.

_AC-13354 - [GitHub-problem](https://github.com/magento/magento2/issues/32362) - [GitHub-kodbidrag](https://github.com/magento/inventory/commit/1b6c8a3e)_

#### Kategoriträdet i administratören har inte utökats så att alla markerade kapslade kategorier från nivå 3 visas

Ett problem har korrigerats där administrationskategoriträdet inte utökades för att visa markerade kapslade kategorier efter nivå 3. Efter korrigeringen utökas alla valda kategorier automatiskt, vilket förbättrar synligheten och användbarheten mellan kategorirelaterade villkor.

_AC-13363 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/913bf1a6)_

#### [Problem] Förbättra användarupplevelsen med rollträdet

Dragbegäran lägger till knappar för att komprimera alla, expandera alla och expandera grenar med markerade objekt. Den här funktionen liknar den som finns i kategoriträdet (Katalog -> Lager -> Kategorier)

_AC-14020 - [GitHub-problem](https://github.com/magento/magento2/issues/39654) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/36511)_

#### Åtgärdsloggar för import/export skapas inte i System > Åtgärdsloggar > Rapportrutnät

Implementerad loggning för Import/Export-administratörsåtgärder så att de nu visas i System > Åtgärdsloggar > Rapport. På så sätt får du bättre granskningsspårning genom att spela in importaktiviteter som tidigare saknades.

_AC-14266 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/b5e99d20)_

#### Symfony\Component\Mime\Exception\LogicException: &quot;Sender&quot;-huvudet måste vara en instans av &quot;Symfony\Component\Mime\Header\MailboxHeader&quot; (men &quot;Symfony\Component\Mime\Header\MailboxListHeader&quot;)

Adobe Commerce skickar nu registreringsmeddelanden när en anpassad retursökvägsadress har konfigurerats för SMTP. Tidigare i vanilj Adobe Commerce 2.4.8 med system/smtp/set_return_path inställd på 2 och system/smtp/return_path_email inställd på en anpassad adress, slutfördes kundregistreringen men e-postmeddelandet skickades inte och Adobe Commerce loggade detta fel: Symfony\Component\Mime\Exception\LogicException: &quot;Sender&quot;-huvudet måste vara en instans av &quot;Symfony\Component\Mime\Header\MailboxHeader&quot; (fick &quot;Symfony\Component\Mime\Header\MailboxListHeader&quot;).

_AC-14520 - [GitHub-problem](https://github.com/magento/magento2/issues/39823) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/1e14bd72) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/1514117f)_

#### Uppdateringsordningen hämtar inte de senaste anpassade attributdata

Ett problem har korrigerats där uppdateringen av ordersidan inte visade de senaste anpassade attributdata för kund. Efter korrigeringen återspeglas uppdaterade attributvärden nu utan att ordern behöver avbrytas och återskapas.

_AC-14690 - [GitHub-problem](https://github.com/magento/magento2/issues/30301)_

#### [Utgåva] - ersätt borttagen

Borttagen den ersatta getEscaper() och lade till den via konstruktorinjektion.

_AC-15132 - [GitHub-problem](https://github.com/magento/magento2/issues/40062) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/38135)_

#### Välkomstmeddelandet överlappar produktkategorin i mobilvyn

Ett gränssnittsproblem har korrigerats där välkomstnamnet överlappade produktkategorier i mobilvyn, vilket blockerade klick.
Nu är kategorier helt synliga och klickbara utan överlappningsproblem.

_AC-15166 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/1b1baf1d)_

#### Knappen Återställ användargränssnitt fungerar inte som förväntat

Systemet fungerar nu som det ska när du klickar på återställningsknappen utan att behöva läsa in hela sidan på nytt. Formulärdata återställs.

_AC-15204 - [GitHub-problem](https://github.com/magento/magento2/issues/40092) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/40094)_

#### [Problem] PageCache/AccessList: Stöd för tillägg av CIDR

Systemet tar nu emot rensningsbegäranden inom ett nätverk, och det är enklare att bara ange ett CIDR-intervall.

_AC-15804 - [GitHub-problem](https://github.com/magento/magento2/issues/39953) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/37809)_

#### [Problem] Lägg till förklarande titlar till cachehanteringsknappar

Systemet lägger nu till förklarande titlar till cachehanteringsknappar när du flyttar markören

_AC-16212 - [GitHub-problem](https://github.com/magento/magento2/issues/38607) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/38598)_

#### Ange en funktion för massradering av skattesatser med hjälp av rutnätet

Administratörsanvändare kan nu ta bort flera skattesatser samtidigt från rutnätet för administrationsskattesatser.  [GitHub-33399](https://github.com/magento/magento2/issues/33399)

_AC-2238 - [GitHub-problem](https://github.com/magento/magento2/issues/33399) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/33484) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/5cd64dd0)_

#### Hovringsfärgen används inte på statiska stödraster i administratören

Hovringsfärger används nu som förväntat på raderna i det statiska administratörsstödrastret.[GitHub-35358](https://github.com/magento/magento2/issues/35358)

_AC-2916 - [GitHub-problem](https://github.com/magento/magento2/issues/35358) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/35384)_

#### &quot;Det går inte att tolka reCAPTCHA-parametern&quot; i undantag.log för administratörspanelen för Google reCAPTCHA

Ett reCaptcha-fel i filen `var/log/exception.log` för inloggningen för Google V3 reCAPTCHA Admin har åtgärdats och inga felmeddelanden loggas. Tidigare utlöstes följande fel var några sekund när en administratörsanvändare konfigurerade sina **Configuration** > **Security** > **administratörsinställningar för Google reCAPTCHA**: `main.ERROR: Can not resolve reCAPTCHA parameter. {"exception":"[object] (Magento\Framework\Exception\InputException(code: 0): Can not resolve reCAPTCHA parameter. at /home/xxxxxxx/public_html/vendor/magento/module-re-captcha-ui/Model/CaptchaResponseResolver.php:25)"} []`.  [GitHub-34975](https://github.com/magento/magento2/issues/34975)

_AC-3179 - [GitHub-problem](https://github.com/magento/magento2/issues/34975) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/4f7e5983) - [GitHub-kodbidrag](https://github.com/magento/security-package/commit/804dbc2a)_

#### Fästprisregeln med villkor-SKU tar inte hänsyn till&quot;inledande nollor&quot; i SKU:n (sku: 01234 är samma som 1234)

Systemet hanterar nu kundvagnsprisregeln korrekt med villkor-SKU med hänsyn tagen till&quot;inledande nollor&quot; i SKU:n

_AC-9428 - [GitHub-problem](https://github.com/magento/magento2/issues/37919) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/39525)_

#### Problem med standardbeteende för attributalternativvärde för Multiselect

Före korrigeringen av standardvärdena för attributet multiple options sparades inte korrekt. Efter korrigeringen lagras värdena korrekt i databasen.

_ACP2E-3523 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/9608ca21)_

#### Problem vid flyttning av produktkvantiteten till varukorgen från administratören

När du skapar en order från administratören försvinner inte produkterna i kundvagnen på sidofältet när de läggs till i ordern.

_ACP2E-3563 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/c8ba4ab1)_

#### [Mellanlagring2] Lagrade kort visas inte på administratörspanelen

Korrigerar problemet där betalningsalternativet &quot;Lagrat kort&quot; inte längre fanns i ersättningsformuläret för backend-order efter en uppgradering.

_ACP2E-3830 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/7accebfa)_

#### Begränsad administratörsanvändare kan spara/uppdatera standardkonfigurationer trots lagringsspecifika behörigheter

Korrigerar problemet där begränsade administratörsanvändare kunde se och försöka uppdatera omfattningen &quot;Default Config&quot; trots att de endast tilldelats särskilda webbplatsomfång, vilket kan orsaka förvirring.

_ACP2E-4011 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/2a1e1e55)_

#### Konfigurerbart produktpris som sparats under DB för alla butiksvyer, vilket orsakar problem i sorteringsfunktionen Produkter i kategori där det sparade priset inte har någon betydelse i förgrunden

Avmarkerade kryssrutan Använd standardvärde för en konfigurerbar produkt när priset har konfigurerats per webbplats och en butiksvy har valts på sidan för redigering av konfigurerbar produkt i administratörsgränssnittet.

_ACP2E-4036 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/fab20b00)_

#### [KVANS]Administratörslösenordsprincipen uppfyller inte PCI DSS 4.0-överensstämmelse (minst 12 tecken)

Administratörer kan nu konfigurera krav på minsta lösenordslängd för administratörsanvändare via Lager > Konfiguration > Avancerat > Admin > Säkerhet. Den här förbättringen ger större säkerhetsflexibilitet samtidigt som befintliga lösenordsprinciper bevaras. Valideringen genomförs både när administratörsanvändare skapas/ändras och konfigureras, med edge-validering i realtid för att förbättra användarupplevelsen.

_ACP2E-4044 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/47721be6)_

#### Problem med datumfilter när admingränssnittsspråket är japanska

Födelsedagsfiltret och -kolumnen kommer att använda det enhetliga formatet M/d/y, samma som &quot;Kundens sedan&quot;-filtret/kolumnen

_ACP2E-4052 - [GitHub-problem](https://stg1.navi-online.kakuyasu.co.jp/adminCgWN7zCh/admin/system_account/index/key/d6fdbee50ff25178d1fef981ec823c5e82e8cee6959717790031bb900c4d6633/) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/52f46328)_

#### Vita block visas på båda sidor om administratörens rutnätshuvud

Ett problem med visuell justering i administratörsrutnät har korrigerats. Tidigare visades vita block vara feljusterade till vänster och höger om stödrasterrubriken när du bläddrar vågrätt genom produktrutnät på adminpanelen. Rutnätets rubrikelement behåller nu korrekt vertikal justering vid bläddring, vilket ger en renare visuell upplevelse för administratörer som hanterar stora produktkataloger.

_ACP2E-4104 - [GitHub-problem](https://mcprod.pap-store.acer.com/index.html)_

#### Ui-komponenten fileUploader fungerar inte korrekt i 2.4.8-p1/ 2.4-develop

Förbättrad filöverföring för anpassad UI-komponent med flera val för att tillåta överföring när du klickar på överföringsområdet.

_ACP2E-4162 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/ee918f0d)_

#### [På tidigare] skapade beställningar/företag/kunder som automatiskt ingår i Select All-scopet under urvalsprocessen

Korrigerade ett problem där alla poster på en inaktuell administratörssida skulle tas bort manuellt när massåtgärder utfördes. Tidigare växlade stödrastret automatiskt till läget&quot;markera alla&quot; internt när antalet markerade objekt matchade det totala antalet, vilket medförde att massåtgärder påverkade alla poster i stället för bara de uttryckligen markerade.

_ACP2E-4202 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/6e134409)_

#### Lösningen från ACP2E-3362 fungerar långsamt på MariaDB 10.6

Förbättrade prestanda för söksidan i teckensnittet om det finns ett stort antal tidigare sökbegäranden.

_ACP2E-4225 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/ab891304)_

#### Datumfiltret fungerar inte enligt butikens tidszon i kreditnotsrutnätet

Före korrigeringsfiltreringen av listor efter datumattribut orsakade att objekt saknades på grund av tidszonsskillnader mellan valda datum och lagrade datum. Nu, efter att filtren för korrigeringsdatum har tillämpats korrekt.

_ACP2E-4239 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/0a8c9a9a)_

#### Dialogrutan Filöverföring öppnas två gånger när Page Builder är installerat

Före korrigeringen av den anpassade komponentens överföringsknapp skulle utlösas två gånger. Efter korrigeringen fungerar knappen Överför som förväntat.

_ACP2E-4241 - [GitHub-kodbidrag](https://github.com/magento/magento2-page-builder/commit/5c4ae802)_

#### Valideringsfel för borttagna kundattribut när kunddata ändras.

Det gick inte att spara kund- och kundadressen före korrigeringen om de innehöll flera attributalternativ som hade tagits bort. Efter korrigeringen kan båda sparas korrekt även när det fortfarande finns flera attributalternativ.

_ACP2E-4281 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/0a8c9a9a)_

#### JS-varning på Admin Dashboard: &quot;Förväntade att starta inläsaren men hittade ingen i bakgrunden&quot;

Korrigerade den JavaScript-varning som visades i webbläsarkonsolen när diagram var aktiverade för administratörskonsolen. Tidigare, vid åtkomst till admin-kontrollpanelen med diagram aktiverade, skulle en föråldrad felsökningskontroll felaktigt varna &quot;Förväntade att inläsaren skulle starta men hittade ingen inläsare&quot; trots att funktionen fungerade korrekt.

_ACP2E-4336 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/2687b487)_

#### [CLOUD]-konfiguration med beroendekonfiguration ändringsbar när Använd standard är markerat i arkivkonfigurationen

Korrigerade problemet när systemkonfigurationsfält kunde återges aktiverade efter sidinläsning, trots att alternativet Använd standard/webbplats har markerats.

_ACP2E-4337 - [GitHub-problem](https://mcstaging.pap-store.acer.com) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/31258bf6)_

#### Admin Dashboard orderdiagram animerar till den slutliga storleken

Ordningsdiagrammet på kontrollpanelen för administratörer visas nu omedelbart utan att någon animering med onödig storleksändring behövs.

_ACP2E-4398 - [GitHub-problem](https://github.com/magento/magento2/issues/38860) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/f7bbcb4e)_

#### Page Builder kan inte spara innehåll i mobilvyn på grund av ett JS-fel (TypeError: Cannot read read properties of undefined)

Ett problem som gjorde att sidor inte kunde sparas i Page Builder när banners lades till i mobilvyn har korrigerats.

_ACP2E-4399 - [GitHub-problem](https://github.com/magento/magento2/issues/38565) - [GitHub-kodbidrag](https://github.com/magento/magento2-page-builder/commit/bdac5bca)_

### Administratörsgränssnitt, B2B

#### B2B-inloggning som kundhuvud har fortfarande Magento varumärke

Tidigare visas i butiksrubriken&quot;Du är nu ansluten som &lt;kundnamn> på &lt;butiksnamn>&quot; med Magento-märkning. Det är nu fixat och rubriken visas med ADOBE branding.

_AC-14361 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/fadcfa8b)_

### Administratörsgränssnitt, katalog

#### Produktsparandet misslyckas när katalogregeln är aktiv och läget Realtime är aktiverat

Ett problem har korrigerats där katalogregelindexeringen kunde misslyckas med ett DDL-transaktionsfel när produkten sparades genom att koppla loss katalogregelindexeringen från produkttransaktionen.

_ACP2E-4378 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/f7bbcb4e)_

### Administratörsgränssnitt, innehåll

#### Undantaget&quot;Det går inte att skapa återgivning för medieresurssökvägar&quot; vid infogning av bilder

När du har tagit bort värdena för Maximal bredd och Maximal höjd i konfigurationen för bildoptimering i Mediegalleriet inträffar felet inte längre under bildoptimeringsprocessen.

_ACP2E-3781 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/520f9e30)_

### Administratörsgränssnitt, beställning

#### Skapa administratörsorder: Sessionsstorleksspill när 20+ produkter läggs till (sessionsstorleken överskrider gränsen på 256 kB)

Löste problem med sessionsstorleksspill när administratörsordningen skapades genom att förhindra att stora HTML-svar lagras i sessionen för JSON-begäranden, vilket säkerställer att större produkttillägg fungerar smidigt utan att administratören loggas ut.

_AC-15893_

### Administratörsgränssnitt, säkerhet

#### Svag lösenordshantering

Administratörsanvändaren kan inte sparas när samma lösenord används. Tidigare sparades den utan korrekt validering.

_ACP2E-3657 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/df92debe)_

### Administratörsgränssnitt, skatt

#### Fel i administrationsgränssnitt för momssats

Den här biljetten åtgärdade ett gränssnittsproblem för momsadministratör där växling av land (t.ex. från USA → Storbritannien) fortfarande visade den tidigare valda amerikanska staten, missvisande användare.
I 2.4.9-alpha3 återställs nu tillståndsfältet till * när det valda landet inte har några lägen.

_AC-8440 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/a3b1abc2)_

### Analyser/rapporter

#### [Issue] har lagt till scp-tillåtelselista för Analytics om du bara använder Google Analytics

Denna PR lägger till en vitlista för CSP i Google Analytics-modulen, vilket gör att den kan fungera oberoende utan ett Google Adwords-beroende. Google Analytics fungerar nu korrekt även när modulen Google Adwords är inaktiverad.

_AC-16311 - [GitHub-problem](https://github.com/magento/magento2/issues/40051) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/40032)_

#### Duplicerade filhuvuden i avancerade rapport-CSV-filer orsakar tomma rapporter

Efter korrigeringen innehåller rapporter som genererats för den avancerade rapportfunktionen inte längre duplicerade rubrikrader när radantalet överskrider batchstorleken.

_ACP2E-4187 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/45cbf9b6)_

#### Övergiven kundvagnsrapport innehåller ogiltiga tecken

Övergiven Cart-rapport som exporterats som CSV-fil innehåller nu korrekt återgivna tecken för valutasymboler som indiska rupie när den öppnas i MS Excel.

_ACP2E-4288 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/0a8c9a9a)_

#### Uppdatering för MDVA-19640 för kompatibilitet med 2.4.8

Korrigeringen flyttar jobbuppgifterna för analyscron från standardgruppen till analysgruppen

_ACP2E-4309 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/c135fc3a)_

#### Intäkter visas inte i rapporter om beställningar/fakturor i Admin för Kanadas webbplats/valuta

I vissa av de orderrelaterade rapporterna tillämpades inte valutakurser för butik. Efter korrigeringen tillämpar rapporter korrekt konfigurerade lagringshastigheter.

_ACP2E-4361 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/31258bf6)_

### B2B

#### Verifiering av företagsfält misslyckas för gästutcheckning

Gästutcheckning validerar nu företagsfältet korrekt.
Tidigare när företagsattributet krävdes misslyckades gästutcheckningen med felet&quot;Företag är ett obligatoriskt värde&quot;, även när fältet fylldes i.
AC-14987

_AC-14987 - [GitHub-problem](https://github.com/magento/magento2/issues/40011) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/f1adb44e)_

#### Återstående API-produkter-render-info returnerar fel slutpris för inloggad kund

Biljetten har en korrigering för Rest API-produkter-render-info returnerar fel slutpris för inloggad kund

_AC-5979 - [GitHub-problem](https://github.com/magento/magento2/issues/35757)_

### B2B, kundvagn och kassan

#### Ingen sådan entitet med cartId = X-fel visas på Storefront när B2B-företagsanvändare loggar in från administratörsfunktionen Logga in som kund

Nu visas ingen sådan entitet med cartId = X-fel efter att ha loggat in från administratörens serverdel med funktionen Logga in som kund.

_ACP2E-3994 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/2a1e1e55)_

#### Faktureringsadressen som saknas förhindrar att beställningar görs med leveransmetoden &quot;In store Delivery&quot;

Ett problem där faktureringsadressen inte fylldes i automatiskt vid utcheckning när In-Store Pickup valdes som leveransmetod har åtgärdats. Det gick inte att slutföra utcheckningen utan en faktureringsadress.

_ACP2E-4030 - [GitHub-kodbidrag](https://github.com/magento/inventory/commit/42d23211)_

### Kort och utcheckning

#### Magento 2.4.7 update (mini)cart no decimal quantity allowed

Nu hanterar Magento korrekt när vi uppdaterar kvantitet med decimaler från mini cart när språkinställningen var NL (holländska)

_AC-13238 - [GitHub-problem](https://github.com/magento/magento2/issues/39236) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/39669)_

#### [Problem] Lägg till EventPrefix och EventObject i utcheckningsavtalsmodellen

Systemet inkluderar nu EventPrefix och EventObject för kassaavtalsmodellen, vilket gör att händelser kan utlösas med ett händelseprefix. Den här förbättringen ger större flexibilitet för utvecklare när de arbetar med avtalshändelser i kassan. Tidigare hade arbetsavtalsmodellen inte stöd för EventPrefix och EventObject, vilket begränsade möjligheten att anpassa händelsehantering.

_AC-13252 - [GitHub-problem](https://github.com/magento/magento2/issues/32510) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/32451)_

#### [Issue] Developer Experience: Quote AbstractItem-kodformat (SwiftOters SOP-348)

Dragningsbegäran åtgärdar vilseledande metoddeklarationer för Abstract Item-metoder.

_AC-13334 - [GitHub-problem](https://github.com/magento/magento2/issues/39340)_

#### Valideringar av grupperat produktantal saknas

Systemet fungerar nu som det ska och ett valideringsfel visas när vi försöker lägga till negativ kvantitet och maximal kvantitet

_AC-13524 - [GitHub-problem](https://github.com/magento/magento2/issues/39479) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/39480)_

#### [Problem] Uppdatera delsumma.phtml

Systemet uppdaterar subtotal.phtml med rätt mellanrum

_AC-13907 - [GitHub-problem](https://github.com/magento/magento2/issues/39619) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/39612)_

#### Det går inte att lägga ordern hos gästen

Adobe Commerce tillåter nu gästkunder att lägga order när fältet för mellannamn är konfigurerat enligt kraven i Admin. Tidigare konfigurerades mellannamn som nödvändigt i Adobe Commerce 2.4.8-beta1 (PHP 8.3/8.4) och utcheckning som gäst förhindrades vid orderplacering även när ett mellannamn angavs, vilket blockerade slutförandet av utcheckningen. AC-14241

_AC-14241 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/27217d0e)_

#### [Graphql] Det går inte att returnera null för det icke-nullbara fältet SelectedCustomizableOption.label

Systemet genererar nu inget internt serverfel med ett meddelande när det valda alternativet inte längre finns

_AC-14256 - [GitHub-problem](https://github.com/magento/magento2/issues/39729) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/39888)_

#### GraphQL addWishlistItemsToCart kan inte uppdatera kvantiteten för befintliga kundvagnsobjekt när ett av listobjekten är ogiltigt (Magento 2.4.7-p3)

Ett problem har korrigerats där GraphQL-mutationen addWishlistItemsToCart slutade bearbeta när en ogiltig konfigurerbar produkt påträffades. Efter korrigeringen läggs giltiga önskelisteobjekt till i kundvagnen och kvantiteterna uppdateras, medan ogiltiga artiklar hoppas över med lämpliga fel returnerade.

_AC-14464 - [GitHub-problem](https://github.com/magento/magento2/issues/39820) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/3cf1a106)_

#### [2.4.8] Det går inte att placera order där City har siffrorna 0-9, Ampersand, stopp eller parentes i stadsnamnet

Ett problem har korrigerats där utcheckningen misslyckades för stadsnamn som innehåller specialtecken som . , &amp; eller parenteser.
Nu kan beställningar med sådana stadsnamn placeras utan valideringsfel.

_AC-14495 - [GitHub-problem](https://github.com/magento/magento2/issues/39854) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/b9f5d6f7)_

#### Gästprefixet har inte sparats i offertadressen 2.4.8

Gästkundprefixet (Mr/Mrs.) sparas nu under utcheckningen.
Tidigare gick hälsningar som valts av gästkunder förlorade innan den slutliga ordern uppnåddes, medan alla andra adressfält överfördes korrekt.
AC-14705

_AC-14705 - [GitHub-problem](https://github.com/magento/magento2/issues/39915) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/f1adb44e)_

#### Salesrule Delmarkera med kvantitetsvillkor ej tillämpligt

Ett problem har korrigerats där kundprisregler med delurvalsvillkor för produkt inte tillämpades vid utcheckningen.
Rabatterna tillämpas nu enligt de konfigurerade reglerna.

_AC-14884 - [GitHub-problem](https://github.com/magento/magento2/issues/39965) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/fe72c407)_

#### [Problem] Ta bort utrymme i klassattribut

Systemet tar nu bort ett extra utrymme i klassattributet

_AC-14939 - [GitHub-problem](https://github.com/magento/magento2/issues/39977) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/39970)_

#### Graphql - Kopplingsvagnen fungerar inte korrekt när backorder är aktiverad

Ett problem har korrigerats där gästvagnsartiklar inte samlades med kundvagnen när vagnen samlades via GraphQL.
Nu återspeglar kundvagnen den kombinerade kvantiteten från både gäst- och kundvagn korrekt.

_AC-15148 - [GitHub-problem](https://github.com/magento/magento2/issues/40064) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/a3b1abc2)_

#### [Integrering] [Utcheckning] Beroendedirektiv har uppdaterats i mallen för misslyckade betalningar

E-postmallen för betalning som uppdaterats för att hantera beroende direktiv på fel sätt misslyckades.
Fix säkerställer att leveransadress och leveranssätt visas korrekt när det är tillämpligt.
Tidigare saknades dessa fält i misslyckade e-postmeddelanden om betalningar.

_AC-15363 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/36d4d6fb)_

#### [KART] Kundvagnssidan läses inte in när Fast produktskatt är aktiverat

Ett problem har korrigerats där kundvagnssidan angav oändlig inläsning när FPT (Fixed Product Tax) aktiverades. Felet orsakades av felaktiga delsummeberäkningar på grund av att moms inkluderades i samma HTML-element som artikelpriset, vilket ledde till en felmatchning mellan centrala och sammanfattande delsummor. Efter korrigeringen läses kundvagnen in korrekt och exakta summor visas.

_AC-16096 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/01cee3c3)_

#### Kundprisregel Åtgärd &quot;Pris i kundvagn&quot;, gäller när den inte ska tillämpas

Ett problem har korrigerats där kundprisreglerna med villkoret&quot;Price in Cart less than&quot; felaktigt tillämpades på icke-berättigade produkter.
Nu valideras kuponger och avvisas när varupostpriser inte uppfyller de konfigurerade regelvillkoren.

_AC-6997 - [GitHub-problem](https://github.com/magento/magento2/issues/36433) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/01cee3c3)_

#### [Utgåva] Ange pris för offertobjekt i stället för baspris

Systemet hanterar offertobjektets pris inställt på base_price i stället för priset om du har flera valutor på en webbplats i klientdelen

_AC-9985 - [GitHub-problem](https://github.com/magento/magento2/issues/38094) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/36878)_

#### Utgångna beständiga citattecken rensas inte av ett cron job sales_clean_quotes

De utgångna beständiga citattecknen rensas nu när kron-jobbet persistent_clear_expirate körs. Tidigare rensades de inaktuella citattecknen inte av något annat cron-jobb.

_ACP2E-3493 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/11be3dff)_

#### Ett fel uppstod vid utcheckning av inaktivt företag

Före korrigeringen slutfördes inte utloggningsåtgärden korrekt på kundvagnssidan om det utloggade användarföretaget inte längre var aktiverat. Om företaget inte längre är tillgängligt utförs utloggningen korrekt.

_ACP2E-3541 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/df92debe)_

#### Markeringen av adresser sparas inte när vi checkar ut med flera adresser

Innan korrigeringen avbröts valdes inte adressen i förväg när du återgick till flera leveranser. Nu ersätts standardadressen med ett av de val som gjorts på skärmen för flera leveranser.

_ACP2E-3646 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/6ea61121)_

#### [Molnet] Senaste beställningar visas inte i den andra butiksvyn om beställningarna skapas i en butiksvy

Ett problem har korrigerats där sidan Mitt konto inte visade de senaste beställningarna från andra butiksvyer i samma Store. Logiken för orderhämtning har uppdaterats för att säkerställa att ordern visas på ett konsekvent sätt i alla butiksvyer, i enlighet med beteendet på sidan&quot;Mina beställningar&quot;.

_ACP2E-3807 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/a20a6ff2)_

#### Kvantitet som visas som  0 i kundvagnsdelen för administratör när BUNDLE-produkter läggs till  

I avsnittet Kundvagn i Kundaktiviteter visas nu rätt kvantitet. Tidigare visades kvantiteten som 0.

_ACP2E-3872 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/3ad96f6a)_

#### [Cloud] Fri frakt-rabatt tas inte bort korrekt när vagnen inte längre uppfyller kraven

Delsumman (exkl. Moms) i kundprisregeln kommer nu att inkludera rabatter från föregående regler.

_ACP2E-3973 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/6dd3fa99)_

#### Dubblettorder hittades för samma kund i Multishipping

Samtidiga beställningar av flera leveransadresser resulterar inte längre i dubbla beställningar för samma kund

_ACP2E-4117 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/a1c57b2e)_

#### [Cloud] Ett meddelande om att gränsen för Stock har överskridits visas två gånger när gränsen för Stock har överskridits

Korrigerade ett problem där kundvagnsuppdateringarna kunde visa dubbla felbanderoller. Tidigare, efter ett valideringsfel i AJAX, lade backend till samma meddelande igen när formuläret skickades in, så att kunderna skulle se två identiska varningar. Nu går det inte att lägga till det extra serverdelsmeddelandet, vilket gör att kundvagnssidan hamnar i en enda felbanderoll.

_ACP2E-4192 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/e885088b)_

#### Verifieringen av serversidan för faktureringsinformation fungerar inte med REST API för leveransinformation

Valideringen av kundadressdata har förbättrats för att vara mer konsekvent mellan REST och GraphQl för utcheckning.

_ACP2E-4223 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/0a8c9a9a)_

#### [Problem med produktpris i molnet] på kundvagnssidan

Korrigerat problemet med paketpris på kundvagnssidan för butiker med flera valutor

_ACP2E-4245 - [GitHub-problem](https://www.techbuyer.com/) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/cbca0396)_

#### Hantera problem med kundvagnsbutiker

Nu visas kundvagnsfel för administratörsanvändaren när kundvagnen hanteras för en kund som tilldelats en icke-standardwebbplats. Tidigare visades inga fel.

_ACP2E-4348 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/31258bf6)_

#### Kupongtider_använda återställningar efter partiell fakturaannullering

Antal kupongtider_använda uppdateras nu korrekt när en order delvis annulleras.

_ACP2E-4365 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/61c96348)_

### Kort och utcheckning, GraphQL

#### Fel vid mappning av meddelande till felkod vid beställning via GraphQL

GraphQL anropar för att lägga en order på en obefintlig eller inaktiv varukorg som nu returnerar felkoderna CART_NOT_ACTIVE eller CART_NOT_FOUND korrekt i alla butiksvyer, vilket åtgärdar ett problem där översatta felmeddelanden tidigare resulterade i en UNDEFINED-kod.

_ACP2E-3942 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/7accebfa)_

#### [GraphQl] kundvagnsfrågeartikelrabattproblem på virtuella offerter

Ett problem där GraphQL kundvagnsfrågan returnerade ett felaktigt rabattbelopp för virtuella offerter har åtgärdats. Tidigare tillämpades rabatterna felaktigt på vissa virtuella produkter som inte var berättigade.

_ACP2E-4248 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/cbca0396)_

#### [Cloud] ACSD-68499_2.4.8-p2 skapar ett annat problem

När en GraphQL-begäran för en artikel med otillräckligt antal gjordes returnerades ett felmeddelande med en felkod och om den begärda kvantiteten är tillgänglig slutfördes uppdateringen av vagnen.

_ACP2E-4404 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/1c547060)_

### Kort och utcheckning, GraphQL, Inventory / MSI

#### is_available-attributet i CartItemInterface returnerar false även när det säljbara lagret är högt

Attributet is_available returnerar true när det säljbara lagret är högt. Tidigare returneras alltid false.

_ACP2E-3885 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/3ad96f6a)_

### Kundvagn och utcheckning, inventering/MSI

#### 414 Fel vid &#39;Sök efter hämtningsplats&#39;-slutpunkt med stora kundvagnsstorlekar

Det går inte längre att välja en butik vid utcheckning med&quot;Välj i butik&quot; på grund av långa URL:er när många produkter finns i vagnen.
Tidigare utlöste detta ett 414-fel som orsakats av alltför långa URL:er som genererats under valet av butik, vilket hindrade kunderna från att slutföra utcheckningen.

_ACP2E-4266 - [GitHub-problem](https://mcstaging.casamyers.com.mx/) - [GitHub-kodbidrag](https://github.com/magento/inventory/commit/ae1f272f)_

### Kundvagn och kassan, kampanj

#### Visningssaldot på presentkortet begränsas inte av webbplatsens omfång

Begränsade saldokontrollen för presentkort med det tilldelade webbplatsomfånget.

_ACP2E-4379 - [GitHub-problem](https://www.panini.it)_

### Kort och utcheckning, säkerhet

#### [CLOUD] Hämtar 404 för JS-fil på utcheckningssidan vid första försök efter implementering av Sri patch

Före korrigeringsblandningarna hade de inte lästs in i varukorgen och i kassan när minify och bundling är aktiverat. Efter korrigeringen ska alla mixins läsas in som förväntat.

_ACP2E-4128 - [GitHub-problem](https://ansg.integration-5ojmyuq-f46gejjrfa7be.ap-3.magentosite.cloud/) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/e457c5e2)_

### Kundvagn och utcheckning, leverans

#### [Mainline] Prisregeln för kundvagn respekterar inte flerleverans

Innan den här korrigeringen genomfördes tillämpades inte kundvagnsprisregeln för produkter med flera leveranser korrekt när vissa villkor tillämpades och fri frakt aktiverades. Men eftersom korrigeringen gjordes fungerar nu kundvagnsprisregeln för varukorgar som avsett.

_ACP2E-3666 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/b12ffe36)_

### Katalog

#### Dubblett av cache fpc för samma sida med samma fråga

Nu identifieras och används samma helsidescache (FPC) korrekt för sidor med samma frågeparametrar, oavsett ordningsföljd eller efterföljande tecken. Detta förhindrar att storleken på sidcachemappen ökar i onödan. Tidigare skulle systemet skapa en annan FPC-identifierare för samma sida om frågeparametrarnas ordning var annorlunda eller om det fanns efterföljande tecken, vilket skulle leda till en ökning av storleken på sidcachemappen.

_AC-10722 - [GitHub-problem](https://github.com/magento/magento2/issues/38269) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/38270)_

#### Indexering av obligatoriska kolumner saknas i tabellen catalog_product_entity_int

Lagt till saknad indexering av obligatoriska kolumner i tabellen catalog_product_entity_int

_AC-10844 - [GitHub-problem](https://github.com/magento/magento2/issues/38315) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/38316)_

#### Scope bug in Catalog URL resource (_getCategories)

Den här PR-versionen lägger till en reserv i standardomfånget om inget värde har definierats i butiksomfånget i kategorins URL-resurs.

_AC-11011 - [GitHub-problem](https://github.com/magento/magento2/issues/38393) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/38394)_

#### [Utgåva] Kontrollera om OpenGraph kan visa pris

Systemet fungerar bra när vi använder ett plugin-program som döljer priset och med det här ändringspriset visas inte i OG-taggen.

_AC-11635 - [GitHub-problem](https://github.com/magento/magento2/issues/38512) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/38510)_

#### Avrundningsproblem med priser när moms läggs till i priser

Systemet åtgärdar nu ett avrundningsproblem i priser när moms läggs till i priser

_AC-11725 - [GitHub-problem](https://github.com/magento/magento2/issues/18025) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/35730)_

#### [Problem] Tillåt villkor för anpassade katalogregler

Ett problem som gjorde att anpassade katalogregelvillkor inte kunde användas på grund av strikt typkontroll har åtgärdats. Korrigeringen ersätter likhetskontrollen för klassen med instanceof, vilket gör att anpassade villkorsklasser fungerar korrekt och möjliggör lyckad regelvalidering och indexering.

_AC-13338 - [GitHub-problem](https://github.com/magento/magento2/issues/39339) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/913bf1a6)_

#### Konfigurerbara alternativ för produktförluster som läggs till i önskelistan

Korrigerade ett problem där konfigurerbara produktalternativ gick förlorade när produkten lades till i önskelistan. Nu behålls de valda alternativen, vilket gör att produkten kan läggas till i varukorgen utan att användaren behöver göra om val.

_AC-13373 - [GitHub-problem](https://github.com/magento/magento2/issues/39363) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/cc0ec250)_

#### Specialpriset visas inte korrekt för den konfigurerbara produktens underordnade produkt (enkel produkt)

Ett problem har korrigerats där specialpriset för en konfigurerbar produkts underordnade (enkla) produkt inte visades korrekt på produktlistsidan när&quot;Används i produktlista&quot; var inställt på Nej. Nu visas specialpriset korrekt tillsammans med normalpriset, vilket ger enhetliga priser för alla produkttyper.

_AC-13594 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/3cf1a106)_

#### [Fel] REST API: Uppdatera specialpriser anger inte värden för alla butiksvyer

REST API uppdaterar nu specialpriser för alla butiksvyer på en webbplats.
Tidigare påverkades bara den angivna butiksvyn om specialpriserna uppdaterades via REST API, inte alla butiksvyer på webbplatsen.
AC-13671

_AC-13671 - [GitHub-problem](https://github.com/magento/magento2/issues/39521) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/7bdafaa2)_

#### Problem med pris och config.php

I Magento 2.4.2 uppdateras inte is_global-värdet i catalog_eav_attribute för prisattributet korrekt om prisomfattningen ändras via config.php.
Detta innebär att produktpriserna förblir globala och inte kan sparas per webbplats, även om prisomfånget är inställt på en webbplats.
För att kringgå problemet måste du uppdatera kolumnen is_global i databasen manuellt, vilket inte är idealiskt för produktionsmiljöer.
Detta beteende är förenligt med Magento standarddesign, där prisomfånget är antingen Global eller Website, men inte per butiksvy.

_AC-13857 - [GitHub-problem](https://github.com/magento/magento2/issues/33559)_

#### [\Magento\ConfigurableProduct\Model\Product\Type\Configurable] PHP-fel okänt

Ändrade ett loopvariabelnamn så att &quot;_cache_instance_product_ids&quot;-data på den angivna produkten lades till korrekt för efterföljande anrop.

_AC-14159 - [GitHub-problem](https://github.com/magento/magento2/issues/39641) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/39642)_

#### Elastic Search stör standardsorteringsordningen för produkter (ändrar den senaste först till den äldsta först)

Nu sorteras de senaste produkterna i databasen (den som har det högsta enhets_id:t) först.

_AC-14411 - [GitHub-problem](https://github.com/magento/magento2/issues/31043) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/36900)_

#### Efter att butikens växlingssida kommer från cache (Store-växlaren fungerar inte) i 2.4.8

Ett problem har korrigerats där växling av butiksvyer från butikshuvudet inte fungerade förrän cachen rensades manuellt.
Nu fungerar vyväxling för butiker korrekt utan att någon cache behöver rensas.

_AC-14426 - [GitHub-problem](https://github.com/magento/magento2/issues/39806)_

#### Ignorerade .less-format med min-width: (@screen_l)

Ett problem där endast tre produkter visades per rad på kategorisidor har korrigerats.
Nu visas fyra produkter per rad som väntat.

_AC-14463 - [GitHub-problem](https://github.com/magento/magento2/issues/39817) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/b9f5d6f7)_

#### Önsklisteantal visas inte på hemsidan/andra sidor förutom önskelistsidan på kundmenyn

Ett problem har korrigerats där antalet önskelistor visades som tomma parenteser på sidor som inte är önskelistor.
Nu visas rätt antal önskelisteobjekt bredvid&quot;Min önskelista&quot; på alla sidor.

_AC-14607 - [GitHub-problem](https://github.com/magento/magento2/issues/39892) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/a3b1abc2) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/b3774fbe)_

#### catalog_product_save_before-betraktaren returnerar ett datumrelaterat fel när REST API används utan butiksnivåvärden (getFinalPrice()-problem)

Denna PR justerar bearbetningen av SpecialFromDate för att säkerställa korrekt formatering när datumet anges som en DateTimeInterface-instans. Detta förhindrar att fel uppstår under körningen av getFinalPrice() i vissa scenarier.

_AC-14847 - [GitHub-problem](https://github.com/magento/magento2/issues/39959) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/40003)_

#### URGENT - Det går inte att lägga till produkten i paketet när produkten som ska läggas till har anpassningsbara alternativ

Ett problem har korrigerats där produkter med anpassningsbara alternativ inte kunde läggas till i paketprodukter.
Tidigare har sådana produkter uteslutits från listan&quot;Lägg till produkter till alternativ&quot; när paket skapades.
Nu kan produkter med anpassningsbara alternativ läggas till i paket utan att deras anpassade alternativ tas med, vilket möjliggör korrekt arkivhantering.
Detta gör det möjligt att skapa paket utan att behöva duplicera produkter eller påverka lagernivåerna.

_AC-14958 - [GitHub-problem](https://github.com/magento/magento2/issues/39993)_

#### Negativ frågesträng `?p=` orsakar ett Elasticsearch-undantag

Systemet åtgärdar nu det negativa ?p=-värdet i kategorinumreringen, som för närvarande leder till undantag och som betraktas som en giltig begäran

_AC-15191 - [GitHub-problem](https://github.com/magento/magento2/issues/40079) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/40080)_

#### Prisetiketten &quot;Så lite som&quot; visas för konfigurerbara produkter med ett enda alternativ

Ett problem har korrigerats där konfigurerbara produkter visade priset med en felaktig etikett &quot;Så lågt som&quot; på PDP/PLP.
Nu visas rätt pris ($500) utan några vilseledande etiketter.

_AC-15237 - [GitHub-problem](https://github.com/magento/magento2/issues/40104) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/a3b1abc2)_

#### Fel metod anropades för knappen Lägg till i jämförelse

Metoden som används i \Magento\Catalog\Ui\DataProvider\Product\Listing\Collector\Url::collect() har korrigerats.
Tidigare anropades getAddToCartButton() felaktigt i stället för getAddToCompareButton().
Ändringen säkerställer att återgivningsknappen Lägg till i jämförelse fungerar korrekt i produktlistor.
Inga funktionsändringar har gjorts. Uppdateringen förbättrar utvecklarupplevelsen och kodkorrektheten.

_AC-15323 - [GitHub-problem](https://github.com/magento/magento2/issues/39754) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/a3b1abc2)_

#### Fel produktpris visas i kundvagnen med olika valutor i olika butiksvyer

Ett problem har korrigerats där felaktiga produktpriser visades i kundvagnen när olika valutor användes i olika butiksvyer. Efter korrigeringen visar vagnen nu korrekt konverterat pris baserat på den konfigurerade valutan, vilket säkerställer konsekvens mellan produktsidan och kundvagnen.

_AC-15385 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/a8cf637b)_

#### Felaktig visning av&quot;Så lågt som&quot;-pris för konfigurerbara produkter när FPT är aktiverat

Bekräftat att det felaktiga &quot;Så lågt som&quot;-priset för konfigurerbara produkter när bildrutefrekvensen aktiverades orsakades av att moms tillämpades två gånger. Korrigeringen säkerställer att den slutliga prisberäkningen respekterar skattekonfigurationen och visar nu korrekt pris.

_AC-15718 - [GitHub-problem](https://github.com/magento/magento2/issues/40171) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/a06a4a57)_

#### Tidskomplexiteten för _loadAttributes i Eav\Model\Entity\Collection\AbstractCollection ökar med antalet produkter i kundvagnen och attribut

Denna PR optimerade _loadAttributes i Eav\Model\Entity\Collection\AbstractCollection genom att ersätta kapslade slingor med arrayunion (+) och minska anrop till _setItemAttributeValue, vilket förbättrar prestanda för stora varukorgar.

_AC-15833 - [GitHub-problem](https://github.com/magento/magento2/issues/40216) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/40217)_

#### Interaktion mellan samlingens cache och galleriet med konfigurerbara produkter har misslyckats

Löste ett cachningsproblem med konfigurerbara produktgallerier genom att lägga till en defensiv typkontroll för att säkerställa att media_gallery_images alltid behandlas som en samling, vilket förhindrar allvarliga fel orsakade av skadade cachedata.

_AC-16066 - [GitHub-problem](https://github.com/magento/magento2/issues/33965) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/3b5ac075)_

#### Produktsidan genererar fel på grund av omskrivningar av URL

Nu läses produktsidan in korrekt när URL-omskrivningar görs

_AC-2950 - [GitHub-problem](https://github.com/magento/magento2/issues/35371) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/39670)_

#### indexer_update_all_views, felmeddelande med MAGE_INDEXER_THREADS_COUNT

Korrigerat problem med MAGE_INDEXER_THREADS_COUNT > 2 med kundsegmentsindexeraren

_ACP2E-3538 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/9608ca21)_

#### Undantag när villkorskombination lades till i widgeten för Page Builder-produkter

Problemet har åtgärdats genom att en kontroll läggs till för att hoppa över saknade eller ofullständiga villkor. Tidigare genererades felloggar på grund av hantering av ofullständiga förhållanden i systemet.

_ACP2E-3545 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/11be3dff)_

#### Webbläsaren kraschar när attributuppsättningen läses in

Webbläsaren kraschar inte längre på redigeringssidan för attributuppsättningar om det finns fler än 4k-produktattribut

_ACP2E-3633 - [GitHub-problem](https://github.com/magento/magento2/issues/38810) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/b12ffe36)_

#### [CLOUD] Produkt-URL-omskrivningar har inte skapats för ny butik: Go Live Blocker

Produkt-URL-omskrivningar för New Store har skapats.
Tidigare slutfördes minnesläckage eller timeout.

_ACP2E-3669 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/df92debe)_

#### Attributstandardvärde för alternativ fungerar inte

Tidigare visades det som ett arrayelement med de tidigare värdena när vi ändrade standardvärdet för ett produktvalsattribut. När den här korrigeringen har tillämpats sparas det som ett element i eav_attribute-tabellen när vi uppdaterar ett produktattributvärde.

_ACP2E-3688 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/520f9e30)_

#### [Mainline] [CLOUD] Bildstorleksändring förbrukar mer än 400 GB diskutrymme

Efter korrigeringen genererar inte kommandot `catalog:images:resize` som används med flaggan `--skip_hidden_images` bildcacher för webbplatser där bilder saknas.

_ACP2E-3869 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/9ad7d277)_

#### Dynamisk bildgenerering genererar ett stort antal bilder

Efter korrigeringen genereras bilder endast för de webbplatser som produkten är tilldelad till.

_ACP2E-3927 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/fab20b00)_

#### Angivet land-ID finns inte - Irland (IE)

Efter korrigeringen kan Irland-postkoder användas för att söka efter hämtningsplatser.

_ACP2E-3932 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/4ca73607) - [GitHub-kodbidrag](https://github.com/magento/inventory/commit/d2f1d6c6)_

#### 500-fel inträffar på klientsidan eftersom en felaktig layoutstruktur cachas i layouten

Ett problem har korrigerats när en sida skulle returnera en felkod på 500 på grund av att en felaktig layoutstruktur cachelagrades i layouten

_ACP2E-4040 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/47721be6)_

#### Felaktig rapport om produktvyer - färre antal jämfört med GA

Korrigerade ett fel där tabellen report_displayed_product_index inte visade rätt antal produktsidesvisningar.

_ACP2E-4045 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/6e134409)_

#### Valideringsfel för rabattbeloppsfältet för katalogprisregel i den schemalagda uppdateringen

Innan den här utgåvan åtgärdats validerades inte rabattbeloppet korrekt för katalogprisregeln om rabattbeloppet är by_fixed på grund av regeln för valideringsnummer. När den här korrigeringen har tillämpats fungerar valideringen korrekt för katalogprisregeln fast pris.

_ACP2E-4054 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/6dd3fa99)_

#### momsvalideringen misslyckas på grund av momsbegränsning för API - utlöser falskt positiv ändring av kundgrupp

Optimerade begäranden till Europa Vat-valideringsverktyget, vilket ger mindre &quot;rate limiter&quot;-fel

_ACP2E-4072 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/ee918f0d)_

#### Massborttagning i Core Indexer utlöser ett fel av typen maximal skrivinställningsstorlek vid produktion

Optimerar rensning av katalogregelns produktindex genom att implementera två raderingsstrategier baserat på datavolym.

_ACP2E-4085 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/0a3b7032)_

#### Produkterna visas som utgångna efter inaktivering

Efter korrigeringen finns inaktiverade produkter inte i produktwidgeten.

_ACP2E-4136 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/a1c57b2e)_

#### [Cloud] Fel med dubblettposter (temp_category_descendants_%)

Ett problem med dubblettposter när schemalagda uppdateringar skapades för miljöer med många kapslade kategorier har korrigerats

_ACP2E-4159 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/a1c57b2e)_

#### [CLOUD] Fel vid jämförelse av antalet produkter för olika butiker

Jämför produktlistan fungerar nu korrekt när du har bytt till en annan granskning

_ACP2E-4249 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/98f028ab)_

#### Det finns inget alternativ för att använda standard i Bilder och videoklipp för tilldelning av bildroller

Alternativen för Använd standardvärde har lagts till i avsnittet för produktbilder och videoklipp, vilket möjliggör arv av inställningar från standardomfånget.

_ACP2E-4280 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/61c96348)_

#### Begränsade kategoriprodukter räknas fortfarande i önskelistan efter uppdatering av kundgrupp

Före korrigeringen tillämpades inte kategoribehörigheter korrekt på kundens önskelisteobjekt. Efter korrigeringen visas önskelisteobjekten korrekt och sidnumreras både på webben och i GraphQL.

_ACP2E-4294 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/c135fc3a)_

#### [Cloud] Paket med produktprisproblem på PDP och PLP

Priset för paketprodukt med fast pris visas korrekt på PDP/PLP för icke-standardvaluta

_ACP2E-4298 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/0a3b7032)_

#### Kunden kan göra en beställning av en produkt som inte är tillgänglig efter ändring av kundgrupp

Tidigare, när kundgruppen ändrades från admin, avspeglades inte ändringarna i katalogbehörigheterna i klientkatalogen och kundvagnen. När du har tillämpat den här korrigeringen ändras emellertid offerten nu enligt de uppdaterade katalogbehörigheterna när kundgruppen ändras från admin.

_ACP2E-4300 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/f7bbcb4e)_

#### Omindexering har fastnat på grund av hög minnesanvändning

Korrigerade problemet där katalogregelindexeraren förbrukade för mycket minne och misslyckades att slutföra, vilket orsakade instabilitet och fel av typen slut på minne.

_ACP2E-4303 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/c135fc3a)_

#### [CMS] Förhandsgranskningslänk för schemalagd uppdatering omdirigeras till underhållssidan

Schemalagd förhandsvisning av startsideslänk med konfigurerbara produkter visar produktlistor korrekt. Tidigare dirigerades användarna till underhållssidan

_ACP2E-4401 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/1c547060)_

### Katalog, GraphQL

#### GraphQl ogiltig rabattberäkning

GraphQL visar nu korrekt rabattprocentsatser och baspriser när katalogpriserna är konfigurerade att inkludera moms. Tidigare uppstod avrundningsfel, till exempel 19,99 % i stället för 20 %.

_ACP2E-3993 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/e457c5e2)_

#### GetCart GraphQL Media Gallery Field Returnerar tomma data när cacheminnet har tömts

Efter korrigeringen returneras produktens media_gallery som förväntat i svaret från GraphQL för kundvagnsbegäran.

_ACP2E-4185 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/45cbf9b6)_

### Katalog, GraphQL, sökning

#### Produktgrafql returnerade inaktiverade kategorier i kategoriaggregeringar

När korrigeringen har inaktiverats returneras inga kategorier för produkterna GraphQl-begäran.

_ACP2E-2885 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/b12ffe36)_

### Katalog, prestanda

#### Kategorier i administratören läses in mycket långsamt

Kategoriinläsningsprestanda har förbättrats avsevärt. Tidigare tog det så lång tid att läsa in kategorin som orsakade ett timeout-problem.

_ACP2E-3891 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/4ca73607)_

### Katalog, pris

#### Felaktig rabatt på katalogprisregel för underordnad produkt

Korrigerar problemet där katalogprisregeln för variationen åsidosätts av den överordnade konfigurerbara produkten, om båda reglerna har samma prioritet.

_ACP2E-3693 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/a20a6ff2)_

#### [Problem med produktpris i molnet]

Priset för paketprodukt med specialpris visas korrekt på PDP/PLP för icke-standardvaluta

_ACP2E-4110 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/6e134409)_

### Katalog, produkt

#### [Slumpmässigt fel] Fotoramalib har inte lästs in

Systemet ser nu till att Fotoramabiblioteket läses in korrekt, så att alla kopplade bilder kan visas i bildgalleriet som förväntat. Tidigare var bara den första bilden synlig på grund av ett problem med att Fotoramabiblioteket inte lästes in korrekt.

_AC-12124 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/45b51c9c) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/27217d0e)_

#### Länken Lägg till produkter manuellt ska alltid vara synlig

Ett problem har korrigerats där länken Lägg till produkter manuellt inte var synlig när en konfigurerbar produkt skapades utan befintliga konfigurationer. Länken visas nu alltid så att administratörer enkelt kan koppla enkla produkter utan att skapa dummy-konfigurationer.

_AC-13866 - [GitHub-problem](https://github.com/magento/magento2/issues/39595) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/ef666cd9)_

#### Redigera en produkt i serverdelen Tar bort extra decimaler från priser för produktalternativ

Ett problem har korrigerats där en produkt i administratörens pris för avkortade produktalternativ ändrades till två decimaler. Systemet bevarar nu priserna med högre decimalprecision, vilket säkerställer att korrekta värden bevaras efter sparandet.

_AC-14050 - [GitHub-problem](https://github.com/magento/magento2/issues/39655) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/3b5ac075)_

### Katalog, söka

#### RestAPI-begäran &#39;/rest/default/V1/categories?searchCriteria%5Bpage_size%5D=1&#39; misslyckas med timeout-fel

Kategori REST API-begäranden misslyckas inte längre med timeoutfel.
Tidigare kunde begäranden till /rest/default/V1/categories?searchCriteria[page_size]=1 misslyckas med en timeout efter vissa kodändringar.
AC-13358

_AC-13358 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/7bdafaa2)_

### Innehåll

#### graphql (magento 2.4.6-p4) - fel när försök görs att hämta cms-sidan utan aktiv status

Ett problem har korrigerats där en GraphQL-fråga om en inaktiverad CMS-sida returnerade ett internt serverfel.
Nu hämtar frågan ett korrekt svar utan fel.

_AC-12302 - [GitHub-problem](https://github.com/magento/magento2/issues/38877) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/1b1baf1d)_

#### Delningsformulär för visningslista tillåter slumpmässig kod i namnfält

Korrigerade en allvarlig SSTI-säkerhetslucka (Server-Side Template Injection) i formuläret för delning av önskelista där skadlig kod kunde anges i meddelandefältet och skickas via e-post. Uppdateringen lägger till indatavalidering för att blockera malldirektiv och osäkra mönster och visar nu ett felmeddelande när ogiltigt innehåll upptäcks.

_AC-12730 - [GitHub-problem](https://github.com/magento/magento2/issues/39024) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/01cee3c3)_

#### Att skicka csp_whitelist.xml i temat fungerar inte och ger upphov till återkommande problem

Implementerad cachelagring av CSP-vitlista per webbplatsområde.

_AC-13069 - [GitHub-problem](https://github.com/magento/magento2/issues/38933) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/39672)_

#### Efter uppgradering till magento 2.4.7 kan p2 inte se nyligen överförda filer i mediegalleriet

Nyligen överförda filer visas nu i Mediegalleriet efter uppgraderingen.
Tidigare, efter uppgradering till Magento 2.4.7 p2, visades inte nyligen överförda bilder i Mediegalleriet förrän en manuell synkronisering utfördes.
AC-13262

_AC-13262 - [GitHub-problem](https://github.com/magento/magento2/issues/39275)_

#### I mediegalleriet visas felaktiga bilder från kataloger med identiska namn men olika skiftlägen

Systemet åtgärdar nu ett problem där filer som överförts till en viss katalog i mediegalleriet också är synliga i kataloger med liknande namn men med olika skiftlägen.

_AC-13489 - [GitHub-problem](https://github.com/magento/magento2/issues/39382) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/39502)_

#### Om du tar bort en galleribild helt och hållet från omfånget behåller rollerna/typerna angivna (bas/liten/miniatyrbild) och när du har lagt till&quot;gamla&quot; roller/typer igen visas

Systemet fungerar som förväntat i lagringsomfånget. Bilderna ärver rollerna/typerna för den nya tillagda bilden enligt standardomfånget

_AC-13556 - [GitHub-problem](https://github.com/magento/magento2/issues/39481) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/39680)_

#### [Små fel] Filter för Admin Panel `listing component` kan inte påverkas när fältvärdet innehåller `\`

Systemet fungerar bra när vi filtrerar sidrubriken med snedstreck (t.ex. Magento\Store)

_AC-13661 - [GitHub-problem](https://github.com/magento/magento2/issues/39513) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/39535)_

#### Fel: Skriptfel för&quot;Magento_Catalog/js/validate-product&quot; för administratörens innehållssidbyggare med produktinläsning

Denna PR åtgärdar skriptfelet för catalogAddToCart när sidbyggaren redigeras med produktvillkoret

_AC-13891 - [GitHub-problem](https://github.com/magento/magento2/issues/39604) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/39677)_

#### catalogAddToCart-skriptfel när produktwidgeten konfigureras.

Korrigerade ett skriptfel som uppstod när widgeten Produkter konfigurerades med Villkorskombination i Page Builder. Problemet uppstod på grund av att JS-filer för klientstruktur saknas, vilket ledde till konsolfel. Efter korrigeringen läses widgeten in korrekt utan konsolfel.

_AC-13892 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/528af81a)_

#### Blockera markering i widgetar som har samma identifierare

Systemet hanterar nu markeringsblock korrekt när vi skapar widgetar när vi har samma identifieringsblock

_AC-14132 - [GitHub-problem](https://github.com/magento/magento2/issues/39692) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/39722)_

#### Loggflödet &quot;CMS-sidan med ID &quot;0&quot; finns inte&quot;

Systemet fungerar som väntat efter att admin-användaren har skapats och när vi skapar ett nytt sidsystem.log visas inga felmeddelanden

_AC-14254 - [GitHub-problem](https://github.com/magento/magento2/issues/39743) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/39746)_

#### [GraphQl] Flödesfråga, oändlig slinga

Den här biljetten åtgärdade ett problem där en GraphQL-ruttfråga med identisk sökväg för begäran och målsökväg orsakade en oändlig loop och så småningom orsakade timeout.
I 2.4.9-alpha3 returnerar frågan nu rätt felsvar i stället för slingor.

_AC-14269 - [GitHub-problem](https://github.com/magento/magento2/issues/39707) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/68a45d0a)_

#### Obefintliga platskartor svarar med produktbild

Systemet åtgärdas nu när vi får åtkomst till Unexisting platskarta svarar med produktbild med svaret: 404 NOT FOUND

_AC-14295 - [GitHub-problem](https://github.com/magento/magento2/issues/39756) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/40135)_

#### Kataloglänkswidgetar använder felaktig URL

Systemet hanterar nu widgetar korrekt efter att länken för katalogprodukt och katalogkategori har lagts till och rätt URL:er i HTML-källan visas också

_AC-14437 - [GitHub-problem](https://github.com/magento/magento2/issues/39464) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/39710)_

#### Tabellprefix beaktas inte

Adobe Commerce respekterar nu databastabellens prefix korrekt vid inläsning av Design > Configuration-temarutnätet i Admin. Tidigare i Adobe Commerce 2.4.8 med ett tabellprefix som konfigurerats i app/etc/env.php uppstod ett fel när användaren navigerade till Innehåll > Design > Konfiguration eftersom tabellprefixet inte togs med i beräkningen och rutnätet med teman inte renderades.

_AC-14556 - [GitHub-problem](https://github.com/magento/magento2/issues/39847) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/1bc2d6d0)_

#### Ändra konstanten IMAGE_FILE_NAME_PATTERN till synlig för att öka flexibiliteten

Konstanten IMAGE_FILE_NAME_PATTERN i GenerateRenditions.php har gjorts offentlig för att ge utvecklare större flexibilitet när de arbetar med bildåtergivningar. Programfixen ingår i Magento 2.4.9-alpha3 med fullständig täckning för enhets- och integreringstest.

_AC-15338 - [GitHub-problem](https://github.com/magento/magento2/issues/39733) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/68a45d0a)_

#### Felaktig leveransmetod visas på granskningsordersidan för flera leveranser

Korrigerade ett problem i en utcheckning av flera leveranser där sidan för granskningsorder visade en felaktig leveranskostnad (5 INR istället för 10 INR). Uppdateringen ser till att rätt fraktbelopp visas för varje adress.

_AC-15664 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/3cf1a106)_

#### bin/magento config:show(or set) design/theme/theme_id failed

Ett problem har korrigerats där CLI-kommandona bin/magento config:show och config:set misslyckades för sökvägen design/theme/theme_id trots att konfigurationen finns.
Nu kan kommandona köras och tillåta visning och inställning av tema-ID utan fel.

_AC-5915 - [GitHub-problem](https://github.com/magento/magento2/issues/35751) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/64823f95)_

#### Det gick inte att överföra bilden med relativt liten bredd

Systemet misslyckas inte längre med att ändra storlek på bilden med relativt liten bredd till höjden.

_ACP2E-3558 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/9608ca21)_

#### Page Builders produktkomponent fungerar inte om användaren inte har Widget-behörighet

Före korrigeringen genererades ett allmänt fel på sidan när en widget utan behörigheter öppnades och en&quot;inläsande&quot; GIF visades. Efter korrigeringen visas nu ett modalt fönster med&quot;Du måste ha behörighet att visa det här innehållet&quot;. meddelande.

_ACP2E-3664 - [GitHub-kodbidrag](https://github.com/magento/magento2-page-builder/commit/bd9181b6)_

#### Felaktig konfigurationssökväg för formatkonfiguration för fjärrlagringssökväg

När korrigeringen är klar påverkas den faktiska sökvägskonfigurationen för AWS S3 när du anger en stil för fjärrlagringssökvägen.

_ACP2E-3734 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/df92debe)_

#### Page Builder Product Widget-ordningen används inte i GraphQL

Korrigerar problemet där GraphQL&quot;rutt&quot;-frågesvaret inte returnerade produkter i rätt sorteringsordning i en Page Builder-innehållstyp.

_ACP2E-3898 - [GitHub-kodbidrag](https://github.com/magento/magento2-page-builder/commit/bd9181b6)_

#### Problem med visning av priser i icke-engelska butiker på grund av ICU-biblioteksversionen

Efter korrigeringen visas produktpriset korrekt på hebreiska (Israel).

_ACP2E-3938 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/7accebfa)_

#### Uppdaterar rensad designkonfiguration för butikskod

Korrigerar problemet där uppdateringen av lagringsvyns kod rensade designkonfigurationsinställningarna på grund av att konfigurationscachen inte uppdaterades korrekt.

_ACP2E-3941 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/462ede94)_

#### Page Builder - Product Condition Logic Issue (OR logic beter sig felaktigt med att visa färre produkter)

Page Builder Products Widget returnerar nu korrekt resultat när ett attribut med globalt omfång används i villkoret Matcha något

_ACP2E-4096 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/e457c5e2)_

#### Produktkarusellen lägger till felaktiga produkter i Page Builder

Före korrigeringen skulle en konfigurerbar produkt automatiskt ha inkluderats i produktkarusellerna för PageBuilder om någon av dess underordnade skulle ha uppfyllt filtervillkoren. Efter korrigeringen kommer den överordnade produkten endast att inkluderas om den underordnade produkten inte syns separat.

_ACP2E-4341 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/61c96348)_

#### Widgeten Produktlista returnerar ett felaktigt resultat om flera kategorier visas i kategorivillkor

Widgeten&quot;Katalogproduktlista&quot; visar nu korrekta resultat när flera kategorier i villkoret&quot;Kategori är en av&quot; visas. Tidigare bearbetades bara den första kategorin i listan.

_ACP2E-4353 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/0a3b7032) - [GitHub-kodbidrag](https://github.com/magento/magento2-page-builder/commit/1c1b3419)_

#### [Molnet] Skapande av mediegallerimappen kräver behörigheten delete_folder i Nytt mediegalleri - roller med endast create_folder kan inte skapa mappar

Innan den här korrigeringen implementerades kunde en administratörsanvändare med enbart behörighet att skapa mappar inte skapa en mapp i CMS mediegalleri. Efter korrigeringen kan innehållsskapare i mediegalleriet nu skapa mappar med enbart behörighet att skapa mappar.

_ACP2E-4376 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/61c96348)_

#### [QUANS] Duplicera en CMS-sida

Före den här korrigeringen hade duplicering av en cms-sida med anpassad layoutuppdatering misslyckats. Nu kan CMS-sidor med anpassade layoutuppdateringar dupliceras utan fel.

_ACP2E-4449 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/f7bbcb4e)_

### Kund/Kunder

#### Undantag på Storefront när Admin lägger till blocket CustomerCustomAttribute via CMS sidinnehåll

Korrigerade ett problem där ett tillägg av CustomerCustomAttribute-blocket via CMS-sidinnehåll orsakade ett butiksundantag och hindrade sidan från att läsas in.
I Storefront visas nu normalt och ett meningsfullt meddelande visas när innehållet inte kan återges, vilket undviker kritiska fel.

_AC-11004_

#### Kunder som nu använder onlineadministrationsrutnätet visar dubblettrader varje gång en användare loggar in, sedan ut och sedan in

Ett problem där administratörsrutnätet för kunder nu online visade dubblettrader när en kund loggade ut och loggade in igen har åtgärdats.
Rutnätet uppdaterar nu den befintliga posten med den senaste aktiviteten i stället för att skapa dubblettposter, vilket ger korrekt kundsessionsspårning.

_AC-11511 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/528af81a)_

#### Validering av minimum- och maxvärden fungerar inte för DOB-attribut i Storefront

Felet åtgärdade ett problem där minimal och maximal datumvalidering för attributet Födelsedatum (DOB) inte fungerade på butiken (trots att det fungerade i Admin).
I 2.4.9-alpha3 blockerar validering nu korrekt att kunder med DOB sparas utanför tillåtet intervall och ett felmeddelande visas.

_AC-13535 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/68a45d0a)_

#### Ajax 401-fel läses in på varningsskärmen på administratörspanelen när inloggning med kundtillstånd återkallas

Felet åtgärdade ett problem där en återkallad inloggning som kundbehörighet orsakade att ett Ajax 401-fel med raw HTML visades i varningsfönstret.
Efter korrigeringen visas nu ett normalt varningsmeddelande korrekt i stället för HTML i Raw-format.
Lösningen levererades i Magento 2.4.9 alpha3

_AC-15336 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/68a45d0a)_

### Ramverk

#### Kompileringskod för inaktiverad modul.

Denna pull-begäran escape inaktiverade moduler innan kodkompilering.

_AC-10933 - [GitHub-problem](https://github.com/magento/magento2/issues/38241) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/39723)_

#### Fel vid körning av kommandokonfiguration :upgrade med anpassad DB-utlösare

Anpassade databasutlösare orsakar inte längre fel under installationen :upgrade.
Tidigare kunde fel uppstå om bin/magento-installationen :upgrade kördes med en anpassad databasutlösare (t.ex. AFTER INSERT i lagringstabellen):
&quot;Varning: Försöker få åtkomst till matrisförskjutning på ett värde av typen null i vendor/magento/framework/Mview/View/Subscription.php på rad 357&quot;
AC-11487

_AC-11487 - [GitHub-problem](https://github.com/magento/magento2/issues/38481)_

#### [Problem] Gör metodsignaturen konsekvent med gränssnittet

Metodsignaturen för getAttributes är nu konsekvent med dess gränssnitt, vilket förhindrar fel när metoden skrivs över. Tidigare orsakade inkonsekvenser i metodsignaturen fel när metoden getAttributes skulle skrivas över.

_AC-11578 - [GitHub-problem](https://github.com/magento/magento2/issues/38501) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/31955)_

#### Det går inte att utöka entitetsformuläret Website/Group/Store med formulärelement med flera värden för tilläggsattribut

Denna PR tillåter formulärelement med flera värden att skicka data till webbplatsen/gruppen/butiksformuläret.

_AC-11657 - [GitHub-problem](https://github.com/magento/magento2/issues/24070) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/24094)_

#### [Problem] Korrigera verifierings-e-postregel för UI-komponent

Systemet validerar nu korrekt flera e-postadresser som anges i gränssnittskomponenterna, vilket säkerställer att varje e-postadress trimmas och valideras korrekt. Tidigare använde systemet en felaktig metod för att trimma e-postadresser, vilket kunde leda till valideringsfel.

_AC-11719 - [GitHub-problem](https://github.com/magento/magento2/issues/38528) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/33470)_

#### [Problem] Ta bort användning av scopematchare

Den här PR:en åtgärdar URL-inställningarna för administratörer globalt i stället för det aktuella arkivet

_AC-11736 - [GitHub-problem](https://github.com/magento/magento2/issues/38566) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/38554)_

#### [Problem] Ta bort överflödiga metoder

Kodkvalitet: Tog bort redundanta metoder i AsynchronousOperations- och Sales-komponenter som endast anropade överordnade metoder utan att lägga till funktioner, vilket förbättrar kodunderhållet.

_AC-11915 - [GitHub-problem](https://github.com/magento/magento2/issues/29748) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/29147)_

#### Mallen Magento_Theme title.phtml är ogiltig för PHP 8.2

Den här pull-begäran åtgärdar ett problem när en CMS-sida som skapas med rubriken null, som i PHP 8.x, skickar null till trim(), genererar ett undantag: Föråldrad funktionalitet: trim(): Överför null till parametern #1 ($string) av typen string

_AC-12856 - [GitHub-problem](https://github.com/magento/magento2/issues/39092) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/39398)_

#### xsd-validering misslyckas för etc/adminhtml/system.xml filer som innehåller kommentarer under fältobjekt.

Den här PR:en korrigerar XML-schemadefinitioner i phpstorm för kommentarnod

_AC-12945 - [GitHub-problem](https://github.com/magento/magento2/issues/39148) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/39867)_

#### Magento Version-exponering via Setup-väg med Nginx-standardkonfiguration

Systemet fungerar nu som förväntat och visar inte den exakta versionen av Magento som webbplatsen körs i

_AC-13205 - [GitHub-problem](https://github.com/magento/magento2/issues/39227) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/39228)_

#### [Problem] Packa upp objektargument som namngivna parametrar

Systemet använder nu funktionen PHP 8.1 för att packa upp arrayen med namngivna parametrar, vilket eliminerar behovet av anrop av array_values och eventuellt förbättrar den övergripande prestandan. Tidigare krävdes array_values i systemet för att dela upp objektargument.

_AC-13210 - [GitHub-problem](https://github.com/magento/magento2/issues/39233) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/37411)_

#### [Utfärdande] av refactoringcitatadress validerar metod

Denna PR innehåller läsbarhetsförbättringar av metoden doValidate.

_AC-13214 - [GitHub-problem](https://github.com/magento/magento2/issues/38230) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/38219)_

#### Magento option —magento-init-params never used when running cli?

Alternativet —magento-init-params används nu när CLI-kommandon körs.
Tidigare hade överföring av —magento-init-params till CLI-kommandon ingen effekt på parametrar som MAGE_MODE.
AC-13231

_AC-13231 - [GitHub-problem](https://github.com/magento/magento2/issues/39248) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/132b9e68)_

#### fel typdeklaration för getItemsByColumnValue

Systemet definierar nu indataparametern $value korrekt som en primitiv typ, inte en array, i funktionen getItemsByColumnValue, vilket säkerställer att funktionen returnerar den förväntade mängden. Tidigare, om en array med ett enda värde användes som indataparameter, skulle funktionen returnera null och IDE:er skulle markera det som ett fel.

_AC-13240 - [GitHub-problem](https://github.com/magento/magento2/issues/33070) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/33120)_

#### När vi använder fillagring för låsleverantören får vi en ständigt växande katalog med filer utan att någon rensning görs

Dragbegäran innehåller ett nytt cronjob som körs en gång om dagen och söker efter låsfiler som inte har ändrats de senaste 24 timmarna och som därför kan tas bort på ett säkert sätt. Detta håller innehållet i katalogen med låsfiler under kontroll.
Detta cronjob kör bara något när låsprovidern är konfigurerad att använda filer, inte när någon av de andra används (databas - standard, zookeeper eller cache)

_AC-13367 - [GitHub-problem](https://github.com/magento/magento2/issues/39369) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/39372)_

#### [Issue] Cleanup: använd inte ett void-returvärde från metodanrop.

Den här PR:en rensar lite. Ibland anropade vi metoder som inte returnerade något (void) och sedan använde vi det resultatvärdet. Det behövs verkligen inte.

_AC-13664 - [GitHub-problem](https://github.com/magento/magento2/issues/39524) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/39516)_

#### Cachenycklar som är associerade med FPC i Magento 2.4.7-multilagringsimplementationer

Korrigerade ett problem där FPC-cachenycklar (Full Page Cache) i flerlagringsinställningar inte innehöll MAGE_RUN_CODE och MAGE_RUN_TYPE, vilket orsakade inkonsekvent cachenyckelbeteende jämfört med tidigare versioner. Cachenycklarna inkluderar nu arkivkontext på rätt sätt, vilket säkerställer korrekt cacheisolering mellan butiker.

_AC-13719 - [GitHub-problem](https://github.com/magento/magento2/issues/39456) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/ae6f305b)_

#### [Problem] [PHPDOC] Korrigera felaktig bild för Magento\Framework\Message\ManagerInterface

Denna PR åtgärdar det felaktiga fotot för \Magento\Framework\Message\ManagerInterface och tar bort alla duplicerade foton i \Magento\Framework\Message\Manager (använd arvsdokumentsyntax).

_AC-14312 - [GitHub-problem](https://github.com/magento/magento2/issues/39593) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/39153)_

#### Partiell indexering fungerar inte längre för kunder med enormt många uppdateringar

Delvis indexering fungerar nu för kunder med ett stort antal uppdateringar.
Tidigare stoppades indexuppdateringarna när maxvärdet för kolumnen version_id i ändringsloggtabellen uppnåddes.
AC-14424

_AC-14424 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/7bdafaa2)_

#### Magento 2.4.8 använder dev-paket som inte följer semantisk versionshantering

Magento 2.4.8 kräver dev-versioner av pdatorparken/ptypen och phpmd/phpmd (3.x-dev) för PHP 8.4-kompatibilitet.
Dessa dev-versioner är i konflikt med verktyg från tredje part som förväntar sig SemVer-kompatibla paket, vilket förhindrar vissa uppgraderingar.
En tillfällig lösning är att aliasera dev-versionerna i Composer.json (t.ex. &quot;3.x-dev as 3.99.0&quot;), vilket möjliggör kompatibilitet samtidigt som semantisk versionshantering uppfylls.
Detta säkerställer att stödet för PHP 8.4 kan hanteras och undviker konflikter tills stabila releaser blir tillgängliga.

_AC-14519 - [GitHub-problem](https://github.com/magento/magento2/issues/39796)_

#### MView-funktionen ignorerar fel vid utlösarkörning

MView-funktionen rapporterar nu korrekt fel vid körning av utlösare.
Tidigare ignorerades fel under körning av utlösare, vilket kan leda till att indexuppdateringar saknas utan något meddelande.
AC-14567

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

#### [Problem] Inkludera konstruktor som en del av `CommandListInterface` API, utöka intern dokumentation

Den här PR-uppdateringen anger Magento\Framework\Console\CommandList som ett API och introducerar konstruktorn i CommandListInterface för bättre utbyggbarhet. Det förbättrar även textbunden dokumentation för att göra konsolkommandon tydligare och enklare att underhålla.

_AC-14680 - [GitHub-problem](https://github.com/magento/magento2/issues/31102) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/37901)_

#### [Problem] Ta bort kod som är relaterad till Microsoft IIS

Den här PR-åtgärden rensar koden som är relaterad till Microsoft IIS enligt dokumentationen för Magento-systemkrav som anger att Microsoft Windows OS inte stöds

_AC-14702 - [GitHub-problem](https://github.com/magento/magento2/issues/39910) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/39894)_

#### Syntaxfel för Förstoringsglaset.js

Funktionen för förstoringsglaset bör fortsätta att fungera som den fungerade tidigare och förstoringsalternativ bör inte vara tillgängliga i det globala omfånget

_AC-14722 - [GitHub-problem](https://github.com/magento/magento2/issues/36200) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/39321)_

#### Bakgrundsvisningsläge i CLI-kommandot `setup:db:status`

CLI-kommandot `setup:db:status` har nu stöd för utförligt läge.
Tidigare var det svårt att förstå databasändringar som krävs för uppgraderingar. Nu ger körning av `bin/magento setup:db:status -v` detaljerad information om schema- och datamässiga skillnader.
AC-14807

_AC-14807 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/7bdafaa2)_

#### SMTP-e-post som skickas med tls och 2.4.8

SMTP-mejl som skickas med TLS fungerar nu som förväntat.
Tidigare uppstod ett fel när e-post skickades via SMTP med TLS: fel :1408F10B:SSL-rutiner:ssl3_get_record:fel versionsnummer.
AC-14883

_AC-14883 - [GitHub-problem](https://github.com/magento/magento2/issues/39947) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/3717e6cb) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/8b453942) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/d3ea191d)_

#### [Problem] Åtgärda samtidighetsproblem vid distribuering av statiskt innehåll

Denna PR åtgärdar ett fel där flera samtidiga processer snurrar upp för att hantera samma temapaket, beroende på hur teman definieras med sina överordnade.

_AC-14944 - [GitHub-problem](https://github.com/magento/magento2/issues/39990) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/39954)_

#### [Problem] Ta bort tidigare kompatibilitetskod för PHP-versioner &lt; 8.1

Den här pull-begäran tar bort kod som är avsedd att köras på PHP &lt;8.1.
Borttagen kontrollerar också om PHP_VERSION_ID-kontakt är tillgänglig eftersom den är tillgänglig i alla PHP-versioner

_AC-14971 - [GitHub-problem](https://github.com/magento/magento2/issues/39891) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/39882)_

#### FPC fungerar inte vid inloggning

FPC (Full Page Cache) fungerar nu korrekt för inloggade kunder.
Tidigare lästes inte hemsidan in från cache när du loggat in och rubriken x-magento-cache-debug visade MISS i stället för HIT.
AC-14999

_AC-14999 - [GitHub-problem](https://github.com/magento/magento2/issues/40007)_

#### Lägg till generiska typer i vissa PHP-klasser för förbättrat stöd för statisk analys

Systemet använder nu en generisk typdefinition för att förbättra detta avsevärt genom att det tolkas som exakt den klass som ett metodanrop returnerar

_AC-15013 - [GitHub-problem](https://github.com/magento/magento2/issues/40017) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/40119)_

#### [Problem] förbättrar felhanteringen i SchemaBuilder

Denna PR förbättrar felmeddelandehanteringen i databasschemat. Det hjälper oss att identifiera problem utan omfattande felsökning.

_AC-15020 - [GitHub-problem](https://github.com/magento/magento2/issues/39816) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/39799)_

#### Resterande API: anrop till en medlemsfunktion getVideoProvider() på null

Ett problem har korrigerats där anrop till den konfigurerbara produkten med underordnade API returnerade ett 500 internt serverfel om en underordnad produkt bara hade en YouTube-video och inga andra bilder.
Felet orsakades av en null-referens i ExternalVideoEntryConverter.
API:t returnerar nu korrekt underordnade produkter med mediegalleriposter, inklusive externa videodata, utan att några fel genereras.
Detta garanterar att alla medietyper för underordnade produkter hämtas korrekt via REST API.

_AC-15046 - [GitHub-problem](https://github.com/magento/magento2/issues/40021)_

#### [W3C] Ta bort text/javascript från deklarationen av skripttaggen för cookie

Denna PR tog bort det onödiga attributet type=&quot;text/javascript&quot; från taggen cookie script för HTML5-kompatibilitet.

_AC-15061 - [GitHub-problem](https://github.com/magento/magento2/issues/39982) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/39983)_

#### [Problem] Åtgärda några stavfel i PHPDoc-kommentarer

Den här PR:en åtgärdar de få stavfel som finns i fotot

_AC-15075 - [GitHub-problem](https://github.com/magento/magento2/issues/40042) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/38809)_

#### [Problem] Ta bort Sprintf-användning i frasanrop

Denna PR tar bort användningen av sprintf i frasfunktionsanropet i Magento Core.

_AC-15183 - [GitHub-problem](https://github.com/magento/magento2/issues/40050) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/40033)_

#### Det går inte att indexera om alla ogiltiga i flertrådsindexerare med aktivt programlås

Det här problemet åtgärdade ett flertrådsindexeringsfel när use_application_lock var aktiverat.
Tidigare gick databaslås förlorade under parallell bearbetning, vilket gjorde att indexerarna fortfarande var i&quot;fungerande&quot; läge och utlöste SQL-fel (tabellen hittades inte).
I Magento 2.4.9-alpha3 säkerställer korrigeringen att indexerarna indexeras korrekt med programlås aktiverat.

_AC-15270 - [GitHub-problem](https://github.com/magento/magento2/issues/40102) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/68a45d0a)_

#### Otydliga/ogiltiga returtyper i Magento\Framework\Escaper

Systemet accepterar typer för metoder för att ta sig förbi när statisk analys utförs med phpstan på nivå 5

_AC-15272 - [GitHub-problem](https://github.com/magento/magento2/issues/40012) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/40114)_

#### [Utgåva] Tillåt köspecifik konfiguration att överskrida standardvärdet för max-messages

Systemet tillåter nu att den köspecifika konfigurationen överskrider standardvärdet för max-messages

_AC-15284 - [GitHub-problem](https://github.com/magento/magento2/issues/40121) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/40110)_

#### [Problem] - dubblettcache fpc för samma sida med samma fråga när lack används

Den här PR korrigerar dubbletter av helsidescacheposter när du använder Varnish genom att normalisera frågeparameterordningen, vilket säkerställer konsekventa cachenycklar för identiska begäranden.
Förbättrar träffkvoten och prestandan för cachelagrade URL-adresser med samma parametrar i olika sekvenser.

_AC-15325 - [GitHub-problem](https://github.com/magento/magento2/issues/39706) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/39704)_

#### Community-teman innehåller resurser för Commerce-utgåvans moduler

Borttagen formatresurser för endast Commerce från användarteman genom att flytta dem till deras respektive modulkataloger. Detta förhindrar att oanvänd CSS paketeras i Community Edition, vilket minskar onödig nyttolast och eliminerar statiska formatregler samtidigt som du säkerställer korrekt formatering när Commerce-moduler är aktiverade.

_AC-15347 - [GitHub-problem](https://github.com/magento/magento2/issues/21446) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/9bcd880a)_

#### [Utgåva] Lägg till lagringskod i URL:er måste vara global

Denna PR åtgärdar problemet genom att se till att inställningen&quot;Lägg till butikskod till URL:er&quot; hämtas med det globala omfånget i kärnkoden

_AC-15365 - [GitHub-problem](https://github.com/magento/magento2/issues/40069) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/40065)_

#### [Utgåva] Logga in odeklarerad plugin-fil endast om den inte är inaktiverad

Denna PR korrigerar och loggar plugin-programmet som är odeklarerat och inte används (aktiverad och saknad instans).

_AC-15386 - [GitHub-problem](https://github.com/magento/magento2/issues/40086) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/40081)_

#### [Problem] Liten rensning, borttagna dubblettnycklar från matris

Nu har små rensningar gjorts och inga fel som relaterar till arrayen har två dubblettnycklar med värdet Vikt (och högre)

_AC-15414 - [GitHub-problem](https://github.com/magento/magento2/issues/39851) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/39844)_

#### Magento 2.4.8-p2, magento/framework version 103.0.8-p2: klassen EmailMessage anropar en metod som inte finns

Klassen EmailMessage hanterar nu hämtning av e-postbrödtext korrekt.
Tidigare, i Magento 2.4.8-p2 med magento/framework version 103.0.8-p2, försökte klassen Magento\Framework\Mail\EmailMessage anropa en metod som inte finns (getTextBody) i meddelandeobjektet Symfony. Detta orsakade fel när moduler eller anpassningar från tredje part förlitade sig på den här metoden för e-postbearbetning.
Klassen EmailMessage anropar nu inte längre odefinierade metoder, vilket förhindrar dessa fel. AC-15446

_AC-15446 - [GitHub-problem](https://github.com/magento/magento2/issues/40170) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/059fd469) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/e9412b24)_

#### [Magento 2.3.x] Data/Schema Patches getAliases() orsakar fel under `setup:upgrade`

getAliases() orsakar fel under installationen:upgrade, denna PR korrigerar samma

_AC-15559 - [GitHub-problem](https://github.com/magento/magento2/issues/31396) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/38239)_

#### Ogiltig blandning av kollationer för operation

_AC-15614 - [GitHub-problem](https://github.com/magento/magento2/issues/40138) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/44329e9d)_

#### [Utgåva] [PHPDOC] Korrigera dåligt Magento\Framework\DB\Adapter\AdapterInterface::quoteColumnAs()

Den här PR uppdaterar PHPDoc för \Magento\Framework\DB\Adapter\AdapterInterface::quoteColumnAs() för att korrekt visa att parametern $alias kan vara null förutom strängen. Detta åtgärdar PHPStan-problem på nivå 5+ och förbättrar verktygskompatibiliteten för kodkvalitet.

_AC-15626 - [GitHub-problem](https://github.com/magento/magento2/issues/39598) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/39581)_

#### Ogiltig blandning av kollationer i urlrewrite-modulen

_AC-15647 - [GitHub-problem](https://github.com/magento/magento2/issues/40189) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/44329e9d)_

#### Villkoret uppfylls aldrig i `\Magento\Framework\Escaper::escapeScriptIdentifiers`

Ett onåbart villkor i \Magento\Framework\Escaper::escapeScriptIdentifiers har korrigerats genom att kontrollen för false har ersatts med null, den har justerats med preg_replace-returvärden och kodexaktheten har förbättrats utan att funktionaliteten påverkades.

_AC-15667 - [GitHub-problem](https://github.com/magento/magento2/issues/40195) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/cc0ec250)_

#### Slutversion 7.3 (senaste versionen) - Underkategorier länkar/alternativ i standardkategorin visas inte på förstasidan i Store

Bekräftat att saknade underkategorilänkar på butikens startsida när du använde Varnish 7.3 orsakades av ESI-begäranhantering och serverkonfiguration snarare än en Magento-kodsdefekt. Problemet löses genom rekommenderade Varnish-konfigurationsjusteringar, utan några viktiga kodändringar.

_AC-15674 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/3cf1a106) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/9a62604c)_

#### [Problem] Lägg till extra felsökningsdata i loggen `cache_invalidate`

Denna PR förbättrade loggen cache_invalidate så att den innehöll begärandekontext och stackspårning för tömning av hela cacheminnet, vilket förbättrade felsökning och synlighet.
Detta hjälper till att identifiera källan till oväntade kompletta cacheminnen utan att ändra befintliga funktioner.

_AC-15719 - [GitHub-problem](https://github.com/magento/magento2/issues/40204) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/40196)_

#### [Problem] Förbättrad undantagslista för automatisk inläsare för disposition lite grann.

Den här PR förfinar undantag för automatisk inläsning av Composer så att testklasser hoppas över, vilket minskar onödiga inmatningar av klassscheman och förhindrar PSR-4-varningar.

_AC-15743 - [GitHub-problem](https://github.com/magento/magento2/issues/40109) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/40107)_

#### [Utgåva] Förhindra `db_schema.xml` deklarationer med `comment=""` från att bryta driftsättningar utan driftstopp

Systemet förhindrar nu att db_schema.xml-deklarationer med comment=&quot;&quot;&quot; bryter ned driftsättningar utan driftstopp

_AC-15980 - [GitHub-problem](https://github.com/magento/magento2/issues/40254) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/40242)_

#### Det går inte att rensa `\Magento\Framework\Filesystem\Glob::glob(...)`-cachen

Den här PR-uppdateringen introducerar ett sätt att rensa det interna statiska cacheminnet som används av \Magento\Framework\Filesystem\Glob, vilket säkerställer nya och korrekta resultat när filstrukturen ändras. Det förbättrar tillförlitligheten och utvecklingsupplevelsen, särskilt i testscenarier och långvariga processer där resultatet från glob måste vara uppdaterat.

_AC-15989 - [GitHub-problem](https://github.com/magento/magento2/issues/35741) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/35742)_

#### URL:en för länken ReadME Leaders har en permanent omdirigering

Länken README Leaders uppdaterades genom att den permanent omdirigerade och utgångna URL:en ersattes med korrekta fungerande länkar, vilket säkerställer att medverkande och underhållssidor öppnas korrekt.

_AC-16046 - [GitHub-problem](https://github.com/magento/magento2/issues/40292) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/913bf1a6)_

#### [Problem] [PHPDOC] Korrigera felaktig Magento\Eav\Model\ResourceModel\Entity\Attribute\Collection

PHPDoc-anteckningar för joinLeft() i samlingen Attribute har korrigerats för att tillåta korrekta arraydefinitioner, vilket förbättrar kodens korrekthet och kompatibilitet med verktyg som PHPStan.

_AC-16187 - [GitHub-problem](https://github.com/magento/magento2/issues/40354) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/39155)_

#### Kontrollera att ett enda kommandofel loggar felet (fil eller stderr) utan att stoppa körningen av efterföljande CLI-kommandon.

Systemet ser nu till att ett enda kommandofel loggar felet (fil eller stderr) utan att stoppa körningen av efterföljande CLI-kommandon

_AC-16244 - [GitHub-problem](https://github.com/magento/magento2/issues/40006) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/40063)_

#### [Problem] Lägg till int-typ till $maxAge i PageCache-kerneln

Den här PR-funktionen ser till att parametern $maxAge i PageCache-kerneln är strikt typbestämd som ett heltal för att förbättra typsäkerheten och förhindra PHPStan/statiska analysfel vid cachehantering.

_AC-16313 - [GitHub-problem](https://github.com/magento/magento2/issues/40438) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/36600)_

#### Lägg till i varukorgshändelse: tomma priser

Ett problem där produktpriser returnerades som null i checkout_cart_product_add_after-händelseövervakaren under processen för att lägga till i varukorgen har korrigerats.
Nu hämtas baspriset och tillhörande prisvärden korrekt, vilket garanterar att korrekta data finns tillgängliga för observatörer och anpassade implementeringar.

_AC-5966 - [GitHub-problem](https://github.com/magento/magento2/issues/35638) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/3b5ac075)_

#### PHP8.1 type bugfix

De associerade produkterna initieras nu till en tom array i stället för till false när det strikta behandlingsläget inte är aktivt eller när produktinformation är tillgänglig. Denna förändring säkerställer att den efterföljande logikhanteringen av tillhörande produkter fungerar på ett konsekvent sätt, vilket förbättrar stabiliteten och förutsägbarheten i produktberedningsprocessen.

_AC-6017 - [GitHub-problem](https://github.com/magento/magento2/issues/35808) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/35842)_

#### Förväntad typ: Magento\Customer\Api\Data\GroupInterface. Hittade Magento\Customer\Model\Group.

Ett problem har korrigerats där ett typfel uppstod när en kundgrupp sparades via GroupRepositoryInterface med GroupFactory.
Tidigare förväntades GroupInterface i databasen, men gruppmodellinstanser skickades, vilket resulterade i ett allvarligt fel.
Nu kan kundgrupper sparas i databasen på ett korrekt sätt genom en korrekt gränssnittsimplementering.
Detta åtgärdar IDE-varningar och körningsfel när kundgrupper skapas eller uppdateras programmatiskt.

_AC-6909 - [GitHub-problem](https://github.com/magento/magento2/issues/36269)_

#### Fältvalidering för kreditnotor

Ett problem har korrigerats där fältvalidering på kreditnotssidan hindrade inskickning även efter att obligatoriska anpassade fält fylldes i.
Valideringen fungerar nu korrekt och skicka-knappen aktiveras när alla obligatoriska fält har fyllts i.

_AC-8308 - [GitHub-problem](https://github.com/magento/magento2/issues/37182) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/64823f95)_

#### [Problem] Ta bort ej tillåten `@author` tagg från ramverket (del 3)

Systemet följer nu kodstandarderna genom att ta bort den förbjudna taggen `@author` från vissa moduler, vilket förbättrar den övergripande kodkvaliteten. Tidigare var förekomsten av den här taggen i vissa moduler ett brott mot de fastställda kodstandarderna.

_AC-8343 - [GitHub-problem](https://github.com/magento/magento2/issues/37270) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/37020)_

#### [Utgåva] Använda egenskapshöjning för konstruktor i modulen Skicka QL-diagram för vän

Systemet utnyttjar nu befordring av konstruktoregenskaper i GraphQL-modulen&quot;skicka vän&quot;, vilket förbättrar kodläsbarheten och minskar komplexiteten. Tidigare använde modulen egenskaper som upptog flera rader, vilket gjorde koden mer komplex och mindre läsbar.

_AC-8346 - [GitHub-problem](https://github.com/magento/magento2/issues/37235) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/37197)_

#### [Utgåva] Ta bort förbjuden `@author` -tagg

Den här PR-funktionen tar bort taggen `@author` från kodbasen

_AC-8349 - [GitHub-problem](https://github.com/magento/magento2/issues/37266) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/37016)_

#### [Utgåva] Ta bort förbjuden `@author` -tagg

Den här PR-funktionen tar bort taggen `@author` från kodbasen

_AC-8350 - [GitHub-problem](https://github.com/magento/magento2/issues/37265) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/37015)_

#### [Problem] Ta bort ej tillåten `@author`-tagg från `Magento_Downloadable`

Systemet följer nu kodstandarderna genom att ta bort den förbjudna taggen `@author` från vissa moduler, vilket förbättrar den övergripande kodkvaliteten. Tidigare var förekomsten av den här taggen i vissa moduler ett brott mot de fastställda kodstandarderna.

_AC-8355 - [GitHub-problem](https://github.com/magento/magento2/issues/37251) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/37001)_

#### [Utgåva] Ta bort förbjuden `@author` -tagg

Systemet följer nu kodstandarderna genom att ta bort den förbjudna taggen `@author` från vissa moduler, vilket förbättrar kodkvaliteten och konsekvensen. Tidigare var förekomsten av den här taggen i vissa moduler ett brott mot de fastställda kodstandarderna.

_AC-8358 - [GitHub-problem](https://github.com/magento/magento2/issues/37264) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/37014)_

#### [Utgåva] Ta bort förbjuden `@author` -tagg

Den här PR-funktionen tar bort taggen `@author` från kodbasen

_AC-8359 - [GitHub-problem](https://github.com/magento/magento2/issues/37262) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/37012)_

#### [Utgåva] Ta bort förbjuden `@author` -tagg

Systemet följer nu kodstandarderna genom att ta bort den förbjudna taggen `@author` från vissa moduler, vilket förbättrar den övergripande kodkvaliteten. Tidigare var förekomsten av den här taggen i vissa moduler ett brott mot de fastställda kodstandarderna.

_AC-8360 - [GitHub-problem](https://github.com/magento/magento2/issues/37261) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/37011)_

#### [Utgåva] Ta bort förbjuden `@author` -tagg

Systemet följer nu kodstandarderna genom att ta bort den förbjudna taggen `@author` från vissa moduler, vilket ger en renare och mer standardiserad kod. Tidigare var förekomsten av den här taggen i vissa moduler ett brott mot de fastställda kodstandarderna.

_AC-8361 - [GitHub-problem](https://github.com/magento/magento2/issues/37260) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/37010)_

#### [Utgåva] Ta bort förbjuden `@author` -tagg

Den här PR-funktionen tar bort taggen `@author` från kodbasen

_AC-8362 - [GitHub-problem](https://github.com/magento/magento2/issues/37259) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/37009)_

#### [Utgåva] Ta bort förbjuden `@author` -tagg

Systemet följer nu kodstandarderna genom att ta bort den förbjudna taggen `@author` från vissa moduler, vilket förbättrar den övergripande kodkvaliteten. Tidigare var förekomsten av den här taggen i vissa moduler ett brott mot de fastställda kodstandarderna.

_AC-8363 - [GitHub-problem](https://github.com/magento/magento2/issues/37258) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/37008)_

#### [Problem] Ta bort ej tillåten `@author`-tagg från `Magento_Backup` och `Magento_Bundle`

Den här PR-funktionen tar bort taggen `@author` från kodbasen

_AC-8367 - [GitHub-problem](https://github.com/magento/magento2/issues/37244) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/36979)_

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

#### [Problem] Korrigera variabelnamn i katalogsökning

Systemet namnger nu variabler korrekt i sökmotormodulen, vilket förbättrar kodklarheten och underhållet. Tidigare användes ett irrelevant variabelnamn, $defaultCountry, i sökmotormodulen, vilket orsakade förvirring.

_AC-9215 - [GitHub-problem](https://github.com/magento/magento2/issues/37810) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/33533)_

#### allow_parallel_generation ska anges via systemvariabeln

Efter korrigeringen kan miljövariabeln &quot;MAGENTO_DC_CACHE_ALLOW_PARALLEL_GENERATION&quot; användas för att ställa in konfigurationen &quot;allow_parallel_generation&quot;.

_ACP2E-3673 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/b12ffe36)_

#### [Cloud] Om du ändrar tabellkolumntyp från Int till Decimal med filen db_schema.xml i Magento 2 uppstår fel

Det går inte att ändra kolumndatatypen korrekt. Tidigare uppstod ett fel: Attributet identity är inte tillåtet.

_ACP2E-3709 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/df92debe)_

#### Stöd för nya valutor (XCG) i Adobe

Karibien Guilder (XCG) läggs till i valutalistan.

_ACP2E-3790 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/520f9e30)_

#### Problem med uppgradering 2.4.7-p5 på grund av ny validering

Korrigerade ett problem i klassen SchemaBuilder där en odefinierad matrisnyckel, kolumn, orsakade en krasch när scheman skapades eller uppdaterades. Detta inträffade när tabelldata som inte innehöll någon kolumnnyckel bearbetades.

_ACP2E-3871 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/9ad7d277)_

#### [QUANS]Serverproblem som kan orsakas av ogiltig S3-åtkomstnyckel

Felaktiga inloggningsuppgifter för AWS S3 gör inte längre att sidorna läses in oändligt på butiken.

_ACP2E-3890 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/2a1e1e55)_

#### [KVANS] [Molnet] Minify fungerar inte

Följande JS-filer är nu fullständigt och korrekt minimerade när JS-minification är aktiverat: mage/backend/tabs.min.j, jquery/jquery.validate.min.js och Magento_PageBuilder/js/form/element/validator-rules-mixin.min.js. Därför fungerar fältvalidering av CSS-klassen i Page Builder som förväntat.

_ACP2E-3925 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/47721be6)_

#### PHP8.4-undertryckningsfel: E_USER_ERROR efter uppgradering till Adobe Commerce 2.4.8

*INGA VERSIONSINFORMATION KRÄVS*
Kundorienterade scenarier påverkas inte av korrigeringen.

_ACP2E-3963 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/7accebfa)_

#### Cron-jobbet rensade inte databastabellen, vilket orsakade avbrott på grund av Galera-krasch

Rensa tabeller i ändringsloggar körs nu i grupper för att undvika stora raderingsåtgärder.

_ACP2E-3995 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/52f46328)_

#### Ej minifierad JS läser ibland in ignorerar&quot;aktivera js minifications&quot;

Före korrigeringen begärdes några av JS-filerna utan &quot;min&quot;-prefixet, vilket resulterade i 404-statuskod, även om du hade minification aktiverat. När miniatyrbildsfunktionen är aktiverad efterfrågas inga icke-minifierade JS-resurser.

_ACP2E-4058 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/6dd3fa99)_

#### Datumattribut i anpassad attributgrupp kan inte visa datumväljare i administratör

Ett problem har korrigerats där kalenderpopup-fönstret för datumattribut visades utanför skärmen när det tilldelats anpassade attributgrupper.

_ACP2E-4060 - [GitHub-problem](https://integration-5ojmyuq-3ssteurpe3xzy.us-5.magentosite.cloud/) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/6dd3fa99)_

#### Kontroll av behörighet för produktionsåtkomstkontrollista orsakade prestandaförsämring - metoden populateAcl är flaskhalsen

Optimerad bearbetning av ACL-regler

_ACP2E-4114 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/98f028ab)_

#### Checkout not loading in latest version with AC-15867 + ACP2E-4296 and SCD compact

Före korrigeringen kunde anpassade javascript-skript ha lästs in via head-avsnittet ha orsakat problem. När den nya inställningen har introducerats kan sådana skript förskjutas automatiskt, vilket ger bättre kompatibilitet med Magento 2-ramverket.

_ACP2E-4319 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/1c547060)_

#### Föråldringsvarning: använd stund.updateLocale(localeName, config) för att ändra en befintlig språkinställning. minute.defineLocale(localeName, config)

Innan korrigeringen utfördes utlöstes en varning i webbläsarkonsolen. Efter korrigeringen visas ingen sådan varning längre.

_ACP2E-4338 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/2687b487)_

#### Inkompatibelt med MariaDB 10.11

Tidigare gick det inte att installera den senaste Magento 2-versionen med MariaDB 10.11, vilket förhindrar att installationsprocessen slutförs. Problemet löstes genom att databaskompatibilitetshantering uppdaterades för att ge stöd åt MariaDB 10.11.x under installationen.

_ACP2E-4367 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/31258bf6)_

### Framework, Search

#### OpenSearch 2.19.1 illegal_argument_exception i kategorier med ett pris

OpenSearch genererar inte längre ett illegal_argument_exception för de kategorier som innehåller alla produkter med samma pris. Tidigare fanns det ett undantag, [from]-parametern, som inte kan vara negativ.

_ACP2E-3896 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/3ad96f6a)_

### GraphQL

#### En beställning i GraphQL har genomförts med en ogiltig leveransmetod

Korrigerade ett problem där beställningar kunde göras via GraphQL med en inaktiverad eller ogiltig leveransmetod.
Systemet validerar den valda leveransmetoden och returnerar ett fel om den inte är tillgänglig, vilket förhindrar att ordern skapas.

_AC-10472 - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/38268) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/a8cf637b)_

#### Ett undantag genererades när GraphQl-frågan kördes

Korrigerade ett problem där en GraphQL-fråga genererade ett undantag på grund av en ogiltig sorteringsparameter. Efter korrigeringen körs frågan utan att fel eller undantagsloggar genereras.

_AC-14835 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/a8cf637b)_

#### Internt serverfel vid tillägg av presentkortsprodukt i kundvagn via AddProductsToCart Mutation inklusive custom_attributesV2

Löste ett internt serverfel som utlöstes när presentkortsprodukter (och liknande anpassade alternativ) lades till i kundvagnen via GraphQL med custom_attributesV2. Korrigeringen hanterar komplexa attributvärden på rätt sätt, vilket gör att produkter kan läggas till utan fel.

_AC-15856 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/7fa400a7)_

#### Null-fält i frågan `Country`

Ett problem har korrigerats där beställningar som innehåller virtuella, återfinansierade och levererade artiklar behandlades eftersom virtuella artiklar inkluderas i beräkning av levererad kvantitet, vilket gör att ordertillståndet kan slutföras korrekt.

_AC-7731 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/ef666cd9)_

#### GraphQL-frågan &quot;customerOrders&quot; med attributet &quot;number&quot; orsakar ett internt serverfel

Ett problem har korrigerats där GraphQL customerOrders-frågan returnerade ett internt serverfel när nummerfältet begärdes.
Upplösaren returnerar nu orderns inkrement-ID korrekt, vilket gör att frågan kan köras och ordernumret hämtas.

_AC-8949 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/3b5ac075)_

#### GraphQL-svar för orderplacering innehåller inte något undantagsmeddelande

Återställde tidigare ändring som returnerade fel i ett annat format. Nu returneras potentiella fel på ett konsekvent sätt, inte GraphQL-schemat. Detta bör läggas till som känd BIC, godkänd av PM här: https://jira.corp.adobe.com/browse/ACP2E-3399?focusedId=45248897&amp;page=com.atlassian.jira.plugin.system.issuetabpanels:comment-tabpanel#comment-45248897

_ACP2E-3399 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/9608ca21)_

#### GraphQL-svar för orderplacering är delvis lokaliserat

Fel som returnerades av placeOrder GraphQl-mutationen var inte helt lokaliserade. I ett flerspråkigt sammanhang översätts nu felen korrekt.

_ACP2E-3506 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/9608ca21)_

#### Samtidiga anrop för att ändra ordning på GraphQL API - samma produkter har lagts till på olika rader

Korrigerar problemet där samtidiga anrop till API:t för att ändra ordning för GraphQL resulterar i att samma produkter läggs till som olika rader, vilket leder till inkonsekventa data.

_ACP2E-3774 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/c8ba4ab1)_

#### updateCustomerEmail GraphQL mutation(Change email Address) utlöser inte e-postmeddelandet

Tidigare skickades inte e-post till kunder efter att deras e-postadresser uppdaterats på deras konton. När korrigeringen har tillämpats får kunderna nu e-postmeddelanden när de har uppdaterat sina e-postadresser.

_ACP2E-3785 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/c8ba4ab1)_

#### Dynamiskt attribut uppdateras inte i presentregistret via updateGiftRegistry Mutation

Före den här korrigeringen via mutationen updateGiftRegistry ändrades eller uppdaterades inte det anpassade attributet i presentregistret via GraphQL-mutationer. När korrigeringen har tillämpats kan presentregistrets dynamiska attribut uppdateras med mutationen updateGiftRegistry.

_ACP2E-3805 - [GitHub-problem](https://mcstaging.briscoes.co.nz/)_

#### Customer Order GraphQL: Retrieve product categories for the associated product is &quot;not visible individual

Före korrigeringen, om ordern innehöll en dold produkt, skulle dess kategorier visa en tom array i kundorderns GraphQl-svar.
Efter korrigeringen ingår nu produktkategorierna i svaret på en begäran om kundorder GraphQl, även om produkten är dold.

_ACP2E-3945 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/2a1e1e55)_

#### Önsklisteobjekt delas inte mellan butiksvyer på en webbplats i en GraphQL-begäran

Före korrigeringen filtrerades önskelisteobjekten efter arkiv-ID. Efter korrigeringen filtreras önskelisteobjekten efter webbplats.

_ACP2E-3987 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/2a252ae6)_

#### [Cloud] getRemoteAddress returneras 127.0.0.1 i produktionen

Innan den här korrigeringen utfördes bestämdes inte fjärradressen korrekt när programservern användes. När korrigeringen är klar bestäms fjärradressen korrekt i kombination med rätt rubrikinställningar i nginx- och rubrikkonfiguration.

_ACP2E-3991 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/47721be6)_

#### [KVANS] Bekräfta omkonvertering av GQL-orderplaceringsundantagshantering

Motverkande inkompatibel ändring för placeOrder-mutation har åtgärdats.

_ACP2E-4031 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/52f46328)_

#### Felmappning av översatt meddelande till felkod vid beställning via GraphQL

Korrigerade ett fel när ett översatt undantagsmeddelande användes för att mappa felkoden för GraphQL-begäranden, vilket orsakade okända felkoder för kända fel.

_ACP2E-4033 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/fab20b00)_

#### [CLOUD] Kundorderfilter fungerar inte för datum

När du har åtgärdat problemet returneras rätt resultat om du hämtar order via GraphQL med ett datumintervallfilter.

_ACP2E-4090 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/a1c57b2e)_

#### Åtgärda problem som uppstod i AVS2E-4031

Före korrigeringen gav inte felnodpositionen sömlös kompatibilitet med versionerna 2.4.7 och 2.4.9. Efter korrigeringen placeras felnoden korrekt för att passa båda versionerna.

_ACP2E-4115 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/e457c5e2)_

#### Paket med överordnad som visar slut på lager även om det underordnade objektet har inlager i Graphql-anrop

Efter korrigeringen returnerar en begäran om en produktlista med GraphQL rätt lagerstatus för paketprodukter.

_ACP2E-4168 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/a1c57b2e) - [GitHub-kodbidrag](https://github.com/magento/inventory/commit/5632fb5e)_

#### GraphQL Exception in SWAT

Efter korrigeringen justeras svaren för GraphQL-begäranden efter GraphQL över HTTP-specifikationerna. En 4XX-svarskod returneras när det är omöjligt att analysera begäran, om begäran inte är auktoriserad eller om det finns ett annat allmänt problem med begäran. Om begäran tolkas och kan behandlas returneras en svarskod på 200.

_ACP2E-4194 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/45cbf9b6)_

#### Produkten tas inte bort från jämförelselistan efter att listan har tilldelats kunden

När en gästanvändares jämförelselista har tilldelats ett kundkonto kan produkter som lagts till som gäst nu tas bort av kunden.
Tidigare gick det inte att ta bort objekt som lagts till av gästen eftersom de inte länkats korrekt till kundens konto efter tilldelningen.

_ACP2E-4244 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/c135fc3a)_

#### updateCartItems GraphQL - felaktigt felsvar

Tidigare returnerades ett felmeddelande med en felkod tillsammans med den begärda kvantiteten och prisberäkningen, även om artikeln inte var tillgänglig, när en GraphQL-begäran för en artikel med otillräckligt antal gjordes. När den här korrigeringen har tillämpats returneras ett felmeddelande med en felkod och artikelns kvantitet ställs in på dess gamla värde om den inte är tillgänglig i svaret.

_ACP2E-4283 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/cbca0396)_

#### Gästordertilldelningsfel för flera webbplatser i plugin-programmet MergeGuestOrder

Före korrigeringen övervägde inte kundtilldelningen för en gästorder vilka kontodelningsalternativ som fanns. Efter korrigeringen tilldelas en kund en order om kunden och orderbutiken matchar (eftersom alternativet för kundkontodelning är inställt på Per webbplats).

_ACP2E-4312 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/c135fc3a)_

### GraphQL, Inventory / MSI

#### Problem med only_x_left_in_stock i Magento 2 GraphQL - Felaktig beräkning vid användning av tröskelvärden

Ett problem har korrigerats där GraphQL-fältet only_x_left_in_stock returnerade null på grund av felaktigt dubbelavdrag av MinQty. Beräkningen korrigerades så att det nu returnerar korrekt lagervärde baserat på tröskelvärden.

_AC-15832 - [GitHub-kodbidrag](https://github.com/magento/inventory/commit/35458c7f)_

#### GraphQL mergeCart - mutationsavvikelser

Efter korrigeringen kontrollerar de kundvagnar som GraphQL begär produktkvantiteten med hänsyn till lagerkonfigurationen.

_ACP2E-4184 - [GitHub-kodbidrag](https://github.com/magento/inventory/commit/5632fb5e)_

### GraphQL, produkt

#### Produktgraf saknar media_type i MediaGalleryInterface

MediaGallery GraphQL-begäran innehåller nu fältet &quot;types&quot; (Typer) för produktbildtyper. Tidigare fanns inte det här typfältet i GraphQL-begäran för MediaGallery.

_ACP2E-3880 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/3ad96f6a)_

### GraphQL, säkerhet

#### Återställning av kundens lösenord via GraphQL följer inte begränsningarna

Löste ett problem där begäranden om återställning av kundlösenord som gjorts via GraphQL-mutationer inte uppfyllde de lösenordsåterställningsbegränsningar som konfigurerats under Store > Konfiguration > Kunder > Kundkonfiguration > Lösenordsalternativ. Dessa inställningar används nu korrekt.

_ACP2E-3992 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/6dd3fa99)_

### Importera/exportera

#### [Problem] Åtgärda parametertyp

Korrigerade en felmatchning av parametertyp i import-/exportmodulen där ett värde som tidigare definierats som en sträng nu är korrekt inställt som en array. Detta justeras mot den förväntade inmatningen från exportkontrollenheten och förhindrar statiska analysvarningar.

_AC-11665 - [GitHub-problem](https://github.com/magento/magento2/issues/38529) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/64823f95)_

#### [Utgåva] Kopiera: ändra &quot;kopiera&quot; till &quot;kopiera&quot;

PR korrigerar den mindre kopieringsredigeringen för att korrigera stavningen av&quot;kopiering&quot;

_AC-13300 - [GitHub-problem](https://github.com/magento/magento2/issues/39311) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/39307)_

#### REST-slutpunkt Produktimport Json validerar inte de obligatoriska fälten

Namnfält krävs nu när nya produkter skapas via importprocessen (admin eller API). Före korrigeringen kunde du ha skapat nya produkter utan namn, vilket hade brytt administratörsgränssnittet och skapat ogiltiga produkter.

_ACP2E-3660 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/df92debe)_

#### Alternativet Webbplatsfilter saknas i exportprocessen

Nu går det att filtrera produkter efter webbplatser när du skapar produktexporter.

_ACP2E-3720 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/520f9e30)_

#### Duplicera AC-13913 - Statisk attributrensning asynkront.

Efter korrigeringen finns det inget &#39;odefinierad matrisnyckel&#39;-fel när flera instanser av \Magento\CatalogImportExport\Model\Import\Product\Type\AbstractType skapas.

_ACP2E-3752 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/520f9e30)_

#### Csv-produktimport: Det går inte att ta bort en färgrutebild

Före korrigeringen kunde du inte uppdatera färgrutebilden för en produkt via produktimporten. Efter korrigeringen kommer bilden att döljas om du markerar produktfärgrutebildskolumnen med den konfigurerade tomma markören.

_ACP2E-3972 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/2a1e1e55)_

#### Produktimport genererar tomma URL:er för butiksomfånget

Produkt-URL-nyckeln i butiksvyn ärver nu det värde som angetts i standardomfånget om url_key har ett tomt värde i importdatakällan. Om du tidigare angav url_key som ett tomt värde i importdatakällan för en lagringsvypost skulle url_key åsidosättas med ett tomt värde i det omfånget.

_ACP2E-4038 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/52f46328)_

#### Produktimportprocessen stöter på ett fel om ett flervalsattribut är konfigurerat enligt behov

Ett problem där produktimporten misslyckades har åtgärdats om ett obligatoriskt attribut av typen multi-select inkluderades. Datavalideringen går nu att utföra korrekt, vilket innebär att produktimporten kan slutföras.

_ACP2E-4057 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/a1c57b2e)_

#### [CLOUD] Produkter utan restorder har valts för att hantera lager och tillåter fortfarande kunder att beställa över våra lagernivåer när de importeras

Efter korrigeringen går det inte längre att importera ett ogiltigt värde för attributet allow_backorders för produkten.

_ACP2E-4116 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/a1c57b2e)_

#### Produktimport misslyckades på grund av en beskrivning som är längre än 65 536 tecken Validering

Efter korrigeringen kan du importera produktattribut med text vars värden överstiger 65 536 tecken.

_ACP2E-4119 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/a1c57b2e)_

#### Exportera filter för produkt - ja-nej-attribut fungerar inte som förväntat

Efter korrigeringen innehåller exporterade produkter som filtrerats med attributet Ja/Nej de förväntade produkterna som respekterar de använda filtren.

_ACP2E-4160 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/ee918f0d)_

#### Problem med priset för uppdateringspaket per webbplats via Importera

Nu går det att exportera och importera urvalspriser för paket per webbplats

_ACP2E-4243 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/98f028ab)_

#### Det går inte att importera en kund med en e-postadress i versaler

Korrigerade ett odefinierat matrisnyckelfel vid import av kunder med e-post med versaler när Kontodelning är inställt på Global. Normalisering av e-postmeddelanden är nu konsekvent genom hela importprocessen, vilket säkerställer att kunderna kan importeras oavsett e-postfall. Kontodelningsbeteendet på webbplatsnivå ändras inte.

_ACP2E-4373 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/31258bf6)_

### Importera/exportera, Kund/Kunder

#### Administratören kan importera kunder med ett födelsedatum som är senare än dagens datum

Korrigerade ett problem där administratörer kunde importera kunder med ett födelsedatum som angetts i framtiden. Systemet validerar nu DOB-filen under importen, visar ett fel för ogiltiga poster och förhindrar att kunder med framtida födelsedatum importeras, vilket ger korrekta kunddata.

_AC-13641 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/8670a2b4)_

### Lager/MSI

#### Butiksplockning respekterar inte maximal sökradie när adressen ändras vid utcheckning

Den förvalda butiken i&quot;Plocka i butik&quot; uppdateras om leveransadressen ändras. Tidigare ändrades inte butiken när den väl hade valts ut, även om den nya leveransadressen inte ligger inom den valda butikens radie

_ACP2E-3728 - [GitHub-kodbidrag](https://github.com/magento/inventory/commit/07620383)_

#### Ingen butik är tillgänglig efter omdirigering till startsidan och kassan

Tidigare valda butiker väljs nu i förväg i leveranserna&quot;Välj i butik&quot; om kunden navigerar till betalningssidan, sedan återgår till startsidan och slutligen går tillbaka till utcheckningssidan. Tidigare rensades den valda butiken i&quot;Plocka i butik&quot; efter att du upprepade gånger gått tillbaka till utcheckningssidan.

_ACP2E-3793 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/a20a6ff2) - [GitHub-kodbidrag](https://github.com/magento/inventory/commit/62c0d79b)_

#### Raderingsåtgärden för Stock slutförs inte

Efter korrigeringen leder borttagning av ett källobjekt inte till en fullständig omindexering och uppdaterar bara de produkter som påverkar prestandan.

_ACP2E-3917 - [GitHub-kodbidrag](https://github.com/magento/inventory/commit/ee0bf4ad)_

#### [MSI] Ingen indikation i administratören om kunden fick ett asynkront meddelande om att beställningen är klar för hämtning

Tillagd i orderhistorikmeddelanden om kunden har underrättats asynkront om att beställningen är klar för hämtning

_ACP2E-3968 - [GitHub-kodbidrag](https://github.com/magento/inventory/commit/29653b1d)_

#### Dubblerade Stock-statusfrågor vid offertinläsning

Dubblettkörning av frågan catalog_stock_status vid inläsning av en offert på butiken har åtgärdats, vilket orsakar redundanta DB-anrop.

_ACP2E-4102 - [GitHub-kodbidrag](https://github.com/magento/inventory/commit/fc15a9ae)_

#### Efter korrigering av ACP2E-4118: Stock-tröskeländring i Admin orsakar negativa försäljningssiffror och felaktig lagerstatus

Lagerlagerstatus justeras nu automatiskt när globala lagerkonfigurationer Kvantitet, Restorder och Utanför lager uppdateras via import.

_ACP2E-4142 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/a1c57b2e) - [GitHub-kodbidrag](https://github.com/magento/inventory/commit/5632fb5e)_

#### Administratörsrapporten [CLOUD] visar inte information när lagret uppdateras

Ändringarna av produktinventeringskällan loggas nu av loggningsmodulen. Före korrigeringen loggades ingen information när en produkt sparades och lagerrelaterade ändringar utfördes.

_ACP2E-4167 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/cbca0396) - [GitHub-kodbidrag](https://github.com/magento/inventory/commit/76b88f7c)_

#### Paketet kan inte läggas till i varukorgen när det är markerat som i lager

Bundle-produktlagerstatus återspeglar nu korrekt underordnade produktreservationer och tröskelvärden som ligger utanför lagret.
Tidigare markerades paketprodukter som&quot;i lager&quot; även när en eller flera underordnade produkter saknade tillräcklig säljbar kvantitet. Detta ledde till&quot;Inte tillräckligt många artiklar för försäljning&quot;-fel när paketet lades till i kundvagnen.

_ACP2E-4220 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/cbca0396) - [GitHub-kodbidrag](https://github.com/magento/inventory/commit/76b88f7c)_

#### Grupperad produkt visas felaktigt som Utanför lager på PDP efter import från CSV när underordnad har tilldelats en anpassad källa/aktie (fast efter manuell omindexering)

Efter korrigeringen utförs en ny indexering automatiskt när en sammansatt produkt skapas med import, vilket gör produkten tillgänglig utan att behöva indexeras om manuellt.

_ACP2E-4233 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/98f028ab) - [GitHub-kodbidrag](https://github.com/magento/inventory/commit/5704166a)_

#### [MSI] Misslyckade MFTF-tester relaterade till de senaste huvudlinjeändringarna.

Innan de gästkunder som valde Pickup i butik utan leveransadress korrigerades fylldes fakturaadressen automatiskt i med butikens adress, som inte kunde ändras, vilket ledde till felaktig fakturainformation. När den fasta faktureringsadressen nu är redigerbar i det här scenariot kan gästerna ange sina egna uppgifter. Registrerade användare ser sin sparade faktureringsadress i stället för butikens.

_ACP2E-4260 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/ab891304) - [GitHub-kodbidrag](https://github.com/magento/inventory/commit/13e432a6)_

#### Felaktig lagerreservation har skapats för virtuella presentkort

Före implementeringen av den här korrigeringen avspeglades inte kvantiteten på ett virtuellt presentkort som innehåller flera artiklar korrekt i lagerreservationen. När lagret tillämpades synkroniserades dock kvantiteten för lagerreservationen och lagren.

_ACP2E-4267 - [GitHub-kodbidrag](https://github.com/magento/inventory/commit/5704166a)_

#### Lagerreservationskompensationskommandot misslyckades med Null och icke-befintliga produktreferenser

Korrigerat problem när CLI för lagerreservationskompensation skulle utlösa ett undantag om den bearbetade kombinationen hade ett order-ID som saknades

_ACP2E-4301 - [GitHub-kodbidrag](https://github.com/magento/inventory/commit/76b88f7c)_

#### Produkten är inte i lager efter att SKU-ärendet har ändrats

När SKU-skiftläget ändras blir produkten inte längre lagrad i butiken.

_ACP2E-4375 - [GitHub-kodbidrag](https://github.com/magento/inventory/commit/0836c2ed)_

#### Beställ per pris-/prisfaktor med ogiltiga data

Före korrigeringen indexerades paketpriserna inte korrekt när underordnade produkter hade lager under anpassade källor. Efter korrigeringen indexeras paketpriserna korrekt oberoende av tilldelning av underordnade produkter.

_ACP2E-4380 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/1c547060) - [GitHub-kodbidrag](https://github.com/magento/inventory/commit/1f83ed24)_

### Beställning

#### AbstractAddress setData(&#39;custom_attributes&#39;, AttributeValue[]) bryter anpassade attribut

Anpassade attribut på adresser hanteras nu korrekt vid utcheckning och API-åtgärder.
Tidigare gick det att använda $address->setCustomAttributes(&#39;custom_attributes&#39;, $attributes) för att bryta den anpassade attributhanteringen, vilket gjorde att attributvärdena inte strukturerades korrekt.
AC-10568

_AC-10568 - [GitHub-problem](https://github.com/magento/magento2/issues/31644)_

#### När kunden har angetts för offertordern är den fortfarande en gästorder

_AC-11689 - [GitHub-problem](https://github.com/magento/magento2/issues/38540)_

#### Ordern är inte fullständig när virtuella, återfinansierade och levererade artiklar blandas

Ett problem har korrigerats där beställningar som innehåller virtuella, återfinansierade och levererade artiklar behandlades eftersom virtuella artiklar inkluderas i beräkning av levererad kvantitet, vilket gör att ordertillståndet kan slutföras korrekt.

_AC-11691 - [GitHub-problem](https://github.com/magento/magento2/issues/38547)_

#### v2.4.7-p1 Magento reorder -1 ordernummer

Systemet fungerar som förväntat och efter omsortering från serverdelen blir ordernumret unikt med 8 siffror

_AC-12854 - [GitHub-problem](https://github.com/magento/magento2/issues/39089) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/39399)_

#### Förlora filöverföring för anpassade produktalternativ vid utcheckning med betalningsmetoden Adobe kreditkort

Filöverföringar med anpassade produktalternativ behålls nu när du checkar ut med betalningsmetoden Adobe kreditkort.
Tidigare gick filöverföringar förlorade när den här betalningsmetoden användes, men fungerade med andra.
AC-14306

_AC-14306 - [GitHub-problem](https://github.com/magento/magento2/issues/39647)_

#### Administratörsorder - det går inte att söka efter Will

Ett problem har korrigerats där sökning efter order efter kundnamn (t.ex. &quot;Will&quot;) i rutnätet Admin Order inte gav några resultat. Efter korrigeringen visas relevanta order korrekt när de filtreras efter kundens namn.

_AC-14360 - [GitHub-problem](https://github.com/magento/magento2/issues/36596) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/a8cf637b)_

#### Magento 2.4.8 GraphQL - Order Items order_date - felaktig formatering

Ett problem har korrigerats där fältet order_date i GraphQL-svar returnerades i formatet åååå-mm-dd.
Nu visas order_date korrekt i formatet dd-mm-åååå.

_AC-14431 - [GitHub-problem](https://github.com/magento/magento2/issues/39805) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/a3b1abc2)_

#### Det går inte att returnera null för det oväntade felet \&quot;AppliedCoupon.code\&quot; som inte kan ha värdet null

Adobe Commerce returnerar nu korrekt tillämpade kupongkoder via GraphQL när man frågar efter kundorder. Tidigare kunde hämtning av en order med fältet applied_coupons.code (till exempel via frågan customer.orders) i Adobe Commerce 2.4.8 misslyckas med ett internt serverfel och meddelandet Det går inte att returnera null för fältet AppliedCoupon.code som inte kan vara null, och applied_coupons returnerades som [null] i stället för en lista som innehåller kupongkoden. AC-14484

_AC-14484 - [GitHub-problem](https://github.com/magento/magento2/issues/39841) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/97b2ea42)_

#### E-postmeddelande om leverans skickas inte när det skickas från administrationsordervyn trots att det är aktiverat i butikskonfigurationen

Systemet skickar nu ett e-postmeddelande med en leveransbekräftelse när det är aktiverat i butikskonfigurationen där beställningen placerades.

_AC-14563 - [GitHub-problem](https://github.com/magento/magento2/issues/39861) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/39897)_

#### Filtrering på datum fungerar inte på grund av tvetydiga fältnamn

I Magento 2.4.7-p6 rapporterades att filtrering av ordningens rutnät efter datum orsakade ett fel på grund av kopplingar med Braintree-moduler.
Problemet gällde frågor som kopplade till tabellerna braintree_transaction_details och sales_order när datumfilter tillämpades.
Adobe Commerce Engineering granskade ärendet men kunde inte återskapa felet i miljön.
Förväntat beteende är att filtrering efter datum ska returnera order som matchar filtret utan fel.

_AC-15037 - [GitHub-problem](https://github.com/magento/magento2/issues/40024)_

#### Orderskapande i bakgrunden med flera produkter av vilka minst en innehåller anpassade alternativ, leder till att oönskade extra produkter läggs till i ordern

Ett problem har korrigerats där en beställning skapades i bakgrunden med flera produkter, inklusive en med anpassade alternativ, som oavsiktligt har lagt till extra produkter och orsakat fel. Systemet lägger nu bara till de valda produkterna, vilket gör att order kan skapas utan oväntade artiklar.

_AC-15286 - [GitHub-problem](https://github.com/magento/magento2/issues/40122) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/b5e99d20)_

#### Magento2: Det går inte att skapa kampanjregeln

Den här PR-korrigeringen, vi får
\Magento\Catalog\Model\ResourceModel\Eav\Attribute i stället för \Magento\Catalog\Model\ResourceModel\Eav\Attribute i metoden \Magento\SalesRule\Model\Rule\Condition\Product::loadAttributeOptions

_AC-15358 - [GitHub-problem](https://github.com/magento/magento2/issues/12176) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/30479)_

#### Magento ändrade enhetstypen för $order efter anrop $invoice = $this->_invoiceService->prepareInvoice($order);

Ett problem har korrigerats där redigering av en befintlig schemalagd uppdatering för en underkategori felaktigt ökade child_count för överordnade kategorier i databasen. Problemet orsakade felaktiga kategorihierarkidata när uppdateringarna sparades. Efter korrigeringen förblir antalet underordnade objekt korrekt och ökas inte oväntat längre.

_AC-15401 - [GitHub-problem](https://github.com/magento/magento2/issues/40154)_

#### Beställningen är fortfarande i status &#39;Bearbetning&#39; efter leverans, om artiklarna delvis återbetalas

Korrigerade ett problem där beställningarna fortfarande hade status Bearbetning efter delvis återfinansiering av artiklar och sedan levererades resten. Orderstatusen uppdateras nu korrekt till Fullständigt när den totala levererade och återfinansierade kvantiteten matchar den fakturerade kvantiteten, vilket ger en korrekt hantering av orderns livscykel.

_AC-15419 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/cc0ec250)_

#### Att skicka ett e-postmeddelande från en server ger alltid framgång - även när det är inaktiverat

Korrigerade e-postmeddelandet om backend-försäljning så att korrekta meddelanden visas genom att e-posttjänstresultatet valideras, vilket säkerställer att användarna informeras när order- eller fakturameddelanden inaktiveras och inte skickas.

_AC-16059 - [GitHub-problem](https://github.com/magento/magento2/issues/40309) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/c95ed7d7)_

#### Det anpassade priset 0 återställs till det ursprungliga priset vid ombeställning.

Ett problem har korrigerats där produkter med ett anpassat pris på 0 återgick till det ursprungliga priset vid ombeställningen.
Nu behålls det anpassade priset korrekt, vilket ger rätt pris vid ändring av objektbeställning.

_AC-8147 - [GitHub-problem](https://github.com/magento/magento2/issues/36970) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/01cee3c3)_

#### Montera order med inaktiverad betalningsmetod

Korrigerade ett problem där order kunde placeras med en inaktiverad betalningsmetod via GraphQL.
Nu returneras ett fel när du försöker ange eller använda en betalningsmetod som inte är tillgänglig, vilket förhindrar att ordern skapas.

_AC-9605 - [GitHub-problem](https://github.com/magento/magento2/issues/37983) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/a8cf637b)_

#### Beställningsstatus låst vid bearbetning

Före korrigeringen växlade orderstatusen inte automatiskt till&quot;fullständig&quot; efter faktura och leverans när en paketprodukt med alternativet&quot;Leverera tillsammans&quot; aktiverades. Efter korrigeringen ändras orderstatusen automatiskt till&quot;fullständig&quot; efter att ordern har fakturerats och skickats.

_ACP2E-3947 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/2a252ae6)_

#### [Cloud]Magento OOTB-kod - Problem med konfiguration av e-postmall

Före korrigeringen, när asynkron e-postutsändning användes, var e-postutskick inkonsekvent med butiksbeställningen. Efter korrigeringen levereras rätt e-postorder för leverans i butik.

_ACP2E-3998 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/462ede94)_

#### Avbryt fakturaomdirigeringar till 404

Annullering av fakturan som gjorts med Inte hämtningstyp leder inte längre till sidan 404.

_ACP2E-4001 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/2a1e1e55)_

#### Problem med uppdaterade order med konfigurerbara alternativ med REST API

Bevara befintliga produktalternativ för försäljningsorderartiklar när en order uppdateras via betalpunkter.

_ACP2E-4061 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/6dd3fa99)_

#### Asynkron försäljning per ID-infogning begränsad till 100 poster per kron körning

Förbättrad bearbetning av asynkron infogning av säljstödraster. En cron-körning infogar nu alla väntande rader i grupper i stället för en strikt 100 per körning.

_ACP2E-4360 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/31258bf6)_

#### Felmeddelandet&quot;The product with ID &quot;1&quot; does not exist.&quot; loggas upprepade gånger in i exception.log

Före korrigeringen loggades kritiska fel när borttagna produkter påträffades i avsnittet Senast beställda artiklar. Efter korrigeringen kan handlare konfigurera om de vill logga eller hoppa över borttagna produkter via parametern `skipDeletedProductLogging` i di.xml. Som standard förblir beteendet oförändrat för bakåtkompatibilitet, men handlare kan ställa in parametern på `true` för att tyst hoppa över borttagna produkter och förhindra loggbrus.

_ACP2E-4366 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/61c96348)_

#### Dubbel skatt på andra återbetalning av kreditnota

Korrigerade felaktig momsberäkning i kreditnotor när en partiell återbetalning skapades från en faktura efter att en tidigare kreditnota skapades från ordervysidan.

_ACP2E-4384 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/61c96348)_

### Order, pris

#### Administratören visar felaktig valutasymbol när retur skapas

I en flerwebbplatskonfiguration med olika valutor (EUR/USD/GBP) visas nu rätt valutasymbol på sidan för val av returprodukt i admin. Tidigare visades standardvalutasymbolen.

_ACP2E-3658 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/df92debe)_

### Order, returer

#### Fel när kreditnota skapades för offlineåterbetalning

Ett problem har korrigerats där det inte gick att skapa en kreditnota för paketprodukter med inställningen Dynamiskt pris = Nej. Kreditnotor kan nu skapas utan fel.

_ACP2E-4157 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/45cbf9b6)_

### Andra utvecklingsverktyg

#### [Fel typtips] för den skyddade medlemmen $_urlHelper

Systemet åtgärdar nu fel typtips med rätt typ, som också används i konstruktorn

_AC-10716 - [GitHub-problem](https://github.com/magento/magento2/issues/32503) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/32496)_

#### [Problem] Rensa oanvänd kod.

Systemet tar nu bort oanvänd kod för oanvända importer.

_AC-10980 - [GitHub-problem](https://github.com/magento/magento2/issues/38424) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/33499)_

#### Fel i hjälpmedel för Lightroom

Nu skickas System med tillgänglighetspoängen 100

_AC-12783 - [GitHub-problem](https://github.com/magento/magento2/issues/39054) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/39164)_

#### Inaktivera Captcha storefont config fortfarande läsa in captcha js-filer

Systemet läser nu inte in captcha js-filer när vi har inaktiverat captcha
för storefont

_AC-14267 - [GitHub-problem](https://github.com/magento/magento2/issues/32987) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/39154)_

#### [Problem] Tillgänglighet: WAI-ARIA-roller som är felaktiga på menyn

Systemet genererar nu fyr-hjälpmedel utan WAI-ARIA-roller som är felaktiga i menyfel och rapporten ska vara grön

_AC-15082 - [GitHub-problem](https://github.com/magento/magento2/issues/40045) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/38617)_

#### Konsolfel i förhandsgranskning av e-post i Magento-administratören

Systemet genererar inga konsolfel när vi förhandsgranskar e-postmallen

_AC-9245 - [GitHub-problem](https://github.com/magento/magento2/issues/37820) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/37933)_

### Betalnings-/betalningsmetoder

#### Paylater-meddelande visas inte i butiken när konfigurationen i backend konfigureras

Ett problem har korrigerats där PayPal PayLater-meddelandet inte visades på Home- och Cart-sidorna trots att det konfigurerades i backend-objektet. Banderollen kunde inte återges när köplandet var null för gäster eller kunder utan standardadress. Efter korrigeringen visas meddelandet Betala senare korrekt i butiken.

_AC-12335 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/528af81a)_

### Betalningar

#### [Problem] Åtgärda offlinefakturainhämtning (404)

Det åtgärdar 404-sidesfelet när fakturor hämtas för offlinebetalningsmetoder från Magento-administratören

_AC-13336 - [GitHub-problem](https://github.com/magento/magento2/issues/39298) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/39297)_

#### Okända IPN:er från PayPal missbrukar programmets IPN-processor

IPN-hanteraren ignorerar nu IPN-typer som inte stöds eller är okända. I stället för att returnera 500 fel loggas problemet och bearbetningen fortsätter utan avbrott.

_ACP2E-4049 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/6dd3fa99)_

#### PayflowPro sparad korttoken misslyckades vid betalning

PayPal PayFlow Pro-transaktions-ID:n (PNREF) kan nu användas i referenstransaktioner under en fast period på 12 månader. När kortet har gått ut visas det inte längre och måste läggas till igen. Tidigare fastställdes giltigheten av utgångsdatumet för det betalkort som användes i den ursprungliga transaktionen.

_ACP2E-4064 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/52f46328)_

#### Vaulerat kortproblem vid beställning från administratör

Att lägga en order med ett lagrat kreditkort på en webbplats med en annan konfiguration för betalningsåtgärd ger inte längre upphov till fel eller fel transaktionstyp

_ACP2E-4270 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/0a8c9a9a)_

#### [Molnet] PayflowPro-sparat kort (Vault), sista 4-siffran visas inte i ordningen

Kortinformationen bevaras nu korrekt och visas när du använder sparade kort med säljbetalningsåtgärden, vilket matchar beteendet när auktoriseringsbetalningsåtgärden används för PayflowPro.

_ACP2E-4346 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/0a3b7032)_

### Prestanda

#### [Utgåva] Uppdatera Store.php

Denna PR förbättrar prestanda genom att hoppa över den aktuella lagringsupplösningen.

_AC-14791 - [GitHub-problem](https://github.com/magento/magento2/issues/39949) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/38717)_

#### [Problem] Uppdatera använd cachekontroll som inte kan ändras för statisk plats

Den här PR-funktionen lägger till prestandaförbättringar genom att inte validera det statiska innehållet på varje sidinläsning förrän &amp; såvida det inte har ändrats.

_AC-15171 - [GitHub-problem](https://github.com/magento/magento2/issues/39486) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/39484)_

#### [Utgåva] cachelagra resultatet av isCacheable-anrop för att förbättra prestandan

Denna PR lägger till cachelagring för metoden isCacheable() vilket resulterar i layoutåtergivningsprocessen, vilket minskar antalet redundanta kontroller och förbättrar den övergripande sidåtergivningsprestandan.

_AC-16054 - [GitHub-problem](https://github.com/magento/magento2/issues/40156) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/40112)_

#### [Problem] Mindre prestandaförbättringar av asynkron bearbetning av orderstödraster

Denna PR introducerar en prestandaoptimering för Magento asynkrona sorteringsrutnätsbearbetning genom att ersätta den tillfälliga cachebaserade last_updated_at-sökningen med en beständig DB-understödd flagga som lagras i flaggtabellen. Detta garanterar att systemet konsekvent behåller den senast bearbetade tidsstämpeln även efter att cacheminnet tömts eller distribuerats, vilket förhindrar att stora data för sales_order läses in i onödan. Detta resulterar i att asynkrona rutnätsuppdateringar blir mer effektiva och förutsägbara, särskilt i storvolyminspelningar med frekvent orderaktivitet.

_AC-16109 - [GitHub-problem](https://github.com/magento/magento2/issues/40282) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/40271)_

#### [CLOUD] Det går inte att lägga till produkter i kategorier

Förbättrade prestanda när du lägger till produkter i en kategori via Visual Merchandiser.

_ACP2E-3946 - [GitHub-kodbidrag](https://github.com/magento/inventory/commit/29653b1d)_

#### Prestandaproblem vid rensning av ändringsloggar efter ACP2E-3995

Efter korrigeringen rensar cron-jobbet indexer_clean_all_changelgos helt och hållet ändringshundar och behåller på plats.

_ACP2E-4211 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/ee918f0d)_

#### [CLOUD] Snabbcachen fungerar inte när vi har uppgraderat till 2.4.8

Ett problem där cachelagrade sidor inte lagrades på rätt sätt eller hanterades från snabbcachen har åtgärdats, vilket resulterade i inkonsekvent cachelagring och minskad prestanda.

_ACP2E-4324 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/2687b487)_

#### Undersök orsakerna till att fler redis-nycklar och cachenycklar har skapats

Före korrigeringen gick cacheminnesnycklar som används för fjärrlagringsmetadata inte ut. Efter korrigeringen kan du nu ange en TTL för sådana cachenycklar genom beroendeinjektion.

_ACP2E-4345 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/0a3b7032)_

### Priser

#### Priset är alltid 0 för produktartiklar utan dynamiskt pris i order rest-API

Order REST API returnerar nu korrekta priser för produktartiklar utan dynamiskt pris.
Tidigare returnerades alltid priset för produktartiklar utan dynamisk prissättning som 0 när order exporterades via REST API, i stället för det faktiska pris som visades på paketsidan.
AC-11925

_AC-11925 - [GitHub-problem](https://github.com/magento/magento2/issues/38687) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/7da46f52)_

#### Felaktigt omfång tilldelat till prisattribut vid skapande

Ett problem har korrigerats där nyligen skapade prisattribut felaktigt tilldelades Store View-omfånget oavsett konfiguration. Efter korrigeringen justeras attributomfånget nu som standard med Catalog Price Scope-inställningen (Global eller Website).

_AC-14945 - [GitHub-problem](https://github.com/magento/magento2/issues/39986) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/8670a2b4)_

#### Produkten sparas även när specialpriset är från datum är senare än Till datum med massåtgärd

Ett problem har korrigerats där produkter kunde sparas med ett ogiltigt datumintervall för specialpris utan validering.
Nu visas ett felmeddelande:&quot;Kontrollera att Till-datumet är senare än eller samma som Från-datumet.&quot;

_AC-15252 - [GitHub-problem](https://github.com/magento/magento2/issues/40113) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/36d4d6fb)_

#### Normalpriset syns inte, även om ett specialpris används.

Löste ett problem där normalpriset inte visades när ett specialpris tillämpades. Normalpriset visas nu korrekt tillsammans med specialpriset som förväntat.

_ACP2E-4100 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/47721be6)_

### Produkt

#### Konfigurerbar produkt med dåligt beteende i början

Ett problem har korrigerats där konfigurerbara produkter visade ett felaktigt frontmönster när ett färgprovsattribut inkluderades, vilket medförde att priser, listrutelayout och obligatoriska fältindikatorer inte visades korrekt.
Nu återges konfigurerbara produkter korrekt med rätt pris, anpassade listrutor och förväntat användargränssnitt.

_AC-1014 - [GitHub-problem](https://github.com/magento/magento2/issues/14296) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/ef666cd9)_

#### Strängen för prisförsäkran matchar inte när den konfigurerbara produkten har tilldelats till webbplatsen Test Stock och Test med alternativet att visa produkter som inte finns i lager aktiverat

Det test som misslyckades uppdaterades för att anpassa till det faktiska prisbeteendet för konfigurerbara produkter när alla underordnade produkter har samma pris.
Påståendet validerar nu korrekt det visade priset, vilket förhindrar felaktiga testfel utan att påverka funktionen.

_AC-10843 - [GitHub-kodbidrag](https://github.com/magento/inventory/commit/1ccc786b)_

#### Etiketten&quot;Så lite som&quot; visas fortfarande för en konfigurerbar produkt för testfallet AC-6158

Implementerade och verifierade konfigurerbara produkter (P1-P7) med respektive variationer och kategoritilldelningar. Korrekt butiksprisvisning och etikettbeteende för&quot;Så lågt som&quot; för produkter i kategori C säkerställs.

_AC-10847 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/a3b1abc2)_

#### Procentrabatt på skiktpris och katalogprisregel som beräknas på det ursprungliga priset utan valda alternativ.

Procentrabatter på skiktpris- och katalogprisregler inkluderar nu valda anpassade alternativ.
Tidigare beräknades de procentuella rabatterna på det ursprungliga produktpriset utan att man tog hänsyn till vissa anpassade alternativ, vilket resulterade i felaktiga slutpriser.
AC-12004

_AC-12004 - [GitHub-problem](https://github.com/magento/magento2/issues/38750)_

#### [Issue] validate-rating fungerar inte, väljaren för recensioner har ändrats

Ett problem har korrigerats där granskningsgraderingen inte aktiverades på grund av en ändrad väljare. Tidigare gick det att spara granskningar utan att välja någon klassificering. Efter korrigeringen fungerar valideringen korrekt och förhindrar att en granskning sparas om inte en klassificering har valts.

_AC-12686 - [GitHub-problem](https://github.com/magento/magento2/issues/33424) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/528af81a)_

#### Magento 2.4.7 minTillåten saknad produktorderkvantitet

Systemet fungerar som det ska och sidans källa visar produktens minsta kvantitet korrekt

_AC-12909 - [GitHub-problem](https://github.com/magento/magento2/issues/39142) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/39480)_

#### Produktsamling - addMediaGalleryData anropar getSize när samlingen läses in (Kan använda count för att undvika en extra DB-fråga)

Denna PR reducerar det extra frågeanropet med count() om produktsamlingen redan har lästs in när Product Graphql anropas med fältet media_gallery.

_AC-13055 - [GitHub-problem](https://github.com/magento/magento2/issues/39111) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/39681)_

#### Ogiltig SKU-hantering för länkade produkter i Magento

Korrigerade ett problem där produkter med SKU &quot;0&quot; inte kunde länkas som relaterade artiklar, merförsäljning eller korsförsäljning på grund av ogiltig SKU-validering. Uppdateringen säkerställer att sådana produkter kan länkas utan fel, vilket gör att produkten kan sparas utan fel.

_AC-13311 - [GitHub-problem](https://github.com/magento/magento2/issues/39329) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/a8cf637b)_

#### Problem med stödrastret för anpassningsbara alternativ på produktsidan på administratörspanelen

Systemet fungerar som väntat när vi skapar anpassningsbara alternativ med listrutan Typ

_AC-14003 - [GitHub-problem](https://github.com/magento/magento2/issues/39640) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/39694)_

#### Fel på administratörens produktsida när alla produktattribut är inställda på globalt omfång

Korrigerade ett problem där redigeringssidan för administratörsprodukten visade ett fel när alla produktattribut var inställda på globalt omfång. Felet orsakades av en tom databasfråga, vilket gör sidan oanvändbar. Efter korrigeringen återges produktsidan korrekt och produkterna kan skapas utan problem.

_AC-14011 - [GitHub-problem](https://github.com/magento/magento2/issues/39646)_

#### [2.4.8] Inga återanrop hittades för cron job catalog_product_alert

Adobe Commerce förhindrar nu att felaktiga cron-jobb av typen catalog_product_alert schemaläggs efter att produktvarningsjobbet har bytt namn till product_alert. Om du konfigurerade Lager > Konfiguration > Katalog > Katalog > Katalog > Produktaviseringar för körning av inställningar i Adobe Commerce 2.4.8 skapades en cron-post för catalog_product_alert i core_config_data och när cron kördes loggades felet Magento_Cron.CRITICAL: Undantag: Inga återanrop hittades för cron job catalog_product_alert trots att de giltiga product_alert-jobben kördes korrekt.

_AC-14494 - [GitHub-problem](https://github.com/magento/magento2/issues/39800) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/1bc2d6d0)_

#### [Produktjämförelse] Jämför lista kommer inte att kunna användas

Ett problem har korrigerats där jämförelselistan blev oanvändbar när samma produkt lades till från olika butiksvyer. Efter korrigeringen läses jämförelselistan in korrekt och objekt visas baserat på den specifika butiken.

_AC-14885 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/8670a2b4)_

#### Extra loggning vid begäran av en produkt via databas misslyckas

Förbättrade felmeddelanden för ProductRepository::get och getById när det inte går att hitta en SKU eller ett ID.
Tidigare fanns det ingen kontext för vilka SKU eller ID som orsakade felet.
Undantagsmeddelandet innehåller den saknade SKU:n eller ID:t, vilket underlättar felsökning och förbättrar utvecklingsmiljön.
Den här ändringen påverkar inte något funktionellt beteende för API:t.

_AC-15199 - [GitHub-problem](https://github.com/magento/magento2/issues/40090) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/1b1baf1d)_

#### Attributuppsättningen Det finns inget fel som bryter sidan

Korrigerade ett problem där ett ogiltigt attributuppsättnings-ID i URL:en orsakade ett allvarligt fel. Systemet visar nu ett felmeddelande om att attributuppsättningen inte finns i stället för att sidan bryts.

_AC-15753 - [GitHub-problem](https://github.com/magento/magento2/issues/40213) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/a06a4a57)_

#### Återbetalning med negativ kvantitet som alltid återbetalas

Ett problem har korrigerats där en kreditnota med en negativ kvantitet felaktigt återbetalade rabattbeloppet.
Rabatterna återbetalas inte för negativa kvantiteter och bidragsbeloppet är korrekt inställt på noll.

_AC-9424 - [GitHub-problem](https://github.com/magento/magento2/issues/37917) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/ef666cd9)_

#### Långsam fråga körs när produktwidgeten inkluderas via pagebuilder

Frågan för att skapa produktwidgetar, inklusive produkt-SKU:er, är optimerad.

_ACP2E-3449 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/df92debe)_

#### Produktbilder som inte ändrar storlek när de läggs till som en konfigurerbar produkt

Tidigare var de bilder som lades till via konfigurationer på adminpanelen inte lika med den maximala överföringsstorleksgränsen, vilket kunde leda till inkonsekvenser och hanteringsproblem. Nu har en korrigering implementerats för att säkerställa att storleken på bilderna automatiskt ändras under överföringen så att de uppfyller den maximala storleksgränsen, vilket effektiviserar processen och bevarar systemstandarderna.

_ACP2E-3504 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/df92debe)_

#### Alla objekt från andra kunders jämförelselistor tilldelas kunden efter inloggning via administratören

Tidigare, när en administratör använde funktionen&quot;Logga in som kund&quot; i serverdelen, hade produkter från jämförelselistan för en tidigare inloggad kund felaktigt tilldelats den just nu personifierade kunden.  Efter korrigeringen läses jämförelselistan in korrekt för rätt inloggade kund.

_ACP2E-3818 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/462ede94)_

#### [B2B] Spara delad katalog returnerar inaktuella funktionsfel

Administratören kan ta bort tilldelning av produkter från den delade katalogen.
Om du tidigare avtilldelade produkter med ett stort antal långa produkt-SKU:er från den delade katalogen uppstod ett fel

_ACP2E-4097 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/ab891304)_

#### [Prestanda för generering av webbplatskartor i molnet] har försämrats avsevärt

Framtagning av webbplatskartor för produkter med bilder upplever inte längre exponentiell avmattning. Tidigare skulle generering av platskartor för butiker med aktiverad bildinkludering ge långa bearbetningstider.

_ACP2E-4153 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/e457c5e2)_

### Produkt, skatt

#### FPT (Fixed Product Tax) visas inte separat med konfigurerbara produkter

Ett problem har korrigerats där FPT (Fixed Product Tax) inte visades separat för konfigurerbara produkter efter att ett alternativ har valts. Nu visas FPT-uppdelningen korrekt på produktlistnings- och detaljsidor, vilket matchar visningsformatet för enkla produkter.

_AC-13171 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/b5e99d20)_

### Kampanj

#### Köp X Hämta Y-kundvagnsprisregeln lägger till fel rabatt när en annan regel redan har tillämpats

Korrigerade ett problem där prisregeln Köp X Hämta Y-kundvagn beräknade rabatter med det ursprungliga produktpriset även efter att en annan regel redan hade reducerat det. Uppdateringen säkerställer att den andra regeln nu tillämpar rabatten på det justerade priset, vilket ger korrekta totalrabatter när flera kampanjer är aktiva.

_AC-12325 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/8670a2b4)_

#### Det gick inte att hämta rabatt för orderartikel tillämpad_på för kundorder via GraphQl-kundförfrågan

Tidigare när rabatter som tillämpats_på för kundorder via GraphQl kundbegäran observerades ett internt serverfel som nu är fast och korrekta kundorderdata med rabatt hämtas

_AC-14888 - [GitHub-problem](https://github.com/magento/magento2/issues/39963) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/fe72c407)_

#### Det gick inte att hämta orderartikelkupongkod för kundorder via GraphQl-kundförfrågan

Ett problem där hämtning av order med kuponginformation via GraphQL returnerade ett internt serverfel har åtgärdats.
Frågan körs nu och returnerar rätt kuponginformation i svaret.

_AC-14889 - [GitHub-problem](https://github.com/magento/magento2/issues/39962) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/fe72c407)_

#### `[Cloud][experienceleague]`-katalogprisregeln används inte

Innan reglerna för korrigeringspriset för kataloger inte tillämpades när `special_price` bara angavs på webbplatsnivå (inte vid Alla butiksvyer). Efter att prisreglerna för korrigeringskatalogen nu har tillämpats korrekt när `special_price` har angetts på webbplatsnivå genom att kontrollera webbplatsens standardbutik först.

_ACP2E-4372 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/61c96348)_

### SEO

#### DynamicStorage.findProductRewriteByRequestPath() saknar Entity_type-filtrering, vilket gör att CMS-sidor behandlas som produkter i kategori-URL:er

Korrigerade ett problem där DynamicStorage inte filtrerade efter entity_type, vilket gjorde att CMS-sidor inte behandlades korrekt som produkter i kategori-URL:er. Felformaterade URL:er returnerar nu korrekt 404 i stället för att visa CMS-innehåll.

_AC-14991 - [GitHub-problem](https://github.com/magento/magento2/issues/39996) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/64823f95)_

#### Aktivera kategorisökväg i produkt-URL-brytningar för butiksväljare på flera sätt

Ett problem har korrigerats där aktiveringen av kategorisökvägar i produkt-URL:er gjorde att butiksväljaren misslyckades. Lagringsväxlingen löser nu korrekt produkt-URL:er i butiksvyer utan att omdirigera till hemsidan eller returnera fel.

_AC-15110 - [GitHub-problem](https://github.com/magento/magento2/issues/40037) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/a7ef6300)_

#### Odefinierad matrisnyckel i ProductRepository getById

Problemet uppstod när ProductRepository::getById() anropades med ett ogiltigt ID som 123abc, vilket ledde till ett&quot;undefined array key&quot;-fel.
Efter korrigeringen i Magento 2.4.9-alpha3 returnerar sådana begäranden nu korrekt en 404-sida i stället för att generera ett undantag.
Kvalitetsbedömningen har bekräftats med både giltiga och felformaterade ID:n och inga ytterligare problem har observerats.

_AC-15345 - [GitHub-problem](https://github.com/magento/magento2/issues/40146) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/68a45d0a)_

#### Jämförelseprodukten i Storefront skapar ett Google SEO-fel - länkarna kan inte crawlas

Ett SEO-problem har korrigerats där butikslänken&quot;Jämför produkter&quot; inte kunde crawlas av sökmotorer på grund av att href-attributet saknas eller är felaktigt bundet. Uppdateringen ser till att länken nu innehåller en giltig, crawlbar URL-adress som gör det enklare att identifiera webbplatsen och som gör att Google SEO-granskningar kan utföras.

_AC-15547 - [GitHub-problem](https://github.com/magento/magento2/issues/40185) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/c95ed7d7)_

#### Uppdatera product url_key via REST API genererar inte en 301 URL-omskrivning

När du uppdaterar URL-nyckeln för produkten via REST API, med inställningen&quot;Skapa permanent omdirigering för URL:er om URL-nyckeln har ändrats&quot; inställd på Ja, skapas en omdirigering från en gammal URL till en ny.

_ACP2E-3900 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/462ede94)_

#### [Genereringen av webbplatskartor i molnet] upphör aldrig

Före korrigeringen kunde platskartan inte skapas korrekt om katalogen innehöll mer än en miljon produkter. Efter korrigeringen kommer webbplatskartan att genereras med mindre minnesallokering och med så många som en miljon produkter per butik.

_ACP2E-3902 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/52f46328)_

#### [Cloud] Store-växlaren fungerar inte från EN till FR för sidan med vanliga frågor

Ett problem har korrigerats där växling mellan butiksvyer omdirigerade användare till hemsidan i stället för till motsvarande översatta CMS-sida. Butiksväljaren söker nu efter URL-omskrivningar i målbutiken för att säkerställa korrekt omdirigering (t.ex. sidan med vanliga frågor och svar på engelska → sidan med vanliga frågor på franska).

_ACP2E-4112 - [GitHub-problem](https://adobe-ent.crm.dynamics.com/main.aspx?appid=f2e74f34-7119-ea11-a811-000d3a5936c5&forceUCI=1&pagetype=entityrecord&etn=incident&id=3e1df344-8a69-f011-bec3-6045bd04f475)_

#### [Cloud] Inaktivera den gamla genereringen av webbplatskartan

Det finns nu ett nytt konfigurationsalternativ för att växla mellan standardprocessen för att skapa platskartor och ett nyligen implementerat batchläge. Den här förbättringen ger större flexibilitet och skalbarhet i arbetsflöden för att skapa webbplatskartor.

_ACP2E-4132 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/45cbf9b6)_

#### Misstänkta begäranden genererar undantag i exception.log

Korrigerade ett problem där skadliga eller felformaterade URL-begäranden orsakade fel i databaskollationeringen och fyllde i undantagsloggar.
Tidigare gjordes försök att avkoda och bearbeta misstänkta begäranden som innehöll ogiltiga teckenkodningar eller tecken som inte stöds, vilket ledde till konflikter för MySQL-sorteringen.

_ACP2E-4328 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/2687b487)_

### Försäljning

#### När ett presentationsmeddelande är aktiverat på ordernivå men användaren inte anger några data och lägger till en order, visar fortfarande Från namn och Till namn i administratören kundens för- och efternamn.

Ett problem har korrigerats där fält för avsändare och mottagare av presentmeddelanden fylldes i automatiskt med kundnamn även när inget presentationsmeddelande angavs. Fälten är nu tomma såvida inte användaren anger informationen.

_AC-15140 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/a8cf637b)_

### Sök

#### &quot;Bekräfta formuläråterskickning&quot; vid katalogsökning med &quot;Kom ihåg kategorisidindelning&quot;

Om du går tillbaka från en produktsida till sidan Katalogsökresultat efter att ha ändrat verktygsfältsinställningarna aktiveras inte längre dialogrutan Bekräfta formuläråterskickning när alternativet Kom ihåg kategorisidindelning är aktiverat.
Tidigare påträffades ett webbläsarfel eller en varning om att formuläret skulle skickas igen när användaren återgår till sökresultatsidan efter att ha ändrat verktygsfältsparametrar som sorteringsordning.

_ACP2E-4208 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/e885088b)_

#### Det aggregerade sökfältet &quot;_search&quot; används inte längre i sökfrågan

Nu returnerar fulltextsökning matchande produkter om minimikravet för att matcha villkoret uppfylls i alla sökbara fält tillsammans, i stället för att villkoret måste uppfyllas i ett enskilt fält.

_ACP2E-4285 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/cbca0396)_

### Säkerhet

#### Internt serverfel

Magento har nu lagt till produkter i kundvagnen när den asynkrona REST-slutpunkten POST /rest/default/async/V1/carts/mine/items används. Tidigare resulterade den här asynkrona&quot;add to cart&quot;-begäran i ett internt serverfel, och Magento loggade följande fel: Fel: Anrop till en medlemsfunktion setFinalPrice() på null i app/code/Magento/Quote/Model/Quote/Item/AbstractItem.php:162.

_AC-16344 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/8670a2b4)_

#### Paketerad/sammanfogad JS ingår inte i SRI-hash

Före korrigeringen av det skapade paketet eller de sammanfogade filerna lades inte till i listan över SRI-hashar. Nu läggs filerna till korrekt i SRI-hashen.

_ACP2E-3854 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/4ca73607)_

#### [CLOUD] har ett skrivbart behörighetsproblem i det nya uttrycket

Före korrigeringen var loggarna utlästa med undantag. När korrigeringen har tillämpats är loggarna nu rena och fria från undantag.

_ACP2E-4296 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/61c96348)_

### Leverans

#### Felaktig leveranskvantitet efter få kreditnotor

Ett problem har korrigerats där värdet för Kvantitet att leverera felaktigt beräknades efter flera kreditnotor, vilket tillåter leverans av återfinansierade artiklar.
Nu uppdaterar systemet korrekt den resterande leveranskvantiteten baserat på levererade och återfinansierade artiklar, vilket förhindrar ogiltiga leveranser.

_AC-1479 - [GitHub-problem](https://github.com/magento/magento2/issues/34289) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/913bf1a6)_

#### Potentiellt prestandaproblem vid inläsning av leveransmetoder

Optimerade inläsningsprocessen för leveransmetoder genom att säkerställa att endast aktiva transportföretag läses in vid begäran. Tidigare initierades fabriker för alla leveransmetoder, vilket orsakade onödig prestandaförlust. Korrigeringen förbättrar effektiviteten genom att endast aktiva transportföretag läses in, vilket minskar belastningstiden och resursanvändningen.

_AC-15415 - [GitHub-problem](https://github.com/magento/magento2/issues/40153) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/cc0ec250)_

#### [Utgåva] Affärsmål ska inte behandlas som bostadsadress

Korrigerade ett problem i leveransintegreringen för UPS REST där kommersiella destinationer felaktigt behandlades som bostäder. Uppgiften om bostadsortAddressIndicator ingår nu endast i UPS-tariffbegäran för bostadsadresser, vilket förhindrar oavsiktliga extra avgifter för bostäder och säkerställer korrekta kommersiella fraktpriser.

_AC-16285 - [GitHub-problem](https://github.com/magento/magento2/issues/40314) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/40307)_

#### Ett undantag uppstod när UPS-etiketten skapades

Fast varning: Konvertering från matris till sträng när UPS-etiketten skapas

_ACP2E-3676 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/b12ffe36)_

#### [QUANS] - Söker Magento_Fedex kärnmodul efter en giltig token innan du skickar en begäran om en ny?

Adobe Commerce gör inte längre många förfrågningar till FedEx API-tjänsten för åtkomsttoken. Tidigare gjorde Adobe Commerce alltid nya förfrågningar till FedEx API trots att åtkomsttoken fortfarande är giltig, vilket orsakade ett hastighetsbegränsande problem.

_ACP2E-3930 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/4ca73607)_

### Mellanlagring och förhandsvisning

#### Priset på produkten i kundvagnen som påverkas av katalogprisregeln ändras inte när regeln justeras av mellanlagringsuppdateringen

Ett problem har korrigerats där produktpriserna i kundvagnen inte uppdaterades fullständigt efter att en katalogprisregel ändrades via en mellanlagringsuppdatering. Tidigare visades det uppdaterade priset endast i sammanfattningsavsnittet medan kundvagnsblocket visade det gamla värdet. Nu uppdaterar den ändrade regeln produktpriset korrekt i hela kundvagnen.

_AC-15304 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/913bf1a6)_

#### När den schemalagda uppdateringen för kategorin tas bort, minskas inte antalet underordnade för den överordnade kategorin

Ett problem har korrigerats där borttagningen av en schemalagd uppdatering för en kategori inte minskade antalet underordnade för den överordnade kategorin. Antalet uppdateras korrekt när schemalagda uppdateringar eller underkategorier tas bort.

_AC-15670 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/ef666cd9)_

#### När schemalagd uppdatering för kategorier redigeras läggs underordnade belopp till i den överordnade kategorin

Ett problem har korrigerats där redigering av en befintlig schemalagd uppdatering för en underkategori felaktigt ökade child_count för överordnade kategorier i databasen. Problemet orsakade felaktiga kategorihierarkidata när uppdateringarna sparades. Efter korrigeringen förblir antalet underordnade objekt korrekt och ökas inte oväntat längre.

_AC-16239 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/8670a2b4)_

#### Om du förhandsgranskar en schemalagd uppdatering öppnas den första butiksvyn i alfabetisk ordning i stället för butiksvyn

Före korrigeringen öppnas förhandsgranskningen av en schemalagd uppdatering i den första butiksvyn i alfabetisk ordning i stället för i den tilldelade butiksvyn.
Efter korrigeringen öppnas nu förhandsgranskningen korrekt i butiksvyn som tilldelats till CMS-blockstagguppdateringen.

_ACP2E-3671 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/b12ffe36)_

#### Det går inte att förhandsgranska den schemalagda produktuppdateringen med kategoribehörigheter aktiverade

Före korrigeringen visades inte en framtida produkt som skulle aktiveras i förhandsgranskningsläget. Nu visas den även om den aktuella statusen är inaktiverad.

_ACP2E-3786 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/7accebfa)_

#### Validering saknas för rabattbeloppsfältet för katalogprisregel

Tidigare validerades fältet rabatt_amount i uppdateringen av mellanlagringsschemat inte korrekt med de aktuella valideringsreglerna. När du har tillämpat korrigeringen valideras dock fältet rabatt_amount korrekt.

_ACP2E-3867 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/462ede94)_

#### Paket med schemalagda uppdateringar tar bort alternativet för att spara paket vid produktsparande

Om du tar bort produktalternativ eller associerade produkter i en schemalagd uppdatering påverkas inte längre de ursprungliga paketalternativen och tillhörande produkter, och vice versa. Om du tar bort alternativen för paketproduktion i den ursprungliga produkten och ersätter dem med andra alternativ efter att du har schemalagt en uppdatering tas de nya alternativen inte längre bort

_ACP2E-4212 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/ab891304)_

#### Det går inte att navigera mellan webbplatser i förhandsversionen av schemauppdateringen

Före den här korrigeringen bryts förhandsgranskningen av den schemalagda uppdateringen när innehåll för butiker med anpassade domäner förhandsgranskas. Efter den här korrigeringen kan anpassade butiksdomäner förhandsgranskas som de är och navigeras i förhandsvisningsbildrutan. Korrigeringen omfattar produkter, kategorier, CMS-sidor och CMS-block, och stöder navigeringslänkar med `{{store url}}`-taggar enligt [Adobe Commerce Variables and Markup Tags ](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/variables/markup-tags).

_ACP2E-4308 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/0a3b7032)_

### Moms

#### Fel ordersumma, avrundningen används inte i prisberäkningen.

Systemet hanteras nu korrekt vid beräkning av pris_after_rabatt, rabatt_amount och moms.
orderns faktiska totalbelopp

_AC-11389 - [GitHub-problem](https://github.com/magento/magento2/issues/38455) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/39687)_

#### [Utgåva] Korrigera: Värdet för kreditnotobjekten base_weee_tax_applied_row_amnt är felaktigt

Beräkningen av kreditnotan har korrigerats genom att rätt set för base_weee_tax_applied_row_amnt användes, vilket säkerställer att momsvärdet endast återspeglar den återfinansierade kvantiteten. Tidigare använde radbeloppet felaktigt det fullständiga ordervärdet i stället för det partiella kreditkortsbeloppet.

_AC-12049 - [GitHub-problem](https://github.com/magento/magento2/issues/38765) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/3b5ac075)_

#### Artiklar i minivagnen visar priser i utländsk valuta utan konvertering

Mini-cart konverterar nu korrekt valuta och visar korrekt belopp baserat på konfigurerade konverteringsgrader.

_ACP2E-4364 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/1c547060)_

### Testramverk

#### [Problem] Ta bort en duplicerad &lt;allvarlighetsgrad>-tagg från MFTF-testet AdminSetUpWatermarkForSwatchImageTest

Systemet innehåller nu bara en enda tagg för allvarlighetsgrad i AdminSetUpWatermarkForSwatchImageTest, vilket förbättrar tydligheten och enhetligheten i koden. Tidigare innehöll testet två identiska taggar för allvarlighetsgrad, vilket var onödigt och kunde leda till förvirring.

_AC-11873 - [GitHub-problem](https://github.com/magento/magento2/issues/38504) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/31862)_

#### [Problem] Ignorera lib/internal/Magento/Framework/App/Test/Unit/_files/app/etc/en..

Systemet ignorerar nu filen &#39;env.php&#39; som genereras när enhetstester körs, vilket säkerställer att Git-statusen förblir ren när testerna körs. Tidigare genererade enhetstester en ny fil, env.php, vilket fick Git-statusen att visa en ny fil som hittades och som fick den att se smutsig ut.

_AC-13293 - [GitHub-problem](https://github.com/magento/magento2/issues/39304) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/37631)_

#### [Problem] Åtgärda integreringstest med spärr

Systemet identifierar och hanterar nu \Magento\TestFramework\App\Config\Interceptor korrekt i integreringstestet, vilket säkerställer att testet kan komma åt nödvändiga data även när det finns ett plugin-program för klassen. Tidigare kunde systemet inte ta hänsyn till att \Magento\TestFramework\App\Config kan vara \Magento\TestFramework\App\Config\Interceptor, vilket resulterade i ett fel vid försök att komma åt egenskapen $data.

_AC-13305 - [GitHub-problem](https://github.com/magento/magento2/issues/39324) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/37187)_

#### [Utgåva] MFTF: Skickar e-post till vänformulär med aktiverad captcha

Testfallet åtgärdar funktionaliteten i formuläret&quot;E-post till vän&quot; när CAPTCHA är aktiverat, vilket säkerställer att inskickningsprocessen fungerar korrekt med både felaktiga och korrekta CAPTCHA-värden.

_AC-13492 - [GitHub-problem](https://github.com/magento/magento2/issues/39462) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/32830)_

#### Hårdkodade korrigeringsbanor misslyckades i Composer-byggen

_AC-16488_

#### [Utgåva] magento/magento2#: GraphQl-mutation. Ytterligare testdisponering för kundens storeConfig-inställningar.

Systemet lägger nu till ytterligare testtäckning för nästa kundbutikConfig-alternativ:
required_character_classes_number
minimum_password_length

_AC-9370 - [GitHub-problem](https://github.com/magento/magento2/issues/37915) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/28761)_

#### Miljöspecifika enhetstestfel i AC 2.4.7-p3

Det här problemet åtgärdar enhetstestfel som inte återskapas i alla versioner och miljöer. Tidigare gick det inte att åtgärda vissa enhetstester på grund av olika biblioteksversioner eller på grund av att funktioner som lagts till i en senare version saknas.

_ACP2E-3712 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/9ad7d277)_

### UI Framework

#### [Problem] Ta bort duplicerade variabler från en av färre filer

Systemet tar nu bort duplicerade variabler från färre filer, vilket ger renare och effektivare kod. Tidigare fanns dessa duplicerade variabler i färre filer, vilket ledde till onödig redundans i koden.

_AC-11743 - [GitHub-problem](https://github.com/magento/magento2/issues/31154) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/31150)_

#### WYSIWYG är tomt i dynamiska rader

WYSIWYG-fält i dynamiska rader är nu korrekt initierade och ifyllda.
Tidigare kunde WYSIWYG-fält i dynamiska rader (t.ex. i designkonfigurationsformulär) se tomma ut eller förlora sitt innehåll efter vissa åtgärder, vilket krävde manuell åtgärd för att återställa data.
AC-12336

_AC-12336 - [GitHub-problem](https://github.com/magento/magento2/issues/38893) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/7bdafaa2)_

#### [Problem] Korrigera MIME-typ

Systemet hanterar och korrigerar MIME-typen och typen av gif-bild korrekt

_AC-8001 - [GitHub-problem](https://github.com/magento/magento2/issues/36899) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/36669)_

#### [Problem] Ta bort ej tillåten `@author`-tagg från `Magento_Backend`

Den här PR-funktionen tar bort taggen `@author` från kodbasen

_AC-8814 - [GitHub-problem](https://github.com/magento/magento2/issues/37522) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/36976)_

#### [Problem] Undvik direktåtkomst till granskningslistan Ajax

Systemet hanterar och förhindrar direkt åtkomst till granskningslistan Ajax

_AC-9381 - [GitHub-problem](https://github.com/magento/magento2/issues/37920) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/33876)_

#### Inloggning/utloggning av huvud uppdateras inte i inställningarna för flera arkiv med delade cookies

Inloggningsrubriken uppdateras korrekt vid utloggning i enlighet med konfigurationsinställningarna. customer-data.js använder en cookie för att lagra värdet för image-customer-login om kundkontona delas globalt. Lokal lagring används annars.

_ACP2E-4149 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/e885088b)_

#### [Mobile] Fotorama kan öppna en stängningsåtgärd för Mini Cart i Image Viewer

Åtgärdade problemet med Fotorama. Tidigare öppnades en Mini Cart i Image Viewer-stängningsåtgärden

_ACP2E-4231 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/e885088b)_

#### Sammanfogade js-filer genereras inte korrekt i projekt med många butiker.

Nu fungerar sammanslagning av JavaScript-filer korrekt när flera arkiv är konfigurerade.
Tidigare kunde filer ibland inte sammanfogas korrekt i flerlagringsinställningar, vilket resulterade i ofullständiga eller inkonsekventa resultat.

_ACP2E-4246 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/ab891304)_

### Uppgraderingar - verktyg för uppgraderingskompatibilitet

#### Föråldrad funktionalitet: Skapande av den dynamiska egenskapen Magento\Framework\Acl::$_roleRegistry

Inaktuella funktionsfel förhindrar inte längre åtkomst till administratörspanelen efter uppgraderingen.
När du tidigare har uppgraderat till Magento 2.4.6 kan ett försök att komma åt administratörspanelen resultera i följande fel:
&quot;Föråldrad funktionalitet: Skapande av den dynamiska egenskapen Magento\Framework\Acl::$_roleRegistry är föråldrat i vendor/magento/framework/Session/SessionManager.php på rad 186&quot;
Detta förhindrade administratörer från att logga in.
AC-12343

_AC-12343 - [GitHub-problem](https://github.com/magento/magento2/issues/37469)_
