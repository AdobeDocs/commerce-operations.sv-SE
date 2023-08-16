---
title: Application Server för GraphQL API:er
description: Följ dessa anvisningar för att aktivera API:er för Application Server for GraphQL i din Adobe Commerce-distribution.
badgeCoreBeta: label="2.4.7-beta1" type="informative"
exl-id: 346cc722-131e-4ed0-bc8c-23c3a1e58258
source-git-commit: f085c0a77fe59ff3b2d76abbd6965b6bc8ee69db
workflow-type: tm+mt
source-wordcount: '533'
ht-degree: 0%

---

# Application Server för GraphQL API:er

API:erna för Commerce Application Server för GraphQL gör det möjligt för Adobe Commerce att upprätthålla status mellan Commerce GraphQL API-begäranden och minska starttiden för varje begäran. Genom att dela programstatus mellan processer blir API-begäranden betydligt effektivare.

Den här betaversionen av Application Server är endast tillgänglig för lokala distributioner som kör PHP 8.1 eller 8.2. Det stöder inte molnbaserade distributioner. Det har ännu inte stöd för B2B GraphQL-funktioner. GraphQL-begäranden kanske inte fungerar som väntat i lokala distributioner när den här versionen av PHP-programservern är konfigurerad.

## Vem kan använda Application Server?

Programservern är endast tillgänglig för lokala Commerce-distributioner.

## Aktivera Application Server för GraphQL API:er

The `ApplicationServer` modul (`Magento/ApplicationServer/`) aktiverar Application Server för GraphQL API:er.

För att köra Application Server krävs att tillägget Öppna svullnad och en mindre ändring av Nginx-konfigurationsfilen för distributionen installeras för att den här programservern ska kunna köras lokalt.

### Innan du börjar

Utför dessa två uppgifter innan du aktiverar `ApplicationServer` modul:

* Konfigurera Nginx

* Installera och konfigurera tillägget OpenSvole v22

### Konfigurera Nginx

Din specifika Commerce-distribution avgör hur du konfigurerar Nginx. Vanligtvis heter konfigurationsfilen Nginx som standard `nginx.conf` och placeras i någon av följande kataloger: `/usr/local/nginx/conf`, `/etc/nginx`, eller `/usr/local/etc/nginx`. Se [Nybörjarhandbok](http://nginx.org/en/docs/beginners_guide.html) om du vill ha mer information om hur du konfigurerar Nginx.

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

Du kan installera både tillägget Öppna svullnad för PHP (v22) och Composer-paketen som det här tillägget kräver med ett kommando.

### Installera Öppna svullnad

Ange:

```bash
pecl install openswoole-22.0.0 | composer require openswoole/core:22.1.1
```

Under installationen visas uppmaningar om att aktivera stöd för `openssl`, `mysqlnd`, `sockets`, `http2`och `postgres`. Retur `yes` för alla alternativ utom `postgres`.

### Bekräfta installation av OpenSvole

Kör `php -m | grep openswoole` för att bekräfta att tillägget har aktiverats.

### Vanliga fel vid installation av Open Svole

Alla fel som inträffar under installationen av OpenSvole inträffar vanligtvis under `pecl` installationsfas. Typiska fel kan vara att det saknas `openssl.h` och `pcre2.h` filer. Kontrollera att de här två paketen är installerade på din lokala dator för att åtgärda felen.

* Kontrollera plats för `openssl` genom att köra:

```bash
openssl version -d
```

Det här kommandot visar banan där `openssl` är installerat.

* Kontrollera plats för `pcre2` genom att köra:

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
