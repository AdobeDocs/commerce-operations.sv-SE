---
title: Aktivera profilering
description: Läs mer om hur du aktiverar MAGE-profilering för användning med analysverktygen.
exl-id: a46289ed-16dc-4a72-84ff-85fe825dac11
source-git-commit: 6896d31a202957d7354c3dd5eb6459eda426e8d7
workflow-type: tm+mt
source-wordcount: '373'
ht-degree: 0%

---

# Aktivera profilering

Med Commerce profilering kan man

- Aktivera en inbyggd profilerare.

  Du kan använda en inbyggd profilerare med Commerce för att utföra åtgärder som att analysera prestanda. Profileringens karaktär beror på vilka analysverktyg du använder. Vi har stöd för flera format, bland annat HTML. När du aktiverar profileraren genereras en `var/profiler.flag`-fil som anger att profileraren är aktiverad och konfigurationer. När den är inaktiverad tas den här filen bort.

- Visa beroendediagram på en Commerce-sida.

  Ett _beroendediagram_ är en lista över objektberoenden och alla deras beroenden, och alla beroenden för dessa beroenden, och så vidare.

  Du bör vara särskilt intresserad av listan över _oanvända beroenden_, som är objekt som skapades eftersom de begärdes i en konstruktor, men som aldrig användes (det vill säga ingen av deras metoder anropades). Därför går processortid och minne som använts för att skapa dessa beroenden förlorade.

Commerce tillhandahåller basfunktionerna i [`Magento\Framework\Profiler`](https://github.com/magento/magento2/blob/2.4.8/lib/internal/Magento/Framework/Profiler.php).

Du kan aktivera och konfigurera profileraren med hjälp av en MAGE_PROFILER-variabel eller kommandoraden.

## Ange MAGE_PROFILER

Du kan ange värdet för `MAGE_PROFILER` på något av de sätt som beskrivs i [Ange värdet för bootstrap-parametrar](../bootstrap/set-parameters.md).

`MAGE_PROFILER` stöder följande värden:

- `1` om du vill aktivera utdata för en viss profilerare.

  Du kan använda något av följande värden för att aktivera en specifik profilerare:

   - `csvfile` som använder [`Magento\Framework\Profiler\Driver\Standard\Output\Csvfile`](https://github.com/magento/magento2/blob/2.4.8/lib/internal/Magento/Framework/Profiler/Driver/Standard/Output/Csvfile.php)
   - Alla andra värden (utom `2`), inklusive ett tomt värde som använder [`Magento\Framework\Profiler\Driver\Standard\Output\Html`](https://github.com/magento/magento2/blob/2.4.8/lib/internal/Magento/Framework/Profiler/Driver/Standard/Output/Html.php)

- `2` om du vill aktivera beroendediagram.

  Beroendediagram visas vanligtvis längst ned på en sida. I följande bild visas en del av utdata:

  ![Beroendediagram](../../assets/configuration/depend-graphs.png)

## CLI-kommandon

Du kan aktivera eller inaktivera profileraren med CLI-kommandon:

- `dev:profiler:enable <type>` aktiverar profileraren med `type` av `html` (standard) eller `csvfile`. När den är aktiverad skapas en flaggfil `var/profiler.flag`.
- `dev:profiler:disable` inaktiverar profileraren. När flaggfilen `var/profiler.flag` är inaktiverad tas den bort.

Använd variabelalternativet om du vill aktivera beroendediagram.

**Så här aktiverar eller inaktiverar du profileraren**:

1. Logga in på din Commerce-server.
1. Byt till Commerce installationskatalog.
1. Som ägare av filsystemet aktiverar du profileraren:

   Så här aktiverar du profileraren med typen `html` och skapar en flaggfil:

   ```bash
   bin/magento dev:profiler:enable html
   ```

   Så här aktiverar du profileraren med typen `csvfile` och skapar en flaggfil:

   ```bash
   bin/magento dev:profiler:enable csvfile
   ```

   Utdata sparas i `<project-root>/var/log/profiler.csv`. `profiler.csv` åsidosätts vid uppdatering av varje sida.

   Så här inaktiverar du profileraren och tar bort flaggfilen:

   ```bash
   bin/magento dev:profiler:disable
   ```

