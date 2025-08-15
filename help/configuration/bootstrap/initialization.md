---
title: Programinitiering och bootstrap
description: Läs om initiering och bootstrap-logik för Commerce.
feature: Configuration, Install, Media
exl-id: 46d1ffc0-7870-4dd1-beec-0a9ff858ab62
source-git-commit: 403a5937561d82b02fd126c95af3f70b0ded0747
workflow-type: tm+mt
source-wordcount: '792'
ht-degree: 0%

---

# Översikt över initiering och bootstrap

Följande åtgärder implementeras i [pub/index.php][index] för att köra Commerce-programmet:

- Inkludera [app/bootstrap.php][bootinitial], som utför viktiga initieringsrutiner som felhantering, initiering av automatisk inläsare, inställning av profileringsalternativ och inställning av standardtidszon.
- Skapa en instans av [\Magento\Framework\App\Bootstrap.php][bootstrap] <!-- It requires initialization parameters to be specified in constructor. Normally, the $_SERVER super-global variable is supposed to be passed there. -->
- Skapa en programinstans i Commerce: [\Magento\Framework\AppInterface][app-face]
- Kör Commerce

## Bootstrap körningslogik

[Bootstrap-objektet][bootinitial] använder följande algoritm för att köra Commerce-programmet:

1. Initierar felhanteraren.
1. Skapar [objekthanteraren][object] och grundläggande delade tjänster som används överallt och som påverkas av miljön. Miljöparametrarna injiceras korrekt i dessa objekt.
1. Kontrollerar att underhållsläget _inte_ är aktiverat, annars avslutas underhållsläget.
1. Kontrollerar att Commerce-programmet är installerat, annars avslutas det.
1. Startar Commerce.

   Alla undantag som inte fångas upp när programmet startas skickas automatiskt tillbaka till Commerce i metoden `catchException()`, som du kan använda för att hantera undantaget. Den senare måste returnera antingen `true` eller `false`:

   - Om `true`: Commerce hanterade ett undantag. Du behöver inte göra något annat.
   - Om `false`: (eller något annat tomt resultat) hanteras inte undantaget av Commerce. Bootstrap-objektet utför standardunderrutinen för undantagshantering.

1. Skickar det svar som anges av programobjektet.

   >[!INFO]
   >
   >Påståendena om att Commerce-programmet är installerat och inte i underhållsläge är standardbeteendet för klassen `\Magento\Framework\App\Bootstrap`. Du kan ändra det med hjälp av ett startpunktsskript när du skapar bootstrap-objektet.

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

Bootstrap-objektet anger hur Commerce-programmet hanterar ej infångade undantag enligt följande:

- I [utvecklarläget](../bootstrap/application-modes.md#developer-mode) visas undantaget i befintligt skick.
- I vilket annat läge som helst försöker logga undantag och visa ett generiskt felmeddelande.
- Avslutar Commerce med felkoden `1`

## Startpunktsapplikationer

Vi har följande startpunktsprogram (d.v.s. program som definieras av Commerce och som används av webbservern som katalogindex):

### HTTP-startpunkt

[\Magento\Framework\App\Http][http] fungerar så här:

1. Bestämmer [programområdet](https://developer.adobe.com/commerce/php/architecture/modules/areas/).
1. Startar frontkontrollenheten och routningssystemen för att hitta och köra en kontrollenhetsåtgärd.
1. Använder ett HTTP-svarsobjekt för att returnera resultat från kontrollenhetsåtgärden.
1. Felhantering (i följande prioritetsordning):

   1. Om du använder [utvecklarläget](../bootstrap/application-modes.md#developer-mode):
      - Om Commerce inte är installerat dirigerar du om till installationsguiden.
      - Om Commerce-programmet är installerat visas ett fel och HTTP-statuskoden 500 (Internt serverfel).
   1. Om Commerce-programmet är i underhållsläge visar du en användarvänlig landningssida för&quot;Service Unavailable&quot; med HTTP-statuskod 503 (Service Unavailable).
   1. Om Commerce-programmet _inte_ är installerat dirigerar du om till installationsguiden.
   1. Om sessionen är ogiltig dirigerar du om till hemsidan.
   1. Om det finns något annat programinitieringsfel visar du en användarvänlig sida med statuskoden HTTP 404 (Hittades inte).
   1. Vid andra fel visar du en användarvänlig&quot;Service Unavailable&quot;-sida med HTTP-svar 503 och genererar en felrapport och visar dess ID på sidan.

### Statisk resursinmatningspunkt

[\Magento\Framework\App\StaticResource][static-resource] är ett program för att hämta statiska resurser (till exempel CSS, JavaScript och bilder). Den skjuter upp alla åtgärder med en statisk resurs tills resursen begärs.

>[!INFO]
>
>Startpunkten för statiska vyfiler används inte i [produktionsläge](application-modes.md#production-mode) för att undvika potentiella avbrott på servern. I produktionsläget förväntar sig Commerce-programmet att alla nödvändiga resurser finns i katalogen `<your Commerce install dir>/pub/static`.

I standardläge eller utvecklarläge omdirigeras en begäran om en statisk resurs som inte finns till den statiska startpunkten enligt omskrivningsreglerna som anges av rätt `.htaccess`.
När begäran omdirigeras till startpunkten, tolkar Commerce-programmet den begärda URL:en baserat på hämtade parametrar och hittar den begärda resursen.

- I läget [developer](application-modes.md#developer-mode) returneras filens innehåll så att det returnerade innehållet är uppdaterat varje gång resursen begärs.
- I [standardläget](application-modes.md#default-mode) publiceras den hämtade resursen så att den kan nås av den tidigare begärda URL:en.

  Alla framtida förfrågningar om den statiska resursen behandlas av servern på samma sätt som statiska filer, dvs. utan att ta med startpunkten. Om det är nödvändigt att synkronisera publicerade filer med ursprungliga filer, bör katalogen `pub/static` tas bort. Därför publiceras filerna automatiskt på nytt med nästa begäran.

### Startpunkt för medieresurs

[Magento\MediaStorage\App\Media][media] hämtar medieresurser (d.v.s. alla filer som överförts till medielagring) från databasen. Den används när databasen har konfigurerats som en medielagring.

`\Magento\Core\App\Media` försöker hitta mediefilen i den konfigurerade databaslagringen och skriva den i katalogen `pub/static` och sedan returnera innehållet. Vid fel returneras HTTP 404-statuskoden (Hittades inte) i huvudet utan innehåll.

<!-- Link Definitions -->

[app-face]: https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/AppInterface.php
[bootinitial]: https://github.com/magento/magento2/tree/2.4/app/bootstrap.php
[bootstrap]: https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/App/Bootstrap.php
[http]: https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/App/Http
[index]: https://github.com/magento/magento2/tree/2.4/pub/index.php
[media]: https://github.com/magento/magento2/tree/2.4/app/code/Magento/MediaStorage/App/Media.php
[object]: https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/ObjectManager
[static-resource]: https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/App/StaticResource.php
