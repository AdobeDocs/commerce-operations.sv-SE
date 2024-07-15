---
title: Testtips för prestanda
description: Lär dig hur du ställer in nyckeltal för att starta din Adobe Commerce- och Adobe Experience Manager-lösning.
exl-id: 4b0d9c4f-e611-452d-a80f-27f82705935d
topic: Commerce, Performance
source-git-commit: 76ccc5aa8e5e3358dc52a88222fd0da7c4eb9ccb
workflow-type: tm+mt
source-wordcount: '1150'
ht-degree: 0%

---

# Tips för prestandatestning

För att utvärdera effekten av alla ändringar ovan bör grundliga prestandatestningar köras före driftsättning och före framtida större driftsättningar i produktionsmiljöerna. När du planerar din lasttestning är det viktigt att simulera konsumenttrafik i realtid så mycket som möjligt.

De resurskrävande områdena på AEM/CIF/Adobe Commerce-webbplatsen är de som inte är tillgängliga, till exempel utcheckningsprocessen och webbplatssökningen. Statisk, och därmed cachelagrad, sidbläddring, t.ex. för PDP (Producera Detail Pages) och PLP (Product Listing Pages), utgör merparten av trafiken till en e-handelsplats i allmänhet och därför bör skripten och scenarierna i testet återspegla detta för att mäta plattformens gränser.

Om du kör ett enda skript för ditt belastningstest som navigerar genom webbplatsen utan väntetid mellan stegen och alltid slutför utcheckningsprocessen varje gång ger det ingen tillförlitlig indikation på plattformens begränsningar, eftersom det inte är vad ett verkligt scenario skulle vara.

Att definiera KPI:er bör vara det första steget i prestandatestningsplanen: definiera mätvärden som du kan testa under det inledande testet, men sedan mäta igen i framtiden, och regelbundet efter att webbplatsen publicerats. Detta gör att du kan spåra prestanda för din webbplats över tid - före och efter start. Exempel på KPI:er som ska definieras kan vara:

- Genomsnittlig svarstid - tid till första byte eller sista byte
- Latens
- Byte/byte (Througput)
- Felfrekvens
- Beställningar per timme
- Sidvyer per timme
- Unika användare per timme (samtidiga kunder)

## Riktlinjer för Jmeter

Följande riktlinjer för hög nivå för Jmeter bör beaktas vid utvecklingen av AEM/CIF/Adobe Commerce-belastningstestning:

- Dela skriptet i konfigurerbara scenarier, som till exempel ska omfatta:
   - Öppna startsidan
   - Öppna kategorisida (PLP)
   - Visa enkla produkter (PDP) - 2 slingor i varje iteration
   - Visa konfigurerbara produkter - 2 slingor i varje iteration
      - Ange till exempel stegen ovan till 60 % av trafiken
   - Produktsökning
      - Ange till exempel att sökningen i katalogen ska vara 37 % av trafiken
   - Kundvagn och kassan
      - En användare som t.ex. fyller i delen för kundvagn och utcheckning i skriptet bör som standard använda en standardsats för konvertering av e-handelsplats på cirka 3 %
      - När utcheckningsflödet är ocachelagrat och vanligtvis en resurskrävande åtgärd, blir det orealistiskt bra att ange ett högt antal personer som slutför beställningar jämfört med antalet webbläsare på platsen, vilket skulle ge ett otillförlitligt resultat för den trafikvolym som din webbplats kan hantera.
- Rengör alla cacher före varje testkörning:
   - Cachen för AEM-dispatchern bör rensas helt
   - Adobe Commerce snabbcache och den interna cachen bör tömmas och rensas fullständigt - detta kan göras via cachekontrollen i Adobe Commerce Admin.
- Inkludera en rampperiod i Jmeter-testet: Om ingen rampperiod är inställd innebär det ingen gradvis ökning av trafiken och ingen möjlighet för webbplatsen att cachelagra någon av de vanligaste sidorna och komponenterna på sidan. I verkligheten skulle det vara ovanligt att all topptrafik anlände till en helt ocachelagrad plats på exakt samma tid, och därför bör en rampperiod inkluderas i Jmeter-testskript för att tillåta att cachen byggs upp som på en riktig e-handelsplats.
- En&quot;väntetid&quot; mellan varje steg i en iteration bör användas - i själva verket skulle användaren inte
direkt gå till nästa sida på webbplatsen under resan - det kan ta en stund medan användaren läser sidan och bestämmer sig för nästa åtgärd.
- Genom att ställa in trådgrupperna så att de slingrar sig oändligt, men under en fast tid på x (t.ex. 60 minuter), får de ett repeterbart test med median-svarstider som är jämförbara med tidigare testkörningar. Det innebär att efter uppstartsprocessen kommer det att finnas ett målantal virtuella användare som körs samtidigt och detta kommer att fortsätta för uppsättningens looptid.
- Mediantiden ska användas för att ge en förbättring/ minskning av den genomsnittliga svarstiden, inte medelvärdet. If
det finns flera edge-resultat som tar mycket längre tid än de andra resultaten, så detta skulle förvränga det här genomsnittliga resultatet, men det vi är intresserade av i slutanvändarens svarstid för de flesta användare, vilket bättre passar medianvärdet.
- Inbäddade resurser samlas inte in som standard i jmeter (t.ex. JS, CSS och andra resurser som laddas ned när en riktig besökssida besöks). Detta kan aktiveras, men bara för den domän du testar bör externa resursanrop fortfarande uteslutas (vi vill t.ex. inte inkludera svarstider från externa värdtjänster, t.ex. Google Analytics-kod eftersom vi inte har någon kontroll över dem).
- HTTP-cachehanteraren bör vara aktiverad, vilket gör att Jmeter kan cachelagra sidelement under en resa som
en verklig användarresa skulle göra under webbläsarens surfning av webbplatsen i sin egen webbläsare. Under hela resan på webbplatsen laddades användarens webbläsare bara ned den relaterade inbäddade resursen en gång och sedan cachelagrades dessa av användarens webbläsare. Om samma användare återgår till webbplatsen någon gång efter sitt ursprungliga besök kan det fortfarande vara cacheminnet som dessa resurser cachelagras.
- Avlyssnare bör hållas inom de faktiska belastningsprovningskörningarna (t.ex. &quot;Visa resultatträd&quot; och &quot;Sammanställningsrapport&quot;). Om detta ingår i den faktiska belastningsprovskörningen som inte är det grafiska användargränssnittet kan det påverka de prestandaresultat som rapporteras av Jmeter, eftersom resurser används under den verkliga provkörningen för att generera rapporterna. Dessa avlyssnare togs bort från testskriptet som skulle ersättas med en JTL-resultatfil, som sedan kan bearbetas med Jmeters rapportkontrollpanelsfunktion.
- En målsvarstid för utvärdering så att kontrollpanelrapportens &quot;Apdex-poäng&quot; kan användas som ett snabbt sätt att mäta effekten av förändringar på prestandan mellan testkörningar. Poängen i Apdex bygger på att en viss mängd personer kan komma åt webbplatsen inom en tolererbar tid. Om svarstiden överstiger en viss&quot;frustrerande&quot; mängd blir resultatet lägre. Du kan ange tider med parametrarna &quot;apdex_meet_threshold&quot; och &quot;apdex_tolerated_threshold&quot;.
- Ange ett målvärde för beställningar per timme som ska visas för företagsanvändare, inte för antalet virtuella användare. &quot;Virtuella användare&quot; kan vara ett komplext ämne för att förstå vad i verkligheten som testet mäter. Genom att beräkna konverteringsgraden, beställningarna per timme, den genomsnittliga tid en användare tillbringar på webbplatsen och att tänka tid mellan varje sidbelastning, kan branschstandardberäkningar användas för att presentera olika lasttestscenarier baserat på beställningar per timme som ska utföras.
- Slutligen bör Jmeter-testservern köras på en server som ligger geografiskt nära den plats där större delen av användartrafiken kommer från och där din molninfrastruktur finns - de här är förhoppningsvis desamma.
