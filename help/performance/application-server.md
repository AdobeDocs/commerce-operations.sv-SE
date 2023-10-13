---
title: Application Server för GraphQL API:er
description: Följ dessa anvisningar för att aktivera API:er för Application Server for GraphQL i din Adobe Commerce-distribution.
badgeCoreBeta: label="2.4.7-beta" type="informative"
exl-id: 9b223d92-0040-4196-893b-2cf52245ec33
source-git-commit: b7639e8830b2cab971e3e22285d91105b64e9a6e
workflow-type: tm+mt
source-wordcount: '1768'
ht-degree: 0%

---

# Application Server för GraphQL API:er

API:erna för Commerce Application Server för GraphQL gör det möjligt för Adobe Commerce att upprätthålla status bland API-begäranden för Commerce GraphQL. Programservern, som bygger på tillägget OpenSvole, fungerar som en process med arbetstrådar som hanterar bearbetningen av begäranden. Genom att bevara ett startläge för ett program bland GraphQL API-begäranden förbättrar Application Server hanteringen av begäranden och produktens övergripande prestanda. API-förfrågningar blir betydligt effektivare.

Programservern stöds endast på Cloud Starter och lokala distributioner. Det är inte tillgängligt för instanser av Cloud Pro under betaversionen. Den är inte tillgänglig för distributioner i Magento Open Source.

## Programserverarkitektur - översikt

Application Server underhåller status mellan Commerce GraphQL API-begäranden och eliminerar behovet av startspärr. Genom att dela applikationsstatus mellan processer blir GraphQL-förfrågningar betydligt effektivare, vilket minskar svarstiderna med upp till 30 %.

PHP-exekveringsmodellen&quot;share-no&quot; utgör en utmaning när det gäller latenstid eftersom varje begäran kräver att ramverket startas. Denna startprocess innehåller tidskrävande uppgifter som att läsa konfigurationen, konfigurera startprocessen och skapa tjänstklassobjekt.

Det verkar som om logiken för hantering av förfrågningar övergår till en händelselösning på programnivå som åtgärdar utmaningen att effektivisera behandlingen av förfrågningar på företagsnivå. På så sätt elimineras behovet av att starta vid körningen av begäran.

## Fördelar med att använda Application Server

Med Application Server kan Adobe Commerce hantera tillstånd mellan efterföljande Commerce GraphQL API-begäranden. Genom att dela programtillstånd mellan begäranden blir API-förfrågningens effektivitet effektivare genom att minimera belastningen på processerna och optimera hanteringen av förfrågningar. Därför kan svarstiden för GraphQL-begäranden minskas till 30 %.

## Systemkrav

Följande krävs för att köra programservern:

* PHP 8.2 eller senare
* Öppna PHP-tillägget v22+ installerat
* Tillräckligt RAM och processor baserat på förväntad belastning

## Aktivera Application Server för Cloud Starter

The `ApplicationServer` modul (`Magento/ApplicationServer/`) aktiverar Application Server för GraphQL API:er. Programservern stöds endast på lokala distributioner och Cloud Starter-distributioner. Det är inte tillgängligt för instanser av Cloud Pro under betaversionen.

### Innan du påbörjar en Cloud Starter-distribution

Utför följande uppgifter innan du distribuerar Application Server:

1. Bekräfta att Adobe Commerce är installerat på Commerce Cloud.
1. Bekräfta att `CRYPT_KEY` Miljövariabeln ställs in för din instans. Du kan kontrollera statusen för den här variabeln på Cloud Project Portal (gränssnittet för introduktion).
1. Klona ditt Commerce Cloud-projekt.
1. Skapa en `graphql` i din `project_root` mapp.
1. Lägg till ytterligare anpassad `.magento.app.yaml` filen finns i [magento.app.yaml, filinnehåll](#magento.app.yaml-file-content) ditt ämne `project_root/graphql` mapp.
1. Redigera `project_root/.magento/routes.yaml` fil som innehåller dessa direktiv:

   ```yaml
   # The routes of the project.
   #
   # Each route describes how an incoming URL is going to be processed.
   
   "http://{default}/":
     type: upstream
     upstream: "mymagento:http"
   
   "http://{default}/graphql":
     type: upstream
     upstream: "graphql:http"
   ```

1. Lägg till uppdaterade filer i Git-indexet med det här kommandot:

   ```bash
   git add -f php.ini graphql/.magento.app.yaml .magento/routes.yaml swoole.so
   ```

1. Genomför ändringarna med det här kommandot:

   ```bash
   git commit -m "AppServer Enabled"
   ```

### Distribuera Application Server på molnstartaren

När du har utfört de nödvändiga åtgärderna distribuerar du Application Server med det här kommandot:

```bash
git push
```

### Verifiera programserveraktivering på molnstart

1. Öppna användargränssnittet för ditt Creative Cloud-projekt. Ytterligare en SSH-åtkomstpunkt för `graphql` program.

1. Använd SSH för att komma åt molninstansen med åtkomstpunkten graphql och kör sedan följande kommando:

   ```bash
   ps aux|grep php
   ```

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

1. Använd SSH för att komma åt din molninstans via åtkomstpunkten för GraphQL-programmet. The `project_root/var/log/magento-server.log` ska innehålla en ny loggpost för varje GraphQL-begäran.

Om dessa verifieringssteg lyckas kan du fortsätta med körningen av testcykeln.


## Aktivera programserver för lokala distributioner

The `ApplicationServer` modul (`Magento/ApplicationServer/`) aktiverar Application Server för GraphQL API:er.

För att köra Application Server krävs att tillägget Öppna svullnad och en mindre ändring av Nginx-konfigurationsfilen för distributionen installeras för att den här programservern ska kunna köras lokalt.

### Innan du påbörjar en lokal distribution

Utför dessa två uppgifter innan du aktiverar `ApplicationServer` modul:

* Konfigurera Nginx

* Installera och konfigurera tillägget OpenSvole v22

### Konfigurera Nginx

Din specifika Commerce-distribution avgör hur du konfigurerar Nginx. Vanligtvis heter konfigurationsfilen Nginx som standard `nginx.conf` och placeras i någon av följande kataloger: `/usr/local/nginx/conf`, `/etc/nginx`, eller `/usr/local/etc/nginx`. Se [Nybörjarhandbok](https://nginx.org/en/docs/beginners_guide.html) om du vill ha mer information om hur du konfigurerar Nginx.

Exempel på Nginx-konfiguration:

```conf
location /graphql {
    proxy_set_header Host $http_host;
    proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;

    proxy_pass http://127.0.0.1:9501/graphql;
}
```

### Installera och konfigurera Öppna SVYLLNING

Installera tillägget Open v22 om du vill köra programservern lokalt. Det finns flera sätt att installera det här tillägget.

## Kör programserver

Starta programservern:

```bash
bin/magento server:run
```

Det här kommandot startar en HTTP-port på 9501. När Application Server startas blir port 9501 en HTTP-proxyserver för alla GraphQL-frågor.

## Exempel: Installera OpenSvole (OSX)

Den här proceduren illustrerar hur du installerar tillägget Öppna i PHP 8.2 för OSX-baserade system. Det är ett av flera sätt att installera tillägget Öppna svullnad.

### Installera Öppna svullnad

Ange:

```bash
pecl install openswoole-22.0.0
composer require openswoole/core:22.1.1
```

Under installationen visas uppmaningar om att aktivera stöd för `openssl`, `mysqlnd`, `sockets`, `http2`och `postgres`. Retur `yes` för alla alternativ utom `postgres`.

### Bekräfta installation av OpenSvole

Kör `php -m | grep openswoole` för att bekräfta att tillägget har aktiverats.

### Vanliga fel vid installation av Open Svole

Alla fel som inträffar under installationen av OpenSvole inträffar vanligtvis under `pecl` installationsfas. Typiska fel kan vara att det saknas `openssl.h` och `pcre2.h` filer. Kontrollera att de här två paketen är installerade på din lokala dator för att åtgärda felen.

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
pecl install openswoole-22.0.0
```

#### Lös problem med pcre2.h

Lös problem relaterade till `pcre2.h`, länkar samman `pcre2.h` sökväg till den installerade PHP-tilläggskatalogen. Din specifika installerade version av PHP och `pcr2.h` bestämmer vilken version av kommandot du ska använda.

### Bekräfta att programservern körs

Kör följande kommando för att bekräfta att programservern körs i din distribution:

```bash
ps aux | grep php
```

Ytterligare sätt att bekräfta att Application Server körs är:

* Kontrollera `/var/log/magento-server.log` för poster som är relaterade till bearbetade GraphQL-begäranden.
* Försök ansluta till HTTP-porten som programservern körs på. Exempel: `curl -g 'http://localhost:9501/graph`.

### Bekräfta att GraphQL-begäranden behandlas av programservern

Application Server lägger till `X-Backend` svarshuvud med värdet `graphql_server` på varje begäran som behandlas. Om du vill kontrollera om en begäran har hanterats av Application Server, söker du efter den här svarshuvudet.

### Bekräfta kompatibilitet för tillägg och anpassning med Application Server

Tilläggsutvecklare och handlare bör först kontrollera att deras kod för tillägg och anpassning följer de tekniska riktlinjer som beskrivs i [Tekniska riktlinjer](https://developer.adobe.com/commerce/php/coding-standards/technical-guidelines/).

Tänk på följande när du utvärderar koden:

* Tjänstklasser (d.v.s. klasser som tillhandahåller beteende men inte data, t.ex. `EventManager`) ska inte ha ett ändringsbart tillstånd.
* Undvik temporal koppling.

## Inaktivera programserver

Hur du inaktiverar Application Server varierar beroende på om servern körs lokalt eller i molnet.

### Inaktivera programserver på molnstart

1. Ta bort alla nya filer och andra kodändringar som ingår i `AppServer Enabled` implementera under dina förberedelser för driftsättningen.

1. Genomför ändringarna med det här kommandot:

   ```bash
   git commit -m "AppServer Disabled"
   ```

1. Distribuera dessa ändringar med det här kommandot:

   ```bash
   git push
   ```

### Inaktivera programserver

1. Kommentera `/graphql` avsnitt i `nginx.conf` som du lade till när du aktiverade Application Server.
1. Starta om nästa.

Den här metoden för att inaktivera Application Server kan vara användbar för att snabbt testa eller jämföra prestanda.

### Bekräfta att programservern är inaktiverad

Bekräfta att GraphQL-begäranden behandlas av `php-fpm` I stället för Application Server anger du följande kommando: `ps aux | grep php`.

När programservern har inaktiverats:

* `bin/magento server:run` är inaktiv.
* `var/log/magento-server.log` innehåller inga poster efter GraphQL begäran.

## Integration- och funktionstester för PHP Application Server

Extension-utvecklare kan köra två integrationstester för att verifiera att tillägg är kompatibla med Application Server: `GraphQlStateTest` och `ResetAfterRequestTest`.

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

Tilläggsutvecklare bör köra WebAPI-funktionstester för GraphQL samt anpassade automatiska eller manuella funktionstester för GraphQL när programservern distribueras. Dessa funktionstester hjälper utvecklare att identifiera potentiella fel eller kompatibilitetsproblem.

## magento.app.yaml, filinnehåll

Se [Innan du påbörjar en Cloud Starter-distribution](#Before-you-begin-a-Cloud-Starter-deployment) för instruktioner om hur du lägger till följande kod i `project_root/graphql` mapp.

```yaml
name: graphql
# The toolstack used to build the application.
type: php:8.2
build:
    flavor: none
 
source:
    root: /
dependencies:
    php:
        composer/composer: '2.5.5'
 
# Enable extensions required by Magento 2
runtime:
    extensions:
        - xsl
        - sodium
 
# The relationships of the application with services or other applications.
# The left-hand side is the name of the relationship as it will be exposed
# to the application in the environment variable. The right-hand
# side is in the form `<service name>:<endpoint name>`.
relationships:
    database: "mysql:mysql"
    redis: "redis:redis"
    opensearch: "opensearch:opensearch"
 
# The configuration of app when it is exposed to the web.
web:
    commands:
        start: "php -dopcache.enable_cli=1 -dopcache.validate_timestamps=0 bin/magento server:run -vvv  --port=${PORT:-80} > ${MAGENTO_CLOUD_APP_DIR}/var/log/magento-server.log 2>&1"
    upstream:
        socket_family: tcp
        protocol: http
    locations:
        '/':
            root: "pub"
            passthru: true
 
# The size of the persistent disk of the application (in MB).
disk: 5120
 
# The mounts that will be performed when the package is deployed.
mounts:
    "var": "shared:files/var"
    "app/etc": "shared:files/etc"
    "pub/media": "shared:files/media"
    "pub/static": "shared:files/static"
 
hooks:
    # We run build hooks before your application has been packaged.
    build: |
        set -e
        composer install
        php ./vendor/bin/ece-tools run scenario/build/generate.xml
        php ./vendor/bin/ece-tools run scenario/build/transfer.xml
    # We run deploy hook after your application has been deployed and started.
    deploy: |
        php ./vendor/bin/ece-tools run scenario/deploy.xml
    # We run post deploy hook to clean and warm the cache. Available with ECE-Tools 2002.0.10.
    post_deploy: |
        php ./vendor/bin/ece-tools run scenario/post-deploy.xml
```
