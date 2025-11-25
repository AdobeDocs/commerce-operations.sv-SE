---
source-git-commit: 84a20012a81278cc95587ec14281b05330261687
workflow-type: tm+mt
source-wordcount: '595'
ht-degree: 0%

---
# God praxis: Arbetsflöde för att skapa innehåll

Det här dokumentet beskriver användararbetsflödet för att begära ändringar eller tillägg av *[Best Practices](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/phases.html* -innehållet i *Adobe Commerce Implementation Playbook*.

## Vem kan skapa en förfrågan?

Adobe accepterar förfrågningar från både interna och externa intressenter, inklusive, men inte begränsat till, personer i följande grupper:

- Adobe Partners
- Adobe CTAG (Customer Technical Advisory Group), kundsupport, Customer Success, Engineering Teams

## Hur skapar jag en förfrågan?

**Interna intressenter** kan skicka begäranden genom att öppna ett Jira-problem i COMDOX-projektet. **Externa intressenter** kan skicka begäranden genom att öppna ett [GitHub-problem](https://github.com/AdobeDocs/commerce-operations.en/issues/new/choose) i den här databasen.

Du kan skicka in följande typer av förfrågningar:

- Ideas för nytt innehåll
- Uppdateringar av innehåll som redan är publicerat
- Publicera nytt innehåll som tillhandahålls av intressenter eller communityn

## Vilken är den övergripande processen?


**Skapa en Jira-biljett eller ett Jira-problem** - Interna intressenter skapar en Jira-biljett i COMDOX-projektet. Externa intressenter skickar in ett GitHub-problem. Inkludera fullständig information i Jira- eller [GitHub-utgåvan](https://github.com/AdobeDocs/commerce-operations.en/issues/new/choose) för att hjälpa teamet att förstå kontexten och prioritera begäran.

**Adobe projektteam utvärderar och prioriterar begäran** - teamet övervakar regelbundet begäranden för att fastställa prioritet och utvärdera de begärda ändringarna för att kunna inkludera dem i Implementeringens spelningsboksmetodtips. Teamet kan till exempel fastställa att istället för att skapa ett nytt avsnitt om bästa praxis ska det begärda innehållet läggas till i den befintliga produktdokumentationen på Experience League- eller Adobe Developer-webbplatsen.

Om det inte finns tillräckligt med information i en begäran begär teamet ytterligare information från den som gjorde begäran. Om den som gjorde begäran inte svarar inom 14 dagar stänger teamet begäran.

**Skapa eller uppdatera innehåll**-Skapandet av innehåll slutförs enligt processen som beskrivs i [Adobe Experience League Contributor Guide](https://experienceleague.adobe.com/docs/contributor/contributor-guide/introduction.html). Beroende på begäran kan det vara bra att konvertera nytt innehåll till markering, skapa ett ämne eller uppdatera ett befintligt ämne.

**Granskning, godkännande och publicering**-Innehåll granskas och redigeras när ämnen skapas eller uppdateras med [GitHub-pull-begäranden](https://experienceleague.adobe.com/docs/contributor/contributor-guide/setup/git-fundamentals.html#pull-requests). Allt innehåll måste gå igenom redaktionell granskning. Teknisk granskning är valfri och beror på innehållet. Om ingen teknisk granskning behövs fortsätter processen endast med en redaktionell granskning. Den här processen kan ta flera iterationer tills innehållet har godkänts.

När en artikel har godkänts kan pull-begäran sammanfogas med produktionsgrenen. Sammanfogningen ska göras av författaren. När ett ämne har sammanfogats kan det publiceras till produktion omedelbart med hjälp av en manuell process, eller automatiskt nästa gång publiceringsjobbet körs. Publiceringsjobb körs vanligtvis varannan timme.

**Meddelande om nytt innehåll**-Adobe innehåller ett avsnitt om *Nyheter* i [Översikt över bästa praxis](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/phases.html) som håller användarna informerade om nyligen publicerade eller uppdaterade ämnen. Adobe kommer också att främja nytt innehåll enligt Best Practices med hjälp av befintliga kanaler, som marknadsföring och intern kommunikation.

## Eftersläpning och kanban Board

För att undvika duplicering kommer förfrågningar som har skapats och prioriterats att visas i Jiras eftersläpning i COMDOX-projektet och [GitHub Issues Project](https://github.com/orgs/AdobeDocs/projects/6/views/1) . Interna intressenter uppmuntras att delta i omröstningssystemet i Jira för att rösta om förfrågningar som de anser nödvändiga eller relevanta. Röstningen hjälper även projektteamet med bästa praxis att förstå vilken typ av innehåll som intressenter förväntar sig och vilket värde de har. Begäranden som väntar på att prioriteras och granskas visas i eftersläpningen tills de flyttas till de aktiva körningarna i Kanban-tavlan.

Kanban-tavlan kan nås av interna användare för att visa (och/eller övervaka) vilket innehåll som bearbetas och förloppet. Endast aktiva förfrågningar visas på den här styrelsen.
