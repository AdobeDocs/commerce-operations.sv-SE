---
title: Adobe Commerce och Adobe Experience Manager Infrastructure Alignment
description: Anpassa din Adobe Commerce- och Adobe Experience Manager-infrastruktur för att ange godtagbara tidsgränser och anslutningsgränser.
exl-id: f9cb818f-1461-4b23-b931-e7cee70912fd
source-git-commit: e76f101df47116f7b246f21f0fe0fa72769d2776
workflow-type: tm+mt
source-wordcount: '675'
ht-degree: 0%

---

# Infrastrukturanpassning (tidsgränser och anslutningsgränser)

Det finns inställningar med AEM och Adobe Commerce och omgivande infrastrukturer som belastningsutjämnare som behöver justeras. Dessa är relaterade till anslutningsgränser och timeoutinställningar.

En felpassning mellan dessa gränser skulle kunna innebära att anslutningar stryps AEM sidan, medan Adobe Commerce klarar att hantera fler anslutningar. På samma sätt kan en feljustering för timeoutinställningarna innebära att timeoutfel inträffar AEM Adobe Commerce fortfarande bearbetar en begäran.

För timeoutinställningarna bör inställningarna granskas och justeras för att förhindra att 503 timeoutfel uppstår under inläsning. Det finns flera inställningar för infrastruktur och programtimeout att granska:

![Numrerat diagram som beskriver tidsgränser och anslutningsgränser för AEM](../assets/commerce-at-scale/timeout-settings.svg)

## AEM belastningsutjämnare

Om det finns en belastningsutjämnare för AWS-program i infrastrukturen och flera avsändare/utgivare bör följande inställningar beaktas för belastningsutjämnaren:

1. Hälsokontroller av utgivare bör granskas för att förhindra att utskickare lämnar tjänsten i onödan tidigt på grund av belastningar. Timeoutinställningarna för hälsokontrollen för belastningsutjämnaren ska justeras mot utgivarens timeoutinställningar.

   ![Skärmbild som visar hälsokontroller AEM belastningsutjämnaren](../assets/commerce-at-scale/health-checks.png)

1. Dispatcher-målgruppsvaraktighet kan inaktiveras och Round Robin-algoritmen för belastningsutjämning kan användas. Detta förutsätter att det inte finns någon AEM specifik funktionalitet eller AEM användarsessioner som skulle kräva att sessionens varaktighet ställs in. Man antar att användarinloggning och sessionshantering endast sker på Adobe Commerce via GraphQL.

   ![Skärmbild som visar AEM attribut för sessionsbegränsning](../assets/commerce-at-scale/session-stickiness.png)

1. Observera att om du aktiverar klisterlappning för sessioner kan detta göra att begäranden snabbt inte cachas, eftersom Fastly som standard inte cachelagrar sidor med huvudet Set-Cookies. Adobe Commerce ställer in cookies även på cachelagrade sidor (TTL > 0), men med standardinställningen Fast VCL raderas dessa cookies på cachelagrade sidor för att Snabb cachelagring ska fungera. Om sidorna inte cachelagras kontrollerar du eventuella egna cookies som du använder och överför även Snabbt VCL och kontrollerar webbplatsen igen.

## Dispatcher timeout-inställningar

/timeout i alternativen för dispatcher &quot;renders&quot; anger den anslutningens timeout som öppnar AEM publiceringsinstans i millisekunder. Detta bör granskas och standardinställningen 0 (oändlig tidsgräns) bör användas om det finns en separat belastningsutjämnare för att hantera timeoutinställningarna.

Om det inte finns någon belastningsutjämnare i infrastrukturen bör timeoutinställningarna i stället anges i inställningarna för dispatcher /timeout, med ett värde som matchar GraphQL timeoutinställningar i utgivaren.

## Utgivare

Gränser och tidsgränser för anslutning av Publisher GraphQL: Inledningsvis bör Max HTTP-anslutningar i Adobe Commerce CIF GraphQL Client Configuration Factory OSGI anges till standardgränsen för snabb anslutning, som för närvarande är inställd på 200. Även om det finns flera utgivare i den AEM servergruppen bör gränsen vara densamma för varje utgivare, vilket matchar inställningen Fastt. Anledningen till detta är att i vissa fall kan en utgivare hantera mer trafik än de andra utgivare, om en associerad utgivare tas bort från servergruppen. Det innebär att all trafik dirigeras genom den enda kvarvarande avsändaren och utgivaren, i det här fallet kan den enda utgivaren behöva alla HTTP-anslutningar.

HTTP-standardmetoden ska anges från POST till GET. Endast GET-begäranden cachelagras i Adobe Commerce GraphQL-cachen och därför bör standardmetoden alltid anges till GET.

Tidsgränsen för http-anslutningen och http-sockettidsgränsen bör anges till ett värde som matchar tidsgränsen för fast anslutning.

I följande bild visas Magento CIF GraphQL Client Configuration Factory. Inställningarna som visas här är bara exempel och behöver justeras från fall till fall:

![Skärmbild av Commerce integrationa frameworkens konfigurationsinställningar](../assets/commerce-at-scale/cif-config.png)

Följande bilder visar snabbgående backend-konfigurationer. Inställningarna som visas här är bara exempel och behöver justeras från fall till fall:

![Skärmbild av Commerce Admin-konfigurationsinställningar för Snabbt](../assets/commerce-at-scale/cif-config-advanced.png)
