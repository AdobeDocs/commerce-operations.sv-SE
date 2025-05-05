---
title: '[!DNL Data Migration Tool] förutsättningar'
description: Lär dig vad du behöver göra innan du börjar använda  [!DNL Data Migration Tool]  för att överföra data mellan Magento 1 och Magento 2.
exl-id: 42dfa1ca-41ed-453d-a3e4-41ff36817ca3
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '234'
ht-degree: 0%

---

# Krav för [!DNL Data Migration Tool]

Kontrollera att följande krav är uppfyllda innan du startar migreringen.

## Magento 2-systemet

* Konfigurera systemet Magento 2 så att det uppfyller [systemkraven](../../installation/system-requirements.md).

  Använd en topologi och design som åtminstone matchar ditt befintliga Magento 1-system.

* [Installera Magento 2](../../installation/overview.md).

## Cron

Starta inte seriejobb för Magento 2.

## Databas

* Efter installationen bör du säkerhetskopiera eller [dumpa](https://dev.mysql.com/doc/refman/8.0/en/mysqldump.html) din Magento 2-databas så snart som möjligt. Detta gör att du kan återställa det inledande databastillståndet om migreringen inte lyckas.

* Kontrollera om [!DNL Data Migration Tool] har nätverksåtkomst för att ansluta Magento 1- och Magento 2-databaserna.

  Öppna portar i brandväggen så att migreringsverktyget kan kommunicera med databaserna.

* Se till att dina MySQL-konton har alla behörigheter som krävs för att komma åt Magento-databaser.

Om binär loggning är aktiverat för din Magento 1-databas anger du den globala [`log_bin_trust_function_creators`](https://dev.mysql.com/doc/refman/5.7/en/server-system-variables.html#sysvar_log_bin_trust_function_creators) MySQL-systemvariabeln till `1` eller tilldelar [SUPER-privilegiet](https://dev.mysql.com/doc/refman/5.7/en/privileges-provided.html#priv_super) till ditt konto.

* Vi rekommenderar inte att du skapar nya entiteter (produkter, kategorier och attribut) i din Magento 2-butik före migrering eftersom [!DNL Data Migration Tool] skriver över sådana nya entiteter med de gamla från Magento 1.

## Tillägg

Migrera tilläggskoden Magento 1 till Magento 2.

Om du vill hitta de senaste tilläggsversionerna går du till [[!DNL [Commerce Marketplace]]](https://marketplace.magento.com/) eller kontaktar din tilläggsleverantör.

Du kan också använda [[!DNL [Code Migration Tool]]](https://github.com/magento-commerce/code-migration/blob/develop/README.md).
