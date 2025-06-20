---
title: 'MDVA-44562: Butiks-ID för offertobjekt som åsidosatts av standardbutiks-ID'
description: Korrigeringen MDVA-44562 åtgärdar ett problem där standarbutiks-ID åsidosätter butiks-ID för offertobjekt för GraphQL-begäranden. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.16 är installerat. Korrigerings-ID är MDVA-44562. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.6.
feature: Quotes
role: Admin
exl-id: 007a82f7-4bc9-4a51-8b18-05f6c0867ea7
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '450'
ht-degree: 0%

---

# MDVA-44562: Butiks-ID för offertobjekt som åsidosatts av standardbutiks-ID

Korrigeringen MDVA-44562 åtgärdar ett problem där standarbutiks-ID åsidosätter butiks-ID för offertobjekt för GraphQL-begäranden. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.16 är installerat. Korrigerings-ID är MDVA-44562. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.6.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.3-p1

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.3 - 2.4.4

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Butiks-ID för offertobjekt åsidosätts av standardbutiks-ID för GraphQL-begäranden.

<u>Steg som ska återskapas</u>:

1. Skapa en ny butiksvy.
1. Skapa en ny enkel produkt med olika namn per butiksvy.
1. Skapa en ny kund.
1. Hämta kundauktoriseringstoken.

   ```GraphQL
    POST /rest/all/V1/integration/customer/token
    {
      "username": "test@example.com",
      "password": "password"
     }
   ```

1. Skapa en ny offert för kunden med en auktoriseringstoken.

   ```GraphQL
   POST rest/default/V1/carts/mine
   ```

1. Lägg en produkt i kundvagnen.

   ```GraphQL
   POST /rest/default/V1/carts/mine/items
   {
     "cartItem": {
       "sku": "simple1",
       "qty": 1,
       "quote_id": "1"
     }
   }
   ```

1. Hämta kundvagnsinnehållet för standardbutiksvyn.

   ```GraphQL
   GET rest/default/V1/carts/mine/
   ```

1. Hämta kundvagnsinnehållet för den nya butiksvyn.

   ```GraphQL
   GET rest/<store_view_2>/V1/carts/mine/
   ```

<u>Förväntade resultat</u>:

Svar från den nya butiksvyn visar produktnamnet från den nya butiksvyn.

<u>Faktiska resultat</u>:

Svar från den nya butiksvyn visar produktnamnsinställningarna under standardbutiksvyn.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med verktyget för kvalitetskorrigeringar ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i [!DNL Quality Patches Tool]-handboken.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool]-handboken.
