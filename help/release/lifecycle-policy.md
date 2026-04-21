---
title: Policy för programvarans livscykel
description: Läs om viktiga datum för när programvarusupporten för Adobe Commerce upphör.
exl-id: 9ee4ecc8-d893-412a-a605-5a8606a1b9a9
source-git-commit: 3e7cef954a2be506c6f72e704710d16ed1d9b7a3
workflow-type: tm+mt
source-wordcount: '807'
ht-degree: 2%

---


# Adobe Commerce livscykelpolicy

För att effektivisera Adobe Commerce livscykelpolicy och stödja kundernas verksamhetskritiska behov erbjuder Adobe ett treårigt supportfönster från datumet General Availability (GA) för varje version och släpper kvalitetskorrigeringar under denna period. Datum och information om slutet på programvarusupporten för varje release finns i tabellen [Slutet av programvarusupporten](#end-of-software-support).

Under den treåriga supportperioden har kunden tillgång till

- **Kvalitetskorrigeringar**-Kunder kan få åtkomst till kvalitetskorrigeringar genom att kontakta [Adobe Commerce Support](https://experienceleague.adobe.com/sv/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide) eller via självbetjäningen [[!DNL Quality Patches Tool]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). I följande tabell beskrivs slutdatum för programsupport för Adobe Commerce versionsrader.

- **Säkerhetskorrigeringar**-Adobe tillhandahåller säkerhetskorrigeringar via kumulativa säkerhetspatchar och icke kumulativa [isolerade säkerhetspatchfiler](versioning-policy.md#isolated-security-fixes) under den treåriga supportperioden.

- **Programfixar**-För viktiga säkerhetsproblem, som noll-dagars säkerhetsluckor, tillhandahåller Adobe [snabbkorrigeringar](https://support.magento.com/hc/en-us/sections/360003869892-Known-issues-patches-attached-) för alla kunder med en version som stöds, även om de inte har den senaste korrigerings- eller säkerhetsuppdateringen. Observera att en programfix inte är heltäckande och inte åtgärdar alla säkerhetsproblem som skulle kunna lösas genom att uppgradera till den senaste versionen.

Adobe erbjuder inga säkerhets- och kvalitetskorrigeringar för tredjepartstjänster och programvaruberoenden (som PHP och MySQL) som kan ta slut när kunden är under den treåriga eller utökade supportperioden för Adobe Commerce. Se [systemkraven](../installation/system-requirements.md) för en fullständig lista över testade och stödda tredjepartstekniker.

## Utökat stöd

Adobe uppmuntrar kunderna att uppgradera så snart som möjligt. För att ge större flexibilitet att anpassa sig till uppgraderingsplaner och verksamhetsbehov erbjuder Adobe ett års support utan extra kostnad för Adobe Commerce-kunder med version 2.4.6. Supporttillägget omfattar kvalitets- och säkerhetsuppdateringar för kärnapplikationen i upp till ett år. Utökat stöd för Adobe Commerce 2.4.4 och 2.4.5 upphör i april och augusti 2026 som planerat.

>[!NOTE]
>
>Utökad support är endast tillgänglig för Adobe Commerce-kunder. Den är inte tillgänglig för Magento Open Source kodbas.

## Programvarusupport upphör

| Frigör | Allmän tillgänglighet | Slutet på den reguljära supporten<sup>1</sup> | Slutet på utökat stöd |
|----------------------|----------------------|------------------------------------|-------------------------|
| Adobe Commerce 2.4.8 | 8 april 2025 | 31 maj 2028 | TBD |
| Adobe Commerce 2.4.7 | 9 april 2024 | 31 maj 2027 | TBD |
| Adobe Commerce 2.4.6 | 14 mars 2023 | 11 augusti 2026 | 30 augusti 2027 |
| Adobe Commerce 2.4.5 | 9 augusti 2022 | 12 augusti 2025 | 11 augusti 2026 |
| Adobe Commerce 2.4.4 | 12 april 2022 | 12 april 2025 | 14 april 2026 |

{style="table-layout:auto"}

>[!NOTE]
>
>- <sup>1</sup> Om du är Adobe Commerce-kund kan du fortsätta att få säkerhets- och kvalitetskorrigeringar under ytterligare ett år under den utökade supportperioden.
>- Se [Princip för programvarans livscykel](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf).

## Ytterligare säkerhetsfixar för Adobe Commerce 2.4.4 och 2.4.5

Som ett engångsundantag erbjuder Adobe en utökad etableringsperiod för säkerhetskorrigeringar för Adobe Commerce version 2.4.4 och 2.4.5, vilket ger kunderna ytterligare tid att migrera till Adobe Commerce as a Cloud Service eller uppgradera till en versionslinje som stöds.

Observera följande under den här etableringsperioden för säkerhetskorrigeringar:

- **Isolerad säkerhetspatchningsfil endast**- En isolerad säkerhetspatchningsfil kommer att släppas för dessa versioner enligt frisläppningsschemat. Inga säkerhetsuppdateringar (inga nya -p-versioner) kommer att tillhandahållas under den här perioden.

  Om du vill använda en isolerad säkerhetskorrigeringsfil måste kunderna finnas på den senaste säkerhetspatchversionen (den senaste -p-versionen) för den versionslinje som stöds, eftersom isolerade säkerhetskorrigeringar endast testas mot den versionen.

- **Inga kvalitetskorrigeringar eller teknisk assistans**-Inga felkorrigeringar, kvalitetsuppdateringar ([kvalitetsuppdateringar &#x200B;](../tools/quality-patches-tool/usage.md)) eller teknisk assistans ([Adobe Commerce Support](https://experienceleague.adobe.com/sv/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide)) kommer att ges för version 2.4.4 eller 2.4.5 under den här perioden.

- **PCI-kompatibilitet garanteras inte:**-Eftersom PHP-versionerna 2.4.4 och 2.4.5 använder PHP som har nått slutet på livscykeln kan PCI-kompatibilitet inte garanteras för handlare i dessa versioner. Om du fortsätter att köra dessa versioner kan det innebära en risk för din PCI-kompatibilitet.

För att upprätthålla fullständig säkerhetstäckning och säkerställa PCI-kompatibilitet måste kunderna uppgradera till en version av Adobe Commerce som stöds så snart som möjligt eller migrera till [Adobe Commerce as a Cloud Service](https://experienceleague.adobe.com/sv/docs/commerce/cloud-service/overview).

| Frigör | Allmän tillgänglighet | Slutet på utökat stöd | Slut på etablering av säkerhetskorrigeringar |
|----------------------|----------------------|-------------------------|------------------------------------|
| Adobe Commerce 2.4.5 | 9 augusti 2022 | 11 augusti 2026 | Maj 2027 |
| Adobe Commerce 2.4.4 | 12 april 2022 | 14 april 2026 | Maj 2027 |

{style="table-layout:auto"}

>[!NOTE]
>
>Ytterligare säkerhetskorrigeringar är bara tillgängliga för Adobe Commerce-kunder och är inte tillgängliga för Magento Open Source kodbas.


## Supporttidslinje

Supporttidslinjens kartor har stöd för perioder per kvartal för varje Adobe Commerce-versionsrad. Använd tabellerna som fanns tidigare i det här avsnittet för exakta slutdatum.

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
    <th colspan="4">2028</th>
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
    <td colspan="5" style="background-color:#FFBF00"></td>
    <td colspan="10"></td>
  </tr>
  <tr>
    <td>2.4.5</td>
    <td colspan="2"></td>
    <td colspan="13" style="background-color:#67ac68;"></td>
    <td colspan="4" style="background-color:#ffd700;"></td>
    <td colspan="4" style="background-color:#FFBF00"></td>
    <td colspan="9"></td>
  </tr>
  <tr>
    <td>2.4.6</td>
    <td colspan="4"></td>
    <td colspan="15" style="background-color:#67ac68;"></td>
    <td colspan="4" style="background-color:#ffd700;"></td>
    <td colspan="10"></td>
  </tr>
  <tr>
    <td>2.4.7</td>
    <td colspan="9"></td>
    <td colspan="13" style="background-color:#67ac68;"></td>
    <td colspan="6"></td>
  </tr>
  <tr>
    <td>2.4.8</td>
    <td colspan="13"></td>
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
    <tr>
   <td style="background-color:#FFBF00;"> </td>
   <td>Utökade säkerhetskorrigeringar</td>
  </tr>
 </tbody>
</table>
