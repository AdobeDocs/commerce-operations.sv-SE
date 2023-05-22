---
title: Konfigurera Redis
description: Få en översikt över Redis-funktioner och starta konfigurationen av Redis.
feature: Configuration, Cache
exl-id: e037c382-334a-4096-a417-a25fdb61a9ce
source-git-commit: a2bd4139aac1044e7e5ca8fcf2114b7f7e9e9b68
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 0%

---

# Konfigurera Redis

Redis-funktioner:

- PHP-sessionslagring
- Taggbaserad cacherensning utan `foreach` slingor
- Spara på disk och överordnad-/slavreplikering

## Installera Redis

Det går inte att installera och konfigurera Redis-programmet i den här guiden. Konsultresurser som:

- [Ladda ned Redis-sida](https://redis.io/download)
- [Redis snabbstart](https://redis.io/docs/getting-started/)
- [DigitalOcean](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-redis)
- [Dokumentationssida för Redis](https://redis.io/docs)

## Konfigurera Redis

Beroende på installationen kan du oftast hitta din Redis-konfiguration i någon av följande filer: `/etc/redis/redis.conf` eller `/etc/redis/<port>.conf`

För att optimera Redis-instansen efter dina behov får du bäst resultat genom att använda en dedikerad instans för varje session, Commerce Cache och FPC.

För sessioner rekommenderar Adobe att du aktiverar beständighet för kopiering av Redis-data till disken med något av följande beständiga alternativ: regelbundna RDB-ögonblicksbilder (Redis Database Backup) eller AOF-beständiga loggar (Append Only File).

- **Säkerhetskopiering av Redis-databas** (RDB) ögonblicksbilder lagrar hela databasen i en dumpfil efter en viss tid, när ett minsta antal nycklar har ändrats sedan den senaste sparningen. Använd `save` -inställningen inuti `redis.conf` fil för att konfigurera den här inställningen.

- **Lägg endast till fil** (AOF) lagrar varje skrivåtgärd som skickas till Redis i en journalfil. Redis läser endast den här filen vid omstart och använder den för att återställa den ursprungliga datauppsättningen.

Du kan också aktivera både RDB- och AOF-alternativen samtidigt. Mer information, som för- och nackdelar med alternativen för beständighet, finns i [Redis Persistence-dokumentation](https://redis.io/topics/persistence).

För cacheinstansen ställer du in instansen så att den är tillräckligt stor för att lagra hela Commerce-cachen. Storlekskraven beror på olika faktorer som antalet produkter och butiksvyer. Som utgångspunkt kan du använda storleken på cachemappen i filsystemet. Om `var/cache` -mappen i filsystemet är 5 GB. Konfigurera Redis-instansen med minst 5 GB för att starta. Det krävs ingen beständighet för cacheinstansen eftersom Commerce-cachen kan återställas. Se [Redis Cache Guide](https://redis.io/docs/manual/eviction/).

För prestandajustering kan du aktivera följande inställningar för asynkron borttagning. De här inställningarna ändrar inte Redis beteende.

```ini
lazyfree-lazy-eviction yes
lazyfree-lazy-expire yes
lazyfree-lazy-server-del yes
replica-lazy-flush yes
```

I Redis 6.x och senare kan du även lägga till följande värde:

```ini
lazyfree-lazy-user-del yes
```
