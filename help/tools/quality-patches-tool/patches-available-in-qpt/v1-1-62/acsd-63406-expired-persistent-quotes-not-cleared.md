---
title: 'ACSD-63406: Utgångna beständiga citattecken rensas inte när ett cron-jobb av typen persistent_clear_expirate körs'
description: Använd korrigeringsfilen ACSD-63406 för att åtgärda Adobe Commerce-problemet där de utgånna, beständiga citattecknen inte rensas av något cron-jobb när kron-jobbet "persistent_clear_expirate" körs.
feature: Quotes, Shopping Cart
role: Admin, Developer
source-git-commit: b3bb6ae825f4912b19e2d1f88b5d55835d9769ff
workflow-type: tm+mt
source-wordcount: '348'
ht-degree: 0%

---


# ACSD-63406: Utgångna beständiga citattecken rensas inte när `persistent_clear_expired` cron-jobb körs

ACSD-63406-korrigeringen åtgärdar ett problem där de utgånna beständiga citattecknen inte rensas av något cron-jobb när kron-jobbet `persistent_clear_expired` körs. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.62 har installerats. Korrigerings-ID är ACSD-63406. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.8.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.7-p1

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4-p9 - 2.4.4-p12, 2.4.5-p8 - 2.4.5-p11, 2.4.6-p6 - 2.4.7-p4

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Utgångna beständiga citattecken rensas inte av något cron-jobb när cron-jobbet `persistent_clear_expired` körs.

<u>Steg som ska återskapas</u>:

1. Skapa en kategori och produkt.
1. Gå till **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Persistent Shopping Cart]**.
   1. Ange alla alternativ till *Ja*.
   1. Ange **[!UICONTROL Persistence Lifetime (seconds)]** till *60*.
1. Skapa ett kundkonto i butiken och logga in.
1. Lägg en produkt i kundvagnen.
1. Logga ut, vänta 60 sekunder och logga in igen.

<u>Förväntade resultat</u>:

Kronjobbet `persistent_clear_expired` ska ta bort beständiga citattecken baserat på inställningarna för beständig livstid i konfigurationen.

<u>Faktiska resultat</u>:

Värdet `is_persistent` för kundofferten är fortfarande *1* i offerttabellen.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.


## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.
