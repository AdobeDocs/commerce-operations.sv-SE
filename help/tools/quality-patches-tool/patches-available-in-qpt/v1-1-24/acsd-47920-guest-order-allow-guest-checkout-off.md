---
title: 'ACSD-47920: En gästanvändare kan göra beställningar via REST API även när [!UICONTROL Allow Guest Checkout] är av'
description: Använd ACSD-47920-korrigeringen för att åtgärda Adobe Commerce-problemet där beställningar kan göras via REST API som gästanvändare även när [!UICONTROL Allow Guest Checkout] är inaktiverad.
feature: REST, Checkout, Orders
role: Admin
exl-id: 27c74803-a3f3-46bc-9eb8-8e2c72c30cd9
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '373'
ht-degree: 0%

---

# ACSD-47920: En gästanvändare kan göra beställningar via REST API även när **[!UICONTROL Allow Guest Checkout]** är av

Korrigeringen ACSD-47920 åtgärdar ett problem där beställningar kan göras via REST API som gästanvändare även när **[!UICONTROL Allow Guest Checkout]** är inaktiverad. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.24 har installerats. Korrigerings-ID är ACSD-47920. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.6.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.3-p1

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Beställningar kan placeras via Rest API som gästanvändare även när **[!UICONTROL Allow Guest Checkout]** är inaktiverat.

<u>Steg som ska återskapas</u>:

1. Gå till Adobe Commerce Admin > **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Sales]** > **[!UICONTROL Checkout]** > **[!UICONTROL Checkout Options]** > och ställ in **[!UICONTROL Allow Guest Checkout]** på _Nej_.
1. Använd REST API för att lägga till en produkt i en kundvagn och göra en beställning.

<u>Förväntade resultat</u>:

API för gästutcheckning returnerar felet *[!UICONTROL Sorry, guest checkout is not available]* om **[!UICONTROL Allow Guest Checkout]** är inställt på _Nej_.

<u>Faktiska resultat</u>:

Gästutchecknings-API tillåter en beställning att placeras även om **[!UICONTROL Allow Guest Checkout]** är inställt på _Nej_.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i guiden [!UICONTROL Quality Patches Tool].


Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i [!DNL Quality Patches Tool]-handboken.
