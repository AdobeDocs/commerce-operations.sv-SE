---
title: 'ACSD-54966: Korrigera för återanvändning av kupongkoder efter misslyckade beställningar'
description: Använd patchen ACSD-54966 för att åtgärda Adobe Commerce-problemet och förhindra återanvändning av kupongkoder som begränsas per kampanj och kundvagn efter en tidigare misslyckad beställning.
feature: Promotions/Events, Shopping Cart, Orders
role: Admin, Developer
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 0%

---

# ACSD-54966: Korrigera för återanvändning av kupongkoder efter misslyckade beställningar

Korrigeringen ACSD-54966 åtgärdar ett problem som förhindrar återanvändning av kupongkoder som begränsas per kund efter en tidigare misslyckad order. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.42 är installerad. Korrigerings-ID är ACSD-54966. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6-p1

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5 - 2.4.6-p3

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

En kupongkod som är begränsad för engångsbruk per kund kan inte återanvändas efter en tidigare misslyckad order.

<u>Steg som ska återskapas</u>:

1. Ställ in en kundvagnsprisregel med *[!UICONTROL Uses per Customer]* = *1*.
1. Fortsätt att göra ett köp med den tilldelade kupongkoden.
1. Avbryt beställningen från adminpanelen eller utför beställningen med ett betalningsfel.
1. Kör kommandot: `bin/magento queue:consumers:start sales.rule.update.coupon.usage`
1. Försök att lägga en efterföljande order med samma kupongkod för samma kund.

<u>Förväntade resultat</u>:

När kunden har annullerat beställningen eller påträffat ett betalningsfel kan den återanvända kupongkoden för ett nytt köp.

<u>Faktiska resultat</u>:

Kunden kan inte återanvända kupongkoden.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i guiden [!UICONTROL Quality Patches Tool].


Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool]-handboken.
