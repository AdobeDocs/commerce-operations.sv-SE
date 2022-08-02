---
title: Konfigurera ett anpassat cron-jobb och en cron-grupp (självstudiekurs)
description: Använd den här stegvisa självstudiekursen för att skapa ett anpassat cron-jobb.
source-git-commit: 53448b11a2d000fe8e8a7eecf2ffcef4b7e248fa
workflow-type: tm+mt
source-wordcount: '822'
ht-degree: 0%

---


# Konfigurera ett anpassat cron-jobb

Den här stegvisa självstudiekursen visar hur du skapar ett anpassat cron-jobb och eventuellt en cron-grupp i en exempelmodul. Du kan använda en modul som du redan har eller använda en exempelmodul från [`magento2-samples` databas][samples].

Om du kör kronjobbet läggs en rad till i `cron_schedule` tabell med namnet på cron-jobbet, `custom_cron`.

Vi visar även hur du kan skapa en cron-grupp som du kan använda för att köra anpassade cron-jobb med andra inställningar än standardinställningarna för Commerce-program.

I den här självstudiekursen antar vi följande:

- Commerce-programmet är installerat i `/var/www/html/magento2`
- Ditt användarnamn och lösenord för Commerce-databasen är båda `magento`
- Du utför alla åtgärder som [ägare av filsystem](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-sys-perms-over.html)

## Steg 1: Hämta en exempelmodul

Om du vill konfigurera ett anpassat cron-jobb behöver du en provmodul. Vi föreslår `magento-module-minimal` -modul.

Om du redan har en exempelmodul kan du använda den; hoppa över det här steget och nästa steg och fortsätt med steg 3: Skapa en klass att köra cron.

**Hämta en exempelmodul**:

1. Logga in på din Commerce-server som eller växla till [ägare av filsystem](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-sys-perms-over.html).
1. Byt till en katalog som inte finns i Commerce-programmets rot (till exempel din arbetskatalog).
1. Klona [`magento2-samples` databas][samples].

   ```bash
   git clone git@github.com:magento/magento2-samples.git
   ```

   Om kommandot misslyckas med felet `Permission denied (publickey).`måste du [lägga till din offentliga SSH-nyckel på GitHub.com][git-ssh].

1. Skapa en katalog dit exempelkoden ska kopieras:

   ```bash
   mkdir -p /var/www/html/magento2/app/code/Magento/SampleMinimal
   ```

1. Kopiera exempelmodulkoden:

   ```bash
   cp -r ~/magento2-samples/sample-module-minimal/* /var/www/html/magento2/app/code/Magento/SampleMinimal
   ```

1. Kontrollera att filerna är korrekt kopierade:

   ```bash
   ls -al /var/www/html/magento2/app/code/Magento/SampleMinimal
   ```

   Följande resultat bör visas:

   ```terminal
   drwxrwsr-x.   4 magento_user apache  4096 Oct 30 13:19 .
   drwxrwsr-x. 121 magento_user apache  4096 Oct 30 13:19 ..
   -rw-rw-r--.   1 magento_user apache   372 Oct 30 13:19 composer.json
   drwxrwsr-x.   2 magento_user apache  4096 Oct 30 13:19 etc
   -rw-rw-r--.   1 magento_user apache 10376 Oct 30 13:19 LICENSE_AFL.txt
   -rw-rw-r--.   1 magento_user apache 10364 Oct 30 13:19 LICENSE.txt
   -rw-rw-r--.   1 magento_user apache  1157 Oct 30 13:19 README.md
   -rw-rw-r--.   1 magento_user apache   270 Oct 30 13:19 registration.php
   drwxrwsr-x.   3 magento_user apache  4096 Oct 30 13:19 Test
   ```

1. Uppdatera Commerce-databasen och -schemat:

   ```bash
   bin/magento setup:upgrade
   ```

1. Rensa cacheminnet:

   ```bash
   bin/magento cache:clean
   ```

## Steg 2: Verifiera exempelmodulen

Innan du fortsätter kontrollerar du att exempelmodulen är registrerad och aktiverad.

1. Kör följande kommando:

   ```bash
   bin/magento module:status Magento_SampleMinimal
   ```

1. Kontrollera att modulen är aktiverad.

   ```terminal
   Module is enabled
   ```

>[!TIP]
>
>Om utdata indikerar att `Module does not exist`, granska [Steg 1](#step-1-get-a-sample-module) noggrant. Kontrollera att koden finns i rätt katalog. Stavning och skiftlägen är viktiga; Om något är annorlunda läses modulen inte in. Glöm inte att köra `magento setup:upgrade`.

## Steg 3: Skapa en klass som ska köras

I det här steget visas en enkel klass för att skapa ett cron-jobb. Klassen skriver bara en rad till `cron_schedule` tabell som bekräftar att den har konfigurerats.

Så här skapar du en klass:

1. Skapa en katalog för klassen och ändra till den katalogen:

   ```bash
   mkdir /var/www/html/magento2/app/code/Magento/SampleMinimal/Cron && cd /var/www/html/magento2/app/code/Magento/SampleMinimal/Cron
   ```

1. Skapade en fil med namnet `Test.php` i den katalogen med följande innehåll:

   ```php
   <?php
   namespace Magento\SampleMinimal\Cron;
   
   use Psr\Log\LoggerInterface;
   
   class Test {
       protected $logger;
   
       public function __construct(LoggerInterface $logger) {
           $this->logger = $logger;
       }
   
      /**
       * Write to system.log
       *
       * @return void
       */
       public function execute() {
           $this->logger->info('Cron Works');
       }
   }
   ```

## Steg 4: Skapa `crontab.xml`

The `crontab.xml` filen anger ett schema för att köra din anpassade kundkod.

Skapa `crontab.xml` enligt följande i `/var/www/html/magento2/app/code/Magento/SampleMinimal/etc` katalog:

```xml
<?xml version="1.0"?>
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Cron:etc/crontab.xsd">
    <group id="default">
        <job name="custom_cronjob" instance="Magento\SampleMinimal\Cron\Test" method="execute">
            <schedule>* * * * *</schedule>
        </job>
    </group>
</config>
```

Föregående `crontab.xml` kör `Magento/SampleMinimal/Cron/Test.php` klass en gång per minut, vilket resulterar i att en rad läggs till i `cron_schedule` tabell.

Använd konfigurationssökvägen för systemkonfigurationsfältet för att göra schemat för cron konfigurerbart från Admin.

```xml
<?xml version="1.0"?>
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Cron:etc/crontab.xsd">
    <group id="default">
        <job name="custom_cronjob" instance="Magento\SampleMinimal\Cron\Test" method="execute">
            <config_path>system/config/path</config_path>
        </job>
    </group>
</config>
```

Var `system/config/path` är en systemkonfigurationssökväg som definieras i `etc/adminhtml/system.xml` för en modul.

## Steg 5: Kompilera och cachelagra rent

Kompilera koden med det här kommandot:

```bash
bin/magento setup:di:compile
```

Och rensa cacheminnet med det här kommandot:

```bash
bin/magento cache:clean
```

## Steg 6: Verifiera kron-jobbet

I det här steget visas hur du verifierar det anpassade cron-jobbet med hjälp av en SQL-fråga på `cron_schedule` databastabell.

Så här kontrollerar du cron:

1. Kör Commerce cron-jobb:

   ```bash
   bin/magento cron:run
   ```

1. Ange `magento cron:run` kommandot två eller tre gånger.

   Första gången du anger kommandot köas jobb; därefter körs cron-jobben. Du måste ange kommandot _minst_ två gånger.

1. Kör SQL-frågan `SELECT * from cron_schedule WHERE job_code like '%custom%'` enligt följande:

   1. Retur `mysql -u magento -p`
   1. På `mysql>` prompt, enter `use magento;`
   1. Retur `SELECT * from cron_schedule WHERE job_code like '%custom%';`

      Resultatet ska vara som följer:

      ```terminal
      +-------------+----------------+---------+----------+---------------------+---------------------+---------------------+---------------------+
      | schedule_id | job_code       | status  | messages | created_at        | scheduled_at        | executed_at         | finished_at     |
      +-------------+----------------+---------+----------+---------------------+---------------------+---------------------+---------------------+
      |        3670 | custom_cronjob | success | NULL     | 2016-11-02 09:38:03 | 2016-11-02 09:38:00 | 2016-11-02 09:39:03 | 2016-11-02 09:39:03 |
      |        3715 | custom_cronjob | success | NULL     | 2016-11-02 09:53:03 | 2016-11-02 09:53:00 | 2016-11-02 09:54:04 | 2016-11-02 09:54:04 |
      |        3758 | custom_cronjob | success | NULL     | 2016-11-02 10:09:03 | 2016-11-02 10:09:00 | 2016-11-02 10:10:03 | 2016-11-02 10:10:03 |
      |        3797 | custom_cronjob | success | NULL     | 2016-11-02 10:24:03 | 2016-11-02 10:24:00 | 2016-11-02 10:25:03 | 2016-11-02 10:25:03 |
      +-------------+----------------+---------+----------+---------------------+---------------------+---------------------+---------------------+
      ```

1. (Valfritt) Kontrollera att meddelanden skrivs till Commerce-systemets systemlogg:

   ```bash
   cat /var/www/html/magento2/var/log/system.log
   ```

   Du bör se en eller flera poster som följande:

   ```terminal
   [2016-11-02 22:17:03] main.INFO: Cron Works [] []
   ```

   Dessa meddelanden kommer från `execute` metod i `Test.php`:

   ```php
   public function execute() {
        $this->logger->info('Cron Works');
   ```

Om SQL-kommandot och systemloggen inte innehåller några poster kör du `magento cron:run` och vänta några gånger till. Det kan ta en stund innan databasen uppdateras.

## Steg 7 (valfritt): Ställa in en anpassad cron-grupp

I det här steget visas hur du kan ställa in en anpassad cron-grupp. Du bör konfigurera en anpassad cron-grupp om du vill att ditt anpassade cron-jobb ska köras enligt ett annat schema än andra cron-jobb (vanligtvis en gång per minut) eller om du vill att flera anpassade cron-jobb ska köras med olika inställningar.

Så här ställer du in en anpassad cron-grupp:

1. Öppna `crontab.xml` i en textredigerare.
1. Ändra `<group id="default">` till `<group id="custom_crongroup">`
1. Avsluta textredigeraren.
1. Skapa `/var/www/html/magento2/app/code/Magento/SampleMinimal/etc/cron_groups.xml` med följande innehåll:

   ```xml
   <?xml version="1.0"?>
   <config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Cron:etc/cron_groups.xsd">
       <group id="custom_crongroup">
           <schedule_generate_every>1</schedule_generate_every>
           <schedule_ahead_for>4</schedule_ahead_for>
           <schedule_lifetime>2</schedule_lifetime>
           <history_cleanup_every>10</history_cleanup_every>
           <history_success_lifetime>60</history_success_lifetime>
           <history_failure_lifetime>600</history_failure_lifetime>
           <use_separate_process>1</use_separate_process>
       </group>
   </config>
   ```

En beskrivning av vad alternativen betyder finns i [Anpassa crons-referens](custom-cron-reference.md).

## Steg 8: Verifiera din anpassade kundriskgrupp

Detta _valfri_ visas hur du verifierar din anpassade cron-grupp med Admin.

Så här verifierar du din anpassade cron-grupp:

1. Kör Commerce cron-jobb för din anpassade grupp:

   ```bash
   php /var/www/html/magento2/bin/magento cron:run --group="custom_crongroup"
   ```

   Kör kommandot minst två gånger.

1. Rensa cacheminnet:

   ```bash
   php /var/www/html/magento2/bin/magento cache:clean
   ```

1. Logga in på administratören som administratör.
1. Klicka **Lager** > **Inställningar** > **Konfiguration** > **Avancerat** > **System**.
1. Expandera i den högra rutan **Cron**.

   Kronsgruppen visas enligt följande:

   ![Din anpassade cron-grupp](../../assets/configuration/cron-group.png)

<!-- link definitions -->

[git-ssh]: https://docs.github.com/en/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account
[samples]: https://github.com/magento/magento2-samples
