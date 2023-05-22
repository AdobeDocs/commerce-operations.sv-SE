---
title: Sessionslagringsplats
description: Lär dig var sessionsfilerna lagras.
feature: Configuration, Storage
exl-id: 43cab98a-5b68-492e-b891-8db4cc99184e
source-git-commit: af45ac46afffeef5cd613628b2a98864fd7da69b
workflow-type: tm+mt
source-wordcount: '260'
ht-degree: 0%

---

# Sessionslagringsplats

I det här avsnittet beskrivs hur du hittar var dina sessionsfiler lagras. Systemet använder följande logik för att lagra sessionsfiler:

- Om du konfigurerade anslutna sessioner lagras sessionerna i RAM-minnet; se [Använd cachelagrat för sessionslagring](memcached.md).
- Om du har konfigurerat Redis lagras sessionerna på Redis-servern; se [Använd Redis för sessionslagring](../cache/redis-session.md).
- Om du använder standardfilbaserad sessionslagring lagrar vi sessioner på följande platser i den ordning som visas:

   1. Katalog definierad i [`env.php`](#example-in-envphp)
   1. Katalog definierad i [`php.ini`](#example-in-phpini)
   1. `<magento_root>/var/session` katalog

## Exempel i `env.php`

Ett exempelfragment från `<magento_root>/app/etc/env.php` följande:

```php
 'session' => [
     'save' => 'files',
     'save_path' => '/var/www/session'
 ],
```

I föregående exempel lagras sessionsfiler i `/var/www/session`

## Exempel i `php.ini`

Som användare med `root` behörighet, öppna `php.ini` fil och sök efter värdet för `session.save_path`. Detta identifierar var sessionerna lagras.

## Hantera sessionsstorlek

Se [Sessionshantering](https://docs.magento.com/user-guide/stores/security-session-management.html) i _Användarhandbok_.

## Konfiguration av skräpinsamling

Om du vill rensa sessioner som gått ut anropar systemet `gc` (_skräpinsamling_)-hanterare slumpmässigt enligt en sannolikhet som beräknas av `gc_probability / gc_divisor` -direktivet. Om du t.ex. anger dessa direktiv som `1/100` det betyder sannolikhet för `1%` (_sannolikhet för ett anrop av skräpinsamling per 100 begäranden_).

Hanteraren för skräpinsamling använder `gc_maxlifetime` direktiv - antalet sekunder som sessionerna ska ses som _skräp_ och kan ha rensats bort.

På vissa operativsystem (Debian/Ubuntu) är standardinställningen `session.gc_probability` direktivet är `0`, vilket förhindrar att skräpinsamlingshanteraren körs.

Du kan skriva över `session.gc_` direktiv från `php.ini` i `<magento_root>/app/etc/env.php` fil:

```php
 'session' => [
     'save' => 'db',
     'gc_probability' => 1,
     'gc_divisor' => 1000,
     'gc_maxlifetime' => 1440
 ],
```

Konfigurationen varierar beroende på trafiken och de specifika behoven på handlarens webbplats.
