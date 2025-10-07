---
title: Anpassat cron-jobb och cron-gruppreferens
description: Lär dig hur du anpassar cron-grupper med cron-flikar i Adobe Commerce. Identifiera anpassad modulkonfiguration och konfiguration av schemalagda aktiviteter.
exl-id: 16e342ff-aa94-4e31-8c75-dfea1ef02706
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '526'
ht-degree: 0%

---

# Anpassa crons-referens

I det här avsnittet får du hjälp med att konfigurera konstanter och (valfritt) kundgrupper för anpassade moduler. Om din anpassade modul behöver schemalägga aktiviteter regelbundet måste du skapa en crontab för den modulen. En _crontab_ är en cron-jobbkonfiguration.

Du kan också konfigurera en anpassad grupp, vilket bland annat gör att du kan köra cron-jobb som definierats i den gruppen oberoende av andra cron-jobb.

En stegvis självstudiekurs finns i [Konfigurera anpassade cron-jobb och cron-grupper (självstudiekurs)](custom-cron-tutorial.md).

En översikt över cron-jobb finns i [Konfigurera cron-jobb](../cli/configure-cron-jobs.md).

## Konfigurera kundgrupper

I det här avsnittet beskrivs hur du kan skapa en cron-grupp för en anpassad modul. Om du inte behöver göra det fortsätter du med nästa avsnitt.

En _cron-grupp_ är en logisk grupp som gör att du enkelt kan köra kron för mer än en process i taget. I de flesta Commerce-moduler används kronigruppen `default`. I vissa moduler används gruppen `index`.

Om du implementerar cron för en anpassad modul kan du välja att använda gruppen `default` eller en annan grupp.

**Så här konfigurerar du en cron-grupp för modulen**:

Skapa en `crontab.xml`-fil i modulkatalogen:

```text
<your component base dir>/<vendorname>/module-<name>/etc/crontab.xml
```

För en grupp bör filen ha följande innehåll:

```xml
<?xml version="1.0"?>
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Cron:etc/crontab.xsd">
    <group id="<group_name>">
        <job name="<job_name>" instance="<classpath>" method="<method>">
            <schedule><time></schedule>
        </job>
    </group>
</config>
```

Var:

| Värde | Beskrivning |
|---|---|
| `group_name` | Namn på cron-gruppen. Gruppnamnet behöver inte vara unikt. Du kan köra cron för en grupp i taget. |
| `job_name` | Unikt ID för det här kronijobbet. |
| `classpath` | Klass som ska instansieras (klassökväg). |
| `method` | Metod i `classpath` att anropa. |
| `time` | Schemalägg i cron-format. Utelämna den här parametern om schemat är definierat i Commerce-databasen eller annan lagring. |

Resultatet `crontab.xml` med två grupper kan se ut så här:

```xml
<?xml version="1.0"?>
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Cron:etc/crontab.xsd">
    <group id="default">
        <job name="<job_1_name>" instance="<classpath>" method="<method_name>">
            <schedule>* * * * *</schedule>
        </job>
        <job name="<job_2_name>" instance="<classpath>" method="<method_name>">
            <schedule>* * * * *</schedule>
        </job>
    </group>
    <group id="index">
        <job name="<job_3_name>" instance="<classpath>" method="<method_name>">
            <schedule>* * * * *</schedule>
        </job>
        <job name="<job_4_name>" instance="<classpath>" method="<method_name>">
            <schedule>* * * * *</schedule>
        </job>
    </group>
</config>
```

Se till exempel [Magento_Customer crontab.xml](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Customer/etc/crontab.xml).

### Ange alternativ för Cron-grupp

Du kan deklarera en ny grupp och ange dess konfigurationsalternativ (som alla körs i butiksvyn) via filen `cron_groups.xml` som finns i:

```text
<your component base dir>/<vendorname>/module-<name>/etc/cron_groups.xml
```

Nedan visas ett exempel på filen `cron_groups.xml`:

```xml
<?xml version="1.0"?>
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Cron:etc/cron_groups.xsd">
    <group id="<group_name>">
        <schedule_generate_every>1</schedule_generate_every>
        <schedule_ahead_for>4</schedule_ahead_for>
        <schedule_lifetime>2</schedule_lifetime>
        <history_cleanup_every>10</history_cleanup_every>
        <history_success_lifetime>60</history_success_lifetime>
        <history_failure_lifetime>600</history_failure_lifetime>
        <use_separate_process>1</use_separate_process>
    </group>
</config>
```

Var:

| Alternativ | Beskrivning |
| -------------------------- | ------------------------------------------------------------------------------------------------------ |
| `schedule_generate_every` | Täthet (i minuter) som scheman skrivs till tabellen `cron_schedule`. |
| `schedule_ahead_for` | Tid (i minuter) i förväg som scheman skrivs till tabellen `cron_schedule`. |
| `schedule_lifetime` | Tidsfönster (i minuter) som ett kron-jobb måste starta eller så betraktas kron-jobbet som missat (&quot;för sent&quot; för att köras). |
| `history_cleanup_every` | Tid (i minuter) som seriehistoriken sparas i databasen. |
| `history_success_lifetime` | Tid (i minuter) som posten för slutförda kronjobb sparas i databasen. |
| `history_failure_lifetime` | Tid (i minuter) som posten för misslyckade kronijobb sparas i databasen. |
| `use_separate_process` | Kör den här cron-gruppens jobb i en separat php-process |

## Inaktivera ett cron-jobb

Kronijobb har inte en `disable`-funktion som vi har för [observatörer](https://developer.adobe.com/commerce/php/development/components/events-and-observers/#observers). Ett cron-jobb kan dock inaktiveras med följande teknik: `schedule` en tid som innehåller ett datum som aldrig kommer att inträffa.

Inaktivera t.ex. cron-jobbet `visitor_clean` som definierats i modulen `Magento_Customer`:

```xml
...
<group id="default">
    <job name="visitor_clean" instance="Magento\Customer\Model\Visitor" method="clean">
        <schedule>0 0 * * *</schedule>
    </job>
</group>
...
```

Om du vill inaktivera cron-jobbet `visitor_clean` skapar du en anpassad modul och skriver om `visitor_clean` cron-jobbet `schedule`:

```xml
...
<group id="default">
    <job name="visitor_clean" instance="Magento\Customer\Model\Visitor" method="clean">
        <schedule>0 0 30 2 *</schedule>
    </job>
</group>
...
```

Nu har kron-jobbet `visitor_clean` ställts in att köras kl. 00:00 den 30 februari - vid ett datum som aldrig inträffar.
