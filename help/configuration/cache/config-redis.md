---
title: Konfigurera Redis
description: Lär dig hur du konfigurerar Redis-cachning för Adobe Commerce prestandaoptimering. Upptäck de bästa metoderna för funktioner, konfiguration och konfiguration.
feature: Configuration, Cache
exl-id: e037c382-334a-4096-a417-a25fdb61a9ce
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '380'
ht-degree: 0%

---

# Konfigurera Redis

Redis-funktioner:

- PHP-sessionslagring
- Taggbaserad cacherensning utan `foreach`-slingor
- Spara på disk och replikera master/slave

## Installera Redis

Det går inte att installera och konfigurera Redis-programmet i den här guiden. Konsultresurser som:

- [Hämta Redis-sida](https://redis.io/download)
- [Redis-snabbstart](https://redis.io/docs/getting-started/)
- [DigitalOcean](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-redis)
- [Redis-dokumentationssida](https://redis.io/docs)

## Konfigurera Redis

Beroende på installationen kan du oftast hitta din Redis-konfiguration i någon av följande filer: `/etc/redis/redis.conf` eller `/etc/redis/<port>.conf`

För att optimera Redis-instansen efter dina behov får du bäst resultat genom att använda en dedikerad instans för varje session, Commerce cache och FPC.

För sessioner rekommenderar Adobe att du aktiverar beständighet för kopiering av Redis-data till disk med något av följande beständiga alternativ: vanliga ögonblicksbilder av Redis Database Backup (RDB) eller beständiga AOF-beständiga loggar (Append Only File).

- **Redis Database Backup** (RDB)-ögonblicksbilder lagrar hela databasen i en dumpfil efter en given tidpunkt, när ett minsta antal nycklar har ändrats sedan den senaste sparningen. Använd inställningen `save` i filen `redis.conf` för att konfigurera den här inställningen.

- **Lägg till endast fil** (AOF) lagrar varje skrivåtgärd som skickas till Redis i en journalfil. Redis läser endast den här filen vid omstart och använder den för att återställa den ursprungliga datauppsättningen.

Du kan också aktivera både RDB- och AOF-alternativen samtidigt. Mer information, inklusive för- och nackdelar med alternativen för beständighet, finns i [Redis Persistence-dokumentationen](https://redis.io/topics/persistence).

För cacheinstansen ställer du in instansen så att den är tillräckligt stor för att lagra hela Commerce-cachen. Storlekskraven beror på olika faktorer som antalet produkter och butiksvyer. Som utgångspunkt kan du använda storleken på cachemappen i filsystemet. Om mappen `var/cache` i filsystemet till exempel är 5 GB ska Redis-instansen konfigureras med minst 5 GB. Det krävs ingen beständighet för cacheinstansen eftersom Commerce-cachen kan återställas. Se [Redis Cache Guide](https://redis.io/docs/latest/develop/use/).

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
