---
title: 'ACSD-51230: Presentkortskontot har tagits bort'
description: Använd patchen ACSD-51230 för att åtgärda Adobe Commerce-problemet där presentkortskontot tas bort när den partiella återbetalningen av en enkel produkt bearbetas från en beställning.
feature: Customer Service, Gift, Marketing Tools
role: Admin
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '420'
ht-degree: 0%

---

# ACSD-51230: Presentkortskontot har tagits bort

Korrigeringen ACSD-51230 åtgärdar ett problem där presentkortskontot tas bort när den partiella återbetalningen av en enkel produkt bearbetas från en beställning. Den här korrigeringen är tillgänglig när [!DNL Quality Patches Tool (QPT)] 1.1.32 har installerats. Korrigerings-ID är ACSD-51230. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.3

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.3.7 - 2.4.6

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Presentkortskontot tas bort när en partiell återbetalning av en enkel produkt bearbetas från en order.

<u>Steg som ska återskapas</u>:

1. Skapa en beställning med ett *presentkort* och en *enkel produkt* (t.ex. *lägg till: SKU: GI000XX000XXX, SKU: PC046CP042076*) - (alla betalnings- och leveransmetoder fungerar).
1. Fakturera ordern.
1. Gå till **[!UICONTROL Marketing]** > **[!UICONTROL Gift Card accounts]**. Ett konto skapas för presentkortet.
1. Gå till **[!UICONTROL Order]** och skapa en **[!UICONTROL Credit Memo]**.
1. Ändra kvantiteten för *presentkortet* till 0 och uppdatera det. Detta skapar en partiell återbetalning för den *enkla produkten*.
1. Klicka på **[!UICONTROL Refund]**.
1. Uppdatera **[!UICONTROL Marketing]** > **[!UICONTROL Gift Card accounts]**. Det nyligen skapade kontot tas bort.

<u>Förväntade resultat</u>

Presentkortskontot kan användas eftersom återbetalningen inte skapades för presentkortet.

<u>Faktiska resultat</u>

Presentkortskontot tas bort och presentkortet återbetalas inte.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i guiden [!UICONTROL Quality Patches Tool].


Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool]-handboken.
