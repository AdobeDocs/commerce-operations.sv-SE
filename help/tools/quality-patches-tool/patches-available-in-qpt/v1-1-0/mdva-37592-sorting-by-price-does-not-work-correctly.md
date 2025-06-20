---
title: 'MDVA-37592: Sortering efter pris fungerar inte för produkter med priset noll'
description: MDVA-37592 Adobe Commerce-korrigeringen löser problemet där sortering efter pris inte fungerar korrekt för produkter med priset noll som tilldelats en delad katalog. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.0 är installerat. Patch-ID:t är MDVA-37592. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.4.
feature: B2B, Catalog Management, Categories, Orders, Products
role: Admin
exl-id: 4d4a158c-2020-42a4-9b8b-14c9b48b4107
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '469'
ht-degree: 0%

---

# MDVA-37592: Sortering efter pris fungerar inte för produkter med priset noll

MDVA-37592 Adobe Commerce-korrigeringen löser problemet där sortering efter pris inte fungerar korrekt för produkter med priset noll som tilldelats en delad katalog. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.0 har installerats. Patch-ID:t är MDVA-37592. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.4.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce i vår molnarkitektur 2.4.0-p1

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionstyper) 2.3.6-2.4.2-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Sortering efter pris fungerar inte korrekt för produkter med priset noll tilldelat till en delad katalog.

<u>Förutsättningar</u>:

B2B är installerat.

<u>Steg som ska återskapas</u>:

1. Aktivera delad katalog.
1. Skapa fyra produkter med följande priser och tilldela dem till en kategori - 50, 60, 70 och 80 dollar.
1. Skapa en delad katalog med produkterna ovan.
1. Ställ in det anpassade priset på noll för produkten med priset 70 USD.
1. Skapa nu en företagsanvändare och tilldela den till den delade katalog som just har skapats.
1. Logga in med företagskontot och bläddra till den kategori där produkterna är tilldelade.
1. Försök sortera efter pris.

<u>Förväntade resultat</u>:

Produkten med priset noll är korrekt sorterad.

<u>Faktiska resultat</u>:

Produkten med priset noll är INTE korrekt sorterad. I stället sorteras den efter det ursprungliga priset.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i guiden [!DNL Quality Patches Tool].

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool]-handboken.
