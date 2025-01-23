---
title: Policy för programvarans livscykel
description: Läs om viktiga datum för när programvarusupporten för Adobe Commerce upphör.
exl-id: 9ee4ecc8-d893-412a-a605-5a8606a1b9a9
source-git-commit: ce7c322c5cf979a992e6f929c3105daf86d4aa49
workflow-type: tm+mt
source-wordcount: '521'
ht-degree: 4%

---


# Adobe Commerce livscykelpolicy

För Adobe Commerce 2.4.4 och senare versioner:

- För att effektivisera Adobe Commerce livscykelpolicy och stödja kundernas verksamhetskritiska behov har Adobe utökat supportfönstret till tre år från datumet General Availability (GA) för Adobe Commerce 2.4.4 och senare. Adobe tillhandahåller kvalitetskorrigeringar till version 2.4.4 och senare för en treårig supportperiod. Kunder kan få åtkomst till kvalitetskorrigeringar genom att kontakta [Adobe Commerce Support](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide) eller via självbetjäningen [[!DNL Quality Patches Tool]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) om deras version fortfarande är berättigad till kvalitetssupport. I följande tabell beskrivs slutdatum för programsupport för Adobe Commerce versionsrader.

- Adobe tillhandahåller säkerhetskorrigeringar via en säkerhetsuppdatering för den treåriga supportperioden.

- För allvarliga säkerhetsproblem, som noll-dagars säkerhetsluckor, tillhandahåller Adobe [snabbkorrigeringar](https://support.magento.com/hc/en-us/sections/360003869892-Known-issues-patches-attached-) för alla kunder i en version som stöds, även om de inte har den senaste korrigerings- eller säkerhetsuppdateringen. Observera att en programfix inte är heltäckande och inte åtgärdar alla säkerhetsproblem som skulle kunna lösas genom att uppgradera till den senaste versionen.

- Adobe erbjuder inga säkerhets- och kvalitetskorrigeringar för tredjepartstjänster och programvaruberoenden (som PHP och MySQL) som kan ta slut när kunderna är under den treåriga supportperioden för Adobe Commerce. Se [systemkraven](../installation/system-requirements.md) för en fullständig lista över testade och stödda tredjepartstekniker.

- Adobe är kompatibelt med tredjepartstjänster och programvaruberoenden medan Adobe Commerce under den treåriga supportperioden omfattas av säkerhetsuppdateringar, men endast när det är möjligt att göra detta utan att införa bakåtkompatibla ändringar.

## Utökat stöd

Adobe uppmuntrar kunderna att uppgradera så snart som möjligt. För att ge större flexibilitet att anpassa sig till uppgraderingsplaner och verksamhetsbehov erbjuder Adobe ett års support utan extra kostnad för Adobe Commerce-kunder med versionerna 2.4.4 och 2.4.5. Supporttillägget omfattar kvalitets- och säkerhetsuppdateringar för kärnapplikationen i upp till ett år.

>[!NOTE]
>
>Utökad support är endast tillgänglig för Adobe Commerce-kunder. Den är inte tillgänglig för kodbasen Magento Open Source.

## Programvarusupport upphör

| Frigör | Allmän tillgänglighet | Slutet på den reguljära supporten<sup>1</sup> | Slutet på utökat stöd | Beroende PHP-version | Beroende MariaDB-version |
|----------------------|----------------------|------------------------------------|-------------------------|-----------------------|------------------------------|
| Adobe Commerce 2.4.7 | 9 april 2024 | 9 april 2027 | Ej tillämpligt | 8.2 och 8.3 | 10,6 |
| Adobe Commerce 2.4.6 | 14 mars 2023 | 11 augusti 2026<sup>2</sup> | Ej tillämpligt | 8.1 och 8.2 | 10,6 |
| Adobe Commerce 2.4.5 | 9 augusti 2022 | 9 augusti 2025 | 11 augusti 2026 | 8,1 | 10.6<sup>3</sup> |
| Adobe Commerce 2.4.4 | 12 april 2022 | 24 april 2025 | 14 april 2026 | 8,1 | 10.6<sup>4</sup> |

{style="table-layout:auto"}

>[!NOTE]
>
>- <sup>1</sup> Stödet för programvarans slut omfattar både slut på kvalitetskorrigeringar och slut på säkerhetskorrigeringar.
>- <sup>2</sup> Uppdaterad för att justeras mot slutet av det utökade stödet för 2.4.5.
>- <sup>3</sup> Börjar med säkerhetspatchen 2.4.5-p11.
>- <sup>4</sup> Börjar med säkerhetspatchen 2.4.4-p12.
>- Se [Princip för programvarans livscykel](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf).

<table style="table-layout:auto">
<thead>
  <tr>
    <th colspan="1"></th>
    <th colspan="4">2022</th>
    <th colspan="4">2023</th>
    <th colspan="4">2024</th>
    <th colspan="4">2025</th>
    <th colspan="4">2026</th>
    <th colspan="4">2027</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>Commerce</td>
    <td>Q1</td>
    <td>Q2</td>
    <td>Q3</td>
    <td>Q4</td>
    <td>Q1</td>
    <td>Q2</td>
    <td>Q3</td>
    <td>Q4</td>
    <td>Q1</td>
    <td>Q2</td>
    <td>Q3</td>
    <td>Q4</td>
    <td>Q1</td>
    <td>Q2</td>
    <td>Q3</td>
    <td>Q4</td>
    <td>Q1</td>
    <td>Q2</td>
    <td>Q3</td>
    <td>Q4</td>
    <td>Q1</td>
    <td>Q2</td>
    <td>Q3</td>
    <td>Q4</td>
  </tr>
  <tr>
    <td>2.4.4</td>
    <td></td>
    <td colspan="13" style="background-color:#67ac68;"></td>
    <td colspan="4" style="background-color:#ffd700;"></td>
    <td colspan="6"></td>
  </tr>
  <tr>
    <td>2.4.5</td>
    <td colspan="2"></td>
    <td colspan="13" style="background-color:#67ac68;"></td>
    <td colspan="4" style="background-color:#ffd700;"></td>
    <td colspan="6"></td>
  </tr>
  <tr>
    <td>2.4.6</td>
    <td colspan="4"></td>
    <td colspan="15" style="background-color:#67ac68;"></td>
    <td colspan="8"></td>
  </tr>
  <tr>
    <td>2.4.7</td>
    <td colspan="9"></td>
    <td colspan="13" style="background-color:#67ac68;"></td>
    <td colspan="2"></td>
  </tr>
</tbody>
</table>

**Nyckel**

<table style="table-layout:auto">
 <tbody>
  <tr>
   <td style="background-color:#67ac68;"></td>
   <td>Regelbundet stöd</td>
  </tr>
  <tr>
   <td style="background-color:#ffd700;"></td>
   <td>Utökat stöd</td>
  </tr>
 </tbody>
</table>
