---
title: PHP-inställningar
description: Följ de här stegen för att installera nödvändiga PHP-tillägg och konfigurera PHP-inställningar för lokala installationer av Adobe Commerce och Magento Open Source.
source-git-commit: f6f438b17478505536351fa20a051d355f5b157a
workflow-type: tm+mt
source-wordcount: '810'
ht-degree: 0%

---


# PHP-inställningar

I det här avsnittet beskrivs hur du ställer in krav [PHP](https://glossary.magento.com/php) alternativ.

>[!NOTE]
>
>Se [systemkrav](../system-requirements.md) för de versioner av PHP som stöds.

## Kontrollera att PHP är installerat

De flesta versioner av Linux har PHP installerat som standard. Det här avsnittet förutsätter att du redan har installerat PHP. Kontrollera om PHP redan är installerat genom att skriva:

```bash
php -v
```

If [PHP](https://glossary.magento.com/php) installeras, ett meddelande som liknar följande visas:

```terminal
PHP 7.4.0 (cli) (built: Aug 14 2019 16:42:46) ( NTS )
Copyright (c) 1997-2018 The PHP Group
Zend Engine v3.1.0, Copyright (c) 1998-2018 Zend Technologies with Zend OPcache v7.1.6, Copyright (c) 1999-2018, by Zend Technologies
```

Adobe Commerce och Magento Open Source 2.4 är kompatibla med PHP 7.3, men vi testar och rekommenderar att du använder PHP 7.4.

Om PHP inte är installerat, eller om en versionsuppgradering behövs, installerar du den enligt instruktionerna för din speciella Linux-smak.
I CentOS [ytterligare steg kan behövas](https://wiki.centos.org/HowTos/php7).

## Verifiera installerade tillägg

Adobe Commerce och Magento Open Source kräver att en uppsättning tillägg installeras.

{{$include /help/_includes/php-extensions.md}}

Så här verifierar du installerade tillägg:

1. Lista installerade moduler.

   ```bash
   php -m
   ```

1. Kontrollera att alla nödvändiga tillägg är installerade.
1. Lägg till saknade moduler med samma arbetsflöde som används för att installera PHP. Om du till exempel använder `yum` PHP 7.4-modulerna kan läggas till med:

   ```bash
    yum -y install php74u-pdo php74u-mysqlnd php74u-opcache php74u-xml php74u-gd php74u-devel php74u-mysql php74u-intl php74u-mbstring php74u-bcmath php74u-json php74u-iconv php74u-soap
   ```

## Kontrollera PHP-inställningar

>[!WARNING]
>
>Om du använder PHP 7.4.20 anger du `pcre.jit=0` i `php.ini` -fil. Det här kommer runt en PHP [bug](https://bugs.php.net/bug.php?id=81101) som förhindrar att CSS läses in.

- Ange systemtidszon för PHP. I annat fall kanske fel som följande visas under installationen och tidsrelaterade åtgärder som cron inte fungerar:

```terminal
PHP Warning:  date(): It is not safe to rely on the system's timezone settings. [more messages follow]
```

- Ange PHP-minnesgränsen.

   Våra detaljerade rekommendationer är:

   - Kompilera kod eller distribuera statiska resurser, `1G`
   - Felsökning, `2G`
   - Testning, `~3-4G`

- Öka värdena för PHP `realpath_cache_size` och `realpath_cache_ttl` till rekommenderade inställningar:

   ```conf
   realpath_cache_size=10M
   realpath_cache_ttl=7200
   ```

   Med de här inställningarna kan PHP-processer cachelagra sökvägar till filer i stället för att leta upp dem varje gång en sida läses in. Se [Prestandajustering](https://www.php.net/manual/en/ini.core.php) i PHP-dokumentationen.

- Aktivera [`opcache.save_comments`](https://www.php.net/manual/en/opcache.configuration.php#ini.opcache.save-comments), vilket krävs för Adobe Commerce och Magento Open Source 2.1 och senare.

   Vi rekommenderar att du aktiverar [PHP OPcache](https://www.php.net/manual/en/book.opcache.php) av prestandaskäl. OPcache är aktiverat i många PHP-distributioner.

   Adobe Commerce och Magento Open Source 2.1 och senare använder PHP-kodkommentarer för kodgenerering.

>[!NOTE]
>
>För att undvika problem under installation och uppgradering rekommenderar vi att du använder samma PHP-inställningar både i PHP-kommandoradskonfigurationen och i PHP-webbserverns plugin-konfiguration. Mer information finns i nästa avsnitt.

## Sök efter PHP-konfigurationsfiler

I det här avsnittet beskrivs hur du hittar de konfigurationsfiler som behövs för att uppdatera nödvändiga inställningar.

### Sök `php.ini` konfigurationsfil

Om du vill hitta webbserverkonfigurationen kör du en [`phpinfo.php` fil](optional-software.md#create-phpinfophp) i webbläsaren och leta efter `Loaded Configuration File` enligt följande:

![PHP-informationssida](../../assets/installation/config_phpini-webserver.png)

Om du vill hitta PHP-kommandoradskonfigurationen anger du

```bash
php --ini | grep "Loaded Configuration File"
```

>[!NOTE]
>
>Om du bara har en `php.ini` gör du ändringarna i filen. Om du har två `php.ini` filer, göra ändringar i *alla* filer. Om du inte gör det kan prestandan bli oförutsägbar.

### Sök efter inställningar för OPcache-konfiguration

Inställningarna för PHP OPcache finns vanligtvis antingen i `php.ini` eller `opcache.ini`. Platsen kan vara beroende av operativsystemet och PHP-versionen. Konfigurationsfilen för OPCache kan ha en `opcache` -avsnitt eller inställningar som `opcache.enable`.

Använd följande riktlinjer för att hitta den:

- Apache-webbserver:

   För Ubuntu med Apache finns inställningarna för OPcache vanligtvis i `php.ini` -fil.

   För CentOS med Apache eller nginx finns inställningarna för OPcache vanligtvis i `/etc/php.d/opcache.ini`

   Om inte, använder du följande kommando för att hitta den:

   ```bash
   sudo find / -name 'opcache.ini'
   ```

- nginx-webbserver med PHP-FPM: `/etc/php/7.2/fpm/php.ini`

Om du har fler än en `opcache.ini`, ändra alla.

## Ange PHP-alternativ

Så här anger du PHP-alternativ:

1. Öppna en `php.ini` i en textredigerare.
1. Leta reda på serverns tidszon i den tillgängliga [tidszonsinställningar](https://www.php.net/manual/en/timezones.php)
1. Leta reda på följande inställning och avkommentera den om det behövs:

   ```conf
   date.timezone =
   ```

1. Lägg till tidszonsinställningen som du hittade i steg 2.

1. Ändra värdet för `memory_limit` till ett av de värden som rekommenderas i början av det här avsnittet.

   Exempel:

   ```conf
   memory_limit=2G
   ```

1. Lägg till eller uppdatera `realpath_cache` så att den matchar följande värden:

   ```conf
   ;
   ; Increase realpath cache size
   ;
   realpath_cache_size = 10M
   
   ;
   ; Increase realpath cache ttl
   ;
   realpath_cache_ttl = 7200
   ```

1. Spara ändringarna och avsluta textredigeraren.

1. Öppna den andra `php.ini` (om de är olika) och gör samma ändringar.

## Ange alternativ för OPCache

Till `opcache.ini` alternativ:

1. Öppna din OPCache-konfigurationsfil i en textredigerare:

   - `opcache.ini` (CentOS)
   - `php.ini` (Ubuntu)
   - `/etc/php/7.2/fpm/php.ini` (nginx-webbserver (CentOS eller Ubuntu))

1. Sök `opcache.save_comments` och avkommentera vid behov.
1. Se till att dess värde är inställt på `1`.
1. Spara ändringarna och avsluta textredigeraren.
1. Starta om webbservern:

   - Apache, Ubuntu: `service apache2 restart`
   - Apache, CentOS: `service httpd restart`
   - nginx, Ubuntu och CentOS: `service nginx restart`

## Felsökning

Se följande Adobe Commerce supportartiklar för hjälp med felsökning av PHP-problem:

- [PHP-versionsfel eller 404-fel vid åtkomst till Adobe Commerce i webbläsaren](https://support.magento.com/hc/en-us/articles/360033117152-PHP-version-error-or-404-error-when-accessing-Magento-in-browser)
- [Fel i PHP-inställningar](https://support.magento.com/hc/en-us/articles/360034599631-PHP-settings-errors)
- [PHP-krypteringstillägget har inte installerats korrekt](https://support.magento.com/hc/en-us/articles/360034280132-PHP-mcrypt-extension-not-installed-properly-)
- [Problem med beredskapskontroll av PHP-version](https://support.magento.com/hc/en-us/articles/360033546411)
- [Vanliga PHP-allvarliga fel och lösningar](https://support.magento.com/hc/en-us/articles/360030568432)
