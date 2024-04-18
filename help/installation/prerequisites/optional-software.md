---
title: Valfri programvara
description: Läs mer om valfri programvara som du kan installera för att få support på lokala installationer av Adobe Commerce.
exl-id: 533ff52b-3301-4624-b691-3dfddde6ce0b
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '597'
ht-degree: 0%

---

# Valfri programvara

Vi rekommenderar starkt att du installerar NTP för att säkerställa att de kroniska uppgifterna utförs korrekt. (Serverdatum kan t.ex. vara tidigare eller framtida.)

De andra valfria verktygen som beskrivs i det här avsnittet kan hjälpa dig med installationen, men de behövs inte för att installera eller använda Adobe Commerce.

## Installera och konfigurera NTP (Network Time Protocol)

[NTP](https://www.ntp.org/) gör att servrar kan synkronisera sina systemklockor med [globalt tillgängliga poolservrar](https://www.ntppool.org/en/). Vi rekommenderar att du använder NTP-servrar som du litar på, oavsett om det är dedikerade maskinvarulösningar i ditt interna nätverk eller externa, offentliga servrar.

Om du distribuerar Adobe Commerce på flera värdar är NTP ett enkelt sätt att säkerställa att alla deras klockor är synkroniserade, oavsett i vilken tidszon servrarna befinner sig. Dessutom beror uppgifter som är relaterade till kron (som indexering och transaktionsmeddelanden) på att serverns klocka är korrekt.

### Installera och konfigurera NTP på Ubuntu

Ange följande kommando för att installera NTP:

```bash
apt-get install ntp
```

Fortsätt med [Använd NTP-poolservrar](#use-ntp-pool-servers).

### Installera och konfigurera NTP i CentOS

Så här installerar och konfigurerar du NTP:

1. Ange följande kommando för att hitta rätt NTP-program:

   ```bash
   yum search ntp
   ```

1. Välj ett paket som ska installeras. Till exempel: `ntp.x86_64`.

1. Installera paketet.

   ```bash
   yum -y install ntp.x86_64
   ```

1. Ange följande kommando så att NTP startar när servern startas.

   ```bash
   chkconfig ntpd on
   ```

1. Fortsätt med nästa avsnitt.

### Använd NTP-poolservrar

Det är upp till dig att välja poolservrar. Om du använder NTP-poolservrar bör du ntp.org [poolservrar](https://www.ntppool.org/en/) som ligger nära serverns tidszon enligt vad som beskrivs på [Projektsida för NTP-pool](https://www.ntppool.org/en/use.html). Om du har en privat NTP-server som är tillgänglig för alla värdar i din distribution kan du använda den servern i stället.

1. Öppna `/etc/ntp.conf` i en textredigerare.

1. Leta efter rader som liknar följande:

   ```conf
   server 0.centos.pool.ntp.org
   server 1.centos.pool.ntp.org
   server 2.centos.pool.ntp.org
   ```

1. Ersätt de raderna eller lägg till ytterligare rader som anger NTP-poolservern eller andra NTP-servrar. Det är en bra idé att ange fler än en.

1. Ett exempel på hur du använder tre USA-baserade NTP-servrar är:

   ```conf
   server 0.us.pool.ntp.org
   server 1.us.pool.ntp.org
   server 2.us.pool.ntp.org
   ```

1. Spara ändringarna i `/etc/ntp.conf` och avsluta textredigeraren.

1. Starta om tjänsten.

   * Ubuntu: `service ntp restart`

   * CentOS: `service ntpd restart`

1. Retur `date` för att kontrollera serverns datum.

   Om datumet är felaktigt kontrollerar du att NTP-klientporten (vanligtvis UDP 123) är öppen i brandväggen.

   Prova `ntpdate _[pool server hostname]_` -kommando. Om det inte fungerar söker du efter felet som returneras.

   Om inget annat fungerar kan du försöka starta om servern.

## Skapa phpinfo.php

The [`phpinfo.php`](https://www.php.net/manual/en/function.phpinfo.php) -filen visar mycket information om PHP och dess tillägg.

>[!NOTE]
>
>Använd `phpinfo.php` i ett utvecklingssystem _endast_. Det kan vara ett säkerhetsproblem i produktionen.

Lägg till följande kod var som helst i webbserverns dokumentmapp:

```php
<?php
// Show all information, defaults to INFO_ALL
phpinfo();
```

Mer information finns i [manuell phpinfo-sida](https://www.php.net/manual/en/function.phpinfo.php).

Om du vill visa resultatet anger du följande URL-adress i webbläsarens plats- eller adressfält:

```http
http://<web server host or IP>/phpinfo.php
```

Om ett 404-fel (Hittades inte) visas kontrollerar du följande:

* Starta webbservern om det behövs.
* Kontrollera att brandväggen tillåter trafik på port 80.

  [Hjälp för Ubuntu](https://help.ubuntu.com/community/UFW)

  [Hjälp för CentOS](https://wiki.centos.org/HowTos%282f%29Network%282f%29IPTables.html)

## phpMyAdmin

Programmet phpMyAdmin är ett lättanvänt, kostnadsfritt databasadministrationsverktyg. Du kan använda den för att kontrollera och ändra innehållet i databasen. Du måste logga in på phpMyAdmin som administrativ användare för MySQL-databasen.

Mer information om phpMyAdmin finns i [phpMyAdmin - startsida](https://www.phpmyadmin.net/).

Mer information om installationen finns i [phpMyAdmin - installationsdokumentation](https://docs.phpmyadmin.net/en/latest/setup.html#quick-install).

>[!NOTE]
>
>Använd phpMyAdmin i ett utvecklingssystem _endast_. Det kan vara ett säkerhetsproblem i produktionen.

1. Om du vill använda phpMyAdmin anger du följande kommando i webbläsarens adress- eller platsfält:

   ```http
   http://<web server host or IP>/phpmyadmin
   ```

1. Logga in med din MySQL-databas när du uppmanas till det `root` eller administratörens användarnamn och lösenord.
