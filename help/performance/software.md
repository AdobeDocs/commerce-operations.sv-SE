---
title: Software Recommendations
description: Granska en lista över rekommenderade program för optimala prestanda i Adobe Commerce- och Magento Open Source-distributioner.
source-git-commit: 1d5956ce22c1a159336e9e7d64064b618fc2e63f
workflow-type: tm+mt
source-wordcount: '1476'
ht-degree: 0%

---


# Programvarurekommendationer

Vi kräver följande program för produktionsinstanser [!DNL Commerce]:

* [PHP](https://devdocs.magento.com/guides/v2.4/install-gde/system-requirements.html)
* Nginx och [PHP-FPM](https://php-fpm.org/)
* [[!DNL MySQL]](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/mysql.html)
* [[!DNL Elasticsearch] eller OpenSearch](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/elasticsearch.html)

För driftsättningar med flera servrar eller för handlare som planerar att skala sin verksamhet rekommenderar vi följande:

* [[!DNL Varnish] cache](https://devdocs.magento.com/guides/v2.4/config-guide/varnish/config-varnish.html)
* [Redis](https://devdocs.magento.com/guides/v2.4/config-guide/redis/redis-session.html) för sessioner (från 2.0.6+)
* En separat Redis-instans som din [standardcache](https://devdocs.magento.com/guides/v2.4/config-guide/redis/redis-pg-cache.html) (använd inte den här instansen för sidcache)

Se [systemkrav](https://devdocs.magento.com/guides/v2.4/install-gde/system-requirements.html) om du vill ha information om vilka versioner som stöds av respektive programtyp.

## Operativsystem

Operativsystemskonfigurationer och optimeringar liknar varandra för [!DNL Commerce] jämfört med andra högbelastade webbapplikationer. När antalet samtidiga anslutningar som hanteras av servern ökar kan antalet tillgängliga socketar allokeras helt. Linux-kärnan har stöd för en mekanism för att återanvända TCP-anslutningar. Om du vill aktivera den här funktionen anger du följande värde i `/etc/sysctl.conf`:

>[!INFO]
>
>Om du aktiverar net.ipv4.tcp_tw_reuse påverkas inte inkommande anslutningar.

```terminal
net.ipv4.tcp_tw_reuse = 1
```

Kernelparametern `net.core.somaxconn` styr det maximala antalet öppna socketar som väntar på anslutningar. Det här värdet kan ökas till 1024, men bör vara relaterat till serverns förmåga att hantera den här mängden. Om du vill aktivera den här kernel-parametern anger du följande värde i `/etc/sysctl.conf`:

`net.core.somaxconn = 1024`

## PHP

Magento stöder fullt ut PHP 7.3 och 7.4. Det finns flera faktorer att ta hänsyn till när PHP konfigureras för att få maximal hastighet och effektivitet vid behandling av begäranden.

### PHP-tillägg

Vi rekommenderar att listan över aktiva PHP-tillägg begränsas till de som krävs för [!DNL Commerce] funktionalitet.

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
* ext-openssl
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
* ext-openssl
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

Om du lägger till fler tillägg tar det längre tid att läsa in biblioteket.

>[!INFO]
>
>`php-mcrypt` har tagits bort från PHP 7.2 och ersatts med [`sodium` bibliotek](https://www.php.net/manual/en/book.sodium.php). Se till att [natrium](https://www.php.net/manual/en/sodium.installation.php) är korrekt aktiverat vid uppgradering av PHP.

>[!INFO]
>
>Om det finns profilerings- och felsökningstillägg kan det påverka sidornas svarstid negativt. En aktiv xDebug-modul utan någon felsökningssession kan till exempel öka svarstiden för sidan med upp till 30 %.

### PHP-inställningar

För att garantera att alla [!DNL Commerce] instanser utan att dumpa data eller kod till disken, ange minnesgränsen enligt följande:

`memory_limit=1G`

För felsökning ökar du värdet till 2G.

#### Konfiguration av Realpath_cache

Att förbättra [!DNL Commerce] prestanda, lägga till eller uppdatera följande rekommenderas `realpath_cache` inställningarna i `php.ini` -fil. Med den här konfigurationen kan PHP-processer cachelagra sökvägar till filer i stället för att leta upp dem varje gång en sida läses in. Se [Prestandajustering](https://www.php.net/manual/en/ini.core.php) i PHP-dokumentationen.

```text
realpath_cache_size=10M
realpath_cache_ttl=7200
```

#### ByteCode

För att få ut maximal hastighet av [!DNL Commerce] på PHP 7 måste du aktivera OpCache-modulen och konfigurera den korrekt. De här inställningarna rekommenderas för modulen:

```text
opcache.memory_consumption=512
opcache.max_accelerated_files=60000
opcache.consistency_checks=0
opcache.validate_timestamps=0
opcache.enable_cli=1
```

När du finjusterar minnesallokeringen för opcache bör du ta hänsyn till storleken på Magento kodbas och alla tillägg. Magento&#39;s performance team använder värdena i det föregående exemplet för testning eftersom det ger tillräckligt med utrymme i opcache för det genomsnittliga antalet installerade tillägg.

Om du har en dator med lite minne och du inte har många tillägg eller anpassningar installerade kan du använda följande inställningar för att få ett liknande resultat:

```text
opcache.memory_consumption=64
opcache.max_accelerated_files=60000
```

#### APCU

Vi rekommenderar att du aktiverar [PHP APCu-tillägg](https://getcomposer.org/doc/articles/autoloader-optimization.md#optimization-level-2-b-apcu-cache) och [konfigurera `composer` för att stödja](https://devdocs.magento.com/guides/v2.4/performance-best-practices/deployment-flow.html#preprocess-dependency-injection-instructions) optimera för maximala prestanda. Det här tillägget cachelagrar filplatser för öppnade filer, vilket ökar prestanda för [!DNL Commerce] serveranrop som sidor, Ajax-anrop och slutpunkter.

Redigera `apcu.ini` som ska innehålla följande:

```text
extension=apcu.so
[apcu]
apc.enabled = 1
```

## Webbserver

Magento har fullt stöd för webbservrarna Nginx och Apache. [!DNL Commerce] innehåller exempelrekommenderade konfigurationsfiler i  `<magento_home>/nginx.conf.sample` (Nginx) och  `<magento_home>.htaccess.sample` (Apache) filer.  Nginx-exemplet innehåller inställningar för bättre prestanda och är utformat så att liten omkonfiguration krävs. Några av de bästa metoderna för konfiguration som definieras i exempelfilen är:

* Inställningar för cachelagring av statiskt innehåll i en webbläsare
* Inställningar för minne och körningstid för PHP
* Inställningar för innehållskomprimering

Du bör också konfigurera antalet trådar för bearbetning av indatabegäran enligt nedan:

| Webbserver | Attributnamn | Plats | Relaterad information |
|--- | --- | --- | ---|
| Nginx | `worker_connections` | `/etc/nginx/nginx.conf` (Debian) | [Justera NGINX för prestanda](https://www.nginx.com/blog/tuning-nginx/) |
| Apache 2.2 | `MaxClients` | `/etc/httpd/conf/httpd.conf` (CentOS) | [Prestandajustering för Apache](http://httpd.apache.org/docs/2.2/misc/perf-tuning.html) |
| Apache 2.4 | `MaxRequestWorkers` | `/etc/httpd/conf/httpd.conf` (CentOS) | [Gemensamma Apache MPM-direktiv](https://httpd.apache.org/docs/2.4/mod/mpm_common.html#maxrequestworkers) |

## [!DNL MySQL]

Det här dokumentet innehåller inte någon mer detaljerad information [!DNL MySQL] justeringsanvisningar eftersom varje butik och miljö är olika, men vi kan göra några allmänna rekommendationer.

Det har gjorts många förbättringar av [!DNL MySQL] 5.7.9 Vi är säkra på att [!DNL MySQL] distribueras med bra standardinställningar. De viktigaste inställningarna är:

| Parameter | Standard | Beskrivning |
|--- | --- | ---|
| `innodb_buffer_pool_instances` | 8 | Standardvärdet är 8 för att undvika problem med flera trådar som försöker få åtkomst till samma instans. |
| `innodb_buffer_pool_size` | 128MB | I kombination med de olika poolinstanser som beskrivs ovan innebär detta en standardminnestilldelning på 1 024 MB. Den totala storleken delas mellan alla buffertpooler. För bästa effektivitet ska du ange en kombination av `innodb_buffer_pool_instances` och `innodb_buffer_pool_size` så att varje buffertpoolinstans är minst 1 GB. |
| `max_connections` | 150 | Värdet för `max_connections` parametern ska korrelera med det totala antalet PHP-trådar som konfigurerats i programservern. En allmän rekommendation skulle vara 300 för en liten och 1 000 för en medelstor miljö. |
| `innodb_thread_concurrency` | 0 | Det bästa värdet för den här konfigurationen ska beräknas med formeln: `innodb_thread_concurrency = 2 * (NumCPUs + NumDisks)` |

## [!DNL Varnish]

Magento rekommenderar starkt att du använder [!DNL Varnish] som helsidescacheserver för din butik. PageCache-modulen finns fortfarande i kodbasen, men den bör bara användas i utvecklingssyfte. Den ska inte användas tillsammans med, eller i stället för, [!DNL Varnish].

Installera [!DNL Varnish] på en separat server framför webbnivån. Den ska acceptera alla inkommande begäranden och tillhandahålla cachelagrade sidkopior. Tillåt [!DNL Varnish] för att arbeta effektivt med skyddade sidor kan en SSL-termineringsproxy placeras framför [!DNL Varnish]. Nginx kan användas för detta ändamål.

[!DNL Commerce] distribuerar en exempelkonfigurationsfil för [!DNL Varnish] (version 4 och 5) som innehåller alla rekommenderade prestandainställningar. Bland de viktigaste prestandaaspekterna finns följande:

* **Hälsokontroll för backend** väljer [!DNL Commerce] för att avgöra om servern svarar i tid.
* **Behagelläge** låter dig instruera [!DNL Varnish] för att behålla ett objekt i cacheminnet efter dess TTL-period (Time to Live) och leverera det inaktuella innehållet om [!DNL Commerce] är inte hälsosamt eller om nytt innehåll inte har hämtats än.
* **Saint-läge** svarta listor ohälsosamma [!DNL Commerce] servrar för en konfigurerbar tidsperiod. På grund av detta kan ohälsosamma backend-objekt inte användas för trafik när de använder [!DNL Varnish] som belastningsutjämnare.

See [Advanced [!DNL Varnish] configuration](https://devdocs.magento.com/guides/v2.4/config-guide/varnish/config-varnish-advanced.html) for more information about implementing these features.

### Optimera resursprestanda

I allmänhet rekommenderar vi att du lagrar dina resurser (bilder, JS, CSS osv.) på ett CDN för optimala prestanda.

Om sajten inte kräver driftsättning på ett stort antal platser och servrarna finns i samma region som de flesta av dina kunder, kan du få betydande prestandavinster till en lägre kostnad genom att lagra dina resurser i [!DNL Varnish] i stället för att använda ett CDN.

Lagra dina resurser i [!DNL Varnish]lägger du till följande VCL-poster i `default.vcl` fil genererad av [!DNL Commerce] for [!DNL Varnish] 5.

I slutet av `if` programsats för PURGE-begäranden i `vcl_recv` subrutin, lägg till:

```javascript
# static files are cacheable. remove SSL flag and cookie

if (req.url ~ "^/(pub/)?(media|static)/.*\.(ico|html|css|js|jpg|jpeg|png|gif|tiff|bmp|mp3|ogg|svg|swf|woff|woff2|eot|ttf|otf)$") {
  unset req.http.Https;
  unset req.http./* {{ ssl_offloaded_header }} */;
  unset req.http.Cookie;
}
```

I `vcl_backend_response` subrutin, leta efter `if` programsats som tar bort cookien för `GET` eller `HEAD` förfrågningar.
Den uppdaterade `if` -blocket ska se ut så här:

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

Starta om [!DNL Varnish] server för att tömma cachelagrade resurser när du uppgraderar webbplatsen eller distribuerar/uppdaterar resurser.

## Cachelagring och sessionsservrar

Magento har ett antal alternativ för att lagra cacheminne och sessionsdata, bland annat Redis, Memcache, filsystem och databas. Vissa av dessa alternativ beskrivs nedan.

### Inställningar för en webbnod

Om du planerar att betjäna all trafik med bara en webbnod är det inte klokt att placera cachen på en fjärr-Redis-server. Använd i stället filsystemet eller en lokal Redis-server. Om du vill använda filsystemet placerar du cachemapparna på en volym som är monterad i ett RAM-filsystem. Om du vill använda en lokal Redis-server rekommenderar vi att du konfigurerar Redis så att den använder socketar för direkta anslutningar i stället för att utbyta data via HTTP.

### Konfigurera flera webbnoder

Redis är det bästa alternativet för att konfigurera flera webbnoder. För [!DNL Commerce] cachelagrar aktivt mycket data för bättre prestanda och observera nätverkskanalen mellan webbnoderna och Redis-servern. Du vill inte att kanalen ska bli en flaskhals för behandling av begäranden.

>[!INFO]
>
>Om du behöver hantera hundratals och tusentals samtidiga begäranden kan du behöva en kanal på upp till 1 Gbit (eller ännu bredare) till din Redis-server.
