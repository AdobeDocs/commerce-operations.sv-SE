---
title: Avancerad lack-konfiguration
description: Lär dig hur du konfigurerar avancerade lack-funktioner för Adobe Commerce, inklusive hälsokontroller, respitläge och helskärmsläge. Upptäck VCL-optimeringstekniker.
feature: Configuration, Cache
exl-id: 178bd675-6ed0-40cc-9455-08a11b32c054
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '881'
ht-degree: 0%

---

# Avancerad lack-konfiguration

På engelska finns flera funktioner som förhindrar kunder från att drabbas av långa förseningar och timeout när Commerce-servern inte fungerar som den ska. Dessa funktioner kan konfigureras i filen `default.vcl`. I det här avsnittet beskrivs de tillägg som Commerce tillhandahåller i VCL-filen (Varnish Configuration Language) som du hämtar från administratören.

Mer information om hur du använder konfigureringsspråket Variish finns i [Definitionsmanualen](https://varnish-cache.org/docs/index.html).

## Hälsokontroll

Funktionen för hälsokontroll av lack avfrågar Commerce-servern för att avgöra om den svarar i tid. Om det svarar normalt genereras nytt innehåll när TTL-perioden (Time to Live) har gått ut. Om inte, har Varnish alltid kvar sitt gamla innehåll.

Commerce definierar följande standardhälsokontroll:

```conf
.probe = {
    .url = "/pub/health_check.php";
    .timeout = 2s;
    .interval = 5s;
    .window = 10;
    .threshold = 5;
    }
```

Var femte sekund anropar den här hälsokontrollen skriptet `pub/health_check.php`. Det här skriptet kontrollerar tillgängligheten för servern, varje databas och Redis (om det är installerat). Skriptet måste returnera ett svar inom 2 sekunder. Om skriptet fastställer att någon av dessa resurser inte fungerar returneras en HTTP-felkod på 500. Om den här felkoden tas emot i sex av tio försök anses serverdelen vara felfri.

Skriptet `health_check.php` finns i katalogen `pub`. Om Commerce rotkatalog är `pub` måste du ändra sökvägen i parametern `url` från `/pub/health_check.php` till `health_check.php`.

Mer information finns i dokumentationen för [Hälsokontroller för lack](https://varnish-cache.org/docs/7.4/users-guide/vcl-backends.html#health-checks).

## Behagelläge

Med Grace-läget kan Varnish behålla ett objekt i cachen utanför dess TTL-värde. Slutgiltigt innehåll kan sedan användas medan det hämtar en ny version. Detta förbättrar trafikflödet och minskar inläsningstiden. Det används i följande situationer:

- När Commerce serverdel är felfri, men en begäran tar längre tid än normalt
- När Commerce serverdel inte är felfri.

Underrutinen `vcl_hit` definierar hur Varnish svarar på en begäran om objekt som har cachelagrats.

### När Commerce serverdel är felfri

När hälsokontrollerna avgör att Commerce serverdel är hälsosam kontrollerar lack om tiden är inne i fristen. Standardrespitperioden är 300 sekunder, men en handlare kan ange värdet från administratören enligt beskrivningen i [Konfigurera Commerce för användning av engelska](configure-varnish-commerce.md). Om respitperioden inte har gått ut skickar lack det inaktuella innehållet och objektet uppdateras asynkront från Commerce-servern. Om respitperioden har gått ut, skickar Varnish det inaktuella innehållet och uppdaterar objektet synkront från Commerce backend.

Den maximala tid som varnish skickar ett inaktuellt objekt är summan av respitperioden (300 sekunder som standard) och TTL-värdet (86400 sekunder som standard).

Om du vill ändra standardfristen från filen `default.vcl` redigerar du följande rad i underrutinen `vcl_hit`:

```conf
if (obj.ttl + 300s > 0s) {
```

### När Commerce serverdel inte är felfri

Om Commerce-serverdelen inte är responsiv, skickar Varnish inaktuellt innehåll från cache i tre dagar (eller enligt definitionen i `beresp.grace`) plus den återstående TTL-nivån (som är en dag som standard), såvida inte det cachelagrade innehållet rensas manuellt.

## Saint-läge

I läget Saint exkluderas ohälsosamma bakgrunder under en konfigurerbar tidsperiod. Därför kan ohälsosamma serverdelar inte generera trafik när Varnish används som belastningsutjämnare. Saint-läget kan användas i respitläge för att möjliggöra komplex hantering av ohälsosamma serverdelsservrar. Om till exempel en backend-server inte är felfri kan försök dirigeras till en annan server. Om alla andra servrar är nere kan du skicka inaktuella cachelagrade objekt. Värdar för helskärmsläge och utbrottsperioder definieras i filen `default.vcl`.

Saint-läge kan även användas när Commerce-instanser tas offline för att utföra underhålls- och uppgraderingsuppgifter utan att detta påverkar tillgängligheten för Commerce webbplats.

### Förutsättningar för Saint-läge

Ange en dator som primär installation. Installera huvudinstansen av Commerce, mySQL-databasen och Varnish på den här datorn.

På alla andra datorer måste Commerce-instansen ha åtkomst till den primära datorns mySQL-databas. De sekundära datorerna bör också ha tillgång till filerna för den primära Commerce-instansen.

Alternativt kan versionshantering av statiska filer inaktiveras på alla datorer. Du kan få åtkomst till detta från administratören under **Lager** > Inställningar > **Konfiguration** > **Avancerat** > **Utvecklare** > **Inställningar för statiska filer** > **Signera statiska filer** = **Nej**.

Slutligen måste alla Commerce-instanser vara i produktionsläge. Rensa cacheminnet för varje instans innan lack startas. Gå till **System** > Verktyg > **Cachehantering** i Admin och klicka på **Rensa Magento-cache**. Du kan också köra följande kommando för att rensa cachen:

```bash
bin/magento cache:flush
```

### Installation

Saint-läget ingår inte i Varnish-paketet. Det är en separat version av `vmod` som måste hämtas och installeras. Därför måste du kompilera om Varnish från källan, vilket beskrivs i [installationsanvisningarna](https://varnish-cache.org/docs/index.html) för din version av Varnish.

När du har kompilerat om kan du installera modulen för det smarta läget. I allmänhet gör du så här:

1. Hämta källkoden från [lack-moduler](https://github.com/varnish/varnish-modules). Klona Git-versionen (huvudversion) eftersom 0.9.x-versionerna innehåller ett källkodsfel.
1. Bygg källkoden med autoverktyg:

   ```bash
   sudo apt-get install libvarnishapi-dev || sudo yum install varnish-libs-devel
   ./bootstrap   # If running from git.
   ./configure
   make
   make check   # optional
   sudo make install
   ```

Mer information om hur du installerar modulen för det smarta läget finns i [Samling med engelska ](https://github.com/varnish/varnish-modules).

### Exempel på VCL-fil

I följande kodexempel visas den kod som måste läggas till i VCL-filen för att helskärmsläget ska aktiveras. Placera `import`-programsatser och `backend` -definitioner överst i filen.

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
