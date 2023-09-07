---
title: Optimera backend-prestanda
description: Läs om hur du optimerar backend-prestanda för Adobe Commerce-webbplatser.
badge: label="Medverkad av objektkälla" type="Informative" url="https://objectsource.co.uk/" tooltip="objektkälla"
role: Admin, User, Developer
feature: Best Practices
source-git-commit: 1ba9325feaa47d767ec7991919fd5ecd53ae6226
workflow-type: tm+mt
source-wordcount: '1075'
ht-degree: 0%

---

# Bästa tillvägagångssätt för optimering av backend-prestanda

I det här avsnittet beskrivs de effektivaste strategierna för att undersöka och optimera backend-prestanda för Adobe Commerce-webbplatser med fokus på databasoptimering och -testning. Utvecklare kan använda den här informationen för att undersöka den unika kontexten i varje Commerce-projekt och identifiera möjligheter att optimera serverdelskonfigurationen och åtgärder för att förbättra webbplatsens prestanda.

>[!NOTE]
>
>Recommendations och exempel inspireras av processer som ObjectSource följer i verkliga kundrelationer för att leverera högpresterande Adobe Commerce-sajter i stor skala.

## Berörda produkter och versioner

[Alla versioner som stöds](../../../release/versions.md) av:

- Adobe Commerce i molninfrastruktur
- Adobe Commerce lokalt

## Optimera databasen för bättre prestanda

Databasoptimering är ett säkert sätt att förbättra användarupplevelsen och öka försäljningen. När du optimerar databasen, som utgör ryggraden i en Commerce-webbplats, kan du förhindra långsamma webbplatsprestanda och eliminera långa laddningstider som skapar friktion för kunderna.

### Stresstestning

Högtrafikperioder som Black Friday kräver att Commerce-sajter hanterar stora trafikvolymer. Som förberedelse för sådana händelser är stresstestning nödvändigt för att förstå hur en webbplats fungerar under exponentiell ökning av belastningen.

Ett verktyg som du kan använda för stresstestning är GTmetrix. Mät platsens beredskap för lastökningar genom att konfigurera GTmetrix för att replikera och multiplicera normalt besökarbeteende och åtgärder. Kör sedan tester för att identifiera och lösa problem som kan påverka prestanda och webbplatsens tillgänglighet under större shoppingtillfällen.

Läs mer om hur du förbereder Commerce-projekt för trafikperioder:

- [Helgdagskänslighet](https://experienceleague.adobe.com/docs/events/mbi-webinars-recordings/2021/holiday-readiness.html)
- [Kundanalys på heldag](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/analyze/performance/holiday-season-perf.html)
- [Ökning av överkapacitet](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/2021-holiday-surge-capacity-requests-for-magento-commerce-cloud.html)

### Belastningstestning

Du kan också använda GTmetrix eller ett liknande verktyg för att läsa in Commerce-testprojekt. Som en prekursor för stresstestning är lasttestning en viktig metod för storskaliga webbplatser med hög trafik. Förebygg oväntade avbrott, frustrerade kunder och ekonomiska förluster genom att förutse och åtgärda problem som påverkar webbplatsens prestanda vid hög belastning.

Använd GTmetrix för att simulera tung trafik och analysera webbplatsens prestanda för att få tydlig information om platskapaciteten. Denna analys hjälper till att identifiera och åtgärda flaskhalsar och identifiera möjligheter att optimera och säkerställa att Commerce-sajter kan fungera effektivt under ökad belastning.

Läs mer om hur du testar Adobe Commerce-projekt:

- [Testvägledning](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/guidance.html)  (molninfrastruktur)
- [Programtestning](https://developer.adobe.com/commerce/testing/guide/)

### Identifiera och åtgärda prestandaproblem

Åtgärda prestandaproblem genom att använda olika verktyg som New Relic och Observation for Adobe Commerce för att upptäcka flaskhalsar och optimera Commerce-sajter effektivt. [New Relic](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/monitor/new-relic/new-relic-service.html) ingår i Adobe Commerce om molninfrastruktur, och [Observation för Adobe Commerce](/help/tools/observation-for-adobe-commerce/intro.md) ingår för både molnbaserade och lokala distributioner.

Använd de här verktygen för att analysera webbplatsens prestanda och identifiera prestandaproblem i samband med:

- Processorintensiva funktioner
- Konfiguration av cachehantering för frågor och backend-åtgärder
- API-anrop från tredje part
- Kronplanering

Du kan till exempel noggrant granska transaktioner med fokus på produktinformation och kategorisidor. Identifiera tidskrävande processer som kan optimeras för att förbättra prestandan. I ett klientengagemang upptäckte objektskällan ett prestandaproblem på en produktinformationssida och hittade ett API-anrop som förbrukade 3,5 % av prestandatiden. Utifrån detta resultat har de undersökt hierarkin för kodkörning för att hitta och åtgärda problemet som orsakar flaskhalsen.

Läs mer om hur du hanterar prestanda för webbplatser:

- [Prestandaövervakning](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/monitor/performance.html) (molninfrastruktur)
- [Granskning av prestandaoptimering](/help/implementation-playbook/infrastructure/performance/recommendations.md)
- [Bästa praxis för konfiguration](/help/performance/configuration.md)
- [Observation för Adobe Commerce](/help/tools/observation-for-adobe-commerce/intro.md)

### Optimera MySQL-prestanda

Att åtgärda prestandaproblem i MySQL genom att implementera databasklustring och frågeoptimering är ett effektivt sätt att förbättra prestanda före och under högtrafikperioder som Black Friday.

#### Implementera databasklustring

Webbplatser med hög trafik har ofta flaskhalsar i databasen, som främst orsakas av att man förlitar sig på en enda MySQL-server. Du kan ta itu med dessa flaskhalsar genom att implementera databasklustring, en distribuerad arkitektur som förbättrar prestanda och garanterar hög tillgänglighet.

Databasklustring minimerar effekten av databasrelaterade problem under trafiktoppar genom att aktivera flera webbnoder för anslutning till flera MySQL-servrar. Använd verktyg som Galera Cluster för att konfigurera databasklustring för Commerce-webbplatser. Galera Cluster ingår i [Adobe Commerce-projekt distribuerade i molninfrastruktur](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/infrastructure/cloud/technology.html).

#### Optimera MySQL-frågor

Infrastrukturen för de flesta Adobe Commerce-webbplatser består oftast av flera webbnoder som är anslutna till en enda MySQL-server.

I den här konfigurationen ansluter varje frontendwebbnod till Galera Cluster, som tillåter flera MySQL-servrar. Om du ökar antalet frontwebbnoder kan du förbättra programmets prestanda, men den enda MySQL-servern är fortfarande en flaskhals.

För att optimera prestanda för MySQL-servern och minimera flaskhalsar är det viktigt att identifiera och minska onödiga frågor. Om du till exempel skickar 1 000 frågor per sekund, men bara 200 är nödvändiga, kan du förbättra prestanda avsevärt genom att optimera och minska antalet frågor.

Läs mer om hur du konfigurerar och optimerar MySQL:

- [Metodtips för databaskonfiguration](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/planning/database-on-cloud.html)
- [Långsam replikering för Galera DB-replikering](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/backend-development/galera-db-slow-replication.html)
- [Allmänna riktlinjer för MySQL](/help/installation/prerequisites/database/mysql.md)
- [Cache-lagring av MySQL-fråga](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/backend-development/mysql-query-cache.html)

## Hantera cron-jobb effektivt: prestanda och timing

Kronjobb spelar en viktig roll när det gäller att bearbeta bakgrundsuppgifter för webbplatser, som rapportgenerering och produktindexering. Optimering av cron-jobb kräver dock att man noggrant undersöker deras inverkan på den övergripande prestandan. Utvecklarna måste utvärdera schemaläggningsfrekvensen och fastställa den optimala timingen baserat på specifika krav.

Prestanda och bekvämlighet balanseras. Det är ofta tillrådligt att schemalägga kundjobb under lågtrafikperioder. Att hantera kunder i olika tidszoner kan dock medföra utmaningar och kräva en genomtänkt strategi för att säkerställa en harmonisk upplevelse över flera olika geografiska områden.

Om du är ansvarig för att optimera prestanda och timing för kron granskar du den aktuella cron-konfigurationen från Commerce Admin och lär dig mer om hur du konfigurerar och konfigurerar cron-jobb för Commerce-projekt.

Du kan också använda Observation for Adobe Commerce för att visa kronrelaterade resultatindikatorer. Detta verktyg kombinerar loggdata från flera källor för att hjälpa dig att bättre hantera Adobe Commerce webbplatsprestanda och diagnostisera problem.

Läs mer om Adobe Commerce cron-implementering:

- [Cron (schemalagda aktiviteter)](https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/cron.html) i _Användarhandbok för Commerce Admin Systems_
- [Programkonfiguration - egenskapen crons](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/app/properties/crons-property.html) (molninfrastruktur)
- [Konfigurera och köra kundvagnar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/app/properties/crons-property.html) (på plats)
- [Observation för Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-operations/tools/observation-for-adobe-commerce/intro.html) (Se [!UICONTROL Cron] och [!UICONTROL MySQL] tabbar.)
