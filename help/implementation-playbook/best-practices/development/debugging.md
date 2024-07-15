---
title: Bästa tillvägagångssätt vid felsökning
description: Lär dig tekniker för att lösa vanliga Adobe Commerce-utvecklingsproblem.
feature: Best Practices
role: Developer
exl-id: 78fbea7b-28e8-4713-990d-b4cae159250c
source-git-commit: 823498f041a6d12cfdedd6757499d62ac2aced3d
workflow-type: tm+mt
source-wordcount: '1139'
ht-degree: 0%

---

# Bästa praxis för felsökning av Adobe Commerce

I det här avsnittet beskrivs olika sätt att systematiskt och effektivt felsöka Adobe Commerce-ramverket. Målet är att hjälpa er att snabbt hitta orsaken till ett problem och minimera tiden för utredningar.

## Felsökning: Oftast misstänkta

I det här avsnittet beskrivs de vanligaste problemen som kan uppstå under utvecklingen.

### Cache

- Töm cacheminnet innan ytterligare utredning
- Titta på APC-cachen, CDN, lack, genererad kod samt katalogerna `var/view_preprocessed` och `pub/static/`
- Stoppa och starta om köhanterare när du har tömt cachen eller ändrat kod

I följande kodexempel finns praktiska kommandon för hantering av cachen (kan inte köras i produktionsmiljöer):

```bash
# restart php-fpm to flush APC
sudo service php-fpm restart
 
# restart varnish to force full flush
sudo service varnish restart
 
# clear generated files
rm -rf generated/*
 
# clear static file cache
rm -rf var/view_preprocessed/*
rm -rf pub/static/*
 
# flush redis cache
redis-cli -n <db_number> FLUSHDB
 
# flush redis cache and sessions
redis-cli FLUSHALL
 
# flush redis cache with telnet
telnet <ip_or_host> 6379
SELECT <db_number>
FLUSHDB
Ctrl + ]
quit
 
# flush redis cache and sessions with telnet
telnet <ip_or_host> 6379
FLUSHALL
Ctrl + ]
quit
 
# find consumers
pgrep -af queue:consumers:start
 
# kill all queue consumers (they will restart by cron job)
sudo pkill -f queue:consumers:start
 
# kill a specific queue consumer (it will restart by cron job)
sudo kill <process_id>
```

### Indexerade data

Indexera om allt om problemet kan vara indexrelaterat. Felsökning av indexerade data sker vanligtvis i icke-produktionsmiljöer. I produktionsmiljöer kanske du vill undersöka orsaken till indexfeljusteringen innan du indexerar om. Egenskaperna hos det felaktiga läget kan tala om orsaken till problemet.

### Disposition

Du kanske har föråldrad kod på grund av en ändring i en gren eller på grund av kärnfiler som har redigerats i en tidigare felsökning. Du kan eliminera potentiella problem genom att köra följande kommandon:

```bash
rm -rf vendor/*
composer clear-cache
composer install
```

### Genererat innehåll

Bygg om klientfiler innan du felsöker det genererade innehållet i JS, CSS, bilder, översättningar och andra filer.

```bash
rm -rf generated/* var/cache/* var/page_cache/* var/session/* var/view_preprocessed/* pub/static/*
bin/magento setup:static-content:deploy
bin/magento cache:flush
```

### Utvecklarläge

Kontrollera att din lokala installation är i läget `developer`.

### Ny modul

Om du har skapat en modul kan du söka efter följande problem:

- Är modulen aktiverad?

  ```bash
  bin/magento module --enable Your_Module
  ```

  Kontrollera filen `app/etc/config.php` för din nya modul.

- Kontrollera fil- och katalogstrukturkapslingen. Finns till exempel layoutfiler i katalogen `view/layout/` i stället för i katalogen `view/frontend/layout`? Finns det mallar i katalogen `view/frontend/template` i stället för i katalogen `view/frontend/templates`?

## Felsökning: Halvdelning

Om de vanliga misstänkta inte erbjuder någon lösning på problemet är det snabbaste sättet att gå vidare genom att halvera (eller dela upp) problemet. Med den här metoden tar du bort stora segment och delar upp det som återstår för att hitta rotorsaken i stället för att gå igenom koden linjärt.

Se följande diagram:

![Objektdiagram](../../../assets/playbooks/bisect.png)

![Objektdiagram](../../../assets/playbooks/bisect2.png)

Det finns flera sätt att se på hur man gör en beskärning, men Adobe rekommenderar att du följer den här ordningen:

- Profilera efter ämne
- Skeva efter implementering
- Visa efter filer

### Steg 1: Specialtecken efter ämne

Om problemet kanske inte är kodrelaterat bör du ta bort de stora delarna först. Några av de stora segment du bör tänka på är:

- **Adobe Commerce Framework** - Är problemet relaterat till Adobe Commerce eller kan det vara relaterat till ett annat anslutet system?
- **Server och klient** - Rensa webbläsarens cache och lagring. Är problemet löst? Det kan utesluta en serverrelaterad orsak. Finns problemet fortfarande? Du behöver inte slösa mer tid på webbläsarfelsökning.
- **Session** - uppstår problemet för alla användare? Annars kan problemet vara begränsat till sessions- eller webbläsarrelaterade ämnen.
- **Cache** - Ändrar inaktivering av alla cacheminnen något? I så fall kan du fokusera på cacherelaterade ämnen.
- **Databas** - inträffar problemet i alla miljöer där samma kod körs? Annars kan du leta efter problem med konfigurationen och andra databasrelaterade ämnen.
- **Kod** - Sök efter kodproblem om inget av ovanstående åtgärdade problemet.

### Steg 2: Skeva efter implementering

Om problemet uppstod för två månader sedan kan du återställa koden till två månader sedan. Kontrollera om problemet kvarstår. Gå framåt en månad. Inträffar problemet där? Om inte, gå fram två veckor. Inträffar den nu? Gå tillbaka en vecka. Fortfarande där? Gå tillbaka fyra dagar. I något skede har du bara ett implementeringsalternativ kvar som troligen innehåller kod som är relaterad till problemet. Din rotorsak är nu troligtvis begränsad till de filer som har redigerats i implementeringen.

Du kan ersätta veckor och dagar med implementeringar. Återställ till 100 implementeringar, framåt 50, framåt 25, bakåt 12.

### Steg 3: Visa upp bilderna efter filer

- Dela upp Adobe Commerce efter filtyp (kärna och icke-kärna). Inaktivera först alla kund- och marknadsplatsmoduler. Finns problemet fortfarande? Det är sannolikt ett icke-kärnrelaterat problem.
- Aktivera (ungefär) hälften av modulerna igen i filen `app/etc/config.php`. Var medveten om beroenden. Det är bäst att aktivera modulkluster med samma ämne samtidigt. Finns problemet fortfarande?
- Aktivera en fjärdedel av återstående moduler. Finns problemet fortfarande? Inaktivera hälften av det du aktiverat. Den här metoden kan hjälpa dig att isolera rotorsaken till en enda modul.

## Tidsbesparande funktioner

Förutom felsökningstekniker innehåller det här avsnittet några allmänna regler som kan hjälpa till att spara tid under felsökningen.

### Begränsa data

Fundera på om du behöver hela katalogen eller alla butiksvyer för att replikera problemet. Du kan felsöka indexeringsproblem med en databasklona där du har tagit bort 95 % av katalogen innan du påbörjar felsökningen. Den här metoden sparar mycket tid under indexeringsprocesserna. Skapa en dubblett av klientdatabasen med minskat arkivantal och katalog. Detta kan även gälla andra enheter (till exempel kunder) beroende på vilket område du felsöker.

### Fråga efter mer information

Ibland kan det vara ett enkelt steg att glömma bland all kod och allt tekniskt arbete: be om mer information. Helskärmsinspelningar, en video, en videokonferenschatt med den person som identifierade problemet, replikeringssteg, frågor om huruvida andra till synes oviktiga saker hände runt den problematiska händelsen. Fråga vad någon förväntade sig skulle hända. Är det här ett fel eller kanske bara ett missförstånd om hur koden fungerar?

### Språk och tolkning

Är beskrivningen av problemet klar? Är du säker på att inga termer eller beskrivningar kan tolkas på flera sätt. I så fall, se till att du pratar om samma sak.

### Internetsökning

Gör en Internetsökning med termer som är relaterade till problemet. Det kan bero på att någon annan redan har stött på samma problem. Sök igenom [Adobe Commerce GitHub-utgåvorna](https://github.com/magento/magento2/issues).

### Ta en paus

Om du tittar på ett problem för länge kan det vara svårt att hitta en lösning. Lägg ner arbetet och fortsätt med en annan uppgift eller ta en promenad. Svaret kan komma dig när du glömmer bort problemet ett tag.

## verktyg

CLI-verktygen för n98-magerun ([https://github.com/netz98/n98-magerun2](https://github.com/netz98/n98-magerun2)) ger användbara funktioner för att arbeta med Adobe Commerce från kommandoraden. Speciellt följande kommandon:

```bash
n98-magerun2.phar dev:console
n98-magerun2.phar sys:cron:run
n98-magerun2.phar db:console
n98-magerun2.phar index:trigger:recreate
```


## Kodfragment

Följande avsnitt innehåller kodfragment som kan användas för att logga eller identifiera problem i Commerce-projekt.

### Kontrollera om en XML-fil används av Commerce

Lägg till ett syntaxfel i en XML-fil för att se om den används. Öppna en tagg och stäng den inte, till exempel:

```xml
<?xml version="1.0"?>
<test
```

Om den här filen används genereras ett fel. Om den inte är det kanske modulen inte används eller aktiveras, till exempel, eller så kanske XML-filen finns på fel plats.

### Loggning

>[!BEGINTABS]

>[!TAB Adobe Commerce]

```php
\Magento\Framework\App\ObjectManager::getInstance()
    ->get(\Psr\Log\LoggerInterface::class)->debug('message');
```

>[!TAB Monolog]

```php
$log = new \Monolog\Logger('custom', [new \Monolog\Handler\StreamHandler(BP.'/var/log/test.log')]);
$log->info('Your Logging Message', ['context' => ['email' => 'john@example.com']]);
```

>[!TAB Zend]

```php
$writer = new \Zend\Log\Writer\Stream(BP . '/var/log/test.log');
$logger = new \Zend\Log\Logger();
$logger->addWriter($writer);
$logger->info('Your text message');
$logger->info(print_r($yourArray, true));
```

>[!ENDTABS]

### Loggning på låg nivå

Två exempel som alltid fungerar i alla PHP-filer:

```php
file_put_contents('/var/www/html/var/log/example.log', "example line\n", FILE_APPEND);
file_put_contents('/var/www/html/var/log/example.log', print_r($yourArray, true) . "\n", FILE_APPEND);
```

Och för en stackspårning:

```php
try {
    throw new \Exception('example');
} catch (\Exception $e) {
    file_put_contents('/var/www/html/var/log/example.log', $e->getTraceAsString() . "\n", FILE_APPEND);
}
```
