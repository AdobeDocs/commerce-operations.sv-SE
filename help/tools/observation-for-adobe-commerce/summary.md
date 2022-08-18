---
title: '"Den [!UICONTROL Summary] tab"'
description: Läs mer om [!UICONTROL Summary] flik för [!DNL Observation for Adobe Commerce].
source-git-commit: 22df5b80262fbc98f3dd929ec8fdf6f697734c9b
workflow-type: tm+mt
source-wordcount: '2650'
ht-degree: 0%

---


# The [!UICONTROL Summary] tab

The [!UICONTROL Summary] flik för [!DNL Observation for Adobe Commerce] är tänkt att snabbt se några av de problem som webbplatser har, så att du kan lösa dem automatiskt eller identifiera möjliga orsaker till platsproblem. De extra flikarna ger mer detaljerad information om komponenttjänster, databaser, infrastruktur och processlägen.

## [!UICONTROL Transaction Overview]

![Transaktionsöversikt](../../assets/tools/transaction-overview.jpg)

### [Vad är en transaktion?](https://docs.newrelic.com/docs/apm/transactions/intro-transactions/transactions-new-relic-apm/#:%7E:text=transactions%20are%20reported.-,What%20is%20a%20transaction%3F,work%20in%20a%20software%20application.&amp;text=For%20APM%2C%20it%20will%20Ofta,when%20the%20response%20is%20sent)

&quot;At [!DNL New Relic], definieras en transaktion som en logisk arbetsenhet i ett program. Det avser i synnerhet funktionsanrop och metodanrop som utgör den aktuella arbetsenheten. Det refererar ofta till en webbtransaktion, som representerar en aktivitet som inträffar när programmet tar emot en webbförfrågan när svaret skickas.&quot;

### Typer av transaktioner:

**Webb:** Transaktioner initieras med en HTTP-begäran. För de flesta organisationer representerar dessa kundcentrerade interaktioner och är därför de viktigaste transaktionerna att övervaka.

**Ej webb:** Andra transaktioner än webbtransaktioner initieras inte med en webbförfrågan. De kan omfatta icke-webbarbetsprocesser, bakgrundsprocesser, skript, meddelandeköaktivitet och andra uppgifter.

Titta på **[!UICONTROL Transaction Overview]** bildruta fanns det nästan 53 000 transaktioner med en genomsnittlig APDEX-poäng på 0,76, och 95 % av dessa transaktioner skedde på under 2 313 sekunder. Detta är en bildruta där en tätare tidsram kan visa avvikelser från det aktuella genomsnittet om en APDEX-träff inträffar under en kort tidsram.

## [!UICONTROL 404 page errors frame]

![Bildruta med 404 sidfel](../../assets/tools/404-page-errors.jpg)

The **[!UICONTROL 404 page errors]** ramlistor [URI](https://en.wikipedia.org/wiki/Uniform_Resource_Identifier) och antalet 404 sidfel under den valda tidsramen.

## [!UICONTROL % of Storage Free frame]

![procent av lagringsfri bildruta](../../assets/tools/percent-of-storage-free.jpg)

The **[!UICONTROL % of Storage Free]** bildrutan visar medelvärdet i % fritt från lagringsutrymme över alla noder i klustret. Om du till exempel har ett kluster med tre noder visas \&lt;mount point=&quot;&quot;>, \&lt;environment name=&quot;&quot;>. Den här bildrutan kan vara bedräglig om det finns en varians över tre noder. Ett exempel på en varians skulle vara om `/data/mysql` den kostnadsfria monteringspunkten var ett annat värde i det tre nodklustret. Det finns en ram under [!UICONTROL MySQL] som facetterar monteringspunkterna efter nodnamn för att mer exakt se vilka `/data/mysql` lagringsutrymme på varje nod är faktiskt fritt.

## [!UICONTROL % of system memory that is free frame]

![procent systemminne som är ledigt bildruta](../../assets/tools/percent-of-system-memory-that-is-free.jpg)

Den här bildrutan visar, per nod, mängden systemminne som är ledigt på varje nod.

## [!UICONTROL Swap memory free in bytes]

![frigör minne i byte](../../assets/tools/swap-memory-free-in-bytes.jpg)

The **[!UICONTROL Swap memory free in bytes]** bildrutan visar, per nod, mängden SWAP-minne som är ledigt på noden.

## [!UICONTROL CPU % by host]

![Processor, procent per värd](../../assets/tools/cpu-percent-by-host.jpg)

Sammanställningen av alla miljöer och noder visas i **[!UICONTROL CPU % by host]** bildruta. Du bör avmarkera icke-produktionsmiljöer. Observera alla instanser där alla noder för produktionsmiljön inte finns. Den här artikeln innehåller tips om hög processoranvändning: [Felsöka prestanda med New Relic på Adobe Commerce](https://support.magento.com/hc/en-us/articles/360042149832#high_cpu_usage).

## [!UICONTROL Alerts during timeframe]

![varningar under tidsram](../../assets/tools/alerts-during-timeframe.jpg)

The **[!UICONTROL Alerts during timeframe]** visar alla varningar, inklusive [!UICONTROL Managed Alerts] som lagts till av Adobe Commerce Support.

## [!UICONTROL CPU Usage]

![CPU-användning](../../assets/tools/cpu-usage.jpg)

Om **[!UICONTROL CPU Usage]** bildrutan är tom, det är en indikator på att infrastrukturtillämpningen av [!DNL New Relic] är inte aktiverat. Om webbplatsen finns på Starter visas inte den här informationen. Om din webbplats är på Pro kan du öppna en supportanmälan och få [!DNL New Relic Infrastructure] aktiverat för din webbplats.

## [!UICONTROL Average Response Time]

![genomsnittlig svarstid](../../assets/tools/average-response-time.jpg)

The **[!UICONTROL Average Response Time]** diagram visar den genomsnittliga svarstiden för transaktioner (webb och andra).

## [!UICONTROL Long duration cron_schedule updates]

![long duration cron_schedule-uppdateringar](../../assets/tools/long-duration-cron-schedule-updates.jpg)

The **[!UICONTROL cron_schedule]** tabellen skrivs i början och slutet av kronijobb. Kronjobb med lång varaktighet kan indikera fördröjning vid uppdatering av den här tabellen, vilket kan indikera kronstackning eller ett problem med schemalagda kroner.

## [!UICONTROL Response Code]

![svarskod](../../assets/tools/response-code.jpg)

The **[!UICONTROL Response Code]** frame är en bra indikation på webbtrafik och svarskoden för förfrågningar. Det är [!DNL New Relic] transaktionsdata, och de kan hanteras av `httpResponseCode` returnerat.

## [!UICONTROL Web Traffic volume compared with one week ago Magento Managed Alerts Information]

![webbtrafik jämfört med för en vecka sedan](../../assets/tools/web-traffic-volume-compared.jpg)

Den här bildrutan visar webbtrafikvolymen för en vecka sedan jämfört med den aktuella volymen.

## [!UICONTROL Deployment Log Entries]

![distributionsloggposter](../../assets/tools/deployment-log-entries.jpg)

The **[!UICONTROL Deployment Log Entries]** bildrutan visar antalet distribuerings- och molnloggposter och antalet upphöjs efter distributionsloggens namn.

## [!UICONTROL Deployment State]

![distributionstillstånd](../../assets/tools/deployment-state.jpg)

The **[!UICONTROL Deployment State]** bildrutan utnyttjar särskilda distributionsfraser från distributionsloggarna. Här är några exempel på fraser som räknas i loggen och ansiktsnamnet:

**Distributionsloggfraser:**

* &quot;%Startar genereringskommando%&quot;) som &quot;start_gen&quot;
* &#39;%git apply /app/vendor/magento/ece-tools/patches%&#39;) as &#39;apply_patches&#39;
* &#39;%Set flag: .static_content_deploy%) som SCD
* &#39;%OBS! Genereringskommandot slutfördes%) som gen_compl
* &#39;%OBS! Distributionen slutfördes i %) som deploy_compl
* &#39;%OBS! Startar postdistribution.%) som start_pdeploy
* &#39;%OBS! Efterdistributionen är slutförd (%) som &#39;pdeploy&#39;
* %deploy-complete%) som cl_deploy_compl

## [!UICONTROL IP Frequency]

![IP-frekvens](../../assets/tools/ip-frequency.jpg)

The **[!UICONTROL IP Frequency]** antalet bildrutor som räknas (MISS- och PASS-status) för varje IP-adress från [!DNL Fastly] loggar. Webbförfrågningar med dessa statusvärden kommer till den ursprungliga servern och kommer att lägga till inläsning till servern. Den visar de tjugo översta adresserna i frekvens. Den här bildrutan kan användas för att identifiera IP-attacker eller källor med hög belastning på en webbplats.

## [!UICONTROL IP Response – top 20 URLs in duration]

![ip-svar - de 20 högsta URL:erna i varaktighet](../../assets/tools/ip-response-top-20-urls.jpg)

I den här bildrutan visas URL-adresser med den längsta svarstiden. Det kan indikera stora bildfiler eller sidor, API eller sidor med den längsta svarstiden.

## [!UICONTROL API Calls by IP]

![api-anrop via IP](../../assets/tools/api-calls-by-ip.jpg)

The **[!UICONTROL API Calls by IP]** frame hjälper till att identifiera tung trafik mot API:erna och IP-adresserna som gör förfrågningar från API:er.

## [!UICONTROL API Calls by IP, details by URL]

![api-anrop via IP-information via URL](../../assets/tools/api-calls-by-ip-details-by-url.jpg)

The **[!UICONTROL API Calls by IP, details by URL]** frame innehåller information om stor trafik mot API:erna och information om de URL:er som gör förfrågningarna.

## [!UICONTROL IP Frequency Rate per minute]

![IP-frekvens per minut](../../assets/tools/ip-frequency-rate-per-minute.jpg)

Ibland är det svårt att se vilken IP-adress som har flest förfrågningar på de andra bildrutorna. The **[!UICONTROL IP Frequency Rate per minute]** bildrutan visar hastigheten per minut per IP-adress.

## [!UICONTROL Potential Bots]

![potentiella stötar](../../assets/tools/potential-bots.jpg)

The **[!UICONTROL Potential Bots]** frame tittar på begäranden med ett request_user_agent-namn som NULL eller %bot%. Vanligtvis följer &quot;%bot%&quot; request_user_agent principinställningarna i `robots.txt` -fil.

## [!UICONTROL Transaction Errors]

![transaktionsfel](../../assets/tools/transaction-errors.jpg)

The **[!UICONTROL Transaction Errors]** bildrutan visar antalet transaktionsfel från [!DNL New Relic].

## [!UICONTROL Nginx access by node]

![nginx-åtkomst per nod](../../assets/tools/nginx-access-by-node.jpg)

The **[!UICONTROL Nginx access by node]** bildrutan tittar på antalet från `access.log` efter nod. Det är praktiskt att se om lasten är jämnt fördelad. Det visas ofta när en nod släpps. Detta visar även inläsning över hela webbplatsen.

## [!UICONTROL Galera Log]

![galerlogg](../../assets/tools/galera-log.jpg)

[Galera](https://galeracluster.com/library/galera-documentation.pdf) används för databaskluster. Den här bildrutan fokuserar på särskilda signaler från [!UICONTROL Galera] kluster. Dessa signaler fokuserar på noder som kommer in i och avslutar klustret, vilket är ett normalt beteende för att upprätthålla databasens dataintegritet. Noderna hålls synkroniserade som [!UICONTROL Galera] klusterstatus ändras.

**Lista över [!UICONTROL Galera] lägesändringar:**

* &#39;%1047 WSREP har ännu inte förberett nod för programanvändning (%) som &#39;node_not_prep_for_use&#39;
* %\[FEL\] WSREP: Det gick inte att läsa från: wsrep_sst_xtrabackup-v2%) som xtrabackup_read_fails
* %\[FEL\] WSREP: Processen slutfördes med fel: wsrep_sst_xtrabackup-v2 %) som xtrabackup_compl_w_err
* %\[FEL\] WSREP: rbr write fails%) as &#39;rbr_write_fails&#39;
* &#39;%self-leave%&#39;) som &#39;sgroups_node&#39;
* &#39;%members = 3/3 (join/total)%&#39;) som &#39;3of3&#39;
* &#39;%members = 2/3 (join/total)%&#39;) as &#39;2of3&#39;
* &#39;%members = 2/2%&#39;) as &#39;2of2&#39; ・ &#39;%members = 1/2%&#39;) as &#39;1of2&#39; ・ &#39;%members = 1/3%&#39;) as &#39;1of3&#39;
* %members = 1/1%) as &#39;1of1&#39;
* &#39;%\[Obs\] /usr/sbin/mysqld (mysqld 10).%) som sql_launch
* &#39;%kvorum: Ingen nod med fullständigt läge:%) som no_node_count
* %WSREP: Medlem 0%) som &#39;mem_0&#39;
* %WSREP: Medlem 1,0 %) som &#39;mem_1&#39;
* %WSREP: Medlem 2 %) som &#39;mem2&#39;
* %WSREP: Synkroniserad med grupp, klar för anslutningar (%) som klar
* %/usr/sbin/mysqld, Version:%) som mysql_launch_mysql.slow
* &quot;%\[Obs\] WSREP: Ny klustervy: globalt läge:%) som galera_Cluster_view_chng

Dessa signaler kan tyda på problem med lagring, minne eller frågor om tillståndet ändras ofta.

## [!UICONTROL Database errors]

![databasfel](../../assets/tools/database-errors.jpg)

**Lista över databasfel eller meddelanden som har identifierats:**

* %Minnesstorleken som allokerats för den temporära tabellen är mer än 20 % av oskyldig_buffer_pool_size%) som temp_tbl_buff_pool
* %\[FEL\] WSREP: rbr write fails%) as &#39;rbr_write_fails&#39;
* %mysqld: Disken är full%) som disk_full
* &#39;%Error number 28%&#39;) as &#39;err_28&#39;
* %rollback%) som rollback
* &#39;%Foreign key constrafor table%&#39;) as &#39;foreign_key_constraint&#39;
* &#39;%Error_code: 1114%) som &#39;sql_1114_full&#39;
* %CRITICAL: SQLSTATE\[HY000\] \[2006\] MySQL-servern har försvunnit%) som sql_borta
* &#39;%SQLSTATE\[HY000\] \[1040\] För många anslutningar%&#39;) som &#39;sql_1040&#39;
* %CRITICAL: SQLSTATE\[HY000\] \[2002\]%) as &#39;sql_2002&#39;
* &#39;%SQLSTATE\[08S01\]:%&#39;) som &#39;sql_1047&#39;
* %\[Warning\] Avbröt anslutningen%) som &#39;aborted_conn&#39;
* &#39;%SQLSTATE\[23000\]: Överträdelse av integritetsbegränsning:%) som sql_23000
* &#39;%1205 Lock wait timeout%&#39;) as &#39;sql_1205&#39;
* &#39;%SQLSTATE\[HY000\] \[1049\] Okänd databas%&#39;) som &#39;sql_1049&#39;
* &#39;%SQLSTATE\[42S02\]: Bastabell eller vy hittades inte:%) som sql_42S02
* &#39;%Allmänt fel: 1114%) som &#39;sql_1114&#39;
* &#39;%SQLSTATE\[40001\]%&#39;) som &#39;sql_1213&#39;
* &#39;%SQLSTATE\[42S22\]: Kolumnen hittades inte: 1054 Okänd kolumn%) som &#39;sq1_1054&#39;
* &#39;%SQLSTATE\[42000\]: Syntaxfel eller åtkomstfel:%) som sql_42000
* &#39;%SQLSTATE\[21000\]: Kardinalitetsöverträdelse:%) som sql_1241
* &#39;%SQLSTATE\[22003\]:%&#39;) som &#39;sql_22003&#39;
* &#39;%SQLSTATE\[HY000\] \[9000\] Klient med IP-adress%&#39;) som &#39;sql_9000&#39;
* &#39;%SQLSTATE\[HY000\]: Allmänt fel: 2014%) som &#39;sql_2014&#39;
* %1927 Anslutningen avbröts%) som sql_1927
* &#39;%1062 \[\ERROR\] InnoDB:%&#39;) som &#39;sql_1062_e&#39;
* &#39;%\[Obs\] WSREP: Tömmer minnesmappning till disk...%&#39;) som &#39;mem_map_flush&#39;
* %Internal MariaDB-felkod: 1146%) som &#39;sql_1146&#39;
* %Internal MariaDB-felkod: 1062%) som &#39;sql_1062&#39; ・ &#39;%1062 \[Warning\] InnoDB:%&#39;) som &#39;sql_1062_w&#39;
* %Internal MariaDB-felkod: 1064%) som &#39;sql_1064&#39;
* &#39;%InnoDB: Kontrollfel i filen %) som assertion_err
* &#39;%mysqld_safe Antal processer som körs nu: 0%) som mysql_oom
* &#39;%\[ERROR\] mysqld fick signal%&#39;) som &#39;mysql_sigterm&#39;
* &#39;%1452 Cannot add%&#39;) as &#39;sql_1452&#39;
* &#39;%ERROR 1698%&#39;) som &#39;sql_1698&#39;
* &#39;%SQLSTATE\[HY000\]: Allmänt fel: 3%) som cnt_write_tmp
* &#39;%Allmänt fel: 1 %) som sql_syntax
* &#39;%42S22%&#39;) som &#39;sql_42S22&#39;
* &#39;%InnoDB: Fel (dubblettnyckel)%&#39;) som &#39;oskuld_dup_key&#39;

## [!UICONTROL Database traces]

![databaspårning](../../assets/tools/database-traces.jpg)

The **[!UICONTROL Database traces]** läser data från [sql-spår](https://docs.newrelic.com/docs/apm/transactions/transaction-traces/transaction-traces-database-queries-page/) enhet [!DNL New Relic] och returnerar spårningens sökväg.

## [!UICONTROL Database mysql-slow.log]

![databasen mysql-slow.log](../../assets/tools/database-mysql-slow-log.jpg)

The **[!UICONTROL Database mysql-slow.log]** bildrutan innehåller ett antal poster i [mysql-slow.log](https://dev.mysql.com/doc/refman/5.7/en/slow-query-log.html) efter frågebegärandetyp. Den isolerar tidsramar som kan vara intressanta i mysql-slow.log (slow query log). Frågor om tabeller utan index eller frågor som uppdaterar stora tabeller kan blockera andra frågor.

## [!UICONTROL Redis synchronization from Log]

![återkallar synkronisering från logg](../../assets/tools/redis-synchronization-from-log.jpg)

[Redis](https://redis.io/docs/about/) är ett databasarkiv med öppen källkod (BSD-licensierad) i minnet som används som databas, cache och meddelandehanterare. Den kan utföra databas- och sessionscachning om den är konfigurerad. The **[!UICONTROL Redis synchronization from Log]** fokuserar bildrutan på [Synkronisera igen](https://redis.io/docs/manual/replication/). Ju större desto [!DNL Redis] datauppsättningen, desto större sannolikhet kommer det att uppstå problem med synkroniseringen (fler data att synkronisera).

**[!DNL Redis]fel och meddelanden**

* %SLAVE-synkronisering: Det finns inget utrymme kvar på enheten %) som space
* %Server startad, Redis version%) som serv_start
* &#39;%Servern är nu klar att acceptera anslutningar%&#39;) som &#39;färdig&#39;
* %Anslutningen med överordnad bröts.%&#39;) som &#39;mstr_loss&#39;
* &#39;%+nedåt sentinel%&#39;) som &#39;+sentinal&#39;
* &#39;%-sdown sentinel%&#39;) som &#39;-sentinal&#39;
* % nedåtgående slav %) som &#39;-slave&#39;, &#39;%+sdown slave%&#39;) som &#39;+slave&#39;
* %-failover-abort-not-selected överordnad mymaster%) as -failover
* %+failover-abort-not-selected överordnad mymaster%) as &#39;+failover&#39;
* %Partiell omsynkronisering är inte möjlig (ingen cachelagrad överordnad)%) som part_sync_err
* %ÖVERORDNAD avbröt replikering med ett fel: ERR Can%) as &#39;mstr_sync_err&#39;
* &#39;%Överordnad stöder inte PSYNC eller är i feltillstånd (%) som &#39;mstr_psync_err&#39;
* %SLAVE-synkronisering: Slutfördes med success%) som slv_sync_suc
* %ÖVERORDNAD avbröt replikering med ett fel: ERR Can%) as &#39;mstr_sync_err,coun&#39;
* &#39;%OOM-kommandot tillåts inte när minne används%&#39;) som &#39; max_mem_err&#39;
* &#39;%CredisException(kod: 0): läsfel vid anslutning%) som credis_read_error
* %Uncaught RedisException:%) as &#39;redis_excp_err&#39;
* &#39;%psync schemalagd att stängas av ASAP för att täcka över utdatabufferten%&#39;) som &#39;output_buf_err&#39;

## [!UICONTROL PHP process states]

![PHP-processlägen](../../assets/tools/php-process-states.jpg)

Hur PHP-processer beter sig beror på [konfiguration](https://www.php.net/manual/en/install.fpm.configuration.php). Konfigurationen är komplex, med många variabler och alternativ. The **[!UICONTROL PHP process states]** bildruta hjälper dig att förstå när PHP-processer avslutas och startas om.

### [!UICONTROL PHP errors]

![php-fel](../../assets/tools/php-errors.jpg)

The **[!UICONTROL PHP errors]** antalet PHP-fel med arbetare under den valda tidsramen. Mer information finns i [Adobe Commerce PHP-inställningar](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/php-settings.html).

**PHP-fel och -meddelanden**

* %worker_connections are not enough%) as &#39;worker&#39;
* &#39;%PHP Allvarligt fel: Tillåten minnesstorlek!%&#39;) som &#39;mem_size&#39;
* &#39;%11 (SIGSEGV)%&#39;) har avslutats som &#39;sig_11&#39;
* &#39;%utgick på signal 7 (SIGBUS)%&#39;) som &#39;sig_7&#39;
* %ökning pm.start_servers%) som pmstart_serv
* &#39;%max_children%&#39;) som &#39;max_children_cnt&#39;
* &#39;%PHP Allvarligt fel: Tillåten minnesstorlek på %) som mem_exhst_coun
* &#39;%Det gick inte att allokera minne för pool%&#39;) som &#39;opc_mem_count&#39;
* &#39;%Warning Interned string buffer overflow%&#39;) as &#39;opc_str_buf&#39;
* %Illegal string offset%) as &#39;opc_sv_comments&#39;
* &#39;%PHP Allvarligt fel: Ohanterat RedisException: läsfel vid anslutning%) som php_exc

## [!UICONTROL PHP processes]

![php-processer](../../assets/tools/php-processes.jpg)

[PHP-FPM](https://php-fpm.org/), a [!UICONTROL FastCGI Process Manager] används av [!DNL Nginx]. Mer information om systemkrav finns i [Krav för PHP-versioner mappade till Adobe Commerce-versioner](https://devdocs.magento.com/guides/v2.4/install-gde/system-requirements.html). The **[!UICONTROL PHP processes]** bildrutan visar antalet PHP-processer som körs vid en viss tidpunkt på den valda tidslinjen.

## [!UICONTROL Secondary processes]

![sekundära processer](../../assets/tools/secondary-processes.jpg)

Sekundära processer kan påverka webbplatsens respons. The **[!UICONTROL Secondary processes]** bildrutan kan indikera en eller flera processer som kan lägga till inläsning på platsen. Databasen har i första hand de mest sekundära processerna som körs.

## [!UICONTROL Traffic vs Week Ago]

![trafik jämfört med vecka sedan](../../assets/tools/traffic-vs-week-ago.jpg)

The **[!UICONTROL Traffic vs Week Ago]** läser webbplatsens trafik (förfrågningar) från [!DNL Fastly] loggar med cachestatus (&quot;MISS&quot;,&quot;PASS&quot;). De här förfrågningarna lägger till inläsning till de ursprungliga servrarna. Den här bildrutan visar volymen för webbförfrågningar jämfört med för en vecka sedan under samma tidsram.

## [!UICONTROL Fastly Cache]

![snabbt cacheminne](../../assets/tools/fastly-cache.jpg)

The **[!UICONTROL Fastly Cache]** bildrutan visar en sammanställd vy över cachestatus för begäranden från snabbloggarna. Om du klickar på FEL visas procentandelen fel i begäran. Detta ökar vanligtvis när den ursprungliga servern inte svarar tillräckligt snabbt på sidförfrågningar.

## [!UICONTROL Page Rendering]

![sidåtergivning](../../assets/tools/page-rendering.jpg)

The **[!UICONTROL Page Rendering]** bildrutan visar den genomsnittliga sidåtergivningstiden från sidvykällan för [!DNL New Relic] jämfört med samma tidsperiod föregående vecka.

## [!UICONTROL Page loading detail]

![sidinläsningsdetaljer](../../assets/tools/page-loading-detail.png)

The **[!UICONTROL Page loading detail]** frame beskriver sidans inläsningshändelser. Den beskriver innebörden av dessa aspekter. Här är frågan som körs för den här bildrutan:

`SELECT percentile(timeToResponseStart, 50) AS 'first byte', percentile(firstPaint, 50) as 'First paint', percentile(firstContentfulPaint, 50) as 'First contentful paint', percentile(timeToDomContentLoadedEventEnd, 50) AS 'DOM content loaded', percentile(duration, 50) AS 'Window load + AJAX' FROM BrowserInteraction TIMESERIES`

## [!UICONTROL Transactions – Avg, Max, Min]

![transaktioner - avg, max, min](../../assets/tools/transactions-avg-max-min.jpg)

Transaktionstiden är i sekunder. Beroende på transaktionen kan den påverka andra transaktioner om den är långvarig. De transaktioner som anges under namn och varaktighet gäller för den specifika tidsperioden. Om det finns en kortfattad problemtidsram ändrar du storlek på [!DNL Observation for Adobe Commerce] datum-/tidsväljare till den smala tidsramen.

## [!UICONTROL Admin Activities]

![administratörsaktiviteter](../../assets/tools/admin-activities.jpg)

The **[!UICONTROL Admin Activities]** bildruta identifierar transaktioner med en administratörsanvändare.

## [!UICONTROL Order transactions (default?)]

![Standardordertransaktioner](../../assets/tools/order-transactions-default.jpg)

The **[!UICONTROL Order transactions (default?)]** ramutseenden för transaktioner `request.headers.host` från transaktioner där namnet = &#39;WebTransaction/Action/checkout/onpage/success&#39;. Om orderns URL är en annan kommer den här bildrutan inte att ha några data.

## [!UICONTROL Elasticsearch Index information]

![indexinformation för elasticsearch](../../assets/tools/elasticsearch-Index-information.jpg)

**[Statusen Elasticsearch:](https://www.elastic.co/guide/en/elasticsearch/reference/current/cluster-health.html)**

* Grön: Alla skuggor tilldelas.
* Gul: Alla primära delningar tilldelas, men en eller flera replikdelningar är inte tilldelade. Om en nod i klustret misslyckas kan vissa data vara otillgängliga tills den noden har reparerats.
* Röd: En eller flera primära kort har inte tilldelats, så vissa data är inte tillgängliga. Detta kan inträffa under klusterstart när primära kort har tilldelats.

## [!UICONTROL Elasticsearch Errors]

![elasticsearch-fel](../../assets/tools/elasticsearch-errors.jpg)

**[!DNL Elasticsearch]fel:**

* &#39;%all shards failed%&#39; as &#39;all_shards_failed&#39;
* &#39;%NoNodesAvailableException%&#39; som &#39;no_alive_nodes&#39;
* &#39;%PHP Allvarligt fel: Ohanterat fel: Fel parametrar för Elasticsearch% som &#39;fel_param&#39;
* %Du kan åtgärda det här problemet genom att uppgradera tjänsten Elasticsearch i Magento Cloud-infrastrukturen till version % som ver_err
* &#39;%klusterhälsostatus har ändrats från \[YELLOW\] till \[RED\] (orsak:%) som &#39;yel_red&#39;
* &#39;%Inget utrymme återstår på enheten%&#39; som &#39;inget_utrymme&#39;
* &#39;% misslyckades med att köra [SearchRequest{searchType=%&#39; som &#39;failed_query&#39;

## [!UICONTROL Cron view]

![cron view](../../assets/tools/cron-view.jpg)

The **[!UICONTROL Cron view]** bildrutan söker i kronloggen efter en balans mellan antalet påbörjade kroner och antalet färdiga kroner.


## [!UICONTROL Cron error]

![cron-fel](../../assets/tools/cron-error.png)

**Kronfel från cron.log:**

* %_stg% som stg_crons
* %Could not obtain lock for cron job%&#39; as &#39;cron_lock&#39;
* &#39;%Allmänt fel: 2006 MySQL-servern har gått bort% som mysql_has_away
* %error% som error
* &#39;%Allmänt fel: 1205 Timeout för låsuppehåll överskreds% som sql_1205_cron

## [!UICONTROL cron_schedule table updates]

![cron_schedule table updates](../../assets/tools/cron-schedule-table-updates.jpg)

The **[!UICONTROL cron_schedule table updates]** bildrutan tittar på den maximala längden i sekunder där datalagrets operationsuppdateringar omfattar tabellen cron_schedule. Den är facetterad i SQL-begärandetypen.

## [!UICONTROL Datastore Operations Tables]

![datastaderåtgärdstabeller](../../assets/tools/datastore-operations-tables.jpg)

Detta **[!UICONTROL Datastore Operations Tables]** bildrutan visar de 25 viktigaste åtgärderna efter varaktighet, tabellnamn och SQL-begärandetyp. Håll pekaren över topparna för att se vilka tabeller som öppnats och av vilken typ av begäran det var.

## [!UICONTROL Cache Flush]

![cachelagring](../../assets/tools/cache-flush.jpg)

**Cache-tömningar har identifierats:**

* %config% som config_cache_flushed
* %layout% som layout_cache_flush
* %block_html% som block_html_cache_flush
* %collections% som collections_cache_flush
* &#39;%refling%&#39; som &#39;mirror_cache_flush&#39;
* %db_ddl% som db_ddl_cache_flush
* &#39;%compiled_config%&#39; som &#39;compiled_config_cache_flush&#39;
* %eav% som eav_cache_flush
* &#39;%customer_notification%&#39; som &#39;cust_notif_cache_flush&#39;
* %config_integration% som config_intg_cache_flush
* %config_integration_api% som config_integ_api_cache_flush
* %full_page% som full_page_cache_flush
* &#39;%config_webservice%&#39; som &#39;config_webserv_cache_flush&#39;
* %translate% som translate_cache_flush