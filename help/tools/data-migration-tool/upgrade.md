---
title: Uppgradera  [!DNL Data Migration Tool]
description: Lär dig hur du uppgraderar  [!DNL Data Migration Tool]  för att överföra data mellan Magento 1 och Magento 2.
exl-id: c0d56d1d-b15b-437f-be72-74282dbe85c1
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '238'
ht-degree: 0%

---

# Uppgradera [!DNL Data Migration Tool]

Om du vill vara säker på att versionerna av din nuvarande Magento 2-installation och [!DNL Data Migration Tool] matchar exakt måste du kanske uppgradera verktyget.

## Förutsättningar

Innan du uppgraderar [!DNL Data Migration Tool] måste du:

* Uppgradera Magento för att få den senaste versionen

* Säkerhetskopiera katalogen `vendor/magento/data-migration-tool`

* Kontrollera att versionen [!DNL Data Migration Tool] matchar programversionen för Magento

### Uppgradera Magento

Om du inte redan har gjort det [uppgraderar du Magento](../../upgrade/overview.md).

### Säkerhetskopiera katalogen `vendor/magento/data-migration-tool`

Innan du uppgraderar [!DNL Data Migration Tool] bör du säkerhetskopiera åtminstone katalogen `vendor/magento/data-migration-tool`. Under uppgraderingen kan den tas bort och ersättas av den uppdaterade koden.

Du kan också säkerhetskopiera hela kodbasen och databasen i Magento med följande kommando:

```bash
php <magento_root>/bin/magento setup:backup --code --db
```

>[!WARNING]
>
>Katalogen `vendor/magento/data-migration-tool` innehåller din anpassade kod. Om du inte säkerhetskopierar den kan du förlora dina anpassningar under uppgraderingen.


### Se till att versionerna matchar

Versionerna för [!DNL Data Migration Tool] och programvaran för Magento måste matcha exakt. Magento 2.1.2 kräver till exempel version 2.1.2 av [!DNL Data Migration Tool].

Läs avsnittet [Installera [!DNL Data Migration Tool]](install.md) om du vill veta mer om:

* [Kontrollera](install.md#check-your-version) din version av Magento 2

* [Sök](install.md#find-released-versions-of-data-migration-tool) släppta versioner av [!DNL Data Migration Tool]

* [Kontrollera](install.md#check-version-of-installed-data-migration-tool) versionen [!DNL Data Migration Tool]

## Uppgradera [!DNL Data Migration Tool]

1. Logga in på programservern som, eller växla till, [ägaren av filsystemet](../../installation/prerequisites/file-system/overview.md).
1. Byt till programmets rotkatalog.
1. Ange följande kommando:

   ```bash
   composer require magento/data-migration-tool:<version>
   ```

   där `<version>` måste matcha versionen av kodbasen Magento 2.

   För version 2.1.2 anger du:

   ```bash
   composer require magento/data-migration-tool:2.1.2
   ```

1. Vänta medan kommandot slutförs.
