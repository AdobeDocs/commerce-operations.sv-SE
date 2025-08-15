---
title: Sessionslagringsplats
description: Lär dig var sessionsfilerna lagras.
feature: Configuration, Storage
exl-id: 43cab98a-5b68-492e-b891-8db4cc99184e
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '257'
ht-degree: 0%

---

# Sessionslagringsplats

I det här avsnittet beskrivs hur du hittar var dina sessionsfiler lagras. Systemet använder följande logik för att lagra sessionsfiler:

- Om du konfigurerade cachelagrade sessioner lagras de i RAM-minnet. Mer information finns i [Använd cachelagrade för sessionslagring](memcached.md).
- Om du har konfigurerat Redis lagras sessioner på Redis-servern. Mer information finns i [Använd Redis för sessionslagring](../cache/redis-session.md).
- Om du använder standardfilbaserad sessionslagring lagrar vi sessioner på följande platser i den ordning som visas:

   1. Katalogen definierad i [`env.php`](#example-in-envphp)
   1. Katalogen definierad i [`php.ini`](#example-in-phpini)
   1. `<magento_root>/var/session`-katalog

## Exempel i `env.php`

Ett exempelfragment från `<magento_root>/app/etc/env.php` följer:

```php
 'session' => [
     'save' => 'files',
     'save_path' => '/var/www/session'
 ],
```

I föregående exempel lagras sessionsfiler i `/var/www/session`

## Exempel i `php.ini`

Som användare med `root`-behörighet öppnar du `php.ini`-filen och söker efter värdet `session.save_path`. Detta identifierar var sessionerna lagras.

## Hantera sessionsstorlek

Se [Sessionshantering](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/security-session-management) i _Användarhandboken_.

## Konfiguration av skräpinsamling

För att rensa bort utgångna sessioner anropar systemet hanteraren `gc` (_skräpinsamling_) slumpmässigt enligt en sannolikhet som beräknas av direktivet `gc_probability / gc_divisor`. Om du till exempel anger dessa direktiv som `1/100` betyder det att det är troligt att det är `1%` (_sannolikhet för ett anrop av skräpinsamlingen per 100 förfrågningar_).

Skräpinsamlingshanteraren använder direktivet `gc_maxlifetime` - det antal sekunder efter vilket sessionerna betraktas som _skräpinsamlingar_ och eventuellt rensas.

På vissa operativsystem (Debian/Ubuntu) är standarddirektivet `session.gc_probability` `0`, vilket förhindrar att skräpinsamlingshanteraren körs.

Du kan skriva över `session.gc_`-direktiven från filen `php.ini` i filen `<magento_root>/app/etc/env.php`:

```php
 'session' => [
     'save' => 'db',
     'gc_probability' => 1,
     'gc_divisor' => 1000,
     'gc_maxlifetime' => 1440
 ],
```

Konfigurationen varierar beroende på trafiken och de specifika behoven på handlarens webbplats.
