---
title: Distributionsöversikt
description: Läs om distributionsstrategier för Commerce.
feature: Configuration, Deploy
exl-id: d5ed6fb3-2dd2-49df-802b-6d712ecd9ccf
source-git-commit: dcc283b901917e3681863370516771763ae87462
workflow-type: tm+mt
source-wordcount: '804'
ht-degree: 0%

---

# Distributionsöversikt

Här beskrivs hur man distribuerar Commerce till en produktionsplats för Adobe Commerce version 2.2 och senare. Adobe rekommenderar den här distributionsmetoden för alla som har en stor webbplats och som inte vill drabbas av driftavbrott under distributionen.

Om du distribuerar Commerce på en enda dator och kan tolerera vissa driftavbrott under distributionen, se [Driftsättning av en enda dator](../deployment/single-machine.md).

## Driftsättning av pipeline

Med Commerce version 2.2 introducerade Adobe _pipeline-distribution_ som ett nytt sätt att distribuera till produktionen med minimala driftavbrott. Den här distributionsprocessen sker på olika system och ger ett sätt att upprätthålla konsekventa konfigurationer för alla pipelinesystem för distribution. Det är en enkel men kraftfull modell som gör att du kan separera vanliga konfigurationsinställningar från systemspecifika inställningar (som värd och port) eller känsliga inställningar (som namn och lösenord).

För att kunna använda pipeline-distribution antar Adobe att du:

- En erfaren systemintegratör med mycket goda kunskaper om Adobe Commerce konfigurationsalternativ.
- Hantera en stor Commerce-sajt (tusentals lagerställeenheter) och vill hålla driftstoppen på produktionsplatsen så kort som möjligt.
- Kunskap om PHP-programmering.
- Erfaren av metoder för källkontroll.
- Koden finns i en källkontrollsdatabas. I den här guiden antar vi att du använder en Git-baserad databas.

### Minskade driftstopp

När du distribuerar statiska resurser och kompilerar kod på en annan dator än produktionssystemet minimerar du driftstoppen. Nedtiden i produktionssystemet är begränsad till den tid som krävs för att överföra statiska filer och kompilerad kod till servern.

## Driftsättningssystem

Vi använder följande termer för att beskriva de system som används vid driftsättningen.

- **Utvecklingssystem** - Dator där utvecklare arbetar med att anpassa kod och installera tillägg, teman och språkpaket från Commerce Marketplace. Dessutom gör du alla konfigurationsändringar i utvecklingssystemet. Du kan ha många utvecklingssystem.

- **Skapa system** - Ett system där du distribuerar statiska resurser och kompilerar kod för produktionssystemet. Eftersom du bygger dessa resurser på ett system som inte är i produktion minimeras driftstoppen i produktionssystemet.

  Ditt byggsystem behöver inte ha Commerce installerat. Den behöver bara Commerce-koden, men ingen databasanslutning krävs. Ditt byggsystem behöver inte heller vara en fysiskt separat server.

- **Mellanlagringssystem**—_Valfritt_. Du kan också konfigurera ett mellanlagringssystem som ska användas för sluttestning av all integrerad kod, inklusive UAT (User Acceptance Testing). Konfigurera ett mellanlagringssystem på samma sätt som du konfigurerar ett produktionssystem. Förutom att staging inte är din livebutik och inte behandlar beställningar från kunder, är det identiskt med produktion.

- **Produktionssystem** - Din livebutik. Du bör göra minimala ändringar av den direkta konfigurationen här, och absolut ingenting som inte har testats på en mellanlagringsinstans. Om det är möjligt kan du göra konfigurationsändringar med [datakatchar](https://developer.adobe.com/commerce/php/development/components/declarative-schema/patches/) som har testats på en mellanlagrings-/utvecklingsinstans.

## Andra distributionsmetoder

Du kan också använda andra distributionsmetoder, som:

- Säker kopiering med SCP eller omsynkronisering
- [Capistrano](https://capistranorb.com/documentation/overview/what-is-capistrano)
- [Distributionsverktyget](https://deployer.org/)

## Hantera konfigurationen

Commerce lagrar nu konfigurationen för varje system i själva systemet efter [faktor 3 i 12-faktorappdesignen](https://12factor.net/config). (Inställningar för utvecklingskonfiguration lagras i utvecklingssystemet, produktionsinställningar lagras i produktionssystemet.)

Vi erbjuder ett sätt att synkronisera konfigurationen av dina system:

- **Delad konfiguration** - Inställningar som varken är systemspecifika eller känsliga.

  Delade inställningar är inställningar som du vill ska vara konsekventa i utvecklings- och produktionssystem. Ange den delade konfigurationen i Admin i ditt utvecklingssystem (eller Adobe Commerce i molninfrastruktursystemet _integration_).

  Den delade konfigurationsfilen, `app/etc/config.php`, bör inkluderas i källkontrollen så att den kan delas mellan utvecklings-, bygg- och produktionssystem.

- **Systemspecifik konfiguration** - Inställningar som varierar beroende på system, till exempel värdnamn och portar för sökmotorer.

- **Känslig konfiguration** - Inställningar som _inte_ ska finnas i källkontrollen eftersom de visar personligt identifierbar information (PII) eller inställningar som API-nycklar eller lösenord.

  Den systemspecifika konfigurationsfilen `app/etc/env.php` ska _inte_ inkluderas i källkontrollen eller på annat sätt delas mellan system. Använd i stället [`magento config:set` och `magento:sensitive:set` commands](../cli/set-configuration-values.md) för att ange värden för de inställningarna i produktionssystemet.

>[!INFO]
>
>Dessa nya metoder för att hantera konfigurationen är valfria. Du behöver inte göra det, men vi rekommenderar starkt att du använder dem.

Oftast går det inte att redigera de konfigurationsalternativ som du anger i den delade, systemspecifika eller känsliga konfigurationen i Admin. På så sätt blir inställningarna enhetliga i alla system. (Du kan också använda kommandot [`magento config:set` &#x200B;](../cli/set-configuration-values.md) utan alternativet `--lock` för att konfigurera inställningar som kan redigeras i administratören.)

Varje konfigurationsalternativ för Commerce har en unik _konfigurationssökväg_. Om du vill ange ett värde för ett konfigurationsalternativ kan du antingen använda ett CLI-kommando eller en miljövariabel för att ange värdet för den konfigurationssökvägen på ett specifikt system.
