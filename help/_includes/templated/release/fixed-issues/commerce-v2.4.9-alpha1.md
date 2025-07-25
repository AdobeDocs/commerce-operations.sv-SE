---
source-git-commit: 2f471a1bc1cbf31076aeb67ceaee289196841cd4
workflow-type: tm+mt
source-wordcount: '3326'
ht-degree: 0%

---
# Adobe Commerce åtgärdade problem (v2.4.9-alpha1)

## Åtgärdade problem i v2.4.9-alpha1

Vi har åtgärdat 84 problem i Adobe Commerce 2.4.9-alpha1-kärnkoden. En deluppsättning av de åtgärdade problemen som ingår i den här versionen beskrivs nedan.

### API:er

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

### Konto

#### [Borttagningsåtgärden i molnet] tillåts inte för aktuellt områdesfel när kundkonton skapas

När korrigeringen har sparats returnerar en kund med en ogiltig adress ett meddelande som beskriver orsaken till invaliditeten i stället för irrelevant&quot;Delete-åtgärden är förbjuden för aktuellt område&quot;.

_ACP2E-3791 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/6ea61121)_

### Administratörsgränssnitt

#### [Problem] Förbättra användarupplevelsen med rollträdet

Dragbegäran lägger till knappar för att komprimera alla, expandera alla och expandera grenar med markerade objekt. Den här funktionen liknar den som finns i kategoriträdet (Katalog -> Lager -> Kategorier)

_AC-14020 - [GitHub-problem](https://github.com/magento/magento2/issues/39654) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/36511)_

#### Symfony\Component\Mime\Exception\LogicException: &quot;Sender&quot;-huvudet måste vara en instans av &quot;Symfony\Component\Mime\Header\MailboxHeader&quot; (men &quot;Symfony\Component\Mime\Header\MailboxListHeader&quot;)

_AC-14520 - [GitHub-problem](https://github.com/magento/magento2/issues/39823) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/1e14bd72)_

#### Ange en funktion för massradering av skattesatser med hjälp av rutnätet

Administratörsanvändare kan nu ta bort flera skattesatser samtidigt från rutnätet för administrationsskattesatser.  [GitHub-33399](https://github.com/magento/magento2/issues/33399)

_AC-2238 - [GitHub-problem](https://github.com/magento/magento2/issues/33399) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/33484) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/5cd64dd0)_

#### Fästprisregel med villkor SKU dosen inte ta hänsyn till&quot;inledande nollor&quot; i SKU:n (sku: 01234 är samma som 1234)

Systemet hanterar nu kundvagnsprisregeln korrekt med villkor-SKU med hänsyn tagen till&quot;inledande nollor&quot; i SKU:n

_AC-9428 - [GitHub-problem](https://github.com/magento/magento2/issues/37919) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/39525)_

#### Problem med standardbeteende för attributalternativvärde för Multiselect

Före korrigeringen av standardvärdena för attributet multiple options sparades inte korrekt. Efter korrigeringen lagras värdena korrekt i databasen.

_ACP2E-3523 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/9608ca21)_

#### Undertexter på serverdelsmenyn visas inte

Alla rubriker i huvudmenygrupperna visas nu korrekt. Tidigare visades inte gruppens rubrik om den andra eller tredje kolumnen på huvudmenyn bara innehöll en grupp länkar.

_ACP2E-3540_

#### Problem vid flyttning av produktkvantiteten till varukorgen från administratören

När du skapar en order från administratören försvinner inte produkterna i kundvagnen på sidofältet när de läggs till i ordern.

_ACP2E-3563 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/c8ba4ab1)_

### Administratörsgränssnitt, B2B

#### B2B-inloggning som kundhuvud har fortfarande Magento varumärke

Tidigare visas i butiksrubriken&quot;Du är nu ansluten som &lt;kundnamn> på &lt;butiksnamn>&quot; med Magento-märkning. Det är nu fixat och rubriken visas med ADOBE branding.

_AC-14361 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/fadcfa8b)_

### Administratörsgränssnitt, innehåll

#### Undantaget&quot;Det går inte att skapa återgivning för medieresurssökvägar&quot; vid infogning av bilder

När du har tagit bort värdena för Maximal bredd och Maximal höjd i konfigurationen för bildoptimering i Mediegalleriet inträffar felet inte längre under bildoptimeringsprocessen.

_ACP2E-3781 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/520f9e30)_

### Administratörsgränssnitt, säkerhet

#### Svag lösenordshantering

Administratörsanvändaren kan inte sparas när samma lösenord används. Tidigare sparades den utan korrekt validering.

_ACP2E-3657 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/df92debe)_

### Administratörsgränssnitt, säkerhet, mellanlagring och förhandsvisning

#### Åtgärdsloggar för innehållstagning

Åtgärdsloggarna visar nu aktiviteterna för mellanlagringsuppdatering. Tidigare spelades inte loggen för mellanlagringsuppdatering in i administratörens åtgärdsloggar.

_ACP2E-3679_

### B2B

#### Monteringsorder fungerar inte med Gå till kassan via Negotiable Quote med betalningsmetoden PayFlow Pro Credit Card

_AC-11973_

#### Meddelande om att offerten har bytt namn försvinner ibland

_AC-13447_

#### Den totala beräkningen inkluderar inte momsbeloppet

Ordern innehåller korrekta summor när platser från en befintlig inköpsorder med alternativet Gränsöverskridande handel är aktiverat.

_ACP2E-3727_

#### Det tar lång tid att frigöra kategorier i en delad B2B-katalog via REST API

Nu har prestandan förbättrats avsevärt när du frigör kategorier i B2B. Tidigare tog det lång tid att ta bort tilldelningen av kategorier i den delade B2B-katalogen.

_ACP2E-3796_

#### Prestandaproblem med den nya installationspatchen inom B2B

Åtgärdar prestandaproblemet där det tog för lång tid att uppgradera Magento_Company-modulen efter uppdatering till B2B 1.5.2 vid bearbetning av ett stort antal poster (~100 000+) i tabellen company_structure.

_ACP2E-3850_

### Kort och utcheckning

#### Magento 2.4.7 update (mini)cart no decimal quantity allowed

Nu hanterar Magento korrekt när vi uppdaterar kvantitet med decimaler från mini cart när språkinställningen var NL (holländska)

_AC-13238 - [GitHub-problem](https://github.com/magento/magento2/issues/39236) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/39669)_

#### [Problem] Uppdatera delsumma.phtml

Systemet uppdaterar subtotal.phtml med rätt mellanrum

_AC-13907 - [GitHub-problem](https://github.com/magento/magento2/issues/39619) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/39612)_

#### Det går inte att lägga ordern hos gästen

_AC-14241 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/27217d0e)_

#### Utgångna beständiga citattecken rensas inte av ett cron job sales_clean_quotes

De utgångna beständiga citattecknen rensas nu när kron-jobbet persistent_clear_expirate körs. Tidigare rensades inte de inaktuella, beständiga citattecknen av något annat cron-jobb.

_ACP2E-3493 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/11be3dff)_

#### Ett fel uppstod vid utcheckning av inaktivt företag

Före korrigeringen slutfördes inte utloggningsåtgärden korrekt på kundvagnssidan om det inloggade användarföretaget inte längre var aktiverat. Om företaget inte längre är tillgängligt utförs utloggningen korrekt.

_ACP2E-3541 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/df92debe)_

#### Markeringen av adresser sparas inte när vi checkar ut med flera adresser

Innan korrigeringen avbröts valdes inte adressen i förväg när du återgick till flera leveranser. Nu ersätts standardadressen med ett av de val som gjorts på skärmen för flera leveranser.

_ACP2E-3646 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/6ea61121)_

### Kort och utcheckning, SEO

#### Felaktig URL för presentkortskod i e-postmeddelandet när det köpts in från den sekundära webbplatsen

Tidigare omdirigerades presentkortsanspråket alltid till standardwebbplatsen när du använde flera butiker och presentkort för andra butiker. När den här korrigeringen har tillämpats dirigeras presentkortets anspråkslänk om till rätt omfattning eller webbplats.

_ACP2E-3699_

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

#### Produktsidan genererar fel på grund av omskrivningar av URL

Nu läses produktsidan in korrekt när URL-omskrivningar görs

_AC-2950 - [GitHub-problem](https://github.com/magento/magento2/issues/35371) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/39670)_

#### [Fel i molnet] när produkter läggs till i kategorin

Etiketten för sidnumrering och antal poster fungerar nu korrekt när du lägger till produkter i en kategori via popup-rutnätet. Tidigare orsakade inläsning av endast en sida med objekt som var lika med sidstorleken problem med listrutan för val av objekt.

_ACP2E-3526_

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

#### Presentkortsvalideringen misslyckas vid redigering på grund av tusentalsavgränsare

Ett problem med att spara presentkortsprodukter när presentkortsbeloppet är 1 000 eller mer har åtgärdats.

_ACP2E-3704_

### Katalog, GraphQL, sökning

#### Produktgrafql returnerade inaktiverade kategorier i kategoriaggregeringar

När korrigeringen har inaktiverats returneras inga kategorier för produkterna GraphQl-begäran.

_ACP2E-2885 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/b12ffe36)_

### Katalog, produkt

#### [Slumpmässigt fel] Fotoramalib har inte lästs in

Systemet ser nu till att Fotoramabiblioteket läses in korrekt, så att alla kopplade bilder kan visas i bildgalleriet som förväntat. Tidigare var bara den första bilden synlig på grund av ett problem med att Fotoramabiblioteket inte lästes in korrekt.

_AC-12124 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/45b51c9c) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/27217d0e)_

### Innehåll

#### Att skicka csp_whitelist.xml i temat fungerar inte och ger upphov till återkommande problem

Implementerad cachelagring av CSP-vitlista per webbplatsområde.

_AC-13069 - [GitHub-problem](https://github.com/magento/magento2/issues/38933) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/39672)_

#### Fel: Skriptfel för&quot;Magento_Catalog/js/validate-product&quot; för administratörens innehållssidbyggare med produktinläsning

Denna PR åtgärdar skriptfelet för catalogAddToCart när sidbyggaren redigeras med produktvillkoret

_AC-13891 - [GitHub-problem](https://github.com/magento/magento2/issues/39604) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/39677)_

#### Blockera markering i widgetar som har samma identifierare

Systemet hanterar nu markeringsblock korrekt när vi skapar widgetar när vi har samma identifieringsblock

_AC-14132 - [GitHub-problem](https://github.com/magento/magento2/issues/39692) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/39722)_

#### Tabellprefix beaktas inte

_AC-14556 - [GitHub-problem](https://github.com/magento/magento2/issues/39847) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/1bc2d6d0)_

#### Det gick inte att överföra bilden med relativt liten bredd

Systemet misslyckas inte längre med att ändra storlek på bilden med relativt liten bredd till höjden.

_ACP2E-3558 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/9608ca21)_

#### Felaktig konfigurationssökväg för formatkonfiguration för fjärrlagringssökväg

När korrigeringen är klar påverkas den faktiska sökvägskonfigurationen för AWS S3 när du anger en stil för fjärrlagringssökvägen.

_ACP2E-3734 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/df92debe)_

### Ramverk

#### Kompilerar kod för inaktiverad modul.

Den här pull-begäran tar bort inaktiverade moduler innan kodkompilering.

_AC-10933 - [GitHub-problem](https://github.com/magento/magento2/issues/38241) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/39723)_

#### Mallen Magento_Theme title.phtml är ogiltig för PHP 8.2

Den här pull-begäran åtgärdar ett problem när en CMS-sida som skapas med rubriken null, som i PHP 8.x, skickar null till trim(), genererar ett undantag: Föråldrad funktionalitet: trim(): Överför null till parametern #1 ($string) av typen string

_AC-12856 - [GitHub-problem](https://github.com/magento/magento2/issues/39092) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/39398)_

#### När vi använder fillagring för låsleverantören får vi en ständigt växande katalog med filer utan att någon rensning görs

Dragbegäran innehåller ett nytt cron-jobb som körs en gång om dagen och söker efter låsfiler som inte har ändrats de senaste 24 timmarna och som därför kan tas bort på ett säkert sätt. Detta håller innehållet i katalogen med låsfiler under kontroll.
Detta cron-jobb kommer endast att köra något när låsprovidern är konfigurerad att använda filer, inte när någon av de andra används (databas - standard, zookeeper eller cache)

_AC-13367 - [GitHub-problem](https://github.com/magento/magento2/issues/39369) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/39372)_

#### [Issue] Cleanup: använd inte ett void-returvärde från metodanrop.

Den här PR:en rensar lite. Ibland anropade vi metoder som inte returnerade något (void) och sedan använde vi det resultatvärdet. Det behövs verkligen inte.

_AC-13664 - [GitHub-problem](https://github.com/magento/magento2/issues/39524) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/39516)_

#### [Problem] [PHPDOC] Korrigera felaktig bild för Magento\Framework\Message\ManagerInterface

Denna PR korrigerar det felaktiga fotot för \Magento\Framework\Message\ManagerInterface och tar bort alla duplicerade foton i \Magento\Framework\Message\Manager (använd arvssyntax).

_AC-14312 - [GitHub-problem](https://github.com/magento/magento2/issues/39593) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/39153)_

#### Borttagen betaversionsstabilitet från Composer.json

Borttagen betaversionsstabilitet från Composer.json

_AC-14450 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/1cbbf187)_

#### allow_parallel_generation ska anges via systemvariabeln

Efter korrigeringen kan miljövariabeln &quot;MAGENTO_DC_CACHE_ALLOW_PARALLEL_GENERATION&quot; användas för att ställa in konfigurationen &quot;allow_parallel_generation&quot;.

_ACP2E-3673 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/b12ffe36)_

#### [Cloud] Om du ändrar tabellkolumntyp från Int till Decimal med filen db_schema.xml i Magento 2 uppstår fel

Det går inte att ändra kolumndatatypen korrekt. Tidigare uppstod ett fel: Attributet identity är inte tillåtet.

_ACP2E-3709 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/df92debe)_

#### Stöd för nya valutor (XCG) i Adobe

Karibien Guilder (XCG) läggs till i valutalistan.

_ACP2E-3790 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/520f9e30)_

### GraphQL

#### GraphQL-svar för orderplacering innehåller inte något undantagsmeddelande

Återställde tidigare ändring som returnerade fel i ett annat format. Nu returneras potentiella fel på ett konsekvent sätt, inte GraphQL-schemat. Detta bör läggas till som känd BIC, godkänd av PM i AVS2E-3399

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

### Importera/exportera

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

### Lager/MSI

#### Butiksplockning respekterar inte maximal sökradie när adressen ändras vid utcheckning

Den förvalda butiken i&quot;Plocka i butik&quot; uppdateras om leveransadressen ändras. Tidigare ändrades inte butiken när den väl hade valts ut, även om den nya leveransadressen inte ligger inom den valda butikens radie

_ACP2E-3728 - [GitHub-kodbidrag](https://github.com/magento/inventory/commit/07620383)_

### Beställning

#### Det går inte att returnera null för fältet \&amp;quot;AppliedCoupon.code\&amp;quot; oväntat fel

_AC-14484 - [GitHub-problem](https://github.com/magento/magento2/issues/39841) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/97b2ea42)_

#### [Cloud] Vissa infogade JavaScript fungerar inte efter uppgradering till magento 2.4.6-p7

Om du klickar på knappen &quot;Ta bort&quot; i &quot;Lägg till i order av SKU&quot; i administratören tas SKU:n bort. Tidigare togs SKU inte bort när du klickade på knappen&quot;Ta bort&quot; i&quot;Lägg till i order av SKU&quot;.

_ACP2E-3515_

#### serialiserade data för presentkort är inkonsekventa i registret sales_order

presentkortsdata i tabellen sales_order är nu korrekt serialiserade. Tidigare serialiserades den varje gång ordern uppdaterades.

_ACP2E-3662_

### Order, pris

#### Administratören visar felaktig valutasymbol när retur skapas

I en flerwebbplatskonfiguration med olika valutor (EUR/USD/GBP) visas nu rätt valutasymbol på sidan för val av returprodukt i administratören. Tidigare visades standardvalutasymbolen.

_ACP2E-3658 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/df92debe)_

### Andra utvecklingsverktyg

#### Fel i hjälpmedel för Lightroom

Nu skickas System med tillgänglighetspoängen 100

_AC-12783 - [GitHub-problem](https://github.com/magento/magento2/issues/39054) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/39164)_

#### Inaktivera captcha storefront-konfigurationen fortfarande läsa in captcha js-filer

Systemet läser nu inte in captcha js-filer när vi inaktiverade captcha för storefront

_AC-14267 - [GitHub-problem](https://github.com/magento/magento2/issues/32987) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/39154)_

### Paketering

#### [Paketering] Korrigera magento/magento-coding-standard-beroende+ page-builder

_ACPLTSRV-6383_

### Betalningar

#### [Problem] Åtgärda offlinefakturainhämtning (404)

Det åtgärdar 404-sidesfelet när fakturor hämtas för offlinebetalningsmetoder från Magento-administratören

_AC-13336 - [GitHub-problem](https://github.com/magento/magento2/issues/39298) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/39297)_

### Prestanda

#### Modulen Kategoribehörigheter förhindrar eventuellt cachelagring

Externa styrenheter har nu cachelagrats korrekt med kundsegment

_ACP2E-3721_

### Produkt

#### Produktsamling - addMediaGalleryData anropar getSize när samlingen läses in (Kan använda count för att undvika en extra DB-fråga)

Denna PR reducerar det extra frågeanropet med count() om produktsamlingen redan har lästs in när Product Graphql anropas med fältet media_gallery.

_AC-13055 - [GitHub-problem](https://github.com/magento/magento2/issues/39111) - [GitHub-kodbidrag](https://github.com/magento/magento2/pull/39681)_

#### [2.4.8] Inga återanrop hittades för cron job catalog_product_alert

_AC-14494 - [GitHub-problem](https://github.com/magento/magento2/issues/39800) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/1bc2d6d0)_

#### Långsam fråga körs när produktwidgeten inkluderas via pagebuilder

Frågan för att skapa produktwidgetar, inklusive produkt-SKU:er, är optimerad.

_ACP2E-3449 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/df92debe)_

#### Produktbilder som inte ändrar storlek när de läggs till som en konfigurerbar produkt

Tidigare var de bilder som lades till via konfigurationer på adminpanelen inte lika med den maximala överföringsstorleksgränsen, vilket kunde leda till inkonsekvenser och hanteringsproblem. Nu har en korrigering implementerats för att säkerställa att storleken på bilderna automatiskt ändras under överföringen så att de uppfyller den maximala storleksgränsen, vilket effektiviserar processen och bevarar systemstandarderna.

_ACP2E-3504 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/df92debe)_

### Leverans

#### Dokumentet bör uppdateras för % implementering som inte är korrekt i det officiella dokumentet

Enheten för DHL Rest API-stöd har uppdaterats

_AC-14507_

#### [DHL]-Hantera valfria dimensioner i inställningarna för normal storlek och prisvarians mellan REST- och XML-API-integreringar

_AC-14601 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/1e3bde4c)_

#### Ett undantag uppstod när UPS-etiketten skapades

Fast varning: Konvertering från matris till sträng när UPS-etiketten skapas

_ACP2E-3676 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/b12ffe36)_

### Mellanlagring och förhandsvisning

#### Om du förhandsgranskar en schemalagd uppdatering öppnas den första butiksvyn i alfabetisk ordning i stället för butiksvyn

Före korrigeringen öppnas förhandsgranskningen av en schemalagd uppdatering i den första butiksvyn i alfabetisk ordning i stället för i den tilldelade butiksvyn.
Efter korrigeringen öppnas nu förhandsgranskningen korrekt i butiksvyn som tilldelats till CMS-blockstagguppdateringen.

_ACP2E-3671 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/b12ffe36)_

#### Staging_apply_version Kron behavior issue - special_price ignore

Efter korrigeringen beräknas offertsummorna om efter ändring av specialpris per schemalagd produktuppdatering.

_ACP2E-3674_

### Moms

#### Momsbeloppet uppdateras inte när en presentbrytning tas bort från vagnen

_AC-14637_
