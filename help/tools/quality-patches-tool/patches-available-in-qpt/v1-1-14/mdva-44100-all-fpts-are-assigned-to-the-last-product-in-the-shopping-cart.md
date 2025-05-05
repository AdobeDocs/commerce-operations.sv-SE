---
title: "MDVA-44100: Alla bildrutefrekvenser tilldelas den sista produkten i kundvagnen"
description: MDVA-44100-korrigeringen löser problemet där alla bildrutefrekvenser tilldelas den sista produkten i kundvagnen. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://experienceleague.adobe.com/sv/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.14 är installerat. Korrigerings-ID är MDVA-44100. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.5.
feature: Orders, Products, Shopping Cart
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '469'
ht-degree: 0%

---

# MDVA-44100: Alla bildrutefrekvenser tilldelas den sista produkten i kundvagnen

MDVA-44100-korrigeringen löser problemet där alla bildrutefrekvenser tilldelas den sista produkten i kundvagnen. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://experienceleague.adobe.com/sv/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.14 är installerat. Korrigerings-ID är MDVA-44100. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.5.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.3-p1

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.3 - 2.4.4

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/sv/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Alla bildrutefrekvenser tilldelas den sista produkten i kundvagnen och FPT-värdena för resten av produkterna återställs.

<u>Steg som ska återskapas</u>:

1. Gå till **Store** > **Configuration** > **Sales** > **Tax** och ange:
   * Aktivera FPT = Ja
   * Tillämpa skatt på FPT = Ja
   * Inkludera FPT i delsumma = Ja
1. Gå till **Lagrar** > **Attribut** > **Produkt** och skapa ett nytt attribut med typen = Fast produktskatt.
1. Lägg till attributet i en attributuppsättning.
1. Skapa två produkter från attributuppsättningen och konfigurera FPT-attributet för ditt land och din stat.
1. Lägg till båda objekten i ordern.
1. Ange en adress som kräver att FPT betalas.
1. Beställ.
1. Kontrollera objektlistan i ordern.

<u>Förväntade resultat</u>:

FPT visas under varje produkt.

<u>Faktiska resultat</u>:

FPT-värdena från båda objekten visas under det andra objektet.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](https://experienceleague.adobe.com/sv/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med verktyget för kvalitetskorrigeringar ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i [!DNL Quality Patches Tool]-handboken.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i [!DNL Quality Patches Tool]-handboken.
