---
title: Översikt över skyddsprofilen för innehåll
description: Lär dig hur du förbättrar säkerhetspositionen i din Adobe Commerce- eller Magento Open Source-butik med hjälp av en skyddsprofil för innehåll.
source-git-commit: 1a608e8a5986026d5a187dc8cbd358fed2db5d9e
workflow-type: tm+mt
source-wordcount: '429'
ht-degree: 0%

---


# Översikt över skyddsprofilen för innehåll

En Content Security Policy (CSP) kan tillhandahålla ytterligare lager av skydd för Adobe Commerce- och Magento Open Source-installationer genom att hjälpa till att upptäcka och minska XSS-attacker (Cross-Site Scripting) och relaterade datainjektionsangrepp. Denna vanliga attackvektor fungerar genom att man injicerar skadligt innehåll som felaktigt hävdas ha sitt ursprung på webbplatsen. När det skadliga innehållet har lästs in och körts kan det initiera obehörig överföring av data.

CSP tillhandahåller en standardiserad uppsättning direktiv som talar om för webbläsaren vilka innehållsresurser som kan betraktas som tillförlitliga och vilka som ska blockeras. Med hjälp av noggrant definierade principer kan CSP begränsa webbläsarinnehåll så att endast godkända resurser kan visas.

## Konfiguration

För att undvika att störa webbplatsåtgärder kan CSP implementeras i faser. CSP har två grundläggande lägen: `report-only mode` och `restrict mode`. Utgåvan av Adobe Commerce 2.3.5 är den första fasen av vår implementering och gör CSP tillgängligt i `report-only mode` som standard. I en framtida release `restrict mode` är aktiverat som standard för ytterligare användbart skydd.

**Läget Endast rapport**: Webbläsaren instrueras att rapportera policyöverträdelser, men inte att verkställa dem. Varje gång en begärd resurs bryter mot CSP loggar webbläsaren de resulterande felen till konsolen. Konsolloggen kan sedan användas för att undersöka orsaken till varje överträdelse.

Det är viktigt att granska alla CSP-fel när de inträffar och förfina profilerna tills alla nödvändiga resurser vitlistas. Det är säkert att växla till `restrict mode` när inga fler fel inträffar. Annars kan en dåligt konfigurerad CSP göra att webbläsaren visar en tom sida med flera konsolfel. Med en korrekt konfigurerad CSP kan vitlistat innehåll levereras utan någon märkbar påverkan på prestandan.

**Begränsa läge**: Webbläsaren instrueras att tillämpa alla innehållsprinciper och begränsa publiceringen till godkända resurser. Eftersom CSP är konfigurerat från servern, i stället för från administratören, behöver de flesta handlare hjälp av en systemintegratör eller utvecklare för att kunna konfigurera den korrekt. Se [Skyddsprofiler för innehåll](https://developer.adobe.com/commerce/php/development/security/content-security-policies/) i _Commerce PHP-tillägg_ utvecklarhandbok.

## Rapportering

Som standard skickar CSP fel till webbläsarkonsolen, men kan konfigureras för att samla in felloggar via HTTP-begäran. Dessutom finns det flera tredjepartstjänster som du kan använda för att övervaka, samla in och rapportera CSP-överträdelser.

[Rapport-URI](https://report-uri.io/) är en tjänst som övervakar CSP-överträdelser och visar resultatet i en kontrollpanel. Både handlare och utvecklare kan använda tjänsten för att ta emot rapporter när CSP-fel inträffar.
