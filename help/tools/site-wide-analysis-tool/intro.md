---
title: '[!DNL Site-Wide Analysis Tool]'
description: Lär dig mer om  [!DNL Site-Wide Analysis] verktyget, dess användningsområden, installationsprocessen och hur du får åtkomst
exl-id: 32774040-d322-43d6-9c26-c340a0ab58a9
source-git-commit: 62ca9093228d4d928d6c61c4c5dcf26e142c9fdb
workflow-type: tm+mt
source-wordcount: '542'
ht-degree: 0%

---

# [!DNL Site-Wide Analysis Tool]

>[!IMPORTANT]
>
>Från och med den 23 april 2024 kommer [!DNL Site-Wide Analysis Tool] att tas bort för alla Adobe Commerce lokala kunder.

Den här guiden ger en helhetsöversikt över [!DNL Site-Wide Analysis Tool]. Den beskriver användningsområdena, steg-för-steg-anvisningar för installation och hur du kommer åt verktyget.

## Vad är [!DNL Site-Wide Analysis Tool]?

[!DNL Site-Wide Analysis Tool] är ett proaktivt självbetjäningsverktyg och en central databas som innehåller detaljerade systeminsikter och rekommendationer för att säkerställa säkerheten och användbarheten för din Adobe Commerce-installation. Den ger prestandaövervakning, rapporter och råd i realtid dygnet runt alla dagar för att identifiera potentiella problem och bättre synlighet för webbplatsens hälsa, säkerhet och programkonfigurationer. Det minskar upplösningstiden och förbättrar webbplatsens stabilitet och prestanda.

>[!NOTE]
>
>När du har tillämpat en rekommendation kan det ta några dagar innan den har uppdaterats på kontrollpanelen för analysverktyget för hela webbplatsen eller i den genererade rapporten.
>
>[!DNL Site-Wide Analysis Tool] rapporterar om data på systemnivå. Rapporter om Adobe Commerce produkter, försäljning, marknadsföring och andra affärsprogramdata finns i [Adobe Commerce Reports](https://experienceleague.adobe.com/en/docs/commerce-admin/start/reporting/reports-menu).

![Kontrollpanel för hela webbplatsanalysverktyget](../../assets/tools/swat-dashboard.png){zoomable="yes"}

Se den här [introduktionsvideon](https://www.youtube.com/watch?v=KW2R8ki_RG4) om du vill veta mer.

## Verktygsöversikt

- **Instrumentpanel**
   - Visar den övergripande hälsan i systemet med meddelanden om identifierade problem och specifika rekommendationer efter prioritet.<br>
Den innehåller också ett historiskt diagram som visar hur webbplatsens hälsa förändras över tid.
   - Visar **[!UICONTROL Security Center Widget]** som innehåller länkar till följande resurser:
      - [Tech [!DNL Stack] Versionskompatibilitet med [!DNL end of life (EOL)]](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/system-requirements)
      - [Adobe säkerhetsbulletin](https://helpx.adobe.com/security/security-bulletin.html)
      - [Rekommendationer från  [!DNL Security Scan Tool]](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/security-scan)
      - [[!DNL Site-Wide Analysis Tool] Rekommendationer för bästa praxis för säkerhet](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/site-wide-analysis-tool/recommendations)

- **Information** - Tillhandahåller kundens kontaktinformation och en sammanfattning av aktuella biljetter med detaljerad information om varje installerad Adobe Commerce-produkt.

- **Rekommendationer** - Tillhandahåller ett [hälsoindexspår för SWAT](#swat-health-index.md) för att spåra webbplatsens hälsa och visar rekommendationer baserade på bästa praxis för att hantera problem som upptäcks på din webbplats:
   - För ändringar som kräver en infrastrukturuppdatering skickar du en supportförfrågan.
   - Gör ändringarna själv för ändringar som kräver en programuppdatering.
   - Om du vill göra ändringar som kräver manuell åtgärd, t.ex. en [koddistribution](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/architecture/pro-develop-deploy-workflow#deployment-workflow), ber du systemadministratören eller utvecklarna om hjälp.

- **Undantag** - Visar en lista över fel som uppstått i programmet och som orsakas av onormala förhållanden utan felhanterare.

- **Tillägg** - Visar alla tillägg från tredje part och tredjepartsbibliotek.

- **Patchar** - Integrerat med [!DNL Quality Patches Tool] och innehåller en lista med alla tillgängliga patchar som är specifika för din Adobe Commerce-instans.

## Integrering med andra Adobe Commerce supportverktyg

Se viktiga insikter om er webbplats på ett och samma ställe. [!DNL Site-Wide Analysis Tool] ger dig direktåtkomst till och information från [!UICONTROL Security Center Widget], [!DNL Upgrade Compatibility Tool] och [!DNL Managed Alerts].

- **[!UICONTROL Security Center Widget]** - Visar säkerhetsinsikter för din webbplats.<br>
Säkerhetsinformationen innehåller [&#x200B; Tech [!DNL Stack] Versionsefterlevnad med  [!DNL end of life (EOL)]](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/system-requirement), [Adobe Security Bulletin](https://helpx.adobe.com/security/security-bulletin.html), [Recommendations from the [!DNL Security Scan Tool]](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/security-scan), and [[!DNL Site-Wide Analysis Tool] Best Practice Security Recommendations](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/site-wide-analysis-tool/recommendations) .

  [[!DNL Security Scan Tool]](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/security-scan) förser Adobe Commerce- och Magento Open-Source-kunder med realtidsinsikter om butikens säkerhetsställning genom att proaktivt identifiera skadlig kod och varna dem om deras butik äventyras.

- **[[!DNL Upgrade Compatibility Tool]](../../upgrade/upgrade-compatibility-tool/overview.md)** - Kontrollerar din Adobe Commerce-instans mot uppgraderingsversionen och flaggar viktiga problem, fel och varningar som ska åtgärdas innan uppgraderingen. Att åtgärda dessa problem effektiviserar uppgraderingsprocessen.&quot;

- **[[!DNL Managed Alerts]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce)** - Övervaka nyckelvärden (CPU, programprestanda, disk, minne och databashälsa) och tillhandahåller tydliga felsökningssteg som hjälper handlare att ligga steget före och undvika driftavbrott.

## Vem är den här guiden till?

Handlare och partners som vill ha större insyn i sina Adobe Commerce webbplatser. Det ger handlare möjlighet att förbättra sina kunders upplevelse och bättre anpassa sig till rekommendationerna om bästa praxis och till grundläggande frågor.

## [!DNL Site-Wide Analysis Tool] demo

Titta på den här videon om du vill veta mer om [!DNL Site-Wide Analysis Tool]:

>[!VIDEO](https://video.tv.adobe.com/v/344001?quality=12)
