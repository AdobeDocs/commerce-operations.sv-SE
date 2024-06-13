---
source-git-commit: 4ed23e2a8319ff97f8206f752cf1cbe2e73ea5c5
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---
# 2.4.7 Säkerhetsförbättringar

* **Stöd för extra resursintegritet (SRI)** uppfyller PCI 4.0-kraven för verifiering av skriptintegritet på betalningssidor. Stöd för SRI (Subresource Integrity) ger integritetshash för alla JavaScript-resurser i det lokala filsystemet. Standardfunktionen för SRI implementeras bara på betalningssidorna för områdena Admin och storefront. Handlare kan dock utöka standardkonfigurationen till andra sidor. Se [Underresursintegritet](https://developer.adobe.com/commerce/php/development/security/subresource-integrity/) i _Commerce PHP Developer Guide_.<!--AC-1153-->

* **Ändringar i CSP (Content Security Policy)**—Konfigurationsuppdateringar och förbättringar av Adobe Commerce Content Security Policies (CSP) som uppfyller PCI 4.0-kraven. Mer information finns i [Skyddsprofiler för innehåll](https://developer.adobe.com/commerce/php/development/security/content-security-policies/) i _Commerce PHP Developer Guide_. <!--AC-11513-->

   * Standardkonfigurationen för CSP för betalningssidor för Commerce Admin och butiksområden är nu `restrict` läge. För alla andra sidor är standardkonfigurationen `report-only` läge.  I versioner före 2.4.7 konfigurerades CSP i `report-only` läge för alla sidor.

   * En nonce-provider har lagts till för att tillåta körning av infogade skript i en CSP. Enonce-providern gör det lättare att skapa unika nonce-strängar för varje begäran. Strängarna kopplas sedan till CSP-huvudet.

   * Lagt till alternativ för att konfigurera anpassade URI:er för att rapportera CSP-fel för sidan Skapa order i Admin och sidan Checka ut i butiken. Du kan lägga till konfigurationen från administratören eller genom att lägga till URI:n i dialogrutan `config.xml` -fil.

     >[!NOTE]
     >
     >Uppdaterar CSP-konfigurationen till `restrict` Läget kan blockera befintliga textbundna skript på betalningssidor i Admin och storefront, vilket orsakar följande webbläsarfel när en sida läses in: `Refused to execute inline script because it violates the following Content Security Policy directive: "script-src`. Åtgärda dessa fel genom att uppdatera vitlistskonfigurationen så att nödvändiga skript tillåts. Se [Felsökning](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#troubleshooting) i _Commerce PHP Developer Guide_.
