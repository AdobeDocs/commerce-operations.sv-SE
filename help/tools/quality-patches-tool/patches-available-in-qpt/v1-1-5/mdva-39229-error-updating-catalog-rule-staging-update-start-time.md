---
title: 'MDVA-39229: Fel efter uppdatering av starttid för katalogregel Mellanlagringsuppdatering'
description: MDVA-39229-korrigeringen åtgärdar ett problem där användare får ett felmeddelande efter att starttiden för uppdateringen av katalogregelns mellanlagring har uppdaterats. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.5 är installerat. Korrigerings-ID är MDVA-39229. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.4.
feature: Catalog Management, Staging
role: Admin
exl-id: 633123bc-634c-4943-a2f1-9a48999774f4
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '446'
ht-degree: 0%

---

# MDVA-39229: Fel efter uppdatering av starttid för katalogregel Mellanlagringsuppdatering

MDVA-39229-korrigeringen åtgärdar ett problem där användare får ett felmeddelande efter att starttiden för uppdateringen av katalogregelns mellanlagring har uppdaterats. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.5 har installerats. Korrigerings-ID är MDVA-39229. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.4.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

Adobe Commerce (alla distributionsmetoder) 2.3.4-p2

**Kompatibel med Adobe Commerce-versioner:**

Adobe Commerce (alla distributionsmetoder) 2.4.2 - 2.4.3-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler &#x200B;](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Användarna får ett fel efter att starttiden för uppdateringen av katalogregelns mellanlagring har uppdaterats.

<u>Steg som ska återskapas</u>:

1. Skapa en katalogprisregel.
1. Skapa och kör alla mellanlagringsuppdateringar.
1. Kör frågan och verifiera att flaggan Förproduktion skapades.


   `select * from flag;`


1. Skapa en ny mellanlagringsuppdatering som börjar efter fem minuter.
1. Öppna **Innehåll** > **Förproduktion** > **Kontrollpanel** > **Ny uppdatering** och fördröj starttiden med en minut.
1. Vänta i sex minuter.
1. Spring cron.

<u>Förväntade resultat</u>:

Uppdateringens starttid ändras och uppdateringen tillämpas. Den gamla uppdateringen tas bort från tabellen `staging_update`.

<u>Faktiska resultat</u>:

Användarna får följande fel:

*report.ERROR: Cron Job staging_synchronize_entities_period har ett fel: Det går inte att ta bort den aktiva uppdateringen.*

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning &#x200B;](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med verktyget för kvalitetskorrigeringar &#x200B;](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i [!DNL Quality Patches Tool]-handboken.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i avsnittet [Patchar i QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE).
