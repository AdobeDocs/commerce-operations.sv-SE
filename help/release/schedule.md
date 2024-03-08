---
title: Frigör schema
description: Läs mer om när Adobe planerar att tillkännage lanseringen av nya funktioner i Adobe Commerce.
exl-id: ae1e09cd-966f-44a3-9e4d-b90bb838429d
source-git-commit: a7aa02cd47deaf7aebdfcf0b3e969cce990a962a
workflow-type: tm+mt
source-wordcount: '504'
ht-degree: 2%

---

# Frigör schema

Adobe strävar hela tiden efter att hitta rätt balans mellan att göra produktuppgraderingar enkla och förutsägbara samtidigt som man levererar förbättringar och nya funktioner till tidiga användare snabbare (se [versionsprincip](versioning-policy.md)). Syftet med denna tidsplan är att ge Adobe datum för när planerar att släppa viktiga nya funktioner. Dessa funktioner kan variera under året. Adobe släpper dock regelbundet och kontinuerligt förbättringar av utökningsverktyg, infrastruktur och SaaS-produkter (tjänster) mellan de datum som anges på den här sidan.

Adobe [patchar](versioning-policy.md#patch-release) för varje versionsrad som stöds i Adobe Commerce PHP-programmets huvudprogram. Patch-versioner är möjligheter att uppgradera kärnkodbasen för att hålla plattformen säker, tillförlitlig och effektiv. Funktionerna är oberoende av kärnkodbasen och är tillgängliga via [extern modul, tillägg, verktyg eller webbtjänst](versioning-policy.md#extensibility-infrastructure-and-services-release).

>[!NOTE]
>
>Från och med 2024 har Adobe inte längre tillgång till förhandsversioner av patchar. För version 2.4.7 och senare kan Adobe Commerce-kunder använda [betaversioner](beta.md) för att få tillgång till pregenerell tillgänglighetskod för testnings- och utvecklingsändamål.

I följande tabell visas datumen för schemalagda releaser (datum kan ändras):

<table>
<thead>
  <tr>
    <th>Allmän tillgänglighet</th>
    <th>Funktioner</th>
    <th>PHP-kärna</th>
  </tr>
</thead>
<tfoot>
   <tr>
      <td colspan="3"><strong>Förklaring</strong>
         <ul>
            <li><strong><img alt="Funktionsikon för B2B" src="../assets/icons/enterprise.svg"></img> B2B</strong>—Nya funktioner, förbättringar och felkorrigeringar för B2B-tillägget för Adobe Commerce.</li>
            <li><strong><img alt="Ikon för utökningsfunktion" src="../assets/icons/brackets.svg"></img> Utbyggbarhet</strong>- Nya verktyg och tjänster för utbyggbarhet som inte längre är i processen och som levereras oberoende av korrigeringsversioner. Exempel: Admin UI SDK, Adobe I/O Events for Commerce och API Mesh.</li>
            <li><strong><img alt="Ikon för infrastrukturfunktion" src="../assets/icons/servers.svg"></img> Infrastruktur</strong>- Nya funktioner och förbättringar i Adobe Commerce i molninfrastrukturen och Cloud Tools Suite for Commerce-paketen, som är utformade för att driftsätta och hantera Adobe Commerce installationer och uppgraderingar på molnplattformen.</li>
            <li><strong><img alt="Ikon för lagningsrelease" src="../assets/icons/file-code.svg"></img> Patchar</strong>- Uppdateringar av Adobe Commerce PHP-programmets kärnprogram som omfattar korrigeringar av säkerhet, regelefterlevnad, prestanda och högprioriterade kvaliteter.</li>
            <li><strong><img alt="Ikon för tjänstefunktion" src="../assets/icons/feature.svg"></img> Tjänster</strong>- Nya SaaS-funktioner som levereras oberoende av korrigeringsversioner. Exempel: Catalog Service, Live Search och Product Recommendations.</li>
         </ul>
      </td>
   </tr>
</tfoot>
<tbody>
  <tr>
    <td>13 februari 2024</td>
    <td><img alt="Ikon för utökningsfunktion" src="../assets/icons/brackets.svg"></img> <a href="https://developer.adobe.com/commerce/extensibility/">Utbyggbarhet</a><br><img alt="Ikon för infrastrukturfunktion" src="../assets/icons/servers.svg"></img> <a href="https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/release-notes/cloud-tools-suite.html">Infrastruktur</a><br><img alt="Ikon för tjänstefunktion" src="../assets/icons/feature.svg"></img> <a href="https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/release-information/release-notes-all.html">Tjänster</a></td>
    <td><img alt="Ikon för lagningsrelease" src="../assets/icons/file-code.svg"></img> <a href="release-notes/security/overview.md">Säkerhetsuppdateringar</a>: 2.4.6-p4, 2.4.5-p6, 2.4.4-p7</td>
  </tr>
  <tr>
    <td>19 mars 2024</td>
    <td>—</td>
    <td><img alt="Ikon för lagningsrelease" src="../assets/icons/file-code.svg"></img> <a href="release-notes/commerce/overview.md">Betakorrigering</a>: 2.4.7-beta3</td>
  </tr>
  <tr>
    <td>9 april 2024</td>
    <td><img alt="Funktionsikon för B2B" src="../assets/icons/enterprise.svg"></img> <a href="https://experienceleague.adobe.com/docs/commerce-admin/b2b/release-notes.html">B2B</a><br><img alt="Ikon för utökningsfunktion" src="../assets/icons/brackets.svg"></img> <a href="https://developer.adobe.com/commerce/extensibility/">Utbyggbarhet</a><br><img alt="Ikon för infrastrukturfunktion" src="../assets/icons/servers.svg"></img> <a href="https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/release-notes/cloud-tools-suite.html">Infrastruktur</a><br><img alt="Ikon för tjänstefunktion" src="../assets/icons/feature.svg"></img> <a href="https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/release-information/release-notes-all.html">Tjänster</a></td>
    <td><img alt="Ikon för lagningsrelease" src="../assets/icons/file-code.svg"></img> <a href="release-notes/commerce/overview.md"><strong>Adobe Commerce 2.4.7</a></strong>:<ul><li>Prestandaförbättringar</li><li>Kvalitetsförbättringar</li><li>Säkerhetsförbättringar</li><li>Beroendeuppdateringar från tredje part</li></ul><img alt="Ikon för lagningsrelease" src="../assets/icons/file-code.svg"></img> <a href="release-notes/security/overview.md">Säkerhetsuppdateringar</a>: 2.4.6-p5, 2.4.5-p7, 2.4.4-p8</td>
  </tr>
  <tr>
    <td>11 juni 2024</td>
    <td><img alt="Funktionsikon för B2B" src="../assets/icons/enterprise.svg"></img> <a href="https://experienceleague.adobe.com/docs/commerce-admin/b2b/release-notes.html">B2B</a><br><img alt="Ikon för utökningsfunktion" src="../assets/icons/brackets.svg"></img> <a href="https://developer.adobe.com/commerce/extensibility/">Utbyggbarhet</a><br><img alt="Ikon för infrastrukturfunktion" src="../assets/icons/servers.svg"></img> <a href="https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/release-notes/cloud-tools-suite.html">Infrastruktur</a><br><img alt="Ikon för tjänstefunktion" src="../assets/icons/feature.svg"></img> <a href="https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/release-information/release-notes-all.html">Tjänster</a></td>
    <td><img alt="Ikon för lagningsrelease" src="../assets/icons/file-code.svg"></img> <a href="release-notes/security/overview.md">Säkerhetsuppdateringar</a>: 2.4.7-p1, 2.4.6-p6, 2.4.5-p8, 2.4.4-p9</td>
  </tr>
  <tr>
    <td>13 augusti 2024</td>
    <td><img alt="Funktionsikon för B2B" src="../assets/icons/enterprise.svg"></img> <a href="https://experienceleague.adobe.com/docs/commerce-admin/b2b/release-notes.html">B2B</a><br><img alt="Ikon för utökningsfunktion" src="../assets/icons/brackets.svg"></img> <a href="https://developer.adobe.com/commerce/extensibility/">Utbyggbarhet</a><br><img alt="Ikon för infrastrukturfunktion" src="../assets/icons/servers.svg"></img> <a href="https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/release-notes/cloud-tools-suite.html">Infrastruktur</a><br><img alt="Ikon för tjänstefunktion" src="../assets/icons/feature.svg"></img> <a href="https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/release-information/release-notes-all.html">Tjänster</a></td>
    <td><img alt="Ikon för lagningsrelease" src="../assets/icons/file-code.svg"></img> <a href="release-notes/security/overview.md">Säkerhetsuppdateringar</a>: 2.4.7-p2, 2.4.6-p7, 2.4.5-p9, 2.4.4-p10</td>
  </tr>
  <tr>
    <td>8 oktober 2024</td>
    <td><img alt="Funktionsikon för B2B" src="../assets/icons/enterprise.svg"></img> <a href="https://experienceleague.adobe.com/docs/commerce-admin/b2b/release-notes.html">B2B</a><br><img alt="Ikon för utökningsfunktion" src="../assets/icons/brackets.svg"></img> <a href="https://developer.adobe.com/commerce/extensibility/">Utbyggbarhet</a><br><img alt="Ikon för infrastrukturfunktion" src="../assets/icons/servers.svg"></img> <a href="https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/release-notes/cloud-tools-suite.html">Infrastruktur</a><br><img alt="Ikon för tjänstefunktion" src="../assets/icons/feature.svg"></img> <a href="https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/release-information/release-notes-all.html">Tjänster</a></td>
    <td><img alt="Ikon för lagningsrelease" src="../assets/icons/file-code.svg"></img> <a href="release-notes/commerce/overview.md">Betakorrigering</a>: 2.4.8-beta1<br><img alt="Ikon för lagningsrelease" src="../assets/icons/file-code.svg"></img> <a href="release-notes/security/overview.md">Säkerhetsuppdateringar</a>: 2.4.7-p3, 2.4.6-p8, 2.4.5-p10, 2.4.4-p11</td>
  </tr>
</tbody>
</table>
