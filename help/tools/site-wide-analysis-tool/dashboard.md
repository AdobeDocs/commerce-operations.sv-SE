---
title: '[!DNL Dashboard]'
description: Lär dig mer om fliken  [!DNL Dashboard] i  [!DNL Site-Wide Analysis Tool] -elementen, när du ska använda dem, fördelarna och de bästa metoderna.
exl-id: 37d848ff-2cff-48b1-8391-520531300bbc
source-git-commit: 6896d31a202957d7354c3dd5eb6459eda426e8d7
workflow-type: tm+mt
source-wordcount: '686'
ht-degree: 0%

---

# [!UICONTROL Dashboard]

Sidan [!UICONTROL Dashboard] visar i korthet [!DNL widgets] som ger en enda ruta av glasvy som visar hälsotillståndet och den aktuella statusen för din Adobe Commerce-webbplats. Varje [!DNL widget] innehåller en åtkomstlänk till varje funktions sida, till varje verktyg eller till rapporter (beroende på [!DNL widget]).
Det finns också en lista med [!UICONTROL External Resources] länkar för Adobe Commerce, bland annat [Adobe Commerce Help Center Support Knowledge Base (Help Center)](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/overview.html), [Adobe Commerce Developer Documentation (DevDocs)](https://developer.adobe.com/commerce/docs/), [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html){target="_blank"}, [Security Center](https://helpx.adobe.com/security.html) och [Observation for Adobe Commerce (OAC)](https://experienceleague.adobe.com/docs/commerce-operations/tools/observation-for-adobe-commerce/intro.html).

## Element

* **[!UICONTROL Recommendations]**: Visar rekommendationer om bästa praxis för din plats. Rekommendationer (problem som hittats och rekommendationer som ska åtgärdas) sorteras efter prioritet - P0 (kritiskt) till P4 (meddelande).
Rekommendationerna är beskrivning, rekommendation, webbplatsens påverkan, rotorsak, scenarier/förhandsförhållanden och verktyg som används.

* **[!UICONTROL Upgrade Compatibility Tool]**: Kontrollerar en Adobe Commerce-anpassad instans mot en viss version genom att analysera alla moduler och all kärnkod som är installerade i den. Den returnerar en lista med allvarliga problem, fel och varningar som måste åtgärdas innan du uppgraderar till den senaste versionen av Adobe Commerce. Den identifierar också potentiella problem som måste åtgärdas i koden innan du försöker uppgradera till en nyare version av Adobe Commerce.
Med [!UICONTROL Upgrade Compatibility Tool] kan du identifiera när viktiga kodändringar har gjorts i anpassade funktioner.

* **[!UICONTROL Security Center Widget]**: Visar säkerhetsinsikter för din webbplats.
Säkerhetsinformationen som visas innehåller [Tech [!DNL Stack] Versionskompatibilitet med  [!DNL end of life (EOL)]](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/system-requirements.html), [Adobe Security Bulletin](https://helpx.adobe.com/security/security-bulletin.html), [Recommendations from the [!DNL Security Scan Tool]](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/security-scan.html), and [[!DNL Site-Wide Analysis Tool] säkerhetsrekommendationer för bästa praxis](https://experienceleague.adobe.com/docs/commerce-operations/tools/site-wide-analysis-tool/recommendations.html).<br>
[[!UICONTROL Security Scan Tool] &#x200B;](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/security-scan.html) övervakar Adobe Commerce webbplatser med avseende på säkerhetsrisker. Programmet kan aktivt och effektivt upptäcka skadlig kod i butiker och meddela handlare om det finns säkerhetsrisker, skadlig programvara eller hot, och kan identifiera saknade Adobe Commerce-patchar och uppdateringar.

* **[!UICONTROL Extensions]**: Visar de tillägg som är installerade på din Adobe Commerce-instans. [Information om Adobe Commerce Marketplace](https://commercemarketplace.adobe.com//extensions.html) tillhandahålls, där den är tillgänglig, för de tillägg som anges där.

* **[!UICONTROL Alerts]**: Visar den senaste [!DNL New Relic Managed Alerts] för Adobe Commerce-instansen. Läs mer om [Hanterade aviseringar för Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/managed-alerts/managed-alerts-for-magento-commerce.html) och hur du [får åtkomst till New Relic-tjänster](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/faq/access-new-relic-services.html) i Adobe Commerce Support Knowledge Base.

* **[!UICONTROL Non-recommended software in use]**: Visar den programvara som inte rekommenderas och som används av din Adobe Commerce-instans, baserat på din Adobe Commerce-version. Den programvara som inte rekommenderas listas av [!UICONTROL Name], [!UICONTROL Installed Version] och [!UICONTROL Recommended Version].

* **[!UICONTROL Recommended Patches]**: Visar en kort lista över rekommenderade korrigeringar baserat på båda korrigeringsfiler som du har installerat och din Adobe Commerce-version. En fullständig lista över rekommenderade korrigeringar finns på fliken **[!UICONTROL Patches]**, som också finns i [!DNL Site-Wide Analysis Tool]. Patcharna tillhandahålls av [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html){target="_blank"}. Alla korrigeringsfiler i listan är kompatibla med din aktuella Adobe Commerce-instans.
Om det inte finns några rekommenderade korrigeringar att visa för din Adobe Commerce-instans visas [!DNL widget], **[!UICONTROL No Recommended Patches]**.

## När ska du använda

Sidan **[!UICONTROL Dashboard]** är din snabbaste kommandocentral i [!DNL Site-Wide Analysis Tool] för att du inte bara ska kunna se helhetsbilden av webbplatsens hälsa som helhet, utan du kan även visa och komma åt specifika verktyg, rekommendationer och rapporter för din Adobe Commerce-webbplats via varje [!DNL widget].

## Fördelar

* [!DNL widgets] för [!UICONTROL Security Center], [!UICONTROL Recommendations], [!UICONTROL Extensions] och [!UICONTROL Security Scan] använder alla lättlästa färgkodade interaktiva cirkeldiagram med diagramteckenförklaringar på sidan och räknade summor i mitten för att ange hur många [!UICONTROL Recommendations], [!UICONTROL Extensions] och [!UICONTROL Security Scan Tool] objekt varje funktion har. [!UICONTROL Recommendations] och [!UICONTROL Security Scan Tool] diagram avgränsas av allvarlighetsgrad. [!UICONTROL Extensions] är indelade i fyra klassificeringar: aktuell version, gammal version, inaktiverad och okänd.

* [!DNL New Relic Alerts] listas med den senaste aviseringen överst, inklusive en kort beskrivning och hur länge sedan aviseringen inträffade.

* [!UICONTROL Recommendations] och [!UICONTROL Extensions] [!DNL widgets] har åtkomst till den fullständiga sidan med data för varje funktion genom att klicka på **[!UICONTROL View All]**.

* [!UICONTROL Security Scan Tool] har en **[!UICONTROL View Report]**-länk i fönstret [!DNL widget] som tar dig till sidan [!UICONTROL Recommendations].

* [!DNL Upgrade Compatibility Tool] har en **[!UICONTROL Run Upgrade Scan]**-knapp i fönstret [!DNL widget].

## Bästa tillvägagångssätt för att använda [!UICONTROL Dashboard]

* Klicka på varje [!DNL widget] för att få tillgång till detaljerade data som den ger för att få insikter och förståelse för webbplatsens säkerhet, hälsa, rekommendationer och bästa metoder för att förbättra den.

* Gå till [!UICONTROL Security Scan Tool] [!DNL widget] och klicka på [!UICONTROL View Report] för att visa en [!UICONTROL Recommendations]-rapport för din webbplats.

* Använd länkarna [!DNL External Resources] för att antingen lära dig mer, hålla dig uppdaterad om säkerhetsuppdateringar, uppdateringar och bästa praxis, eller för att dra nytta av insikten i [Adobe Commerce Help Center Support Knowledge Base (Help Center)](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/overview.html), [Adobe Commerce Developer Documentation (DevDocs)](https://developer.adobe.com/commerce/docs/), [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html){target="_blank"}, [Security Center](https://helpx.adobe.com/security.html) och [&#x200B; Observation för Adobe Commerce (OAC)](https://experienceleague.adobe.com/docs/commerce-operations/tools/observation-for-adobe-commerce/intro.html).
