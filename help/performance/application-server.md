---
title: GraphQL Application Server
description: Följ dessa anvisningar för att aktivera GraphQL Application Server i din Adobe Commerce-distribution.
exl-id: 9b223d92-0040-4196-893b-2cf52245ec33
source-git-commit: b89ed5ddb4c6361de22d4a4439ffcfcc3ec8d474
workflow-type: tm+mt
source-wordcount: '2267'
ht-degree: 0%

---


# GraphQL Application Server

Med Commerce GraphQL Application Server kan Adobe Commerce upprätthålla status bland API-begäranden i Commerce GraphQL. GraphQL Application Server, som bygger på svullningstillägget, fungerar som en process med arbetstrådar som hanterar bearbetningen av begäranden. Genom att bevara ett startläge för ett program bland GraphQL API-begäranden förbättrar GraphQL Application Server hanteringen av begäranden och produktens övergripande prestanda. API-förfrågningar blir betydligt effektivare.

GraphQL Application Server finns endast för Adobe Commerce. Det finns inte för Magento Open Source. Du måste [skicka in en Adobe Commerce-support](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide) biljett för att aktivera GraphQL Application Server i Pro-projekt.

>[!NOTE]
>
>GraphQL Application Server är för närvarande inte kompatibel med [[!DNL Amazon Simple Storage Service (AWS S3)]](https://aws.amazon.com/s3/). Adobe Commerce på molnbaserade infrastrukturkunder använder [!DNL AWS S3] for [fjärrlagring](../configuration/remote-storage/cloud-support.md) kan inte använda GraphQL Application Server förrän Adobe släpper en snabbkorrigering senare under 2024.

## Arkitektur

GraphQL Application Server upprätthåller status mellan Commerce GraphQL API-begäranden och eliminerar behovet av startspärr. Genom att dela applikationsstatus mellan processer blir GraphQL-förfrågningar betydligt effektivare, vilket minskar svarstiderna med upp till 30 %.

PHP-exekveringsmodellen&quot;share-no&quot; utgör en utmaning när det gäller latenstid eftersom varje begäran kräver att ramverket startas. Denna startprocess innehåller tidskrävande uppgifter som att läsa konfigurationen, konfigurera startprocessen och skapa tjänstklassobjekt.

Det verkar som om logiken för hantering av förfrågningar övergår till en händelselösning på programnivå som åtgärdar utmaningen att effektivisera behandlingen av förfrågningar på företagsnivå. På så sätt elimineras behovet av att starta vid körningen av begäran.

## Fördelar

Med GraphQL Application Server kan Adobe Commerce hantera status mellan efterföljande Commerce GraphQL API-begäranden. Genom att dela programtillstånd mellan begäranden blir API-förfrågningens effektivitet effektivare genom att minimera belastningen på processerna och optimera hanteringen av förfrågningar. Därför kan svarstiden för GraphQL-begäranden minskas till 30 %.

## Systemkrav

För att köra GraphQL Application Server krävs följande:

* PHP 8.2 eller senare
* Svepande PHP-tillägg v5+ har installerats
* Tillräckligt RAM och processor baserat på förväntad belastning

## Aktivera och distribuera i molninfrastruktur

The `ApplicationServer` modul (`Magento/ApplicationServer/`) aktiveras GraphQL Application Server.

### Aktivera Pro-projekt

Utför följande steg innan du distribuerar GraphQL Application Server i Pro-projekt:

1. Distribuera Adobe Commerce i molninfrastrukturen med hjälp av molnmallen från [2.4.7-appservergren](https://github.com/magento/magento-cloud/tree/2.4.7-appserver).
1. Se till att alla anpassningar och tillägg för din Commerce [kompatibel](https://developer.adobe.com/commerce/php/development/components/app-server/) med GraphQL Application Server.
1. Klona ditt Commerce Cloud-projekt.
1. Justera inställningarna i filen application-server/nginx.conf.sample om det behövs.
1. Kommentera det aktiva webbavsnittet i `project_root/.magento.app.yaml` helt och hållet.
1. Avkommentera följande konfiguration av avsnittet &#39;web&#39; i `project_root/.magento.app.yaml` fil som innehåller GraphQL Application Server `start` -kommando.

   ```yaml
   web:
       upstream:
           socket_family: tcp
           protocol: http
       commands:
           start: ./application-server/start.sh > var/log/application-server-status.log 2>&1
   ```

1. Lägg till uppdaterade filer i Git-indexet med det här kommandot:

   ```bash
   git add -f .magento/routes.yaml application-server/.magento/*
   ```

1. Genomför ändringarna med det här kommandot:

   ```bash
   git commit -m "AppServer Enabled"
   ```

### Distribuera Pro-projekt

När du är klar med aktiveringsstegen skickar du ändringar till Git-databasen för att distribuera GraphQL Application Server:

```bash
git push
```

### Aktivera startprojekt

Utför följande steg innan du distribuerar GraphQL Application Server i Starter-projekt:

1. Distribuera Adobe Commerce i molninfrastrukturen med hjälp av molnmallen från [2.4.7-appservergren](https://github.com/magento/magento-cloud/tree/2.4.7-appserver).
1. Se till att alla anpassningar och tillägg i Commerce är kompatibla med GraphQL Application Server.
1. Bekräfta att `CRYPT_KEY` Miljövariabeln ställs in för din instans. Du kan kontrollera statusen för den här variabeln på Cloud Project Portal (gränssnittet för introduktion).
1. Klona ditt Commerce Cloud-projekt.
1. Byt namn `application-server/.magento/.magento.app.yaml.sample` till `application-server/.magento/.magento.app.yaml` och justera inställningarna i .magento.app.yaml om det behövs.
1. Avkommentera följande flödes konfiguration i `project_root/.magento/routes.yaml` fil att omdirigera `/graphql` till GraphQL Application Server.

   ```yaml
   "http://{all}/graphql":
       type: upstream
       upstream: "application-server:http"
   ```

1. Lägg till uppdaterade filer i Git-indexet:

   ```bash
   git add -f .magento/routes.yaml application-server/.magento/*
   ```

1. Genomför ändringarna:

   ```bash
   git commit -m "AppServer Enabled"
   ```

>[!NOTE]
>
>Se till att alla anpassade inställningar i roten `.magento.app.yaml` filen migreras korrekt till `application-server/.magento/.magento.app.yaml` -fil. Efter `application-server/.magento/.magento.app.yaml` filen läggs till i ditt projekt bör du underhålla den utöver roten `.magento.app.yaml` -fil. Om du till exempel behöver [konfigurera kaninitmq](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/service/rabbitmq) eller [hantera webbegenskaper](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/app/properties/web-property) du bör lägga till samma konfiguration i `application-server/.magento/.magento.app.yaml` också.

### Distribuera startprojekt

När aktiveringen är klar [steg](#before-you-begin-a-cloud-starter-deployment), skickar ändringar till Git-databasen för att distribuera GraphQL Application Server:

```bash
git push
```

### Verifiera aktivering i molnprojekt

1. Utför en GraphQL-fråga eller mutation mot instansen för att bekräfta att `graphql` slutpunkten är tillgänglig. Exempel:

   ```
   mutation {  
    createEmptyCart
   }
   ```

   Det förväntade svaret ska likna följande exempel:

   ```terminal
   {    
    "data": {        
        "createEmptyCart": "HLATPzcLw5ylDf76IC92nxdO2hXSXOrv"    
        }
    }
   ```

1. Använd SSH för att komma åt din molninstans. The `project_root/var/log/application-server.log` ska innehålla en ny loggpost för varje GraphQL-begäran.

1. Du kan också kontrollera om GraphQL Application Server körs genom att köra följande kommando:

   ```bash
   ps aux|grep php
   ```

   Du borde se en `bin/magento server:run` med flera trådar.

Om dessa verifieringssteg lyckas körs GraphQL Application Server `/graphql` förfrågningar.

## Aktivera lokala projekt

The `ApplicationServer` modul (`Magento/ApplicationServer/`) aktiveras GraphQL Application Server för GraphQL API:er.

Om du kör GraphQL Application Server lokalt måste du installera SVULLE-tillägget och göra en mindre ändring i Nginx-konfigurationsfilen för distributionen.

### Förutsättningar

Utför följande steg innan du aktiverar `ApplicationServer` modul:

* Konfigurera Nginx
* Installera och konfigurera tillägget SVULLA v5+

#### Konfigurera Nginx

Din specifika Commerce-distribution avgör hur du konfigurerar Nginx. Vanligtvis heter konfigurationsfilen Nginx som standard `nginx.conf` och placeras i någon av följande kataloger: `/usr/local/nginx/conf`, `/etc/nginx`, eller `/usr/local/etc/nginx`. Se [Nybörjarhandbok](https://nginx.org/en/docs/beginners_guide.html) om du vill ha mer information om hur du konfigurerar Nginx.

Exempel på Nginx-konfiguration:

```conf
location /graphql {
    proxy_set_header Host $http_host;
    proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;

    proxy_pass http://127.0.0.1:9501/graphql;
}
```

#### Installera och konfigurera SVG

Om du vill köra GraphQL Application Server lokalt installerar du svullningstillägget (v5.0 eller senare). Det finns flera sätt att installera det här tillägget.

I proceduren nedan beskrivs hur du installerar svullningstillägget för PHP 8.2 på OSX-baserade system. Det är ett av flera sätt att installera tillägget för svullnad.

```bash
pecl install swoole
```

Under installationen visas uppmaningar om att aktivera stöd för `openssl`, `mysqlnd`, `sockets`, `http2`och `postgres`. Retur `yes` för alla alternativ utom `postgres`.

### Verifiera installation med svullnad

Bekräfta att tillägget har aktiverats:

```bash
php -m | grep swoole
```

### Vanliga fel vid installation med svepfunktion

Eventuella fel som uppstår under svullnad uppstår vanligtvis under `pecl` installationsfas. Typiska fel kan vara att det saknas `openssl.h` och `pcre2.h` filer. Kontrollera att de här två paketen är installerade på din lokala dator för att åtgärda felen.

* Kontrollera platsen för `openssl` genom att köra:

```bash
openssl version -d
```

Det här kommandot visar banan där `openssl` är installerat.

* Kontrollera platsen för `pcre2` genom att köra:

```bash
pcre2-config --prefix 
```

Använd Homebrew för att installera de saknade paketen om kommandoutdata indikerar att filer saknas:

```bash
brew install openssl
```

```bash
brew install pcre2
```

#### Lös problem med openssl

Lös problem relaterade till `openssl`, kör:

```bash
export LDFLAGS="-L/opt/homebrew/etc/openssl@3/lib" export CPPFLAGS="-I/opt/homebrew/etc/openssl@3/include"
```

Bekräfta att du använder sökvägen från din lokala `dev` miljö.

#### Bekräfta lösning av problem relaterade till openssl

Du kan köra följande kommando igen för att kontrollera om problem som är relaterade till öppning har åtgärdats:

```bash
pecl install swoole
```

#### Lös problem med pcre2.h

Lös problem relaterade till `pcre2.h`, länkar samman `pcre2.h` sökväg till den installerade PHP-tilläggskatalogen. Din specifika installerade version av PHP och `pcr2.h` bestämmer vilken version av kommandot du ska använda.

### Kör GraphQL Application Server

Starta GraphQL Application Server:

```bash
bin/magento server:run
```

Det här kommandot startar en HTTP-port på 9501. När GraphQL Application Server startas blir port 9501 en HTTP-proxyserver för alla GraphQL-frågor.

Så här bekräftar du att GraphQL Application Server körs i din distribution:

```bash
ps aux | grep php
```

Ytterligare sätt att bekräfta att GraphQL Application Server körs är:

* Kontrollera `/var/log/application-server.log` för poster som är relaterade till bearbetade GraphQL-begäranden.
* Försök ansluta till HTTP-porten som GraphQL Application Server körs på. Till exempel: `curl -g 'http://localhost:9501/graph`.

### Bekräfta att GraphQL-begäranden behandlas

GraphQL Application Server lägger till `X-Backend` svarshuvud med värdet `graphql_server` på varje begäran som behandlas. Om du vill kontrollera om en begäran har hanterats av GraphQL Application Server ska du leta efter den här svarshuvudet.

### Bekräfta kompatibilitet för tillägg och anpassning

Tilläggsutvecklare och handlare bör först kontrollera att deras kod för tillägg och anpassning följer de tekniska riktlinjer som beskrivs i [Tekniska riktlinjer](https://developer.adobe.com/commerce/php/coding-standards/technical-guidelines/).

Tänk på följande när du utvärderar koden:

* Tjänstklasser (d.v.s. klasser som tillhandahåller beteende men inte data, t.ex. `EventManager`) ska inte ha ett ändringsbart tillstånd.
* Undvik temporal koppling.

## Inaktivera GraphQL Application Server

Hur du inaktiverar GraphQL Application Server varierar beroende på om servern körs lokalt eller i molnet.

### Inaktivera GraphQL Application Server (molnet)

1. Ta bort alla nya filer och andra kodändringar som ingår i `AppServer Enabled` implementera under dina förberedelser för driftsättningen.

1. Genomför ändringarna med det här kommandot:

   ```bash
   git commit -m "AppServer Disabled"
   ```

1. Distribuera dessa ändringar med det här kommandot:

   ```bash
   git push
   ```

### Inaktivera GraphQL Application Server (lokalt)

1. Kommentera `/graphql` avsnitt i `nginx.conf` som du lade till när du aktiverade GraphQL Application Server.
1. Starta om nästa.

Den här metoden för att inaktivera GraphQL Application Server kan vara användbar för att snabbt testa eller jämföra prestanda.

### Bekräfta att GraphQL Application Server är inaktiverad

Bekräfta att GraphQL-begäranden behandlas av `php-fpm` i stället för GraphQL Application Server anger du följande kommando: `ps aux | grep php`.

När GraphQL Application Server har inaktiverats:

* `bin/magento server:run` är inaktiv.
* `var/log/application-server.log` innehåller inga poster efter GraphQL begäran.

## Integrerings- och funktionstester för GraphQL Application Server

Extension-utvecklare kan köra två integrationstester för att verifiera att tillägg är kompatibla med GraphQL Application Server: `GraphQlStateTest` och `ResetAfterRequestTest`.

### GraphQlStateTest

`GraphQlStateTest` identifierar tillstånd i delade objekt som inte ska återanvändas för flera begäranden.

Det här testet är utformat för att identifiera lägesändringar i serviceobjekt som genereras av `ObjectManager`. Testet kör identiska GraphQL-frågor två gånger och jämför tjänstobjektets tillstånd före och efter den andra frågan.

#### GraphQlStateTest-fel och möjlig reparation

* **Kan inte lägga till, hoppa över eller filtrera en lista**. Om du råkar ut för ett fel som tyder på att det inte är säkert att lägga till, hoppa över eller filtrera en lista, bör du överväga om klassen kan refactoras på ett bakåtkompatibelt sätt för att använda fabrikerna för de tjänsteklasser som har ändringsbart tillstånd.

* **Klassen har ett ändringsbart läge**. Om själva klassen har ett ändringsbart läge kan du försöka skriva om koden för att kringgå det här läget. Om mutable-läge krävs av prestandaskäl ska du implementera `ResetAfterRequestInterface` och använda `_resetState()` för att återställa objektet till dess ursprungliga konstruerade läge.

* **Den angivna egenskapen $x får inte nås före initieringsmeddelandet**. Fel med den här typen av meddelande tyder på att den angivna egenskapen inte har initierats av konstruktorn. Detta är en form av temporal koppling som uppstår eftersom objektet inte kan användas efter att det först har konstruerats. Den här kopplingen inträffar även om egenskapen är privat eftersom den insamlare som hämtar data från egenskaperna använder PHP-reflektionsfunktionen. I så fall kan du försöka omfaktorisera klassen för att undvika temporal koppling och för att undvika muterbart tillstånd. Om omfaktoriseringen inte löser problemet kan du ändra egenskapstypen till en typ som kan ha värdet null så att den kan initieras till null.  Om egenskapen är en array kan du försöka initiera egenskapen som en tom array.

Kör `GraphQlStateTest` genom att köra `vendor/bin/phpunit -c $(pwd)/dev/tests/integration/phpunit.xml dev/tests/integration/testsuite/Magento/GraphQl/App/GraphQlStateTest.php`.

### ÅterställEfterBegäranTesta

`ResetAfterRequestTest` söker efter alla klasser som implementerar `ResetAfterRequestInterface` och verifierar att `_resetState()` metoden returnerar ett objekts läge till samma läge som det hade efter att ha konstruerats av `ObjectManager`.  Det här testet skapar ett serviceobjekt med `ObjectManager`, klonar sedan objektet, anrop `_resetState()`och jämför sedan båda objekten. Testet anropar inga metoder mellan objektinstansiering och `_resetState()`så att det inte bekräftar att ett ändringsbart tillstånd har återställts. Det finns problem där ett fel eller ett inskrivningsfel `_resetState()` kan ställa in läget på något annat än det var från början.

#### ResetAfterRequestTest-fel och potentiella reparationer

* **Klassen har inkonsekventa egenskapsvärden**. Om testet misslyckas kontrollerar du om en klass har ändrats och resultatet blir att objektet efter konstruktionen har andra egenskapsvärden än efter den `_resetState()` -metoden anropas. Om klassen som du arbetar med inte innehåller `_resetState()` och sedan kontrollera klasshierarkin för en superklass som implementerar den.

* **Den angivna egenskapen $x får inte nås före initieringsmeddelandet**. Det här problemet uppstår också med `GraphQlStateTest`.

  Kör `ResetAfterRequestTest` genom att köra: `vendor/bin/phpunit -c $(pwd)/dev/tests/integration/phpunit.xml dev/tests/integration/testsuite/Magento/Framework/ObjectManager/ResetAfterRequestTest.php`.

### Funktionstestning

Tilläggsutvecklare bör köra WebAPI-funktionstester för GraphQL samt anpassade automatiska eller manuella funktionstester för GraphQL när de distribuerar GraphQL Application Server. Dessa funktionstester hjälper utvecklare att identifiera potentiella fel eller kompatibilitetsproblem.

#### Läge för tillståndsövervakare

När du kör funktionstester (eller manuell testning) kan programservern köras med `--state-monitor mode` aktiveras för att hjälpa till att hitta klasser där tillstånd oavsiktligt återanvänds. Starta programservern normalt, förutom att lägga till `--state-monitor` parameter.

```
bin/magento server:run --state-monitor
```

När varje begäran har bearbetats läggs en ny fil till i `tmp` katalog, till exempel: `var/tmp/StateMonitor-thread-output-50-6nmxiK`. När du är klar med testningen kan dessa filer sammanfogas med `bin/magento server:state-monitor:aggregate-output` som skapar två sammanfogade filer, en i `XML` och en tum `JSON`.

Exempel:

```
/var/workspace/var/tmp/StateMonitor-json-2024-04-10T18:50:39Z-hW0ucN.json
/var/workspace/var/tmp/StateMonitor-junit-2024-04-10T18:50:39Z-oreUco.xml
```

Dessa filer kan inspekteras med alla verktyg du använder för att visa XML eller JSON, som visar de ändrade egenskaperna för serviceobjekt som GraphQlStateTest gör. The `--state-monitor` I läget används samma hopplista och filterlista som GraphQlStateTest.

>[!NOTE]
>
>Använd inte `--state-monitor` produktionsläge. Den är endast avsedd för utveckling och testning. Det skapar många utdatafiler och kommer att köras långsammare än normalt.

>[!NOTE]
>
>`--state-monitor` är inte kompatibelt med PHP-versioner `8.3.0` - `8.3.4` på grund av ett fel i PHP-skräpinsamlaren. Om du använder PHP 8.3 måste du uppgradera till `8.3.5` eller nyare för att använda den här funktionen.

## Kända fel

### Förfrågningar går förlorade om arbetstråd avslutas.

Om det uppstår ett problem med en arbetstråd som gör att arbetstråden avslutas, kommer alla HTTP-begäranden som redan står i kö till samma arbetstråd att få en TCP-socketanslutningsåterställning. Med en omvänd proxy, till exempel NGINX, framför servern visas felen som `502` fel. Medarbetare kan dö av krascher, slut på minneshantering eller PHP-fel i tillägg från tredje part. Standardbeteendet för SVYLLENS HTTP-server orsakar det här problemet. Som standard startas HTTP-servern i `SWOOLE_BASE` läge. I det här läget tilldelas de HTTP-begäranden som kommer in till arbetstrådar i en kö, även om arbetstråden fortfarande bearbetar en tidigare begäran. Om du ändrar detta till `SWOOLE_PROCESS` , underhålls anslutningarna av huvudprocessen och använder betydligt mer kommunikation mellan processer. Nersidan till `SWOOLE_PROCESS` är att det inte stöder PHP ZTS. Läs [Svullnad - dokumentation](https://wiki.swoole.com/en/#/learn?id=swoole_process) för mer information.

### Programservern kan använda tidigare attributkonfigurationer under vissa förhållanden.

The `CatalogGraphQl\Model\Config\AttributeReader` in `2.4.7` innehåller ett sällsynt fel som kan göra att en GraphQL-begäran får ett svar med hjälp av det tidigare tillståndet för attributkonfigurationen. En fix för det här levererades i `2.4-develop`, men inte i tid för `2.4.7` release.
