---
title: Skapa eller uppdatera distributionskonfigurationen
description: Följ de här stegen för att hantera din distributionskonfiguration för Adobe Commerce eller Magento Open Source.
source-git-commit: f6f438b17478505536351fa20a051d355f5b157a
workflow-type: tm+mt
source-wordcount: '708'
ht-degree: 0%

---


# Skapa eller uppdatera distributionskonfigurationen

Det finns inga krav för att använda det här kommandot.

## Skapa eller uppdatera distributionskonfigurationen

[Distributionskonfiguration](../../configuration/reference/deployment-files.md) innehåller den information som programmet behöver för att initiera och bootstrap.

Du kan använda det här kommandot om:

* Du har redan installerat programmet och du vill ändra distributionskonfigurationen
* Du vill bara skapa distributionskonfigurationen och fortsätta med installationen på något annat sätt
* Uppdatera distributionskonfigurationen utan att påverka något annat

Kommandoalternativ:

```bash
bin/magento setup:config:set [--<parameter>=<value>, ...]
```

I följande tabell beskrivs innebörden av installationsparametrar och -värden.

| Parameter | Värde | Obligatoriskt? |
|--- |--- |--- |
| `--backend-frontname` | Uniform Resource Identifier ([URI](https://www.w3.org/Protocols/rfc2616/rfc2616-sec3.html#sec3.2)) för att komma åt administratören.<br><br>Vi rekommenderar att du inte använder ett vanligt ord som admin, backend. Admin-URI kan innehålla alfanumeriska värden och understreck (`_`). | Nej |
| `--db-host` | Använd något av följande:<br><br>- Databasserverns kvalificerade värdnamn eller IP-adress.<br><br>- `localhost` (standard) eller `127.0.0.1` om databasservern finns på samma värd som webbservern. localhost betyder att MySQL-klientbiblioteket använder UNIX-socketar för att ansluta till databasen. `127.0.0.1` gör att klientbiblioteket använder TCP-protokollet. Mer information om socketar finns i [PHP-SUB_MYSQL-dokumentation](https://www.php.net/manual/en/ref.pdo-mysql.php).<br><br>**Obs!** Du kan också ange databasserverporten i värdnamnet som `www.example.com:9000` | Nej |
| `--db-name` | Namnet på den databasinstans där du vill installera databastabellerna.<br><br>Standard är `magento2`. | Nej |
| `--db-user` | Användarnamn för databasinstansens ägare.<br><br>Standard är `root`. | Nej |
| `--db-password` | Lösenord för databasinstansens ägare. | Nej |
| `--db-prefix` | Använd bara om du installerar databastabellerna i en databasinstans som redan innehåller Adobe Commerce- och Magento Open Source-tabeller.<br><br>I så fall använder du ett prefix för att identifiera tabellerna för den här installationen. Vissa kunder har fler än en Adobe Commerce- eller Magento Open Source-instans som körs på en server med alla tabeller i samma databas.<br><br>Prefixet får innehålla högst fem tecken. Den måste börja med en bokstav och kan bara innehålla bokstäver, siffror och understreck.<br><br>Med det här alternativet kan dessa kunder dela databasservern med mer än en Adobe Commerce- eller Magento Open Source-installation. | Nej |
| `--session-save` | Använd något av följande:<br><br>- `db` för att lagra sessionsdata i [databas](https://developer.adobe.com/commerce/php/development/cache/partial/database-caching/). Välj databaslagring om du har en klustrad databas; i annat fall kanske det inte finns någon större fördel jämfört med filbaserad lagring.<br><br>- `files` för att lagra sessionsdata i filsystemet. Filbaserad sessionslagring är lämplig om inte filsystemåtkomsten är långsam, du har en klustrad databas eller du vill lagra sessionsdata i Redis.<br><br>- `redis` lagra sessionsdata i [Använd Redis för sessionslagring](../../configuration/cache/config-redis.md). Om du använder Redis som standard- eller sidcache-lagring måste Redis vara installerat. | Nej |
| `--key` | Om du har en sådan anger du en nyckel som ska krypteras [känsliga data](#sensitive-data) i databasen. Om du inte har någon skapar programmet en åt dig. | Nej |
| `--db-init-statements` | Avancerad MySQL-konfigurationsparameter. Använder databasinitieringssatser som ska köras vid anslutning till MySQL-databasen.<br><br>Standard är `SET NAMES utf8;`.<br><br>Använd en referens som liknar [den här](https://dev.mysql.com/doc/refman/5.6/en/server-options.html) innan du anger några värden. | Nej |
| `--http-cache-hosts` | Kommaavgränsad lista över gateway-värdar för HTTP-cache som begäranden om rensning ska skickas till. (Till exempel Varnish-servrar.) Använd den här parametern för att ange värden som ska rensas i samma begäran. (Det spelar ingen roll om du bara har en värd eller många värdar.)<br><br>Formatet måste vara `<hostname or ip>:<listen port>`där du kan utesluta `<listen port>` om det är port 80. Exempel, `--http-cache-hosts=192.0.2.100,192.0.2.155:6081`. Separera inte värdar med ett blankstegstecken. | Nej |

## Importera konfigurationsdata

När du konfigurerar ett produktionssystem är det bra att importera konfigurationsinställningar från `config.php` och `env.php` till databasen.
Dessa inställningar omfattar konfigurationssökvägar och -värden, webbplatser, butiker, butiksvyer och teman.

När du har importerat webbplatser, butiker, vyer och teman kan du skapa produktattribut och tillämpa dem på webbplatser, butiker och butiksvyer i produktionssystemet.

Kör följande kommando på produktionssystemet för att importera data från konfigurationsfilerna (`config.php` och `env.php`) till databasen:

```bash
bin/magento app:config:import [-n, --no-interaction]
```

Valfritt `[-n, --no-interaction]` kan kommandot köras utan ytterligare bekräftelser.

Mer information finns i [Importera data från konfigurationsfiler](../../configuration/cli/import-configuration.md)

### Känsliga data

{{$include /help/_includes/sensitive-data.md}}
