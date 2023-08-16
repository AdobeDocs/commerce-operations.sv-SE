---
title: The [!UICONTROL bots] tab
description: Läs mer om [!UICONTROL bots] flik för [!DNL Observation for Adobe Commerce].
exl-id: 741310ca-28fb-4b08-95c7-e8d1fb952018
feature: Configuration, Observability
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '1903'
ht-degree: 0%

---

# The [!UICONTROL bots] tab

På den här fliken finns information om hur du identifierar om och vad [!DNL bots] orsakar webbplatsproblem.

## Översikt över hög nivå [!DNL bots]:

* A [!DNL bot] är ett program som kör återkommande automatiserade uppgifter. Med hjälp av artificiell intelligens och maskininlärningsutveckling kan man [!DNL bots] håller på att förändras. Det finns *bra* [!DNL bots] som hjälper webbplatser genom att crawla och lägga till dem i sökmotorer på Internet. Detta leder till att Internetanvändare vägleds till webbplatsen med sökmotorresultat. A *bra* [!DNL bot] tar vanligtvis hänsyn till gränser som placerats på [!DNL bot] av en `robots.txt` fil eller inställningar i en sökmotorkonsol. Gränser kan begränsa åtkomsten till platsen eller delar av platsen.
* Skadlig [!DNL bots] ignorera `robots.txt` eller så kan de hitta något bra [!DNL bot] via fältet för användaragent för begäran av data för HTTP-begäran. Vissa saker som gör ont [!DNL bots] do:
   * Lägg till inläsning på en webbplats för att neka legitima användare åtkomst till webbplatsen.
   * Rita och återanvänd material utan tillstånd.
   * Registrera falska konton för att översvämma e-posttjänster eller adresser eller omdirigera till andra webbplatser ([!DNL SPAM bots]).
   * Skapa falska vyer ([!DNL Viewbots]).
   * Köp produkter eller biljetter ([!DNL Focused bots]).
* Hantera [!DNL bots]
   * [!DNL Observation for Adobe Commerce] har vyer över [!DNL bot] trafik:
      * Den visar totalt antal icke-cachelagrade [!DNL bot] aktivitet som visar inläsningen som en [!DNL bot] lägger till i en webbplats och när den inläsningen sker.
      * Den visar [!DNL bots] som genererar fel. Vanligtvis om en [!DNL bot] lägger till inläsning som orsakar webbplatsproblem, som [!DNL bot] eller IP-adressen har den högsta felfrekvensen.
      * Det syns [!DNL bot] namn (begär fältvärden för användaragent) och IP-adresser att hantera via:
         * [!DNL Fastly] (hastighetsbegränsande eller [!DNL VCLs] som blockerar IP-adresser, intervall eller [!DNL bots] efter namnvärde).
         * Tillföra bra [!DNL bot] information till `robots.txt field` för att begränsa eller begränsa webbplatsens åtkomst.
         * Hantera [!DNL Bing] eller [!DNL Google bots] genom sökmotorkonsolen.

## [!UICONTROL Experimental Potential Malicious Bots frame]

![Bildruta för experimentella potentiella skadliga starter](../../assets/tools/observation-for-adobe-commerce/experimental-potential-malicious-bots-frame-new.jpg)

The **[!UICONTROL Experimental Potential Malicious Bots frame]** bildrutan består av över 12 separata, komplexa frågor. Den upptäcker skadliga IP-förfrågningssignaturer och sammanställer sedan resultaten, summerar och sorterar dem efter antal i fallande ordning. Frågorna innehåller en mängd datasignaturer av CVE-explosioner och andra skadliga förfrågningar. Även om explosionerna blockeras av säkerhetskorrigeringar/patchar och inte utgör ett hot mot webbplatsen måste begäran fortfarande hanteras av webbplatsen. Antalet förfrågningar kan bli mycket stort på kort tid. Den här bildrutan visar inte totalt antal begäranden från IP-adressen, utan i stället begäranden som har signaler som indikerar att begäran hade misstänkt avsikt.

Kontrollera att trafiken är misstänkt och att den inte kommer från en [!DNL Content Distributed Network] (CDN)-adress som också kan leverera giltiga begäranden. Om förfrågningarna kommer från en CDN IP-adress kontaktar du tjänsteleverantören för att få hjälp med att blockera den misstänkta trafiken via nätverket. Om du behöver blockera adressen eller URL:en för begäran, se [Blockera skadlig trafik för Adobe Commerce på [!DNL Fastly] nivå](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/block-malicious-traffic-for-magento-commerce-on-fastly-level.html) i Adobe Commerce Support Knowledge Base.

## [!UICONTROL Rate of HTTP request per second (top 25) during requested time period]

![Frekvens för HTTP-begäran per sekund (högst 25) under begärd tidsperiod](../../assets/tools/observation-for-adobe-commerce/rate-of-http-request-per-second.jpg)

The **[!UICONTROL Rate of HTTP request per second (top 25) during requested time period]** bildrutan visar de högsta förfrågningarna per sekund-IP-adresser under den valda tidsramen. Om dessa adresser också finns i tabellen ovan kontrollerar du att de inte är CDN-adresser och skadliga och blockerar dem via [!DNL Fastly].

## [!UICONTROL Total Bot traffic by bot name]:

![Total punkttrafik per robotnamn under den valda tidsperioden:](../../assets/tools/observation-for-adobe-commerce/total-bot-traffic-bot-name.png)

The **[!UICONTROL Total Bot traffic by bot name during selected time period]** tabellen innehåller det aggregerade antalet icke-cachelagrade begäranden där [!UICONTROL request_user_agent] fältet har en sträng med [!DNL bots] i värdet. Detta kan vara namngivet [!DNL bot] som [!UICONTROL request_user_agent] fältvärdet kan förfalskas. Värdet under [!UICONTROL Count] -kolumnen är den viktigaste.

## [!UICONTROL Total Bot Traffic by Bot name/IP address]

![Total starttrafik per punktnamn/IP-adress under den valda tidsperioden Hur man blockerar starttrafiken på snabbnivå ELLER hanterar robotar via robots.txt file God praxis för Adobe Commerce robots.txt](../../assets/tools/observation-for-adobe-commerce/best-practices-adobecommerce-robots.png)

The **[!UICONTROL Total Bot Traffic by Bot name/IP address during selected time period How to block bot traffic on Fastly level OR manage bots through your robots.txt file Best practices for Adobe Commerce robots.txt]** tabellen visar samma data som föregående tabell, men lägger till IP-adresser som gör förfrågningar för den namngivna [!DNL bot]. Som illasinnad [!DNL bots] god [!DNL bots]bör IP-adressen/IP-adresserna verifieras via webbplatser som identifierar IP-adresser som ger upphov till missbruk eller via *hora* tjänster eller [!DNL DNS lookups]. Till exempel: [!DNL Google] publicerar sina [[!DNL googlebot] IP-adresser](https://developers.google.com/search/apis/ipranges/googlebot.json) och [!DNL Microsoft] har ett verifieringsverktyg för [[!DNL Bingbots]](https://www.bing.com/webmasters/help/Verify-Bingbot-2195837f).

## [!UICONTROL Graph - Bots with HTTP status errors]

![Diagram - Börjar med HTTP-statusfel under den valda tidsperioden Hur man blockerar starttrafik på snabbnivå ELLER hanterar robotar genom robots.txt-filen God praxis för Adobe Commerce robots.txt](../../assets/tools/observation-for-adobe-commerce/bots-with-http-status-errors.png)

The **[!UICONTROL Graph - Bots with HTTP status errors during selected time period How to block bot traffic on Fastly level OR manage bots through your robots.txt file Best practices for Adobe Commerce robots.txt]** diagram visar fel på [!DNL bots] som deklarerar sig själva i fältet för användaragent för begäran. Det behöver inte innebära att felet orsakas av volymen från [!DNL bot] eller annan trafik. Felen kan vara att [!DNL bot] begär information som inte finns eller som det finns ett annat problem i begäran.

Om det finns en rad fel på IP-adresser under platsinstallationer eller driftavbrott kan de misstänkas för webbplatsproblemet.

## [!UICONTROL Table - IPs that do not identify as bots]

![Tabell - IP:n som inte identifieras som bottar med HTTP-statusfel under den valda tidsperioden Hur man blockerar starttrafiken på snabbnivå ELLER hanterar robotar genom robots.txt-filen God praxis för Adobe Commerce robots.txt ](../../assets/tools/observation-for-adobe-commerce/ips-http-errors.png)

The **[!UICONTROL Table - IPs that do not identify as bots with HTTP status errors during selected time period How to block bot traffic on Fastly level OR manage bots through your robots.txt file Best practices for Adobe Commerce robots.txt]** tabellen visar IP-begäranden med http-statuskoder som inte är 200 och som INTE är självidentifierande som [!DNL bots] i fältet för användaragent för begäran. Dessa IP-adresser kan vara skadliga IP-adresser, särskilt om antalet är högt för den valda tidsperioden.

Om antalet http-statuskoder som inte är 200 är lågt och IP-adressintervallen inte är lika, kanske inte adresserna bidrar till webbplatsproblemen.

## [!UICONTROL Table – Cache Status 'ERROR']

![Tabell - detaljregister för cachestatus &#39;FEL&#39; (vad gör dessa IP-adresser?) Så här blockerar du robottrafiken på snabbnivå ELLER hanterar robotar genom filen robots.txt Best practices for Adobe Commerce robots.txt](../../assets/tools/observation-for-adobe-commerce/cache-status-errors.png)

När IP-adresser genererar en hög frekvens av fel, fråga vad gör de? The **[!UICONTROL Table – Cache Status 'ERROR' detail table (what are these IPs doing?) How to block bot traffic on Fastly level OR manage bots through your robots.txt file Best practices for Adobe Commerce robots.txt]** tabellen visar den begärda URL:en tillsammans med HTTP-statusvärdet för begäranden som har cachestatus [!UICONTROL ERROR] värde. Frekvensen anges av URL:en så att antalet kan vara lågt. Kom ihåg att IP-adressen kan göra tusentals begäranden under den valda tidsperioden. Detta är en vy mot upp till 2 000 begäranden under tidsramen (gränsen för postvisning).

## [!UICONTROL Show 5XX status distribution]

![Visa 5XX-statusfördelning över IP-adresser (de 200 högsta adresserna) Så här blockerar du starttrafiken på snabbnivå ELLER hanterar robotar via robots.txt-filen God praxis för Adobe Commerce robots.txt ](../../assets/tools/observation-for-adobe-commerce/5xx-status.png)

The **[!UICONTROL Show 5XX status distribution across IP addresses (top 200 addresses) How to block bot traffic on Fastly level OR manage bots through your robots.txt file Best practices for Adobe Commerce robots.txt]** bildrutan är kraftfull. Den visar de IP-adresser som har 5XX http-statuskoder under den valda tidsperioden. Om en IP-adress gör stora mängder förfrågningar och platsen påverkas till den punkt där den inte kan hantera trafiken, har de IP-adresser som gör den högsta frekvensen av förfrågningar vanligtvis den högsta antalet fel. 5XX http-statuskoder indikerar vanligtvis en webbplats som har svårt att svara på förfrågningar.

Ju större fält, desto större är procentandelen fel som IP-adressen har i det totala antalet 5 gånger fel under den tidsperioden. Obs! En IP-adress kan ha flera segment i diagrammet om den har flera http-statuskoder (till exempel 502- och 503 http-statusar).

Normal fördelning anges till höger om fältet där IP-adresserna är lika breda eller där det finns några breda fält med mycket låga tal.

Om du håller markören över stapelsegmentet visas antalet angivna fel under den valda tidsperioden.

## [!UICONTROL IP cache status (MISS, PASS, ERROR) and HTTP status]

![Status för IP-cache (MISS, PASS, ERROR) och http under den valda tidsperioden Hur du blockerar starttrafik på snabbnivå ELLER hanterar robotar via filen robots.txt Best practices for Adobe Commerce robots.txt](../../assets/tools/observation-for-adobe-commerce/ip-cache-status-miss-pass-error.png)

Detta **[!UICONTROL IP cache status (MISS, PASS, ERROR) and HTTP status during selected time period How to block bot traffic on Fastly level OR manage bots through your robots.txt file Best practices for Adobe Commerce robots.txt]** bildrutan visar antalet HTTPS-statuskoder och icke-cachelagrade begäranden per IP i den valda tidsbildrutan. Detta anger den proportionella belastningen från varje IP-adress och den totala volymen. Den visar IP-adresserna med de flesta förfrågningar.

## [!UICONTROL Fastly Cache Summary for selected time period]

![Snabbt cachelagra sammanfattning för den valda tidsperioden](../../assets/tools/observation-for-adobe-commerce/fastly-cache-summary.png)

Klicka på [!UICONTROL Error] i nedanstående diagram kan du jämföra de två sista diagrammen med varandra. Detta kan visa var inläsningen bidrar till webbplatsproblem.

![Snabbt felkontroll](../../assets/tools/observation-for-adobe-commerce/compare-fastly.png)

## [!UICONTROL Graph - IPs that do not identify as bots]

![IP-adresser som inte identifieras som robotar utan fel under den valda tidsperioden Hur man blockerar robottrafiken på snabbnivå ELLER hanterar robotar genom robots.txt-filen God praxis för Adobe Commerce robots.txt](../../assets/tools/observation-for-adobe-commerce/ips-that-do-not-identify-as-bots.png)

The **[!UICONTROL Graph - IPs that do not identify as bots without error during selected time period How to block bot traffic on Fastly level OR manage bots through your robots.txt file Best practices for Adobe Commerce robots.txt]** frame visar fältet för begärande användaragent, IP-adressen och statuskoden för begäranden där fältet för begärande användaragent inte anger en [!DNL bot]. Den här bildrutan kan visa förfrågningar med hög frekvens från alla IP-adresser, men du bör vara uppmärksam på förfrågningar med hög frekvens, särskilt under en tidsperiod då webbplatsen kan ha problem.

## [!UICONTROL Graph - Suspicious Non-Bot traffic]

![Misstänkt icke-punktstrafik under vald tidsperiod](../../assets/tools/observation-for-adobe-commerce/suspicious-non-bot-traffic.png)

The **[!UICONTROL Graph - Suspicious Non-Bot traffic during selected time period]** Ett diagram söker efter användaragentvärdet för Go-http-client, men det kommer att utökas för att undersöka andra värden för användaragent för misstänkt begäran. Det här användaragentvärdet för begäran används av webbplatser för anslutning från tjänster och kan vara giltigt, men används även av skadliga webbplatser [!DNL bots].

## [!UICONTROL Graph - Bot traffic by Bot name]

![Diagram - Punkttrafik efter punktnamn under den valda tidsperioden)](../../assets/tools/observation-for-adobe-commerce/bot-traffic-bot-name.png)

The **[!UICONTROL Graph - Bot traffic by Bot name during selected time period]** bildrutan visar samma data som Total Bot-trafik med [!DNL Bot] namnet under den markerade tidsperiodtabellen högst upp på fliken. Den visar data via tidslinjen så att du kan se när förfrågningarna från [!DNL bots] görs och distribueras.

## [!UICONTROL Graph - Top 250 Bot Names and IP addresses]

![De 250 bästa punktnamnen och IP-adresserna under en viss tidsperiod Hur man blockerar starttrafiken på snabbnivå ELLER hanterar robotar via robots.txt-filen God praxis för Adobe Commerce robots.txt](../../assets/tools/observation-for-adobe-commerce/top-250-bot-names-ip-addresses.png)

The **[!UICONTROL Graph - Top 250 Bot Names and IP addresses during selected time period How to block bot traffic on Fastly level OR manage bots through your robots.txt file Best practices for Adobe Commerce robots.txt]** bildrutan visar samma data som Summa [!DNL Bot] Trafik efter punktnamn/IP-adress under den valda tidsperiodtabellen högst upp på fliken. Den visar data via tidslinjen och facetterar dem med IP-adress. Detta visas när förfrågningarna från [!DNL bots] görs, vilka IP-adresser som gör förfrågningar och hur förfrågningarna distribueras.

## [!UICONTROL Blocked Bot name / IP addresses (in Fastly)]

![Blockerat startnamn/IP-adresser (i fast form) under den valda tidsperioden. I det här diagrammet visas både trafik- och IP-adresser som returnerats som 403 Ej tillåten HTTP-statuskod](../../assets/tools/observation-for-adobe-commerce/blocked-bot-name-ip-addresses-403-code2.png)

The **[!UICONTROL Blocked Bot name / IP addresses (in Fastly) during selected time period. This graph displays bot traffic and IPs that were returned a 403 Forbidden HTTP Status code]** bildrutan visar robotnamnet och IP-adresserna som är blockerade. I det här diagrammet ser du hur alla förfrågningar blockeras i [!DNL Fastly] gå framåt.

## [!UICONTROL Blocked non-Bot name / IP addresses (in Fastly)]

![Blockerade namn/IP-adresser (i fast form) under den valda tidsperioden. I det här diagrammet visas icke-robottrafik och IP-adresser som returnerades som en 403 förbjuden HTTP-statuskod ](../../assets/tools/observation-for-adobe-commerce/blocked-non-bot-name-ip-addresses.png)

The **[!UICONTROL Blocked non-Bot name / IP addresses (in Fastly) during selected time period graph displays non-bot traffic and IPs that were returned a 403 Forbidden HTTP Status code]** bildrutan visar IP-adresser som inte identifieras som en [!DNL bot] som har blockerats via [!DNL Fastly].

## [!UICONTROL This table shows the number of user agents per IP address, number of successful, unsuccessful and blocked requests:]

![Tabellen visar antalet användaragenter per IP-adress, antal lyckade, misslyckade och blockerade begäranden:](../../assets/tools/observation-for-adobe-commerce/unsuccessful-attempts.png)

Skadlig [!DNL bots] ofta andra [!DNL bots] genom värdet på [!UICONTROL Request User Agent] fält. Tabellen visar hur många unika värden IP-adressen har i fältet. Ju högre värde, [!UICONTROL Request User Agent] -fältet, desto mer misstänkt är IP-adressen.

## [!UICONTROL IP with non-200 status errors]

![IP med icke-200-statusfel - utan 403-status](../../assets/tools/observation-for-adobe-commerce/ip-non-200-status-errors.png)

The **[!UICONTROL IP with non-200 status errors – without 403 status]** bildrutan visar fördelningen över den valda tidsramen för IP-adresser med andra HTTP-statuskoder än 200. När du ser högre värden för en enskild IP-adress eller grupp av IP-adresser måste du undersöka dem ytterligare.

## [!UICONTROL IP with 403 status codes:]

![IP med 403 statuskoder:](../../assets/tools/observation-for-adobe-commerce/ip-403-status-code2.png)

The **[!UICONTROL IP with 403 status codes]** bildrutan visar icke-cachelagrade begäranden utan [!UICONTROL cache_status=ERROR] som har HTTP-status 403. Detta kan visa att ursprungsservern är källan till 403 (obehörig) i stället för ett block från [!DNL Fastly].

## [!UICONTROL Top 5 with non-200 status codes]

![De fem vanligaste med icke-200-statuskoder som visar cache_status:](../../assets/tools/observation-for-adobe-commerce/top-5-non-200-status-code-status.png)

The **[!UICONTROL Top 5 with non-200 status codes showing cache_status]** tabellen på en IP-/statusnivå visar antalet var och en med [!UICONTROL cache_status] värde.

## [!UICONTROL Pageview Latency will show as spikes]

![Latens för sidvisning visas som taggar i det här diagrammet:](../../assets/tools/observation-for-adobe-commerce/pageview-latency.png)

The **[!UICONTROL Pageview Latency will show as spikes on this graph:]** bildrutan visar sidinläsnings-/API-svarstid som kan vara i linje med [!DNL bot] trafik.
