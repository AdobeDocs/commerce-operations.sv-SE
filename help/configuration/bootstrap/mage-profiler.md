---
title: Aktivera profilering
description: Läs mer om hur du aktiverar MAGE-profilering för användning med analysverktygen.
exl-id: a46289ed-16dc-4a72-84ff-85fe825dac11
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '410'
ht-degree: 0%

---

# Aktivera profilering

Med Commerce-profilering kan ni

- Aktivera en inbyggd profilerare.

   Du kan använda en inbyggd profilerare med Commerce för att utföra uppgifter som att analysera prestanda. Profileringens karaktär beror på vilka analysverktyg du använder. Vi har stöd för flera format, bland annat HTML. När du aktiverar profileraren `var/profiler.flag` filen genererar som anger att profileraren är aktiverad och konfigurationer. När den är inaktiverad tas den här filen bort.

- Visa beroendediagram på en Commerce-sida.

   A _beroendediagram_ är en lista över objektberoenden och alla deras beroenden, och alla beroenden för dessa beroenden, och så vidare.

   Du bör vara särskilt intresserad av listan över _oanvända beroenden_, som är objekt som skapades eftersom de begärdes i en konstruktor, men som aldrig användes (det vill säga ingen av deras metoder anropades). Därför går processortid och minne som använts för att skapa dessa beroenden förlorade.

Commerce tillhandahåller basfunktionerna i [`Magento\Framework\Profiler`][profiler].

Du kan aktivera och konfigurera profileraren med hjälp av en MAGE_PROFILER-variabel eller kommandoraden.

## Ange MAGE_PROFILER

Du kan ange värdet för `MAGE_PROFILER` på något av de sätt som beskrivs i [Ange värdet för bootstrap-parametrar](../bootstrap/set-parameters.md).

`MAGE_PROFILER` har stöd för följande värden:

- `1` för att aktivera en viss profilerares utdata.

   Du kan använda något av följande värden för att aktivera en specifik profilerare:

   - `csvfile` som använder [`Magento\Framework\Profiler\Driver\Standard\Output\Csvfile`][csvfile]
   - Alla andra värden (utom `2`), inklusive ett tomt värde som använder [`Magento\Framework\Profiler\Driver\Standard\Output\Html`][html]

- `2` för att aktivera beroendediagram.

   Beroendediagram visas vanligtvis längst ned på en sida. I följande bild visas en del av utdata:

   ![Beroendediagram](../../assets/configuration/depend-graphs.png)

## CLI-kommandon

Du kan aktivera eller inaktivera profileraren med CLI-kommandon:

- `dev:profiler:enable <type>` aktiverar profileraren med `type` av `html` (standard) eller `csvfile`. När den är aktiverad, en flaggfil `var/profiler.flag` skapas.
- `dev:profiler:disable` inaktiverar profileraren. När den är inaktiverad visas flaggfilen `var/profiler.flag` tas bort.

Använd variabelalternativet om du vill aktivera beroendediagram.

**Aktivera eller inaktivera profileraren**:

1. Logga in på din Commerce-server.
1. Ändra till installationskatalogen för Commerce.
1. Som ägare av filsystemet aktiverar du profileraren:

   Aktivera profileraren med hjälp av typ `html` och skapa en flaggfil:

   ```bash
   bin/magento dev:profiler:enable html
   ```

   Aktivera profileraren med hjälp av typ `csvfile` och skapa en flaggfil:

   ```bash
   bin/magento dev:profiler:enable csvfile
   ```

   Utdata sparas i `<project-root>/var/log/profiler.csv`. The `profiler.csv` åsidosätts vid uppdatering av varje sida.

   Så här inaktiverar du profileraren och tar bort flaggfilen:

   ```bash
   bin/magento dev:profiler:disable
   ```

<!-- link definitions -->

[csvfile]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Profiler/Driver/Standard/Output/Csvfile.php
[html]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Profiler/Driver/Standard/Output/Html.php
[profiler]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Profiler.php
