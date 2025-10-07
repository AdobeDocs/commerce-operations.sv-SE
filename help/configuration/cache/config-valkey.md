---
title: Konfigurera Valkey
description: Lär dig hur du konfigurerar Valkey-cachning för prestandaoptimering i Adobe Commerce. Upptäck de bästa metoderna för funktioner, konfiguration och konfiguration.
feature: Configuration, Cache
exl-id: 12dbc171-3df6-4413-869b-a3450b5647b4
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 0%

---

# Konfigurera Valkey

Viktiga funktioner:

- PHP-sessionslagring
- Taggbaserad cacherensning utan `foreach`-slingor
- Spara på disk och replikera master/slave

## Install Valkey

Information om hur du installerar och konfigurerar Valkey-programmet finns i följande resurser:

- [Hämta Valkey-sida](https://valkey.io/download/)
- [Nyckelsnabbstart](https://valkey.io/topics/quickstart/)
- [Valkey-dokumentationssida](https://valkey.io/docs)

## Konfigurera Valkey-konfiguration

Beroende på installationen kan du vanligtvis hitta din Valkey-konfiguration i antingen filen `/etc/valkey/valkey.conf` eller filen `/etc/valkey/<port>.conf`.

För att optimera Valkey-instansen efter dina behov kan du få bästa resultat genom att använda en dedikerad instans för varje session, Commerce-cache och FPC.

Adobe rekommenderar att du aktiverar beständighet för sessioner så att Valkey-data kopieras till disk. Du kan använda antingen RDB-ögonblicksbilder (Valkey Database Backup) eller AOF-beständiga loggar (Append Only File).

- **RDB** (Valkey Database)-ögonblicksbilder lagrar hela databasen i en dumpfil efter en given tidpunkt, när ett minsta antal nycklar har ändrats sedan den senaste sparningen. Använd inställningen `save` i filen `valkey.conf` för att konfigurera den här inställningen.

- **Lägg till endast fil** (AOF) lagrar varje skrivåtgärd som skickas till Valkey i en journalfil. Valkey läser endast den här filen vid omstart och använder den för att återställa den ursprungliga datauppsättningen.

Du kan också aktivera både RDB- och AOF-alternativen samtidigt. Mer information, bland annat för- och nackdelar med beständighetsalternativen, finns i [dokumentationen för Valkey Persistence](https://valkey.io/topics/persistence/).

För cacheinstansen ställer du in instansen så att den är tillräckligt stor för att lagra hela Commerce-cachen. Storlekskraven beror på olika faktorer som antalet produkter och butiksvyer. Som utgångspunkt kan du använda storleken på cachemappen i filsystemet. Om mappen `var/cache` i filsystemet till exempel är 5 GB ska du konfigurera din Valkey-instans med minst 5 GB så att den startar. Det krävs ingen beständighet för cacheinstansen eftersom Commerce-cachen kan återställas.

För prestandajustering kan du aktivera följande inställningar för asynkron borttagning. De här inställningarna ändrar inte Valkeys beteende.

```ini
lazyfree-lazy-eviction yes
lazyfree-lazy-expire yes
lazyfree-lazy-server-del yes
replica-lazy-flush yes
lazyfree-lazy-user-del yes
```
