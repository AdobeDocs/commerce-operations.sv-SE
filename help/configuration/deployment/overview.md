---
title: Distributionsöversikt
description: Läs om distributionsstrategier för Commerce-programmet.
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '816'
ht-degree: 0%

---


# Distributionsöversikt

Dessa ämnen handlar om processen att distribuera Commerce-programmet till en produktionsplats för Adobe Commerce version 2.2 och senare. Adobe rekommenderar den här distributionsmetoden för alla som har en stor webbplats och som inte vill drabbas av driftavbrott under distributionen.

Om du distribuerar Commerce på en enda dator och kan tolerera vissa driftavbrott under distributionen, se [Driftsättning av en dator](../deployment/single-machine.md).

## Driftsättning av pipeline

I Commerce version 2.2 införde Adobe _distribution av pipeline_ som ett nytt sätt att driftsätta i produktionen med minimala driftstopp. Den här distributionsprocessen sker på olika system och ger ett sätt att upprätthålla konsekventa konfigurationer för alla pipelinesystem för distribution. Det är en enkel men kraftfull modell som gör att du kan separera vanliga konfigurationsinställningar från systemspecifika inställningar (som värd och port) eller känsliga inställningar (som namn och lösenord).

För att kunna använda pipeline-distribution antar Adobe att du:

- En erfaren systemintegratör med mycket goda kunskaper om Adobe Commerce konfigurationsalternativ.
- Hantera en stor handelsplats (tusentals lagerställeenheter) och vill hålla driftstoppen på produktionsplatsen så kort som möjligt.
- Kunskap om PHP-programmering.
- Erfaren av metoder för källkontroll.
- Koden finns i en källkontrollsdatabas. I den här guiden antar vi att du använder en Git-baserad databas.

### Minskade driftstopp

När du distribuerar statiska resurser och kompilerar kod på en annan dator än produktionssystemet minimerar du driftstoppen. Nedtiden i produktionssystemet är begränsad till den tid som krävs för att överföra statiska filer och kompilerad kod till servern.

## Driftsättningssystem

Vi använder följande termer för att beskriva de system som används vid driftsättningen.

- **Utvecklingssystem**- Dator där utvecklare arbetar med att anpassa kod. och installera tillägg, teman och språkpaket från Commerce Marketplace. Dessutom gör du alla konfigurationsändringar i utvecklingssystemet. Du kan ha många utvecklingssystem.

- **Bygg system**- Ett system där du distribuerar statiska resurser och kompilerar kod för produktionssystemet. Eftersom du bygger dessa resurser på ett system som inte är i produktion minimeras driftstoppen i produktionssystemet.

   Ditt byggsystem behöver inte ha Commerce installerat på det. Den behöver bara Commerce-koden, men ingen databasanslutning krävs. Ditt byggsystem behöver inte heller vara en fysiskt separat server.

- **Mellanlagringssystem**—_Valfritt_. Du kan också konfigurera ett mellanlagringssystem som ska användas för sluttestning av all integrerad kod, inklusive UAT (User Acceptance Testing). Konfigurera ett mellanlagringssystem på samma sätt som du konfigurerar ett produktionssystem. Förutom att staging inte är din livebutik och inte behandlar beställningar från kunder, är det identiskt med produktion.

- **Produktionssystem**—Din livebutik. Du bör göra minimala ändringar av den direkta konfigurationen här, och absolut ingenting som inte har testats på en mellanlagringsinstans. Gör konfigurationsändringar med [Datakorrigeringar](https://developer.adobe.com/commerce/php/development/components/declarative-schema/patches/) som har testats på en Staging/Development-instans.

## Andra distributionsmetoder

Du kan också använda andra distributionsmetoder, som:

- Säker kopiering med SCP eller omsynkronisering
- [Capistrano](https://capistranorb.com/documentation/overview/what-is-capistrano)
- The [Distributionsverktyg](https://deployer.org/)

## Hantera konfigurationen

Modellering efter [faktor 3 i 12-faktorsappdesignen](https://12factor.net/config)sparar nu Commerce konfigurationen för varje system i själva systemet. (Inställningar för utvecklingskonfiguration lagras i utvecklingssystemet, produktionsinställningar lagras i produktionssystemet.)

Vi erbjuder ett sätt att synkronisera konfigurationen av dina system:

- **Delad konfiguration**—Inställningar som varken är systemspecifika eller känsliga.

   Delade inställningar är inställningar som du vill ska vara konsekventa i utvecklings- och produktionssystem. Ange den delade konfigurationen i Admin i din utveckling (eller Adobe Commerce i molninfrastrukturen) _integration_).

   Den delade konfigurationsfilen, `app/etc/config.php`, bör ingå i källkontrollen så att den kan delas mellan utvecklings-, bygg- och produktionssystem.

- **Systemspecifik konfiguration**—Inställningar som varierar beroende på system, t.ex. sökmotorns värdnamn och portar.

- **Känslig konfiguration**—Inställningar som ska _not_ ha källkontroll eftersom de visar personligt identifierbar information (PII) eller inställningar som API-nycklar eller lösenord.

   Den systemspecifika konfigurationsfilen, `app/etc/env.php`, bör _not_ ingå i källkontrollen eller på annat sätt delas mellan system. Använd i stället [`magento config:set` och `magento:sensitive:set` kommandon](../cli/set-configuration-values.md) för att ange värden för de inställningarna i produktionssystemet.

>[!INFO]
>
>Dessa nya metoder för att hantera konfigurationen är valfria. Du behöver inte göra det, men vi rekommenderar starkt att du använder dem.

Oftast går det inte att redigera de konfigurationsalternativ som du anger i den delade, systemspecifika eller känsliga konfigurationen i Admin. På så sätt blir inställningarna enhetliga i alla system. (Du kan också använda [`magento config:set` kommando](../cli/set-configuration-values.md) utan `--lock` för att konfigurera inställningar som kan redigeras i administratören.)

Varje Commerce-konfigurationsalternativ har en unik _konfigurationssökväg_. Om du vill ange ett värde för ett konfigurationsalternativ kan du antingen använda ett CLI-kommando eller en miljövariabel för att ange värdet för den konfigurationssökvägen på ett specifikt system.
