---
title: 'MDVA-42326: Kunder får felmeddelanden vid utcheckning efter timeout för session'
description: MDVA-42326-korrigeringen löser problemet där kunderna får ett felmeddelande vid utcheckning efter timeout-datumet för sessionen, även om beständig kundvagn är aktiverad. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://experienceleague.adobe.com/sv/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.8 är installerat. Korrigerings-ID är MDVA-42326. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.4.
feature: Checkout, Orders
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '533'
ht-degree: 0%

---

# MDVA-42326: Kunder får felmeddelanden vid utcheckning efter timeout för session

MDVA-42326-korrigeringen löser problemet där kunderna får ett felmeddelande vid utcheckning efter timeout-datumet för sessionen, även om beständig kundvagn är aktiverad. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://experienceleague.adobe.com/sv/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.8 har installerats. Korrigerings-ID är MDVA-42326. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.4.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.3-p1

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.3.6 - 2.3.7-p2, 2.4.1 - 2.4.3-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/sv/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Kunderna får ett felmeddelande vid utcheckning efter sessionstimeout, även om beständig kundvagn är aktiverad.

<u>Förutsättningar</u>:

1. Gå till **Konfiguration** > **Allmänt** > **Webb** > **Standardinställningar för cookie** > **Kakens livstid** och ange **120**.
1. Gå till **Konfiguration** > **Kunder** > **Kundkonfiguration** > **Alternativ för onlinekunder** och ange båda värdena till **2**.
1. Gå till **Konfiguration** > **Kunder** > **Beständig kundvagn** och ange **Aktivera**.
1. Gå till **Konfig** > **Försäljning** > **Betalningsmetoder** och inaktivera alla betalningsmetoder utom **Kontrollera/betala-order** (den ska vara aktiverad).

<u>Steg som ska återskapas</u>:

1. Logga in som kund och lägg till några produkter i kundvagnen.
1. Kolla kundvagnen.
1. Vänta i två minuter (förvillkor anges). Sessionen bör timeout.
1. Klicka på **Gå till kassan** och uppdatera inte sidan.
1. Checka ut som gäst, fyll i leveransadress och välj leveranssätt.
1. Klicka på **Nästa**.
1. Klicka på **Placera beställning** på sidan **Granska och betalningar**. Eftersom endast en betalningsmetod är tillåten bör kunden kunna lägga ordern utan att välja betalningsmetod.

<u>Förväntade resultat</u>:

Kunden bör kunna lägga ordern.

<u>Faktiska resultat</u>:

Kunden får följande fel: *Adressvalidering misslyckades: E-postmeddelandet har fel format*.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](https://experienceleague.adobe.com/sv/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med verktyget för kvalitetskorrigeringar ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i [!DNL Quality Patches Tool]-handboken.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i [!DNL Quality Patches Tool]-handboken.
