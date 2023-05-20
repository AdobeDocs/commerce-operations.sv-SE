---
title: Uppgradera [!DNL Data Migration Tool]
description: Så här uppgraderar du [!DNL Data Migration Tool] att överföra data mellan Magento 1 och Magento 2.
exl-id: c0d56d1d-b15b-437f-be72-74282dbe85c1
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '227'
ht-degree: 0%

---

# Uppgradera [!DNL Data Migration Tool]

För att säkerställa att versionerna av din nuvarande installation av Magento 2 och [!DNL Data Migration Tool] matchar exakt, du kan behöva uppgradera verktyget.

## Förutsättningar

Innan du uppgraderar [!DNL Data Migration Tool]måste du:

* Uppgradera Magento för att få den senaste versionen

* Säkerhetskopiera `vendor/magento/data-migration-tool` katalog

* Se till att [!DNL Data Migration Tool] versionen matchar programversionen för Magento

### Uppgradera Magento

Om du inte redan har gjort det, [uppgradera Magento](../../upgrade/overview.md).

### Säkerhetskopiera `vendor/magento/data-migration-tool` katalog

Innan du uppgraderar [!DNL Data Migration Tool], säkerhetskopiera minst `vendor/magento/data-migration-tool` katalog. Under uppgraderingen kan den tas bort och ersättas av den uppdaterade koden.

Du kan också säkerhetskopiera hela kodbasen och databasen i Magento med följande kommando:

```bash
php <magento_root>/bin/magento setup:backup --code --db
```

>[!WARNING]
>
>The `vendor/magento/data-migration-tool` -katalogen innehåller din egen kod. Om du inte säkerhetskopierar den kan du förlora dina anpassningar under uppgraderingen.


### Se till att versionerna matchar

Versionerna av [!DNL Data Migration Tool] och Magento måste matcha exakt. Magento 2.1.2 kräver till exempel version 2.1.2 av [!DNL Data Migration Tool].

Se [Installera [!DNL Data Migration Tool]](install.md) för att lära dig mer om:

* [Kontrollera](install.md#check-your-version) din Magento 2-version

* [Sök](install.md#find-released-versions-of-data-migration-tool) släppta versioner av [!DNL Data Migration Tool]

* [Kontrollera](install.md#check-version-of-installed-data-migration-tool) den [!DNL Data Migration Tool] version

## Uppgradera [!DNL Data Migration Tool]

1. Logga in på programservern som eller växla till [filsystemets ägare](../../installation/prerequisites/file-system/overview.md).
1. Byt till programmets rotkatalog.
1. Ange följande kommando:

   ```bash
   composer require magento/data-migration-tool:<version>
   ```

   där `<version>` måste matcha versionen av kodbasen Magento 2.

   För version 2.1.2 anger du till exempel:

   ```bash
   composer require magento/data-migration-tool:2.1.2
   ```

1. Vänta medan kommandot slutförs.
