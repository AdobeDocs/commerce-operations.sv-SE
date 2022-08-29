---
title: Uppgradera [!DNL Data Migration Tool]
description: Så här uppgraderar du [!DNL Data Migration Tool] att överföra data mellan Magento 1 och Magento 2.
source-git-commit: b5a2c362b09de993e1dc196bdda90e74cf4a8ba2
workflow-type: tm+mt
source-wordcount: '239'
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

Om du inte redan har gjort det, [uppgradera Magento](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/overview.html).

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

1. Logga in på Magento-servern som eller växla till [filsystemets ägare](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-sys-perms-over.html).
1. Byt till rotkatalog för Magento 2.
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
