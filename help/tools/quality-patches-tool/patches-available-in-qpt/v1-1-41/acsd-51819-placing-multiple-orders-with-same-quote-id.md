---
title: 'ACSD-51819: Placera flera order med ett enda offert-ID'
description: Använd patchen ACSD-51819 för att åtgärda Adobe Commerce-problemet där flera beställningar kan göras via samma offert-ID.
feature: Orders, Checkout
role: Admin, Developer
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---

# ACSD-51819: Placera flera order med ett enda offert-ID

Korrigeringen ACSD-51819 åtgärdar ett problem där flera order kan beställas med samma offert-ID. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.41 är installerad. Korrigerings-ID är ACSD-51819. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4-p2

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.4-p3

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Flera order kan placeras med samma offert-ID.

<u>Steg som ska återskapas</u>:

1. Logga in som användare.
1. Lägg till artiklar i kundvagnen och fortsätt till kassan.
1. Välj en betalningsmetod men klicka inte på knappen **[!UICONTROL Place Order]**.
1. Logga in på samma konto i en annan webbläsare.
1. Gå till kassan med samma objekt utan att klicka på knappen **[!UICONTROL Place Order]**.
1. Klicka på knappen **[!UICONTROL Place Order]** i båda systemen samtidigt.
1. Validera beställningarna i båda webbläsarna.

<u>Förväntade resultat</u>:

Endast den första beställningen från en webbläsare kan bearbetas.

<u>Faktiska resultat</u>:

Beställningar har gjorts i båda webbläsarna.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i guiden [!UICONTROL Quality Patches Tool].


Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool]-handboken.
