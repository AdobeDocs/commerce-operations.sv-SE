---
title: Konfigurera och använda engelska
description: Förstå hur lack lagrar filer och förbättrar HTTP-trafiken.
exl-id: 57614878-e349-43bb-b22b-1aa321907be1
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '1079'
ht-degree: 0%

---

# Konfigurera lack

[Finska cache] är en webbprogramsaccelerator med öppen källkod (kallas även _HTTP-accelerator_ eller _cachelagring av omvänd HTTP-proxy_). I Finish lagras (eller cachelagrar) filer eller fragment av filer i minnet, vilket gör att Varnish kan minska svarstiden och bandbreddsanvändningen för framtida, likvärdiga begäranden. Till skillnad från webbservrar som Apache och nginx har Varnish utformats för att endast användas med HTTP-protokollet.

Commerce 2.4.2 har testats med Varnish 6.4. Commerce 2.4.x är kompatibel med Varnish 6.x

>[!WARNING]
>
>Vi _starkt rekommendera_ du använder varnish i produktionen. Den inbyggda helsidescachningen - för filsystemet eller [databas]—är mycket långsammare än varnish, och varnish är utformat för att accelerera HTTP-trafiken.

Mer information om lack finns i:

- [The Big Varnish Picture]
- [Alternativ för avslutning av lack]
- [Prestanda för lack och webbplatser]

## Topologidiagram för lack

Följande bild visar en grundläggande vy av lack i din Commerce-topologi.

![Basic Varnish-diagram](../../assets/configuration/varnish-basic.png)

I föregående bild resulterar användarens HTTP-begäran över Internet i många begäranden om CSS, HTML, JavaScript och bilder (kallas tillsammans för _resurser_). Finska sitter framför webbservern och proxiderar dessa begäranden till webbservern.

Efterhand som webbservern returnerar resurser lagras cachelagrade resurser i svenska. Efterföljande förfrågningar om dessa resurser besvaras av Varnish (vilket innebär att förfrågningarna inte når webbservern). Finska returnerar cachelagrat innehåll extremt snabbt. Resultatet blir snabbare svarstider för att återsända innehållet till användarna och ett minskat antal förfrågningar som måste uppfyllas av Commerce.

Resurser som cachas av Varnish förfaller vid ett konfigurerbart intervall eller ersätts av senare versioner av samma resurser. Du kan även rensa cacheminnet manuellt antingen med hjälp av Admin eller [`magento cache:clean`](../cli/manage-cache.md#clean-and-flush-cache-types) -kommando.

## Processöversikt

I det här avsnittet beskrivs hur du initialt installerar Varnish med en minimal uppsättning parametrar och testar att det fungerar. Exportera sedan en lack-konfiguration från Commerce Admin och testa den igen.

Processen kan sammanfattas enligt följande:

1. Installera lack och testa den på en Commerce-sida för att se om du får HTTP-svarshuvuden som anger att Varnish fungerar.
1. Installera Commerce-programvaran och använd administratören för att skapa en lack-konfigurationsfil.
1. Ersätt den befintliga konfigurationsfilen för lack med den som genererats av administratören.
1. Testa allting igen.

   Om det inte finns något i din `<magento_root>/var/page_cache` har du konfigurerat engelska med Commerce!

>[!NOTE]
- Förutom där det anges måste du ange alla kommandon som beskrivs i det här avsnittet som en användare med `root` behörighet.
- Det här avsnittet är skrivet för lack i CentOS och Apache 2.4. Om du konfigurerar lack i en annan miljö kan vissa kommandon vara annorlunda. Mer information finns i dokumentationen för Varnish.


## Kända fel

Vi känner till följande problem med Varnish:

- [Varnish stöder inte SSL]

   Alternativt kan du använda SSL-avslutning eller en SSL-avslutningsproxy.

- Om du tar bort innehållet i `<magento_root>/var/cache` måste du starta om Varnish.

- Möjligt fel vid installation av Commerce:

   ```terminal
   Error 503 Service Unavailable
   Service Unavailable
   XID: 303394517
   Varnish cache server
   ```

   Om det här felet uppstår kan du redigera `default.vcl` och lägga till en timeout i `backend` stanza enligt följande:

   ```conf
   backend default {
       .host = "127.0.0.1";
       .port = "8080";
       .first_byte_timeout = 600s;
   }
   ```

## Översikt över cachning i lack

Cachelagring av lack fungerar tillsammans med Commerce med:

- [`nginx.conf.sample`](https://github.com/magento/magento2/blob/2.4/nginx.conf.sample) från GitHub-databasen Magento 2
- `.htaccess` distribuerad konfigurationsfil för Apache som tillhandahålls med Commerce
- `default.vcl` konfiguration för lack som genererats med [Administratör](../cache/configure-varnish-commerce.md)

>[!INFO]
Det här avsnittet omfattar endast standardalternativen i föregående lista. Det finns många andra sätt att konfigurera cachelagring i komplexa scenarier (till exempel med hjälp av ett leveransnätverk). Dessa metoder ligger utanför den här handbokens räckvidd.

På den första webbläsarbegäran levereras cachelagrade resurser till klientwebbläsaren från Varnish och cachelagras i webbläsaren.

Dessutom används en enhetstagg (ETag) för statiska resurser i lack. Med ETag kan du avgöra när statiska filer ändras på servern. Detta innebär att statiska resurser skickas till klienten när de ändras på servern, antingen på en ny begäran från en webbläsare eller när klienten uppdaterar webbläsarens cache, vanligtvis genom att trycka på F5 eller Ctrl+F5.

Mer information finns i följande avsnitt.

## Cachelagring efter webbläsarbegäran

I det här avsnittet används en webbläsarkontroll för att visa hur resurser levereras till webbläsaren i den första begäran och sedan läses in från den lokala webbläsarcachen.

### Första webbläsarbegäran

`nginx.conf.sample` och `.htaccess` innehåller alternativ för klientcachelagring. När den första begäran görs från en webbläsare för ett cachelagrat objekt, skickar Varnish den till klienten.

I bilden nedan visas ett exempel med en webbläsarkontroll:

![Första gången en begäran görs för ett cachelagrat objekt skickas det till webbläsaren av Varnish](../../assets/configuration/varnish-apache-first-visit.png)

I exemplet ovan visas en begäran för huvudsidan för butiken (`m2_ce_my`). CSS- och JavaScript-resurser cachelagras i klientwebbläsaren.

>[!NOTE]
De flesta statiska resurser har en HTTP 200-statuskod (OK) som anger att resursen hämtades från servern.

### Andra webbläsarbegäran

Om samma webbläsare begär samma sida igen levereras dessa resurser från den lokala webbläsarcachen, vilket visas i följande bild.

![Nästa gång samma objekt begärs, läses resurser in från den lokala webbläsarens cache](../../assets/configuration/varnish-apache-second-visit.png)

Observera skillnaden i svarstid mellan den första och den andra begäran. Även här har statiska resurser en 200-svarskod (OK) eftersom de levereras från det lokala cacheminnet för första gången.

## Så här använder Commerce Etag

I följande exempel visas svarshuvuden för en viss statisk resurs.

![ETag gör det enklare att avgöra om en statisk resurs har ändrats eller inte](../../assets/configuration/varnish-etag.png)

`calendar.css` har ett ETag-svarshuvud, vilket innebär att CSS-filen i klientwebbläsaren kan jämföras med den på servern.

Dessutom returneras statiska resurser med en HTTP-statuskod på 304 (inte ändrad), vilket visas i bilden nedan.

![HTTP 304-svarskoden (inte ändrad) anger att den statiska resursen i det lokala cacheminnet är densamma som på servern](../../assets/configuration/varnish-304.png)

304-statuskoden inträffar eftersom användaren ogiltigförklarade sin lokala cache och innehållet på servern inte ändrades. På grund av 304-statuskoden är den statiska resursen _innehåll_ inte överförs, bara HTTP-huvuden hämtas till webbläsaren.

Om innehållet ändras på servern hämtar klienten den statiska resursen med en HTTP 200-statuskod (OK) och en ny ETag.

<!-- Link Definitions -->

[databas]: https://developer.adobe.com/commerce/php/development/cache/partial/database-caching/
[The Big Varnish Picture]: https://www.varnish-cache.org/docs/trunk/users-guide/intro.html
[Finska cache]: https://varnish-cache.org
[Alternativ för avslutning av lack]: https://www.varnish-cache.org/docs/trunk/reference/varnishd.html#ref-varnishd-options
[Prestanda för lack och webbplatser]: https://www.varnish-cache.org/docs/trunk/users-guide/performance.html#users-performance
[Varnish stöder inte SSL]: https://www.varnish-cache.org/docs/3.0/phk/ssl.html
