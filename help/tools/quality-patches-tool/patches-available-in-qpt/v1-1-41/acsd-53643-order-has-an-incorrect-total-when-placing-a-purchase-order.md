---
title: "ACSD-53643: Ordern har ett felaktigt totalt värde när en inköpsorder placeras"
description: Använd patchen ACSD-53643 för att åtgärda Adobe Commerce-problemet där ordern har ett felaktigt totalt ordervärde när en inköpsorder med inaktiverade eller färdiga produkter läggs.
feature: B2B
role: Admin, Developer
source-git-commit: d722ba5ba25ffc03d87b9eddeb2830353124055d
workflow-type: tm+mt
source-wordcount: '463'
ht-degree: 0%

---

# ACSD-53643: Ordern har ett felaktigt belopp när en inköpsorder placeras

Korrigeringen ACSD-53643 åtgärdar ett problem där ordern har ett felaktigt totalt ordervärde när en inköpsorder med inaktiverade produkter eller produkter som inte finns i lager läggs. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.41 är installerad. Korrigerings-ID är ACSD-53643. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.3 - 2.4.6-p3

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Ordersumman är felaktig när en inköpsorder med inaktiverade produkter eller produkter som inte finns i lager placeras.

<u>Steg som ska återskapas</u>:

1. Installera *[!UICONTROL B2B]* och *[!UICONTROL Inventory]*.
1. Gå till **[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL B2B]** och ange **[!UICONTROL Company]** = *Yes* och **[!UICONTROL Purchase Order]** = *Yes*.
1. Rensa konfigurationscachen.
1. Skapa ett nytt företag, aktivera det och aktivera *[!UICONTROL Purchase order]* för företaget.
1. Skapa en ny användare för företaget.
1. Skapa en *godkännanderegel* om du vill godkänna alla order på mer än *1 USD* av företagsadministratören.
1. Skapa ytterligare en källa.
1. Logga in som ny företagsanvändare.
1. Lägg två produkter i kundvagnen och gör en inköpsorder.
1. Inaktivera den andra produkten.
1. Logga in som företagsadministratör.
1. Öppna inköpsordern och se att inköpsordern innehåller båda produkterna och summan är för båda produkterna.
1. Godkänn inköpsordern.
1. Beställ.
1. Öppna orderinformationen.

<u>Förväntade resultat</u>:

* Det går inte att placera beställningen även om en produkt i beställningen är *inaktiverad* eller *inte i lager*.
* Knappen *[!UICONTROL Place Order]* är dold.

<u>Faktiska resultat</u>:

Den monterade ordern innehåller endast den första aktiva produkten, men ordersumman beräknas för båda produkterna.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i guiden [!UICONTROL Quality Patches Tool].


Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool]-handboken.
