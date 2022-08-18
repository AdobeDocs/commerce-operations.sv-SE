---
title: '"Så här använder du [!DNL Observation for Adobe Commerce] nerdlet"'
description: Lär dig använda [!DNL Observation for Adobe Commerce] nördlet.
source-git-commit: 69bcb755c3c1f9a820856ac69ce12eb85c686213
workflow-type: tm+mt
source-wordcount: '631'
ht-degree: 0%

---

# Så här använder du [!DNL Observation for Adobe Commerce] nerdlet

## Allmän metod för att se på frågor

Kontrollera tillstånd för miljöresurser:

* Undersök % av **[!UICONTROL Storage Free and MySQL % free storage by node]** bildrutor.

   * Följ länkarna i bildrutans sidhuvud om du ser lite lagringsutrymme.

* Undersök % av **[!UICONTROL free system memory and Swap memory free in bytes]** bildrutor.

   * Om dessa visar mycket små minneslägen kan de bidra till problem.

* Undersök **[!UICONTROL Alerts during the timeframe]** bildruta.

   * Adobe Commerce molninfrastruktur tillhandahåller [!DNL Managed alerts]. Du kan klicka på länken i sidhuvudet för att se [!DNL Support Knowledge Base] artiklar som hjälper dig att avgöra vilka åtgärder du ska vidta för att få specifika aviseringar.

* Undersök **[!UICONTROL CPU % by host]** bildruta: Om du har ett högt processorutnyttjande ska du kontrollera [!DNL Support Knowledge Base] artikel i ramens sidhuvud. Kontrollera också att import/export eller säkerhetskopiering av databaser inte sker under trafiktoppar.

* Kontrollera **[!UICONTROL Web Traffic volume compared to one week ago]** bildruta: Om trafiken är mycket högre än föregående vecka under samma period, kan det då förklaras (t.ex. en försäljningskampanj eller nya produkter som har marknadsförts)?
   * Om det inte går att förklara en trafikökning tittar du på den genomsnittliga svarstiden (millisekunder) för produktionsmiljön. Bidrar den högre trafiken till en annan svarstid än vad som är normalt? Expandera tidsramen för att se om det är en avvikelse.
   * Påverkar den ökade trafiken webbtransaktioner? Kontrollera **[!UICONTROL Response Code]** bildruta för fel. Om platsen är nere kan du klicka på *[!UICONTROL Site Down?]* i bildrutehuvudet. Bildrutan identifierar eventuella fel som inträffar och deras frekvens.
   * Distribuerade någon ändringar på din webbplats? The **[!UICONTROL Deployment Log Entries]** bildrutan anger om några distributioner har gjorts under problemets tidsram. Om problemet uppstår omedelbart efter distributionen kan det bero på att distributionsaktiviteterna lägger till ytterligare belastning på platsen (cachelagrar rensas, tjänster startas om osv.).
   * Uppstod en storleksändring eller en storleksändring? Om platsens storlek tillfälligt har uppgraderats kan den ha återgått till den ursprungliga klusterstorleken. Om en begäran gjordes om att öka platskapaciteten kan det bero på att platsens storlek har ändrats. Kontrollera **[!UICONTROL Upsize/Downsize – vCPU view over the timeline]** bildruta. Den här bildrutan upptäcker ibland ett avbrott på en viss nod. Om storleken minskar kan det tyda på ett problem med en eller flera noder.

* The **[!UICONTROL IP Frequency]** identifierar begärandefrekvens från IP-adresser som görs mot de ursprungliga servrarna (vilket innebär att begäran inte kunde hanteras från [!DNL Fastly] 74 var det inte cache-lagrat).

   * För alla [!DNL Fastly] relaterade problem, kontrollera **[!UICONTROL Fastly Cache]** bildruta och välj felaspekten för att se hur många procent av förfrågningarna som är fel. De kan tyda på ett serverdelsfel om de sammanfaller med icke-webbexport.
   * Om inläsningen inte verkar bero på webbtrafik kan det finnas fel eller en uppbyggnad av icke-webbförfrågningar, som långsamma frågor eller kundvagnar.

* Kontrollera **[!UICONTROL Database Errors]** bildruta för fel som kan sammanfalla med problemets/problemets tidslinje.
* Kontrollera **[!UICONTROL Database mysql-slow.log]** bildruta för att identifiera SQL-satser som inträffar. `INSERT`, `UPDATE`och `DELETE` -kommandon kan ta en stund om frågan inte är optimerad. Jämn `SELECT` -satser kan vara mycket ineffektiva om de utförs mot stora tabeller.
* **[!UICONTROL PHP States]** och **[!UICONTROL PHP Errors]** kommer att visa potentiella problem med PHP. The **[!UICONTROL PHP States]** bildrutan visar PHP-processavslutningar, start och när tjänsten når ready-läget per nod. The **[!UICONTROL PHP Errors]** bildrutan kan hjälpa till att isolera var problemet finns med PHP, t.ex. minnesstorlek, arbetare eller antalet servrar.
* Om du vill visa fördröjning i transaktioner kan tabellen Transaktioner - Medel, Max och Min sorteras efter kolumn för att visa den längsta transaktionslängden. Ett överbelastat kluster kommer att ha latenta varaktigheter i transaktioner, men det kommer också att visa avvikelser som kan tyda på ett problem med en metod eller kron.
* The **[!UICONTROL Cron error]** bildrutan kommer att visa kronlås, SQL-fel som kan vara kopplade till kronloggar och delade mellanlagringscron som kan köras i produktionsmiljöer när det finns en dedikerad mellanlagringsmiljö.
* The [!UICONTROL ElasticSearch Errors] bildrutan visar fel som kan tyda på större problem med [!DNL Elasticsearch] frågor, data eller index.