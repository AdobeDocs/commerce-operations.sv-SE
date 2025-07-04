---
title: 'ACSD-53628: CSV-försäljningsorderrapporten innehåller felaktiga specialtecken'
description: Använd patchen ACSD-53628 för att åtgärda Adobe Commerce-problemet där CSV-försäljningsorderrapporten innehåller felaktiga specialtecken.
feature: Orders, Data Import/Export
role: Admin, Developer
exl-id: b6293efe-fbeb-4b1e-b408-34dc86228b8e
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '331'
ht-degree: 0%

---

# ACSD-53628: CSV-försäljningsorderrapporten innehåller felaktiga specialtecken

Korrigeringen ACSD-53628 åtgärdar ett problem där CSV-försäljningsorderrapporten innehåller felaktiga specialtecken. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.37 är installerad. Korrigerings-ID är ACSD-53628. Observera att problemet har åtgärdats i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder): 2.4.5-p2

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder): 2.3.7 - 2.4.6-p2

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

CSV-försäljningsorderrapporten innehåller felaktiga specialtecken.

<u>Steg som ska återskapas</u>:

1. Ändra **[!UICONTROL Base Currency]** och **[!UICONTROL Default Display Currency]** till euro i valutainställningarna.
1. Beställ.
1. Gå till **[!UICONTROL Reports]** > **[!UICONTROL Sales]** > **[!UICONTROL Orders]** på sidlisten Admin.
1. Välj datum. Klicka på **[!UICONTROL Show Report]**. Klicka på **[!UICONTROL Export]** om du vill exportera CSV-filen.

<u>Förväntade resultat</u>:

Specialtecken i en exporterad CSV-fil visas korrekt i Excel.

<u>Faktiska resultat</u>:

CSV-försäljningsorderrapporten innehåller ogiltiga specialtecken.


## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i guiden [!UICONTROL Quality Patches Tool].


Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i [!DNL Quality Patches Tool]-handboken.
