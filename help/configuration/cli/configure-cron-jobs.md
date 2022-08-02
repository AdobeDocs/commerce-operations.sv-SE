---
title: Konfigurera och köra cron-jobb
description: Lär dig hur du hanterar cron-jobb.
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '766'
ht-degree: 0%

---


# Konfigurera cron-jobb

{{file-system-owner}}

Flera Commerce-funktioner kräver minst ett cron-jobb som schemalägger aktiviteter i framtiden. En del av dessa verksamheter följer:

- Katalogprisregler
- Nyhetsbrev
- Generera Google-webbplatskartor
- Kundaviseringar/meddelanden (produktprisändring, återlagrad produkt)
- Omindexering
- Privat försäljning (endast Adobe Commerce)
- Automatisk uppdatering av valutakurser
- Alla e-postmeddelanden om handel (inklusive orderbekräftelse och transaktion)

>[!WARNING]
>
>Du kan inte längre köra `dev/tools/cron.sh` eftersom skriptet har tagits bort.

>[!INFO]
>
>Handel är beroende av korrekt konfiguration av cron-jobb för många viktiga systemfunktioner, inklusive indexering. Om den inte konfigureras korrekt kommer Commerce inte att fungera som förväntat.

UNIX-system schemalägger uppgifter som ska utföras av vissa användare med en _crontab_, som är en fil som innehåller instruktioner till seriemonden som talar om för daemon att &quot;köra det här kommandot vid det här datumet&quot;. Varje användare har sin egen crontab, och kommandon på en viss crontab körs som den användare som äger den.

Information om hur du kör cron i en webbläsare finns i [Säkra cron.php för att köras i en webbläsare](../security/secure-cron-php.md).

## Skapa eller ta bort fliken Commerce

I det här avsnittet beskrivs hur du skapar eller tar bort din Commerce crontab (d.v.s. konfigurationen för Commerce cron-jobb).

The _crontab_ är den konfiguration som används för att köra cron-jobb.

I Commerce-programmet används kroniska uppgifter som kan köras med olika konfigurationer. PHP-kommandoradskonfigurationen styr det allmänna cron-jobbet som omindexerar indexerare, genererar e-post, genererar platskartan och så vidare.

>[!WARNING]
>
>- För att undvika problem under installation och uppgradering rekommenderar vi att du använder samma PHP-inställningar både på PHP-kommandoradskonfigurationen och på PHP-webbserverpluginens konfiguration. Mer information finns i [Nödvändiga PHP-inställningar](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/php-settings.html).
>- I ett flernodssystem kan crontab endast köras på en nod. Detta gäller endast dig om du konfigurerar mer än en webbnod på grund av prestanda eller skalbarhet.


### Skapa fliken Commerce crontab

Från och med version 2.2 skapar Commerce en crontab åt dig. Vi lägger till fliken Commerce crontab till en konfigurerad crontab för ägaren av Commerce-filsystemet. Det innebär att om du redan har konfigurerat klientflikar för andra tillägg eller program lägger vi till fliken Commerce.

Commerce crontab är inuti `#~ MAGENTO START` och `#~ MAGENTO END` kommentarer på din crontab.

Så här skapar du Commerce crontab:

1. Logga in som eller växla till [ägare av filsystem](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-sys-perms-over.html).
1. Ändra till installationskatalogen för Commerce.
1. Ange följande kommando:

   ```bash
   bin/magento cron:install [--force]
   ```

Använd `--force` om du vill skriva om en befintlig crontab.

>[!INFO]
>
>- `magento cron:install` skriver inte om en befintlig crontab inuti `#~ MAGENTO START` och `#~ MAGENTO END` kommentarer på din crontab.
>- `magento cron:install --force` har ingen effekt på några cron-jobb utanför Commerce-kommentarerna.


Om du vill visa fliken crontab anger du följande kommando som ägare av filsystemet:

```bash
crontab -l
```

Ett exempel följer:

```terminal
#~ MAGENTO START c5f9e5ed71cceaabc4d4fd9b3e827a2b
* * * * * /usr/bin/php /var/www/html/magento2/bin/magento cron:run 2>&1 | grep -v "Ran jobs by schedule" >> /var/www/html/magento2/var/log/magento.cron.log
#~ MAGENTO END c5f9e5ed71cceaabc4d4fd9b3e827a2b
```

>[!INFO]
>
>The `update/cron.php` filen har tagits bort i Commerce 2.4.0. Om filen finns i din installation kan den tas bort på ett säkert sätt.
>
>Alla referenser till `update/cron.php` och `bin/magento setup:cron:run` ska också tas bort från crontab&#39;

### Ta bort fliken Commerce crontab

Du bör bara ta bort Commerce crontab innan du avinstallerar Commerce-programmet.

Så här tar du bort fliken Commerce:

1. Logga in som eller växla till [ägare av filsystem](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-sys-perms-over.html).
1. Ändra till installationskatalogen för Commerce.
1. Ange följande kommando:

   ```bash
   bin/magento cron:remove
   ```

>[!INFO]
>
>Det här kommandot har ingen effekt på cron-jobb utanför `#~ MAGENTO START` och `#~ MAGENTO END` kommentarer på din crontab.

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

Information om hur du ställer in anpassade cron-jobb och grupper finns i [Konfigurera anpassade cron-jobb och cron-grupper](../cron/custom-cron.md).

>[!INFO]
>
>Du måste köra cron två gånger: första gången som du identifierar uppgifter som ska köras och andra gången - för att köra själva uppgifterna. Den andra kron-körningen måste göras på eller efter `scheduled_at` tid för varje uppgift.

## Loggning

Alla `cron` jobbinformation har flyttats från `system.log` till en separat `cron.log`.
Som standard finns kroniinformationen på `<install_directory>/var/log/cron.log`.
Alla undantag från cron-jobb loggas av `\Magento\Cron\Observer\ProcessCronQueueObserver::execute`.

Förutom att loggas in `cron.log`:

- Misslyckade jobb med `ERROR` och `MISSED` status loggas på `<install_directory>/var/log/support_report.log`.

- Jobb med en `ERROR` status loggas alltid som `CRITICAL` in `<install_directory>/var/log/exception.log`.

- Jobb med en `MISSED` status loggas som `INFO` i `<install_directory>/var/log/debug.log` katalog (endast utvecklarläget).

>[!INFO]
>
>Alla kronidata skrivs också till `cron_schedule` i Commerce-databasen. Tabellen innehåller en historik över cron-jobb, inklusive:
>
>- Jobb-ID och kod
>- Status
>- Skapad den
>- Schemalagt datum
>- Kört den
>- Slutdatum
>
>Om du vill visa poster i tabellen loggar du in i Commerce-databasen på kommandoraden och anger `SELECT * from cron_schedule;`.
