---
title: 'ACSD-49065: Offertobjekt visas inte i administratören'
description: Använd patchen ACSD-49065 för att åtgärda Adobe Commerce-problemet där offertobjekten inte syns i administratören om de bara tilldelats det anpassade lagret.
feature: Admin Workspace, B2B, Orders, Quotes
role: Admin
exl-id: fc3bea92-305b-4598-9915-3422d61c76ec
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '410'
ht-degree: 0%

---

# ACSD-49065: Offertobjekt visas inte i administratören

Korrigeringen ACSD-49065 åtgärdar ett problem där offertobjekten inte är synliga i administratören om de bara är tilldelade till det anpassade lagret. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.28 har installerats. Korrigerings-ID är ACSD-49065. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4-p2

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.3 - 2.4.6

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Offertobjekten visas inte i administratören om de bara är tilldelade till det anpassade arkivet.

Förutsättningar:

Modulerna **[!UICONTROL B2B]** och **[!UICONTROL Inventory]** måste vara installerade.

<u>Steg som ska återskapas</u>:

1. Aktivera **[!UICONTROL Company]** och **[!UICONTROL B2B Quote]** under **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B Features]**.
1. Skapa en sekundär **[!UICONTROL Inventory Source]** och tilldela den till en sekundär **[!UICONTROL Inventory Stock]**.
1. Skapa en ny produkt genom att endast tilldela den sekundära (icke-standard) **[!UICONTROL Inventory Source]**.
1. Gå till butiken och skapa ett nytt företagskonto. Logga in som **[!UICONTROL Company Admin]** och lägg till den skapade produkten i kundvagnen.
1. Navigera till kundvagnen och *[!UICONTROL Request a Quote]*.
1. Gå till administratören och visa den begärda offerten på **[!UICONTROL Sales]** > **[!UICONTROL Quotes]**.

<u>Förväntade resultat</u>:

Objekten visas i den nya offerten som skapats med nya produkter utan att produkterna sparas om.

<u>Faktiska resultat</u>:

Avsnittet *[!UICONTROL Items Quoted]* är tomt. Om du sparar om den nya produkten visas objekten.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i guiden [!UICONTROL Quality Patches Tool].


Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i [!DNL Quality Patches Tool]-handboken.
