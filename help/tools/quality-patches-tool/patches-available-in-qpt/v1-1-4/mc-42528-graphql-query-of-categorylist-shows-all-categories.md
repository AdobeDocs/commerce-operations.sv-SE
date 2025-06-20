---
title: 'MC-42528: GraphQL-frågan för categoryList visar alla kategorier'
description: Korrigeringen MC-42528 löser problemet där GraphQL-frågan för categoryList returnerar både tilldelade och ej tilldelade kategorier när bläddringskategorin för en viss kategori är inställd på Neka. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.4 är installerat. Korrigerings-ID är MC-42528. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.4.
feature: Catalog Management, Categories, GraphQL, Customer Service
role: Admin
exl-id: 0611a7ff-9d55-4d95-9d4e-9ce1d9096bb6
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '465'
ht-degree: 0%

---

# MC-42528: GraphQL-frågan för categoryList visar alla kategorier

Korrigeringen MC-42528 löser problemet där GraphQL-frågan `categoryList` returnerar både tilldelade och ej tilldelade kategorier när bläddringskategorin för en viss kategori är inställd på&quot;Neka&quot;. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.4 har installerats. Korrigerings-ID är MC-42528. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.4.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.3

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.3 - 2.4.3-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

GraphQL-frågan för `categoryList` returnerar både tilldelade och ej tilldelade kategorier.

<u>Steg som ska återskapas</u>:

1. Skapa två kategorier, CAT1 och CAT2, och tilldela ett fåtal produkter till varje kategori.
1. Skapa en privat delad katalog.
1. Skapa en företagsanvändare och tilldela den till den skapade delade katalogen.
1. Tilldela CAT1 till den anpassade katalogen och ange kategoribehörigheten till&quot;Tillåt&quot; bläddringskategori för kundgruppen i den privata katalogen.
1. Ställ in kategoribehörigheten för CAT2 på bläddringskategorin&quot;Neka&quot; för kundgruppen för den privata katalogen.
1. Kör `categoryList`- eller `categories` GraphQL-frågan som företagsanvändare.

<u>Förväntade resultat</u>:

Endast CAT1 visas i svaret.

<u>Faktiska resultat</u>:

Alla kategorier visas i svaret oavsett kategoriens bläddringsbehörigheter.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med verktyget för kvalitetskorrigeringar ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i [!DNL Quality Patches Tool]-handboken.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i avsnittet [Patchar i QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-).
