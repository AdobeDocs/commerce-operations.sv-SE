---
title: 'ACSD-53998: Dynamiskt block som baseras på kundsegment fungerar felaktigt efter utloggning'
description: Använd patchen ACSD-53998 för att åtgärda Adobe Commerce-problemet där ett dynamiskt block som baseras på ett kundsegment inte fungerar korrekt efter utloggning från ett kundkonto.
feature: Customers, Page Builder, Personalization
role: Admin, Developer
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 0%

---

# ACSD-53998: Dynamiskt block som baseras på kundsegment fungerar felaktigt efter utloggning

Korrigeringen ACSD-53998 åtgärdar ett problem där ett dynamiskt block som baseras på ett kundsegment inte fungerar korrekt efter utloggning från ett kundkonto. Den här korrigeringen är tillgänglig när [!DNL Quality Patches Tool (QPT)] 1.1.39 har installerats. Korrigerings-ID är ACSD-53998. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5-p2

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4-p2 - 2.4.4-p6, 2.4.5-p1 - 2.4.6-p3

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Ett dynamiskt block som baseras på ett kundsegment fungerar inte korrekt efter utloggning från ett kundkonto.

<u>Förutsättningar</u>:

Installera och aktivera [!DNL Page Builder] moduler.

<u>Steg som ska återskapas</u>:

1. Skapa två kundsegment utan villkor.
1. Skapa två dynamiska block för varje segment.
1. Skapa ett block som innehåller de två dynamiska blocken som [!DNL Page Builder] dynamiska block.
1. Skapa en widget med det ovanstående blocket och gör blocket synligt under sidfotsavsnittet på alla sidor.
1. Rensa cacheminnen.
1. Öppna hemsidan.
1. Logga in som kund.
1. Logga ut.

<u>Förväntade resultat</u>:

Banderollen som skapats för inloggade kunder visas inte för gästanvändare.

<u>Faktiska resultat</u>:

Banderollen som skapats för det inloggade kundsegmentet visas även efter utloggning från kundkontot.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i guiden [!UICONTROL Quality Patches Tool].


Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool]-handboken.
