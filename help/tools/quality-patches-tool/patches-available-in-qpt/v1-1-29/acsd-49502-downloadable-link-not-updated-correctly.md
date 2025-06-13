---
title: 'ACSD-49502: Hämtningsbar länk har inte uppdaterats korrekt efter  [!DNL staging] uppdatering'
description: Använd korrigeringsfilen ACSD-49502 för att åtgärda Adobe Commerce-problemet där den hämtningsbara länken inte uppdateras korrekt efter att en  [!DNL staging] uppdatering har installerats på den hämtningsbara produkten.
feature: Staging
role: Admin
exl-id: 9bdc9a7e-4291-4438-9ba0-65fcab1f95bb
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 0%

---

# ACSD-49502: Hämtningsbar länk har inte uppdaterats korrekt efter [!DNL staging]-uppdateringen

Korrigeringen ACSD-49502 åtgärdar ett problem där den hämtningsbara länken inte uppdateras korrekt efter att en [!DNL staging]-uppdatering har tillämpats på den hämtningsbara produkten. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.29 är installerad. Korrigerings-ID är ACSD-49502. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5-p1

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.3 - 2.4.6

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Den hämtningsbara länken uppdateras inte korrekt efter att en [!DNL staging]-uppdatering har tillämpats på den hämtningsbara produkten.

<u>Steg som ska återskapas</u>:

1. Skapa en nedladdningsbar produkt med länkar.
1. Skapa ett kundkonto och logga in.
1. Lägg den nedladdningsbara produkten i kundvagnen från butiken.
1. I **[!UICONTROL Admin]** schemalägger du en ny uppdatering för den hämtningsbara produkten och låter den schemalagda uppdateringen slutföras.
1. Slutför beställningen i butiken.

<u>Förväntade resultat</u>:

Hämtningsbara länkar bevaras när schemalagda uppdateringar används medan tidigare tillagda produkter finns i kundvagnen.

<u>Faktiska resultat</u>:

Hämtningsbara länkar saknas både under kundens *[!UICONTROL My Account]* ([!UICONTROL My Downloadable Products]) och på ordervysidorna i **[!UICONTROL Admin]**.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i guiden [!UICONTROL Quality Patches Tool].


Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool]-handboken.
