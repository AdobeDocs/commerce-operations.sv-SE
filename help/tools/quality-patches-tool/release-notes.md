---
title: Versionsinformation
description: Läs mer om vilka korrigeringsfiler som finns för Adobe Commerce och vilka problem de löser.
source-git-commit: 2754ce0c8e27d51777924f4640b81628fbb2ea81
workflow-type: tm+mt
source-wordcount: '10379'
ht-degree: 0%

---

# Versionsinformation

The [[!DNL Quality Patches Tool]](https://github.com/magento/quality-patches) levererar individuella plåster som utvecklats av Adobe och Magento Open Source-communityn. Med den kan du tillämpa, återställa och visa allmän information om alla enskilda korrigeringsfiler som är tillgängliga för den installerade versionen av Adobe Commerce eller Magento Open Source. Du kan använda korrigeringsfiler i Adobe Commerce- och Magento Open Source-projekt oavsett vem som har utvecklat korrigeringsfilen. Du kan till exempel använda en korrigering som utvecklats av communityn på Adobe Commerce-projekt.

>[!INFO]
>
>Se [Tillämpa patchar](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html#apply-individual-patches) för instruktioner om hur du använder korrigeringsfiler i dina Adobe Commerce- eller Magento Open Source-projekt. Se [Tillgängliga korrigeringar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i programuppdateringshandboken för att se en fullständig lista över de släppta korrigeringsfilerna.

>[!INFO]
>
>Mer information om [!DNL quality patches] som skapats av gemenskapen för Magento Open Source, se [versionsinformation](https://github.com/magento/quality-patches/blob/master/community-release-notes.md).

## v1.1.25 {#v1-1-25}

* **ACSD-48058** (för Adobe Commerce och Magento Open Source >=2.4.5 &lt;2.4.6) - Korrigerar problemet där produktprisomindexering inte fungerar om paketprodukten inte har tilldelats någon webbplats.
* **ACSD-48262** (för Adobe Commerce och Magento Open Source >=2.4.5 &lt;2.4.6) - Korrigerar problemet där produkter inte visas i förgrunden när inställningen &quot;Tillåt alla produkter per sida&quot; är inställd på Ja.
* **ACSD-48293** (för Adobe Commerce och Magento Open Source >=2.4.3 &lt;2.4.4) - Korrigerar problemet där sammansatta produkter lämnar lager när de underordnade produkter som sålts returneras till lager.
* **ACSD-47520** (för Adobe Commerce och Magento Open Source >=2.4.0 &lt;2.4.6) - Korrigerar problemet där kunderna förlorar belöningspoäng när en kreditnota skapas.
* **ACSD-48044** (för Adobe Commerce och Magento Open Source >=2.4.0 &lt;2.4.4) - Korrigerar problemet där användning av flera presentkort på en enda order med flera leveranser förhindrar att beställningar görs.
* **ACSD-48300** (för Adobe Commerce och Magento Open Source >=2.4.0 &lt;2.4.6) - Korrigerar problemet där en retur inte kan skapas om den konfigurerbara produkten tas bort.
* **ACSD-47910** (för Adobe Commerce och Magento Open Source >=2.4.4 &lt;2.4.6) - Korrigerar problemet med saknade order, fakturor, leveranser och kreditnotor i respektive entitetsrutnät.
* **ACSD-47292** (för Adobe Commerce och Magento Open Source >=2.4.4 &lt;2.4.6) - Korrigerar problemet där paketerade produkter som inte finns i lager inte är tillgängliga i GraphQL-svaret om &quot;show out-of-stock products&quot; är inställd på Ja.
* **ACSD-48234** (för Adobe Commerce och Magento Open Source >=2.4.5 &lt;2.4.6) - Korrigerar problemet där katalogsökresultatet visar ett felaktigt antal kategoriobjekt när alternativet &quot;visa ej i lager&quot; är aktiverat.
* **ACSD-48313** (för Adobe Commerce och Magento Open Source >=2.4.0 &lt;2.4.5) - Korrigerar problemet där kolumnen &quot;configurable_variations&quot; inte tolkas om attributvärdet innehåller ett komma. Samma parsningsalgoritm används för &quot;additional_attributes.
* **ACSD-48627** (för Adobe Commerce och Magento Open Source >=2.4.5 &lt;2.4.6) - Korrigerar problemet där den konfigurerbara produkten som inte finns i lager orsakar ett fel när en GraphQL-begäran skickas för att få kundvagnsinformation.
* Uppdaterad patch: MDVA-39384.

## v1.1.24 {#v1-1-24}

* **ACSD-45168** (för Adobe Commerce och Magento Open Source >=2.4.2 &lt;2.4.6) - Korrigerar problemet där SEO-vänliga URL:er inte genereras för produkter som har *url_key* attribut åsidosätts på butiksvynivå.
* **ACSD-46865** (för Adobe Commerce och Magento Open Source >=2.4.4 &lt;2.4.6) - Korrigerar problemet där rutnätet för utleverans och kreditnota inte fylls i när asynkron indexering är aktiverat.
* **ACSD-47004** (för Adobe Commerce och Magento Open Source >=2.4.2 &lt;2.4.6) - Korrigerar problemet där moms inte tillämpas på en faktureringsadress utan moms-ID.
* **ACSD-47803** (för Adobe Commerce och Magento Open Source >=2.4.0 &lt;2.4.6) - Korrigerar problemet där ej lagrade konfigurerbara produktfärgrutor visas som tillgängliga.
* **ACSD-47137** (för Adobe Commerce och Magento Open Source >=2.4.4 &lt;2.4.6) - Förbättrar inläsningshastigheten för bildgalleriet när mappen pub/media är mycket stor.
* **ACSD-46770** (för Adobe Commerce och Magento Open Source >=2.4.0 &lt;2.4.6) - Korrigerar problemet där e-postmeddelanden om administratörsorder skickas även när *E-postorderbekräftelse* är inte markerad.
* **ACSD-47955** (för Adobe Commerce och Magento Open Source >=2.4.4 &lt;2.4.6) - Korrigerar problemet där GraphQL inte visar kundvagnsrabatten korrekt.
* **ACSD-46617** (för Adobe Commerce och Magento Open Source >=2.4.0 &lt;2.4.6) - Korrigerar problemet där *Fortsätt till kassan* knappen är nedtonad även om delsumman är större än den konfigurerade *Minsta orderbelopp*.
* **ACSD-47079** (för Adobe Commerce och Magento Open Source >=2.4.4 &lt;2.4.5) - Korrigerar problemet där sammansatta produkter (bundle, grouped och configurable) inte uppdateras när delproduktens lagerstatus ändras via REST API-POSTEN /rest/V1/lager/source-items.
* **ACSD-47336** (för Adobe Commerce och Magento Open Source >=2.4.0 &lt;2.4.6) - Korrigeringar *Något gick fel.* fel vid inaktivering av meddelanden i Commerce Admin.
* **ACSD-47559** (för Adobe Commerce och Magento Open Source >=2.4.0 &lt;2.4.6) - Korrigerar problemet där e-postmallen för förhandsgranskning inte är helt synlig.
* **ACSD-47920** (för Adobe Commerce och Magento Open Source >=2.4.0 &lt;2.4.6) - Korrigerar problemet där beställningar kan göras via Rest API som gästanvändare även när *Tillåt gästutcheckning* är avstängd.
* Ersatta patchar: MDVA-39305, MDVA-42855.

## v1.1.23 {#v1-1-23}

* **ACSD-47179** (för Adobe Commerce och Magento Open Source >=2.4.0 &lt;2.4.6) - Korrigerar problemet där en administratör med begränsad åtkomst till ett specifikt omfång inte kan ta bort produktrecensioner.
* **ACSD-47107** (för Adobe Commerce och Magento Open Source >=2.4.2 &lt;2.4.5) - Korrigerar problemet där rabatten på katalogprisregel tillämpas på anpassade produktalternativ.
* **ACSD-47232** (för Adobe Commerce och Magento Open Source >=2.4.0 &lt;2.4.6) - Korrigerar problemet där kuponger med totalviktsvillkor inte kan användas i administratören.
* **ACSD-46519** (för Adobe Commerce och Magento Open Source >=2.4.1 &lt;2.4.6) - Korrigerar problemet där GraphQL categoryList-begäran returnerar ett felaktigt product_count för en ankarkategori.
* **ACSD-47027** (för Adobe Commerce och Magento Open Source >=2.4.2 &lt;2.4.6) - Korrigerar en långsam updateCompanyRole GraphQL-begäran.
* **ACSD-47666** (för Adobe Commerce och Magento Open Source >=2.4.0 &lt;2.4.6) - Korrigerar problemet där filterfunktionen inte fungerar i Admin > System > Behörigheter > Användarroller > en roll > Rutnät för rollanvändare.
* **ACSD-47497** (för Adobe Commerce och Magento Open Source >=2.4.0 &lt;2.4.6) - Korrigerar problemet där fliken Tjänster inte visas i konfigurationen under Admin.
* Uppdaterad patch: ACSD-47743.
* Ersatta patchar: MDVA-42807.

## v1.1.22 {#v1-1-22}

* **ACSD-47444** (för Adobe Commerce och Magento Open Source >=2.4.0 &lt;2.4.3) - Korrigerar _Försöker få åtkomst till matrisförskjutning på värde av typen bool_ fel vid åtkomst till vissa kategorisökvägar som inte finns för kända produkter i PHP 7.4.
* **ACSD-47332** (för Adobe Commerce och Magento Open Source >=2.4.0 &lt;2.4.6) - Korrigerar problemet där kron inte fungerar med ett fel som bara rapporteras när den körs mellan 00:00 och 00:59 UTC.
* **ACSD-47280** (för Adobe Commerce och Magento Open Source >=2.4.0 &lt;2.4.6) - Korrigerar problemet där inaktivering av den delade katalogfunktionen i ett specifikt omfång inte fungerar korrekt.
* **ACSD-47106** (för Adobe Commerce och Magento Open Source >=2.4.4 &lt;2.4.6) - Korrigerar problemet där ett värde inte kan sparas i ett nytt anpassat attribut på en företagsskapandesida.
* Uppdaterad patch: ACSD-45143.

## v1.1.21 {#v1-1-21}

* **ACSD-46809** (för Adobe Commerce och Magento Open Source >=2.4.2 &lt;2.4.6) - Korrigerar problemet där en användare får ett fel när de tilldelar ett stort antal produktkällor.
* **ACSD-46856** (för Adobe Commerce och Magento Open Source >=2.4.0 &lt;2.4.6) - Förbättrar prestanda genom att uppdatera nivåpriser via System > Konfiguration > Importera > Avancerade priser.
* **ACSD-46541** (för Adobe Commerce och Magento Open Source >=2.4.0 &lt;2.4.4) - Korrigerar problemet där en administratörsanvändare inte kan skapa en kreditnota om ett orderobjekt tas bort.
* **ACSD-46581** (för Adobe Commerce och Magento Open Source >=2.4.0 &lt;2.4.6) - Korrigerar problemet där den beräknade momssumman inte uppdateras efter att du har valt ett land i kundvagnen.
* **ACSD-46618** (för Adobe Commerce och Magento Open Source >=2.4.0 &lt;2.4.6) - Korrigerar problemet där produktlistwidgeten visar felaktiga cachelagrade priser för en inloggad kund.
* **ACSD-46674** (för Adobe Commerce och Magento Open Source >=2.4.0 &lt;2.4.6) - Korrigerar problemet där anpassade alternativ för en bildtyp visas som HTML i kundens e-postmeddelanden.
* **ACSD-46988** (för Adobe Commerce och Magento Open Source >=2.4.4 &lt;2.4.6) - Korrigerar problemet där API-begäran GraphQL &#39;currency&#39; returnerar NULL-värden för en anpassad valuta.
* **ACSD-47076** (för Adobe Commerce och Magento Open Source >=2.4.1 &lt;2.4.5) - Korrigerar problemet där Vimeo-videor inte kan spelas upp i butiken.
* **ACSD-45071** (för Adobe Commerce och Magento Open Source >=2.4.2 &lt;2.4.4) - Korrigerar problemet där standardkällan läggs till i produkten under importen.
* **AC-3023** (för Adobe Commerce och Magento Open Source >=2.4.0 &lt;2.4.6) - Uppdatera DHL-schemat till den senaste versionen, 10.0.
* Uppdaterade patchar: MDVA-42584.
* Ersatta patchar: MDVA-36572, ACSD-45241.

## v1.1.20 {#v1-1-20}

* **ACSD-46520** (*för Adobe Commerce och Magento Open Source >=2.4.0 &lt;2.4.5*) - Korrigerar problemet där en användare får en felaktig orderstatus när de återbetalas med butikskrediten.
* **ACSD-46703** (*för Adobe Commerce och Magento Open Source >=2.4.4 &lt;2.4.6*) - Korrigerar problemet där det inte går att dra och släppa anpassade alternativ på en produktredigeringssida.
* **ACSD-44851** (*för Adobe Commerce och Magento Open Source >=2.4.0 &lt;2.4.6*) - Korrigerar problemet där en kategori med underkategorier inte kan öppnas eller expanderas.
* **ACSD-46815** (*för Adobe Commerce och Magento Open Source >=2.4.5 &lt;2.4.6*) - Korrigerar problemet där kategoriträdets begäran är begränsad till 20 kategorier.
* **ACSD-45675** (*för Adobe Commerce och Magento Open Source >=2.4.0 &lt;2.4.6*) - Korrigerar problemet där produktexporten använder kategorinamn från *Standardbutiksvy* omfång.
* **ACSD-46869** (*för Adobe Commerce och Magento Open Source >=2.4.4 &lt;2.4.6*) - Korrigerar problemet där en konfigurerbar produkt i en kundvagn inte uppdateras via en *PUT REST API* begära utan att ändra produktkvantiteten.
* **MDVA-42768-V2** (*för Adobe Commerce och Magento Open Source >=2.4.2 &lt;2.4.3*) - Korrigerar problemet där den konfigurerbara produkten visar det normala priset som *0* när *Visa ej lagrad* är *Ja*.
* Uppdaterade patchar: MDVA-44562, ACSD-46213, MDVA-41305, MDVA-38346, MDVA-13203.
* Föråldrad korrigering: MDVA-42768.

## v1.1.19 {#v1-1-19}

* **ACSD-46213** (*för Adobe Commerce och Magento Open Source >=2.4.2 &lt;2.4.3*) - Korrigerar problemet där kategoriträdets begäran är begränsad till 20 kategorier.
* **ACSD-45781** (*för Adobe Commerce och Magento Open Source >=2.4.1 &lt;2.4.2*) - Korrigerar problemet där sökfältet längst fram i butiken inte visas på mobilen.
* **ACSD-46192** (*för Adobe Commerce och Magento Open Source >=2.3.6 &lt;2.4.5*) - Åtgärdar problemet med att använda `async/bulk/V1/configurable-products/bySku/options` slutpunkt.
* **ACSD-46404** (*för Adobe Commerce och Magento Open Source >=2.4.4 &lt;2.4.5*) - Korrigerar problemet där en administratörsanvändare inte kan logga in efter uppgradering till 2.4.4.
* Uppdaterade patchar: MDVA-41305, MDVA-38626, MDVA-38728, MDVA-41061-V4, MDVA-42269, MDVA-39305.

## v1.1.18 {#v1-1-18}

* **ACSD-45817** (*för Adobe Commerce och Magento Open Source >=2.4.2 &lt;2.4.4*) - Korrigerar problemet där en GraphQL-produktmutation för en viss butik returnerar alla konfigurerbara varianter, inklusive de som inte tilldelats den begärda butiken.
* **ACSD-46146** (*för Adobe Commerce och Magento Open Source >=2.3.0 &lt;2.4.6*) - Korrigerar problemet där två e-postmeddelanden med orderbekräftelse skickas efter att en beställning har gjorts från administratören.
* **ACSD-45255** (*för Adobe Commerce >=2.4.3 &lt;2.4.6*) - Korrigerar ett undantag på rapportsidan LågStock för en begränsad administratörsanvändare.
* **ACSD-45488** (*för Adobe Commerce och Magento Open Source >=2.4.2 &lt;2.4.6*) - Korrigerar problemet där en konfigurerbar produkt med flera källor inte returneras till In Stock automatiskt.
* **ACSD-45754** (*för Adobe Commerce och Magento Open Source >=2.3.1 &lt;2.4.6*) - Korrigerar problemet där belöningspoäng inte läggs till efter att en kupong använts i kundvagnen.
* **ACSD-45849** (*för Adobe Commerce >=2.4.3 &lt;2.4.4*) - Korrigerar problemet där videometadata förloras efter att en mellanlagringsuppdatering har tillämpats.
* **ACSD-45257** (*för Adobe Commerce och Magento Open Source >=2.3.4 &lt;2.4.4*) - Korrigerar problemet där GraphQL inte visar en kundvagnsrabatt korrekt.
* **ACSD-44938** (*för Adobe Commerce och Magento Open Source >=2.4.0 &lt;2.4.4*) - Åtgärdar problemet där `VAT_ID` kan inte användas i en GraphQL-begäran för en gästanvändare.
* Uppdaterade patchar: MDVA-43417.

## v1.1.17 {#v1-1-17}

* **ACSD-45241** (*för Adobe Commerce och Magento Open Source >=2.3.5 &lt;2.4.4*) - Korrigerar problemet där lagerkvantiteten för en virtuell produkt inte beräknas korrekt efter att en kreditnota har skapats.
* **ACSD-43887** (*för Adobe Commerce och Magento Open Source >=2.4.2 &lt;2.4.5*) - Korrigerar problemet där felaktiga detaljer visas på betalningssidan i kassan när inköpsorder för företag är aktiverade.
* **ACSD-45143** (*för Adobe Commerce och Magento Open Source >=2.4.0 &lt;2.4.5*) - Korrigerar problemet där `setShippingAddressesOnCart` mutation tillåter inte att numerisk regionkod anges som *region*.
* **ACSD-44591** (*för Adobe Commerce och Magento Open Source >=2.4.3 &lt;2.4.6*) - Korrigerar felet som inträffar när en order placeras utan CAPTCHA-bekräftelse.
* **ACSD-45520** (*för Adobe Commerce och Magento Open Source >=2.3.0 &lt;2.4.6*) - Korrigerar problemet där färgrutealternativen inte är förvalda på produktinformationssidan när en användare redigerar konfigurerbara produkter från kundvagnen.
* **ACSD-45169** (*för Adobe Commerce och Magento Open Source >=2.4.1 &lt;2.4.6*) - Åtgärdar problemet där [!DNL Visual Merchandiser] visar inte korrekt lager och pris för en konfigurerbar produkt efter att en mellanlagringsuppdatering har tillämpats.
* **ACSD-45424** (*för Adobe Commerce och Magento Open Source >=2.3.4 &lt;2.4.6*) - Korrigerar problemet där en felaktig reservationskompensation skapas efter en partiell återbetalning (kreditnota).
* **MDVA-42807** (*för Adobe Commerce och Magento Open Source >=2.3.1 &lt;2.4.6*) - Korrigerar problemet där den anpassade valutasymbolen inte visas på butikens framsida.
* Uppdaterade patchar: MDVA-42689, AC-3022.

## v1.1.16 {#v1-1-16}

* **MDVA-44703** (*för Adobe Commerce och Magento Open Source >=2.4.3 &lt;2.4.4*) - Korrigerar problemet där ordersummor i orderrapporten inte beräknas korrekt för den begränsade administratörsanvändaren.
* **MDVA-44940** (*för Adobe Commerce och Magento Open Source >=2.4.3 &lt;2.4.4*) - Korrigerar det SQL-fel som inträffar när kategorin sparas från Admin.
* **MDVA-44562** (*för Adobe Commerce och Magento Open Source >=2.4.0 &lt;2.4.2-p2*) - Korrigerar problemet där det icke-förvalda arkiv-ID:t för offertobjekt åsidosätts av standardarkiv-ID:t, trots GraphQL-begäran som kommer från den icke-standardbutiksvyn.
* **MDVA-43167** (*för Adobe Commerce och Magento Open Source >=2.4.2 &lt;2.4.4*) - Korrigerar problemet där massåtgärden för administratörsorderraster inte gäller för flersidiga dokument när administratören väljer alla order.
* **MDVA-44044** (*för Adobe Commerce och Magento Open Source >=2.3.0 &lt;2.4.2-p2*) - Korrigerar problemet där en produkt inte visas på kategorisidan efter att den har tilldelats till en ny webbplats.
* **MDVA-42509** (*för Adobe Commerce och Magento Open Source >=2.3.3 &lt;2.4.4*) - Korrigerar problemet där en CSV-fil inte kunde överföras för en snabborder som resulterade i ett *Det går inte att skicka cookien* fel.
* Uppdaterade patchar: MDVA-41061, MDVA-42584.
* Prefixet för den nya [!DNL Quality Patches Tool] korrigeringar ändras från *MDVA* till *ACSD* på grund av interna processändringar.

## v1.1.15 {#v1-1-15}

* **MDVA-40961** (*för Adobe Commerce och Magento Open Source >=2.4.3 &lt;2.4.4*) - Korrigerar problemet där en ytterligare artikel inte kan läggas till i vagnen när artikelns minsta kvantitet redan finns i vagnen.
* **MDVA-44887** (*för Adobe Commerce och Magento Open Source >=2.4.4 &lt;2.4.5*) - Korrigerar *Ohanterat SyntaxError: Oväntad token &#39;const&#39;* fel på panelen Admin.
* **MDVA-43718** (*för Adobe Commerce och Magento Open Source >=2.3.0 &lt;2.4.5*) - Korrigeringar *Konsumenten har inte behörighet att komma åt %resources.* fel som visas vid åtkomst till en delad katalog från en anpassad integrering.
* **MDVA-44660** (*för Adobe Commerce och Magento Open Source >=2.4.2-p1 &lt;2.4.5*) - Korrigerar problemet där det grav accenttecknet ``` ` ``` kunde inte användas för en kunds för- och efternamn.
* **MDVA-40896** (*för Adobe Commerce och Magento Open Source >=2.4.3 &lt;2.4.4*) - Korrigerar *Fel: TypeError: Argument 3 har skickats till Magento* fel i asynkron produkt bulk-API.
* **MDVA-38559** (*för Adobe Commerce och Magento Open Source >=2.4.0 &lt;2.4.3*) - Korrigerar */V1/customers/search API* fel för kunder med mer än en prenumeration.
* **MDVA-44533** (*för Adobe Commerce och Magento Open Source >=2.3.1 &lt;2.4.4*) - Korrigerar problemet där rabatten felaktigt tillämpas på en underordnad paketprodukt.
* Uppdaterade patchar: MDVA-41061, MDVA-42269.

## v1.1.14 {#v1-1-14}

* **MDVA-43983** (*för Adobe Commerce och Magento Open Source >=2.4.2 &lt;2.4.5*) - Åtgärdar problemet där produkter *Inte synlig enskilt* visas fortfarande i katalogernas avancerade sökresultat.
* **MDVA-44100** (*för Adobe Commerce och Magento Open Source >=2.4.3 &lt;2.4.5*) - Korrigerar problemet där alla bildrutefrekvenser för bildrutefrekvens tilldelas den sista produkten i kundvagnen och återställs för andra produkter.
* **MDVA-43605** (*för Adobe Commerce och Magento Open Source >=2.3.1 &lt;2.4.5*) - Korrigerar problemet där orderdata returnerar negativa värden för radsummor när Rest API används.
* **MDVA-43102** (*för Adobe Commerce och Magento Open Source >=2.3.1 &lt;2.4.5*) - Korrigerar problemet där den försäljningsbara kvantiteten inte uppdateras korrekt när en återbetalning görs via REST API.
* **MDVA-43178** (*för Adobe Commerce och Magento Open Source >=2.4.3-p2 &lt;2.4.5*) - Korrigerar problemet där en kundtoken för en anpassad butik inte kan hämtas i GraphQL.
* **MDVA-43859** (*för Adobe Commerce och Magento Open Source >=2.4.1 &lt;2.4.5*) - Åtgärdar problemet där felet *Ingen sådan enhet med customerId =* loggas när en borttagen kund försöker logga in.
* **MDVA-44147** (*för Adobe Commerce och Magento Open Source >=2.4.2 &lt;2.4.5*) - Korrigerar problemet där en GraphQL-begäran inte returnerar rekvisitionslistor.
* **MDVA-44505** (*för Adobe Commerce och Magento Open Source >=2.4.1 &lt;2.4.3*) - Åtgärdar problem där GraphQL Tillämpar belöningspunkter inte uppdaterar totalsumman och där butikskrediten tillämpas flera gånger under orderplaceringen.
* Uppdaterade patchar: MDVA-29148, MDVA-36464-V5, MDVA-42584, MDVA-39993-V2.

## v1.1.13 {#v1-1-13}

* **MDVA-42969** (*för Adobe Commerce och Magento Open Source >=2.4.1 &lt;2.4.3*) - Korrigerar problemet där den relaterade produktregeln endast fungerar när kundsegmentet är inställt på *Alla*.
* **MDVA-39605** (*för Adobe Commerce och Magento Open Source >=2.3.4 &lt;2.4.5*) - Korrigerar problemet där Redis cache TTL (förfallodatum) har ett felaktigt värde.
* **MDVA-43862** (*för Adobe Commerce och Magento Open Source >=2.3.3 &lt;2.4.5*) - Korrigerar problemet där kunden inte kan uppdatera kundvagnsartiklar på grund av en GraphQL *UpdateCartItems-mutation* fel.
* **MDVA-43824** (*för Adobe Commerce och Magento Open Source >=2.3.6 &lt;=2.3.7-p3 || >=2.4.1 &lt;2.4.5*) - Korrigerar problemet där ett fel uppstår vid annullering av order med rabatt.
* **MDVA-43451** (*för Adobe Commerce och Magento Open Source >=2.4.3 &lt;2.4.5*) - Åtgärdar problemet där felet *Det gick inte att hitta det begärda arkivet. Kontrollera butiken och försök igen.* visas när du konfigurerar en delad katalog för en viss webbplats.
* **MDVA-43491** (*för Adobe Commerce och Magento Open Source >=2.3.5 &lt;2.4.5*) - Korrigerar problemet där basbildetiketten inte uppdateras vid import av produkter till en webbplats för flera butiker.
* **MDVA-43601** (*för Adobe Commerce och Magento Open Source >=2.3.0 &lt;2.4.5*) - Korrigerar problemet med saknade utlösare efter fullständig omindexering.
* **MDVA-42046** (*för Adobe Commerce och Magento Open Source >=2.3.4 &lt;=2.3.5-p2 || >=2.4.0 &lt;2.4.5*) - Korrigerar problemet där ett felaktigt värde tilldelas ett produktattribut med ett datuminmatningsfält när en produkt uppdateras.
* **MDVA-43935** (*för Adobe Commerce och Magento Open Source >=2.4.1 &lt;2.4.5*) - Korrigerar problemet där merförsäljning visas två gånger.
* **MDVA-44188** (*för Adobe Commerce och Magento Open Source >=2.4.3 &lt;2.4.5*) - Korrigerar problemet där systemutfärdade e-postmeddelanden med `.-` i adresser skickas inte.
* **MDVA-42283** (*för Adobe Commerce och Magento Open Source >=2.3.0 &lt;2.4.5*) - Korrigerar problemet där datum- och tidsformatet i administrationsorderrutnätet för franska är ogiltigt.
* Uppdaterade patchar: MDVA-41061-V2, MDVA-36309, MDVA-30862, MDVA-39713.
* Lagt till metadata för korrigeringsfiler för [!DNL Site-Wide Analysis Tool].

## v1.1.12 {#v1-1-12}

* **MDVA-39713** (*för Adobe Commerce och Magento Open Source >=2.3.0 &lt;2.3.6*) - Korrigerar problemet där användaren kan redigera starttiden för en aktiv schemalagd uppdatering.
* **MDVA-42410** (*för Adobe Commerce och Magento Open Source >=2.3.0 &lt;2.4.5*) - Korrigerar problemet där kupongrapporter endast visar standardbasvalutan.
* **MDVA-41136** (*för Adobe Commerce och Magento Open Source >=2.3.0 &lt;2.4.5*) - Korrigerar problemet där utgångsdatumet för `mage-cache-sessid` utökas inte, vilket resulterar i rensning av kunddata.
* **MDVA-39993** (*för Adobe Commerce och Magento Open Source >=2.3.5 &lt;=2.3.7-p2 || >=2.4.0 &lt;2.4.4*) - Korrigerar problemet där lagerändringar som gjorts via API inte återspeglas på produktsidan i klientdelen.
* **MDVA-42855** (*för Adobe Commerce och Magento Open Source >=2.4.3 &lt;2.4.5*) - Korrigerar problemet där en ny kundadress inte sparas i adressboken under utcheckningen.
* **MDVA-42645** (*för Adobe Commerce och Magento Open Source >=2.4.3 &lt;2.4.5*) - Korrigerar problemet där administratören inte kan återbetala belöningspoäng om butikskreditfunktionen är inaktiverad.
* **MDVA-43414** (*för Adobe Commerce och Magento Open Source >=2.3.6 &lt;=2.3.7-p2*) - Korrigerar det allvarliga PHP-fel som inträffar när `inventory.reservations.updateSalabilityStatus` kökonsument på numeriska SKU:er.
* **MDVA-41628** (*för Adobe Commerce och Magento Open Source >=2.4.0 &lt;2.4.5*) - Korrigerar problemet där befintliga begränsade administratörsanvändare får åtkomst till de nya resurserna när nya moduler läggs till.
* **MDVA-43348** (*för Adobe Commerce och Magento Open Source >=2.4.2 &lt;2.4.5*) - Korrigerar problemet där GraphQL-begäran för presentkort visar ett fel om `gift_card_options` innehåller *uid*.
* **MDVA-39546** (*för Adobe Commerce och Magento Open Source >=2.3.0 &lt;2.4.5*) - Korrigerar problemet där startdatumet för mellanlagringsuppdateringen kan anges till ett tidigare datum än det aktuella datumet under redigeringen.
* **MDVA-42950** (*för Adobe Commerce och Magento Open Source >=2.3.0 &lt;2.4.5*) - Korrigerar problemet där videoklipp inte spelas upp på produktsidan.
* **MDVA-42689** (*för Adobe Commerce och Magento Open Source >=2.3.0 &lt;2.4.4*) - Korrigerar problemet där Adobe Commerce orsakar en *Överträdelse av integritetsbegränsning* fel vid uppdatering av produktkategorier under import.
* **MDVA-41229** (*för Adobe Commerce och Magento Open Source >=2.3.0 &lt;2.4.5*) - Korrigerar problemet där bilder som finns på baksidan inte visas på framsidan efter att konfigurerbara produkter har importerats.
* **MDVA-43731** (*för Adobe Commerce och Magento Open Source >=2.4.3 &lt;2.4.4*) - Åtgärdar problemet där *Sök efter synonymer* fungerar inte längre när ett värde läggs till i *Minimivillkor att matcha*.
* **MDVA-43232** (*för Adobe Commerce och Magento Open Source >=2.3.4 &lt;2.4.5*) - Korrigerar problemet där sortering av produkter i [!DNL Visual Merchandiser] efter specialpris längst ned/högst upp uppstår ett fel när kategorin sparas.
* **MDVA-43726** (*för Adobe Commerce och Magento Open Source >=2.3.3 &lt;2.4.3*) - Korrigerar problemet där katalogprisregeln som baseras på butiksattributmatchning inte kan tillämpas efter partiell omindexering.
* Uppdaterade patchar: MDVA-36464, MDVA-37478, MDVA-38608.
* Lagt till metadata för korrigeringsfiler för [!DNL Site-Wide Analysis Tool].

## v1.1.11 {#v1-1-11}

* **MDVA-42790** (*för Adobe Commerce och Magento Open Source >=2.4.3 &lt;2.4.5*) - Korrigerar problemet där produktprisattribut inte kan uppdateras för en specifik webbplats via REST API.
* **MDVA-41350** (*för Adobe Commerce och Magento Open Source >=2.3.0 &lt;2.4.5*) - Korrigerar problemet där ett undantag inträffar när en administratörsanvändare med begränsad åtkomst lägger till en produkt utanför sin rollomfång av SKU i en ordning.
* **MDVA-42269** (*för Adobe Commerce och Magento Open Source >=2.4.3-p1 &lt;2.4.5*) - Korrigerar problemet där en administratörsanvändare inte kan logga in på administratören på grund av *TypeError: strtotime() förväntar att parameter 1 ska vara sträng, null angiven* fel.
* **MDVA-40830** (*för Adobe Commerce och Magento Open Source >=2.3.0 &lt;2.4.5*) - Korrigerar problemet där butikskrediten tillämpas flera gånger under orderplacering.
* **MDVA-42237** (*för Adobe Commerce och Magento Open Source >=2.4.2 &lt;2.4.5*) - Korrigerar problemet där ett specialpris för en konfigurerbar produkt inte uppdateras efter ändringar av dess underproduktspris.
* **MDVA-42520** (*för Adobe Commerce och Magento Open Source >=2.4.3 &lt;2.4.4*) - Korrigerar problemet där momssatsen tillämpas två gånger om *Aktivera gränsöverskridande handel* används.
* Uppdaterade patchar: MDVA-27239, MDVA-39305, MDVA-41236, MDVA-36832.
* Föråldrad korrigering: MDVA-37725.

## v1.1.10 {#v1-1-10}

* **MDVA-38728** (*för Adobe Commerce och Magento Open Source >=2.3.2 &lt;2.4.5*) - Korrigerar problemet där massattributsuppdatering skapar URL-omskrivning för standardlagring endast efter ändring *Produktsynlighet*.
* **MDVA-43091** (*för Adobe Commerce och Magento Open Source >=2.4.3 &lt;2.4.4*) - Korrigerar problemet där beställning av en paketprodukt från administratören i serverdelen ger felet *Du kan inte använda decimalkvantitet för den här produkten*.
* **MDVA-40816** (*för Adobe Commerce och Magento Open Source >=2.3.0 &lt;2.4.5*) - Korrigerar problemet där relaterade produktregler visar produkter från kategorier som inte definierats i regelvillkoren.
* **MDVA-41305** (*för Adobe Commerce och Magento Open Source >=2.4.2 &lt;2.4.5*) - Korrigerar problemet där GraphQL-mutationen inte returnerar konfigurerbara produktalternativ när den har lagts till i önskelistan.
* **MDVA-39181** (*för Adobe Commerce och Magento Open Source >=2.4.1 &lt;2.4.5*) - Korrigerar problemet där relaterade produktregler visar produkter från kategorier som inte definierats i regelvillkoren.
* **MDVA-42584** (*för Adobe Commerce och Magento Open Source >=2.4.2 &lt;2.4.3*) - Korrigerar problemet där konfigurerbar lagerstatus i serverdelen inte uppdateras efter att kvantitet och lagerstatus har ändrats via Import eller API.
* **MDVA-40175** (*för Adobe Commerce och Magento Open Source >=2.4.0 &lt;2.4.3*) - Åtgärdar problemet där *Klicka för att ändra leveranssätt* I visas inte alternativknappar för att välja leveransmetoder i Admin vid omsortering.
* **MDVA-42768** (*för Adobe Commerce och Magento Open Source >=2.3.4 &lt;2.4.5*) - Korrigerar problemet där den konfigurerbara produkten visar det normala priset som 0 när *Visa ej lagrad* Ja.
* **MDVA-43201** (*för Adobe Commerce och Magento Open Source >=2.4.2 &lt;2.4.4*) - Korrigerar problemet där ett fel inträffar vid kundinloggning när DOB-attribut används med vissa språkinställningar.
* Uppdaterade patchar: MDVA-35092, MDVA-33970.

## v1.1.9 {#v1-1-9}

* **MDVA-38346** (*för Adobe Commerce och Magento Open Source >=2.3.0 &lt;2.4.5*) - Korrigerar problemet där datumfilter inte fungerar som de ska när Adobe Commerce tidszon skiljer sig från den lokala miljöns tidszon.
* **MDVA-42657** (*för Adobe Commerce och Magento Open Source >=2.4.1 &lt;2.4.5*) - Korrigerar problemet där administratörsanvändaren inte kan välja kategorier i kundsegmentsvillkoren.
* **MDVA-42806** (*för Adobe Commerce och Magento Open Source >=2.4.2 &lt;2.4.4*) - Åtgärdar problemet där *Ny företagsregistrering* e-post skickas varje gång ett befintligt företag uppdateras via REST API.
* **MDVA-37984** (*för Adobe Commerce och Magento Open Source >=2.4.1 &lt;2.4.5*) - Korrigerar problemet där [!DNL Visual Merchandiser] *Matcha produkt efter regel* -funktionen filtrerar inte produkter korrekt med mellanlagringsuppdateringar.
* **MDVA-40488** (*för Adobe Commerce och Magento Open Source >=2.4.2 &lt;2.4.4*) - Korrigerar problemet där konfigurerbara produkter med underordnade produkter utanför lagret inte visas i rätt prisintervall.
* **MDVA-42507** (*för Adobe Commerce och Magento Open Source >=2.4.3 &lt;2.4.5*) - Korrigerar problemet där helsidescachen rensas efter att en mellanlagringsuppdatering har tillämpats för kundvagnsregeln.
* **MDVA-39163** (*för Adobe Commerce och Magento Open Source >=2.3.5 &lt;2.4.5*) - Korrigerar problemet där leveransmetoder inte är tillgängliga när en ny användare registreras och produkter i kundvagnen kommer från gästsessionen.
* **MDVA-38626** (*för Adobe Commerce och Magento Open Source >=2.3.3 &lt;2.4.5*) - Korrigerar problemet där administratörsanvändaren inte kan lägga en order på backend-objektet med [!DNL PayPal Payflow Pro] betalning.
* **MDVA-38666** (*för Adobe Commerce och Magento Open Source >=2.3.2 &lt;2.3.6*) - Korrigerar problemet där administratörsanvändaren inte kan ändra de konfigurerbara produktalternativen i kundvagnen.
* **MDVA-38526** (*för Adobe Commerce och Magento Open Source >=2.4.1 &lt;2.4.4*) - Korrigerar problemet där administratörsanvändaren inte har åtkomst till [!DNL Site-Wide Analysis tool].
* Uppdaterade patchar: MDVA-40101.

## v1.1.8 {#v1-1-8}

* **MDVA-41215** (*för Adobe Commerce och Magento Open Source >=2.3.0 &lt;2.4.4*) - Korrigerar problemet där användaren får felmeddelandet 500 efter att ha ställt in *bildmeddelanden* cookie om den redan finns, men det finns inga nya meddelanden.
* **MDVA-41139** (*för Adobe Commerce och Magento Open Source >=2.4.3 &lt;2.4.4*) - Korrigerar problemet där konfigurerbara produkter blir utanför lagret efter produktimport när en enkel produkts kvantitet=0 för en av dess källor.
* **MDVA-42326** (*för Adobe Commerce och Magento Open Source >=2.3.6 &lt;=2.3.7-p2 || >=2.4.1 &lt;2.4.4*) - Korrigerar problemet där kunderna får ett felmeddelande vid utcheckning efter en sessionstimeout även om den beständiga kundvagnen är aktiverad.
* **MDVA-42341** (*för Adobe Commerce och Magento Open Source >=2.4.2 &lt;2.4.4*) - Korrigerar problemet där `categoryList` GraphQL-frågan filtrerar inte resultat om en begäran har Store-rubriken.
* **MDVA-38393** (*för Adobe Commerce och Magento Open Source >=2.3.0 &lt;2.4.4*) - Korrigerar problemet där katalogregler slutar att fungera för en konfigurerbar produkt om den enkla produkten får ett nytt namn.
* **MDVA-39153** (*för Adobe Commerce och Magento Open Source >=2.4.2 &lt;2.4.4*) - Korrigerar problemet där ett rabattbelopp beräknas felaktigt under omsorteringen i Admin.
* Uppdaterade patchar: MDVA-28993, MDVA-41061, MDVA-35984.

## v1.1.7 {#v1-1-7}

* **MDVA-39711** (*för Adobe Commerce och Magento Open Source >=2.3.0 &lt;2.4.3*) - Korrigerar problemet där administratörsanvändare inte kan komma åt kundens rutnät efter att webbplatsen har tagits bort.
* **MDVA-40311** (*för Adobe Commerce och Magento Open Source >=2.4.2-p2 &lt;2.4.4*) - Korrigerar problemet där administratörsanvändare får felmeddelandet *Ogiltig säkerhets- eller formulärnyckel. Uppdatera sidan* efter inloggning på administratören om den anpassade administratörssökvägen är konfigurerad och den hemliga nyckeln är aktiverad.
* **MDVA-41631** (*för Adobe Commerce och Magento Open Source >=2.4.1 &lt;2.4.4*) - Korrigerar problemet där användare får ett fel vid försök att hämta orderinformation utan ett valfritt *telefon* värde via GraphQL.
* **MDVA-27239** (*för Adobe Commerce och Magento Open Source >=2.3.0 &lt;2.3.6*) - Korrigerar problemet där korsförsäljningsprodukter inte visas.
* Uppdaterade patchar: MDVA-37068, MDVA-35254, MDVA-41164, MDVA-37916, MDVA-37478, MDVA-34551, MDVA-31791.

## v1.1.6 {#v1-1-6}

* **MDVA-40550** (*för Adobe Commerce och Magento Open Source >=2.3.5 &lt;2.4.4*) - Korrigerar problemet med saknade produkter på klientsidan vid omindexering.
* **MDVA-40120** (*för Adobe Commerce och Magento Open Source >=2.4.1 &lt;2.4.4*) - Korrigerar problemet där GraphQL sortering efter DESC/ASC inte fungerar med produkter med samma relevans eller pris.
* **MDVA-41399** (*för Adobe Commerce och Magento Open Source >=2.3.3 &lt;2.4.2*) - Korrigerar problemet där administratörsanvändare inte har åtkomst till *Hantera kundvagn* om en kund lägger till en produkt i önskelistan.
* **MDVA-40609** (*för Adobe Commerce och Magento Open Source >=2.4.2 &lt;2.4.3*) - Korrigerar problemet där inaktiverade produktdata saknas i `cataloginventory_stock_status` indextabell, visa felaktiga inaktiverade produktkvantiteter.
* **MDVA-39031** (*för Adobe Commerce och Magento Open Source >=2.4.1 &lt;2.4.4*) - Korrigerar problemet där det är möjligt att lägga till en produkt i kundvagnen via GraphQL även om den inte har tilldelats till målwebbplatsen.
* **MDVA-41597** (*för Adobe Commerce och Magento Open Source >=2.4.2 &lt;2.4.4*) - Korrigerar problemet där användare får ett fel när de lägger till mer än en konfigurerbar produkt i kundvagnen med GraphQL.
* **MDVA-27456** (*för Adobe Commerce och Magento Open Source >=2.3.5 &lt;2.3.7*) - Korrigerar problemet där användare får ett fel när de försöker läsa in [!DNL Swagger].
* **MDVA-32776** (*för Adobe Commerce och Magento Open Source >=2.4.0 &lt;2.4.2*) - Korrigerar problemet där lagerstatus inte uppdateras när en order placeras men inte skickas.
* **MDVA-30862** (*för Adobe Commerce och Magento Open Source >=2.3.4 &lt;2.4.0*) - Korrigerar problemet med fel orderdatum på den utskrivna PDF-fakturan.
* Förbättrad indexsida för [!DNL Quality Patch Tool]. Lagt till smidig sökning och filtrering för [!DNL quality patches] den senaste versionen av verktyget.
* Uppdaterade patchar: MDVA-33382, MDVA-39482.

## v1.1.5 {#v1-1-5}

* **MDVA-41236** (*för Adobe Commerce och Magento Open Source >=2.3.0 &lt;2.4.4*) - Korrigerar problemet där det är omöjligt att skapa en ny eller redigera en befintlig schemalagd uppdatering för en produkt om slutdatumet har tagits bort tidigare.
* **MDVA-41046** (*för Adobe Commerce och Magento Open Source >=2.3.0 &lt;2.4.4*) - Korrigerar problemet där enkla produkter med anpassade alternativ är tillgängliga för tilldelning till konfigurerbara/grupperade produkter.
* **MDVA-40545** (*för Adobe Commerce och Magento Open Source >=2.3.0 &lt;2.4.4*) - Korrigerar problemet där bara den första noden för en sida hämtades, även om det fanns mer än en nod för samma sida.
* **MDVA-41164** (*för Adobe Commerce och Magento Open Source >=2.4.2 &lt;2.4.3-p1*) - Korrigerar problemet där en administratörsanvändare inte kan spara eller redigera ett företag med ett anpassat kundattribut för fil- eller bildtyp.
* **MDVA-39229** (*för Adobe Commerce och Magento Open Source >=2.3.0 &lt;2.4.4*) - Korrigerar problemet som orsakar att följande fel visas efter att starttiden för uppdatering av katalogregel för mellanlagring har uppdaterats: *Cron Job staging_synchronize_entities_period har ett fel: Det går inte att ta bort den aktiva uppdateringen.*
* **MDVA-40619** (*för Adobe Commerce och Magento Open Source >=2.3.0 &lt;2.4.4*) - Korrigerar problemet där ändringar i CMS-sidhierarkin orsakar ett 500-fel vid försök att göra infogad redigering på en CMS-sida.
* **MDVA-41061** (*för Adobe Commerce och Magento Open Source >=2.4.2 &lt;2.4.3*) - Korrigerar problemet där lagerstatus återställs till säljbar när en produkt sparas från administratören.
* **MDVA-31763** (*för Adobe Commerce och Magento Open Source >=2.3.0 &lt;2.4.4*) - Korrigerar problemet där katalogprisreglerna återställs (eller inte tillämpas) tills den manuella indexeringen görs om.
* **MDVA-37748** (*för Adobe Commerce och Magento Open Source >=2.4.2 &lt;2.4.3*) - Korrigerar problemet där en GraphQL-fråga returnerar produkter som inte är tilldelade till en delad katalog.

## v1.1.4 {#v1-1-4}

* **MDVA-40399** (*för Adobe Commerce och Magento Open Source >=2.4.2 &lt;2.4.4*) - Korrigerar problemet där partiella fakturor för samma order inte kan skapas samtidigt via REST API.
* **MDVA-40101** (*för Adobe Commerce och Magento Open Source >=2.3.2 &lt;2.4.0*) - Korrigerar problemet där artiklar inte tas bort från minivagnen efter en genomförd orderplacering med [!DNL PayPal Express] Checka ut.
* **MDVA-40401** (*för Adobe Commerce och Magento Open Source >=2.3.6 &lt;=2.3.7-p2 || >=2.4.1 &lt;2.4.4*) - Korrigerar problemet där kuponganvändningsvärdet ändras även om en beställning misslyckas.
* **MDVA-40537** (*för Adobe Commerce och Magento Open Source >=2.3.4 &lt;=2.4.0-p1*) - Korrigerar problemet där användare får ett fel när de skapar en butiksvy om det finns flera CMS-sidor med samma URL-nyckel.
* **MDVA-37725** (*för Adobe Commerce och Magento Open Source >=2.3.0 &lt;=2.4.3-p1*) - Korrigerar problemet där asynkrona e-postmeddelanden om beställningar som skickas från icke-standardwebbplatser innehåller logotyper-URL:er från standardwebbplatsen.
* **MDVA-39482** (*för Adobe Commerce och Magento Open Source >=2.3.6 &lt;=2.3.7-p2 || >=2.4.1 &lt;2.4.4*) - Korrigerar problemet där en produkt går ut ur lagret om den importeras med kvantiteten &quot;0&quot; när restorder är aktiverade.
* **MDVA-40435** (*för Adobe Commerce och Magento Open Source >=2.3.4 &lt;2.4.4*) - Åtgärdar problemet med felaktig rabatt på paketprodukter med dynamiska priser när de tillämpas via GraphQL.
* **MC-42528** (*för Adobe Commerce och Magento Open Source >=2.4.3 &lt;=2.4.3-p1*) - Korrigerar problemet där `categoryList` GraphQL-frågan returnerar både tilldelade och ej tilldelade kategorier.
* **MDVA-29400** (*för Adobe Commerce och Magento Open Source >=2.3.0 &lt;=2.3.7-p1 || >=2.4.0 &lt;=2.4.0-p1*) - Korrigerar problemet med duplicerade order som placerats med [!DNL PayPal Express Checkout].
* **MDVA-26005** (*för Adobe Commerce och Magento Open Source >=2.3.4 &lt;=2.3.5-p2*) - Korrigerar problemet där det inte går att välja en kategori i ett kategoriträd för villkor för kundprisregel.
* **MDVA-25631** (*för Adobe Commerce och Magento Open Source >=2.3.3 &lt;=2.3.5-p2*) - Förbättrar prestanda för att redigera och spara kundsegment som innehåller ett stort antal kunder.

## v1.1.3 {#v1-1-3}

* **MDVA-40262** (*för Adobe Commerce och Magento Open Source >=2.4.2 &lt;2.4.4*) - Korrigerar problemet där GraphQL sökfrågor inte visas i vanliga söktermer i Admin.
* **MDVA-40601** (*för Adobe Commerce och Magento Open Source >=2.3.1 &lt;=2.4.2-p2*) - Korrigerar problemet där användare får ett fel när de försöker få information om den kategori som ändrats av den schemalagda uppdateringen via GraphQL.
* **MDVA-37234** (*för Adobe Commerce och Magento Open Source >=2.3.5 &lt;2.4.0 || >=2.4.1 &lt;=2.4.2-p2*) - Korrigerar problemet där ett objekt läggs till i kundvagnen flera gånger (parallell begäran) för samma SKU skapar en dubblettradobjekt för samma kundvagn-ID.
* **MDVA-33606** (*för Adobe Commerce och Magento Open Source >=2.4.1 &lt;=2.4.2-p2*) - Korrigerar problemet där användarna får en *Unik begränsningsöverträdelse* fel när en CMS-sida som tilldelats en hierarki sparas.
* **MDVA-31590** (*för Adobe Commerce och Magento Open Source >=2.4.0 &lt;=2.4.1-p1*) - Korrigerar problemet där användare inte kan uppdatera attribut i grupp med hjälp av asynkrona MySQL-köer.
* **MDVA-36309** (*för Adobe Commerce och Magento Open Source >=2.4.2 &lt;=2.4.2-p2*) - Korrigerar problemet där produktsökning efter attribut är långsam i administratörsrutnätet.

## v1.1.2 {#v1-1-2}

* **MDVA-38929** (*för Adobe Commerce och Magento Open Source >=2.3.0 &lt;2.4.4*) - Korrigerar problemet där fakturan med FPT visar fel totalsumma när ordern betalas från butikskrediten.
* **MDVA-37364** (*för Adobe Commerce och Magento Open Source >=2.4.0 &lt;=2.4.3*) - Korrigerar problemet där det anpassade kundattributet av datumtyp bryter kundens rutnätsgränssnitt.
* **MDVA-39195** (*för Adobe Commerce och Magento Open Source >=2.4.2 &lt;=2.4.2-p2*) - Åtgärdar problemet där *Lägg i kundvagnen* Knappen var inaktiv på kategorisidan när omdirigering till kundvagnen är aktiverad.
* **MDVA-37115** (*för Adobe Commerce och Magento Open Source >=2.4.2 &lt;=2.4.2-p2*) - Korrigerar problemet där det inte behövs *Endast 0 kvar* visas på den konfigurerbara produktsidan.
* **MDVA-39521** (*för Adobe Commerce och Magento Open Source >=2.4.0 &lt;2.4.4*) - Korrigerar problemet där användaren inte kan ange leveransadresser i kundvagnen med ett tomt telefonnummer via GraphQL.
* **MDVA-39384** (*för Adobe Commerce och Magento Open Source >=2.3.1 &lt;=2.3.6 || >=2.4.1 &lt;=2.4.3*) - Korrigerar problemet där det anpassade kundattributet för en företagsanvändare inte sparas.
* **MDVA-39043** (*för Adobe Commerce och Magento Open Source >=2.3.4 &lt;=2.4.3*) - Korrigerar problemet där administratörsanvändaren med begränsad åtkomst får ett fel när han/hon försöker lägga till *Produkter* till CMS-sidan.
* **MDVA-39966** (*för Adobe Commerce och Magento Open Source >=2.3.0 &lt;=2.3.5-p2 || >=2.4.0 &lt;=2.4.0-p1*) - Åtgärdar problemet med att distribuera felaktiga språkområden.
* **MDVA-38852** (*för Adobe Commerce och Magento Open Source >=2.3.0 &lt;=2.3.5-p2*) - Korrigerar problemet där kataloginventeringen efter design låser tabeller för uppdateringar som avsevärt försämrar prestanda vid flera parallella order.
* **MDVA-39986** (*för Adobe Commerce och Magento Open Source >=2.4.1 &lt;2.4.3*) - Korrigerar problemet där användaren inte kan göra en beställning i Admin på MacOS med webbläsaren Safari.
* **MDVA-38447** (*för Adobe Commerce och Magento Open Source >=2.4.2 &lt;2.4.4*) - Korrigerar två problem: där *Inte synlig separat* konfigurerbara underordnade produkter returneras i GraphQL-svaret och optimera MySQL-frågan för GraphQL-produktfrågan med kategorifilter.
* **MDVA-40134** (*för Adobe Commerce och Magento Open Source >=2.4.2 &lt;2.4.3*) - Korrigerar problemet där GraphQL inte returnerar relaterade produkter när den delade katalogen är aktiverad.
* **MDVA-39935** (*för Adobe Commerce och Magento Open Source >=2.4.1 &lt;2.4.4*) - Korrigerar problemet där GraphQL returnerar konfigurerbara underordnade produkter som är inaktiverade på webbplatsnivå.

## v1.1.1 {#v1-1-1}

* **MDVA-36021** (*för Adobe Commerce och Magento Open Source >=2.4.0 &lt;2.4.4*) - Korrigerar problemet där *Anrop till medlemsfunktionen getId()* fel visas på sidan med orderinformation i Admin.
* **MDVA-34948** (*för Adobe Commerce och Magento Open Source >=2.3.6 &lt;=2.3.6-p1 || >=2.4.0 &lt;=2.4.0-p1*) - Åtgärdar problemet med långvariga frågor, som `GET_LOCK`.
* **MDVA-39305** (*för Adobe Commerce och Magento Open Source >=2.4.0 &lt;=2.4.2-p1*) - Korrigerar problemet där registrerade kunder inte kan logga in med aktiverade Google ReCaptcha.
* **MDVA-37897** (*för Adobe Commerce och Magento Open Source >=2.3.0 &lt;2.4.4*) - Korrigerar problemet med en felaktig omdirigering när en kund försöker lägga till produkter med alternativ från widgeten Senast visade.

## v1.1.0 {#v1-1-0}

* Korrigeringskategorierna introducerades för att förbättra användarupplevelsen och göra det enklare för kunderna att söka efter nödvändiga korrigeringsfiler.
* The `patches.json` filen har bytt namn till `support-patches.json`.
* **MDVA-38799** (*för Adobe Commerce >=2.3.0 &lt;2.4.3*) - Korrigerar problemet där hämtningsbara produkter inte sparades efter att en mellanlagringsuppdatering skapades.
* **MDVA-37592** (*för Adobe Commerce >=2.3.6 &lt;=2.4.2-p1*) - Korrigerar problemet när sortering efter pris inte fungerar korrekt för produkter med ett nollpris tilldelat den delade katalogen.
* **MDVA-38827** (*för Adobe Commerce >=2.3.3-p1 &lt;2.4.4*) - Korrigerar problemet där kunderna får ett e-postmeddelande med ett felmeddelande om orderleverans.

## v1.0.26 {#v1-0-26}

* **MDVA-38468** (*för Adobe Commerce >=2.3.2 &lt;=2.3.5-p2*) - Korrigerar felet när CMS-sidor sparas: *Det finns redan ett objekt med samma ID PAGE_ID*.
* **MDVA-34680** (*för Adobe Commerce >=2.3.6 &lt;=2.3.7 || >=2.4.1 &lt;2.4.3*) - Korrigerar problemet där kundkontots skapade tid inte filtreras korrekt i kundrutnätet.
* **MDVA-37068** (*för Adobe Commerce >=2.3.1 &lt;2.4.4*) - Korrigerar problemet där den felaktiga momssatsen visas när kundvagnen bara har virtuella produkter.
* **MDVA-38608** (*för Adobe Commerce >=2.3.0 &lt;2.4.3*) - Korrigerar problemet där temporära tabeller inte tas bort när omindexeringen inte slutförs korrekt.
* **MDVA-38308** (*för Adobe Commerce >=2.3.5 &lt;=2.3.6-p1 || >=2.4.0 &lt;=2.4.1-p1 || >=2.4.2 &lt;2.4.4*) - Korrigerar problemen med att lägga till [!DNL Vimeo] videor till produkterna.

## v1.0.25 {#v1-0-25}

* **MDVA-37916** (*för Adobe Commerce >=2.3.6 &lt;2.4.3*) - Korrigerar problemet där kunden inte kommer till sidan Betalningsbekräftelse när användaren använder [!DNL Paypal Payment Advanced] -metod.
* **MDVA-37082** (*för Adobe Commerce >=2.3.0 &lt;2.4.3*) - Korrigerar problemet när du sparar den anpassade versionen av grupperade produkter så att produkten inte finns i lager i förgrunden.
* **MDVA-36572** (*för Adobe Commerce >=2.3.5 &lt;2.4.3*) - Korrigerar problemet när kreditnotan inte längre uppdateras och orsakar dubblettproduktreservationsuppdateringar i databasen.
* **MDVA-38132** (*för Adobe Commerce >=2.3.3 &lt;2.4.3*) - Korrigerar problemet när det inte går att nå administrationspanelen på grund av en *för många omdirigeringar* fel.
* **MDVA-38270** (*för Adobe Commerce >=2.4.1 &lt;2.4.3*) - Korrigerar problemet med att information om presentkort saknas i ordersumman i GraphQL.

## v1.0.24 {#v1-0-24}

* **MDVA-37779** (*för Adobe Commerce >=2.4.2 &lt;=2.4.4*) - Åtgärdar problemet med att lägga till en konfigurerbar produkt i kundvagnen via GraphQL när webbplats-ID:t inte sammanfaller med butiks-ID:t.
* **MDVA-36832** (*för Adobe Commerce >=2.3.4 &lt;=2.4.2-p1*) - Korrigerar problemet där bilder dupliceras på sidor när visningsbredden är 768 px.
* **MDVA-37874** (*för Adobe Commerce >=2.3.6 &lt;=2.3.7 || >=2.4.1 &lt;=2.4.2-p1*) - Åtgärdar problemet där *Fast rabattbelopp för hel vagn* används felaktigt på en paketprodukt som innehåller mer än ett alternativ.
* **MDVA-37913** (*för Adobe Commerce >=2.3.0 &lt;=2.4.0-p1*) - Korrigerar problemet där hämtningsbara länkar försvinner om den hämtningsbara produkten uppdateras via API.
* **MDVA-34330** (*för Adobe Commerce >=2.3.1 &lt;=2.4.2-p1*) - Korrigerar problemet där order i orderrastret inte filtreras enligt administratörens tidszon.

## v1.0.23 {#v1-0-23}

* **MDVA-37478** (*för Adobe Commerce >=2.3.0 &lt;=2.3.7*) - Korrigerar problemet där Adobe Commerce genererar ett fel när en delfaktura skapas för order som läggs med *Betalning à conto* betalningsmetod via REST API.
* **MDVA-37362** (*för Adobe Commerce >=2.3.4 &lt;=2.4.2-p1*) - Korrigerar problemet där konfigurerbara produktalternativvärden och variantattributvärden var tomma i GraphQL-svaret.
* **MDVA-37288** (*för Adobe Commerce 2.4.2*) - Korrigerar problemet där felaktiga nivåpriser returnerades efter GraphQL-begäran.
* **MDVA-37225** (*för Adobe Commerce >=2.4.1 &lt;=2.4.2-p1*) - Korrigerar problemet där överföringsprocessen fastnar när snabborder skapas när det finns ett heltalsvärde i importerade SKU:er.
* **MDVA-37224** (*för Adobe Commerce >=2.3.3 &lt;=2.4.2-p1*) - Korrigerar problemet där kunderna inte kan betala för överlåtbar offert med [!DNL PayFlow Pro] med en annan produkt i varukorgen.
* **MDVA-36286** (*för Adobe Commerce >=2.3.6 &lt;=2.4.2-p1*) - Korrigerar problemet där förhandsvisningen i Page Builder-widgeten bryts om samma SKU har en annan position i underkategorier.
* **MDVA-30186** (*för Adobe Commerce >=2.3.4 &lt;=2.3.5-p2, >=2.4.0 &lt;=2.4.0-p1, >=2.4.2 &lt;=2.4.2-p1*) - Korrigerar problemet där attributalternativen sorteras efter alternativvärde i stället för efter antalet attributobjekt i GraphQL svar.

## v1.0.22 {#v1-0-22}

* **MDVA-36718** (*för Adobe Commerce >=2.3.0 &lt;=2.4.2*) - Korrigerar problemet där de gamla anpassade alternativen kvarstår efter att de har ändrats via API.
* **MDVA-35773** (*för Adobe Commerce >=2.3.6 &lt;=2.3.6-p1 || >=2.4.1 &lt;=2.4.2*) - Korrigerar problemet med att Summa inte visas som noll på fakturan för order med 100 % rabatt.
* **MDVA-36833** (*för Adobe Commerce 2.4.2*) - Korrigerar problemet med sökresultat som visar slumpmässiga antal produkter per sida efter att ha exkluderat vissa produkter från en delad katalog.
* **MDVA-37182** (*för Adobe Commerce >=2.4.1 &lt;=2.4.2*) - Åtgärdar problemet med att få felaktiga sökresultat i båda [!DNL Elasticsearch] version 6 och version 7.
* **MDVA-36253** (*för Adobe Commerce >=2.4.0 &lt;=2.4.1-p1*) - Korrigerar problemet där fel delsumma visas i minivagnen efter att artikeln tagits bort.
* **MDVA-36853** (*för Adobe Commerce 2.4.2*) - Korrigerar problemet med att inga bilder visas vid inläsning av stora mediegallerier.

## v1.0.21 {#v1-0-21}

* **MDVA-34665** (*för Adobe Commerce >=2.3.4 &lt;=2.3.4-p2*) - Åtgärdar problemet med saknade paketerade produkter på kategorisidor.
* **MDVA-36615** (*för Adobe Commerce 2.4.2*) - Korrigerar problemet med felaktigt produktantal i Admin produktrutnät.
* **MDVA-36464** (*för Adobe Commerce >=2.4.0 &lt;=2.4.2*) - Korrigerar problemet där e-postmeddelandekonfigurationen inte fungerar på butiksvisningsnivå.
* **MDVA-36138** (*för Adobe Commerce ^2.3.2*) - Korrigerar problemet där leveranspriset inte justeras och det fulla fraktpriset visas för kunderna om inte alla artiklar i vagnen berättigar till fraktkostnaden.
* **MDVA-36424** (*för Adobe Commerce >=2.3.0 &lt;=2.3.3-p1 || >=2.0.0 &lt;2.2.0*) - Korrigerar problemet där mediabilder som är kopplade till sidbyggarelement försvinner när innehållet redigeras upprepade gånger om backend-bas-URL:en inte är samma som lagerfront-URL:en.
* **MDVA-35984** (*för Adobe Commerce ^2.4.0*) - Åtgärdar problemet med felaktig produktkvantitet och säljbar kvantitet efter att ha skapat flera samtidiga leveranser för samma produkt.

## v1.0.20 {#v1-0-20}

* **MDVA-36170** (*för Adobe Commerce >=2.3.4 &lt;2.4.2*) - Detta åtgärdar problemet där GraphQL-frågan inte cachelagras med cache-taggen category.
* **MDVA-33168** (*för Adobe Commerce >=2.3.3 &lt;2.4.2*) - Åtgärdar problemet när ett produktattribut uppdateras via API. Alla andra attribut ändras till ett tomt värde.
* **MDVA-19640** (*för Adobe Commerce >=2.3.0*) - Åtgärdar problemet där [!DNL Advanced Reporting] visar inga data.
* **MDVA-11189** (*för Adobe Commerce >=2.3.0 &lt;2.3.5*) - Korrigerar problemet när du har importerat en CSV-fil för att uppdatera produktlager, rader från `cataloginventory_stock` tabellen tas bort.
* **MDVA-26639** (*för Adobe Commerce >=2.3.3-p1 &lt;2.3.6*) - Korrigerar problemet där orderobjekten saknas i orderposten om en ny e-postmall för orderbekräftelse skapas.
* **MDVA-15546** (*för Adobe Commerce >=2.3.0*) - Korrigerar problemet där efter att en order har skapats *Column entity_id where-satsen är tvetydig* fel visas i undantagsloggen.
* **MDVA-21095** (*för Adobe Commerce >=2.3.0 &lt;2.3.5*) - Korrigerar problemet när en fråga `INSERT INTO search_tmp` slutar inte efter att massattributvärdet har uppdaterats.
* **MDVA-23845** (*för Adobe Commerce >=2.3.2-p2 &lt;2.3.5*) - Korrigerar problemet där e-postmallar inte kan förhandsgranskas när JavaScript-miniatyrbilder har aktiverats.
* **MDVA-22026** (*för Adobe Commerce >=2.3.2 &lt;2.3.4*) - Korrigerar problemet där det inte går att importera produkter från CSV-filen, inklusive bilder från externa URL:er.
* **MDVA-22383** (*för Adobe Commerce >=2.3.0 &lt;2.3.4*) - Korrigerar problemet där det tar lång tid att spara en produkt och sidan avbryts.
* **MC-41359** (*för Adobe Commerce >=2.3.6-p1 &lt;2.3.7, >=2.4.2 &lt;2.4.3*) - Korrigerar problemet med felaktiga inställningar för cookie-parametrar för SameSite.

## v1.0.19 {#v1-0-19}

* **MDVA-33614** (*för Adobe Commerce 2.4.1*) - Korrigerar problemet där Page Builder orsakar följande fel: *Ett fel uppstod när Page Builder startades. Kontakta din tekniska supportkontakt.*
* **MDVA-35356** (*för Adobe Commerce >=2.3.0 &lt;2.4.3*) - Korrigerar problemet med felaktig butikskreditretur efter delvis fakturerad orderannullering.
* **MDVA-33289** (*för Adobe Commerce >=2.4.0 &lt;2.4.3*) - Korrigerar problemet där rå JavaScript-kod visas i faktureringsadressgränssnittet vid utcheckning om [!DNL Google Tag Manager] är aktiverat.
* **MDVA-35982** (*för Adobe Commerce >=2.3.0 &lt;2.4.3*) - Korrigerar problemet där administratörsanvändare som är begränsade till en viss webbplats inte kan skapa en leverans för den beställning som finns på samma webbplats.
* **MDVA-35155** (*för Adobe Commerce >=2.3.0 &lt;2.3.6*) - Korrigerar problemet där det är omöjligt att köpa en paketprodukt om alternativtiteln ändrades.
* **MDVA-35910** (*för Adobe Commerce >=2.4.1 &lt;2.4.3*) - Korrigerar problemet där det är omöjligt att skapa ett nytt kundkonto efter att ha inaktiverat inloggningen som kundfunktion.
* **MDVA-34474** (*för Adobe Commerce >=2.3.0 &lt;2.4.3*) - Åtgärdar problemet med att lägga till en produkt i rekvisitionslistan med API:t.
* **MDVA-34591** (*för Adobe Commerce >=2.3.0 &lt;2.4.3*) - Korrigerar problemet med en felaktig beräkning av kundvagnsregelrabatt för *Maximal mängdrabatt används för* och *Steg för rabattant (Köp X)*.
* **MDVA-33704** (*för Adobe Commerce >=2.4.0 &lt;2.4.3*) - Korrigerar problemet där *Hämtning i butik* Leveransalternativet visas inte, men är konfigurerat att vara tillgängligt.
* **MDVA-34928** (*för Adobe Commerce >=2.3.5 &lt;2.3.5-p2*) - Korrigerar problemet där sidinläsaren visas i oändlighet efter att butikskrediten tagits bort från betalningen.
* **MDVA-35254** (*för Adobe Commerce >=2.3.1 &lt;2.4.3*) - Korrigerar problemen med CAPTCHA vid utcheckning.
* **MDVA-35569** (*för Adobe Commerce >=2.3.4 &lt;2.4.2*) - Korrigerar problemet där *fast produktskatt* fältet fylls inte i i GraphQL-svaret när tillstånd anges.
* **MDVA-35847** (*för Adobe Commerce >=2.4.1 &lt;2.4.3*) - Korrigerar B2B-problemet där företagsanvändare tar bort information om ett anpassat kundattribut används.
* **MDVA-31307** (*för Adobe Commerce >=2.4.0 &lt;2.4.2*) - Korrigerar problemet där det finns *Slut på minne* fel i vissa kategorier på grund av problem med dynamisk CSP-vitlista för cachelagrade block.

## v1.0.18 {#v1-0-18}

* **MDVA-32655** (*för Adobe Commerce >=2.3.0 &lt;2.4.3*) - Korrigerar fel *pågår* meddelandestatus till rätt *complete* meddelande till konsument `quoteItemCleaner` efter att flera produkter har tagits bort.
* **MDVA-34102** (*för Adobe Commerce >=2.3.0 &lt;2.4.3*) - Anger att standardlagret är noll för inaktiverade produkter i produktstödrastret och Redigera produktsidor i administratörsområdet.
* **MDVA-35286** (*för Adobe Commerce >=2.4.0 &lt;2.4.2*) - Korrigerar problemet där ett fel uppstår om en kund har paketerat produkter i kundvagnen och växlar från utcheckning av flera adresser till utcheckning av en sida.
* **MDVA-35312** (*för Adobe Commerce >=2.4.1-p1 &lt;2.4.2*) - Korrigerar svarskod 500 när en tom GraphQL-begäran anges.
* **MDVA-34189** (*för Adobe Commerce >=2.3.4 &lt;2.4.3*) - Korrigerar 503-bytetimeout på [!DNL Visual Merchandiser] frågar när sidan Administratörskategori läses in.
* **MDVA-34695** (*för Adobe Commerce >=2.3.0 &lt;2.4.1*) - Korrigerar negativ `children_count` efter att kategorier har tagits bort.

## v1.0.17 {#v1-0-17}

* **MDVA-34012** (*för Adobe Commerce >=2.3.1 &lt;2.4.3*) - Korrigerar problemet där *Använd standardvärde* kryssrutan rensas när de schemalagda ändringarna har tillämpats. Problemet uppstår när de schemalagda ändringarna inte längre gäller.
* **MDVA-35064** (*för Adobe Commerce >=2.3.3 &lt;2.4.3*) - Korrigerar problemet där URL-omskrivningar inte genereras för konfigurerbara produkter som skapas via API.
* **MDVA-34943** (*för Adobe Commerce >=2.3.0 &lt;2.4.2*) - Korrigerar problemet där snabbbeställning cachelagrar de tidigare angivna SKU:erna.
* **MDVA-35197** (*för Adobe Commerce >=2.3.5 &lt;2.4.0*) - Korrigerar problemet där ett fel uppstod när GraphQL lades till i kundvagnen om tidigare tillagda produkter inte fanns i lager.
* **MDVA-34850** (*för Adobe Commerce >=2.3.1 &lt;2.4.0*) - Korrigerar problemet där alternativen för utlagring för en konfigurerbar produkt inte visas i stället för att visas som genomstruken.
* **MDVA-34867** (*för Adobe Commerce >=2.3.0 &lt;2.4.3*) - Korrigerar problemet där värden för ett villkorsfält som angetts för en schemalagd uppdatering inte sparas.
* **MDVA-35092** (*för Adobe Commerce >=2.3.5 &lt;2.4.3*) - Korrigerar problemet där användare inte kan lägga till [!DNL Vimeo] videoklipp på grund av inaktuella [!DNL Vimeo] API.

## v1.0.16 {#v1-0-16}

* **MDVA-33453** (*för Adobe Commerce >=2.3.6 &lt;2.4.3*) - Korrigerar problemet där förhandsvisningen av Page Builder-innehållstypen bryts om matchande produkter har olika priser för varje webbplats.
* **MDVA-32634** (*för Adobe Commerce ^2.3.1*) - Korrigerar problemet där `url_path` för kategorin som tilldelats till alla butiker ändras inte när kategorin har flyttats i hierarkin.
* **MDVA-33344** (*för Adobe Commerce ^2.3.0*) - Korrigerar problemet där hårdkodad `rma_item` ID för entitetens standardattributuppsättning används i stället för värdet från databasen.
* **MDVA-34192** (*för Adobe Commerce >=2.3.4 &lt;2.4.3*) - Korrigerar problemet där det inte går att ändra/ange kundens födelsedatum i formatet dd/mm/åååå.
* **MDVA-34847** (*för Adobe Commerce ^2.3.0*) - Korrigerar konvertering av lagrings-ID:n till heltal för SQL-villkor i Admin-samlingar för Admin User med anpassade behörigheter.
* **MDVA-34886** (*för Adobe Commerce ^2.3.2*) - Korrigerar problemet där sökningen inte returnerar resultat om *vikt* produktattributet är konfigurerat som sökbart.

## v1.0.15 {#v1-0-15}

* **MDVA-33559** (*för Adobe Commerce >=2.3.0 &lt;2.4.3*) - Åtgärdar problemet med [!DNL PayPal Payflow Pro] betalning misslyckades med formatfel för omdirigeringsparameterlista.
* **MDVA-34023** (*för Adobe Commerce >=2.3.0 &lt;2.4.3*) - Åtgärdar problemet där felet *Ingen sådan entitet med addressId* visas slumpmässigt i besökarnas webbläsare.
* **MDVA-32759** (*för Adobe Commerce >=2.3.1 &lt;2.4.3 med B2B-tillägg*) - Korrigerar problemet där delade kataloger tar bort befintliga nivåpriser.
* **MDVA-33482** (*för Adobe Commerce ^2.3.5*) - Korrigerar problemet där generering av en kreditnota mot en partiell faktura resulterar i moms för den totala ordern i stället för moms för den partiella fakturan.
* **MDVA-33393** (*för Adobe Commerce >=2.3.0 &lt;2.4.2*) - Korrigerar felet *Angivet countryId finns inte*.
* **MDVA-33632** (*för Adobe Commerce >=2.3.0 &lt;2.3.7*) - Anger en korrigering där undantagsmeddelandet *Produkten är inte i lager* visas nu för en administratörsanvändare när de försöker beställa om en produkt som inte finns i lager.
* **MDVA-34469** (*för Adobe Commerce >=2.4.1 &lt;2.4.2*) - Korrigerar problemet där GraphQL-mutationer i kundvagnen misslyckas när flera butiksvyer används.
* **MDVA-33976** (*för Adobe Commerce >=2.3.0 &lt;2.3.7*) - Korrigerar problemet där paketprodukten visas utanför lagret efter att det andra alternativet tagits bort från paketprodukten.
* **MDVA-33894** (*för Adobe Commerce >=2.4.0 &lt;2.4.1 med B2B-tillägg*) - Korrigerar flera problem med funktionen Snabbordning, inklusive att lägga till och ta bort flera produkter och SKU-skiftlägeskänslighet.
* **MDVA-27664** (*för Adobe Commerce >=2.3.4 &lt;2.3.6*) - Korrigerar problemet i kundregistreringsformuläret som orsakade att ett fel visades: *FEL - Födelsedatumet får inte vara senare än idag.*
* **MDVA-33970** (*för Adobe Commerce >=2.3.4 &lt;2.4.2*) - Korrigerar problemet där det finns fel valutasymbol i kreditnotan när prisattributets omfång är inställt på webbplatsen.
* **MDVA-33992** (*för Adobe Commerce >=2.3.0 &lt;2.4.2*) - Åtgärdar problemet med att B2B-specialpriser visas felaktigt vid utcheckning.
* **MDVA-34100** (*för Adobe Commerce >=2.3.4 &lt;2.4.2 med B2B-tillägg*) - Korrigerar problemet där ett företagskonto inte kan skapas från företagsstruktursidan.

## v1.0.14 {#v1-0-14}

* **MDVA-31969** (*för Adobe Commerce >=2.3.3 &lt;2.3.5, >=2.4.0 &lt;2.4.2*) - Åtgärdar problemet med duplicerade bilder efter produktimport från en CSV-fil.
* **MDVA-33382** (*för Adobe Commerce >=2.3.0 &lt;2.4.2*) - Korrigerar problemen med indexerarens ogiltigförklaring efter att produkterna tagits bort från en kategori.
* **MDVA-28511** (*för Adobe Commerce >=2.3.5 &lt;2.3.6*) - Korrigerar problemet där det inte går att slutföra [!DNL PayPal] checka ut om fältet Namn innehåller vissa tecken (som versala bokstäver med accent).
* **MDVA-31519** (*för Adobe Commerce >=2.3.5 &lt;2.3.6*) - Korrigerar problemet med timeout i gästutcheckning när en platsövergripande försäljningsregel används.
* **MDVA-33281** (*för Adobe Commerce >=2.3.4 &lt;2.3.6*) - Korrigerar problemet där det finns ett allvarligt fel i `inventory:reservation:list-inconsistencies` på grund av fel SKU-parametertyp.
* **MDVA-24201** (*för Adobe Commerce >=2.3.0 &lt;2.3.5*) - Korrigerar problemet där priserna inte återspeglar den schemalagda kundvagnsprisregeln förrän indexeringen görs manuellt.
* **MDVA-32694** (*för Adobe Commerce >=2.3.0 &lt;2.3.6 || >= 2.4.0 &lt;2.4.2*) - Korrigerar problemet där en administratörsanvändare inte kan lägga till en produkt i en överlåtbar offert om den är relaterad till en butik som inte är standard.
* **MDVA-33516** (*för Adobe Commerce >=2.3.0 &lt;2.3.6*) - Korrigerar problemet där redigering av en paketprodukt i en rekvisitionslista leder till ett fel.
* **MDVA-33975** (*för Adobe Commerce >=2.3.4 &lt;2.4.2*) - Korrigerar flera problem relaterade till prisberäkning i GraphQL-begäranden.

## v1.0.13 {#v1-0-13}

* **MDVA-30858** (*för Adobe Commerce >=2.3.0 &lt;2.4.2*) - Åtgärdar problemet med [!DNL PayPal] Kvittningsrapporter är inte tillgängliga under **Rapporter** > **Försäljning** > **[!DNL PayPal]** Kvittning som förväntat.
* **MCP-87** (*för Adobe Commerce >=2.3.1 &lt;2.4.2*) - Förbättrad indexeringstid för kategoriprodukter och börsindexerare för stora profiler.
* **MDVA-33106** (*för Adobe Commerce >=2.3.0 &lt;2.4.2*) - Korrigerar problemet där de omlagda produktändringarna raderas efter kronen `run` kommandot körs.
* **MDVA-19391** (*för Adobe Commerce >=2.3.0 &lt;2.3.5*) - Åtgärdar problemet där `analytics_collect_data` genererar ett fel på grund av NULL-beskrivningsposter i `catalog_category_entity_text` tabell.
* **MDVA-20376** (*för Adobe Commerce >=2.3.2 &lt;2.3.4*) - Åtgärdar problemet med *Ingen sådan entitet med customerId = 1* fel i `exception.log` för inloggade kunder efter orderplacering.
* **MDVA-23764** (*för Adobe Commerce >=2.3.2 &lt;2.3.5*) - Korrigerar felet i `JsFooterPlugin.php` som påverkar visningen av dynamiska block.
* **MDVA-13203** (*för Adobe Commerce >=2.3.0 &lt;2.4.2*) - Korrigerar problemet där *Integritetsbegränsningen bryter tabellen search_tmp_* felet visas efter en fullständig omindexering.
* **MDVA-23426** (*för Adobe Commerce >=2.3.3 &lt;2.3.5*) - Korrigerar problemet där e-postmeddelanden från Adobe Commerce innehåller en tom brödtext med innehåll som läggs till som bilaga.
* **MDVA-22150** (*för Adobe Commerce >=2.3.1 &lt;2.3.4*) - Korrigerar problemet där kunder med en konfigurerbar produkt i kundvagn och en kupong som används inte kan logga in om den konfigurerbara produkten är inaktiverad i Admin.
* **MDVA-32545** (*för Adobe Commerce >=2.3.0 &lt;2.4.2*) - Korrigerar problemet där fakturor inte skickas ut automatiskt när du skapar order från administratören.
* **MDVA-32714** (*för Adobe Commerce >=2.3.4 &lt;2.4.1*) - Korrigerar problemet där kundgruppspriset inte fungerar i GraphQL-produktfrågan.

## v1.0.12 {#v1-0-12}

* **MDVA-31399** (*för Adobe Commerce >=2.3.2 &lt;2.4.2*) - Lägger till *Delsumma (inkl. Skatt)* alternativ för prisregelvillkor.
* **MDVA-31236** (*för Adobe Commerce >=2.4.0 &lt;2.4.2*) - Korrigerar problemet där administratörer med anpassad resursåtkomst inte kan konfigurera 2FA eller logga in.
* **MDVA-30845** (*för Adobe Commerce >=2.3.5 &lt;2.3.7*) - Korrigerar problemet där *Det finns tyvärr inga offerter för den här beställningen* fel visas när det inte går att ansluta till UPS XML/USPS/DHL och ingen annan leveransmetod är tillgänglig.
* **MDVA-32133** (*för Adobe Commerce >=2.4.0 &lt;2.4.1*) - Korrigerar problemet där mediegalleriet inte läses in från Page Builder i vissa fall.
* **MDVA-12304** (*för Adobe Commerce >=2.3.0*) - Ökar det maximala antalet cookies från 50 till 200.
* **MDVA-32632** (*för Adobe Commerce >=2.3.2 &lt;2.3.5*) - Korrigerar problemet där order visas i betalningssystemet, men inte i Adobe Commerce.
* **MDVA-32449** (*för Adobe Commerce >=2.3.0 &lt;2.3.6 || 2.4.0 || >=2.4.1 &lt;2.4.2 med B2B-tillägg*) - Korrigerar problemet där orderhistoriken läses in mycket långsamt eller inte läses in alls.
* **MDVA-32739** (*för Adobe Commerce >=2.3.0 &lt;2.4.2*) - Korrigerar problemet där aktivering av asynkrona e-postmeddelanden skickar gamla e-postmeddelanden.

## v1.0.11 {#v1-0-11}

* **MC-38509** (*för Adobe Commerce 2.3.6, 2.4.1*) - Korrigerar problemet där *Skapa ett konto* knappen förblir inaktiverad efter att ogiltiga data i *Skapa nytt kundkonto* formulär.
* **MDVA-31006** (*för Adobe Commerce 2.3.0, 2.3.1*) - Korrigerar problemet där dubblettorder visas efter att en order har lagts med [!DNL Paypal Express] betalning.
* **MDVA-25602** (*för Adobe Commerce 2.3.0*) - Åtgärdar problem med [!DNL PayPal Payflow Pro] betalningssätt och hantering av cookies som `SameSite=Lax` som standard i webbläsaren Chrome 80 och API-svaret omdirigeras till kundens inloggningssida.

## v1.0.10 {#v1-0-10}

Mindre korrigeringar för korrigeringsversioner

## v1.0.9 {#v1-0-9}

* **MDVA-31363** (*för Adobe Commerce >=2.3.2 &lt;2.4.2*) - Korrigerar problemet där kundprisregeln med kupong inte gäller via GraphQL när *Fast beloppsrabatt för hela kundvagn* används.
* **MDVA-30889** (*för Adobe Commerce >=2.3.0 &lt;2.4.2*) - Korrigerar problemet där ett fel inträffar efter att ett paket med virtuella och enkla produkter har fakturerats som alternativ.
* **MDVA-31791** (*för Adobe Commerce >=2.3.4 &lt;2.3.5*) - Förbättrar prestanda för produktsidan när målregler eller länkade produkter används.
* **MDVA-31168** (*för Adobe Commerce >=2.3.0 &lt;2.4.2*) - Korrigerar problemet där produktexportens CSV-fil inte visas och där det finns ett minnesallokeringsfel.
* **MDVA-32313** (*för Adobe Commerce >=2.3.0 &lt;2.3.4*) - Korrigerar problemet där konfigurerbara produkter kunde läggas till i önskelistan med fel konfigurationsalternativ.
* **MDVA-31759** (*för Adobe Commerce >=2.3.0 &lt;2.4.2*) - Korrigerar problemet där produkter inte uppdateras med *listruta* och *textområde* attributvärden under CSV-import.
* **MDVA-32012** (*för Adobe Commerce >=2.3.0 &lt;2.4.2*) - Korrigerar problemet där postnummer i Korea och Argentina inte kan valideras.
* **MDVA-31640** (*för Adobe Commerce >=2.3.1 &lt;2.3.6 || >=2.4.0 &lt;2.4.1*) - Korrigerar problemet där ett specialpris inte kan uppdateras via REST API.
* **MDVA-28651** (*för Adobe Commerce >=2.3.0 &lt;2.3.6 || >2.4.0 med B2B-tillägg*) - Korrigerar problemet där det finns prestandaproblem med inläsning av överlåtbara offerter via REST API.

## v1.0.8 {#v1-0-8}

* **MDVA-31242** (*för Adobe Commerce >=2.3.0 &lt;2.4.1 med B2B-tillägg*) - Korrigerar problemet där en felaktig valutasymbol visas i rutnätet för kreditnotor.
* **MDVA-31295** (*för Adobe Commerce >=2.3.0 &lt;2.4.2*) - Korrigerar problemet där belöningspoäng inte beräknas när en delorder har slutförts och artiklarna beskattas.
* **MDVA-30112** (*för Adobe Commerce >=2.3.4 &lt;2.4.2*) - Korrigerar problemet där antalet order överstiger *teckenstorlek* värde, Adobe Commerce ser beställningarna med *väntar* status som inkonsekvenser.
* **MDVA-31150** (*för Adobe Commerce >=2.3.0 &lt;2.4.2*) - Korrigerar problemet där butikskreditsaldon och presentkortsaldon inte returneras av API-anropet för GET Invoice Rest, när fakturan bokfördes av Rest API-anrop och ordern delvis betalades av butikskreditkonton och presentkortskonton.
* **MDVA-30963** (*för Adobe Commerce >=2.3.2 &lt;2.4.2*) - Korrigerar problemet där produktfiltreringsresultat bara innehåller värden som angetts för *Alla butiksvyer* i Admin, ta med produkter med värden som åsidosatts på butiksvynivån.
* **MDVA-29954** (*för Adobe Commerce >=2.3.0 &lt;2.3.6 || 2.4.0 || 2.4.2 med B2B-tillägg*) - Korrigerar problemet där *Ny registreringsbegäran för företag* och *Du har länkats till ett företag* e-postmeddelanden skickas från fel adress.
* **MDVA-28357** (*för Adobe Commerce >=2.3.2 &lt;2.3.6 || >=2.4.0 &lt;2.4.1*) - Ersätter standardanalyseraren med en anpassad analyserare med nyckelordstokenzer för SKU-fältet i [!DNL ElasticSearch] index för att få sökfrågor med jokertecken att fungera med SKU:er som innehåller ett bindestreck (&quot;-&quot;).

## v1.0.7 {#v1-0-7}

* **MDVA-30972** (*för Adobe Commerce >=2.3.0 &lt;2.4.2*) - Korrigerar problemet där status för anpassad order ändrades till *Bearbetar* efter att en del av leveransen har skapats med WebApi.
* **MDVA-30428** (*för Adobe Commerce >=2.3.4 &lt;2.3.5*) - Korrigerar problemet där kunderna inte kan lägga till en produkt i önskelistan om den här produkten har tilldelats en anpassad lagerkälla.
* **MDVA-30594** (*för Adobe Commerce >=2.3.0 &lt;2.4.2*) - Korrigerar problemet där en order med flera adresser inte kunde sparas vid utcheckning när FPT har konfigurerats.
* **MDVA-29148** (*för Adobe Commerce >=2.3.0 &lt;2.4.2*) - Åtgärdar problemet när en produkt skapas via ett API-anrop, det anpassade produktattributet för `\Magento\Eav\Model\Entity\Attribute\Backend\ArrayBackend` (som Multiselect)-typen använder inte standardvärdet om inget värde angavs i nyttolasten.
* **MDVA-30837** (*för Adobe Commerce >=2.3.1 &lt;2.3.5*) - En konfigurationsinställning har lagts till *Inkludera moms till belopp: Ja/Nej* i konfiguration av kostnadsfri leveransmetod. När *Inkludera moms i belopp* är inställd på *Ja*, Minsta orderbelopp beräknas som Delsumma + moms. När *Inkludera moms i belopp* är inställd på *Nej*, Minsta orderbelopp beräknas som delsumma
* **MDVA-25028** (*för Adobe Commerce >=2.3.2 &lt;2.3.3 || >=2.3.5 &lt;2.3.6*) - Korrigerar problemet när order som placeras med [!DNL PayPal Payflow Pro] är inte inställda på statusen Misstänkt bedrägeri när bedrägerifilter aktiveras.
* **MDVA-31224** (*för Adobe Commerce >=2.3.3 &lt;2.3.5*) - Förbättrar prestanda för `catalog_product_price` indexera om för paketprodukter.
* **MDVA-31321** (*för Adobe Commerce >=2.3.2 &lt;2.3.5*) - Korrigerar en tom sida (fel) när *Visa alla* är markerat. [!DNL Elasticsearch] returnerar en stor lista över produkt-ID:n. I det här fallet konverteras order by-satsen till ett felaktigt SQL-format.
* **MDVA-30815** (*för Adobe Commerce >=2.3.2 &lt;2.3.4*) - Korrigerar problemet där en tom sida visas när du ändrar hur många sökresultat som ska visas på sökresultatsidan. [!DNL Elasticsearch] visar nu resultat från kategorisidor korrekt när du ändrar antalet sökresultat som visas per sida.
* **MDVA-30782** (*för Adobe Commerce >=2.3.5 &lt;2.4.2*) - Korrigerar problemet där dynamiskt block visas oavsett kundvagnsregel.
* **MDVA-31021** (*för Adobe Commerce >=2.3.0 &lt;2.4.2*) - Korrigerar problemet där det finns prestandaproblem i `module-catalog-import-export/Model/Import/Product/Option.php`. Om det finns fler än ~100 kB poster i `catalog_product_option` en ny CSV-fil med en enda produkt tar mindre än 10 sek att validera.
* **MDVA-31007** (*för Adobe Commerce >=2.4.0 &lt;2.4.1*) - Korrigerar problemet där anpassade adressattribut inte visas korrekt på sidan med orderinformation i mitt kontoområde och i serverdelen.
* **MDVA-29389** (*för Adobe Commerce >=2.3.0 &lt;2.4.2*) - Åtgärdar problemet med avancerad rapportering där `analytics_collect_data` cronjob säger: *Port måste konfigureras inom värdparametern (som localhost:3306)*.
* **MDVA-31343** (*för Adobe Commerce >=2.3.4 &lt;2.3.6*) - Korrigerar problemet med den borttagna brödklassen `page-layout-category-full-width` när en kategori är schemalagd.
* **MDVA-30945** (*för Adobe Commerce >=2.3.0 &lt;2.4.2*) - Korrigerar problemet där du får ett allvarligt felmeddelande när du uppdaterar kundvagnar `Call to a member function getValue() on null in module-configurable-product CartItemProcessor.php`.

## v1.0.6 {#v1-0-6}

* **MDVA-28993** (*för Adobe Commerce >=2.3.4 &lt;2.4.0*) - Implementerar *Minimivärdet måste matcha* funktionalitet och delvis sökning efter [!DNL Elasticsearch] motor. Löser problem med bindestreck i sökfrågor.
* **MDVA-30102** (*för Adobe Commerce >=2.3.2 &lt;=2.4.0*) - Korrigerar problemet där Redis-cachen växer snabbt eftersom layoutcachen inte har TTL.
* **MDVA-30599** (*för Adobe Commerce >=2.3.4 &lt;=2.4.0*) - Korrigerar problemet där gästcitat som skapats med API felaktigt markeras som citattecken för inloggade kunder.
* **MDVA-29446** (*för Adobe Commerce >=2.3.3 &lt;=2.4.0*) - Korrigerar problemet där priset på en leveransmetod som inte är tillämplig visas som noll vid utcheckning.
* **MDVA-30357** (*för Adobe Commerce >=2.3.2 &lt;=2.4.0*) - Korrigerar problemet med fel bild-URL:er som skapas när en platskarta genereras av cron.
* **MDVA-30565** (*för Adobe Commerce >=2.3.2 &lt;=2.3.3-p1*) - Åtgärdar problemet där *Ingen sådan entitet med cartid = 0* fel visas för gästkund vid utcheckning i butiken om beständig kundvagn är aktiverad.
* **MDVA-29787** (*för Adobe Commerce >=2.3.0 &lt;=2.4.0*) - Korrigerar problemet där målregeln för relaterade produkter inte fungerar när *är en av* villkor används för att definiera produkter som ska visas.
* **MDVA-30977** (*för Adobe Commerce >=2.3.4 &lt;=2.3.5-p2*) - Åtgärdar problemet med slumpmässiga produkter som saknas i kategorier efter omindexering.
* **MDVA-28202** (*för Adobe Commerce >=2.3.4 &lt;=2.4.2*) - Korrigerar problemet där navigering i lager inte filtrerar konfigurerbara produkter korrekt när MSI används.
* **MDVA-28300** (*för Adobe Commerce >=2.3.0 &lt;2.3.6*) - Korrigerar problemet där GQL-begäran inte återspeglar prisförändringar från katalogprisregler.
* **MDVA-31006** (*för Adobe Commerce >=2.3.2 &lt;=2.4.2*) - Korrigerar problemet där dubblettorder visas efter att en order har lagts med [!DNL Paypal Express] betalning.

## v1.0.5 {#v1-0-5}

* **MDVA-30841** (*för Adobe Commerce >=2.3.4 &lt;2.3.6 || 2.4.0*) - Åtgärdar problemet med lagerstyrd navigering, där *Nej* värdet för booleska typproduktattribut inkluderades inte i lagerstyrd navigering om [!DNL Elasticsearch] användes som sökmotor.
* **MDVA-28191** (*för Adobe Commerce >=2.3.3 &lt;2.4.2*) - Korrigerar problemet där inga betalningsmetoder har lästs in när order skapas via Admin.
* **MDVA-29959** (*för Adobe Commerce >=2.3.0 &lt;=2.3.3-p1 med B2B-tillägg*) - Korrigerar problemet där begränsad administratörsanvändare med *Företag* behörigheter kan inte ta bort företagskonto.
* **MDVA-30265** (*för Adobe Commerce >=2.3.3 &lt;2.4.2*) - Korrigerar problemet där länken för leveransspårning slutar fungera efter att fakturan har skapats.
* **MDVA-28409** (*för Adobe Commerce >=2.3.4 &lt;2.3.6 || 2.4.0*) - Korrigerar problemet där `sales_clean_quotes` cron-jobb misslyckas med *slut på minne* fel när antalet utgångna citattecken i databasen är enormt.
* **MDVA-30593** (*för Adobe Commerce >=2.3.0 &lt;2.3.4*) - Korrigerar problemet där offerter som har gått ut enligt inställningen för Offerts livstid inte rensas.
* **MDVA-30107** (*för Adobe Commerce >=2.3.0 &lt;2.3.6*) - Korrigerar problemet där butiksväljaren inte fungerar som förväntat om olika bas-URL:er används för butiksvyer.
* **MDVA-28763** (*för Adobe Commerce >=2.3.2 &lt;2.3.4*) - Korrigerar problemet där produktavbildningen dupliceras efter att produktinformationen har uppdaterats med REST API mer än en gång.
* **MDVA-30284** (*för Adobe Commerce >=2.3.0 &lt;2.4.2*) - Korrigerar problemet där katalogsökningsindexeraren misslyckas på grund av följande *[!DNL Elasticsearch]fel: gränsen för det totala antalet fält i indexet har överskridits.*
* **MDVA-29042** (*för Adobe Commerce >=2.3.3 &lt;=2.3.4-p2 med B2B-tillägg*) - Korrigerar problemet där katalogbehörigheter ändrades till *Tillåt* automatiskt när en ny produkt har lagts till i den delade katalogen.
* **MDVA-30428** (*för Adobe Commerce >=2.3.3 &lt;2.4.2*) - Korrigerar problemet där kunderna inte kan lägga till en produkt i önskelistan om den här produkten har tilldelats en anpassad lagerkälla.
* **MDVA-28661** (*för Adobe Commerce >=2.3.0 &lt;2.4.2 med B2B-tillägg*) - Korrigerar problemet där ett fel uppstår i företagsanvändarkontoavsnittet efter att företagsadministratören har ändrats.

## v1.0.4 {#v1-0-4}

* **MDVA-30195** (*för Adobe Commerce 2.3.1 - 2.3.4-p2*) - Korrigerar problemet där cron-jobb misslyckas om databasnamnet är för långt, vilket resulterar i att kategorier inte uppdateras i förgrunden.
* **MDVA-30106** (*för Adobe Commerce ^2.3.0*) - Korrigerar ett fel där betalningar inte läses in med *Det går inte att läsa egenskapen length för null* fel i JS-konsolen.
* **MDVA-28656** (*för Adobe Commerce >=2.3.1 &lt;2.3.6 || >=2.4.0 &lt;2.4.2*) - Korrigerar problemet där orderstatusen ändras till om en order placerades utan betalningsinformation (t.ex. med 100 % rabatt) och en faktura skapades för ordern. *Stängd* i stället för Complete.
* **MDVA-30209** (*för Adobe Commerce 2.3.0 - 2.3.3-p1*) - Korrigerar problemet där kundgruppen ändrades till standard om kunden uppdaterade sin kontoinformation.
* **MDVA-30123** (*för Adobe Commerce >=2.3.4 &lt;2.4.2*) - Korrigerar problemet där attributalternativetiketter inte översätts korrekt för GraphQL-frågor.
* **MDVA-29996** (*för Adobe Commerce >=2.3.3 &lt;2.4.2*) - Korrigerar problemet där kategorisidan inte cachelagras av helsidescache när kategoribehörigheten har aktiverats.
* **MDVA-30164** (*för Adobe Commerce >=2.3.1 &lt;2.4.2*) - Korrigerar problemet där kundposter inte kan exporteras från kundrutnätet om det finns anpassade kundattribut.
* **MDVA-30444** (*för Adobe Commerce >=2.3.0 &lt;2.4.1*) - Korrigerar problemet där inget bekräftelsemeddelande skickas för beställningar som gjorts med GraphQL.
* **MDVA-30490** (*för Adobe Commerce 2.3.4 - 2.3.5-p2*) - Korrigerar problemet där produktjämförelsen genererar felsidan 500 om en av produkterna har en tom kort beskrivning.
* **MDVA-30232** (*för Adobe Commerce >=2.3.1 &lt;2.4.1*) - Korrigerar problemet där det inte går att beställa om den ursprungliga ordern innehåller ett presentkort.
* **MDVA-29965** (*för Adobe Commerce >=2.3.3 &lt;2.4.0*) - Korrigerar problemet där kunderna får ett ogiltigt formulärnyckelfel när en produkt läggs till i kundvagnen.
* **MDVA-30008** (*för Adobe Commerce >=2.3.0 &lt;2.4.2*) - Korrigerar B2B-problemet där det inte går att göra beställningar via Admin API för en produkt som finns i en offentlig katalog.
* **MDVA-22469** (*för Adobe Commerce 2.3.2-p2 - 2.3.3-p1*) - Korrigerar problemet där Page Builder inte fungerar i administrationspanelen när du har uppgraderat till Adobe Commerce 2.3.3 och vissa JS- och CSS-filer inte läses in.
* **MC-35984** (*för Adobe Commerce >=2.4.0 &lt;2.4.1*) - Korrigerar problemet där handlarna inte kunde interagera med några sidelement på retursidan efter att ha skapat en etikett för en RMA (Return Merchandise Authorization).

## v1.0.3 {#v1-0-3}

* **MDVA-25602** (*för Adobe Commerce 2.3.0 - 2.3.4*) - Åtgärdar problemet med [!DNL PayPal Payflow Pro] betalningssätt och hantering av cookies som `SameSite=Lax` som standard i webbläsaren Chrome 80 och API-svaret omdirigeras till kundens inloggningssida.
* **MDVA-26694** (*för Adobe Commerce >=2.3.0 &lt;2.3.6 || 2.4.0*) - Korrigerar problemet med att produkt- och katalogcacheminnen förfaller dagligen, även om de schemaläggs på annat sätt.
* **MDVA-27825** (*för Adobe Commerce >=2.3.0 &lt;2.4.1*) - Korrigerar problemet där export av stora mängder data misslyckades på grund av minnesläckage.
* **MDVA-29085** (*för Adobe Commerce >=2.3.0 &lt;=2.3.5-p1*) - Korrigerar B2B-problemet där inga nya e-postmeddelanden skickas ut om ett företag skapas med API.
* **MDVA-29344** (*för Adobe Commerce >=2.3.5 &lt;=2.4.0-p1*) - Korrigerar problemet där Page Builder fastnar efter att text har kopierats från ett rubrikelement till ett textelement.
* **MDVA-29835** (*för Adobe Commerce >2.3.1 &lt;2.4.2*) - Korrigerar problemet där presentkortsbeställningar innehöll två koder i stället för en.
* **MDVA-30052** (*för Adobe Commerce >=2.3.2-p2 &lt;2.3.5*) - Korrigerar problemet med att privat innehåll (lokal lagring) inte fylldes i korrekt, vilket resulterade i prestandaproblem.
* **MDVA-30131** (*för Adobe Commerce >=2.3.4 &lt;2.3.6 || 2.4.0*) - Åtgärdar problemet med lagerstyrd navigering, där *Nej* värdet för booleska typproduktattribut inkluderades inte i lagerstyrd navigering om [!DNL Elasticsearch] användes som sökmotor.
* **MDVA-35514** (*för Adobe Commerce >=2.4.0 &lt;2.4.1*) - Korrigerar problemet med att skapa en leveransetikett och lägga till beställda produkter i ett paket i det modala fönstret Skapa paket.
