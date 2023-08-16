---
title: '[!DNL Dashboard]'
description: Läs mer om [!DNL Dashboard] i [!DNL Site-Wide Analysis Tool], element, när de ska användas, fördelar och bästa praxis.
exl-id: 37d848ff-2cff-48b1-8391-520531300bbc
source-git-commit: 786be8bfa915fe82d9316f51662b20bde71abbaa
workflow-type: tm+mt
source-wordcount: '771'
ht-degree: 0%

---

# [!UICONTROL Dashboard]

The [!UICONTROL Dashboard] i korthet [!DNL widgets] som ger en&quot;enda ruta av glasvy&quot; av hälsotillståndet och den aktuella statusen på din Adobe Commerce-webbplats. Varje [!DNL widget] innehåller en åtkomstlänk till varje funktions sida, till varje verktyg eller till rapporter (beroende på [!DNL widget]).
Det finns också en lista över [!UICONTROL External Resources] länkar till Adobe Commerce, inklusive [Adobe Commerce Help Center Support Knowledge Base (Help Center)](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/overview.html), [Adobe Commerce Developer Documentation (DevDocs)](https://developer.adobe.com/commerce/docs/), [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html){target="_blank"}, [Security Center](https://helpx.adobe.com/security.html)och [Observation för Adobe Commerce (OAC)](https://experienceleague.adobe.com/docs/commerce-operations/tools/observation-for-adobe-commerce/intro.html).

## Element

* **[!UICONTROL Recommendations]**: Visar rekommendationer om de bästa metoderna för din webbplats. Recommendations (problem som hittats och rekommendationer som ska åtgärdas) sorteras efter prioritet - P0 (kritiskt) till P4 (meddelande).
Recommendations innehåller beskrivning, rekommendation, webbplatseffekt, rotorsak, scenarier/förhandsvillkor och verktyg som används.

* **[!UICONTROL Upgrade Compatibility Tool]**: Kontrollerar en Adobe Commerce-anpassad instans mot en viss version genom att analysera alla moduler och all kärnkod som är installerade i den. Den returnerar en lista med allvarliga problem, fel och varningar som måste åtgärdas innan du uppgraderar till den senaste versionen av Adobe Commerce. Den identifierar också potentiella problem som måste åtgärdas i koden innan du försöker uppgradera till en nyare version av Adobe Commerce.
The [!UICONTROL Upgrade Compatibility Tool] gör att du kan identifiera när viktiga kodändringar har gjorts i anpassade funktioner.

* **[!UICONTROL Security Center Widget]**: Visar säkerhetsinsikter för din webbplats.
Den säkerhetsinformation som visas innehåller [Tech [!DNL Stack] Versionskompatibilitet med [!DNL end of life (EOL)]](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/system-requirements.html), [Adobe Security Bulletin](https://helpx.adobe.com/security/security-bulletin.html), [Recommendations from the [!DNL Security Scan Tool]](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/security-scan.html), and [[!DNL Site-Wide Analysis Tool] Best Practice Security Recommendations](https://experienceleague.adobe.com/docs/commerce-operations/tools/site-wide-analysis-tool/recommendations.html).<br>
The [[!UICONTROL Security Scan Tool]](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/security-scan.html) övervakar Adobe Commerce webbplatser för att se om det finns säkerhetsrisker. Programmet kan aktivt och effektivt upptäcka skadlig kod i butiker och meddela handlare om det finns säkerhetsrisker, skadlig programvara eller hot, och kan identifiera saknade Adobe Commerce-patchar och uppdateringar.

* **[!UICONTROL Extensions]**: Visar de tillägg som är installerade på din Adobe Commerce-instans. [Adobe Commerce Marketplace](https://marketplace.magento.com/extensions.html) Information tillhandahålls, om sådan finns, för de tillägg som anges där.

* **[!UICONTROL Alerts]**: Visar den senaste [!DNL New Relic Managed Alerts] för Adobe Commerce. Läs mer om [Hanterade aviseringar för Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/managed-alerts/managed-alerts-for-magento-commerce.html) och hur [Få tillgång till New Relic tjänster](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/faq/access-new-relic-services.html) i Adobe Commerce Support Knowledge Base.

* **[!UICONTROL Non-recommended software in use]**: Visar den programvara som inte rekommenderas och som används av din Adobe Commerce-instans, baserat på din Adobe Commerce-version. Programvaran som inte rekommenderas listas i [!UICONTROL Name], [!UICONTROL Installed Version]och [!UICONTROL Recommended Version].

* **[!UICONTROL Recommended Patches]**: Visar en kort lista över rekommenderade korrigeringsfiler baserat på båda korrigeringsfilerna som du har installerat och din Adobe Commerce-version. En fullständig lista över rekommenderade korrigeringsfiler finns på **[!UICONTROL Patches]** -fliken, som också finns i [!DNL Site-Wide Analysis Tool]. Patcharna finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html){target="_blank"}. Alla korrigeringsfiler i listan är kompatibla med din aktuella Adobe Commerce-instans.
Om det inte finns några rekommenderade korrigeringar att visa för din Adobe Commerce-instans är detta [!DNL widget] kommer att visas **[!UICONTROL No Recommended Patches]**.

## När ska du använda

The **[!UICONTROL Dashboard]** finns i kommandocentralen på [!DNL Site-Wide Analysis Tool] så att du inte bara kan se helhetsbilden av webbplatsens hälsa som helhet, utan även se och få tillgång till specifika verktyg, rekommendationer och rapporter för Adobe Commerce webbplats via varje [!DNL widget].

## Fördelar

* The [!DNL widgets] for [!UICONTROL Security Center], [!UICONTROL Recommendations], [!UICONTROL Extensions]och [!UICONTROL Security Scan] alla använder lättlästa färgkodade interaktiva cirkeldiagram med diagramteckenförklaringar på sidan och räkningssummor i mitten för att ange hur många [!UICONTROL Recommendations], [!UICONTROL Extensions]och [!UICONTROL Security Scan Tool] objekt som varje funktion har. [!UICONTROL Recommendations] och [!UICONTROL Security Scan Tool] diagram avgränsas av allvarlighetsgrad. [!UICONTROL Extensions] är indelade i fyra klassificeringar: aktuell version, gammal version, inaktiverad och okänd.

* [!DNL New Relic Alerts] visas med den senaste varningen överst, inklusive en kort beskrivning och hur länge sedan varningen inträffade.

* The [!UICONTROL Recommendations] och [!UICONTROL Extensions] [!DNL widgets] få tillgång till den fullständiga sidan med data för varje funktion genom att klicka **[!UICONTROL View All]**.

* The [!UICONTROL Security Scan Tool] har en **[!UICONTROL View Report]** i [!DNL widget] fönstret som tar dig till [!UICONTROL Recommendations] sida.

* The [!DNL Upgrade Compatibility Tool] har en **[!UICONTROL Run Upgrade Scan]** knappen i [!DNL widget] -fönstret.

## Bästa tillvägagångssätt för att använda [!UICONTROL Dashboard]

* Klicka på varje [!DNL widget] för att få tillgång till de detaljerade data som den ger för att få insikter och förståelse för webbplatsens säkerhet, hälsa, rekommendationer och bästa metoder för att förbättra den.

* Gå till [!UICONTROL Security Scan Tool] [!DNL widget] och klicka [!UICONTROL View Report] för att visa en [!UICONTROL Recommendations] för din webbplats.

* Använd [!DNL External Resources] länkar för att antingen lära sig mer information, hålla sig uppdaterad om säkerhetsuppdateringar, uppdateringar och bästa praxis, eller utnyttja insikterna i [Adobe Commerce Help Center Support Knowledge Base (Help Center)](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/overview.html), [Adobe Commerce Developer Documentation (DevDocs)](https://developer.adobe.com/commerce/docs/), [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html){target="_blank"}, [Security Center](https://helpx.adobe.com/security.html)och [Observation för Adobe Commerce (OAC)](https://experienceleague.adobe.com/docs/commerce-operations/tools/observation-for-adobe-commerce/intro.html).
