---
title: 'ACSD-57941: Produktalternativen har felaktigt tilldelats administratörsarkivet'
description: Använd patchen ACSD-57941 för att åtgärda Adobe Commerce-problemet där produktalternativen felaktigt har tilldelats till administratörsbutiken i stället för deras respektive butiker.
feature: Products
role: Admin, Developer
exl-id: a78c1797-c366-4931-b036-966d3dcf59bb
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '350'
ht-degree: 0%

---

# ACSD-57941: Produktalternativen har felaktigt tilldelats administratörsarkivet

Korrigeringen ACSD-57941 åtgärdar ett problem där produktalternativen felaktigt har tilldelats till administratörsbutiken i stället för deras respektive butiker. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.49 är installerad. Korrigerings-ID är ACSD-57941. Observera att problemet har åtgärdats i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6-p3

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.3 - 2.4.6-p7

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Produktalternativen tilldelas felaktigt till administratörsarkivet i stället för till deras respektive butiker.

<u>Steg som ska återskapas</u>:

1. Skapa en enkel produkt.
1. Importera samma produkt med några anpassade alternativ.
1. Gå till **[!UICONTROL Catalog]** > **[!UICONTROL Products]** och öppna den skapade produkten. Klicka på **[!UICONTROL Customizable options]** och kontrollera att de importerade alternativen är synliga.
1. Importera samma fil några gånger till.

<u>Förväntade resultat</u>:

Anpassade alternativ uppdateras.

<u>Faktiska resultat</u>:

Anpassade produktalternativ är dubblerade.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i guiden [!UICONTROL Quality Patches Tool].


Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool]-handboken.
