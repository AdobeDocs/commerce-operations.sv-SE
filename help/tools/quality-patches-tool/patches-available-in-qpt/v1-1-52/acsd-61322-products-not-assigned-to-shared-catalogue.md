---
title: 'ACSD-61322: Produkter som inte har tilldelats [!UICONTROL Shared Catalogue] ingår i XML-platskartan'
description: Använd patchen ACSD-61322 för att åtgärda Adobe Commerce-problemet där produkter/kategorier som inte har tilldelats [!UICONTROL Shared Catalog] för standardgruppen (Allmänt) fortfarande ingår i XML-platskartan.
feature: Site Navigation, B2B
role: Admin, Developer
exl-id: 4698ba5a-673e-4bf0-b36c-39f6122dab26
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '446'
ht-degree: 0%

---

# ACSD-61322: Produkter som inte har tilldelats [!UICONTROL Shared Catalogue] ingår i XML-platskartan

Korrigeringen ACSD-61322 åtgärdar ett problem där produkter/kategorier som inte har tilldelats [!UICONTROL Shared Catalog] för standardgruppen (Allmänt) fortfarande ingår i XML-platskartan. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.52 är installerad. Korrigerings-ID är ACSD-61322. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.8.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

Adobe Commerce (alla distributionsmetoder) 2.4.7-p1

**Kompatibel med Adobe Commerce-versioner:**

Adobe Commerce (alla distributionsmetoder) 2.4.6 - 2.4.7-p2

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Produkter/kategorier som inte har tilldelats [!UICONTROL Shared Catalog] för standardgruppen (Allmänt) ingår fortfarande i XML-webbplatskartan.

<u>Steg som ska återskapas</u>:

1. Skapa några kategorier och lägg till produkter (till exempel kategori 1 med kategori 2).
1. Gå till **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B Features]** och aktivera *[!UICONTROL Company and Shared Catalog]*.
1. Gå till **[!UICONTROL Catalog]** > **[!UICONTROL Shared Catalogs]** och ändra standardkatalogen.
1. I listrutan **[!UICONTROL Select]** väljer du **[!UICONTROL Set Pricing and Structure]** och klickar på **[!UICONTROL Configure]**.
1. Under kategorin *Kategori 1 > Kategori 2* avmarkerar du några produkter som inte ska ingå i [!UICONTROL Shared Catalog].
1. Klicka på **[!UICONTROL Next]** och generera katalogen.
1. Skapa ett kundkonto på Storefront.
1. Gå till kategorin *Kategori 1 > Kategori 2*. Den visar bara de produkter som har tilldelats [!UICONTROL Shared Catalog].
1. Gå till **[!UICONTROL Marketing]** > **[!UICONTROL SEO & Search]** > **[!UICONTROL Site Map]** och generera en ny platskarta.
1. Öppna `sitemap.xml` på Storefront.
1. Sök efter de produkter som du inte inkluderade i [!UICONTROL Shared Catalog].

<u>Förväntade resultat</u>:

Platskartan innehåller inte länkar till produkter och kategorier som inte har tilldelats [!UICONTROL Shared Catalog].

<u>Faktiska resultat</u>:

Platskartan innehåller länkar till produkter och kategorier som inte har tilldelats [!UICONTROL Shared Catalog].

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i guiden [!UICONTROL Quality Patches Tool].


Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i [!DNL Quality Patches Tool]-handboken.
