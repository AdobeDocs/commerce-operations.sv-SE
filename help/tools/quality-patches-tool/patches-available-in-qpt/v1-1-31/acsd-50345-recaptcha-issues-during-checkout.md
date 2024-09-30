---
title: 'ACSD-50345: reCAPTCHA-problem under utcheckningen'
description: Använd patchen ACSD-50345 för att åtgärda Adobe Commerce-problemet där reCAPTCHA v2- och v3-valideringarna misslyckas vid beställningar och vid utcheckningen.
feature: Checkout, Orders
role: Admin
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '448'
ht-degree: 0%

---

# ACSD-50345: reCAPTCHA-problem under utcheckningen

Korrigeringen ACSD-50345 åtgärdar ett problem där valideringarna reCAPTCHA v2 och v3 misslyckas vid beställning och vid utcheckning. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.31 har installerats. Korrigerings-ID är ACSD-50345. Observera att problemet delvis korrigerades i Adobe Commerce 2.4.6 och att det är planerat att åtgärdas helt i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5-p1

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.3 - 2.4.5-p2

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

**Fall 1**

Google reCAPTCHA v2 läses inte in igen när en misslyckad betalning har skickats.

<u>Steg som ska återskapas</u>

1. Konfigurera **[!UICONTROL Google reCAPTCHA v2]** (*Jag är inte en robot*).
1. Aktivera **[!UICONTROL reCAPTCHA]** för utcheckning.
1. Försök att göra en beställning utan att klicka på **[!UICONTROL reCAPTCHA]**.
1. När användaren får felmeddelandet för den saknade reCAPTCHA-valideringen (*reCAPTCHA misslyckades, försök igen*), klicka på **[!UICONTROL reCAPTCHA]** och försök sedan göra en beställning.

<u>Förväntade resultat</u>

Ordern kommer inte att placeras med felaktig reCAPTCHA.

<u>Faktiska resultat</u>

Ett fel har uppstått - *reCAPTCHA-validering misslyckades, försök igen* och *Ingen sådan kundvagn med ID = 4*

**Case #2**

Google reCAPTCHA v3 Osynlig fungerar inte i kassan och beställningen kan inte placeras. `PlaceOrder`-händelsen har inte utlösts.

<u>Steg som ska återskapas</u>

1. Konfigurera **[!UICONTROL reCAPTCHA v3 Invisible]** från **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Security]**.
1. Aktivera **[!UICONTROL reCAPTCHA v3 Invisible]** för utcheckning/placering av en order på fliken **[!UICONTROL Storefront]**.
1. Försök att göra en beställning med betalningsmetoden [!UICONTROL Check/Money order].

<u>Förväntade resultat</u>

Ordningen ska placeras med **[!UICONTROL reCAPTCHA]** aktiverat.

<u>Faktiska resultat</u>

När du har klickat på knappen **[!UICONTROL Place Order]** inaktiveras den och inget händer längre.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i guiden [!UICONTROL Quality Patches Tool].


Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool]-handboken.
