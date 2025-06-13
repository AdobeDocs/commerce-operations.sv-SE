---
title: 'ACSD-48044: Användning av flera presentkort förhindrar att beställningar görs'
description: Använd patchen ACSD-48044 för att åtgärda Adobe Commerce-problemet där det inte går att lägga in flera presentkort på en enda order med flera leveranser.
feature: Admin Workspace, Gift, Orders
role: Admin
exl-id: c7b72b1f-2f1b-4445-b842-5847d05d5ae9
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '485'
ht-degree: 0%

---

# ACSD-48044: Användning av flera presentkort förhindrar att beställningar görs

Korrigeringen ACSD-48044 åtgärdar ett problem där det inte går att lägga order på flera presentkort på en enda order med flera leveranser. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.25 är installerad. Korrigerings-ID är ACSD-48044. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.6.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5-p1

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.3.4 - 2.4.5-p1

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Att lägga på flera presentkort på en och samma order med flera leveranser förhindrar att beställningar görs.

<u>Steg som ska återskapas</u>:

1. Installera en ren version av Adobe Commerce.
1. Skapa en enkel produkt till priset 100 USD och en annan enkel produkt till priset 10 USD.
1. Logga in på [!UICONTROL Admin panel] och skapa två presentkort.

   * 02 kB8M0H0GRD = $50
   * 00GXM6SUGBLW = $25

1. Skapa en kund med två adresser.
1. Lägg två produkter i kundvagnen.

   * Lägg till produkten $10 först och lägg sedan till produkten $100. Utgåvan kan inte reproduceras om produkten $100 läggs till först.

1. Gå till kundvagnen och lägg till de två presentkorten du skapade.
1. Klicka på **[!UICONTROL Ship to Multiple Addresses]** på kundvagnssidan.
1. Tilldela varje produkt till en annan adress.
1. Gå till sidan **[!UICONTROL Shipping information]**.
1. Gå till sidan **[!UICONTROL Billing information]**.
1. Gå till sidan **[!UICONTROL Review Your Order]** där du kan se problemet.
1. Försök att lägga ordern.

<u>Förväntade resultat</u>:

* Presentkort används korrekt på det totala beloppet.
* Beställningar placeras.

<u>Faktiska resultat</u>:

Presentkortsbelopp blandas med felet *&quot;Korrigera presentkortskoden.&quot;* när du placerar ordern.

* Första produkten:

   * Ta bort presentkort (00GXM6SUGBLW) - $15.00
   * Ta bort presentkort (02 kB8M0H0GRD) - $0,00

* Andra produkten:

   * Ta bort presentkort (00GXM6SUGBLW) - $25.00
   * Ta bort presentkort (02 KB8M0H0GRD) - 35,00 USD

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i guiden [!UICONTROL Quality Patches Tool].


Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i [!DNL Quality Patches Tool]-handboken.
