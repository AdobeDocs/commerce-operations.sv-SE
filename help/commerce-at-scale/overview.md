---
title: Leverera upplevelser i stor skala
description: Lär dig leverera upplevelser i stor skala med Adobe Commerce och Adobe Experience Manager.
exl-id: e3166c46-fc9d-4ff4-a3a9-2cd740a95e9b
source-git-commit: 76ccc5aa8e5e3358dc52a88222fd0da7c4eb9ccb
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Leverera upplevelser i stor skala med Adobe Commerce, Commerce Integration Framework och Adobe Experience Manager

Ett rekommenderat integreringsmönster mellan AEM och Adobe Commerce som använder CIF som en koppling är för AEM att äga presentationslagret (&quot;glaset&quot;) och Adobe Commerce för att driva handelsbackend som en&quot;headless&quot; backend. Detta integreringssätt drar nytta av styrkan hos varje program: redigering, personalisering och flerkanalsfunktioner i Adobe Commerce AEM- och e-handelsverksamhet.

I en AEM-/CIF-/Adobe Commerce-miljö kommer besökare på e-handelsplatsen till att börja med att AEM. AEM kontrollerar om den begärda sidan finns tillgänglig i dess dispatcherns cache. Om sidan finns kommer den här cachelagrade sidan att skickas till besökaren och ingen ytterligare bearbetning krävs. Om dispatchern inte innehåller den begärda sidan, eller om den har gått ut, begär dispatchern att AEM utgivaren ska bygga sidan, med utgivaren som anropar Adobe Commerce för e-handelsdata för att vid behov skapa sidan. Den inbyggda sidan skickas sedan till avsändaren för att betjäna besökaren och cachelagras sedan för att förhindra att ytterligare inläsningar behöver placeras på servrarna vid efterföljande förfrågningar till samma sida från andra besökare.

![Översiktsdiagram över Adobe Experience Manager och Adobe Commerce-arkitektur](../assets/commerce-at-scale/overview.png)

En kombination av serversidesåtergivning och klientsidesåtergivning kan användas i AEM/CIF/Adobe Commerce-modellen: Återgivning på serversidan för att leverera statiskt innehåll och rendering på klientsidan för att leverera dynamiskt innehåll som ofta ändras eller är personligt genom att anropa Adobe Commerce för specifika komponenter direkt inifrån användarens webbläsare.

Ett exempel på de olika komponenterna på en produktinformationssida på ett exempel AEM e-handel storefront visas i exemplet nedan:

![Översiktsdiagram över Adobe Experience Manager och Adobe Commerce-arkitektur](../assets/commerce-at-scale/product-details-page.svg)

## Återgivning på serversidan

E-handelssidor som produktinformationssidor (PDP) och produktlistsidor (PLP) ändras sannolikt inte ofta och är lämpliga att cachelagras till fullo efter att de har renderats på serversidan med AEM CIF Core Components. Sidorna ska återges på den AEM utgivaren med hjälp av generiska mallar som skapas i AEM. Dessa komponenter hämtar data från Adobe Commerce via GraphQL API:er. Dessa sidor skapas dynamiskt, återges på servern, cachelagras i AEM och skickas sedan till webbläsaren. Exempel på detta visas i de lila rutorna i exemplet ovan.

## Återgivning på klientsidan

Om mer dynamiska attribut som aktienivåer/tillgänglighet eller pris visas, till exempel på produktinformationssidor (PDP), kan komponenter på klientsidan användas. Mallsidan kan byggas och cachas på dispatchern med serversidans renderingsmetod ovan, men inom den statiska sidan kan det finnas dynamiska webbkomponenter på klientsidan. Dessa dynamiska komponenter kan hämta data direkt i klientens webbläsare från Adobe Commerce via GraphQL-API:er för att kontrollera exempelvis aktuellt pris eller aktuell börsnivå i realtid på PDP. Detta säkerställer att innehåll som vanligtvis är viktigt att kunna visas i realtid alltid hämtas vid sidinläsning. Exempel på detta visas i de röda rutorna i exemplet ovan.

En kombination av AEM och klientåtergivning kan också användas under utcheckningsprocessen: kundens kundvagnskomponenter återger kundvagnen, kassaformuläret och integreringen med betaltjänstleverantören. Det här hybridtillvägagångssättet kan även användas för Adobe Commerce kontohanteringsfunktioner som att skapa konto, logga in och glömma lösenord.
