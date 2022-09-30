---
title: Versionspolicy
description: Läs mer om de olika typerna av Adobe Commerce-utgåvor, inklusive smärre utgåvor, korrigeringsfiler, säkerhetsuppdateringar, snabbkorrigeringar, enskilda korrigeringsfiler och anpassade korrigeringsfiler.
source-git-commit: 79f36e3728e6bc436e8093bd4051143a48e681d6
workflow-type: tm+mt
source-wordcount: '951'
ht-degree: 0%

---


# Versionspolicy för Adobe Commerce

Adobe Commerce och Magento Open Source använder [semantisk versionshantering](https://semver.org/) på den enskilda modulnivån (till exempel `magento/framework 101.1.1`), men inte för marknadsföringsversionsnumret. Exempel:

- **STÖRRE UTGÅVA**—2
- **MINDRE frisläppning**—2.4
- **PATCH**—2.4.1
   - **säkerhetsuppdatering**—2.4.1-p1
      - Säkerhetsfelkorrigering
      - Säkerhetsförbättring
- **Funktionsrelease**
- **Hotfix**
- **Enskild patch**
- **Egen korrigering**

## MINDRE frisläppning

Följande riktlinjer gäller för mindre releaser:

- Det är möjligt att bryta ned systemet. kod som skrivits för Adobe Commerce 2.2.x kanske inte längre fungerar med Adobe Commerce 2.3.x. Mindre versioner kan till exempel ge stöd för större systemkrav och beroenden, som PHP.
- Modulversionerna kan variera. Vissa moduländringar införs till exempel i en ny korrigering medan andra införs i en mindre version.
- Mindre versioner kan innehålla nya funktioner som kan kräva ytterligare arbete av dig eller din partner under uppgraderingen för att säkerställa kompatibilitet.
- Mindre releaser kan innehålla korrigeringar av säkerhets- och kvalitetsproblem.

## PATCH

Patch-releaser är främst inriktade på att leverera säkerhets-, prestanda-, efterlevnads- och högprioriterade kvalitetskorrigeringar som hjälper dig att få webbplatserna att prestera maximalt.

Följande riktlinjer gäller för korrigeringsversioner:

- Den senaste delversionen som stöds får fullständiga funktionsförbättringar och korrigeringar.
- Ändringar som kan bryta tillägg eller kodkompatibilitet undviks. Kod som skrivits för version 2.2.0 bör till exempel fortfarande fungera med version 2.2.7.
- I undantagsfall kan ändringar eller ytterligare patchar eller programfixar släppas för att åtgärda säkerhets- eller kompatibilitetsproblem och högkvalitativa problem. På modulnivå är detta i huvudsak förändringar på PATCH-nivå. ibland mindre ändringar.

## säkerhetsuppdatering

**Felkorrigering för säkerhet**: En programvarukodsändring som åtgärdar ett identifierat säkerhetsproblem och ger förväntade resultat i ett påverkat produktområde. Dessa korrigeringar är vanligtvis bakåtkompatibla.

**Säkerhetsförbättring**: En programvaruförbättring eller konfigurationsändring som proaktivt förbättrar säkerheten i programmet. Dessa säkerhetsförbättringar hjälper till att hantera säkerhetsrisker som påverkar säkerhetsställningen i Adobe Commerce-programmet, men som kan vara inkompatibla bakåt.

Med säkerhetsuppdateringar kan du skydda din webbplats utan att lägga på ytterligare kvalitetskorrigeringar och förbättringar som ingår i en fullständig kvartalsvis patch-release. Säkerhetsuppdateringar läggs till med&quot;-pN&quot;, där N är den stegvisa korrigeringsversionen som börjar med 1 (till exempel 2.3.5-p1). Säkerhetsuppdateringar kan även innehålla snabbkorrigeringar som krävs för att åtgärda viktiga problem som påverkar Adobe Commerce-programmet.

Varje säkerhetsuppdatering baseras på den tidigare fullständiga patchversionen. Den innehåller kvalitets- och säkerhetskorrigeringar från tidigare korrigeringsversioner och säkerhetskorrigeringar som skapats mellan den tidigare fullständiga korrigeringsversionen och säkerhetsuppdateringen.

I och med kungörandet av [strategi för ny release och uppdaterad livscykelpolicy](https://business.adobe.com/blog/how-to/accelerating-innovation-through-simplified-release-strategy) (9/16/2021) skiljer sig våra säkerhetsuppdateringar åt beroende på om de gäller den senaste mindre versionen som stöds eller en del av en tidigare mindre version som fortfarande stöds:

- **Säkerhetsuppdateringar för den senaste mindre versionen som stöds**:

   - Säkerhetsuppdateringen för den senaste mindre utgåvan som stöds (för närvarande Adobe Commerce 2.4) innehåller:

      - Säkerhetsfelkorrigeringar som har skapats sedan den tidigare fullständiga korrigeringsversionen.

      - Dessa säkerhetsuppdateringar kan även innehålla programfixar som krävs för att åtgärda viktiga problem som kan påverka Adobe Commerce-programmet.
   - Säkerhetsuppdateringen för den senaste mindre utgåvan som stöds (för närvarande Adobe Commerce 2.4) innehåller vanligtvis inga säkerhetsförbättringar. Dessa ingår i den fullständiga patchversionen för den senaste mindre versionen.


- **Säkerhetsuppdateringar för tidigare mindre versioner som stöds**:

   - Säkerhetsuppdateringen för en tidigare mindre version som fortfarande stöds (för närvarande Adobe Commerce 2.3) innehåller:

      - Säkerhetsfelkorrigeringar som har skapats sedan den tidigare korrigerings- eller säkerhetskorrigeringsversionen samt nya säkerhetsförbättringar.

      - Dessa säkerhetsuppdateringar kan även innehålla snabbkorrigeringar som krävs för att åtgärda viktiga problem som påverkar Adobe Commerce-programmet.

      |  | Säkerhetsfel | Säkerhetsförbättring |
      |--------------------------------------------------------------------------------|--------------|----------------------|
      | Säkerhetsuppdateringar för den senaste mindre versionen som stöds (för närvarande 2.4) | X |  |
      | Säkerhetsuppdateringar för tidigare mindre versioner som stöds (för närvarande 2.3) | X | X |


Allmän information om säkerhetsreleaser finns i [Vi presenterar den nya patchversionen med endast säkerhet](https://community.magento.com:443/t5/Magento-DevBlog/Introducing-the-New-Security-Patch-Release/ba-p/141287). Instruktioner om hur du hämtar och använder säkerhetspatchar finns i [Snabbstart](../installation/composer.md).

## Funktionsrelease

Funktionsreleaser innehåller nya funktioner och funktionsuppdateringar som levereras som fristående tjänster, utöver korrigeringsversionerna. Exempel är tjänster som Product Recommendations och Live Search, oberoende moduler som PWA Studio och Inventory management (MSI) samt uppdateringar av våra molntjänster och vår infrastruktur.

## Hotfix

Programfixar är korrigeringar som innehåller effektiva säkerhets- eller kvalitetskorrigeringar, t.ex. korrigeringar av noll-dagars sårbarheter, som påverkar många handlare. Adobe släpper snabbkorrigeringar för Adobe Commerce-versioner som fortfarande stöds och påverkas av viktiga säkerhets- eller kvalitetsproblem efter behov. Programfixar publiceras på [Avsnittet Kända fel](https://support.magento.com/hc/en-us/sections/360003869892-Known-issues-patches-attached-) i vår kunskapsbas. Dessa korrigeringar ingår i nästa planerade korrigeringsversion.

>[!NOTE]
>
>Snabbkorrigeringar kan innehålla inkompatibla ändringar bakåt.

## Enskild patch

Enskilda korrigeringsfiler innehåller korrigeringar av låg kvalitet för ett specifikt problem. Dessa korrigeringar tillämpas på de mindre versioner av Adobe Commerce som stöds. Adobe släpper enskilda patchar efter behov för Adobe Commerce i enlighet med våra [Software Lifecycle Policy](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf).

>[!NOTE]
>
>Enskilda korrigeringsfiler innehåller inte ändringar som är inkompatibla bakåt.

## Egen korrigering

Skapas av annan personal än Adobe för att åtgärda ett problem eller ändra Adobe Commerce-koden av olika anledningar. Anpassade patchar levereras via [Verktyget Korrigeringar](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html).

## Relaterade ämnen

- [Planering och budgetering för Commerce-uppgraderingscykler](https://magento.com/sites/default/files8/2019-08/Magento-Release-Cycle-Infosheet_Aug_2019.pdf)
- [Versionshantering](https://developer.adobe.com/commerce/php/development/versioning/)
- [Kommande versioner](schedule.md)
- [Software Lifecycle Policy](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)
