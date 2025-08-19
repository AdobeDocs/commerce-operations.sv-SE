---
title: GraphQL Application Server
description: Följ dessa anvisningar för att aktivera GraphQL Application Server i din Adobe Commerce-distribution.
exl-id: 9b223d92-0040-4196-893b-2cf52245ec33
source-git-commit: ed46f48472a51db17e1c3ade9bfe3ab134098548
workflow-type: tm+mt
source-wordcount: '2212'
ht-degree: 0%

---


# GraphQL Application Server

Med Commerce GraphQL Application Server kan Adobe Commerce upprätthålla status bland Commerce GraphQL API-begäranden. GraphQL Application Server, som bygger på svullningstillägget, fungerar som en process med arbetstrådar som hanterar bearbetningen av begäranden. Genom att bevara ett startläge för ett program bland GraphQL API-begäranden förbättrar GraphQL Application Server hanteringen av begäranden och produktens övergripande prestanda. API-förfrågningar blir betydligt effektivare.

GraphQL Application Server finns endast för Adobe Commerce. Det finns inte för Magento Open Source. För Cloud Pro-projekt måste du [skicka in en Adobe Commerce Support](https://experienceleague.adobe.com/sv/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide)-biljett för att aktivera GraphQL Application Server.

>[!NOTE]
>
>GraphQL Application Server är inte kompatibel med [[!DNL Amazon Simple Storage Service (AWS S3)]](https://aws.amazon.com/s3/). Adobe Commerce-kunder i molninfrastruktur som för närvarande använder [!DNL AWS S3] för [fjärrlagring](../configuration/remote-storage/cloud-support.md) kan inte använda GraphQL Application Server.

## Arkitektur

GraphQL Application Server upprätthåller status mellan Commerce GraphQL API-begäranden och eliminerar behovet av att starta. Genom att dela applikationsstatus mellan processer blir GraphQL-förfrågningar betydligt effektivare, vilket minskar svarstiderna med upp till 30 %.

PHP-exekveringsmodellen&quot;share-no&quot; utgör en utmaning när det gäller latenstid eftersom varje begäran kräver att ramverket startas. Denna startprocess innehåller tidskrävande uppgifter som att läsa konfigurationen, konfigurera startprocessen och skapa tjänstklassobjekt.

Det verkar som om logiken för hantering av förfrågningar övergår till en händelselösning på programnivå som åtgärdar utmaningen att effektivisera behandlingen av förfrågningar på företagsnivå. På så sätt elimineras behovet av att starta vid körningen av begäran.

## Fördelar

Med GraphQL Application Server kan Adobe Commerce hantera tillstånd mellan efterföljande Commerce GraphQL API-begäranden. Genom att dela programtillstånd mellan begäranden blir API-förfrågningens effektivitet effektivare genom att minimera belastningen på processerna och optimera hanteringen av förfrågningar. Du kan därför minska svarstiden för GraphQL-begäranden med upp till 30 %.

## Systemkrav

För att köra GraphQL Application Server krävs följande:

* Commerce version 2.4.7+
* PHP 8.2 eller senare
* Tillräckligt RAM och CPU baserat på förväntad belastning
* Svullet PHP-tillägg v5+ (se projektspecifika krav nedan)

### Molnprojekt

Adobe Commerce i molninfrastrukturprojekt innehåller svullnadstillägget som standard. Du kan [aktivera](https://experienceleague.adobe.com/sv/docs/commerce-on-cloud/user-guide/configure/app/php-settings#enable-extensions) den i egenskapen `runtime` för filen `.magento.app.yaml`. Exempel:

```yaml
runtime:
    extensions:
        - swoole
```

### Lokala projekt

Du måste [installera och konfigurera](#install-and-configure-swoole)-tillägget för SVG PHP manuellt för lokala projekt.

## Aktivera och distribuera i molninfrastruktur

Modulen `ApplicationServer` (`Magento/ApplicationServer/`) aktiverar GraphQL Application Server.

### Aktivera Pro-projekt

>[!NOTE]
>
>Programservern är en anmälningsfunktion för Cloud Pro-instanser. Om du vill aktivera det skickar du en supportförfrågan.

När Application Server-funktionen har aktiverats i ditt Pro-projekt utför du följande steg innan du distribuerar GraphQL Application Server:

1. Distribuera Adobe Commerce i molninfrastrukturen med hjälp av molnmallen från grenen [ 2.4.7-appserver](https://github.com/magento/magento-cloud/tree/2.4.7-appserver).
1. Kontrollera att alla dina Commerce-anpassningar och tillägg är [kompatibla](https://developer.adobe.com/commerce/php/development/components/app-server/) med GraphQL Application Server.
1. Klona ditt Commerce Cloud-projekt.
1. Justera inställningarna i filen application-server/nginx.conf.sample om det behövs.
1. Kommentera det aktiva webbavsnittet i filen `project_root/.magento.app.yaml` helt och hållet.
1. Avkommentera följande konfiguration av avsnittet &#39;web&#39; i filen `project_root/.magento.app.yaml` som innehåller kommandot GraphQL Application Server `start`.

   ```yaml
   web:
       upstream:
           socket_family: tcp
           protocol: http
       commands:
           start: ./application-server/start.sh > var/log/application-server-status.log 2>&1
   ```

1. Kontrollera att `/application-server/start.sh` är körbar genom att köra följande kommando:

   ```bash
   chmod +x application-server/start.sh
   ```

1. Lägg till uppdaterade filer i Git-indexet med det här kommandot:

   ```bash
   git add -f .magento.app.yaml application-server/*
   ```

1. Genomför ändringarna med det här kommandot:

   ```bash
   git commit -m "AppServer Enabled"
   ```

### Distribuera Pro-projekt

När du är klar med aktiveringsstegen skickar du ändringarna till Git-databasen för att distribuera GraphQL Application Server:

```bash
git push
```

### Aktivera startprojekt

Utför följande steg innan du distribuerar GraphQL Application Server i Starter-projekt:

1. Distribuera Adobe Commerce i molninfrastrukturen med hjälp av molnmallen från grenen [ 2.4.7-appserver](https://github.com/magento/magento-cloud/tree/2.4.7-appserver).
1. Kontrollera att alla Commerce-anpassningar och tillägg är kompatibla med GraphQL Application Server.
1. Bekräfta att miljövariabeln `CRYPT_KEY` är inställd för din instans. Du kan kontrollera den här variabelns status på molnkonsolen.
1. Klona ditt Commerce Cloud-projekt.
1. Byt namn på `application-server/.magento/.magento.app.yaml.sample` till `application-server/.magento/.magento.app.yaml` och justera inställningarna i .magento.app.yaml om det behövs.
1. Avkommentera konfigurationen för följande väg i filen `project_root/.magento/routes.yaml` för att omdirigera `/graphql`-trafik till GraphQL Application Server.

   ```yaml
   "http://{all}/graphql":
       type: upstream
       upstream: "application-server:http"
   ```

1. Avkommentera avsnittet `files` i filen `.magento/services.yaml`.

   ```yaml
   files:
       type: network-storage:2.0
       disk: 5120
   ```

1. Avkommentera `TEMPORARY SHARED MOUNTS`-delen av monteringskonfigurationen i `.magento.app.yaml`-filen.

   ```yaml
   "var_shared":
       source: "service"
       service: "files"
       source_path: "var"
   "app/etc_shared":
       source: "service"
       service: "files"
       source_path: "etc"
   "pub/media_shared":
       source: "service"
       service: "files"
       source_path: "media"
   "pub/static_shared":
       source: "service"
       service: "files"
       source_path: "static"
   ```

1. Lägg till uppdaterade filer i Git-indexet:

   ```bash
   git add -f .magento.app.yaml .magento/routes.yaml .magento/services.yaml application-server/.magento/*
   ```

1. Genomför dina ändringar och skicka dem för att aktivera en distribution:

   ```bash
   git commit -m "Enabling AppServer: initial changes"
   git push
   ```

1. Använd SSH för att logga in i fjärrmolnmiljön (_inte_ appen `application-server` ):

   ```bash
   magento-cloud ssh -p <project-ID> -e <environment-ID>
   ```

1. Synkronisera data från de lokala monteringarna till de delade mängderna:

   ```bash
   rsync -avz var/* var_shared/
   rsync -avz app/etc/* app/etc_shared/
   rsync -avz pub/media/* pub/media_shared/
   rsync -avz pub/static/* pub/static_shared/
   ```

1. Kommentera `DEFAULT MOUNTS` och `TEMPORARY SHARED MOUNTS` delar av monteringskonfigurationen i filen `.magento.app.yaml`.

   ```yaml
   #"var": "shared:files/var"
   #"app/etc": "shared:files/etc"
   #"pub/media": "shared:files/media"
   #"pub/static": "shared:files/static"
   
   #"var_shared":
   #    source: "service"
   #    service: "files"
   #    source_path: "var"
   #"app/etc_shared":
   #    source: "service"
   #    service: "files"
   #    source_path: "etc"
   #"pub/media_shared":
   #    source: "service"
   #    service: "files"
   #    source_path: "media"
   #"pub/static_shared":
   #    source: "service"
   #    service: "files"
   #    source_path: "static"
   ```

1. Avkommentera `OLD LOCAL MOUNTS` och `SHARED MOUNTS` delar av monteringskonfigurationen i `.magento.app.yaml`-filen.

   ```yaml
   "var_old": "shared:files/var"
   "app/etc_old": "shared:files/etc"
   "pub/media_old": "shared:files/media"
   "pub/static_old": "shared:files/static"
   
   "var":
       source: "service"
       service: "files"
       source_path: "var"
   "app/etc":
       source: "service"
       service: "files"
       source_path: "etc"
   "pub/media":
       source: "service"
       service: "files"
       source_path: "media"
   "pub/static":
       source: "service"
       service: "files"
       source_path: "static"
   ```

1. Lägg till den uppdaterade filen i Git-indexet, implementera ändringar och skicka för att aktivera en distribution:

   ```bash
   git add -f .magento.app.yaml
   git commit -m "Enabling AppServer: switch mounts"
   git push
   ```

1. Kontrollera att filer från `*_old` kataloger finns i de faktiska katalogerna.

1. Rensa gamla lokala berg:

   ```bash
   rm -rf var_old/*
   rm -rf app/etc_old/*
   rm -rf pub/media_old/*
   rm -rf pub/static_old/*
   ```

1. Kommentera den `OLD LOCAL MOUNTS` delen av monteringskonfigurationen i filen `.magento.app.yaml`.

   ```yaml
   #"var_old": "shared:files/var"
   #"app/etc_old": "shared:files/etc"
   #"pub/media_old": "shared:files/media"
   #"pub/static_old": "shared:files/static"
   ```

1. Lägg till den uppdaterade filen i Git-indexet, implementera ändringar och skicka för att aktivera en distribution:

   ```bash
   git add -f .magento.app.yaml
   git commit -m "Enabling AppServer: finish"
   git push
   ```

>[!NOTE]
>
>Se till att alla anpassade inställningar i rotfilen `.magento.app.yaml` migreras korrekt till filen `application-server/.magento/.magento.app.yaml`. När filen `application-server/.magento/.magento.app.yaml` har lagts till i ditt projekt bör du behålla den förutom rotfilen `.magento.app.yaml`. Om du till exempel behöver [konfigurera tjänsten RabbitMQ ](https://experienceleague.adobe.com/sv/docs/commerce-on-cloud/user-guide/configure/service/rabbitmq) eller [hantera webbegenskaper](https://experienceleague.adobe.com/sv/docs/commerce-on-cloud/user-guide/configure/app/properties/web-property) bör du även lägga till samma konfiguration i `application-server/.magento/.magento.app.yaml`.

### Verifiera aktivering i molnprojekt

1. Utför en GraphQL-fråga eller mutation mot din instans för att bekräfta att slutpunkten `graphql` är tillgänglig. Exempel:

   ```
   mutation {  
    createEmptyCart
   }
   ```

   Det förväntade svaret ska likna följande exempel:

   ```json
   {    
    "data": {        
        "createEmptyCart": "HLATPzcLw5ylDf76IC92nxdO2hXSXOrv"    
        }
    }
   ```

1. Använd SSH för att komma åt din molninstans. `project_root/var/log/application-server.log` ska innehålla en ny loggpost för varje GraphQL-begäran.

1. Du kan också kontrollera om GraphQL Application Server körs genom att köra följande kommando:

   ```bash
   ps aux|grep php
   ```

   Du bör se en `bin/magento server:run`-process med flera trådar.

Om dessa verifieringssteg lyckas körs GraphQL Application Server och hanterar `/graphql` begäranden.

## Aktivera lokala projekt

Modulen `ApplicationServer` (`Magento/ApplicationServer/`) aktiverar API:er för GraphQL Application Server för GraphQL.

Om du kör GraphQL Application Server lokalt måste du installera SVULLE-tillägget och göra en mindre ändring i Nginx-konfigurationsfilen för distributionen.

### Förutsättningar

Utför följande steg innan du aktiverar modulen `ApplicationServer`:

* Konfigurera Nginx
* Installera och konfigurera tillägget SVULLA v5+

#### Konfigurera Nginx

Din specifika Commerce-distribution avgör hur du konfigurerar Nginx. I allmänhet är Nginx-konfigurationsfilen som standard `nginx.conf` och placeras i någon av följande kataloger: `/usr/local/nginx/conf`, `/etc/nginx` eller `/usr/local/etc/nginx`. Mer information om hur du konfigurerar Nginx finns i _[nybörjarhandboken](https://nginx.org/en/docs/beginners_guide.html)_.

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

Under installationen visas ett meddelande i Adobe Commerce om att aktivera stöd för `openssl`, `mysqlnd`, `sockets`, `http2` och `postgres`. Ange `yes` för alla alternativ utom `postgres`.

### Verifiera installation med svullnad

Bekräfta att tillägget har aktiverats:

```bash
php -m | grep swoole
```

### Vanliga fel vid installation med svepfunktion

Alla fel som inträffar under svullnad inträffar vanligtvis under installationsfasen för `pecl`. Typiska fel är bland annat att `openssl.h`- och `pcre2.h`-filer saknas. Kontrollera att de här två paketen är installerade på din lokala dator för att åtgärda felen.

* Kontrollera platsen för `openssl` genom att köra:

```bash
openssl version -d
```

Det här kommandot visar sökvägen där `openssl` är installerad.

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

Om du vill lösa problem relaterade till `openssl` kör du:

```bash
export LDFLAGS="-L/opt/homebrew/etc/openssl@3/lib" export CPPFLAGS="-I/opt/homebrew/etc/openssl@3/include"
```

Bekräfta att du använder sökvägen från din lokala `dev`-miljö.

#### Bekräfta lösning av problem relaterade till openssl

Du kan köra följande kommando igen för att kontrollera om problem som är relaterade till öppning har åtgärdats:

```bash
pecl install swoole
```

#### Lös problem med pcre2.h

Om du vill lösa problem som rör `pcre2.h` länkar du sökvägen `pcre2.h` till den installerade PHP-tilläggskatalogen. Din specifika installerade version av PHP och `pcr2.h` avgör vilken version av kommandot som du bör använda.

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

* Kontrollera om filen `/var/log/application-server.log` innehåller poster som är relaterade till bearbetade GraphQL-begäranden.
* Försök ansluta till HTTP-porten som GraphQL Application Server körs på. Till exempel: `curl -g 'http://localhost:9501/graph`.

### Bekräfta att GraphQL-begäranden behandlas

GraphQL Application Server lägger till svarshuvudet `X-Backend` med värdet `graphql_server` i varje begäran som bearbetas. Om du vill kontrollera om GraphQL Application Server har hanterat en begäran kan du kontrollera den här svarshuvudet.

### Bekräfta kompatibilitet för tillägg och anpassning

Tilläggsutvecklare och handlare bör först kontrollera att deras kod för tillägg och anpassning följer riktlinjerna som beskrivs i _[Tekniska riktlinjer](https://developer.adobe.com/commerce/php/coding-standards/technical-guidelines/)_.

Tänk på följande när du utvärderar koden:

* Tjänstklasser (d.v.s. klasser som tillhandahåller beteende men inte data, t.ex. `EventManager`) får inte ha ett ändringsbart tillstånd.
* Undvik temporal koppling.

## Inaktivera GraphQL Application Server

Hur du inaktiverar GraphQL Application Server varierar beroende på om servern körs lokalt eller i molnet.

### Inaktivera GraphQL Application Server (molnet)

1. Ta bort alla nya filer och eventuella andra kodändringar som ingick i implementeringen av `AppServer Enabled` under dina förberedelser för distributionen.

1. Genomför ändringarna med det här kommandot:

   ```bash
   git commit -m "AppServer Disabled"
   ```

1. Distribuera dessa ändringar med det här kommandot:

   ```bash
   git push
   ```

### Inaktivera GraphQL Application Server (lokalt)

1. Kommentera avsnittet `/graphql` i filen `nginx.conf` som du lade till när du aktiverade GraphQL Application Server.
1. Starta om nästa.

Den här metoden för att inaktivera GraphQL Application Server kan vara användbar för att testa eller jämföra prestanda snabbt.

### Bekräfta att GraphQL Application Server är inaktiverad

Bekräfta att `php-fpm` bearbetar GraphQL-begäranden i stället för GraphQL Application Server genom att ange följande kommando: `ps aux | grep php`.

När GraphQL Application Server har inaktiverats:

* `bin/magento server:run` är inaktiv.
* `var/log/application-server.log` innehåller inga poster efter GraphQL-begäranden.

## Integrerings- och funktionstester för GraphQL Application Server

Tilläggsutvecklare kan köra två integrationstester för att verifiera tilläggskompatibiliteten med GraphQL Application Server: `GraphQlStateTest` och `ResetAfterRequestTest`.

### GraphQlStateTest

`GraphQlStateTest` identifierar tillstånd i delade objekt som inte ska återanvändas för flera begäranden.

Det här testet är utformat för att identifiera lägesändringar i tjänstobjekt som skapas av `ObjectManager`. Testet kör identiska GraphQL-frågor två gånger och jämför tjänstobjektets tillstånd före och efter den andra frågan.

#### GraphQlStateTest-fel och möjlig reparation

* **Det går inte att lägga till, hoppa över eller filtrera en lista**. Om du får det här felet kan du försöka omfaktorisera klassen så att den använder fabriker för tjänsteklasser med ändringsbart tillstånd.

* **Klassen uppvisar ett ändringsbart tillstånd**. Om själva klassen har ett ändringsbart läge kan du försöka skriva om koden för att kringgå det här läget. Om det ändringsbara läget krävs av prestandaskäl implementerar du `ResetAfterRequestInterface` och använder `_resetState()` för att återställa objektet till dess ursprungliga konstruktionstillstånd.

* **Den typbestämda egenskapen $x får inte nås före initieringsmeddelandet**. Fel med den här typen av meddelande tyder på att den angivna egenskapen inte har initierats av konstruktorn. Detta är en form av temporal koppling som uppstår eftersom objektet inte kan användas efter att det först har konstruerats. Den här kopplingen inträffar även om egenskapen är privat eftersom den insamlare som hämtar data från egenskaperna använder PHP-reflektionsfunktionen. I så fall kan du försöka omfaktorisera klassen för att undvika temporal koppling och för att undvika muterbart tillstånd. Om omfaktoriseringen inte löser problemet kan du ändra egenskapstypen till en typ som kan ha värdet null så att den kan initieras till null.  Om egenskapen är en array kan du försöka initiera egenskapen som en tom array.

Kör `GraphQlStateTest` genom att köra `vendor/bin/phpunit -c $(pwd)/dev/tests/integration/phpunit.xml dev/tests/integration/testsuite/Magento/GraphQl/App/GraphQlStateTest.php`.

### ÅterställEfterBegäranTesta

`ResetAfterRequestTest` söker efter alla klasser som implementerar `ResetAfterRequestInterface` och verifierar att metoden `_resetState()` returnerar ett objekts tillstånd till samma läge som det hade efter att ha konstruerats av `ObjectManager`.  Det här testet skapar ett tjänstobjekt med `ObjectManager`, klonar sedan objektet, anropar `_resetState()` och jämför sedan båda objekten. Testet anropar inga metoder mellan objektinstansiering och `_resetState()`, så det bekräftar inte att något muterbart tillstånd återställs. Det finns problem där ett fel eller ett stavfel i `_resetState()` kan ställa in läget på något annat än det var från början.

#### ResetAfterRequestTest-fel och potentiella reparationer

* **Klassen har inkonsekventa egenskapsvärden**. Om testet misslyckas kontrollerar du om en klass har ändrats och resultatet blir att objektet efter konstruktionen har andra egenskapsvärden än det har efter att metoden `_resetState()` anropats. Om klassen som du arbetar med inte innehåller själva metoden `_resetState()` kontrollerar du i klasshierarkin om det finns en superklass som implementerar den.

* **Den typbestämda egenskapen $x får inte nås före initieringsmeddelandet**. Det här problemet inträffar även med `GraphQlStateTest`.

  Kör `ResetAfterRequestTest` genom att köra: `vendor/bin/phpunit -c $(pwd)/dev/tests/integration/phpunit.xml dev/tests/integration/testsuite/Magento/Framework/ObjectManager/ResetAfterRequestTest.php`.

### Funktionstestning

När tilläggsutvecklare distribuerar GraphQL Application Server bör de köra WebAPI-funktionstester och anpassade automatiska eller manuella funktionstester för GraphQL. Dessa funktionstester hjälper utvecklare att identifiera potentiella fel eller kompatibilitetsproblem.

#### Läge för tillståndsövervakare

När funktionstester körs (eller manuell testning) kan GraphQL Application Server köras med `--state-monitor mode` aktiverat för att hjälpa till att hitta klasser där tillståndet oavsiktligt återanvänds. Starta programservern normalt, förutom att lägga till parametern `--state-monitor`.

```
bin/magento server:run --state-monitor
```

När varje begäran har bearbetats läggs en ny fil till i katalogen `tmp`, till exempel: `var/tmp/StateMonitor-thread-output-50-6nmxiK`. När du har testat klart kan dessa filer sammanfogas med kommandot `bin/magento server:state-monitor:aggregate-output`, vilket skapar två sammanfogade filer, en i `XML` och en i `JSON`.

Exempel:

```
/var/workspace/var/tmp/StateMonitor-json-2024-04-10T18:50:39Z-hW0ucN.json
/var/workspace/var/tmp/StateMonitor-junit-2024-04-10T18:50:39Z-oreUco.xml
```

De här filerna kan inspekteras med alla verktyg som du använder för att visa XML eller JSON som visar de ändrade egenskaperna för serviceobjekt som `GraphQlStateTest` gör. Läget `--state-monitor` använder samma hopplista och filterlista som GraphQlStateTest.

>[!NOTE]
>
>Använd inte läget `--state-monitor` i produktionen. Den är endast avsedd för utveckling och testning. Den skapar många utdatafiler och körs långsammare än normalt.

>[!NOTE]
>
>`--state-monitor` är inte kompatibel med PHP-versionerna `8.3.0` - `8.3.4` på grund av ett fel i PHP-skräpinsamlaren. Om du använder PHP 8.3 måste du uppgradera till `8.3.5` eller senare för att kunna använda den här funktionen.
