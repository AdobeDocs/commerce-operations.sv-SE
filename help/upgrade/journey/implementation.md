---
title: Implementering av uppgradering
description: Läs om de olika faserna i uppgraderingsimplementeringen för Adobe Commerce-projekt.
exl-id: d64855a7-73ee-463f-a314-6a8d4ebe4726
source-git-commit: a81d2c0b6526c2c8c8c5c4652c83595667985543
workflow-type: tm+mt
source-wordcount: '826'
ht-degree: 1%

---

# Implementering av uppgradering

Uppgraderingsimplementeringen består av fem faser:

- Uppgraderingsanalys
- Utveckling och kvalitetssäkring
- UAT (User accept testing) och förberedelse för att starta
- Starta
- Post-lansering

## Uppgraderingsanalys

Analys är enligt andra ord den viktigaste delen i uppgraderingsprocessen. En väl utförd analys sparar tid och begränsar antalet överraskningar i framtiden. Resultatet av den här fasen bör vara en detaljerad uppgraderingskontrolllista och ett dokument med alla beroenden.

Här följer några punkter som du kanske vill ta med i en grundlig analys:

- **Omfattningen av målversionen** - Dokumentation om [Experience League](../../release/release-notes/overview.md) och information från partnerreleasemedelswebbinarier innehåller all information du behöver veta om måluppgraderingen.

- **[!DNL Upgrade Compatibility Tool]resultat** - Det här verktyget gör en uppgradering snabbare och enklare genom att jämföra den aktuella koden med målversionens kod och skapa en rapport över alla problem som behöver åtgärdas. Se [[!DNL Upgrade Compatibility Tool]](../upgrade-compatibility-tool/overview.md). Bland huvuduppgifterna i rapporten finns:

   - Aktuell installerad version
   - Uppgradera målversion
   - Antal och information om kritiska fel som påträffats

  >[!TIP]
  >
  >All den här informationen (och mer) är tillgänglig i Site-Wide Analysis Tool [dashboard](../../tools/site-wide-analysis-tool/dashboard.md).

- Uppgraderar tjänster som stöder målversion. Använd följande tabellmall för att mappa ut vilka tjänster du måste uppgradera. Använd [systemkraven](../../installation/system-requirements.md) för att avgöra vad som ska läggas till i kolumnen _Uppgradera till_.


  | Tjänst | Aktuell version | Uppgradera till | Anteckningar |
  |-----------------|-----------------|------------|----------------------------------------------------------|
  | PHP | 7,4 | 8,1 |                                                          |
  | Redis | 6,0 | 6,2 |                                                          |
  | [!DNL RabbitMQ] | 3,8 | 3,9 | Används inte just nu, men vi bör överväga att använda den |
  | MariaDB (molnet) | 10,4 | 10,6 |                                                          |
  | MySQL | 8,0 | -/-/ |                                                          |
  | Disposition | 1.9.2 | 2,2 |                                                          |
  | Elasticsearch | 7,10 | 7,17 |                                                          |

- **Tillägg och tredjepartsmoduler** - Använd den här tabellmallen för att få en förståelse för statusen för dina tillägg och anpassningar, så att du kan fatta strategiska beslut och definiera åtgärder. Detta är en möjlighet att ersätta tillägg som kan vara inbyggda i Adobe Commerce för att minimera komplexiteten i ditt projekt. Använd kommandot `bin/magento module:status` om du vill visa en lista med moduler och tillägg.

  | # | Modulnamn för tillägg/<br> | Kompositpaket | Leverantör | Aktuell version | Funktionalitet | Kompatibel med den senaste<br>Commerce-versionen? | Problem | Inbyggt i Commerce? | Åtgärd | Anteckningar |
  |---|-----------------------------|------------------------------------|-------------|-------------------|-----------------------|---------------------------------------------|--------------------------------------------------|---------------------|-------------------------|-------|
  | 1 | Tilläggsnamn och länk | extension/<br>extensionx-magento-2 | Leverantörsnamn | Version installerad | Affärskrav | Ja/Nej | Lista identifierade problem som uppstår med det här tillägget | Ja/Nej | Behåll/Ersätt/<br>Ta bort |       |

- **Anpassade moduler** - På samma sätt som modultabellen från tredje part hjälper den här mallen dig att spåra och förstå status och vilka åtgärder som krävs för att uppgradera anpassade moduler.

  | # | Modulnamn | Funktionalitet | Obligatoriskt? | Inbyggt i Commerce? | Åtgärd | Anteckningar |
  |---|--------------|-----------------------|-----------|---------------------|---------------------|-------|
  | 1 | Modulnamn | Affärskrav | Ja/Nej | Ja/Nej | Behåll/Ersätt/Ta bort |       |

- **Kompositpaket och beroenden i Composer.json som kräver en uppdatering.**

Dessutom kan partners delta i [betaversioner av Adobe Commerce](../../release/beta.md) och använda förhandsversioner för att få tidig åtkomst till koden för en kommande release. Genom att få tillgång till koden i ett tidigt skede kan utvecklarna förbereda sig för att slutföra uppgraderingen till datumet General Availability (GA). Beta-koden släpps vanligtvis fem veckor före GA-datumet och förhandsversioner släpps två veckor i förväg.

## Utveckling och kvalitetssäkring

Testning är den fas av en uppgradering som kräver mest tid. Därför bör denna process vara så automatiserad som möjligt. _[Programtestningsguiden](https://developer.adobe.com/commerce/testing/guide/)_ innehåller information om hur du konfigurerar och använder plattforms- och systemtestningsverktyg för snabbare kvalitetskontroll. Använd en testmiljö för att testa och validera uppgraderingen innan du går över till produktion.

## UAT och förberedelse för att starta

UAT är ett av de sista stegen i uppgraderingen som kräver granskning och validering av webbplatsen. Du måste också bestämma när du ska distribuera och om du behöver en underhållssida. Planera kundprocesser och tredjepartsmeddelanden.

I takt med att driftsättningsdatumet närmar sig är det viktigt att kunna kommunicera. Om fler människor känner till förändringen i horisonten, hur den påverkar dem och hur de måste ta itu med den, är det troligare att ni får en framgångsrik start. Var inte rädd för att överkommunicera varje steg på vägen - det ökar sannolikheten för att alla inblandade kommer att glöda recensioner när du väl är klar!

## Starta

Slutför uppgraderingen genom att distribuera till produktion och uppdatera tillägg. Kontrollera att du testar kritiska banflöden med simulerade order. Läs de här [bästa metoderna](../prepare/best-practices.md) om du vill ha tips om hur du startar med minimala problem.

Följ er kommunikationsplan och se till att alla intressenter är medvetna om uppgraderingen och är fullt utbildade för att stödja den.

Till sist kan du diskutera med teamet för att ta reda på vad de lärt sig och fallgropar. Med det här perspektivet kan du förbättra processen nästa gång.

## Post-Launch

När webbplatsen har startats bör du kontrollera dina analysdata, Google Search Console och andra resurser så att du kan vara säker på att inga oväntade problem uppstår och att allt fungerar som förväntat.

Det är alltid en bra idé att hålla ett öga på prestanda med väldesignade övervakningsverktyg. Det finns många verktyg och verktyg för att övervaka webbplatsens prestanda, så se till att du väljer ett som passar bra ihop med din organisation. Vi rekommenderar att Adobe Commerce-kunder som använder vårt molninfrastrukturhanteringssystem utnyttjar tjänster som [New Relic](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/monitor/new-relic/new-relic-service.html) för att övervaka webbplatsens prestanda.
