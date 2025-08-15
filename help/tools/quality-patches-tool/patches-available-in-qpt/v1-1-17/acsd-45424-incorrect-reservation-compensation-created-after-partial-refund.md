---
title: 'ACSD-45424: Felaktig reservationskompensation skapad efter partiell återbetalning'
description: Korrigeringen ACSD-45424 åtgärdar ett problem där en felaktig reservationskompensation skapas efter en partiell återbetalning. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.17 är installerat. Korrigerings-ID är ACSD-45424. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.6.
feature: Orders
role: Admin
exl-id: 94435816-9f4a-40f9-be80-05836ed7781f
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '571'
ht-degree: 0%

---

# ACSD-45424: Felaktig reservationskompensation skapad efter partiell återbetalning

Korrigeringen ACSD-45424 åtgärdar ett problem där en felaktig reservationskompensation skapas efter en partiell återbetalning. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.17 är installerat. Korrigerings-ID är ACSD-45424. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.6.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.1

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.3.4 - 2.4.4

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Felaktig reservationskompensation skapas efter en partiell återbetalning.

<u>Steg som ska återskapas</u>:

1. Aktivera leveranssätt i butik.
1. Skapa tre lagerkällor och se till att hämtningsplatsen är aktiv i varje (källa1, källa2, källa3).
1. Skapa en ny aktie och tilldela de tre källorna till den nya aktien.
   * Det här Stock ska tilldelas huvudwebbplatsen.
1. Skapa en enkel produkt, P3, och tilldela den alla källor.
1. Lägg till följande kvantiteter för källorna till den enkla produkten och aktivera restorder:
   * Standardkälla - 100
   * källa1 - 0
   * källa2 - 10
   * källa3 - 0
1. Lägg den enkla produkten i varukorgen och fortsätt till leveransformuläret.
1. Välj &quot;source1&quot; som leveransplats.
1. Slutför ordningen och kör följande fråga i databasen:

   ```sql
   SELECT * FROM inventory_reservation WHERE sku = 'P3';
   ```

   Du får den beställda posten i tabellen `inventory_reservation`. Kvantiteten är 10, vilket är korrekt.
1. Fakturera den här ordern från serverdelen.
1. Skapa en kreditnota för endast en produkt. Markera INTE kryssrutan *Återgå till Stock*.
1. Kör samma fråga från steg 8.

<u>Förväntade resultat</u>:

Om du inte valde *Återgå till Stock* när kreditnotan skapades kommer tabellen `inventory_reservation` inte att ha någon post som motsvarar kreditnotan.

<u>Faktiska resultat</u>:

Även om du inte valde *Återgå till Stock* när kreditnotan skapades, läggs en post till i `inventory_reservation`-tabellen med händelsetypen `creditmemo_created`. Dessutom har posten för kreditnota som lagts till i tabellen `inventory_reservation` en kvantitet på 10 trots att du skapade kreditnotan för endast en kvantitet.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med verktyget för kvalitetskorrigeringar ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i [!DNL Quality Patches Tool]-handboken.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i [!DNL Quality Patches Tool]-handboken.
