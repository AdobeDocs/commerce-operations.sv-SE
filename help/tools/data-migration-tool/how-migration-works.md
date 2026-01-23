---
title: Så fungerar datamigrering
description: Läs om datamigreringsprocessen mellan Magento 1 och Magento 2, inklusive terminologi, arbetsflödesdiagram och steg.
exl-id: 821492dc-ee5b-4c4a-9479-680ee8c5756d
topic: Commerce, Migration
source-git-commit: 6896d31a202957d7354c3dd5eb6459eda426e8d7
workflow-type: tm+mt
source-wordcount: '781'
ht-degree: 0%

---

# Så fungerar datamigrering

Det här avsnittet innehåller en översikt på hög nivå över hur data migreras från Magento 1 till Magento 2 med [!DNL Data Migration Tool].

[!DNL Data Migration Tool] är ett kommandoradsverktyg (CLI) som används för att överföra data från Magento 1 till Magento 2. Verktyget verifierar konsekvensen mellan databasstrukturer i Magento 1 och 2 (tabeller och fält), spårar dataöverföringsförloppet, skapar loggar och kör dataverifieringstester.

## Terminologi

* **Lägen** - en ordnad uppsättning åtgärder för att migrera data från Magento 1.x till Magento 2.x.
* **Steg** - aktiviteterna i ett läge som definierar vilken typ av data som ska migreras.
* **Steg** - de uppgifter i steg som validerar, överför och verifierar data.
* **Mappa filer** - XML-filer som definierar regler och anslutningar mellan datastrukturerna Magento 1.x och Magento 2.x för att slutföra faserna.

## Lägen

[!DNL Data Migration Tool] delar upp migreringsprocessen i tre faser eller *lägen* för att överföra och anpassa data från Magento 1.x till Magento 2.x. De tre lägena visas här och måste köras i följande ordning:

1. **Inställningsläge**: migrerar systemkonfigurationen och webbplatsrelaterade inställningar.
1. **Dataläge**: migrerar databasresurser i grupp.
1. **Deltaläge**: migrerar inkrementella ändringar (ändringar sedan den senaste körningen), till exempel nya kunder och beställningar.

![Migreringslägen](../../assets/data-migration/MigrationModes2.png)

## Steg

[!DNL Data Migration Tool] använder en lista med *steg* i varje läge för att migrera en viss typ av data. I inställningsläget används till exempel två steg för att migrera alla inställningsdata: steget Lagrar och steget Inställningar. Information om de specifika data som migreras i vart och ett av dessa steg (och för steg i andra lägen) finns i [[!DNL Data Migration Tool] den tekniska specifikationen](technical-specification.md).

![Migreringsöversikt](../../assets/data-migration/MigrationOverview2.png)

## Steg

Inom varje steg finns tre *faser* som alltid körs i den här ordningen för att säkerställa att data migreras korrekt:

1. **Integritetskontroll**: Jämför tabellfältsnamn, -typer och annan information för att verifiera kompatibiliteten mellan datastrukturerna Magento 1 och 2.
1. **Dataöverföring**: Överför datatabellen per tabell från Magento 1 och 2.
1. **Volymkontroll**: Jämför antalet poster mellan tabeller för att verifiera att överföringen lyckades.

![Migreringsfaser](../../assets/data-migration/MigrationSteps2.png)

## Mappa filer

Vid den lägsta nivån av migreringsprocesserna finns XML-mappningsfilerna *1.* [!DNL Data Migration Tool] använder kartfiler i steg om du vill omforma olika datastrukturer mellan Magento 1.x- och 2.x-tabellerna.

När du till exempel transformerar data från en Magento Open Source 1.8.0.0-databas till Magento Open Source 2.x.x, tar kartfilen hänsyn till att en tabell har fått ett nytt namn och byter namn på den i måldatabasen. Om det inte finns några skillnader i datastruktur eller dataformat överför [!DNL Data Migration Tool] den i befintligt skick, inklusive data från tabeller som skapats av tillägg, till Magento 2-databasen.

Om skillnader inte har deklarerats i mappningsfiler visas ett fel i [!DNL Data Migration Tool] och den startar inte.

Mappningsfiler beskrivs mer ingående i [[!DNL Data Migration Tool] Technical Specification].

## Flyttningsflödesdiagram

![Migreringsflöde](../../assets/data-migration/migration_flow.png)

[[!DNL Data Migration Tool] teknisk specifikation](technical-specification.md)

Vi är glada över att du funderar på att gå över från världens främsta e-handelsplattform - Magento 1.x - till framtidens plattform, Magento 2. Vi är glada att kunna dela med oss av detaljerna om den här processen, som vi kallar migrering.

## Migreringskomponenter

Magento 2-migrering omfattar fyra komponenter: data, tillägg och anpassad kod, teman och anpassningar.

### Data

Vi har utvecklat **Magento 2[!DNL Data Migration Tool]** som hjälper dig att effektivt flytta alla dina produkter, kunder och beställningsdata, butikskonfigurationer, kampanjer med mera till Magento 2. Den här handboken innehåller information om verktyget och de bästa sätten att använda det för att migrera data.

### Tillägg och anpassad kod

Vi har arbetat hårt med utvecklingscommunityn för att hjälpa dig använda dina Magento 1-tillägg i Magento 2. Nu kan vi presentera [Commerce Marketplace](https://commercemarketplace.adobe.com//), där du kan hämta eller köpa de senaste versionerna av dina favorittillägg.

Mer information om hur du utvecklar tillägg för Magento 2 finns i [PHP Developer Guide](https://developer.adobe.com/commerce/php/development/).

### Teman och anpassningar

Magento 2 använder nya metoder och tekniker som ger handlarna oöverträffade möjligheter att skapa innovativa shoppingupplevelser och anpassa sig till nya nivåer. För att kunna utnyttja dessa framsteg måste utvecklarna göra ändringar i sina teman och anpassningar. Dokumentation finns online för att skapa Magento 2 [teman](https://developer.adobe.com/commerce/frontend-core/guide/themes/), [layouter](https://developer.adobe.com/commerce/frontend-core/guide/layouts/) och [anpassningar](https://developer.adobe.com/commerce/frontend-core/guide/layouts/xml-manage/).

## Migreringsarbete

Precis som en uppgradering mellan 1.x-versioner (till exempel från v1.12 till v1.14) beror migreringsnivån från Magento 1 till Magento 2 på hur du har skapat webbplatsen och hur du har anpassat den.
Vi förbättrar dock hela tiden [!DNL Data Migration Tool] (mer information finns i [Ändra](https://github.com/magento/data-migration-tool/blob/2.3/CHANGELOG.md)), så migreringsarbetet minskar kontinuerligt.
