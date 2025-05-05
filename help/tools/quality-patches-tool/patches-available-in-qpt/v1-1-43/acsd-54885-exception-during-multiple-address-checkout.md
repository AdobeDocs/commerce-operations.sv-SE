---
title: 'ACSD-54885: Undantag under utcheckning av flera adresser när administratören loggar in som kund'
description: Använd korrigeringsfilen ACSD-54885 för att åtgärda Adobe Commerce-problemet när ett fel inträffar under utcheckning av flera adresser när administratören använder funktionen *[!UICONTROL Login as Customer]*.
feature: Checkout
role: Admin, Developer
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '389'
ht-degree: 0%

---

# ACSD-54885: Undantag vid utcheckning av flera adresser när administratören loggar in som kund

Korrigeringen ACSD-54885 åtgärdar ett problem där ett fel inträffar vid utcheckning av flera adresser när administratören använder funktionen *[!UICONTROL Login as Customer]*. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/sv/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.43 har installerats. Korrigerings-ID är ACSD-54885. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6-p1

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Ett fel inträffar vid utcheckning av flera adresser när administratören använder funktionen *[!UICONTROL Login as Customer]*.

<u>Steg som ska återskapas</u>:

1. Kontrollera att *[!UICONTROL Login as Customer]* är aktiverat. Gå till **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Configurations]** > **[!UICONTROL Advanced]** > **[!UICONTROL Admin]** > **[!UICONTROL Admin Actions]** > **[!UICONTROL Logging]** > **[!UICONTROL Login as Customer]**.
1. Skapa en enkel produkt.
1. Skapa ett nytt kundkonto med en adress.
1. Gå till kundkontot i serverdelen:

   * Gå till fliken **[!UICONTROL Account Information]** och ange *[!UICONTROL Allow remote shopping assistance]* = *Ja*.
   * Klicka på **[!UICONTROL Login as Customer]**.

1. Lägg produkten i kundvagnen och fortsätt till *[!UICONTROL Checkout with multiple addresses]*.
1. Uppdatera produktkvantiteten.
1. Försök gå tillbaka till kundvagnen.

<u>Förväntade resultat</u>:

Du kan uppdatera kundvagnen och använda flera adressköp.

<u>Faktiska resultat</u>:

Du får följande fel när du går tillbaka till kundvagnen.

```PHP
report.CRITICAL: Error: Call to a member function getCustomer() on null in magento2ee/app/code/Magento/LoginAsCustomerLogging/Observer/LogUpdateQtyObserver.php:88
```

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](https://experienceleague.adobe.com/sv/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i guiden [!UICONTROL Quality Patches Tool].


Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i [!DNL Quality Patches Tool]-handboken.
