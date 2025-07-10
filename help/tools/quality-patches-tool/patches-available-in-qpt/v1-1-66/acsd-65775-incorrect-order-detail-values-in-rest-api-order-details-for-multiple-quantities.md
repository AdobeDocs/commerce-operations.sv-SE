---
title: 'ACSD-65775: Felaktiga värden för "base_row_total" och "row_total" i REST API-orderdetaljer för flera kvantiteter'
description: Använd patchen ACSD-65775 för att åtgärda Adobe Commerce-problemet där ordningsinformationen för REST API returnerar felaktiga värden för "base_row_total" och "row_total" när flera kvantiteter av samma objekt beställs.
feature: REST
role: Admin, Developer
type: Troubleshooting
source-git-commit: 23c78abaf28f64baf0e91bcaf89bd0e34b5bf78a
workflow-type: tm+mt
source-wordcount: '394'
ht-degree: 0%

---


# ACSD-65775: Felaktiga `base_row_total`- och `row_total`-värden i REST API-orderinformation för flera kvantiteter

Korrigeringen ACSD-65775 åtgärdar ett problem där informationen om REST API-ordningen returnerar felaktiga `base_row_total`- och `row_total`-värden när flera kvantiteter av samma objekt beställs. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.66 har installerats. Patch-ID:t är ACSD-65775. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.9.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.8

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.8

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

`base_row_total` och `row_total` i orderdetaljen REST API-svar visar enhetspriset i stället för det totala priset när flera kvantiteter av samma artikel beställs.

<u>Steg som ska återskapas</u>:

1. Skapa två enkla produkter: simple1 till priset $10 och simple2 till priset $15.
1. Skapa ett nytt kundkonto.
1. Lägg enkel1 i vagnen med kvantitet 2 och enkel2 med kvantitet 3.
1. Gör beställningen med kundkontot.
1. Hämta en administratörstoken genom att skicka en POST-begäran till `/rest/V1/integration/admin/token` med följande nyttolast:

   ```
   {
     "username": "admin",
     "password": "password"
   }
   ```

1. Hämta orderinformationen med en GET-begäran till `/rest/default/V1/orders/1`.

<u>Förväntade resultat</u>:

`base_row_total` och `row_total` ska återspegla det totala priset beräknat som kvantitet multiplicerat med artikelpris (till exempel 2 × $10 = $20 för simple1).

<u>Faktiska resultat</u>:

`base_row_total` och `row_total` returnerar bara enhetspriset (till exempel $10 för simple1 i stället för $20).

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.
