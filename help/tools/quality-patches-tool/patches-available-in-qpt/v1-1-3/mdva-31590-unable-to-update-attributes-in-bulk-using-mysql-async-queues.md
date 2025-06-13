---
title: 'MDVA-31590: Det går inte att uppdatera attribut i grupp med MySQL async-köer'
description: MDVA-31590-korrigeringen löser problemet där användarna inte kan uppdatera attribut i grupp med hjälp av MySQL async-köer. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.3 är installerat. Korrigerings-ID är MDVA-31590. Observera att problemet har åtgärdats i Adobe Commerce 2.4.2.
feature: Attributes, Services
role: Admin
exl-id: f8d1c3bd-e995-41ef-89e1-93eec6e8b1f1
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '558'
ht-degree: 0%

---

# MDVA-31590: Det går inte att uppdatera attribut i grupp med MySQL async-köer

MDVA-31590-korrigeringen löser problemet där användarna inte kan uppdatera attribut i grupp med hjälp av MySQL async-köer. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.3 har installerats. Korrigerings-ID är MDVA-31590. Observera att problemet har åtgärdats i Adobe Commerce 2.4.2.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.0

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.0-2.4.1-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Användare kan inte uppdatera attribut i grupp med MySQL async.

<u>Steg som ska återskapas</u>:

1. Utför en massåtgärd för att uppdatera attributvärden för ett fåtal produkter i produktrutnätet.
   * Kontrollera produkter och välj **Uppdatera attribut** i listrutan Åtgärder.
1. Ange värden för attributen och tilldela produkter till webbplatser och spara.
1. När sidan har lästs in igen visas ett meddelande som följande:
   *Uppgiften Uppdatera attribut för N valda produkter: 1 objekt har schemalagts för en uppdatering.*
1. Vänta i några sekunder och ladda om backend-sidan.

<u>Förväntade resultat</u>:

1. Sidan visar ett meddelande om att uppdateringen lyckades, till exempel: *1 objekt har uppdaterats.*
1. Attributvärden för relaterade produkter uppdateras.
1. I DB skapas nya poster i både tabellen `magento_bulk` och tabellen `magento_operation` (åtgärder som är relaterade till massan).
1. Nya poster skapas i tabellen `queue_message` (relaterat till köerna `product_action_attribute.update` och/eller `product_action_attribute.website.update`).
1. `queue_message_status`-tabellen har poster med status &quot;4&quot;.
1. `system.log` innehåller INGA fel.

<u>Faktiska resultat</u>:

1. På sidan visas fortfarande ett meddelande som följande:
   *Uppgiften Uppdatera attribut för N valda produkter: 1 objekt har schemalagts för en uppdatering.*
1. Attributvärden för produkterna uppdateras.
1. En ny post skapas i tabellen `message_bulk`, men det finns inga relaterade poster i tabellen `magento_operation`.
1. Nya poster skapas i tabellerna `queue_message` och `queue_message_status`.
1. `queue_message_status`-tabellen har en post med felstatus (statusvärde &quot;6&quot;).
1. `system.log` innehåller fel som liknar följande:

   ```sql
   *main.CRITICAL: Message has been rejected: SQLSTATE[23000]: Integrity constraint violation: 1048 Column 'operation_key' cannot be null, query was: INSERT INTO {{magento_operation}} ({{id}}, {{bulk_uuid}}, {{topic_name}}, {{serialized_data}}, {{result_serialized_data}}, {{status}}, {{error_code}}, {{result_message}}, {{operation_key}}) VALUES (?, ?, ?, ?, ?, ?, ?, ?, ?) [] []*
   ```

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med verktyget för kvalitetskorrigeringar ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i [!DNL Quality Patches Tool]-handboken.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i avsnittet [Patchar i QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-).
