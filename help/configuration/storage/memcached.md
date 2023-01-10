---
title: Använd cachelagrat för sessionslagring
description: Lär dig hur du använder cachelagrade data för Commerce-sessionslagring.
source-git-commit: 0d106b36f479ecf2eda3fecf6740b28d4b6793eb
workflow-type: tm+mt
source-wordcount: '285'
ht-degree: 0%

---


# Använd cachelagrat för sessionslagring

Minnescache är ett allmänt, distribuerat minnescachningssystem. Den används ofta för att snabba upp dynamiska databasdrivna webbplatser genom att data och objekt cachelagras i RAM för att minska det antal gånger som en extern datakälla (som en databas eller API) måste läsas.

Memcache-lagrade tillhandahåller en stor hashtabell som kan distribueras på flera datorer. När tabellen är full gör efterföljande infogningar att äldre data rensas i LRU-ordning (minimum recently used). Storleken på den här hashtabellen är ofta mycket stor. (Källa: [memcached.org](https://www.memcached.org/))

I Commerce används cachelagrade data för sessionslagring, men inte för sidcachelagring. Vi rekommenderar cachning av sidor [Redis](../cache/redis-pg-cache.md) eller [Varnish](../cache/config-varnish.md).

**Så här konfigurerar du Commerce att använda cachelagrade**:

1. Öppna `<your install dir>/app/etc/env.php` i en textredigerare.
1. Gå till följande:

   ```php
   'session' =>
       array (
       'save' => 'files',
   ),
   ```

1. Ändra den enligt följande:

   ```php
   'session' =>
       array (
         'save' => 'memcached',
         'save_path' => '<memcache ip or host>:<memcache port>'
   ),
   ```

   i cache-minnet har valfria startparametrar som ligger utanför den här guidens omfång. Mer information om dem finns i [memcache](https://www.php.net/manual/en/memcached.sessions.php) dokumentation, källkod och ändringshundar.

1. Fortsätt med nästa avsnitt.

**Verifiera cachelagrade arbeten med Commerce**:

1. Ta bort innehållet i följande kataloger under din Commerce-installationskatalog:

   ```bash
   rm -rf var/cache/* var/page_cache/* var/session/*
   ```

1. Gå till valfri sida i butiken.

1. Logga in på Admin och bläddra till flera sidor.

   Om inga fel visas, grattis! fungerar! Du kan också titta på den cachelagrade lagringen enligt beskrivningen i nästa steg.

   Om fel visas (till exempel HTTP 500 (Internt serverfel)) aktiverar du utvecklarläget och diagnostiserar problemet. Kontrollera att den anslutna cachen körs, är korrekt konfigurerad och att `env.php` har inga syntaxfel.

1. (Valfritt.) Använd Telnet för att titta på det inspelade lagringsutrymmet.

   ```bash
   telnet <memcached host or ip> <memcached port>
   ```

   ```bash
   stats items
   ```

   Resultaten visas på ungefär följande sätt:

   ```terminal
   STAT items:3:number 1
   STAT items:3:age 7714
   STAT items:3:evicted 0
   STAT items:3:evicted_nonzero 0
   STAT items:3:evicted_time 0
   STAT items:3:outofmemory 0
   STAT items:3:tailrepairs 0
   
   [Look at the keys in more detail](https://darkcoding.net/software/memcached-list-all-keys/)
   ```
