---
title: 'ACSD-51036: Utrymmesvillkor vid samtidiga REST API-anrop resulterar i en överskrivning av leveransstatus'
description: Använd patchen ACSD-51036 för att åtgärda Adobe Commerce-problemet där det finns konkurrensförhållanden under samtidiga REST API-anrop, vilket resulterar i en överskrivning av leveransstatus i artikeltabellen.
feature: REST, Orders, Shipping/Delivery
role: Admin
exl-id: 6150d072-05fe-4010-b31b-8ccde9cab656
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '394'
ht-degree: 0%

---

# ACSD-51036: Utrymmesvillkor vid samtidiga REST API-anrop resulterar i en överskrivning av leveransstatus i artikelordningsregistret

Korrigeringen ACSD-51036 åtgärdar ett problem där tävlingsvillkoren under samtidiga REST API-anrop resulterar i en överskrivning av leveransstatus i artikelordningsregistret. Den här korrigeringen är tillgänglig när [!DNL Quality Patches Tool (QPT)] 1.1.31 har installerats. Korrigerings-ID är ACSD-51036. Observera att problemet har åtgärdats i Adobe Commerce 2.4.5.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4-p2

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.6

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Följevillkoren vid samtidiga REST API-anrop resulterar i en överskrivning av leveransstatus i artikelordningsregistret.

<u>Steg som ska återskapas</u>:

1. Skapa en order med två objekt.
1. Fakturaartikel A.
1. Skicka återbetalningsbegäran för artikel A via REST API samtidigt som du skickar en leveransbegäran för artikel B.
1. Gå till ordningen i **[!UICONTROL Admin Panel]**.

<u>Förväntade resultat</u>

Status *[!UICONTROL Shipped 1]* ska finnas för objekt B i den *[!UICONTROL Items]* ordnade tabellen.

<u>Faktiska resultat</u>

Status *[!UICONTROL Shipped 1]* finns inte för objekt B i den *[!UICONTROL Items]* ordnade tabellen.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i guiden [!UICONTROL Quality Patches Tool].


Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i [!DNL Quality Patches Tool]-handboken.
