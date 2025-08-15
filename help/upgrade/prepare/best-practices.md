---
title: Bästa praxis
description: Använd de bästa metoderna som rekommenderas av Adobe för att hantera uppgraderingsprocessen för dina Adobe Commerce-projekt.
feature: Upgrade, Best Practices
exl-id: 53c505a3-8b99-4fc3-b1b4-f2f75208a51b
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '1055'
ht-degree: 0%

---

# Bästa tillvägagångssätt för uppgradering

I det här avsnittet beskrivs de åtgärder du bör vidta för att hantera komplexiteten hos uppgraderingar av Adobe Commerce-projekt. Teamet bör fundera på uppgraderingar från det ögonblick projektutvecklingen börjar och fortsätter i varje release. Genom att följa dessa standarder blir uppgraderingsprocessen mycket enklare, snabbare och billigare.

>[!TIP]
>
>Rekommendationerna bygger på bästa praxis som stöds av belägg för dess effekt och effektivitet från partner, handlare, Adobe experter och communityn.

## Vad påverkar en uppgradering?

Det är viktigt att förstå de variabler som avgör hur komplex en uppgradering är. Du måste ta hänsyn till dessa variabler i början av varje projekt, inte bara när det är dags att uppgradera. Utvecklingen av ett projekt är avgörande för att säkerställa att framtida uppgraderingar blir smidiga och att du kan styra vad som krävs för att slutföra dem.

Hur stor uppgradering du ska göra beror på följande faktorer:

- **Hur skapade du din webbplats?** Omfattningen av anpassat arbete och antalet installerade tredjepartsmoduler påverkar verkligen komplexiteten i en uppgradering. Kvaliteten på det anpassade arbetet och modulerna kan avgöra om en uppgradering går smidigt.

- **Hoppar du över flera versioner?** Hoppar över releaser gör nästa uppgradering mer komplex, och om du uppgraderar från efterföljande versioner blir processen enklare och billigare.

- **Vilken typ av uppgradering utför du?** En uppgradering till en mindre version (till exempel från 2.3.x till 2.4.0) är mer omfattande än en uppgradering mellan korrigeringsfiler (till exempel från 2.4.2 till 2.4.3). Säkerhetsuppgraderingar är den enklaste typen att implementera.

## Bästa tillvägagångssätt för planering av uppgraderingar

Om du arbetar med ett projekt som redan är i produktion kan du förbättra kvaliteten på koden och anpassningarna och optimera för framtida uppgraderingar genom att uppgradera. Den tid du investerar idag sparar tid på lång sikt.

Om du hanterar flera webbplatser för olika handlare är det bästa sättet att ha en basinstans med de huvudfunktioner och anpassningar du normalt använder. Använd den här grundinstansen som testwebbplats för att slutföra en uppgradering och sedan göra det på andra. Detta ger er flexibilitet att återanvända anpassade moduler för olika kunder och förenkla uppgraderingar mellan olika projekt.

Om ditt projekt är direktsänt föreslår vi att du kör en granskning för att fastställa dess kvalitet och förstår hur du kan förbättra det för att göra uppgraderingarna mer effektiva.

### Utveckla med uppgraderingar i åtanke

Från det att du börjar arbeta med ett projekt bör du fundera över hur framtida uppgraderingar kommer att påverkas av ditt nuvarande arbete. Följ alltid de effektivaste strategierna för Adobe Commerce-utveckling som beskrivs här:

- [Bästa praxis för utveckling](https://developer.adobe.com/commerce/php/best-practices/)
- [Kodningsstandarder](https://developer.adobe.com/commerce/php/coding-standards/)

Börja använda Adobe Commerce Extensibility-plattformen om du inte redan har gjort det. Plattformen gör det möjligt att effektivt anpassa processer, integrera system och driftsätta nya funktioner samtidigt som SaaS-liknande uppgraderingsmöjligheter bibehålls. Funktionerna är:

- **UI-utökningsbarhet**. Utöka och utveckla din butiksverksamhet oberoende av din backend- och mellanvara med [PWA Studio](https://developer.adobe.com/commerce/pwa-studio/).

- **API-utökningsbarhet**. Använd [GraphQL](https://developer.adobe.com/commerce/webapi/graphql/index.html) för att utöka webb-API-lagret genom att utveckla diagramdatamodellen och köra lambda-funktioner direkt från diagramlagret.

- **Adobe I/O mellanvara och tjänster**. Anslut dina system med Adobe Commerce via Adobe mellanvara och en uppsättning appanslutningar som är byggda på [Adobe I/O](https://www.adobe.io/). Dessutom kan ni utöka era kärnplattformsfunktioner genom att skriva över standardbeteendet med er egen affärslogik som fungerar i Adobe I/O.

### Planera uppgraderingar

När vi ständigt utökar möjligheterna i Adobe Commerce är det viktigt att du utvecklar den senaste versionen och definierar en uppgraderingsstrategi i dina projektplaner. På så sätt kan ni vara säkra, kompatibla och uppdaterade med de senaste förbättringarna som gör att ni kan öka försäljningen snabbare, arbeta effektivare och ligga steget före konkurrenterna nu och i framtiden.

För att hjälpa dig att planera och budgetera för uppgraderingar bör du övervaka vårt [releaseschema](https://experienceleague.adobe.com/en/docs/commerce-operations/release/planning/schedule). Planera uppgraderingsuppgifter i teamets eftersläpning i förväg. Målet är att slutföra arbetet med GA.

- Använd förhandsversionen för att lära dig mer om varje ny release. Förhandsversionen är den allmänna tillgänglighetskoden som är tillgänglig för Adobe Commerce handlare och alla partners två veckor före den allmänna tillgängligheten. Om du har flera butiker använder du förhandsversionen i din basbutik och kontrollerar att dina anpassade moduler och teman är kompatibla med den.

- Kontrollera checklistan för [Upgrade Plan](https://support.magento.com/hc/en-us/articles/360057968951) för Adobe Commerce om du vill ha hjälp med att planera uppgraderingen.

- Planera för uppgraderingar i början av året. Du måste boka en budget och resurser för att slutföra varje uppgradering. Kom ihåg att uppgraderingen kan variera avsevärt mellan olika projekt. Använd era upplevelser och kunskaper för att göra en så korrekt plan som möjligt.

- Om uppgraderingarna kräver mer arbete än vad vi beskriver här rekommenderar vi att du granskar ditt projekt och gör justeringar i din miljö för att minska det långsiktiga underhållet.

### Utföra uppgraderingar

Uppgraderingar bör göras regelbundet och inom en fördefinierad budget. Vi rekommenderar att man planerar förgodkända uppgraderingar i början av året för att säkerställa att uppgraderingarna planeras och slutförs i tid.

Utvärdera det arbete som ska utföras för uppgradering:

- Granska [versionsinformationen](https://experienceleague.adobe.com/en/docs/commerce-operations/release/notes/overview) för att förstå den nya versionens omfång och effekt.

- Använd [[!DNL Upgrade Compatibility Tool]](../upgrade-compatibility-tool/overview.md) för att identifiera potentiella problem som måste åtgärdas i din anpassade kod innan du försöker uppgradera till en senare version.

- Om du använder tillägg från tredje part ska du validera deras kompatibilitet med den målversion du planerar att uppgradera till.

### Testning efter uppgradering

Testning är den fas av en uppgradering som kräver mest tid. Därför bör denna process vara så automatiserad som möjligt. Du kan dra nytta av att använda testverktygen. [Programtestguiden](https://developer.adobe.com/commerce/testing/guide/) innehåller information.

Använd en testmiljö för att testa och validera uppgraderingen innan du går över till produktion.

Använd en **underhållssida**. Om du förbereder den här sidan i förväg kan du kommunicera med dina kunder och meddela dem att arbetet pågår i bakgrunden. Den här sidan bör vara synlig i några minuter, men om det finns ett problem kan du behöva använda den längre. Att ha rätt innehåll och design för din underhållssida ger användarna en bra upplevelse även när din butik inte är tillgänglig.
