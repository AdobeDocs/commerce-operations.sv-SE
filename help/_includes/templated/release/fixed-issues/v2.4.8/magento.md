---
source-git-commit: 62b6501fc2ba595146bf7f38a7d3352ef02be1a0
workflow-type: tm+mt
source-wordcount: '26051'
ht-degree: 0%

---
# Versionsinformation om Magento Open Source (v2.4.8)

## Högdagrar

Följande 31 markeringar gäller för Magento Open Source 2.4.8.

### Ramverk

* _AC-10721_: Uppgradera league/flysystem Composer-beroenden genom att uppgradera till senaste versionen
   * _Åtgärdat_: Uppgradera 2.x league/flysystem Composer-beroenden till den senaste versionen 3.x
   * _Bidrag till_ GitHub-kod: <https://github.com/magento/magento2/commit/91cb4d46>
* _AC-11673_: Undersök de senaste versionerna av php-amqplib/php-amqplib
   * _Korrigera anteckning_: Uppdaterat den senaste versionen av php-amqplib/php-amqplib :^3.x
   * _Bidrag till_ GitHub-kod: <https://github.com/magento/magento2/commit/de4dfb8e>
* _AC-11911_: css-rensning av jQuery/fileuploader efter migrering till uppy-bibliotek
   * _Fix note_: Tog bort jQuery/fileUploader-biblioteket eftersom det har migrerats till Uppy-biblioteket
   * _Bidrag till_ GitHub-kod: <https://github.com/magento/magento2/commit/7cabfb46>
* _AC-11995_: Lägg till kompatibilitet med MySQL 8.4 LTS för Magento CE
   * _Bidrag till_ GitHub-kod: <https://github.com/magento/magento2/commit/672a2e61>
* _AC-12015_: Rensning av ExtJs-mappar efter migrering till jsTree-bibliotek
   * _Korrigera anteckning_: TextJs-mappen togs bort eftersom de relaterade funktionerna har migrerats till jsTree
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/7cabfb46>
* _AC-12022_: Uppgradera systemberoende för monolog/monolog till den senaste större versionen
   * _Korrigera anteckning_: Systemet har uppdaterats för att använda den senaste större versionen av biblioteket &quot;monolog/monolog:^3.x&quot;, vilket säkerställer kompatibilitet och förbättrade prestanda. Tidigare använde systemet en föråldrad version av &quot;monolog/monolog&quot;-biblioteket som kunde ha orsakat potentiella problem och begränsningar.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/edcd0dcc>
* _AC-12023_: Uppgradera wikimedia/less.php till den senaste större versionen
   * _Korrigera anteckning_: Systemet har uppdaterats för att använda den senaste större versionen, 5.x, av biblioteket wikimedia/less.php, vilket garanterar kompatibilitet och aktuella funktioner. Tidigare använde systemet en inaktuell version av biblioteket som kunde ha orsakat säkerhetsproblem.
   * _Bidrag till_ GitHub-kod: <https://github.com/magento/magento2/commit/edcd0dcc>
* _AC-12024_: Uppgradera jquery/validera biblioteksberoende till den senaste delversionen
   * _Åtgärdsmeddelande_: Uppgradera jquery/validate biblioteksberoendet till den senaste delversionen 1.20.0
   * _Bidrag till_ GitHub-kod: <https://github.com/magento/magento2/commit/de4dfb8e>
* _AC-12025_: Systemberoende för uppgradering av stund.js till den senaste delversionen
   * _Korrigera anteckning_: Systemberoendet för uppgradering stund.js till den senaste mindre versionen, 2.30.1
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/de4dfb8e>
* _AC-12032_: Lägg till kompatibilitet med MySQL 8.4 LTS för EE
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/672a2e61>
* _AC-12034_: Lägg till kompatibilitet med MySQL 8.4 LTS för B2B
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/672a2e61>
* _AC-12074_: Lägg till kompatibilitet med MySQL 8.4 LTS för pakettillägg
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/672a2e61>
* _AC-12085_: Lägg till kompatibilitet med MariaDB 11.4 LTS för CE
   * _Åtgärdsmeddelande_: MariaDB 11.4-stöd har lagts till med Adobe Commerce och tillägg
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/b34c0a75>
* _AC-12165_: Prenumerantoptimering - PhpUnit10
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/90e25b6b>
* _AC-12267_: Stöd för anslutningsförsök för Redis-sessioner och kompatibelt med colinblöenhour/php-redis-session-abstract v2.0.0
   * _Korrigera anteckning_: Uppdaterad version av colinsolenhour/php-redis-session-abstract v2.0.0 kompatibel med Adobe commerce
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/672a2e61>
* _AC-12576_: Undersök misslyckanden med automatiseringstester med MySQL 8.4 LTS
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/672a2e61>
* _AC-12595_: Lägg till kompatibilitet med MariaDB 11.4 LTS för EE
   * _Åtgärdsmeddelande_: MariaDB 11.4-stöd har lagts till med Adobe Commerce och tillägg
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/b34c0a75>
* _AC-12715_: Uppdatera beroenden för laminas-disposition när du uppgraderar till den senaste versionen
   * _Fix note_: Systemet stöder nu de senaste versionerna av laminas composer dependencies:
laminas/laminas-servicemanager
laminas/laminas-server
laminas/laminas-stdlib
laminas/laminas-validator
säkerställa kompatibilitet och uppdaterad funktionalitet. Tidigare kunde uppdatering till de senaste versionerna av dessa beroenden orsaka problem med bakåtkompatibilitet och testfel.
   * _Bidrag till_ GitHub-kod: <https://github.com/magento/magento2/commit/b34c0a75>
* _AC-12823_: Undersök enhetstestfelet på grund av uppdatering av phpunit-patch under komponentuppgradering
   * _Bidrag till_ GitHub-kod: <https://github.com/magento/magento2/commit/b34c0a75>
* _AC-13076_: [Del 1] - Uppdatera alla js-bibliotek och npm-beroenden med den senaste tillgängliga versionen
   * _Korrigera anteckning_: Versionsstöd för dispositionsversion var endast upp till dispositionsversion 2.2.x. Nu har stödet även utökats till version 2.4.x.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/19844aa0>

### Ordning

* _ACP2E-2709_: [Funktionsbegäran] Kunden föreslår att knappen Skicka kommentar på sidan för beställningsinformation är förvirrande och bör ändras till något annat
   * _Fixnotering_: För att minimera förvirringen ändrades etiketten &quot;Skicka kommentar&quot; till &quot;Uppdatera&quot; på orderdetaljsidan.
   * _Bidrag till_ GitHub-kod: <https://github.com/magento/magento2/commit/488c1034>

### Annan

* _AC-11420_: Ställ in indexerare visas som standard med statusen Klar när en ny version av Adobe Commerce installeras
   * _Åtgärdsmeddelande_: Efter installationen Magento måste indexerarens status vara i *Redo-läge* som standard.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/71432aeb>
* _AC-11421_: I en befintlig Magento-installation anger indexeraren som standard i modulen för indexering från tredje part i ett uppdateringsschema.
   * _Korrigera anteckning_: Alla nya indexerare är som standard i läget [Uppdatera enligt schema]. Tidigare var standardläget [Uppdatera vid Spara]. Samma sak med anpassade indexerare.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/71432aeb>
* _AC-12480_: Elasticsearch 7- och 8-alternativen ska finnas med i konfigurationen Borttagen i Admin.
   * _Korrigera anteckning_: Alternativet Elasticsearch 8 i alternativet Admin Config visas med inaktuell text för att informera användare om att Elasticsearch 8 inte längre rekommenderas att använda.
   * _Bidrag till_ GitHub-kod: <https://github.com/magento/magento2/commit/0611e750>
* _AC-12481_: Lägg till textanteckning när alternativet Elasticsearch väljs i Admin-konfigurationen
   * _Korrigera anteckning_: En textanteckning läggs till för att informera Adobe Commerce-administratörsanvändare om att elasticsearch inte längre stöds av Adobe och är föråldrad.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/0611e750>
* _AC-13448_: Leverera prestandaförbättring för nivååtgärder till 2.4.8
   * _Korrigera anteckning_: Systemet tillåter nu mer effektiva bulkuppdateringar av nivåpriser utan att detta orsakar prestandaproblem eller att webbplatsen inte svarar när REST API-slutpunkten /V1/products/tier-prices används. Tidigare kunde en uppdatering av ett stort antal priser med denna slutpunkt leda till prestandaproblem och att webbplatsen inte svarade.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/082d981c>
* _AC-13550_: Ta bort alla sekretessbelagda Adobe-copyrightmeddelanden från Magento Open Source-databaserna
   * _Korrigera anteckning_: Alla sekretessbelagda Adobe-copyrightmeddelanden har tagits bort från databaser med öppen källkod, vilket säkerställer att endast den reducerade formen av Adobe upphovsrätt används. Tidigare innehöll vissa filer i de offentliga databaserna Adobe konfidentiella copyrightmeddelanden, vilket ledde till eskaleringar från communityn.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/39493>
   * _Bidrag till_ GitHub-kod: <https://github.com/magento/magento2/commit/4bca5dfe>

### Ramverk för användargränssnitt

* _AC-12726_: [2.4.8-beta1] TinyMCE 5-migrering till TinyMCE 7
   * _Korrigera anmärkning_: TinyMCE 5 har migrerats till TinyMCE 7.3.0 för att vara en version som stöds för Adobe Commerce. Tidigare användes 5.10.2, som var inaktuellt och rapporterat säkerhetsproblem
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/edcd0dcc>
* _AC-12825_: [ 2.4.8-beta1] TinyMCE 5-migrering till TinyMCE 7 Page Builder
   * _Korrigera anmärkning_: TinyMCE 5 har migrerats till TinyMCE 7.3.0 för att vara en version som stöds för Adobe Commerce. Tidigare användes 5.10.2, som var inaktuellt och rapporterat säkerhetsproblem
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/edcd0dcc>
* _AC-12844_: [ 2.4.8-beta1] Överföring av TinyMCE 5 till TinyMCE 7 - Magento2-infra - förbjudna ord
   * _Fix note_: Migrerade TinyMCE 5 till TinyMCE 7.3.0 för att vara en version som stöds för Adobe Commerce, tidigare använde systemet 5.10.2 som var föråldrad och rapporterade säkerhetsrisk
   * _Bidrag till_ GitHub-kod: <https://github.com/magento/magento2/commit/edcd0dcc>
* _AC-12901_: Require.js uppgradering till den senaste versionen, 2.3.7 (säkerhetslucka, CVE-2024-38999)
   * _Korrigera anteckning_: Uppdaterad require.js till den senaste versionen, 2.3.7. I tidigare version rapporterades säkerhetslucka
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/b34c0a75>

## Åtgärdade problem

Vi har åtgärdat 497 problem i Magento Open Source 2.4.8 Core-koden. En deluppsättning av de åtgärdade problemen som ingår i den här versionen beskrivs nedan.

### API:er

* _AC-10042_: /V1/operations REST API returnerar fel när parent_txn_id = txn_id
   * _Korrigera anteckning_: Systemet hanterar nu transaktioner för det överordnade och underordnade konceptet korrekt där det överordnade transaktions-ID:t är detsamma som transaktions-ID:t, vilket förhindrar en oändlig loop när en fråga ställs till REST API-slutpunkten för /V1/transaktioner. Tidigare skulle detta scenario resultera i ett allvarligt fel på grund av att den maximala körningstiden överskrids.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/1bafc571>
* _AC-11878_: [Graphql] Typproblem i 2.4.7
   * _Korrigera anteckning_: Systemet hanterar nu heltalsvärden korrekt i funktionen GetCustomSelectedOptionAttributes när en GraphQL-fråga körs, vilket förhindrar typrelaterade fel. Tidigare uppstod ett typfel när en GraphQL-fråga som använde GetCustomSelectedOptionAttributes med ett heltalsargument startades.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/38662>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/pull/38663>
* _AC-3223_: Specialtecken i kategori url_key (när de skapas via REST API)
   * _Korrigera anteckning_: I specialtecknet category_url_key finns det inte något specialtecken efter korrigeringen som visar specialtecknet i category_url_key
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/35577>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/c699c206>
* _ACP2E-2755_: Problem med rest api efter aktivering av 2FA Duo
   * _Korrigera anteckning_: 2FA med Duo-säkerhetsalternativ genererar nu korrekt signatur för Rest API
   * _GitHub-kodbidrag_: <https://github.com/magento/security-package/commit/412fa642>
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
* _ACP2E-3236_: Async-åtgärden misslyckas när SKU saknas i nyttolasten
   * _Korrigera anteckning_: Async- och sync-åtgärder misslyckades tidigare på grund av produktsparningsfel om sku saknas i nyttolasten. Efter korrigeringen misslyckas åtgärderna för asynkron och synkroniserad produkt för att spara rest-API med relevant undantagsmeddelande.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/66dea0de>
* _ACP2E-3376_: [CLOUD] Det går inte att uppdatera baspriserna med REST API (värdet för &#39;value_id&#39; i &#39;catalog_product_entity_decimal&#39; ökas inte korrekt.)
   * _Korrigera anteckning_: Tidigare i den här korrigeringen ökade ökningen av kostnadsöknings-ID när rest api /rest/default/V1/products/base-prices anropades felaktigt så att det fanns ett mellanrum mellan värdena. Efter korrigeringen ökas det stegvisa ID:t stegvis. Även value_id fältområde ökades.
   * _Bidrag till_ GitHub-kod: <https://github.com/magento/magento2/commit/d50f6b5d>
* _ACP2E-3460_: Orderartiklar är inte synliga i e-postmeddelanden med kreditnotor för API POST V1/order/:orderId/reserve
   * _Korrigera anteckning_: Tidigare, före den här korrigeringen, fanns det inget rutnät för produktinformation när en kund skapade en kreditnota från en API-begäran som meddelar send_email. När den här korrigeringen har tillämpats skickar kunden en begäran om kreditnota-API och hittar produktartikelinformationen i e-postmeddelandet.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/3f12d152>
* _ACP2E-3486_: Standardvärden är inte inställda för datum- och tidsattribut med produkterna RestAPI
   * _Korrigera anteckning_: Standardvärden ställs nu in korrekt för datum- och datum- och tidsattribut via RestAPI
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/1984c61c>

### API:er, kundvagn och utcheckning

* _ACP2E-3343_: Kritiskt 500-fel: Magento\Framework\Webapi\Exception relaterat till Acceptera HTTP-huvud
   * _Korrigera anteckning_: Efter korrigeringen finns det inget problem med att ange rubriken&quot;Godkänn&quot;.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/1366ae5e>

### Konto

* _AC-10782_: Formulär för kundadress tillåter slumpmässig kod i namnfälten
   * _Fix-anteckning_: Systemet validerar nu inmatningen i fälten Förnamn och Efternamn i kundadressformuläret, vilket förhindrar användning av slumpmässig kod. Tidigare tillät systemet användning av slumpmässig kod i dessa fält utan att utlösa ett fel.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/38331>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/pull/38345>
* _AC-10886_: Uppdatera administratörslösenord.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/38352>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/4bca5dfe>
* _AC-10990_: mitt konto lägger till en adress som kraschar när jag sparar
   * _Korrigera anteckning_: Systemet sparar nu kundadresser korrekt även när regionsfältet inte visas, vilket förhindrar en krasch under sparningsprocessen. Tidigare uppstod ett undantagsfel om du försöker lägga till eller redigera en adress utan ett fält som visas.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/38406>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/pull/38407>
* _AC-11718_: Omdirigeringsslinga när URL har versaler
   * _Korrigera anteckning_: Systemet konverterar nu automatiskt versaler i URL:er till gemener, vilket förhindrar en omdirigeringsslinga vid åtkomst till hemsidan. Tidigare skulle en omdirigeringsslinga uppstå om det fanns versaler i URL:en för den säkra basen när du försökte komma åt hemsidan.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/38538>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/pull/38539>
* _AC-11755_: middlename(s) har inte sparats för gästkonton
   * _Korrigera anteckning_: Systemet sparar nu mellannamnet för gästkonton korrekt under utcheckning, så att det blir tillgängligt i e-postmallen. Tidigare sparades inte mellannamnet i offerttabellen och det gick inte att komma åt det i e-postmallen för gästkonton.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/38593>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/pull/39067>
* _AC-11919_: Admin: Sidåtgärdsknappar flyter åt vänster i stället för åt höger
   * _Korrigera anteckning_: Systemet justerar nu sidåtgärdsknapparna korrekt till höger om det klisterlappande huvudet på adminpanelen, vilket förbättrar det professionella utseendet och känslan. Tidigare var dessa knappar felaktigt flytande till vänster om den klibbiga rubriken.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/38701>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/44cef3a9>
* _AC-11999_: dev:di:infofel i magento 2.4.7
   * _Korrigera anteckning_: Systemet visar nu konstruktorparametrar korrekt när kommandot dev:di:info körs, vilket förhindrar att fel uppstår. Tidigare resulterade körningen av det här kommandot i ett fel på grund av ett typmatchningsfel i argumentet.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/38740>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/0c53bbf7>
* _AC-13000_: Kryssrutan Logga in som kundanmälan kan inte översättas
   * _Korrigera anteckning_: Systemet tillåter nu att kryssrutorna Logga in som kundanmälan och Logga in som kund anges i Store-vyn, vilket möjliggör översättningar för olika butiksvyer. Tidigare hade dessa fält bara angetts i webbplatsomfånget, vilket förhindrar översättningar för enskilda butiksvyer.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/32329>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/pull/32359>
* _AC-6071_: Kunden är inloggad, men 404-fel i frontend visas.
   * _Korrigera anteckning_: Butikskundens kontrollpanel läses nu in som förväntat när en kund loggar in. Tidigare kunde kunderna logga in, men den här sidan visade ett 404-fel. [GitHub-35838](https://github.com/magento/magento2/issues/35838)
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/35838>
   * _Bidrag till_ GitHub-kod: <https://github.com/magento/magento2/pull/36263>
* _ACP2E-2791_: Det går inte att spara information om kundattribut i avsnittet Redigera kund i administratören;
   * _Åtgärdsmeddelande_: Kundens butiks-ID är nu implementerat korrekt enligt webbplatsens omfattning för administratörskundredigeringsformuläret.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/488c1034>
* _ACP2E-3329_: När du har loggat in visas inte produkter som lagts till i jämförelselistan som gästanvändare.
   * _Korrigera anteckning_: Produkter som lades till i produktjämförelselistan före inloggning som kund bevaras nu efter inloggning.
Tidigare var produkterna som lagts till i jämförelselistan som gästanvändare inte synliga efter inloggning.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/078c387e>
* _ACP2E-3433_: Konfiguration av Tillåt länder orsakar problem i kundadresskonfigurationer
   * _Korrigera anteckning_: Om du nu väljer Tillåt länder påverkas inte länder som visas utanför det angivna omfånget. Tillåt tidigare att länder konfigureras som påverkade kundadressattribut utanför angivet omfång
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/078c387e>
* _ACP2E-3501_: VAPT: Affärslogikfel - framtida datum som kundens födelsedatum
   * _Korrigera anteckning_: Kundens födelsedatum kan inte anges senare än idag
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/d4de4726>

### Konto, API:er, GraphQL

* _ACP2E-3246_: Kund-API - Numret för inloggningsfel kan inte återställas till 0 efter lyckad inloggning
   * _Åtgärdsmeddelande_: Nu återställs felnumret till noll i kundenhetstabellen efter att kunden har loggat in via API-slutpunkter.
   * _Bidrag till_ GitHub-kod: <https://github.com/magento/magento2/commit/ec7e32a9>

### Konto, Admin UI, B2B

* _ACP2E-3038_: Begränsade administratörsanvändare kan inte alltid se anpassade delade kataloger
   * _Korrigera anteckning_: Begränsade administratörsanvändare kan nu konsekvent visa och hantera kunder och alla delade kataloger som produkterna är tilldelade till, förutsatt att de har tillgång till den specifika butiken. Tidigare kunde en begränsad administratörsanvändare med åtkomst till en viss butik inte alltid se alla delade kataloger som produkterna var tilldelade till eller kunde se kunder som inte kunde spara, vilket ledde till inkonsekvenser i systemet.
   * _Bidrag till_ GitHub-kod: <https://github.com/magento/magento2/commit/7377de59>

### Konto, kundvagn och kassa

* _AC-2341_: &quot;Välj&quot; anpassat kundadressattribut återges inte för ny kundadress
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/34950>

### Användargränssnitt för administratör

* _AC-10705_: [Problem] med att lägga till behörighetskontroll för knappen &quot;ladda data&quot;
   * _Fixeringsanmärkning_: Systemet inkluderar nu en behörighetskontroll för knappen &quot;Ladda om data&quot;, vilket säkerställer att den endast visas och är tillgänglig för användare med rätt behörighet. Tidigare var knappen &quot;Ladda om data&quot; synlig och klickbar för alla användare, vilket ledde till en &quot;inte tillåten&quot; sida när den klickades av användare utan nödvändiga behörigheter.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/38283>
   * _Bidrag till_ GitHub-kod: <https://github.com/magento/magento2/pull/38279>
* _AC-11427_: [Utfärda] inkonsekventa etiketter för attribut i marknadsföringsregler
   * _Åtgärdat_: Systemet fyller nu korrekt i etiketterna konsekvent för kategori- och attributalternativ i kundvagnsprisregeln
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/31232>
   * _Bidrag till_ GitHub-kod: <https://github.com/magento/magento2/pull/31231>
* _AC-11588_: Datavalidering lyckas och importknappen finns vid import av produkter med ersättningsbeteende
   * _Korrigera anteckning_: Systemet validerar data korrekt och döljer knappen Importera under produktimportprocessen med beteendet Ersätt, vilket förhindrar oavsiktlig ersättning av data. Tidigare validerades data felaktigt och knappen Importera visades, vilket kan leda till inkonsekventa data.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/0574ac23>
* _AC-12167_: [Fel] Magento 2.4.7 tillåter inte produktfoton med filnamnstillägg i versaler.
   * _Korrigera anteckning_: Systemet accepterar nu produktavbildningar med filtillägg i versaler, vilket ger en smidig process för att skapa produkter. Tidigare nekades bildöverföringar med filtillägg i versaler, vilket tvingade användarna att ändra filnamnstillägget till gemener.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/38831>
   * _Bidrag till_ GitHub-kod: <https://github.com/magento/magento2/commit/c8f87c25>
* _AC-12319_: Dold listruta i rutnät med markeringsåtgärd (t.ex. Innehåll > Element > Sidor)
   * _Korrigera anteckning_: Nu har systemet korrigerats för alla liknande listrutor för alla stödraster.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/38891>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/pull/39371>
* _AC-13131:_[ Problemkorrigering] Varning: Odefinierade matrisnyckel &quot;filter&quot;
   * _Korrigera anteckning_: Systemet hanterar nu scenarier där en ny användare ännu inte har interagerat med bokmärken, vilket förhindrar att en odefinierad matrisnyckelvarning (filters) loggas. Tidigare loggades den här varningen när en ny användare inte interagerat med bokmärken.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/39013>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/pull/38996>
* _AC-13529_: CSV-fil för import av produkter med specialtecken misslyckas på grund av kodändringar i filen Validate.php
   * _Fixnotering_: Systemet validerar och importerar nu produkt-CSV-filer som innehåller specialtecken korrekt, vilket möjliggör framgångsrik dataöverföring. Tidigare uppstod ett fel när en CSV-fil med specialtecken skulle importeras.
   * _Bidrag till_ GitHub-kod: <https://github.com/magento/magento2/commit/6cfb9b6b>
* _AC-13850_: Det finns ingen röd asterisk för obligatoriskt telefonnummerfält
   * _Korrigera anteckning_: Tidigare röd asterisk visades inte för telefonnummer, men  telefonnummer var obligatoriskt. Nu är den röda asterisken lagrad och kan ses som ett obligatoriskt fält på telefonnumret.
   * _Bidrag till_ GitHub-kod: <https://github.com/magento/magento2/commit/c699c206>
* _AC-6975_: [Problem] : Ställ in standardindexerarläget på &quot;schema&quot;
   * _Fixnotering_: Alla nya indexerare är som standard i **[!UICONTROL Update by Schedule]** läge.  Tidigare var standardläget **[!UICONTROL Update on Save]**. Befintliga indexerare påverkas inte. [GitHub-36419](https://github.com/magento/magento2/issues/36419)
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/36419>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/0b410856>
* _AC-7700_: [Utgåva] Ta bort indexerarändringstabeller när mview-prenumerationen avbryts
   * _Korrigera anteckning_: Systemet tar nu automatiskt bort oanvända ändringstabeller när ett index ändras från &quot;uppdatera enligt schema&quot; till &quot;uppdatera vid spara&quot;, vilket markerar indexet som ogiltigt för att säkerställa att inga poster missas. Om du tidigare växlade ett index till&quot;update on save&quot; skulle oanvända ändringsloggtabeller i systemet utelämnas och alla ändrade index markeras som&quot;valid&quot;.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/29789>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/pull/25859>
* _AC-7962_: Ingen länk till leverans vid betalning i kassan i mobiltelefonvyn
   * _Korrigera anteckning_: Systemet ser nu till att utcheckningsrubrikerna/länkarna &quot;Leverans&quot; och &quot;Granska och betalningar&quot; alltid visas ovanpå sidan i mobilvyn, så att användarna enkelt kan navigera mellan stegen och göra nödvändiga korrigeringar. Tidigare var dessa titlar/länkar dolda i mobilvyn, vilket gjorde det svårt för användarna att ta reda på det aktuella steget eller gå tillbaka till tidigare steg.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/36856>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/pull/36982>
* _AC-8109_: Leveranskommentarer för kundbeställningar som skapas_at returneras i +0-tidszon som inte finns i den butikskonfigurerade tidszonen
   * _Korrigera anteckning_: Systemet visar nu korrekt fältet &#39;created_at&#39; från leveranskommentarer i kundens konfigurerade tidszon när kundorderfrågan används. Tidigare visades fältet&quot;created_at&quot; i tidszonen +0, oavsett kundens konfigurerade tidszon.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/36947>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/pull/37642>
* _AC-9843_: i18n:collect-frases break the translations integrity
   * _Fix note_: Kommandot `bin/magento i18n:collect-phrases -o` samlar nu in och lägger till nya fraser från JavaScript- och .phtml-filer, vilket säkerställer att översättningar återspeglas korrekt i översättningsfilen. Tidigare misslyckades systemet med att inkludera flerradiga översättningsfraser från JavaScript-filer och fraser från .phtml-filer i översättningsfilen, vilket ledde till ofullständiga eller felaktiga översättningar.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/0c53bbf7>
* _ACP2E-2787_: Apostrofen i butiksvyns namn ersätts av &#39;
   * _Korrigera anteckning_: Stödrastrets visningsfilter visar nu apostrofer korrekt
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/38395>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/39d54c2d>
* _ACP2E-2847_: Favicon-överföringen kan inte validera ICO-filer
   * _Fixnotering_: Filvalideringsfelet har uppdaterats till &quot;Filvalidering misslyckades. Kontrollera inställningarna för bildbehandling i Store-konfigurationen.&quot; Tidigare var det helt enkelt &quot;Filvalidering misslyckades.&quot;
   * _Bidrag till_ GitHub-kod: <https://github.com/magento/magento2/commit/39d54c2d>
* _ACP2E-2957_: Galleriet i PageBuilder visar en gammal miniatyrbild istället för en nyligen uppladdad bild
   * _Åtgärdsmeddelande_: Återskapa förhandsgranskningar av bilder som raderats och laddats upp på nytt med samma namn via mediegalleriet i sidbyggarens innehåll.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2-page-builder/commit/60140cd2>, <https://github.com/magento/magento2/commit/001e5188>
* _ACP2E-2978_: Om du sparar produkten av en admin-användare med ett annat rollomfång skrivs befintlig relaterad produktinformation över/tas bort i produkten
   * _Korrigera anteckning_: Tidigare, före korrigeringen, återställdes de relaterade produkterna och blev tomma när den sekundära administratören klickade på knappen Spara utan att ändra i den relaterade produkten. Efter den här korrigeringen klickar den sekundära administratören på knappen Spara och produkten återställs inte och sparas utan fel.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/3056e9cb>
* _ACP2E-3033_: Det går inte att exportera fler än 200 ordrar
   * _Korrigera anteckning_: Servergränsen för begärandorleken för tidigare skickade valda ID:n har ignorerats genom att HTTP-begäran från GET till POST ändrades för att åtgärda problemet. På grund av serverbegränsningarna för GET-begäran har ett problem påträffats.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/93d50f8d>
* _ACP2E-3037_: Utcheckningssidans valideringsmeddelande är felaktigt.
   * _Korrigera anteckning_: Om ett obligatoriskt fält lämnas tomt, till exempel &quot;adress&quot;, visas inte meddelandet vid validering på serversidan. Valideringen på klientsidan säkerställer att det obligatoriska fältfelmeddelandet visas med meddelandet&quot;This is a required field&quot;. Tidigare visades meddelandet&quot;address is required&quot; om något obligatoriskt fält lämnades tomt, förutom valideringsmeddelandet på klientsidan.
   * _Bidrag till_ GitHub-kod: <https://github.com/magento/magento2/commit/9af794a4>
* _ACP2E-3125_: Problem med mall för lösenordsåterställning med administratörsanvändare
   * _Åtgärdsmeddelande_: Problemet har lösts genom att använda rätt nyckel, som nu inkluderar administratörens användarnamn i e-postmallen och fyller i ämnet på rätt sätt. Tidigare berodde problemet på en föråldrad nyckel som användes.
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
   * _Bidrag till_ GitHub-kod: <https://github.com/magento/magento2/commit/8459b17d>
* _ACP2E-3294_: Leveransadressens status uppdateras inte automatiskt
   * _Åtgärdsmeddelande_: Före korrigeringen var leveransadressregionen (eller region-id:t) inte synkroniserad med faktureringsinformationen för adressen. Nu uppdateras både leveransadressregion och region-ID korrekt när faktureringsadressinformationen ändras.
   * _Bidrag till_ GitHub-kod: <https://github.com/magento/magento2/commit/581b7ef1>
* _ACP2E-3364_: Knappen Återställ fungerar inte för Admin-användare för Lägg till/redigera
   * _Korrigera anteckning_: Tidigare fungerade inte knappen Återställ på sidan Lägg till/redigera admin-användare. Nu, i Admin-panelen under System -> Behörigheter -> Alla användare, kommer återställningsknappen att fungera korrekt på sidan Lägg till/redigera administratörsanvändare.
   * _Bidrag till_ GitHub-kod: <https://github.com/magento/magento2/commit/5184c067>
* _ACP2E-3373_: Magento admin URL-dirigering felaktig detektering och CORS-fel
   * _Fix note_: Efter korrigeringen, om den anpassade administratörsdomänen är en underdomän till huvuddomänen, är administratören endast tillgänglig från den konfigurerade underdomänen.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/37663>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/3f12d152>
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
   * _Korrigera anteckning_: Tidigare visades JavaScript-fel relaterade till TinyMCE 6 i webbläsarkonsolen när JavaScript-miniatyrbilder aktiverades i produktionsläge på administratörspanelen, vilket påverkade funktionaliteten och användarupplevelsen. Nu har problemet lösts och säkerställer att TinyMCE 6 fungerar smidigt utan att några fel genereras, även när JS-minification är aktiverat.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/56463d5e>
* _ACP2E-3459_: Begär ytterligare ändringar för att slutföra korrigeringen för AVS2E-3375 fullständigt
   * _Korrigera anteckning_: -
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/d50f6b5d>
* _ACP2E-3503_: Automatisk aktivering av nya ACL-behörigheter
   * _Korrigera anteckning_: Nya behörigheter som lagts till i anpassade moduler ger inte längre automatiskt åtkomst till alla befintliga användarroller om de inte uttryckligen har konfigurerats.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/3f12d152>
* _ACP2E-3509_: Användarrapporten för administratörsåtgärdsloggen visar inte information för adminhtml_user_delete
   * _Korrigera anteckning_: Viktig information loggas nu korrekt i adminhtml_user_delete. Tidigare genererades inga loggar för borttagning av användare.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/4de008a9>
* _ACP2E-3536_: Vagnregel med leveransvillkor gäller inte vid beställning från administratör
   * _Korrigera anteckning_: Om kundvagnsprisregeln har en rabattmetod med kupongen kan den inte tillämpas via administratörsgränssnittet. När den här korrigeringen har tillämpats tillämpas rabatten på kundprisregeln med en kupong för en viss leveransmetod från administratörsgränssnittet.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/a52ff98f>, <https://github.com/magento/inventory/commit/11ce816b>
* _ACP2E-3559_: [FRESH] HEX-kod uppdateras inte korrekt i SWATCH
   * _Korrigera anteckning_: HEX-kod som anges manuellt av användaren i färgväljaren för visuell färgruta ändras inte längre av systemet. Tidigare hade vissa HEX-koder haft mindre justeringar på grund av konverteringsfel mellan färgmodeller.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/344fce23>, <https://github.com/magento/inventory/commit/1ef984c0>

### Administratörsgränssnitt, B2B

* _AC-13628_: B2B-inloggning som kundhuvud har fortfarande Magento-märkning
   * _Fix note_: Tidigare visade skyltfönstrets rubrik &quot;Du är nu ansluten som &lt;customer name=&quot;&quot;> på &lt;store name=&quot;&quot;>&quot; med Magento-varumärke. &lt;/store>&lt;/customer> Vilket nu är åtgärdat och rubriken visas med ADOBE-varumärke.
   * _Bidrag till_ GitHub-kod: <https://github.com/magento/magento2/commit/96dec499>

### Administratörsgränssnitt, betalningssätt, beställning

* _AC-13520_: Transaktionsauktorisering visas inte på fliken Transaktion efter ordningen för smarta knappar i PayPal
   * _Korrigera anteckning_: Systemet visar nu transaktionsauktoriseringen korrekt på fliken Transaktion när en order har placerats med den smarta knappen PayPal. Auktoriseringstransaktionen visades inte på fliken Transaktion när du klickade på Auktorisera och ingen ny transaktion av typen Authorization skapades.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/6cfb9b6b>

### Administratörsgränssnitt, prestanda

* _ACP2E-3169_: Efter uppdatering till 2.4.5-p8 uppstår 500 fel när order skapas från administratör
   * _Korrigera anteckning_: Tidigare gick det inte att göra en beställning från administratören när HTML-minifiering aktiverades. Nu när HTML minification är aktiverat kan du beställa från administratören.
   * _Bidrag till_ GitHub-kod: <https://github.com/magento/magento2/commit/b21e5d91>

### Admin UI, frakt

* _ACP2E-2519_: Antalet kupongkoder uppdateras inte i kolumnen &quot;Använd tid&quot; på fliken Hantera kupongkoder om en beställning görs med flera leveranser.
   * _Åtgärdsmeddelande_: Tidigare, när en beställning gjordes med multifrakt, uppdaterades inte antalet kupongkoder i kolumnen &quot;Tidsanvändning&quot; på fliken Hantera kupongkoder. Nu visas det korrekta antalet i både &quot;Tidsanvändning&quot; som återspeglar de önskade värdena med multifrakt.
   * _Bidrag till_ GitHub-kod: <https://github.com/magento/magento2/commit/4745100c>

### Admin UI, Staging och Preview

* _ACP2E-3424_: [Molnborttagning] av mall med saknade bilder gör att pub/media tas bort
   * _Fix note_: Före den här korrigeringen, om namnet på förhandsgranskningsbilden saknades för en pagebuilder-mall, togs pub/media-mappen bort. Efter korrigeringen kommer endast mallen att tas bort och förhandsgranskningsbilden om den hittas.
   * _Bidrag till_ GitHub-kod: <https://github.com/magento/magento2-page-builder/commit/0986853b>

### Analyser/rapporter

* _AC-9922_: Google Analytics CSP-fel https://region1.analytics.google.com
   * _Korrigera anteckning_: Systemet tillåter nu anslutningar till https://region1.analytics.google.com&#39; när Google Analytics är aktiverat och förhindrar CSP-fel (Content Security Policy). Tidigare skulle det resultera i fel i CSP-konsolen om Google Analytics kunde aktiveras och webbplatsen från EU på grund av en vägran att ansluta till https://region1.analytics.google.com&#39;.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/37750>
   * _Bidrag till_ GitHub-kod: <https://github.com/magento/magento2/pull/38991>
* _ACP2E-2570_: Förhandsrapporten fungerar inte
   * _Fix-anteckning_: Systemet stöder nu generering av datafiler för förhandsrapportering för extra stora datamängder genom att ladda och skriva rapporter i batchar om 10 000. Tidigare kunde Advance Reporting-modulen inte generera datafiler för extra stora datamängder, vilket orsakade &quot;MySQL-servern har försvunnit&quot;-fel under körningen av det analytics_collect_data cron-jobbet.
   * _Bidrag till_ GitHub-kod: <https://github.com/magento/magento2/commit/a12063bd>
* _ACP2E-3080_: Problem med synlighet för datumintervall för administratörsbeställda produkter.
   * _Korrigera anteckning_: Användaren kan välja valfritt datum från rapporten för beställda produkter. När en tabell har uppdaterats återställs TO-datumet när du väljer FROM-datumet.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/6f4805f8>
* _ACP2E-3096_: Felaktiga rullhuvuden som gör att newrelic:create:deploy-marker fungerar inte
   * _Korrigera anteckning_: Systemet formaterar nu krullningshuvuden korrekt, så att kommandot newrelic:create:deploy-marker kan skapa en distributionsmarkör i New Relic. Tidigare kunde felaktiga rullrubriker inte skapa en distributionsmarkör i New Relic.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/37641>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/6a185204>
* _ACP2E-3183_: NewRelic-webbläsarövervakning av inlineJS-skript orsakar CSP-fel
   * _Korrigera anteckning_: Skript för övervakning av nya webbläsare har nu injicerats av programmet i stället för APM-agenten för kompatibilitet med CSP (Content Security Policy). Tidigare var de NewRelic Browser Monitoring-skript som injicerades av APM-agenten inte kompatibla med CSP och orsakade att skripten inte kördes.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/66dea0de>
* _ACP2E-3189_: INSERT-frågor till sales_bestsellers_aggregated_daily-tabellen blir långsamma i projekt med stor försäljningsordervolym
   * _Fix note_: Tidigare skulle bästsäljarnas aggregerade dagliga rapport ta mycket tid att generera för stora volymer av lagda beställningar. Nu genereras rapporten i tid.
   * _Bidrag till_ GitHub-kod: <https://github.com/magento/magento2/commit/7377de59>
* _ACP2E-3276_: Orderrapporter som visar fel valutasymbol
   * _Åtgärdat_: Valutasymbolen för orderbelopp i orderrapporten togs felaktigt från valuta/optioner/bas. Den har nu korrigerats för att använda valuta/optioner/standard för korrekt rapportering.
   * _Bidrag till_ GitHub-kod: <https://github.com/magento/magento2/commit/fd5cf3af>
* _ACP2E-3302_: [Felaktiga beräkningar av molnet] i kuponganvändningsrapporten
   * _Fix:_ Försäljningssumman i kupongrapportrutnätet beräknas nu korrekt genom att inkludera både &quot;Rabattskattekompensationsbelopp&quot; och &quot;Belopp för fraktrabattskattekompensation&quot;. Tidigare saknades dessa belopp i beräkningen, vilket ledde till skillnader mellan den totala försäljningen och försäljningsorderdata.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/d75cff27>
* _ACP2E-3339_: Problem med delade &quot;&lt;project_id>/var/tmp&quot;
   * _Fix:_ Temporära filer för Analytics DataExport kommer att använda sys-tmp-katalogen, som är mer lämplig för frekvent åtkomst och ändringar. För att undvika kollisioner om flera instanser körs på samma server uppdaterades tmp-sökvägen till att använda en instanss unika ID
   * _Bidrag till_ GitHub-kod: <https://github.com/magento/magento2/commit/a4cf5e62>

### Analys / Rapportering, B2B

* _ACP2E-2300_: B2B - sitemap inkluderar produkter/kategorier som inte tilldelats delad katalog
   * _Åtgärdsmeddelande_: Begränsa de kategorier och produkter som genereras av webbplatskartan till de kategorier och produkter som endast tilldelats den offentliga delade katalogen och/eller behörighetsinställningen för katalogkategori.
   * _Bidrag till_ GitHub-kod: <https://github.com/magento/magento2/commit/ea79f7dd>

### Analys / Rapportering, Moln

* _ACP2E-3067_: Magento kasserar de flesta New Relic cron-transaktioner #34108
   * _Fix note_: AC rapporterar cron-jobbrelaterade transaktioner korrekt till NewRelic. Tidigare visades vissa cron-jobbrelaterade transaktioner som &quot;OtherTransaction/Action/unknown&quot; i NR
   * _Bidrag till_ GitHub-kod: <https://github.com/magento/magento2/commit/35b1b1da>
* _ACP2E-3187_: Metrik i NR kan vara missvisande för bakgrundstransaktioner - Uppföljning av ACP2E-3067
   * _Fixnotering_: Bakgrundstransaktioner (cron) kommer att använda New Relic-appens namn som definierats i konfigurationsinställningarna
   * _Bidrag till_ GitHub-kod: <https://github.com/magento/magento2/commit/ec7e32a9>

### B2B (B2B)

* _ACP2E-2139_: Produkter som tilldelats delad katalog återspeglas inte i frontend när partiellt index körs
   * _Fix note_: Produkter som tilldelats delad katalog via REST API är nu omedelbart synliga i skyltfönstret efter att partiell indexering är klar. Tidigare var produkterna bara synliga efter en fullständig omindexering.
   * _Bidrag till_ GitHub-kod: <https://github.com/magento/magento2/commit/7377de59>
* _ACP2E-3044_: Onödiga gränser i avsnittet Mina beställningar
   * _Fixnotering_: Tidigare skapades en extra behållare (orderreferenser) som tillämpade ytterligare CSS-klasser, vilket orsakade att onödiga kantlinjer visades under ordernumret i avsnittet Mina beställningar, som inte är synligt nu.
   * _Bidrag till_ GitHub-kod: <https://github.com/magento/magento2/commit/9af794a4>
* _ACP2E-3247_: sales_clean_quotes cron tar bort offerter från till ännu godkända inköpsorder
   * _Korrigera anteckning_: Offerter som används i inköpsorder tas nu inte bort av cron-jobbet sales_clean_quotes
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/581b7ef1>

### B2B, ramverk

* _AC-9607_: Det går inte att filtrera företagsstödrastret och sedan försöka exportera stödraster-CSV:n. Undantag genereras
   * _Korrigera anteckning_: Systemet tillåter nu lyckad CSV-export av företagsrutnätsdata på adminpanelen, även när filter som Utgående balans och Företagstyp tillämpas. Om du tidigare tillämpade vissa filter och försökte exportera stödrasterdata skulle det resultera i ett fel och ett undantag genereras.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/44cef3a9>

### Paket

* _AC-10826_: Antal meddelanden om bekräftelsefel i Checkbox-kryssrutan i Store mer än 1
   * _Korrigera anteckning_: Systemet visar nu endast ett valideringsfelmeddelande när användaren klickar på knappen Lägg till i kundvagnen utan att markera några kryssrutealternativ för en paketerad produkt. Tidigare visades flera valideringsfelmeddelanden för varje omarkerad kryssruta.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/3ea26621>

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
* _AC-11717_: Magento 2-inloggning i kassan med befintlig kund ger konsolfel i Firefox-webbläsaren
   * _Korrigera anteckning_: Nu kan användare logga in under utcheckningsprocessen utan att stöta på konsolfel i Firefox-webbläsaren. Tidigare uppstod ett konsolfel i Firefox om du försökte logga in som en befintlig kund under utcheckningen.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/38557>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/pull/39509>
* _AC-11876_: [Utfärda] regression för försäljningsregler i 2.4.7
   * _Fix note_: Systemet validerar nu försäljningsregler korrekt, vilket förhindrar att en kupongkod tillämpas på en varukorg när produktens skick inte matchar något produktnamn. Tidigare kunde en försäljningsregel tillämpas och en rabatt ges på fraktbeloppet även när produktvillkoret inte stämde överens med något produktnamn.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/38671>
   * _Bidrag till_ GitHub-kod: <https://github.com/magento/magento2/commit/0574ac23>
* _AC-11914_: [Utfärda] försäljningsregel CartFixad beräkning: felaktigt rabattbelopp
   * _Åtgärdsmeddelande_: Systemet beräknar nu rabattbeloppet korrekt för försäljningsregler med fasta belopp i kundvagnen, vilket säkerställer att korrekta rabatter tillämpas oavsett ändringar i varukorgsartiklar. Tidigare kunde rabattbeloppet variera felaktigt när varukorgsvaror ändrades, vilket ibland resulterade i betydligt större rabatter än förväntat.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/38694>
   * _Bidrag till_ GitHub-kod: <https://github.com/magento/magento2/commit/581b7ef1>
* _AC-11993_: [Problem] Lastaren blockerar leveransmetoderna efter att postnumret har ändrats, valideringsregler för fraktkostnader
   * _Korrigera anteckning_: Systemet hanterar nu anpassade leveransmetoder korrekt utan valideringsregler för fraktsatser, vilket säkerställer att inläsaren inte blockerar leveransmetoderna efter att postkoden har ändrats i leveransadressen under utcheckningen. Om du ändrar postnumret i leveransadressen under utcheckningen skulle det medföra att inläsaren blockerar leveransmetoderna och inte försvinner när anpassade leveransmetoder utan regler för utcheckning av fraktsatser används.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/38742>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/1bafc571>
* _AC-12170_: Funktionen för kupongkod fungerar inte som den ska på utcheckningssidan för Magento 2.4.7
   * _Korrigera anteckning_: Systemet aktiverar nu inmatningsfältet för rabattkod/kupong på utcheckningssidan för virtuella och nedladdningsbara produkter, så att användare kan tillämpa rabattkoder som förväntat. Tidigare var inmatningen av rabattkod/kupong inaktiverad och knappens titeltext visades som &quot;Avbryt kupong&quot;, vilket hindrade användare från att använda rabattkoder.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/38826>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/1bafc571>
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
* _ACP2E-2518_: Ombeställning lägger till icke-tilldelad produkt i varukorgen
   * _Fix note_: Tidigare, för de olika butikerna, kunde produkter beställas om från den andra butiken. När korrigeringen har tillämpats på samma butik kan samma omfattningsprodukt omordnas när kundkontoresursen är aktiverad
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/f89a447e>
* _ACP2E-2620_: I admin uppdateras inte kundvagnen till vänster när du väljer artiklar och &quot;Flytta till kundvagn&quot; till höger
   * _Korrigera anteckning_: Kundvagnen till vänster uppdateras när du väljer artiklarna och Flytta till kundvagn till höger i administratörssidan. Tidigare fungerade inte den här funktionen eftersom de omformade varukorgsobjekten inte blev tomma från sessionen.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/39d54c2d>
* _AVS2E-2646_: [Förs.regel för molnet] tillämpas inte på den första ordern för flerleverans
   * _Korrigera anteckning_: Efter korrigeringen visas rabatten korrekt för varje order av samma flerleveransoffert.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/f89a447e>
* _ACP2E-2664_: [Cloud] Production Parallel-begäranden om att lägga till samma produkt i kundvagnen resulterar i två separata objekt i Cart rest API
   * _Fix note_: Systemet behandlar nu korrekt flera parallella förfrågningar om att lägga till samma produkt i kundvagnen i en enda radartikel, vilket förhindrar att separata radartiklar skapas för samma SKU. Tidigare skulle parallella begäranden om att lägga till samma produkt i kundvagnen via REST API resultera i flera radartiklar för samma SKU.
   * _Bidrag till_ GitHub-kod: <https://github.com/magento/magento2/commit/f89a447e>
* _ACP2E-2704_: Det går inte att skicka cookien. Storlek på&quot;bildmeddelanden&quot; vid försök att ändra ordning
   * _Korrigera anteckning_: Omsorteringsprocessen genererar inga egna fel nu. Den förlitar sig på varukorg som listar inbyggda artikelkontroller.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/ba25af8a>
* _ACP2E-2798_: Standardleveransadress har inte valts vid utcheckning
   * _Korrigera anteckning_: Standardleveransadress väljs nu för händelse i samband med aktiverad adresssökning.
   * _Bidrag till_ GitHub-kod: <https://github.com/magento/magento2/commit/7e0e5582>
* _ACP2E-2897_: [CLOUD] graphql addProductsToCart api-problem med anpassat alternativ
   * _Korrigera anteckning_: GraphQL lägger korrekt till samma produkt i varukorgen med olika anpassade alternativ
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/c971859e>
* _ACP2E-2923_: Flera adresser har lagts till i kontot vid utcheckning som ny kund
   * _Korrigera anteckning_: Systemet sparar nu en ny kundadress endast en gång om beställningen inte kunde skapas, vilket förhindrar att flera identiska adresser skapas i händelse av orderplaceringsfel. Tidigare sparade systemet en ny adress varje gång ett orderplaceringsförsök gjordes, oavsett om ordern skapades eller inte.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/001e5188>, <https://github.com/magento/inventory/commit/2ebcef39>
* _ACP2E-3004_: Om du ändrar ordningen på kundorder via gästbeställningsformulär blir kundvagnen tom
   * _Korrigera anteckning_: Tidigare omdirigerades kunden till inloggningssidan när en ombeställning placerades via sidan Beställningar och returnering. När den här korrigeringen har tillämpats omdirigeras den registrerade kunden korrekt till sidan Visa kundvagn när en ombeställning görs. Flödet fungerar på samma sätt som gästkunder.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/6a185204>
* _ACP2E-3025_: Administratörsanvändare med begränsade rollresurser kan inte visa varukorgar
   * _Korrigera anteckning_: Tidigare kunde den begränsade administratören inte se den övergivna kundvagnen från adminpanelen för en associerad webbplats. När den här korrigeringen har tillämpats kan administratören se den övergivna kundvagnen på adminpanelen.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/d1f7dc95>
* _ACP2E-3176_: [Cloud] snabbeställa stora mängder SKU-prestanda
   * _Korrigera anteckning_: Utcheckningsprestanda har förbättrats när attribut som används i kundprisregler inte finns för alla produkter och när funktionen för att ange lägsta annonspris är aktiverad.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/66dea0de>
* _ACP2E-3211_: Dubblerade objekt i kundvagnen
   * _Fix note_: Systemet behandlar nu korrekt flera parallella förfrågningar om att lägga till samma produkt i kundvagnen i en enda radartikel, vilket förhindrar att separata radartiklar skapas för samma SKU. Tidigare skulle parallella förfrågningar om att lägga till samma produkt i kundvagnen i Storefront resultera i flera radartiklar för samma SKU.
   * _Bidrag till_ GitHub-kod: <https://github.com/magento/magento2/commit/66dea0de>
* _ACP2E-3296_: E-postbekräftelse för utcheckningsorder skickas till e-postmeddelanden som anges i för-/efternamn
   * _Åtgärdsmeddelande_: E-postbekräftelsen för kassaordern, som tidigare skickades när ett e-postliknande mönster angavs i fälten för för- och efternamn, skickas inte längre.
   * _Bidrag till_ GitHub-kod: <https://github.com/magento/magento2/commit/5184c067>
* _ACP2E-3402_: Checkout shipping address form get update with errors address
   * _Korrigera anteckning_: shippingAddressFromData sparas nu i den lokala lagringen per webbplats. Tidigare kunde en adress från fel webbplats fyllas i automatiskt i leveransadressformuläret vid utcheckning om en butikskod användes i URL:en och utcheckningen initierades från flera webbplatser under samma gästsession.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/078c387e>
* _ACP2E-3407_: Presentkortsprodukt | Koppla kort sammanfogar presentkort
   * _Korrigera anteckning_: Presentkortsprodukter har nu sammanfogats korrekt i vagnen
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/88660e79>
* _ACP2E-3415_: Cart persistence respekteras inte vid utloggning
   * _Korrigera anteckning_: Funktionen som saknas har lagts till Kom ihåg mig från kundinloggning till autentiserings-popup och utcheckning av inloggningar.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/344fce23>
* _ACP2E-3488_: Befintliga offertdata uppdateras inte/visas inte, utan skapar i stället en ny offertpost när trigger_recllect = 1
   * _Korrigera anteckning_: Kundens kundvagnsartiklar försvinner inte längre om en produkt tas bort efter att den har lagts till i kundvagnen.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/1984c61c>
* _ACP2E-3618_: [CLOUD] Ordna om knappfunktioner
   * _Korrigera anteckning_: Om du ändrar ordning på en order från administratörsområdet läggs nu produkter med lager till i offerten, även om det finns produkter i den ursprungliga ordern som inte har något lager längre. Före korrigeringen lades inga produkter till i den nya offerten om produkten utan lager fanns i den ursprungliga ordern.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/a52ff98f>
* _ACP2E-3622_: Sökarkiv fungerar inte med postnummer
   * _Korrigera anteckning_: Sökningar efter hämtningsplatser efter postnummer fungerade inte korrekt för nederländska lokaliseringar. Efter korrigeringen kommer sökningen efter hämtningsplatsen att ge resultat baserat på postnummer.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/344fce23>

### Kort och utcheckning, utcheckning/utcheckning av en sida

* _AC-9386_: [Slumpmässigt fel] E-postfältet renderas inte eller det tar lång tid att visa det på utchecknings- eller betalningssidan
   * _Åtgärd_: **[!UICONTROL Email]** Commerce återger nu fältet på frakt- och betalningssidorna i kassan som förväntat. Tidigare var det här fältet antingen frånvarande eller renderades långsamt.
   * _Bidrag till_ GitHub-kod: <https://github.com/magento/magento2/commit/e1babcfd>

### Varukorg &amp; Kassa, Beställ

* _ACP2E-3097_: Datumväljaren för produkt med flera anpassningsbara alternativ med datumfält som inte fungerar när en beställning från en administratör placeras
   * _Korrigera anteckning_: Datumväljaren visas nu korrekt för alla datumfält när en produkt konfigureras med flera anpassningsbara datumalternativ i processen för att skapa administratörsorder. Tidigare visades datumväljaren bara för det första datumfältet, och återstående fält lämnades utan datumväljare.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/b21e5d91>

### Kundvagn och utcheckning, leverans

* _AC-12119_: Direktköp -&quot;billigaste leveransen&quot; brutet för konfigurerbara produkter
   * _Åtgärdsmeddelande_: Funktionen för direktköp valde felaktigt det dyrare alternativet för leverans i butik för konfigurerbara produkter i stället för den billigaste schablonmetoden. Denna korrigering säkerställer att rätt fraktmetod väljs baserat på det faktiska priset.&quot;
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
* _AC-11970_: Det går inte att ordna om konfigurerbara produkter med en kryssruta markerad som anpassat alternativ
   * _Korrigera anteckning_: Systemet bearbetar nu korrekt omsorteringen av konfigurerbara produkter med ett enda anpassat kryssrutealternativ, vilket gör att korgen kan skapas. Tidigare uppstod ett fel när sådana produkter skulle sorteras om och artiklarna kunde inte läggas till i kundvagnen.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/38736>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/1d144bce>
* _AC-12076_: [Problem] Åtgärda formuleringen för filterobjektet vid navigering i lager
   * _Korrigera anteckning_: Systemet använder nu orden&quot;objekt&quot; och&quot;objekt&quot; korrekt i det lageruppbyggda navigeringsfilterobjektet, vilket gör filterbeskrivningarna tydligare och exaktare. Tidigare användes dessa ord felaktigt, vilket kan skapa förvirring för användare som navigerar i filteralternativen.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/38789>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/pull/37852>
* _AC-12164_: Formatet Datum och tid för det anpassade alternativet fungerar inte
   * _Korrigera anteckning_: Systemet tillämpar nu korrekt det konfigurerade datumformatet på anpassade produktalternativ av typen Datum, vilket säkerställer att datumformatet visas korrekt på frontsidan. Tidigare speglade inte ändringar i datumformatskonfigurationen på frontend för anpassade produktalternativ av typen Date.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/32990>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/pull/38925>
* _AC-13068_: Listrutealternativ saknas
   * _Korrigera anteckning_: Nu visas alla värden korrekt i listrutan när ett nytt attribut med fler än 20 värden skapas. Tidigare visades bara de första 20 värdena eller något annat av de valda sidvärdena, vilket medförde att de återstående värdena saknades.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/47b448e2>
* _AC-13296_: [Problem] Använd aktuellt lager-ID för kategorins körtidscache
   * _Korrigera anteckning_: Systemet använder nu korrekt det aktuella lagrings-ID:t för kategorikörningscache, vilket förhindrar åsidosättning av data när emulering används eller anpassad kod sparar kategorin i olika butiker. Tidigare kunde objektet som lagrats i körningsmiljön ha kommit från fel butik, vilket ledde till åsidosättande av data.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/39310>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/pull/36394>
* _AC-13324_: bin/magento sampledata:deploy —no-update genererar ett undantag
   * _Korrigera anteckning_: Systemet accepterar nu ett booleskt värde korrekt när alternativet —no-update används i kommandot sample data:deploy, vilket förhindrar fel under distributionen av exempeldata. Tidigare uppstod ett fel när det här kommandot användes eftersom systemet felaktigt förväntade sig ett heltalsvärde.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/39344>
   * _Bidrag till_ GitHub-kod: <https://github.com/magento/magento2/pull/39345>
* _AC-13355_: [Problem: Åtgärda] användning av EAV-cachetyp
   * _Fix note_: Systemet använder nu EAV-cachetypen korrekt på alla relevanta platser, vilket säkerställer konsekvent och effektiv datacachelagring. Tidigare användes EAV-cachetypen inte konsekvent, vilket ledde till ineffektivitet och inkonsekvenser i datacachningen.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/32322>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/pull/31264>
* _AC-13596_: Katalogsökning med tomma data går till sökresultatsidan[2.4.dev-grenen]
   * _Korrigera anteckning_: Systemet behåller nu användare korrekt på sidan Avancerad sökning och visar ett felmeddelande när de försöker utföra en sökning utan att ange några data. Tidigare omdirigeras användare till sidan Avancerad sökning i katalog med ett meddelande som uppmanar dem att ändra sökningen.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/6cfb9b6b>
* _AC-13622_: [Utgåva] Produktlayout baserad på attribute_set
   * _Korrigera anteckning_: Systemet tillåter nu att produktlayouten justeras baserat på attributuppsättningen, vilket ger ett mer praktiskt och effektivt sätt att hantera produktvisningen i klientbutiken. Tidigare kunde layouten bara justeras av SKU eller efter produkttyper, vilket inte alltid var praktiskt för många produkter eller specifika artiklar.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/38790>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/pull/36244>
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
   * _Åtgärdsmeddelande_: Lager visas nu enligt vald butik.
   * _Bidrag till_ GitHub-kod: <https://github.com/magento/inventory/commit/bdbf97ea>
* _ACP2E-2621_: Widgetens innehåll uppdateras inte på cms-sidan
   * _Fixnotering_: Systemet uppdaterar nu widgetinnehållet på en CMS-sida när en produkt ställs in som ny och sparas, vilket säkerställer att sidan visar den uppdaterade produktsamlingen. Tidigare uppdaterades inte sidan för att visa den nya produkten på grund av felaktiga cacheidentiteter som användes för widgeten i cacheminnet.
   * _Bidrag till_ GitHub-kod: <https://github.com/magento/magento2/commit/f89a447e>
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
   * _Fix note_: Produktbilder tas inte bort när du tar bort staging-uppdateringen.
   * _Bidrag till_ GitHub-kod: <https://github.com/magento/magento2/commit/c8931218>
* _ACP2E-2799_: [Fel produktpris för molnpaket] när det används med nivåpriser
   * _Fix-anteckning_: Tidigare vid beräkning av vissa procentuella rabatter avrundade uppåt till 2 decimaler genererade olika slutpriser för kundvagnen och produktlistningssidan/produktinformationssidan. När den här korrigeringen har tillämpats är det slutliga priset för paketprodukten detsamma som på produktinformationssidan, produktlistningssidan och minikundvagnssidan.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/38091>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/b2286ecf>
* _ACP2E-2805_: Regeln för katalogkampanjer fungerar inte med quantity_and_stock_status attribut
   * _Fix:_ Attributet quantity_and_stock_status kommer nu att beaktas av katalogkampanjregeln, som inte tidigare beaktades när en ny produkt genererades från administratörssidan.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/35627>
   * _Bidrag till_ GitHub-kod: <https://github.com/magento/inventory/commit/cf34971d>
* _ACP2E-2837_: Kolumnvärden för produktenhet updated_at uppdateras inte vid uppdatering av pris via REST API
   * _Åtgärdsmeddelande_: Kolumnen &quot;senast uppdaterad kl&quot; från administratören uppdateras till rätt datum och tid när de befintliga produkterna uppdateras via REST API. Tidigare uppdaterades inte kolumnen &quot;senast uppdaterad&quot; korrekt.
   * _Bidrag till_ GitHub-kod: <https://github.com/magento/magento2/commit/39d54c2d>
* _ACP2E-2840_: Det går att ange icke-unika värden via produktimport
   * _Korrigera anteckning_: Systemet använder nu den unika värdebegränsningen för unika produktattribut vid import, vilket förhindrar dubblettvärden för det attributet. Tidigare var det möjligt att ange icke-unika värden för produktattribut som konfigurerats att ha unika värden via produktimport.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/38445>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/7e0e5582>
* _ACP2E-2843_: Produkter på klientsidan lagrar specifika data när Single-Store-läge är aktiverat
   * _Korrigera anteckning_: Tidigare migrerades inte ändringarna till webbplatsnivå när vi aktiverade läget för en enskild butik för standardbutiksvyn. När den här korrigeringen har tillämpats synkroniseras standardarkivspecifika data med data på webbplatsnivå när läget för en enskild butik aktiveras, och eventuella konflikter för produkter och kategorier kommer att lösas.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/c8931218>
* _ACP2E-2857_: Det går inte att ställa in &quot;Standardsortering efter&quot; i en kategori med hjälp av resten API
   * _Fix note_: Uppdatera korrekt default_sort_by på en kategori via REST / SOAP APi-begäran
   * _Bidrag till_ GitHub-kod: <https://github.com/magento/magento2/commit/57a32313>
* _ACP2E-2871_: [Molnet] Handlaren står inför problem med antal önskelistor
   * _Åtgärdsmeddelande_: Att lägga till en produkt i önskelistan i en butik ökar inte längre antalet önskelistor i andra butiker som är öppna i samma webbläsare. Tidigare hade antalet önskelistor ökat även i den andra butiken om båda butikerna lästs in i samma webbläsare.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/3a7c4d17>
* _ACP2E-2874_: Kategorisidan i förgrunden visar tomma platser när paketprodukten används
   * _Korrigera anteckning_: Paketprodukter som inte kan säljas i den aktuella butikskontexten indexeras inte längre.
   * _GitHub-kodbidrag_: <https://github.com/magento/inventory/commit/bc37ec76>
* _ACP2E-2905_: [Cloud] Utfärdande av offert i arkitektur för flera webbplatser
   * _Korrigera anteckning_: Tidigare kunde inte arkitekturen för flera webbplatser med olika valutor och kundgrupper tillämpa rabatter på butiken korrekt. När den här korrigeringen har implementerats kommer flerwebbplatsarkitekturen med olika kundgruppsprisrabatter att gälla för olika butiker.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/38506>
   * _Bidrag till_ GitHub-kod: <https://github.com/magento/magento2/commit/a4fbf702>
* _ACP2E-2909_: dynamic-rows.js:658 Uncaught TypeError: dataRecord.slice vid redigering av paketprodukter
   * _Fixnotering_: Det finns inget javascript-fel i webbläsarkonsolen när du tar bort alternativet från paketprodukten.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/38505>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/93d50f8d>
* _ACP2E-2950_: [Cloud] Felaktigt produktpris i orderbekräftelsen
   * _Korrigera anteckning_: Korrekt belopp visas för paketalternativ i ordning på Storefront när en annan valuta än bas användes.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/a4fbf702>
* _ACP2E-2956_: YouTube-video lägger till bugg
   * _Korrigera anteckning_: Produktbilder och videor har konfigurerats i det globala omfånget. Eftersom du inte kan ha en produktvideo i ett omfång och inte i ett annat, har Youtube API-nyckelinställningen ställts in på globalt omfång.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/a4fbf702>
* _ACP2E-2964_: [Cloud] URL-uppdatering endast för store_id=0
   * _Korrigera anteckning_: URL-sökvägen lagras nu med rätt lagrings-ID. Tidigare var lagrings-ID felaktigt, vilket resulterade i att felaktiga URL-sökvägar återstår i databasen när kategorier flyttas.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/9af794a4>
* _ACP2E-3009_: async.operations.all kördes och skapade ett fel.
   * _Åtgärdsmeddelande_: Felaktiga produktlänkdata i REST API-anrop orsakar inte längre kritiska fel.
   * _Bidrag till_ GitHub-kod: <https://github.com/magento/magento2/commit/a4fbf702>
* _ACP2E-3029_: [Problem med molnmobil] Det går bara inte att klämma på PDP-bilden
   * _Korrigera anteckning_: Systemet har nu stöd för funktionen att nypa till zooma i bilder av produktinformationssidor i mobilvyn i Chrome, vilket förbättrar användarupplevelsen för mobila enheter. Tidigare zoomade inte dubbeltryck på bilden i mobilvyn i Chrome in på bilden som förväntat.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/148c3ead>
* _ACP2E-3058_: Etikett saknas i LayeredNavigation med alternativnamnet 0
   * _Åtgärdsmeddelande_: Problemet har lösts genom att hoppa över en tom värdekontroll för attributvärdet 0. Tidigare ansågs den vara tom och orsakade problemet.
   * _Bidrag till_ GitHub-kod: <https://github.com/magento/magento2/commit/3a7c4d17>
* _ACP2E-3069_: Kunder ser priser från andra kundgrupper
   * _Fixat_: Fixade ett problem där kundgruppsrelaterad information sparades i fel segment på grund av det gamla värdet på X-Magento-Vary i begäran
   * _Bidrag till_ GitHub-kod: <https://github.com/magento/magento2/commit/d1f7dc95>
* _ACP2E-3076_: Fel vid borttagning av paketalternativ
   * _Korrigera anteckning_: Systemet tar nu bort paketalternativen korrekt utan att utlösa ett fel eller få sidan att sluta svara. Om du tidigare försökte ta bort paketalternativen skulle det resultera i felet&quot;Sidan svarar inte&quot; och förhindra att produkten sparas.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/6a185204>
* _ACP2E-3100_: [Cloud] Bildfilen finns inte i New Relic fellogg
   * _Korrigera anteckning_: Systemet synkroniserar nu anpassade platshållarbilder till lokal lagring så att de återges korrekt när du använder fjärrlagring som AWS S3. Tidigare kunde inte anpassade platshållarbilder återges när fjärrlagring användes, vilket resulterade i en trasig bildvisning och felloggar.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/d1f7dc95>
* _ACP2E-3103_: RSS-flöde för nya produkter uppdateras inte med nya produkter på grund av cache
   * _Korrigera anteckning_: RSS-flödet för nya produkter uppdateras nu när en produkt har angetts som ny och sparad
   * _Bidrag till_ GitHub-kod: <https://github.com/magento/magento2/commit/d01ee51e>
* _ACP2E-3126_: [GQL-svar från Cloud] Product Media Gallery sorteras inte efter bildposition
   * _Korrigera anteckning_: Systemet sorterar nu objekt korrekt i mediegalleriet efter position i GraphQL-svaret, vilket ger rätt visningsordning. Tidigare sorterades inte objekt i mediegalleriet efter position, vilket ledde till en felaktig visningsordning.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/37671>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/b21e5d91>
* _ACP2E-3136_: [Underkategoriobjekt i molnet] visas inte i widgetredigeringen på administratörens serverdel
   * _Korrigera anteckning_: Kategoriträdet på den nya widgetsidan bör inte längre ha problem med att läsa in kategorierna Nivå 5+. Tidigare saknades vissa kategorier när trädet lästes in efter kategorierna Nivå 5.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/148c3ead>
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
   * _Fix-anteckning_: Före korrigeringen konstruerades konfigurerbara produktvarianter baserat på alla möjliga kombinationer av attributalternativ. I de fall där attributen hade många alternativ resulterade detta i en långsam och resurskrävande åtgärd. Nu kan du konstruera produktvariationer utifrån befintliga underordnade produktattribut. Detta resulterar i betydligt färre beräkningar, vilket innebär en förbättrad resursanvändning.
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
* _ACP2E-3513_: [CLOUD] Specialpriset visas inte i den konfigurerbara produkten
   * _Korrigera anmärkning_: Efter korrigeringen påverkas inte visningen av specialpriset för konfigurerbara produkter om du ändrar värdet &quot;Används i produktlista&quot; för specialprisattributet.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/d4de4726>
* _ACP2E-3516_: Tillfälliga register rensas inte om processen avslutas
   * _Korrigera anteckning_: Temporära tabeller för indexeraren för CatalogRule rensas nu om indexeringsprocessen avslutas
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/1984c61c>
* _ACP2E-3520_: [QUANS] Kärnenhetstestfel i 2.4.7-p3
   * _Korrigera anteckning_: Versionsinformation för det här testet behövs inte eftersom det är en förbättring av enhetstestet.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/1984c61c>
* _ACP2E-3533_: Prestandaproblem i hämtning av lagerkvantitet för grupperade produkter med flera källor
   * _Korrigeringsanteckning_: Redigeringssidan för grupperad produkt och paketprodukt är nu optimerad när tilldelade produkter har ett stort antal lagerkällor.
   * _GitHub-kodbidrag_: <https://github.com/magento/inventory/commit/0208e433>
* _ACP2E-3641_: Refix https://jira.corp.adobe.com/browse/ACP2E-3389
   * _Korrigera anteckning_: Förbättrade prestanda för administratörskategorisidan vid ett stort antal ankarkategorier
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/982b1c42>

### Katalog, innehåll

* _ACP2E-3063_: [Cloud]-cachen ogiltigförklaras inte.
   * _Korrigera anteckning_: När en CMS-sida med en uppdaterad designlayout sparades reflekterades den inte korrekt på framsidan. När den här korrigeringen har tillämpats visas rätt designlayout längst fram när vi ändrar designlayouten och sparar CMS-sidan.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/66dea0de>
* _ACP2E-3131_: [Cloud] ankarkategorier/icke-ankarkategorier inverterade i innehållswidgeten
   * _Korrigera anteckning_: När vi tidigare valde Visa på -> ankarkategorier visades alla kategorier som inte reflekterade relationen mellan överordnad och underordnad mellan ankarpunkten och icke-ankarpunkten. När den här korrigeringen har tillämpats visar Display On -> Anchor Categories endast Anchor Categories (valbar) och Display On -> Non Anchor Categories visar Non-Anchor Categories (valbar)
   * _Bidrag till_ GitHub-kod: <https://github.com/magento/magento2/commit/7377de59>
* _ACP2E-3152_: Kategorier fungerar inte med widgetar
   * _Fix note_: Tidigare, om vi sparade CMS-blocket för olika ankare/icke-ankarkategorier, fungerade det inte för de underordnade kategorierna när det visades på frontend. När den här korrigeringen har tillämpats visas blocket i frontend för olika kategorier.
   * _Bidrag till_ GitHub-kod: <https://github.com/magento/magento2/commit/d01ee51e>

### Katalog, Ramverk

* _AC-9111_: Order get(Shipments|Creditmemos|Invoice)Collection - Samlingen ska inte läsas in
   * _Korrigera anteckning_: Systemet ser nu till att samlingarna för försändelser och kreditnotor inte är förinlästa när de hämtas från en order, vilket gör att ytterligare filter eller order kan tillämpas på dessa samlingar. Tidigare lästes dessa samlingar in automatiskt, vilket förhindrar ytterligare ändringar.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/37561>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/pull/37562>
* _ACP2E-2949_: [Molnuppföljning]: Matchningsfel i datajämförelse när man kontrollerar om data har ändrats
   * _Åtgärdsmeddelande_: Tidigare anropades det sparade objektet varje gång utan några dataändringar (för alla numeriska datafält - t.ex. int/float/double). Den utlöser flaggan _hasDataChanges till true och anropar funktionen save. Den kontrollerar inte heller de flytande talen som är inkapslade med sträng. När den här korrigeringen har tillämpats anropas funktionen spara bara om data har ändrats. Datavärdet för int/float/double check med värdet som skickas till funktionen och utför strikt typmatchning
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/c8931218>

### Katalog, GraphQL

* _ACP2E-3090_: Hantera kategorifilter i GraphQL: includeDirectChildrenOnly och category_uid
   * _Fix-anteckning_: Endast de direkta underordnade kategorierna hämtas vid filtrering efter category_uid.
   * _Bidrag till_ GitHub-kod: <https://github.com/magento/magento2/commit/93d50f8d>
* _ACP2E-3166_: [Sortering av Cloud] Graphql-produkter fungerar inte
   * _Åtgärdsmeddelande_: GraphQl Product sortering efter flera fält när fälten skickas i variabler fungerar nu som förväntat.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/8459b17d>
* _ACP2E-3312_: Tier Prices returnerar fel värde i GraphQL-produkter (jämfört med Storefront)
   * _Korrigera anteckning_: Efter korrigeringen har produktskiktspriserna som returnerats för grafikförfrågningar priset per ett objekt.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/1366ae5e>

### Katalog, priser, mellanlagring och förhandsvisning

* _ACP2E-2672_: [Cloud] API-slutpunkten för specialpris returnerar ett fel när ett stort antal produkter uppdateras samtidigt
   * _Korrigera anteckning_: Nu skapas en kampanj för varje datumintervall i stället för flera schemalagda uppdateringar för varje produkt och datumintervall. Dessutom kommer det att stödja samtidiga API-begäranden för snabbare bearbetning av ett stort antal SKU:er.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/f89a447e>

### Katalog, produkt

* _AC-7050_: Kategorivalsträdet i redigeringsprodukten är inte i samma ordning som i Catalog->Kategorier
   * _Korrigera anteckning_: Systemet visar nu kategorivalsträdet korrekt i produktredigeringsavsnittet i samma ordning som i Katalog->Kategorier, vilket gör produktadministrationen enklare i stora kataloger. Tidigare visades kategoriträdet i produktredigeringsavsnittet i den ordning som kategorin skapades, oavsett visningsordningen i Katalog->Kategorier.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/36101>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/pull/36104>

### Katalog, SEO

* _ACP2E-3653_: Felaktig kanonisk URL för kategori när sida > 1
   * _Korrigera anteckning_: Tidigare fungerade inte den kanoniska URL:en för flersidigt innehåll korrekt, utan baswebbadressen visades konsekvent. När korrigeringen har implementerats visar den kanoniska URL:en för flersidigt innehåll nu korrekt URL:en med sid-ID:t.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/982b1c42>

### Katalog, söka

* _ACP2E-2757_: Produkter som inte visas i kategori och sökning, men direktlänkar fungerar
   * _Korrigera anteckning_: Tidigare fungerade inte attributet Yes/No med price_* attribute_code med indexering. Efter den här korrigeringen fungerar attributet Yes/No som förväntat.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/ba25af8a>
* _ACP2E-3053_: [Cloud] Elastiskt sökfel på vissa kategorisidor
   * _Korrigera anteckning_: Tidigare, med konfigurationsbiljetten angiven, utlöstes ett undantag på gruppkategorisidan när vi sätter priset 0 för flera produkter. Efter denna korrigering tillämpas när flera produktpriser 0 och vi laddar kategorisidan i frontend kommer det inte att kasta något undantag och kommer att ladda kategorisidan framgångsrikt.
   * _Bidrag till_ GitHub-kod: <https://github.com/magento/magento2/commit/c8931218>
* _ACP2E-3345_: Typfel uppstod när objekt skapades: Magento\CatalogSearch\Model\Indexer\Fulltext\Interceptor Exception
   * _Fix note_: Efter korrigeringen kan en instans av klassen Magento\CatalogSearch\Model\Indexer\Fulltext skapas utan att ange $data.
   * _Bidrag till_ GitHub-kod: <https://github.com/magento/magento2/commit/1366ae5e>
* _ACP2E-3521_: [CLOUD] Problem med produkter visas inte i Edge efter att de sparats i Magento Admin
   * _Korrigera anteckning_: Efter korrigeringen går det inte att missa konfigurerbara produkter med underordnade produkter med långa namn i butiken.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/1984c61c>

### Moln

* _ACP2E-3010_: [Cloud] PHPSESSID ändrar varje POST-begäran
   * _Korrigera anteckning_: PHPSESSID återskapas inte längre på POST-begäranden i frontend för en inloggad kund om L2 Redis-cache är aktiverad och kunden har uppdaterats från backend-sidan
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/6a185204>
* _ACP2E-3532_: Varningar för att skapa webbplatskartor
   * _Korrigera anteckning_: Efter korrigeringen genereras platskartan i systemets TMP-katalog och kopieras till det slutliga målet.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/d4de4726>

### Innehåll

* _AC-10539_: [Problem] med prisvisningen i widgeten Senast visade
   * _Korrigera anteckning_: Systemet visar nu priset på enkla produkter som inte finns i lager i widgeten &quot;Senast visade produkter&quot;, vilket ger en konsekvent hantering för alla widgetar och produktlistsidor. Tidigare visades inte priset på färdiga enkla produkter i widgeten &quot;Senast visade produkt&quot; på grund av ett villkor i prissättningsmallarna.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/38167>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/pull/38159>
* _AC-10596_: [Problem] Korrigera stavfel och grammatik i filen acl.xsd
   * _Korrigera anteckning_: Systemet rättar nu till ett stavfel och grammatikfel i filen acl.xsd, vilket gör dokumentationen tydligare och exaktare. Tidigare innehöll filen acl.xsd ett stavfel och en felaktig grammatik, vilket skulle kunna orsaka förvirring.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/38061>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/pull/38046>
* _AC-10845_: Bannerbild för sidbyggare visas inte i galleriet
   * _Åtgärdsmeddelande_: Systemet visar nu bannerbilder som laddats upp i nyskapade mappar i Pagebuilder-galleriet på ett korrekt sätt, vilket eliminerar tidigare konsolfel. Före den här korrigeringen visades inte banderollbilder i galleriet om de laddades upp i en ny mapp, vilket orsakade ett konsolfel.
   * _Bidrag till_ GitHub-kod: <https://github.com/magento/magento2/commit/c8f87c25>
* _AC-12283_: &quot;Riktnummer ej inställt&quot; efter uppdatering till 2.4.5-p8
   * _Åtgärdsmeddelande_: Systemet har nu slutfört distributionsprocessen för statiskt innehåll när Magento_CSP-modulen är aktiverad och &quot;dev/js/translate_strategy&quot; är inställt på &quot;embedded&quot;, utan att utlösa felet &quot;Riktnummer har inte angetts&quot;. Tidigare misslyckades den statiska innehållsdistributionsprocessen under dessa förhållanden med felet&quot;Ingen riktkod har angetts&quot;.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/38845>
   * _Bidrag till_ GitHub-kod: <https://github.com/magento/magento2/pull/38922>
* _AC-12692_: Widgetkategoriträdet återges inte korrekt
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/39008>
   * _Bidrag till_ GitHub-kod: <https://github.com/magento/magento2/commit/58e40ceb>
* _AC-13054_: Det går inte att se meddelandet &quot;Använder standardvärde&quot; när du ändrar temat på designkonfigurationssidan
   * _Fix-anteckning_: Systemet innehåller nu en separat kolumn för att visa meddelandet &quot;Använder standardvärde&quot; beroende på det valda temat på designkonfigurationssidan. Detta säkerställer tydlighet och synlighet för standardvärdesstatusen. Tidigare visades inte meddelandet &quot;Använder standardvärde&quot;, vilket ledde till förvirring om statusen för det valda temat.
   * _Bidrag till_ GitHub-kod: <https://github.com/magento/magento2/commit/47b448e2>
* _AC-13569_: [Problem] Återställer bakåtkompatibilitet med TinyMCE-plugins igen (efter det...
   * _Fix-anteckning_: Systemet återställer nu bakåtkompatibilitet med TinyMCE-plugins, vilket gör att funktioner som definierats inuti plugin-programmet kan anropas när widgeten används från en annan plats. Tidigare, på grund av en ändring i TinyMCE-versionen, returnerade plugin-programmen inte widgetarna som ett objekt, vilket resulterade i ett fel när vissa funktioner försökte anropa vissa funktioner i widgetinstansen.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/39262>
   * _Bidrag till_ GitHub-kod: <https://github.com/magento/magento2/pull/39258>
* _AC-9638_: [Problem] med problem med filuppladdning i WYSIWYG-redigeraren på produktsidan
   * _Fixnotering_: Systemet visar nu mappträdet korrekt och tillåter bilduppladdningar i WYSIWYG-redigeraren på produktsidan, även efter att du först har expanderat fliken &quot;Bilder och videor&quot;. Tidigare resulterade en expansion av fliken &quot;Bilder och videor&quot; först i att mappträdet inte visades och ett felmeddelande när du försökte ladda upp en bild i WYSIWYG-redigeraren.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/38026>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/pull/38025>
* _ACP2E-2392_: [On-PREM] Problem med dynamiskt block
   * _Fix note_: Wdigets renderas nu korrekt i dynamiska block.
   * _Bidrag till_ GitHub-kod: <https://github.com/magento/magento2/commit/a12063bd>
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
   * _Bidrag till_ GitHub-kod: <https://github.com/magento/magento2/commit/35b1b1da>
* _ACP2E-3064_: Fel Page Builder vid redigering av CMS-block
   * _Korrigera anteckning_: Systemet sparar nu ändringar som gjorts i administratörsområdet med Page Builder korrekt, utan att utlösa felet&quot;Page Builder återgav i 5 sekunder utan att frigöra lås&quot;. i webbläsarkonsolen. Tidigare inträffade detta fel när ändringar skulle sparas, vilket förhindrar att innehållet uppdateras.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/35b1b1da>, <https://github.com/magento/magento2-page-builder/commit/4d5db10a>
* _ACP2E-3092_: [CLOUD] Inga knappar för utcheckning eller redigering av kundvagn i kundvagnssektionen
   * _Korrigera anteckning_: Paketprodukten läggs nu till i vagnen via widgetar utan fel.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/b21e5d91>, <https://github.com/magento/magento2-page-builder/commit/4ebe3f1d>
* _ACP2E-3122_: [CLOUD] Knappen Överför bild fungerar inte
   * _Korrigera anteckning_: Före knappen Överför bild för Banner och Slider från PageBuilder fungerade inte som förväntat, och när du trycker på knappen öppnas den lokala filhanteraren för att välja den bild som ska överföras.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2-page-builder/commit/476ef8ea>
* _ACP2E-3127_: imagecreatetruecolor(): Argument #2 ($height) måste vara större än 0. Det går inte att överföra en viss bild
   * _Korrigera anteckning_: Problemet med att bilder med höjden 0 överfördes via mediegalleriet löstes och resurssynkroniseringen slutfördes med synkroniseringskommandot. Tidigare gick det inte att överföra bilden via mediegalleriet och synkroniseringskommandot misslyckas också när en viss bild finns i galleriet.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/6f4805f8>
* _ACP2E-3154_: Prototype.js Array.from i konflikt med Google Maps API
   * _Korrigera anteckning_: Google Maps återges nu korrekt i PageBuilder-redigeraren. Tidigare förhindrade ett Javascript-fel Google Maps från att återges korrekt.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/148c3ead>
* _ACP2E-3275_: [Cloud] - CMS Slider återspeglar inte de senaste ändringarna
   * _Åtgärdsmeddelande_: Problemet har åtgärdats genom att se till att skjutreglaget uppdateras medan spara-händelsen utlöses på redigeringsskärmen. Tidigare utlöstes den och orsakade problemet.
   * _Bidrag till_ GitHub-kod: <https://github.com/magento/magento2-page-builder/commit/ae2cdeb0>
* _ACP2E-3326_: Ett fel inträffar på CSM-sidan när CMS-block infogas med hjälp av Page Builder i en viss ordning
   * _Korrigera anteckning_: Tidigare i vissa versioner av PHP och OS (Linux) hade återgivningen av block som refererade till andra cms-block via PageBuilder misslyckats med &quot;Ett okänt fel uppstod. Försök igen.&quot;. Nu återges innehållet i cms-blocken korrekt i ett PageBuilder-kontrollerat innehåll.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2-page-builder/commit/ae2cdeb0>
* _ACP2E-3428_: Förhandsgranskningsfel för sidbyggarens mall för stort innehåll
   * _Korrigera anteckning_: Ett stort innehåll ledde till att arbetsyteelementet flöde över webbläsarens gränser och returnerade ett felaktigt värde, vilket gjorde att backend-koden (bilden kan inte avkodas korrekt). Åtgärdat med begränsning av arbetsytans storlek till den universella webbläsarens gräns.
   * _Bidrag till_ GitHub-kod: <https://github.com/magento/magento2-page-builder/commit/adfb1747>
* _ACP2E-3430_: De senaste säkerhetsuppdateringarna med TinyMCE 7 saknar teckenstorlek
   * _Åtgärdsmeddelande_: Väljare för teckenstorlek och teckensnittsfamilj är nu tillgängliga i WYSIWYG-redigeraren. Innan den här korrigeringen var dessa inte tillgängliga i redigeringsgränssnittet med TinyMCE 7.
   * _Bidrag till_ GitHub-kod: <https://github.com/magento/magento2/commit/d50f6b5d>, <https://github.com/magento/magento2-page-builder/commit/2c2f7a0e>
* _ACP2E-3483_: TinyMCE 7 editor teckenstorlek i admin i PT och inte PX vänligen förtydliga
   * _Fix-anteckning_: Innan korrigeringen kunde du inte ange teckenstorlek i px i WYSIWYG-områden. Nu kan du ställa in teckenstorleken i px istället för pt.
   * _Bidrag till_ GitHub-kod: <https://github.com/magento/magento2/commit/3f12d152>, <https://github.com/magento/magento2-page-builder/commit/20aa5d7a>
* _ACP2E-3490_: Produktinnehållstypen i Page Builder komprimeras utan korrekta meddelanden
   * _Korrigera anteckning_: Före korrigeringen genererades inte HTML-koden för förhandsgranskning korrekt när det inte fanns några produkter i widgeten. Nu genereras det tomma svaret korrekt och produktwidgeten visas korrekt i förhandsgranskning.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/3f12d152>, <https://github.com/magento/magento2-page-builder/commit/20aa5d7a>
* _ACP2E-3534_: [page builder]Om produktlistor läggs till i block uppstår fel
   * _Korrigera anteckning_: Om du lägger till programpaketproduktlista för att blockera via sidbyggare uppstår inga fel
   * _Bidrag till_ GitHub-kod: <https://github.com/magento/magento2/commit/344fce23>

### Kund/ Kunder

* _AC-12162_: Front end - Det gick inte att validera födelsedatumet på sidan Kund
   * _Korrigera anteckning_: Se till att all validering fungerar efter uppgraderingsövningen.js systemberoende av den senaste delversionen
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/de4dfb8e>
* _AC-8499_: Regiontextfältet återställs inte när listrutan för land ändras
   * _Korrigera anteckning_: Systemet återställer nu regionens textfält när landet ändras i listrutan, vilket säkerställer att tidigare värden inte kvarstår. Tidigare återställdes inte regionfältet om landet ändrades från listrutan, vilket innebar att det senast sparade värdet bevaras.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/3ea26621>
* _AC-9240_: Om du tar bort kunden rensas inte alla sessionsdata för webbläsaren på Storefront för inloggad och borttagen kund
   * _Korrigera anteckning_: Om en kund tas bort rensas alla webbläsarsessionsdata från butiken för inloggade och borttagna kunder som förväntat. Köparen kan fortsätta handla och webbläsaren behandlar sin session som en gästsession. Tidigare när kundkontot för en inloggad kund togs bort från Admin uppstod JavaScript-fel i webbläsaren.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/7d5e3906>

### Ramverk

* _AC-10037_: [Fråga]Oanvänd typkonfiguration i `app/code/Magento/Translation/etc/di.xml`
   * _Fix note_: Systemet tar nu bort oanvända beroenden i konfigurationen, vilket förbättrar den övergripande kodrenheten och effektiviteten. Tidigare fanns det oanvända beroenden i konfigurationen som inte bidrog till några funktioner.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/38030>
   * _Bidrag till_ GitHub-kod: <https://github.com/magento/magento2/pull/38064>
* _AC-10654_: V1/kunder/lösenordsslutpunkt fråga/problem
   * _Fix note_: Systemet följer nu de begränsningar som ställts in i hanteringsgränssnittet när begäran om lösenordsändring bearbetas via API:et, vilket förhindrar potentiellt missbruk av funktionen för återställning av lösenord. Tidigare kunde API:t bearbeta begäranden om lösenordsändringar utanför de regler som definierats i det hanterade användargränssnittet, vilket eventuellt skulle möjliggöra en konstant ström av återställda e-postmeddelanden om giltiga e-postmeddelanden var kända.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/38238>
   * _Bidrag till_ GitHub-kod: <https://github.com/magento/magento2/commit/0c53bbf7>
* _AC-10738_: Lackkonfigurationen utesluter inte alla marknadsföringsparametrar
   * _Fix note_: Systemet utesluter nu korrekt alla vanliga marknadsföringsparametrar i Varnish-konfigurationen, vilket säkerställer korrekt spårning och analys. Tidigare uteslöts inte vissa marknadsföringsparametrar som gad_source, srsltid och msclkid, vilket ledde till potentiella felaktigheter i datainsamlingen.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/38298>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/pull/39188>
* _AC-10838_: Indexeringsprocess för katalogsökindexprocessfel
   * _Korrigera anteckning_: Systemet slutför nu kommandot för omindexering utan att stöta på några fel, oavsett vilken libxml-version som kompilerats med PHP. Tidigare resulterade omindexeringskommandot i ett fel av typen&quot;Katalogsökindexprocessfel under indexeringsprocessen&quot; när PHP kompilerades med vissa versioner av libxml.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/38254>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/pull/38553>, <https://github.com/magento/magento2/commit/0574ac23>
* _AC-10941_: Filtren created_at, status och total_total_total har lagts till i kundorderfrågan och flera filterfel har åtgärdats
   * _Korrigera anteckning_: Systemet stöder nu användningen av filtren created_at, status och total_total i kundorderfrågor och har åtgärdat ett problem där flera filter inte tillämpades korrekt. Tidigare hade systemet inte stöd för dessa filter och kunde inte tillämpa alla filter när mer än ett användes i en fråga.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/38392>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/pull/36949>
* _AC-10991_: Slumpmässigt översvämmas av frågor från relaterade block/merförsäljning/korsförsäljning och prisindexering
   * _Korrigera anteckning_: Systemet optimerar nu frågor från relaterade block, merförsäljning och korsförsäljning, vilket förbättrar prestanda och förhindrar att webbplatsen kraschar på grund av för många frågor. Tidigare kunde systemet bli överbelastat med frågor från de här blocken, vilket gjorde att det gick betydligt långsammare och kunde göra att webbplatsen inte fungerade som den skulle.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/36667>
   * _Bidrag till_ GitHub-kod: <https://github.com/magento/magento2/pull/38050>
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
* _AC-11592_: [Utgåva] Tillåt endast giltiga inställningar under konfiguration:di:kompilering
   * _Korrigera anteckning_: Systemet genererar nu ett fel under kompileringskommandot setup:di:om en inställning skapas för en klass som inte finns eller som är exkluderad, vilket säkerställer att endast giltiga inställningar tillåts. Tidigare misslyckades dessa scenarier utan att någon information om plugin-program som är associerade med de ursprungliga klasserna återges.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/38517>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/pull/33161>
* _AC-11651_: Magento försöker ändra den skrivskyddade egenskapen i __wakeup-metoden för LoggerProxy
   * _Korrigera anteckning_: Systemet tillåter nu att tidigare skrivskyddade egenskaper ändras i LoggerProxyns __wakeup-metod, vilket ger en smidig funktion utan att användarna tvingas använda en lösning. Tidigare uppstod problem om du försökte tilldela om värdet för en skrivskyddad egenskap i LoggerProxyns __wakeup-metod.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/38526>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/c8f87c25>
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
* _AC-11809_: [Problem] Skicka anpassade attribut till den aktuella länken via XML
   * _Korrigera anteckning_: Systemet tillåter nu att anpassade attribut skickas till den aktuella länken via XML, vilket säkerställer att attributen visas korrekt även när länken är den aktuella sidan. Tidigare visades inte anpassade attribut för den aktuella sidlänken eftersom metoden getAttributesHtml() inte används för den aktuella länken.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/38500>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/pull/30070>
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
* _AC-12002_: [Problem] [Visa] Extra utrymme i länk- och skripttagg har tagits bort
   * _Korrigera anteckning_: Systemet ser nu till att det inte finns några extra blanksteg i länk- och skripttaggarna, vilket ger en renare och mer effektiv kod. Tidigare gick det att hitta dubbla mellanslag mellan attribut i link- och script-taggarna.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/32920>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/pull/32919>
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
* _AC-12594_: [Problem] Använd kompilerad konfiguration för genererade data i stället för allmän konfiguration
   * _Korrigera anteckning_: Systemet använder nu den kompilerade konfigurationen för genererade data i stället för den allmänna konfigurationen, vilket minskar nätverksöverföringen och belastningen på data som är beroende av en viss version av koden. Den här ändringen förhindrar åsidosättning av cache i delade instanser under behållarbyte, vilket leder till förbättrad stabilitet och minskad drifttid. Tidigare använde vissa huvudklasser en delad config-typ, vilket kan leda till att cache-lagring åsidosätts eller att programmet blir driftsavbrott på grund av skillnader i kodversioner mellan flera servrar.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/38785>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/pull/29954>
* _AC-12597_: [Problem] Ta bort referenser till filer från filer som har tagits bort i e1ccdb..
   * _Korrigera anteckning_: Systemet tar nu bort referenser till filer från tidigare borttagna filer, vilket eliminerar fel i webbläsarens konsol och systemloggfilen. Tidigare orsakade dessa referenser fel på grund av att det inte fanns några refererade filer.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/38960>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/pull/38951>
* _AC-12778_: [Utgåva] Mindre rensning: korrigerad felaktig användning av sprintf, tar bara två platshållare här och w..
   * _Korrigera anteckning_: Systemet använder nu sprintf-funktionen korrekt med rätt antal platshållare, vilket förbättrar renheten och konsekvensen i koden. Tidigare användes sprintf-funktionen felaktigt med ett extra argument, som inte orsakade några större problem men som inte var korrekt.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/39062>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/pull/38628>
* _AC-12857_: PHP 8.2.15 har tagit bort FTP-tillägget
   * _Korrigera anteckning_: Systemet inkluderar nu FTP-tillägget som ett beroende i filen Composer.json, vilket säkerställer att CSV-import via FTP kan konfigureras korrekt. Tidigare uppstod ett fel vid försök att konfigurera CSV-import via FTP eftersom FTP-tillägget saknas i PHP-paketet.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/39083>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/47b448e2>
* _AC-12869_: [Problem] Korrigerar felaktiga klasser som refereras i Magento-moduler.
   * _Korrigera anteckning_: Systemet refererar nu klasser i moduler korrekt, vilket ger en smidigare åtgärd och förhindrar krascher på grund av klasser som inte finns. Detta inkluderar en bugfix i indexer- och Creditmemo-modulerna och implementeringen av HttpGetActionInterface i klassen PrintAction. Tidigare ledde felaktiga klassreferenser till fel och potentiella systemkrascher, och vissa funktioner, till exempel filnamnet för creditmemo PDF-filer och omindexering av aktier, fungerade inte som förväntat.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/39126>
   * _Bidrag till_ GitHub-kod: <https://github.com/magento/magento2/pull/37784>
* _AC-12964_: Möjlighet att definiera område för CLI-kommando för dev:di:info
   * _Fix note_: Systemet tillåter nu utvecklare att definiera ett område för dev:di:info CLI-kommandot, vilket förbättrar utvecklings- och felsökningsprocessen. Tidigare kunde det här kommandot bara visa information för området GLOBAL.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/38758>
   * _Bidrag till_ GitHub-kod: <https://github.com/magento/magento2/pull/38759>
* _AC-13149_: [Problem] med att lägga till egenskapen isMultipleFiles i elementmallen för bildformulär
   * _Korrigera anteckning_: Den här korrigeringen förhindrar att knappen Bläddra för att hitta eller dra bilden hit försvinner när en bild läggs till i ett formulärelement för flera filer.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/39219>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/pull/36325>
* _AC-13279_: [Problem] Ta bort alla parametrar för marknadsföringsget för att minimera cachen
   * _Korrigera anteckning_: Systemet tar nu bort alla parametrar för marknadsföringsinhämtning för att optimera användningen av cache, och speglar logiken som används när lack används. Tidigare kunde de här parametrarna leda till cachebloggning och försämrade prestanda.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/39266>
   * _Bidrag till_ GitHub-kod: <https://github.com/magento/magento2/pull/39099>
* _AC-13345_: [Problem] [PHPDOC] Åtgärda dålig phpdoc Magento\Directory\Model\AllowedCountries::getAllowedCountries()
   * _Åtgärdsmeddelande_: PHPDoc för metoden AllowedCountries::getAllowedCountries() har korrigerats för att ge korrekt information, vilket förbättrar tydligheten och användbarheten av dokumentationen. Tidigare innehöll PHPDoc för denna metod felaktig information, vilket kunde leda till förvirring eller missbruk av metoden.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/39246>
   * _Bidrag till_ GitHub-kod: <https://github.com/magento/magento2/pull/39241>
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
* _AC-13725_: Magento\Framework\Filesystem\Driver\Http beror på orsaksfrasen OK
   * _Korrigera anteckning_: Tog bort fraskontrollen &quot;OK&quot; från Magento\Framework\Filesystem\Driver\Http::isExists
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/39546>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/pull/39558>
* _AC-13810_: Indexeraren för kundstödraster fungerar inte korrekt i schemaläge för uppdatering
   * _Korrigera anteckning_: Tidigare kundrutnät uppdaterades omedelbart, men efter att korrigeringen av kundrutnätet har uppdaterats efter att kron körts, men speglas inte direkt.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/1da9ba6f>
* _AC-6754_: typfel i en js-fil.
   * _Korrigera anteckning_: Systemet använder nu termen &quot;prenumeranter&quot; i JavaScript-filen korrekt, vilket garanterar att de relaterade funktionerna fungerar som de ska. Tidigare har ett typografiskt fel i JavaScript-filen resulterat i felaktig användning av termen &quot;subsctibers&quot;.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/36163>
   * _Bidrag till_ GitHub-kod: <https://github.com/magento/magento2/pull/36171>
* _AC-8353_: Problem: [Ta] bort förbjuden `@author` tagg
   * _Fix note_: Systemet följer nu kodningsstandarder genom att ta bort den förbjudna `@author` taggen från vissa moduler, vilket säkerställer renare och mer standardiserad kod. Tidigare fanns taggen `@author` i vissa moduler, vilket stred mot de etablerade kodningsstandarderna.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/37253>
   * _Bidrag till_ GitHub-kod: <https://github.com/magento/magento2/pull/37003>
* _AC-8356_: [Problem] Ta bort ej tillåten `@author` tagg från `Magento_Customer` (del 2)
   * _Fix note_: Systemet följer nu kodningsstandarden genom att ta bort den förbjudna `@author` taggen från vissa moduler, vilket säkerställer renare och mer standardiserad kod. Tidigare fanns taggen `@author` i vissa moduler, vilket stred mot de etablerade kodningsstandarderna.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/37250>
   * _Bidrag till_ GitHub-kod: <https://github.com/magento/magento2/pull/37000>
* _AC-8659_: Mellanslag i editorconfig-syntaxen bryter regeln för [{composer,auth}.json]
   * _Åtgärdningsmeddelande_: Systemet tillämpar nu korrekt ett 4-mellanslagsindrag på brevskrivar- och auth.json-filerna, efter en korrigering av ett syntaxfel i editorconfig. Tidigare, på grund av ett mellanslag i editorconfig-syntaxen, formaterades dessa filer felaktigt med ett indrag på 2 mellanslag.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/37394>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/pull/37395>
* _AC-8662_: [Problem] Förbättra felloggningen
   * _Korrigera anteckning_: Systemet hämtar och loggar nu både STDERR och STDOUT för cron-processer, vilket ger värdefull diagnostikinformation i scenarier där kron-processer misslyckas. Tidigare spelades inga felmeddelanden in i cron-processer och STDERR och STDOUT för cron-grupper som körs i separata processer gick förlorade.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/37453>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/pull/32690>
* _AC-8984_: [Issue] Lägger till fler färger i utdata för vissa kommandon för att konfigurera kli
   * _Korrigera anteckning_: Systemet lägger nu till fler färger i utdata från vissa kommandon i kommandoradsgränssnittet (CLI), vilket förbättrar läsbarheten och användarupplevelsen. Tidigare var utdata från dessa kommandon svårare att läsa på grund av brist på färgdifferentiering.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/29335>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/pull/29298>
* _AC-9630_: Uppgradering av Magento återställer allmänt/region/state_required när ett nytt land med nödvändig stat/region läggs till.
   * _Korrigera anteckning_: Systemet lägger nu bara till det ändrade landet i konfigurationen &quot;general/region/state_required&quot; när ett nytt land med obligatoriska lägen läggs till, vilket förhindrar eventuella avbrott i den anpassade koden som förutsätter att regionen är inaktiverad. Om du tidigare lade till ett nytt land med obligatoriska lägen återställs konfigurationen General/region/state_required till standardländer med ett obligatoriskt tillstånd, vilket kan göra att affären bryts.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/37796>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/pull/38076>
* _AC-9712_: Skillnad i mindre kompilering mellan php- och nodatumbibliotek (grunt) med komplicerade `calc`-uttryck
   * _Korrigera anteckning_: Korrigera skillnaden i mindre kompilering mellan php- och nodejs-biblioteket (grunt) efter uppdatering wikimedia/less.php:^5.x
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/37841>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/b34c0a75>
* _ACP2E-2692_: Felet &quot;Bastabell eller vy hittades inte&quot; inträffar när partiell indexering utförs
   * _Åtgärdat_: Partiell omindexering fungerar nu korrekt med stor ändringslogg vid sekundär db-anslutning
   * _Bidrag till_ GitHub-kod: <https://github.com/magento/magento2/commit/ba25af8a>
* _ACP2E-2844_: Problem efter uppgradering av MariaDB till 10.5.1 eller senare
   * _Åtgärdade felet_ när datetime-värden i en DB skulle konverteras till 0000-00 00:00:00 efter Mysql-uppgradering
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/a12063bd>
* _ACP2E-2855_: Typmatchningsfel i datajämförelse vid kontroll av om data har ändrats
   * _Korrigera anteckning_: Tidigare anropades objektet save varje gång utan dataändringar (för numeriska datafält, till exempel int/float/double). Den utlöser flaggan _hasDataChanges till true och anropar funktionen save. När den här korrigeringen har tillämpats anropas funktionen spara bara om data har ändrats. Datavärdet för int/float/double-check med värdet som skickas till funktionen och utför strikt typmatchning.
   * _Bidrag till_ GitHub-kod: <https://github.com/magento/magento2/commit/57a32313>
* _ACP2E-2959_: [Det går inte att använda molnimport] med katalogen var
   * _Korrigera anteckning_: Det går att importera produkten oavsett filnamn.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/3a7c4d17>
* _ACP2E-2966_: I iPad mini läses meny och header in som mobila, i stället läses de in som skrivbord.
   * _Korrigera anteckning_: Systemet hanterar nu enheter med en bredd på 768 px som stationära datorer, vilket säkerställer att meny och rubrik läses in korrekt. Tidigare behandlades enheter med bredden 768 px som mobila enheter, vilket gjorde att menyn och huvudet lästes in i en mobilvy.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/35b1b1da>, <https://github.com/magento/magento2-page-builder/commit/4d5db10a>
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
* _ACP2E-3537_: Motsvarande cachenyckelposter är inte tillgängliga i cachetaggar, vilket innebär att cacherensning inte fungerar korrekt
   * _Korrigera anteckning_: LUA-läget är nu aktiverat som standard för skräpinsamlaren i Redis-cachen för att förhindra konkurrensförhållanden
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/a52ff98f>
* _ACP2E-3681_: MAGENTO_DC_INDEXER_USE_APPLICATION_LOCK-värdet ignoreras
   * _Korrigera anteckning_: Efter korrigeringen behandlas en ENV-variabel som är inställd på &quot;false&quot; som bool false, inte som strängen &quot;false&quot;.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/982b1c42>

### Ramverk, GraphQL

* _AC-7976_: [Issue] Stöd för anpassade skalära typer för GraphQL-schema introducerades
   * _Korrigera anteckning_: Systemet har nu stöd för anpassade skalära typer för GraphQL-schema, vilket gör att utvecklare kan definiera anpassade skalära typer och implementeringar. Den här funktionen kan vara särskilt användbar för att uttrycka värden som kan behöva valideras, t.ex. HTML, e-post, URL:er, datum och mer avancerade fall som EAV-attribut. Tidigare hade systemet inte stöd för bearbetning av anpassade skalära typer i GraphQL.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/36877>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/pull/34651>, <https://github.com/magento/magento2/commit/0574ac23>

### Framework, UI Framework

* _ACP2E-3324_: Möjlighet att skriva över konfigurationsvärdet även om det är låst
   * _Korrigera anteckning_: Tidigare till den här korrigeringen kunde designkonfigurationen inte anges med kommandot bin/magento config:set och låsta värden kunde ändras genom att formuläret som visade dem ändrades. Efter korrigeringen av låsta värden som angetts från cli med —lock-env eller —lock-conf kan inte uppdateras längre.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/55615e61>

### GraphQL (på engelska)

* _AC-11729_: Magento_GraphQl kör rubriker även om rubrikvärdet inte godkänns i valideringen
   * _Korrigera anteckning_: Systemet ser nu till att huvudbearbetningen bara körs en gång och bara om huvudvärdet godkänns i valideringen, förbättrar säkerheten och förhindrar potentiella sårbarheter. Tidigare utfördes rubrikbearbetning även om rubrikvärdet inte godkändes vid valideringen, vilket ledde till potentiella sårbarheter och oväntade beteenden på grund av dubbelbearbetning av rubrikvärden.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/c8f87c25>
* _AC-8951_: Alternativen för fysiskt Giftcard har inte rätt sorteringsordning
   * _Korrigera anteckning_: Systemet sorterar nu alternativen för fysiska presentkortsprodukter korrekt när de efterfrågas via GraphQL, vilket ger en konsekvent återgivning med Luma-temat. Tidigare var sorteringsordningen felaktig enligt lumatema, vilket ledde till felaktig visning och ordning av alternativ som avsändarnamn, mottagarnamn och belopp.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/1bafc571>
* _AC-9157_: [GraphQL] Resolver-cachen ogiltigförklaras när en mellanlagringsuppdatering skapas/redigeras/flyttas/tas bort
   * _Åtgärdsmeddelande_: Systemet ser nu till att resolvercachen inte ogiltigförklaras när en mellanlagringsuppdatering skapas, redigeras, flyttas eller tas bort, utan endast när mellanlagringsuppdateringen tillämpas på entiteten. Tidigare ogiltigförklarades matchningscachen i förtid, även innan mellanlagringsuppdateringen tillämpades, vilket ledde till onödiga cacheogiltigförklaringar.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/0c53bbf7>
* _ACP2E-2642_: Snabb cachelagring har inte rensats för uppdatering av innehållsmellanlagring
   * _Korrigera anteckning_: Nu är svarscachen för GraphQL med PageBuilder-innehåll ogiltig när innehållsrelaterade entiteter för PageBuilder uppdateras.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/ba25af8a>
* _ACP2E-2653_: Inaktiverar navigering i lager - tar inte bort aggregering från Graphql
   * _Åtgärdsmeddelande_: Problemet har åtgärdats efter att ha tillämpat kontrollen när du begärde en produktsökning med kategoriaggregeringar via en GraphQL-fråga när administratörskonfigurationsinställningen för &quot;Katalog > Layered Navigation > Display Category Filter&quot; tillämpades.
   * _Bidrag till_ GitHub-kod: <https://github.com/magento/magento2/commit/12e071c3>
* _ACP2E-2928_: GraphQL Products-anrop som innehåller prisfiltret {from:&quot;0&quot;} returnerar inget resultat
   * _Korrigera anteckning_: Tidigare sökning med grafikprocessorer med filter för nollpriser returnerade inga resultat alls på grund av ett utlöst undantag. Nu returnerar sökningen det förväntade resultatet.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/c971859e>
* _ACP2E-2974_: Översättningar för kundreturattribut återspeglas inte i GraphQL API för respektive StoreView
   * _Korrigera anteckning_: Översättningar för kundreturattribut visas i GraphQL API för respektive StoreView.
Tidigare återspeglas inte kundreturattribut för respektive StoreView i GraphQL API.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/ec7e32a9>
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
* _ACP2E-3215_: [Cloud] Problem med användarautentisering och åtkomst med token på flera platser i konfigurationen för flera platser
   * _Korrigera anteckning_: GraphQl kundinformation och kundvagnsfrågor i installationsprogrammet för flera platser kontrollerar om kunden på en webbplats som inte är standard finns.
Tidigare arbetade frågan utan att kontrollera att kunden finns på en icke-standardwebbplats i konfigurationen av flera webbplatser.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/581b7ef1>
* _ACP2E-3253_: GraphQL cart itemsV2 pagination fungerar inte korrekt
   * _Åtgärda anteckning_: Problemet har åtgärdats genom att rätt värde för det aktuella sidargumentet har skickats i samlingsfrågan. Tidigare skickades fel värde för att ställa in den aktuella sidan, vilket orsakade problemet.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/8459b17d>
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
   * _Fix note_: Efter korrigeringen kommer ogiltiga graphql-förfrågningar inte att loggas in i exception.log-filen.
   * _Bidrag till_ GitHub-kod: <https://github.com/magento/magento2/commit/1984c61c>
* _ACP2E-3492_: [Molnproblem] med Graphql API
   * _Fix note_: Innan korrigeringen med hjälp av Graphql-applikationsservern returnerade kundadressbegäran inte de senaste data.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/3f12d152>
* _ACP2E-3505_: Den inaktiverade produkten visas fortfarande i relaterade, merförsäljning och korsförsäljningsobjekt i GPahQL-frågan
   * _Korrigera anteckning_: Graphql ger nu korrekt svar för inaktiverade produkter för återförsäljning, merförsäljning och korsförsäljning
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/d4de4726>
* _ACP2E-3647_: [CLOUD]: GraphQl-fel Internt serverfel placeOrder-mutation
   * _Korrigera anteckning_:&quot;placeOrder&quot;-mutationen med kupongkodinformation i begäran genererar inte längre ett internt felundantag. Ordningen har placerats korrekt. Tidigare misslyckades det med &quot;Internt serverfel&quot;.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/982b1c42>
* _LYNX-426_: Rabatt_percentage beräknas inte för paketprodukter med dynamiskt pris
   * _Korrigeringsanteckning_: Korrigering har lagts till för rabatt_procent för product.price_details och korrekt värde har inte angetts för paketprodukter med dynamiskt pris aktiverat och rabattkupong används.
* _LYNX-485_: Paketprodukter visar fortfarande&quot;IN_STOCK&quot; när en av de paketerade produkterna inte finns i lager
   * _Korrigera anteckning_: Problemet där programpaketet fortfarande innehöll&quot;IN_STOCK&quot; har åtgärdats även om en av de paketerade produkterna inte fanns i lager.
* _LYNX-486_: not_available_message och only_x_left_in_stock visar inte samma tillgängliga lager
   * _Fixnotering_: Löste problemet där not_available_message och only_x_left_in_stock visade inkonsekvent lagertillgänglighet
* _LYNX-488_: original_row_total fält returnerar fel värde
   * _Fixnotering_: Löste problemet med original_row_total-fältet, som returnerade felaktiga värden när anpassade alternativ valdes.
* _LYNX-503_: Grupperad produktminiatyrbild ska visas enligt konfigurationen.
   * _Åtgärda anteckning_: Löste problemet för att säkerställa att den grupperade produktminiatyren visas enligt konfigurationsinställningarna
* _LYNX-512_: original_item_price inkluderar inte rabatter
   * _Fix note_: Uppdaterad original_item_price för att inkludera rabatter.
* _LYNX-530_: Meddelandet Ej tillgängligt visar inte den tillgängliga lagerkvantiteten
   * _Åtgärda:_ Felmeddelandet och felkoden för AddProductsToCart-mutationen har åtgärdats så att de överensstämmer med meddelandekonfigurationen &quot;inte tillgänglig&quot;.
* _LYNX-532_: &quot;OUT_OF_STOCK&quot;-status återgår till Enkla med anpassade alternativprodukter med flervalsalternativ
   * _Åtgärdsmeddelande_: StockStatusProvider-resolvern i lagerpaketet har uppdaterats för att åtgärda stock_status för enkla produkter med anpassade alternativ.
* _LYNX-533_: Fel (GQL): cart.itemsV2.items.product.custom_attributesV2 returnerar ett serverfel
   * _Åtgärdsmeddelande_: Löste serverfelet som uppstod när en kundvagnsfråga inkluderade en produkts anpassade attribut genom att lägga till en produkt utan några anpassade attribut.
* _LYNX-536_: order/date_of_first_order returnerar alltid null
   * _Åtgärdsmeddelande_: Löste problemet där order > date_of_first_order alltid returnerade null.
* _LYNX-544_: Kunden får inte kunna annullera en delvis skickad order
   * _Åtgärdsmeddelande_: Validering har lagts till för att hindra kunder från att avbryta en delvis skickad beställning.
* _LYNX-548_: Felkoder för annullering av order baserat på felmeddelandet
   * _Fix:_ Felkoderna för annullering av order baseras nu på det specifika felmeddelandet.
* _LYNX-581_: Flytta tillbaka cookie-relaterade egendomar från privata till skyddade
   * _Korrigera anteckning_: Återställer synlighet för klasskonstruktoregenskaper från privat till skyddad
* _LYNX-600_: Öka den högsta standardkomplexiteten för GraphQL-frågor till 1 000
   * _Korrigera anteckning_: Ökade GraphQL-frågans standardkomplexitet från 300 till 1 000.
* _LYNX-620_: GQL - itemsV2 > Ursprunglig radsumma, priser returneras som 0,00 USD för hämtningsbar produkt med filalternativ som har separata priser.
   * _Korrigera anteckning_: Ett problem har korrigerats där hämtningsbara produkter med alternativ för separat länkköp aktiverade returnerade $0 för artiklarV2 > total ursprunglig radsumma, prisintervall returnerades som $0,00 för produkter med filalternativ med separata priser.
* _LYNX-772_: GraphQl-kompatibilitet för PHP-8.4-version
   * _Korrigera anteckning_: Korrigerade GraphQL-kompatibilitetsproblem med PHP 8.4 för flera matchare, vilket ger smidig funktionalitet. Uppdaterade filer som påverkas i modulerna CatalogRule, Customer, GiftMessage, GiftCard och GiftWrapping.

### GraphQL, Inventory / MSI

* _ACP2E-2607_: MergeCart-mutation genererar undantag när käll- och målvagnen har samma paketobjekt
   * _Korrigera anteckning_: -
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/c971859e>, <https://github.com/magento/inventory/commit/db0620da>

### GraphQL, Inventory/MSI, Performance

* _ACP2E-1716_: Platsen stängs efter uppgradering
   * _Korrigera anteckning_: Prestandan för hämtning av paketprodukter via GraphQl har förbättrats.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/ba25af8a>, <https://github.com/magento/inventory/commit/bdbf97ea>

### GraphQL, prestanda

* _AC-9569_: [Kundmatchardata för GraphQL Resolver] ogiltigförklaras inte vid import
   * _Åtgärd:_ GraphQL-kundmatchningscachen ogiltigförklaras nu som förväntat när en kund redigeras eller tas bort genom import. Tidigare ogiltigförklarades inte cachen och kunddata kunde redigeras eller tas bort under importen.
   * _Bidrag till_ GitHub-kod: <https://github.com/magento/magento2/commit/0574ac23>

### GraphQL, Sök

* _ACP2E-2809_: Det går inte att sortera GraphQL-produktlistor efter flera parametrar
   * _Korrigera anteckning_: Produktsortering efter flera fält i GraphQl fungerar nu enligt beskrivningen i dokumentationen
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/c971859e>
* _ACP2E-948_: Produktlista GraphQL-fråga begränsad till endast total_count 10 000 produkter
   * _Fix note_: Efter fixen är sökresultatet inte begränsat till 10000 produkter, det blir möjligt att få alla produkter som matchar sökkriterierna även om antalet är mer än 10000.
   * _Bidrag till_ GitHub-kod: <https://github.com/magento/magento2/commit/a4cf5e62>

### GraphQL, ramverk för test

* _ACP2E-3363_: Fel vid integreringstest av Magento\GraphQl\App\GraphQlCustomerMutationsTest.php
   * _Fix anteckning_: &#39;-
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/a4cf5e62>

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
* _ACP2E-2902_: Lägg till/uppdatera import på produkter som duplicerar anpassningsbara alternativ
   * _Åtgärdsmeddelande_: Problemet har lösts genom att tilldela rätt butik till produktalternativ under CSV-import av produktalternativ.
Tidigare tilldelad till administratörsarkivet i stället för deras respektive arkiv.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/3a7c4d17>
* _ACP2E-2990_: Kundens &quot;created_at&quot;-datum har inte konverterats för att lagra tidszonen vid export
   * _Korrigera anteckning_: Ett datumvärde för kolumnen &#39;created_at&#39; konverteras till rätt datumformat baserat på butikstidszonen i CSV-avsnittet för kundexport.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/3056e9cb>
* _ACP2E-3165_: [Cloud] Hämtar fel vid kontroll av data i importdata med CSV
   * _Fix note_: Det finns inget fel när du kontrollerar data under CSV-import. Tidigare var felmeddelandet som visades: &quot;Vi kan inte hitta en kund som matchar den här e-postadressen och webbplatskoden på rad(er): 1&quot; när du kontrollerar data i importavsnittet med CSV från administratören.
   * _Bidrag till_ GitHub-kod: <https://github.com/magento/magento2/commit/8459b17d>
* _ACP2E-3172_: Importknapp saknas
   * _Åtgärd:_ Lös problemet med att importknappen saknas efter att data har kontrollerats med korrekta och felaktiga poster i CSV-filen. Tidigare visades inte importknappen efter datakontroller med korrekta och felaktiga poster i CSV-filen.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/1819fe73>
* _ACP2E-3382_: Det går inte att importera den exporterade kundadressen
   * _Korrigera anteckning_: Importen av kundadressen fortsätter som förväntat. Tidigare godkändes inte valideringen av en kundadressimportfil om Dela kundkonton = Global, och det finns två webbplatser där standardwebbplatsen har en lista med begränsade länder och adressen som importeras är till en annan webbplats där tillåtna länder är olika
   * _Bidrag till_ GitHub-kod: <https://github.com/magento/magento2/commit/ec7e32a9>
* _ACP2E-3448_: [Molnfel] kvantitet i CSV-filen gav inte fel
   * _Korrigera anteckning_: Nu genereras valideringsfel för icke-numeriska värden i kvantitetskolumnen vid import av Stock-källor. Om du importerar Stock-källor med ett icke-numeriskt värde i kvantitetskolumnen hade kvantiteten angetts till 0.
   * _GitHub-kodbidrag_: <https://github.com/magento/inventory/commit/5b21b7af>
* _ACP2E-3455_: Felmeddelandet för dubblettnyckel som genereras när en produkt importeras är inte korrekt när URL-nyckeln redan tillhör en kategori
   * _Korrigera anteckning_: Rätt felmeddelande visas under produktimportkontrollen när kunden försökte importera produkten när produktens URL-nyckel redan tillhör en kategori.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/d4de4726>
* _ACP2E-3475_: Produktexport orsakar OOM även med 4G-minnesgräns
   * _Fix note_: Före den här korrigeringen misslyckades produktexporten om produktattributen hade tusentals alternativvärden även med 4G tillgängligt minne. Efter den här korrigeringen bör produktexporten slutföra exporten av csv-filen.
   * _Bidrag till_ GitHub-kod: <https://github.com/magento/magento2/commit/1984c61c>
* _ACP2E-3527_: [Cloud] Import Processes Interfering with Varann
   * _Korrigera anteckning_: Korrigerade meddelanden visas om samma administratörsanvändare utför två eller flera importåtgärder med samma användarsession.
   * _Bidrag till_ GitHub-kod: <https://github.com/magento/magento2/commit/d4de4726>

### Import/export, prestanda

* _ACP2E-3476_: [Importtiden för molnprodukter] har ökat avsevärt
   * _Fix note_: Före korrigeringen hade import av katalogprodukter med över 10K poster en betydande tidsförsämring. Efter korrigeringen körs importen av katalogprodukten i tid.
   * _Bidrag till_ GitHub-kod: <https://github.com/magento/magento2/commit/87d012e5>

### Installera och administrera

* _AC-13242_: Magento-uppgraderingen misslyckas på MariaDB 11.4 + 2.4.8-beta1
   * _Fix note_: Uppgraderingen bör ske utan några fel.
   * _Bidrag till_ GitHub-kod: <https://github.com/magento/magento2/commit/7b336d0a>
* _ACP2E-2102_: Ingen export VCL för lackknapp 7 i adminpanelen
   * _Fix note_: Knappen &quot;Exportera VCL för lack 7&quot; lades till i adminpanelen.
   * _Bidrag till_ GitHub-kod: <https://github.com/magento/magento2/commit/a4fbf702>

### Inventering / MSI

* _AC-10750_: Lageruppdateringen av den konfigurerbara produkten misslyckas när databasen använder prefix
   * _Åtgärdsmeddelande_: Systemet uppdaterar nu korrekt inventeringen av konfigurerbara produkter när databasen använder prefix, vilket förhindrar felmeddelanden och säkerställer att rätt kvantitet sparas. Tidigare uppstod ett fel när man försökte spara lagerkvantiteten för enkla produkter i en konfigurerbar produkt om databasen använde prefix.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/38045>
* _AC-11593_: Google Google API-nyckel fungerar inte när karta med attribut läggs till
   * _Korrigera anteckning_: Systemet har nu stöd för den senaste Google Maps API-versionen, 3.56, vilket gör att användare kan lägga till ett kartinnehållsblock från PageBuilder-menyn på scenen utan att några fel påträffas. Tidigare kunde användare inte lägga till ett kartinnehållsblock på grund av kompatibilitetsproblem med Google Maps API-versionen, vilket resulterade i ett felmeddelande om att något gick fel.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/0574ac23>
* _AC-13922_: Det går inte att skapa leverans för orderobjekt med flera källor och skadad SKU
   * _Korrigeringsanteckning_: Tidigare när blanktecken av misstag lades till i sku via databasen, uppstår ett fel på utleveranssidan som nu är fast och automatisk trimning betraktas som ett användarvänligt fel och ingen påverkan hittades. Leveransen skapades därför.
   * _GitHub-kodbidrag_: <https://github.com/magento/inventory/commit/c18eb5fa>
* _ACP2E-1411_: [Testa] Paketprodukter med 0 lager vid lagerframsidan
   * _Korrigera anteckning_: Paketprodukten visas inte på ytterligare webbplatser som använder extra lager.
* _ACP2E-2794_: [Cloud] Kritiskt problem med produktlistor med tomma utrymmen
   * _Korrigera anteckning_: Systemet visar nu produktlistor korrekt utan tomma utrymmen när produkter anges till Out of Stock, vilket ger en konsekvent och korrekt visning av tillgängliga produkter. Om du tidigare angav en produkt som &quot;Out of Stock&quot; skulle det resultera i att ett tomt utrymme visas i produktlistan, vilket stör layouten och kan förvirra kunderna.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/ea79f7dd>, <https://github.com/magento/inventory/commit/b59e48ca>
* _ACP2E-3335_: Det går inte att skicka beställningen när MSI-upphämtningsarkivet är aktiverat
   * _Korrigera anteckning_: Förbättrade lagerprestanda för att skapa leverans i händelse av många källor med hämtning i butik
   * _GitHub-kodbidrag_: <https://github.com/magento/inventory/commit/9f3e63d1>
* _ACP2E-3355_: Cron reindex misslyckas med att uppdatera produkttillgänglighet på klientsidan
   * _Korrigera anteckning_: Tidigare fanns produkterna inte i lager på klientsidan efter att bakgrundsorderstatusen uppdaterats via REST API. Efter att ha uppdaterat restorderstatusen via REST API visas nu produkterna som i lager.
   * _GitHub-kodbidrag_: <https://github.com/magento/inventory/commit/e6fe0aa7>
* _ACP2E-3357_: Det går inte att lägga till bilder i konfigurerbara när MSI är aktiverat.
   * _Korrigera anteckning_: Bildöverföring för konfigurerbar produkt kommer nu att fungera som förväntat när lagermodulen används. Tidigare fungerade inte bildöverföringen
   * _GitHub-kodbidrag_: <https://github.com/magento/inventory/commit/fdf409aa>
* _ACP2E-3470_: Problem med paketprodukt + MSI i Clean M2.4.7-p3
   * _Korrigera anteckning_: Tidigare kunde den enkla produkten inte sparas för lagerpaketprodukter efter duplicering med samma enkla produkt. När den här korrigeringen har tillämpats kan den enkla produkten sparas utan några undantag.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/39358>
   * _GitHub-kodbidrag_: <https://github.com/magento/inventory/commit/0208e433>

### Lager/MSI, Sök

* _ACP2E-3413_: Alla produkter indexeras med [ is_out_of_stock] = 1 när SKU inte är inställt som ett sökbart attribut
   * _Korrigera anteckning_: Efter korrigeringen är &quot;is_out_of_stock&quot; i katalogsökindexet korrekt, även om sku inte är sökbart.
   * _GitHub-kodbidrag_: <https://github.com/magento/inventory/commit/5b21b7af>

### Beställning

* _AC-10828_: Skärm med översikt över backend-order: Kvantitet som inte är synlig på orderartikelnivå
   * _Korrigera anteckning_: Systemet visar nu antalet underordnade objekt i kolumnen quantity på översiktsskärmen för backend-order. Detta gör att användarna kan spåra status för alla objekt i en ordning på rätt sätt. Tidigare visade kolumnen för kvantitet endast antalet artiklar som beställts, fakturerats och levererats, men inte antalet beställda artiklar.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/38252>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/pull/38320>
* _AC-10994_: [Problem] Fel lagrings-ID används i orderadressrenderaren
   * _Korrigera anteckning_: Systemet använder nu korrekt det arkiv-ID som är kopplat till en order när orderadressen återges, vilket säkerställer att adresserna formateras korrekt enligt deras respektive butik-ID. Tidigare använde systemet felaktigt det aktuella butiks-ID:t, vilket kunde leda till felaktig adressformatering om flera beställningsmejl från olika butiker behövde skickas.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/38412>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/pull/37932>
* _AC-11690_: Cachelagringsproblem med JoinProcessor
   * _Korrigera anteckning_: Systemet använder nu JoinProcessor korrekt för varje iteration, även med efterföljande anrop, för att säkerställa korrekt datahämtning. Tidigare hade JoinProcessor felaktigt markerats som använd i upprepade iterationer, vilket ledde till fel vid datahämtning.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/27504>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/pull/37550>
* _AC-11798_: [Utleverans] Leveranspriset skiljer sig åt i utskriven PDF
   * _Åtgärdsmeddelande_: Systemet visar nu fraktkostnader korrekt i utskrivna PDF-filer enligt inställningarna för momskonfiguration, vilket säkerställer konsekvens mellan visningssidan för försäljningsorderfakturan och den utskrivna fakturan. Tidigare var fraktkostnaden som visades i den utskrivna PDF-filen exklusive moms, oavsett inställningarna för momskonfiguration.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/38608>
   * _Bidrag till_ GitHub-kod: <https://github.com/magento/magento2/pull/38595>, <https://github.com/magento/magento2/commit/1bafc571>
* _AC-13839_: Ändra ordning med en borttagen överordnad konfigurerbar produkt
   * _Fix note_: Nu när du beställer om med den raderade produkten kommer systemet inte att visa ombeställningsknappen för att beställa om
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/39568>
   * _Bidrag till_ GitHub-kod: <https://github.com/magento/magento2/pull/39601>
* _AC-13924_: [Problem] Åtgärda felaktig egenskap \Magento\Sales\Model\Order\Email\Container\Template::$id
   * _Fix note_: Detta rättar den dåliga phpdoc för \Magento\Sales\Model\Order\Email\Container\Template::$id, faktiskt är $id typ int men i verkligheten är string.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/39151>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/pull/39150>
* _ACP2E-2622_: Det går inte att spara ändringar i telefonnummer i befintlig orderinformation
   * _Åtgärda anteckning_: Nu kan användaren lägga till det internationella prefixet 00 i telefonfältet för orderadress
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/38201>
   * _Bidrag till_ GitHub-kod: <https://github.com/magento/magento2/commit/12e071c3>
* _ACP2E-2734_: E-postmeddelanden kan inte skickas
   * _Åtgärdsmeddelande_: Systemet innehåller nu ett konfigurationsalternativ async_sending_attempts att ange antalet försök att skicka ett e-postmeddelande innan det stoppas, vilket förbättrar hanteringen av misslyckade e-postsändningar när &quot;Asynkron sändning&quot; är aktiverat. Tidigare, om ett e-postmeddelande inte skickades, försökte systemet kontinuerligt skicka det igen, vilket resulterade i en oändlig loop av felmeddelanden i systemloggen.
   * _Bidrag till_ GitHub-kod: <https://github.com/magento/magento2/commit/b2286ecf>
* _ACP2E-2756_: [Molnorderstatus] har ändrats till slutförd vid delvis återbetalning av en delvis levererad order
   * _Korrigera anteckning_: När du utfärdar en kreditnota ändras orderstatusen inte längre till&quot;slutförd&quot; om det finns artiklar som ännu inte har skickats.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/7e0e5582>
* _ACP2E-3002_: [CLOUD] Det går inte att inaktivera Skicka e-post från Admin UI som Dev Docs visar
   * _Fix note_: Systemet förhindrar nu korrekt att försäljningsmejl skickas när e-postkommunikation är inaktiverad. Dessa e-postmeddelanden skickas inte längre när e-postkommunikation har återaktiverats. Tidigare skickades säljmeddelanden som initierats medan e-postkommunikation inaktiverades när e-postkommunikation återaktiverades.
   * _Bidrag till_ GitHub-kod: <https://github.com/magento/magento2/commit/c8931218>
* _ACP2E-3045_: Beställningen har stängts utan att återbetalas helt
   * _Korrigera anteckning_: Systemet behåller nu orderstatusen korrekt som Bearbetning och fakturastatusen som Väntande när en order med en ej infångad betalning har en leverans skapad. Detta garanterar att beställningar endast markeras som&quot;Stängda&quot; efter att de har återbetalats helt. Om du tidigare skapade en leverans för en order med en väntande faktura skulle orderstatusen felaktigt ändras till Stängd.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/6a185204>
* _ACP2E-3311_: [Molnet] kan inte skapa order i admin i en butik om endast standardfaktureringsadressen inte har ställts in
   * _Fixnotering_: Nu relevant felmeddelande &quot;En kund med samma e-postadress finns redan på en associerad webbplats.&quot; visas om en kund inte har en standardfaktureringsadress och försöker skapa en order i en annan butik.
   * _Bidrag till_ GitHub-kod: <https://github.com/magento/magento2/commit/d75cff27>
* _ACP2E-3416_: Admin duplicerade förfrågningar om att placera order skickade
   * _Fixnotering_: Tidigare kunde knappen &quot;Skicka beställning&quot; i adminpanelen klickas på flera gånger eller aktiveras genom att upprepade gånger trycka på &quot;Enter&quot;-tangenten, vilket orsakade dubbletter eller orderinlämningar med fel. Nu kan du förhindra ytterligare åtgärder tills ordern har bearbetats fullständigt, så att bara en order skickas.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/5184c067>
* _ACP2E-3425_: Administratören kan fortfarande göra beställningar även utan betalningsmetod
   * _Korrigera anteckning_: Den betalningsmetod som valts tidigare behålls nu när betalningsmetoden visas igen i listan över tillgängliga betalningar.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/d50f6b5d>

### Order, betalningar

* _ACP2E-3233_: Administratören kan fortfarande göra beställningar även utan betalningsmetod
   * _Korrigera anteckning_: Tidigare kunde handlaren göra beställningar från adminpanelen utan att välja någon betalningsmetod. Nu måste handlaren ha en betalningsmetod för att kunna göra en beställning.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/fd5cf3af>

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
   * _Korrigera anteckning_: Korrigerade ett fel där cookien private_content_version returnerades i GraphQL-frågor, även när sessionscookien inaktiverades. Cookien inkluderas inte längre i GraphQL-svar när sessionen inaktiveras, som förväntat.
* _LYNX-380_: attributet is_available i CartItemInterface returnerar alltid false för konfigurerbara produkter
   * _Korrigeringsanteckning_: Ett problem har korrigerats där attributet is_available i CartItemInterface alltid returnerade false för konfigurerbara produkter i lager. Nu visas tillgängligheten som true när det är tillämpligt.
* _LYNX-382_: attributet is_available i CartItemInterface returnerar true även när det säljbara lagret är mindre än produktkvantiteten
   * _Åtgärdade felet där attributet is_available i CartItemInterface felaktigt returnerade true även om kvantiteten i kundvagnsartikeln överskred det säljbara lagret._
* _LYNX-399_: Platshållarminiatyrbilder returneras när en enkel produkt läggs till i varukorgen i en grupperad produkt
   * _Åtgärdade ett fel_ där en enkel produkt (en del av en grupperad produkt) i vagnen returnerade en platshållarminiatyrbild, även när produkten hade en tilldelad bild.
Korrigeringsinformation:
・ Miniatyrbilden av produkten visar nu korrekt den tilldelade bilden om den är tillgänglig.
・ Miniatyrbildsmarkeringen respekterar administratörskonfigurationen under:
Stores > Configuration > Sales > Checkout > Shopping Cart > Group Product Image.
På så sätt får du en konsekvent miniatyrbildsfunktion för grupperade produkter baserat på butiksinställningarna.
* _LYNX-400_: Kundens anpassade alternativattribut fungerar inte med heltalsvärden
   * _Korrigera anteckning_: Ett problem har korrigerats där kundens anpassade alternativattribut inte fungerade när det returnerade värdet var ett heltal. Anpassade alternativ hanterar nu korrekt och returnerar heltalsvärden som förväntat.
* _LYNX-402_: Internt serverfel vid försök att hämta priceDetails för paketprodukter med dynamiskt pris
   * _Korrigera anteckning_: Ett problem har korrigerats där frågan price_details för paketprodukter med dynamisk prissättning via GraphQL resulterade i ett internt serverfel. Den här förbättringen säkerställer stabila kundvagnsfrågor när du arbetar med paketprodukter som konfigurerats med dynamisk prissättning.
* _LYNX-403_: only_x_left_in_stock returnerar alltid 0 för konfigurerbara produkter
   * _Korrigera anteckning_: Ett problem har åtgärdats där attributet only_x_left_in_stock alltid returnerade 0 för konfigurerbara produkter när det lades till med den överordnade SKU:n med alternativ.
Fix Detaljer:
• Det only_x_left_in_stock värdet återspeglar nu korrekt lagret för den valda underordnade varianten istället för den överordnade SKU:n.
• Detta säkerställer att lagernivåer visas korrekt för konfigurerbara produktvarianter i varukorgen och på produktsidorna.
* _LYNX-411_: GraphQL-frågan returnerar inte korrekt beräknat normalpris för anpassningsbara produkter
   * _Korrigeringsanteckning_: Ett problem har korrigerats där GraphQL inte returnerade korrekt beräknat normalpris för anpassningsbara produkter. Frågan innehåller nu korrekt det beräknade ordinarie priset med anpassningsbara värden (t.ex. $125) i egenskapen prices, som återspeglar både baspriset och eventuella ytterligare anpassningskostnader.
* _LYNX-412_: AppliedTaxes via EstimatedTotals kvarstår med uppdaterade mutationer
   * _Korrigera anteckning_: Korrigerade ett problem med mutationen EstimatedTotals, där pålagda skatter bestod i en vagn även efter att regionen eller postkoden uppdaterats. Mättnaden uppdaterar nu korrekt de pålagda skatterna när värden mellan region och postnummer ändras, vilket säkerställer att endast rätt momsregel tillämpas baserat på aktuella kundvagnsdata.
* _LYNX-420_: attributet is_available i CartItemInterface returnerar true även när det säljbara lagret är mindre än produktkvantiteten
   * _Korrigeringsanteckning_: Ett problem har korrigerats där attributet is_available i CartItemInterface felaktigt returnerade true även om det säljbara lagret var lägre än den begärda produktkvantiteten. Fältet is_available returnerar nu korrekt false när produktens kvantitet överskrider det tillgängliga lagret.
* _LYNX-425_: Normalpris för produkt med 12 decimaler och fel värde
   * _Korrigera anteckning_: Korrigerade ett fel där GraphQL-sökvägarna regular_price i product.price_range.maximum_price och minimum_price inte matchade katalogpriset när flera skattesatser tillämpades. I Cart Summary visas nu katalogpriset enhetligt för alla momskonfigurationer, vilket ger korrekt enhetspris, beräkning av totalkostnader och rabattkontroller.
* _LYNX-430_: GraphQL-serverfel i varukorgen med produkt som inte ingår i paketet
   * _Åtgärdade ett fel_ där GraphQL returnerade ett internt serverfel när en kundvagn som innehåller en paketerad produkt med ett objekt som inte finns i lager hämtades, särskilt när frågan innehöll egenskapen itemsV2. GraphQL returnerar nu korrekt en lista med objekt med relevanta felmeddelanden som är kopplade till den paketerade produktposten, som förväntat.
* _LYNX-441_: Det går inte att skapa en adress med anpassade attribut
   * _Åtgärdat_: Åtgärdade ett problem med mutationen createCustomerAddress som förhindrade skapandet av adresser med nödvändiga anpassade attribut. Mutationen hanterar nu anpassade adressattribut korrekt när lämplig nyttolast tillhandahålls.
* _LYNX-447_: GraphQL-serverfel i kundvagnen med only_x_left_in_stock på den medföljande produkten
   * _Åtgärdat_: Åtgärdade ett problem där hämtning av en kundvagn som innehöll en paketerad produkt med fältet only_x_left_in_stock i GraphQL-frågan resulterade i ett internt serverfel. GraphQL returnerar nu korrekt flyttal eller null för det only_x_left_in_stock fältet utan fel.
* _LYNX-464_: GraphQL-fel vid borttagning av andra produkter med otillräcklig konfigurerbar produkt i varukorgen
   * _Åtgärdat_: Åtgärdade ett problem där försök att ta bort produkter i lager från varukorgen resulterade i ett GraphQL-fel av typen &quot;Den begärda kvantiteten är inte tillgänglig&quot; om varukorgen också innehöll konfigurerbara produkter med otillräckligt lager. Borttagningen fungerar nu som förväntat utan att utlösa fel.
* _LYNX-469_: Det går inte att lägga till produkter på grund av att SKU i mutationen är skiftlägeskänsligt
   * _Åtgärdsmeddelande_: Löste ett problem där addProductsToCart-mutationen returnerade ett &quot;PRODUCT_NOT_FOUND&quot;-fel vid användning av SKU:er med olika höljen. Mutationen hanterar nu SKU:er skiftlägesokänsligt, vilket säkerställer konsekvens med katalogtjänstfrågor och PDP-beteende.
* _LYNX-603_: Product attribute > trademark short form ™ returneras som ™
   * _Korrigera anteckning_: Problem med teckenkodning med produktnamnet för GraphQL API har åtgärdats
* _LYNX-619_: updateCustomerEmail - mutationsproblem
   * _Korrigera anteckning_: Ett problem med updateCustomerEmail-mutationen har åtgärdats där kunder utan nödvändiga anpassade attribut (som lagts till efter att kontot skapats) inte kunde uppdatera sin e-post.
* _LYNX-626_: Mutation setShippingAddressesOnCart genererar fel när pickup_location_code används
   * _Korrigeringsanteckning_: Ett problem har korrigerats där mutationen setShippingAddressesOnCart returnerade ett fel när koden pickup_location_code användes utan att kundens_address_id eller adress angavs. Mmutationen gör att det nu går att ange en leveransadress med bara koden pickup_location_code.
* _LYNX-637_: Storefront-kompatibilitet - Uppdatera logik för att hämta tabellnamn med prefix och andra mindre förbättringar
   * _Korrigera anteckning_: Logiken för att hämta tabellnamnet med prefixet (relaterat till SCP-ändringar) har uppdaterats.
* _LYNX-643_: Det går inte att spara i adressboken när du använder setBillingAddressOnCart GQL:s fält same_as_shipping
   * _Korrigera anteckning_: Ett problem har korrigerats där leveransadressen inte sparades i kundens adressbok när GraphQL-mutationen setBillingAddressOnCart användes med värdet true för samma_as_shipping-fält. Leveransadressen lagras som förväntat.
* _LYNX-650_: Standardisera order_id i mutationer
   * _Korrigera anteckning_: Standardiserade indata för order_id i mutationer och uppdaterade e-postmallen för bekräftelse av orderavslutning så att ett inkrement-ID visas i stället för order-ID.
* _LYNX-651_: CustomerOrder visar inte orderkommentarerna
   * _Korrigera anteckning_: Ett problem med CustomerOrder har åtgärdats med orderkommentarer i GraphQL-frågor för gäst- och kundorder.
* _LYNX-652_: original_item_price får inte innehålla någon rabatt
   * _Korrigera anteckning_: Logiken för original_item_price i GraphQL Cart Item-priser har uppdaterats för att exkludera rabatter.
* _LYNX-681_: Paketprodukter visar fortfarande&quot;IN_STOCK&quot; när en av de paketerade produkterna inte finns i lager
   * _Åtgärdat_: Löste ett problem där product.stock_status för paketprodukter fortfarande visade &quot;IN_STOCK&quot; även när en av de medföljande artiklarna var slut i lager.
* _LYNX-686_: kundfråga returnerar internt serverfel om det finns ett värde för det borttagna anpassade attributet för en kund
   * _Åtgärdad anteckning_: Åtgärdade problemet där kundfrågan returnerade ett internt serverfel när ett borttaget anpassat attribut fortfarande hade ett lagrat värde. Nu returneras ett korrekt felmeddelande om ett icke-existerande attribut begärs. Nödvändig cache ogiltigförklaras när kundens anpassade attribut tas bort.
* _LYNX-687_: Åtgärdsparameter för bekräftelselänkar för retur och annullering
   * _Korrigera anteckning_: Åtgärdsparameter har lagts till för e-postlänkar för retur och annullering av bekräftelsemeddelanden
* _LYNX-689_: Användarens bekräftelse-URL för gäst omdirigeras till orderstatussidan eftersom den saknar orderRef
   * _Åtgärdsmeddelande_: Parametern orderRef har lagts till i länken i e-postmeddelandet med bekräftelsen av avbokning av gästorder
* _LYNX-699_: Det går inte att returnera null för det icke-nullbara fältet &quot;TaxItem.title&quot; i placeOrder GQL
   * _Åtgärdad anteckning_: Åtgärdade ett problem där placeOrder-mutationen misslyckades med ett internt serverfel på grund av ett null-värde för det icke-nullbara fältet TaxItem.title. Nu returnerar fältet alltid ett giltigt värde, vilket säkerställer en lyckad orderplacering.
* _LYNX-702_: EstimateTotals: Rabatter är null för virtuella produkttyper
   * _Åtgärdsmeddelande_: Löste problemet med att estimateTotals-mutationen returnerade null för rabatter när en rabattkod tillämpas på en varukorg som innehåller virtuella produkter.
* _LYNX-703_: Paketprodukten returnerar inte rätt rabatt i procent och belopp
   * _Åtgärd_: Nya egenskaper &quot;catalog_discount&quot; och &quot;row_catalog_discount&quot; har införts för katalogartikelpriser för att visa korrekta rabattbelopp och procentsatser på både rad- och enskild artikelnivå.
* _LYNX-714_: Presentmeddelandekonfiguration på produktnivå
   * _Korrigera anteckning_: Korrigerade ett problem där presentmeddelanden inte tillämpades på produktnivån när de var globalt inaktiverade. Nu, om presentmeddelanden är aktiverade för en specifik produkt, kan de läggas till med hjälp av updateCartItems-mutationen och kommer att sparas och återspeglas korrekt.
* _LYNX-757_: cart.rules frågereturfel istället för tom matris om inga aktiva kundvagnsregler tillämpas
   * _Åtgärdad anteckning_: Åtgärdade cart.rules-frågan för att returnera en tom matris i stället för ett fel när inga aktiva kundvagnsregler tillämpas.
* _LYNX-778_: GraphQL-anrop med OPTIONS-metoden returnerar 500-svarskod när paketet adobe-commerce/storefront-compatibility installeras
   * _Åtgärdat_: Korrigerade ett problem där GraphQL-anrop med OPTIONS-metoden returnerade ett 500 internt serverfel när paketet adobe-commerce/storefront-compatibility installerades. Slutpunkten returnerar nu korrekt ett 200/204-svar som förväntat.

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
   * _Bidrag till_ GitHub-kod: <https://github.com/magento/magento2/commit/0611e750>
* _AC-12731_: CSP-problem i kombination med dev/css/use_css_critical_path
   * _Åtgärdsmeddelande_: Systemet läser nu in CSS-filer asynkront på utcheckningssidor, även när inställningen &quot;dev/css/use_css_critical_path&quot; är aktiverad, vilket säkerställer att dessa sidor återges med rätt CSS-stilar. Tidigare hindrade en begränsad CSP (Content Security Policy) infogad JavaScript från att köras, vilket resulterade i att CSS-filer inte lästes in som förväntat.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/39020>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/pull/39040>
* _AC-13398_: Det går inte att generera gränssnittsmetoden korrekt med den virtuella typen för att konfigurera plugin-programmet i kommandot :di:kompilera
   * _Korrigera anteckning_: Systemet genererar nu korrekt spärrmetoder när en virtuell typ används för att konfigurera ett plugin-program, vilket ger konsekventa resultat oavsett om det är förkompilerat eller körtidskompilerat. Tidigare genererade systemet felaktiga resultat vid förkompilering jämfört med körtidskompilering.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/33980>
   * _Bidrag till_ GitHub-kod: <https://github.com/magento/magento2/pull/38141>
* _AVS2E-3631_: Enhetstester för Adobe Commerce 2.4.7-p3 misslyckas
   * _Korrigera anteckning_: Inga versionsinformation krävs.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/982b1c42>

### Betalnings-/betalningsmetoder, beställning

* _AC-13699_: Information om det pappersbaserade betalningsflödet Kreditkort som sparats för senare bruk visas inte på sidan med den lagrade betalningsmetoden
   * _Korrigeringsanteckning_: Information om det tidigare pappersbaserade betalningsflödet Kreditkortsinformation som sparats för senare bruk visades inte på den lagrade betalningsmetodsidan, som nu har fast kreditkortsinformation, visas på den lagrade betalningsmetoden.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/96dec499>

### Betalningar

* _AC-13414_: Betalningen för kreditkort (Payflow Link) fungerar inte
   * _Korrigera anteckning_: Tidigare hämtningsfel (betalningen nekades) när beställningen med kreditkort skulle placeras efter att korrigeringsordern har placerats.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/a68324bc>
* _ACP2E-2841_: Betalningsflödet skapar en ny transaktion varje gång vi klickar på knappen Hämta på skärmen Visa transaktion
   * _Korrigera anteckning_: Systemet hämtar nu transaktionsinformation korrekt utan att skapa en ny betalningstransaktion varje gång knappen Hämta visas på skärmen Visa transaktion. Tidigare skapades en ny betalningstransaktion felaktigt för en beställning som redan hade betalats när du klickade på knappen Hämta.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/b2286ecf>
* _ACP2E-3028_: Senare betalningsmeddelande visas inte i PDP för kanadensiskt betalningsmottagarkonto
   * _Korrigera anteckning_: Systemet visar nu korrekt PayLater-meddelandet för kanadensiska PayPal-handelskonton på produktinformationssidan (PDP) när köparens land kan fastställas från faktureringsadressen eller leveransen för kontot. Tidigare visades inte PayLater-meddelandet på grund av en saknad parameter, vilket resulterade i ett fel i webbläsarkonsolen.
   * _Bidrag till_ GitHub-kod: <https://github.com/magento/magento2/commit/6a185204>
* _ACP2E-3143_: Återbetalning av PayPal-order resulterar i dubbel kreditnota
   * _Åtgärdat_: Åtgärdat samtidighetsproblem med IPN-skapade kreditnotor för PayPal-betalningstjänsten.
   * _Bidrag till_ GitHub-kod: <https://github.com/magento/magento2/commit/d01ee51e>
* _ACP2E-3163_: Regeln för kundvagnspris fungerar inte för PayPal
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
* _AC-12000_: [Utgåva] Kodrensning och lägg till nytt kritiskt huvudblock och flytta kritiska CSS före resurser
   * _Korrigera anteckning_: Systemet innehåller nu ett nytt kritiskt huvudblock och flyttar kritisk CSS före resurser, vilket möjliggör mer anpassning och prestandaoptimering i förgrunden. Tidigare placerades inte den kritiska CSS-koden före resurserna, vilket begränsade möjligheterna till anpassning och optimering.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/38748>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/pull/35580>
* _AC-12176_: Temakompileringen avbryts när mysql-värden innehåller portinformation
   * _Korrigera anteckning_: Systemet hanterar nu konfigurationen för MySQL-värden som innehåller portinformation, vilket säkerställer att temat kompileras. Tidigare misslyckades temakompileringen om konfigurationen MySQL-värd i databasanslutningen innehöll portinformation.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/38799>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/pull/38842>
* _AC-13471_: Stöd för Symfonys CommandLoaderInterface i Magento CLI
   * _Korrigera anteckning_: Den här ändringen minskar initieringstiden för Magento CLI-appen genom att tillåta fördröjd initiering av kommandon tills de behövs.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/29266>
   * _Bidrag till_ GitHub-kod: <https://github.com/magento/magento2/pull/29355>
* _ACP2E-2494_: Prestandaproblem vid inläsning av produktattribut i kundvagnsregler
   * _Fix note_: Förbättrad frågeprestanda för försäljningsregler - från cirka 150 ms till ensiffriga ms.
   * _Bidrag till_ GitHub-kod: <https://github.com/magento/magento2/commit/ba25af8a>
* _ACP2E-2673_: Prestanda för partiell prisindexering
   * _Korrigera anteckning_: Prestandan för partiell prisindexering har förbättrats genom att några av de borttagningsfrågor som används i indexeringsprocessen har optimerats.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/ba25af8a>
* _ACP2E-2850_: Beställningen avvisas vid konfiguration med flera butiker när du använder Async-orderbehandling + Regler och villkor
   * _Korrigera anteckning_: Beställningar från icke-standardwebbplatser med aktiverade villkor bearbetas nu.
Innan de avvisades automatiskt.
   * _Bidrag till_ GitHub-kod: <https://github.com/magento/magento2/commit/57a32313>
* _ACP2E-2910_: API-anrop för orderåterställning tar lång tid att köra
   * _Korrigera anteckning_: Systemet kör nu anropet till API:t för orderåterställning inom en rimlig tidsram, vilket förbättrar prestanda när ett stort antal order hämtas. Tidigare tog det lång tid att köra anropet till API:t för orderraster, vilket orsakade fördröjningar när ett stort antal order hämtades.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/001e5188>

### Priser

* _AC-11810_: Pris saknas för Magento2.4.6-p4 Order API Simple Item
   * _Korrigera anteckning_: Systemet visar nu priset på enkla produkter korrekt när det efterfrågas via Order API, vilket ger korrekt datarepresentation. Tidigare visades priset på enkla produkter felaktigt som noll i API-svaret.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/38603>
* _AC-13855_: Löpande avrundningsfel i katalogregel
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/276e0acd>

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
* _AC-13173_: [Problem] Korrigeringstyp i PHPDoc-block
   * _Korrigera anteckning_: Systemet tar nu bort en okänd refererad variabel i PHPDoc korrekt för $helper-variabeldeklarationen, vilket gör koden tydligare och exaktare. Tidigare orsakade den här okända refererade variabeln i PHPDoc förvirring och potentiella fel i koden.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/38961>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/pull/38940>
* _AC-13423_: [Problem] Åtgärdat brutet paket och hämtningsbar layout för produktsidor i Magento >= 2.4.7
   * _Korrigera anteckning_: Layouten för programpaket och hämtningsbara produktsidor har korrigerats, vilket ger en konsekvent och korrekt visning på alla enheter. Tidigare hade dessa sidor layoutproblem på grund av en omorganisering av produktinformationsmediablocket.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/39403>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/6cfb9b6b>
* _AC-5969_: AlertProcessor - Argument #2 ($storeId) måste vara av typen int, sträng angiven
   * _Korrigera anteckning_: Systemet utlöser nu produktvarningsmeddelanden korrekt genom att se till att butiksidentifieraren har rätt datatyp. Tidigare skickades inga produktvarningsmeddelanden på grund av ett typmatchningsfel i butiksidentifieraren.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/35602>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/0574ac23>
* _ACP2E-2944_: [Cloud] funktionen addFilterToMap fungerar inte för vissa kolumner
   * _Korrigera anteckning_: Nu kan den anpassade modulen användas i orderstödrastret. Tidigare inträffade fel när en anpassad modul användes.
   * _Bidrag till_ GitHub-kod: <https://github.com/magento/magento2/commit/3a7c4d17>

### Befordran

* _ACP2E-2602_: Kundattributet är inte synligt när du skapar konto från inbjudan
   * _Korrigera anteckning_: Kundattribut är tillgängliga när du skapar konto från inbjudan.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/39d54c2d>
* _ACP2E-2627_: Kupongkod med en kuponggräns frisläppas inte för betalning. Orderannullering misslyckades.
   * _Korrigera anteckning_: Systemet uppdaterar nu omedelbart kuponganvändning när en order skapas eller annulleras, och lägger till regelanvändning i en kö för att förhindra potentiella lås. Detta garanterar att en kupongkod med en kuponggräns för användning per kupong frisläpps och kan återanvändas om en order annulleras på grund av en misslyckad betalning. Tidigare släppte systemet inte kupongkoden för återanvändning i sådana fall, vilket resulterade i ett felmeddelande om att kupongkoden inte var giltig.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/c971859e>
* _ACP2E-2811_: [Cloud] Omindexering av katalogregelns produktindexerare ger SQLSTATE [HY000]: Allmänt fel: 2006 MySQL-servern har försvunnit.
   * _Korrigera anteckning_: Systemet hanterar nu korrekt anpassat batchantal i di.xml för Magento\CatalogRule\Model\Indexer\IndexBuilder, vilket förhindrar SQL-fel som &quot;Allmänt fel: 2006 MySQL-servern har försvunnit&quot; under omindexeringen av katalogregelns produktindexerare på grund av felaktig batchstorlek för stora kataloger
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/b2286ecf>
* _ACP2E-3139_: Förs.regel med rabattkvantitetssteg (Buy X)-attribut leder till att andra regler inte tillämpas
   * _Korrigera anteckning_: I kundvagnsprisregeln avbryts inte tidigare tillämpade regler om kvantiteten av produkten i vagnen inte räcker för att regeln ska tillämpas.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/d01ee51e>
* _ACP2E-3332_: Utfärda försäljningsregler med fast beloppsrabatt och &quot;maximal mängdrabatt används för&quot;
   * _Korrigera anteckning_: Ett problem med rabatt på kundvagnsregler har korrigerats när rabatt på fast belopp har konfigurerats för en begränsad produktkvantitet är vagnen. Tidigare användes värdet för maximal mängdrabatt till för att beräkna den aktuella artikelns pris i kundvagnen, inte bara för att beräkna regelns rabatt.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/581b7ef1>
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
* _ACP2E-3472_: [CLOUD] Leveransberäkningen överväger inte kundvagnsregeln
   * _Korrigera anteckning_: Före korrigeringen tillämpades inte en vagnsregel med regionsvillkor konsekvent. Efter korrigeringen tillämpas kundvagnsregler med regionvillkor korrekt.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/d4de4726>
* _AVS2E-3491_: Det gick inte att skapa kundvillkor för kundvagnsregel för faktura.
   * _Korrigera anteckning_: Rabatten på paketprodukt med dynamiskt pris visas nu korrekt i fakturan. Tidigare återspeglades inte rabatten på fakturan.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/3f12d152>
* _ACP2E-3498_: Felaktigt rabattvärde när flera kundprisregler tillämpas samtidigt med rabatterade/specialprissatta produkter
   * _Åtgärdsmeddelande_: Före korrigeringen tillämpades inte reglerna för fast belopp för hela kundvagnen korrekt om fler än en tillämpades. Nu tillämpas reglerna för rabattvagn med fast belopp korrekt.
   * _Bidrag till_ GitHub-kod: <https://github.com/magento/magento2/commit/1984c61c>

### Optimering och utveckling

* _AC-11907_: Att lägga till URL-omskrivningar med accent orsakar oändlig inläsning
   * _Fix note_: Systemet skapar nu framgångsrikt och fungerar URL-omskrivningar med accenter, vilket förhindrar oändlig laddning under sparprocessen. Tidigare orsakade tillägg av en URL-omskrivning med en accent ett oändligt inläsningsproblem.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/38692>
   * _Bidrag till_ GitHub-kod: <https://github.com/magento/magento2/commit/44cef3a9>
* _ACP2E-2641_: Multi Store Fel kategori url-omskrivning för tredje nivåns kategori
   * _Åtgärdsmeddelande_: Generera korrekta URL-omskrivningar för barn med förälder med anpassad URL-nyckel
   * _Bidrag till_ GitHub-kod: <https://github.com/magento/magento2/commit/ea79f7dd>
* _ACP2E-2770_: Dubbelbyte-tecken (specialtecken) i fältet Produktnamn blockerar produktskapande i backend
   * _Fix note_: En ny inställning har lagts till som gör att du kan tillämpa translitterering på produkt-URL eller inte. Inställningen är tillgänglig här: Lagrar > Konfiguration > Katalog > Katalog > Sökmotoroptimering: &quot;Tillämpa translitterering för produkt-URL&quot;
   * _Bidrag till_ GitHub-kod: <https://github.com/magento/magento2/commit/b2286ecf>
* _ACP2E-3383_: Felaktigt skapande av url_rewrite-poster med flera butiker i en butiksgrupp
   * _Korrigera anteckning_: Innan korrigeringen kunde du bara generera URL-skrivningar på webbplatsnivå när du redigerade en produkt. Med korrigeringen introducerades en ny inställning (Lager > Konfiguration > Katalog > Katalog > Sökmotoroptimering, Återskrivningsomfång för produkt-URL med alternativen Store-vy, Webbplats) som gör att du kan generera URL-omskrivningar på butiksvy- eller webbplatsnivå.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/2d627301>

### Sök

* _AC-13053_: Hämtar &quot;Ange ett sökord och försök igen.&quot; fel på avancerad söksida i storefront i 2.4.8 beta1
   * _Korrigera anteckning_: Systemet visar nu sökresultaten korrekt på sidan Avancerad sökning när ett produktattribut är inställt på Nej. Om du tidigare angav ett produktattribut som &quot;Nej&quot; och gjorde en sökning, skulle ett felmeddelande visas: &quot;Ange ett sökord och försök igen&quot;.
   * _Bidrag till_ GitHub-kod: <https://github.com/magento/magento2/commit/3ea26621>
* _AC-13721_: magento/module-open-search beror på en obefintlig opensearch-php-gren
   * _Bidrag till_ GitHub-kod: <https://github.com/magento/magento2/commit/05dc0bbf>
* _ACP2E-3362_: tabellen search_query har stor betydelse för inläsningstidens förskjutning när den är mycket stor
   * _Fix note_: Förbättrad laddningstid för söklistningssidan. Före korrigeringen fördröjdes söklistningssidan på grund av en icke-optimerad fråga.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/55615e61>

### Säkerhet

* _AC-11855_: [Problem] Popup-meny för CSP-teckensnittsstöd saknas
   * _Korrigera anteckning_: Systemet tillåter nu inläsning av teckensnittet https://www.paypalobjects.com/webstatic/mktg/2014design/font/PP-Sans/PayPalSansBig-Medium.woff&#39; utan att bryta mot direktivet Content Security Policy, vilket säkerställer att popup-menyn Paylater visas korrekt. Tidigare nekades teckensnittet att läsas in på grund av en överträdelse av direktivet Content Security Policy, vilket orsakade visningsproblem med popup-menyn Paylater.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/38624>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/pull/37401>
* _AC-12035_: [Problem] Uppdatera js.js DOM-text omtolkad som HTML
   * _Korrigera anteckning_: Genom att använda innerText undviker den risken för HTML-injektion, eftersom dessa egenskaper automatiskt utesluter alla HTML-specialtecken i den angivna texten. Med den här korrigeringen kan du förebygga XSS-problem (cross-site scripting) genom att behandla indata som oformaterad text i stället för att tolka HTML.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/38767>
* _ACP2E-3273_: ReCaptcha V2 visas felaktigt vid utcheckning för tyska språk
   * _Korrigera anteckning_: Tidigare visades reaptcha från undere-postadressen i utcheckningen som oformaterad för språk med långa ord, som german. Därefter ser reaptcha ut på samma sätt som alla recaptcha-element från resten av områdena.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/7377de59>
* _ACP2E-3300_: Captcha vid administratörsinloggning kräver inte interaktion för vissa användare
   * _Åtgärdsmeddelande_: ReCaptcha för administratörsinloggning valideras som förväntat
   * _GitHub-kodbidrag_: <https://github.com/magento/security-package/commit/8f64ab3c>

### Frakt

* _AC-10757_: [Problem] Korrigerat stavfel i tracking.phtml - JS-funktioner med namnet &quot;currier&quot; har ändrats till &quot;operator&quot;
   * _Korrigera anteckning_: Systemet använder nu termen &quot;operator&quot; i stället för den felstavade &quot;currier&quot; i de JavaScript-hanterarfunktioner som används i orderspårningsmallen, vilket ger korrekt funktionsnamn och kodklarhet. Tidigare användes den felstavade termen&quot;currier&quot;, vilket kan leda till förvirring och inkonsekvenser i kodbasen.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/34523>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/pull/33414>
* _AC-11938_: UPS REST &quot;En sändning kan inte ha en KGS/IN eller LBS/CM eller OZS/CM som måttenhet&quot;
   * _Fix note_: Se till att UPS-priserna ska synas i kassan och kundvagnen.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/38618>
   * _Bidrag till_ GitHub-kod: <https://github.com/magento/magento2/commit/493e01f5>
* _AC-13172_: [Problem] Korrekt stavning av variabler för kundadress
   * _Åtgärdsmeddelande_: Systemet stavar nu variabler för kundadresser korrekt, vilket säkerställer korrekt visning i kontoområdet i frontend. Tidigare kunde felaktig stavning av dessa variabler leda till fel under granskningar av lokal kod.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/32817>
   * _Bidrag till_ GitHub-kod: <https://github.com/magento/magento2/pull/32815>
* _ACP2E-2738_: Spårningsfönster visar fel förväntat leveransdatum
   * _Åtgärdsmeddelande_: Visa korrekt leveransdatum för Fedex Carrier.
   * _Bidrag till_ GitHub-kod: <https://github.com/magento/magento2/commit/57a32313>
* _ACP2E-2763_: Tabellpriser visas fortfarande trots att fri frakt tillämpas
   * _Fix note_: Table Rate fraktmetod visas nu även om gratis frakt blir tillgänglig efter att kupongen har tillämpats
   * _Bidrag till_ GitHub-kod: <https://github.com/magento/magento2/commit/b2286ecf>
* _ACP2E-2765_: MFTF-test AdminCreatingShippingLabelTest misslyckades på grund av att autentiseringsuppgifter inte har lagts till i Jenkins-miljön
   * _Korrigera anteckning_: korrigering för mftf-test
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/ea79f7dd>
* _ACP2E-3340_: FedEx Track API fungerar inte med REST-autentiseringsuppgifter
   * _Korrigera anteckning_: Tidigare FedEx-integrering krävde inte ytterligare API-nycklar för spårnings-API. Nu har en ny konfiguration lagts till som stöd för API-nycklar för spårning.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/ec7e32a9>
* _ACP2E-3354_: [Cloud] Förhandlingsfrekvenser för FedEx returneras inte för REST
   * _Fix note_: Före korrigeringen skickades inte FedEx-kontospecifika priser på svaret, även om de enligt FedEx-dokumentation skulle ha skickats. Efter korrigeringen skickas de kontospecifika priserna på svaret genom att ändra begäran från vår sida.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/55615e61>

### Mellanlagring och förhandsvisning

* _ACP2E-3453_: Det går inte att uppdatera schemalagd uppdatering när unikt kategoriattribut används
   * _Korrigera anteckning_: Ett problem har korrigerats där en schemalagd uppdatering för en kategori inte var möjlig om kategorin hade ett unikt attribut
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/078c387e>

### Målinriktning

* _AC-9432_: [Utgåva] Tillåt användning av CIDR-intervall i tillåtelselista för underhåll
   * _Korrigera anteckning_: Systemet stöder nu användning av CIDR-intervall i underhållsläget Tillåt IP-lista, vilket möjliggör ett intervall av IP-adresser för att kringgå underhållsläge. Tidigare tillät underhållsläget IP-listan endast tillåtna enskilda IP-adresser att kringgå underhållsläge.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/37943>
   * _Bidrag till_ GitHub-kod: <https://github.com/magento/magento2/pull/30699>

### Skatt

* _AC-13295_: [Problem] Funktion/php8.1 konstruktoregenskap höjdes när graf ql
   * _Korrigera anteckning_: Ersätt alla egenskaper med en befordran av konstruktoregenskaper i modulen där diagrammet ql visas:
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/39309>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/pull/36975>
* _ACP2E-3193_: FPT (Fixed Product Tax) fungerar inte med konfigurerbara produkter
   * _Korrigera anteckning_: FPT för konfigurerbara produktvariationer fungerar korrekt.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/ec7e32a9>

### Testramverk

* _AC-11654_: Integrationstest misslyckades med testDbSchemaUpToDate på grund av JSON-kolumntyp
   * _Korrigera anteckning_: Systemet känner nu igen JSON-kolumntyper korrekt i databasschemat under integrationstester och förhindrar testfel på grund av en felmatchning mellan databasschemat och det deklarativa schemat. Tidigare identifierades JSON-kolumntyper felaktigt som LONGTEXT i MariaDB, vilket medförde att integreringstester misslyckades.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/ef81f5a2>
* _AC-13362_: [Problem ] PHPDoc-korrigeringsstavning
   * _Korrigera anteckning_: Systemet identifierar nu korrekt inaktuella metoder i IDE:er på grund av en stavningskorrigering i PHPDoc. Tidigare orsakade ett stavfel i PHPDoc att vissa metoder inte kändes igen som inaktuella.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/31399>
   * _Bidrag till_ GitHub-kod: <https://github.com/magento/magento2/pull/31398>
* _AC-13478_: MAGETWO-95118: Kontrollera beteendet med den beständiga kundvagnen när sessionen har upphört
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/7d5e3906>
* _AC-13848_: Korrigera statiska tester för att aktivera användning av tillägg från tredje part
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/9e383b4d>
* _ACP2E-3334_: [Internt] Fel vid tillämpning av korrigering visas inte under körning eller i loggar
   * _Korrigera anteckning_: -
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/d4de4726>
* _ACP2E-3458_: [MFTF] StorefrontCheckoutProcessForQuoteWithoutNegotiatedPricesTest
   * _Korrigera anteckning_: Korrigerade MFTF-filer
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/078c387e>

### UI Framework

* _AC-12128_: Prototype.js security vulnerability fix CVE-2020-27511
   * _Åtgärdsmeddelande_: Systemet har uppdaterats för att åtgärda säkerhetsluckan CVE-2020-27511 i Prototype.js 1.7.3, vilket förbättrar den övergripande säkerheten i systemet. Före den här uppdateringen var systemet känsligt för en denial of service-attack (Regular Expression Denial of Service) genom att ta bort skapade HTML-taggar.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/de4dfb8e>
* _AC-12189_: Grunt Less använder pub/-prefix för källmappningar
   * _Korrigera anteckning_: Systemet genererar nu färre/css-källkartor utan prefixet /pub för sökvägar när grunt används, vilket eliminerar behovet av en lösning i webbserverkonfigurationen. Tidigare krävdes en specifik konfiguration på webbservern för att /pub-prefixet i källmappssökvägar skulle fungera korrekt.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/38837>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/pull/38840>
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
* _AC-1306_: Statiskt innehåll distribueras för inaktiverade moduler
   * _Korrigera anteckning_: Nu utesluts CSS-relaterade till inaktiverade moduler från de slutliga CSS-utdatafilerna, vilket säkerställer att onödiga format inte läses in. Tidigare inkluderades CSS för inaktiverade moduler i de slutliga CSS-utdatafilerna, vilket ledde till inläsning av extra, onödiga format.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/24666>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/pull/32922>
* _AC-13459_: Inkonsekvent beteende vid sortering av &quot;slut i lager&quot; med tröskel för minsta lager
   * _Åtgärdsmeddelande_: Systemet sorterar nu produkter i katalogen korrekt baserat på lagernivåer, följer den inställda minimilagertröskeln och flyttar artiklar som inte finns i lager till botten av listan konsekvent. Tidigare var sorteringsbeteendet inkonsekvent, med artiklar som inte alltid visades i rätt ordning baserat på deras lagernivåer, och ändringar i sorteringen kunde inträffa oförutsägbart efter att kategorihierarkin har sparats, uppdaterats eller ändrats.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/47b448e2>
* _AC-13472_: Förslag till förbättrad felrapportering för problem med inläsning av require.js
   * _Fix note_: Denna PR förbättrar felmeddelandet när requirejs inte kan ladda en komponent.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/36761>
   * _Bidrag till_ GitHub-kod: <https://github.com/magento/magento2/pull/38971>
* _AC-14004_: PHP 8.4-borttagningsfel som orsakar byggfel i 2.4-utveckling
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/1da9ba6f>
* _AC-9007_: [Utgåva] Läs inte in kontext för serverdelsblock på klientdel
   * _Korrigera anteckning_: Systemet ser nu till att kontexten för backend-block inte läses in på klientservern, vilket förhindrar att onödiga backend-sessioner och eventuella sessionslås skapas. Tidigare lästes serverdelen in felaktigt på klientsidan, vilket ledde till att serverdelssessioner och eventuella sessionslås skapades.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/37617>
   * _Bidrag till_ GitHub-kod: <https://github.com/magento/magento2/pull/36368>
* _AC-9168_: Problem: [Ta] bort onödig sammanfattning av skriptgranskning
   * _Fix note_: Systemet optimerar nu sidans laddningstid genom att ta bort onödiga JavaScript-skript från betygssektionen och istället använda inline CSS-stilar för en mer effektiv och läsbar kod. Tidigare kunde användningen av JavaScript-skript för klassificeringsavsnittet potentiellt sakta ner sidans inläsningstid.
   * _GitHub-problem_: <https://github.com/magento/magento2/issues/37776>
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/pull/34643>
* _ACP2E-2529_: Undantag vid kontroll av ett presentkortssaldo när Recaptcha är aktiverat
   * _Korrigera anteckning_: Användare kan hämta presentkortssaldo i vyn och redigera kundvagnsskärmen. Tidigare visades inte dessa uppgifter när reCAPTCHA aktiverades.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2-page-builder/commit/4a2795ea>
* _ACP2E-2729_: [CLARIFICATION] Funktionsbegäran ADA-överensstämmelse
   * _Korrigera anteckning_: Systemet garanterar nu ADA-kompatibilitet genom att ta bort CSS-egenskaper som inte stöds och ersätta dem med de som stöds i filen print.css. Tidigare ledde användningen av CSS-egenskaper som inte stöds till problem med webbläsarkompatibiliteten.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/57a32313>
* _ACP2E-3061_: [Cloud] Sammanfusionsbibliotekskod i effect-drop.js i AC 2.4.4-p8
   * _Korrigera anteckning_: Systemet implementerar nu biblioteket effect-drop.js korrekt, vilket garanterar att jQuery-gränssnittseffekterna fungerar som de ska. Tidigare skrevs biblioteket effect-drop.js av misstag över med biblioteket effect-clip.js, vilket kan orsaka problem med jQuery-gränssnittseffekter.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/35b1b1da>
* _ACP2E-3367_: Platshuvud | Specialtecken som bryter kundens välkomstavsnitt
   * _Korrigera anteckning_: Efter korrigeringen visas specialtecken korrekt i välkomstavsnittet för kunder.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/1366ae5e>
* _ACP2E-3561_: Kundsegmentversionen misslyckas med daterange
   * _Korrigera anteckning_: Det går att spara kundsegment med datumintervallvillkor när endast ett av datumen har redigerats.
   * _GitHub-kodbidrag_: <https://github.com/magento/magento2/commit/a52ff98f>
