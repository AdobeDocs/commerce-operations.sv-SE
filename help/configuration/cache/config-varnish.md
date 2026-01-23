---
title: Konfigurera och använda engelska
description: Lär dig hur du konfigurerar och använder lack-cachning för Adobe Commerce. Upptäck HTTP-acceleration, fillagring och prestandaoptimeringstekniker.
feature: Configuration, Cache
exl-id: 57614878-e349-43bb-b22b-1aa321907be1
source-git-commit: 6896d31a202957d7354c3dd5eb6459eda426e8d7
workflow-type: tm+mt
source-wordcount: '1042'
ht-degree: 0%

---

# Konfigurera lack

[Avvikande cacheminne](https://varnish-cache.org) är en webbprogramaccelerator med öppen källkod (kallas även _HTTP-accelerator_ eller _cachelagring av HTTP-proxy_). I Finish lagras (eller cachelagrar) filer eller fragment av filer i minnet, vilket gör att Varnish kan minska svarstiden och bandbreddsanvändningen för framtida, likvärdiga begäranden. Till skillnad från webbservrar som Apache och nginx har Varnish utformats för att endast användas med HTTP-protokollet.

[Systemkrav](../../installation/system-requirements.md) visar vilka versioner av engelska som stöds.

>[!WARNING]
>
>Vi _rekommenderar starkt_ att du använder lack i produktionen. Den inbyggda helsidescachningen, antingen för filsystemet eller [databasen](https://developer.adobe.com/commerce/php/development/cache/partial/database-caching/), är mycket långsammare än för Varnish, och Varnish är utformat för att accelerera HTTP-trafiken.

Mer information om lack finns i:

- [Den stora svartvita bilden](https://www.varnish-cache.org/docs/trunk/users-guide/intro.html)
- [Alternativ för avslutad start](https://www.varnish-cache.org/docs/trunk/reference/varnishd.html#ref-varnishd-options)
- [Prestanda för lack och webbplats](https://www.varnish-cache.org/docs/trunk/users-guide/performance.html#users-performance)

## Topologidiagram för lack

Följande bild visar en grundläggande vy av lack i din Commerce topologi.

![Grundläggande lack-diagram](../../assets/configuration/varnish-basic.png)

I föregående bild resulterar användarens HTTP-begäran över Internet i många begäranden om CSS, HTML, JavaScript och bilder (kallas tillsammans för _resurser_). Finska sitter framför webbservern och proxiderar dessa begäranden till webbservern.

Efterhand som webbservern returnerar resurser lagras cachelagrade resurser i svenska. Efterföljande förfrågningar om dessa resurser besvaras av Varnish (vilket innebär att förfrågningarna inte når webbservern). Finska returnerar cachelagrat innehåll extremt snabbt. Resultatet blir snabbare svarstider för att skicka tillbaka innehållet till användarna och ett reducerat antal förfrågningar som måste uppfyllas av Commerce.

Assets som cachas av Varnish förfaller vid ett konfigurerbart intervall eller ersätts av senare versioner av samma resurser. Du kan även rensa cachen manuellt med hjälp av Admin eller kommandot [`magento cache:clean`](../cli/manage-cache.md#clean-and-flush-cache-types).

## Processöversikt

I det här avsnittet beskrivs hur du initialt installerar Varnish med en minimal uppsättning parametrar och testar att det fungerar. Exportera sedan en lack-konfiguration från Commerce Admin och testa den igen.

Processen kan sammanfattas enligt följande:

1. Installera Varnish och testa det genom att gå till en Commerce-sida för att se om du får HTTP-svarshuvuden som anger att Varnish fungerar.
1. Installera Commerce och använd administratören för att skapa en lack-konfigurationsfil.
1. Ersätt den befintliga konfigurationsfilen för lack med den som genererats av administratören.
1. Testa allting igen.

   Om det inte finns något i katalogen `<magento_root>/var/page_cache` har du konfigurerat Varnish med Commerce!

>[!NOTE]
>
>- Förutom där det anges måste du ange alla kommandon som beskrivs i det här avsnittet som en användare med `root`-behörighet.
>
>- Det här avsnittet är skrivet för lack i CentOS och Apache 2.4. Om du konfigurerar lack i en annan miljö kan vissa kommandon vara annorlunda. Mer information finns i dokumentationen för Varnish.

## Kända fel

Vi känner till följande problem med Varnish:

- [lack stöder inte SSL](https://www.varnish-cache.org/docs/3.0/phk/ssl.html)

  Alternativt kan du använda SSL-avslutning eller en SSL-avslutningsproxy.

- Om du tar bort innehållet i katalogen `<magento_root>/var/cache` manuellt måste du starta om lack.

- Möjligt fel vid installation av Commerce:

  ```
  Error 503 Service Unavailable
  Service Unavailable
  XID: 303394517
  Varnish cache server
  ```

  Om det här felet uppstår redigerar du `default.vcl` och lägger till en timeout i `backend`-instansen enligt följande:

  ```conf
  backend default {
      .host = "127.0.0.1";
      .port = "8080";
      .first_byte_timeout = 600s;
  }
  ```

## Översikt över cachning i lack

Cachelagring i lack fungerar med Commerce:

- [`nginx.conf.sample`](https://github.com/magento/magento2/blob/2.4/nginx.conf.sample) från Magento 2 GitHub-databasen
- `.htaccess` distribuerad konfigurationsfil för Apache som tillhandahålls med Commerce
- `default.vcl`-konfiguration för lack genererad med [Admin](../cache/configure-varnish-commerce.md)

>[!INFO]
>
>Det här avsnittet omfattar endast standardalternativen i den föregående listan. Det finns många andra sätt att konfigurera cachelagring i komplexa scenarier (till exempel med hjälp av ett leveransnätverk). Dessa metoder ligger utanför den här guidens räckvidd.

På den första webbläsarbegäran levereras cachelagrade resurser till klientwebbläsaren från Varnish och cachelagras i webbläsaren.

Dessutom används en enhetstagg (ETag) för statiska resurser i lack. Med ETag kan du avgöra när statiska filer ändras på servern. Detta innebär att statiska resurser skickas till klienten när de ändras på servern, antingen på en ny begäran från en webbläsare eller när klienten uppdaterar webbläsarens cache, vanligtvis genom att trycka på F5 eller Ctrl+F5.

Mer information finns i följande avsnitt.

## Cachelagring efter webbläsarbegäran

I det här avsnittet används en webbläsarkontroll för att visa hur resurser levereras till webbläsaren i den första begäran och sedan läses in från den lokala webbläsarcachen.

### Första webbläsarbegäran

`nginx.conf.sample` och `.htaccess` innehåller alternativ för klientcachelagring. När den första begäran görs från en webbläsare för ett cachelagrat objekt, skickar Varnish den till klienten.

I bilden nedan visas ett exempel med en webbläsarkontroll:

![Första gången en begäran görs för ett cachelagrat objekt skickas den till webbläsaren &#x200B;](../../assets/configuration/varnish-apache-first-visit.png)

I exemplet ovan visas en begäran för huvudsidan för butiken (`m2_ce_my`). CSS- och JavaScript-resurser cachelagras i klientwebbläsaren.

>[!NOTE]
>
>De flesta statiska resurser har en HTTP 200-statuskod (OK) som anger att resursen hämtades från servern.

### Andra webbläsarbegäran

Om samma webbläsare begär samma sida igen levereras dessa resurser från den lokala webbläsarcachen, vilket visas i följande bild.

![Nästa gång samma objekt begärs, läses resurser in från den lokala webbläsarcachen](../../assets/configuration/varnish-apache-second-visit.png)

Observera skillnaden i svarstid mellan den första och den andra begäran. Även här har statiska resurser en 200-svarskod (OK) eftersom de levereras från det lokala cacheminnet för första gången.

## Hur Commerce använder Etag

I följande exempel visas svarshuvuden för en viss statisk resurs.

![ETag gör det enklare att avgöra om en statisk resurs har ändrats eller inte](../../assets/configuration/varnish-etag.png)

`calendar.css` har ett ETag-svarshuvud, vilket innebär att CSS-filen i klientwebbläsaren kan jämföras med den på servern.

Dessutom returneras statiska resurser med en HTTP-statuskod på 304 (inte ändrad), vilket visas i bilden nedan.

![HTTP 304-svarskoden (inte ändrad) anger att den statiska resursen i det lokala cache-minnet är densamma som på servern](../../assets/configuration/varnish-304.png)

304-statuskoden inträffar eftersom användaren ogiltigförklarade sin lokala cache och innehållet på servern inte ändrades. På grund av 304-statuskoden överförs inte den statiska resursen _content_; bara HTTP-huvuden hämtas till webbläsaren.

Om innehållet ändras på servern hämtar klienten den statiska resursen med en HTTP 200-statuskod (OK) och en ny ETag.

