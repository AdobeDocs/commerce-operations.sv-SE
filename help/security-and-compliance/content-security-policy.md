---
title: Översikt över skyddsprofilen för innehåll
description: Lär dig hur du förbättrar säkerhetspositionen i din Adobe Commerce-butik med hjälp av en skyddsprofil för innehåll.
exl-id: 81070a09-5f8f-48b1-b542-1443dbd43f5f
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '493'
ht-degree: 0%

---

# Översikt över skyddsprofilen för innehåll

En Content Security Policy (CSP) kan tillhandahålla ytterligare lager av skydd för Adobe Commerce-installationer genom att hjälpa till att upptäcka och minska attacker som rör XSS (Cross-Site Scripting) och relaterade datainmatningsattacker. Denna vanliga attackvektor fungerar genom att man injicerar skadligt innehåll som felaktigt hävdas ha sitt ursprung på webbplatsen. När det skadliga innehållet har lästs in och körts kan det initiera obehörig överföring av data.

CSP tillhandahåller en standardiserad uppsättning direktiv som talar om för webbläsaren vilka innehållsresurser som kan betraktas som tillförlitliga och vilka som ska blockeras. Med hjälp av noggrant definierade principer kan CSP begränsa webbläsarinnehåll så att endast godkända resurser kan visas.

## Konfiguration

För att undvika att störa webbplatsåtgärder kan CSP implementeras i faser. CSP har två grundläggande åtgärdslägen: `report-only mode` och `restrict mode`.

**Läge för enbart rapport**: Webbläsaren instrueras att rapportera policyöverträdelser, men framtvinga dem inte. Varje gång en begärd resurs bryter mot CSP loggar webbläsaren de resulterande felen till konsolen. Konsolloggen kan sedan användas för att undersöka orsaken till varje överträdelse.

Det är viktigt att granska alla CSP-fel när de inträffar och förfina profilerna tills alla nödvändiga resurser vitlistas. Det är säkert att växla till `restrict mode` när inga fler fel inträffar. Annars kan en dåligt konfigurerad CSP göra att webbläsaren visar en tom sida med flera konsolfel. Med en korrekt konfigurerad CSP kan vitlistat innehåll levereras utan någon märkbar påverkan på prestandan.

**Begränsa läge**: Webbläsaren instrueras att framtvinga alla innehållsprinciper och begränsa publiceringen till godkända resurser.

Den första fasen av Adobe Commerce CSP-implementeringen introducerades i Adobe Commerce 2.3.5 och gjordes tillgänglig i `report-only mode` som standard.  I Adobe Commerce 2.4.7 och senare konfigureras CSP i `restrict-mode` som standard för betalningssidor i butiks- och administratörsområdena och i `report-only`-läge för alla andra sidor. Motsvarande CSP-rubrik innehåller inte nyckelordet `unsafe-inline` i direktivet `script-src` för betalningssidor. Dessutom tillåts bara inline-skript i vitlista.

Eftersom CSP är konfigurerat från servern, i stället för från administratören, behöver de flesta handlare hjälp av en systemintegratör eller utvecklare för att kunna konfigurera den på rätt sätt. Se [Säkerhetsprinciper för innehåll](https://developer.adobe.com/commerce/php/development/security/content-security-policies/) i _Commerce PHP-utvecklarhandboken_.


## Rapportering

Som standard skickar CSP fel till webbläsarkonsolen, men kan konfigureras för att samla in felloggar via HTTP-begäran. Dessutom finns det flera tredjepartstjänster som du kan använda för att övervaka, samla in och rapportera CSP-överträdelser. CSP-fel kan rapporteras till en slutpunkt för samling genom att lägga till URI:n från administratören eller från filen `config.xml` för en anpassad modul.  Se [Rapportera URI-konfiguration](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#report-uri-configuration) i _Commerce PHP Extensions Developer Guide_.

[Rapport-URI](https://report-uri.io/) är en tjänst som övervakar CSP-överträdelser och visar resultaten på en instrumentpanel. Både handlare och utvecklare kan använda tjänsten för att ta emot rapporter när CSP-fel inträffar.
