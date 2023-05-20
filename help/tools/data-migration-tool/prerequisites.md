---
title: '''[!DNL Data Migration Tool] krav'
description: Läs vad du behöver göra innan du börjar använda [!DNL Data Migration Tool] att överföra data mellan Magento 1 och Magento 2.
exl-id: 42dfa1ca-41ed-453d-a3e4-41ff36817ca3
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '249'
ht-degree: 0%

---

# [!DNL Data Migration Tool] krav

Kontrollera att följande krav är uppfyllda innan du startar migreringen.

## Magento 2

* Konfigurera ditt Magento 2-system så att det uppfyller [systemkrav](../../installation/system-requirements.md).

   Använd en topologi och design som åtminstone matchar ditt befintliga Magento 1-system.

* [Installera Magento 2](../../installation/overview.md).

## Cron

Starta inte seriejobb för Magento 2.

## Databas

* Efter installation, säkerhetskopiering eller [dump](https://dev.mysql.com/doc/refman/8.0/en/mysqldump.html) din Magento 2-databas så snart som möjligt. Detta gör att du kan återställa det inledande databastillståndet om migreringen inte lyckas.

* Verifiera om [!DNL Data Migration Tool] har nätverksåtkomst för att ansluta till databaserna Magento 1 och Magento 2.

   Öppna portar i brandväggen så att migreringsverktyget kan kommunicera med databaserna.

* Se till att dina MySQL-konton har alla behörigheter som krävs för att komma åt Magento-databaser.

Om binär loggning är aktiverat för din Magento 1-databas anger du den globala [`log_bin_trust_function_creators`](https://dev.mysql.com/doc/refman/5.7/en/server-system-variables.html#sysvar_log_bin_trust_function_creators) MySQL-systemvariabel till `1`eller bevilja [SUPER-privilegium](https://dev.mysql.com/doc/refman/5.7/en/privileges-provided.html#priv_super) till ditt konto.

* Vi rekommenderar inte att du skapar nya enheter (produkter, kategorier och attribut) i din Magento 2-butik före migrering eftersom [!DNL Data Migration Tool] skriver över sådana nya enheter med de gamla från Magento 1.

## Tillägg

Migrera tilläggskoden Magento 1 till Magento 2.

Information om de senaste tilläggen finns på [!DNL [Commerce Marketplace]](https://marketplace.magento.com/) eller kontakta din tilläggsleverantör.

Du kan också använda [!DNL [Code Migration Tool]](https://github.com/magento-commerce/code-migration/blob/develop/README.md).
