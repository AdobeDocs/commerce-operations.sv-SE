---
title: 'ACSD-52929: Redundant begäran om att indexera om standardkällobjekt'
description: Använd patchen ACSD-52929 för att åtgärda Adobe Commerce-problemet där det finns en redundant begäran om att indexera om standardkällartiklarna när lagerindexeraren är konfigurerad i asynkront läge.
feature: Configuration, Inventory
role: Admin, Developer
exl-id: 904aed0e-a6cd-4a0f-949d-bb32fcd77356
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 0%

---

# ACSD-52929: Redundant begäran om att indexera om standardkällobjekt

Korrigeringen ACSD-52929 åtgärdar ett problem där det finns redundans av begäranden om att indexera om standardkällartiklar när lagerindexeraren har konfigurerats i asynkront läge. Den här korrigeringen är tillgänglig när [!DNL Quality Patches Tool (QPT)] 1.1.38 har installerats. Korrigerings-ID är ACSD-52929. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5-p2

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.3.7 - 2.4.6-p2

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Det finns en redundans av begäranden om att indexera om standardkällartiklar när lagerindexeraren har konfigurerats i asynkront läge.

<u>Steg som ska återskapas</u>:

1. Konfigurera [!DNL RabbitMQ].
1. Aktivera asynkron omindexeringsstrategi genom att gå till **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Inventory Indexer Setting]** och ange **[!UICONTROL Stock/Source reindex strategy]=[!UICONTROL Asynchronous]**.
1. Skapa en anpassad lagerkälla.
1. Logga in på kontrollpanelen [!DNL RabbitMQ] och gå till fliken Köer.
1. Kontrollera kön `inventory.indexer.sourceItem` och se till att den har noll meddelanden.
1. Öppna en enkel produkt från serverdelen och lägg till *[!UICONTROL stock only]* i den anpassade källan och spara produkten.
1. Läs in kön `inventory.indexer.sourceItem` på kontrollpanelen [!DNL RabbitMQ] och kontrollera sedan meddelandena.

<u>Förväntade resultat</u>:

Det finns bara ett meddelande i kön för den anpassade källan.

<u>Faktiska resultat</u>:

Två meddelanden visas i kön: ett för standardkällan och ett för den anpassade källan.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i guiden [!UICONTROL Quality Patches Tool].


Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool]-handboken.
