---
title: 'ACSD-65202: På sidan Mitt konto visas inte senaste beställningar från andra butiksvyer'
description: Använd patchen ACSD-65202 för att åtgärda Adobe Commerce-problemet där sidan Mitt konto inte visar de senaste beställningarna från andra butiksvyer i samma butik.
feature: Orders, User Account
role: Admin, Developer
type: Troubleshooting
exl-id: 031f12f2-1b70-4cbc-92a0-8eb561e34067
source-git-commit: b1912bbc5aabd36067563326ee5c6bb84e14441d
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 0%

---

# ACSD-65202: Sidan [!UICONTROL My Account] visar inte senaste beställningar från andra butiksvyer

Korrigeringen ACSD-65202 åtgärdar ett problem där sidan **[!UICONTROL My Account]** inte visar senaste beställningar från andra butiksvyer i samma butik. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.65 har installerats. Korrigerings-ID är ACSD-65202. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.9.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4-p12

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.7-p5

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

När du går till kundkontosidan (avsnitt **[!UICONTROL My Account]**) visas inte de senaste beställningarna i en annan butiksvy. När du går till orderhistoriken (avsnitt *[!UICONTROL My Orders]*) ser du alla order i båda butiksvyerna.

<u>Steg som ska återskapas</u>:

1. Installera Adobe Commerce.
1. Skapa en ny butiksvy på panelen *Admin* och ange dess kod som, *second*, för att identifiera vyn.
1. Skapa en enkel produkt och indexera om den.
1. Skapa ett kundkonto och placera en order i standardbutiksvyn vars kod är *standard*.
1. Gå till sidan **[!UICONTROL My Orders]** och kontrollera att ordningen är synlig i båda vyerna, till exempel:
1. Standard: https://localhost/pub/default/sales/order/history/
1. Andra: https://localhost/pub/second/sales/order/history/

1. Gå till sidan **[!UICONTROL My Account]** i båda butiksvyerna:
1. Standard: https://localhost/pub/default/customer/account/
1. Andra: https://localhost/pub/second/customer/account/

<u>Förväntade resultat</u>:

Du kan se beställningar från båda butiksvyerna på sidan Beställningar. Det är samma butik, bara en annan butiksvy.

<u>Faktiska resultat</u>:

Beteendet är inkonsekvent. Beställningar visas inte i den andra butiksvyn.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning &#x200B;](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.
