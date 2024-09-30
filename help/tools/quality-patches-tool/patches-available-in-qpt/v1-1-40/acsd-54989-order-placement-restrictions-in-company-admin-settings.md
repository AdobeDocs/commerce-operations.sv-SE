---
title: '''ACSD-54989: Företagsadministratören kan inte beställa när [!UICONTROL Enable Purchase Orders] har värdet Ja och [!UICONTROL Purchase Order] har värdet Nej'
description: Använd ACSD-54989-korrigeringen för att åtgärda Adobe Commerce-problemet där företagsadministratören inte kan göra beställningar om [!UICONTROL Enable Purchase Orders] är inställt på Ja och [!UICONTROL Purchase Order] är inställd på Nej.
feature: Orders, Companies, Purchase Orders
role: Admin, Developer
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 0%

---

# ACSD-54989: Företagsadministratören kan inte beställa när *[!UICONTROL Enable Purchase Orders]* har värdet *Yes* och *[!UICONTROL Purchase Order]* har värdet *No*

ACSD-54989-korrigeringen åtgärdar ett problem där beställningar inte kan placeras om **[!UICONTROL Enable Purchase Orders]** är inställt på *Yes* och **[!UICONTROL Purchase Order]** är inställda på *No*. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.40 har installerats. Korrigerings-ID är ACSD-54989. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6-p2

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4-p5 - 2.4.6-p3

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Företagsadministratörer kan inte göra beställningar när **[!UICONTROL Enable Purchase Orders]** är inställt på *Yes* och **Purchase Order** är inställt på *No*.

<u>Förutsättningar</u>:

Installera [!DNL B2B] moduler.

<u>Steg som ska återskapas</u>:

1. Aktivera företag och lämna [!UICONTROL **Order Approval Configuration]** > **[!UICONTROL Purchase Order**] = *Nej*.
1. Skapa en enkel produkt till priset 100.
1. Skapa ett nytt företag via Admin.
1. Ange [!UICONTROL **Aktivera inköpsorder**] till *Ja*.
1. Logga in som företagsadministratör i butiken.
1. Lägg den skapade enkla produkten i kundvagnen.
1. Gå till utcheckningssidan och klicka på **[!UICONTROL Place Order]** för att slutföra köpet.

<u>Förväntade resultat</u>:

Du kan göra en beställning.

<u>Faktiska resultat</u>:

Sidan **[!UICONTROL My Account]** öppnas och ordningen placeras inte.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i guiden [!UICONTROL Quality Patches Tool].


Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool]-handboken.
