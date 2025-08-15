---
title: Så här använder du  [!DNL Observation for Adobe Commerce] nerdleten
description: Lär dig hur du använder  [!DNL Observation for Adobe Commerce] nördleten.
exl-id: 3c368814-0786-4e8f-ac81-9a77cec94677
feature: Configuration, Observability
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '627'
ht-degree: 0%

---

# Så här använder du [!DNL Observation for Adobe Commerce]-nördleten

## Allmän metod för att se på frågor

Kontrollera tillstånd för miljöresurser:

* Undersök % av **[!UICONTROL Storage Free and MySQL % free storage by node]** bildrutor.

   * Följ länkarna i bildrutans sidhuvud om du ser lite lagringsutrymme.

* Undersök % av **[!UICONTROL free system memory and Swap memory free in bytes]** bildrutor.

   * Om dessa visar mycket små minneslägen kan de bidra till problem.

* Granska bildrutan **[!UICONTROL Alerts during the timeframe]**.

   * Adobe Commerce i molninfrastrukturen tillhandahåller [!DNL Managed alerts]. Du kan klicka på länken i sidhuvudet för att se [!DNL Support Knowledge Base] artiklar som hjälper dig att avgöra vilka åtgärder du ska vidta för specifika aviseringar.

* Granska **[!UICONTROL CPU % by host]**-bildrutan: Om den har hög användning av CPU bör du kontrollera [!DNL Support Knowledge Base]-artikeln i bildrutans sidhuvud. Kontrollera också att import/export eller säkerhetskopiering av databaser inte sker under trafiktoppar.

* Kontrollera **[!UICONTROL Web Traffic volume compared to one week ago]**-bildrutan: Om trafiken är mycket högre än föregående vecka under samma period, kan den förklaras (t.ex. en försäljningskampanj eller nya produkter som har marknadsförts)?
   * Om det inte går att förklara en trafikökning tittar du på den genomsnittliga svarstiden (millisekunder) för produktionsmiljön. Bidrar den högre trafiken till en annan svarstid än vad som är normalt? Expandera tidsramen för att se om det är en avvikelse.
   * Påverkar den ökade trafiken webbtransaktioner? Kontrollera om det finns fel i bildrutan **[!UICONTROL Response Code]**. Om webbplatsen är nere kan du klicka på länken `Site Down?` i bildrutehuvudet. Bildrutan identifierar eventuella fel som inträffar och deras frekvens.
   * Distribuerade någon ändringar på din webbplats? Bildrutan **[!UICONTROL Deployment Log Entries]** anger om några distributioner har gjorts under problemets tidsram. Om problemet uppstår omedelbart efter distributionen kan det bero på att distributionsaktiviteterna lägger till ytterligare belastning på platsen (cachelagrar rensas, tjänster startas om osv.).
   * Uppstod en storleksändring eller en storleksändring? Om platsens storlek tillfälligt har uppgraderats kan den ha återgått till den ursprungliga klusterstorleken. Om en begäran gjordes om att öka platskapaciteten kan det bero på att platsens storlek har ändrats. Kontrollera bildrutan **[!UICONTROL Upsize/Downsize – vCPU view over the timeline]**. Den här bildrutan upptäcker ibland ett avbrott på en viss nod. Om storleken minskar kan det tyda på ett problem med en eller flera noder.

* Fliken **[!UICONTROL IP Frequency]** identifierar begärandefrekvens från IP-adresser som görs mot de ursprungliga servrarna (vilket innebär att begäran inte kunde hanteras från [!DNL Fastly] eftersom 74 den inte cachelagrades).

   * Kontrollera bildrutan [!DNL Fastly] för eventuella **[!UICONTROL Fastly Cache]**-relaterade problem och välj felaspekten för att se hur många begäranden som är fel. De kan tyda på ett serverdelsfel om de sammanfaller med icke-webbexport.
   * Om inläsningen inte verkar bero på webbtrafik kan det finnas fel eller en kombination av icke-webbförfrågningar, som långsamma frågor eller [!DNL crons].

* Kontrollera bildrutan **[!UICONTROL Database Errors]** för att se om det finns fel som kan sammanfalla med tidslinjen för problem/problem.
* Kontrollera **[!UICONTROL Database mysql-slow.log]**-bildrutan för att identifiera SQL-satser som inträffar. Kommandona `INSERT`, `UPDATE` och `DELETE` kan ta en stund om frågan inte är optimerad. Även `SELECT`-satser kan vara mycket ineffektiva om de utförs mot stora tabeller.
* **[!UICONTROL PHP States]** och **[!UICONTROL PHP Errors]** bildrutor visar potentiella problem med PHP. Bildrutan **[!UICONTROL PHP States]** visar PHP-processavslutningar, starter och när tjänsten når färdigt läge per nod. Bildrutan **[!UICONTROL PHP Errors]** kan hjälpa dig att isolera var problemet finns med PHP, t.ex. minnesstorlek, arbetare eller antalet servrar.
* Om du vill visa fördröjning i transaktioner kan tabellen Transaktioner - Medel, Max och Min sorteras efter kolumn för att visa den längsta varaktigheten för transaktioner. Ett överlagrat kluster kommer att ha latenta varaktigheter i transaktioner, men det kommer också att visa avvikelser som kan tyda på ett problem med en metod eller [!DNL cron].
* Bildrutan **[!UICONTROL Cron error]** visar [!DNL cron] lås, SQL-fel som kan vara kopplade till [!DNL cron]-loggar och delad mellanlagring [!DNL crons] som kan köras i produktionsmiljöer när det finns en dedikerad mellanlagringsmiljö.
* Bildrutan [!UICONTROL ElasticSearch Errors] innehåller fel som kan tyda på större problem med [!DNL Elasticsearch] frågor, data eller index.
