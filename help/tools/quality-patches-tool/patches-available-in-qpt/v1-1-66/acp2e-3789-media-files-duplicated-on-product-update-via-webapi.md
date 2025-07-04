---
title: 'ACP2E-3789: Mediafiler dupliceras vid produktuppdatering via WebAPI'
description: Använd programfixen ACP2E-3789 för att åtgärda Adobe Commerce-problemet där produktuppdateringar via WebAPI-duplicerade mediefiler när ett medie-ID anges.
feature: Catalog Management, Media, REST, Products, Cache
role: Admin, Developer
type: Troubleshooting
source-git-commit: 8c1924a47248b22327dfc9a15ae426b2802e126b
workflow-type: tm+mt
source-wordcount: '361'
ht-degree: 0%

---


# ACP2E-3789: Mediafiler dupliceras vid produktuppdatering via WebAPI

Programrättningen ACP2E-3789 åtgärdar ett problem där produktuppdateringar via WebAPI-duplicerade mediefiler när ett medie-ID anges. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.66 har installerats. Korrigerings-ID är ACP2E-3789. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.9.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.7-p3

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5 - 2.4.8

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Om en produkt uppdateras via WebAPI med ett medie-ID dupliceras mediefiler i systemet i stället för att de ersätts, skapas nya filer med varje API-anrop och resultatet blir en samling bilder som överför katalogen `/pub/media/catalog/products/cache/`.

<u>Steg som ska återskapas</u>:

1. Skapa en produkt och lägg till en bild.
1. Hämta produktinformation med REST API på `base_url/rest/V1/products/<sku>`.
1. Utför en PUT-begäran om att uppdatera produkten, så att `media_gallery_entrie` inte ändras (samma bildnamn och fil).
1. Kontrollera katalogen `pub/media/catalog/product/xx/yy` före och efter uppdateringen.

<u>Förväntade resultat</u>:

Bildfilen ersätts när medie-ID:t inkluderas i begäran.

<u>Faktiska resultat</u>:

Bilden dupliceras med ett nytt namn (t.ex. wb04-blue-1.jpg), vilket orsakar onödig filgenerering.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.
