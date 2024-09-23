---
title: 'MDVA-42790: Produktprisattribut kan inte uppdateras för en specifik webbplats via REST API'
description: MDVA-42790-korrigeringen åtgärdar ett problem där användare inte kan uppdatera produktprisattribut för specifika webbplatser via REST API. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.11 är installerat. Korrigerings-ID är MDVA-42790. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.5.
feature: REST, Attributes, Orders, Products
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 0%

---

# MDVA-42790: Produktprisattribut kan inte uppdateras för en specifik webbplats via REST API

MDVA-42790-korrigeringen åtgärdar ett problem där användare inte kan uppdatera produktprisattribut för specifika webbplatser via REST API. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.11 är installerat. Korrigerings-ID är MDVA-42790. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.5.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.3-p1

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.3 - 2.4.3-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Användare kan inte uppdatera produktprisattribut för specifika webbplatser via REST API.

<u>Steg som ska återskapas</u>:

1. Gå till **Lager** > **Konfiguration** > **Katalog** > **Pris** > och ställ in **Katalogens prisomfång** på webbplatsen.
1. Uppdatera specialpris för en paketerad produkt med REST API, `POST rest/V1/products/`.

   ```JSON
   {
     "product": {
       "id": 46,
       "sku": "24-WG080",
       "name": "Sprite Yoga Companion Kit",
       "attribute_set_id": 4,
       "price": 10,
       "status": 1,
       "visibility": 1,
       "type_id": "bundle",
       "weight": 0,
       "custom_attributes": [
         {
           "attribute_code": "special_price",
           "value": "2"
         }
       ]
     }
   }
   ```

<u>Förväntade resultat</u>:

Specialpriset uppdateras för den paketerade produkten när **Katalogprisomfånget** är inställt på Webbplats.

<u>Faktiska resultat</u>:

Specialpriset uppdateras inte för den paketerade produkten när **Katalogprisomfånget** är inställt på Webbplats.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med verktyget för kvalitetskorrigeringar ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i [!DNL Quality Patches Tool]-handboken.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool]-handboken.
