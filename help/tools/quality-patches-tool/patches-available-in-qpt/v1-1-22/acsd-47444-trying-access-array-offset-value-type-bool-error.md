---
title: 'ACSD-47444: _[!UICONTROL Trying to access array offset on value of type bool]_ fel vid åtkomst till vissa kategorisökvägar som inte finns för kända produkter i PHP 7.4'
description: Använd patchen ACSD-47444 för att åtgärda Adobe Commerce-problemet där det finns ett _[!UICONTROL Trying to access array offset on value of type bool]_-fel vid åtkomst till vissa icke-befintliga kategorisökvägar för kända produkter i PHP 7.4.
feature: Categories, Products
role: Admin
exl-id: 9f04ee28-d22c-4fdf-9228-e436abe973e8
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '334'
ht-degree: 0%

---

# ACSD-47444: _[!UICONTROL Trying to access array offset on value of type bool]_-fel vid åtkomst till vissa kategorisökvägar som inte finns för kända produkter i PHP 7.4

Korrigeringen ACSD-47444 löser problemet där _[!UICONTROL Trying to access array offset on value of type bool]_-fel visas vid åtkomst till vissa kategorisökvägar för kända produkter i PHP 7.4. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)] ](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.22 är installerad.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**
* Adobe Commerce (alla distributionsmetoder) 2.4.2-p1

**Kompatibel med Adobe Commerce-versioner:**
* Adobe Commerce (alla distributionsmetoder) 2.4.0 - 2.4.2-p2

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Följande fel uppstod: _[!UICONTROL Trying to access array offset on value of type bool]_&#x200B;vid åtkomst till vissa kategorisökvägar som inte finns för kända produkter i PHP 7.4.

<u>Förutsättningar</u>:

PHP 7.4.

<u>Steg som ska återskapas</u>:

1. Skapa en ny produkt - med namnet&quot;test&quot;.
1. Gå till **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL CATALOG]** > **[!UICONTROL Catalog]** > **[!UICONTROL Search Engine Optimization]** > ange **[!UICONTROL Generate "category/product" URL Rewrites]** = _Nej_.
1. Gå till butiken och gå till URL:en som ../abc/test.html (&quot;abc&quot; - should not exist).

<u>Förväntade resultat</u>:

404 sidor.

<u>Faktiska resultat</u>:

500-fel:

_[!UICONTROL Notice: Trying to access array offset on value of type bool in /app/code/Magento/CatalogUrlRewrite/Model/Storage/DynamicStorage.php on line 182]_

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce i molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i vår utvecklardokumentation.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i guiden [!UICONTROL Quality Patches Tool].


Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i [!DNL Quality Patches Tool]-handboken.
