---
title: Programinitiering och bootstrap
description: Läs om initierings- och bootstrap-logik för Commerce-programmet.
source-git-commit: 5c0d285717a79d654af769cb734ec385d2d4046f
workflow-type: tm+mt
source-wordcount: '866'
ht-degree: 0%

---


# Översikt över initiering och bootstrap

Följande åtgärder implementeras i för att köra Commerce-programmet [pub/index.php][index]:

- Inkludera [app/bootstrap.php][bootinitial], som utför viktiga initieringsrutiner som felhantering, initiering av automatisk inläsare, inställning av profileringsalternativ och inställning av standardtidszon.
- Skapa en instans av [\Magento\Framework\App\Bootstrap.php][bootstrap] <!-- It requires initialization parameters to be specified in constructor. Normally, the $_SERVER super-global variable is supposed to be passed there. -->
- Skapa en instans av ett Commerce-program: [\Magento\Framework\AppInterface][app-face]
- Kör handel

## Bootstrap-körningslogik

[Bootstrap-objektet][bootinitial] använder följande algoritm för att köra Commerce-programmet:

1. Initierar felhanteraren.
1. Skapar [objekthanterare][object] och grundläggande delade tjänster som används överallt och påverkas av miljön. Miljöparametrarna injiceras korrekt i dessa objekt.
1. Kontrollerar att underhållsläget är _not_ aktiverad; annars avslutas.
1. Kontrollerar att Commerce-programmet är installerat, annars avslutas.
1. Startar Commerce-programmet.

   Alla undantag som inte fångas upp när programmet startas skickas automatiskt tillbaka till Commerce i `catchException()` som du kan använda för att hantera undantaget. Den senare måste returnera antingen `true` eller `false`:

   - If `true`: Ett undantag har hanterats i Commerce. Du behöver inte göra något annat.
   - If `false`: (eller något annat tomt resultat) Handeln behandlade inte undantaget. Bootstrap-objektet utför standardunderrutinen för undantagshantering.

1. Skickar det svar som anges av programobjektet.

   >[!INFO]
   >
   >Påståendena om att Commerce-programmet är installerat och inte i underhållsläge är standardbeteendet för `\Magento\Framework\App\Bootstrap` klassen. Du kan ändra det med hjälp av ett startpunktsskript när du skapar bootstrap-objektet.

   Exempel på ett startpunktsskript som ändrar bootstrap-objektet:

   ```php
   <?php
   use Magento\Framework\App\Bootstrap;
   require __DIR__ . '/app/bootstrap.php';
   
   $params = $_SERVER;
   $params[Bootstrap::PARAM_REQUIRE_MAINTENANCE] = true; // default false
   $params[Bootstrap::PARAM_REQUIRE_IS_INSTALLED] = false; // default true
   $bootstrap = Bootstrap::create(BP, $params);
   
   /** @var \Magento\Framework\App\Http $app */
   $app = $bootstrap->createApplication('Magento\Framework\App\Http');
   $bootstrap->run($app);
   ```

## Standardundantagshantering

Bootstrap-objektet anger hur programmet Commerce hanterar ej infångade undantag enligt följande:

- I [utvecklarläge](../bootstrap/application-modes.md#developer-mode), visar undantaget i befintligt skick.
- I vilket annat läge som helst försöker logga undantag och visa ett generiskt felmeddelande.
- Avbryter handel med felkod `1`

## Startpunktsapplikationer

Vi har följande startpunktsprogram (d.v.s. program som definieras av Commerce och som används av webbservern som ett katalogindex):

### HTTP-startpunkt

[\Magento\Framework\App\Http][http] fungerar enligt följande:

1. Bestämmer [programområde](https://developer.adobe.com/commerce/php/architecture/modules/areas/).
1. Startar frontkontrollenheten och routningssystemen för att hitta och köra en kontrollenhetsåtgärd.
1. Använder ett HTTP-svarsobjekt för att returnera resultat från kontrollenhetsåtgärden.
1. Felhantering (i följande prioritetsordning):

   1. Om du använder [utvecklarläge](../bootstrap/application-modes.md#developer-mode):
      - Om Commerce-programmet inte är installerat dirigerar du om till installationsguiden.
      - Om Commerce-programmet är installerat visas ett fel och HTTP-statuskod 500 (Internt serverfel).
   1. Om Commerce-programmet är i underhållsläge, visa en användarvänlig landningssida för&quot;Service Unavailable&quot; med HTTP-statuskod 503 (Tjänsten är inte tillgänglig).
   1. Om Commerce-programmet är _not_ installerat, omdirigera till installationsguiden.
   1. Om sessionen är ogiltig dirigerar du om till hemsidan.
   1. Om det finns något annat programinitieringsfel visar du en användarvänlig sida med statuskoden HTTP 404 (Hittades inte).
   1. Vid andra fel visar du en användarvänlig&quot;Service Unavailable&quot;-sida med HTTP-svar 503 och genererar en felrapport och visar dess ID på sidan.

### Statisk resursinmatningspunkt

[\Magento\Framework\App\StaticResource][static-resource] är ett program för att hämta statiska resurser (till exempel CSS, JavaScript och bilder). Den skjuter upp alla åtgärder med en statisk resurs tills resursen begärs.

>[!INFO]
>
>Startpunkten för statiska vyfiler används inte i [produktionsläge](application-modes.md#production-mode) för att undvika potentiella explosioner på servern. I produktionsläget förväntar sig Commerce-programmet att alla nödvändiga resurser finns i `<your Commerce install dir>/pub/static` katalog.

I standardläge eller utvecklarläge omdirigeras en begäran om en statisk resurs som inte finns till den statiska startpunkten enligt de omskrivningsregler som anges av lämplig `.htaccess`.
När begäran omdirigeras till startpunkten, tolkar Commerce-programmet den begärda URL:en baserat på hämtade parametrar och hittar den begärda resursen.

- I [utvecklare](application-modes.md#developer-mode) i , returneras filens innehåll så att det returnerade innehållet är uppdaterat varje gång resursen begärs.
- I [standard](application-modes.md#default-mode) i publiceras den hämtade resursen så att den kan nås av den tidigare begärda URL:en.

   Alla framtida förfrågningar om den statiska resursen behandlas av servern på samma sätt som statiska filer. dvs. utan att ta med startpunkten. Om det är nödvändigt att synkronisera publicerade filer med de ursprungliga filerna `pub/static` Katalogen bör tas bort. Därför publiceras filerna automatiskt på nytt vid nästa begäran.

### Startpunkt för medieresurs

[Magento\MediaStorage\App\Media][media] hämtar medieresurser (dvs. alla filer som överförts till medielagring) från databasen. Den används när databasen har konfigurerats som en [medielagring](https://glossary.magento.com/media-storage).

`\Magento\Core\App\Media` försöker hitta mediefilen i den konfigurerade databaslagringen och skriva den i `pub/static` och sedan returnera innehållet. Vid fel returneras HTTP 404-statuskoden (Hittades inte) i huvudet utan innehåll.

<!-- Link Definitions -->

[app-face]: https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/AppInterface.php
[bootinitial]: https://github.com/magento/magento2/tree/2.4/app/bootstrap.php
[bootstrap]: https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/App/Bootstrap.php
[http]: https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/App/Http
[index]: https://github.com/magento/magento2/tree/2.4/pub/index.php
[media]: https://github.com/magento/magento2/tree/2.4/app/code/Magento/MediaStorage/App/Media.php
[object]: https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/ObjectManager
[static-resource]: https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/App/StaticResource.php
