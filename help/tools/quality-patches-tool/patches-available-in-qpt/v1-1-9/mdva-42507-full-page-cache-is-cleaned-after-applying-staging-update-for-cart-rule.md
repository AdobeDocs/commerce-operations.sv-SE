---
title: 'MDVA-42507: Helsidescachen rensas när mellanlagringsuppdateringen för kundvagnsregeln har tillämpats'
description: MDVA-42507-korrigeringen löser problemet där helsidescachen rensas efter att mellanlagringsuppdateringen för kundvagnsregeln har tillämpats. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.9 är installerat. Patch-ID:t är MDVA-42507. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.5.
feature: Cache, Categories, Orders, Shopping Cart, Staging
role: Admin
exl-id: 19f61e31-67da-4bd6-bce7-a9250f3946c7
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 0%

---

# MDVA-42507: Helsidescachen rensas när mellanlagringsuppdateringen för kundvagnsregeln har tillämpats

MDVA-42507-korrigeringen löser problemet där helsidescachen rensas efter att mellanlagringsuppdateringen för kundvagnsregeln har tillämpats. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.9 har installerats. Patch-ID:t är MDVA-42507. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.5.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.3-p1

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.3 - 2.4.3-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Helsidescachen rensas efter att en mellanlagringsuppdatering har tillämpats för kundvagnsregeln.

<u>Steg som ska återskapas</u>:

1. Aktivera utvecklarläge.
1. Öppna flera produkter och kategorisidor och kontrollera (via rubriker) att de har lästs in från cache.
1. Använd alla mellanlagringsuppdateringar för kundvagnsregeln.
1. Kontrollera om kategori- och produktsidorna fortfarande läses in från cachen.

<u>Förväntade resultat</u>:

Helsidescachen rensas INTE efter att en mellanlagringsuppdatering har tillämpats för kundvagnsregeln.

<u>Faktiska resultat</u>:

Helsidescachen rensas när en mellanlagringsuppdatering har tillämpats för kundvagnsregeln.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med verktyget för kvalitetskorrigeringar ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i [!DNL Quality Patches Tool]-handboken.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool]-handboken.
