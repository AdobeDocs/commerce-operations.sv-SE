---
source-git-commit: 151272eed6c4bb2e1c2e5138a5c8a3a7e7bd8fe6
workflow-type: tm+mt
source-wordcount: '6077'
ht-degree: 0%

---
# Adobe Commerce åtgärdade problem (v2.4.9-alpha3)

## Åtgärdade problem i v2.4.9-alpha3

Vi har åtgärdat 129 problem i Adobe Commerce 2.4.9-alpha3-kärnkoden. En deluppsättning av de åtgärdade problemen som ingår i den här versionen beskrivs nedan.

### API:er

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

#### REST API-slutpunkt export-stock-salable-quet returnerar felaktigt antal poster total_count

Ett problem med sidnumrering i API:t för lagerexportlagersaldo där total_count felaktigt begränsades till sidstorleken har åtgärdats. Tidigare, när du använde slutpunkten /rest/all/V1/layer/export-stock-salable-qty/website/base med sidnumreringsparametrar som page_size=5, skulle fältet total_count i svaret returnera 5 i stället för det faktiska antalet produkter som matchar sökvillkoren. Efter den här korrigeringen återspeglar fältet total_count nu korrekt det totala antalet produkter som är tillgängliga oavsett page_size-parametern, vilket säkerställer ett konsekvent sidnumreringsbeteende för alla Magento REST API-slutpunkter.

_ACP2E-4086 - [GitHub-kodbidrag](https://github.com/magento/inventory/commit/5632fb5e)_

#### Attacker kan använda POST-begäran med REST API och skicka RCE-nyttolast

REST API:er V1/gästcarts/&lt;cartId>/items/ and V1/carts/mine/items/ validerar nu &quot;product_options.extension_attributes.custom_options.*.option_id&quot; om du vill vara ett giltigt option_id i artikelvagnsartikeln SKU. Tidigare bearbetades och sparades ett sådant alternativ i databasen utan validering.

_ACP2E-4138 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/a1c57b2e)_

### Konto

#### [Problem] Onödigt avstånd i backend-stödrastret har tagits bort

Systemet tar nu bort onödiga avstånd i backend-stödrastret när det finns markerade objekt

_AC-11579 - [GitHub-problem](https://github.com/magento/magento2/issues/38502) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/32622)_

#### Det går inte att rensa kommentar för önskelisteobjekt via `updateProductsInWishlist` GraphQL-mutation

Ett problem där önskelistekommentarer inte uppdaterades via GraphQL-mutationer har korrigerats.
Nu uppdateras kommentarerna korrekt och återspeglas både i API-svaret och i butiken.

_AC-14682 - [GitHub-problem](https://github.com/magento/magento2/issues/39911) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/36d4d6fb)_

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

#### Problem efter inloggning i magento 2.4.8-p1

Korrigerat problem i Magento 2.4.8-p1 där länken Skapa ett konto fortfarande var synlig på startsidan efter inloggningen.
Länken döljs nu korrekt efter inloggning, vilket överensstämmer med andra sidor.

_AC-15292 - [GitHub-problem](https://github.com/magento/magento2/issues/40120)_

### Administratörsgränssnitt

#### [Utgåva] - ersätt borttagen

Denna PR tar bort den borttagna getEscaper() och lägger till den via konstruktorinjektion

_AC-15132 - [GitHub-problem](https://github.com/magento/magento2/issues/40062) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/38135)_

#### Välkomstmeddelandet överlappar produktkategorin i mobilvyn.

Ett gränssnittsproblem har korrigerats där välkomstnamnet överlappade produktkategorier i mobilvyn, vilket blockerade klick.
Nu är kategorier helt synliga och klickbara utan överlappningsproblem.

_AC-15166 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/1b1baf1d)_

#### &quot;Det går inte att tolka reCAPTCHA-parametern&quot; i undantag.log för administratörspanelen för Google reCAPTCHA

Ett reCaptcha-fel i filen `var/log/exception.log` för inloggningen för Google V3 reCAPTCHA Admin har åtgärdats och inga felmeddelanden loggas. Tidigare utlöstes följande fel var några sekund när en administratörsanvändare konfigurerade sina **Configuration** > **Security** > **administratörsinställningar för Google reCAPTCHA**: `main.ERROR: Can not resolve reCAPTCHA parameter. {&quot;exception&quot;:&quot;[object] (Magento\Framework\Exception\InputException(code: 0): Can not resolve reCAPTCHA parameter. at /home/xxxxxxx/public_html/vendor/magento/module-re-captcha-ui/Model/CaptchaResponseResolver.php:25)&quot;} []`.  [GitHub-34975](https://github.com/magento/magento2/issues/34975)

_AC-3179 - [GitHub-problem](https://github.com/magento/magento2/issues/34975) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/4f7e5983) - [GitHub-kodbidrag](https://github.com/magento/security-package/commit/804dbc2a)_

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

_ACP2E-4052 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/52f46328)_

### Administratörsgränssnitt, skatt

#### Fel i administrationsgränssnitt för momssats

Den här biljetten åtgärdade ett gränssnittsproblem för momsadministratör där växling av land (t.ex. från USA → Storbritannien) fortfarande visade den tidigare valda amerikanska staten, missvisande användare.
I 2.4.9-alpha3 återställs nu tillståndsfältet till * när det valda landet inte har några lägen.

_AC-8440 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/a3b1abc2)_

### B2B

#### Återstående API-produkter-render-info returnerar fel slutpris för inloggad kund

Biljetten har en korrigering för Rest API-produkter-render-info returnerar fel slutpris för inloggad kund

_AC-5979 - [GitHub-problem](https://github.com/magento/magento2/issues/35757) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/)_

#### Knappen Lägg till i rekvisitionslistan försvinner när vi försöker lägga till den från katalogsidan

Knappen Lägg till i rekvisitionslistan försvinner när vi försöker lägga till den från en katalogsida som nu är fast och vi kan se rekvisitionsknappen på kategorisidan

_AC-8575_

### B2B, kundvagn och kassan

#### Ingen sådan entitet med cartId = X-fel visas på Storefront när B2B-företagsanvändare loggar in från administratörsfunktionen Logga in som kund

Nu visas ingen sådan entitet med cartId = X-fel efter att ha loggat in från administratörens serverdel med funktionen Logga in som kund.

_ACP2E-3994 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/2a1e1e55)_

### Kort och utcheckning

#### [Problem] Lägg till EventPrefix och EventObject i utcheckningsavtalsmodellen

Systemet inkluderar nu EventPrefix och EventObject för kassaavtalsmodellen, vilket gör att händelser kan utlösas med ett händelseprefix. Den här förbättringen ger större flexibilitet för utvecklare när de arbetar med avtalshändelser i kassan. Tidigare hade arbetsavtalsmodellen inte stöd för EventPrefix och EventObject, vilket begränsade möjligheten att anpassa händelsehantering.

_AC-13252 - [GitHub-problem](https://github.com/magento/magento2/issues/32510) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/32451)_

#### [Graphql] Det går inte att returnera null för det icke-nullbara fältet SelectedCustomizableOption.label

Systemet genererar nu inget internt serverfel med ett meddelande när det valda alternativet inte längre finns

_AC-14256 - [GitHub-problem](https://github.com/magento/magento2/issues/39729) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/39888)_

#### [2.4.8] Det går inte att placera order där City har siffrorna 0-9, Ampersand, stopp eller parentes i stadsnamnet

Ett problem har korrigerats där utcheckningen misslyckades för stadsnamn som innehåller specialtecken som . och, eller parenteser.
Nu kan beställningar med sådana stadsnamn placeras utan valideringsfel.

_AC-14495 - [GitHub-problem](https://github.com/magento/magento2/issues/39854) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/b9f5d6f7)_

#### Salesrule Delmarkera med kvantitetsvillkor ej tillämpligt

Ett problem har korrigerats där kundprisregler med delurvalsvillkor för produkt inte tillämpades vid utcheckningen.
Rabatterna tillämpas nu enligt de konfigurerade reglerna.

_AC-14884 - [GitHub-problem](https://github.com/magento/magento2/issues/39965) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/fe72c407)_

#### Graphql - Kopplingsvagnen fungerar inte korrekt när backorder är aktiverad

Ett problem har korrigerats där gästvagnsartiklar inte samlades med kundvagnen när vagnen samlades via GraphQL.
Nu återspeglar kundvagnen den kombinerade kvantiteten från både gäst- och kundvagn korrekt.

_AC-15148 - [GitHub-problem](https://github.com/magento/magento2/issues/40064) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/a3b1abc2)_

#### [Integrering] [Utcheckning] Beroendedirektiv har uppdaterats i mallen för misslyckade betalningar

E-postmallen för betalning som uppdaterats för att hantera beroende direktiv på fel sätt misslyckades.
Fix säkerställer att leveransadress och leveranssätt visas korrekt när det är tillämpligt.
Tidigare saknades dessa fält i misslyckade e-postmeddelanden om betalningar.

_AC-15363 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/36d4d6fb)_

#### [Cloud] Fri frakt-rabatt tas inte bort korrekt när vagnen inte längre uppfyller kraven

Delsumman (exkl. Moms) i kundprisregeln kommer nu att inkludera rabatter från föregående regler.

_ACP2E-3973 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/6dd3fa99)_

#### Dubblettorder hittades för samma kund i Multishipping

Samtidiga beställningar av flera leveransadresser resulterar inte längre i dubbla beställningar för samma kund

_ACP2E-4117 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/a1c57b2e)_

### Kort och utcheckning, beställning, produkt

#### Presentkortets e-postadress skickas även om orderfakturan inte fungerar

Före implementeringen av den här korrigeringen skickades presentkortsmeddelanden efter att fakturan hade skapats. Men efter att korrigeringen har tillämpats skickas presentkortsms nu när fakturor har sparats och verkställts.

_ACP2E-3905_

### Kort och utcheckning, säkerhet

#### [CLOUD] Hämtar 404 för JS-fil på utcheckningssidan vid första försök efter implementering av Sri patch

Före korrigeringsblandningarna hade de inte lästs in i varukorgen och i kassan när minify och bundling är aktiverat. Efter korrigeringen ska alla mixins läsas in som förväntat.

_ACP2E-4128 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/e457c5e2)_

### Katalog

#### Problem med pris och config.php

I Magento 2.4.2 uppdateras inte is_global-värdet i catalog_eav_attribute för prisattributet korrekt om prisomfattningen ändras via config.php.
Detta innebär att produktpriserna förblir globala och inte kan sparas per webbplats, även om prisomfånget är inställt på en webbplats.
För att kringgå problemet måste du uppdatera kolumnen is_global i databasen manuellt, vilket inte är idealiskt för produktionsmiljöer.
Detta beteende är förenligt med Magento standarddesign, där prisomfånget är antingen Global eller Website, men inte per butiksvy.

_AC-13857 - [GitHub-problem](https://github.com/magento/magento2/issues/33559)_

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

#### Dynamisk bildgenerering genererar ett stort antal bilder

Efter korrigeringen genereras bilder endast för de webbplatser som produkten är tilldelad till.

_ACP2E-3927 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/fab20b00)_

#### 500-fel inträffar på klientsidan eftersom en felaktig layoutstruktur cachas i layouten

Ett problem har korrigerats när en sida skulle returnera en felkod på 500 på grund av att en felaktig layoutstruktur cachelagrades i layouten

_ACP2E-4040 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/47721be6)_

#### Valideringsfel för rabattbeloppsfältet för katalogprisregel i den schemalagda uppdateringen

Innan den här utgåvan åtgärdats validerades inte rabattbeloppet korrekt för katalogprisregeln om rabattbeloppet är by_fixed på grund av regeln för valideringsnummer. När den här korrigeringen har tillämpats fungerar valideringen korrekt för katalogprisregeln fast pris.

_ACP2E-4054 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/6dd3fa99)_

#### Produkterna visas som utgångna efter inaktivering

Efter korrigeringen finns inaktiverade produkter inte i produktwidgeten.

_ACP2E-4136 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/a1c57b2e)_

#### [Cloud] Fel med dubblettposter (temp_category_descendants_%)

Ett problem med dubblettposter när schemalagda uppdateringar skapades för miljöer med många kapslade kategorier har korrigerats

_ACP2E-4159 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/a1c57b2e)_

### Katalog, GraphQL

#### GraphQl ogiltig rabattberäkning

GraphQL visar nu korrekt rabattprocentsatser och baspriser när katalogpriserna är konfigurerade att inkludera moms. Tidigare uppstod avrundningsfel, till exempel 19,99 % i stället för 20 %.

_ACP2E-3993 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/e457c5e2)_

### Katalog, produkt

#### Relaterade produkter via relaterade produktregler visas inte i PDP via GraphQL

Innan den här korrigeringen tillämpades returnerade regeln tom/null för en produkt som matchade regeln. När den här korrigeringen har tillämpats har den relativa regeln för produktreturer tillämpats för matchade produkter.

_ACP2E-3949_

### Innehåll

#### graphql (magento 2.4.6-p4) - fel när försök görs att hämta cms-sidan utan aktiv status

Ett problem har korrigerats där en GraphQL-fråga om en inaktiverad CMS-sida returnerade ett internt serverfel.
Nu hämtar frågan ett korrekt svar utan fel.

_AC-12302 - [GitHub-problem](https://github.com/magento/magento2/issues/38877) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/1b1baf1d)_

#### [GraphQl] Flödesfråga, oändlig slinga

Den här biljetten åtgärdade ett problem där en GraphQL-ruttfråga med identisk sökväg för begäran och målsökväg orsakade en oändlig loop och så småningom orsakade timeout.
I 2.4.9-alpha3 returnerar frågan nu rätt felsvar i stället för slingor.

_AC-14269 - [GitHub-problem](https://github.com/magento/magento2/issues/39707) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/68a45d0a)_

#### Ändra konstanten IMAGE_FILE_NAME_PATTERN till synlig för att öka flexibiliteten

Konstanten IMAGE_FILE_NAME_PATTERN i GenerateRenditions.php har gjorts offentlig för att ge utvecklare större flexibilitet när de arbetar med bildåtergivningar. Korrigeringen ingår i Magento 2.4.9-alpha3 med fullständig enhets- och integrationstesttäckning.

_AC-15338 - [GitHub-problem](https://github.com/magento/magento2/issues/39733) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/68a45d0a)_

#### Förhandsgranskning av innehållstaggar fungerar inte med sökresultat

Sökning i mellanlagringsförhandsvisning returnerar nu produkter i enlighet med det valda omfånget. Tidigare returnerade sökningen resultat i standardomfånget, utan hänsyn till det valda arkivet.

_ACP2E-4095_

#### Page Builder - Product Condition Logic Issue (OR logic beter sig felaktigt med att visa färre produkter)

Page Builder Products Widget returnerar nu korrekt resultat när ett attribut med globalt omfång används i villkoret Matcha något

_ACP2E-4096 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/e457c5e2)_

### Kund/Kunder

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

#### [Problem] Gör metodsignaturen konsekvent med gränssnittet

Metodsignaturen för getAttributes är nu konsekvent med dess gränssnitt, vilket förhindrar fel när metoden skrivs över. Tidigare orsakade inkonsekvenser i metodsignaturen fel när metoden getAttributes skulle skrivas över.

_AC-11578 - [GitHub-problem](https://github.com/magento/magento2/issues/38501) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/31955)_

#### [Problem] Korrigera verifierings-e-postregel för UI-komponent

Systemet validerar nu korrekt flera e-postadresser som anges i gränssnittskomponenterna, vilket säkerställer att varje e-postadress trimmas och valideras korrekt. Tidigare använde systemet en felaktig metod för att trimma e-postadresser, vilket kunde leda till valideringsfel.

_AC-11719 - [GitHub-problem](https://github.com/magento/magento2/issues/38528) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/33470)_

#### [Problem] Ta bort överflödiga metoder

Kodkvalitet: Tog bort redundanta metoder i AsynchronousOperations- och Sales-komponenter som endast anropade överordnade metoder utan att lägga till funktioner, vilket förbättrar kodunderhållet.

_AC-11915 - [GitHub-problem](https://github.com/magento/magento2/issues/29748) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/29147)_

#### xsd-validering misslyckas för etc/adminhtml/system.xml filer som innehåller kommentarer under fältobjekt.

Den här PR:en korrigerar XML-schemadefinitioner i phpstorm för kommentarnod

_AC-12945 - [GitHub-problem](https://github.com/magento/magento2/issues/39148) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/39867)_

#### Magento 2.4.8 använder dev-paket som inte följer semantisk versionshantering

Magento 2.4.8 kräver dev-versioner av pdatorparken/ptypen och phpmd/phpmd (3.x-dev) för PHP 8.4-kompatibilitet.
Dessa dev-versioner är i konflikt med verktyg från tredje part som förväntar sig SemVer-kompatibla paket, vilket förhindrar vissa uppgraderingar.
En tillfällig lösning är att aliasera dev-versionerna i Composer.json (t.ex. &quot;3.x-dev as 3.99.0&quot;), vilket möjliggör kompatibilitet samtidigt som semantisk versionshantering uppfylls.
Detta säkerställer att stödet för PHP 8.4 kan hanteras och undviker konflikter tills stabila releaser blir tillgängliga.

_AC-14519 - [GitHub-problem](https://github.com/magento/magento2/issues/39796)_

#### Resterande API: anrop till en medlemsfunktion getVideoProvider() på null

Ett problem har korrigerats där anrop till den konfigurerbara produkten med underordnade API returnerade ett 500 internt serverfel om en underordnad produkt bara hade en YouTube-video och inga andra bilder.
Felet orsakades av en null-referens i ExternalVideoEntryConverter.
API:t returnerar nu korrekt underordnade produkter med mediegalleriposter, inklusive externa videodata, utan att några fel genereras.
Detta garanterar att alla medietyper för underordnade produkter hämtas korrekt via REST API.

_AC-15046 - [GitHub-problem](https://github.com/magento/magento2/issues/40021)_

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

#### Uppdatera modulen Viktigt och åtgärda dokumentlänkar

_AC-15340 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/ec9459d0)_

#### [Utgåva] Logga in odeklarerad plugin-fil endast om den inte är inaktiverad

Denna PR korrigerar och loggar plugin-programmet som är odeklarerat och inte används (aktiverad och saknad instans).

_AC-15386 - [GitHub-problem](https://github.com/magento/magento2/issues/40086) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/40081)_

#### Magento 2.4.8-p2, magento/framework version 103.0.8-p2: klassen EmailMessage anropar en metod som inte finns

_AC-15446 - [GitHub-problem](https://github.com/magento/magento2/issues/40170) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/059fd469) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/e9412b24)_

#### [Magento 2.3.x] Data/Schema Patches getAliases() orsakar fel under `setup:upgrade`

getAliases() orsakar fel under installationen:upgrade, denna PR korrigerar samma

_AC-15559 - [GitHub-problem](https://github.com/magento/magento2/issues/31396) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/38239)_

#### Förväntad typ: Magento\Customer\Api\Data\GroupInterface. Hittade Magento\Customer\Model\Group.

Ett problem har korrigerats där ett typfel uppstod när en kundgrupp sparades via GroupRepositoryInterface med GroupFactory.
Tidigare förväntades GroupInterface i databasen, men gruppmodellinstanser skickades, vilket resulterade i ett allvarligt fel.
Nu kan kundgrupper sparas i databasen på ett korrekt sätt genom en korrekt gränssnittsimplementering.
Detta åtgärdar IDE-varningar och körningsfel när kundgrupper skapas eller uppdateras programmatiskt.

_AC-6909 - [GitHub-problem](https://github.com/magento/magento2/issues/36269)_

#### [Utgåva] Ta bort förbjuden `@author` -tagg

Den här PR-funktionen tar bort taggen `@author` från kodbasen

_AC-8349 - [GitHub-problem](https://github.com/magento/magento2/issues/37266) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/37016)_

#### [Utgåva] Ta bort förbjuden `@author` -tagg

Den här PR-funktionen tar bort taggen `@author` från kodbasen

_AC-8350 - [GitHub-problem](https://github.com/magento/magento2/issues/37265) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/37015)_

#### [Utgåva] Ta bort förbjuden `@author` -tagg

Den här PR-funktionen tar bort taggen `@author` från kodbasen

_AC-8359 - [GitHub-problem](https://github.com/magento/magento2/issues/37262) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/37012)_

#### [Utgåva] Ta bort förbjuden `@author` -tagg

Den här PR-funktionen tar bort taggen `@author` från kodbasen

_AC-8362 - [GitHub-problem](https://github.com/magento/magento2/issues/37259) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/37009)_

#### [Problem] Ta bort ej tillåten `@author`-tagg från `Magento_Backup` och `Magento_Bundle`

Den här PR-funktionen tar bort taggen `@author` från kodbasen

_AC-8367 - [GitHub-problem](https://github.com/magento/magento2/issues/37244) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/36979)_

#### [Problem] Korrigera variabelnamn i katalogsökning

Systemet namnger nu variabler korrekt i sökmotormodulen, vilket förbättrar kodklarheten och underhållet. Tidigare användes ett irrelevant variabelnamn, $defaultCountry, i sökmotormodulen, vilket orsakade förvirring.

_AC-9215 - [GitHub-problem](https://github.com/magento/magento2/issues/37810) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/33533)_

#### [QUANS]Serverproblem som kan orsakas av ogiltig S3-åtkomstnyckel

Felaktiga inloggningsuppgifter för AWS S3 gör inte längre att sidorna läses in oändligt på butiken.

_ACP2E-3890 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/2a1e1e55)_

#### [KVANS] [Molnet] Minify fungerar inte

Följande JS-filer är nu fullständigt och korrekt minimerade när JS-minification är aktiverat: mage/backend/tabs.min.j, jquery/jquery.validate.min.js och Magento_PageBuilder/js/form/element/validator-rules-mixin.min.js. Därför fungerar fältvalidering av CSS-klassen i Page Builder som förväntat.

_ACP2E-3925 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/47721be6)_

#### Cron-jobbet rensade inte databastabellen, vilket orsakade avbrott på grund av Galera-krasch

Rensa tabeller i ändringsloggar körs nu i grupper för att undvika stora raderingsåtgärder.

_ACP2E-3995 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/52f46328)_

#### Ej minifierad JS läser ibland in ignorerar&quot;aktivera js minifications&quot;

Före korrigeringen begärdes några av JS-filerna utan &quot;min&quot;-prefixet, vilket resulterade i 404-statuskod, även om du hade minification aktiverat. När miniatyrbildsfunktionen är aktiverad efterfrågas inga icke-minifierade JS-resurser.

_ACP2E-4058 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/6dd3fa99)_

#### Datumattribut i anpassad attributgrupp kan inte visa datumväljare i administratör

Ett problem har korrigerats där kalenderpopup-fönstret för datumattribut visades utanför skärmen när det tilldelats anpassade attributgrupper.

_ACP2E-4060 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/6dd3fa99)_

### GraphQL

#### Customer Order GraphQL: Retrieve product categories for the associated product is &quot;not visible individual

Före korrigeringen, om ordern innehöll en dold produkt, skulle dess kategorier visa en tom array i kundorderns GraphQl-svar.
Efter korrigeringen ingår nu produktkategorierna i svaret på en begäran om kundorder GraphQl, även om produkten är dold.

_ACP2E-3945 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/2a1e1e55)_

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

### GraphQL, Inventory / MSI

#### GraphQL mergeCart - mutationsavvikelser

Efter korrigeringen kontrollerar de kundvagnar som GraphQL begär produktkvantiteten med hänsyn till lagerkonfigurationen.

_ACP2E-4184 - [GitHub-kodbidrag](https://github.com/magento/inventory/commit/5632fb5e)_

### GraphQL, säkerhet

#### Återställning av kundens lösenord via GraphQL följer inte begränsningarna

Löste ett problem där begäranden om återställning av kundlösenord som gjorts via GraphQL-mutationer inte uppfyllde de lösenordsåterställningsbegränsningar som konfigurerats under Store > Konfiguration > Kunder > Kundkonfiguration > Lösenordsalternativ. Dessa inställningar används nu korrekt.

_ACP2E-3992 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/6dd3fa99)_

### Importera/exportera

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

### Lager/MSI

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

### Beställning

#### Magento 2.4.8 GraphQL - Order Items order_date - felaktig formatering

Ett problem har korrigerats där fältet order_date i GraphQL-svar returnerades i formatet åååå-mm-dd.
Nu visas order_date korrekt i formatet dd-mm-åååå.

_AC-14431 - [GitHub-problem](https://github.com/magento/magento2/issues/39805) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/a3b1abc2)_

#### E-postmeddelande om leverans skickas inte när det skickas från administrationsordervyn trots att det är aktiverat i butikskonfigurationen

Systemet skickar nu ett e-postmeddelande med en leveransbekräftelse när det är aktiverat i butikskonfigurationen där beställningen placerades.

_AC-14563 - [GitHub-problem](https://github.com/magento/magento2/issues/39861) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/39897)_

#### Filtrering på datum fungerar inte på grund av tvetydiga fältnamn

I Magento 2.4.7-p6 rapporterades att filtrering av ordningens rutnät efter datum orsakade ett fel på grund av kopplingar med Braintree-moduler.
Problemet gällde frågor som kopplade till tabellerna braintree_transaction_details och sales_order när datumfilter tillämpades.
Adobe Commerce Engineering granskade ärendet men kunde inte återskapa felet i miljön.
Förväntat beteende är att filtrering efter datum ska returnera order som matchar filtret utan fel.

_AC-15037 - [GitHub-problem](https://github.com/magento/magento2/issues/40024)_

#### Magento2: Det går inte att skapa kampanjregeln

Den här PR-korrigeringen, vi får
\Magento\Catalog\Model\ResourceModel\Eav\Attribute i stället för \Magento\Catalog\Model\ResourceModel\Eav\Attribute i metoden \Magento\SalesRule\Model\Rule\Condition\Product::loadAttributeOptions

_AC-15358 - [GitHub-problem](https://github.com/magento/magento2/issues/12176) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/30479)_

#### Avbryt fakturaomdirigeringar till 404

Annullering av fakturan som gjorts med Inte hämtningstyp leder inte längre till sidan 404.

_ACP2E-4001 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/2a1e1e55)_

#### Cron-jobb för försäljningsarkiv orsakar problem med databaslåsning

Innan korrigeringen kunde obundna DELETE-frågor som fanns i arkivkron orsaka problem med Galera. Efter uppdateringen körs raderingsfrågor med begränsningar.

_ACP2E-4010_

#### Problem med uppdaterade order med konfigurerbara alternativ med REST API

Bevara befintliga produktalternativ för försäljningsorderartiklar när en order uppdateras via betalpunkter.

_ACP2E-4061 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/6dd3fa99)_

### Andra utvecklingsverktyg

#### [Problem] Rensa oanvänd kod.

Systemet tar nu bort oanvänd kod för oanvända importer.

_AC-10980 - [GitHub-problem](https://github.com/magento/magento2/issues/38424) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/33499)_

#### [Problem] Tillgänglighet: WAI-ARIA-roller som är felaktiga på menyn

Systemet genererar nu fyr-hjälpmedel utan WAI-ARIA-roller som är felaktiga i menyfel och rapporten ska vara grön

_AC-15082 - [GitHub-problem](https://github.com/magento/magento2/issues/40045) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/38617)_

#### Konsolfel i förhandsgranskning av e-post i Magento-administratören

Systemet genererar inga konsolfel när vi förhandsgranskar e-postmallen

_AC-9245 - [GitHub-problem](https://github.com/magento/magento2/issues/37820) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/37933)_

### Betalningar

#### Okända IPN:er från PayPal missbrukar programmets IPN-processor

IPN-hanteraren ignorerar nu IPN-typer som inte stöds eller är okända. I stället för att returnera 500 fel loggas problemet och bearbetningen fortsätter utan avbrott.

_ACP2E-4049 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/6dd3fa99)_

#### PayflowPro sparad korttoken misslyckades vid betalning

PayPal PayFlow Pro-transaktions-ID:n (PNREF) kan nu användas i referenstransaktioner under en fast period på 12 månader. När kortet har gått ut visas det inte längre och måste läggas till igen. Tidigare fastställdes giltigheten av utgångsdatumet för det betalkort som användes i den ursprungliga transaktionen.

_ACP2E-4064 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/52f46328)_

### Prestanda

#### [Problem] Uppdatera använd cachekontroll som inte kan ändras för statisk plats

Den här PR-funktionen lägger till prestandaförbättringar genom att inte validera det statiska innehållet på varje sidinläsning förrän &amp; såvida det inte har ändrats.

_AC-15171 - [GitHub-problem](https://github.com/magento/magento2/issues/39486) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/39484)_

#### [CLOUD] Det går inte att lägga till produkter i kategorier

Förbättrade prestanda när du lägger till produkter i en kategori via Visual Merchandiser.

_ACP2E-3946 - [GitHub-kodbidrag](https://github.com/magento/inventory/commit/29653b1d)_

#### [Cloud] cache_invalidate över 10K-loggar

Tidigare rensades cache på varje PLP- eller Cart-besök, vilket orsakade onödig prestandaförsämring. Målregelcachen är inte längre ogiltigt på dessa sidor, vilket förbättrar webbläsningseffektiviteten.

_ACP2E-4059_

### Priser

#### Produkten sparas även när specialpriset är från datum är senare än Till datum med massåtgärd

Ett problem har korrigerats där produkter kunde sparas med ett ogiltigt datumintervall för specialpris utan validering.
Nu visas ett felmeddelande:&quot;Kontrollera att Till-datumet är senare än eller samma som Från-datumet.&quot;

_AC-15252 - [GitHub-problem](https://github.com/magento/magento2/issues/40113) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/36d4d6fb)_

#### Leveransdetaljerna matchar inte efter att ha slutfört utcheckningen av en betalande offert.

Problemet åtgärdade ett leveransfel vid slutförande av en PayPal Express-utcheckning för en godkänd överlåtbar offert.
Före korrigeringen fördubblades leveransen felaktigt (10 dollar istället för 5 dollar), vilket ledde till ett totalt belopp.
Programfixen i Magento 2.4.9 alpha3 säkerställer att rätt fraktkostnad används

_AC-15280_

#### Specialpriset gäller inte för webbplatser som skapats med olika tidszoner

Före korrigeringen skapades giltigheten för det särskilda prisdatumet i omfånget för den aktuella butikens tidsstämpel. När korrigeringen är klar beaktas standardarkivets tidszon.

_ACP2E-4002_

#### Normalpriset syns inte, även om ett specialpris används.

Löste ett problem där normalpriset inte visades när ett specialpris tillämpades. Normalpriset visas nu korrekt tillsammans med specialpriset som förväntat.

_ACP2E-4100 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/47721be6)_

### Produkt

#### Etiketten&quot;Så lite som&quot; visas fortfarande för en konfigurerbar produkt för testfallet AC-6158

Implementerade och verifierade konfigurerbara produkter (P1-P7) med respektive variationer och kategoritilldelningar. Korrekt butiksprisvisning och etikettbeteende för&quot;Så lågt som&quot; för produkter i kategori C säkerställs.

_AC-10847 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/a3b1abc2)_

#### Extra loggning vid begäran av en produkt via databas misslyckas

Förbättrade felmeddelanden för ProductRepository::get och getById när det inte går att hitta en SKU eller ett ID.
Tidigare fanns det ingen kontext för vilka SKU eller ID som orsakade felet.
Undantagsmeddelandet innehåller den saknade SKU:n eller ID:t, vilket underlättar felsökning och förbättrar utvecklingsmiljön.
Den här ändringen påverkar inte något funktionellt beteende för API:t.

_AC-15199 - [GitHub-problem](https://github.com/magento/magento2/issues/40090) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/1b1baf1d)_

#### Enkla produkter ej tilldelade vid konfigurerbar produkt redigerad av begränsad roll

Före den här korrigeringen togs en begränsad admin-användare bort från den konfigurerbara produkten när den sparades om de skulle spara en konfigurerbar produkt som innehåller enkla produkter som administratörsanvändaren inte hade tillgång till. Efter korrigeringen bevaras den konfigurerbara produkten som sparad från en administratör med fullständig behörighet.

_ACP2E-4081_

#### [Prestanda för generering av webbplatskartor i molnet] har försämrats avsevärt

Framtagning av webbplatskartor för produkter med bilder upplever inte längre exponentiell avmattning. Tidigare skulle generering av platskartor för butiker med aktiverad bildinkludering ge långa bearbetningstider.

_ACP2E-4153 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/e457c5e2)_

### Kampanj

#### Det gick inte att hämta rabatt för orderartikel tillämpad_på för kundorder via GraphQl-kundförfrågan

Tidigare när rabatter som tillämpats_på för kundorder via GraphQl kundbegäran observerades ett internt serverfel som nu är fast och korrekta kundorderdata med rabatt hämtas

_AC-14888 - [GitHub-problem](https://github.com/magento/magento2/issues/39963) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/fe72c407)_

#### Det gick inte att hämta orderartikelkupongkod för kundorder via GraphQl-kundförfrågan

Ett problem där hämtning av order med kuponginformation via GraphQL returnerade ett internt serverfel har åtgärdats.
Frågan körs nu och returnerar rätt kuponginformation i svaret.

_AC-14889 - [GitHub-problem](https://github.com/magento/magento2/issues/39962) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/fe72c407)_

### SEO

#### Odefinierad matrisnyckel i ProductRepository getById

Problemet uppstod när ProductRepository::getById() anropades med ett ogiltigt ID som 123abc, vilket ledde till ett&quot;undefined array key&quot;-fel.
Efter korrigeringen i Magento 2.4.9-alpha3 returnerar sådana begäranden nu korrekt en 404-sida i stället för att generera ett undantag.
Kvalitetsbedömningen har bekräftats med både giltiga och felformaterade ID:n och inga ytterligare problem har observerats.

_AC-15345 - [GitHub-problem](https://github.com/magento/magento2/issues/40146) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/68a45d0a)_

#### [Genereringen av webbplatskartor i molnet] upphör aldrig

Före korrigeringen kunde platskartan inte skapas korrekt om katalogen innehöll mer än en miljon produkter. Efter korrigeringen kommer webbplatskartan att genereras med mindre minnesallokering och med så många som en miljon produkter per butik.

_ACP2E-3902 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/52f46328)_

#### [Cloud] Store-växlaren fungerar inte från EN till FR för sidan med vanliga frågor

Ett problem har korrigerats där växling mellan butiksvyer omdirigerade användare till hemsidan i stället för till motsvarande översatta CMS-sida. Butiksväljaren söker nu efter URL-omskrivningar i målbutiken för att säkerställa korrekt omdirigering (t.ex. sidan med vanliga frågor och svar på engelska → sidan med vanliga frågor på franska).

_ACP2E-4112_

### Mellanlagring och förhandsvisning

#### Förgranskning av mellanlagringsuppdatering avbryts vid utcheckning när en annan administratörsdomän används

En kund kan logga in och visa sin kundvagn i butiksförhandsgranskningsläge när butiksbas-URL:en inte är samma som admin-URL:en.

_ACP2E-3906_

#### Instrumentpanel för innehållsmellanlagring - visning av tid är felaktigt

Nu visar datumfiltren &quot;Starttid&quot; och &quot;Sluttid&quot; i &quot;Kontrollpanel för innehållsmellanlagring&quot; rätt datum och tid. Tidigare visades fel datum och tid efter att du valt datum och tid i datumväljaren

_ACP2E-3969_

#### Olika butiksvy visas under förhandsgranskning för schemalagda uppdateringsprodukter och -kategori

Före den här korrigeringen genererades inte förhandsgranskningslänken för kategorier och produkter för rätt butik. Efter den här korrigeringen väljer förhandsgranskningslänken automatiskt den butik som förhandsgranskningen skapades på.

_ACP2E-4053_

### UI Framework

#### [Problem] Ta bort ej tillåten `@author`-tagg från `Magento_Backend`

Den här PR-funktionen tar bort taggen `@author` från kodbasen

_AC-8814 - [GitHub-problem](https://github.com/magento/magento2/issues/37522) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/36976)_
