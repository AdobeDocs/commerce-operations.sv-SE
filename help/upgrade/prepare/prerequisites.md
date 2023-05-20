---
title: Förutsättningar
description: Förbered ditt Adobe Commerce-projekt för en uppgradering genom att slutföra dessa nödvändiga steg.
exl-id: f7775900-1d10-4547-8af0-3d1283d9b89e
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '1639'
ht-degree: 0%

---

# Krav för fullständig uppgradering

Det är viktigt att förstå vad som krävs för att köra Adobe Commerce. Du måste först granska [systemkrav](../../installation/system-requirements.md) för den version du tänker uppgradera till.

När du har granskat systemkraven måste du uppfylla följande krav innan du uppgraderar systemet:

* Uppdatera all programvara
* Kontrollera att en sökmotor som stöds är installerad
* Konvertera databastabellformat
* Ange gräns för öppna filer
* Verifiera att cron-jobb körs
* Ange `DATA_CONVERTER_BATCH_SIZE`
* Verifiera behörigheter i filsystemet
* Ange `pub/` katalogrot
* Installera plugin-programmet för Composer-uppdatering

## Uppdatera all programvara

The [systemkrav](../../installation/system-requirements.md) beskriv exakt vilka versioner av tredjepartsprogram som har testats med Adobe Commerce-releaser.

Se till att du har uppdaterat alla systemkrav och beroenden i din miljö. Se PHP [7.4](https://www.php.net/manual/en/migration74.php), PHP [8.0](https://www.php.net/manual/en/migration80.php), PHP [8.1](https://www.php.net/manual/en/migration81.php)och [obligatoriska PHP-inställningar](../../installation/prerequisites/php-settings.md#php-settings).

>[!NOTE]
>
>För Adobe Commerce i molnbaserade infrastrukturprojekt måste du skapa en [Support](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket) biljett för att installera eller uppdatera tjänster i mellanlagrings- och produktionsmiljöer. Ange vilka tjänständringar som krävs och inkludera dina uppdaterade `.magento.app.yaml` och `services.yaml` filer och PHP-version i biljetten. Det kan ta upp till 48 timmar för molninfrastrukturteamet att uppdatera ditt projekt. Se [Programvara och tjänster som stöds](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/cloud-architecture.html#supported-software-and-services).

## Kontrollera att en sökmotor som stöds är installerad

Adobe Commerce kräver att Elasticsearch eller OpenSearch är installerade för att programmet ska kunna användas.

**Om du uppgraderar från 2.3.x till 2.4** måste du kontrollera om du använder MySQL, Elasticsearch eller ett tillägg från tredje part som katalogsökmotor i din 2.3.x-instans. Resultatet avgör vad du måste göra _före_ uppgradering till 2.4.

**Om du uppgraderar korrigeringsfiler i versionerna 2.3.x eller 2.4.x** om Elasticsearch 7.x redan är installerat kan du [migrera till OpenSearch](opensearch-migration.md).

Du kan använda kommandoraden eller Admin för att bestämma katalogsökmotorn:

* Ange `bin/magento config:show catalog/search/engine` -kommando. Kommandot returnerar värdet `mysql`, `elasticsearch` (vilket anger att Elasticsearch 2 är konfigurerad), `elasticsearch5`, `elasticsearch6`, `elasticsearch7`, eller ett anpassat värde, som anger att du har installerat en sökmotor från tredje part. För tidigare versioner än 2.4.6 använder du `elasticsearch7` för Elasticsearch 7- eller OpenSearch-motorn. För version 2.4.6 och senare använder du `opensearch` för OpenSearch-motorn.

* Kontrollera värdet för **[!UICONTROL Stores]** > [!UICONTROL Settings] > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog Search]** > **[!UICONTROL Search Engine]** fält.

I följande avsnitt beskrivs vilka åtgärder du måste vidta innan du uppgraderar till 2.4.0.

### MySQL

Från och med 2.4 är MySQL inte längre en katalogsökmotor som stöds. Du måste installera och konfigurera Elasticsearch eller OpenSearch innan du uppgraderar. Använd följande resurser för att hjälpa dig igenom den här processen:

* [Installera och konfigurera Elasticsearch](../../configuration/search/overview-search.md)
* [Installerar Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/current/install-elasticsearch.html)
* Konfigurera [nginx](../../installation/prerequisites/search-engine/configure-nginx.md) eller [Apache](../../installation/prerequisites/search-engine/configure-apache.md) för att arbeta med din sökmotor
* [Konfigurera Commerce att använda Elasticsearch](../../configuration/search/configure-search-engine.md) och indexera om

Vissa katalogsökmotorer från tredje part körs ovanpå Adobe Commerce sökmotor. Kontakta leverantören för att avgöra om du måste uppdatera tillägget.

#### MariaDB

{{$include /help/_includes/maria-db-config.md}}

### Sökmotor

Du måste installera och konfigurera Elasticsearch 7.6 eller senare eller OpenSearch 1.2 innan du uppgraderar till 2.4.0. Adobe stöder inte längre Elasticsearch 2.x, 5.x och 6.x. [Sökmotorkonfiguration](../../configuration/search/configure-search-engine.md) i _Konfigurationshandbok_ beskriver de uppgifter du måste utföra efter att ha uppgraderat Elasticsearch till en version som stöds.

Se [Uppgraderar Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/current/setup-upgrade.html) om du vill ha fullständiga anvisningar om hur du säkerhetskopierar data, upptäcker potentiella migreringsproblem och testar uppgraderingar innan du distribuerar till produktionen. Beroende på vilken version av Elasticsearch du använder behöver du kanske inte starta om hela klustret.

Elasticsearch kräver Java Development Kit (JDK) 1.8 eller senare. Se [Installera Java Software Development Kit (JDK)](../../installation/prerequisites/search-engine/overview.md#install-the-java-software-development-kit-jdk) för att kontrollera vilken version av JDK som är installerad.

#### OpenSearch

OpenSearch är en öppen källkodsgaffel i Elasticsearch 7.10.2 efter Elasticsearch licenschange. I följande versioner av Adobe Commerce finns stöd för OpenSearch:

* 2.4.6 (OpenSearch har en separat modul och inställningar)
* 2.4.5
* 2.4.4
* 2.4.3-p2
* 2.3.7-p3

Du kan [migrera från Elasticsearch till OpenSearch](opensearch-migration.md) endast om du uppgraderar till en version av Adobe Commerce som listas ovan (eller senare).

OpenSearch kräver JDK 1.8 eller senare. Se [Installera Java Software Development Kit (JDK)](../../installation/prerequisites/search-engine/overview.md#install-the-java-software-development-kit-jdk) för att kontrollera vilken version av JDK som är installerad.

[Sökmotorkonfiguration](../../configuration/search/configure-search-engine.md) beskriver de åtgärder du måste utföra efter att du har ändrat sökmotorer.

#### Uppgradera Elasticsearch

Stöd för Elasticsearch 8.x introducerades i Adobe Commerce 2.4.6. Följande instruktioner visar ett exempel på hur du uppgraderar Elasticsearch från 7.x till 8.x:

1. Uppgradera servern Elasticsearch 7.x till 8.x och kontrollera att den är igång. Se [Elasticsearch dokumentation](https://www.elastic.co/guide/en/elasticsearch/reference/current/install-elasticsearch.html).

1. Aktivera `id_field_data` genom att lägga till följande konfiguration i `elasticsearch.yml` och starta om tjänsten Elasticsearch 8.x.

   ```yaml
   indices:
     id_field_data:
       enabled: true
   ```

   >[!INFO]
   >
   >Adobe Commerce 2.4.6 tillåter inte att Elasticsearch 8.x stöds `indices.id_field_data` som standard och använder `_id` i `docvalue_fields` -egenskap.

1. Uppdatera dina Composer-beroenden i Adobe Commerce-projektets rotkatalog för att ta bort `Magento_Elasticsearch7` och installera `Magento_Elasticsearch8` -modul.

   ```bash
   composer require magento/module-elasticsearch-8 --update-with-all-dependencies
   ```

1. Uppdatera projektkomponenterna.

   ```bash
   bin/magento setup:upgrade
   ```

1. [Konfigurera Elasticsearch](../../configuration/search/configure-search-engine.md#configure-your-search-engine-from-the-admin) i [!DNL Admin].

1. Indexera om katalogindexet.

   ```bash
   bin/magento indexer:reindex catalogsearch_fulltext
   ```

1. Ta bort alla objekt från de aktiverade cachetyperna.

   ```bash
   bin/magento cache:clean
   ```

#### Nedgradera Elasticsearch

Om du av misstag uppgraderar Elasticsearch på servern eller av någon annan anledning måste du också uppdatera dina Adobe Commerce projektberoenden. Om du till exempel vill nedgradera från Elasticsearch 8.x till 7.x

1. Uppgradera servern Elasticsearch 8.x till 7.x och kontrollera att den är igång. Se [Elasticsearch dokumentation](https://www.elastic.co/guide/en/elasticsearch/reference/current/install-elasticsearch.html).

1. Uppdatera dina Composer-beroenden i Adobe Commerce-projektets rotkatalog för att ta bort `Magento_Elasticsearch8` och dess Composer-beroenden och installera `Magento_Elasticsearch7` -modul.

   ```bash
   composer remove magento/module-elasticsearch-8
   ```

1. Uppdatera projektkomponenterna.

   ```bash
   bin/magento setup:upgrade
   ```

1. [Konfigurera Elasticsearch](../../configuration/search/configure-search-engine.md#configure-your-search-engine-from-the-admin) i [!DNL Admin].

1. Indexera om katalogindexet.

   ```bash
   bin/magento indexer:reindex catalogsearch_fulltext
   ```

1. Ta bort alla objekt från de aktiverade cachetyperna.

   ```bash
   bin/magento cache:clean
   ```

### Tredjepartstillägg

Vi rekommenderar att du kontaktar din sökmotorleverantör för att avgöra om ditt tillägg är helt kompatibelt med en Adobe Commerce-release.

## Konvertera databastabellformat

Du måste konvertera formatet för alla databastabeller från `COMPACT` till `DYNAMIC`. Du måste också konvertera lagringsmotortypen från `MyISAM` till `InnoDB`. Se [bästa praxis](../../implementation-playbook/best-practices/maintenance/commerce-235-upgrade-prerequisites-mariadb.md).

## Ange gräns för öppna filer

Genom att ange gränsen för antalet öppna filer (ulimit) kan du undvika fel vid flera rekursiva anrop av långa frågesträngar eller problem med att använda `bin/magento setup:rollback` -kommando. Det här kommandot är annorlunda för olika UNIX-skal. Mer information om `ulimit` -kommando.

Adobe rekommenderar att du anger öppna filer [ulimit](https://ss64.com/bash/ulimit.html) till ett värde av `65536` eller mer, men du kan använda ett större värde om det behövs. Du kan ange gränsen på kommandoraden eller göra den till en permanent inställning för användarens skal.

Så här anger du gränsen från kommandoraden:

1. Växla till [ägare av filsystem](../../installation/prerequisites/file-system/overview.md).
1. Ange gränsvärdet till `65536`.

   ```bash
   ulimit -n 65536
   ```

Så här anger du värdet i Bash-skalet:

1. Växla till [ägare av filsystem](../../installation/prerequisites/file-system/overview.md).
1. Öppna `/home/<username>/.bashrc` i en textredigerare.
1. Lägg till följande rad:

   ```bash
   ulimit -n 65536
   ```

1. Spara ändringarna i `.bashrc` och avsluta textredigeraren.

>[!IMPORTANT]
>
>Vi rekommenderar att du undviker att ange ett värde för `pcre.recursion_limit` -egenskapen i `php.ini` eftersom det kan resultera i ofullständiga återställningar utan felmeddelande.

## Verifiera att cron-jobb körs

UNIX-uppgiftsschemaläggaren `cron` är avgörande för Adobe Commerce dagliga verksamhet. Det schemalägger saker som omindexering, nyhetsbrev, e-post och webbplatskartor. Flera funktioner kräver minst ett cron-jobb som körs som filsystemets ägare.

Kontrollera på fliken crontab genom att ange följande kommando som ägare av filsystemet för att kontrollera att ditt cron-jobb är korrekt konfigurerat:

>[!NOTE]
>
>crontab är den konfigurationsfil som ansvarar för att köra cron-jobb.

```bash
crontab -l
```

Resultat som liknar följande ska visas:

```cron
#~ MAGENTO START c5f9e5ed71cceaabc4d4fd9b3e827a2b
* * * * * /usr/bin/php /var/www/html/magento2/bin/magento cron:run 2>&1 | grep -v "Ran jobs by schedule" >> /var/www/html/magento2/var/log/magento.cron.log
#~ MAGENTO END c5f9e5ed71cceaabc4d4fd9b3e827a2b
```

Ett annat symtom på att kron inte körs är följande fel i Admin:

![](../../assets/upgrade-guide/cron-not-running.png)

Klicka på **Systemmeddelanden** högst upp i fönstret enligt följande:

![](../../assets/upgrade-guide/system-messages.png)

Se [Konfigurera och kör cron](../../configuration/cli/configure-cron-jobs.md) för mer information.

## Ange DATA_CONVERTER_BATCH_SIZE

Adobe Commerce 2.4 innehåller säkerhetsförbättringar som kräver att vissa data konverteras från serialiserade till JSON. Den här konverteringen sker under uppgraderingen och kan ta lång tid, beroende på hur mycket data som finns i databasen.

Följande tabeller påverkas mest:

* `catalogrule`
* `core_config_data`
* `magento_reward_history`
* `quote_payment`
* `quote`
* `sales_order_payment`
* `sales_order`
* `salesrule`
* `url_rewrite`

Om du har en stor mängd data kan du förbättra prestandan genom att ange värdet för en miljövariabel, `DATA_CONVERTER_BATCH_SIZE`. Som standard är värdet inställt på `50,000`.

Så här anger du miljövariabeln:

1. Växla till [ägare av filsystem](../../installation/prerequisites/file-system/overview.md).
1. Ange variabeln:

   ```bash
   export DATA_CONVERTER_BATCH_SIZE=100000
   ```

   >[!NOTE]
   >
   > `DATA_CONVERTER_BATCH_SIZE` kräver minne, Undvik att ange ett stort värde (ungefär 1 GB) utan att först testa det.

1. När uppgraderingen är klar kan du ta bort variabeln:

   ```bash
   unset DATA_CONVERTER_BATCH_SIZE
   ```

## Verifiera behörigheter i filsystemet

Av säkerhetsskäl kräver Adobe Commerce vissa behörigheter i filsystemet. Behörigheterna skiljer sig från _[ägarskap](../../upgrade/prepare/prerequisites.md#verify-file-system-permissions)_. Ägarskapet avgör vem som kan utföra åtgärder i filsystemet. behörigheter bestämmer vad användaren kan göra.

Kataloger i filsystemet måste vara skrivbara av [filsystemets ägare](../../installation/prerequisites/file-system/overview.md) grupp.

Om du vill verifiera att filsystembehörigheterna är korrekt loggar du antingen in på programservern eller använder värdtjänstleverantörens filhanterarprogram.

Ange till exempel följande kommando om programmet är installerat i `/var/www/html/magento2`:

```bash
ls -l /var/www/html/magento2
```

Exempelutdata:

```console
total 1028
drwxrwx---. 12 magento_user apache   4096 Jun  7 07:55 .
drwxr-xr-x.  3 root         root     4096 May 11 14:29 ..
drwxrwx---.  4 magento_user apache   4096 Jun  7 07:53 app
drwxrwx---.  2 magento_user apache   4096 Jun  7 07:53 bin
-rw-rw----.  1 magento_user apache 439792 Apr 27 21:23 CHANGELOG.md
-rw-rw----.  1 magento_user apache   3422 Apr 27 21:23 composer.json
-rw-rw----.  1 magento_user apache 425214 Apr 27 21:27 composer.lock
-rw-rw----.  1 magento_user apache   3425 Apr 27 21:23 CONTRIBUTING.md
-rw-rw----.  1 magento_user apache  10011 Apr 27 21:23 CONTRIBUTOR_LICENSE_AGREEMENT.html
-rw-rw----.  1 magento_user apache    631 Apr 27 21:23 COPYING.txt
drwxrwx---.  4 magento_user apache   4096 Jun  7 07:53 dev
-rw-rw----.  1 magento_user apache   2926 Apr 27 21:23 Gruntfile.js
-rw-rw----.  1 magento_user apache   7592 Apr 27 21:23 .htaccess
-rw-rw----.  1 magento_user apache   6419 Apr 27 21:23 .htaccess.sample
drwxrwx---.  4 magento_user apache   4096 Jun  7 07:53 lib
-rw-rw----.  1 magento_user apache  10376 Apr 27 21:23 LICENSE_AFL.txt
-rw-rw----.  1 magento_user apache  30634 Apr 27 21:23 LICENSE_EE.txt
-rw-rw----.  1 magento_user apache  10364 Apr 27 21:23 LICENSE.txt
-rw-rw----.  1 magento_user apache   4108 Apr 27 21:23 nginx.conf.sample
-rw-rw----.  1 magento_user apache   1427 Apr 27 21:23 package.json
-rw-rw----.  1 magento_user apache   1659 Apr 27 21:23 .php_cs
-rw-rw----.  1 magento_user apache    804 Apr 27 21:23 php.ini.sample
drwxrwx---.  2 magento_user apache   4096 Jun  7 07:53 phpserver
drwxrwx---.  6 magento_user apache   4096 Jun  7 07:53 pub
-rw-rw----.  1 magento_user apache   2207 Apr 27 21:23 README_EE.md
drwxrwx---.  7 magento_user apache   4096 Jun  7 07:53 setup
-rw-rw----.  1 magento_user apache   3731 Apr 27 21:23 .travis.yml
drwxrwx---.  7 magento_user apache   4096 Jun  7 07:53 update
drwxrws---. 11 magento_user apache   4096 Jun 13 16:05 var
drwxrws---. 29 magento_user apache   4096 Jun  7 07:53 vendor
```

Se följande för en förklaring av exempelresultatet:

* De flesta filerna är `-rw-rw----`, som `660`
* `drwxrwx---` = `770`
* `-rw-rw-rw-` = `666`
* Ägaren av filsystemet är `magento_user`

Om du vill ha mer detaljerad information anger du följande kommando:

```bash
ls -la /var/www/html/magento2/pub
```

Eftersom Adobe Commerce distribuerar statiska filresurser till underkataloger till `pub`, det är en bra idé att även verifiera behörigheter och ägarskap där.

Mer information finns i [Filsystembehörigheter och ägarskap](../../installation/prerequisites/file-system/overview.md).

## Ange `pub/` katalogrot

Se [Förbättra säkerheten genom att ändra dokumentroten](../../installation/tutorials/docroot.md) för mer information.

## Installera plugin-programmet för Composer-uppdatering

The [`magento/composer-root-update-plugin`](https://github.com/magento/composer-root-update-plugin) Composer-plugin-programmet åtgärdar ändringar som måste göras i rotprojektet `composer.json` filen innan den uppdateras till ett nytt produktkrav.

Plugin-programmet automatiserar delvis den manuella uppgraderingen genom att identifiera och hjälpa dig att lösa beroendekonflikter i stället för att kräva att du identifierar och åtgärdar dem manuellt.

Så här installerar du plugin-programmet:

1. Lägg till paketet i `composer.json` -fil.

   ```bash
   composer require magento/composer-root-update-plugin ~2.0 --no-update
   ```

1. Uppdatera beroenden:

   ```bash
   composer update
   ```
