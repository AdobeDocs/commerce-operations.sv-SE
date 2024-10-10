---
title: 'ACSD-49822: Uppdateringar på rekvisitionslistsidan återspeglas inte i utskriftsrekvisitionslistan'
description: Använd patchen ACSD-49822 för att åtgärda Adobe Commerce-problemet där uppdateringarna på rekvisitionslistsidan inte visas i listan över utskriftsrekvisitioner.
feature: Admin Workspace, B2B
role: Admin
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%

---

# ACSD-49822: Uppdateringar i rekvisitionslistan återspeglas inte i utskriftsrekvisitionslistan

Korrigeringen ACSD-49822 åtgärdar ett problem där uppdateringar på rekvisitionslistsidan inte visas i listan över utskriftsrekvisitioner. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.29 är installerad. Korrigerings-ID är ACSD-49822. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.3-p1

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.3.7 - 2.4.6

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Uppdateringar på rekvisitionslistsidan återspeglas inte i utskriftsrekvisitionslistan.

<u>Steg som ska återskapas</u>:

1. Aktivera rekvisitionslistan genom att gå till **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[B2B-funktioner]**.
1. Skapa en produkt.
1. Logga in som kund och lägg till två produkter i rekvisitionslistan.
1. Gå till **[!UICONTROL My Account]** > **[!UICONTROL My Requisition Lists]**.
1. Visa en rekvisitionslista.
1. Klicka på **[!UICONTROL Print]** i det övre högra hörnet.
1. Stäng utskriftsfönstret och listsidan för utskriftsrekvisitioner.
1. Ta bort en artikel i listan eller uppdatera en kvantitet av en artikel och försök skriva ut den igen.
1. Observera att objekten inte uppdateras i utskriftsfönstret.
1. Stäng utskriftsfönstret.
1. Observera att objekten inte uppdateras på sidan för utskrift av rekvisitionslista.

<u>Förväntade resultat</u>:

Listan som ska skrivas ut uppdateras när ändringarna har tillämpats.

<u>Faktiska resultat</u>:

Uppdateringar visas inte på sidan för utskrift av rekvisitionslista.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i guiden [!UICONTROL Quality Patches Tool].


Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool]-handboken.