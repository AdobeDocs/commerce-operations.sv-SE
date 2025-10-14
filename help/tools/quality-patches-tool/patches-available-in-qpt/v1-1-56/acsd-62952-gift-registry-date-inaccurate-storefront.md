---
title: 'ACSD-62952: Presentregisterdatumet visas felaktigt på butiken'
description: Använd patchen ACSD-62952 för att åtgärda Adobe Commerce-problemet där gift-registerdatumet visas felaktigt i butiken.
feature: Gift, Storefront
role: Admin, Developer
exl-id: c11e95ab-775d-4aa7-828b-29ec52685d47
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '331'
ht-degree: 0%

---

# ACSD-62952: Presentregisterdatumet visas felaktigt på butiken

Korrigeringen ACSD-62952 åtgärdar ett problem där gift-registrets datum inte visas korrekt i butiken. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.56 har installerats. Korrigerings-ID är ACSD-62952. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.8.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6-p3

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Händelsedatumet som visas i butiken för ett delat presentationsregister visas felaktigt som en dag före det faktiska datumet.

<u>Steg som ska återskapas</u>:

1. Logga in som kund på frontend.
1. Klicka på [!UICONTROL My Account] på kontrollpanelen **[!UICONTROL Gift Registry]**.
1. Om det inte finns något befintligt register skapar du ett och anger ett datum.
1. Lägg alla artiklar i vagnen.
1. Klicka på **[!UICONTROL Add all items to Gift Registry]** på kundvagnssidan.
1. Dela presentregistret.

<u>Förväntade resultat</u>:

Presentregistret visar korrekt händelsemedatum.

<u>Faktiska resultat</u>:

Presentregistret som öppnats från inbjudningsmeddelandet visar händelsedatumet en dag tidigare.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning &#x200B;](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: Uppgraderingar och korrigeringar > Tillämpa korrigeringar i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.
