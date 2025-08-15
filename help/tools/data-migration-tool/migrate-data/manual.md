---
title: Data som kräver manuell migrering
description: Lär dig mer om data som måste migreras manuellt under en datamigrering från Magento 1 till Magento 2 och hur du gör det.
exl-id: 830abd81-4c6d-418b-9da4-b6acd95f5ec8
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '287'
ht-degree: 0%

---

# Data som kräver manuell migrering

Det finns fyra typer av data som behöver migreras manuellt:

* Media

* Layout för butiker

* Administratörsanvändarkonton

* ACL-listor (Access Control Lists)

## Media

I det här avsnittet beskrivs hur du migrerar mediefiler manuellt.

### Mediefiler som lagras i databasen

>[!WARNING]
>
>Databasens medialagringsmetod används inte i Magento 2.4.3.


Det här avsnittet gäller *endast* om du lagrar mediefiler i Magento-databasen. Det här steget bör utföras före [migrering av data](data.md):

1. Logga in som administratör på Magento 1 Admin Panel.

1. Klicka på **System** > **Konfiguration** > AVANCERAT > **System**.

1. Bläddra till **Lagringskonfiguration för media** i den högra rutan.

1. Klicka på namnet på medielagringsdatabasen i listan **Välj mediedatabas**.

1. Klicka på **Synkronisera**.

Upprepa sedan samma steg på administrationspanelen i Magento 2.

### Mediefiler i filsystemet

Alla mediefiler (bilder för produkter, kategorier, WYSIWYG-redigeraren och så vidare) ska kopieras manuellt från `<your Magento 1 install dir>/media` till `<your Magento 2 install dir>/pub/media`.

Kopiera *inte* filerna `.htaccess` som finns i mappen Magento 1 `media` . Magento 2 har en egen `.htaccess` som ska bevaras.

## Layout för butiker

* Design i filer (CSS, JS, mallar, XML-layouter) ändrade plats och format

* Layoutuppdateringar sparas i databasen. Placerad via Magento 1 Admin på CMS Pages, CMS Widgets, Category Pages och Product Pages

## ACL-listor (Access Control Lists)

Du måste återskapa alla manuellt:

* autentiseringsuppgifter för webbtjänstens API:er (SOAP, XML-RPC och REST)

* administratörskonton och associera dem med åtkomstbehörighet

>[!NOTE]
>
>Du kan justera tidszonen för en databasentitet med hjälp av hanteraren `\Migration\Handler\Timezone`. Mer information finns i avsnittet [uppföljning](follow-up.md).
