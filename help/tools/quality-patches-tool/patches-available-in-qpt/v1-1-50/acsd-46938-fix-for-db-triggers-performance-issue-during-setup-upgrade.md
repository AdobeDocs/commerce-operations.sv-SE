---
title: '"ACSD-46938: Prestandaproblem med DB-utlösare under "setup:upgrade"'
description: Använd patchen ACSD-46938 för att åtgärda Adobe Commerce-problemet där kommandot "setup:upgrade" ändrar indexerarläget från schemat för att spara, vilket ger avsevärda prestandaförluster.
feature: Upgrade
role: Admin, Developer
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 0%

---

# ACSD-46938: Prestandaproblem med DB-utlösare under `setup:upgrade`

ACSD-46938-korrigeringen åtgärdar ett problem där `setup:upgrade`-kommandot ändrar indexeringsläget från schemat för att spara, vilket ger avsevärda prestandaförluster. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.50 är installerad. Korrigerings-ID är ACSD-46938. Observera att problemet har åtgärdats i Adobe Commerce 2.4.6.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.5-p9

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Prestandaförsämring under återskapande av databasutlösare i `setup:upgrade`.

<u>Steg som ska återskapas</u>:

1. Skapa en stor katalog med många produkter och kategorier.
1. Logga in på [!UICONTROL Admin].
1. Ställ in alla indexerare till läget [!UICONTROL Update By Schedule].
1. Öppna valfri produkt.
1. Uppdatera den. Du kan till exempel tilldela en ny kategori till den.
1. Klicka på [!UICONTROL Save].
1. Kör kommandona `bin/magento setup:upgrade` och `bin/magento cron:run` parallellt.

<u>Förväntade resultat</u>:

Körningstiden för kommandot `bin/magento setup:upgrade` ökar avsevärt när kommandot `bin/magento cron:run` körs samtidigt.

<u>Faktiska resultat</u>:

Kommandots körningstid ökar inte.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i guiden [!UICONTROL Quality Patches Tool].


Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool]-handboken.