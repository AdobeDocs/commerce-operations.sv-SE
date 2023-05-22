---
title: Konfigurera cachelagrade data för Ubuntu
description: Installera och konfigurera cachelagrade filer på Ubuntu.
feature: Configuration, Cache, Storage
exl-id: 831193d2-3e81-472c-9b87-78a8d52959b4
source-git-commit: af45ac46afffeef5cd613628b2a98864fd7da69b
workflow-type: tm+mt
source-wordcount: '449'
ht-degree: 0%

---

# Konfigurera cachelagrade data för Ubuntu

I det här avsnittet finns anvisningar om hur du installerar som är cachelagrade i Ubuntu.

>[!INFO]
>
>Adobe rekommenderar att du använder den cachelagrade versionen 3.0.5 eller senare.

Eftersom PHP inte har inbyggt stöd för memcache måste du installera ett tillägg för PHP för att kunna använda det. Det finns två PHP-tillägg tillgängliga och det är viktigt att avkoda vilka som ska användas:

- `memcache` (_no d_) - ett äldre men populärt tillägg som inte underhålls regelbundet.
The `memcache` tillägg för närvarande _inte_ arbeta med PHP 7. Se [PHP-dokumentation för memcache](https://www.php.net/manual/en/book.memcache.php).

   Det exakta namnet är `php5-memcache` för Ubuntu.

- `memcached` (_med`d`_) - ett nyare och underhållet tillägg som är kompatibelt med PHP 7. Se [PHP-dokumentation för cachelagrad](https://www.php.net/manual/en/book.memcached.php).

   Det exakta namnet är `php5-memcached` för Ubuntu.

## Installera och konfigurera cachelagrade filer på Ubuntu

**Installera och konfigurera cachelagrade filer på Ubuntu**:

1. Som användare med `root` behörigheter, ange följande kommando:

   ```bash
   apt-get -y update
   ```

   ```bash
   apt-get -y install php5-memcached memcached
   ```

1. Ändra den cachelagrade konfigurationsinställningen för `CACHESIZE` och `-l`:

   1. Öppna `/etc/memcached.conf` i en textredigerare.
   1. Leta reda på `-m` parameter.
   1. Ändra värdet till minst `1GB`
   1. Leta reda på `-l` parameter.
   1. Ändra värdet till `127.0.0.1` eller `localhost`
   1. Spara ändringarna i `memcached.conf` och avsluta textredigeraren.
   1. Omstarten är cachelagrad.

      ```bash
      service memcached restart
      ```

1. Starta om webbservern.

   För Apache `service apache2 restart`

1. Fortsätt med nästa avsnitt.

## Verifiera anslutna arbeten innan du installerar Magento

Adobe rekommenderar att du testar i cache-minnet för att kontrollera att det fungerar innan du installerar Commerce. Det tar bara några minuter och kan förenkla felsökningen senare.

### Verifiera att cachelagrade data känns igen av webbservern

Så här verifierar du att cachelagrade data känns igen av webbservern:

1. Skapa en `phpinfo.php` i webbserverns dokumentrot:

   ```php
   <?php
   // Show all information, defaults to INFO_ALL
   phpinfo();
   ```

1. Gå till den sidan i webbläsaren. Till exempel:

   ```http
   http://192.0.2.1/phpinfo.php
   ```

1. Kontrollera att de anslutna skärmarna är följande:

   ![Bekräfta att cachelagrade data känns igen av webbservern](../../assets/configuration/memcache.png)

   Kontrollera att du använder den cachelagrade versionen 3.0.5 eller senare.

   Om det inte går att visa den anslutna sidan startar du om webbservern och uppdaterar webbläsarsidan. Om den fortfarande inte visas kontrollerar du att du har installerat `php-pecl-memcached` tillägg.

### Verifiera att cachelagrade data kan cachelagra

I det här testet används ett PHP-skript för att verifiera att cachelagrade data kan lagra och hämta cachedata.

Mer information om testet finns i [Installera och använda PMcache i självstudiekursen](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-memcache-on-ubuntu-14-04).

Skapa `cache-test.php` i webbserverns dokument med följande innehåll:

```php
$meminstance = new Memcached();

$meminstance->addServer("<memcached hostname or ip>", <memcached port>);

$result = $meminstance->get("test");

if ($result) {
    echo $result;
} else {
    echo "No matching key found. Refresh the browser to add it!";
    $meminstance->set("test", "Successfully retrieved the data!") or die("Could not save anything to memcached...");
}
```

Plats `<memcached hostname or ip>` är antingen `localhost`, `127.0.0.1`, eller minnesvärdnamnet eller IP-adressen. The `<memcached port>` är avlyssningsport, som standard, `11211`.

Gå till den sidan i en webbläsare. Till exempel

```http
http://192.0.2.1/cache-test.php
```

Första gången du går till sidan visas följande: `No matching key found. Refresh the browser to add it!`

Uppdatera webbläsaren. Meddelandet ändras till `Successfully retrieved the data!`

Slutligen kan du visa minnesknapparna med Telnet:

```bash
telnet localhost <memcache port>
```

Vid uppmaningen skriver du

```shell
stats items
```

Resultatet liknar följande:

```terminal
STAT items:2:number 1
STAT items:2:age 106
STAT items:2:evicted 0
STAT items:2:evicted_nonzero 0
STAT items:2:evicted_time 0
STAT items:2:outofmemory 0
STAT items:2:tailrepairs 0
STAT items:2:reclaimed 0
STAT items:2:expired_unfetched 0
STAT items:2:evicted_unfetched 0
```

Töm det cachelagrade lagringsutrymmet och avsluta Telnet:

```shell
flush_all
```

```shell
quit
```

[Ytterligare information om Telnet-testet](https://darkcoding.net/software/memcached-list-all-keys/)
