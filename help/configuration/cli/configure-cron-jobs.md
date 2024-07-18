---
title: Konfigurera och köra cron-jobb
description: Lär dig hur du hanterar cron-jobb.
exl-id: 8ba2b2f9-5200-4e96-9799-1b00d7d23ce1
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '748'
ht-degree: 0%

---

# Konfigurera cron-jobb

{{file-system-owner}}

Flera Commerce-funktioner kräver minst ett cron-jobb, vilket schemalägger framtida aktiviteter. En del av dessa verksamheter följer:

- Katalogprisregler
- Nyhetsbrev
- Generera Google-webbplatskartor
- Kundaviseringar/meddelanden (produktprisändring, återlagrad produkt)
- Omindexering
- Privat försäljning (endast Adobe Commerce)
- Automatisk uppdatering av valutakurser
- Alla e-postmeddelanden från Commerce (inklusive orderbekräftelse och transaktioner)

>[!WARNING]
>
>Du kan inte längre köra `dev/tools/cron.sh` eftersom skriptet har tagits bort.

>[!INFO]
>
>Commerce är beroende av korrekt konfiguration av cron-jobb för många viktiga systemfunktioner, inklusive indexering. Om den inte konfigureras korrekt kommer Commerce inte att fungera som förväntat.

I UNIX-system schemaläggs uppgifter att utföras av vissa användare med en _crontab_, som är en fil som innehåller instruktioner till cron daemon som talar om för daemon som används att &quot;köra det här kommandot vid den här tidpunkten&quot;. Varje användare har sin egen crontab, och kommandon på en viss crontab körs som den användare som äger den.

Information om hur du kör cron i en webbläsare finns i [Skydda cron.php för att köras i en webbläsare](../security/secure-cron-php.md).

## Skapa eller ta bort Commerce crontab

I det här avsnittet beskrivs hur du skapar eller tar bort din Commerce crontab (dvs. konfigurationen för Commerce cron-jobb).

_crontab_ är den konfiguration som används för att köra cron-jobb.

Commerce-programmet använder kroniska uppgifter som kan köras med olika konfigurationer. PHP-kommandoradskonfigurationen styr det allmänna cron-jobbet som omindexerar indexerare, genererar e-post, genererar platskartan och så vidare.

>[!WARNING]
>
>- För att undvika problem under installation och uppgradering rekommenderar vi att du använder samma PHP-inställningar både på PHP-kommandoradskonfigurationen och på PHP-webbserverpluginens konfiguration. Mer information finns i [Nödvändiga PHP-inställningar](../../installation/prerequisites/php-settings.md).
>- I ett flernodssystem kan crontab endast köras på en nod. Detta gäller endast dig om du konfigurerar mer än en webbnod av orsaker som rör prestanda eller skalbarhet.

### Skapa Commerce crontab

Från och med version 2.2 skapar Commerce en crontab åt dig. Vi lägger till Commerce crontab i en konfigurerad crontab för Commerce filsystemsägare. Det innebär att om du redan har konfigurerat flikar för andra tillägg eller program lägger vi till fliken Commerce crontab i den.

Commerce crontab finns i `#~ MAGENTO START` och `#~ MAGENTO END` kommentarer på din crontab.

Så här skapar du Commerce crontab:

1. Logga in som, eller växla till, ägare av [filsystemet](../../installation/prerequisites/file-system/overview.md).
1. Byt till Commerce installationskatalog.
1. Ange följande kommando:

   ```bash
   bin/magento cron:install [--force]
   ```

Använd `--force` för att skriva om en befintlig crontab.

>[!INFO]
>
>- `magento cron:install` skriver inte om en befintlig crontab inuti `#~ MAGENTO START` - och `#~ MAGENTO END` -kommentarer på din crontab.
>- `magento cron:install --force` har ingen effekt på några kroniska jobb utanför Commerce kommentarer.

Om du vill visa fliken crontab anger du följande kommando som ägare av filsystemet:

```bash
crontab -l
```

Ett exempel följer:

```
#~ MAGENTO START c5f9e5ed71cceaabc4d4fd9b3e827a2b
* * * * * /usr/bin/php /var/www/html/magento2/bin/magento cron:run 2>&1 | grep -v "Ran jobs by schedule" >> /var/www/html/magento2/var/log/magento.cron.log
#~ MAGENTO END c5f9e5ed71cceaabc4d4fd9b3e827a2b
```

>[!INFO]
>
>Filen `update/cron.php` har tagits bort i Commerce 2.4.0. Om filen finns i installationen kan den tas bort.
>
>Alla referenser till `update/cron.php` och `bin/magento setup:cron:run` ska också tas bort från crontab

### Ta bort Commerce crontab

Du bör bara ta bort Commerce crontab innan du avinstallerar Commerce.

Så här tar du bort Commerce crontab:

1. Logga in som eller växla till [filsystemets ägare](../../installation/prerequisites/file-system/overview.md).
1. Gå till Commerce installationskatalog.
1. Ange följande kommando:

   ```bash
   bin/magento cron:remove
   ```

>[!INFO]
>
>Det här kommandot har ingen effekt på cron-jobb utanför kommentarerna `#~ MAGENTO START` och `#~ MAGENTO END` på din crontab.

## Kör cron från kommandoraden

Kommandoalternativ:

```bash
bin/magento cron:run [--group="<cron group name>"]
```

där `--group` anger vilken cron-grupp som ska köras (utelämna det här alternativet om du vill köra cron för alla grupper)

Om du vill köra indexeringsjobbet anger du:

```bash
bin/magento cron:run --group index
```

Om du vill köra standardcron-jobbet anger du:

```bash
bin/magento cron:run --group default
```

Mer information om hur du konfigurerar anpassade cron-jobb och grupper finns i [Konfigurera anpassade cron-jobb och cron-grupper](../cron/custom-cron.md).

>[!INFO]
>
>Du måste köra cron två gånger: första gången du upptäcker uppgifter som ska köras och andra gången - för att köra själva uppgifterna. Den andra kron-körningen måste utföras på eller efter `scheduled_at`-tiden för varje aktivitet.

## Loggning

All jobbinformation för `cron` har flyttats från `system.log` till en separat `cron.log`.
Som standard finns kroninformationen på `<install_directory>/var/log/cron.log`.
Alla undantag från cron-jobb loggas av `\Magento\Cron\Observer\ProcessCronQueueObserver::execute`.

Förutom inloggning `cron.log`:

- Misslyckade jobb med statusvärdena `ERROR` och `MISSED` loggas till `<install_directory>/var/log/support_report.log`.

- Jobb med statusen `ERROR` loggas alltid som `CRITICAL` i `<install_directory>/var/log/exception.log`.

- Jobb med statusen `MISSED` loggas som `INFO` i katalogen `<install_directory>/var/log/debug.log` (endast i utvecklarläget).

>[!INFO]
>
>Alla cron-data skrivs också till tabellen `cron_schedule` i Commerce-databasen. Tabellen innehåller en historik över cron-jobb, inklusive:
>
>- Jobb-ID och kod
>- Status
>- Skapad den
>- Schemalagt datum
>- Kört den
>- Slutdatum
>
>Om du vill visa poster i tabellen loggar du in på Commerce-databasen på kommandoraden och anger `SELECT * from cron_schedule;`.
