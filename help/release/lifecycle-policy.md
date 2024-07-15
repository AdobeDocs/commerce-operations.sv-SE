---
title: Policy för programvarans livscykel
description: Läs om viktiga datum för när programvarusupporten för Adobe Commerce upphör.
exl-id: 9ee4ecc8-d893-412a-a605-5a8606a1b9a9
source-git-commit: 7df5edf2acba706fb01f58cc3749c4a2bf136fc5
workflow-type: tm+mt
source-wordcount: '426'
ht-degree: 5%

---


# Adobe Commerce livscykelpolicy

För Adobe Commerce 2.4.4 och senare versioner:

- För att effektivisera Adobe Commerce livscykelpolicy och stödja kundernas verksamhetskritiska behov har Adobe utökat supportfönstret till tre år från datumet General Availability (GA) för Adobe Commerce 2.4.4 och senare. Adobe tillhandahåller kvalitetskorrigeringar till version 2.4.4 och senare för en treårig supportperiod. Kunder kan få åtkomst till kvalitetskorrigeringar genom att kontakta [Adobe Commerce Support](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html) eller via självbetjäningen [[!DNL Quality Patches Tool]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) om deras version fortfarande är berättigad till kvalitetssupport. Se tabellen nedan för mer information om supportdatum för Adobe Commerce releaserader.

- Adobe tillhandahåller säkerhetskorrigeringar via en säkerhetsuppdatering för den treåriga supportperioden.

- För allvarliga säkerhetsproblem, som noll-dagars säkerhetsluckor, tillhandahåller Adobe [snabbkorrigeringar](https://support.magento.com/hc/en-us/sections/360003869892-Known-issues-patches-attached-) för alla kunder i en version som stöds, även om de inte har den senaste korrigerings- eller säkerhetsuppdateringen. Det är viktigt att komma ihåg att en programfix inte är en&quot;catch-all&quot; och inte åtgärdar alla säkerhetsproblem som skulle ha åtgärdats genom en uppgradering till den senaste versionen.

- Adobe erbjuder inga säkerhets- och kvalitetskorrigeringar för tredjepartstjänster och programvaruberoenden (som PHP och MySQL) som kan ta slut när kunderna är under den treåriga supportperioden för Adobe Commerce. Se [systemkraven](../installation/system-requirements.md) för en fullständig lista över testade och stödda tredjepartstekniker.

- Adobe är kompatibelt med tredjepartstjänster och programvaruberoenden medan Adobe Commerce under den treåriga supportperioden omfattas av säkerhetsuppdateringar, men endast när det är möjligt att göra detta utan att införa bakåtkompatibla ändringar.

## Programvarusupport upphör

| Frigör | Allmän tillgänglighet | Programvarusupporten upphör<sup>1</sup> | Beroende PHP-version | Beroende MariaDB-version |
|----------------------|----------------------|-------------------------------------|-----------------------|------------------------------|
| Adobe Commerce 2.4.7 | 9 april 2024 | 9 april 2027 | 8.2 och 8.3 | 10,6 |
| Adobe Commerce 2.4.6 | 14 mars 2023 | 14 mars 2026 | 8.1 och 8.2 | 10,6 |
| Adobe Commerce 2.4.5 | 9 augusti 2022 | 9 augusti 2025 | 8,1 | 10.5<sup>2</sup> |
| Adobe Commerce 2.4.4 | 12 april 2022 | 24 april 2025 | 8,1 | 10.5<sup>3</sup> |

{style="table-layout:auto"}

>[!NOTE]
>
>- <sup>1</sup> Stödet för programvarans slut omfattar både slut på kvalitetskorrigeringar och slut på säkerhetskorrigeringar.
>- <sup>2</sup> Börjar med säkerhetspatchen 2.4.5-p8.
>- <sup>3</sup> Börjar med säkerhetspatchen 2.4.4-p9.
>- Se [Princip för programvarans livscykel](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf).

<table style="table-layout:auto">
<thead>
  <tr>
    <th colspan="2"></th>
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
    <td colspan="10"></td>
  </tr>
  <tr>
    <td>2.4.5</td>
    <td colspan="2"></td>
    <td colspan="13" style="background-color:#67ac68;"></td>
    <td colspan="9"></td>
  </tr>
  <tr>
    <td>2.4.6</td>
    <td colspan="4"></td>
    <td colspan="13" style="background-color:#67ac68;"></td>
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
   <td style="background-color:#67ac68;">Stöds</td>
   <td>Säkerhets- och kvalitetspatchar för Adobe Commerce</td>
  </tr>
  <!-- <tr>
   <td style="background-color:#cd3c3c;">End of software support</td>
   <td>Version that has reached end of software support.</td>
  </tr>
 </tbody> -->
</table>
