---
source-git-commit: 6c7feee0cd23d397c40bb66593a79b59ac2f620a
workflow-type: tm+mt
source-wordcount: '3326'
ht-degree: 0%

---
# Adobe Commerce åtgärdade problem (v2.4.9-alpha1)

## Åtgärdade problem i v2.4.9-alpha1

Vi har åtgärdat 84 problem i Adobe Commerce 2.4.9-alpha1-kärnkoden. En deluppsättning av de åtgärdade problemen som ingår i den här versionen beskrivs nedan.

### API:er

* __Den asynkrona gruppåtgärden är fortfarande öppen för async.magento.configurableproduct.api.optiondatabasinterface.save.post__
Massor-API-slutpunkter genererar nu ett fel om begärandetexten inte är en matris, vilket kräver att bulkartikelnycklar är siffror i följd från 0. Tidigare uppdaterades inte bulkartikelstatus på grund av den godtyckliga artikelnyckeln som skickades i bulkbegäran.
  _ACP2E-3544 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/9608ca21)_
* __[CLOUD] API REST-fel för is_subscribed-värdet som inte beaktas från det aktuella arkivet med searchCriteria__
API REST-kundfrågan hämtar rätt &quot;is_subscribed&quot;-värde från rätt butik med hjälp av searchCriteria
Tidigare beaktades inte arkivet vid hämtning av värdet is_subscribed i API:ts REST-kundfråga.
  _ACP2E-3621 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/9608ca21)_
* __async.operations.all kan skapa flera poster för 1 SKU__
Samtidiga begäranden om att spara och uppdatera samma produkt har nu serialiserats för att förhindra konkurrensförhållanden som kan leda till inkonsekventa data eller dubblerade produkter
  _ACP2E-3744 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/520f9e30)_

### Konto

* __[Borttagningsåtgärden i molnet] tillåts inte för aktuellt områdesfel när kundkontot skapas__
När korrigeringen har sparats returnerar en kund med en ogiltig adress ett meddelande som beskriver orsaken till invaliditeten i stället för irrelevant&quot;Delete-åtgärden är förbjuden för aktuellt område&quot;.
  _ACP2E-3791 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/6ea61121)_

### Administratörsgränssnitt

* __[Problem] Förbättra användarupplevelsen med rollträdet__
Dragbegäran lägger till knappar för att komprimera alla, expandera alla och expandera grenar med markerade objekt. Den här funktionen liknar den som finns i kategoriträdet (Katalog -> Lager -> Kategorier)
  _AC-14020 - [GitHub-problem](https://github.com/magento/magento2/issues/39654) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/36511)_
* __Symfony\Component\Mime\Exception\LogicException: Avsändarhuvudet måste vara en instans av Symfony\Component\Mime\Header\MailboxHeader (har värdet Symfony\Component\Mime\Header\MailboxListHeader)__
  _AC-14520 - [GitHub-problem](https://github.com/magento/magento2/issues/39823) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/1e14bd72)_
* __Ange en funktion för massradering av momssatser med stödrastret__
Administratörsanvändare kan nu ta bort flera skattesatser samtidigt från rutnätet för administrationsskattesatser.  [GitHub-33399](https://github.com/magento/magento2/issues/33399)
  _AC-2238 - [GitHub-problem](https://github.com/magento/magento2/issues/33399) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/33484) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/5cd64dd0)_
* __Artikelprisregel med villkor-SKU dosen tar inte hänsyn till &quot;inledande nollor&quot; i SKU:n (sku: 01234 är samma som 1234)__
Systemet hanterar nu kundvagnsprisregeln korrekt med villkor-SKU med hänsyn tagen till&quot;inledande nollor&quot; i SKU:n
  _AC-9428 - [GitHub-problem](https://github.com/magento/magento2/issues/37919) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/39525)_
* __Problem med standardvärdesbeteende för attributalternativ för multiselect__
Före korrigeringen av standardvärdena för attributet multiple options sparades inte korrekt. Efter korrigeringen lagras värdena korrekt i databasen.
  _ACP2E-3523 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/9608ca21)_
* __Undertexter på administratörsmenyn för serverdelen visas inte__
Alla rubriker i huvudmenygrupperna visas nu korrekt. Tidigare visades inte gruppens rubrik om den andra eller tredje kolumnen på huvudmenyn bara innehöll en grupp länkar.
  _ACP2E-3540_
* __Ett problem uppstod när produktkvantiteten flyttades tillbaka till kundvagnen från administratören__
När du skapar en order från administratören försvinner inte produkterna i kundvagnen på sidofältet när de läggs till i ordern.
  _ACP2E-3563 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/c8ba4ab1)_

### Administratörsgränssnitt, B2B

* __B2B-inloggning som kundhuvud har fortfarande Magento-märkning__
Tidigare visas i butiksrubriken&quot;Du är nu ansluten som &lt;kundnamn> på &lt;butiksnamn>&quot; med Magento-märkning. Det är nu fixat och rubriken visas med ADOBE branding.
  _AC-14361 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/fadcfa8b)_

### Administratörsgränssnitt, innehåll

* __Undantag&quot;Det går inte att skapa återgivning för medieresurssökvägar&quot; vid infogning av bilder__
När du har tagit bort värdena för Maximal bredd och Maximal höjd i konfigurationen för bildoptimering i Mediegalleriet inträffar felet inte längre under bildoptimeringsprocessen.
  _ACP2E-3781 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/520f9e30)_

### Administratörsgränssnitt, säkerhet

* __Svag lösenordshantering__
Administratörsanvändaren kan inte sparas när samma lösenord används. Tidigare sparades den utan korrekt validering.
  _ACP2E-3657 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/df92debe)_

### Administratörsgränssnitt, säkerhet, mellanlagring och förhandsvisning

* __Åtgärdsloggar för innehållstagning__
Åtgärdsloggarna visar nu aktiviteterna för mellanlagringsuppdatering. Tidigare spelades inte loggen för mellanlagringsuppdatering in i administratörens åtgärdsloggar.
  _ACP2E-3679_

### B2B

* __Monteringsorder fungerar inte med Gå till kassan via Negotiable Quote med betalningsmetoden PayFlow Pro Credit Card__
  _AC-11973_
* __Meddelande om att offerten har bytt namn försvinner ibland__
  _AC-13447_
* __Summeringsberäkningen inkluderar inte momsbeloppet__
Ordern innehåller korrekta summor när platser från en befintlig inköpsorder med alternativet Gränsöverskridande handel är aktiverat.
  _ACP2E-3727_
* __Det tar lång tid att frigöra kategorier i en delad B2B-katalog via REST API:t__
Nu har prestandan förbättrats avsevärt när du frigör kategorier i B2B. Tidigare tog det lång tid att ta bort tilldelningen av kategorier i den delade B2B-katalogen.
  _ACP2E-3796_
* __Prestandaproblem med ny installationspatch i B2B__
Åtgärdar prestandaproblemet där det tog för lång tid att uppgradera Magento_Company-modulen efter uppdatering till B2B 1.5.2 vid bearbetning av ett stort antal poster (~100 000+) i tabellen company_structure.
  _ACP2E-3850_

### Kort och utcheckning

* __Magento 2.4.7 update (mini)cart no decimal quty allowed__
Nu hanterar Magento korrekt när vi uppdaterar kvantitet med decimaler från mini cart när språkinställningen var NL (holländska)
  _AC-13238 - [GitHub-problem](https://github.com/magento/magento2/issues/39236) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/39669)_
* __[Problem] Uppdatera delsumma.phtml__
Systemet uppdaterar subtotal.phtml med rätt mellanrum
  _AC-13907 - [GitHub-problem](https://github.com/magento/magento2/issues/39619) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/39612)_
* __Det går inte att lägga beställningen hos gästen__
  _AC-14241 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/27217d0e)_
* __Utgångna beständiga citattecken rensas inte av ett cron job sales_clean_quotes__
De utgångna beständiga citattecknen rensas nu när kron-jobbet persistent_clear_expirate körs. Tidigare rensades inte de inaktuella, beständiga citattecknen av något annat cron-jobb.
  _ACP2E-3493 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/11be3dff)_
* __Ett fel uppstod vid utcheckning av inaktivt företag__
Före korrigeringen slutfördes inte utloggningsåtgärden korrekt på kundvagnssidan om det inloggade användarföretaget inte längre var aktiverat. Om företaget inte längre är tillgängligt utförs utloggningen korrekt.
  _ACP2E-3541 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/df92debe)_
* __Adressmarkeringen sparas inte när vi checkar ut med flera adresser.__
Innan korrigeringen avbröts valdes inte adressen i förväg när du återgick till flera leveranser. Nu ersätts standardadressen med ett av de val som gjorts på skärmen för flera leveranser.
  _ACP2E-3646 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/6ea61121)_

### Kort och utcheckning, SEO

* __Felaktig URL för presentkortskod i e-postmeddelandet när det köpts in från den sekundära webbplatsen__
Tidigare omdirigerades presentkortsanspråket alltid till standardwebbplatsen när du använde flera butiker och presentkort för andra butiker. När den här korrigeringen har tillämpats dirigeras presentkortets anspråkslänk om till rätt omfattning eller webbplats.
  _ACP2E-3699_

### Kundvagn och utcheckning, leverans

* __[Mainline] Prisregeln för kundvagn respekterar inte flerleverans__
Innan den här korrigeringen genomfördes tillämpades inte kundvagnsprisregeln för produkter med flera leveranser korrekt när vissa villkor tillämpades och fri frakt aktiverades. Men eftersom korrigeringen gjordes fungerar nu kundvagnsprisregeln för varukorgar som avsett.
  _ACP2E-3666 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/b12ffe36)_

### Katalog

* __Duplicerad cache fpc för samma sida med samma fråga__
Nu identifieras och används samma helsidescache (FPC) korrekt för sidor med samma frågeparametrar, oavsett ordningsföljd eller efterföljande tecken. Detta förhindrar att storleken på sidcachemappen ökar i onödan. Tidigare skulle systemet skapa en annan FPC-identifierare för samma sida om frågeparametrarnas ordning var annorlunda eller om det fanns efterföljande tecken, vilket skulle leda till en ökning av storleken på sidcachemappen.
  _AC-10722 - [GitHub-problem](https://github.com/magento/magento2/issues/38269) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/38270)_
* __Indexering av obligatoriska kolumner saknas i tabellen catalog_product_entity_int__
Lagt till saknad indexering av obligatoriska kolumner i tabellen catalog_product_entity_int
  _AC-10844 - [GitHub-problem](https://github.com/magento/magento2/issues/38315) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/38316)_
* __Produktsidan ger ett fel på grund av URL-omskrivningar__
Nu läses produktsidan in korrekt när URL-omskrivningar görs
  _AC-2950 - [GitHub-problem](https://github.com/magento/magento2/issues/35371) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/39670)_
* __[Fel i molnet] när produkter läggs till i kategori__
Etiketten för sidnumrering och antal poster fungerar nu korrekt när du lägger till produkter i en kategori via popup-rutnätet. Tidigare orsakade inläsning av endast en sida med objekt som var lika med sidstorleken problem med listrutan för val av objekt.
  _ACP2E-3526_
* __cron-felet indexer_update_all_views med MAGE_INDEXER_THREADS_COUNT__
Korrigerat problem med MAGE_INDEXER_THREADS_COUNT > 2 med kundsegmentsindexeraren
  _ACP2E-3538 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/9608ca21)_
* __Undantag när villkorskombination lades till i widgetvillkoret för Page Builder-produkter__
Problemet har åtgärdats genom att en kontroll läggs till för att hoppa över saknade eller ofullständiga villkor. Tidigare genererades felloggar på grund av hantering av ofullständiga förhållanden i systemet.
  _ACP2E-3545 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/11be3dff)_
* __Webbläsaren kraschar när attributuppsättningen läses in__
Webbläsaren kraschar inte längre på redigeringssidan för attributuppsättningar om det finns fler än 4k-produktattribut
  _ACP2E-3633 - [GitHub-problem](https://github.com/magento/magento2/issues/38810) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/b12ffe36)_
* __[CLOUD] Produkt-URL-omskrivningar har inte skapats för ny butik: Go Live Blocker__
Produkt-URL-omskrivningar för New Store har skapats.
Tidigare slutfördes minnesläckage eller timeout.
  _ACP2E-3669 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/df92debe)_
* __Attributstandardvärde för alternativ som inte fungerar__
Tidigare visades det som ett arrayelement med de tidigare värdena när vi ändrade standardvärdet för ett produktvalsattribut. När den här korrigeringen har tillämpats sparas det som ett element i eav_attribute-tabellen när vi uppdaterar ett produktattributvärde.
  _ACP2E-3688 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/520f9e30)_
* __Vykortsvalideringen misslyckas vid redigering på grund av tusentalsavgränsare__
Ett problem med att spara presentkortsprodukter när presentkortsbeloppet är 1 000 eller mer har åtgärdats.
  _ACP2E-3704_

### Katalog, GraphQL, sökning

* __Produktgrafen returnerade inaktiverade kategorier i kategoriaggregeringarna__
När korrigeringen har inaktiverats returneras inga kategorier för produkterna GraphQl-begäran.
  _ACP2E-2885 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/b12ffe36)_

### Katalog, produkt

* __[Slumpmässigt fel] Fotoramalib har inte lästs in__
Systemet ser nu till att Fotoramabiblioteket läses in korrekt, så att alla kopplade bilder kan visas i bildgalleriet som förväntat. Tidigare var bara den första bilden synlig på grund av ett problem med att Fotoramabiblioteket inte lästes in korrekt.
  _AC-12124 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/45b51c9c) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/27217d0e)_

### Innehåll

* __Att skicka csp_whitelist.xml i temat fungerar inte och skapar intermittent problem__
Implementerad cachelagring av CSP-vitlista per webbplatsområde.
  _AC-13069 - [GitHub-problem](https://github.com/magento/magento2/issues/38933) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/39672)_
* __Fel: Skriptfel för&quot;Magento_Catalog/js/validate-product&quot; för administratörens innehållssidbyggare med produkter inlästa__
Denna PR åtgärdar skriptfelet för catalogAddToCart när sidbyggaren redigeras med produktvillkoret
  _AC-13891 - [GitHub-problem](https://github.com/magento/magento2/issues/39604) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/39677)_
* __Blockera markering i widgetar som har samma identifierare__
Systemet hanterar nu markeringsblock korrekt när vi skapar widgetar när vi har samma identifieringsblock
  _AC-14132 - [GitHub-problem](https://github.com/magento/magento2/issues/39692) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/39722)_
* __Tabellprefix tas inte med i beräkningen__
  _AC-14556 - [GitHub-problem](https://github.com/magento/magento2/issues/39847) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/1bc2d6d0)_
* __Det gick inte att överföra bilden med relativt liten bredd__
Systemet misslyckas inte längre med att ändra storlek på bilden med relativt liten bredd till höjden.
  _ACP2E-3558 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/9608ca21)_
* __Felaktig konfigurationssökväg för formatkonfiguration för fjärrlagringssökväg__
När korrigeringen är klar påverkas den faktiska sökvägskonfigurationen för AWS S3 när du anger en stil för fjärrlagringssökvägen.
  _ACP2E-3734 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/df92debe)_

### Ramverk

* __Kompilerar kod för inaktiverad modul.__
Den här pull-begäran tar bort inaktiverade moduler innan kodkompilering.
  _AC-10933 - [GitHub-problem](https://github.com/magento/magento2/issues/38241) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/39723)_
* __Mallen Magento_Theme title.phtml är ogiltig för PHP 8.2__
Den här pull-begäran åtgärdar ett problem när en CMS-sida som skapas med rubriken null, som i PHP 8.x, skickar null till trim(), genererar ett undantag: Föråldrad funktionalitet: trim(): Överför null till parametern #1 ($string) av typen string
  _AC-12856 - [GitHub-problem](https://github.com/magento/magento2/issues/39092) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/39398)_
* __När vi använder fillagring för låsleverantören får vi en ständigt växande katalog med filer utan att någon rensning görs__
Dragbegäran innehåller ett nytt cron-jobb som körs en gång om dagen och söker efter låsfiler som inte har ändrats de senaste 24 timmarna och som därför kan tas bort på ett säkert sätt. Detta håller innehållet i katalogen med låsfiler under kontroll.
Detta cron-jobb kommer endast att köra något när låsprovidern är konfigurerad att använda filer, inte när någon av de andra används (databas - standard, zookeeper eller cache)
  _AC-13367 - [GitHub-problem](https://github.com/magento/magento2/issues/39369) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/39372)_
* __[Issue] Cleanup: använd inte ett void-returvärde från metodanrop.__
Den här PR:en rensar lite. Ibland anropade vi metoder som inte returnerade något (void) och sedan använde vi det resultatvärdet. Det behövs verkligen inte.
  _AC-13664 - [GitHub-problem](https://github.com/magento/magento2/issues/39524) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/39516)_
* __[Problem] [PHPDOC] Korrigera felaktig bild för Magento\Framework\Message\ManagerInterface__
Denna PR korrigerar det felaktiga fotot för \Magento\Framework\Message\ManagerInterface och tar bort alla duplicerade foton i \Magento\Framework\Message\Manager (använd arvssyntax).
  _AC-14312 - [GitHub-problem](https://github.com/magento/magento2/issues/39593) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/39153)_
* __Borttagen betaversion av minimal stabilitet från Composer.json__
Borttagen betaversionsstabilitet från Composer.json
  _AC-14450 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/1cbbf187)_
* __allow_parallel_generation bör anges via systemvariabeln__
Efter korrigeringen kan miljövariabeln &quot;MAGENTO_DC_CACHE_ALLOW_PARALLEL_GENERATION&quot; användas för att ställa in konfigurationen &quot;allow_parallel_generation&quot;.
  _ACP2E-3673 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/b12ffe36)_
* __[Cloud] Ändra tabellkolumntyp från Int till Decimal med db_schema.xml-filen I Magento 2 resulterar i fel__
Det går inte att ändra kolumndatatypen korrekt. Tidigare uppstod ett fel: Attributet identity är inte tillåtet.
  _ACP2E-3709 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/df92debe)_
* __Stöd för ny valuta (XCG) i Adobe__
Karibien Guilder (XCG) läggs till i valutalistan.
  _ACP2E-3790 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/520f9e30)_

### GraphQL

* __GraphQL-svar för orderplacering innehåller inte undantagsmeddelandet__
Återställde tidigare ändring som returnerade fel i ett annat format. Nu returneras potentiella fel på ett konsekvent sätt, inte GraphQL-schemat. Detta bör läggas till som känd BIC, godkänd av PM i AVS2E-3399
  _ACP2E-3399 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/9608ca21)_
* __GraphQL-svar för orderplacering är delvis lokaliserat__
Fel som returnerades av placeOrder GraphQl-mutationen var inte helt lokaliserade. I ett flerspråkigt sammanhang översätts nu felen korrekt.
  _ACP2E-3506 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/9608ca21)_
* __Samtidiga anrop för att ändra ordning på GraphQL API - samma produkter som lagts till på olika rader__
Korrigerar problemet där samtidiga anrop till API:t för att ändra ordning för GraphQL resulterar i att samma produkter läggs till som olika rader, vilket leder till inkonsekventa data.
  _ACP2E-3774 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/c8ba4ab1)_
* __updateCustomerEmail GraphQL mutation(Change email Address) utlöser inte e-postmeddelandet__
Tidigare skickades inte e-post till kunder efter att deras e-postadresser uppdaterats på deras konton. När korrigeringen har tillämpats får kunderna nu e-postmeddelanden när de har uppdaterat sina e-postadresser.
  _ACP2E-3785 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/c8ba4ab1)_
* __Det dynamiska attributet uppdateras inte i presentregistret via updateGiftRegistry Mutation__
Före den här korrigeringen via mutationen updateGiftRegistry ändrades eller uppdaterades inte det anpassade attributet i presentregistret via GraphQL-mutationer. När korrigeringen har tillämpats kan presentregistrets dynamiska attribut uppdateras med mutationen updateGiftRegistry.
  _ACP2E-3805 - [GitHub-problem](https://mcstaging.briscoes.co.nz/)_

### Importera/exportera

* __[Utgåva] Kopiera: ändra &quot;kopiera&quot; till &quot;kopiera&quot;__
PR korrigerar den mindre kopieringsredigeringen för att korrigera stavningen av&quot;kopiering&quot;
  _AC-13300 - [GitHub-problem](https://github.com/magento/magento2/issues/39311) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/39307)_
* __REST-slutpunkt Produktimport Json validerar inte obligatoriska fält__
Namnfält krävs nu när nya produkter skapas via importprocessen (admin eller API). Före korrigeringen kunde du ha skapat nya produkter utan namn, vilket hade brytt administratörsgränssnittet och skapat ogiltiga produkter.
  _ACP2E-3660 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/df92debe)_
* __Alternativet Webbplatsfilter saknas i exportprocessen__
Nu går det att filtrera produkter efter webbplatser när du skapar produktexporter.
  _ACP2E-3720 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/520f9e30)_
* __Duplicering av AC-13913 - Statisk attributrensning asynkront.__
Efter korrigeringen finns det inget &#39;odefinierad matrisnyckel&#39;-fel när flera instanser av \Magento\CatalogImportExport\Model\Import\Product\Type\AbstractType skapas.
  _ACP2E-3752 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/520f9e30)_

### Lager/MSI

* __Butiksplockning respekterar inte maximal sökradie när adressen ändras vid utcheckning__
Den förvalda butiken i&quot;Plocka i butik&quot; uppdateras om leveransadressen ändras. Tidigare ändrades inte butiken när den väl hade valts ut, även om den nya leveransadressen inte ligger inom den valda butikens radie
  _ACP2E-3728 - [GitHub-kodbidrag](https://github.com/magento/inventory/commit/07620383)_

### Beställning

* __Det går inte att returnera null för fältet \&amp;quot;AppliedCoupon.code\&amp;quot; oväntat fel__
  _AC-14484 - [GitHub-problem](https://github.com/magento/magento2/issues/39841) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/97b2ea42)_
* __[Cloud] Vissa infogade JavaScript fungerar inte efter uppgradering till magento 2.4.6-p7__
Om du klickar på knappen &quot;Ta bort&quot; i &quot;Lägg till i order av SKU&quot; i administratören tas SKU:n bort. Tidigare togs SKU inte bort när du klickade på knappen&quot;Ta bort&quot; i&quot;Lägg till i order av SKU&quot;.
  _ACP2E-3515_
* __present_cards serialiserade data är inkonsekventa i tabellen sales_order__
presentkortsdata i tabellen sales_order är nu korrekt serialiserade. Tidigare serialiserades den varje gång ordern uppdaterades.
  _ACP2E-3662_

### Order, pris

* __Admin visar felaktig valutasymbol när retur skapas__
I en flerwebbplatskonfiguration med olika valutor (EUR/USD/GBP) visas nu rätt valutasymbol på sidan för val av returprodukt i administratören. Tidigare visades standardvalutasymbolen.
  _ACP2E-3658 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/df92debe)_

### Andra utvecklingsverktyg

* __Hjälpmedelsfel för Lightroom__
Nu skickas System med tillgänglighetspoängen 100
  _AC-12783 - [GitHub-problem](https://github.com/magento/magento2/issues/39054) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/39164)_
* __Inaktivera Captcha storefront-konfigurationen läser fortfarande in captcha js-filer__
Systemet läser nu inte in captcha js-filer när vi inaktiverade captcha för storefront
  _AC-14267 - [GitHub-problem](https://github.com/magento/magento2/issues/32987) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/39154)_

### Paketering

* __[Paketering] Korrigera magento/magento-coding-standard-beroende+ page-builder__
  _ACPLTSRV-6383_

### Betalningar

* __[Problem] Åtgärda offlinefakturainhämtning (404)__
Det åtgärdar 404-sidesfelet när fakturor hämtas för offlinebetalningsmetoder från Magento-administratören
  _AC-13336 - [GitHub-problem](https://github.com/magento/magento2/issues/39298) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/39297)_

### Prestanda

* __Modulen Kategoribehörigheter förhindrar eventuellt cachelagring__
Externa styrenheter har nu cachelagrats korrekt med kundsegment
  _ACP2E-3721_

### Produkt

* __Produktsamling - addMediaGalleryData anropar getSize när samlingen kanske läses in (Kan använda count för att undvika en extra DB-fråga)__
Denna PR reducerar det extra frågeanropet med count() om produktsamlingen redan har lästs in när Product Graphql anropas med fältet media_gallery.
  _AC-13055 - [GitHub-problem](https://github.com/magento/magento2/issues/39111) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/39681)_
* __[2.4.8] Inga återanrop hittades för cron job catalog_product_alert__
  _AC-14494 - [GitHub-problem](https://github.com/magento/magento2/issues/39800) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/1bc2d6d0)_
* __Långsam fråga körs när produktwidgeten inkluderas via pagebuilder__
Frågan för att skapa produktwidgetar, inklusive produkt-SKU:er, är optimerad.
  _ACP2E-3449 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/df92debe)_
* __Storleken på produktbilder ändras inte när de läggs till som en konfigurerbar produkt__
Tidigare var de bilder som lades till via konfigurationer på adminpanelen inte lika med den maximala överföringsstorleksgränsen, vilket kunde leda till inkonsekvenser och hanteringsproblem. Nu har en korrigering implementerats för att säkerställa att storleken på bilderna automatiskt ändras under överföringen så att de uppfyller den maximala storleksgränsen, vilket effektiviserar processen och bevarar systemstandarderna.
  _ACP2E-3504 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/df92debe)_

### Leverans

* __Dokumentet ska uppdateras för % implementering vilket inte är korrekt i det officiella dokumentet__
Enheten för DHL Rest API-stöd har uppdaterats
  _AC-14507_
* __[DHL]-Hantera valfria dimensioner i inställningarna för normal storlek och prisvarians mellan REST- och XML-API-integreringar__
  _AC-14601 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/1e3bde4c)_
* __Undantag när UPS-leveransetikett skapas__
Fast varning: Konvertering från matris till sträng när UPS-etiketten skapas
  _ACP2E-3676 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/b12ffe36)_

### Mellanlagring och förhandsvisning

* __Om du förhandsgranskar en schemalagd uppdatering öppnas den första butiksvyn i alfabetisk ordning i stället för butiksvyn__
Före korrigeringen öppnas förhandsgranskningen av en schemalagd uppdatering i den första butiksvyn i alfabetisk ordning i stället för i den tilldelade butiksvyn.
Efter korrigeringen öppnas nu förhandsgranskningen korrekt i butiksvyn som tilldelats till CMS-blockstagguppdateringen.
  _ACP2E-3671 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/b12ffe36)_
* __Beteendefel för Stage_apply_version Cron - special_price ignorerades__
Efter korrigeringen beräknas offertsummorna om efter ändring av specialpris per schemalagd produktuppdatering.
  _ACP2E-3674_

### Moms

* __Momsbeloppet uppdateras inte när en presentbrytning tas bort från vagnen__
  _AC-14637_
