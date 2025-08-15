---
title: 'ACSD-66049: Icke-engelska butiker visar felaktigt pris på grund av ICU-biblioteksversionen'
description: Använd patchen ACSD-66049 för att åtgärda Adobe Commerce-problemet där icke-engelska butiker visar felaktiga priser på grund av att versionerna av ICU-biblioteket inte matchar i äldre PHP-miljöer (version 63.1 till 74.1).
feature: Products
role: Admin, Developer
type: Troubleshooting
exl-id: e667d462-87f6-4db5-bf3f-3213edac2f09
source-git-commit: da11e8bd5c4937ec2a7e548ce487797b83f8fd27
workflow-type: tm+mt
source-wordcount: '338'
ht-degree: 0%

---

# ACSD-66049: Icke-engelska butiker visar felaktigt pris på grund av ICU-biblioteksversionen

Korrigeringen ACSD-66049 åtgärdar ett problem där icke-engelska butiker visar felaktiga priser på grund av att versionerna av ICU-biblioteket inte matchar i äldre PHP-miljöer (version 63.1 till 74.1). Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.67 har installerats. Korrigerings-ID är ACSD-66049. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.9.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.7-p3

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5-p3 - 2.4.5-p13, 2.4.7 - 2.4.8-p1

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Icke-engelska butiker visar felaktiga priser när äldre PHP ICU-biblioteksversioner (63.1 till 74.1) används.

<u>Steg som ska återskapas</u>:

1. Kontrollera ICU-version:
   * Anslut till servern via SSH och kör kommandot: `php -a`
   * Ange: `echo INTL_ICU_VERSION;`
1. Gå till **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL Locale]** > **[!UICONTROL Locale Options]**. **[!UICONTROL Configure Locale]** = *[!UICONTROL Hebrew (Israel)]*.
1. Skapa en produkt med pris = 100.
1. Visa produktsidan i butiken.

<u>Förväntade resultat</u>:

Det visade priset är inte 0.

<u>Faktiska resultat</u>:

Efter att kort ha visat sig vara 100 uppdateras priset omedelbart till 0.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.
