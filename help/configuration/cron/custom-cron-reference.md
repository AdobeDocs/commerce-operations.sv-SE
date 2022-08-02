---
title: Anpassat cron-jobb och cron-gruppreferens
description: Lär dig att anpassa kroner med hjälp av cron-grupper.
source-git-commit: ee2e446edf79efcd7cbbd67248f8e7ece06bfefd
workflow-type: tm+mt
source-wordcount: '535'
ht-degree: 0%

---


# Anpassa crons-referens

I det här avsnittet får du hjälp med att konfigurera konstanter och (valfritt) kundgrupper för anpassade moduler. Om din egen [modul](https://glossary.magento.com/module) måste schemalägga aktiviteter regelbundet, du måste skapa en crontab för den modulen. A _crontab_ är en konfiguration för cron-jobb.

Du kan också konfigurera en anpassad grupp, vilket bland annat gör att du kan köra cron-jobb som definierats i den gruppen oberoende av andra cron-jobb.

En stegvis självstudiekurs finns på [Konfigurera anpassade cron-jobb och cron-grupper (självstudiekurs)](custom-cron-tutorial.md).

En översikt över kronjobb finns i [Konfigurera cron-jobb](../cli/configure-cron-jobs.md).

## Konfigurera kundgrupper

I det här avsnittet beskrivs hur du kan skapa en cron-grupp för en anpassad modul. Om du inte behöver göra det fortsätter du med nästa avsnitt.

A _kreditgrupp_ är en logisk grupp som gör att du enkelt kan köra cron i mer än en process i taget. De flesta Commerce-moduler använder `default` kreditgrupp, vissa moduler använder `index` grupp.

Om du implementerar kron för en anpassad modul kan du välja att använda `default` eller en annan grupp.

**Konfigurera en cron-grupp för modulen**:

Skapa en `crontab.xml` i modulkatalogen:

```text
<your component base dir>/<vendorname>/module-<name>/etc/crontab.xml
```

För en grupp bör filen ha följande innehåll:

```xml
<config>
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
| `method` | Metod in `classpath` att ringa. |
| `time` | Schemalägg i cron-format. Utelämna den här parametern om schemat har definierats i Commerce-databasen eller annan lagring. |

Resultatet `crontab.xml` med två grupper kan se ut så här:

```xml
<config>
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

Ett exempel finns i [Magento_Customer crontab.xml](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Customer/etc/crontab.xml).

### Ange alternativ för Cron-grupp

Du kan deklarera en ny grupp och ange dess konfigurationsalternativ (som alla körs i [butiksvy](https://glossary.magento.com/store-view) omfång) via `cron_groups.xml` -fil, som finns i:

```text
<your component base dir>/<vendorname>/module-<name>/etc/cron_groups.xml
```

Nedan visas ett exempel på `cron_groups.xml` fil:

```xml
<config>
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
| `schedule_generate_every` | Täthet (i minuter) som scheman skrivs till `cron_schedule` tabell. |
| `schedule_ahead_for` | Tid (i minuter) i förväg som tidsplanerna skrivs till `cron_schedule` tabell. |
| `schedule_lifetime` | Tidsfönster (i minuter) som ett kron-jobb måste starta eller så betraktas kron-jobbet som missat (&quot;för sent&quot; för att köras). |
| `history_cleanup_every` | Tid (i minuter) som kronithistoriken sparas i databasen. |
| `history_success_lifetime` | Tid (i minuter) som posten för slutförda kronijobb sparas i databasen. |
| `history_failure_lifetime` | Tid (i minuter) som posten för misslyckade kronijobb sparas i databasen. |
| `use_separate_process` | Kör den här cron-gruppens jobb i en separat php-process |

## Inaktivera ett cron-jobb

Kronijobb har ingen `disable` som vi har för [observatörer](https://developer.adobe.com/commerce/php/development/components/events-and-observers/#observers). Ett cron-jobb kan dock inaktiveras med följande teknik: `schedule` en tid som innehåller ett datum som aldrig kommer att inträffa.

Du kan till exempel inaktivera `visitor_clean` cron-jobb som definieras i `Magento_Customer` modul:

```xml
...
<group id="default">
    <job name="visitor_clean" instance="Magento\Customer\Model\Visitor" method="clean">
        <schedule>0 0 * * *</schedule>
    </job>
</group>
...
```

Så här inaktiverar du `visitor_clean` cron-jobb, skapa en anpassad modul och skriva om `visitor_clean` cron `schedule`:

```xml
...
<group id="default">
    <job name="visitor_clean" instance="Magento\Customer\Model\Visitor" method="clean">
        <schedule>0 0 30 2 *</schedule>
    </job>
</group>
...
```

Nu `visitor_clean` cron-jobbet är inställt på att köras kl. 00:00 den 30 februari - det datum som aldrig inträffar.
