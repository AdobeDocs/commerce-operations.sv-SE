---
title: 'MDVA-42520: Skattesats som tillämpas två gånger när"Aktivera gränsöverskridande handel" används'
description: MDVA-42520-korrigeringen åtgärdar ett problem där skattesatsen tillämpas två gånger när **Enable Cross Border Trade** används. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.11 är installerat. Korrigerings-ID är MDVA-42520. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.5.
feature: Catalog Management, Orders, Taxes
role: Admin
exl-id: 34c101fd-3a47-4877-8a41-ccaeaa010969
type: Troubleshooting
source-git-commit: 4caabd1578e56b74600441c9c779b7b2dfd06987
workflow-type: tm+mt
source-wordcount: '501'
ht-degree: 0%

---

# MDVA-42520: Skattesats som tillämpas två gånger när&quot;Aktivera gränsöverskridande handel&quot; används

Korrigeringen MDVA-42520 åtgärdar ett problem där momssatsen tillämpas två gånger när **Aktivera gränsöverskridande handel** används. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.11 är installerat. Korrigerings-ID är MDVA-42520. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.5.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.3-p1

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.3 - 2.4.3-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Skattesatsen tillämpas två gånger när **Aktivera gränsöverskridande handel** används.

<u>Steg som ska återskapas</u>:

1. Aktivera **Företag**, **Delad katalog** och **Citat**
1. Konfigurera moms enligt skärmbilden. Se till att du aktiverar **Gränsöverskridande handel**.

   ![Sidan med skattekonfigurationsinställningar med alternativ för gränsöverskridande handel och tariffberäkningar](/help/assets/tools/tax_settings_1.png){width="700"}

1. Skapa en skattesats för Tyskland (10 %).
1. Skapa en momsregel för att tillämpa momssatsen.
1. Skapa ett företag och en anpassad delad katalog.
1. Skapa en produkt med priset 100 och inkludera den i den anpassade delade katalogen med en prisrabatt på 20 %.
1. Skapa en kund med en tysk adress och tilldela den till företaget
1. Lägg till tio produkter på kortet som kund.
1. Gå till kundvagnen och begär en offert.
1. Öppna offerten på baksidan och försök lägga till ytterligare 10 % rabatt.

<u>Förväntade resultat</u>:

Offertdelsumma (inklusive skatt) och totalsumma för offert (inklusive skatt) = $720

<u>Faktiska resultat</u>:

Offertdelsumma (inklusive skatt) och totalsumma för offert (inklusive skatt) = 649,50 USD.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med verktyget för kvalitetskorrigeringar ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i [!DNL Quality Patches Tool]-handboken.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool]-handboken.
