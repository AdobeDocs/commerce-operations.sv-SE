---
title: 'MDVA-41164: Det går inte att spara eller redigera företag med anpassade kundattribut'
description: MDVA-41164-korrigeringen löser problemet där administratörsanvändaren inte kan spara eller redigera ett företag med anpassade kundattribut för filer eller bilder av någon typ. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.5 är installerat. Korrigerings-ID är MDVA-41164. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.4.
feature: Admin Workspace, Attributes, B2B, Companies
role: Developer
exl-id: 9d1792e0-ba7b-444b-b1b1-771fd0e328eb
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '479'
ht-degree: 0%

---

# MDVA-41164: Det går inte att spara eller redigera företag med anpassade kundattribut

MDVA-41164-korrigeringen löser problemet där administratörsanvändaren inte kan spara eller redigera ett företag med anpassade kundattribut för filer eller bilder av någon typ. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.5 har installerats. Korrigerings-ID är MDVA-41164. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.4.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2 - 2.4.3

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Administratörsanvändaren kan inte spara eller redigera ett företag med anpassade kundattribut för filer eller bilder av någon typ.

<u>Förutsättningar</u>:

B2B-modulen är installerad.

<u>Steg som ska återskapas</u>:

1. Aktivera företag i **Lagrar** > **Konfig** > **B2B-funktioner**.
1. Skapa ett kundattribut i **Lagrar** > **Attribut** > **Kunder** > **Lägg till nytt attribut**:
   * Indatatyp: Fil (bifogad)
   * Visa på Storefront: Ja
   * Sorteringsordning: Alla
   * Forms att använda i: Markera alla
1. Skapa ett nytt företag i **Kunder** > **Företag** > **Lägg till nytt företag** och överför en fil för det nya attributet som skapas ovan.

<u>Förväntade resultat</u>:

Användaren kan slutföra skapandet av företaget och bilagan överförs utan fel.

<u>Faktiska resultat</u>:

* Du får ett felmeddelande: *Något gick fel när filen sparades.*
* Undantagsloggen innehåller en post som följande:

  ```php
  report.CRITICAL: Notice: Undefined index: customer in
  ../app/code/Magento/Customer/Controller/Adminhtml/File/Customer/Upload.php on line 69
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
