---
title: Avancerad lack-konfiguration
description: Konfigurera avancerade lack-funktioner, inklusive hälsokontroll, respitläge och helskärmsläge.
feature: Configuration, Cache
exl-id: 178bd675-6ed0-40cc-9455-08a11b32c054
source-git-commit: a2bd4139aac1044e7e5ca8fcf2114b7f7e9e9b68
workflow-type: tm+mt
source-wordcount: '892'
ht-degree: 0%

---

# Avancerad lack-konfiguration

På engelska finns flera funktioner som förhindrar kunder från att drabbas av långa förseningar och timeout när Commerce-servern inte fungerar som den ska. Dessa funktioner kan konfigureras i `default.vcl` -fil. I det här avsnittet beskrivs de tillägg som finns i den VCL-fil (Varnish Configuration Language) som du hämtar från administratören.

Se [Referenshandbok för lack](https://varnish-cache.org/docs/6.3/reference/index.html) om du vill ha mer information om hur du använder Konfigurationsspråk för engelska.

## Hälsokontroll

Funktionen för hälsokontroll av lack avfrågar Commerce-servern för att avgöra om den svarar i tid. Om det svarar normalt genereras nytt innehåll när TTL-perioden (Time to Live) har gått ut. Om inte, har Varnish alltid kvar sitt gamla innehåll.

I Commerce definieras följande standardhälsokontroll:

```conf
.probe = {
    .url = "/pub/health_check.php";
    .timeout = 2s;
    .interval = 5s;
    .window = 10;
    .threshold = 5;
    }
```

Var femte sekund anropar den här hälsokontrollen `pub/health_check.php` skript. Det här skriptet kontrollerar tillgängligheten för servern, varje databas och Redis (om det är installerat). Skriptet måste returnera ett svar inom 2 sekunder. Om skriptet fastställer att någon av dessa resurser inte fungerar returneras en HTTP-felkod på 500. Om den här felkoden tas emot i sex av tio försök anses serverdelen vara felfri.

The `health_check.php` skriptet finns i `pub` katalog. Om Commerce-rotkatalogen är `pub`och se sedan till att ändra banan i `url` parameter från `/pub/health_check.php` till `health_check.php`.

Mer information finns i [Djurhälsokontroller](https://varnish-cache.org/docs/6.3/users-guide/vcl-backends.html?highlight=health%20check#health-checks) dokumentation.

## Behagelläge

Med Grace-läget kan Varnish behålla ett objekt i cachen utanför dess TTL-värde. Slutgiltigt innehåll kan sedan användas medan det hämtar en ny version. Detta förbättrar trafikflödet och minskar inläsningstiden. Det används i följande situationer:

- När Commerce-serverdelen är felfri, men en begäran tar längre tid än normalt
- När Commerce-serverdelen inte är hälsosam.

The `vcl_hit` subrutin definierar hur lack svarar på en begäran om objekt som har cache-lagrats.

### När Commerce-serverdelen är hälsosam

När hälsokontrollerna avgör att Commerce-serverdelen är hälsosam kontrollerar lack om tiden ligger kvar inom fristen. Standardrespitperioden är 300 sekunder, men en handlare kan ange värdet från administratören enligt beskrivningen i [Konfigurera Commerce att använda engelska](configure-varnish-commerce.md). Om respitperioden inte har gått ut levererar engelska det inaktuella innehållet och uppdaterar objektet asynkront från Commerce-servern. Om respitperioden har gått ut, skickar Varnish det inaktuella innehållet och uppdaterar objektet synkront från Commerce-serverdelen.

Den maximala tid som varnish skickar ett inaktuellt objekt är summan av respitperioden (300 sekunder som standard) och TTL-värdet (86400 sekunder som standard).

Ändra standardrespitperioden från `default.vcl` -fil, redigera följande rad i `vcl_hit` subrutin:

```conf
if (obj.ttl + 300s > 0s) {
```

### När Commerce-serverdelen inte är felfri

Om Commerce-serverdelen inte är responsiv, visar Varnish gammalt innehåll från cache i tre dagar (eller enligt definitionen i `beresp.grace`) plus återstående TTL (som är en dag som standard), såvida inte det cachelagrade innehållet rensas manuellt.

## Saint-läge

I läget Saint exkluderas ohälsosamma bakgrunder under en konfigurerbar tidsperiod. Därför kan ohälsosamma serverdelar inte generera trafik när Varnish används som belastningsutjämnare. Saint-läget kan användas i respitläge för att möjliggöra komplex hantering av ohälsosamma serverdelsservrar. Om till exempel en backend-server inte är felfri kan försök dirigeras till en annan server. Om alla andra servrar är nere kan du leverera inaktuella cachelagrade objekt. Värdar i helskärmsläget och utbrottsperioder definieras i `default.vcl` -fil.

Saint-läge kan också användas när Commerce-instanser tas offline för att utföra underhålls- och uppgraderingsuppgifter utan att det påverkar tillgängligheten för Commerce-webbplatsen.

### Förutsättningar för Saint-läge

Ange en dator som primär installation. Installera huvudinstansen av Commerce, mySQL-databasen och Varnish på den här datorn.

På alla andra datorer måste Commerce-instansen ha åtkomst till den primära datorns mySQL-databas. De sekundära datorerna bör också ha tillgång till filerna för den primära Commerce-instansen.

Alternativt kan versionshantering av statiska filer inaktiveras på alla datorer. Det här kan du komma åt från administratören under **Lager** > Inställningar > **Konfiguration** > **Avancerat** > **Utvecklare** > **Inställningar för statiska filer** > **Signera statiska filer** = **Nej**.

Slutligen måste alla handelsinstanser vara i produktionsläge. Rensa cacheminnet för varje instans innan lack startas. Gå till Admin **System** > Verktyg > **Cachehantering** och klicka **Rensa Magento-cache**. Du kan också köra följande kommando för att rensa cachen:

```bash
bin/magento cache:flush
```

### Installation

Saint-läget ingår inte i Varnish-paketet. Det är en separat version `vmod` som måste hämtas och installeras. Därför bör du kompilera om Varnish från källan enligt följande artiklar:

- [Installerar lack 6.4](https://varnish-cache.org/docs/6.4/installation/install.html)
- [Installerar lack 6.0](https://varnish-cache.org/docs/6.0/installation/install.html) (LTS)

När du har kompilerat om kan du installera modulen för det smarta läget. I allmänhet gör du så här:

1. Hämta källkoden från [Finska moduler](https://github.com/varnish/varnish-modules). Klona Git-versionen (överordnad version) eftersom 0.9.x-versionerna innehåller ett källkodsfel.
1. Bygg källkoden med autoverktyg:

   ```bash
   sudo apt-get install libvarnishapi-dev || sudo yum install varnish-libs-devel
   ./bootstrap   # If running from git.
   ./configure
   make
   make check   # optional
   sudo make install
   ```

Se [Samling med slutna moduler](https://github.com/varnish/varnish-modules) om du vill ha information om hur du installerar modulen för det smarta läget.

### Exempel på VCL-fil

I följande kodexempel visas den kod som måste läggas till i VCL-filen för att helskärmsläget ska aktiveras. Placera `import` programsatser och `backend` definitioner högst upp i filen.

```cpp
import saintmode;
import directors;

backend default1 {
    .host = "192.168.0.1";
    .port = "8080";
    .first_byte_timeout = 600s;
    .probe = {
        .url = "/pub/health_check.php";
        .timeout = 2s;
        .interval = 5s;
        .window = 10;
        .threshold = 5;
    }
}

backend default2 {
    .host = "192.168.0.2";
    .port = "8080";
    .first_byte_timeout = 600s;
    .probe = {
        .url = "/pub/health_check.php";
        .timeout = 2s;
        .interval = 5s;
        .window = 10;
        .threshold = 5;
    }
}

sub vcl_init {
    # Instantiate sm1, sm2 for backends tile1, tile2
    # with 10 blacklisted objects as the threshold for marking the
    # whole backend sick.
    new sm1 = saintmode.saintmode(default1, 10);
    new sm2 = saintmode.saintmode(default2, 10);

    # Add both to a director. Use sm0, sm1 in place of tile1, tile2.
    # Other director types can be used in place of random.
    new magedirector = directors.random();
    magedirector.add_backend(sm1.backend(), 1);
    magedirector.add_backend(sm2.backend(), 1);
}

sub vcl_backend_fetch {
    # Get a backend from the director.
    # When returning a backend, the director will only return backends
    # saintmode says are healthy.
    set bereq.backend = magedirector.backend();
}

sub vcl_backend_response {
    if (beresp.status >= 500) {
        # This marks the backend as sick for this specific
        # object for the next 20s.
        saintmode.blacklist(20s);
        # Retry the request. This will result in a different backend
        # being used.
        return (retry);
    }
}
```
