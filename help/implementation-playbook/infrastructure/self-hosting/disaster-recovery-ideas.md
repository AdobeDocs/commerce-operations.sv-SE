---
title: Självvärdande Adobe Commerce katastrofåterställning
description: Lär dig mer om självvärdande idéer och koncept för katastrofåterställning och de bästa metoderna att tänka på.
landing-page-description: Lär dig några koncept och saker du bör tänka på när du är värd för Adobe Commerce på egen hand.
short-description: Lär dig strategier och koncept för katastrofåterställning för att själv vara värd för Adobe Commerce.
kt: 11420
doc-type: tutorial
audience: all
last-substantial-update: 2023-04-13T00:00:00Z
exl-id: cab6213b-da44-498f-b5c1-e7f89e95038e
feature: Install
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '1771'
ht-degree: 0%

---

# Självvärdande idéer om Adobe Commerce Disaster Recovery

Disaster Recovery för den här artikeln omfattar en misslyckad distribution. Även om hela processen kanske inte är densamma gäller liknande principer. En katastrof kan bero på en misslyckad produktionsdistribution, att servern inte svarar, att ett kryphål upptäcks och många andra scenarier. Om återställningsprocessen för en misslyckad distribution endast kräver två enkla steg kan det vara en mycket större utmaning att återställa från en utnyttjandeprocess. På grund av komplex miljö, variationer av värdtjänster och andra komplexa funktioner ger den här artikeln idéer och koncept, men du måste fortsätta undersökningen på egen hand. På så sätt kan du vara säker på att du utformar en strategi som passar dina affärsbehov.

## Rutinåterställning sker ofta

Öva, öva, öva. Det finns en anledning till att rutiner visas först i återställningslistan. Det är långt ifrån lätt att upprätta en återhämtningsplan, men aldrig genomföra den. Om du inte tränar tillräckligt är du benägen att råka ut för fel, missade steg och antagligen får en återställning att ta längre tid. Det är upp till dig och dina affärspartners att bestämma om ni ska återfinna era rutiner. Det kan räcka att göra återställningsprocessen till ett årligt event, men en djupgående konversation med beslutsfattarna i ditt företag bör innehålla flera viktiga ämnen. Dessa ämnen hjälper dem att förstå varför övning är viktigt och bör förväntas. Här är några ämnen som hjälper dig att komma igång med konversationen:

* Practicing minskar den faktiska driftstoppen när en händelse inträffar i verkligheten. Om en torr körning tar ned platsen i en timme per år kan det minska den faktiska driftstoppen för en händelse med flera timmar. Det är inte ovanligt att en återställning av en plats tar åtta timmar eller längre. Genom att öva på den här händelsen ofta kan du minska tiden som varje fas tar och du kan återskapa snabbare.
* Schemalagda driftavbrott för dessa övningar kan sammanfalla med serverkorrigeringar, lagerjusteringar eller annat som bör göras regelbundet.
* Använd olika scenarier istället för samma. Ta en stund då du vill återställa data från ett tidigare datum. Detta inkluderar t.ex. att söka efter och använda en arkiverad kopia av databasen och återställa koden så att den matchar datumet. En enklare återställning kan vara en återställning från misslyckad distribution, där du helt enkelt måste återställa den tidigare implementeringen.
* Kontrollera att återställningsprocessen fungerar, ibland kan arkiverade databaser bli skadade. På så sätt säkerställer programmet att allt kan återställas och fungera. Det tar tid att hitta och återställa en gammal databas. Det bör vara känt hur lång tid den här delen av processen kan ta.
* Verifiera att alla ändringar i konfigurationer dokumenteras. Detta garanterar att alla återställningar från en äldre databas får nya konfigurationsändringar att fungera. Om din API-nyckel till exempel har ändrats till din betalningsprocessor de senaste dagarna. Genom att ha en bra process för ändringshantering kan du hitta de här viktiga uppdateringarna så att processen blir som planerat.

## DB-säkerhetskopiering

Säkerhetskopieringar av databaser bör vara relativt regelbundna. Det är inte ovanligt att du tar bilder varje timme, dag, vecka och månad. Säkerhetskopiorna bör så småningom flyttas till långsiktig lagring. Den här långsiktiga lagringen kan inträffa när affärs- eller teknikteamet beslutar att det finns tillräckligt med tid för att det troligtvis inte längre behövs en snabb återställning från dem. En återställning från en långvarig lagring lägger till tid i återställningsprocessen, så försiktighet bör iakttas när beslut om när detta bör ske. Databassäkerhetskopieringarna bör automatiseras och inte vara beroende av mänsklig interaktion. Detta garanterar att du har tillräckligt många av dem för en säker och förutsägbar återställningsprocess. Detta bidrar också till all kriminalteknisk verksamhet, om sådan verksamhet är nödvändig, är genomförbar och tillförlitlig. Du kan behöva göra en kriminalteknisk undersökning efter att ett kryphål har upptäckts, eller när du försöker diagnostisera när ett kreditkortsbedrägeri har inträffat eller till och med när någon har anslutit till din webbplats. Det finns ingen gräns för hur du använder dessa säkerhetskopior, men att ha bra kontroll över säkerhetskopieringen är din besparande respons när du faktiskt behöver den.

Följande är ett exempel på en datalagringspolicy:

* Var 8:e timme. Säkerhetskopiorna ska vara lättillgängliga.
* Dagliga säkerhetskopieringar under de senaste sju dagarna och bör vara lättillgängliga. En kopia av dem kan vara en kandidat för att flyttas utanför webbplatsen.
* Veckovisa säkerhetskopieringar under de senaste fyra veckorna överväg att flytta utomhus.
* månadsvis säkerhetskopiering de senaste tre månaderna har flyttats till en annan plats.
* Äldre säkerhetskopior flyttas till långsiktig lagring utanför webbplatsen.

## Infrastruktur som kod

Den här metoden innebär att du har verktyg och kod på plats för att återskapa delar eller hela infrastrukturen för ditt projekt. Detta kan behövas om en server har problem och måste tas ur bruk. Du kan snabbt ansluta en ny server, driftsätta koden, göra alla PHP-, Nginx- och Apache-konfigurationer och vad som helst, vilket automatiskt innebär färre driftavbrott. Även väldokumenterade steg i en körningsbok är enklare att ställa in, för att köra stegen tar det mycket längre tid. Tänk också på det mänskliga fel som kan uppstå när du är stressad för att få en webbplats som inte svarar online igen.

## Sekundär databas

Det kan vara praktiskt att använda en sekundär databas av några anledningar:

* Varma vänteläge om det uppstår fel på den primära enheten
* Tillåt färdiga begäranden från programmet
* Tillåt att mysqldump inträffar och låt vanliga transaktioner utföras utan att databasen låses
* Tillåter åtkomst av data från en extern datakälla utan att minska webbplatsernas möjligheter att hantera information på kundens begäran.

Den sekundära databasen kan användas som en `warm standby`. Detta kan bli aktuellt när du funderar på hur du ska återställa efter ett primärt databasfel. Att uppgradera den sekundära databasen till primär är är mindre komplicerat än att återskapa och återställa en databas till en nyligen skapad Mysql-instans. Detta minskar de faktiska driftstoppen under en återställning.

Det finns möjlighet att dirigera vissa av förfrågningarna till den sekundära databasen. Om den här metoden används bör du göra den sekundära databasen skrivskyddad. Genom att tillåta att Adobe Commerce-programmet använder den här sekundära databasen för läsåtgärder hjälper till genom att ta några av läsförfrågningarna och tillåta den sekundära databasen att svara. Den här ändringen står dock endast för 30-50 % av alla förfrågningar, men all belastning du kan ta bort från den primära databasen är en vinst.

## Skapa en distributionsplan som innehåller en återställning

Varje distribution bör innehålla en återställningsplan. Ja, varje driftsättning. Om du tänker göra det blir du aldrig förvånad och är redo för den dåliga händelsen. Ibland kan de mest enkla koduppdateringarna misslyckas av någon anledning.

Tänk på den här verkliga historien om ett team som implementerade en liten, enkel pull-begäran för att utföra en schemaändring i databasen. Allt eftersom driftsättningen gick från 1 minut till 5, sedan 10, blev teamet mer bekymrat. Det de inte kunde verifiera och överväga fram till den här punkten var eventuella avvikelser från produktionsdatabasen jämfört med mellanlagringsdatabasen. De hade som praxis att ta bort alla kunddata när de uppdaterade mellanlagringsmiljön med en kopia av produktionen. Detta innebar att all testning och kvalitetskontroll före detta reflekterade driftsättningen skulle ta några minuter att slutföra. I verkligheten hade de över 20 miljoner kunder och den här lilla schemaförändringen tog en exceptionellt lång tid att slutföra. Eftersom de inte hade någon aning om hur lång tid det här faktiskt tog tvingades de avsluta mysql-processen och återställa distributionen.

Det tar bara några minuter att förbereda en återställningsprocess för en distribution eftersom den övergripande processen kommer att bli densamma. Du bör dock ta dig tid att dokumentera exakt vad du implementerat och återställa HEAD i Git-databasen till. Du bör dokumentera exakt vilken databasögonblicksbild som ska användas eller var du ska hitta den aktuella om den alltid finns på samma plats. Har definierade tider när statusen för distributionen måste diskuteras och när den ska börja gälla automatiskt. Om en distribution tar längre tid än 15 minuter frågar du projektledaren och andra intressenter om det ska fortsätta. Kör återställningsprocessen automatiskt och meddela alla intressenter om processen tar 45 minuter, oavsett om projektledaren och arkitekten tvekar.

Se till att flera personer är involverade i hela processen och i varje fas. Att låta utvecklare på mellannivå granska driftsättningsprocessen, är en återställningsprocedur och plats för filer ett bra sätt att få dem involverade. De kommer så småningom att utföra de olika stegen, så att de förstår hela processen är avgörande för att lyckas på lång sikt. Se till att alla har behörighet att avbryta en distribution. Att ge ditt team så mycket att säga ger både makt och belöning. Om en eftergymnasial utvecklare verkligen känner att något saknas, borde de känna sig tvungna att tala upp och låta sin försiktighet höras. Låt arkitekten och projektledarna bekräfta eller mildra deras rädsla. Det är viktigt att ha ett starkt team som håller utkik efter projektet och håller koll på felfria driftsättningar.

## Verifiera åtkomst till domännamnshantering, DMS, SSL, WAF

Eftersom domännamn upphör att gälla kan DNS-poster ändras av misstag, SSL-certifikat kan upphöra att gälla och mycket mer. Se till att du har möjlighet att logga in och verifiera att anslutningen bör ske ofta. Genom att göra den här enkla kontrollen varje kvartal kan du vara säker på att du vet exakt var det finns, särskilt i en nödsituation. Anta inte att din DNS hanteras i din registrator bara för att ta reda på att du har det hanterat i Amazon. Posterna används inte så ofta, så det är mycket troligt att du glömmer bort var de finns. Lita inte på skriven dokumentation för enbart användarnamn och lösenord. Logga in på var och en och kontrollera att de konfigurationer du söker verkligen hanteras där. Alltför ofta ändras saker under ledning av omsättningen eller företagsförvärv och bara en person vet vad som hände, eftersom det var de som gjorde uppdateringen. De var inte medvetna om att du förlitade dig på ett delat orddokument för att ange plats, användarnamn och lösenord. Hitta en kontrollprocess som passar både dig och din organisation, men att göra detta var tredje till sjätte månad är en bra startpunkt.

{{$include /help/_includes/hosting-related-links.md}}
