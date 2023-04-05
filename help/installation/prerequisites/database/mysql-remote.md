---
title: Konfigurera en MySQL-fjärrdatabasanslutning
description: Följ de här stegen för att konfigurera en fjärrdatabasanslutning för lokala installationer av Adobe Commerce och Magento Open Source.
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '743'
ht-degree: 0%

---


# Konfigurera en MySQL-fjärrdatabasanslutning

Ibland kanske du vill lagra databasen på en separat server i stället för att köra databasservern och webbservern på samma dator.

Adobe har tillhandahållit ett sätt att ansluta till en MySQL-server på en annan dator. Från och med Adobe Commerce och Magento Open Source 2.4.3 kan du även konfigurera programmet så att det använder en Amazon Web Services (AWS) Aurora-databas utan kodändringar.

Aurora är en högpresterande, helt kompatibel MySQL-server som finns på AWS.

## Ansluta till en AWS Aurora-databas

Att använda Aurora som databas är lika enkelt som att ange databasen i den vanliga konfigurationskonfigurationen för Adobe Commerce och Magento Open Source med hjälp av standarddatabaskopplingen.

Vid körning `bin/magento setup:install`använder du Aurora-informationen i `db-` fält:

```bash
bin/magento setup:install ... --db-host='database-aurora.us-east-1.rds.amazonaws.com' --db-name='magento2' --db-user='username' --db-password='password' ...
```

The `db-host` värdet är Aurora-URL:en med `https://` och efterföljande `:portnumber`  borttagen.

## Konfigurera en fjärrdatabasanslutning

>[!NOTE]
>
>Det här är ett avancerat ämne som endast bör användas av en erfaren nätverksadministratör eller databasadministratör. Du måste ha `root` åtkomst till filsystemet och du måste kunna logga in på MySQL som `root`.

### Förutsättningar

Innan du börjar måste du:

* [Installera MySQL-server](mysql.md) på databasservern.
* [Skapa en databasinstans](mysql.md#configuring-the-database-instance) på databasservern.
* Installera MySQL-klienten på Adobe Commerce- eller Magento Open Source-webbnoden. Mer information finns i MySQL-dokumentationen.

### Hög tillgänglighet

Använd följande riktlinjer om du vill konfigurera fjärrdatabasanslutningar om webbservern eller databasservern är klustrad:

* Du måste konfigurera en anslutning för varje webbservernod.
* Vanligtvis konfigurerar du en databasanslutning till databasens belastningsutjämnare; Men databasklustring kan vara komplicerad och det är upp till dig att konfigurera den. Adobe ger inga specifika rekommendationer för databasklustring.

   Mer information finns i [MySQL-dokumentation](https://dev.mysql.com/doc/refman/5.6/en/mysql-cluster.html).

### Löser anslutningsproblem

Om du har problem med att ansluta till någon av värdarna måste du först pinga den andra värddatorn för att se till att den är tillgänglig. Du kan behöva tillåta anslutningar från en värd till en annan genom att ändra brandväggs- och SELinux-reglerna (om du använder SELinux).

## Skapa fjärranslutningen

Så här skapar du en fjärranslutning:

1. På databasservern, som en användare med `root` behörighet, öppna MySQL-konfigurationsfilen.

   Om du vill hitta den anger du följande kommando:

   ```bash
   mysql --help
   ```

   Platsen ser ut ungefär så här:

   ```terminal
   Default options are read from the following files in the given order:
   /etc/my.cnf /etc/mysql/my.cnf /usr/etc/my.cnf ~/.my.cnf
   ```

   >[!NOTE]
   >
   >På Ubuntu 16 är sökvägen vanligtvis `/etc/mysql/mysql.conf.d/mysqld.cnf`.

1. Sök i konfigurationsfilen efter `bind-address`.

   Om den finns ändrar du värdet enligt följande.

   Om den inte finns lägger du till den i `[mysqld]` -avsnitt.

   ```conf
   bind-address = <ip address of your web node>
   ```

   Se [MySQL-dokumentation](https://dev.mysql.com/doc/refman/5.6/en/server-options.html), särskilt om du har en klustrad webbserver.

1. Spara ändringarna i konfigurationsfilen och avsluta textredigeraren.
1. Starta om MySQL-tjänsten:

   * CentOS: `service mysqld restart`

   * Ubuntu: `service mysql restart`
   >[!NOTE]
   >
   >Om MySQL inte kan startas söker du efter källan till problemet i syslog. Lös problemet med hjälp av [MySQL-dokumentation](https://dev.mysql.com/doc/refman/5.6/en/server-options.html#option_mysqld_bind-address) eller någon annan auktoritativ källa.

## Bevilja åtkomst för en databasanvändare

Om du vill att webbnoden ska kunna ansluta till databasservern måste du ge en användare i en webbnoddatabas åtkomst till databasen på fjärrservern.

I det här exemplet tilldelas `root` databasanvändaren har fullständig åtkomst till databasen på fjärrvärden.

Så här beviljar du åtkomst till en databasanvändare:

1. Logga in på databasservern.
1. Anslut till MySQL-databasen som `root` användare.
1. Ange följande kommando:

   ```shell
   GRANT ALL ON <local database name>.* TO <remote web node username>@<remote web node server ip address> IDENTIFIED BY '<database user password>';
   ```

   Till exempel:

   ```shell
   GRANT ALL ON magento_remote.* TO dbuser@192.0.2.50 IDENTIFIED BY 'dbuserpassword';
   ```

   >[!NOTE]
   >
   >Om webbservern är grupperad anger du samma kommando på alla webbservrar. Du måste använda samma användarnamn för alla webbservrar.

## Verifiera databasåtkomst

På webbnodvärden anger du följande kommando för att verifiera att anslutningen fungerar:

```bash
mysql -u <local database username> -h <database server ip address> -p
```

Om MySQL-skärmen visas enligt följande är databasen klar för Adobe Commerce eller Magento Open Source:

```terminal
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 213 Server version: 5.6.26 MySQL Community Server (GPL)

Copyright (c) 2000, 2015, Oracle and/or its affiliates. All rights reserved.

Oracle is a registered trademark of Oracle Corporation and/or its affiliates. Other names may be trademarks of their respective owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.
```

Om webbservern är klustrad anger du kommandot på varje webbservervärd.

## Installera Adobe Commerce eller Magento Open Source

När du installerar Adobe Commerce eller Magento Open Source måste du ange följande:

* Bas-URL (kallas även *butiksadress*) anger värdnamnet eller IP-adressen för *webbnod*
* Databasvärden är *fjärrdatabasserver* IP-adress (eller belastningsutjämnare om databasservern är klustrad)
* Databasens användarnamn är *lokal webbnod* databasanvändare som du gav åtkomst till
* Databaslösenordet är den lokala webbnodens användarlösenord
* Databasnamnet är namnet på databasen på fjärrservern
