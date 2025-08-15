---
title: 'MDVA-43491: Etiketten för basbilden uppdateras inte när den importeras via CSV'
description: Korrigeringen MDVA-43491 åtgärdar ett problem där "base_image_label" inte uppdateras när den importeras via en CSV-fil för en webbplats med flera lager. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.13 är installerat. Korrigerings-ID är MDVA-43491. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.5.
feature: Data Import/Export
role: Admin
exl-id: f6a5f641-aaf0-4b6e-afa9-7f436f8f59e6
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '491'
ht-degree: 0%

---

# MDVA-43491: Etiketten för basbilden uppdateras inte när den importeras via CSV

MDVA-43491-korrigeringen åtgärdar ett problem där `base_image_label` inte uppdateras när den importeras via en CSV-fil för en webbplats med flera butiker. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.13 är installerat. Korrigerings-ID är MDVA-43491. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.5.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2-p2

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.3.5 - 2.4.4

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

`base_image_label` uppdateras inte när den importeras med en CSV-fil för en webbplats med flera lager.

<u>Förutsättningar</u>:

En eller flera befintliga webbplatser, butiker och butiksvyer som inte är standard.

<u>Steg som ska återskapas</u>:

1. Skapa en ny produkt.

   * Överför en bild.
   * Tilldela produkten till nya webbplatser.

1. Exportera produkten som CSV.
1. Uppdatera `base_image_label` för varje butiksvy genom att duplicera standardraden i CSV-filen.
1. Importera CSV-filen. Etiketterna för varje butik uppdateras korrekt, vilket kan verifieras under fliken **Bilder och videor** på produktredigeringssidan.
1. Exportera CSV-filen igen och uppdatera kolumnen `base_image_label` med olika värden.
1. Importera CSV-filen igen.
1. Öppna produkten i Admin och kontrollera om etiketten har uppdaterats för varje butiksvy.

<u>Förväntade resultat</u>:

Alt-text (bildetikett) uppdateras med det butiksspecifika värdet enligt CSV-filen.

<u>Faktiska resultat</u>:

Alt-text (bildetikett) uppdateras inte med värdet `base_image_label` i CSV-filen.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med verktyget för kvalitetskorrigeringar ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i [!DNL Quality Patches Tool]-handboken.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i [!DNL Quality Patches Tool]-handboken.
