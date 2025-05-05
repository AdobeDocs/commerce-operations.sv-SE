---
title: Svara på en säkerhetsincident
description: Hantera säkerhetsincidenter genom att följa bästa praxis för att hantera och åtgärda säkerhetsproblem som påverkar webbplatsens tillgänglighet och prestanda.
feature: Best Practices
exl-id: 77275d37-4f1d-462d-ba11-29432791da6a
source-git-commit: e63f68dd469564e70269154810cbfbd95d2b2e57
workflow-type: tm+mt
source-wordcount: '1172'
ht-degree: 0%

---

# Bästa tillvägagångssätt för att hantera säkerhetstillbud

I följande artikel sammanfattas de effektivaste strategierna för att hantera säkerhetsincidenter och åtgärda problem som påverkar tillgängligheten, tillförlitligheten och prestandan för Adobe Commerce-webbplatser.

Om du följer dessa standarder kan du förhindra obehörig åtkomst och skadliga programattacker. Om en säkerhetsincident inträffar hjälper dessa bästa metoder dig att förbereda dig för en omedelbar reaktion, utföra en analys av grundorsaken och hantera reparationsprocessen för att återställa normala åtgärder.

>[!TIP]
>
>Adobe har upptäckt att de flesta säkerhetsincidenter inträffar när hotskådespelare drar nytta av befintliga, ej patchade säkerhetsluckor, dåliga lösenord och svaga ägar- och behörighetsinställningar i Commerce program- och infrastrukturkonfiguration. Minimera antalet säkerhetstillbud genom att granska och följa de bästa säkerhetsrutinerna för Adobe när du konfigurerar, konfigurerar och uppdaterar Adobe Commerce-installationer. Se [Skydda din Commerce-webbplats och infrastruktur](../launch/security-best-practices.md).


## Berörda produkter och versioner

[Alla versioner som stöds](../../../release/versions.md) av:

- Adobe Commerce i molninfrastruktur
- Adobe Commerce lokalt

## Svara på en incident

Om du misstänker att ditt Adobe Commerce-projekt för molninfrastruktur påverkas av en säkerhetsincident är följande viktiga första steg:

- Granska åtkomst till alla administratörsanvändarkonton
- Aktivera avancerade MFA-kontroller (Multi-factor authentication)
- Bevara kritiska loggar
- Granska säkerhetsuppgraderingar för din version av Adobe Commerce.

Fler rekommendationer finns nedan.

## Vidta omedelbara åtgärder i händelse av en attack

I den olyckliga händelse att sajten inte fungerar är följande viktiga rekommendationer att följa:

- Engagera systemintegratören och lämplig säkerhetspersonal för att genomföra utredningar och åtgärder.

- Bestäm omfattningen av attacken:
   - Användes kreditkortsinformation?
   - Vilken information stals?
   - Hur lång tid har gått sedan kompromissen?
   - Krypterades informationen?

- Försök att hitta attackvektorn för att avgöra när och hur platsen komprometterades genom att granska serverloggfiler och filändringar.

   - Under vissa omständigheter kan det vara tillrådligt att svepa och installera om allt eller skapa en ny instans om det är en virtuell värdtjänst. Skadlig kod kan döljas på en plats som inte misstänks, bara i väntan på att återställas.

   - Ta bort alla onödiga filer. Installera sedan om nödvändiga filer från en känd, ren källa. Du kan till exempel installera om med hjälp av filer från versionskontrollsystemet eller från de ursprungliga distributionsfilerna från Adobe.

   - Återställ alla autentiseringsuppgifter, inklusive databas-, filåtkomst-, betalnings- och leveransintegreringar, webbtjänster och administratörsinloggning. Återställ även alla integrerings- och API-nycklar och konton som kan användas för att attackera systemet.

## Analysera en incident

Det första steget i incidentanalysen är att samla in så många fakta som möjligt, så snabbt du kan. Genom att samla in information kring incidenten kan det bli lättare att fastställa den potentiella orsaken till incidenten. Adobe Commerce tillhandahåller verktygen nedan som kan underlätta incidentanalysen.

- [Granska administratörsåtgärdsloggar](https://experienceleague.adobe.com/docs/commerce-admin/systems/action-logs/action-log-report.html?lang=sv-SE).

  Rapporten Åtgärdsloggar innehåller en detaljerad beskrivning av alla administratörsåtgärder som har aktiverats för loggning. Varje post är tidstämplad och registrerar användarens IP-adress och namn. Logginformationen innehåller administratörsanvändardata och relaterade ändringar som gjordes under åtgärden.

- Analysera händelser med verktyget [Observation for Adobe Commerce](../../../tools/observation-for-adobe-commerce/intro.md).

  Med verktyget Observation for Adobe Commerce kan du analysera komplexa problem för att identifiera rotorsaker. Istället för att spåra olika data kan ni lägga tid på att korrelera händelser och fel för att få djupare insikter i orsakerna till flaskhalsar i prestandan.

  Använd fliken **Säkerhet** i verktyget för att få en tydlig bild av potentiella säkerhetsproblem som hjälper till att identifiera rotorsaker och se till att webbplatserna fungerar optimalt.

- Analysera loggar med [New Relic-loggar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/monitor/new-relic/new-relic-service.html?lang=sv-SE)

  Adobe Commerce i molninfrastrukturproprojekt innehåller tjänsten [New Relic Logs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/monitor/new-relic/log-management.html?lang=sv-SE). Tjänsten är förkonfigurerad för att samla alla loggdata från dina miljö för förproduktion och produktion och visa dem på en central kontrollpanel för logghantering där du kan söka efter och visualisera aggregerade data.

  För andra Commerce-projekt kan du konfigurera och använda tjänsten [New Relic Logs](https://docs.newrelic.com/docs/logs/get-started/get-started-log-management/) för att utföra följande uppgifter:
   - Använd [New Relic-frågor](https://docs.newrelic.com/docs/logs/new-relic-logs/ui-data/query-syntax-logs) för att söka efter aggregerade loggdata.
   - Visualisera loggdata via programmet New Relic Logs.

## Granskningskonton, kod och databas

Granska Commerce Admin och användarkonton, programkod och databaskonfiguration samt loggar för att identifiera och åtgärda misstänkt kod och säkerställa säkerheten för konto-, webbplats- och databasåtkomst. Distribuera sedan om det behövs.

Fortsätt att noga övervaka webbplatsen efter incidenten eftersom många webbplatser på nytt komprometteras inom några timmar. Se till att logggranskningen och filintegritetsövervakningen sker kontinuerligt för att snabbt upptäcka tecken på nya kompromisser.

### Granska administratörens användarkonton

- [Granska administratörsanvändaråtkomst](https://experienceleague.adobe.com/docs/commerce-admin/systems/user-accounts/permissions-users-all.html?lang=sv-SE) - Ta bort gamla, oanvända eller misstänkta konton och rotera lösenord för alla administratörsanvändare.

- [Granska säkerhetsinställningarna för administratörer](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/security-admin.html?lang=sv-SE) - Verifiera att säkerhetsinställningarna för administratörer följer god säkerhetspraxis.

- [Granska användarkonton för Adobe Commerce i molninfrastrukturprojekt](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html?lang=sv-SE) - Ta bort gamla, oanvända eller misstänkta konton och rotera lösenord för alla användare i molnprojektadministratören. Kontrollera att kontosäkerhetsinställningarna är korrekt konfigurerade.

- [Granska SSH-nycklar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html?lang=sv-SE) för Adobe Commerce i molninfrastruktur - Granska, ta bort och rotera SSH-nycklar.

### Granskningskod

- Gå till konfigurationen [HTML för sidhuvud och sidfot](https://experienceleague.adobe.com/docs/commerce-admin/content-design/design/page-setup.html?lang=sv-SE) i Admin i alla omfångsnivåer, inklusive `website` och `store view`. Ta bort okänd JavaScript-kod från skript och formatmallar samt olika HTML-inställningar. Behåll endast identifierad kod som spårningsfragment.

- Jämför den aktuella produktionskodbasen med kodbasen som lagras i Version Control System (VCS).

- Karantän all misstänkt kod.

- Se till att det inte finns några kvar misstänkt kod genom att omdistribuera kodbasen till produktionsmiljön.

### Granska databaskonfiguration och loggar

- Granska alla lagrade procedurer för ändringar.

- Kontrollera att databasen bara är tillgänglig för Commerce-instansen.

- Kontrollera att det inte längre finns någon skadlig kod genom att skanna webbplatsen med offentligt tillgängliga skanningsverktyg för skadlig kod.

- Skydda administrationspanelen genom att ändra dess namn och verifiera att URL:erna för webbplatsen `app/etc/local.xml` och `var` inte är tillgängliga för alla.

- Fortsätt att noga övervaka webbplatsen efter incidenten eftersom många webbplatser på nytt komprometteras inom några timmar. Se till att logggranskningen och filintegritetsövervakningen sker kontinuerligt för att snabbt upptäcka tecken på nya kompromisser.

## Ta bort Google-varningar

Om Google har flaggat webbplatsen som innehåller skadlig kod begär du en granskning när webbplatsen har rensats. Det kan ta några dagar att granska webbplatser som infekterats med skadlig kod. När Google har fastställt att webbplatsen är ren bör varningar från sökresultaten och webbläsare försvinna inom 72 timmar. Se [Begär en granskning](https://web.dev/articles/request-a-review).

## Granska checklista för resultat av skadlig programvara

Om de allmänt tillgängliga verktygen för sökning efter skadlig kod bekräftar en skadlig kod-attack, bör du undersöka incidenten. Arbeta med lösningsintegratören för att rensa webbplatsen och följa den rekommenderade reparationsprocessen.

## Genomför ytterligare granskningar

När du hanterar sofistikerade attacker är det bästa sättet att agera att samarbeta med en erfaren utvecklare, en tredjepartsexpert eller en lösningsintegratör för att helt reparera webbplatsen och granska säkerhetsrutiner. Genom att samarbeta med erfarna säkerhetspersonal kan du säkerställa att omfattande och avancerade åtgärder vidtas för att säkerställa säkerheten för ditt företag och dess kunder.

## Ytterligare information

- [Rotorsaksanalysramverk](https://sansec.io/kb/incident-response/magento-root-cause-analysis).
