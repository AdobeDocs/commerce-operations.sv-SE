---
title: Självvärdande - översikt
description: Lär dig mer om de bästa sätten att tänka på vid självvärdskap. Ämnena kan vara allt från säkerhetselement till katastrofåterställning. Dessa ämnen är till för att hjälpa ett företag som har bestämt sig att ha en egen version av Adobe Commerce. De presenterade objekten är inte alla inkluderade, men de bör innehålla en rad koncept för att främja en säker, stabil och flexibel webbplats.
landing-page-description: Lär dig några koncept och saker att tänka på när du är värd för Adobe Commerce på egen hand.
short-description: Lär dig strategier och koncept för att vara värd för Adobe Commerce själv.
kt: 11420
doc-type: tutorial
audience: all
last-substantial-update: 2023-04-13T00:00:00Z
exl-id: 63f552f3-836c-4a07-96c3-c0e00614fe39
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '738'
ht-degree: 0%

---

# Självvärdande Adobe Commerce - översikt

När du funderar på att gå över till en e-handelsplattform som Adobe Commerce har du alla de alternativ du behöver. Dessa alternativ medför dock ytterligare kostnader, risker och skulder att tänka på. Det går att använda en paketerad lösning som värd för en Commerce-webbplats, till exempel [Adobe Commerce i molninfrastruktur](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/getting-started/cloud/1-overview.html){target="_blank"}, där infrastrukturen, servrarna, e-post, SSL-certifikat och många andra är förkonfigurerade och klara att användas. Att hitta en bra värdlösning som Adobe Commerce på molninfrastruktur gör hela processen enklare, det finns övertygande skäl till att din Commerce-webbplats är värd för sig själv. På de medföljande sidorna finns det många ämnen som ger insikter och vägledning om de tjänster, tekniker och koncept som självbetjäning erbjuder. Informationen här är inte fullständig och man förväntar sig inte att ni ska implementera alla förslag. Men de här artiklarna kan hjälpa dig att förstå idéer och koncept som kan göra Adobe Commerce självbetjäning så stabil och säker som möjligt.

När du inte går med i Adobe Commerce på molninfrastruktur används termerna självvärdande eller lokal, eller till och med lokal. Lokalt innebär inte bara i ett datacenter i en byggnad som ett företag äger. Termen representerar allt som inte hanteras av Adobe Commerce i deras infrastruktur. Det finns värdföretag som tillgodoser Adobe Commerce och som också betraktas som självvärdföretag eller fysiska företag.

När det gäller Adobe Commerce och Magento som har öppen källkod fungerar de flesta av de råd och tips som ges för båda versionerna. Även om det inte anges direkt är det förväntat att det är tillämpligt för båda. I det här avsnittet om alternativ för värdtjänster för Adobe Commerce beaktas båda versionerna. Slutligen är de flesta ämnen relevanta för [Adobe Commerce i molninfrastruktur](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/getting-started/cloud/1-overview.html){target="_blank"} väljs som värdleverantör.

## Terminologisk nivå

Följande termer används ofta i olika Experience League-artiklar när du pratar med DevOps-teamet och arbetar med företagssupport:

* **DevOps** är en term som används för att beskriva de team som hanterar serverkonfiguration, konfiguration, hantering, SSL-certifikat och allt annat om de servrar och tjänster som används för att köra en Adobe Commerce-webbplats. Termen används för att avgöra när utvecklarens ansvar normalt upphör och var resor och support från ett infrastrukturteam börjar.

* **Säkerhetskoncept** omfattar flera ämnen och överväganden som gör Adobe Commerce-kodbas, filer och filsystem på servrarna och konfigurationer eller uppdateringar som minskar attackytan för många kända utnyttjandemönster.

* **Övervakningsverktyg** omfattar ett fåtal befintliga verktyg och tjänster som övervakar Adobe Commerce webbplatser. De här verktygen kan ibland ge tips om hur du kan förbättra saker eller upptäcka problem och säkerhetsluckor.

* **Disaster Recovery** innehåller vissa begrepp och överväganden för den olyckliga händelsen med ett skadat eller utnyttjat projekt.

* **Prestandapstips** ge några proffsiga tips och vägledning så att Adobe Commerce-programmet blir så bra som möjligt.

* **Felaktig aktör** är den term som används för en person eller ett team som försöker göra något illa eller obehörigt. Den är inte begränsad till e-handelsapplikationen utan omfattar även infrastrukturen eller någon komponent som är relaterad till webbplatsen.

* **Brandvägg för webbaserade program** (WAF) hjälper till genom att se varje begäranderubrik för e-handelsprogrammet och blockera kända mönster och explosioner. En WAF används ofta tillsammans med anpassade filter och regler för att hantera DDOS-attacker.

* **Distribuerad denial of service** (DDoS) är en metod för angrepp som tvingar de servrar som kör webbplatsen att konsumeras med falska förfrågningar med tillräckligt stor volym för att de inte längre ska kunna svara på legitima förfrågningar.

## Vad händer nu?

Dessa ämnen finns inte i någon speciell ordning eller sekvens. De är avsedda att förmedla samtalspunkter med en DevOps-tekniker, Commerce Architect och alla andra som är inblandade i detta viktiga beslut om var och hur Adobe Commerce ska vara värd.

{{$include /help/_includes/hosting-related-links.md}}
