---
title: 'MDVA-39923: Sökning på SKU i B2B-snabbordningsfunktioner är skiftlägeskänsligt'
description: MDVA-39923-korrigeringen åtgärdar ett problem där kunderna får ett felmeddelande när de söker igenom beställningen av SKU:n i B2B-snabborderfunktionen med ett annat fall än det som namnet sparas med. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.2 är installerat. Korrigerings-ID är MDVA-39923. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.4.
feature: B2B, Catalog Management, Orders, Search
role: Admin
exl-id: 9bed5615-b398-42f5-8313-ae2acca59155
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '480'
ht-degree: 0%

---

# MDVA-39923: Sökning på SKU i B2B-snabbordningsfunktioner är skiftlägeskänsligt

MDVA-39923-korrigeringen åtgärdar ett problem där kunderna får ett felmeddelande när de söker igenom beställningen av SKU:n i B2B-snabborderfunktionen med ett annat fall än det som namnet sparas med. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.2 har installerats. Korrigerings-ID är MDVA-39923. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.4.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

Adobe Commerce (alla distributionsmetoder) 2.4.1-p1

**Kompatibel med Adobe Commerce-versioner:**

Adobe Commerce (alla distributionsmetoder) 2.4.1 - 2.4.2-p2

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Att söka på SKU i B2B-snabbordningsfunktioner är skiftlägeskänsligt och visar ett fel när ett annat skiftläge används än det som SKU:n sparas med.

<u>Förutsättningar</u>:

B2B-moduler är installerade.

<u>Steg som ska återskapas</u>:

1. Logga in på administratören och gå till **Store** > **Configuration** > **B2B**.
1. Aktivera **delad katalog** och **snabbordning**.
1. Skapa en produkt med SKU i versaler, t.ex. TEST20-1234
1. Tilldela skapad produkt till **den delade katalogen**.
1. Logga in som kund och klicka på **Snabbbeställning**.
1. Ange SKU i gemener, t.ex. test20-1234.

<u>Förväntade resultat</u>:

Produkten bör hittas oavsett vilket fall som används.

<u>Faktiska resultat</u>:

Följande felmeddelande har tagits emot: *1 produkter kräver din åtgärd*.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med verktyget för kvalitetskorrigeringar ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i [!DNL Quality Patches Tool]-handboken.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i [!DNL Quality Patches Tool]-handboken.
