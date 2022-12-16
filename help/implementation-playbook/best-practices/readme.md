---
source-git-commit: aaf174e5d895ebc60d4937b0214e23a559532942
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---
# God praxis: Arbetsflöde för att skapa innehåll

Det här dokumentets syfte är att detaljgranska arbetsflödet som användare måste följa för att begära innehåll med metodtips.

## Vem kan skapa en förfrågan?

Det finns två grupper av intressenter som kan göra en begäran, inklusive, men inte begränsat till:

- Extern: Partners
- Intern: CTAG (Customer Technical Advisory Group), Customer Support, Customer Success, Engineering Teams

## Hur skapar jag en förfrågan?

Interna intressenter måste göra förfrågningar genom att öppna ett Jira-problem i COMDOX-projektet. Externa intressenter måste göra förfrågningar genom att öppna ett GitHub-problem i den här databasen. Intressenter kan begära följande:

- Begär att nytt innehåll ska läggas till
- Begär redigeringar av innehåll som redan är publicerat
- Dela eget innehåll som ska publiceras

## Vilken är den övergripande processen?

Interna intressenter måste öppna en Jira-biljett i Commerce Documentation-projektet (COMDOX) och ge fullständig information, inklusive att fylla i en mall. Dessa detaljer hjälper teamet att prioritera förfrågningar om innehåll.

Teamet övervakar regelbundet förfrågningar i eftersläpningen för att avgöra prioriteten och om implementeringens spelbok är den bästa platsen för förfrågan. Teamet kan bestämma att istället för att skapa ett nytt ämne ska det begärda innehållet läggas till i den befintliga produktdokumentationen på Experience League eller Adobe Developer webbplats.

Om det inte finns tillräckligt med information i en begäran kommer teamet att be den som gjorde begäran att fylla i alla motsvarande fält. Om den som gjorde begäran inte svarar inom X antal dagar stänger teamet begäran.
När teamet har validerat och prioriterat begäran är nästa steg att skapa ämnet. Det kan innebära att du antingen anpassar innehåll till .md-format eller skapar artikeln från grunden.

Innehållet granskas och redigeras när ämnen skapas. Granskningsprocessen sker genom GitHub-pull-begäranden. Allt innehåll måste gå igenom redaktionell granskning. Teknisk granskning är valfri och beror på innehållet. Om ingen teknisk granskning behövs fortsätter processen endast med en redaktionell granskning. Den här processen kan ta flera iterationer tills innehållet har godkänts.

När en artikel har godkänts sammanfogar nästa steg den med produktionsgrenen. Sammanfogningen ska göras av författaren. Ämnet kan publiceras omedelbart eller vänta på att nästa publiceringsjobb ska köras, vilket publicerar alla godkända och sammanfogade ämnen.

Vi kommer att visa ett nytt avsnitt på startsidan för Bästa metoder på Experience League för att hjälpa användare att hålla sig uppdaterade med nyligen publicerade ämnen, så att de inte behöver navigera mellan olika sidor och portaler för att hitta relevant information av intresse. Vi kommer också att främja innehåll i befintliga kanaler, som marknadsföring och intern kommunikation.

## Eftersläpning och kanban Board

För att undvika dubbelarbete bör begäranden som har skapats och prioriterats vara synliga i eftersläpningen. Användarna uppmuntras att delta i omröstningssystemet i Jira för att rösta på förfrågningar som de anser nödvändiga eller relevanta. Detta kommer också att vara en bra indikator för gruppen på vilken typ av innehåll som förväntas av intressenter. Begäranden om prioritering och granskning som väntar visas i eftersläpningen tills de flyttas till aktiva banor i Kanban-styrelsen.

Kanban-tavlan kan nås av interna användare för att visa (och/eller övervaka) vilket innehåll som bearbetas och förloppet. Endast aktiva förfrågningar visas på den här anslagstavlan.
