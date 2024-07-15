---
title: Självvärdande - översikt
description: Lär dig mer om de bästa sätten att tänka på när du är värd för dig själv. Ämnena varierar från säkerhetselement till katastrofåterställning av många fler. Dessa ämnen är till för att hjälpa ett företag som har bestämt sig att ha en egen version av Adobe Commerce. De presenterade objekten är inte alla inkluderade, men de bör innehålla ett bra utbud av koncept för att främja en säker, stabil och flexibel webbplats.
landing-page-description: Lär dig några koncept och saker att tänka på när du är värd för Adobe Commerce på egen hand.
short-description: Lär dig strategier och koncept för att vara värd för Adobe Commerce själv.
kt: 11420
doc-type: tutorial
audience: all
last-substantial-update: 2023-04-13T00:00:00Z
exl-id: 1c63d082-c6fb-4795-81cd-75d097c03e6b
feature: Install
source-git-commit: 823498f041a6d12cfdedd6757499d62ac2aced3d
workflow-type: tm+mt
source-wordcount: '724'
ht-degree: 0%

---

# Självvärdande Adobe Commerce - översikt

När du funderar på att gå över till en e-handelsplattform som Adobe Commerce har du alla de alternativ du behöver. Dessa alternativ medför dock ytterligare kostnader, risker och skulder att tänka på. Värdtjänster för en Commerce-webbplats kan utföras med en paketerad lösning, som [Adobe Commerce i molninfrastrukturen](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/getting-started/cloud/1-overview.html){target="_blank"}, där infrastrukturen, servrarna, e-postmeddelanden, SSL-certifikat och många andra är förkonfigurerade och klara att användas. Att hitta en bra värdlösning som Adobe Commerce på molninfrastruktur gör hela processen enklare - det finns övertygande skäl till att du kan vara värd för din Commerce webbplats. På de medföljande sidorna finns det många ämnen som ger insikter och vägledning om de tjänster, tekniker och koncept som självbetjäning erbjuder. Informationen här är inte fullständig och man förväntar sig inte att ni ska implementera alla förslag. Men de här artiklarna kan hjälpa dig att förstå idéer och koncept som kan göra Adobe Commerce självbetjäning så stabil och säker som möjligt.

När du inte går med i Adobe Commerce på molninfrastruktur används termerna självvärdande eller lokal, eller till och med lokal. Lokalt innebär inte bara i ett datacenter i en byggnad som ett företag äger. Termen representerar allt som inte hanteras av Adobe Commerce i deras infrastruktur. Det finns värdföretag som tillgodoser Adobe Commerce och som också betraktas som självvärdföretag eller fysiska företag.

När det gäller Adobe Commerce och Magento som har öppen källkod fungerar de flesta av de råd och tips som ges för båda versionerna. Även om det inte anges direkt är det förväntat att det är tillämpligt för båda. I det här avsnittet om alternativ för värdtjänster för Adobe Commerce beaktas båda versionerna. Slutligen är de flesta ämnen relevanta för [Adobe Commerce i molninfrastrukturen](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/getting-started/cloud/1-overview.html){target="_blank"} som värdtjänstleverantör.

## Terminologisk nivå angiven

Följande termer används ofta i olika Experience League-artiklar när du pratar med DevOps-teamet och arbetar med företagssupport:

* **DevOps** är en term som används för att beskriva de team som hanterar serverkonfiguration, konfiguration, hantering, SSL-certifikat och allt annat om de servrar och tjänster som används för att köra en Adobe Commerce-webbplats. Termen används för att avgöra när utvecklarens ansvar normalt upphör och var resor och support från ett infrastrukturteam börjar.

* **Säkerhetskoncept** omfattar flera ämnen och överväganden som gör Adobe Commerce-kodbas, filer och filsystem på servrarna och konfigurationer eller uppdateringar som minskar attackytan för många kända utnyttjandemönster.

* **Övervakningsverktygen** täcker några befintliga verktyg och tjänster som övervakar Adobe Commerce webbplatser. De här verktygen kan ibland ge tips om hur du kan förbättra saker eller upptäcka problem och säkerhetsluckor.

* **Disaster Recovery** hjälper dig att ge dig en del koncept och överväganden för den olyckliga händelsen med ett skadat eller utnyttjat projekt.

* **Prestandatips** innehåller proffsiga tips och vägledning för hur du kan få Adobe Commerce-programmet att fungera så bra som möjligt.

* **Dålig aktör** är den term som används för en person eller ett team som försöker göra något skadligt eller obehörigt. Den är inte begränsad till e-handelsapplikationen utan omfattar även infrastrukturen eller någon komponent som är relaterad till webbplatsen.

* **Brandvägg för webbaserade program** (WAF) hjälper till genom att granska varje begäranderubrik till e-handelsprogrammet och blockerar kända mönster och explosioner. En WAF används ofta tillsammans med anpassade filter och regler för att hantera DDOS-attacker.

* **Distributed Denial of Service** (DDoS) är en metod för angrepp som tvingar servrar som kör webbplatsen att konsumeras med falska förfrågningar med tillräckligt stor volym så att de inte längre kan svara på legitima förfrågningar.

## Vad händer nu?

Dessa ämnen finns inte i någon speciell ordning eller sekvens. De är avsedda att förmedla samtalspunkter med en DevOps-tekniker, Commerce Architect och alla andra som arbetar med att fatta detta viktiga beslut om var och hur Adobe Commerce ska vara värd.

{{$include /help/_includes/hosting-related-links.md}}
