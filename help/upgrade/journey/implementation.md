---
title: Implementering av uppgradering
description: Läs om de olika faserna i uppgraderingsimplementeringen för Adobe Commerce- och Magento Open Source-projekt.
source-git-commit: bbc412f1ceafaa557d223aabfd4b2a381d6ab04a
workflow-type: tm+mt
source-wordcount: '883'
ht-degree: 1%

---


# Implementering av uppgradering

Uppgraderingsimplementeringen består av fem faser:

- Uppgraderingsanalys
- Utveckling och kvalitetssäkring
- Testning av användargodkännande (UAT) och förberedelse för att starta
- Starta
- Efter start

## Uppgraderingsanalys

Analys är enligt andra ord den viktigaste delen i uppgraderingsprocessen. En väl utförd analys sparar tid och begränsar antalet överraskningar i framtiden. Resultatet av den här fasen bör vara en detaljerad uppgraderingskontrolllista och ett dokument med alla beroenden.

Här följer några punkter som du kanske vill ta med i en grundlig analys:

- **Omfattning av målrelease**—Dokumentation på [Commerce DevDocs](https://devdocs.magento.com) och information från webbinarier om partnerreleaser innehåller all information du behöver veta om måluppgraderingen.

- **Resultat av verktyget Kompatibilitet för uppgradering**- Med det här verktyget kan du uppgradera snabbare och enklare genom att jämföra den aktuella koden med målversionens kod och ta fram en rapport över alla problem som behöver åtgärdas. Se [Kompatibilitetsverktyg för uppgradering](../upgrade-compatibility-tool/overview.md). Bland huvuduppgifterna i rapporten finns:

   - Aktuell installerad version
   - Uppgradera målversion
   - Antal och information om kritiska fel som påträffats

- Uppgraderar tjänster som stöder målversion. Använd följande tabellmall för att mappa ut vilka tjänster du måste uppgradera. Använd [systemkrav](https://devdocs.magento.com/guides/v2.4/install-gde/system-requirements.html) för att avgöra vad som ska läggas till i _Uppgradera till_ kolumn.


   | Tjänst | Aktuell version | Uppgradera till | Anteckningar |
   |-----------------|-----------------|------------|----------------------------------------------------------|
   | PHP | 7.2.33 | 8.1 |  |
   | Redis | 5.05 | 6.0 |  |
   | KaninMQ | 3.7 | 3.8 | Används inte just nu, men vi bör överväga att använda den |
   | MariaDB (molnet) | 10.2.33 | 10.4 |  |
   | MySQL | 8.0 |  |  |
   | Disposition | 1.9.2 | 2.0 |  |
   | Elasticsearch | 7.7 | 7.10 |  |

- **Tillägg och tredjepartsmoduler**- Använd den här tabellmallen för att få en förståelse för status för tillägg och anpassningar, så att du kan fatta strategiska beslut och definiera åtgärder. Detta är en möjlighet att ersätta tillägg som kan vara inbyggda i Adobe Commerce eller Magento Open Source för att minimera komplexiteten i ditt projekt. Använd `bin/magento module:status` om du vill visa en lista med moduler och tillägg.

   | # | Tillägg/<br>modulnamn | Kompositpaket | Leverantör | Aktuell version | Funktionalitet | Kompatibel med den senaste<br>Handelsversion? | Problem | Inbyggt i Commerce? | Åtgärd | Anteckningar |
   |---|-----------------------------|------------------------------------|-------------|-------------------|-----------------------|---------------------------------------------|--------------------------------------------------|---------------------|-------------------------|-------|
   | 1 | Tilläggsnamn och länk | extension/<br>extensionx-magento-2 | Leverantörsnamn | Version installerad | Affärskrav | Ja/Nej | Lista identifierade problem som uppstår med det här tillägget | Ja/Nej | Behåll/Ersätt/<br>Ta bort |  |

- **Anpassade moduler**- På samma sätt som modultabellen från tredje part kan du med den här mallen spåra och förstå status och vilka åtgärder som krävs för uppgradering av anpassade moduler.

   | # | Modulnamn | Funktionalitet | Obligatoriskt? | Inbyggt i Commerce? | Åtgärd | Anteckningar |
   |---|--------------|-----------------------|-----------|---------------------|---------------------|-------|
   | 1 | Modulnamn | Affärskrav | Ja/Nej | Ja/Nej | Behåll/Ersätt/Ta bort |  |

- **Composer-paket och beroenden i Composer.json som kräver en uppdatering.**

Dessutom kan partners delta i [Adobe Commerce Beta Program](https://devdocs.magento.com/release/beta-program.html) och använda förhandsversioner för att få tidig åtkomst till koden för en kommande release. Genom att få tillgång till koden i ett tidigt skede kan utvecklarna förbereda sig för att slutföra uppgraderingen till datumet General Availability (GA). Betakoden släpps vanligtvis fem veckor före GA-datumet och förhandsversioner släpps två veckor i förväg. För version 2.4.4 började Adobe lansera betakod fem månader före GA-datumet (8 mars 2022), så partners kan börja förbereda sig för uppgraderingen nu senast [registrera sig för programmet](https://community.magento.com/t5/Magento-DevBlog/BREAKING-NEWS-2-4-4-beta-releases-are-coming-soon/ba-p/484310).

## Utveckling och kvalitetssäkring

Testning är den fas av en uppgradering som kräver mest tid. Därför bör denna process vara så automatiserad som möjligt. The _[Programtestguide](https://devdocs.magento.com/guides/v2.4/test/testing.html)_ innehåller information om hur du konfigurerar och använder plattforms- och systemtestverktyg för snabbare kvalitetskontroll. Använd en testmiljö för att testa och validera uppgraderingen innan du går över till produktion.

## UAT och förberedelse för att starta

UAT är ett av de sista stegen i uppgraderingen som kräver granskning och validering av webbplatsen. Du måste också bestämma när du ska distribuera och om du behöver en underhållssida. Planera kundprocesser och tredjepartsmeddelanden.

I takt med att driftsättningsdatumet närmar sig är det viktigt med kommunikation. Om fler människor känner till förändringen i horisonten, hur den påverkar dem och hur de måste ta itu med den, är det troligare att ni får en framgångsrik start. Var inte rädd för att överkommunicera varje steg på vägen - det ökar sannolikheten för att alla inblandade kommer att glöda recensioner när du väl är klar!

## Starta

Slutför uppgraderingen genom att distribuera till produktion och uppdatera tillägg. Kontrollera att du testar kritiska banflöden med simulerade order. Kolla in de här [bästa praxis](../prepare/best-practices.md) om du vill få tips om hur du startar med minimala problem.

Följ er kommunikationsplan och se till att alla intressenter är medvetna om uppgraderingen och är fullt utbildade för att stödja den.

Till sist kan du diskutera med teamet för att ta reda på vad de lärt sig och fallgropar. Med det här perspektivet kan du förbättra processen nästa gång.

## Efter start

När webbplatsen har startats bör du kontrollera dina analysdata, Google Search Console och andra resurser så att du kan vara säker på att inga oväntade problem uppstår och att allt fungerar som förväntat.

Det är alltid en bra idé att hålla ett öga på prestanda med väldesignade övervakningsverktyg. Det finns många verktyg och verktyg för att övervaka webbplatsens prestanda, så se till att du väljer ett som passar bra ihop med din organisation. Vi rekommenderar att Adobe Commerce-kunder som använder vårt molninfrastrukturhanteringssystem drar nytta av tjänster som [New Relic](https://devdocs.magento.com/cloud/project/new-relic.html) för att övervaka webbplatsens prestanda.
