---
source-git-commit: b63fa9a8b2b59f6e8dfd7003e75c66caf99d5e81
workflow-type: tm+mt
source-wordcount: '277'
ht-degree: 0%

---
# 2.4.7 Säkerhetsförbättringar

* **Stöd för SRI (Subresource Integrity) har lagts till** för att uppfylla PCI 4.0-kraven för verifiering av skriptintegritet på betalningssidor. Stöd för SRI (Subresource Integrity) ger integritetshash för alla JavaScript-resurser i det lokala filsystemet. Standardfunktionen för SRI implementeras bara på betalningssidorna för områdena Admin och storefront. Handlare kan dock utöka standardkonfigurationen till andra sidor. Se [Delresursintegritet](https://developer.adobe.com/commerce/php/development/security/subresource-integrity/) i _Commerce PHP-utvecklarhandbok_.<!--AC-1153-->

* **Ändringar av CSP (Content Security Policy)** - Konfigurationsuppdateringar och förbättringar av Adobe Commerce Content Security Policies (CSP) uppfyller PCI 4.0-kraven. Mer information finns i [Säkerhetsprinciper för innehåll](https://developer.adobe.com/commerce/php/development/security/content-security-policies/) i _Commerce PHP-utvecklarhandboken_. <!--AC-11513-->

   * CSP-standardkonfigurationen för betalningssidor för Commerce Admin- och storefront-områden är nu `restrict`. Standardkonfigurationen är `report-only` för alla andra sidor.  I versioner före 2.4.7 konfigurerades CSP i `report-only`-läge för alla sidor.

   * En nonce-provider har lagts till för att tillåta körning av infogade skript i en CSP. Enonce-providern gör det lättare att skapa unika nonce-strängar för varje begäran. Strängarna kopplas sedan till CSP-huvudet.

   * Lagt till alternativ för att konfigurera anpassade URI:er för att rapportera CSP-fel för sidan Skapa order i Admin och sidan Checka ut i butiken. Du kan lägga till konfigurationen från administratören eller genom att lägga till URI:n i filen `config.xml`.

     >[!NOTE]
     >
     >Om du uppdaterar CSP-konfigurationen till läget `restrict` kan befintliga textbundna skript på betalningssidor i Admin och storefront blockeras, vilket orsakar följande webbläsarfel när en sida läses in: `Refused to execute inline script because it violates the following Content Security Policy directive: "script-src`. Åtgärda dessa fel genom att uppdatera vitlistskonfigurationen så att nödvändiga skript tillåts. Se [Felsökning](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#troubleshooting) i _Commerce PHP Developer Guide_.
