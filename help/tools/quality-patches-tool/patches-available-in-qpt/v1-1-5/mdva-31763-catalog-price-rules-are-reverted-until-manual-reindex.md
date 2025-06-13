---
title: 'MDVA-31763: Katalogens prisregler återställs tills manuell omindexering utförs'
description: MDVA-31763-korrigeringen löser problemet där katalogprisreglerna återställs tills manuell omindexering. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.5 är installerat. Patch-ID:t är MDVA-31763. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.4.
feature: Catalog Management, Orders, Price Rules
role: Admin
exl-id: 1d144bfc-c26b-43d0-a80c-26a9c2d8ef32
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '484'
ht-degree: 0%

---

# MDVA-31763: Katalogens prisregler återställs tills manuell omindexering utförs

MDVA-31763-korrigeringen löser problemet där katalogprisreglerna återställs tills manuell omindexering. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.5 har installerats. Patch-ID:t är MDVA-31763. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.4.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.3.5-p1

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

När `catalogrule_product` partiell indexerare körs på konfigurerbara produkter försvinner katalogreglerna.

<u>Steg som ska återskapas</u>:

1. Logga in på Admin Backend.
1. Gå till **Lagrar** > **Attribut** > **Produkt** och sök efter attributet &quot;tillverkare&quot;.
   * Lägg till några alternativ och ange *Ja* som Använd för kampanjregelvillkor.
1. Gå till **Lagrar** > **Attribut** > **Attributuppsättningar**.
   * Välj standardattributuppsättningen och lägg till attributet &quot;manufacturer&quot; i den.
1. Skapa en konfigurerbar produkt med några varianter.
1. Ange attributvärdet &quot;manufacturer&quot; för en tidigare skapad konfigurerbar produkt.
1. Skapa katalogregler:
   * Aktiv = Ja
   * Webbplatser = huvudwebbplats
   * Kundgrupper = INTE INLOGGAD
   * Villkor: tillverkare = \&lt;valt värde för konfigurerbar produkt>
   * Åtgärder: Alla rabatter
1. Gör ett fullständigt index.
1. Kontrollera produktpriset på PDP och se till att priset är korrekt.
1. Uppdatera viktattributet för den skapade konfigurerbara produkten.
1. Kontrollera produktpriset på PDP.

<u>Förväntade resultat</u>:

Katalogprisreglerna som har angetts för konfigurerbara produkter tas inte bort under partiell omindexering.

<u>Faktiska resultat</u>:

Katalogens prisregler för konfigurerbara produkter försvinner vid partiell omindexering.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med verktyget för kvalitetskorrigeringar ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i [!DNL Quality Patches Tool]-handboken.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i avsnittet [Patchar i QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-).
