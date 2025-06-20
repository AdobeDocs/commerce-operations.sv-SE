---
title: 'ACSD-46865: [!UICONTROL shipment] och [!UICONTROL credit memo] fylldes inte i när [!UICONTROL asynchronous indexing] är aktiverat'
description: Använd korrigeringen ACSD-46865 för att åtgärda Adobe Commerce-problemet där [!UICONTROL shipment] och [!UICONTROL credit memo] rutnät inte fylls i när [!UICONTROL asynchronous indexing] är aktiverat.
feature: Cache, Orders, Returns, Shipping/Delivery
role: Admin
exl-id: 6f84f5b6-6c34-476c-aae5-9a8ba306f8e4
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 0%

---

# ACSD-46865: [!UICONTROL shipment] och [!UICONTROL credit memo] fylldes inte i när [!UICONTROL asynchronous indexing] är aktiverat

Korrigeringen ACSD-46865 åtgärdar ett problem där [!UICONTROL shipment] och [!UICONTROL credit memo] rutnät inte fylls i när [!UICONTROL asynchronous indexing] aktiveras. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.24 har installerats. Korrigerings-ID är ACSD-46865. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.6.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5-p1

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.5-p1

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

[!UICONTROL Shipment] och [!UICONTROL credit memo] rutnät fylls inte i när [!UICONTROL asynchronous indexing] är aktiverat.

<u>Steg som ska återskapas</u>:

1. Gå till **[!UICONTROL Set Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL Developer]** > **[!UICONTROL Grid Settings]** > **[!UICONTROL Asynchronous indexing Enable]** = *JA* i [!DNL Commerce] Admin.
2. Gå igen till **[!UICONTROL Set Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Sales]** > **[!UICONTROL Orders]** > **[!UICONTROL Invoices]** > **[!UICONTROL Shipments]** > **[!UICONTROL Credit Memos Archiving]** > **[!UICONTROL Enable Archiving]** = *[!UICONTROL YES]*.
3. Rensa konfigurationscachen.
4. Gör en ny gästbeställning av en enkel produkt.
5. Spring cron.
6. Öppna ordern i [!UICONTROL Commerce]-administratören genom att gå till **[!UICONTROL Sales]** > **[!UICONTROL Orders]** och generera en faktura och en kreditnota.
7. Flytta ordningen till [!UICONTROL Archive].
8. Skapa en ny order för en enkel produkt.
9. Spring cron.
10. Gå till den nya ordern och generera en ny leverans, en faktura och en kreditnota.
11. Spring cron.
12. Kontrollera rutnäten [!UICONTROL shipments], [!UICONTROL invoices] och [!UICONTROL credit memo] i administratören.

<u>Förväntade resultat</u>:

Nya [!UICONTROL shipment], [!UICONTROL invoice] och [!UICONTROL credit memo] visas.

<u>Faktiska resultat</u>:

Nya [!UICONTROL shipment], [!UICONTROL invoice] och [!UICONTROL credit memo] visas inte.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i guiden [!UICONTROL Quality Patches Tool].


Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i [!DNL Quality Patches Tool]-handboken.
