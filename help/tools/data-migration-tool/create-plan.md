---
title: Skapa en datamigreringsplan
description: Följ de här stegen för att skapa en datamigreringsplan för att säkerställa en lyckad uppgradering från Magento 1 till Magento 2.
exl-id: a14237f3-c5fe-4f5f-86eb-ed4c39507bff
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '939'
ht-degree: 0%

---

# Skapa en datamigreringsplan

Om du vill migrera utan problem måste du planera och testa migreringen noggrant.

## Innan du startar: Överväg att uppgradera

Migrering är ett perfekt tillfälle att göra allvarliga ändringar och förbereda er webbplats för nästa tillväxtnivå. Fundera på om din nya webbplats behöver utformas med mer maskinvara eller en mer avancerad topologi med bättre cachningsnivåer.

## Steg 1: Granska tillägg på den aktuella webbplatsen

* Vilka tillägg har du installerat?

* Har du identifierat om du behöver alla dessa tillägg på den nya platsen? Det kan finnas gamla som du kan ta bort utan problem.

* Har du fastställt om det finns Magento 2-versioner av dina tillägg? Gå till [Commerce Marketplace] om du vill hitta de senaste versionerna eller kontakta din tilläggsleverantör.

* Vilka databasresurser från tilläggen vill du migrera?

## Steg 2: Skapa och förbered din butik för migrering

* Konfigurera ett maskinvarusystem för Magento 2 med hjälp av topologi och design som åtminstone matchar ditt befintliga Magento 1-system

* Installera Magento 2.x (med alla moduler i den här versionen) och [!DNL Data Migration Tool] på ett system som uppfyller [systemkraven](../../installation/system-requirements.md)

* Gör dina anpassade justeringar av [!DNL Data Migration Tool]-koden om du inte behöver migrera vissa data (som CMS-sidor, försäljningsregler) eller om du vill konvertera din anpassning av Magento under migreringen. Läs [Tekniska specifikationer](technical-specification.md) för [!DNL Data Migration Tool] för att få en bättre förståelse för hur migrering fungerar inifrån

## Steg 3: Torr körning

Innan du startar migreringen i produktionsmiljön är det bäst att gå igenom alla migreringssteg i testmiljön.

Gör så här för att testa migreringen:

* Kopiera din Magento 1-butik till en testserver

* Migrera den replikerade Magento 1-butiken till Magento 2

* Testa din nya butik noggrant

## Steg 4: Starta migreringen

1. Kontrollera att [!DNL Data Migration Tool] har nätverksåtkomst för att ansluta till Magento 1- och Magento 2-databaser. Öppna motsvarande portar i brandväggen.

1. Stoppa alla aktiviteter på administratörspanelen för Magento 1.x (utom för orderhantering), som frakt, skapa fakturor och kreditnotor. Listan över tillåtna aktiviteter kan utökas genom att ändra inställningarna för Delta-läget i [!DNL Data Migration Tool].

   >[!NOTE]
   >
   >Du får inte återuppta dessa aktiviteter förrän din Magento 2-butik publiceras.

1. Vi rekommenderar att du stoppar alla kronjobb i Magento 1.x.

   Om vissa jobb måste köras under migreringen måste du dock se till att de inte skapar nya databasentiteter eller ändrar de befintliga på det sätt som sådana entiteter inte kan bearbetas i Delta-läget.

   Kronijobbet `enterprise_salesarchive_archive_orders` flyttar till exempel gamla order till arkivering. Det är säkert att köra det här jobbet under migreringen eftersom Delta-läget känner igen jobbet och bearbetar arkiverade order korrekt.

1. Använd [!DNL Data Migration Tool] för att migrera inställningar och webbplatser.

1. Kopiera dina Magento 1.x-mediefiler till Magento 2.x.

   Du måste kopiera dessa filer manuellt från katalogen `magento1-root/media` till `magento2-root/pub/media`.

1. Använd [!DNL Data Migration Tool] för att masskopiera data från Magento 1-databasen till Magento 2-databasen.

   Om några av tilläggen innehåller data som du vill migrera kan du behöva installera dessa tillägg som är anpassade för Magento 2. Om tilläggen har en annan struktur i Magento 2-databasen använder du mappningsfilerna som finns i [!DNL Data Migration Tool].

1. Indexera om alla Magento 2.x-indexerare. Mer information finns i [Hantera indexerare](../../configuration/cli/manage-indexers.md) i _Konfigurationsguiden_.

## Steg 5: Gör ändringar i migrerade data (om det behövs)

Ibland kanske du vill att din Magento 2-butik ska ha olika katalogstruktur, försäljningsregler och CMS-sidor efter migreringen.

Det är viktigt att iaktta försiktighet när du arbetar med manuella dataändringar. Fel skapar fel i det stegvisa datamigreringssteget som följer.

Exempel: en produkt som har tagits bort från Magento 2: den som har köpts i din Magento 1-butik och som inte längre är tillgänglig i din Magento 2-butik. Om du överför data om ett sådant köp kan det orsaka ett fel när [!DNL Data Migration Tool] körs i Delta-läge.

## Steg 6: Uppdatera inkrementella data

När du har migrerat data måste du inkrementellt hämta datauppdateringar som har lagts till i Magento 1-butiken (t.ex. nya order, granskningar och ändringar i kundprofiler) och överföra dessa uppdateringar till Magento 2-butiken med Delta-läget.

* Starta den stegvisa migreringen. Uppdateringarna körs kontinuerligt. Du kan när som helst avbryta överföringen av uppdateringar genom att trycka på `Ctrl+C`.

* Testa Magento 2-sajten under den här tiden för att upptäcka eventuella problem så snart som möjligt. Om du råkar ut för problem trycker du på `Ctrl+C` för att stoppa den inkrementella migreringen och starta den igen när du har löst problemen.

>[!NOTE]
>
>Varningar vid volymkontroll kan visas om du testar din Magento 2-plats och kör migreringsprocessen samtidigt. Det inträffar eftersom du i Magento 2 skapar enheter som inte finns i Magento 1-instansen.

## Steg 7: Publicera

Nu när webbplatsen Magento 2 är uppdaterad med Magento 1 och fungerar normalt gör du följande för att gå till den nya webbplatsen:

1. Sätt Magento 1-systemet i underhållsläge (DOWNTIME STARTS).

1. Tryck på Ctrl+C i kommandofönstret för migreringsverktyget för att stoppa inkrementella uppdateringar.

1. Starta dina Magento 2-kronjobb.

1. Indexera om börsindexeraren i ditt Magento 2-system. Mer information finns i [Konfigurationsguiden].

1. Använd ett valfritt verktyg för att trycka på sidor i Magento 2-systemet för att cachelagra sidor innan de kunder som använder din butik använder dem.

1. Slutverifiering av Magento 2-sajten.

1. Ändra DNS, belastningsutjämnare och så vidare så att de pekar på ny produktionsmaskinvara (DOWNTIME ENDS).

1. Magento 2 Store är nu klar att användas. Du och dina kunder kan återuppta alla aktiviteter.

<!-- LINK ADDRESSES -->

[Commerce Marketplace]: https://marketplace.magento.com
