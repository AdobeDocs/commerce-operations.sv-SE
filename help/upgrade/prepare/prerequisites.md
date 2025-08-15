---
title: Förutsättningar
description: Förbered ditt Adobe Commerce-projekt för en uppgradering genom att slutföra dessa nödvändiga steg.
exl-id: f7775900-1d10-4547-8af0-3d1283d9b89e
source-git-commit: df185e21f918d32ed5033f5db89815b5fc98074f
workflow-type: tm+mt
source-wordcount: '1866'
ht-degree: 0%

---

# Krav för fullständig uppgradering

Det är viktigt att förstå vad som krävs för att köra Adobe Commerce. Du måste först granska [systemkraven](../../installation/system-requirements.md) för den version du planerar att uppgradera till.

När du har granskat systemkraven måste du uppfylla följande krav innan du uppgraderar systemet:

* Uppdatera all programvara
* Kontrollera att en sökmotor som stöds är installerad
* Konvertera databastabellformat
* Ange gräns för öppna filer
* Verifiera att cron-jobb körs
* Ange `DATA_CONVERTER_BATCH_SIZE`
* Verifiera behörigheter i filsystemet
* Ange katalogroten `pub/`
* Installera plugin-programmet för Composer-uppdatering

## Uppdatera all programvara

[Systemkraven](../../installation/system-requirements.md) beskriver exakt vilka versioner av tredjepartsprogram som har testats med Adobe Commerce-versioner.

Se till att du har uppdaterat alla systemkrav och beroenden i din miljö. Se PHP [ 7.4](https://www.php.net/manual/en/migration74.php), PHP [ 8.0](https://www.php.net/manual/en/migration80.php), PHP [ 8.1](https://www.php.net/manual/en/migration81.php) och [nödvändiga PHP-inställningar](../../installation/prerequisites/php-settings.md#php-settings).

>[!NOTE]
>
>För Adobe Commerce i molnbaserade infrastrukturproprojekt måste du skapa en [supportbiljett](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket) för att kunna installera eller uppdatera tjänster i mellanlagrings- och produktionsmiljöer. Ange de tjänständringar som krävs och inkludera dina uppdaterade `.magento.app.yaml`- och `services.yaml`-filer och PHP-version i biljetten. Det kan ta upp till 48 timmar för molninfrastrukturteamet att uppdatera ditt projekt. Se [Program och tjänster som stöds](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/cloud-architecture.html#supported-software-and-services).

## Kontrollera att en sökmotor som stöds är installerad

Adobe Commerce kräver att Elasticsearch eller OpenSearch är installerat för att du ska kunna använda programmet.

**Om du uppgraderar från 2.3.x till 2.4** måste du kontrollera om du använder MySQL, Elasticsearch eller ett tillägg från tredje part som katalogsökmotor i din 2.3.x-instans. Resultatet avgör vad du måste göra _innan_ uppgraderar till 2.4.

**Om du uppgraderar korrigeringsutgåvor på versionslinjerna 2.3.x eller 2.4.x** kan du [migrera till OpenSearch](opensearch-migration.md) om Elasticsearch 7.x redan är installerat.

Du kan använda kommandoraden eller Admin för att bestämma katalogsökmotorn:

* Ange kommandot `bin/magento config:show catalog/search/engine`. Kommandot returnerar värdet `mysql`, `elasticsearch` (vilket anger att Elasticsearch 2 har konfigurerats), `elasticsearch5`, `elasticsearch6`, `elasticsearch7` eller ett anpassat värde, vilket anger att du har installerat en sökmotor från tredje part. För tidigare versioner än 2.4.6 använder du värdet `elasticsearch7` för Elasticsearch 7- eller OpenSearch-motorn. Använd värdet `opensearch` för OpenSearch-motorn för version 2.4.6 och senare.

* Gå till Admin och kontrollera värdet för fältet **[!UICONTROL Stores]** > [!UICONTROL Settings] > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog Search]** > **[!UICONTROL Search Engine]**.

I följande avsnitt beskrivs vilka åtgärder du måste vidta innan du uppgraderar till 2.4.0.

### MySQL

Från och med 2.4 är MySQL inte längre en katalogsökmotor som stöds. Du måste installera och konfigurera Elasticsearch eller OpenSearch innan du uppgraderar. Använd följande resurser för att hjälpa dig igenom den här processen:

* [Installera och konfigurera Elasticsearch](../../configuration/search/overview-search.md)
* [Installerar Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/current/install-elasticsearch.html)
* Konfigurera [nginx](../../installation/prerequisites/search-engine/configure-nginx.md) eller [Apache](../../installation/prerequisites/search-engine/configure-apache.md) så att det fungerar med sökmotorn
* [Konfigurera Commerce att använda Elasticsearch](../../configuration/search/configure-search-engine.md) och indexera om

Vissa katalogsökmotorer från tredje part körs ovanpå Adobe Commerce sökmotor. Kontakta leverantören för att avgöra om du måste uppdatera tillägget.

### MySQL 8.4-ändringar

Adobe har lagt till stöd för MySQL 8.4 i version 2.4.8.
I det här avsnittet beskrivs viktiga ändringar av MySQL 8.4 som utvecklare bör känna till.

#### Inaktuell nyckel som inte är standard

Användning av icke-unika eller partiella nycklar som sekundärnycklar är inte standard och används inte i MySQL 8.4. Från och med MySQL 8.4.0 måste du uttryckligen aktivera sådana nycklar genom att ange [`restrict_fk_on_non_standard_key`](https://dev.mysql.com/doc/refman/8.4/en/server-system-variables.html#sysvar_restrict_fk_on_non_standard_key) till `OFF` eller genom att starta servern med alternativet `--skip-restrict-fk-on-non-standard-key`.

#### Uppgradera från MySQL 8.0 (eller tidigare versioner) till MySQL 8.4

För att kunna uppgradera MySQL från version 8.0 till version 8.4 måste du följa dessa steg för att:

1. Aktivera underhållsläge:

   ```bash
   bin/magento maintenance:enable
   ```

1. Säkerhetskopiera databasen:

   ```bash
   bin/magento setup:backup --db
   ```

1. Uppgradera MySQL till version 8.4.
1. Ange `restrict_fk_on_non_standard_key` som `OFF` i `[mysqld]` i filen `my.cnf`.

   ```bash
   [mysqld]
   restrict_fk_on_non_standard_key = OFF 
   ```

   >[!WARNING]
   >
   >Om du inte ändrar värdet för `restrict_fk_on_non_standard_key` till `OFF` får du följande fel under importen:
   >
   ```sql
   > ERROR 6125 (HY000) at line 2164: Failed to add the foreign key constraint. Missing unique key for constraint 'CAT_PRD_FRONTEND_ACTION_PRD_ID_CAT_PRD_ENTT_ENTT_ID' in the referenced table 'catalog_product_entity'
   >```
1. Starta om MySQL-servern.
1. Importera säkerhetskopierade data till MySQL.
1. Rensa cachen:

   ```bash
   bin/magento cache:clean
   ```

1. Inaktivera underhållsläge:

   ```bash
   bin/magento maintenance:disable
   ```

#### MariaDB

{{$include /help/_includes/maria-db-config.md}}

### Sökmotor

Du måste installera och konfigurera Elasticsearch 7.6 eller senare eller OpenSearch 1.2 innan du uppgraderar till 2.4.0. Adobe stöder inte längre Elasticsearch 2.x, 5.x och 6.x. [Sökmotorkonfigurationen](../../configuration/search/configure-search-engine.md) i _Konfigurationshandboken_ beskriver de åtgärder du måste utföra efter att du har uppgraderat Elasticsearch till en version som stöds.

Se [Uppgradera Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/current/setup-upgrade.html) för fullständiga instruktioner om hur du säkerhetskopierar data, identifierar potentiella migreringsproblem och testar uppgraderingar innan du distribuerar till produktionen. Beroende på vilken version av Elasticsearch du har behöver du kanske starta om hela klustret eller inte.

Elasticsearch kräver Java Development Kit (JDK) 1.8 eller senare. Se [Installera Java Software Development Kit (JDK)](../../installation/prerequisites/search-engine/overview.md#install-the-java-software-development-kit-jdk) för att kontrollera vilken version av JDK som är installerad.

#### OpenSearch

OpenSearch är en öppen källkodsgaffel till Elasticsearch 7.10.2 efter Elasticsearch licensändring. I följande versioner av Adobe Commerce finns stöd för OpenSearch:

* 2.4.6 (OpenSearch har en separat modul och inställningar)
* 2.4.5
* 2.4.4
* 2.4.3-p2
* 2.3.7-p3

Du kan [migrera från Elasticsearch till OpenSearch](opensearch-migration.md) endast om du uppgraderar till en version av Adobe Commerce som listas ovan (eller senare).

OpenSearch kräver JDK 1.8 eller senare. Se [Installera Java Software Development Kit (JDK)](../../installation/prerequisites/search-engine/overview.md#install-the-java-software-development-kit-jdk) för att kontrollera vilken version av JDK som är installerad.

[Sökmotorkonfigurationen](../../configuration/search/configure-search-engine.md) beskriver de uppgifter du måste utföra efter att du har ändrat sökmotorer.

#### Uppgradera Elasticsearch

Stöd för Elasticsearch 8.x infördes i Adobe Commerce 2.4.6. Följande instruktioner visar ett exempel på hur du uppgraderar Elasticsearch från 7.x till 8.x:

>[!NOTE]
>
>I den kommande 2.4.8-versionen behövs inte dessa steg eftersom Elasticsearch 8-modulen ingår som standard och du inte behöver installera den separat.

1. Uppgradera Elasticsearch 7.x-servern till 8.x och se till att den är igång. Se [Elasticsearch-dokumentationen](https://www.elastic.co/guide/en/elasticsearch/reference/current/install-elasticsearch.html).

1. Aktivera fältet `id_field_data` genom att lägga till följande konfiguration i filen `elasticsearch.yml` och starta om tjänsten Elasticsearch 8.x.

   ```yaml
   indices:
     id_field_data:
       enabled: true
   ```

   >[!INFO]
   >
   >För att ha stöd för Elasticsearch 8.x tillåter inte Adobe Commerce 2.4.6 egenskapen `indices.id_field_data` som standard och använder fältet `_id` i egenskapen `docvalue_fields`.

1. Uppdatera dina Composer-beroenden i Adobe Commerce-projektets rotkatalog för att ta bort modulen `Magento_Elasticsearch7` och installera modulen `Magento_Elasticsearch8`.

   ```bash
   composer require magento/module-elasticsearch-8 --update-with-all-dependencies
   ```

   Om du råkar ut för ett beroendefel för `psr/http-message`, klickar du för att expandera följande felsökningsavsnitt:

   +++Felsökning

   Om du stöter på beroendekonflikter när du installerar Elasticsearch 8, särskilt med `psr/http-message`, kan du lösa detta genom att följa de här stegen:

   1. Kräv först modulen Elasticsearch 8 utan att uppdatera andra beroenden:

      ```bash
      composer require magento/module-elasticsearch-8 --no-update
      ```

   1. Uppdatera sedan Elasticsearch 8-modulen och `aws/aws-sdk-php`-paketen:

      ```bash
      composer update magento/module-elasticsearch-8 aws/aws-sdk-php -W
      ```

   Detta tillvägagångssätt fungerar för 2.4.7-p4 med PHP 8.3. Problemet inträffar eftersom `aws/aws-sdk-php` kräver `psr/http-message >= 2.0`, vilket kan orsaka konflikter. Ovanstående steg hjälper dig att lösa dessa beroendeproblem.

   +++

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

Om du av misstag uppgraderar Elasticsearch-versionen på servern eller av någon annan anledning måste du också uppdatera dina Adobe Commerce projektberoenden. Om du till exempel vill nedgradera från Elasticsearch 8.x till 7.x

1. Uppgradera Elasticsearch 8.x-servern till 7.x och se till att den är igång. Se [Elasticsearch-dokumentationen](https://www.elastic.co/guide/en/elasticsearch/reference/current/install-elasticsearch.html).

1. Uppdatera dina Composer-beroenden i Adobe Commerce-projektets rotkatalog för att ta bort modulen `Magento_Elasticsearch8` och dess Composer-beroenden och installera modulen `Magento_Elasticsearch7`.

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

Du måste konvertera formatet för alla databastabeller från `COMPACT` till `DYNAMIC`. Du måste också konvertera lagringsmotortypen från `MyISAM` till `InnoDB`. Se [bästa praxis](../../implementation-playbook/best-practices/maintenance/mariadb-upgrade.md).

## Ange gräns för öppna filer

Genom att ange gränsen för antalet öppna filer (ulimit) kan du undvika fel vid flera rekursiva anrop av långa frågesträngar eller problem med att använda kommandot `bin/magento setup:rollback`. Det här kommandot är annorlunda för olika UNIX-skal. Mer information om kommandot `ulimit` finns i din individuella variant.

Adobe rekommenderar att de öppna filerna [ulimit](https://ss64.com/bash/ulimit.html) anges till `65536` eller mer, men du kan använda ett större värde om det behövs. Du kan ange gränsen på kommandoraden eller göra den till en permanent inställning för användarens skal.

Så här anger du gränsen från kommandoraden:

1. Växla till [filsystemets ägare](../../installation/prerequisites/file-system/overview.md).
1. Ange gränsen till `65536`.

   ```bash
   ulimit -n 65536
   ```

Så här anger du värdet i Bash-skalet:

1. Växla till [filsystemets ägare](../../installation/prerequisites/file-system/overview.md).
1. Öppna `/home/<username>/.bashrc` i en textredigerare.
1. Lägg till följande rad:

   ```bash
   ulimit -n 65536
   ```

1. Spara ändringarna i filen `.bashrc` och avsluta textredigeraren.

>[!IMPORTANT]
>
>Vi rekommenderar att du undviker att ange ett värde för egenskapen `pcre.recursion_limit` i filen `php.ini` eftersom det kan leda till ofullständiga återställningar utan felmeddelande.

## Verifiera att cron-jobb körs

UNIX-uppgiftsschemaläggaren `cron` är viktig för de dagliga Adobe Commerce-åtgärderna. Det schemalägger saker som omindexering, nyhetsbrev, e-post och webbplatskartor. Flera funktioner kräver minst ett cron-jobb som körs som filsystemets ägare.

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

![Systemmeddelanden - kron körs inte](../../assets/upgrade-guide/cron-not-running.png)

Om du vill visa felet klickar du på **Systemmeddelanden** högst upp i fönstret enligt följande:

![Systemmeddelanden](../../assets/upgrade-guide/system-messages.png)

Mer information finns i [Konfigurera och köra cron](../../configuration/cli/configure-cron-jobs.md).

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

Om du har en stor mängd data kan du förbättra prestandan genom att ange värdet för en miljövariabel, `DATA_CONVERTER_BATCH_SIZE`. Som standard är värdet `50,000`.

Så här anger du miljövariabeln:

1. Växla till [filsystemets ägare](../../installation/prerequisites/file-system/overview.md).
1. Ange variabeln:

   ```bash
   export DATA_CONVERTER_BATCH_SIZE=100000
   ```

   >[!NOTE]
   >
   > `DATA_CONVERTER_BATCH_SIZE` kräver minne. Undvik att ange ett stort värde (ungefär 1 GB) utan att först testa det.

1. När uppgraderingen är klar kan du ta bort variabeln:

   ```bash
   unset DATA_CONVERTER_BATCH_SIZE
   ```

## Verifiera behörigheter i filsystemet

Av säkerhetsskäl kräver Adobe Commerce vissa behörigheter i filsystemet. Behörigheter skiljer sig från _[ägarskap](../../upgrade/prepare/prerequisites.md#verify-file-system-permissions)_. Ägarskapet avgör vem som kan utföra åtgärder i filsystemet. Behörigheterna avgör vad användaren kan göra.

Kataloger i filsystemet måste vara skrivbara av [filsystemets ägargrupp ](../../installation/prerequisites/file-system/overview.md).

Om du vill verifiera att filsystembehörigheterna är korrekt loggar du antingen in på programservern eller använder värdtjänstleverantörens filhanterarprogram.

Ange till exempel följande kommando om programmet är installerat i `/var/www/html/magento2`:

```bash
ls -l /var/www/html/magento2
```

Exempel:

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

* De flesta filerna är `-rw-rw----`, vilket är `660`
* `drwxrwx---` = `770`
* `-rw-rw-rw-` = `666`
* Filsystemets ägare är `magento_user`

Om du vill ha mer detaljerad information anger du följande kommando:

```bash
ls -la /var/www/html/magento2/pub
```

Eftersom Adobe Commerce distribuerar statiska filresurser till underkataloger till `pub` är det en bra idé att verifiera behörigheter och ägarskap även där.

Mer information finns i [Filsystembehörigheter och ägarskap](../../installation/prerequisites/file-system/overview.md).

## Ange katalogroten `pub/`

Mer information finns i [Förbättra säkerheten genom att ändra dokumentroten](../../installation/tutorials/docroot.md).

## Installera plugin-programmet för Composer-uppdatering

[`magento/composer-root-update-plugin`](https://github.com/magento/composer-root-update-plugin) Composer-plugin-programmet åtgärdar ändringar som måste göras i rotprojektfilen `composer.json` innan det uppdateras till ett nytt produktkrav.

Plugin-programmet automatiserar delvis den manuella uppgraderingen genom att identifiera och hjälpa dig att lösa beroendekonflikter i stället för att kräva att du identifierar och åtgärdar dem manuellt.

Installera plugin-programmet:

1. Lägg till paketet i din `composer.json`-fil.

   ```bash
   composer require magento/composer-root-update-plugin ~2.0 --no-update
   ```

1. Uppdatera beroenden:

   ```bash
   composer update
   ```
