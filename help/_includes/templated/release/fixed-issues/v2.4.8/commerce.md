---
source-git-commit: 53b2494d848c027e32f1493bbc7a9f204677afaa
workflow-type: tm+mt
source-wordcount: '27958'
ht-degree: 0%

---
# Åtgärdade problem i Adobe Commerce (v2.4.8)

## Åtgärdade problem i v2.4.8

Vi har åtgärdat 582 problem i Adobe Commerce 2.4.8 Core-koden. En deluppsättning av de åtgärdade problemen som ingår i den här versionen beskrivs nedan.

### API:er

* __/V1/operations REST API returnerar fel när parent_txn_id = txn_id__
Systemet hanterar nu transaktioner för det överordnade och underordnade konceptet korrekt där det överordnade transaktions-ID:t är detsamma som transaktions-ID:t, vilket förhindrar en oändlig slinga när en fråga ställs till REST API-slutpunkten för /V1/transaktioner. Tidigare skulle detta scenario resultera i ett allvarligt fel på grund av att den maximala körningstiden överskrids.
  _AC-10042 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/1bafc571)_
* __[Graphql] Typproblem i 2.4.7__
Systemet hanterar nu heltalsvärden korrekt i funktionen GetCustomSelectedOptionAttributes när en GraphQL-fråga körs, vilket förhindrar typrelaterade fel. Tidigare uppstod ett typfel när en GraphQL-fråga som använde GetCustomSelectedOptionAttributes med ett heltalsargument startades.
  _AC-11878 - [GitHub-problem](https://github.com/magento/magento2/issues/38662) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/38663)_
* __Specialtecken i kategorin url_key (när de skapas via REST API)__
I specialtecknet category_url_key visas inte specialtecknet där efter korrigeringen visas specialtecknet i category_url_key
  _AC-3223 - [GitHub-problem](https://github.com/magento/magento2/issues/35577) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/c699c206)_
* __REST API som visar beställningar från en annan webbplats. __
Systemet har nu stöd för scopeauktoriserad åtkomst för REST API-administratörstoken och Magento_Sales-slutpunkter, vilket säkerställer att REST API endast visar order som administratören har åtkomst till. Tidigare visades beställningar från alla webbplatser i REST-API:t, oavsett vilken webbplats administratörsanvändaren tilldelat.
  _ACP2E-2703_
* __Problem med rest-API efter att 2FA Duo har aktiverats__
2FA med säkerhetsalternativet Duo genererar nu korrekt signatur för Rest API
  _ACP2E-2755 - [GitHub-kodbidrag](https://github.com/magento/security-package/commit/412fa642)_
* __[REST API]: Använd standardvärdet i butiksvyn förblir inte markerat när du har lagt till konfigurationer för en konfigurerbar produkt__
Problemet har åtgärdats genom att korrekta databasposter har angetts för de anpassningsbara alternativen för en annan lagringsplats än standardbutiken. Kryssrutan för den anpassade butiken i avsnittet&quot;Admin > Katalog > Produktredigering > Anpassningsbara alternativ&quot; avmarkerades tidigare på grund av felaktiga databasposter, även om alternativtiteln för den anpassade butiken inte var densamma som standardbutiken.
  _ACP2E-2927 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/3056e9cb)_
* __REST API kan inte göra begäranden med snedstreck (/) i SKU när Oauth1 används.__
Före korrigeringen kunde du inte göra ett lyckat API-anrop för en produkt som hade &quot;/&quot; i SKU:n. Nu kan du utfärda en lyckad API-inhämtning av produktinformation även om SKU:n innehåller ett snedstreck.
  _ACP2E-2969 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/b21e5d91)_
* __Uppdatering av kundadress misslyckas vid uppdatering via REST API om validateDefaultAddress är aktiverat__
API-slutpunkten fungerar nu som avsett efter att problemet med ID-nyckeln som saknas i API-nyttolasten har åtgärdats.
  _ACP2E-3079 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/9af794a4)_
* __[Cloud] Skapar kundgruppen Duplicera webbplatsgrupppris i Tier Prices API.__
Nu går det inte att skapa kundgruppen Duplicera webbplatsens grupppris i API:t för nivåprissättning.
Tidigare var det möjligt att skapa kundgruppen Duplicera webbplatsens grupppris i Tier Prices API som inte klarade valideringen i Admin när produkten sparades.
  _ACP2E-3091 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/148c3ead)_
* __Det går inte att lägga till orderkommentar med status via REST API__
Problemet har lösts genom att ändra orderstatus om det bara är från det aktuella läget. Tidigare respekterade den inte orderstatus och förhindrade ändringar i orderstatus, även om den kom från samma läge.
  _ACP2E-3130 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/93d50f8d)_
* __Async-åtgärden misslyckas när SKU saknas i nyttolasten__
Async- och sync-åtgärder misslyckades tidigare på grund av fel som beror på att produkten har sparats om sku saknas i nyttolasten. Efter korrigeringen misslyckas åtgärderna för asynkron och synkroniserad produkt för att spara rest-API med relevant undantagsmeddelande.
  _ACP2E-3236 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/66dea0de)_
* __[CLOUD] Det gick inte att uppdatera baspriserna med REST API (värdet för value_id i catalog_product_entity_decimal ökas inte korrekt.)__
Tidigare i den här korrigeringen, när rest api /rest/default/V1/products/base-prices anropades, ökade öknings-ID felaktigt så att det fanns ett mellanrum mellan värdena. Efter korrigeringen ökas det stegvisa ID:t stegvis. Fältintervallet value_id har också ökats.
  _ACP2E-3376 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/d50f6b5d)_
* __Beställningsartiklar visas inte i e-postmeddelanden med kreditnotor för API POST V1/order/:orderId/returned__
Tidigare, före den här korrigeringen, innehöll inte produktinformationsrutnätet när en kund skapar en kreditnota från en API-begäran som meddelar send_email. När den här korrigeringen har tillämpats skickar kunden en begäran om kreditnota-API och hittar produktartikelinformationen i e-postmeddelandet.
  _ACP2E-3460 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/3f12d152)_
* __Standardvärden har inte angetts för datum- och tidsattribut med produkterna RestAPI__
Standardvärden ställs nu in korrekt för datum- och datum- och tidsattribut via RestAPI
  _ACP2E-3486 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/1984c61c)_

### API:er, kundvagn och utcheckning

* __Allvarligt 500-fel: Magento\Framework\Webapi\Exception relaterat till Acceptera HTTP-huvud__
Efter korrigeringen finns det inget problem med att ange rubriken&quot;Godkänn&quot;.
  _ACP2E-3343 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/1366ae5e)_

### API:er, GraphQL

* __det finns ingen graphQl tillgänglig för prenumeration på uppdateringar för belöningspunkter för kund__
Tidigare till korrigeringen kunde inte kundattributet belöning_warning_notification uppdateras via GraphQL mutation och Rest API-anrop. Nu kan uppdateras på samma sätt som kundattributet belöning_update_notification.
  _ACP2E-3348_

### API:er, GraphQL, skatt

* __Både Luma (Rest API) och Graphql beräknar inte skatter när bara postnummer anges.__
Systemet beräknar nu moms korrekt när endast en postkod anges, vilket ger korrekta skattningar för både Luma (Rest API) och GraphQL. Tidigare beräknades endast fraktuppskattningar och skatter inkluderades inte när endast postnummer angavs.
  _AC-12060_

### Konto

* __Kundadressformuläret tillåter slumpmässig kod i namnfälten__
Systemet validerar nu indata i fälten Förnamn och Efternamn i kundadressformuläret, vilket förhindrar att slumpmässig kod används. Tidigare tillät systemet att slumpmässig kod användes i dessa fält utan att något fel uppstod.
  _AC-10782 - [GitHub-problem](https://github.com/magento/magento2/issues/38331) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/38345)_
* __uppdatering av administratörslösenord.__
  _AC-10886 - [GitHub-problem](https://github.com/magento/magento2/issues/38352) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/4bca5dfe)_
* __mitt konto lägger till adress kraschar när jag sparar__
Systemet sparar nu kundadresser korrekt även när regionsfältet inte visas, vilket förhindrar att det kraschar under sparandet. Tidigare uppstod ett undantagsfel om du försöker lägga till eller redigera en adress utan ett fält som visas.
  _AC-10990 - [GitHub-problem](https://github.com/magento/magento2/issues/38406) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/38407)_
* __Omdirigeringsslinga när URL har versaler__
Systemet konverterar nu automatiskt versaler i URL:er till gemener, vilket förhindrar omdirigeringsslingor vid åtkomst till hemsidan. Tidigare skulle en omdirigeringsslinga uppstå om det fanns versaler i URL:en för den säkra basen när du försökte komma åt hemsidan.
  _AC-11718 - [GitHub-problem](https://github.com/magento/magento2/issues/38538) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/38539)_
* __middlename(s) har inte sparats för gästkonton__
Systemet sparar nu mellannamnet för gästkonton korrekt under utcheckningen, så att det blir tillgängligt i e-postmallen. Tidigare sparades inte mellannamnet i offerttabellen och det gick inte att komma åt det i e-postmallen för gästkonton.
  _AC-11755 - [GitHub-problem](https://github.com/magento/magento2/issues/38593) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/39067)_
* __Admin: Sidåtgärdsknappar flyter åt vänster i stället för åt höger__
Systemet justerar nu sidåtgärdsknapparna korrekt till höger om det klisterlappande huvudet på administratörspanelen, vilket förbättrar det professionella utseendet. Tidigare var dessa knappar felaktigt flytande till vänster om den klibbiga rubriken.
  _AC-11919 - [GitHub-problem](https://github.com/magento/magento2/issues/38701) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/44cef3a9)_
* __`dev:di:info`fel i magento 2.4.7__
Konstruktorparametrar visas nu korrekt i systemet när kommandot `dev:di:info` körs, vilket förhindrar att fel uppstår. Tidigare resulterade körningen av det här kommandot i ett fel på grund av ett typmatchningsfel i argumentet.
  _AC-11999 - [GitHub-problem](https://github.com/magento/magento2/issues/38740) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/0c53bbf7)_
* __Kryssrutan Inloggning som kundanmälan kan inte översättas__
Systemet tillåter nu att kryssrutorna&quot;Inloggning som kundanmälan&quot; och&quot;Inloggning som kundens verktygstips&quot; ställs in i butiksvyn, vilket möjliggör översättningar för olika butiksvyer. Tidigare hade dessa fält bara angetts i webbplatsomfånget, vilket förhindrar översättningar för enskilda butiksvyer.
  _AC-13000 - [GitHub-problem](https://github.com/magento/magento2/issues/32329) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/32359)_
* __Gränssnittets startsida i listrutan för min profil är inte där.(intermittent)__
  _AC-14299_
* __Kunden är inloggad, men 404-fel i klientdatorn visas.__
Butikskundkontrollpanelens sida läses nu in som förväntat när en kund loggar in. Tidigare kunde kunderna logga in, men den här sidan visade ett 404-fel. [GitHub-35838](https://github.com/magento/magento2/issues/35838)
  _AC-6071 - [GitHub-problem](https://github.com/magento/magento2/issues/35838) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/36263)_
* __Det går inte att spara kundattributinformation i kundavsnittet för Admin Edit;__
Kundens butiks-ID implementeras nu korrekt per webbplatsomfång för administratörskundens redigeringsformulär.
  _ACP2E-2791 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/488c1034)_
* __[Cloud] Det går inte att skapa kunder via API när privat försäljning är aktiverat__
Nu kan kunden skapas av både autentiserade administrationsanvändare och autentiserade integreringstoken via REST api när webbplatsbegränsningar är aktiverade.
  _ACP2E-3115_
* __När du har loggat in visas inte produkter som lagts till i jämförelselistan som gästanvändare.__
Produkter som lagts till i produktjämförelselistan innan de loggas in som kund bevaras nu efter inloggning.
Tidigare var produkterna som lagts till i jämförelselistan som gästanvändare inte synliga efter inloggning.
  _ACP2E-3329 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/078c387e)_
* __Tillåt länder orsakar problem i kundadresskonfigurationer__
Om du nu väljer Tillåt länder påverkas inte länder som visas utanför det angivna omfånget. Tillåt tidigare att länder konfigureras som påverkade kundadressattribut utanför angivet omfång
  _ACP2E-3433 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/078c387e)_
* __Delat presentationsregister visar händelsedatumet som 1 dag tidigare__
Presentregisterdatumet visas nu korrekt i Storefront
  _ACP2E-3445_
* __VAPT: Affärslogikfel - framtida datum som kundens födelsedatum__
Kundens födelsedatum kan inte anges senare än idag
  _ACP2E-3501 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/d4de4726)_

### Konto, API:er, GraphQL

* __Kund-API - inloggningsfelnummer kan inte återställas till 0 efter slutförd inloggning__
Felnumret återställs till noll i kundentitetstabellen efter att kunden har loggat in via API-slutpunkter.
  _ACP2E-3246 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/ec7e32a9)_

### Konto, administratörsgränssnitt, B2B

* __Begränsade administratörsanvändare kan inte alltid se anpassade delade kataloger__
Begränsade administratörsanvändare kan nu konsekvent visa och hantera kunder och alla delade kataloger som produkterna är tilldelade till, förutsatt att de har tillgång till den specifika butiken. Tidigare kunde en begränsad administratörsanvändare med åtkomst till en viss butik inte alltid se alla delade kataloger som produkterna var tilldelade eller se kunder som inte kunde spara, vilket ledde till inkonsekvenser i systemet.
  _ACP2E-3038 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/7377de59)_

### Konto, kundvagn och utcheckning

* __&quot;välj&quot;-attributet för anpassad kundadress återges inte för den nya kundadressen__
  _AC-2341 - [GitHub-problem](https://github.com/magento/magento2/issues/34950)_

### Administratörsgränssnitt

* __[Problem] Lägg till behörighetskontroll för knappen &quot;Läs in data igen&quot;__
Systemet innehåller nu en behörighetskontroll för knappen &quot;Läs in data igen&quot; som säkerställer att den bara visas och är tillgänglig för användare med rätt behörighet. Tidigare var knappen &quot;Läs in data igen&quot; synlig och klickbar för alla användare, vilket ledde till en&quot;ej tillåten&quot; sida när användaren klickade utan nödvändig behörighet.
  _AC-10705 - [GitHub-problem](https://github.com/magento/magento2/issues/38283) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/38279)_
* __[Utgåva] Inkonsekventa etiketter för attribut i marknadsföringsregler__
Systemet fyller nu etiketterna korrekt för kategori- och attributalternativ i kundprisregeln
  _AC-11427 - [GitHub-problem](https://github.com/magento/magento2/issues/31232) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/31231)_
* __Dataverifieringen är klar och knappen Importera finns under Importera produkter med beteendet Ersätt__
Systemet validerar nu data korrekt och döljer&quot;Importera&quot;-knappen under produktimportprocessen med beteendet&quot;Ersätt&quot;, vilket förhindrar att data ersätts av oönskade data. Tidigare validerades data felaktigt och knappen Importera visades, vilket kan leda till inkonsekventa data.
  _AC-11588 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/0574ac23)_
* __[Fel] Magento 2.4.7 tillåter inte produktfoton med filnamnstillägg i versaler.__
Systemet kan nu överföra produktbilder med filtillägg i versaler vilket ger en smidig process för att skapa produkter. Tidigare nekades bildöverföringar med filtillägg i versaler, vilket tvingade användarna att ändra filnamnstillägget till gemener.
  _AC-12167 - [GitHub-problem](https://github.com/magento/magento2/issues/38831) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/c8f87c25)_
* __Dold listruta i rutnät med markeringsåtgärd (t.ex. Innehåll > Element > Sidor)__
Nu har systemet fixats i alla liknande listrutor för alla stödraster.
  _AC-12319 - [GitHub-problem](https://github.com/magento/magento2/issues/38891) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/39371)_
* __[Problem] Åtgärdsvarning: Odefinierade matrisnycklar &quot;filters&quot;__
Systemet hanterar nu scenarier där en ny användare ännu inte har interagerat med bokmärken, vilket förhindrar att en odefinierad array-nyckel &quot;filters&quot;-varning loggas. Tidigare loggades den här varningen när en ny användare inte interagerat med bokmärken.
  _AC-13131 - [GitHub-problem](https://github.com/magento/magento2/issues/39013) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/38996)_
* __CSV-fil för produktimport med specialtecken misslyckas på grund av kodändringar i filen Validate.php__
Systemet validerar och importerar nu produktfiler som innehåller specialtecken på rätt sätt, vilket möjliggör en lyckad dataöverföring. Tidigare uppstod ett fel när en CSV-fil med specialtecken skulle importeras.
  _AC-13529 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/6cfb9b6b)_
* __När det maximala antalet begäranden om lösenordsåterställning har angetts till mer än 0, t.ex. 3, skickas felmeddelanden om att gränsen överskrids innan gränsen nåtts, dvs. från andra gången__
  _AC-13767_
* __Trots att maximalt antal begäranden om lösenordsåterställning har angetts till 0 ( inaktiverat) skickas felmeddelanden om att gränsen överskrids från och med 2:a gången.__
  _AC-13768_
* __Det finns ingen röd asterisk för obligatoriskt telefonnummerfält__
Tidigare röd asterisk visades inte för telefonnummer, men  telefonnummer var obligatoriskt. Nu är den röda asterisken lagrad och kan ses som ett obligatoriskt fält på telefonnumret.
  _AC-13850 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/c699c206)_
* __Det går inte att klicka på knappen Skicka order i Admin när vi försöker ändra ordningen. (intermittent)__
  _AC-14300_
* __[Problem] Ange standardindexeringsläget till &quot;schedule&quot;__
Alla nya indexerare är som standard i **[!UICONTROL Update by Schedule]** -läge.  Tidigare var standardläget **[!UICONTROL Update on Save]**. Befintliga indexerare påverkas inte. [GitHub-36419](https://github.com/magento/magento2/issues/36419)
  _AC-6975 - [GitHub-problem](https://github.com/magento/magento2/issues/36419) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/0b410856)_
* __[Issue] Släpp indexerarändringsloggtabeller i mview unsubscribe__
Systemet tar nu automatiskt bort oanvända ändringstabeller när ett index ändras från &quot;update on schedule&quot; till &quot;update on save&quot;, vilket markerar indexet som ogiltigt för att säkerställa att inga poster missas. Om du tidigare växlade ett index till&quot;update on save&quot; skulle oanvända ändringsloggtabeller i systemet utelämnas och alla ändrade index markeras som&quot;valid&quot;.
  _AC-7700 - [GitHub-problem](https://github.com/magento/magento2/issues/29789) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/25859)_
* __Ingen länk till leverans vid betalning i kassan i mobiltelefonvyn__
Systemet ser nu till att utcheckningsrubrikerna/länkarna&quot;Leverans&quot; och&quot;Granska och betalningar&quot; alltid visas ovanpå sidan i mobilvyn, vilket gör att användarna enkelt kan navigera mellan stegen och göra nödvändiga korrigeringar. Tidigare var dessa titlar/länkar dolda i mobilvyn, vilket gjorde det svårt för användarna att ta reda på det aktuella steget eller gå tillbaka till tidigare steg.
  _AC-7962 - [GitHub-problem](https://github.com/magento/magento2/issues/36856) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/36982)_
* __Försändelsekommentarer för kundorder som skapats_at returneras i +0-tidszon som inte finns i den butikskonfigurerade tidszonen__
Systemet visar nu fältet&quot;created_at&quot; korrekt från leveranskommentarer i kundens konfigurerade tidszon när kundorderfrågan används. Tidigare visades fältet&quot;created_at&quot; i tidszonen +0, oavsett kundens konfigurerade tidszon.
  _AC-8109 - [GitHub-problem](https://github.com/magento/magento2/issues/36947) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/37642)_
* __i18n:collect-frases bryter översättningsintegriteten__
Kommandot `bin/magento i18n:collect-phrases -o` samlar nu in och lägger till nya fraser från JavaScript- och .phtml-filer på rätt sätt, vilket säkerställer att översättningarna återspeglas korrekt i översättningsfilen. Tidigare kunde systemet inte inkludera flerradiga översättningsfraser från JavaScript-filer och fraser från .phtml-filer i översättningsfilen, vilket ledde till ofullständiga eller felaktiga översättningar.
  _AC-9843 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/0c53bbf7)_
* __Behörighetsproblem vid åtkomst till dynamiskt block__
Tidigare uppstod ett fel när en begränsad administratör skulle lägga till ett nytt dynamiskt block. Efter implementeringen av den här korrigeringsbegränsade administratören kan lägga till det dynamiska blocket och redigera blocket utan fel
  _ACP2E-2687_
* __Apostrofen i butiksvyns namn ersätts av &amp;#039;__
Filtren för att visa stödrastrets lagringsvy visar nu apostrofer korrekt
  _ACP2E-2787 - [GitHub-problem](https://github.com/magento/magento2/issues/38395) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/39d54c2d)_
* __Favicon-överföringen kan inte validera ICO-filer__
Filvalideringsfelet har uppdaterats till &quot;Filverifieringen misslyckades. Kontrollera inställningarna för bildbearbetning i Store-konfigurationen.&quot; Tidigare var det bara&quot;Filvalidering misslyckades&quot;.
  _ACP2E-2847 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/39d54c2d)_
* __Galleriet i PageBuilder visar en gammal miniatyrbild i stället för den nyligen överförda bilden__
Generera om förhandsvisningar av bilder för bilder som har tagits bort och överförts igen med samma namn via mediegalleriet i Page Builder-innehåll.
  _ACP2E-2957 - [GitHub-kodbidrag](https://github.com/magento/magento2-page-builder/commit/60140cd2) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/001e5188)_
* __Om en produkt sparas av en administratörsanvändare med ett annat rollomfång skrivs befintlig relaterad produktinformation över/tas bort i produkten__
Tidigare återställdes de relaterade produkterna och blev tomma när den sekundära administratören klickade på knappen Spara utan att ändra i den relaterade produkten. Efter den här korrigeringen klickar den sekundära administratören på knappen Spara och produkten återställs inte och sparas utan fel.
  _ACP2E-2978 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/3056e9cb)_
* __Det går inte att exportera fler än 200 order__
Serverns begränsningar för begärandestorleken för tidigare skickade valda ID:n har ignorerats genom att HTTP-begäran från GET till POST ändrades för att åtgärda problemet. På grund av serverbegränsningarna för GET-begäran har ett problem påträffats.
  _ACP2E-3033 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/93d50f8d)_
* __Utcheckningssidans valideringsmeddelande är felaktigt.__
Om ett obligatoriskt fält lämnas tomt, t.ex. &quot;adress&quot;, visas inte meddelandet vid valideringen på serversidan. Valideringen på klientsidan säkerställer att det obligatoriska fältfelmeddelandet visas med meddelandet&quot;This is a required field&quot;. Tidigare visades meddelandet&quot;address is required&quot; om något obligatoriskt fält lämnades tomt, förutom valideringsmeddelandet på klientsidan.
  _ACP2E-3037 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/9af794a4)_
* __Problem med mallen för återställning av lösenord med administratörsanvändaren__
Problemet har lösts med rätt nyckel, som nu inkluderar administratörens användarnamn i e-postmallen och som fyller i ämnet på rätt sätt. Tidigare berodde problemet på en inaktuell nyckel som användes.
  _ACP2E-3125 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/93d50f8d)_
* __Dubbla snedstreck i kundsegmentets URL__
Dubbla snedstreck visas inte i URL:en när du klickar på Återställ filter i rutnätet.
  _ACP2E-3149 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/8459b17d)_
* __COD är inte tillgängligt för tillåtna specifika länder__
Nu kan man få kontanter i vissa länder när det behövs och   AC-3216 fungerar som förväntat.
  _ACP2E-3171 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/6f4805f8)_
* __Det går inte att uppdatera status för anpassad skapad ordning__
&quot;Vi kan nu uppdatera beställningsstatus som skapats av egna användare, men tidigare kunde status bara ändras om den aktuella statusen var &quot;bearbetning&quot; eller &quot;bedrägeri&quot;.&quot;
  _ACP2E-3178 - [GitHub-problem](https://github.com/magento/magento2/issues/38659) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/8459b17d)_
* __Leveransadressläget uppdateras inte automatiskt__
Före korrigeringen var leveransadressens region (eller region-id) inte synkroniserad med adressfaktureringsinformationen. Nu uppdateras både leveransadressens region och region-id korrekt när faktureringsadressinformationen ändras.
  _ACP2E-3294 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/581b7ef1)_
* __Återställningsknappen fungerar inte för administratörsanvändaren Lägg till/redigera__
Tidigare fungerade inte knappen Återställ på sidan Lägg till/redigera admin-användare. På panelen Admin under System -> Behörigheter -> Alla användare fungerar nu knappen Återställ korrekt på sidan Lägg till/redigera admin-användare.
  _ACP2E-3364 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/5184c067)_
* __Magento-administratörens URL för att dirigera fel och CORS-fel__
Om den anpassade administratörsdomänen är en underdomän till huvuddomänen efter korrigeringen är administratören bara tillgänglig från den konfigurerade underdomänen.
  _ACP2E-3373 - [GitHub-problem](https://github.com/magento/magento2/issues/37663) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/3f12d152)_
* __Bruten validering för &quot;Högsta tillåtna kvantitet i kundvagn&quot;__
Tidigare utlöstes inga undantag när `Maximum Qty Allowed in Shopping Cart` skulle vara tom, men ett tomt värde accepteras inte här. När den här korrigeringen har tillämpats genereras undantag när en tom sträng skickas och produkten kan inte sparas.
  _ACP2E-3392 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/d50f6b5d)_
* __[Gränssnittsproblem för förhandsgranskning i Page Builder] Knapparna i kolumnen Page Builder är inte korrekt justerade__
Knapparna i Page Builder-kolumnerna justeras nu korrekt. Tidigare var de feljusterade i Page Builder-kolumnerna.
  _ACP2E-3408 - [GitHub-kodbidrag](https://github.com/magento/magento2-page-builder/commit/1a52ef4c)_
* __Rapporten Beställda produkter exporteras inte. 404-fel i stället.__
Export av produktbeställda rapporter till CSV och XML fungerar nu som väntat
  _ACP2E-3431 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/88660e79)_
* __TinyMCE JS-fel i konsolen efter JS-minification aktiverat med produktionsläge__
När JavaScript minification aktiverades i produktionsläge på adminpanelen visades tidigare JavaScript-fel relaterade till TinyMCE 6 i webbläsarkonsolen, vilket påverkade funktionaliteten och användarupplevelsen. Nu har problemet lösts och säkerställer att TinyMCE 6 fungerar smidigt utan att några fel genereras, även när JS-minification är aktiverat.
  _ACP2E-3457 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/56463d5e)_
* __Begär ytterligare ändringar för att slutföra AVS2E-3375-korrigeringen__
&#39;-
  _ACP2E-3459 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/d50f6b5d)_
* __Automatisk aktivering av nya ACL-behörigheter__
Nya behörigheter som läggs till i anpassade moduler ger inte längre automatiskt åtkomst till alla befintliga användarroller om de inte konfigureras explicit.
  _ACP2E-3503 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/3f12d152)_
* __Användarrapporten för administratörsåtgärdsloggen visar inte information för adminhtml_user_delete__
adminhtml_user_delete loggar nu viktig information korrekt. Tidigare genererades inga loggar för borttagning av användare.
  _ACP2E-3509 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/4de008a9)_
* __Kundregel med leveransvillkor gäller inte vid beställning från administratör__
Om kundvagnsprisregeln tidigare har en rabatt på leveranssätt med kupongen, kan den inte tillämpas via administratörsgränssnittet. När den här korrigeringen har tillämpats tillämpas rabatten på kundprisregeln med en kupong för en viss leveransmetod från administratörsgränssnittet.
  _ACP2E-3536 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/a52ff98f) - [GitHub-kodbidrag](https://github.com/magento/inventory/commit/11ce816b)_
* __[FRESH] HEX-koden uppdateras inte korrekt i SWATCH__
HEX-kod som användaren anger manuellt i färgväljaren för visuell färgruta ändras inte längre av systemet. Tidigare hade vissa HEX-koder haft mindre justeringar på grund av konverteringsfel mellan färgmodeller.
  _ACP2E-3559 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/344fce23) - [GitHub-kodbidrag](https://github.com/magento/inventory/commit/1ef984c0)_

### Administratörsgränssnitt, B2B

* __B2B-inloggning som kundhuvud har fortfarande Magento-märkning__
Tidigare visas i butiksrubriken&quot;Du är nu ansluten som &lt;kundnamn> på &lt;butiksnamn>&quot; med Magento-märkning. Det är nu fixat och rubriken visas med ADOBE branding.
  _AC-13628 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/96dec499)_

### Administratörsgränssnitt, katalog

* __Det går inte att ändra befattningar för kategoriprodukterna på den tillåtna webbplatsen som en begränsad administratörsanvändare__
Tillåt en begränsad administratörsanvändare att lägga till och sortera produkter i en kategori i rotkategorin som tilldelats under en begränsad webbplats.
  _ACP2E-2708_

### Administratörsgränssnitt, betalningssätt, beställning

* __Transaktionsauktorisering visas inte på fliken Transaktion efter ordningen för smarta PayPal-knappar__
Systemet visar nu transaktionsauktoriseringen korrekt på fliken Transaktion efter att en order har placerats med smarta PayPal-knappar. Auktoriseringstransaktionen visades inte på fliken Transaktion när du klickade på Auktorisera och ingen ny transaktion av typen Authorization skapades.
  _AC-13520 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/6cfb9b6b)_

### Administratörsgränssnitt, prestanda

* __Efter uppdatering till 2.4.5-p8 500 inträffar fel när ordningen skapas från admin__
Tidigare gick det inte att göra en beställning från administratören när HTML-miniatyr aktiverades. Nu när HTML minification är aktiverat kan du beställa från administratören.
  _ACP2E-3169 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/b21e5d91)_

### Administratörsgränssnitt, leverans

* __Kupongkoden uppdateras inte i   Kolumnen &quot;Använd tid&quot; på fliken Hantera kupongkoder om en order har flera leveranser.__
Tidigare uppdaterades inte kupongkodsantalet i kolumnen &quot;Tid använd&quot; på fliken Hantera kupongkoder när en order placerades med flera leveranser. Nu visas rätt antal i både &quot;Använd tid&quot; och återspeglar önskade värden vid flera leveranser.
  _ACP2E-2519 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/4745100c)_

### Administratörsgränssnitt, mellanlagring och förhandsvisning

* __[Cloud] Om du tar bort en mall med saknade bilder tas puben/media bort__
Tidigare till den här korrigeringen togs mappen pub/media bort om namnet på förhandsvisningsbilden saknades för en sidbyggarmall. Efter korrigeringen tas bara mallen bort och förhandsvisningsbilden tas bort om den hittas.
  _ACP2E-3424 - [GitHub-kodbidrag](https://github.com/magento/magento2-page-builder/commit/0986853b)_

### Analyser/rapporter

* __Google Analytics CSP-fel https://region1.analytics.google.com__
Systemet tillåter nu anslutningar till https://region1.analytics.google.com&#39; när Google Analytics är aktiverat, vilket förhindrar CSP-fel (Content Security Policy). Tidigare skulle det resultera i fel i CSP-konsolen om Google Analytics kunde aktiveras och webbplatsen från EU på grund av en vägran att ansluta till https://region1.analytics.google.com&#39;.
  _AC-9922 - [GitHub-problem](https://github.com/magento/magento2/issues/37750) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/38991)_
* __Avancerad rapport fungerar inte__
Systemet har nu stöd för generering av avancerade rapporteringsdatafiler för extra stora datauppsättningar genom att ladda in och skriva rapporter i grupper om 10 000. Tidigare kunde inte modulen för avancerad rapportering generera datafiler för extra stora datauppsättningar, vilket orsakade felen&quot;MySQL-servern har försvunnit&quot; under körningen av cron-jobbet analytics_collect_data.
  _ACP2E-2570 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/a12063bd)_
* __Admin Ordered Products Rapporterar problem med synlighet för datumintervall.__
Användaren kan välja valfritt datum från rapporten över beställda produkter. När en tabell har uppdaterats återställs TO-datumet när du väljer FROM-datumet.
  _ACP2E-3080 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/6f4805f8)_
* __Felaktiga kurvhuvuden gör att `newrelic:create:deploy-marker` inte fungerar__
Systemet formaterar nu curl Headers korrekt, så att kommandot `newrelic:create:deploy-marker` kan skapa en distributionsmarkör i New Relic. Tidigare kunde felaktiga rullrubriker inte skapa en distributionsmarkör i New Relic.
  _ACP2E-3096 - [GitHub-problem](https://github.com/magento/magento2/issues/37641) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/6a185204)_
* __GTM saknar addToCart-händelse i dataLayer för konfigurerbar produkt med anpassat alternativ__
Tidigare utlöstes inte händelsen addToCart för konfigurerbara produkter. Händelsen läggs nu till korrekt i GTM-datalagrets variabel.
  _ACP2E-3146_
* __NewRelic-webbläsarövervakning av inlineJS-skript orsakar CSP-fel__
Skript för övervakning av NewRelic Browser injiceras nu av programmet i stället för APM-agenten för kompatibilitet med CSP (Content Security Policy). Tidigare var de NewRelic Browser Monitoring-skript som injicerades av APM-agenten inte kompatibla med CSP och orsakade att skripten inte kördes.
  _ACP2E-3183 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/66dea0de)_
* __INSERT-frågor i registret sales_bestsellers_aggregate_day blir långsamma i projekt med stor försäljningsordervolym__
Tidigare tog det lång tid att generera en stor mängd monterade order i den dagliga rapporten från de bästsäljarna. Nu genereras rapporten i tid.
  _ACP2E-3189 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/7377de59)_
* __Orderrapporter visar fel valutasymbol__
Valutasymbolen för orderbelopp i orderrapporten togs felaktigt från valuta/alternativ/bas. Det har nu korrigerats till att använda valuta/alternativ/standard för korrekt rapportering.
  _ACP2E-3276 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/fd5cf3af)_
* __[Cloud] Felaktiga beräkningar i kuponganvändningsrapport__
Försäljningssumman i rabattrapportrutnätet beräknas nu korrekt genom att både&quot;Rabattbelopp&quot; och&quot;Momskompensationsbelopp för fraktrabatt&quot; läggs till. Tidigare saknades dessa belopp i beräkningen, vilket ledde till avvikelser mellan försäljningssumman och försäljningsorderdata.
  _ACP2E-3302 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/d75cff27)_
* __Problem med delat &lt;project_id>/var/tmp&quot;__
AnalysdataExportera temporära filer använder systemkatalogen tmp, vilket är mer lämpligt för frekvent åtkomst och ändringar. För att undvika kollisioner om flera instanser körs på samma server uppdaterades tmp-sökvägen till att använda en instanss unika ID
  _ACP2E-3339 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/a4cf5e62)_

### Analys/rapportering, B2B

* __B2B - platskartan innehåller produkter/kategorier som inte har tilldelats den delade katalogen__
Begränsa de kategorier och produkter som genereras av webbplatskartan till de kategorier och produkter som endast tilldelats den offentliga delade katalogen och/eller behörighetsinställningarna för katalogkategorin.
  _ACP2E-2300 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/ea79f7dd)_

### Analytics/Reporting, Cloud

* __Magento ignorerar de flesta New Relic cron-transaktioner #34108__
AC rapporterar korrekt kundjobbrelaterade transaktioner till NewRelic. Tidigare visades vissa kundjobbrelaterade transaktioner som&quot;OtherTransaction/Action/unknown&quot; i NR
  _ACP2E-3067 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/35b1b1da)_
* __Mått i NR kan vara vilseledande för bakgrundstransaktioner - Uppföljning av ACP2E-3067__
För bakgrundstransaktioner (cron) används det New Relic-programnamn som definieras i konfigurationsinställningarna
  _ACP2E-3187 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/ec7e32a9)_

### B2B

* __2.4.8-beta102 package Enterprise Edition fungerar inte med programundantag__
  _AC-13501_
* __Produkter som tilldelats en delad katalog återspeglas inte i frontdelen när partiellt index körs__
Produkter som har tilldelats en delad katalog via REST API är nu omedelbart synliga i butiken när partiell indexering är klar. Tidigare var produkterna bara synliga efter en fullständig omindexering.
  _ACP2E-2139 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/7377de59)_
* __[Molnet] Prisvisningen i mobil- och datorversionen är inte densamma i&quot;Mina offerter&quot;__
Raden Inkludera moms som inte behövs visas inte längre i Negotiable Quote när avsnittet Katalogens totala pris har utökats.
  _ACP2E-2873_
* __Onödiga kantlinjer i avsnittet Mina beställningar__
Tidigare skapades ytterligare en behållare (orderreferenser) som tillämpade ytterligare CSS-klasser, vilket orsakade att onödiga kantlinjer visades under ordernumret i delen Mina beställningar, som inte visas nu.
  _ACP2E-3044 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/9af794a4)_
* __sales_clean_quotes cron tar bort offerter från till ännu godkända inköpsorder__
Offerter som används i inköpsorder kommer nu inte att tas bort av cron-jobbet sales_clean_quotes
  _ACP2E-3247 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/581b7ef1)_
* __Knappen Montera beställning försvinner i inköpsorderinformationen__
Ett problem har korrigerats där knappen Montera order doldes för godkända inköpsorder när en produktvariant hade ett minsta antal på kortet angivet
  _ACP2E-3465_
* __[CLOUD] Ingen sådan entitet med ID = 0 med b2b-modulen__
Inloggad användare kan lägga till produkten i kundvagnen när funktionen för delad katalog är aktiverad.
Tidigare tillagd produkt i kundvagn resulterade i felet &#39;ingen sådan entitet med ID = 0&#39;
  _ACP2E-3474_
* __Inget felmeddelande visas för våra Stock-produkter när massutskick läggs till från rekvisitionslistan__
Före korrigeringen visades ett meddelande om att åtgärden lyckades, oavsett hur många produkter som inte kunde läggas till i kundvagnen. Nu visas separata meddelanden för produkter som lagts till i kundvagnen och för produkter som inte godkänts.
  _ACP2E-3562_
* __Problem med SKU-uppdateringar efter schemalagda uppdateringar som orsakar felaktiga produktbehörigheter (-2 Neka)__
Om du ändrar en produkts SKU med tidigare schemalagda uppdateringar blir produkten inte längre tillgänglig för de kunder som har delat produktkatalog.
  _ACP2E-3628_

### B2B, katalog

* __Produkter/kategorier som visas under omindexering vid användning av NoDDL och kategoribehörigheter__
Undvik att visa i butiksbegränsade kategorier och deras innehåll medan katalogbehörighetsindexering utförs.
  _ACP2E-2860_

### B2B, ramverk

* __Filtrering av företagsrutnät och försök sedan att exportera stödraster-CSV misslyckas och orsakar undantag__
Systemet tillåter nu en lyckad CSV-export av företagsrutnätsdata på adminpanelen, även när filter som &quot;Utgående balans&quot; och &quot;Företagstyp&quot; tillämpas. Om du tidigare tillämpade vissa filter och försökte exportera stödrasterdata skulle det resultera i ett fel och ett undantag genereras.
  _AC-9607 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/44cef3a9)_

### B2B, GraphQL

* __[Cloud] Det går inte att ange custom_attributes när ett företag skapas över grafikanropet__
Efter korrigeringen kan du ange attributet &quot;custom_attributes&quot; för företagsadministratören när företaget skapades med hjälp av en graphql-begäran.
  _ACP2E-3391_

### Braintree

* __Knappen för expressincheckning av administratör har inaktiverats.__
  _AC-14293_
* __Betala via LPM__
Systemet återger nu LPM (Local Payment Methods) korrekt vid första inläsningen, även när en inloggad kunds leverans- och faktureringsadresser inte matchar, vilket ger en smidig utcheckningsprocess. Tidigare var det fel på kundens leverans- och faktureringsadresser som förhindrar LPM-återgivning, vilket kan orsaka störningar vid utcheckningen.
  _BUNDLE-3367_
* __Kan konfigureras med virtuell som underordnad produkt__
Systemet tillåter nu expressbetalningsmetoder för konfigurerbara produkter som har en virtuell underordnad produkt, vilket ger en smidig utcheckningsprocess. Tidigare var expressbetalningsmetoder inte tillgängliga när en konfigurerbar produkt med en virtuell underordnad produkt lades till i kundvagnen.
  _BUNDLE-3368_
* __CVV-verifieringen misslyckades.__
  _BUNDLE-3369_
* __Vaulting Via kontoområdet Issues 247__
Systemet tillåter nu att kunder sparar ny kortinformation eller PayPal-kontoinformation på flera webbplatser utan att stöta på auktoriseringsfel. Tidigare kunde kunderna inte spara nya betalningsmetoder på olika webbplatser och fick ett felmeddelande om auktorisering.
  _BUNDLE-3370_
* __Leverera till en adress från ett annat land__
Systemet tillåter nu att transaktioner behandlas utan fel när de skickas till en adress från ett annat land, vilket ger en smidig utcheckningsprocess. Tidigare skulle försök att leverera till en adress från ett annat land resultera i konsolfel, trots att det inte finns några synliga fel på klientsidan.
  _BUNDLE-3371_
* __Kreditkort - Avsökningsfunktion__
Systemet hanterar nu riggningen av Braintree PayPal-komponenter korrekt när en kund går tillbaka från betalningssidan till leveranssidan, vilket förhindrar fel och säkerställer att PayPal Express-knapparna återges korrekt. Tidigare uppstod ibland ett fel när Braintree PayPal-komponenterna skulle kapas ned när du navigerade tillbaka till leveranssidan från betalningssidan.
  _BUNDLE-3372_
* __Leveransåteranrop för PayPal Express__
Systemet visar nu korrekt tillgängliga leveransmetoder i PayPal Express modal, vilket gör att kunderna kan välja leveranssätt innan de går vidare till granskningssidan eller slutför transaktionen. Tidigare fanns det inga leveransmetoder att välja mellan i PayPal Express modal, vilket innebar att kunderna måste välja en leveransmetod på en separat granskningssida innan de kunde slutföra transaktionen.
  _BUNDLE-3373_

### Paket

* __Antal felmeddelanden för Storefront-kryssruteverifiering som är fler än 1__
Systemet visar nu endast ett valideringsfelmeddelande när användaren klickar på knappen Lägg till i kundvagnen utan att markera några kryssrutealternativ för en paketerad produkt. Tidigare visades flera valideringsfelmeddelanden för varje omarkerad kryssruta.
  _AC-10826 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/3ea26621)_
* __Magento Exception utlöstes i vissa ordningsrelaterade testfall__
Systemet hanterar nu steget sendGuestPaymentInformation korrekt i olika testfall, vilket förhindrar att Magento-undantag genereras. Tidigare inträffade dessa undantag på grund av en null-betalningsmetod, vilket orsakade fel i flera testfall.
  _AC-13321_

### Kort och utcheckning

* __Undantaget hanteras inte korrekt när en produkt läggs till i kundvagnen på produktsidan__
Systemet hanterar nu undantag korrekt när en produkt läggs till i varukorgen från jämförelseproduktsidan, vilket visar ett meddelandehanteringsmeddelande i styrenheten. Tidigare skulle ett undantag resultera i att en JSON-kodad sida returneras i stället för att fångas upp och hanteras korrekt.
  _AC-10660 - [GitHub-problem](https://github.com/magento/magento2/issues/38200) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/38257) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/0c53bbf7)_
* __GTag skickar inte transaktionspriser och summor.__
Systemet skickar nu transaktionspriser och summor korrekt till Google Tag när GTag är aktiverat, vilket ger korrekt spårning av e-handelsdata. Tidigare skickades valutan felaktigt som en del av&quot;alla&quot;-beställningarna, i stället för att kopplas till den enskilda ordern.
  _AC-10698 - [GitHub-problem](https://github.com/magento/magento2/issues/37348) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/37504) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/37349)_
* __[Utgåva] [Utcheckning] Beroendedirektiv har uppdaterats i mallen för misslyckade betalningar__
Systemet utelämnar nu leveransadressen och leveransmetoden korrekt från den misslyckade betalningsmallen för virtuella produkter, vilket säkerställer att endast relevant information inkluderas i e-postmeddelandet. Tidigare innehöll den misslyckade e-postbetalningen för virtuella produkter felaktigt leveransadressen och leveransmetoden.
  _AC-11641 - [GitHub-problem](https://github.com/magento/magento2/issues/32781) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/32511)_
* __Magento 2-inloggning i kassan med befintlig kund ger konsolfel i Firefox-webbläsaren__
Systemet tillåter nu användare att logga in under utcheckningsprocessen utan att upptäcka konsolfel i webbläsaren Firefox. Tidigare uppstod ett konsolfel i Firefox om du försökte logga in som en befintlig kund under utcheckningen.
  _AC-11717 - [GitHub-problem](https://github.com/magento/magento2/issues/38557) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/39509)_
* __[Problem] Regression för försäljningsregler i 2.4.7__
Systemet validerar nu försäljningsreglerna korrekt och förhindrar att en kupongkod tillämpas på en kundvagn när produktvillkoret inte matchar något produktnamn. Tidigare kunde en försäljningsregel tillämpas och en rabatt ges på fraktbeloppet även när produktvillkoret inte matchade något produktnamn.
  _AC-11876 - [GitHub-problem](https://github.com/magento/magento2/issues/38671) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/0574ac23)_
* __[Utgåva] Förs.regel, CartFixed-beräkning: felaktigt rabattbelopp__
Nu beräknas rabattbeloppet korrekt för försäljningsregler med fasta kundvagnsbelopp, vilket säkerställer korrekta rabatter oavsett ändringar i kundvagnsartiklar. Tidigare kunde rabattbeloppet variera felaktigt när artiklar i kundvagnen ändrades, vilket ibland resulterade i betydligt större rabatter än förväntat.
  _AC-11914 - [GitHub-problem](https://github.com/magento/magento2/issues/38694) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/581b7ef1)_
* __[Utgåva] Inläsaren blockerar leveransmetoderna efter att postkoden har ändrats, regler för validering av fraktsatser__
Systemet hanterar nu anpassade leveransmetoder utan regler för validering av fraktsatser, vilket säkerställer att inläsaren inte blockerar leveransmetoderna efter att postkoden har ändrats i leveransadressen under utcheckningen. Om du ändrar postnumret i leveransadressen under utcheckningen skulle det medföra att inläsaren blockerar leveransmetoderna och inte försvinner när anpassade leveransmetoder utan regler för utcheckning av fraktsatser används.
  _AC-11993 - [GitHub-problem](https://github.com/magento/magento2/issues/38742) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/1bafc571)_
* __Funktionen för kupongkod fungerar inte som den ska på utcheckningssidan för Magento 2.4.7__
Systemet aktiverar nu rabattkodens/kupongens inmatningsfält på kassasidan för virtuella och nedladdningsbara produkter, så att användarna kan tillämpa rabattkoder som förväntat. Tidigare inaktiverades rabattkoden/kuponginmatningen och knappens titel visades som&quot;Avbryt kupong&quot;, vilket förhindrar användare att använda rabattkoder.
  _AC-12170 - [GitHub-problem](https://github.com/magento/magento2/issues/38826) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/1bafc571)_
* __Kryssrutan Villkor tillåter inte HTML i butiken__
Systemet har nu stöd för HTML-formatering i kryssrutan &quot;Villkor&quot; i butiken, vilket gör det enklare att anpassa och läsa. Tidigare visades kryssrutetexten i oformaterad text, och eventuella HTML-taggar som användes ignorerades.
  _AC-12479 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/6cfb9b6b)_
* __Regeln för kundvagn som skapats för inloggad användare tillämpas felaktigt för användare som inte är inloggad__
Systemet tar nu bort kundvagnsprisregeln för inloggade användare korrekt när de loggas ut automatiskt på grund av att cookie-filen har upphört att gälla, vilket säkerställer att rabatten inte tillämpas på användare som inte är inloggade. Tidigare tillämpades kundvagnsprisregeln även när användaren var utloggad, vilket resulterade i att en felaktig rabatt tillämpades på icke-inloggade användare.
  _AC-12541 - [GitHub-problem](https://github.com/magento/magento2/issues/38944) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/7d5e3906)_
* __[Utgåva] [FUNKTION] Prestandaoptimering av stora kundvagnar genom att förhindra..__
Systemet optimerar nu prestanda för stora kundvagnar genom att förhindra dubbla getActions-anrop, vilket ökar hastigheten och effektiviteten i kundvagnsdriften. Tidigare anropades funktionen getActions flera gånger för en kundvagn med flera artiklar, vilket saktade ned systemets prestanda.
  _AC-13302 - [GitHub-problem](https://github.com/magento/magento2/issues/39292) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/39290)_
* __Presentregisterprodukten visas inte korrekt__
  _AC-13797_
* __Presentregisterprodukten visas inte korrekt__
  _AC-13841_
* __Översättningsmoms i adressrenderaren__
Systemet tillåter nu översättning av texten&quot;moms&quot;,&quot;T&quot;,&quot;F&quot; i adressrenderarna, vilket gör att användarna kan översätta dessa villkor till butikens specifika språk. Tidigare var dessa villkor inte översättningsbara, vilket tvingade användarna att använda en lösning.
  _AC-8103 - [GitHub-problem](https://github.com/magento/magento2/issues/36942) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/36943)_
* __Duplicera order med samma offert-ID samtidigt med liten tidsskillnad__
Ett problem har korrigerats när Adobe Commerce-kunder påträffade dubblettorder med samma QuoteID
  _ACP2E-2055 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/f89a447e)_
* __Beständig kundvagn rensades under utcheckningssteget__
Efter korrigeringen avslutas inte den beständiga sessionen om du väljer betalningsmetod under utcheckning när du inte är inloggad.
  _ACP2E-2470 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/a4fbf702)_
* __Otilldelad produkt läggs till i kundvagnen__
För de olika butikerna kan man tidigare beställa produkter från den andra butiken. När korrigeringen har tillämpats på samma butik kan samma omfattningsprodukt omordnas när kundkontoresursen är aktiverad
  _ACP2E-2518 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/f89a447e)_
* __I admin uppdateras inte kundvagnen till vänster när du väljer artiklar och Flytta till kundvagn till höger__
&quot;Kundvagnen&quot; till vänster uppdateras när du väljer artiklar och &quot;Flytta till kundvagn&quot; till höger på adminsidan. Tidigare fungerade inte den här funktionen eftersom de omformade varukorgsobjekten inte blev tomma från sessionen.
  _ACP2E-2620 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/39d54c2d)_
* __[Molnet] Försäljningsregel tillämpas inte på första beställningen av Multi-Shipping__
Efter korrigeringen visas rabatten korrekt för varje order i samma flerleveranskurs.
  _ACP2E-2646 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/f89a447e)_
* __[Cloud] Parallella produktionsförfrågningar om att lägga till samma produkt i kundvagnen resulterar i två separata objekt i kundvagnens rest-API__
Systemet bearbetar nu flera parallella förfrågningar korrekt för att lägga till samma produkt i varukorgen i en enda radartikel, vilket förhindrar att separata radartiklar för samma SKU skapas. Tidigare skulle parallella begäranden om att lägga till samma produkt i kundvagnen via REST API resultera i flera radobjekt för samma SKU.
  _ACP2E-2664 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/f89a447e)_
* __Problem med beställning från presentregistret Magento 2.4.4 Enterprise/Commerce__
Problemet med att det inte gick att köpa en produkt från ett presentregister har lösts så att man kan lägga order och uppdatera presentregistret på rätt sätt. Tidigare inträffade ett fel när en beställning från ett presentregister skulle göras, vilket förhindrar att köpet slutförs.
  _ACP2E-2676 - [GitHub-problem](https://github.com/magento/magento2/issues/35432)_
* __Det går inte att skicka cookien. Storlek på &#39;image-messages&#39; vid försök att ändra ordning på__
Omsorteringsprocessen genererar inga egna fel just nu. Den förlitar sig på varukorg som listar inbyggda artikelkontroller.
  _ACP2E-2704 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/ba25af8a)_
* __Standardleveransadress har inte valts vid utcheckning__
Standardleveransadress väljs nu för händelse i samband med aktiverad adresssökning.
  _ACP2E-2798 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/7e0e5582)_
* __[CLOUD] problem med addProductsToCart-API:t för grafer med anpassat alternativ__
GraphQL tillför korrekt samma produkt i varukorgen med olika anpassade alternativ
  _ACP2E-2897 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/c971859e)_
* __[Regler för relaterade produkter i molnet] fungerar inte när butiksvyn ändras__
Problemet har korrigerats genom att bekräfta att värdet för den anpassade egenskapen har tagits emot på kundvagnssidan. Tidigare hämtades det inte korrekt när man växlade mellan butiker på kundvagnssidan.
  _ACP2E-2917_
* __Flera adresser har lagts till i kontot vid utcheckning som ny kund__
Systemet sparar nu bara en ny kundadress en gång om ordern inte kunde skapas, vilket förhindrar att flera identiska adresser skapas om det skulle uppstå fel på orderplaceringen. Tidigare sparade systemet en ny adress varje gång ett orderplaceringsförsök gjordes, oavsett om ordern skapades eller inte.
  _ACP2E-2923 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/001e5188) - [GitHub-kodbidrag](https://github.com/magento/inventory/commit/2ebcef39)_
* __Om du ändrar ordning på kundorder via gästbeställningsformulär skapas en tom kundvagn__
Tidigare omdirigerades kunden till inloggningssidan när en ombeställning gjordes via sidan Beställningar och Returer. När den här korrigeringen har tillämpats omdirigeras den registrerade kunden korrekt till sidan Visa kundvagn när en ombeställning görs. Flödet fungerar på samma sätt som gästkunder.
  _ACP2E-3004 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/6a185204)_
* __Administratörsanvändare med begränsade rollresurser kan inte visa kundvagnar__
Tidigare kunde den begränsade administratören inte se den övergivna kundvagnen på adminpanelen för en associerad webbplats. När den här korrigeringen har tillämpats kan administratören se den övergivna kundvagnen på adminpanelen.
  _ACP2E-3025 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/d1f7dc95)_
* __[Cloud] snabbeställa stora mängder SKU-prestanda__
Utcheckningsprestanda har förbättrats när attribut som används i kundprisregler inte finns för alla produkter och när funktionen för att ange lägsta kampanjpris är aktiverad.
  _ACP2E-3176 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/66dea0de)_
* __Duplicerade objekt i varukorgen__
Systemet bearbetar nu flera parallella förfrågningar korrekt för att lägga till samma produkt i varukorgen i en enda radartikel, vilket förhindrar att separata radartiklar för samma SKU skapas. Tidigare skulle parallella begäranden om att lägga till samma produkt i varukorgen på Storefront resultera i flera radobjekt för samma SKU.
  _ACP2E-3211 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/66dea0de)_
* __E-postbekräftelse för utcheckningsorder skickas till e-postmeddelanden som anges i Förnamn/Efternamn__
E-postbekräftelse för utcheckningsorder, som tidigare skickades när ett e-postliknande mönster angavs i fälten Förnamn och Efternamn, skickas inte längre.
  _ACP2E-3296 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/5184c067)_
* __Utcheckningsadressens formulär uppdateras med fel adress__
shippingAddressFromData sparas nu i det lokala lagret per webbplats. Tidigare kunde en adress från fel webbplats fyllas i automatiskt i leveransadressformuläret vid utcheckning om en butikskod användes i URL:en och utcheckningen initierades från flera webbplatser under samma gästsession.
  _ACP2E-3402 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/078c387e)_
* __[CLOUD] Utcheckningen behåller inte den valda faktureringsadressen när adresssökning är aktiverat__
Utcheckningssidan behåller nu den valda faktureringsadressen när adresssökning är aktiverat. Tidigare om&quot;Antal kundadresser gräns&quot; har konfigurerats till 1 och kunden har fler än en adress, kommer den valda faktureringsadressen att försvinna när sidan har lästs in igen.
  _ACP2E-3405_
* __Presentkortsprodukt | Kundsammanfogning sammanfogar presentkort__
Presentkortsprodukter som nu sammanfogats korrekt i kundvagnen
  _ACP2E-3407 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/88660e79)_
* __Kontarts beständighet respekteras inte vid utloggning__
Lagt till funktioner som saknas Kom ihåg mig från kundinloggning till popup-fönstret för autentisering och utcheckning av inloggningar.
  _ACP2E-3415 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/344fce23)_
* __Befintliga offertdata uppdateras inte/visas inte. Skapa i stället en ny offertpost när trigger_recept = 1__.
Kundens kundvagnsartiklar försvinner inte längre om en produkt tas bort efter att den lagts till i kundvagnen.
  _ACP2E-3488 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/1984c61c)_
* __När ett presentregisterobjekt köpts ser kunden objekt som inte finns i deras register__
Presentregisteruppdateringen innehåller inte längre artiklar som inte tillhör presentregistret.
  _ACP2E-3495_
* __[Cloud] Problem med bekräftelsepopup-menyn Ta bort alla kundvagnsobjekt utan bekräftelse__
Om du klickar på knappen &quot;Ta bort alla&quot; för produkter som behöver åtgärdas visas ett bekräftelsefönster som kontrollerar att objekten bara tas bort med din bekräftelse. Tidigare togs objekt bort omedelbart utan någon bekräftelse
  _ACP2E-3510_
* __[CLOUD] Ordna om knappfunktioner__
Om du beställer om en order från administratörsområdet läggs produkter med lager till i offerten, även om det finns produkter i den ursprungliga ordern som inte har något lager längre. Före korrigeringen lades inga produkter till i den nya offerten om produkten utan lager fanns i den ursprungliga ordern.
  _ACP2E-3618 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/a52ff98f)_
* __Sökarkiv fungerar inte med postnummer__
Sökningen efter hämtningsplatser efter postnummer fungerade inte korrekt för nederländska lokaliseringar. Efter korrigeringen kommer sökningen efter hämtningsplatsen att ge resultat baserat på postnummer.
  _ACP2E-3622 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/344fce23)_

### Kort och utcheckning, utcheckning/utcheckning av en sida

* __[Slumpmässigt fel] E-postfältet återges inte eller tar lång tid att visa på sidan för utcheckning, leverans eller betalning__
Commerce återger nu fältet **[!UICONTROL Email]** på utchecknings- och betalningssidorna som förväntat. Tidigare fanns inte det här fältet eller så renderades det långsamt.
  _AC-9386 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/e1babcfd)_

### Kort och utcheckning, beställ

* __Datumväljaren för produkt med flera anpassningsbara alternativ med datumfält som inte fungerar när en beställning från administratören placeras__
Datumväljaren visas nu korrekt för alla datumfält när du konfigurerar en produkt med flera anpassningsbara datumalternativ i processen för att skapa administratörsorder. Tidigare visades datumväljaren bara för det första datumfältet, och återstående fält lämnades utan datumväljare.
  _ACP2E-3097 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/b21e5d91)_

### Kundvagn och utcheckning, leverans

* __Direktköp -&quot;billigaste leveransen&quot; brutet för konfigurerbara produkter__
Funktionen Direktköp valde felaktigt det dyrare alternativet för leverans i butik för konfigurerbara produkter i stället för den billigaste metoden med schablonbelopp. Med den här programfixen kan du säkerställa att rätt leveranssätt väljs baserat på det faktiska priset.&quot;
  _AC-12119 - [GitHub-problem](https://github.com/magento/magento2/issues/38811) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/38819) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/29fe9097)_

### Katalog

* __Rensning av cron_schedule-databastabellen rensar inte jobb som inte finns.__
Systemet rensar nu automatiskt databastabellen cron_schedule och tar bort poster för jobb som inte längre finns i systemet. Detta ger optimala prestanda genom att ett minimalt antal rader i tabellen bevaras. Tidigare rensades inte poster för jobb från inaktiva eller borttagna moduler, vilket ledde till onödig datainsamling i tabellen cron_schedule.
  _AC-10910 - [GitHub-problem](https://github.com/magento/magento2/issues/38217) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/38693)_
* __Nivåpriset tas inte bort från den konfigurerbara produkten__
Systemet tar nu bort en produkts nivåpris korrekt när den konverteras från en enkel produkt till en konfigurerbar produkt, vilket säkerställer korrekt prisvisning i klientledet. Tidigare togs inte nivåpriset bort för en konfigurerbar produkt när en produkt konverterades från en enkel produkt till en konfigurerbar produkt, vilket ledde till en felmatchning av det visade priset.
  _AC-10953 - [GitHub-problem](https://github.com/magento/magento2/issues/38390) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/38427)_
* __Kategoribeskrivning WYSIWYG är tomt i en icke-standardbutiksgranskning__
Systemet sparar nu och visar kategoribeskrivningen korrekt i WYSIWYG Editor när en kategori redigeras på butiksvynivå. Tidigare visades WYSIWYG-redigeraren som tom när en kategoribeskrivning sparades på butiksvynivån.
  _AC-11804 - [GitHub-problem](https://github.com/magento/magento2/issues/38622) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/38623)_
* __Det går inte att ordna om konfigurerbara produkter med en kryssruta markerad med anpassat alternativ__
Systemet bearbetar nu omsorteringen av konfigurerbara produkter korrekt med ett enda anpassat kryssrutealternativ, vilket möjliggör att korgen kan skapas. Tidigare uppstod ett fel när sådana produkter skulle sorteras om och artiklarna kunde inte läggas till i kundvagnen.
  _AC-11970 - [GitHub-problem](https://github.com/magento/magento2/issues/38736) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/1d144bce)_
* __[Problem] Åtgärda formuleringen för filterobjektet vid navigering i lager__
Systemet använder nu orden&quot;item&quot; och&quot;items&quot; i det lageruppbyggda navigeringsfilterobjektet, vilket gör filterbeskrivningarna tydligare och exaktare. Tidigare användes dessa ord felaktigt, vilket kan skapa förvirring för användare som navigerar i filteralternativen.
  _AC-12076 - [GitHub-problem](https://github.com/magento/magento2/issues/38789) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/37852)_
* __Formatet Datum och tid för det anpassade alternativet fungerar inte__
Systemet använder nu det konfigurerade datumformatet korrekt på anpassade produktalternativ av typen Datum, vilket säkerställer att datumformatet visas korrekt på frontsidan. Tidigare speglade inte ändringar i datumformatskonfigurationen på frontend för anpassade produktalternativ av typen Date.
  _AC-12164 - [GitHub-problem](https://github.com/magento/magento2/issues/32990) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/38925)_
* __Listrutealternativ saknas__
Alla värden visas nu korrekt i listrutan när du skapar ett nytt attribut med fler än 20 värden. Tidigare visades bara de första 20 värdena eller något annat av de valda sidvärdena, vilket medförde att de återstående värdena saknades.
  _AC-13068 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/47b448e2)_
* __[Problem] Använd aktuellt lager-ID för kategorins körtidscache__
Systemet använder nu korrekt det aktuella lagrings-ID:t för kategorins körtidscache, vilket förhindrar att data åsidosätts när emulering används eller anpassad kod sparar kategorin i olika butiker. Tidigare kunde objektet som lagrats i körningsmiljön ha kommit från fel butik, vilket ledde till åsidosättande av data.
  _AC-13296 - [GitHub-problem](https://github.com/magento/magento2/issues/39310) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/36394)_
* __bin/magento sampledata:deploy —no-update returnerar ett undantag__
Systemet accepterar nu ett booleskt värde korrekt när alternativet —no-update används i kommandot sample data:deploy, vilket förhindrar fel under distributionen av exempeldata. Tidigare uppstod ett fel när det här kommandot användes eftersom ett heltalsvärde felaktigt förväntades.
  _AC-13324 - [GitHub-problem](https://github.com/magento/magento2/issues/39344) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/39345)_
* __[Problem] Korrigera användning av EAV-cachetyp__
Systemet använder nu EAV-cachetypen korrekt på alla relevanta platser, vilket ger en konsekvent och effektiv datacachning. Tidigare användes EAV-cachetypen inte konsekvent, vilket ledde till ineffektivitet och inkonsekvenser i datacachningen.
  _AC-13355 - [GitHub-problem](https://github.com/magento/magento2/issues/32322) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/31264)_
* __Katalogsökning med tomma data går till sökresultatsidan[ 2.4.dev-grenen]__
Systemet behåller nu användare korrekt på sidan Avancerad sökning och visar ett felmeddelande när de försöker utföra en sökning utan att ange några data. Tidigare omdirigeras användare till sidan Avancerad sökning i katalog med ett meddelande som uppmanar dem att ändra sökningen.
  _AC-13596 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/6cfb9b6b)_
* __[Problem] Produktlayout baserad på attribute_set__
Systemet tillåter nu att produktlayouten justeras baserat på attributuppsättningen, vilket ger ett mer praktiskt och effektivt sätt att hantera produktvisningen i klientbutiken. Tidigare kunde layouten bara justeras av SKU eller efter produkttyper, vilket inte alltid var praktiskt för många produkter eller specifika artiklar.
  _AC-13622 - [GitHub-problem](https://github.com/magento/magento2/issues/38790) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/36244)_
* __Unik nyckel saknas i tabellen eav_attribute_option_value__
Systemet innehåller nu en unik nyckel för kolumnerna &#39;option_id&#39; och &#39;store_id&#39; i tabellen &#39;eav_attribute_option_value&#39;, vilket förhindrar möjligheten att ha flera värden för samma butiksvy. Tidigare kunde felaktig kod resultera i ett alternativ med flera värden för samma butiksvy, vilket orsakade problem när du redigerade produkter eller attribut.
  _AC-6738 - [GitHub-problem](https://github.com/magento/magento2/issues/24718) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/28796)_
* __[Utgåva] Använd synlighetsklassen för produktindexeraren i stället för hårdkodade värden__
Systemet använder nu synlighetsklassen för kategoriproduktindexeraren i stället för hårdkodade värden, vilket förbättrar modulariteten. Tidigare användes hårdkodade värden i kategoriproduktindexeraren, vilket begränsade flexibiliteten och anpassningsbarheten.
  _AC-8297 - [GitHub-problem](https://github.com/magento/magento2/issues/37200) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/37199)_
* __Valutakoden ändras inte i widgeten Ny produkt__
Systemet uppdaterar nu valutakoden i widgeten Ny produkt korrekt när valutan ändras i sidled, vilket ger en konsekvent valutavisning på hela webbplatsen. Tidigare påverkades inte valutakoden som visades i widgeten Ny produkt om du ändrade valutan i klientdelen.
  _AC-9375 - [GitHub-problem](https://github.com/magento/magento2/issues/37898) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/37899)_
* __Normalpriset visas inte på PLP för konfigurerbar produkt__
Normalpriset visas nu på produktlistsidor för konfigurerbara produkter som har underordnade produkter med specialpris.
  _ACP2E-2224 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/a4fbf702)_
* __Stock-information visas inte korrekt på stödrastret för visuell marknadsföring__
Stock visas nu enligt vald butik.
  _ACP2E-2478 - [GitHub-kodbidrag](https://github.com/magento/inventory/commit/bdbf97ea)_
* __Widget-innehåll uppdateras inte på cms-sidan__
Systemet uppdaterar nu widgetinnehållet på en CMS-sida när en produkt är inställd som ny och sparad, så att sidan visar den uppdaterade produktsamlingen. Tidigare uppdaterades inte sidan för att visa den nya produkten på grund av de felaktiga cacheidentiteter som användes för widgeten i cachen.
  _ACP2E-2621 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/f89a447e)_
* __Problem med att spara avancerade priser på paketprodukter__
Paket med produktbesparande prestandaförbättringar.
  _ACP2E-2630 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/b2286ecf)_
* __[Omindexeringsprocessen på plats] är ineffektiv när regler för katalogpris skapas__
När katalogprisregeln sparas blir indexerare inte ogiltiga, utan indexeras bara om berörda produkter
  _ACP2E-2652 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/f89a447e)_
* __Uppdaterar tid för produktattribut av typen Datum och Tid via CSV-import__
Nu kommer datetime-attribut att ha en tidsdel i exporterade data. Det går också att uppdatera tiden för sådana attribut med import. Om Fältbilaga är aktiverat kommer attributvärden i kolumnen &quot;additional_attributes&quot; att omslutas av dubbla citattecken.
  _ACP2E-2679 - [GitHub-problem](https://github.com/magento/magento2/issues/38306) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/ea79f7dd)_
* __Inget lämpligt felmeddelande när webbplats-ID är fel i begäran__
Nu har rätt felmeddelande lagts till för att visas när webbplats-ID:t är fel i begäran. Tidigare fanns det ingen validering när webbplats-ID:t var fel i begäran.
  _ACP2E-2689 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/39d54c2d)_
* __Produktbilden förloras efter att en befintlig schemalagd uppdatering som inte påverkar bilden har tagits bort__
Produktbilder tas inte bort när mellanlagringsuppdateringen tas bort.
  _ACP2E-2785 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/c8931218)_
* __[Cloud] Fel produktpris för paket när det används med nivåpriser__
Tidigare genererades olika slutpriser för kundvagn- och produktlistsidan/produktinformationssidan när man beräknade vissa rabatter avrundade upp till 2 decimaler. När den här korrigeringen har tillämpats är slutpriset för paketprodukten detsamma som på produktinformationssidan, produktlistningssidan och minikundvagnssidan.
  _ACP2E-2799 - [GitHub-problem](https://github.com/magento/magento2/issues/38091) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/b2286ecf)_
* __Katalogkampanjregeln fungerar inte med attributet quantity_and_stock_status__
Attributet quantity_and_stock_status kommer nu att beaktas av katalogerbjudanderegeln, som inte tidigare har beaktats när en ny produkt genereras från adminsidan.
  _ACP2E-2805 - [GitHub-problem](https://github.com/magento/magento2/issues/35627) - [GitHub-kodbidrag](https://github.com/magento/inventory/commit/cf34971d)_
* __Kolumnvärdena för datatabellen updated_at uppdateras inte när priset uppdateras via REST API__
Produktens kolumn &quot;senast uppdaterad den&quot; från administratören uppdateras med rätt datum och tid samtidigt som befintliga produkter uppdateras via REST API. Tidigare uppdaterades inte kolumnen&quot;senast uppdaterad&quot; korrekt.
  _ACP2E-2837 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/39d54c2d)_
* __Det går att ange icke-unika värden via produktimport__
Systemet använder nu den unika värdebegränsningen för unika produktattribut vid import av produkten korrekt, vilket förhindrar att det finns dubblettvärden för det attributet. Tidigare var det möjligt att ange icke-unika värden för produktattribut som konfigurerats att ha unika värden via produktimport.
  _ACP2E-2840 - [GitHub-problem](https://github.com/magento/magento2/issues/38445) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/7e0e5582)_
* __Produkter på klientsidan lagrar specifika data när Single-Store-läge är aktiverat__
Tidigare migrerades inte ändringarna till webbplatsnivå när vi aktiverade läget för en enskild butik för standardbutiksvyn. När den här korrigeringen har tillämpats synkroniseras standardarkivspecifika data med data på webbplatsnivå när läget för en enskild butik aktiveras, och eventuella konflikter för produkter och kategorier kommer att lösas.
  _ACP2E-2843 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/c8931218)_
* __Det går inte att ange &quot;Default Sort By&quot; i en kategori med det övriga API:t__
Uppdatera korrekt default_sort_by i en kategori via REST/SOAP APi-begäran
  _ACP2E-2857 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/57a32313)_
* __[Cloud] Handläggaren har problem med önskelisteantal__
När du lägger till en produkt i önskelistan i en butik ökar inte längre antalet önskelistor i andra butiker som är öppna i samma webbläsare. Tidigare hade antalet önskelistor ökat även i den andra butiken om båda butikerna lästs in i samma webbläsare.
  _ACP2E-2871 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/3a7c4d17)_
* __Kategorisidan i förgrunden visar tomma platser när paketprodukten används__
Paket med produkter som inte är säljbara i den aktuella butikskontexten indexeras inte längre.
  _ACP2E-2874 - [GitHub-kodbidrag](https://github.com/magento/inventory/commit/bc37ec76)_
* __[CLARIFICATION] Problem med produktsekvensregister__
Posterna i Bundle-produktsekvenstabellerna (sequence_product_bundle_option, sequence_product_bundle_selection) tas nu bort när Bundle-produkten tas bort eller Bundle-produktalternativen tas bort.
Tidigare togs posterna i produktsekvenstabellerna i Bundle inte bort.
  _ACP2E-2888_
* __[Cloud] Utfärdande av offert i arkitektur för flera webbplatser__
Tidigare kunde inte flerwebbplatsarkitekturen med olika valutor och kundgrupper tillämpa rabatter på butiken korrekt. När den här korrigeringen har implementerats kommer flerwebbplatsarkitekturen med olika kundgruppsprisrabatter att gälla för olika butiker.
  _ACP2E-2905 - [GitHub-problem](https://github.com/magento/magento2/issues/38506) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/a4fbf702)_
* __dynamic-rows.js:658 Ohanterad TypeError: dataRecord.slice när paketprodukter redigeras__
Det finns inget javascript-fel i webbläsarkonsolen när du tar bort alternativ från paketprodukten.
  _ACP2E-2909 - [GitHub-problem](https://github.com/magento/magento2/issues/38505) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/93d50f8d)_
* __[Cloud] Paketet med felaktiga priser i orderbekräftelsen__
Korrekt belopp visas för paketalternativ i ordning på lagerfonden när annan valuta än bas ett användes.
  _ACP2E-2950 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/a4fbf702)_
* __YouTube Video Adding Bug__
Produktbilder och videor är konfigurerade i globalt omfång. Eftersom du inte kan ha en produktvideo i ett omfång och inte i ett annat, har Youtube API-nyckelinställningen ställts in på globalt omfång.
  _ACP2E-2956 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/a4fbf702)_
* __[URL-uppdatering för molnet] endast för store_id=0__
URL-sökvägen lagras nu med rätt lagrings-ID. Tidigare var lagrings-ID felaktigt, vilket resulterade i att felaktiga URL-sökvägar återstår i databasen när kategorier flyttas.
  _ACP2E-2964 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/9af794a4)_
* __async.operations.all utförde och skapade ett fel.__
Felaktiga produktlänksdata i REST API-anrop orsakar inte längre allvarliga fel.
  _ACP2E-3009 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/a4fbf702)_
* __[Mobilutgåva i molnet] Det går endast att fästa vid PDP-bilden__
Systemet har nu stöd för funktionen att nypa till zooma i produktinformationsbilder i mobilvyn på Chrome, vilket förbättrar användarupplevelsen på mobilen. Tidigare zoomade inte dubbeltryck på bilden i mobilvyn i Chrome in på bilden som förväntat.
  _ACP2E-3029 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/148c3ead)_
* __Etikett saknas i LayeredNavigation med alternativnamnet 0__
Problemet har lösts genom att en tom värdekontroll för attributvärdet 0 ignoreras. Tidigare ansågs den vara tom och orsakade problemet.
  _ACP2E-3058 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/3a7c4d17)_
* __Kunderna ser priser från andra kundgrupper__
Ett problem där kundgruppsrelaterad information sparades i fel segment på grund av det gamla värdet för X-Magento-Vary i begäran har åtgärdats
  _ACP2E-3069 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/d1f7dc95)_
* __Fel vid borttagning av paketalternativ__
Systemet tar nu bort paketalternativen korrekt utan att utlösa något fel eller få sidan att sluta svara. Om du tidigare försökte ta bort paketalternativen skulle det resultera i felet&quot;Sidan svarar inte&quot; och förhindra att produkten sparas.
  _ACP2E-3076 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/6a185204)_
* __Kategoribehörigheter utanför minneswebbläsarproblem__
Gränssnittet för kategoribehörigheter har gjorts om så att det går att återge ett stort antal behörigheter med gränssnittskomponenter och sidnumrering som inte ingår i rutan. Tidigare kategoribehörigheter kan få webbläsaren att krascha med ett stort antal behörigheter som tilldelats kategorin.
  _ACP2E-3094_
* __[Molnavbildningsfilen] finns inte i New Relic-felloggen__
Systemet synkroniserar nu anpassade platshållarbilder till lokala lager och ser till att de återges korrekt när du använder fjärrlagring som AWS S3. Tidigare kunde inte anpassade platshållarbilder återges när fjärrlagring användes, vilket resulterade i en trasig bildvisning och felloggar.
  _ACP2E-3100 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/d1f7dc95)_
* __RSS-flöde för nya produkter uppdateras inte med nya produkter på grund av cache__
RSS-flödet för nya produkter uppdateras nu när en produkt har angetts som ny och sparad
  _ACP2E-3103 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/d01ee51e)_
* __[Cloud] GQL-svaret för produktmediegalleriet sorteras inte efter bildposition__
Systemet sorterar nu objekt i mediegalleriet korrekt efter position i GraphQL-svaret, vilket ger rätt visningsordning. Tidigare sorterades inte objekt i mediegalleriet efter position, vilket ledde till en felaktig visningsordning.
  _ACP2E-3126 - [GitHub-problem](https://github.com/magento/magento2/issues/37671) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/b21e5d91)_
* __[Underkategoriobjekt i molnet] visas inte i widgetredigeringen på adminbackend__
Kategoriträdet på den nya widgetsidan bör inte längre ha problem med att läsa in kategori på nivå 5+. Tidigare saknades vissa kategorier när trädet lästes in efter kategorierna Nivå 5.
  _ACP2E-3136 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/148c3ead)_
* __[cloud] Zooma med två fingrar och flytta problem på den riktiga mobila enheten__
Systemet ger nu en konsekvent bildzoomningsfunktion på mobila enheter, vilket ger en smidig och förutsägbar användarupplevelse. Tidigare var funktionen för bildzoomning inkonsekvent och skulle plötsligt zoomas ut efter en viss punkt när den visades på en mobil enhet.
  _ACP2E-3198 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/1366ae5e)_
* __När vi tar bort tilldelning av produkter från den delade katalogen rensas inte önskelisteprodukterna__
Nu visas inga objekt i önskelistan om en produkt inte är tillgänglig i den delade katalogen. Tidigare visade önskelistsidan felaktigt antalet &quot;1 objekt&quot; även när det inte fanns några objekt i önskelistan.
  _ACP2E-3282 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/5184c067)_
* __Relaterade produkter Markera alla/Avmarkera alla utgåva__
Tidigare fungerade inte knapparna&quot;Markera alla&quot;/&quot;Avmarkera alla&quot; för relaterade produkter korrekt om en produkt har valts manuellt. Efter korrigeringen fungerar knapparna nu konsekvent, även efter det manuella valet, så att alla produkter markeras eller avmarkeras korrekt.
  _ACP2E-3286 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/fd5cf3af)_
* __[Cloud] Stock-aviseringsöversättning via e-post till fel språk__
När du skickar Stock-/prisaviseringar för en webbplats med flera butiksvyer på olika språk, kommer språket för butiksvyn där aviseringen skapades att användas i e-postmeddelandet.
  _ACP2E-3336 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/a4cf5e62) - [GitHub-kodbidrag](https://github.com/magento/inventory/commit/9f3e63d1)_
* __Inaktiverade kategorier är inte längre nedtonade i kategoriträdet__
Tidigare var inaktiverade kategorier inte nedtonade i kategoriträdet. Nu visas de med en gråskaleeffekt.
  _ACP2E-3350 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/d75cff27)_
* __Inläsning av konfigureringsbart produktredigeringsformulär orsakar timeout och minnesöverbelastning__
Före korrigeringen konstruerades konfigurerbara produktvariationer baserat på alla möjliga kombinationer av attributalternativ. I de fall där attributen hade många alternativ resulterade detta i en långsam och resurskrävande åtgärd. Nu kan du konstruera produktvariationer utifrån befintliga underordnade produktattribut. Detta resulterar i betydligt färre beräkningar, vilket innebär en förbättrad resursanvändning.
  _ACP2E-3410 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/078c387e)_
* __Fotoramat läser inte in video korrekt när färgrutor används och alternativet är förvalt via URL__
Produktvideor återges nu korrekt på sidan med konfigureringsbar produktinformation om URL:en innehåller valda alternativ.
  _ACP2E-3454 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/078c387e)_
* __PageBuilder Carousel Widget visar produkter som inte matchar villkoren__
Produktlistan som används i widgetar uppfyller nu kategorivillkoren
  _ACP2E-3461 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/078c387e)_
* __Verifieringsfel utlöstes för alla produkter i gruppen när en har en ogiltig kvantitet__
Valideringsfelet utlöses nu korrekt för alla produkter i gruppen när en produkt har en ogiltig kvantitet, vilket inte hände tidigare.
  _ACP2E-3469 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/56463d5e)_
* __[CLOUD] Specialpriset visas inte i den konfigurerbara produkten__
Efter korrigeringen påverkas inte visningen av specialpriset för konfigurerbara produkter om du ändrar värdet &quot;Används i produktlista&quot; för specialprisattributet.
  _ACP2E-3513 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/d4de4726)_
* __Tillfälliga indexeringstabeller rensas inte om processen avslutas__
KatalogRule-indexerarens temporära tabeller rensas nu bort om indexeringsprocessen avslutas
  _ACP2E-3516 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/1984c61c)_
* __[KVANS] Fel vid test av kärnenhet i 2.4.7-p3__
Versionsinformation för det här testet behövs inte eftersom det är en förbättring av enhetstestet.
  _ACP2E-3520 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/1984c61c)_
* __Prestandaproblem i hämtning av lagerkvantitet för grupperade produkter med flera källor__
Redigeringssidan för grupperade produkter och paketprodukter är nu optimerad när tilldelade produkter har ett stort antal lagerkällor.
  _ACP2E-3533 - [GitHub-kodbidrag](https://github.com/magento/inventory/commit/0208e433)_
* __Refix ACP2E-3389__
Förbättrade prestanda för administratörskategorisidor vid ett stort antal ankarkategorier
  _ACP2E-3641 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/982b1c42)_

### Katalog, innehåll

* __[Cachen i molnet] blir inte ogiltig.__
När en CMS-sida med en uppdaterad designlayout sparades reflekterades den inte korrekt på framsidan. När den här korrigeringen har tillämpats visas rätt designlayout längst fram när vi ändrar designlayouten och sparar CMS-sidan.
  _ACP2E-3063 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/66dea0de)_
* __[Kategorier för ankarpunkter/icke-ankarpunkter i molnet] har återförts i innehållswidgeten__
När vi tidigare valde Visa på -> ankarkategorier visades alla kategorier som inte reflekterade relationen mellan det överordnade och det underordnade objektet mellan ankarpunkten och icke-ankarpunkten. När den här korrigeringen har tillämpats visar Visa på -> ankarkategorier bara ankarkategorier (valbara), och Visa på -> icke-ankarkategorier visar icke-ankarkategorier (valbara)
  _ACP2E-3131 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/7377de59)_
* __Kategorier som inte fungerar med widgetar__
Tidigare, om vi sparade CMS-blocket för olika ankarpunktskategorier/icke-ankarkategorier, fungerade det inte för de underordnade kategorierna när det visades på framsidan. När den här korrigeringen har tillämpats visas blocket längst fram för olika kategorier.
  _ACP2E-3152 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/d01ee51e)_

### Katalog, Framework

* __Beställ get(Shipments|Creditmemos|Invoice)Samling - Samlingen ska inte läsas in__
Systemet ser nu till att samlingarna för försändelser och kreditnotor inte är förinlästa när de hämtas från en order, vilket gör att ytterligare filter eller order kan tillämpas på dessa samlingar. Tidigare lästes dessa samlingar in automatiskt, vilket förhindrar ytterligare ändringar.
  _AC-9111 - [GitHub-problem](https://github.com/magento/magento2/issues/37561) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/37562)_
* __[Cloud]Uppföljning: Felmatchning i datajämförelse vid kontroll av om data har ändrats__
Tidigare anropades objektet save varje gång utan några dataändringar (för numeriska datafält som int/float/double). Den utlöser flaggan _hasDataChanges till true och anropar funktionen save. Den kontrollerar inte heller de flytande talen som är inkapslade med sträng. När den här korrigeringen har tillämpats anropas funktionen spara bara om data har ändrats. Datavärdet för int/float/double check med värdet som skickas till funktionen och utför strikt typmatchning
  _ACP2E-2949 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/c8931218)_

### Katalog, GraphQL

* __Hantera kategorifilter i GraphQL: includeDirectChildrenOnly och category_uid__
Endast direkta underordnade kategorier hämtas vid filtrering efter category_uid.
  _ACP2E-3090 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/93d50f8d)_
* __[Cloud] Graphql Produktsortering fungerar inte__
GraphQl Produktsortering efter flera fält när fälten skickas i variabler fungerar nu som förväntat.
  _ACP2E-3166 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/8459b17d)_
* __Nivåpriser returnerar fel värde i GraphQL-produkter (jämfört med Storefront)__
Efter korrigeringen har produktskiktspriserna som returneras för grafikförfrågningar priset per en artikel.
  _ACP2E-3312 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/1366ae5e)_
* __[CLOUD] B2B: kategoriproblem via GraphQL__
Efter korrigeringen returnerar kategorifrågan kategorier med tillåten behörighet, även om rotkategorin inte tillåter behörighet.
  _ACP2E-3385_

### Katalog, priser, mellanlagring och förhandsvisning

* __[Cloud] API-slutpunkten för specialpris returnerar ett fel när ett stort antal produkter uppdateras samtidigt__
Nu kommer uppdaterings-API:t för specialpris att skapa en kampanj för varje datumintervall i stället för flera schemalagda uppdateringar för varje produkt och datumintervall. Dessutom kommer det att stödja samtidiga API-begäranden för snabbare bearbetning av ett stort antal SKU:er.
  _ACP2E-2672 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/f89a447e)_

### Katalog, produkt

* __Kategorivalsträdet i redigeringsprodukten har inte samma ordning som i Catalog->Kategorier__
Systemet visar nu kategorivalsträdet korrekt i produktredigeringsavsnittet i samma ordning som i Catalog->Kategorier, vilket gör produktadministrationen enklare i stora kataloger. Tidigare visades kategoriträdet i produktredigeringsavsnittet i den ordning som kategorin skapades, oavsett visningsordningen i Katalog->Kategorier.
  _AC-7050 - [GitHub-problem](https://github.com/magento/magento2/issues/36101) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/36104)_

### Katalog, SEO

* __Felaktig kanonisk URL för kategori när sida > 1__
Tidigare fungerade inte den kanoniska URL:en för flersidigt innehåll korrekt, och baswebbadressen visades konsekvent. När korrigeringen har implementerats visar den kanoniska URL:en för flersidigt innehåll nu korrekt URL:en med sid-ID:t.
  _ACP2E-3653 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/982b1c42)_

### Katalog, söka

* __Produkter som inte visas i kategori och sökning, men direktlänkar fungerar__
Tidigare gick det inte att indexera det anpassade attributet Yes/No med price_* attribute_code. Efter den här korrigeringen fungerar attributet Yes/No som förväntat.
  _ACP2E-2757 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/ba25af8a)_
* __[Moln] Elastiskt sökfel på vissa kategorisidor__
Tidigare, med konfigurationsbiljetten som nämndes, utlöses ett undantag på sidan för kategorin Front när vi sätter priset 0 för flera produkter. När den här korrigeringen har tillämpats när flera produktpriser 0 och vi läser in kategorisidan direkt genereras inga undantag och kategorisidan läses in korrekt.
  _ACP2E-3053 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/c8931218)_
* __Typfel uppstod när objektet skapades: Magento\CatalogSearch\Model\Indexer\Fulltext\Interceptor Exception__
Efter korrigeringen kan en instans av Magento\CatalogSearch\Model\Indexer\Fulltext klass skapas utan att $data anges.
  _ACP2E-3345 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/1366ae5e)_
* __[CLOUD] Problem med produkter visas inte i Edge efter att de har sparats i Magento Admin__
Efter korrigeringen kommer konfigurerbara produkter med underordnade produkter med långa namn inte att gå miste om i butiken.
  _ACP2E-3521 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/1984c61c)_

### Katalog, leverans

* __Leveransadressen är tom när en beställning av ett presentregisterobjekt placeras__
Tidigare genererades en tom adress för presentregisterobjekt för gästanvändare när de returnerades från e-postfunktionen. Den är felaktig för att göra en beställning. När den här korrigeringen har tillämpats kontrollerar presentregistret inloggade användare/gästanvändare och tilldelade adresser om de finns.
  _ACP2E-3195_

### Cloud

* __[Cloud] PHPSESSID ändrar varje POST-begäran__
PHPSESSID återskapar inte längre POST-begäranden i klientutökningsområdet för en inloggad kund om L2 Redis-cache är aktiverad och kunden har uppdaterats från serverdelen
  _ACP2E-3010 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/6a185204)_
* __Varningar för att skapa webbplatskartor__
Efter korrigeringen genereras platskartan i systemets tmp-katalog och kopieras till det slutliga målet.
  _ACP2E-3532 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/d4de4726)_

### Innehåll

* __[Problem] med prisvisningen i widgeten Senast visade__
Systemet visar nu priset på färdiga, enkla produkter korrekt i widgeten&quot;Senast visade produkter&quot;, vilket säkerställer konsekvens för alla widgetar och produktlistsidor. Tidigare visades inte priset på färdiga enkla produkter i widgeten &quot;Senast visade produkt&quot; på grund av ett villkor i prissättningsmallarna.
  _AC-10539 - [GitHub-problem](https://github.com/magento/magento2/issues/38167) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/38159)_
* __[Problem] Korrigera stavfel och grammatik i filen acl.xsd__
Systemet rättar nu till ett stavfel och grammatikfel i filen acl.xsd, vilket gör dokumentationen tydligare och exaktare. Tidigare innehöll filen acl.xsd ett stavfel och en felaktig grammatik, vilket skulle kunna orsaka förvirring.
  _AC-10596 - [GitHub-problem](https://github.com/magento/magento2/issues/38061) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/38046)_
* __Banderollbilden för PageBuilder visas inte i galleriet__
Systemet visar nu banderollbilder som överförts i nyligen skapade mappar i PageBuilder-galleriet korrekt, vilket eliminerar tidigare konsolfel. Före den här korrigeringen var banderollbilderna inte synliga i galleriet om de överfördes till en ny mapp, vilket orsakade ett konsolfel.
  _AC-10845 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/c8f87c25)_
* __&quot;Riktnummer har inte angetts&quot; efter uppdatering till 2.4.5-p8__
Systemet slutför nu den statiska innehållsdistributionsprocessen när modulen Magento_CSP är aktiverad och&quot;dev/js/translate_strategy&quot; är inställd på&quot;embedded&quot;, utan att utlösa felet&quot;Area code not set&quot;. Tidigare misslyckades den statiska innehållsdistributionsprocessen under dessa förhållanden med felet&quot;Ingen riktkod har angetts&quot;.
  _AC-12283 - [GitHub-problem](https://github.com/magento/magento2/issues/38845) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/38922)_
* __Widget-kategoriträdet återges inte korrekt__
  _AC-12692 - [GitHub-problem](https://github.com/magento/magento2/issues/39008) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/58e40ceb)_
* __Det går inte att se meddelandet &quot;Använda standardvärde&quot; när du ändrar temat på designkonfigurationssidan__
Systemet innehåller nu en separat kolumn som visar meddelandet &quot;Använda standardvärde&quot; beroende på det valda temat på designkonfigurationssidan. Detta garanterar att standardvärdets status är tydlig och synlig. Tidigare visades inte meddelandet&quot;Använda standardvärde&quot;, vilket ledde till missförstånd om det valda temats status.
  _AC-13054 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/47b448e2)_
* __[Problem] Återställer bakåtkompatibilitet med TinyMCE-plugin-program igen (efter det..__
Systemet återställer nu bakåtkompatibilitet med TinyMCE-plugin-program, vilket gör att funktioner som definierats inuti plugin-programmet kan anropas när widgeten används från en annan plats. Tidigare returnerade inte plugin-programmen widgetarna som ett objekt på grund av en ändring i TinyMCE-versionen, vilket resulterade i ett fel när vissa funktioner anropades i widgetinstansen.
  _AC-13569 - [GitHub-problem](https://github.com/magento/magento2/issues/39262) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/39258)_
* __[Problem med ] filöverföring i WYSIWYG Editor på produktsidan__
Nu visas mappträdet korrekt och bildöverföringar tillåts i WYSIWYG-redigeraren på produktsidan, även efter att du har expanderat fliken Bild och video först. När du tidigare expanderade fliken Bild och video visades inte mappträdet och ett felmeddelande visades när en bild skulle överföras i WYSIWYG Editor.
  _AC-9638 - [GitHub-problem](https://github.com/magento/magento2/issues/38026) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/38025)_
* __[On-PREM] Problem med dynamiskt block__
Wdigets renderas nu korrekt i dynamiska block.
  _ACP2E-2392 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/a12063bd)_
* __YouTube nocookie-URL fungerar inte i Page Builder__
Nu tillåter pagebuilder youtube no-cookie url i inställningarna för formulärelementet i valideringsreglerna. Tidigare fungerar inte youtube no-cookie url i pagebuilder.
  _ACP2E-2606_
* __[Cloud] Sidslut läses inte in på grund av ett problem i nyhetsbrevmallen__
Tillägg av block via innehållsavsnittet på CMS-sidan leder inte längre till undantag
  _ACP2E-2693 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/ea79f7dd)_
* __ACP2E-2836: [Cloud] Ett undersökningsundantag hittades i loggen: InvalidArgumentException: Klassen finns inte i vendor/magento/module-rule/Model/ConditionFactory.php__
Om du tar bort ett villkor i innehållsinställningarna för PageBuilder-produkter sparas inte längre ett undantag i loggfilerna. Om du tidigare tog bort ett villkor i innehållsinställningarna för PageBuilder-produkter skulle ett kritiskt undantag registreras i loggarna, trots att inga problem uppstod i förgrunden.
  _ACP2E-2836 - [GitHub-kodbidrag](https://github.com/magento/magento2-page-builder/commit/36c0f5df)_
* __Växlar till läget för en enskild butik - globalt innehåll visas inte längre__
Systemet synkroniserar nu designkonfigurationer för butiksvyn med designkonfigurationer för webbplatser när du aktiverar läget för en enskild butik, vilket säkerställer att innehållsuppdateringar visas i förgrunden. Om du växlar till läget för en enskild butik tidigare skulle det förhindra att innehållsuppdateringar återspeglas i butiken.
  _ACP2E-2842 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/7e0e5582)_
* __Page Builder ersätter bilden när du försöker lägga till länkar och andra användbarhetsfel.__
När du klickar på en bild kommer länkar i Wysiwyg-redigeraren i textelementet i Page Builder att läsa in korrekta data i dialogrutan för bildkonfiguration och länkkonfiguration. Nu fungerar det också bra att lägga till en länk till en bild i redigeraren. Tidigare ersattes bilden med en länk.
  _ACP2E-2903 - [GitHub-kodbidrag](https://github.com/magento/magento2-page-builder/commit/4d5db10a)_
* __Gammalt mediegalleri kan inte återge bilder när en bild på 0 byte placeras i katalogen__
Systemet hanterar nu bilder på 0 byte i mediegalleriet utan att störa funktionaliteten, vilket gör att andra bilder i katalogen kan visas och markeras som förväntat. Tidigare fanns det en bild på 0 byte i mediegalleriet som hindrade alla bilder i katalogen från att visas eller markeras.
  _ACP2E-2970 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/35b1b1da)_
* __Fel i Page Builder vid redigering av CMS Block__
Systemet sparar nu ändringar som gjorts i administratörsområdet med Page Builder korrekt, utan att felmeddelandet&quot;Page Builder renderade i 5 sekunder utan att frigöra lås visades&quot;. i webbläsarkonsolen. Tidigare inträffade detta fel när ändringar skulle sparas, vilket förhindrar att innehållet uppdateras.
  _ACP2E-3064 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/35b1b1da) - [GitHub-kodbidrag](https://github.com/magento/magento2-page-builder/commit/4d5db10a)_
* __[CLOUD] Inga knappar för utcheckning eller redigering av kundvagn i kundvagnssektionen__
Paketet läggs nu till i kundvagnen via widgetar utan fel.
  _ACP2E-3092 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/b21e5d91) - [GitHub-kodbidrag](https://github.com/magento/magento2-page-builder/commit/4ebe3f1d)_
* __Förhandsgranskning av innehållsmellanlagring på kategorisidor visar inte produktwidgetar__
Problemet har korrigerats genom att man säkerställt att produktposter för den ytterligare kategori som är länkad till CMS-blocket har registrerats korrekt i databasen. Tidigare returnerades en tom resultatuppsättning när sidan för kategoriförhandsgranskning begärdes.
  _ACP2E-3113_
* __[CLOUD] Knappen Överför bild fungerar inte__
Före knappen Överför bild för Banner och Slider från PageBuilder fungerade inte som förväntat, och när du trycker på knappen öppnas nu den lokala filhanteraren för att välja den bild som ska överföras.
  _ACP2E-3122 - [GitHub-kodbidrag](https://github.com/magento/magento2-page-builder/commit/476ef8ea)_
* __imageCreateColor(): Argumentet #2 ($height) måste vara större än 0. Det går inte att överföra den specifika bilden__
Löste problemet som orsakade fel i administratören när bilder med höjden 0 överfördes via mediegalleriet och synkroniseringen av resurser slutfördes med synkroniseringskommandot. Tidigare gick det inte att överföra bilden via mediegalleriet och synkroniseringskommandot misslyckas också när en viss bild finns i galleriet.
  _ACP2E-3127 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/6f4805f8)_
* __Prototype.js Array.from i konflikt med Google Maps API__
Google Maps återges nu korrekt i PageBuilder-redigeraren. Tidigare förhindrade ett Javascript-fel Google Maps från att återges korrekt.
  _ACP2E-3154 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/148c3ead)_
* __[Cloud] - CMS Slider speglar inte de senaste ändringarna__
Problemet har åtgärdats genom att skjutreglagelistan uppdateras medan händelsen save aktiveras på bildredigeringsskärmen. Tidigare utlöstes den och orsakade problemet.
  _ACP2E-3275 - [GitHub-kodbidrag](https://github.com/magento/magento2-page-builder/commit/ae2cdeb0)_
* __Ett fel inträffar på CSM-sidan när CMS-block infogas med hjälp av Page Builder i en viss ordning.__
Tidigare i vissa versioner av PHP och OS (Linux) hade återgivningen av block som refererade till andra cms-block via PageBuilder misslyckats med &quot;Ett okänt fel uppstod. Försök igen.&quot;. Nu återges innehållet i cms-blocken korrekt i ett PageBuilder-kontrollerat innehåll.
  _ACP2E-3326 - [GitHub-kodbidrag](https://github.com/magento/magento2-page-builder/commit/ae2cdeb0)_
* __[Molnet] Dynamiska block fungerar inte korrekt__
Inloggade kundsegment rensas nu efter utloggning så att gästsessionen inte kan ärva tidigare inloggade segment
  _ACP2E-3388_
* __Förhandsgranskning av sidbyggarens mall misslyckades för stort innehåll__
Större innehåll ledde till att arbetsyteelementet flödade över webbläsarens gränser och returnerade ett felaktigt värde, vilket gjorde att backend-koden (det går inte att avkoda bilden korrekt). Korrigerad med begränsad arbetsytestorlek till gränsen för den universella webbläsaren.
  _ACP2E-3428 - [GitHub-kodbidrag](https://github.com/magento/magento2-page-builder/commit/adfb1747)_
* __De senaste säkerhetsuppdateringarna med TinyMCE 7 saknar teckensnittsstorlek__
Väljare för teckensnittsstorlek och teckensnittsfamilj finns nu i WYSIWYG Editor. Före den här korrigeringen fanns de inte i TinyMCE 7 i redigeringsgränssnittet.
  _ACP2E-3430 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/d50f6b5d) - [GitHub-kodbidrag](https://github.com/magento/magento2-page-builder/commit/2c2f7a0e)_
* __TinyMCE 7-redigerarens teckensnittsstorlek i PT-administratören och inte PX, förtydliga__
Före korrigeringen kunde du inte ange teckensnittsstorlek i pixlar i WYSIWYG-områden. Nu kan du ange teckenstorleken i px i stället för pt.
  _ACP2E-3483 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/3f12d152) - [GitHub-kodbidrag](https://github.com/magento/magento2-page-builder/commit/20aa5d7a)_
* __Produktinnehållstyp i Page Builder komprimeras utan korrekta meddelanden__
HTML-filen för förhandsgranskning genererades inte korrekt innan korrigeringen utfördes när det inte fanns några produkter i widgeten. Nu genereras det tomma svaret korrekt och produktwidgeten visas korrekt i förhandsgranskning.
  _ACP2E-3490 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/3f12d152) - [GitHub-kodbidrag](https://github.com/magento/magento2-page-builder/commit/20aa5d7a)_
* __[page builder]Om du lägger till produktlistor för att blockera uppstår fel__
Om du lägger till programpaketet för att blockera via Page Builder uppstår inga fel
  _ACP2E-3534 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/344fce23)_

### Innehåll, SEO

* __CMS sidhierarki kan orsaka problem med URL-omskrivning__
Tidigare, för anpassad permanent URL-omskrivning för icke-webbplatsens rotsidor, omdirigeras oändligt och sidan lästes aldrig in. När den här korrigeringen har tillämpats fungerar den anpassade URL-omskrivningen för rotsidan som inte är webbplats som förväntat och ingen omdirigeringsslinga sker.
  _ACP2E-2870_

### Innehåll, mellanlagring och förhandsvisning

* __Katalogprisregeln visas inte när den är inställd på att schemalägga med dynamiska block__
Systemet visar nu dynamiskt innehåll som är kopplat till regler för katalogpris korrekt på produktinformationssidan. Tidigare gick det inte att läsa in dynamiskt innehåll när katalogens prisregler var schemalagda.
  _ACP2E-2979_

### Kund/Kunder

* __Front end - Det gick inte att validera födelsedatumet på sidan Kund__
Se till att all validering fungerar efter uppgraderingsevenemanget.js systemberoende av den senaste mindre versionen
  _AC-12162 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/de4dfb8e)_
* __Kundsegment > Villkor > Produkthistorik* > &quot;produkten visades&quot; fungerar inte__
Systemet visar nu korrekt matchade registrerade kunder i villkoret&quot;Produkten visades&quot; under Kundsegment när villkoret är uppfyllt. Tidigare var antalet matchade registrerade kunder noll, även när villkoret var uppfyllt.
  _AC-13060_
* __Regiontextfältet återställs inte när listrutan för land ändras__
Systemet återställer nu regionens textfält när landet ändras i listrutan, vilket säkerställer att tidigare värden inte kvarstår. Tidigare återställdes inte regionfältet om landet ändrades från listrutan, vilket innebar att det senast sparade värdet bevaras.
  _AC-8499 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/3ea26621)_
* __Om du tar bort kunden rensas inte alla sessionsdata för webbläsaren på Storefront för inloggad och borttagen kund__
När en kund tas bort rensas alla webbläsarsessionsdata från butiken för inloggade och borttagna kunder som förväntat. Köparen kan fortsätta handla och webbläsaren behandlar sin session som en gästsession. Tidigare när kundkontot för en inloggad kund togs bort från Admin uppstod JavaScript-fel i webbläsaren.
  _AC-9240 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/7d5e3906)_

### Ramverk

* __[Fråga]Oanvänd typkonfiguration i`app/code/Magento/Translation/etc/di.xml`__
Systemet tar nu bort oanvända beroenden i konfigurationen, vilket förbättrar den övergripande renheten och effektiviteten i koden. Tidigare fanns det oanvända beroenden i konfigurationen som inte bidrog till någon funktion.
  _AC-10037 - [GitHub-problem](https://github.com/magento/magento2/issues/38030) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/38064)_
* __V1/customers/password endpoint question/issue__
Systemet följer nu de begränsningar som anges i det hanterings-GUI när begäranden om lösenordsändringar bearbetas via API:t, vilket förhindrar eventuellt missbruk av funktionen för lösenordsåterställning. Tidigare kunde API:t bearbeta begäranden om lösenordsändringar utanför de regler som definierats i det hanterade användargränssnittet, vilket eventuellt skulle möjliggöra en konstant ström av återställda e-postmeddelanden om giltiga e-postmeddelanden var kända.
  _AC-10654 - [GitHub-problem](https://github.com/magento/magento2/issues/38238) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/0c53bbf7)_
* __Slutlig konfiguration utesluter inte alla marknadsföringsparametrar__
Systemet utesluter nu alla vanliga marknadsföringsparametrar korrekt i Varnish-konfigurationen, vilket ger korrekt spårning och analys. Tidigare har vissa marknadsföringsparametrar som gned_source, srsltid och msclodd inte uteslutits, vilket kan leda till felaktiga datainsamlingar.
  _AC-10738 - [GitHub-problem](https://github.com/magento/magento2/issues/38298) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/39188)_
* __Processen för indexbearbetning av katalogsökindex (indexeringsprocess)__
Systemet slutför nu kommandot för indexering utan att några fel påträffas, oavsett vilken libxml-version som kompilerats med PHP. Tidigare resulterade omindexeringskommandot i ett fel av typen&quot;Katalogsökindexprocessfel under indexeringsprocessen&quot; när PHP kompilerades med vissa versioner av libxml.
  _AC-10838 - [GitHub-problem](https://github.com/magento/magento2/issues/38254) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/38553) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/0574ac23)_
* __Filtren created_at, status och total_total_filters har lagts till i kundorderfrågan och flera filterfel har åtgärdats__
Systemet har nu stöd för användningen av filtren created_at, status och total_total i kundorderfrågor, och har åtgärdat ett problem där flera filter inte tillämpades korrekt. Tidigare hade systemet inte stöd för dessa filter och kunde inte tillämpa alla filter när mer än ett användes i en fråga.
  _AC-10941 - [GitHub-problem](https://github.com/magento/magento2/issues/38392) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/36949)_
* __översvämmas slumpmässigt av frågor från relaterade / merförsäljning / korsförsäljning och prisindexering__
Systemet optimerar nu frågor från relaterade, merförsäljning och korsförsäljning, vilket förbättrar prestanda och förhindrar att webbplatsen kraschar på grund av för många frågor. Tidigare kunde systemet bli överbelastat med frågor från de här blocken, vilket gjorde att det gick betydligt långsammare och kunde göra att webbplatsen inte fungerade som den skulle.
  _AC-10991 - [GitHub-problem](https://github.com/magento/magento2/issues/36667) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/38050)_
* __Undantag: Varning! Försöker få åtkomst till matrisförskjutning i.. -> Calendar.php sedan uppgradering till ICU 74.1 (PHP Intl)__
Commerce loggar inte längre följande undantag i exception.log när en kund eller handlare besöker antingen butiken eller administratören: `main.CRITICAL: Exception: Warning: Trying to access array offset on value of type null in /vendor/magento/framework/View/Element/Html/Calendar.php on line 114 in /vendor/magento/framework/App/ErrorHandler.php:62`. [GitHub-38214](https://github.com/magento/magento2/issues/38214)
  _AC-11423 - [GitHub-problem](https://github.com/magento/magento2/issues/38214) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/38364)_
* __[Problem] Åtgärda problem med kunddata när formuläret innehåller element med namnet`method`__
Systemet identifierar nu attributet method i formulärskickningar korrekt, även när det finns ett element med namnet method i formuläret. Detta säkerställer korrekt behandling av kunddata. Tidigare, om ett formulärelement hette &#39;method&#39;, skulle det störa identifieringen av &#39;method&#39;-attributet i formulärskickningar, vilket skulle kunna orsaka problem med kunddatahanteringen.
  _AC-11476 - [GitHub-problem](https://github.com/magento/magento2/issues/38484) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/38449)_
* __[Problem] Korrigera PHPDocs för \Magento\Framework\Data\Collection::getItemById__
PHPDocs för metoden \Magento\Framework\Data\Collection::getItemById har uppdaterats så att null inkluderas som en möjlig returtyp, vilket åtgärdar problem med statiska analysverktyg. Tidigare specificerade metodens PHPDocs inte null som en möjlig returtyp, vilket ledde till varningar eller fel i den statiska analysen när metoden användes i villkorssatser.
  _AC-11489 - [GitHub-problem](https://github.com/magento/magento2/issues/38485) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/38439)_
* __[Problem] Tillåt endast giltiga inställningar under`setup:di:compile`__
Systemet genererar nu ett fel under kommandot `setup:di:compile` om en inställning skapas för en klass som inte finns eller som är exkluderad, vilket säkerställer att endast giltiga inställningar tillåts. Tidigare misslyckades dessa scenarier utan att någon information om plugin-program som är associerade med de ursprungliga klasserna återges.
  _AC-11592 - [GitHub-problem](https://github.com/magento/magento2/issues/38517) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/33161)_
* __Magento försöker ändra den skrivskyddade egenskapen i __väckningsmetoden för LoggerProxy__
Systemet tillåter nu att tidigare skrivskyddade egenskaper ändras i LoggerProxyns __wakeup-metod, vilket ger en smidig funktion utan att användarna tvingas att använda en lösning. Tidigare uppstod problem om du försökte tilldela om värdet för en skrivskyddad egenskap i LoggerProxyns __wakeup-metod.
  _AC-11651 - [GitHub-problem](https://github.com/magento/magento2/issues/38526) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/c8f87c25)_
* __[Utgåva] AC-2039 AC-1667 uppgradera TinyMCE-referenser__
Uppdaterad tidsbesparande senaste versionen i Composer.json
  _AC-11681 - [GitHub-problem](https://github.com/magento/magento2/issues/38533) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/36543) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/b34c0a75)_
* __ChangeBatchWalker fungerar inte i flera trådar__
Systemet har nu stöd för processgaffel för MView-indexering, vilket förhindrar fel under indexeringskörning vid arbete på flera trådar. Tidigare ledde en körning av ChangelogBatchWalker på flera trådar till att tabeller som används av andra trådar togs bort, vilket orsakade ett fel under körningen av indexeraren.
  _AC-11696 - [GitHub-problem](https://github.com/magento/magento2/issues/38246) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/38248)_
* __[Problem] Byt namn på variabel med felaktigt namn__
Systemet namnger nu variabeln som innehåller det belopp som fortfarande kan återbetalas korrekt, vilket förhindrar förvirring under felsökningen. Tidigare hade variabeln felaktigt fått namnet totalRefund, vilket kunde leda till missförstånd för utvecklare.
  _AC-11781 - [GitHub-problem](https://github.com/magento/magento2/issues/38609) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/36205)_
* __[Problem] Skicka anpassade attribut till den aktuella länken via XML__
Systemet tillåter nu att anpassade attribut skickas till den aktuella länken via XML, vilket säkerställer att dessa attribut visas korrekt även när länken är den aktuella sidan. Tidigare visades inte anpassade attribut för den aktuella sidlänken eftersom metoden getAttributesHtml() inte används för den aktuella länken.
  _AC-11809 - [GitHub-problem](https://github.com/magento/magento2/issues/38500) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/30070)_
* __Inbyggt FPC-cacheminne bryts i 2.4.7 för vissa konfigurationer__
Systemet cachelagrar nu sidor korrekt när parametern MAGE_RUN_CODE är inställd, vilket ger optimala prestanda. Tidigare cachelagrades inte sidor under dessa förhållanden, vilket ledde till potentiella prestandaproblem.
  _AC-11819 - [GitHub-problem](https://github.com/magento/magento2/issues/38626) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/38646) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/0c53bbf7)_
* __[Problem] Åtgärda inkonsekvenser i undantagshantering mellan utvecklare och produktionslägen__
Systemet hanterar nu konsekvent undantag mellan utvecklare och produktionslägen, vilket förhindrar oväntad omdirigering till inloggningssidan när ett undantag inträffar. Tidigare kunde en inkonsekvens i undantagshanteringen leda till en omdirigering till inloggningssidan i produktionsläge i stället för att visa undantagsmeddelandet.
  _AC-11829 - [GitHub-problem](https://github.com/magento/magento2/issues/38639) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/37712)_
* __Ersätt översättningen PayPal Account i token_list.phtml__
Systemet märker nu avsnittet för tokeniserbara kontobetalningsmetoder som &quot;Konto&quot; i stället för &quot;PayPal-konto&quot; på sidan Lagrade betalningsmetoder, vilket gör det mer representativt för funktionen. Tidigare hette det här avsnittet särskilt&quot;PayPal Account&quot;, vilket var vilseledande när andra tokenliknande betalningsmetoder lades till.
  _AC-11852 - [GitHub-problem](https://github.com/magento/magento2/issues/35622) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/37959)_
* __Bakåtkompatibiliteten har förlorats i Magento\Catalog\Model\ProductRepository class__
Klassen ProductRepository behåller nu bakåtkompatibilitet genom att återställa klassen Initialization Helper som den andra parametern, vilket säkerställer att moduler som utökas från den här klassen fungerar som förväntat. Tidigare ledde borttagningen av initieringshjälpen från konstruktorn i klassen ProductRepository till att bakåtkompatibiliteten gick förlorad, vilket tvingade användarna att använda en lösning.
  _AC-11874 - [GitHub-problem](https://github.com/magento/magento2/issues/38669)_
* __[Problem] Distribuera statiskt innehåll - typfel__
Systemet hanterar nu tomma LESS-filer korrekt under distributionen av statiskt innehåll och visar felmeddelandet&quot;LESS-filen är tom&quot;. Tidigare uppstod ett felaktigt typfel när en tom LESS-fil påträffades under distributionen.
  _AC-11905 - [GitHub-problem](https://github.com/magento/magento2/issues/38682) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/38683)_
* __[Problem] [Visa] Extra utrymme i länk- och skripttagg har tagits bort__
Systemet ser nu till att det inte finns några extra mellanslag i länk- och skripttaggarna, vilket ger renare och mer effektiv kod. Tidigare gick det att hitta dubbla mellanslag mellan attribut i link- och script-taggarna.
  _AC-12002 - [GitHub-problem](https://github.com/magento/magento2/issues/32920) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/32919)_
* __[Utgåva] Undvik en oändlig loop för felkonfiguration__
Systemet undviker nu en oändlig slinga genom att förhindra självrefererande mappning i virtuella typkonfigurationer. Detta garanterar att programmet inte fastnar i en oändlig slinga när ett försök görs att avreferera en självreferensnod. Tidigare, om en virtuell typkonfiguration var självrefererande, skulle det få programmet att snurra oändligt.
  _AC-12127 - [GitHub-problem](https://github.com/magento/magento2/issues/38822) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/38794)_
* __Objekthanteraren används inte för Magento\Csp\Model\Mode\Data\ModeConfigured__
Systemet använder nu Object Manager korrekt när ModeConfiguring-objektet skapas, vilket tillåter att plugin-program används på det här objektet. Tidigare användes inte Object Manager, vilket förhindrar att plugin-program används i ModeConfiguring-objektet.
  _AC-12299 - [GitHub-problem](https://github.com/magento/magento2/issues/38875) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/38886)_
* __Felaktig dokumentblockkommentar i produktStock och prisaviseringar__
Dokumentblockkommentaren för metoden deleteCustomer i produktStock- och prisaviseringar har korrigerats för att korrekt återspegla att metoden tar bort alla aktiekursprodukter eller prisaviseringar som är kopplade till en viss kund och webbplats, inte kunden från webbplatsen. Tidigare hade kommentaren felaktigt angett att metoden var att ta bort en kund från webbplatsen.
  _AC-12540 - [GitHub-problem](https://github.com/magento/magento2/issues/38939) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/39001)_
* __[Problem] Använd kompilerad konfiguration för genererade data i stället för allmän konfiguration__
Systemet använder nu den kompilerade konfigurationen för genererade data i stället för den allmänna konfigurationen, vilket minskar nätverksöverföringen och belastningen på data som är beroende av en viss version av koden. Den här ändringen förhindrar åsidosättning av cache i delade instanser under behållarbyte, vilket leder till förbättrad stabilitet och minskad drifttid. Tidigare använde vissa huvudklasser en delad config-typ, vilket kan leda till att cache-lagring åsidosätts eller att programmet blir driftsavbrott på grund av skillnader i kodversioner mellan flera servrar.
  _AC-12594 - [GitHub-problem](https://github.com/magento/magento2/issues/38785) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/29954)_
* __[Problem] Ta bort referenser till filer från filer som har tagits bort i e1ccdb..__
Systemet tar nu bort referenser till filer från tidigare borttagna filer, vilket eliminerar fel i webbläsarens konsol och systemloggfilen. Tidigare orsakade dessa referenser fel på grund av att det inte fanns några refererade filer.
  _AC-12597 - [GitHub-problem](https://github.com/magento/magento2/issues/38960) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/38951)_
* __[Problem] Mindre rensning: Korrigerad felaktig användning av sprintf, det tar bara två platshållare här och w..__
Systemet använder nu sprintf-funktionen korrekt med rätt antal platshållare, vilket förbättrar kodens renhet och enhetlighet. Tidigare användes sprintf-funktionen felaktigt med ett extra argument, som inte orsakade några större problem men som inte var korrekt.
  _AC-12778 - [GitHub-problem](https://github.com/magento/magento2/issues/39062) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/38628)_
* __PHP 8.2.15 har tagit bort FTP-tillägget__
Systemet inkluderar nu FTP-tillägget som ett beroende i filen Composer.json, vilket säkerställer att CSV-import via FTP kan konfigureras korrekt. Tidigare uppstod ett fel vid försök att konfigurera CSV-import via FTP eftersom FTP-tillägget saknas i PHP-paketet.
  _AC-12857 - [GitHub-problem](https://github.com/magento/magento2/issues/39083) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/47b448e2)_
* __[Problem] Korrigerar felaktiga klasser som refereras i Magento-moduler.__
Nu refererar systemet till klasser i moduler på rätt sätt, vilket ger smidigare drift och förhindrar krascher på grund av icke-befintliga klasser. Detta inkluderar en bugfix i indexer- och Creditmemo-modulerna och implementeringen av HttpGetActionInterface i klassen PrintAction. Tidigare ledde felaktiga klassreferenser till fel och potentiella systemkrascher, och vissa funktioner, som t.ex. filnamnet för kreditnota PDF-filer och omindexering av lager, fungerade inte som förväntat.
  _AC-12869 - [GitHub-problem](https://github.com/magento/magento2/issues/39126) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/37784)_
* __Möjlighet att definiera område för `dev:di:info` CLI-kommando__
Nu kan utvecklare definiera ett område för CLI-kommandot i `dev:di:info` , vilket förbättrar utvecklings- och felsökningsprocessen. Tidigare kunde kommandot bara visa information för området GLOBAL.
  _AC-12964 - [GitHub-problem](https://github.com/magento/magento2/issues/38758) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/38759)_
* __[Utgåva] Lägg till egenskapen isMultipleFiles i bildformulärelementmallen__
Den här korrigeringen förhindrar att knappen &quot;Bläddra för att hitta eller dra bilden hit&quot; försvinner när en bild läggs till i ett formulärelement för flera filer.
  _AC-13149 - [GitHub-problem](https://github.com/magento/magento2/issues/39219) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/36325)_
* __konfiguration:uppgradering misslyckas med MariaDB 11.4-versionen på grund av ändringar i teckenuppsättning och sortering__
  _AC-13247_
* __[Problem] Ta bort alla parametrar för marknadsföringsinhämtning för att minimera cachen__
Systemet tar nu bort alla parametrar för marknadsföringsget för att optimera användningen av cacheminnet, vilket speglar logiken som används när Varnish används. Tidigare kunde de här parametrarna leda till cachebloggning och försämrade prestanda.
  _AC-13279 - [GitHub-problem](https://github.com/magento/magento2/issues/39266) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/39099)_
* __[Utgåva] [PHPDOC] Korrigera dåligt Magento\Directory\Model\AllowedCountries::getAllowedcountries()__
PHPDoc för metoden Allowedcountries::getAllowedcountries() har korrigerats för att ge korrekt information, vilket gör dokumentationen tydligare och mer användbar. Tidigare innehöll PHPDoc för den här metoden felaktig information, vilket kan leda till förväxling eller missbruk av metoden.
  _AC-13345 - [GitHub-problem](https://github.com/magento/magento2/issues/39246) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/39241)_
* __[Problem] Tar bort kod för PHP-versioner som inte längre stöds.__
Borttagning av kod för PHP-versioner som inte längre stöds i Magento
  _AC-13348 - [GitHub-problem](https://github.com/magento/magento2/issues/39361) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/39202)_
* __[Problem] Gör ImageMagick Adapter-kompatibelt med php8 (implicit konvertering från flyttal till heltal)__
Systemet garanterar nu kompatibilitet med PHP8 genom att hantera flyttal korrekt vid beräkning av bilddimensioner, vilket förhindrar fel som beror på implicit konvertering från flyttal till heltal. Tidigare kunde beräkningen av bildens dimensioner resultera i flyttal, som skulle orsaka ett fel om de var implicit avrundade.
  _AC-13417 - [GitHub-problem](https://github.com/magento/magento2/issues/39402) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/37362)_
* __[Problem] [PHPDOC] Korrigera felaktig avbildning Magento\Framework\App\Config\ScopeConfigInterface__
Den här uppdateringen korrigerar PHPDoc-anteckningarna i Magento\Framework\App\Config\ScopeConfigInterface så att de korrekt återspeglar typen av $scopeCode-argument för metoderna getValue och isSetFlag.
  _AC-13537 - [GitHub-problem](https://github.com/magento/magento2/issues/39492) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/39199)_
* __Magento\Framework\Filesystem\Driver\Http beror på orsaksfrasen OK__
Borttagen &quot;OK&quot;-fraskontroll från Magento\Framework\Filesystem\Driver\Http::isExists
  _AC-13725 - [GitHub-problem](https://github.com/magento/magento2/issues/39546) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/39558)_
* __Indexeraren för kundstödraster fungerar inte korrekt i schemaläge för uppdatering__
Tidigare kundrutnät uppdaterades omedelbart men efter att korrigeringen av kundrutnätet uppdaterades efter att kron kördes, men speglades inte direkt.
  _AC-13810 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/1da9ba6f)_
* __skrivfel i en js-fil.__
Systemet använder nu termen&quot;prenumeranter&quot; i JavaScript-filen korrekt, vilket säkerställer att de relaterade funktionerna fungerar som de ska. Tidigare har ett typografiskt fel i JavaScript-filen resulterat i felaktig användning av termen &quot;subsctibers&quot;.
  _AC-6754 - [GitHub-problem](https://github.com/magento/magento2/issues/36163) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/36171)_
* __[Problem] Ta bort ej tillåten `@author` tagg__
Systemet följer nu kodningsstandarderna genom att ta bort den förbjudna `@author` -taggen från vissa moduler, vilket ger en renare och mer standardiserad kod. Tidigare fanns taggen `@author` i vissa moduler, vilket stred mot de etablerade kodningsstandarderna.
  _AC-8353 - [GitHub-problem](https://github.com/magento/magento2/issues/37253) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/37003)_
* __[Problem] Ta bort ej tillåten `@author` tagg från `Magento_Customer` (del 2)__
Systemet följer nu kodstandarden genom att ta bort den förbjudna `@author` -taggen från vissa moduler, vilket ger en renare och mer standardiserad kod. Tidigare fanns taggen `@author` i vissa moduler, vilket stred mot de etablerade kodningsstandarderna.
  _AC-8356 - [GitHub-problem](https://github.com/magento/magento2/issues/37250) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/37000)_
* __Utrymme i syntaxbrytningsregel för editorconfig för [{Composer,auth}.json]__
Systemet tillämpar nu indrag med 4 blanksteg korrekt på Composer- och auth.json-filer, efter en korrigering av ett syntaxfel i EditorConfig. Tidigare formaterades dessa filer felaktigt med ett indrag med två blanksteg på grund av ett blanksteg i editorconfig-syntaxen.
  _AC-8659 - [GitHub-problem](https://github.com/magento/magento2/issues/37394) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/37395)_
* __[Problem] Förbättra loggning av kroniska fel__
Systemet samlar nu in och loggar både STDERR och STDOUT för cron-processer, vilket ger värdefull diagnosinformation i scenarier där kron-processer misslyckas. Tidigare spelades inga felmeddelanden in i cron-processer och STDERR och STDOUT för cron-grupper som körs i separata processer gick förlorade.
  _AC-8662 - [GitHub-problem](https://github.com/magento/magento2/issues/37453) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/32690)_
* __[Problem] Lägger till fler färger i utdata från vissa kommandon för Konfigurera klient__
Nu läggs fler färger till i utdata från vissa kommandon i CLI (setup command line interface), vilket förbättrar läsbarheten och användarupplevelsen. Tidigare var utdata från kommandona svårare att läsa på grund av bristande färgdifferentiering.
  _AC-8984 - [GitHub-problem](https://github.com/magento/magento2/issues/29335) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/29298)_
* __Uppgradering av Magento återställer general/region/state_required när new country med obligatoriskt läge/region läggs till.__
Systemet lägger nu bara till det ändrade landet i konfigurationen &quot;general/region/state_required&quot; när ett nytt land med obligatoriska lägen läggs till, vilket förhindrar eventuella avbrott i den anpassade koden som förutsätter att regionen är inaktiverad. Om du tidigare lade till ett nytt land med obligatoriska lägen återställs konfigurationen General/region/state_required till standardländer med ett obligatoriskt tillstånd, vilket kan göra att affären bryts.
  _AC-9630 - [GitHub-problem](https://github.com/magento/magento2/issues/37796) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/38076)_
* __Skillnad i mindre kompilering mellan php &amp; nodatums-biblioteket (grunt) med komplicerade `calc` uttryck__
Åtgärda skillnaden i mindre kompilering mellan php &amp; nodejs-biblioteket (grunt) efter uppdatering wikimedia/less.php:^5.x
  _AC-9712 - [GitHub-problem](https://github.com/magento/magento2/issues/37841) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/b34c0a75)_
* Felet __&quot;Bastabell eller vy hittades inte&quot; inträffar när partiell indexering körs__
Partiell omindexering fungerar nu korrekt med stor ändringslogg vid sekundär databasanslutning
  _ACP2E-2692 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/ba25af8a)_
* __Problem efter uppgradering av MariaDB till 10.5.1 eller senare__
Korrigerade problemet när datetime-värden i en DB konverterades till 0000-00 00:00:00 efter Mysql-uppgradering
  _ACP2E-2844 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/a12063bd)_
* __Typmatchningsfel i datajämförelse vid kontroll av om data har ändrats__
Tidigare anropades objektet save varje gång utan några dataändringar (för numeriska datafält som int/float/double). Den utlöser flaggan _hasDataChanges till true och anropar funktionen save. När den här korrigeringen har tillämpats anropas funktionen spara bara om data har ändrats. Datavärdet för int/float/double-check med värdet som skickas till funktionen och utför strikt typmatchning.
  _ACP2E-2855 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/57a32313)_
* Det går inte att använda __[molnimport] med katalogen var__
Produkten kan importeras utan problem oavsett filnamn.
  _ACP2E-2959 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/3a7c4d17)_
* __I iPad mini läses meny och sidhuvud in som mobilt, i stället läses de in som skrivbord.__
Systemet hanterar nu enheter med en bredd på 768px som stationära datorer, vilket säkerställer att meny- och rubrikerna läses in korrekt. Tidigare behandlades enheter med bredden 768 px som mobila enheter, vilket gjorde att menyn och huvudet lästes in i en mobilvy.
  _ACP2E-2966 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/35b1b1da) - [GitHub-kodbidrag](https://github.com/magento/magento2-page-builder/commit/4d5db10a)_
* __Det gick inte att hitta något fel i bastabellen eller vyn när mview cron kördes med en DDL-åtgärd__
Systemet hanterar nu databasuppdateringsåtgärder korrekt medan vyuppdateringen körs i bakgrunden, vilket förhindrar att fel i bastabellen eller vyn inte hittades inträffar. Tidigare kunde en del databasuppdateringsåtgärder resultera i felet &quot;Bastabell eller vy hittades inte&quot; om mview-uppdateringen kördes samtidigt.
  _ACP2E-3046_
* __Det går inte att ändra kolumnlängden via db_schema.xml för främmande nycklar__
om du ändrar en kolumn med en sekundärnyckel via ett deklarativt schema uppstår nu inga fel med MariaDB
  _ACP2E-3230 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/581b7ef1)_
* __Vissa av relationsposterna sparas i DB när orderposten sparas__
Innan korrigeringen av onödiga UPDATE-frågor utlöstes, vilket kan påverka prestandan negativt. Efter korrigeringen togs de onödiga UPDATE-frågorna bort.
  _ACP2E-3361 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/1366ae5e)_
* __[CLOUD] I admin finns många javascript-fel i konsolen__
Tidigare fanns det många javascript-fel i konsolen på administratörspanelen. Nu kommer det inte att finnas några JavaScript-fel i konsolen på administratörspanelen och alla JavaScript standardfunktioner kommer att köras utan några problem.
  _ACP2E-3375 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/d75cff27)_
* __[Cloud] Magento: Kömeddelandet har tagits bort__
Kömeddelanden rensas nu korrekt. Före korrigeringen kunde nya meddelanden ha tagits bort om rensningskömeddelandet kördes samtidigt eftersom SQL-kösystemet användes.
  _ACP2E-3387 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/d50f6b5d)_
* __Motsvarande cachenyckelposter är inte tillgängliga i cachetaggar, vilket innebär att cacherensning inte fungerar korrekt__
LUA-läget är nu aktiverat som standard för Redis-cache-skräpinsamlare för att förhindra konkurrensförhållanden
  _ACP2E-3537 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/a52ff98f)_
* __MAGENTO_DC_INDEXER_USE_APPLICATION_LOCK-värdet ignoreras__
Efter korrigeringen behandlas en ENV-variabel som är inställd på &quot;false&quot; som bool false, inte som strängen &quot;false&quot;.
  _ACP2E-3681 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/982b1c42)_

### Framework, GraphQL

* __[Problem] Stöd för anpassade skalära typer för GraphQL-schema har introducerats__
Systemet har nu stöd för anpassade skalära typer för GraphQL-scheman, vilket gör att utvecklare kan definiera anpassade skalära typer och implementeringar. Den här funktionen kan vara särskilt användbar för att uttrycka värden som kan behöva valideras, t.ex. HTML, e-post, URL:er, datum och mer avancerade fall som EAV-attribut. Tidigare hade systemet inte stöd för bearbetning av anpassade skalära typer i GraphQL.
  _AC-7976 - [GitHub-problem](https://github.com/magento/magento2/issues/36877) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/34651) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/0574ac23)_

### Framework, Product

* __2.4.8-beta1 EE-rapporter genereras inte på grund av ett magento-undantag__
  _AC-13011_

### Framework, UI Framework

* __Möjlighet att skriva över konfigurationsvärdet även om det är låst__
Tidigare till den här korrigeringen kunde designkonfigurationen inte anges med kommandot bin/magento config:set och låsta värden kan ändras genom att formuläret som visar dem ändras. Efter korrigeringen av låsta värden som angetts från cli med —lock-env eller —lock-conf kan inte uppdateras längre.
  _ACP2E-3324 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/55615e61)_

### GraphQL

* __Magento_GraphQl kör rubriker även om rubrikvärdet inte godkänns i valideringen__
Systemet ser nu till att huvudbearbetningen endast utförs en gång och endast om huvudvärdet godkänns i valideringen, vilket förbättrar säkerheten och förhindrar potentiella sårbarheter. Tidigare utfördes rubrikbearbetning även om rubrikvärdet inte godkändes vid valideringen, vilket ledde till potentiella sårbarheter och oväntade beteenden på grund av dubbelbearbetning av rubrikvärden.
  _AC-11729 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/c8f87c25)_
* __Alternativen för fysiskt Giftkort har inte rätt sorteringsordning__
Systemet sorterar nu alternativen för fysiska presentkortsprodukter korrekt när man frågar via GraphQL, vilket ger en konsekvent rendering med Luma-temat. Tidigare var sorteringsordningen felaktig enligt lumatema, vilket ledde till felaktig visning och ordning av alternativ som avsändarnamn, mottagarnamn och belopp.
  _AC-8951 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/1bafc571)_
* __[GraphQL] Resolver Cache är ogiltig när en mellanlagringsuppdatering skapas/redigeras/flyttas/tas bort__
Systemet ser nu till att lösningsservercachen inte blir ogiltig när du skapar, redigerar, flyttar eller tar bort en mellanlagringsuppdatering, utan bara när mellanlagringsuppdateringen tillämpas på entiteten. Tidigare ogiltigförklarades cacheminnet för lösaren i förtid, till och med innan mellanlagringsuppdateringen tillämpades, vilket ledde till onödiga cacheminnen.
  _AC-9157 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/0c53bbf7)_
* __Cacheminnet har inte rensats för uppdatering av innehållsmellanlagring__
Nu ogiltigförklaras GraphQL med innehållets svarscache i PageBuilder när innehållsrelaterade entiteter i PageBuilder uppdateras.
  _ACP2E-2642 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/ba25af8a)_
* __Inaktiverar nivånavigering - Tar inte bort aggregering från grafik__
Problemet har korrigerats efter att kontrollen tillämpats när en produktsökning begärdes med kategoriaggregering via en GraphQL-fråga när administratörskonfigurationsinställningen &quot;Katalog > Layered Navigation > Display Category Filter&quot; (Katalog > Visningskategorifilter).
  _ACP2E-2653 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/12e071c3)_
* __GraphQL Products-anropet som innehåller prisfiltret  returnerar inget resultat__
Tidigare sökning med grafikprocessorer med filter för nollpriser returnerade inga resultat alls på grund av ett utlöst undantag. Nu returnerar sökningen det förväntade resultatet.
  _ACP2E-2928 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/c971859e)_
* __Översättningar för kundreturattribut återspeglas inte i GraphQL API för respektive StoreView__
Översättningar för kundreturattribut återspeglas i GraphQL API för respektive StoreView.
Tidigare återspeglas inte kundreturattribut för respektive StoreView i GraphQL API.
  _ACP2E-2974 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/ec7e32a9)_
* __[Cloud] Brutet GraphQL-anrop för getPurchaseOrder med nodcitat__
GraphQL-anropet för inköpsorder kan utföra uppgiften utan att några interna serverfel påträffas.
  _ACP2E-3128 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/6f4805f8)_
* __[Cloud] Konfigurerbara produkter visas inte på produktionsplatsen om produkten inte är aktiverad i vyn Alla butiker__
Systemet visar nu konfigurerbara produkter på webbplatsen korrekt, även om produkten inte är aktiverad i Alla butiksvyer, men är aktiverad i specifika butiksvyområden.
Om en produkt tidigare var inaktiverad i&quot;Alla butiksvyer&quot; och endast aktiverad i specifika butiksvyområden, skulle produktattributen inte visas korrekt i GraphQL-svaret, vilket leder till att produkten inte visas korrekt.
  _ACP2E-3184 - [GitHub-kodbidrag](https://github.com/magento/inventory/commit/3f300077)_
* __[Cloud] Produktgrafik har fel när samma enkla produkt har tilldelats flera konfigurerbara produkter__
Tidigare returnerade grapQL ett fel för separata konfigurerbara produkter med samma enkla produkt. När den här korrigeringen har tillämpats returnerar grapQL resultat utan fel för olika konfigurerbara produkter med samma enkla produkt.
  _ACP2E-3190 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/148c3ead)_
* __[Cloud] Issue with User Authentication and Cross-Site Token Access in Multi-Site Setup__
GraphQl kundinformation och kundvagnsfrågor i installationsprogrammet för flera platser kontrollerar om kunden på en webbplats som inte är standard finns.
Tidigare arbetade frågan utan att kontrollera att kunden finns på en icke-standardwebbplats i konfigurationen av flera webbplatser.
  _ACP2E-3215 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/581b7ef1)_
* __GraphQL cart itemsV2-sidindelningen fungerar inte korrekt__
Problemet har åtgärdats genom att rätt värde för det aktuella sidargumentet har skickats i samlingsfrågan. Tidigare skickades fel värde för att ställa in den aktuella sidan, vilket orsakade problemet.
  _ACP2E-3253 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/8459b17d)_
* __[Modellvärdet för GRAPHQL] ska anges när customerCart hämtas__
GraphQL kundvagnsfråga kan nu skapa en tom kundvagn även när offerten inte är tillgänglig i databasen. Tidigare misslyckades den här åtgärden på grund av landsvalideringsproblem när en tom kundvagn skapades.
  _ACP2E-3255 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/fd5cf3af)_
* __[GraphQl] Önsklisteobjekt är synliga via GraphQl men inte synliga i storefront__
Önska produkter som inte är listade på rätt sätt när de begärs via GraphQL. Nu filtreras önskelisteprodukter baserat på den angivna butikskontexten.
  _ACP2E-3380 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/55615e61)_
* __[GraphQL] Återställ inkonsekvent e-postadress för lösenord mellan innehåll och ämne/länk__
Problemet har lösts genom att simulera rätt butik där kundens konto är registrerat när begäran om lösenordsåterställning skickas, oavsett webbplatsarkivet.
  _ACP2E-3404 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/5184c067)_
* __[Cloud] produkter GraphQL-frågan returnerar relaterade produkter som inte har tilldelats den aktuella webbplatsen__
Tidigare visades inte produkter som är relaterade till flera butiker korrekt för produktfrågan i en GraphicQL-fråga. När den här korrigeringen har tillämpats visas graphQL-frågor för produkter som är relaterade till flera butiker.
  _ACP2E-3419 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/078c387e)_
* __Om fel lagrings-ID används i GraphQL header uppstår ett allvarligt minnesfel__
Om du skickar fel lagringskod i en GraphQL-begäran leder detta inte längre till en överdriven minnesförbrukning.
  _ACP2E-3447 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/d50f6b5d)_
* __[Cloud] 500 svar på tomt Graphql-svar på 2.4.7__
Efter korrigeringen loggas inte ogiltiga grafikförfrågningar i filen exception.log.
  _ACP2E-3467 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/1984c61c)_
* __[Moln] Problem med Graphql API__
Före korrigeringen med Graphql-programservern returnerade kundadressbegäran inte de senaste data.
  _ACP2E-3492 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/3f12d152)_
* __Inaktiverad produkt visas fortfarande i relaterade, merförsäljning, korsförsäljningsobjekt i grpahQL-frågan__
Graphql ger nu korrekt respons för inaktiverade produkter med relaröd, merförsäljning och korsförsäljning
  _ACP2E-3505 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/d4de4726)_
* __[CLOUD]: GraphQl-fel Internt serverfel placeOrder-mutation__
mutationen&quot;placeOrder&quot; med information om kupongkod i begäran genererar inte längre ett internt felundantag. Ordningen har placerats korrekt. Tidigare misslyckades det med &quot;Internt serverfel&quot;.
  _ACP2E-3647 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/982b1c42)_
* __Rabatt_procent beräknas inte för paketprodukter med dynamiskt pris__
Korrigering har lagts till för rabatt_procent för product.price_details som inte visar korrekt värde för paketprodukter med dynamiskt pris aktiverat och rabattkupong tillämpad.
  _LYNX-426_
* __Paketprodukter visar fortfarande&quot;IN_STOCK&quot; när någon av dess paketerade produkter inte finns i lager__
Löste problemet med att paketprodukter fortfarande visade&quot;IN_STOCK&quot;, även när en av deras paketerade produkter inte fanns i lager.
  _LYNX-485_
* __not_available_message och only_x_left_in_stock visar inte samma tillgängliga lager__
Löste problemet där not_available_message och only_x_left_in_stock visade inkonsekvent lagertillgänglighet
  _LYNX-486_
* __fältet original_row_total returnerar fel värde__
Löste problemet med fältet original_row_total som returnerade felaktiga värden när anpassade alternativ valdes
  _LYNX-488_
* __Miniatyrbilden för grupperad produkt ska visas enligt konfigurationen     .__
Problemet har åtgärdats för att se till att den grupperade produktminiatyrbilden visas enligt konfigurationsinställningarna
  _LYNX-503_
* __Fel vid fråga av selected_options i OrderAddress__
AttributeSelectedOptions för custom_attributesV2 har uppdaterats i orderadressen för GraphQL.
  _LYNX-510_
* __original_item_price inkluderar inte rabatter__
Uppdaterat original_item_price för att inkludera rabatter.
  _LYNX-512_
* __Meddelandet Inte tillgängligt visar inte tillgänglig lagerkvantitet__
Löste felmeddelandet och felkoden för mutationen AddProductsToCart som justerades efter konfigurationen för meddelandet&quot;ej tillgänglig&quot;
  _LYNX-530_
* Statusen __&quot;OUT_OF_STOCK&quot; returneras för Simple med anpassade alternativprodukter med flervalsalternativ__
StockStatusProvider-lösaren i lagerpaketet har uppdaterats för att korrigera stock_status för enkla produkter med anpassade alternativ.
  _LYNX-532_
* __Fel (GQL): cart.itemsV2.items.product.custom_attributesV2 returnerar ett serverfel__
Löste serverfelet som uppstod när en kundvagnsfråga inkluderade en produkts anpassade attribut genom att lägga till en produkt utan anpassade attribut.
  _LYNX-533_
* __order/date_of_first_order returnerar alltid null__
Löste problemet där order > date_of_first_order alltid returnerade null.
  _LYNX-536_
* __Kunden får inte kunna avbryta en delvis levererad order__
Validering har lagts till för att hindra kunder från att annullera en delvis levererad order.
  _LYNX-544_
* __Felkoder för annullering av order baseras på felmeddelandet__
Felkoderna för orderannullering baseras nu på det specifika felmeddelandet.
  _LYNX-548_
* __Flytta tillbaka cookie-relaterade egenskaper från privat till skyddad__
Återställer synlighet för Magento\Framework\App\PageCache\Version klasskonstruktoregenskaper från privat till skyddad
  _LYNX-581_
* __Öka den högsta standardkomplexiteten för GraphQL-frågor till 1000__
Ökade standardkomplexiteten för GraphQL-frågor från 300 till 1 000.
  _LYNX-600_
* __GQL - itemsV2 > Ursprunglig radsumma, priser returneras som 0,00 USD för hämtningsbar produkt med filalternativ som har separata priser.__
Löste ett problem där nedladdningsbara produkter med alternativ för separat länkköp aktiverade returnerade $0 för artiklarV2 > total ursprunglig radsumma. Prisintervallet returnerades som $0,00 för produkter med filalternativ med separata priser.
  _LYNX-620_
* __Schema för en tabell när har skapats skiljer sig åt när du uppgraderar__
Löste ett problem där ett tillägg av en ny VARCHAR-kolumn till en befintlig tabell orsakade testfel på grund av schemaskillnader mellan nya installationer och uppgraderingar. Metoden modifyColumn() hanterar nu VARCHAR-kolumner korrekt genom att ställa in standardteckenuppsättningen och sorteringen.
  _LYNX-711_
* __GraphQl-kompatibilitet för PHP-8.4-version__
Korrigerade GraphQL-kompatibilitetsproblem med PHP 8.4 för flera olika lösare, vilket ger smidig funktionalitet. Uppdaterade filer som påverkas i modulerna CatalogRule, Customer, GiftMessage, GiftCard och GiftWrapping.
  _LYNX-772_

### GraphQL, Inventory / MSI

* __MergeCart-mutationen orsakar ett undantag när käll- och destinationskartor har samma paketobjekt__
&#39;-
  _ACP2E-2607 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/c971859e) - [GitHub-kodbidrag](https://github.com/magento/inventory/commit/db0620da)_

### GraphQL, Inventory/MSI, Performance

* __Webbplatsen stängs efter uppgradering__
Prestandan för hämtning av paketprodukter via GraphQl har förbättrats.
  _ACP2E-1716 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/ba25af8a) - [GitHub-kodbidrag](https://github.com/magento/inventory/commit/bdbf97ea)_

### GraphQL, prestanda

* __[GraphQL Resolver] Kundlösningsdata har inte verifierats från import__
GraphQL kundmatchningscache ogiltigförklaras nu som förväntat när en kund redigeras eller tas bort via import. Tidigare var cachen inte ogiltig och kunddata kunde redigeras eller tas bort under importen.
  _AC-9569 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/0574ac23)_

### GraphQL, sökning

* __GraphQL produktlista sorterar efter flera parametrar fungerar inte__
Produktsortering efter flera fält i GraphQl fungerar nu så som beskrivs i dokumentationen
  _ACP2E-2809 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/c971859e)_
* __Produktlista GraphQL-fråga begränsad till total_count 10 000 produkter endast__
Efter korrigeringen är sökresultatet inte begränsat till 10000 produkter, det blir möjligt att hämta alla produkter som matchar sökvillkoren, även om antalet är över 10000.
  _ACP2E-948 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/a4cf5e62)_

### GraphQL, testramverket

* __Magento\GraphQl\App\GraphQlCustomerMutationsTest.php Integrationstest misslyckades__
&#39;-
  _ACP2E-3363 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/a4cf5e62)_

### Importera/exportera

* __Utgåva vid produktimport när den tillhandahålls med anpassad options-typ: fil (Skapad produkt innehåller inte pris för anpassat alternativ och visar bara det första filtypstillägget som anges)__
Systemet importerar nu produktdata korrekt med anpassade alternativ av typen &#39;file&#39;, vilket säkerställer att alla angivna filtillägg visas och att priset för det anpassade alternativet inkluderas. Tidigare visades bara det första tillägget under produktimporten om ett anpassat alternativ av typen &#39;file&#39; hade fler än ett filtillägg, och priset för det anpassade alternativet saknades.
  _AC-12172 - [GitHub-problem](https://github.com/magento/magento2/issues/38805) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/38926)_
* __Fel körningstid för importåtgärd i rutnätet för importhistorik__
Vid import av rapportkörningstid visas korrekt oberoende av administratörens nationella inställningar.
  _ACP2E-2710 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/ea79f7dd)_
* __Duplicerade kunder skapas med samma e-postadress med hjälp av import__
Importering av kund med kontodelning inställd på Global, importerad kund som finns i systemet uppdateras.
Tidigare importerad kund duplicerades.
  _ACP2E-2737 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/c971859e)_
* __Lägg till/uppdatera import för produkter som duplicerar anpassningsbara alternativ__
Problemet har lösts genom att rätt butik har tilldelats till produktalternativ under CSV-import av produktalternativ.
Tidigare tilldelades till administratörsarkivet i stället för deras respektive butik.
  _ACP2E-2902 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/3a7c4d17)_
* __Kundens &quot;created_at&quot;-datum har inte konverterats till butikens tidszon vid export__
Ett datumvärde för kolumnen &#39;created_at&#39; konverteras till rätt datumformat baserat på butikens tidszon i CSV-avsnittet för kundexport.
  _ACP2E-2990 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/3056e9cb)_
* __[Cloud] Hämtar fel vid kontroll av data i importdata med CSV__
Det finns inget fel när data kontrolleras vid CSV-import. Tidigare visades felmeddelandet:&quot;Vi kan inte hitta en kund som matchar den här e-postadressen och webbplatskoden i rad(er): 1&quot; när data kontrolleras i importavsnittet med CSV från administratören.
  _ACP2E-3165 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/8459b17d)_
* __Importknappen saknas__
Åtgärda problemet med knappen Importera som saknas efter datakontroller med korrekta och felaktiga poster i CSV-filen. Tidigare visades inte importknappen efter datakontroller med korrekta och felaktiga poster i CSV-filen.
  _ACP2E-3172 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/1819fe73)_
* __Det går inte att importera den exporterade kundadressen__
Kundadressimporten fortsätter som förväntat. Tidigare godkändes inte valideringen av en kundadressimportfil om Dela kundkonton = Global, och det finns två webbplatser där standardwebbplatsen har en lista med begränsade länder och adressen som importeras är till en annan webbplats där tillåtna länder är olika
  _ACP2E-3382 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/ec7e32a9)_
* __[Cloud] Fel kvantitet i CSV-fil gav inget fel__
Vid import av Stock-källor genereras ett valideringsfel för icke-numeriska värden i kvantitetskolumnen. Om du importerar Stock-källor med ett icke-numeriskt värde i kvantitetskolumnen hade kvantiteten angetts till 0.
  _ACP2E-3448 - [GitHub-kodbidrag](https://github.com/magento/inventory/commit/5b21b7af)_
* __Felmeddelandet för dubblerad URL-nyckel som genererades när en produkt importerades är inte korrekt när URL-nyckeln redan tillhör en kategori__
Rätt felmeddelande visas vid kontroll av produktimport, när kunden försökte importera produkten när produktens URL-nyckel redan tillhör en kategori.
  _ACP2E-3455 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/d4de4726)_
* __Produktexport orsakar OOM även med en minnesgräns på 4G__
Före den här korrigeringen misslyckades produktexporten om produktattributen hade tusentals alternativvärden, även med 4G tillgängligt minne. Efter den här korrigeringen bör produktexporten avsluta exporten av csv-filen.
  _ACP2E-3475 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/1984c61c)_
* __[Cloud] Importera processer som hänger ihop med varandra__
Korrekta meddelanden visas om samma administratörsanvändare utför två eller flera importåtgärder med samma användarsession.
  _ACP2E-3527 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/d4de4726)_

### Import/export, prestanda

* __[Cloud] Produktimporttiden har ökat avsevärt__
Före korrigeringen hade importen av katalogprodukter med över 10 000 poster försämrats avsevärt. Efter korrigeringen körs importen av katalogprodukten i rätt tid.
  _ACP2E-3476 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/87d012e5)_

### Installera och administrera

* __Magento-uppgradering misslyckas på MariaDB 11.4 + 2.4.8-beta1__
Uppgraderingen bör ske utan fel.
  _AC-13242 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/7b336d0a)_
* __Ingen VCL-exportfil för lack 7-knapp på administratörspanelen__
Knappen Exportera VCL för lack 7 har lagts till på panelen Admin.
  _ACP2E-2102 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/a4fbf702)_

### Lager/MSI

* __Lageruppdatering av konfigurerbar produkt misslyckas när databasen använder prefix__
Systemet uppdaterar nu lagret av konfigurerbara produkter korrekt när prefix används i databasen, vilket förhindrar felmeddelanden och säkerställer att rätt kvantitet sparas. Tidigare uppstod ett fel när lagerkvantiteten för enkla produkter i en konfigurerbar produkt skulle sparas om databasen använde prefix.
  _AC-10750 - [GitHub-problem](https://github.com/magento/magento2/issues/38045)_
* __Google Google API-nyckel fungerar inte när Map med attribut läggs till__
Systemet har nu stöd för den senaste versionen av Google Maps API, version 3.56, vilket gör att användare kan lägga till ett innehållsblock från PageBuilder-menyn på scenen utan att några fel påträffas. Tidigare kunde användare inte lägga till ett kartinnehållsblock på grund av kompatibilitetsproblem med Google Maps API-versionen, vilket resulterade i ett felmeddelande om att något gick fel.
  _AC-11593 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/0574ac23)_
* __Det går inte att skapa leverans för orderobjekt med flera källor och skadad SKU__
Tidigare när blanktecken av misstag lades till i sku via databasen uppstår ett fel på utleveranssidan som nu är fast och automatisk trimning betraktas som ett användarvänligt fel och ingen påverkan hittades. Leveransen skapades därför.
  _AC-13922 - [GitHub-kodbidrag](https://github.com/magento/inventory/commit/c18eb5fa)_
* __[Testa] Paketprodukter med 0 lager synliga på lagerframsidan__
Paketprodukten visas inte på ytterligare webbplatser som använder extra Stock.
  _ACP2E-1411_
* __[Allvarligt fel i molnet] med produktlista med tomma utrymmen__
Systemet visar nu produktlistor korrekt utan blanksteg när produkterna är inställda på &quot;Utanför lager&quot;, vilket ger en konsekvent och korrekt visning av tillgängliga produkter. Om du tidigare angav en produkt som &quot;Out of Stock&quot; skulle det resultera i att ett tomt utrymme visas i produktlistan, vilket stör layouten och kan förvirra kunderna.
  _ACP2E-2794 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/ea79f7dd) - [GitHub-kodbidrag](https://github.com/magento/inventory/commit/b59e48ca)_
* __Det går inte att skicka ordern när MSI-upphämtningsarkivet är aktiverat__
Förbättrade lagerprestanda när det gäller att skapa leveranser om många källor skulle kunna hämtas från butiken
  _ACP2E-3335 - [GitHub-kodbidrag](https://github.com/magento/inventory/commit/9f3e63d1)_
* __Cron reindex misslyckas med att uppdatera produkttillgänglighet på klientsidan__
Tidigare fanns produkterna inte i lager vid fronten efter att ha uppdaterat backorder-statusen via REST API. Efter att ha uppdaterat restorderstatusen via REST API visas nu produkterna som i lager.
  _ACP2E-3355 - [GitHub-kodbidrag](https://github.com/magento/inventory/commit/e6fe0aa7)_
* __Det går inte att lägga till bilder i konfigurerbara om MSI är aktiverat.__
Bildöverföring för konfigurerbar produkt kommer nu att fungera som förväntat när lagermodulen används. Tidigare fungerade inte bildöverföringen
  _ACP2E-3357 - [GitHub-kodbidrag](https://github.com/magento/inventory/commit/fdf409aa)_
* __Problem med paketprodukt + MSI i Clean M2.4.7-p3__
Tidigare gick det inte att spara den enkla produkten för lagerpaketprodukter efter duplicering med samma enkla produkt. När den här korrigeringen har tillämpats kan den enkla produkten sparas utan några undantag.
  _ACP2E-3470 - [GitHub-problem](https://github.com/magento/magento2/issues/39358) - [GitHub-kodbidrag](https://github.com/magento/inventory/commit/0208e433)_

### Lager/MSI, Sök

* __Alla produkter indexeras med [ is_out_of_stock] = 1 när SKU inte är inställt som ett sökbart attribut__
Efter korrigeringen är &quot;is_out_of_stock&quot; i katalogens sökindex korrekt, även när sku inte är sökbar.
  _ACP2E-3413 - [GitHub-kodbidrag](https://github.com/magento/inventory/commit/5b21b7af)_

### Beställning

* __Översiktsskärm för backend-order: Ej beställd kvantitet synlig på orderartikelnivå__
Systemet visar nu antalet underordnade artiklar i kolumnen för antal på översiktsskärmen för backend-order. Detta gör att användarna kan spåra status för alla objekt i en ordning på rätt sätt. Tidigare visade kolumnen för kvantitet endast antalet artiklar som beställts, fakturerats och levererats, men inte antalet beställda artiklar.
  _AC-10828 - [GitHub-problem](https://github.com/magento/magento2/issues/38252) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/38320)_
* __[Problem] Fel lagrings-ID används i orderadressrenderaren__
Systemet använder nu det butiks-ID som är kopplat till en beställning korrekt vid återgivning av orderadressen, vilket säkerställer att adresserna formateras korrekt enligt deras respektive butiks-ID. Tidigare använde systemet felaktigt det aktuella butiks-ID:t, vilket kunde leda till felaktig adressformatering om flera beställningsmejl från olika butiker behövde skickas.
  _AC-10994 - [GitHub-problem](https://github.com/magento/magento2/issues/38412) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/37932)_
* __Cachelagring av JoinProcessor__
Systemet använder nu JoinProcessor korrekt för varje iteration, även med efterföljande anrop, vilket ger korrekt datahämtning. Tidigare hade JoinProcessor felaktigt markerats som använd i upprepade iterationer, vilket ledde till fel vid datahämtning.
  _AC-11690 - [GitHub-problem](https://github.com/magento/magento2/issues/27504) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/37550)_
* __[Utleverans] Leveranspriset skiljer sig åt i den utskrivna PDF-filen__
Systemet visar nu fraktpriser i utskrivna PDF-filer korrekt enligt momskonfigurationsinställningarna, vilket säkerställer konsekvens mellan vysidan för försäljningsorderfaktura och den utskrivna fakturan. Tidigare undantogs moms för det fraktpris som visades i den utskrivna PDF, oavsett momskonfigurationsinställningar.
  _AC-11798 - [GitHub-problem](https://github.com/magento/magento2/issues/38608) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/38595) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/1bafc571)_
* __Ändra ordning med en borttagen överordnad konfigurerbar produkt__
När du nu beställer om den borttagna produkten visas inte knappen för att ändra ordning
  _AC-13839 - [GitHub-problem](https://github.com/magento/magento2/issues/39568) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/39601)_
* __[Problem] Åtgärda fel \Magento\Sales\Model\Order\Email\Container\Template::$id property__
Detta korrigerar det dåliga fotot för \Magento\Sales\Model\Order\Email\Container\Template:$id, $id är egentligen typen int, men i verkligheten är det en sträng.
  _AC-13924 - [GitHub-problem](https://github.com/magento/magento2/issues/39151) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/39150)_
* __Det går inte att spara ändringar av telefonnummer i befintlig orderinformation__
Nu kan användaren lägga till det internationella prefixet 00 i telefonfältet till orderadressen
  _ACP2E-2622 - [GitHub-problem](https://github.com/magento/magento2/issues/38201) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/12e071c3)_
* __E-postmeddelanden kan inte skickas__
Systemet innehåller nu ett konfigurationsalternativ för async_sending_try för att ange antalet försök att skicka ett e-postmeddelande innan det stoppas, vilket förbättrar hanteringen av misslyckade e-postmeddelanden när asynkron sändning är aktiverat. Tidigare, om ett e-postmeddelande inte kunde skickas, skulle systemet kontinuerligt försöka skicka om det, vilket resulterar i en oändlig loop med felmeddelanden i systemloggen.
  _ACP2E-2734 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/b2286ecf)_
* __[Cloud] Beställningsstatusen har ändrats till slutförd när en delvis återbetalning av en delvis levererad order har gjorts__
När du utfärdar en kreditnota ändras orderstatusen inte längre till&quot;slutförd&quot; om det finns artiklar som ännu inte har levererats.
  _ACP2E-2756 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/7e0e5582)_
* __[CLOUD] Det går inte att inaktivera Skicka e-post från administratörsgränssnittet som Dev Docs__
Systemet förhindrar nu att e-postmeddelanden skickas korrekt när e-postkommunikation är inaktiverad. Dessa e-postmeddelanden skickas inte längre när e-postkommunikation har återaktiverats. Tidigare skickades säljmeddelanden som initierats medan e-postkommunikation inaktiverades när e-postkommunikation återaktiverades.
  _ACP2E-3002 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/c8931218)_
* __Beställningen har stängts utan helt återbetalas__
Systemet behåller nu orderstatusen som Bearbetning och fakturastatusen som Väntande när en order med en ej infångad betalning har en leverans skapad. Detta garanterar att beställningar endast markeras som&quot;Stängda&quot; efter att de har återbetalats helt. Om du tidigare skapade en leverans för en order med en väntande faktura skulle orderstatusen felaktigt ändras till Stängd.
  _ACP2E-3045 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/6a185204)_
* __[Cloud] Det går inte att skapa beställning i en administratör på en butik om bara standardfaktureringsadressen inte har konfigurerats__
Nu relevant felmeddelande&quot;En kund med samma e-postadress finns redan på en associerad webbplats.&quot; visas om en kund inte har en standardfaktureringsadress och försöker skapa en order i en annan butik.
  _ACP2E-3311 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/d75cff27)_
* __Administratören har skickat dubblettbeställningsförfrågningar__
Tidigare gick det att klicka på knappen &quot;Skicka beställning&quot; på administratörspanelen flera gånger eller aktivera den genom att trycka på Retur flera gånger, vilket orsakade fel i dubbletter eller ordningsföljd. Nu kan du förhindra ytterligare åtgärder tills ordern har bearbetats fullständigt, så att bara en order skickas.
  _ACP2E-3416 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/5184c067)_
* __Admin kan fortfarande göra beställningar även utan betalningsmetod__
Tidigare vald betalningsmetod behålls nu när betalningsmetoden visas igen i listan över tillgängliga betalningar.
  _ACP2E-3425 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/d50f6b5d)_
* __Objekten dupliceras när vi har skapat en beställning från Admin i webbläsaren Mozilla Firefox__
Produkter som läggs till med&quot;Lägg till produkter efter SKU&quot; dupliceras inte längre i Firefox när en beställning skapas i en administratör.
  _ACP2E-3518_

### Order, betalningar

* __Admin kan fortfarande göra beställningar även utan betalningsmetod__
Tidigare kunde handlaren göra beställningar från adminpanelen utan att välja någon betalningsmetod. Nu måste handlaren ha en betalningsmetod för att kunna göra en beställning.
  _ACP2E-3233 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/fd5cf3af)_

### Order, returer

* __Orderåterbetalning resulterar i dubblettkreditnota__
När två identiska begäranden verkställs samtidigt och återbetalningar skickas över REST API skapas inte längre dubbla kreditnotor.
  _ACP2E-2982 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/a4fbf702)_

### Order, skatt

* __[CLOUD] Felaktig base_row_total i API för RESTFUL-order när gränsöverskridande transaktioner aktiveras och kupongrabatter tillämpas__
Korrekt base_row_total returneras nu från RESTFUL-order-API när gränsöverskridande transaktioner är aktiverade och kupongrabatt tillämpas.
  _ACP2E-3003 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/9af794a4)_

### Övriga

* __[Braintree] Återbetala onlinelagringstransaktion som transactionid-returned__
  _BUNDLE-3394_
* __[Braintree] + [CLOUD] Braintree-beställningar (kreditkort) kan inte dela upp tilläggen__
  _BUNDLE-3421_
* __[Braintree] [Cloud]Braintree SSL-certifikat upphör att gälla den 30 juni__
  _BUNDLE-3422_
* __private_content_version-cookie returnerad i GQL-frågor__
Korrigerade ett problem där cookien private_content_version returnerades i GraphQL-frågor, även när sessionscookien inaktiverades. Cookien inkluderas inte längre i GraphQL-svar när sessionen inaktiveras, som förväntat.
  _LYNX-339_
* __Serverfel i e-postprops i fysiska presentkortsfrågor__
Ett problem har korrigerats där frågor för sender_email och mottagare_email på fysiska presentkort resulterade i ett serverfel. Dessa utkast returneras nu korrekt för virtuella presentkort och frågebeteendet är konsekvent.
  _LYNX-366_
* Attributet __is_available i CartItemInterface returnerar alltid false för konfigurerbara produkter__
Ett problem har korrigerats där attributet is_available i CartItemInterface alltid returnerade false för konfigurerbara produkter i lager. Nu visas tillgängligheten som true när det är tillämpligt.
  _LYNX-380_
* Attributet __is_available i CartItemInterface returnerar true även när det säljbara lagret är mindre än kvantiteten för produkten__
Korrigerade ett problem där attributet is_available i CartItemInterface felaktigt returnerade true även när kvantiteten i kundvagnsartikeln överskred det säljbara lagret.
  _LYNX-382_
* Attributet __only_x_left_in_stock i ProductInterface är inte korrekt för konfigurerbara produkter__
Ett problem har korrigerats där attributet only_x_left_in_stock i ProductInterface inte korrekt återspeglar det tillgängliga lagret för konfigurerbara produktvarianter i kundvagnen. Nu motsvarar det enda_x_left_in_stock-värdet korrekt de faktiska lagernivåerna, vilket säkerställer att korrekta lagerdata returneras i kundvagnens GQL-fråga.
  _LYNX-395_
* __Platshållarminiatyrbilden returneras när en enkel produkt läggs till i kundvagnen i en grupperad produkt__
Ett problem har korrigerats där en enkel produkt (en del av en grupperad produkt) i kundvagnen returnerade en platshållarminiatyrbild, även när produkten hade en tilldelad bild.
Korrigeringsinformation:
* Produktminiatyrbilden visar nu den tilldelade bilden korrekt om den är tillgänglig.
* Miniatyrbildsmarkeringen respekterar administratörskonfigurationen under:
Stores > Configuration > Sales > Checkout > Shopping Cart > Group Product Image.
På så sätt får du en konsekvent miniatyrbildsfunktion för grupperade produkter baserat på butiksinställningarna.
  _LYNX-399_
* __Kundens anpassade alternativattribut fungerar inte med heltalsvärden__
Korrigerade ett problem där kundens anpassade alternativattribut inte fungerade när det returnerade värdet var ett heltal. Anpassade alternativ hanterar nu korrekt och returnerar heltalsvärden som förväntat.
  _LYNX-400_
* __Internt serverfel vid försök att hämta priceDetails för Bundle-produkter med dynamiskt pris__
Löste ett problem där frågor om pris_details för paketprodukter med dynamisk prissättning via GraphQL resulterade i ett internt serverfel. Den här förbättringen säkerställer stabila kundvagnsfrågor vid arbete med paketprodukter som konfigurerats med dynamiska priser.
  _LYNX-402_
* __only_x_left_in_stock returnerar alltid 0 för konfigurerbara produkter__
Löste ett problem där attributet only_x_left_in_stock alltid returnerade 0 för konfigurerbara produkter när det lades till med den överordnade SKU:n med alternativ.
Korrigeringsinformation:
* Värdet only_x_left_in_stock återger nu korrekt stocken för den valda underordnade varianten i stället för den överordnade SKU:n.
* På så sätt ser du till att lagernivåerna visas korrekt för konfigurerbara produktvariationer i kundvagnen och på produktsidorna.
  _LYNX-403_
* __GraphQL-fel: Filtypen stöds inte i frågan om anpassningsbara alternativ__
Korrigerade ett problem där GraphQL returnerade ett fel för anpassningsbara alternativ av typen &#39;file&#39; i kundvagnsobjekt. Frågan returnerar nu korrekt information för alla anpassningsbara alternativtyper, inklusive filbaserade alternativ, utan att orsaka fel.
  _LYNX-405_
* __GraphQL-frågan returnerar inte korrekt beräknat normalpris för anpassningsbara produkter__
Ett problem har korrigerats där GraphQL inte returnerade korrekt beräknat normalpris för anpassningsbara produkter. Frågan innehåller nu korrekt det beräknade ordinarie priset med anpassningsbara värden (t.ex. $125) i egenskapen prices, som återspeglar både baspriset och eventuella ytterligare anpassningskostnader.
  _LYNX-411_
* __Använda skatter via EstimatedTotals finns kvar med uppdaterade mutationer__
Korrigerade ett problem med mutationen EstimatedTotals där tillämpade skatter bestod på en vagn även efter att regionen eller postkoden uppdaterats. Mättnaden uppdaterar nu korrekt de pålagda skatterna när värden mellan region och postnummer ändras, vilket säkerställer att endast rätt momsregel tillämpas baserat på aktuella kundvagnsdata.
  _LYNX-412_
* Attributet __is_available i CartItemInterface returnerar true även när det säljbara lagret är mindre än kvantiteten för produkten__
Korrigerade ett problem där attributet is_available i CartItemInterface felaktigt returnerade true även när det säljbara lagret var lägre än den begärda produktkvantiteten. Fältet is_available returnerar nu korrekt false när produktens kvantitet överstiger det tillgängliga lagret.
  _LYNX-420_
* __Det går inte att lägga till kupong i kundvagn för enbart fraktrabatt__
Korrigerade ett problem där en kupong inte kunde användas i en kundvagn för enbart frakt-rabatter. Kupongen tillämpas nu korrekt på fraktbeloppet när en försäljningsregel utan produktvillkor används, vilket säkerställer att den förväntade rabatten tillämpas på leveranskostnaden.
  _LYNX-421_
* __Normalpris för produkt med 12 decimaler och fel värde__
Ett problem har korrigerats där värdet regular_price i sökvägarna product.price_range.maximum_price och minimum_price i GraphQL inte matchade katalogpriset när flera skattesatser tillämpades. I Cart Summary visas nu katalogpriset enhetligt för alla momskonfigurationer, vilket ger korrekt enhetspris, beräkning av totalkostnader och rabattkontroller.
  _LYNX-425_
* __GraphQL-serverfel i varukorgen med produkt som inte ingår i paketet__
Korrigerade ett problem där GraphQL returnerade ett internt serverfel när en kundvagn som innehåller en paketerad produkt med ett objekt som inte finns i lager hämtades, särskilt när frågan innehöll egenskapen itemsV2. GraphQL returnerar nu korrekt en lista med objekt med relevanta felmeddelanden som är kopplade till den paketerade produktposten, som förväntat.
  _LYNX-430_
* __Det går inte att skapa en adress med anpassade attribut__
Korrigerade ett problem med mutationen createCustomerAddress som förhindrade att adresser med nödvändiga anpassade attribut skapades. mutationen hanterar nu anpassade adressattribut korrekt när lämplig nyttolast anges.
  _LYNX-441_
* __GraphQL-serverfel i varukorgen med endast_x_left_in_stock för den paketerade produkten__
Ett problem har korrigerats där hämtning av en kundvagn som innehåller en paketerad produkt med fältet only_x_left_in_stock i GraphQL-frågan resulterade i ett internt serverfel. GraphQL returnerar nu korrekt ett flyttal eller null för fältet only_x_left_in_stock utan fel.
  _LYNX-447_
* __GraphQL-fel vid borttagning av andra produkter med otillräcklig konfigurerbar produkt i kundvagn__
Ett problem har korrigerats där ett försök att ta bort lageruppbyggda produkter från vagnen resulterade i ett GraphQL-fel &quot;Begärd kvantitet är inte tillgänglig&quot; om vagnen även innehöll konfigurerbara produkter med otillräckligt lager. Borttagningen fungerar nu som förväntat utan att utlösa fel.
  _LYNX-464_
* __Det går inte att lägga till produkter på grund av att SKU:n i mutationen är skiftlägeskänslig__
Ett problem där mutationen addProductsToCart returnerade felet PRODUCT_NOT_FOUND när SKU:er med olika hölje användes har åtgärdats. Mutationen hanterar nu SKU:er som inte är skiftlägeskänsliga, vilket säkerställer konsekvens med katalogtjänstfrågor och PDP-beteende.
  _LYNX-469_
* __Product attribute > trademark short form&amp;trade; is returned as &amp;trade;__
Ett problem med teckenkodning med produktnamnet för GraphQL API har åtgärdats
  _LYNX-603_
* __updateCustomerEmail - mutationsproblem__
Löste ett problem med updateCustomerEmail-mutationen där kunder utan nödvändiga anpassade attribut (tillagda efter att kontot skapats) inte kunde uppdatera sin e-post.
  _LYNX-619_
* __Mutation setShippingAddressesOnCart returnerar ett fel när pickup_location_code används__
Korrigerade ett problem där mutationen setShippingAddressesOnCart returnerade ett fel när koden för pickup_location användes utan att ange customer_address_id eller address. Mmutationen gör att det nu går att ange en leveransadress med bara koden pickup_location_code.
  _LYNX-626_
* __Listan CustomerOrder.items_eligibility_for_return måste vara konsekvent med orderobjekten__
Lösta inkonsekvenser med rätt till retur i order:
1. Listan CustomerOrder.items_eligibility_for_return överensstämmer nu med faktiska orderartiklar.
2. Fältet OrderItemInterface.eligibility_for_return returnerar korrekt false när hela kvantiteten redan har returnerats.
3. CustomerOrder.items_eligibility_for_return innehåller nu bara objekt som inte redan håller på att returneras.
   _LYNX-627_
* __Lägg till quantity_return_requested-fält__
Lade till fältet quantity_return_requested i OrderItemInterface, vilket gör att du kan identifiera den kvantitet av artiklar för vilka en retur har skickats. Detta förbättrar returspårningen tillsammans med det befintliga fältet quantity_returned.
  _LYNX-628_
* __Tillgängliga beställningsåtgärder får inte innehålla RETURN efter att returer har skapats för alla artiklar i fullständigt antal__
Korrigerade ett problem där fältet available_actions i GraphQL customer.orders-frågan felaktigt inkluderade RETURN efter att en fullständig retur skapades för alla artiklar. RETURN-åtgärden tas nu bort korrekt när returprocessen är klar.
  _LYNX-634_
* __Storefront-kompatibilitet - Uppdatera logik för att hämta tabellnamn med prefix och andra mindre förbättringar__
Uppdaterad logik för att hämta tabellnamnet med prefixet (relaterat till SCP-ändringar).
  _LYNX-637_
* __Spara i adressboken fungerar inte när du använder fältet same_as_shipping för setBillingAddressOnCart GQL__
Korrigerade ett problem där leveransadressen inte sparades i kundens adressbok när mutationen setBillingAddressOnCart för GraphQL användes med samma_as_shipping-fält inställt på true. Leveransadressen lagras som förväntat.
  _LYNX-643_
* __Ordna order_id i mutationer__
Standardiserade indata för order_id i mutationer och uppdaterade e-postmallen för bekräftelse av orderavslutning så att inkrement-ID visas i stället för order-ID.
  _LYNX-650_
* __CustomerOrder visar inte orderkommentarerna__
Löste ett problem med CustomerOrder om att inkludera orderkommentarer i GraphQL-frågor om gäst- och kundorder.
  _LYNX-651_
* __original_item_price får inte innehålla någon rabatt__
Logiken för original_item_price i GraphQL Cart Item-priser har uppdaterats för att exkludera rabatter.
  _LYNX-652_
* __Paketprodukter visar fortfarande&quot;IN_STOCK&quot; när någon av dess paketerade produkter inte finns i lager__
Löste ett problem där product.stock_status för paketprodukter fortfarande visade &quot;IN_STOCK&quot; även när en av de paketerade artiklarna inte fanns i lager.
  _LYNX-681_
* __kundfrågan returnerar Internt serverfel om det finns ett värde för borttaget anpassat attribut för en kund__
Korrigerade problemet där kundfrågan returnerade ett internt serverfel när ett borttaget anpassat attribut fortfarande hade ett lagrat värde. Nu returneras ett felmeddelande om ett attribut som inte finns begärs. Nödvändig cache görs ogiltig när kundens anpassade attribut tas bort.
  _LYNX-686_
* __Åtgärdsparameter för att returnera och avbryta bekräftelselänkar__
Åtgärdsparameter har lagts till för att returnera och avbryta e-postrelaterade bekräftelselänkar
  _LYNX-687_
* __Användarens bekräftelse-URL omdirigeras till orderstatussidan eftersom den saknar orderRef (för GuestRMA)__
Parametern orderRef har lagts till i länken i e-postmeddelandet med RMA-bekräftelse för gästen
  _LYNX-688_
* __Användarens bekräftelse-URL omdirigeras till orderstatussidan eftersom den saknar orderRef__
Added orderRef parameter to the link in gästorder cancel confirmation email
  _LYNX-689_
* __Problem med kundfråga när RMA är inaktiverat__
GraphQL-logiken har uppdaterats för att säkerställa att tidigare skapade returtecken förblir tillgängliga även när RMA är inaktiverat globalt. Felmeddelandet har tagits bort för att förbättra butikens användargränssnitt, vilket säkerställer att kunderna fortfarande kan se sina tidigare returer.
  _LYNX-690_
* __GraphQL returnerar inte uppdaterade kundvagnsdata när kuponger i konflikt används__
Ett problem har korrigerats där en kupong med högre prioritet som använder en konflikt resulterade i ett felmeddelande utan att uppdaterade kundvagnsdata returnerades. När en ny kupong ogiltigförklarar den befintliga, returnerar mutationen korrekt vagnen med den giltiga kupongen.
  _LYNX-696_
* __Det går inte att returnera null för det icke-nullbara fältet &quot;TaxItem.title&quot; i placeOrder GQL__
Korrigerade ett problem där placeOrder-mutationen misslyckades med ett internt serverfel på grund av ett null-värde för det icke-nullbara fältet TaxItem.title. Nu returnerar fältet alltid ett giltigt värde, vilket säkerställer att ordern läggs korrekt.
  _LYNX-699_
* __BeräknaSummor: Rabatterna är null för virtuella produkttyper__
Löste problemet med mutationen estimatTotals som returnerade null för rabatter när en rabattkod tillämpas på en vagn som innehåller virtuella produkter.
  _LYNX-702_
* __Paketprodukten returnerar inte rätt rabatt i procent och belopp__
Nya egenskaper, &quot;catalog_disc&quot; och &quot;row_catalog_disc&quot;, har införts för katalogobjektpriser för att visa rätt rabattbelopp och procentsatser på både rad- och artikelnivå.
  _LYNX-703_
* __Konfiguration av presentationsmeddelande på produktnivå__
Korrigerade ett problem där presentmeddelanden inte tillämpades på produktnivån när de var globalt inaktiverade. Om presentmeddelanden nu är aktiverade för en viss produkt kan de läggas till med mutationen updateCartItems och sparas och återspeglas korrekt.
  _LYNX-714_
* __Problem med att ta bort presentomslutning från vagnsartikel__
Ett problem har korrigerats där borttagning av presentomslutning från en kundvagnsartikel med mutationen updateCartItems inte fungerade som förväntat. Nu fungerar både att tillämpa och ta bort presenter korrekt utan fel.
  _LYNX-717_
* __Den matchande registrerade kundfunktionen fungerar inte i Boilerplate och trackViewedProduct-mutationen måste aktiveras för gäster.__
Exponerad trackViewedProduct-mutation för att spåra produktvyhändelser för kunder och gäster
  _LYNX-751_
* __cart.rules-frågan returnerar fel i stället för en tom array om inga aktiva kundvagnsregler tillämpas__
Korrigerade frågan cart.rules så att den returnerar en tom array i stället för ett fel när inga aktiva kundvagnsregler tillämpas.
  _LYNX-757_
* __Utfärdar hämtning av presentomslag för varukorgsartiklar__
Uppdaterad hämtningslogik för att returnera presentförpackningsalternativ för artiklar när de är globalt inaktiverade men aktiverade på produktnivå
  _LYNX-758_
* __GraphQL-anrop med OPTIONS-metod returnerar 500 svarskoder när kompatibilitetspaketet för adobe-commerce/storefront är installerat__
Ett problem har korrigerats där GraphQL anrop med OPTIONS-metoden returnerade ett 500 internt serverfel när kompatibilitetspaketet adobe-commerce/storefront installerades. Slutpunkten returnerar nu korrekt ett svar på 200/204 som förväntat.
  _LYNX-778_

### Andra utvecklingsverktyg

* __[Problem] Åtgärda HTML-syntaxfel i visual.phtml__
Systemet stänger nu starttaggen i filen visual.phtml korrekt, vilket säkerställer korrekt HTML-syntax. Tidigare stängdes inte starttaggen korrekt, vilket orsakade ett syntaxfel i HTML.
  _AC-10658 - [GitHub-problem](https://github.com/magento/magento2/issues/38247) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/37457)_
* __[Problem] Ändrad &quot;aktiv&quot; till &quot;aktiverad&quot; i bin/magento-underhåll:statuskommando__
Systemet ger nu mer korrekta statusmeddelanden för kommandot för underhållsläge, vilket ändrar statusen från&quot;aktiv&quot; till&quot;aktiverad&quot; och från&quot;inte aktiv&quot; till&quot;inaktiverad&quot;. Tidigare visades statusmeddelandet för kommandot för underhållsläge som &quot;active&quot; eller &quot;not active&quot;, vilket kan leda till förvirring.
  _AC-11474 - [GitHub-problem](https://github.com/magento/magento2/issues/38486) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/38410)_
* __Navigering i kategoriträdet leder till fel i Redis: &quot;Redis-sessionen överskrider samtidiga anslutningar&quot;__
  _AC-12571 - [GitHub-problem](https://github.com/magento/magento2/issues/38851) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/0611e750)_
* __CSP-problem i kombination med dev/css/use_css_critical_path__
Nu läses CSS-filer in asynkront på utcheckningssidor korrekt, även när inställningen &#39;dev/css/use_css_critical_path&#39; är aktiverad, vilket säkerställer att sidorna återges med rätt CSS-format. Tidigare förhindrade en begränsad CSP (Content Security Policy) infogad JavaScript från att köras, vilket medförde att CSS-filer inte lästes in som förväntat.
  _AC-12731 - [GitHub-problem](https://github.com/magento/magento2/issues/39020) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/39040)_
* __Det går inte att generera spärrmetoden korrekt i `setup:di:compile` command__ om en virtuell typ används för att konfigurera plugin-programmet.
Systemet genererar nu snittometoder korrekt när en virtuell typ används för att konfigurera ett plugin-program, vilket ger enhetliga resultat oavsett om det är förkompilerat eller körtidskompilerat. Tidigare genererade systemet felaktiga resultat vid förkompilering jämfört med körtidskompilering.
  _AC-13398 - [GitHub-problem](https://github.com/magento/magento2/issues/33980) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/38141)_
* __Det går inte att hämta filer från datainsamlaren__
När du hämtar säkerhetskopian visas inte längre en tom sida i stället för att filen hämtas.
  _ACP2E-3441_
* __Adobe Commerce 2.4.7-p3-enhetstester misslyckas__
Inga versionsinformation krävs.
  _ACP2E-3631 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/982b1c42)_

### Betalnings-/betalningsmetoder, beställning

* __Information om betalningskreditkort som sparats för senare bruk visas inte på sidan med lagrade betalningsmetoder__
Tidigare pappersbaserade betalningsflödesdetaljer Kreditkortsinformation som sparats för senare bruk visades inte på sidan med lagrade betalningsmetoder, som nu är fast kreditkortsinformation visas på sidan med lagrade betalningsmetoder.
  _AC-13699 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/96dec499)_

### Betalningar

* __Betalningen för kreditkort (Payflow Link) fungerar inte__
Tidigare hämtningsfel (betalningen nekades) vid beställning med kreditkort efter att korrigeringsordern har placerats ut.
  _AC-13414 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/a68324bc)_
* __Betalningsflödet skapar en ny transaktion varje gång vi klickar på knappen Hämta på skärmen Visa transaktion__
Systemet hämtar nu transaktionsinformation korrekt utan att skapa en ny betalningstransaktion varje gång knappen Hämta klickas på skärmen Visa transaktion. Tidigare skapades en ny betalningstransaktion felaktigt för en beställning som redan hade betalats när du klickade på knappen Hämta.
  _ACP2E-2841 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/b2286ecf)_
* __Senare betalningsmeddelande visas inte i PDP för kanadensiskt betalningsmottagarkonto__
Systemet visar nu PayLater-meddelandet korrekt för kanadensiska PayPal-handelskonton på produktinformationssidan (PDP) när köparens land kan avgöras från faktureringsadressen eller leveransen för kontot. Tidigare visades inte PayLater-meddelandet på grund av en saknad parameter, vilket resulterade i ett fel i webbläsarkonsolen.
  _ACP2E-3028 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/6a185204)_
* __Återbetalning av PayPal-order resulterar i dubblettkreditnota__
Ett problem med samtidig användning av IPN-skapade kreditnotor för PayPal-betalningstjänsten har korrigerats.
  _ACP2E-3143 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/d01ee51e)_
* __Kundprisregeln fungerar inte för PayPal__
Korrekt belopp visas på PayPal-sidan när rabatten tillämpas med betalningsmetod
  _ACP2E-3163 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/7377de59)_
* __[Cloud]-användare med en specifik roll kan inte logga in__
Administratörsanvändare med roll som endast innehåller PayPal-avsnittsåtkomst kan nu logga in utan fel
  _ACP2E-3208 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/66dea0de)_

### Prestanda

* __Problem med standardinställningar för produktattribut__
Systemet tillåter nu användare att avmarkera ett standardalternativ för ett produktattribut och ser till att attributet inte alltid har en standarduppsättning. Tidigare fanns det inget sätt att avmarkera ett produktattribut när ett standardvärde angavs, vilket innebar att attributet alltid hade en standarduppsättning.
  _AC-11932 - [GitHub-problem](https://github.com/magento/magento2/issues/38703) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/7d5e3906)_
* __[Utgåva] Kodrensning och lägg till nytt kritiskt huvudblock och flytta kritiska CSS före resurser__
Systemet innehåller nu ett nytt kritiskt head-block och flyttar kritisk CSS före resurser, vilket gör det möjligt att anpassa och optimera prestanda mer i förgrunden. Tidigare placerades inte den kritiska CSS-koden före resurserna, vilket begränsade möjligheterna till anpassning och optimering.
  _AC-12000 - [GitHub-problem](https://github.com/magento/magento2/issues/38748) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/35580)_
* __Temakompileringen avbryts när mysql-värden innehåller portinformation__
Systemet hanterar nu konfigurationen av MySQL-värden som innehåller portinformation, vilket säkerställer att temat kompileras korrekt. Tidigare misslyckades temakompileringen om konfigurationen MySQL-värd i databasanslutningen innehöll portinformation.
  _AC-12176 - [GitHub-problem](https://github.com/magento/magento2/issues/38799) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/38842)_
* __Stöd för Symfonys CommandLoaderInterface i Magento CLI__
Denna ändring minskar initieringstiden för Magento CLI-programmet genom att tillåta fördröjd initiering av kommandon tills de behövs.
  _AC-13471 - [GitHub-problem](https://github.com/magento/magento2/issues/29266) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/29355)_
* __Prestandaproblem vid inläsning av produktattribut i kundvagnsregler__
Förbättrade frågeprestanda för försäljningsregler - från ca 150 ms till ensiffriga ms.
  _ACP2E-2494 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/ba25af8a)_
* __Pris, partiell indexering__
Prestandan för partiell indexering av pris har förbättrats genom att några av de borttagningsfrågor som används i indexeringsprocessen har optimerats.
  _ACP2E-2673 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/ba25af8a)_
* __Beställningen avvisas vid konfiguration av flera butiker när Async-order-bearbetning + Villkor används__
Beställningar från icke-standardwebbplatser med aktiverade villkor bearbetas nu.
Innan de avvisades automatiskt.
  _ACP2E-2850 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/57a32313)_
* __Det tar lång tid att köra anrop från API:t för beställningsåterställning__
Systemet kör nu anropet till API:t för orderraster inom en rimlig tidsram, vilket förbättrar prestandan när ett stort antal order hämtas. Tidigare tog det lång tid att köra anropet till API:t för orderraster, vilket orsakade fördröjningar när ett stort antal order hämtades.
  _ACP2E-2910 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/001e5188)_

### Prestanda, marknadsföring

* __Indexeraren för försäljningsregel slutade köra__
Systemet slutför nu försäljningsregelindexeraren även med ett stort antal kombinerade filtergrupper, vilket säkerställer att kundvagnsregelvillkoren tillämpas som förväntat. Tidigare kunde indexeraren för försäljningsregeln inte slutföras när det fanns ett stort antal kombinerade filtergrupper, vilket ledde till ett felmeddelande och förhindrar att villkoren för kundvagnsregeln tillämpades.
  _ACP2E-2617_

### Priser

* __Magento2.4.6-p4 Order API Simple Item missing price__
Systemet visar nu priset på enkla produkter korrekt när det efterfrågas via Order API, vilket ger korrekt datarepresentation. Tidigare visades priset på enkla produkter felaktigt som noll i API-svaret.
  _AC-11810 - [GitHub-problem](https://github.com/magento/magento2/issues/38603)_
* __Löpande avrundningsfel i katalogregel__
  _AC-13855 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/276e0acd)_

### Produkt

* __Specialtecken i det konfigurerbara associerade produktnamnet konverteras till HTML-entiteter.__
Systemet behåller nu specialtecken i namnen på associerade produkter korrekt när en konfigurerbar produkt redigeras, vilket förhindrar att de konverteras till HTML-enheter. Tidigare konverterades specialtecken i associerade produktnamn till HTML-enheter när den konfigurerbara produkten redigerades.
  _AC-10535 - [GitHub-problem](https://github.com/magento/magento2/issues/38146) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/38447)_
* __Funktionen GetById för produktdatabasen skapar inte rätt cachenyckel__
Systemet skapar nu en cachenyckel korrekt i funktionen GetById för ProductRepository, oavsett om detta lagrings-ID skickas som en sträng eller ett heltal. Detta garanterar att produkten hämtas från minnet vid efterföljande anrop, vilket förbättrar prestandan. Tidigare skulle systemet hämta produkten från databasen varje gång funktionen anropas, även med samma parametrar, på grund av att en felaktig cachenyckel skapades.
  _AC-10947 - [GitHub-problem](https://github.com/magento/magento2/issues/38384) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/38433)_
* __[Utgåva] [MFTF] AdminClickAddOptionForBundleItemsActionGroup__
Systemet innehåller nu AdminClickAddOptionForBundleItemsActionGroup, vilket förbättrar administratörspanelens funktioner. Den här åtgärdsgruppen var inte tillgänglig tidigare.
  _AC-11992 - [GitHub-problem](https://github.com/magento/magento2/issues/30857) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/30838)_
* __[Problem] Åtgärda stavfel i PHPDoc-block__
Systemet tar nu bort en okänd refererad variabel i PHPDoc korrekt för $helper-variabeldeklarationen, vilket gör koden tydligare och exaktare. Tidigare orsakade den här okända refererade variabeln i PHPDoc förvirring och potentiella fel i koden.
  _AC-13173 - [GitHub-problem](https://github.com/magento/magento2/issues/38961) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/38940)_
* __[Problem] Åtgärdat brutet paket och hämtningsbar layout för produktsidor i Magento >= 2.4.7__
Layouten för paket och nedladdningsbara produktsidor har korrigerats, vilket ger en konsekvent och korrekt visning på alla enheter. Tidigare hade dessa sidor layoutproblem på grund av en omorganisering av produktinformationsmediablocket.
  _AC-13423 - [GitHub-problem](https://github.com/magento/magento2/issues/39403) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/6cfb9b6b)_
* __AlertProcessor - Argument #2 ($storeId) måste vara av typen int, strängen anges__
Systemet utlöser nu produktvarningsmeddelanden korrekt genom att se till att butiksidentifieraren har rätt datatyp. Tidigare skickades inga produktvarningsmeddelanden på grund av ett typmatchningsfel i butiksidentifieraren.
  _AC-5969 - [GitHub-problem](https://github.com/magento/magento2/issues/35602) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/0574ac23)_
* __[Molnet] Funktionen addFilterToMap fungerar inte för vissa kolumner__
Nu kan den anpassade modulen användas i orderstödrastret. Tidigare inträffade fel när en anpassad modul användes.
  _ACP2E-2944 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/3a7c4d17)_
* __[Cloud] Produkter i kategori - Lägg till produkter - Tilldela - Markera alla__
Användare kan nu markera eller avmarkera produkter med hjälp av växlingsknappen.
  _ACP2E-3471_

### Kampanj

* __Kundattributet är inte synligt när du skapar konto från inbjudan__
Kundattribut är tillgängliga när du skapar konto från inbjudan.
  _ACP2E-2602 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/39d54c2d)_
* __Kupongkod med användningskupongsgräns frisläpps inte för betalning. Orderannullering__ misslyckades.
Systemet uppdaterar nu omedelbart kuponganvändning när en order skapas eller annulleras, och lägger till regelanvändning i en kö för att förhindra potentiella lås. Detta garanterar att en kupongkod med en kuponggräns för användning per kupong frisläpps och kan återanvändas om en order annulleras på grund av en misslyckad betalning. Tidigare släppte systemet inte kupongkoden för återanvändning i sådana fall, vilket resulterade i ett felmeddelande om att kupongkoden inte var giltig.
  _ACP2E-2627 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/c971859e)_
* __[Cloud] Omindexering av katalogregelns produktindexerare ger SQLSTATE [HY000]: Allmänt fel: 2006 MySQL-servern har försvunnit.__
Systemet hanterar nu det anpassade värdet &quot;batchCount&quot; i di.xml för &quot;Magento\CatalogRule\Model\Indexer\IndexBuilder&quot; korrekt, vilket förhindrar SQL-fel som &quot;Allmänt fel: 2006 MySQL-servern har försvunnit&quot; under omindexeringen av katalogregelns produktindexerare på grund av den felaktiga gruppstorleken på stora kataloger
  _ACP2E-2811 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/b2286ecf)_
* __[CLOUD]Kundsegmentets kundprisregel för besökare tillämpar inte rabatt på kundvagnen__
Systemet tillämpar nu kundprisreglerna korrekt för besökare, även om regeln inte använder en kupong, vilket säkerställer att rätt rabatter ges i kundvagnen. Tidigare tillämpades inga rabatter på kundvagnen för besökssegment såvida inte kundprisregeln använde en kupong.
  _ACP2E-2926_
* __Attributet &quot;Type&quot; saknas på fliken &quot;Products to Match&quot; i relaterade produktregler__
Attributet&quot;Typ&quot; finns nu som ett filteralternativ på fliken&quot;Produkter att matcha&quot; i modulen&quot;Relaterade produktregler&quot;, vilket ger en mer exakt regeldefinition. Tidigare saknades det här attributet på fliken&quot;Produkter att matcha&quot;, vilket begränsar möjligheten att skapa korrekta matchningsvillkor.
  _ACP2E-3024_
* __Försäljningsregel med attributet Rabattkvantitet steg (Köp X) gör att andra regler inte tillämpas__
Kundprisregeln avbryter inte tidigare tillämpade regler om kvantiteten av produkten i kundvagnen inte räcker för att regeln ska tillämpas.
  _ACP2E-3139 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/d01ee51e)_
* __Prestandaproblem i kundprisregel - modul för avancerad försäljningsregel__
Lagt till saknade DB-index för AdvancedSalesRule-filter
  _ACP2E-3331_
* __Utfärda försäljningsregler med rabatt på fast belopp och &quot;Rabatt på högsta kvantitet används&quot;__
Korrigerat problem med rabatt på kundvagnsregler när rabatt med fast belopp har konfigurerats att tillämpas för en begränsad produktkvantitet är vagnen. Tidigare användes värdet för maximal mängdrabatt till för att beräkna den aktuella artikelns pris i kundvagnen, inte bara för att beräkna regelns rabatt.
  _ACP2E-3332 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/581b7ef1)_
* __[CLOUD] Magento-uppgradering gjorde att kuponger blev skiftlägeskänsliga__
Före korrigeringen var du tvungen att skriva in kupongkoden exakt som den var konfigurerad med hänsyn tagen till versaler eller gemener. Kupongen valideras nu i serverdelen oberoende av koden i versaler eller gemener.
  _ACP2E-3342_
* __Kundregler&quot;Fast beloppsrabatt för hela kundvagnen&quot;  Åtgärden tillämpar rabatter felaktigt__
Kupongkoder valideras korrekt oavsett versaler och gemener när de används för att skapa i administrationsområdet. Före validerades inte kupongkoden om den inte matchade det exakta bokstavsfallet för den konfigurerade kundvagnsregelkoden.
  _ACP2E-3349 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/581b7ef1)_
* __I backend lagras standardvärden för produktattribut (i stället för förväntade administratörsvärden)__
I Backend används nu administratörsvärden i stället för standardvärden för lagring för produktattribut.
  _ACP2E-3374 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/5184c067)_
* __Kassareglerna&quot;Fast beloppsrabatt för hela kundvagnen&quot; ger felaktigt rabatter när paketprodukter läggs till__
Kundvagnsregler med fast belopp tillämpades inte korrekt för paketprodukter. När man beräknar det totala rabattbeloppet beaktas även underordnade paketprodukter, vilket ger en korrekt rabattberäkning.
  _ACP2E-3377 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/1366ae5e)_
* __Rabatt beräknas inte utifrån kundprisregler__
Rabatter med fast belopp beräknas nu korrekt. Före korrigeringen hade rabatterna inte summerats korrekt för paketprodukterna.
  _ACP2E-3403 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/0b488dd1)_
* __Kapslade kategorier i regelvillkor visas inte__
Ett problem har korrigerats när kapslade kategorier under kategori 3 inte visas i marknadsföringsreglerna för kategorivillkor
  _ACP2E-3406 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/88660e79)_
* __usage_limit och uses_per_customer uppdaterar inte i salesrule_coupon-tabellen__
Om du uppdaterar Användare per kupong och Användare per kund i kundvagnsprisregeln kommer det nu att påverka befintliga automatiskt genererade kuponger. Tidigare påverkades endast nya kuponger
  _ACP2E-3432 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/88660e79)_
* __I kundprisregeln tas ingen hänsyn till överordnad kategori när villkoret är lika med eller större än.__
Kundprisregler hanterar nu den överordnade kategorin korrekt när den används i avancerade villkor
  _ACP2E-3456 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/93359343)_
* __Ogiltig rabattberäkning med prioritet__
När det gäller det fasta belopp som tillämpades för hela kassarabattypen beräknades inte beloppet korrekt för varukorgsartiklar som redan hade rabatterats i en tidigare kampanj. Rabatterna summeras.
  _ACP2E-3463 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/078c387e)_
* __[CLOUD] Leveransberäkningen överväger inte kundvagnsregeln__
Före korrigeringen tillämpades ingen vagnsregel med regionsvillkor konsekvent. Efter korrigeringen tillämpas kundvagnsregler med regionvillkor korrekt.
  _ACP2E-3472 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/d4de4726)_
* __Sku-villkoret för kundkontroll av kundvagnsregel misslyckas för faktura.__
Rabatten på programpaketet med dynamiskt pris framgår nu korrekt i fakturan. Tidigare återspeglades inte rabatten på fakturan.
  _ACP2E-3491 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/3f12d152)_
* __Felaktigt rabattvärde när flera kundvagnsprisregler tillämpas samtidigt med rabatterade/specialprisprodukter__
Det fasta beloppet för hela kundvagnsregler tillämpades inte korrekt före korrigeringen om mer än en hade tillämpats. Nu används rabattreglerna för fast belopp korrekt.
  _ACP2E-3498 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/1984c61c)_

### Returnerar

* __[CLOUD] Administratörsanvändare med begränsad behörighet kan se returmenyn och knapparna__
Begränsade administratörsanvändare har nu inte åtkomst till RMA-relaterade kontroller (menyer och knappar).
Administratörsanvändare som tidigare var begränsade kunde se returmenyn och knapparna.
  _ACP2E-3330_
* __Returskärmen är felaktig när skärmen uppdateras__
Användaren kan uppdatera sidan utan att det uppstår någon skärmförvrängning.
  _ACP2E-3443_

### SEO

* __Om du lägger till URL-omskrivningar med en accent läses inläsningen oändlig__
Nu kan systemet skapa och hantera URL-omskrivningar med accenter, vilket förhindrar oändlig inläsning under sparandet. Tidigare orsakade tillägg av en URL-omskrivning med en accent ett oändligt inläsningsproblem.
  _AC-11907 - [GitHub-problem](https://github.com/magento/magento2/issues/38692) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/44cef3a9)_
* __Fel kategori för multibutik - url-rewrite för kategori 3-nivå__
Generera korrekt URL-omskrivning för underordnade med en anpassad URL-nyckel för omfång
  _ACP2E-2641 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/ea79f7dd)_
* __Dubbelbyte-tecken (specialtecken) i fältet Produktnamn blockerar skapande av produkter i serverdelen__
En ny inställning har lagts till som gör att du kan använda transkribering på produkt-URL:en eller inte. Inställningen är tillgänglig här: Lagrar > Konfiguration > Katalog > Katalog > Sökmotoroptimering: &quot;Tillämpa transkribering för produkt-URL&quot;
  _ACP2E-2770 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/b2286ecf)_
* __Felaktiga url_rewrite-poster skapades med flera butiker i en butiksgrupp__
Innan korrigeringen kunde du bara generera URL-omskrivningar på webbplatsnivå när du redigerade en produkt. Med korrigeringen introducerades en ny inställning (Lager > Konfiguration > Katalog > Katalog > Sökmotoroptimering, Återskrivningsomfång för produkt-URL med alternativen Store-vy, Webbplats) som gör att du kan generera URL-omskrivningar på butiksvy- eller webbplatsnivå.
  _ACP2E-3383 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/2d627301)_

### Försäljning

* __Andra kundvagnsprisregeln används inte om Första kundvagnsregeln redan används__
  _AC-13751_

### Sök

* __Hämtar&quot;Ange ett sökord och försök igen.&quot; fel på avancerad söksida i storefront i 2.4.8-beta1__
Sökresultaten visas nu korrekt på sidan Avancerad sökning när ett produktattribut är inställt på Nej. Om du tidigare angav ett produktattribut som &quot;Nej&quot; och gjorde en sökning, skulle ett felmeddelande visas: &quot;Ange ett sökord och försök igen&quot;.
  _AC-13053 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/3ea26621)_
* __magento/module-open-search är beroende av en grenen open search-php som inte finns__
  _AC-13721 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/05dc0bbf)_
* __söktabellen search_query när den är mycket stor har stor inverkan på inläsningstiden frontend__
Förbättrad inläsningstid för söklistsidor. Före korrigeringen försenades söklistsidan på grund av en ooptimerad fråga.
  _ACP2E-3362 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/55615e61)_

### Säkerhet

* __[Problem] Popup-menyn Teckensnitt för CSP-senare__ saknas
Systemet tillåter nu inläsning av teckensnittet https://www.paypalobjects.com/webstatic/mktg/2014design/font/PP-Sans/PayPalSansBig-Medium.woff&#39; utan att bryta mot direktivet Content Security Policy, vilket säkerställer att popup-menyn Paylater visas korrekt. Tidigare nekades teckensnittet att läsas in på grund av en överträdelse av direktivet Content Security Policy, vilket orsakade visningsproblem med popup-menyn Paylater.
  _AC-11855 - [GitHub-problem](https://github.com/magento/magento2/issues/38624) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/37401)_
* __[Utgåva] Uppdatera js.js DOM-text omtolkas som HTML__
Genom att använda innerText undviker man risken för injektion av HTML, eftersom dessa egenskaper automatiskt undgår alla HTML specialtecken i den angivna texten. Med den här korrigeringen kan du förebygga XSS-problem (cross-site scripting) genom att behandla indata som oformaterad text i stället för att tolka HTML.
  _AC-12035 - [GitHub-problem](https://github.com/magento/magento2/issues/38767)_
* __ReCaptcha V2 visas felaktigt vid utcheckning för tyska språk__
Tidigare visades reaptcha från under e-postadress från utcheckning som oformaterad för språk med långa ord, som german. Därefter ser reaptcha ut på samma sätt som alla recaptcha-element från resten av områdena.
  _ACP2E-3273 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/7377de59)_
* __Captcha vid administratörsinloggning kräver inte interaktion för vissa användare__
ReCaptcha för administratörsinloggning valideras som förväntat
  _ACP2E-3300 - [GitHub-kodbidrag](https://github.com/magento/security-package/commit/8f64ab3c)_

### Leverans

* __[Problem] Korrigerat stavfel i tracking.phtml - JS-functions &quot;currier&quot; har bytt namn till &quot;operator&quot;__
Systemet använder nu termen&quot;operator&quot; i stället för den felstavade&quot;currier&quot; i JavaScript-hanterarfunktionerna som används i orderspårningsmallen, vilket säkerställer korrekt funktionsnamn och kodklarhet. Tidigare användes den felstavade termen&quot;currier&quot;, vilket kan leda till förvirring och inkonsekvenser i kodbasen.
  _AC-10757 - [GitHub-problem](https://github.com/magento/magento2/issues/34523) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/33414)_
* __UPS REST &quot;En leverans kan inte ha KGS/IN eller LBS/CM eller OZS/CM som måttenhet&quot;__
Se till att UPS-hastigheterna visas i kassan och i kundvagnen.
  _AC-11938 - [GitHub-problem](https://github.com/magento/magento2/issues/38618) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/493e01f5)_
* __UPS REST-instruktionsuppdateringar för sandlådan och prod i devdoc__
  _AC-12938_
* __[Problem] Korrigera stavning av variabler för kundadressen__
Systemet skannar nu variabler för kundadresser korrekt och ser till att de visas korrekt i kontoområdet på klientsidan. Tidigare kunde felaktig stavning av dessa variabler leda till fel vid lokala kodgranskningar.
  _AC-13172 - [GitHub-problem](https://github.com/magento/magento2/issues/32817) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/32815)_
* __Spårningsfönstret visar fel förväntat leveransdatum__
Visa korrekt leveransdatum för fraktfirma.
  _ACP2E-2738 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/57a32313)_
* __Tabellavgifter visas fortfarande även om kostnadsfri leverans används__
Leveransmetoden för tabellränta visas nu även om kostnadsfri frakt blir tillgänglig efter kuponganvändning
  _ACP2E-2763 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/b2286ecf)_
* __MFTF-test AdminCreatingShippingLabelTest misslyckades på grund av att autentiseringsuppgifter inte har lagts till i Jenkins-miljön__
mftf test fix
  _ACP2E-2765 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/ea79f7dd)_
* __FedEx Track API fungerar inte med REST-autentiseringsuppgifter__
Tidigare krävdes inga ytterligare API-nycklar för API:t för spårning i FedEx-integreringen. Nu har en ny konfiguration lagts till som stöd för API-nycklar för spårning.
  _ACP2E-3340 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/ec7e32a9)_
* __[Cloud] Förhandlingsfrekvenser för FedEx returneras inte för REST__
Före korrigeringen hade FedEx-kontospecifika satser om de inte skickades på svaret, även via FedEx-dokumentation som de skulle ha skickats. Efter korrigeringen skickas de kontospecifika priserna på svaret genom att begäran ändras från vår sida.
  _ACP2E-3354 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/55615e61)_

### Mellanlagring och förhandsvisning

* __Schemalagda uppdateringsinställningar sparades inte om de ursprungligen lades till genom att köra uppdateringen__
Systemet raderar nu produktattributvärden korrekt i efterföljande schemalagda uppdateringar när sådana attribut ändras i den aktuella uppdateringen som körs. Tidigare var det omöjligt att radera sådana attributvärden när ett produktattribut ändrades av en schemalagd uppdatering när en ny schemalagd uppdatering skapades, vilket innebar att användaren måste redigera dem igen när den skapades.
  _ACP2E-2901_
* __Från-datum och till-datum för kundprisregel är inte synkroniserad med mellanlagringsuppdatering__
Datumen sparas enligt uppdateringar för kundprisregelsmellanlagring.
  _ACP2E-2999_
* __JS-fel i mellanlagringsförhandsvisning__
Nu läses filen form-mini-stub.js in utan Js-syntaxfel i utvecklingsverktygen.
  _ACP2E-3104_
* __Det går inte att uppdatera mellanlagrat produktinnehåll till specialpris__
Systemet tillåter nu redigering av slutdatumet för en prisuppdateringskampanj efter att den har startats, vilket säkerställer att användarna kan göra nödvändiga justeringar i sina kampanjer. Tidigare uppstod ett fel när slutdatumet för en aktiv kampanj skulle uppdateras, vilket hindrade användarna från att göra ändringar.
  _ACP2E-3162_
* __Det går inte att uppdatera schemalagd uppdatering när unikt anpassat kategoriattribut används__
Ett problem har korrigerats där en schemalagd uppdatering för en kategori inte var möjlig om kategorin hade ett unikt attribut
  _ACP2E-3453 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/078c387e)_

### Målinriktning

* __[Utgåva] Tillåt användning av CIDR-intervall i tillåtelselista för underhåll__
Systemet har nu stöd för användning av CIDR-intervall i underhållsläget tillåt IP-listor, vilket gör att ett intervall med IP-adresser kan kringgå underhållsläget. Tidigare tillät underhållsläget IP-listan endast tillåtna enskilda IP-adresser att kringgå underhållsläge.
  _AC-9432 - [GitHub-problem](https://github.com/magento/magento2/issues/37943) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/30699)_

### Moms

* __[Utgåva] Funktion/php8.1, egenskapshöjning för konstruktor var diagram ql__
Ersätt alla egenskaper med konstruktoregenskapshöjningen i modulen där graf ql visas:
  _AC-13295 - [GitHub-problem](https://github.com/magento/magento2/issues/39309) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/36975)_
* __FPT (Fixed Product Tax) fungerar inte med konfigurerbara produkter__
FPT för konfigurerbara produktvariationer fungerar korrekt.
  _ACP2E-3193 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/ec7e32a9)_

### Testramverk

* __Integrationstestet misslyckades med testDbSchemaUpToDate på grund av JSON-kolumntypen__
Systemet känner nu igen JSON-kolumntyper korrekt i databasschemat under integreringstester, vilket förhindrar testfel på grund av en felmatchning mellan databasschemat och det deklarativa schemat. Tidigare identifierades JSON-kolumntyper felaktigt som LONGTEXT i MariaDB, vilket medförde att integreringstester misslyckades.
  _AC-11654 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/ef81f5a2)_
* __[Problem] PHPDoc-korrigering av stavning__
Systemet känner nu igen inaktuella metoder i IDE på ett korrekt sätt på grund av en stavningskorrigering i PHPDoc. Tidigare orsakade ett stavfel i PHPDoc att vissa metoder inte kändes igen som inaktuella.
  _AC-13362 - [GitHub-problem](https://github.com/magento/magento2/issues/31399) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/31398)_
* __MAGETWO-95118: Kontrollera beteendet med den beständiga kundvagnen efter att sessionen har upphört__
  _AC-13478 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/7d5e3906)_
* __Integrationstester misslyckades Magento\NegotiableQuote\Controller\Quote\DownloadTest::testCompanyManagerDownloadWithNQSubPermission__
  _AC-13716_
* __[Databasjämförelse] Allvarligt fel om databasen innehåller post om målregel utan villkor__
Tidigare om databasen innehåller poster om målregeln utan något villkor uppstod allvarliga fel, men efter att verktyget för att åtgärda databasjämförelsen har slutförts utan allvarliga fel.
  _AC-13722_
* __Åtgärda statiska tester för att aktivera användning av tillägg från tredje part__
  _AC-13848 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/9e383b4d)_
* __[Internt] Fel vid tillämpning av korrigering visas inte under körning eller i loggar__
&#39;-
  _ACP2E-3334 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/d4de4726)_
* __[MFTF] StorefrontCheckoutProcessForQuoteWithoutNegotiatedPricesTest__
Fasta mftfs
  _ACP2E-3458 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/078c387e)_

### UI Framework

* __Prototype.js, säkerhetslucka som åtgärdar CVE-2020-27511__
Systemet har uppdaterats för att åtgärda säkerhetsluckan CVE-2020-27511 i Prototype.js 1.7.3, vilket förbättrar systemets övergripande säkerhet. Före den här uppdateringen var systemet känsligt för en denial of service-attack (Regular Expression Denial of Service) genom att ta bort skapade HTML-taggar.
  _AC-12128 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/de4dfb8e)_
* __Grunt Mindre använder pub/-prefix för källmappningar__
Systemet genererar nu mindre/css-källmappningar utan /pub-prefixet för sökvägar när de använder grunt, vilket eliminerar behovet av en lösning i webbserverkonfigurationen. Tidigare krävdes en specifik konfiguration på webbservern för att /pub-prefixet i källmappssökvägar skulle fungera korrekt.
  _AC-12189 - [GitHub-problem](https://github.com/magento/magento2/issues/38837) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/38840)_
* __Fält för UI-komponentfil__
Systemet validerar nu filfältet korrekt i ett UI-komponentformulär, så att formuläret kan skickas utan fel när en fil är markerad. Tidigare misslyckades valideringen även om en fil valdes, vilket förhindrar att formuläret skickas.
  _AC-12432 - [GitHub-problem](https://github.com/magento/magento2/issues/38908) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/39004)_
* __[Problem] Förbättrat datumformat i js-konsolen: växla från 12 till 24 timmar..__
Förbättrat datumformat i js-konsolen: byt från 12 till 24 timmar
  _AC-12645 - [GitHub-problem](https://github.com/magento/magento2/issues/38983) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/38972)_
* __[Problem] lägga till sourceMap-generering för färre filer i utvecklarläge__
Systemet genererar nu källmappningar för mindre filer i utvecklarläget, vilket gör det enklare att identifiera källan till ett format. Tidigare var det en utmaning att identifiera källan till en stil när systemet kördes i utvecklarläge med mindre kompilering på serversidan.
  _AC-12650 - [GitHub-problem](https://github.com/magento/magento2/issues/38982) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/38977)_
* __Statiskt innehåll distribueras för inaktiverade moduler__
Nu utesluts CSS som är relaterad till inaktiverade moduler från de slutliga CSS-utdatafilerna, vilket säkerställer att onödiga format inte läses in. Tidigare inkluderades CSS för inaktiverade moduler i de slutliga CSS-utdatafilerna, vilket ledde till inläsning av extra, onödiga format.
  _AC-1306 - [GitHub-problem](https://github.com/magento/magento2/issues/24666) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/32922)_
* __Inkonsekvent beteende vid sortering utanför lagret med lägsta tillåtna lagertröskelvärde__
Systemet sorterar nu produkter i katalogen korrekt baserat på lagernivåer, enligt det fastställda minimitröskelvärdet för lager och flyttar utlagerartiklar till listans nedre del på ett konsekvent sätt. Tidigare var sorteringsfunktionen inkonsekvent, med objekt som inte alltid visas i rätt ordning baserat på deras lagernivåer, och ändringar i sorteringen kan inträffa oförutsägbart efter att kategorihierarkin har sparats, uppdaterats eller ändrats.
  _AC-13459 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/47b448e2)_
* __Förslag om förbättrad felrapportering för problem med att.js läses in__
Den här PR-funktionen förbättrar felmeddelandet när en komponent inte kan läsas in i ett krav.
  _AC-13472 - [GitHub-problem](https://github.com/magento/magento2/issues/36761) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/38971)_
* __PHP 8.4-borttagningsfel som orsakar byggfel i 2.4-develop__
  _AC-14004 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/1da9ba6f)_
* __[Utgåva] Läs inte in kontext för backend-block på frontend__
Systemet ser nu till att serverdelsblockens kontext inte läses in på klientsidan, vilket förhindrar att onödiga serverdelssessioner och eventuella sessionslås skapas. Tidigare lästes serverdelen in felaktigt på klientsidan, vilket ledde till att serverdelssessioner och eventuella sessionslås skapades.
  _AC-9007 - [GitHub-problem](https://github.com/magento/magento2/issues/37617) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/36368)_
* __[Problem] Ta bort översiktssammanfattning för onödiga skript__
Systemet optimerar nu sidinläsningstiden genom att ta bort onödiga JavaScript-skript från klassificeringssektionen, i stället för att använda infogade CSS-format för en mer effektiv och läsbar kod. Tidigare kunde användningen av JavaScript-skript för klassificeringsavsnittet göra sidinläsningen långsammare.
  _AC-9168 - [GitHub-problem](https://github.com/magento/magento2/issues/37776) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/34643)_
* __Undantag vid kontroll av presentkortssaldo när Recaptcha är aktiverat__
Användarna kan hämta presentkortssaldot i vyn och redigera kundvagnen. Tidigare visades inte dessa uppgifter när reCAPTCHA aktiverades.
  _ACP2E-2529 - [GitHub-kodbidrag](https://github.com/magento/magento2-page-builder/commit/4a2795ea)_
* __[CLARIFICATION] ADA-kompatibilitet för funktionsförfrågan__
Systemet garanterar nu ADA-kompatibilitet genom att ta bort CSS-egenskaper som inte stöds och ersätta dem med de som stöds i filen print.css. Tidigare ledde användningen av CSS-egenskaper som inte stöds till problem med webbläsarkompatibiliteten.
  _ACP2E-2729 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/57a32313)_
* __[Cloud] Konfusionsbibliotekskod i effect-drop.js i AC 2.4.4-p8__
Systemet implementerar nu biblioteket effect-drop.js korrekt, vilket säkerställer att jQuery-gränssnittseffekterna fungerar korrekt. Tidigare skrevs biblioteket effect-drop.js av misstag över med biblioteket effect-clip.js, vilket kan orsaka problem med jQuery-gränssnittseffekter.
  _ACP2E-3061 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/35b1b1da)_
* __Platshuvud | Specialtecken som bryter kundens välkomstavsnitt__
Efter korrigeringen visas specialtecken korrekt i välkomstavsnittet för kunder.
  _ACP2E-3367 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/1366ae5e)_
* __Kundsegmentversionen fungerar inte med daterange__
Det går att spara kundsegment med datumintervallvillkor när endast ett av datumen har redigerats.
  _ACP2E-3561 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/a52ff98f)_
