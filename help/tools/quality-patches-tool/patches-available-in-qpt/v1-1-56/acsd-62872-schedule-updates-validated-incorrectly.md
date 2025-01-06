---
title: 'ACSD-62872: Schemauppdateringar har inte validerats korrekt'
description: Använd patchen ACSD-62872 för att åtgärda Adobe Commerce-problemet med unik attributvalidering där schemalagda uppdateringar inte valideras korrekt.
feature: Catalog Management, Admin Workspace
role: Admin, Developer
source-git-commit: f734dab2316237d60164a430eeabed17782b0ae6
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 0%

---


# ACSD-62872: Schemauppdateringar har inte validerats korrekt

Korrigeringen ACSD-62872 åtgärdar problemet med unik attributvalidering där schemalagda uppdateringar valideras felaktigt. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.56 har installerats. Korrigerings-ID är ACSD-62872. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.8.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6-p5

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Den schemalagda uppdateringen av ett anpassat attribut verifieras felaktigt.

<u>Steg som ska återskapas</u>:

1. Skapa ett anpassat attribut för kategorier.
1. Navigera till **[!UICONTROL Catalog]** > **[!UICONTROL Categories]**.
1. Skapa en ny kategori.
1. Gå till avsnittet **[!UICONTROL Scheduled Updates]** i samma kategori.
1. Ställ in en ny uppdatering för den här kategorin vid framtida tillfällen.
1. Innan du startar den schemalagda uppdateringen kan du försöka redigera den schemauppdatering som har skapats för kategorin.

<u>Förväntade resultat</u>:

Bör kunna uppdatera den schemalagda uppdateringen.

<u>Faktiska resultat</u>:

Ett fel uppstod: *Värdet för attributet Custom är inte unikt. Ange ett unikt värde och försök igen.*

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.


## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.