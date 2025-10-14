---
title: 'ACSD-60234: [!DNL PayPal] visar ett felaktigt belopp när rabatt tillämpas'
description: Använd korrigeringsfilen ACSD-60234 för att korrigera Adobe Commerce-problemet där  [!DNL PayPal]  visar ett felaktigt belopp när rabatten tillämpas via betalningsmetoden.
feature: Products, Configuration
role: Admin, Developer
exl-id: 2ce7bde5-02a4-4989-80d6-ab1be0ca5fe9
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 0%

---

# ACSD-60234: [!DNL PayPal] visar ett felaktigt belopp när rabatten tillämpas

Korrigeringen ACSD-60234 åtgärdar ett problem där [!DNL PayPal] visar ett felaktigt belopp när rabatten tillämpas via betalningsmetoden. Den här korrigeringen är tillgänglig när [!DNL Quality Patches Tool (QPT)] 1.1.51 har installerats. Korrigerings-ID är ACSD-60234. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.5.0.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

Adobe Commerce (alla distributionsmetoder) 2.4.5-p1

**Kompatibel med Adobe Commerce-versioner:**

Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.7-p2

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

[!DNL PayPal] visar ett felaktigt belopp när rabatten tillämpas via betalningsmetoden.

<u>Steg som ska återskapas</u>:

1. Konfigurera *[!DNL PayPal Express]* i **[!UICONTROL Stores]** > **[!UICONTROL Config]** > **[!UICONTROL Sales]** > **[!UICONTROL Payment methods]** > **[!DNL PayPal]** > **[!UICONTROL Express checkout]**.
   * [!UICONTROL Enable In-Context Checkout] kan vara [!UICONTROL Yes] eller [!UICONTROL NO]. Problemet återskapas i båda scenarierna.
1. Skapa en *[!UICONTROL Cart Rule]* i **[!UICONTROL Marketing]** > **[!UICONTROL Promotions]** > **[!UICONTROL Cart Price Rules]** > **[!UICONTROL Add New Rule]**.
   * Villkor: Om alla dessa villkor är sanna: *[!UICONTROL Payment Method]* är *[!DNL PayPal Express Checkout]*.
   * Åtgärder: Åtgärder.
1. Skapa en produkt.
1. Gå till butiken, lägg till produkten i kundvagnen och gå sedan till steget **[!UICONTROL Payment Method]** i kassan.
1. Se till att välja *[!DNL PayPal Express]* och verifiera att rabatten används korrekt.
1. Klicka på knappen **[!DNL PayPal]**.
1. Logga in och observera innehållet i popup-fönstret.

<u>Förväntade resultat</u>:

Det belopp som ska betalas som skickas till [!DNL PayPal] inkluderar rabatten som den är i kundvagnen.

<u>Faktiska resultat</u>:

Det totala beloppet som ska betalas inkluderar inte rabatten.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning &#x200B;](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i guiden [!DNL Quality Patches Tool].

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i [!DNL Quality Patches Tool]-handboken.
