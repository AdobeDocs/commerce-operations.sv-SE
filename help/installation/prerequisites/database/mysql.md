---
title: MySQL-riktlinjer
description: Följ de här stegen för att installera och konfigurera MySQL och MariaDB för lokala installationer av Adobe Commerce och Magento Open Source.
source-git-commit: c65217cd277be5226681ef239d6a3cf34c251a9f
workflow-type: tm+mt
source-wordcount: '1142'
ht-degree: 0%

---


# Allmänna riktlinjer för MySQL

Se [Systemkrav](../../system-requirements.md) för de versioner av MySQL som stöds.

Adobe _starkt_ rekommenderar att du följer följande standard när du konfigurerar databasen:

* Adobe Commerce och Magento Open Source använder [MySQL-databasutlösare](https://dev.mysql.com/doc/refman/8.0/en/triggers.html) för att förbättra databasåtkomsten vid omindexering. Dessa skapas när indexeringsläget är inställt på [schema](../../../configuration/cli/manage-indexers.md#configure-indexers). Programmet stöder inte några anpassade utlösare i databasen eftersom anpassade utlösare kan orsaka inkompatibilitet med framtida versioner av Adobe Commerce och Magento Open Source.
* Bekanta dig med [dessa potentiella MySQL-utlösarbegränsningar](https://dev.mysql.com/doc/mysql-reslimits-excerpt/8.0/en/stored-program-restrictions.html) innan du fortsätter.
* Aktivera [`STRICT_ALL_TABLES`](https://dev.mysql.com/doc/refman/5.7/en/sql-mode.html#sqlmode_strict_all_tables) SQL-läge för att förhindra att ogiltiga datavärden lagras, vilket kan orsaka oönskade databasinteraktioner.
* Adobe Commerce och Magento Open Source _not_ har stöd för MySQL-satsbaserad replikering. Se till att du använder _endast_ [radbaserad replikering](https://dev.mysql.com/doc/refman/8.0/en/replication-formats.html).

>[!WARNING]
>
>Adobe Commerce använder `CREATE TEMPORARY TABLE` programsatser inuti transaktioner, som [inkompatibel](https://dev.mysql.com/doc/refman/5.7/en/replication-gtids-restrictions.html) med databasimplementeringar använder GTID-baserad replikering, som [Andra generationens instanser av Google Cloud SQL](https://cloud.google.com/sql/docs/features#differences). Överväg MySQL för Cloud SQL 8.0 som ett alternativ.

>[!NOTE]
>
>Om webbservern och databasservern finns på olika värdar kan du utföra de uppgifter som beskrivs i det här avsnittet på databasservervärden och sedan se [Konfigurera en MySQL-fjärrdatabasanslutning](mysql-remote.md).

## Installerar MySQL på Ubuntu

Adobe Commerce och Magento Open Source 2.4 kräver en ren installation av MySQL 8.0. Följ länkarna nedan för instruktioner om hur du installerar MySQL på datorn.

* [Ubuntu](https://ubuntu.com/server/docs/databases-mysql)
* [CentOS](https://dev.mysql.com/doc/refman/8.0/en/linux-installation-yum-repo.html)

Om du tror att du kommer att importera ett stort antal produkter kan du öka värdet för [`max_allowed_packet`](https://dev.mysql.com/doc/refman/5.6/en/program-variables.html) som är större än standardvärdet, 16 MB.

>[!NOTE]
>
>Standardvärdet gäller för Adobe Commerce i molninfrastrukturen _och_ lokala projekt. Adobe Commerce i molninfrastruktur Pro-kunder måste öppna en supportbiljett för att öka `max_allowed_packet` värde. Adobe Commerce om molninfrastruktur Starter-kunder kan öka värdet genom att uppdatera konfigurationen i `/etc/mysql/mysql.cnf` -fil.

Om du vill öka värdet öppnar du `/etc/mysql/mysql.cnf` i en textredigerare och leta reda på värdet för `max_allowed_packet`. Spara ändringarna i `mysql.cnf` stäng textredigeraren och starta om MySQL (`service mysql restart`).

Om du vill verifiera det värde du anger anger du följande kommando på `mysql>` fråga:

```sql
SHOW VARIABLES LIKE 'max_allowed_packet';
```

Sedan [Konfigurera databasinstansen](#configuring-the-database-instance).

## MySQL 8-ändringar

För Adobe Commerce och Magento Open Source 2.4 har vi lagt till stöd för MySQL 8.
I det här avsnittet beskrivs viktiga ändringar av MySQL 8 som utvecklare bör känna till.

### Bredd för heltalstyper (utfyllnad) har tagits bort

Specifikationen för visningsbredd för heltalsdatatyper (TINYINT, SMALLINT, MEDIUMINT, INT, BIGINT) har tagits bort i MySQL 8.0.17. Programsatser som innehåller datatypsdefinitioner i utdata visar inte längre visningsbredden för heltalstyper, med undantag för TINYINT(1). MySQL-kopplingar förutsätter att TINYINT(1)-kolumner har sitt ursprung som BOOLEAN-kolumner. Med det här undantaget kan de fortsätta att anta det.

#### Exempel

Beskriv admin_user vid mysql 8.19

| Fält | Typ | Null | Nyckel | Standard | Extra |
| :--- | :--- | :--- | :--- | :--- | :--- |
| user\_id | `int unsigned` | NEJ | PRI | `NULL` | `auto_increment` |
| `firstname` | `varchar(32)` | JA |  | `NULL` |  |
| `lastname` | `varchar(32`) | JA |  | `NULL` |  |
| `email` | `varchar(128)` | JA |  | `NULL` |  |
| `username` | `varchar(40)` | JA | UNI | `NULL` |  |
| `password` | `varchar(255)` | NEJ |  | `NULL` |  |
| `created` | `timestamp` | NEJ |  | `CURRENT_TIMESTAMP` | `DEFAULT_GENERATED` |
| `modified` | `timestamp` | NEJ |  | `CURRENT_TIMESTAMP` | `DEFAULT_GENERATED` vid uppdatering `CURRENT_TIMESTAMP` |
| `logdate` | `timestamp` | JA |  | `NULL` |  |
| `lognum` | `smallint unsigned` | NEJ |  | `0` |  |

Förutom för _TINYINT(1)_, ska all heltalsutfyllnad (TINYINT > 1, SMALLINT, MEDIUMINT, INT, BIGINT) tas bort från `db_schema.xml` -fil.

Mer information finns i [https://dev.mysql.com/doc/relnotes/mysql/8.0/en/news-8-0-19.html#mysqld-8-0-19-feature](https://dev.mysql.com/doc/relnotes/mysql/8.0/en/news-8-0-19.html#mysqld-8-0-19-feature).

### Standardbeteendet ORDER BY

Före 8.0 sorterades posterna efter sekundärnyckeln. Standardsorteringsordningen beror på vilken motor som används.
Ange alltid en sorteringsordning om koden är beroende av en viss sortering.

### ASC- och DESC-kvalificerare för GROUP BY har tagits bort

Från och med MySQL 8.0.13 är den borttagna `ASC` eller `DESC` kvalificerare för `GROUP BY` -satser har tagits bort. Frågor som tidigare förlitats på `GROUP BY` sortering kan ge resultat som skiljer sig från tidigare MySQL-versioner. Om du vill skapa en viss sorteringsordning anger du en `ORDER BY` -sats.

## Commerce och MySQL 8

Vissa förändringar av Adobe Commerce och Magento Open Source har gjorts för att stödja MySQL 8.

### Fråga och infoga beteende

Adobe Commerce och Magento Open Source inaktiverade det reguljära valideringsbeteendet genom att ställa in SET SQL_MODE=&#39; i `/lib/internal/Magento/Framework/DB/Adapter/Pdo/Mysql.php:424.`. Om valideringen är inaktiverad är det möjligt att MySQL trunkerar data. I MySQL har frågebeteendet ändrats: `Select * on my_table where IP='127.0.0.1'` returnerar inte längre resultat eftersom IP-adressen nu visas korrekt som en sträng i stället för som ett heltal.

## Uppgraderar från MySQL 5.7 till MySQL 8

Om du vill uppdatera MySQL korrekt från version 5.7 till version 8 måste du följa dessa steg för att:

1. Uppgradera Adobe Commerce eller Magento Open Source till 2.4.0. Testa allt och kontrollera att systemet fungerar som det ska.
1. Aktivera underhållsläge:

   ```bash
   bin/magento maintenance:enable
   ```

1. Säkerhetskopiera databasen:

   ```bash
   bin/magento setup:backup --db
   ```

1. Uppdatera MySQL till version 8.
1. Importera säkerhetskopierade data till MySQL.
1. Rensa cacheminnet:

   ```bash
   bin/magento cache:clean
   ```

1. Inaktivera underhållsläge:

   ```bash
   bin/magento maintenance:disable
   ```

## Konfigurera databasinstansen

I det här avsnittet beskrivs hur du skapar en databasinstans för Adobe Commerce eller Magento Open Source. Även om en ny databasinstans rekommenderas kan du installera Adobe Commerce eller Magento Open Source med en befintlig databasinstans.

Så här konfigurerar du en MySQL-databasinstans:

1. Logga in på databasservern som vilken användare som helst.
1. Gå till en MySQL-kommandotolk:

   ```bash
   mysql -u root -p
   ```

1. Ange MySQL `root` användarens lösenord när du uppmanas till det.
1. Ange följande kommandon i den ordning som visas för att skapa en databasinstans med namnet `magento` med användarnamn `magento`:

   ```sql
   create database magento;
   ```

   ```sql
   create user 'magento'@'localhost' IDENTIFIED BY 'magento';
   ```

   ```sql
   GRANT ALL ON magento.* TO 'magento'@'localhost';
   ```

   ```sql
   flush privileges;
   ```

1. Retur `exit` för att avsluta kommandotolken.

1. Verifiera databasen:

   ```bash
   mysql -u magento -p
   ```

   Om MySQL-övervakaren visas har du skapat databasen på rätt sätt. Om ett fel visas upprepar du de föregående kommandona.

1. Om webbservern och databasservern finns på olika värdar kan du utföra de uppgifter som beskrivs i det här avsnittet på databasservervärden och sedan se [Konfigurera en MySQL-fjärrdatabasanslutning](mysql-remote.md).

   Vi rekommenderar att du konfigurerar din databasinstans så att den passar ditt företag. Tänk på följande när du konfigurerar databasen:

   * Indexerare kräver högre `tmp_table_size` och `max_heap_table_size` värden (till exempel 64 M). Om du konfigurerar `batch_size` -parametern kan du justera det värdet tillsammans med tabellstorleksinställningarna för att förbättra indexeringsprestanda. Se [Optimeringsguide](../../../performance/configuration.md) för mer information.

   * Kontrollera att alla indextabeller för MySQL och Adobe Commerce eller Magento Open Source kan sparas i minnet (till exempel konfigurera `innodb_buffer_pool_size`).

   * Omindexering av MariaDB 10.4 tar längre tid jämfört med andra versioner av MariaDB eller MySQL. Se [Bästa praxis för konfiguration](../../../performance/configuration.md#indexers).

1. För MySQL `TIMESTAMP` fält för att följa de inställningar och den komposition som förväntas av programmets deklarativa schemaarkitektur, systemvariabeln `explicit_defaults_for_timestamp` måste anges till `on`.

   Referenser:

   * [MySQL 5.7](https://dev.mysql.com/doc/refman/5.7/en/server-system-variables.html#sysvar_explicit_defaults_for_timestamp)
   * [MariaDB](https://mariadb.com/kb/en/server-system-variables/#explicit_defaults_for_timestamp)

   Om den här inställningen inte är aktiverad `bin/magento setup:db:status` rapporterar alltid att `Declarative Schema is not up to date`.

>[!NOTE]
>
>The `explicit_defaults_for_timestamp` inställningen är inaktuell. Den här inställningen kontrollerar inaktuella TIMESTAMP-beteenden som kommer att tas bort i en framtida MySQL-version. När de beteendena tas bort visas `explicit_defaults_for_timestamp` -inställningen tas också bort.

>[!WARNING]
>
>För Adobe Commerce i molninfrastrukturprojekt finns `explicit_defaults_for_timestamp` inställningen för MySQL (MariaDB) är som standard _AV_.

{{$include /help/_includes/maria-db-config.md}}
