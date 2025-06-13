---
title: 'MDVA-37984: Visual Merchandiser fungerar inte korrekt när mellanlagringsuppdateringar tillämpas'
description: MDVA-37984-korrigeringen löser problemet där Visual Merchandisers"Match product by rule"-funktion inte filtrerar produkter korrekt när mellanlagringsuppdateringar tillämpas. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.9 är installerat. Patch-ID:t är MDVA-37984. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.5.
feature: Categories, Merchandising, Products, Staging
role: Admin
exl-id: 3aeb74a4-b6f7-453a-a8f6-45a345aaa74f
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '466'
ht-degree: 0%

---

# MDVA-37984: Visual Merchandiser fungerar inte korrekt när mellanlagringsuppdateringar tillämpas

MDVA-37984-korrigeringen löser problemet där Visual Merchandisers&quot;Match product by rule&quot;-funktion inte filtrerar produkter korrekt när mellanlagringsuppdateringar tillämpas. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.9 har installerats. Patch-ID:t är MDVA-37984. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.5.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.1 - 2.4.3-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Visual Merchandisers&quot;Match product by rule&quot;-funktion filtrerar inte produkter korrekt när mellanlagringsuppdateringar tillämpas.

<u>Steg som ska återskapas</u>:

1. Skapa en schemauppdatering för alla befintliga produkter.
   * Ange olika värden för `entity_id` och `row_id`.
1. Skapa en ny konfigurerbar produkt och sedan en enkel produkt (så den nya produkten `entity_id` och `row_ids` är också olika).
   * För att det ska bli enklare att replikera problemet anger du ett särskiljande värde för kvantitet för den enkla produkten, till exempel 5000.
1. Gå till en kategori > **Produkter i kategori** och aktivera **Matcha produkter efter regel**.
1. Välj sedan&quot;Quantity&quot; som attribut,&quot;Greater&quot; som operator och&quot;4500&quot; som värde.
1. Klicka på **Spara**.

<u>Förväntade resultat</u>:

Den nya konfigurerbara produkten visas.

<u>Faktiska resultat</u>:

Den nya konfigurerbara produkten visas inte.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med verktyget för kvalitetskorrigeringar ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i [!DNL Quality Patches Tool]-handboken.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool]-handboken.
