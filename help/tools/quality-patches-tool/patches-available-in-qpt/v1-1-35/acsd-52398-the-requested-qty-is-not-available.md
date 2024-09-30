---
title: 'ACSD-52398: Begärd kvantitet är inte tillgänglig vid försök att uppdatera kvantitet för paketerad produkt'
description: Använd patchen ACSD-52398 för att åtgärda Adobe Commerce-problemet där den begärda kvantiteten inte är tillgänglig när du försöker uppdatera kvantiteten för en paketerad produkt i kundvagnen på butiken.
feature: Shopping Cart, Quotes, Products
role: Admin
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '407'
ht-degree: 0%

---

# ACSD-52398: Begärd kvantitet är inte tillgänglig vid försök att uppdatera kvantitet för paketerad produkt

Korrigeringen ACSD-52398 åtgärdar ett problem där den begärda kvantiteten inte är tillgänglig när man försöker uppdatera kvantiteten för en paketerad produkt i vagnen på butiken. Den här korrigeringen är tillgänglig när [!DNL Quality Patches Tool (QPT)] 1.1.35 har installerats. Korrigerings-ID är ACSD-52398. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.3-p3

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.0 - 2.4.6-p1

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Begärd kvantitet är inte tillgänglig när du försöker uppdatera kvantiteten för en paketerad produkt i kundvagnen i butiken.

<u>Steg som ska återskapas</u>:

1. Skapa två enkla produkter med kvantiteten *1* och *10*.
1. Skapa en paketerad produkt med de enkla produkterna.
1. Lägg den paketerade produkten i kundvagnen.
1. Redigera produkten och försök uppdatera kvantiteten till *3* för alternativet där *10* objekt är tillgängliga.

<u>Förväntade resultat</u>:

Det finns inget fel. Kvantiteten har uppdaterats eftersom det finns *10* objekt i lager för det här alternativet.

<u>Faktiska resultat</u>:

Följande fel inträffar: *Den begärda kvantiteten är inte tillgänglig*.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i guiden [!UICONTROL Quality Patches Tool].


Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool]-handboken.
