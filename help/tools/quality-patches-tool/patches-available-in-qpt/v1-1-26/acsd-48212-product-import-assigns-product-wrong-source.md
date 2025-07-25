---
title: 'ACSD-48212: Produktimport tilldelar produkten fel källa'
description: Använd patchen ACSD-48212 för att åtgärda Adobe Commerce-problemet där produktimporten tilldelar produkten fel källa.
feature: Admin Workspace, Data Import/Export, Products
role: Admin
exl-id: d573d95b-95fc-4f59-b518-18088855a154
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 0%

---

# ACSD-48212: Produktimport tilldelar produkten fel källa

Korrigeringen ACSD-48212 åtgärdar ett problem där produkten tilldelas fel källa vid import. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.26 har installerats. Korrigerings-ID är ACSD-48212. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4-p2

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.3.7 - 2.4.6

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Vid import tilldelas produkten till fel källa.

<u>Steg som ska återskapas</u>:

1. Skapa en sekundär lagerkälla.
1. Skapa en produkt med enbart standardlagerkällan.
1. Exportera produkten.
1. Kör `bin/magento cron:run`.
1. Öppna **[!UICONTROL Catalog]** > **[!UICONTROL Prdoucts]**.
1. Välj produkten i rutnätet.
1. Ta bort tilldelningen för Stock med menyn *[!UICONTROL mass action]*.
1. Kör `bin/magento cron:run`.
1. Tilldela den sekundära källan via menyn *[!UICONTROL mass action]*.
1. Kör `bin/magento cron:run`.
1. Ta bort produkten från menyn *[!UICONTROL mass action]*.
1. Kör `bin/magento cron:run`.
1. Importera produkten med den tidigare exporterade CSV-filen.
1. Kontrollera källtilldelningen.

<u>Förväntade resultat</u>:

Produkten är endast tilldelad standardkällan.

<u>Faktiska resultat</u>:

Produkten är tilldelad både standardkällan och den sekundära källan.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i guiden [!UICONTROL Quality Patches Tool].


Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i [!DNL Quality Patches Tool]-handboken.
