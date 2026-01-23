---
title: Skapa en datamigreringsplan
description: Lär dig hur du skapar en datamigreringsplan för uppgradering från Magento 1 till Magento 2. Planera och testa migreringen för att undvika problem.
exl-id: a14237f3-c5fe-4f5f-86eb-ed4c39507bff
topic: Commerce, Migration
source-git-commit: 6896d31a202957d7354c3dd5eb6459eda426e8d7
workflow-type: tm+mt
source-wordcount: '889'
ht-degree: 0%

---

# Skapa en datamigreringsplan

Om du vill migrera utan problem måste du planera noggrant och testa migreringen.

## Innan du startar: Överväg en uppgradering

Migrering är ett bra tillfälle att göra allvarliga ändringar och förbereda er webbplats för nästa tillväxtnivå. Fundera på om din nya webbplats behöver utformas med ytterligare maskinvara eller en mer avancerad topologi med bättre cachningsnivåer.

## Steg 1: Granska tillägg på den aktuella webbplatsen

* Vilka tillägg har du installerat?

* Har du identifierat om du behöver alla dessa tillägg på den nya platsen? Det kan finnas gamla som du kan ta bort utan problem.

* Har du fastställt om det finns Magento 2-versioner av dina tillägg? Besök [Commerce Marketplace](https://commercemarketplace.adobe.com/) för att hitta de senaste versionerna eller kontakta din tilläggsleverantör.

* Vilka databasresurser från tilläggen vill du migrera?

## Steg 2: Skapa och förbered din butik för migrering

* Konfigurera ett Magento 2-maskinvarusystem med hjälp av en topologi och design som åtminstone matchar ditt befintliga Magento 1-system

* Installera Magento 2 (med alla moduler i den här versionen) och [!DNL Data Migration Tool] på ett system som uppfyller [systemkraven](../../installation/system-requirements.md)

* Anpassa [!DNL Data Migration Tool]-koden om du vill hoppa över vissa data (som CMS-sidor, försäljningsregler) eller konvertera anpassningar under migreringen. Läs [!DNL Data Migration Tool]Tekniska specifikationer[&#x200B; för &#x200B;](technical-specification.md) om du vill veta mer om hur migreringen fungerar

## Steg 3: Torr körning

Innan du startar migreringen i produktionsmiljön bör du gå igenom alla migreringssteg i testmiljön.

Gör så här för att testa migreringen:

* Kopiera din Magento 1-butik till en testserver

* Migrera helt den replikerade Magento 1-butiken till Magento 2

* Testa din nya butik noggrant

## Steg 4: Starta migreringen

1. Kontrollera att [!DNL Data Migration Tool] har nätverksåtkomst för att ansluta till Magento 1- och Magento 2-databaser. Öppna motsvarande portar i brandväggen.

1. Stoppa alla aktiviteter i administrationspanelen för Magento 1 (utom för Order Management), som frakt, skapa fakturor och kreditnotor. Listan över tillåtna aktiviteter kan utökas genom att inställningarna för Delta-läget i [!DNL Data Migration Tool] justeras.

   >[!NOTE]
   >
   >Återuppta inte dessa aktiviteter förrän Magento 2 Store har publicerats.

1. Vi rekommenderar att alla Magento 1-seriejobb stoppas.

   Om vissa jobb måste köras under migreringen måste du se till att de inte skapar eller ändrar databasentiteter på ett sätt som Delta-läget inte kan behandla.

   Kronijobbet `enterprise_salesarchive_archive_orders` flyttar till exempel gamla order till arkivering. Det är säkert att köra det här jobbet under migreringen eftersom Delta-läget känner igen jobbet och bearbetar arkiverade order korrekt.

1. Använd [!DNL Data Migration Tool] för att migrera inställningar och webbplatser.

1. Kopiera dina Magento 1-mediefiler till Magento 2.

   Kopiera dessa filer manuellt från katalogen `magento1-root/media` till `magento2-root/pub/media`.

1. Använd [!DNL Data Migration Tool] för att masskopiera data från Magento 1-databasen till Magento 2-databasen.

   Om några av tilläggen innehåller data som du vill migrera kan du behöva installera dessa tillägg som är anpassade för Magento 2. Om tilläggen har en annan struktur i Magento 2-databasen använder du mappningsfilerna som finns i [!DNL Data Migration Tool].

1. Indexera om alla Magento 2-indexerare. Mer information finns i [Hantera indexerare](../../configuration/cli/manage-indexers.md) i _Konfigurationsguiden_.

## Steg 5: Gör ändringar i migrerade data (om det behövs)

Ibland kanske du vill ha en Magento 2 Store med olika katalogstrukturer, försäljningsregler och CMS-sidor efter migreringen.

Det är viktigt att iaktta försiktighet när du arbetar med manuella dataändringar. Fel skapar fel i det stegvisa datamigreringssteget som följer.

Exempel: en produkt som har tagits bort från Magento 2: den som har köpts i din Magento 1-butik och som inte längre finns i din Magento 2-butik. Om du överför data om ett sådant köp kan det orsaka ett fel när [!DNL Data Migration Tool] körs i Delta-läge.

## Steg 6: Uppdatera inkrementella data

När du har migrerat data använder du Delta-läget för att hämta in och överföra inkrementella uppdateringar från Magento 1 (t.ex. nya order, granskningar och kundprofilsändringar) till Magento 2.

* Starta den stegvisa migreringen. Uppdateringarna körs kontinuerligt. Du kan när som helst avbryta överföringen av uppdateringar genom att trycka på `Ctrl+C`.

* Testa Magento 2-sajten så snart som möjligt. Om du råkar ut för problem trycker du på `Ctrl+C` för att stoppa den inkrementella migreringen och starta den igen när du har löst problemen.

>[!NOTE]
>
>Varningar vid volymkontroll kan visas om du testar din Magento 2-webbplats och kör migreringsprocessen samtidigt. Det beror på att du i Magento 2 skapar enheter som inte finns i Magento 1.

## Steg 7: Publicera

När Magento 2-sajten är helt migrerad och fungerar som den ska kan du slutföra övergången:

1. Ställ Magento 1-systemet i underhållsläge (DOWNTIME STARTS).

1. Tryck på Ctrl+C i kommandofönstret för migreringsverktyget för att stoppa inkrementella uppdateringar.

1. Starta dina Magento 2 cron-jobb.

1. Indexera om börsindexeraren i Magento 2. Mer information finns i [Hantera indexerare](../../configuration/cli/manage-indexers.md) i _Konfigurationsguiden_.

1. Med ett valfritt verktyg kan du trycka på sidor i Magento 2-systemet för att cachelagra sidor före kunder som använder din butik.

1. Slutverifiering av Magento 2-sajten.

1. Ändra DNS, belastningsutjämnare och så vidare så att de pekar på ny produktionsmaskinvara (DOWNTIME ENDS).

1. Magento 2 Store är nu klar att användas. Du och dina kunder kan återuppta alla aktiviteter.
