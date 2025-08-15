---
title: 'ACSD-53204: *Produkten kan inte sparas* fel vid samtidig begäran om att lägga till bilder i galleriet'
description: Använd patchen ACSD-53204 för att åtgärda Adobe Commerce-problemet där *Felet inte kan sparas* uppstår när du gör samtidiga begäranden om att lägga till bilder i produktgalleriet med resten/V1/products/&lt;sku&gt;/media endpoint.
feature: Catalog Management, Media, Products, REST
role: Admin, Developer
exl-id: 7fdf41e5-46ef-4505-b8ce-c330bd899fa1
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 0%

---

# ACSD-53204: *Det går inte att spara produkten* vid samtidig begäran om att lägga till bilder i galleriet

Korrigeringen ACSD-53204 åtgärdar ett problem där felet *Det går inte att spara produkten* genereras när samtidiga begäranden om att lägga till bilder i produktgalleriet görs med slutpunkten `rest/V1/products/<sku>/media`. Den här korrigeringen är tillgänglig när [!DNL Quality Patches Tool (QPT)] 1.1.39 har installerats. Korrigerings-ID är ACSD-53204. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Felet *Det går inte att spara produkten* när du gör samtidiga begäranden om att lägga till bilder i produktgalleriet med slutpunkten `rest/V1/products/<sku>/media`.

<u>Steg som ska återskapas</u>:

1. Logga in på Admin Panel.
1. Skapa en produkt med SKU p1.
1. Gör flera samtidiga begäranden till slutpunkten `rest/V1/products/<sku>/media` om att överföra flera bilder samtidigt.

<u>Förväntade resultat</u>:

Bilderna sparas utan fel.

<u>Faktiska resultat</u>:

&quot;*Felet &quot;*&quot; kan inte sparas.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i guiden [!UICONTROL Quality Patches Tool].


Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool]-handboken.
