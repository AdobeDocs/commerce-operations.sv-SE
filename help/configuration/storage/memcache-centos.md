---
title: Konfigurera cachelagrade i CentOS
description: Lär dig hur du installerar och konfigurerar cachelagrade filer i CentOS för Adobe Commerce-cachning. Instruktioner och optimeringstips.
feature: Configuration, Cache, Storage
exl-id: fc4ad18b-7e99-496e-aebc-1d7640d8716c
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '563'
ht-degree: 0%

---

# Konfigurera cachelagrade i CentOS

I det här avsnittet finns anvisningar om hur du installerar cachelagrade CentOS. Mer information finns i den [cachelagrade wiki](https://github.com/memcached/old-wiki).

>[!INFO]
>
>Adobe rekommenderar att du använder den senaste stabila, cachelagrade versionen (för närvarande 3.1.3 för cachelagrade).

Eftersom PHP inte har inbyggt stöd för memcache måste du installera ett tillägg för PHP för att kunna använda det. Det finns två PHP-tillägg tillgängliga och det är viktigt att avkoda vilka som ska användas:

- `memcache` (_no d_) - ett äldre men populärt tillägg som inte underhålls regelbundet.
Tillägget `memcache` för närvarande _fungerar inte_ med PHP 7. Mer information om memcache[&#x200B; finns i &#x200B;](https://www.php.net/manual/en/book.memcache.php)PHP-dokumentationen.

  Det exakta namnet är `php-pecl-memcache` för CentOS.

- `memcached` (_med en`d`_) - ett nyare och underhållet tillägg som är kompatibelt med PHP 7. Se [PHP-dokumentation för cachelagring](https://www.php.net/manual/en/book.memcached.php).

  Det exakta namnet är `php-pecl-memcached` för CentOS.

## Installera och konfigurera cachelagrade i CentOS

Utför följande uppgifter som en användare med behörighet `root` för att installera som är ansluten till CentOS:

1. Installera cachelagrade filer och dess beroenden:

   ```bash
   yum -y update
   ```

   ```bash
   yum install -y libevent libevent-devel
   ```

   ```bash
   yum install -y memcached
   ```

   ```bash
   yum install -y php-pecl-memcache
   ```

   >[!INFO]
   >
   >Syntaxen för föregående kommandon kan bero på vilka paketdatabaser du använder. Om du t.ex. använder webbstatistik och PHP 5.6 anger du `yum install -y php56w-pecl-memcache`. Använd `yum search memcache|grep php` för att hitta rätt paketnamn.


1. Ändra den cachelagrade konfigurationsinställningen för `CACHESIZE` och `OPTIONS`:

   1. Öppna `/etc/sysconfig/memcached` i en textredigerare.
   1. Leta reda på värdet för `CACHESIZE` och ändra det till minst 1 GB. Exempel:

      ```config
      CACHESIZE="1GB"
      ```

   1. Leta reda på värdet för `OPTIONS` och ändra det till `localhost` eller `127.0.0.1`

1. Spara ändringarna i `memcached` och avsluta textredigeraren.
1. Omstarten är cachelagrad.

   ```bash
   service memcached restart
   ```

1. Starta om webbservern.

   För Apache:

   ```bash
   service httpd restart
   ```

1. Fortsätt med nästa avsnitt.

## Kontrollera att det finns anslutna verk innan du installerar Commerce

Adobe rekommenderar att du testar cachelagrade filer för att kontrollera att de fungerar innan du installerar Commerce. Det tar bara några minuter och kan förenkla felsökningen senare.

### Verifiera att cachelagrade data känns igen av webbservern

Så här verifierar du att cachelagrade data känns igen av webbservern:

1. Skapa en `phpinfo.php`-fil i webbserverns dokumentrot:

   ```php
   <?php
   // Show all information, defaults to INFO_ALL
   phpinfo();
   ```

1. Gå till den sidan i webbläsaren.

   Exempel: `http://192.0.2.1/phpinfo.php`

1. Se till att minnet visas enligt följande:

![Bekräfta memcache känns igen av webbservern](../../assets/configuration/memcache.png)

Kontrollera att du använder den cachelagrade versionen 3.0.5 eller senare.

Om minnet inte visas startar du om webbservern och uppdaterar webbläsarsidan. Om det fortfarande inte visas kontrollerar du att du har installerat tillägget `php-pecl-memcache`.

### Skapa ett memcache-test som består av en MySQL-databas och ett PHP-skript

Testet använder en MySQL-databas, tabell och data för att verifiera att du kan hämta databasdata och lagra dem i memcache. Ett PHP-skript söker först i cachen. Om resultatet inte finns frågar skriptet databasen. När frågan har slutförts av den ursprungliga databasen lagrar skriptet resultatet i memcache med kommandot `set`.

[Mer information om testet](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-memcache-on-ubuntu-12-04)

Skapa MySQL-databasen:

```bash
mysql -u root -p
```

Ange följande kommandon vid `mysql`-prompten:

```sql
create database memcache_test;
GRANT ALL ON memcache_test.* TO memcache_test@localhost IDENTIFIED BY 'memcache_test';
use memcache_test;
create table example (id int, name varchar(30));
insert into example values (1, "new_data");
exit
```

Skapa `cache-test.php` i webbserverns dokumentrot:

```php
$meminstance = new Memcached();

$meminstance->addServer('<memcached hostname or ip>', <memcached port>);

$query = "select id from example where name = 'new_data'";
$querykey = "KEY" . md5($query);

$result = $meminstance->get($querykey);

if (!$result) {
   try {
        $dbh = new PDO('mysql:host=localhost;dbname=memcache_test','memcache_test','memcache_test');
        $dbh->setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION);
        $result = $dbh->query("select id from example where name = 'new_data'")->fetch();
        $meminstance->set($querykey, $result, 0, 600);
        print "got result from mysql\n";
        return 0;
    } catch (PDOException $e) {
        die($e->getMessage());
    }
}
print "got result from memcached\n";
return 0;
```

Där `<memcached hostname or ip>` antingen är `localhost`, `127.0.0.1` eller memcache-värdnamnet eller IP-adressen. `<memcached port>` är avlyssningsporten, som standard `11211`.

Kör skriptet från kommandoraden.

```bash
cd <web server docroot>
```

```bash
php cache-test.php
```

Det första resultatet är `got result from mysql`. Det innebär att nyckeln inte fanns i ett cache-minne, men den hämtades från MySQL.

Det andra resultatet är `got result from memcached`, vilket verifierar att värdet har sparats i cache-minnet.

Slutligen kan du visa minnesknapparna med Telnet:

```bash
telnet localhost <memcache port>
```

Vid uppmaningen skriver du

```bash
stats items
```

Resultatet liknar följande:

```
STAT items:3:number 1
STAT items:3:age 1075
STAT items:3:evicted 0
STAT items:3:evicted_nonzero 0
STAT items:3:evicted_time 0
STAT items:3:outofmemory 0
STAT items:3:tailrepairs 0
```

Töm memcache-lagringen och avsluta Telnet:

```bash
flush_all
```

```bash
quit
```

[Ytterligare information om Telnet-testet](https://darkcoding.net/software/memcached-list-all-keys/)
