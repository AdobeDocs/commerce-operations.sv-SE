---
title: 'ACSD-49286: Produkten har lagts till två gånger i kundvagnen när det finns flera produktwidgetar'
description: Använd patchen ACSD-49286 för att åtgärda problemet med Adobe Commerce där produkten läggs till två gånger i en kundvagn när det finns flera produktwidgetar på sidan.
feature: Admin Workspace, Orders, Products, Shopping Cart
role: Admin
exl-id: 03fdaafe-5566-4b75-a0eb-e0cba3dad3e7
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '414'
ht-degree: 0%

---

# ACSD-49286: Produkten har lagts till två gånger i kundvagnen när det finns flera produktwidgetar

Korrigeringen ACSD-49286 åtgärdar ett problem där produkten läggs till två gånger i en varukorg när det finns flera produktwidgetar på sidan. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.28 har installerats. Korrigerings-ID är ACSD-49286. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5-p1

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.3 - 2.4.6

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Produkten läggs till två gånger i en kundvagn när det finns flera produktwidgetar på sidan.

<u>Steg som ska återskapas</u>:

1. Logga in som administratör och gå till **[!UICONTROL Admin]** > **[!UICONTROL Content]** > **[!UICONTROL Page]** > **[!UICONTROL Home Page]**
1. Klicka på **[!UICONTROL Edit]** med [!DNL Page Builder] i innehållsavsnittet.
1. Lägg till två radelement i **[!UICONTROL Content]**.
1. Lägg till produkter i båda radelementen.
1. På den första raden anger du produktutseendet som [!UICONTROL Product Grid] och väljer en kategori att visa.
1. I den andra raden anger du produktutseendet som [!UICONTROL Product Carousel] och väljer en annan kategori som ska visas.
1. Gå till butiken **[!UICONTROL Home Page]** och lägg till en produkt från produktrutnätet.
1. Lägg till en annan produkt från [!UICONTROL Product Carousel].

<u>Förväntade resultat</u>:

Produktkvantiteten får inte dubbleras efter att en produkt har lagts till i varukorgen från [!UICONTROL Product Grid].

<u>Faktiska resultat</u>:

Produktkvantiteten dubbleras efter att en produkt har lagts till i kundvagnen från [!UICONTROL Product Grid].

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur. 

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i guiden [!UICONTROL Quality Patches Tool].


Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i [!DNL Quality Patches Tool]-handboken.
