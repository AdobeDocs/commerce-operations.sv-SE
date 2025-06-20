---
title: 'ACSD-49433: Standardbelopp som visas som delsumma i kundvagn för presentkort'''
description: Använd patchen ACSD-49433 för att korrigera Adobe Commerce-problemet där standardbeloppet visas som delsumma i kundvagnen för presentkort med ett öppet belopp.
feature: Admin Workspace, Gift, Orders, Shopping Cart
role: Admin
exl-id: 22691e35-0491-4935-8e7c-148900706491
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '391'
ht-degree: 0%

---

# ACSD-49433: Standardbelopp som visas som delsumma i kundvagn för presentkort

Korrigeringsfilen ACSD-49433 åtgärdar ett problem där standardbeloppet visas som delsumma i presentkortets kundvagn med ett öppet belopp. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.28 har installerats. Korrigerings-ID är ACSD-49433. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.3-p1

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.3 - 2.4.6

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Standardbeloppet visas som delsumma i kundvagnen för presentkortet med ett öppet belopp.

<u>Steg som ska återskapas</u>:

1. Skapa ett presentkort.
1. Kontrollera att det öppna beloppet är inställt på *[!UICONTROL Yes]* (mellan 50 och 500 USD).
1. Gå till produkten [!UICONTROL Gift Card] i butiken och välj ett annat belopp i listrutan.
1. Ange $100 i USD.
1. Fyll i andra fält och lägg dem i kundvagnen.
1. Gå till minivagnen eller kundvagnen.

<u>Förväntade resultat</u>:

Delsumman visar beloppet som användaren har angett.

<u>Faktiska resultat</u>:

Delsumman visar standardbeloppet för presentkortet.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i guiden [!UICONTROL Quality Patches Tool].


Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i [!DNL Quality Patches Tool]-handboken.
