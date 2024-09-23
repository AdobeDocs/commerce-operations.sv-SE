---
title: 'ACSD-54418: Fast rabattbelopp som felaktigt lagts till i den underordnade produkten i det dynamiskt prissatta paketet'
description: Använd patchen ACSD-54418 för att åtgärda Adobe Commerce-problemet där det fasta rabattbeloppet felaktigt tillämpas på varje underordnad produkt i det dynamiskt prissatta paketet.
feature: Shopping Cart
role: Admin, Developer
source-git-commit: d722ba5ba25ffc03d87b9eddeb2830353124055d
workflow-type: tm+mt
source-wordcount: '380'
ht-degree: 0%

---

# ACSD-54418: Fast rabattbelopp som felaktigt lagts till i den underordnade produkten i det dynamiskt prissatta paketet.

Korrigeringen ACSD-54418 åtgärdar ett problem där det fasta rabattbeloppet felaktigt tillämpas på varje underordnad produkt i det dynamiskt prissatta paketet. Den här korrigeringen är tillgänglig när [!DNL Quality Patches Tool (QPT)] 1.1.42 har installerats. Korrigerings-ID är ACSD-54418. Observera att problemet har åtgärdats i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6-p1

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.0 - 2.4.6-p3

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Det fasta rabattbeloppet tillämpas felaktigt på alla underordnade produkter i det dynamiskt prissatta paketet.

<u>Steg som ska återskapas</u>:

1. Skapa en **[!UICONTROL bundle product]** med dynamisk prissättning och alternativ för *2*-paket.
1. Skapa en **[!UICONTROL cart price rule]** med en specifik kupongkod som bara gäller för den paketerade produkten **[!UICONTROL SKU]** och som har en fast rabatt.
1. Lägg den paketerade produkten i kundvagnen.
1. Använd **[!UICONTROL coupon code]**.
1. Kontrollera rabatten i kundvagnen.

<u>Förväntade resultat</u>:

Rabatten gäller endast en gång för hela den paketerade produkten.

<u>Faktiska resultat</u>:

Rabatten ges för varje underordnad paketprodukt.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i guiden [!UICONTROL Quality Patches Tool].


Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool]-handboken.
