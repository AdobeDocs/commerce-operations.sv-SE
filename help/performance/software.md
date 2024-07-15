---
title: Software Recommendations
description: Granska en lista över rekommenderade program för optimala prestanda för Adobe Commerce-distributioner.
feature: Best Practices, Install
exl-id: b091a733-7655-4e91-a988-93271872c5d5
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '1392'
ht-degree: 0%

---

# Programvarurekommendationer

Följande programvara krävs för produktionsinstanser av [!DNL Commerce]:

* [PHP](../installation/system-requirements.md)
* Nginx och [PHP-FPM](https://php-fpm.org/)
* [[!DNL MySQL]](../installation/prerequisites/database/mysql.md)
* [[!DNL Elasticsearch] eller OpenSearch](../installation/prerequisites/search-engine/overview.md)

För driftsättningar med flera servrar eller för handlare som planerar att skala sin verksamhet rekommenderar vi följande:

* [[!DNL Varnish] cache](../configuration/cache/config-varnish.md)
* [Redis](../configuration/cache/redis-session.md) för sessioner (från 2.0.6+)
* En separat Redis-instans som din [standardcache](../configuration/cache/redis-pg-cache.md) (använd inte den här instansen som sidcache)

Se [systemkraven](../installation/system-requirements.md) om du vill ha information om vilka versioner som stöds av respektive programtyp.

## Operativsystem

Operativsystemskonfigurationer och optimeringar liknar varandra för [!DNL Commerce] jämfört med andra webbprogram med hög belastning. När antalet samtidiga anslutningar som hanteras av servern ökar kan antalet tillgängliga socketar allokeras helt. Linux-kärnan har stöd för en mekanism för att återanvända TCP-anslutningar. Om du vill aktivera den här funktionen anger du följande värde i `/etc/sysctl.conf`:

>[!INFO]
>
>Om du aktiverar net.ipv4.tcp_tw_reuse påverkas inte inkommande anslutningar.

```text
net.ipv4.tcp_tw_reuse = 1
```

Kernelparametern `net.core.somaxconn` styr det maximala antalet öppna socketar som väntar på anslutningar. Det här värdet kan ökas till 1024, men det bör vara relaterat till serverns förmåga att hantera den här mängden. Om du vill aktivera den här kernel-parametern anger du följande värde i `/etc/sysctl.conf`:

```text
net.core.somaxconn = 1024
```

## PHP

Magento stöder fullt ut PHP 7.3 och 7.4. Det finns flera faktorer att ta hänsyn till när PHP konfigureras för att få maximal hastighet och effektivitet vid behandling av begäranden.

### PHP-tillägg

Vi rekommenderar att listan med aktiva PHP-tillägg begränsas till de som krävs för funktionen [!DNL Commerce].

Magento Open Source och Adobe Commerce:

* ext-bcmath
* ext-type
* extrakrullning
* ext-dom
* ext-fileinfo
* ext-gd
* ext-hash
* ext-iconv
* ext-intl
* ext-json
* ext-libxml
* ext-mbstring
* textobensl
* ext-pcre
* ext-pdo_mysql
* ext-simplexml
* ext-soap
* textsocketar
* extranatrium
* ext-tokenizer
* ext-xmlwriter
* ext-xsl
* ext-zip
* lib-libxml
* lib-openssl

Dessutom kräver Adobe Commerce:

* ext-bcmath
* ext-type
* extrakrullning
* ext-dom
* ext-fileinfo
* ext-gd
* ext-hash
* ext-iconv
* ext-intl
* ext-json
* ext-libxml
* ext-mbstring
* textobensl
* ext-pcre
* ext-pdo_mysql
* ext-simplexml
* ext-soap
* textsocketar
* extranatrium
* ext-spl
* ext-tokenizer
* ext-xmlwriter
* ext-xsl
* ext-zip
* lib-libxml
* lib-openssl

Om du lägger till fler tillägg ökar bibliotekets laddningstid.

>[!INFO]
>
>`php-mcrypt` har tagits bort från PHP 7.2 och ersatts med [`sodium` library](https://www.php.net/manual/en/book.sodium.php). Kontrollera att [natrium](https://www.php.net/manual/en/sodium.installation.php) är korrekt aktiverat när du uppgraderar PHP.

>[!INFO]
>
>Om det finns profilerings- och felsökningstillägg kan det påverka sidornas svarstid negativt. En aktiv xDebug-modul utan någon felsökningssession kan till exempel öka svarstiden för sidan med upp till 30 %.

### PHP-inställningar

För att garantera att alla [!DNL Commerce]-instanser körs utan att dumpdata eller kod dumpas på disken anger du minnesgränsen enligt följande:

```text
memory_limit=1G
```

För felsökning ökar du värdet till 2G.

#### Konfiguration av Realpath_cache

Om du vill förbättra prestanda för [!DNL Commerce] lägger du till eller uppdaterar följande rekommenderade `realpath_cache`-inställningar i filen `php.ini`. Med den här konfigurationen kan PHP-processer cachelagra sökvägar till filer i stället för att leta upp dem varje gång en sida läses in. Se [Prestandajustering](https://www.php.net/manual/en/ini.core.php) i PHP-dokumentationen.

```text
realpath_cache_size=10M
realpath_cache_ttl=7200
```

#### ByteCode

Om du vill få ut maximal hastighet av [!DNL Commerce] på PHP 7 måste du aktivera OpCache-modulen och konfigurera den korrekt. De här inställningarna rekommenderas för modulen:

```text
opcache.memory_consumption=512
opcache.max_accelerated_files=60000
opcache.consistency_checks=0
opcache.validate_timestamps=0
opcache.enable_cli=1
```

När du finjusterar minnestilldelningen för opcache bör du ta hänsyn till storleken på Magento-kodbasen och alla dina tillägg. Magento prestandateam använder värdena i det föregående exemplet för testning eftersom det ger tillräckligt med utrymme i opcache för det genomsnittliga antalet installerade tillägg.

Om du har en dator med lite minne och du inte har många tillägg eller anpassningar installerade kan du använda följande inställningar för att få ett liknande resultat:

```text
opcache.memory_consumption=64
opcache.max_accelerated_files=60000
```

#### APCU

Vi rekommenderar att du aktiverar [PHP APCu-tillägget](https://getcomposer.org/doc/articles/autoloader-optimization.md#optimization-level-2-b-apcu-cache) och [konfigurerar `composer` så att det stöds](../performance/deployment-flow.md#preprocess-dependency-injection-instructions) för optimering för maximala prestanda. Det här tillägget cachelagrar filplatser för öppnade filer, vilket ökar prestanda för [!DNL Commerce] serveranrop, inklusive sidor, Ajax-anrop och slutpunkter.

Redigera din `apcu.ini`-fil så att den innehåller följande:

```text
extension=apcu.so
[apcu]
apc.enabled = 1
```

## Webbserver

Magento har fullt stöd för webbservrarna Nginx och Apache. [!DNL Commerce] innehåller rekommenderade exempelkonfigurationsfiler i `<magento_home>/nginx.conf.sample`- (Nginx) och `<magento_home>.htaccess.sample`-filerna (Apache).  Nginx-exemplet innehåller inställningar för bättre prestanda och är utformat så att liten omkonfiguration krävs. Några av de bästa metoderna för konfiguration som definieras i exempelfilen är:

* Inställningar för cachelagring av statiskt innehåll i en webbläsare
* Inställningar för minne och körningstid för PHP
* Inställningar för innehållskomprimering

Du bör också konfigurera antalet trådar för bearbetning av indatabegäran enligt nedan:

| Webbserver | Attributnamn | Plats | Relaterad information |
|--- | --- | --- | ---|
| Nginx | `worker_connections` | `/etc/nginx/nginx.conf` (Debian) | [NGINX-justering för prestanda](https://www.nginx.com/blog/tuning-nginx/) |
| Apache 2.2 | `MaxClients` | `/etc/httpd/conf/httpd.conf` (CentOS) | [Prestandajustering för Apache](https://httpd.apache.org/docs/2.2/misc/perf-tuning.html) |
| Apache 2.4 | `MaxRequestWorkers` | `/etc/httpd/conf/httpd.conf` (CentOS) | [Gemensamma direktiv för Apache MPM](https://httpd.apache.org/docs/2.4/mod/mpm_common.html#maxrequestworkers) |

## [!DNL MySQL]

Det här dokumentet innehåller inga detaljerade [!DNL MySQL] justeringsanvisningar eftersom varje butik och miljö är olika, men vi kan göra några allmänna rekommendationer.

Det har gjorts många förbättringar i [!DNL MySQL] 5.7.9 Vi är säkra på att [!DNL MySQL] distribueras med bra standardinställningar. De viktigaste inställningarna är:

| Parameter | Standard | Beskrivning |
|--- | --- | ---|
| `innodb_buffer_pool_instances` | 8 | Standardvärdet är 8 för att undvika problem med flera trådar som försöker få åtkomst till samma instans. |
| `innodb_buffer_pool_size` | 128MB | I kombination med de olika poolinstanser som beskrivs ovan innebär detta en standardminnestilldelning på 1 024 MB. Den totala storleken delas mellan alla buffertpooler. För bästa effektivitet bör du ange en kombination av `innodb_buffer_pool_instances` och `innodb_buffer_pool_size` så att varje buffertpoolinstans är minst 1 GB. |
| `max_connections` | 150 | Värdet för parametern `max_connections` ska korrelera med det totala antalet PHP-trådar som konfigurerats i programservern. En allmän rekommendation skulle vara 300 för en liten och 1 000 för en medelstor miljö. |
| `innodb_thread_concurrency` | 0 | Det bästa värdet för den här konfigurationen ska beräknas med formeln: `innodb_thread_concurrency = 2 * (NumCPUs + NumDisks)` |

## [!DNL Varnish]

Magento rekommenderar att du använder [!DNL Varnish] som helsidescache-server för din butik. PageCache-modulen finns fortfarande i kodbasen, men den bör bara användas i utvecklingssyfte. Den ska inte användas tillsammans med, eller i stället för, [!DNL Varnish].

Installera [!DNL Varnish] på en separat server framför webbskiktet. Den ska acceptera alla inkommande begäranden och tillhandahålla cachelagrade sidkopior. För att [!DNL Varnish] ska kunna fungera effektivt med skyddade sidor kan en SSL-termineringsproxy placeras framför [!DNL Varnish]. Nginx kan användas för detta ändamål.

[!DNL Commerce] distribuerar en exempelkonfigurationsfil för [!DNL Varnish] (version 4 och 5) som innehåller alla rekommenderade inställningar för prestanda. Bland de viktigaste prestandaaspekterna finns följande:

* **Hälsokontroll vid serverdel** avfrågar servern [!DNL Commerce] för att avgöra om den svarar i tid.
* I **Respitläge** kan du instruera [!DNL Varnish] att behålla ett objekt i cachen efter TTL-perioden (Time to Live) och att hantera det här inaktuella innehållet om [!DNL Commerce] inte är felfritt eller om det inte har hämtats färskt innehåll än.
* **Sankt läge** svartlistar ohälsosamma [!DNL Commerce] servrar under en konfigurerbar tidsperiod. Därför kan felfria backends inte generera trafik när [!DNL Varnish] används som belastningsutjämnare.

Mer information om hur du implementerar de här funktionerna finns i [Avancerat [!DNL Varnish] konfiguration](../configuration/cache/config-varnish-advanced.md).

### Optimera resursprestanda

I allmänhet rekommenderar vi att du lagrar dina resurser (bilder, JS, CSS osv.) på ett CDN för optimala prestanda.

Om din plats inte kräver att du distribuerar ett stort antal språkområden och dina servrar finns i samma region som de flesta av dina kunder, kan du få betydande prestandavinster till en lägre kostnad genom att lagra dina resurser i [!DNL Varnish] i stället för att använda ett CDN.

Om du vill lagra dina resurser i [!DNL Varnish] lägger du till följande VCL-poster i `default.vcl`-filen som genereras av [!DNL Commerce] för [!DNL Varnish] 5.

Lägg till följande i slutet av programsatsen `if` för PURGE-begäranden i underrutinen `vcl_recv`:

```javascript
# static files are cacheable. remove SSL flag and cookie

if (req.url ~ "^/(pub/)?(media|static)/.*\.(ico|html|css|js|jpg|jpeg|png|gif|tiff|bmp|mp3|ogg|svg|swf|woff|woff2|eot|ttf|otf)$") {
  unset req.http.Https;
  unset req.http./* {{ ssl_offloaded_header }} */;
  unset req.http.Cookie;
}
```

I underrutinen `vcl_backend_response` söker du efter programsatsen `if` som tar bort cookien för `GET` - eller `HEAD` -begäranden.
Det uppdaterade `if`-blocket ska se ut så här:

```javascript
# validate if we need to cache it and prevent from setting cookie
# images, css and js are cacheable by default so we have to remove cookie also

if (beresp.ttl > 0s && (bereq.method == "GET" || bereq.method == "HEAD")) {
  unset beresp.http.set-cookie;
if (bereq.url !~ "\.(ico|css|js|jpg|jpeg|png|gif|tiff|bmp|gz|tgz|bz2|tbz|mp3|ogg|svg|swf|woff|woff2|eot|ttf|otf)(\?|$)") {
  set beresp.http.Pragma = "no-cache";
  set beresp.http.Expires = "-1";
  set beresp.http.Cache-Control = "no-store, no-cache, must-revalidate, max-age=0";
  }
}
```

Starta om servern [!DNL Varnish] om du vill tömma cachade resurser när du uppgraderar webbplatsen eller distribuerar/uppdaterar resurser.

## Cachelagring och sessionsservrar

Magento har ett antal alternativ för att lagra cacheminne och sessionsdata, bland annat Redis, Memcache, filsystem och databas. Vissa av dessa alternativ beskrivs nedan.

### Inställningar för en webbnod

Om du planerar att betjäna all trafik med bara en webbnod är det inte klokt att placera cachen på en fjärr-Redis-server. Använd i stället filsystemet eller en lokal Redis-server. Om du vill använda filsystemet placerar du cachemapparna på en volym som är monterad i ett RAM-filsystem. Om du vill använda en lokal Redis-server rekommenderar vi att du konfigurerar Redis så att den använder socketar för direkta anslutningar i stället för att utbyta data via HTTP.

### Konfigurera flera webbnoder

Redis är det bästa alternativet för att konfigurera flera webbnoder. Eftersom [!DNL Commerce] aktivt cachelagrar mycket data för bättre prestanda bör du vara uppmärksam på nätverkskanalen mellan webbnoderna och Redis-servern. Du vill inte att kanalen ska bli en flaskhals för behandling av begäranden.

>[!INFO]
>
>Om du behöver hantera hundratals och tusentals samtidiga begäranden kan du behöva en kanal på upp till 1 Gbit (eller ännu bredare) till din Redis-server.
