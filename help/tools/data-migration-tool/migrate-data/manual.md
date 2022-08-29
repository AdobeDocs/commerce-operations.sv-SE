---
title: Data som kräver manuell migrering
description: 'Lär dig mer om data som måste migreras manuellt under en datamigrering från Magento 1 till Magento 2 och hur du gör det. '
source-git-commit: d609c497fdf00c5e5f975a5679b1d072cec4f8a2
workflow-type: tm+mt
source-wordcount: '302'
ht-degree: 0%

---


# Data som kräver manuell migrering

Det finns fyra typer av data som behöver migreras manuellt:

* Media

* [Storefront](https://glossary.magento.com/storefront) design

* [Administratör](https://glossary.magento.com/admin) användarkonton

* ACL-listor (Access Control Lists)

## Media

I det här avsnittet beskrivs hur du migrerar mediefiler manuellt.

### Mediefiler som lagras i databasen

>[!WARNING]
>
>Databasmedielagringsmetoden används inte i Magento 2.4.3.


Det här avsnittet gäller dig *endast* om du sparar mediefiler i Magento-databasen. Detta steg bör utföras före [migrering av data](data.md):

1. Logga in som administratör på administratörspanelen för Magento 1.

1. Klicka **System** > **Konfiguration** > AVANCERAT > **System**.

1. I den högra rutan bläddrar du till **Lagringskonfiguration för media**.

1. Från **Välj mediedatabas** klickar du på namnet på [medielagring](https://glossary.magento.com/media-storage) databas.

1. Klicka **Synkronisera**.

Upprepa sedan samma steg på administratörspanelen i Magento 2.

### Mediefiler i filsystemet

Alla mediefiler (bilder för produkter, kategorier, [WYSIWYG](https://glossary.magento.com/wysiwyg) (och så vidare) ska kopieras manuellt från `<your Magento 1 install dir>/media` till `<your Magento 2 install dir>/pub/media`.

Men gör *not* kopiera `.htaccess` filer i Magento 1 `media` mapp. Magento 2 har sin egen `.htaccess` som bör bevaras.

## Layout för butiker

* Designa i filer (CSS, JS, mallar, [XML](https://glossary.magento.com/xml) layouter) ändrade plats och format

* [Layout](https://glossary.magento.com/layout) Uppdateringar som lagras i databasen. Placerad via Magento 1 Admin i [CMS](https://glossary.magento.com/cms) Sidor, CMS-widgetar, [Kategori](https://glossary.magento.com/category) Sidor och produktsidor

## ACL-listor (Access Control Lists)

Du måste återskapa alla manuellt:

* autentiseringsuppgifter för webbtjänstens API:er (SOAP, XML-RPC och REST)

* administratörskonton och associera dem med åtkomstbehörighet

>[!NOTE]
>
>Du kan justera tidszonen för en databasenhet med `\Migration\Handler\Timezone` hanterare. Se [uppföljning](follow-up.md) för mer information.
