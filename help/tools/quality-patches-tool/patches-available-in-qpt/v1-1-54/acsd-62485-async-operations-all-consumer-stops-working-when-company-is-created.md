---
title: '"ACSD-62485: "async.operations.all" slutar konsumenten att arbeta när företaget skapas"'
description: Använd patchen ACSD-62485 för att åtgärda Adobe Commerce-problemet där konsumenterna "async.operations.all" slutar att arbeta när ett B2B-företag skapas.
feature: B2B, Companies
role: Admin, Developer
source-git-commit: 8061f6df01c3c308b46e6164300192b01359ce94
workflow-type: tm+mt
source-wordcount: '315'
ht-degree: 0%

---

# ACSD-62485: `async.operations.all`-konsumenten slutar att arbeta när företaget skapas

ACSD-62485-korrigeringen åtgärdar ett problem där `async.operations.all`-konsumenten slutar att arbeta när ett B2B-företag skapas. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.54 har installerats. Korrigerings-ID är ACSD-62485. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.8.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6-p7

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.6-p7, 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Konsumenten `async.operations.all` avbryter bearbetningen av meddelanden om ett B2B-företag skapas asynkront medan konsumenten fortfarande körs.

<u>Förutsättningar</u>:

B2B-moduler installeras och aktiveras.

<u>Steg som ska återskapas</u>:

1. Skapa två kunder.
1. Skicka en REST-satsbegäran för att skapa två företag och tilldela de kunder som skapats som företagsadministratörer.
1. Starta konsumenten med följande kommando:

   ``` bin/magento queue:consumer:start async.operations.all --max-messages=20000 ```

<u>Förväntade resultat</u>:

Konsumenten behandlar 20 000 meddelanden och avslutas med framgång.

<u>Faktiska resultat</u>:

Konsumenten slutar arbeta omedelbart efter avrättningen.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.
