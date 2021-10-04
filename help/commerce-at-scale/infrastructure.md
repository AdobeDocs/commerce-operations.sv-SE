---
title: Adobe Commerce och Adobe Experience Manager Infrastructure Alignment
description: Anpassa er Adobe Commerce och Adobe Experience Manager infrastruktur för att ange godtagbara tidsgränser och anslutningsgränser.
source-git-commit: 6ad72d5110ae3e3a7cf341282f2af9b700874f09
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Infrastrukturanpassning (tidsgränser och anslutningsgränser)

Det finns inställningar för AEM och Adobe Commerce och omgivande infrastruktur, t.ex. belastningsutjämnare som behöver justeras. Dessa är relaterade till anslutningsbegränsningar och timeoutinställningar.

En feljustering mellan dessa gränser skulle kunna innebära att anslutningarna i AEM skulle kunna strypas, medan Adobe Commerce kan hantera fler anslutningar. På samma sätt kan en feljustering för timeoutinställningarna innebära att timeoutfel inträffar AEM Adobe Commerce fortfarande bearbetar en begäran.

För timeoutinställningarna bör inställningarna granskas och justeras för att förhindra att 503 timeoutfel uppstår under inläsning. Det finns flera inställningar för infrastruktur och programtimeout att granska:

![Numrerat diagram som beskriver tidsgränser och anslutningsgränser för AEM](../assets/commerce-at-scale/timeout-settings.svg)

## AEM belastningsutjämnare

Om det finns en belastningsutjämnare för AWS-program i infrastrukturen och flera avsändare/utgivare bör följande inställningar beaktas för belastningsutjämnaren:

1. Hälsokontroller av utgivare bör granskas för att förhindra att utskickare lämnar tjänsten i onödan tidigt på grund av belastningsökningar. Timeoutinställningarna för hälsokontrollen för belastningsutjämnaren ska justeras mot utgivarens timeoutinställningar.

   ![Skärmbild som visar hälsokontroller AEM belastningsutjämnaren](../assets/commerce-at-scale/health-checks.png)

1. Identifiering av målgrupp för dispatcher kan inaktiveras och algoritmen för Round Robin-belastningsutjämning kan användas. Detta förutsätter att det inte finns någon AEM specifik funktionalitet eller AEM användarsessioner som skulle kräva att sessionens varaktighet ställs in. Det förutsätter att användarinloggning och sessionshantering endast sker i Adobe Commerce via GraphQL.

   ![Skärmbild som visar AEM av webbplatsens klistermärken](../assets/commerce-at-scale/session-stickiness.png)

1. Observera att om du aktiverar klisterlappning för sessioner kan detta göra att begäranden snabbt inte cachas, eftersom Fastly som standard inte cachelagrar sidor med huvudet Set-Cookies. Adobe Commerce ställer in cookies även på cacheable-sidor (TTL > 0), men med standardinställningen Fast VCL raderas dessa cookies på cacheable-sidor för att Snabb cachelagring ska fungera. Om sidorna inte cachelagras kontrollerar du eventuella egna cookies som du använder och överför även Snabbt VCL och kontrollerar webbplatsen igen.

## Timeoutinställningar för utsändning

/timeout i alternativen för dispatcher &quot;renders&quot; anger den anslutningens timeout som öppnar AEM publiceringsinstans i millisekunder. Detta bör granskas och standardinställningen 0 (oändlig tidsgräns) bör användas om det finns en separat belastningsutjämnare för att hantera timeoutinställningarna.

Om det inte finns någon belastningsutjämnare i infrastrukturen bör timeoutinställningarna i stället anges i inställningarna för dispatcher /timeout, med ett värde som matchar GraphQL-timeoutinställningarna i utgivaren.

## Utgivare

Gränser och tidsgränser för anslutning till Publisher GraphQL: Inledningsvis bör OSGI-inställningarna för Max HTTP-anslutningar i Adobe Commerce CIF GraphQL Client Configuration Factory anges till standardgränsen för snabbt högsta antal anslutningar, som för närvarande är inställd på 200. Även om det finns flera utgivare i den AEM servergruppen bör gränsen vara densamma för varje utgivare, vilket matchar inställningen Fastt. Orsaken till detta är att i vissa fall kan en utgivare hantera mer trafik än de andra utgivare, om en associerad utgivare tas bort från servergruppen till exempel. Det innebär att all trafik dirigeras genom den enda kvarvarande avsändaren och utgivaren, i det här fallet kan den enda utgivaren behöva alla HTTP-anslutningar.

HTTP-standardmetoden ska anges från POST till GET. Endast GET-begäranden cachelagras i Adobe Commerce GraphQL-cachen och därför bör standardmetoden alltid anges till GET.

Tidsgränsen för http-anslutningen och http-sockettidsgränsen bör anges till ett värde som matchar tidsgränsen för fast anslutning.

Följande bild visar konfigurationsfabriken för klienten Magento CIF GraphQL. Inställningarna som visas här är bara exempel och behöver justeras från fall till fall:

![Skärmbild av konfigurationsinställningar för Commerce-integreringsramverk](../assets/commerce-at-scale/cif-config.png)

Följande bilder visar snabbgående backend-konfigurationer. Inställningarna som visas här är bara exempel och behöver justeras från fall till fall:

![Skärmbild av konfigurationsinställningar för Commerce Admin för snabbt](../assets/commerce-at-scale/cif-config-advanced.png)
