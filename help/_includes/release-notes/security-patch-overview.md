---
source-git-commit: 52c330f62d722a4cae7f7f360ca61eca0f04b961
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 0%

---
# Om Adobe Commerce säkerhetsuppdateringar

**Säkerhetsfelkorrigering**: En programkodändring som åtgärdar ett identifierat säkerhetsproblem och ger förväntade resultat i ett påverkat produktområde. Dessa korrigeringar är vanligtvis bakåtkompatibla.

**Säkerhetsförbättring**: En programvaruförbättring eller konfigurationsändring som proaktivt förbättrar säkerheten i programmet. Dessa säkerhetsförbättringar hjälper till att hantera säkerhetsrisker som påverkar säkerhetsställningen i Adobe Commerce-programmet, men som kan vara inkompatibla bakåt.

Med säkerhetsuppdateringar kan du skydda din webbplats utan att lägga på ytterligare kvalitetskorrigeringar och förbättringar som finns i en fullständig patchversion. Säkerhetsuppdateringar läggs till med&quot;-pN&quot;, där N är den stegvisa korrigeringsversionen som börjar med 1 (till exempel 2.3.5-p1). Säkerhetsuppdateringar kan även innehålla snabbkorrigeringar som krävs för att åtgärda viktiga problem som påverkar Adobe Commerce-programmet.

Säkerhetsuppdateringar kan även innehålla kompatibilitetsrelaterade ändringar som krävs för att säkerställa att Adobe Commerce-programmet uppfyller kompatibilitetskraven. Dessa ändringar kan medföra bakåtkompatibla ändringar och krävs för att säkerställa att alla versionsrader som stöds förblir kompatibla.

Varje säkerhetsuppdatering baseras på den tidigare fullständiga patchversionen. Den innehåller kvalitets- och säkerhetskorrigeringar från tidigare korrigeringsversioner och säkerhetskorrigeringar som skapats mellan den tidigare fullständiga korrigeringsversionen och säkerhetsuppdateringen.

Instruktioner om hur du hämtar och använder säkerhetsuppdateringar finns i [Så här hämtar och använder du säkerhetsuppdateringar](https://experienceleague.adobe.com/sv/docs/commerce-knowledge-base/kb/how-to/how-to-obtain-and-apply-security-patches) i _Adobe Commerce Knowledgebase_.

>[!NOTE]
>
>Utökade säkerhetsuppdateringar för support är bara tillgängliga för Adobe Commerce-kunder och är inte tillgängliga för Magento Open Source kodbas. Se [Utökad support](https://experienceleague.adobe.com/sv/docs/commerce-operations/release/planning/lifecycle-policy#extended-support).

## Isolerad säkerhetskorrigeringsfil

Isolerade säkerhetspatchfiler är icke-kumulativa, fristående korrigeringsfiler som endast innehåller korrigeringar för en eller flera säkerhetsluckor, utan ytterligare funktionsuppdateringar eller icke-säkerhetsändringar. Dessa patchar släpps fristående för att möjliggöra snabbare åtgärder och ingår i nästa fullständiga säkerhetskorrigering. Information om säkerhetsluckorna finns i den tillhörande säkerhetsbulletinen som länkar till en KB-artikel (Knowledge Base) med anvisningar om hur du tillämpar patchen och ytterligare information.

För att kunna använda en isolerad säkerhetsuppdateringsfil måste kunden ha den senaste säkerhetsuppdateringen (den senaste -p-versionen) för den versionslinje som stöds, eftersom isolerade säkerhetsuppdateringsfiler endast testas mot den versionen.

Gå till [Säkerhetscenter](https://helpx.adobe.com/se/security/products/magento.html) för att hitta de senaste säkerhetsuppdateringarna för Adobe Commerce.

