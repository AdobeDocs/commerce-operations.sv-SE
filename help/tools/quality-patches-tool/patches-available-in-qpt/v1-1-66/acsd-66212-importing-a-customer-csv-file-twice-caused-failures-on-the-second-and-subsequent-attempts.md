---
title: 'ACSD-66212: Vid import av CSV-kundfil två gånger uppstod fel vid andra och efterföljande försök'
description: Använd patchen ACSD-66212 för att åtgärda Adobe Commerce-problemet där import av en CSV-kundfil orsakade fel på den andra och efterföljande försök två gånger.
feature: Data Import/Export, Customers
role: Admin, Developer
source-git-commit: 97a5979a189e43b737c44cfe7a65025effae711c
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 0%

---


# ACSD-66212: Vid import av CSV-kundfil två gånger uppstod fel vid andra och efterföljande försök

Korrigeringen ACSD-66212 åtgärdar ett problem där import av en CSV-kundfil två gånger orsakade fel på den andra och efterföljande försök. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.66 har installerats. Korrigerings-ID är ACSD-66212. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.9.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.8

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.8

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Om en kund-CSV-fil importerades två gånger uppstod fel vid det andra och efterföljande försök.

<u>Steg som ska återskapas</u>:

Importera en CSV-fil som innehåller kunddata, inklusive kundstatus.

<u>Förväntade resultat</u>:

Statusen importeras och exporteras korrekt.

<u>Faktiska resultat</u>:

Ett fel inträffar under importen:

```
General system exception happened
Additional data: <div class="messages"><div class="message message-error error"><div data-ui-id="messages-message-error" >SQLSTATE[42000]: Syntax error or access violation: 1064 You have an error in your SQL syntax; check the manual that corresponds to your MariaDB server version for the right syntax to use near " at line 1, query was: INSERT INTO company_advanced_customer_entity (customer_id*) VALUES </div></div></div>
```

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.
