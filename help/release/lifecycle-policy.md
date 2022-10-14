---
title: Policy för programvarans livscykel
description: Läs om viktiga datum för när supporten för Adobe Commerce upphör.
source-git-commit: ffa8b957828833d2c3f9bc79c31dc3fa2c6035a5
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 5%

---


# Adobe Commerce livscykelpolicy

För Adobe Commerce 2.4 och senare:

- För att effektivisera vår livscykelpolicy kan Adobe tillhandahålla kvalitetsfixar till version 2.4 fram till supportdatumet för den PHP-version som den baseras på. Kunden kan få tillgång till kvalitetskorrigeringar genom att kontakta [Adobe Commerce Support](https://developer.adobe.com/commerce/contributor/community/support/) eller genom självbetjäningen [[!DNL Quality Patches Tool]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html){target=&quot;_blank&quot;} om deras version fortfarande är berättigad till kvalitetssupport. Se tabellen nedan för&quot;End of Software Support&quot; för Adobe Commerce versionsrader.

- Adobe tillhandahåller bara säkerhetskorrigeringar via den senaste patchen eller säkerhetsuppdateringen, även om en kunds version fortfarande är berättigad till kvalitetssupport. Till skillnad från kvalitetskorrigeringar kan säkerhetskorrigeringar inte säkerhetskopieras till tidigare mindre utgåvor eller till tidigare korrigeringsutgåvor inom de mindre utgåvor som stöds.

- För allvarliga säkerhetsproblem, som noll-dagars säkerhetsluckor, tillhandahåller Adobe [snabbkorrigeringar](https://support.magento.com/hc/en-us/sections/360003869892-Known-issues-patches-attached-) för alla kunder som har en version som stöds, även om de inte har den senaste patchen eller säkerhetsuppdateringen. Det är viktigt att komma ihåg att en programfix inte är en&quot;catch-all&quot; och inte åtgärdar alla säkerhetsproblem som skulle ha åtgärdats genom en uppgradering till den senaste versionen.

## Programvarusupport upphör

| Frigör | Releasedatum | Programvarusupport upphör<sup>1</sup> | Beroende PHP-version |
| -------------------------------- | ----------------- | ----------------------------------- | --------------------------- |
| Adobe Commerce 2.3 | 28 november 2018 | 8 september 2022<sup>2</sup> | PHP 7.3 och 7.4<sup>3</sup> |
| Adobe Commerce 2.4.0-2.4.3 | 28 juli 2020 | 28 november 2022 | PHP 7.4 |
| Adobe Commerce 2.4.4-2.4.6 | 12 april 2022 | 25 november 2024 | PHP 8.1 |

<sup>1 Supporten för programvarusupporten omfattar både slutdatum för kvalitetskorrigeringar och slutet av säkerhetskorrigeringar.</sup><br>
<sup>2 Slutdatumet för programvarusupporten för 2.3 har förlängts till 8 september 2022 så att kunderna får mer tid att uppgradera till version 2.4.4 som blir allmänt tillgänglig den 8 mars 2022.</sup><br>
<sup>3 2.3.0-2.3.6 är beroende av PHP 7.3; 2.3.7 beror på PHP 7.4.</sup>

>[!NOTE]
>
>Se [Software Lifecycle Policy](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf).

<table>
<thead>
  <tr>
    <th colspan="2"></th>
    <th colspan="4">2022</th>
    <th colspan="4">2023</th>
    <th colspan="4">2024</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>Handel</td>
    <td>PHP</td>
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
    <td>2.4.0 - 2.4.3</td>
    <td style="text-align:center">7.4</td>
    <td colspan="3" style="background-color:#67ac68;"></td>
    <td style="background-color:#cd3c3c;">Nov</td>
    <td colspan="8" ></td>
  </tr>
  <tr>
    <td>2.4.4</td>
    <td rowspan="2" style="text-align:center">8.1</td>
    <td></td>
    <td colspan="10" style="background-color:#67ac68;">Mars</td>
    <td rowspan="2" style="background-color:#cd3c3c;">Nov</td>
  </tr>
  <tr>
    <td>2.4.5</td>
    <td colspan="2"></td>
    <td colspan="9" style="background-color:#67ac68;">aug</td>
  </tr>
</tbody>
</table>

## Nyckel

<table>
  <thead>
   <tr>
    <th></th>
    <th></th>
   </tr>
  </thead>
 <tbody>
  <tr>
   <td style="background-color:#67ac68;">Stöds</td>
   <td>Versionen har testats fullt ut av Adobe och stöds.</td>
  </tr>
  <tr>
   <td style="background-color:#cd3c3c;">Programvarusupport upphör</td>
   <td>Version som har nått slutet av programvarusupporten.</td>
  </tr>
 </tbody>
</table>
