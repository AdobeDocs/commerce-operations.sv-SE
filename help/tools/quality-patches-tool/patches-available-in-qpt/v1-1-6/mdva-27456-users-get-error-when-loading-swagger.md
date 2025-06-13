---
title: 'MDVA-27456: Användarna får ett fel när de läser in Swagger'
description: MDVA-27456-korrigeringen åtgärdar ett problem där användare får ett fel när de försöker läsa in Swagger. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.6 är installerat. Korrigerings-ID är MDVA-27456. Observera att problemet har åtgärdats i Adobe Commerce 2.3.7.
feature: Tools and External Services
role: Admin
exl-id: a7d5dc7d-b916-4a09-9068-646f8474bba4
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '365'
ht-degree: 0%

---

# MDVA-27456: Användarna får ett fel när de läser in Swagger

MDVA-27456-korrigeringen åtgärdar ett problem där användare får ett fel när de försöker läsa in Swagger. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.6 har installerats. Korrigerings-ID är MDVA-27456. Observera att problemet har åtgärdats i Adobe Commerce 2.3.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

Adobe Commerce (alla distributionsmetoder) 2.3.5-p1

**Kompatibel med Adobe Commerce-versioner:**

Adobe Commerce (alla distributionsmetoder) 2.3.5 - 2.3.6-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Användarna får ett fel när de läser in Swagger.

<u>Steg som ska återskapas</u>:

Gå till `../swagger.`

<u>Förväntade resultat</u>:

Swagger läses in utan fel.

<u>Faktiska resultat</u>:

Användarna får följande fel: *Det gick inte att läsa in API-definitionen*. Felloggen innehåller:

*report.CRITICAL: Rapport-ID: webapi-5ea9c6da19cb1; Meddelande: Parametertypen &quot;\DateTime&quot; är ogiltig. Verifiera parametern och försök igen.*

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med verktyget för kvalitetskorrigeringar ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i [!DNL Quality Patches Tool]-handboken.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i avsnittet [Patchar i QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html).
