---
title: 'ACSD-56280: Inköp av presentregister har inte slutförts'
description: Använd patchen ACSD-56280 för att åtgärda Adobe Commerce-problemet där inköp av presentregister inte är slutförda
feature: Checkout
role: Admin
exl-id: a79f789f-999f-4d11-b7ee-2c065b681efb
source-git-commit: ab02be3396e68044e9356f89fba6b55aa880056f
workflow-type: tm+mt
source-wordcount: '360'
ht-degree: 0%

---

# ACSD-56280: Inköp av presentregister har inte slutförts

>[!NOTE]
>
>Den här korrigeringen har ersatts av [ACSD-63283](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-58/acsd-63283-resolving-gift-registry-email-and-order-placement-issues-in-adobe-commerce.md).

Korrigeringen ACSD-56280 åtgärdar ett problem där inköp av presentregister inte har slutförts. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/sv/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.44 har installerats. Korrigerings-ID är ACSD-56280. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.6-p3

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Inköpen från presentregistret har inte slutförts.

<u>Steg som ska återskapas</u>:

1. Logga in som kund och lägg till en **[!UICONTROL product]** i presentregistret.
1. Dela presentregisterlänken.
1. Öppna presentregisterlänken i ett annat webbläsare/inkognito-fönster.
1. Lägg kvantiteten och lägg artiklarna i vagnen.
1. Gå till **[!UICONTROL Checkout Page]**, välj **[!UICONTROL shipping method]** (eftersom leveransadressen redan har valts, tillhandahålls av registranten).
1. Välj betalningsmetod.
1. Klicka på knappen Placera ordning.

<u>Förväntade resultat</u>:

Beställningen ska placeras.

<u>Faktiska resultat</u>:

Ordningen har inte placerats och felet som visas är `Call to a member function getUpdatedQty() on null`.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](https://experienceleague.adobe.com/sv/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i guiden [!UICONTROL Quality Patches Tool].


Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i [!DNL Quality Patches Tool]-handboken.
