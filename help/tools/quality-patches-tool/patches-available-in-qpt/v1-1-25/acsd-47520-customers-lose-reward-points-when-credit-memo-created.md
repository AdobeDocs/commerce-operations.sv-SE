---
title: 'ACSD-47520: kunderna förlorar belöningspoäng när en kreditnota skapas'
description: Använd patchen ACSD-47520 för att åtgärda Adobe Commerce-problemet där kunderna förlorar belöningspoäng när en kreditnota skapas.
feature: Admin Workspace, Cache, Orders, Rewards, Returns
role: Admin
exl-id: 09104451-e9f0-4ddb-b019-8aa34630edb9
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '414'
ht-degree: 0%

---

# ACSD-47520: kunderna förlorar belöningspoäng när en kreditnota skapas

Korrigeringen ACSD-47520 åtgärdar ett problem där kunderna förlorar belöningspoäng när en kreditnota skapas. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.25 är installerad. Korrigerings-ID är ACSD-47520. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.6.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**
* Adobe Commerce (alla distributionsmetoder) 2.4.5

**Kompatibel med Adobe Commerce-versioner:**
* Adobe Commerce (alla distributionsmetoder) 2.4.0 - 2.4.5-p4

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Kunderna förlorar belöningspoäng när en kreditnota skapas.

<u>Steg som ska återskapas</u>:

1. Gå till Adobe Commerce Admin > **[!UICONTROL Store]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Reward Points]**.
1. Ändra inställningen:
   * **[!UICONTROL Enable Reward Points Functionality]** = _Ja_
   * **[!UICONTROL Enable Reward Points Functionality on Storefront]** = _Ja_
   * **[!UICONTROL Customers May See Reward Points History]** = _Ja_
   * **[!UICONTROL Refund Reward Points Automatically]** = _Nej_
   * **[!UICONTROL Deduct Reward Points from Refund Amount Automatically]** = _Ja_
1. Gå till Admin > **[!UICONTROL Store]** > **[!UICONTROL Other Settings]** > **[!UICONTROL Reward Exchange Rates]** och klicka på **[!UICONTROL Add New Rate]**.
1. Lägg till ny frekvens (1:1) och tömma cachen.
1. Skapa en kund och lägg till 10 belöningspoäng på det här kontot.
1. Gå till Admin > **[!UICONTROL Sales]** > **[!UICONTROL Orders]** > **[!UICONTROL Create New Order]** > Välj kunden som skapades i föregående steg.
1. Välj en produkt vars pris är högre än belöningspoängen.
1. Lägg en order via valfri betalningsmetod och belöningspoäng.
1. Skapa en faktura för ordern.
1. Skapa en kreditnota, men återbetala inte belöningspoängen.

<u>Förväntade resultat</u>:

* Administratören kan återbetala belöningspoängen.

* Orderstatusen stängs.

<u>Faktiska resultat</u>:

* Det finns inget sätt att återbetala belöningspoängen.

* Orderstatusen är **[!UICONTROL Completed]**.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i guiden [!UICONTROL Quality Patches Tool].


Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i [!DNL Quality Patches Tool]-handboken.
